# Security Policy

## Reporting a vulnerability

If you believe you have found a security vulnerability in AutoClaw, **please do not open a public issue**. Instead:

1. Open a [private security advisory](../../security/advisories/new) on this repository, **or**
2. Email the maintainers (a dedicated address will be added once a maintainer team is established; in the interim, use a private security advisory).

We aim to acknowledge reports within **72 hours** and to provide an initial assessment within **7 days**. Coordinated disclosure timelines are negotiable depending on severity.

## What is in scope

- The AutoClaw head-unit apps (Android Auto, CarPlay) and the on-phone agent router.
- The music-sync, character, wheel-controls, and agent adapter modules.
- The build, CI, and release pipeline for the above.

## What is explicitly out of scope

- Vulnerabilities in upstream agent runtimes (OpenClaw, NemoClaw, OpenHuman). Please report those to their respective maintainers.
- Bugs in Android Auto, Apple CarPlay, Spotify, or any other third-party platform AutoClaw integrates with.

## Privacy and platform posture

AutoClaw is designed around three commitments. Treat any deviation from these as a security issue:

1. **No telemetry by default.** Anything that phones home must be opt-in, clearly documented, and disable-able from a single setting.
2. **Vehicle signals are read-only.** AutoClaw never writes to CAN, OBD-II, or any other vehicle bus. We will not accept code that does.
3. **Driver-distraction guidelines are non-negotiable.** Any UI behavior that violates Android Auto or CarPlay distraction rules — even unintentionally — is treated as a security-class bug and tagged with the \`safety\` label.

## Supported versions

While AutoClaw is pre-1.0, only the \`main\` branch receives security fixes. After 1.0, the most recent minor release will receive security updates for at least six months.
