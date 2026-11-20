---
name: mc-symbolic-score
description: Compiling ARR-SPEC into symbolic notation (symbolic score output) - ABC, MusicXML and MIDI from one emitter. Why the symbolic path matters (it is the only fully reproducible output and the only way YuE2 executes rather than guesses), the field-by-field mapping from spec to ABC headers and body, roman numerals to letter chords, multi-voice and per-part output, what each target format can and cannot carry, MIDI CC and velocity for expression, and the verification loop that catches a bad emit before it reaches a synth. Use when producing ABC for YuE2, when exporting MIDI or MusicXML for a DAW, when a deterministic reference render is needed for A/B, or when an LLM should write notation directly. Keywords: symbolic score, ABC, MusicXML, MIDI, uchikomi (MIDI programming), direct notation output, deterministic rendering.
---

# Symbolic Score Output

**One emitter, four target formats, two purposes.**

```
ARR-SPEC (+ lyrics from meta.upstream.lyrics)
   ↓  mc-symbolic-score
   ├─→ ABC        → YuE2's abc= input (★ lets the spec be "executed" rather than "hinted"); the native language of large models
   ├─→ MusicXML   → notation software / handing to musicians (lead sheet: melody, chords, lyrics, sections, dynamics, breaths)
   ├─→ MIDI       → DAW + sound source, deterministic rendering
   └─→ ChordPro   → guitarists, rehearsal (sections, chords, lyrics)
```

**Why one emitter**: ABC, MusicXML and MIDI can be converted into one another, ChordPro is a subset of the first three,
and all four carry the same information (pitch, duration, bar, key, time signature, dynamics, chords, lyrics).
**Splitting this into four skills would produce four inconsistent scores from the same spec.** The spelling of the executable fields in the spec is defined by these four formats (schema §1.3.1, §4), so the emitter does not need to translate notation.

## Which sections to read for each task

| Task | Read |
|---|---|
| Supplying a score to YuE2 | §3 ABC + §7 |
| Exporting MIDI for a DAW | §5 |
| Exporting MusicXML for musicians | §4 |
| A deterministic baseline for A/B | §2.2 |
| Converting roman numerals to letters | §3.3 |
| How to write expression/dynamics into MIDI | §5.2 |
| How to verify after emitting | §8 |

## Boundaries

| Not covered here | Where it lives |
|---|---|
| Prompts, section tags, backend selection | `mc-render-compile` |
| The content of melody, harmony, and counterpoint themselves | The L1 skills |
| Which sound source to use, sample library selection, keyswitches | Not covered by this package (the production environment decides which sound source to use); the meaning of MIDI CCs in orchestration is covered in `mc-orchestration` reference §5 |
| The meaning of MIDI CCs in orchestration | `mc-orchestration` reference §5 |
| The **groove** design of quantisation and velocity | `mc-rhythm-section` |
| Full notation specification (ties, slurs, ornament notation) | [reference.md](reference.md) |

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① Target format** | ABC / MusicXML / MIDI / ChordPro. **What each can carry differs** (§6); emit whichever ones are listed in `meta.deliverable` |
| **② Number of parts** | Only the main melody plus chords? Or the full score? |
| **③ Who will read it** | YuE2 / DAW / a person. **Determines the level of detail** |
| **④ Is this run a baseline** | If yes, **turn off all randomness** |

---

## 2. Why take the symbolic path

### 2.1 It is the only route by which the spec can be "executed"

Every other backend can only "hint". YuE2's synthesis step **takes ABC directly**:
once `form[].harmony_letters` / `meta.key` / `meta.meter` / `meta.tempo`
are compiled into ABC, **they are no longer suggestions**.

> Bypass the model's own symbolic-planning step entirely, and send our ABC directly into the synthesis step.
> Any host that supports YuE2 can connect this way (see `mc-render-compile` §8.2); how the wiring is done is up to the user's environment.

