# 安装 0.6.3（build 17）

开发者本机桌面已提供 `AutoGolden-0.6.3-build17-iPhone.ipa`、同名 `.ipa.sha256` 文件和 `安装AutoGolden到iPhone.command`。连接并解锁已登记的 iPhone 17 Pro Max，信任此电脑，开启 iOS 开发者模式，然后双击脚本。三个文件需放在同一目录。

脚本先校验完整性、签名、版本与描述文件，再执行安装。`--check` 参数仅做离线检查。请覆盖安装以保留原有数据，不要先卸载。此次交付未进行真机安装或测试。

公开仓库只提供 [App Store 发行包](downloads/AutoGolden-0.6.3-build17-AppStore.ipa)，供开发者使用 Xcode Organizer 或 Transporter 上传，不支持直接侧载。开发包内含设备登记信息，因此只保存在开发者本地。

此版本尚未上传 App Store Connect、配置 TestFlight 或提交审核；公开下载 IPA 不代表已经上架。用户正式安装需等待后续 TestFlight 邀请或 App Store 发布。
