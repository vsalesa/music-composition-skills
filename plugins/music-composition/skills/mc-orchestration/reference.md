# mc-orchestration Reference: Instrument Technique Navigator and MIDI Orchestration Quick Guide

> Instrument technique is a subject you look things up in. `SKILL.md` covers orchestration decisions; this file holds the things you can look up:
> bowing and the hard constraints of each instrument, the arrangement methods for orchestrating strings, and a quick guide to MIDI orchestration.

---

## 1. Which book to consult

| What you need | Where to look |
|---|---|
| The range, fingerings, and whether a given passage can be played on an instrument | **Adler vol. 1** (`adler-orch-1`) |
| How to assign a passage to the orchestra; adaptation principles | **Adler vol. 2** (`adler-orch-2`), from Chapter 15 onward |
| The mechanics of mixed timbre, color contrast, tutti | **Yang Liqing, *Tutorial on Orchestration*, middle volume** (`yang-orch-2`) |
| Credible orchestration using MIDI / sample libraries | **Pejrolo, *Acoustic and MIDI Orchestration*** (`pejrolo-en`, `pejrolo-midi-orch`) |
| **Tuning, range, technique, and notation of Chinese folk instruments** | **Zhu Xiaogu, *Instrument Technique for the Chinese Folk Orchestra*** → §7 of this file |
| **Instrument order in folk scores, octave notation, section markings, and the scoring workflow** | **Yang Chunlin, *Tutorial on Orchestration Method for Chinese Folk Orchestra* / Li Minxiong, *Score Writing for the Chinese Folk Orchestra*** → §8 of this file |

> ★ The division of labor among the three: **Adler teaches what an instrument can do, Yang Liqing teaches what it becomes when combined, and Pejrolo teaches how to realize it with machines.**
> This library uses Pejrolo as its path to implementation, because our output goes through MIDI/generation back ends, not live orchestras.
> The same applies on the folk side: **Zhu Xiaogu teaches what an instrument can do, Yang Chunlin teaches what combinations become, and Li Minxiong teaches how a score is put onto paper.**

---

## 2. String and woodwind sections: bowing, individual instruments, orchestrating strings and winds (Adler vol. 1)

### 2.1 Bowing: choose by what you want (Chapter 2, p0028–p0045)

Bowing determines **the shape of the attack**, and the shape of the attack determines blend (`SKILL.md` §3.5).
So bowing is not the player's concern; it is an orchestration matter: with the same two instruments, changing the bowing changes whether they blend.

#### 2.1.1 Bow on the string (p0033–0037)

| Bowing | What you get | What to watch for |
|---|---|---|
| **Legato** | All notes within a slur are played in one bow, with consistent bow direction (p0030) | The longer the line, the more the bow must sustain. See the load problem below |
| **Détaché** | One note per bow, with no break between notes, only changes of direction | The default state. If nothing is written in the score, this is it |
| **Playing near the tip / near the frog** | Tip: light and clear; frog: heavy and rough (p0033–0034) | If you want a certain weight, specify the bow position; do not count on the default |
| **Staccato** | Several short, separated notes within one bow (p0037) | ★ **Has a speed limit.** Beyond a certain tempo the bow must leave the string, and at that point it is a jeté, not a staccato bow |
| **Détaché staccato** | Short notes that are crisp, light, and gentle; the slur is dropped and détaché is marked instead (p0037) | Mostly played near the tip; long notes usually use an up-bow |
| **Martelé / Martellato** | Each note carries a hard attack | Use it when you want a "bite" |

★ **Slow, long slurred lines are the easiest place to write something that fails** (p0032–0033).
Even with soft dynamics, slow passages overload the bow and it cannot pull through; cellos and double basses suffer most, because their bows are shorter than those of the violin and viola.
**The solution is to divide the players into groups that use different bowings in relay**, giving the ear a very long continuous line while no single bow is overloaded.
This is the standard treatment for "long sentences that cannot be written," and it follows the same reasoning as the register layering in §2.3.2.

#### 2.1.2 Bow off the string (p0038–0040)

| Bowing | What you get |
|---|---|
| **Conscious spiccato** | Spiccato controlled actively by the player; the grains are clear |
| **Natural spiccato** (Saltando) | The bow bounces on its own elasticity; faster, with lighter grains |
| **Slurred spiccato** | Continuous spiccato played within one bow |
| **Jeté / Ricochet** | The bow is tossed down and rebounds to produce several notes in a row; the most granular quality |
| **Arpeggiando** | One bow crosses strings to roll out an arpeggio |

Spiccato is divided into three types by speed and dynamics (p0038). **Which one to choose depends on how much granularity and how much control you need**;
the more natural the grain, the less controllable it is.

#### 2.1.3 Coloristic bowing (p0041–0045)

- **Trills** (p0041)
- **Tremolo** comes in two kinds (p0042): **bowed tremolo** (rapid back-and-forth bowing on one note) and **finger tremolo** (rapid alternation between two notes).
  They sound completely different, so you must specify which kind you want
- **Note-value effects that resemble tremolo** (p0043): writing specific note values instead of a tremolo sign produces a controllable density
- **Unconventional bow positions** (p0044–0045): playing over the bridge or with the stick are timbral effects, not dynamic effects

#### 2.1.4 Two rules that can ruin the effect

1. **Finger glissando given to a whole section becomes muddy** (p0028). Written glissandos (with each note marked) are clear only when played by a soloist or a few players; if the whole string section plays them together, the result is a blurred, confused glissando.
   If you want that effect, you can have it, but if you do not, do not give it to the whole section.
2. **A staccato that is too fast turns into something else** (p0037). If a staccato is marked at a tempo that is too fast, the player can only bounce the bow off the string,
   what you get is the granularity of a spiccato, not the separated quality of a staccato.

