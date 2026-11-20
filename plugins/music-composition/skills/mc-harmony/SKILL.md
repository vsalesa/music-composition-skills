---
name: mc-harmony
description: Functional and colour harmony - choosing chords for a melody and then upgrading them without over-cooking. The three functions and three cadence types, the measure-by-measure harmonization procedure, substitution rules, seventh chords, and the colour techniques (slash chords, secondary dominants, two-fives, tritone substitution, subdominant minor, modal flavours, sus4, tensions, cliche lines, passing diminished, pedal point, blue notes) organised as a nine-step reharmonization checklist with an explicit stop rule. Use when harmonizing a melody, when a progression is bland or too busy, when a section needs a specific colour (wistful, jazzy, driving, chromatic bass), or when filling the harmony fields of an ARR-SPEC. Keywords: harmony, chords, harmonization, cadences, reharmonization, secondary dominants, two-fives, substitution, tensions.
---

# Harmony: Function and Colour

**This skill has two halves. Know which half you are in when you use it:**

| Half | What it does | Section |
|---|---|---|
| **Function** | Gives a melody chords that make sense | §2–§5 |
| **Colour** | Makes the sensible chords sound good | §6–§7 |

★ **The order cannot be reversed.** Build the functional skeleton first, then add colour.
Starting from colour leads to "every chord is very sophisticated, but you can't tell what the progression is doing."

## Which sections to read for each task

| Symptom or task | Read |
|---|---|
| Have a melody and need chords | §2 → §3 → §4, the bar-by-bar procedure |
| Harmony is flat | §7 nine-step upgrade table |
| Harmony is too busy or too fragmented | ★ The stop rule in §7 |
| Want a specific colour | §6 symptom-to-technique quick reference |
| One chord stays too long without change | §6 cliché line / sus4 / pedal |
| Bass wants to move by semitones | §6 slash chords / tritone substitution (ura-wakon) / passing diminished |
| How to harmonise a minor key | §5 |
| Look up an existing progression | `mc-progressions` |

## Boundaries: what this skill does not cover

| Not covered here | Where it lives |
|---|---|
| The library of existing chord progressions (120 entries) | `mc-progressions` |
| Key changes | `mc-modulation` (§6 of this skill gives only the **harmonic lead-in to a modulation**) |
| How the melody itself is written | `mc-melody` |
| How voices become independent, parallel fifths and octaves | `mc-counterpoint` |
| Which instruments play the chords, and voicings | `mc-orchestration` |
| The **groove** implications of harmonic rhythm (how many chords per bar) | `mc-rhythm-groove`, section "harmonic change rate is also groove" |
| Harmonic vocabulary specific to a style | `mc-style-*` (L3) |
| Full catalogue of scales, chords and tensions | [reference.md](reference.md) |

---

## 1. Required before starting

| Required | Question to ask |
|---|---|
| **① Key** | Major or minor, and which key. **All scale-degree notation is based on it** |
| **② Harmonic rhythm** | How many chords per bar? ★ One chord per bar throughout is the most typical formula |
| **③ What colour this section needs** | Answer with the words of §6, not "make it sound nicer" |
| **④ Where it must be most stable and where most unstable** | Decides where the cadences go |

---

## 2. The three functions

| Function | Character | Members |
|---|---|---|
| **T (Tonic)** | Stable | **I, VIm** (VIm is the "stand-in" for I) |
| **S (Subdominant)** | Slightly unstable, leans toward D | **IIm, IV** |
| **D (Dominant)** | Unstable, wants to return to T | **V, VIIm(♭5)** (V is overwhelmingly common) |

**D's instability must "resolve" to T. This psychological need is the source of the forward drive in music.**

★ **IIIm is excluded from this table.** It is a chameleon: it can act as either T or D. See §6.

---

## 3. The three cadence types

| # | Type | Feel | Example |
|---|---|---|---|
| 1 | **T → D → T** | Like "stand up, bow, sit down": simple and forceful | C→G→C (I→V→I), Am→G→C (VIm→V→I) |
| 2 | **T → S → D → T** | Tension climbs step by step, then resolves to T in one move: **the most satisfying** | C→F→G→C, Am→Dm→G→C |
| 3 | **T → S → T** | Returns to T without passing through D. S→T is usually IV→I, the **Amen cadence (plagal cadence)** | C→F→C |

**Same-function chaining**: chords of the same function can be strung together.
Example: C→Am→F→Dm→G→C (I→VIm→IV→IIm→V→I).
I and VIm form a T; IV and IIm form an S; the whole still runs T→S→D→T.

### 3.1 ★ Cadences and emotion: the one source here that addresses lyrics (Kachulis)

The three harmony sources in this library say nothing about what the lyrics mean. This layer comes from Kachulis, *The Songwriter's Workshop: Harmony* (p0163–0174):

