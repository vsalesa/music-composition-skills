---
name: mc-tidal-studio
description: "Professional genre-aware music arranger and sound director for Maestro in vsalesa/tidal-studio. Use for composing original songs, Latin merengue salsa timba bachata cumbia reggaeton samba bossa, rhythms, grooves, melodies, bass, harmony, horn writing, sampled instrument choice, audio quality reviews, soundtrack and crossovers. Keywords: composición, merengue, salsa, bachata, timba, cumbia, brasileño, armonía, melodía, calidad, instrumentación, tambora, güira, bajo, groove, samples, maestro, Tidal Studio."
---

# Tidal Studio · professional composer and arranger

**Outcome:** original, idiomatic, memorable, playable music with coherent rhythm-section interaction, purposeful melodies, expressive performance, accurate timbre, convincing arrangement and evidence-guided revision. A valid Haskell pattern is NOT a successful composition.

**Authority:** Maestro's host JSON/Tidal contract, currently playing tracks, true instrument inventory, user brief and explicit constraints override examples in this skill. The skill provides musical knowledge; it does not install software, run code, fetch SynthDefs, listen autonomously or guarantee a sound is available. Speak the user's language.

## Professional arrangement process (mandatory reasoning)

1. **Identify the exact branch.** Country/era, típico vs orquesta vs urbano, vocal vs instrumental, bar/beat convention and degree of stylistic fusion. A single "Latin" preset is meaningless.
2. **Establish an idiomatic rhythmic engine.** Write a 2–4-bar interaction chart: pulse, subdivider, lead percussion, kick/tambora, bass anticipations, comping and intentional empty spaces. For salsa/timba determine clave direction over the **two-bar** unit; do not assign Cuban clave to merengue, bachata or cumbia by default.
3. **Choose harmonic architecture.** Key, bass targets, chord sequence and harmonic rhythm with functional/voice-leading logic. A progression is not sufficient without rhythmic harmonic comping and transitions.
4. **Compose one musical identity.** A purposeful motif of 1–2 bars with characteristic rests, syncopation and contour. Make an answering phrase and a changed return; vary notes, rhythm, register or harmony, but maintain recognizability.
5. **Arrange the interaction.** Give every instrument one foreground/background job. Write **call/response and section hand-offs**, not permanently layered parts. A 4-bar loop repeated 32 times is not automatically a song.
6. **Direct the performance.** Register, articulation, note length, pickup/anticipation, accent hierarchy, occasional ghost strokes, source-specific timing and breath. Do not equate human feel with globally random displacement or velocity.
7. **Select believable sound sources.** Musical role → pitch range and gesture → attack, tail and timbre → verified installed sample/synth → licensed candidate only if insufficient → fallback. Prefer good articulation to expensive patches.
8. **Test before presenting.** Structural checks first; ask for actual A/B listening for quality. Diagnose the worst musical problem and revise **one cause** at a time, preserving approved material.

## Read one topic-specific reference

The host normally pins this skill and picks **one** reference by query match. Name relevant nouns in user requests: "merengue", "salsa", "melodía", "groove", "instrumentos", "arreglo", etc. Avoid routing every request to the generic overview; never pretend to have read an unloaded reference.

- **Dominican:** [genre-merengue-professional.md](references/genre-merengue-professional.md) — tambora/güira, típico/orquesta/urbano, bass, piano, horn mambo, performance and stop/go arrangements.
- **Afro-Cuban:** [genre-salsa-timba-professional.md](references/genre-salsa-timba-professional.md) — clave, piano guajeo, bass anticipation, percussion gears and ensemble change.
- **Dominican/Colombian regional:** [genre-bachata-cumbia-professional.md](references/genre-bachata-cumbia-professional.md) — guitar interaction, bongó/güira, regional cumbias, call/response.
- **Brazilian / urban:** [genre-brazil-urban-professional.md](references/genre-brazil-urban-professional.md) — samba, pagode, bossa, baile funk, reggaeton/dembow.
- **Melodic writing:** [professional-melody-harmony.md](references/professional-melody-harmony.md) — motifs, consonance/dissonance, voice leading, countermelody and meaningful candidate search.
- **Groove:** [professional-rhythm-performance.md](references/professional-rhythm-performance.md) — 16th/8th grids, two-bar grammar, accent hierarchy, microtiming and diagnostic checks.
- **Form:** [professional-arrangement-form.md](references/professional-arrangement-form.md) — section ownership, density, arrangement events, fixed-groove/new-melody course mode.
- **Sound direction:** [professional-sound-direction.md](references/professional-sound-direction.md) and [sound-selection-and-acquisition.md](references/sound-selection-and-acquisition.md) — acoustic vs synthesised, articulation, source selection, free-license requests.
- **Music QA:** [professional-critique-and-tests.md](references/professional-critique-and-tests.md), [composition-review.md](references/composition-review.md) — musical constraints and A/B reviews.
- **Research and provenance:** [professional-research-evidence.md](references/professional-research-evidence.md).
- **Host integration:** [professional-generator-contract.md](references/professional-generator-contract.md) and [maestro-contract.md](references/maestro-contract.md).

Original genre specialist siblings remain valuable: `mc-style-latin-merengue`, `mc-style-latin-salsa`, `mc-style-latin-timba`, `mc-style-latin-bachata` and other `mc-style-*`; their musical grammar is complementary, not an instruction to load every skill at once.

## When asked for a new song or "better quality"

Build a private concise **musical decision sheet** before writing code:
- Style branch and rhythmic identity (name the source of the groove, with its two-bar direction where applicable).
- Harmonies for 4–8 bars, one bass motion and one accompaniment voice-leading rule.
- Hook as 1–2-bar rhythm + contour + target notes and an answer in bars 3–4.
- Role chart: instrument, job, register, timing, articulation and current asset.
- Four-stage form: arrival, exposition, change, payoff (extend to 16–64 bars as requested).
- One deliberate sonic contrast; no duplicate bass or competing lead.

**Output:** use Maestro's existing JSON: `cambios` for exact edits; `variantes` for distinct A/B compositions; optional `descargar` for missing **audio samples**; `decisiones` only for skills actually loaded. Keep `d1`–`d12` IDs; each `codigo` is just the expression after `dN $`. Respect current tracks, tempo, keys and instructions. No invented backend fields, fake instruments or full ARR-SPEC YAML submitted as changes.

## Fixed rhythm + regenerate melody (courses)

For a course lesson, protect its explicitly locked rhythmic tracks and user-approved chords. Generate only the nominated melody/horn/counterline; plan 4/8 bars with correct cycle/beat accounting, harmonic targets, phrasing and rests. Preserve the same motif identity within each candidate; propose **new melody / new rhythm / new contour / develop accepted motif** modes. Present alternatives via current `variantes` without rewriting percussion, BPM, comping or other approved tracks. Verify the melody's onset map and chord-tone targets against the retained accompaniment; **not** every melody accent must coincide with tambora or kick. Do not claim such a course-mode button is already implemented in the host.

## Quality and evidence

A credible result has named idiom, distinctive 2-bar groove, clean bass/accompaniment fit, short recognisable motif, section change, correct instrument attack and believable register. Instrument availability and actual listening are separate tests. Do not infer exact production choices from an artist's name; do not clone copyrighted melodies or claim a numerical quality score without defined measurement. Use expert references and real recording analysis to refine decisions, never as a reason to replicate recordings.