# 安装与测试说明

## TestFlight（推荐）

构建上传并处理完成、完成所需测试配置后，开发者会提供 TestFlight 邀请。外部测试可能需要 Beta App Review。构建已上传，尚未发布邀请。

## App Store

正式版本获批后，请直接从 App Store 搜索 `AutoGolden` 下载。

## 不支持的安装方式

本仓库中的 `AutoGolden-0.6.2-build12-AppStore.ipa` 已采用 Apple Distribution 签名，但它是供上传 App Store Connect 的分发包，不能通过拷贝到 iPhone、邮件或文件应用直接安装。请等待 TestFlight 邀请或 App Store 上线。

## 开发者上传包

核对 [SHA256SUMS.txt](SHA256SUMS.txt) 后，可通过 Apple Transporter 等 Apple 官方工具上传 IPA。上传前，App Store Connect 应已存在对应应用记录，Bundle ID 为 `com.geruyang.autogolden.apple`。下载 IPA 不代表应用已通过 App Review。

## 报告问题

请通过 [支持页面](support.html) 提交问题，并附上应用版本、iOS 版本、复现步骤和截图（如适用）。请勿公开提交 API Key、密码、验证码、交易账户信息或身份证明。
