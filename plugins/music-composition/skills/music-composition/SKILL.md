---
name: music-composition
description: Parent entry point for the whole music composition library (51 mc-* skills). Use for any request to compose, arrange, orchestrate, produce or critique popular music - writing a song from a brief, arranging for a band or orchestra, choosing chords or modulations, designing a vocal, turning an idea into a Suno / YuE2 / MIDI prompt, or auditing generated music. It indexes every child skill by layer and says which to load for which task, so none has to be added one by one. Keywords - song, arrangement, ARR-SPEC, composition, orchestration, harmony, melody, mix intent, Suno, style.
---

# Music Composition: parent skill

This skill is the front door to the whole library. It does not hold the rules itself. It tells you **which child skill to load for the task at hand**, so that installing the library once gives you every skill and you never have to pick them one by one.

## How to use it

1. **Start with `mc-workflow`.** It is the entry point and router: the S0-S7 stages from brief to delivered audio, the ARR-SPEC contract (the spec sheet every other skill reads and writes), and the full boundary table that says which skill owns which decision.
2. Follow its routing and load only the child skills the current stage needs. Each child has its own `SKILL.md`, and most have a `reference.md` for lookups.
3. For an isolated question (one chord progression, one modulation, one vocal problem), skip the workflow and go straight to the matching child skill in the index below.
4. Before accepting generated output, run `mc-ai-tell-audit`.

All child skills live next to this one under `skills/`, in directories named after the skill (for example `mc-melody/SKILL.md`). If the host lists them as separate skills, invoke them by name; otherwise read the file at that path.

## Index by layer

### Entry
| Skill | Use it for |
|---|---|
| `mc-workflow` | Any full song or arrangement job; routing; the ARR-SPEC schema, template and examples; the 20-point spec self-check |

### General craft (L1)
| Skill | Use it for |
|---|---|
| `mc-melody` | Writing or fixing a melodic line; singability, range, leaps, cadences |
| `mc-harmony` | Choosing and upgrading chords for a melody; substitutions, colour |
| `mc-progressions` | Looking up named chord progressions, mood reverse-lookup, variation techniques |
| `mc-modulation` | Moving between keys so the seam sounds intended |
| `mc-rhythm-groove` | Beat feel, syncopation, groove as musical material |
| `mc-form` | Song form, section terminology, building sections back from the chorus |
| `mc-counterpoint` | Writing a genuinely independent second line, countermelodies |
| `mc-development` | What the theme is and what each section does with it |

### Arrangement craft (L2)
| Skill | Use it for |
|---|---|
| `mc-arrangement-arch` | Energy curve, entry/exit events, subtraction, section proportion |
| `mc-orchestration` | Which instrument carries which line; Western and Chinese folk orchestra |
| `mc-texture-layering` | Space budget, foreground/background depth, spectral layering |
| `mc-rhythm-section` | Drums, bass and harmony instruments as one unit; MIDI programming |
| `mc-sound-design` | Deciding what a synth sound must be before touching a knob |
| `mc-vocal-direction` | How a vocal is delivered; harmony vocals |
| `mc-mix-intent` | Stating what the mix must achieve, as a handoff to an engineer or backend |

### Style layers (L3)
| Skill | Use it for |
|---|---|
| `mc-style-jpop` | J-pop, chorus-centred design |
| `mc-style-citypop-rnb` | City pop and R&B |
| `mc-style-jazz` | Jazz harmony and practice |
| `mc-style-latin` | Latin genre router: Afro-Caribbean, Brazil, Mexico, Colombia, tango, urban styles and contemporary fusion |
| `mc-style-chinese-pop` | Mandarin and Cantonese pop |
| `mc-style-edm` | EDM and club music |
| `mc-style-rock-band` | Rock and band-format music |
| `mc-style-cinematic` | Cinematic and hybrid orchestral |
| `mc-style-hiphop` | Hip-hop and trap |


### Latin genre subskills (L3 — route via `mc-style-latin`)
| Skill | Use it for |
|---|---|
| `mc-style-latin-salsa` | salsa composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-timba` | timba composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-bachata` | bachata composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-merengue` | merengue composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-reggaeton` | reggaeton composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-dembow` | dembow composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-cumbia` | cumbia composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-regional-mexicano` | regional mexicano composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-corridos-tumbados` | corridos tumbados composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-samba-pagode` | samba pagode composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-bossa-mpb` | bossa mpb composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-funk-brasileiro` | funk brasileiro composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-forro-piseiro` | forro piseiro composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-tango` | tango composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-bolero-pop` | bolero pop composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-vallenato` | vallenato composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-bomba-plena` | bomba plena composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-latin-jazz` | latin jazz composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-andino-afroperuano` | andino afroperuano composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-caribbean-soca-reggae` | caribbean soca reggae composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-cumbia-villera-sonidera` | cumbia villera sonidera composition, contemporary artist lenses and fusion boundaries |
| `mc-style-latin-fusion` | fusion composition, contemporary artist lenses and fusion boundaries |

Do not load every Latin child for a single brief; select the branch and load the fusion skill only when more than one tradition is intentionally combined.

When two styles are mixed, `mc-workflow` and the style skills' fusion-ownership rules decide which style owns which dimension.

### Execution
| Skill | Use it for |
|---|---|
| `mc-render-compile` | Compiling an ARR-SPEC into a prompt for Suno, YuE2 or other backends |
| `mc-symbolic-score` | Emitting ABC, MusicXML and MIDI from the spec |
| `mc-ai-tell-audit` | Auditing generated tracks for the default habits of generation models |

### Corpus
| Skill | Use it for |
|---|---|
| `mc-case-studies` | Checking a rule against real recordings; finding a worked example |

## Notes

- Answer in the language the user writes in. Scores and lyrics stay in their own language.
- Lyrics belong to the separate lyric-writing library. The two libraries meet only through the shared fields of the spec sheets (see `mc-workflow`).
- This parent skill adds nothing to the music rules. If this index and a child skill ever disagree, the child skill wins.
