---
name: mc-style-latin-corridos-tumbados
description: "Specific composition and arrangement for Corridos tumbados and sierreño urbano. Use for corrido tumbado acústico, sierreño urbano, trap corrido, regional pop crossover; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: corridos-tumbados, Latin, contemporary, fusion, composition, artist analysis."
---

# Corridos tumbados and sierreño urbano

**Primary lineage:** Mexico / Mexico-US youth scenes. **Branches:** corrido tumbado acústico, sierreño urbano, trap corrido, regional pop crossover.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | The corrido/sierreño guitar pulse need not become a trap beat. Decide if rhythmic guitar drives the song and hip-hop owns vocal flow, or if a programmed kick and 808 take over sections. |
| Low end | Tololoche, bass or electric bass can supply a moving root line; if 808 enters, control overlapping low notes and specify its role as color or ownership. |
| Harmony | Short tonal/minor loops, characteristic repeated guitar turnarounds and rhythmic substitutions. A clear harmonic turn may be more effective than complex extensions. |
| Form | Signature requinto intro -> narrative verses -> recurring chorus/hook -> guitar instrumental answer -> final hook; variable phrase lengths should follow text, not a mandatory 8-bar square. |
| Melody/hook | Create a recognizable picked requinto phrase, and a lead line near spoken conversational contour with distinctive leap or cadence. |
| Vocal roles | Close, speech-like/nasal textures and rap-adjacent timing are choices to analyze, not instructions to clone any living voice. |
| Essential lineup | Requinto/12-string or six-string guitar, rhythmic guitar, bass/tololoche/electric bass, optional tuba, and optional trap drums. |
| Production/space | Record/accent picked guitar transients; use sparse beat layering and preserve intelligibility of sung narrative. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **Natanael Cano** — Pioneering identification of corridos tumbados as a modern strand. **Transfer:** Pair corrido/sierreño strings with young urban cadence.
- **Junior H** — Melancholic and melodic tumbado language. **Transfer:** Use reflective guitar and restrained rhythm.
- **Peso Pluma** — Global pop prominence of contemporary regional/tumbado crossover. **Transfer:** Make the picked guitar riff a primary hook.
- **Fuerza Regida** — Ensemble-led and urban regional crossover. **Transfer:** Plan gang response and rhythmic breaks.
- **Eslabón Armado** — Romantic sierreño melodic writing. **Transfer:** Let guitar arpeggios and vocal melody carry emotion.

## Fusion routes
- **With trap:** Use hip-hop for vocal rhythm or selectively 808, while the requinto retains the central memory hook.
- **With reggaeton:** Alternate the drum owner across sections; preserve the corrido guitar riff across the transition.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-corridos-tumbados` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Using a trap beat with no regional instrument role; presenting criminal narrative as a genre requirement; duplicating famous riff/voice.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
