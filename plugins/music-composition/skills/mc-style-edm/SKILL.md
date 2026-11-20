---
name: mc-style-edm
description: EDM and club music as a style layer - a form built on layer addition and subtraction rather than verses and choruses. Why club structure works on the floor and not at home, the long build and the drums-only section that exists for the DJ, layering as form when there is no melody to carry it, the one place where absolute quantization is correct and the one constraint that still applies, sound design as the primary compositional act in this style, and the transfer table. Use when writing or arranging EDM, house, techno or club-oriented tracks, when a build does not build, when a drop lands flat, or when borrowing club devices into song-form music. Keywords: electronic dance music, EDM, house, techno, four-on-the-floor, drop, build, layering, club.
---

# Electronic Dance Music Style Layer (EDM / Club)

**The biggest difference between this style and the rest of this library: it is not "a song."**

> **The structure of song-type music is "a sequence of content" (the verse says this, the chorus says that).
> The structure of club music is "addition and subtraction of layers."**

So many general rules must be re-interpreted here, but **not invalidated; they have taken a different form**.

## Which sections to read by task

| Task | Read |
|---|---|
| **Judge whether an EDM technique can be carried over** | ★ §2 transfer table |
| Arrange the structure | §3 |
| The build won't build / the drop won't land | §4 |
| No melody: what holds it up | §5 layering as form |
| **Whether to quantize everything** | ★ §6 (**the one point this skill most needs to make clear**) |
| Timbre | §7 |
| Measured data: how EDM differs from other styles | §8 |

## Boundaries

