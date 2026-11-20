# mc-render-compile Reference: Lyric Format Sent to the Backend

> [SKILL.md](SKILL.md) §5.3 covers where lyrics come from and how they are chunked by section id. This file holds **the formatting rules for the chunked blocks as they are sent to the backend**: line breaks, breath points, held notes, punctuation and brackets, comments, instrumental sections, and what to check before sending.
> The original lyric text lives in `meta.upstream.lyrics.sections`, which this package only reads. The "add markers" and "remove" steps below apply only to the copy sent to the backend (written back to `render.<backend>`); the original is left untouched.
>
> ⚠ These are general lessons: how each backend actually reacts to held-note notation, punctuation and brackets, and blank lines versus single line breaks should be decided by testing.

---

## 1. Line breaks are instructions, not layout

Every line break inside a section's lyric block is read by the backend as a phrase boundary (SKILL §5.3). The consequences:

| What is sent | What the backend understands |
|---|---|
| One line split into two | **Two phrases**, with a breath between them |
| Two lines merged into one | **One long phrase**, with no breath between them |
| A blank line | A longer pause |

So each element of `meta.upstream.lyrics.sections[].lines` is one line as sent: keep the lines exactly as they are, neither merging nor splitting them.

## 2. Breath points must fall on line breaks

`vocal.breath_points` records after which line and which syllable a breath is taken. For backends that accept only plain-text lyrics, breathing can be expressed only through line breaks. When the two do not match:

- **Breath point inside a line** → the backend will not breathe there, and the singer has to hold the breath until the end of the line
- **No breath point at a line break** (two lines that are meant to be sung without stopping) → the backend still pauses at the break, adding an extra pause

Record each mismatch as an entry in `checks.exemptions` (this backend cannot express it). If a line division needs to change, write a `messages` entry for `lyrics` saying which section and which line. The lead-sheet and symbolic paths can write mid-line breaths as breath marks (`mc-symbolic-score`), so this limitation does not apply to them.

★ **Self-check action**: read the lyrics to be sent aloud, line by line, taking a breath at the end of each line. If you cannot read it through, the line divisions and breath points do not match.

## 3. Held notes

The backend cannot tell which syllable you want stretched. To hold a note, write it explicitly in the lyrics copy sent to the backend. The usual methods are repeating a vowel (`a-a-ah`) or using hyphens; the notation differs between backends, so decide by testing. On the symbolic path the durations are already on the score, so nothing needs to be added.

## 4. Punctuation and brackets

| Element | How backends usually handle it | At compile time |
|---|---|---|
| **Commas, full stops** | Mostly ignored, though sometimes read as a slight pause | Leave them out where possible; line breaks are a more reliable way to express pauses |
| **Round brackets `()`** | ★ Often read as harmony or backing vocals | Reserve them for backing vocals and vocal responses only; **do not use brackets for comments** |
| **Square brackets `[]`** | ★ Reserved for section labels | Do not appear in the lyric text |
| **Ellipses, dashes** | Behaviour is unpredictable | Avoid |
| **Capitalisation** (English) | May affect emphasis | Write normally |
| **Comments, performance notes** | ★ Will be sung as words | ★★ Keep out of the lyric block; see §5 |

## 5. Comments stay out of the lyric block

Every character in the lyric block gets sung. If you write a line such as "repeat this three times" in the lyrics, the backend will **sing that sentence aloud**. This is the most common accident.

- Requirements for the arrangement or the vocal go in `style_prompt`, `vocal`, or `form[].note`, not in the lyric block
- If the source lyrics contain notes mixed in with the text, do not send the notes to the lyric block. Carry out what they ask through `form[]` (a section that should repeat is written out in full in the chunks). Then write a `messages` entry for `lyrics`

## 6. Instrumental sections

Put no words under `[Instrumental]`. The backend assigns section positions by label, and any words placed there will be sung as if they were a phrase.
★ However, **keep the label**. If this slot is removed, all later sections shift forward, and the backend uses the next label to fill this section's position. Intros, interludes, and outros have ids in `form[]` but none in the lyrics, so at compile time place the label from `form[]` and place no words.

## 7. Which backends accept lyrics, and where the character-to-note alignment counts

Whether a backend accepts lyrics is determined by `accepts.lyrics` in `backends.yaml`. Backends where it is `false` (Stable Audio) have no vocals, so lyrics are not sent. The symbolic path does not use the lyric block; lyrics travel with the score (the `w:` line in ABC, syllable by syllable in MusicXML; MIDI can carry them only as text events, see `mc-symbolic-score`).

★ **The Chinese tone-setting check only takes effect when the melody is executed.** The tone-setting check is run against the melody in the spec. For backends that accept both lyrics and score (YuE2 injects ABC), the melody being sung is the one that was checked, so the result is locked in before generation. Other backends can only be given the melody as a hint, and the model writes the melody itself, so the checked result is not guaranteed to hold for them.

## 8. Checks before handing off to the backend (links to SKILL §11)

- [ ] The target backend **does accept lyrics** (`accepts.lyrics` is not `false`)
- [ ] Line divisions match `meta.upstream.lyrics.sections[].lines` exactly, with no merging or splitting
- [ ] Read aloud line by line, with a breath possible at the end of each line; mid-line breath points are recorded as exemptions or raised as messages
- [ ] `[Instrumental]` sections **keep their label but have no words**
- [ ] ★★ The lyric block contains **no comments or performance notes**
- [ ] Round brackets are used only for **backing vocals**, and square brackets only for **section labels**
- [ ] Punctuation is kept to a minimum; pauses are handled through line breaks
- [ ] Chinese: if the backend can only be given the melody as a hint, **know that the tone-setting check is not guaranteed to hold**
