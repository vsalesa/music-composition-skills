---
name: mc-style-latin
description: "Router for Latin American and Caribbean music composition: salsa, timba, bachata, merengue, reggaeton, Dominican dembow, cumbia, vallenato, regional mexicano, corridos tumbados, samba, pagode, bossa, MPB, forro, piseiro, Brazilian funk, tango, bolero, Latin jazz, bomba, plena, and contemporary fusion. Load this before the appropriate mc-style-latin-* child. Historic Afro-Cuban and Brazilian rhythmic sources retained in reference.md and references/legacy-style-essay.md."
---

# Latin music — routing, authenticity, contemporary innovation and fusion

**Latin is not a groove preset.** This skill identifies an historically specific tradition, then routes to a skill that can make concrete rhythmic, melodic, vocal, arrangement and production decisions. The original long Afro-Cuban/Brazilian/Caribbean study is preserved verbatim at [references/legacy-style-essay.md](references/legacy-style-essay.md) with its original [reference tables](reference.md). The preserved essay is a **historical source interpretation**, not an override of present routing or `ARR-SPEC.schema.md`. It contains some outdated prohibitions and schema field names.

## Routing table

- **Afro-Caribbean ensemble and Puerto Rico:** salsa, son, mambo → salsa; songo, timba → timba; bomba, plena → bomba-plena; Puerto Rican urban → reggaeton; fusion → fusion.
- **Dominican traditions:** bachata → bachata; merengue típico/orquestal → merengue; Dominican dembow → dembow.
- **Colombia, Mexico and regional Latin Americas:** cumbia general → cumbia; Mexican sonidera/Argentine villera → cumbia-villera-sonidera; vallenato → vallenato; Mexican ranchera/norteño/banda → regional-mexicano; corridos tumbados → corridos-tumbados; Andean/Afro-Peruvian → andino-afroperuano.
- **Brazil:** samba/pagode → samba-pagode; bossa nova/MPB → bossa-mpb; baião/forró/piseiro → forro-piseiro; funk carioca → funk-brasileiro.
- **Other Latin/cross-border:** tango, milonga → tango; bolero, ballad, Latin pop-rock → bolero-pop; Latin jazz → latin-jazz; calypso, soca, ska, reggae, dancehall → caribbean-soca-reggae.

## Child skills to load — precise IDs

- `mc-style-latin-salsa`
- `mc-style-latin-timba`
- `mc-style-latin-bachata`
- `mc-style-latin-merengue`
- `mc-style-latin-reggaeton`
- `mc-style-latin-dembow`
- `mc-style-latin-cumbia`
- `mc-style-latin-regional-mexicano`
- `mc-style-latin-corridos-tumbados`
- `mc-style-latin-samba-pagode`
- `mc-style-latin-bossa-mpb`
- `mc-style-latin-funk-brasileiro`
- `mc-style-latin-forro-piseiro`
- `mc-style-latin-tango`
- `mc-style-latin-bolero-pop`
- `mc-style-latin-vallenato`
- `mc-style-latin-bomba-plena`
- `mc-style-latin-latin-jazz`
- `mc-style-latin-andino-afroperuano`
- `mc-style-latin-caribbean-soca-reggae`
- `mc-style-latin-cumbia-villera-sonidera`
- `mc-style-latin-fusion`

**Only open needed children.** For a single style open its child and any relevant rhythm reference, not all 21. For a fusion load the base style, the overlay style(s), `mc-style-latin-fusion` and `mc-workflow` §2.4. For a full song, `mc-workflow` owns the ARR-SPEC.

## Five questions before committing a style

1. Identify **subgenre, region and era**; distinguish an artist-influenced reinterpretation from a historically rooted performance.
2. Choose the **groove owner**, including which part anchors subdivisions, what bass/kick share, and whether a real clave governs the chosen style. Son/rumba clave cannot be required for bomba, plena, cumbia, Brazilian, merengue, regional Mexican or modern electronic forms by default.
3. Identify **melodic/harmonic signatures** and the arrangement roles of core instruments. Do not assume Brazilian and Afro-Cuban music must never meet: planned genre fusion is legitimate, but must not accidentally combine unexamined competing two-bar grammars.
4. Name the **vocal and form architecture**, and what the proposed artist or producer changed relative to a root tradition. A musician's name without concrete parameters does not count.
5. For deliberate hybridization choose **superposition**, **alternation by section**, or **transformation through development**. Write who owns rhythm and bass in every simultaneous layer or sequential section.

## Three legitimate fusion modes

| Mode | Arrangement decision | Ownership |
|---|---|---|
| Superposition | A clear base groove + a second genre's voicing, melody, timbre or voice | One owner per simultaneous dimension |
| Section alternation | Distinct genre-specific rhythmic engines for different sections, with an explicit transition | Declare the sequence in existing `form[].note`, `form[].events` and `meta.fusion_note` |
| Transformation | Shared motif changes instrumentation, accent pattern or harmonic function over time | Choose each stage's primary rhythmic identity and record the change |

**Research rule:** genre history, artist innovation and track-specific measured analysis are three separate evidence levels. Never invent a recording's BPM, clave direction, microtiming, harmony, session personnel or gear.

## Universal performance and arrangement checks

- The bass and percussion must be functionally coordinated, not duplicated because two genre presets were layered.
- Keep a clear primary pulse: son clave can function as a two-bar guide even when not sounded, but a clave is not mandatory in every Latin tradition.
- Specify whether a groove is straight, swayed or triplet based on the selected **branch**, not continent.
- Use structural subtraction and rhythmic conversation: a call-and-response, solo/ensemble relationship, or guitar/instrumental answer, wherever the genre supports it.
- In contemporary adaptations, **preserve at least one structural identity** (musical function and recognizable hook); sampled decoration alone is not evidence of fusion.

## ARR-SPEC compatibility

- Correct keys: `meta.style_layer`, `meta.style_layers`, `meta.fusion_note`, `meta.tempo`.
- `arrangement.groove.feel` accepts `straight`, `swing16`, `shuffle`, `halftime`, `2:1`, `3:1`. Never `straight16`.
- `arrangement.groove.quantize_policy` takes percentages by part, not prose; `arrangement.groove.push_pull` takes structured parts and offsets, never unsupported measured claims.
- `arrangement.bass_kick_relation.mode`: `locked`, `call-and-response`, `interlocking` (not `bound`).
- `arrangement.roster[].note` is allowed. `arrangement.spectrum_budget` is a list of band conflicts with `resolution` = `yield`, `separate registers` or `alternate`.
- There is no `meta.notes`: place explanatory decisions in `form[].note`, `arrangement.roster[].note` or `meta.fusion_note` as applicable.
- The 20 checks and the definitive field contract belong to `mc-workflow`. This router must not introduce new YAML fields.

## Genre-specific validation

1. Does removing the characteristic instrumental/rhythmic role make the song lose its named identity? If not, improve the design.
2. Can the vocalist and the principal rhythmic instrument occupy separate roles?
3. Does a modern artist reference change a musical **decision**, not merely adjectives about style?
4. In fusion, is there a documented reason for the overlap or hand-off, and no involuntary double groove?
5. Did the ARR-SPEC preserve the closed enums and produce real harmonic and structural choices?

## Sources and additional references

- Legacy book-based rhythm survey: [references/legacy-style-essay.md](references/legacy-style-essay.md); [reference.md](reference.md)
- Genre history and primary-source research: Smithsonian Folkways https://folkways.si.edu/ ; International Association for the Study of Popular Music https://www.iaspm.net/
- Each child contains an artist/fusion reference; treat historical claims as lenses and verify at track level before producing exact note/timing rules.
