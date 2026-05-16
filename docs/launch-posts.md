# Launch post drafts

> These are **drafts for the project maintainer to review and post manually**. AutoClaw automation never posts to social platforms.
>
> Three variants below, sized for different audiences. Tweak names/handles before posting.

---

## 1. Mastodon / Bluesky (short, friendly)

> Building **AutoClaw** — an open-source (MIT) in-car AI copilot that brings agent frameworks like OpenClaw, NemoClaw, and OpenHuman (from Tinyhumans.ai) into the dashboard via Android Auto and Apple CarPlay.
>
> The vibe: a little copilot that holds conversations through the steering-wheel voice button and dances to whatever’s playing on Spotify when the car is parked.
>
> Scaffolding, roadmap, and starter issues are up. Code lands soon. Contributors and testers very welcome.
>
> https://github.com/btc710/AutoClaw
>
> #opensource #androidauto #carplay #ai

*Character count check: keep an eye on platform limits when posting.*

---

## 2. X / Twitter (punchier)

> Just opened **AutoClaw** — open-source in-car AI copilot for Android Auto + Apple CarPlay. 
>
> 👋 OpenClaw, NemoClaw, OpenHuman agents
> 🎧 Idle dance-sync to Spotify
> 🔊 Steering-wheel push-to-talk
> 🛡️ Read-only on vehicle signals
> 📄 MIT, no telemetry
>
> Scaffold + roadmap up, code lands soon. Help wanted!
>
> https://github.com/btc710/AutoClaw

---

## 3. Hacker News “Show HN”

**Title:** Show HN: AutoClaw – open-source in-car AI copilot for Android Auto and CarPlay

**URL:** https://github.com/btc710/AutoClaw

**First comment (post immediately after submitting):**

> Hi HN — author here.
>
> AutoClaw is an early-alpha, MIT-licensed project that brings open agent frameworks (OpenClaw, NemoClaw, OpenHuman from Tinyhumans.ai) into the car via Android Auto and Apple CarPlay. The pitch is a little copilot that:
>
> - Holds conversations through the steering-wheel voice button (short-press to engage, second press to end).
> - Dances to whatever’s playing on Spotify or any MediaSession-aware app when the vehicle reports a parked state.
> - Has a pluggable persona layer (OpenHuman) so different drivers get a different copilot.
>
> What’s in the repo today is scaffolding and design, not a runnable app yet. The README has the architecture, the v0.1 → v1.0 roadmap is in Milestones, and there are good-first-issue tickets for an AA hello-copilot template, a CarPlay scene, a MediaSession beat estimator, and an OpenClaw adapter.
>
> Three commitments worth calling out:
>
> 1. No telemetry by default.
> 2. Read-only on vehicle signals — AutoClaw will never write to CAN/OBD-II.
> 3. Driver-distraction guidelines from AA and CarPlay are treated as hard constraints, not suggestions.
>
> Happy to chat about anything — architecture, the agent adapter contract, the safety state machine, the steering-wheel hooks, or the broader “AI in the car” design space.

---

## Before you post

- Replace any handles/links if you maintain different repo names or accounts.
- Double-check the repo is set to Public (it is, today).
- Pin the repo on your GitHub profile so the launch post drives traffic to a discoverable home.
- Be ready to answer questions about safety, telemetry, and the unaffiliated relationship with Tinyhumans.ai — the README and SECURITY.md both cover this.