#### 2.1.5 Pizzicato, mutes, scordatura, harmonics (p0046–0063)

**Pizzicato**

- **The thicker and larger, the longer it sustains**: string thickness and instrument size determine the volume and sustain of pizzicato; the double bass has the longest sustain of the family (p0046).
  If you want pizzicato to "hold," go lower; pizzicato in the high register is essentially a dot.
- ★ **Transitions are asymmetric**: moving from bowing to pizzicato is easy, but moving back from pizzicato to bowing is hard, because the hand must return from the frog to the standard position (p0046).
  **Plan an up-bow before a pizzicato so that the hand stops right at the frog and the return to bowing is smooth.** This is an arrangement the orchestrator should make, not something the player must handle.
- `pizz.` and `arco` must be written in both the full score and the parts (p0046).
- **Pizzicato chords default to a slight arpeggio**, because the fingers sweep from the lowest string; if you do not want this effect, write `non arpegg.` (p0049).
- **Long passages of fast pizzicato cause fatigue** (p0049). When writing long passages, know that the player may need to alternate two fingers, and do not push the density to the limit.
- To make a note ring as long as possible, mark `l.v.` (let vibrate) (p0049).
- Left-hand pizzicato is marked `+`, common in solo and chamber music, often on open strings (p0048);
  pinched pizzicato, marked `o`, and fingernail pizzicato, marked `∩`, are twentieth-century practices (p0048).
- After using special techniques such as playing with the stick or over the bridge, **you must state where to return to normal** (`normale` / `naturale` / `in modo ordinario`) (p0046).

**Mutes** (p0051–0052)

`con sordino` to put on, `senza sordino` to take off; usable across the whole family.

★ **The most useful point: adding a mute does not mean you can only write soft.** The tone quality is completely altered,
and writing loud or very loud passages with mutes produces a **restrained, compressed, tense** sound. This is the real compositional value of mutes;
using them only to "make it softer" is a waste. Allow time for both putting them on and taking them off.

**Scordatura** (p0052–0054)

Changing the pitch of the open strings serves three purposes: easing the playing difficulty of distant keys, obtaining chords that cannot be played in standard tuning, and changing the timbre.

- The **beginning of the full score and parts, and each point where the tuning changes**, must state the tuning of all four strings, with time allowed for restoration after the passage ends (marked `accord` / `accordatura`)
- Examples in both directions: Stravinsky lowered the cello's A string to G♯ at the end of *The Rite of Spring*, otherwise the final chord cannot be played (p0054);
  Mahler raised all four violin strings by a whole step, and the change in tension shifted the timbre away from the nobility the violin normally has (p0053).
  **The latter uses scordatura as a timbral resource, not as a technical convenience**

**Harmonics** (p0054–0056)

Touch the node lightly rather than pressing down, so the harmonic separates from the fundamental.

| Partial | Touch point (string length) | Reliability |
|---|---|---|
| 1st | Open string | Fundamental |
| 2nd | 1/2 | Octave higher |
| 3rd | 1/3 or 2/3 | |
| 4th | 1/4 or 3/4 | |
| 5th | 1/5, 2/5, 3/5, 4/5 | ★ Only 1/5, 2/5, and 4/5 are reliable enough for the orchestra; 2/5 is mainly for solo and chamber music |

- **The first six partials are the most stable.** Higher ones (up to the 7th and 8th partials) are easier on viola, cello, and double bass, because their strings are longer and thicker (p0055)
- **Two points of notation**: add a small circle above the note that is to produce the harmonic, then use a diamond notehead to show the pitch of the touch point (p0056)
- ★ **You must specify which string**, because the same harmonic pitch can be obtained on different strings (p0056). Write `sul G`, or use Roman numerals:

| | I | II | III | IV |
|---|---|---|---|---|
| Violin | E | A | D | G |
| Viola | A | D | G | C |
| Cello | A | D | G | C |
| Double bass | G | D | A | E |

### 2.2 Individual bowed-string instruments (Chapters 3–4, p0064–p0123)

The character of the violin's four strings is in `SKILL.md` §6; here are the other instruments and their hard constraints.

#### 2.2.1 Viola: size is its constraint (p0073–0085)

Technique is largely the same as the violin's: trills, bowing, harmonics, arpeggios, and double-, triple-, and quadruple-stops all apply equally.
The real difference is that **the body is three to four inches larger than the violin's**; the hand must stretch further to play accurately, and **left-hand tension is greater, especially in the high positions** (p0073).

**Orchestration implication**: viola fast figurations and wide intervals cannot be written to violin standards; restraint is especially needed in the high positions.
Notated in the alto clef; the treble clef is used for the high register only to avoid ledger lines.

> The book also records some history: the viola was long neglected, first because in the eighteenth century four independent string parts were rarely written, and second because violists were often doubled by violinists, so composers did not trust them.
> Berlioz was the first to give it an independent part in orchestral writing (p0073).
> For today's practical purposes, the lesson is this: an empty viola layer reflects historical inertia, not any lack of capability.

#### 2.2.2 Cello: the four strings differ greatly (p0087–0094)

| String | Character |
|---|---|
| **A** | The most brilliant and most powerful |
| **D** | The most pleasing and melodious, warm and lyrical |
| **G** | The weakest, with penetration far inferior to the other three |
| **C** | Round and deep, relying on its own weight and thickness |

(p0089) ★ **The G string is a trap**: it is the least penetrating of the four, and a line that must be heard written on the cello's G string is easily buried.
The old claim that "the cello is not nimble enough" no longer holds; it can play almost any technique the violin or viola can (p0089).

#### 2.2.3 Double bass: the body stretches the intervals (p0095–0099)

