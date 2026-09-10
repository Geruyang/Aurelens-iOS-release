# Aurelens 0.6.3 (build 18) — 2026-09-10

New consumer brand: **Aurelens: Gold Market Insights**.
Subtitle: **Events & AI, 10 Timeframes**.

Read gold in context: explore two-day and weekly rise/flat/fall probability estimates and 50%/80% return ranges, compare ten chart timeframes, review global event risks, and ask AI using current analysis and necessary manually recorded holding summaries. AI access requires your own API key; provider charges may apply.

- Home-screen and in-app branding now use Aurelens. The navy and gold bullion/chart icon remains the current branding asset.
- Store copy is prepared for the UK, US, Germany, France, Italy, Spain and Simplified Chinese. The app interface remains English and Simplified Chinese.
- Existing business logic, bundle identifier, privacy manifest, permissions and storage identifiers are unchanged. Only visible brand strings and support URLs changed in production Swift sources.
- 111 unit tests and 4 UI regression tests passed across macOS, iPhone and iPad simulators; static analysis, archive/export, IPA signatures and offline installer checks passed.
- An iPad run displayed the existing market-parser demo fallback (with a Chinese error in the English UI). A separate hourly-feed probe returned HTTP 200 and 1,000 bars. See VERIFICATION.md for scope and limitations.

No physical-device testing, personal paid-model calls, App Store Connect upload, TestFlight distribution or review submission was performed. The public IPA is an App Store upload artifact and cannot be installed directly on an iPhone. The development IPA and installer remain on the developer’s Mac desktop.

Source: [Geruyang/AutoGolden-iOS at 6598597](https://github.com/Geruyang/AutoGolden-iOS/commit/65985976dc6f996e36380bbbafdc7bb836e38b1e) (private).
Source tag: `v0.6.3-build18`.

App Store IPA SHA-256: `1deb1123ec24a65b26f37372098642791328b456d8551e86b7d7fa60cef2d21e`.

Final store branding: Aurelens: Gold Market Insights / Events & AI, 10 Timeframes. The same name and subtitle are used across store locales; descriptions remain localized. Two-day and weekly gold probability forecasts remain a core feature in the description. The IPA, icon, binary-source tag and original packaging report are unchanged.
