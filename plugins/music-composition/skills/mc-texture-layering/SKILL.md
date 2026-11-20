---
name: mc-texture-layering
description: Texture and spectral layering - arranging as a space budget rather than an instrument list. Foreground/middle-ground/background depth planning, the perceptual cues that decide what a listener hears as lead, rate-of-change discipline per depth layer, the frequency budget and the three ways to resolve a collision (yield / separate registers / alternate), and the maximal-density method for building dense sections. Use when a mix or arrangement sounds muddy, flat, or two-dimensional, when two parts fight, when the wrong element is grabbing attention, when something is written but inaudible, or when filling the spectrum_budget field of an ARR-SPEC. Grounded in critical bands, masking asymmetry (low masks high), temporal masking and auditory grouping. Keywords: texture, frequency budget, critical band, masking, foreground/middle-ground/background, depth, density, part collision.
---

# Texture & Spectral Layering

**Core principle: arranging is a space budget, not an instrument list.**

> **Musical space has edges, like a canvas. Adding beyond the limit covers what is already there.**
> **Each added part makes every other part work harder to win the listener's attention.** (p0286)

So "adding one more layer" is never free. This skill governs **how to allocate this limited space**.

## Which sections to read, by task

| Symptom / task | Read |
|---|---|
| Muddy, murky, unclear | §4 Spectrum budget |
| Flat, two-dimensional, no depth | §2 Three depth layers |
| Lead is not prominent / someone else is stealing the focus | §3 Depth cues + §3.2 the trap |
| Written but inaudible | §3 and §4 together |
| Sections get messier toward the end | §5 Rate-of-change discipline |
| Want a very dense section that does not turn to mud | §6 Maximal-density method |
| Filling the spectrum_budget field of an ARR-SPEC | §7 + §8 |

## Boundary: what this skill does not cover

| Not covered here | Where it lives |
|---|---|
| Which instrument to use, how to blend timbres | `mc-orchestration` |
| When parts enter and exit, the energy curve | `mc-arrangement-arch` |
| Specific EQ frequencies, compression ratios, mastering | Mixing; this package only supplies the `mix_intent` brief |
| The **intent** of making way between sections (which section yields to which) | `mc-mix-intent` (this skill handles **structural** layering; it handles **section-level** yielding) |
| Layering inside the drum kit | `mc-rhythm-section` |

> The boundary between `mc-texture-layering` and `mc-mix-intent` is easy to blur. Remember this:
> **this skill's fix is to "rewrite" (change register, reduce notes, swap instruments, offset timing);
> mix-intent's fix is to "remix" (EQ, sidechain, dynamics).**
> Anything that can be solved at the writing stage should not be left to the mix. Doing so pushes the problem downstream.

---

## 1. Required before you start writing

| Required | Question to ask |
|---|---|
| **① Depth map** | Which layer (foreground / middle ground / background) does each element sit in? (§2) |
| **② Band assignment** | Which frequency band does each element mainly occupy? If you cannot say, you have not thought it through yet |
| **③ Collision list** | Which two elements are competing for the same space? (§4) |
| **④ Resolution for each collision** | Yield / separate registers / alternate: **pick one of the three and state which** |

---

## 2. Three depth layers: foreground, middle ground, background

**Problem**: music can feel "flat" or two-dimensional, lacking a sense of depth (p0111).

**Approach**: borrow concepts from the visual arts (film, photography, painting) and **plan the depth levels at the composition stage**,
rather than leaving all of it to the mix (p0111).

| Layer | Visual analogy (p0112) |
|---|---|
| **Foreground** | Closest to the observer; usually the subject, sharp focus, rich detail |
| **Middle ground** | Between the two; not the main focus, but nearer and more prominent than the background |
| **Background** | Farthest away; recognisable but blurred, with less detail |

**How to push and pull in production** (p0112–0113):

| | Bring closer (toward foreground) | Push back (toward background) |
|---|---|---|
| Volume | Louder | Quieter |
| Timbre | Brighter (more high frequencies) | Darker |
| Space | Drier (higher proportion of direct signal, less reverb) | More reverb |

