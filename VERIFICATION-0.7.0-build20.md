# Aurelens 0.7.0 (build 20) 月度订阅验证报告

> 后续真机补测发现付费解锁失败，build 20 尚不能视为可发布。以下为较早的模拟器/macOS 阶段记录，请同时阅读[真机测试报告](DEVICE-VERIFICATION-0.7.0-build20.md)。

日期：2026-09-14。Xcode 26.6；iOS/iPadOS Simulator 26.5；macOS 26.6.2。

## 本次变更

新购买改为 `com.geruyang.autogolden.fullaccess.monthly`，目标美国区价格每月 1.00 美元，1 个月自动续期。首次打开的 72 小时免费试用及试用到期后手动购买保持不变。按月周期来自 StoreKit，没有用固定 30 天代替日历月。

只更新订阅商品识别、订阅界面和设置文案；原有行情、预测、事件、持仓、AI、图标与名称保持不变。既有有效年度权益继续按 Apple 验证的原到期日识别，新购买仅加载月度 SKU。`DeviceTrial.swift` 与 build 19 相同，覆盖升级不主动重置试用记录。

## 测试结果

| 范围 | 结果 | 证据（本地 build/monthly20） |
|---|---|---|
| iPhone 17 Pro Max 模拟器核心 | 68 通过，0 失败 | iPhone-core.xcresult |
| iPad Pro 13-inch (M5) 模拟器核心 | 68 通过，0 失败 | iPad-core-final.xcresult |
| macOS 核心 | 67 通过，0 失败 | macOS-core.xcresult |
| iPhone 界面逻辑场景 | 4 个场景最终通过 | iPhone-UI-recovered.xcresult 中 3 项 + iPhone-navigation-final.xcresult 中 1 项 |
| iPad 界面逻辑场景 | 4 个场景最终通过 | iPad-UI-final.log 中导航/风险 2 项 + iPad-subscription-UI-recovered.xcresult 中 2 项 |

核心测试合计 **203 项全部通过**，加上 iPhone/iPad 的 **8 个界面场景最终通过**，共 **211 项最终通过**；另有 2 项模拟购买 UI 测试因环境限制跳过。StoreKit 集成验证了产品金额 Decimal(1)、1 个月周期、自动续期状态、月度购买与恢复、到期失效、关闭续期保留付费期限、重新续期延长权限、退款、家长批准/拒绝、购买取消/错误、产品加载失败恢复及无效签名拒绝。新增测试同时验证旧年度权限保留其原始到期时间。

购买 UI 限制：iPhone 和 iPad 的 `testDisplayedMonthlyPricePurchaseAndUnlock` 因 Xcode UI runner 无法启用 SKTestSession 控制而显式跳过。这不影响应用宿主中的真实 StoreKit 本地集成测试通过，但不能据此宣称该 UI 测试已通过。本轮未测试真机、Apple 沙盒服务器交易或线上扣费；没有产生真实订阅扣款或付费 AI 请求。

## 重试和环境记录

初始同时启动新模拟器和编译检查时，12 GB Mac 出现资源拥堵；中断首轮 iPad/静态检查后改为串行执行，保留中断日志。首轮 iPhone UI 为 4 项未通过、1 项跳过；重启测试环境后，试用、到期和风险提示 3 项通过，导航脚本仍错误地从折叠侧栏推断语言。脚本改为同时匹配英文/中文设置入口并等待导航就绪后，该导航场景独立重跑通过。iPad 首轮导航和风险场景通过后，购买 UI 测试跳过，随后的启动遇到 Mach IPC server died。中断该次执行后，单独运行试用界面又遇到 60 秒启动超时；待设备完成启动后，两个试用界面场景独立重跑均通过。首轮 iPad UI 结果包不是全通过，导航/风险通过证据保留在其日志中。应用生产代码未因这些脚本调整而变化。`iPhone-UI-recovered.xcresult` 整包仍是 3 通过、1 失败，不能将它单独称为全通过。

## 构建与交付

- iOS 与 macOS Release 静态检查最终通过；iOS Simulator 检查为 x86_64，真机 arm64 Release 归档通过。
- App Store 与开发签名两种导出通过；ZIP、严格代码签名、Bundle ID、0.7.0/20、开发描述文件及安装脚本离线校验通过。
- Release 不含 .storekit、XCTest 或 DEBUG 试用/模拟支付入口；App Store 包 get-task-allow=false 且无登记设备列表。
- App Store IPA SHA-256：`da8e30d2b25614e2bb6798b18ab9d6682647a5b0927a595aa9e9846d4229cb93`。
- 开发签名 IPA SHA-256：`22d5c4e5ac253c8ba984289995a980a07ea7f4ffc0b4bee51085282bc212c759`。
- 桌面已有 `Aurelens-0.7.0-build20-iPhone.ipa`、对应校验文件、`安装Aurelens-build20到iPhone.command`、月度订阅说明及版本更新文案。
- [build 20 已成功上传 App Store Connect](APPSTORE-UPLOAD-0.7.0-build20.md)，回执显示进入处理流程，未提交审核。

## 线上收费状态

月度商品仍是本地规格；尚未在本轮 App Store Connect 中创建或核实商品、价格及沙盒支付，网页端认证未确认。Xcode 登录及二进制上传不会代替商品配置。需完成每月 1.00 美元商品设置与应用版本关联后再提交审核。详见 [订阅配置说明](https://github.com/Geruyang/Aurelens-iOS/blob/main/docs/Subscriptions-Implementation.md)。现有年度 build 19 及 GitHub 历史材料保留。
