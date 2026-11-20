# mc-form Reference: Section Contrast Techniques, Section-by-Section Lineup Table and Classical Form Catalogue

> [SKILL.md](SKILL.md) covers how to arrange structure; this file covers **how to make sections actually sound different**,
> and a catalogue of classical forms for when pop terms run out.
>
> Sources: *A Book That Explains How Professionals Write Songs*, Takayama Hiroshi, *Melody Writing for Popular Music Composition* (expanded edition);
> **Wu Zuqiang, *Musical Forms and Work Analysis***.

---

## 1. ★ Section contrast: the six-element table

> **A sense of sectionhood does not come from attaching labels; it comes from contrasts in the nature of motion.**
>
> **Premise: the character of the same material is determined by its context**:
> if it follows a static phrase, it is heard as a small climax; if it follows a soaring phrase, it becomes a soothing answer.

**The typical development from A to sabi. Reversing any one item produces a contrast;
reversing several at once = strong contrast (suited to entering the chorus), reversing a single item = weak contrast (suited to small variations within a section):**

| # | Element | A-melo (introductory) | Sabi (climax) |
|---|---|---|---|
| 1 | **Range** | Low, narrow | High, wide (**pushed up in one breath across a wide range**) |
| 2 | **Note values / density** | Speech-like density of short notes, or long sustained "white-jade" (*shiratama*) notes | ★ **The opposite of A**: if A is dense, the sabi opens out into long note values; if A is sparse, the sabi adds density |
| 3 | **Interval motion** | Repeated notes, stepwise motion | **Large leaps**, especially an upward leap at the opening |
| 4 | **Phrase starting point** | Off-beat / upbeat | Starts on a strong beat |
| 5 | **Rhythmic character** | Plain, sitting on the beat | Syncopated, or conversely a powerful rhythm locked tightly to the beat |
| 6 | **Harmonic rhythm** | Mainly short chords (changing frequently) | Mainly long chords (or the reverse), matching the expansion of the melody |

### 1.1 ★ The trick for choosing contrast material

> **Identify the most characteristic element at the opening (*dasi*, the "start") of the preceding section, and reverse it.**

Example: if section A's signature is "upbeat + repeated notes + low narrow range",
then the chorus contrasts it with "strong-beat start + large leaps + high wide range".

**Prioritizing the character at the start of each phrase is a general technique for making structure clear.**

### 1.2 "Different motion ≠ audibly contrasting"

> If the motion differs but the **character is the same kind** (all eighth notes, narrow range, stepwise), it sounds like "the same thing continuing".
> ★ **For quiet sections, this is actually an appropriate sense of unity.**

**For a clear contrast, the nature of the motion must differ markedly**:
stepwise ↔ leaps, short note values ↔ long note values, on the beat ↔ syncopated. **Reverse several items at once.**

### 1.3 A demonstration

Section A = upbeat, densely syncopated eighth notes;
Section B = sparse, sustained whole notes ("white jade");
Sabi = raised register, medium density, motif repetition
→ **the section contrast is built through density and register.**

This is an abstract skeleton, used only to demonstrate which cells of the six-element table are hit by "reversing a single item" and "reversing several items". It is not a breakdown of any real song. For real examples, see `mc-case-studies` §2.4 (three cases: Kuwata Keisuke, "Hey Jude" and "Sunday Morning" can all be checked against this table in reverse).

---

## 2. Section-by-section lineup thickness table

Using a typical pop lineup (drums, bass, acoustic guitar, electric guitar, piano) as the example.

