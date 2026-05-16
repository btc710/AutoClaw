# Outreach to Tinyhumans.ai (draft)

> This file is a **template message** for the AutoClaw maintainer to send manually to Tinyhumans.ai. It is intentionally **not** sent by any automation in this repository.

## Goal

Give the Tinyhumans.ai team a friendly heads-up that AutoClaw exists and is building an OpenHuman adapter, and open the door to whatever level of collaboration they want — from “cool, good luck” to active partnership.

## Suggested channels

- Their public contact form / email on https://tinyhumans.ai (use whichever they list as preferred).
- A polite mention/DM on whatever social account they list on their site, if email is not surfaced.
- Avoid posting in unrelated GitHub issues on their projects — only open an issue in their repo if they invite that.

## Template message

> Subject: Heads-up — OpenHuman adapter in AutoClaw (open-source in-car AI copilot)
>
> Hi Tinyhumans.ai team,
>
> I’m building **AutoClaw**, an open-source (MIT) project that brings agent frameworks like OpenClaw, NemoClaw, and your OpenHuman into the dashboard via Android Auto and Apple CarPlay. The idea is a little AI copilot that holds conversations through the steering-wheel voice button and dances to whatever’s playing on Spotify when the car is parked.
>
> OpenHuman feels like a natural fit for the *persona and embodiment* side of the copilot, so the repo already has an \`agents/openhuman/\` directory scaffolded as a thin adapter to your runtime. The README and that directory both clearly state that AutoClaw is an independent integration effort and is not affiliated with or endorsed by Tinyhumans.ai.
>
> Two things I wanted to ask:
>
> 1. Is there anything you would prefer we change in how OpenHuman is named, described, or integrated?
> 2. Would you like a closer collaboration — review the adapter, share examples, exchange feedback — or are you happy to stay arm’s-length for now? Either is genuinely fine.
>
> The repo lives at https://github.com/btc710/AutoClaw if you want to take a look. Thanks for building OpenHuman, and for taking a minute to read this.
>
> — (your name)

## After sending

- Note the date sent in this file (or in an issue) so future maintainers know the conversation is in flight.
- If they request name/description changes, open a PR updating the root README, \`agents/openhuman/README.md\`, and any other affected docs.
- If they decline integration or ask us to back off, retire the adapter and update the README accordingly.
