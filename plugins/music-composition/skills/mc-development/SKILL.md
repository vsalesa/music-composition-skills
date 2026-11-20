---
name: mc-development
description: Thematic development layer - what the theme is and what each section does with it. Owns `material` (motif, character, stated_in) and `form[].development`, a closed set of ten operations (repeat/sequence/extend/contract/fragment/vary/augment/counterpoint/new/recap). Covers the line between developing and piling up, each operation with its criterion and cost, motive-to-phrase construction, phrase-to-section-to-whole (overlap, supplement, recapitulation), the variation branch, and where it all lands in a pop song. Use when every section sounds like new material, when a song feels loose, when deciding what the second verse or the last chorus should do, or when filling `material` and `form[].development` in an ARR-SPEC. Keywords: thematic development, motif, thematic material, every section writing new material, expansion, contraction, fragmentation, sequence, variation, recapitulation.
---

# Thematic Development Layer

> **A song = one body of thematic material + one job each section does with it.**
> This skill covers only the second part: **what this section does with the material that came before.**

How the melody itself is written belongs to `mc-melody`; how sections are arranged and how long they are belongs to `mc-form` and `mc-arrangement-arch`.
This skill owns `material` and `form[].development` in the spec sheet.
They answer the question the spec sheet could not answer before: **where this section's material comes from.**

## Which sections to read by task

| Symptom / task | Read |
|---|---|
| Form just settled, need to fill material and development | §1 → §3 |
| Every section sounds like a new song, feels scattered | ★ §2 + §5.1 |
| A motif does not know how to grow further | §4 |
| Halfway through a section and want to lengthen it | §3.3 + §3.2 |
| Second verse copies the first | §7.1 |
| Pre-chorus will not build | §7.2 + §3.5 |
| Bridge has turned into another song | §7.3 + §3.9 |
| How should the final chorus change | §7.4 + §3.10 |
| Choruses advance through variation on each pass | §6 |
| Sections join awkwardly | §5.3, §5.4 |

## Boundary: what this skill does not cover

| Not covered here | Covered by |
|---|---|
| How the melodic line itself moves, singability, leaps and range | `mc-melody` |
| The causes of motive → phrase segmentation, answering, climax placement | `mc-melody` §7 |
| The five modes of statement, six structural functions, five forms of recapitulation, sonata form | `mc-form` §6.1–6.2, reference §4.2 |
| Form templates, how long a section should be, energy curves | `mc-form` / `mc-arrangement-arch` |
| How to choose chords, how to configure progressions, modulation | `mc-harmony` / `mc-progressions` / `mc-modulation` |
| The nature of the five types of counterpoint, imitation, canon, fugue | `mc-counterpoint` §7 and reference §7 |
| The repetition budget on the lyric side and the final-section micro-variation | **Lyric writing**; the corpus figures used in this skill are in §2.2 and §7.4 |

> ★ Boundary with `mc-form`: **form governs what this section is (its name and function); this skill governs what this section does with old material.**
> The same section can be a Chorus, a closing statement, and the driving shape of a `recap` at once; the three labels do not substitute for one another.

---

## 1. Required before starting

**If the three `material` items cannot all be filled, do not proceed to fill `form[].development`.**

| Required | The question | Criterion |
|---|---|---|
| **① What is the motif** | Written out explicitly: interval contour, rhythmic pattern, length | Schoenberg: the characteristic shape of a motif is **interval and rhythm**, combined into one memorable contour (p0025). If you cannot write down these two things, you do not yet have a motif |
| **② One line of character** | What temperament does this motif have | Li Jiti: rhythmic patterns take on character according to accent placement; a trochaic (falling) pattern suits descent, an iambic (rising) pattern is rich in drive, a spondaic (both-stressed) pattern is firm, and a pyrrhic (both-unstressed) pattern is gentle (p0016–0017) |
| **③ In which sections the original statement appears** | Section ids; may be several | Yang Ruhuai: the original statement is the root of all subsequent development; a new musical idea that appears midway and becomes the root of later development also counts (p0110) |
| **④ What drives the song forward** | Elaboration / development / contrast; choose one dominant | Li Jiti's three methods of development (p0020), see §5.1 |

**What counts as enough writing for a motif**: an important musical idea must have a distinctive tonal character, that is, an **organic combination** of rhythm, mode, and melodic progression features (Yang p0110).
Li Jiti sets a stricter gate: a musical figure qualifies as a motif only if it has the value of being independently elaborable, so that music can take root and grow from it (p0016–0018);
another theoretical system equates motif with musical figure. The two views coexist, so before starting, specify which definition you are using.

★ **Where the motif goes**: an important musical idea should be stated at a key point in the piece; without an introduction, at the beginning; with an introduction, at the start of the main formal section, and it may also be foreshadowed in embryonic form in the introduction (Yang p0110).

★ **A motif suited to development is simple**: if a theme already contains too many interesting characteristic figures, there is no room left to add content for variation to work with (Schoenberg p0229–0230);
melody, harmony, tempo, dynamics, texture, and register should ideally all sit in a middle state (Li p0165).

---

## 2. ★ The boundary between development and piling up

> **There is only one criterion: can the listener recognize that it comes from what came before?**
> Expansion, sequence, fragmentation, variation, counterpoint, and recapitulation all satisfy this; a brand-new melody does not.

### 2.1 The two baselines for recognizability

