---
title: WebView2 应用的开发最佳做法
description: 了解开发 WebView2 应用程序时要使用的开发最佳做法。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 08/03/2021
ms.openlocfilehash: 1dd436d0ba1e2cdc7ce3b5be406dcb4886a4cde9
ms.sourcegitcommit: 205a858d62e3ca1162251e4c3b2bd621b9f0f04c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/07/2022
ms.locfileid: "12472815"
---
# <a name="development-best-practices-for-webview2-apps"></a>WebView2 应用的开发最佳做法

每个开发团队在构建应用程序时都遵循不同的做法。  生成 WebView2 生产应用时，建议遵循这些建议和最佳做法。


<!-- ====================================================================== -->
## <a name="use-the-evergreen-runtime-recommended"></a>使用常青运行时 (推荐) 

我们通常建议使用 Evergreen WebView2 运行时。  仅对于具有严格兼容性要求的应用，建议使用固定版本运行时分发。  Evergreen 运行时会在客户端上自动更新，以便 WebView2 应用可以使用最新的功能和安全修补程序。  与固定版本运行时相比，常青运行时还需要更少的磁盘存储空间。

如果使用 Evergreen 运行时，在运行 WebView2 应用之前，请测试是否在客户端上安装了 Evergreen WebView2 运行时。  请参阅 [部署 Evergreen WebView2 运行时](../concepts/distribution.md#deploying-the-evergreen-webview2-runtime)。

<!-- ====================================================================== -->
## <a name="run-compatibility-tests-regularly-when-using-the-evergreen-runtime"></a>使用常青运行时定期运行兼容性测试

使用 Evergreen WebView2 运行时时，运行时会自动更新，因此必须定期运行兼容性测试。  若要确保 WebView2 应用继续按预期工作，请在 WebView2 控件中针对 [Microsoft Edge 预览体验成员 (预览版) 频道 (](https://www.microsoftedgeinsider.com/download) Beta、Dev 或 Canary) 测试 Web 内容。

此指南类似于我们为 Web 开发人员提供指南。  请参阅 ["测试应用"以获取前向兼容性](../concepts/distribution.md#test-your-app-for-forward-compatibility)。


<!-- ====================================================================== -->
## <a name="test-whether-newer-apis-are-supported-by-the-installed-webview2-runtime"></a>测试已安装的 WebView2 运行时是否支持较新的 API

<!-- the main section about QueryInterface is in versioning.md; this section should be only a couple paragraphs -->

若要运行使用特定版本的 Webview2 SDK 开发的 WebView2 应用，客户端必须安装兼容版本的 WebView2 运行时。  由于 API 不断添加到 WebView2，因此还会发布运行时的新版本以支持新的 API。  使用功能检测确保 WebView2 应用使用的较新 API 受客户端上安装的 WebView2 运行时的支持。

如果使用 Evergreen WebView2 运行时，在某些情况下，客户端上的运行时尚未自动更新到最新版本。  例如，如果客户端没有 Internet 访问权限，则不会自动更新运行时。

此外，某些组策略会暂停运行时的更新。  将更新推送到 WebView2 应用时，如果应用尝试调用客户端安装的运行时中不可用的较新的 API，则该应用可能无法正常工作。

若要解决此问题，在代码调用最近添加的 WebView2 API 之前，请测试该 API 是否在客户端安装的运行时中可用。  此针对较新功能的测试类似于使用新的 Web API 之前检测受支持功能的其他 Web 开发最佳做法。  若要测试已安装运行时的 API 可用性，请使用以下任一项：

*  `QueryInterface` 在 C/C++ 中。
*  `try/catch`.NET 或 WinUI 中的块。

请参阅 [功能检测，以测试已安装的运行时是否支持最近添加的 API](../concepts/versioning.md#feature-detecting-to-test-whether-the-installed-runtime-supports-recently-added-apis)。


<!-- ====================================================================== -->
## <a name="update-the-fixed-version-runtime"></a>更新固定版本运行时

如果使用固定版本 WebView2 运行时，请确保定期更新随应用打包的 WebView2 运行时，以降低安全风险。  在 Webview2 应用中使用第三方内容时，始终认为内容不受信任。  请参阅 [固定版本分发模式](../concepts/distribution.md#details-about-the-fixed-version-runtime-distribution-mode)。


<!-- ====================================================================== -->
## <a name="manage-new-versions-of-the-evergreen-runtime"></a>管理长青运行时的新版本

将 Evergreen WebView2 运行时的新版本下载到客户端时，运行的任何 WebView2 应用将继续使用之前版本的运行时，直到发布浏览器进程。  此行为允许应用持续运行，并防止删除以前的运行时。  若要使用运行时的新版本，需要释放对以前的 WebView2 环境对象的所有引用，或者重启应用。  下次应用创建新的 WebView2 环境时，应用将使用新版本的运行时。

当新版本的运行时可用时，应用可以自动采取措施，例如通知用户重启应用。  若要检测运行时的新版本是否可用，可以在代码中使用 [add_NewBrowserVersionAvailable (Win32) ](/microsoft-edge/webview2/reference/win32/icorewebview2environment#add_newbrowserversionavailable) 或 [CoreWebView2Environment.NewBrowserVersionAvailable (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.newbrowserversionavailable) 事件。  如果代码处理重新启动应用，请考虑在 WebView2 应用退出之前保存用户状态。

<!-- are the Ref links enough, or link to a regular article or article subsection? -->


<!-- ====================================================================== -->
## <a name="manage-the-lifetime-of-the-user-data-folder"></a>管理用户数据文件夹的生存期

WebView2 应用创建用户数据文件夹来存储 Cookie、凭据和权限等数据。  创建文件夹后，应用负责管理用户数据文件夹的生存期。  例如，在卸载应用时，应用必须进行清理。  请参阅 ["管理用户数据"文件夹](../concepts/user-data-folder.md)。


<!-- ====================================================================== -->
## <a name="handle-runtime-process-failures"></a>处理运行时进程失败

WebView2 应用应侦听和处理 `ProcessFailed` 事件，以便应用可以从支持 WebView2 应用进程的运行时进程故障中恢复。

与应用进程一起运行的运行时进程集合支持 WebView2 应用。  这些支持运行时进程可能由于各种原因而失败，例如内存不足或被用户终止。  当支持运行时进程失败时，WebView2 通过引发 [ProcessFailed 事件](/microsoft-edge/webview2/reference/win32/icorewebview2processfailedeventargs)通知应用。

<!-- is the Ref link enough, or link to a long section in regular docs? -->


<!-- ====================================================================== -->
## <a name="event-handlers-on-the-environment-object"></a>环境对象上的事件处理程序

如果 [环境对象](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environment) 上的任何应用的事件处理程序都持有对环境对象的引用，并且应用只需释放对环境和事件处理程序的引用而不删除事件处理程序，则环境对象和处理程序对象之间可能会有循环引用，这会泄漏内存。

若要防止此类内存泄漏，请执行以下操作：

*  对于任何添加的事件处理程序，请在释放环境对象之前删除事件处理程序。

*  避免在事件处理程序中保存对环境对象的引用。  相反，事件处理程序可以从 `sender` "事件已完成"回调的参数访问环境对象。

*  如果希望应用保存对 WebView2 对象的引用，请尽可能使用弱引用。


<!-- ====================================================================== -->
## <a name="follow-recommended-webview2-security-best-practices"></a>遵循建议的 WebView2 安全最佳做法

对于任何 WebView2 应用，请务必遵循我们在 [开发安全 WebView2 应用](../concepts/security.md)中的建议。
