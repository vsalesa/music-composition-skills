# mc-sound-design Reference: Timbre Recipe Index

> This file is a **lookup table**, not reading material. `SKILL.md` explains how to judge; this file says where specific recipes are and what their core settings are.
> All page numbers refer to **Nozaki Takao, "Illustrated Synthesizer Music Composition Method: 99 Techniques to Learn at Once"** (圖解合成器音樂創作法：99種技法一次學會).
> The synthesizer demonstrated in the book is **NoiseMaker** (a free VST); parameter names are common across most subtractive synthesizers.

---

## 0. Read these two principles first

### 0.1 "What is lost cannot be recovered"

> Timbre making has a major principle, "**what is lost cannot be recovered**":
> **Overtones that have been cut away, or onsets that have been thinned out, are beyond help once processed by sampling.**
> To keep room for flexibly editing the timbre, **most professional creators choose to build synthesizer timbres "from scratch"**.

This is the other half of the reasoning behind `SKILL.md` §2, "return to zero": not only to avoid the average of presets,
**but also to preserve room for later changes**. Using someone else's sample means all the subtractions have already been made in advance.

### 0.2 Using the filter as a sound source

Not every sound needs to start from an oscillator. **When RESONANCE is turned fully right, the filter self-oscillates,
producing a sine wave with controllable pitch** — this is how the 909 Kick is made (§5.1).

When you need an extremely clean sine wave with dramatic pitch envelopes, this approach is more flexible than using a sine oscillator.

---

## 1. Looking up recipes by need

### 1.1 Bass (techniques 26–40, p0100–0142)

| The sound I want | Technique | Page |
|---|---|---|
| Presence-heavy, lead-level gritty bass (electro-funk) | 26 | p0100 |
| New wave / Giorgio Moroder classic synth bass | 27 | p0103 |
| Detroit Techno bass | 28 | p0106 |
| IDM warped bass | 29 | p0107 |
| Electro House bass (**inverted FILTER EG**) | 30 | p0109 |
| Hip-hop fat bass | 31 | p0111 |
| Morphing, bizarre bass | 32 | p0114 |
| Old-school funk bass (**pulse width + filter**) | 33 | p0117 |
| R&B ballad classic synth bass | 34 | p0120 |
| House / R&B "sexy bass" | 35 | p0123 |
| Low-lying **sine wave bass** on the ground | 36 | p0126 |
| Fierce drum and bass (Drum'n'Bass) | 37 | p0130 |
| Reese bass ① **LFO modulation** | 38 | p0133 |
| Reese bass ② | 39 | p0136 |
| Pick Bass from the M1 | 40 | p0140 |

**★ Required warning for the sine wave bass (technique 36)** is in `SKILL.md` §6 — the difference-tone problem;
a pure sine bass disappears on phones. The two methods of adding overtones (transposed doubling / FILTER DRIVE distortion) are on p0127–0128.

### 1.2 Pads / Backgrounds (techniques 41–47, p0144–0163)

| The sound I want | Technique | Page | Core method |
|---|---|---|---|
| Bright string pad | 41 | p0144 | **Two detuned oscillators + FILTER EG texture** |
| Gloomy string pad (UK new wave) | 42 | p0147 | |
| Solemn, atmospheric pad | 43 | p0150 | **Octave unison** |
| Light, transparent pad (fills gaps without competing) | 44 | p0153 | **High-pass filtering** |
| Morphing pad ① | 45 | p0157 | FILTER EG |
| Morphing pad ② | 46 | p0159 | **Filter varied by LFO** |
| Pad made with waveform editing | 47 | p0161 | **Reversed sound** |

> Technique 44, "light and transparent", corresponds to **frequency yielding** in `mc-texture-layering` §4.2 —
> it is an example of using timbre design to resolve frequency-band conflicts.

### 1.3 Accompaniment (techniques 48–53, p0165–0182)

| | Technique | Page |
|---|---|---|
| Electric piano style | 48 | p0165 |
| Electric organ style | 49 | p0168 |
| House-type accompaniment | 50 | p0171 |
| String-type accompaniment (includes REVERB setting example p0176) | 51 | p0174 |
| Wind-type accompaniment (includes FILTER DRIVE + REVERB p0178) | 52 | p0177 |
| Morphing accompaniment (**LFO also used in the filter**) | 53 | p0180 |

### 1.4 FM family (techniques 54–58, p0184–0198)

| | Technique | Page |
|---|---|---|
| Things about the DX7 (FM introduction) | 54 | p0184 |
| FM bass ① (**using EG to control FM over time**) | 55 | p0187 |
| FM bass ② (the warped family, also applicable to Reese bass) | 56 | p0190 |
| FM wind instrument | 57 | p0194 |
| FM pad | 58 | p0196 |

### 1.5 Sequences / Leads / Sound effects (techniques 59–75, p0200–0233)

