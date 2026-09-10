# AutoGolden 黄金行情 / Gold Price Tracker

本仓库保存 iPhone/iPad 发行包、商店素材、元数据和验证摘要。应用源码位于 [Geruyang/AutoGolden-iOS](https://github.com/Geruyang/AutoGolden-iOS)（私有仓库）。

当前版本：**0.6.3（build 17）**，更换名称与图标，功能保持不变。已生成签名安装包，尚未进行此次版本的真机测试，也未上传 App Store Connect 或提交审核。

- [App Store 发行 IPA](downloads/AutoGolden-0.6.3-build17-AppStore.ipa)：供开发者后续上传，不能直接安装到 iPhone。
- [新图标与中英文元数据](AppStore-Media/0.6.3-build17/)
- [SHA-256 校验](SHA256SUMS.txt)
- [版本说明](RELEASE-NOTES-0.6.3.md) · [验证报告](VERIFICATION.md) · [安装说明](INSTALLATION.md)

名称：AutoGolden黄金行情；副标题：伦敦金走势、技术指标与持仓记录。
英文：AutoGolden: Gold Price Tracker；副标题：XAU/USD Charts & Portfolio。

本地源码位于 `/Users/geruyang/AIProject/AutoGolden-iOS`，发行资料位于 `/Users/geruyang/AIProject/AutoGolden-iOS-release`。开发测试 IPA 与安装脚本已交付到本机桌面，并备份于发行目录 `local/0.6.3-build17/`；此目录不上传 GitHub。公开发行包不包含测试设备登记列表。

旧下划线仓库保留历史与政策网页，应用内已有支持和隐私链接继续可用。新仓库保留原有 Git 历史。本次不改变销售地区、数据源、账户授权方式或功能。

原有行情源首次联网检查返回 HTTP 502，复测恢复 HTTP 200 并返回 1000 根小时线；外部服务的间歇性问题已记录于验证报告。
