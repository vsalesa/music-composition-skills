---
name: mc-style-chinese-pop
description: Mandarin and Cantonese pop as a style layer (Chinese pop style layer). What is actually specific to Chinese-language pop rather than borrowed wholesale from J-pop and Anglo-American pop, the transfer table for what may and may not be carried in or out, the tone-melody constraint that shapes Mandarin and Cantonese melody writing and why judging it belongs to the lyricist, what the corpus can currently support and what it cannot, and the declared gaps. Use when writing or arranging Mandarin or Cantonese pop, when deciding whether a J-pop or Western device fits, when a melody fights the words, or when choosing references. Keywords: Chinese pop, Mandarin pop, Cantonese, lyric setting, tone clash, tone fitting, Chinese pop arrangement.
---

# Chinese Pop Style Layer (Chinese Pop)

## Basis for this skill

The basis is the songbook corpus (*The Same Song* (Tóng Yī Shǒu Gē), 20th-Century Chinese Pop Classics; *2012 Selection of Pop Songs*; *My Pop Guitar* (Wǒ de Liúxíng Jítā) 1/2/4), empirical reverse-engineered ARR-SPEC measurements, and transfers from the general layer. There is no specialist book on Mandarin pop arrangement method. ★ **This skill will not invent style claims just to look complete**: every item below is marked with its source.

## Which sections to read for each task

