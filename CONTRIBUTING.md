# Contributing to AutoClaw

Thanks for stopping by. AutoClaw is an early-alpha, community-driven effort to put open agent frameworks into the dashboard, and there is plenty of room to help.

## Ground rules

1. **Driver safety first.** Any UI or interaction proposal must be compatible with Android Auto and CarPlay distraction guidelines. Glanceable, voice-first, no free-text while moving.
2. **Open source forever.** We will not accept code that requires a proprietary SDK or paid service to even build. Optional cloud features are fine if they degrade gracefully.
3. **No telemetry by default.** Anything that phones home must be opt-in, clearly documented, and disable-able from a single setting.
4. **Be kind.** See CODE_OF_CONDUCT.md.

## Where to start

- Browse open issues with the **good first issue** label.
- The v0.1 milestone tracks the earliest pieces of work; pick one of those if you want to ship something visible quickly.
- If you have a bigger idea, open a discussion or a draft PR first so we can shape it together.

## Development workflow

1. Fork the repository and create a feature branch.
2. Keep PRs scoped — one logical change per PR is much easier to review.
3. Add or update tests where applicable. For Android Auto / CarPlay work, link a short screen recording or screenshot of the Desktop Head Unit / CarPlay Simulator in the PR description.
4. Run any linters the module ships with before pushing.
5. Open a PR against \`main\`. The PR template will guide you through the rest.

## Module conventions

- Each top-level directory has its own README explaining its scope.
- Agent adapters live under \`agents/<name>/\` and must implement the adapter contract documented in \`docs/agents.md\` (landing with v0.3).
- Platform code is split: \`android-auto/\` for the AA app, \`carplay/\` for the iOS app, and shared logic lives in the cross-platform modules.

## Commit messages

Conventional Commits are appreciated but not required. Anything that is clear and scannable works:

- \`feat(android-auto): add hello-copilot template\`
- \`fix(music-sync): handle MediaSession null callback\`
- \`docs: clarify steering-wheel long-press behavior\`

## Licensing

AutoClaw is MIT licensed. By submitting a contribution you agree that your contribution is licensed under the same terms.
