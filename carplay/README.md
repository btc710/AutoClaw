# carplay/

Apple CarPlay integration layer for AutoClaw.

This module hosts an iOS app extension that exposes AutoClaw’s copilot through CarPlay’s scene-based templates. Responsibilities:

- Implementing a CPTemplateApplicationScene with CPListTemplate, CPGridTemplate, CPInformationTemplate, and CPNowPlayingTemplate-compatible surfaces.
- Wiring a SiriKit Intents extension so the steering-wheel voice button (Siri trigger) can route to AutoClaw’s agent router.
- Driving the character renderer through CPNowPlayingTemplate or a custom template when CarPlay surfaces allow.
- Subscribing to MPNowPlayingInfoCenter / AVAudioSession to feed beats into music-sync/.

## Status

Not yet implemented — see the v0.2 milestone for CarPlay parity with the v0.1 Android Auto template.

## References

- Apple CarPlay App Programming Guide: https://developer.apple.com/carplay/
- CarPlay Human Interface Guidelines: https://developer.apple.com/design/human-interface-guidelines/carplay
