# Sound selection and asset acquisition — real Tidal Studio capabilities

**Goal:** help Maestro choose a timbre that makes a better arrangement, while respecting already-loaded resources, license and audio-engine constraints. This is a **decision process**. The skill cannot download or execute code itself.

## The six-step sound choice

1. Name the musical role and instrument idiom (e.g. picked requinto answer, warm sustained pad, clipped 808 sub, open conga).
2. Specify pitch span, attack, release, rhythmic density, expressive variation and mix register.
3. Inspect what the **running** studio actually exposes (built-in Dirt-Samples, custom user samples, installed packs, and registered synths). A GitHub file with a SynthDef is not evidence it loaded on the user's OS.
4. Try the closest suitable **existing** sample or built-in synth; set note lengths, filter/envelope and articulations. Use a track only if it advances the composition.
5. If insufficient, request one precise compatible licensed sample through the existing `descargar` capability (and use fallback); if a custom synth is genuinely necessary, propose a *future engineering task* or manual reviewed addition.
6. Use A/B variants to check identity and musical impact with/without the better timbre. Never confuse downloaded resources with improved composition.

## Samples: supported today

The studio's `server/fetcher.py` uses licensed community sample packs and optional Freesound. Some known sources are VCSL (CC0), Uzu drumkit, Salamander piano, and mridangam; availability and attribution requirements vary per resource. Freesound may require a user-configured API key. The program handles downloading, license filter, attribution in `samples/CREDITS.md`, loading a bank into SuperDirt and fallback substitution.

Tidal Studio Maestro can request a missing sample with its **existing** JSON key (example is a fragment, not a full Maestro reply):

```json
{
  "descargar": [
    {
      "nombre": "conga_abierta",
      "busqueda": "conga open tone",
      "tipo": "percusion",
      "duracion": "golpe",
      "alternativa": "perc",
      "por_que": "La conga abierta permite una respuesta tímbrica diferente del golpe cerrado del patrón"
    }
  ]
}
```

The host validates and limits requests; its current parser reads `nombre, busqueda, tipo, duracion, alternativa, por_que` and processes at most 3 distinct requests. A large sample pack is not automatically approved: the host asks before downloading. To avoid accidental failures, choose safe names using lowercase letters/digits/underscore and a **known existing** alternative. For an unavailable sound, be transparent and do not claim it was loaded before the host reports success.

**One-shot vs pitched instrument vs full loop:** for acoustic guitar, brass and strings, a one-shot may be unconvincing across several notes; prefer appropriate sampled instruments and performance articulation where available. Full loops require matching tempo, key, bars and compatible groove; the studio has dedicated loop analysis/stretch/slicing support. Avoid arbitrary copyright-bearing music loops.

## Synthesis: supported today vs future

`supercollider/start_superdirt.scd` loads `studio-synths.scd` during SuperDirt startup. `studio-synths.scd` defines fallback/basic oscillators, a custom trumpet and synth fallbacks for environments without sc3-plugins. The runtime may expose `superpiano`, `superpwm`, `supersaw`, `superfm`, `supertrumpet`, `sawtooth`, `square`, `triangle`, `pulse`, `sine`, etc., **but verify runtime availability** through the active engine sound list.

Choose synths by audio function:
- Warm mono bass: simple harmonic waveform, controlled LPF, short attack, envelope matched to kick/gap; don't use long release across busy syncopation.
- Acid/techno lead: harmonics + filter movement/resonance, a recognizable motif, rhythmic articulation.
- Soft pad: attack/release supporting section boundaries, high-pass or low-mid restraint to protect bass and guitar.
- Synthetic brass: brassy attack and expression may suffice for a sketch but is not the same as a realistic brass section; if acoustic idiom is essential, search a legitimate sample.
- Percussive metallic hit: short transient, tuned if melodic, tails managed to avoid rhythmic blur.

**No arbitrary SynthDef downloads today:** `server/fetcher.py` handles audio samples, not remote SuperCollider code. A third-party SynthDef may need sc3-plugins, executable .scd code review, server registration, version and resource tests. Never recommend auto-running downloaded code or claiming a new `install_synth` API exists. A future feature should require user approval, trusted provenance and compatibility tests in an isolated environment.

## Download decision matrix

| Desired role | Preferred first step | If unavailable | Why |
|---|---|---|---|
| Authentic conga/cajón/güira/cowbell | Search current sample banks | Licensed one-shot request | Acoustic transients are central to identity |
| Bachata requinto / charango | Existing multisample or expressive pluck | Appropriate licensed instrument samples or disclose approximation | Repeated pitches and articulations must remain realistic |
| Timbales/brass orchestra | Available hits/synth sketch | Licensed brass/hit bank with correct licensing | Harmonized horn phrase needs more than one static chord stab |
| Reggaeton sub / techno bass | Available synth and envelope control | Refine synth/bass notes before downloading | Expressive synthesis is part of the genre |
| Cinematic transition | Existing FX/noise/filter envelope | Optional licensed effect sample | Only if it helps form and contrast |
| Sampled long loop | Library loop matching tempo/key | Host's pack search with license/loop confirmation | Poorly synced loops erase groove |

**Do not perform unrequested installations, modify SuperCollider startup files or reinterpret a synthesis code fragment as a musical sample.**
