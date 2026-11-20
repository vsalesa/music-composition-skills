---
name: mc-style-jazz
description: Jazz as a style layer - what is specific to jazz and what is merely general music theory wearing a jazz hat. Chord-scale theory and the avoid-note idea, melodic minor harmony and the interchangeability that makes altered dominants work, the diminished and whole-tone resources, comping and voicing conventions, the head-solos-head form, bebop phrasing and accent placement, what a jazz arrangement measurably does differently (smallest roster, fewest entry events in the corpus), and an explicit transfer table saying which of these survive outside jazz. Use when writing or arranging in a jazz idiom, when a progression needs jazz reharmonization, when comping, when adding a solo section, or when deciding whether a jazz device belongs in a pop track. Keywords: jazz, bebop, chord-scale, altered dominant, ii-V-I, swing, solo, comping.
---

# Jazz Style Layer

**Every skill in the L3 style layer must first answer one question:**

> **Within this style, which elements are specific to it, and which are just general music theory wearing this style's coat?**

For jazz this question is especially sharp, because **jazz theory is widely taught as "advanced theory"**,
and many of its elements actually belong to `mc-harmony`, not to this skill.

## Which sections to read for each task

| Task | Read |
|---|---|
| **Deciding whether a technique should be carried into another style** | ★ §2 transfer table (**read this first**) |
| Writing jazz harmony | §3 Chords and scales |
| Needing altered dominants or an "outside" sound | §3.3 Melodic minor |
| Writing accompaniment (comping) | §4 |
| Laying out the structure of a jazz tune | §5 |
| Writing a solo / improvised section | §6 |
| Where jazz arrangements measurably differ from pop arrangements | ★ §7 |

## Boundaries

| Not covered here | Where it lives |
|---|---|
| General usage of ii-V-I, secondary dominants, backdoor chords, and tension notes (★ **these are not specific to jazz**) | `mc-harmony` §6, §7 |
| Definition of church modes | `mc-melody` [reference.md](../mc-melody/reference.md) §2 |
| How to set the quantisation ratio for swing | `mc-rhythm-section` §2 (percentage quantisation); this library does not give millisecond values, and swing is written as a ratio in `groove.quantize_policy` |
| General principles of form | `mc-form` |
| Instrumentation technique | `mc-orchestration` |
| Complete catalogue of scales, chords, and voicings | [reference.md](reference.md) |

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① Which jazz style** | swing / bebop / modal / bossa / fusion / pop with a jazz flavour. **"Jazz" is not a single style**. Bossa grooves, instrumentation, and chord-change timing are covered in `mc-style-latin`; this skill covers only the harmony it borrows |
| **② Is this jazz or "jazz-flavoured"** | ★ Determines how the §2 transfer table is used |
| **③ Is there an improvised section** | If so, the form is completely different (§5) |
| **④ Arrangement size** | ★ Measured: the median roster in the jazz corpus is **22 tracks**, against 36 for pop. **Jazz is achieved by subtraction** |

---

## 2. ★ Transfer table: what can and cannot be carried over

**Every L3 style skill carries this table, because it is the key to preventing style contamination.**

| Technique | Transferable? | Notes |
|---|---|---|
| **ii-V-I, secondary dominants, backdoor chords** | ✅ **Fully transferable** | They already live in `mc-harmony`. Used heavily in J-POP and city pop |
| **Tension notes (9/11/13)** | ✅ Transferable | Same as above. But **reduce the density**; in pop, full tension stacks become muddy |
| **Chord-scale thinking** | ⚠️ **Partly transferable** | Transferable as a **basis for choosing notes**; not transferable as an **improvisational framework** (pop songs have no improvised sections) |
| **The four usable chords of the melodic minor** | ⚠️ Partly transferable | Used singly (e.g. Lydian Dominant as colour) they transfer; **used in a series they immediately sound like jazz** |
| **Altered dominants** | ❌ **Largely not transferable** | As soon as they enter pop, they sound "jazzy", not "sophisticated" |
| **Diminished-scale licks** | ❌ Not transferable | Strong markers of jazz vocabulary |
| **Jazz use of sus chords** | ⚠️ Partly transferable | ★ **Slash-chord dominant substitutes such as F/G are the mainstay in city pop** (→ `mc-progressions` reference §3) |
| **Comping rhythm** | ❌ Not transferable | It assumes an improviser who needs room |
| **Head–Solos–Head form** | ❌ Not transferable | Pop songs do not have this structure |
| **Swing feel** | ⚠️ Partly transferable | Shuffle is common in blues-rock and R&B, but **the swing ratio differs** |
| **Small ensembles, lots of space** | ✅ **Transferable, and should be transferred** | See §7 |

