---
name: mc-orchestration
description: Orchestration at the decision level - which instruments carry which line, pure vs mixed timbre, blending (unison, octave coupling, separate registers), balance, technique's effect on blend, register-dependent character, MIDI orchestration, and Chinese folk orchestra scoring - four sections, pairing/clash, melody/bass/harmony assignment, arranging/transplanting. Use when picking an instrument, adding a layer, muddy or vanishing woodwinds, fake MIDI mockups, erhu/pipa/dizi/suona/sheng/guzheng, or ARR-SPEC roster fields. Keywords: orchestration, instrumentation, mixed timbre, octave doubling, instrument balance, register character, MIDI orchestration, Chinese folk orchestra, minyue scoring, full score layout, transposing instruments. Tables in reference.md.
---

# Orchestration

**This skill covers "which instrument should play this line" and "what timbre a few instruments create when combined."**

Orchestration is not about "adding instruments" to music that is already written — **choosing the instruments itself changes the music**.
The same chord played sustained by strings versus staccato by woodwinds are two different things.

> **Division of labor with adjacent skills**: this skill decides **who plays**;
> `mc-texture-layering` decides **who occupies which frequency band and who yields to whom**;
> `mc-arrangement-arch` decides **who enters and exits when**.
> The three are often used together, but do not write frequency budgets or entry/exit tables here.

## Which sections to read for each task

| What you need to do | Read |
|---|---|
| A melody/harmony line, not sure who should play it | §1 required before starting → §2 pure timbre or mixed |
| Want to add a layer, not sure what to add | §3 three forms of mixing |
| Added a layer and it turned muddy | §3.4 neutralization, §4 balance |
| Woodwind writing is inaudible | §3.3 coloring + §5 three conditions for projection |
| Same instrument sounds wrong in a different register | §6 register is character |
| MIDI mockup sounds fake | §7 MIDI orchestration |
| **Writing for Chinese folk orchestra** | Difference table at the start of §8 → §8.1 four group characters |
| Which two groups in a folk orchestra work together | §8.2 group combinations |
| How to divide melody/bass/harmony/accompaniment in a full lineup | §8.3 full lineup |
| Folk orchestra fails to build to a climax, or sounds muddy | §8.4 treatments (balance, emphasis, transition, growth and reduction) |
| Folk concerto, soloist gets overwhelmed by the ensemble | §8.5 solo instruments within the ensemble |
| Converting a Western piece into folk style (or the reverse) | §8.6 adaptation and transplanting |
| Look up tuning/range/technique of Chinese instruments | **reference-minyue.md §7** |
| Folk score order, octave notation, section markings, lineup counts | **reference-minyue.md §8** |
| Look up Western instrument ranges/techniques/notation | **reference.md §2–§5** (this file does not contain the table of contents) |
| How to organize the string section internally: lineup size, line amplitude, seating and sectioning, four types of figuration, texture levels, pedal tones, multiple divisi, period models | **reference-yang-strings.md** |
| Criteria for woodwind combinations: three levels of blend effect and cost, line width and top-to-bottom ordering, harmonic linear writing, woodwinds with strings, separation and fusion, derived parts | **reference-yang-winds.md** |
| When brass is present, how the whole orchestra divides: lines and chords within the brass section, harmonic combinations across two or three groups, timbre allocation for texture elements, timbral layout for counterpoint and fugue, period defaults | **reference-yang-brass.md** |
| After the orchestration is set, what else can be added and how timbre is distributed over time across the piece: emphasis and ornament, dynamic gradations and sudden changes, dynamic counterpoint, echo and transitions, tutti, timbral rhythm, local vs global orchestral layout | **reference-yang-tutti.md** |
| Percussion: how many players, which instruments, striking points and techniques, pitched vs unpitched instruments, combinations within the section, entering the orchestra | **reference-percussion.md** |
| Harp, plucked/struck strings and keyboard instruments: whether a single instrument can be written and heard, what layer it carries in the orchestra, what it doubles | **reference-keyboard-harp.md** |
| Filling in the ARR-SPEC roster | §9 field mapping + §10 must pass after writing |

## Boundaries: what this skill does not cover

| Not covered here | Where it belongs |
|---|---|
| Frequency budgets, which parts compete for frequency, frequency masking | `mc-texture-layering` |
| When instruments enter and exit, energy curves | `mc-arrangement-arch` |
| Realistic drum/bass/guitar/keys playing and groove | `mc-rhythm-section` |
| How to build synthesizer timbres | `mc-sound-design` |
| Harmony itself (which chords to use) | `mc-harmony` |
| Voice leading, parallel fifths | `mc-counterpoint` |
| EQ, reverb, panning | Mixing; write the intent into `mix_intent` (`mc-mix-intent`) |
| **Instrument-by-instrument range tables, technique notation, transposition** | String section and harp in [reference.md](reference.md) §2.1–2.3 (color of arrangement methods in §2.3.6); woodwind section §2.4 (five arrangement patterns in §2.4.5); brass section §2.5; the four Chinese folk groups in [reference-minyue.md](reference-minyue.md) §7; percussion in [reference-percussion.md](reference-percussion.md); harp and keyboard in [reference-keyboard-harp.md](reference-keyboard-harp.md); the Yang Liqing combination-method system is in the four files reference-yang-strings / winds / brass / tutti |
| Instrument order in folk scores, section markings, octave notation, lineup counts | **reference-minyue.md §8** |

---

## 1. Required before starting

| Required | Question to ask |
|---|---|
| **① Role of this line** | Melody / bass / harmonic padding / texture / color / memorable hook? (use the role values from ARR-SPEC) |
| **② Pure timbre or mixed** | Do you want one instrument's individuality, or a new timbre? |
| **③ Register** | Specify the pitch-name range. "Middle register" does not count as filled in. |
| **④ Playing technique** | Sustained / staccato / plucked / with mute ... **this item determines blend, see §3.5** |

