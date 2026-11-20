---
name: mc-mix-intent
description: Mix intent as a handoff artifact - stating what a mix must achieve so a human engineer, a DAW, or a generative backend can all act on it, without prescribing EQ or compressor settings. The five domains (time, frequency, level, stereo, depth) and the imagined sound stage, the four goals (mood, balance, definition, interest), where balance is required and where depth must be consistent instead, the two legitimate reasons to be unbalanced, why sustained pads mask far more than short percussive hits, and how to use reference tracks as calibration. Use when writing the mix_intent block of an ARR-SPEC, handing a session to an engineer, deciding what a backend can actually honor, or diagnosing a mix that is technically clean but emotionally wrong. Grounded in masking (low masks high), critical bands, temporal masking, localization cues and the precedence effect. Keywords: mix intent, sound stage, masking, critical bands, balance, reference tracks, handoff.
---

# Mix Intent

**What this skill produces is intent, not parameters.**

The distinction matters:
- "Vocals +2 dB at 3 kHz" is a **parameter**. Only a DAW can execute it, and it is useless once the backend changes.
- "The vocal must stay the clearest element in the densest chorus, and it is the pad that yields, not the guitar" is **intent**. A human engineer can execute it, a DAW can execute it, a text backend can partly execute it, and it can be checked item by item at acceptance.

**This library stops at intent.** EQ frequencies, compression ratios and the mastering chain belong to mixing. This package supplies only the `mix_intent` block.

## Which sections to read for each task

| Symptom / task | Read |
|---|---|
| Filling in the `mix_intent` of an ARR-SPEC | §2–§4, then §8 |
| Mix is technically clean but "wrong" | §3.1 Mood |
| Unsure whether to pursue balance | §4 (**depth should be consistent, not balanced**) |
| Parts are covering each other | §5 Masking (**usually a pad problem, not a drum problem**) |
| Handing off to a mix engineer | §2 five domains, plus the handoff format in §8 |
| Judging how much a backend can take | §7 |
| Looking for reference tracks | §6 |

## Boundary: what this skill does not cover

