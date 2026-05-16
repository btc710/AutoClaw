# agents/nemoclaw/

NemoClaw adapter for the AutoClaw agent router.

NemoClaw plugs into AutoClaw as either a peer to OpenClaw or as a specialized sub-agent (e.g., for short-horizon reactive behavior while OpenClaw handles planning).

Responsibilities:

- Mapping router calls to NemoClaw’s runtime entry points.
- Exposing NemoClaw’s tool/skill catalog so the router can plan multi-agent flows.
- Reporting latency hints so the router can prefer NemoClaw for fast turns and defer heavier work to other backends.

## Status

Stub. v0.4 milestone tracks the initial integration alongside the OpenHuman adapter.