★ **The factor that most affects writing**: the body is large and the strings are thick and long, so **even the smallest interval is stretched into a very wide hand-position distance**.
In low position, the first through fourth fingers span only a major second (p0097).
From the first through fifth positions only fingers one, two, and four are used; in the sixth position the third finger is occasionally used; the thumb is needed only from the seventh position (p0097).

**Orchestration implication**: the double bass cannot write dense chromatic stepwise motion or fast scales; if you write them, they remain paper music.
The bass part must move by leaps and position changes, not by dense stepwise motion.

#### 2.2.4 Harp: the pedals determine what you can write (p0100–0117)

This is the most constrained instrument in its group; **you cannot write for the harp correctly without understanding the pedals**.

**Mechanism** (p0100): 47 strings, six complete octaves plus six additional notes. With all pedals in the upper position, the tuning is C-flat major.
Each pedal has three positions: pressing to the middle raises the note a semitone, and pressing to the bottom raises it a whole step.

★ **The fatal rule: all strings with the same note name are controlled by the same pedal.**
Press the C pedal and all six C strings change together. So **it is impossible to play C-flat and C-natural in the same octave at the same time** (p0100).

**The workaround is enharmonic notation** (p0100, p0101): write C-flat as B-natural, so the two notes fall on different strings controlled by different pedals.
Likewise, to use F and F-sharp at the same time, write F as E-sharp, or write F-sharp as G-flat.
★ **This is the orchestrator's job, not the player's.** Before writing, plan the pedals; if they cannot be arranged, change the notation.

**Pedal arrangement and pedal changes** (p0101):

| Left foot | Right foot |
|---|---|
| D C B | E F G A |

- ★ **Avoid requiring the same foot to change two pedals at once** (for example, changing E and G at the same time, both on the right foot).
  Pedals on different feet (for example D and G) can change simultaneously
- Pedal markings in the score come in three forms: listing each letter one by one, a diagram of the three positions, or ordering the letters by the left and right sides
- A pedal change can be placed at the last instant before the note is needed

**The two lowest strings (D¹ and C¹) are not controlled by pedals and must be adjusted by hand; the highest, G⁷, is controlled by the G pedal** (p0100).
String colors are used to find positions: **every C string is red and every G string is blue** (p0100).

#### 2.2.5 Plucked-string instruments (p0109–0123)

Look up the specific ranges and notation on the corresponding pages; here we state only whether they can be used and when. **Guitar** (p0109): its actual pitch sounds an octave lower than written, and **its overtones are very soft**; without amplification it suits only solo or light ensembles, so do not expect it to project in tutti. **Mandolin** (p0109–0110): tuned like the violin, sustaining by tremolo; **it is a quiet instrument**; in Example 4-30, a similar banjo is "almost completely masked" by two horns, so surrounding instruments must yield. **Banjo** (p0119–0120): in modern orchestras it almost never appears except to imitate bluegrass style; before using it, confirm that you truly want its period flavor. **Zither** (p0121–0123): appears very rarely and has no general writing convention; work from the specific musical examples.

### 2.3 Orchestrating for strings (Chapter 5, p0124–p0172)

The difficulty of the string section is that **the whole section has a homogeneous timbre**, so layering cannot rely on timbral differences; it can only rely on register, arrangement, and playing technique.
This section covers the Western string arrangement and layering methods; the boundary table in `mc-harmony` that says "arrangement methods belong here" refers to this section.

#### 2.3.1 Three-layer division of labor: foreground, middle ground, background

| Layer | What it carries |
|---|---|
| **Foreground** | The most important part: the melody the composer wants the listener to hear |
| **Middle ground** | Contrapuntal melody, or important contrapuntal material |
| **Background** | Accompaniment. It may be harmonic figuration, or polyphonic or melodic material |

★ **The writing order is fixed**: first set the foreground, its range, and the emotional tension it should reach; then choose instruments for the five instruments according to each one's register character.
**Once the foreground is fixed, the middle ground and background have a basis to be written** (p0130–0131). Conversely, if you lay down accompaniment first and then look for a melody, the three layers will inevitably clash.

> The book uses Haydn as a benchmark: when the three elements are distributed well, balance can be achieved without relying on dynamic markings (p0131).
> This is a practical criterion for judging orchestration quality: **an orchestration that needs dynamic markings to achieve balance most likely has its layers built wrongly**.

#### 2.3.2 When timbres are similar, layer by register

This is the primary layering method within the string section (p0136):

- **Place the foreground melody on the instrument's best register**
- **Place the background figuration on the register where the instrument is dullest and has the least distinctive character**

Two supporting rules: switching the double bass to pizzicato can weaken the impact of the bass (p0136); nested background arpeggios can produce an uninterrupted, flowing texture,
while repeated swirling accompaniment adds tension to the long notes in the melody and keeps the figuration itself from being interrupted (p0137).

#### 2.3.3 Unison and parallel thirds: the emotional difference is larger than it looks

A strong unison or octave statement is suited to presenting an idea first, then turning to another mood through changes in texture (p0137–0138).
★ In the Classical style, **there is a huge emotional contrast between a simple accompaniment in parallel thirds and stiff octaves**,
even when the change in texture and dynamics is small. Suddenly resting an Alberti-type figure can make a predictable statement suddenly light and floating (p0138).

#### 2.3.4 Homophonic voicing: spacing that follows the harmonic series

When writing a chord for full string section, the distribution of notes is determined mainly by voicing, range, and melody (p0154).

★ **Core judgment: the intervals between notes in the low parts should be larger than those in the high parts**, because the spacing below in the harmonic series is naturally wider than above (p0154).
Violating this makes the low register muddy.

**Example 5-26 (p0154)**: the same D major triad (D-F♯-A) written for five string parts in two voicings; both can play soft or loud, the fingerings are all comfortable, and the difference is small; but the version with wider octaves in the low parts and denser spacing above sounds slightly darker. **This criterion governs fine adjustments of darkness and brightness, not right and wrong**; which to choose depends on how dark you want it. Conversely, if a chord sounds stuffy when voiced, first check whether the low parts are doubled more densely than the high parts.

