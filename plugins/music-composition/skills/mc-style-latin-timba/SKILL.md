---
name: mc-style-latin-timba
description: "Specific composition and arrangement for Cuban songo and timba. Use for songo, timba, timba-funk, contemporary Cuban funk crossover; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: timba, Latin, contemporary, fusion, composition, artist analysis."
---

# Cuban songo and timba

**Primary lineage:** Cuba. **Branches:** songo, timba, timba-funk, contemporary Cuban funk crossover.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Write two-bar clave-aware cycles and explicit gears (marchas): each planned gear alters the bass, piano, bell and kit parts at a coordinated cue. A straight repeated salsa loop does not become timba by adding fills. |
| Low end | Electric-bass tumbao can play anticipated notes, pedals and sharply articulated bloque figures. Describe kick–bass attack relationships; use interlocking only when attacks partly coincide. |
| Harmony | Short cyclic vamps allow strong ensemble development; funk harmony, parallel brass voicings and chromatic passing notes are choices, not defaults. |
| Form | Tema → coro/pregón → marcha A → bloque → marcha B → break → reprise/cierre. The section changes must be named in arrangement events. |
| Melody/hook | Compose short chant-like coro cells, rhythmic vocal pickups and sharply answered brass bloques. |
| Vocal roles | Lead/coro call-and-response; improvisatory lead exclamations must leave room for collective answers. |
| Essential lineup | Electric bass, drum kit, congas, timbales, campanas, piano/keyboards, trombones and trumpets, chorus; optional electric guitar. |
| Production/space | Drum kit and hand percussion must share a distinct rhythmic division of labor; gear changes should be audible even at constant BPM. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **Juan Formell and Los Van Van** — Songo's electric rhythm-section language. **Transfer:** Arrange bass, percussion and keyboards as one changing mechanism.
- **Changuito** — Songo kit independence and cross-rhythm. **Transfer:** Allocate bell, snare ghosts and kick roles rather than layering samples.
- **José Luis Cortés / NG La Banda** — Brass bloques and timba vocabulary. **Transfer:** Introduce a sharp horn block as a sectional turning point.
- **Alexander Abreu / Havana D'Primera** — Modern melodic brass-led timba. **Transfer:** Develop trumpet responses between vocal phrases.
- **Cimafunk** — Afro-Cuban rhythm meeting soul/funk. **Transfer:** Let funk timbre transform the song while preserving a selected Cuban rhythmic cell.

## Fusion routes
- **With funk:** Cuban cycle remains the main rhythmic identity; funk adds bass/guitar articulation.
- **With electronic:** Use an intentional change of gear and program sounds per-part rather than overlaying an EDM kick blindly.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-timba` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
- `meta.tempo` is a numeric quarter-note BPM; double-time counting must be recorded in an existing descriptive field, not invented schema keys.
- `arrangement.groove.feel` accepts `straight | swing16 | shuffle | halftime | 2:1 | 3:1`; `quantize_policy` is a part-to-percentage map; `push_pull` uses per-part values with evidence or an explicitly marked hypothesis.
- `arrangement.bass_kick_relation.mode` accepts `locked | interlocking | call-and-response`. Choose it from actual attacks, not genre stereotypes.
- Use valid `form[].name` enums, distinct roster entries/exits, `spectrum_budget` resolutions `yield | separate registers | alternate`, and an intentional subtraction event. Write sound changes in instrument `timbre` and existing notes, not made-up YAML fields.
- `form[].harmony` and `harmony_letters` must agree. Do not invent exact MIDI note placements from historical descriptions alone.

## Failure tests
- [ ] Can a listener distinguish this named branch without relying on the song title?
- [ ] Does every core instrument have a rhythmic/functional job rather than decorating a generic pop loop?
- [ ] Is there at least one distinct return/variation of the signature hook and one subtractive event?
- [ ] Does the proposed fusion declare which genre owns groove and low end at each relevant section?
- [ ] Are exact measured timing, recording personnel and artist-specific claims evidenced, not guessed?
- [ ] **Reject:** Generic salsa described as timba, no distinct gears, bass and kit changing independently at random.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