**Schoenberg's standard** (p0025): applying a motif calls for variation, since mere repetition is monotonous; but if every characteristic figure is varied, the result is incoherent and fragmented, and the basic shape of the motif is destroyed. The correct approach is to **vary the secondary characteristic figures and keep a few of the more important ones, especially the rhythmic characteristic figures**, which are most effective for coherence.

**Baseline for derivation** (p0038–0039): distantly related motif forms (changing rhythm and also interval and direction at the same time) may hinder comprehension; each new motif derived **must still have the quality of a "true short phrase,"** otherwise what results is fragments. The more distant the relation, the more it must rely on rhythm, auxiliary tones, and other cues to remain recognizable;
**the faster the tempo, the less diversification the work can bear** (p0040).

### 2.2 The budget for new material

Yang Ruhuai gives the heaviest warning on introducing new material (p0122): introducing new material has a wider scope of application than any other technique, and **it is also the most easily abused**;
one must not assume that any unrelated new material may be used for novelty. Li Jiti explains the same thing from the side of form (p0025): juxtaposed combination renews music through contrast between sections, but its limitation is that too many juxtaposed sections create a "centrifugal force" that weakens the structural force of the whole. If every section is new material, the whole song is handed over to centrifugal force.

- The three warnings are in §9; the most important is that **the number of sections labelled `new` should not exceed half.**
- The lyric side has empirical reference figures to align with (Chinese-language lyric corpus: songs by the top 100 singers on singer charts, 3,631 non-rap songs counted by section labels): choruses make up between a quarter and seven-tenths of the song, with a median close to half, and 27% of songs have every chorus pass identical word for word.
  **Give whole choruses over to repetition, and verses have room to move the story forward.** On the music side, `recap` and `repeat` must take up a considerable share of space.
- Section proportions are covered in `mc-arrangement-arch` §4.

### 2.3 The criterion is not an iron law

After presenting the full set of developmental forms, Yang Ruhuai makes a specific reminder (p0127): the various developmental forms **can transform into one another and have many intermediate forms**, and
"under any circumstances, dogmatic, mechanical analysis will harm the actual practice of musical art." So `development` takes one primary value plus several secondary values, and a section may simultaneously be an extension and a sequence. Anything that cannot be fitted into the ten values is assigned to the nearest one, with a sentence in `note`; do not invent new names.

---

## 3. The ten techniques: what they are, when to use them, what they cost

The values of `form[].development` are these ten. **Each section takes one primary value, with optional secondary values, the primary written first.**
The definition, criterion, cost, and page reference for each are compiled into a comparison table in [reference.md](reference.md) §1; this section gives only the points needed when starting to write.

### 3.1 `repeat` Repetition (verbatim, or with the head or tail changed)

Highlights the repeated musical idea and deepens the impression; **the shorter and more essential the idea, the more it needs repeating** (Yang p0111).

- **Cost**: mechanical repetition provides unity but no contrast; the number of repetitions is usually no more than two, and three or more in succession becomes a weakness. It ceases to be "mere" only when accompanied by crescendo, acceleration, or a shift in register; short but crucial motives and sustained bass lines are exceptions and may repeat many times. Musical ideas are often repeated in pairs, and even-numbered repetitions are the most clearly perceived (p0111–0112).
- **Head and tail changes**: joining or swapping does not split the development into another section, but connects it with what comes before and after into a single continuous long idea. The criterion is elegant:
  **"joining" sets off the fit because there is novelty, and "swapping" sets off the replacement because there is identical repetition** (p0128).

### 3.2 `sequence` Sequence

A musical idea is repeated at a new interval degree, or simultaneously in a new tonality; it is "unity within change" (Yang p0115).

- **Carries momentum**: ascending sequences raise the sound, descending ones weaken it; combined with compression or fragmentation, the momentum is more pronounced (p0115–0116).
- ★ **Using it at the wrong stage becomes formula**: it is most suitable where the melody is to develop further (the continuation, the transitional turn toward the next stage, the build-up before a climax), and **it should not be used at the initial statement stage, especially not for modulating sequences** (p0116).
- **Avoiding stereotype**: alter one link locally (scale degree, melodic line, interval, textural detail); **the final link is often adjusted so that it can receive the music that follows**; sequences in pentatonic material cannot be strictly on the same scale degree, and consistency of direction counts as strict (p0116). One point Schoenberg sets alongside this (p0092): sequences on the natural scale have clear tonality but limited room for development, and substitute notes allow modulation.

### 3.3 `extend` Extension

When a statement is repeated, the idea is stretched **from within**; the stretched portion joins organically with the original idea, and there is no sense of cadence between them or the join is deliberately concealed (Yang p0131).

- ★ **The criterion that separates it from repetition**: regardless of where the extension begins or how large it is, **it generally does not return to the original closing material**; swapping the head and tail generally does not change the total length of the idea, whereas internal extension does (p0131–0132).
- **Three types side by side**, the first two most used: internal extension before the cadential formula; extension after an obstructed resolution on the cadence; and compact extension after the cadence (p0131–0133).
- **Judging direction**: among internal extensions, distinguish whether it brings the growth of new qualities or the expenditure of emotion, separating the developing nature from the concluding nature (p0132);
  an extension can also change function and become preparation for the next new idea, in which case the harmony is open, halting on the dominant or modulating (p0134).
