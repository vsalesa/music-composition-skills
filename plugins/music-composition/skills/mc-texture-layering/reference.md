# mc-texture-layering Reference: Frequency Bands, Separation Targets, and Masking

> `SKILL.md` covers how to allocate space; this file holds **the ruler you use when allocating**:
> how to divide the bands, how far separation must go to be enough, and how masking happens.
>
> Main source: **Roey Izhaki, *Mixing Audio***;
> auditory basis: **Howard & Angus, *Acoustics and Psychoacoustics***.

---

## 1. Four-band division

> Handling frequency accounts for **roughly half of the mixing work** (p0092).
> The human audible range is 20 Hz–20 kHz.

The **4-band division** commonly used in mixing has its dividing points roughly at **250 Hz, 2 kHz, and 6 kHz** (p0092):

| Band | Range |
|---|---|
| **Low band** | 20 Hz – 250 Hz |
| **Low-mid band** | 250 Hz – 2 kHz |
| **High-mid band** | 2 kHz – 6 kHz |
| **High band** | 6 kHz – 20 kHz |

> Being able to tell the low-mid and high-mid bands apart **takes a certain amount of practice** (p0093).

**How this library uses it**: the `roster[].band` field in ARR-SPEC **takes one of these four bands**,
and only when more detail is genuinely needed should a specific Hz value be written. Four bands are enough, and they are a language everyone can align on.

(Figure 6.1, the basic 4-band spectral division method, p0093)

### 1.1 Where the fundamentals of each part sit (Takeuchi p0242)

| Part | Fundamental range |
|---|---|
| Female voice | 165–587 Hz |
| Male voice | 110–392 Hz |
| Guitar (accompaniment) | 82–494 Hz |
| Piano / synth (accompaniment) | 220–523 Hz |
| Kick drum | 41–220 Hz |
| Bass | 41–123 Hz |

★ **The fundamental is not the same as the band where the sound is perceived.** In the table, voice, guitar, and piano fundamentals all cluster in the 250 Hz–2 kHz band, but their recognisability and their "harshness" lie in the harmonic-overtone region,
and 4 kHz is the position where the ear is most sensitive and most easily stung (p0242). A band budget drawn neatly by fundamentals can still clash, usually because the overtone regions collide.
When budgeting, write down both: which band the fundamental falls in, and which band the main overtones fall in.

### 1.2 Critical bands: the smallest graduation on this ruler

The four bands are a coarse scale for communication; the ear's real unit of resolution is the **critical band** (Howard & Angus p0083).
When two tones fall within the same critical band, they mask each other and produce a sense of roughness. Bandwidth is estimated with ERB:
ERB = 24.7 × (4.37 × f_c + 1) Hz, with f_c in kHz, valid for 100 Hz–10 kHz (p0083).

| Centre frequency | Critical bandwidth |
|---|---|
| 200 Hz | about 46 Hz (p0084) |
| 790 Hz | about 110 Hz (p0130) |
| 2 kHz | about 241 Hz (p0084) |

This is roughly equivalent to a 1/3-octave band (p0086). **In the low register, one critical band spans a wider interval**, so two instruments in the low register need to be spaced further apart than in the high register
(the "bass and tenor at least a fourth apart" rule in four-part writing is the practical version of this, p0146).
Two pure tones whose frequencies differ by between 5% and 50% of a critical bandwidth sound dissonant; the difference is roughest at 1/4 of a bandwidth, and only beyond one full bandwidth does it sound consonant (p0141–0142).
The further down into the low register an interval goes, the more harmonic pairs fall into the "highly dissonant" category (p0146).

**Use both rulers together**: fill `roster[].band` with the four bands; use critical bands to judge whether two parts are actually fighting.
Two instruments several critical bands apart within the same band may not clash; two instruments in adjacent bands but close to the dividing point (for example, either side of 2 kHz) will clash just the same.

---

## 2. Four typical imbalances

> Frequency balance (also called **timbral balance**) is the main challenge in mixing.
> **The most common problem is handling it too extremely.** (p0093–0094)

| Imbalance | Perceived result |
|---|---|
| Too much low frequency | **Muddy** |
| Too little low frequency | **Thin** |
| Too little high frequency | **Dull** |
| Too much high frequency | **Harsh** |