### 2.2 It is the only fully reproducible output

> **The same spec always renders identically.**

This makes it the **controlled baseline for A/B experiments**:
to find out exactly how much difference a single field makes, render two versions via the symbolic path, and the difference is 100% attributable to that field.
Generation backends cannot do this: even with a fixed seed, changing the prompt changes other things too.

### 2.3 The Japanese uchikomi (MIDI programming) workflow already has this shape

An LLM writes MIDI/MusicXML directly, which goes into a DAW, and a sound source is attached.
★ **This route has no vocals**: vocals must be connected separately (or use a generation backend for vocals and the symbolic path for the accompaniment).

---

## 3. ABC mapping

### 3.1 Header

| ABC field | Source | Example |
|---|---|---|
| `X:` | Fixed at 1 | `X:1` |
| `T:` | `meta.title` | `T:Night Drive` |
| `M:` | `meta.meter` | `M:4/4` |
| `L:` | Default unit note length (usually 1/8 or 1/16) | `L:1/8` |
| `Q:` | `meta.tempo` | `Q:1/4=112` |
| `K:` | `meta.key` | `K:D` |

★ **When `tempo_map` has several entries**: `Q:` takes the first entry; later tempo changes are written as inline `[Q:...]` fields within the bar.

### 3.2 Body

| Content | Source | Notation |
|---|---|---|
| Barlines | `form[].bars` / `start_bar` | `|` |
| Section markers | `form[].id` + `name` | ★ **Written as a comment `%` or a `[P:A1]` section marker**; see §7.2 |
| Chords | `form[].harmony_letters` | `"F#m7"`, placed in quotes before the note |
| Melody | Melody written at L1 | Standard ABC pitch notation |
| Repeats | Section repetition | `|:` `:|`. ★ **Use sparingly**; see §3.4 |

### 3.3 ★ Roman numerals → letters

**In ARR-SPEC, `harmony` is in roman numerals and `harmony_letters` is in letters; both are recorded.
When emitting ABC, use the letters, but you must verify that the two agree.**

**Verification step**: convert `harmony_letters` back into roman numerals using `meta.key`,
and compare chord by chord against `harmony`. **A mismatch means there is a typo in the spec**.
This is what the dual-notation convention in ARR-SPEC is actually for, not only for readability.

For the transposition table, see `mc-progressions` [reference.md](../mc-progressions/reference.md) §8.

### 3.4 ★ The repeat-sign trap

ABC's `|: :|` makes **two passes come out exactly identical**.
But lint #16 in this library requires **each pass of the chorus to be different**,
**so in most cases do not use repeat signs; write out every pass.**

★ **Exception**: sections that really are identical (for example an instrumental vamp) may use repeats.
**But choruses are always written out in full.**

---

## 4. MusicXML

**Purpose**: handing to notation software and to musicians.

**What it can carry beyond ABC**:
- Full staff layout and part assignment
- Performance markings (bowing, slurs, articulation)
- Dynamic markings (p / mf / f and gradual changes)
- Lyrics (aligned syllable by syllable)

**What it can carry beyond MIDI**: **notational intent** (the same pitch and duration, whether it is written as a sharp or a flat, as a triplet or a dotted note).

★ **When it is mandatory**: when the output of `mc-orchestration` is to be played by real musicians.
Neither ABC nor MIDI can express bowing or separate instrument parts.

---

## 5. MIDI

### 5.1 Basic mapping

| Content | Source |
|---|---|
| Notes | Melody and harmony |
| Tracks / channels | `arrangement.roster[]`, one instrument per track |
| Sound source mapping | `roster[].midi` (`{program, bank, channel}`, GM numbers; drum kit on channel 10); `render.midi.instrument_map` holds only notes such as VST names |
| Tempo | `meta.tempo` / `tempo_map` |

### 5.2 ★ Expression: velocity and CC

**MIDI's biggest advantage over ABC is that it can write continuous controls.**

