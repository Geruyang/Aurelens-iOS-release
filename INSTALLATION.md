# 安装与测试说明

## TestFlight（推荐）

构建在 App Store Connect 处理完成并配置测试信息后，开发者可以提供 TestFlight 邀请。外部测试可能需要 Beta App Review。

## App Store

正式版本获批后，请直接从 App Store 搜索 `AutoGolden` 下载。本次销售范围排除中国大陆。

## 不支持的安装方式

仓库中的 `AutoGolden-0.6.2-build16-AppStore.ipa` 已采用 Apple Distribution 签名，但它是供上传 App Store Connect 的分发包，不能通过拷贝到 iPhone、邮件或“文件”应用直接安装。

## 开发者上传包

核对 [SHA256SUMS.txt](SHA256SUMS.txt) 后，可通过 Apple Transporter、Xcode Organizer 等 Apple 官方方式上传。App Store Connect 应已存在 Bundle ID 为 `com.geruyang.autogolden.apple` 的应用记录。下载 IPA 不代表应用已通过 App Review。

## 报告问题

请通过 [支持页面](support.html) 提交问题，并附上应用版本、iOS 版本、复现步骤和截图（如适用）。请勿公开提交 API Key、密码、验证码、交易账户信息或身份证明。