| Cadence | Emotion |
|---|---|
| Perfect cadence V → I | Firm |
| Half cadence (stopping on V) | Uncertain, creates tension |
| **Deceptive cadence** | An ambiguous surprise, and its three landing points differ: **V → VImin, sorrow; V → IV, surprise; V → VI (major triad), bright, cheerful surprise** (p0169) |
| Plagal cadence IV → I | Religious feeling, spirituality |
| Mixed cadence (major borrowing from minor: ♭VI – ♭VII – I) | Mixed joy and sorrow; especially effective in rock and blues |

Perfect cadences look different in each mode (p0163–0165): major V–I; minor ♭VII–Imin or V–Imin; blues V7–IV7–I7; mixolydian ♭VII–I. ★ **Dorian has no perfect cadence.**

### 3.2 Home and away: three shapes of section (p0176–0193)

| Section | Shape |
|---|---|
| Verse plus chorus | **home – away – home** |
| Verse | **home – away**, stopping on V to push into the chorus |
| Bridge | **away – away**, starting on a non-I chord and ending on V; the greatest tension |

Two ways to build a chorus: use a single cadence repeatedly, or place cadences only on the hook phrase. ★ **Avoid the tonic chord before the hook phrase appears** (p0182–0187).
Joining sections: a verse ending on V followed by a chorus starting on I is a perfect-cadence join. A chorus starting on VImin is a deceptive-cadence join, which gives a sense of surprise (p0191–0193).

★ **Four harmonic tests for section contrast** (p0195): each section starts on a different chord; each section has at least one new chord; **only the chorus has a perfect cadence**; each section has a different phrase length. Check the two sections against all four. Two sections that fail all four will sound like the same section.

### 3.3 Chord colour changes meaning: embellishing words and phrases (Kachulis p0149–0160)

The same word on the same note, set to different chords, changes its meaning: **major triads feel hopeful, power chords feel forceful and confident, minor triads feel sad and introspective, seventh chords feel melancholy and sensual** (p0149–0150). The library previously had no line connecting "chord" to "lyric meaning."

**Procedure for embellishing a phrase** (p0152–0160): find two or three important notes in the phrase. **Build a multi-column table of candidate chords, one column for each bar**, then try combinations. Placing two chords in one bar creates a little drive (p0118).
A companion grouping by function (p0082): IIm–IIIm–IV–V, IV–V, IIm–V, and VIm–V. This group is a "leaning toward V" progression, used specifically to build tension that leads into the chorus.

---

## 4. The bar-by-bar harmonization procedure

1. **Confirm the base**: write out the I, IIm, IV, V and VIm of this key and their functions, then the three cadence types.
2. **List candidates bar by bar**: take the melody notes of this bar and find the **diatonic chords whose constituent notes include them**.
   - A melody note exactly matches a chord member → direct candidate (for example, A·F·C → F)
   - Several chords contain it → parallel candidates (for example, B♭·D → B♭ or Gm, both S)
3. **Decide with the cadence**: if the first three bars already form T→S→D, the fourth bar should return to T. Choose a T-function candidate.
4. **Ending rule**: it is best for the whole piece to land on the most stable **I**.
5. **T is both the end and the start**: in a functional chain such as T S D T S T D T, **one T is often shared by the cadences on either side of it.**

### 4.1 A worked example (F major, 3/4, 8 bars)

Candidate table: F (I, T), Gm (IIm, S), B♭ (IV, S), C (V, D), Dm (VIm, T)

| Bar | Melody notes | Candidates | Ruling |
|---|---|---|---|
| 1 | A·F·C | F (constituent notes match exactly) | F (T) |
| 2 | B♭·D | B♭ or Gm (both S) | Either works |
| 3 | E·G·C | C | C (D) |
| 4 | A | F or Dm (both T) | Bars 1–3 already form T→S→D, so return to T here |
| 5–8 | Same method | B♭ → F → C → F | S→T→D→T, landing on I |

**Result**: F → B♭ (or Gm) → C → F (or Dm), or B♭ → F → C → F

> **Rule of thumb: fitting the cadence framework first is the shortcut to progress.**
>
> ★ **Failure condition**: real songs break theory all the time. Insisting that cadence rules must hold absolutely itself produces unnatural progressions. **Stay flexible, and expect exceptions.**

### 4.2 Two beginner substitution rules, and their limits

**Swapping IIm and IV (within the S function group)**: this is the safest of the rules. Ren Damin's *Pop and Jazz Harmony* places ii, IV and vi in one subdominant function group, and says the most common case is mutual substitution of chords within the subdominant function group (p0134). I–IV–V7–I can become I–ii7–V7–I or I–vi–V7–I, and both give smoother stepwise voice leading (p0135). In jazz the rule goes further: once IV is replaced by ii7, ii7 is in practice more common than the original IV (p0280).

