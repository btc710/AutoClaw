# agents/openclaw/

OpenClaw adapter for the AutoClaw agent router.

OpenClaw is treated here as a pluggable agent backend. This adapter is responsible for:

- Translating AutoClaw’s router calls (turn input, tool-use requests, cancellations) into OpenClaw’s API surface.
- Streaming partial responses back to the head unit so the character can react incrementally.
- Reporting OpenClaw capabilities (tool list, supported modalities) to the router at startup.

## Status

Stub. The v0.3 milestone tracks the first working adapter and a smoke-test against a mocked OpenClaw runtime.

## Notes

OpenClaw, NemoClaw, and OpenHuman are referenced as community-maintained agent frameworks. AutoClaw does not vendor their source — each adapter expects the upstream runtime to be installed separately, with a thin shim living here.
