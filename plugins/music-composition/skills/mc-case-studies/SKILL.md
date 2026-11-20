---
name: mc-case-studies
description: The corpus layer - how real recordings are made to testify for or against the textbook rules. Covers the reverse ARR-SPEC as the unit of the corpus, the corroboration table that turns rules times corpus into hit rates and tiers them as strong rule / tendency / not a rule, the two honesty constraints that keep the table from being circular, why naturally sampled corpora beat curated ones, what this corpus can and cannot measure, and how to look up a worked example. Use when checking whether a rule actually holds in real music, when adding a rule, when a rule and the data disagree, when annotating a track, or when you need a real-world example of a technique. Keywords - corpus, corroboration, hit rate, measured ARR-SPEC, reverse spec, case breakdown, rule validation.
---

# Corpus Layer (Case Studies & Corroboration)

**This layer answers one question:**

> **The textbooks say so, but do real works actually do it?**

The rules in this library were not simply copied. **They were copied, then checked against 62 real multitracks.**
The results of that check fall into three tiers, and **only strong rules go into the 20-item self-check table**.

## Which sections to read for which task

| Task | Read |
|---|---|
| Want to know how reliable a rule is | §4 corroboration table |
| Adding a new rule | §4.3 process |
| A rule and the data disagree | ★ §5 |
| Looking for a real example | §6 |
| Annotating a track | §3.3 |
| Want to know what this corpus can measure | §2.2 |

## Boundaries

| Not handled here | Goes to |
|---|---|
| The content of the rules themselves | The L1/L2 skills |
| Acceptance of generated output | `mc-ai-tell-audit` |
| Checking a finished spec | `mc-workflow` §3.0 |
| The vocabulary of a particular style | `mc-style-*` (L3) |
| Section-by-section breakdown of specific pieces | [reference.md](reference.md) |

---

## 1. Three principles of the corpus

### 1.1 ★ Store only structure and parameters, not works

> **A corpus entry contains no audio, no score, no lyrics, only measured numeric values.**

This is both a copyright necessity and methodologically correct:
**what we want is "the parameter distribution of real works", not the works themselves.**

### 1.2 ★ Natural sampling beats curation

**The corpus is not hand-picked; it uses natural sampling.**

> **Curation skews the corpus toward the side where "the rule holds"**:
> what you pick are what you consider good examples, and what you consider good examples are the ones that fit your existing theory.
>
> **Natural sampling supplies counterexamples automatically.**

So what is finally used is **the 60+ naturally sampled songs of Cambridge-MT**, with no filtering.
This also removes the need to look for a separate MIDI/stem corpus (whose only original use was calibrating the stem-separation tool,
and real stems eliminate that need directly).

### 1.3 The unit of the corpus is the "reverse ARR-SPEC"

**Not an audio file, but an ARR-SPEC measured by working backwards from the audio.**
This unit was chosen because it **uses the same fields as our output**: structure, lineup entries and exits, and the energy curve are all recorded in the same places,
so the corroboration table can line corpus entries up with rule criteria directly, without first converting formats.
What the fields look like, and which markers are honest blanks rather than omissions, are covered in §2.1.

---

## 2. The reverse ARR-SPEC

### 2.1 What it looks like

The library's measured corpus is **63 entries** (60 Cambridge-MT multitrack songs + 3 finished Chinese-language pop songs). Each one states its nature in its header:

```yaml
# Measured ARR-SPEC (corpus entry) — generated automatically by working backwards from audio
# ★ Stores only structure and parameters, not scores or lyrics. TODO items such as intent / hooks need to be filled in by a person.
```

★ **Note the `# TODO` and `# estimate, not measured` comments**:
they are **honest labelling**, not unfinished work.
Things like `intent.one_thing` **cannot be measured by a machine**, and filling them in anyway would be fabrication.

### 2.2 ★ What this corpus can and cannot measure

**Cambridge-MT is raw, unmixed multitrack, not finished masters.** So:

| Can measure | Cannot measure |
|---|---|
| Section boundaries, bar counts | **DR / loudness** (unmixed) |
| Tempo | **Stereo width** (unmixed) |
| Energy curve, subtraction events | **Absolute spectral centroid** (unmixed + unmastered) |
| Lineup entries and exits (real stems!) | Production feel |
| Onset offset relative to the grid | |
| Chords (chroma matching) | |

