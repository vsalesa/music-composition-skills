---
name: mc-style-latin-regional-mexicano
description: "Specific composition and arrangement for Regional mexicano: ranchera, mariachi, norteño, banda and sierreño. Use for ranchera, mariachi, huapango, norteño, banda sinaloense, sierreño, norteño sax, grupero; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: regional-mexicano, Latin, contemporary, fusion, composition, artist analysis."
---

# Regional mexicano: ranchera, mariachi, norteño, banda and sierreño

**Primary lineage:** Mexico and Mexican diaspora. **Branches:** ranchera, mariachi, huapango, norteño, banda sinaloense, sierreño, norteño sax, grupero.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Differentiate 3/4 ranchera, 6/8 huapango, polka-like norteño and banda marches; no universal 'Mexican beat'. Identify meter and 6/8 vs 3/4 hemiola before writing. |
| Low end | Guitarrón has a resonant plucked pulse; tuba can carry banda's bass motif; electric bass fits grupero and some norteño. Don't apply 808 unless the substyle actually needs it. |
| Harmony | Tonal dominant/tonic motion, secondary dominants and vocal cadence; rich mariachi violins/trumpets can add dramatic tension without jazz stacking. |
| Form | Strophic ranchera/corrido narrative; pop regional forms can use choruses but need a defined instrumental intro and response lines. |
| Melody/hook | Vocal storytelling/long-held cadences; mariachi trumpet/violin responses, accordion riffs or requinto hooks based on ensemble. |
| Vocal roles | Project lyric narrative and consonant articulation, with regional ornaments and deliberate register changes; avoid generic opera-like projection. |
| Essential lineup | Mariachi: violins, trumpets, vihuela, guitarrón and guitars. Norteño: accordion/bajo sexto/bass/drums. Banda: brass/clarinets/tuba and percussion. Sierreño: requinto/guitar and bass. |
| Production/space | Preserve ensemble differentiation: tuba/accordion/strings are not interchangeable MIDI placeholders. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **José Alfredo Jiménez** — Ranchera songcraft with memorable narrative refrains. **Transfer:** Write a strophic emotional turn and powerful cadence.
- **Vicente Fernández** — Vocal dramatic and mariachi tradition. **Transfer:** Reserve space for long held phrases and trumpet/violin responses.
- **Los Tigres del Norte** — Narrative norteño/corrido storytelling. **Transfer:** Keep accordion and bajo sexto supporting plot.
- **Banda El Recodo** — Banda sinaloense orchestral identity. **Transfer:** Write a tuba/bass foundation with brass and clarinet roles.
- **Christian Nodal** — Mariacheño/pop regional stylistic combination. **Transfer:** Combine mariachi color with contemporary vocal intimacy.
- **Carín León** — Regional songwriting crossed with soul/pop. **Transfer:** Keep regional instrument ownership while varying vocal timbre.

## Fusion routes
- **With pop:** Borrow compact verse/chorus without erasing instrumental tradition.
- **With trap:** Hand rhythmic/low-end ownership to trap only in a named crossover; use corridos-tumbados skill if corrido is central.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-regional-mexicano` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Inventing one regional-Mexican drum kit, using tuba and guitarrón redundantly, assuming all regional music is 4/4.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