**Self-check**: once the four items are answered, you should be able to name a concrete lineup, not "strings plus woodwinds."

---

### 1.1 ★ Master switch: first decide the texture type, then decide whether to blend or separate

All the means in §2 through §6 take their direction from this step (Yang Liqing p0240–0241):

| Texture type | What it is | Orchestration principle |
|---|---|---|
| **Homogeneous** | Contains only one kind of element; all parts share the same character and presentation form (especially rhythmic shape): unison type, chord-tone cluster type, sectional-writing type | **Choral-style orchestration**: aim for maximum balance, fusion, and unity |
| **Heterogeneous** | Contains two or more elements of different character: counterpoint, melody with accompaniment, pointillism | **Timbral separation**: separate the elements by timbre, register, and dynamics; within each element, keep vertical timbral affinity |

For a homogeneous texture, ask three questions (p0241): does the chosen timbre fit the expressive intent of this passage; does the writing exploit the instrument's register, dynamics, and technique; and will the combined timbres actually fuse into one.
The goal of a heterogeneous texture is to strip the components apart in timbre and register, clarify what is primary and secondary, and arrange them into a three-dimensional structure of foreground, middle ground, and background (p0241),
with the endpoint being Mahler's "maximum clarity," or Schoenberg's "everything written on the page should be audible" (p0241).

★ **The most fundamental principle of melody-with-accompaniment texture is to mobilize every means to make the layers separate in timbre.**
Pop arrangements are almost entirely heterogeneous textures, so the "blending" discussed in this skill's §3 is used only **inside a single element**; **elements are not blended with one another**.
The six means of separation are in `mc-texture-layering` §3.4.

## 2. Pure timbre or mixed timbre

This is the first fork in orchestration, and **the two paths want opposite things**:

| | Pure timbre | Mixed timbre |
|---|---|---|
| What it wants | That instrument's **individuality** | A **new timbre** whose components cannot be heard |
| Cost | Limited volume and thickness | Individuality is worn away |
| Suited to | Lines that must be recognized (lead, solo, memorable hook) | Padding, needing thickness, needing an unfamiliar sound |

**Criterion**: if the listener should be able to say "that is an oboe," use pure timbre;
if the listener should only feel "a warm thickness," use a mix.

**Where this breaks down**: in pop/electronic arrangements this boundary is blurrier — synthesizer timbres are often themselves the result of mixing.
The decision still holds: **do you want the timbre to be identifiable or unidentifiable?**

---

## 3. Three forms of mixing

### 3.1 Unison blending

Different instruments play the same pitch — **the highest degree of blend**, and the components are hardest to tell apart; but whether they fuse depends on whom you pair. Doubling two instruments of similar timbre from the same section is most natural (e.g., VII-11, cor anglais + bassoon, Yang Liqing middle volume p0032). For cross-section pairings, first look for a **"contact point"**: traditional recipes such as bassoon + cello, clarinet/cor anglais + viola, flute/oboe + violin (p0033). Without a contact point, results tend to sound harsh. Stacking too many layers causes "neutralization" (§3.4), and mismatched playing techniques also pull them apart (§3.5).

### 3.2 Octave coupling (doubling at the octave)

★ **Who sits on top is not decided by the score order, but by which instrument is stronger in that register** (reverse-order combination, Yang Liqing middle volume p0046).
The clarinet is weak in its middle register, but above c² its "trumpet register" is full, bright, and powerful; the oboe in its low-middle register is far fuller than a clarinet in the same register.
So placing the clarinet an octave higher with the oboe supporting below sounds more vivid and forceful than the natural order.
Rimsky-Korsakov criticized this kind of arrangement as "muddled in register," and the author disagrees; Debussy even used reverse-order combinations purely for color.
**Method**: when doubling at the octave, first see which of the two instruments is stronger in these two registers, and place the stronger one in its strong position.

Instruments an octave apart. Theorists call this **"coupled" or "doubled" timbre**,
with **fusion weaker than unison blending** (p0039).

> **The instrument positioned an octave higher often serves to reinforce the overtones of the instrument below** (p0039).

This is the most important point about octave coupling: the upper instrument is not "yet another melody";
it is **lighting up the overtones of the instrument below**. So which timbre it should use depends on how bright you want the lower instrument to become.

**Example VII-17, Rossini, *Semiramide***: a series of octave couplings among different woodwind types alternating with pure timbres,
with color changes exceptionally rich, **and nearly every "coupled" timbral component clearly distinguishable** (p0039).
→ The "incomplete fusion" of octave coupling is not a flaw; it is a usable effect.

### 3.3 Combining different registers — "coloring"

When strings and woodwinds are **placed in different registers** and do not form any unison combination (p0039–0040):

- Strings are usually the dominant, leading timbre
- **But the woodwinds in the other register are generally not completely drowned out; they act to "color" the sound or add brightness**
- **This kind of writing is quite typical of the Classical period** (Example VII-18, Haydn, Symphony No. 94, IV, G major)

**Use**: when you want "you can't hear what was added, but the overall sound got brighter" — use this.

### 3.4 ★ The "neutralization" phenomenon: the more you add, the more ordinary the individuality becomes

This is the most counterintuitive and most often stumbled-upon principle (p0037):

> When register ranges are roughly equal, **the instrument with numerical superiority usually has a decisive influence on the total sound**.
> But in combinations of strings and woodwinds, sometimes **different kinds of woodwinds "neutralize" each other, dulling their individual timbral character and making them sound "ordinary,"
> which instead makes the strings (such as the second violins) sound very vivid and prominent**.

**Example VII-15, Mahler, *Symphony No. 1*, IV (B-flat major)**:
Ten woodwinds in unison with the second violins: **the woodwind timbres cancel each other out, setting off the vivid color of the second violins** (p0037).