**Two practical observations** (p0094):
- **A common beginner mistake: making every instrument bright**, which ends up with too much high frequency in the final signal
- **The low frequencies are the hardest band to keep stable**, because playback systems (bookshelf speakers and the like) have deficiencies in low-frequency reproduction
- **The low-mid band is where most instruments' fundamentals sit**; mixing in other, unimportant frequency content here makes the mix chaotic

> ★ The third observation explains why 250 Hz–2 kHz is the most crowded band and the one most in need of budget management:
> in the conflict list in `SKILL.md` §4, most conflicts land here.

Judgements of too much or too little low frequency must be made at a fixed monitoring level: when the level drops, low and high frequencies are suppressed relative to the midrange, and the sound thins and darkens
(equal-loudness contours, Howard & Angus p0091). Another cause of "making everything bright" is auditory fatigue:
after adaptation, people keep boosting the same band (p0342).

**Reference tracks** (accompanying Izhaki, the song *Hero*):
6.11 well balanced / 6.12 too much low frequency / 6.13 too little low frequency / 6.14 too much high frequency / 6.15 too little high frequency (p0094–0095)

---

## 3. ★ Separation: the key issue in the frequency domain

> **The key issue in the frequency domain is achieving frequency "separation" between instruments** (p0095).

**An ideal ordering (from low to high)** (p0095):

> Bass → kick drum → piano → snare → vocal → guitar → cymbals

> But: **the specific ordering of instruments does not matter; what matters is separating them from one another in frequency** (p0095).

**Two things to check** (p0095):
1. Whether there are **gaps** between the frequency ranges of the instruments
2. Whether they are **strictly separated**

Figure 6.2's three diagrams make the standard very clear (p0096):

| Diagram | State |
|---|---|
| **a** | Frequency **imbalance**: the instruments' frequency ranges **overlap** one another (no separation), and there are **holes** at some frequencies |
| **b** | Frequency **balance**: each instrument has a defined frequency range, **with no overlap**, forming a **complete, continuous** frequency response |
| **c** | The **actual** frequency range distribution of each instrument |

> ★ Note that diagram b satisfies two conditions at once: **no overlap** and **continuity**.
> Avoiding overlap alone leaves holes (it sounds as if "a piece is missing"); achieving continuity alone creates overlap (it sounds muddy).
> That is the precise meaning of the word "budget": **cover the whole spectrum, but give each slice only one owner.**

**This diagram is the acceptance criterion for the mandatory table in §1 of `SKILL.md`**:
when you plot your band-assignment table, it should look like diagram b, not diagram a.

---

## 4. Masking

### 4.1 Basic principles (p0038)

> - A loud sound masks a quiet sound
> - One instrument's frequency range can mask another instrument's frequency range

The quantified version from Howard & Angus p0238–0240: the degree of masking depends on the frequency and amplitude of both sounds (p0239).
**Masking spreads upward: low frequencies readily mask high frequencies**, because the response curve of the auditory filter is asymmetric (p0239).
The masking threshold within the critical band of the masker sits about 20 dB below the masker; each critical band further up drops by a further 5–13 dB, while the slope downward is much steeper (p0239–0240).
→ In the band budget, "who is below" matters more than "who is louder": elements in the low register are the masking sources for the whole piece.

### 4.2 ★ Implications along the time dimension (more useful)

> - **Percussion instruments (such as the kick drum) sound for a short time, so their masking effect is small**
> - **Continuously sounding instruments (such as a sawtooth pad) fill the spectrum and stereo space, so their masking effect is large**
> - **Raising the level of a dense pad part creates more masking than raising the level of the kick drum;
>   a pad masking the kick drum is a major problem that happens continuously** (p0038)

Howard & Angus also give figures for the time dimension: after the masker stops, masking persists for 100–200 ms before it disappears; when the masker lasts under 50 ms, masking grows with its duration;
post-masking lasts about 10 ms and is nearly negligible (p0241). Loudness itself is also discounted for sounds shorter than 200 ms according to their duration (p0095).
That is why "short percussive hits mask little, and sustained sounds mask a lot."

**Usage**: when diagnosing "muddiness", **check the sustained sounds first**. See `mc-mix-intent` §5:
that section covers the same phenomenon's consequences at the mix-intent level, whereas this one covers its causes at the texture-design level.

### 4.3 Stereo placement and masking

Izhaki has a dedicated section on "stereo placement and masking" (p0250).
**Separating two instruments that compete for the same frequencies by stereo placement is a fourth resolution**,
but it does not appear among the three resolutions in `SKILL.md` §4.2, because **it is "remixing", not "rewriting"**, and so belongs to `mc-mix-intent`.

