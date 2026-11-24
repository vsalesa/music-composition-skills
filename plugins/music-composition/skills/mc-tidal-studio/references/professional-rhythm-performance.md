# Groove & performance · a time-domain production specification

The test of an expert arranger is not whether it adds "humanisation". It is whether distinct instruments sound like players agreeing on one beat while disagreeing **expressively** on placement and stress. Every microtiming value without a reference is an experiment, not a genre fact.

## Time model first

For a studio 4/4 bar mapped to one Tidal cycle:
- At quarter-note BPM = B, the cycle lasts `240 / B` seconds; one beat lasts `60 / B`.
- A 16-step grid has 4 sixteenths per beat. Its step spacing is `15 / B` seconds.
- A two-bar clave occupies two cycles if one cycle = one 4/4 bar. Some Latin reference scores count in 2: re-map deliberately, don't double the tempo blindly.
- An anticipation one sixteenth early at 140 BPM is ~107 ms; 10 ms is a microtiming offset, not a new sixteenth-note placement.

**Distinguish:** rhythmic composition (which subdivision sounds), velocity/dynamics (how hard), articulation/gate (how long), and microtiming (how early/late). Do not use random `nudge` to replace a written pickup.

## Layer interplay

| Player | Structural onset decision | Performance/sonic treatment |
|---|---|---|
| Güira/güiro | Recurring texture with differentiated long/short gestures | Distinct sample positions and accents, not uniform hats |
| Tambora | Rim vs head role, cadence pickup across bars | Strike families and overlap management |
| Conga | Open/mute/slap/heel-toe functionality | Different transient/tail and velocity |
| Bass | Harmonic landing vs anticipation | Short-attack or damped release relative to low drum |
| Piano/segunda | Rhythmic comping with meaningful rests | Short chord gates, stronger/weaker accents |
| Horn/requinto | Phrase lead/answer, rests and pickup | Breath/pick, articulation, phrase boundaries |

## Programming steps

1. **Tap only pulse**, then add one percussion timeline. Decide if a strong stroke coincides with beat or offbeat.
2. Add **independent** secondary percussion; if all attacks duplicate pulse exactly, the engine has no internal movement.
3. Add bass and check collisions with low drums. Ask if a bass note should anticipate a harmonic event: correct **pitch destination**, not just onset.
4. Add chordal comping around the existing pattern. Decide which events carry harmonic clarity and which provide only accent.
5. Add melody only after you can dance to the rhythm section alone.
6. Add accent map, note-off envelopes, ghost tones and measured/controlled placement selectively.
7. Listen at normal tempo and a slower tempo, solo and paired layers. Avoid making everything "loose".

## Microtiming experiments, not invented measurements

Choose one consistent **per-instrument** timing strategy to audition (e.g. lead horn fractionally ahead; pad farther behind; percussion solid), but do NOT treat these as universal salsa/merengue timing laws. At 140 BPM, 10 ms is roughly 0.023 beats, while shifting a full sixteenth is ~107 ms. Fixed offsets can quickly harm fast patterns. Note-on and offbeat anticipation must remain in meaningful relation to meter. Tidal's function names and actual timing units must be confirmed against version/runtime; do not hardcode unverified syntax.

## Accent architecture

- The rhythmic identity should survive with all velocities fixed, but the performance should improve with **instrument-role accents**.
- Main pulse/accent not always loudest sample: leave room for natural dynamic contrast. Do not randomly alternate between very quiet and clipping velocities.
- In multi-layer Latin music use two-bar phrase accent contours where the genre requires them, including occasional break/transition gestures.
- Articulation and timbre vary with strokes: one cowbell or conga sample with different gains is not equal to several human articulations.
- Restrict swing: not every merengue, salsa or samba performance is uniformly swung. Never globally apply a house shuffle to "make it Latin".

## Diagnostic gates

**Structural:** consistent meter/BPM; length aligned across tracks; intentional pickups; correct harmonic targets; clave direction when relevant; no undefined sound names. **Performance:** role-specific velocities; plausible attack/decay; no inadvertent double triggers; no competing low-end tails; meaningful breath/rest. **Playback:** listen for timing between bass/kick/piano and for repetitive mechanical accents; compare in A/B with timing change alone.

**Measured vs hypothetical:** MIDI timing grids and statistical onset matrices derived from a few songs may support hypotheses, not establish a definitive style law. Record reference count and subdivision interpretation. If a user-provided take is available, extract its actual attack/velocity map and adapt it with permission.

Useful external implementations: https://github.com/tomascabralh/prod-skills (groove skill as an engineering analogue, not an authority for every Latin groove); Berklee Afro-Latin instruction https://pulse.berklee.edu/?id=4&lesson=15 .