| Not covered here | Where it lives |
|---|---|
| EQ frequencies, compression ratios, reverb parameters, bus chains, mastering | **Mixing**. This package supplies only the `mix_intent` block (for the fields handed off and how to read them, see `mc-workflow` §5) |
| **Rewriting** solutions to frequency conflicts (changing register, removing notes, alternating) | `mc-texture-layering` (**solve it there first; only bring it here if it cannot be solved there**) |
| Structural planning of foreground / midground / background | `mc-texture-layering` §2 |
| How the vocal should be sung | `mc-vocal-direction` |
| Concrete placement plans for harmony and doubled vocals | `mc-vocal-direction` §6.2 |
| How to design the timbre itself | `mc-sound-design` |
| Left/right and high/low layout of the individual pieces **inside** the drum kit | `mc-rhythm-section` §6 (this skill's sound-stage map only decides where the **drum kit as a whole** sits) |

> ★ Boundary with `mc-texture-layering` (repeated here because it is the easiest to confuse):
> **The texture-layering solution is "rewrite"; the mix-intent solution is "remix".**
> Anything a rewrite can solve should not be left to the mix.

---

## 1. Required before starting

| Required | Question to answer |
|---|---|
| **① Mood** | One sentence on what this mix must convey. **Write this first; it overrules every later decision** |
| **② Sound-stage map** | Left/right and front/back position of each instrument (§2) |
| **③ Lead sequence** | Section by section: who is the clearest element in this section |
| **④ Yielding relationships** | Who yields to whom, and when (`ducking_map`) |
| **⑤ Reference tracks** | At least one, and be able to say **which specific aspect** of it you are referencing |

---

## 2. Five domains and the sound stage

The mixing process must address **5 main domains** (p0089):

| # | Domain |
|---|---|
| 1 | **Time** |
| 2 | **Frequency** |
| 3 | **Level** |
| 4 | **Stereo** |
| 5 | **Depth** |

> **Stereo and depth together make up "space"** (p0089).

**Sound stage**:
> A mix should be presented within an **imagined sound stage**, in which each instrument has a certain **left/right (stereo)** and
> **front/back (depth)** position (p0089).

**This is the skeleton of the handoff format**: one sound-stage map plus one sentence for each of the five domains, and the mix engineer can start work.

**What cues place a sound left/right and front/back** (Howard & Angus):
- A pan pot provides **level differences** (p0112). Level differences mainly work for localizing high frequencies, and time differences mainly work for low frequencies. **700 Hz–2.8 kHz is the transition zone between the two cues, where localization is weakest** (p0108).
  → Panning low-frequency elements has essentially no effect, so centering them is enough. To make an instrument's position clear, it needs content above 3 kHz.
  Failure condition: headphone monitoring (in-head localization, p0109).
- Front/back position depends on the ratio and time gap between direct sound and reverberant sound (p0261, p0264). Delayed sound arriving within 30 ms is not heard separately, and localization stays with the leading sound (precedence effect, p0110). An initial delay of 10–20 ms is a natural front/back spacing; 50 ms is an echo (p0346).
  → For depth, write only three values, "near / mid / far", not milliseconds.

**Macro vs micro** (p0089):

| | Targets | Example |
|---|---|---|
| **Macro mixing** | Elements that affect the whole mix | The frequency balance of the mix |
| **Micro mixing** | Each instrument part handled individually | Whether the vocal sounds natural |

**This skill mainly specifies the macro level.** Micro work is the mix engineer's craft and should not be fixed by the arrangement spec.

---

## 3. Four goals

A mix has 4 basic goals (p0089):

| # | Goal |
|---|---|
| 1 | **Mood** |
| 2 | **Balance** |
| 3 | **Definition** |
| 4 | **Interest** |

> **When evaluating a mix, first look at the coherence and appeal it shows across the main domains, and only then analyze how fully it meets each goal** (p0089).

### 3.1 ★ Mood: it has veto power

> Mood refers to whether the mix can express the **emotional content** contained in the music (p0090).

Two counterexamples make the point clearly (p0090):
- **Heavy compression, extreme EQ, noisy distortion, a snare that hits too hard** → ruins a **gentle jazz** piece
- **Sweet vocal reverb, an overly harmonious drum kit, soft guitar** → ruins a piece **full of anger**, i.e. heavy metal

Note the second example: **each item on its own looks like a sign of a "good mix", yet taken together they are wrong.**
**Technically correct does not mean emotionally correct.**

> **A mix engineer who is only good at one style of music often performs poorly on other styles** (p0090).

**What this means for this library**: a generative model is also "a mix engineer who is only good at one style". It will pull any input toward whatever balance it has seen most.
So `mix_intent.mood` must be fixed, and **placed near the front of the prompt**.

### 3.2 Definition

> **Definition describes whether a sound is heard as clear and identifiable** (p0090).

On the spec sheet this becomes the **lead sequence** in §1③: section by section, state clearly who must be identifiable.

Definition is essentially part of separation. Whether an instrument is clear depends on whether it can be heard and identified (intelligibility), and also on whether it sounds natural. How loud it is matters little (p0260). Two counterexamples test this: a piano recorded as if it came up from the bottom of the sea, or a hi-hat missing its basic high frequencies. In both cases the level may be normal, yet definition has collapsed (p0260).

Level and definition are often treated as simply proportional, "the louder the instrument, the clearer it is" (p0100). But this holds only when the instrument's own frequency content is healthy. An instrument with a defect in its frequency content only gets bigger when you raise its level, not clearer (p0100). When diagnosing "this part is not clear enough", first decide whether it is not loud enough or has a hole in its frequency content, and only then decide whether to raise the level.

### 3.3 Interest

Interest often comes from **violating balance** (see §4.3), but violating balance is only one extreme form of interest. The underlying mechanism is more basic: the ear adapts, and when a sound stays unchanged for a long time, attention drops. Only change can pull the ear back (p0091). Repeating verses and choruses, doubling tracks, and changing instrumentation all work by creating change to sustain attention (p0091).

A mix can add a layer of change on top of the arrangement's structure. The test is "which section has it and which does not", without any specific parameters (p0092):
- A part is pushed up through automation only in specific sections
- An instrument appears only in specific sections (example: a trumpet enters only when the verse repeats)
- The same instrument gets different processing in different sections, so brightness and darkness change with the section
- The chorus squeezes the overall sound harder and allows the bass to distort
- The snare gets different reverb in different sections

Style decides how far to go: ambient music should hold interest without being too catchy; trance relies on repeating one theme, so its changes must be finer to avoid becoming tiresome (p0092).

**How to write it**: these change points go by section into `focus_by_section[]`. Unbalanced changes go into `deliberate_imbalance[]` (§4.3). None of them should be written as a single state applied to the whole piece.

---
## 4. Balance: where to seek it, and where not to

### 4.1 Three domains where balance is sought (p0090)

1. **Frequency balance**: a lack of mid and high frequencies makes a mix sound muddy and blurred, and makes the sound stage seem further away (p0090). The test is not to boost to a specific number. It is this: once the listening impression falls into the three words "muddy, blurred, distant", the mid and high frequencies are lacking.

2. **Stereo image balance**: supported by level balance and frequency balance together, aiming for the overall image to be left/right symmetric (for example guitars, shakers, backing vocals) (p0252). "Balance" here refers to the **overall** image distribution. It does not require every single instrument to be centered. Centering is actually the position with the worst definition (see the localization cues in §2).

3. **Level balance**: this means **relative level**, not absolute level. A mix assessment asks "how loud is this instrument relative to the others", not "how loud is this instrument by itself". Turning up the monitoring volume overall does not solve a relative-level problem (p0097). Relative level is usually set by how important the instrument is at that moment, and it must follow the song's progression. For example, the level of a lead guitar solo section should be higher than in the accompaniment sections (p0098).
   Cost: if you press all the hits down to one level to make relative levels neat, the drum kit will sound like a "drum machine" and lose the timbral variation that comes from natural dynamics. Level balance does not mean uniform levels (p0388).

### 4.2 ★ Depth should be **consistent**, not **balanced**

> **Depth problems should be solved by consistency, not balance** (p0090).

> Example: if the **kick drum sounds as close as an ear-level whisper while the snare sounds as far away as the neighbor's house**, the whole drum kit ends up with an **extremely distorted spatial layout in depth** (p0090).

This is easily misread as "depth should also be centered". It is not.
**Depth may be uniformly close or uniformly far overall, but within one group of sound sources it must be consistent.**

**Self-check action**: list the instruments by group (drum kit, keyboard group, string group) and their depth values.
**If the difference within a group is larger than the difference between groups, something is wrong.**

Physically, "the same group" means sharing the same set of early reflections and reverb tail. Early reflections can differ for each position in the image, but the decay rate of the tail must be the same (Howard & Angus p0348–0350).

### 4.3 Two cases where imbalance is allowed (p0090)

1. **Creating a deliberate sonic effect**
2. **Making the song interesting**

> Example: in Delgados' "The Past That Suits You Best", the mix engineer Dave Fridmann placed the **drum kit and vocals entirely in one channel**, creating an effect that is unbalanced in stereo but compelling (p0090).

> **Interesting imbalance is usually a momentary treatment**, such as doubling some low-frequency signal in a climactic passage of a dance track (p0090).

**The phrase "usually momentary" is the key**: imbalance is an **event**, not a **state**.
Imbalance across the whole piece is an error. Imbalance at one point is a technique.

**How to write it**: imbalance goes into `mix_intent.deliberate_imbalance[]`, with **start and end bars** and a **reason**. Any imbalance without a bar range is treated as a mistake.

---

## 5. Masking: why problems are usually in the pad, not the drums

> **Core principle of masking**: a loud sound masks a quiet sound;
> one instrument's frequency range masks another instrument's frequency range (p0038).

But the most useful point is the following inference along the **time dimension**:

> - **Percussive instruments (such as the kick drum) sound for a short time and mask little**
> - **Instruments that sustain (such as a sawtooth pad) fill the spectrum and the stereo space and mask a great deal** (p0038)
> - ★ **Raising the level of a dense pad part brings more masking than raising the kick drum's level.
>   A pad masking the kick is a major problem because it happens continuously** (p0038)

Howard & Angus explain these as mechanisms:
- **Masking spreads upward: low frequencies readily mask high frequencies**, and the reverse is much weaker (p0239). So a pad's low frequencies do not only cover the kick; they mask everything above them. Hence "leave the low end of the pad empty" is the first cut.
- Within the critical band containing the masking sound, the masking threshold is only about 20 dB below the masking sound (p0240). So yielding must be effective: a part counts as having "yielded" only when it is more than 20 dB quieter in the same frequency band. Being 3 dB quieter only makes it muddy.
- **Temporal masking**: for 100–200 ms after a loud sound stops, a quiet onset remains inaudible. Backward masking (post-masking) lasts only about 10 ms and is almost nonexistent (p0241). The perceived loudness of a short hit is also discounted by its duration: sounds under 200 ms sound quieter the shorter they are (p0095).
  → **When a vocal or hook enters right after a crash or fill, either leave a gap of ≥ 200 ms, or make its first note loud enough on its own.**
  Self-check: find the entry point of each lead element, and check whether something louder has just ended within the 200 ms before it.

**Corollary (how this library uses it)**:
When diagnosing "muddiness", **check the sustained sounds first, not the percussion**.
Intuition always points to "the drums are too big", but by this principle the culprit is more likely the pad or the bed guitar that never stops.

**The first-choice solution still lies upstream**: leave the pad's low-frequency range empty (a rewrite, `mc-texture-layering`), rather than pushing it down with sidechaining (a remix). **Sidechaining is for use only when a problem cannot be solved otherwise.**

---

## 6. Reference tracks: this library's calibration tool

### 6.1 Six uses (p0051–0052)

| Use | Description |
|---|---|
| **As a template to imitate** | An excellent training method, but "imitation is the greatest enemy of creativity"; and differences in type of work can make imitation fail |
| **As a source of inspiration** | Played **before** mixing starts, to spark direction |
| **As a breakthrough when stuck** | Study the **differences** between your mix and the reference |
| **As a finished-product reference** | After completion, compare frequency response and levels |
| **Calibrating your ears** | In an unfamiliar environment, first play a familiar reference track to get to know the speakers, room and seating position |
| **Evaluating speakers** | Play a work you know well yourself; this is more useful than the pop music a shop plays |

### 6.2 Selection and pitfalls

- Reference tracks should **match the type of mix** (if you are mixing string music, find ones with strings; if you are doing chill-out, find similar chill-out) (p0051)
- Store them in **lossless format**, not MP3 (p0051)
- Ideally include **pre-selected excerpts** for quick comparison; you may add **unmixed stems** (p0051)
- ★ **Be aware of the effect of mastering** (p0052): a mastered reference track is usually denser in dynamics
  (consistent relative levels plus heavier compression), and its frequency characteristics may have been altered to suit the **least favorable** song on the album
- ★ **Match loudness before comparing**: equal-loudness contours change with sound pressure level. When the volume drops, low and high frequencies are suppressed relative to the midrange, and the sound becomes thin and dull (Howard & Angus p0091). A +10 dB increase in sound pressure level roughly doubles perceived loudness (p0094).
  The louder of two versions almost always "sounds better". If loudness is not matched, you are comparing volume rather than mixes.

**This last point is especially important for this library**: when deriving metrics from a finished audio file, the measured dynamic range is **after mastering**. So using a reference track's dynamic value as a target systematically biases the target too tight.
Likewise, before measuring a reference track, first check its bitrate and high-frequency cutoff: lossy encoding removes high frequencies, so files at different bitrates cannot be compared directly.

---
## 7. What each backend can take

| Backend | Can take | Cannot take |
|---|---|---|
| **Suno / MiniMax** | Mood and overall texture descriptions (`warm`, `dry`, `wide chorus`) | Sound-stage map, ducking_map, per-section depth |
| **YuE2** | Same as above, with finer section granularity | Precise stereo placement and depth |
| **MIDI / DAW** | Everything. Use directly as the direction sheet | — |

**★ Rule**: items marked `honors: none` in a backend profile
must be **excluded** when calculating the compliance rate, and must **not be given a score of 0**.
Otherwise, a backend that honestly declares "I cannot do stereo placement" would score lower than one that pretends it can. That would push the scoring system in the wrong direction.

---

## 8. Mapping to ARR-SPEC fields

| Field | Section of this skill |
|---|---|
| `mix_intent.mood` | §3.1 (**one sentence, placed early in the generation prompt**) |
| `mix_intent.sound_stage[]` | §2 (pan and depth for each instrument) |
| `mix_intent.focus_by_section[]` | §3.2 lead sequence |
| `mix_intent.ducking_map[]` | §5 (who yields to whom, and when) |
| `mix_intent.deliberate_imbalance[]` | §4.3 (**must include start and end bars and a reason**) |
| `mix_intent.reference_tracks[]` | §6 (**must state which aspect of it is referenced**) |

---

## 9. Checklist to pass after writing

- [ ] `mood` is written, **in one sentence**, and does not conflict with the later decisions
- [ ] Each of the five domains **has one sentence**, not just frequency
- [ ] Every instrument on the sound-stage map **has both a left/right and a front/back value**
- [ ] **Depth is consistent within each group of instruments** (inside the drum kit, inside the string group)
- [ ] The **clearest element** is written for each section
- [ ] Every imbalance has **start and end bars and a reason**, not a whole-piece state
- [ ] When diagnosing "muddiness", **the sustained sounds were checked first**, not the drums
- [ ] Within 200 ms before each lead element's entry point, nothing louder has just ended (§5)
- [ ] Low-frequency elements are centered in the image; loudness is matched when comparing to a reference track (§2, §6.2)
- [ ] Conflicts that can be resolved at the composition level **were already resolved in `mc-texture-layering`** and not pushed here
- [ ] At least one reference track, **with the aspect being referenced stated**
- [ ] No EQ frequencies or compression ratios are written in this file (those belong to mixing)

---

## Appendix: Sources

- **Roey Izhaki, *Mixing Audio*** (a mixing guide). This is the backbone of §2, §3, §4, §5 and §6 (domains and goals of mixing from chapter 6, goals of mixing from 6.1, masking from 2.x, using reference tracks from 3.4). Page numbers refer to the book's pages.
  **This library takes only the "domains and goals" and "reference tracks" parts.** The practical chapters on EQ, compression, reverb and mastering belong to mixing and are not included in this package.
- **Howard & Angus, *Acoustics and Psychoacoustics*** (Chinese edition). Covers the localization cues and precedence effect in §2, the reverb tails in §4.2, the masking mechanisms and temporal masking in §5, and the equal-loudness contours in §6.2. Page numbers refer to the Chinese edition's pages.
- **Takeuchi Kazuhiro, *EDM Production*** (Chinese title: *EDM Zhizuo*). Drawn on for frequency balance and Lo-Mid management, and for balancing volume across parts. Only the intent layer is taken here; the parameter summary is in [reference.md](reference.md).
- The definitions of backend profiles and `honors` are in `mc-render-compile` §6 and in [`backends.yaml`](../mc-workflow/backends.yaml).
