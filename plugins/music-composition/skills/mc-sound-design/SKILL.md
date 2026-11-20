---
name: mc-sound-design
description: Synth and timbre design as an arrangement decision (timbre design) - deciding what a sound must be before touching a knob. The four-question intent checklist (percussive or pitched / register / envelope shape / bright or dark) and its mapping to oscillator, tune, amp EG and filter; resetting to an unprocessed starting state instead of browsing presets; the sculpting model of subtractive synthesis; filter selection; and why a pure sine bass vanishes on small speakers (difference tones). Use when choosing or designing a patch, when a synth sound is generic or preset-sounding, when a bass disappears on phones or laptops, when a pad has no character, or when writing the timbre descriptors of an ARR-SPEC roster. timbre design, synthesizer, filter, envelope, preset, bass disappears, difference tone.
---

# Sound Design

**The stance of this skill: timbre is an arrangement decision, not something handled after the fact.**

A wrong timbre choice means every later step of orchestration, layering and mixing is compensating. In practice, "choosing a sound" for most people means "scrolling through presets until one isn't unpleasant" — **and that is the most reliable source of the AI sound**,
because generative models do the same thing: they pick the most typical timbre within a category.

> The core method of this skill comes from Nozaki Takao: **first state the concept clearly, then touch the parameters.**

## Which sections to read for each task

| Symptom / task | Read |
|---|---|
| Don't know where to start designing a timbre | §1 four-question checklist → §3 mapping |
| Have been scrolling presets for ages and nothing is right | §2 return to zero |
| Timbre sounds "like a preset", no character | §2 + §4 |
| The timbre is right on its own but wrong once in the arrangement | §3 ② register |
| Bass disappears on phones / laptops | §6 difference tones |
| Pad is thick but has no texture | §4 four-step sculpting |
| Filling in the roster timbre description for ARR-SPEC | §7 |

## Boundary: what this skill does not cover

