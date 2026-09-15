# Aurelens 0.7.0 (build 21): reliable monthly subscription access

Build 21 fixes paid-access reading after a verified monthly purchase; the monthly plan introduced in build 20 is unchanged. Build 19's annual binary and upload remain historical artifacts. Existing verified annual entitlements are honored through their original expiry, but the app offers only the new monthly SKU. See [build 19 implementation](Subscriptions-Implementation-build19.md) for the previous plan.

## Billing behavior

The first foreground opening records a device-local 72-hour trial in Keychain before network-dependent work. No purchase confirmation or automatic payment is initiated for this trial. The date is displayed in a tappable banner and in Settings → Trial and monthly subscription. On expiry, the app displays its paywall and stops gated foreground/background market activity and AI requests; stored positions, model keys and settings remain intact.

Users explicitly confirm an Apple purchase to start a one-month auto-renewable subscription. The intended U.S. base price is USD 1/month (live configuration remains unverified); StoreKit supplies the localized customer price. The purchase sheet and paywall disclose monthly renewal and cancellation. Purchasing before the device trial ends charges immediately and starts the monthly period immediately. Cancelling renewal preserves access through the paid period. Apple, rather than a developer-operated payment service, collects and settles proceeds to the developer's configured bank account subject to agreements, fees, taxes and settlement schedules.

A valid verified subscription also restores access on another device. Only known, verified, unrevoked, unexpired entitlements or verified billing grace may grant paid access. Unverified, failed, cancelled and pending purchases cannot grant paid access. StoreKit transaction updates handle external approvals, refunds and renewals. Restore explicitly invokes AppStore.sync; it never treats a remaining local trial as a restored subscription.

## Build 21 entitlement fix

`Transaction.currentEntitlements` remains the primary source. Each refresh also fetches `Transaction.latest(for:)` for the monthly and legacy annual product IDs. The physical iOS 27 Xcode test store returned verified, unexpired transactions while its entitlement and subscription-status indexes were empty; relying on the entitlement sequence alone therefore left completed purchases in trial mode.

Both sources pass the same signature, auto-renewable product type, product ID, revocation, upgrade and expiration checks. Grace access still requires matching verified subscription status and renewal information. No successful-purchase flag is persisted or trusted. For duplicate transaction IDs, failed verification, revocation, upgrade and the earlier expiration take precedence, so stale evidence cannot override a refund. Valid distinct entitlements can still grant access.

Regression tests cover empty-entitlement-index recovery, expiration, both orders of old/refunded evidence, invalid signatures, restore, relaunch, renewal and legacy annual access. Physical payment UI tests include cancellation, purchase, cold relaunch, restore, expiration, repurchase and refund. iOS 27 local error-injection/status-index limitations are documented separately from application behavior in the build 21 report.

