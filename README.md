# Aurelens: Gold Market Insights

**Events & AI, 10 Timeframes**

Read gold in context. Aurelens brings ten chart timeframes, global event risk and your manually recorded gold holdings into one XAU/USD research workspace.

- Explore two-day and weekly rise/flat/fall probabilities, median percentage changes and 50%/80% return ranges from similar historical samples. Forecast calculations need no AI API key; estimates are uncertain.
- Compare multi-timeframe consensus from one-minute to yearly charts with technical indicators.
- Put recent, upcoming and continuing global risks beside news and probability estimates.
- Ask OpenAI, DeepSeek or GLM about current analysis and necessary manual-holding summaries after consent. Requires your own API key; provider charges may apply.

App interface: English and Simplified Chinese. Store metadata additionally covers British English, German, French, Italian and Spanish. The build 19 update adds subscription access; existing analysis functionality is retained.

## Current developer release

**0.7.0 build 20 — 2026-09-14**

New purchases now use a **USD 1/month** U.S. base-price plan with automatic monthly renewal unless cancelled. StoreKit supplies the actual local price. The 3-day first-open trial still ends without an automatic charge; users explicitly choose to subscribe. Existing trial records and verified annual entitlements are retained. Gold research features, name and icon are unchanged.

- [GitHub release and downloads](https://github.com/Geruyang/Aurelens-iOS-release/releases/tag/v0.7.0-build20)
- [Release notes](RELEASE-NOTES-0.7.0-build20.md)
- [App Store upload IPA](downloads/Aurelens-0.7.0-build20-AppStore.ipa)
- [Build 20 checksums](SHA256SUMS-0.7.0-build20.txt)
- [Verification report](VERIFICATION-0.7.0-build20.md)
- [App Store Connect upload receipt](APPSTORE-UPLOAD-0.7.0-build20.md)
- [Icon and store metadata](AppStore-Media/0.7.0-build20/)
- [Installation information](INSTALLATION.md)
- [Previous build 19 release](RELEASE-NOTES-0.7.0-build19.md)
- [Public website](https://geruyang.github.io/Aurelens-iOS-release/)

The binary upload succeeded; Apple reported processing at upload completion. Review has not been submitted. **Live monthly-product configuration and pricing remain unverified.** The public IPA is an upload artifact, not a directly installable iPhone package. Development packages, device installers and private evidence remain local.

**Not ready for App Review:** physical follow-up found that a completed local monthly purchase does not unlock paid access. The final iPhone core run has 62 passes and 6 failures; purchase UI failed and actual payment-sheet cancellation passed. See the [physical-device report](DEVICE-VERIFICATION-0.7.0-build20.md) and [screenshots / recordings](AppStore-Media/0.7.0-build20/Device-Verification-20260914/). The iPad StoreKit serial rerun passed all 9 scenarios. Earlier simulator/macOS results are retained in the original verification report. No real payment was made.

Source repository: [Geruyang/Aurelens-iOS](https://github.com/Geruyang/Aurelens-iOS) (private). The repositories have been renamed to Aurelens; the bundle identifier and historical releases are retained for continuity.

This tool does not execute trades. Data and research estimates may be delayed or inaccurate and are not investment advice.