**Using IIIm in place of I: the two frameworks judge it differently, so do not mix them**

- On the "chameleon" route (see §2 and §6), IIIm standing in for I is darker than VIm, and is more easily heard as a transition toward D.
- In Ren Damin's classical and jazz functional scheme, iii belongs to the **dominant** function group, alongside V and vii°7 (p0134). He states that the resolving force of iii toward I is weaker than that of V, and does not recommend iii standing in for I at a cadence (p0135). In major keys, his more standard substitute for I is VIm, because most of I's chord tones are contained in the VI chord. But this holds only in major, and after the substitution the V that follows I usually also needs rewriting as ii–V (p0279).
- Using substitute chords has a cost. In a melody where most tonic chords are replaced by substitutes such as iii, vi and ii, and which lands on VIm, the sound slides toward the relative minor and no longer feels like the original major key (p0118; p0120, examples 1–20).

---

## 5. Minor keys (based on harmonic minor)

The minor function table and the three cadence types have the same structure as in major. But **V must use a major triad or dominant seventh** (from the raised seventh degree of harmonic minor). Otherwise the resolving force of D→T disappears. The detailed comparison of natural, harmonic and melodic minor is in [reference.md](reference.md).

---

## 6. Colour techniques: symptom-to-technique quick reference

| Want | First-choice technique |
|---|---|
| **More drive, more vivid** | Secondary dominants, two-fives |
| **More jazzy, more fashionable** | Tensions, chained two-fives, slash chords |
| **Setsunasa (wistfulness), a touch of shadow** | **Subdominant minor (S.M)**, IIIm7 |
| **A chromatically descending bass line** | Slash chords, tritone substitution (ura-wakon), passing diminished, cliché line |
| **One chord sits too long; want internal motion** | **Cliché line**, sus4, pedal |
| **Avoid the plain dominant seventh cliché** | Dominant minor, tritone substitution, unresolved V7sus4 |
| **Melancholy, cool, improvisational feel** | Blues and blue notes |
| **Whole section needs a change of mood** | Modulation lead-in (→ `mc-modulation`) |
| **Whole section needs reharmonising** | §7 nine-step table |

### 6.1 Each technique in one sentence

| Technique | What it does |
|---|---|
| **Slash chord** | Specifies the bass note, creating a smooth or chromatic bass line |
| **IIIm7** | ★ **Chameleon**: it can act as T (a stand-in for I) or as D (a stand-in for V). Which role depends on context |
| **Secondary dominant (Sec.D)** | Places its V7 in front of any chord that is temporarily acting as T |
| **Two-five (ii–V)** | Splits a dominant chord into IIm7→V7, doubling the drive |
| **Tritone substitution (ura-wakon)** | V7 → ♭II7. The bass moves by semitone and the flavour is sharper. Add ♭5 when it doesn't fit |
| **Subdominant minor (S.M)** | IV→IVm(6), or substitute ♭VI△7 / ♭VII7. **The main source of wistfulness** |
| **Modal flavour (Dorian IV / dominant minor)** | Borrows modal colour to avoid the blunt directness of functional harmony |
| **sus4** | Delays resolution. **An unresolved V7sus4** can avoid the dominant-seventh cliché altogether |
| **Tensions (9/11/13)** | Add colour without changing the function |
| **Cliché line (chromatic line)** | The chord stays put while an inner voice moves by semitone. The cure for "a chord sitting too long" |
| **Passing diminished chord** | Fills a whole-step gap |
| **Pedal** | The bass stays put while chords change above it |
| **Blues / blue notes** | Rubbing ♭3, ♭5 and ♭7 against the harmony |

(The full usage of each technique, the usable tension table and the forbidden combinations are in [reference.md](reference.md).)

---

## 7. ★ Nine-step reharmonization table

**Given a plain progression, try these in order. The ear is the final judge at every step.**

| # | What to do |
|---|---|
| 1 | **Upgrade to seventh chords** (triad → seventh chord). **Do not add them everywhere**; check the overall balance |
| 2 | **Substitute**: I ⇄ IIIm7/VIm7, IV ⇄ IIm7, V7 ⇄ VIIm7(♭5)/IIIm7 |
| 3 | **Insert secondary dominants**: in front of every chord that is temporarily acting as T, try placing its V7 |
| 4 | **Turn dominant chords into two-fives**: check whether each dominant seventh can be split into IIm7→V7 |
| 5 | **Tritone-substitute the dominants**: when you want a semitone bass or a sharper flavour, V7 → ♭II7 |
| 6 | **Borrow the subdominant minor**: IV→IVm(6), or ♭VI△7 / ♭VII7, for wistfulness |
| 7 | **Insert a dim7 in a whole-step gap**, **use slash chords for a smooth bass**, **use sus4 for delayed resolution** |
| 8 | **Scatter tensions**: add 9/11/13 using the table in the reference |
| 9 | ★ **Finally ask yourself: have I overdone it?** |

