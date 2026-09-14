# Aurelens: Gold Market Insights

**Events & AI, 10 Timeframes**

Read gold in context. Aurelens brings ten chart timeframes, global event risk and your manually recorded gold holdings into one XAU/USD research workspace.

- Explore two-day and weekly rise/flat/fall probabilities, median percentage changes and 50%/80% return ranges from similar historical samples. Forecast calculations need no AI API key; estimates are uncertain.
- Compare multi-timeframe consensus from one-minute to yearly charts with technical indicators.
- Put recent, upcoming and continuing global risks beside news and probability estimates.
- Ask OpenAI, DeepSeek or GLM about current analysis and necessary manual-holding summaries after consent. Requires your own API key; provider charges may apply.

App interface: English and Simplified Chinese. Store metadata additionally covers British English, German, French, Italian and Spanish. The build 19 update adds subscription access; existing analysis functionality is retained.

## Current developer release

**0.7.0 build 19 — 2026-09-14**

Adds a 3-day first-open trial with no automatic charge at expiry, followed by an explicitly purchased annual subscription. Purchased subscriptions renew annually unless cancelled. View access status, restore purchases and manage subscriptions in the app. Existing gold research features are retained.

- [GitHub release and downloads](https://github.com/Geruyang/Aurelens-iOS-release/releases/tag/v0.7.0-build19)
- [Release notes](RELEASE-NOTES-0.7.0-build19.md)
- [App Store upload IPA](downloads/Aurelens-0.7.0-build19-AppStore.ipa)
- [Build 19 checksums](SHA256SUMS-0.7.0-build19.txt)
- [Verification report](VERIFICATION-0.7.0-build19.md)
- [App Store Connect upload receipt](APPSTORE-UPLOAD-0.7.0-build19.md)
- [Icon and store metadata](AppStore-Media/0.7.0-build19/)
- [Installation information](INSTALLATION.md)
- [Previous build 18 materials](AppStore-Media/0.6.3-build18/)
- [Public website](https://geruyang.github.io/Aurelens-iOS-release/)

The App Store Connect upload succeeded; Apple reported processing at upload completion. Review has not been submitted. Live subscription product setup remains outstanding. The public IPA is an upload artifact, not a directly installable iPhone package. The development IPA, device installer and private test evidence remain local.

The initial simulator/macOS matrix passed 205 tests. Physical iPhone testing passed 65/66 core tests and all 8 UI scenarios; one injected-cancellation compatibility issue is documented in the report.

Source repository: [Geruyang/Aurelens-iOS](https://github.com/Geruyang/Aurelens-iOS) (private). The repositories have been renamed to Aurelens; the bundle identifier and historical releases are retained for continuity.

This tool does not execute trades. Data and research estimates may be delayed or inaccurate and are not investment advice.
