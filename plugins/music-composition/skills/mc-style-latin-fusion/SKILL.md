---
name: mc-style-latin-fusion
description: "Composing intentional Latin fusion and contemporary crossovers: salsa/reggaeton, bachata/R&B, cumbia/electronic, corridos/trap, samba/jazz, pagode/pop, funk brasileiro/pop, tango/electronic, plena/urbano. Defines dimensions, genre identity tests, arranged transitions, artist innovation as technical parameters and ARR-SPEC-safe ownership. Use for any request naming two or more genres or a contemporary Latin artist with hybrid arrangements."
---

# Latin fusion — a composition engine, not a blend of presets

Start with `mc-workflow` and the base genre child, then load the counterpart child (or another L3 style), **not** a generic 'Latin flavor' recipe. This skill owns decisions specific to the **seams and ownership** of the hybrid. The workflow still owns the ARR-SPEC format.

## Determine the form of fusion

| Mode | Musical technique | Risk |
|---|---|---|
| Superposition | Keep one unambiguous bass/groove engine, and let another genre own harmony, instrumental color or vocal delivery | Overlapping drum loops and low-end |
| Alternation | Genre A governs section A, genre B governs section B; use a shared motif, chord/common tone, silence, percussion pickup or countable crossfade | Arbitrary unrelated songs glued together |
| Transformation | The same motive gradually switches instrumentation, harmonic rhythm and accent grammar | Identity disappears during transformation |

## Ownership of current ARR-SPEC

Read `mc-workflow/ARR-SPEC.schema.md` before generating. `meta.style_layers` contains one `base` and overlay skill(s) with exclusive owners from:
`harmony`, `melody`, `groove`, `low_end`, `fill_policy`, `instrumentation`, `color_instruments`, `timbre`, `arrangement_hook`, `vocal_delivery`, `vocal_delivery_verse`, `vocal_delivery_chorus`, `form`, `mix`.

**Important:** the current `owns` property is *global* and cannot represent a different groove owner for verse and chorus. Until the main schema evolves, record section-local transitions explicitly in `meta.fusion_note`, `form[].note` and `form[].events`, with the base groove owner as global and section-specific borrowing documented in prose; do not invent `style_layers_by_section` or other illegal fields.

### Example: urban bachata with R&B voice and harmony

```yaml
meta:
  style_layer: mc-style-latin-bachata
  style_layers:
    - {skill: mc-style-latin-bachata, role: base, owns: [groove, low_end, instrumentation, arrangement_hook]}
    - {skill: mc-style-citypop-rnb, role: overlay, owns: [harmony, melody, vocal_delivery, timbre]}
  fusion_note: "Bachata guitars and percussion set rhythm, while R&B supplies harmony and vocal phrasing."
```

This is the *meta fragment only*, not a complete validated ARR-SPEC. Ensure individual tracks use only legal template fields.

## Practical contemporary fusion recipes

| Base and target | Keep from base | Borrow | Avoid |
|---|---|---|---|
| Salsa + urbano | Clave-oriented ensemble, bass/piano interlocking, call/response | Urban texture or a distinct beat-break section | Two full uncoordinated drum engines |
| Bachata + R&B | Segunda/requinto/percussion dialogue | Extended harmony, vocal runs, intimate electronic timbre | Bachata guitar used only for ornamental fills |
| Cumbia + electronic | Repeated cumbia bass/percussion engine and regional lead hook | Texture, reverb, transitions and selective synth bass | Replacing the entire cumbia pulse with straight EDM |
| Corrido tumbado + trap | Requinto hook and regional narrative | Vocal cadence, selective hats/808 | Guitar-only decoration behind generic trap |
| Tango + electronic | Tango phrasing, marcato and instrumental tension | Drum programming and texture | Constant EDM four-on-floor masquerading as tango |
| Brazilian funk + pop | Brazilian electronic percussion identity | Pop chorus and harmony | Generic dembow mislabeled funk carioca |
| MPB + jazz | Explicit Brazilian branch, melodic prosody, nylon/ensemble dialogue | Jazz extensions/solo language | Labeling all Brazilian music 'bossa nova' |
| Plena + urbano | Pandereta conversation and responsive choruses | Electronic sub, short urban verse | Calling plena a variant of Cuban son clave |

## Artist-driven innovation transfer

Use **era + intervention + compositional consequence**, not 'make it sound like celebrity X'. Examples:
- **Aventura:** bachata engine with New York R&B-inflected vocal phrasing -> assign ownership to bachata groove, R&B vocal harmony.
- **Los Van Van:** songo kit and Cuban electric bass mechanics -> orchestrate gear changes, not simply fast salsa.
- **Carlos Vives:** vallenato/rock band integration -> retain accordion and regional rhythmic jobs.
- **Bomba Estéreo:** Colombian rhythmic motifs and electronic production -> keep cumbia identity while changing synthesis.
- **Tainy:** producer-led sparse urban experimentation -> design silent beats, subtraction and evolving texture.
- **Astor Piazzolla / Bajofondo:** tango grammar meeting concert/jazz or electronic structure -> retain tension, articulations and a specific rhythmic phrase.
- **Bad Bunny / Karol G / Rauw Alejandro:** contemporary cross-tradition projects -> distinguish a **real genre change** between sections from an acoustic sample on top of a persistent reggaeton beat.

These are analytical strategies, not instructions to copy protected compositions, studio masters, exact artist timbres or living people's voices.

## Six-step fusion validation

1. Identify the *primary* genre and at least two audibly verifiable traits.
2. Identify exactly which dimension is borrowed; write a reason linked to the musical idea.
3. Map 2-4 bars of rhythm, bass and hook; inspect competing clave directions and double transients.
4. Plot a section switch including a **shared motif, chord tone, pickup, silence, or deliberate tempo reinterpretation**.
5. Rehearse an A/B version with the borrowed layer muted. Decide if the genre still sounds like itself and what the overlay contributes.
6. Verify `ARR-SPEC.schema.md`: enums, chorus variants, one base and single ownership of simultaneous dimensions, beat-count tempo conversion, consistent chord spellings.

**Evidence:** use a real performance/recording and credited source before reporting numeric patterns or precise artist-specific production settings. Regional practices are diverse; no named artist speaks for an entire country.
