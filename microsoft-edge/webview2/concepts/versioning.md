---
description: 用于 WebView2 Microsoft Edge模型
title: 了解 WebView2 SDK 版本
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/03/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、wpf 应用、wpf、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: 5461d752164b2af49c7104e3008166ce8abbbaea
ms.sourcegitcommit: 01ed086305c06b4e3a0436586524986700276148
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "11893567"
---
# <a name="understand-webview2-sdk-versions"></a>了解 WebView2 SDK 版本

WebView2 SDK 的 NuGet 包同时包含发布包和预发行版包。  将预发行版 SDK 与预览频道一Microsoft Edge，或将发布 SDK 与 WebView2 运行时一同使用。

_预发布_ 如果要在将支持这些 API 添加到运行时之前测试最新的 WebView2 API（包括实验性 API），则 SDK 包在开发过程中使用。  建议使用 Canary 通道，因为它具有最新 API 的实现。  当你想要测试和使用实验性 WebView2 API 时，请使用以下组合：
*   _WebView2_ SDK 的预发布版本。
*   开发_客户端上_Microsoft Edge预览频道。

_发布_ SDK 包仅包含稳定的 API，而不包含实验性 API。  在开发 WebView2 应用的生产版本时，请使用以下组合：
*   _WebView2_ SDK 的发行版。
*   开发客户端 _上的_ WebView2 运行时。

下面提供了关于预发行版和发布 SDK 包的更多详细信息。


## <a name="use-a-prerelease-version-of-the-sdk-along-with-a-preview-channel-of-microsoft-edge"></a>将 SDK 的预发布版本与预览频道一Microsoft Edge

开发 Evergreen WebView2 应用时，除了针对 WebView2 运行时进行测试之外，还定期针对最新的 Microsoft Edge 预览频道测试应用。  由于 Web 平台在不断演变，因此定期测试是确保应用继续正常工作的最佳方法。

使用 WebView2 SDK_预发布_包时，请使用Microsoft Edge客户端上的预览频道。  预览频道也称为 _预览体验_ 成员频道。  建议使用 Canary 预览频道，而不是 Beta 或 Dev，因为 Canary 是最新的，并且具有最新实验 API 的实现。

