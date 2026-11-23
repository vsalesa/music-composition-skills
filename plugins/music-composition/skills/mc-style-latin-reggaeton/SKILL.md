---
name: mc-style-latin-reggaeton
description: "Specific composition and arrangement for Reggaeton from underground to experimental and melodic urbano. Use for reggae en español roots, Puerto Rican underground, old-school reggaeton, perreo, pop reggaeton, neo-perreo, club/experimental, melodic reggaeton; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: reggaeton, Latin, contemporary, fusion, composition, artist analysis."
---

# Reggaeton from underground to experimental and melodic urbano

**Primary lineage:** Panama, Puerto Rico and diasporic Caribbean exchange. **Branches:** reggae en español roots, Puerto Rican underground, old-school reggaeton, perreo, pop reggaeton, neo-perreo, club/experimental, melodic reggaeton.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Dembow-derived kick/snare placements are a family of loops, not one immutable pattern. Map kick displacement, snare pickup, ghosts and hats at each section; document whether the felt beat is half-time. |
| Low end | Select sub/808/bass ownership, shorten low-end tails when kick collides, and avoid a simultaneously long sub with an acoustic kick on the same attacks. |
| Harmony | Repetitive minor/modal or pop vamps are valid; chromatic and acoustic changes may create a second-half turn but need a motif tying sections together. |
| Form | Instant signature or hook → verse → coro/perreo hook → subtractive break → reworked hook; beat switches must have a stated transition mechanism. |
| Melody/hook | Create distinctive rhythmic consonant patterns plus a singable chorus; repeated vocal motif can take different pitches or rhythms across sections. |
| Vocal roles | Rap, sing-rap, falsetto and melodic singing are choices. Separate lead/ad-lib/coro roles and avoid endless automatically spaced ad-libs. |
| Essential lineup | Programmed drums, tuned low-end, sample/keys/synth texture, vocal stacks and optional acoustic regional overlay. |
| Production/space | Producer-authored micro-variation by bar, half-bar breaks and selective reduction matter more than layering every four beats. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **El General / reggae en español pioneers** — Panamanian reggae-in-Spanish pathway. **Transfer:** Recognize Jamaican dancehall lineage rather than claiming a single invention.
- **Ivy Queen** — Assertive rhythmic vocal presence in Puerto Rican reggaeton. **Transfer:** Write a forceful recognizable rhythmic lead motif.
- **Daddy Yankee** — Worldwide crossover of reggaeton hooks. **Transfer:** Foreground instantly identifiable rhythmic chorus.
- **Tego Calderón** — Afro-Caribbean rhythmic flow and hip-hop links. **Transfer:** Vary rap accents against a stable beat.
- **Don Omar** — Melodic, dramatic reggaeton architecture. **Transfer:** Use an expansive hook over spare verse beat.
- **Tainy** — Minimalist and experimental Latin urban production. **Transfer:** Use texture subtraction and beat switch as harmonic-form decisions.
- **Bad Bunny** — Cross-genre contemporary Puerto Rican urban music. **Transfer:** Treat salsa/plena/bomba sections as full music traditions, not samples only.
- **Rauw Alejandro** — Melodic dance-pop/electronic experimentation. **Transfer:** Use sectional electronic timbre change and agile sung hooks.
- **Karol G** — Contemporary pop/urbano and tropical crossovers. **Transfer:** Use a strong unified melodic motif across multiple rhythmic idioms.

## Fusion routes
- **With salsa / plena:** Alternate groove ownership, keep a shared vocal motive, plan human-played percussion as structural.
- **With electronic:** Allow EDM sound design to own timbre, not automatically the drum grammar.
- **With bachata:** Preserve bachata guitar roles while reducing the dembow so the hybrid is not two complete backing tracks.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-reggaeton` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Claiming reggaeton was solely Puerto Rican without acknowledging Panama/Jamaica; one dembow file duplicated 64 bars; excessive always-on layers.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
