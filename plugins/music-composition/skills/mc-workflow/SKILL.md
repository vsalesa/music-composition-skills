---
name: mc-workflow
description: Entry point and router for the music composition library (composition and arrangement workflow and routing). The S0-S7 stage table from brief to delivered audio, which skill to load for which task, the full-library boundary table that prevents two skills claiming the same decision, the ARR-SPEC gate rules, and the three checks (boundary tables against style bleed, text-layer A/B, compliance rate). Load this FIRST for any request that will produce or change an ARR-SPEC (a whole track, a section rewrite, a generation run). A single knowledge question or a single-part task goes straight to the owning skill without this one. Use when starting a new track, when unsure which skill owns a question, when a spec fails lint, when a generated result sounds wrong and you need the diagnostic path, or when handing the spec to another department (lyrics, mixing, editing). composition, arrangement, workflow, routing, which skill to read, ARR-SPEC, song production pipeline.
---

# Workflow & Routing

**For any composition or arrangement request, read this skill first, then decide which other one to read.**

The output of this library is **not audio, it is an ARR-SPEC** (arrangement spec sheet).
Audio is produced by the backend; the spec determines what it sounds like and how to accept it.

> **The fundamental stance of this library**: AI flavor is not a timbre problem; it is **nobody having made a choice**.
> The entire process is a **machine that forces choices to be made**.

---

## 0. Thirty-second orientation: where to go

| What you are doing now | Go to |
|---|---|
| Starting a song from scratch | §1 stage table, start from S0. ★ Before S2a you must read `mc-development`, then fill `material` and `form[].development`; filling only from the schema field descriptions turns every section into a new picture |
| You have a brief and need a spec sheet | §1 S1–S4 (S2 is now split into S2a material and development, and S2b harmony) |
| Spec sheet is written, ready to generate | §1 S5 + `mc-render-compile` |
| Generated result, something is off | §4 diagnostic path |
| Not sure which skill owns a question | §2 full-library boundary table |
| Lint fails | §3.2 |
| Handing off to lyricists, mixing, editing, or other departments or people | §5 external interfaces |
| To verify: whether the chosen skill is right, which of two versions is better, whether the backend followed the spec | §6 three verification methods |
| **Mixing two styles** (rap + Chinese style, city pop + EDM…) | ★ §2.4 |

---

## 1. Stage table S0–S7

**Each stage has a clear deliverable and a gate. A gate that does not pass does not allow entry to the next stage.**

| Stage | What it does | Output | Gate | Main skill |
|---|---|---|---|---|
| **S0 Intent** | Turn the brief into "does exactly one thing" | the four `intent` items | **all four present**; `borrow` may not just write a song title | this skill §3.1 |
| **S1 Skeleton** | Set key, meter, tempo, form table | `meta` + `form` | sections chain end to end; **not all multiples of 8** | `mc-form`, `mc-harmony`, `mc-arrangement-arch` |
| **S2a Material & development** | Set the theme motif, which section holds its original statement, what each section does with it | `material` + `form[].development` | **read `mc-development` before filling**; motif and stated_in non-empty; development filled for every section; fewer than half the sections marked as new | `mc-development`, `mc-melody` |
| **S2b Melody & harmony** | Write the main melody, the harmonic progression, necessary counterpoint | `form[].harmony` + `harmony_letters` | **both notations must be present**; at least one section has a non-diatonic chord | `mc-melody`, `mc-harmony`, `mc-progressions`, `mc-modulation`, `mc-counterpoint` |
| **S3 Lineup** | Who is present, when they enter and exit, which frequency bands they occupy | full `arrangement` | the energy curve **must drop somewhere**; at least one instrument exits early; at least one subtraction event | `mc-arrangement-arch`, `mc-orchestration`, `mc-texture-layering`, `mc-rhythm-section`, `mc-sound-design` |
| **S4 Vocals & mix intent** | How to sing, how the soundstage is placed | `vocal` + `mix_intent` | dynamics **differ section by section**; the chorus **changes on every pass**; width takes at least two values | `mc-vocal-direction`, `mc-mix-intent` |
| **S5 Compile** | Spec sheet → input for each backend | `render.*` | Run the 20 self-check items in §3.0; items that fail are fixed or have their reasons written down | `mc-render-compile`, `mc-symbolic-score` |
| **S6 Generate** | Run the backend, take several versions | audio | use `backends.yaml` `honors` to decide which fields can be relied on | `mc-render-compile` |
| **S7 Acceptance** | Compute first, then listen | compliance rate + AI-flavor flags | look at two things separately: did the backend follow the spec, and does the output carry a machine fingerprint; the ear comes in only after that | `mc-ai-tell-audit` |