> Remember this boundary: this skill provides only the **rewriting-type** resolutions (yield / separate registers / alternate).
> Intent for panning, sidechaining, and dynamics processing all belong to mix-intent; the parameters are a matter for mixing.

Howard & Angus set the boundary for this fourth resolution: a panpot provides only a level difference (p0112), and level difference mainly works for high-frequency localisation;
time difference governs low frequencies, and 700 Hz–2.8 kHz is the weakest transition zone for localisation (p0108). So separating by panning works for high-frequency conflicts such as cymbals against guitar,
but offers limited help for the most crowded low-mid conflicts in the 250 Hz–2 kHz range, where you still have to rewrite.

### 4.4 Auditory grouping: the other lever for fusion and separation

Elements that are close in frequency and move in similar directions are grouped together by the ear (p0244). When timbres differ greatly and the tempo is fast (over roughly 10 notes per second), the ear groups by timbre instead,
and a single line is heard as two (p0245). Reverb also fuses different instruments together (p0261).
→ To make two instruments **fuse**: put them in similar registers, have them enter together, and share reverb. To make them **separate**: widen the register gap, increase the timbral contrast, and stagger their entries.
The lead needs a register of its own, or it will be grouped into the neighbouring group.

---

## 5. Chapter index for depth and stereo

These belong to `mc-mix-intent`, and are listed here only for convenient lookup:

| Topic | Page |
|---|---|
| 6.4 Stereo field | — |
| 6.4.1 Standards for stereo image | — |
| 6.4.2 Stereo balance | — |
| 6.4.3 Other issues in the stereo image and processing goals | — |
| **6.5 Depth** | — |
| 7.3.4 Early reflections | — |
| Phase meter and stereo monitoring | p0136 |
| Out of Phase Stereo technique | — |
| Chapter 13 Panning (full chapter) | p0240– |
| 13.2.3 **Pan laws** | — |
| **13.4.1 Panning and masking** | p0250 |
| 13.4.3 Panning of effect signals | p0253 |

---

## 5a. A single instrument's own auditory rules (Howard & Angus)

Section 2 covers how two instruments interfere with each other (masking, localisation, grouping, consonance); those belong to `mc-mix-intent`.
This section covers **how an instrument's timbre is established when it exists on its own**, which determines who can share a layer and who must be offset during layering.

### 5a.1 The onset is the timbre's identity card

**With the attack and decay removed, a violin and a trumpet are hard to tell apart** (p0222–0223).
The steady-state spectrum does not determine recognisability; recognisability lies almost entirely in the first few tens of milliseconds.

The six acoustic cues the book names (p0223): the friction of bow on string, the consonant-like onset of brass, the breath noise of the player blowing, the slapping sound of a reed starting to vibrate, the muffled strike of a piano hammer, and the falling sound of a string decaying.

**Three takeaways for arrangement**:

1. **If you want recognisability, leave room for the onset.** Packing two instruments with similar onset characteristics into one layer amounts to voluntarily giving up both of their identities.
2. **What synthesized timbres often lack is not the spectrum but the onset.** A sample that sounds "fake" is often because its loop was taken from the steady state, so the attack was cut off or homogenised (p0217).
3. **The onset is not coloured by the room.** The first reflection usually arrives after the onset has ended (p0217), so the onset carries uncoloured information. No amount of reverb can rescue an onset that has been flattened.

### 5a.2 Onset timing across families determines who can play fast phrases

| Instrument | Onset characteristics | Arrangement implication |
|---|---|---|
| Brass (trumpet, French horn, trombone, tuba) | All four are **fundamental-first**, with a very short attack that quickly settles into periodic vibration (p0221) | Best suited to hard-edged, rhythmic entries |
| Clarinet, soprano sax | Fundamental-first (p0220) | Same as above, but much weaker in energy |
| Oboe | **Second harmonic first**; third and fourth harmonics come in after about 5 ms, and the fundamental only after about 8 ms (p0220) | The note head carries a non-fundamental "core", which competes with other middle-register layers when stacked on them |
| Flute | About **70 ms of breath noise** (above 2 kHz) before the fundamental; higher harmonics only gradually enter about 80 ms after the fundamental (p0221) | ★ **The long onset stage makes it unsuitable for fast staccato writing**. If you write it anyway, it will blur into a mass of breathy sound |
| Violin | Attack about 160 ms, decay about 250 ms; **vibrato does not appear until about 250 ms after the note begins** (p0221) | Notes shorter than 250 ms get no vibrato, so their timbre is entirely different from that of long notes |

