# AFTERHOURS

*The night has its own frequency.*

Afterhours is a fictional late-night broadcast station, brought to life as a small, self-contained website. A glowing television, a handful of frequencies, and music for when the rest of the world has gone to bed.

## Somewhere on the dial, since 1990

The station started in a room above an electronics repair shop. There was a second-hand transmitter, a cassette deck with one unreliable button, and a television nobody ever switched off. The first schedule was written on the back of a repair invoice: start at midnight, finish when it felt right.

It found a small audience. People driving home after a late shift. Students watching the rain instead of their notes. Someone leaving the television on in the kitchen just to make the room feel less empty.

Over time, one frequency became three. The equipment stayed. So did the promise: no announcements shouting you awake, no hurry to get to the next thing. Just somewhere to spend a little of the night.

The screen still says October 24, 1994. Nobody has found a good reason to fix it.

## Three frequencies

| Channel | Station | What comes through |
| --- | --- | --- |
| **03** | **Midnight Drive** | Warm synths, steady drums, and the last stretch of motorway before home. |
| **07** | **Low Tide Radio** | Soft electric-piano tones, slow beats, and letters you never quite sent. |
| **09** | **The Quiet Signal** | Spacious pads, distant bells, and the possibility that someone is listening back. |

Each station has three original instrumental tracks, with its own melodies, arrangements, and pace. Songs move through intros, fuller passages, breakdowns, and endings before the next record comes around.

## Tune in

Open [index.html](index.html) in a modern browser. The station tries to start playing immediately; if autoplay is blocked, a click or keypress gets it going.

Choose a channel, turn the tuning dial, or pick a track from the station rotation. You can skip, rewind, seek through a song, adjust the volume, or fiddle with the tape tracking. Playback continues when you switch tabs, and returning to a station restores its place during the current session.

**Keyboard:** `←` / `→` change channels, `Space` pauses, `M` toggles sound, and `P` switches the television on or off. The footer also has fullscreen and motion controls.

Created by **Vincent Verbist** — [@vincentjanv](https://github.com/vincentjanv).

## For the nerds

- **One file:** HTML, CSS, and plain JavaScript live in `index.html`. No build step, package installation, server, or external media downloads. It works locally and can be served by any static host.
- **The pictures:** CSS gradients, transforms, clipping, and layered elements create the landscapes, CRT glass, scanlines, and moving grid. The layout adapts to smaller screens and respects reduced-motion preferences.
- **The music:** Nine compositions, roughly **3:02–5:20** each, are synthesized in the browser with the Web Audio API. Oscillators supply the tonal instruments; generated noise supplies percussion and surf. A shared convolution reverb, feedback delay, stereo panning, and compression give each station its sound.
- **The arrangements:** `SCORES` defines the three foundation tracks, `PLAYLISTS` adds their sister tracks, and `Soundtrack.arrange()` schedules the instruments. Tempo, chord voicings, melodic phrases, drum accents, and section energy are defined in code. A bar contains four beats, divided into sixteen steps.
- **The clock:** A scheduler wakes every 25 ms and places notes against the audio context's clock. It queues about 120 ms ahead in the foreground and two seconds ahead in a hidden tab to accommodate slower background timers. Browser or operating-system suspension can still interrupt playback.
- **The transport:** Tracks advance automatically with a short fade. Switching stations preserves the selected track and playback position in memory; refreshing starts a new session. Pause and power suspend the audio context, and finished voices are disconnected.

To reshape a transmission, edit its score in `SCORES` or `PLAYLISTS`: change the tempo, chords, melody, or section sequence. The duration follows from the number of bars and the tempo: `bars × 240 / BPM`.
