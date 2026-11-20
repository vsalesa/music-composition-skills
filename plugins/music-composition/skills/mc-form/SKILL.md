---
name: mc-form
description: Song form and section design - the terminology, the standard templates, and how to build a section (setsu) backwards from the chorus. The Japanese section vocabulary mapped onto Anglo-American terms (and the two that are routinely mistranslated), the two broad families sorted by chorus position, the royal-road template with its repetition-omission rule, ternary form and the recapitulation principle, EDM and club variants, lead-in options, and the classical Chinese/Russian period-and-phrase apparatus for when pop terms run out. Use when laying out a song, when sections blur together, when deciding how many verse-chorus cycles, when a bridge is needed, or when filling the form table of an ARR-SPEC. Keywords: song form, sections, verse, chorus, bridge, period, recapitulation, A-melo, sabi.
---

# Song Form and Sections

**This skill covers "which blocks make up this song, how long each block is, and in what order".**

The division of labor between this skill and `mc-arrangement-arch` is the easiest point in this library to confuse:

> **`mc-form` covers what song form is (music theory and convention);
> `mc-arrangement-arch` covers why this song is cut this way (decisions and asymmetry).**

Concretely: **"the chorus is usually 8 bars" belongs to form; "the second verse of this song is 14 bars because it must break the integer pattern" belongs to arrangement-arch.**

## Which sections to read for each task

| Task | Read |
|---|---|
| Laying out a song's structure | §2 templates → §5 designing backwards |
| Section terminology does not match | §1 mapping table (★ two terms are routinely mistranslated) |
| Sections blur together | §4 and `mc-arrangement-arch` §4 |
| Whether to add a C section or a bridge | Composition options in §5 |
| Writing EDM / club music | §2.5 |
| How to start the opening | §3 |
| Pop terms are not enough | §6 classical form devices |
| Filling in the form table of an ARR-SPEC | §7 |

## Boundary

| Not covered here | Where it lives |
|---|---|
| Why this section is 14 bars rather than 16 (asymmetric design) | `mc-arrangement-arch` §4 |
| Energy curves, entry and exit events | `mc-arrangement-arch` |
| How a motif develops into a phrase, and what old material a section reuses | `mc-development`; the internal segmentation and answering of phrases remains in `mc-melody` §7 |
| How to modulate between sections | `mc-modulation` |
| How to harmonize the chorus | `mc-harmony` |
| The typical form of a given style | `mc-style-*` (L3) |
| Structure of film and TV scores (follows the picture, not the form) | Scoring (writing music for picture) is outside this package; the sections and durations this package hands off are in `mc-workflow` §5 |
| Full classification and score examples of classical forms | [reference.md](reference.md) |

---

## 1. Section terminology mapping

**Japanese (J-POP) terms do not map one-to-one onto Anglo-American terms.** Clarify them before analysis or discussion.

| Japanese | English / Anglo-American | Function |
|---|---|---|
| **A-melo** | Verse (*hira-uta*) | Introductory section. Narrow range, short note values, "*katari*" (narrated) singing; lyrics tell a concrete story and set the scene |
| **B-melo** | Pre-chorus | ★ A Japanese-specific "second verse": a section between A-melo and sabi with a different character, climbing in range and building expectation |
| **sabi** | Chorus | The section where the climax of the whole song sits: highest range, greatest density, most memorable; carries the core message |
| **C-melo / D-melo** | Third development section (bridge position) | Entirely new melody, harmony or rhythm after the second verse, creating an "unexpected development" |
| **ō-sabi** (big sabi) | ≈ Anglo-American bridge / middle eight | ★★ **Not "a bigger sabi"!** Its character is closer to a "second B-melo": introspective, convergent, often with a half-time feel; **it is always followed by a sabi** |
| **atama-sabi** (head sabi) | Chorus opening | The sabi arrives in the first seconds, seizing memory directly |
| **ochi-sabi** (falling sabi) | "Falling" chorus | The same sabi melody **suddenly switches to a very thin lineup** (for example, only piano and voice), moving the listener through the contrast |
| **kime** | Unison accent / tag phrase | A marker phrase of about 2 bars after the end of the sabi: the accompaniment suddenly stops or hits a signature rhythm, and the title words are sung |
| **intro** | Intro (prelude) | |
| **kanso** (interlude) | Interlude | Called "Second Introduction" in English: "the prelude to a second round of verse and chorus" |
| **outro / kōsō** | Outro (postlude) | An instrumental ending |
| **vamp** | Groove section | A section that plays no melody and only states a rhythmic pattern (may be percussion alone, or with bass or guitar added) |
| **coda** | Coda | A **sung** passage appended after the final round of sections ends |
| **ichi-ban / ni-ban** (verse 1 / verse 2) | First round / second round | One round of verse and chorus = one "*setsu*" section; same melody + different words + slight change in lineup: **a device refined over generations to prevent boredom** |
| **break** | Break | The moment when the accompaniment stops completely and only the voice remains |
| **fill** | Fill | A drum fill at a section seam, igniting anticipation in advance |