### 5a.3 Harmonics 5–7 mark the boundary between "bright" and "dull"

Regardless of the fundamental, **harmonics from the 5th to 7th and above are generally not distinguishable, while lower ones are** (p0223).
Sounds with significant harmonics above the 5th–7th in their steady state (the reed stops of a pipe organ, soprano sax, trumpet, violin, professional singing voice)
are described as bright, brilliant, and harsh; those without them (clarinet, oboe, flute, trombone, French horn, tuba)
are described as dull, soft, and monotonous (p0223–0224).

**The seventh harmonic is the lowest harmonic the ear cannot distinguish, and without it a sound is noticeably softer** (p0224).

**Arrangement implication**: the "should this layer be bright or dark" decision in the band budget table can be translated directly into "does this instrument have significant harmonics above the 5th–7th",
rather than waiting until mixing to fix it with EQ. If you want a layer to be bright without adding high frequencies, changing instruments is cleaner than adding EQ.

### 5a.4 Percussion timbre comes from non-harmonic relationships

The distinctive timbre of mallet, membrane, and plate percussion instruments comes from **non-harmonic relationships** between their vibration mode frequencies,
which produce a clanging, ringing quality (p0224). A strike is an impulsive source with an aperiodic, continuous spectrum that excites all the vibration modes the instrument can support at once (p0194–0195).
This is the opposite of string and wind instruments, which settle onto a series of whole-number multiples of the fundamental through periodic vibration.

**The book gives figures for how far "non-harmonic" goes**: for a freely suspended bar such as the xylophone, the second vibration mode is 2.758 times the first mode,
which in interval terms is 17.56 semitones, neither a pure octave nor a pure fifth (p0195–0196, Table 4.1).
A bar fixed at one end (such as the metallophone) differs even more: its second mode is 6.267 times the first, or 31.77 semitones (p0195).
Membranes are more extreme: for an ideal circular membrane, the first few mode frequency ratios are 1, 1.59, 2.14, 2.30…, which in semitones are 0, 8.1, 13.1, 14.4,
none of which falls where a harmonic would be (p0198, Table 4.2). This is what "non-harmonic relationship" looks like in numbers:
not vaguely "unclear pitch", but a ratio between vibration modes that is not a whole-number ratio at all.

**The exceptions also explain why the rule holds**: pitched percussion instruments such as timpani, xylophone, and marimba
are tuned to pull certain modes back to near harmonic positions. Timpani use the air cavity behind the membrane to shift the mode frequencies so they approach a single harmonic series (p0200);
xylophone and marimba bars are shaped by carving the underside of the bar into an arc, which changes the mode ratios.
Marimba and vibraphone usually tune the second mode to two octaves above the first, and xylophone to roughly a twelfth above (p0197).
Tuning works by adjusting exactly these non-harmonic relationships; instruments that cannot be tuned this way (snare drum, cymbals, bass drum) can only be unpitched percussion.

**Arrangement implication**: by default, percussion does not take part in the band budget for the harmonic layer, since its "pitch" is not part of the harmonic system.
Placing cymbals on the same budget line as high strings miscalculates the budget, unless the percussion instrument itself is tuned (timpani, xylophone,
marimba, vibraphone). Only then does its fundamental genuinely participate in the harmony, and only then should the band it occupies be calculated by pitch.

### 5a.5 Items that belong to `mc-mix-intent`, listed here for lookup only

| Topic | Page |
|---|---|
| 2.2 Critical bands and ERB | p0082–0086 |
| 2.4 Loudness: equal-loudness contours, +10 dB, 200 ms, across critical bands | p0090–0097 |
| 2.6 Localisation: time difference / level difference / precedence effect | p0102–0110 |
| 3.3.2 Consonance and critical bandwidth; intervals in the low register | p0141–0146 |
| 5.5.2 Masking: simultaneous and non-simultaneous | p0238–0241 |
| 5.5.3 Auditory grouping | p0244–0245 |
| 7.2.3 Equalisation and masking (example: vocal at 1.5 kHz) | p0342–0343 |

## 6. Depth and density (DeSantis)

### 6.1 The three-layer depth map: layer while writing, do not leave it to the mix