★ **One test**:
> **Whether something can be carried over depends on whether it assumes "a person is improvising right now".**
> If it assumes this (comping rhythm, solo structure, the handling of outer-sounding notes), it cannot be carried over;
> if it does not (harmonic resources, the philosophy of ensemble size), it can.

---

## 3. Chords and scales

### 3.1 Core idea

**Each chord corresponds to one (or several) scales, and the scale determines the usable notes.**
This is the biggest difference in thinking between jazz theory and classical functional harmony:
**classical theory asks "where does this note resolve to?", while jazz asks "which notes are usable over this chord?"**

| Mode | Chord |
|---|---|
| Ionian | △7 |
| **Dorian** | m7 |
| **Mixolydian** | Dominant 7 |
| Aeolian | m7 (natural-minor colour) |
| **Locrian** | **m7(♭5)** (half-diminished) |
| **Lydian** | △7(♯11) |
| Phrygian | Sus♭9 |

### 3.2 Avoid notes

**Not "cannot be used", but "should not be stopped on".**
The most typical case: in a major-key ii-V-I, **the 4th degree over I△7** (which clashes a semitone with the major third).

★ **This is exactly where Lydian is useful**: raising the 4 to ♯4 makes the **avoid note disappear**,
which is why **△7(♯11) sounds more "open" than △7**. The same applies to ♯11 on a dominant 7.

> Levine devotes a whole chapter to "**rethinking dissonance**": the history of jazz is the ongoing absorption of notes that were once "not allowed".

### 3.3 ★ Melodic minor harmony: the core of jazz

**The melodic minor scale has seven modes, four of which give jazz its signature chords:**

| Mode | Chord | Use |
|---|---|---|
| Degree 1 | **Minor-major 7 (mMaj7)** | The jazz version of the minor tonic chord |
| Degree 2 | **Sus♭9** | |
| Degree 3 | **Lydian Augmented** | |
| Degree 4 | **Lydian Dominant** (dominant 7♯11) | ★ The most common, and also **the easiest to carry into pop** |
| Degree 6 | **Half-diminished (m7♭5)** | The ii in a minor ii-V |
| **Degree 7** | ★ **Altered dominant** | **The core of the jazz sound** |

★★ **Interchangeability**:
**The chords generated by the same melodic minor scale can substitute for one another.**
This is tonal thinking: you are not thinking of individual chords, but of **"which melodic minor we are currently on"**.

> **This is the biggest dividing line between jazz and pop harmony.**
> Pop harmony is a **sequence of chords**; jazz harmony is a **sequence of scale regions**, with chords as slices through them.

### 3.4 Other resources

| Resource | Use |
|---|---|
| **Diminished scale** | Over dim7 and V7♭9. ★ **The diminished seventh chord is a "disguise" for V7♭9**: after bebop, V7♭9 is used directly in place of diminished chords. The **minor-third repetition** principle lets one voicing serve several V7♭9 chords |
| **Whole-tone scale** | Over augmented chords and V7♯5 |

---

### 3.9 ★ Blues harmony: the foundation shared by jazz, rock, and R&B (Chen Yunqiang)

The library previously had only one line on "the rasp of ♭3 ♭5 ♭7". Blues harmony is a complete system; page references come from *Jazz Harmony*.

**The functional skeleton is fixed** (p0192): the first four bars are tonic I7, bars five and six are subdominant IV7, and bars nine and ten form the cadence.
★ **Only in the blues can the I chord use a dominant 7 as its tonic function** (p0187).

**Four stages of evolution of the basic progression** (p0186–0187): major triads on I and IV only → every chord made a dominant 7 → add IV–V–I in the last four bars → change the last four bars to **V–IV–I**.
★ **Reverse cadences are a distinctive feature of the blues.**