#### 2.3.5 Six allocations of dense voicing (Western-side arrangement methods)

For the same chord progression, handed to five string parts, there are six common allocations, with very different sounds (p0155):

| Allocation | Sound |
|---|---|
| 1. Four parts each on its own (Vln1 high, Vln2 second, Vla middle, Vc low; Db an octave below repeating Vc) | The simplest. **At dynamics between soft and mezzo-forte it sounds awkward**; at very loud dynamics the bass is too heavy, because the three middle-to-low instruments are all in registers more suitable to them than to the violin |
| 2. Viola divided into two upper parts, cello divided into two lower parts | Soft, slightly dark |
| 3. Allocation 2 plus double bass an octave below | The melody becomes much darker |
| 4. Vln1 takes the high part; Vln2 or Vla divided to take the second-highest and middle parts | Slightly brighter, still soft |
| 5. All to cello, with double bass in unison doubling the low part | Very intense |
| 6. Whole thing moved up one to two octaves, with no double bass | Increasingly sparkling |

**Usage**: this table is the lookup for "what color does this harmony need." Settle the color first, then choose the allocation; do not divide first and then listen to the effect.

#### 2.3.6 Repetition in first inversion

- **Repeating the bass (i.e., the third) is not standard practice**, except when the root falls on scale degree 6, 7, 2, or 3 (p0155)
- For the commonly used I⁶, IV⁶, and V⁶, pay special attention to intervals and doubling; **in four-part textures, do not double the bass**
- With more than four parts, the third must be doubled somewhere to reinforce it; **place the doubling near the bottom of the texture** so that the open sound characteristic of first inversion emerges (p0155)

#### 2.3.7 Seven ways to reinforce a single melody

To make one melody "more powerful," choose from (p0156):

1. First violin solo, with no accompaniment
2. Second violin plays, with the first violin repeating an octave higher
3. Two instruments in unison doubling (Vln1+Vln2 / violin+viola / violin+cello / viola+cello)
4. Move it to the violin's G string
5. Give it to viola or cello solo; **at this register these two are more tense than the violin**
6. Spread across four to five octaves, with all five instruments
7. Violin section, viola section, and cello section in unison

★ Item 5 is the most often overlooked. To obtain tension, you need not add it higher; switching to an instrument that is tighter in that register is often more effective.

#### 2.3.8 Two troubles with contrapuntal texture

Between foreground, middle ground, and background there is a gray zone; this is where contrapuntal orchestration most often goes wrong (p0145):

1. **You must clearly mark which tier each melody belongs to**, or listeners cannot perceive what is primary and what is secondary
2. **Choices must be limited**, especially when a section repeats and the repetition could have been handled another way

The second point is a demand for restraint on the orchestrator: faced with the vast range of options in orchestration, trying everything amounts to doing nothing.

#### 2.3.9 String ensemble accompanying soloists

The homogeneity, technical capacity, and varied registers of the string section make it suitable for accompanying instrumental soloists, vocal soloists, and choirs (p0163).
The book gives the traditional model plus a list of works (Mendelssohn, Mozart, Bizet, Fauré, p0163–0169),
and the practice of arranging piano works for strings (p0170–0171).

> Haydn's *String Quartet* Op. 76 No. 3, second movement (p0125–0126) demonstrates the roles of voices and the control of dynamics within variation,
> corresponding to `SKILL.md` §4, "Balance."

---

#### 2.3.6 Dense, open, hollow, and wide top spacing: voicing determines color (Yang Liqing upper volume p0199–0207)

Adler's six allocations (§2.3.5) cover who gets the same voicing; Yang Liqing's section here covers what **the voicing itself** sounds like in the orchestra.

| Voicing | Sound | Conditions and cost |
|---|---|---|
| **Close** | The most harmonious, with the fullest resonance (p0199) | Placed in the low register with intervals between parts smaller than an octave, it becomes heavy and dark: the characteristic color of Brahms and Sibelius (p0201) |
| **Open** | Soft and bright at soft dynamics; majestic and broad at loud dynamics with wide spans (p0204) | ★ **At the same dynamic, the actual loudness is slightly lower than close voicing** (p0204): choose open for "bigness," close for "loudness" |
| **Gap in the middle register** | At soft dynamics, leave a gap of no more than an octave in the middle register; low harmonics shine through the gap, giving a refined, transparent color (p0201). At ppp, a gap of a major sixth or minor seventh makes the whole texture clearer and softer (p0202) | Works only at soft dynamics |
| **Hollow middle** | Leave a large gap in the middle of the harmonic layer so that important textural elements appearing in the middle register can be heard (p0203) | **Usually used only at soft dynamics**, and the gap **usually must be filled with flowing figuration** (p0203) |
| **Wide top spacing** | Dense harmony over a very broad range; at the top, use fifths, sixths, or even octaves: the highest note reinforces the overtones of the chord tones below, raising brightness (p0203) | If the top is filled with thirds, "the ethereal, dreamlike atmosphere will be considerably diminished" (p0203) |
| **Mixed** | Based on open voicing, the tenor part is also repeated one to two octaves higher (p0206). The book's example: bass + cello + divisi viola in open voicing; second violin divisi repeating the viola in dense voicing in the high register, three upper parts; first violin capping it a fifth higher, "exceptionally pure and moving" (p0207) | Traditional writing repeats only the top two parts an octave higher, which already forms local density between the basic part and the doubled parts (p0205) |

Another point often overlooked: wide spacing is not always for fullness; **a sustained bass note and inner voices separated by two octaves aim for a transparent sense of space** (p0200).

