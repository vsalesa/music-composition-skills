# mc-development Reference: Technique Overview, Three Types of Expansion, Variation Method Checklist, Types of Variation Form, Statement Types

> [SKILL.md](SKILL.md) covers what to do with the old material in each section; this file holds the **long reference tables**: definitions and cost comparisons for the ten techniques, the detailed breakdown of the three types of expansion and three methods of reduction, Schoenberg's classified checklist of variation methods, the types of variation form, and the correspondence between statement types and structural function.
>
> Sources: Yang Ruhuai, *Analysis and Composition of Music* (Vol. 1); Schoenberg, *Fundamentals of Musical Composition*; Li Jiti, *Musical Form and Analysis of Works*; Jimmy Kachulis, *Songwriting: Harmony* (for popular songs). Page numbers are noted in the text.

---

## 1. Overview of the Ten Techniques

The closed set of values for `form[].development`. The **criterion** column answers "how do you confirm that a section belongs to this technique."

| Technique | Definition | Criterion | Cost | Page |
|---|---|---|---|---|
| **`repeat`** Repetition | The musical idea is restated unchanged, or one end is kept while the other is changed (same-head / same-tail / changed-head / changed-tail) | The material is recognisable as a whole and the total length stays essentially the same; "same" works only when something new has appeared to set off the match, and "changed" works only when identical repetition sets off the replacement | Mechanical repetition provides unity but no contrast; usually no more than twice, and three or more consecutive repetitions become a flaw | p0111, p0128–0129 |
| **`sequence`** Sequence | The idea is repeated at a new interval degree, or at a new pitch level at the same time | The interval relations of each step shift regularly; in pentatonic material, strict sequence only requires the direction to match | Placed in the initial statement stage, it is heard immediately as a formula, especially a modulating sequence; if the steps do not change, it becomes rigid | p0115–0116 |
| **`extend`** Extension | On a repeated statement, the idea is stretched from within, and the extended part joins organically with the original idea | **Generally does not return to the original closing material** (distinguishing it from the head-and-tail principle); the total length grows | An internal extension, if not compared with the original statement, is sometimes hard to recognise | p0131–0135 |
| **`contract`** Contraction | On a repeated statement, the structure is shortened compared with the original statement | The material remains recognisable but has lost some notes or bars; the total length gets shorter | Its effect is to draw things together, and it **does not bring emotional rise**; it is less used and the method is simpler | p0136 |
| **`fragment`** Fragmentation | Pieces of the idea are extracted on their own and used in separate pieces, repeatedly, each time shorter | You can hear that "a fragment" is recurring, and each time it is shorter than the last | The more it is cut down, the more melodic character is removed at the same time; at the extreme only rhythmic specks remain | p0137–0139; Schoenberg p0280 |
| **`vary`** Variation | Keeps the overall outline, motion layout and structural scale, but changes its appearance | **Has a new appearance yet the unity with the prototype can still be recognised**; the structural proportions stay the same | Decorative variation cannot step outside the expressive range of the original theme; character variation requires finding a rhythmic figure appropriate to the genre | p0114–0115 |
| **`augment`** Augmentation / Diminution | Under the same metre and tempo, note values are lengthened or shortened by a multiple | **Relative note values stand in a multiple ratio**; it is judged neither by how the score is written nor by how the performance handles tempo | Augmentation slows the progression down, diminution uses up singability; after consecutive diminutions there must be a point of arrival | p0116–0119 |
| **`counterpoint`** Contrapuntal form | One part imitates another by using an augmented or diminished form of the idea | The same material appears staggered across two or more parts | Every layer must be audible; if frequency bands and depth are poorly arranged, the layers blur into one line | p0118–0119 |
| **`new`** New material | No fixed tonal or melodic outline of the original idea is maintained, and a new idea appears | You cannot tell that it comes from what came before | It has the widest range of application and is **the easiest to abuse**; too many juxtaposed sections create centrifugal force | p0122–0126; Li p0025 |
| **`recap`** Recapitulation | After a contrasting statement, a previously stated idea returns | The material corresponds to some earlier section; **it need not be in the tonic key** | An unchanged recapitulation lacks drive; a dynamic recapitulation that is altered too much may no longer be recognisable as the original | p0112–0113; Schoenberg p0188 |

### 1.1 Primary and Secondary Values

Each section has one primary value, and a secondary value may be added. Yang Ruhuai reminds us that the various derived forms **can transform into one another and pass through many intermediate forms**, and that "in any case, dogmatic, mechanical analysis will harm the actual practice of musical art" (p0127). Secondary values are therefore the norm rather than the exception. Common pairings:

| Pairing | What it means |
|---|---|
| `fragment` + `sequence` | Cut out a fragment and push it upward through sequence; the drive is most evident when the two combine (p0115–0116) |
| `vary` + `extend` | Varying the idea while a few bars grow at the end of the phrase |
| `recap` + `augment` | On the recapitulation, stretch the hook to twice its note values |
| `recap` + `extend` | Extension before the final cadence on the tonic, returning to the home key (p0135) |
| `repeat` + `vary` | Repetition in the manner of iteration (p0113) |
| `new` + `repeat` | New material repeats itself immediately so that it can be remembered (p0111) |

### 1.2 Detailed Table of the Three Kinds of New Material (Yang Ruhuai p0123–0126)

Arranged from near to far in terms of "how far away from what came before." When filling in `new`, note in `note` which kind it is.

| Kind | Criterion | What still connects it | Common position |
|---|---|---|---|
| **Inheritive new material** | Different ideas in succession within the same expressive domain of an image; whether separated by a cadence or joined into a whole, they express a unified intention | Consistency in rhythmic range, melodic development scale, tempo, style, mode and key, and the overall character; even without tonal connection, it can rely on the direction of the melodic line, rhythmic combination before and after, the matching of long and short phrases, harmonic and modal echoes of key pillar notes, and unity of performance technique and dynamics (p0124) | The second phrase inside a section; the safe approach for a bridge |
| **Synthetic new material** | The contrast is very marked, showing only a more hidden connection or little connection | Only the same metre, tempo, key and expressive dynamics remain; **contrast of thematic material dominates** (p0124) | Most common in large, complex sonata and symphonic development |
| **Opposing new material** | The preceding and following ideas create an interruption, forming a clear opposition, with no internal connection by any local technical means | It makes sense only from the dramatic development of the whole compositional conception and the image content (p0125) | Divided into **violent opposition** (sudden contrast, dramatic turn) and **mild opposition** (not surprising, seeking only freshness and variety) |

★ **Intrusive opposition** (p0125–0126): To achieve a clear division into sections and a dramatic effect, a contrasting idea suddenly intrudes before the current idea has ended, and a new formal section begins at the same time. What usually brings it about is the cadence of the previous section and a change of mode and key in the following section, sometimes accompanied by changes in dynamics, tempo or register.

★ **The three kinds can coexist** (p0126): Within the different developmental stages of one long melody, all three kinds of new material can appear in turn, linked together and forming a complete dramatic process. This is especially representative of large synthetic melodic structures.

**Li Jiti's dichotomy, side by side** (p0020–0021): derived contrast (the contrasting material still has an internal connection with the original idea, for example the descending broken chords of the main section of the first movement of *Appassionata* stand in contrary motion to the ascending broken chords of the subordinate section) versus juxtaposed contrast (no internal connection between the materials). Derived contrast creates a sense of difference while keeping the materials related by blood; juxtaposed contrast is stronger in contrast, but the unity of the whole piece must then be solved separately.

### 1.3 How Yang Ruhuai's Three-Level Progression Maps onto These Ten Values

| The book's term | Definition | Mapping | Page |
|---|---|---|---|
| **Development along the type** | Keeps the rhythmic figure unchanged, changing only the direction or interval of melodic motion | `vary` (secondary `sequence`) | p0120–0121 |
| **Evolutionary development** | Keeps the core tonal shape and rough outline, altering rhythmic figure, intervals or structure to form a variant | `vary` or `extend`, secondary `new` | p0121 |
| **New material** | Does not preserve any fixed tonal pattern or outline | `new` | p0122 |
| **Iterative performance** | On repetition, keeps the overall melodic appearance and makes only local melodic changes; the passes may each differ | `repeat` + `vary` | p0113 |
| **Expansion and development** (Li Jiti) | Starting from the original idea, gradually renews the material; especially common in traditional Chinese music | Same as evolutionary development | Li p0020 |

★ **The boundary between development along the type and sequence** (p0120): both hold firmly to a fixed rhythmic pattern. Development along the type is freer in interval and direction, and its unity depends mainly on "rhythmic resemblance" (people perceive rhythm more readily than pitch); sequence, by transposing at a set interval, carries a sense of motion. Development along the type is better at expressing echo and paired-couplet effects between statements: using a differently functioning ending tone each time connects the statements functionally, whereas sequence readily isolates one statement from another. **For a sense of echo, use development along the type; for a sense of forward momentum, use sequence.**

★ **How development along the type avoids becoming aimless** (p0121): when restating the original statement, use sequence at the start, let the ending tones of each step form a modal echo, and use the same opening phrase.