- **Cost**: an internal extension is sometimes hard to recognize if not compared with the original statement (p0133).

### 3.4 `contract` Contraction

On repetition, the structure is shortened compared with the original statement (Yang p0136).

- **Character**: gathering in, often expressed as a brief recollection, summary restatement, or supplement; **it does not bring emotional rise**, and is mostly used at endings or near the close.
- **Three methods**: omit the middle tones and keep only the beginning and end; omit evenly and dispersedly to control fluctuation; contract with modulation (turning back to the original key while compressing a long statement back to normal size).
  Compared with extension it is used less and is simpler in method (p0136). **If you want to create a rise at the ending, this technique cannot provide it.**

### 3.5 `fragment` Fragmentation

Isolates the fragments that make up the musical idea, and uses them separately, either as they are or after treatment (Yang p0137).

- ★ **The typical process is continuous, repeated, and drawn from different positions**: a fragment that has been cut off is cut again, **shorter and shorter, with development becoming ever more compact** (p0137).
- **Uses**: to push emotion toward a climax, to create increasingly lively or tense atmosphere, while producing great unity and multiple layers; the material can serve as a principal voice or as background accompaniment, and orchestration can thicken it to build intensity (p0137–0139).
- **Cost**: cutting shorter also strips out melodic quality at the same time. The extreme form is when the residue of the motif is cut down to pure rhythmic specks (Schoenberg p0280),
  and at that point the section has no singable line.

### 3.6 `vary` Variation

Retains the overall contour of the original statement, the general layout of the melodic movement, and the structural scale, **bringing a new appearance while still letting the listener recognize the unified relation to the prototype** (Yang p0114).
Two directions: making the idea more flowing (adding ornamentation) or more formed (simplifying), without departing from its basic character; or retaining the overall contour and structural proportions while achieving another character through technique, that is, **character variation**, which must identify the rhythmic patterns, figurations, and tempo peculiar to the genre, **rhythmic patterns being especially important** (p0114–0115).

- **Boundary with iteration** (p0113–0114): iteration keeps the overall melodic appearance on each repetition and changes only local melodic figuration, so each pass can differ; variation unfolds across the whole process and emphasizes the **overall unity** of the means of change.
- **Schoenberg's four categories of variation method** (changing rhythm / changing interval / changing harmony / adapting the melody, p0030–0031) form the most detailed checklist; the full table is in [reference.md](reference.md) §3, and the seven harmonic variations are at the end of the same section. The baseline sentence (p0028):
  **the motif forms produced should not stray too far from the basic motif.**

### 3.7 `augment` Augmentation and Diminution

Within the same or similar meter and tempo, the musical idea is stated in proportion slowed or accelerated by a factor of two or three (Yang p0116–0117).

- ★ **The criterion is a multiple of relative note values**, not a change of how the score is written, nor a matter of how fast the performance is played: if the notation appears to slow things by half but the actual unit beat value has not truly doubled, it does not count as augmentation (p0117).
- **Augmentation**: solemn, majestic, stable, and weighty; used at an ending, it lets the mood gradually settle into calm and the tempo slow. **Only part of the musical idea may be augmented** (p0117).
- **Diminution**: note values are shortened, producing more motion and stronger forward drive; **continuous diminution** can accumulate great tension and readily push emotion toward a climax or introduce a new musical idea; there is also **temporal diminution**, which merely compresses musical ideas that were originally separated (p0118). Diminished shapes can also serve directly as a fixed accompaniment figure (p0119).

### 3.8 `counterpoint` Contrapuntal Development

One voice imitates the original statement at a given pitch using an **augmented or diminished form** of the musical idea; this is a widely used technique in polyphonic development and voice imitation (Yang p0118–0119).
**This skill owns only the determination that "this section is contrapuntal development"**; the substance of imitation, canon, fugal sections, and consequent sections is in `mc-counterpoint` §7 and reference §7. **Cost**: every layer must be audible; if register and depth are not arranged well, the two lines blur into one.

### 3.9 `new` New Material

During development, no fixed tonal and melodic contour of the original musical idea is maintained, and no connection exists through the techniques described above; a new musical idea appears (Yang p0122).
**Filling in this value amounts to declaring that "this section does not rely on old material," so it is the only one of the ten values that is counted (§9).**

Yang Ruhuai classifies it by nature into three types, from "still connected" to "completely severed": **inherited novelty** (new in many respects, yet still consistent in many ways in the scope of rhythmic activity, the extent of melodic development, tempo, style, mode and tonality, and character); **synthetic novelty** (what links before and after is only the same meter, tempo, tonality, and expressive dynamics, and **contrast of thematic material dominates**); **opposing novelty** (creates a blocking relationship between before and after, yet still logical from the dramatic development of the overall conception, graded into intense and mild levels, of which **intrusive opposition** suddenly bursts in before the musical idea has finished, starting a new formal section at the same time).
A detailed table of criteria and uses is at the end of [reference.md](reference.md) §1 (p0123–0126).

**Li Jiti's dichotomy, set alongside** (p0020–0021): derivative contrast (with an internal connection to the original idea) **creates contrast while preserving the kinship and unity of the material**; juxtaposed contrast (with no internal connection between materials) **gives stronger contrast but must separately solve the unity of the whole piece**. When writing `new`, first ask yourself which kind this is; if you cannot answer, you have not yet decided. Schoenberg's interpolated sections (p0224) give guidance on length: they create tension through a sense of suspension, at the cost of breaking continuity, so their length is usually restrained.

