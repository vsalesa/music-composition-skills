---
name: mc-modulation
description: Modulation - moving between keys and making the seam sound intended rather than accidental. Closely related versus distant keys, the cushion chord and its announcement ladder from smoothest to most impactful, degree thinking, the three tools that keep a modulation feeling unified, what each interval distance expresses, a six-step decision flow including the return trip, and a warning about the one modulation generative models reach for by default. Use when a section needs to change key, when a key lift feels cheap or abrupt, when a modulation sounds accidental, when planning a bright-to-dark or dark-to-bright switch, or when returning to the home key. Keywords: modulation, key change, key lift, closely related keys, distant keys, parallel key, relative key, cushion chord.
---

# Modulation

**The whole difficulty of modulation lies not in "where to go" but in "whether the seam sounds intentional."**

The core of this skill is one concept, the **cushion chord**,
and one measuring scale: **how loudly it announces "I am modulating now."**

## Which sections to read by task

| Task | Read |
|---|---|
| Decide which key to go to | §2 closeness of relationship + §4 distance and character |
| The seam is abrupt | §3 cushion chord |
| Want the modulation to pass unnoticed | §3.2 the two lowest announcement levels |
| Want the modulation to hit with impact | §3.2 the top two levels |
| Got there and cannot get back | §5 step 6 |
| **Worried a key lift is too cheap** | ★ §6 |
| Choose a technique by scenario | §7 |
| Look up a specific technique (50 items) | [reference.md](reference.md) |

## Boundaries

| Not covered here | Where it goes |
|---|---|
| Out-of-key chords that do not modulate (secondary dominants, borrowed chords, ura-codes) | `mc-harmony` §6 — ★ **that is a temporary departure from the key, not a modulation** |
| Chord progressions themselves | `mc-progressions` |
| Where the modulation point sits in the form | `mc-modulation` §5 (step 1 of the six-step flow places it) and §6 |
| How the melody connects through a modulation | `mc-melody` §3 (preparing large leaps) + §6 (closing) |
| Score examples for the 50 techniques | [reference.md](reference.md) |

> ★ **Temporary departure vs. modulation**: inserting an E7 and returning to C is a
> **temporary departure from the key** (`mc-harmony`);
> inserting an E7 and then **staying in A major from there on** is a **modulation** (this skill).
> The criterion is "**whether it stays**," not "which chords were used."

---

## 1. Required before starting

| Required | Question |
|---|---|
| **① Target key** | Name the key and work out its **interval relationship** with the original key |
| **② Why modulate** | A lift? A switch between bright and dark? A switch of world? **"Because it's time to" is not a reason** |
| **③ Announcement strength** | Subtle or impactful? (choose one of the five levels in §3.2) |
| **④ Return** | Does it come back? How? **★ This is the item most often forgotten** |

---

### 1.1 Four purposes of modulation (Huang Huwei, pp. 0010–0013)

Expressing content and characterizing a figure; developing material (repeating the same passage in different keys is "saving material, achieving more with less effort"); color contrast;
★ **adapting to the range, register, and timbre of the voice or instrument.** This fourth purpose was not on this skill's checklist before, yet it is the most practical: if a singer cannot reach the notes, modulating is the answer, with no need to look for another reason.
A subordinate key is naturally unstable and demands a return to the home key; that is the driving force. **The return is best led by first modulating to the dominant of the home key, just as the dominant chord is best suited to lead to the tonic chord** (p0011).

## 2. Closely related and distant keys

There are 24 commonly used keys (12 major + 12 minor). Taking Key=C as an example, there are **six closely related keys**:

| Relationship | Example | Character |
|---|---|---|
| **Parallel key** (same tonic) | C ↔ Cm | Major and minor on the same tonic; the bright-dark contrast **can be pushed very hard** |
| **Relative key** | C ↔ Am | Same key signature, nearly all chords shared; **a light touch changes the mood** |
| **Dominant key** (rising perfect fifth) | C → G | Differs by only one scale note, many shared chords, **the smoothest** |
| **Relative key of the dominant** | C → Em | Same key signature as G |
| **Subdominant key** (falling perfect fifth) | C → F | Mirrors the dominant key, equally smooth |
| **Relative key of the subdominant** | C → Dm | Same key signature as F |