★ **Concrete means of evolutionary development** (p0121, can be combined): freely alter pitches, rhythm, and metre; partial augmentation and diminution; keep the direction of motion and the rhythmic figure while changing only the intervals; local variation, extension or contraction; over the course of evolution, a longer idea changes its mode and key. The object of evolution is not necessarily the whole idea: for a large-scale idea, one evolutionary step may be just a fragment cut out from it. **When the degree of development is greater, failing to analyse closely can sometimes lead one to mistake it for a contrasting new idea.**

---

## 2. Three Types of Expansion, Three Methods of Reduction, and Fragmentation (Yang Ruhuai p0131–0139)

### 2.1 Three Types of Expansion (side by side; the first two are the most important and most used, p0131)

| Type | Method | Effect and criterion | Page |
|---|---|---|---|
| **Internal expansion before the cadence** | The simplest technique is to use one element from within a sequence or a repeated idea, and by emphasising that element, the structure "grows" in place | If two phrases within a passage were originally related by same-tail changed-head, once this kind of expansion is applied they can no longer be seen as a same-head changed-tail development: same-head changed-tail generally does not change the total length of the idea, whereas internal expansion does | p0131–0132 |
| **Expansion after a blocked resolution before the cadence** | A cadence that should pause on the perfect tonic chord has its dominant resolution blocked, so development must continue briefly before it finally ends with a normal cadence; the earlier thematic material is usually restated once more before the expansion | **Can be observed without comparing with the original statement** (a blocked cadence is itself recognisable); an internal expansion, if not compared with the original statement, is sometimes hard to recognise | p0132–0133 |
| **Compact expansion after the cadence** | After the cadence has been completed, a passage continues in a rhythmically very compact way before the ending is truly reached; compact syncopation is often used so that the originally complete cadence seems less certain, and then a more definitive cadence after the expansion closes it | Rhythmic compactness often takes the form of reverse-dotted rhythmic figures and also often brings a further emotional rise; the difference from a "supplement" is that a typical supplement does not show the condition of rhythmic compactness so prominently | p0133 |

**Developing versus concluding** (p0132): for any internal expansion, the criterion is whether it brings **the growth of new qualities** or **the consumption of emotion**. A developing expansion accompanies sublimation of the image and emotional rise, producing a climax or introducing a new idea for the next section from within the climax; a concluding expansion leads to no greater rise, and instead lengthens and delays the statement, gradually falling quiet.

**Functional transformation** (p0134–0135): an expansion can become the preparation or lead-in before a new idea appears. In that case it does not end with a perfect cadence; instead, the harmony remains open (stopping on the dominant chord or moving to another key). This both emphasises development of the preceding idea and unifies the old and new ideas into a continuous whole. This kind of functional transformation is usually accomplished through internal expansion before the cadence. Modulating within an expansion is the typical practice of the transition section in sonata form.
★ When each expansion also completes a modulating transition, the themes **gain internal motion and organic growth** between one another, rather than merely changing position externally. If the original statement of an idea ends on a half cadence or in another key, the repetition or recapitulation that follows often has an expansion before it returns to the tonic cadence (p0135).

**Two rarer kinds of expansion** (p0135):

| Type | Method | Effect |
|---|---|---|
| **Tail expansion** (rare) | Before the tonic of the cadence arrives, the idea suddenly breaks off; the accompaniment either continues or stops abruptly, and then a new cadential fragment or a repeated fragment of the idea follows, ending normally | Sometimes produces a light, playful effect |
| **Forward expansion** (fairly rare) | On a repeated statement, a new head is added at the front | Similar to the same-tail technique, but **it first displays the core of the idea and then returns to that core from a different starting point**, emphasising the dominance of the core element |

### 2.2 Three Methods of Reduction (side by side, p0136)

| Method | Method | Use |
|---|---|---|
| **Omitting the middle pitches** | On repetition, keeps only the opening and closing motion of the idea and omits the middle | The most direct cut |
| **Evenly distributed omission** | Omissions are not concentrated in one part but spread fairly evenly | Used to control the rise and fall of the melodic line and gradually lower and soothe the emotion |
| **Key-changing reduction** | While moving from a different key in which the original statement ended back to the original key, the lengthened statement is compressed to normal size | The reverse process of expansion |

**Character**: reduction has a drawing-together effect, usually taking the form of a brief recollection, a summarising restatement, or a supplement, and **it brings no emotional rise**. It is therefore used mostly at endings or near the close, so that development gradually comes to rest and the sound gradually becomes silent. It is less used than expansion, and its methods are simpler.