### 1.1 ★ Three order rules you must not skip

1. **Do not write `form` until `intent` is complete.** This is the only hard gate in the whole process.
2. **Do not compile while any of the 17 items fail.** A failure means the spec is unfinished, not that the checker is being picky. ★ Self-check item by item per §3.0; **do not write a lint script for this**.
3. **Do not rework by ear until the compliance rate passes.** Fix the spec and regenerate first; the ear is the last small step.

> Rule 3 breaks most easily. "It sounds wrong to me, so I'll adjust the mix" —
> at that moment you have dropped from **spec-driven** back to **feel-driven**,
> and feel-driven output cannot be reproduced, cannot be A/B tested, and cannot accumulate.

### 1.2 How the ear comes in (after S7)

Listen only after the compliance rate passes, and: **A/B shuffle → paired comparison → listen to the same pair twice to see whether the conclusion holds.**
Two listens are not excessive caution: the auditory system changes its processing strategy under repeated exposure, so the same sound heard a second time can yield a different conclusion; this kind of judgment is naturally hard to reproduce (p0251-p0252). If the two listens disagree, the difference does not exist; do not change anything.

If a long gap separates the two listens, guard against the opposite bias: under sustained exposure the ear gradually adapts to timbre changes, so the longer you listen, the more the two versions seem alike, and a real difference can be misjudged as nonexistent (p0342). **Leave a break between the two judgments; do not keep switching back and forth**, which guards against both errors at once.

---

## 2. Full-library boundary table

**Every decision has exactly one owner.** If unsure, check this table.

### 2.1 By question

| Question | Owner |
|---|---|
| What is this song for | **this skill**, S0 |
| Which form to use, how long the sections are | `mc-form` (theory) + `mc-arrangement-arch` (asymmetry and energy) |
| How to write the melody, singability | `mc-melody` |
| How to choose and voice chords | `mc-harmony` |
| Look up an existing progression | `mc-progressions` |
| How to modulate | `mc-modulation` |
| What the rhythmic pattern is | `mc-rhythm-groove` |
| How to make parts independent and avoid parallels | `mc-counterpoint` |
| How a motif grows into a section, and a section into a song | `mc-development` (L1); the melody itself in `mc-melody`, section function in `mc-form` |
| When instruments enter and exit, the energy curve | `mc-arrangement-arch` |
| Which instrument to use, blending timbres | `mc-orchestration` |
| How frequency bands are divided, who competes with whom, foreground / midground / background | `mc-texture-layering` |
| Whether the playing sounds human, how bass and kick are paired | `mc-rhythm-section` |
| How to build synth timbres | `mc-sound-design` |
| How to sing the vocal, how to add harmony | `mc-vocal-direction` |
| How to place the soundstage, who yields to whom | `mc-mix-intent` |
| How to approach this style | `mc-style-*` (L3); for Latin American styles read `mc-style-latin` router then the selected `mc-style-latin-*` child |
| How the spec sheet becomes a prompt | `mc-render-compile` |
| Producing ABC / MIDI / MusicXML | `mc-symbolic-score` |
| Where the generated output sounds like AI | `mc-ai-tell-audit` |
| Finding a breakdown of a real work | `mc-case-studies` |