| Task | Read |
|---|---|
| **Deciding whether a J-pop or Western device works** | ★ §2 transfer table |
| Melody fights the lyrics | §3 Tone clash and tone fitting (★ **but judging and correcting it is the lyricist's job**) |
| What the corpus can show | §4 |
| Cantonese | §5 |
| What is still missing | §6 |

## Boundaries

| Not covered here | Where it belongs |
|---|---|
| **Judging and correcting tone clashes and tone fitting** | ★ **The lyricist's job.** This skill only states its constraint on **arrangement** (§3.2) and the self-check method for melody writing (§3.1, §3.3) |
| Chord progressions themselves | `mc-progressions`, `mc-harmony` |
| General arrangement decisions | L2 skills |
| Instrument technique for Chinese folk instruments | `mc-orchestration` |
| Process-based structure in Chinese music, zhǎnyǎn (extension), and qǐchéngzhuǎnhé (introduction–development–turn–conclusion) | `mc-form` reference.md §5 |
| sǎn–màn–zhōng–kuài–sǎn (free–slow–medium–fast–free tempo sequence), bǎnqiāngtǐ (banqiang form), qǔpáitǐ (qupai form) | Traditional opera and folk structures; this package does not cover them |
| Songbook score examples | this skill §4.2 |

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① Mandarin or Cantonese** | ★ **The melodic constraints of the two are completely different** (§3, §5) |
| **② Era** | Chinese pop "style" varies enormously across eras (1990s vs 2010s vs now) |
| **③ Is the reference Chinese or foreign?** | ★ Determines how the §2 transfer table is used |
| **④ Lyrics first or melody first?** | ★ In Chinese this decision matters far more than in English (§3.2) |

---

## 2. ★ Transfer Table

**Chinese pop borrows heavily from J-pop and Western pop in arrangement. That in itself is not a problem; the problem is borrowing in the wrong place.**

| Device | Can it transfer to Chinese pop? | Notes |
|---|---|---|
| **J-pop harmonic vocabulary** (Oudou progression, Komuro, canon) | ✅ **Fully transferable**, and already mainstream | See `mc-progressions` |
| **J-pop A–B–sabi (chorus) three-part structure** | ✅ Transferable; already mainstream | `mc-form` §2.2 |
| **J-pop B-melo (pre-chorus)** | ✅ Transferable | In Chinese it is simply the pre-chorus (yù fùgē) |
| **Western Verse–Chorus two-part form** | ✅ Transferable | Earlier Chinese pop was mostly this form |
| **City pop instrumentation and timbre** | ✅ Transferable | See `mc-style-citypop-rnb` |
| **J-pop melodic density** | ⚠️ **Partially transferable** | ★ Japanese sets one syllable per note; Chinese sets one character per note, but characters are "heavier." Copying Japanese density wholesale makes Chinese hard to articulate |
| **English pop's linking and weak-syllable treatment** | ❌ **Not transferable** | Chinese has no unstressed syllables; forcing it turns into blur |
| **English-style rap flow** | ⚠️ Partially transferable | Chinese rap stress patterns differ. ★ For how rap and Chinese-style elements divide the work, see `mc-style-hiphop` §8.1 and `mc-workflow` §2.4 |
| **Position of large melodic leaps** | ⚠️ ★ **Constrained by tone clash** (§3) | This is the hardest local constraint in Chinese |

★ **One criterion**:
> **Harmony, instrumentation, and structure can be borrowed freely; melodic pitch direction cannot, because it is locked by tone.**

---

## 3. ★ Tone Clash: The Hardest Local Constraint in Chinese

### 3.1 What it is

Standard Mandarin has four tones, and **each syllable carries its own pitch contour**.
If the melodic interval entering a syllable runs against that syllable's tone shape, listeners will hear **a different character**. This is called **tone clash** (dàozì).

**Judgment model**:

```python
contour  = TONE_PITCH[t][1] - TONE_PITCH[t][0]   # the syllable's own tone shape
incoming = notes[i] - notes[i - 1]               # interval entering the syllable
if   contour > 0 and incoming < 0: risk         # rising tone (yángpíng) should rise but descends
elif contour < 0 and incoming > 0: risk         # falling tone (qùshēng) should fall but ascends
elif contour == 0 and abs(incoming) >= 3: risk  # level tone pulled off course by a large leap
```

`TONE_PITCH` takes the start and end point of each tone from Zhao Yuanren's five-degree tone-letter system: yīnpíng 55 (level), yángpíng 35 (rising), shǎngshēng 21 (falling; in connected speech it takes the half-third form, and the full 214 appears only in isolation and at the end of a phrase),
qùshēng 51 (falling), and neutral tone about 3 (level; inherently light and short, so its weight is halved). For melody, this reduces to three rules: **rising-tone syllables should not be entered by a descending interval, falling and third-tone syllables should not be entered by an ascending interval, and level-tone syllables should not be entered by a leap of three semitones or more.**

★ **The key point of this model**: it compares the **melodic interval entering this syllable** with **this syllable's own tone shape**,
**not** "the trailing note of the previous syllable vs. the leading note of the next syllable."
(The latter was the first-version approach; it fails to detect the textbook cases.)

### 3.2 Three consequences for arrangement

**Judging and correcting is the lyricist's job, but it constrains the arrangement in return:**

1. ★ **Positions of large leaps are not free**: whichever syllable a large leap lands on carries tone-clash risk.
   → This limits the leap placement in `mc-melody` §3.
2. ★ **"Melody first" costs more in Chinese**: writing the melody and then filling in lyrics means the lyricist must satisfy meaning, rhyme, and no tone clash at once. **Lyrics first, or revising while writing, is more common.**
3. **Changing the lyrics on the same melody requires rechecking**: the second verse has different words, so the tone-clash risk points differ.
   → Write in `form[].note`: "this section's melody is the same as A1 but the words differ; recheck needed."

### 3.3 Self-check action

> **Read each section's melody and lyrics aloud together. If it sounds like a different character, that is a tone clash.**
> A more systematic method: check only three kinds of positions (the highest note of each section, the first syllable of each phrase, and the landing of each large leap of five semitones or more), and use the §3.1 model to compare the entering interval with the syllable's tone shape.

---

## 4. Corpus Status: What Can Be Looked Up

### 4.1 Reverse-engineered ARR-SPEC (3 entries)

Among this library's measured reverse-engineered ARR-SPECs, **3** have `style_layer: mc-style-chinese-pop` (3 finished Chinese pop tracks):

| Metric | Value |
|---|---|
| BPM median | 137 (range 131–141) |
| Median section count | 10 |
| Median duration | 217 seconds |

⚠ **3 entries are not enough to support any style claim.** They are listed here only to show what can be looked up.
★ The 137 above is only the median of three entries; **do not treat it as the BPM of Chinese pop.** The BPM that the scores can show is in §4.3.

### 4.2 Songbook corpus

| Book | Pages | Nature |
|---|---|---|
| *The Same Song* (Tóng Yī Shǒu Gē), 20th-century Chinese pop collection | 569 | 20th-century song collection; the selection pool for the four-way alignment table |
| *2012 Selection of Pop Songs* | 140 | Used for harmony and form statistics |
| *My Pop Guitar* 1 / 2 / 4 | 100/111/107 | ★ **Includes chord markings and section-by-section harmonic analysis**; suitable for progression statistics |

### 4.3 Songbook measurements (931 entries across five songbooks; only score parameters stored)

Four Chinese songbooks (*The Same Song*, 20th-century works, 379 songs; *2012 Selection*, 102 songs; *My Pop Guitar*, three volumes, 83 songs; total n=564):

| Metric | Value |
|---|---|
| Key signature (tonic of the first key; for modulations, take the starting key) | F 15%, C 13%, G 13%, D 10%, ♭B 10%, E 9%, A 9%, ♭E 8% (n=550) |
| Time signature | 4/4 69%, 2/4 25%, 3/4 4%, 6/8 2% (n=546) |
| BPM, only where a number is marked on the score | P10 58 / median **84** / P90 120 (n=78; **almost all from the 20th-century works in *The Same Song***) |
| Tempo and expression terms | moderate 58, slightly slow 28, slightly fast 24, gradually slower 18, with feeling 12, passionate 9, freely 8 |
| Genres marked on the scores | Film interlude songs, film theme songs, Xinjiang folk songs, Shaanxi folk songs, opera excerpts |

**How to read this:**
- The key-signature distribution in the Chinese songbooks is quite flat: F, C, G, D, and ♭B together account for 60%, and no single key exceeds 20%. Contemporary works (*2012 Selection* and the guitar scores) are led by C, G, D, and ♭E, and many guitar scores use a capo to return to C/G chord shapes.
- ★ **This library still has no measured BPM for contemporary Chinese pop.** The 78 songs with numbers are almost all 20th-century folk and film songs, so the median of 84 cannot be extrapolated to today's pop. *2012 Selection* and the guitar scores give only tempo terms (moderate, slightly slow) and no numbers. BPM will require an audio corpus.
- 2/4 time, a quarter of entries, is a feature of 20th-century songbooks; contemporary Chinese pop is almost entirely 4/4.

The English Fake Book (Billboard top twenty, 1955–1986, n=367) keys, chord cycles, and skeletons are in `mc-case-studies` reference §1.2, serving as the Western reference.

### 4.3 ⚠ One Statistical Attempt and Its Result (Honest Record)

**What was done**: from the *My Pop Guitar* series, extracted the "1=X" key signatures and the section-by-section harmonic progressions, converted them to Roman numerals, and counted four-chord windows.

**Result**: only **10 songs** could be parsed. The most common windows are `I V I V` (3 times), `V I IV V` (3 times), `I IV IV I` (2 times), and so on.

**Conclusion**: ★ **The sample is too small, and the results are generic progressions that do not constitute a Chinese-pop feature.**
**It was not written up as "characteristic progressions of Chinese pop"**: that would be a misuse of the data.

---

## 5. Cantonese: Declared as a Later Layer

> **Cantonese and Korean do not block progress: this library is layered and composed from the start, so these language layers can be added later.**

**So Cantonese here is a declared interface, not an empty placeholder:**

| Item | Notes |
|---|---|
| **xiéyīn (tone fitting)** | Cantonese has nine tones, so the constraints are **much stricter** than Mandarin's four. Judgment is the **lyricist's** job |
| **What this skill can say** | Only that it exists and is stricter; no specific rules are given |

★ **Do not invent Cantonese rules before reading the source texts.** Cantonese tone fitting has a precise system; anything guessed will certainly be wrong.

### 5.1 What Each Period Means for Arrangement (Huang Zhihua, *Forty Years of Cantonese Pop* (Yuèyǔ Liúxíng Qǔ Sìshí Nián))

| Period | Foundation | What it means for arrangement |
|---|---|---|
| 1949–1959 | Two sources: the Mandarin-era popular songs (shídài qǔ) passed down from Shanghai, and the golden-age Cantonese opera and ballad tradition (yuèqǔ) (p0047) | Cantonese pop began with two foundations: a dance-band sound from the era songs, and the gongs and bānghuáng melodic style of Cantonese ballad tunes. To write "old-school Cantonese flavor," choose the foundation first |
| 1960s | Cantonese film dominance pushed styles to be either **too Cantonese-opera-like** or **"a tiger painted badly that ends up looking like a dog," i.e., over-Westernized** (p0048); mostly old tunes with new lyrics, such as Cantonese opera tunes with newly written words (p0048) | ★ The two failures the book names are exactly what "retro Cantonese" falls into today: once the gongs sound it becomes Cantonese opera; once it is Westernized, it becomes neither |
| 1980–1982 | The campus folk wave from Taiwan blew in, encouraging young people to write their own songs (p0051); the market cooled, and record companies brought in new singers and new lyricists (p0051–0052) | Folk-guitar instrumentation entered Cantonese pop: acoustic guitar as the core, light instrumentation, lyrics weighted above melody |

---

## 7. Mapping to ARR-SPEC Fields

| Field | This skill |
|---|---|
| `meta.style_layer` | `mc-style-chinese-pop` |
| `form[].note` | ★ Sections with the same melody but different words should be marked "recheck tone clash needed" |
| `vocal.persona` | Language (Mandarin or Cantonese) must be written in: **it affects which voice library the backend selects** |
| **Coupling with lyrics** | ★ In Chinese this coupling is much tighter than in English (§3.2). The lyrics for the same song are read from `meta.upstream.lyrics`; for who sets and who reads the six shared fields, see `mc-workflow` §5.1 |

---

## 8. Checklist After Writing

- [ ] Determined **Mandarin or Cantonese**
- [ ] Checked the §2 transfer table; borrowed devices are in the "can transfer" column
- [ ] **Considered tone clash for the positions of large melodic leaps**
- [ ] Sections with the same melody and different words **are marked for recheck**
- [ ] The direction of lyric-melody coupling (lyrics first or melody first) was **deliberately chosen**
- [ ] ★ **Did not cite the 10-song statistic from §4.3 as a style feature**
- [ ] ★ **Did not invent Cantonese rules**
- [ ] Every style claim cited can be backed by a source

---

## Appendix: Sources

- **Corpus**: *The Same Song* songbook; Chinese pop song collections (cnpop-2012, cnpop-gtr-1/2/4). ★ **These are songbooks, not theory books**
- **Cantonese source text**: Huang Zhihua, *Forty Years of Cantonese Pop*
- **Measurement**: 3 reverse-engineered ARR-SPECs derived from 3 finished Chinese pop tracks
- **Tone-clash judgment**: model in §3.1; tone values from Zhao Yuanren's five-degree tone-letter system
