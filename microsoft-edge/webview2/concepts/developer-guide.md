---
description: 了解在开发 WebView2 应用程序时要使用的开发最佳做法。
title: WebView2 开发的最佳做法
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/03/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview2、WebView、webview、edge、最佳做法
ms.openlocfilehash: 9345273089c620b366d007edaac87e98a34f9b79
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12155876"
---
# <a name="webview2-development-best-practices"></a>WebView2 开发的最佳做法

每个开发团队在构建其应用程序时都遵循不同的做法。  生成 WebView2 生产应用时，建议遵循这些建议和最佳做法。


<!-- ====================================================================== -->
## <a name="use-the-evergreen-runtime-recommended"></a>使用 Evergreen Runtime (推荐) 

我们通常建议使用 Evergreen WebView2 运行时。  固定版本运行时分发仅建议用于具有严格兼容性要求的应用。  Evergreen 运行时在客户端上自动更新，以便你的 WebView2 应用可以使用最新的功能和安全修补程序。  与固定版本运行时相比，Evergreen 运行时还需要更少的磁盘上的存储空间。

如果使用 Evergreen 运行时，在运行 WebView2 应用之前，测试是否已在客户端上安装 Evergreen WebView2 运行时。  有关详细信息，请导航到 [部署 Evergreen WebView2 运行时](../concepts/distribution.md#deploying-the-evergreen-webview2-runtime)。


<!-- ====================================================================== -->
## <a name="run-compatibility-tests-regularly-when-using-the-evergreen-runtime"></a>使用 Evergreen 运行时时定期运行兼容性测试

使用 Evergreen WebView2 运行时时，运行时会自动更新，因此必须定期运行兼容性测试。  若要确保 WebView2 应用继续正常工作，请针对[Microsoft Edge Insider (preview) Channels (](https://www.microsoftedgeinsider.com/download) Beta、Dev 或 Canary) 测试 WebView2 控件中的 Web 内容。

本指南类似于我们向 Web 开发人员提供的指导。  有关详细信息，请导航到["测试你的应用是否向前兼容"。](../concepts/distribution.md#test-your-app-for-forward-compatibility)


<!-- ====================================================================== -->
## <a name="test-whether-newer-apis-are-supported-by-the-installed-webview2-runtime"></a>测试安装的 WebView2 运行时是否支持较新的 API

<!-- the main section about QueryInterface is in versioning.md; this section should be only a couple paragraphs -->

若要运行使用 Webview2 SDK 的特定版本开发的 WebView2 应用，客户端必须已安装 WebView2 运行时的兼容版本。  由于 API 不断添加到 WebView2，因此也发布了新版本的运行时以支持新的 API。  使用功能检测确保安装在客户端上的 WebView2 运行时支持 WebView2 应用使用的较新的 API。

如果使用 Evergreen WebView2 运行时，在某些情况下，客户端上的运行时尚未自动更新到最新版本。  例如，如果客户端没有 Internet 访问权限，则运行时不会自动更新。  此外，某些组策略会暂停运行时的更新。  将更新推送到 WebView2 应用时，如果应用尝试调用客户端安装运行时中不可用的较新 API，该应用可能无法运行。

若要解决此问题，在代码调用最近添加的 WebView2 API 之前，测试该 API 在客户端的安装运行时中是否可用。  此较新功能测试与其他 Web 开发最佳实践类似，这些最佳实践在使用新的 Web API 之前检测支持的功能。  若要测试已安装运行时中的 API 可用性，请使用：

*   `QueryInterface` 在 C/C++ 中。
*   `try/catch`.NET 或 WinUI 中的块。

有关详细信息，请导航到功能[检测以测试安装的运行时是否支持最近添加的 API。](../concepts/versioning.md#feature-detecting-to-test-whether-the-installed-runtime-supports-recently-added-apis)


<!-- ====================================================================== -->
## <a name="update-the-fixed-version-runtime"></a>更新固定版本运行时

如果使用固定版本的 WebView2 运行时，请确保定期更新与应用打包的 WebView2 运行时，以减少安全风险。  在 Webview2 应用中使用第三方内容时，始终考虑不受信任的内容。  有关详细信息，请导航到"[固定版本分发模式"。](../concepts/distribution.md#details-about-the-fixed-version-runtime-distribution-mode)


<!-- ====================================================================== -->
## <a name="manage-new-versions-of-the-evergreen-runtime"></a>管理新版本的 Evergreen Runtime

将新版本的 Evergreen WebView2 运行时下载到客户端后，正在运行的任何 WebView2 应用将继续使用早期版本的运行时，直到发布浏览器进程。  此行为允许应用连续运行，并阻止删除以前的运行时。  若要使用新版本的运行时，需要释放对以前的 WebView2 环境对象的所有引用，或重新启动应用。  下次应用创建新的 WebView2 环境时，应用将使用新版本的运行时。

当新版本的运行时可用时，你的应用可以自动采取措施，例如通知用户重新启动该应用。  若要检测新版本的运行时是否可用，可以在代码中使用 [add_NewBrowserVersionAvailable (Win32) ](/microsoft-edge/webview2/reference/win32/icorewebview2environment#add_newbrowserversionavailable) 或 [CoreWebView2Environment.NewBrowserVersionAvailable (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.newbrowserversionavailable) 事件。  如果你的代码处理重新启动应用，请考虑在 WebView2 应用退出之前保存用户状态。

<!-- are the Ref links enough, or link to a regular article or article subsection? -->


<!-- ====================================================================== -->
## <a name="manage-the-lifetime-of-the-user-data-folder"></a>管理用户数据文件夹的生命周期

WebView2 应用创建用户数据文件夹来存储 Cookie、凭据和权限等数据。  创建文件夹后，应用负责管理用户数据文件夹的生命周期。  例如，卸载应用时，你的应用必须执行清理操作。  有关详细信息，请导航到["管理用户数据文件夹"。](../concepts/user-data-folder.md)


<!-- ====================================================================== -->
## <a name="handle-runtime-process-failures"></a>处理运行时进程故障

WebView2 应用应侦听和处理事件，以便该应用可以从支持 WebView2 应用进程的运行时进程故障 `ProcessFailed` 中恢复。

与应用进程一起运行的运行时进程集合支持 WebView2 应用。  这些支持运行时进程可能由于各种原因（如内存不足或用户终止）而失败。  当支持运行时进程失败时，WebView2 将通过引发 [ProcessFailed 事件通知应用](/microsoft-edge/webview2/reference/win32/icorewebview2processfailedeventargs)。

<!-- is the Ref link enough, or link to a long section in regular docs? -->


<!-- ====================================================================== -->
## <a name="event-handlers-on-the-environment-object"></a>环境对象上的事件处理程序

如果环境对象上的应用的任何事件处理程序包含对环境对象的[](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environment)引用，并且应用只是释放对环境和事件处理程序的引用而不删除事件处理程序，则环境对象和处理程序对象之间可能会存在循环引用，这将泄漏内存。

为了防止此类内存泄露：
*  对于任何添加的事件处理程序，在释放环境对象之前删除事件处理程序。
*  避免在事件处理程序中持有对环境对象的引用。  相反，事件处理程序可以从"已完成事件"回调的参数访问 `sender` 环境对象。
*  如果希望应用保留对 WebView2 对象的引用，请尽可能使用弱引用。


<!-- ====================================================================== -->
## <a name="follow-recommended-webview2-security-best-practices"></a>遵循建议的 WebView2 安全性最佳做法

对于任何 WebView2 应用，请确保遵循我们建议的 WebView2 安全性最佳做法。  有关详细信息，请导航到 [Best practices for developing secure WebView2 applications](../concepts/security.md)。