**Three positions where change is possible** (p0192–0193): weak positions in the harmonic rhythm, junctions between functional sections, and between one chord and the next. Common bar-by-bar changes (p0193–0195):

| Bar | Change |
|---|---|
| 2 | I7 → IV7 |
| 4 | I7 → III-7♭5 (equivalent to an I9 with the root omitted) |
| 5 | Add I7 after IV7 |
| 6 | Add **♯IV°7** after IV7 (equivalent to IV7 with ♭9, root omitted), so that the I7 in bar 7 is used in inversion with the fifth in the bass, making the bass line move up by a **semitone** from IV → ♯IV° → I/5 |
| 8 | What is added is determined by the first chord of bar 9: if it is II-7, add V7/II; if it is IV7, add III-7♭5 |
| 9–10 | Variable II-7 – V7 – I7 – ♭VII7 |
| 11–12 | Add a secondary or extended dominant |

★ **Identifying the blues is decoupled from the form** (p0196): using I7 and IV7 with the blues scale (1 ♭3 4 ♯4 5 ♭7) makes it blues, **not necessarily twelve bars**; eight-bar and sixteen-bar forms are equally common.

Tension: **the 11th over I7, IV7, and V7 is not usable**; on I7 the ♭3 can be used as ♯9 (p0189–0190).
The minor-second clash between harmony and scale is precisely the flavour of the blues, and corroborates the account in `mc-melody` reference §4.
`mc-style-rock-band` and `mc-harmony` both draw their skeletons from here.

## 4. Comping (accompaniment)

**The whole point of comping is to leave room for the improviser.**

| Principle | Explanation |
|---|---|
| **Do not fill everything** | ★ This is its biggest difference from pop accompaniment. Pop accompaniment holds a stable place in the texture; comping **comes and goes** |
| **Respond, do not pad** | Listen to what the improviser has just played and react |
| **Omit the root in voicings** | Leave the bass line to the bass player. **The 3rd and 7th are the skeleton** (guide tones) |
| **Arranging sus chords** | Levine has a dedicated section (p0064): they are the "unresolved" sound |

★ **Transfer warning** (§2): **comping rhythm must not be carried into pop**.
Pop has no improviser, so those gaps become holes.

---

### 4.1 Guide-tone lines: how to write the inner voices (Chen Yunqiang p0093–0096)

§4 says the 3rd and 7th are the skeleton; this section gives the method.

**Characteristic notes**: the 3rd and 7th of seventh chords; the 3rd and 6th of sixth chords; **for chords with altered fifths such as diminished-7, half-diminished, and augmented-7, the fifth is also a characteristic note**.

**Connection rules**: when the root moves by a fifth, a fourth, or a third, the motion is **3 → 7 or 7 → 3**; when the root moves stepwise, or by a third, or stays put, the motion is **3 → 3 or 7 → 7** in the same direction (for a third-related move, either is allowed).

**Four adjustments** to stop the line from becoming monotonous or the voices from sitting too high or too low: add the root or the fifth (adding usable extensions where needed); leap by octave while the chord is sustained; swap the 3rd and 7th while the chord is sustained; re-plan the starting note after a harmonic section ends.

★ **It is not only for jazz**: this is a general method for writing inner voices or counterpoint lines, and it works equally for writing countermelodies. The melody of *All The Things You Are* is largely built from guide-tone lines.
`mc-counterpoint` §3 covers relative motion; this section covers the choice of notes.

## 5. Form: Head–Solos–Head

```
Head (theme, once or twice)
  → Solo 1 (cycling the head's harmony several times)
  → Solo 2 …
  → (4s / 8s: trading phrases with the drummer)
  → Head (once more)
  → Tag (tag / fade / defined ending)
```

★ **The fundamental difference from pop form**:
- **Pop structure is a sequence of content** (verse says this, chorus says that)
- **Jazz structure is the same harmonic cycle played many times**, with the content filled in on each pass by the improviser

**So the meaning of `form[].bars` differs in jazz**:
it is "how many bars one chorus has" (32-bar AABA is the standard), **not "how long this section is"**.

**Common head forms**: AABA (32 bars), ABAC, 12-bar blues.
For ready-made repertoire, see the Fake Book (source listed below).

