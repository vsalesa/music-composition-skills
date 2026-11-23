---
name: mc-style-latin-dembow
description: "Specific composition and arrangement for Dominican dembow, trapbow and urbano dance production. Use for Dominican dembow, trapbow, street dembow, melodic dembow, pop crossover; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: dembow, Latin, contemporary, fusion, composition, artist analysis."
---

# Dominican dembow, trapbow and urbano dance production

**Primary lineage:** Dominican Republic. **Branches:** Dominican dembow, trapbow, street dembow, melodic dembow, pop crossover.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Treat Dominican dembow as a distinct contemporary practice, not a spelling variant of reggaeton. Build short kick/snare loops with aggressive repetition, local percussion variants and interruptions. Dancefloor performance can emphasize repeated vocal/beat handoffs. |
| Low end | Short, forceful sub-bass hits and controlled low-end sustain; specify the kick/bass relationship, especially for dense rapid drums. |
| Harmony | Minimal vamp, pedal point or repeated modal figure can be more effective than harmonic complexity. |
| Form | Immediate beat-vocal hook, compact sections, phrase-based beat interruptions, contrasting drop or vocal call and response. |
| Melody/hook | Highly rhythmic vocal motifs, short pitch cells and intentionally repeated accents; build recognizability through delivery and edits. |
| Vocal roles | Percussive fast lead delivery, traded ad-libs/crowd shouts and breath-aware timing; not all tracks need high-speed unbroken rap. |
| Essential lineup | Programmed percussion, sub, voice, occasional synth stab or sampled accent; keep sparse. |
| Production/space | Make vocal edits, silence and percussion edits primary features. Differentiate Dominican dembow from mainstream reggaeton without stereotypes. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **El Alfa** — Global exposure of high-energy Dominican dembow. **Transfer:** Prioritize rapid vocal/beat interplay and abrupt structural edits.
- **Tokischa** — Genre-blurring Dominican urbano. **Transfer:** Use unconventional vocal character and provocative rhythmic contrast.
- **Chimbala** — Melodic and percussive dembow hooks. **Transfer:** Build concise chant hooks with short responses.
- **Chael Produciendo** — Producer-led rhythmic design in Dominican dembow. **Transfer:** Change percussion texture and stops without changing identity.

## Fusion routes
- **With trap:** Trap can own sub-bass and selected hats while Dominican dembow retains its signature vocal/beat exchange.
- **With merengue:** Make tambora/güira active in a dedicated section rather than sprinkling a güira loop throughout.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-dembow` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Identical reggaeton description duplicated; inappropriate generic trap hihat in every bar; no cadence/edit variation.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