★★ **The two most often mistranslated**:
1. **ō-sabi ≠ "big chorus"**; it is a bridge
2. **The Japanese term *heikō-chō* = relative major/minor**, not the English "parallel key" (which the Japanese call *dōshu-chō*, same tonic) — see `mc-modulation` §2

**Hierarchy of melodic technique**: partial motif → motif → small phrase → phrase → section → whole song.
> **Melodic-technique definition of sabi: the phrase within a "section" that serves as the climax.**
> **At each level, the size of the climax is proportional to the size of the block at that level.**

---

## 2. Standard templates

### 2.1 Two broad families, sorted by chorus position

| Family | Shape | Description |
|---|---|---|
| **Suehirogari type** (widening toward the end) | `[A→B→sabi]` or `[A→sabi]` | Every section except the sabi "lays the table". **The large majority of modern J-POP belongs to this family** |
| **Junkan kaiketsu type** (cyclic resolution) | `[A→sabi→A]` or `[sabi→B→sabi]` | Ends by returning to the opening melody (ternary form, **recapitulation principle**). Common in the 1960s, in *enka*, *kayōkyoku* and jazz standards; increasingly rare today |

### 2.2 Royal-road full-song template (suehirogari type)

```
Intro → 1A → 1B → 1sabi → (interlude 1)
     → 2A → 2B → 2sabi → interlude 2
     → C-melo (ō-sabi) → 3sabi (may modulate) → (3sabi 2) → outro
```

**Key points**:

- **The A-B-sabi three-part structure is the most common form in Japanese pop** (melodic technique: the pure three-part structure a-b-c = opening − change of perspective − synthesis and resolution)
- **Why there is a "second verse"**: same melody + slightly altered sound + **entirely different lyrics**, an anti-boredom device
- After the second verse, insert a C-melo or bridge (may have a completely new melody, harmony and rhythm) to keep things fresh and build further, then give the sabi once more
- ★ **Omission-of-repetition rule**: section 1 `A−A'−B−C` → section 2 `A−B−C` → **section 3 may start directly from the sabi**
- A full song usually has **2–3 sections and runs 3–5 minutes**; slow songs reduce the number of sections, fast songs increase it (when BPM differs by 3× or more, balance with the number of sections)
- > **The only true standard: the listener is neither bored by its length nor feels shortchanged by its brevity, and finishes satisfied.**

### 2.3 Ternary form template (sabi in the middle)

```
A(melo) → B(sabi) → A'(melo)    ×2–3 sections
```

- The pillar is the **recapitulation principle**: B expands the content of A in a more emotional way (or narrates from a wider perspective), and the return to A brings "a deep sense of insight and wistfulness"
- The continuity between A and B is usually stronger than in a verse = chorus type
- The extended form **A−A'−B−A'' = the classic structure of *qi-cheng-zhuan-he* (introduction, development, turn, conclusion)**
- Rare variant A−B−C: the final section does not recapitulate A; instead it uses a melody that "repeatedly lands on the same note and grows quieter as it closes", **which still sounds like coming home**

### 2.4 Quick reference of other forms

