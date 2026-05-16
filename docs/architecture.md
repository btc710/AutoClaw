# AutoClaw architecture

This document expands on the diagram in the root README and defines the three contracts every contributor should know: the **agent-router contract**, the **beat-clock event shape**, and the **safety state machine**. Code lands later; this is the design surface.

## 1. Component split

```
            ┌───────────────────────────────────────┐
            │           Head Unit  (AA / CarPlay)             │
            │  ┌─────────────┐   ┌──────────────────┐    │
            │  │ Character  │←── Beat clock        │    │
            │  │ Renderer   │   │ (music-sync/)     │    │
            │  └──┬────────┘   └──────────────────┘    │
            └────┼────────────────────────────────────┘
                 │
                 ▼
            ┌───────────────────────────────────────┐
            │     Agent Router  (on-phone service)          │
            │ OpenClaw │ NemoClaw │ OpenHuman │ ...      │
            └────────────────────────────────────────┘
                 │
     ┌───────────┼────────────────┐
     ▼                              ▼
Steering Wheel HID         Vehicle signals (CAN/OBD-II, opt-in, read-only)
```

Three processes, three contracts:

1. **Head Unit app** runs inside Android Auto or CarPlay. Owns the character renderer, the steering-wheel hooks, and the safety state machine. Talks to the phone service over a stable IPC boundary.
2. **Agent router (on-phone service)** routes turns to one or more agent adapters and streams results back. The router does *not* know anything about the head unit beyond the contract below.
3. **Music-sync** is a per-platform module that publishes a beat-clock event stream the renderer subscribes to.

## 2. Agent-router contract

The router exposes one core operation:

```
startTurn(input: TurnInput) -> Stream<TurnEvent>
cancelTurn(turnId)
```

### TurnInput

- \`turnId\` (uuid): assigned by the head unit at start.
- \`text\` (string, optional): a transcribed user utterance.
- \`audioRef\` (handle, optional): pointer to streaming audio for STT-on-the-router setups.
- \`personaId\` (string): currently-active persona, fed to the OpenHuman adapter.
- \`vehicleState\` (enum): parked / moving / unknown. Affects what the router lets agents do.

### TurnEvent (streamed)

- \`partial-transcript\`: STT partials, if applicable.
- \`partial-reply\`: incremental text the renderer can synthesize.
- \`character-action\`: a motion-state hint (\`thinking\`, \`speaking\`, \`celebrate\`).
- \`tool-call\` / \`tool-result\`: opaque to the head unit; surfaced for logging.
- \`final\`: turn ended cleanly.
- \`error\`: turn failed; includes a user-safe message.

### Capability discovery

At startup each adapter answers \`describe()\` returning a capability struct (supported modalities, tools, latency hints). The router uses this to decide which adapter handles which turn type and whether to compose multiple adapters.

## 3. Beat-clock event shape

```
BeatEvent {
  type: "beat" | "bar" | "section" | "tempo"
  // monotonic ms timestamp relative to the music-sync session start
  t: int
  // 0.0 - 1.0 confidence the event is real
  confidence: float
  // for "tempo" events only
  bpm?: float
  // optional source tag for debugging
  source: "mediasession" | "spotify" | "onset-detector"
}
```

The renderer subscribes and decides what to do with each event. Low-confidence streams are still useful for ambient idle.

## 4. Safety state machine

Three states, transitions driven by vehicle telemetry from the head unit:

- **parked** — full character animation including dance-sync, glanceable text allowed.
- **moving** — character renders glanceable, low-motion poses only. No free-text UI. Voice-first.
- **unknown** — treat as moving. Safe default.

Every module that draws or accepts input must read this state and degrade accordingly. Bugs that bypass this state are tagged with the \`safety\` label and treated as release blockers.

## 5. What is explicitly out of scope

- Anything that writes to vehicle systems. AutoClaw is read-only on CAN/OBD-II.
- Driver-identification via biometrics.
- Network telemetry by default. Opt-in only, off-by-default.

