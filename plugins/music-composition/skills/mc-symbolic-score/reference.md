# mc-symbolic-score Reference: ABC Syntax Cheat Sheet and GM Instrument Table

> [SKILL.md](SKILL.md) covers mapping and validation; this file holds the tables to look up **syntax** in.

---

## 1. ABC Syntax Cheat Sheet

### 1.1 Header fields

| Field | Meaning | Example |
|---|---|---|
| `X:` | Index number (required, usually 1) | `X:1` |
| `T:` | Title | `T:Night Drive` |
| `C:` | Composer | |
| `M:` | Meter | `M:4/4`, `M:6/8`, `M:C` (=4/4), `M:C|` (=2/2) |
| `L:` | Default unit note length | `L:1/8`, `L:1/16` |
| `Q:` | Tempo | `Q:1/4=112` |
| `K:` | Key (**must be the last line of the header**) | `K:D`, `K:Am`, `K:Dphr` (mode) |
| `V:` | Voice | `V:1`, `V:2` |

### 1.2 Pitch

```
C,, C, C c c' c''      ← low to high; comma lowers an octave, apostrophe raises an octave
^C  _C  =C             ← sharp / flat / natural
^^C  __C               ← double sharp / double flat (rare; most pop and film scores do not need these)
```

★ **Case is an octave marker, not a pitch-name marker**: `C` to `B` is the octave around middle C,
`c` to `b` is the octave above. Commas (`,`) keep lowering and apostrophes (`'`) keep raising,
and they can be stacked: `C,,` is one octave lower than `C,`.

★ **Accidentals hold for the rest of the bar**, until the next barline,
or until another sharp, flat or natural in the same bar overrides them.
This rule is easy to miss. The consequence is that "the score is written correctly but the pitches read back wrong".
The syntax check in §8 does not catch this kind of error; only note-by-note comparison does.
To keep a chromatic alteration across a barline, the accidental must be written again in the next bar (ABC will not carry it over for you).

### 1.3 Durations (relative to `L:`)

```
C2   two unit lengths
C/2  half a unit (also writable as C/)
C3/2 one and a half (dotted)
C>D  dotted rhythm (C long, D short)
C<D  reversed dotted rhythm
z    rest; length notation is the same as for notes: z2, z/2
Z4   multi-bar rest (the number after Z is a count of bars, not of unit lengths)
(3CDE  triplet: fits 3 notes into the time of 2 units (equivalent to (3:2:3)
```

★ **`L:` defines how long "1" is, not an absolute duration**.
The same `C2` is a quarter note under `L:1/8` but only an eighth note under `L:1/16`.
If the `L:` in the header does not match the duration units actually used in the notes,
the relative rhythm of the finished piece stays correct, but **the absolute length is scaled throughout**.
This kind of error is not caught by the "syntax pass" in §8.
It has to be found by arithmetic such as "total duration / total beats", or by rendering the piece and listening to whether the tempo is right.

★ **Dotted chains can be written in a row**: `C>D>E` is three notes with dotted values that step down in turn,
common in western and jazz melodies with a swing feel. Beyond two or three notes in a row, readability drops;
past that point, splitting into several notations within the bar is easier to maintain.

### 1.4 Bars and structure

| Notation | Meaning |
|---|---|
| `|` | Barline |
| `||` | Double barline |
| `|]` | Final barline |
| `|:` `:|` | Repeat (★ **do not use for the chorus**; see SKILL.md §3.4) |
| `[1` `[2` | First and second endings |
| `%` | Inline comment |
| `%%` | Directive |

### 1.5 Chords and ornaments

```
"F#m7"C     ← chord symbol written in quotes before the note
(CDE)       ← slur
C-C         ← tie
(3CDE       ← triplet
~C  .C  HC  ← ornament / staccato / fermata
```

### 1.6 Multiple voices

```
V:1 name="Melody"
V:2 name="Bass" clef=bass
```

★ **Whether YuE2 supports multiple voices is not yet confirmed** (SKILL.md §7.2). Send single-voice scores first.

---

## 2. GM Instrument Table (common)

Fill `render.midi.instrument_map` with these.

| # | Instrument | # | Instrument |
|---|---|---|---|
| 1 | Acoustic Grand Piano | 34 | Electric Bass (finger) |
| 2 | Bright Acoustic Piano | 35 | Electric Bass (pick) |
| 5 | **Electric Piano 1** (Rhodes) | 36 | Fretless Bass |
| 6 | Electric Piano 2 | 39 | Synth Bass 1 |
| 17 | Drawbar Organ | 41 | Violin |
| 19 | Rock Organ | 43 | Cello |
| 25 | Acoustic Guitar (nylon) | 49 | **String Ensemble 1** |
| 26 | Acoustic Guitar (steel) | 53 | Choir Aahs |
| 28 | **Electric Guitar (clean)** | 54 | **Voice Oohs** (vocal placeholder) |
| 30 | Electric Guitar (overdriven) | 57 | Trumpet |
| 31 | Electric Guitar (distortion) | 66 | Alto Sax |
| 33 | Acoustic Bass | 67 | **Tenor Sax** |
| | | 74 | Flute |
| | | 82 | **Lead 2 (sawtooth)** |
| | | 89 | Pad 1 (new age) |

**Drum kit**: GM Drum Kit 1, **channel 10**.

| Sound | GM pitch | Sound | GM pitch |
|---|---|---|---|
| Kick | C1 (36) | Closed HH | F#1 (42) |
| Snare | D1 (38) | Open HH | A#1 (46) |
| Toms | F1/G1/A1/B1 | Crash | C#2 (49) |
| | | Ride | D#2 (51) |

★ **Mappings on non-GM sound sources may differ**; when using a sample library, follow its documentation.

---

## 3. Common MIDI CCs (orchestration-related)

The full table is in `mc-orchestration` [reference.md](../mc-orchestration/reference.md) §5. Only the most common are listed here:

| CC | Purpose | ★ Note |
|---|---|---|
| **1** | Modulation (usually vibrato) | Some libraries use it to control volume; **confirm the mapping before use** |
| **7** | Volume | ★ **Sets this track's position in the mix**; does not shape phrases |
| **11** | Expression | ★ **Sets how this phrase breathes**; the swell within a phrase is controlled by this |
| **64** | Sustain pedal | |
| **68** | Legato switch | 0–63 off / 64–127 on |
| **74** | Filter cutoff (brightness) | |
| **91** | Reverb send level | |

★★ **Mixing CC7 and CC11 is the number-one reason an orchestral mockup sounds fake**
(→ `mc-style-cinematic` §8).

---

## 4. Choosing between MusicXML and MIDI

See the full comparison table in [SKILL.md](SKILL.md) §6. The one-line version:

- **For YuE2 to perform it → ABC**
- **For handing to a human → MusicXML**
- **For expression and rhythmic feel → MIDI**

---

## 5. Unconfirmed backend behaviour

Only one item is still open, so only one is listed:

- ⚠ YuE2's ABC dialect is not confirmed (SKILL.md §7.2)

**Criteria for marking it "confirmed"**: once the three items listed in SKILL.md §7.2 (how section markers are written,
the chord-symbol dialect, and whether multiple voices are supported) have each been tested to a definite answer,
write the conclusions back here and delete the word "unconfirmed". Until then, scores must follow the
"most conservative subset" described in §7.2; do not write them using the habits of other dialects.