★ **Rules that cannot be measured must be flagged, not run regardless.**
In the rule table, such rules are marked `evidence: unusable_here`,
and the statistics **skip them rather than produce a fake number**.

**This library's corpus is multitrack stems and contains no finished mixes, so these rules currently have no numbers.**

---

## 3. Ground truth and annotation

### 3.1 Why human ground truth is needed

The section boundaries measured by the algorithm are **themselves of doubtful reliability** (marked `no_truth` in the rule table).
Without an independent ground truth, there is no way to tell whether an anomalous hit rate means the rule fails or the algorithm itself measured wrongly.
The case in §5.2 where "a hard-coded threshold pushed the hit rate down to 16%" was overturned only thanks to human ground truth.
So a batch of human annotations was made to serve as ground truth; calibration results are in §3.2.

### 3.2 ★ A worry that was put to the test

The user worried that "I'm not an expert, so the boundaries I mark won't be accurate." **The measured result overturned that worry:**

> **The median deviation between human marks and the algorithm = 0.0 seconds.**

★ **Conclusion**: **Section boundaries are a perceptual judgement, not a judgement of taste.**
Boundaries marked by a non-expert agree with the algorithm, which shows this never needed an expert.
(**Separate what can be annotated from what cannot**: boundaries can be annotated; "does this section sound good" cannot.)

**Calibration result**: 7 songs annotated by hand, the algorithm hits **72%**, median deviation **0.0 s**.

### 3.3 How to annotate

In any software that shows the waveform and can play it, listen and note down **the time in seconds of each section start**; the section name is optional, and it is mainly the time points that get used.
**Mark only the boundaries you can actually hear, and leave out any you are unsure of**, because these are to be used as ground truth, and a wrong mark is worse than none. Annotating 5 songs is enough to be usable.

**The 7 songs already annotated in this library** (Cambridge-MT):
AMContra_HeartPeripheral, APZX_CyberMower, DigitalHumans_Electrvm,
Forkupines_Semantics, MERCMusic_Knockout, MR1103_Flags, SimonLyn_Copper

---

## 4. ★ The corroboration table: rule × corpus → hit rate → tier

### 4.1 Two honesty constraints

**If they are violated, the corroboration table is self-deception:**

| # | Constraint |
|---|---|
| **1** | ★ **The criterion must not reuse the generator's definition.** `subtraction_events` in the reverse ARR-SPEC is filled in automatically during reverse derivation as "drops by more than 1 dB from the previous section"; using it to test "do real arrangements have subtraction" is **circular reasoning**. So every criterion involving subtraction is **recomputed directly from `energy_curve`**, with a threshold that has musical meaning (≥3 dB), and **does not read the `subtraction_events` field** |
| **2** | ★ **Rules the corpus cannot measure must be flagged, not run regardless** (see §2.2) |

The three values of `evidence`:

| Value | Meaning |
|---|---|
| `ok` | This corpus can verify it |
| `unusable_here` | This corpus is of the wrong kind; a finished-mix corpus is needed |
| `no_truth` | Lacks ground truth (e.g. section boundaries), so the criterion itself is of doubtful reliability |

### 4.2 First-round results

| Rule | Hits | Tier |
|---|---|---|
| The energy curve must have a drop | **62/62** | **Strong rule** |
| The lineup must have instruments entering mid-song | **59/59** | **Strong rule** |
| At least one instrument leaves early | **59/59** | **Strong rule** |
| Not all parts should be strictly aligned to the grid | **62/62** | **Strong rule** |
| The opening should not lay in all instruments at once | **54/59** | **Strong rule** |
| At least one clear subtraction in the whole song | 36/62 = **70%** | **Tendency** |
| There should be an energy fall before the climax | Full set 22% / human ground truth 5/7 | ★ **Contradictory, treat as a technique only** |
| The lineup is densest at the climax | 25/59 = 42% | **Suspended** |

### 4.3 What each tier decides

| Tier | How it is written in a skill | Enters lint? |
|---|---|---|
| **Strong rule** | "must" | ✅ hard check |
| **Tendency** | "should usually" | ❌, goes into the "must pass after writing" checklist |
| **Technique** | "you can do it this way" | ❌, appears only in the diagnostic path |
| **Suspended** | **not written into a skill** | ❌, only listed in the corroboration table, waiting for more data |

### 4.4 Process for adding a rule

