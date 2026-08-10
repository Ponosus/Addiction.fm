# [Addiction.fm](http://addiction.fm/) 2.0

**[Русская версия страницы](./Readme.ru.md)**

<img width="1918" height="885" alt="image" src="https://github.com/user-attachments/assets/bdf23332-a122-4b1a-aca1-0bf1150165c8" />

**Mobile version:**

<img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/1dbd40fd-f5db-41bf-8215-38d193d0a10d" /><img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/b9c78e26-c095-43c0-8128-979a68d58972" />

**Generative radio. One button - sound built for your mental state.**

Addiction.fm is a browser-based generative audio app with no playlists, no accounts, and no ads. Pick a state - get a unique sound that never repeats.

---

## 🔥 What's new in 2.0

The biggest update since launch: the mobile interface was rebuilt from scratch, the drum bank grew five and a half times, and you can now run the radio without ever opening the tab.

### System-wide media controls

The radio is no longer trapped inside a browser tab. It shows up wherever a normal music player does, with its own artwork:

- **Android** - a card in the notification shade and on the lock screen: play/pause, track skipping, and a dedicated "another break" button.
- **Windows** - the Chrome and Edge media panel (the one behind the address-bar icon, which also feeds the system media controls), plus hardware media keys on keyboards and headsets.
- **iOS/macOS** - lock screen and Control Center.
- With a **sleep timer** armed, the system card draws a real countdown, so you can see what's left without unlocking the phone.

This turned out to be the fiddliest part of the release: the operating system has no idea Web Audio exists, so the card is carried by a separate inaudible `<audio>` element. Chrome and Edge only promote tracks longer than 5 seconds into the system controls, and a track of pure zeroes gets written off as "no audio at all" - so the carrier runs for 30 seconds and holds a square wave one least-significant bit tall: quieter than the noise floor of any signal chain, yet unmistakably real audio to the OS.

### 268 real breaks instead of 49

The drum bank went from 49 to **268 live loops** - real breaks, not synthesis. The large packs live in separate files and are only fetched once DRIVE is playing, so the page still opens instantly.

### Every visit sounds new

Track `#1` used to sound the same forever. Now the **bank is reshuffled on every visit**: the same track number today and tomorrow lands on completely different drums. Within a single session the numbering stays deterministic, so going back to `‹‹ #N ››` still returns the same track.

### The 🎲 "another break" button

Love the harmony, hate the drums? The 🎲 button in the player (or the `X` key, or the extra button in the system card) swaps the break **on the fly**, without restarting the track or breaking the mood.

### Redesigned mobile player

The phone player was rebuilt: a sticky panel at the bottom edge, a CSS-grid layout instead of wrapping rows, thumb-sized tap targets, and dedicated breakpoints for narrow screens. Sliders, timer, and track controls no longer fall apart at 360 pixels wide.

### Small things you can see and hear

- **mp3 codec delay compensation** - decoders leave up to 25 ms of silence at the head of a file, which made the slicing land just barely late. The real start of the loop is now detected from the signal, so hits sit exactly on the grid.
- **The break name** appears in the player caption and on the second line of the system card.
- **Custom icon** - the app artwork doubles as the tab favicon, the home-screen icon, and the system player cover.
- **Bank counter** in the About dialog shows how many breaks are loaded.
- **FOCUS was rewritten** around pure synthesis - the `genres.js` file from 1.1 is gone.

---

## Why this exists

Most music services require you to choose. Choosing is a distraction.
Addiction.fm removes the choice entirely: one button, one state, one stream of sound. Runs in the browser, no install required, no login needed.

---

## States

| State | Genre | For |
|-------|-------|-----|
| 🔴 **DRIVE** | Amen-break · Jungle · ~180 BPM | Energy, task focus, movement |
| 🔵 **FOCUS** | Deep ambient | Sub-bass and dark pads only - no drums |
| 🟢 **CALM** | Slow drone + rain | Relaxation, sleep, recovery |

---

## How it works

Sound is **generated in real time** via the Web Audio API - this is not streaming, not a playlist. Every press creates a unique combination:

- **DRIVE** - a break from a 268-loop bank sliced into 16th notes with DJ jumps, stutters and rolls, soft piano on top
- **FOCUS** - sub-bass synthesized in the chosen key, dark pads through a delay chain
- **CALM** - drone from detuned oscillators, filtered noise, slow bells

---

## Why Addiction.fm

- **Runs everywhere** - Chrome, Firefox, Safari, Android, iOS, Windows. Open and play.
- **Controlled from the OS** - Android shade, Windows media controls, lock screen, media keys
- **Works offline** - download the files and run locally from any folder
- **No accounts** - no tracking, no ads, no recommendation algorithms
- **Always different** - the generative engine creates a new version on every press
- **268 breaks** - the bank is reshuffled on every visit
- **Deterministic tracks** - the `‹‹ #N ››` counter locks a specific track by seed number within a session
- **WAV recording** - the ⏺ rec button captures the track in real time and downloads it as `.wav`
- **Propeller** - spins during playback, gradually coasts to a stop on pause

---

## Files

| File | What's inside | Required |
|------|---------------|----------|
| `addiction-fm.html` | the whole app: engine, interface, artwork | yes |
| `breaks.js` | base bank, 49 breaks | yes |
| `breaks2.js` | main pack, 219 breaks | optional, but far more fun |
| `breaks3.js` | pack top-up | optional |

Without `breaks2.js` and `breaks3.js` the radio runs on the base bank; without `breaks.js` it falls back to synthesized drums.

---

## Shortcuts

| Key | Action |
|-----|--------|
| `Space` | pause |
| `1` `2` `3` | state |
| `V` / `B` | previous / next track |
| `X` | another break |

---

Requirements: **modern browser** (Chrome 90+, Firefox 88+, Safari 15+). Nothing else.

---

## Tech stack

- **Web Audio API** - synthesis, slicing, mixing, real-time recording
- **Media Session API** - system media controls, artwork, sleep-timer countdown
- **OfflineAudioContext** - full track and stem rendering without artifacts
- **ScriptProcessorNode** - PCM capture for WAV export
- **Pure HTML/JS** - zero dependencies, zero frameworks, single file

---

## Author

Made by **Sewerbox** / [sewerdev](https://github.com/sewerdev)
Telegram: [@VestronVulture](https://t.me/VestronVulture)

---

*Addiction.fm is not a playlist. It's a state of mind.*
