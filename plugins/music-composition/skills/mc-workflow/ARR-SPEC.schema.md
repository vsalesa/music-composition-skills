# ARR-SPEC v1.0 — Arrangement Spec: Specification

> The single hand-off artifact of this library. One artifact, four uses: external hand-off (external interface in §5), A/B test subject, compile source (→ Suno / YuE / MusicXML / MIDI / ChordPro), and the baseline for post-generation checks.
> Companion files: `ARR-SPEC.template.yaml` (blank template), `example-*.yaml` (filled-in examples); the 20 self-checks are in `mc-workflow` §3.0.
>
> **Every field has a destination** (executable / bridged / intent-only, see §4). Values in executable fields use forms that industry formats can read directly: chord spelling is all ASCII, time positions are structured, timbres carry GM numbers, and section names come from a closed set. There is one reason for this: once the spec is written, it must be convertible into a MusicXML lead sheet, a MIDI skeleton, ChordPro and ABC without human hands, for musicians, DAWs, guitarists and models.

## 0. Usage discipline

1. **Do not write `form` until all four `intent` items are filled in.** This is the required table before drafting; it plays the role of a playwright asking, before writing a scene, "what is the value turn of this scene?"
2. After writing, **run through the 20 self-checks** (§2). Any item that fails must be fixed or have its reason written down before compiling. These are criteria, not hard rules: a deviation with a written reason is a legitimate choice.
3. After generation, **first compare the output field by field against the spec** to measure compliance (reference lines in §3). If compliance is clearly low → revise the spec and regenerate; **do not rely on listening to rework it**.
4. Ears come in only at the last small step: once compliance passes, do blind A/B, paired comparison, and listen to the same pair twice to see whether the conclusion holds.
5. ★ **Items the backend cannot do do not count toward its score.** Each backend declares `honors: exact|hint|none` in `backends.yaml`; when computing compliance, items marked `none` are **excluded from scoring**, not scored as 0.
6. ★ **Executable fields use ASCII only.** Symbols such as `△ ♭ ♯ ° ø ×` look nice to people but MusicXML, ChordPro and ABC do not accept them. The spec stores `maj7 b # dim m7b5 x2`; the human-friendly display version is produced by the rendering layer.

---

## 1. Field specification

### 1.1 `meta`

| Field | Type | Required | Description |
|---|---|---|---|
| `spec_version` | str | ✅ | `"1.0"` |
| `title` | str | ✅ | Exported as MusicXML work-title, MIDI track name, ChordPro `{title}`, ABC `T:` |
| `style_layer` | str | ✅ | L3 skill id of the **base style** (e.g. `mc-style-citypop-rnb`); write `none` if the L3 skill has not been built yet |
| `style_layers` | list | ○ | Fill in **when styles are mixed**, see §1.1.1. Leave empty for a single style |
| `key` | str | ✅ | Fixed syntax: `<tonic> <major|minor>`, tonic with ASCII accidentals: `F# minor`, `Bb major`, `D major`. **All harmony symbols follow this key**. Exported as MusicXML fifths+mode, MIDI key signature, ChordPro `{key}`, ABC `K:` |
| `mode` | str | ○ | Fill in when the scale is not a natural major/minor; enum locked to the MusicXML values: `major` `minor` `ionian` `dorian` `phrygian` `lydian` `mixolydian` `aeolian` `locrian`. If `mode` is filled, the tonic in `key` is still the tonal center (`D major` + `mode: mixolydian` = D mixolydian) |
| `meter` | str | ✅ | e.g. `4/4`. Meter changes go in `meter_map`, not in sentences inside `form[].note` |
| `meter_map` | list | ○ | `[{bar: 1, meter: "4/4"}, {bar: 33, meter: "3/4"}, …]`, same shape as `tempo_map`; if present, `meter` takes the first entry. Exported as per-bar time signatures |
| `tempo` | int | ✅ | BPM |
| `tempo_map` | list | ○ | `[{bar: 1, bpm: 96}, …]`; if present, `tempo` takes the first entry. Exported as MIDI set_tempo events and MusicXML tempo marks |
| `target_duration` | str | ✅ | `mm:ss`. **Constrained by lint item 14**: must agree with the bar count × tempo calculation (±10%) |
| `deliverable` | list | ✅ | `full_mix` / `stems` / `midi` / `musicxml` / `chordpro` / `abc`; the last four correspond to the four export targets in §4 |
| `upstream` | obj | ○ | Upstream inputs to read if present: `brief` (source of the requirement), `lyrics` (lyrics for the same song), `picture` (picture to be matched). Fields and usage in §5.2; if absent, proceed with this package's own analysis |

#### 1.1.1 `style_layers` — Division of labor table for mixed styles ✦

**Mixing is not blending two styles evenly; it is assigning each dimension to one style.**

The values of `owns` form a **closed set**; choose only from the fourteen below:

`harmony`  `melody`  `groove`  `low_end`  `fill_policy`  `instrumentation`  `color_instruments`
`timbre`  `arrangement_hook`  `vocal_delivery` (or split into `vocal_delivery_verse` / `vocal_delivery_chorus`)  `form`  `mix`

If something to assign is not in the table, assign it to the closest one and add one sentence in `fusion_note`; do not invent new names.
Contamination and mixing differ on one point only: **mixing is a choice that is written down; contamination is a choice nobody made**.

```yaml
meta:
  style_layer: mc-style-chinese-pop        # base
  style_layers:
    - {skill: mc-style-chinese-pop, role: base,    owns: [harmony, melody, color_instruments]}
    - {skill: mc-style-hiphop,      role: overlay, owns: [groove, low_end, vocal_delivery_verse]}
  fusion_note: "sung chorus, rapped verses; folk-instrument samples only as a color layer, no rhythmic role"
```

