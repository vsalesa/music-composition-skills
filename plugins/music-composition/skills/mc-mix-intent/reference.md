# mc-mix-intent Reference: Handoff Format, Process Order and Goal Detail

> `SKILL.md` covers how to write intent; this file covers **who it is written for, in what order, and to what level of detail**.
>
> Main source: **Roey Izhaki, *Mixing Audio***.
> Auditory basis: **Howard & Angus, *Acoustics and Psychoacoustics***.

---

## 1. Why write intent: mixing is a competition for space

> The instruments in a mix all **compete with each other for their place in the space**. For example, guitar and vocals mask each other (p0089).

The definition and mechanisms of masking are in Howard & Angus p0238–0239. The book gives exactly the example of vocals and accompaniment:
the accompaniment backs off a little around 1.5 kHz, the vocal adds a little at the same spot, and the singing then emerges from the accompaniment (p0342).
This is the prototype of a "remix" yielding. Doing it the other way round makes the vocal even less audible.

A mix engineer has to make trade-offs. **If intent is not written down, the engineer makes the trade-offs for you**:
they follow their own habits rather than what this song needs.
This is why this skill exists: **the `mix_intent` in ARR-SPEC states these trade-offs up front on your behalf.**

---

## 2. ★ A counterintuitive ordering problem: which section to start with

Izhaki gives two approaches and points out the trap in the first one (p0065):

| Approach | Problem |
|---|---|
| **Order by time** (work through sections from the start) | Looks logical, but **if the verse is made extremely good, little room is left to showcase the instruments that newly appear in the chorus** |
| **Order by importance** | Process the most important section first. Recorded music is usually the **chorus**; electronic music may be the **climax** |

> ★ This is **the same principle appearing twice** as the maximum-density method in `mc-texture-layering` §6:
> **do the fullest places first, then work backwards.** If you start from the sparse places, you will spend your budget without noticing.

**Applied to `mix_intent`**: `focus_by_section[]` **should write the densest section first**,
and define the other sections relative to it, rather than listing them one by one in time order.

---

## 3. Four approaches to mixing order (by track) (p0064)

Useful when writing the handoff sheet: **telling the mix engineer which order you want them to follow affects how the final space is allocated**.

| Approach | Advantage | Disadvantage |
|---|---|---|
| **From fewest to most** | Lets attention focus on each instrument alone | As tracks are added, **the mix space fills up**, leaving insufficient space for the remaining parts |
| **Rhythm → harmony → melody** | Follows the production order of multitrack recording done in stages | — |
| **By importance** | Important tracks are handled from the start, **leaving enough space for them to be large enough** | — |
| **Parallel progression** | No track is treated in isolation during mixing | **Only suitable for works with relatively simple orchestration** |

(Rhythm tracks = drums, percussion, bass; harmony tracks = rhythm guitar, pads, keyboards; melody tracks = vocals and solos)

**This library's default recommendation**: **by importance**, for the reason given in §2.

### 3.1 Mixing order within the drum kit (p0064–0065)

| Piece | Description |
|---|---|
| **Overheads** | Usually recorded with a stereo pair of microphones, and serve as the **reference for processing the other drum pieces**; processing them first brings more benefit |
| **Kick** | In most works the **most dominant** rhythmic element; often enters the mix before the other drum pieces, **sometimes even before the overheads** |
| **Snare** | The **second most important** dominant rhythmic element, often following the kick closely |
| **Toms** | **Sound only at certain moments**, and contribute **the least** to the sonic effect of the whole kit |
| **Cymbals (Hi-hat / Ride / Crash)** | There is **considerable bleed** in the overhead track; during mixing they are often used to **reinforce the effect of the overhead track** |

> The last point explains why the drum kit cannot be imagined as "each piece independent".
> The overheads already contain all the cymbals, so a separate cymbal track is a **reinforcement**, not a **source**.
> This disappears when using sample libraries or generative backends (there is no bleed),
> **so machine-made drum kits naturally lack this layer of glue**, and `mix_intent` needs to request it explicitly.

---

## 4. Standard audio processing order (p0066, Figure 4.4)

**This is not something this library prescribes** (it belongs to mixing). But if the intent sheet specifies effects, the order will be constrained by them,
so it is listed here for reference:

1. If you **skip stereo processing** and fold the material to mono, **you lose the width and depth of the sound**
2. **The sound of an insert processor replaces the original signal**, so it should come **before** any **send effects**
   (modulation, delay, reverb)
3. For the same reason, usually **modulation first, then delay**, rather than delay first and modulation after
4. **Reverb imitates natural spatial impression**, so usually the signal after reverb should **no longer pass through other effects**
5. **Automation control is usually the last important stage in mixing**

**Dry–wet processing method** (p0066): first combine all tracks through **dry processing tools** (faders, pan pots, processors), and only then send them to **wet processing tools** (modulation, delay, reverb).

**Final step before release**: usually **further refinement of the stereo layout and level balance** (p0066).