**Orchestration implication**: when writing a string pad, set the dynamic first and then the voicing. At soft dynamics, gaps, a hollow middle, and wide top spacing are all usable colors. For loud passages, use close voicing to be loud or open voicing to be broad, accepting that open voicing is slightly less loud than close.

### 2.4 Woodwind section: lineup, register character of each instrument, chord arrangement (Chapters 6–8, p0172–p0290)

#### 2.4.1 Lineup and score rules

The classical double-woodwind lineup is 2 flutes, 2 oboes, 2 clarinets (types set by the key of the work), and 2 bassoons (p0188). Score rules (p0190):
same-type instruments' first and second parts are written on the same line, and separate lines are used only when rhythmic complexity differs. With three instruments, 1st and 2nd share a line and the 3rd is separate, or lines are grouped by which instruments are closest. Unison is marked `a2` / `a3`; solo performance is marked `1.` and `2.`.

#### 2.4.2 Register character of each instrument

| Instrument | Register character | Orchestration implication |
|---|---|---|
| **Flute** | The low register is beautiful but weak, **audible only with a very sparse accompanying texture** (p0193). The high register has "undeniable brilliance" and also flexibility (p0194). Long notes require a great deal of breath, **so breath points must be provided** (p0195) | With melody in the low register, the accompaniment can only be a sustained harmonic background; place fast runs in the high register |
| Piccolo / alto flute / bass flute | The piccolo extends the flute's range up an octave, on the same principles. The alto flute is the first downward extension, often used by Stravinsky and Ravel; the bass flute extends further down | A piccolo an octave higher can make dark passages "gaudy"; **use sparingly in passages meant to be dark** (p0289) |
| **Oboe** | The most influential register is **F⁴ to C⁶**; for soft, penetrating tone, write between high C and the F above it (p0206). The highest A⁶ is extremely difficult, and even professional players may not manage it | Place the melody in this range; do not push harmonic fill upward |
| Cor anglais | The alto member of the oboe family, with a slightly longer tube and reed (p0208) | One step darker than the oboe |
| **Clarinet** | Four registers (p0218): the **chalumeau register** is deep and rich; the **throat register** is pale; the **clarino register** is bright, precise, and expressive; the extreme top is piercing. **The most evenly balanced range of all the woodwinds**, usable from ppp to fff; **for keys with flats, use the B-flat clarinet** (p0218) | Choose it for an instrument that is stable from low to high; avoid placing melody in the throat register |
| Bass clarinet | Commonly in B-flat (p0224) | One of the best low-frequency bases among the woodwinds |
| **Bassoon** | Double reed, conical bore, **but without the nasal quality of the oboe**; suits both lyrical melody and crisp staccato (p0232). Bass clef; tenor clef is used when many ledger lines would be needed above | Doubling a violin theme an octave lower is a classic use, to "highlight the melody and add warmth" (p0288) |
| Contrabassoon | The lowest woodwind, an octave below the bassoon | |
| **Saxophone** | Belongs to the woodwind section: its pitch is close to the clarinet family, its reed and mouthpiece are close to the clarinet's, performers often double, and it is originally a woodwind member (p0228). The family runs from soprano to bass in five types (p0229) | |

#### 2.4.3 Four arrangement methods for two-woodwind chords (p0264–0265)

| Method | Procedure | Evaluation |
|---|---|---|
| **Stacking** | One instrument placed on top of another | The most common; **the melody stands out only if each instrument is in its best register** |
| **Interleaving** | Parts cross each other | Ideal, blending the timbres; but in some registers some instruments will overpower weaker ones, so be careful |
| **Enclosing** | One group of instruments enclosed between another group | The same kind of problem as interleaving; ★ Enclosing the oboe between two instruments of different timbres gives better balance and adds color (the clarinet is stronger than the second flute on D⁵) |
| **Contact arrangement** | Parts repeat at the same pitch | Common before the twentieth century; it masks timbral character and strengthens notes that need no emphasis; still common in tutti |

The book's evaluations of each interleaving combination range from "good" to "poor, especially when playing pp," and **the difference in arrangement is greatest in soft passages**.

#### 2.4.4 Conventions for woodwinds doubling strings (p0288–0289)

A whole-section doubling common in the nineteenth and twentieth centuries: the first violin doubled an octave higher by flute and piccolo; the viola doubled an octave higher by oboe and clarinet, filling in the harmony an octave above; the cello doubled at unison and an octave higher by bassoon (p0288).
Two accompanying rules: when combining woodwinds with strings, reduce the volume of the brass; **as the pitch rises, the timbre becomes ever more brilliant** (p0289).

#### 2.4.5 Five woodwind arrangement patterns and three rules (Yang Liqing lower volume p0068–0073)

Beyond Adler's four (§2.4.3), Yang Liqing counts by pairs, adding a juxtaposed form, and gives the appropriate occasions for each form:

| Form | Method | Suitable for |
|---|---|---|
| **Stacking** | Two or more pairs of instruments arranged in order from high to low, with no overlapping chord tones | The most natural, with a complete sound; still the most commonly used. As the chord's "volume" expands, the flute keeps moving upward to a more distinct register (p0068–0069) |
| **Interweaving** | Two pairs of instruments cross each other in register | Easier to fuse than stacking, and balance is usually better. In the low register, the combination of clarinet and bassoon is dark and steady, like an organ (p0069) |
| **Enclosing (sandwich)** | Two notes of one pair are inserted between another pair | The outer timbre has a slight advantage, while the enclosed one is weaker (p0070). ★ **When combining sustained long-note harmony with flowing harmonic parts, use enclosing to separate the two timbres; stacking or interweaving is not advisable** (p0070). Conversely, using the reverse order, with the oboe enclosing the flute, can highlight the melodic significance of the oboe |
| **Contact** | The lower part of the upper pair and the higher part of the lower pair overlap at unison | Common in the Classical period; Beethoven especially favored it (p0070–0071) |
| **Juxtaposition** | Each chord tone is played by two or more instruments | For a fuller, more balanced sound. The 3 Fl, 3 Ob, 3 Cl juxtaposition in a three-per-section lineup can be seen as a doubled form of stacking (p0072) |

