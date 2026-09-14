# Aurelens 0.7.0 (build 20) — App Store Connect upload

Uploaded successfully on 2026-09-14 at 16:56:13 UTC using Xcode `exportArchive`, `app-store-connect`, destination `upload`, with automatic build-number changes disabled.

- Version/build: `0.7.0 / 20`
- App ID: `6808663544`
- Bundle ID: `com.geruyang.autogolden.apple`
- Xcode returned `Upload succeeded.` and `EXPORT SUCCEEDED`, exit code 0.
- Apple reported that the package was processing. Later processing completion is not verified.
- App Review has not been submitted.
- App Store export SHA-256: `da8e30d2b25614e2bb6798b18ab9d6682647a5b0927a595aa9e9846d4229cb93`.
- Application implementation commit: `dbcfa94b3273bf8276f860ad07807c1fbc9ae89e`.

Build 20 offers a USD 1/month auto-renewable plan using `com.geruyang.autogolden.fullaccess.monthly`. The 72-hour device trial still requires no payment confirmation and does not charge automatically at expiry. Existing verified annual entitlements remain recognized.

The local monthly product specification is not evidence of an App Store Connect product. Live monthly product setup, storefront pricing, sandbox-server purchases and agreement/bank/tax status remain unverified. Xcode authentication used for binary upload does not provide product-management access.

See [monthly subscription setup](https://github.com/Geruyang/Aurelens-iOS/blob/main/docs/Subscriptions-Implementation.md) and [verification report](VERIFICATION-0.7.0-build20.md). Historical build 19 was retained.

## Physical verification follow-up

The subsequent physical-device run found that a completed local monthly purchase did not unlock paid access. Build 20 is not ready for App Review. The uploaded binary hash is unchanged; no duplicate upload or review submission was performed. See [the physical-device report](DEVICE-VERIFICATION-0.7.0-build20.md).
