# mc-style-hiphop Reference: Sample Processing, Flow Notation, Delivery Parameters, Glossary

> [SKILL.md](SKILL.md) covers judgment and trade-offs; this file holds the **detailed lookup tables**.
> Citation conventions: Schloss, *Making Beats*, is cited as `Schloss p0163`; Edwards's two books as `How to Rap p0142` and `How to Rap 2 p0031`; Charnas, *Dilla Time*, has no page numbers and is cited by **chapter** as `Chapter 8`. The full chapter table of contents is in reference-vocal.md §6.

---

## 1. From Break to Beat: Build Step Table

### 1.1 Pin Down Three Verbs First

| Verb | Definition | Source |
|---|---|---|
| **looping** | Sample one or more bars and repeat them with almost no change | Schloss p0121 |
| **chopping** | Cut a sample into smaller fragments and reorder them so that continuous performance sounds like collage; fragments can be used to assemble a melody the original never had | Schloss p0166 |
| **flipping** | Any substantial creative change (including, but not limited to, chopping) | Schloss p0179 |

**Chopping has replaced whole-loop sampling as the mainstream practice** (Schloss p0166). There are two reasons:
- Aesthetic: Vitamin D wants the **texture and sound** of the sample, not the **composition** of the original; a composition carries someone else's feeling and intent (Schloss p0179).
- Practical: old records have been mostly sampled out (Domino, Schloss p0179); a four-bar straight loop "won't sell even if you keep it" (King Otto, Schloss p0195).

★ But **don't chop for the sake of chopping**: Jake One: "What I care about is how it sounds, whether he loops or chops" (Schloss p0182).

### 1.2 The Ten-Step Process

| Step | What to do | Criterion / detail | Source |
|---|---|---|---|
| **① Drums first** | Mr. Supreme: *"Usually you start with the drums … that's the backbone and the heart of it."* | Get the drums right, and whatever goes underneath is right | Schloss p0154 |
| **② Trial fit** | Find a sound you like, first cut it in on the downbeat and run it along, check whether it fits, then decide whether to sample it | This is the direct use of DJ skills for producers | Schloss p0069 |
| **③ Truncate** | **Truncate**: fix the start and end point of each sample | The start and end points decide whether the attack gets clipped and how long the tail is | Chapter 5 |
| **④ Loop and layer** | Loop & layer: let several sample layers run together | The relation between layers is a "relationship," not "orchestration" | Chapter 5; Schloss p0165 |
| **⑤ Set section lengths** | **Use bar counts to set the lengths of intro / verse / chorus** | MPC allows non-four-beat loops: "You can loop around every three beats, or five, or six, or seven if you want." (Chapter 5) | Chapter 5 |
| **⑥ Chop and rearrange** | DJ Topspin: give him only a **one-and-a-half-beat** fragment and he wants to "turn it into sixteen beats that sound like a live performance"; four one-and-a-half-beat pieces can be assembled into six beats | Fragment length need not be a whole number of beats | Schloss p0157 |
| **⑦ Lock up** | "Locking up" a beat: the elements enter a self-sustaining relationship | ★ **Whether it locks is a yes-or-no matter**: if it doesn't lock, it isn't a beat | Schloss p0154 |
| **⑧ Check vertical interference** | A sample never contains just one sound (eight or nine people playing); when sampling a keyboard tone, a small hi-hat may be embedded in it | **It is not on your beat, and it interferes with your drums**: the most common hidden conflict in sample-based work | Schloss p0157–0158 |
| **⑨ Unify timbre** | The snare comes from a 1970s rock record, the hat from a 1950s jazz record, the kick from an 80s drum machine; they must **sound natural together** | Prince Paul: if you sample 1960s material you can't pair it with the laser drums of *Planet Rock*; "keep everything in one texture" | Schloss p0161, p0081 |
| **⑩ Add and remove layers** | Bring in and pull out loops and stabs by section | This is the **only structural tool** of the genre (SKILL §6.2) | Schloss p0051, p0151 |

