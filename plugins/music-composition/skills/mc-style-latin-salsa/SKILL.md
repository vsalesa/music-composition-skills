---
name: mc-style-latin-salsa
description: "Composing and arranging salsa, son montuno, mambo, salsa dura, salsa romantica and Colombian/modern salsa. Use for clave-aware piano guajeos, coro-pregon, brass moñas, bass tumbao, contemporary salsa orchestration and salsa crossovers; consult mc-style-latin-fusion for mixed genres. Keywords: salsa, son, mambo, guajeo, montuno, coro, pregon, moña, Fania, Grupo Niche."
---

# Salsa composition and arrangement

**Identity gate:** specify the tradition first: Cuban son/son montuno, New York salsa dura, salsa romántica, Colombian salsa, mambo-led or contemporary crossover. 'Latin' alone is not a musical decision. Salsa is a transnational evolution of son and other Afro-Caribbean traditions, not just the percussion pattern of one nation.

## Routing and ownership

- Read `mc-workflow` first for a complete ARR-SPEC. This skill owns **style-specific decisions**; `mc-rhythm-section` owns kit execution, `mc-harmony` generic voicing, `mc-vocal-direction` vocal production, and `mc-arrangement-arch` song-wide energy and instrument entrances.
- For a salsa + reggaeton or salsa + jazz result, read `mc-style-latin-fusion` and the partner style layer. Do not assign two simultaneous owners to `groove`.
- Clave and two-bar interlocking belong in the composition plan even when no claves are audible.

## Five obligatory choices

1. **Tradition and era:** identify one named substyle; choose traditional ensemble, modern orchestra or hybrid.
2. **Clave direction:** son or rumba; 2-3 or 3-2. Determine from the phrasing of the melody, bass and ensemble, not a genre-wide default. Write two bars and compare each fixed figure for crossed orientation.
3. **Engine:** specify bass tumbao, piano montuno/guajeo, conga, timbal cáscara/bell and optional bongó/campana separately. Some parts can be omitted when the same role is already filled.
4. **Vocal architecture:** tema and coro-pregón (call/response) versus the more continuous pop/romantic verse-chorus model.
5. **Hook:** choose one memorable recurring musical identity (horn moña, piano motif, coro cell, or bass riff) and specify exactly where it returns altered.

## Composition grammar

| Dimension | Actionable guidance |
|---|---|
| Groove | Write a two-bar map. Interlock clave-oriented bass, conga open tones, guajeo syncopation and bell; do not copy every accent into each part. |
| Low end | Write exact bass anticipations against kick on both clave sides. `bass_kick_relation.mode` accepts `locked`, `call-and-response`, or `interlocking`; choose by actual attacks, not labels such as 'bound'. |
| Harmony | A 2-, 4- or 8-bar vamp may sustain montuno while orchestration intensifies. Dominants, minor cycles, chromatic passing chords and jazz color are options rather than fixed requirements. |
| Melody | Compose a distinct tema; simplify repeated coro cells; leave space for pregón improvisation. |
| Brass | Write concise trumpet/trombone/sax moñas with rests and contrary/answering motion. Avoid doubling the vocal continuously. |
| Form | Possible: intro -> tema -> coro-pregón/montuno -> mambo/moñas -> solo/descarga -> cierre. Salsa romántica can retain verse/chorus but must specify how its orchestral language works. |
| Dynamics | Plan cuts to percussion, horn entries and singer-only moments; density is a structural parameter. |
| Vocal | Differentiate a lead narrative, tight coro unison/harmony and improvised pregón. Write breathable phrase lengths. |

### Artist innovations as compositional lenses

These are **analytical influences, not instructions to duplicate a particular recording or a living artist's voice**.

| Artist / movement | Distinctive contribution | Transferable composition decision |
|---|---|---|
| Arsenio Rodríguez | Son conjunto and the expanded montuno ensemble | Assign tres/piano, bass and percussion interlocking roles |
| Eddie Palmieri | Angular piano writing and adventurous harmony with strong trombones | Place a harmonically tense piano answer against a shorter brass motif |
| Willie Colón with Héctor Lavoe | Urban New York trombone-led salsa | Use low brass as a repeatable instrumental hook |
| Celia Cruz | Powerful lead/coro interplay and expressive improvisation | Keep pregón responses flexible and progressively varied |
| Rubén Blades | Narrative and socially conscious salsa songwriting | Hold back arrangement density when lyrics carry a plot turn |
| Grupo Niche | Distinctive Colombian salsa hooks and orchestration | Let brass countersubjects vary with chorus returns |
| Marc Anthony | Salsa romántica and pop-oriented vocal drama | Retain live interlocking percussion beneath a wide melodic chorus |
| Nathy Peluso | Contemporary theatrical engagement with salsa | Design contrasts between spoken, sung and shouted vocal gestures |

## Contemporary and fusion recipes

**Salsa + urbano:** keep a real salsa engine in the full-orchestra section; use an electronic break with a different groove owner in another section, or add carefully chosen electronic texture while salsa retains the pulse. Avoid an automatic full dembow loop under a complete son clave ensemble.

**Salsa + jazz:** keep dance pulse and clear coro-pregón, letting jazz own selected brass harmony or solo language. Reharmonize a transition rather than every coro bar.

**Salsa + pop:** use a shorter intro and earlier vocal hook; retain identifiable guajeo, hand percussion, brass dialogue and clave-consistent phrasing. A pop form is not inherently an authenticity failure.

## ARR-SPEC integration

- `meta.style_layer: mc-style-latin-salsa`; for fusion use `meta.style_layers` and `meta.fusion_note`.
- `meta.tempo` is numeric quarter-note BPM. Many salsa percussion sources count double-time; explicitly document the pulse convention in musical prose, not by silently doubling the BPM.
- `arrangement.groove.feel: straight` unless a justified alternative is intended. `quantize_policy` is a per-part map.
- Express kick/bass role as `arrangement.bass_kick_relation: {mode: interlocking, detail: "..."}` when partly coincident; never use an invalid enum.
- Provide roster `id, instrument, role, band, entry, exit`; plan `spectrum_budget` as a list of band ownership solutions.
- `form[].harmony` and `form[].harmony_letters` must agree; place section-specific musical commentary in `form[].note`.
- `vocal` must specify lead/coro delivery and section-specific variations; put non-vocal recurring hook in `arrangement.hooks.arrangement_hook`.
- The source-of-truth format is `mc-workflow/ARR-SPEC.schema.md`; this skill cannot add imaginary YAML fields.

## Acceptance tests

- [ ] Tradition, groove orientation and vocal architecture are explicit.
- [ ] Two-bar bass/guajeo/brass accents do not fight the chosen clave orientation.
- [ ] Coro and pregón have distinct jobs; orchestration supports rather than obscures them.
- [ ] At least one distinctive salsa instrument or structural role remains, even in pop/urban fusion.
- [ ] A real change in density or instrument lineup occurs; no identical endless four-bar loop.
- [ ] ARR-SPEC uses only existing schema paths and enum values.

## Research / listening starting points

- Smithsonian Folkways catalog and essays about Afro-Caribbean popular music: https://folkways.si.edu/
- Smithsonian National Museum of American History, Latin music collections: https://americanhistory.si.edu/
- For track-specific musical assertions, verify credited personnel and arrangement from primary releases, scores or scholarly analysis rather than inferring precise patterns from an artist name.

**Evidence discipline:** the tables above describe broad historical and stylistic contributions. Exact BPM, key, recording-specific clave orientation, MIDI notes, and measured millisecond timing require evidence from the specific track; never fabricate them.