| From ARR-SPEC | Written as |
|---|---|
| `arrangement.energy_curve` | **CC11 (expression) curve** + velocity layering |
| `vocal.dynamics_by_section` | CC11 on the vocal track (if there is a vocal sound source) |
| `groove.push_pull` | ★ **Actual offsets of note positions** (the only route that executes push_pull precisely) |
| `groove.quantize_policy` | Quantisation amount per track |
| `roster[].synth_params` | Sound source parameters or CC74 (brightness), etc. |

★ **The division of labour between CC7 and CC11 must not be mixed** (→ `mc-orchestration` reference §5.1):
- **CC7** sets this track's **position** in the orchestration
- **CC11** sets **how this phrase breathes**

Mixing them produces "the faders were pushed but the phrase is still lifeless".

### 5.3 ★ push_pull is exact on the symbolic path

The groove-related entries for the symbolic backend in `backends.yaml` are **exact**,
because note positions can be written precisely.
**This is the only reliable way to verify whether push_pull actually makes a difference**:
for the same score, produce one version aligned to the grid and one offset by push_pull, and compare them directly.

---

## 6. What each of the four formats can carry

| | ABC | MusicXML | MIDI | ChordPro |
|---|---|---|---|---|
| Pitch / duration / bars | ✅ | ✅ | ✅ | ❌ sections only |
| Key / time signature / tempo | ✅ | ✅ | ✅ | ✅ header directives |
| Chord symbols | ✅ | ✅ | ⚠ only as text events | ✅ |
| Lyrics | ✅ basic | ✅ full | ⚠ only as text events | ✅ |
| **Notational intent** (sharps/flats, triplet notation) | Partial | ✅ | ❌ | ❌ |
| **Performance markings** (bowing, articulation) | ❌ | ✅ | ⚠ only approximated via CC/keyswitch | ❌ |
| **Continuous control** (CC curves) | ❌ | ❌ | ✅ | ❌ |
| **Micro-timing offsets** (push_pull) | ❌ | ❌ | ✅ | ❌ |
| **Directly consumed by YuE2** | ✅ | ❌ | ❌ | ❌ |

★ **Conclusions**:
- **For YuE2 to execute → ABC**
- **For handing to a person → MusicXML**
- **For expression and rhythmic feel → MIDI**
- **For guitarists and rehearsal → ChordPro**
- **If you need several, emit several**, but **emit them all from the same spec**; do not write each separately

---

## 6b. YuE2 dialect: four lessons from testing (2026-09-17)

The same score, compiled from ARR-SPEC, sent into YuE2's abc input in three different forms gave very different results: `L:1/16` with a single voice produced 2:18 (the score is 4:00, and the model stopped early); deleting the section comments made it shorter (1:58); **switching to `L:1/32` ran the full 3:56**. So write the ABC for YuE2 in the way that YuE2 itself writes scores:

1. **`L:1/32`**: all durations are counted in thirty-second notes; a quarter note is written as 8, a dotted half note as 24, and a full-bar rest as `z32`. With `L:1/16`, the model treats the score as half as long and ends early.
   ⚠ But changing this alone is not enough: the same score in `L:1/32` ran to full length, yet whisper recognised not a single word (direct-output version 76%, model-written score 65%, this version 2%). The cause lies in the melody itself: each syllable is held too long, there are too few notes, and the register is an octave lower than in the model's own scores. The vocal line for YuE2 must look like the model's own writing: lowercase note-name range (roughly c to a), four to six notes per bar, and individual syllables rarely longer than one beat. Test result: moving the same score up an octave into the lowercase range raised whisper recognition from 2% to 47%; adding the `w:` lyric line brought it to 56% (direct output was 76%). This is the origin of points 5 and 6:
