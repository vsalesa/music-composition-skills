# mc-vocal-direction Reference: Microphones, Recording Conditions and Vocal Chain Parameters

> `SKILL.md` covers how to specify a performance; this file covers **what to prepare for recording one vocal**,
> and a reference vocal mixing chain.
>
> Sources: Takayama Hiroshi, *Melody Writing for Popular Music Composition* (expanded edition) and *A Book That Explains How Professionals Write Songs*.

---

## 0. Is this content still useful to people using generative backends?

**Partly yes, partly no.**

| Content | When using generative backends |
|---|---|
| Microphone selection, placement, proximity effect | **Not useful**, though the "pairing logic" in §1 is still **a way of choosing the voice persona** |
| Design of monitoring (cue mix) | **Not useful** |
| Vocal chain parameters (§3) | **Reference**. Use them to judge what a generated vocal is missing |
| De-esser and sibilance | **Useful**. Sibilance problems in generated vocals are very common |
| §4 recording standards | **Useful**. It defines the minimum format standard for a deliverable vocal |

> Reason for keeping the full content: this library's L4 compile layer supports the MIDI/DAW backend, and that path requires a real singer recording.
> These parameters also serve as **a frame of reference for judging generated output**.
> Knowing how a good vocal is made tells you what the model's output is missing.

---

## 1. Microphone selection

**Photography analogy**: microphone = lens; preamp + sound card = camera body; DAW = film.
**The same microphone sounds different through different preamps.**

| | Dynamic | Condenser |
|---|---|---|
| Characteristics | Sturdy, cheap, needs no power supply | Delicate and fragile, expensive, needs phantom power |
| Positioning | **Standard for live performance** | **Standard for studio recording** |
| Sound | — | "The sound is simply better": it **picks up even breath**, with even high- and low-frequency response |

**How to choose**: **have the singer actually sing and listen through the microphone**. Check three points:
1. Whether the hardness or fullness of the voice **suits this song**
2. Whether the **midrange** you want is being captured
3. Whether the **singer is comfortable singing into it**

**Pairing with the arrangement**:

| Arrangement | Microphone |
|---|---|
| Soft | Soft-voiced microphone |
| Hard | Microphone with a hard-edged character |
| Rock impact | One with **a distinctive low-midrange** |
| R&B texture | **Sparkling high frequencies** |

> When an engineer is present, **simply describe your feeling in plain words**:
> "I want it more gorgeous", "I want a brighter sound", "I want it to feel more like summer". Any phrasing works.
> ★ This is the same principle as `SKILL.md` §2.2, and it applies equally to writing prompts.

---

## 2. Placement, distance and environment