**Schoenberg's three terms** (p0091 footnote, p0188): **curtailment** merely deletes part of the prototype; **condensation** compresses the prototype's content, and the order of its characteristic figures may also change; adding **elision**, the three differ in meaning. In a recapitulation, shortening is used to avoid monotony, and lengthening (inserted material, interpolated repetition, extension or addition) is used to create emphasis; the two are parallel but opposite-direction treatments.

### 2.3 Fragmentation (p0137–0139)

- **Method**: The pieces that make up the idea are extracted independently in some way and used as they are or after processing through various development techniques, cut into segments as needed.
- **Typical process**: consecutive, repeated, and drawn from different parts of the idea; each extracted fragment is then cut again, **getting shorter and shorter, and the development becoming more and more compact**.
- **Effect**: suitable for pushing emotion toward a climax and creating an increasingly lively or tense atmosphere; it can produce extreme unity of development while expressing multiple layers.
- **Role**: the fragmented material can serve as either a principal part or a background accompanying part, and can take on both functions at once. The overall tendency is that it gets shorter and the motion faster, and combined with orchestration that gradually thickens, it builds to a rise in sound and emotion.
- **Difference from motivic-thread development** (p0139): In motivic development, fragmenting the theme **always retains the core element of the motif**; every fragmentation form keeps this core, non-motivic material is not developed by fragmentation, and the motif may be extended with new material during fragmentation. General fragmentation, by contrast, simply cuts all the material of the theme itself shorter and shorter.

---

## 3. Schoenberg's Classified Checklist of Variation Methods (p0030–0031)

**Definition** (p0028): A variation is a repetition in which some characteristic figures change and the rest remain as they are. The rhythm, interval, harmony and contour characteristics can each change independently; several methods are often applied to several characteristic figures at once, but **the resulting motif should not stray too far from the basic motif**.

### 3.1 Changing Rhythm (six methods)

