---
name: mc-style-citypop-rnb
description: City pop and R&B as a style layer (city pop and R&B style layer) - the sound built on borrowed jazz harmony, a pushed bass, and deliberate space. The harmonic vocabulary that defines it and where it comes from, the rhythm-section signature of a bass ahead of the grid against drums on it, the instrumentation roster with its register discipline, a measured spectrum budget, why R&B is the most subtractive style in the corpus, and the transfer table. Use when writing or arranging city pop, neo-soul, or R&B-adjacent pop, when a track needs that late-night urban sound, when a groove needs to lean forward, or when borrowing these devices elsewhere. city pop, R&B, neo-soul, maru-sa progression, pushed bass, Rhodes.
---

# City Pop and R&B Style Layer (City Pop / R&B)

**The three pillars of this style: borrowed jazz harmony, a bass that pushes ahead of the beat, and deliberate space.**

★ **It is the most thoroughly validated style in this library** —
`mc-workflow/example-01-citypop.yaml` is a fully filled-in ARR-SPEC (**all 20 self-checks passed**),
and much of the content below comes directly from it.

## Which sections to read for each task

| Task | Read |
|---|---|
| **Judging whether these techniques can be carried over** | ★ §2 transfer table |
| Harmony | §3 |
| The groove "doesn't walk forward" | ★ §4 pushed bass |
| How to arrange the lineup | §5 + §5.2 register discipline |
| How to divide the frequency bands | §6 (**a measured spectrum budget**) |
| The difference between R&B and city pop | §7 |
| Finding a complete example | `mc-workflow/example-01-citypop.yaml` |

## Boundary

| Not covered here | Covered by |
|---|---|
| The full system of jazz harmony | `mc-style-jazz` §3, `mc-harmony` |
| Specific progressions (maru-sa, reverse cycles…) | `mc-progressions` |
| The general principle of pushed and pulled beats | `mc-rhythm-section` §3 |
| The general method of spectrum budgeting | `mc-texture-layering` §4 |
| How to make synthesizer timbres | `mc-sound-design` |
| Vocal design | `mc-vocal-direction` |

---

## 1. Required before starting

| Required | Question to ask |
|---|---|
| **① City pop or R&B** | ★ The two have completely different grooves and vocals (§7) |
| **② Sense of era** | Original 70s–80s? 2010s revival? Or contemporary neo-soul? |
| **③ Groove pushing forward or sitting back** | ★ City pop **rushes forward**, neo-soul **sits back**. These are two directions |
| **④ Who carries the "space"** | ★ The character of this style comes from the empty space; **decide who is assigned the silence** |

---

## 2. ★ Transfer table

| Device | Can it be carried out? | Notes |
|---|---|---|
| **Maru-sa progression (IV–III7–VIm–I)** | ✅ **Fully transferable** | Already in `mc-progressions` §2.4. "Almost any melody sounds stylish laid over it" |
| **F/G-type slash dominant substitute** | ✅ Transferable | ≈ G7sus4(9), more understated and refined than G7 |
| **Seventh-chord conversion + moderate tension** | ✅ Transferable | But **density must be controlled** — full-lineup tension turns it into jazz |
| **Bass rushing ahead, drums holding the grid** | ✅ ★ **Transferable, and the most valuable item** | See §4 |
| **Rhodes / electric piano register limits** | ✅ Transferable | §5.2 |
| **16th-note muted strumming** | ⚠️ Partly transferable | A very strong style marker; moved into another style it is immediately heard as city pop |
| **Gated snare** | ⚠️ Partly transferable | Strong 80s marker |
| **Saxophone solo** | ⚠️ Partly transferable | Same as above, and easily comes across as deliberately nostalgic |
| **"Silence as style"** | ✅ ★ **Transferable, and should be transferred** | See §8 |

★ **Criterion**:
> **Harmony and groove can be borrowed freely; timbres (muted strumming, gated snare, sax) are markers, and borrowing them gets you recognized.**

---

## 3. Harmony

### 3.1 It borrows from jazz, but at lower density

