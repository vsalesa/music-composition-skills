---
name: mc-ai-tell-audit
description: The post-generation AI-tell audit (AI-tell diagnosis). Run this on every generated track before accepting it. Covers the fourteen enumerable defaults that generative music models fall into, which of them are machine-measurable and which need ears, why compliance rate and AI-tell count are two separate numbers that must never be merged, the zero-point calibration that sets the pass threshold at 82 rather than 60, the ordered diagnostic path from symptom to owning skill, and the remediation list. Use when a generation comes back and must be accepted or rejected, when a track sounds synthetic but you cannot say why, when deciding whether to accept a take, or when a high compliance rate still produced a bad result. AI sound, diagnosis, acceptance, sounds like AI but can't say why, compliance rate, post-generation check.
---

# AI-Tell Audit

**Every generated take must go through this skill. This is the final check of the library.**

> **Core proposition**: the AI sound is not mysticism.
> **Generative models fall back to default values when no spec is given, and those defaults can be enumerated.**
> This skill is that enumeration, plus "how to check each one and who owns it".

## Which sections to read for each task

| Task | Read |
|---|---|
| Just generated, need to accept | §2 the fourteen items → §3 judgment |
| "Sounds like AI but can't say where" | §2 (★ **check item by item, don't rely on intuition**) |
| High compliance rate but a bad result | §4 |
| Setting the threshold | §3.2 zero-point calibration |
| Problems found and need fixing | §5 remediation path |
| How to check the four vocal items | §6 |

## Boundary

| Not covered here | Covered by |
|---|---|
| Checking the spec **when it is finished being written** | The 20-item self-check table in `mc-workflow` §3.0 |
| How the compliance rate is calculated | This skill §3.1 (definition and calibration); how the three honors tiers affect scoring is in `mc-render-compile` §6 |
| Specifically how to fix things | Each L1/L2 skill (§5 gives the routing) |
| What to do about fields the backend cannot do | `mc-render-compile` §6, §7 |

> ★ **Division of labor with the 20-item self-check**:
> **The self-check asks "is the spec written?"; this skill asks "does the generated output sound like something a human made?"**
> **Both must be checked to be complete.** A spec that passes all 17 checks can still generate audio full of AI sound.

---

## 1. Required before starting

| Required | Question to ask |
|---|---|
| **① The spec and seed for this version** | Without a record it cannot be reproduced, **so the audit result is also useless** |
| **② The backend's honors table** | Which items it cannot do — **those are not counted against it** |
| **③ Whether stems are available** | The four vocal items (§6) need the vocal stem separated first |

---

## 2. ★ The fourteen enumerated items

**Tick each one. Don't go by overall impression.**

| # | Source of AI sound (backend default) | Spec field it counters | Automatically testable | Owned by |
|---|---|---|---|---|
| **1** | Sections are all multiples of 8 bars | `form[].bars` | ✅ Section boundary detection | `mc-arrangement-arch` §4 |
| **2** | **Energy curve rises monotonically, never falls** | `energy_curve`, `subtraction_events` | ✅ Per-section RMS | `mc-arrangement-arch` §2, §3 |
| **3** | Lineup stays the same from start to finish | `roster[].entry/exit` | ✅ Per-stem onset density | `mc-arrangement-arch` §5 |
| **4** | One harmonic loop runs through the whole song | The bridge must modulate or change key | ✅ Chord recognition | `mc-harmony`, `mc-modulation` |
| **5** | Fills mechanically land on multiples of 4 | `fill_policy` | ✅ Onset peak position | `mc-rhythm-section` §8 |
| **6** | No non-vocal memorable hook | `hooks.arrangement_hook` | ⚠️ Semi-automatic (repeated-section similarity) | `mc-arrangement-arch` §7 |
| **7** | **Dynamics squashed, spectral centroid constant** | `dynamics`, `width_map` | ✅ DR / LRA, temporal variance of the centroid | `mc-mix-intent` |
| **8** | **Gridded, no push/pull** | `groove.push_pull` | ✅ Onset offset relative to the grid | `mc-rhythm-section` §3 |
| **9** | Duration always 3:30, no tail | `target_duration` + ending treatment | ✅ | `mc-arrangement-arch` §8 |
| **10** | **Every phrase has the same dynamics and articulation, no breathiness, distortion, or rubato** | `vocal.delivery`, `dynamics_by_section` | ⚠️ Needs stems, then measure short-term loudness variance | `mc-vocal-direction` §2, §4 |
| **11** | **The chorus is sung identically all three times** | `vocal.chorus_variation` | ✅ Segment-level similarity of the vocal stem | `mc-vocal-direction` §1④ |
| **12** | **Breath points unnatural or breaths inaudible** | `vocal.breath_points` | ⚠️ Semi-automatic | `mc-vocal-direction` |
| **13** | **Ad-libs scattered evenly or absent entirely** | `vocal.ad_libs` | ⚠️ Semi-automatic | `mc-vocal-direction` |
| **14** | **Pitch perfect throughout** | `vocal.pitch_policy` | ⚠️ Semi-automatic (distribution of pitch deviation after stem separation) | `mc-vocal-direction` §4 |

> ★ **This table serves three purposes**: the skeleton of this skill, the skeleton of the A/B experiment judging sheet,
> and the source of the 20-item self-check. **Change one place, and sync all three.**

### 2.1 ★ The three easiest to miss and most fatal

**Not because they are the hardest to check, but because they are not hard to hear — they simply "don't sound human-made".**

| # | Why it is fatal |
|---|---|
| **2 (energy only rises)** | Measured: **62/62** real arrangements all have drops. **This is the strong rule with the highest hit rate**, and the one that sounds most like AI |
| **8 (everything aligned to the grid)** | Measured: **62/62**. Note the reading: "**not every instrument in the whole song may sit on the grid**" — absolute quantization of the drum kit is allowed (→ `mc-rhythm-section` §2.0) |
| **6 (no non-vocal memorable hook)** | Its symptom is "sounds fine but is forgettable", and it **most easily passes all other checks**. A song missing it is forgotten as soon as it ends |

---

## 3. Two numbers, never merged

### 3.1 Definitions

| | What it asks | How it is obtained | Range |
|---|---|---|---|
| **Compliance rate** | **How much the backend followed the spec** | Field-by-field comparison against the spec | 0–100 |
| **AI-tell flag count** | **How many machine fingerprints the finished product has** | Tick each item in §2 | 0–14 |

★ **Never combine them into one score.** They diagnose different illnesses:

```
High compliance + few flags  → Good, accept
High compliance + many flags → ★ The spec itself reads like AI (see §4)
Low compliance + few flags   → The backend did well on its own, but you can't reproduce it (see §4.2)
Low compliance + many flags  → Compilation or backend choice is the problem, go back to mc-render-compile
```

### 3.2 ★ Zero-point calibration: why the threshold is 82, not 60

**Unrelated, well-made finished tracks score 63–66 on the compliance scale.**

This is because any normal song will "happen to" satisfy some items (it has a tempo, sections, dynamics).
So:

| Line | Value |
|---|---|
| **Zero point** (unrelated finished product) | **63–66** |
| **Pass** | **70** |
| **Qualified** | **82** |

★ The three numbers above are **reference values**: the zero point was measured by taking one City Pop spec (112 BPM, 10 sections, 114 bars), comparing it against three unrelated, well-made Chinese-language finished tracks, and scoring by field weighting (63.4–66.4; the same spec against a plain MIDI-rendered demo scored only 39.5). They serve to convey the order of magnitude, not as a delivery gate; in field-by-field comparison, the compliance rate is one judgment formed after comparing.

★★ **A pitfall I hit**: moving weight from a **discriminating** item (`boundaries`) to a
**non-discriminating** item (`energy_shape`, which unrelated tracks also score 0.8 on)
**raised everyone's score**, including the zero-point baseline (66→72).
**Weight must be added to the items that can discriminate.**

### 3.3 Items the backend cannot do are not counted against it

Fields with `honors: none` are **excluded from scoring, not given a score of 0**.
See `mc-render-compile` §6.1 for details — **this is a correctness issue, not a matter of accounting convention**.

---

## 4. ★ High compliance rate but still sounds like AI

**This is the main reason this skill exists.**

The compliance rate only measures "did the backend follow the spec", **not "is the spec itself good"**.
If the spec reads like AI, the backend faithfully executes it, and the result is an AI song with a compliance rate of 95.

### 4.1 Four signs that the spec is AI-like

| Sign | Where to check |
|---|---|
| `intent.one_thing` was **filled in to pass a lint** and doesn't read as a human sentence | S0 in `mc-workflow` §1 |
| `reference_pair`'s `borrow` is very vague ("borrow its atmosphere") | Same as above. **"Borrow only the space of the intro" is what counts as written** |
| Each section's `bars` is an odd number **chosen only to avoid multiples of 8** | `mc-arrangement-arch` §4 — **asymmetry needs a reason** |
| The progression / key change used hits the **cliché warning line** with no reason given | `mc-progressions` §3, `mc-modulation` §6 |

★ **Common thread**: **rules were treated as conditions to satisfy, not choices to make.**
This is exactly the definition of the AI sound — **no one made a choice**.

### 4.2 Low compliance rate but good sound

**This shows the backend did well on its own. You can accept this product, but be aware that:**
- You **cannot reproduce** it
- You **don't know** which decision made it good
- The next track has to start from scratch and rely on luck

★ **How to handle it**: reverse-engineer this product field by field into a measured ARR-SPEC (fill it in while listening; mark anything you can't measure precisely as "estimated"),
and see where it differs from your original spec. **That difference is what you have learned.**

---

## 5. Remediation path

**Follow this order. Don't jump by intuition.**

```
Sounds "like AI"
 └─ ① Compare field by field against the spec, get the compliance rate
 └─ ② Go through the fourteen items in §2 one by one, count the flags
     ├─ Low compliance → check honors
     │   ├─ This field is none for this backend → not its fault. Switch backend (YuE2 has the strongest control) or accept
     │   └─ Not none → compilation issue → mc-render-compile §3
     └─ High compliance but many flags → ★ problem with the spec itself → §4.1
```

### 5.1 Symptom → skill (quick reference)

| Symptom | Check first |
|---|---|
| Flat, no rise and fall | `mc-arrangement-arch` §2 |
| Muddy, murky | `mc-texture-layering` §4 (★ **check sustained sounds first, don't blame the drums first**) |
| Lead isn't prominent | `mc-texture-layering` §3 four depth cues |
| Mechanical, too precise | `mc-rhythm-section` §2 + `mc-vocal-direction` §4 |
| Sounds fine but can't remember it | `mc-arrangement-arch` §7 (is `arrangement_hook` empty?) |
| Second chorus identical to the first | `mc-arrangement-arch` §6 + `mc-vocal-direction` §1④ |
| Vocal buried in the accompaniment | **Check pitch first** (`mc-vocal-direction` §4.1), then the frequency bands |
| Bass disappears on phones | `mc-sound-design` §6 difference tones |
| Abrupt ending / a fade-out that just stops | `mc-arrangement-arch` §8; ★ check whether `exclude` rules out `fade out ending` |
| Technically clean but the mood is wrong | `mc-mix-intent` §3.1 (was `mood` left unwritten?) |
| Harmony loops one cycle the whole way | `mc-harmony` §7, `mc-modulation` |

---

## 6. The four vocal items (#10, #12, #13, #14)

**All four require the vocal stem to be separated first.**

### 6.1 Stem separation

Use any stem separation tool to isolate the vocal stem (demucs-type, or the stem split that the generation platform itself provides, usually into vocals / bass / drums / other).
This skill does not presume which one.

> ★ **This is one of the few places in this library where stem separation is necessary**:
> multitrack corpora (Cambridge-MT) cannot provide "vocals sung by Suno", so they must be separated from the generated result.

### 6.2 What to measure after separation

| # | What to measure | Criterion |
|---|---|---|
| **10** Dynamics | **Short-term loudness variance** of the vocal stem | Variance near 0 = one dynamic level throughout |
| **11** Chorus similarity | **Segment-level similarity** of the vocal stem across chorus repetitions | Similarity too high = copied as-is |
| **12** Breaths | Low-energy segments between phrases | ⚠️ Semi-automatic, currently done by ear |
| **13** Ad-libs | Distribution of decorative vocalizations | ⚠️ Semi-automatic. **Evenly spaced = scattered, not sung** |
| **14** Pitch | **Distribution of pitch deviation** | ⚠️ Semi-automatic. **All within ±5 cents = over-corrected / generated** |

### 6.3 ⚠ Current status

**#12, #13 and #14 are checked by ear. This is a deliberate choice, not a missed step.**

These three measure energy valleys for breaths, the distribution of ornamentation, and the distribution of pitch deviation. Their automatic criteria would each need thresholds calibrated per generation model, since baselines differ widely between models, and forcing one universal number easily flags well-sung takes as problematic. Listening through these three by ear is quick anyway, and it is where the ear is naturally better than a machine, so it is not an extra burden.

---

## 7. Acceptance checklist

**Every generated result must pass through this.**

- [ ] Recorded the **spec version and seed**
- [ ] Compared field by field against the spec; the compliance rate is clear
- [ ] **Item by item** went through the fourteen items in §2 and **counted the flag number** (not by impression)
- [ ] Items with `honors: none` were **excluded from scoring**, not given 0
- [ ] If the compliance rate is high but flags are many, checked the four signs in §4.1
- [ ] The four vocal items were **listened to by a human at least once**
- [ ] ★ **The ear intervenes last**: A/B shuffled → paired comparison → **listen to the same pair twice to see whether the conclusion holds steady**
- [ ] If the two listens disagree → **the difference does not exist, don't change anything**

---

## Appendix: Sources

- Measured data (the 62/62 in §2.1, the 22% and 5/7 below): statistics over 62 naturally sampled tracks from Cambridge-MT multitracks; 5/7 is the ground truth from 7 tracks whose section boundaries were manually annotated
- Zero point 63–66: see §3.2
- All fourteen items in this skill can be judged by a human
- Among the fourteen, items 1–5, 7–9 and 11 can be computed by machine if audio analysis is available; **6, 10, 12, 13 and 14 are human-judged items**

> ★ **A methodological reminder** (a pitfall I hit):
> When a metric cannot measure something accurately, **don't use the metric to overturn the textbook; first ask whether the metric is measuring what you think it is.**
> Example: "a drop in energy should occur before the climax" holds for only 22% of the full set of 62 tracks, but for the ground truth of the 7 manually annotated tracks it holds for 5/7 —
> the gap comes from the algorithm locating the "climax" by energy peaks, which the human ear does not do.
> **The 22% figure does not measure this rule.**