| Form | Structure |
|---|---|
| **Binary form** | A (verse) − B (chorus): the basic form of Western pop and rock |
| **Bridged form** | A − (short bridge) − sabi: does not write a full second verse, only inserts a short connecting passage (raises the range, builds heat) |
| **Compound ternary** | `[A−B−A]−[C−D−C]−[A−B−A]` |
| **Mixed form** | `A−B−sabi−A` (verse = chorus, then the verse returns) |
| **Single-section structure** | Only chorus, or only verse: counting songs, narrative ballads, looping dance tracks |
| **Commercial (CM) song** | Squeezes A/B/sabi into 15 or 30 seconds; development must be extremely clear; **uses changing meters to "adjust the length"** |

### 2.5 EDM / club music variant

**Accumulating intensity over a time scale far longer than in song-based music:**

```
four-on-the-floor kick enters
 → add hi-hat
 → add sustained accompaniment such as piano (repeated in units of 8+ bars)
 → formal intro → A-melo → sabi
 → return to a drums-only section → loop……
```

- Characteristics: **the melody is optional**; the structure is long and large; there are sections with only drums or only pad,
  so **the change in thickness is extremely sharp**; the arrangement is built around the drums
- Two reasons this structure works: (1) gradual accumulation suits dancing; (2) drums-only sections make it easy for a DJ to bring in the next track
- ★ **A structure that sounds verbose and boring at home is extremely effective on the dance floor: purpose determines form**
- The section structure of dance music is often **A−A−A−…−A'−B**: the verse repeats one motif many times, followed by a short chorus
- Extreme form: only one motif within a section (a a a a). **Repetition seeps into the unconscious and evokes a half-involuntary bodily response.
  Even without a big climax, the repetition itself builds intensity**

---

## 3. Starting the opening

Adding an introductory section before the main song, at the very top, works with both broad families of form:

| Method | How |
|---|---|
| **Spoken-style opening** (quiet introduction) | Middle range + pitch almost static + simple rhythm + accompaniment with static harmony, possibly free tempo: start from a state "between speech and song", smoothly leading the listener into the work's world (very common in opera and musical theatre). Form: `D(prelude) − [A−B−sabi] − [A−B−sabi]` |
| **Soaring introduction** (the opposite) | The prelude starts with a soaring phrase (leaping intervals + high register), creating a sharp contrast with the everyday and pulling the listener in at once |
| **Head sabi** | The prelude uses the sabi directly: **the most common option**. `C−[A−B−C]−[A−B−C]` (verse = chorus); `B−[A−B−A]` (ternary). ★ **Two ways to play it**: as written = a dazzling opening; thin accompaniment + slow + free tempo = a smooth narrative introduction |

---

## 4. Contrast between sections

**The root cause of sections blurring together is that adjacent sections are the same in too many dimensions.**
The specific techniques for contrast are in [reference.md](reference.md) §1; here only the test is given:

> **Self-check action**: for two adjacent sections, tick each of these six items—
> **register / rhythmic density / harmonic rhythm / lineup thickness / vocal delivery / phrase length**.
> **If fewer than two items differ, the two sections will be heard as one.**

---

## 5. ★ Designing backwards: from the chorus back to the start

**The design principle is always "work backwards from the sabi as the center".**

| Structure | How to design it |
|---|---|
| **A structure** (single phrase) | Do not change character; plain and simple. When a dance track repeats the same riff, the motif within a section may even be just one (a a a a) |
| **A−B structure** (basic verse = chorus form) | Two-section principle; common in Western rock and R&B, strong in catchiness. **If the sabi already exists → work backwards to "what kind of A could lead into it"; if the A already exists → decide what kind of sabi should follow it.** ★ **The sabi must have impact not only at the opening but also needs enough climax in its second half** |
| **A−B−C structure** (Japanese royal road) | ★ **First think about the sabi (C) and the introductory section A, settle the plan for the middle part, and write B last** |
| **A−B−A structure** (ternary) | Stage "deep wistfulness" or "open resolution" at the end of the phrase. ★ **For the recapitulation to pay off fully, the standard method is to make B's character change dramatically** |

