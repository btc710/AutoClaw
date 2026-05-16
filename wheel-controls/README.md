# wheel-controls/

Steering-wheel control bindings for AutoClaw.

On Android Auto and CarPlay, the steering-wheel **voice command button** is the canonical and only sanctioned hook for invoking a voice assistant. AutoClaw rides on top of that signal:

- **Short press** — engage the copilot (start a conversation turn).
- **Press during reply** — barge-in / cancel current utterance.
- **Long press** (when the platform exposes it) — hand off to a deeper agent task (e.g., “plan my evening”) instead of a quick reply.
- **Double press** (where supported) — switch persona/voice profile.

## Platform notes

- **Android Auto:** receive ACTION_VOICE_COMMAND, optionally consult \`CarHardwareManager\` (where permitted) for parked-state and speed signals.
- **CarPlay:** register a SiriKit intents extension; long-press behavior depends on the head unit firmware and may be advisory only.
- **Custom CAN/OBD-II hardware (opt-in):** for tinkerers, a side channel for extra buttons or rotary dials. Strictly optional and never required.

## Status

Stub. v0.1 wires short-press push-to-talk on Android Auto; CarPlay parity follows in v0.2.
