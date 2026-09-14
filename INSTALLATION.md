# Install Aurelens 0.7.0 (build 20)

The developer's Mac desktop and local release folder contain `Aurelens-0.7.0-build20-iPhone.ipa`, its `.ipa.sha256` file and `安装Aurelens-build20到iPhone.command`. Keep the three files together. Connect and unlock the registered iPhone, trust the Mac, enable Developer Mode, and run the script. An in-place update retains existing app data. `--check` performs offline package verification only.

The script checks SHA-256, signature, bundle identifier, version and development provisioning profile. The development IPA is kept local because it contains registered-device information.

The public [App Store IPA](downloads/Aurelens-0.7.0-build20-AppStore.ipa) is for developer upload and cannot be directly sideloaded. Build 19 was successfully uploaded to App Store Connect on 14 September 2026; processing completion, TestFlight availability and App Store review/release have not been confirmed.

Build 20 simulator/macOS verification and its limits are documented in [the build 20 verification report](VERIFICATION-0.7.0-build20.md). Simulated subscriptions used Xcode StoreKit Testing and did not cause real charges. The new USD 1/month plan still requires App Store Connect product setup. The 3-day trial does not auto-charge at expiry.

Historical packages, materials and release tags retain their original names.
