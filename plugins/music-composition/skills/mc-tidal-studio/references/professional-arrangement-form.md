# Form and orchestration · from looping patterns to authored songs

A professional track has narrative events: introduction, motif presentation, variation, tension, withheld expectation, payoff and exit. Most Tidal patterns are cycles; **cycles must be directed into form**.

## Four nested timescales

1. **Single attack:** sound shape and accent (articulation).
2. **1–2-bar cell:** genre-defining percussion/bass/piano relation.
3. **4–8-bar phrase:** hook question, answer, altered return, short anticipation.
4. **Whole arrangement:** contrasting sections, changes of instrument ownership and density, ending.

Use the **smallest timescale that fixes the actual complaint**. A bad guitar lick cannot be repaired by adding a 32-bar riser. A monotonous 4-bar loop can be repaired by section design without changing its harmony.

## Voice/role ownership

Maintain a role map for every active track: pulse, secondary rhythm, bass foundation, harmonic rhythm, main melody, melodic response, pad/colour, transition. For each write an active section range. Only one unambiguous lead foreground at a time unless purposeful counterpoint. In salsa/timba/merengue, the "comping" part can provide rhythmic detail without serving as lead. In vocals, supporting horns answer during rests.

**Breach conditions:** two subs with long sustained tails; two foreground melodies in same register and subdivision; piano chords and second guitar both filling every eighth note; horns playing every bar at full density; noisy percussion taking all high-frequency space.

## Section design worksheet (illustrative)

| Stage | Function | Material retained | Material changed |
|---|---|---|---|
| Intro | Declare identity and anticipation | Short rhythm figure or lead pickup | Withhold bass/horns or first hook resolution |
| A / verse | State motif and story | Groove cell, harmonic grammar | Fewer chords/instruments, vocal space |
| B / chorus | Pay off and lift | Recognisable motif or answer | Register, voicing, participation, harmonic rhythm |
| Instrumental / mambo | Ensemble's own thematic statement | Key/progression or rhythmic identity | Horn answer or accordion lead with controlled percussion hits |
| Break / puente | Contrast then build expectation | A small invariant motif/clave/pulse | Remove/reassign parts; change gear deliberately |
| Return / outro | Recognisable transformed return and closure | Hook identity | Alter cadence, orchestration and exit |

For a 16-bar class lesson a 4+4+4+4 layout is possible; for finished music plan a longer form if requested. **Do not equate every genre with "verse → pre-chorus → drop".** Traditional dance-music coro/pregón, montuno, marcha or instrumental breaks deserve their own terminology.

## A/B choice architecture

Provide variants on the *same song context*:
- **A: idiomatic:** protect base grammar, repair one mis-voiced/mis-timed instrument.
- **B: melodic:** change motif rhythm/answer while preserving chords and locked groove.
- **C: structural:** rearrange part entrances, silence, accompaniment density and payoff timing.
- **D (optional): sound:** hold MIDI notes constant and compare acoustic vs synthetic timbre.

When explaining musical differences, predict something observable (e.g. "horns enter only after the guitar rests"), not "this feels better". When a variant is chosen, record its motif identity/harmonic context and preserve it on the next step.

## Special course feature: "Otra propuesta"

This is a **recommended host feature, not currently provided by the skill**. Keep the course's verified traditional groove and prior user-approved harmonic framework immutable, then regenerate only the melody/lead track for its specified 4/8 bars. Return three different choices using existing Maestro `variantes`, keeping locked track IDs absent from `cambios`. Candidate options:
- regenerate all melody while keeping genre grammar and chord destinations;
- preserve pitch landmarks but change onset/rest pattern;
- preserve onset map but regenerate contour;
- develop accepted motif with sequence/fragmentation/counter-answer.

Upon selection, store the chosen candidate and its seed/brief plus the harmonic map for later section continuity; do not reset on "next course step". Validate timing and target chords from queryArc/MIDI if the host implements programmatic checks. No fake claim that this validator is already available.

## Ending must be authored

Songs need a decisive exit or designed fade; e.g. call-response tag then one final hit, cadence and stop, or a justified loop fade for electronic styles. Do not just leave the last four-bar pattern replaying forever. Provide a role-based final two-bar script to transition from chorus or mambo and resolve the expected harmonic target.

## Diagnostic prompts

- Can the intro be distinguished from chorus without looking at the timeline?
- Does a motif return at least once **changed but recognisable**?
- Is there a scene in which one important instrument drops out for another to speak?
- Does the last phrase connect to the ending rather than stop at an arbitrary bar?
- Is the chosen genre's section grammar preserved, not shoehorned into EDM structure?
- Is the part count justified by listening, not "more tracks = quality"?

Music-production skills emphasizing lifecycle and decision preservation: https://github.com/sb-dev/music-production-skills .