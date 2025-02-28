---
title： Microsoft Edge 和 WebView2 的区别说明：Microsoft Edge 和 WebView2 之间的功能差异。
author： MSEdgeTeam ms.author： msedgedevrel ms.topic： conceptual ms.prod： microsoft-edge ms.technology： webview no-loc：
- "Autofill for Addresses"
- "Autofill for Passwords"
- "Autofill for Payments""
- "Browser Extensions""
- "Browser Task Manager"
- "Collections"
- "Continue-where-I-left-off prompt"
- "Downloads"
- "Edge Shopping"
- "Family Safety"
- "Favorites"
- "Hotkeys"
- "IE Mode"
- "Immersive Reader"
- "Intrusive Ads"
- "Read Aloud"
- "Smart Screen"
- "Translate"
- "Tracking Prevention"
- "Profile and Identity"
- "Web Payment API"
- "Windows Defender Application Guard"
- “edge:// URLs” ms.date： 03/14/2022

---
# <a name="differences-between-microsoft-edge-and-webview2"></a>Microsoft Edge 与 WebView2 之间的区别

WebView2 基于 Microsoft Edge 浏览器。  你有机会将功能从浏览器扩展到基于 WebView2 的应用，这非常有用。  但是，由于 WebView2 不限于类似浏览器的应用，因此需要修改或删除一些浏览器功能。

本文介绍：

*  修改后的浏览器功能和支持信息。
*  启用或关闭该功能的功能。
*  键盘快捷方式指南。


<!-- ====================================================================== -->
## <a name="design-guidelines"></a>设计指南

在 WebView2 的上下文中，浏览器功能遵循以下设计准则：

*  大多数功能在 WebView2 和 Microsoft Edge 中的工作方式相同。  如果某个功能在 WebView2 上下文或其他原因中没有意义，则会修改或关闭该功能。

*  WebView2 功能不包括 Microsoft Edge 品牌。


<!-- ====================================================================== -->
## <a name="browser-features"></a>浏览器功能

下表显示了与 Microsoft Edge 浏览器不同的 WebView2 功能：

*  **默认状态** 指示该功能是新 WebView2 实例上默认体验的一部分。

*  **可配置** 指示可以使用 WebView2 API 或命令行开关打开或关闭该功能。