**Distant keys**: everything beyond the above. The mood changes drastically; used well, it can produce dramatic development.
**Semitone and tritone relationships both belong to distant keys.**

---

### 2.1 Quantitative three-level classification of relationships (Huang Huwei)

"Closely related" and "distant" can be counted (pp. 0013–0017). Distance is measured on the circle of fifths, on the nearer side:

| Relationship | Difference in key signature | Shared natural triads |
|---|---|---|
| Close | 1 | **4** |
| Farther | 2 | 2 |
| Distant | 3–6 | 0 |
| Farthest | 6 | 0 |

The number of shared triads is how much material the cushion chord (§3) has to choose from. A modulation with zero shared chords can only be smoothed by enharmonic equivalence or by a change of key (§4.1).

### 2.2 Modulation in pentatonic modes

In pentatonic modes there are only two routes for changing the gong system: the *bian gong* becomes the rising fifth of *jiao*, and *qing jiao* becomes the falling fifth of *gong*; two consecutive whole-step moves reach the target (Huang Huwei pp. 0041–0042, 0063–0064).
★ **Pentatonic modulation to a closely related key is melodically seamless.** The seven natural notes of one gong system can write a melody in the home key and in two closely related keys without any accidentals (pp. 0040–0041), so the sense of modulation rests entirely on harmony, and the harmony must make the new key's characteristic note appear (p0045). The system and the four variants on the same tonic are in `mc-melody` reference §3.0.

### 2.3 What does not count as modulation (preventing over-analysis)

When secondary dominants, extended dominants, related ii7, modal interchange, substitute dominants, or passing chords appear, they generally **cannot be analyzed as a modulation**; a chord that stays for only one bar is better explained by its degree in the original key (Chen Yunqiang, *Jazz Harmony*, p0257). This and the criterion in §5 ("whether it stays") are two sides of the same rule: **a chord that does not stay is not a modulation; it is a temporary departure from the key.**

### 2.4 Three modulation methods in songs (Kachulis)