This addresses the problem of sounding "flat, two-dimensional, with no sense of depth" (p0111).
The remedy is to plan with the three layers borrowed from the visual arts: **foreground** is nearest, with clear focus and rich detail; **background** is farthest, recognisable but blurred, with little detail;
**middle ground** sits between them, not the focus but more prominent than the background (p0112).

★ **The key point is that this is a decision made at the composition stage, not a remedy applied at the mixing stage.**
What mixing can do is make things louder, brighter, and drier (to bring closer), or quieter, darker, and more reverberant (to push back) (p0112–0113);
those belong to `mc-mix-intent`. This skill is concerned with the other half: **which writing choices by themselves make a layer move forward**.

**What the ear hears as foreground** (p0113): **high, loud, fast, and rapidly changing**.

Of these four, **rate of change is the easiest to overlook and the most useful**:

- Drums are usually loud, but because they stay constant, they are generally heard as middle ground or background
- A drum fill makes density and complexity change suddenly, so **the drums temporarily jump to the foreground**, then recede again
- ★ **The reverse is a trap**: if a synth line sits an octave above the vocal, or has more complex rhythm and more violent leaps,
  listeners will subconsciously hear the synth as the lead. **The lead you think you wrote and the lead the listener actually hears are not the same thing**;
  this is exactly why the "lead sequence" in the spec must be written out section by section

**Two actionable points** (p0113–0114):

1. When writing each part, ask which layer of the three-layer map it belongs in
2. **Keep the rate of change in the middle ground and background to a minimum, so that the foreground has freedom to move**. If every layer is changing, there are no layers at all

> A corroborating point worth noting: Adler, discussing string orchestration, uses this same three-part division of foreground, middle ground, and background
> (see `mc-orchestration` reference §2.3.1). One comes from the orchestral tradition, the other from electronic music production, and both converge on the same model. It is not the position of any one school.

### 6.2 The maximal-density method: do not write from left to right

This addresses the problem where, after the first section is written, writing a second section feels like starting a new project from scratch (p0265).

Method (p0265–0266):

1. **First make a maximum-density section**: stack up every element that could possibly sound together, actually all at the same time. At first this is usually a jumbled mess
2. **Subtract elements one at a time** until the section is both dense and musically coherent. **This section becomes the song's climax**
3. Copy this peak section, and make several lower-density versions by muting or deleting tracks
4. Pick the combinations you like, each becoming a new section
5. **The arrangement then becomes the process of arranging sections of different densities into a rise and fall**, rather than growing forward from the beginning

**Difference from subtractive arrangement**: subtractive arrangement works at the arrangement stage, while the maximal-density method works at the **composition stage**.
It does not require filling the entire length of the song with material; instead it first stacks a dense section vertically, then subtracts from it (p0266).

**Boundaries of applicability** (p0266):

- For genres where sections are not meant to contrast strongly with each other (such as minimal techno), this approach can be used literally
- For genres that need contrast, **build a separate maximum-density version of each section**, each serving as the master for several variants of that section

The subtractive side (the power of erasing and the cost of over-layering, p0286–0288) is covered in §4.3 and §4.4 of this document.

---

## 7. Focus and priority (Illustrated Pop Band Arrangement)

The preceding sections covered how to divide frequency and depth; this section covers **who is the focus in each bar** and how to adjust that focus.

The book treats arrangement as arithmetic (p0019–0020): addition and subtraction are the additive and subtractive layers (this document §4),
**multiplication is synergy and division is priority**. The rest of this document does not cover multiplication or division.

### 7.0 ★ Adjusting focus: five knobs and four levels of hierarchy

§7.2 covers deciding first whom to emphasise; this section covers **which knobs you have for turning the focus of a phrase up or down** (illustrated arrangement, p0082–0106).

**Five knobs** (p0084–0094), with the further right, the more attention they attract:

| Knob | Low → High |
|---|---|
| **Rhythm** | The greater the **deviation** from the basic groove, the higher the focus |
| **Direction of motion** | Straight-line motion < up-and-down motion; stepwise < leaps; descending < ascending |
| **Sound usage** | Chord tones < approach tones < **extension tones** |
| **Register** | The higher, the higher the focus, **but too high and it drops away again** |
| **Phrase length** | The longer, the higher the focus |

★ **The first three are the "three pillars"**. Direction of motion also applies to the drum kit: the pitch order is cymbal > snare > high tom > low tom > floor tom > kick drum,
**the drum kit almost never has straight ascending phrases**, and tom fills are basically descending by default (p0088–0089).

