---
name: mc-style-latin-cumbia
description: "Specific composition and arrangement for Cumbia: Colombian roots and Latin American transformations. Use for Colombian traditional/orchestral, Mexican sonidera, rebajada, cumbia villera, Peruvian chicha/amazónica, Argentine cumbia, electro-cumbia; includes original tradition, modern artist innovations and documented fusion boundaries. Keywords: cumbia, Latin, contemporary, fusion, composition, artist analysis."
---

# Cumbia: Colombian roots and Latin American transformations

**Primary lineage:** Colombia, Mexico, Peru, Argentina and beyond. **Branches:** Colombian traditional/orchestral, Mexican sonidera, rebajada, cumbia villera, Peruvian chicha/amazónica, Argentine cumbia, electro-cumbia.

## Routing and decisions
For a complete track load `mc-workflow`, then this skill. Select **a specific branch and era** before choosing sounds. General melody/harmony/rhythm rules belong to `mc-melody`, `mc-harmony` and `mc-rhythm-section`; this skill owns only genre-specific decisions. For mixed genres, invoke `mc-style-latin-fusion` (or `mc-workflow` §2.4 until installed), and partner styles. Artist case studies are in [references/artists-fusion.md](references/artists-fusion.md).

Answer these questions before writing: Which named branch? Which beat and tempo counting convention? Which two instruments create its identity? What is the vocal/section architecture? Which musical dimension, if any, is borrowed from another genre?

## Style grammar and composition actions

| Dimension | Must decide |
|---|---|
| Groove | Different regional cumbia families use different percussion patterns; never force Afro-Cuban clave as a global rule. Map bass cycle, drum or guacharaca/güiro accents and subdivision pattern from chosen branch. |
| Low end | Repetitive syncopated motif often carries dance identity; a slow rebajada or chopped electronics needs a re-authored bass phrase, not merely a BPM change. |
| Harmony | Short major/minor repetitive loops; psychedelic cumbia can use modal pedal tones or guitar-driven harmony; electric cumbia may choose synth chord pulses. |
| Form | Instrumental riff/opening → verse/coro → interlude variation → return; modern cumbia may use beat-built structures and producer breaks. |
| Melody/hook | Accordion, gaita, flute, electric guitar or synth may carry the main hook depending on region; the voice is not always the lead signature. |
| Vocal roles | Regional conversational and call-response approaches; for cumbia villera and sonidera distinguish storytelling, chants and MC voice. |
| Essential lineup | Choose regional gaita/drums/guacharaca OR Mexican accordion/keys OR Peruvian processed electric guitars; not every optional color at once. |
| Production/space | For chicha/amazónica preserve guitar picking and effects as a structural hook; for electro-cumbia preserve the bass-percussion cycle rather than applying generic EDM beats. |

## Traditional / contemporary separation
**Traditional:** choose a historical ensemble and describe its rhythmic role; do not treat a modern producer's preset as the timeless definition. **Contemporary:** name the altered dimension (e.g., electronic bass, pop vocal phrases, chorus placement, harmonic color, textural break). Retain a demonstrable functional link to the original style. Contemporary does not automatically mean 'more quantized' or 'more 808'.

## Artists: which musical decision changed?
- **Lucho Bermúdez** — Colombian orchestral dance arrangements. **Transfer:** Use winds and brass as arrangements of a cumbia pulse.
- **Totó la Momposina** — Rooted Colombian vocal/percussive performance. **Transfer:** Let chorus and local percussion articulate form.
- **Los Ángeles Azules** — Sonidera cumbia with expansive pop collaborations. **Transfer:** Use accordion/keyboard melodic hook and clear dance low end.
- **Damas Gratis** — Argentine cumbia villera keyboard and vocal character. **Transfer:** Make synth motif and colloquial rhythmic delivery core.
- **Los Mirlos** — Peruvian Amazonian psychedelic electric-guitar cumbia. **Transfer:** Use spring/reverb/phase color on a genuine guitar hook.
- **Bomba Estéreo** — Electro-cumbia and Colombian Caribbean crossover. **Transfer:** Combine rhythmic continuity with electronic textural changes.
- **Chancha Vía Circuito** — Folkloric/electronic cumbia atmosphere. **Transfer:** Let organic samples remain rhythmic rather than decorative.

## Fusion routes
- **With electronic:** Cumbia bass and percussion own groove; electronic layer owns timbre and transitions.
- **With rock/psychedelia:** Electric guitar is melodic engine; do not turn rhythmic subdivision into rock backbeat by default.

Never use an artist name as sufficient production instructions. Translate an artist reference into at least **two concrete arrangement dimensions** (rhythm, instrumentation, harmony, melody, phrasing, structure, sound), and cite a track-level recording or primary credit before asserting note positions or BPM.

## ARR-SPEC contract (v1.0)
- `meta.style_layer: mc-style-latin-cumbia` for single-style works. A multi-style spec uses `meta.style_layers` with exactly one base and one owner per dimension.
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
- [ ] **Reject:** One generic cumbia pattern for all countries; automatically adding clave; equating 'Latin' with horns.

See [references/artists-fusion.md](references/artists-fusion.md) for era and fusion recipes. And see `mc-workflow/ARR-SPEC.schema.md` for the authoritative syntax.