### 3.10 `recap` Recapitulation

After a new, contrasting statement, a previously stated musical idea reappears, embodying the three stages of "original statement, contrast, and original statement once more"; its function is to make the idea that first appeared stand out, serving as a unifying summary of structure and thematic material (Yang p0112).

- ★ **When filling in `recap`, state whether it is verbatim or dynamic**: a static (original-form) recapitulation makes no essential change beyond texture, orchestration, and dynamics, whereas a varied recapitulation makes essential changes to its structure and content (p0112–0113); a **dynamic recapitulation** is one in which the development of the middle section permeates the recapitulation section (Li Jiti p0023–0024; the complete table of five forms is in `mc-form` §6.2).
- ★ An observation of Yang Ruhuai's that is easily overlooked (p0112–0113): **a recapitulation that is small in scale and not separated by intervals has a more pronounced effect on the unity of the material**. Small-scale recapitulations between passes of a chorus belong to this category.
- **How much change is too much** (Schoenberg p0188): variation may be applied to all the elements of the recapitulation, but **unless the structure undergoes a substantial change, the melodic contour should not be altered entirely**; decorative variation does not necessarily change the contour in substance, but **too many rhythmic changes or accent shifts will likely make the original appearance unrecognizable**.

---

## 4. From motif to phrase

### 4.1 The yardstick: two systems side by side

| | Schoenberg (p0006) | Li Jiti (p0016–0019) |
|---|---|---|
| Smallest | Motive (motif) | Melodic figure (a group of tones built around one accent) |
| ↓ | Unit, element | Motif (a melodic figure that can be independently elaborated) |
| ↓ | **Short phrase (phrase)** | Melodic segment (2 figures, 2–4 bars, requiring only a melodic pause) |
| ↓ | Antecedent / consequent phrases | Phrase (2 segments, 4–8 bars, **requires a cadence**) |
| ↓ | Fragment, section, part | Passage → theme (can be as large as a simple binary or simple ternary form) |

**The criterion separating a segment from a phrase is "whether it cadences," not length** (Li p0018). Both sources emphasize that length is determined by tempo: at a medium-moderate tempo a phrase is often 4 bars, and long phrases built from repeated sequences of a motif can reach several dozen bars (Li p0018–0019); at a very slow tempo a short phrase can shrink to half a bar, and at a very fast tempo it takes eight or more bars to form one, nearly always crossing bar lines (Schoenberg p0019). ★ Some phrases are carried through in a single breath, so that no figure or segment can be marked off; the phrase itself is then the most basic unit (Li p0019).

### 4.2 How a motif can be treated

Schoenberg divides this into three categories (p0026): **exact repetition, varied repetition (variation), and developing repetition**. Exact repetition retains all characteristic figures and the relations among pitches, so **transposition to another scale degree, inversion, retrograde, retrograde inversion, diminution, and augmentation all count as exact repetition**; the judgment rests only on whether the relations are strictly preserved, not on surface similarity.
Operations that sound very different to the ear are grouped here in one category, a point that is often misread. The complete table of the four categories of variation method is in [reference.md](reference.md) §3.

### 4.3 How motif forms combine

**Whether they can combine logically depends on three factors** (p0036): common content (derived from the same basic motif), similar rhythm (which serves a unifying function), and coherent harmony (which strengthens the relation). If any of the three is missing, the logic weakens. A companion point:

- **The beginning determines what follows** (p0041): the theme must clearly present the basic motif in its opening fragment; if the opening is a two-bar short phrase, bars three and four may be an unchanged or displaced repetition, with minor alterations allowed, **but the repetition must remain recognizable as such**.
  The relation of "principal form and dominant form," in which the first short phrase uses tonic harmony and the second uses dominant harmony, resembles the subject and answer of a fugue (p0041–0045); the comparison table of harmonic layouts is in [reference.md](reference.md) §5.

### 4.4 How a phrase is brought to rest: liquidation

**Liquidation is defined as "gradually removing the characteristic features until only non-characteristic features remain,"** the aim being to counteract the tendency toward unlimited extension; the residue left behind often has nothing in common with the basic motif, and is mostly combined with a cadential formula to mark the boundary (Schoenberg p0091).
★ **The cost is paid deliberately**: the recognizability of the motif is sacrificed; this is the cost needed to achieve the aim, not an error.
This is the only permitted exception to the "recognizable" criterion of §2, and it is permitted only in closing positions.

★ **For Schoenberg, the word development runs in both directions** (p0091): it refers both to growth, expansion, extension, and enlargement, and to cutting down, condensing, and intensifying. This is the reason this skill lists `extend` and `contract` as two separate values. The model for this is **developing variation** (p0095): all the motif forms and short phrases of a melody are gradually developed from the opening three notes, or even the opening two notes; the `material.motif` field exists precisely to force this source to be identified.

---

## 5. From phrase to section to whole piece

### 5.1 The functional chain and three paths of advance

**Yang Ruhuai's three logics of movement, set side by side** (p0093): four stages (opening, development, turn, closing), three stages (opening, opposition, closing), and two stages (call and response).
★ Stage divisions are relative, and each stage may be subdivided further, so the whole-piece level, the section level, and the phrase level each have their own opening-development-turn-closing and need not align.