**Two ways to write section B** (within an A−B−C structure):
- **B as bridge**: convergent A → B with short repeating rhythmic motifs and a range that steps up gradually → C with a sense of groove
- **B as second verse**: light A → introspective, quiet B → C that doubles the soaring feeling through contrast
  (the second half of B can be built to stack upward, leading into a short bridge to C)

### 5.1 ★ Warning on expansion

> **Before adding an element in the form `A−B−C → A−B−C−D`, first consider expanding by repeating phrases.**
> Too many elements → the road to the sabi winds and wanders, and focus scatters.

This is an order-of-operations test, not a rule against adding sections. First check whether the techniques already listed in the table above can stretch the length enough (such as repeating a whole riff in the A structure, or the short bridge built into the end of section B in A−B−C). Only when those cannot fill the length and the contrast still cannot be achieved should you consider adding new elements. Whether to add is ultimately governed by the duration budget in §8: each extra element usually means several more bars, and anything beyond 3–5 minutes needs a stated reason.

### 5.2 Adding a kime

Any structure can have a kime of about 2 bars added at the end of a phrase or inside the sabi.
★ **When a song feels like it lacks dynamic contrast (*meri-hari*), consider this first**, rather than adding a section.

This is one of two prescriptions for lacking dynamic contrast; the other is the phrase-repetition expansion in §5.1. Both are lighter than adding a new section, so they come first when trying fixes. How to arrange the kime itself (unison, leaving space, or adding ornaments) depends strongly on its position and style, and belongs to the arrangement execution layer, so it is not expanded in this form section.

---

## 6. When pop terms are not enough: classical form devices

For film and TV scores, instrumental pieces, or when more detailed structural analysis is needed, the pop vocabulary of "A/B/sabi" is insufficient.
The Chinese and Russian-influenced systems provide finer gradations:

| Device | Use |
|---|---|
| **Period (*yuèduàn*)** | A unit stricter than "section". Divided into **one-phrase**, **two-phrase** and **three-or-more-phrase** structures |
| **Compound period** | A larger unit made of two periods |
| **Open period** | A period ending on a non-tonic chord — ★ corresponds to the **cadence openness levels 5–8** in `mc-melody` reference §5 |
| **Introductions and supplements around a period** | Additional parts outside the structure. ★ Explains "why this section is 17 bars rather than 16" |
| **Simple binary form** | Two kinds: with recapitulation / without recapitulation |
| **Simple ternary, compound ternary, rondo, variation, sonata** | See [reference.md](reference.md) §3 |

★ **A period functioning as an independent form and a period functioning as part of a larger form have different characteristics.**
This distinction is useful for judging "is this one section or a whole piece".

> **How this library uses it**: when writing pop songs, use the terms in §1–§5.
> When working on `mc-style-cinematic` or doing structural analysis (`mc-case-studies`), switch to this system.
> **Do not mix the two vocabularies in the same discussion**, or handoffs become muddled.

---

### 6.1 ★ What a section is doing: five modes of statement and six structural functions (Li Jiti)

§1 to §5 use the **names** of sections; this system uses the **behavior** of sections, and fills the gap between names and functions (Li Jiti, *Musical Forms and Work Analysis*, p0022–0024).

| Mode of statement | Characteristics | In one line |
|---|---|---|
| **Presentational** | Stable tonality, unified material, complete syntax | Lay things out |
| **Developmental** | Both statement and harmonic tonality are unstable and increasingly turbulent, the structure fragments, modulations are frequent, syntax is incomplete | Take things apart |
| **Transitional** | Connects what precedes and what follows: first supplements the preceding musical idea → modulates → introduces a new idea, or stops on an **expectant chord** | Build a bridge |
| **Concluding** | Melody is fragmented, tonality is stable, emphasizes a cadence or a sustained tonic | **Answers only** |
| **Introductory** | Hints at the following tonality, tempo, texture and melodic outline | **Asks only** |

Six structural functions: introduction (introductory; there is also a "concluding-style introduction", as in *The Internationale*), beginning (presentational), middle (★ **even when a new theme is introduced in a presentational statement, the function is still contrast**),
connection (transitional, and in large works also "develops earlier unfinished statements"), recapitulation (restores the presentational mode, but its purpose becomes reinforcing the main idea and restoring balance; infusing developmental elements is **dynamic recapitulation**),
coda (concluding; in large works the coda can begin with one supplementary development).

