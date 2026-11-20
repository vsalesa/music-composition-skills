---
name: mc-progressions
description: Chord progression lookup library - the eight famous named progressions with their variants and what each one actually does, a mood reverse-lookup, the eight variation techniques that turn one standard progression into ten, and an explicit warning list of the progressions generative models default to. This is a lookup skill, not a teaching skill - it answers "give me a progression that does X". Harmonizing a melody, choosing chords bar by bar, or reharmonizing is mc-harmony, and a full track needs mc-harmony first and this table second. Use when you need a progression for a specific mood or section, when a loop feels stale, when varying a standard progression, or when checking whether a progression is too defaulted-to. Keywords: chord progression, progression lookup, canon progression, Komuro progression, loop, cliche, vary progression.
---

# Chord Progression Lookup (Progressions)

**This is a lookup skill, not a teaching skill.**

| You ask | Go to |
|---|---|
| "Give me a progression that feels like X" | **this skill** |
| "Why does this progression work" | `mc-harmony` |
| "How do I make this progression sound better" | this skill §4 + `mc-harmony` §7 |

## Which sections to read for each task

| Task | Read |
|---|---|
| Find a progression by mood | §1 Mood reverse-lookup table |
| Want a progression with a specific classic flavor | §2 The eight famous progressions |
| Browse by category | [reference.md](reference.md) |
| The progression you have is getting stale | §4 Eight variation techniques |
| **Worried the progression is too cliche** | ★ §3 |
| Transposing | [reference.md](reference.md) §5 |

## Boundaries

| Not covered here | Where it belongs |
|---|---|
| Harmony principles, function, and reasons | `mc-harmony` |
| The nine-step reharmonization process | `mc-harmony` §7 |
| Modulation | `mc-modulation` |
| Progression vocabulary specific to a style | `mc-style-*` (L3). ★ This skill's vocabulary leans toward **J-POP**; Chinese pop harmonic vocabulary is not broken out separately; **K-POP and Western pop have no corresponding L3 skill**, so use this skill's general table and declare it in the spec sheet (see reference.md §11) |
| Full category tables, famous-song index, transposition table | [reference.md](reference.md) |

---

## 1. Mood Reverse-Lookup Table

| Mood | First choice |
|---|---|
| **Bright / powerful** | I–IV–V–I / IV–V–I–VIm / pop-punk progression |
| **Setsunai (bittersweet ache) / emo (heart-wrenching)** | **Oudou progression 4536** / C–E7–F–Fm / IVm type (C–Fm–C) |
| **Warm / steady** | C–Dm–Em–F / C–Am–F–G / C–Gm7·C7–F |
| **Stylish / urban** | **Marusa progression** / ura-chord (backdoor) progression / ii–V–I / F/G dominant substitute |
| **Melancholy / enka / kayokyoku** | Am–G–F–E / Am–Dm–E7–Am / minor ii–V |
| **Grand / epic lyrical** | C–Bm7(♭5)·E7–Am type / 8-bar canon / descending bass cliche |
| **Abrupt turns / complex** | Em–F–Am–G / F–Dm–G–Em·E7 / C–B7–Em7–E♭ |
| **Danceable** | F△7–E7–Am–C7 + four-on-the-floor / C7(9,13)–F7(9,13) riff |

---

## 2. The Eight Famous Progressions

Below, all are in **Key = C** (minor-type progressions in Key = Am). Roman numerals are for thinking; letter names are for handoff; **record both**.

### 2.1 Oudou Progression (4536)

```
IV△7 – V7 – IIIm7 – VIm7      F△7 – G7 – Em7 – Am7
```
The name is the numerals 4-5-3-6. **4 and 5 are major chords, 3 and 6 are minor chords — the drop from "bright to dark" is the source of the setsunai (bittersweet ache) feeling.** Together with the canon progression, it is one of the two ace cards.

| Variant | Effect |
|---|---|
| `IV△7–V7–III7–VIm7` (F△7–G7–E7–Am7) | III becomes a dominant seventh → **stronger weeping quality**, a stronger pull toward VIm |
| `IV△7–V(onIV)–IIIm7–VI7` (F△7–G/F–Em7–A7) | The slash chord in bar 2 is the **"kyun" (heart-fluttering) point** |

### 2.2 Canon Progression

