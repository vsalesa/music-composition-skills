---
name: mc-render-compile
description: The compiler from ARR-SPEC to any generation backend (compile layer). One compiler, many backends - the backend differences live in backends.yaml as data, never as separate skills. Covers the compile order, section-tag mapping, turning structured fields into prose style prompts without losing information, lyric chunking, the honors contract that decides which fields are scorable, degradation strategy when a backend cannot execute a field, seeds and best-of-N, and what to hand over so the user can run it in whatever tool hosts the backend. Use when turning a finished ARR-SPEC into Suno / YuE2 / MiniMax / ACE-Step / symbolic output, when choosing a backend, when a generation ignored the spec, or when adding a new backend. Keywords: compile, backend, Suno, YuE2, MiniMax, ACE-Step, prompt generation, section tags, honors.
---

# Render Compile Layer

**This library has only one compiler. Backends are data, not skills.**

```
ARR-SPEC (the only IR)
    ↓  mc-render-compile   ← the only one; handles what is common
    ├─→ backends.yaml: yue2      ★ can take an ABC score directly; the strongest control
    ├─→ backends.yaml: suno         prose prompt + section tags; the most polished output
    ├─→ backends.yaml: minimax-music-3
    ├─→ backends.yaml: ace-step-1.5
    ├─→ backends.yaml: stable-audio-3   (no vocals)
    └─→ backends.yaml: symbolic         MIDI/MusicXML, fully deterministic
```

> **Adding a new model = add one block in `backends.yaml`, without touching any skill.**
> This is the frontend/backend separation of a compiler.

## Which sections to read for each task

| Task | Read |
|---|---|
| Choosing which backend | §2 capability comparison |
| Compiling a spec | §3 compile order (**follow it in sequence, do not skip steps**) |
| Writing the style_prompt | §4 |
| Section tags do not match | §5 |
| Backend ignores the spec | §6 honors contract + §7 degradation |
| Need ABC/MIDI output | `mc-symbolic-score` |
| Handing the compiled result to a backend for execution | §8 |
| Adding a new backend | §9 |
| Generation is finished | `mc-ai-tell-audit` |

## Boundaries

| Not covered here | Where it lives |
|---|---|
| How the content in ARR-SPEC is conceived | L1/L2 skills |
| How ABC / MusicXML / MIDI are generated | `mc-symbolic-score` |
| Whether the output sounds AI-generated | `mc-ai-tell-audit` |
| How the compliance rate is calculated | Defined in `mc-ai-tell-audit` §3.1; this skill's §6 covers only how the three honors levels affect scoring |
| Where per-backend weights go and what nodes are called | [`backends.yaml`](../mc-workflow/backends.yaml) (**data**) |
| Which style words to write in a style description | `mc-style-*` (L3) |

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① Target backend** | At least one. **If there are several, you need the §7 degradation table** |
| **② What this run is meant to verify** | Producing a final output, or running an A/B test? **An A/B test must lock all other variables** |
| **③ Seed strategy** | Fixed seed for controlled comparison, or best-of-N selection |
| **④ Which fields this backend cannot do** | Check `honors`. **This decides where you should not spend prompt budget** |

---

## 2. Backend capability comparison

| | **YuE2** | Suno | MiniMax | ACE-Step | Stable Audio | Symbolic |
|---|---|---|---|---|---|---|
| Input | Style + lyrics + **optional ABC** | Prose + section tags | Prose + lyrics + reference | Tags + prose | Prose | Score |
| **Key/harmony** | ★ **Precise** (ABC) | Hint only | Hint | Hint | — | Precise |
| **Form/bar count** | ★ **Precise** | **Cannot be controlled** | Hint | Hint | — | Precise |
| Vocals | Yes | Yes | Yes | Yes | **No** | **No** |
| Reproducibility | seed + best-of-8 | Weak | — | seed | seed | **Complete** |
| Timbre quality | High | **Highest** | High | Medium | High | Depends on the sound source |
| Commercial use | ★ **Weights are CC-BY-NC, not commercially usable** | Depends on subscription tier | To be verified | Depends on licence | Depends on licence | Yes |

**Selection guide**:

| Purpose | Choose |
|---|---|
| **Verify whether the spec is executed** | **YuE2** (the only one that "executes" rather than "hints") |
| **Need finished-product quality** | **Suno** |
| **Need a fully reproducible control baseline** | **Symbolic path** |
| **Pure instrumental / ambient** | Stable Audio |
| **Commercial release** | ★ **Resolve the licence first**: YuE2 weights are CC-BY-NC-4.0, not commercially usable |

