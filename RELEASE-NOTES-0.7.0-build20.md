# Aurelens 0.7.0 (build 20) — Monthly subscription

Aurelens now offers a monthly subscription for USD 1 per month in the U.S., with automatic monthly renewal. Your local App Store displays the actual price.

• Enjoy 3 days free from your first launch. No automatic charge when the trial ends.
• Choose a monthly subscription to continue using gold market insights, probability forecasts, global events and all 10 chart timeframes.
• Restore purchases and manage or cancel your subscription in the app.

Payment starts only after you confirm your purchase. Subscriptions renew automatically unless cancelled. AI provider API charges are separate.


## Delivery and verification

**Not ready for App Review: physical simulated purchase does not unlock paid access.** See [the physical-device report](DEVICE-VERIFICATION-0.7.0-build20.md) and [capture material](AppStore-Media/0.7.0-build20/Device-Verification-20260914/).

- Final iPhone core: 62 passed, 6 failed. Monthly purchase UI failed; actual cancellation UI passed without a purchased transaction. Real trial and original app records were preserved.
- Reference capture and five functional scenarios passed on iPhone; iPad reference capture and the final serial StoreKit run (9 tests) passed. Earlier interrupted and failed attempts are documented.
- 32 reference PNGs, 14 supplemental PNGs and 9 edited, silent native-resolution videos are included. Test pricing is local StoreKit data, not proof of live App Store Connect configuration. No real charge or paid AI request was made.
- The same binary was uploaded successfully on 2026-09-14 at 16:56:13 UTC. Apple reported processing at upload completion. Later processing completion is unverified; App Review has not been submitted. No duplicate binary upload was made during this test follow-up.
- Live monthly-product configuration, USD 1.00 U.S. pricing and Apple sandbox-server transactions remain unverified. Resolve and retest the physical unlock failure before review.
- Public IPA: App Store upload artifact only. Development-signed IPA, installer and private diagnostic data remain local.

Source: [Geruyang/Aurelens-iOS at 9ee5011](https://github.com/Geruyang/Aurelens-iOS/commit/9ee5011d288c003506103988440bf221a1ad090a) (private). Application implementation remains `dbcfa94`; this follow-up changes only tests, capture tooling and records.

Branch: `codex/v0.7.0-build20-monthly`. Existing `v0.7.0-build20` and historical tags are unchanged.
App Store IPA SHA-256: `da8e30d2b25614e2bb6798b18ab9d6682647a5b0927a595aa9e9846d4229cb93`.
