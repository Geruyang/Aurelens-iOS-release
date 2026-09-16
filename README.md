# Aurelens: Gold Market Insights

**Events & AI, 10 Timeframes**

Read gold in context. Aurelens brings ten chart timeframes, global event risk and your manually recorded gold holdings into one XAU/USD research workspace.

- Explore two-day and weekly rise/flat/fall probabilities, median percentage changes and 50%/80% return ranges from similar historical samples. Forecast calculations need no AI API key; estimates are uncertain.
- Compare multi-timeframe consensus from one-minute to yearly charts with technical indicators.
- Put recent, upcoming and continuing global risks beside news and probability estimates.
- Ask OpenAI, DeepSeek or GLM about current analysis and necessary manual-holding summaries after consent. Requires your own API key; provider charges may apply.

App interface: English and Simplified Chinese. Store metadata additionally covers British English, German, French, Italian and Spanish. The build 19 update adds subscription access; existing analysis functionality is retained.

## Current developer release

**0.7.0 build 22 — 2026-09-16 PDT**

This update fixes startup loading that could wait indefinitely for App Store or external data services. Trial access is checked locally, market loading runs independently of news and calendars, and stalled requests have bounded waits. App features and interface are unchanged. The intended plan remains **USD 1/month**, automatically renewing unless cancelled; the first-open 3-day trial does not automatically charge the user.

- [GitHub release and downloads](https://github.com/Geruyang/Aurelens-iOS-release/releases/tag/v0.7.0-build22-release)
- [Release notes](RELEASE-NOTES-0.7.0-build22.md)
- [App Store upload IPA](downloads/Aurelens-0.7.0-build22-AppStore.ipa)
- [Build 22 checksum](SHA256SUMS-0.7.0-build22.txt)
- [Verification report](VERIFICATION-0.7.0-build22.md)
- [App Store Connect upload receipt](APPSTORE-UPLOAD-0.7.0-build22.md)
- [Installation information](INSTALLATION.md)
- [Existing screenshots and recordings, captured on build 21](AppStore-Media/0.7.0-build21/Device-Verification-20260914/)
- [Previous build 21](RELEASE-NOTES-0.7.0-build21.md)
- [Historical build 20 and its failure record](RELEASE-NOTES-0.7.0-build20.md)
- [Previous annual build 19](RELEASE-NOTES-0.7.0-build19.md)

**398 core test executions passed**: 79 cases × 3 rounds on the physical iPhone, 81 on iPad simulator and 80 on macOS. Final Release UI checks passed five cold launches and five foreground returns on each iOS device, main-page navigation and a simulator reinstall check. Earlier failed/interrupted attempts and their resolution are documented. No real charge was made, and no new screenshots or recordings were generated.

The [App Store Connect upload succeeded](APPSTORE-UPLOAD-0.7.0-build22.md) at 2026-09-16 12:09:19 UTC; Apple reported processing. Later processing completion is unverified.

The physical iPhone ran iOS 27.0; the iPad Air 11-inch M3 simulator ran iPadOS 26.5. The exact review runtime, iPadOS 26.6, was unavailable locally. **Live monthly-product configuration, pricing and Apple sandbox-server purchases remain unverified**, so delivery remains a prerelease. The public IPA is an upload artifact, not a directly installable iPhone package. Development packages, installers and private evidence remain local. App Review is not automatically submitted.

Source repository: [Geruyang/Aurelens-iOS](https://github.com/Geruyang/Aurelens-iOS) (private). The repositories have been renamed to Aurelens; the bundle identifier and historical releases are retained for continuity.

This tool does not execute trades. Data and research estimates may be delayed or inaccurate and are not investment advice.