### 1.3 What the Loop Grows on Its Own (Schloss p0152–0153)

These explain why looping is not laziness, and they are also the criteria for choosing loop points:

| Phenomenon | Explanation |
|---|---|
| **Unintended juxtaposition** | When the end of a phrase repeatedly leads into its beginning, this is a join the original player never intended; after several repetitions it "starts to feel inevitable" |
| **New chord progression** | Take a jazz sample that contains one chord change: at the loop point, the second chord goes straight back to the first, **producing a progression the original composer never wrote** |
| **Melody becomes rhythm** | "Melodies become rhythms": after enough repetitions, the ear stops following the melodic contour and listens only to its rhythmic outline |
| **Built-in call and response** | The end of a break builds tension that its own beginning resolves; **call-and-response is built into the loop** |
| **Let a loop grow** | DJ Kool Akiem: leave one loop running for two or three days, and "you'll hear things the musician didn't try to put in" |

Chopping can also create new harmony: Dilla used Kool & the Gang's *Summer Madness* to chop out "a completely different harmonic progression" (Chapter 7); Busta's *Enjoy Da Ride* works the same way (Chapter 8). This and creating new chords at loop points are the same thing at two levels.

### 1.4 Three Things Sampling Can Do That Live Performance Cannot (Schloss p0165–0166)

Choosing the "sample-based" rather than the "played" approach gets you these three things. When writing `roster`, you should explicitly use at least one of them:

1. **Juxtaposing the room sound of different recording environments** (ambient qualities): a fully reverberant guitar and a very dry bass present at the same time.
2. **Repeating the same note exactly**: identical repetition of velocity and attack, which human hands cannot do.
3. **Organizing patterns that acoustic instruments struggle to play live** because of physical limits.

Behind this is Olly Wilson's **heterogeneous sound ideal**: *"The desirable musical sound texture is one that contains a combination of diverse timbres."* (Schloss p0165). **The ideal texture is a combination of many timbres, not the uniform tone of one band.** This directly determines how `spectrum_budget` is written: sample-based work does not pursue a tidy division of frequency bands; it pursues heterogeneity of timbral source.

### 1.5 Meter and Length Can Be Bent

| Technique | Example | Source |
|---|---|---|
| A 5/4 jazz passage looped into a 4/4 drum pattern | "It's a loop, but played in a completely different way" (Stroman) | Schloss p0181 |
| 3 beats turned into 4 | *King Heroin* | Chapter 8 |
| A 6-beat sample colliding with a 4-beat drum | The sample triggers just before the strong beat of every other bar | Chapter 7 |
| **7-bar loop against a 4-bar beat** | Makes verse and chorus start at unpredictable positions | Chapter 8 |
| Loop point off the strong beat | *The Light* | Chapter 8 |

→ All of these must be written into `form[].note`, with a note that the rhyme scheme has been adjusted to match (§3 last row).

### 1.6 Common Failures

| Failure | Symptom | Fix |
|---|---|---|
| Not locked | Layers run each on their own, sounding like several pieces of music stacked | Return to ①, rebuild the drums |
| Hidden hi-hat in the sample | Drums sound "dirty," beats blur, yet each track sounds correct on its own | ⑧: filter it out or change the cut point |
| Mismatched eras | One layer sounds like the 1960s, another like an 80s drum machine | ⑨: process uniformly (low-pass, add noise, unify compression) |
| Kick can't be extracted | The kick is low-frequency; "you can't put a low-pass on it" | Find the kick separately (old record or drum machine); the loop supplies only snare and hat (Schloss p0160–0161) |
| Pure samples fall apart in a car | On a good car stereo the low end can't hold up | Add an 808 kick or keyboard bass line, which "thickens considerably" (Schloss p0206–0207) |

---

## 2. Sample Selection and Rules

### 2.1 Digging: Four Levels of Skill

The choice of `timbre` for each sample layer in `roster` depends on the level at which selection stops (Schloss p0097–0099):