**Practical meaning of this principle**:
- You may think that adding ten woodwinds will give you "a very thick woodwind sound," but what you actually get is "a flattened background" plus "a prominent string line"
- So **if you want to highlight one instrument, one method is to surround it with a crowd of instruments that will neutralize each other**
- Conversely: **if you find some part unexpectedly standing out, check whether the things around it are neutralizing each other**

**Self-check action**: after mixing, ask yourself — am I hearing "a new timbre," or "a bunch of flattened things with one poking out on top"?

### 3.5 Playing technique determines blend

> **When combining timbres from different groups, do not forget that each instrument's playing technique affects how fused its sound is** (p0038).

**Example VII-16, Schoenberg, *Variations for Orchestra*** (Presto ♩=120) (p0038):
- Bar 441: the flute is repeated by harp and glockenspiel. **Because the flute uses staccato articulation, its temporal transient character (attack and decay) is close to the decorative instruments, so the combination sounds reasonably harmonious**
- Bar 448: clarinet and harp **form a certain degree of sonic separation because of the difference in playing technique (= temporal transient character)**

**Core point**: whether instruments fuse depends on whether their **temporal transient characteristics** (the shape of attack and decay) are similar, not merely on whether their timbres are bright or dark.
A plucked harp and a staccato flute can blend; a sustained clarinet cannot blend with them.

**This principle holds equally for MIDI/synthesizers**, and more obviously so — see §7.

---

### 3.6 How a line changes color over time (Yang Liqing middle volume p0059–0063, lower volume p0327–0342)

§3.1 through §3.5 covered vertical mixing; this section covers **horizontal** mixing: how the same line changes color over time, and how the joints between them are handled.

**Four methods** (middle volume p0059–0063):

| Method | What it does | Key points |
|---|---|---|
| **Timbral juxtaposition** | Different timbres placed directly against each other, alternating | **Alternation must match the division of the phrase or motif structure** (p0059). In Beethoven's *Eroica*, the three-note motif passes through oboe → clarinet → flute → violin in linked succession, forming a rhythm of timbral change that finally leads into tutti (p0060–0061). This is also the basic principle of pointillist writing |
| **Layered addition and reduction** | Add one instrument per layer, or remove one | Not only changes timbral complexity but also produces gradual or sudden crescendo/decrescendo and expansion/contraction of line amplitude (p0061). Reduction is "peeling away layer after layer of cocoon until the clarinet shows its true color" (p0062) |
| **Timbral substitution** | On the basic coloration of a line, continually swapping in similar instruments with subtle differences to tint it | The amount and texture of color shift frequently and slightly; common after the Romantic era (p0062) |
| **Timbral modulation** | Using an **intermediary coloration** to move a line from A to B | The simplest method is to briefly overlap A and B, using that overlap as the medium (p0063) |

**Pop equivalents**: bringing in a pad by first layering an intermediate timbre and then removing the old one is timbral modulation; adding one more instrument each time the chorus repeats is layered addition; swapping instruments every four bars on the same riff is juxtaposition.

**Two types of joints for transitions** (lower volume p0336): the **overlapping type**, where the end and beginning of each segment stack on each other, and the **break type**, with no overlap. The former seeks gradual, smooth transitions; the latter seeks lightness and fluency or avoids accents caused by overlapping ends and beginnings;
both can be used within the same phrase. Fast passing phrases cut into small units always connect using the overlapping type (p0339).

**Techniques for concealing the seams** (p0339–0342): double two notes instead of one; offset the joint from the metric accent; cover the seam with a part that does not change. All three aim to strengthen the "unity" of each structural unit.

**Echo and answering phrases** (p0327–0331): answering occurs between motifs of identical or similar material, **with at least one contrast in timbre, register, or amplitude, and roughly equal dynamics and playing technique**.
Echo is a type of answering: **strong first, then much weaker, with a difference large enough to create a sense of space**, and the leading and following voices mostly use **the same kind** of timbre.
★ The most economical echo is **artificial reverberation**: use a long note in a weak-dynamic timbre to overlap the tail of a strong phrase, often producing a sudden drop in the manner of sfp (p0330);
having the echoing instrument enter early with p on the preceding beat and then sustain makes the sudden change sound natural (p0331).

### 3.7 Three types of combination and five types of varied combination (Yang Liqing middle volume p0150–0155)

§3.1 through §3.3 all covered **copying as-is**. What is really commonly used is layering something different:

| Type | What it does |
|---|---|
| Full combination | Different timbres completely overlap, producing a blended coloration |
| **Partial combination** | Only the most characteristic portion of a part (or even individual moments) is locally repeated by another instrument to emphasize it |
| **Varied combination** | The overlapping parts differ in construction to varying degrees |

The five types of varied combination (p0150–0151): **dynamic-characteristic variant** (same pitch and rhythm, but with a playing technique having a completely different temporal transient character, e.g., legato overlapping staccato), **simplified variant**, ornamental variant, rhythmic variant, and harmonic variant.

**How to do a simplified variant** (p0151): extract a number of skeleton tones from the basic part to form a "framework part" that always runs parallel to the main line while retaining some independent meaning,
giving clear outline to textures with large swells or complex shapes. Two rules:
- **The variant and the skeleton should use contrasting timbres**; if the timbres are similar, then playing technique and register must be separated (p0151, p0154)
- ★ **Mark the dynamic of a simplified variant one level lower**, or the whole thing sounds muffled (p0155)

In pop arrangements, "a pad that follows the broken chords" is a simplified variant; almost no one writes into the spec sheet the rule that the pad should sit one dynamic level below the arpeggio layer.

### 3.8 How harmonic layers of two instrument groups combine (Yang Liqing middle volume p0074–0079)

