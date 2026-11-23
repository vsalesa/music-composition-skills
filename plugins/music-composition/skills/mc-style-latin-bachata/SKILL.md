---
name: mc-style-latin-bachata
description: "Specific composition and arrangement for Dominican bachata, electric bachata and urban bachata. Use for traditional guitar bachata, electric bachata, bachata moderna, urban / New York bachata, bachata pop; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: bachata, Latin, contemporary, fusion, composition, artist analysis."
---

# Dominican bachata, electric bachata and urban bachata

**Primary lineage:** Dominican Republic / New York diaspora. **Branches:** traditional guitar bachata, electric bachata, bachata moderna, urban / New York bachata, bachata pop.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Map lead requinto, segunda rhythm guitar, bass, bongó and güira as distinct parts. Guitar syncopations must stay legible; chorus changes may alter bongó to a brighter rhythmic role. |
| Low end | Play a real complementary bass line to guitarra segunda; modern electronic sub can support but must not mask the bass and guitar attacks. |
| Harmony | Traditional compact cycles and bolero inheritances; modern R&B/pop can extend minor or major triads with color tones without overwriting groove. |
| Form | Instrumental requinto hook → verse → chorus → requinto response/solo → bridge or changed verse → final chorus. Short pop introductions are acceptable. |
| Melody/hook | The requinto answers vocal line endings. Keep a recurring descending or ascending figure and vary its ending at section returns. |
| Vocal roles | Traditional grounded speech-like lead vs R&B melisma and airy layering in urban bachata; select intentionally. |
| Essential lineup | Requinto guitar, segunda guitar, electric or acoustic bass, bongó, güira, lead voice; modern synths optional. |
| Production/space | Distinguish picked guitar attacks from vocal sibilants and shaker/güira; remove pads during a guitar response. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **Blas Durán** — Electrification of bachata sound. **Transfer:** Use electric guitar as a lead instrument with identifiable phrases.
- **Antony Santos** — Electric bachata's melodic and rhythmic identity. **Transfer:** Compose purposeful requinto phrases between vocal sentences.
- **Juan Luis Guerra** — Bachata's polished harmonic/arrangement crossover. **Transfer:** Write an elegant melodic chorus without erasing guitar roles.
- **Aventura / Romeo Santos** — New York urban bachata and R&B/hip-hop inflection. **Transfer:** Pair bachata engine with R&B vocal rhythm and pop hooks.
- **Prince Royce** — Bilingual modern bachata-pop crossover. **Transfer:** Shorten the path to an immediately identifiable vocal hook.
- **Rosalía** — Bachata reinterpretation in experimental pop context. **Transfer:** Preserve clear rhythmic cues while transforming vocal color.

## Fusion routes
- **With R&B:** Bachata owns guitar-bass-percussion grammar; R&B can own harmony/vocal timbre.
- **With reggaeton:** Use alternating sections with different groove ownership or spare synthetic texture, not full superposed drum loops.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-bachata` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** Generic slow romantic pop with acoustic guitar labelled bachata; lead guitar replacing all rhythmic guitar roles.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
