# mc-arrangement-arch Reference: Section Terminology, Common Forms, and Measured Data

> `SKILL.md` covers structural decisions; this file holds **term definitions, a catalogue of forms, and the full table of this library's measured data**.
>
> Source: **Dennis DeSantis, *Making Music***,
> plus this library's own rule-corroboration statistics run on the Cambridge-MT multitrack set (§3).

---

## 1. Precise Definitions of Section Terms

From DeSantis, "Common Forms 1: Elements of Song Form."
**When writing `form[].name` in ARR-SPEC, use terms according to these definitions**; do not coin your own.

### Verse ("A" section)

- Usually **recurs** as a section
- Typically **16 or 32 bars** long
- Forms the **body** of the song
- When there are lyrics, it usually **tells the "story"**

> DeSantis gives an attribute-catalogue case that can serve as a criterion: in that song the verse vocals are breathy and intimate (close-miked, sung softly), switch to full-voice singing in the chorus, and the lead synth is held back until the second chorus. The form runs Verse 16, Verse 16, Chorus 16, Breakdown 32, Chorus 16, Chorus 16 bars (p0018).
> The exact numbers vary from song to song, but the direction is stable: the verse should sit "quieter" than the chorus. You can distribute this first through the vocal delivery and the entry points of instruments, rather than relying only on adding or removing tracks.

### Chorus ("B" section)

- Also usually recurs, **of comparable length to the verse**
- Provides **contrast** with the verse material
- Usually contains the song's **hook**: the melodic idea meant to stay in the listener's mind
- Usually serves as the **musical resolution** point, whereas the **verse builds musical tension**
- ★ **Key distinction**:
  **Recurring verses share the same music but usually have different lyrics;
  recurring choruses usually share the same music and the same lyrics.**
- When there are lyrics, the chorus usually **contains the song title**
- General rule: **the first chorus comes after the verse** (although some songs open with the chorus)

### Bridge ("C" section)

- Provides **contrast** with the verse and chorus
- Usually appears **only once** in the song
- Often sounds **markedly different** from the rest musically: it may be in a **different key**, use **an unusual chord progression**, or have **a distinctly different texture density and energy level**
- In some genres the bridge is used for an **instrumental solo**
- Usually appears **only after at least one verse and one chorus**

> ★ Note that the chorus rule "share the same lyrics" does not conflict with this library's lint #16, "chorus varies from pass to pass": **the words can stay the same while the arrangement must not**. DeSantis is talking about the identity of the song's words and music; the lint is talking about the arrangement.

---

## 2. Common Commercial Forms

> **ABABCB** = Verse–Chorus–Verse–Chorus–Bridge–Chorus

- Some songs **add one or more extra choruses** at the end of this basic form
- **This form, unaltered, is used by most contemporary pop songs that might be heard on the radio**
- **Textbook example**: Lorde, "Royals"

### 2.1 When This Terminology Does Not Apply

> Forms built only from verse, chorus and bridge are **less common in more underground or experimental music**.
>
> **Most contemporary electronic genres without vocals tend to avoid traditional verse and chorus sections,
> and instead create formal contrast through the "addition and subtraction of layers."**
> (See DeSantis, "Common Forms 2: Layering as Form.")

**This library's handling**: ARR-SPEC's `form[]` supports both approaches.
Vocal music uses section names; purely electronic music uses **changes in layer count**,
whose energy curve is generated naturally by `roster[].entry/exit`, so it does not need section names to hold it up.

> This is also the source of the "lineup is form" section in `SKILL.md` §5.

### 2.2 DeSantis's Own Closing Advice

> If the work is in a genre closer to pop music, **using just these few section types is enough to create a great deal of music**.

**Do not invent section types just because you fear monotony.** Monotony comes from treating everything the same way, not from repeating section names.

---

## 3. Full Table of This Library's Measured Data

Corpus: **62 songs from Cambridge-MT multitrack** (natural sample, not curated). Each song was reverse-engineered into ARR-SPEC, and the hit rates for each rule's criterion were counted.