> [!NOTE]
> 本文不介绍如何使用命令行开关修改功能。  有关使用命令行开关打开和关闭功能的详细信息，请参阅[Chromium命令行交换机列表](https://peter.sh/experiments/chromium-command-line-switches)。

| 功能 | 默认状态 | 可配置 | 详细信息 |
| --- | --- | --- | --- |
| Autofill for Addresses | 开 | 是 | 默认情况下，此功能处于启用状态。  可以使用 WebView2 自动填充 API 打开或关闭此功能。 |
| Autofill for Passwords | 开 | 是 | 默认情况下，此功能处于启用状态。  可以使用 WebView2 自动填充 API 打开或关闭此功能。 |
| 自动填充付款 | 关闭 | 否 | 此功能已关闭。 |
| 浏览器扩展 | 关闭 | 否 | 此功能已关闭。 |
| Browser Task Manager | 关闭 | 否 | 此功能已关闭。 |
| Collections | 关闭 | 否 | 此功能已关闭。 |
| Continue-where-I-left-off prompt | 关闭 | 否 | 此功能已关闭。 |
| Downloads | 开 | 是 | WebView2 提供了一个 API，可用于自定义下载 UI 以操作下载。 例如，可以阻止、重定向、保存、暂停等。  有关详细信息，请参阅 [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting)。 |
| Edge Shopping | 关闭 | 否 | 此功能已关闭。 |
| Family Safety | 关闭 | 否 | 此功能已关闭。 |
| Favorites | 关闭 | 否 | 此功能已关闭。 |
| IE Mode | 关闭 | 否 | 此功能已关闭。 WebView2 不支持 IE 模式，与 IE (（例如 MHT 或 BIN 支持) ）相比，其行为存在差异。 |
| Immersive Reader | 关闭 | 否 | 此功能取决于用于交互的浏览器 UI。  此功能已关闭。 |
| Intrusive Ads | 关闭 | 否 | 此功能已关闭。 |
| 键盘快捷方式 | 查看详细信息 | 查看详细信息 | 默认情况下关闭的键盘快捷方式在 WebView2 中没有意义或导致问题。  不能关闭或打开这些快捷方式。  相反，可以使用事件侦听密钥组合， `AcceleratorKeyPressed` 并在需要时创建自定义响应。  有关详细信息，请参阅 [其他键盘快捷方式信息](#additional-keyboard-shortcuts-information)。 |
| PDF 批注 | 关闭 | 否 | 此功能已关闭。 已启用 PDF 查看功能，但未启用 PDF 中的绘图、墨迹和突出显示。 有关详细信息，请参阅 [禁用功能：PDF 注释支持](https://github.com/MicrosoftEdge/WebView2Announcements/issues/21)。 |
| 微型菜单 | 关闭 | 否 | 此功能已关闭。 |
| Read Aloud | 关闭 | 否 | 此功能已关闭。 |
| Smart Screen | 开`*` | 否 | `*` 此功能的 UI 已删除，但基础功能仍可用。  此外，可以使用命令行开关关闭 Smart Screen 。 |
| Translate | 关闭 | 否 | 此功能已关闭。 |
| Tracking Prevention | 开`*` | 否 | `*` 此功能的 UI 已删除，但基础功能仍可用。  跟踪防护始终设置为均衡。 |
| 图像悬停时的视觉搜索 | 关闭 | 否 | 此功能已关闭。
| Profile and Identity | 关闭 | 否 | 同步收藏夹、Cookie 等的功能已关闭。 |
| Windows Defender Application Guard | 关闭 | 否 | 此功能已关闭。 |
| edge:// URLs | 查看详细信息 | 否 | Microsoft Edge 浏览器的设置位于 URL 上 `edge://` 。  由于这些网页中的大多数都有 Microsoft Edge 品牌，或者在 WebView2 的上下文中没有意义，因此其中一些 URL 会关闭。  有关详细信息，请参阅 [受阻的内部 URL](#blocked-internal-urls)。 |


<!-- ====================================================================== -->
## <a name="web-platform-features"></a>Web 平台功能

以下 WebView2 平台功能当前不可用：

| 功能 | 详细信息 |
|:--- | :--- |
| 推送通知 | 此功能未在 WebView2 中实现。 |
| Web Payment API | 此功能已关闭。 |


<!-- ====================================================================== -->
## <a name="blocked-internal-urls"></a>阻止的内部 URL

WebView2 中不提供以下 Microsoft Edge 和 Google Chrome 设置网页：

*  `chrome-search://local-ntp/local-ntp.html`
*  `edge://application-guard-internals`
*  `edge://apps`
*  `edge://compat`
*  `edge://extensions`
*  `edge://favorites`
*  `edge://help`
*  `edge://management`
*  `edge://network-error`
*  `edge://new-tab-page`
*  `edge://newtab`
*  `edge://omnibox`
*  `edge://settings`
*  `edge://supervised-user-internals`
*  `edge://version`

<!-- ====================================================================== -->
## <a name="google-authentication"></a>Google 身份验证

Google 已禁用嵌入式 Web 视图（包括 WebView2）中的 Google 身份验证，因为它们设置了安全策略。  请参阅 [嵌入式 Web 视图中 Google OAuth 2.0 授权终结点即将发生的安全更改](https://developers.googleblog.com/2021/06/upcoming-security-changes-to-googles-oauth-2.0-authorization-endpoint.html)。

若要随时了解最新讨论，请在 WebView2Feedback 存储库中查看 [Google Auth Flow 和 WebView2](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1647)。
<!-- ====================================================================== -->
## <a name="additional-keyboard-shortcuts-information"></a>其他键盘快捷方式信息

Microsoft Edge 和 WebView2 支持键盘快捷方式或键绑定。


### <a name="preventing-shortcuts-from-changing-during-update"></a>防止在更新期间更改快捷方式

更新 Microsoft Edge 时，默认键绑定可能会更改。  此外，如果 WebView2 现在支持该功能，默认情况下关闭的键盘快捷方式可能会打开。

若要避免对键盘快捷方式进行此类更改，可以设置为`AreBrowserAcceleratorKeysEnabled``FALSE`关闭访问浏览器功能的所有键，但使所有基本文本编辑和移动快捷方式保持打开状态。


### <a name="shortcuts-that-are-turned-off"></a>已关闭的快捷方式

以下快捷方式始终在 WebView2 中关闭，或被有效关闭。  星号 (`*`) 指示快捷方式未关闭，但它访问的功能已关闭，或者该功能不适用于 WebView2。

| 操作 | 快捷方式 |
|:--- |:--- |
| 添加到 Favorites | `Ctrl`+`D` |
| 将所有选项卡添加到 Favorites | `Ctrl`+`Shift`+`D` |
| 焦点位置 | `Ctrl`+`L, Alt`+`D` |
| 粘贴和转到 | `Ctrl`+`Shift`+`L` |
| 打开文件 | `Ctrl`+`O` |
| Read Aloud `*` | `Ctrl`+`Shift`+`U` |
| Web 捕获 `*` | `Ctrl`+`Shift`+`S` |
| 侧 栏 | `Ctrl`+`Shift`+`E` |
| 保存页 | `Ctrl`+`S` |
| 选择“最后一个”选项卡 | `Ctrl`+`9` |
| 选择“下一个”选项卡 | `Ctrl`+`Tab` |
| 选择“上一个”选项卡 | `Ctrl`+`Shift`+`Tab` |
| 选择选项卡 (1 - 8)  | `Ctrl`+`(1-8)` |
| 显示 Favorites 栏 `*` | `Ctrl`+`Shift`+`B` |
| 帮助 | `F1` |
| 焦点下一个窗格 `*` | `F6`.  在窗口托管模式下受支持，但在视觉托管模式下不受支持。  可视托管模式用于 [WinUI 2 (UWP) 应用](../samples/webview2_sample_uwp.md)，以及适用于 [具有 Visual Composition 的 Win32 C++ 应用](../samples/webview2samplewincomp.md)。 |
| 焦点上一个窗格 `*` | `Shift`+`F6`.  与上述支持相同 `F6` 。 |
| 阅读视图 `*` | `F9` |
| 焦点菜单栏 | `F10` |
| 显示标识菜单 `*` | `Ctrl`+`Shift`+`M` |
| Browser Task Manager `*` | `Shift`+`Escape` |
| 边缘反馈 `*` | `Shift`+`Alt`+`I` |
| “静音”选项卡 `*` | `Ctrl`+`M` |
| “新建隐身”窗口 | `Ctrl`+`Shift`+`N` |
| “新建”选项卡 | `Ctrl`+`T` |
| 新建窗口 | `Ctrl`+`N` |
| 还原上次关闭的选项卡 | `Ctrl`+`Shift`+`T` |
| 对焦 Favorites | `Alt`+`Shift`+`B` |
| 焦点非活动弹出窗口 | `Alt`+`Shift`+`A` |
| 焦点搜索 | `Ctrl`+`E`, `Ctrl`+`K`, `Search Key` |
| “重复”选项卡 | `Ctrl`+`Shift`+`K` |
| 焦点工具栏 `*` | `Alt`+`Shift`+`T` |
| Home 键 | `Alt`+`Home`, `Browser Home Key` |
| 显示应用菜单 | `Alt`+`E, Alt`+`F` |
| 显示 Favorites | `Ctrl`+`Shift`+`O` |
| 显示 Downloads | `Ctrl`+`J` |
| 显示历史记录 | `Ctrl`+`H` |
| 显示阅读模式栏 `*` | `Shift`+`Alt`+`R` |
| 显示 Collections `*` | `Ctrl`+`Shift`+`Y` |


### <a name="shortcuts-turned-off-except-when-event-not-handled"></a>关闭快捷方式（未处理事件时除外）

以下键盘快捷方式始终关闭，但在未处理事件时显示的 `NewWindowRequested` 窗口中除外：

| 操作 | 快捷方式 |
|:--- |:--- |
| 关闭选项卡 | `Ctrl`+`W, Ctrl`+`F4` |
| 关闭窗口 | `Ctrl`+`Shift`+`W` |
| 全屏 | `F11` |


### <a name="shortcuts-turned-off-if-acceleratorenabled-is-false"></a>如果 AcceleratorEnabled 为 False，则快捷方式已关闭

如果设置为`AreBrowserAcceleratorKeysEnabled``FALSE`，将关闭以下附加键盘快捷方式：

| 操作 | 快捷方式 |
|:--- |:--- |
| 停止 | `Escape` |
| 在页面上查找 | `Ctrl`+`F` |
| 查找下一步 | `Ctrl`+`G` |
| 查找上一个 | `Ctrl`+`Shift`+`G` |
| Print | `Ctrl`+`P` |
| 刷新 | `Ctrl`+`R`, `F5`, `Reload Key` |
| 刷新无缓存 | `Ctrl`+`Shift`+`R`, `Ctrl`+`F5`, `Shift`+`F5`, `Ctrl`+`Refresh`, `Shift`+`Refresh` |
| 缩小 | `Ctrl`+`-` |
| 放大 | `Ctrl`+`+` |
| 重置缩放 | `Ctrl`+`0` |
| 查找下一步 | `F3` |
| 查找上一个 | `Shift`+`F3` |
| 后退 | `Alt`+`Left, Browser Back Key` |
| 前进 | `Alt`+`Right`, `Browser Forward Key` |
| Print | `Ctrl`+`P` |
| 打开/关闭 DevTools | `Ctrl`+`Shift`+`I` |
| 打开 DevTools 控制台 | `Ctrl`+`Shift`+`J` |
| 打开 DevTools 检查 | `Ctrl`+`Shift`+`C` |


### <a name="customizing-an-individual-key"></a>自定义单个密钥

若要单独自定义任何密钥，请使用 [AcceleratorKeyPressed](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.acceleratorkeypressed?view=webview2-dotnet-1.0.774.44&preserve-view=true) 事件。
