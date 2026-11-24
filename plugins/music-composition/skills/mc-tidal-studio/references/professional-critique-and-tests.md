# Professional producer QA · tests that reject "technically valid but musically weak"

A good composer **rejects and revises** weak candidates. These tests are structured editorial gates; no text-only skill can promise the quality of an unheard recording. The model's self-rating is not a trusted audio measurement.

## Three layers of verification

**Layer A — mechanically testable without sound**
- All generated tracks preserve IDs `d1`–`d12`, use known functions and actually loaded sounds where obtainable; syntax valid.
- BPM/meter/cycle and section duration consistent; no undesired changes to locked tracks.
- Chord name–pitch mapping valid; strong arrival notes have an explained harmonic relation; no unintended out-of-register part.
- Bass approach notes point to correct **next** harmony; note-off events and loop boundaries coherent.
- Two-bar clave direction consistent where relevant; no extraneous Cuban clave imputed to another genre.
- A/B alternatives are structurally distinct and preserve user-approved decisions.

**Layer B — arrangement-level editorial tests**
- Genre identity survives when lead/timbre decorations are muted.
- At least one convincing 1–2-bar motif appears, returns recognisably and changes in one musical dimension.
- Every line has a nonredundant job; call/response rests audible, no persistent duplicate foreground.
- Section energy or texture changes happen at intentional musical boundaries.
- Instrument range, articulation and phrase length are idiomatic enough for chosen source.
- The music does not masquerade a one-sample synth sketch as a fully realistic band.

**Layer C — requires real playback or user audio**
- Listen for bounce, controlled low end, instrument source believability and timbral balance.
- Compare full mix and reduced reference (groove only; bass/piano; lead only).
- Compare A/B at matched volume and same surrounding musical context; label subjective impression as listener evidence.
- Use timbral spectrum/LUFS measurements only if audio-analysis tools actually ran; don't invent them.

## Representative acceptance tests by genre

| Test prompt | Required result | Reject |
|---|---|---|
| "Merengue típico, con buen acordeón" | Distinct tambora head/rim, güira long/short, bass anticipation and short accordion statement/response | House kick with hi-hat + fake organ lead |
| "Merengue orquesta, nueva melodía" | Genre-correct percussion, original hook, horn phrasing and staged chorus/mambo | One synth-brass repeating 8 notes forever |
| "Salsa 2-3, 8 compases" | Declared two-bar clave direction, coherent bass/piano interplay and transitions | Clave sample laid over generic drum loop |
| "Timba con cambio de marcha" | Coordinated rhythm-section gear switch and clear hand-off | One random fill on a single track |
| "Bachata romántica" | Requinto/segunda complementary and guitar/bongó/güira interaction | Reggaeton + nylon preset |
| "Cumbia sonidera" | Recognisable keyboard/bass rhythmic identity and riff | Generic salsa clave + accordion |
| "Bossa íntima" | Guitar voicings, subtle rhythm and breathing melody | Pop house beat at low volume |
| "Reggaeton cambia el hook" | Controlled sub/dembow family with new hook and preserved rhythmic grammar | Replacing whole song when only hook requested |

## Evaluation protocol for a release or model change

1. Fix brief, installed sample inventory, tempo, base rhythm, optional MIDI reference and permitted edits.
2. Record 3–5 candidates per genre (with fixed seed where deterministic). Include a **baseline using current Studio release**.
3. Check Layer A automatically with the same fixture.
4. Blind A/B listening (minimum two independent listeners if feasible): identity, hook, groove, arrangement and sound. Record specific failures, not just "bad".
5. Review worst failures and classify as **knowledge / algorithm / renderer / sample / timing / sound engine**. Change one layer at a time.
6. Regression test multiple genres—fixing merengue must not worsen reggaeton, salsa or bossa.
7. Record approved choices and prevent model from rewriting them later.

## Rubric usable by an arranger

Use internal qualitative labels **insufficient / acceptable / distinctive** for: genre grammar, groove interaction, harmonic direction, motif identity, phrasing, part separation, sound realism, development and originality. Avoid magical aggregate "8.7/10 professional" claims. A piece can be harmonically simple and professionally effective; don't reward complexity over musical intention.

**First repair** policy: identify the lowest-performing critical domain. Missing tambora cannot be fixed by sophisticated reverb; weak lead motif not by expensive brass; implausible register not by random timing.

## Engineering implications

The Studio currently has `server/timeline.py` (Tidal event queries), `server/midigen.py` (template-based MIDI-driven song generation), `server/data/style_profiles.json` (small style-statistic reference corpus), and `server/inventory.py` (sound availability). The future evaluator should use their outputs as **data** and add constraint assertions + listening loop. The skill itself cannot instrument `scsynth` or run the tests automatically.

External inspiration on evaluators and versioned prompt regression: https://github.com/sb-dev/music-production-skills ; https://github.com/tomascabralh/prod-skills (see their self-review skill and tests/prompts.md).