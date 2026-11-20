---
name: mc-style-rock-band
description: Rock and band-format music as a style layer (band lineup style layer) - what changes when five people in a room have to play it. The band roster as a hard constraint, why rock opens with fewer instruments than any other style, power chords and the harmony rules that stop applying, and riff as the primary hook carrier - Rooksby's 30 riff types (interval / scale / chord based), riff length and the 3+1 repetition pattern, riff vs vocal (alternate, end-of-line, or sustain), where riffs sit in the form, variation devices, riff-drum-bass dovetailing, twin-guitar roles, drop D / open G tuning, and the transfer table. Use when arranging for a band lineup, when a track needs a riff hook, when a riff sounds monotonous or fights the vocal, when a rock arrangement feels thin or muddy, or when borrowing band devices into produced music. Also matches rock, band, riff writing, riff types, power chord, distorted guitar, twin guitars, drop D, tuning, live feel.
---

# Band Lineup Style Layer (Rock / Band)

**The organizing principle of this skill is not "what rock sounds like," but:**

> **When this music has to be played simultaneously by five people in a room, what changes?**

This constraint is far more useful than the "rock" style label, and it covers punk, indie, funk, country rock, and blues at the same time—**the whole corpus bundle `Alt-Rock---Blues---Country-Rock---Indie---Funk---Reggae` is packaged exactly this way.**

## Which sections to read by task

| Task | Read |
|---|---|
| **Judging whether band techniques can be transplanted** | ★ §2 transfer table |
| How to set the lineup | §3 (★ **it is a constraint, not a palette**) |
| How to bring in the opening | ★ §4 (**measured: rock opens with the least**) |
| Harmony | §5 (★ **which general rules stop applying here**) |
| Where the hook goes | §6 riff |
| **How to write a riff** (type / length / variation) | ★ §6.2–§6.6 plus [reference.md](reference.md) §1–§3 |
| How riffs coexist with vocals | §6.4 |
| How riffs interlock with bass and drums | ★ §6.7 |
| Dividing roles between two guitars, choosing tuning | §3.3–§3.5 |
| Looking up the riff taxonomy / example index / terminology | [reference.md](reference.md) |
| Sounding "assembled" rather than played | §7 |

## Boundaries

| Not covered here | Where it belongs |
|---|---|
| Whether drumming sounds human | `mc-rhythm-section` (★ general, not style-specific) |
| Guitar, bass, and drum instrument technique | Electric guitar and electric bass instrument technique is not transcribed in this library; tunings and riff-friendly keys are in this skill's reference §6–§7; arrangement of individual drum kit pieces is in `mc-rhythm-section` reference §2 |
| How to make distortion tones | Not in this package: the guitar distortion effects chain is a matter of recording and mixing (`mc-sound-design` covers synthesizer timbres) |
| Frequency-band budget | `mc-texture-layering` |
| Form | `mc-form` |
| Practical band recording | A matter of audio recording, not covered in this package |
| Fretboard fingering, positions, and bending details for riffs | Not covered here (this skill covers only writing and arrangement; the reference only records page numbers) |
| General theory of meter and groove | `mc-rhythm-groove` (this skill only records meter effects relevant to riffs, reference §4) |

---

## 1. Required before starting

| Required | Question to answer |
|---|---|
| **① Lineup roster** | ★ **Fix it.** How many guitars, is there a keyboard? **This is a hard constraint** |
| **② Can it be performed live?** | ★ Determines how many layers can be stacked (§3.2) |
| **③ Is the hook in the vocal or the riff?** | §6 |
| **④ How many instruments are present at the opening?** | ★ Measured: rock is **only 8%** (§4) |
| **⑤ Which riff type, how many bars, what chords are underneath?** | §6.2, §6.3 |

---

## 2. ★ Transfer Table