★ **Relationship between this table and `mc-arrangement-arch`**:
It gives **the default values of convention**; breaking the default (why this song's 2A is actually thicker) belongs to arrangement-arch.

| Section | Thickness keyword | Arranging points |
|---|---|---|
| **Intro** | Thin lineup | Not too long; flow smoothly into A; the theme can be stated by a string quartet; **bury a phrase that previews the chorus** |
| **1 A-melo** | **Leave space** | Piano or acoustic guitar + bass + drums is enough; **may even drop the bass and drums**; open soundstage, with breath and air audible |
| **1 B-melo** | Slightly thicker | A thin layer of sustained strings, flute thickening; mandolin / sitar / harp / soft short trumpet accenting the motif; electric guitar harmonics. ★ **Do not bring everything in at once**: "rest → fill with a short phrase" |
| **Section seam** | Bridging sounds | Strings doing a rising run (*kakeagari*, a fast ascending scale), cymbal roll, harp glissando pushing upward; ★ **when the vocal enters on an upbeat, boldly go unaccompanied** |
| **1 sabi** | Everyone in | Everyone pushes toward the climax; strings play **counter-melody**; add brass; add choir or lyrical harmony (*ji-hamo*) |
| **2 A-melo** | **A different impression from 1A** | ★ **Where the arranger shows their skill**: 1A piano → 2A acoustic guitar; remove drums and bass; double-tracked vocal changed to single-tracked (breath audible) |
| **2 B-melo** | — | May be the same as 1B; fine adjustments such as strings are where the skill lies |
| **2 sabi** | — | Usually the same lineup as 1 sabi; **weave counter-melody into the gaps in the vocal** to deepen memorability |
| **Interlude** | **Deliberate nonchalance** | Keep the lingering resonance of the sabi and let the ear rest; at the same time add instruments one by one and lay down modulating chords, running up to the next section |
| **C / D-melo** | **Unexpected development** | ★ **Chord progressions matter most**: create a world that has not appeared before |
| **3 sabi 1** (ō-sabi position) | Peak of climax | May modulate; strings soar higher than in the earlier sabi, choir thicker |
| **3 sabi 2** | — | Push to the summit with greater string dynamics |
| **Outro** | **Lingering beautifully** | Not too long; fade out? Or leave only piano? **Work on leaving an impression** |

---

## 3. ★ Complementary dynamics between singer and arrangement

**This point is often overlooked, but it decides whether a song sounds "stacked" or "breathes":**

| Singer | Arrangement |
|---|---|
| **Little dynamic variation** (flat delivery) | **An arrangement with plenty of dynamic variation** (many notes, but also leaving ample space) to make up the dynamics, so listeners can still comfortably "follow the vocal with their ears" |
| **Rich dynamic variation** (strong expressiveness) | **An arrangement with little dynamic variation**, pushing the vocal to the front (for example, just one acoustic guitar as accompaniment) |

> ★ **Pushing both forward in sync is the mainstream of pop, but when done too conventionally it loses freshness and falls into a cutthroat contest over "who plays flashier". Deliberate "offset complementarity" is a differentiation strategy.**

**Interface with this library**: this must be decided together with the section-by-section delivery in `mc-vocal-direction` §1 ② and the energy curve in `mc-arrangement-arch` §2.
Maxing out both singer dynamics and arrangement dynamics at once is exactly the default behavior of generative models.

---

## 4. Classical form catalogue (Wu Zuqiang)

Switch to this system when pop terms are not enough. **Do not mix the two systems.**

### 4.1 Period: a finer scale than "section" (Chapter 3, from p0082)

**This chapter is the most practical part of the whole book**: it gives a finer scale than "section".

| Topic | Page |
|---|---|
| Periods and their components (overview) | — |
| **Principles for dividing periods, phrases, sub-phrases and motifs** | — |
| Dividing phrases: analysis of period examples | — |
| Period examples with **a one-phrase structure** | — |
| Periods with **a two-phrase structure** | — |
| Periods with **three or more phrases** | — |
| **Compound period** | — |
| ★ **Open period** | — |
| Classification of periods and their characteristics | p0082 |
| **Typical structure of periods** | p0083 |
| Synthesis and decomposition of period structure | p0091 |
| ★ **Introductions and supplements before and after periods** | p0092 |
| Repetition of periods | p0092 |
| ★ **Periods functioning as independent forms vs periods as part of a larger form: differing characteristics** | p0093 |

**Three points especially useful for this library**:

1. **Open period** (ending on a non-tonic chord) —
   directly corresponds to **cadence openness levels 5–8** in `mc-melody` reference §5.
   The two books describe the same thing from different directions.
2. **Introductions and supplements before and after a period** —
   ★ This explains "why this section is 17 bars rather than 16": **that bar is a supplement outside the structure, not part of the section**.
   This is different from the asymmetric design in `mc-arrangement-arch` §4: **one is an addition outside the structure, the other is a break within it.**
3. **Period as independent form vs period as part of a form** —
   the basis for judging "is this one section or a whole piece". Needed when doing section-by-section breakdown in `mc-case-studies`.

### 4.2 Sonata form: the parts that can be carried over into pop songs (Chapter 9, p0266–0292)

Simple binary, simple ternary, compound ternary, rondo, variation and suite chapters should be looked up in the book's table of contents; only sonata form is covered here, because it is a model of "two themes clashing and then reconciling", and the relationship between verse and chorus, or between section A and section B, in pop songs can be modeled on it.

**Thematic relationships** (p0266–0268): the contrasting themes in compound ternary and rondo are **juxtaposed**; in sonata form the contrasting theme has an **internal connection**, directly generating conflict and tending toward unity. Three natures: mutually complementary, mutually contradictory, or both. The subordinate section is often **derived** from the main section.
**Tonality**: the main section is in the home key and the subordinate section is in a subordinate key; in major-key works the subordinate section is most typically in the dominant, while in minor-key works it often uses the parallel major (p0267).

**Continuous development** (p0268–0269): six stations for the main theme: preparation in the introduction, initial statement in the exposition, fragments appearing in the "turn" of the subordinate section and in the closing section, full exploitation in the development section, a new stage in the recapitulation, and as closing material in the coda. **Continuous development of the theme is crucial to forming the climax of the whole piece.** In pop songs, the equivalent is the hook's motif appearing once each in the verse, pre-chorus and bridge.

| Part | Method | Page |
|---|---|---|
| **Exposition** | Main section, transition, subordinate section, closing; the main contrast lies between the main and subordinate sections, while the transition, bearing the burden of linking, has little contrast | p0270 |
| **Transition** | Two types: one with independent structure, or one attached within the main section (the post-phrase of the main section, or the recapitulation in a simple ternary main section). A typical three-part shape: beginning (end of the main section), basic part (development of a not-very-contrasting new tune, modulation), preparatory phrase (stopping on the dominant chord of the subordinate section); not every transition has all three parts. The most typical tonal approach is **a dominant chord of the subordinate section appearing after a modulation** | p0275–0277 |
| **Subordinate section** | Usually a single lyrical theme of song-like character; ★ when the subordinate section is quiet and lacks internal contrast, classical composers **introduce a "turn" in its second half**, using active material to create a sudden contrast, often leading to an expansion of the subordinate section; the subordinate section typically closes with a full cadence in its home key, or may be left open to proceed directly into the development. After the Romantic era, the subordinate section changed to a new tempo to emphasize contrast | p0277–0279 |
| **Closing section** | Rounds off the exposition and gives a preliminary summary; uses the tonality at the close of the subordinate section. Typically the tonic cadence at the end of the subordinate section is repeated as an expanded large cadence, often with a sustained tonic pedal. The structure is a period plus supplement, or simply a combination of several supplements | p0279–0280 |
| **Development section** | The hardest part to generalize, in three aspects. **Material**: not quoted verbatim, with theme fragmentation as the main technique; often begins with main-section material in another key or with closing-section material; main-section material is most often used because it is active; polyphonic texture or even fugal passages are common; new derived themes may be introduced. **Tonality**: unstable for long stretches, with the home key almost never appearing; starts from closely related or mediant-related keys; the second half often uses the subdominant area, contrasting with the tonic–dominant emphasis of the exposition; rarely reaches a full cadence; the ending returns to the tonic's dominant chord as a "dominant preparation passage" or "dominant pedal preparation passage". **Structure**: the introductory part is very short or absent, the basic part forms the overall climax, and it leads to a recapitulation preparation passage; false recapitulations may occur; episodes are rare | p0280–0287 |
| **Recapitulation** | **Always a varied recapitulation**: the smallest change is the subordinate section returning to the home key, the closing section following suit, and the transition restructured accordingly; when the musical idea develops dramatically it becomes a dynamic recapitulation, with changes in structure, tonal layout and thematic character, not just in dynamics, texture or orchestration | p0287–0288 |
| **Introduction** | Material may contrast with the theme or be derived from it; the structure may be complete and independent or just a few bars of preparation; it must prepare the entry of the main section, often leading from a subordinate key to the dominant chord of the home key as a "dominant preparation passage", so the introduction often does not close; an independently meaningful introduction can run through the whole piece as a dominant motif | p0290–0291 |
| **Coda** | Synthesis and conclusion: often recapitulates or develops earlier thematic material, may use all the themes or emphasize just one; new themes are rare; requires a full cadence in the home key; with a substantial development, it tends toward the subdominant area; may begin after a full cadence or after an interrupted cadence; sometimes the structure resembles the development section, cross-echoing it to achieve balance | p0291–0292 |

**Four points that can be applied directly to pop songs**:
1. The subordinate section's "turn" is the reason the second half of a chorus needs a moment where it lifts up (p0278).
2. The closing section "repeating the cadence as a large cadence" is the classical basis for an outro that repeats the hook's final phrase (p0280).
3. The development section's second half moving to the subdominant, and the coda also tending toward the subdominant, is the basis for a bridge moving toward the subdominant; returning requires a dominant preparation passage (p0284–0285, p0292).
4. The recapitulation is always a varied recapitulation (p0288): the final round of the chorus must have at least one difference. This is the same principle as the final-section variation in `mc-arrangement-arch`.

### 4.3 Sources for other forms

| Source |
|---|
| Collection of form score examples |
| On Musical Form |
| Yang Ruhuai, *Analysis and Creation of Music*, vol. 2 |
| Yang Ruhuai, vol. 1 |
| **Li Jiti, *Musical Forms and Work Analysis*** (a Western form textbook, sixteen lectures; observations on the structure of Chinese music are scattered across the lectures) |

---

## 5. Principles of Chinese music structure

> The base text is Li Jiti's *Musical Forms and Work Analysis*, with its scattered observations on the structure of Chinese music. **It is a Western form textbook, and it does not cover the layer of banjiang-ti and qupai-ti** (*banqiang* and *qupai* structures).
> The structural rules of banjiang-ti and qupai-ti are not covered by this package.

### 5.1 ★★ Process, not return

"Chinese people regard music as a process: when the music enters a new starting point, it can be developed at a new height, and there is no need to stress recapitulation or return to the tonic" (p0071–0072).
Qu Wei's *Huagu* (Flower Drum) has only a thematic-synthesis recapitulation and a tempo recapitulation, with no tonal recapitulation; its tonal layout is in fact binary.
**When writing in a Chinese style, "the final section must return to the home key" is not a rule**; the return of material and tempo is enough.

### 5.2 ★★ The basis for dividing sections has changed

"In folk music or mass songs, **contrasts and recapitulations of thematic material, tempo, *banshi* (metric pattern) or genre may become more important markers for dividing sections of form**,
and Western classical form theory should not be applied to them simply" (p0072). For single-ternary structures in Chinese pieces, "harmonic change or modulation may not be emphasized, while more attention is paid to changes of thematic material, tempo and genre, and to shifts of mode" (p0065).
**Contrast between sections in a Chinese style relies on material, tempo, genre and mode, not on harmony.** This is the same thing as the *tonggong fan diao* ("same palace, offending modulation") in `mc-melody` reference §3.0: change the color, not the key.

### 5.3 How material grows: elaboration and *qi-cheng-zhuan-he*

- **Elaboration** (*zhanyan*): progressively renewing material from a single musical phrase (for example *Erquan Yingyue*, Moon Reflected in the Second Spring), "especially common in traditional Chinese music" (p0016, p0020). It is the developmental logic of material in Chinese music, standing alongside the recapitulation principle rather than beneath it.
- The four-line structure of *qi-cheng-zhuan-he* "has more universal significance in traditional Chinese music" (p0022, p0035); the process of presenting a musical idea (statement → consolidation → developing contrast → summary and closure) itself matches *qi-cheng-zhuan-he*.
- **Paired couplets** (*ju ju shuang*) (p0035, p0153): two lines, each repeated once to make four lines, found in both Chinese and foreign folk music, with very low cost in terms of avoiding monotony.
- **Closing-tail form** (*he wei shi*) (p0032): the response at the end of the phrase is missing but the **contrast at the beginning of the phrase** still forms a section. `mc-melody` §7.3 assumes the response at the end of the phrase by default; this is the other route, at the head of the phrase.
- **Stacked phrases** (*duo ju*) drive the development of musical ideas, forming developmental contrasting phrases (*Caidiao*, Guessing Tune, p0031).

### 5.4 How tripartite form arises in folk music

Folk musicians play the same short tune by moving it between keys on different instruments, forming a layout of "home key – contrasting key – home key" (p0077). **When a Chinese-style piece needs tripartite form but should not feel forced, change the instrument and the palace, not the material.**
This route is theoretically limited to **single-theme** structures: what changes is key and instrumental timbre, and the theme itself never presents a second contrasting theme. Once that happens, it is no longer this type (p0077).
Chopin's Mazurka Op. 33 No. 2, first section, is a comparable Western example: section A in D major, section A1 shifted down a fourth to A major, and section A recapitulated back in D major. The material is completely unchanged; only the key moves (p0078). Viewed another way, this can also count as a fixed-melody variation in the form of "the same melody presented in a changed key" (p0078). The Chinese route of changing instrument and palace and the Western route of repeating in a changed key differ in cost: the former relies on timbral difference for contrast and leaves material and tempo untouched; the latter leaves the material unchanged but truly shifts the tonality. For a Chinese-style piece seeking a "sense of process" (see §5.1), the former is more suitable.

---

## 6. Expansion, reduction and truncation of musical ideas (Yang Ruhuai, p0131–0138)

The full text on the three types of expansion, the three methods of reduction, and truncation has been merged into `mc-development` reference §2 (criteria and usage are in its SKILL §3.3–3.5). This section keeps only this pointer.

## 7. Parts not in this file, covered elsewhere

| Content | Where it goes |
|---|---|
| Hooks and attention-grabbing techniques (originally §V) | `mc-arrangement-arch` §7 |
| Climax and ending (originally §VI) | `mc-arrangement-arch` §2 and §8 |
| Lineup approaches for intro / interlude / outro / vamp (originally §VII) | This file §2 plus `mc-arrangement-arch` |
| Anti-predictability checklist (originally §VIII) | `mc-melody` §8 |
| Sabi design and maximization (originally §IV) | `mc-arrangement-arch` §2 plus this file §1 |
| Workflow (originally §IX) | `mc-workflow` |