### 7.1 ★ Step 9 is the most important step in this table

> **"Never chop chords too finely."**
> Plain rock and pop especially must guard against wordiness. **The simplest option is just as often the best one.**

**Self-check action**: play the upgraded version and the original alternately.
**If you cannot say what the upgraded version does better, go back.**
Harmonic complexity is not a score. It is a **means**.

### 7.2 Step-by-step upgrade demo

The same skeleton, `C → Am → Dm → G` (I → VIm → IIm → V, a cyclic progression):

| Stage | Progression | Steps used |
|---|---|---|
| Original | `C → Am → Dm → G` | Diatonic triads |
| Seventh-chord upgrade | `C△7 → Am7 → Dm7 → G7` | 1 |
| Insert secondary dominants | `C E7 Am C7 F D7 G` (I III7 VIm I7 IV II7 V) | 3 |
| Two-five-ise | `C → Bm7(♭5) → E7 → Am → Em7(♭5) → A7 → Dm7 → G7` | 4 |
| Tritone substitution + tensions | `Em7 → E♭7 → Dm7 → D♭7 → C△7(9)` (chromatically descending bass to close) | 5 + 8 |
| Add wistfulness | `C → Am → Fm6 → G7sus4 → G7` | 6 + 7 |

> ★ Note that these six lines are **not "the further down, the better."** They are six different things.
> Which line you choose is decided by required item ③ in §1, not by "how sophisticated it sounds."

---

## 8. Three common skeletons (full table in `mc-progressions`)

| Name | Progression | Function |
|---|---|---|
| **Cyclic progression** | I → VIm → IIm → V | T→T→S→D. **Can repeat indefinitely**; the skeleton of skeletons |
| **Reverse cycle** | IIm → V → I → VIm | S→D→T→T. A cyclic progression that starts from the S section; used even more than the cycle in major keys |
| **Canon progression** | I → V → VIm → IIIm → IV → I → IIm → V | ★ Its appeal is that the constituent notes of the chords trace a stepwise-descending melodic line, which turns upward at the last chord. The effect is "a ray of hope suddenly appears" |

**The most common development of the reverse cycle**: repeat it, with the second pass landing on I. Or, when repeating, replace the final VIm with the **VI major triad**:
`Dm→G→Em→Am / Dm→G→C→A`

---

## 9. Correspondence with ARR-SPEC fields

| Field | Section of this skill |
|---|---|
| `form[].harmony` (scale degrees) | §2–§5 |
| `form[].harmony_letters` (chord letters) | **The same progression written in both notations. A hard convention of this library** |
| lint #9 (at least one section has a non-diatonic chord or a modulation marker) | §6, §7 |

★ **Dual notation is a hard convention.** Scale degrees are for thinking and transposing; letters are for handover and for compiling into prompts. **Writing only one of them counts as unfilled.**

---

## 10. Must pass after writing

- [ ] **Functional skeleton first, colour second**, not the reverse
- [ ] For each section, you can state its **functional chain** (T S D T…)
- [ ] The whole piece lands on **I**. (To leave it hanging, do so deliberately and state the reason.)
- [ ] **Harmonic rhythm is not one chord per bar throughout**
- [ ] At least one section has a **non-diatonic chord** (lint #9)
- [ ] After running the nine-step table, you **asked "have I overdone it?"** and can say what the upgrade improved
- [ ] Scale degrees **and** letters are both written
- [ ] Colour techniques were chosen according to the need in §1 ④, not according to "how sophisticated it sounds"

---

## Appendix: Sources

- **Japanese: *Learn Chord Selection from the Basics* (Shohō kara migi ni tsukeru! Kōdo no erabikata manyuaru) and *Writing Music the Way You Want* (Motto! Omoi-dōri ni sakkyoku ga dekiru hon)**. These are the main body of §2–§8. Choosing chords and beautifying chords are placed in one skill because they are two stages of the same process; splitting them into two skills would leave the agent stuck halfway.
- **Sposobin, *Textbook of Harmony***: the strict version of classical functional harmony, kept alongside the Japanese system. Sposobin's criteria judge whether voice leading is correct; the Japanese criteria judge whether it sounds good. The two do not conflict, but their criteria differ. A comparison table is in the reference.
- **Ren Damin, *Pop and Jazz Harmony*** and **Levine, *The Jazz Theory Book***: fuller versions of tensions and substitutions.
- **Kachulis, *The Songwriter's Workshop: Harmony***
- The 120 ready-made progressions are in `mc-progressions`.
