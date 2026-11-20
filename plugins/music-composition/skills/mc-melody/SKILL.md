---
name: mc-melody
description: Melody writing - what a melodic line expresses and how to make it singable. Direction and interval width as expression, the hard limits on leaps and how to prepare and land them (windup, run-up, cushion, rebound), range setting against the human voice and the passaggio, long and short note values, cadence treatment and the eight degrees of closure, motive-phrase-section construction and the six causes of segmentation, and a checklist against predictable cliche. Use when writing or fixing a melody, when a line is unsingable or bland or too predictable, when deciding a key and range for a specific singer, when a melody gets buried by the accompaniment, or when filling melody_register in an ARR-SPEC. Keywords: melody, tune, leap, range, phrase, motif, hard to sing, too predictable.
---

# Melody Writing

> **A melody = one pitch moving through time.**
> All of its expressiveness comes from four things: the **direction, width, note value, and metric position** of that movement.

This skill covers **the line itself**. It does not cover which chords sit under it (that is `mc-harmony`),
nor which words are set to it (that is **lyric writing**).

## Which sections to read, by task

| Symptom / task | Read |
|---|---|
| Writing a melody from scratch | §1 Required before starting → §2 → §5 |
| Melody is flat and boring | §2 Width + §8 Anti-cliché |
| Hard to sing / can't reach the notes | §3 Hard limits on leaps + §4 Range |
| Setting the key for a specific singer | §4.2 Passaggio |
| Every step is predictable | §8 Predictability checklist |
| Loose, won't hold together | §7 Motive and syncopation |
| Strong start, weak finish | §7.4 + §6 Closure |
| Buried by the accompaniment | §9 Diagnostic table |
| Ending doesn't feel final enough | §6.3 |

## Boundary: what this skill does not cover

| Not covered here | Where it lives |
|---|---|
| How to choose chords, matching melody to harmony | `mc-harmony` |
| Form, how long sections are, how the whole song is put together | `mc-form` (theory) / `mc-arrangement-arch` (decisions) |
| Independence of multiple voices and avoiding parallels | `mc-counterpoint` |
| Modulation | `mc-modulation` |
| Rhythmic patterns themselves | `mc-rhythm-groove` |
| How syllables are placed on notes, inverted word stress, rhyme | **Lyric writing** |
| How the voice sings (breathiness / dynamics / pitch correction) | `mc-vocal-direction` |
| Which instrument plays the melody | `mc-orchestration` |
| The full catalogue of modes and scales | [reference.md](reference.md) |

> ★ The boundary with lyric writing matters: **this skill decides whether the line sounds good and is singable,
> while lyric writing decides whether the words can be fitted onto it.** Syllable-to-note alignment, excess syllables, and inverted word stress all belong to that side.
> This skill needs only two inferences from it: when lyrics come first, the lyrics for the song are read from `meta.upstream.lyrics`, and each line's syllable count sets the number of notes (in Chinese, one character is one syllable), with one line forming one phrase;
> the tones of Chinese characters limit where a large leap can land (`mc-style-chinese-pop` §3.2). Without lyrics, the melody is responsible only for itself.

---

## 1. Required before starting

| Required | Question to ask |
|---|---|
| **① Core range** | A one-octave span, fixed. **Without this, the melody will scatter** |
| **② Who sings it** | Range and passaggio location. **This determines the key** (§4.2) |
| **③ Where the climax is** | Specify the bar. **The default placement is at roughly the 2/3–3/4 point of the song** |
| **④ Direction of the line** | Overall rising or falling? Why? |

---

## 2. Direction and width: the movement itself is the expression

### 2.1 Direction

| Movement | Expression |
|---|---|
| **Ascending** | Tension, eagerness; **a phrase ending that rises = a question, a throw-out, speaking to the other party** |
| **Descending** | Relaxation, stability; **a phrase ending that falls = an answer, a nod, a sigh, certainty** |
| **Narrow up-and-down wobble** | Hesitation, indecision; neither rising nor falling |

**For a phrase of three or more notes, judge the overall direction by the relative height of the first and last notes.**
If the **local motion arriving at the final note runs against the overall direction**, the sense of overall direction is **weakened**.

★ **The harmonic background can rewrite the meaning of direction**: if a rise lands on a stable note through harmonic function
(such as G7→C landing on the tonic), the "questioning" feeling is replaced by a "resolved" feeling.
**To emphasise a question, remove whatever is blocking it: do not land on a stable note.**