| Not covered here | Covered by |
|---|---|
| Choice of real instruments and blended timbres | `mc-orchestration` |
| Which frequency band this timbre occupies and what it clashes with | `mc-texture-layering` |
| EQ frequencies, compression ratios, bus processing | `mc-mix-intent` (intent) / implementation is a mixing matter |
| Film sound effects, Foley, ambience | **Sound** (sound effects, Foley) work (**same name, different thing, don't mix them up**) |
| Specific style timbre recipes (how to set a Detroit techno bass) | The recipe table in [reference.md](reference.md) |
| Sample selection and slicing | `mc-style-hiphop` §6.3–6.5 and its reference §1–2 (material selection, slicing, loop building); choice of sample library products is not covered by this package |

> ★ Naming note: `mc-sound-design` in this library refers to **the synthesis and design of pitched musical timbres**;
> "sound design" in the film sense (sound effects, Foley, space) is the job of the **sound** function and is not covered by this package.

---

## 1. Required before starting: the four-question checklist

Before starting a design, determine the **character of the role** the timbre plays, and answer these 4 items (p0091):

| # | Question |
|---|---|
| **①** | Is it a **percussion-type instrument** (no clear pitch) or a **pitched sound** (has pitch, can play melody or chords)? |
| **②** | What is its approximate **register range**? |
| **③** | What **amplitude envelope** curve does the timbre have? |
| **④** | **Bright (many overtones) or dull (few overtones)**? |

> The author's requirement is to build a habit: **"When doing timbre design, first form the habit of comparing your concept against ①–④"** (p0091).

**Why these four questions are enough**: each one corresponds to a single synthesizer module (§3),
so once the four are answered, much of the parameter setting is already decided — **what remains is taste**.

**Self-check action**: if you cannot answer even one of the four questions, don't touch the knobs.
When you can't answer, what you are doing is not design, it is trial and error.

---

## 2. Return to zero: start from an "unprocessed sound"

**Problem**: a synthesizer doesn't have a simple, clear "original sound" the way an electric guitar or piano does.
When you open one, you are already inside someone's preset, **so every decision you make is relative to decisions someone else made**.

**Method**: establish an "unprocessed sound" initial setting (p0088):

| Module | Setting |
|---|---|
| Oscillator | **Use only one sawtooth wave** |
| Filter | **CUTOFF turned fully right, RESONANCE 0, FILTER EG 0** (fully open) |
| AMP EG | **ATTACK 0, DECAY 0, SUSTAIN fully open, RELEASE 0** (organ-like envelope) |
| LFO and other modulation | **Not used at all** |
| Effects | **Off** |

> **"Only by tuning to this kind of 'raw waveform sounding state' does the 'unprocessed sound' of a guitar or piano form"** (p0088).

**Suggestion**: save this as "initial state 1", and **start every timbre design from here** (p0089).

**The mechanism by which this counters the AI sound**: a preset is someone else's average judgment of a category.
Starting from a preset, you can only fine-tune around that average. Starting from zero, your timbre grows out of your own choices.

**Failure conditions**: when time is extremely tight, or when you need a specific classic timbre (such as the TB-303 acid bass), starting from the closest preset and modifying it is reasonable (p0090, approach ②) — but **you must be able to say which four places you changed**; if you can't, you changed nothing.

---

## 3. Mapping the four questions to parameters

| Concept | Parameter | How to set it |
|---|---|---|
| **① Percussion or pitched** | **Oscillator waveform** | Percussion → **NOISE**; pitched → **SAW** or **SQUARE** (p0092) |
| **② Register** | **TUNE / TRANSPOSE** | See the ★ below |
| **③ Envelope curve** | **AMP EG** | See the three groups below |
| **④ Bright or dull** | **FILTER** | First set a **−24 dB/oct low-pass**, then adjust with **CUTOFF** (p0092) |

### ★ ② Register is the most easily overlooked item and the costliest

> **"No matter how hard you try to approximate the ideal timbre, as long as the register differs, the sound will never be exactly as imagined"** (p0092).

This explains a common phenomenon: **the timbre sounds right on its own but wrong once in the arrangement**.
Most of the time the timbre is not the problem; it is sitting in the wrong register.
— This connects directly to the "staggering registers" in `mc-texture-layering` §4.2.

### ③ The three decisions for the envelope (p0092)

| | What you want | How to set it |
|---|---|---|
| **Attack** | Quick and crisp / gradual build-up | ATTACK short / ATTACK long |
| **Sustain** | Decays naturally / holds and extends | SUSTAIN=0 and adjust DECAY / use SUSTAIN to set the level |
| **Release** | Stops immediately / keeps a tail | RELEASE=0 / lengthen RELEASE |

> General principle: **"The most important thing is to start from 'the parts already established'"** (p0093).
> Of the four questions, the one you are most certain of is the first module to adjust.

**Tip**: if the phrase is already written, **design the timbre while repeatedly playing it back**, which works well (p0093).
— Timbre is judged in context, not by judging it through solo auditioning.

---

### 3.5 ★ The attack is the timbre's identity (Howard & Angus)

The four-question checklist addresses spectrum and envelope, but **the recognizability depends almost entirely on the first few dozen milliseconds**: without the onset and decay, a violin and a trumpet are hard to tell apart (p0222–0223).
When a synthetic timbre sounds "fake", the spectrum is usually not wrong; the clues that should be in the onset are missing. The book names six (p0223):
bow friction, the consonant-like onset of brass, the breath noise of wind instruments, the slap of a reed onset, the strike of hammers, and the decay of strings.

**Three rules when making a timbre**:

1. When imitating a real instrument, first ask what noise or inharmonic components its onset contains, and only then ask about the steady-state spectrum. A sample sounds "fake" mostly because the loop was taken from the steady state and the onset was clipped flat (p0217).
2. The onset is not colored by the room; the first reflection usually arrives only after the onset has finished (p0217). **Reverb cannot rescue an onset that was clipped flat.**
3. Onset lengths differ greatly across families: the fundamental of brass comes first and is extremely short; flute has about 70 ms of breath noise before the fundamental; the violin onset is about 160 ms and vibrato does not appear until after 250 ms (p0220–0221).
   For a timbre meant for "fast staccato", the onset must be short; for a timbre meant for "long notes", a longer onset actually sounds more natural.

A comparison table of onsets by family is in `mc-texture-layering` reference §5a.2.

### 3.6 ★ Emphasizing sound dynamics: giving a slow-attack layer a fast attack (Yang Liqing)

"Sound dynamics" refers to the temporal transition characteristics of a note's onset, sustain and decay. **Stacking different timbres to reinforce, exaggerate, or even reshape the original sound dynamics of one factor**
is called emphasizing sound dynamics (Yang Liqing, vol. 2, p0287).

The most common use: **a pad or string long note has no attack, so layer something with a fast attack (pluck, piano, plucked strings, mallet) to give it an onset**.
Aurally, the pad acquires edges of its own, though the attack actually comes from another instrument. Conversely, an overly hard attack can be softened by layering a slow-attack sound on top of it.

This is one of the most common mechanisms behind "two layers stacked sound better than each alone". When writing it into the spec sheet, treat it as an explicit decision:
write in `roster[].note` who this layer is giving an attack to.

The same system contains a point relevant to timbre: **the peak of psychological loudness is not necessarily the peak of physical loudness** (p0283–0284).
Even when a melody's top note or skeleton note is descending in dynamics, another timbre is often layered on top to emphasize it. Berlioz doubling the top note with horns at ppp is an example of this.
When building timbre layers, reserving a timbre that can be layered onto "the point that should be heard" is more effective than pushing the dynamics of the whole.

## 4. The sculpting model: what subtractive synthesis is doing

The author compares timbre design to **sculpture** (p0037):

| Sculpture | Synthesizer |
|---|---|
| ① Choosing the material (wood, stone) | **Choosing the waveform** |
| ② Using composite material | **Using multiple oscillators** |
| ③ **Cutting away** unwanted parts from a large original form | **Removing unwanted overtones with a filter** |
| ④ Repairing and reinforcing the needed parts | **RESONANCE** emphasizes a designated frequency band, or **FM / OSC SYNC / RING MOD** creates new overtones |

Meanwhile **EG and LFO create changes over time**, much like stop-motion clay animation (p0037).

**Use of this model**: it removes "adding effects" from the workflow.
All four means in ④ exist inside the synthesizer — **get the timbre right inside the sound source first, and only then consider effects**.

---

## 5. Filter selection

| Type | What it does (p0037–0038) |
|---|---|
| **Low-pass LPF** | Cuts from the top of the sound (high-frequency overtones) |
| **High-pass HPF** | Cuts from the bottom foundation (low frequencies) |
| **Band-pass BPF** | Keeps only the desired part, cutting both above and below |
| **Notch** | Cuts only a specified part, keeping both above and below |
| **Comb** | Like a comb dragged across, leaving a striped result |

> **More than nine out of ten uses of filters in synthesizer timbre design are low-pass** — because the overtone content of synthesizer preset waveforms is usually richer than ordinary instruments,
> so high-frequency overtones need to be cut (p0038).

**So**: when unsure which to use, use low-pass. When you reach for a Notch or Comb, you should be able to say why.

---

## 6. ★ Difference tones: why a pure sine bass disappears

This is a **psychoacoustic** hard constraint, not a matter of taste.

> **Difference tone**: even when the fundamental is not heard, the brain infers it from the overtones.
> For example, when 300 Hz and 400 Hz are heard together, the brain automatically fills in the greatest common divisor, **100 Hz**,
> so that one believes a 100 Hz sound was heard (p0127).

> But — **"A sine wave contains no overtones that could serve as a basis for judgment, so no auditory error naturally arises"** (p0127).

**Consequence**: a pure sine bass sounds fine on studio monitors, but **on phones, laptops and Bluetooth speakers it simply does not exist**.
Those devices cannot reproduce the fundamental, and a sine wave leaves no clues from which the brain could infer the fundamental.

**Two paths** (p0127):

1. **Add overtones**, creating a sound that can produce the auditory error ← almost always choose this one
2. Assume an environment that can play very low bass, such as a large dance hall or concert hall, and **give up on ordinary listening environments**

### Two methods of adding overtones

**Method one: transposed doubling** (p0127)
Copy the same performance to another track, **TRANSPOSE up an octave, or up an octave plus a perfect fifth**, and mix in lightly.

> **"Adding several overtones is also effective, but if you add too many you lose the texture of a sine wave,
> so the target should be a level that is audible but barely noticeable"** (p0127).

**Method two: distortion** (recommended for beginners, the more natural-sounding option) (p0127)
Insert a distortion effect to create a subtle result.
> **"If you can tell that it is distorted, you have added too much"** (p0127).

**Routing method**: send the sine bass through a Bus to an AUX track, add distortion on the AUX, and send it back to mix;
if the distortion amount is too small, **apply a low cut on the AUX first, so that it does not interfere with the original** (p0128).

**Self-check action**: any arrangement whose low-frequency body rests on a sine wave or an extremely dark timbre
**must be verified on phone speakers**. This is the only check in this skill that requires actually listening on a device.

---

## 7. Correspondence with ARR-SPEC and each backend

In ARR-SPEC, timbre lives in `roster[].instrument` (abstract choice), `roster[].timbre` (for text backends)
and `roster[].synth_params` (for parameter backends).
**The same description must be consumable by three kinds of backend**, so the wording matters:

| Backend | How it consumes | Writing requirement |
|---|---|---|
| Suno / MiniMax (text prompts) | Accepts only natural language | Use **audible descriptions**: material, era, reference instrument. Do not write CUTOFF values |
| YuE2 (text + conditioning) | Same as above, but can carry section-level differences | Same as above, but can differ section by section |
| MIDI / MusicXML → DAW | Accepts parameters | Write the answers to the four questions and the key knob settings in `roster[].synth_params` |

**Writing example** (two projections of the same timbre):
- Text backend: `warm analog saw bass, slightly detuned, short attack, filter opens over 2 bars`
- Parameter backend: `{osc: saw×2 detune 8c, filter: LP24 cutoff 320Hz, FEG amount +40 decay 900ms, amp: A0 D200 S0.7 R120}`

**These two must share one source** — generated from the answers to the four questions, not written separately.
If they come from different sources, you get "the text backend and the MIDI backend sound like two different songs".

---

## 8. Must-pass checks after writing

- [ ] Every designed timbre has had the **four questions** answered, and the answers are written down
- [ ] Started from **zero**; if modified from a preset, can say which places were changed
- [ ] **Register** was set first, not adjusted last
- [ ] Every place a non-low-pass filter is used, can say why
- [ ] Overtone enhancement for ④ is done first **inside the sound source** (FM/SYNC/RING/RESO), not by first attaching an effect
- [ ] If the low-frequency body is a sine wave / extremely dark timbre, **overtones were added**, and **verified on phone speakers**
- [ ] The roster timbre description gives both a **text version and a parameter version**, and the two share one source
- [ ] The timbre was tested **in the context of the phrase**, not decided by solo auditioning

---

## Appendix: Sources

- **Nozaki Takao, "Illustrated Synthesizer Music Composition Method" (圖解合成器音樂創作法)** — all of §1–§6 main body
  (theorem 24 of timbre design, 25 starting from the initial setting, 09 filter ①, 36 sine bass / difference tones). Page numbers refer to that book.
- Specific style timbre recipes (gritty electro-funk bass, Detroit techno, IDM, Electro House,
  hip-hop fat bass, R&B soulful timbres, drum and bass, and 10+ others) are organized in [reference.md](reference.md).
- The EQ / compression chapters of Takeuchi Kazuhiro, "EDM Production", are **not in this skill** — intent belongs to `mc-mix-intent`, and parameters are a mixing matter.

- The acoustic principle of difference tones is also covered in **Howard & Angus, "Acoustics and Psychoacoustics"** (missing fundamental).