| Form | Method | Result |
|---|---|---|
| **Juxtaposed combination** | The harmonic layers of the two groups fully overlap, each with a complete harmony | Fullest and most dense, with good resonance (p0074) |
| **Partial overlap** | Group A is complete; group B doubles only the skeleton parts | **Group A's coloration dominates** (p0075); the reverse, with complete strings and partial horn doubling, is also common |
| **Layered combination** | Neither group is complete; each group's "harmonic plane" combines into the total harmony, and the planes may or may not adjoin or partly coincide | Least even; slight mistakes cause disharmony, **but when handled well the coloring is the most unusual** (p0078) |

In pop, how to stack the three layers of "string section + pad + brass" corresponds to these three forms. When writing the spec sheet, state which form is being used — especially for layered combination, check note by note for holes.

### 3.9 Five methods of emphasis: what to layer to make one spot heard

| Method | What it does |
|---|---|
| **Rhythmic emphasis** | In a layer carrying the basic rhythm, use another timbre to **periodically double its metric accents** (p0275); ★ offsetting the period of the emphasis from the period of the metric accents, so that logical and metric accents disagree, produces a sense of "weightlessness" and greatly increases rhythmic interest (p0277) |
| **Color emphasis** | In a passage founded on one timbre, use a contrasting timbre to **double only the most characteristic spots** (p0279). Dukas, *The Sorcerer's Apprentice*: muted strings set the basic tone; piccolo and flute articulate lightly on the skeleton tones; the motif is outlined by harp and soloist string harmonics |
| **Dynamic emphasis** | The high points of perceived loudness (melodic peaks, skeleton tones) are not necessarily the physical loudness peaks; layering another timbre on top emphasizes them (p0283–0284, see `mc-sound-design` §3.6) |
| **Structural emphasis** | Use a contrasting timbre to double and outline the **most individual portion** in the structural shape of a phrase or motif, making its contour clearer (p0286) |
| **Emphasis of sonic dynamics** | Layer a timbre with a fast attack over a slow-attack layer to reshape its onset (p0287, `mc-sound-design` §3.6) |

**Usage**: once the spec's "protagonist sequence" states who is the protagonist of a passage, answer one more question: **which of the five methods is used to layer it**. If none of the five is used, the protagonist can only rely on pushing dynamics, which is the weakest tier described in §4.

★ An extreme form of rhythmic emphasis (p0276): irregular accents in the string layer are reinforced by a group of horns with sf, giving the passage an alternating 2/4, 2/8, 6/8, 3/8 effect, and the emphasis itself is elevated into a "rhythmic theme."

## 4. Balance: number and register

**Basic rule** (p0037): **when register ranges are roughly equal, the instrument with numerical superiority has a decisive influence on the total sound.**

But "number" should be counted by the actual lineup, not by the number of parts:

| | Standard symphony orchestra |
|---|---|
| First violins | about 16 players |
| Second violins | about 14 players |

> So **a double-stop passage that is difficult for a single player becomes quite simple in the orchestra when played in divisi (divided parts)** (p0067).
> — This is a convenience unique to the string section: a double stop that cannot be written can simply be split into two parts.

**Self-check action**: are you computing balance by "how many lines" or by "how many people are playing"?

### 4.1 ★ A principle that comes before number: register must match

Number is only the second principle. The first is that **instruments should sit in registers of matching dynamic strength; if both are in strong registers or both in weak registers, balance is easier to achieve** (Yang Liqing middle volume p0021):

| Combination | Result |
|---|---|
| Flute + bassoon | Registers not matched; **the bassoon sticks out whether played loud or soft** |
| Oboe + clarinet | Acceptable when loud; when soft, the oboe is too strong |
| Oboe + bassoon | Registers roughly equal; blends evenly at both loud and soft |

Add one more point: in harmonic combinations, **instruments with rich overtones and strong individual timbre will stick out even at equal volume** (p0021).
"Balance is only a relative concept," and most textures do not require absolute balance (p0021).

### 4.2 Horizontal balance: at a handoff, the next instrument must be able to carry on from the previous one

Balance is not only vertical; there is also the question of whether **the loudness of a line can carry on as it passes from one instrument to another** (p0021–0023).
The book's estimates: the first violin section is about 83.5 dB, a flute solo about 72 dB, and a2 reaches only 75 dB (p0022).
So a flute in the low register cannot take over the momentum of a bassoon (above 80 dB); switch to an oboe or clarinet to pick it up.
If an oboe hands off downward, you also need to switch to flute or clarinet, otherwise the line shows a loudness break at the joint (p0023).
**Method**: before writing a transition, compare the loudness of the two instruments in the register of the joint; the receiving instrument must not be a full dynamic level weaker than the one handing off.

---

For how a tutti becomes loud, and the character of each of the five types of tutti, see `mc-arrangement-arch` §2.4.

## 5. Three conditions for letting one group project through

A woodwind passage that cannot be heard is the most common orchestration failure. Sibelius's *Symphony No. 2*, I, provides a positive example (p0040) —
**the woodwind colors clearly project through the total sound**, for three reasons, none of which can be missing:

1. **The number of woodwind instruments is increased**
2. **A combination of octave coupling and unison blending is used** (not a single technique)
3. **The highest-layer flute sits in its strong register, sounding exceptionally vivid and luminous**

**Item 3 is the easiest to overlook**: the same instrument in a different register can differ in projecting power by an order of magnitude. See §6.

---

## 6. Register is character

**The same instrument in different registers is effectively a different instrument.** Taking the violin's four strings as an example (p0065–0067):

