---
title: WebView2 SDK 发行说明
description: Microsoft Edge Win32、WPF 和 WinForms 的 WebView2 发行说明。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 06/15/2022
ms.openlocfilehash: 118cbd9858c6e3808ed32fb90dcae6c7a318ff0c
ms.sourcegitcommit: bfe5a842d3a17160f62f007b212901df1cc857ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2022
ms.locfileid: "12595986"
---
# <a name="release-notes-for-the-webview2-sdk"></a>WebView2 SDK 发行说明

WebView2 团队以四周的节奏更新 [WebView2 SDK](https://www.nuget.org/packages/Microsoft.Web.WebView2) 。 本文包含有关 API 的产品公告、添加、修改和重大更改的最新信息。

WebView2 bug 修复（如下面列出的修补程序）特定于运行时或特定于 SDK。


<!-- ====================================================================== -->
## <a name="recommended-browser-channel-and-runtime"></a>建议的浏览器通道和运行时

更新 WebView2 SDK NuGet 包后，请务必重新编译 WebView2 应用。  WebView2 团队建议执行以下操作：

* 使用 WebView2 SDK 包的预发行版本进行开发时，请使用Microsoft Edge的 Canary 预览频道。  Canary 是建议的预览频道，因为它以最快的节奏提供，并且具有最新的 API。

* 使用 WebView2 SDK 包的发布版本时，请使用 Evergreen WebView2 运行时。

有关详细信息，请参阅 [将运行时版本与 SDK 版本匹配](concepts/versioning.md#matching-the-runtime-version-with-the-sdk-version)。


<!-- ====================================================================== -->
## <a name="minimum-version-of-the-browser-or-runtime-to-load-webview2"></a>用于加载 WebView2 的浏览器或运行时的最小版本

若要加载 WebView2，Microsoft Edge或 WebView2 运行时的最小版本为 86.0.616.0。  仅当 Web 平台中发生重大更改时，要加载 WebView2 的最小版本才会更改。

若要使用预发行版 SDK 以及Microsoft Edge预览频道，请参阅[测试即将推出的 API 和功能](how-to/set-preview-channel.md)。


<!-- ====================================================================== -->
## <a name="platforms-covered"></a>涵盖的平台

通常，发行说明适用于 Win32、.NET 和 WinRT。  平台的 API 大致并行，例如：
* Win32 [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2) 以及类似命名的接口，例如 [ICoreWebView2_10](/microsoft-edge/webview2/reference/win32/icorewebview2_10)。
* .NET [CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)。
* WinRT [CoreWebView2 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2)。


<!-- ====================================================================== -->
## <a name="10124522"></a>1.0.1245.22

发布日期：2022 年 6 月 14 日

[NuGet WebView2 SDK 1.0.1245.22 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1245.22)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 102.0.1245.22 或更高版本。

没有相应的预发行包。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现在稳定：

* 提供在应用程序级别信任服务器的 TLS 证书的选项的 [服务器证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_14?view=webview2-1.0.1245.22&preserve-view=true) 。 它会呈现页面，而不提示用户了解 TLS 或提供取消 Web 请求的功能。

*  [ClearBrowsingData API](/microsoft-edge/webview2/reference/win32/icorewebview2profile2?view=webview2-1.0.1245.22&preserve-view=true) 允许开发人员以编程方式清除持续时间内的特定数据类型：
   * `ClearBrowsingData`
   * `ClearBrowsingDataAll`
   * `ClearBrowsingDataInTimeRange`

*  [HttpStatusCode API](/microsoft-edge/webview2/reference/win32/icorewebview2navigationcompletedeventargs2?view=webview2-1.0.1245.22&preserve-view=true)，它为事件中的导航请求`NavigationCompleted`提供 HTTP 状态代码。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了屏幕键盘的问题，即键盘在关闭后不会重新出现，方法是单击 **X** 按钮。 还修复了当用户在 WebView2 中从一个编辑控件切换到另一个编辑控件时键盘被关闭的问题。  ([问题 #460](https://github.com/MicrosoftEdge/WebView2Feedback/issues/460)) 
*  修复了在脚本中使用代理 `AddHostObjectToScript` 时出现的问题。  如果调用 `setHostProperty` 失败，则可能会收到内部错误消息结构，而不是 JavaScript Error 对象。
*  修复了 WebView2 在 WebView2 可见时会从应用中窃取焦点的回归。   ([问题 #862](https://github.com/MicrosoftEdge/WebView2Feedback/issues/862)) 
*  修复了使用大型数据的事件导致内存使用量 `WebResourceRequested` 增加的 bug。   ([问题 #2171](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2171)) 
*  修复 `StatusBarTextChanged` 了回归。 [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1245.22&preserve-view=true) 再次与以前的版本兼容。  ([问题 #2414](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2414)) 
*  更好地支持以管理员身份运行的应用。 ([问题 #2356](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2356)) 


<!-- ====================================================================== -->
## <a name="10121039"></a>1.0.1210.39

发布日期：2022 年 5 月 9 日

[NuGet WebView2 SDK 1.0.1210.39 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1210.39)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 101.0.1210.39 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现在稳定：

* 支持 WebView2 中的 [多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2environment10?view=webview2-1.0.1210.39&preserve-view=true) 。

* [主题 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1210.39&preserve-view=true) 提供一种自定义 WebView2 颜色主题的方式，例如`light``dark`，或 `system`。

* [默认下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1210.39&preserve-view=true) 提供自定义默认下载位置的方法。

<!-- ====================================================================== -->
## <a name="101248-prerelease"></a>1.0.1248-prerelease

发布日期：2022 年 5 月 9 日

[webView2 SDK 1.0.1248-prelease 的NuGet包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1248-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 102.0.1248.0 或更高版本。

### <a name="general"></a>概要

* 通过在 NuGet 包中添加 WinRT JS 投影工具 (**wv2winrt**) ，向 JavaScript 添加了对 WinRT 对象投影的支持。 有关使用 WinRT JS 投影工具的说明，请 [参阅从 Web 端代码调用本机 WinRT 代码](/microsoft-edge/webview2/how-to/winrt-from-js)。

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

* [服务器证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_14?view=webview2-1.0.1248-prerelease&preserve-view=true) 提供一个选项，用于在应用程序级别信任服务器的 TLS 证书，并在不提示用户了解 TLS 或提供取消 Web 请求的功能的情况下呈现页面。

* [ClearBrowsingData API](/microsoft-edge/webview2/reference/win32/icorewebview2profile2?view=webview2-1.0.1248-prerelease&preserve-view=true) 允许开发人员以编程方式清除持续时间内的特定数据类型：
   * `clearBrowsingDataInTimeRange`
   * `clearBrowsingDataAll`

#### <a name="bug-fixes"></a>Bug 修复

* 修复了 WPF 控 `OnWindowPositionChanged` 件事件中发生的不可避免的崩溃。  ([问题 #1531](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1531)) 

* 修复了 .NET SDK 中无法正常工作的问题 `CoreWebView2EnvironmentOptions.ExclusiveUserDataFolderAccess` 。  ([问题 #2363](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2363)) 

* 修复了导致某些Office加载项的运行时回归，这些加载项使用主机对象在以前运行的操作期间崩溃。  ([问题 #2337](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2337)) 

* 修复了在具有不同缩放的监视器之间移动时 WebView2 内容可能变得模糊的问题。

* 修复了回归，以确保 WebView2 创建快速 `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` 失败，而不是超时。

* 修复了Chromium的更改打破了 WebView2 背景色的错误。


<!-- ====================================================================== -->
## <a name="10118539"></a>1.0.1185.39

发布日期：2022 年 4 月 12 日

[NuGet WebView2 SDK 1.0.1185.39 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1185.39)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 100.0.1185.39 或更高版本。

### <a name="general"></a>概要

* 已重 `ICoreWebView2Certificate` 命名为 `ICoreWebView2ClientCertificate`.

#### <a name="promotions"></a>促销

以下项现在稳定：

* 支持 `sessionId` CDP 方法调用[的 CallDevToolsProtocolMethodForSession API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1185.39&preserve-view=true#calldevtoolsprotocolmethodforsession)。

* [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1185.39&preserve-view=true)：
    *  `add_StatusBarTextChanged`
    *  `get_StatusBarText`
    *  `remove_StatusBarTextChanged`

* 支持启用/禁用外部删除操作的 [AllowExternalDrop API](/microsoft-edge/webview2/reference/win32/icorewebview2controller4?view=webview2-1.0.1185.39&preserve-view=true) 。

* [HiddenPdfToolbarItems API](/microsoft-edge/webview2/reference/win32/icorewebview2settings7?view=webview2-1.0.1185.39&preserve-view=true) 可用于自定义 PDF 工具栏项。

* [ExclusiveUserDataFolderAccess API](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2?view=webview2-1.0.1185.39&preserve-view=true) 允许控制其他进程是否可以使用同一用户数据文件夹创建 `WebView2Environment` WebView2，从而共享同一 WebView 浏览器进程实例。

* 请求 [对 iframe 的支持的权限](/microsoft-edge/webview2/reference/win32/icorewebview2frame3?view=webview2-1.0.1185.39&preserve-view=true)：
    * `add_PermissionRequested`
    * `remove_PermissionRequested`


<!-- ====================================================================== -->
## <a name="101222-prerelease"></a>1.0.1222-prerelease

发布日期：2022 年 4 月 12 日

[NuGet WebView2 SDK 1.0.1222-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1222-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 102.0.1222.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

* 添加了 [服务器证书 API，该 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental15?view=webview2-1.0.1222-prerelease&preserve-view=true) 提供了一个选项，用于信任应用程序级别的服务器的 TLS 证书并呈现页面，而无需提示用户了解 TLS 或提供取消 Web 请求的能力。

* 添加了 [Favicon API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental12?view=webview2-1.0.1222-prerelease&preserve-view=true) ，它提供了一种在更改或设置网站时获取 favicon 的方法。

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

* 支持 WebView2 中的 [多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2environment10?view=webview2-1.0.1222-prerelease&preserve-view=true) 。

* [主题 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1222-prerelease&viewFallbackFrom=webview2-1.0.1185.39&preserve-view=true) 提供一种自定义 WebView2 颜色主题的方式，例如`light``dark`，或 `system`。

* [默认下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1222-prerelease&viewFallbackFrom=webview2-1.0.1185.39&preserve-view=true) 提供自定义默认下载位置的方法。

#### <a name="bug-fixes"></a>Bug 修复

* 修复 `ZoomFactor` 了在值超出边界时错误地将值设置 `ZoomFactor` 为最大值的问题。

* 修复了在具有不同缩放的监视器之间移动时 WebView2 内容可能变得模糊的问题。

* 修复了在视觉托管模式下始终为 **0** 的 bug `MouseEvent.movementX` `MouseEvent.movementY`。  ([问题 #2220](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2220)) 

* 修复了 WebView2 中密码回归导致的登录问题。  ([问题 #2291](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2291)) 

* 修复了当用户打开新应用窗口且网页未分配导航条目时导致的故障。

* 对 WinUI 2 (UWP) 中未显示拥有的窗口的 bug 进行了运行时更改。

* 修复 `ICoreWebView2Frame::PostWebMessage` 了源更新后的功能。  ([问题 #2267](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2267)) 


<!-- ====================================================================== -->
## <a name="10115038"></a>1.0.1150.38

发布日期：2022 年 3 月 10 日

[NuGet WebView2 SDK 1.0.1150.38 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1150.38)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 99.0.1150.38 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现在稳定：

*   可让开发人员处理基本 HTTP 身份验证请求和响应的 [BasicAuthentication API](/microsoft-edge/webview2/reference/win32/icorewebview2_10?view=webview2-1.0.1150.38&preserve-view=true) 。


<!-- ====================================================================== -->
## <a name="101189-prerelease"></a>1.0.1189-prerelease

发布日期：2022 年 3 月 10 日

[NuGet WebView2 SDK 1.0.1189-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1189-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 100.0.1189.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*   添加 [了 ContextMenuRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true) ，使主机应用能够创建或修改其自己的上下文菜单。

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

*    支持 CDP 方法调用的 sessionId 的 [CallDevToolsProtocolMethodForSession API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true#calldevtoolsprotocolmethodforsession) 。
*   [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1189-prerelease&preserve-view=true)：
    *  `add_StatusBarTextChanged`
    *  `get_StatusBarText`
    *  `remove_StatusBarTextChanged`
*   支持启用/禁用外部删除的 [AllowExternalDrop API](/microsoft-edge/webview2/reference/win32/icorewebview2controller4?view=webview2-1.0.1189-prerelease&preserve-view=true) 。
*    [HiddenPdfToolbarItems API](/microsoft-edge/webview2/reference/win32/icorewebview2settings7?view=webview2-1.0.1189-prerelease&preserve-view=true) 可用于自定义 PDF 工具栏项。
*  [ExclusiveUserDataFolderAccess API](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2?view=webview2-1.0.1189-prerelease&preserve-view=true) 允许控制其他进程是否可以使用同一用户数据文件夹创建 WebView2。

#### <a name="bug-fixes"></a>Bug 修复

*   修复了 WebView2 应用偶尔被 UWP 卡住的 bug。
*   修复了关闭窗口模式的 **“查找** ”栏后焦点未返回到应用程序的 bug。
*   修复了 `DocumentTitleChanged` 未在单页应用中为向后/向前导航引发事件的 bug。
*   修复了 `HistoryChanged` 未为 Iframe 导航引发事件的 bug。


<!-- ====================================================================== -->
## <a name="10110844"></a>1.0.1108.44

发布日期：2022 年 2 月 6 日

[NuGet WebView2 SDK 1.0.1108.44 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1108.44)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 98.0.1108.44 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现在稳定：

*  [AdditionalAllowedFrameAncestors API](/microsoft-edge/webview2/reference/win32/icorewebview2navigationstartingeventargs2?view=webview2-1.0.1108.44&preserve-view=true)，使开发人员能够提供其他允许的帧上级。
*  [ProcessInfo API](/microsoft-edge/webview2/reference/win32/icorewebview2processinfo?view=webview2-1.0.1108.44&preserve-view=true) 提供有关 WebView2 进程和进程集合的详细信息。
*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame2?view=webview2-1.0.1108.44&preserve-view=true&preserve-view=true)：
   *  `add_NavigationStarting`
   *  `remove_NavigationStarting`
   *  `add_ContentLoading`
   *  `remove_ContentLoading`
   *  `add_NavigationCompleted`
   *  `remove_NavigationCompleted`
   *  `add_DOMContentLoaded`
   *  `remove_DOMContentLoaded`
   *  `ExecuteScript`
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`


<!-- ====================================================================== -->
## <a name="101158-prerelease"></a>1.0.1158-prerelease

发布日期：2022 年 2 月 6 日

[NuGet WebView2 SDK 1.0.1158-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1158-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 100.0.1158.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [状态栏 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental13?view=webview2-1.0.1158-prerelease&preserve-view=true) 以在 Webiew 显示状态消息、URL 或空字符串时提供信息。
*  添加了 [CDP API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental14?view=webview2-1.0.1158-prerelease&preserve-view=true) ，为开发人员提供了 WebView2 中多个 `DevToolsProtocol` 目标的可能性。

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

*  将 ICoreWebView2ClientCertificate 重命名为 [ICoreWebView2Certificate](/microsoft-edge/webview2/reference/win32/icorewebview2certificate?view=webview2-1.0.1158-prerelease&preserve-view=true)。
*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame3?view=webview2-1.0.1158-prerelease&preserve-view=true)：
   *  `add_PermissionRequested`
   *  `remove_PermissionRequested`

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在Visual Studio“错误列表”窗口中导致错误警告的问题。   ([问题 #1722](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1722)) 
*  修复了在打开 PDF 下载时未引发 NewWindowRequested 的 bug。
*  解决了 WinUI3 中未显示选择下拉列表的 bug。   ([问题 #1693](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1693)) 
*  添加了切换 WebView2 静音状态的功能，即使没有音频播放。


<!-- ====================================================================== -->
## <a name="10107254"></a>1.0.1072.54

发布日期：2022 年 1 月 13 日

[webView2 SDK 1.0.1072.54 的NuGet包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1072.54)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 97.0.1072.54 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现在稳定：

*  使开发人员能够在 WebView2 中静音/取消静音媒体的 [媒体 API](/microsoft-edge/webview2/reference/win32/icorewebview2_8?view=webview2-1.0.1072.54&preserve-view=true#summary) 。
*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2_9?view=webview2-1.0.1072.54&preserve-view=true) 支持：
   *  更改下载对话框的位置（相对于 WebView2 边界）。  可以将下载对话框定位到 **“下载** ”按钮，而不是默认位置（即右上角）。
   *  以编程方式打开并关闭默认下载对话框。
   *  对对话框打开和关闭进行更改。


<!-- ====================================================================== -->
## <a name="101133-prerelease"></a>1.0.1133-prerelease

发布日期：2022 年 1 月 13 日

[NuGet WebView2 SDK 1.0.1133-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1133-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 99.0.1133.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了对 [主题](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile2?view=webview2-1.0.1133-prerelease&preserve-view=true) (整体配色方案的支持 - 浅色、深色和 WebView2 的系统) 。
*  添加了设置 [默认下载路径](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile3?view=webview2-1.0.1133-prerelease&preserve-view=true)的方法。
*  添加了对 [清除浏览器数据](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4?view=webview2-1.0.1133-prerelease&preserve-view=true)的支持。
*  添加 [了请求](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe3?view=webview2-1.0.1133-prerelease&preserve-view=true) 对 iframe 的支持的权限。

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1133-prerelease&preserve-view=true)：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`
*  ProcessInfo API 提供有关 WebView2 [进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1133-prerelease&preserve-view=true) 和 [进程集合的](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1133-prerelease&preserve-view=true)详细信息。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1133-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了阻止 `Set-Cookies` 标头出现在事件中的 `WebResourceResponseReceived` bug。
*  解决了弹出窗口和拥有的窗口在关闭前跳转到其他位置而不是随应用窗口一起关闭的 bug。 此 bug 仅在很短的时间段内处于活动状态。
*  修复了关闭文件选取器对话框后的焦点问题。
*  修复了在 WebView2 可见性中查找页面 UI 可见性未更改的 bug。
*  修复了无法找到/加载`WebView2Loader.dll`的 `GetAvailableBrowserVersionString()` bug。  ([问题 #1236](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1236)) 
*  修复了未处理事件时`NewWindowRequested`创建`window.open`的新窗口的大小和位置。  ([问题 #1343](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1343)) 
*  修复了禁用上下文菜单时，迷你菜单仍显示在所选文本上的 bug。 此更改特定于运行时。  ([问题 #1345](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1345)) 
*  修复了在 WinForms 中切换应用后焦点返回到错误位置的 bug。


<!-- ====================================================================== -->
## <a name="101083-prerelease"></a>1.0.1083-prerelease

发布日期：2021 年 11 月 29 日

[NuGet WebView2 SDK 1.0.1083-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1083-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 97.0.1083.0 或更高版本。

### <a name="experimental-features"></a>实验功能

* 在 WebView2 中添加了以下 [适用于 iframe 的 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1083-prerelease&preserve-view=true) ：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`

* 添加了 ProcessInfo API 以提供有关 WebView2 [进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1083-prerelease&preserve-view=true) 和 [进程集合的](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1083-prerelease&preserve-view=true)详细信息。

### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：

*  使开发人员能够在 WebView2 中静音/取消静音媒体的 [媒体 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1083-prerelease&preserve-view=true#summary) 。
*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1083-prerelease&preserve-view=true)。  此 API 支持：
   *  更改下载对话框的位置（相对于 WebView2 边界）。  可以将下载对话框定位到 **“下载** ”按钮，而不是默认位置（即右上角）。
   *  以编程方式打开和关闭默认下载对话框。
   *  对对话框打开和关闭进行更改。

### <a name="bug-fixes"></a>Bug 修复

*  修复了关闭文件选取器对话框后的焦点问题。
*  修复了 WebView2 在初始启动时不接收空间输入的 bug。
*  修复了阻止 WebView2 中单一登录的问题。
*  解决了下载对话框未随 WPF 和 WinForms 上的窗口一起移动的 bug。
*  更新了兼容的命令行检查，以防止需要对可选交换机进行版本检查。
*  修复了导致辅助功能树中显示“Microsoft Edge”品牌的错误。


<!-- ====================================================================== -->
## <a name="10105431"></a>1.0.1054.31

发布日期：2021 年 11 月 29 日

[NuGet WebView2 SDK 1.0.1054.31 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1054.31)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 96.0.1054.31 或更高版本。

### <a name="general"></a>概要

*  常规可靠性修复。

### <a name="bug-fixes"></a>Bug 修复

*  关闭适用于 v96 WebView2 运行时的控制流强制技术 (CET) 阴影堆栈功能。
*  修复了在 .NET 单文件应用程序中启动时导致启动时间缓慢的问题。  ([问题 #1909](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1909)) 
*  修复了Microsoft Edge浏览器策略也错误地应用于 WebView2 导致的崩溃。  ([问题 #1860](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1860)) 
*  修复了关闭包含下载对话框的弹出窗口时发生的崩溃。  ([问题 #1765](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1765)) & ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 


<!-- ====================================================================== -->
## <a name="101056-prerelease"></a>1.0.1056-prerelease

发布日期：2021 年 10 月 29 日

[NuGet WebView2 SDK 1.0.1056-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1056-prerelease)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要Microsoft Edge版本 97.0.1056.0 或更高版本。

### <a name="general"></a>概要

*  常规可靠性改进。

#### <a name="experimental-features"></a>实验功能

*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1056-prerelease&preserve-view=true)。  此 API 支持：
   *  更改下载对话框的位置（相对于 WebView2 边界）。  可以将下载对话框定位到 **“下载** ”按钮，而不是默认位置（即右上角）。
   *  以编程方式打开和关闭默认下载对话框。
   *  对对话框打开和关闭进行更改。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1056-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  现在提供真正的进程退出代码，就像进程失败一`COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED`样`ExitCode``ICoreWebView2ProcessFailedEventArgs2`。
*  开关`--js-flags`现在在提供的开关中`AdditionalBrowserArguments``CoreWebView2EnvironmentOptions`受到尊重。
*  修复了 `name` 对 JavaScript 中主机对象的属性的访问。  ([问题 #641](https://github.com/MicrosoftEdge/WebView2Feedback/issues/641)) 
*  修复了 `InvalidCastException` 在事件循环启动之前隐式初始化的 WPF 控件中的某个控件。  ([问题 #1577](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1577)) 


<!-- ====================================================================== -->
## <a name="10102030"></a>1.0.1020.30

发布日期：2021 年 10 月 25 日

[NuGet WebView2 SDK 1.0.1020.30 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1020.30)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 95.0.1020.30 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  更新 `EnsureCoreWebView2Async` 为在设置 WPF 源属性时不引发异常。  ([问题 #1781](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1781)) 
*  修复了 WebView2 在与显示下载 UI 的多个窗口交互后崩溃的 bug。  ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 

#### <a name="promotions"></a>促销

以下项现在稳定：
*  [PrintToPdf API](/microsoft-edge/webview2/reference/win32/icorewebview2_7?view=webview2-1.0.1020.30&preserve-view=true#printtopdf)。


<!-- ====================================================================== -->
## <a name="1099228"></a>1.0.992.28

发布日期：2021 年 9 月 27 日

[NuGet WebView2 SDK 1.0.992.28 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.992.28)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 94.0.992.31 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了缺少的 WebView2 DLL (导致初始化失败) 在用户的 .NET 项目中未设置时 `PlatformTarget` 。  ([问题 #1061](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1061)) 

#### <a name="promotions"></a>促销

以下项现在稳定：
*  [OpenTaskManagerWindow API](/microsoft-edge/webview2/reference/win32/icorewebview2_6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [isSwipeNavigationEnabled 属性](/microsoft-edge/webview2/reference/win32/icorewebview2settings6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [BrowserProcessExited API](/microsoft-edge/webview2/reference/win32/icorewebview2browserprocessexitedeventargs?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  接口上的`ICoreWebView2NewWindowRequestedEventArgs2`[get_Name属性](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs2?view=webview2-1.0.992.28#get_name&preserve-view=true#summary)。


<!-- ====================================================================== -->
## <a name="101018-prerelease"></a>1.0.1018-prerelease

发布日期：2021 年 9 月 20 日

[NuGet WebView2 SDK 1.0.1018-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1018-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 95.0.1018.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了一个 [媒体 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1018-prerelease&preserve-view=true#summary) ，使开发人员能够在 WebView2 中静音/取消静音媒体。
*  添加了对 [WebView2 的多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment8?view=webview2-1.0.1018-prerelease&preserve-view=true) 的支持。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了当应用跨监视器和监视器规模更改时 WebView2 停止呈现的 bug。
*  修复了在打开多个下载窗口时关闭下载 UI 导致 WebView2 崩溃的 bug。  ([问题 #1723](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1723)) 
*  修复了未在用户的 .NET 项目中设置 PlatformTarget 时生成/初始化错误。  ([问题 #730](https://github.com/MicrosoftEdge/WebViewFeedback/issues/730) 和 [问题 #1548](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1548)) 


<!-- ====================================================================== -->
## <a name="101010-prerelease"></a>1.0.1010-prerelease

发布日期：2021 年 9 月 14 日

[NuGet包，适用于 WebView2 SDK 1.0.1010-prerelease](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1010-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 95.0.1010.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  可靠性修复。  ([问题 #1605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1605) 和 [问题 #1678](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1678)) 
*  在启动期间和主机应用处于前台时添加了性能改进。

#### <a name="experimental-features"></a>实验功能

*  通过使用 `EnsureCoreWebView2Async`删除无提示故障，这会引发 `ArgumentException` 多次使用不兼容参数调用的时间。
*  更改了环境对象中 [UserDataFolder](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment5?view=webview2-1.0.1010-prerelease&preserve-view=true#get_userdatafolder) 属性的默认处理。

   > [!CAUTION]
   > **中断性变更**：如果开发人员未指定放置位置，则用户数据文件夹的默认处理将更改。  请参阅 [公告：用户目录文件夹默认处理更新](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1410)。

*  添加 [了用于 iframe 的导航&脚本 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.1010-prerelease&preserve-view=true) 。
*  添加 [了 MemoryUsageTargetLevel](/microsoft-edge/webview2/reference/win32/icorewebview2experimental5?view=webview2-1.0.1010-prerelease&preserve-view=true) ，使开发人员能够指定内存消耗级别，例如低或正常。
*  向环境选项添加了 [ExclusiveUserDataFolderAccess](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-1.0.1010-prerelease&preserve-view=true) 。
*  添加了 [HiddenPdfToolbarItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.1010-prerelease&preserve-view=true) 以自定义 PDF 工具栏项。
*  添加了 [PrintToPdf](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprinttopdfcompletedhandler?view=webview2-1.0.1010-prerelease&preserve-view=true)，允许将当前页面打印到 PDF。 此外，还可以将可选自定义设置与此新 API 配合使用。
*  添加了 [AllowExternalDrop](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.1010-prerelease&preserve-view=true) 属性，允许将 WebView2 控件外部的对象拖放到其中。
*  添加了允许自定义 WebView2 上下文菜单的 [ContextMenu API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem?view=webview2-1.0.1010-prerelease&preserve-view=true) 。

#### <a name="bug-fixes"></a>Bug 修复

*  改进了在 JavaScript 代码中捕获主机对象异常的方式。
*  将 WebView2 图标替换为 DevTools 窗口中的泛型图标。
*  使用时 `MediaDevices.getDisplayMedia()` 打开 Tab 屏幕共享选项。  ([问题 #1566](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1566)) 
*  修复了未选择正确证书时客户端证书 API 中的 bug。 这是运行时更改。  ([问题 #1666](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1666)) 
*  修复了同一父域中新窗口中不可用的 bug `window.chrome.webview` 。 此更改特定于运行时。  ([问题 #1144](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1144)) 
*  修复了以下 bug：下拉菜单或列表显示在具有焦点的窗口后面。  ([问题 #411](https://github.com/MicrosoftEdge/WebViewFeedback/issues/411)) 
*  修复了使用 `put_IsVisible(false)`时的焦点问题。  ([问题 #238](https://github.com/MicrosoftEdge/WebViewFeedback/issues/238)) 
*  修复了要应用于 `SetVirtualHostNameToFolderMapping` 弹出窗口的 bug。
*  Fixed bugs where an `IDispatch` objects were returned as `IUnknown`.

#### <a name="promotions"></a>促销

以下 API 在此预发行版 SDK 中提升为稳定：
*  `IsSwipeNavigationEnabled`
*  `BrowserProcessExited`
*  `OpenBrowserTaskManager`


<!-- ====================================================================== -->
## <a name="1096133"></a>1.0.961.33

发布日期：2021 年 9 月 8 日

[NuGet WebView2 SDK 1.0.961.33 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.961.33)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 93.0.961.44 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了导致 `ERR_SSL_CLIENT_AUTH_CERT_NEEDED` 错误的 bug。 这是运行时更改。
*  修复了无法使用`AreBrowserAcceleratorKeysEnabled`**“刷新**”、“**开始**”、“**返回**”等特殊浏览器密钥的 bug。 此更改特定于运行时。
*  修复了未呈现透明背景色的 bug。
*  修复了加载 WebView2 时导致白色闪烁的 bug。
*  修复了 WebView2 .NET 控件中的 bug，其中 WebView2 窗口在后台创建时为空白。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 
*  修复了用户导航到或显示 `about:blank` 页面的新窗口时未更新设置的 bug。 这是运行时更改。

#### <a name="promotions"></a>促销

以下项现在稳定：
*  [客户端证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.961.33&preserve-view=true#add_clientcertificaterequested)。


<!-- ====================================================================== -->
## <a name="10955-prerelease"></a>1.0.955-prerelease

发布日期：2021 年 7 月 26 日

[NuGet WebView2 SDK 1.0.955-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.955-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 93.0.967.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  为Windows (ETW) 支持添加了部分事件跟踪。
*  从 `edge://history`中删除了 Microsoft 品牌。
*  新的默认下载 UI。

#### <a name="experimental-features"></a>实验功能

*  添加 [了 OpenTaskManagerWindow](/microsoft-edge/webview2/reference/win32/icorewebview2experimental4?view=webview2-1.0.955-prerelease&preserve-view=true#opentaskmanagerwindow) 以启动 WebView2 浏览器任务管理器。
*  添加了 [NewWindowRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-1.0.955-prerelease&preserve-view=true#get_name)。
*  添加了对虚拟主机名映射的支持，以便与服务辅助角色配合使用。
*  添加了 [HiddenPdfToolbarItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.955-prerelease&preserve-view=true#get_hiddenpdftoolbaritems) 以自定义 PDF 工具栏项。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了中断了页面的 `edge://downloads` `edge://history` bug。 此更改特定于运行时。
*  修复了用于提高WebView2Loader.dll可靠性的 bug。
*  修复了事件处理程序在 `NewWindowRequested` 处理使用 `target=_blank`链接时启动两个窗口的 bug。
*  修复了 WebView2 视觉托管中在启动前闪烁的 bug。
*  修复了未使用使用 `add_NewWindowRequested`WebView2 创建的 WebView2 控件时`add_WebResourceRequested`出现的 bug。  ([问题 #616](https://github.com/MicrosoftEdge/WebViewFeedback/issues/616)) 
*  允许主机应用在不同的应用程序上设置前台，以响应事件，包括 `NavigationStarting`、 `AddHostObjectToScript` 方法 `WebMessageReceived`和 `NewWindowRequested`。  ([问题 #1092](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1092)) 
*  修复 bug 以触发 `PermissionRequested` 麦克风的事件。 此更改是特定于运行时的. ([问题 #1462](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1462)) 
*  修复了多次成功运行后阻止的 `ExecuteScriptAsync` bug。 此更改特定于运行时。  ([问题 #1348](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1348)) 
*  修复了阻止在其中使用`ResultFilePath``DownloadStartingEventArgs`非 ASCII 文件名的 bug。  ([问题 #1428](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1428)) 
*  修复了默认弹出窗口上的标题栏未完全显示的 bug。 此更改特定于运行时。  ([问题 #1016](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1016)) 

#### <a name="promotions"></a>促销
*  [add_ClientCertificateRequested](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.955-prerelease&preserve-view=true#add_clientcertificaterequested) 被提升到稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 WebView2 .NET API 参考文档中仅导致显示第一个异常的问题。
*  .NET core 库现在以发布模式生成。 若要调试，请确保清除 **“仅我的代码”** 复选框。
*  修复了在带有子窗体的表单上导致 WebView2 崩溃的 bug。 打开页面栏中的查找的子窗体在关闭子窗体时导致 WebView2 崩溃。  ([问题 #1097](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1097)) 


<!-- ====================================================================== -->
## <a name="1090249"></a>1.0.902.49

发布日期：2021 年 7 月 26 日

[NuGet WebView2 SDK 1.0.902.49 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902.49)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 92.0.902.49 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了导致属性中断 `IsBuiltInErrorPageEnabled` 的 bug，该 bug 关闭了导航失败或呈现进程失败时显示的错误页。  此更改特定于运行时。  ([问题 #634](https://github.com/MicrosoftEdge/WebViewFeedback/issues/634)) 
*  修复了 WebView2 控件将焦点从用户焦点中移开的问题。
*  修复了未在子窗口上工作时的 `AddScriptToExecuteOnDocumentCreated` bug。  ([问题 #935](https://github.com/MicrosoftEdge/WebViewFeedback/issues/935)) 
*  修复了导致自动丢弃非活动选项卡的 bug。  ([问题 #637](https://github.com/MicrosoftEdge/WebViewFeedback/issues/637)) 
*  修复了导航事件被另一个导航事件中断时导致事件导航 `NavigationCompleted` ID 不正确的 bug。  ([问题 #1142](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1142)) 

#### <a name="promotions"></a>促销

以下项现在处于稳定状态：

*  [add_FrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902.49&preserve-view=true#add_framecreated)。
*  [get_IsGeneralAutofillEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902.49&preserve-view=true#get_isgeneralautofillenabled)。
*  [get_IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902.49&preserve-view=true#get_ispinchzoomenabled)。
*  [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting)。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 支持 iFrame 元素的 API。


<!-- ====================================================================== -->
## <a name="10902-prerelease"></a>1.0.902-prerelease

发布日期：2021 年 6 月 1 日

[NuGet WebView2 SDK 1.0.902-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 92.0.902.0 或更高版本。

### <a name="general"></a>概要

*  改进了 WebView2 启动性能和磁盘占用情况。

#### <a name="experimental-features"></a>实验功能

*  添加 [了 IsSwipeNavigationEnabled 属性，](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_isswipenavigationenabled) 以启用或禁用最终用户在启用触摸输入的设备上使用轻扫手势在 WebView2 中导航的能力。
*  添加 [了 BrowserProcessExited](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment4?view=webview2-1.0.902-prerelease&preserve-view=true#add_browserprocessexited) 事件。
*  添加 [了add_ClientCertificateRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental3?view=webview2-1.0.902-prerelease&preserve-view=true#add_clientcertificaterequested)。 它允许根据需要显示客户端证书对话提示，并允许访问所需的元数据以替换默认的客户端证书对话提示。

#### <a name="bug-fixes"></a>Bug 修复

*  修复鼠标左键单击不关闭上下文菜单的 bug。 此更改特定于运行时。
*  修复了以下 bug：当共享相同用户数据文件夹的应用的 exe 文件具有不一致的版本信息时，WebView2 创建失败。
*  修复了特殊浏览器密钥（例如`Refresh``Home`）无法`Back`禁用`AreBrowserAcceleratorKeysEnabled`的 bug。 此更改特定于运行时。
*  修复了 WebView2 .NET 控件中的 bug，其中 WebView2 窗口在后台创建时为空白。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 。
*  通过使用 WebView2 控件按 `Enter` 下或 `Esc` 不再崩溃 WPF 应用程序来消除文件选取器对话框。  ([问题 #1099](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1099)) 。
*  修复了在附加事件处理程序时 `WebResourceRequested` [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#get_allowsinglesignonusingosprimaryaccount) 无法正常使用 WebView2 的 bug。 此更改特定于运行时。  ([问题 #1183](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1183)) 。
*  下载文件不再会破坏 WebView2 `DefaultBackgroundColor` 透明度。 此更改特定于运行时。  ([问题 #1108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1108)) 。
*  删除了包含 Microsoft 品牌的屏幕共享媒体选取器消息。  ([问题 #940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 WebView2 WinForm 控件中的 bug，其中隐藏父窗体不会隐藏 WebView2 控件 ([问题 #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828) 和 [问题 #1079](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1079)) 。
*  向 WebView2 的 WPF 窗口添加了静态WS_CLIPCHILDREN样式。  ([问题 #1013](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1013)) 。
*  修复了右键单击链接导致 WebView2 主机应用崩溃的 bug。 此更改特定于运行时。
*  修复了在移动到较新的 Edge WebView2 运行时版本时可能会导致主机应用进程崩溃的可靠性 bug。
*  **弃用**：正式弃用 `DefaultBackgroundColor` Windows 7 的 API。

#### <a name="promotions"></a>促销

*  [现在，下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting) 已提升为稳定。
*  [PinchZoom API](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_ispinchzoomenabled) 现已提升为稳定。
*  [AddFrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_framecreated) 现已升级到稳定。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 使用 iFrame 元素支持将 API 提升为稳定。
*  [自动填充 API](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902-prerelease&preserve-view=true#get_isgeneralautofillenabled) 现已升级到稳定。
   > [!NOTE]
   > 当前没有 API 可以删除本地存储的常规自动填充和密码自动保存信息。  请提供一个控件来删除数据，这涉及到删除整个用户数据文件夹。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 WebView2 WinForm 控件中的 bug，其中在释放父窗口后 WebView2 窗口可见性未正确更新。  ([问题 #1282](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1282) 和 [问题 #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828)) 。
*  修复了 WebView2 WPF 控件中的一个 bug，即 WPF OneWay 绑定模式下的源属性绑定无法正常工作。  ([问题 #619](https://github.com/MicrosoftEdge/WebViewFeedback/issues/619) 和 [问题 #608](https://github.com/MicrosoftEdge/WebViewFeedback/issues/608)) 。


<!-- ====================================================================== -->
## <a name="1086435"></a>1.0.864.35

发布日期：2021 年 5 月 31 日

[NuGet WebView2 SDK 1.0.864.35 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.864.35)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 91.0.864.35 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在移动到较新的 Edge WebView2 运行时版本时可能会导致主机应用进程崩溃的可靠性 bug。
*  修复了在某些情况下阻止内存清除的 bug。 此更改特定于运行时。
*  修复了 818 SDK 发布包中项目找不到 `WebView2.h` 文件的错误。  ([问题 #1209](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1209)) 。
*  修复了导致某些具有二进制正文的请求删除 WebResourceRequested 事件的 bug。
*  改进 `NewWindowRequested` 文档。  ([问题 #448](https://github.com/MicrosoftEdge/WebViewFeedback/issues/448)) 。

#### <a name="promotions"></a>促销
*  [UserAgent API](/microsoft-edge/webview2/reference/win32/icorewebview2settings2?view=webview2-1.0.864.35&preserve-view=true#get_useragent) 现在稳定。
*  [IsBrowserkeysenabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings3?view=webview2-1.0.864.35&preserve-view=true#get_arebrowseracceleratorkeysenabled) 现在稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了在迭代 `CoreWebView2WebResourceRequest` 标头集合时缺少第一个标头的 WebView2 .NET 控件中的 bug。  ([问题 #1123](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1123)) 。


<!-- ====================================================================== -->
## <a name="10865-prerelease"></a>1.0.865-prerelease

发布日期：2021 年 4 月 26 日

[NuGet WebView2 SDK 1.0.865-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.865-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 91.0.865.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings4?view=webview2-1.0.865-prerelease&preserve-view=true#ispinchzoomenabled) 设置。 它允许在设置中打开或关闭页面缩放控件。
*  添加了自定义 [add_DownloadStarting](/microsoft-edge/webview2/reference/win32/icorewebview2experimental2?view=webview2-1.0.865-prerelease&preserve-view=true#add_downloadstarting) API。  它允许阻止下载、保存到其他路径，并访问所需的元数据以生成自定义下载 UI。
*  添加了`iframe`[来自 AddHostObjectToScriptWithOrigins 的](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.865-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins)元素支持。
*  为 [WPF 示例应用](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser) 添加了示例代码，用于使用 API 关闭浏览器函数密钥。
*  添加了 [UpdateRuntime](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment3?view=webview2-1.0.865-prerelease&preserve-view=true#updateruntime) API，以便轻松更新 WebView2 运行时。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 `Chromium DevTools Protocol` WebView2 中包含 `POST` 二进制数据的消息的处理程序。
*  关闭 `OpenSaveAsAwareness` 下载 UI，因为它包含指向 `edge://settings`的链接。   ([问题 #1120](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1120)) 。
*  从屏幕共享对话框中删除了品牌。   ([问题 #940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 [SetWindowDisplayAffinity](/windows/win32/api/winuser/nf-winuser-setwindowdisplayaffinity) 函数在 WebView2 应用中停止屏幕捕获时中断 WebView2 的 bug。   ([问题 #841](https://github.com/MicrosoftEdge/WebViewFeedback/issues/841)) 。
*  修复了在将任何笔输入发送到 WebView2 时鼠标输入停止工作的合成托管 bug。
*  修复了任何笔输入后鼠标输入中断的 bug。  此更改特定于运行时。

### <a name="net"></a>.NET

#### <a name="experimental-features"></a>实验功能

*  向 WPF 工具箱添加了 WebView2 设计器工具。   ([问题 #210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  在 .NET 设计器模式下添加了 WebView2 UI 元素。

#### <a name="bug-fixes"></a>Bug 修复

*  通过将每个异常包装在更详细的 .NET 异常中，改进了 COM 异常说明。   ([问题 #338](https://github.com/MicrosoftEdge/WebViewFeedback/issues/338)) 。  此更改特定于运行时。
*  修复了选择`Tab`转移焦点时导致 WebView2 控件在Microsoft Visual Studio工具Office中崩溃时导致的 bug。   ([问题 #589](https://github.com/MicrosoftEdge/WebViewFeedback/issues/589) 和 [问题 #933](https://github.com/MicrosoftEdge/WebViewFeedback/issues/933)) 。  此更改特定于运行时。
*  改进了 .NET framework 加载程序下级，使其更加可靠。   ([问题 #946](https://github.com/MicrosoftEdge/WebViewFeedback/issues/946)) 。
*  修复了在第一次导航完成之前尝试刷新时导致崩溃的 bug。   ([问题 #1011](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1011)) 。
*  修复了初始化，以便在导航期间 `CoreWebView2InitializationCompleted`进行导航。   ([问题 #1050](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1050)) 。
*  改进了 .NET 浏览器进程崩溃错误处理。  现在可以在处理 `ProcessFailed` 事件后重新创建控件，而无需崩溃。   ([问题 #996](https://github.com/MicrosoftEdge/WebViewFeedback/issues/996)) 。


<!-- ====================================================================== -->
## <a name="1081841"></a>1.0.818.41

发布日期：2021 年 4 月 21 日

[NuGet WebView2 SDK 1.0.818.41 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.818.41)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 90.0.818.41 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在针对非呈现器子进程和帧呈现器引发。
*  添加了对 `AddScriptToExecuteOnDocumentCreated`. . 的`iframe`元素支持。
*  改进了 WebView2 代码，使之对格式错误的版本信息的应用程序文件更具复原能力 `.exe` 。   ([问题 #850](https://github.com/MicrosoftEdge/WebViewFeedback/issues/850)) 。
*  从 WebView2 浏览器进程命令行中删除 `--winhttp-proxy-resolver` ，启用了 WebView2 的其他代理命令行选项。


<!-- ====================================================================== -->
## <a name="10824-prerelease"></a>1.0.824-prerelease

发布日期：2021 年 3 月 8 日

[NuGet WebView2 SDK 1.0.824-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.824-prerelease)

为了实现完整的 API 兼容性，此预发行版的 WebView2 SDK 需要Microsoft Edge版本 91.0.824.0 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在针对非呈现器子进程和帧呈现器引发。
*  添加了试验 [性 AreBrowserAcceleratorKeysEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings2?view=webview2-1.0.824&preserve-view=true#get_arebrowseracceleratorkeysenabled) 设置。  可以阻止浏览器响应与导航、打印、保存和其他特定于浏览器的函数相关的键盘快捷方式。
*  添加了对 `AddScriptToExecuteOnDocumentCreated`. . 的`iframe`元素支持。

#### <a name="promotion"></a>推广

*  [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) API 现已升级到“稳定”。
*  光栅化缩放 API ([RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性、  [RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件、 [BoundsMode 属性](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode)和 [ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性) 现已升级到稳定。

#### <a name="bug-fixes"></a>Bug 修复

*  扩展了支持的 C++ 和 .NET 项目类型，例如 MFC 和 ATL。   ([问题 #506](https://github.com/MicrosoftEdge/WebViewFeedback/issues/506)、 [问题 #669](https://github.com/MicrosoftEdge/WebViewFeedback/issues/669) 和 [问题 #851](https://github.com/MicrosoftEdge/WebViewFeedback/issues/851)) 。
*  修复了 Evergreen WebView2 运行时泄漏入站防火墙项的 bug。
*  修复了事件期间的 `WebResourceRequested` 设置响应。   ([问题 #568](https://github.com/MicrosoftEdge/WebViewFeedback/issues/568)) 。
*  修复了导航到 `edge://` 导致浏览器进程退出的 bug。   ([问题 #604](https://github.com/MicrosoftEdge/WebViewFeedback/issues/604)) 。
*  修复了在 Visual Hosting 模式下将 WebView2 限制为屏幕大小的 bug。


<!-- ====================================================================== -->
## <a name="1077444"></a>1.0.774.44

发布日期：2021 年 3 月 8 日

[webView2 SDK 1.0.774.44 的NuGet包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.774.44)

为了实现完整的 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 89.0.774.44 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  在 WebView2 中关闭各种Microsoft Edge浏览器服务。
*  视觉托管 API 现已正式发布。

#### <a name="promotions"></a>促销

*  以下实验性 API 现已升级到稳定。
   *  [DPI 支持](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) 相关的 API
   *  可视托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)
   *  [TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend)
   *  [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor)

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在 Visual Hosting 模式下将 WebView2 限制为屏幕大小的 bug。


<!-- ====================================================================== -->
## <a name="10790-prerelease"></a>1.0.790-prerelease

发布日期：2021 年 2 月 10 日

[NuGet WebView2 SDK 1.0.790 预发行版的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.790-prerelease)

此预发行版的 WebView2 SDK 需要Microsoft Edge版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **中断性变更**：WebView2 预发行包 1.0.781 已弃用。  使用包 1.0.781 停止开发。

> [!IMPORTANT]
> WebView2 预发行包 0.9.430 已弃用，并在下一版本中删除。  如果 WebView2 应用使用该包，WebView2 团队建议你移动到较新的包。

#### <a name="features"></a>功能

*  添加 [了 TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend) 方法以暂停和恢复 WebView。
*  添加 [了 SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping) 方法，用于将虚拟主机名映射到目录路径。   ([问题 #37](https://github.com/MicrosoftEdge/WebViewFeedback/issues/37)、 [问题 #161](https://github.com/MicrosoftEdge/WebViewFeedback/issues/161) 和 [问题 #212](https://github.com/MicrosoftEdge/WebViewFeedback/issues/212)) 。
*  添加了 [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor) 属性以设置背景的颜色和 alpha 通道。   ([问题 #414](https://github.com/MicrosoftEdge/WebViewFeedback/issues/414)) 。
*  添加了 [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings?view=webview2-1.0.790-prerelease&preserve-view=true#get_useragent) 属性以获取或设置用户代理。   ([问题 #122](https://github.com/MicrosoftEdge/WebViewFeedback/issues/122)) 。
*  `CreateCookieWithCookie`将方法替换为`CopyCookie`该方法。
*  使用 [ICoreWebView2CompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller?view=webview2-1.0.790-prerelease&preserve-view=true) 接口添加了视觉托管支持，该接口是使用新 `CreateCoreWebView2CompositionController` 方法创建的 `ICoreWebView2Environment3`。

#### <a name="bug-fixes"></a>Bug 修复

*  在 WebView2 中关闭Microsoft Edge购物功能。
*  何时关闭 PDF 查看器`AreDefaultContextMenusEnabled``false`中的上下文菜单。   ([问题 #605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/605)) 。
*  修复了查询时返回 `E_NOINTERFACE` 的 `ICoreWebView2` `ICoreWebView2Experimental`bug。   ([问题 #691](https://github.com/MicrosoftEdge/WebViewFeedback/issues/691)) 。
*  Fixed a bug that allowed navigation with malformed URIs when `CoreWebView2NavigationStartingEventArgs.Cancel` is set to `false`.   ([问题 #400](https://github.com/MicrosoftEdge/WebViewFeedback/issues/400)) 。
*  修复了在已附加到`NewWindowRequested`事件的事件处理程序的弹出窗口上阻止`window.print()`的 bug。   ([问题 #409](https://github.com/MicrosoftEdge/WebViewFeedback/issues/409)) 。
*  修复了在不同监视器之间移动应用时的动态 DPI 问题。   ([问题 #58](https://github.com/MicrosoftEdge/WebViewFeedback/issues/58)) 
*  改进了 `HRESULT` [ICoreWebView2WebResourceResponseViewGetContentCompletedHandler：：Invoke 传递的实例](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponseviewgetcontentcompletedhandler?view=webview2-1.0.790-prerelease&preserve-view=true#invoke)。
*  关闭自动填充管理按钮。   ([问题 #585](https://github.com/MicrosoftEdge/WebViewFeedback/issues/585)) 。
*  修复了在多个窗口中托管时运行`WebView2.Dispose`时Visual Studio崩溃的问题。   ([问题 #816](https://github.com/MicrosoftEdge/WebViewFeedback/issues/816)) 和 [问题 #442](https://github.com/MicrosoftEdge/WebViewFeedback/issues/442)) 。
*  修复了在工具箱Visual Studio中显示 WebView2 控件的 bug。   ([问题 #210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  减少了 CPU 使用率过高的问题。   ([问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。
*  修复了已弃用的 1.0.781 预发行包的问题。   ([问题 #875](https://github.com/MicrosoftEdge/WebViewFeedback/issues/875) 和 [问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。

#### <a name="promotions"></a>促销

*  以下实验性 API 现已升级到稳定：
   *  可视托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了导致使用 WPF SDK 的 WebView2 应用崩溃的 bug。  当您选择 `F4` 关闭窗口时发生崩溃。   ([问题 #399](https://github.com/MicrosoftEdge/WebViewFeedback/issues/399)) 。
*  WebView2 初始化屏幕现在是透明的，而不是灰色的。   ([问题 #196](https://github.com/MicrosoftEdge/WebViewFeedback/issues/196)) 。


<!-- ====================================================================== -->
## <a name="1070550"></a>1.0.705.50

发布日期：2021 年 1 月 25 日

[NuGet WebView2 SDK 1.0.705.50 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.705.50)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

*  以下实验性 API 现已升级到稳定：
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)


<!-- ====================================================================== -->
## <a name="10721-prerelease"></a>1.0.721-prerelease

发布日期：2020 年 12 月 8 日

[NuGet WebView2 SDK 1.0.721-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.721-prerelease)

此预发行版的 WebView2 SDK 需要Microsoft Edge版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **中断性变更**：WebView2 预发行包 1.0.707 和包 0.9.628 已弃用。  停止使用包 1.0.707 和 package0.9.628 进行开发。

#### <a name="features"></a>功能

*  添加了 [WebView2 组策略](/deployedge/microsoft-edge-webview-policies)。  有关最佳做法，请参阅 [WebView2 的组策略](concepts/enterprise.md#group-policies-for-webview2)。
*  > [!IMPORTANT]
   > **中断性变更**：已弃用旧注册表位置。
   >
   > ```text
   > {Root}\Software\Policies\Microsoft\EmbeddedBrowserWebView\LoaderOverride\{AppId}
   > ```

*  在 WebView2 中添加了对 [拖放](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.721-prerelease&preserve-view=true) 的支持。
*  添加了用于处理 DPI 支持的 API。
   *  添加 [了 RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性以更改 WebView2 内容和 UI 弹出窗口的 DPI 缩放，以及关联 [的 RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件。
   *  添加 [了 ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性，以便根据需要自动更新 `RasterizationScale` 属性。
   *  添加[了 BoundsMode 属性](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode)，用于指定边界是逻辑像素，并允许 WebView2 用于 `RasterizationScale` WebView2 像素显示，WebView2 使用该`RasterizationScale``Bounds`属性来获取物理大小。
*  更新`NewWindowRequested`了要处理`Ctrl`+`click`的事件和 .`Shift`+`click`   ([问题 #168](https://github.com/MicrosoftEdge/WebViewFeedback/issues/168) 和 [问题 #371](https://github.com/MicrosoftEdge/WebViewFeedback/issues/371)) 。
*  以下实验性 API 现已升级到稳定。
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)

### <a name="net"></a>.NET

#### <a name="features"></a>功能

*  在 .NET Core 3.1+ 和 .NET 5 中启用 WinForms 设计器。
*  改进了 .NET Cookie 管理。   ([问题 #611](https://github.com/MicrosoftEdge/WebViewFeedback/issues/611)) 。
*  替换为 `CoreWebView2Ready` [CoreWebView2InitializationCompleted](/dotnet/api/microsoft.web.webview2.core.corewebview2initializationcompletedeventargs)。

#### <a name="bug-fixes"></a>Bug 修复

*  添加 [了 AcceleratorKeyPressed](/dotnet/api/microsoft.web.webview2.wpf.webview2.acceleratorkeypressed) 事件以支持 `AcceleratorKey` WebView2 中的选择。   ([问题 #288](https://github.com/MicrosoftEdge/WebViewFeedback/issues/288)) 。
*  从输出到 WebView2 文件夹中删除了不必要的文件。   ([问题 #461](https://github.com/MicrosoftEdge/WebViewFeedback/issues/461)) 。
*  改进了主机对象 API。   ([问题 #335](https://github.com/MicrosoftEdge/WebViewFeedback/issues/335) 和 [问题 #525](https://github.com/MicrosoftEdge/WebViewFeedback/issues/525)) 。


<!-- ====================================================================== -->
## <a name="1066437"></a>1.0.664.37

发布日期：2020 年 11 月 20 日

[NuGet WebView2 SDK 1.0.664.37 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.664.37)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：.NET WPF/WinForms WebView2 SDK 现已正式发布 (GA) 。  从此版本开始，发布 SDK 是向前兼容的。  有关详细信息，请参阅 [GA 公告博客帖子](https://devblogs.microsoft.com/dotnet/announcing-general-availability-for-microsoft-edge-webview2-for-net-and-fixed-distribution-method)。

#### <a name="features"></a>功能

*  .NET WPF/WinForms WebView2 现已正式发布 (正式版) 。
*  固定的分发 (自带) 模式达到正式版。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  `CoreWebView2NewWindowRequestedEventArgs.Handled` 阻止打开新窗口。   ([问题 #549](https://github.com/MicrosoftEdge/WebViewFeedback/issues/549) 和 [问题 #560](https://github.com/MicrosoftEdge/WebViewFeedback/issues/560)) 。


<!-- ====================================================================== -->
## <a name="10674-prerelease"></a>1.0.674-prerelease

发布日期：2020 年 10 月 19 日

[NuGet WebView2 SDK 1.0.674-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.674-prerelease)

此预发行版的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  添加[了 NavigateWithWebResourceRequest](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#navigatewithwebresourcerequest) 方法，用于在导航过程中提供帖子数据或其他请求标头。
*  添加了在加载和分析初始 HTML 文档时运行的 [DOMContentLoaded](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_domcontentloaded) 事件。
*  在 WebView2 上添加了 [Environment](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_environment) 属性。  此属性公开创建 WebView2 实例的 WebView2 环境。
*  添加了 [Cookie 管理](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_cookiemanager) API，使开发人员能够对 WebView2 会话进行身份验证，或从 WebView2 检索 Cookie 以对其他工具进行身份验证。  WebView2 团队计划进行特定于语言或框架的改进。  请参阅 [API 审阅：Cookie 管理](https://github.com/MicrosoftEdge/WebView2Announcement/issues/2)。
*  更新了 [WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件，并将不可变 [WebResourceResponseView](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true) 和 [WebResourceResponseReceivedEventArgs：:P opulateResponseContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponsereceivedeventargs?view=webview2-0.9.628-prerelease&preserve-view=true#populateresponsecontent) 添加到 [WebResourceResponseView：：GetContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true#getcontent)。
*  在 WebView2 中关闭[Microsoft Defender 应用程序防护 (WDAG) ](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)。
*  添加了用于视觉对象托管 [的 SystemCursorId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller2?view=webview2-1.0.674-prerelease&preserve-view=true#get_systemcursorid) 。
*  在 Visual Hosting 中为输入方法添加了已修复的 bug。
*  删除了使用 WebView2 静态库时的要求 `version.lib` 。

### <a name="net"></a>.NET

*  更新了 [CoreWebView2](/dotnet/api/microsoft.web.webview2.core.corewebview2) 类以公开 `CoreWebView2Environment` 变量。
*  将命名空间中 `Microsoft.Web.WebView2.Core` 自定义 EventArgs 类的实现更改为 [System.EventArgs](/dotnet/api/system.eventargs) 或 [System.ComponentModel.CancelEventArgs](/dotnet/api/system.componentmodel.canceleventargs) 的子类。   ([问题 #250](https://github.com/MicrosoftEdge/WebViewFeedback/issues/250)) 
*  在 WinForms 中添加了对 [CoreWebView2CreationProperties](/dotnet/api/microsoft.web.webview2.winforms) 的支持。   ([问题 #204](https://github.com/MicrosoftEdge/WebViewFeedback/issues/204)) 。
*  添加 [了 WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) .NET API。   ([问题 #219](https://github.com/MicrosoftEdge/WebViewFeedback/issues/219)) 。
*  将 WinForms Designer [Source](/dotnet/api/microsoft.web.webview2.winforms.webview2.source) 属性更新为默认属性或重置为 null。   ([问题 #177](https://github.com/MicrosoftEdge/WebViewFeedback/issues/177)) 。
*  更新了 WebView2.Init () 中的 WebView2 边界，以支持小于 100% 的 DPI 模式。   ([问题 #432](https://github.com/MicrosoftEdge/WebViewFeedback/issues/432)) 。
*  更新了 [BuildWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.buildwindowcore) 和 [DestroyWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.destroywindowcore) 以提高可靠性。   ([问题 #382](https://github.com/MicrosoftEdge/WebViewFeedback/issues/382)) 。
*  更新了 .NET 加载程序基础以在进程位而不是操作系统体系结构上加载。   ([问题 #431](https://github.com/MicrosoftEdge/WebViewFeedback/issues/431)) 。
*  重 `EdgeNotFoundException` 命名为 [WebView2RuntimeNotFoundException](/dotnet/api/microsoft.web.webview2.core.webview2runtimenotfoundexception)。


<!-- ====================================================================== -->
## <a name="1062222"></a>1.0.622.22

发布日期：2020 年 10 月 19 日

[NuGet WebView2 SDK 1.0.622.22 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.622.22)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：Win32 C/C++ WebView2 现已正式发布 (GA) 。  从此版本开始，发布 SDK 是向前兼容的。  请参阅 [GA 公告博客帖子](https://blogs.windows.com/msedgedev/edge-webview2-general-availability)。

*  Evergreen WebView2 运行时和安装程序为 GA。  Microsoft Edge [WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) 上提供了启动程序、Bootstrapper 的下行链接以及 Evergreen WebView2 运行时的独立安装程序。  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)中也提供了安装工作流的示例代码。

有关运行时、常青版分发和固定版本分发的详细信息，请参 [阅分发应用和 WebView2 运行时](concepts/distribution.md)。


<!-- ====================================================================== -->
## <a name="0962211"></a>0.9.622.11

发布日期：2020 年 9 月 10 日

[NuGet WebView2 SDK 0.9.622.11 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.622.11)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：此 SDK 是 WebView2 Win32 C/C++ GA 的发布候选项。  GA 版本应使用相同的 API 接口和功能。

*  已断开 [连接的浏览器策略](/deployedge/microsoft-edge-policies)。
*  在 WebView2 环境选项上添加了 [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#get_allowsinglesignonusingosprimaryaccount) 属性，以启用 WebView2 的条件访问。
*  更新 `ICoreWebView2NewWindowRequestedEventArgs` 为包括 [WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.622&preserve-view=true#get_windowfeatures) 属性和关联的 [ICoreWebView2WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2windowfeatures?view=webview2-0.9.622&preserve-view=true)。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  更新 `System.Windows.Rect`  为使用 `System.Drawing.Rectangle` ，而不是 `System.Windows.Rect` ([问题 #235](https://github.com/MicrosoftEdge/WebViewFeedback/issues/235)) 。
*  更新了 NewWindowRequested 事件以处理 `window.open()` 不带参数的请求。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  使用`ICoreWebView2EnvironmentOptions`指定的 [AdditionalBrowserArguments](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#put_additionalbrowserarguments) 不会使用环境变量或注册表值重写。  请参阅 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.622&preserve-view=true#createcorewebview2environmentwithoptions)。


<!-- ====================================================================== -->
## <a name="09579"></a>0.9.579

发布日期：2020 年 7 月 20 日

[NuGet WebView2 SDK 0.9.579 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.579)

此版本的 WebView2 SDK 需要Microsoft Edge版本 86.0.579.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：Evergreen WebView2 运行时和安装程序发布以进行预览。  请参阅 [“分发应用”和“WebView2 运行时](concepts/distribution.md)”。

*  > [!IMPORTANT]
   > **公告**：下一个 SDK 发布后不再支持以下 WebView2 SDK 版本：
   >
   > *  [0.8.190](#08190)
   > *  [0.8.230](#08230)
   > *  [0.8.270](#08270)
   > *  [0.8.314](#08314)
   > *  [0.8.355](#08355)
   >
   > WebView2 SDK 版本在 nuget.org 上也被标记为已弃用。 WebView2 建议保持最新版本的 WebView2。

*  添加了 WebView2 辅助角色线程改进。   ([问题 #318](https://github.com/MicrosoftEdge/WebViewFeedback/issues/318)) 。
*  在 WebView2 中关闭弹出窗口阻止程序。  请参阅事件中的 `NewWindowRequested` [IsUserInitiated](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.538&preserve-view=true#get_isuserinitiated) 属性。
*  确保运行 `about:blank`WebView2 导航启动事件。  现在，`NavigationStarting`所有导航都会运行事件，但不支持或`srcdoc`忽略元素的`iframe`取消`about:blank`。
*  在 WebView2 中阻止了某些 `edge://` URI 方案。
*  在 WebView2 环境选项上添加了实验性 [IsSingleSignOnUsingOSPrimaryAccountEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-0.9.538-prerelease&preserve-view=true#get_issinglesignonusingosprimaryaccountenabled) 属性，以启用 WebView2 的条件访问。
*  添加了在 WebView2 从 WebResource 请求接收和处理响应后运行的实验性 [WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-0.9.538-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件。  身份验证标头（如果有）包含在响应对象中。

### <a name="net"></a>.NET

*  改进了 WPF 焦点处理。   ([问题 #185](https://github.com/MicrosoftEdge/WebViewFeedback/issues/185)) 。
*  在 WPF Webview2 控制器上添加 `ZoomFactor` 了属性。


<!-- ====================================================================== -->
## <a name="09538"></a>0.9.538

[NuGet WebView2 SDK 0.9.538 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.538)

此版本的 WebView2 SDK 需要Microsoft Edge版本 85.0.538.0 或更高版本。

### <a name="general"></a>概要

*  放弃对 WebView2 SDK 版本 [0.8.149](#08149) 的支持。  WebView2 建议保持最新版本的 WebView2。
*  更新了组策略，用于考虑何时修改Microsoft Edge浏览器的配置文件路径 ([#179](https://github.com/MicrosoftEdge/WebViewFeedback/issues/179)) 。

### <a name="win32-cc"></a>Win32 C/C++

*  添加了 [ICoreWebView2ExperimentalNewWindowRequestedEventArgs：：get_WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-0.9.538-prerelease&preserve-view=true#get_windowfeatures)，在运行时 `window.open()` 触发，并与 [ICoreWebView2ExperimentalWindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwindowfeatures?view=webview2-0.9.538-prerelease&preserve-view=true) ([#70](https://github.com/MicrosoftEdge/WebViewFeedback/issues/70)) 关联。
*  > [!IMPORTANT]
   > **中断性变更**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) 并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.538&preserve-view=true#createcorewebview2environmentwithoptions)。

*  > [!IMPORTANT]
   > **重大更改**：为了确保 WebView2 API 与Windows API 命名约定保持一致，WebView2 团队更新了以下名称。
   >
   > *  [IsRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_areremoteobjectsallowed) 现在是 [AreHostObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.538&preserve-view=true#get_arehostobjectsallowed)。

*  更新了 [AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.538&preserve-view=true#addhostobjecttoscript)。  原始主机对象序列化程序标记现在设置为代理对象。  然后，当在 JavaScript 回调 ([#148](https://github.com/MicrosoftEdge/WebViewFeedback/issues/148)) 中作为参数传递时，主机对象序列化标记将作为主机对象序列化。

### <a name="net-09538-prerelease"></a>.NET (0.9.538 预发行版) 

*  发布的 WinForms 和 WPF WebView2API 示例，是 WebView2 SDK 的综合指南。  请参阅 [示例存储库](https://github.com/MicrosoftEdge/WebView2Samples)。
*  添加了对视觉托管和窗口功能 [实验性 API](concepts/versioning.md#experimental-apis) 的支持。
*  > [!IMPORTANT]
   > **中断性变更**：以下延迟现在实现 IDisposable：  [ScriptDialogOpening](/dotnet/api/microsoft.web.webview2.core.corewebview2.scriptdialogopening)、 [NewWindowRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.newwindowrequested)、 [WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) 和 [PermissionRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.permissionrequested)。

*  添加 [了 GetAvailableBrowserVersionString](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.getavailablebrowserversionstring) 和 [CompareBrowserVersions](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.comparebrowserversions) 作为 [CoreWebView2Environment](/dotnet/api/microsoft.web.webview2.core.corewebview2environment) 静态。


<!-- ====================================================================== -->
## <a name="09515-prerelease"></a>0.9.515-prerelease

[NuGet WebView2 SDK 0.9.515-prerelease 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.515-prerelease)

此预发行版的 WebView2 SDK 需要Microsoft Edge版本 84.0.515.0 或更高版本。

*  > [!IMPORTANT]
   > **公告**：WebView2 现在支持 .NET Framework 4.6.2 或更高版本的 Windows 窗体 和 WPF，**在预发行包**中支持 .NET Core 3.0 或更高版本。

*  有关生成 WPF 应用的详细信息，请参阅 [WPF 应用中的 WebView2 开始](get-started/wpf.md)和特定于 WPF 的 API 的 WebView2 [WPF 参考](/dotnet/api/microsoft.web.webview2.wpf)。
*  有关构建Windows 窗体应用的详细信息，请参阅 [WinForms 应用中 WebView2 的开始](get-started/winforms.md)，以及适用于Windows 窗体特定 API 的 WebView2 [Windows 窗体参考](/dotnet/api/microsoft.web.webview2.winforms)。
*  有关 CoreWebView2 API 的详细信息，请参 [阅 .NET 参考](/dotnet/api/microsoft.web.webview2.core)。
*  > [!CAUTION]
   > **已知问题**：WebView2 团队知道预发行版中的一些问题，这些问题将在未来版本中得到解决。
   >
   > *  **DPI 感知**：WPF 的 WebView2 目前不了解 DPI。  在高 DPI 监视器上初始化 WebView2 时，存在一个已知问题：WebView2 控件最初初始化为窗口的一小部分，直到窗口调整大小。
   > *  **WPF 设计器**：当前不支持 WPF 设计器。  通过直接修改文本编辑器中的相应 XAML，在应用中添加 WebView2 控件。


<!-- ====================================================================== -->
## <a name="09488"></a>0.9.488

[NuGet WebView2 SDK 0.9.488 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.488)

此版本的 WebView2 SDK 需要Microsoft Edge版本 84.0.488.0 或更高版本。

*  > [!IMPORTANT]
   > **公告**：从即将推出的Microsoft Edge版本 83 开始，Evergreen WebView2 不再面向稳定浏览器通道。  相反，它面向另一组二进制文件（品牌为 Evergreen WebView2 运行时），你可以通过 WebView2 团队当前正在开发的安装程序进行链式安装。  请参阅 [“分发应用”和“WebView2 运行时](concepts/distribution.md)”。

*  > [!IMPORTANT]
   > **公告**：WebView2 团队将发布两个包：一个预发行包，其中包含实验性 API (供你试用) ，以及一个稳定 API 的稳定发布包， (为你) 提供置信度。  若要了解这些差异，请参阅 [了解浏览器版本和 WebView2](concepts/versioning.md)。

*  > [!IMPORTANT]
   > **重大更改**：为了确保 WebView2 API 与Windows API 命名约定保持一致，WebView2 团队更新了以下接口的名称。
   >
   > *  `CORE_WEBVIEW2_*` 前缀现在是 `COREWEBVIEW2_*`。
   > *  [GetCoreWebView2BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.430&preserve-view=true#getcorewebview2browserversioninfo) 现在是 [GetAvailableCoreWebView2BrowserVersionString](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#getavailablecorewebview2browserversionstring)。
   > *  [get_BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.430&preserve-view=true#get_browserversioninfo) 现在 [get_BrowserVersionString](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.488&preserve-view=true#get_browserversionstring)。
   > *  [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 现在是 [AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#addhostobjecttoscript)。
   > *  [RemoveRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#removeremoteobject) 现在是 [RemoveHostObjectFromScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#removehostobjectfromscript)。
   > *  `chrome.webview.remoteObjects` 是现在 `chrome.webview.hostObjects`。

*  > [!IMPORTANT]
   > **中断性变更**： `AddRemoteObject` JS 代理方法也会重命名。
   >
   > *  `getLocal` 是现在 `getLocalProperty`。
   > *  `setLocal` 是现在 `setLocalProperty`。
   > *  `getRemote` 是现在 `getHostProperty`。
   > *  `setRemote` 是现在 `setHostProperty`。
   > *  `applyRemote` 是现在 `applyHostFunction`。

*  > [!IMPORTANT]
   > **中断性变更**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) 并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithoptions)。

*  添加 [了 FrameNavigationCompleted](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_framenavigationcompleted) 事件。  现在，当元素完成导航时 `iframe` ，将运行事件并返回导航和导航 ID 的成功。
*  添加 [了 ICoreWebView2EnvironmentOptions](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.488&preserve-view=true) 接口，可用于确定应用目标的 Evergreen WebView2 运行时版本。
*  添加 [了 IsBuiltInErrorPageEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_isbuiltinerrorpageenabled) 设置。  现在，可以选择打开或关闭内置错误网页，以实现导航失败和呈现进程失败。
*  更新了远程对象注入以支持 .NET `IDispatch` 实现 ([#113](https://github.com/MicrosoftEdge/WebViewFeedback/issues/113)) 。
*  更新了 [NewWindowRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_newwindowrequested) 事件以处理来自上下文菜单 ([#108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/108)) 的请求。
*  发布了第一个单独的 WebView2 预发行包，可在其中访问可视托管 API。  WebView2 团队更新了 [APISample](https://github.com/MicrosoftEdge/WebView2Samples) 以包含新的实验性 API。
   *  添加了 [ICoreWebView2ExperimentalCompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller?view=webview2-0.9.488-prerelease&preserve-view=true) 接口，用于连接到合成树并为 WebView2 控件提供输入。
   *  添加了 [ICoreWebView2ExperimentalPointerInfo](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalpointerinfo?view=webview2-0.9.488-prerelease&preserve-view=true)，其中包含来自 a `POINTER_INFO`. 的所有信息。  此对象将传递给 SendPointerInput，以将指针输入注入 WebView2。
   *  添加了 [ICoreWebView2ExperimentalCursorChangedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcursorchangedeventhandler?view=webview2-0.9.488-prerelease&preserve-view=true)，告知应用何时应更改 WebView2 控件上的鼠标光标。  当鼠标位于 WebView2 中的文本框上时，光标会从箭头更改为选择器。  该 `cursor` 属性告知 `CompositionController` 应用 WebView2 的鼠标光标当前应是什么。


<!-- ====================================================================== -->
## <a name="09430"></a>0.9.430

[NuGet WebView2 SDK 0.9.430 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.430)

此版本的 WebView2 SDK 需要Microsoft Edge版本 82.0.430.0 或更高版本。

WebView2 SDK 是官方 Win32 C++ Beta 版本，它包含来自反馈的多个功能请求。  WebView2 团队尝试限制具有重大更改的版本数。  随着正式发布的临近，Beta 版本中合并了一些重大的重大更改。

*  > [!IMPORTANT]
   > **中断性变更**：随着最终版本的临近，WebView2 团队将前缀`IWebView2WebView`重命名为`ICoreWebView2`，以确保 WebView2 API 与Windows API 命名约定保持一致。  此外，为了利用 UI 框架中的 WebView2 SDK，WebView2 团队分为 `ICoreWebView2` [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true) 和 [ICoreWebView2Host](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true)。  `ICoreWebView2Host` 支持调整大小、显示和隐藏、聚焦以及与窗口和组合相关的其他功能。  ICoreWebView2 支持所有其他 WebView2 功能。  若要了解有关合并更改的详细信息，请参阅 WebView2 [APISample](https://github.com/MicrosoftEdge/WebView2Samples) 项目中的 WebView2 [拉取请求](https://github.com/MicrosoftEdge/WebView2Samples/pull/17)。

*  > [!IMPORTANT]
   > **重大更改**：将 [DocumentStateChanged](/microsoft-edge/webview2/reference/win32/iwebview2webview?view=webview2-0.8.355&preserve-view=true#add_documentstatechanged) 拆分为三个组件：  [SourceChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_sourcechanged)、 [ContentLoading](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_contentloading) 和 [HistoryChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_historychanged)。  现在，当源 URL 更改时， `SourceChanged` 将运行该事件。  更改历史记录状态时， `HistoryChanged` 将运行该事件。  加 `ContentLoading` 载新文档时，事件在初始脚本之前运行。

*  添加了对 ARM64 体系结构的支持。
*  添加了软输入面板 (SIP) 对触摸屏设备的支持。
*  添加了对 Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 和 Windows Server 2016 的支持。
*  为状态栏添加 [了 NotifyParentWindowPositionChanged](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#notifyparentwindowpositionchanged) ，以便在窗口模式下遵循窗口。  此外，请在无窗口模式下实现更改，以便辅助功能正常工作。
*  添加 [了 AreRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_areremoteobjectsallowed) 设置以全局控制是否可由任何远程对象访问网页。  默认情况下处于 `AreRemoteObjectsAllowed` 打开状态，因此 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 添加的远程对象可从网页访问。  关闭后 `AreRemoteObjectsAllowed` ，无法从网页访问对象。  更改将应用于下一个导航事件。
*  添加了 [IsZoomControlEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_iszoomcontrolenabled) 设置，以防止用户使用`ctrl`+`+`和+`ctrl``-` (或 `ctrl`+ 鼠标滚轮) 影响 WebView2 控件的缩放。  关闭设置时，仍可使用 [put_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#put_zoomfactor) 设置缩放。
*  将 ZoomFactor 更改为仅应用于当前 WebView2 控件。  缩放对当前 WebView2 控件所做的更改不会影响你使用同一源站点导航到的其他 WebView。  请参阅 [get_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#get_zoomfactor)。
*  Hid ZoomView UI for WebView2 control ([#95](https://github.com/MicrosoftEdge/WebViewFeedback/issues/95)) .
*  添加 [了 SetBoundsAndZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#setboundsandzoomfactor)。  现在，可以同时设置 WebView2 控件的缩放因子和边界。
*  添加 [了 WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) 事件。  请参阅 [add_WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) ([#119](https://github.com/MicrosoftEdge/WebViewFeedback/issues/119)) 。
*  添加了 `beforeunload` 对 JavaScript 对话框事件的对话类型的支持，并添加 [了CORE_WEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#core_webview2_script_dialog_kind) 枚举条目。
*  将 [GetHeaders](/microsoft-edge/webview2/reference/win32/icorewebview2httprequestheaders?view=webview2-0.9.430&preserve-view=true#getheaders) 添加到 HttpRequestHeaders、 [GetHeader](/microsoft-edge/webview2/reference/win32/icorewebview2httpresponseheaders?view=webview2-0.9.430&preserve-view=true#getheader) 到 HttpResponseHeaders，并将 [get_HasCurrentHeader](/microsoft-edge/webview2/reference/win32/icorewebview2httpheaderscollectioniterator?view=webview2-0.9.430&preserve-view=true#get_hascurrentheader) 属性添加到 HttpHeadersCollectionIterator。
*  > [!IMPORTANT]
   > **中断性变更**：修改 `DevToolsProtocolEventReceived` 的行为。  现在，可以为特定[的 DevTools 协议事件创建 DevToolsProtocolEventReceiver](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true)，并使用[add_DevToolsProtocolEventReceived remove_DevToolsProtocolEventReceived](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#add_devtoolsprotocoleventreceived)/订阅/取消订阅此类事件。[](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#remove_devtoolsprotocoleventreceived)

*  > [!IMPORTANT]
   > **中断性变更**：[将get_WebMessageAsString](/microsoft-edge/webview2/reference/win32/iwebview2webmessagereceivedeventargs?view=webview2-0.8.355&preserve-view=true#get_webmessageasstring)属性更改`WebMessageReceivedEventArgs`为 [TryGetWebMessageAsString](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventargs?view=webview2-0.9.430&preserve-view=true#trygetwebmessageasstring) 方法。

*  > [!IMPORTANT]
   > **中断性变更**：将 [Handle](/microsoft-edge/webview2/reference/win32/iwebview2acceleratorkeypressedeventargs?view=webview2-0.8.355&preserve-view=true#handle) 方法更改`AcceleratorKeyPressedEventArgs`为[get_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2acceleratorkeypressedeventargs?view=webview2-0.9.430&preserve-view=true#get_handled)属性。


<!-- ====================================================================== -->
## <a name="08355"></a>0.8.355

[NuGet WebView2 SDK 0.8.355 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.355)

此版本的 WebView2 SDK 需要Microsoft Edge版本 80.0.355.0 或更高版本。

*  发布了 WebView2API 示例，这是 WebView2 SDK 的综合指南。  请参阅 [API 示例](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample)。
*  添加了对除英语 ([#30](https://github.com/MicrosoftEdge/WebViewFeedback/issues/30)) 之外的所有语言的 IME 支持。
*  更新了事件的 `WebResourceRequested` API 图面以响应 bug 报告。  同时指定筛选器和创建时的事件现已弃用。  若要创建 Web 资源请求的事件，请使用 [add_WebResourceRequested](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#add_webresourcerequested) 添加事件， [并使用 AddWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#addwebresourcerequestedfilter) 添加筛选器。  [RemoveWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#removewebresourcerequestedfilter) 删除筛选器 ([#36](https://github.com/MicrosoftEdge/WebViewFeedback/issues/36))  ([#74](https://github.com/MicrosoftEdge/WebViewFeedback/issues/74)) 。
*  > [!IMPORTANT]
   > **中断性变更**：修改了全屏行为。  已弃用 [的 IsFullScreenAllowed](/microsoft-edge/webview2/reference/win32/iwebview2settings?view=webview2-0.8.355&preserve-view=true#get_isfullscreenallowed_deprecated)。  现在，默认情况下，如果 WebView2 控件中的元素 (（例如视频) ）设置为全屏，则它将填充 WebView2 控件的边界。  使用 [ContainsFullScreenElementChanged](/microsoft-edge/webview2/reference/win32/iwebview2containsfullscreenelementchangedeventhandler?view=webview2-0.8.355&preserve-view=true) 事件和 [get_ContainsFullScreenElement](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#get_containsfullscreenelement) 指定如果元素想要进入全屏模式，应用应如何调整 WebView2 控件的大小。


<!-- ====================================================================== -->
## <a name="08314"></a>0.8.314

[NuGet WebView2 SDK 0.8.314 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.314)

此版本的 WebView2 SDK 需要Microsoft Edge版本 80.0.314.0 或更高版本。

### <a name="changes"></a>更改

*  添加了对 Windows 7、Windows 8 和Windows 8.1的支持。
*  添加了对 WebView2 的Visual Studio和Visual Studio Code调试支持。  现在，直接从 IDE 在 WebView2 中调试脚本。  请参阅 [如何在使用 WebView2 控件进行开发时进行调试](how-to/debug.md)。
*  添加 `Native Object Injection` 了 WebView2 中正在运行的脚本，用于从应用的 Win32 组件访问 IDispatch 对象并访问 IDispatch 对象的属性。  请参阅 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#addremoteobject) ([#17](https://github.com/MicrosoftEdge/WebViewFeedback/issues/17)) 。
*  添加 `AcceleratorKeyPressed` 了事件。  请参阅 [add_AcceleratorKeyPressed](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#add_acceleratorkeypressed) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  关闭 .`Context Menus`  请参阅 [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/iwebview2settings2?view=webview2-0.8.355&preserve-view=true#put_aredefaultcontextmenusenabled) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  已更新 `DPI Awareness`。  现在，WebView2 控件的 DPI 感知与主机应用的 DPI 感知相同。

   > [!NOTE]
   > 如果使用与原始 WebView2 控件实例不同的 DPI 感知启动另一个混合应用，则如果 `user data folder` 与原始 WebView2 控件实例相同，则不会启动新的 WebView2 控件实例 ([#1](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1)) 。

*  更新 `Notification Change Behavior` 后，WebView2 会自动拒绝 WebView2 控件中托管的 Web 内容提示的通知权限请求。


<!-- ====================================================================== -->
## <a name="08270"></a>0.8.270

[NuGet WebView2 SDK 0.8.270 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.270)

此版本的 WebView2 SDK 需要Microsoft Edge版本 78.0.270.0 或更高版本。

### <a name="changes"></a>更改

*  添加 `DocumentTitleChanged` 了指示文档标题更改 ([问题 #27](https://github.com/MicrosoftEdge/WebViewFeedback/issues/27)) 的事件。

*  添加 `GetWebView2BrowserVersionInfo` 了 API ([问题 #18](https://github.com/MicrosoftEdge/WebViewFeedback/issues/18)) 。

*  添加 `NewWindowRequested` 了事件。

*  更新了 `CreateWebView2EnvironmentWithDetails` 要删除 `releaseChannelPreference`的函数。  有关函数的 `CreateWebView2EnvironmentWithDetails` 详细信息，请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  仍然支持注册表和环境变量替代。  除非重写，否则将使用默认通道首选项。

   在频道搜索期间，WebView2 团队将跳过与 WebView2 SDK 不兼容的任何以前的频道版本。

   WebView2 团队选择更稳定的通道，以确保最终用户的行为最一致。  使用最新的 Canary 生成进行测试时，应创建一个脚本，将环境变量设置 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE` 为 `1` 启动应用之前。  请参阅 [测试即将推出的 API 和功能](how-to/set-preview-channel.md)。

*  使用逻辑更新了 `CreateWebView2EnvironmentWithDetails` 函数，以便在未指定时进行选择 `userDataFolder` 。  有关函数的 `CreateWebView2EnvironmentWithDetails` 详细信息，请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  如果以前使用过默认 `userDataFolder` 位置，则切换到新 SDK 时，默认 `userDataFolder` 值将重置 (设置为主机代码目录中的新位置) 并且状态也会重置。  如果主机进程没有写入指定目录的权限，则该 `CreateWebView2EnvironmentWithDetails` 函数可能会失败。  可以将数据从旧 `user data folder` 目录复制到新目录。


<!-- ====================================================================== -->
## <a name="08230"></a>0.8.230

[NuGet WebView2 SDK 0.8.230 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.230)

此版本的 WebView2 SDK 需要Microsoft Edge版本 77.0.230.0 或更高版本。

### <a name="changes"></a>更改

*  添加 `Stop` 了 API，用于停止所有导航和挂起的资源提取 ([问题 #28](https://github.com/MicrosoftEdge/WebViewFeedback/issues/28)) 。
*  将文件添加`.tlb`到NuGet包 ([问题 #22](https://github.com/MicrosoftEdge/WebViewFeedback/issues/22)) 。
*  将 .NET 项目添加到NuGet包中的安装程序列表 ([问题 #32](https://github.com/MicrosoftEdge/WebViewFeedback/issues/32)) 。


<!-- ====================================================================== -->
## <a name="08190"></a>0.8.190

[NuGet WebView2 SDK 0.8.190 的包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.190)

此版本的 WebView2 SDK 需要Microsoft Edge版本 77.0.190.0 或更高版本。

*  添加 `get_AreDevToolsEnabled`/`put_AreDevToolsEnabled` 以控制用户是否可以打开 DevTools ([问题 #16](https://github.com/MicrosoftEdge/WebViewFeedback/issues/16)) 。
*  添加 `get_IsStatusBarEnabled`/`put_IsStatusBarEnabled` 到控制状态栏是否显示 ([问题 #19](https://github.com/MicrosoftEdge/WebViewFeedback/issues/19)) 。
*  添加`get_CanGoBack``get_CanGoForward``GoForward`/`GoBack`//了用于在导航历史记录中进行后退和向前操作的功能。
*  添加了 HTTP 标头类型 (`IWebView2HttpHeadersCollectionIterator`//`IWebView2HttpRequestHeaders``IWebView2HttpRequestHeaders`) 用于在 WebView2 中查看和修改 HTTP 标头。
*  在 64 位计算机上添加了 32 位 WebView2 支持 ([问题 #13](https://github.com/MicrosoftEdge/WebViewFeedback/issues/13)) 。
*  向 SDK ([问题 #14](https://github.com/MicrosoftEdge/WebViewFeedback/issues/14)) 添加了 WebView2 IDL。
*  添加了 lib 以支持 `IID\_\*` ([问题 #12](https://github.com/MicrosoftEdge/WebViewFeedback/issues/12)) 的接口 ID 对象。
*  添加了将 DLL 文件的路径、链接和自动复制到 SDK 中NuGet`TARGET`文件。
*  在脚本中打开请求 `window.open()` 。


<!-- ====================================================================== -->
## <a name="08149"></a>0.8.149

[webView2 SDK 0.8.149 的NuGet包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.149)

此版本的 WebView2 SDK 需要Microsoft Edge版本 76.0.149.0 或更高版本。

初始开发人员预览版。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [联系 Microsoft Edge WebView2 团队](contact.md)