Three rules (p0073):
1. **In Classical and Romantic writing, do not give a dissonant minor second to instruments of the same timbre**; the sound becomes too tense.
2. In a three-per-section lineup, **a pair of same-type instruments plus a variant instrument** (for example, two oboes plus cor anglais) is the best combination; a three-part chord usually uses a same-type pair plus one instrument of a different type.
3. Unless each part is played by a single instrument, **rarely distribute chord tones among instruments of different timbres**, as this easily separates the timbres and makes balance difficult, especially in dense voicing. Exceptions: when the chord has a linear implication, or when a color contrast with traditional scoring is wanted.

### 2.5 Brass section: two groups, the mechanics of range, mutes, and the character of each instrument (Chapters 9–11, p0307–p0370)

#### 2.5.1 Lineup and the two groups

The modern lineup is 4 horns, 3 trumpets, 3 trombones, and 1 tuba (p0307). The timbre of the brass is more unified than that of the woodwinds, but it splits into two groups: **horns** as one group, and **trumpets, trombones, and tuba** as another (p0307).
Two grounds for this: the horn has the property of fusing with and reinforcing the woodwinds, so it is both a member of the brass and an appendage of the woodwinds; the horn has a funnel-shaped mouthpiece, while the others have shallow cup-shaped mouthpieces.
Forsyth's rule: **the shallower the cup-shaped part of the mouthpiece, the more brilliant the sound**. Trumpets and trombones mostly have elongated, tubular bodies; horns and tuba mostly have conical bodies (p0307–0308).

**Orchestration implication**: for a "brass character" without harshness, use horns; for brilliance, use the shallow-cup group. Horns can be layered like a woodwind; trumpets cannot.

#### 2.5.2 The mechanics of range

Range depends on tube length and bore width: **the wider the bore, the easier it is to play low; the narrower it is, the easier it is to play high** (p0309).
Fundamental tones are harder to play than high ones and are generally found only in modern symphonies and solo works (p0309).

**Why going up is hard**: without valves, high notes are produced by overblowing the harmonic series. In theory this reaches the 21st harmonic, but most players cannot reach beyond the 16th (p0307). The 7th, 11th, 13th, and 14th harmonics themselves deviate from equal temperament, so intonation problems multiply as you go higher. Lips are relaxed for low notes and tightened for high notes; **climbing in the brass is physical work**. Loud playing uses more breath than soft playing, so for long phrases at slow, loud dynamics, calculate breath points in advance (p0309). Long high lines are best given breath gaps or relayed among players.

#### 2.5.3 Mutes

Trumpets and trombones have various mutes; **horns and tuba each have only one kind** (p0318).
The horn's **hand mute** raises the pitch; players compensate by lowering a semitone with the hand or with fingering, and commercial mutes can correct this (p0318).
Besides mutes, soft playing can also use the plunger; blowing fast notes tight against the mouthpiece gives a burst of sound (p0321).
**Orchestration implication**: a horn or tuba writing for mutes has only one color to choose from; do not expect them to produce the palette of mutes a trumpet section can offer.

#### 2.5.4 Character of each instrument

| Instrument | Character | Orchestration implication |
|---|---|---|
| **Horn** | See §2.5.1; can blend with woodwinds | The only brass instrument that can act as "glue" |
| **Trumpet** | The **most agile and fastest-speaking** of the brass; must play both loud and soft, across the entire range and all volumes (p0336, p0343). **Slurs are played in one breath; staccato is done entirely by tonguing**, with single, double, and triple tonguing all common (p0343) | Give fast staccato phrases to it; writing a slur means writing a breath |
| **Trombone** | The section is often two tenor trombones plus one bass. The tenor's range is E² to B⁴, with seven positions, from first-position B♭ to seventh-position E♭; bass clef, switching to tenor clef above G⁴ (p0351–0352) | ★ **The extent of a slide glissando must not exceed a tritone**, which is the largest interval the same harmonic can reach across positions (p0357). Writing a larger glissando amounts to writing something unplayable |
| **Tuba** | The low register is **deep and heavy but slightly blunt**; the middle register is **very powerful**, smooth and round, like a horn; the high register is slightly weaker but very tense, and the sound thins (p0361) | The tuba's "power" lies in its middle register; the low register gives weight, not force |

#### 2.5.5 Functions of the brass section

Composers did not begin to exploit the brass to the fullest until the second half of the nineteenth century; Wagner and Brahms still favored natural trumpets and horns (p0368). There are four functions: as a unit in homophonic music (alone or combined with other groups), playing melody (solo, combined, or as independent parts in counterpoint), building climaxes, and rhythmic and color emphasis (p0368–0369).
For how brass is placed in tutti, see `mc-arrangement-arch` §2.4; for the "unison that is not quite together" of brass unisons, see `mc-style-cinematic` §4.

## 3. Adler vol. 2: Orchestration and adaptation (`adler-orch-2`)

| Topic |
|---|
| **Chapter 15: Orchestrating for the orchestra** |
| **Unison and Octave Tutti** |
| Schoenberg orchestral adaptation examples / analysis of adaptation styles |
| Principles for adapting wind ensemble music to orchestra |
| **Four dimensions of adaptation study** |
| Milhaud, *Suite française*: adaptation comparison (examples 17-15 and 17-16 include orchestral-version comparisons) |
| Summary of timbral contrast |

