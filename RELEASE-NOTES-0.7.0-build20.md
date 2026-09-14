# Aurelens 0.7.0 (build 20) — Monthly subscription

Aurelens now offers a monthly subscription for USD 1 per month in the U.S., with automatic monthly renewal. Your local App Store displays the actual price.

• Enjoy 3 days free from your first launch. No automatic charge when the trial ends.
• Choose a monthly subscription to continue using gold market insights, probability forecasts, global events and all 10 chart timeframes.
• Restore purchases and manage or cancel your subscription in the app.

Payment starts only after you confirm your purchase. Subscriptions renew automatically unless cancelled. AI provider API charges are separate.


## Delivery and verification

- Uploaded successfully to App Store Connect on 2026-09-14 at 16:56:13 UTC. Apple reported processing at upload completion; later processing completion is not verified. App Review has not been submitted.
- Monthly product: `com.geruyang.autogolden.fullaccess.monthly`. Live product configuration, USD 1.00 U.S. pricing and sandbox-server transactions remain to be completed/verified. Local StoreKit pricing is not evidence of a live product.
- 203 core tests passed across iPhone/iPad simulators and macOS, plus 8 UI scenarios passed across final reruns. Two StoreKit purchase UI tests were skipped because Xcode runner overrides were unavailable. Earlier failures, interrupted runs and simulator launch errors are documented in [the verification report](VERIFICATION-0.7.0-build20.md). No physical-device test or real charge was performed for this build.
- Verified unexpired annual entitlements retain their original expiry. The app offers only the new monthly SKU; existing trial records are retained across updates.
- The public IPA is for App Store upload, not direct iPhone installation. Registered-device development packages and the installer remain local.

Source: [Geruyang/Aurelens-iOS at 4ddbcdb](https://github.com/Geruyang/Aurelens-iOS/commit/4ddbcdbbb3f5a686f647418d65214f69f3cfa168) (private). Application implementation: `dbcfa94`; subsequent changes cover testing and documentation.

Branch: `codex/v0.7.0-build20-monthly`; tag: `v0.7.0-build20`.
App Store IPA SHA-256: `da8e30d2b25614e2bb6798b18ab9d6682647a5b0927a595aa9e9846d4229cb93`.

Historical builds, files and release tags are retained.