> Body analogy: ascending = standing on tiptoe to look into the distance; descending = bending down to look at something close.

### 2.2 Width

| Width | Expression and limits |
|---|---|
| **Stepwise motion** | Smooth and unobstructed; moving up or down the scale = smooth increase or decrease of tension, very common. Adding a supporting second as an ornament = keeps the contour while adding motion |
| **Semitone** | The narrowest interval, expressing subtlety and delicacy; melodies containing semitones have **a lush quality and depth**. ★ **Overuse (especially chromatic semitone runs with accidentals) → nervousness, sickliness, the grotesque**; must be restrained |
| **Leap** | Dramatic, large emotional swings; **the syllable on the landing note of a leap is emphasised** |
| **Repeated note** | In the low register = calm confiding, restrained narration (or forced suppression); in the high register = sustained tension, incessant calling. ★ When the pitch does not move, listeners' attention shifts to rhythm → pairing it with syncopation and varied note values = **an expression close to speech** |

> **"Using semitones well" is one of the two main sources of melodic feeling** (the other being the density of the pentatonic).

**Width × tempo**: the narrower the interval, the easier it is to sing and the more it adapts to any tempo; the wider it is, the more it needs a slow tempo and preparation.
**A large leap needs sufficient note value at its start or end point (or both)** to be sung naturally.
**Rapid alternation between high and low notes is the most likely to become stiff.**

---

## 3. Leaps: preparation and landing

### 3.1 ★ Three hard limits

1. **A single leap should not exceed a sixth**, but **a pure octave actually sings well and is usable**
2. **Leaps of a fourth or more: at most 2 consecutive in the same direction, and the total span across both ends must not exceed one octave**
   - Compliant: 3+5=7th, 4+4=7th
   - Non-compliant: 5+5=9th, 4+4+4=10th — unnatural and hard to sing
3. **A seventh leap is most often split at a middle note into 3+5 or 4+4** (stepping-stone style, done in two steps)

### 3.2 Upward leaps are easy; downward leaps are hard

(Motion that adds energy is controllable; motion that releases energy is hard to steady.)

**Two remedies for a wide downward leap**:
1. The landing note naturally carries **stress**: anticipate it and **deliberately use it**
2. **Lengthen the starting note sufficiently and diminuendo**, accumulating emotion and tension at the start before leaping

**In narrow leaps, downward is actually easier** (releasing energy): "a short high note leaping downward" placed at the start of a phrase as a phrase-initial accent is a common technique.

### 3.3 Four devices

| Device | Method |
|---|---|
| **Tame (the hold-back)** | Before the leap, place one or several notes **in the opposite direction** (usually stepwise), like the lead-in before a large gesture. Can also be placed midway through the leap |
| **Run-up (josou)** | Before the leap, place one or several stepwise notes **in the same direction**. The run-up note can be within or outside the leap interval |
| **Landing cushion** | **After** reaching the landing point of the leap, follow with one or several stepwise notes **in the same direction**, softening the impact of landing; **especially effective for downward leaps** |
| **Rebound** | After a large leap, stepwise motion **in the opposite direction** = a bounce off the landing. ★ This rebound note can simultaneously serve as the **tame for the next leap**, forming a chain of "leap→bounce (tame)→leap→bounce (tame)→leap" |

### 3.4 Leaps larger than an octave

**Strongly cuts the melody** (it cannot be segmented as a single phrase).
**Use it in reverse**: open the register gap at a segmentation boundary → creates a **pseudo two-part** melody
(a low-register motive and a high-register motive in dialogue).

### 3.5 The value of "unnaturalness" (all must be restrained; overuse makes them fail)

| Technique | Effect |
|---|---|
| Unprepared large leap | **A sudden emotional outburst** (filling in the middle notes would smooth it out, but would destroy the burst of force) |
| After a leap, not resolving in the opposite direction but continuing in the same direction | A special **setsunasa (heart-wrenching ache)** |
| Consecutive leaps with weak internal connection | Weightless lightness, **a lifeless pop quality** |
| Misplaced semitones, scale membership not audible | An artificial feel, a detached irony |
| Augmented intervals | A non-Western flavour |

> **General formula: embed local unnaturalness as a "hook", then finally resolve it in a natural way.**

---

## 4. Range and the human voice

### 4.1 Basic rules of range