| String | Character |
|---|---|
| **G** | The thickest of the four strings, with the roundest and lowest sound. **When moved to high positions, the sound becomes very tense**, because the vibrating length keeps shortening |
| **D** | Adler: the timbre may be the **least distinctive** of the four strings, but it contains warmth and lyricism, becoming richer when moved to higher positions. ★ Yang Liqing (p0129) says the opposite: among the four strings it **sounds sweetest and most moving**, soft and bright when played softly, with a "noble, poetic charm" (as Casella put it). Specifying the D string usually aims for a sturdier, richer timbre than the A string. The two accounts are placed side by side; per this library's convention, no ruling is made |
| **A** | **Its character is most distinct in first position**; high positions lose some brilliance and strength and suit softer, lyrical playing. For brilliance in the high register, move to the E string |
| **E** | The **most brilliant** string, with an extremely bright extreme top of range; but **even when played softly, it can reveal a quiet, mysterious quality** |

**Notation for specifying which string**: `sul E` / `sul A` / `sul D` / `sul G` (p0065).

**When to specify and when not to** (p0065):

> When a note can be played in several positions, **it is entirely pointless to dictate in which position the performer must play it**.
> If the composer knows the instrument's fingerings well, exact fingerings may be marked in the score and parts to obtain the desired timbre.
> Otherwise, **fingering is best left for the performer to decide**.

**Special nature of open strings** (p0065):
- Open strings are free of finger control, so **their vibrating potential is greater**
- In fast passages, mixing open and stopped strings does not produce dissonance
- **But in slow, expressive passages, one usually wants all notes to have the same timbre, or the open-string notes will stand out unduly**
- Example: Brahms's *Symphony No. 1*, IV, bars 61–75 lie entirely on the G string; "pay attention to the vibrating sound created by the open G string"

**Generalization**: this logic is not limited to strings. Every instrument has a "strong register / weak register / register-change point."
**Before writing, ask what state this instrument is in at this pitch.** For specific range tables, see reference.md.

---

## 7. MIDI orchestration: what changed and what did not

**What did not change**: everything in §2–§6 still holds. Neutralization, playing technique determining blend, and register as character
all occur in sampled sound as well, because samples are recordings of real instruments to begin with.

**Four things that changed**:

| | |
|---|---|
| **① No automatic correction by players** | Real players adjust intonation and balance on their own; samples do not. So balance problems in orchestration will be **exposed as-is** in MIDI |
| **② Playing technique must be switched explicitly** | Staccato/legato/pizzicato is a single phrase in a real orchestra, but in MIDI it means switching articulations or timbre layers. **The difference in blend described in §3.5 you must create manually** |
| **③ The convenience of divisi disappears** | In a real orchestra, divisi is easy; in MIDI, 16 violins are one sample. To get the thickness of divisi, use multiple instances plus slight differences |
| **④ Open strings, positions, and string changes do not exist** | The string character system in §6 is typically not distinguished in sample libraries. **To get the tension of sul G, you can only choose a timbre layer or use a solo sample** |

**Practical criterion**: when MIDI sounds "fake," the cause is usually not insufficient timbre quality, but
**the decisions that real players would make have been omitted**: dynamic shaping, changes of playing technique, register choice.