**Li Jiti's three methods of development** (p0020) form a multiple-choice question for item ④ of `material`:

| Method | What it does | Mapped to `development` |
|---|---|---|
| **Processing** | Repetition, varied repetition, variation, sequence, expanding or contracting intervals or rhythm; characterized by "dismembering" processing of the original structure | `repeat` `sequence` `vary` `augment` `extend` `contract` `fragment` |
| **Unfolding** | A method of statement that **gradually renews the material**, starting from the original musical idea; especially common in traditional Chinese music | Primary `vary` or `extend`, secondary `new` |
| **Contrast** | Replacing the musical idea, divided into derivative and juxtaposed types | `new` |

**Yang Ruhuai's three-level progression** (p0120–0126) is a yardstick measuring "how far from the original musical idea"; in this scheme, unfolding is called evolution:

- **Retrograde-type development**: keeps the rhythmic pattern unchanged and alters only the direction or interval of melodic movement. ★ The difference from sequence: retrograde-type unity relies mainly on "rhythmic sameness," whereas sequence relies on the regularity of interval relations; so **for a sense of "call and response," use the retrograde type; for a sense of "forward motion," use sequence** (p0120–0121).
- **Evolutionary development**: keeps the core tonality and the broad melodic contour while altering rhythmic pattern, intervals, or structure (also possibly local augmentation or diminution, extension or contraction, modulation).
  ★ **The degree of unfolding is greater, and without detailed analysis it can sometimes be mistaken for a contrasting new musical idea** (p0121).
- **Novelty**: see §3.9. ★ The three kinds of novelty may coexist at different developmental stages of one long melody, linked to one another (p0126).

### 5.2 Threading: what holds the whole piece together

- **Joined ending** (p0129–0130): all themes end with the same melodic fragment in the same key, unifying the whole piece in both content and thematic material;
  ★ even if the middle section is a contrasting section formed by inherited novelty, a joined ending can still unify it with the other sections.
  Companion device: **swapped-tail cadential answer** (p0129): when a swapped-tail repetition changes the closing tone to the principal functional tone of the mode, the two statements, before and after, form a continuous antecedent-consequent relation.
- **Head-to-tail linking (chain linking)** (p0130–0131): after a preceding musical idea ends on a clear cadential formula, the next idea begins by repeating that same closing passage as its own opening.
  Another form is that during repeated statements the beginning and end are consistent while a variation in the manner of iteration occurs in the middle. ★ **A longer iterative variation right in the middle is often precisely the opportunity for a climax to form on restatement (or to surpass the first climax point)**.
- **Motivic threading** (p0139): what distinguishes it from ordinary fragmentation is that every fragmentary form retains the core elements of the motif.

### 5.3 Overlap: no seam between sections

**Overlap**: in the successive statement of one musical idea followed by another, the division between them is dissolved and they are joined compactly, while the existence of a boundary between them and the occurrence of a transformation remain clearly perceptible (Yang p0139). Four types side by side: overlap on a regular downbeat (a shared bar); syncopated overlap; overlap of introduction and theme; and overlap of accompaniment background.

★ The fourth type is the most useful in popular arrangements: the accompanying figure or sustained harmonic background of the new theme overlaps the ending of the preceding section, and the new theme does not truly enter until it has sounded for a moment; the effect is to build atmosphere and delay the entry of the theme to create freshness, **and because the theme appears late, the listener pays more attention to its entry** (p0140–0141).
★ There is also **dramatic intrusion** (p0141): new material begins without conforming to the tonic harmony of the preceding cadence; harmonically it resembles blocking the cadence, and materially it resembles extension, but it has its own independent developmental thread.

### 5.4 Supplement: a further remark after the close

**Supplement**: after a musical idea or theme ends with a perfect or half cadence, a closing passage follows that is consistent in content and mood with what came before, whose stated material is conclusive, whose tonality is clear, and which likewise lands on the original key (Yang p0141).

★ **The criterion distinguishing it from extension** (p0142): an extension, before a cadential formula appears, deliberately conceals the sense of having come to a close and expands the idea from within, manifesting as internal organic growth; a supplement must come separately **after** a perfect or half cadence and manifests as an external addition or auxiliary statement.
(Compact extension is a grey area: it also occurs after the cadence, but a typical supplement lacks the emphasized condition of compact rhythm that it has; p0133.)

Three usage situations side by side (p0142): consolidating a hurried cadence; wearing down emotion and sonority so that the image gradually recedes; maintaining or intensifying the climax and brightness at the close.

★ **The transformative function of a supplement** (p0143–0144): at a point where the musical image is about to change, the supplement can alter its nature during the process, turning it into "continued development" and preventing the cadence from arriving; at this point the supplement's function converts into a connecting transition. This is the mechanism by which an outro is reworked into a bridge.
Schoenberg sets three concepts side by side: extension, interpolated section, and small coda (p0224–0225); the internal timeline of a coda involves three things happening simultaneously: **most of the material derives from the preceding theme, the direction of working is restructuring plus liquidation, and the fragments grow shorter one after another** (p0253).

---

## 6. The variation branch

★ Schoenberg makes clear four levels at which the term "variation" operates (p0229): producing motif forms within the construction of a theme, producing contrast in a middle section, producing diversity on repetition, and, in the "theme and variations" form, rising to a structural principle of the entire work.