> The textbook basis for `SKILL.md` §3.1, "Unison blending," is in the section "Unison and Octave Tutti."

---

### 3.1 How new color enters (p0019)

In a melody with accompaniment, the accompaniment's color often contrasts with the soloist, sometimes strongly; but in many cases a successful accompaniment is played by **instruments the same as or similar to the soloist's** (p0019). There are two customary ways to change color:
1. **Assign a newly beginning phrase (including one starting on a weak beat) to a new instrument**;
2. ★ **Place a rest before the new color enters.**
The second point is the one AI orchestration most often omits: timbres stack layer upon layer without ever stopping, so when the new color enters there is no "breathing space," and what is heard is a wall. The four methods for seams are in SKILL §3.6.

## 4. Yang Liqing middle volume: three widths of line and woodwind breath (p0028–0085)

The neutralization phenomenon, playing technique determining blend, octave coupling, coloring, and the three conditions for woodwind projection in SKILL §3 all have their sources in Chapter 7 of the middle volume (p0028–0045, examples VII-15 to VII-19). Here are three things from Chapter 7 that SKILL did not expand on.

### 4.1 Fifteenth (and above) lines (p0048–0051)

Already common in the Classical period, usually using **contrasting high and low instruments of different woodwind types placed in opposition** (flute and piccolo against bassoon and cor anglais). The timbres stay separate, the sound is slightly hollow, **with a certain humorous flavor** (p0048). The original instrument and its variant, placed a fifteenth (two octaves) apart in different registers, can be inventive: the piccolo, in the middle-to-high register and two octaves apart, repeats the skeleton tones of a low-register flute melody, and the open sonic space conveys melancholy and sorrow (p0050). Piccolo and bassoon combined at three octaves apart carry an exotic, colorful flavor (p0051).
**Usage**: for "emptiness," "wit," or "exoticism," use the fifteenth rather than the octave; for "thickness," do not use it.

### 4.2 Multi-layer octaves: rarely written for same-type instruments (p0052)

Multi-layer octave lines played by one instrument type are rare, because the differing character of each type across registers makes it hard for the layers to balance in timbre and dynamics. Among the woodwinds, only the clarinet can barely manage it, and even then the lower layer sits in an unfavorable register (p0052). Multi-layer octaves should use different instrument types for each layer.

### 4.3 Woodwind breath in figurated textures (p0081, p0085)

When a figurated line flows on without end and "offers no gap," breath support becomes a problem (p0081). Two solutions:
- **Alternate playing the same phrase between different instrument parts** (in a double-layered, interlaced dense broken harmony, clarinet and flute alternate). This is easy to play, solves the breathing problem, and keeps the timbre consistent and evenly transparent (p0081).
- ★ **Breath rotation**: in multi-layer figurated textures, each part breathes at different points in time, so the overall sound continues without interruption (p0085).
Supporting point: give fast descending staccato arpeggios to the most agile "virtuoso" woodwinds: piccolo, flute, and clarinet (p0081). MIDI has no breath problem, but §5.3 notes that virtual players need breath points for the same reason: woodwind lines without breathing do not sound like they were played by a human.

---

## 5. MIDI orchestration quick reference (Pejrolo)

### 5.1 CCs that orchestration actually uses

The full specification of the 128 CCs is in Table 1.2 of `pejrolo-midi-orch` (p0027–0031).
**For orchestration you need only the following:**

