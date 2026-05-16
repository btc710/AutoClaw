# character/

The visual layer of the copilot — the “little AI riding shotgun”.

This module owns:

- A platform-agnostic rig spec (2D sprite or simple 3D mesh) and a state machine for: idle-listen, thinking, speaking, celebrating, sleeping, and dance-sync.
- Renderer back-ends for Android (Compose / Canvas / SurfaceView) and iOS (SwiftUI / Metal) that can be embedded inside Android Auto and CarPlay-allowed surfaces.
- A blendshape/parameter API consumed by the OpenHuman adapter so persona changes (mood, energy, tone) propagate to motion.
- Beat-clock consumption from music-sync/ to drive dance animation when the vehicle is parked.

## Constraints

- Must run within Android Auto / CarPlay drawing budgets and never push interactive widgets while moving.
- Animation FPS should adapt to thermal state; the character is a feature, not a heater.

## Status

Stub. v0.1 ships a static “hello” sprite; richer rig work follows the agent and music-sync modules.