> For detailed MIDI orchestration methods, see [reference.md](reference.md) §5: §5.1 CCs used in orchestration; §5.3 checklist for making samples come alive (layering and CC#1 crossfades, two recording methods for keyboard switching, dry/wet ratio for layered timbres, one real instrument per group, CC#7/CC#11 envelopes, velocity to attack and filter, quantization start points, natural noise).

---

## 8. Chinese folk orchestra: differences from the Western orchestra and orchestration principles

**The mechanisms in §2–§6 apply equally in a Chinese folk orchestra, but the instruments differ, so first reverse four things in your thinking.**
Citations in this section: page numbers without a book title refer to Yang Chunlin's *Tutorial on Orchestration Method for Chinese Folk Orchestra*; Zhu Xiaogu and Li Minxiong are cited separately.

| Difference | Consequence |
|---|---|
| Four groups: winds / plucked / bowed strings / percussion; the plucked group has no counterpart in the Western orchestra (p0012–0013) | Adds a whole group of "point-like" sound sources; blending points with lines is the central tension of folk orchestration |
| Bowed-string instruments of the huqin family: **the higher the register, the more volume and dynamic are lost** (the membrane cannot reach high-frequency vibration) (p0038) | The Western intuition that "higher is brighter" fails; do not rely on writing the erhu high to build a climax |
| Bangdi, qudi, and high-pitched suona are **notated an octave lower**; the bass beidihu is notated an octave higher (p0352) | Flute harmonies that look "not high" on the page are actually very high (p0162); think in **actual pitch** when orchestrating |
| Commonly used total range: seven pitch groups spanning six octaves, from the lowest E (beidihu) to g³ (G-key bangdi) (p0351) | Narrower than a symphony orchestra; in the low register the bowed strings of the folk orchestra are "helpless" and need plucked instruments to help (p0442) |

**Terminology**: the same melody stated at the same pitch is called a **single group**; one octave apart is a **double group**; two octaves apart is a **triple group**... Whatever the number of groups, the texture is always **monophonic** and must never be understood as parallel octaves (p0045).

### 8.1 Character and register of the four groups

| Group | Character | Register notes | Self-check |
|---|---|---|---|
| **Bowed strings** | The foundation of the ensemble; linear, the most singing of the groups (p0026, p0072). Gaohu, erhu, and zhonghu are vibrating membranes, while cello and double bass are vibrating plates, so unison combinations are not timbrally uniform (p0037) | The erhu's best register lies within the treble staff without added ledger lines (p0040); the gaohu takes the high part and is slightly nasal in its low register (p0034); the zhonghu takes harmony, and its register should not be high or it loses its fullness (p0041); the zhonghu's lowest note is only G, so the whole group lacks a sub-middle voice (p0057, p0061) | Four-part allocation: gaohu = high, erhu = middle, zhonghu = sub-middle, dihu/beidihu = bass; the zhonghu layer is the "waist" of resonance (p0056–0057). Gaohu, erhu, and zhonghu **can only play single notes** (at most parallel fifths) (p0051); polyphonic passages must use div.; after dividing, the overall volume drops, which suits soft playing and harmonic color, so do not divide for loud passages (p0054) |
| **Plucked** | Dot-like sound (p0275); its range is generally wider than the bowed strings: "the bowed strings hold the timbral advantage, the plucked hold the range advantage" (p0224). The timbre splits into two groups: liuqin + yangqin + zhongruan are tight and straight, while pipa + guzheng are loose and crisp (p0094) | Liuqin takes the high part, pipa the middle, yangqin high-middle, zhongruan middle, daruan bass (p0074–0088); full-group harmony: daruan low, zhongruan and yangqin middle, pipa/guzheng/liuqin high (p0119); yangqin works in every register and is best suited to harmony (p0120) | Within the same melody, **plucking and rolling must be consistent**; mixing them causes confusion (p0092); for repeated notes use "one pluck, one roll" (p0093). The guzheng is tuned to a pentatonic scale; in vertical chords avoid accidentals as much as possible, and horizontal use is acceptable but not at fast tempos (p0118). Pipa and yangqin repeating a three-note figure in the same pitch group do not sound good (p0120) |
| **Winds (blown)** | The orchestra's timbral palette and source of momentum; almost always present at the climax (p0133). The sheng can sound multiple notes and sounds on both inhalation and exhalation, making it the orchestra's "blending agent" (p0132–0133). Suona timbre is very hard to blend with other instruments (p0281), and one suona has the decibel level of sixteen erhus (p0415) | The bangdi's middle register is best, its low register is breathy, and its top two notes are sharp (p0136); the qudi is good in any register (p0150); the xindi (new flute) is an octave lower than a bangdi in the same key, has no membrane, and has an intrinsic timbre (p0138, p0150); the high sheng sounds most beautiful from d¹ to d³ (p0150); the low sheng melody should not exceed g¹ (p0151); the high suona sounds good in the low-middle register, and **lowering its register actually works better** (p0152); the middle suona's timbre is not pleasant, so use more repetition and harmony (p0143) | The flute group has no bass, so its harmony can only be colorful harmony; do not write it thick (p0162, p0267). Suona harmony requires "extreme caution": its reeds are unstable, and its middle-low register already counts as a high register in the orchestra (p0162); the harmony register of the high suona should be notated no higher than #c²/d² (p0165). Bamboo flutes: one flute per key; the score must specify which key of flute is used and when to change flutes (Zhu Xiaogu p0014) |
| **Percussion** | No fixed setup; assembled according to the needs of the piece (p0192); dynamic range much larger than the other groups (p0288). Chinese percussion is **used forcefully and overtly**, Western percussion is **used lightly and covertly**; the Chinese-to-Western instrument ratio is about 2:1; the number of players should not exceed one-tenth of the orchestra (p0220) | Timpani is used most often and governs accent and momentum (p0192); yunluo sounds best in the middle register (p0206); muyu works for almost every lively rhythm (p0211); snare drum and marimba clash with folk style, so use them sparingly (p0178, p0217) | Four principles: use only when truly needed; when several instruments play together, avoid mutual cancellation; play only to "set off the clouds to highlight the moon" (a supporting role); give more consideration to doubling (p0289). Unpitched percussion does not create compound timbres with bowed strings; it simply reveals itself as it is (p0292) |

### 8.2 Combining groups: who works well with whom

**Who dominates in unison combinations**: when bowed strings + plucked, or bowed strings + winds are in unison, the timbre is **led by the bowed strings** (p0256, p0281). The exception is suona: one suona against a group of gaohu still stands out clearly (p0281).

| Combination | Good | Poor / conditions |
|---|---|---|
| Bowed + plucked | Erhu + pipa, zhonghu + zhongruan, dihu + daruan: most practical and most frequently used (p0228, p0231, p0233); gaohu + liuqin in the high register is the friendliest (p0226). Principle: **combine instruments of the same register** — zhonghu with zhongruan rather than liuqin, since the thickness is similar (p0235) | Gaohu + pipa is neither high enough nor low enough to fit (p0227); gaohu + guzheng and zhonghu + liuqin are impractical (p0228, p0231) |
| Bowed + winds | Bowed strings soften and beautify the wind timbre; the winds increase the volume of the bowed strings and strengthen their resilience (p0267). Dihu + bass sheng is most practical (p0260) | Winds are louder than plucked, so balance must be calculated first (p0267); suona is calculated separately (p0256) |
| Plucked + winds | Liuqin + bangdi, pipa + high sheng, zhongruan + middle sheng, daruan + bass sheng (p0273); with a sheng section, harmony is "very convenient" (p0275) | The difference between dot and line is the key point (p0275). Liuqin cannot play the flute's downward glissando: omit the falling note, or switch to rolled playing (p0271) |
| Percussion + each group | Like plucked, "both are dots," so it fuses most easily (p0292); with winds the volume can be balanced, "a match made in heaven" (p0295) | With bowed strings, balance is key (p0292) |

**Pitfalls of cross-group octave coupling**: bowed strings (lines) and plucked (dots) coupled at the octave produce a very obvious timbral difference. The solution is to **use a compound timbre in each pitch group**: first group gaohu + liuqin, second group erhu + pipa (p0240). Bowed + winds works the same way: gaohu + qudi / erhu + xindi (p0263). **Failure condition**: you specifically want the effect of separating dot from line.

### 8.3 Full lineup: how to divide melody, bass, parts, and accompaniment

The three categories of section division (harmonic, attached, and contrasting), the six criteria for whether the plucked group should be divided, the five patterns for statements of harmony, and the eight pairings of single- and double-timbre groups are in [reference-minyue.md](reference-minyue.md) §8.4.1–8.4.3.

- **Melody**: three modes — a single group states it, two groups state it jointly, or three groups state it together. The other groups do not state the melody but **must not be absent**; only unpitched percussion may be an exception (p0302–0303). The melody is least easily swallowed in the high register, but the high register of bowed strings and plucked in the folk orchestra is relatively thin (few gaohu), so extra instruments are often needed (p0414–0415). In the middle register the melody is an inner voice, and the other parts must yield that register (p0415, p0451).
- **Layered harmony**: each group keeps a consistent high/middle/low harmonic structure: high = flute group, high suona, liuqin, pipa, yangqin, gaohu, erhu; middle = sheng, middle suona, ruan, zhonghu; low = bass sheng, bass suona, daruan, dihu, beidihu (p0352). Stacking: **dense on top, sparse below, never empty in the middle**; the D–d sub-middle register and the G–g middle register determine the resonance (p0375, p0451). Dense voicing is for loud passages and for instruments of the same type; open voicing is for soft coloration and different instruments (p0375). Do not repeat three-note figures; in seventh chords, do not reuse a pitch above one already used in the bass (p0375). **Self-check**: is the sheng, ruan, zhonghu layer empty?
- **Bass**: bowed strings: dihu/beidihu; plucked: daruan; winds: bass sheng/bass suona. Sheng and suona can only be lines, while hu and ruan can be lines or dots (p0336). The lowest note of the daruan is a major second above that of the dihu, and the bass suona is a fifth higher (p0336). Bass sheng must be arranged according to the harmonic series, otherwise it sounds "muddy" (p0140). Dihu bowed and beidihu plucked can serve as a "dot-line bass" (p0062). When the dihu plays the melody, the beidihu must be at least a fifth away from it (p0062).
- **Accompaniment**: rhythmic harmony generally uses eighth notes (quarter notes cannot produce the pulse), often played by high sheng, middle sheng, and zhongruan (p0359). Plucked instruments use sixteenth-note harmony to avoid the muddy, stiff quality of block chords (p0361). "Assigning harmony by instrument group" (winds on the melody, plucked or bowed strings on the harmony) is standard practice (p0370).
- **Section division and markings**: two same-type winds use a²/I/II (p0347). The sheng is generally not divided and is marked solo or tutti (p0348). Plucked double stops are generally not marked div., and yangqin is not divided (p0348). Bowed strings use div./unis., and solo/soli/tutti appear in pairs (p0348). Dihu double stops must be marked div. or non div. (p0349).

### 8.4 Treatments (each with a self-check)

| Treatment | Key points | Self-check |
|---|---|---|
| Balance | The melody must be clear; the harmony should be neither too thick (muddy) nor too thin (dry and harsh) (p0414–0415). The same dynamic marking produces different loudness on different instruments, so set dynamics per instrument (p0413) | Did you account for the volume drop after dividing? |
| Emphasis | All instruments other than the melody help with accents (p0416) | Did you rely only on dynamic markings? |
| Transition | The melody changes instruments within a single line to compensate for the folk orchestra's limited range; the receiving instrument **enters early**, and the handing-off instrument plays one extra note (p0418) | Is there overlap at the handoff point? |
| Growth / reduction | Mnemonic: "strings first, then plucked, then winds, finally percussion" (p0421). Decrescendo relies on dynamics plus fewer parts (p0421) | Did you push all crescendos and decrescendos onto the conductor (p0450)? |
| Sonic momentum | Short, propulsive drive from ornaments, rolls, and scrapes (p0422) | |
| Dialogue, call-and-response / timbral juxtaposition | Folk "antiphonal phrases"; the same material passed between groups in turn (p0424–0427) | |
| Supplementation | Temporarily add a part, or give a cadence a "brake" (p0428–0432) | |
| Retention | Do not use that timbre before an important melody enters; when the melody is in the middle-low register, other parts yield (p0451) | |

Li Minxiong adds two points: the "rhythm" of timbral change must match the division into motifs, phrases, and sections, and developmental and dramatic passages should be varied (Li Minxiong p0097). Each passage establishes one **dominant timbre**, with other changes revolving around it (Li Minxiong p0100).

### 8.5 Solo instruments within the ensemble

- Definition: a single instrument playing alone, with no part in the score identical to it (p0394). There is only one principle: **ensure the soloist is clear and not swallowed** (p0410).
- Five methods (p0411): keep the accompaniment at low volume; keep the accompaniment register away from the soloist's register; use an accompaniment timbre of a different type from the soloist (plucked accompanying bowed, winds accompanying plucked); use register contrast (a bass solo with a high accompaniment); use an accompaniment rhythm different from the solo's.
- By instrument: suona and bangdi are not easily covered; the sheng needs its accompaniment reduced; be careful with a liuqin solo in the low register; the zhongruan is hard to make stand out and sounds poor in the high register, so use its middle register; for an erhu solo, accompaniment mostly uses plucked instruments; for a zhonghu solo, avoid its register in the accompaniment (p0410).
- Four contrasts for concertos: timbre (if the soloist is suona, do not accompany with suona), register (leave space for the soloist), rhythm, and dynamics (p0412–0413).

### 8.6 Adaptation and transplanting

- **Adaptation** = melody only, with the full score written out; **transplanting** = an existing score moved to a different ensemble without changing harmony or texture, with the key possibly changed in special cases (p0440). Adapting traditional instrumental masterworks **must not change the key** (p0440).
- Transplanting: check range before key (p0441). Violin ↔ liuqin coincide fully; pipa below c³, yangqin below g³, guzheng below d³, and gaohu above g¹ coincide (p0441). Oboe → high sheng is best; clarinet → middle sheng; bassoon → bass sheng; trumpet → high suona (mind the octave notation difference); horn → middle sheng; harp → guzheng (or yangqin if there are many accidentals) (p0444–0447). **Flute parts cannot be given directly to the bamboo flute**, because the bamboo flute is notated an octave lower (p0444).
- Layout: the most suitable keys lie between two flats and three sharps (p0449). *Huahao Yueyuan* (Flowers Bloom, Moon Full) uses G major rather than D major so that the whole orchestra "brightens" (p0449). Follow the principle of the best range; do not keep writing the huqin higher and higher (p0450). Use unison tutti and maximum dynamics sparingly (p0450). Harmonic rhythm should be broad, and adding non-chord tones to broken chords dilutes the "Western flavor" (p0451–0452).

> For instrument-by-instrument tuning, range, technique, score order, and transposition conventions, see reference-minyue.md §7–§8.

---

## 9. Field mapping to ARR-SPEC

| Field | Section of this skill |
|---|---|
| `arrangement.roster[].instrument` | §2 pure/mixed → §3 forms; for folk, see §8.1 four groups + reference-minyue.md §7 |
| `arrangement.roster[].role` | §1 required ①; for folk melody/bass/layered harmony/accompaniment assignment, see §8.3 |
| `form[].melody_register` | §6 register is character; for folk, fill in **actual pitch**; for instruments with octave notation, see reference-minyue.md §8.3 |
| `roster[].midi` (GM number) and `render.midi.instrument_map` (VST notes) | §7 |
| Lineup size (how many people, how many instruments) | §8.1 + reference-minyue.md §8.2 lineup table |

**Not filled by this skill**: `roster[].band` (→ `mc-texture-layering`),
`roster[].entry/exit` (→ `mc-arrangement-arch`).

---

## 10. Must pass after writing

- [ ] Every line can state its **role** and **why this instrument**
- [ ] Wherever instruments are mixed, you can state whether it is **unison / octave coupling / different pitch groups**
- [ ] Wherever octave coupling is used, you can state **what the upper instrument is lighting up**
- [ ] **Neutralization** has been checked: the mix produces a new timbre, not a bunch of flattened things with one poking out on top
- [ ] **Playing technique is filled in**, and the temporal transient characteristics of the instruments that fuse are similar
- [ ] Each instrument's register is specified **to the pitch name**, and you have confirmed what state it is in at that register
- [ ] Balance was calculated by **number of players**, not by number of parts
- [ ] For MIDI: decisions have been made on dynamic shaping, playing-technique switching, and register choice; none were left to defaults

**For Chinese folk orchestras, add these items**:

- [ ] All four groups **are present** (only unpitched percussion may be absent), and you can state whether the melody is stated by one group, two groups, or three groups
- [ ] The **middle voices (sheng, ruan, zhonghu) are not empty**: stacking follows "dense on top, sparse below, never empty in the middle"
- [ ] Each instrument has been checked against its **actual pitch**: bangdi, qudi, high banhu, jinghu, high suona, and haidi are notated an octave lower; beidihu, leiqin, and timpani are notated an octave higher; zhongruan and traditional suona must state which notation is used
- [ ] Bamboo flute and suona parts **state which key of instrument is used**, and points where the instrument changes mid-passage are also marked
- [ ] The huqin has not been written higher and higher (volume and dynamics drop as the register rises); climaxes do not rely on writing the erhu high
- [ ] Section markings come in pairs: `div.` with `unis.`, `solo`/`soli` with `tutti`; dihu double stops are marked `div.` or `non div.`
- [ ] Stylistic techniques (glissando, flower-tongue, sweep rolls, strike sounds, and the like) are marked in the score, and consistent within each part
- [ ] Adaptation/transplanting: range was checked before choosing the key; traditional instrumental masterworks **keep their key**

---

## Appendix: sources and conventions

- Yang Liqing, *Tutorial on Orchestration* (three volumes): the overall combination-method system is organized as follows: upper volume Chapter 4, string combinations → reference-yang-strings.md; middle volume Chapter 7, woodwind combinations → reference-yang-winds.md; middle volume Chapters 8–11, percussion, plucked strings, and keyboard → reference-percussion.md and reference-keyboard-harp.md (paired with the corresponding chapters of Adler's upper volume); lower volume Chapter 14, brass and multi-group combinations → reference-yang-brass.md; Chapters 15–16, color enhancement, tutti, timbral contrast, and layout → reference-yang-tutti.md. The beginning or end of each file states which content is explicitly excluded.

- **Yang Liqing, *Tutorial on Orchestration*** (upper / middle / lower volumes): the backbone of §3, §4, and §5.
  The middle volume covers blending and texture and is the volume this skill cites most. Example numbers such as `Ex. VII-15` follow that book's numbering.
- **Samuel Adler, *The Study of Orchestration*, 3rd edition** (upper/lower) — the backbone of §6 and reference.md.
- **Pejrolo & DeRosa, *Arranging Manual for Modern Musicians*** (Chinese translation) /
  *Acoustic and MIDI Orchestration for the Contemporary Composer* (English original) — §7.
  The English original has a text layer; when quoting the original text, refer to the original edition.
- **Yang Chunlin, *Tutorial on Orchestration Method for Chinese Folk Orchestra*** — the backbone of §8.
  Also the lineup tables, score templates, octave notation, and section markings in reference-minyue.md §8. Page numbers in §8 without a book title all refer to this book.
- **Zhu Xiaogu, *Instrument Technique for the Chinese Folk Orchestra*** —
  instrument-by-instrument tuning, range, technique, and notation in reference-minyue.md §7.
- **Li Minxiong, *Score Writing for the Chinese Folk Orchestra*** —
  the color changes and dominant timbre in §8.4, and in reference-minyue.md §8 the score-writing order, the division of labor between harmony and polyphonic orchestration, and the five methods of percussion scoring.

**Convention**: page numbers refer to the scanned pages of the corresponding book. Instrument-by-instrument range tables, technique notation, and transposition methods are all in [reference.md](reference.md),
this file contains only the decision layer.