| CC# | Name | Use in orchestration |
|---|---|---|
| **1** | Modulation | Usually controls the **vibrato** produced by an LFO; some sample libraries use it to control volume. **Confirm the library's mapping before use** |
| **2** | Breath | Commonly used by wind libraries for breath/dynamics |
| **7** | Volume | The channel's overall volume (**do not use it for shaping within a phrase**; that is CC11's job) |
| **11** | Expression | **Dynamic shaping within a phrase is done with this.** The "life" of strings and winds comes mainly from this curve |
| **64** | Sustain pedal | Keyboard instruments |
| **68** | Legato pedal switch | Creates **legato** (no break between adjacent notes). Only two states: 0–63 off, 64–127 on |
| **71** | Sound controller 2 | Controls the **VCF envelope over time**, commonly called "Resonance" |
| **72** | Sound controller 3 | Controls the **release stage of the VCA** (the note's sustain time) |
| **73** | Sound controller 4 | Controls the **attack stage of the VCA** (the time for the waveform to reach maximum amplitude) |
| **74** | Sound controller 5 | Controls the **VCF cutoff frequency**: **changes the brightness of the sound** |
| **84** | Portamento control | Controls the amount of glide |
| **91** | Effect 1 depth | Usually the **reverb send level** |
| **93** | Effect 3 depth | Usually the chorus send level |

**★ The most important rule**: the division of labor between `CC7` and `CC11` must not be confused.
CC7 sets the **position** of this track in the orchestration (a sound-field decision belonging to `mc-mix-intent`);
CC11 sets **how this phrase breathes** (a playing-technique decision belonging to this skill).
Mixing the two produces the result "I pushed the fader, but the phrase is still dead."

### 5.2 Other CC categories (for reference)

| Range | Content |
|---|---|
| CC0 / CC32 | Bank select (must be used together to send bank numbers above 128) |
| CC69 | Sustain pedal 2: when pressed, notes are **not prolonged**, but fade out according to their own release times |
| CC75–79 | Sound controllers 6–10, manufacturer-defined |
| CC80–83 | General-purpose switch controllers (0–63 off / 64–127 on) |
| CC85–90, CC102–119 | Undefined |
| CC92 / 94 / 95 | Effect 2/4/5 depth (tremolo / celeste detune / phaser) |
| CC96 / 97 | Data increment / decrement |
| CC98–101 | NRPN / RPN least and most significant bytes |
| CC120–127 | Channel mode messages (all sound off, reset controllers, local on/off, all notes off, omni, mono/poly) |

### 5.3 Bringing samples to life: Pejrolo's implementation checklist (p0112–0114, p0138–0142, p0166–0168, p0210–0211)

SKILL §7 says MIDI sounds fake because it omits the player's decisions. This section gives the means to restore those decisions, ordered as "choose the timbre first, then write, then fix."

**① Sample layers and keyswitching methods (p0138–0141)**
- The secret of realism is that **timbre must not be static**: when the same note is repeated, the attack, release, and overtones all change with velocity. Multi-layer samples are split by velocity (in the book's example: pp 1–39, mf 40–90, ff 91–127). More layers are more accurate, at the cost of memory and CPU.
- ★ **Use CC#1 instead of velocity for crossfading between layers**; only then are the transitions between layers seamless, whereas velocity triggering produces steps.
- Keyswitches (sustain, pizzicato, staccato, placed on keys outside the playing range) have two recording methods: **switching while playing** saves time but fast phrases are error-prone; **recording the full part with sustain first, then recording a second pass for the switches**, reduces the pressure of doing two things at once. Large productions use the latter.

**② Layering timbres (p0141–0142, p0168)**
- One sample library is often not enough. Layering different libraries on the same part gives cohesion, removes the feeling of a loop, and produces new overtones.
- Wet/dry ratio: **for fast, busy passages, 70% dry and 30% wet; for sustained notes and pads, 30% dry and 70% wet**. Add 5%–10% of an old-style wavetable timbre to smooth out the harshness of the samples and add resonance.
- After layering, **offset the pan positions of the layers by ±5** (on a 0–127 scale) to establish a natural separation.
- ★ **Layer one real instrument into each string group** (one real violin in the violin section, and likewise for viola and cello). The detuning and noise of real instruments inject life into MIDI; do not layer a dozen. Real players each record 3–4 takes. The same applies to the winds, and especially the saxophone, which is the hardest to reproduce in a virtual environment (p0211).
- Solo parts **never use synthetic strings**; use at least a high-end solo sample library (p0167).

**③ While writing (p0167, p0210–0211)**
- Write bowing and slurs into the score. Slurs matter more than up/down bows, because they specify how many notes lie within one bow.
- For balance, **the violin is always the loudest, since the lower strings carry their own power**. A real string ensemble has at least 11 players (6-2-2-1); record three takes and layer them into a large lineup, and having players switch parts helps the blend.
- When writing for winds, think of the MIDI keyboard as having only the few notes of that instrument, not as a full piano keyboard. Unison textures are the hardest to make sound real.
- ★ **Leave phrases and rests for the "virtual player" to breathe**, especially for winds. Where possible, use a breath controller or wind controller (Yamaha WX, AKAI EWI).

**④ When fixing (p0166, p0211)**
- **Use CC#7 and CC#11 together to reshape the dynamic envelope**, avoiding several bars that sit at the same volume. CC#11 can be recorded while playing, or drawn after recording and played back from the beginning. If time allows, use CC#11 to fix the attack and release of each note (splitting one part into a channel for down-bow notes and a channel for up-bow notes).
- **Velocity to attack**: high velocity gives a fast attack, low velocity a slow one. **Velocity to filter**: at low velocity the cutoff frequency is low and the timbre dark; at high velocity the filter opens and the timbre brightens. These two make the same sample change in more than loudness at different velocities.
- Pitch-bend controller CC#5 (glide rate), CC#65 (portamento switch), CC#84; soft pedal CC#67.
- **Quantization**: over-quantizing sounds stiff, while without quantization a loose performance is unstable. Long notes and sustained strings can be left completely unquantized. For start points, use **negative sensitivity of −60% to −70% at 80% strength**; if still unstable, increase the strength.
- **Natural noise**: floor and chair creaks, page turns, and wind breath sounds, added in small amounts. In excess they make it sound like "a group of amateur players."

**⑤ A few points on the rhythm section (p0112–0114)**
- Piano: classical and jazz choose a round, warm timbre; pop and rock choose a sharp, bright one. When the piano is exposed in front, the round timbre is more realistic. Use CC#66 for the sustain pedal and CC#67 for the soft pedal. Reverb: classical 2.3–3.2 seconds, jazz 2–2.5 seconds.
- Guitar: multi-sample libraries are best; use keyswitches for slides and pull-offs. Busy background parts take reverb of 1.5–1.7 seconds; solo or forward melodies can go up to 1.9 seconds.
- Bass: keep panning conservative and centered; use almost no reverb in the low register; add performance noise from time to time; re-amp (reamp) to remove the "boxy" quality of the synthesizer.
- Drums and percussion: **record with a MIDI drum pad, not a keyboard**. Each instrument gets its own track; the only exception is the kick and snare, which can be recorded in one pass for a much more natural feel.

---

## 7–8. Chinese folk orchestra (separate file)

The quick reference on folk instrument technique and the score-writing conventions for the folk orchestra are in [reference-minyue.md](reference-minyue.md).
Bar numbers follow §7 and §8, and citations are unchanged. They are separated because these two sections together run over thirty thousand characters, which is also inconvenient to read alongside the Western material in the same file.

---

## 9. What is not part of this skill

| Content | Where to go |
|---|---|
| Frequency budgets, which parts compete for frequency, frequency carving | `mc-texture-layering` |
| Timing of entrances and exits, energy curves | `mc-arrangement-arch` |
| How to build synthesizer timbres | `mc-sound-design` |
| Realistic drum, bass, guitar, and keys playing | `mc-rhythm-section` |
| Specific sample-library product selection, keyswitch charts | Not part of this package (which sound source to use is determined by the production environment) |
| Full-score notation conventions, part preparation | L4 compilation layer (`mc-symbolic-score`); others are not part of this package |
