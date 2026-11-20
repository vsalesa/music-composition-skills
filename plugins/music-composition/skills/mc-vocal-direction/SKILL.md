---
name: mc-vocal-direction
description: Vocal direction and harmony design - specifying how a vocal should be delivered, not just what notes it sings. The two musical criteria, the vocabulary that actually changes a performance (brighter rather than louder, harder consonants rather than louder), consonant/vowel separation and why the beat lives in the vowel, the anti-perfection pitch philosophy that keeps a vocal from sounding machine-made, the four harmony types with their purpose and delivery, double and triple panning, and how all of this maps onto text prompts for Suno / YuE2 / MiniMax. Use when a vocal sounds flat, machine-made, or buried, when planning harmonies or doubles, when writing the vocal block of an ARR-SPEC, or when a generated vocal is too perfectly in tune. Keywords: singing, vocals, harmony, diction, pitch, double-tracking, AI sound.
---

# Vocal Direction

**This skill covers how the vocal should be _sung_, not just which notes it sings.**

This matters especially for this library, because—

> **The most consistent giveaway of AI vocals is "perfection"**: every note dead in tune, dynamics perfectly flat, every repetition of the chorus sung identically.
> Real singers cannot do this, and do not want to.

So half of this skill teaches **how to ask for "imperfection"**, and **how to write that request in a form a backend can consume**.

## Which sections to read for each task

| Symptom / task | Read |
|---|---|
| Vocal sounds flat, expressionless | §2 vocabulary of performance direction |
| Want the vocal to hit harder | §2.3 Consonants |
| Vocal is "too in tune", sounds like a machine | §4 Pitch philosophy |
| Vocal won't push forward, buried in the accompaniment | §4.1 (usually not a volume problem) |
| Adding harmony, unsure which type | §5 The four types |
| Harmony overpowers the lead / is too showy | §5, the delivery and EQ approach for the relevant type |
| Deciding whether to double | §6 |
| Writing a vocal prompt for Suno / YuE2 | §7 |
| Filling in the vocal block of an ARR-SPEC | §8 and §9 |

## Boundary: what this skill does not cover

| Not covered here | Where it lives |
|---|---|
| How lyrics are written, rhyme, inversion / syllable coordination | **Lyric writing**; the lyrics for the same song are read from `meta.upstream.lyrics` |
| Pitch contour and range design of the melody | `mc-melody` (L1) |
| How words are fitted onto notes (note-to-syllable fitting, *fushi-wari* / extra-syllable fitting, *ji-amari*) | **Lyric writing**, since it is part of the lyric process. On this skill's side: `breath_points` and `phrasing` follow the lines and phrase breaks of the lyrics (one line per phrase, breaths fall at phrase breaks). Without lyrics, write them to the melody's phrases, and check again once the words arrive |
| Concrete EQ frequencies and compression parameters for the vocal | `mc-mix-intent` (intent). Practical implementation is mixing |
| Which instrument the vocal competes with for frequency range | `mc-texture-layering` |
| Synthetic vocal sources (engine parameters of Vocaloid, Synthesizer V) | Not done. This library writes only performance intent (mapped to each backend in §7), not engine parameters |

---

## 1. Required before starting

