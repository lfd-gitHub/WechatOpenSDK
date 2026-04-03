重要!
SDK2.0.5
1. 支持模块化集成：XCFramework 头文件引用改为标准化格式 #import <WechatOpenSDK/WXApi.h>，解决路径冲突并支持 Swift/ObjC 混合开发
2. 修复 openWXApp 偶现失败的问题

SDK2.0.4
1.增加 privacy manifest 文件
2.修复跳微信时可能卡顿的问题

SDK2.0.2
1. 优化 XCFramework 打包方式

SDK2.0.1
1. SDK 支持 XCFramework

SDK2.0.0
1. 分享能力支持内容防篡改校验

SDK1.9.9
1. 授权登录支持关闭自动授权
2. 分享支持添加签名，防止篡改

SDK1.9.7
1. 适配 CocoaPods

SDK1.9.6
1. 适配 iOS 16，减少读写剪切板

SDK1.9.4
1. 修复授权登录取消/拒绝时 state 字段没有带回

SDK1.9.3
1. 新增发起二维码支付能力

SDK1.9.2
1. 新增发起企微客服会话能力

SDK1.9.1
1. 音乐视频分享类型增加运营 H5 字段

SDK1.8.9
1. 增加音乐视频分享类型

SDK1.8.8
1. 增加游戏直播消息类型

SDK1.8.7.1
1. 修复 Xcode11 以下编译不通过

SDK1.8.7
1. 修复 iPadOS，未安装微信的情况下，因为 UA 问题无法授权登录
2. 修复未安装微信的情况下，适配了 UIScene 的 App 因为 UIAlertView Crash
3. 增加 Universal Link 检测函数

SDK1.8.6.2
1. 修改包含"UIWebView"字符的类名

SDK1.8.6.1
1.短信授权登录使用的 UIWebview 切换成 WKWebview

SDK1.8.6
1. 支持 Universal Link 拉起微信以及返回 App
2. SDK 移除 MTA 库

SDK1.8.5
1. 更换 MTA 库：取消对剪切板的访问，防止和其他 SDK 竞争导致 crash
2. NSMutableArray 的 MTA 分类方法改名，减少命名冲突
3. 不含支付功能版本移除非税支付和医保支付接口
4. 分享音乐支持填写歌词和高清封面图

SDK1.8.4
1. 调整分享图片大小限制
2. 新增 openBusinessView 接口

SDK1.8.3
1. SDK 增加调起微信刷卡支付接口
2. SDK 增加小程序订阅消息接口
3. 修复小程序订阅消息接口没有 resp 的问题

SDK1.8.2
1. SDK 增加开发票授权 WXInvoiceAuthInsert
2. SDK 增加非税接口   WXNontaxPay
3. SDK 增加医保接口   WXPayInsurance
4. 更换 MTA 库

SDK1.8.1
1. SDK 打开小程序支持指定版本（体验，开发，正式版）
2. SDK 分享小程序支持指定版本（体验，开发，正式版）
3. SDK 支持输出 log 日志

SDK1.8.0
1. SDK 支持打开小程序
2. SDK 分享小程序支持 shareTicket

SDK1.7.9
1. SDK 订阅一次性消息

SDK1.7.8
1 SDK 分享小程序支持大图

SDK1.7.7
1 增加 SDK 分享小程序
2 增加选择发票接口

SDK1.7.6
1. 提高稳定性
1 修复 mta 崩溃
2  新增接口支持开发者关闭 mta 数据统计上报

SDK1.7.5
1. 提高稳定性
2. 加快 registerApp 接口启动速度

SDK1.7.4
1. 更新支持 iOS 启用 ATS(App Transport Security)
2. 需要在工程中链接 CFNetwork.framework
3. 在工程配置中的"Other Linker Flags"中加入"-Objc -all_load"

SDK1.7.3
1. 增强稳定性，适配 iOS10
2. 修复小于 32K 的 jpg 格式缩略图设置失败的问题

SDK1.7.2
1. 修复因 CTTeleponyNetworkInfo 引起的崩溃问题

SDK1.7.1
1. 支持兼容 ipv6(提升稳定性)
2. xCode Version 7.3.1 (7D1014) 编译

SDK1.7
1. 支持兼容 ipv6
2. 修复若干问题增强稳定性

SDK1.6.3
1. xCode7.2 构建的 sdk 包。
2. 请使用 xCode7.2 进行编译。
3. 需要在 Build Phases 中 Link  Security.framework
4. 修复若干小问题。

SDK1.6.2
1、xCode7.1 构建的 sdk 包
2、请使用 xCode7.1 进行编译

SDK1.6.1
1、修复 armv7s 下，bitcode 可能编译不过
2、解决 warning

SDK1.6
1、iOS 9 系统策略更新，限制了 http 协议的访问，此外应用需要在"Info.plist"中将要使用的 URL Schemes 列为白名单，才可正常检查其他应用是否安装。
受此影响，当你的应用在 iOS 9 中需要使用微信 SDK 的相关能力（分享、收藏、支付、登录等）时，需要在"Info.plist"里增加如下代码：
<key>LSApplicationQueriesSchemes</key>
<array>
<string>weixin</string>
</array>
<key>NSAppTransportSecurity</key>
<dict>
<key>NSAllowsArbitraryLoads</key>
<true/>
</dict>
2、开发者需要在工程中链接上 CoreTelephony.framework
3、解决 bitcode 编译不过问题

SDK1.5
1、废弃 safeSendReq:接口，使用 sendReq:即可。
2、新增+(BOOL) sendAuthReq:(SendAuthReq*) req viewController : (UIViewController*) viewController delegate:(id<WXApiDelegate>) delegate;
支持未安装微信情况下 Auth，具体见 WXApi.h 接口描述
3、微信开放平台新增了微信模块用户统计功能，便于开发者统计微信功能模块的用户使用和活跃情况。开发者需要在工程中链接上:SystemConfiguration.framework,libz.dylib,libsqlite3.0.dylib。