---

## 3. ★ Compile order

**Follow the order. Skipping steps produces prompts that contradict each other.**

| # | Step | Notes |
|---|---|---|
| **0** | **Run through the 20 self-checks in `mc-workflow` §3.0** | Fix any item that fails, or state the reason before compiling. **This is not an entry gate**; it is the last chance to catch an unfinished spec |
| **1** | **Read `honors` in `backends.yaml`** | Mark the fields set to `none`. **They do not go into the prompt and are not scored** |
| **2** | **Put `mix_intent.mood` first** | It has veto power over the remaining decisions, so it must appear early in the prompt |
| **3** | **Compile the style_prompt** | §4 |
| **4** | **Compile the section-tag sequence** | §5. ★ **The count must equal the number of `form` sections** (lint #13) |
| **5** | **Compile the lyric chunks** | §5.3 |
| **6** | **Symbolic path** (if the backend supports it) | → `mc-symbolic-score` |
| **7** | **Compile exclude / negative prompt** | §4.4 |
| **8** | **Set seed and batch size** | §7.3 |
| **9** | **Write back to `render.<backend>`** | ARR-SPEC records the result of this compile itself |

★ **Do not forget step 9**: the `render` section is part of the spec.
**If it is not written back, the next A/B round has no way of knowing exactly what was sent last time.**

---

## 4. style_prompt: compressing structured fields into prose without losing information

### 4.1 Source priority

**Extract from the fields below, in this order** (the earlier an element appears, the more likely the model is to adopt it):

1. `mix_intent.mood` (one sentence)
2. Style words matching `meta.style_layer` (→ L3 skill)
3. `meta.tempo`, `meta.key`
4. `arrangement.roster[].instrument` + `timbre`
5. `groove.feel` + the **direction** of push_pull (not milliseconds; write "bass playing ahead of the beat")
6. `vocal.persona` + `vocal.delivery`
7. Era / production-texture words

### 4.2 ★ Three hard rules

1. **Ban empty adjectives**: `epic` / `emotional` / `beautiful` / `amazing` / `masterpiece` / `perfect`
   (lint #13 soft warning). They carry no executable information and only take up space
2. **Convert numeric values into audible descriptions**:
   `push_pull: bass −12ms` → `bass playing slightly ahead of the beat` (**do not write −12ms**)
3. **Every word must point to a roster item or a spec field.**
   ★ **Self-check action**: go through the style_prompt word by word, circling each one; delete any word whose source you cannot circle

### 4.3 A measured sample (City Pop)

```
1980s Japanese city pop, 112 BPM, D major, Rhodes electric piano,
16th-note muted clean guitar, electric bass playing ahead of the beat,
gated reverb snare, analog saw synth lead riff,
tenor saxophone solo in the bridge and outro,
female vocal with breathy tone mixed back, warm tape saturation
```

**Note its construction**: era + style → tempo and key → **each instrument with its playing technique** → vocal → production texture.
**Not one adjective is empty.**

### 4.4 Exclude (negative prompt)

**Write it from "what this song is not", not from "don't sound bad".**

Measured sample:
```
["EDM drop", "trap hi-hats", "modern sidechain pumping",
 "orchestral epic", "fade out ending"]
```

★ The last item, `fade out ending`, is worth noting:
**a fade-out is the default ending of generation models**, and without excluding it you will very likely get a fade-out
(→ `mc-arrangement-arch` §8, three types of ending).

---

## 5. Section tags and lyrics

### 5.1 Mapping table

`form[].name` → backend tag:

| ARR-SPEC | Suno / most backends |
|---|---|
| Intro | `[Intro]` |
| Verse | `[Verse]` |
| Pre-Chorus | `[Pre-Chorus]` |
| Chorus | `[Chorus]` |
| **Bridge** | `[Bridge]` |
| Instrumental | `[Instrumental]` |
| Outro | `[Outro]` |

★ **Two mapping traps**:
1. **The ōsabi (大サビ, big final chorus) maps to `[Bridge]`, not `[Chorus]`** (→ `mc-form` §7).
   If it is mapped wrongly, the backend will place a high-energy chorus at the position where the introspective section should be
2. **The otosabi (落ちサビ, chorus in a sparse arrangement) still maps to `[Chorus]`**.
   Express the sparseness in the style_prompt or in a section note, **do not try to express it by changing the tag**

### 5.2 Counts must match

The full statement of this rule is in §3 step 4 (the count must equal the number of `form` sections, lint #13), and it is also repeated in the §11 pre-submission checklist. It has its own section because it is the easiest place to make an error during compilation: after manually editing lyric sections, it is easy to forget to add or remove the matching tags. If one tag is missing, the backend decides for itself what that section is. When something goes wrong, check here first.

### 5.3 Lyric chunking

- Split the lyrics by section, **with one-to-one correspondence to the tags**
- ★ Line breaks within a section **affect phrase breaks**. They are not just layout: the backend reads them as phrase boundaries
- **Where the lyrics come from**: this skill compiles only the side of this package (section tags, style description, exclusion words, symbolic path). The lyric side is read from `meta.upstream.lyrics.sections`, where each `id` is the same as `form[].id`; place each section's lines under the matching tag by id. It can also be the lyric spec sheet for the same song: locate it via `meta.upstream.lyrics.source`, take lines by section id, and use the lines as they are, without changing any characters or re-splitting them
- If section ids do not match (the lyrics contain a section that `form` lacks, or the reverse) → do not guess; compile according to `form[]`, record the unmatched sections in `checks.exemptions`, and write one `messages` entry to the lyricist (`to: lyrics`). When lyrics come first, section ids are set by the lyric side (`mc-workflow` §5.1), so instead change this package's `form[]` to align with them
- If there are no lyrics, handle it according to the three cases in `mc-workflow` §2.3 (no words, placeholder syllables to indicate the vocal rhythm, or this package writes the lyrics and records an exemption)
- For the format for sending chunked lyrics to a backend (consequences of line breaks, breath points, held notes, punctuation and brackets, comments kept out of the lyric block, instrumental sections, which backends accept lyrics, and what to check before sending), see [reference-lyrics.md](reference-lyrics.md)

---

## 6. ★ The honors contract: the most important rule in this skill

Each backend declares in `backends.yaml` how well it can execute each ARR-SPEC field:

| Value | Meaning | How it is judged |
|---|---|---|
| **exact** | Can execute precisely | **Scored**; falling short means it failed to deliver |
| **hint** | Can only influence generation as a hint | **Scored, but with reduced weight** |
| **none** | Does not accept this field at all | ★ **Excluded from scoring**, marked "not supported by this backend" |

### 6.1 Why none must be excluded rather than scored as 0

> **Suno has never been told exact chords, so deducting its score for "chords not followed" punishes it for something it cannot do.**

★ **A worse consequence**: if none scores 0, then
**a backend that honestly declares "I cannot do timbre placement" would score lower than one that pretends it can** —
the scoring system would reward misrepresenting capability. **This is a correctness bug, not a question of definition.**

### 6.2 How to use it when compiling

1. Fields set to `none` **do not go into the prompt**: writing them does no good, and it takes up room that useful information could occupy
2. Fields set to `hint` **should be written, but do not rely on them**: pair them with best-of-N
3. Fields set to `exact` **must be written precisely**; this is where you spend money to gain control

---

## 7. Degradation strategy

### 7.1 One spec, several backends

**Do not write a separate spec for each backend.** Write one, and degrade it according to honors:

| Field | YuE2 (exact) | Suno (none) | How to degrade |
|---|---|---|---|
| `form.harmony` | Compiled into ABC | — | **Degrade into modal/colour words in the style description** ("with a lot of minor-subdominant colour") |
| `form.bars` | Compiled into ABC bars | — | **Degrade into a length hint in the section-tag sequence**, and accept that it cannot be controlled |
| `groove.push_pull` | — | hint | Degrade to "playing ahead of the beat" |
| `mix_intent` | none | none | ★ **Neither backend can do it → handle in post-production, or use the symbolic path** |

### 7.2 Record degradations

Record format is in §10 (written to `checks.exemptions`); the delivery checklist is in §8.1 (written back to `render.<backend>`). What matters here is the reason: ★ record in `render.<backend>` which fields were degraded this time. Otherwise, when the next round shows a low compliance rate, you cannot tell whether the spec was written wrongly or the backend simply cannot do it. A low score caused by degradation and a low score caused by a spec error look identical in the compliance rate, and only the person who compiled it at the time knows the difference, so it must be recorded on the spot.

### 7.3 Seeds and batches

| Purpose | Approach |
|---|---|
| **A/B comparison** | **Fixed seed**, change only one field. Changing two proves nothing |
| **Producing a final output** | **Best-of-N** (YuE2 suggests 8), ranked by compliance rate (use a measurement tool if available; otherwise compare field by field), **then choose by ear from the top 3** |
| **Exploration** | Leave the seed free, but record which seed produced what |

---

## 8. Handing over for backend execution

The output of this skill is **the input values for each backend**: Suno's style description and section tags, YuE2's ABC and parameters,
and the prompt and parameters for ACE-Step / MiniMax / Stable Audio.
★ **Which tool is used to send these values to the model is decided by the user's environment**: command line, Python API,
or a node-based host such as ComfyUI. This skill does not assume or manage it.
The `transport` field in `backends.yaml` records only "where this backend usually runs"; it is data, not a precondition.

### 8.1 What to give the user at delivery

| Backend | What to hand over |
|---|---|
| Suno | style_prompt, exclude, lyrics with section tags or placeholder syllables (§4, §5) |
| YuE2 | ABC text (`mc-symbolic-score`) + genre / tempo parameters; **and state explicitly: feed this ABC directly into the synthesis step, bypassing the model's own symbolic planning** |
| ACE-Step / MiniMax / Stable Audio | Prompt and parameters such as duration, following each one's `accepts` list |

Write every item back to `render.<backend>`; the user takes it into their own tool and fills it in there.

### 8.2 The key connection for YuE2

YuE2 works in two steps: **symbolic planning (the model writes ABC itself) → synthesise audio from the ABC**.
★ **Bypass the first step**: feed the ABC compiled by `mc-symbolic-score` directly into the second step.
This is the highest point of control in this library: the spec is no longer a "hint" but is executed.
Any host that supports YuE2 can connect this way (the official repository has scripts, and ComfyUI has native nodes); how the wiring is done is up to the user's environment.

> The official YuE2 repository includes `skills/yue2-music/` (including "check musical invariants").
> ★ **Do not rewrite it**: we write only the ARR-SPEC→ABC adapter, and for model-operation knowledge we refer to theirs.

---

## 9. Adding a new backend

1. Add one block in `backends.yaml`: `id / name / transport / accepts / honors / license`
2. ★ **Make `honors` honest**: it is better to mark `none` than to pad things out with `hint` (reasons in §6.1)
3. Fill in `transport` (hosted / local): this only records where it usually runs; it is not a requirement
4. **Run `example-01-citypop.yaml` through it**, and check whether the compiled output is reasonable
5. **Do not change any skill**

---

## 10. Field mapping to ARR-SPEC

| Field | This skill |
|---|---|
| `render.suno` | §4, §5 |
| `render.yue` | §4, §5, §8.3 |
| `render.midi` | → `mc-symbolic-score` |
| `checks.exemptions` | ★ Degradation records are also written here |

---

## 11. Checks after compiling

- [ ] Ran through the 20 checks in `mc-workflow` §3.0; any that failed have a recorded reason
- [ ] Checked the target backend's `honors`; fields set to `none` **did not go into the prompt**
- [ ] `mood` is **near the start** of the prompt
- [ ] In the style_prompt, **every word points to a spec field**
- [ ] **No empty words** such as `epic` / `emotional` / `beautiful`
- [ ] Numeric parameters **were converted into audible descriptions**; no milliseconds written into the prompt
- [ ] Number of section tags **== number of `form` sections**
- [ ] **The ōsabi (大サビ) maps to `[Bridge]`**
- [ ] `exclude` **excludes a fade-out ending** (unless a fade-out is actually intended)
- [ ] Seed strategy is explicit; for an A/B test, **only one variable changed**
- [ ] **Degradation records written back to `render.<backend>`**
- [ ] After generation, compare against the spec field by field first (compliance rate), **then listen**

---

## Appendix: Sources

- Backend data: [`backends.yaml`](../mc-workflow/backends.yaml)
- ⚠ **The MiniMax Music commercial API is closed to new users**; see the profile in backends.yaml
- ⚠ Unconfirmed: the ABC dialect accepted by the YuE2 synthesis step; the correspondence between its musical invariants and the 20 self-checks
- **Stem separation**: the vocal AI-tell audit must first separate out the vocal track; any stem-separation tool will do (Demucs-type, or one bundled with the user's host), see `mc-ai-tell-audit` §6.1