| Field | Description |
|---|---|
| `skill` | L3 skill id |
| `role` | `base` (exactly one) / `overlay` (one or more) |
| `owns` | Dimensions owned by that style, fixed values: `harmony` `melody` `groove` `low_end` `instrumentation` `color_instruments` `timbre` `vocal_delivery` `vocal_delivery_verse` `vocal_delivery_chorus` `form` `mix` |
| `fusion_note` | One sentence on why this combination works |

**Constrained by lint item 17**: when there is more than one layer, there is exactly one `base`; **each dimension has exactly one owner** (two layers both claiming `groove` = no choice was made);
and each layer owns at least one dimension (otherwise it is only read and does nothing).

**How to use each L3's porting table**: what an overlay style brings in is exactly the items its porting table marks "❌ do not port / will be recognized". **That is the distinctiveness you want.**
But for every item brought in, sign it off in `owns`, and check whether the base style's porting table allows giving up that dimension.

### 1.2 `intent` — Required table before drafting (★ gate)

| Field | Type | Required | Description |
|---|---|---|---|
| `one_thing` | str | ✅ | **The one thing this song does**. One sentence, not two; no "both … and …". If you cannot write it, the idea is not yet clear |
| `reference_pair` | list | ✅ | **Exactly 2 items**, each `{track, borrow}`. `borrow` must state clearly **which point is borrowed** (e.g. "borrow only the space at the start of the intro"); **writing only the track name counts as unfilled** |
| `listener_situation` | str | ✅ | Where it is listened to, which listen this is, and how much attention is available. Determines how early the hook appears and the information density |
| `emotional_arc` | list | ✅ | `[{section, mood, value}]`. **Must contain a turn**; rising all the way means nothing was written |

