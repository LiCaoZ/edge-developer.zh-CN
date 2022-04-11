---
title: 了解不同的 WebView2 SDK 版本
description: 了解用于Microsoft Edge WebView2 的不同 WebView2 SDK 版本和版本模型。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 08/03/2021
ms.openlocfilehash: d3314c3cdb116a25aead31227099ed82a5ea275d
ms.sourcegitcommit: 5351b3950b3bb7bc698415a2e5608816f1f9fca4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2022
ms.locfileid: "12473790"
---
# <a name="understand-the-different-webview2-sdk-versions"></a>了解不同的 WebView2 SDK 版本

WebView2 SDK 的NuGet包包含发布和预发行包。  使用预发行 SDK 和预览频道的 Microsoft Edge，或将版本 SDK 与 WebView2 运行时配合使用。

_预发行版_ 如果要在将这些 API 的支持添加到运行时之前测试最新的 WebView2 API（包括实验性 API），则 SDK 包在开发过程中使用。  建议使用 Canary 通道，因为它具有最新 API 的实现。  若要测试和使用实验性 WebView2 API，请使用以下组合：
*  WebView2 SDK 的 _预发行_ 版本。
*  开发客户端上Microsoft Edge_的预览频道_。

_释放_ SDK 包仅包含稳定的 API，而不包含实验性 API。  在开发 WebView2 应用的生产版本时，请使用以下组合：
*  WebView2 SDK 的 _发布_ 版本。
*  开发客户端上的 WebView2 _运行时_ 。

下面提供了有关预发行版和版本 SDK 包的更多详细信息。


<!-- ====================================================================== -->
## <a name="use-a-prerelease-version-of-the-sdk-along-with-a-preview-channel-of-microsoft-edge"></a>使用 SDK 的预发行版本以及预览版Microsoft Edge

开发 Evergreen WebView2 应用时，除了针对 WebView2 运行时进行测试外，还定期针对最新的Microsoft Edge预览频道测试应用。  由于 Web 平台不断发展，因此定期测试是确保应用继续按预期工作的最佳方式。

使用 WebView2 SDK _预发行_包时，请在开发客户端上使用Microsoft Edge预览频道。  预览频道也称为 _预览体验成员_ 频道。  建议使用 Canary 预览频道而不是 Beta 或 Dev，因为 Canary 是最新的，并且具有最新实验性 API 的实现。

