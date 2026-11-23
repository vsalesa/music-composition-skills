# music-composition-skills

English · [中文版](README_ZH.md) · [日本語](README_JA.md) · [한국어](README_KO.md)

> **English-language fork with new Latin music extensions.** This repository builds on [jtydhr88/music-composition-skills](https://github.com/jtydhr88/music-composition-skills). Its original skill material was translated from Chinese into English; v1.1.0 adds 21 Latin genre subskills, a fusion skill, artist references and revised routing developed in this fork. Consult the cited originals for exact quotations and book titles. Original credits and the MIT license remain documented in [LICENSE](LICENSE) and [NOTICE](NOTICE).

**53 skill entrypoints (52 child skills + the parent router)** (for [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills) and [OpenAI Codex](https://developers.openai.com/codex/)) for composing and arranging popular music, distilled from 50 books on orchestration, harmony, form, counterpoint, mixing and style practice, plus 62 arrangements measured from multitrack recordings.

Both agents share the same files: install once and it works in both.

[Tidal Studio & Maestro](#tidal-studio-integration-v120) · [Latin expansion](#latin-music-in-v110-all-21-subskills) · [Install](#install)

**The output is a spec sheet.** Ask for a song and the agent fills in an ARR-SPEC (arrangement spec sheet): key, tempo, bar-accurate section map, chord letters and roman numerals, who enters and leaves when, the energy curve, vocal delivery, mix intent. It then compiles that one document into a Suno prompt, a score for YuE2, or a note file that loads into music software. The same document is what you check the result against. The whole design comes down to **one artifact, four uses**: handoff, controlled A/B, compile source, acceptance baseline.

**Ask in your own language.** In the original repository the skill bodies are written in Chinese, because most of the sources are Chinese originals or Chinese translations; in this fork they are translated into English. The agent answers in whatever language you ask in.

**These skills trade time for quality.** A full pass through a professional music workflow often takes twenty minutes or more for a single song (the agent reads the criteria, fills in the spec, runs the checklists). What you get in return is a professional-grade spec.

**This library ships no musical works at all, neither the author's own nor any other artist's, no arrangements and no lyrics.** Whether a piece of music is good is a subjective call. Use it yourself and judge for yourself what it is worth, and what it costs you in time.

## The four libraries in this series

One audio line, cut into four independent libraries. Each one is usable on its own; the seams between them are written down, so they also combine.

| Library | What it does | State |
|---|---|---|
| **[music-composition-skills (this fork)](https://github.com/vsalesa/music-composition-skills)** | Composing and arranging. A brief becomes an ARR-SPEC: key, tempo, section map, harmony, who enters and leaves when, the energy curve, vocal and mix intent, compiled into input for Suno, YuE2 or music software | **This library** |
| **[lyric-writing-skills](https://github.com/jtydhr88/lyric-writing-skills)** | Lyric writing. The intent gate becomes a LYR-SPEC (lyric spec sheet): structure, imagery, rhyme, narrative, plus the language layer for Mandarin, Cantonese, English, Japanese and Korean | Available |
| **Film scoring** | Music written to picture: spotting, the relation to cuts, how a cue is written and named, how a theme develops across a film | Planned |
| **Mixing and sound design** | Turning mix intent into actual moves: EQ, compression, reverb, automation, mastering | Planned |

**Independent.** Filling words to an existing melody needs the lyric library only. Arranging an instrumental needs the composition library only.

**Combinable, through named handoffs.** ARR-SPEC and LYR-SPEC share six fields: section id, bar count, section name, tempo, key, and who is singing. Whoever works first sets them and whoever works second only reads them: music-first, composition and arrangement set them; lyrics-first, the lyricist sets them, and line lengths and stress positions then constrain the bar counts. If the second side needs one of the six changed, it sends a message to the first side and re-reads once that side has made the change. Lyrics-first, tempo and key may be left empty for composition and arrangement to set. The mix intent written in an ARR-SPEC is what gets handed to whoever does the mix; a cue sheet from whoever scores the picture is the brief handed to composition and arrangement.

**The seams are written into the spec sheets.** Each library is self-contained and works when installed on its own; no skill names another library or assumes you have installed one. Anything a library does not own is handed to the role that does, named by its role: EQ and compression practice belongs to mixing, spotting and cue writing belong to film scoring. Libraries meet only through the spec sheet: its external-interface section lists the fields handed out and the upstream fields read when present, and there is a message channel any side may write to.

## Why this exists alongside a generative model

Arranging is a craft with decades of accumulated practice behind it. When to subtract before a lift, why a chorus sits higher, who owns the low end, whether the second verse should be emptier or fuller than the first: these judgements are written down across dozens of books, in several languages and traditions. **This library turns them into the decisions a professional arranger would make, in a form a generation model can be told.**

Suno and YuE2 will already turn one sentence into a finished-sounding track. What they are missing is those decisions. Whatever you leave unspecified, the model supplies from its own defaults, which is why unguided output tends to come back sounding like the same producer every time.

So what this library hands over is the decisions themselves: which bar the guitar leaves, which section drops a layer before the lift, where the energy falls, what the vocal does differently on the third chorus. **The point is to direct a generation model with expert-level rules.**

What that buys you is the part prompt engineering cannot reach. A prompt is a sentence, and you cannot check a sentence field by field. A spec sheet can be compared against what came back, changed one field at a time, and re-run for a controlled comparison. Every decision in it carries a reason and a source, so six months later you can still say why the second chorus is arranged the way it is.

The model stays the performer and the studio. This is the arranger's chart handed to it.

## What's new in v1.2.0: Tidal Studio

New [`mc-tidal-studio`](plugins/music-composition/skills/mc-tidal-studio/SKILL.md): an expert, **music-first composition and sound-selection skill** for [Tidal Studio](https://github.com/vsalesa/tidal-studio) and Maestro. It helps choose the best *original musical ideas* and the right instruments, synths and samples for each style, instead of merely producing plausible Tidal syntax.

The four targeted references explain [genre sound palettes](plugins/music-composition/skills/mc-tidal-studio/references/genre-sound-palettes.md), [sound selection and sourcing](plugins/music-composition/skills/mc-tidal-studio/references/sound-selection-and-acquisition.md), [composition-quality assessment](plugins/music-composition/skills/mc-tidal-studio/references/composition-review.md), and [Maestro's existing JSON/Tidal contract](plugins/music-composition/skills/mc-tidal-studio/references/maestro-contract.md). This release increases the package to **53 `SKILL.md` entrypoints (52 children + one parent)**.

## What's new in v1.1.0

**21 dedicated Latin genre skills and a fusion composer** join the original music-composition framework. You can now request salsa, timba, bachata, merengue, reggaeton, Dominican dembow, cumbia, corridos tumbados, regional Mexican music, samba, pagode, MPB, Brazilian funk, forró, tango, Latin jazz and other traditions **with their own musical roles**, rather than one generic `mc-style-latin` preset. The new references also distinguish historical foundations from contemporary innovations and artist-led crossovers.

- [Browse all 21 genre skills and the artist/fusion references](#latin-music-in-v110-all-21-subskills)
- [How contemporary fusion works](#dedicated-fusion-skill)
- [Copy working brief examples and an ARR-SPEC fragment](#practical-requests-and-routing)

The package now contains **52 `SKILL.md` entrypoints**: one parent index (`music-composition`) and **51 child skills**; 22 children were added for v1.1.0 (21 genres plus fusion). These are guidance files, not music samples or recorded tracks.

## Install

### Claude Code

#### Plugin marketplace (recommended)

```
/plugin marketplace add vsalesa/music-composition-skills
/plugin install music-composition@music-composition-skills
```

Skills are then invoked as `/music-composition:<skill>`, e.g. `/music-composition:mc-workflow`.

#### Personal (all projects)

```bash
git clone https://github.com/vsalesa/music-composition-skills.git
cp -r music-composition-skills/plugins/music-composition/skills/* ~/.claude/skills/
```

#### Project-specific

```bash
mkdir -p .claude/skills
cp -r music-composition-skills/plugins/music-composition/skills/* .claude/skills/
```

### Codex (CLI / ChatGPT desktop app / IDE extension)

```bash
codex plugin marketplace add vsalesa/music-composition-skills
# Then: Plugins → select "Music Composition Skills" → Install
```

Or copy the same files to `~/.agents/skills/` (personal) or `.agents/skills/` (project). The same skill directory is used by both plugin manifests; it contains 53 `SKILL.md` entrypoints (parent + children), with no duplicated skill tree.

**One entry skill.** `music-composition` is a parent skill that indexes all 52 child skills by layer and routes to them (it points to `mc-workflow` as the start). Installing the plugin, or copying the whole `skills/` directory, gives you all of them at once; you never need to add skills one by one.

#### Verify

Skills load automatically when the agent detects relevant context. To list them: `/skills`.

## Usage examples

```
# "Write me a city pop track about the last train home, three and a half minutes,
#  and give me everything I need to paste into Suno"
# → mc-workflow → mc-style-citypop-rnb → mc-arrangement-arch → mc-render-compile

# "This chorus doesn't lift. Fix the arrangement and leave the melody alone"
# → mc-arrangement-arch (energy curve, subtraction before the lift) + mc-texture-layering

# "Rap verses over a Chinese-style chorus, like a named song"
# → mc-workflow §2.4 fusion → mc-style-hiphop (base) + mc-style-chinese-pop (overlay)

# "The generated track sounds like AI but I can't say why"
# → mc-ai-tell-audit: fourteen enumerated tells, counted one by one

# "What drum pattern and tempo does a bossa nova need?"
# → mc-style-latin → mc-style-latin-bossa-mpb + mc-rhythm-section reference tables
```

## Common combinations

This is more involved than it looks. A one-sentence brief pulls in a dozen skills across composition, arrangement and lyrics, and what the agent reads and produces depends on whether that sentence names a few key things. Below are combinations that have actually been run end to end: how to say it, which skills it walks, what comes out. Anything with lyrics needs both the music library and the lyric library installed.

**1. A song with lyrics in the style of a named artist** (the most common case)

> Write a Mandarin pop song in the style of a named artist's song, female vocal, to be generated on Suno, with lyrics.

Walks: lw-workflow → lw-song-intent → lw-structure → lw-mandarin → lw-tone-check; mc-workflow → mc-style-chinese-pop → mc-melody → mc-development → mc-arrangement-arch → mc-vocal-direction → mc-render-compile
Produces: LYR-SPEC, ARR-SPEC, the pack you paste into Suno (title, style description, section-tagged lyrics, exclusions)
Note: the reference artist lends instrumentation, tempo, vocal persona and section layout. Never words or melody.

**2. A Douyin-style earworm, no storytelling**

> Write a Douyin earworm, female, sweet, no storytelling. Suno, with lyrics.

Walks: lw-song-intent (attitudinal) → lw-structure (repetition budget, hook placement) → lw-rhyme → lw-mandarin; mc-style-chinese-pop → mc-rhythm-groove → mc-arrangement-arch → mc-render-compile
Note: "no storytelling" is what sets the lyric type. Leave it out and you get a situational lyric by default.

**3. A sad love song that says it straight, no scenery**

> Write a sad love song like a named artist's ballad, male vocal, Suno, with lyrics. The kind that says it directly, no scene description.

Walks: as in 1, but lw-song-intent takes the attitudinal route and the anchor is a sentence (the line that opens every chorus); mc-vocal-direction handles the close-mic male voice and the bare final line
Note: in the corpus, four in ten attitudinal songs contain nothing you could photograph. The chorus is one sentence said to "you", the verses state how I am, the opener is a monologue. To get that, say "say it directly, no scenes, no objects" in the brief.

**4. A feeling, no story**

> Write a Mandarin pop song, three and a half minutes, female vocal. The subject: on moving day I left the charger cable in the wall socket, walked two blocks before remembering, and did not go back. Not a story. I want the feeling of remembering and letting it go.

Walks: lw-song-intent (situational, anchor object = the cable) → lw-imagery → lw-structure → lw-mandarin → lw-tone-check; music side as in 1
Note: this is the line between situational and narrative. There is an object; there is no plot advancing.

**5. An instrumental, composed from nothing**

> Write a two-minute-forty instrumental as a short-video bed. Lead is a nylon-string guitar, a little percussion and bass, one keyboard allowed. The feel is "three in the afternoon, waiting for someone, no hurry". No vocals.

Walks: mc-workflow → mc-development (motif, character, development devices) → mc-melody → mc-form → mc-harmony → mc-rhythm-section → mc-orchestration → mc-render-compile
Produces: ARR-SPEC (motif material and per-section development filled in), the Suno pack, a one-page note
Note: no lyrics, so the lyric library stays out. The criterion lives in mc-development: new material under half, and a return.

**6. Melody and words exist, arrangement only**

> Arrange a Mandarin love song whose melody and lyrics are already written. I want a salsa feel, with brass, medium-fast. Spec only, no Suno prompt.

Walks: mc-workflow (arrangement route) → mc-style-latin (router) → mc-style-latin-salsa → mc-rhythm-section → mc-orchestration (brass) → mc-arrangement-arch → mc-texture-layering
Produces: ARR-SPEC and a one-page note, nothing else

**7. Fusion: rap verses, Chinese-style chorus**

> Write a song like a named song, rap plus Chinese style, full Chinese lyrics, for Suno.

Walks: mc-workflow §2.4 fusion → mc-style-hiphop (base) + mc-style-chinese-pop (overlay); lw-rap (verses) + lw-chinese-style (chorus) + lw-mandarin

**8. Cantonese lyric to a given melody**

> Fill this melody with Cantonese lyrics. Bars and syllables per line are attached.

Walks: lw-workflow (music-first) → lw-cantonese (compute by pitch class first, then choose characters) → lw-tone-check
Note: Cantonese writes in the reverse order, and the Mandarin layer cannot stand in for it.

**9. Switching to a local open-source model (YuE2)**

> Same song, not through Suno. Generate it with local YuE2 and compile the spec into a score YuE2 can read.

Walks: as in 1, plus mc-symbolic-score (compiles ARR-SPEC into a score, with the vocal line and the lyric lines written into it)
Note: experimental. The share of lyrics that come out sung is currently below the path that passes a style description and the lyrics directly; details in mc-symbolic-score §6b.

The sentences in a brief that actually do something:

| What you say | What it decides |
|---|---|
| artist + song title | analyze high-level arrangement, groove, vocal *technique* and section design as references; never copy words, melody, recorded production or a living singer's identifiable voice |
| female / male, sweet / close-mic | persona and range in mc-vocal-direction |
| Suno / local YuE2 / spec only | the exit: the Suno pack, a score for YuE2, or ARR-SPEC alone |
| no storytelling / say it straight, no scenes / not a story | lyric type: attitudinal / attitudinal without objects / situational. Unsaid, situational is the default |
| duration | section count and bar count are derived from it |
| a list of deliverables | name the files you want and the agent produces exactly that list; one missing means not done |

Each of these takes twenty minutes or more to run in full, as described under "time for quality" above.

## No tooling required

The plugin is text only, with nothing extra to run. Every check in the library exists as a checklist you or the agent can walk through by eye: the twenty-point spec self-check in `mc-workflow` §3.0, the fourteen AI-tell flags in `mc-ai-tell-audit`, the per-skill "must pass before you finish" lists.

**The rules are criteria.** When a check does not pass, you either change the spec or write one line saying why this song should be that way. A deviation with a stated reason is a legitimate choice; nothing in the library blocks you from compiling.

## Multilingual support

**One source tree, every language at runtime.** The skill bodies in this English fork are maintained in English; the agent answers in the language you use. No per-language skills installation is required. README translations are separate and may need updates after a release.

Skills are not duplicated per language: 53 `SKILL.md` entrypoints and their supporting references share one implementation. Keeping several translated skill trees synchronized would create substantial maintenance overhead. The new v1.1.0 Latin skill content is documented in English, while agents may respond in Spanish, English or other requested languages.

How the runtime covers it instead:

- **Output language follows your question.** Ask in Japanese, get Japanese. The chart, the section names and the reasoning all come back in that language.
- **Terminology is anchored to the original term.** This field's vocabulary is a mix of English, Italian, German and Japanese in the original: *tension*, *avoid note*, *comping*, *build*, *drop*, 落ちサビ, 打ち込み. The Chinese in the source books is itself a translation, and different translators chose differently, so the original term travels with the concept.
- **Terms with no equivalent keep their original form plus a gloss.** 落ちサビ, 符割り, 類音階 and 十三辙 come through as the original plus a short explanation.
- **Your score and your lyrics stay in their own language.** Discussing a Chinese song in English is normal. What switches is the language of the conversation.

The primary skill files of this fork can be inspected directly in English. For exact musical assertions, verify the cited source or recording rather than relying only on a skill's summary.

**README translations** are provided for convenience, but v1.1.0 Latin additions may not yet be reflected in every translated README.

## How the skills are organised

Six layers. A layer only knows about the layers below it, and every skill carries a boundary table saying what it does **not** own. That table is what keeps a style layer from quietly rewriting general harmony.

```
L0 workflow      router, the ARR-SPEC contract, fusion ownership, the stage map
L1 general       melody · harmony · progressions · modulation · rhythm · form · counterpoint
L2 arrangement   architecture · orchestration · texture · rhythm section · sound design · vocal · mix intent
L3 style         J-pop · city pop & R&B · jazz · Mandarin pop · EDM · rock · cinematic · hip-hop · Latin (21 genre skills + fusion)
L4 execution     compile to backends · symbolic score · AI-tell audit
L5 corpus        measured recordings that testify for or against the textbook rules
```

### L0: entry point

| Skill | What it covers |
|---|---|
| `mc-workflow` | Router and stage map (intent → skeleton → melody & harmony → roster → vocal & mix → compile → generate → accept). Owns the **ARR-SPEC** schema, the empty template, the backend capability file, three worked examples, the twenty-point self-check, and the **style fusion** rules: which skill signs for harmony, which for groove, which for low end |

### L1: general craft (style-independent)

| Skill | What it covers | Main sources |
|---|---|---|
| `mc-melody` | What a line expresses and how to make it singable: range and tessitura, motif and development, peak placement, the reason a chorus sits higher | Schoenberg, Kachulis, 杨儒怀 |
| `mc-harmony` | Function and colour: the three functions, cadence types, reharmonisation without over-cooking, available tensions and avoid notes with Levine's chord-scale judgement kept beside the Japanese pop practice | 斯波索宾, Levine, Kachulis, 任达敏 |
| `mc-progressions` | 122 named progressions with letters and roman numerals, the eight famous ones, what each implies about form | Japanese progression corpus, 任达敏 |
| `mc-modulation` | Moving between keys so the seam sounds intended: pivot chords, the buffer-chord route, direct lifts and when they are cheap | 黄虎威, Japanese modulation practice |
| `mc-rhythm-groove` | Rhythm as material before anyone plays it: subdivision, syncopation, anticipation, push and pull | DeSantis, Japanese basics |
| `mc-form` | Section design and the standard templates, Japanese section naming, why every section being a multiple of eight is the most audible default | 吴祖强, 李吉提, 杨儒怀 |
| `mc-counterpoint` | A second line that is genuinely independent: four complementarity axes, the five species, voice-leading checks, invertible counterpoint for varying a repeat | 于苏贤, Schoenberg, 赵晓生 |
| `mc-development` | How one motif grows into a phrase, a section and a whole song: the ten development devices (repeat, sequence, extend, contract, fragment, vary, augment, counterpoint, new, recap), the line between developing and piling up, and the two items it fills in, motif material and per-section development | Yang Ruhuai, Schoenberg *Fundamentals*, Li Jiti |

### L2: arrangement craft

| Skill | What it covers | Main sources |
|---|---|---|
| `mc-arrangement-arch` | The shape of a track over time: energy curve, subtraction events, entry and exit, the arrangement hook. Five rules verified against 62 measured recordings | 文海良, measured corpus |
| `mc-orchestration` | Which instrument carries which line, pure versus mixed timbre, balance by register and count, for western orchestra **and** Chinese folk orchestra (four sections, group combination, score order, transposing instruments) | Adler, 杨立青, 杨春林, 朱晓谷, 李民雄 |
| `mc-texture-layering` | Arranging as a space budget: foreground/middle/background depth, the critical band as the real unit of masking, why two instruments a fifth apart in the low register fight | Izhaki, Howard & Angus |
| `mc-rhythm-section` | Drums, bass and harmony instruments as one unit: the five-step pattern decision (style & feel → tempo band → backbeat position → kick-bass relation → cymbal subdivision), eleven style tables with tempo ranges | Drummer's Bible, Groove Essentials, DeSantis |
| `mc-sound-design` | Deciding what a sound must be before touching a synth: 99 technique recipes, the brief-first discipline | 野崎貴朗 |
| `mc-vocal-direction` | How a vocal should be delivered and stacked: persona, per-section dynamics, pitch policy (where it is allowed to be imperfect), harmony types and panning | Japanese vocal production practice |
| `mc-mix-intent` | What a mix must achieve, stated so a human engineer, a DAW or a generative backend can all act on it. It does not prescribe EQ or compression | Izhaki, Howard & Angus |

### L3: style layers

Existing style layers carry transfer tables; the new Latin genre layers also describe regional lineage, composition roles, modern artist innovations and testable fusion decisions.

| Skill | What is specific to it | Main sources |
|---|---|---|
| `mc-style-jpop` | Chorus-centred design discipline, 落ちサビ, the section-contrast rules | Japanese arranging practice |
| `mc-style-citypop-rnb` | Borrowed jazz harmony over pop form plus a specific timbre set; the worked example spec is this style | measured corpus, L1 harmony |
| `mc-style-jazz` | What is jazz-specific: head form, standards, comping, modal thinking | Levine, Valerio, 爵士和声 |
| `mc-style-latin` | Router for 21 specialized Latin style skills, from Afro-Caribbean rhythms to regional Mexican, Brazil, tango and contemporary urban/fusion; preserves legacy rhythm references | Drummer's Bible, Groove Essentials, selected genre studies and ongoing recording analysis |
| `mc-style-chinese-pop` | Mandarin and Cantonese pop: what the tone system does to arrangement, the Cantonese layer, era differences | 同一首歌 corpus, 黄志华 |
| `mc-style-edm` | Form built on layer addition and subtraction: build, drop, tension devices | 竹內一弘, 野崎, measured corpus |
| `mc-style-rock-band` | What changes when five people in a room must play it: the roster as a hard constraint, riff as primary hook (Rooksby's 30 riff types, the 3+1 repetition pattern, riff versus vocal), twin guitars, drop D | Rooksby *Riffs*, measured corpus |
| `mc-style-cinematic` | Hybrid orchestral scoring at the arrangement level, depth and colour design | Adler, 杨立青 |
| `mc-style-hiphop` | Beat-first music: the third time-feel (Dilla), per-voice quantisation, 808 versus kick, sample-based texture and the producers' craft ethics, rap versus sung delivery | Charnas *Dilla Time*, Schloss *Making Beats*, *How to Rap* 1 & 2 |

### L4: execution and verification

| Skill | What it covers |
|---|---|
| `mc-render-compile` | One compiler, many backends. What each backend can and cannot honour is kept as **data** in a capability declaration, so a field the backend cannot act on is never held against it. Adding a model only takes adding a data block |
| `mc-symbolic-score` | Compiles ARR-SPEC straight into scores and note files, every format written by the same converter. On this path the spec is **executed** |
| `mc-ai-tell-audit` | Fourteen enumerable tells of machine-made music, counted individually. Keeps two questions apart on purpose: *did the backend do what the spec said*, and *does the result carry machine fingerprints*. A track can pass the first and fail the second |
| [`mc-tidal-studio`](plugins/music-composition/skills/mc-tidal-studio/SKILL.md) | Musical quality and genre-specific instrument, synthesizer and sample decisions for Maestro in Tidal Studio; uses existing JSON, downloads and A/B variants |

### L5: corpus

| Skill | What it covers |
|---|---|
| `mc-case-studies` | How recordings are made to testify. 62 arrangements measured from multitrack sources and written back as ARR-SPECs, so a textbook claim can be checked against a hit rate. **The corpus is a natural sample.** It is not curated, because curating it would bias it toward the rules you already believe |

## What ships in the package

Text only: 52 child skills plus one parent entry skill, the reference files that hold the long tables, and six specification files inside `mc-workflow`:

| File | What it is |
|---|---|
| Spec sheet definition | Every field, what it is for, what it is fighting |
| Empty template | Copy it and fill it in |
| Backend capabilities | What each backend can honour |
| Example 1: city pop | A complete worked spec, all twenty checks passing |
| Example 2: fusion | Rap over a Chinese-style base, with the ownership table |
| Counter-example | What a model writes with no guidance, and which eight checks it fails |


## Tidal Studio integration (v1.2.0)

[Tidal Studio](https://github.com/vsalesa/tidal-studio) already runs TidalCycles + SuperDirt + SuperCollider, provides a music-teaching AI named **Maestro**, plays auditionable options, and has a sound library with downloaded sample packs, optional Freesound and built-in synths. The new [mc-tidal-studio skill](plugins/music-composition/skills/mc-tidal-studio/SKILL.md) gives Maestro *expert musical judgment* for making the **best possible original composition for the selected style**.

### What the skill actually does

| Decision | Music-first rule | Existing Studio feature |
|---|---|---|
| Style | Choose the exact regional/era idiom and its bass–percussion / instrument relationships, not a generic "Latin beat" | Plugin's genre subskills and Maestro context |
| Composition | Write a memorable original motif, meaningful chord/voice-leading decisions and a clear groove | Tidal patterns, tracks, melody and harmony tools |
| Arrangement | Assign every instrument a job; develop sections with response, subtraction, tension and payoff | Timeline, arrangement, mixer |
| Sonic palette | Specify attack, release, articulation, register and timbre before choosing a bank | Available Dirt-Samples, synths, user banks |
| Missing sounds | Use an existing resource first, request a specifically justified licensed sample if essential | Studio's already supported \`descargar\` and sample library |
| Revision | Test musical A/B choices and fix structural flaws before polishing effects | Existing \`variantes\` and listening interface |

**Selection sequence:** musical role → rhythmic/melodic behaviour → timbre/articulation → installed playable source → fallback → audible revision. For traditional bachata, for example, Maestro should build a recognisable requinto/segunda–bongó–güira–bass dialogue before adding R&B colours. For reggaeton sub-bass or techno, a controlled synth envelope may be better than downloading an acoustic loop. For cumbia or salsa percussion, a well-recorded licensed one-shot may significantly improve stylistic identity.

The [genre palettes](plugins/music-composition/skills/mc-tidal-studio/references/genre-sound-palettes.md) cover salsa, timba, bachata, merengue, reggaeton, Dominican dembow, cumbia, regional Mexican, corridos tumbados, samba, pagode, bossa, MPB, Brazilian funk, forró, tango, Latin jazz, Andean/Afro-Peruvian traditions, plus electronic, jazz, hip-hop, rock and cinematic music. For the full lineage and artist case studies, pair this skill with a genre-specific \`mc-style-*\` skill.

### Downloads and synthesizers: two different capabilities

- **Audio samples:** Maestro can already request them using the existing \`descargar\` JSON fields (\`nombre\`, \`busqueda\`, \`tipo\`, \`duracion\`, \`alternativa\`, \`por_que\`). The *app* handles catalog search, license/credits, asking permission for large downloads, loading into SuperDirt and fallbacks. The skill itself performs **no downloads**.
- **Synthesizers:** Studio already loads suitable SuperDirt synths and its own [\`studio-synths.scd\`](https://github.com/vsalesa/tidal-studio/blob/main/supercollider/studio-synths.scd). The skill chooses musical synthesis characteristics and a **runtime-confirmed working** instrument. **It cannot download, vet, compile or install third-party SuperCollider SynthDefs**: no such automatic host workflow exists yet.

### Real examples to ask Maestro

- "Compose an original modern bachata with R&B harmony and the best guitar sound already available; download a licensed requinto only if needed."
- "My salsa feels generic: fix the clave-aware bass, piano and brass conversation before adding instruments."
- "Write a melodic techno build with an original hook, evolving synthesizer timbre and an intentional breakdown."
- "Make three *musically different* cumbia variations, preserving the Colombian bass groove while exploring distinct lead instruments."

**Routing:** Maestro → \`mc-tidal-studio\` + the most relevant genre or craft skill → compatible \`cambios\`, \`variantes\`, optional \`descargar\` → playback and revision. A full ARR-SPEC is optional planning material; Studio does **not** directly accept its YAML as changes. Consult the [Maestro compatibility guide](plugins/music-composition/skills/mc-tidal-studio/references/maestro-contract.md).

### Installing and updating in Tidal Studio

The application already lists \`https://github.com/vsalesa/music-composition-skills\` as a default plugin. **New installations** can download v1.2.0, but **previously installed copies do not automatically update** just because GitHub changed (the studio tracks completed default installs). Open Studio's **Plugins** panel, remove the old Music Composition plugin and reinstall from the repository URL, then check that \`mc-tidal-studio\` is enabled in the **Skills** panel. Keep the agent's skill context budget in mind: Studio currently loads up to **two unpinned skills** per response and limits each loaded skill/reference to 9,000 characters (24,000 total).

**Verified scope:** this adds a skill and documentation to \`music-composition-skills\`, **not** a new Tidal Studio server feature. There is no automatic SynthDef installation, guaranteed acoustic sound fidelity, or comprehensive playback test. The existing studio's code/JSON validation and actual sound availability remain authoritative.


## Latin music in v1.1.0: all 21 subskills

The Latin layer was expanded from a single, mostly percussion-focused essay into a **router + 21 focused genre skills + a dedicated fusion skill**. Unlike a generic “Latin” preset, each genre distinguishes its historical lineage, rhythmic grammar, bass role, lead/chorus structure, instrumentation, modern production and characteristic failure cases.

Start with [`mc-style-latin` (router)](plugins/music-composition/skills/mc-style-latin/SKILL.md). It will select one or more of these children; you **do not** need to load them all. Click any subskill below to read the actual composition rules. Each genre also has a `references/artists-fusion.md` file with artists, innovations and compositional A/B exercises.

### Afro-Caribbean, Puerto Rico and Dominican Republic

| Subskill | What it teaches | Artist lenses (examples) |
|---|---|---|
| [`mc-style-latin-salsa`](plugins/music-composition/skills/mc-style-latin-salsa/SKILL.md) | Son, mambo, salsa dura / romántica; clave, tumbao, guajeo, brass moñas, coro–pregón | Willie Colón, Rubén Blades, Eddie Palmieri, Celia Cruz, Marc Anthony |
| [`mc-style-latin-timba`](plugins/music-composition/skills/mc-style-latin-timba/SKILL.md) | Cuban songo and timba; gear changes (marchas), bloques, bass/keyboard/percussion interaction | Los Van Van, Changuito, NG La Banda, Cimafunk |
| [`mc-style-latin-bachata`](plugins/music-composition/skills/mc-style-latin-bachata/SKILL.md) | Traditional, electric, New York urban and pop bachata; requinto/segunda, bongó, güira | Antony Santos, Juan Luis Guerra, Aventura, Romeo Santos, Prince Royce |
| [`mc-style-latin-merengue`](plugins/music-composition/skills/mc-style-latin-merengue/SKILL.md) | Merengue típico, orchestral, pop and merengue-house; tambora/güira and horns/accordion | Johnny Ventura, Wilfrido Vargas, Elvis Crespo, Omega |
| [`mc-style-latin-reggaeton`](plugins/music-composition/skills/mc-style-latin-reggaeton/SKILL.md) | Roots, underground, perreo, melodic and experimental reggaeton; dembow-derived drums, vocal cadence, 808 | Ivy Queen, Daddy Yankee, Tego Calderón, Tainy, Bad Bunny, Rauw Alejandro |
| [`mc-style-latin-dembow`](plugins/music-composition/skills/mc-style-latin-dembow/SKILL.md) | Dominican dembow and trapbow; rapid beat/vocal exchanges and edited percussion | El Alfa, Tokischa, Chimbala |
| [`mc-style-latin-bomba-plena`](plugins/music-composition/skills/mc-style-latin-bomba-plena/SKILL.md) | Distinct Afro-Puerto Rican bomba and plena practices; dancer/drum dialogue vs pandereta ensemble | Rafael Cepeda, Plena Libre, Los Pleneros de la Cresta |
| [`mc-style-latin-caribbean-soca-reggae`](plugins/music-composition/skills/mc-style-latin-caribbean-soca-reggae/SKILL.md) | Calypso, soca, ska, reggae and dancehall; consciously distinct Caribbean traditions | Machel Montano, Bob Marley, Sly & Robbie |

### Colombia, Mexico and regional Latin America

| Subskill | What it teaches | Artist lenses (examples) |
|---|---|---|
| [`mc-style-latin-cumbia`](plugins/music-composition/skills/mc-style-latin-cumbia/SKILL.md) | Colombian roots plus regional and electronic cumbia; bass cycle, percussion and regional melodic lead | Totó la Momposina, Los Mirlos, Bomba Estéreo |
| [`mc-style-latin-cumbia-villera-sonidera`](plugins/music-composition/skills/mc-style-latin-cumbia-villera-sonidera/SKILL.md) | Mexican sonidera and Argentine cumbia villera; DJ/MC, keyboard/accordion and dance bass | Los Ángeles Azules, Damas Gratis |
| [`mc-style-latin-vallenato`](plugins/music-composition/skills/mc-style-latin-vallenato/SKILL.md) | Paseo, son, merengue vallenato and puya; accordion, caja, guacharaca and pop-rock adaptation | Diomedes Díaz, Carlos Vives, Silvestre Dangond |
| [`mc-style-latin-regional-mexicano`](plugins/music-composition/skills/mc-style-latin-regional-mexicano/SKILL.md) | Ranchera, mariachi, norteño, banda and sierreño; meters and instrument-specific roles | Vicente Fernández, Los Tigres del Norte, Banda El Recodo, Carín León |
| [`mc-style-latin-corridos-tumbados`](plugins/music-composition/skills/mc-style-latin-corridos-tumbados/SKILL.md) | Corrido/sierreño songwriting with modern urban rhythm and vocal cadence | Natanael Cano, Junior H, Peso Pluma, Fuerza Regida |
| [`mc-style-latin-andino-afroperuano`](plugins/music-composition/skills/mc-style-latin-andino-afroperuano/SKILL.md) | Andean huayno and Afro-Peruvian landó/festejo as separate lineages; regional instruments and percussion | Susana Baca, Eva Ayllón, Los Kjarkas |

### Brazil

| Subskill | What it teaches | Artist lenses (examples) |
|---|---|---|
| [`mc-style-latin-samba-pagode`](plugins/music-composition/skills/mc-style-latin-samba-pagode/SKILL.md) | Samba, partido alto, samba-enredo and pagode; surdo, pandeiro, cavaquinho and coro | Cartola, Fundo de Quintal, Zeca Pagodinho, Thiaguinho |
| [`mc-style-latin-bossa-mpb`](plugins/music-composition/skills/mc-style-latin-bossa-mpb/SKILL.md) | Bossa nova, MPB and tropicalismo; guitar–voice counterpoint and Brazilian pop evolution | João Gilberto, Tom Jobim, Elis Regina, Caetano Veloso, Liniker |
| [`mc-style-latin-funk-brasileiro`](plugins/music-composition/skills/mc-style-latin-funk-brasileiro/SKILL.md) | Funk carioca, tamborzão, funk melody and pop crossover; programmed percussion and bass | DJ Marlboro, Anitta, Ludmilla |
| [`mc-style-latin-forro-piseiro`](plugins/music-composition/skills/mc-style-latin-forro-piseiro/SKILL.md) | Baião, xote, forró and piseiro; zabumba, triangle, accordion and keyboard-led production | Luiz Gonzaga, Dominguinhos, João Gomes |

### Rio de la Plata, romantic songwriting and cross-regional jazz

| Subskill | What it teaches | Artist lenses (examples) |
|---|---|---|
| [`mc-style-latin-tango`](plugins/music-composition/skills/mc-style-latin-tango/SKILL.md) | Tango, milonga, nuevo tango and electrotango; marcato, bandoneon and dramatic phrasing | Carlos Gardel, Astor Piazzolla, Gotan Project, Bajofondo |
| [`mc-style-latin-bolero-pop`](plugins/music-composition/skills/mc-style-latin-bolero-pop/SKILL.md) | Bolero, romantic Latin pop and rock en español; narrative melody, vocal dynamics and orchestration | Los Panchos, Juan Gabriel, Shakira, Natalia Lafourcade |
| [`mc-style-latin-latin-jazz`](plugins/music-composition/skills/mc-style-latin-latin-jazz/SKILL.md) | Afro-Cuban, Brazilian and other Latin-jazz branches; interplay with improvisation and jazz harmony | Tito Puente, Chucho Valdés, Paquito D'Rivera, Michel Camilo |

### Dedicated fusion skill

[`mc-style-latin-fusion`](plugins/music-composition/skills/mc-style-latin-fusion/SKILL.md) combines genres **by musical responsibility**, not by stacking complete drum loops. Examples include salsa + reggaeton, bachata + R&B, cumbia + electronic music, corridos tumbados + trap, Brazilian funk + pop, and tango + electronic music.

It distinguishes three compositional strategies:

1. **Superposition:** one genre owns the rhythm and low end; another supplies harmony, vocal phrasing or timbre. Example: bachata guitars + R&B vocal harmonies.
2. **Alternation:** the song changes rhythmic engine between clearly marked sections. Example: a salsa coro followed by a reggaeton breakdown, joined by a shared melodic motif.
3. **Transformation:** the same motif changes accent, instrumentation or harmonic function gradually. Example: a regional guitar phrase moving into a programmed urban arrangement.

**Compatibility caveat:** `ARR-SPEC v1.0` assigns style dimensions globally. Section-by-section ownership changes are documented via existing `form[].note`, `form[].events` and `meta.fusion_note`; there is **no** new section-local YAML field. For a complete reference, see [`mc-workflow/ARR-SPEC.schema.md`](plugins/music-composition/skills/mc-workflow/ARR-SPEC.schema.md) and the [fusion skill](plugins/music-composition/skills/mc-style-latin-fusion/SKILL.md).

### What artist studies add

A reference to **Aventura**, **Los Van Van**, **Carlos Vives**, **Bomba Estéreo**, **Tainy**, **Astor Piazzolla**, **Bad Bunny** or **Karol G** should become **explicit arrangement choices**, rather than a generic request to “sound like” the artist. The genre reference describes the historical idea, its impact on groove/harmony/melody/vocal production and a testable way to borrow a **technique** without reproducing the original recording.

The cases are *research and composition prompts*, **not note-for-note transcriptions or a new measured recording corpus**. Track-level BPM, key, performer credits, recording settings and exact rhythmic placements require a primary recording, score, or reliable credited source; do not invent them.

### Practical requests and routing

| Ask the agent | Typical path |
|---|---|
| “Compose salsa dura: trombone moñas, piano montuno, coro–pregón and a break before the final coro.” | `mc-workflow` → `mc-style-latin` → `mc-style-latin-salsa` → `mc-arrangement-arch` |
| “Write a contemporary bachata with a requinto hook and R&B vocal harmonies.” | `mc-workflow` → `mc-style-latin-bachata` + `mc-style-citypop-rnb` + `mc-style-latin-fusion` |
| “Build psychedelic Amazonian cumbia with electric guitar and electronic transitions, keeping the cumbia bass pattern.” | `mc-workflow` → `mc-style-latin-cumbia` + `mc-style-latin-fusion` |
| “Compose a corrido tumbado where the guitar drives the verse and trap production enters in a later section.” | `mc-workflow` → `mc-style-latin-corridos-tumbados` + `mc-style-hiphop` + `mc-style-latin-fusion` |
| “Turn a tango motif into electrotango without losing bandoneon phrasing.” | `mc-workflow` → `mc-style-latin-tango` + `mc-style-latin-fusion` |
| “Analyze what modern artists changed relative to classic samba or pagode.” | `mc-style-latin-samba-pagode` → `references/artists-fusion.md` (no full workflow needed) |

#### Example: describe a contemporary crossover in ARR-SPEC

This illustrates the **style ownership fragment only**, not a complete ARR-SPEC:

```yaml
meta:
  style_layer: mc-style-latin-bachata
  style_layers:
    - skill: mc-style-latin-bachata
      role: base
      owns: [groove, low_end, instrumentation, arrangement_hook]
    - skill: mc-style-citypop-rnb
      role: overlay
      owns: [harmony, melody, vocal_delivery, timbre]
  fusion_note: "Bachata guitars and bongó/güira hold the groove; R&B supplies harmony and vocal phrasing."
```

Keep the selected branch identifiable: specify the lead instrument's musical role, the bass/percussion relationship, a variation of the hook and an instrument subtraction event. Use valid enum values (`arrangement.groove.feel: straight`, not `straight16`; `bass_kick_relation.mode: interlocking`, not `bound`).

### Backward compatibility, provenance and current limitations

- **Existing installations and prompts:** `mc-style-latin` remains available but now routes to its specialized children. Other `mc-*` skills and the ARR-SPEC v1.0 contract remain in place.
- **Original study retained:** the former book-derived Latin essay is archived within the repo at [`mc-style-latin/references/legacy-style-essay.md`](plugins/music-composition/skills/mc-style-latin/references/legacy-style-essay.md), alongside [`reference.md`](plugins/music-composition/skills/mc-style-latin/reference.md). Older assertions about prohibiting Brazilian/Cuban fusion and outdated ARR-SPEC paths should not override the new routing or schema.
- **Version:** `plugins/music-composition/.claude-plugin/plugin.json` is `1.1.0`. The v1.0.0 code snapshot is preserved at [`backup/v1.0.0-before-latin-expansion`](https://github.com/vsalesa/music-composition-skills/tree/backup/v1.0.0-before-latin-expansion); this is a **branch**, not a Git tag.
- **Testing:** structure, skill paths and schema descriptions were checked, but the genre-specific recommendations have **not** been validated by systematically generating and measuring audio for every new skill.
- **Translated READMEs:** the English README is the source of truth for this fork's v1.1.0 additions; other language README versions may lag until their translations are updated.

## Source books

**Orchestration and instrumentation (10):** Samuel Adler *The Study of Orchestration* vols 1–2; 杨立青《管弦乐配器教程》上中下; Pejrolo & DeRosa *Acoustic and MIDI Orchestration for the Contemporary Composer*, English edition and the Chinese translation《现代音乐人编曲手册》; 杨春林《中国民族管弦乐配器法教程》; 朱晓谷《民族管弦乐队乐器法》; 李民雄《民族管弦乐总谱写法》

**Harmony, counterpoint and theory (11):** 斯波索宾《和声学教程》; Schoenberg *Theory of Harmony* and *Fundamentals of Musical Composition*; Mark Levine *The Jazz Theory Book*; 任达敏《流行音乐与爵士乐和声学》; 于苏贤《复调音乐教程》; 黄虎威《转调法》; Madeleine Richardson *Modes and their Harmony*; 赵晓生《巴赫平均律键盘曲集结构分析版》; 李重光《基本乐理》; 爵士和声（流行音乐学院系列）

**Form and songwriting (9):** 吴祖强《曲式与作品分析》; 李吉提《曲式与作品分析》; 杨儒怀《音乐的分析与创作》上下; 中央音乐学院《曲式与作品分析课程谱例集》; 《论曲式与音乐作品分析》; 朱敬修《歌曲写作基础》; Jimmy Kachulis *The Songwriter's Workshop: Melody* and *Harmony*

**Arranging, production and mixing (9):** 文海良《编曲》; 野崎貴朗《圖解合成器音樂創作法》; 竹內一弘《圖解電子音樂創作法》; 藤谷一郎《圖解樂風編曲入門》; 熊川浩孝等《图解编曲入门》; Roey Izhaki *Mixing Audio*; 黄承箱、刘希望《音乐制作人白金手册》; Dennis DeSantis *Making Music*; J. Anthony Allen *Music Theory for Electronic Music Producers*

**Rhythm, style and genre (9):** Berry & Gianni *The Drummer's Bible*; Tommy Igoe *Groove Essentials*; Rikky Rooksby *Riffs*; Dan Charnas *Dilla Time*; Joseph Schloss *Making Beats*; Paul Edwards *How to Rap* 1 & 2; John Valerio *Bebop Jazz Piano*; 爵士吉他即兴演奏·节奏律动

**Acoustics (1):** Howard & Angus *Acoustics and Psychoacoustics*

**Cantonese and Chinese pop history (1):** 黄志华《粤语流行曲四十年》

**Corpus:** Cambridge-MT multitrack library (62 arrangements measured and written back as ARR-SPECs), 《同一首歌》and Chinese guitar-chart collections for form and progression statistics

## Conventions

- Each skill has YAML frontmatter with its name and an English routing description; genre names and keywords identify the appropriate skill.
- Skill bodies in this fork are English; principles, tables and checklists are language-neutral in purpose. Output language follows the user's question.
- **Every rule carries a failure condition or a self-check action.** A rule you cannot test is an opinion.
- Where the sources disagree, both positions are kept side by side with a note on when each applies: Levine's chord-scale judgement against the Japanese pop practice, the Drummer's Bible tempo bands against Groove Essentials' refusal to print numbers.
- Chords are always written twice: letter symbols **and** roman numerals, default key C.
- Legacy book-derived citations carry source and page when available; newer genre/artist notes are research guides, not verified song transcriptions. Exact facts require source checking.
- Long tables and worked examples live in each skill's reference file, so the skill bodies stay short.
- Agent-neutral by design: the skill files name no agent and use no agent-specific syntax.

## Technical notes

- **Runtime.** The plugin is plain text. There is no script to run, no Python, no Node, no lint step. The skill files follow the open [agentskills.io](https://agentskills.io) standard, and both agents read the same `SKILL.md` files.
- **Spec files.** An ARR-SPEC is a YAML file (`ARR-SPEC.yaml`); the lyric side's is `LYR-SPEC.yaml`. The six specification files sit in `mc-workflow/`: the definition `ARR-SPEC.schema.md`, the empty template `ARR-SPEC.template.yaml`, the backend capability declarations `backends.yaml`, the examples `example-01-citypop.yaml` and `example-02-fusion.yaml`, and the counter-example `example-00-ai-default.yaml`.
- **Fields mentioned above.** The mix intent is the `mix_intent` field. The two items mc-development fills in are `material` (motif material) and `form[].development` (per-section development).
- **Backends and export formats.** What you paste into Suno is packed in `suno-pack.md` (title, style description, section-tagged lyrics, exclusions). The score for YuE2 is ABC, with the vocal line in the lowercase note register and the lyrics on `w:` lines. mc-symbolic-score writes ABC, MusicXML and MIDI from one emitter; the note file that loads into music software is the MIDI. In `backends.yaml` each backend declares `honors: exact / hint / none` for every field, and a field declared none is left out of that backend's score.
- **Per-skill files.** `SKILL.md` frontmatter holds a kebab-case `name` matching the folder and a routing `description`. Many older skills use `reference.md`; new Latin genre skills use `references/artists-fusion.md` for artist lenses and fusion exercises.

## License

MIT for the skills themselves, see [LICENSE](LICENSE). Quotations from the source books are not covered by it and remain the property of their authors and translators. See [NOTICE](NOTICE).

---

Sister project, same idea applied to screenwriting: [screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills).

This library supersedes [japanese-composition-skills](https://github.com/jtydhr88/japanese-composition-skills); its eleven skills were absorbed into the general and style layers here.
