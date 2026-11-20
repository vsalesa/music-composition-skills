---
name: mc-arrangement-arch
description: Arrangement architecture - the shape of a track over time rather than its notes. Energy curve and dramatic arc, subtractive arranging, layering as form (instrument entry/exit events), formal skeletons and section proportion, arrangement-hook placement, why the second verse must not be a copy, and how to end. Use when the user is arranging a song and asks how to structure it, when a track "goes nowhere" or "sounds flat", when every section sounds the same, when a generated track sounds like AI (monotonic energy, unchanging instrumentation, no subtraction), when deciding where instruments enter and leave, or when filling the arrangement/energy_curve/subtraction_events/roster fields of an ARR-SPEC. Keywords: arrangement structure, energy curve, subtraction, instrument entry/exit, section proportion, hook placement, ending.
---

# Arrangement Architecture

**This skill governs the shape of a song over time, not its notes.**

Harmony, melody and orchestration decide "what sounds at this moment"; arrangement architecture decides "how the listening experience changes from second 0 to second 220."
A song can have every chord right and every instrument sounding good, and still be so flat that nobody can bear to listen to it. The problem lies at this layer.

> **This layer is the main battleground for "not sounding like AI."**
> The defaults of generative models are concentrated almost entirely here: energy rises monotonically, the lineup never changes from start to finish,
> sections are rigidly locked to multiples of 8, subtraction is never used, and endings are all identical.
> These are not timbre problems that a better model would make disappear; they are the **absence of structural decisions**.

## Which Sections to Read for Each Task

| What you need to do | Read |
|---|---|
| Plan a song's structure from scratch | §1 required before drafting → §2 energy curve → §4 formal skeleton → §3 subtraction |
| The song is "flat," lacks drive, is unbearable to listen to | §2 energy curve, §3 subtraction |
| Every section sounds the same | §5 lineup is form, §6 the second pass must not be a copy |
| The generated output sounds like AI | §9 diagnostic path (look up by symptom) |
| Not sure when instruments should enter or leave | §5 lineup is form |
| How long should sections be | §4 formal skeleton |
| The song is hard to remember | §7 hook placement |
| Not sure how to end | §8 three kinds of ending |
| Filling the arrangement section of ARR-SPEC | §10 field mapping + §11 must-pass checklist after writing |

## Boundaries: What This Skill Does Not Cover

| Not covered here | Where it lives |
|---|---|
| How specific instruments are orchestrated, how ranges are arranged | `mc-orchestration` |
| How frequency bands are divided, who competes with whom for frequency | `mc-texture-layering` |
| Making drums, bass, guitar and keys sound like real players | `mc-rhythm-section` |
| Harmonic motion within a section | `mc-harmony` |
| Historical forms (sonata form, etc.) | `mc-form` |
| How vocals are sung | `mc-vocal-direction` |
| EQ, compression, mastering | Mixing; this package only supplies the `mix_intent` brief (`mc-mix-intent`) |

This skill manages only **the relationships between sections** and **the events on the timeline**.

---

## 1. Required Before Drafting (Four Items; Do Not Draw the Timeline Until All Four Are Filled)

These four items are not a formality. Generated material sounds like AI to the ear not because its timbre is poor,
but because **no one made a choice**, and choices happen precisely at these four questions.

| Required item | Question to answer | What an inadequate answer looks like |
|---|---|---|
| **① Energy target** | Which section holds the highest point of the whole song? Which section holds the lowest point? | "The chorus is the highest"—and the lowest? Without a lowest point there is no highest point |
| **② Subtraction event** | Where do you **take things away**? What is removed? Why there? | None at all → see §3; this is one of the strongest AI signals |
| **③ Lineup entry/exit** | Which instrument **enters partway through**? Which **leaves early**? | Everything present from start to finish → see §5 |
| **④ Non-vocal memory point** | Without the voice, what can the listener remember? | Cannot say → see §7 |

**Self-check**: if you can answer these four questions in 30 seconds, you have not yet thought it through; if you cannot answer them at all, you are not ready to begin.

---

## 2. Energy Curve: The Dramatic Arc

### 2.1 The Model

