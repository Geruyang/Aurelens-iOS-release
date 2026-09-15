# Aurelens 0.7.0 (build 21) — App Store Connect upload

Uploaded successfully on **2026-09-15 at 00:46:33 UTC** (14 September, 17:46:33 PDT) using Xcode exportArchive, method app-store-connect, destination upload. Automatic build-number changes were disabled.

- Version/build: `0.7.0 / 21`
- App ID: `6808663544`; bundle ID: `com.geruyang.autogolden.apple`
- Final archive: `Aurelens-0.7.0-build21-final.xcarchive`
- Application implementation: `42c5642cb7b563982bb50180bccfeb77d35d150e`
- Xcode returned `Upload succeeded.` and `EXPORT SUCCEEDED`, exit code 0; ContentDelivery reported `UPLOAD SUCCEEDED with no errors` for IOS build 21 / version 0.7.0.
- Apple reported the uploaded package was processing. Later processing completion has not been verified.
- App Review was not submitted. Existing builds 19 and 20 were retained.

Public App Store export SHA-256: `e631cf67f1a95f3410e035bc7ffbe8e109b1a4bfb363ccfbb22e8fcec0940e03`. The public IPA and uploaded package come from the same final archive; separately exported packages are not claimed byte-identical. The development-signed IPA and device-specific installer remain local.

Build 21 fixes paid-access recognition after a verified monthly purchase. The intended plan remains USD 1/month in the U.S., automatically renewing monthly; the first-open 72-hour device trial does not automatically initiate a subscription. Gold research functionality is unchanged.

[Verification](Verification-0.7.0-build21.md) and [physical-device / simulator media](Device-Verification-0.7.0-build21.md) cover final local StoreKit testing, including simulated purchase, relaunch, restore, expiry, refund and actual test-payment-sheet cancellation. No real charge was made.

Live monthly-product configuration, storefront pricing, sandbox-server transactions and subscription-review association remain unverified. The App Store Connect web session was still logged out during this upload. Xcode authentication and binary upload do not configure the subscription product; see [subscription setup](Subscriptions-Implementation.md). No bank settings or paid agreements were changed.