SDK _预发行版_ 包是 SDK 发布包的超集，具有适用于更多实验 [性 API 的方法签名](#experimental-apis)。  预览频道提供实验性 WebView2 API 的实现。  实验性 API 可能会根据你的反馈发生变化。  避免使用 SDK 预发布包生成生产应用。

有关将应用临时指向预览频道（而不是默认指向 WebView2 运行时）的信息，请导航到切换到预览频道，以测试即将推出的 [API 和功能][SetPreviewChannel]。


## <a name="use-a-release-version-of-the-sdk-along-with-the-runtime"></a>将 SDK 的发行版与运行时一同使用

当你使用 WebView2 _SDK_发布包时，请使用开发客户端上的 WebView2 Evergreen _Runtime，_ 而不是使用Microsoft Edge预览通道。  默认情况下，WebView2 应用面向运行时，而不是Microsoft Edge。  根据设计，Microsoft Edge Stable 渠道不支持 WebView2。

SDK _发布_ 包包含所有稳定的 Win32 C/C++ 和 .NET API，并且不包括实验性 API 的方法签名。  在 WebView2 运行时的相同或更高的内部版本号中，SDK 发布包中所有 API 都完全受支持。

SDK 发布包包含以下组件：
*  [Win32 C/C++ API][ReferenceWin32]。
*  .NET [API：WPF、WinForms][DotnetMicrosoftWebWebview2WpfNamespace]和[Core][DotnetMicrosoftWebWebview2CoreNamespace]。 [][DotnetMicrosoftWebWebview2WinformsNamespace]

有关自动更新 Evergreen Runtime 的信息，请导航到分发 [WebView2 应用和 WebView2 运行时][Webview2ConceptsDistribution]。


## <a name="release-cadence"></a>版本节奏

新版本的 WebView2 SDK 的发布与 Microsoft Edge \ (Chromium\) 浏览器的一般节奏相同，大约每六周发布一次。  此节奏计划从版本 94 起每四周Microsoft Edge更改一次。


## <a name="minimum-version-and-build-number-to-instantiate-webview2"></a>实例化 WebView2 的最低版本号和内部版本号

若要使客户端能够创建 WebView2 实例并使用 WebView2 通用版本 (SDK 版本 616) 中的 API 集，客户端必须具有 WebView2 运行时版本 86.0.616.0 或更高版本。  运行时 86.0.616.0 是一个特殊版本，因为它是通用版本。

在开发计算机上，客户端必须具有 Microsoft Edge 预览频道版本 86.0.616.0 或更高版本，或 WebView2 运行时版本 86.0.616.0 或更高版本。


## <a name="forward-compatibility-of-apis"></a>API 的向前兼容性

WebView2 _版本_ SDK 自版本 1（即 SDK 版本 [1.0.622.22](../release-notes.md#1062222) (）以来一直) 。
你可以更新 WebView2 应用以使用最新版 SDK 中的 API。  你的应用将继续在客户端上运行，因为客户端自动具有最新的 WebView2 Evergreen Runtime。

_SDK_发布包中的 WebView2 API 稳定且向前兼容。  使用与引入 API 的 SDK 内部版本号相同或更高的内部版本号的 WebView2 运行时时，WebView2 API 可正常工作。  内部版本号是 Webview2 SDK 的四部分版本号的第三部分，以及 Microsoft Edge 和 WebView2 运行时的四部分版本号。

*  当你使用生成号等于或小于 WebView2 运行时__ 的 WebView2 SDK 时，你有权访问该 SDK 中的每个 API 都适用于该版本的运行时。
*  当你使用内部版本号大于 WebView2 运行时的__ WebView2 SDK 时，更新的 API 的实现在运行时中不可用。

<!-- create diagram showing 3 SDK releases on a timeline, which ones would work w/ a given runtime -->
例如，如果 API 是在 SDK 1.0 中引入的。**900**.0，该 API 将与运行时 94.0 一起运行。**900+**.0，但不包括运行时 90.0。**700**.0.

<!-- dup statements, delete? -->
必须协调用于开发的 WebView2 SDK 版本和安装在客户端计算机上的 WebView2 运行时版本。
客户端应具有一个运行时版本，该版本支持用于开发应用的 SDK 版本中的所有最新 API。
若要在 SDK 的发布版本中完全支持最新 API，客户端上的运行时必须具有大于或等于 SDK 内部版本号的版本号。


## <a name="experimental-apis"></a>实验性 API

WebView2 _SDK_ 预发布包中的实验性 API 不能保证向前兼容，并且可能会在将来的运行时更新中删除。
当_WebView2_ SDK 的预发布版本最初可用时，该 SDK 仅适用于 Microsoft Edge Canary。  在此之后，预发布 SDK 还适用于 Beta 和开发人员渠道。
使用预发布 SDK 尽早试用新 API，在提升新 API 成为稳定且向前兼容的 API 之前提供反馈。

要完全支持实验性 API，请使用Microsoft Edge预览频道，而不是 WebView2 Evergreen Runtime。
预发布 SDK 中任何实验性 API 都不能保证向前兼容。
_SDK_发布版本中的 API 是向前兼容的。  有关详细信息，请参阅上面的 [API 的向前](#forward-compatibility-of-apis) 兼容性。

WebView2 团队正在寻求有关实验性 WebView2 API 的反馈，这些 API 可能会在未来版本中提升为 Stable。
WebView2 SDK 参考文档中将实验性 API 指示为"实验性"。
若要帮助你评估实验性 API 并分享你的反馈，请导航到 [WebView 反馈存储库][GithubMicrosoftedgeWebviewfeedback]。

避免在生产应用中使用实验性 API。  在 SDK 的后续版本中，可能会修改、删除或添加实验性 API。  在将 API 作为稳定公开发布后，该 API 的实验版本受弃用状态中的两个版本的支持。


## <a name="matching-the-runtime-version-with-the-sdk-version"></a>将运行时版本与 SDK 版本匹配

在 Evergreen 分发方法中，客户端的 WebView2 运行时将自动更新到最新版本。
但是，用户或 IT 管理员可能会选择阻止自动更新 WebView2 运行时。
在客户端上生成的过期运行时可能会导致使用最新 SDK 中的新 API 的更新的 WebView2 应用出现兼容性问题。

如果客户端上阻止更新 WebView2 运行时，请确保你知道应用所需的 [WebView2][MicrosoftDeveloperEdgeWebview2] 运行时的最低内部版本号。
支持 SDK 版本 616 版本 616 (版本所需的最低运行时版本) 低于最新运行时版本。
最新运行时支持最新 SDK 版本内的所有 API。

若要检查 SDK 的特定内部版本号与运行时或预览Microsoft Edge之间的兼容性，请导航到[WebView2 SDK][Webview2ReleaseNotes]发行说明。


## <a name="feature-detecting-to-test-whether-the-installed-runtime-supports-recently-added-apis"></a>用于测试已安装的运行时是否支持最近添加的 API 的功能检测

<!-- this is the main section about QI; other articles should have a couple paragraphs only, and link to here -->

如果你的应用使用 Evergreen Runtime 而不是固定版本，你应该使用 或 包装对相对新的 WebView2 API `QueryInterface` 的任何调用 `try-catch` 。  在某些情况下，客户端的 Evergreen Runtime 不是最新的内部版本，因此它滞后于 SDK 内部版本编号，因为管理员可能已经关闭 WebView2 运行时的更新，或者客户端可能处于脱机状态。

在使用最新版本的 WebView2 SDK 开发 WebView2 应用时，如果使用最近添加的 API，应测试或"功能检测"该 API 是否存在于客户端安装的 WebView2 运行时中。  你的应用如何以编程方式测试 API 支持取决于编码平台。

*   **Win32 C/C++**。  请求 DLL 导出时 `CreateCoreWebView2Environment` 以及在任何对象上运行时 `QueryInterface` `CoreWebView2` ，请测试 的返回值 `E_NOINTERFACE` 。  该返回值可能指示客户端的 WebView2 运行时是不支持该接口的较旧版本。  有关检查运行时中是否存在特定 WebView2 API 的示例，在 `try_query` [AppWindow.cpp 中查找][GithubMicrosoftedgeWebview2samplesSampleappsWebview2apisampleAppwindowCpp]。  此文件包装宏函数中的 WebView2 API 调用， `CHECK_FAILURE` 在 中定义 `CheckFailure.h` 。

*   **.NET 和 WinUI**。  使用 `try/catch` 已添加到 WebView2 SDK 的最新版本的方法、属性和事件时，使用并检查 `No such interface supported` 异常。  此异常可能表示客户端的 WebView2 运行时是不支持该 API 的较旧版本。

如果代码确定 API 在客户端安装的 WebView2 运行时中不可用，应为关联的功能提供正常回退，或通知用户他们必须更新 WebView2 运行时以使用该功能。

在测试安装的 WebView2 运行时是否支持 API 时，此技术作为 [WebView2 开发最佳做法列出][Webview2ConceptsDevguideTestAPIs]。


<!--links -->
[Webview2ConceptsDistribution]: ./distribution.md "分发 WebView2 应用和 WebView2 运行时|Microsoft Docs"
[Webview2ReleaseNotes]: ../release-notes.md "WebView2 SDK 发行说明 | Microsoft Docs"
[Webview2ReleaseNotes1062222]: ../release-notes.md#1062222 "1.0.622.22 - WebView2 SDK |Microsoft Docs"
[Webview2ConceptsDevguideTestAPIs]: developer-guide.md#test-whether-newer-apis-are-supported-by-the-installed-webview2-runtime "测试安装的 WebView2 运行时应用程序是否支持 API |Microsoft Docs"
[SetPreviewChannel]: ../how-to/set-preview-channel.md "切换到预览频道以测试即将推出的 API 和功能|Microsoft Docs"
<!-- external links -->
[DeployedgeChannels]: /deployedge/microsoft-edge-channels "频道Microsoft Edge概述|Microsoft Docs"

[DotnetMicrosoftWebWebview2CoreNamespace]: /dotnet/api/microsoft.web.webview2.core "Microsoft.Web.WebView2.Core 命名空间|Microsoft Docs"
[DotnetMicrosoftWebWebview2WpfNamespace]: /dotnet/api/microsoft.web.webview2.wpf "Microsoft.Web.WebView2.Wpf 命名空间|Microsoft Docs"
[DotnetMicrosoftWebWebview2WinformsNamespace]: /dotnet/api/microsoft.web.webview2.winforms "Microsoft.Web.WebView2.WinForms 命名空间|Microsoft Docs"
[DotnetApiWebview2WinformsWebview2Appliesto]: /dotnet/api/microsoft.web.webview2.winforms.webview2#applies-to "WebView2 类|Microsoft Docs"
[ReferenceWin32]: /microsoft-edge/webview2/reference/win32 "WebView2 Win32 C++ 参考|Microsoft Docs"

[MicrosoftDeveloperEdgeWebview2]: https://developer.microsoft.com/microsoft-edge/webview2/ "Microsoft EdgeWebView2 |Microsoft 开发人员"

[GithubMicrosoftedgeWebviewfeedback]: https://github.com/MicrosoftEdge/WebViewFeedback "WebView 反馈 - MicrosoftEdge/WebViewFeedback | GitHub"
[GithubMicrosoftedgeWebview2samplesSampleappsWebview2apisampleAppwindowCpp]: https://github.com/MicrosoftEdge/WebView2Samples/blob/8ec7de9d3e80a942bc7025cffad98eee75e11e64/SampleApps/WebView2APISample/AppWindow.cpp#L622 "AppWindow.cpp - MicrosoftEdge/WebView2Samples |GitHub"

[MicrosoftedgeinsiderDownload]: https://www.microsoftedgeinsider.com/download "下载 Microsoft Edge 预览体验成员频道"
