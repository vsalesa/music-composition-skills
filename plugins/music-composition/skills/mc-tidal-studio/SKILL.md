---
name: mc-tidal-studio
description: "Expert knowledge for original composition and selecting the best instruments, synths and samples in vsalesa/tidal-studio's Maestro (TidalCycles, SuperDirt, SuperCollider). Use for any musical genre, Latin style, fusion, melody, harmony, groove, bass, arranging, composition quality, sound design or music improvement in Tidal Studio. Keywords: composición, mejor música, estilo, instrumentos, sintetizadores, samples, arreglos, producción, Tidal Studio, Maestro, calidad, fusion."
---

# Tidal Studio: compose the music first, choose the sound second

**Mission:** help Maestro make the **strongest coherent original music for the user's brief and selected genre**. A good-sounding demo requires a compelling motif, purposeful harmonic and rhythmic relationships, genre-defining roles, distinctive timbre, evolving form, and listening-led revision. Technically valid Tidal code alone is not evidence of musical quality.

**Boundary:** this is an **advisory skill**, not a downloader, installation script, new API or executable ARR-SPEC→Tidal compiler. [Tidal Studio](https://github.com/vsalesa/tidal-studio) already hosts Maestro, TidalCycles, SuperDirt, built-in synths, sample downloads and live A/B variants. **Existing session state, host JSON schema, supported Tidal functions, actual sound inventory, licensing and the user's directions take precedence.**

## Seven compositional gates (in this order)

1. **Identity.** Name the precise genre, era, rhythmic tradition and emotional intention. If fusion, assign each source a role (groove, harmony, voice, timbre or section) rather than layering genre presets.
2. **Musical seed.** Compose an **original, memorable 1–2-bar cell**: specific pitches or contour, accents, rhythm, rests and a primary instrument/voice. Give it a recognizable return with development, not another unrelated riff.
3. **Groove and bass.** Choose meter/cycle counting, syncopation, percussion subdivisions and bass movement. Define kick/bass relationship (locked, answering or interlocking). For salsa, bachata, cumbia, samba, timba etc., preserve actual genre-specific rhythmic roles; don't use a generic four-on-floor plus ethnic samples.
4. **Harmony and melody.** Define key/modal center, concrete chord sequence and harmonic rhythm, voice-leading and tension/release (or deliberate stasis); check melody and bass against chord tones/approaches. Don't randomize chord colour as a substitute for musical direction.
5. **Orchestration and timbre.** Give each part a **clear job**: pulse, bass, rhythmic harmony, lead hook, counterline, texture or transition. For each job specify attack/decay, register, articulation, timbre and required authenticity. Remove redundant tracks before adding new ones.
6. **Development.** Plan intro, phrase development, contrast/negative space, a payoff and an altered return. Make periodic variations meaningful, not a compulsory fill every four bars. Tidal loops must be arranged into musical form.
7. **Audition and revision.** For creative choices present **musically different** A/B options using Maestro's existing \`variantes\`; make falsifiable listening predictions. Exact user commands use \`cambios\` directly. Never assert "it sounds great" without hearing the actual audio.

**Quality check:** Is the hook memorable? Genre recognizable *without decorative samples*? Bass and percussion supporting each other? Harmony doing something intentional? Each instrument distinct? Form with contrast? Sound selection truly suited to the performance? Material original and cohesive? Diagnose the **most consequential** failure first and revise it before adding reverb or more tracks.

## Genre-aware choice, not a bank-name lookup

For each desired sound write mentally:
\`musical role → rhythmic/melodic behaviour → timbre + articulation + register → current source → fallback → audible reason\`.

- **Acoustic identity:** if a picked requinto, conga, bandoneon or accordion is central to the subgenre, a poor approximation can damage the result more than a simpler, honest arrangement. Prefer a suitable licensed sample if available, or explicitly flag the approximation.
- **Electronic identity:** where synthesis *is* the idiom (acid, techno, reggaeton sub, funk brasileiro), a tweakable built-in synth may beat an inflexible prerecorded loop. Optimize envelope, filter and bass-tail interaction.
- **Layering:** never add three similar pads, dual sub-basses or a constant drum loop behind a complete independent groove merely to sound "full".
- **Samples vs synths:** use a sampled one-shot for a specific acoustic attack or colour; a multi-sample pitched instrument when its register/articulation matters; a synth for controllable evolving electronic timbre; a loop only when its original rhythm/form fits and is musically transformed.

See [genre sound palettes](references/genre-sound-palettes.md) for concrete traditional-to-contemporary choices and [sound sourcing](references/sound-selection-and-acquisition.md) for a decision tree.

## Real Tidal Studio interface

Maestro returns **JSON**, not YAML or a pasted .tidal file. Recognized fields include \`mensaje\`, \`cambios\`, \`variantes\`, \`sugerencias\`, \`explicacion\`, \`opciones\`, \`reto\`, \`controles\`, optional \`descargar\`, and skill trace \`skills\`/\`decisiones\`. Follow the runtime system prompt for precedence.

- \`cambios.pistas\`: \`{"id":"d3","nombre":"Bajo","tipo":"bajo","codigo":"n \"c3 ~ g2 ~\" # s \"superpwm\" # lpf 650"}\`. **Only** the pattern after \`d3 $\`; \`d1\`–\`d12\` are valid IDs; supported types include \`percusion,bajo,armonia,melodia,textura,voz,fx\`.
- Use existing functions and names actually present in the sound library; avoid invented synths, banks, OSC or Tidal modifiers. Sample availability changes by installation. Current parser limits BPM to **40–220**.
- A/B \`variantes\` has 3–4 options, each with \`titulo,descripcion,concepto,cambios\`; normally change only 1–2 tracks per option to isolate the musical difference. Suggestions are **unapplied**.
- The host permits optional \`descargar\` requests for licensed sample acquisition; do not invent \`install_synth\`, \`sound_library_add\`, or \`arrspec\` output keys. The separate full ARR-SPEC framework is for *planning* until a real adapter is implemented.
- When music is not actually played (e.g., engine simulation mode), separate syntax/structure analysis from **audible** verification.

## Acquiring sounds: the capability boundary

**Reuse first:** installed Dirt-Samples, user samples/loops, installed packs and known-working SuperDirt synths. Maestro may request a missing sample using the studio's existing \`descargar\` fields (\`nombre,busqueda,tipo,duracion,alternativa,por_que\`); the host handles free-license selection, attribution, permission for large packs and sample reload. Request only sounds with a specific missing musical function and an actual fallback. Check the active sound inventory before naming a bank. A sample download is not a synthesizer installation.

**Synth choice:** the app already loads SuperDirt synths and its \`supercollider/studio-synths.scd\` (including custom fallback instruments). Use known-working synths; describe the desired oscillator, filter, envelope, modulation and performance articulation. Arbitrary third-party SynthDef code is **not** currently fetched, compiled or installed by Maestro. Treat that as future host engineering with explicit review, not as a completed action. See [sound selection and acquisition](references/sound-selection-and-acquisition.md).

## Specialist routing and host budget

For advanced technique read one relevant sibling: \`mc-style-latin-<genre>\`, \`mc-style-latin-fusion\`, \`mc-harmony\`, \`mc-development\`, \`mc-rhythm-section\` or \`mc-arrangement-arch\`. For whole-song planning \`mc-workflow\` may provide ARR-SPEC; do not force a full ARR-SPEC into a one-bar edit. Tidal Studio usually loads **two unpinned skills** per response, with a **24,000-character total** budget, **9,000-character per-file cap**, and one relevant reference per selected skill. These references are intentionally topic-specific. The original musical specialist should win where it has stronger genre evidence.

**Example (modern bachata + R&B):** keep the bachata requinto/segunda, güira, bongó and bass roles recognizable; give the requinto an original answer motif, add R&B harmonic colour/voice phrasing, reduce pads when the guitar responds, use existing usable plucked sounds before requesting one licensed guitar sample. Offer variants contrasting acoustic articulation vs extended chords; don't simply swap an 808 and call it fusion.

**Evidence:** artist case studies are techniques to analyze, not invitations to copy protected songs or identifiable living voices. Exact record BPM, measured microtiming and real-world session instrumentation require a source, not guesswork.