| From jazz | How city pop uses it |
|---|---|
| Seventh and ninth chords | ★ **Seventh chords are the default**, not an "upgrade option" |
| Tension notes 9/11/13 | **Used, but one or two at a time**, not the full jazz stack |
| ii–V, secondary dominants | Used extensively |
| **Sus / slash dominant substitutes** | ★ **F/G is a favorite** |
| Altered dominants, diminished-scale licks | ❌ **Not used** — that would turn it into jazz |

★ **This difference is the core of this skill**:
**city pop harmony is "jazz vocabulary with pop grammar."**
The vocabulary is borrowed in full, while the grammar (functional progressions, sections, chorus centering) remains pop.

### 3.2 Signature progressions

See `mc-progressions`:
- **Maru-sa progression 4361** (`IV–III7–VIm–I`) — a synonym for city pop / neo-soul
- **`IV△7–IIIm7–IIm7–I△7`** — a pop/R&B standard ("Lovin' You");
  ★ **inserting a #IVm7(♭5) just before the loop returns is very stylish**
- **`C△7–D7–F–F/G`** — a floating feel; the V7 pointed to by the secondary dominant II7 never arrives

---

## 4. ★ Groove: pushed bass + drums that hold the grid

**This is the most replicable aspect of this style, and also the one most often done wrong.**

**Measured sample (example-01, 112 BPM)**:

| Part | Offset | Role |
|---|---|---|
| **Bass** | **−12 ms (ahead)** | ★ **The only source of this song's "rushing forward"** |
| Clean guitar | **+8 ms (behind)** | Separated from the bass, **producing an illusion of width** |
| **Drums** | **0** | ★ **Hold the grid, serve as the reference frame** |

### 4.1 Why one part must hold the grid

**"Pushing ahead" is relative.** If everyone rushes together, it just means the tempo is a bit faster, and no forward push can be heard.
**An immovable reference point is required for the rush to exist.**

★ This is where the principle in `mc-rhythm-section` §2.0, that "quantization is a per-instrument decision", lands in this specific style.

### 4.2 The relationship between bass and kick drum

City pop usually uses **interlocking** (`mc-rhythm-section` §7.1) —
coinciding to thicken the low end when needed, separating when not needed, **preserving the bass's own melodic line**.
★ **The bass in this style is melodic**, not merely hitting rhythmic points.

### 4.3 Feel

`straight16` (not swing). The density of 16th notes comes from **muted strumming**, not from swing — the two sound similar and are easy to confuse, and choosing wrongly drags down the judgment about pushing ahead in §4 (the baseline for "how many ms ahead" is a straight grid; on a swung grid, the statement "rushing by X ms" itself does not hold). The general steps for choosing a feel (style first, then tempo; the backbeat criterion; how to handle middle-ground cases such as "in the crack") are in `mc-rhythm-section` §1.1 and are not repeated here.

---

## 5. Lineup

### 5.1 A measured roster (example-01)

| Instrument | Role | Frequency range | In / out |
|---|---|---|---|
| **Acoustic drums + gated snare** (recorded in the 70s) | Groove | 60 Hz–12 kHz | A1 / end (**entire D section silent**) |
| **Precision Bass**, fingerstyle, short sustain | Low end | 40–250 Hz | A1 / end |
| **Rhodes Mk I + light chorus** | Harmonic bed | 200 Hz–2 kHz | I / end |
| **Strat single-coil, 16th-note muted strumming** | Texture | 1–3 kHz | A1 / **C2** (★ never appears again afterward, giving space to the sax) |
| **Prophet-type sawtooth monophonic line, slow glide** | **Memorable hook** | 1.5–4 kHz | I / end (★ **plays only the hook, never provides a bed**) |
| **String section, long notes in high position** | Color | 400 Hz–6 kHz | C1 / end (exits once at A2, returns at C2) |
| **Tenor saxophone** | Melody | 250 Hz–4 kHz | **D** / O (★ **enters only after the song passes halfway; the outro is its**) |
| **Female vocal**, breathy, not in your face | Melody | 200 Hz–8 kHz | A1 / **C3** (★ **no vocal in the outro**) |