- **First set the melody's core range at roughly one octave**; the centre of gravity of each phrase should fall within it,
  otherwise the melody will scatter, and may even sound like several voices mixed together
- The actual range of the whole song should be about **1.5 octaves, at most 2** (this is exactly the usable range of most voices and instruments)
  - Keeping within one octave = a narrow-interval melody, intimate and easy to sing
  - Spanning two octaves = dynamically strong but hard to sing

**The position of a phrase within the range determines its effect**:

| Position | Effect |
|---|---|
| Centre of gravity high | Bright, full of tension; **tension rises sharply on notes that break through the range ceiling**; extremely high = a pained expression |
| Centre of gravity low | Calm and relaxed; **dipping below the floor = heaviness**; extremely low = weakness and sloppiness |

★ **The same motion has different effects in different parts of the range**:
- An ascent in the middle of the range = moderate tension
- An ascent rushing toward the top and breaking through the range = tension is markedly amplified
- An ascent climbing back from low up to the middle = the added tension is offset by the "low register softening", and **can even have a relaxing effect**
- The same ascending phrase ending: in the low register = an easy question; in the high register = an earnest request, even an interrogation

> **Pitch character is relative**: the same middle C is heard as "high" in a low-register melody and as "low" in a high-register melody.

### 4.2 ★ The passaggio determines the key

Male voices sound about an octave lower than female voices, and by convention **male parts are notated one octave higher than they actually sound**.
Pop practice: male singers rarely use the low register and often use the high register; female singers rarely use the extreme high register and often use the low register.

| Register | Character |
|---|---|
| **Chest voice** | The root of realism and intimacy in pop music; pitch movement is expressed most strongly here. Tightness in the high chest range can express **earnestness** (urgency to get a message across) |
| **Mix voice** | Vocal folds partly closed, extending the range upward; bright and open timbre = a positive, outgoing, strong expression. ★ **The same high phrase: sung in chest voice = a tense plea; sung in mix voice = an open gaze into the distance**. The choice of register changes the melody's character |
| **Falsetto** | **Treat it as a different instrument from chest voice**: pure and delicate, suited to refined, gentle expression. Limitations: few overtones → slightly blurred diction; dynamics hard to vary → unsuitable for intimate confiding and large emotional swings |
| **Chest-to-falsetto break** | The **desperate effort** of going past the crack to reach a high note → intense longing, extreme setsunasa |

> ★ **"Does this male singer have a mix voice, and where is his passaggio?" is the major precondition for deciding range and key: confirm it first.**
> For a singer with an awkward passaggio: **design the register phrase by phrase** (this phrase in chest, that one in falsetto or mix), so that no phrase crosses the passaggio.

**Set the basic octave in the middle of the usable extreme range**: this leaves headroom, while keeping the expressive option of deliberately pushing toward the limit.

### 4.3 The singalong effect

Listeners hum along in their heads.

- Once listeners are **drawn into synchronisation** by easy-to-follow repetition, a high note that comes later still sounds "high and tense" to them, even if the singer sings it effortlessly
- **A sudden high note at the opening or at the start of a phrase** gives no time to synchronise → it is externalised and heard as "showing off"

**Be clear while writing**: is this passage meant to be **sung along to**, or **watched and admired**? Then induce it deliberately.

---

## 5. Note values

### 5.1 Usable range

Commonly use **sixteenth notes through whole notes**; tuplets are usually limited to triplets of one or two beats.
**Principle: pop music must keep listeners in sync; the combination of note values must not cause listeners to lose the beat.**

- If the whole piece has a triplet feel, do not write triplets everywhere; **notate it as 6/8, 9/8, or 12/8 instead**
- First examine the character at **BPM ≈ 100**, a moderate tempo where "note value ≈ duration", and only then consider deviations at extreme tempos

### 5.2 Long and short notes

| | Expression |
|---|---|
| **Long notes** | Sustained force = tension; the note can be shaped within (vibrato, crescendo/diminuendo) → **climaxes often place long notes in the high register** (the strongest expression of tension) |
| **Short notes** | Light and agile; sung forcefully = sharp, flung-off. Short notes in the low register are offset by a sense of heaviness |

