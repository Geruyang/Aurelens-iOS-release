# Install Aurelens 0.7.0 (build 22)

The developer's Mac desktop and ignored `local/0.7.0-build22` folder contain `Aurelens-0.7.0-build22-iPhone.ipa`, its `.ipa.sha256` file and `安装Aurelens-build22到iPhone.command`. Keep all three together. Connect and unlock the registered iPhone, trust the Mac, enable Developer Mode, and run the script. An in-place update retains app data. `--check` performs offline verification only.

The installer checks SHA-256, signature, bundle identifier, version and development profile. The development IPA stays local because its profile includes registered-device information. The final development-signed Release 22 was installed over Release 21 on the connected iPhone and passed repeated startup/navigation checks. The phone was left with version 0.7.0 (22) installed.

The public [App Store IPA](downloads/Aurelens-0.7.0-build22-AppStore.ipa) is an upload artifact and cannot be directly sideloaded. [Upload status](APPSTORE-UPLOAD-0.7.0-build22.md) is separate from processing, TestFlight availability and App Review approval.

[Verification and limitations](VERIFICATION-0.7.0-build22.md) describe physical and simulator testing. Local StoreKit simulation caused no real charge. Live storefront configuration and Apple sandbox-server behavior remain unverified. The 3-day first-open trial does not automatically initiate a subscription.

Historical packages, media and release tags retain their original names. No build 22 screenshots or recordings were generated.