| Not covered here | Where it goes |
|---|---|
| The **design method** for synthesizer timbres | `mc-sound-design` (★ the recipe tables are in its reference, including Detroit techno / Electro House / IDM bass) |
| General principles of quantization and groove | `mc-rhythm-section` §2 |
| Frequency budget | `mc-texture-layering` |
| EQ / compression parameters | Mixing work (★ the EQ and compression chapters of Takeuchi's book also belong there; this package takes only the intent, which goes to `mc-mix-intent`) |
| General principles of form | `mc-form` |
| DJ technique, live performance | Not covered |

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① For whom, and where is it heard** | ★ **Dance floor or headphones**. This decides the entire structure (§3.2) |
| **② Which sub-genre** | House / techno / trance / dubstep / future bass… **BPM and structure differ enormously** |
| **③ Is there a melody** | ★ If not, the form depends entirely on the layering in §5 |
| **④ Who doesn't stay on the grid** | ★ **Even in a fully quantized style, not every part of the whole track sits on the grid** (§6) |

---

## 2. ★ Transfer table

| Technique | Can it carry over to song-type music? | Notes |
|---|---|---|
| **Form built by adding and subtracting layers** | ✅ ★ **Transferable, and very useful** | It is the extreme form of "lineup as form" in `mc-arrangement-arch` §5 |
| **Long build** | ⚠️ **Partially transferable** | Listeners of song-type music have much less patience. **Shorten it to 2–4 bars to be usable** (the anticipation before the chorus in J-POP, `mc-style-jpop` §6) |
| **Drums-only section** | ⚠️ Partially | In a song it is a useful subtraction event, but **do not make it 16 bars long** |
| **Four-on-the-floor kick** | ⚠️ Partially | A strong style marker |
| **Sidechain pumping** | ⚠️ Partially | ★ A very strong marker. `example-01`'s `exclude` explicitly excludes `modern sidechain pumping` |
| **Absolute quantization** | ⚠️ ★ **Partially transferable, with a precondition** (§6) | |
| **Repetition that seeps in below conscious attention** | ✅ Transferable | §5.2. **But in song-type music it must go along with the advance of the lyrics** |
| **The idea that "purpose determines form"** | ✅ ★ **Transferable, and should be** | §3.2 |

★ **Criterion**:
> **You can carry away its structural techniques (layering, build, repetition),
> but do not carry away its time scale (build-ups that start at 16 bars).**

---

## 3. Structure

### 3.1 Typical shape

```
four-on-the-floor kick enters
 → add hi-hat
 → add sustained accompaniment such as piano (repeated in units of 8+ bars)
 → proper intro → A-melo → sabi
 → back to a drums-only section → loop...
```

**Characteristics**:
- **The melody is optional**
- The structure is **long and large**
- There are sections with **only drums** or **only pad** → ★ **the contrast in thickness is extremely sharp**
- **Arranged around the drums**

### 3.2 ★ Why this structure holds

**Two reasons, both tied to "where it is heard":**

1. **Building up slowly suits dancing**
2. ★ **A drums-only section makes it easy for a DJ to segue into the next track**

> ★★ **A structure that sounds repetitive and boring at home is extremely effective on the dance floor: purpose determines form.**

**This sentence is the most important one in this skill**, and it can be carried outside: **for any question of "is this right," first ask "where is it heard, and how many times is it heard"**
(→ ARR-SPEC's `intent.listener_situation`).

### 3.3 Section composition

How a club track is divided internally: two approaches should be looked at side by side.

★ **Form supported by density (DeSantis p0299)**: rather than traditional sectioning, it relies on "continually changing the texture's density around a small amount of material" to hold up the form. Three concrete units can be borrowed directly:
- **Buildup**: commonly **16 or 32 bars** (or multiples), pushing the density to the peak of the section by continually adding layers
- **Breakdown**: a low-energy contrasting section; the common approach is **to remove all drum elements**, or conversely **to keep only the drums**; usually shorter than a buildup, but still in units of **8 or 16 bars**
- **Drop**: the densest section of the whole track; it can follow a buildup or a breakdown. **Usually only 1–2 per track**, while buildups and breakdowns can appear more often

**Classic dub techno** (e.g. the Chain Reaction label) takes the opposite extreme: a bassline or drum pattern runs through the whole track with no obvious sectional contrast; new material is added on top of existing material, and the scale changes little (p0299).

**Criterion (p0300)**: for branches closely tied to pop music, a more traditional song form is advisable. For "purely electronic" genres such as techno, trance, and dubstep, a small amount of material with continuous density change is enough to hold up a sense of structure, with no need to force verse/chorus.

---

## 4. Build and drop

### 4.1 A build is about anticipation, not loudness

**The usual reason a build won't build: it only adds things, without making a "promise."**

An effective build must offer a **predictable endpoint**:
- **Filter sweep** (cutoff moving in one direction → listeners know it will reach the top)
- **Rhythmic acceleration** (8th → 16th → 32nd → listeners can count how many beats remain)
- **Rising pitch** (riser)
- ★ **A stop at the last moment** (→ `mc-style-jpop` §6, "everything suddenly stops and then slams back in")

**A fifth endpoint for a build: the Shepard tone** (Howard & Angus p0248–0250). The spectrum loops within a single octave; each semitone up shifts every component up one slot; the high components fade out and the low components fade in. The result is heard as **an endlessly rising scale**, yet acoustically it never exceeds one octave. It is the only riser that can continue indefinitely, suitable for passages where the location of the drop is unknown, or where the anticipation should be stretched very long. Method: a set of stacked octave partials, each controlled in amplitude by a bell-shaped envelope.

### 4.2 Three reasons a drop fails to land

| Reason | Fix |
|---|---|
| **The build is already as full as the drop** | ★ Return to `mc-arrangement-arch` §2: **the energy curve must include a decline** (62/62 strong rule). The peak of the build should be **lower than the drop** |
| **The low end was not released during the build** | Cut the low frequencies during the build, and bring them back together at the drop. This is the physical source of the contrast |
| **The drop has nothing new** | The drop must introduce an **element that has not appeared before** (a timbre, a riff) |

### 4.3 ★ A default to be wary of

The generation back end, under EDM prompts, will **default to a build + drop**, and often a **textbook one**.
The `exclude` in `example-01` excludes `EDM drop` precisely for this reason.
**The criterion, as elsewhere: did you choose it, or did it land on you by default?**

---

## 5. Layering as form

### 5.1 Where form comes from when there is no melody

> **Most non-vocal contemporary electronic genres tend to avoid traditional verse and chorus sections,
> and instead create formal contrast through the addition and subtraction of layers.**

**How this is expressed in ARR-SPEC**:
- `form[].name` still needs to be filled, but **use `Instrumental` / `Intro` / `Outro`**,
  and in `note` state which layers this section contains
- ★ **The form is actually carried by `roster[].entry/exit`**, not by `form[].name`
- `energy_curve` becomes the main structural description

★ This is exactly what `mc-arrangement-arch` §5, "lineup as form," describes; EDM is its pure form.

### 5.1a ★ Entry order is itself structure: the classic Acid method (Nozaki)

A classic Acid track has only four tracks: riff, bass, hi-hat, and kick. **They do not enter together; the order of entry is fixed** (p0271–0272):

1. Riff only
2. Add hi-hat
3. Bass comes in
4. Finally, the 4/4 kick is released

★ **The kick enters last**, which is the opposite of the intuition to lay down the drums first and build upward. Three accompanying points (p0273):

- At the opening, set the riff's CUTOFF very low so it almost fades in. The aim is a phrase in which **it cannot be heard where it starts**: until the hi-hat enters, listeners take the beat to be half a beat off from the real one. The rhythmic ambiguity is deliberate; the effect comes when the hi-hat enters and lines up with that moment.
- Before the hi-hat enters, slowly turn the CUTOFF open by hand so the monotonous repetition does not become tiresome. A slow LFO or a filter envelope can also do this, but the author holds that **only manual control produces unpredictable variation**.
- **When a new part enters, first pull down the CUTOFF of the layer already playing**: before the bass enters, temporarily turn the riff's CUTOFF down so the two are not both pushed to the maximum and interfering. Once the kick comes in, the riff and the bass "tangle freely," controlled by turning CUTOFF and RESONANCE together (when one goes down, the other goes up).

**Generalization**: in any loop-based style, "who enters first and who enters last" is a decision to write into the spec, not a default that starts with the drums.

### 5.2 Repetition itself is accumulation

> **Repetition seeps in below conscious attention and evokes semi-involuntary bodily responses;
> even without a big climax, repetition alone constitutes accumulation.**

★ **This superficially conflicts with `mc-melody` §8, "against predictable harmony," but in practice it does not conflict**:
- **Song-type music**: listeners are **following the content**; predictable = boring
- **Club music**: listeners are **dancing**; predictable = something they can keep up with

**This is a real failure condition**: the rule in `mc-melody` §8.1 ("the same phrase repeated 3 or more times") **does not hold in club music**.

---

## 6. ★ Quantization: the one point this skill most needs to make clear

**The two sources should be viewed side by side:**

| Source | Position |
|---|---|
| DeSantis (p0154) | In **techno, house, electro, and EDM**, **absolute quantization is entirely appropriate**, often accompanied by completely uniform, unvaried dynamics |
| This library's corroboration table | "Not every voice should be strictly aligned to the grid": **62/62 hits**, a strong rule |

**Reconciliation: the key lies in "every part":**

- ✅ **The drum kit can be absolutely quantized**, if the style calls for it
- ❌ **But not every single instrument in the whole track should sit on the grid.** That is a fingerprint of generative models, not a requirement of any style
- ★ **Quantization is a per-instrument decision, not a global switch**

**Practical approach**: quantize the drum kit 100%, and **leave one played element unquantized** (bass, sampled material, vocals, or the attack of one pad layer).

### 6.1 If everything really must be zero

The judgment itself was covered in §6; here we only settle the notation: **write the reason in `checks.exemptions`** (for example, "grid-locking is this style's language").
**An exemption must state its reason; it may not be skipped silently.**

### 6.2 Drum-machine aesthetics

> The drum-machine aesthetic (the canonical example is the Roland TR-808) **deliberately gives the hi-hat and snare no velocity variation at all**:
> **cold, flat, and proud of it.**

★ This is a **legitimate style choice**, not laziness.
But in the spec it looks the same as "forgot to do dynamics," **so it must be written into exemptions to tell the two apart.**

---

## 7. Timbre: in this style, timbre is the composition

**In passages without melody, "what timbre this layer is" is the entire content.**

→ So `mc-sound-design` carries far more weight in this style than elsewhere.

**The directly relevant recipes in its [reference.md](../mc-sound-design/reference.md)**:

| Need | Technique | Page |
|---|---|---|
| Detroit Techno bass | 28 | p0106 |
| IDM warped bass | 29 | p0107 |
| **Electro House bass** (inverted FILTER EG) | 30 | p0109 |
| Funky, rough electro bass | 26 | p0100 |
| Drum and bass (D'n'B) | 37 | p0130 |
| Reese bass | 38, 39 | p0133 |
| Minimal-music sequences | 59 | p0200 |
| Fierce, intense sequences | 62 | p0210 |
| **The full Acid set** (the 303's secrets, slides, real-time control, distortion) | 76–84 | p0258–0281 |
| **TR-909 kick** (using the filter as the sound source) | — | p0235 |
| TR-808 snare / pedal hi-hat | 71, 72 | — |

★ **Technique 82, "real-time control," deserves special mention**:
**variation produced by a human hand sweeping CUTOFF in real time cannot be achieved by quantization or randomization.**
This is where "leave one part unquantized" from §6 lands most naturally in this style.

---

## 8. Measured data: EDM vs. other styles

Measured on 10 EDM tracks from the Cambridge-MT multitrack set (10 pop and 10 jazz tracks as controls):

| Metric | edm | pop | jazz |
|---|---|---|---|
| roster size (median) | 32 | 36 | 22 |
| number of sections (median) | 10 | 10 | 9 |
| share of instruments already present at the opening | 21% | 21% | 16% |
| instruments entering mid-track | 26 | 29 | 20 |
| **instruments exiting early** | **20** | 16 | 10 |

**Reading**: EDM has **more exits than pop** (20 vs 16), which fits §3.1's "drums-only sections."
**But the gap is smaller than R&B's (28).**

⚠ **Do not cite BPM**: the detected median for edm is 129, with a range of 68–152. Beat tracking on electronic music produces octave errors (68 is clearly half of 136).

---

## 9. Mapping to ARR-SPEC fields

| Field | This skill |
|---|---|
| `meta.style_layer` | `mc-style-edm` |
| `intent.listener_situation` | ★ §3.2 — **decisive in this style** |
| `form[].name` | §5.1 — mostly use `Instrumental`; **the real structure is in the roster** |
| `arrangement.roster[].entry/exit` | ★ §5.1 — **the actual carrier of form** |
| `energy_curve` | §4.2 — **the build peak must be lower than the drop** |
| `groove.quantize_policy` | ★ §6 — write it per instrument |
| `checks.exemptions` | ★ §6.1, §6.2 — full quantization and no velocity variation must both have reasons written here |
| `render.*.exclude` | §4.3 — explicitly exclude if you do not want the textbook drop |

---

## 10. Checklist before finishing

- [ ] Stated **where it is heard** (dance floor / headphones), and the structure matches it
- [ ] Stated **which sub-genre** of EDM it is
- [ ] **The build peak is below the drop** (the energy curve has a decline)
- [ ] During the build **the low end was cut**, and it returns at the drop
- [ ] The drop introduces **an element not heard before**
- [ ] ★ **Not every part of the whole track sits on the grid**; if so, **exemptions record the reason**
- [ ] The drum-machine aesthetic (no velocity variation) is **a chosen style**, and it is written into exemptions
- [ ] In passages without melody, **form is carried by the roster's entries and exits**
- [ ] Timbres are designed, not preset-flipped (→ `mc-sound-design` §2)
- [ ] When carrying this over to song-type music, **the time scale was shortened** (§2)

---

## Appendix: Sources

- ***A Book on How Professional Songs Are Made*** (*Puro no kyokuzukuri ga wakaru hon*) — the main body of §3 and §5 (the EDM/club section variants).
- **DeSantis, *Making Music*** — the section units in §3.3 (p0298–0300) and the quantization judgment in §6 (p0154).
- **Nozaki, *Illustrated Synthesizer Music Composition*** — all the recipes in §7.
- **Measured**: Cambridge-MT multitrack measurements (10 EDM tracks).
- **Takeuchi Kazuhiro, *EDM Production*** — the mixing chapter belongs to `mc-mix-intent`.
