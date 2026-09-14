# Aurelens build 19 verification

## Completed checks

| Scope | Result |
|---|---|
| Initial iPhone simulator core | 66 passed |
| Initial iPad simulator core | 66 passed |
| Initial macOS core | 65 passed |
| Initial iPhone/iPad UI | 4 + 4 passed |
| Physical iPhone 17 Pro Max core, iOS 27 | 65 passed, 1 failed |
| Physical iPhone UI | All 8 scenarios passed |
| Additional iPad StoreKit regression | All 8 passed |
| iOS/macOS Release analysis and iOS archive/export | Passed |
| Release signature, version and absence of test-only access hooks | Passed |
| App Store Connect upload, 2026-09-14 | Succeeded; processing at upload completion |

Physical UI scenarios: bilingual navigation/capture, risk-decline/review, trial persistence, ten timeframes/chart controls, manual holding save/undo, pause/resume refresh, simulated annual purchase/restore/refund, and actual cancellation of the simulated payment sheet. No real charge or paid AI request was made. Existing device data was restored after testing.

## Known issue and limits

`SubscriptionStoreKitTests.testCancellationPurchaseFailureAndRestoreFailure` failed on iOS 27 when injecting `.userCancelled`: the local StoreKit service returned `ASDServerErrorDomain 907`, which was displayed as a generic failure. Access was not granted. Actual payment-sheet cancellation on that iPhone and the equivalent injected test on iPadOS Simulator 26.5 passed.

Production product setup, actual storefront pricing, Apple sandbox-server purchase flow and bank/tax/agreement readiness remain unverified. App Review was not submitted. Local Xcode StoreKit tests do not establish production subscription availability. The 72-hour boundary was tested with controlled time; no full natural 72-hour or factory-reset experiment was conducted.

Capture inspection also retained pre-existing event-title escaping and some iPad forecast-card/navigation-title display differences. Private device backups, raw test bundles and registered-device provisioning data remain local.

Detailed implementation and test reports are in the private source repository at tag `v0.7.0-build19`.