---

## 6. Bebop phrasing

From Valerio:

| Element | Key point |
|---|---|
| **Harmonic foundation** | Extensions + alterations |
| **Interlocking triads and sevenths** | Use upper-structure triads to express complex chords |
| **Harmonic-melodic improvisation** | The improvised line is simultaneously a statement of the harmony |
| **Rhythm** | — |
| **Phrasing** | — |
| **Accents** | ★ One of the hallmarks of bebop is **accents falling on the offbeat** |
| **Contour** | — |

**Historical line**: Ragtime → Blues → Swing → Bebop.
★ Knowing this line is useful, because **the word "jazz" referred to different music in different decades** (§1①).

---

## 7. ★ Measured: how jazz arrangements differ from pop arrangements

**Cambridge-MT corpus, jazz-acoustic (10 tracks) vs the rest:**

| Metric | jazz-acoustic | pop | rock | hiphop-rnb |
|---|---|---|---|---|
| **Roster size (median)** | ★ **22 tracks** | 36 | 30 | 37 |
| **Number of sections (median)** | 9 | 10 | 10 | 9 |
| **Share of instruments present at the opening** | **16%** | 21% | **8%** | 24% |
| **Instruments entering mid-piece** | ★ **20** | 29 | 26 | 26 |
| **Instruments leaving early** | ★ **10** | 16 | 18 | 28 |

**Three reliable readings**:

1. ★ **Jazz rosters are clearly smaller (22 vs 36)** —
   partly because it was **recorded live together**, with less overdubbing.
   **This can be carried over**: a small ensemble with every part doing something is the most valuable thing jazz can offer pop.
2. ★ **Jazz also has the fewest entry and exit events (20 entries / 10 exits)** —
   its changes come not from **changing the ensemble**, but from **the same group of players varying the content**.
3. **hiphop-rnb has the most early exits (28)** — it is the most "subtractive" style.

> ⚠ **Unreliable reading**: BPM. Detected jazz median is 117, range 74–162, but beat tracking has a known double-tempo error on swung grooves. **Do not cite this figure.**

---

## 8. Field mapping to ARR-SPEC

| Field | This skill |
|---|---|
| `meta.style_layer` | `mc-style-jazz` |
| `form[].harmony` | §3. ★ In jazz **harmony is the protagonist**, so degrees must be written out in full |
| `form[].bars` | ★ §5 — means "the length of one chorus" |
| `arrangement.roster` | §7 — **target just over 20 tracks, not 36** |
| `groove.feel` | `swing16` / `shuffle` |
| `render.*.style_prompt` | State which jazz style it is (§1①); do not write only `jazz` |

---

## 9. Checks after writing

- [ ] Specified **which** jazz style, not a generic "jazz"
- [ ] Checked the §2 transfer table; every technique carried out of jazz is in the "transferable" column
- [ ] When carrying something into jazz, checked whether it breaks the premise that "someone is improvising"
- [ ] Harmony is thought of as **regions of scale**, not just a sequence of chords (§3.3)
- [ ] Roster is **clearly smaller than pop** (target just over 20, not 36)
- [ ] If there is an improvised section, the meaning of `form[].bars` is clearly labelled
- [ ] Comping leaves gaps and **does not fill everything**
- [ ] Altered dominants and diminished-scale licks have not been carried into pop songs (unless jazz flavour is intended)

---

## Appendix: Sources

- **Mark Levine, *The Jazz Theory Book***:
  all of §3 (chord-scale, avoid notes, melodic minor harmony and interchangeability, diminished scale, whole-tone scale).
- **Valerio, *Bebop***: §6.
- **Fake Book**: repertoire and head forms.
- **Jazz Guitar Groove**:
  CAGED, scale patterns, four-note sequences, chromatic alterations, triplet patterns.
  ★ **This book was originally misfiled under `mc-rhythm-section`; it is in fact improvisation vocabulary and belongs to this skill and `mc-melody`.**
- **Measured data**: Cambridge-MT multitrack measurements (jazz-acoustic, 10 tracks).
- Jazz harmony piano practice (practical companion to Chen Yunqiang's *Jazz Harmony*)
