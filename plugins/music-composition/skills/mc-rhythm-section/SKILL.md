---
name: mc-rhythm-section
description: Rhythm section arranging and MIDI programming - drums, bass and harmony instruments as one unit, and how to make programmed parts sound played. Includes a style-by-style drum pattern and tempo lookup (rock, funk, R&B, hip hop, jazz, blues, Afro-Cuban, Brazilian, country, metal, techno); kick/snare/cymbal roles, tempo ranges, straight/swing/shuffle/half-time feel, signature fills and hi-hat handling; groove classification by feel and subdivision; the order in which to pick a pattern; partial and percentage quantization; push/pull with real magnitudes; linear drumming; ghost notes; the top/bottom/left/right map of a kit; and the three ways a bass sits against the kick (locked / answering / interlocking). Use when choosing a drum pattern or tempo for a style, when programmed drums sound mechanical, when deciding what to quantize, or when filling the tempo/groove/push_pull/fill_policy/bass_kick_relation fields of an ARR-SPEC. Keywords: rhythm section, drum kit, bass, programming, quantization, groove, ghost notes, linear drumming, push/pull, fills.
---

# Rhythm Section & Programming

**This skill covers how to make what you write sound like someone is playing it.**

> Core creed (the Japanese arranging school's formulation): **work out how real instruments are actually played, then reproduce that.**
> All realism is built on **the physical limits and habits of an imagined player**.

## Which Sections to Read for Each Task

| Symptom / task | Read |
|---|---|
| **Don't know what drum pattern this style needs** | §1.1 + [reference.md](reference.md) §8 |
| **How fast to set the tempo** | §1.1 step 2 + the tempo column of reference-styles.md §8 |
| **Should the feel be written as straight or swing** | §1.1 steps 1 and 3 + reference.md §9.2 |
| Drums sound too perfect, too mechanical | §2 the four ways to approach quantization |
| Hand-played parts are too messy | §2.1 percentage quantization |
| Groove "doesn't move", lacks energy | §3 push and pull |
| Drum hits pile up but lack power | §4 linear drumming |
| Too much empty space between snare hits | §5 ghost notes |
| The kit blurs into one mass | §6 Top/Bottom/Left/Right |
| Where to put the fill | §8 position of fills |
| How to match bass with kick | §7 three configurations |
| Bass line isn't clear | §7.2 |
| Filling the groove section of an ARR-SPEC | §9 + §10 |

## Boundary: What This Skill Does Not Cover

| Not covered here | Covered by |
|---|---|
| Choice and blending of instruments and timbres | `mc-orchestration` |
| Drum kit **competing with other instruments** for frequency bands | `mc-texture-layering` (the frequency and spatial distribution **within** the kit is covered here in §6) |
| The **structural role** of a fill across the whole song (foreshadowing at a section seam, refusing to foreshadow, deliberately withholding it on the second pass); this skill's §8; the entry/exit event table is in `mc-arrangement-arch` §5.2 | §8 of this skill |
| How drum machine timbres are synthesised | `mc-sound-design` |
| Music theory of rhythm patterns (compound rhythm, notation of syncopation) | `mc-rhythm-groove` (L1) |
| **How syncopation and anticipation are themselves notated and calculated** | `mc-rhythm-groove` (L1) |
| **The "third sense of time" in hip-hop where straight and swung coexist** | `mc-style-hiphop` |
| **Bar-by-bar drum pattern templates for a given style** | [reference-styles.md](reference-styles.md) §8 (gives kick / snare / hat placements and tempo ranges by family, not by style name); when a style deviates, consult its L3 skill |
| EQ, compression, parallel compression of drums | Mixing; this package only supplies the `mix_intent` brief |

> `mc-rhythm-groove` (L1) covers **what the rhythm itself is**; this skill covers **how to play it so it sounds human**.
> **Selecting** a style's drum pattern (which family, how fast, what feel) is a procedure and belongs here; **templates** (patterns fixed bar by bar) are style material and belong to L3.

---

## 1. Required Before Starting

| Required | Question |
|---|---|
| **① How precise is this style** | Absolute quantization? Or loose and organic? **Answer this first; everything in §2 depends on it** |
| **② Who keeps to the grid, who doesn't** | You must be able to name at least one part that "keeps" and one that "doesn't" |
| **③ Magnitude of push/pull** | Specific to milliseconds or ticks. "Slightly ahead" does not count as filled in |
| **④ Which bars the fill occupies** | And **why it sits there** |

### 1.1 ★ Decision Order for Choosing a Drum Pattern

**These five steps have a sequence; doing them backwards wastes work**: tempo changes the feel, the feel changes where the kick sits, and the kick's position determines how the bass is matched.
Values are looked up in [reference.md](reference.md) §8 (drum patterns and tempo quick reference by style) and §9 (groove classification and character).

**Step 1: Set style and feel.** Find this style's row in reference-styles.md §8 and copy its feel column. The options are more than straight and swing:

| Feel | Criterion | Examples |
|---|---|---|
| straight | Eighths/sixteenths evenly divided | Standard Rock, Disco, Techno, Bossa |
| swing | Played with a triplet sense, whether notated as eighths or dotted (Groove Essentials p0073) | Big Band, Dixieland, Western Swing |
| shuffle | The 1st and 3rd of each beat's triplet (Drummer's Bible p0013); can also be thought of as "swing with some kind of backbeat" (Groove Essentials p0072) | Blues Shuffle, Country Shuffle |
| half-time | **Backbeat falls on beat 3** rather than 2 and 4 (Groove Essentials p0036) | Half-Time Standard Rock, Purdie Shuffle |
| 12/8 | Notated in 4/4, felt in 12/8, with all 12 eighths played | 12/8 Slow Blues, Country Ballad |
| in the crack | Between straight and swung, not settling on either side | New Orleans Funk (Drummer's Bible p0095), Second Line (p0112), Reggae One Drop (p0074) |

> "In the crack" is not "undecided"; it is **a clearly defined third option**. If `feel` accepts only the first few options,
> choose the closest one and note it. The sense of time where straight and swung coexist in hip-hop belongs to `mc-style-hiphop`.

**Step 2: Set the tempo range.** Copy the range from reference-styles.md §8 and place it in the ARR-SPEC `tempo`:

- Groove Essentials deliberately **does not specify a bpm**; the final choice is made by "feels good" (p0116), and each groove gives only a slow and a fast option (p0003).
  **The range is an entry point, not a verdict.**
- **Tempo changes the feel in turn**: swing gradually becomes straighter as tempo increases; ♩=75 to 350 is one continuous climb (Groove Essentials p0122).
  After setting the tempo, return to confirm the step 1 feel still holds.

**Step 3: Set the backbeat position.** The feel is pinned to notes here, and it is the first thing a listener checks when judging your groove:

| Where the backbeat is | What it means |
|---|---|
| 2 & 4 | Default. Standard Rock, Blues, Disco |
| Beat 3 | Half-time (Groove Essentials p0036) |
| Displaced | Displaced Funk: **keep at least one standard backbeat so the groove doesn't lose its footing** (Drummer's Bible p0096) |
| Rarely on beat 2 | Country Waltz (Drummer's Bible p0084), Klezmer's Hora (p0129) |
| No sustained snare pattern | Calypso (Drummer's Bible p0071) |

**Step 4: Set the relationship between kick and bass, linking to the three configurations in §7.1.** Do not default to interlocking; **first check this style's conventions**:

| Configuration | Stylistic evidence |
|---|---|
| **Locked** | The repeating kick pattern in Cumbia **usually matches the bassist** (Drummer's Bible p0047); Samba's foot imitates the surdo and **cooperates with the bassist** (p0059). Big Band is similar, but four-on-the-floor should be played **lightly** so it does not interfere with the walking bass (p0115) |
| **Answering** | Heavy four-on-the-floor in Techno/House fills the low frequencies (Drummer's Bible p0162); in Reggae One Drop the bass weaves through the groove while the drummer anchors the bottom (Groove Essentials p0088) |
| **Interlocking** | In Mambo the kick supports the bass's tumbao, **sometimes in unison and sometimes split** (Drummer's Bible p0037); "aligned in the first half of the bar, rubbing in the second half" (Groove Essentials p0021, p0034), which is the prototype of the bar-by-bar locked/split table |

**Step 5: Set the hi-hat subdivision and fill family.** For subdivision (eighths / sixteenths / triplets / bell pattern), consult the "drum pattern" column of reference-styles.md §8; for fills, consult §8.11:

- **Close the open hi-hat within the groove**; closing it randomly kills the groove (Groove Essentials p0030); **don't play fast hi-hat too loudly** (p0033);
  the hi-hat is also the knob for "how steady this song is", see reference.md §2.3
- In straight styles, triplet fills are rare; shuffle styles use only swung eighths and triplets;
  the order for escalating a variation is **note value → accent → syncopation → orchestration** (Drummer's Bible p0172)

**Self-check actions**: ① Can you say which beat the backbeat falls on (if not, step 3 was skipped);
② Is the tempo a range you copied or an integer you wrote on a whim; ③ Were the kick–bass configuration chosen by convention or filled in by default; ④ If you said interlocking, can you list "which bars are locked and which are split" (if you cannot, fall back to locked); ⑤ Has the fill's note value gone outside its family.

---

### 1.0 Two Higher-Level Decisions Before Choosing a Drum Pattern (Illustrated Arranging p0028–0029)

§1.1 starts from style and feel; illustrated arranging has two decisions before it: **A** whether the basic groove centres on quarter, eighth, or sixteenth notes; **B** whether the rhythmic figure contains syncopation, and whether the syncopation is eighth or sixteenth.
Once these two are set, style and feel have something to attach to.

**Three levels of high-register rhythm instruments** (p0036): sustained, closed hi-hat < ride cymbal < open hi-hat; use closed to suppress, ride for a sense of space, and open to heat things up.
**The open hi-hat is one of the few instruments able to produce very high frequencies**; use it when the chorus needs to lift the register upward (p0041).
★ Two sources side by side: illustrated arranging says once the hi-hat is opened it basically stays open, and the second verse should keep it open to avoid "too much sense of back-and-forth" (p0039, p0044); Groove Essentials says the open hi-hat should be closed within the groove, and random closing kills the groove.
One addresses consistency at the section level, the other cleanliness at the bar level; the two do not govern the same thing.

## 2. Quantization: Four Approaches

### 2.0 ★ Judge the Style First: This Rule Has Real Failure Conditions

**Read the two accounts side by side, because on the surface they conflict:**

| Source | Statement |
|---|---|
| DeSantis (p0154) | In **Techno, House, Electro, and EDM**, **absolute quantization is entirely appropriate**, often accompanied by perfectly uniform, unvaried dynamics. In most **hip-hop**, a looser, more organic feel suits better, because the style often directly samples recordings of real drummers |
| This library's corroboration table | "Not every part should align strictly to the grid" **hit 62/62**, a strong rule |

**Reconciliation: the key is the phrase "every part":**

What we measured is the **onset offset from the grid across the entire mix**. Even if a techno track's drum kit is 100% quantized,
as long as one played instrument (bass, vocals, sampled material) is off the grid, the overall offset exists.

So the correct reading is:
- **The drum kit may be absolutely quantized**, if the style calls for it
- **But not every element across the whole piece should sit on the grid**: that is the fingerprint of a generative model, not a requirement of any style
- In other words, **quantization is a per-instrument decision, not a global switch**. This ties directly into §2.2

### 2.1 Percentage Quantization (Partial Quantization)

Modern DAW quantization strength is expressed as a percentage (p0154):

> 100% quantization to sixteenth notes → notes move to the nearest grid point;
> **50% quantization → notes move only half the distance between their original position and the nearest correct position** (p0155)

> **Effect: reduces rather than eliminates human inaccuracy; it is the best way to "retain the human feel while correcting playing looseness"** (p0155).

**Usage**: when hand-played material is too messy, try 50–70% first rather than going straight to 100%.

### 2.2 ★ Quantizing Only Some Instruments

The conventional practice is to quantize the whole drum kit as one unit (p0155). **The improvement is to separate them**:

> - Quantize **only the hi-hats**, leaving **kick and snare** as played
> - Or the reverse: keep the hi-hats loose and quantize the kick and snare to perfect alignment (p0155)

> **Although perfect quantization does not accurately represent how real drummers play, this technique produces more realistic drum patterns**,
> and it can be combined with percentage quantization (p0155).

**This is the most practical move in this section**, and it is where the reconciliation in §2.0 lands:
**let one part stay on the grid as a reference frame, and let another part not; the "human" quality you hear comes from the tension between the two.**

### 2.3 Finding Your "Natural" Tempo

A common technique is to record slowly and play back faster. However (p0155–0156):

> **There is a floor to rhythmic accuracy**: most people are most accurate in **a particular range of tempos**, neither too slow nor too fast.

**Suggestion**: find a tempo that feels comfortable, try composing at that tempo directly,
**and see whether you get the desired feel without any subsequent quantization** (p0156).

### 2.4 Humanization / Randomization

The DAW's humanize/randomize functions. **Use these last, not first** —
they add meaningless jitter, whereas §2.2 adds structured difference.

> Randomization tools lack the most important element that makes music work: **your own taste**.
> When you control each element, you make conscious micro-decisions; when a tool generates a wrong note, you easily overlook it (p0273).

**How to set it**: **increase the randomization until it is clearly excessive, then dial it back** (p0274). The right amount is entirely subjective.

---

## 3. Push and Pull

> **Measured**: in 62 real arrangements, **62/62 were not strictly aligned to the grid across all parts** (strong rule).

A groove that "rushes ahead" or "sits back" comes from **systematic offsets of different parts relative to the grid**,
not from random jitter.

**Method**: specify **which part pushes, which part pulls, and by how much**, and keep at least one part on the grid as a reference frame.


A measured sample (City Pop, 112 BPM):

| Part | Offset | Why |
|---|---|---|
| Bass | **−12 ms** (pushes ahead) | The sole source of this song's "rushing ahead" |
| Clean guitar | **+8 ms** (pulls back) | Separated from the bass, creating an illusion of width |
| Drums | 0 | **Keeps to the grid, serves as the reference frame** |

**Self-check action**: does your push_pull have a magnitude? Writing only "slightly ahead" amounts to writing nothing.

**Failure condition**: hard-gridded electronic dance music may be all 0, **but you must state that this is a stylistic choice**
(give the reason in `checks.exemptions` in ARR-SPEC); it must not be an omission.

---

## 4. Linear Drumming

> **Linear patterns treat every instrument as equal in weight, rather than emphasising particular beat positions by layering multiple parts** (p0163).

In other words, **only one drum element sounds at any moment**, with no stacking.

**Why it helps**: when drum hits pile up yet lack power, it is usually because each strong beat is kick + snare + hat slamming together,
which ends up muddy to the ear. The linear approach keeps every stroke clear, so density is high without blur.

**Suited to**: funk, fusion, contemporary R&B, and passages that need "dense but not muddy".
**Not suited to**: places that need heavy unison impact (the chorus landing points in rock).

---

## 5. Ghost Notes

> **Ghost notes are extremely soft notes, usually played on the snare, used to fill the space between prominent notes in a pattern** (p0166).

**This is the least effortful move for "playing like a human"**. A real drummer's hands are always moving, and the very soft taps that land between strong beats
are something a machine does not produce on its own.

**Method**: add snare notes with very low velocity (typically 20–40) between the main snare hits.
**The key is that velocity must be low enough**: too high and they become part of the rhythmic figure; only low velocity gives the "human" quality.

---

## 6. Spatial and Frequency Distribution of the Kit: Top / Bottom / Left / Right

(p0171) arranges the drum kit as a **two-dimensional plane**:

| Axis | Meaning |
|---|---|
| **Bottom** | Low frequencies: kick, floor tom |
| **Top** | High frequencies: hat, ride, cymbals |
| **Left / Right** | Panning: arrangement of toms, width of overheads |

**Usage**: check that all four directions of your kit have something in them.
If only bottom and top are present, with everything in the centre left and right → the kit sounds like "a line" rather than "a set of drums".

> The **practical execution** of panning belongs to mixing; but **which instrument should sit in which position** is an arranging decision, so it is covered here.

---

## 7. Bass and Kick: The Other Half of the Rhythm Section

No matter how well the drums are played, if the relationship between bass and kick is wrong, the entire rhythm section falls apart.

### 7.1 Three Configurations: You Must Choose One and State It

Bass and kick both occupy the low frequencies; handled poorly, they drown each other out. There are only three routes (p0044–0047):

| Configuration | Definition | Effect / Suitability |
|---|---|---|
| **Locked** | The bass rhythm **follows the kick, with rhythms fully coinciding**, differing only in note length | **Strong attack, solid and elastic**, forming a powerful, full bass part |
| **Answering** | The bass **avoids the kick's rhythmic points**, placed on free points outside the kick, in call and response | Suited to styles like **electronic dance music** where the kick covers the low range — **avoids timbral masking and low-frequency muddiness** |
| **Interlocking** | Combines both: **coincides when needed, splits and answers when not** | **Can thicken the low end when needed while keeping a clear bass melodic line**; suited to more modern-sounding pop |

> **Interlocking is the default recommendation**: it is the only option that delivers both "thick" and "clear".
> However, it requires you to decide bar by bar where they coincide and where they split; **if you cannot write out this table, fall back to locked**, and do not pretend you are doing interlocking.

**This point and `mc-texture-layering` §4.2 are two aspects of the same problem**:
that section gives the general three solutions for frequency-band conflicts (sharing frequencies / separating registers / alternating),
while this is the concrete form of the specific low-frequency conflict. **Answering = alternating appearance**.

### 7.2 Writing Requirements for Bass

**Overall goal**: achieve a **clear, flowing bass part with strong melodic sense** (p0047).

| Requirement | Explanation |
|---|---|
| **Interval relationships** | The bass is a low instrument, and **leaps work better than stepwise motion**, since stepwise motion in the low register easily blurs into a mass |
| **Direction of stepwise motion** | When using stepwise motion, **continuous descending motion works better than ascending** |
| **Texture avoidance** | Avoid **low-frequency collisions** in the bass register as far as possible |
| **Register** | **The deeper the descent the better, but balance range against clarity**; going too deep makes it inaudible |

### 7.3 Two Bass Forms and Timbre Matching

| Form | Characteristics | Suited to |
|---|---|---|
| **"Point"** | Played rhythmically, with weak melodic-line character, mostly rhythmic accents | Strong rhythmic feel, fast tempos, **dance music** |
| **"Line"** | Emphasises the melodic line | The **most widely used** in popular music |

**The bass timbre should follow the kick** (p0047):

| Kick | Bass choice |
|---|---|
| Acoustic drums | **Electric bass with broader low-frequency range** |
| Heavy electronic timbres | **Brighter synth bass** |

**Physical limitations of the bass** (which determine that it cannot be written too densely) (p0043):
- Deep and full, **sounds more slowly than other instruments** — cannot play overly dense melodies
- **Too many simultaneous polyphonic notes cannot sound together**, or the bass register becomes muddled

---

### 7.4 Hard Rule for Bass and Bass Drum, Side by Side with §7.1 (Illustrated Arranging)

Illustrated arranging gives a rule harder than the three configurations in §7.1 (p0047–0051):
**when the bass drum sounds, the bass must play along; when the bass drum is silent, the bass may play alone; the number of sounds must be bass ≥ bass drum.**
The same applies to syncopation: **it is acceptable for the bass drum to be syncopated while the bass is not, but it is wrong for the bass to be syncopated alone while the bass drum is not.**

★ **This directly conflicts with the "answering" configuration in §7.1**; side by side: illustrated arranging describes the default for the **bright-tempo** category, where the goal is a solid groove;
the answering configuration intentionally has two parts offset in dialogue, at the cost of a looser groove. The criterion is whether this passage should feel "solid": if so, follow the illustrated-arranging rule; if not, use answering.

### 7.5 The Fifth: Playing Only the Root Lacks Brightness (p0052–0055)

A bass that plays only the root has no shift in centre of gravity. Uses of the fifth: **place it a fourth below the root** (a fifth above sounds abrupt);
**place it before an accent you wish to emphasise**, as a launching build-up; when encountering slash chords, the fifth may become a non-chord tone, in which case use **the nearest chord tone**.

### 7.6 Using Drum Patterns for Section Contrast: Three Examples and Two Taboos (Illustrated Arranging p0039–0046)

| Section | Approach | Effect |
|---|---|---|
| Verse A | No kick on the downbeat of beat 3 | Floating feel |
| Verse B | Two eighth-note snare hits on beat 2, switching to ride cymbal | Distinguishes it from A and the chorus |
| Chorus | Kick syncopation on the off-beat of beat 2, open hi-hat to raise the high frequencies | Sense of momentum |

- ★ **Do not add a crash cymbal on the chorus syncopation point**: many people add one there, but it weakens the syncopation that really matters (p0041)
- **Cross-bar syncopation** is most commonly kick with crash, a technique to use only when "this is the spot"; adding too many weakens the impression (p0031, p0037)
- **The rhythmic patterns of the last four bars of a section should vary together with the main melody**, which is the knack for "making it easy to remember" (p0046). This is handling at the level of drum patterns at the end of a section, a different layer from the seam scheduling in `mc-arrangement-arch`
- Guitar uses voicing types for section contrast: verses use power chords, the chorus switches to closed chords (p0063); piano changes the left hand to quarter notes, and uses balanced two-hand combinations to distinguish verse from chorus (p0073, p0076)

## 8. Position of Fills

> **Measured**: `fill_policy.bars` may not be an arithmetic progression with common difference 4 (lint #10).
> "A fill every 4 bars" is textbook AI-sounding.

**The correct approach is to give every fill a reason**:

| Reason for the fill | Example |
|---|---|
| Lift before a section change | The bar before entering the chorus |
| **Masking a seam** | The second verse is 4 bars shorter than the first, so a fill mid-section covers it |
| Depth scheduling | Briefly bringing the drums to the foreground (see `mc-arrangement-arch` §3.1) |

A measured sample of fill positions: `[22, 28, 44, 62, 78, 88, 106]`,
with gaps `[6, 16, 18, 16, 10, 18]` — **deliberately unequal**. Bar 44 is the only mid-section fill,
used to mask the seam where A2 is 4 bars shorter than A1.

---

## 9. Mapping to ARR-SPEC Fields

| Field | Section of this skill |
|---|---|
| `arrangement.tempo` | §1.1 step 2 (look up the range in reference-styles.md §8) |
| `arrangement.groove.feel` | §2.0 style judgement + §1.1 steps 1 and 3 (**which beat the backbeat falls on** is the criterion) |
| `arrangement.groove.quantize_policy` | §2.2 per-instrument quantization |
| `arrangement.bass_kick_relation` | §7.1 three configurations; **which one to choose** depends on the style conventions in §1.1 step 4 |
| `arrangement.groove.push_pull` | §3 (**must include a magnitude**, lint #11) |
| `arrangement.groove.fill_policy` | §8 (lint #10 forbids equal spacing) |
| Groove-type parts in `arrangement.roster` | §4, §5, §6, §7 |
| From chord to accompaniment figure: form, four steps, four knobs for figure construction, arpeggiation and inversions, two accompaniment parts yielding to each other | [reference.md](reference.md) §5–5.4 |

---

## 10. Must Pass After Writing

- [ ] **Style, feel, and tempo all resolve to concrete values**, not something like "rock, mid-tempo"; you can state **which beat the backbeat falls on**
- [ ] The tempo is taken from the common range for this style (if outside the range, state why), and the feel still holds at this tempo
- [ ] The kick–bass configuration was chosen **following this style's conventions**, not defaulted to interlocking
- [ ] The fill's **note-value family** matches the style (no random triplets in straight styles); open hi-hats are all closed within the groove
- [ ] You answered "how precise is this style" first, and later decisions are consistent with it
- [ ] **Quantization is decided per instrument**, not one switch for the whole kit
- [ ] At least one part keeps to the grid, and at least one does not
- [ ] `push_pull` **has a magnitude in milliseconds or ticks**, not "slightly"
- [ ] If all are 0, the stylistic reason is given in `exemptions`
- [ ] Ghost notes are added between snare hits, with low enough velocity
- [ ] The kit has content in all four directions: Top/Bottom/Left/Right
- [ ] Fills are **not equally spaced**, and you can state why each fill sits where it does
- [ ] The bass–kick pairing **has been set to one of locked / answering / interlocking**, with the choice stated
- [ ] If you say interlocking, you **can state bar by bar where they coincide and where they split**
- [ ] The bass timbre and kick timbre **have been matched** (acoustic drums with electric bass / electronic kick with synth bass)

---

## Appendix: Sources

- **Mick Berry & Jason Gianni, *The Drummer's Bible: How to Play Every Drum Style***
  — style, feel, tempo ranges, backbeat positions and fill note-value families in §1.1; the style-by-style quick reference table is in [reference.md](reference.md) §8.
- **Tommy Igoe, *Groove Essentials***— classification of grooves in §1.1,
  time centre, the relationship between swing and tempo, and hi-hat handling; the classification summary is in [reference.md](reference.md) §9.
  Where it differs from the Drummer's Bible (whether tempo should be marked with a number, how shuffle is defined), both views are presented side by side, each with its source marked.
- **Dennis DeSantis, *Making Music*** (Ableton) — the core of §2, §4, §5, §6
  (On Looseness / Linear Drumming / Ghost Notes / Top, Bottom, Left, Right / Randomness and Responsibility). Page numbers refer to that book's pages.
- **Wen Hailiang, *Bianqu* (Arrangement)** (popular music academy series) — all of §7
  (three configurations of bass and kick p0044–0047, bass writing requirements p0047, point/line forms of bass p0043); the rules for arranging individual drum-kit parts are in [reference.md](reference.md).
- *Pro Songwriting Explained* and *Pro Songwriting Techniques* (Japanese), the MIDI programming sections — supplementary material.
- Measured data comes from statistics on 62 Cambridge-MT multitrack recordings.
- The specific drum pattern library and velocity parameter tables for each style are in [reference.md](reference.md).