| Level | Basis for selection | Typical practice |
|---|---|---|
| **1. Records at home** | The parents' collection | A batch of 1970s core records established the sonic parameters of the style |
| **2. Search for what others have sampled** | Known, previously sampled originals | Shepard: most people start with "finding what others have used," and only later turn to "finding what **I** might want to sample" |
| **3. Judge the vibe from cover and title** | Cover art, band name, song title | "Freak / freaky" in a title almost always has something; "funk" guarantees nothing |
| **4. Read the personnel list and the timbre** | Player credits, label, recorded sound | Samson S.: "Is that Billy Cobham on drums? Does this guy have his own album?"; at an advanced level you can recognize a producer or label by sound |

★ **The criterion at level 4 is the drums** (Oliver Wang, Schloss p0099): *"If you don't want to use drums that everyone else on earth has used, there is a science to picking a specific break from a rock or jazz record. You want your snare to sound a certain way, and your low kick and your ride cymbal too."* The giveaway in a beginner's demo is always that **the drum sample is the same as everyone else's**, or that the drums are pure digital drum-machine sounds: "it just sounds fake."

→ Written into `roster`: for drum voices, `timbre` should not say "snare" but should give **source type + era + processing** ("snare from a 1970s rock record, midrange-heavy, with room").

### 2.2 What to Look For: Target List and Listening Process

| Item | Content | Source |
|---|---|---|
| **Common sample targets** | Breaks, isolated drum hits, bass lines, Fender Rhodes, horns, "ill" guitar tones (like the ones in 007), vocals (shouts and the like) | Schloss p0103 |
| **Targeted search** | Sometimes you search for one specific instrument: flugelhorn, harp, cello | Schloss p0103 |
| **Any genre** | Experienced diggers don't stay in the soul section; they flip through the whole store, since any genre may have something | Schloss p0103 |
| **Look at the grooves** | On vinyl, the groove width of a break section differs and **can be seen with the naked eye**; dropping the needle and listening for a few seconds is enough to judge | Schloss p0102 |
| **Sample "corny" records too** | Two reasons: ① even the corniest record may contain a sincere, valuable passage; ② making a good beat from a corny record is itself a display of skill. Samson S.: "You can use almost anything, even just a hi-hat" | Schloss p0164 |
| **Not irony** | Sampling corny records is not postmodern irony; it is **explaining the process**. Prince Paul: *"That's a good song!"* | Schloss p0163–0165 |

★ For writing the spec: do not describe a sample layer's source as a style label ("jazz sample"). Describe **what it brings** ("a Rhodes chord with room, two beats long, tail cut short").

### 2.3 Rule Table: The Craft Ethics of the Producer Community

Schloss Chapter 5 records the set of rules that sample-based producers among themselves **follow by default, and whose violation gets them mocked by peers** (Vitamin D: "They're rules! It's all following rules," Schloss p0116). They are not law and not aesthetics. **Ethics is an "entry fee": following them only guarantees you are respected, not praised** (Schloss p0147). Aesthetics is a separate matter (§1). The two underlying values of the rules are **physical effort** (going out and finding records yourself) and **intellectual effort** (not using ready-made material, and not using material that is already very good) (Schloss p0146).

