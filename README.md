# AutoClaw

> Open-source in-car AI copilot bringing **OpenClaw**, **NemoClaw**, and **OpenHuman** (from [Tinyhumans.ai](https://tinyhumans.ai)) agents to **Android Auto** and **Apple CarPlay**.

AutoClaw turns your dashboard into a living AI companion: a little copilot that rides shotgun, holds conversations through the steering wheel, and dances to your music when there's nothing else to do.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/status-early--alpha-orange)
![Platforms](https://img.shields.io/badge/platforms-Android%20Auto%20%7C%20CarPlay-blue)

---

## Vision

The car is the last untapped frontier for embodied AI agents. AutoClaw is a community-built bridge between the new wave of open agent frameworks and the two operating systems that already live in every modern dashboard. Instead of yet another voice assistant that only fires alarms and reads texts, AutoClaw treats the head unit as a stage — an evolving little character that listens, reasons, reacts to the world outside the windshield, and grooves along with whatever's on the speakers.

## Core Features

- **Multi-agent runtime** — swap between OpenClaw, NemoClaw, and OpenHuman backends, or run them cooperatively (planner / persona / motion).
- **Android Auto + Apple CarPlay templates** — first-class support for both platforms using their official template APIs (no rooting, no jailbreaking).
- **Steering-wheel conversation control** — press-to-talk and press-to-end via the standard voice-command button; long-press hooks for handing off to a deeper agent task.
- **Idle dance-sync** — when the car is parked or cruising and the copilot has nothing to say, it animates in time with Spotify, Apple Music, YouTube Music, or any MediaSession-aware app (BPM + beat-grid via the platform audio APIs).
- **Persona evolution** — the copilot remembers preferences, driving routines, and inside jokes locally; long-term memory is opt-in and never leaves the device by default.
- **Fully open source** — MIT licensed, no telemetry, no required cloud account.

## Architecture (proposed)

```
             ┌────────────────────────────────────────┐
             │        Head Unit (AA / CarPlay)        │
             │  ┌────────────┐   ┌──────────────────┐ │
             │  │ Character  │◄──│  Music Beat Bus  │ │
             │  │ Renderer   │   │ (Spotify/MediaS) │ │
             │  └─────┬──────┘   └──────────────────┘ │
             └────────┼───────────────────────────────┘
                      │
                      ▼
             ┌────────────────────────────────────────┐
             │     Agent Router (on-phone service)    │
             │  OpenClaw │ NemoClaw │ OpenHuman │ ... │
             └────────┬───────────────────────────────┘
                      │
       ┌──────────────┼──────────────┐
       ▼                             ▼
 Steering Wheel HID         Vehicle Signals (CAN/OBD-II opt.)
```

## Repository Layout

```
AutoClaw/
├── android-auto/        # Android Auto Car App Library templates
├── carplay/             # iOS CarPlay scene + templates
├── agents/
│   ├── openclaw/        # OpenClaw adapter
│   ├── nemoclaw/        # NemoClaw adapter
│   └── openhuman/       # OpenHuman (Tinyhumans.ai) adapter
├── music-sync/          # Beat detection, MediaSession + Spotify Web API bridge
├── character/           # 2D/3D rig, idle/dance animation states
├── wheel-controls/      # Steering wheel HID + voice button handlers
├── docs/                # Architecture, contribution, hardware notes
└── examples/            # Reference apps and demo personas
```

## Roadmap

- [ ] v0.1 — Android Auto "hello copilot" template app with steering-wheel push-to-talk
- [ ] v0.2 — CarPlay parity (Siri remote intent + CPTemplate UI)
- [ ] v0.3 — Agent router with OpenClaw adapter
- [ ] v0.4 — NemoClaw + OpenHuman adapters
- [ ] v0.5 — Music-sync idle dance (MediaSession beat estimator)
- [ ] v0.6 — Spotify Web API beat-grid integration
- [ ] v0.7 — Persona memory + local vector store
- [ ] v1.0 — Stable public release, Play Store / TestFlight builds

## Getting Involved

AutoClaw is in early-alpha scaffolding. If you build agents, ship Android Auto / CarPlay apps, animate characters, or hack on car HID, open an issue or a draft PR. A `CONTRIBUTING.md` and code of conduct will land alongside the first runnable build.

## Safety

Driving comes first. AutoClaw's UI will follow the **driver-distraction guidelines** of both Android Auto and CarPlay: no free-text input while moving, glanceable UI, voice-first interaction, and the dance animations only play when the vehicle reports a parked/idle state.

## License

[MIT](LICENSE) © AutoClaw contributors.

*OpenClaw, NemoClaw, OpenHuman, Tinyhumans.ai, Android Auto, Apple CarPlay, and Spotify are trademarks of their respective owners. This project is an independent, community-driven integration effort and is not affiliated with or endorsed by any of them.*
