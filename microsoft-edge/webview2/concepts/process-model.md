---
title: WebView2 进程模型
description: WebView2 运行时进程模型，以及它如何使用用户数据文件夹和网站隔离。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 09/21/2021
ms.openlocfilehash: ccc9dd0ea22a21aa19e5f53db3b1ebb80f9d9cf1
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345749"
---
# <a name="the-webview2-process-model"></a>WebView2 进程模型

支持的平台：Win32、Windows Forms、WinUI、WPF。

WebView2 运行时使用与浏览器相同的Microsoft Edge模型。  此浏览器过程模型在内部 [查看新式 Web 浏览器 (第 1 部分 ](https://developers.google.com/web/updates/2018/09/inside-browser-part1#browser-architecture)) 。


<!-- ====================================================================== -->
## <a name="processes-in-the-webview2-runtime"></a>WebView2 运行时中的进程

_WebView2 进程组_是 WebView2 运行时进程的集合。  WebView2 进程组包括以下内容：
*  单个浏览器进程。
*  一个或多个呈现器进程。
*  其他帮助程序进程，如 GPU 进程和音频服务进程。

:::image type="content" source="../media/process-model-1.png" alt-text="进程 1。" lightbox="../media/process-model-1.png":::

当 WebView2 应用程序使用 WebView2 功能时，WebView2 进程组中进程的数量和状态可能会发生变化。   (但是，WebView2 进程组中只有一个特定的浏览器进程。例如，) 例如，从同一个 ，但在 属性中使用不同的域创建新 WebView`CoreWebView2Environment``Source`，通常会启动一个新的呈现器进程。

呈现器进程的数量可能因以下条件而异：

*  使用 WebView2 _运行时_ 中的网站隔离功能。  请参阅 [每帧呈现器进程 - 网站隔离](https://developers.google.com/web/updates/2018/09/inside-browser-part1#site-isolation)。

*  使用同一用户数据文件夹的 WebView2 实例中呈现的已断开连接源的数量。

控制何时创建这些额外进程的逻辑取决于Chromium体系结构，超出了 WebView2 运行时的范围。


<!-- ====================================================================== -->
## <a name="webview2-runtime-processes-and-the-user-data-folder"></a>WebView2 运行时进程和用户数据文件夹

WebView2 运行时进程集合中所有进程都绑定到浏览器进程，而浏览器进程又与单个用户数据文件夹关联。  如果应用程序使用多个用户数据文件夹，将针对每个用户数据文件夹创建一个 WebView2 运行时进程集合。

用户数据文件夹可以由多个应用程序共享，但请务必考虑对性能和管理的影响，如管理用户 [数据文件夹中所述](./user-data-folder.md)。

:::image type="content" source="../media/process-model-2.png" alt-text="进程 2." lightbox="../media/process-model-2.png":::

若要使用多个用户数据文件夹，WebView2 应用程序需要创建不同的 `CoreWebView2Environment` 对象。  通过 `WebView2` 配置的对象为给定用户数据文件夹创建实例 `CoreWebView2Environment` 。  每个 `CoreWebView2Environment` 对象都需要使用不同的用户数据文件夹值进行配置。

当为给定的 `WebView2` 用户数据文件夹创建第一个实例时，将启动 WebView2 运行时处理与该用户数据文件夹关联的集合的浏览器进程。  所有其他进程都将在浏览器进程的生命周期内进行管理。

<!-- TODO: update with profile info -->
`CoreWebView2Environment`表示用户数据文件夹及其关联的进程集合。  给定呈现器进程不与`CoreWebView2``CoreWebView2`单个实例关联，因为呈现器进程可以在使用相同用户数据文件夹的多个实例中为帧提供服务，具体取决于网站隔离。  请参阅 [每帧呈现器进程 - 网站隔离](https://developers.google.com/web/updates/2018/09/inside-browser-part1#site-isolation)。


<!-- ====================================================================== -->
## <a name="handling-process-events-and-lifetime"></a>处理进程事件和生存期

若要对浏览器和呈现器进程中的崩溃和挂起做出反应，请使用 `ProcessFailed` 的 事件 `CoreWebView2`。

<!-- todo: add info about the new APIs BrowserProcessExited and ProcessInfo -->

若要安全关闭关联的浏览器和呈现器进程，请使用 `Close` 的 方法 `CoreWebView2Controller`。

若要从 WebView2 实例的 **DevTools** 窗口打开浏览器任务管理器窗口，请右键单击 DevTools 窗口标题栏，然后选择 `Browser task manager`。****  或者，按 `Shift`+`Escape`。

将显示与 WebView2 的浏览器进程关联的所有进程，包括其关联目的。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [内部查看新式 Web 浏览器 (第 1) ](https://developers.google.com/web/updates/2018/09/inside-browser-part1#browser-architecture) 部分 - WebView2 运行时和 Microsoft Edge 使用的浏览器进程模型。
* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