| Item | Key points |
|---|---|
| **Orientation** | Face the microphone as directly as possible. **Singing while looking at the lyric sheet records a "soft-focus voice"**, so plan the geometry of the music stand and the microphone in advance |
| **Do not over-direct** | Asking for too much makes the singer stiff. **Prefer letting the singer move, to capture a vocal with rhythmic feel** (a stomp's "thud" gets absorbed by the studio carpet) |
| **Proximity effect** | The closer to the microphone, **the more the lows are emphasized**. Keep a moderate distance; for a rock flavor, **recording deliberately close** is also an option |
| **Height relationship** | Having the microphone directly in front of the mouth is the baseline. **Mouth above the microphone → picks up more low end; mouth below the microphone (microphone angled down from above) → picks up more high end** |
| **Accommodate habits** | If the singer usually sings while holding a guitar, or prefers to sing seated, arrange the session around that habit |

**Special case**: when a singer becomes jittery and cannot sing well because the monitoring is too clear,
**deliberately lower the microphone's level**, or **add more reverb in the cue mix**.

### 2.1 Monitoring (cue mix)

- How loud the singer's own voice is in their headphones **is up to the singer**, but if it is too loud, it becomes **hard to control pitch**
- A strong rhythm section gives the vocal a sense of groove, but it can **cover the parts that serve as pitch references**
- ★ **Heavy compression in the monitoring chain is not recommended**: the singer cannot hear their own dynamics, which hinders their development.
  "Singing harder and harder with no tactile feedback" can actually produce a thin voice

---

## 3. Lead vocal chain (goal: the vocal "emerges" from the accompaniment)

**In order**:

| # | Process | Parameters (example) | Key points |
|---|---|---|---|
| 1 | **Compression** | WAVES Renaissance Compressor, **Ratio ≈ 4:1 (4.27:1), Attack 16 ms, Release 160 ms** (slightly slow attack) | **Do not squash it.** In ordinary sections the meter barely moves; set the threshold so that it compresses **3–4 dB when the chorus level rises**. The aim is to "gently flatten the vocal's fluctuations" |
| 2 | **Limiter** | WAVES L1 | Raises overall loudness. The Maximizer **can raise loudness while preserving the expressive contour of the performance** (parts that are about to be buried get lifted) |
| 3 | **EQ** | WAVES Renaissance Equalizer | **Boost high frequencies** to emphasize the edge content of the voice. **Also boost around 125 Hz in the low end** (example: a 151 Hz peak at **+6.9 dB**). This band "does not sound much like a voice", yet it lifts the voice's **latent thickness and presence** (a technique approaching the texture of Western singers). Watch the level rise and beware of clipping |
| 4 | **Short delay** | AVID Mod Delay II, **run via a send** | Creates a sense of width similar to a chorus. Too much makes it "smear (*nijimi-kan*)". **Set it right at the threshold of audibility** |
| 5 | **Reverb** | AVID Reverb One | Add **a thin layer** at the end |
| 6 | **Final balance** | — | After the vocal is processed, if you want the accompaniment to stand out more, **lower the entire vocal slightly** |

### 3.1 The R&B "pinned to the front" technique

**Multiband compression**: WAVES C4 (four bands, emphasizing mainly low and high frequencies) = **used as EQ and compression at the same time**,
so the vocal sits "flatly pinned at the very front".

**Cost**: **vocal expression in the chorus and similar passages gets flattened.**
In pop outside R&B, this risks destroying vocal expression.

**When doing this kind of processing, use automation to fine-tune the volume and preserve the song's inherent dynamics.**

### 3.2 De-esser

> A de-esser is **"a compressor focused on the sibilance frequency band"** (example: **FREQ 7.0 kHz / RANGE −5.0 dB**).

**Overdoing it produces a muffled, "tongue-tied" vocal**.
This in turn proves **how important consonants are** (see `SKILL.md` §2.3).

> ★ The sibilance of generated vocals is often too heavy or too light. This gives a test:
> **if you can hear a "tongue-tied" quality, the de-esser has been overdone**, so leave a little more in place.

---

## 4. Two specific treatment techniques

### 4.1 Removing pop noise: the "dynamic EQ" method

1. Find the plosive point and **loop only that short segment**
2. Insert a **steep high-pass filter** and **slowly raise the cutoff frequency from low to high** until the "pop" disappears
   (example: **around 300 Hz, precisely 309.6 Hz**)
3. **Render only that segment offline**, **paste it back in place** on the original track, and **join both ends with a crossfade**

### 4.2 Taming an out-of-control vocal (large swings in level)

- **Compression example**: WAVES Renaissance Compressor,
  **Attack 24.9 ms / Release 16.6 ms / Ratio 4.72:1**, plus WAVES L1
- ★ **The threshold is the key**: set it to "ride the critical point". **Set too shallow, the level difference cannot be pulled in; set too deep, the singing becomes unnatural**
- If compression is not enough: use **fader automation** to lift the quieter waveform sections as a finishing step
- > In the DAW era, **it is entirely feasible to use no compression at all and level everything through automation**.
  > It can even draw complex curves that compression cannot follow, with no unnaturalness whatsoever. **Levelling with automation first is recommended.**

---

## 5. EQ examples for harmony and doubles

Parameters belong to mixing. Example values are kept here only for reference (for type definitions see `SKILL.md` §5):

| Type | EQ approach |
|---|---|
| **Type 1** (sung-up upper harmony) | **Let the harmony escape the lead's frequency range**: cut the lows heavily, **hollow out the core of the midrange**, and where necessary boost the highs instead |
| **Type 3** (subdued lower harmony) | Cut the lows. Example: **110 Hz low cut, 123 Hz −10 dB, 247 Hz −4.9 dB, 621 Hz −4.2 dB** (an overall attenuation of the low-mid range) |
| **Type 4** (aizuchi) | **Adjust the EQ first to change the texture** (a radio-like timbre also works); the whole group shares a spatial effect; chain: **EQ → compression → chorus → delay** |
| Reverb pairing | Types 1 and 2 use **high-frequency-rich reverb/delay** to supply brilliance; Type 3 **reduces direct sound and adds reverb** to lower presence |

---

## 6. Delivery standards and workflow (from the original book, §6)

The original skill pack's section "Demo trio and studio data standards" covers:

- The **pre-session trio** for the lead singer
- **Audio format standards**
- **Iron rules for data** taken into the studio
- Conventions for **writing scores** for the studio
- The professional production workflow (tracking along the rough mix)
- A quick reference of professional practice (studio jargon) and a checklist of common tasks

> This section is **mostly irrelevant to this library** (we do not go into a studio), but **the "audio format standards" and "iron rules for data" subsections
> should be absorbed by the L4 compile layer** as format constraints on deliverables.
> Source: the section on delivering recordings in *A Book That Explains How Professionals Write Songs*.

---

## 7. Parts not in this file, covered elsewhere

| Content | Where it goes |
|---|---|
| **Lyric–melody alignment**: intonation (pitch accent), word rhythm, segmentation, **note-to-syllable fitting (*fushi-wari*)**, the four methods of syllable correction, **extra-syllable / missing-syllable fitting (*ji-amari* / *ji-tarazu*)** | **Lyric writing**, since it is part of the lyric process |
| Rhyme (*in*), seven-five meter, rhetoric | Lyric writing |
| The two workflows **words-first (*kotoba-saki*)** and **music-first (*kyoku-saki*)** | Lyric writing. On this package's side, whoever goes first sets the shared six fields, and the party who goes second only reads them (`mc-workflow` §5.1) |
| Rules for English syllables, *fake* (improvised ornamentation) | Lyric writing / this skill §2 (delivery part) |
| Guide vocal demos (*kari-uta*) and competitions (competitions, *konpe*) | Not covered in this package (this library does not involve commercial workflows) |
| Practical EQ and compression tutorials | Mixing; not covered in this package |