- Consecutive long notes + little pitch movement = sustained tension; but **dragging on too long becomes slack and boring**. Insert a leap, or weave short notes between the long ones
- **Long notes + large leap** = smooths out large pitch movement while **amplifying the sense of scale**
- **Narrow intervals × short notes = a melody close to speech** (news-reading speed is roughly equal to eighth notes at BPM 120, and does not feel fast)
- Wide-ranging continuous short notes = light, rolling motion; **sustained too long = nervousness, a sense of compulsion**

★ **When mixing long and short notes: long notes are the main voice (centre of gravity and natural stress); short notes are subordinate, regardless of metric position.**
A common cycle: short notes **approach** a high long note → tension → a low short note **releases** → approach again…
Extreme compression = a leaping feel of alternating long and short notes (common in 6/8 and 12/8). Effective, but **highly prone to predictability**.

---

## 6. Closure (cadence)

### 6.1 Note-value treatment

Lengthening the closing note = motion stops. There are two possible follow-ups: add a short note to **release** the tension, or use a rest to **shed** it.

★ **Note values alone cannot close a cadence**: if harmony and mode (scale degrees) do not close at the same time,
the sense of ending is half-finished. **Use this in reverse**: let the chorus settle while keeping the whole song unresolved, leaving the sense that "the story is not yet finished".

### 6.2 Major closure (end of a section / end of the song)

| Technique | Effect |
|---|---|
| Ritardando + diminuendo | Releases energy. **"Notated ritardando" = write each note before the close progressively longer, or insert a bar of 2/4** |
| Lengthen the note before the close (building tension), then land on a **short** note | Tension is held to the last moment, then released instantly |
| **The melody omits the closing note and hands it to the accompaniment** | Like a dreamy afterglow where the breath has been cut off |
| Neither slowing nor lengthening, close on a short accented note | **A decisive, strong sense of will** (can be reinforced with one more accented short note) |

### 6.3 Rests are part of the melody

Rests play two roles that have been covered thoroughly elsewhere; this section simply places them: for segmentation signals, see the first of the six causes in §7.2 (long note values and rests are the clearest); for the release of tension at the end of a phrase, see the note-value treatment in §6.1 Major closure (a rest can replace a short note in completing the release).

---

## 7. Motive → phrase → section

### 7.1 Terminology hierarchy

```
Partial motive (cannot stand alone, but has recognisable features) ≈ word       labelled a1, a2; variants add '
  → Motive: the smallest melodic unit that can stand alone, at least 1 bar       labelled a, b
     (any shorter and its metric position cannot be judged independently)
     ★ On repetition, it usually inherits the rhythmic contour and repeats with variation
  → Sub-period: usually 2 motives                                                 labelled A1, A2
     → Period: most often 8 bars, 4 bars also common                              labelled A, B
        (other bar counts are mostly additions or subtractions from 8 or 4)
        A whole unified in its emotional character
```