```
I – V – VIm – IIIm – IV – I – IIm – V      C – G – Am – Em – F – C – Dm – G
```
**The inversion form `C–G/B–Am–Em/G–F–C/E–Dm–G`** makes the bass **step down along the scale** (C-B-A-G-F-E-D-G) = bass-line cliche.

- The four-chord simplified form `C–G–Am–Em` is equally standard; **ending Em→G loops better** (the final dominant chord flows smoothly back to the tonic).
- For the chromatic version (bass C–B–B♭–A–A♭–F#–G), see [reference.md](reference.md) §4.

### 2.3 Komuro Progression (6451)

```
VIm – IV – V – I      Am – F – G – C
```
**Starts with minor color → resolves stably to major.** The sound of the J-POP golden age of the 1990s.
Close relative `Am–G–F–C` (6541; the bass steps downward, more lyrical).

### 2.4 Marusa Progression / Just The Two Of Us (4361)

```
IV – III7 – VIm – I      F – E7 – Am – C
```
**Stylish, urban, emo — synonymous with city pop / neo-soul.**
E7 is a **secondary dominant** pointing to Am, i.e., the "emo point."
It can be used once as an accent or looped for the whole song; **"almost any melody sounds stylish over it."**

The seventh-chord enhanced version `F△7–E7–Am–C7` with a four-on-the-floor kick → techno/dance.

### 2.5 Pop-Punk Progression (1564)

```
I – V – VIm – IV      C – G – Am – F
```
Bright, powerful, universally used.
**Starting the same set of chords at a different point** yields the common variants `4156` (F–C–G–Am) and `6415` (Am–F–C–G);
**whether the first and last chords are major or minor determines the overall brightness or darkness.**

### 2.6 Loop Progression (1625)

```
I – VIm – IIm – V      C – Am – Dm – G
```
The seventh-chord version `C–Am7–Dm7–G7` is equally standard. **It sounds somewhat retro today, and deliberately using that retro quality is an effective choice.**
The second half's 2→5 is the **ii–V**: IIm stands in for IV, and the bass **leaps up a fourth**, more forceful than 4→5.

> **Typical use**: loop `C–Am–F–G` three times, **then switch to this progression on the fourth time** as the trigger into the next section.

### 2.7 Reverse Loop (2516)

```
IIm – V – I – VIm      Dm – G – C – Am
```
★ **Key insight**: it is not the chords arranged backwards, but **two groups of structure** —
"the motion group (2→5) comes first, the tonic group (1→6) comes after."

Seventh-chord version `Dm7–G7–C△7–Am7`: **it does not start on the tonic**; the ii–V circles back to the tonic from the opposite direction.

### 2.8 Dreams Come True Progression (Dorikamu)

```
I△7 – VIIm7 – IIIm7 – IIIm7(onII)      C△7 – Bm7 – Em7 – Em7/D
```
**Its character changes dramatically with tempo and melody.** The variant `C△7–B7–Em7–G7` (VIIm7→VII7) is more tear-jerking;
the closing dominant seventh strengthens the motion back to the tonic.

---

## 3. ★ Cliche Warning Line: Which Progressions Generative Models Default To

**This section is unique to this library; it does not appear in the Japanese source texts.**

Generation backends, given prompts like "pop / emotional / ballad," **very likely default to outputting the following**:

| Progression | Why it is risky |
|---|---|
| `I–V–VIm–IV` (1564) | The **most overused** four-chord pattern in the world. The model's first instinct |
| `VIm–IV–I–V` (6415) | A rotation of the same set, equally overused |
| `I–VIm–IV–V` (1645) | A template since the 1950s |
| `IV–V–IIIm–VIm` (4536) | The first instinct in a J-POP context |

**This does not mean it cannot be used.** The test is:

> **Did you "choose" it, or did it "default" into place?**

**Three countermeasures** (increasing in strength):

1. **Keep the progression, change its form** — use at least two of the §4 variations, especially **changing the starting point** and **bass-line design**
2. **Keep the progression, change the harmonic rhythm** — don't do one chord per bar. Moving where the chord changes is more effective than changing the chords themselves
3. **Replace it** — pick a functionally equivalent one from §3 (sentimental type) or §4 (jazz/urban type) of [reference.md](reference.md)

★ **The most effective is actually #2**, because models are heavily trained on "what the chords are," but are weak on "when the chords change" — **harmonic rhythm is a cheaper means of differentiation**.

**Self-check action**: look up your progression in the table above.
If it matches, write one sentence in `form[].note` of ARR-SPEC explaining "why I still chose it."

---

## 4. Eight Variations: Turning One Progression into Ten

**These techniques can be applied to any progression in this library.**

| # | Technique | Method |
|---|---|---|
| 1 | **Change the starting point** | Start the same set of chords from a different chord (1564→4156→6415; 1625→2516). ★ **Whether the first and last chords are major or minor determines brightness** |
| 2 | **Seventh-ize / add9-ize** | Adding sevenths to all chords (Am–Dm–Em→Am7–Dm7–Em7) instantly gives a modern pop feel; add9 (Amadd9–Fadd9–Gadd9) is lighter and softer |
| 3 | **III→III7 (secondary dominant)** | ★ **The fastest "weeping" switch.** A secondary dominant (A7/B7/C7/D7/E7) can be placed before any diatonic chord |
| 4 | **Slash-chord conversion (bass-line design)** | Use inversions to make the bass move stepwise (canon C–G/B–Am–Em/G…), or chromatize (C–G/B–B♭–F/A–Fm/A♭–D/F#–F/G). ★ The dominant chord can be replaced with **F/G** (= G7sus4(9)), which is more subtle and refined |
| 5 | **Insert sus4** | Insert Vsus4 before the V at the end of a section (F→Gsus4→G) to emphasize "this part is ending." **Adding it only on the last pass** also works |
| 6 | **ii–V-ize** | Split out IIm7 before V (E7→Bm7(♭5)–E7; G7→Dm7–G7). Gm7–C7 pointing to IV brings a warm surprise |
| 7 | **Beat adjustment and splicing** | A 4-bar pattern can be compressed to 2 beats per chord; **splice together 4-bar patterns you like into 8 bars, and the melody will naturally emerge** |
| 8 | **Borrowing from the parallel key** | IV→IVm, or add ♭VI/♭VII/♭III, instantly getting setsunai or rock grit |

> ★ Technique 7 is the most underrated in this section: **splicing two 4-bar patterns is much easier than inventing one 8-bar pattern, and the results are good.**

---

## 5. Mapping to ARR-SPEC Fields

| Field | Notes |
|---|---|
| `form[].harmony` | Roman-numeral notation. **Progressions copied from this skill must be converted to Roman numerals; do not copy the letter names** |
| `form[].harmony_letters` | Letter-name notation. Transpose according to `meta.key`; see the table in [reference.md](reference.md) §5 |
| `form[].note` | ★ If you used a progression on the §3 warning list, **write here why you still chose it** |
| lint #9 | At least one section must contain a non-diatonic chord — techniques 3, 6, and 8 in §4 all satisfy this |

---

## 6. Must Pass After Use

- [ ] The progression has been converted to **Roman numerals**, not copied directly as letters
- [ ] Letter notation has been transposed to the actual `meta.key`
- [ ] Checked against the §3 warning list; if it matched, the reason was written down
- [ ] **Harmonic rhythm is not one chord per bar throughout the piece**
- [ ] At least one §4 variation was used (unless the original feel is deliberately wanted, and this is stated)
- [ ] The chorus and verse do **not repeat the same progression verbatim** (the same progression with different harmonic rhythm also counts as a variation)

---

## Appendix: Sources and Bias Statement

- **Motto! Omoi Doori ni Sakkyoku ga Dekiru Hon (More! A Book for Composing as You Wish)**, **Dekiru Zero kara Hajimeru Sakkyoku Chō-Nyūmon (Ultra-Beginner Composition, Starting from Zero)**, **Puro no Kyoku-zukuri Tekunikku (Professional Songwriting Techniques)** — §1, §2, §4, and all classification tables.
- ★ **Bias statement**: this vocabulary **leans toward J-POP** (Oudou, Komuro, Marusa, and Dreams Come True are all names used in the Japanese industry).
  It is **highly applicable to Mandarin pop and city pop**, but under-covers EDM, hip-hop, and Western rock.
  Those are covered separately by the **L3 style layer** — **do not treat this table as "all of pop harmony."**
- Chinese pop progression vocabulary: → `mc-style-chinese-pop`
- Jazz standard progressions: → `mc-style-jazz`
- Full category tables (Oudou J-POP type / sentimental type / jazz urban type / minor type / cliche-line type / 8-bar large-scale), famous-song→progression index, and transposition table are all in [reference.md](reference.md).