SDK _预发行_ 包是 SDK 发布包的超级集，具有更多实验 [性 API](#experimental-apis) 的方法签名。  预览频道提供试验性 WebView2 API 的实现。  实验性 API 可能会根据你的反馈进行更改。  避免使用 SDK 预发行包生成生产应用。

有关暂时将应用指向预览频道而不是默认为 WebView2 运行时的信息，请参阅 [测试即将推出的 API 和功能](../how-to/set-preview-channel.md)。


<!-- ====================================================================== -->
## <a name="use-a-release-version-of-the-sdk-along-with-the-runtime"></a>将 SDK 的发布版本与运行时一起使用

使用 WebView2 SDK _发布_包时，请在开发客户端上使用 WebView2 Evergreen _Runtime_，而不是Microsoft Edge预览频道。  默认情况下，WebView2 应用面向运行时，而不是Microsoft Edge。  根据设计，Microsoft Edge稳定通道不支持 WebView2。

SDK _发布_ 包包含所有稳定的 Win32 C/C++ 和 .NET API，不包括实验性 API 的方法签名。  SDK 发布包中的所有 API 都完全受支持，其内部版本号与 WebView2 运行时相同或更高。

SDK 发布包包含以下组件：
*  [Win32 C/C++ API](/microsoft-edge/webview2/reference/win32)。
*  .NET API：  [WPF](/dotnet/api/microsoft.web.webview2.wpf)、 [WinForms](/dotnet/api/microsoft.web.webview2.winforms) 和 [Core](/dotnet/api/microsoft.web.webview2.core)。

有关自动更新 Evergreen Runtime 的详细信息，请参阅 [“分发应用”和“WebView2 运行时](distribution.md)”。


<!-- ====================================================================== -->
## <a name="release-cadence"></a>版本节奏

WebView2 SDK 的新版本与Microsoft Edge浏览器的常规节奏相同，大约每四周一次。


<!-- ====================================================================== -->
## <a name="minimum-version-and-build-number-to-instantiate-webview2"></a>用于实例化 WebView2 的最小版本和内部版本号

为了使客户端能够创建 WebView2 实例并在 WebView2 正式发布版 (SDK 内部版本 616) 中使用 API 集，客户端必须具有 WebView2 运行时版本 86.0.616.0 或更高版本。  运行时 86.0.616.0 是一种特殊版本，因为它是正式发布版。

在开发计算机上，客户端必须具有Microsoft Edge预览频道版本 86.0.616.0 或更高版本，或者 WebView2 运行时版本 86.0.616.0 或更高版本。


<!-- ====================================================================== -->
## <a name="forward-compatibility-of-apis"></a>API 的向前兼容性

自 SDK 版本 1 (（即 SDK 版本 [1.0.622.22](../release-notes.md#1062222)) ）以来，WebView2 _版本_ SDK 一直向前兼容。
可以更新 WebView2 应用，以使用最新版本的 SDK 中的最新 API。  你的应用将继续在客户端上工作，因为客户端会自动拥有最新的 WebView2 Evergreen 运行时。

SDK _发布_ 包中的 WebView2 API 是稳定且向前兼容的。  使用生成号等于或更高版本号作为引入 API 的 SDK 生成号的 WebView2 运行时，WebView2 API 有效。  生成号是 Webview2 SDK 的四部分版本号的第三部分，也是 Microsoft Edge 和 WebView2 运行时的四部分版本号的第三部分。

*  使用内部版本号 _等于或小于_ WebView2 运行时的 WebView2 SDK 时，在该 SDK 中有权访问的每个 API 都适用于该版本的运行时。

*  使用内部版本号 _大于_ WebView2 运行时的 WebView2 SDK 时，较新的 API 实现在运行时中不可用。

<!-- create diagram showing 3 SDK releases on a timeline, which ones would work w/ a given runtime -->
例如，如果在 SDK 1.0 中引入了 API。**900.0**，该 API 将适用于运行时 94.0。**900+**.0，但不使用运行时 90.0。**700.0**.

<!-- dup statements, delete? -->
必须协调用于开发的 WebView2 SDK 版本和客户端计算机上安装的 WebView2 运行时版本。
客户端应具有运行时版本，该版本支持用于开发应用的 SDK 版本中的所有最新 API。
若要完全支持 SDK 版本中的最新 API，客户端上的运行时必须具有大于或等于 SDK 生成号的内部版本号。


<!-- ====================================================================== -->
## <a name="experimental-apis"></a>实验性 API

WebView2 SDK _预发行_ 包中的实验性 API 不能保证是向前兼容的，并且可能会在将来的运行时更新中删除。  当 WebView2 SDK 的_预发行_版本最初可用时，该 SDK 仅适用于Microsoft Edge Canary。  不久之后，预发行版 SDK 也适用于 Beta 和 Dev 通道。  使用预发行版 SDK 尽早试用新的 API，并在提升新 API 成为稳定且向前兼容的 API 之前提供反馈。

若要完全支持实验性 API，请使用Microsoft Edge预览频道，而不是 WebView2 常青运行时。  预发行版 SDK 中的任何实验性 API 都不能保证是向前兼容的。  SDK _版本_ 中的 API 是向前兼容的。  有关详细信息，请参阅上述 [API 的向前兼容性](#forward-compatibility-of-apis) 。

WebView2 团队正在寻求有关实验性 WebView2 API 的反馈，这些 API 可能会在将来的版本中升级到“稳定”。  在 WebView2 SDK 参考文档中，实验性 API 指示为“实验性”。

若要帮助你评估实验性 API 并共享反馈，请使用 [WebView2Feedback](https://github.com/MicrosoftEdge/WebViewFeedback) 存储库。

避免在生产应用中使用实验性 API。  在 SDK 的后续版本中，可能会修改、删除或添加实验性 API。  将 API 发布为稳定且公开后，在已弃用状态下的两个版本支持该 API 的实验版本。


<!-- ====================================================================== -->
## <a name="matching-the-runtime-version-with-the-sdk-version"></a>将运行时版本与 SDK 版本匹配

在 Evergreen 分发方法中，客户端的 WebView2 运行时会自动更新到可用的最新版本。  但是，用户或 IT 管理员可能会选择阻止自动更新 WebView2 运行时。  客户端上生成的过时的运行时可能会导致与使用最近 SDK 中的新 API 的更新 WebView2 应用的兼容性问题。

如果在客户端上阻止更新 WebView2 运行时，请确保知道应用所需的 [WebView2 运行时](https://developer.microsoft.com/microsoft-edge/webview2/) 的最小内部版本号。  支持 SDK 正式发布所需的最低运行时版本 (内部版本 616) 早于最新运行时。
最新的运行时支持最新 SDK 版本中的所有 API。  

若要检查 SDK 的特定内部版本号与运行时或Microsoft Edge预览频道之间的兼容性，请参阅 [WebView2 SDK 的发行说明](../release-notes.md)。


<!-- ====================================================================== -->
## <a name="feature-detecting-to-test-whether-the-installed-runtime-supports-recently-added-apis"></a>用于测试已安装的运行时是否支持最近添加的 API 的功能检测

<!-- this is the main section about QI; other articles should have a couple paragraphs only, and link to here -->

如果你的应用使用常青运行时而不是固定版本，则应使用或`try-catch`使用或包装对相对较新的 WebView2 API 的任何调用`QueryInterface`。  有些边缘情况下，客户端的 Evergreen 运行时不是最新的生成，因此会落后于 SDK 生成号，因为管理员可能已关闭 WebView2 运行时的更新，或者客户端可能处于脱机状态。

使用 WebView2 SDK 的最新版本开发 WebView2 应用时，如果使用最近添加的 API，则应测试或“功能检测”该 API 是否存在于客户端安装的 WebView2 运行时中。  应用如何以编程方式测试 API 支持取决于编码平台。

*  **Win32 C/C++**。  请求 DLL 导出`CreateCoreWebView2Environment`时，以及在任何`CoreWebView2`对象上运行`QueryInterface`时，测试返回值 。`E_NOINTERFACE`  该返回值可能表示客户端的 WebView2 运行时是不支持该接口的较旧版本。

   有关检查运行时中是否存在特定 WebView2 API 的示例，请在 [AppWindow.cpp](https://github.com/MicrosoftEdge/WebView2Samples/blob/8ec7de9d3e80a942bc7025cffad98eee75e11e64/SampleApps/WebView2APISample/AppWindow.cpp#L622) 中找到`try_query`。  此文件包装宏函数中定义`CheckFailure.h`的 `CHECK_FAILURE` WebView2 API 调用。

*  **.NET 和 WinUI**。  使用添加到较新版本的 `No such interface supported` WebView2 SDK 的方法、属性和事件时，使用`try/catch`并检查异常。  此异常可能指示客户端的 WebView2 运行时是不支持该 API 的较旧版本。

如果代码确定 API 在客户端安装的 WebView2 运行时中不可用，则应为关联的功能提供正常回退，或通知用户必须更新 WebView2 运行时才能使用该功能。

此技术被列为 WebView2 开发最佳做法，测试 [已安装的 WebView2 运行时是否支持 API](developer-guide.md#test-whether-newer-apis-are-supported-by-the-installed-webview2-runtime)。