---

## 5. Repeated processing: from rough to fine (p0067–0068)

> **"Start rough, and end fine. Only when it is genuinely needed, after the mixing process is over, does the sound need to be made perfect."** (p0068)

**Why it has to be this way**: mixing is a process with very tight interdependencies (p0067):

> A partial mix that already exists generally **needs adjusting and polishing** whenever new material is added;
> any adjustment to the sound **may require follow-up adjustments elsewhere**.

An example of a chain reaction (p0067):

1. Raise the high frequencies of the vocal to make it brighter
2. → The high frequencies may produce **a reverb tail that is too long** → the reverb's damping decay must be adjusted
3. → EQ also makes the vocal **sound louder** (energy spreads into more critical bands; total sound intensity is unchanged but perceived loudness rises, Howard & Angus p0096) → the fader must be adjusted
4. → If the vocal was EQ'd before compression → **the compression parameters may need adjusting**

> ★ Significance for this library: this chain shows **why `mix_intent` can only state intent and not parameters**.
> Parameters pull on each other. Fixing a value in the spec sheet
> locks the engineer out of the following four steps, and you cannot know what their chain looks like.

---

## 6. Two common predicaments and their solutions (p0068–0069)

### 6.1 Obstacles while listening and evaluating

**Symptom**: something is clearly wrong, **but you cannot tell where the problem is**.

**Solution**: **reference tracks are the tool that can really resolve the difficulty**.
Compare the current mix with a finished mix you like. This comparison can show where the problem is,
**or at least help you settle on a direction to move forward**.

(The six uses of reference tracks are in `SKILL.md` §6.)

### 6.2 Getting stuck in a loop

**Mechanism**: we **can only remember the last few operations**.
You cannot recall the details of a compression step from two days ago, but you remember clearly how you EQ'd half an hour ago.
— So you go back and forth between the most recent few decisions.

**Solution**:
1. Take a **short break**
2. **Listen to the entire mix again**, decide what genuinely needs doing, and only then decide what to do next
3. > "Be sure to **re-evaluate your recent mixing decisions**."

Howard & Angus call the same thing "auditory fatigue": the ear adapts to a change in timbre, so after a while a boost sounds weaker, and one keeps boosting the bands one has already adapted to. The only remedy is again to take a break and listen afresh (p0342).
This is not the same as the temporary threshold shift caused by excessive volume; it also happens at normal volume.

> ★ This applies to agents as well, and more severely:
> an agent's "recent memory" is its context window.
> So this library's approach is: **judgments go into the ARR-SPEC, not left in the conversation**.
> The spec sheet is the written form of the act of "listening to the whole mix again".

---

## 7. Izhaki chapter navigation

| Topic | Location |
|---|---|
| 1.2 The perfect mix and ear training | — |
| 2.1 **The louder it is, the better it sounds** (auditory basis: equal-loudness contours, Howard & Angus p0091; +10 dB ≈ loudness doubles, p0094) | — |
| 3.1.5 Interpersonal skills / 3.1.6 Ability to work quickly | — |
| 3.2 Methods of learning to mix / 3.3 Analysis of mixes | — |
| **3.4 Using reference tracks** | p0050–0052 |
| 4.1 Mixing and music production workflow / 4.1.5 Editing | — |
| 4.2 Mixing is a composite of many elements | — |
| **4.3 Mixing order and workflow** | p0064–0068 |
| 4.4 Some difficult problems | p0068–0069 |
| **4.5 Milestones in the mixing workflow** | — |
| 4.6 Fixing and locking in the mix effect | — |
| 5.1 How long mixing takes | p0073 |
| 5.2 Breaks / 5.3 Using solo listening / **5.4 Mono monitoring** | p0074–0075 |
| 5.5 Bouncing | p0077 |
| 5.6 Mix project management / 5.7 Final edit / **5.8 Mastering** | — |
| **6 Domains and goals of mixing** | p0089 |
| **6.1 Goals of mixing** (mood / balance / definition / interest) | p0089–0090 |
| 6.2 The frequency domain (four-band division, separation) | p0092–0096 |
| 6.4 Stereo domain / 6.5 Depth | — |
| Chapter 13, the full chapter on panning (including **13.4.1 Panning and masking** p0250) | p0240– |
| Chapter 14, the full chapter on equalizers | p0258– |

---

## 8. Parts not covered by this skill

| Content | Where it goes |
|---|---|
| Parameters and operation of equalizers, compressors and reverb from chapter 14 onward | Mixing; not part of this package |
| Mastering (5.8) | Mastering; not part of this package |
| The structural solutions of the four-band division and separation of instrument frequencies | `mc-texture-layering` (the reference there contains the full four-band table) |
| Concrete parameters of the vocal mixing chain | The `mc-vocal-direction` reference keeps example values; practical implementation is mixing |
| The order of **arranging** (not mixing) the individual drum pieces | `mc-rhythm-section` reference |
