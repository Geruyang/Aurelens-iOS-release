> Update, 2026-09-10: build 18 navigation/capture checks now passed on a physical iPhone and iPad simulator. See [the capture report](CAPTURE-0.6.3-build18-round2.md). The packaging-time report below is retained as historical evidence.

# Aurelens 0.6.3（build 18）验证与交付报告

日期：2026-09-10。环境：macOS 26.6.2、Xcode 26.6（17F113）、iOS/iPadOS Simulator 26.5。

## 品牌与变更范围

- 商店名称：**Aurelens: Gold Market Insights**。
- 副标题：**10 Timeframes, AI & Event Risk**。
- 主张：Read gold in context. / 把黄金走势、事件与持仓放在一起看。
- 重点：十周期共识、全球事件风险、结合当前分析和必要手动持仓摘要的 AI 问答。AI 需自行配置 API Key，提供商可能收费。
- 主屏幕和应用内名称统一 Aurelens；深蓝金条与走势线图标沿用本次 build 17 已生成的图标。
- 增加英国、德国、法国、意大利、西班牙商店文案；应用界面仍仅为英文和简体中文。

以源码提交 `a962e9b9fad12c53cefea2f495af2119dbad6294`（build 17）为基线：6 个业务 Swift 文件逐字节一致；另外 2 个文件仅替换可见品牌与公开政策/支持地址。验证脚本按这些精确替换规则比较原始内容，拒绝其他源码变化。Bundle ID、数据存储标识、权限、隐私清单、最低系统版本不变。没有改动行情、指标、事件、概率、持仓、AI、通知或用户设置逻辑。

## 验证结果

| 检查 | 结果 |
| --- | --- |
| 项目结构、plist、资源、敏感字面量与脚本语法 | 通过 |
| 限定品牌替换、权限及隐私清单一致性 | 通过 |
| 7 个 RGB 图标与 7 组商店元数据长度 | 通过 |
| iPhone 17 Pro Max 模拟器单元测试 | 37/37，0 失败 |
| iPad Pro 13-inch (M5) 模拟器单元测试 | 37/37，0 失败 |
| macOS 单元测试 | 37/37，0 失败 |
| iPhone 模拟器 UI 回归 | 2/2，0 失败 |
| iPad 模拟器 UI 回归 | 2/2，0 失败 |
| iOS Release 模拟器静态分析/编译 | 通过，包含 x86_64 与 arm64 |
| macOS Release 静态分析/编译 | 通过 |
| iOS arm64 Release 自动签名归档 | 通过 |
| debugging 和 app-store-connect 两类导出 | 均通过 |
| 两个 IPA 的 ZIP 完整性、代码签名、Bundle ID、build 18、Aurelens 双语显示名 | 均通过 |
| 开发包设备列表存在，商店包无设备列表 | 通过 |
| 安装脚本正常包离线检查 | 通过，没有安装或连接真机 |
| 安装脚本缺失/损坏包拒绝 | 均以非零状态退出 |
| 当前行情源联网检查 | HTTP 200，1,000 根小时线 |
| 英文网站桌面及 440px 手机布局、隐私/支持导航、图片和样式链接 | 通过 |

UI 回归覆盖风险提示拒绝、重新阅读与同意、七个页面导航、语言切换及重启保留、主屏幕品牌。已检查 iPhone 主屏幕以及 iPhone/iPad 总览截图。iPad 总览截图出现既有“行情响应格式无法识别”演示回退提示；英文界面中该错误提示仍为中文。独立小时线探测同时返回 HTTP 200，不能据此认定全部周期实时源都稳定。这两项既有行为记录为后续功能改进，不在本次品牌更新中改动。行情演示回退是既有功能，不以出现演示数据代表实时数据成功。

网页初次加载缺少 favicon，已添加现有品牌图标链接并复查资源 HTTP 200。Playwright 使用本机已有 Chromium for Testing 与随桌面应用提供的 CLI，无需变更系统 Node 环境。Xcode 的 LLDB 版本提示、未使用 AppIntents 时跳过提取提示，以及 UI Runner 的启动画面提示未阻止测试或发行编译。

## 交付与追溯

- Bundle ID：`com.geruyang.autogolden.apple`。版本 0.6.3，构建 18；最低 iOS/iPadOS 17.0。
- 桌面：`Aurelens-0.6.3-build18-iPhone.ipa`、同名 `.ipa.sha256`、`安装Aurelens到iPhone.command`、安装说明和测试报告。
- 开发 IPA SHA-256：`641f86f43d8f799e0afa46cd6299aca496408b0d4cb85efe5e0fddb653d4537a`。
- App Store IPA SHA-256：`1deb1123ec24a65b26f37372098642791328b456d8551e86b7d7fa60cef2d21e`。
- 源码：`/Users/geruyang/AIProject/AutoGolden-iOS`。
- 发行：`/Users/geruyang/AIProject/AutoGolden-iOS-release`。
- 原始日志、xcresult 与模拟器截图：源码 `build/verification18/`；网页截图：`output/playwright/`。
- 签名归档、开发包和安装资料：发行 `local/0.6.3-build18/`，Git 忽略。旧 build 17 桌面文件保存在 `local/0.6.3-build17/desktop-originals/`。
- GitHub 指定仓库：`Geruyang/AutoGolden-iOS`（私有源码）、`Geruyang/AutoGolden-iOS-release`（公开发行）。发布标签 `v0.6.3-build18`。

## 未执行事项

按请求未做真机安装和测试。真实个人 API Key 的付费模型调用、真机通知、实际系统后台调度仍需后续验证；未调用用户的付费账号。单元测试与模拟器验证不能替代这些实际服务/设备测试。

未上传 App Store Connect、验证名称占用、开启 TestFlight、提交审核或改变销售地区。名称检索不是商标清查，流量提升需上线后用数据验证。已有行情服务在 build 17 检查时曾短暂返回 HTTP 502；本次 HTTP 200 仅证明检查时可用。
