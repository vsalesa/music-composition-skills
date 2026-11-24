# Original melody, harmony and counterline: high-quality candidate design

A correct scale fit is a **constraint**, not a composition. Good melodies have identity, rhythm, direction, short- and long-term expectation, expression and breathing room. Treat melody as its own form within a song form.

## Motif specification before note choice

Create an internal motif record:
- 1–2-bar **rhythmic silhouette**: note onsets, rests, syncopation and held landing.
- **Contour**: relative up/down/repeated direction, climax and comfortable instrument register.
- **Target degrees** against the local harmony: which arrivals are thirds/fifths/tonic, which are prepared colour or passing notes.
- **Question/answer**: answer echoes 1–2 distinguishing rhythmic/pitch features but resolves differently.
- **Characteristic sound**: picked/breath/sung note lengths, attack and expressive ornaments feasible for the chosen source.

If a candidate could be transposed into any genre without changing timing or expression, its *genre-specific* composition is likely weak. The melody must listen to the accompaniment.

## Four-bar professional phrase example (abstract, no borrowed tune)

- **Bar 1:** identity A; rhythm with one displaced accent and rest; establish tonal centre.
- **Bar 2:** answer B; change last two notes or pause in a different place; land near chord movement.
- **Bar 3:** A′; recognizable rhythm, altered pitch contour or register following a new chord.
- **Bar 4:** cadence/payoff; use a prepared rhythmic breath and target tonic/third or an intentional open ending.

Do not implement A′ by shifting all notes the same random interval; correct harmony-specific targets and preserve the **motivic relationship**. At a dominant-to-tonic turn, lead note resolution can be a small step; a random note from the global major scale may invalidate the tension.

## Generate and filter candidate melodies

**Candidate generation** should explore meaningful dimensions separately:
1. Original motive with plausible note targets for style and harmonic rhythm.
2. New **rhythmic phrasing** on the same pitch landmarks.
3. New **contour** on the same onset/rest map.
4. Developed version with sequence, inversion of contour, fragmentation or offset.
5. Contrasting counterline built explicitly in the *gaps* left by the lead.

Use deterministic chord-and-register checks to remove candidates with out-of-range notes, false pitch names, unwanted collisions or nonexistent section mapping. Then listen to survivors in the **complete** rhythm-section context, not only on solo piano.

## Harmony with purpose

Plan harmonic **rhythm** (how often chords change), not merely chord names. For a 4-bar cycle state what happens on bars 1–2 and why bars 3–4 provide departure/return or intentional vamp. Choose common tones and small movements in accompaniment voicings; clarify when chromatic approach or dominant secondary function is desired. Use chord extensions when they enrich the actual voice leading, not to cosmetically sound "professional".

- **Bachata:** guitar phrases and bass may favour an intimate, compact chord motion; rich R&B overlays must not clutter the picked guitar.
- **Merengue:** a simple progression can sound sophisticated through moving inner voices, anticipations and horn voicings.
- **Salsa:** piano guajeo rhythmic/harmonic motion across a declared clave direction is as important as chord sophistication.
- **Timba:** a gear change may be a better dramatic event than an extra reharmonization.
- **Bossa:** internal guitar voicing motion and sparse melodic phrasing dominate; dense percussion isn't compulsory.

## Countermelody and brass

Give the supporting voice a *defined function*: response, held pedal, inner-moving harmony, rhythmic punctuation, or independent contrasting line. Check register, melodic direction and rhythmic density against the lead. For a horn choir, choose voicing spacing and instrumental ranges; do not merely assign three copies of an identical note pattern to trumpet/sax/trombone. Separate melody arrivals from brass answer with real silence. Consonant thirds/sixths and occasional tension can help, but voiced harmony must be context-specific.

## Course-mode locked rhythm

Given fixed drums/bass/comping, keep their code and the BPM exactly unchanged. Extract a 4/8-bar **harmonic timeline** and accompaniment onset map. The new melody must have a phrase plan within exactly that duration and share the target harmonic arrivals, but it **need not accent every drum hit**. After generating A/B variants, enforce constraints programmatically when the host implements a validator. Until then, present it as a best-effort musical plan and do not pretend validation was executed.

## Common "algorithmic" failure modes

- nearest chord tone on every strong note → staircase melody;
- repeating the same short onset list in every section → predictable machine groove;
- every section starts on scale degree 1 → weak dramatic contour;
- no rests → no instrumental dialogue;
- no returning motif or one-to-one repetition → incoherence or fatigue;
- changing sample name while leaving the notes and articulations unchanged → timbral polish, not compositional improvement.

Review with one question: **What exact melodic shape would a human listener remember and recognize when it comes back?**

Related external examples (paraphrased, not copied): https://github.com/T-Rzeznik/reaper-composer ; internal `mc-melody`, `mc-development`, `mc-harmony`.