Apple documents using the verified latest transaction and checking its fields before granting access: [latest(for:)](https://developer.apple.com/documentation/storekit/transaction/latest(for:)), [currentEntitlements](https://developer.apple.com/documentation/storekit/transaction/currententitlements), [revocationDate](https://developer.apple.com/documentation/storekit/transaction/revocationdate).

## Production setup still required

The product specification is `StoreKit/AppStoreConnect-product.json`; it is not evidence of a created App Store Connect product. At the time of implementation, no live product has been created in this session. Browser authentication is pending. Xcode account authentication used for signing/export is not App Store Connect product-management API access.

For App Store Connect app **6808663544**, bundle **com.geruyang.autogolden.apple**:

1. Confirm the Paid Apps Agreement, tax and banking information are active. This task does not sign agreements or change bank details.
2. Create the subscription group **Aurelens Access**, then **Aurelens Monthly Access**, product ID **com.geruyang.autogolden.fullaccess.monthly**.
3. Set the subscription duration to **one month** and U.S. customer price to **USD 1.00**, then review Apple's generated local prices and intended storefront availability. Do not silently substitute USD 0.99 if the requested price point is unavailable.
4. Do **not** configure an introductory free trial: the 72-hour device trial is administered by the app and never starts a payment.
5. Add the supplied English/Chinese product localization, review screenshot and review notes. Use a screenshot showing the loaded monthly price and purchase button; the price-unavailable failure-state screenshots are not a substitute for this review screenshot. Verify live product fetching in Apple's sandbox once product configuration propagates.
6. Publish the updated policy/support pages from `docs-site/`, and apply the localized store descriptions from `metadata/`. Terms use Apple's standard EULA.
7. Submit the first subscription with the app version for App Review. Local Xcode StoreKit tests and an exported IPA do not mean the product is approved or purchasable in production.

Review note suggestion: “The app grants 72 hours from first open without payment. Open Settings → Trial and monthly subscription, or tap the bottom trial banner, to inspect and purchase the monthly plan before trial expiry. After expiry the same purchase screen gates the app. Confirm purchases using Apple's payment sheet. Restore and manage/cancel controls and legal links remain accessible while locked. AI model provider API keys and fees are separate; probability forecasts and market analytics do not require an AI key.”

## Device trial limits and privacy

The first-open, last-observed and integrity-state record uses a non-synchronizing, AfterFirstUnlockThisDeviceOnly Keychain item. Read/write/decoding failures fail closed for the trial, while verified paid access remains available. No record is created by a background launch. A monotonic elapsed-time anchor protects the current process against a frozen or backward wall clock, and a backward change over five minutes relative to the saved observation blocks the local trial. The 72-hour duration is independent of daylight saving and display time zone.

Ordinary app relaunch and reinstall do not intentionally reset a retained Keychain record. **This is not a server-enforced hardware identity guarantee.** Keychain persistence after uninstall is platform behavior, and erasing the device, deleting Keychain data or tampering with a compromised device cannot be conclusively defeated by a local-only app. Complete hardware-reset resistance would require a separate trusted backend and device-attestation design. No such service is included or claimed. Users upgrading directly from build 18 start a trial on first opening this subscription version. Upgrades from build 19 or 20 retain their existing trial record and do not restart the 72-hour period.

Elapsed-time measurements and trial records remain on the device. The privacy manifest declares system-uptime use with reason **35F9.1**, alongside the existing UserDefaults declaration. The app receives no bank card information and uploads no trial records or transaction history to a developer-operated server.

## Build and testing

See `docs/Verification-0.7.0-build21.md` for current verification; earlier build results are historical. The local `StoreKit/Aurelens.storekit` fixture is for development tests only and is not included in the released app. Simulator-only trial scenarios are compiled only under DEBUG and targetEnvironment(simulator). The Release bundle audit rejects test entry-point strings, test bundles and StoreKit fixture files.

Tests must be signed. The initial unsigned runs caused Keychain error -34018 and StoreKit SKInternalErrorDomain Code 3; adding correct simulator app/keychain/debug entitlements resolved both. macOS tests use a sandboxed ad-hoc Debug signature with get-task-allow. Release entitlements do not inherit these test permissions. Those signing observations describe earlier build environments. For build 21, the physical UI runner completed simulated purchase and cancellation tests. Simulator purchase UI uses the app-hosted preparation and verification helper documented in `tools/storekit-ui-fixture/README.md`; all ordinary and purchase UI scenarios were ultimately covered, with earlier skips and failures retained in the current verification report.

## References

- https://developer.apple.com/in-app-purchase/
- https://developer.apple.com/app-store/subscriptions/
- https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/overview-for-configuring-in-app-purchases
- https://developer.apple.com/documentation/storekit/transaction/currententitlements
- https://developer.apple.com/documentation/bundleresources/app-privacy-configuration/nsprivacyaccessedapitypes/nsprivacyaccessedapitype

## Apple configuration reference

Apple configures an auto-renewable product's billing duration and price in App Store Connect: [subscription information](https://developer.apple.com/help/app-store-connect/reference/in-app-purchases-and-subscriptions/auto-renewable-subscription-information). Select **1 month**, not a one-year commitment with monthly payments. Use the exact monthly product ID in `StoreKit/AppStoreConnect-product.json`; the app rejects a loaded product with a different duration or an introductory offer.