### 2.2 Six boundaries that are most easily confused (★ memorize each)

| A ⇄ B | Dividing line |
|---|---|
| `mc-form` ⇄ `mc-arrangement-arch` | **form governs what the form is (theory); arrangement-arch governs why this song is cut this way (decisions)** |
| `mc-rhythm-groove` ⇄ `mc-rhythm-section` | **groove governs what the rhythm itself is; rhythm-section governs how to play it so it sounds human** |
| `mc-texture-layering` ⇄ `mc-mix-intent` | **texture is solved by "rewriting" (change register / reduce notes / alternate); mix-intent is solved by "remixing" (frequency carving / sidechain / dynamics). Anything rewriting can solve must not be left to mixing** |
| `mc-orchestration` ⇄ `mc-sound-design` | **orchestration governs real instruments and their blend; sound-design governs the design of synthesized timbres** |
| `mc-sound-design` ⇄ sound (sound effects, Foley) | this library's sound-design is **musical timbre**; "sound design" in the film sense (effects / Foley / space) is the job of the **sound** function. Same name, different work |
| this library ⇄ lyricists | **everything about the words belongs to the lyricist**, including word-to-melody alignment (syllable splitting, extra syllables, inverted syllables, xieyin). That is the words' own workflow; this library reads the same song's lyrics (`meta.upstream.lyrics`); for the shared six-field ownership of who decides and who reads, see §5.1 |

### 2.4 ★ Style blending: not an even mix, but signing off by dimension

**Latin substyle routing:** `mc-style-latin` is an L3 index to specific genre skills. When salsa, bachata, dembow, cumbia, samba, regional mexicano or other Latin idioms are requested, read the corresponding `mc-style-latin-*` child. For deliberate Latin crossover read `mc-style-latin-fusion` as well. Historical Afro-Cuban and Brazilian drum notes do not override regional substyles. The existing global `meta.style_layers[].owns` contract is not section-local: state deliberate sectional handoffs in `form[].note`, `form[].events` and `meta.fusion_note` instead of adding new schema keys.


> ★ **Boundaries are a division of labor, not a prohibition.** The purpose of isolation is to make sure every choice has someone signing it off, not to lock a style down. When writing a J-Pop spec you may borrow a city-pop ura-chord (backdoor chord) in passing, or when writing a Chinese-style piece the bass may take an 808 from hip-hop. As long as you write one sentence in `style_layers` / `fusion_note` explaining why, that is a legitimate blend; **slight bleed is entirely acceptable**. What really must be guarded against is "nobody chose it, so it defaulted to that."

**Contamination isolation ≠ prohibiting blends.** The two differ on exactly one point:

