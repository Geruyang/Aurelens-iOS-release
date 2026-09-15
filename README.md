# Aurelens: Gold Market Insights

**Events & AI, 10 Timeframes**

Read gold in context. Aurelens brings ten chart timeframes, global event risk and your manually recorded gold holdings into one XAU/USD research workspace.

- Explore two-day and weekly rise/flat/fall probabilities, median percentage changes and 50%/80% return ranges from similar historical samples. Forecast calculations need no AI API key; estimates are uncertain.
- Compare multi-timeframe consensus from one-minute to yearly charts with technical indicators.
- Put recent, upcoming and continuing global risks beside news and probability estimates.
- Ask OpenAI, DeepSeek or GLM about current analysis and necessary manual-holding summaries after consent. Requires your own API key; provider charges may apply.

App interface: English and Simplified Chinese. Store metadata additionally covers British English, German, French, Italian and Spanish. The build 19 update adds subscription access; existing analysis functionality is retained.

## Current developer release

**0.7.0 build 21 — 2026-09-14 PDT**

This update fixes paid-access recognition after a verified monthly purchase, including relaunch and restoration, while preserving conservative expiry and refund handling. The intended U.S. plan remains **USD 1/month**, automatically renewing unless cancelled. The first-open 3-day trial ends without an automatic charge; users choose to subscribe. Existing trial records, verified annual entitlements and gold research features are retained.

- [GitHub release and downloads](https://github.com/Geruyang/Aurelens-iOS-release/releases/tag/v0.7.0-build21)
- [Release notes](RELEASE-NOTES-0.7.0-build21.md)
- [App Store upload IPA](downloads/Aurelens-0.7.0-build21-AppStore.ipa)
- [Build 21 checksums](SHA256SUMS-0.7.0-build21.txt)
- [Verification report](VERIFICATION-0.7.0-build21.md)
- [App Store Connect upload receipt](APPSTORE-UPLOAD-0.7.0-build21.md)
- [50 screenshots / 9 edited recordings](AppStore-Media/0.7.0-build21/Device-Verification-20260914/)
- [Physical-device report](DEVICE-VERIFICATION-0.7.0-build21.md)
- [Icon and store metadata](AppStore-Media/0.7.0-build21/)
- [Installation information](INSTALLATION.md)
- [Historical build 20 and its failure record](RELEASE-NOTES-0.7.0-build20.md)
- [Previous annual build 19](RELEASE-NOTES-0.7.0-build19.md)

**285 core tests passed**, with 304 final functional/capture checks in total plus 7 fixture/verification/restoration checks. Physical purchase, relaunch, restoration, expiry, refund and payment-sheet cancellation passed using local StoreKit simulation. Earlier test failures and the separately covered simulator purchase skip remain documented. No real charge was made; original phone data was restored.

The binary upload succeeded at 2026-09-15 00:46:33 UTC; Apple reported processing. Review was not submitted. **Live monthly-product configuration, pricing and Apple sandbox-server purchases remain unverified**, so delivery remains a prerelease. The public IPA is an upload artifact, not a directly installable iPhone package. Development packages, device installers and private evidence remain local.

Source repository: [Geruyang/Aurelens-iOS](https://github.com/Geruyang/Aurelens-iOS) (private). The repositories have been renamed to Aurelens; the bundle identifier and historical releases are retained for continuity.

This tool does not execute trades. Data and research estimates may be delayed or inaccurate and are not investment advice.
