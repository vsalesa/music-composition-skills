# mc-case-studies reference: corpus index and breakdown template

> [SKILL.md](SKILL.md) covers the method; this file covers **where to look** and **how to write up a breakdown**.

---

## 1. Corpus index

### 1.1 Measured ARR-SPECs (63)

Reverse-derived automatically, track by track, from Cambridge-MT multitracks (60 songs) and 3 finished Chinese-language pop songs.

**By `style_layer`**:

| style_layer | Count |
|---|---|
| `pop` | 10 |
| `rock` | 10 |
| `edm` | 10 |
| `jazz-acoustic` | 10 |
| `hiphop-rnb` | 10 |
| `Alt-Rock---Blues---Country-Rock---Indie---Funk---Reggae` (★ six styles mixed in one pack, **not split out**) | 10 |
| `mc-style-chinese-pop` | 3 |

### 1.2 ★ Measured parameters by style (computed by this library itself)

**Reliable**:

| Metric | pop | rock | edm | jazz | hiphop-rnb | Alt pack |
|---|---|---|---|---|---|---|
| **Roster size (median)** | 36 | 30 | 32 | ★ **22** | 37 | 38 |
| **Section count (median)** | 10 | 10 | 10 | 9 | 9 | 10 |
| **Share of instruments present at the opening** | 21% | ★ **8%** | 21% | 16% | 24% | 20% |
| **Instruments entering mid-song** | 29 | 26 | 26 | ★ **20** | 26 | 28 |
| **Instruments leaving early** | 16 | 18 | 20 | ★ **10** | ★ **28** | 16 |

**Three readings you can cite**:
1. ★ **Jazz has the smallest lineup (22) and the fewest events**: it is recorded live, so change comes from playing, not from swapping the lineup.
2. ★ **Rock has the most restrained opening (8%)**: the whole band has to play together later, and if the opening is already full there is no contrast.
3. ★ **R&B/hip-hop has the most exits (28)**: the sense of structure comes from continually taking things away.

⚠ **Not citable**:
- **BPM**: beat tracking misjudges by octaves (edm measured 68–152, and 68 is obviously half of 136).
- **Energy peak/trough**: normalised to 0–10, so every song comes out as 10/0 and nothing distinguishes them.
- **DR / loudness / stereo width**: Cambridge-MT is unmixed multitrack, so these quantities have no reference value.

**Songbook corpus (score parameters, 2026-09-17; five songbooks read page by page, one entry extracted per song, no lyrics stored, n=931)**:

| | Four Chinese-language books (n=564) | English Fake Book 1955–1986 (n=367) |
|---|---|---|
| Top five key signatures | F 15, C 13, G 13, D 10, B♭ 10 (%) | C 25, G 22, F 19, E♭ 9, B♭ 7 (%) |
| Time signature | 4/4 69%, 2/4 25%, 3/4 4% | 4/4 and C 58%, 2/2 16%, 3/4 10% (n=50, most scores unmarked) |
| BPM figure | Median 84, P10–P90 58–120 (n=78, twentieth-century works) | No figure on the page |
| Section skeleton | Intro-verse-chorus-outro / intro-verse-chorus-interlude, 8% each (n=88) | Verse-Chorus 68% (including case variants, n=55) |
| Most common four-chord loops (symbols as written) | A E A D, G D G D, F C F C, C F G C, C Am G C (4 times each, small sample) | G C G C ×16, B♭ F C7 F ×14, F B♭ F B♭ ×12, C7 F B♭ F ×11, C F G C ×11 |

How to read it: in the English fake books the four-chord loops are almost all I–IV and I–IV–V7 swings, and the B♭ and F keys cluster in keys that suit brass and saxophone. In the Chinese-language books, chord symbols appear only in the guitar scores (83 songs), so the loop counts are too small to show more than two families, I–IV–V–I and I–vi–V–I.
In the BPM row, only the twentieth-century Chinese-language works have figures, so **it cannot stand in for the BPM of contemporary Chinese-language pop**. Only figures with an n are listed here.

### 1.3 Human-annotated ground truth (7)

Seven songs from Cambridge-MT, with section starts marked by ear (marking method in [SKILL.md](SKILL.md) §3.3):

AMContra_HeartPeripheral, APZX_CyberMower, DigitalHumans_Electrvm,
Forkupines_Semantics, MERCMusic_Knockout, MR1103_Flags, SimonLyn_Copper