| Rule | Hits | Tier | Notes |
|---|---|---|---|
| Energy curve must have a drop | **62/62** | **Strong rule** | No exceptions |
| Lineup must have an instrument entering mid-song | **59/59** | **Strong rule** | |
| At least one instrument must exit early | **59/59** | **Strong rule** | |
| Not all parts should align strictly to the grid | **62/62** | **Strong rule** | Failure conditions in `mc-rhythm-section` §2.0 |
| The opening should not lay every instrument in at once | **54/59** | **Strong rule** | The 5 exceptions are all specific styles |
| At least one clear subtraction somewhere in the song | **36/62 = 70%** | **Tendency** | |
| Energy should fall back before the peak climax | Full set **22%** / human ground truth **5/7** | **★ Contradiction, treat only as a technique** | See §3.1 |
| Lineup is densest at the climax | **25/59 = 42%** | **Pending** | |

**Also**: tempo calibration (56 songs of ground truth), section calibration (7 songs human-annotated, 72% hit rate, **median deviation 0.0 s**).

### 3.1 ★ The Contradiction Deserves Separate Mention

"Energy should fall back before the peak climax" holds in only **22%** of the full set of 62 songs,
but in the 7 **human-annotated** ground-truth songs it holds **5/7**.

**Source of the gap**: the algorithm locates the "climax" using the energy peak, whereas the human ear does not always place the climax at the point of greatest energy.
So the 22% figure **does not measure this rule**; it measures "whether there is a dip before the energy peak."

**Conclusion**: this rule is **neither downgraded to a pseudo-rule nor promoted to a strong rule**.
It is listed as a **technique**, and appears in `SKILL.md` in the wording "you can do this" rather than "you must do this."

> ★ This is an instance of this library's methodology: **when a metric cannot measure accurately, do not use the metric to overturn the textbook; first ask whether the metric is measuring what you think it is.**
> (Another instance is in `mc-case-studies` §5.2: the lesson from the misjudgement caused by a hard-coded "12 dB dynamic range.")

### 3.2 How to Use Evidence Tiers

| Tier | How to write it in SKILL.md |
|---|---|
| **Strong rule** | "must"; goes into the 20-item self-check table |
| **Tendency** | "should usually"; not in lint, goes into the "must pass after writing" checklist |
| **Technique** | "you can do this"; appears only in the diagnostic path |
| **Pending** | **Not written into the skill**; only listed in the measured table above, awaiting more data |

---

## 4. Suno Default Behaviour → ARR-SPEC Counter-Fields

The full fourteen items are in `mc-ai-tell-audit` §2. Only the arrangement-related rows are kept here for easy comparison.

**Usage**: when no instructions are given, the generation backend drifts toward the left column. The corresponding ARR-SPEC field exists **to pull it back**.

| Backend default tendency | ARR-SPEC counter-field |
|---|---|
| Sections of equal length, all multiples of 8 or 16 | `form[].bars` + lint #3 (not all may be multiples of 4) |
| Energy rises monotonically to the end | `energy_curve[]` + lint #1 (must include a drop) |
| Every instrument filled in from the opening | `roster[].entry` + lint #5 |
| Every instrument sounds from start to finish | `roster[].exit` + lint #6 (at least one instrument exits early) |
| A fill every 4 bars | `groove.fill_policy.bars` + lint #10 (not an arithmetic sequence of 4) |
| All parts strictly aligned to the grid | `groove.push_pull` + lint #11 (must carry a magnitude) |
| Second chorus identical to the first | `section_variation[]` + lint #16 |
| Dynamic range flattened | `dynamics[]` + lint #12 |
| Stereo width unchanged across the whole song | `mix_intent.sound_stage[]` + lint #13 |

---

## 6. Parts Not Covered by This Skill

| Content | Where to find it |
|---|---|
| Music-theory analysis of form (sonata form, rondo form, phrase structure) | `mc-form` (L1), based on Wu Zuqiang, Li Jiti and Yang Ruhuai |
| How to divide the frequency bands and who competes with whom | `mc-texture-layering` |
| How to orchestrate specific instruments | `mc-orchestration` |
| Whether it sounds like a real human player | `mc-rhythm-section` |
| Typical forms of each style (city pop's, trap's) | **L3 style layer** |
| Structure of film scoring (follows the picture, not the sections) | Writing music to picture is outside the scope of this package |
