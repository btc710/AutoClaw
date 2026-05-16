# android-auto/

Android Auto integration layer for AutoClaw.

This module hosts a Car App Library project that exposes AutoClaw’s copilot as an Android Auto-compatible app. It is responsible for:

- Declaring AutoClaw’s templates (NavigationTemplate, GridTemplate, MessageTemplate, etc.) within Android Auto’s distraction-optimized constraints.
- Bridging steering-wheel voice-action intents (the standard ACTION_VOICE_COMMAND) to the agent router.
- Hosting the character renderer surface inside an allowed template (likely a custom Pane or full-screen idle animation when the vehicle is parked).
- Forwarding MediaSession callbacks to music-sync/ for beat-driven idle dance.

## Status

Not yet implemented — see the v0.1 milestone for the first Android Auto “hello copilot” template.

## References

- Android for Cars App Library: https://developer.android.com/training/cars/apps
- Driver distraction guidelines: https://developer.android.com/training/cars/apps#distraction