| Rule | Content | Recognized exceptions | Source |
|---|---|---|---|
| **No biting** | Do not loop again something another person has already looped; do not reuse a combination of two elements another person has already combined (e.g., someone has used a certain James Brown passage over the "Substitution" drums; you may not pair them the same way) | ① You **flip** it (substantial transformation); ② an obvious **parody / answer** (Premier chopped and rearranged the bass from *Player's Anthem* into *Ya Playin' Yaself*, changing the melodic contour and accents); ③ an accidental collision | Schloss p0120–0124 |
| **Drums may be reused, samples may not** | Strath Shepard: *"Drums can get reused, but samples can't get reused … unless you chop it up really good."* | Individual drum hits (kick / snare / hat) are almost unrestricted | Schloss p0122, p0142 |
| **Sample only from vinyl** | Philosophy (the digging tradition), aesthetics (analog sound quality), practicality (the needle locates a break instantly; when memory is short, sample at 45 rpm and slow it down), and the material existed only on vinyl | Negus I: use CD for clean sound, decided case by case; The Angel: take the clean sound from CD and add vinyl noise | Schloss p0124–0128 |
| **Do not sample other hip-hop records** | That uses other people's digging labor | ① An "open" kick or snare the producer deliberately left (Q-Tip left one in the remix of *The World Is Yours*); ② a short vocal phrase as tribute, but Vitamin D requires that it be **cut in live from a turntable**, not sampled on a sampler; ③ a clear parody (Ice Cube, *Jackin' For Beats*) | Schloss p0129–0134 |
| **Do not sample records you respect** | Unless you can add something or "flip it in a completely astonishing way"; three reasons: disrespect, it is already too good to change, no challenge | Opposing views: Samson S., "If I respect it, I sample it hard"; DJ Kool Akiem, "Sampling is the highest compliment"; Negus I: you must invest your own spirit in changing it, not just lay a drum beat under the melody | Schloss p0134–0135 |
| **Do not use breakbeat compilations** | A shortcut, no education, exploits the labor of predecessors; writing "who sampled it" on a compilation label is snitching. Beni B can even **hear it**: the compilation version is slightly distorted | ① Take only the drum hits, not the whole loop (Negus I); ② you already dug it up and have the original disc, and bought the compilation to avoid collectors' price hikes (Mr. Supreme, Stroman); ③ the earliest *Ultimate Breaks and Beats* is old enough to count as an "original recording" in itself (Samson S.) | Schloss p0135–0144, p0220 |
| **Do not sample two sounds from the same record** | "Thou shall not sample two sounds from the same record": bass line, horns, and Rhodes all taken from one record counts as cheating, because "putting together what already belonged together" has no creativity; **part of the art is combining elements that would not normally be combined** (DJ Kool Akiem) | Continuous loops (when chopping); only drums or very small fragments; within one album, the same artist used at most once | Schloss p0145–0146 |
| **TR-808 exception** | Sampling "the sound of the machine" is not exploitation: people play differently each time and it takes effort to find, while drum machines sound identical every time; sampling an 808 from a record is the same as using the machine itself | — | Schloss p0220 |

★ **The ethical question is not "may you sample it," but "is the use appropriate and creative"** (Schloss p0218). For writing the spec: every sample layer in `roster` must be stated with **what kind of source material it comes from, and whether it shares a source with the other sample layers in the same track**. Layers from the same source may only be a continuous loop from chopping, or drum hits; otherwise, under these rules, it is cheating.

### 2.4 Sample-Based vs. Played: Why Sampling Is the Default

| Argument | Content | Source |
|---|---|---|
| **The preference is for "the sound of the sample," not for "the act of sampling"** | Even with live instruments, the ideal sought is *the sound of the sample*; using live instruments is treated as a "forgivable circumstance" and a second choice | Schloss p0093 |
| **Definition of "live instrumentation"** | Instruments that do not use previously recorded sounds: almost everything apart from turntables and samplers. Some producers don't even count keyboards, because keyboards are more often used to trigger samples than to play long phrases | Schloss p0218 |
| **Conditions for adding a played layer** | It must **support the theme already in the sample** (adding a bass line under a loop to thicken it works; swapping in a full horn section only makes it "hip-hop based"), and it **must sound like the sample** (Domino: "it's gotta blend in"). The Angel goes further and records live musicians, then samples the result | Schloss p0085–0088 |
| **Cyclic sensibility** | Even without loop technology, the formal structure is designed to create an impression of cycling: *"Without knowing the original, you usually cannot tell whether a sample has been heavily processed or merely looped."* | Schloss p0220 |
| **The word "beat"** | Its meaning slid from "a drum sample" to "a whole work," showing that percussion and rhythm are the composition itself in this style | Schloss p0220 |
| **The word "live"** | Here it means **rhythmically exciting**, not "played on real instruments" | Schloss p0221 |

