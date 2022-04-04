---
title: WebView2 SDK 发行说明
description: 适用于 Win32 Microsoft Edge WPF 和 WinForms 的 WebView2 发行说明。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 03/14/2022
ms.openlocfilehash: b386e204217d94a4a9bc487dfa9d5fcc69e7b3bd
ms.sourcegitcommit: ff4eb05a7d6726c9c58746c225f80d85e496478e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2022
ms.locfileid: "12468429"
---
# <a name="release-notes-for-the-webview2-sdk"></a>WebView2 SDK 发行说明

WebView2 团队将每四周更新一次 [WebView2 SDK](https://www.nuget.org/packages/Microsoft.Web.WebView2) 。  本文包含有关产品公告、添加、修改和 API 的变更的最新信息。

WebView2 Bug 修复（如下面列出的修复程序）特定于运行时或特定于 SDK。


<!-- ====================================================================== -->
## <a name="recommended-browser-channel-and-runtime"></a>推荐的浏览器通道和运行时

确保在更新 WebView2 SDK 程序包后重新编译 webView2 NuGet应用。  WebView2 团队建议执行以下操作：

*  在使用 WebView2 SDK Microsoft Edge的预发布版本进行开发时，请使用 Canary 预览频道。  Canary 是推荐的预览频道，因为它以最快节奏提供，并且具有最新的 API。

*  使用 WebView2 SDK 程序包的发布版本时，请使用 Evergreen WebView2 运行时。

有关详细信息，请参阅 [将运行时版本与 SDK 版本匹配](concepts/versioning.md#matching-the-runtime-version-with-the-sdk-version)。


<!-- ====================================================================== -->
## <a name="minimum-version-of-the-browser-or-runtime-to-load-webview2"></a>要加载 WebView2 的浏览器或运行时的最低版本

若要加载 WebView2，Microsoft Edge WebView2 运行时的最低版本是 86.0.616.0。  加载 WebView2 的最低版本仅在 Web 平台发生重大变化时更改。

若要将预发行 SDK 与 Microsoft Edge一起使用，请参阅测试即将推出的 [API 和功能](how-to/set-preview-channel.md)。


<!-- ====================================================================== -->
## <a name="10115038"></a>1.0.1150.38
  
发布日期：2022 年 3 月 10 日  
  
[NuGet WebView2 SDK 1.0.1150.38 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1150.38)  
  
为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 99.0.1150.38 或更高版本。  

### <a name="general"></a>概要

#### <a name="promotions"></a>促销
  
以下项目现已稳定：

*   使开发人员能够处理基本 HTTP 身份验证请求和响应的 [BasicAuthentication API](/microsoft-edge/webview2/reference/win32/icorewebview2_10?view=webview2-1.0.1150.38&preserve-view=true) 。
  

<!-- ====================================================================== -->
## <a name="101189-prerelease"></a>1.0.1189-prerelease
  
发布日期：2022 年 3 月 10 日  

[NuGet WebView2 SDK 1.0.1189 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1189-prerelease)  
  
为了完全实现 API 兼容性，此版本的 WebView2 SDK Microsoft Edge版本 100.0.1189.0 或更高版本。  

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验性功能
  
*   添加了 [ContextMenuRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true) 以允许主机应用创建或修改其自己的上下文菜单。


#### <a name="promotions"></a>促销
  
  
在此预发布 SDK 中，以下 API 已提升为稳定：  

*    支持 CDP 方法调用的 sessionId 的 [CallDevToolsProtocolMethodForSession API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true#calldevtoolsprotocolmethodforsession) 。
*   [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1189-prerelease&preserve-view=true)：
    *  `add_StatusBarTextChanged`
    *  `get_StatusBarText`
    *  `remove_StatusBarTextChanged`
*   支持 [启用/禁用外部拖放的 AllowExternalDrop API](/microsoft-edge/webview2/reference/win32/icorewebview2controller4?view=webview2-1.0.1189-prerelease&preserve-view=true) 。
*    [HiddenPdfToolbarItems API](/microsoft-edge/webview2/reference/win32/icorewebview2settings7?view=webview2-1.0.1189-prerelease&preserve-view=true) 可用于自定义 PDF 工具栏项。
*  [ExclusiveUserDataFolderAccess API](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2?view=webview2-1.0.1189-prerelease&preserve-view=true) 允许控制其他进程是否可以使用相同的用户数据文件夹创建 WebView2。

#### <a name="bug-fixes"></a>Bug 修复
  
*   修复了 WebView2 应用偶尔与 UWP 卡在一起的问题。
*   修复了关闭窗口模式的"查找"栏后不会 **向** 应用程序返回焦点的问题。  
*   修复了在单 `DocumentTitleChanged` 页应用中未针对向后/向前导航引发事件的错误。  
*   修复了未针对 `HistoryChanged` Iframe 导航引发事件的错误。  

## <a name="10110844"></a>1.0.1108.44

发布日期：2022 年 2 月 6 日

[NuGet WebView2 SDK 1.0.1108.44 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1108.44)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 98.0.1108.44 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项目现已稳定：

*  使开发人员能够提供其他允许的框架上级的 [AdditionalAllowedFrameAncestors API](/microsoft-edge/webview2/reference/win32/icorewebview2navigationstartingeventargs2?view=webview2-1.0.1108.44&preserve-view=true) 。
*  [ProcessInfo API](/microsoft-edge/webview2/reference/win32/icorewebview2processinfo?view=webview2-1.0.1108.44&preserve-view=true) 提供有关 WebView2 进程和进程集合详细信息。
*  适用于 [iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame2?view=webview2-1.0.1108.44&preserve-view=true&preserve-view=true)：
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

[NuGet WebView2 SDK 1.0.1158 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1158-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK Microsoft Edge版本 100.0.1158.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验性功能

*  添加了 [状态栏 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental13?view=webview2-1.0.1158-prerelease&preserve-view=true) ，以在 webiew 显示状态消息、URL 或空字符串时提供相关信息。
*  添加了 [CDP API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental14?view=webview2-1.0.1158-prerelease&preserve-view=true) ，为开发人员提供了在 WebView 中 `DevToolsProtocol` 具有多个目标的可能性。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 已提升为稳定：

*  将 ICoreWebView2ClientCertificate 重命名为 [ICoreWebView2Certificate](/microsoft-edge/webview2/reference/win32/icorewebview2certificate?view=webview2-1.0.1158-prerelease&preserve-view=true)。
*  适用于 [iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame3?view=webview2-1.0.1158-prerelease&preserve-view=true)：
   *  `add_PermissionRequested`
   *  `remove_PermissionRequested`

#### <a name="bug-fixes"></a>Bug 修复

*  修复了导致"错误列表"窗口中Visual Studio错误警告的问题。   ([问题 #1722](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1722)) 
*  修复了打开 PDF 下载时未引发 NewWindowRequested 的问题。
*  解决了 WinUI3 中不会显示选择下拉列表的 Bug。   ([问题 #1693](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1693)) 
*  添加了切换 WebView2 静音状态（即使没有播放音频）的能力。


<!-- ====================================================================== -->
## <a name="10107254"></a>1.0.1072.54

发布日期：2022 年 1 月 13 日

[NuGet WebView2 SDK 1.0.1072.54 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1072.54)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 97.0.1072.54 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项目现已稳定：

*  使 [开发人员](/microsoft-edge/webview2/reference/win32/icorewebview2_8?view=webview2-1.0.1072.54&preserve-view=true#summary) 能够将 WebView2 中的媒体静音/取消静音的媒体 API。
*  下载 [定位和定位 API 支持](/microsoft-edge/webview2/reference/win32/icorewebview2_9?view=webview2-1.0.1072.54&preserve-view=true) ：
   *  更改下载对话框相对于 WebView2 边界的位置。  您可以将下载对话框定位到"下载"**** 按钮，而不是位于右上角的默认位置。
   *  以编程方式打开和关闭默认下载对话框。
   *  对打开和关闭对话框做出响应进行更改。


<!-- ====================================================================== -->
## <a name="101133-prerelease"></a>1.0.1133-prerelease

发布日期：2022 年 1 月 13 日

[NuGet WebView2 SDK 1.0.1133-prerelease 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1133-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK Microsoft Edge版本 99.0.1133.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验性功能

*  添加了 [对 WebView2](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile2?view=webview2-1.0.1133-prerelease&preserve-view=true) (、浅色、深色、系统) 设置的支持。
*  添加了设置默认 [下载路径的方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile3?view=webview2-1.0.1133-prerelease&preserve-view=true)。
*  添加了对清除 [浏览器数据的支持](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4?view=webview2-1.0.1133-prerelease&preserve-view=true)。
*  添加了 [请求对](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe3?view=webview2-1.0.1133-prerelease&preserve-view=true) iframe 的权限支持。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 已提升为稳定：

*  适用于 [iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1133-prerelease&preserve-view=true)：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`
*  ProcessInfo API 提供有关 WebView2 进程 [和进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1133-prerelease&preserve-view=true) 集合 [详细信息](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1133-prerelease&preserve-view=true)。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1133-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了阻止标头 `Set-Cookies` 在事件内显示的错误 `WebResourceResponseReceived` 。
*  解决了弹出窗口和所拥有的窗口在关闭前跳转到不同位置而不是与应用窗口一起关闭的 Bug。 此 Bug 仅在非常短的时间时段内处于活动状态。
*  修复了关闭文件选取器对话框后的焦点问题。
*  修复了页面 UI 可见性没有随 WebView2 可见性而更改的 Bug。
*  修复了无法找到 `GetAvailableBrowserVersionString()` / `WebView2Loader.dll`加载的错误。  ([问题 #1236](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1236)) 
*  修复了在未处理事件时 `window.open` 创建的新 `NewWindowRequested` 窗口的大小和位置。  ([问题 #1343](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1343)) 
*  修复了在禁用上下文菜单时，迷你菜单仍显示在所选文本上的 Bug。 此更改特定于运行时。  ([问题 #1345](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1345)) 
*  修复了在 WinForms 中切换应用后焦点返回到错误位置的错误。


<!-- ====================================================================== -->
## <a name="101083-prerelease"></a>1.0.1083-prerelease

发布日期：2021 年 11 月 29 日

[NuGet WebView2 SDK 1.0.1083 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1083-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK Microsoft Edge版本 97.0.1083.0 或更高版本。

### <a name="experimental-features"></a>实验功能

* 在 WebView2 [中添加了以下适用于 iframe](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1083-prerelease&preserve-view=true) 的 API：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`

* 添加了 ProcessInfo API 以提供有关 WebView2 进程 [和进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1083-prerelease&preserve-view=true) 集合 [详细信息](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1083-prerelease&preserve-view=true)。

### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 已提升为稳定：

*  使 [开发人员](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1083-prerelease&preserve-view=true#summary) 能够将 WebView2 中的媒体静音/取消静音的媒体 API。
*  下载 [定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1083-prerelease&preserve-view=true)。  此 API 支持：
   *  更改下载对话框相对于 WebView2 边界的位置。  您可以将下载对话框定位到"下载"**** 按钮，而不是位于右上角的默认位置。
   *  以编程方式打开和关闭默认下载对话框。
   *  对打开和关闭对话框做出响应进行更改。

### <a name="bug-fixes"></a>Bug 修复

*  修复了关闭文件选取器对话框后的焦点问题。
*  修复了 WebView2 在初始启动时不接收空间输入的 bug。
*  修复了阻止在 WebView2 中单一登录的问题。
*  解决了下载对话框未随 WPF 和 WinForms 上的窗口一起移动的 Bug。
*  更新了兼容的命令行检查，以防止需要检查可选开关的版本。
*  修复了导致"Microsoft Edge"品牌显示在辅助功能树中的错误。


<!-- ====================================================================== -->
## <a name="10105431"></a>1.0.1054.31

发布日期：2021 年 11 月 29 日

[NuGet WebView2 SDK 1.0.1054.31 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1054.31)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 96.0.1054.31 或更高版本。

### <a name="general"></a>概要

*  常规可靠性修补程序。

### <a name="bug-fixes"></a>Bug 修复

*  为 v96 WebView2 运行时关闭控制流强制执行技术 (CET) 卷影堆栈功能。
*  修复了在 .NET 单文件应用程序中启动时导致启动时间变慢的问题。  ([问题 #1909](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1909)) 
*  修复了浏览器策略Microsoft Edge错误应用于 WebView2 导致的崩溃。  ([问题 #1860](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1860)) 
*  修复了关闭包含下载对话框的弹出窗口时发生的崩溃。  ([问题 #1765](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1765)) & ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 


<!-- ====================================================================== -->
## <a name="101056-prerelease"></a>1.0.1056-prerelease

发布日期：2021 年 10 月 29 日

[NuGet WebView2 SDK 1.0.1056 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1056-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK Microsoft Edge版本 97.0.1056.0 或更高版本。

### <a name="general"></a>概要

*  常规可靠性改进。

#### <a name="experimental-features"></a>实验功能

*  下载 [定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1056-prerelease&preserve-view=true)。  此 API 支持：
   *  更改下载对话框相对于 WebView2 边界的位置。  您可以将下载对话框定位到"下载"**** 按钮，而不是位于右上角的默认位置。
   *  以编程方式打开和关闭默认下载对话框。
   *  对打开和关闭对话框做出响应进行更改。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1056-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  针对进程失败，现在`ExitCode``ICoreWebView2ProcessFailedEventArgs2`提供了实际进程退出`COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED`代码。
*  现在`--js-flags`，开关在 中`AdditionalBrowserArguments`提供。`CoreWebView2EnvironmentOptions`
*  修复了对 `name` JavaScript 中主机对象的 属性的访问。  ([问题 641](https://github.com/MicrosoftEdge/WebView2Feedback/issues/641)) 
*  修复了 `InvalidCastException` 在事件循环启动之前隐式初始化 WPF 控件中的 。  ([问题 #1577](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1577)) 


<!-- ====================================================================== -->
## <a name="10102030"></a>1.0.1020.30

发布日期：2021 年 10 月 25 日

[NuGet WebView2 SDK 1.0.1020.30 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1020.30)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 95.0.1020.30 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  进行了 `EnsureCoreWebView2Async` 更新，在设置 WPF 源属性时不会引发异常。  ([问题 #1781](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1781)) 
*  修复了与显示下载 UI 的多个窗口交互后 WebView2 崩溃的问题。  ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 

#### <a name="promotions"></a>促销

以下项目现已稳定：
*  [PrintToPdf API](/microsoft-edge/webview2/reference/win32/icorewebview2_7?view=webview2-1.0.1020.30&preserve-view=true#printtopdf)。

<!-- ====================================================================== -->
## <a name="1099228"></a>1.0.992.28

发布日期：2021 年 9 月 27 日

[NuGet WebView2 SDK 1.0.992.28 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.992.28)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 94.0.992.31 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了缺少的 WebView2 (`PlatformTarget` 未在用户的 .NET 项目中) 导致初始化失败。  ([问题 #1061](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1061)) 

#### <a name="promotions"></a>促销

以下项目现已稳定：
*  [OpenTaskManagerWindow API](/microsoft-edge/webview2/reference/win32/icorewebview2_6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [isSwipeNavigationEnabled 属性](/microsoft-edge/webview2/reference/win32/icorewebview2settings6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [BrowserProcessExited API](/microsoft-edge/webview2/reference/win32/icorewebview2browserprocessexitedeventargs?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [get_Name接口上的](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs2?view=webview2-1.0.992.28#get_name&preserve-view=true#summary) 属性 `ICoreWebView2NewWindowRequestedEventArgs2` 。


<!-- ====================================================================== -->
## <a name="101018-prerelease"></a>1.0.1018-prerelease

发布日期：2021 年 9 月 20 日

[NuGet WebView2 SDK 1.0.1018 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1018-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 95.0.1018.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [媒体 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1018-prerelease&preserve-view=true#summary) ，使开发人员能够将 WebView2 中的媒体静音/取消静音。
*  添加了对使用 WebView2 [的多个](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment8?view=webview2-1.0.1018-prerelease&preserve-view=true) 用户配置文件的支持。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在应用跨越监视器和监视器缩放更改时 WebView2 停止呈现的问题。
*  修复了在多个下载窗口打开时关闭下载 UI 崩溃 WebView2 的问题。  ([问题 #1723](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1723)) 
*  修复了在用户的 .NET 项目中未设置 PlatformTarget 时生成/初始化错误。  ([问题 730](https://github.com/MicrosoftEdge/WebViewFeedback/issues/730) 和[问题 #1548) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1548)


<!-- ====================================================================== -->
## <a name="101010-prerelease"></a>1.0.1010-prerelease

发布日期：2021 年 9 月 14 日

[NuGet WebView2 SDK 1.0.1010 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1010-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 95.0.1010.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  可靠性修补程序。  ([问题 #1605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1605) 和 [问题 #1678](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1678)) 
*  在启动期间和主机应用位于前台时添加了性能改进。

#### <a name="experimental-features"></a>实验功能

*  使用 删除无提示失败 `EnsureCoreWebView2Async`，当 `ArgumentException` 调用时，将引发 具有不兼容参数的多个错误。
*  更改了环境 [对象中 UserDataFolder](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment5?view=webview2-1.0.1010-prerelease&preserve-view=true#get_userdatafolder) 属性的默认处理。

   > [!CAUTION]
   > **中断更改**：如果开发人员未指定要在何处放入用户数据文件夹，则其默认处理将会更改。  请参阅 [通知：用户目录文件夹默认处理更新](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1410)。

*  为 [iframe &添加了](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.1010-prerelease&preserve-view=true) 导航和脚本 API。
*  添加了 [MemoryUsageTargetLevel](/microsoft-edge/webview2/reference/win32/icorewebview2experimental5?view=webview2-1.0.1010-prerelease&preserve-view=true) ，允许开发人员指定内存消耗级别，如低或正常。
*  向 [环境选项添加了 ExclusiveUserDataFolderAccess](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-1.0.1010-prerelease&preserve-view=true) 。
*  添加了 [HiddenPdfToolbarItems 以自定义](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.1010-prerelease&preserve-view=true) PDF 工具栏项。
*  添加了 [PrintToPdf](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprinttopdfcompletedhandler?view=webview2-1.0.1010-prerelease&preserve-view=true)，允许将当前页面打印为 PDF。 此外，还可以在此新 API 中使用可选的自定义设置。
*  添加了 [AllowExternalDrop](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.1010-prerelease&preserve-view=true) 属性以允许从 WebView2 控件外向其中拖放对象。
*  添加了 [ContextMenu API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem?view=webview2-1.0.1010-prerelease&preserve-view=true) ，允许自定义 WebView2 上下文菜单。

#### <a name="bug-fixes"></a>Bug 修复

*  改进了在 JavaScript 代码中捕获主机对象异常的方法。
*  使用 DevTools 窗口中的通用图标替换了 WebView2 图标。
*  使用时打开选项卡屏幕共享 `MediaDevices.getDisplayMedia()` 选项。  ([问题 #1566](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1566)) 
*  修复了未选择正确证书时客户端证书 API 中的 Bug。 这是运行时更改。  ([问题 #1666](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1666)) 
*  修复了在同 `window.chrome.webview` 一父域中的新窗口中不可用的错误。 此更改特定于运行时。  ([问题 #1144](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1144)) 
*  修复了下拉菜单或列表显示在具有焦点的窗口后面的 Bug。  ([问题 #411](https://github.com/MicrosoftEdge/WebViewFeedback/issues/411)) 
*  修复了使用 时的焦点问题 `put_IsVisible(false)`。  ([问题 238](https://github.com/MicrosoftEdge/WebViewFeedback/issues/238)) 
*  修复了应用于弹出窗口 `SetVirtualHostNameToFolderMapping` 的 Bug。
*  修复了对象返回 `IDispatch` 为 的错误 `IUnknown`。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 已提升为稳定：
*  `IsSwipeNavigationEnabled`.
*  `BrowserProcessExited`.
*  `OpenBrowserTaskManager`.


<!-- ====================================================================== -->
## <a name="1096133"></a>1.0.961.33

发布日期：2021 年 9 月 8 日

[NuGet WebView2 SDK 1.0.961.33 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.961.33)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 93.0.961.44 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了导致错误的 `ERR_SSL_CLIENT_AUTH_CERT_NEEDED` Bug。 这是运行时更改。
*  修复了无法通过使用 关闭**刷新**、主页、后退**** 等特殊**** 浏览器键的问题`AreBrowserAcceleratorKeysEnabled`。 此更改特定于运行时。
*  修复了未呈现透明背景色的 Bug。
*  修复了在加载 WebView2 时导致白闪烁的 Bug。
*  修复了 WebView2 .NET 控件中的一个 bug，即在后台创建 WebView2 窗口时，这些窗口为空。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 
*  修复了用户导航到新窗口或显示页面时未更新设置的问题 `about:blank` 。 这是运行时更改。

#### <a name="promotions"></a>促销

以下项目现已稳定：
*  [客户端证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.961.33&preserve-view=true#add_clientcertificaterequested)。


<!-- ====================================================================== -->
## <a name="10955-prerelease"></a>1.0.955-prerelease

发布日期：2021 年 7 月 26 日

[NuGet WebView2 SDK 1.0.955-prerelease 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.955-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 93.0.967.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  添加了部分事件跟踪Windows (ETW) 支持。
*  从 中删除了 Microsoft 品牌 `edge://history`。
*  新的默认下载 UI。

#### <a name="experimental-features"></a>实验功能

*  添加了 [OpenTaskManagerWindow](/microsoft-edge/webview2/reference/win32/icorewebview2experimental4?view=webview2-1.0.955-prerelease&preserve-view=true#opentaskmanagerwindow) 以启动 WebView2 浏览器任务管理器。
*  添加了 [NewWindowRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-1.0.955-prerelease&preserve-view=true#get_name)。
*  添加了对虚拟主机名映射的支持，以使用服务工作人员。
*  添加了 [HiddenPdfToolbarItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.955-prerelease&preserve-view=true#get_hiddenpdftoolbaritems) 以自定义 PDF 工具栏项。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了使 和 页面 `edge://downloads` 中断 `edge://history` 的 Bug。 此更改特定于运行时。
*  修复了 Bug 以提高产品WebView2Loader.dll。
*  修复了事件处理程序 `NewWindowRequested` 在处理使用 的链接时启动两个窗口的错误 `target=_blank`。
*  修复了 WebView 视觉托管中在启动前闪烁的 Bug。
*  修复了在使用 `add_WebResourceRequested` 创建的 WebView2 控件上不起作用时的错误 `add_NewWindowRequested`。  ([问题 #616](https://github.com/MicrosoftEdge/WebViewFeedback/issues/616)) 
*  允许主机应用在不同的应用程序上设置前台，以`NavigationStarting``AddHostObjectToScript`响应事件，包括 、 方法和 `WebMessageReceived``NewWindowRequested`。  ([问题 #1092](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1092)) 
*  修复了用于触发麦克风 `PermissionRequested` 事件的错误。 此更改特定于运行时。 ([问题 #1462](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1462)) 
*  修复了多次 `ExecuteScriptAsync` 成功运行后被阻止的错误。 此更改特定于运行时。  ([问题 #1348](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1348)) 
*  修复了防止 在 中使用非 ASCII 文件名 `ResultFilePath` 的错误 `DownloadStartingEventArgs`。  ([问题 #1428](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1428)) 
*  修复了默认弹出窗口上的标题栏未完全显示的问题。 此更改特定于运行时。  ([问题 1016](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1016)) 

#### <a name="promotions"></a>促销
*  [add_ClientCertificateRequested](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.955-prerelease&preserve-view=true#add_clientcertificaterequested) 已提升为稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 WebView2 .NET API 参考文档中仅导致显示第一个异常的问题。
*  .NET 核心库现在内置于发布模式。 若要调试，请确保清除" **仅我的代码"** 复选框。
*  修复了在包含子表单的表单上 WebView2 崩溃的 Bug。 在页面栏中打开查找的子窗体导致 WebView2 在关闭子窗体时崩溃。  ([问题 #1097](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1097)) 


<!-- ====================================================================== -->
## <a name="1090249"></a>1.0.902.49

发布日期：2021 年 7 月 26 日

[NuGet WebView2 SDK 1.0.902.49 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902.49)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 92.0.902.49 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了导致属性 `IsBuiltInErrorPageEnabled` 出错的 bug，它已关闭在出现导航失败或呈现进程失败时显示的错误页面。  此更改特定于运行时。  ([问题 #634](https://github.com/MicrosoftEdge/WebViewFeedback/issues/634)) 
*  修复了 WebView2 控件焦点离开用户焦点的问题。
*  修复了 `AddScriptToExecuteOnDocumentCreated` 在子窗口无法工作时的错误。  ([问题 #935](https://github.com/MicrosoftEdge/WebViewFeedback/issues/935)) 
*  修复了导致非活动选项卡被自动丢弃的 Bug。  ([问题 #637](https://github.com/MicrosoftEdge/WebViewFeedback/issues/637)) 
*  修复了导航事件被另一个导航事件中断导致事件的导航 ID `NavigationCompleted` 不正确时的错误。  ([问题 #1142](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1142)) 

#### <a name="promotions"></a>促销

以下项目现在稳定：

*  [add_FrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902.49&preserve-view=true#add_framecreated)。
*  [get_IsGeneralAutofillEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902.49&preserve-view=true#get_isgeneralautofillenabled)。
*  [get_IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902.49&preserve-view=true#get_ispinchzoomenabled)。
*  [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting)。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 支持 iFrame 元素的 API。


<!-- ====================================================================== -->
## <a name="10902-prerelease"></a>1.0.902-prerelease

发布日期：2021 年 6 月 1 日

[NuGet WebView2 SDK 1.0.902 预发布包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 92.0.902.0 或更高版本。

### <a name="general"></a>概要

*  改进了 WebView2 启动性能和磁盘占用。

#### <a name="experimental-features"></a>实验功能

*  添加了 [IsSwipeNavigationEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_isswipenavigationenabled) 属性以启用或禁用最终用户在启用了触控输入的设备上使用轻扫手势在 WebView2 中导航的能力。
*  添加了 [BrowserProcessExited](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment4?view=webview2-1.0.902-prerelease&preserve-view=true#add_browserprocessexited) 事件。
*  添加了 [add_ClientCertificateRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental3?view=webview2-1.0.902-prerelease&preserve-view=true#add_clientcertificaterequested)。 它允许显示客户端证书对话框提示（如果需要）并允许访问所需的元数据以替换默认客户端证书对话框提示。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了鼠标左键单击不消除上下文菜单的问题。 此更改特定于运行时。
*  修复了当共享相同用户数据文件夹的应用的 exe 文件具有不一致的版本信息时 WebView2 创建失败的错误。
*  修复了诸如 `Refresh``Home``Back` 、和 等特殊浏览器密钥无法被 禁用的 Bug。`AreBrowserAcceleratorKeysEnabled` 此更改特定于运行时。
*  修复了 WebView2 .NET 控件中的 Bug，其中 WebView2 窗口在后台创建时为空。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 。
*  通过按 WebView 控件`Enter``Esc`使 WPF 应用程序崩溃或不再崩溃，关闭文件选取器对话框。  ([问题 #1099](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1099)) 。
*  修复了在附加事件处理程序时 [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#get_allowsinglesignonusingosprimaryaccount) 无法正常使用 WebView2 `WebResourceRequested` 的 Bug。 此更改特定于运行时。  ([问题 #1183](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1183)) 。
*  下载文件不再会破坏 WebView2 `DefaultBackgroundColor` 的透明度。 此更改特定于运行时。  ([问题 #1108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1108)) 。
*  删除了包含 Microsoft 品牌打造的屏幕共享媒体选取器消息。  ([问题 940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 WebView2 WinForm 控件中隐藏父表单不会隐藏 WebView2 控件的 bug ([Issue #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828) and [Issue #1079](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1079)) 。
*  向 WebView2 WS_CLIPCHILDREN添加了静态样式样式。  ([问题 #1013](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1013)) 。
*  修复了右键单击链接导致 WebView2 主机应用崩溃的 Bug。 此更改特定于运行时。
*  修复了在移动到较新的 Edge WebView2 运行时版本时可能导致主机应用进程崩溃的可靠性 Bug。
*  **弃用**：正式弃用 `DefaultBackgroundColor` 7 Windows API。

#### <a name="promotions"></a>促销

*  [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting) 现已升级为稳定。
*  [现在，将 PinchZoom API](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_ispinchzoomenabled) 提升为稳定。
*  [AddFrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_framecreated) 现已提升为稳定。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 通过 iFrame 元素支持将 API 提升为稳定。
*  [自动填充 API](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902-prerelease&preserve-view=true#get_isgeneralautofillenabled) 现已提升为稳定。
   > [!NOTE]
   > 没有当前 API 可删除本地存储的常规自动填充和密码自动保存信息。  请提供用于删除数据的控件，这将涉及删除整个用户数据文件夹。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 WebView2 WinForm 控件中释放父窗口后 WebView2 窗口可见性未正确更新的 Bug。  ([问题 #1282](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1282) 和 [问题 #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828)) 。
*  修复了 WebView2 WPF 控件中的一个 Bug，即 WPF OneWay 绑定模式下的 Source 属性绑定无法正常工作。  ([问题 619](https://github.com/MicrosoftEdge/WebViewFeedback/issues/619) 和 [问题 #608](https://github.com/MicrosoftEdge/WebViewFeedback/issues/608)) 。


<!-- ====================================================================== -->
## <a name="1086435"></a>1.0.864.35

发布日期：2021 年 5 月 31 日

[NuGet WebView2 SDK 1.0.864.35 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.864.35)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 91.0.864.35 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在移动到较新的 Edge WebView2 运行时版本时可能导致主机应用进程崩溃的可靠性 Bug。
*  修复了在某些情况下阻止清除内存的 Bug。 此更改特定于运行时。
*  修复了项目找不到文件的 818 SDK 发布包中的 `WebView2.h` 错误。  ([问题 #1209](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1209)) 。
*  修复了一个缺陷，该 Bug 导致对具有二进制主体的一些请求丢弃 WebResourceRequested 事件。
*  改进 `NewWindowRequested` 文档。  ([问题 #448](https://github.com/MicrosoftEdge/WebViewFeedback/issues/448)) 。

#### <a name="promotions"></a>促销
*  [UserAgent API](/microsoft-edge/webview2/reference/win32/icorewebview2settings2?view=webview2-1.0.864.35&preserve-view=true#get_useragent) 现已稳定。
*  [AreBrowserkeysenabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings3?view=webview2-1.0.864.35&preserve-view=true#get_arebrowseracceleratorkeysenabled) 现已稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 WebView2 .NET 控件中 `CoreWebView2WebResourceRequest` 在访问标头集合时缺少第一个标头的 bug。  ([问题 #1123](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1123)) 。


<!-- ====================================================================== -->
## <a name="10865-prerelease"></a>1.0.865-prerelease

发布日期：2021 年 4 月 26 日

[NuGet WebView2 SDK 1.0.865 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.865-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 91.0.865.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings4?view=webview2-1.0.865-prerelease&preserve-view=true#ispinchzoomenabled) 设置。 它允许你在设置中打开或关闭页面缩放缩放控件。
*  添加了自定义 [add_DownloadStarting](/microsoft-edge/webview2/reference/win32/icorewebview2experimental2?view=webview2-1.0.865-prerelease&preserve-view=true#add_downloadstarting) API。  它允许你阻止下载、保存到其他路径，并访问所需的元数据以生成自定义下载 UI。
*  添加了 `iframe` [AddHostObjectToScriptWithOrigins 中的元素支持](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.865-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins)。
*  添加了 [WPF 示例应用的示例代码](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser) ，以使用 API 关闭浏览器功能键。
*  添加了 [UpdateRuntime](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment3?view=webview2-1.0.865-prerelease&preserve-view=true#updateruntime) API，以轻松更新 WebView2 运行时。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 WebView2 `Chromium DevTools Protocol` 中具有二 `POST` 进制数据的消息处理程序。
*  关闭下载 `OpenSaveAsAwareness` UI，因为它包含指向 的链接 `edge://settings`。   ([问题 #1120](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1120)) 。
*  从屏幕共享对话框中删除了品牌。   ([问题 940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 [当 SetWindowDisplayAffinity](/windows/win32/api/winuser/nf-winuser-setwindowdisplayaffinity) 函数在 WebView2 应用中停止屏幕捕获时使 WebView2 成为错误。   ([问题 #841](https://github.com/MicrosoftEdge/WebViewFeedback/issues/841)) 。
*  修复了将任何笔输入发送到 WebView2 时鼠标输入停止工作的合成托管 Bug。
*  修复了在任何笔输入后使鼠标输入中断的 Bug。  此更改特定于运行时。

### <a name="net"></a>.NET

#### <a name="experimental-features"></a>实验功能

*  向 WPF 工具箱添加了 WebView2 设计器工具。   ([问题 210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  在 .NET Designer 模式下添加了 WebView2 UI 元素。

#### <a name="bug-fixes"></a>Bug 修复

*  改进了 COM 异常描述，将每个异常包装在更详细的 .NET 异常中。   ([问题 #338](https://github.com/MicrosoftEdge/WebViewFeedback/issues/338)) 。  此更改特定于运行时。
*  修复了在选择切换焦点时`Tab`导致 WebView2 控件在 Microsoft Visual Studio Tools for Office 中崩溃Office。   ([问题 #589](https://github.com/MicrosoftEdge/WebViewFeedback/issues/589) 和 [问题 #933](https://github.com/MicrosoftEdge/WebViewFeedback/issues/933)) 。  此更改特定于运行时。
*  改进了 .NET framework 加载程序下层级别，更可靠。   ([问题 946](https://github.com/MicrosoftEdge/WebViewFeedback/issues/946)) 。
*  修复了在首次导航完成之前尝试刷新时导致崩溃的 Bug。   ([问题 #1011](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1011)) 。
*  修复了初始化，因此导航在 期间发生 `CoreWebView2InitializationCompleted`。   ([问题 #1050](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1050)) 。
*  改进了 .NET 浏览器进程崩溃错误处理。  你现在可以在处理事件后重新创建控件 `ProcessFailed` ，而不会崩溃。   ([问题 #996](https://github.com/MicrosoftEdge/WebViewFeedback/issues/996)) 。


<!-- ====================================================================== -->
## <a name="1081841"></a>1.0.818.41

发布日期：2021 年 4 月 21 日

[NuGet WebView2 SDK 1.0.818.41 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.818.41)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 90.0.818.41 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在针对非呈现器子进程和帧呈现器引发。
*  添加了 `iframe` 对 的元素支持 `AddScriptToExecuteOnDocumentCreated`。
*  改进的 WebView2 代码可以 `.exe` 更弹性地使用格式错误的版本信息处理应用程序文件。   ([问题 #850](https://github.com/MicrosoftEdge/WebViewFeedback/issues/850)) 。
*  已从 `--winhttp-proxy-resolver` WebView 浏览器进程命令行中删除，为 WebView2 打开其他代理命令行选项。


<!-- ====================================================================== -->
## <a name="10824-prerelease"></a>1.0.824-prerelease

发布日期：2021 年 3 月 8 日

[NuGet WebView2 SDK 1.0.824 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.824-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK Microsoft Edge版本 91.0.824.0 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在针对非呈现器子进程和帧呈现器引发。
*  添加了实验 [性 AreBrowserAcceleratorKeysEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings2?view=webview2-1.0.824&preserve-view=true#get_arebrowseracceleratorkeysenabled) 设置。  你可以阻止浏览器响应与导航、打印、保存和其他特定于浏览器的功能相关的键盘快捷方式。
*  添加了 `iframe` 对 的元素支持 `AddScriptToExecuteOnDocumentCreated`。

#### <a name="promotion"></a>促销

*  [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) API 现已提升为稳定。
*  [Rasterization Scale API (RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性、[RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件、[BoundsMode](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode) 属性和 [ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性) 现在提升为 Stable。

#### <a name="bug-fixes"></a>Bug 修复

*  扩展支持的 C++ 和 .NET 项目类型，如 MFC 和 ATL。   ([问题 506](https://github.com/MicrosoftEdge/WebViewFeedback/issues/506)、 [问题 #669](https://github.com/MicrosoftEdge/WebViewFeedback/issues/669) 和 [问题 #851](https://github.com/MicrosoftEdge/WebViewFeedback/issues/851)) 。
*  修复了 Evergreen WebView2 运行时泄露入站防火墙条目的 Bug。
*  修复了事件期间的响应 `WebResourceRequested` 设置。   ([问题 #568](https://github.com/MicrosoftEdge/WebViewFeedback/issues/568)) 。
*  修复了导航到导致 `edge://` 浏览器进程退出的 Bug。   ([问题 604](https://github.com/MicrosoftEdge/WebViewFeedback/issues/604)) 。
*  修复了在可视托管模式下将 WebView2 限制到屏幕大小的 Bug。


<!-- ====================================================================== -->
## <a name="1077444"></a>1.0.774.44

发布日期：2021 年 3 月 8 日

[NuGet WebView2 SDK 1.0.774.44 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.774.44)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 89.0.774.44 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  在 WebView2 中Microsoft Edge浏览器服务。
*  可视化托管 API 现已普遍可用。

#### <a name="promotions"></a>促销

*  以下实验 API 现已提升为稳定。
   *  [DPI 支持](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) 相关 API
   *  可视托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)
   *  [TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend)
   *  [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor)

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在可视托管模式下将 WebView2 限制到屏幕大小的 Bug。


<!-- ====================================================================== -->
## <a name="10790-prerelease"></a>1.0.790-prerelease

发布日期：2021 年 2 月 10 日

[NuGet WebView2 SDK 1.0.790 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.790-prerelease)

此预发布版本的 WebView2 SDK 要求Microsoft Edge版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **更改：** WebView2 预发布包 1.0.781 已弃用。  停止使用程序包 1.0.781 进行开发。

> [!IMPORTANT]
> WebView2 预发布包 0.9.430 已弃用，并且随下一版本一起删除。  如果你的 WebView 应用使用程序包，WebView2 团队建议你移动到较新的程序包。

#### <a name="features"></a>功能

*  添加了 [TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend) 方法来挂起和恢复 WebViews。
*  添加了 [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping) 方法，该方法将虚拟主机名映射到目录路径。   ([问题 37](https://github.com/MicrosoftEdge/WebViewFeedback/issues/37)、 [问题 161](https://github.com/MicrosoftEdge/WebViewFeedback/issues/161) 和 [问题 #212](https://github.com/MicrosoftEdge/WebViewFeedback/issues/212)) 。
*  添加了 [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor) 属性以设置背景的颜色和 alpha 通道。   ([问题 #414](https://github.com/MicrosoftEdge/WebViewFeedback/issues/414)) 。
*  添加了 [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings?view=webview2-1.0.790-prerelease&preserve-view=true#get_useragent) 属性以获取或设置用户代理。   ([问题 #122](https://github.com/MicrosoftEdge/WebViewFeedback/issues/122)) 。
*  将 方法 `CreateCookieWithCookie` 替换为 `CopyCookie` 方法。
*  添加了使用 [ICoreWebView2CompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller?view=webview2-1.0.790-prerelease&preserve-view=true) 接口的可视托管支持，该接口是使用 中的新方法 `CreateCoreWebView2CompositionController` 创建的 `ICoreWebView2Environment3`。

#### <a name="bug-fixes"></a>Bug 修复

*  在 WebView2 Microsoft Edge"购物"功能。
*  在 为 时关闭 PDF 查看器中的上下文 `AreDefaultContextMenusEnabled` 菜单 `false`。   ([问题 605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/605)) 。
*  修复了在查询 时 `E_NOINTERFACE` 返回的 `ICoreWebView2` Bug `ICoreWebView2Experimental`。   ([问题 691](https://github.com/MicrosoftEdge/WebViewFeedback/issues/691)) 。
*  修复了将 设置为 时允许使用格式错误的 URI `CoreWebView2NavigationStartingEventArgs.Cancel` 进行导航的 bug `false`。   ([问题 #400](https://github.com/MicrosoftEdge/WebViewFeedback/issues/400)) 。
*  修复了在弹出窗口中 `window.print()` 阻止的 Bug，并附带事件 `NewWindowRequested` 的事件处理程序。   ([问题 #409](https://github.com/MicrosoftEdge/WebViewFeedback/issues/409)) 。
*  修复了在不同监视器之间移动应用时的动态 DPI 问题。   ([问题 58](https://github.com/MicrosoftEdge/WebViewFeedback/issues/58)) 
*  改进了 [ICoreWebView2WebResourceResponseViewGetContentCompletedHandler：：Invoke 传递的实例](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponseviewgetcontentcompletedhandler?view=webview2-1.0.790-prerelease&preserve-view=true#invoke)。`HRESULT`
*  关闭自动填充管理按钮。   ([问题 #585](https://github.com/MicrosoftEdge/WebViewFeedback/issues/585)) 。
*  修复Visual Studio窗口托管时`WebView2.Dispose`运行时崩溃的问题。   ([问题 #816](https://github.com/MicrosoftEdge/WebViewFeedback/issues/816)) [和问题 #442](https://github.com/MicrosoftEdge/WebViewFeedback/issues/442)) 。
*  修复了在工具箱中显示 WebView2 Visual Studio Bug。   ([问题 210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  减少了高 CPU 使用率问题。   ([问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。
*  修复了已弃用 1.0.781-prerelease 程序包的问题。   ([问题 #875](https://github.com/MicrosoftEdge/WebViewFeedback/issues/875) 和 [问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。

#### <a name="promotions"></a>促销

*  以下实验 API 现已提升为稳定：
   *  可视托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了使用 WPF SDK 的 WebView 应用崩溃的错误。  当你选择关闭窗口时 `F4` 发生崩溃。   ([问题 #399](https://github.com/MicrosoftEdge/WebViewFeedback/issues/399)) 。
*  WebView2 初始化屏幕现在是透明的，而不是灰色的。   ([问题 #196](https://github.com/MicrosoftEdge/WebViewFeedback/issues/196)) 。


<!-- ====================================================================== -->
## <a name="1070550"></a>1.0.705.50

发布日期：2021 年 1 月 25 日

[NuGet WebView2 SDK 1.0.705.50 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.705.50)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

*  以下实验 API 现已提升为稳定：
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [WebView Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)


<!-- ====================================================================== -->
## <a name="10721-prerelease"></a>1.0.721-prerelease

发布日期：2020 年 12 月 8 日

[NuGet WebView2 SDK 1.0.721 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.721-prerelease)

此预发布版本的 WebView2 SDK 要求Microsoft Edge版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **更改：** 已弃用 WebView2 预发布包 1.0.707 和程序包 0.9.628。  停止使用程序包 1.0.707 和 package0.9.628 进行开发。

#### <a name="features"></a>功能

*  添加了 [WebView2 组策略](/deployedge/microsoft-edge-webview-policies)。  有关最佳做法，请参阅 [WebView2 的组策略](concepts/enterprise.md#group-policies-for-webview2)。
*  > [!IMPORTANT]
   > **中断更改**：弃用旧的注册表位置。
   >
   > ```text
   > {Root}\Software\Policies\Microsoft\EmbeddedBrowserWebView\LoaderOverride\{AppId}
   > ```

*  添加了对 WebView2 [中的](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.721-prerelease&preserve-view=true) 拖放功能的支持。
*  添加了 API 以处理 DPI 支持。
   *  添加了 [RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性以更改 WebView 内容和 UI 弹出窗口的 DPI 缩放以及关联的 [RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件。
   *  添加了 [ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性以根据需要 `RasterizationScale` 自动更新属性。
   *  添加了 [BoundsMode](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode) 属性以指定边界为逻辑像素并允许 WebView `RasterizationScale` 用于 WebView2 像素显示，WebView `RasterizationScale` `Bounds` 使用 和 获取物理大小。
*  更新 `NewWindowRequested` 了处理 和 `Ctrl`+`click` 的事件 `Shift`+`click`。   ([问题 #168](https://github.com/MicrosoftEdge/WebViewFeedback/issues/168) 和 [问题 #371](https://github.com/MicrosoftEdge/WebViewFeedback/issues/371)) 。
*  以下实验 API 现已提升为稳定。
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [WebView Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)

### <a name="net"></a>.NET

#### <a name="features"></a>功能

*  在 .NET Core 3.1+ 和 .NET 5 中打开 WinForms 设计器。
*  改进了 .NET Cookie 管理。   ([问题 611](https://github.com/MicrosoftEdge/WebViewFeedback/issues/611)) 。
*  替换为 `CoreWebView2Ready` [CoreWebView2InitializationCompleted](/dotnet/api/microsoft.web.webview2.core.corewebview2initializationcompletedeventargs)。

#### <a name="bug-fixes"></a>Bug 修复

*  添加了 [AcceleratorKeyPressed](/dotnet/api/microsoft.web.webview2.wpf.webview2.acceleratorkeypressed) 事件以支持 `AcceleratorKey` 在 WebView2 中选择。   ([问题 288](https://github.com/MicrosoftEdge/WebViewFeedback/issues/288)) 。
*  删除了输出到 WebView2 文件夹的不必要的文件。   ([问题 #461](https://github.com/MicrosoftEdge/WebViewFeedback/issues/461)) 。
*  改进了主机对象 API。   ([问题 335](https://github.com/MicrosoftEdge/WebViewFeedback/issues/335) 和 [问题 525](https://github.com/MicrosoftEdge/WebViewFeedback/issues/525)) 。


<!-- ====================================================================== -->
## <a name="1066437"></a>1.0.664.37

发布日期：2020 年 11 月 20 日

[NuGet WebView2 SDK 1.0.664.37 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.664.37)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：.NET WPF/WinForms WebView2 SDK 现已正式发布 (GA) 。  从此版本开始，发布 SDK 是向前兼容的。  有关更多详细信息，请参阅 [GA 公告博客文章](https://devblogs.microsoft.com/dotnet/announcing-general-availability-for-microsoft-edge-webview2-for-net-and-fixed-distribution-method)。

#### <a name="features"></a>功能

*  .NET WPF/WinForms WebView2 现已在 GA (中) 。
*  固定 (自带设备模式) 达到 GA。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  `CoreWebView2NewWindowRequestedEventArgs.Handled` 阻止打开新窗口。   ([问题 549](https://github.com/MicrosoftEdge/WebViewFeedback/issues/549) 和 [问题 560](https://github.com/MicrosoftEdge/WebViewFeedback/issues/560)) 。


<!-- ====================================================================== -->
## <a name="10674-prerelease"></a>1.0.674-prerelease

发布日期：2020 年 10 月 19 日

[NuGet WebView2 SDK 1.0.674 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.674-prerelease)

此预发布版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  添加了 [NavigateWithWebResourceRequest](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#navigatewithwebresourcerequest) 方法，可在导航期间提供 Post 数据或其他请求标头。
*  添加了 [DOMContentLoaded](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_domcontentloaded) 事件，该事件在加载和分析初始 HTML 文档时运行。
*  在 WebView2 上添加了 [Environment](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_environment) 属性。  此属性公开创建 WebView2 实例的 WebView2 环境。
*  添加了 [允许开发人员](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_cookiemanager) 对 WebView2 会话进行身份验证或从 WebView 检索 Cookie 以验证其他工具的 Cookie 管理 API。  WebView2 团队计划进行特定于语言或框架的改进。  请参阅 [API 审阅：Cookie 管理](https://github.com/MicrosoftEdge/WebView2Announcement/issues/2)。
*  更新[了 WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件，向 [WebResourceResponseView：：GetContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true#getcontent) 添加了不可变 [WebResourceResponseView](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true) 和 [WebResourceResponseReceivedEventArgs：:P opulateResponseContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponsereceivedeventargs?view=webview2-0.9.628-prerelease&preserve-view=true#populateresponsecontent)。
*  在 WebView2 [Microsoft Defender 应用程序防护 (WDAG) ](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)关闭。
*  添加了 [用于可视化托管的 SystemCursorId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller2?view=webview2-1.0.674-prerelease&preserve-view=true#get_systemcursorid) 。
*  为可视化托管中的 Input 方法添加了 bug 修复。
*  删除了使用 `version.lib` WebView2 静态库时对 的 include 要求。

### <a name="net"></a>.NET

*  更新 [了 CoreWebView2](/dotnet/api/microsoft.web.webview2.core.corewebview2) 类以公开 `CoreWebView2Environment` 变量。
*  将命名空间中自定义 EventArgs `Microsoft.Web.WebView2.Core` 类的实现更改为 [System.EventArgs](/dotnet/api/system.eventargs) 或 [System.ComponentModel.CancelEventArgs](/dotnet/api/system.componentmodel.canceleventargs) 的子类。   ([问题 250](https://github.com/MicrosoftEdge/WebViewFeedback/issues/250)) 
*  增加了对 [WinForms 中 CoreWebView2CreationProperties](/dotnet/api/microsoft.web.webview2.winforms) 的支持。   ([问题 204](https://github.com/MicrosoftEdge/WebViewFeedback/issues/204)) 。
*  添加了 [WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) .NET API。   ([问题 #219](https://github.com/MicrosoftEdge/WebViewFeedback/issues/219)) 。
*  将 WinForms Designer [Source](/dotnet/api/microsoft.web.webview2.winforms.webview2.source) 属性更新为默认值或重置为 null。   ([问题 #177](https://github.com/MicrosoftEdge/WebViewFeedback/issues/177)) 。
*  更新了 WebView2.Init () 中的 WebView2 边界，以支持小于 100% 的 DPI 模式。   ([问题 #432](https://github.com/MicrosoftEdge/WebViewFeedback/issues/432)) 。
*  更新 [了 BuildWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.buildwindowcore) 和 [DestroyWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.destroywindowcore) 以提高稳定性。   ([问题 #382](https://github.com/MicrosoftEdge/WebViewFeedback/issues/382)) 。
*  更新了 .NET 加载程序基，以在进程位（而不是操作系统体系结构）上加载。   ([问题 #431](https://github.com/MicrosoftEdge/WebViewFeedback/issues/431)) 。
*  重命名为 `EdgeNotFoundException` [WebView2RuntimeNotFoundException](/dotnet/api/microsoft.web.webview2.core.webview2runtimenotfoundexception)。


<!-- ====================================================================== -->
## <a name="1062222"></a>1.0.622.22

发布日期：2020 年 10 月 19 日

[NuGet WebView2 SDK 1.0.622.22 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.622.22)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：Win32 C/C++ WebView2 现已正式发布， (GA) 。  从此版本开始，发布 SDK 是向前兼容的。  请参阅 [GA 公告博客文章](https://blogs.windows.com/msedgedev/edge-webview2-general-availability)。

*  Evergreen WebView2 运行时和安装程序是 GA。  引导程序、引导程序下行链接和 Evergreen WebView2 运行时的独立安装程序Microsoft Edge [WebView2](https://developer.microsoft.com/microsoft-edge/webview2/)。  [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库也提供了安装工作流的示例代码。

有关运行时、常青分发和固定版本分发详细信息，请参阅分发 [应用和 WebView2 运行时](concepts/distribution.md)。


<!-- ====================================================================== -->
## <a name="0962211"></a>0.9.622.11

发布日期：2020 年 9 月 10 日

[NuGet WebView2 SDK 0.9.622.11 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.622.11)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：此 SDK 是 WebView2 Win32 C/C++ GA 的候选发布版。  GA 版本应使用相同的 API 界面和功能。

*  断开 [浏览器策略](/deployedge/microsoft-edge-policies)。
*  在 WebView2 环境选项上添加了 [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#get_allowsinglesignonusingosprimaryaccount) 属性以打开 WebView 的条件访问。
*  进行了 `ICoreWebView2NewWindowRequestedEventArgs` 更新以包括 [WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.622&preserve-view=true#get_windowfeatures) 属性和关联的 [ICoreWebView2WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2windowfeatures?view=webview2-0.9.622&preserve-view=true)。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  进行了 `System.Windows.Rect`  更新以 `System.Drawing.Rectangle` 使用而不是 (`System.Windows.Rect` [问题 #235](https://github.com/MicrosoftEdge/WebViewFeedback/issues/235)) 。
*  更新了 NewWindowRequested 事件以处理 `window.open()` 不带参数的请求。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  [使用 指定的 AdditionalBrowserArguments](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#put_additionalbrowserarguments) `ICoreWebView2EnvironmentOptions` 不会替代环境变量或注册表值。  请参阅 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.622&preserve-view=true#createcorewebview2environmentwithoptions)。


<!-- ====================================================================== -->
## <a name="09579"></a>0.9.579

发布日期：2020 年 7 月 20 日

[NuGet WebView2 SDK 0.9.579 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.579)

此版本的 WebView2 SDK 要求Microsoft Edge版本 86.0.579.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：发布 Evergreen WebView2 运行时和安装程序进行预览。  请参阅 [分配应用和 WebView2 运行时](concepts/distribution.md)。

*  > [!IMPORTANT]
   > **通知**：下一个 SDK 发布后，不再支持以下 WebView2 SDK 版本：
   >
   > *  [0.8.190](#08190)
   > *  [0.8.230](#08230)
   > *  [0.8.270](#08270)
   > *  [0.8.314](#08314)
   > *  [0.8.355](#08355)
   >
   > WebView2 SDK 版本在发布时也标记为 nuget.org。 WebView2 建议使用最新版本的 WebView2 保持最新。

*  添加了 WebView 工作线程改进。   ([问题 #318](https://github.com/MicrosoftEdge/WebViewFeedback/issues/318)) 。
*  在 WebView 中关闭弹出窗口阻止程序。  请参阅 [事件中的 IsUserInitiated](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.538&preserve-view=true#get_isuserinitiated) `NewWindowRequested` 属性。
*  确保为 运行 WebView 导航启动事件 `about:blank`。  `NavigationStarting`现在，所有导航都`about:blank` `srcdoc` `iframe`运行事件，但不支持和忽略元素的 取消。
*  在 WebView 中 `edge://` 阻止了某些 URI 方案。
*  在 WebView2 环境选项上添加了实验性 [IsSingleSignOnUsingOSPrimaryAccountEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-0.9.538-prerelease&preserve-view=true#get_issinglesignonusingosprimaryaccountenabled) 属性，以打开 WebView 的条件访问。
*  添加了实验 [性 WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-0.9.538-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件，该事件在 WebView 接收并处理来自 WebResource 请求的响应后运行。  响应对象中包含身份验证标头（如果有）。

### <a name="net"></a>.NET

*  改进了 WPF 焦点处理。   ([问题 #185](https://github.com/MicrosoftEdge/WebViewFeedback/issues/185)) 。
*  在 `ZoomFactor` WPF Webview2 控制器上添加了 属性。


<!-- ====================================================================== -->
## <a name="09538"></a>0.9.538

[NuGet WebView2 SDK 0.9.538 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.538)

此版本的 WebView2 SDK 要求Microsoft Edge版本 85.0.538.0 或更高版本。

### <a name="general"></a>概要

*  放弃对 WebView2 SDK 版本 [0.8.149 的支持](#08149)。  WebView2 建议使用最新版本的 WebView2 保持最新。
*  更新了组策略，以考虑Microsoft Edge浏览器的配置文件路径 ([#179](https://github.com/MicrosoftEdge/WebViewFeedback/issues/179)) 。

### <a name="win32-cc"></a>Win32 C/C++

*  添加了 [ICoreWebView2ExperimentalNewWindowRequestedEventArgs：：get_WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-0.9.538-prerelease&preserve-view=true#get_windowfeatures)`window.open()`，在运行并关联 [ICoreWebView2ExperimentalWindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwindowfeatures?view=webview2-0.9.538-prerelease&preserve-view=true) [ (#70) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/70) 时触发。
*  > [!IMPORTANT]
   > **中断更改**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) ，并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.538&preserve-view=true#createcorewebview2environmentwithoptions)。

*  > [!IMPORTANT]
   > **更改：** 为了确保 WebView2 API 符合 Windows API 命名约定，WebView2 团队更新了以下名称。
   >
   > *  [AreRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_areremoteobjectsallowed) 现在 [为 AreHostObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.538&preserve-view=true#get_arehostobjectsallowed)。

*  更新 [了 AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.538&preserve-view=true#addhostobjecttoscript)。  原来的主机对象序列化器标记现在设置为代理对象。  然后，当在 JavaScript 回调 ([#148](https://github.com/MicrosoftEdge/WebViewFeedback/issues/148)) 中作为参数传递时，主机对象序列化标记将序列化回主机) 。

### <a name="net-09538-prerelease"></a>.NET (0.9.538 预发行) 

*  发布的 WinForms 和 WPF WebView2API 示例是 WebView2 SDK 的全面指南。  请参阅 [示例存储库](https://github.com/MicrosoftEdge/WebView2Samples)。
*  添加了对可视化托管和窗口功能实验 [API 的支持](concepts/versioning.md#experimental-apis)。
*  > [!IMPORTANT]
   > **中断更改**：以下延迟现在实现 IDisposable：  [ScriptDialogOpening](/dotnet/api/microsoft.web.webview2.core.corewebview2.scriptdialogopening)、 [NewWindowRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.newwindowrequested)、 [WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) 和 [PermissionRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.permissionrequested)。

*  添加了 [GetAvailableBrowserVersionString 和](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.getavailablebrowserversionstring) [CompareBrowserVersions](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.comparebrowserversions) 作为 [CoreWebView2Environment](/dotnet/api/microsoft.web.webview2.core.corewebview2environment) 静态。


<!-- ====================================================================== -->
## <a name="09515-prerelease"></a>0.9.515-prerelease

[NuGet WebView2 SDK 0.9.515 预发行包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.515-prerelease)

此预发布版本的 WebView2 SDK 要求Microsoft Edge版本 84.0.515.0 或更高版本。

*  > [!IMPORTANT]
   > 通知 **：** WebView2 现在支持 Windows 窗体 4.6.2 或更高版本上的 .NET Framework 和 WPF，以及预发行程序包中的 .NET Core 3.0 或**更高版本。**

*  有关生成 WPF 应用的信息，请参阅[开始 WPF 应用中的 WebView2](get-started/wpf.md) 和 WPF 特定 API 的 WebView2 [WPF](/dotnet/api/microsoft.web.webview2.wpf) 参考。
*  有关生成应用Windows 窗体，请参阅 [WinForms 开始中的 WebView2](get-started/winforms.md) 和 WebView2 [Windows 窗体](/dotnet/api/microsoft.web.webview2.winforms)参考，Windows 窗体特定 API。
*  有关 CoreWebView2 API 详细信息，请参阅 [.NET 参考](/dotnet/api/microsoft.web.webview2.core)。
*  > [!CAUTION]
   > **已知问题**：WebView2 团队了解预发行版中在将来版本中要解决的一些问题。
   >
   > *  **DPI 感知**：WebView2 for WPF 当前无法感知 DPI。  在高 DPI 监视器上初始化 WebView2 时，存在一个已知问题，即 WebView 最初初始化为窗口的一小部分，直到调整窗口大小。
   > *  **WPF 设计器**：当前不支持 WPF 设计器。  在文本编辑器中直接修改相应的 XAML，在应用中添加 WebView2 控件。


<!-- ====================================================================== -->
## <a name="09488"></a>0.9.488

[NuGet WebView2 SDK 0.9.488 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.488)

此版本的 WebView2 SDK 要求Microsoft Edge版本 84.0.488.0 或更高版本。

*  > [!IMPORTANT]
   > **公告**：从即将发布的 Microsoft Edge版本 83 开始，Evergreen WebView 不再面向稳定浏览器渠道。  相反，它面向另一组二进制文件（品牌为 Evergreen WebView2 Runtime）中，可以通过 WebView2 团队当前正在开发的安装程序进行链接安装。  请参阅 [分配应用和 WebView2 运行时](concepts/distribution.md)。

*  > [!IMPORTANT]
   > 公告 **：今后**，WebView2 团队发布两个程序包：包含实验性 API (的预发布包) 以及具有稳定 API (的稳定版本包，用于增强可信度) 。  若要了解这些差异，请参阅了解 [浏览器版本和 WebView2](concepts/versioning.md)。

*  > [!IMPORTANT]
   > **更改**：为了确保 WebView2 API 符合 Windows API 命名约定，WebView2 团队更新了以下接口的名称。
   >
   > *  `CORE_WEBVIEW2_*` 前缀现在为 `COREWEBVIEW2_*`。
   > *  [GetCoreWebView2BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.430&preserve-view=true#getcorewebview2browserversioninfo) 现在为 [GetAvailableCoreWebView2BrowserVersionString](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#getavailablecorewebview2browserversionstring)。
   > *  [get_BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.430&preserve-view=true#get_browserversioninfo) 现已 [get_BrowserVersionString](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.488&preserve-view=true#get_browserversionstring)。
   > *  [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 现在为 [AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#addhostobjecttoscript)。
   > *  [RemoveRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#removeremoteobject) 现在 [为 RemoveHostObjectFromScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#removehostobjectfromscript)。
   > *  `chrome.webview.remoteObjects` `chrome.webview.hostObjects`现在是 。

*  > [!IMPORTANT]
   > **中断更改**： `AddRemoteObject` JS 代理方法也重命名。
   >
   > *  `getLocal` `getLocalProperty`现在是 。
   > *  `setLocal` `setLocalProperty`现在是 。
   > *  `getRemote` `getHostProperty`现在是 。
   > *  `setRemote` `setHostProperty`现在是 。
   > *  `applyRemote` `applyHostFunction`现在是 。

*  > [!IMPORTANT]
   > **中断更改**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) ，并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithoptions)。

*  添加了 [FrameNavigationCompleted](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_framenavigationcompleted) 事件。  现在，当元素 `iframe` 完成导航时，将运行事件并返回导航和导航 ID 的成功。
*  添加了 [ICoreWebView2EnvironmentOptions](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.488&preserve-view=true) 接口，可用于确定应用面向的 Evergreen WebView2 运行时的版本。
*  添加了 [IsBuiltInErrorPageEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_isbuiltinerrorpageenabled) 设置。  现在，可以选择针对导航失败打开或关闭内置错误网页，并呈现进程失败。
*  更新了远程对象注入以支持 #[113 (.](https://github.com/MicrosoftEdge/WebViewFeedback/issues/113)NET `IDispatch`) 。
*  更新 [了 NewWindowRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_newwindowrequested) 事件以处理来自上下文菜单的请求 ([#108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/108)) 。
*  发布了第一个单独的 WebView2 预发布包，可在其中访问可视托管 API。  WebView2 团队更新 [了 APISample](https://github.com/MicrosoftEdge/WebView2Samples) 以包含新的实验性 API。
   *  添加了 [ICoreWebView2ExperimentalCompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller?view=webview2-0.9.488-prerelease&preserve-view=true) 接口，以连接到合成树并为 WebView 提供输入。
   *  添加了 [ICoreWebView2ExperimentalPointerInfo](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalpointerinfo?view=webview2-0.9.488-prerelease&preserve-view=true)，其中包含 来自 的所有信息 `POINTER_INFO`。  此对象传递到 SendPointerInput 以将指针输入注入 WebView。
   *  添加了 [ICoreWebView2ExperimentalCursorChangedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcursorchangedeventhandler?view=webview2-0.9.488-prerelease&preserve-view=true)，告知应用何时应更改 WebView 上的鼠标光标。  当鼠标悬停在 WebView 中的文本框上时，光标会从箭头变为选择器。  上的 `cursor` 属性 `CompositionController` 告知应用鼠标光标当前应适用于 WebView 的内容。


<!-- ====================================================================== -->
## <a name="09430"></a>0.9.430

[NuGet WebView2 SDK 0.9.430 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.430)

此版本的 WebView2 SDK 要求Microsoft Edge版本 82.0.430.0 或更高版本。

WebView2 SDK 是官方 Win32 C++ Beta 版本，它包含了来自反馈的多项功能请求。  WebView2 团队尝试通过发生重大变化来限制发布数量。  作为一般可用性方法，Beta 版本中将包含一些重大重大更改。

*  > [!IMPORTANT]
   > **更改：** 在最终版本接近最终发布时，WebView2 `IWebView2WebView` `ICoreWebView2` 团队将前缀重命名为 ，以确保 WebView2 API 符合 Windows API 命名约定。  此外，为了从 UI 框架利用 WebView2 SDK，WebView2 团队分为 [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true) `ICoreWebView2` 和 [ICoreWebView2Host](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true)。  `ICoreWebView2Host` 支持调整大小、显示和隐藏、对焦以及与窗口和合成相关的其他功能。  ICoreWebView2 支持所有其他 WebView2 功能。  若要了解有关合并更改的信息，请参阅 [WebView2](https://github.com/MicrosoftEdge/WebView2Samples/pull/17) [APISample](https://github.com/MicrosoftEdge/WebView2Samples) 项目中的 WebView2 拉取请求。

*  > [!IMPORTANT]
   > **重大更改**：将 [DocumentStateChanged](/microsoft-edge/webview2/reference/win32/iwebview2webview?view=webview2-0.8.355&preserve-view=true#add_documentstatechanged) 拆分为三个组件：  [SourceChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_sourcechanged)、 [ContentLoading](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_contentloading) 和 [HistoryChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_historychanged)。  现在，当源 URL 更改时， `SourceChanged` 将运行事件。  当历史记录状态更改时， `HistoryChanged` 将运行事件。  加载 `ContentLoading` 新文档时，该事件在初始脚本之前运行。

*  添加了对 ARM64 体系结构的支持。
*  添加了对 (设备的) 输入面板支持。
*  添加了对 Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 和 Windows Server 2016 的支持。
*  添加了 [NotifyParentWindowPositionChanged](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#notifyparentwindowpositionchanged) ，使状态栏在窗口模式下跟随窗口。  此外，在无窗口模式下实现更改，以便辅助功能正常工作。
*  添加了 [AreRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_areremoteobjectsallowed) 设置以全局控制网页是否可以通过任何远程对象访问。  默认情况下，启用 `AreRemoteObjectsAllowed` ，因此 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 添加的远程对象可从网页访问。  关闭 `AreRemoteObjectsAllowed` 后，无法从网页访问对象。  更改将应用于下一个导航事件。
*  添加了 [IsZoomControlEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_iszoomcontrolenabled) 设置，以防止用户使用 和 `ctrl`+`ctrl`+`+` `ctrl``-` (或 + 鼠标滚轮) 。  当关闭该设置时，仍可 [put_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#put_zoomfactor) 设置缩放。
*  将 ZoomFactor 更改为仅应用于当前 WebView。  对当前 WebView 的缩放更改不会影响使用同一源网站导航到的其他 WebView。  请参阅 [get_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#get_zoomfactor)。
*  Hid ZoomView UI for WebView ([#95](https://github.com/MicrosoftEdge/WebViewFeedback/issues/95)) 。
*  添加了 [SetBoundsAndZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#setboundsandzoomfactor)。  现在，你可以同时设置 WebView 的缩放系数和边界。
*  添加了 [WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) 事件。  请参阅 [add_WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) ([#119](https://github.com/MicrosoftEdge/WebViewFeedback/issues/119)) 。
*  添加了对 `beforeunload` JavaScript 对话框事件对话框类型的支持， [并添加了CORE_WEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#core_webview2_script_dialog_kind) 枚举条目。
*  向 HttpRequestHeaders 添加了 [GetHeaders](/microsoft-edge/webview2/reference/win32/icorewebview2httprequestheaders?view=webview2-0.9.430&preserve-view=true#getheaders) ，将 [GetHeader](/microsoft-edge/webview2/reference/win32/icorewebview2httpresponseheaders?view=webview2-0.9.430&preserve-view=true#getheader) 添加到 HttpResponseHeaders，将 [get_HasCurrentHeader 属性添加到](/microsoft-edge/webview2/reference/win32/icorewebview2httpheaderscollectioniterator?view=webview2-0.9.430&preserve-view=true#get_hascurrentheader) HttpHeadersCollectionIterator。
*  > [!IMPORTANT]
   > **中断更改**：已修改 `DevToolsProtocolEventReceived` 的行为。  现在，你可以为特定的 [DevTools 协议事件创建 DevToolsProtocolEventReceiver](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true)，然后使用 add_DevToolsProtocolEventReceived [remove_DevToolsProtocolEventReceived 订阅/取消订阅](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#remove_devtoolsprotocoleventreceived)[此类事件](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#add_devtoolsprotocoleventreceived)/。

*  > [!IMPORTANT]
   > **Breaking Change**： Changed `WebMessageReceivedEventArgs` [get_WebMessageAsString](/microsoft-edge/webview2/reference/win32/iwebview2webmessagereceivedeventargs?view=webview2-0.8.355&preserve-view=true#get_webmessageasstring) property to a [TryGetWebMessageAsString](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventargs?view=webview2-0.9.430&preserve-view=true#trygetwebmessageasstring) method.

*  > [!IMPORTANT]
   > **Breaking Change**： Changed `AcceleratorKeyPressedEventArgs` [Handle](/microsoft-edge/webview2/reference/win32/iwebview2acceleratorkeypressedeventargs?view=webview2-0.8.355&preserve-view=true#handle) method to a [get_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2acceleratorkeypressedeventargs?view=webview2-0.9.430&preserve-view=true#get_handled) property.


<!-- ====================================================================== -->
## <a name="08355"></a>0.8.355

[NuGet WebView2 SDK 0.8.355 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.355)

此版本的 WebView2 SDK 要求Microsoft Edge版本 80.0.355.0 或更高版本。

*  发布的 WebView2API 示例，WebView2 SDK 的全面指南。  请参阅 [API 示例](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample)。
*  添加了对除英语 # [30 (之外](https://github.com/MicrosoftEdge/WebViewFeedback/issues/30) 的所有语言的 IME) 。
*  更新了事件的 API 图面 `WebResourceRequested` 以响应 Bug 报告。  现在，已弃用创建时同时指定筛选器和事件。  若要创建 Web 资源请求的事件，add_WebResourceRequested添加事件[](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#add_webresourcerequested)，使用 [AddWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#addwebresourcerequestedfilter) 添加筛选器。  [RemoveWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#removewebresourcerequestedfilter) 删除筛选器 ([#36](https://github.com/MicrosoftEdge/WebViewFeedback/issues/36))  ([#74](https://github.com/MicrosoftEdge/WebViewFeedback/issues/74)) 。
*  > [!IMPORTANT]
   > **中断更改**：已修改全屏行为。  已弃用 [IsFullScreenAllowed](/microsoft-edge/webview2/reference/win32/iwebview2settings?view=webview2-0.8.355&preserve-view=true#get_isfullscreenallowed_deprecated)。  现在，默认情况下，如果 WebView 中的元素 (如视频) 设置为全屏，它将填充 WebView 边界。  使用 [ContainsFullScreenElementChanged](/microsoft-edge/webview2/reference/win32/iwebview2containsfullscreenelementchangedeventhandler?view=webview2-0.8.355&preserve-view=true) 事件和 get_ContainsFullScreenElement [](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#get_containsfullscreenelement) 指定当元素要进入全屏模式时应用应如何调整 WebView 的大小。


<!-- ====================================================================== -->
## <a name="08314"></a>0.8.314

[NuGet WebView2 SDK 0.8.314 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.314)

此版本的 WebView2 SDK 要求Microsoft Edge版本 80.0.314.0 或更高版本。

### <a name="changes"></a>更改

*  添加了对 Windows 7、Windows 8 和 Windows 8.1 的支持。
*  添加了Visual Studio和Visual Studio Code对 WebView2 的调试支持。  现在，从 IDE 在 WebView2 中调试脚本。  请参阅 [如何使用 WebView2 控件进行开发时调试](how-to/debug.md)。
*  为 `Native Object Injection` WebView2 中正在运行的脚本添加了 ，用于从应用的 Win32 组件访问 IDispatch 对象并访问 IDispatch 对象的属性。  请参阅 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#addremoteobject) ([#17](https://github.com/MicrosoftEdge/WebViewFeedback/issues/17)) 。
*  添加了 `AcceleratorKeyPressed` event。  请参阅 [add_AcceleratorKeyPressed](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#add_acceleratorkeypressed) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  `Context Menus`已关闭 。  请参阅 [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/iwebview2settings2?view=webview2-0.8.355&preserve-view=true#put_aredefaultcontextmenusenabled) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  已更新 `DPI Awareness`。  现在，WebView 的 DPI 感知与主机应用的 DPI 感知相同。

   > [!NOTE]
   > 如果启动另一个混合应用时 DPI 感知不同于原始 WebView，则新 WebView `user data folder` 不会启动（如果 与 #) [1 (相同](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1) ）。

*  进行了 `Notification Change Behavior` 更新，以便 WebView2 自动拒绝 WebView 中托管的 Web 内容所提示的通知权限请求。


<!-- ====================================================================== -->
## <a name="08270"></a>0.8.270

[NuGet WebView2 SDK 0.8.270 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.270)

此版本的 WebView2 SDK 要求Microsoft Edge版本 78.0.270.0 或更高版本。

### <a name="changes"></a>更改

*  添加了 `DocumentTitleChanged` 事件以指示文档标题 ([问题 27) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/27) 。

*  添加了 `GetWebView2BrowserVersionInfo` API ([Issue #18](https://github.com/MicrosoftEdge/WebViewFeedback/issues/18)) 。

*  添加了 `NewWindowRequested` event。

*  更新 `CreateWebView2EnvironmentWithDetails` 了 函数以删除 `releaseChannelPreference`。  有关函数详细信息， `CreateWebView2EnvironmentWithDetails` 请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  仍然支持注册表和环境变量替代。  除非重写，否则使用默认通道首选项。

   在频道搜索期间，WebView2 团队将跳过任何与 WebView2 SDK 不兼容的以前频道版本。

   WebView2 团队选择更稳定的渠道，以确保最终用户的行为最一致。  使用最新的 Canary 版本进行测试`WEBVIEW2_RELEASE_CHANNEL_PREFERENCE``1`时，应在启动应用之前创建一个脚本，将环境变量设置为 。  请参阅 [测试即将推出的 API 和功能](how-to/set-preview-channel.md)。

*  使用逻辑 `CreateWebView2EnvironmentWithDetails` 更新了函数，以选择 `userDataFolder` 未指定时。  有关函数详细信息， `CreateWebView2EnvironmentWithDetails` 请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  如果您之前 `userDataFolder` 使用默认位置，则切换到新 SDK `userDataFolder` 时，默认设置将重置 (设置为主机代码目录中的新位置，) 也会重置您的状态。  如果主机进程无权 `CreateWebView2EnvironmentWithDetails` 写入指定目录，则函数可能会失败。  你可以将数据从旧目录复制到 `user data folder` 新目录。


<!-- ====================================================================== -->
## <a name="08230"></a>0.8.230

[NuGet WebView2 SDK 0.8.230 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.230)

此版本的 WebView2 SDK 要求Microsoft Edge版本 77.0.230.0 或更高版本。

### <a name="changes"></a>更改

*  添加了 `Stop` API 以停止所有导航和挂起的资源提取 ([问题 28](https://github.com/MicrosoftEdge/WebViewFeedback/issues/28)) 。
*  向`.tlb`文件包NuGet问题 ([#22](https://github.com/MicrosoftEdge/WebViewFeedback/issues/22)) 。
*  向 NuGet Issue [#32](https://github.com/MicrosoftEdge/WebViewFeedback/issues/32) (中的安装程序列表添加了 .NET) 。


<!-- ====================================================================== -->
## <a name="08190"></a>0.8.190

[NuGet WebView2 SDK 0.8.190 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.190)

此版本的 WebView2 SDK 要求Microsoft Edge版本 77.0.190.0 或更高版本。

*  已 `get_AreDevToolsEnabled`/`put_AreDevToolsEnabled` 添加到控制用户能否打开 DevTools ([问题 #16) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/16) 。
*  已 `get_IsStatusBarEnabled`/`put_IsStatusBarEnabled` 添加到控件中，以控制状态栏是否 ([问题 #19) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/19) 。
*  已`get_CanGoBack``get_CanGoForward``GoForward`/`GoBack`//添加用于返回和向前浏览导航历史记录。
*  添加了 HTTP 标头 (`IWebView2HttpHeadersCollectionIterator`//`IWebView2HttpRequestHeaders``IWebView2HttpRequestHeaders`) WebView 中查看和修改 HTTP 标头。
*  在 64 位计算机上添加了 32 位 WebView ([Issue #13](https://github.com/MicrosoftEdge/WebViewFeedback/issues/13)) 。
*  向 SDK ([Issue #14) 添加了](https://github.com/MicrosoftEdge/WebViewFeedback/issues/14) WebView IDL。
*  添加了 lib 以支持接口 `IID\_\*` ID 对象 ([Issue #12](https://github.com/MicrosoftEdge/WebViewFeedback/issues/12)) 。
*  在 SDK 中添加了 `TARGET` DLL 文件的路径、链接和自动NuGet文件。
*  在脚本中打开 `window.open()` 请求。


<!-- ====================================================================== -->
## <a name="08149"></a>0.8.149

[NuGet WebView2 SDK 0.8.149 的程序包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.149)

此版本的 WebView2 SDK Microsoft Edge版本 76.0.149.0 或更高版本。

初始开发人员预览版本。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [联系 Microsoft Edge WebView2 团队](contact.md)