**★ But this skill is concerned with depth at the compositional level**, see §3. That is the part mixing cannot recover.

---

## 3. Depth cues: what makes the listener decide who is the lead

### 3.1 Four perceptual cues

> **The ear tends to hear sounds that are "high", "loud", "fast", or "changing quickly" as foreground.** (p0113)

Of these four, only "loud" can be adjusted in the mix; the other three **are fixed at the composition stage**.

Three of them have auditory explanations given by Howard & Angus: **loud**: hearing is most sensitive around 3–4 kHz, so at the same sound pressure level this range sounds much louder than the low frequencies (p0091, p0093); **high**: timbres with strong harmonics from the 5th to 7th and above are described as bright, harsh, and highly penetrating (p0223, p0228); **rate of change**: hearing is very sensitive to changing sounds, and unchanging things get "adapted" out (p0352, p0342).

**A precise example** (p0113):
> The drum kit is usually very loud, but because of its **consistent and unvarying** character, it is typically placed in the middle ground or background;
> when a **drum fill** occurs, the **sudden change in texture density and complexity** briefly moves the drums to the foreground.

This makes the point about rate of change clear: the same instrument, with no change in volume or timbre, can be shifted in depth **by rate of change alone**.
This is why a fill is not decoration; it is **depth scheduling**.

### 3.2 ★ The most common trap

> If a synth melody line sits **an octave above the vocal**, or has **more complex rhythm and more jumping intervals**,
> listeners may subconsciously hear the synth, rather than the vocal, as the **leading part**. (p0113)

This is the real reason the vocal gets buried: **often it is not a volume problem, but the perceptual cues are pointing the wrong way**.
Pushing the vocal up 3 dB will not fix it, because the synth wins on both "high" and "fast".

The vocal has its own cue as well: opera singers are heard above a full orchestra thanks to the 2.5–4 kHz "singer's formant"
(Howard & Angus p0209; measured at 2.4–3.5 kHz for tenors, p0221). Pop vocals do not have such a strong formant, but the principle is the same:
**this range is the window where the vocal comes forward**. Synth, distorted guitar, and cymbal harmonic peaks piled into this range push the vocal back.
Self-check: in the chorus, who occupies 2.5–4 kHz? Fails when the lead is not the vocal.

**Self-check action**: for each section, list which element is currently the highest, the loudest, the fastest, and the one changing most dramatically.
**If the lead does not hold at least two of these four answers, it is not the lead.**

### 3.3 Solutions

Rather than turning the lead up, **push the competitors down on the four cues**:

| How the competitor wins | How to push it down |
|---|---|
| High | Move it down an octave, or let it appear only in the gaps between the lead's phrases |
| Loud | (Hand this to the mix) |
| Fast | Reduce note density, lengthen note values |
| Rate of change | Turn it into a repeating pattern: **consistency pushes it toward the background** |

---

### 3.4 ★ Six means of separating layers (Yang Liqing)

§3.1 explains why the listener hears one layer as the lead; this section covers **which knobs you have to pull two layers apart** (Yang Liqing p0244–0250):

| Means | What it does | Key point |
|---|---|---|
| **Timbre** | Switch to a different instrument family | The dominant factor in separating layers (p0244) |
| **Register** | Widen the interval distance, or place the main line in the register where it is most characteristic | The greater the distance, the less overlap; **a main line in its most characteristic mid-to-high register will float out even when it shares a register with the accompaniment** (p0246) |
| **Articulation** | Change the playing technique | Timbres with different transitional characteristics produce heterogeneous sound, which helps separate layers (p0247) |
| **Density / concentration** | Contrast in the number of players for solo, soli, and tutti | ★ Two layers using exactly the same instruments can still be separated by player count alone (p0248) |
| **Amplitude** | Single-note groups against multi-note groups (unison against octave, multi-layer octaves) | Supporting role (p0250) |
| **Dynamics** | Raise or lower by one level | ★ **Always only a supporting means.** When register, timbre, density, and amplitude are already out of balance, dynamics cannot rescue it (p0250) |