**How to use it**: in the spec sheet, write for each section which mode of statement it uses. If a sabi is written in developmental mode and a bridge in presentational mode, the section functions are misaligned, and renaming them will not fix it.

### 6.2 Five forms of recapitulation (Li Jiti p0066, p0070)

| Form | Method |
|---|---|
| Complete (static) recapitulation | Exactly as before |
| Varied recapitulation | Change the texture or the orchestration; the material stays the same |
| **Dynamic recapitulation** | The motif is reworked, rhythm becomes unstable, harmony intervenes, texture thickens, dynamics intensify; this often expands the structure and can even become the climax of the whole song |
| **Synthetic recapitulation** | Recapitulates material from the middle or the introduction at the same time |
| Reduced recapitulation | Recapitulates only part of it |

The answer to "how does the final sabi change" is in this table. The lyric side's common practice of changing one to three words or adding a line in the last round is the same thing applied to the words (for the corpus figures and how they align with the melody, see `mc-development` §7.4).
★ Recapitulation does not have to be in the home key: Bach's recapitulations are often in the dominant or subdominant. As long as the parts of the section correspond to the exposition, it is called a recapitulation (Zhao Xiaosheng p0232).

### 6.3 How musical ideas develop, and how forms are assembled (Li Jiti)

How musical ideas develop (elaboration, expansion and contrast, and their mapping onto ten techniques) belongs to **`mc-development`** §5.1; how forms are assembled remains in this skill's §2 and reference §4.

## 7. Mapping to ARR-SPEC fields

| Field | This skill |
|---|---|
| `form[].id` | The terminology system in §1 (I / A1 / B1 / C1 / D / O) |
| `form[].name` | ★ **Use Anglo-American terms** (Intro / Verse / Pre-Chorus / Chorus / Bridge / Instrumental / Outro), because they map directly onto the backend's section labels. **Japanese terms are used only in notes and discussion** |
| `form[].bars` | The templates in §2 give default values; **breaking the defaults belongs to `mc-arrangement-arch`** |
| `form[].start_bar` | Sections connect end to end (lint #2) |
| Number of sections | 2–3 sections per §2.2 |

★ **A mapping trap**: **ō-sabi must map to `Bridge`, not `Chorus`.**
If it is mapped wrongly, the backend will give you a high-energy chorus at that position, whereas it should be introspective.

---

## 8. Checklist to pass after writing

- [ ] Terms use the **Anglo-American set** in `form[].name`; Japanese terms appear only in comments
- [ ] **ō-sabi is mapped to Bridge**, not Chorus
- [ ] The song has **2–3 sections**, runs **3–5 minutes** (or a reason is stated for why not)
- [ ] The **omission-of-repetition rule** is applied (the second section drops the repeated opening)
- [ ] Adjacent sections **differ in at least two of the six contrast items**
- [ ] Designed **backwards from the sabi**, not arranged from the beginning forward
- [ ] Before adding a section, **phrase repetition was tried first**
- [ ] The **second half of the sabi also has a climax**, not just impact at the opening
- [ ] If using ternary form, **B's character changes dramatically**

---

## Appendix: Sources

- ***A Book That Explains How Professionals Write Songs*** together with Takayama Hiroshi, ***Melody Writing for Popular Music Composition*** (expanded edition). The backbone of §1–§5.
  **Parts moved elsewhere**: specific contrast techniques for sections → [reference.md](reference.md);
  hook design and climax/ending → `mc-arrangement-arch` §7 and §8;
  the list of anti-predictability checks → `mc-melody` §8.
- **Wu Zuqiang, *Musical Forms and Work Analysis***: the backbone of §6 on classical form devices.
- **Leonard, *On Musical Form***, and the **Central Conservatory of Music form examples collection**: sources of score examples.
- **Li Jiti, *Musical Forms and Work Analysis*** (Central Conservatory of Music distance-education series, sixteen lectures): Chinese traditional music's organizational logic differs fundamentally from the Western "recapitulation principle"; outline in [reference.md](reference.md) §5.
