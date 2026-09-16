# Aurelens 0.7.0 (build 22) — Startup reliability

Fixed a startup path that could keep the app loading while waiting for App Store or external data services. Local trial access is available without waiting for StoreKit; market loading runs independently of news and calendar requests. Stalled requests now end their loading state and use existing recovery behavior.

The app's research features, interface, 3-day first-open trial and monthly auto-renewing subscription are unchanged. Trial expiry does not automatically charge the user. Existing screenshots and recordings are retained; no new build 22 media were generated.

## 中文更新内容

修复了启动时可能因 App Store 或外部数据服务响应缓慢而持续加载的问题。优化试用资格检查、行情加载及网络超时处理，提升启动和后台返回的稳定性。现有功能、界面和订阅规则保持不变。

## Delivery

The public IPA is an App Store upload artifact and cannot be installed directly on a phone. The development-signed iPhone package and installer remain local on the developer's Mac desktop. This is a developer prerelease, not an announcement of App Store availability.

[Verification](VERIFICATION-0.7.0-build22.md) · [Checksums](SHA256SUMS-0.7.0-build22.txt) · [Installation](INSTALLATION.md)

Source: [Geruyang/Aurelens-iOS at 570bcb6](https://github.com/Geruyang/Aurelens-iOS/commit/570bcb6051be2da01eb6f526a490968cda134c23) (private). Both repositories use version branch `codex/v0.7.0-build22-launch-fix`. Historical release names and tags are unchanged.