| # | Technique |
|---|---|
| 1 | Change the note values |
| 2 | Repetition of a note |
| 3 | Repetition of certain rhythms |
| 4 | Shift the rhythm to different beats |
| 5 | Add upbeats |
| 6 | Change the metre (the author's comment: "this technique is not very applicable in small pieces") |

### 3.2 Changing Intervals (six methods)

| # | Technique |
|---|---|
| 1 | Change the original order and direction |
| 2 | Add or remove intervals |
| 3 | Fill intervals with auxiliary notes (the author deliberately avoids the word "ornament" to prevent aesthetic misunderstanding) |
| 4 | Curtailment (with the help of elision or condensation) |
| 5 | Repeat the characteristic figure |
| 6 | Shift the characteristic figure to other beats |

### 3.3 Changing Harmony (four methods)

| # | Technique |
|---|---|
| 1 | Use inversions |
| 2 | Add material at the end |
| 3 | Insert material in the middle |
| 4 | Substitute another chord or chord connection |

The four changes differ in weight: the first three (inversion, adding at the end, inserting in the middle) still follow the original harmonic skeleton, merely spreading it out or thickening it; the fourth directly replaces the chord or its connection, making it the largest change of the four. Schoenberg's own music examples also progress in this order (p0033–0035): first a richer harmony is applied, and then the whole passage is re-harmonised with harmonic markings, with the degree of change increasing steadily as the method numbers rise. The melody itself does not move, and these four harmonic changes are enough to make the same melody sound new; this is why they come after "changing rhythm" and "changing intervals" and are given a category of their own (p0030).

### 3.4 Adaptive Changes to the Melody (three methods)

| # | Technique |
|---|---|
| 1 | Transposition (shifting position) |
| 2 | Add passing chords |
| 3 | Treat the accompaniment in a "semi-contrapuntal" way |

★ These three items are **passive adjustments** the melody makes to accommodate the first three categories of change; they are not independent sources of variation motifs. Schoenberg says that systematically exploring the possibilities of variation greatly helps in acquiring fluent technique and a rich creative capacity (p0031).

### 3.5 The Five Equivalent Forms of Exact Repetition (p0026)

Inversion, retrograde, retrograde inversion, diminution, and augmentation, plus simple transposition to another scale degree, **all count as exact repetition**, because the relationships between notes are strictly preserved. ★ The judgement rests only on whether the relationship is strictly preserved, not on surface similarity, so operations that sound very different are classed together here.

### 3.6 Degrees of Derivation (p0037–0039)

| Distance | Characteristics |
|---|---|
| Near | Rhythmic characteristics stay unchanged; only pitch changes |
| Somewhat far | Rhythm stays strictly unchanged; direction changes and the figure is shifted |
| Further | Both rhythm and intervals and direction change |
| Remote contrast | Rhythmic shift + added upbeats + curtailment + elision of characteristic figures |

**Bottom line**: a motif type adopted from a remote relationship may hinder comprehension; every new motif derived **must still have the quality of a "true short phrase"** (a complete musical unit). If derivation fails, what is produced is only fragments. A short phrase that does not begin on the tonic chord may be used as material for contrast, secondary ideas, or other structural needs (p0037).

### 3.7 Seven Variations Without Adding New Chords (Kachulis, p0102–0138)

The direction is the opposite of "making the progression more complex": **not a single chord is added; only the face changes.**

**Three rhythmic variations** (p0102–0110):

1. Change the length of the progression: the same progression with each chord lasting 1 beat, 2 beats, 1 bar, or 2 bars; phrases ranging from half a bar to 4 bars
2. Change the note value of just one or two chords
3. **Change the order of chords**: I–IV–V → V–IV–I → I–V–IV

**Four pitch variations** (p0122–0138):

1. Remove one chord
2. Add chords: add back ones already in the progression, or add new ones from inside or outside the key
3. Replace one chord
4. **Add a sustained note**, in three levels: a single tonic in the bass → a fixed bass figure → an additional sustained part above the bass

★ **Use two rhythmic variations of the same progression for the verse and the chorus**: the identical chords guarantee the connection, and the changing rhythm provides the contrast (p0111–0115). Ranking of contrast strength: same progression with changed rhythm < same progression with changed chord note values < **two sections using different progressions with different starting chords** (p0116).

---

## 4. Types of Variation Form (Li Jiti p0159–0171)

Variation is a material-processing technique that can be used within any form; as a mature variation form, it **must rely on other principles of form-combination** (ternary recapitulation, multi-part symmetry, sonata, suite, etc.) to form a logical whole. In analysis, one must not only mark each section and its variation technique, but also indicate which combination principle the whole relies on (p0159).

### 4.1 The Two Major Types

| Type | Definition | Page |
|---|---|---|
| **Strict variation** | Processes the material under the overall premise of keeping the original thematic material and structural outline unchanged | p0159 |
| **Free variation / character variation** | The original theme's structure may be unfolded or dismembered, and even new material may be added; the range is wider and often leads to a change of musical character | p0159, p0166 |

### 4.2 Fixed-Basis Variation (under strict variation; three types side by side)

The basic feature is to **fix one memorable element of the musical structure** and vary the other aspects on that foundation.

| Type | What is fixed | Characteristics and specialisation | Page |
|---|---|---|---|
| **Fixed-bass variation** (passacaglia) | The fixed figured bass | Originates from ancient organ playing: the pedal board first sounds the fixed bass alone, and then the fingers gradually add other parts, forming a polyphonic development; the style is always associated with polyphonic music, and the themes vary in length (long ones spanning one passage, short ones a phrase or a single unit); it has a positive effect in intensifying the deeper expressive power of music | p0160 |
| **Fixed-harmony variation** (chaconne) | The fixed harmonic-function progression | Does not require keeping the original theme's upper melody or bass; it need only operate within the established harmonic-function progression, so that **only the harmonic skeleton is fixed, and every other dimension is open**; it excels especially in instrumental figuration textures and harmonic cadenza-style variation, providing a formula of "never straying from the basic principle" for improvisation | p0161 |
| **Fixed-melody variation** (fixed soprano) | The original melody | A product of the national school, directly addressing the problem that folk strophic songs have "many verses, a strong narrative character, and simple repetition that becomes tiresome": the melody is kept unchanged while the accompanying orchestra creates different emotional backgrounds; apart from the melody, which must be fixed, the harmony, key, texture, and even orchestration can all be varied | p0163–0164 |

★ Fixed-bass variation and fixed-harmony variation were later often used in combination, so that the terms are no longer strictly distinguished (Brahms's *Symphony No. 4*, final movement: some call it a chaconne, others a passacaglia); in actual analysis, there is no need to force a choice between the two (p0162).

### 4.3 Theme-and-Variation (fixing no single dimension; requires varying the theme itself, p0165–0166)

| Type | Definition | Limits and cost |
|---|---|---|
| **Classical decorative variation** | The emphasis is on decorative processing of many aspects around the theme's melody; the original theme's formal structure stays unchanged, its melodic skeleton stays unchanged, and its harmonic skeleton remains relatively stable | Precisely because neither the structure nor the basic harmonic skeleton changes, it **rarely steps outside the basic expressive range set by the original theme**; suitable when one wants to dig deeply into the many-sided expressive power of a single emotion, but not for passages seeking dramatic breakthrough |
| **Free variation (character variation)** | The original theme may be unfolded and dismembered in various ways, including changing its form and genre; harmony and key may also be altered, so that the theme undergoes essential, dramatic change | Three paths for handling material: vary all the basic material of the theme, develop one particular material intensively, or occasionally insert new material for contrast, **on the premise that the overall structure remains dominated by variation** |

**Criteria for choosing a theme** (p0165): a theme is best when it is short and easy to remember yet rich in content (containing contrasting elements); many composers prefer a simple binary form as the theme; the melody, harmony, tempo, dynamics, texture and register are best kept in an "intermediate state" (neither overly ornate nor overly plain, neither too fast nor too slow, neither too loud nor too soft), so that more room is left for processing.

### 4.4 How to Control the Overall Rhythm (p0166)

Strict and free variation are often used in mixture: a variation set led by free variation will always interleave several strict-variation sections, and **especially the opening few variations generally begin with strict variation**, so that listeners first memorise the structural framework and tonal character of the original theme before the music gradually shifts to free variation. In a structurally large variation set, after free variation has developed to a certain extent (for example after entering a climax), a "returning" strict variation may reappear, creating an internal wave-like rise and fall once more. **Pure free variation from the opening may leave listeners unable to grasp the theme; pure strict variation may lack dramatic rise and fall.**

### 4.5 Four Ways to Combine Two Themes (p0169)

| Method | Arrangement |
|---|---|
| Alternation one by one | A, B, A1, B1 …… |
| Alternation by groups | A, A1, A2, B, B1, B2, A3, A4 …… |
| Mixed alternation | A, A1, B, A2, B1, B2 …… |
| Vertical combination | For example, A is a fixed-bass theme and B is an upper contrapuntal theme, stacked vertically at the same time |

★ A variation set generally uses only one theme; **more than two themes is generally avoided**, because too many themes make the variation set long-winded and complicated (p0160).

★ **The *Boléro* model** (p0169): fixed rhythm, fixed harmony (tonic and dominant), and fixed key are all locked down, and the only variable falls on timbre, orchestration and the layered build-up of dynamics, thereby creating the single source of tension for the whole piece. The principle is that **the more fixed elements there are, the more the changing element stands out against them**.

### 4.6 Schoenberg's Supplements on Variation Form (p0229–0234)

- A classical variation set requires the theme to be **recognisable** in every variation: even if the character changes, the course of events (the number and order of the fragments) should not change; metre and tempo may change, and the number of bars may be regularly doubled, but the proportions and structural relations among the parts and the main characteristic figures are all retained; each variation should, like the theme itself, be self-contained in form with its own beginning and end.
- The **variation motif** is taken from the theme itself, so that all variations are closely related to it. The method of obtaining it is first to identify the basic elements of the theme, then omit all secondary components (embellishments, ornaments, passing notes, suspensions, appoggiaturas, trills, and flowing figures) so that the "skeleton" of the basic structure is laid bare; harmonic relations must be considered during curtailment.
- The characteristic figures that dominate each section need not be uniform, so **there may be more than one usable skeleton**.
- The length of a variation motif is limited by the number of principal notes and principal chords; it **seldom exceeds two bars and in many cases is only half a bar or shorter**. ★ The contrast between static harmonic passages and sequential passages demands that the variation motif be extremely flexible and varied, with the result that many motifs become very short: **the denser the harmonic motion, the shorter the length a motif can sustain** (p0234).
- Uniform accompaniment makes variation easy to write; too many changes in the accompaniment can become an obstacle (p0231).

---

## 5. Harmonic Layout of the Antecedent and Consequent Forms (Schoenberg p0041–0045)

The relationship between the first phrase (antecedent form) and the second phrase (consequent form) resembles the subject and answer of a fugue: on repetition, **the rhythm and melodic outline remain unchanged**, and "unity within contrast" is formed through harmonic change and the necessary adaptive adjustment of the melody.

| Antecedent form | Consequent form |
|---|---|
| I | V |
| I–V | V–I |
| I–V–I | V–I–V |
| I–IV | V–I |
| I–II | V–I |

★ An antecedent of the I–IV or I–II type could in theory be simply inverted to form the answering phrase, but Schoenberg explicitly holds that **the V–I progression is superior** (its tonality is clearer), so in practice V–I is preferred.

★ If the antecedent contains too many chords, **answering it mechanically, identically, is impractical**: in that case only the principal chords (such as I–V) receive an answer (using V–I), and the other passing chords need not be retained mechanically (p0044–0045).

---

## 6. Correspondence Between Statement Types and Structural Function (Li Jiti p0022–0024)

The usual logic of a musical idea's statement is "first state the original idea → consolidate it → develop and contrast → summarise and conclude," which corresponds to the classical four-part sequence of "introduction, development, turn, and conclusion" (qi, cheng, zhuan, he).
★ For each section in the specification sheet, write which mode of statement it uses; if a chorus is written as developmental or a bridge as presentational, the section's function is misaligned, and changing its name will not fix that.

| Mode of statement | Characteristics | In one line |
|---|---|---|
| **Presentational statement** | Original statement plus consolidation; stable key, unified material, complete syntax | Lay the material out |
| **Developmental statement** | Harmony and key are unstable and increasingly turbulent, the structure fragments, key shifts are frequent, and there is no complete stable syntax | Take the material apart |
| **Transitional statement** | First supplements the preceding idea, then modulates, and finally introduces a new idea or stops on an **expectant chord** (the dominant of the new key) | Build a bridge |
| **Concluding statement** | The idea no longer moves forward; the melody is fragmented, the key is stable, and the cadence or tonic pedal is emphasised | Answer without asking |
| **Introductory statement** | Prepares for the entry of the main idea; may indicate key, tempo, texture, or a melodic outline, or prepare through contrasting devices | Ask without answering |

| Structural function | Which mode of statement | Key points |
|---|---|---|
| **Introduction / prelude** | Introductory | May also be a summarising or concluding introduction |
| **Opening section** | Presentational | |
| **Middle section** | Development or contrast | ★ Even if a new theme is introduced in a presentational statement, as long as its purpose is to contrast with the original theme, the function is still classed as contrast |
| **Connecting section** | Transitional | In large works it sometimes has the dual function of "developing what was left unsaid earlier and then turning toward what comes next" |
| **Recapitulation section** | Presentational restored | Its purpose differs from the original opening statement: it emphasises the main idea and restores structural balance; when development from the middle seeps in, it becomes a **dynamic recapitulation** |
| **Coda** | Concluding | The coda of a large work may also first supplement, then develop, then conclude |

★ Introductions, connecting passages and codas are **subordinate structures**, and may be treated more freely than the main sections (p0023–0024).

**Developing treatment in single-part form** (p0035–0036): ordinarily, presentational statement predominates, and developmental function is not common; but in dramatic works a developmental treatment may also be used, marked by **breaking the periodicity of the internal structure**. The means are structural decomposition devices such as local repetition, variation, fragmentation, sequence and imitation, plus contrast and structural synthesis, or harmonic complication and obstruction of progression. The common procedure is: in the second phrase of the passage, the first unit consolidates the basic idea, and from the second unit onward, fragmentation, sequence and other developmental techniques are used, forming a complete process of "consolidate, develop into a climax, then conclude."

---

## 7. Four Types of Overlap and Three Supplementary Situations (Yang Ruhuai p0139–0144)

### 7.1 Four Types of Overlap (side by side)

| Type | Method | Page |
|---|---|---|
| **Regular-bar overlap** | A certain bar is both the last bar of the preceding music and the first bar of the following music, becoming a "shared" bar between the two passages | p0139–0140 |
| **Syncopated overlap** | When the whole theme is repeated, it overlaps the preceding material by syncopation, making the statement particularly urgent and compact and forming two great wave-like motions | p0140 |
| **Overlap of introduction and theme** | The introduction is built on a passage sustaining an unstable dominant function; when the melody reaches the register at which the theme enters, the unstable function is finally resolved, so the end of the introduction and the entry of the theme fall on the same beat | p0140 |
| **Overlap of accompaniment figure or harmonic background** | What overlaps the end of the preceding material is the prelude accompaniment figure or sustained harmonic background of the new theme; the new theme sounds for a moment here before truly entering | p0140–0141 |

★ The effect of the fourth type: it renders the mood of entry and delays the theme's arrival to create freshness; it is more compact than direct overlap, and **because the theme's appearance is delayed, the listener's attention to its entry actually increases**.

**Dramatic intrusion** (p0141): the overlapping new material not only contrasts sharply with what precedes it in expressive means, but also does not begin by conforming to the tonic harmony of the preceding theme's cadence. Criterion: from the harmonic progression it resembles an obstructed cadence, and from the development of the thematic material it resembles an extension; but the overlapping new material is independent, with its own developmental thread and an original conception of intrusion. If the harmony has no conditions at all for an obstructed cadence, that is a true "intrusion," and then the harmony and the thematic material stand in a "leaping" relation; the connection between them can only be found from the standpoint of the overall artistic conception.

### 7.2 Three Supplementary Situations and Three Kinds of Material

| Situation | What it is used for |
|---|---|
| **Consolidating an abrupt cadence** | The idea ends abruptly, and the cadence is too brief to give a sense of stable closure; or the idea ends in a low register and its emotion has not fully developed |
| **Consuming emotion and sonority** | Gradually uses up the emotional height and sonic brightness reached at the end, so that the depicted image recedes gradually or the scene transition is prepared |
| **Sustaining or intensifying the climax** | Keeps or increases the emotional climax and sonic brightness reached at the ending, deepening the impression |

**Three kinds of material** (p0143): simply repeating previously stated material (especially the closing tonal fragment once the cadence has been reached); using entirely new material; or combining previously stated tonal fragments with new material.

**Harmonic character** (p0143): halts the preceding music's development so that no new development opposes it; often alters the original harmonic arrangement, emphasises the subdominant and tonic functions, avoids distantly related modal and harmonic devices, and often features a tonic pedal.

★ **The criterion distinguishing it from expansion** (p0142): expansion deliberately conceals the sense of having reached a stopping point **before** the cadence appears, expanding the idea from within and then closing with a perfect cadence; it manifests as organic growth from inside. A supplement, by contrast, must be a concluding statement carried out **after** a perfect cadence or half cadence, and it manifests as an external, additional, auxiliary statement.

### 7.3 Structural Unifying Techniques: Same-Head, Same-Tail, Changed-Head, Changed-Tail, Head-and-Tail Match (p0127–0131)

| Technique | Criterion and use |
|---|---|
| **Same-head / changed-tail** | Starts from the same idea and unfolds outward into several presentations |
| **Same-tail / changed-head** | Starts from different statements and gathers inward into one central idea |
| **The whole-piece function of same-tail** | All themes end with the same melodic fragment in the same key, unifying the whole piece in both content and thematic material; even when the middle contains a contrasting section formed by inheritive new material, same-tail can still unify it with the other sections |
| **Head-and-tail match (linked chain)** | After one idea ends on a clear cadence, the next idea begins by repeating the same cadential passage, linking one after another |
| **Another form of head-and-tail match** | On repeated statement, the beginning and end stay consistent while an iterative change occurs in the middle; ★ a longer iterative change right in the middle often provides the very opportunity for the restatement of the idea to create a climax (or to surpass the first climax point) |

★ **Criterion** (p0128): "same" creates a match in thematic material because something new has appeared, and "changed" creates a replacement in material because identical repetition has appeared. Same and changed operate between juxtaposed statements, whereas recapitulation is when an independent idea reappears after other ideas have been stated; the two are different.

★ **When the distinction becomes meaningful** (p0129): Only when the idea is long enough to divide into head, middle and tail, and the head or tail being changed occupies only a small part of the whole (a third or less), does "same-head changed-tail" versus "same-tail changed-head" have a meaningful distinction; if the idea is too short to divide into head, middle and tail, or the same/changed portion begins exactly at the midpoint, the two descriptions make no difference.

★ **Cadential echo in changed-tail** (p0129): If a changed-tail development ends on a note with the meaning of a half cadence in the mode, then when the changed-tail repetition is made, moving the closing note to the mode's tonic-function note means the two statements form a continuous antecedent–consequent relation through the functional echo of the cadences.

---

## Appendix: Sources for These Tables

| Table | Source |
|---|---|
| §1 Overview of techniques, §1.2 Three kinds of new material, §1.3 Three-level progression | Yang Ruhuai, *Analysis and Composition of Music* (Vol. 1), p0110–0144; Li Jiti p0020–0021, p0025 |
| §2 Three types of expansion, three methods of reduction, fragmentation | Yang Ruhuai p0131–0139; Schoenberg p0091, p0188 |
| §3 Classified checklist of variation methods, five forms of exact repetition, degrees of derivation | Schoenberg, *Fundamentals of Musical Composition*, p0026–0039 |
| §3.7 Seven variations without added chords | Jimmy Kachulis, *Songwriting: Harmony*, p0102–0138 |
| §4 Types of variation form | Li Jiti, *Musical Form and Analysis of Works*, p0159–0171; Schoenberg p0229–0234 |
| §5 Antecedent and consequent forms | Schoenberg p0041–0045 |
| §6 Statement types and structural function | Li Jiti p0022–0024, p0035–0036 |
| §7 Overlap, supplementation, same-head and same-tail | Yang Ruhuai p0127–0144 |

**Covered elsewhere, not in this file**: the full use of the five statement modes at the section level and the five forms of recapitulation are in `mc-form` §6.1–6.2; sonata form is in `mc-form` reference §4.2; imitation, canon, fugal sections and continuation sections are in `mc-counterpoint` §7 and reference §7; the causes of motif → phrase → section segmentation and echo are in `mc-melody` §7.