2. Include the `w:` lyric line (see point 6).
3. **Write the voice header as `V: Vocal clef=treble name="Vocal Melody" snm="Vocal"`**, and mark sections with `% intro` / `% verse` / `% pre-chorus` / `% chorus` / `% bridge` / `% outro` comments. The model's own score also has a `V: Ins` voice for instrumental phrases, and it runs to full length even with a single voice.
4. The `T:` title line may be empty. Standard key forms such as `K:D` are fine: when the model writes its own score it tends toward the relative minor (the same song it wrote as `K:Dm`), which does not matter.

5. **Write the vocal line in the lowercase note-name range** (ABC's c to a, roughly C5 to A5). In the uppercase range it sings indistinct vowels; this has nothing to do with the human vocal range, it is a habit of the model.
6. **Include the `w:` lyric line** (one syllable per note, with the number of syllables equal to the number of notes line by line). This gives better recognition than supplying words only in the lyrics field; keep the `w:` lines, and keep supplying lyrics in the lyrics field too.
7. To do: note density. The compiler currently assigns long held notes (dotted half notes, whole notes) to each syllable, whereas the model's own scores have four to six notes per bar, with individual syllables rarely longer than one beat. The remaining gap in recognition is most likely here.

Spec fields that ABC cannot express (subtraction events, reverb cut-offs, per-instrument entries and exits) can only be carried by the style text; see `mc-render-compile`.

## 7. Practical supply of scores to YuE2

### 7.1 Connection

```
[our ABC]  ──→  YuE2GenerateMusic  ──→  audio
                     ↑
   (YuE2GenerateABC is bypassed)
```

This skill is responsible only for the left-hand box: compiling ARR-SPEC into ABC text.
Why the right-hand connection should be made, why once it is made the spec is no longer merely a "hint",
and which hosts (official scripts, ComfyUI nodes) to wire it with, are covered in `mc-render-compile` §8.2.

### 7.2 Dialect now established

The ABC input of `YuE2GenerateMusic` has been fixed by testing, as set out in §6b: sections use `%` comments, chords use standard spelling in quotes (`"F#m7"`), and both the `V: Vocal` voice and the optional `V: Ins` voice run. The one remaining uncertainty is note density (§6b, point 7).

### 7.3 Official upstream skill

The official YuE2 repository includes `skills/yue2-music/` (in SKILL.md format, including "check musical invariants").

> ★ **Do not rewrite it.** We write the ARR-SPEC→ABC adapter, and for model-operation knowledge we refer to theirs.
> Its musical invariants should **align with or complement** our 20 self-checks.

---

## 8. ★ Verification loop after emitting

**Do not send an unverified score into a synthesiser.** Three steps:

| # | Check | How |
|---|---|---|
| **1** | **Syntax** | ABC → run through a parser; MusicXML → schema validation; MIDI → read back and check track count and duration |
| **2** | **Consistency with the spec** | ★ **Total bar count == `Σ form[].bars`**; key, time signature and tempo match; **letter chords converted back to roman numerals == `harmony`** |
| **3** | **Listen to a minimal render** | Quickly render with any sound source, **listening only to whether the structure is right**, not to the timbre |

★ **The bar-total check in step 2 is the most valuable**:
the most common bug in an emitter is a miscalculated section boundary, and in the audio that error shows up as "the structure is scrambled",
which is easily mistaken for the backend not following instructions.

**All three steps can be checked by eye.**

A route tested in practice (2026-09): ABC written to this skill's conventions (including `w:` lines, quoted chords, `%` section comments and `V:` headers) parsed with zero warnings in music21, and converted directly into MIDI and MusicXML. Rendering the MIDI with any GM sound is the minimal render in step 3, bypassing the generation model; tone-setting mismatches and melody density can be heard at this stage. Two cautions: music21 does not read `w:` lines, so MusicXML handed to musicians should be produced by a converter that reads `w:` (abc2xml, abcm2ps or similar), or the syllables should be attached by hand, one syllable per note; quoted chords are silent by default, so to hear harmony as a backing pad you must expand them yourself into a piano part.

---

## 9. Field mapping to ARR-SPEC (four export targets)

Every field in the spec has a destination (schema §4). The executable fields are mapped to the four formats as follows; this skill is responsible for the emission rules within them.

| ARR-SPEC field | ABC | MusicXML | MIDI | ChordPro | This skill |
|---|---|---|---|---|---|
| `meta.title` | `T:` | work-title | track name | `{title}` | §3.1 |
| `meta.key` / `mode` | `K:` (`K:Ddor`) | key fifths + mode | key signature meta | `{key}` | §3.1 |
| `meta.meter` / `meter_map` | `M:`, inline metre changes | time, per bar | time signature meta | `{time}` | §3.1 |
| `meta.tempo` / `tempo_map` | `Q:` | metronome / sound tempo | set_tempo | `{tempo}` | §3.1 |
| `form[].id` / `name` | `P:` or `%` comment | rehearsal mark + words | marker | `{start_of_verse}` etc. | §3.2 |
| `form[].bars` / `start_bar` | Barlines | measure number | tick | | §3.2; §8 step 2 |
| `form[].harmony_letters` | `"F#m7"` | harmony root / kind / bass; mapping in schema §1.3.1 | chord track or marker text | `[F#m7]` | §3.3 |
| `material.motif_abc` / `arrangement_hook.abc` | Embedded as-is | actual notes | actual notes | | §3 |
| `roster[].id` / `midi` | `V:` name | part-name + midi-instrument | track name + program change | | §5.1 |
| `roster[].entry` / `exit`, `form[].events` | `Z` multi-bar rest before the section | multi-bar rest | track content range | | §5.1 |
| `energy_curve`, `vocal.dynamics_by_section` | `!p!` `!f!` dynamic markings | dynamics (mapping in schema §1.5) | velocity scaling / cc11 | | §5.2 |
| `groove.push_pull` | None | None | tick offset (★ the only exact route) | | §5.3 |
| `vocal.breath_points` | `!breath!` | breath-mark | None | | §4 |
| `mix_intent.sound_stage[].pan` | None | pan on midi-instrument | cc10 | | §5.1 |
| `depth_map` | None | None | cc91 | | §5.2 |
| `meta.upstream.lyrics.sections[].lines` | `w:` lines | lyric, syllabic=single, Chinese one character per syllable | None | lyric lines | §3 |
| `render.yue.abc` | Body | | | | §7 |
| `render.musicxml` / `render.midi` / `render.chordpro` | | Target switch | Target switch | Target switch | §4 §5 |

Blocks that are intent only (`intent`, the prose of `material`, and most of `mix_intent` and `vocal`) travel with the file as text: ABC uses `%` comments, MusicXML uses miscellaneous, and MIDI uses a text event in the first bar. For what each of the four targets receives and carries, see schema §4.

---

## 10. Checks after emitting

- [ ] The target format was chosen according to §6, not out of habit (MIDI by default)
- [ ] **Total bar count == `Σ form[].bars`**
- [ ] Key, time signature and tempo match `meta`
- [ ] ★ **Letter chords converted back to roman numerals match `harmony` chord by chord**
- [ ] **Each pass of the chorus is written out**, without repeat signs (lint #16)
- [ ] In MIDI, **CC7 and CC11 are assigned their correct roles**
- [ ] If verifying push_pull, **produced both an aligned version and an offset version**
- [ ] **Ran the three steps in §8** before sending into a synthesiser
- [ ] When supplying a score to YuE2, the subset of the ABC dialect used is one that has been confirmed

---

## Appendix: Sources

- The three validation steps in §8 are manual; of these, the "total bar count" and "reverse roman-numeral check of chords" are pure data validation and do not require listening.
- ⚠ **Unconfirmed**: the YuE2 ABC dialect (§7.2)
- Notation details, the ABC syntax cheat sheet, and the GM instrument table are in [reference.md](reference.md).