| | Technique | Page |
|---|---|---|
| Minimal-music style sequence | 59 | p0200 |
| Square-wave sequence | 60 | p0203 |
| Sparkling style sequence | 61 | p0206 |
| Fierce, intense style sequence | 62 | p0210 |
| Morphing sequences ① ② (**LFO modulating LFO**, p0217) | 63, 64 | p0213 |
| Sine wave lead | 65 | p0219 |
| Gritty noise-based lead | 66 | p0222 |
| Guitar-type lead | 67 | p0225 |
| Warm flute-type lead | 68 | p0228 |
| Chord-style lead | 69 | p0231 |
| Sound effect: wind | 73 | — |
| Sound effect: ZAP shot (a techno staple percussive hit) | 74 | — |
| Sound effect: sci-fi (**pitch-drop converted to FM, two modulation layers overlapping**) | 75 | — |

### 1.6 Acid (techniques 76–84, p0258–0281)

| | Technique | Page |
|---|---|---|
| What an Acid timbre is | 76 | p0258 |
| **The 303's secret** | 77 | p0259 |
| Basic Acid settings | 78 | p0261 |
| Making use of slides (AUTO mode / substitute notes / humanizing) | 79 | p0263 |
| Bass + high-register riff ①② | 80, 81 | p0266 |
| **Real-time control** (adding unpredictable organic variation) | 82 | p0271 |
| Overdriven Acid ① (Overdrive for "just right" distortion) | 83 | p0275 |
| Overdriven Acid ② (Bitcrusher / downsampling / Fuzz) | 84 | p0279 |

> Technique 82, "real-time control", shares its origin with the anti-AI-sound logic in `SKILL.md` §2:
> **variation produced by a human hand sweeping CUTOFF in real time is something quantization and randomization cannot produce.**

---

## 2. The only recipe here with full parameters: 909 Kick

Because it demonstrates the unconventional approach of **using the filter as a sound source**, it is worth transcribing in full.

> The TR-909 bass drum **does not use an oscillator at all**. The 909 Kick is made almost entirely from a sine wave,
> and the sine wave used here as the sound source comes from **vibration self-generated by resonance** —
> this makes pitch manipulation more flexible.

| Module | Setting |
|---|---|
| **FILTER** | Low-pass (LOW PASS), **−24 dB/oct** |
| **RESONANCE** | **Turned fully right** (so the filter generates its own vibration) |
| **CUTOFF** | Around **8 o'clock** (so that it drops to a lower state after the EG boldly opens it) |
| **FILTER EG** | ATTACK 0 / DECAY **11 o'clock** / SUSTAIN 0 / RELEASE **11 o'clock** (rapid drop); **EG AMOUNT 2 o'clock** |
| **AMP EG** | ATTACK 0 / DECAY 0 / SUSTAIN **turned fully right** / RELEASE **1 o'clock** |

**The result**: the onset has a very high pitch, which quickly drops to a low, drum-like bass.
**For fine-tuning, adjust CUTOFF or the DECAY of FILTER EG** — the detail changes dramatically.

(Score example: Figure ① p0235, CD TRACK 64 p0236)

Other drum parts: TR-808 snare = technique 71, TR-808 hi-hat cymbal = technique 72.

---

## 3. Quick reference for filter and modulation parameters

From PART 1 (p0018–0090), the supporting material for `SKILL.md` §4 and §5.

| Topic | Page |
|---|---|
| Basics of overtones | p0012–0014 |
| Synthesizer structure and sound flow | p0013–0017 |
| Three representative waveforms (sawtooth / square / pulse) | p0019 |
| Triangle / sine / noise | p0022 |
| PWM and waveforms of preset timbres | p0025 |
| TUNE and FINE | p0030–0031 |
| Portamento (glide) | p0031–0032 |
| Amplitude envelope AMP EG | p0034–0036 |
| Filter types (LP/HP/BP/Notch/Comb) | p0037–0038 |
| Low-pass and cutoff frequency | p0040 |
| Applications of high-pass / band-pass / notch | p0046–0048 |
| **RESONANCE and Sweep** | p0049–0051 |
| **KEY FOLLOW** and register overtones | p0053–0054 |
| Modulation and Vibrato | p0055 |
| **LFO** | p0058 |
| **Filter Envelope** (including AMOUNT inversion) | p0061 |
| LFO × OSC / × FILTER / × VOLUME | p0070, p0073, p0076 |
| EG × OSC (changing pitch to simulate instruments) | p0079 |
| OSC × OSC: **FM** for bell sounds | p0080 |
| OSC × OSC: **Ring Modulation (Ring Mod)** | p0082–0084 |
| OSC × OSC: **Oscillator Sync (OSC Sync)** | p0085–0087 |

---

## 4. Vocoder

- Basic principles: p0285
- **Difference between vocoder and EQ**: p0286

> Relationship to this library: vocoded vocals belong to the delivery decisions in `mc-vocal-direction` plus this skill's implementation.
> When used on a generative backend, it falls into **items the backend cannot do** (`honors: none`),
> and needs post-processing on the DAW side — see the backend profile at L4.

---

## 5. Parts not in this library

The following content from the Nozaki book **does not belong to this skill**:

| Content | Where it goes |
|---|---|
| All EQ / compressor chapters of Takeuchi Kazuhiro, "EDM Production" | `mc-mix-intent` (intent) / parameters are a mixing matter |
| Specific insertion of distortion effects and bus routing | A mixing matter, not covered by this package |
| Sample slicing, material management | `mc-rhythm-section` / otherwise not covered by this package |
| Record analyses from Greatest Discs (COCHIN MOON, Aphex Twin, etc.) | Corpus layer L5, as candidate reference tracks |