> Why this gate exists: Suno's AI flavor is not a timbre problem; it is that **nobody made a choice**. These four items are where a choice is forced.
> This whole block is **intent-only**: no industry format stores it, so on export the whole block travels with the file as text (MusicXML's miscellaneous element, or a text event in MIDI bar 1), and the "why" is not lost.

### 1.2b `material` — Thematic material (★ owned by `mc-development`)

| Field | Type | Required | Description |
|---|---|---|---|
| `motif` | str | ✅ | Text description of the theme motif: interval contour, rhythmic pattern, length. Write it so that another person could recognize it |
| `motif_abc` | str | ○ | The same motif written in one to two bars of ABC (only `L:` and notes, no header). If present, MusicXML and MIDI can export the motif as actual notes; the symbolic path uses it as a seed |
| `character` | str | ○ | One-sentence character ("rushing, pushing upward") |
| `stated_in` | list | ✅ | Section ids where the motif is first stated; at least one |
| `development_mode` | str | ○ | What drives the song forward: `elaboration` / `expansion` / `contrast` (`mc-development` §5.1, the three routes proposed by Li Ji) |

### 1.3 `form` — Form table, one section per line

| Field | Type | Required | Description |
|---|---|---|---|
| `id` | str | ✅ | Globally unique, e.g. `I`/`A1`/`B1`/`C1`/`D`/`O`. Exported as MusicXML rehearsal mark, MIDI marker, ChordPro section label |
| `name` | str | ✅ | Closed set: `Intro` `Verse` `Pre-Chorus` `Chorus` `Post-Chorus` `Bridge` `Instrumental` `Solo` `Breakdown` `Drop` `Outro`. Suno section tags and the ChordPro `{start_of_verse}`/`{start_of_chorus}`/`{start_of_bridge}` are all derived from it and not stored separately. The precise definitions of these terms are in `mc-arrangement-arch/reference.md` §1 |
| `bars` | int | ✅ | Number of bars. **Constrained by lint item 3**: the whole song must not consist entirely of multiples of 8 |
| `start_bar` | int | ✅ | Starting bar. **Constrained by lint item 2**: sections must join end to end, with no gaps or overlaps |
| `harmony` | str | ✅ | Roman-numeral progression, ASCII: `"|VIm7 |IVmaj7 |I |V |"`. Chromatic prefixes `b`/`#` (`bVI`, `#IVm7b5`), secondary dominant `V/V`. For analysis and teaching; MusicXML 4.0 can store numerals, but software rarely reads them |
| `harmony_letters` | str | ✅ | The same progression in letter symbols: `"|F#m7 |Dmaj7 |A |E |"`. **Dual notation is a hard convention of this library**. Spelling in §1.3.1, **constrained by lint item 19**. Exported as MusicXML harmony, ChordPro `[F#m7]`, ABC `"F#m7"`, and the MIDI chord track |
| `melody_register` | str | ○ | `low` / `mid-low` / `mid` / `mid-high` / `high`. There must be contrast between sections. The actual range can be added as `melody_range: "A3-E5"` (ASCII note names with octave); if present, exported as a range hint for the part |
| `development` | str | ✅ | ★ What this section does with the thematic material. Closed set: `repeat` (verbatim or with a changed ending) / `sequence` / `extend` / `contract` / `fragment` / `vary` / `augment` (stretched or compressed) / `counterpoint` / `new` (new material) / `recap`. Can be written `"vary+extend"` for a primary and a secondary technique. **Constrained by lint item 18**. Technique definitions in `mc-development` |
| `energy` | int | ✅ | 0–10. Same source as `arrangement.energy_curve`; repeated here for readability |
| `events` | list | ○ | Lineup events occurring in this section, fixed values `<roster_id>_in` / `<roster_id>_out`, e.g. `[drums_in, bass_in, gtr_out]`. Cross-checked against `roster[].entry/exit` |
| `note` | str | ○ | **Asymmetric design goes here**, e.g. "second phrase is 6 bars, breaking the integer-8 pattern". Meter changes do not go here; they go in `meter_map` |

#### 1.3.1 Chord spelling (★ lint item 19)

One pair of vertical bars per bar. Multiple chords in one bar are separated by spaces and divide the beats evenly; if the division is uneven, write the beat count after the chord: `|Em7(3) A(1) |`. `%` repeats the previous bar. To repeat a whole passage, write `x2` at the end of the string.

Root: `A`–`G` with `#` or `b`. Slash bass: `/E`. The quality suffix is a closed set; the right-hand column is the kind used when exporting to MusicXML:

| Notation | Meaning | MusicXML kind |
|---|---|---|
| (empty) | major triad | major |
| `m` | minor triad | minor |
| `5` | power chord | power |
| `dim` | diminished triad | diminished |
| `aug` | augmented triad | augmented |
| `sus2` `sus4` | suspended 2nd / suspended 4th | suspended-second / suspended-fourth |
| `6` `m6` | major 6th / minor 6th | major-sixth / minor-sixth |
| `69` | six-nine | major-sixth + degree 9 |
| `7` | dominant 7th | dominant |
| `maj7` | major 7th | major-seventh |
| `m7` | minor 7th | minor-seventh |
| `mMaj7` | minor-major 7th | major-minor |
| `m7b5` | half-diminished | half-diminished |
| `dim7` | diminished 7th | diminished-seventh |
| `aug7` | augmented dominant 7th | augmented-seventh |
| `7sus4` | dominant 7th suspended 4th | suspended-fourth + degree 7 |
| `9` `maj9` `m9` | ninth chords | dominant-ninth / major-ninth / minor-ninth |
| `11` `13` | eleventh, thirteenth | dominant-11th / dominant-13th |
| `add9` `madd9` | added ninth | major / minor + degree add 9 |
| `7b9` `7#9` `7#11` `7b13` | altered dominant 7ths | dominant + degree alter |

Notations not in the table (`△`, `ø`, `°`, `M7`, `-7`, `Δ`) are all treated as misspellings. If the sound you want is not in the table, choose the nearest one and explain it in `note`.

### 1.4 `arrangement`

#### `roster` — Full instrument roster

Every instrument must be specifiable: which frequency band it occupies, when it enters, and when it exits. **An instrument whose exit cannot be stated is usually the one that flattens the arrangement.**

| Field | Required | Description |
|---|---|---|
| `id` | ✅ | Unique; `mix_intent`, `form[].events` and `render.midi` all reference this id. Exported as MusicXML part-name, MIDI track name, ABC `V:` name |
| `instrument` | ✅ | Specific instrument / patch, not a category word such as "synth". A human-readable name |
| `midi` | ✅ (when `deliverable` includes `midi`/`musicxml`) | `{program: 0-127, bank: 0, channel: 1-16}`, GM program number. Drum kit `channel: 10`. This is the single authoritative place for export; `render.midi.instrument_map` holds only notes such as VST names |
| `role` | ✅ | `groove` / `low end` / `harmonic pad` / `texture` / `melody` / `color` / `memory hook` |
| `band` | ✅ | Main frequency band occupied. **Use one of four bands** (`low` / `mid-low` / `mid-high` / `high`, with split points at 250 Hz / 2 kHz / 6 kHz) or a specific range such as `"1-3 kHz"`. Cross-checked against `spectrum_budget` |
| `entry` | ✅ | Section id where it enters |
| `exit` | ✅ | Section id where it exits, or `end`. **Constrained by lint item 7**: at least one instrument's `exit` is not `end` |
| `timbre` | ○ | **For text backends**: a description of the timbre: material, era, reference instrument. Do not write knob values |
| `synth_params` | ○ | **For parameter backends**: the same timbre. ★ Must be **from the same source** as `timbre` (both generated from the answers to the "four timbre questions"); different sources cause the text backend and the MIDI backend to sound like two different songs. Those four items that map to MIDI controllers use GM2 numbering: cutoff `cc74`, resonance `cc71`, attack `cc73`, release `cc72`, values 0–127 |
| `note` | ○ | |

#### `depth_map` — Three layers of depth ✦

`{roster_id: foreground|midground|background}`. Listeners judge what is foreground by four cues: "higher, louder, faster, faster rate of change".
**Of these only "louder" can be adjusted at mixing**, so depth must be planned at the arrangement stage.
See `mc-texture-layering` §2–§3. On export, roughly mapped to MIDI reverb send cc91 (low for foreground, high for background).

#### `spectrum_budget` — Frequency-band budget

`[{band, owner, competitors, resolution}]`. State which two parts compete for a band and how they divide it: **yield** / **separate registers** / **alternate**.
**`resolution` must be one of these three**. This is where the concept "arrangement = spectrum budget" lands, and it is the precondition for `mix_intent` being intent-only.

> Acceptance criterion: the band ownership drawn out should be **neither overlapping nor gapped** (Izhaki, Figure 6.2 b).
> Merely avoiding overlap leaves holes; merely being continuous makes things muddy.

#### `bass_kick_relation` — Relationship between bass and kick ✦

`{mode: locked|call-and-response|interlocking, detail}`. Choose one of three and state which one applies.

- **Locked**: the bass rhythm follows the kick and coincides fully → strong, firm attacks
- **Call-and-response**: the bass avoids the kick's rhythmic points → suits electronic dance music where the kick covers the low end
- **Interlocking**: coincides when needed, separates when not → **default recommendation**, but requires that you can state, bar by bar, where they coincide and where they separate; if you cannot, fall back to locked

#### `energy_curve`

`{section id: 0–10}`. The set of keys must equal the set of ids in `form` (lint item 4).
**Constrained by lint item 5: there must be at least one drop.** Monotonic increase is Suno's strongest default.
(Measured: 62/62 real arrangements contain a drop: a **hard rule**.) In reference renders, folded into velocity scaling or cc11.

#### `subtraction_events` — Subtraction events (★ at least 1)

`[{at, what, why}]`. Typical examples: removing the drums before the second chorus so only vocals and one instrument remain; cutting the low end for one bar.
**Constrained by lint item 6.** Real records create impact through subtraction; AI only adds.

`at` is a structured time position (§1.9), not a sentence: `at: {section: C2, bar_offset: -1, beat: 4}` means beat 4 of the bar before C2; `at: {section: D}` means the whole section. Descriptions such as "the last half-beat before entry" go in `what`; the position goes in `at`.

#### `hooks`

| Field | Required | Description |
|---|---|---|
| `vocal_hook` | ○ | `{where, shape}` |
| `arrangement_hook` | ✅ | `{what, first_at, recurs_at, abc}`. **A non-vocal memory point**: riff / signature timbre / recurring sound event. **Constrained by lint item 8**. Missing this item is the main cause of "sounds fine but is not memorable". `abc` is optional, same as `motif_abc`; if present, it can be exported as notation |

#### `groove`

| Field | Required | Description |
|---|---|---|
| `feel` | ✅ | `straight` / `swing16` / `shuffle` / `halftime` / `2:1` / `3:1`. MusicXML 4.0's swing element can store the first three; MIDI has no standard, so it is realized through the note values of the reference render |
| `quantize_policy` | ○ | `{part: percentage}`. ★ **Quantization is a per-instrument decision, not a global switch**: at least one part stays on the grid, and at least one does not |
| `push_pull` | ✅ | `[{part, offset_ms, note}]`. **Constrained by lint item 11**: at least one entry with `offset_ms ≠ 0`. Everything aligned to the grid is the root of a machine feel (measured 62/62, **hard rule**). Reference renders convert it into tick offsets according to tempo |
| `fill_policy` | ✅ | `{bars: [int], rationale}`. **Constrained by lint item 10**: `bars` must not be an arithmetic sequence with common difference 4 |

### 1.5 `vocal` — Vocal design

Corresponds to `mc-vocal-direction`. **The most consistent giveaway of AI vocals is "perfection"**: pitch is perfect throughout, dynamics are flat,
and every chorus is identical. About half of this section is about **asking for "imperfection"**.

| Field | Required | Description |
|---|---|---|
| `persona` | ✅ | **Who is singing**: gender, vocal range, texture, sense of era. Writing "female voice" alone counts as unfilled |
| `delivery` | ✅ | Breathy / full / mixed voice; tightness of articulation. **Can be a single string, or per-section `{section id: description}`**. Use executable terms: `bright` / `breathy` / `consonants pushed`. ★ **Do not write "sing louder"** (volume is the fader's job, not the singing's) |
| `dynamics_by_section` | ✅ | `{section id: 0–10}`. **Constrained by lint item 15**: must not be the same level throughout. Export to MusicXML dynamic marks follows this mapping: 0–1 `ppp`, 2 `pp`, 3 `p`, 4 `mp`, 5–6 `mf`, 7 `f`, 8 `ff`, 9–10 `fff`; the MIDI reference render uses velocity `40 + 8×value` |
| `phrasing` | ○ | `[{line, timing, why}]` which lines lay back (behind the beat) and which line anticipates the beat. ★ Judging whether a note rushes or lags depends on the position of the **vowel**, not the start of the syllable |
| `breath_points` | ○ | `[{section, line, after_syllable, note}]`: section id, line number (starting from 1), and the syllable within that line after which to breathe. Breathing is also space; its position must match the lyric's phrasing. Exported as MusicXML breath-mark |
| `ad_libs` | ○ | `[{at, what}]`, `at` uses the time position from §1.9; ★ evenly scattering them is forbidden |
| `chorus_variation` | ✅ | ★ How each pass of the chorus differs. **Constrained by lint item 16**. (The words may stay the same; the arrangement may not) |
| `stacking` | ○ | Harmony / doubling: how many layers, which lines they enter on, and which of the **four types** to use (full-voice above / close-harmony above / understated below / aino-te call-and-response). A double requires a **second performance**, not a copied track. Layers with actual pitches are exported as extra voices in MusicXML |
| `pitch_policy` | ○ | ★ Write **which positions retain a pitch offset**, rather than "correct to pitch". A vocal that sits too low will not come through even if the fader is pushed to the top; **a slightly sharp vocal has better carrying power**. Failure condition: sections with very dense arrangements should be corrected; the criterion is **accompaniment density**, not the section name |
| `register_arc` | ○ | Direction of the vocal range, consistent with `form[].melody_register` |

### 1.6 `mix_intent`

Write only **intent**, not EQ frequencies / compression ratios / mastering chain (those are the mixing engineer's job).
**Parameters influence each other** (raise vocal high-frequency → reverb tail lengthens → fader must be adjusted → compression parameters must be adjusted). Pinning a numeric value in the spec locks the mixing engineer out of the four steps that follow.
Everything in this block except `sound_stage` is intent-only.

| Field | Required | Description |
|---|---|---|
| `mood` | ✅ | ★ One sentence on what this mix must convey. **Has veto power over all other decisions**, and **appears early in the generation prompt** (the generation model is also a "mixing engineer who is only good at one style", and will pull the input toward the balance it has seen most often) |
| `sound_stage` | ○ | `[{id, pan, depth}]` left/right and front/back for each instrument. `pan` takes `-100..100` (negative left, positive right, 0 centered); exported as a linear mapping to MIDI cc10 0–127 and MusicXML pan -180..180. `depth` takes `foreground / midground / background`, the same enumeration as `depth_map`. ★ **Depth must be consistent within a group of instruments** (depth should be "consistent", not "balanced"). Positioning within the drum group belongs to `mc-rhythm-section`; this only fixes where the drum group as a whole sits |
| `focus_by_section` | ○ | `{section id: roster_id}`: which element must be the clearest in each section. ★ **Write the densest section first**; define the others relative to it |
| `ducking_map` | ○ | `[{section, who_yields, band, to}]`: in which section, which part yields which band to which other part |
| `deliberate_imbalance` | ○ | `[{from_bar, to_bar, what, why}]`. ★ **Must include the start and end bars**. An imbalance is an **event**, not a state; any entry without a bar range is treated as an error |
| `reference_tracks` | ○ | `[{track, aspect}]`. ★ `aspect` **must state which aspect of the reference is being used**; writing only the track name counts as unfilled. Note the mastering effect: the dynamic values of reference tracks are systematically compressed |
| `dynamics` | ✅ | `{target_DR_dB, notes}`. `notes` states "which section must be x dB quieter than the chorus" |
| `width_map` | ✅ | `{section id: narrow/medium/wide}`. **Constrained by lint item 12**: at least two different values |
| `loudness_target` | ✅ | e.g. `"-9 LUFS integrated"` |

### 1.7 `render`

#### `render.suno`

| Field | Required | Description |
|---|---|---|
| `style_prompt` | ✅ | Style description string. **Must not contain content-free adjectives such as `epic`/`emotional`/`beautiful`** (lint item 13, soft warning) |
| `section_tags` | ○ | Derived from `form[].name` (`[Intro]` `[Verse]` …) and generated at compile time, no need to fill by hand. If filled by hand, **the count and order must match `form` exactly** (lint item 13) |
| `exclude` | ○ | Negative prompt |
| `knobs` | ○ | `{model, weirdness, style_influence}` |

#### `render.yue`

`{genre_tags, structure, ref_audio, abc}`. YuE2 takes a genre-tag string plus structured sections,
**and can take an ABC score directly** (`abc=` parameter). This is the only path where the spec is **executed** rather than **prompted**.
`form[].harmony_letters` / `key` / `meter` / `tempo` are compiled directly into ABC. Compilation rules in `mc-symbolic-score`.

#### `render.midi`

`{instrument_map: {roster_id: {name, program, bank, channel}}}`. `program/bank/channel` come from the same source as `roster[].midi`, and the roster is authoritative; `name` holds notes that GM cannot express, such as a VST or sample-library name. If only a VST name is given, `program` must still be given as a fallback, otherwise the reference render has no sound.

#### `render.musicxml`

`{lead_sheet: true, parts: [roster_id, …]}`. If not filled, the default is a vocal lead sheet only: melody, chord symbols, lyric syllables, section marks, tempo, key and time signatures, dynamics, breath marks. Each roster id listed in `parts` adds a part (the part needs actual notes, which come from the symbolic path).

#### `render.chordpro`

`{transpose: 0}`. Sections are derived from `form[].name`, chords from `harmony_letters`, and lyrics from `meta.upstream.lyrics.sections` (§5.2).

### 1.8 `checks`

`self_audit: [ … ]`: manual items that the author ticks off one by one (automatic items are run by lint). The manual items are fixed as follows:

- [ ] `one_thing`, read aloud, is one sentence, not two things stitched together
- [ ] The points borrowed from the two references do not overlap
- [ ] `arrangement_hook` can be hummed without looking at the score
- [ ] At least one section's `melody_register` is clearly different from its neighbors
- [ ] Somewhere in the song there is a place where something that could be said is left unsaid (a rest); state where it is
- [ ] For each section, list who is the highest, loudest, fastest, and most dramatically changing; **the lead must hold at least two of these**
- [ ] If the low end is a sine wave or a very dark timbre, harmonics were added and **verified on a phone speaker** (the missing-fundamental / difference-tone problem)

`exemptions: [{rule, why}]`: exemptions. **An exemption must state its reason; silently skipping is not allowed.**

### 1.9 Writing time positions

Every field that states "where it happens" (`subtraction_events[].at`, `ad_libs[].at`, `deliberate_imbalance`, and `phrasing[].line` if it refers to a position) accepts only two forms:

- Absolute: `{bar: 40}` or `{bar: 40, beat: 3}`
- Relative to a section: `{section: C2}` (the whole section), `{section: C2, bar_offset: -1}` (the bar before C2), `{section: C2, bar_offset: 0, beat: 4.5}` (beat 4½ of the first bar of C2)

`beat` starts from 1 and may be fractional. Both forms convert losslessly into MIDI ticks and MusicXML bar numbers; sentences cannot be converted.

---

## 2. The 20 self-checks (SPEC-LINT)

Checked manually, one by one. **Failing = fix it or state a reason**; it does not forbid compilation.

| # | Check | Default it counters |
|---|---|---|
| 1 | The four `intent` items are non-empty; `reference_pair` has exactly 2 items and each `borrow` is non-empty | No choice was made |
| 2 | `start_bar` in `form` joins end to end, without gaps or overlaps | The spec contradicts itself |
| 3 | At least one section's `bars` is not a multiple of 8 | Every section is a multiple of 8 |
| 4 | The key set of `energy_curve` == the id set of `form` | The spec is incomplete |
| 5 | `energy_curve` has at least one drop | Energy rises monotonically |
| 6 | `subtraction_events` ≥ 1 | Only adds, never subtracts |
| 7 | Every `roster` item has `entry`; at least one item has `exit != end` | The lineup never changes from start to finish |
| 8 | `arrangement_hook.what` is non-empty | No non-vocal memory point |
| 9 | At least one non-Intro/Outro section's `harmony` contains an out-of-key chord or a modulation marker (in minor, `bIII`/`bVI`/`bVII` are diatonic chords of natural minor and do not count as out-of-key) | One loop all the way through |
| 10 | `fill_policy.bars` is not an arithmetic sequence with common difference 4 | Fills are formulaic |
| 11 | `groove.push_pull` has at least one entry with `offset_ms != 0` | Grid-locked |
| 12 | `mix_intent.width_map` has at least two different values | Constant stereo width |
| 13 | `render.suno.style_prompt` is non-empty; if `section_tags` is filled by hand, its section count and order match `form` | Incomplete compilation |
| 14 | `target_duration` deviates from `Σbars × meter ÷ tempo` by ≤ 10% | Duration is always 3:30 |
| **15** | `vocal.dynamics_by_section` has at least two different values | Vocal at one level throughout |
| **16** | `vocal.chorus_variation` is non-empty and states what changed on each pass | Chorus copied verbatim each time |
| **17** | When `style_layers` has more than one layer: exactly one base; each dimension has only one owner; each layer owns at least one dimension | Styles "blended evenly": two defaults stacked, and no one made a choice |
| **18** | `material.motif` and `stated_in` are non-empty; every `form[].development` is filled; the number of sections marked `new` is less than half; at least one section in the whole song is `repeat` or `recap`; not every chorus pass is `new` | Every section writes something new; no development, just piling up |
| **19** | Each chord in `harmony_letters` has its root, suffix and slash bass within the closed set in §1.3.1, all ASCII; `harmony` likewise ASCII | Spellings vary by writer; cannot be exported |
| **20** | `key` matches the `<tonic> <major|minor>` syntax; `mode` is within the enum; `meter` with the bar numbers of `meter_map`/`tempo_map` falls within the song; `form[].name` is within the closed set; `subtraction_events[].at` has the §1.9 structure | Executable fields were written as sentences |

**Failure conditions (must be written into `checks.exemptions`)**:

- Item 9: minimalist works (ambient / drone / single-chord vamp) may be exempt
- Item 11: `feel: straight` hard-grid electronic dance music may set the amount to 0, with a note that "grid-locking is this style's language"
  (Note that this does not conflict with the 62/62 hard rule: the hard rule says **a whole song must not have every part on the grid**;
  absolute quantization of the drum group is allowed, see `mc-rhythm-section` §2.0)
- Items 15 / 16: **for purely instrumental works with no vocals, the whole `vocal` section may be omitted**, and both items are then skipped automatically
- Item 18: **works that are entirely improvised or are ambient / drone with no thematic material**: write "no thematic material" in `material.motif` and explain it here; `development` may be all `new` or left empty
- Items 19 / 20: no failure conditions. These two check syntax, not judgment

---

## 3. Correspondence with measured quantities (how compliance is computed)

| ARR-SPEC field | Measured quantity on the generated audio | Judgment |
|---|---|---|
| `form[].start_bar` | Section boundary detection (seconds → bars) | Boundary hit rate, tolerance ±1.5 bars |
| `form[].harmony` | Per-bar chroma → chord template matching | Edit distance of the chord sequence |
| `meta.tempo` | Beat tracking | Relative error (tolerance 4%) |
| `groove.push_pull` | Mean onset offset relative to the grid | Whether sign and magnitude match |
| `energy_curve` | Per-section RMS | Spearman correlation with the spec curve |
| `roster[].entry/exit` | Per-track onset density | Event hit rate |
| `dynamics.target_DR_dB` | Crest factor / LRA | Absolute difference |
| (general AI-flavor item) | Temporal variance of spectral centroid | Below the threshold → judged as "one level throughout" |
| `width_map` | Per-section M/S ratio and correlation coefficient | Whether it varies with the sections |
| `target_duration` | Actual duration | Relative error |

Summing gives a **0–100 compliance score** (just compare field by field against this table; no need to compute a number).

> ★ **Zero-point calibration**: a City Pop spec (112 BPM, 10 sections, 114 bars) scored against this table lands at **63–66**, compared with three unrelated, well-produced Chinese-language commercial tracks.
> So we treat **82 / 70** as reference lines, not 60. These are reference values for understanding the scale, not delivery thresholds.
> This calibration value must be re-measured together with any change in weights: **changing weights without re-measuring the zero point = the data are not comparable**.
>
> ★ A pitfall we hit: moving weight from **discriminative** items (`boundaries`) to **non-discriminative** items
> (`energy_shape`, where unrelated tracks can still score 0.8) **raises everyone's score**, including the zero-point baseline.
> Add weight only to items that can discriminate.

> ★ **Backend capability**: items with `honors: none` are **excluded from scoring**, not scored as 0.
> Otherwise a backend that honestly declares "I cannot do stereo imaging" would score lower than one that pretends it can.

---

## 4. Field destinations: what can be exported and where

The spec is not a MusicXML or MIDI file; they store results, not reasons. But every field must have a stated destination, one of three kinds:

- **Executable**: exported losslessly to at least one industry format; value syntax follows the target format.
- **Bridged**: the industry format has no matching field, so an approximation is made with its existing mechanisms (dynamics, controllers, mute, text marks). Lossy; the spec remains authoritative.
- **Intent-only**: no industry format stores it. On export, the whole block travels with the file as text, so the "why" is not lost.

| Destination | Fields |
|---|---|
| Executable | `title` `key` `mode` `meter` `meter_map` `tempo` `tempo_map` `form[].id/name/bars/start_bar/harmony_letters` `melody_range` `motif_abc` `arrangement_hook.abc` `roster[].id/instrument/midi` `breath_points` `stacking` (when pitches are written) `render.midi/musicxml/chordpro/yue.abc` |
| Bridged | `form[].energy/events` `roster[].entry/exit/synth_params` `depth_map` `energy_curve` `subtraction_events` `groove.*` `dynamics_by_section` `phrasing` `sound_stage` |
| Intent-only | `style_layer(s)` `fusion_note` `intent.*` `material.motif/character/stated_in/development_mode` `form[].harmony/melody_register/development/note` `roster[].role/band/timbre` `spectrum_budget` `bass_kick_relation` `hooks.*.what` `fill_policy` the remaining items of `vocal` `the remaining items of mix_intent` `render.suno.*` |

The four export targets and their audiences:

| Target | For whom | Contents |
|---|---|---|
| MusicXML lead sheet | Musicians, notation software | Melody, chord symbols, lyric syllables, section marks, tempo, key and time signatures, dynamics, breath marks |
| MIDI skeleton | DAW | Tempo map, time signatures, section markers, per-track program numbers, entries and exits, pan, reference render |
| ChordPro | Guitarists, rehearsal | Sections, chords, lyrics |
| ABC | Large models, YuE2 | Melody, chords, lyric lines; see `mc-symbolic-score` |

Proprietary DAW project formats and DAWproject are not supported. `mix_intent` has no matching format: mixing intent is, in the industry, simply text.

`meta.upstream.lyrics.sections[].lines` (lyric lines) is exported as executable: as MusicXML lyric, as ChordPro lyric lines, as ABC `w:` lines. The remaining items of `meta.upstream` and `messages` are not exported; they travel with the spec only.

---

## 5. External interface

This spec records **the composition and arrangement decisions for one song**. This section is written for readers outside the spec (another department, another toolset, or another agent alike); it does not assume who is reading, and only agrees on the data: the fields handed off (§5.1), the upstream fields read when present (§5.2), the message channel `messages` (§5.3), and the six fields shared with the lyrics side (§5.4). The skills in this package exchange data only through these fields.

### 5.1 Fields handed off (by function)

**Read these conventions first**; every row in the table below is read in line with them:

- **Decisions and intent, not prescriptions.** The spec contains no EQ frequencies, compression ratios, or mastering chain, and no lyrics, no edit points for the picture; these are decided by each function. Most of `intent`, `vocal` and `mix_intent` are intent-only (§4).
- **Time positions are given in bars and beats** (§1.9), counting from 1. To convert to seconds: accumulate bar by bar using `tempo_map` (or `tempo` if absent) and `meter_map` (or `meter` if absent); one bar = beats per bar × 60 ÷ BPM (quarter note = one beat); with `form[].start_bar` joining end to end, the start and end seconds of each section can all be computed.
- **id**: `form[].id` is globally unique, and per-section fields and lyrics align on it; `form[].name` is a closed set and may repeat (C1 and C2 are both `Chorus`). `roster[].id` is the MIDI track name and the part name, and also the name used in `depth_map`, `spectrum_budget` and `sound_stage`.
- **Plan vs. measurement**: the spec is a plan; once audio returns, compare field by field per §3; a deviation whose reason is written in `checks.exemptions` is a deliberate choice; a field with `honors: none` is one that the given backend cannot do.

| Function | Fields read | How to interpret the fields |
|---|---|---|
| **Lyrics** | Shared six fields (§5.4); `form[].start_bar / melody_register / melody_range`; `vocal.phrasing / breath_points / chorus_variation`, `hooks.vocal_hook`; `intent.emotional_arc`; the melody produced by the symbolic path | **The section id is the column where words and music interlock**: lyrics are split by `form[].id`, one lyric line per phrase, one syllable per Chinese character. `breath_points` are breath positions (section, line, the syllable after which to breathe); the lyric's line breaks must match them; `melody_register / melody_range` mark which sections sit high, and words on high notes must survive being sung. `chorus_variation` is the arrangement side's change per chorus pass (the words may be the same; the arrangement may not); `emotional_arc` is the mood and turn for each section |
| **Sound** (mixing, mastering) | `mix_intent`; `roster`, `depth_map`, `spectrum_budget`, `bass_kick_relation`, `energy_curve`, `subtraction_events`; `vocal.stacking / pitch_policy`; `meta.deliverable` | **`mix_intent` is intent, not parameters**: EQ, compression, reverb, buses and mastering are decided by the mix. `mood` has veto power over other decisions; `deliberate_imbalance` carries start and end bars and is a deliberate event; the section gaps in `dynamics.notes` must survive after mastering. `spectrum_budget[].resolution` indicates that band conflicts have already been resolved in the arrangement; `depth_map` keeps depth consistent within a group of instruments. `subtraction_events` are deliberately left gaps: do not fill them through dynamics processing; the positions listed in `pitch_policy` deliberately retain pitch offsets and are not corrected to pitch |
| **Score** (scoring to picture: spotting, cues) | `meta.tempo / tempo_map / meter_map / target_duration`; `form[]`, `energy_curve`; `material`, `hooks.arrangement_hook`; `roster`, `meta.deliverable` | The song's **structure is set by its form**; duration is set by the song itself. When used against picture, section start and end seconds are computed from bars. `material.motif` and `arrangement_hook` are themes and memory points that can be reused. Section boundaries must follow the picture, and structure belongs to the score; this package only sets duration, tempo and bar count when `meta.upstream.picture` supplies a duration and hit points |
| **Editing** (where to cut, trimming, joins) | The time fields in the row above; `form[].events`, `roster[].entry / exit`, `subtraction_events`, `groove.fill_policy.bars` | Section boundaries are natural joins; `fill_policy.bars` are the bars where the fill occurs; `subtraction_events` are the impact sources of the arrangement (§1.4) and should be kept when trimming. If `deliverable` includes `stems`, deliver the stems |

Shot design reads `meta.tempo / tempo_map` and `form[].start_bar / bars` at shooting time: once handed off, changes will not line up with footage already shot, so write a message first (`to: shot-design`) before changing anything. Before commercial use, production and on-set staff check the `license` of the backends used, as listed in `backends.yaml`.

### 5.2 Upstream fields read when present

| Field | Contents | How this package uses it |
|---|---|---|
| `meta.upstream.brief` | Source of the requirement and its original wording (one brief line, one scene of a script, one row of a cue sheet); write `none` if absent | S0 starts reading here; this package still forms the four `intent` items itself |
| `meta.upstream.lyrics` | Lyrics for the same song, `{source, flow, shared, sections}`: `source` is the path to the lyrics spec or a note saying the words were supplied by the user; `flow` takes `composed-first` / `lyrics-first`; `shared` holds, for lyrics-first, the six items read in `{form: [{id, name, bars}], tempo, key, persona}`; `sections: [{id, lines}]`, where `id` equals `form[].id` | **For lyrics-first, `shared` items are locked** (§5.4); this package copies them as given. Word count and phrasing constrain `form[].bars` and the melody. `sections[].lines` are the lyrics used for compilation: the lead sheet, ChordPro, ABC `w:` lines, and the backends' lyric chunking all draw from here (`mc-render-compile` §5.3) |
| `meta.upstream.picture` | The picture to be matched, `{source, sec, hits: [{at_sec, what}], note}`: total duration in seconds and the moments to hit; for playback-timed work, written into `note` | `target_duration`, tempo, and `form[].bars` are set according to `sec`. `hits` are placed on a bar and beat, written into `form[].note` or `subtraction_events`. Section boundaries are still set by the form |

- **It does not matter who supplied them.** Read them if present; if absent, proceed with this package's own analysis: without `lyrics`, this package sets the six items itself, and whether to produce lyrics follows `mc-workflow` §2.3; without `picture`, this package sets the duration itself.
- Upstream fields that are already filled are not rewritten. On conflict, record it truthfully in this package's fields, then write `messages` to the function that supplied the source; the shared six items are an exception: for lyrics-first, do not change them, only send a message.

### 5.3 Message channel `messages`

A top-level list; each entry covers one matter. Like `checks.exemptions`, it is a shared area, and **either side may write to it**.

| Field | Type | Required | Description |
|---|---|---|---|
| `messages` | list | ○ | Each entry `{from, to, about, says, status, reply}`; an empty list means no messages |
| `from` / `to` | enum | ✅ | Closed set of functions: `music` (this package) `lyrics` `sound` `editing` `shot-design` `writing` `production`; the two must differ |
| `about` | str or list | ✅ | What it concerns: a field path (`form[B2].bars`, `mix_intent.dynamics`), a section id, or bars |
| `says` | str | ✅ | What the other side should do and why; one matter per entry |
| `status` | enum | ✅ | The sender writes `open`; the receiver changes it to `answered` (replied, field not changed), `accepted` (field changed as requested) or `rejected` (not accepted) |
| `reply` | str | ○ | Written by the receiver: for `accepted`, which field was changed; for `rejected`, the reason |

1. **Send**: add a new entry with `status: open`, e.g. "The gap between D and C2 at 6 dB is the only large drop; please preserve it in mastering" (`from: music, to: sound, about: mix_intent.dynamics`). If you want to change one of the shared six items in lyrics-first work, also use this channel (`to: lyrics`).
2. **Reply**: change only the `status` and `reply` of the entry addressed to you; do not delete others' entries or change their `says`. A message does not itself change fields: a field that needs changing is still changed by its owner skill (`mc-workflow` §2.1); after the change, mark the entry `accepted`.
3. **No waiting**: if no reply is read, treat it as no reply; an `open` entry does not block self-checks or stop a stage, and is handed off as it stands. Data goes into the fields; messages only say where and why.
4. Messages addressed to this package (`to: music`) are read at S0 kickoff and before every change to the spec.

### 5.4 Six fields shared with the other side of the song

> **Six fields shared with the other side of the song**: `form[].id`, `form[].bars`, `form[].name`, `meta.tempo`, `meta.key`, `vocal.persona`. Both sides use the same set of section ids.
> - **The party that goes first sets these six items**; the party that comes later reads them in as given, and treats them as locked items (`meta.upstream`). Composed-first: the composer/arranger sets them and the lyricist reads them; lyrics-first: the lyricist sets them and the composer/arranger reads them, and then the lyrics' word count and phrasing constrain `form[].bars` in reverse.
> - **The party that comes later does not change these six items.** If a change is truly needed (for example, the lyrics do not fit these bars), write a `messages` entry to the party that went first, stating which item to change and why. Once that party accepts, it changes its own spec, and the later party re-reads it.
> - Only when one side is present and the other side's spec does not exist are these six items set by this package itself.

In this spec: for lyrics-first, the six items read in are recorded in `meta.upstream.lyrics.shared`; if the `tempo` or `key` read in is `null` (the lyrics side could not determine it), this package sets it, then sends a message informing `lyrics`. In messages this package is `music`; the lyrics side is `lyrics`.