| Required | Question to answer |
|---|---|
| **① Who is singing** | Voice persona: gender, register, texture, sense of era. **Not merely "female voice"** |
| **② Delivery for each section** | At minimum split verse / chorus / bridge. Write it using the vocabulary in §2, not "emotional" |
| **③ Dynamic contour** | Relative loudness section by section. **Lint #15 checks this; a single dynamic level across the whole song fails outright** |
| **④ Chorus variation per repetition** | What changes in the second and third repetitions (lint #16) |
| **⑤ Harmony plan** | Which type (§5), in which sections, above or below |

---

## 2. Vocabulary of performance direction

### 2.1 Only two musical criteria

> 1. **Does it suit this song**
> 2. **Does it suit this singer (*niatte iru ka*, "does it fit")**

Just these two. **Technical quality is not a criterion**; technique is a means.
In this library, the second criterion becomes "**does it suit this voice persona**".

### 2.2 ★ Do not say "sing louder"

This is the most practical point in the whole section:

> When a grand arrangement is paired with a muddy vocal, **do not say "sing louder"**. The volume fader can solve volume.
> What you most likely want is a "**brighter sound**", so saying "**sing a little brighter**" is more effective.

**Imagery-based instructions** work just as well:
- "Sing with a smile"
- "Corners of the mouth turned up"
- "Sing toward a distant place"

**Why this matters especially for this library**: these are exactly **words a text backend can consume**.
`sing brighter` / `smiling delivery` / `sung toward a far distance` are effective prompts,
whereas `louder` has almost no meaning for a generative model, because it does not control volume.

### 2.3 ★ Think of consonants and vowels separately

This is shared foundational knowledge for performance direction and post-production editing:

- One syllable = **consonant + vowel** (*ka* = K + A, which is clearest when written in romaji)
- **When you want impact, "hit the consonant harder" works better than "sing louder"**
- In editing, distinguish: is this a **timing problem with the consonant**, or a **length problem with the vowel**?
- In mixing, **controlling the level of the consonant alone** can change the expression of a vocal

### 2.4 The "S" as a magic consonant

> **S ≈ white noise produced by the voice: it is essentially noise.**

Corollaries (all practical):
- **You can splice in the middle of an S, and the seam is inaudible**
- **Its length can be stretched or shortened freely without sounding wrong**
- Transplanting an S from another take is essentially seamless

> **★ The beat lives in the vowel, not the consonant.**
> When *sa* (= S + A) is sung on beat 2, the S actually happens at the tail of beat 1.
> **What aligns with the beat is the vowel A.**

**This has two uses**:
1. When editing AI-generated vocals, **"there is an S here" = "this is a good splice point"**
2. When judging whether a vocal is "rushing / dragging" against the beat, **look at where the vowel falls, not the start of the syllable**.
   Otherwise you will misjudge every word beginning with S, SH or TS as rushing.

---

## 3. Analogy with the production chain

A useful comparison (film → popular music):

| Film | Music |
|---|---|
| Script | Lyrics and melody |
| Sets and costumes | **Arrangement** |
| Actor | **Singer** |
| Hair and makeup | **Live performance direction** |
| Cinematography | Recording |
| Editing | Treatment (vocal correction) |
| MA | Mixing |

Live direction + recording + treatment together make up **vocal direction in the broad sense**.

**What this means for this library**: when using a generative model, the "recording" stage disappears,
but **the "hair and makeup" (direction) and "editing" (treatment) stages both remain, and matter more**,
because direction is the only place where you can control the model, and treatment is the only place where you can repair it.

---

## 4. ★ Pitch philosophy: the most counterintuitive section of this skill

### 4.1 Two empirical observations

> - **A flat vocal will not "come through" no matter how high the fader is pushed**
> - **A vocal that is slightly sharp has better penetration (*nuke*)**, and good singers sing slightly high without thinking about it

The first explains a common misdiagnosis: **when a vocal is buried in the accompaniment, check pitch first, then check volume.**

### 4.2 Do not correct everything

> "The singing is good because the pitch is correct" is incomplete. The correct statement is the reverse: **people who sing well are, broadly speaking, in tune.**

So:
- Where the accompaniment is sparse, the moments of being slightly flat or sharp **are themselves "flavor"**
- Where you want emphasis, **being sharp is acceptable**. It is not dragged up afterwards; instead, you **deliberately keep** the places where singers "cannot help singing high in the emotion"
- > **Not everything is aligned; deliberately leaving some parts untouched is what natural tuning looks like.**

**This is this library's core vocal rule against the AI sound.**
Generative models output vocals that are naturally all in tune. What you should do is not "tune it even more accurately", but **specify where inaccuracy is allowed**.

**How to write it**: in ARR-SPEC's `vocal.pitch_policy`, state "which positions keep their deviation",
not "correct to pitch".

**Failure condition**: in sections where the arrangement is very dense and the harmonies are thickly stacked, pitch deviation turns into muddiness rather than flavor.
Those places should be corrected. **The criterion is the density of the accompaniment, not the name of the section.**

### 4.3 The three-step order of treatment

1. **Clean up the splice points between multiple takes**
2. **Align the rhythm**
3. **Correct the pitch**

> **Why this order**: if you move the timing first and splice afterwards, the splice points have to be redone.

---

## 5. The four harmony types

**Each type is defined by three things: purpose / delivery / how to keep it from competing with the lead.**
Note that delivery belongs to this skill, while EQ belongs to `mc-mix-intent`; here only the approach is given.

### Type 1: *Utaiage kami-hamo* (sung-up upper harmony, usually a third above)

- **Purpose**: keep the main melody unchanged while making the overall sound **brighter and more brilliant**
- **Inherent tension**: it sits above the lead, so it naturally stands out, yet it must not overpower the lead
- **★ Solution**: **do not solve this by "singing softer"**, because singing softer loses the brilliance.
  **Keep the full-voiced singing style and solve it with EQ** (approach: let the harmony "escape" the lead's frequency range,
  by cutting the lows heavily, hollowing out the core of the midrange, and where necessary boosting the highs instead)

### Type 2: Upper harmony close to the lead

- **Purpose**: not brilliance, but **creating a sense of air and conveying the chord feeling**
- **★ The key is changing the singing style**: not an open voice, but a **light, breathy, clean style**
- **Note**: the volume will drop, but **do not compensate by moving closer to the microphone** (the proximity effect boosts the lows); use gain control instead

### Type 3: Subdued parallel lower harmony

- **Image**: **"the shadow the lead casts"**. The illustration in the original book shows a singer and their own shadow: the singing style and diction stay as close to the lead as possible, and the shadow itself has no independent expression (p0186)
- **Lower the presence**: cut the lows. The reference EQ in the original book (a six-band equalizer): a low cut at about 110 Hz, plus a −10 dB cut at 123 Hz, −4.9 dB at 247 Hz and −4.2 dB at 621 Hz. This is an overall reduction from low to low-mid, not a single notch (p0186)

### Type 4: *Ai no te* (short responsive phrases between lines, sung by 2–3 voices in unison)

- **Positioning**: relative to the lead, these are **"different objects"**
- **Method**: **reach for EQ first** to change the texture (a radio-like timbre also works; cutting the lows alone can change the atmosphere)
- **Increase unity within the group**: align levels with fader and compression → **apply one shared spatial effect to the group** →
  you may even run the whole group through one shared modulation effect (chain: EQ → compression → chorus → delay)

### Reverb is also part of the type

- Types 1 and 2 can use **reverb or delay rich in high-frequency content** to supply brilliance or air. This extends the idea of "escaping the lead's frequency range" from EQ into spatial effects (p0186)
- Type 3 can **reduce direct sound and increase reverberant content** to lower presence. As the wet/dry ratio shifts toward wet, the sense of a real person singing *here* fades accordingly (p0186)
- Type 4's spatial treatment aims at uniformity: give the whole group the same spatial effect to unify its texture (see Type 4 above). For how the reverb's stereo placement sits alongside the lead's, see §6.2

---

## 6. Doubles and stereo placement

### 6.1 Doubling the lead: a clear trade-off

> - **Doubling a lead with excellent diction dilutes the sense of the words**
> - But the stereo solidity unique to doubles brings **warmth and thickness that machine copying cannot produce**

★ Note the phrase "machine copying cannot produce". It also explains why
**a "double track" output directly by a generative model sounds fake**: it is a copy, not a second performance.
To get a real double, the backend must **generate it a second time**, rather than copying one track and adjusting it.

**Operational points**:
- **The lead take must be selected first**, because the double is sung while listening to and hugging the lead
- But choosing slowly makes the singer wait around. **It is better to record the double immediately, while the singer still remembers the diction** (a trade-off between time and quality)
- For songs with complex diction: **record them phrase by phrase, carefully**
- **Check method**: hard-pan the two tracks left and right, or **mute the lead**, and strictly check whether the double is hugging the lead
- **Guiding principle**: **do not let the lead's diction be erased**. Have the singer record the double in a **style that emphasizes diction**, which is precisely the point

### 6.2 Stereo placement strategy

| Form | Approach |
|---|---|
| **Single** | Without a specific reason, place it **dead center**. Create distance and depth from the lead with volume, reverb and delay. For harmonies in the extreme high or low registers, **use a different microphone from the lead's** |
| **Double** | Can be panned apart left and right. **The more extreme the pan, the more it stands out, and it is emphasized even at low volume**, so pan far the parts you want emphasized. When both the upper and lower harmonies have doubles, **pan only one pair**; panning both pairs to extremes adds too many elements. If only the harmonies are wide in the arrangement, it sounds odd (deliberate use is fine), so **consider the reverb's stereo placement together** |
| **Triple** | Think of it as "**single + double**": the single handles depth, the double handles width. **Pulling the single's volume down** gives a cleaner result |

### 6.3 Guidance for recording harmonies

Singers who sing the main melody well often find harmonies surprisingly hard, **because harmony lines are subtly similar to the melody and are hard to memorize**.

**The guide track (*gaido*) is the most common solution**:
- Create a new track and play the harmony line on a **soft timbre with a weak attack**
- Tips: **deliberately play an octave higher** to make it easier to hear clearly; make a 1-bar line into a **2-bar loop**; you may **pan it only to one side of the headphones**
- Once the singer is familiar, **gradually lower the guide volume**, then record the final take
- **The most effective approach is actually singing it to them**. Instrument timbre and the voice are completely different things,
  and it is extremely hard for a lead singer who does not play an instrument to "mentally swap the instrument sound for a voice in their head",
  especially when the lyric syllables are arranged in complicated ways

> **Mapping to this library**: when using generative backends, the "guide track" corresponds to **giving the model a reference melody or reference audio**.
> The same principle applies: **letting the model hear a voice works better than showing it an instrument MIDI**.

---

## 7. Mapping to each backend

| Backend | What it can take | How to write it |
|---|---|---|
| **Suno / MiniMax** | Natural-language delivery descriptions | Use the vocabulary in §2.2: `brighter`, `breathy`, `harder consonants`, `smiling`. **Do not write `louder`** |
| **YuE2** | Same as above, and can vary by section | Write delivery section by section, which matches the required item ② in §1 |
| **MIDI / DAW (recorded by a real singer)** | The full §2–§6 | Use directly as the direction sheet |

**Two rules common to all backends**:
1. **Dynamics must differ from section to section** (lint #15)
2. **Every repetition of the chorus must change** (lint #16). Choose at least one or more of: add harmony, change delivery, add a double

**Handling differences in backend capability**: if a backend does not accept delivery descriptions at all (`honors: none`),
those items should be **excluded** when calculating the compliance rate, rather than given a score of 0. See the backend profile rules in L4 for details.

---

## 8. Mapping to ARR-SPEC fields

| Field | Section of this skill |
|---|---|
| `vocal.persona` | §1 ① |
| `vocal.delivery` (can vary by section) | §2 |
| `vocal.dynamics_by_section` | §1 ③, **lint #15** |
| `vocal.chorus_variation` | §1 ④, **lint #16** |
| `vocal.pitch_policy` | §4.2 (write **where deviation is kept**, not "correct to pitch") |
| `vocal.stacking` | §5 four types and §6 doubles (including type / section / delivery / stereo placement) |

---

## 9. Checklist to pass after writing

- [ ] The voice persona is specific enough that you can imagine **who it is**, not just "female voice"
- [ ] Each section has its own **delivery**, using actionable terms such as "bright / breathy / consonants hit hard"
- [ ] **"Sing louder" is not written anywhere**
- [ ] Dynamics **differ from section to section** (lint #15)
- [ ] The chorus **changes something in every repetition**, and you can state what changed (lint #16)
- [ ] `pitch_policy` states **where inaccuracy is allowed**, not "correct to pitch"
- [ ] A harmony type is chosen, and its **delivery and "how it avoids competing with the lead" are both written**
- [ ] Type 1 harmony does **not** avoid competing by "singing softer"
- [ ] If doubling, the requirement is a **second performance**, not a copied track
- [ ] When both upper and lower harmonies have doubles, **only one pair** is panned to extremes
- [ ] When judging whether a vocal is rushing or dragging, the position of the **vowel** is what is checked

---

## Appendix: Sources

- **Takayama Hiroshi, *Melody Writing for Popular Music Composition*** (*Popular Music Composition Melody Methods*, expanded edition) together with ***A Book That Explains How Professionals Write Songs*** (*Puro no Kyokusaku ga Wakaru Hon*). These form the backbone of §2, §4, §5 and §6.
- The EQ reference example for Type 3 in §5, and the three points on "reverb is also part of the type", come from ***A Book That Explains How Professionals Write Songs*** (p0186).
- **The lyric-to-melody alignment part (note-to-syllable fitting, extra-syllable fitting and intonation) is not covered in this skill.**
  It belongs to **lyric writing**, since it is part of the lyric process.
- The concrete parameters of the vocal mixing chain (compression ratios, EQ frequencies, the 309.6 Hz example for removing pop noise, etc.)
  are compiled in [reference.md](reference.md). Practical implementation is mixing.
- The method for self-checks #15 / #16 is described in `mc-workflow` §3.0.
