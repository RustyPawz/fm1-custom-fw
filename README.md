# M-VAVE FM1 Resource Hub, Custom Firmwares & MIDI SysEx Protocol Documentation

A curated directory and reference hub for the **M-VAVE FM1** synthesizer (powered by the **JieLi AC791N** processor) — gathering community custom firmwares, documentation, tools, MIDI SysEx protocol details, and the `M-UPGRADE-FM1.app` (macOS) updater.

> [!NOTE]
> **Device Compatibility Notice & SMK-37 Resources:**  
> This repository strictly curates custom firmwares and tools specifically targeted at the **M-VAVE FM-1** synthesizer.  
> If you are looking for custom firmwares, ports, community discussions, and tools for the **M-VAVE SMK-37 / SMK-37 Pro** keyboard controller:
> * **[r/MvaveSmk Subreddit](https://www.reddit.com/r/MvaveSmk/):** Community hub for SMK-37 discussion and mods.
> * **[M-VAVE SMK-37 Custom Firmware Hub](https://genkigenki.github.io/smk37/):** Firmware hub and guides.
> * **[fm1-to-smk37 Port Kit by genkigenki](https://github.com/genkigenki/fm1-to-smk37)** & **[Snoop37](https://github.com/genkigenki/Snoop37)**:
>   * **License:** Open Source (GPL-3.0 for Snoop37 firmware port; CC BY-NC 4.0 for hardware guide & documentation).
>   * **Hardware Relationship:** Both devices share the identical **JieLi AC791N (WL82)** processor, second-stage bootloader, update loader, and chip key, differing primarily in panel wiring (keyboard matrix, 16 RGB pads, 8 encoders, 4 faders, pitch/mod wheels, display pins, and flash partition map).
>   * **Features:** Board Port Patch Series (`smk37-board`), Snoop37 reference port of SLOOP 2.5 on SMK-37 Pro, porting compatibility matrix, and critical flash safety documentation on preserving unique SPI flash regions (`0xC1000` USRTRIM factory calibration `trimdat`, `0xC0000` BTIF, `0xFF000` chip key/MAC).

> [!IMPORTANT]
> **Official Open Source Firmware & SDK (M-VAVE):**  
> In October 2026, M-VAVE briefly open-sourced their FM-1 firmware and development toolkit under GPL-3.0.  
> **Status Notice:** While the official GitHub repository (`m-vave/fm1_open`), the online web workbench (`open.m-vave.com`), and forum announcements were subsequently taken down by the manufacturer, community mirrors and web cache archives are preserved:
> * **Repository (Offline / Removed):** **[m-vave/fm1_open](https://github.com/m-vave/fm1_open)** (8 tracks, 8 sample slots, 16 demo FX, hardware C drivers, and WebAssembly simulator).
> * **Community Cached Open Workbench:** Preserved by the community with instructions, discussion, and mirror link on Reddit: **[r/MVaveFM1: Cached web page for the open workbench](https://www.reddit.com/r/MVaveFM1/comments/1x5y4qy/cached_web_page_for_the_open_workbench/)** — provides working in-browser WebAssembly simulation, firmware flashing, and stock V15 recovery when other tools fail.
> * **Announcement & Discussion (Removed):** **[M-VAVE Official Forum Topic #4](https://forum.m-vave.com/topic/4)**.



---

## 1. Custom & Alternative Firmwares

Community-developed custom firmwares, mods, and experimental firmware projects for the M-VAVE FM-1, clearly divided into sound/groovebox instruments, modular builders, games and non-audio ports, and stock binary patchers:

### 1.1. Sound, Synthesizer & Groovebox Firmwares (Music & Audio)

Community musical firmwares organized by architectural family and lineage — the **Felucca** multi-engine platform, the **SLOOP** live groovebox ecosystem, the **FoMni** chord harp branch, and standalone independent engines:

#### 1.1.1. Felucca Ecosystem (Multi-Engine Platform & Direct Forks)

Firmwares built upon or directly forked from the foundational open-source multi-engine **Felucca** synthesizer core by Hügelton Instruments:

 1. **[Felucca by hugelton](https://github.com/hugelton/Felucca) ([Web Installer](https://hugelton.github.io/Felucca/) | [Web Editor](https://hugelton.github.io/Felucca/webapp/editor/) | [Build Guide](https://github.com/hugelton/Felucca/blob/main/BUILDING.md)):**
   * **License:** Open Source (GPL-3.0-only).
   * **Synthesizer Engines:** 9 distinct sound engines including **ANALOG** (virtual analog, 2 osc, PWM, resonant LPF), **DIGITAL** (4-op FM, 8 algorithms, feedback), **PHASE** (phase distortion), **LOFI** (chiptune, 4-bit wave RAM), **SAMPLE** (multisampled instruments + user slots), **VOICE** (formant/vocal osc), **TRIO** (3 osc with ring mod/sync), **WHEEL** (tonewheel organ with drawbars & rotary speaker), and **GRAIN** (granular textures).
   * **Architecture & Features:** 4 tracks (3 synth parts + 1 GM drum track, 8 shared voices), 64-step sequencer per track with chords/ties/slides and live loop recording, per-track SLICER (16-step tempo-synced gate/stutter), effects (distortion, chorus, delay, reverb sends, master limiter), scales & white-key quantization, and web editor.
   * **Documentation:** [Felucca BUILDING.md Guide](https://github.com/hugelton/Felucca/blob/main/BUILDING.md) — complete build guide for compiling Felucca-family firmwares from source using the JieLi `pi32v2` toolchain.
   * **Video Guides & Demos:** [Complete Guide (v0.9)](https://www.youtube.com/watch?v=UzgbDjsFEpY) | [Engine Tour & Sequencing](https://www.youtube.com/watch?v=EzFknmhtKZk) | [Live Performance Jam](https://www.youtube.com/watch?v=XEK4VhsYwCE).
   * **Installation:** Direct web installer via WebMIDI in Chrome/Edge over standard USB-C cable (no extra hardware needed; stock updater restores official firmware).

 2. **[Felucca [Salt] by Chance Roth (ChanceTheMaker)](https://github.com/ChanceTheMaker/Felucca) ([Web Installer](https://chancethemaker.github.io/Felucca/webapp/installer/) | [Web Studio](https://chancethemaker.github.io/Felucca/webapp/editor/)):**
    * **License:** Open Source (GPL-3.0-only). Enhanced fork of Felucca by Leo Kuroshita (Hügelton Instruments).
    * **Concept:** Multi-engine synthesizer firmware with hardware-inspired browser Studio, hardware TRS MIDI expansion, rich display palettes, and standalone in-browser sound generation.
    * **Features:**
      * **Studio & In-Browser Synthesizer:** Browser Studio can act as an online synthesizer without physical hardware (nine engines, 54 presets, live oscilloscope waveform, 12 hardware themes like Stage Red, Matrix, Vintage DX, Model D, Vaporwave, and on-screen keyboard).
      * **Hardware TRS MIDI Input:** Full expression handling on 3.5 mm TRS MIDI IN alongside USB (sustain pedal, pitch bend, mod-wheel vibrato, MIDI panic/reset).
      * **Flexible Clock Sources:** Internal, USB, or TRS clock sync and MIDI Start/Stop/Continue.
      * **Display Themes & Typography:** 20 on-device screen palettes (including 8 light palettes and light/dark high contrast modes), selectable Terminus Regular/Bold typography.
      * **Preset Management:** Persistent favorite stars, All/Favorites browsing filtering, and live MIDI event/chord monitor.
    * **Installation:** Browser-based WebMIDI installer via USB.

 3. **[Melodee by keremimo](https://github.com/keremimo/melodee) ([Web Installer](https://keremimo.github.io/melodee/) | [Web Editor](https://keremimo.github.io/melodee/webapp/editor/)):**
   * **License:** Open Source (GPL-3.0-only). Modified build based on Felucca.
   * **Features:**
     * **Prophet-5 Engine (New in 0.13):** Native **Sequential Prophet-5 Rev 4** engine replacing ANALOG — two oscillators with hard sync, Poly-Mod, LFO/noise wheel modulation, selectable SSI (Rev 1/2) and Curtis (Rev 3) 4-pole low-pass filters, separate filter/amp envelopes, Vintage knob, glide, unison, and 5 voices per track. Includes **all 200 programs** of Sequential's v1.03 factory bank (128 native user slots P001–P128), 16 device parameter pages, and `.syx` program/bank import and export in the web editor.
     * **Casio CZ-1 Phase Distortion:** Authentic CZ-1 engine with 64 original CZ-1 factory preset tones, 8 CZ device banks with `.syx` import/export, and 38 dedicated editing pages.
     * **FM6 & Microtonal Scales:** 64 DX7/FM6 slots with direct SysEx bank dump support, 70 microtonal tunings across equal divisions, just intonation, historical temperaments, and maqam models.
     * **Advanced Sequencing:** Single unified note editor (`SEQ > NOTES`), reversible timing quantization (`QNT`), and 1,024 recorded notes across 32 pattern banks.
   * **Installation:** Browser WebMIDI installer with built-in backup before installation.

 4. **[ChoralRoot FM-1 by Quixotic7](https://github.com/Quixotic7/ChoralRootFM1) ([Web Installer](https://quixotic7.github.io/ChoralRootFM1/) | [Web Emulator](https://quixotic7.github.io/ChoralRootFM1/emu/)):**
   * **License:** Open Source (GPL-3.0). Based on Felucca (engines/platform) and ChoralRoot (Monome grid chord engine).
   * **Concept:** Telepathic Orchid / Monome-style chord performance instrument.
   * **Features:** Two-handed chord shaping (one hand selects roots, the other shapes voicings), custom key modes, performance bass line, built-in looper, full color UI, and browser sound emulator.
   * **Installation:** Browser WebMIDI installer via USB.
   * **Community Remix / Mod:** [Choralroot-remix on r/MVaveFM1](https://www.reddit.com/r/MVaveFM1/comments/1x3qrqx/choralrootremix/) by Creative_One919 — extended remix incorporating Melodee's 6-voice Prophet-5 engine with 200 factory presets, DUELL-inspired Morph engine, dedicated BASS engine with multi-core rendering, "Rosen" random preset cycling, "Swag voicing" mode, synced BPM gate, and sidechain volume.

 5. **[X0X by Charles Vestal](https://github.com/charlesvestal/fm1-x0x) ([Web Installer](https://charlesvestal.github.io/fm1-x0x/install/) | [Web Emulator](https://charlesvestal.github.io/fm1-x0x/emu/) | [Manual](https://charlesvestal.github.io/fm1-x0x/manual/)):**
    * **License:** Open Source (GPL-3.0). Based on Felucca.
    * **Concept:** Propellerhead ReBirth-inspired techno/acid groovebox machine.
    * **Features:** TR-909, TR-808, two TB-303 synths with an integrated acid line generator, and a breakbeat player all playing simultaneously; includes automation, shared reverb and tape delay sends, and a master compressor.
    * **Installation:** Browser WebMIDI installer via USB (with stock restore option).

 6. **[GHOULBOX 2.0 by Jason Persinger](https://github.com/jasonpersinger/ghoulbox-fm1-dungeon-synth) ([Website & Browser Emulator](https://ghoulbox.messy.quest) | [Web Installer](https://ghoulbox.messy.quest/webapp/installer/)):**
    * **License:** Open Source (GPL-3.0). Based on Felucca.
    * **Concept:** Dungeon synth, dark ambient, and fantasy music groovebox firmware.
    * **Features:** Cathedral-sized HALL reverb, worn-cassette TAPE / CRKL stage, dedicated hurdy-gurdy engine (GURDY with crank clicks and buzzing trompette), drone latching, historical/just temperaments, and 36+ dungeon sounds (crypt pads, monk choirs, lutes, organs) with an old-school RPG UI and skull boot screen.
    * **Interactive Browser Version:** Complete in-browser emulation playable on an interactive virtual FM-1 via keyboard or mouse at [ghoulbox.messy.quest](https://ghoulbox.messy.quest) without flashing hardware first.
    * **Installation:** Browser WebMIDI installer via USB with full backup feature before flashing.

 7. **[Jangada by zednaked](https://github.com/zednaked/jangada) ([Web Installer](https://zednaked.github.io/jangada/) | [Web Studio](https://zednaked.github.io/jangada/webapp/studio/)):**
    * **License:** Open Source (GPL-3.0). Based on Felucca.
    * **Concept:** Dark, industrial, Brazilian-accented groovebox firmware.
    * **Features:** 10 sound engines (including 6-op FM and superwave analog), 4 tracks, modulation matrix, ratchets, drone holding/evolving modes, and dedicated custom drum kits.
    * **Installation:** Browser WebMIDI installer via USB.

 8. **[REDACTED by DJ Redacted](https://fm1-redacted-installer.xrhetor.chatgpt.site/):**
    * **License:** Open Source (GPL-3.0). Built on Felucca by Hügelton Instruments.
    * **Concept:** Experimental dark, fractured lo-fi four-track groovebox firmware (`PULSE` · `VOLTAGE` · `STATIC` · `GHOST`).
    * **Features:**
      * **Four Track Engines:** Four distinct sound layers chosen via `ALGORITHM`.
      * **Real-Time Track Shapers:** Four top knobs mapped to dynamic performance parameters: `FRACTURE`, `STATIC`, `CHANCE`, and `MUTATE`.
      * **Startup Artwork:** Custom broken vinyl record splash screen.
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

 9. **[Hortator by DEADACTIVE](https://github.com/DeadActive/hortator) ([Web Emulator & Player](https://deadactive.github.io/hortator/)):**
    * **License:** Open Source (GPL-3.0). Built on Felucca.
    * **Concept:** 8-track drum machine firmware.
    * **Features:** TR-808, TR-909 and Mutable Instruments Plaits drum models, user samples, Mutable Instruments Grids generative rhythm algorithm, pumping master compressor, and acoustic resonators.
    * **Installation:** Browser WebMIDI installer via USB.

10. **[April OS by beashoko](https://github.com/beashoko/april-os) ([Web Installer](https://beashoko.github.io/april-os/)):**
    * **License:** Open Source (MIT). Based on Felucca.
    * **Concept:** Dedicated sampling-focused groovebox firmware.
    * **Features:** 32 sample slots (up to 3 seconds each), 8-track sequencer, built-in sample slice and loop editor, direct audio recording using a connected smartphone or computer microphone.
    * **Installation:** Browser WebMIDI installer via USB.

11. **[WaveLoop FM-1 by ELI7VH](https://github.com/ELI7VH/Felucca) ([Web Installer](https://eli7vh.github.io/Felucca/)):**
    * **License:** Open Source (GPL-3.0). Based on Felucca.
    * **Concept:** Performance firmware specifically mapped for external control via Arturia MiniLab 3.
    * **Features:** Dedicated track fader mappings, follow-the-track encoder integration, DJ filter mode, and momentary punch-in FX pad triggers.
    * **Installation:** Browser WebMIDI installer via USB.

12. **[Rainbow mode by joshbartlettband-web](https://github.com/joshbartlettband-web/felucca-rainbow) ([Web Installer & Emulator](https://joshbartlettband-web.github.io/felucca-rainbow/)):**
    * **License:** Open Source (GPL-3.0). Based on Felucca.
    * **Concept:** Children's musical exploration instrument with rainbow color-coded keys, 40 animal sound effects and rhythms, safe volume limiter, and access to the complete Felucca engine via secret key combination.
    * **Installation:** Browser WebMIDI installer via USB.

13. **[fm1-chord by math0ne](https://github.com/math0ne/fm1-chord):**
    * **License:** Open Source (GPL-3.0). Built on Felucca.
    * **Concept:** Chord composition tool, chord sequencer, rhythm accompanist, and ear-training aid.
    * **Installation:** Python installation script via USB MIDI.

14. **[DUELL by balinthcom](https://github.com/oscillr/DUELL) ([Web Emulator](https://oscillr.github.io/DUELL/emu/)):**
    * **License:** Open Source (GPL-3.0). Built on Felucca by Hügelton Instruments.
    * **Concept:** Multi-morphing bi-timbral synthesizer firmware for the FM-1: two full simultaneous sound parts, each with its own synthesis engine, patches, effects, EQ, and arpeggiator.
    * **Features:**
      * **Bi-Timbral Modes:** LAYER, SPLIT (keyboard zone), and STEREO (dual mono, part 1 hard-left and part 2 hard-right with isolated audio engines).
      * **Patch Morphing:** Smooth glide between two states of any patch with SMART randomization and per-patch morph amount.
      * **Per-Part Engine Architecture:** Independent arpeggiators, secondary envelopes and LFOs, 8-slot modulation matrix, dedicated EQ, sidechain ducking triggered via MIDI, and ping-pong delay.
      * **Factory Sound Bank:** ~100 sounds across 12 synthesis engines, 16 multi-setups, and 16 patterns.
      * **MIDI Implementation:** Discrete MIDI channel per part, program change, bank select, and clock sync.
    * **Status & Installation:** Available to play via in-browser WebAssembly emulator; hardware flashing in ongoing development.

15. **[MAKU (幕間機) by okumurari2](https://github.com/okumurari2/maku) ([Web Emulator](https://okumurari2.github.io/maku/) | [Releases](https://github.com/okumurari2/maku/releases)):**
    * **License:** Open Source (GPL-3.0-only). Built on Felucca by Hügelton Instruments.
    * **Concept:** Always-on generative ambient machine firmware designed for DJ intermissions and generative soundscapes: power on and an evolving, random, in-key sonic world is immediately playing.
    * **Features:**
      * **Four Continuous Parts:** Pulse (kick/rhythm, DRUM engine), Floor (drone, PHYS physical modeling), Haze (shimmer/textures, GRAIN granular engine), and Voice (arpeggiated melodic phrase, PHYS engine).
      * **Dynamic Generative Evolution:** Every boot generates a unique scale, tempo (70–90 BPM), sounds, and macro states. Holding HOME regenerates a new world.
      * **Taste Memory ("Likes"):** Tapping REC saves preferred worlds (up to 16). Future generated worlds increasingly draw inspiration and mutate from saved favorites.
      * **Verb-Based Interface:** Action buttons perform timed organic changes — FX (sinks depth), SCL (cascades higher intervals), ENV (swells chords), LFO (wobbles filter/pitch), EDIT (lifts brightness/sharpness), GLO (scrambles phrases), and PLAY (toggles DRIFT value wandering).
    * **Installation:** Flash prebuilt `maku-X.Y.fwsc` via `tools/fm1_install.py` or browser WebMIDI updaters.

16. **[Polly by Charles Vestal](https://github.com/charlesvestal/fm1-polly) ([Web Installer & Emulator](https://charlesvestal.github.io/fm1-polly/)):**
    * **License:** Open Source (GPL-3.0). Built on Felucca by Leo Kuroshita / Hügelton Instruments.
    * **Concept:** Yamaha QY70-inspired 8-track pocket accompaniment arranger and auto-accompaniment workstation for the FM-1.
    * **Features:**
      * **8-Track Arranger Architecture:** Dedicated parts for Drums, Percussion, Bass, and 5 Chord accompaniment tracks powered by the Sonivox EAS General MIDI sound engine.
      * **Interactive Chord Recognition & Follower:** Play chord shapes on the keyboard (or via MIDI IN) to drive realistic live auto-accompaniment transformations.
      * **Style Engine & QY70 Import:** Built-in accompaniment styles with variation switching, fill-ins, intro/outro, and direct import compatibility for Yamaha QY-format style patterns.
      * **In-Browser WebAssembly Simulator:** Full hardware simulation with screen rendering and audio playback running directly in the browser at [charlesvestal.github.io/fm1-polly](https://charlesvestal.github.io/fm1-polly/).
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

17. **[TRIBE (fm1-tribe) by Alexandre Piel (apiel)](https://github.com/apiel/fm1-tribe) ([Site & Web Installer](https://apiel.github.io/fm1-tribe/)):**
    * **License:** Open Source (GPL-3.0-only). Fork of X0X (Charles Vestal) and built on Felucca (Leo Kuroshita / Hügelton Instruments) with kicks and scatter effects from zicBox.
    * **Concept:** Ten-track groovebox firmware where any synthesis or drum engine plays on any track.
    * **Features:**
      * **10 Tracks & 25 Engines:** Freely assignable tracks running two dedicated kick models (`KICK W`, `KICK P`), Roland TR-909 and TR-808 drum voice models (9W9 / 8W8 ports), and TB-303 bassline synthesis (schwung-303 port).
      * **16 Clips per Track:** Launch clips at pattern boundaries or instantly; supports 16, 32, or 64 steps, 6 playback clock rates, 4 playback directions, and shuffle/swing.
      * **Live Performance Scatter FX:** Momentary performance effects triggered directly from keys while playing (beat loops, reverse, rhythmic gating, bitcrush, distortion, ring modulation, and resonant filters).
      * **Dual Master FX & Compressor:** Reverb, delay, drive, distortion, fuzz, wavefolder, bitcrusher, decimator, or ring modulator fed by per-track sends, plus an always-on master compressor.
      * **In-Browser Emulator:** Real firmware compiled to WebAssembly running directly in the browser at [apiel.github.io/fm1-tribe](https://apiel.github.io/fm1-tribe/#emulator).
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

18. **[Golana by Gadlele](https://github.com/Gadlele/Golana):**
    * **License:** Open Source (GPL-3.0). Built on Felucca by Leo Kuroshita / Hügelton Instruments.
    * **Concept:** Korg microKORG-inspired analog-modeling synthesizer firmware for the FM-1 featuring the classic MATRIX editing workflow.
    * **Features:**
      * **MicroKORG Synth Architecture:** 4-voice polyphonic / unison / mono / legato engine with 2 oscillators per voice (saw, pulse with PWM, tri with wavefold, sine with cross-mod from OSC 2, noise, and ring modulation), dual LFOs, and 4 assignable virtual modulation patch routings.
      * **Resonant Multi-Mode Filter:** 24 dB/oct LPF, 12 dB/oct LPF, BPF, HPF, and an aggressive screaming MS-20-style resonant low-pass filter model.
      * **Matrix Interface & Waveform Drawing:** On-device 240 × 240 graphics rendering real-time waveforms for OSC 1/2, dynamic filter response curves, envelope graphs, and live LFO waveforms calculated directly from parameter values.
      * **FX Chain & 16-Step Sequencer:** Integrated arpeggiator, 16-step sequencer with ties/slides per program, modulation FX (chorus, flanger, ensemble, phaser, metal distortion), tempo-synced delay, and reverb with flexible FX routing orders.
    * **Installation:** Build and flash firmware via CLI toolchain (`tools/fm1_install.py`).

19. **[FANTASMA / Pelucco by Gadlele](https://github.com/Gadlele/Pelucco) ([Web Emulator / Artifact](https://claude.ai/artifact/RLDaXqXDuzzfyJZ8ibS5Gk)):**
    * **License:** Open Source (GPL-3.0). Built on Felucca by Leo Kuroshita / Hügelton Instruments.
    * **Concept:** Generative ambient and drone synthesizer firmware for the FM-1 with dedicated chord-strum and generative "haunted" modes.
    * **Features:**
      * **"Haunted" Generative Ambient Engine:** Pressing `OCT+` on the fourth SEQ page triggers self-generating, evolving ambient music across three independent channels across randomized musical scales (major, minor, dorian, mixolydian, pentatonic, phrygian, lydian) even with the transport stopped; `OCT-` halts the generator.
      * **BELL Generative Loops:** 4 drifting loops of 13/17/23/29 steps (`DENS`, `EVOLVE`, `RANGE`, `SEED`) snapped to the scale on the BELL engine.
      * **Dedicated Ambient Role Split:** 4 channels configured for ambient roles: Pads (automatic chord generator), Lead (key-locked for live manual jamming over drones), FM Bells (generative chime echoes), and Continuous Noise (sea/wind textures).
      * **OMNI Strum Mode:** Omnichord-style performance mode where black keys trigger chords following the active root scale while white keys act as a harp strum plate.
      * **USB Rescue Boot:** Built-in safe recovery mode (`OCT-` held on power-on or two crash loops in a row) launching a minimal updater screen reporting as `FM-1_000` to guarantee web flashing and recover without bricking.
      * **Custom Ambient UI & Reverb:** Expansive long-decay `AMBI` reverb engine, custom ghost splash screen, and high-visibility neon "ECTO" color theme.
    * **Installation:** In-browser WebAssembly simulation and WebMIDI installer via Claude artifact, or build from the [Gadlele/Pelucco repository](https://github.com/Gadlele/Pelucco).

20. **[Skiff by illuminus5](https://github.com/illuminus5/skiff) ([Web Installer](https://illuminus5.github.io/skiff/webapp/installer/) | [Web Editor](https://illuminus5.github.io/skiff/webapp/editor/)):**
    * **License:** Open Source (GPL-3.0). Fork of Felucca by Leo Kuroshita / Hügelton Instruments.
    * **Concept:** 6-track groovebox firmware for the FM-1 with 14 synthesis engines and deep parameter-locking sequencer.
    * **Features:**
      * **6 Tracks & 14 Engines:** Expanded polyphonic tracks hosting virtual analog, FM, wavetable, physical modeling, drums, and noise generators.
      * **Advanced 64-Step Sequencer:** Per-step parameter locks (p-locks), microtiming, ratchets, and trig conditions (probability / iteration logic).
      * **Dual Effects & Mod Matrix:** Flexible send effects and real-time knob modulation assignments.
      * **Web Tooling:** Dedicated browser WebMIDI installer and companion web editor for patch and pattern management.
    * **Installation:** Browser WebMIDI installer via USB directly from the web installer page.

21. **[Felucca 8 Patterns by echoe](https://github.com/echoe/Felucca_8_patterns) ([Releases](https://github.com/echoe/Felucca_8_patterns/releases/tag/1.5.1_and_sequences)):**
    * **License:** Open Source (GPL-3.0). Fork of Felucca 1.5.1.
    * **Concept:** Pattern-chaining and arrangement expansion fork of Felucca.
    * **Features:**
      * **8 Chainable Patterns per Track:** Extends Felucca with 8 independent pattern slots per track that can be chained into song sequences.
      * **Optimized Flash Footprint:** Sample playback assets removed to maximize flash space and code budget for sequence memory and pattern chaining.
    * **Installation:** Prebuilt `.fwsc` firmware releases available on GitHub; flash via WebMIDI or CLI flasher.

#### 1.1.2. SLOOP Ecosystem (Groovebox Core & Derived Firmwares)

Firmwares centered around the **SLOOP** 4-track live groovebox workflow and its DX7/sampling expansion forks:

 1. **[SLOOP by isod89](https://github.com/isod89/sloop-fm1) ([Web Installer](https://isod89.github.io/sloop-fm1/) | [Web Editor](https://isod89.github.io/sloop-fm1/webapp/editor/)):**
   * **License:** Open Source (GPL-3.0). Based on Felucca by Hügelton Instruments.
   * **Concept:** Live performance groovebox firmware designed for any music style without mandatory presets or fixed patterns.
   * **Features:** 4 tracks (3 synth tracks + 1 drum machine with 16 sounds across the white keys), 9 synthesis engines, 68 sounds, 37 drum kits, custom sample support, and live-playable song mode. Features USB stereo audio input (class-compliant recording directly into DAWs without drivers), 3.5 mm TRS MIDI IN keyboard input, MIDI clock in/sync, button and note LED illumination modes for dark environments, sample chopping/fitting, and a web editor with full backup/restore.
   * **Installation:** Browser-based installer via WebMIDI in Chrome/Edge, with easy rollback to M-VAVE stock V15.

 2. **[sloopDX by zvenson](https://github.com/zvenson/dxsloop) ([Website & Web Installer](https://dx7.designburgapps.com/) | [Web Editor](https://dx7.designburgapps.com/webapp/editor/) | [Cheat Sheet PDF](https://dx7.designburgapps.com/sloopdx-cheat-sheet.pdf)):**
    * **License:** Open Source (GPL-3.0-only). Built upon SLOOP (isod89), Felucca (Leo Kuroshita), and the `msfa` 6-operator DX7 core of Dexed (Apache-2.0).
    * **Concept:** SLOOP's live groovebox workflow merged with an authentic Yamaha DX7 engine and a fully programmable FM drum machine.
    * **Features:**
      * **6-Operator FM Engine:** Complete 32-algorithm DX7 engine ported directly from Dexed's `msfa` (99% sample-identical to Dexed), featuring full envelope scaling, keyboard level/rate scaling, LFO, and feedback.
      * **Cutoff & Resonance Filter:** Dedicated resonant low-pass filter (CUT and RESO on Knobs 1 & 2) placed behind every DX7 voice, modulatable via envelope and LFO.
      * **On-Device Voice Editing:** Full voice programming on the FM-1 hardware with parameter lists, visual operator box diagrams, and operator solo/mute auditioning, backed by a companion web editor.
      * **256 Sysex Voices:** 8 banks of 32 voices loaded directly from standard DX7 `.syx` bulk dumps (4104 bytes), supplemented with 20 factory modern patches (DEEP SUB, 808 SUB, REESE).
      * **Programmable 16×8 FM Drums:** 16 distinct FM drum sounds across 5 kits (`DX KIT`, `808 FM`, `ELECTRO`, `METAL`, `MY KIT`). Each sound provides 8 on-device macro controls (TUNE, DECAY, SWEEP, BRIGHT, NOISE, LEVEL, PAN, CHOKE) plus a dedicated reverb send, parameter locks per step, kit randomization dice, and kit export/import via `.syx`.
      * **OMNI Chord Harp Mode:** Turn any synth track into an Omnichord-like instrument (black keys trigger chords like F, C, G, Dm, Am, Em, G7, E7, D7, Bb, A7, while white keys act as 16 strum strings; bass tracks can follow chords via `FLW`).
      * **Sequencer & Effects:** Up to 128 steps per track (256 steps shared dynamically across tracks), dedicated per-effect pages (SENDS, DIST with soft/hard/fuzz/crush, CHORUS, DELAY, REVERB), USB audio streaming, and live punch-in FX.
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

 3. **[FM1 Move by Nicodesy06](https://github.com/Nicodesy06/FM1-MOVE) ([Web Simulator](https://nicodesy06.github.io/FM1-MOVE/sim/) | [Device Installer & Manager](https://nicodesy06.github.io/FM1-MOVE/device/) | [Manual / Quick Start](https://nicodesy06.github.io/FM1-MOVE/manual/) | [Source Branch](https://github.com/Nicodesy06/FM1-MOVE/tree/fm1-move/dev)):**
    * **License:** Open Source (GPL-3.0). Built upon SLOOP 2.5 by isod89.
    * **Concept:** Eight-track groovebox firmware for the FM-1 inspired by the Ableton Move workflow, featuring a custom 240 × 240 UI designed for live performance.
    * **Features:**
      * **8 Independent Tracks:** Flexible track assignments (any combination of synth tracks or drum kits).
      * **Clips & Scenes:** Performance-oriented clips and scene launcher replacing traditional linear song arrangers.
      * **Browser Simulator:** Firmware compiled to WebAssembly running directly on a simulated device panel in the browser.
      * **Device Page:** In-browser WebMIDI tool to install/backup firmware, manage presets, kits, FM6 banks, and samples.
      * **Status:** Verified in host simulation and builds cleanly for the JieLi AC791N target compiler (experimental / hardware verification in progress).

 4. **[FM1 Quest by hericdk](https://github.com/hericdk/fm1-quest) ([Web Installer](https://hericdk.github.io/fm1-quest/webapp/installer/) | [Web Emulator](https://hericdk.github.io/fm1-quest/emulator/)):**
   * **License:** Open Source (GPL-3.0-only). Built upon the SLOOP groovebox core.
   * **Concept:** Fantasy RPG sidescroller interface for the groovebox: tracks are represented as party heroes, sequence steps are attacks, BPM drives party walk speed, scales dictate biomes, and recording loops triggers boss fights.
   * **Installation:** Browser WebMIDI installer via USB.

 5. **[JIANT FM by juanjiant-bit](https://github.com/juanjiant-bit/JIANT) ([Online Emulator](https://juanjiant-bit.github.io/JIANT/) | [Web Installer](https://juanjiant-bit.github.io/JIANT/webapp/installer/) | [Web Editor](https://juanjiant-bit.github.io/JIANT/webapp/editor/)):**
    * **License:** Open Source (GPL-3.0-only). Built upon Felucca 1.1.5.1 and SLOOP.
    * **Concept:** Bio-synthetic groovebox & performance synthesizer OS for the FM-1 with a high-contrast "thermal camera" UI theme (ironbow gradient palette and Chakra Petch typography). Treat each sound engine as an organic bio-organism reacting dynamically in real time.
    * **Features:**
      * **6 Multi-Engine Tracks (T1–T6):** Flexible pattern sequencing with compressed song sections (storing 8 songs × 4 sections within the FM-1's flash boundary).
      * **8 Distinct Sound Engines:**
        * `ANALOG`: Dual-oscillator analog synth with hard sync, ring mod, 3-saw supersaw, and per-voice multi-mode filter.
        * `FM6`: 6-operator FM engine (Dexed core) with native `.syx` patch import.
        * `PHASE`: Feedback phase-distortion synthesis engine.
        * `LOFI`: Bytebeat (`BYTE`) and floatbeat (`FLOAT`) algorithmic generator with 32 selectable math formulas, live motion (`MOTN`), pitch bending (`BEND`), and looping (`LOOP`).
        * `VOICE`: Formant/speech synthesis model.
        * `WHEEL`: Tone wheel organ emulation.
        * `NOISE`: Dedicated metallic and noise percussive generator.
        * `DRUM-X`: Bio-percussion kit with colony-morphing X-MOD tempo-synced LFOs.
      * **Bus Slicer (SL BUS):** 16-step mix-bus stutter/repeater and pitch-slicing processor (can be routed post-effects or pre-effects tail).
      * **Technical Visualizer:** Live display curves for envelopes, LFOs, distortion, delay, reverb, and thermal isotherm spectrum.
      * **Live Performance Navigation:** Quick page-jumping by turning the `PRESETS` encoder while holding page navigation buttons.
    * **Installation:** One-click USB browser installer, web-based companion librarian/editor, or in-browser emulator.

 6. **[ORBIT by dspaudio](https://github.com/dspaudio/orbit) ([Web Emulator](https://dspaudio.github.io/orbit-web-emu/)):**
    * **License:** Open Source (GPL-3.0). Based on SLOOP.
    * **Concept:** Groovebox with visual aesthetic and screen interfaces inspired by the Teenage Engineering OP-1.
    * **Features:** Integrated sample manipulation tools and an event tape mechanism for dynamically shifting and rearranging what the 4 tracks play.
    * **Installation:** Browser WebMIDI installer via USB.

 7. **[NoteSorcery by catacombius](https://github.com/catacombius/NoteSorcery):**
    * **License:** Open Source (GPL-3.0). Built on SLOOP.
    * **Concept:** OP-1-style 8-track groovebox firmware.
    * **Features:** Live USB audio sampling, project export straight to Ableton Live sets, companion Android controller application.
    * **Installation:** Build and flash via CLI toolchain.

 8. **[SLOOP ALG by shaw-core](https://github.com/shaw-core/Sloop_ALG02):**
    * **License:** Open Source (GPL-3.0-only). Based on SLOOP.
    * **Concept:** Experimental synthesis expansion fork adding Karplus-Strong string synthesis, plucked physical models, additive synthesis, DX7, and VA engines.
    * **Installation:** Web installer and companion editor.

 9. **[FM80S by Floydus (y6zkcqnf5r-hue)](https://github.com/y6zkcqnf5r-hue/fm1-fm80s):**
    * **License:** Open Source (GPL-3.0). Based on SLOOP 2.5 and Felucca.
    * **Concept:** Synthwave-oriented synth-looper firmware for live loop stacking, step sequencing, and song assembly with planned 8-track expansion.
    * **Installation:** Build from source via CLI toolchain.

10. **[SLOOP DX7 Banks by majnikool](https://github.com/majnikool/sloop-fm1):**
    * **License:** Open Source (GPL-3.0). Built on SLOOP by isod89.
    * **Concept:** SLOOP expansion fork supporting up to 12 DX7 voice banks grouped by sound category.
    * **Features:**
      * **12 Categorized DX7 Banks:** Direct flash storage and instant switching across 12 full DX7 voice banks (384 presets) categorized by instrument types (Keys, Bass, Leads, Pads, Strings, Brass, Percussion, FX).
      * **Fast Preset Navigation:** Instant preset category selection without overwriting SLOOP sequencer project states.
    * **Installation:** Build and flash via CLI toolchain (`tools/fm1_install.py`).

11. **[SLOOP Floyd FM by René Bohne](https://github.com/renebohne/sloop-fm1):**
    * **License:** Open Source (GPL-3.0). Fork of SLOOP by isod89.
    * **Concept:** SLOOP fork integrating Floyd Steinberg's 4-operator FM synthesis algorithms and real-time visual envelope feedback.
    * **Features:**
      * **Floyd Steinberg 4-OP FM Engine:** Adds dedicated 4-operator FM sound algorithms with custom modulation matrices and operator wave shaping.
      * **Live Envelope & Scope Display:** Real-time on-device oscilloscope rendering active voice output and ADSR envelope curve response directly on the 240 × 240 screen.
    * **Installation:** Build and flash via CLI toolchain.

12. **[SLICE64-FM by jeymadcat-ops](https://jeymadcat-ops.github.io/SLICE64-FM-web/):**
    * **License:** Open Source (GPL-3.0). Built upon SLOOP / Felucca core.
    * **Concept:** 64-slice sample chopper, beat-slicing, and FM groovebox firmware for the FM-1.
    * **Features:** Deep 64-slice sample mapping across pads/keys, auto-transient detection, slice reversal, pitch pitching per slice, and integrated FM synth accompaniment.
    * **Installation:** Browser WebMIDI installer via USB directly from the web project page.

13. **[winampFM by hericdk](https://github.com/hericdk/winampFM) ([Website & 3D Web Simulator](https://hericdk.github.io/winampFM/)):**
    * **License:** Open Source (GPL-3.0-only). Built upon SLOOP 2.6 (isod89) and Felucca (Leo Kuroshita / Hügelton Instruments).
    * **Concept:** Winamp 2.x-inspired performance synthesizer & groovebox firmware turning the FM-1 interface into classic Winamp windows (main player, equalizer sliders, playlist, and pixel-art visualizers).
    * **Features:**
      * **Winamp 2.x Main Screen & Playlist:** Main home screen styled as Winamp 2.x with time counter, audio spectrum analyzer, BPM, sound marquee, and track buttons. Sound presets browse like a Winamp playlist.
      * **Reel-to-Reel Tape Looping:** Tape deck recording screen with live input VU meter, tape counter, note display, and pass counts. Arming REC starts recording; pressing REC again calculates and locks the loop BPM automatically.
      * **Equalizer Sliders FX & PARTY Mode:** Effects grouped into Winamp equalizer slider bands (SEND, SPACE, MASTER, PARTY, TRACK) controlled via the 4 knobs. Dedicated PARTY performance staging (SOLO, DUEL, TRIAD, AUTOTURN stage cycling, KEEP lead holding, YOYO cross-track stepping).
      * **28 Full-Screen Pixel-Art Visualizers:** Pressing HOME twice unlocks 28 reactive full-screen visualizers responding to played notes, loops, and knobs (Milkdrop-style oscilloscope, spectrum bars, starfield shooter, 80s neon night drive, polygonal chords, doomscrolling feed, dancing raccoon, and lofi study).
      * **Expanded Sound Library & Tapes Carousel:** 157 total sounds (including 153 SLOOP 2.6 sounds plus Brazilian acoustic instruments: Cavaquinho, Berimbau, Agogô Bell, Sanfona, and Brasil drum kits), with a PS1-style 3D cassette tape preview carousel.
      * **Web 3D Simulator & Recorder:** Includes an interactive in-browser 3D model simulator running the real firmware via WebAssembly with audio playback and a Win98-style screen & sound recorder widget.
    * **Installation:** One-click WebMIDI installer via USB directly on the website or flashing `release/winampfm-0.12.fwsc`.

#### 1.1.3. FoMni Family (Strumplate & Chord Instruments)

Suzuki Omnichord and Japanese Shigin accompaniment instruments featuring strumplate and chord-shaping workflows:

 1. **[FoMni-1 by charlesvestal](https://github.com/charlesvestal/fm1-fomni) ([Web Installer](https://charlesvestal.github.io/fm1-fomni/)):**
   * **License:** Open Source (GPL-3.0).
   * **Concept:** Suzuki Omnichord-inspired chord harp firmware for the FM-1.
   * **Features:** Strum chords across the white keys like a harp strumplate, select chord roots and types on the black keys, integrated rhythmic accompaniment and arpeggiator modes.
   * **Installation:** Browser WebMIDI installer via USB.

 2. **[FuMi-1 by cartesive](https://github.com/cartesive/fumi-1) ([Web Installer & Emulator](https://cartesive.github.io/fumi-1/)):**
    * **License:** Open Source (GPL-3.0). Fork of FoMni.
    * **Concept:** Traditional Japanese Shigin accompaniment synthesizer inspired by Suikohsha's ST-50.
    * **Features:** Authentic Koto, Sho, Shakuhachi, and Taiko voices tuned to the historical ST-50 just intonation scale system.
    * **Installation:** Browser WebMIDI installer via USB.

#### 1.1.4. Independent & Original Engine Firmwares

Firmwares featuring original sound engines, written-from-scratch architectures, or specialized controller frameworks:

 1. **[baud girl Custom Firmware Mod](https://baudgirl.com/) ([MIDI & SysEx Guide](https://m-vave-fm1-midi-guide.up.railway.app/)):**
   * **License:** Closed Source.
   * **Features:** Comprehensive overhaul and reimagining of the stock firmware ergonomics and controls. Adds Virtual Analog (VA) synthesizer engines and a 64-step sequencer.
   * **Documentation:** [FM-1 MIDI & SysEx Guide](https://m-vave-fm1-midi-guide.up.railway.app/) — exhaustive human-readable documentation of channels, SysEx structure, CC mappings for internal DSP effects, and clock synchronization.
   * **Video Tutorial:** [Baud Girl FM-1+VA Comprehensive Tutorial (NatLife Sounds)](https://www.youtube.com/watch?v=jfuoEBIUsEE) — programming VA engines and the dot-matrix sequencer.
   * **Installation:** Web-based browser installer in a couple of clicks via WebMIDI.

 2. **[Groove OS](https://www.groove-os.com/) ([Web Emulator](https://www.groove-os.com/emu)):**
   * **License:** Commercial / Proprietary ($29).
   * **Concept:** Transforms the FM-1 into a standalone multitrack groovebox without needing any external equipment.
   * **Features:** Up to 8 independent tracks (drums, bass, chords, leads) with independent loop lengths (1 to 8 bars) for evolving polyrhythmic structures, dual sound engine (native 6-op FM + Virtual Analog with ladder filter), up to 20 voices of polyphony (12 FM + 8 VA, max 6 for drums), 64-step sequencer with parameter locks (p-locks), live stage view, curated sound packs, and DX7 SysEx patch reception.
   * **Installation:** Browser-based USB installer via WebMIDI in Chrome/Edge (~2 minutes).

 3. **[Bubba Machine by Erbubar23](https://github.com/Erbubar23/bubba-machine) ([Website](https://erbubar23.github.io/bubba-machine/) | [Web Emulator](https://erbubar23.github.io/bubba-machine/emulador.html) | [Manual](https://github.com/Erbubar23/bubba-machine/blob/main/docs/MANUAL.md)):**
    * **License:** Open Source (GPL-3.0-or-later). Written from scratch in C99.
    * **Concept:** 6-track live performance groovebox firmware for the FM-1 with four gestures per button, dedicated HOME layer, and zero third-party audio dependencies (all factory kits and wavetables synthesized procedurally in C).
    * **Features:**
      * **6 Flexible Tracks:**
        * `T1` TR-Style Drum Machine: 16 instruments with independent polymeter track lengths, accent, ratchets, flam, parameter locks (P-Locks), fill-only steps, and live TR-style roll/erase while running.
        * `T2` Sampler 3.0: 8-slice loop engine reassembled bar-by-bar via algorithmic generator (`TU` programmed row vs `SUENA` played row), integrated sample recorder, take library, slice editor, and 3-band frequency waveform visualization (low/mid/high).
        * `T3` Wavetable Bass: Glide and wavetable synthesis.
        * `T4–T6` Assignable Tracks: Configurable as `SYNTH`, `MONO`, `KIT` (secondary drum machine), or `MIDI`. Per-track arpeggiator, looper, and dedicated musical scale.
      * **Polymeter & Independent Track Timing:** Each track features independent length (1–64 steps) and clock multipliers/dividers (×2 to ×1/4).
      * **Chord Grid:** 16 color-coded chords displaying scale degree and harmonic function.
      * **Live Performance & Safe Flash:** 4 chained scenes, song recording, auto-fills, 16 punch-in FX, track/instrument mutes, and crash-resilient flash saving (CRC, end commit, wear-leveling, and auto-save on stop).
    * **Status & Installation:** Firmware runs in desktop simulation and the in-browser WebAssembly emulator; hardware flasher/installer is in roadmap development.

 4. **[zp12 by Sven Trogus (zvenson)](https://github.com/zvenson/zp12) ([Web Installer & Homepage](https://zp12.designburgapps.com/)):**
    * **License:** Open Source (GPL-3.0-only).
    * **Concept:** Authentic 1980s-style 12-bit sampling drum machine firmware for the FM-1.
    * **Features:**
      * **Lo-Fi 12-Bit Sound Engine:** 32 pads across 4 banks running at 26.04 kHz (or 27.5 kHz). Samples are pitched via pure playback rate skipping without interpolation for authentic gritty 80s aliasing and grain.
      * **8 Filtered Channels:** Independent channel playback where new hits cut previous ones. Channels 1–2 feature a resonant 4-pole low-pass filter closing with decay, channels 3–6 have fixed filters, and knobs act as channel faders.
      * **Performance & Sequencing:** 11 loops triggered on black keys, 4 chained songs, real-time recording with auto-correct and 16-step grid editing, classic MPC-style swing (50–71%), and 4 punch-in FX (beat repeat/roll, reverse, tape stop).
      * **Browser Sample Dropper:** In-browser tool to drop custom user WAVs onto pads and transmit them directly to flash over WebMIDI.
    * **Installation:** Web-based browser installer via WebMIDI in Chrome/Edge.

 5. **[FiMba-1 by J. Adam Sowers (jadamsowers)](https://github.com/jadamsowers/fm1-fimba) ([Web Installer & Emulator](https://jadamsowers.github.io/fm1-fimba/)):**
    * **License:** Open Source (GPL-3.0-only).
    * **Concept:** Thumb piano / kalimba / mbira physical modeling synthesizer firmware for the FM-1.
    * **Features:**
      * **Physical Modeling Engine:** Detailed kalimba acoustic simulation running at 44.1 kHz, featuring modeled tines (material hardness, decay, tone, worn character, tuning, release), resonator bodies (box, gourd, board, buzzers, wah resonance), and built-in effects (space reverb/delay, lo-fi/tape color, chorus, filter, and granular cloud engine).
      * **Keyboard & Key Layouts:** Traditional kalimba *Tine* layout (lowest C4 tine in the center, alternating outwards across white keys) or chromatic *Keyboard* layout. Black keys configurable for thumb-roll chord accompaniment, sharps, or performance modifiers (mute, sound hole covering, freeze, octave shift).
      * **Built-in Sequencer/Arpeggiator:** Mbira pattern generator over chords and live playing.
      * **WebAssembly Browser Emulator:** Complete C sound engine and UI compiled to WebAssembly running in-browser with Web MIDI and preset saving.
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

 6. **[Lunar Modulator by ip2k](https://github.com/ip2k/lunar-modulator):**
   * **License:** Open Source (MIT).
   * **Status:** Research / bench stage.
   * **Features:** *Intergalactic Modulation Station* — alternative firmware based on Mutable Instruments synthesizer engines, a Movy-style sequencer, and an in-browser virtual FM-1 emulator/simulator.

 7. **[AMB-1 by Charles Vestal](https://github.com/charlesvestal/fm1-amb) ([Web Installer & Emulator](https://charlesvestal.github.io/fm1-amb/) | [Manual](https://charlesvestal.github.io/fm1-amb/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Generative ambient synthesizer machine inspired by Brian Eno's *Music for Airports*.
    * **Features:** Self-generating playback immediately from power-on, unsynced tape loops of unequal lengths, gliding bass lines, and generative Euclidean percussion patterns.
    * **Installation:** Browser WebMIDI installer via USB.

 8. **[CTL-1 by Charles Vestal](https://github.com/charlesvestal/fm1-ctl) ([Web Installer](https://charlesvestal.github.io/fm1-ctl/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Dedicated MIDI master controller firmware for the FM-1.
    * **Features:** Turns the FM-1's keys and knobs into a multi-channel USB/TRS MIDI controller while providing internal General MIDI sounds for standalone monitoring.
    * **Installation:** Browser WebMIDI installer via USB.

 9. **[PurpleMonkey FM-1 by Quixotic7](https://github.com/Quixotic7/PurpleMonkeyFM1) ([Web Emulator](https://quixotic7.github.io/PurpleMonkeyFM1/emu/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Simplified toddler music instrument featuring a 5-note pentatonic scale, backing drum beats, and zero menus.
    * **Installation:** Browser WebMIDI installer via USB.

10. **[FM-1 B-Boy Edition by friendsmakenoise-prog](https://github.com/friendsmakenoise-prog/fm1-pocket-sampler):**
    * **License:** Open Source (No license specified in upstream repository).
    * **Concept:** Late-1990s hip-hop chop sampler firmware featuring 3 sample tracks and a dedicated FM bass/lead lane.
    * **Installation:** Web installer via USB.

11. **[fm1-polyseq by NOVALENTI](https://github.com/NOVALENTI/fm1-polyseq):**
    * **License:** Open Source (No license file in repository; source code is publicly accessible).
    * **Concept:** Polyphonic 16-step sequencer and bare-metal hardware abstraction layer (HAL) written in strict C99 for the AC791N's pi32v2 CPU.
    * **Installation:** Compile from source.

12. **[FM-106 by PattF](https://github.com/patttf/fm-106) ([Librarian & SysEx Editor](https://patttf.github.io/fm-106/Librarian.html)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Roland Juno-106 emulation firmware for the FM-1 based on an optimized port of the open-source KR-106 synthesizer engine.
    * **Features:**
      * **Full 6-Voice Polyphony:** Authentic Juno DCO sound generation hitting ~30% CPU load across both JieLi `pi32v2` cores.
      * **Oscilloscope & Real-Time Controls:** Split on-device display showing the live oscilloscope waveform alongside simultaneous filter, envelope, and oscillator parameters.
      * **Juno-106 SysEx Patch Compatibility:** Direct `.syx` patch import and management via companion web Librarian.
      * **Bank Management:** 4 banks (2 factory banks + 2 user banks) selectable via the `ALGORITHM` encoder, with on-device patch naming and saving.
      * **USB-C Audio:** Integrated class-compliant digital stereo audio output over USB-C.
    * **Installation:** Browser WebMIDI installer via USB.

13. **[ETCH by SikkenWorks](https://github.com/SikkenWorks/ETCH) ([Homepage & Web Installer](https://etch.sikkenworks.com/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** "Draw. Morph. Modulate." — waveform drawing and morphing synthesizer firmware.
    * **Features:** 8-voice polyphony, direct on-device single-cycle waveform drawing (Waves A, B, and modulating Wave C), real-time interpolation/morphing between drawn waves, wave library, motion recording, and arpeggiator with generative RIFF mode.
    * **Installation:** Browser WebMIDI installer via USB or flashing prebuilt `.fwsc` image.

14. **[AMBII by MilkBoyG / JalopyMusic](https://github.com/JalopyMusic/fm1-milkboyg-ambii):**
    * **License:** Open Source (GPL-3.0). Built on Melodee and Felucca.
    * **Concept:** Alternative performance and recording interface firmware built on Melodee's real multi-engine C core.
    * **Features:** Four tracks with scoped pattern actions, drum ratchets, parameter automation graphs with undo, shared delay/reverb, and dedicated Galaxy / Dark Matter UI themes.
    * **Status:** In-browser prototype and development preview (no hardware release image yet).

15. **[MC-1 by dspaudio](https://github.com/dspaudio/mc-1) ([Web Hub & Online Player](https://dspaudio.github.io/mc-1-web/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** 4-track groovebox firmware inspired by Roland Linear Arithmetic (LA) synthesis (D-50) and MC-series grooveboxes (MC-101 / MC-303).
    * **Features:**
      * **LA Synthesis Sound Engine:** Combines PCM attack transients with synthesized sustaining partials, driving authentic late-80s digital/analog hybrid timbres.
      * **4 Tracks & Performance Sequencer:** Dedicated lanes for Drums, Bass, Chords, and Lead/Arp with step sequencing and live parameter modulation.
      * **Drum & Acid Generators:** Built-in synthesized TR-style rhythm voices and resonant 303 acid line generator.
      * **Dedicated Web Companion:** Web audio player and patch tool running at `dspaudio.github.io/mc-1-web`.
    * **Installation:** Browser WebMIDI installer via USB directly from the web hub or build from source.

16. **[OberVave by Sven Trogus (zvenson)](https://github.com/zvenson/obervave) ([Webpage & Web Installer](https://fm1.designburgapps.com/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** 8-voice American analog polysynth emulation (Oberheim OB-Xa / OB-8 style, 1979–1984) for the M-VAVE FM-1.
    * **Features:**
      * **Classic 8-Voice Polysynth Architecture:** Dual oscillators per voice with sawtooth and pulse (PWM) waves, hard oscillator sync, cross-modulation, and white noise generator.
      * **Morphing 12/24 dB Resonant Filter:** Continuous morphing between 2-pole (12 dB/oct Oberheim SEM style) and 4-pole (24 dB/oct Curtis/CEM style) low-pass filter responses with dedicated envelope modulation.
      * **Vintage Drift & Unison:** Modeled analog voice circuit drift, polyphonic unison/detune stack, dual LFOs, and vintage chorus/delay spatial effects.
      * **On-Device Graphical Editing:** Real-time filter frequency curve rendering and envelope visualization on the 240 × 240 display.
    * **Installation:** Browser WebMIDI installer via USB directly from the project homepage.

17. **[MONK-1 by Charles Vestal](https://github.com/charlesvestal/fm1-monk) ([Web Emulator](https://charlesvestal.github.io/fm1-monk/emu/) | [Web Installer](https://charlesvestal.github.io/fm1-monk/install/) | [Manual](https://charlesvestal.github.io/fm1-monk/manual/) | [Releases](https://github.com/charlesvestal/fm1-monk/releases)):**
    * **License:** Open Source (GPL-3.0). Free of charge (donations suggested to savetibet.org).
    * **Concept:** Formant vocal synthesizer firmware turning the FM-1 into Jonathan Taylor's **MonkSynth** (homage to AudioNerdz's 2002 *Delay Lama* plug-in) with twelve singing characters (Jerry the monk, Philip the unicorn, Snider, etc.).
    * **Features:**
      * **12 Animated Singing Characters:** Each character sings with its own vocal tract size and voice; mouth animations follow vowels in real-time sprite frames on the color screen.
      * **Native Velocity & Pressure/Aftertouch:** Leverages the FM-1's stock capacitive keys without hardware modifications (via [Velo](https://github.com/charlesvestal/fm1-velocity) sensing algorithms) to control note loudness via strike velocity and vowel morphing/pitch bends via pressure aftertouch.
      * **Dedicated Vocal Controls:** Gliding legato mono voice, Choir/Unison stack (1–10 voices with detune and head size spread), vibrato rate/depth, echo delay, ADSR envelopes, and octave switching.
      * **USB MIDI & Accessibility:** Full USB-MIDI in/out with polyphonic aftertouch and vowel CC controls; integrates with the [FM-1 Screen Reader](https://charlesvestal.github.io/fm1-reader/) to speak aloud on-screen parameters and button actions for visually impaired users.
    * **Installation:** Browser WebMIDI installer via USB, in-browser WebAssembly emulator, or flashing prebuilt releases.

18. **[M-VAVE FM1 Open Firmware (m-vave/fm1_open)](https://github.com/m-vave/fm1_open) ([Releases / V10](https://github.com/m-vave/fm1_open/releases) | [Official Workbench (Offline)](https://open.m-vave.com/fm1-workbench) | [Cached Workbench on Reddit](https://www.reddit.com/r/MVaveFM1/comments/1x5y4qy/cached_web_page_for_the_open_workbench/)):**
    * **License:** Open Source (GPL-3.0-only for application code; includes vendor binary libraries and third-party notices).
    * **Significance:** Official open-source release of the factory FM-1 firmware and SDK directly from the manufacturer (M-VAVE).
    * **Status Notice:** While upstream links (`m-vave/fm1_open` and `open.m-vave.com`) were taken down by M-VAVE, a [cached copy of the open workbench](https://www.reddit.com/r/MVaveFM1/comments/1x5y4qy/cached_web_page_for_the_open_workbench/) is preserved and shared on the r/MVaveFM1 subreddit (allowing in-browser WebAssembly simulation, firmware flashing, and stock V15 recovery).
    * **Architecture & Features:**
      * **8 Tracks & 8 Sample Slots:** Full multitrack groovebox architecture with 8 audio/synth tracks, 8 sample slots, and 16 built-in demo presets/FX.
      * **Board Drivers & Audio HAL:** Direct hardware C source code for panel controls, 240 × 240 display, encoders, and audio engine rendering (`app/board/`, `app/audio_output.c`) supporting USB/Bluetooth mixing and USB recording.
      * **Complete Toolchain & WebAssembly Workbench:** Complete build scripts (`build.bat`) supporting both native firmware compilation via JieLi PI32v2 Clang 4.0.1 (`FM1_OFFICIAL_OPEN.fwsc`) and WebAssembly compilation via WASI SDK 27 for in-browser workbench simulation.
    * **Installation:** Web workbench flasher via USB (using cached page shared on Reddit), official flasher, or building `.fwsc` from source.




### 1.2. Modular Firmware Platforms & Builders

 1. **[fm1-rocket-os by cmlarsen](https://github.com/cmlarsen/fm1-rocket-os):**
    * **License:** Open Source (GPL-3.0). Forked from X0X and Felucca.
    * **Concept:** Clip-launching performance firmware turning the FM-1 into an Ableton Live-style clip launcher and matrix sequencer.
    * **Status:** Work in progress.

 2. **[Optimist by w0ts](https://github.com/w0ts/optimist):**
    * **License:** Open Source (GPL-3.0-only). Derived from SLOOP, Felucca, Melodee, and X0X.
    * **Status:** In active development (tested in emulator).
    * **Concept:** Modular firmware builder and platform allowing users to custom-assemble FM-1 firmware images tailored to flash and RAM budgets.
    * **Features:**
      * **Firmware Builder (`make builder`):** Choose specific synth engines (ANALOG 2, DIGITAL, PHASE, LOFI, SAMPLE, VOICE, TRIO, WHEEL, GRAIN, FM6, SLICE, PHYS, ACID), drum kits, effects (DUST, DUCK, DJ filter, delay, reverb), and sequencer capabilities at compile-time.
      * **Multi-Layer UI & Sequencer:** SLOOP-style live button-held layers, per-track patterns, scenes, snapshots, fills, microtiming, and parameter locks.
      * **SLOOP 2.4 Project Compatibility & Web Editor:** Full project interchangeability and web-based parameters librarian.
    * **Installation:** Build and flash via CLI/Docker toolchain.

 3. **[Dinghy by Sven Trogus (zvenson)](https://github.com/zvenson/dinghy):**
    * **License:** Open Source (GPL-3.0-only).
    * **Concept:** Minimal, clean firmware skeleton for custom developers: 4-voice sine wave synthesizer on top of working display, audio DMA, and button input drivers.
    * **Installation:** Compile and flash via Makefile/CLI.

 4. **[Modular-1 by morgulbrut](https://wiggismodular.github.io/Modular-1/) ([Webapp & Flasher](https://wiggismodular.github.io/Modular-1/)):**
    * **License:** Open Source (GPL-3.0). Built using Felucca HAL and tooling.
    * **Concept:** Nord Modular-inspired modular synthesizer engine and visual web patch editor for the FM-1.
    * **Features:**
      * **Browser Patch Editor:** Interactive visual web environment allowing users to construct modular signal paths, configure modules, and upload patches directly to the FM-1 hardware.
      * **Module Architecture & Matrix:** Modules feature parameter inputs (`p1` and `p2` with attenuverters) alongside an assignable modulation matrix routing global `p1`/`p2` and contextual `k1`–`k4` knob controls per module.
      * **Generative Arpeggiator:** Complex multi-page arpeggiator engine featuring dedicated melody controls (scale, root, speed), Euclidean rhythm sequencing (pulses, rotation, rate), and chaotic generative probability/octave spreading.
    * **Installation:** Browser WebMIDI installer via USB directly under the webapp's Flash tab.

 5. **[Hexagon Console](https://www.reddit.com/r/MVaveFM1/comments/1x5qq7z/coming_soon_hexagon_console/):**
    * **Status:** Upcoming / Teased announcement.
    * **Concept:** Console-style musical environment and custom firmware architecture for the M-VAVE FM-1.
    * **Details:** Teased within the r/MVaveFM1 community ([Coming soon: Hexagon Console](https://www.reddit.com/r/MVaveFM1/comments/1x5qq7z/coming_soon_hexagon_console/)), introducing a modular hexagonal UI paradigm and performance console interface tailored for the FM-1 hardware.

### 1.3. Gaming, Emulators & Non-Audio Ports (Games & Experiments)

 1. **[FM-1 Doom by Sven Trogus (zvenson)](https://github.com/zvenson/fm1doom) ([Web Installer](https://doom.deadlockinteractive.com/) | [Alt Web Installer](https://dx7.designburgapps.com/doom/)):**
    * **License:** Open Source (GPL-2.0-or-later / GPL-3.0; FreeDM game data under BSD-3-Clause). Based on doomgeneric, Chocolate Doom, and the sloopDX / SLOOP / Felucca platform.
    * **Concept:** Port of classic Doom (running a FreeDM arena map) on the M-VAVE FM-1 synthesizer hardware.
    * **Features:**
      * Rendered directly to the FM-1's color screen with health, armor, ammo, and automap overlay.
      * Controls mapped to physical synthesizer keys and knobs: F3/B3 or KNOB 1 to turn, A3/G3 forward/back, OCT−/OCT+ or F#3/G#3 to strafe, C5/PLAY to fire, D5/REC to open/use, E5 to run, C#5/D#5/F#5 weapon selection (fist, pistol, shotgun), ARP for automap, and FX for brightness.
      * Preserves sloopDX projects in flash without overwriting user patch data.
    * **Installation:** Browser WebMIDI installer via USB directly from the project page.

 2. **[FM-1 NES by Keitark](https://github.com/Keitark/fm1-nes) ([App Updates Guide](https://github.com/Keitark/fm1-nes/blob/main/APP_UPDATES.md)):**
    * **License:** Open Source (Apache-2.0).
    * **Status:** Experimental / Source only (reference proof-of-concept).
    * **Concept:** Nintendo Entertainment System (NES) emulator running on the FM-1 hardware.
    * **Features:** Uses the FM-1's 27 keys as the game controller and its color screen as the television display. Developed as a worked example and educational kit for writing bare-metal FM-1 firmware from scratch.
    * **Documentation:** [FM-1 NES APP_UPDATES.md Guide](https://github.com/Keitark/fm1-nes/blob/main/APP_UPDATES.md) — developer guide detailing application-only updates (`app.bin`) that preserve the stock USB bootloader.
    * **Installation:** Compile from source (no web installer or prebuilt release; does not produce audio/music).

 3. **[Mocky by Charles Vestal](https://github.com/charlesvestal/fm1-mocky) ([Web App](https://charlesvestal.github.io/fm1-mocky/)):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Display testing firmware and web companion for transmitting and displaying arbitrary bitmap pictures on the FM-1's color screen over WebMIDI.
    * **Installation:** Browser WebMIDI installer via USB.

 4. **[fm1-mdx by Keitark](https://github.com/Keitark/fm1-mdx):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Experimental Sharp X68000 MDX/PDX karaoke music player running a software YM2151 FM chip emulation allowing interactive part muting and live keyboard accompaniment.
    * **Installation:** Research project / computer emulator testing.

 5. **[GameDude by Chance The Maker](https://github.com/ChanceTheMaker/gamedude-fm1-smk) ([Web Simulator & Compiler](https://chancethemaker.github.io/gamedude-fm1-smk/)):**
    * **License:** Open Source (GPL-3.0). Built on Peanut-GB and Felucca.
    * **Concept:** Nintendo Game Boy emulator, browser-based ROM-to-firmware compiler, and interactive web simulator for the M-VAVE FM-1 and SMK-37 controller hardware.
    * **Features:**
      * **Peanut-GB Core Port:** Optimized Game Boy emulator core running at smooth framerates on the JieLi AC791N RISC CPU.
      * **Web ROM Compiler & Simulator:** Drag-and-drop any Game Boy `.gb` ROM into the browser to test it immediately in the WebAssembly simulator and generate a flashable `.fwsc` firmware image in seconds.
      * **Ergonomic Synth-Key Layout:** Physical synth keys mapped intuitively to D-pad (Up/Down/Left/Right), A/B buttons, and Start/Select, with knob controls for volume, display brightness, and color palette cycling (classic DMG pea-soup green, pocket grayscale, neon cyberpunk).
      * **Dual Device Support:** Supports both the FM-1 synthesizer and SMK-37 keyboard controller hardware.
    * **Installation:** Browser WebMIDI installer via USB directly from the web compiler page.

 6. **[Fart Machine One by adamcharleswilsonmusic-code](https://github.com/adamcharleswilsonmusic-code/Fart-Machine-One):**
    * **License:** Open Source (GPL-3.0).
    * **Concept:** Novelty joke sample-synthesizer and sequencer firmware for the FM-1.
    * **Features:** 11 distinct pitched flatulence sample sounds, integrated 16-step sequencer, dynamic pitch modulation, and onboard stereo delay and reverb effects.
    * **Installation:** Build and flash via CLI toolchain.

### 1.4. Stock Firmware Patchers & Binary Mods

 1. **[FM-1 Firmware Patcher by Christian Zietz (czietz)](https://github.com/czietz/fm1-firmware-patcher):**
    * **License:** Open Source (Unlicense / Public Domain).
    * **Target:** Stock official **V15** firmware (`FM-1.fwsc`).
    * **Modifications & Bug Fixes:**
      * Fixes the oscillator detune calculation in the stock synth engine to accurately match Dexed / Yamaha DX7 behavior.
      * Disables unhandled MIDI aftertouch messages that cause unwanted heavy vibrato.
      * Modifies the UI colorway: changes the main oscilloscope display to dark blue and the FX selection cursor to green (as visual confirmation of patched firmware).
    * **Usage:** Python patcher script applying precise binary offsets (`python patch_firmware.py FM-1.fwsc FM-1-fixed.fwsc`). Flashed via M-VAVE's M-UPGRADE utility.

 2. **[FM-1 Macropad Patch by smememe](https://github.com/smememe/fm1-macropad-patch) ([Web Patcher](https://smememe.github.io/fm1-macropad-patch/)):**
    * **License:** Open Source (MIT).
    * **Target:** Stock official **V15** firmware (`FM-1.fwsc`).
    * **Concept & Modifications:** Binary patch that transforms the FM-1 into a 55-input MIDI macro pad controller. Modifies the firmware so every physical button, piano key, and rotary knob sends a USB-MIDI note message while turning off all LEDs. Combined with desktop hotkey software, it converts the synthesizer into an external macro pad.
    * **Usage:** Apply patch directly in the browser via WebAssembly/WebMIDI or via Python script (`python3 fm1patch.py FM-1.fwsc`). Flashed via standard update tools.

> [!TIP]
> **Community Flashing Experience & Safe Upgrade Practice:**  
> While not an absolute hard rule, there is a prominent community recommendation to avoid flashing one custom firmware directly over another. To minimize bricking risks, some users suggest rolling back to the official stock firmware (v15) via M-VAVE's official updater first, and only then flashing the next custom firmware build.

---

## 2. Hardware Architecture & Reverse Engineering Reference

All technical deep dives, hardware reverse engineering findings, bootloader memory maps, and protocol specifications are documented in **[REVERSE_ENGINEERING.md](REVERSE_ENGINEERING.md)**:

* **Hardware & Ecosystem Overview:** JieLi AC791N SoC specs, devboard details, PCB characteristics, and teardown instructions.
* **Device Recovery Vectors:**
  * **Plain USB Unbricking:** Soft-brick recovery directly into `WL82 UBOOT1.00` mask-ROM mode via `jl-uboot-tool` and `MvaveFM1Unbricker` without opening the casing.
  * **Hardware `USB_KEY` Mask-ROM Recovery:** Forcing mask-ROM USB download mode on frozen/hard-bricked processors using an external RP2040 dongle ([FM-1 Transporter](https://github.com/kurogedelic/FM-1-transporter)) pulsing the JieLi hardware boot key (`0x16EF` at ~50 kHz) over USB D+/D- lines, with community wiring instructions for Seeed XIAO RP2040 / Raspberry Pi Pico (Green to D6, White to D7, Black to GND).
* **Firmware Container Analysis:** Embedded `.fwsc` firmware extraction from `M-UPGRADE-FM1` (Qt resource layout, `@JMUA` / `JLUFW` signatures).
* **MIDI SysEx OTA Protocol:** Handshake, parameter query behavior, and verified two-step device-pull session flow with 8→7 LSB-first bitstream encoding.
* **Memory Map & Bootloader:** Flash partitions (UBOOT, App, VM), linker script requirements, and critical bootloader re-entry guidelines.
* **Binary References & Offsets:** Magic numbers, Qt container offsets, and symbol references.
* **Firmware Size Boundaries:** SPI flash memory budget, execution model (XIP), and partition limits.
* **Python Firmware Utility:** CLI utility ([`fm1_flasher.py`](fm1_flasher.py)) for extracting firmware images and exploring protocol exchanges.
* **Disassembly & Tooling:** Ghidra processor module ([`ghidra-jieli`](https://github.com/kagaimiq/ghidra-jieli)) and official Pi32v2 toolchain notes.

**Read the full documentation:** **[REVERSE_ENGINEERING.md](REVERSE_ENGINEERING.md)**

---

## 3. External References & Resources

Useful open-source tools, documentation, and SDK repositories:

### 3.1. Hardware Recovery, Bootloaders & Firmware Flashers

 1. **[jl-uboot-tool Repository](https://github.com/kagaimiq/jl-uboot-tool):**
    Utility for interacting with JieLi UBOOT bootloaders over USB Mass Storage / SCSI pass-through.

 2. **[Unbricking a Soft-Bricked FM-1 over Plain USB (Reddit Guide by acrawf1)](https://www.reddit.com/r/MVaveFM1/comments/1wz48t7/guide_unbricking_a_softbricked_fm1_black_screen/):**
    Detailed community guide for recovering devices stuck on a black screen in `WL82 UBOOT1.00` mode (`VID_4C4A:PID_8057`) via plain USB cable and `jl-uboot-tool` without extra hardware. Includes the [`fm1_extract_app.py` helper script](https://gist.github.com/Acrawf1/ae2b9930b49231db397568cfc2abc2a8).

 3. **[FM-1 Transporter by Leo Kuroshita (kurogedelic)](https://github.com/kurogedelic/FM-1-transporter) ([Hard Brick Recovery Guide](https://www.reddit.com/r/MVaveFM1/comments/1x5lifu/mvave_fm1_unbricking_after_a_hard_brick_using_a/)):**
    Hardware RP2040-based USB dongle firmware that pulses the JieLi `USB_KEY` pattern (`0x16EF`) to force unresponsive FM-1 devices into mask-ROM USB download mode for emergency flash recovery. See the practical community walkthrough for wiring a Seeed XIAO RP2040 or Raspberry Pi Pico (Green to D6, White to D7, Black to GND) and recovering via `jl-uboot-tool`: [Reddit: Unbricking after a hard brick using a RP2040 and the FM-1 Transporter](https://www.reddit.com/r/MVaveFM1/comments/1x5lifu/mvave_fm1_unbricking_after_a_hard_brick_using_a/).

 4. **[MvaveFM1Unbricker by Quixotic7](https://github.com/Quixotic7/MvaveFM1Unbricker) ([Troubleshooting Guide](https://github.com/Quixotic7/MvaveFM1Unbricker#troubleshooting)):**
    Python-based unbricking toolkit and comprehensive troubleshooting reference for M-VAVE FM-1 recovery. Automates safe backup and restoring via `jl-uboot-tool` (strictly protects the `< 0x4000` boot head, prevents `erasechip`, and verifies flash SHA-256), while providing procedures for forcing unresponsive units into ROM boot (watchdog timeouts, OCT-/OCT+ holds, quick power cycles) and RP2040 Transporter hardware recovery.

 5. **[flipper-fm1-recovery by merthsoft](https://github.com/merthsoft/flipper-fm1-recovery):**
    Firmware flasher and unbricker utility utilizing a **Flipper Zero** to pulse the hardware ROM recovery sequence on the FM-1's USB data pins without requiring an RP2040 dongle or wiring.

 6. **[fm-static by seajaysec](https://github.com/seajaysec/fm-static) ([Web App](https://seajaysec.github.io/fm-static/)):**
    WebMIDI flasher solving the issue where an FM-1's USB-MIDI port identifies under an unusual/renamed descriptor, which causes official updaters to report the synthesizer as missing.

 7. **[fm1-linux-update by fuleo](https://github.com/fuleo/fm1-linux-update):**
    Linux CLI updater tool for flashing and verifying stock V14 to V15 firmware binaries over USB-MIDI.

 8. **[FM-1 Firmware Patcher by Christian Zietz](https://github.com/czietz/fm1-firmware-patcher):**
    Python patcher utility applying fixes to the official stock V15 firmware binary: corrects oscillator detune to match Dexed, strips unexpected MIDI aftertouch vibrato, and updates oscilloscope/cursor palette.

 9. **[JieLi USB Boot Key Activation (jielie docs)](https://kagaimiq.github.io/jielie/isp/usb/usb-key.html):**
    Documentation on triggering JieLi hardware USB boot loader mode via D+/D- signal patterns and ISP keys.

10. **[ip2k/mvave-fm1-open-firmware Repository](https://github.com/ip2k/mvave-fm1-open-firmware):**
    Research project towards an open-source firmware for the M-VAVE FM-1. Includes specification, reference implementation, and simulation testbench for an **RP2040-based `USB_KEY` hardware recovery dongle** (`dongle/` directory) that forces the JieLi AC791N SoC into mask-ROM USB download mode (`UBOOT1.00`) via the external USB-C port, enabling low-level flash backup and unbricking.

### 3.2. Reverse Engineering, Disassembly & Decompilation

 1. **[M-VAVE FM1 Hardware Architecture & Protocol Reference (Local)](REVERSE_ENGINEERING.md):**
    In-depth local technical reverse-engineering documentation: JieLi AC791N hardware overview, UBOOT memory map, Qt container analysis, verified two-step device-pull SysEx OTA protocol, and flasher implementation.

 2. **[AL-255/FM-1-RE Repository](https://github.com/AL-255/FM-1-RE):**
    Reverse-engineering repository for M-VAVE FM-1 firmware. It reveals that the stock FM-1 firmware itself utilizes a Dexed/msfa-derived 6-operator FM synthesis engine, and contains V13/V14 disassembly function maps, XIP flash offset analyses, as well as an experimental custom firmware build.

 3. **[ghidra-jieli Repository](https://github.com/kagaimiq/ghidra-jieli):**
    Ghidra processor extension for disassembling and decompiling JieLi `pi32`, `pi32v2`, and `q32s` CPU binaries.

 4. **[fm1-bootloader by jvitkauskas](https://github.com/jvitkauskas/fm1-bootloader):**
    Readable C source implementation of the stock FM-1 bootloader, reverse-engineered and reconstructed byte-identically from the hardware image.

 5. **[MVAVE-M-UPGRADE-decompiled by entitymar](https://github.com/entitymar/MVAVE-M-UPGRADE-decompiled):**
    Full decompilation and resource extraction of the official M-VAVE M-UPGRADE macOS and Windows updater applications.

 6. **[jl-misctools Repository](https://github.com/kagaimiq/jl-misctools):**
    Utilities for inspecting and converting JieLi firmware containers, key files, and UI resources.

 7. **[M-VAVE SMK-37 PRO Reverse Engineering Gist (by probonopd)](https://gist.github.com/probonopd/18b3ed65a69d0229eb630c47d7e316dc):**
    Research notes on unpacking `.fwsc` firmware files for the M-VAVE SMK-37 PRO (DX7 FM MIDI keyboard) and identifying the underlying JieLi AC791N platform structure using `jl-misctools`.

### 3.3. Vendor SDKs, Architecture & JieLi Community Research

 1. **[JieLi AC79 AIoT SDK (Gitee Repository)](https://gitee.com/Jieli-Tech/fw-AC79_AIoT_SDK):**
    Official C SDK codebase for AC79 series (WL82 / AC791N) microcontrollers, containing board support packages (BSP), linker scripts, and hardware register headers.

 2. **[JieLi AC79 Official Peripheral Documentation](https://doc.zh-jieli.com/AC79/zh-cn/release_v1.0.3/module_example/peripherals/sd.html):**
    Official documentation covering AC79xx series peripheral hardware modules (SD controller, GPIO, UART, SPI, I2S).

 3. **[JieLi SoC Forum Thread (esp8266.ru)](https://esp8266.ru/forum/threads/jl-soc.5500/):**
    Community research thread discussing JieLi SoCs, SDKs, toolchains, flash recovery, and hardware boot modes.

### 3.4. Emulators, Simulators & Virtual Instruments

 1. **[fm1-emulator by Simon Johansson](https://github.com/simonjohansson/fm1-emulator):**
    Rust-based desktop emulator for the M-VAVE FM-1. Executes firmware binaries (`.fwsc`, `.elf`, `.bin`) on desktop operating systems, emulating the JieLi dual-core CPU and peripheral state.

 2. **[m-wave-fm1-browser-emulator by shcherbakov7](https://github.com/shcherbakov7/m-wave-fm1-browser-emulator):**
    Rust/WebAssembly in-browser emulation of the AC791N SoC's two `pi32v2` cores and the FM-1's color display.

 3. **[SLOOP FM-1 Simulator by Chance Roth](https://github.com/chancethemaker/sloop-fm1-sim) ([Web Simulator](https://chancethemaker.github.io/sloop-fm1-sim)):**
    Self-contained in-browser interactive simulator of the SLOOP / Felucca firmware for the FM-1, allowing testing controls, sound engines, and workflow directly in the browser without physical hardware.

 4. **[FM-1 Mobile by hb3p8](https://github.com/hb3p8/fm1-mobile-emu) ([Web App & Mobile Emulator](https://hb3p8.github.io/fm1-mobile-emu/)):**
    * **Platform:** Mobile-first progressive web app (PWA) with full offline support (Add to Home Screen on iOS/Android).
    * **Concept:** Seven real FM-1 C firmware engines compiled to WebAssembly running inside an accurate hardware-simulated touch panel matching the physical FM-1 instrument layout.
    * **Switchable Firmwares:** On-the-fly switching between **X0X** 1.0.6 (acid/TR-style drums & 303), **Felucca** 1.6 (multi-engine synth & 64-step sequencer), **SLOOP** 2.6 (live groovebox), **FiMba-1** 0.6.1 (physical modeling kalimba), **Melodee** 1.4.0-rc.1 (CZ-1, FM6, Prophet-5 & microtonal), **AMB-1** 1.1 (generative ambient), and **MAKU** 0.1 (generative intermission soundscapes).
    * **Features & Architecture:**
      * **AudioWorklet Hardware Clock:** Accurate timing loop where rendering audio advances the device's clock, driving firmware audio interrupts and main loops exactly as on physical hardware.
      * **Display & Graphics:** Real-time 240 × 240 display output drawn via WebGL with optional retro xBR smoothing filter.
      * **Responsive Ergonomics:** Adaptive portrait and landscape touch layouts, multi-touch keys with glides, encoder drag controls, button latching ("Hold" mode for SEL combos), and computer keyboard shortcuts.
      * **Persistent Storage:** Browser local storage isolates and preserves patterns, projects, and custom loops separately across each firmware switch.


 5. **[Virtual-FM-1 by jbschooley](https://github.com/jbschooley/Virtual-FM-1):**
    Software replica of the M-VAVE FM-1: standalone FM synthesizer application and VST3/AU audio plugin featuring bidirectional preset and pattern synchronization with hardware over the Baud Girl (FM-1+VA) firmware.

 6. **[FM1VST by Quixotic7](https://github.com/Quixotic7/FM1VST):**
    DAW plugin host (VST3, AU, and standalone) running Felucca-family firmwares (ChoralRoot, Felucca, Melodee) compiled directly from source and switchable on the fly.

 7. **[fm1-emu by Joakim Eriksson](https://github.com/joakimeriksson/fm1-emu) ([Web Emulator](https://joakimeriksson.github.io/fm1-emu/)):**
    Full hardware emulator for the M-VAVE FM-1 running its firmwares completely unchanged both natively and directly in the browser via WebAssembly (emulates JieLi CPU, display, buttons, knobs, and audio output).

 8. **[FM-1 Studio by thingsapart](https://github.com/thingsapart/fm1-studio):**
    * **License:** Open Source (GPL-3.0).
    * **Platform:** Native Android Application (Java / WebAssembly runtime).
    * **Concept:** Multi-firmware companion environment and touch synthesizer for Android smartphones and tablets.
    * **Features:**
      * Hosts real FM-1 C firmware engines (SLOOP, FM1 MOVE, Felucca, sloopDX) compiled to WebAssembly running directly on Android.
      * Full touch panel simulating the FM-1's 240 × 240 color display, keys, and rotary encoders.
      * Integrated touch piano roll, sound editors, preset management, and USB-MIDI integration to synchronize projects with physical FM-1 hardware.

### 3.5. Web Editors, Patch Librarians & Companion Utilities

 1. **[FM-1 Online Editor & Firmware Directory](https://fm1-editor.com/) ([Firmware Catalog](https://fm1-editor.com/firmware/)):**
    Web-based configuration and patch editor / librarian for the M-VAVE FM1 synthesizer, along with a curated directory and status tracker for community firmwares.

 2. **[FM-1 Utility](https://fm1-utility.pages.dev/):**
    Lightweight, dependency-free WebMIDI parameter editor and diagnostic tool for the FM-1.

 3. **[FM-1 Workbench by thegiantsnail](https://github.com/thegiantsnail/fm1-workbench-public) ([Web App](https://fm1-workbench.web.app)):**
    Multi-platform utility suite (Web app, Android app, VST3/CLAP plugin, and Model Context Protocol MCP server) featuring a DX7 preset library, voice randomizer/mutator, drum sequencer, and MIDI file player.

 4. **[fm1-read-voice by Christian Zietz](https://github.com/czietz/fm1-read-voice):**
    Python utility to request and read the currently active sound patch back from the FM-1 hardware over USB-MIDI SysEx.

 5. **[OpenPatch.es (Yamaha DX7 Patch Utility)](https://openpatch.es/):**
    Web utility for DX7 FM patches allowing WAV upload to recover/match patches, live auditioning, sequencing, modifying, mutating, and exporting patch sets as `.syx` files.

 6. **[DXcompanion](https://dxcompanion.uk/):**
    Browser-based patch and parameter editor for the Yamaha DX synth family featuring experimental M-VAVE FM-1 support.

 7. **[Dexed by asb2m10](https://asb2m10.github.io/dexed/):**
    Open-source DX7 plugin and editor. The FM-1 hardware natively responds to Dexed real-time parameter-change SysEx messages for live DAW sound design.

 8. **[FM-1 Pulses by mene311](https://github.com/mene311/fm1-pulses) ([Web App](https://mene311.github.io/fm1-pulses/)):**
    Browser-based generative MIDI sequencer and pattern generator for the M-VAVE FM-1 (Web MIDI API / PWA, runs on desktop/mobile). Generates reproducible 64-step banks with parameter drift and can freeze them directly into the hardware pattern slots over SysEx (supported on Baud Girl / FM-1+VA firmware), or broadcast live MIDI notes in real time.

 9. **[sloop-fm1-go by jahlib](https://github.com/jahlib/sloop-fm1-go) ([Releases / APK](https://github.com/jahlib/sloop-fm1-go/releases)):**
    * **License:** Open Source (GPL-3.0).
    * Android-native touchscreen companion and project editor for SLOOP custom firmware (based on the SLOOP web editor). Allows editing tracks, synth parameters, samples, and sequence patterns directly from an Android smartphone or tablet over USB-MIDI.

10. **[SLOOP 8-Track Web Workstation by smhulme](https://github.com/smhulme/sloop-web-8trk):**
    Hybrid production environment driving SLOOP's four hardware tracks over WebMIDI while adding four synchronized browser audio tracks alongside them.

11. **[Choppa Lite by WaveLoop](https://waveloop.app/toys/choppa):**
    In-browser, installable sampler web application for the FM-1. Allows recording up to 12 seconds of audio, chopping it into 16 pads, and transferring the sample bank directly to the FM-1 over USB-MIDI. Built for Felucca and SLOOP firmware families (also available for iOS, with Android version planned).

12. **[take-taker by groundstation1](https://github.com/groundstation1/take-taker) ([Releases / APK](https://github.com/groundstation1/take-taker/releases)):**
    * **License:** Open Source (MIT).
    * Android multitrack audio & video recorder designed specifically for USB audio devices.
    * When paired with the **Melodee** firmware on FM-1 (which exposes all 4 audio outputs as discrete USB audio streams), it bypasses Android's default stereo downmixing via raw USB mode to record each channel as an independent track.
    * Exports individual lossless FLAC stems, normalized MP3 mixdowns, or synced video takes (using phone camera footage or rendered live scrolling waveform overlays).

13. **[FM-1 Patch Bank Utility (Soundspirate) by klonecom](https://github.com/klonecom/M-VAVE-FM1-LOADER---):**
    * Single-file, client-side browser Web MIDI tool for transmitting `.syx` patch bank files to the FM-1 with auto-detection and SysEx framing validation.

14. **[FM1 Bank Sender by Leo Maimoni](https://github.com/leomaimoni/fm1-bank-sender):**
    * Android utility app to transmit DX7 sound bank files (`.syx`, 32-voice banks or single patches) to the M-VAVE FM-1 via USB-OTG without entering special receive modes.

15. **[Felucca Editor Skill by hunterxiong2026](https://github.com/hunterxiong2026/fm1-felucca-editor-2026):**
    * **License:** Open Source (MIT).
    * Natural language LLM / Agent skill integration for controlling the M-VAVE FM-1 (running Felucca firmware) over MIDI SysEx for tone design, multi-track arranging, and song playback.

16. **[Oscuro Companion Protocol & File Bridge by kartun83](https://github.com/kartun83/oscuro-companion-protocol):**
    * **License:** Open Source (Apache-2.0).
    * **Concept:** High-speed phone ↔ hardware file bridge and companion communication service over USB (smartphone acts as USB host, device runs as USB peripheral).
    * **Architecture & Features:**
      * Native Android USB-Host app (Kotlin) paired with a lightweight RAM firmware payload (`usbfiles.c` + `usbven.c`) executed on the JieLi AC791N SoC.
      * Fast bidirectional file listing, patch browsing, sample transfer, and remote UI state synchronization on 240 × 240 displays without requiring flash wear.
      * Developed for M-VAVE SMK-37 (under the Oscuro project) and architecturally adaptable to the M-VAVE FM-1 given their shared AC791N SoC and USB stack. Includes desktop Python host mock (`pyusb`) and wire protocol documentation.

17. **[Relay FM-1 Editor, Firmware Database & Manager by Stanley Gurvich (EmeraldMoonLabs)](https://github.com/stanleygurvich/fm1-firmware-database) ([Web Feed](https://stanleygurvich.github.io/fm1-firmware-database/) | [Reddit Announcement](https://www.reddit.com/r/MVaveFM1/comments/1x6gg0h/relay_fm1_editor_firmware_database_emulator/)):**
    * **Concept:** Comprehensive FM-1 editor, firmware database, emulator host, and automated release feed service.
    * **Automated Firmware Feed:** Runs a scheduled automated crawler tracking the [FM-1 Resource Hub](https://github.com/aroum/fm1-custom-fw) and upstream GitHub releases every 3 hours. Publishes a unified `feed.json` verifying firmware update packages (`.fwsc` SHA-256, `FELUCCA-LOADER-1` and `FM-1_` package markers, asset sizes, and web installer links) across 60+ projects.
    * **Felucca Web App & Deep Editor:** Includes companion [UplinkFeluccaEditor-WebApp](https://github.com/stanleygurvich/UplinkFeluccaEditor-WebApp) with Web MIDI SysEx parameter control, custom package verification, backup tools, and in-browser mock testing.

### 3.6. Developer Frameworks, UI Designers & Curated Collections


 1. **[MvaveFM1-Designer by Quixotic7](https://github.com/Quixotic7/MvaveFM1-Designer):**
    Visual UI and panel state designer for FM-1 custom developers (mapping key/button LED states, knob functions, and OLED/TFT screen layouts).

 2. **[Schwung by Charles Vestal](https://github.com/charlesvestal/schwung):**
    Open-source music architecture framework for standalone devices. Core synthesis code and models (TR-909, TR-808, TB-303, PSX Verb) are shared with the X0X and Lunar Modulator FM-1 firmwares.

 3. **[awesome-fm-1 by cicloid](https://github.com/cicloid/awesome-fm-1):**
    A curated awesome-list of resources, custom firmwares, tools, and open-source projects for the M-VAVE FM-1 pocket synthesizer.

 4. **[Fluyt by rgrvmusic](https://www.reddit.com/r/LogueSDK/comments/1x3upww/fluyt_felucca_synth_engines_for_drumlogue/):**
    Community port and adaptation of the open-source **Felucca** synthesizer engines from the M-VAVE FM-1 to the **Korg drumlogue** (LogueSDK user synth unit), demonstrating cross-platform portability of Felucca DSP algorithms.

### 3.7. Custom Soundbanks & Preset Collections

Dedicated sound banks, commercial patches, and SysEx preset packs tailored for the M-VAVE FM-1:

 1. **[Ambient & Dreams by NatLife Sounds](https://natlifesounds.com/product/ambient-dreams-for-m-vave-fm-1-fm-synthesizers/):**
    * **Format & Compatibility:** Standard 32-preset SysEx bank (`.syx`) with FM-1 USB installation instructions (cross-compatible with Yamaha DX7/DX7 II, Korg Opsix 2.0, Korg Volca FM/FM2, Dexed, Arturia DX7 V, and NI FM8).
    * **Sound Design:** 32 tailored ambient FM presets designed to showcase soft, harmonic FM textures without harsh digital dissonance — includes 1 AAH vocal preset, 5 bass patches, 2 FX textures, 2 leads, 5 ambient pads, 10 plucks, and 8 melodic synth sounds. Includes video demo walkthroughs and tutorials.

---


## 4. Documentation, Protocols & Guides

Comprehensive technical references and community guides:

1. **[FM-1 SysEx Protocol & Provenance (by KingParamount)](https://github.com/KingParamount/fm1-factory-presets/blob/main/docs/protocol-and-provenance.md):**
   Technical documentation of the FM-1 handshake sequence, 7-bit payload packing, and bulk dump transfers.
2. **[FM-1 OTA Protocol & Architecture Docs (AL-255/FM-1-RE)](https://github.com/AL-255/FM-1-RE/blob/main/docs/io/11-ota-protocol.md):**
   In-depth specifications for the USB-MIDI packet framing, session handshakes, and XIP flash memory layouts.
3. **[FM-1 Easy Guide (by pingywon)](https://pingywon.github.io/fm1-easy-guide/) ([Source](https://github.com/pingywon/fm1-easy-guide)):**
   Beginner-friendly rewrite of the official manual with an interactive step-by-step browser walkthrough.
4. **[fm1-guide (by fuleo)](https://fuleo.github.io/fm1-guide/):**
   Practical operational notes covering sequencer workflows, the V15 reverb bugfix, and Linux flashing procedures.
5. **[FM-1 on Tao of Mac (by Rui Carmo)](https://taoofmac.com/space/com/m-vave/fm-1):**
   Architectural notes, teardown observations, and hackability insights.

---

## 5. Hardware Add-ons & DIY Enhancements

Community hardware companion projects and accessories:

1. **[FM-1 Bonus Box by pfkellogg](https://github.com/pfkellogg/fm1-bonus-box):**
   ESP32-S3 external companion module featuring a rotary preset browser with round color TFT, sustain pedal input, Wi-Fi bank manager, USB-MIDI host, and a sing-on-pitch voice trainer.
2. **[fm1-sustain-footswitch by pfkellogg](https://github.com/pfkellogg/fm1-sustain-footswitch):**
   Arduino-based adapter converting a standard 1/4" sustain pedal into MIDI CC64 over the FM-1's 3.5 mm TRS MIDI input (includes full schematics).
3. **[fm1-midi-voice-tuner by pfkellogg](https://github.com/pfkellogg/fm1-midi-voice-tuner):**
   Passive TRS MIDI splitter box with built-in microphone and OLED pitch display guiding singers on whether they match the FM-1's current note.

---

## 6. Articles, Reviews & Community Analyses

Articles and press coverage detailing community custom firmwares and feature overhauls:

* **[Synth Anatomy: Baud Girl FM-1+VA](https://synthanatomy.com/2026/09/baud-girl-fm-1-va-custom-m-vave-fm-1-firmware.html):** Detailed review of the first community firmware adding Virtual Analog synthesis and 64-step sequencing.
* **[Synth Anatomy: Felucca 1.0 Release](https://synthanatomy.com/2026/10/hugelton-instruments-felucca-custom-m-vave-fm-1-firmware-turns-it-into-a-multi-engine-synth.html):** Coverage of Hügelton Instruments' multi-engine open-source platform.
* **[Synth Anatomy: SLOOP Groovebox](https://synthanatomy.com/2026/10/3dsam-sloop-custom-firmware-turns-m-vave-fm-1-into-a-4-track-groovebox.html):** Feature breakdown of SLOOP 4-track groovebox with USB audio.
* **[Synth Anatomy: X0X Techno Firmware](https://synthanatomy.com/2026/10/charles-vestal-x0x-custom-firmware-turns-the-m-vave-fm-1-into-a-rebirth-like-groovebox.html):** Examination of Charles Vestal's ReBirth-inspired 303/808/909 firmware.
* **[Synth Anatomy: Groove OS](https://synthanatomy.com/2026/10/groove-os-turns-the-m-vave-fm-1-into-an-8-track-groovebox.html):** Coverage of the commercial 8-track groovebox firmware.
* **[Piano & Synth Magazine: Custom Firmware Collection](https://pianoandsynth.com/m-vave-fm-1-custom-firmware-collection/):** Side-by-side comparison matrix of major FM-1 custom firmwares.
* **[Sonicstate: Free Custom Firmware for M-VAVE FM-1](https://sonicstate.com/news/2026/09/29/free-custom-firmware-for-mvave-fm-1-/):** News coverage of third-party firmware development.

---

## 7. Community Hubs & Discussions

Where the M-VAVE FM-1 community discusses reverse engineering, troubleshooting, and new releases:

* **[M-VAVE Official Forum (Topic #4: FM1 Open Firmware Announcement)](https://forum.m-vave.com/topic/4):** The official manufacturer forum and announcement hub (announcement topic #4 was subsequently removed by manufacturer).
* **[Reddit: r/MVaveFM1](https://www.reddit.com/r/MVaveFM1/):** The primary community hub for custom firmware releases, unbricking help, and hardware hacks.
* **[KVR Audio: M-VAVE FM-1 Thread](https://www.kvraudio.com/forum/viewtopic.php?t=632127):** Technical thread where factory preset recovery and early tools were first shared.
* **[Hacker News: FM-1 Reverse-Engineering Discussion](https://news.ycombinator.com/item?id=49994065):** Discussion on the FM-1-RE architecture and JieLi SoC discoveries.
* **[Elektronauts: M-VAVE FM-1 Thread](https://www.elektronauts.com/t/m-vave-fm-1/252170):** Groovebox workflow discussions, firmware releases, and audio demos.
* **[Gearspace: M-VAVE FM-1 Owners Thread](https://gearspace.com/threads/m-vave-fm-1.1465371/):** Hardware impressions, comparison with Yamaha DX-series hardware, and tips.