**Parallel-key modulation** (changing the modal color on the same tonic, e.g. G mixolydian to G dorian, used to mark turns in the lyric's story); **relative-key modulation** (the pivot chord takes a different degree in the two keys: the expected chord is replaced by one from the other key, and the music then stays there); **exclamation modulation** (a direct jump to the new key after V). All three are cruder than Huang Huwei's system, but they are tied to lyrics: the modulation falls wherever the lyric's story turns. If there are lyrics, read where the turn happens from `meta.upstream.lyrics`; if not, place it at the section that `intent.emotional_arc` marks as the turn.

## 3. ★ Cushion chord: the core concept of this skill

### 3.1 What it is

**A transitional chord that makes a modulation sound smooth.**

> **The most common is the target key's V or V7**, placed in the last 1–2 beats before the modulation,
> **resolving across the barline as V7→I (dominant motion)**.

★ This V7 **is usually a non-diatonic chord in the original key** (III7, IV7, VI7, etc.) —
**and that is exactly the signal that the color is about to change.**

### 3.2 Announcement scale: how loudly it says "I am modulating now"

**From softest to loudest:**

| Level | Cushion chord | Effect |
|---|---|---|
| 1 | **V (triad)** | **Smoothest, lowest announcement** |
| 2 | **V7** | Contains a tritone, stronger push |
| 3 | **♭II7 (ura-code)** | Brings in foreign notes, **strongest announcement**, with a jazzy flavor |
| 4 | **dim / aug** (stand-ins for V7(♭9) / V7(♭13)) | Distinctive sonority, **greatest impact** |
| 5 | **IV(onV)-type slash chord** (e.g. F/G) | ★ **No third (leading tone) → sense of key blurred → "can fly to any key"** |

★ **Level 5 is a special case**: it is not "louder" but works in the **opposite direction**.
Levels 1–4 announce the modulation explicitly; level 5 makes it **hard to hear which key you started in**.
**If you want to modulate covertly, use it.**

### 3.3 Degree thinking

**Think of every chord as a Roman numeral degree: when the key changes, the degree stays the same.**
This is a conversion habit, not a conditional criterion, so there is only this one sentence. It is used repeatedly in §3.4 tool ① (transposing a whole progression unchanged), in §3.5 "how to choose common chords" (the same chord's degree converted between the two keys), and in §5 step 3 (calculating the target key's V7). See those places for how it is applied and what it costs.

### 3.4 Three tools for keeping a sense of unity

The biggest risk in modulation is that it "sounds like a different song." Three countermeasures:

1. **Transpose the whole progression unchanged** (the same progression moved, degrees completely unchanged)
2. **Run one cliché line through both keys** (chromatic stepwise motion in the bass, an inner voice, or the top voice)
3. ★ **Use a common tone as the top note**, letting the melody carry through the modulation

---

### 3.5 Nine approaches to the cushion chord (Huang Huwei)

§3 explains what a cushion chord is; this section covers the concrete ways of connecting one, ordered from nearest to most distant:

| Approach | Key point | Pages |
|---|---|---|
| **How to choose common chords** | When several adjacent chords are shared, **only the last one, the chord right next to the modulating chord, counts as the common chord**; its degree in the two keys is generally different, though its function may be the same | pp. 0033–0034 |
| **Characteristic note introduced early or delayed** | A common chord may already slip in a characteristic note of the new key (often entering as a passing tone), or defer it to be acknowledged later. ★ This is a real dial: **melody turns first and harmony confirms afterward** sounds completely different from **harmony turns first and melody follows** | pp. 0034–0035, 0049–0050 |
| **Semitone modulation** | If the new key is major, the common chord contains the new key's natural VI degree, which is lowered a semitone when entering the modulating chord; if the new key is minor, it contains the natural VII degree, which is raised a semitone to become the leading tone | pp. 0037–0039 |
| **Intermediate key** | Expand the shared triad into a temporary tonal center (adding its dominant function before and after), then turn to the new key. Distant keys are bridged in two hops with this technique | pp. 0057–0059 |
| **Augmented triad as common chord** | Twelve-tone equal temperament has only four augmented triads with distinct sonorities; any one of them, together with two equivalent chords, can resolve to all twelve keys. Shortcut: **pick an augmented triad that contains one or two chord tones of the new key's tonic triad** | See the augmented-triad chapter of Huang's book |
| **Dominant seventh and augmented sixth as equivalents** | The old key's dominant seventh serving as the new key's augmented sixth → a key a semitone lower; the old key's augmented sixth serving as the new key's dominant seventh → a key a semitone higher. Another route for semitone modulation up or down | pp. 0120–0121 |
| **Single-voice modulation** | Complete the modulation using only one sustained note or a single voice; the minimal transition at a section seam | pp. 0145–0153 |
| **Minor-third cycle** | Consecutive minor thirds in one direction modulate repeatedly, **returning to the original key on the fourth step**; a major-third cycle with a whole-step passing tone in the bass generates the whole-tone scale | pp. 0163–0164 |
| **Minor for major, major for minor** | The expected tonic chord has its third lowered or raised. It usually follows the previous key's dominant function directly; because that function link is too tight, it **generally does not constitute a modulation**, but the color contrast is vivid, making it a cheap false modulation | pp. 0167–0168 |

**Axis note** (p0061): the note that runs through both keys and is a skeletal tone of both keys' modes (e.g. the old key's dominant that is also the new key's subdominant). It is the actionable form of §3.4 tool 3, "use a common tone as the top note": first find the axis note, then hang the melody above it.

## 4. Distance determines character

| Direction | Character |
|---|---|
| **Rising semitone** | The standard key lift before the outro; lifts the mood. ★ See §6 |
| **Falling semitone** | The shock of a distant key, yet **requires no special technique** |
| **Rising whole step** | Surging; **passing through a dim chord makes it more tragic** |
| **Falling whole step** | A neighboring key; naturally produces a beautiful **sense of finale** and weight |
| **Rising minor third** | Major = splendid and grand; minor = a subtle change of color |
| **Falling minor third** | Major = bright yet settled; positive and fresh |
| **Parallel key** | Direct bright-dark switch (contrast), or gradual coloring |
| **Relative key** | **The smoothest bright-dark switch** |
| **Dominant / subdominant key** | Most shared chords, **the smoothest of all** |
| **Tritone** | **Farthest distance**; with a bridge built, **the most dramatic** |

---

### 4.1 Switching without a bridge: go direct

**Key switching** (tonal juxtaposition) uses no cushion: the two keys are placed directly against each other, relying only on color contrast (Huang Huwei pp. 0156–0164). Pairing rule: **a key switch between differing material goes between large structures at the section level; a key switch between identical material goes between small structures at the phrase, sub-phrase, or motif level.** Short structures keep the impression fresh, so the contrast stands out.
Color gradient: closely related keys are functionally strong but have weak contrast → third-related keys are the most colorful → a key-signature difference of 5 is "sudden yet novel" → a difference of 6 is "most sudden, most remote." The rising semitone at the end of §6 is the most overused cell of this key-switching gradient.

## 5. Six-step decision flow

1. **Set the target key and direction**: where to go (a key lift for the chorus? a bright-dark switch? the final climax?), and work out the interval relationship
2. **Consult the direction index** ([reference.md](reference.md) §1): find the techniques for this direction and pick by the desired **announcement strength**
3. **Calculate the target key's V7**: this is the all-purpose cushion. For more style, switch to a **ura-code**; for more impact, use a **dim/aug stand-in**; to modulate covertly, use the **IV(onV) slash chord**
4. **Choose a unifying strategy**: transpose the whole progression? run a cliché line through? keep a common tone on top? (pick one or combine)
5. **Place the landing**: put the cushion chord in the last 1–2 beats before the modulation, **resolving across the barline to the new key's I** (or to an entry such as IIm7 or IVm, a two-five entry)
6. ★ **Plan the return**: turn the new key's I into a dominant seventh (I→I7), or make it the IIm of the original key, using a secondary dominant or a two-five to come home

> **Step 6 is the one most often forgotten.** A modulation that goes out but cannot come back leaves the second half awkward,
> and the 20-item self-check cannot catch it — **this is a rule that can only be enforced by self-check.**

---

### 5.1 The four steps of a complete modulation, and the characteristic note

The six steps are a design procedure; these four steps are a **diagnosis** to run through one by one when a seam goes wrong (Huang Huwei pp. 0032–0036).

1. Establish the previous key
2. Common chords appear
3. A **modulating chord** appears
4. Affirm the new key (perfect authentic cadence)

Real works either take all four steps, or merge or drop some of them; the extreme case is the tonic chords of the two keys placed directly against each other (that is the key switch of §4.1).

★ **Characteristic note** (p0035): the modulating chord must contain a note **present only in the new key and absent from the previous key**, usually the one whose key signature differs (C to G adds F♯; C to F adds B♭). If the new key is harmonic major, look for the lowered VI degree; if harmonic minor, look for the raised VII degree. **It is the check for "did you actually modulate?": if the characteristic note never appears, listeners will not know you modulated.**

## 6. ★ Cliché warning line: the rising semitone in the final chorus

**This is the most heavily overused device in popular music, and the default move of generative models.**

Under prompts like "epic / emotional / final chorus," the back end **will with high probability raise a semitone for you on its own**.

**The criterion is the same as in `mc-progressions` §3**:

> **Did you choose it, or did it land on you by default?**

### 6.1 Four alternatives (each achieves "stronger for the last pass")

| Alternative | Why it works |
|---|---|
| **Falling whole step** | Gives a sense of finale and weight rather than a cheap lift. **Going the opposite way makes it heavier** |
| **Rising minor third** | Splendid and grand; more of an event than a semitone |
| **No modulation; change the lineup** | ★ **Most of the time this is the right answer**: a key lift is often a patch for arrangement work that was not done (→ `mc-arrangement-arch` §6) |
| **Same-tonic switch** | Major to minor or minor to major; the mood changes far more than with a rising semitone |

### 6.2 If you still want the rising semitone

**Do at least one of these two things**:
- Use the §3.2 level 4 (dim/aug) or level 5 (slash chord) **to change how the modulation is announced**; do not use the most obvious V7
- **Let the key lift coincide with a lineup event** (remove an instrument, or add a new one), so listeners remember the event rather than the semitone

★ **Self-check action**: write one sentence in `form[].note` in ARR-SPEC explaining why the modulation happens here.
**If you cannot write it, do not modulate.**

---

## 7. Scenario → technique

| Scenario | Recommended technique numbers (see [reference.md](reference.md)) |
|---|---|
| Whole chorus lifted a key (the standard approach before the outro) | 10, 15, 41 |
| The final climactic chorus (*ōsabi*) explodes once more | 15, 09, 21 |
| Verse → chorus opening up suddenly (dark → bright) | 05, 12, 17, 23, 36, 39 |
| Bright A/B section → a suddenly deep chorus (bright → dark) | 16, 30, 34, 40 |
| Finale feel / flamboyant ending in the outro | 02, 08, 24, 31, 33, 43 |
| Switch of world in an interlude or solo section | 27, 40 |
| Contrasting key for the intro and the A section | 30, 35, 45, 48 |
| Stylish jazz flavor | 20, 21, 49 |
| Gradual, unobtrusive shading from bright to dark | 36, 37 |
| Multi-key journey / flamboyant chorus progression | 44, 47, 50 |

---

## 8. Mapping to ARR-SPEC fields

| Field | Description |
|---|---|
| `meta.key` | **The original key**. A modulated key does not change this |
| `form[].harmony` | ★ Degrees in a modulated section are **counted in the new key**, and `note` states "this section: Key=X" |
| `form[].harmony_letters` | Letter notation naturally reflects the new key |
| `form[].note` | ★ **The reason for the modulation goes here** (the self-check action of §6) |
| lint #9 | "At least one section contains a non-diatonic chord **or a modulation marker**"; a modulation satisfies this |

---

## 9. Checklist before finishing

- [ ] Can state **why** to modulate here, not just "it's time"
- [ ] The cushion chord's **announcement strength** was chosen, not defaulted to V7
- [ ] Used at least one of the three unifying tools in §3.4
- [ ] ★ **Planned the return** (or explicitly decided not to return, and wrote that down)
- [ ] If it is a "final chorus rising semitone," passed the §6 cliché-line check
- [ ] Degree notation in a modulated section **is counted in the new key**, and `note` marks the new key
- [ ] The large leap at the modulation point is prepared (→ `mc-melody` §3.3)

---

## Appendix: Sources

- **Umegaki Luna, *Modulation Techniques 50*** — §1–§5, §7, and the 50 techniques.
- ⚠ **Huang Huwei, *Modulation Methods* (Zhuandiao fa)** —
  this is the Chinese-language treatise on modulation in the Chinese music-theory system.
  Expected difference: Huang's book starts from **common chords** (the classical route), while the Japanese book starts from **cushion chords / dominant motion** (the popular-music route).
- **Sposobin, *A Course in Harmony*** — the strict classical version of modulation.
- The directory index and type index for the 50 techniques are in [reference.md](reference.md).