> **A blend is a choice that was written down; contamination is a choice nobody made.**
> A song that blends rap and Chinese style (for example Wang Sulong's "Peach Blossom Fan" (桃花扇)) is entirely valid, provided the spec can state **which dimension belongs to whom**.

**How**: `meta.style_layers` holds a division-of-labor table (schema §1.1.1): one `base` plus several `overlay`s, with each layer stating which dimensions it `owns`:

| Dimension | Division in a Peach Blossom Fan-style piece (illustrative) |
|---|---|
| `harmony`, `melody`, `color_instruments` | Chinese style (pentatonic melody, folk-instrument samples as a color layer) |
| (complete division in `mc-style-hiphop` §8.1) | |
| `groove`, `low_end`, `vocal_delivery_verse` | hip-hop (groove, 808, verse flow) |
| `vocal_delivery_chorus`, `form` | Chinese-style sung chorus; the structure is still verse/chorus |

★ `owns` is a **closed set**; it may only be chosen from these fourteen:
`harmony` `melody` `groove` `low_end` `fill_policy` `instrumentation` `color_instruments` `timbre` `arrangement_hook` `vocal_delivery` (may be split into `vocal_delivery_verse` / `vocal_delivery_chorus`) `form` `mix`.
Anything being allocated that is not in the table goes under the closest match, with one sentence in `fusion_note` explaining it. **Do not invent new names.**

**Three rules** (self-check item 18):
1. **Each dimension has exactly one owner.** If two layers both claim `groove`, two defaults are stacked on top of each other and nobody chose.
2. **Each layer owns at least one dimension.** Otherwise it is merely read and does nothing.
3. **`fusion_note` states in one sentence why this combination holds.** If you cannot say it, it is forced together.

**How to use each L3's porting table**: what an overlay brings in is exactly the items its porting table marks as "not portable / will be recognized". **That recognizability is what you want.** But every item brought in must be signed off in `owns`, and you must check whether the base style's porting table allows giving up that dimension. For example, the city-pop porting table says a rushing bass can be ported; when the base is city pop, handing `groove` to someone else needs careful thought.

**On routing**: a blended brief should **read all of the L3 skills it names**; that is not contamination. Reading a style that was **not named** is what counts as contamination.

### 2.3 Things outside this package

| Content | Which function owns it |
|---|---|
| EQ frequencies, compression ratios, reverb parameters, bus chain, mastering | **Sound (mixing, mastering)**; this package only provides the `mix_intent` intent |
| Film sound effects, Foley, ambience, spatial design | **Sound** (recording, sound effects) |
| Score structure that follows picture, cue sheets, spotting | **Scoring** (writing music for picture) |
| Lyric writing, rhyme, imagery, narrative person | **Lyricist**. ★ **Three cases for words**: if the user did not mention words, they are optional; if you output some, record an entry in `checks.exemptions` saying "words not produced by the lyric workflow". If the user explicitly wants **pure music / light music / instrumental**, add not a single word and leave `vocal` empty. If the user **explicitly wants words**, you must produce them: if lyrics for the same song exist (`meta.upstream.lyrics`), follow them; if not, write them per this library's `mc-vocal-direction` and record an exemption. When only indicating vocal rhythm (rap flow, syllable counts per chorus line), use placeholder syllables (da-da / la-la) or X marks |
| Business workflow (pitch competitions, guide vocals (kari-uta), copyright, revenue splits) | Out of scope |

---

## 3. ARR-SPEC: this library's only handoff artifact

**The full specification is [ARR-SPEC.schema.md](ARR-SPEC.schema.md) (v1.0) in this skill directory; the blank template is [ARR-SPEC.template.yaml](ARR-SPEC.template.yaml); the backend capability profile is [backends.yaml](backends.yaml).**
★ **Before writing a spec sheet, Read the template and fill in its field names as given.** In testing, without looking at the template the agent invented its own fields (`intent.scene/borrow`, and `push_pull` written as a string).
(These three files are the entire "format" this library ships with. Beyond reading them, no tools are needed.)

### 3.1 One artifact, four uses

| Use | How it is used |
|---|---|
| **External handoff** | The one document that mixing engineers, musicians, lyricists and other departments read (§5) |
| **AB test subject** | Change one field → regenerate → compare. **Variables are controllable** |
| **Compile source** | `mc-render-compile` compiles it into a Suno prompt / YuE input / MIDI |
| **Acceptance baseline** | Compare the generated output field by field against it, to see how much the backend followed |

★ Points two and four are the key ones: **without a spec sheet there are no controllable experiments, and without controllable experiments you can only rely on feel.**

### 3.0 ★ The 20 self-checks after writing

**This library requires no tools on the user's machine**: no lint, no scripts, no assumed Python or Node.
After writing the spec sheet, go through the 20 items below one by one yourself, and write the results into `checks.self_audit`.
★ **These are criteria, not iron rules.** If an item fails, either fix it, or state in one sentence why this song should be that way.
A deviation with a stated reason is a legitimate choice; **no single item will "block" the compile that follows.**
★ Do not write scripts to do the checking (in testing, some agents did this and wasted many rounds). All 20 items can be judged by eye.

| # | Self-check question | Field checked |
|---|---|---|
| 1 | Are all four `intent` items filled? Does `reference_pair` have exactly 2 items, each stating which point is borrowed? | `intent` |
| 2 | Do the sections' `start_bar` values chain end to end? (previous start + bars = next start) | `form` |
| 3 | Is at least one section's `bars` not a multiple of 8? | `form[].bars` |
| 4 | Does the key set of `energy_curve` equal the id set of `form`? (no more, no less) | `energy_curve` |
| 5 | Does the energy curve drop at least once? | `energy_curve` |
| 6 | Is `subtraction_events` ≥ 1? | `subtraction_events` |
| 7 | Does every instrument have an `entry`, and does at least one have an `exit` that is not `end`? | `roster` |
| 8 | Is `arrangement_hook.what` non-empty? | `hooks` |
| 9 | Does at least one section other than Intro/Outro have a non-diatonic chord or a key-change marking? (In minor, `bIII`／`bVI`／`bVII` are the key's own diatonic chords and do not count.) | `form[].harmony` |
| 10 | Is `fill_policy.bars` not an arithmetic sequence with common difference 4? | `groove` |
| 11 | Does at least one `push_pull` item have `offset_ms ≠ 0`, and is each item a `{part, offset_ms, note}` dictionary? | `groove` |
| 12 | Does `width_map` take at least two values? | `mix_intent` |
| 13 | Is `style_prompt` non-empty and free of epic/emotional/beautiful? If `section_tags` is filled in by hand, does it match the number and order of `form` sections? (It is derived from `form[].name` and may be left blank.) | `render.suno` |
| 14 | Does `Σbars × beats per bar ÷ tempo × 60` deviate from `target_duration` by ≤ 10%? | `meta` |
| 15 | With vocals, does `dynamics_by_section` take at least two values? (Skip for instrumental works.) | `vocal` |
| 16 | With vocals, is `chorus_variation` non-empty? (Skip for instrumental works.) | `vocal` |
| 17 | With multiple styles: exactly one base; each dimension has only one owner; each layer has at least one dimension; `fusion_note` non-empty? | `meta.style_layers` |
| 18 | Are `material.motif` and `stated_in` non-empty; is `development` filled for every section; is `new` less than half; at least one section `repeat` or `recap`; are the chorus passes not all `new`? | `material` `form[].development` |
| 19 | Are chord spellings all ASCII, with suffixes from the closed set (`maj7` `m7b5` `dim`; do not write △ ø ° ♭ ♯ ×)? | `form[].harmony_letters` `harmony` |
| 20 | Is `key` in the form "tonic major/minor"; is `mode` within the enumeration; are section names within the closed set; is `subtraction_events[].at` a structure like `{section, bar_offset}` rather than a sentence? | `meta` `form[].name` `subtraction_events` |

**YAML self-checks** (where agents most often break things):
- Under the `- {…}` entries of list fields (`roster` / `sound_stage` / `push_pull` / `emotional_arc` …) you **may not attach a `note:` key**. For a comment, use a sibling `xxx_note:` key or `#`.
- A space after each colon; quote values that contain colons; uniform two-space indentation.

### 3.2 What to do when a self-check fails

**A failing item usually points to a skill you have not read**, rather than something to force-fill:

| Failing item | Most likely unread skill |
|---|---|
| 1 (intent incomplete) | this skill's §1 S0. **Go back and think it through; do not force-fill** |
| 2, 3, 14 (sections and duration) | `mc-arrangement-arch` §4 |
| 4, 5 (energy curve) | `mc-arrangement-arch` §2 |
| 6 (subtraction event) | `mc-arrangement-arch` §3 |
| 7 (lineup entries and exits) | `mc-arrangement-arch` §5 |
| 8 (arrangement_hook) | `mc-arrangement-arch` §7 |
| 9 (harmonic monotony) | `mc-harmony`, `mc-modulation` |
| 10, 11 (fills and groove) | `mc-rhythm-section` §3, §8 |
| 12 (constant width) | `mc-mix-intent` §2 |
| 13 (incomplete compile) | `mc-render-compile` |
| 15, 16 (vocals) | `mc-vocal-direction` §1, §4 |

**Exemption rule**: record it in `checks.exemptions`, and **a reason is required**.
A silent skip = unfinished work.

### 3.3 ★ Backend default comparison table

**Without instructions, backends slide toward the left column. The corresponding ARR-SPEC fields exist to pull them back.**

| Backend default tendency | Counter field | lint |
|---|---|---|
| Sections of equal length, all multiples of 8 | `form[].bars` | #3 |
| Energy rises monotonically to the end | `energy_curve` | #5 |
| Fills the instruments in at the opening | `roster[].entry` | — |
| All instruments sound from start to finish | `roster[].exit` | #7 |
| Only adds, never subtracts | `subtraction_events` | #6 |
| A fill every 4 bars | `fill_policy.bars` | #10 |
| All parts strictly aligned to the grid | `groove.push_pull` | #11 |
| Vocal at a single dynamic level throughout | `vocal.dynamics_by_section` | #15 |
| Chorus repeated verbatim on each pass | `vocal.chorus_variation` | #16 |
| Vocal pitch perfect throughout | `vocal.pitch_policy` | manual item |
| Stereo width constant for the whole song | `mix_intent.width_map` | #12 |
| Dynamics flattened | `mix_intent.dynamics` | manual item |
| No non-vocal memorable hook | `hooks.arrangement_hook` | #8 |
| Duration always 3:30 | `meta.target_duration` | #14 |

---

## 4. Diagnostic path: the generated result feels wrong

**Check in this order; do not jump by intuition.**

```
Sounds "like AI"
 └─ First separate two questions: did the backend follow the spec (compliance rate), and does the output carry a machine fingerprint (AI-flavor flag)
     ├─ Low compliance → the backend did not follow
     │   ├─ Check backends.yaml: is this field's `honors` for this backend `none`?
     │   │   └─ Yes → not its fault. Switch backend (YuE2 has the strongest control) or accept
     │   └─ No → compile problem; check mc-render-compile
     └─ High compliance but still sounds like AI → the spec itself is not enough
         └─ Go through the checklist in mc-ai-tell-audit
```

### 4.1 Specific symptom → skill

| Symptom | Check first |
|---|---|
| Flat, no contour | `mc-arrangement-arch` §2 energy curve |
| Muddy, blurry | `mc-texture-layering` §4 → **check the sustained sounds first, not the drums** |
| The lead does not stand out | `mc-texture-layering` §3, the four depth cues |
| Mechanical, too precise | `mc-rhythm-section` §2 + `mc-vocal-direction` §4 |
| Sounds fine but cannot be remembered | `mc-arrangement-arch` §7: is `arrangement_hook` empty? |
| The second chorus pass is the same as the first | `mc-arrangement-arch` §6 + `mc-vocal-direction` §1④ |
| Vocal buried in the accompaniment | **check pitch first** (`mc-vocal-direction` §4.1), then the frequency bands |
| Bass disappears on a phone | `mc-sound-design` §6, difference tones |
| Ending is abrupt / just fades out | `mc-arrangement-arch` §8, three kinds of ending |
| Technically clean but the emotion is wrong | `mc-mix-intent` §3.1: was `mood` left unwritten? |

### 4.2 ★ The two numbers must not be confused

| | What it asks | How it is computed |
|---|---|---|
| **Compliance rate** | How much the backend followed the spec | Check field by field against the spec by listening or looking; the 0–100 reference lines are in §6.3 |
| **AI-flavor flag** | Whether the output carries a machine fingerprint | The checklist in `mc-ai-tell-audit`, counted independently |

**A compliance rate of 100 can very well be full of AI flavor**, which means the spec itself reads like AI.
Conversely, a compliance rate of 40 that still sounds good means the backend did well on its own, but **you cannot reproduce it**.

---

## 5. External interfaces

**This library governs a song's composition and arrangement decisions** (key, tempo, sections, harmony, thematic material, who enters and exits when, the energy curve, how it is sung, and what the mix must achieve). The output is an ARR-SPEC. It does not assume who the downstream is or what tools they use. Externally it communicates only through the spec: the fields it hands over, the upstream fields it reads if present (§5.2), and `messages` (§5.3). For how to read the fields, see `ARR-SPEC.schema.md` §5.

| Function | What is not in this library | What it is handed |
|---|---|---|
| Lyricist | How words are written: rhyme, imagery, narrative person; how words are fitted onto notes (syllable splitting, extra syllables, inverted syllables, xieyin) | Shared six fields (§5.1); `vocal.phrasing／breath_points`, `hooks.vocal_hook`, `intent.emotional_arc`, `form[].melody_register` |
| Sound (mixing, mastering) | EQ frequencies, compression ratios, reverb parameters, bus chain, mastering; recording; film-sense sound effects and Foley | `mix_intent` (intent only), `roster`, `depth_map`, `spectrum_budget`, `subtraction_events`, `vocal.pitch_policy／stacking`; when `deliverable` includes `stems`, hand over the stems |
| Scoring (music for picture) | Structure that follows picture: spotting, cue sheets, which frame to enter on | `meta.tempo／tempo_map／target_duration`, `form[].start_bar／bars`, `material`, `hooks.arrangement_hook`, `energy_curve` |
| Editing | Placing the music against picture: where to cut, shorten, and seams | The same timing fields as above, `subtraction_events`, stems |

Shot design reads the tempo and section timing at the playback point; once handed off, any change must first be sent as a message. Before commercial use, check the `license` in `backends.yaml` (producers and on-set use). The convention for converting bars to seconds is in schema §5.1.

### 5.1 Six fields shared with the other side of the song

`form[].id` / `form[].bars` / `form[].name` / `meta.tempo` / `meta.key` / `vocal.persona`. Both sides use the same section ids.

- **Whoever goes first decides.** Music first, lyrics second: this library decides and writes into its own fields. Lyrics first, music second: read them in unchanged from `meta.upstream.lyrics.shared` and treat them as locked items; the lyrics' syllable count and phrasing in turn constrain `form[].bars`.
- **Do not change these six items when working second.** If the words cannot fit these bars, or the key or tempo cannot be sung, write a `messages` entry (`to: lyrics`) saying which item to change and why. Once the other side accepts and changes its own spec, this library re-reads it.
- When only the music side exists and there are no lyrics, this library sets these six items itself.

Full rules and original text: schema §5.4.

### 5.2 Upstream: read if present

It does not matter where `meta.upstream.brief／lyrics／picture` comes from: read it if present (in lyrics-first mode the six shared items are locked). If absent, follow this library's own analysis: S0 starts from the brief; with no lyrics, use the three cases in §2.3; with no picture duration, set the duration yourself. Do not rewrite upstream fields that are already filled. On conflict, write this library's field as it stands, then send a message to the originating function.

### 5.3 `messages`: how to send and receive

- **Receive**: at the start of S0 and before each spec change, read the entries with `to: music`, and hand each to the owner of the field named in `about` (§2.1). Mark it `accepted` if you changed the spec, `rejected` if not, with `reply` stating what changed or why.
- **Send**: for example `{from: music, to: sound, about: "mix_intent.dynamics", says: "The D section sitting 6 dB below C2 is the only large drop; please keep it through mastering", status: open}`. `to` takes `lyrics`, `sound`, `editing`, `shot-design`, `writing`, or `production`.
- **Do not wait**: if no reply arrives, treat it as none. `open` does not block the self-check or stop a stage; deliver it as-is at handoff.

---

## 6. Three verification methods

### 6.1 Check the boundary table when choosing skills

Before starting, list the skills this song needs to read, then check against §2 and each skill's boundary table for two things:

1. **Did you read the ones you should?** Every decision in the brief has a chosen owner.
2. **Did anything you should not read creep in?**
   — especially with L3 style layers: **reading one extra unnamed style skill is the easiest way to carry its defaults into this song** (named blends do not count; see §2.4)

> This is why every skill must have a "Boundary: what this skill does not govern" table.
> That table is there for choosing skills, not only for people to read.

### 6.2 Text-layer A/B

**Fix the judging criteria before looking at results.** Change one field → regenerate → blind comparison.
Once the results are in, do not change the criteria, or you will unconsciously tune them toward the one you have already seen.

Align the levels before comparing loudness, then compare content. If one version is simply louder, the ear tends to judge it better, and this bias quietly replaces the judgment of "which field took effect" with "which version is louder" (p0299-p0300). If the loudness or overall density of the two generated results does not match, level those two first before the paired comparison; otherwise the field's real effect is drowned out by the loudness difference.

### 6.3 Compute first, then listen (compliance rate)

See S7 in §1 and §4.2.

★ **Zero-point calibration** (reference values, to convey the scale, not a delivery threshold): take a City Pop spec (112 BPM, 10 sections, 114 bars) and compare it against three unrelated, well-produced Chinese-language finished tracks. Field-weighted scoring gives **63–66**, so we use **82 / 70** as the reference lines for "followed well / barely", not 60.
When comparing field by field, the compliance rate is one judgment made after the comparison; it need not be computed as a number.

---

## 7. Directory map

```
Shipped with the package (what the user receives is exactly these, all plain text):
  skills/<27 skills>/SKILL.md, reference.md
  skills/mc-workflow/ARR-SPEC.schema.md      ★ spec definition (v1.0)
  skills/mc-workflow/ARR-SPEC.template.yaml  blank template
  skills/mc-workflow/backends.yaml           ★ honors declarations for each backend
  skills/mc-workflow/example-*.yaml          filled examples (citypop / blend / counter-example)
```

---

## 8. Self-check for a finished song

- [ ] The four `intent` items were **thought out**, not filled in to pass lint
- [ ] The 20 items in §3.0 were gone through one by one, and every failing item has a stated reason
- [ ] Every field can name **which section of which skill** decided it
- [ ] The generated result was compared field by field, and it is known which items were never expected because of `honors: none`
- [ ] `mc-ai-tell-audit` has been run
- [ ] The ear came in **last**, and the A/B conclusion held on both listens

---

## Appendix: why this library is layered this way

**The criteria for splitting the library into sub-libraries and skills are four things that all differ: handoff artifact, referee, corpus, and evaluation method.**
**Split by workflow step, not by knowledge domain.**

So:
- "Harmony" is a **knowledge domain**, but it is cut into `mc-harmony` (when writing) and `mc-progressions` (when looking things up), because these are two workflow steps.
- "City pop" is a **style**; its drum patterns do not go into `mc-rhythm-section`, they go into `mc-style-citypop-rnb`, because "playing like a human" and "playing like city pop" are two workflow steps.
- "Mixing" spans three layers: the intent is in `mc-mix-intent`, the rewrite-type solutions are in `mc-texture-layering`, and the parameters are the job of **mixing**. This is because their referees differ (composition judgment / arrangement judgment / engineering judgment).

## Appendix: Sources

- **Howard & Angus, *Acoustics and Psychoacoustics***. §1.2 cites two psychoacoustic grounds for listening twice: repeated listening changes the processing strategy of the auditory system, and auditory adaptation follows sustained exposure. Page numbers refer to the Chinese translation.
- **Roey Izhaki, *Mixing Audio*** (a mixing guide). The loudness bias flagged in §6.2: the louder version tends to be judged "better", regardless of differences in content. Page numbers refer to that book.

Bibliographies cited by the library's other skills are listed under each one's "Appendix: Sources".