1. Write the rule as one item: rule + **a runnable criterion** + `evidence`
2. Check whether it violates the two constraints in §4.1
3. Run the criterion over the corpus song by song (natural sampling, §1.2) and count the hits
4. Assign a tier by hit rate (§4.3)
5. ★ **Record the result first** (which corpus, what criterion, how many hits, which tier), and only then change the spec or the rule

> **The rule set is versioned.**
> If the rule set is changed it must be re-run, otherwise one round cannot be compared with the next.

---

## 5. ★ What to do when a rule and the data disagree

**This is the most important section of this skill.**

### 5.1 First ask: does the metric measure that thing

**Do not use a metric to overturn a textbook.**

**Example**: "There should be an energy fall before the climax" is only **22%** across all 62 songs,
but **5/7** in the 7 human-annotated ground-truth songs.

**Source of the gap**: the algorithm locates "the climax" by **energy peak**, whereas **the human ear does not**.
So that 22% figure **is not measuring this rule**; it measures "is there a fall before the energy peak".

★ **Conclusion**: this one is neither demoted to a false rule nor promoted to a strong rule; **it is listed as a technique**.

### 5.2 Another example: a false low hit rate caused by a hard-coded threshold

During corroboration the criterion was once **hard-coded as "12 dB dynamic range"**,
which pushed the hit rate of rule ARR-R-012 down to **16%** and nearly got reported as "the textbook is wrong".

**How it was disproved**: test on the 7 human-annotated ground-truth songs → **5/7 = 71%**.
**The fix**: score on the normalised 0–10 units instead, **without pretending to recover dB**.

★ **General lesson**: **an anomalously low hit rate: suspect the criterion first, then the rule.**

### 5.3 The corroboration table and lint do not ask the same question

| | What it asks |
|---|---|
| **Corroboration table** | **Do humans generally do this** |
| **The 20-item self-check** | **If you don't do this, will it sound like AI** |

★ **So a 70% hit rate does not mechanically demote a lint check.**
Something may be done by only 70% of people, but **the 30% who don't do it may all happen to sound like machines**.

---

## 6. Finding a real example

| You want | Go to |
|---|---|
| A real use case of a technique | The section-by-section breakdowns in [reference.md](reference.md) |
| Which songs use a given chord progression | `mc-progressions` [reference.md](../mc-progressions/reference.md) §7 index of famous pieces |
| Measured parameters by style (medians) | [reference.md](reference.md) §1.2 |
| Score examples of orchestration / blended timbre | `mc-orchestration` [reference.md](../mc-orchestration/reference.md) §4 |
| Score examples of counterpoint | `mc-counterpoint` [reference.md](../mc-counterpoint/reference.md) |

### 6.1 Format of a section-by-section breakdown

**Four-way alignment**: timecode / section / lineup event / harmony.
The format matches the reverse ARR-SPEC, with a person filling in the parts a machine cannot measure (intent, hooks, why it works).

---

## 7. Interfaces with other layers

| Direction | Content |
|---|---|
| **→ L1/L2 skills** | Provides evidence-level labels such as "measured: 62/62, strong rule" |
| **→ the 20-item self-check** | Only a **strong rule** may enter the self-check table |
| **→ `mc-ai-tell-audit`** | The zero-point calibration (unrelated finished songs scoring 63–66) was measured on this corpus |
| **← finished-mix corpus** (★ **missing**) | The `unusable_here` rules in §2.2 need it |

---

## 8. Must pass after use

- [ ] When citing a rule, **the evidence level was included** (strong rule / tendency / technique), not just "the textbook says so"
- [ ] Newly added criteria **do not reuse the generator's definition** (§4.1 constraint 1)
- [ ] Rules the corpus cannot measure **are marked `unusable_here`** and were not run to produce fake numbers
- [ ] When a hit rate was anomalously low, **the criterion was suspected first** (§5.2)
- [ ] The corroboration table's hit rates were not used to **mechanically** demote a lint check (§5.3)
- [ ] If the rule set was changed, it was **re-run and this round's results were recorded**

---

## Appendix: current state

**The numbers in this skill rest on**:
- **63** measured ARR-SPECs (60 Cambridge-MT multitrack songs + 3 finished Chinese-language pop songs)
- A versioned rule set (first-round corroboration table in §4.2)
- Ground truth for the section boundaries of **7** human-annotated songs (§3)
- Tempo calibration: **56 songs of ground truth**
