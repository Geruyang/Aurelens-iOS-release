# Aurelens 0.7.0 (build 21) 验证报告

日期：2026-09-14（America/Los_Angeles）。Xcode 26.6；iPhone 17 Pro Max / iOS 27；iPhone、iPad Pro 13-inch (M5) 模拟器 / 26.5；macOS 26.6.2。应用实现提交：`42c5642cb7b563982bb50180bccfeb77d35d150e`。

## 修复内容

build 20 真机本地 StoreKit 购买返回已验证交易，但 currentEntitlements 和订阅状态未返回权益，导致购买后仍显示试用。build 21 每次刷新同时读取 currentEntitlements 和 Apple 最新交易，接受已验证且未到期的月度或历史年度权益。不会持久化“已付费”标记，也不会用未经验证的数据授予权限。同一交易的多个快照冲突时，验证失败、撤销、升级和更早的到期时间优先，防止旧快照覆盖退款或延长已到期权益。

首次打开 72 小时试用、手动购买、月度自动续期（美国区目标 USD 1/月）保持不变；原行情、概率预测、事件、持仓、AI、品牌、图标均未改动。`DeviceTrial.swift` 未改变。最终发行包由上述实现提交归档；后续修改仅涉及测试、脚本和文档。

## 最终核心测试

证据位于本地忽略目录 `build/fix21/`。公开报告不包含设备标识、个人偏好、聊天备份或原始日志。

| 平台 | 通过 | 失败 / 跳过 | 结果包 |
|---|---:|---|---|
| iPhone 真机 | 70 | 0 / 0 | iPhone-core-release-code-final.xcresult |
| iPhone 模拟器 | 72 | 0 / 0 | iPhone-sim-core-final.xcresult |
| iPad 模拟器 | 72 | 0 / 0 | iPad-core-final.xcresult |
| macOS | 71 | 0 / 0 | mac-core-isolated-final.xcresult |

核心合计 **285 项通过**。覆盖行情和分析既有逻辑、试用首次启动与持久化/时钟回退/存储故障、月度价格 Decimal(1)、1 个月周期及无额外订阅试用优惠、购买与恢复、到期、续期与取消续期、退款、家长审批、产品/支付/同步错误、无效签名拒绝和旧年度权益保留。新增回归覆盖权益索引缺失、到期边界以及冲突或未验证的旧/新证据。

## 界面与真机验证

- 真机购买 UI 两项全部通过：购买→已订阅→冷启动→恢复购买→到期返回原试用→再次购买→退款返回原试用，以及 Apple 本地模拟支付窗口取消。无真实扣款。
- iPhone 模拟器四项普通 UI 通过；购买 UI 通过独立宿主准备流程补测通过，随后验证真实本地 StoreKit 交易与权限。原普通结果包中的购买跳过保留，不能把该原包称为零跳过。
- iPad 模拟器四项普通 UI 通过；重启模拟器并重新准备 StoreKit 后，购买 UI、宿主交易验证和清理均通过。最终证据为 `ipad-storekit-ui-reboot/{prepare,purchase,verify,cleanup}.xcresult`。
- 真机 Release 参考采集与五项功能检查共六项通过；原偏好恢复与最终 Release 状态核验另外两项通过。iPad Release 采集和最终材料数量见[采集报告](DEVICE-VERIFICATION-0.7.0-build21.md)。

## 中间失败与限制

保留所有失败和重试证据。最初真机 StoreKit 测试的 `.userCancelled` 注入被 iOS 27 映射为 ASD 907，且本地 subscription.status 为空；取消支付改由实际 Apple 测试支付窗口验证，自动续期由本地交易属性和强制续期/到期验证。没有把 ASD 907 特判加入生产代码，也没有称该 SDK 行为已修复。到期 UI 原等待 20 秒短于应用既有 30 秒轮询，改为 45 秒后完整生命周期通过。

macOS 最初新增回归遇到 latest 索引暂未可见，测试改为等待其可读后再断言。另一次 expireSubscription 后本地交易、currentEntitlements 和 latest 均仍显示未来到期；保留该失败，独立重跑完整 71 项通过。未以放宽到期条件处理。

Simulator UI runner 无法获得 SKTestSession 控制权限（SKInternalError 3）；临时签名实验无效并已撤回。最终采用应用宿主准备/验证真实本地商店、UI 操作购买的流程，生产订阅客户端不替换。iPad 在早先错误注入测试后出现应用查询为空而宿主能读取购买的差异；重跑和 GUI 启动均无效，重启该模拟器后未改应用代码即通过。诊断用临时日志代码已完全移除，未进入发行归档。

本轮是 StoreKit 本地模拟测试，未进行真实付费，也未发送付费 AI 请求。Apple 沙盒服务器交易、线上商品创建/价格/审核状态尚未核实。App Store Connect 网页仍需登录；Xcode 上传二进制不等于已配置线上订阅。

## 发行检查

iOS arm64 Release 最终归档、开发与 App Store 双导出、Simulator Release 构建通过。项目结构、ZIP 完整性、严格代码签名、Bundle ID、0.7.0/21、描述文件与安装脚本离线检查通过。Release 不含 StoreKit 测试配置、XCTest 或 DEBUG 试用入口，App Store 包不可调试且不含设备登记列表。

App Store IPA SHA-256：`e631cf67f1a95f3410e035bc7ffbe8e109b1a4bfb363ccfbb22e8fcec0940e03`。
开发 IPA SHA-256：`42d82d84fd4ec7e3b5daa26a037eb3237ce22cdf51b6b9da91c6c83bcdd589f4`。

最终 iOS arm64 与 macOS x86_64 Release 静态分析均通过（`analyze-ios-final.log`、`analyze-mac-final.log`）；最终归档编译及发行包审计通过。完整源代码及上述测试结果见此版本分支。上传结果另见[App Store Connect 回执](APPSTORE-UPLOAD-0.7.0-build21.md)。旧版本源码标签和既有截图/发行文件保留。