### 6.1 Two main types (Li Jiti p0159, p0166)

- **Strict variation**: processes the material on the overall premise that the original theme's material and structural contour remain unchanged.
- **Free variation / character variation**: may dismember the original theme's structure and even introduce new material, often leading to a change of musical character. Material is handled in three ways: varying all of the theme's basic material, concentrating development on one particular material, or occasionally inserting new material for contrast, **provided the structure remains predominantly variational for the whole piece**.

The complete table of each type (three types of fixed bass / fixed harmony / fixed melody, classical ornamental variation, and free variation) is in [reference.md](reference.md) §4.
★ **Two judgments that can be carried directly into popular songs**:

1. **Strict first, then free** (p0166): **the opening few variations generally need to begin with strict variation**, so that listeners first memorize the structural framework and tonal characteristics of the original theme;
   once development has reached a certain degree (for instance after entering a climax), a "returning" strict variation may reappear, forming another internal wave of rise and fall.
   Pure free variation at the outset may cause listeners to lose track of the theme, while pure strict variation may lack dramatic rise and fall.
2. **The more factors held fixed, the more conspicuous the one factor that varies** (p0169): *Boléro* locks rhythm, harmony, and tonality entirely; the only variable falls on timbre, orchestration, and the layered crescendo of dynamics.

### 6.2 The baseline for recognizability (Schoenberg p0231–0234)

- The theme should be recognizable in every variation; even if the character changes, **the course of events (the number and order of fragments) should not change**;
  meter and tempo may change, and the number of bars may double in a regular way, but the proportions of the parts, the structural relations, and the main characteristic figures are all retained.
- Unity is achieved through systematic use of a **variation motive**, which is taken from the theme itself; the method of obtaining it is to first omit all secondary components so that the "skeleton" of the basic structure is laid bare (p0232). It **rarely exceeds two bars and in many cases is only half a bar or shorter**;
  ★ **the denser the harmonic motion, the shorter the length over which the motive can be sustained** (p0232–0234).

### 6.3 How to use this branch in popular songs

- **Choruses advance through variation on each pass**: use seven variations that add no new chords to give each pass its face; changing rhythm with the same progression is the weakest grade of contrast, while using different progressions with different starting chords for the two sections is the strongest (end of [reference.md](reference.md) §3).
- **Fixed-melody variation is the solution for strophic songs** (Li p0163–0164): for strophic songs, which have many lyric stanzas and where plain repetition tends to become tiresome, keep the melody unchanged and create different emotional backgrounds through accompaniment and orchestration. **This is the origin of the popular convention "the verse melody stays the same while the arrangement thickens section by section."**
- **The ceiling of classical ornamental variation** (Li p0165–0166): neither the structure nor the basic harmonic skeleton changes, so it rarely leaves the basic affective range delimited by the original theme; it applies when you want to dig deeper into the same emotion, and **do not use it in sections that seek a dramatic breakthrough**.

---

## 7. Where it lands in pop songs

> The defaults in this section (the second verse using `repeat` with a swapped tail, the pre-chorus using `fragment`, and the final section using `recap`) are reasonable defaults derived from classical criteria; **they have not been counted in Chinese-language or Japanese pop corpora**. The lyric side has been measured (Chinese-language lyric corpus; figures in §2.2 and §7.4); the music side is still to be done.

### 7.1 How the second verse advances

**The default is not verbatim repetition.** Three options, ordered from lowest to highest cost:

1. **`repeat` with a swapped tail**: swapping the tail while keeping the head does not change the total length of the musical idea (p0131–0132); this is the lowest cost,
   and it is grounded by the criterion that "a change is set off only by an identical repetition" (p0128).
2. **`vary` iteration**: keeps the overall melodic appearance, making individual note substitutions, rhythmic fill-ins, ornamentation, or simplification.
   ★ In vocal music, changes in the tones of the lyrics naturally lead to iterative variation (p0113–0114), **so this option is almost free for songs in Chinese**.
3. **`contract`**: the second verse is shorter than the first. Conventions for section length are covered in `mc-arrangement-arch` §4.4; this skill is only responsible for making clear that this cut is a contraction, which in character gathers in and does not bring a rise (p0136).

★ **Do not use sequences modulating in the verses** (p0116): verses one and two are both still in the statement stage, and placing a sequence here is the source of the formulaic feel that `mc-melody` §8 describes.

### 7.2 Pre-chorus

Its function is transitional statement: first supplement the preceding idea, then modulate, and finally introduce a new idea or come to rest on an **expectant chord** (Li p0022).
Mapped onto `development`:

- The primary value is usually `fragment`: **to make it "increasingly urgent" relies on fragmentation, not on acceleration**; each fragment that is cut off is cut again, growing shorter and shorter (Yang p0137).
- A secondary value is often `sequence` (this is precisely "the build-up before the climax forms," the proper place for sequence, p0115–0116) or the diminution side of `augment` (p0118).
  **The functional conversion of extension** (p0134) also lands here: the harmony is open, halting on the dominant or modulating, emphasizing the preceding idea while linking the old and new ideas together.

### 7.3 Bridge

Two paths: choose one and write it into `note`:

- **Fragmentation path**: use the preceding material, cutting it shorter and shorter, to create an increasingly lively or tense atmosphere while preserving unity (p0137).
  If you want the final chorus to rise one more level, the following-section technique of `counterpoint` is more effective than adding instruments.