---

## 3. Flow: Notation and Element Tables

### 3.1 Flow Diagram: Notation for Writing Flow Down

The notation used in *How to Rap 2* p0014–0015 can be used directly to write schematic `vocal.phrasing`:

| Mark | Meaning |
|---|---|
| **1 2 3 4 at the top** | The four beats of a bar, used to mark where words fall relative to the beat |
| **Each new line** | A new bar of music |
| **Bold syllable directly under the beat number** | A stressed syllable, sounded **at the same time** as that beat; the anchor where words and music synchronize |
| **Empty space under a beat number** | That beat is a rest |
| **(MM:SS)** | The time in the reference track where the example appears |

Example (*How to Rap 2* p0014–0015, demonstrated with Pharcyde's *Drop* at 00:26): the stresses fall on "**Let** me freak the **funk**, obso-**lete** is the **punk** that talks"; the four bold syllables line up with beats 1/2/3/4; under beat 3 of the second bar and beat 2 of the fourth bar there are no words, meaning rests.

★ **Write into the spec:** a rap section does not need the words, but it does need **this diagram**: one line per four beats, marking which syllables sit on the beats and which beats are empty. Placeholder syllables (da / X) are enough; what the arrangement side needs is the position of stresses and rests.

### 3.2 Set the Flow First, Then Fill in Words: Placeholder Syllables Are Standard Practice

This is the basis for "this skill can specify a rap section clearly without writing out the words":

| Claim | Source |
|---|---|
| Professional MCs usually **work out flow and delivery before writing words** (Royce Da 5'9": I come up with the flow before I write anything down) | *How to Rap 2* p0011 |
| Schoolly D: I don't write lyrics, **I use sound instead of words**. As long as there's a feel and a rhythm, I add words last | *How to Rap 2* p0018 |
| Masta Ace: play the beat and **mumble** until you find a bounce that rhymes and fits the beat, then turn it into real words | *How to Rap 2* p0022 |
| Thes One: flow meaningless syllables over the beat until you get a groove you like; what you end up with is **the syllable count and the pause positions**, and only then do you fill in words | *How to Rap 2* p0022 |
| Tech N9ne: first decide the "style" (this one I want to sound like ping-pong), then fill in words | *How to Rap 2* p0021 |
| Thinking of rhythm first is "often the key difference between high-level flow MCs and ordinary MCs" | *How to Rap 2* p0021 |

**The percussion view of the voice** (*How to Rap 2* p0020–0021): rap's rhythmic skill is closer to percussion than to poetry. Mighty Casey: "Your voice is the drum on the beat, and each syllable is a different drum sound"; Del can write lyrics "the way you'd write a drum score"; Shock G memorizes the positions of words as a **percussion part**.
→ So in `roster`, a rap section can be balanced as a single percussion part (§5 and SKILL §7.5).

**Pocket over content** (*How to Rap 2* p0019): Crooked I: between "very clever content" and "being in the pocket," the latter usually wins; Mighty Casey gave up many clever metaphors for precise placement on the beat. **The arrangement-side trade-off follows the same principle: fix the rhythmic positions first, then fit the words.**

### 3.3 Flow Element Table: How It Lands on the Grid

Rhyme density and how to write multisyllabic rhyme are matters for songwriting. This table covers only the **relation of flow to the beat**.

| Element | Content | Source |
|---|---|---|
| **Stresses on the beat** | Unless the beat is a rest, **stressed syllables must sound at the same time as beats 1, 2, 3, and 4**. Spoken stress and beat stress may differ, but only stresses that land on the four beats make words and music synchronize. This is called **in the pocket** | *How to Rap* p0084–0085 |
| **Basic grid** | The most common rap rhythm divides a bar into **16 parts**. Since about 1980 this has been the basis of most rap rhythms; you can count 1–16 along while listening | *How to Rap 2* p0023–0024 |
| **Speed effect of 16ths** | At mid tempo it sounds like **conversation and everyday speech**; at fast tempos it becomes rapid-fire talk | *How to Rap 2* p0025–0027 |
| **32nds** | Double-time; also used for short, rapid bursts | *How to Rap 2* p0029–0032 |
| **Triplets** | Three syllables placed in the space of two sixteenths. Uses: embellishments in conversational flow, **launching a section** (like a drummer's small roll before a section), repeated phrases, interruption by extra syllables, creating swing over slow beats, spanning four sixteenths, and unusual positions | *How to Rap 2* p0033–0045 |
| **Flam** | Two syllables placed close enough to merge into one sound: weak-strong (the-pain), strong-weak (when-I), weak-weak-strong, strong-weak-weak, corresponding directly to drum flam / ruff / drag | *How to Rap 2* p0045–0048 |
| **One syllable per beat** | Suddenly slowing down to interrupt rapid-fire talk and focus on a word (ho-tel, mo-tel) | *How to Rap 2* p0049 |
| **Lazy tails** | The phrase is on the beat, but the final word of the phrase **slides off the beat**, stretching its initial consonant (cccooking). The hallmark of West Coast gangsta rap | *How to Rap 2* p0050–0053 |
| **The next syllable slides onto the beat** | When the slide is large enough, the syllable that should have landed slides off, and **the preceding syllable lands on the beat instead** (One, two, three, and to **the** four) | *How to Rap 2* p0053 |
| **Staccato** | Shorten each syllable so it is "choppy," so each syllable is clearly heard hitting a beat point; the more staccato, the more it sounds like percussion; rapid-fire talk must be staccato to be understood | *How to Rap 2* p0129–0131 |
| **Crossing bars** | A verse need not start on beat 1 or end at the end of a bar (N.O.R.E. starts at the end of the previous bar; Clipse enters after beat 2 and rests on beat 3; O.C. enters on beat 4) | *How to Rap* p0088, p0092 |
| **Pushing and pulling** | Phrase generally slightly ahead of the beat → hurried, tense; slightly behind → relaxed, nonchalant (Snoop, Evidence). Evidence: being able to **stay behind the beat** consistently is a talent, and many people who can hit the drums precisely cannot do it | *How to Rap* p0269–0270 |
| **Repeated phrase with changed rhythm** | Repeating the same line with a different rhythm is a means of internal variation within a section | *How to Rap 2* p0064–0070 |
| **3/4 and other meters** | When the meter is not 4/4, the flow must be rewritten (rhymes land on beat 3) | *How to Rap 2* p0070 |
| **3-bar loop** | If the beat cycles every 3 bars, the words must be written specifically for it: use a three-line multi-liner, or a "pair plus a single-liner." Even-bar rhyme schemes will fall out of step with the music's restart points | *How to Rap 2* p0203–0204 |

### 3.4 Rests: Four Uses and Common Positions

| Item | Content | Source |
|---|---|---|
| **Definition** | No syllable is sounded on beats 1/2/3/4 | *How to Rap 2* p0055 |
| **Four uses** | ① Breathing; ② dividing sections (Eminem's *Yellow Brick Road*: the first eight bars of the second verse have no rests, then the flow changes after a rest at the end of bar 8); ③ adding rhythmic variation; ④ emphasizing content: after an important line, rest one beat in the following bar so listeners can absorb it | *How to Rap* p0140–0143 |
| **One-beat rest + couplet** | The second line holds the punch line; two lines are grouped and separated by a one-beat rest | *How to Rap 2* p0055–0057 |
| **Two-beat rest** | Makes a short opening statement (Public Enemy's "Bass!") | *How to Rap 2* p0057 |
| **Three consecutive beats of rest** | Landing a single word only on beat 4 creates a sing-songy feel | *How to Rap 2* p0062 |
| **Separating content or changing rhyme scheme** | Place a rest on **bar 8 or 9 of a 16-bar section** to separate content or change the rhyme scheme | *How to Rap 2* p0058–0060 |
| **Emphasizing weak beats** | Rest on beat 4 to push attention onto a word on a weak beat (the word "Mama" in 2Pac's *Dear Mama*) | *How to Rap 2* p0063; *How to Rap* p0143 |
| **Write breaths into rests** | Gift of Gab: while rhyming you are exhaling; when you find a pause, take a quick breath and continue. Masta Ace: after trying it out, if you run out of breath you delete words to make space; when writing, you have to leave breath points, otherwise "the rhyme doesn't sound right" | *How to Rap* p0141, p0285 |

### 3.5 Rhyme Landing Positions (Arrangement Side)

| Position | Effect | Source |
|---|---|---|
| Lands on **beat 4** | Most common, most prominent | *How to Rap* p0120–0122 |
| Lands on a **weak beat** | Less prominent, more conversational | *How to Rap* p0120–0122 |
| **Shifting a whole phrase** | Tajai: scoot it over: add a few words at the start and remove a few at the end, and the rhyme lands in an unexpected place | *How to Rap* p0121 |
| Common couplet setups | First line rhymes on beat 4, second line rhymes on the weak beat after beat 4 (punch lines hit harder); rhymes on both beats 2 and 4; alternating beats 3 and 4 | *How to Rap 2* p0189–0194 |
| **End signal** | A shortened final line (rhyme on the weak beat after beat 3) marks the end of a section | *How to Rap 2* p0189–0194 |
| **Sudden change in rhyme density** | Switching from few rhymes per bar to many and back again **is itself a section signal** | *How to Rap 2* p0203 |

---

## 4. Delivery Parameter Tables

**The sound is the first thing listeners hear, and it decides whether they keep listening** (*How to Rap 2* p0072). Three further kinds of non-word sound can be used as delivery (p0149–0151): saying words while laughing or crying; bodily sounds such as spitting, kissing, sneezing, or hiccupping; and **loud inhalation treated as a syllable placed inside the rhythm**. The dimensions below can be allocated section by section, and written into `vocal.delivery` and `vocal.chorus_variation`.

### 4.1 The Eight Dimensions

| Dimension | Options and effect | Which sections to assign it to | Source |
|---|---|---|---|
| **Overall pitch** | High: easily **cuts through** other elements in the backing, often used for playful sections (B-Real, Q-Tip). Mid: ordinary speaking voice. Low: **weight and authority**, for serious subjects (Chuck D, Scarface) | Give high-pitched voice to dense backing sections; give low pitch to serious sections | *How to Rap 2* p0078–0079 |
| **Pitch variation** | Monotone: calm, conversational, **more like percussion** (the drum also repeats the same pitch), does not overpower the beat, avoids sounding silly. Varied: adds personality and emotion | Monotone for sections that showcase the beat; varied for emotional sections | *How to Rap 2* p0080–0081 |
| **Per-word pitch** | Raising a word or syllable: adds variety, emphasizes a point, persuades, expresses fear or asks a question. Lowering: serious or authoritative; **falling pitch at the end of a line = sense of finality**; a whole line from low to high = gradual urgency, **sliding into a verse**; a whole line from high to low = strong statement, **ending a verse**; hoarseness often appears together with lowered pitch | First line of a verse uses rising pitch; last line uses falling | *How to Rap 2* p0112–0123 |
| **Volume** | Loud and forceful: cuts through a dense backing (Chuck D), live shows, party call-and-response, authority. **Slightly above speech**: keeps a conversational feel with energy, suits long, showy verses (requires good breath control). Quiet: relaxed, laid-back tracks, leaves room to raise volume later. Whisper: adds variation, atmosphere or eeriness | ★ Do not write "louder"; write **which section uses which level** | *How to Rap 2* p0082–0091 |
| **Timbre** | Nasal (B-Real), unpredictably gravelly (Lil Wayne), rough (Method Man, DMX, suggesting maturity), smooth (Q-Tip, Snoop; **blends better with the other instruments on the track**), shrill (Mystikal, frenetic energy), breathy (MCA, relaxed and lazy) | A smooth beat pairs with smooth voice. Crooked I: when the backing has many instruments, tune the voice to sound "like one of the instruments," **flowing with the beat instead of cutting across it** | *How to Rap 2* p0093–0096 |
| **Duration** | Stretching individual words = emphasis, adds character (2Pac, "enemiiies"); **stretching the first word of a phrase to launch a section** (Beastie Boys, "Nooooow"); stretching the last word of a phrase so the sound lingers. **Stretching pushes the following words later, changing the rhythm.** For shortening see staccato in §3.3 | Use a stretched opening word at the entry to a section | *How to Rap 2* p0125–0131 |
| **Stuttering / repetition / trills** | A stutter on the first sound launches a section (St-St-St-Straight), like a small drum roll; repeated words in a specific rhythm, or **synchronized to a drum fill** (Andy Cat set "Fast, fast, fast, fast" against a drum fill to bring the track from half-speed back to full speed); trills as ornament on a held note | Section entries, fill positions | *How to Rap 2* p0132–0140 |
| **Breath** | Inhalation as a syllable (Method Man); sighing to open a line; exhaling through a word; deliberately running out of breath (as a style); **when recording a whole section in one take, breathing must adapt to the rhythm**, and inhalation sounds stand out more | Long verses require planning breath first | *How to Rap 2* p0151–0153 |

### 4.2 Emotional and Persona Types (The Option Set for `vocal.persona`)

All six types come from *How to Rap 2* p0168–0170:

| Type | Vocal approach |
|---|---|
| Energetic / wild | Busta, ODB: volume, timbre, and pitch all vary; noise added |
| Playful / bouncy | B-Real, Pharcyde: higher pitch, onomatopoeia |
| Serious / authoritative | KRS, Chuck D: loud volume, deep tone, uses rising and falling pitch for statements and questions |
| Cool / relaxed | Snoop, Slick Rick: normal volume, smooth timbre, lots of half-sung melody |
| Introspective / poetic | 2Pac, Nas: restrained volume and timbre, controlled pitch at key moments |
| Angry | Ice Cube, Mystikal: loud volume, rough, raised pitch on particular words |

**Emotional rule** (*How to Rap 2* p0172–0175): emotion must be **audible in the voice** through changes in pitch, volume, timbre, vibrato, and melody. Expressing anger with a soft voice means listeners won't know it is anger. You can also deliberately make the emotion of the voice oppose the content. Emotional sections use a single take recorded in one go; if the rhythm drifts slightly, it can be fixed with punch-in.

### 4.3 Accents and Character Voices

Motives for switching voice and how to do it (*How to Rap 2* p0100–0111): **the native accent** keeps credibility when the content concerns real experience. **Switching accent** creates an alter ego, gives narrative characters distinct styles, or serves humor. **Regional accents** convey different settings (city vs. open countryside); when switching to a foreign accent, slang and phrasing usually change along with it. Story songs also include male and female voices, telephone effects, and self-dialogue.

★ Write into `vocal.persona` / `form[].note`: **which section switches voice, and to whom.** This is where punch-in happens, and it also determines whether this section needs its own vocal track in `roster`.

### 4.4 Recording and Take Notes

- A hook can change voice frequently; the verse stays consistent (Yukmouth, *How to Rap* p0263).
- Use **punch-in** to change voice for different roles or situations (Slick Rick's narrative, *How to Rap* p0289).
- A take recorded in one go keeps its cracks and other flaws, which makes it "more real, more raw" (*How to Rap* p0293).
- On the mix side, the same principle: adding too many elements gets cluttered, they mask one another, and it turns to mud. **Less is more** (*How to Rap 2* p0145).

---

## 5–7. Vocals, *Dilla Time* Citation Locations, and Glossary (The Other File)

The section structure, ad-libs and vocal sound effects, citation locations, and the glossary are in [reference-vocal.md](reference-vocal.md), numbered to match §5–§7. The full text of the flow elements, delivery dimensions, rap section structure, and vocal-backing relationship from SKILL §7 is also there (§8–§11).