**Calibration result**: the algorithm hits **72%**, with a **median deviation of 0.0 seconds**.

### 1.4 Original multitrack material

Beyond the measured ARR-SPECs, a portion of the corresponding original multitrack files is kept (with a master catalogue and per-stem lists),
so that when a result looks doubtful you can go back and check whether a given measurement was taken correctly.
This layer takes no part in the criteria calculations and serves only for provenance, so it is not necessary to keep it for every measured track.

### 1.5 Three measurements

| Measurement | What it was taken on | Where the conclusion is |
|---|---|---|
| Compliance-rate zero point | One City Pop spec against three unrelated finished Chinese-language songs | `mc-ai-tell-audit` §3.2 |
| Tempo calibration | The 56 songs in the Cambridge-MT multitracks that carry an annotated tempo | This file §1.2 (why BPM is not citable) |
| First round of rule corroboration | 62 songs in the Cambridge-MT multitracks | [SKILL.md](SKILL.md) §4.2 |

---

## 2. Piece → technique index

**These are not in the audio corpus. They come from books and are for "finding an example".**

### 2.1 Chord progression → famous pieces

See `mc-progressions` [reference.md](../mc-progressions/reference.md) §7 (11 entries).

### 2.2 Orchestration and blended timbre

See `mc-orchestration` [reference.md](../mc-orchestration/reference.md):

| Technique | Score example |
|---|---|
| Neutralisation | Ex. VII-15, Mahler, Symphony No. 1, IV |
| Effect of playing technique on blend | Ex. VII-16, Schoenberg |
| Octave doubling | Ex. VII-17, Rossini |
| Colouring | Ex. VII-18, Haydn |
| Three conditions for a woodwind to show through | Ex. VII-19, Sibelius |
| Mixed use of timbral layering and juxtaposition | Ex. XIV-48, Chen Yi, *Ge Xu* (Song Fair) |
| Texture analysis | Ex. XIV-47, Milhaud, Symphony No. 2, IV |
| **Unison with rhythmic differentiation** | Ex. IV-85, Shchedrin, *The Seagull* |

### 2.3 Counterpoint

See `mc-counterpoint` [reference.md](../mc-counterpoint/reference.md):

| Technique | Score example |
|---|---|
| Contrasting polyphony of differing character | Ex. 61, Ding Shande, *Long March Symphony* II; Ex. 62, Prokofiev, Symphony No. 7, I |
| Contrasting polyphony of the same character | Ex. 63, *Romeo and Juliet*; Ex. 64, Beethoven, Symphony No. 9, II; Ex. 65, Chen Peixun, *Qingming Sacrifice* |
| Three-voice canon | Ex. 262, Franck, *Fugue*; Ex. 263, Mozart, *Canon* |
| Polyphonic chorus | Ex. 264, *The Peacock Flies* |

### 2.4 Form

See `mc-form`:
- Keisuke Kuwata, "Shiroi Koibitotachi" (白い恋人達): a dense demonstration of the standard structure
- The Beatles, "Hey Jude": the chorus comes right at the start, yet the second half is no weaker
- Maroon 5, "Sunday Morning": **one 2-bar loop throughout, built up by adding and removing parts**

### 2.5 A fully filled-in spec

★ **`mc-workflow/example-01-citypop.yaml`**: passes lint 16/16 and can be adapted directly as a template.
**`mc-workflow/example-00-ai-default.yaml`**: a negative example that passes only 3/16.

---

## 3. Template for a section-by-section breakdown

**Four-way alignment**: timecode / section / lineup event / harmony.

```yaml
# Case: <song title> — <why it was chosen>
source: { artist: , title: , year: , why_chosen: }

# What can be measured (fill from measurement; mark what can't be measured accurately "estimate, not measured")
measured:
  tempo: / key: / meter: / duration:
  sections: [{t: "0:00", bars: , name: , energy: }]
  roster:   [{id: , band: , entry: , exit: }]

# ★ What a machine can't measure, filled in by a person
analysis:
  one_thing:            # the one thing this song does
  arrangement_hook:     # what the non-vocal memorable point is
  subtraction:          # where the subtraction is, and why
  why_it_works:         # ★ the most important field
  what_to_steal:        # concrete moves that can be carried over
  what_not_to_steal:    # what belongs to this song/this style and loses its flavour if carried over
```

★ **Don't skip the `what_not_to_steal` field**:
it is the source material for the transfer tables in each L3 skill.

---
