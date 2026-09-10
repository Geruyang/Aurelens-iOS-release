# AutoGolden 0.6.3（build 17）测试与交付报告

日期：2026-09-10。环境：macOS 26.6.2、Xcode 26.6（17F113）、iOS/iPadOS Simulator 26.5。

## 变更范围

仅更新名称资源、图标和版本号；增加商店元数据、独立 UI 回归工程及打包/验证工具。8 个应用 Swift 文件与基线 `f43012c1052dea1b601819c53ce616fc133e6363` 逐字节相同。Bundle ID、隐私清单、权限、后台任务标识、设备支持范围和最低系统版本保持一致。

中文名称：AutoGolden黄金行情。副标题：伦敦金走势、技术指标与持仓记录。
英文名称：AutoGolden: Gold Price Tracker。副标题：XAU/USD Charts & Portfolio。
主屏幕名称按系统语言显示为 AutoGolden黄金 / AutoGolden Gold。

## 测试结果

| 检查 | 结果 |
| --- | --- |
| 项目结构、plist、资源引用、隔离与敏感字面量校验 | 通过 |
| 功能源码、权限及隐私清单与基线一致性 | 通过 |
| 商店名称/副标题长度、关键词长度、7 个 RGB 无透明图标尺寸 | 通过 |
| macOS 单元测试 | 37/37，0 失败 |
| iPhone 17 Pro Max 模拟器单元测试 | 37/37，0 失败 |
| iPad Pro 13-inch (M5) 模拟器单元测试 | 37/37，0 失败 |
| iPhone 最终 UI 回归 | 2/2，0 失败 |
| iPad 最终 UI 回归 | 2/2，0 失败 |
| iOS Release 模拟器静态分析/编译 | 通过，包含 x86_64 与 arm64 |
| macOS Release 静态分析与编译 | 通过 |
| iOS arm64 Release 签名归档 | 通过 |
| debugging 开发包与 app-store-connect 发行包导出 | 均通过 |
| 两个 IPA ZIP 完整性、签名、版本、本地化名称及设备族 | 均通过 |
| 开发包设备列表存在、公开发行包无设备列表 | 通过 |
| 安装脚本离线正常包检查 | 通过，未调用真机安装 |
| 安装脚本缺失文件及损坏包拒绝路径 | 通过，非零退出，未调用真机安装 |
| 旧版隐私政策与支持网页 | HTTP 200 |
| 现有行情源联网检查 | 初次 HTTP 502；复测 HTTP 200，返回 1000 根小时线；观察到应用恢复显示行情 |

UI 回归覆盖风险提示拒绝、重新阅读、同意、七个页面导航、语言切换与重启保留、主屏幕名称和图标截图。数据加载允许应用本身的明确标识演示回退，不把演示数据当作实时行情成功。

## 测试过程中的修正

初次手动签名归档被 Xcode 拒绝，因为本机使用 Xcode 管理的描述文件；改用自动签名后归档与两种导出均成功，没有修改证书或应用权限。

最初 UI 脚本使用总览导航标题作为断言。日志和视图层级确认原有总览内嵌图表可在加载后将标题覆盖为 London spot gold；最终改为验证总览独有的 Multi-timeframe trend 内容，并等待导航动画稳定。应用 UI 与功能源码保持不变。初始失败日志保留，最终通过结果以最终 xcresult 为准。

Xcode 发出未使用 AppIntents 时跳过元数据提取的提示；UI 测试 Runner 另有启动画面及启动指标提示。这些不是发布应用的编译错误。

## 安装与发行

- Bundle ID：`com.geruyang.autogolden.apple`；版本：0.6.3；构建：17。
- 最低系统：iOS/iPadOS 17.0，iPhone/iPad。
- 桌面：`AutoGolden-0.6.3-build17-iPhone.ipa`、同名 `.ipa.sha256` 文件、`安装AutoGolden到iPhone.command` 与安装说明。
- 本地源码：`/Users/geruyang/AIProject/AutoGolden-iOS`。
- 本地发行：`/Users/geruyang/AIProject/AutoGolden-iOS-release`。
- GitHub 源码：`https://github.com/Geruyang/AutoGolden-iOS`（私有）。
- GitHub 发行：`https://github.com/Geruyang/AutoGolden-iOS-release`（公开）。
- 原下划线仓库保留历史和政策链接，新的连字符仓库继承其历史。
- 原始测试报告、日志与截图位于源码 `build/verification/`，签名归档同时保存在发行目录的 `local/0.6.3-build17/`。

开发包 SHA-256：`992f341d92ab4784b7c93e02877e550c1e1eb92b81f8ab164ccdb8d09e6782c2`。
App Store 发行包 SHA-256：`969f991017a8eb26e306a9d05288b77e2806c4970f702bbe08f5ceb8485e0f64`。

## 未执行及外部限制

按请求未安装或测试真机。带个人 API Key 的付费模型调用、真机通知交付、系统后台调度与实际设备兼容性未验证，须由用户继续测试。本次没有调用用户的付费模型账号。

未上传 App Store Connect、未验证商店名称占用、未提交审核、未修改销售地区。名称与副标题已备好，但商店搜索流量效果需要上线后观察。行情源曾出现 HTTP 502，复测已恢复 HTTP 200 并返回 1000 根小时线；此结果仅证明检查时可用，已记录间歇性外部服务问题。本次品牌更新没有改动数据源。

对应源码提交：`a962e9b9fad12c53cefea2f495af2119dbad6294`。
