# AutoGolden 0.6.2（build 16）构建验证

日期：2026-09-06

- 对应源码提交：`f43012c1052dea1b601819c53ce616fc133e6363`。
- 环境：macOS 26.6.2、Xcode 26.6（17F113）、iPhoneOS SDK 26.5。
- iOS Release 编译、Archive 及 App Store Connect 模式 IPA 导出成功。
- macOS 单元测试：37 项通过，0 项失败。
- iPhone 17 Pro Max 真机测试（iOS 26.6.1）：37 项通过，0 项失败；安装和启动验证成功。
- Bundle ID：`com.geruyang.autogolden.apple`。
- 版本：0.6.2，build 16；设备族为 iPhone、iPad；最低系统版本 17.0。
- IPA 完整性与 Apple Distribution 签名验证通过，并已上传 App Store Connect。
- App Store 截图：iPhone 与 iPad、英文与简体中文共 28 张，尺寸和 RGB 模式验证通过。
- App Preview：iPhone 886×1920、iPad 1200×1600，均为 25 秒、H.264、30 fps。
- 应用含隐私清单；发行仓库不含源代码、签名私钥、API Key、设备 UDID 或构建日志。

## 尚未完成

- 在 App Store Connect 的 0.6.2 版本页选择 build 16，并完成最终元数据核对。
- 提交 App Review，等待 Apple 审核。

本地签名、测试和上传成功不等同于 Apple 审核通过或正式上架。