★ **Three design decisions here embody strong rules from this library**:
1. **The sax enters only after the song passes halfway** — the lineup must include a mid-song entrance (**59/59 strong rule**)
2. **Guitar exits at C2, vocal exits at C3** — at least one part exits early (**59/59 strong rule**)
3. **The synthesizer plays only the hook, never the bed** — a non-vocal memorable hook (lint #8)

### 5.2 ★ Register discipline

**The place this style most easily turns to mud is 200–500 Hz, because Rhodes, strings, and vocals all live there.**

Measured solution:
- **Limit the Rhodes to C3–C4**
- **Write strings only at C4 and above**

★ **This is the textbook use of "staggering registers"** (`mc-texture-layering` §4.2, solution ②).
**It is not achieved by cutting with EQ, but by not writing the conflicting notes in the first place.**

---

## 6. A measured spectrum budget

| Band | Owned by | Competitors | Solution |
|---|---|---|---|
| **40–120 Hz** | Bass | Drums | Kick sidechains the bass, 30 ms release; bass yields 3 dB at the kick's hit point (**frequency yielding**) |
| **200–500 Hz** | Rhodes | Strings, vocals | ★ **Stagger registers**: ep limited to C3–C4, strings written only at C4 and above |
| **1–3 kHz** | Muted guitar | Synth lead | ★ **Alternate**: guitar only in A/B sections, synth lead only in the gaps at phrase ends in I/C/O sections |
| **6–12 kHz** | Drums | Strings | Strings roll off high frequencies above 8 kHz, leaving the air for hi-hat |

★ **Four conflicts, all three solutions used** (frequency yielding / staggering registers / alternating) —
exactly the "pick one of three and state it" that `mc-texture-layering` §4.2 requires.

---

## 7. Distinguishing city pop from R&B

| | **City pop** | **R&B / neo-soul** |
|---|---|---|
| **Groove direction** | ★ **Rushes forward** (bass ahead of the beat) | ★ **Sits back** (laid back) |
| **Vocals** | Relatively straightforward, mixed further back | **Heavy ornamentation, runs, ad-libs** |
| **Harmony** | Jazz vocabulary + pop grammar | Closer to jazz, **tension is fuller** |
| **Lineup** | Band lineup (drums, bass, guitar, keys + strings + horns) | Relies more on **sampling and programming** |
| **Vocal layering** | Harmonies on the chorus | ★ **Stacked harmonies are the main tool** (all four types in `mc-vocal-direction` §5 are used) |

★ **The two share a harmonic vocabulary, but their grooves run in opposite directions.**
**Putting city pop's pushed bass into neo-soul will directly ruin that style.**

### 7.1 ★ A measured finding: R&B is the most "subtractive" style

Measured across 10 hiphop-rnb tracks in the Cambridge-MT multitrack set:

| Metric | hiphop-rnb | pop | jazz |
|---|---|---|---|
| **Median number of instruments that exit early** | ★ **28** | 16 | 10 |
| Share of instruments already present at the opening | **24%** | 21% | 16% |

**How to read it**: R&B/hip-hop opens with the fullest texture but also strips away the most —
its sense of structure comes from **continually removing things**, not continually adding them.

★ **Directly transferable**: when writing R&B, `subtraction_events` should be written more densely than for other styles.

> This corpus of 10 tracks is a mix of hiphop-rnb. **The hip-hop side** (a third sense of time, 808 division of labor, sampled textures) is in `mc-style-hiphop`; this section covers only the R&B half.

---

### 7.2 ★ Western R&B and Japanese R&B are two different things (Fujitani)

| | Western R&B | Japanese R&B |
|---|---|---|
| Notes | **Few** | **Many** |
| Character | Dark, cold | Shimmering, bright |
| Harmony | Influenced by jazz, often uses very complex chords | |

(p0154). Before writing, state which one you want; the three letters "R&B" are not enough. The principle: **when there are few notes, every note must sound good, or the arrangement does not hold**;
the beat is the lifeblood of R&B, and the timbres of kick and snare must be carefully chosen (p0154).

### 7.3 Programming conventions for Western-leaning R&B (Fujitani pp. 0157–0162)

- **All drums use synthesized timbres, with beats programmed in the hip-hop manner**; all three timbres should sound "as if sampled from vinyl", thick and rough. A characteristic of samples is that when the kick and snare ring, the hi-hat resonates along with them, and that is the groove (p0157)
- **Two layers of kick**: the main kick, plus a "puff" sub-bass kick, **appearing only at the start of a bar** (p0157)
- **Hi-hat plays eighth notes with no velocity variation at all**, entered lightly step by step (p0160); fills are placed at the end of even-numbered bars, using a record-scratch effect (p0160)
- **Bass plays root notes only**, landing only on beat one and on the off-beat eighth note in the second half of beat three; notes are stretched as much as possible but do not overlap the onsets of beats two and four — too long and it becomes sluggish (p0161)
- **Electric piano uses only half notes or whole notes**; with a good vibrato and timbre it is comfortable, and it is also used in other styles when a thick, expansive feel is wanted (p0162)

This is the opposite of the city pop groove in §4: there the bass rushes and the drums hold the grid; here the bass has only two landing points and the hi-hat has no velocity variation. Under the same "R&B" label are two sets of lineup discipline.

## 8. ★ "Silence as style"

Half of this style's character comes from **what it chooses not to play**.

Three subtraction events in the measured sample:

| Position | What happens | Why |
|---|---|---|
| **Before C2** | **The whole band (including drums) stops for the last half beat** | ★ **The second chorus cannot win over the first by being louder; it relies on the hole before it** |
| **D section** | Drums and bass **drop out for the whole section**, leaving only electric piano + vocal + sax | ★ **The lowest energy point of the song must come before C3, or C3 does not work** |
| **A2** | Strings and half the guitars exit | ★ **The second verse should be emptier than the first, not fuller** |

★★ **These three reasons are each worth remembering on their own**; they are general arrangement wisdom, not specific to this style
(→ `mc-arrangement-arch` §3).

---

## 9. Correspondence with ARR-SPEC fields

| Field | This skill |
|---|---|
| `meta.style_layer` | `mc-style-citypop-rnb` |
| `groove.feel` | `straight16` |
| `groove.push_pull` | ★ §4 — **bass negative, drums 0**; this is the signature of the style |
| `arrangement.spectrum_budget` | §6 |
| `arrangement.roster[].note` | ★ Register limits are written here (§5.2) |
| `arrangement.bass_kick_relation` | **Interlocking** |
| `subtraction_events` | §8. R&B should have more (§7.1) |

---

## 10. Must-pass checks after writing

- [ ] Distinguished **city pop (forward)** from **R&B (back)**
- [ ] **One instrument holds the grid** as the reference frame (§4.1)
- [ ] The bass **has a melodic line**, not merely hitting rhythm points
- [ ] Low-mid conflicts are solved by **staggering registers**, not by cutting with EQ
- [ ] Each frequency-band conflict states which of the three solutions it uses
- [ ] ★ **Has explicit subtraction events, and can state the reason for each**
- [ ] Hook-playing instruments **play only the hook, never a bed**
- [ ] At least one instrument **enters only after the song passes halfway**, and at least one **exits early**
- [ ] When carrying into another style, checked §2 — **did not carry the timbre markers along with it**

---

## Appendix: Sources

- ★ **`mc-workflow/example-01-citypop.yaml`** — the main basis of this skill.
  A fully filled-in ARR-SPEC with **all 20 self-checks passed**, which can be used directly as a template to modify.
- **Measured data**: Cambridge-MT multitrack measurements (10 hiphop-rnb tracks)
- Harmonic vocabulary: `mc-progressions` [reference.md](../mc-progressions/reference.md) §2, §3
- This skill is built on example-01 and the general layer: the "rules" of city pop are essentially **jazz harmony + pop structure + a specific set of timbres**.
