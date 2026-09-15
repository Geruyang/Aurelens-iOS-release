# Aurelens 0.7.0 (build 21) — Subscription access fix

This update improves monthly subscription access and reliability.

• Fixed an issue where a verified monthly purchase could leave the app in trial mode.
• Improved access after reopening the app and restoring purchases, with correct handling of expiration and refunds.
• Monthly access is USD 1 per month in the U.S. and renews automatically unless cancelled. Your local App Store displays the actual price.
• Your 3-day first-launch trial remains free and does not charge you automatically when it ends. Choose a subscription manually to continue.

Gold market insights, probability forecasts, global events and all 10 chart timeframes remain available with access. AI provider API charges are separate.

## Delivery and verification

- Fixed the build 20 physical simulated-purchase unlock failure. Production implementation: `42c5642cb7b563982bb50180bccfeb77d35d150e`.
- 285 core tests passed across physical iPhone, iPhone simulator, iPad simulator and macOS. Final functional/capture checks total 304 passes; fixture and restoration checks add 7. Earlier failures and the subsequently covered simulator purchase skip remain documented.
- 50 native screenshots and 9 edited silent videos are included. No real charge or paid AI request was made. Original phone settings, holdings and chat records were restored byte-for-byte.
- App Store Connect upload succeeded at **2026-09-15 00:46:33 UTC**; Apple reported processing. Later processing completion is unverified; App Review was not submitted.
- **Live monthly-product configuration, actual USD 1 U.S. pricing and Apple sandbox-server purchases remain unverified.** This is a developer prerelease, not an announcement of public App Store availability.
- Public IPA: App Store upload artifact only. The development-signed IPA, device installer and private records stay local.

[Verification](VERIFICATION-0.7.0-build21.md) · [Device report](DEVICE-VERIFICATION-0.7.0-build21.md) · [Upload receipt](APPSTORE-UPLOAD-0.7.0-build21.md) · [Screenshots and recordings](AppStore-Media/0.7.0-build21/Device-Verification-20260914/)

Source: [Geruyang/Aurelens-iOS at 47a7b05](https://github.com/Geruyang/Aurelens-iOS/commit/47a7b050fe6742d6c45d806c4edab44971faaed1) (private). Version branch: `codex/v0.7.0-build21-subscription-fix`. Existing release files and historical version tags are unchanged.

App Store IPA SHA-256: `e631cf67f1a95f3410e035bc7ffbe8e109b1a4bfb363ccfbb22e8fcec0940e03`.

Final release tag: `v0.7.0-build21-release`. The earlier `v0.7.0-build21` checkpoint is retained. This finalization removes two Git-internal paths from the public checksum list; application binaries and media are unchanged.
