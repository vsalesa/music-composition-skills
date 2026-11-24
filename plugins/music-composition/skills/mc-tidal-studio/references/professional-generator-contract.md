# Maestro and generator contract · proposed professional integration

The knowledge skill is only one side of quality. To improve generated music reliably, Tidal Studio must turn musical hypotheses into **candidate material, structural validation and playback comparisons**. This file distinguishes what exists from what needs code.

## Today: verified host contracts (November 2026)

- `server/assistant.py`: JSON `cambios.pistas` with `id,nombre,tipo,codigo`; `variantes` are listenable alternatives; `sugerencias` optional; `descargar` for audio samples; `plan`/`plan_paso` for multi-step actions; host system prompt and validators take precedence.
- `server/skills.py`: `mc-tidal-studio` is a designated pinned route when the main composition plugin is preferred. Usually up to 2 **unpinned** skills per response, total budget 24k characters and per-file 9k; only **one best reference** per loaded skill.
- `server/app.py`: courses pass a forced genre skill if named; session includes tracks, BPM, active course and additional instrument inventory/genre profile. Plugin auto-update support is now present; check configured state rather than saying "never updates".
- `web/courses.js`: traditional rhythm tracks and their steps are authored **statically**. `courseApply` copies the predefined patterns; Maestro helps explain and modify but does not independently regenerate each course step.
- `server/midigen.py`: deterministic MIDI-to-style conversion with a small `STYLES` template and lead rhythms, nearest chord-tone choices and fixed four-bar question/answer logic. Not the same as LLM Maestro generation.
- `server/data/style_profiles.json`: statistical chord/groove distributions from a small MIDI corpus; no full human performance model.
- `server/inventory.py`, `server/instlib.py`, `server/engines.py`: actual loaded samples, large sample instrument catalog, optional Mi-UGens/VSTPlugin/Surge XT, license-aware host asset workflows.
- `server/timeline.py`: Tidal `queryArc` event introspection exists; an integrated musical acceptance validator is **not** confirmed.

## Recommended target: a small explicit musical plan

In the **host implementation only**, create an internal `MusicalPlan` record (do not emit as an unsupported current Maestro key):

```yaml
style:
  branch: merengue-orquesta
  meter: 4/4
  bpm: 140
  count: quarter-note
  core_roles: [guira, tambora, electric-bass, piano, brass]
harmony:
  bars: [C, F, G7, C]
phrase:
  bars: 4
  motif_id: hook_A
  onset_grid: [0, 3, 6, 10]
  target_degrees: [3, 5, 7, 1]
  allowed_edit_roles: [melody, horns]
locked_track_ids: [d1, d2, d3, d4, d5]
quality:
  gates: [time, chord, role, motif, asset, playback]
```

**This YAML is illustrative and is not the current ARR-SPEC schema or host JSON.** The real host model should have stable versioned types and source-of-truth for track locking.

## Deterministic candidate pipeline (future host changes)

1. **Genre router** selects precise variant and obtains melodic/harmonic/rhythmic grammar from skills.
2. **State extraction** takes actual track code, arrangement masks, harmonic map, available sound IDs, locked tracks and user-approved motifs.
3. **Constrained generation** generates N candidate lead lines under meter/BPM/number-of-bars, chord destinations, compatible register, phrase architecture and named performance idiom. The model may propose, but validators must check.
4. **Renderer** emits Tidal code from typed note events instead of hallucinated arbitrary Haskell; no user track rewriting outside `allowed_edit_roles`.
5. **Validator** queries note events via `timeline.py` or symbolic note grid: bar alignment, chord target resolution, originality distance to previous alternatives, motif relationship, instrument availability, bass/kick collisions. These checks should be genre-aware and not ban expressive syncopation.
6. **Audition** produces listenable A/B in same context and loudness; user accepts a candidate or asks for a developed variant.
7. **State persistence** stores approved motif/progression/variant metadata for future steps. Avoid generating a disconnected solo at every lesson.

## Minimal implementation order

**P0:** add "Otra propuesta" only to melody/horn steps, keep fixed genre drums and BPM; pass explicit locked IDs/chord map to Maestro and disallow writes to protected tracks; persist accepted motif.

**P1:** replace fixed melody-generator note picking with rhythmic-motif and phrase-cadence constraints, candidate pool, genre-aware filter; write unit tests with existing `tests/test_midigen.py`.

**P2:** section-level arrangement/gear and planned timbral change; integrate available instrument inventory in selection with one sample A/B.

**P3:** formal runtime note-event and playback tests, real licensed phrase reference corpus, regression benchmarks on merengue, salsa, bachata, cumbia AND reggaeton baseline.

## Quality guarantees that must NOT be claimed

The skill does not implement `MusicalPlan`, locked-track enforcement, automatic A/B scoring, `SynthDef` downloads, license verification or audio-listening agents by itself. More textual knowledge alone will **not** make deterministic `midigen.py` generate complex new merengue motifs until the host algorithm is changed. A mandatory rerender/review loop can improve reliability, but subjective musical quality must still be judged through listening.