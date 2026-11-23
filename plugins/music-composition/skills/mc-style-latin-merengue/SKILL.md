---
name: mc-style-latin-merengue
description: "Specific composition and arrangement for Merengue típico, orchestra, merengue-house and urbano. Use for merengue típico/perico ripiao, orquestal, merengue-house, merengue de calle, merengue-pop; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: merengue, Latin, contemporary, fusion, composition, artist analysis."
---

# Merengue típico, orchestra, merengue-house and urbano

**Primary lineage:** Dominican Republic. **Branches:** merengue típico/perico ripiao, orquestal, merengue-house, merengue de calle, merengue-pop.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Tambora two-sided gestures and güira continuous subdivisions are independent from an accordion/sax riff. Specify whether the reference counts in 2 or 4 and distinguish double-time notation. |
| Low end | Propulsive bass with short approaches and strong coordination with tambora. Avoid over-long 808s over continuous acoustic kicks. |
| Harmony | Compact major/minor loops and dominant functions; harmonic sophistication should serve repeated vocal and instrumental hooks. |
| Form | Instrumental launch → verse → coro and horn/accordion response → dance break → chorus variation; shorter pop hybrids can frontload the hook. |
| Melody/hook | Bright compact repeated motifs and instrumental answers with room for brisk vocal diction. |
| Vocal roles | Call-and-response, quick consonants and shouts are optional subgenre features; don't flatten every line into one level. |
| Essential lineup | Típico accordion+sax+güira+tambora+bass; orquesta uses brass/keyboard; urbano may bring electronic drum and bass. |
| Production/space | Keep güira in a separate high transient slot from hats; subtract horns when the vocal melody needs emphasis. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **Johnny Ventura** — Stage-band presentation of merengue. **Transfer:** Design punchy vocal/band exchanges.
- **Wilfrido Vargas** — Horn-focused orchestral merengue. **Transfer:** Build coordinated brass riffs and percussion hits.
- **Juan Luis Guerra / 4.40** — Refined arrangements and harmonic palette. **Transfer:** Support elegant melody with precise Dominican rhythmic roles.
- **Elvis Crespo** — Immediate merengue-pop hooks. **Transfer:** Open with a strong melodic or instrumental signature.
- **Omega** — Merengue de calle/electronic impact. **Transfer:** Put aggressive electronic bass inside a defined merengue rhythmic engine.

## Fusion routes
- **With house:** Choose whether tambora or house kick owns low-end clock and document the compromise.
- **With pop:** Keep perico ripiao/merengue percussion roles while rearranging into verse/chorus.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-merengue` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Merengue mislabeled as clave-based salsa; ignoring güira; treating half-time and double-time BPM as different songs.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