- **Novelty path**: fill in `new`, but **you must first answer whether it is inherited, synthetic, or opposing novelty** (§3.9). If you cannot answer, you have not decided, and this section will most likely turn into another song.

★ **Asymmetry in entry and exit** (Li p0065): entry into the middle section generally uses no connection, which keeps the boundary of contrast sharply defined; exit often takes an indirect, gradual route.
**Cut hard on entry, withdraw indirectly on exit.** The hard-cut end can directly use intrusive opposition (Yang p0125–0126).

### 7.4 How the final chorus moves

Fill in `recap`, and state whether it is verbatim or dynamic. Four specific ways to move:

| Way | Basis |
|---|---|
| **Verbatim, changing only texture, orchestration, and dynamics** | Static recapitulation (Yang p0112). In the corpus, songs whose last pass is word-for-word identical to the first pass account for nearly 30% (Chinese-language lyric corpus, non-rap); this is not laziness |
| **Dynamic recapitulation** | Re-working of the motif, harmonic intervention, and thickening of texture, often leading to structural expansion or even becoming the climax of the whole song (Li p0023–0024; the five forms are in `mc-form` §6.2) |
| **Stretch the hook to twice its note values** | Augmentation: stable and weighty; used at the ending it calms the mood (Yang p0117). **It may augment only part of it**, lengthening just the first segment of the hook |
| **Added tail (extension or supplement)** | Extensions often occur before the cadence returning to the main key (p0135); or a supplement follows a perfect cadence, intensifying the climax and brightness at the close (p0142) |

★ **Aligned with the lyric side** (Chinese-language lyric corpus read song by song, 487 non-rap Mandarin songs: final pass unchanged 43%, one to three characters changed 25%, added tail 21%, fully rewritten 4%): the handling of the final section divides three ways: unchanged, a change of one to three characters, or an added tail;
**a full rewrite is a minority, and a rewrite means giving up the expectation accumulated in the first two passes.** The same holds on the music side: filling `new` in the final chorus is almost always a mistake.

### 7.5 Closing the whole piece

The first criterion is whether **a perfect cadence has already occurred before this passage**: if it has not, the only option is to shorten the statement itself through contraction;
if it has already cadenced but you still want to extend a passage further, use a supplement. The usage of each of the three paths:

- **Contraction**: gathering in, bringing no emotional rise; development gradually pauses and the sound gradually falls silent, mostly used at the ending or near the close (Yang p0136).
  For choosing among the three methods of omitting middle tones, omitting evenly and dispersedly, and contracting with modulation, see [reference.md](reference.md) §2.2.
