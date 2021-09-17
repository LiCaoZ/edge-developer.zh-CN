---
description: WebView2 进程模型。
title: WebView2 进程模型
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/06/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、wpf 应用、wpf、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: 407c532d7492bac7769c3186905e7a917d3f2fcd
ms.sourcegitcommit: 5113e8f2d6823239911d8a7fed64d9652a96c26e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2021
ms.locfileid: "12018531"
---
# <a name="the-webview2-process-model"></a>WebView2 进程模型

支持的平台：Win32、Windows Forms、WinUI、WPF。

WebView2 运行时使用与浏览器相同的Microsoft Edge模型。  此浏览器过程模型在新式 Web 浏览器的内部外观 [ (第 1 部分 ][GoogleDeveloperWebUpdates201809InsideBrowserPart1BrowserArchitecture]) 。


<!-- ====================================================================== -->
## <a name="processes-in-the-webview2-runtime"></a>WebView2 运行时中的进程

WebView2 运行时进程的集合（或 WebView2 进程组）由以下进程组成：
*  单个浏览器进程。
*  一个或多个呈现进程。
*  其他帮助程序进程，如 GPU 进程和音频服务进程。

:::image type="complex" source="../media/process-model-1.png" alt-text="进程 1" lightbox="../media/process-model-1.png":::
   进程 1
:::image-end:::

除了浏览器进程外，当 WebView2 应用程序使用 WebView2 功能时，此集合中进程的数量和状态可能会更改。  例如，使用 属性中的不同域从同一 WebView 创建新的 WebView `CoreWebView2Environment` `Source` 通常会启动一个新的呈现器进程。  控制何时创建这些额外进程的逻辑取决于Chromium体系结构，超出了 WebView2 运行时的范围。

例如，呈现器进程数因以下条件而异：
*   使用 WebView2 _运行时_ 中的网站隔离功能。  请参阅 [每帧呈现器进程 - 网站隔离](https://developers.google.com/web/updates/2018/09/inside-browser-part1#site-isolation)。
*   使用同一用户数据文件夹的 WebView2 实例中呈现的已断开连接源的数量。


<!-- ====================================================================== -->
## <a name="webview2-runtime-processes-and-the-user-data-folder"></a>WebView2 运行时进程和用户数据文件夹

WebView2 运行时进程集合中所有进程都绑定到浏览器进程，浏览器进程又与 UDF (单个用户数据文件夹) 。  如果应用程序使用多个用户数据文件夹，将针对每个用户数据文件夹创建一个 WebView2 运行时进程集合。

用户数据文件夹可以由多个应用程序共享，但请务必考虑对性能和管理的影响，如管理用户 [数据文件夹中所述][WebView2ManageUDF]。

:::image type="complex" source="../media/process-model-2.png" alt-text="过程 2" lightbox="../media/process-model-2.png":::
   过程 2
:::image-end:::

若要使用多个用户数据文件夹，WebView2 应用程序需要创建不同的 `CoreWebView2Environment` 对象。  通过 `WebView2` 配置的对象为给定用户数据文件夹创建 `CoreWebView2Environment` 实例。  每个 `CoreWebView2Environment` 对象都需要使用不同的用户数据文件夹值进行配置。

当为给定用户数据文件夹创建第一个实例时，将启动 `WebView2` WebView2 运行时处理与该 UDF 关联的集合的浏览器进程。  所有其他进程都将在浏览器进程的生命周期内进行管理。

<!-- TODO: update with profile info -->
`CoreWebView2Environment`表示用户数据文件夹及其关联的进程集合。  给定呈现器进程不与单个实例关联，因为呈现器进程可以在使用相同用户数据文件夹的多个实例中为帧提供服务， `CoreWebView2` `CoreWebView2` 具体取决于网站隔离。  请参阅 [每帧呈现器进程 - 网站隔离](https://developers.google.com/web/updates/2018/09/inside-browser-part1#site-isolation)。


<!-- ====================================================================== -->
## <a name="handling-process-events-and-lifetime"></a>处理进程事件和生存期

若要对浏览器和呈现器进程中的崩溃和挂起做出反应，请使用 `ProcessFailed` 的 事件 `CoreWebView2` 。

若要安全关闭关联的浏览器和呈现器进程，请使用 的 `Close` 方法 `CoreWebView2Controller` 。

若要从**** WebView2 实例的**DevTools**窗口打开浏览器任务管理器窗口，请执行下列操作之一：
*   选择 `Shift`+`Escape`。
*   将鼠标悬停在 DevTools 窗口标题栏上，打开上下文菜单 (右键单击") "，然后选择 `Browser task manager` 。

将显示与 WebView2 的浏览器进程关联的所有进程，包括其关联目的。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [内部查看新式 Web 浏览器 (第 1) ][GoogleDeveloperWebUpdates201809InsideBrowserPart1BrowserArchitecture]部分 - WebView2 运行时和 Microsoft Edge 浏览器使用的浏览器进程模型。
*  [WebView2 入门指南][Webview2IndexGetStarted]
*  [WebView2Samples 存储库][GithubMicrosoftedgeWebview2samples] - WebView2 功能的综合示例。
*  [WebView2 API 参考][DotnetApiMicrosoftWebWebview2WpfWebview2]
*  [WebView2][Webview2IndexNextSteps] _简介中的Microsoft Edge步骤_。


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]


<!-- ====================================================================== -->
<!-- links -->
[Webview2IndexGetStarted]: ../index.md#get-started "入门 - WebView2 Microsoft Edge简介|Microsoft Docs"
[Webview2IndexNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 |Microsoft Docs"
[WebView2ManageUDF]: ./user-data-folder.md "管理用户数据文件夹 | Microsoft Docs"
<!-- external links -->
[DotnetApiMicrosoftWebWebview2WpfWebview2]: /dotnet/api/microsoft.web.webview2.wpf.webview2 "WebView2 类|Microsoft Docs"

[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"

[GoogleDeveloperWebUpdates201809InsideBrowserPart1BrowserArchitecture]: https://developers.google.com/web/updates/2018/09/inside-browser-part1#browser-architecture "内部查看新式 Web 浏览器 (第 1 部分) "