**How to use it**: if two layers are fighting, try the table from top to bottom, **leave dynamics for last**. Only the last row is available to the mixing layer; the first five rows all sit in the arrangement layer.
This is the basis for "solve yielding at the writing level rather than leaving it to the mix" (reference §7.4).

## 4. Spectrum budget

### 4.1 Be able to state the band each instrument occupies

This is what the `roster[].band` and `spectrum_budget` fields in ARR-SPEC are for.
**If you cannot name an instrument's band, you do not know who it is fighting with.**

### 4.2 The three ways to resolve a collision

When two instruments occupy the same band, **there are only three paths**. You must choose one and state it:

| Resolution | What it does | When to use it |
|---|---|---|
| **① Yield** | One side gives way while the other sounds (rewrite: reduce notes, shorten sustains, change chord voicing) | Both must be present, but their importance differs |
| **② Separate registers** | Move one side as a whole to a different register | Both are important and both must be present throughout |
| **③ Alternate** | The two never sound at the same time; take turns by section or by phrase | The two have similar character, and sounding together would only cancel them out |

**Option ③ is often overlooked, but it is frequently the best solution**: it resolves both the band collision and the masking problem in `mc-orchestration` §3.4.

Each of the three resolutions has a boundary drawn by Howard & Angus:
- **Separating registers**: masking spreads upward; low frequencies masking high frequencies is far stronger than the reverse (p0239). Moving a secondary part **below** the lead is more dangerous than moving it above. Critical bandwidth grows with frequency (p0083–0084), so the same interval sounds muddier in the low register. Four-part writing requires at least a fourth between bass and tenor, unless they are already above the bass clef (p0146).
- **Yielding**: within the same critical band, the masking threshold sits only about 20 dB below the masker (p0240). If a secondary part in the lead's band is less than 20 dB quieter, it is "written but inaudible"; delete it or change its register instead.
- **Alternating**: a soft attack within 100–200 ms after a loud sound stops is still masked (p0241). A "turn-taking" gap at a phrase ending shorter than 200 ms does not count as alternating.

> A measured example (City Pop):
> In the `1–3 kHz` band, a clean guitar and a synth lead collide → **resolution: alternate**.
> The guitar appears only in the verses and build-ups; the synth appears only in the intro, chorus, and outro, in the phrase-ending gaps.

### 4.3 "Thinning": middle options short of removing an element entirely

You do not have to delete an entire instrument; you can just thin it (p0287):

1. **Reduce the number of notes the instrument plays**
2. **Shorten the decay of sustained notes**, so they yield quickly to the other elements in the mix

**These two are composition-level fixes, not mix-level ones**: they change how many notes are written on the score and how much note value each note occupies. They are not EQ or compression carving out certain overtones. That is why they belong to this skill and not to mix-intent.

Choosing between thinning and removing outright: if an instrument carries a middle-ground or foreground role from §2, deleting it entirely leaves that layer empty, so try thinning first. If it is only filling density in a passage and removing it does not change who is speaking, removing it outright is cleaner.

After stacking a section to a very high density using the §6 maximal-density method, the two rounds of removal in §4.2/4.3 tend to be too timid: an over-layered section needs **heavy** erasing before it regains musicality, and if you hesitate you will leave a pile of notes competing for attention (p0288). The test for "enough" is not counting how many instruments you removed; it is listening again after removal: if any part still cannot state the band it occupies or its beat placement, you have not removed enough.

### 4.4 A premise to establish first

> **A subtractive strategy only works when your existing parts are already as good as they can be.** (p0286)

Removing a few parts from a pile of mediocre material leaves mediocre material. **Layering cannot rescue weak material.**

When to think along these lines: if a section sounds "small", "weak", or "without force", the first instinct is often to add things. But the principle runs the other way: every extra component makes the others work harder for the listener's attention, and musical space is a bounded canvas; overfilling it only buries what has already been written (p0286). The question at this point is whether something can be removed, not what else can be squeezed in.