- **Supplement**: a passage added after a perfect cadence. Choose one of three situations rather than doing all of them: a hurried cadence needs consolidating; emotion and sonority need to be gradually worn down; a climax already reached needs to be maintained or intensified (Yang p0142). A detailed table of situations is in [reference.md](reference.md) §7.2.
- **Compression into a fixed accompaniment**: compress the melody or hook into a figure; once the melody truly enters, the figure stays underneath, thereby becoming a fixed accompaniment figure (the prelude of Dvořák's *Lullaby* is an example, Yang p0119).
  The looping figure of an outro can be drawn directly from a compressed hook, with no need to write it separately.

---

## 8. Correspondence with ARR-SPEC fields

| Field | Type | Required | Notes |
|---|---|---|---|
| `material.motif` | str | ✅ | **Described in words, not written as notation**: interval contour, rhythmic pattern, and length, all three present. Missing interval or missing rhythm counts as unfilled (§1) |
| `material.character` | str | ✅ | One line of character |
| `material.stated_in` | list | ✅ | The ids of the sections where the original statement appears; may be several. **A new musical idea that appears midway and becomes the root of later development also counts** (Yang p0110) |
| `form[].development` | str | ✅ | **Closed set**; primary value first, secondary values joined with `+` (e.g. `fragment+sequence`); a list is also accepted. Only these ten values are valid:<br>`repeat` `sequence` `extend` `contract` `fragment` `vary` `augment` `counterpoint` `new` `recap` |

- Anything that cannot be fitted into these ten goes to the nearest one, with a sentence of explanation in `form[].note`; do not invent new names (§2.3).
- When filling `recap`, state **verbatim or dynamic** in `note` (§3.10); when filling `new`, state **which kind of novelty** it is in `note` (§3.9).

```yaml
material: {motif: "four-note stepwise descent, then a leap back up a fourth; short-long iambic figure, one and a half bars", character: "hesitant, held back", stated_in: [A1]}
form:
  - {id: A1, name: Verse,      development: repeat, note: "original statement, second phrase swaps the tail"}
  - {id: B1, name: Pre-Chorus, development: "fragment+sequence", note: "takes the second half of the motif, two ascending sequences"}
  - {id: D,  name: Bridge,     development: new, note: "inherited novelty, meter, tempo, and tonality unchanged"}
  - {id: C3, name: Chorus,     development: "recap+augment", note: "dynamic recapitulation, first segment of the hook doubled in value"}
```

| Adjacent field | Owned by | Relation to this skill |
|---|---|---|
| `form[].harmony` | `mc-harmony` | If a section is marked `vary`, the harmonic side can be realized with the seven variations that add no new chords (§6.3) |
| `form[].melody_register` | `mc-melody` | Contrast is needed between sections; the dynamic form of `recap` often also raises the register |
| `form[].bars` | `mc-form` / `mc-arrangement-arch` | `extend` and `contract` necessarily change `bars`; section names and development techniques are two separate labels, and a final chorus named Chorus that uses `recap` is not a conflict |
| `arrangement.energy_curve` | `mc-arrangement-arch` | `fragment` and continuous diminution are the mechanisms of rising energy; `contract` and supplement are the mechanisms of falling energy |

★ **Order**: `material` and `form[].development` are set after the skeleton and before melody and harmony. The reason is Schoenberg's "the beginning determines what follows" (p0041) and Yang Ruhuai's "the original statement is the root of all subsequent development" (p0110). Set the material first, then write the melody; only then can each section say where it comes from.

---

## 9. Checks to pass after writing

**Material and each section**

- [ ] `motif` contains **all three of interval contour, rhythmic pattern, and length**, with no notation written out; `character` is a single line that conveys a temperament
- [ ] `stated_in` is non-empty, and the `development` of those sections is not `new`
- [ ] Every section has a `development` filled in, primary value in first position; `extend` and `contract` both match `bars`
- [ ] Every `recap` states **verbatim or dynamic**
- [ ] Every `new` states **which kind of novelty** it is (inherited / synthetic / opposing, or derivative / juxtaposed)

**Three warnings for the whole piece** (the criteria are not iron laws; if a limit is exceeded, state the reason in `note`. ★ The three thresholds are this library's own settings; the source gives only the direction: mechanical repetition no more than twice, novelty is the most easily abused, and no more than two variation themes; on the music side there is not yet a corpus statistic on "which technique each section uses," to be calibrated once one exists)

- [ ] ★ **The number of sections filled with `new` does not exceed half the total number of sections**. If exceeded, first suspect that nothing is developing and it is merely piling up (§2.2)
- [ ] ★ **At least one section in the whole song is `recap` or `repeat`**. If none is, nothing has returned at all (Yang p0112)
- [ ] ★ **The `development` of the chorus passes must not all be `new`**. Every pass being new amounts to re-teaching the listener the hook every time

**Other**

- [ ] Can state whether the song is dominated by processing, unfolding, or contrast (§5.1)
- [ ] At least one threading device is present: joined ending, head-to-tail linking, motivic threading, or an accompaniment figure that runs across sections (§5.2)
- [ ] Sequences do not appear in the initial statement of verses one and two (§7.1), and the final chorus does not fill in `new` (§7.4)
- [ ] The joints between sections have been considered once: hard cut, overlap, or supplement (§5.3, §5.4)

---

## Appendix: Sources

- **Yang Ruhuai, *Analysis and Composition of Music*, Vol. I**: the backbone of the ten techniques in §3 (p0110–0144), and the joined and swapped endings, overlap, and supplement in §5.
- **Schoenberg, *Fundamentals of Musical Composition***: §4 from motif to phrase (p0018–0045, p0091–0099), the standard for rewriting in recapitulations (p0188), the baseline for recognizability in variation (p0229–0234), and the motif treatment of development sections and codas (p0253–0286).
- **Li Jiti, *Musical Form and Analysis***: the character and scale grading of motifs (p0016–0019), the three methods of development (p0020), and the variation-form system (p0159–0171).
- **Jimmy Kachulis, *Pop Songwriting: Harmony***: the seven variations that add no new chords (p0102–0138).
- **Chinese-language lyric corpus** (lyrics of songs by the top 100 singers on singer charts; only derived figures are counted): the chorus proportion and word-for-word identity ratio in §2.2 (counted by section labels, 3,631 non-rap songs), and the final-pass handling distribution in §7.4 (read song by song, 487 non-rap Mandarin songs).
- **Gathered from elsewhere**: the usage of augmentation, diminution, and sequence, and an alternative account of motif and phrase (`mc-melody`); how to develop musical ideas and how to combine forms, the three types of extension, the three methods of contraction, and fragmentation (`mc-form`); the seven variations that add no new chords (`mc-harmony`). Those points now retain only pointers.
- **Pointers only**: the causes of syncopation and answering (`mc-melody` §7); modes of statement, structural functions, the five forms of recapitulation, and sonata form (`mc-form`); counterpoint and fugue (`mc-counterpoint`).

## Appendix: Not covered by the source

- The `counterpoint` branch has only one entry, from Yang Ruhuai (imitation using augmentation and diminution), and its substance depends entirely on `mc-counterpoint`; there is no operational threshold for "does this section count as contrapuntal development."
- The pairing of secondary values (which primary values pair with which secondary values) is absent from the source; the common pairings in reference §1.1 are generalizations, not citations.
- The thresholds of the three warnings and the section defaults in §7 have not been calibrated against a pop corpus.
- For sections that advance through layering and filtering in loops, sampling, and electronic music, the ten values can only loosely map to `repeat` or `vary`; the Boléro model (Li p0169) is the only one that reaches, and the rest rely on `mc-arrangement-arch` §5 for arrangement, that is, form.
- Material development in rap (whether a change in flow counts as `vary`, and the relations of material between verses) is not addressed in the source.
- No source gives a number for how long a hook motive should be to be memorable; Schoenberg says only that variation motives rarely exceed two bars (p0232), and Li Jiti gives only bar ranges for figure, segment, and phrase (p0016–0019).
