# AutoGolden 0.6.2（build 9）构建验证

日期：2026-09-04

- 来源提交：iOS 源码仓库 `151ff99`。
- 环境：macOS 26.6.2、Xcode 26.6（17F113）、iPhoneOS SDK 26.5。
- iOS Release 编译及 Archive 成功；App Store Connect 模式 IPA 导出成功。
- 单元测试：iPhone 17 Pro Max 模拟器、iOS 26.5，20 项通过，0 项失败。
- Bundle ID：`com.geruyang.autogolden.apple`。
- 版本：0.6.2，build 9；设备族为 iPhone、iPad；最低系统版本 17.0。
- IPA 完整性与 `codesign --verify --deep --strict` 验证通过。
- 签名类型为 Apple Distribution，Team 为 `VA8X63NPCS`。
- 描述文件为 App Store 分发类型，无调试授权、无设备 UDID 清单；有效期至 2027-09-04。
- 应用含隐私清单；发布文件不含源代码或签名私钥。

## 尚未完成

- 0.6.2 的物理 iPhone/iPad 完整回归测试。
- App Store Connect 上传、服务端验证、TestFlight 测试与 App Review。

本地签名校验和模拟器测试不等同于 Apple 审核通过，也不等同于物理设备测试。