★ **Different motives can share part of a motive** (e.g. a'' = a1' + b2). **This is an important means of achieving structural unity.**

> **The same material takes its character from context**: the same motive, placed after a static phrase, becomes a minor climax;
> placed after a soaring phrase, it becomes a soothing answer.

### 7.2 Six causes of segmentation (ranked by clarity)

1. **Long note values and rests** (clearest)
2. **Leaps** (interrupt pitch continuity)
3. **Repetition of a motion pattern** (each repeating unit forms its own segment)
4. **Clear closure**
5. **Clear beginning** (recognised retrospectively: only when the start of the next phrase is recognised does the previous segment confirm that it has ended)
6. **Repetition / contrast** (likewise recognised retrospectively)

**Segmentation in groups of 2, 4, and 8 bars is easiest to grasp**; odd-bar groupings (3+3+2, etc.) are hard to perceive.

| | Effect |
|---|---|
| **Strong segmentation** (tonic + strong beat + tonic chord + long note/rest) | A sense of restarting: suited to opening a new section, reinforcing repetition/contrast. **But it cuts the song in two, so use sparingly except at the end of a section** |
| **Weak segmentation** | Smooth and continuous, mood sustained; may blur structure or create a sense of stagnation |

### 7.3 Call and response: the most basic engine

Present two passages; **the latter is heard as a reaction to the former** (it need not be a literal question and answer).

- Call and response with similar phrases = echo type; with contrasting phrases = continuation type; **the "answer" can even come first** (establish the form first, then ask the question)
- **Paired call and response is the most stable but also the most predictable**; **chain-like extension ("string of beads") develops richly but risks dispersal**
- Call and response runs **in parallel across several levels** of motives and phrases (one motive responds both to the immediately preceding motive and to the entire preceding phrase)

### 7.4 Where the climax falls

**Default placement: the 2/3–3/4 point of the song.**

A climax section has three recognisable signals: higher register, longer note values, and stronger dynamics, with the instrumentation also tending to broaden (Wen Hailiang p0149).
There are two routes into the climax, **presented side by side**:
**Gradual build**: the melody uses continuous ascent, combined with contrasts of rhythmic density, changes in harmonic language, and shifts in timbre or tonality; drums add embellishments at the seam between the statement and the climax, consolidating the drive (Wen Hailiang p0149).
**Stillness to create motion**: the statement section is brought fully to rest, and the climax enters with no transition, driving forward through the contrast itself. The cost is that it needs a sufficiently clean pause point; if handled badly, it sounds abrupt (Wen Hailiang p0151).

The climax point and the climax section also end differently: once the climax point has been pushed through, the rhythm often suddenly slows and widens, giving a complete closure; the climax section must continue on from its high emotion and should not rush to end (Wen Hailiang p0149).

Remedy for a strong start with a weak finish: check the position of the climax and how the song ends, **revise how the motive or phrase ends**, and strengthen the climax in the second half of the chorus.
If the climax has been repeated several times and still feels unfinished, you can attach a continuing supplementary passage before a volume fade-out. This is more complete than cutting off abruptly (Wen Hailiang p0152).

---

### 7.5 Index for musical-idea development: how a motive grows into a section and a section into a song

How a motive grows into a section and a section into a song belongs to **`mc-development`** (L1). It owns `material` and `form[].development`; the ten techniques, the boundary between development and mere accumulation, and where pop songs land are all covered there. This skill covers only how the motive and phrase themselves are written.

## 8. ★ Anti-cliché (yotei chowa: predictability)

> **Yotei chowa = the listener can read the next step, and everything unfolds as expected. This is the problem melody writing most needs to guard against.**

### 8.1 High-risk pattern checklist

- The same phrase **repeated unchanged 3 or more times**
- A motive **shifting in parallel along the chord progression** (by the third chord the listener has already worked out the whole song)
- Formulaic harmonic rhythm: one chord per bar, dominant chord at the end of an 8-bar unit
- The second verse **copies** the A−A' opening of the first verse (the listener immediately predicts that B−C must follow)
- A long-short-long-short leaping rhythm **running through the whole song**
- Textbook leading-tone→tonic and iv→iii resolutions **played straight**

### 8.2 Six countermeasures

1. **The third repetition must change**; in the second verse, **drop the repeated opening** (A-A'-B-C → A-B-C)
2. **Use expectation to turn the tables**: first induce the listener's prediction, then **sharply betray** it at the very point predicted, using surprise to shape the climax
3. **Stretch the melodic line**: a long arc not chopped up by motives (use anticipation notes to bind the rhythmic figure together, sink deep → rebound upward to become the climax → a strong semitone appoggiatura as a second centre of gravity → close calmly).
   ★ **A long line = a sense of direction + a relay of varied motion devices**, not merely the absence of breaks (that only drags)
4. **Keep material to a minimum**: every new phrase should make clear how it differs from what came before and what it continues (partial contrast + partial repetition). **The fewer the materials, the more easily a song is understood and the more moving it can be**
5. **Break ready-made resolutions with suspensions, appoggiaturas, and anticipation notes**
6. Between "mediocrity" (copying stock devices, comforting but worthless) and "incomprehensibility" (straying so far from shared form that it becomes a wall),
   **support originality with strong internal logic within the work**

### 8.3 Distortion + answer

**Smoothness throughout = boredom**; a **misshapen** (ibitsu, distorted) point is needed to stir things up.
★ **But a distortion must be answered** (a moving resolution after a string of unstable notes; a leap that defies the accent = endorsement of strong feeling).
Otherwise it is simply a flaw.

> Once early cleverness has convinced listeners that the song is worth hearing, even a plain line that follows
> will be waited through patiently, with the listener expecting that a good answer is coming.

---

## 9. Diagnostic table

| Symptom | What to check → what to prescribe |
|---|---|
| **Flat and boring** | All stepwise / chord tones / on the beat? → Add non-chord tones (appoggiaturas / suspensions), syncopation, leaps with preparation; check whether pentatonic density and semitone usage are unchanging |
| **Every step is predictable** | Same phrase unchanged 2+ times? Motive shifting in parallel with the chords? → Vary on the 3rd repetition, omit repetitions, or induce expectation and turn the tables for the climax |
| **Loose, won't hold together** | Too much material, continuous brand-new motives? → Share partial motives, keep repeated elements in new phrases; narrow the range to 1 octave; segment in 2/4/8 bars |
| **Strong start, weak finish** | Position of climax and ending? → Place the climax at 2/3–3/4; change the **ending method** of the motive/phrase; strengthen the second half of the chorus |
| **Hard to sing** | Leap over a sixth? Same-direction leaps more than 2 or total span over an octave? Neither end of a large leap given note value? Crossing the passaggio? Augmented second? → Split sevenths into 3+5 / 4+4, add tame / run-up / landing cushion, assign registers phrase by phrase |
| **Buried by the accompaniment** | Opening and bass both landing on strong beats? Melody tracing the rhythmic pattern? Stuck to the beat throughout? → Offset the start points, give way on off-beats or answer them, leave gaps |
| **Like an instruction manual / school song** | Functional progressions like leading-tone→tonic too blunt? → Break them with suspensions/appoggiaturas, mix in pentatonic, avoid the strongest cadence at phrase ends (tonic + I + strong beat) |
| **Pentatonic melody lacks character** | Only circling between easy neighbouring tones? → Use turn figures, offset the pentatonic tonic from the key tonic, insert large leaps / arpeggios to dilute, add ornamental semitones |
| **Ending doesn't feel final** | Note value has stopped but mode/harmony has not? → Landing on tonic + I + leading tone approach = the strongest closure; for an afterglow, do the reverse |
| **Whole song monotonous** | Every section starts on the tonic chord? Interludes all the same length? → Start one section from a reversed cycle, omit phrases in the second half, repeat the chorus with a key change in the final section |

---

## 10. Mapping to ARR-SPEC fields

| Field | Section of this skill |
|---|---|
| `form[].melody_register` | §4.1 (**there must be contrast between sections**) |
| `hooks.vocal_hook` | §7.1 Motives + §8 |
| `vocal.register_arc` | §4.2 (consistent with the passaggio) |
| `meta.key` | ★ §4.2 — **the key is determined by the singer's passaggio, not by choosing a key first and then finding a singer** |

---

## 11. Must-pass checks after writing

- [ ] Core range **within one octave**; the whole song does not exceed 1.5–2 octaves
- [ ] No single leap larger than a sixth (octaves excepted)
- [ ] Consecutive same-direction leaps **no more than 2**, with total span **no more than one octave**
- [ ] Every large leap has at least one of: **tame / run-up / landing cushion / rebound**
- [ ] The singer's **passaggio** has been confirmed, and no phrase crosses it
- [ ] Climax at **2/3–3/4**, with a stated reason why it is the climax
- [ ] **No phrase repeated unchanged 3 times**; the second verse drops the repeated opening
- [ ] Motives **share partial motives**, rather than a pile of entirely new material
- [ ] There is one **distortion**, and it **is answered**
- [ ] At closure, **note value, harmony, and mode all arrive together** (for an afterglow, do the reverse)

---

## Appendix: Sources

- **Takayama Hiroshi, *Melody Writing for Popular Music Composition*, expanded edition** (Japanese original: ポピュラー音楽作曲のための旋律法 増補版) — the backbone of §2–§9.
  **Parts of the book not covered by this skill**:
  matching words to music → a matter for lyric writing, not in this package; form and whole-song assembly → `mc-form`;
  catalogue of modes and scales → [reference.md](reference.md).
- **Jimmy Kachulis, *The Songwriter's Workshop: Melody*** —
  the four types of motive (parallel / similar / oblique / contrasting) and modal melody (major blues, mixolydian, dorian, pentatonic)
  are summarised in [reference.md](reference.md).
- **Schoenberg, *Fundamentals of Musical Composition*** —
  another account of phrase construction and motive development, kept **alongside** the Japanese approach above; differences are noted in the reference.
- **Richardson modes** — the modal catalogue.
- **Wen Hailiang, *Arranging*** (Popular Music Academy textbook series) — §7.4 the techniques for driving to the climax and handling the ending.
- **Huang Huwei, *Modulation Methods*; Li Chongguang, *General Textbook of Basic Music Theory*** — the criteria for non-chord tones and stable scale degrees in pentatonic closure, reference.md §3.5.
