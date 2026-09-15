# Install Aurelens 0.7.0 (build 21)

The developer’s Mac desktop and ignored local release folder contain `Aurelens-0.7.0-build21-iPhone.ipa`, its `.ipa.sha256` file and `安装Aurelens-build21到iPhone.command`. Keep all three together. Connect and unlock the registered iPhone, trust the Mac, enable Developer Mode, and run the script. An in-place update retains app data. `--check` performs offline verification only.

The installer checks SHA-256, signature, bundle identifier, version and development profile. The development IPA is kept local because its profile contains registered-device information. The final development Release build 21 was installed after testing, with original settings, holdings and chat records restored and verified byte-for-byte.

The public [App Store IPA](downloads/Aurelens-0.7.0-build21-AppStore.ipa) is an upload artifact and cannot be directly sideloaded. [Build 21 upload succeeded](APPSTORE-UPLOAD-0.7.0-build21.md) at 2026-09-15 00:46:33 UTC. Apple reported processing; later processing completion, TestFlight availability and App Store release have not been confirmed. Review was not submitted.

[Verification and limitations](VERIFICATION-0.7.0-build21.md) describe local StoreKit testing, which caused no real charges. The USD 1/month target plan still requires live App Store Connect product/price verification and Apple sandbox-server testing. The first-open 3-day trial does not auto-charge at expiry.

Historical packages, materials and release tags retain their original names.
