# music-sync/

The beat-sync engine that drives AutoClaw’s idle dance animations.

Inputs:

- **MediaSession (Android) / MPNowPlayingInfoCenter (iOS)** — currently-playing track metadata, playback state, elapsed position.
- **Spotify Web API (optional)** — when a Spotify session is detected and the driver has linked their account, fetch \`audio-analysis\` to get a precise beat grid, tempo, and section/bar boundaries.
- **Realtime audio (fallback)** — when no metadata is available, run a lightweight onset/BPM detector on the platform audio loopback (where permitted).

Outputs:

- A monotonic beat clock event stream consumed by character/ to drive animation states.
- A confidence score so the character can fall back to ambient idle when sync confidence is low.

## Safety

Idle dance plays **only** when the vehicle reports a parked or stationary state. While driving, music-sync still tracks beats but the character renderer falls back to glanceable, low-motion poses per Android Auto / CarPlay distraction guidelines.

## Status

Stub. v0.5 milestone tracks the first MediaSession-based beat estimator; v0.6 adds Spotify audio-analysis integration.
