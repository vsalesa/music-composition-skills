# Professional Latin composition in Tidal Studio · code and music audit (2026-11-24)

## Scope and what was verified

This document inspects Tidal Studio's current repository code, not private user sessions or rendered audio. No claim of actual subjective improvement is made without audio listening tests. Knowledge expansion is in `music-composition-skills`; no new Tidal Studio engine, course UI or MIDI generator features were added in this release.

### Existing architecture

- `web/courses.js`: courses teach genres through authored, fixed rhythm, bass, harmony, lead, arrangement and mix steps. The studio applies these directly; Maestro may explain and vary them on request.
- `server/midigen.py`: deterministic MIDI-based style adaptation. Each style owns a small rhythm-template bank, small bass pattern bank, accompaniment patterns and two lead rhythm options. `new_melody()` chooses near chord tones/scale steps to fill a four-bar question/answer structure. Designed for offline simplicity rather than expert arranging.
- `server/data/style_profiles.json`: sample-dependent measured MIDI statistics. The merengue profile explicitly describes 3 songs; confidence and genre representativeness must not be inferred from hundreds of bars within those three recordings.
- `server/assistant.py`: Maestro provides JSON changes and A/B variants and may propose sound downloads, while retaining a pedagogical chat role. System rules strongly emphasize beginners and Tidal syntax.
- `server/skills.py`: per-file `MAX_FILE=9000`, total `BUDGET=24000`, two unpinned skills plus pinned. `mc-tidal-studio` is a preferential pinned route and the course may force the genre-specific skill.
- `server/instlib.py`, `server/inventory.py`, `server/instcatalog.py`, `server/engines.py`: wide instrumental catalog, installed sample/synth inventory, downloadable multi-sample instruments and optional Mi-UGens, VSTPlugin and Surge XT engines.
- `server/timeline.py`: Tidal event query support; not the same as a proven genre-aware quality validator.

## Failure analysis, especially merengue

1. **Genre identity via sample names rather than articulation**: tambora head/rim and güira long/short scrape must be independently performed. A generic drum+hi-hat combo can be formally rhythmic and still not sound Dominican.
2. **Four-bar template rigidity**: a fixed 4-bar A/B/A′/cadence structure and near-chord-tone algorithm generates correct but bland contours; does not analyze hook memorability or singable phrasing.
3. **Rhythm-section mismatch**: piano, bass and percussion are designed as mostly independent pattern fragments. A professional arranger plans their rhythmic and harmonic interaction and changes together.
4. **Limited empirical coverage**: a measured profile of only three merengue songs can skew toward one orchestra/era/MIDI transcription. Avoid "X% of all merengue does this" assertions.
5. **Instrument sound gap**: even a good note list sounds toy-like if pitched accordion, horn articulations and Dominican percussion are unconvincing. Inventory and asset mapping need to be part of generation constraints.
6. **No full-song acceptance loop**: code execution is not music quality. Need motif return, section change, low-end separation, expressive performance and blind A/B listening.

The relatively positive results for reggaeton are consistent with its greater compatibility with synthetic low end, regular pattern programming and sparse loop-based hooks. This is an engineering hypothesis, not an objective comparative listening result.

## Independent professional references evaluated

| Resource | What transfers well to Studio | What does NOT transfer directly |
|---|---|---|
| sb-dev/music-production-skills | Compose/evaluate lifecycle, approved-decision state, failure attribution | Not a domain-authoritative Latin performance corpus |
| T-Rzeznik/reaper-composer | Genre template, motif development, foreground/response and DAW skill separation | Its Reaper/MCP code cannot be pasted into Tidal |
| tomascabralh/prod-skills | Groove microtiming discipline, note-level checks, self-review prompts, regression tests | Electronic drum grids are not universal merengue/salsa rhythms |
| auto-duan/supercollider-skill | Distinguish sclang/scsynth, SynthDef lifecycle, safe sound engineering | Expertise in synthesis does not confer authentic Dominican guitar/tambora style |
| SJY051/music-composition | Strong general voice-leading, rhythm, song form, music pedagogy | Generic Latin sections are insufficient for specialist perico ripiao or timba |
| Kevin Moore, Beyond Salsa Ensemble; Berklee Latin instruction | Interlocking Cuban rhythm sections, clave direction, timba gears, style-specific arrangement | Copyrighted methods/audio must be studied/attributed, not distributed as raw copies |

### Audio-domain credible reference sources

- Berklee's Latin writing/arranging pedagogy: https://college.berklee.edu/courses/cw-225
- Berklee on Juan Luis Guerra and Dominican instrument lineage: https://www.berklee.edu/berklee-today/summer-2005/juan-luis-guerra
- Kevin Moore, authorized free introductory sample: https://www.latinpulsemusic.com/files/album_pages/beyondsalsaensemble/BeyondSalsaEnsemble_Vol1_KevinMoore_Sample.pdf
- Cuban timba coordinated gear changes: https://www.timba.com/artist_pages/gears-what-where-and-how
- Smithsonian Folkways culture/instrument credits: https://folkways.si.edu/

The new skill references summarize production decisions in original writing and provide links for source study.

## Proposed host roadmap (NOT implemented by the skill)

### P0: audibly better courses with constrained new melody

Introduce **Otra propuesta** on melody/horn steps only. Rhythm instruments and explicitly approved harmonies are locked. Generate 3 candidate melodies per 4–8 bar phrase with an onset contour, chord targets, singable register, motif identity, response and different cadence. Present via existing `variantes`, listen on the same accompaniment and save chosen phrase for future steps. Add tests prohibiting changes to protected track IDs.

### P1: replace melody template engine

In `server/midigen.py`, separate: `RhythmGrammar`, `HarmonyTimeline`, `MotifModel`, `CandidateGenerator`, `PhraseEvaluator`, `ArticulationRenderer`. Rather than random nearest-chord-tone selection, produce intentional pitch/duration/phrase variants and preserve motif across 8/16 bars. A/B against existing `new_melody()` while holding sound constant.

### P2: ensemble interaction and acoustic articulation

Model synchronized bass/tambora/piano and two-bar clave where relevant. Provide role-specific attack maps, instrument phrase envelopes and planned breakdown/gear change. Map Latin acoustic percussion to proper stroke families; verify sample/instrument ID from active library. Do not equate adding an optional synth engine with realistic accordion/tambora playback.

### P3: score and regression

Add structural validators for bar count, harmonic targets, instrument range, locked-role changes, motif relationship and intended rhythmic grammar (but never naively demand a melody hit coincide with each drum hit). Render two versions at the same loudness; A/B listen. Use a legal source set of several *varied* songs per genre with variant, era and annotation provenance. Evaluate merengue **and** regression performance on reggaeton and other genres.

## Practical acceptance fixture

Brief: **"Merengue orquesta 140 BPM in C major, fixed güira/tambora, original 4-bar lead + 4-bar altered return, piano/bass I–IV–V7–I, two different brass responses"**. Require: protected drums untouched; harmonic resolutions correct; no absent sample IDs; call/response with empty spaces; variants musically distinct; trumpet/sax not permanent doubling; audible instrument articulation judged by listener.

Report errors by root cause: **genre knowledge / melody algorithm / timing / sample/instrument mapping / renderer / mixing / performance**. Don't tune five subsystems simultaneously; compare to a controlled baseline.

## Boundary and licensing

This audit and the skill provide educational/production knowledge, not rights to reuse protected compositions, vocal recordings, purchased MIDI or instrument multisamples. No runtime analysis of mp3/audio was performed during this audit; conclusions follow inspected source code and cited public training references.
