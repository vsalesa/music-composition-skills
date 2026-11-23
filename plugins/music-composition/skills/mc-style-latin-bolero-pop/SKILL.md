---
name: mc-style-latin-bolero-pop
description: "Composition and production grammar for Bolero, romantic ballad, rock en español and contemporary Latin pop. Distinguishes cultural and rhythmic roots, composer/artist innovations, contemporary forms and explicit cross-genre fusion. Keywords: bolero-pop, Latin, Brazilian, Caribbean, contemporary, fusion."
---

# Bolero, romantic ballad, rock en español and contemporary Latin pop

## Select a real tradition
**Region:** Mexico, Caribbean and Ibero-American pop scenes. Choose the specific substyle, era and instrumental lineup; never assume the whole continent follows son clave, a single tempo, a universal backbeat or a single harmonic palette. For complete tracks load `mc-workflow` first. For mixed styles load `mc-style-latin-fusion` and the partner style.

## Functional rhythm and ensemble
Bolero's slow pulse, guitar/piano arpeggios and dramatic vocal cadence must be differentiated from Cuban bolero-chacha and generic ballad. Contemporary pop and rock en español are larger families requiring explicit subgenre naming.

## Composition and arrangement
Write a vocal phrase with long cadence/space, harmonic tension at key words, melodic instrumental answers, and small dynamic increases. Latin pop may adopt other grooves but shouldn't use 'Latin' as a self-sufficient rhythm label.

### Required decisions
1. Decide the substyle and notation unit (quarter-note BPM, any 6/8–3/4 or half/double-time relationship).
2. Write a recognizable two-to-four-bar bass/percussion skeleton, naming which instrument holds pulse and which carries anticipations.
3. Choose a characteristic timbre or melodic instrument as the non-vocal hook; write its first entry and one variation.
4. Distinguish the primary lead, rhythmic accompaniment, instrumental responses and any collective chorus.
5. Plan one density drop and at least one instrumental exit, not just a continually growing arrangement.
6. For contemporary adaptation identify what precisely changes in harmony, groove, vocals, instrumentation or electronic production.

## Artists as compositional lenses
- **Los Panchos** —  voice/guitar bolero architecture.
- **Armando Manzanero** —  sophisticated romantic songcraft.
- **Luis Miguel** —  orchestral bolero reinterpretation.
- **Juan Gabriel** —  expansive dramatic ballad.
- **Shakira** —  pop-rock and global rhythm crossings.
- **Juanes** —  guitar-led rock en español.
- **Natalia Lafourcade** —  acoustic Mexican roots.
- **Mon Laferte** —  bolero and modern alt-pop theatricality..

*Artist names do not authorize imitating a living singer's voice, copying a recording, asserting a BPM, or reproducing a protected arrangement. These are broad analytical lenses; validate any track-level claim with recording and personnel evidence.*

## Fusion experiments
1. **bolero with orchestral pop** — build an A version retaining the named tradition, then a B changing exactly one external musical dimension. Keep the musical motif constant, document style ownership, and compare the arrangement with/without the traditional rhythmic role.
2. **pop-rock with cumbia** — build an A version retaining the named tradition, then a B changing exactly one external musical dimension. Keep the musical motif constant, document style ownership, and compare the arrangement with/without the traditional rhythmic role.
3. **bolero with R&B** — build an A version retaining the named tradition, then a B changing exactly one external musical dimension. Keep the musical motif constant, document style ownership, and compare the arrangement with/without the traditional rhythmic role.

## ARR-SPEC integration
- `meta.style_layer: mc-style-latin-bolero-pop` for base. For multistyle use `meta.style_layers` with one base and one owner for each dimension; explain in `meta.fusion_note`.
- `meta.tempo` is numeric quarter-note BPM. `arrangement.groove.feel` uses `straight|swing16|shuffle|halftime|2:1|3:1`, not `straight16`.
- `arrangement.groove.quantize_policy` is a per-part percentage map. `arrangement.bass_kick_relation.mode` must be `locked`, `interlocking` or `call-and-response`.
- Fill `form[].harmony` and `form[].harmony_letters` consistently. Do not invent schema fields such as `meta.notes`.
- Source-of-truth: `mc-workflow/ARR-SPEC.schema.md`; other skills own generic theory and postproduction. If claiming a unique genre marker, cite a musical example and describe an audible/structural consequence.

## Acceptance
- [ ] Is the chosen branch recognizable from its musical functions even with the instrument names hidden?
- [ ] Are low-end, groove and harmonic/melodic hooks independently specified?
- [ ] Does the artist-era innovation alter a real musical dimension rather than an adjective?
- [ ] Is fusion intentionally assigned with one owner per simultaneous dimension?
- [ ] Are there a contrasting section and at least one subtraction event?
