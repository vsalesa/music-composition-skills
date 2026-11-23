# Maestro compatibility guide (vsalesa/tidal-studio)

This is a knowledge reference, **not a new protocol implementation**. Maestro's own `server/assistant.py` sets the current authoritative JSON and Tidal rules; `server/skills.py` chooses which skill/reference to include. Re-check the host when code evolves.

## Host constraints observed

- `server/skills.py`: up to **2 unpinned** skills per response, `BUDGET=24000` total chars, `MAX_FILE=9000` chars and a single relevant reference per loaded skill. Sibling skill recommendations are not automatically loaded simply because this document links to them.
- `server/assistant.py`: JSON object containing `mensaje`, optional `cambios`, `variantes`, `sugerencias`, `controles`, `explicacion`, `reto`, `opciones`, `paso`, `descargar`. Skill selector asks for `skills` and `decisiones`; do not credit unread skills.
- `cambios.pistas`: each has `id` d1..d12, `nombre`, `tipo`, `codigo` (the pattern **after** dN $). Types `percusion`, `bajo`, `armonia`, `melodia`, `textura`, `voz`, `fx`. Don't replace whole session unless explicitly asked.
- `cambios.bpm` is clamped by the Python parser to **40..220**. Quarter-note BPM and Tidal cycle conventions must be reasoned carefully.
- Do not invent samples/synths or runtime functions. The engine can simulate success without a sound server; no real audition is implied.
- `variantes` holds 3–4 options with `titulo, descripcion, concepto, cambios`; `sugerencias` holds optional unapplied ideas with `titulo, porque, concepto, cambios`.

## Good Maestro response (illustrative JSON, not a guaranteed playback test)

```json
{
  "mensaje": "He preparado dos ideas musicales; escucha primero si el bajo deja respirar al motivo de guitarra.",
  "opciones": ["Más acústico", "Más contraste"],
  "variantes": [
    {
      "titulo": "Bajo sincopado",
      "descripcion": "El bajo deja espacio al ataque del requinto.",
      "concepto": "Interlocking",
      "cambios": {
        "pistas": [
          {"id":"d3", "nombre":"Bajo", "tipo":"bajo", "codigo":"n \"c3 ~ g2 ~\" # s \"superpwm\" # lpf 650"}
        ]
      }
    },
    {
      "titulo": "Bajo más sobrio",
      "descripcion": "Un pedal deja más protagonismo al motivo.",
      "concepto": "Espacio y contraste",
      "cambios": {
        "pistas": [
          {"id":"d3", "nombre":"Bajo", "tipo":"bajo", "codigo":"n \"c3 ~ ~ ~\" # s \"superpwm\" # lpf 650"}
        ]
      }
    },
    {
      "titulo": "Respuesta melódica",
      "descripcion": "Conserva el bajo e introduce una variación muy breve.",
      "concepto": "Motivo y respuesta",
      "cambios": {
        "pistas": [
          {"id":"d4", "nombre":"Respuesta", "tipo":"melodia", "codigo":"n \"~ e4 ~ g4\" # s \"superpiano\" # gain 0.7"}
        ]
      }
    }
  ],
  "skills": ["mc-tidal-studio"],
  "decisiones": [
    {"aspecto":"bajo", "skill":"mc-tidal-studio", "regla":"Evitar solapar continuamente ataques de bajo y motivo", "aplicado":"Variante A reubica silencios del bajo"}
  ]
}
```

This is **example data**. If a user's current track IDs, available synths, sampler names or permitted output shape differ, adapt rather than copying. Do not emit a partial ARR-SPEC as if it were `cambios`.

## Sound downloads

`descargar` requests from Maestro use `nombre`, `busqueda`, `tipo`, `duracion`, `alternativa`, `por_que`. The host searches pack and optional Freesound sources; may ask permission for large downloads; handles attribution and reload. Example:

```json
{"descargar":[{"nombre":"conga_abierta","busqueda":"conga open tone","tipo":"percusion","duracion":"golpe","alternativa":"perc","por_que":"Hace más expresivo el patrón de llamadas y respuestas"}]}
```

A third-party **SynthDef is code**. There is currently no automatic `install_synth` action in Tidal Studio, and sample download workflows do not vet/compile it. Built-in synth names are contingent on runtime registration.

## Tidal syntax and state

Prefer simple, testable patterns: `s "bd*4"`, `s "~ cp ~ cp"`, `n "c3 ~ g2 ~" # s "superpwm"`, `every 4 (fast 2) $ s "hh*8"`. `ho` is the conventional open hat; `# speed (-1)` requires parentheses for negative numbers. Do not emit a `dN $` prefix inside `codigo`, an invented `# orbit`, unsupported SuperCollider code or `setcps` inside track patterns. Tidal Studio creates and evaluates the surrounding track code.

## Future architecture (not implemented by this skill)

The optional ideal host feature is `composition plan (ARR-SPEC subset) → renderer/validator → Maestro changes → A/B playback`. A separate Python adapter, tests and runtime feedback would be needed. This skill provides musical intent and sound-selection criteria **without changing the host application**.
