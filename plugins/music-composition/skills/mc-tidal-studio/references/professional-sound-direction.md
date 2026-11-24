# Professional sound direction · instruments, samples, synths and performance

**Fundamental principle:** instrument *role and articulation* select the source. A beautiful preset is irrelevant if it cannot perform the phrase. The same written notes may sound authentic on a multivelocity accordion and unusable on a single pitch-stretched organ hit.

## Studio capabilities, verified from current code

Tidal Studio has:
- installed Dirt-Samples and the user's sample packs, Freesound/sample fetcher with license handling;
- an instrument catalog with General MIDI collections, VSCO/VCSL mapped sample instruments and custom sample banks; small sampled instruments can be downloaded by the host when chosen;
- a synth collection including SuperDirt synths and custom `ts_*` patches, plus available `supertrumpet`; installation/runtime support varies;
- optional engine installers for **sc3-plugins**, **Mi-UGens** (Plaits/Braids/Rings), **VSTPlugin**, and **Surge XT** integration; Vital may need an external account/installation;
- inventory checks and engine sound-list introspection; a patch listed in a catalog is **not automatically loaded** on the current machine.

The skill **does not** download or install these assets. The host API does. Never ask a sample fetcher to execute a third-party SuperCollider `.scd` script. Use only catalog names or sound IDs verified as active; avoid inventing `install_synth` JSON actions.

## Per-role sound requirements

| Function | Required sonic behavior | Likely solution | Failure if wrong |
|---|---|---|---|
| Güira | Long/short scraping textures, transient accent, controllable choke | Distinct real scrape samples | Constant hi-hat metallic clicks sound like electronic dance |
| Tambora | Head open/muted and rim attack families | Multiple mapped sample variants | One snare sample loses two-sided conversation |
| Accordion | Reed tone, short & longer notes, dynamic phrasing and playable register | Multi-sampled accordion, velocity/articulation mapping | Organ patch exposes fake identity |
| Electric/acoustic bass | Stable low pitch, damped short attacks/pickups | Multi-sample bass or synthesis when idiomatic | Long boomy tail masks fast dance groove |
| Salsa piano | Bright compact, responsive chord fragments, voiced correctly | Acoustic piano multi-sample | Sustained generic pad lacks dance definition |
| Requinto/segunda | Pick attack vs strum, muting, tonal register | Suitable guitar multi-sample | Static synth pluck cannot execute expressive guitar ornaments |
| Horn section | Distinct ranges, short vs held attacks, phrased breaths | Brass multi-samples or carefully voiced sketch | Fixed fake brass on every beat |
| Reggaeton sub | Controlled pitch, decay and narrow transient | `ts_sub` or supported sub synth | Low-frequency overlap with kick |
| Bossa guitar | Intimate nylon pluck and chord voice-leading | Nylon guitar sample/instrument | Synthetic chord stab changes genre |
| Timbales/congas | Correct strokes and resonant differences | Multi-articulation banks | All drums sound identical except for pitch |

## Selection algorithm for Maestro

1. Name **instrumental role**, not category ("tambora rim attack in chorus transition", not "drum").
2. Define expected register, pitch span, articulation, sample tail, number of velocity/timbre layers and solo-vs-section position.
3. Query **actual** runtime inventory and exact available IDs. Choose a current source; do not assume the host has installed everything it lists online.
4. Check if it can perform the notes. If multi-sample range is inadequate, simplify or choose an alternative.
5. Compare a **short phrase** in context. If mismatch, request one precise sample (free-license and attribution) or recommend explicit installed plugin.
6. Return a credible fallback and disclose the approximation; do not claim audible verification without audio.

## Samples versus synths versus loops

**Acoustic one-shots** suit drum hits and individual articulation, and should be distinct by strike type. **Pitched sample instruments** are better for expressive accordion, acoustic bass, horn or strings across multiple notes; note range, velocity and sustain mapping matter. **Built-in synth** is often best for reproducible electronic bass, pads and leads with envelopes/filter controls. **Full loops** must align bar count, tempo and harmonic key; they obscure the student's ability to learn individual parts, so favour decomposed elements in courses.

## Dynamic sound handoff and rights

When a sound is absent, `descargar` requests existing supported fields: `nombre,busqueda,tipo,duracion,alternativa,por_que`. The host's automatic instrument downloads are separately triggered by recognized catalog instrument IDs in generated code; **do not invent a unified downloader field**. Sample provenance, license restrictions and user approval for large downloads are host concerns, but mention when suitability depends on them. Do not sample a recognizable recording or musician voice without permission.

**Engine choice:** optional Mi-UGens and Surge XT expand the synthesis palette; they do not turn a synth into an authentic accordion. VST/UGen install may require restart and platform compatibility. Vital requires external steps in some installations. Prefer a source already present and working to an unreviewed installation. A missing synth may be a runtime/loading issue; inspect inventory first.

## Sound QA matrix

A/B *one* timbre at fixed notes, fixed tempo and same levels. Check: attack identity, intelligibility at tempo, release, pitch range, articulation change, masking in mix, room placement and perceived genre authenticity. Only then adjust EQ/reverb, which cannot repair incorrect note grammar.

Code provenance inspected: https://github.com/vsalesa/tidal-studio/blob/main/server/instcatalog.py ; https://github.com/vsalesa/tidal-studio/blob/main/server/instlib.py ; https://github.com/vsalesa/tidal-studio/blob/main/server/inventory.py ; https://github.com/vsalesa/tidal-studio/blob/main/server/engines.py .