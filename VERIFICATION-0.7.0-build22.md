# Aurelens 0.7.0 (build 22): startup reliability

Apple reported an indefinite launch loading state on iPad Air 11-inch (M3), iPadOS 26.6, with an active internet connection. The exact reviewer network conditions are unknown.

## Changes

- Local 72-hour device trial access no longer waits for StoreKit. Entitlement and product requests release their UI waiters after eight seconds, including APIs that do not cooperate with cancellation. Only one system request remains in flight at a time. A refresh after a transaction change reads fresh evidence instead of reusing an older in-flight snapshot; late results are accepted. A timeout never grants paid access, restarts a trial, or extends an entitlement.
- Market loading runs independently of news and calendar loading. News and calendar URL sessions have a 15-second overall resource deadline instead of Foundation's default seven days. An active connection alone does not imply that these external services will respond.
- Initial market acquisition has a 15-second deadline. Failed or stalled market requests use the existing explicitly labelled demo fallback. Cancellation prevents a superseded or locked refresh from publishing content.
- Latest-transaction recovery respects any available subscription-status evidence. A non-active or unverified status cannot unlock access, including the declined-purchase history returned by the physical StoreKit test environment.
- No application views, navigation, subscription prices/periods, analysis algorithms, or screenshots were changed.

## Reproduction and evidence

`StartupRegressionTests.testSlowNewsCannotDelayDashboardAndCancelledRefreshDoesNotPublish` failed when the previous sequential startup order was temporarily restored, and passed with the fix. Only the previous startup ordering was restored for this controlled comparison; the dependency-injection test seams remained. This is a deterministic reproduction of a blocking path, not a claim to reproduce Apple's exact network environment.

Private local results live in `build/fix22/`. The expected-failure comparison is retained as `baseline-news-block.xcresult`. Final fixed-source results are reported separately; the expected failure is not counted as a passing test.

The iPad Air 11-inch (M3) simulator uses iPadOS 26.5. Xcode reported that iOS 26.6 was unavailable for download; no exact iPadOS 26.6 test is claimed. The connected iPhone 17 Pro Max reports iOS 27.0 (24A437).

## Completed checks

- Physical iPhone: 79 unit/integration cases passed in each of three separate-process rounds (237 executions), including eight startup fault-injection regressions and local simulated subscription purchase, restoration, cancellation, expiry, refund, approval and decline. Results: `phone-repeat-isolated.xcresult`.
- macOS: all 80 cases passed in `mac-complete-check.xcresult`.
- iPad simulator: all 81 unit/integration cases passed in `ipad-complete-check.xcresult`.
- After uninstalling and reinstalling the final simulator Release 22, launch, all main pages and dashboard rendering passed again (`ipad-release22-fresh-final.xcresult`). This resets the app container; Keychain persistence is intentionally retained. New-device trial behavior is covered by the isolated startup regression.
- Final simulator Release 22 installed over Release 21 passed both UI tests: five cold launches, five foreground returns and all main-page navigation; dashboard content was reached in every iteration. Results: `ipad-release22-final.xcresult`.
- Final development-signed Release 22 was installed over Release 21 on the iPhone. Both standalone UI tests passed: five cold launches, five Home/foreground returns, and Settings, Markets, Forecast, Events, Position, Gold Agent and Overview navigation. All dashboard checks reached content rather than the trial-expired paywall. Results: `phone-release22-final.xcresult`. Text timing attachments include notice-handling and automation overhead; they are not launch benchmarks.
- Production archive/export, project-structure validation, subscription/metadata/Release-bundle audit, signature, installer version/profile and SHA-256 checks passed. The historical branding-only verifier intentionally compares against a pre-subscription release; it was attempted and failed that obsolete baseline comparison, so it is not counted as a current regression result. A direct comparison with build 21 confirms unchanged app views, assets and app entry point.

## Retained failures and limits

Earlier fixture/integration failures are retained alongside the successful final runs. The physical Ask-to-Buy fixture was split into separate approval/refund and decline cases to avoid deleting and reusing transaction history inside one case. Final production code rejects non-active subscription status evidence. Three complete physical rounds passed after that change. Earlier restrictive status handling was discarded before the final archive because it rejected legitimate verified purchases when the local test store returned an empty status index.

One iPad batch failed forced renewal. A subsequent isolated renewal passed. A full isolated-case sweep then passed 12 of 14 cases; the two failures showed local StoreKit purchase/transaction errors, including “Missing transaction data for purchase”. The final unchanged-source complete 81-case run passed, including these cases. This documents simulator variability rather than claiming every attempted run passed.

Two physical UI sessions failed to enable automation before a Mac restart. Automation worked after the restart; the final Release UI run completed successfully. Interrupted sessions are excluded from pass counts.

No real subscription charge or paid AI request was made. Tests use the local Xcode StoreKit environment and isolated in-memory trial records; they do not establish Apple sandbox-server or live storefront behavior. The exact App Review network environment and iPadOS 26.6 remain unverified. Existing screenshots and recordings were not regenerated.

The final archive is `build/Aurelens-0.7.0-build22.xcarchive`. Deliverable exports are in `build/fix22/delivery-debugging` and `build/fix22/delivery-app-store-connect`; older candidate exports in this ignored directory are not the delivery. The local development package and installer are also on the Mac desktop.


Final core execution count: 79 × 3 on iPhone + 81 on iPad + 80 on macOS = **398 passing executions**. Final Release UI suites add five top-level passing cases, including 10 cold-launch iterations and 10 foreground returns across iPhone and iPad. No tests were skipped in these final runs.