| Technique | Can it be transferred? | Notes |
|---|---|---|
| **Lineup as constraint (fix the roster before writing)** | ✅ ★ **Transferable, and should be** | The biggest harm of unlimited sound sources is that you never have to make trade-offs |
| **Extremely sparse opening** | ✅ ★ **Transferable** (§4) | Measured rock is the extreme on this item and worth learning |
| **Riff as hook** | ✅ Transferable | It is one implementation of `arrangement_hook` (lint #8) |
| **Power chords (parallel fifths)** | ⚠️ **Partially transferable** | It is a **timbral device**, not voice-leading. Moving it into a lineup with real voice-leading will collide with rules (§5.1) |
| **Full-ensemble unison hits** | ⚠️ Partially transferable | Effective in pop, but not too often—it will drown out the vocal |
| **Distorted guitar's frequency-band occupation** | ❌ Not transferable | It consumes almost the entire midrange, which other styles cannot afford |
| **The "can be performed" standard** | ✅ ★ **Transferable** | §7 |

★ **Criterion**:
> **Transfer its discipline (lineup constraint, sparse opening, can be performed live),
> but do not transfer its spectral occupation (distorted guitar + full-ensemble unison).**

---

## 3. The Lineup Is a Constraint, Not a Palette

### 3.1 Write the roster first

**The most fundamental difference between band music and produced music**:
in produced music, "adding another layer" is free; in band music, **adding a layer means one more person or one more overdub**.

★ **This constraint is a good thing**:
the line that opens `mc-texture-layering`, "musical space has boundaries; adding beyond the limit will cover existing content," is a **physical fact** in a band lineup, not a reminder.

### 3.2 The two lines for overdubbing

| | Notes |
|---|---|
| **Playable live** | Lineup = number of people. **Arrangements on this line are the cleanest** |
| **Can be overdubbed** | Double-tracked guitars, added keyboard layers, added harmonies. ★ **But ask: how will this song be handled live?** |

**Practical compromise**: **the core four (drums / bass / guitar / vocals) must work live**;
overdubbed layers are **color**, and the song should still stand if they are removed.

### 3.3 The lineup determines how the riff is written

| Lineup | How the riff is written | Page |
|---|---|---|
| **Power trio / four-piece including vocalist** (only one harmonic instrument) | Favor riffs of at least two notes; chord-based riffs are more appealing. In single-note riffs, add thirds to some notes to imply chords—best when both notes are not the root, **leave the root to the bass** | Rooksby, *Riffs*, p0140, p0048 |
| **Has a second guitar** | The riff can be harmonized; single-note riffs can be doubled | Riffs p0140 |
| **Has a keyboardist** | Try single-note riffs with more "cutting" quality, with keyboards filling the harmony. ★ **Have the keyboardist limit the number of notes to serve the riff** (Deep Purple's approach) | Riffs p0140 |
| **No bass (White Stripes style)** | Build major triads on every note of the minor pentatonic, yielding a palette of six major chords (reference §7) | Riffs p0123 |

★ This follows from §3.1: **once the lineup roster is fixed, how many notes the riff should have and who plays the root is already half decided.**

### 3.4 Dividing roles between two guitars

| Division | Description | Page |
|---|---|---|
| **One riff, one chords** | In the chorus, the guitar playing the riff follows the vocal melody, while the other plays straight eighth-note chords; the riff is not doubled by the second guitar or bass, giving the arrangement more breathing room | Riffs p0056 |
| **One riff, one shuffle** | When chords move to C and D, the other guitar plays a standard shuffle rather than a transposed riff, so the riff sounds fresh when it returns after the solo | Riffs p0038 |
| **Two similar but different** | Two guitars play parts that are similar but not identical (*All Right Now*); a same-scale riff with some notes different (*Helicopter*) | Riffs p0111, p0139 |
| **Splitting notes** | Fast fifths are hard for one player to play cleanly → two guitars each play one single note; thirds harmony split with each guitar taking one note | Riffs p0139, p0178 |
| **Twin lead** | Two guitars play parallel lines built mainly on thirds (Wishbone Ash, Thin Lizzy, Queen); thirds sound best on strings 1–2 or 3–4, and turn muddy on the low strings | Riffs p0043 |
| **One sustained, one riff** | The first guitar does not carry the pedal note; the second guitar on the other side of the stereo field eventually enters, supported by a D5 | Riffs p0091 |
| **Split left and right** | In the intro the riff appears only once in the center; once the band enters, the riff splits into two guitars, left and right | Riffs p0038 |
| **12-string over 6-string** | An electric 12-string mixed quietly over an overdriven six-string, with the high octave strings adding a sense of overtones | Riffs p0139 |

★ Interface with §5.1: **when two guitars each play their own line, the parallel-fifths problem returns; parallel thirds in twin lead are part of its vocabulary, not an error.**

### 3.5 How tuning affects the arrangement

(The full table is in [reference.md](reference.md) §6–§7.) Five points to know at the writing stage:

- **The key determines the sound**: transposing the same I–bVII–IV has a huge effect on guitar—how many open strings there are and what the lowest note is (Riffs p0122). Hard rock favors E and A; F# and B are also popular, because the open strings a whole step below the tonic are exactly bVII (Riffs p0122).
- **Tuning down adds weight**: lowering all strings by a semitone keeps the fingerings the same, just a semitone lower; each semitone down calls for one step heavier string gauge, or the strings go slack, pitch suffers, and they don't hold up to heavy attack (Riffs p0124). Dropped D shifts the guitar's center from E to D, and the lowest three strings can be barred with one finger (Riffs p0126).
- **Open tunings change which riffs can be written**: open G makes the on/off figure of "sus4/6/9 added over a barred major chord" more effective than standard tuning (Riffs p0125); DADGAD grew out of imitations of folk baroque and North African drones (Riffs p0125).
- ★ **If you change the tuning, reduce the distortion**: under open or altered tunings, resonance, sustain, and overtones are all enhanced, so lower the distortion; dense notes on adjacent strings a whole step or semitone apart need a cleaner tone (Riffs p0127). This should share a source with the timbre decisions in `mc-sound-design`.
- **Transposition loses open strings**: an original riff that uses open strings will lose them in most transpositions; pedal, sustained, inverted, and chord-based riffs are especially sensitive (Riffs p0122)—see how to handle this in §6.6. Riffs written in altered tunings must have their fingerings noted down (Riffs p0127), **written into `roster[].note`**.

---

## 4. ★ Measured: Rock Opens With the Least

Cambridge-MT multitrack measurements (10 tracks per style), giving the share of the full roster that is present at the opening for each style:

| Style | Share present at opening |
|---|---|
| ★ **rock** | ★ **8%** |
| jazz-acoustic | 16% |
| Alt-Rock bundle | 20% |
| pop | 21% |
| edm | 21% |
| hiphop-rnb | 24% |

**How to read it**: ★ **Rock is the most restrained at the opening of all styles.**

**Why**: because it has to **go full ensemble** later.
**If everyone is in from the start, there is no contrast when the full ensemble arrives.**

> **The measurements also confirm a strong rule in this library**: "the opening should not lay out all the instruments at once"—**54/59 hits**.
> ★ Rock does not merely satisfy this rule; it pushes it to the extreme.

**Self-check**: ★ **Count the instruments in your opening lineup. If it exceeds 20% of the full roster, it is too full.**

### 4.1 Other measurements

| Metric | rock | Alt-Rock bundle | pop |
|---|---|---|---|
| Roster size (median) | 30 | **38** | 36 |
| Instruments entering mid-track | 26 | 28 | 29 |
| Instruments leaving early | 18 | 16 | 16 |

⚠ **Do not cite BPM** (the reliability of beat tracking on distorted guitar has not been verified).

---

## 5. Harmony: Which General Rules Stop Applying Here

### 5.1 ★ Power chords and parallel fifths

Rule 2 in `mc-counterpoint` reference §1: **strictly prohibit parallel fifths and parallel octaves**.

★ **It does not apply here**, but **the reason must be stated clearly**:

> **A power chord is not a chord; it is a timbre.**
> It has no third and does not take part in functional harmony; moving it in parallel is **shifting one timbre**, not **carrying out the motion of two voices**.

★ **Criterion**: **ask whether these two "voices" have their own melodic identity.**
If not → it is timbre, and it may move in parallel freely.
If so → the parallel-fifths problem returns (for example, when two guitars each play a line).

Rooksby reaches the same conclusion from the standpoint of timbre: a fifth has no third and is neither major nor minor, and **it tolerates heavy distortion and stays effective in a rock context**, which is linked to the overtones that distortion enhances (Rooksby, *Riffs*, p0030). Thirds carry the emotional content of major and minor and turn muddy on the low strings (Riffs p0030, p0096), which is why rock riffs use thirds sparingly and fifths often (Riffs p0043).

### 5.2 Weak progressions (D→S)

Dominant-to-subdominant progressions such as `C–G–F–C` are treated as errors in classical harmony (see the comparison table in `mc-harmony` reference §5).

> ★ **In rock and folk it is standard vocabulary.**
> Adding a minor seventh to each of the three chords (C7/F7/G7) gives a blues sound with blue notes.

### 5.3 Still valid

- **The skeleton of functional progressions** is still valid (T–S–D–T)
- **Non-diatonic chords** remain color (lint #9 still applies)
- ★ **Bass-line design** is still valid—**this is the one point that both Sposobin and Japanese practice agree on**

### 5.4 Harmony rules deduced from riffs

| Rule | Description | Page |
|---|---|---|
| **Two major triads a semitone apart do not belong to any major key** | Making a semitone shift into a fifth or major triad necessarily produces an out-of-key note; this is the source of its "rebelliousness." Punk places a major triad a semitone lower before each chord in a 12-bar form | Rooksby, *Riffs*, p0018–p0019 |
| **bVII is the norm** | A whole-step shift erases the leading tone, and the mode becomes Mixolydian; I–bVII–IV is the core rock progression; "every major-key I–IV–V riff may correspond to two or three Mixolydian I–bVII–IV riffs" | Riffs p0022–p0023, p0097, p0100 |
| **Major triads built on the minor pentatonic** | A minor pentatonic → major triads on A, C, D, E, G, which may add F. Equivalently: from the major scale, discard the diminished chord and the three minor chords, and lower the 3rd, 6th, and 7th by a semitone to make them major triads | Riffs p0123 |
| **Minor chords are rare** | Rock favors fifths and is uneasy with the "excess emotion" of minor chords; the most common minor-chord riff is I–VII–VI (Am–G–F) | Riffs p0104 |
| **The riff's mode is decided by the chords beneath it** | Which mode a riff lacking a third is heard as depends on the rhythm guitar or bass; modal riffs need harmonic support that does not weaken them | Riffs p0071, p0078 |
| **Modes are flavor, not the whole** | In rock, modes rarely appear in pure form, and even fewer have both melody and chords staying within the mode | Riffs p0077 |
| **Implied chords** | The guitar stays static while the bass moves underneath, creating the illusion of chord changes; the same fifth with a different bass note is heard as a different chord | Riffs p0037, p0033 |
| **Major sevenths in heavy contexts** | Rarely used in heavy rock (too sweet), but extremely effective when combined with its power | Riffs p0137 |

These share a source with §5.2: **the skeleton of rock harmony is blues and Mixolydian, not functional major.** The functional rules of `mc-harmony` recede here to "the skeleton still stands" (§5.3), and color is determined by the riff's intervals (§6.2).

---

## 6. Riff as Hook

**In band music, the `arrangement_hook` (lint #8) is usually a riff.**

| Point | Description |
|---|---|
| **It is a memory point, not filler** | ★ Same principle as "the synth lead in `example-01` only plays the hook and does not fill in the background" |
| **It needs space** | When the riff sounds, the vocal usually does not sing (**alternating**, `mc-texture-layering` §4.2 solution ③) |
| **It must recur** | `hooks.arrangement_hook.recurs_at` must specify which sections it returns in |
| **It can be rhythm rather than pitch** | A specific pause or syncopation can also serve as a riff |

Details (taxonomy, repetition patterns, variation techniques, example index, terminology) are in [reference.md](reference.md); the seven checkpoints to pass when writing a riff follow below.

### 6.1 What counts as a riff: short, repeated, memorable, low

Rooksby's working definition: **"a short, repeated, memorable phrase, usually in the low register of the guitar, that concentrates most of a rock song's energy and excitement"** (Rooksby, *Riffs*, p0007). Each of the four words is a constraint:

- **Short**: 1–4 bars; any longer and it sounds like a melody or a solo (Riffs p0007).
- **Repeated**: repetition is how it sticks in memory, and it is also the driving force—"shoveling coal into a steam locomotive's firebox" (Riffs p0007).
- **Memorable**: it relies on specific rhythmic, harmonic, or melodic qualities (Riffs p0007). To check, use the **RHM formula**—run through all three facets: rhythm, harmony, melody (Riffs p0008).
- **Low**: most guitar riffs sit on the lowest three strings, where there is "power and authority," and the bass defines the harmony above it (Riffs p0007). Riffs in the high register are exceptions, and need echo to thicken them and combination with the bass (The Edge, Riffs p0008).

★ **The four functions of a riff**: rhythm (makes people move), filling sections without vocals, dynamic contrast (the verse pulls back, the instrumental section explodes with the riff), and temporarily substituting a chord progression (Riffs p0008). **Before writing, state which of these it serves in this song.**

**Criterion**: a chord progression can also be a riff—provided it repeats often enough and has a clearly defined, forceful rhythmic pattern (Riffs p0013–p0014). Conversely, the same chords become a riff in the intro/verse through a clear rhythm, but in the chorus are merely accompaniment (*American Idiot*, Riffs p0100). **"Is this a riff or accompaniment" is decided by the rhythmic pattern, not by the notes.**

### 6.2 Typology: choose the material first, then accept its harmonic consequences

Rooksby divides them into three groups totaling 30 types (Riffs p0013; full table in reference §1):
**① Intervals between two single notes**—semitone / whole tone / octave / fifth / fourth / tritone / third / sixth / mixed;
**② Scales**—minor pentatonic / blues / major pentatonic / major / Mixolydian / natural minor / Dorian / Phrygian / Lydian / Locrian / chromatic;
**③ Chords**—pedal note / drone / arpeggio / major chord / Mixolydian chord / minor chord / suspension / triad / inversion / unconventional.

The criterion when writing is not "which type sounds good," but **the harmonic consequences each type carries with it**:

| If you choose | You must accept | Page |
|---|---|---|
| A semitone shift made into a fifth or major triad | An out-of-key note is inevitable—this is the source of its "rebelliousness," and it also means it belongs to no major key | Riffs p0018–p0019 |
| A whole-step shift bVII→I | The leading tone is gone, the mode is Mixolydian, and the bVII chord comes with it | Riffs p0022–p0023 |
| Fifths, fourths, octaves | Neither major nor minor; any chord can go above them—**the harmony is decided by someone else (bass / rhythm guitar)** | Riffs p0027, p0030, p0034 |
| Thirds, sixths | Clearly major or minor; sweet, lacking aggression; muddy on low strings | Riffs p0043, p0048, p0096 |
| Minor pentatonic / blues scale | Sounds "hard" over major chords; blends in over minor chords and loses its assertiveness | Riffs p0053 |
| Major pentatonic | Sounds "pretty bad" over minor chords | Riffs p0063 |
| Dorian / Phrygian / Lydian / Locrian | Must have harmonic support that does not weaken it, or it will be heard as something else (5.15 heard as Mixolydian rather than Dorian); modes are mostly used as "flavor" rather than in pure form throughout | Riffs p0077–p0078 |
| Chromatic | Needs a steady drum pattern and a clearly stated root to keep it stable | Riffs p0085 |
| Pedal / drone / inversion / chord riffs with open strings | Transposition loses the open strings; this must be "solved compositionally" at the writing stage | Riffs p0122 |
| Unconventional chords | Use sparingly—"without normal, you don't know what is strange" | Riffs p0116 |

**Failure condition**: when a riff lacks a third (most fifth-, fourth-, octave-, and pentatonic riffs do), its mode is decided by **the chords beneath it**—*Taxman* and *Paperback Writer* are heard as Mixolydian rather than pentatonic because of the rhythm guitar's major triads (Riffs p0071). **So writing the riff alone does not count as finished; you must write out what is underneath it.**

Asymmetric riffs (odd scales, odd accents, unpredictable leaps, changing meters) are interesting to players but rarely resonate with the public (Riffs p0013)—if you want something like *Smoke on the Water*, don't pile them on.

### 6.3 Length and repetition

- **Length**: 1, 2, and 4 bars are the norm; 3 bars are rare (repeated, they make 6, which breaks the grouping in fours, but four repetitions give 12); more than 4 bars is hard to hear as a single unit (Riffs p0129). Four bars usually split into two answering phrases; unsplit ones are rare (Riffs p0072).
- **Repetition patterns**: label one bar as a1; the basic shape is **3+1**: `a1 a1 a1 a2`; eight bars `a1 a1 a1 a2 / a1 a1 a1 a3`; sixteen bars add a4 at the end; call-and-response `a1 a2 a1 a3` (Riffs p0129–p0130; full table in reference §2.2).
- ★ **Harmonic level of variants**: a2 and a3 must not sound more "complete" than a4, because a4 is the ending of the whole block—in A, a2 and a3 are best landing on notes that imply D, E, or bIII, bVII (Riffs p0130).
- **How many repetitions**: the riff in the intro plays three times, not four, before the verse comes in (*Tush*, Riffs p0038); repeating a 4-bar riff 3 or 5 times instead lets the ear notice change sooner (Peter Buck, Riffs p0132); a one-bar riff played only four times (about 10 seconds) before the song enters also works (Riffs p0056).
- **The upper-limit criterion**: when listeners feel "the riff is great but the song ended too soon," they replay it—this is the desired effect (Riffs p0118). Keeping the riff in focus throughout is a source of power, but it should be hard to make it boring (Riffs p0047).

**Self-check**: count how many times the riff sounds before the vocal enters—if it is four or more times with no variation at all (accents, bass notes, added instruments), you are already wearing it out.

### 6.4 Riff and vocal: yielding or sustaining

Both relationships are valid, but you must choose:

| Relationship | How | Page |
|---|---|---|
| **Alternating** (no singing while the riff sounds) | The riff fills sections without vocals; the verse pulls back, the instrumental section explodes | Riffs p0008 |
| **Riff lands at the end of the line** | The riff is inserted at the end of each lyric line, so it does not divert attention from the words (*Queen Bitch*); the riff acts as an "affirmation" of the lyric rather than running simultaneously (*The Thunderthief*, *Money*) | Riffs p0099, p0145 |
| **Riff sustained, vocal on top** | In hard rock and metal, the riff runs from the intro into the verse, with the vocal singing over it | Riffs p0130 |
| **Vocal riding over the riff** | The melody does not follow the riff but "rides" over it, establishing a contrapuntal rhythm (Howlin' Wolf) | Riffs p0046 |
| **Verse changes material** | The vocal sits on a single static chord, followed by a busier riff—a static chord does not distract from the vocal | Riffs p0047 |

★ **Three conditions for a riff and vocal to coexist** (Riffs p0131): a complex riff distracts from the melody and does not provide harmonic support the way chords do. To layer a melody over a riff, **① match the melody's rhythm to the riff's rhythm; ② choose melody notes that harmonize with the riff's notes; ③ place the melody in the gaps when the riff has them**.

**Register solutions**: low-register riffs do not clash with the lead singer the way high guitar riffs do (*Ball of Confusion*, Riffs p0056); a high guitar riff plus a low bass setup leaves room in the middle of the arrangement for the vocal (U2, Riffs p0037); in the verse, the riff guitar drops out of the mix and only the bass plays the riff (*Smells Like Teen Spirit*, Riffs p0131).

**Failure conditions**: if the riff contains notes that collide with the lyrics, delete them as soon as the vocal enters—in *Are You Gonna Go My Way*, the riff's fourth disappears when the singer comes in (Riffs p0062); the riff's ascending run must fall into the gaps between the singer's phrases for it to serve as both accompaniment and hook (*Street Life*, Riffs p0065).

### 6.5 Where the riff sits in the section structure

The positions Rooksby lists: **intro; sustained through the verse; the link between verse and chorus; under or leading into a solo; recurring in the coda** (Riffs p0131). Each position has its own strategy:

| Position | Strategy | Page |
|---|---|---|
| **Intro riff** | Give a shortened version first (five notes, ending on an unresolved note), then the full version—"write a riff, then make a shortened version to delay the appearance of the full one" | Riffs p0095 |
| (same) | The intro enters as if from bar 9 of a 12-bar form, heightening the impact when the riff arrives | Riffs p0025 |
| (same) | The riff enters late: sequencer synth → piano → drums → the guitar riff only arrives after the first verse | Riffs p0099 |
| (same) | Catchy in the first 5 seconds: bass E octave against guitar Bb octave, a tritone | Riffs p0041 |
| **Verse riff** | Simplify the verse; keep the full form for the chorus or linking section | Riffs p0131 |
| (same) | In the verse, only the bass plays the root and the chords are implied; or the bass alone plays the roots to carry the third verse, then the left and right guitars double it | Riffs p0098, p0102 |
| (same) | A bass riff carries the first verse (only cymbals and vocal with it); other instruments come in, but the bass continues into the chorus—"the riff persists while other things happen above it" creates tension | Riffs p0070 |
| (same) | The verse riff has no bass; the bass enters only in the chorus | Riffs p0111 |
| **Transition riff** | Use an arpeggiated riff to connect chorus and verse; a second riff after the first chorus serves as the link to the second verse | Riffs p0094, p0070 |
| **Solo section** | Solos often use a simplified form, transposed up a whole step | Riffs p0064, p0121 |
| **Coda** | Transposing in the ending breathes new life into a riff heard many times; moving the riff to E and using the lowest notes of guitar and bass gives the greatest power | Riffs p0120, p0082 |
| **One riff carries the whole song** | A two-bar riff carries the whole song, relying only on occasional accent changes (*Louie Louie*, Riffs p0100); three variants carry an entire song (*Ain't Talkin' Bout Love*, Riffs p0096). This presupposes that the riff has a hierarchy of variants (§6.3) | |

**When the bass enters** (Riffs p0139): don't spend all your ammunition in the first minute—① the bass first doubles the guitar an octave lower, then drops another octave later; ② the bass first plays a pedal note before the full ensemble comes in; ③ the bass plays the riff first, then the guitar layers on top.

**Self-check**: for each occurrence listed in `hooks.arrangement_hook.recurs_at`, be able to write out "how this time differs from the last" (simplified / full / transposed / different bass note / different instrument). If it appears identically three or more times, the techniques of §6.6 have not been used.

### 6.6 Variation techniques

Vary it along the three RHM facets. Don't treat the riff as a finished product; treat it as "an object that shows only one side" (Riffs p0118; full table in reference §3):

| Facet | Technique | In brief | Page |
|---|---|---|---|
| Rhythm | Testing tempo | The goal is **the fastest speed at which the riff keeps its identity**, not the fastest it can be played; demos often run slow | Riffs p0118 |
| Rhythm | Diminution | At the end, compress a four-bar riff into two bars; listeners feel acceleration though the tempo is unchanged | Riffs p0134 |
| Rhythm | Shifting accents / reversing note values / shifting by a beat | Add accents that were not there in the repetition; reverse a dotted eighth + sixteenth; move certain notes earlier or later by a beat or half-beat | Riffs p0134, p0060 |
| Rhythm | Changing meter | Put a 4/4 riff into 5/4, adding an extra beat of rest for a drum fill; insert a 3/4 bar so the next section arrives a beat early | Riffs p0135, p0132 |
| Harmony | Re-harmonizing | Major → relative minor; a riff containing only fifths or fourths is harmonized with major or minor chords in different sections | Riffs p0119 |
| Harmony | Changing the bass note | In a unison riff, change the bass note to imply an inversion; the first inversion is less "stable" than root-position unison, and can be used to delay the arrival of the root-position unison | Riffs p0119 |
| Harmony | Changing context, not notes | The riff stays put while the chords move Em→G→C→F (*Androgyny*); "change the context you hear, not the notes" | Riffs p0119–p0120, p0184 |
| Harmony | Partial harmonization | Add a few notes above only the last bar; thirds and sixths carry major/minor color, fourths/fifths/octaves stay hollow; when choosing octaves, look at the pitch of the vocal line | Riffs p0140 |
| Pitch | Transposition (following structure) | In a 12-bar form, go up a fourth and then a fifth; a single one-bar riff covers all 12 bars | Riffs p0120–p0121 |
| Pitch | Transposition (not following structure) | Most commonly up a major second; a minor third; step through the pentatonic scale; for unease, use a semitone or tritone | Riffs p0121–p0122 |
| Pitch | Octave layering | Stacking 2–3 tracks at the same pitch adds no more loudness; layer different octaves instead | Riffs p0139 |
| Form | Development across repetitions | A5 rhythm → add a minor third → the minor third becomes a bIII chord → run thickened; "development is almost never used in rock," so using it occasionally is effective | Riffs p0177, p0175 |

**Failure conditions**:
- Transposition loses open strings—pedal, sustained, inverted, and chord-based riffs are especially sensitive. In the studio, you can use a capo or retuning to layer only the transposed version, **but ask how it will be handled live**. A wiser move is to treat it as an opportunity to write a variant—"solve it compositionally" (Riffs p0122). This shares a source with §3.2.
- Added notes need a reason—"each note should either support the harmony or support the rhythm; if there's no reason, don't play it" (John Paul Jones, Riffs p0146).

### 6.7 Counterpoint between the riff and bass and drums

★ This is the key to whether a riff "sounds played," and it connects directly to §7.

**With drums** (Riffs p0135):
- Two basic choices: **the riff's notes dovetail into the drums**, or **they sound together with the drums**. Pay particular attention to the kick and snare—you can write around one of them, or leave a gap so one of them punches through.
- A classic technique: **leave gaps where the snare hits and play around it** (Riffs p0135). The power of *You Really Got Me* comes from the snare hitting hard in the gaps of the riff (Riffs p0024); the impact of *Last Resort* comes from clear beat-spaces between the notes (Riffs p0076).
- The most effective octave riffs are locked to the drums—think carefully about where each note lands rhythmically (Riffs p0027).
- Many of the best riffs emerge while playing along with a drum machine, drum loop, or drummer's improvisation: without a rhythmic backing, people chase the excitement of harmony or melody, but rock is mainly about rhythm (Riffs p0135).
- John Paul Jones's version: think about the riff from the rhythm section's perspective; if you want the snare (or kick) to be a feature, leave space for it in the riff; in a complex riff, sometimes you should stop the riff and let the drums express dynamics—**"if everyone plays at the same time, it won't get heavier, only weaker"**; place tension at the micro level, so that the parts of the riff push and pull against each other (Riffs p0145–p0146).

**With bass**:
- The rhythmically best guitar riffs are often doubled by the bass, with a rhythmic pattern matching the drums (Riffs p0135).
- **The bass determines the riff's harmonic identity**: over the same A–C–G, a low A sounds like A minor pentatonic, while a low F or C sounds completely different (Riffs p0129). When the bass settles down and enters the verse, the riff's timbre changes accordingly (Riffs p0037). The guitar stays static while the bass moves underneath—this is an "implied chord" (Riffs p0037).
- For inverted guitar riffs, the bass must follow the inverted bass line; playing only the root weakens the effect (Riffs p0174). Conversely, when exploring inversions, **it is easier to have the bassist change notes than to change the guitar chords** (Riffs p0115). AC/DC create "harmonic distortion" in familiar pentatonic chord riffs by using bass inversions or pedal notes (Riffs p0100).
- Under an arpeggiated riff, the bass may play only the root to highlight the chord changes (Riffs p0094). When the riff is too fast for the bass to imitate, the bass is free to play something else (Riffs p0158). Placing a minor-scale bass line under a major triad creates tension (*The Rocker*, Riffs p0103).
- The bass holds one note steady while the guitar changes intervals above it (*Radar Love*, ZZ Top style, Riffs p0051, p0090)—this is the riff version of the fused type in `bass_kick_relation`.

**Self-check** (mandatory after writing a riff):
1. State the relationship between the snare's landing points and the riff's notes: dovetailed in, left as gaps, or simultaneous?
2. State whether the bass doubles, plays the root, plays a pedal note, or plays another line—and say why.
3. Count the bars where everyone hits together: if they outnumber half the riff's length, return to the line "it gets weaker, not heavier."

---

## 7. ★ "Sounds Assembled"

**This is the most common failure in band styles, and it has specific causes:**

| Cause | Remedy |
|---|---|
| Every instrument is perfectly aligned to the grid | → `mc-rhythm-section` §2.2: **quantize instrument by instrument**, leaving one instrument unquantized |
| Everyone plays from start to finish | → At least one instrument drops out early (**59/59 strong rule**) |
| Nobody responds to anyone else | ★ The essence of band music is **interaction**: guitar fills between vocal phrases, drums hit hard on the guitar riff's landing points, the bass follows the kick or deliberately doesn't (→ `mc-rhythm-section` §7.1) |
| Dynamics are uniform throughout | Real bands naturally pull back in the verse and open up in the chorus. → `energy_curve` |
| Fills land on multiples of 4 | → lint #10 |
| The riff and drums hit together, filling everything | → §6.7: "if everyone plays at once, it doesn't get heavier, only weaker" (Rooksby, *Riffs*, p0146); leave space for the riff at the snare |
| The riff is identical every time | → §6.3, §6.6: 3+1 variants, change the bass note, change the context but not the notes |

★ **The most direct self-check**:
> **Imagine the five people in the room. Are they listening to each other?**
> If every layer can say "who it is responding to," the song will sound played.

---

## 8. Field Mapping to ARR-SPEC

| Field | This skill |
|---|---|
| `meta.style_layer` | `mc-style-rock-band` |
| `arrangement.roster` | ★ §3 — **define the roster first; it is the constraint** |
| `roster[].entry` | ★ §4 — at the opening, present instruments **no more than 20%** |
| `hooks.arrangement_hook.what` | §6.1–§6.2 — state the riff's type (name from reference §1), length (number of bars), and **the chords beneath it** (§6.2 failure conditions) |
| `hooks.arrangement_hook.first_at` | §6.5 — whether the shortened version comes first or the full version appears directly; when the bass enters |
| `hooks.arrangement_hook.recurs_at` | §6.5 — note the difference at each occurrence (simplified / full / transposed / different bass note / different instrument) |
| `form[].harmony` | §5.4 — bVII and major triads on the pentatonic are the norm and need no exemption |
| `form[].note` | §6.6, reference §4 — record meter changes (inserted 3/4, 5/4 sections) here |
| `meta.key` | §3.5, reference §7 — the key should be guitar-friendly (E, A, F#, B and similar); if the key is not friendly, state the reason |
| `roster[].note` / `roster[].timbre` | §3.5 — record tuning (drop D / open G) and fingerings in note; if the tuning is changed, reduce the distortion in timbre |
| `depth_map` | §6.4 — when the riff and vocal are both in the foreground, the riff should be either in the low register or the high register, not occupying the middle |
| `groove.quantize_policy` | §7 — leave one instrument unquantized |
| `bass_kick_relation` | Fused (heavy) or interlocking (melodic). §6.7 — state clearly whether the bass doubles, plays the root, plays a pedal, or plays an inverted bass line against the riff: pick one of the four |
| `checks.exemptions` | ★ Parallel fifths from power chords **need no exemption** (§5.1 already explains they are not voice-leading), but **watch out when two guitars each play a line**; parallel thirds in twin lead are vocabulary (§3.4) |

---

## 9. Must-Check After Writing

- [ ] **Fix the roster first**; all later arrangement stays within it
- [ ] Can state **how this song is handled live** (which layers are overdubbed color)
- [ ] ★ **Instruments present at the opening ≤ 20% of the full roster**
- [ ] At least one instrument **drops out early**
- [ ] `arrangement_hook` has a **riff**, and the sections where it recurs are written down
- [ ] **Leave it space** while the riff sounds (don't compete with the vocal)
- [ ] ★ **Every layer can state "who it is responding to"**
- [ ] Not every instrument is perfectly aligned to the grid
- [ ] When using power chords, be clear that it is **timbre, not voice** (§5.1)
- [ ] When transferring to other styles, checked §2
- [ ] Riff's **type** (reference §1), **length**, and **chords beneath** (§6.2) are written
- [ ] The riff's repetitions have a variant hierarchy: 3+1, and a2/a3 are not more complete than a4 (§6.3)
- [ ] A **relationship between riff and vocal** is chosen: alternating / line-end / sustained (if sustained, pass the three conditions in §6.4)
- [ ] Can state **the snare's landing points in relation to the riff** and **what the bass plays** (§6.7)
- [ ] The lost-open-string problem after transposition has been "solved compositionally," not left to the studio (§6.6)
- [ ] If tuning was changed, distortion was reduced (§3.5)

---

## Appendix: Sources

- **Measurements**: Cambridge-MT multitracks—`rock` 10 tracks, `Alt-Rock---Blues---Country-Rock---Indie---Funk---Reggae` 10 tracks. ★ **The "8% at the opening" point in §4 is this skill's most solid basis.**
- **Failure conditions for harmony**: `mc-harmony` [reference.md](../mc-harmony/reference.md) §5, `mc-counterpoint` [reference.md](../mc-counterpoint/reference.md) §1.1
- **Riff writing**: Rikky Rooksby, *Riffs: How to Create and Play Great Guitar Riffs*, cited pages p0007–p0184. The definitions, typology, length and repetition patterns, riff and vocal, section placement, variation techniques, and counterpoint with bass and drums in §6, the lineup and tuning in §3.3–§3.5, and the harmony rules in §5.4 all come from this book; the taxonomy, example index, and glossary are in [reference.md](reference.md). The division of the book's 30 types follows its own account (Riffs p0013); this skill adopts only what the book states explicitly.
- This skill rests on **corpus measurement + the general layer + deduction from the "band lineup" constraint + Rooksby's riff-writing method**.
- ⚠ The six-style bundle in the corpus (`Alt-Rock---Blues---Country-Rock---Indie---Funk---Reggae`) **was not split apart**, so this skill's measured numbers do not distinguish funk from reggae.