DeSantis carries the **dramatic arc** of narrative media (the diagram is called Freytag's pyramid) directly over to music (p0276):

| Arc stage | In the story | In the music |
|---|---|---|
| **Exposition** | Introduces characters and setting | Introduces the musical material the whole song will use (melody, harmonic progression, rhythmic motif) (p0277) |
| **Rising action** | Conflict between protagonist and opponent | **Variations or mutations** of the exposed material (p0277) |
| **Climax** | Turning point | Often marked by a **sudden increase in textural density**, which in EDM is "the drop" (p0277) |
| **Falling action** | Resolves unresolved conflict | Often mirrors the activity of the rising action (p0277) |
| **Dénouement** | Characters return to normal | Restatement of established material (a repeated chorus) or gradual dissipation (p0278) |

**The scale is nestable**: a single melody can be one arc (rising to a peak and falling back; the melodic contour itself visually forms a Freytag pyramid);
a one-hour DJ set is also one arc (p0278).

### 2.2 Rule: The Energy Curve Must Have a Drop

**★ Strong rule**. This is the best-evidenced rule in this skill.

> **Measured**: of 62 real multitrack arrangements, **62/62 all have an energy drop** (95% interval 94–100%).
> Not a single one rises monotonically.

Monotonic rise is precisely the most stubborn default of generative models.

**Self-check action**: write each section's energy as a sequence from 0 to 10. If this sequence never decreases, what you have written is not a song but a slope.

**Failure conditions**:
- **Forms without a clear climax build, such as dub and minimal techno**—exceptions that DeSantis himself points out:
  in this kind of music dramatic tension is created "in a completely different way, through **sound design** and attention to subtle changes in static textures over time" (p0278).
  Here a flat energy curve is part of the style itself, not a defect. **But you must be able to say that you are taking this path.**
- Very short works (a 15-second advert, a short game loop) do not have room for a full arc.

### 2.3 A Claim Not to Use as a Rule

"There should be a single energy drop before the climax (a pause before the chorus)"—this idea is **widely circulated, but our measured data contradict it**:

| Evidence | Result |
|---|---|
| Full measurement of 62 songs | Only 22% match |
| 7 human-annotated ground-truth songs | **5/7 = 71%** match |

The gap stems from the reliability of section-boundary detection (the full-set run relied on automatic detection; the human-annotated run used ground truth).

**So this skill does not write it as a rule.** It is a **technique worth trying**, not a constraint that must be obeyed.
You may use it, but do not insert an unneeded silent gap simply because "the textbook says to leave space."

### 2.4 ★ Why a Chorus Stuffed Full Sounds Weaker: Five Types of Full Tutti and One Overall Rule (Yang Liqing)

Full tutti falls into five types (Vol. 2, p0361–0378): **unison type**, **chordal-power type**, **polyphonic type**, **thematic type**, and **multi-factor compound type** (there is also a colouristic full tutti). Each has its own character:

| Type | Character |
|---|---|
| Unison type | Very loud across a wide range, **but lacks harmonic support, so saturation and fullness will be insufficient** (p0361) |
| Chordal-power type | Simple structure, sonic "focus" concentrated; when well arranged, the chord tones support and resonate with one another well, **the most powerful of all types** (p0362) |
| Polyphonic type | A heterogeneous texture full of internal tension and drive, mostly used for development, transition, and pushing toward a climax; **pure polyphonic type is "constrained by the breakdown of force," and its volume cannot rise**; to get force, follow it with a full tutti of homophonic character to achieve the satisfaction of a climax (p0363–0364) |
| Thematic type | See the two counterexamples under the overall rule below |
| Multi-factor compound type | Very wide range, many instruments in the most tense upper register, with both tension and brightness high; harmony placed only in the brass and concentrated in the middle register, leaving ample room for the bass line and the highest melody, so resonance is not impaired (p0372) |

★ **Overall rule** (p0365–0369): for a full tutti aimed at showing the power of the orchestra, **the clearer the textural layers, the more uniform the rhythm, and the simpler the harmonic structure, the better the resonance and the stronger the effect**.
When a chorus stuffed full sounds weaker rather than louder, it is usually because all three have been done in reverse: the layers are blurred together, each layer's rhythm goes its own way, and the chords are stacked in complex ways.

Three remedies (p0368–0372):
- **For solidity, strengthen the middle register first**: place horns, trombones and tubas in the rich middle register, densely arranged without leaving out notes
- **For brilliance, raise the register**, or add a layer of reinforced overtones an octave above (divisi violins repeating the melodic line in the very high register, "reinforcing overtones and improving resonance")
- **For tension, place the main parts in tense registers**, at the cost of reduced resonance

Beam-type complex harmonic relations not only fail to let overtones support one another, but also cause overtone interference that compromises purity; their loudness is inferior to a full tutti of simple chords (p0363).
**If you want "big," do not simultaneously want "complex"; you can have only one of the two.**

---

## 3. Subtraction: Arranging Is Carving, Not Painting

### 3.1 Arranging as a Subtractive Process

Fear of an empty timeline is the same as fear of an empty page (p0281). The conventional approach is to fill it gradually from left to right,
like painting on a blank canvas. DeSantis argues the opposite (p0281):

**Step 1: fill quickly**
- Immediately fill every track across the entire timeline with material (p0282)
- The aim is not to make a good arrangement, but to **turn "from nothing to something" into "from something to nothing"** (p0282)
- **★ Hard time limit: no more than 20 seconds**. If you run over, you are making creative decisions, and you must resist that temptation (p0282)
- Use copy and paste, duplicate, drag the right edge of clips (p0282)
- **Do not** consider section names, and **you do not have to** use all the material (p0282)

**Step 2: carve away by subtraction**
- Start chiselling from a solid block of raw material, carving out space (p0283)
- **Basis for judgement**: "it is often easier to hear when a combination is bad than to imagine a good one"
  (easier to hear when something is bad than it is to imagine something good) (p0283)
- When a section lasts too long, your instinct will tell you it needs change (p0283)

**Reverse variant**: if the genre's signature is density that increases or decreases over the course of the song,
you can **work backwards from the ending to the beginning**, removing more the further back you go (p0284).

**Failure conditions**: this process presupposes that **you already have enough material in hand**.
If the material is insufficient, "fill quickly" produces a pile of repetition, and what you carve out is also repetition.

### 3.2 The Power of Erasure

> "It seems that perfection is reached not when there is nothing left to add,
> but when there is nothing left to take away." (p0286)
> (Perfection is reached not when nothing remains to add, but when nothing remains to take away.)

**The core counter-intuitive judgement**: when music feels "small," "weak," or "lacking force,"
the remedy is often to **remove** rather than add (p0286).

**Principle**: musical space is like a canvas with fixed boundaries. **Each part added forces all the other parts to compete harder for the listener's attention** (p0286).
So the more you add, the weaker each individual element becomes.

**★ Precondition (DeSantis states it explicitly)**: the subtraction strategy **works only if your existing parts are already as good as they can be** (p0286).
Removing a few items from a pile of mediocre material leaves the rest mediocre.

**Clarification on whether this is minimalism** (p0287): it is not.
- Music whose rate of change is slow will sound minimal even when it has many elements
- High-density music (some commercial EDM) that **deliberately limits the number of parts sounding at once** remains clear and open
- Core principle: **add parts only as necessary, and mercilessly remove whatever contributes nothing**

**"Thinning out"—an intermediate means beyond outright removal** (p0287):
1. Reduce the **number of notes** an instrument plays
2. Shorten the **decay time** of sustained sounds so they yield quickly

### 3.3 Rule: At Least One Clear Subtraction Somewhere in the Song

> **Measured**: **70%** of the 62 songs have a clear subtraction (energy span ≥30%). **A tendency, not an iron law.**

**Self-check action**: state which bar your subtraction event falls in, what is removed, and why it happens there. All three must be answerable for the claim to count.

**Failure conditions**: the 30% counterexamples are mainly sustained high-density dance and noise-oriented works.
If you are going that way, state your reason; do not cut a drum part just to satisfy the rule.

---

## 4. Formal Skeleton and Section Proportion

### 4.1 Borrow the Skeleton, Not the Material

Problem: the material exists, but when arranged it is unsatisfying, because **the sense of internal proportion is missing** (p0290).

DeSantis's method is to **measure proportion from a model** (p0290–0292):

1. Find a song whose form works and which inhabits the same "musical universe" as yours
2. Create an empty project and place it at bar 1
3. **Carefully adjust the tempo until the DAW grid and the song's actual beat align perfectly**—if you get this step wrong, everything after will be wrong
4. Listen, and each time you hear a formal division (or an interesting moment within a section), stop and drop a marker
5. Carry on to the end
6. Give each marker a **descriptive or functional** name ("Verse," "Bass starts") so you can understand it later without re-listening
7. **Delete the original audio and keep only the markers**—this is a **formal skeleton** whose effectiveness is already proven
8. Fill it with your own material

**The most valuable part of this method is step 7**: what you take is proportion, not content. A skeleton does not constitute plagiarism, and its source cannot be heard.

**DeSantis's own caution**:
> "once you actually start employing this in practice, you may find that your own musical
> materials don't naturally fit into the arrangement skeleton perfectly."

If your breakdown "wants" four more bars, **trust your instinct absolutely** (p0292). The skeleton is for getting started; once you are in flow, move freely.

### 4.2 ★ A Real Disagreement: Should Sections Be Multiples of 8?

Two sources state directly conflicting positions. **Both are right, and they must be read together**:

| Source | Position |
|---|---|
| DeSantis (p0291) | In most electronic genres, formal divisions occur at **multiples of 4 or 8 bars**; listeners have been "primed" to expect divisions at these points |
| This library's 20-item self-check #3 + item 1 of the fourteen AI-tell items (`mc-ai-tell-audit` §2) | **Sections that are all whole multiples of 8** are among the easiest defaults for a generative model to be heard as such |

**Reconciliation**:
- **The primed expectation is real.** The great majority of sections landing on multiples of 8 is correct; breaking it makes people "lose count of the beats."
- **The problem is not "being a multiple of 8" but "all of them being so."** A human-written arrangement will break the pattern **at one point**:
  a 6-bar lifting phrase, a second verse 4 bars shorter than the first, a tag that hangs 2 bars off the end of the chorus.
- **So the rule is: treat multiples of 8 as the default, but break the pattern at least once across the whole song, and be able to say why you broke it there.**

> **Measured reference**: among the 62 real arrangements, almost all contain sections that are not multiples of 8—
> but this item depends on automatic section detection, marked `no_truth`, so **the figures are not reliable and serve only as corroboration**.

### 4.3 General Definitions of Sections (p0293–0294)

| Section | Length | Function | Key points |
|---|---|---|---|
| **Verse / A** | Usually 16 or 32 bars | Main body of the song; tells the "story" when there are lyrics | Recurs |
| **Chorus / B** | Comparable to the verse | **Contrast** with the verse; usually contains the **hook**; the **musical resolution point** (the verse creates tension) | Recurring verses share music but not lyrics; **recurring choruses usually share both music and lyrics** |
| **Bridge / C** | — | Contrast with verse and chorus | **Usually appears only once in the whole song**; often in a **different key**, using unusual chord progressions, or with texture density and energy markedly different; in some genres used as an instrumental solo |

**Ordering convention**: the first chorus comes after the verse (though some songs open with the chorus); the bridge usually comes after at least one verse plus one chorus (p0294).

### 4.4 Where to Break It: Bar-Count Conventions in Japanese Pop Sections (Fujitani)

§4.2 says to break the multiple-of-8 pattern at least once; this table gives **the positions where the length is conventionally not 8** (Fujitani p0061–0062):

| Section | Conventional length |
|---|---|
| Intro | 4–8 bars; 32 is also possible, but without enough persuasive force it grows tiresome halfway through |
| 1A | Basically 8; 16 also occurs, in which case the form is A–A'–B–chorus, with the last 8 slightly different from the first 8 |
| 1B | **Half of 1A**, or equal in length to 1A |
| 1 chorus | 8 or 16 |
| Interlude | Interludes after a large section are short, **4 at most** |
| 2A | ★ **If 1A is 16, 2A takes 8**; if 1A is 8, it stays unchanged |
| 2B, 2 chorus | Equal in length to 1B and 1 chorus |
| D melody (big chorus) or interlude | Around 8, usually made very full |
| Final chorus | Equal in length to the previous two passes, or **double**; when doubled, the first half is quiet and the second half grows livelier as it nears the chorus |

Three natural "break" points: 1B is half of 1A, the interlude is at most 4, and 2A is halved. Once you use one of these, the §4.2 self-check is passed, and you do not need to invent another irregular section.

## 5. Lineup Is Form (Layering as Form)

**This is the most underrated section of this skill, and the one with the strongest measured evidence.**

The boundary between sections is, in many cases, not a change in harmony but a change in **lineup**—an instrument added, or one removed.
**The entry and exit of instruments is itself form.**

### 5.1 Two Strong Rules

> **Measured** (62 real multitrack songs, instrument by instrument on actual separate tracks, not estimated):
>
> | Rule | Hits | Interval |
> |---|---|---|
> | An instrument must **enter partway through** | **59/59** | 94–100% |
> | At least one instrument must **leave early** | **59/59** | 94–100% |
> | The opening should not lay every instrument in at once (presence at the opening ≤60%) | 54/59 | 82–96% |
>
> All three are **strong rules**. 59/59 means that in this corpus **not a single song is an exception**.

Contrast with the default of generative models: **the lineup stays the same from start to finish**. This is item 3 of the fourteen AI-tell items (`mc-ai-tell-audit` §2),
and the measurements tell us that human arrangers **never** do this in any of the songs.

### 5.2 Implementation: Write an Entry/Exit Event Table

Every instrument must be able to answer three questions:

| | |
|---|---|
| **Which frequency band it occupies** | If you cannot say, you will not know whom it competes with for frequency (details belong to `mc-texture-layering`) |
| **When it enters** | Specified down to the section |
| **When it leaves** | ★ **An instrument for which you cannot say "when it leaves" is usually the one that flattens the arrangement** |

**Self-check action**: sort the roster by entry and read it from top to bottom—
you should be able to see how the song's lineup builds up layer by layer. If you cannot read any layering, there is no layering.

**A real sample** (an alt-rock song from Cambridge-MT, measured):

```
I1  Drums / Bass / ElecGtr1–6 / LeadVox      ← six guitars in the opening
I3  +ElecGtr7,8  +BackingVox1
V1  +Organ1,2
C1  +HandClaps +Organ3 +BackingVox2 +VocalSFX1
V2  +Tambourine +BackingVox4,5
C2  +ElecGtr9 +BackingVox3                    ← by the second chorus, nine guitars and five backing-vocal groups have piled up
```

Note that it is **not** "everything that is going to enter enters in the opening," but rather that almost every section brings something new in.

### 5.3 Failure Conditions

- **Minimal lineups** (a demo of voice plus one guitar, solo piano) lack enough layers to enter and leave.
  In such cases "form" has to be carried by register, dynamics and texture density rather than by adding or removing instruments.
- **Some electronic genres** derive their sense of sectioning from filter sweeps and effect amounts, not from adding or removing instruments.

---

### 5.4 ★ The Rhythm of Timbre: The Frequency of Timbre Changes Is Also a Parameter to Plan (Yang Liqing)

Harmony has a "harmonic rhythm" (the number and rhythmic character of root changes), and timbre has one too: **the colour rhythm formed by how often the timbre changes** (Yang Liqing, Vol. 2, p0381).
It sometimes coincides with and sometimes diverges from the rhythms of melody and harmony, and it is usually **more leisurely** than they are (p0381). Differences between styles of different eras
are to a large extent expressed in three things: how often timbres change, how they are combined, and how they contrast (p0383).

**How to set the frequency** depends on the section's structural function within the whole song (p0397, p0400):

| Section | Timbre rhythm |
|---|---|
| Statement of theme, summary and recapitulation | **Relaxed and unhurried**. The book's example: a 10-bar melody played in one breath by three flutes, with the accompaniment texture almost unchanged |
| Development, connection, transition | **Frequent, with large jumps**. Example: each time the motif splits and shifts, the timbral allocation changes bar by bar, and no combination repeats |
| Fast pieces | Change cautiously; changing too often causes auditory and even psychological fatigue |
| Slow pieces | Moderately increasing the frequency of change is an effective way to reduce a sense of monotony |
| Long works | Economise, leaving room for what follows |
| Short works | Increase variety appropriately |

You can also **deliberately lower the frequency**, treating a large passage as a "block of colour" (as in *Boléro* or *Atmosphères*); that is an expressive intention, not an oversight (p0397).

**Practical use**: when writing the entry/exit event table (§5.2), count in passing how many times each section changes timbre. The statement sections and the development sections should have clearly different frequencies;
a single frequency across the whole song is the version of "flatness" from §2.2 applied to the colour dimension.

## 6. The Second Pass Must Not Be a Copy

**Symptom**: the second verse is identical to the first, and the second chorus is identical to the first chorus.
Listeners' attention drops when they hear it a second time.

DeSantis offers three categories of variation techniques (Creating Variation 1/2/3):
**clone-then-mutate**, **generational mutation**, and **note transformation**.

**The least effortful and most effective approach is not to change the notes but to change the lineup**—the second verse should be **sparser** than the first,
not fuller. This runs counter to intuition: many people add things on the second pass when they should be subtracting.

★ **This rule is conditional, and the two sources are placed side by side**: Fujitani says the opposite. If 1A has only piano and lead vocal, 2A should add drums or bass, or backing vocals (p0059),
because once a section has been completed, an unchanged arrangement will make listeners feel "here we go again." Both are right; **the difference lies in the density at the starting point of 1A**:
if 1A is already a full lineup, 2A should subtract; if 1A is a minimal opening, 2A should add. **The criterion is not adding or subtracting; it is that 2A must be different from 1A.**
Fujitani offers two further low-effort methods: in a band arrangement, change only the drum pattern of 2A; or give 2A's first bar a break in which only the voice remains, with the rest entering in the second bar (p0059).

> See the sample in §5.2: in the measurements, A2 (the second verse) has **strings and half of the guitars drop out**, making it thinner than A1.

**Self-check action**: list the differences between A1 and A2. If you cannot list even one, go back and revise.

**Failure conditions**: some forms (such as loop-based house) keep the second pass identical as part of their style;
even so, there is usually some change on at least one layer (a different hi-hat pattern, an added pad layer).

---

## 7. Hook Placement: Non-Vocal Memory Points

**Required field**: `arrangement_hook`—something the listener can remember without the voice.

It can be: a riff, a signature timbre, or a recurring sonic event (a single sample hit, a riser).

**Why it is required**: lacking this item is the main cause of "fine while listening, but forgettable."
A vocal hook relies on words and melody, but **instrumental sections, intros, interludes and outros have no voice**—what holds the listener's attention during those times?

**Three decisions for placement**:

| | |
|---|---|
| **First appearance** | The earlier the better. The listener's attention is most focused in the first 20 seconds |
| **Recurrence positions** | At least 3 times, and **not evenly distributed**—even spacing is mechanical |
| **Variation** | Change it a little on the final appearance (change timbre, shift an octave, extend) |

**Self-check action**: without looking at the score, can you hum this hook? If you cannot, it is not a hook.

---

## 8. Three Kinds of Ending

The default for generative models is a "3:30 fade-out," or simply an abrupt stop. DeSantis offers three routes (p0308–0309):

### ① Mirror
Play the layers that built up at the opening back in reverse.

```
Kick only (8 bars) → +other percussion (8) → +bass (8) → +harmony and melody (8)
→ −harmony and melody (8) → −bass (8) → −other percussion (8) → kick only (8)
```
**Suitable for**: songs that open by building up layers. The symmetry itself is the structure.

### ② Loop and add/subtract

Find a loop and repeat it, **adding one layer** or **subtracting one layer / thinning out** on each pass (p0309). The two directions produce two kinds of ending:

| Direction | Result |
|---|---|
| **Add one layer per pass** | Density and tension keep piling up, closing at the fullest point |
| **Subtract one layer or thin out per pass** | **The song closes weakly rather than forcefully** |

**Difference from ①**: ① is symmetrical adding and subtracting—stacking to the top and then retracing the same path; the structure is the symmetry itself.
② **does not require symmetry**: it can only add, only subtract, or stop halfway through an addition.

**How to choose the loop**: choose a section that **can loop indefinitely without sounding broken**.
This is the same judgement that underlies ③ fade-outs: jagged, asymmetric or rough material is unsuitable for both.

**What to change on each pass**: you do not have to change only one layer per pass.
Thinning can be done by removing a whole instrument, reducing the number of notes an instrument plays, or shortening the decay time of sustained sounds (see the subtraction section, §3).

★ **It is a pair with the maximum-density method used in the composition stage** (see `mc-texture-layering` reference §6.2):
the maximum-density method first stacks the fullest section vertically and then reduces downward, producing several **sections** of different densities;
loop add/subtract changes density **within one section**, pass by pass. The former determines the section table; the latter determines how things move within a section.

**Self-check**: do you change something on every pass, or only every other pass? Changing it on every pass makes people hear a mechanical quality;
**the pass you leave untouched is the time the listener uses to confirm the loop**.

### ③ Fade out
**It has preconditions and is not a casual choice**:
- Electronic musicians are generally negative about fade-outs, because tracks with fade-outs are **hard to use in DJ mixes** (p0309)
- The philosophical implication is that "this song might never end," **so a fade-out is appropriate only when you have settled on ending material suited to indefinite looping** (p0309)
- **Material unsuitable for fading**: jagged, asymmetric, "rough" sections (p0309)
- **Timing**: if you are doing mastering, **the fade-out should be made at the mastering stage**—the way a fade sounds differs enormously before and after mastering compression (p0309)

**Self-check action**: which of the three did you choose? If you cannot say, you have defaulted to a fade-out, and that is the AI choice.

---

## 9. Diagnostic Path: Look Up by Symptom

When generated output is wrong, start here. **Check what can be measured first, then listen.**

| Symptom | Most likely cause | Section | Measurable? |
|---|---|---|---|
| Flat, lacking drive, unbearable to listen to | Monotonic energy curve | §2.2 | ✅ per-section RMS |
| Gets louder toward the end but never reaches a climax | Only adding, never subtracting | §3 | ✅ per-section RMS |
| Every section sounds the same | Lineup unchanged from start to finish | §5 | ✅ per-track onset density |
| The second verse is dull | Second pass copied unchanged | §6 | ✅ section similarity |
| Forgotten immediately after listening | No arrangement hook | §7 | ⚠ semi-automatic |
| Ending is abrupt or drags | No ending method chosen | §8 | ✅ energy slope of final section |
| "Cannot say what's wrong, it just sounds like AI" | Usually several of the above at once | §9 full table | — |

> Check the measurable items against the specification one by one first;
> **do not rely on repeated listening to find problems**—save your ears for the final step.

---

## 10. Mapping to ARR-SPEC Fields

This skill is responsible for filling these ARR-SPEC fields:

| Field | Section of this skill | Lint |
|---|---|---|
| `arrangement.energy_curve` | §2 | #5 must include a drop |
| `arrangement.subtraction_events` | §3 | #6 at least one |
| `arrangement.roster[].entry/exit` | §5 | #7 must have both entries and exits |
| `arrangement.hooks.arrangement_hook` | §7 | #8 required |
| Asymmetric design of `form[].bars` | §4.2 | #3 must not be all multiples of 8 |
| `form[].events` | §5.2 | — |
| Ending treatment written into the `note` of the final section of `form` | §8 | #14 duration consistency |

Fields this skill does not fill: `spectrum_budget` (→ `mc-texture-layering`),
`groove` (→ `mc-rhythm-section`), `vocal` (→ `mc-vocal-direction`),
`mix_intent` (→ `mc-mix-intent`).

---

## 11. Must-Pass Checklist After Writing

Before running the 20 items in `mc-workflow` §3.0, first pass through this yourself:

- [ ] The energy sequence is written out, **and it is not non-decreasing**
- [ ] The subtraction event can state **which bar, what is removed, and why there**
- [ ] Read the roster sorted by entry, and the layering of the lineup can be read out
- [ ] **At least one instrument's exit is not the end**
- [ ] The arrangement_hook can be hummed without the score, and its recurrence positions are unevenly distributed
- [ ] A2 and A1 differ in at least one listed respect
- [ ] Section lengths are mainly multiples of 8, but the pattern is **broken at least once**, and you can say why
- [ ] You can say which of the three ending types was chosen
- [ ] Wherever a rule is "not followed," the **failure condition** is stated (which exception path is being taken)

**The last item matters most**: every rule in this skill carries a failure condition.
**Not following a rule is permitted; being unable to give a reason for it is not.**

---

## Appendix: Evidence Tier Notes

The rules in this skill fall into three tiers, each annotated in the text:

| Tier | Meaning | In this skill |
|---|---|---|
| **Strong rule** | Measured across 62 real arrangements, hit rate lower bound ≥80% | The energy must drop; an instrument must enter partway through; at least one must leave early; the opening should not be fully loaded |
| **Tendency** | Hit rate 50–80% | At least one clear subtraction (70%) |
| **Technique** | Taught in textbooks, but measurements do not support it as a rule | The dip before the climax (§2.3) |

Measurement corpus: 60 songs from Cambridge-MT multitrack (2,906 independent instrument tracks) plus 2 finished Chinese-language pop songs, 62 songs in total, each reverse-engineered into ARR-SPEC and then counted for hits.

**What distinguishes this "hit rate" from ordinary arrangement tutorials**:
rules are not "a certain teacher says so," but "how many of the 62 real arrangements do this."
Where the hit rate is low, this skill does not write the claim as a rule.

Main source: Dennis DeSantis, *Making Music: 74 Creative Strategies for Electronic Music Producers* (Ableton),
page numbers refer to that book. For the rest, see [reference.md](reference.md).