This is not the privilege of minimalism, nor a technique belonging to any one genre. Music with slow rates of change may sound minimal even with many elements (see §5 Rate-of-change discipline); conversely, high-density commercial EDM can still sound clear and open if it deliberately limits the number of parts sounding at once (p0287). The core principle is to add only when necessary, and also to ruthlessly remove whatever does not contribute to the music (p0287).

### 4.5 Stacking is not the same as louder

Two equally loud instruments stacked together gain only +3 dB; ten give +10 dB, and +10 dB is a doubling of loudness (Howard & Angus p0040, p0094–0095).
To make a section feel "bigger", spread the energy across more critical bands: the total sound intensity stays the same, yet perceived loudness rises (p0096).
In other words, add material to **empty bands**, rather than unison-stacking on bands that are already occupied.
Exception: copies of the same signal add coherently, which is a separate case (in phase up to +6 dB, p0035, p0037).
Self-check: which previously empty band does the new layer occupy? If you cannot answer, the addition is wasted.

★ **Beyond the frequency axis there is a time axis** (Takeuchi p0028–0031): the impression of sound pressure depends on **whether there are silent gaps**.
Popping a balloon once every three seconds does not sound loud; popping it continuously does, even though the maximum volume is identical (p0029).
A kick drum on quarter notes leaves gaps between beats, so the kick alone cannot push up perceived loudness; the bass has to fill those gaps.
But no matter how much low frequency you add, by equal-loudness curves it does not produce the feeling of high loudness. **What really raises perceived loudness is wrapping 1–5 kHz in sustained sound** (p0029–0030).
That is the range where guitar, voice, and piano sit, which is why a self-accompanied singer can sometimes build more size than with a continuous kick (p0030).

**Arrangement implication**: to make the chorus feel "big", check two things. First, is there sustained material filling the gaps between beats? Second, is there a continuous layer in 1–5 kHz (pad, distorted guitar wall, harmony vocals)?
If neither is in place, adding low frequencies will only sound muddy.

---

### 4.6 ★ Pedal tones: when to add a sustained layer, and when not to

A band pedal tone is a sustained note or long chord; the pads and sustained strings in pop arrangements are examples (Yang Liqing p0309). It serves four functions (p0309):

1. **Mediation**: connects different timbres so the layers blend into one whole
2. **Stabilisation**: provides a clear harmonic outline within a flowing figured texture
3. **Fullness**: makes the sound rounder and thicker
4. **Contrast**: creates a contrast of density and sparseness against sections without a pedal tone

★ **When not to add one** (p0313): when the melody, bass, or inner parts in the texture **already contain long-value notes**, they are already acting as a pedal, and adding another sustained layer is gilding the lily.
Styles that aim for a harsh, dry sound also use pedal tones sparingly; how often a pedal tone appears is itself a stylistic marker.

**How to choose the pitch** (p0313): in sections where the harmony changes frequently, choose **common tones** shared by the successive chords as the pedal, so it becomes a running thread. If no common tone exists, screen several long notes of different pitches and try to connect them into a pleasant line.
The pedal layer does not have to be long notes; tremolo or a structurally simple figure can also serve.

**Gluing** (p0311): placing a long chord layer above a dense figure, with its register, voicing, and density matching the figure layer on the first note of each beat, binds the two layers together.
Conversely, **a fixed figure or a percussion rhythm pattern also acts as glue** (Yang Liqing, middle volume p0514–0515): a rhythmic pattern with a distinct, recurring contour can integrate a complex structure,
providing both vertical integration and horizontal connection between sections.

## 5. Rate-of-change discipline

> **Middle-ground and background elements should keep their rate of change to a minimum, while foreground elements may move more freely.** (p0114)

This principle is very practical, and it is the remedy for "sections get messier toward the end":

- Background changing → the listener's attention is constantly pulled, and the lead cannot hold its ground
- Background static → every change in the lead is heard