**Four levels of hierarchy** (p0082, p0095–0096):

1. Main melody: first focus
2. **Gap phrases**, which should be "slightly weaker than the main melody"
3. **Background phrases**, which sit between the gap phrases and the lively beat
4. The lively beat

**The fix** (p0082): if a phrase is stealing the show, **do not remove the whole phrase**; keep its essence, turn down the knobs, and drop it to the second or third level of focus.

Three supporting points: gap phrases should use instruments with a register close to the main melody, mainly guitar or piano, with bass only as support (p0099);
★ when a gap phrase overlaps the sustained notes of the main melody, **the overlapping notes must not be dissonant, and should avoid thirds where possible**; the only place in the piece where a third would be heard as a half-baked third harmony, so the teaching examples use stacked fifths instead (p0100–0101);
and the recommended dynamic order for background parts is **bass > guitar > piano** (p0106).

### 7.1 Synergy: the whole is greater than the sum of its parts

**Synergy** refers to the effect produced when one element merges with others, exceeding the effect of any single element (p0134).
When several instruments play together, **their focus is noticeably higher than that of any one of them alone** (p0135).

Three methods (p0135): **unison**, **doubling**, and **same rhythm**.

★ **The boundaries of applicability are stated very firmly, and are worth quoting directly** (p0135):

- **Use only on gap phrases**, and only on the phrase you most want to be ornate in the whole piece; **a fill-style phrase is most suitable**
- **Using it on background phrases backfires**; they become too conspicuous

This rule explains a common flaw: spreading "amplifying" techniques such as unison or doubling across the lowest-ranking parts
results in the background moving forward while the lead becomes muddy.

### 7.2 Priority: decide whom to emphasise first, then rank focus

**Priority** addresses the situation where every track sounds perfect on its own but the whole becomes chaotic when stacked (p0134).
The remedy is to **deliberately decide which section to emphasise, then rank the focus accordingly** (p0153).

**Focus** refers to how concentrated the listener's attention is on a given instrument.

★ **The ranking must change bar by bar**, otherwise it becomes monotonous (p0153).
The book's sketch of the first four bars of a chorus runs like this: the vocal is always the highest, but the relative positions of piano, two guitars, bass, and drums
change every bar, **and none of them is fixed at the same level from start to finish**.

### 7.3 ★ Adjusting focus can only be done by subtraction, not by addition

This is the single most important point in the whole framework (p0154):

> **Rather than raising the focus of the high-priority section, lower the focus of the low-priority sections.**

Once the secondary parts are pulled down, the focus of the high-priority part **rises relatively**.
Conversely, forcibly lifting a secondary part will make it **overtake the main melody**, and the hierarchy falls into disorder (p0154).

This is the same logic as the subtractive strategy in §4 of this document, applied at a different level:
**§4 subtracts density; §7.3 subtracts attention.**
It also gives the "lead sequence" in ARR-SPEC an executable form:
**write out the focus ranking section by section (ideally bar by bar), and state clearly whose focus was lowered to achieve each level.**

### 7.4 Concrete means of making way for accompaniment (p0166–0171)

| Means | What it does |
|---|---|
| **Extend the piano notes** | Stretch the piano into long notes to free up dynamic space for the guitar |
| **Fill the gaps** | The accompaniment sounds only in the gaps left by the lead |
| **Rhythmic suppression** | Reduce the rhythmic activity of the accompaniment; focus can drop without reducing volume |
| **Lead switching** | Two instruments take turns as the lead, with the handover balanced by dynamics |
| **Octave doubling** | Lead guitar doubled at the octave with another instrument, raising the whole by one level |
| **Bass dynamic tracking** | The bass follows the dynamics of the lead rather than setting its own course |

★ **Note that none of these six is a volume operation; they are all writing operations.** Volume belongs to `mc-mix-intent`,
and **making way that can be solved in the writing should not be left to the mix to solve**.

---

## 8. Parts outside this skill

| Content | Where it goes |
|---|---|
| The function and types of equalisers (from Chapter 14 onward, p0258–) | A matter for mixing; not part of this package |
| The **practical application** of panning, depth, and reverb | A matter for mixing; the **intent** belongs to `mc-mix-intent` |
| Which instrument occupies this band | `mc-orchestration` / `mc-sound-design` |
| When to enter and exit | `mc-arrangement-arch` |
