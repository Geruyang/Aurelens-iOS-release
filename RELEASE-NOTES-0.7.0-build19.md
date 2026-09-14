# Aurelens 0.7.0 (build 19) — Trial and annual subscription

Aurelens now includes a 3-day free trial and an annual subscription.

• Start your free trial when you first open the app. No automatic charge when the trial ends.
• Subscribe for one year of access to gold market insights, forecasts, global events and all 10 chart timeframes.
• View your trial and subscription status, restore purchases, and manage your subscription in the app.

Annual subscriptions renew automatically unless cancelled. AI provider API charges are separate.


## Delivery status

- Uploaded successfully to App Store Connect on 2026-09-14 at 10:29:37 UTC. Apple reported processing at upload completion; later processing completion is not verified. App Review has not been submitted.
- The annual product specification targets USD 3/year in the U.S. Live App Store Connect product configuration and pricing are not verified and remain required before review/distribution.
- The public IPA is signed for App Store upload and cannot be directly installed on an iPhone. Registered-device development packages remain local.
- App name, icon and existing market-analysis features are unchanged from build 18. The functional changes in build 19 concern trial and subscription access.

## Verification

The initial simulator/macOS matrix passed 205 tests. Subsequent iPhone 17 Pro Max testing passed 65 of 66 core tests and all 8 UI scenarios; an additional iPad StoreKit regression passed all 8 tests. Actual cancellation of the Xcode simulated purchase sheet passed. One iOS 27 injected-cancellation test returned a generic failure instead of cancellation; it did not grant paid access. This known compatibility difference remains unresolved. No real subscription charge was made.

See [verification report](VERIFICATION-0.7.0-build19.md) and [installation guidance](INSTALLATION.md).

## Source and integrity

Source: [Geruyang/Aurelens-iOS at 9600433](https://github.com/Geruyang/Aurelens-iOS/commit/96004333ff0d40ad77a96ebc377f9e7fde35d9c0) (private).
Branch: `codex/v0.7.0-subscriptions`; tag: `v0.7.0-build19`.
Application implementation: `d518b1d`; subsequent commits update tests, tooling and release documentation.

App Store IPA SHA-256: `8cac8f808106a552552d7f838ff6212997504e406e82ac285dec58dd5d68d750`.