**Self-check action**: write down how often each element changes, e.g. "changes every few bars".
**If background elements change as often as the foreground, there is no background, only a pile of foreground.**

**Failure condition**: some styles (IDM, breakcore) aesthetically embrace high rate of change across all elements.
In those cases, the "foreground" is established by other cues (usually extreme timbre), not by rate of change.

---

## 6. Maximal-density method: how to build a very dense section that does not turn to mud

**Problem**: after writing the first part, adding a second part feels like starting from scratch; building linearly from left to right is daunting (p0265).

**Approach** (note that this is a **composition-stage** method; it is similar to but operates at a different point from the subtractive arrangement in §3 of `mc-arrangement-arch`, which is an **arrangement-stage** method) (p0266):

1. Start from any **point of maximum density** in the song, where all the elements that could possibly sound together **actually do sound together** (p0265)
2. This step will produce **unmusical mess**, which is expected
3. **Remove elements one at a time** until reaching a level that is both dense and musically logical → this becomes the song's **climax** (p0265)
4. **Copy** this peak section, and test lower-density versions by muting or deleting
5. When you find a combination you like, copy and paste it as a new section
6. The arrangement thereby becomes "organising these sections of different densities to match the ebb and flow of the song" (p0266)

**Value of this method**: it makes **all sections naturally share one source**: the low-density sections are subsets of the high-density section,
so the sections will not sound like "different songs".

**Cost**: it tends to produce over-layering. DeSantis himself warns that after using maximal density or subtractive arrangement,
**over-layering may arise unintentionally**, requiring heavy erasing before musicality returns,
and you must take special care in judging **whether you have removed enough** (p0288).

---

## 7. Mapping to ARR-SPEC fields

| Field | Section of this skill |
|---|---|
| `arrangement.spectrum_budget` | §4 (each entry includes band / owner / competitors / **resolution**) |
| `arrangement.roster[].band` | §4.1 |
| `arrangement.depth_map` | §2 Three depth layers |
| The four-segment division of `arrangement.roster[].band` | §4.1 (see reference §1) |

**Not filled by this skill**: `roster[].entry/exit` (→ `mc-arrangement-arch`),
`roster[].instrument` (→ `mc-orchestration`), `mix_intent.ducking_map` (→ `mc-mix-intent`).

---

## 8. Must-pass checks after writing

- [ ] Every element is labelled **foreground / middle ground / background**
- [ ] Every element can state **which frequency band it occupies**
- [ ] For each section, the answers to "highest, loudest, fastest, changing most dramatically" are listed; **the lead holds at least two**
- [ ] Every band collision states whether the resolution is **yield / separate registers / alternate**
- [ ] When the lead is the vocal, the chorus's 2.5–4 kHz belongs to the vocal; in the low register, the spacing between two parts is at least a fourth (§3.2, §4.2)
- [ ] Background elements' rate of change is **clearly lower** than the foreground's
- [ ] If the maximal-density method was used, check that you **removed enough** (cost in §6)
- [ ] Every collision that can be solved at the composition level **has not been pushed to the mix**

---

## Appendix: Sources

- **Dennis DeSantis, *Making Music*** (Ableton): the backbone of §2, §3, §4.3, §4.4, §5, and §6
  (Foreground/Middle Ground/Background, Maximal Density, The Power of Erasing). Page numbers refer to the book's pages.
- The auditory basis for the frequency budget is in the masking chapter of **Izhaki, *Mixing Audio***, summarised in [reference.md](reference.md).
- **Howard & Angus, *Acoustics and Psychoacoustics***: §3's loudness / harmonics / singer's formant, §4.2's masking asymmetry and temporal masking, and §4.5's loudness summation; the critical-band ruler is in reference §1.1. Page numbers refer to the Chinese edition's pages.
- The corresponding mixing techniques are in **Izhaki, *Mixing Audio***. **Only the frequency-budget and intent parts are taken**;
  EQ and compression practice is a matter for mixing and is not included in this package.
