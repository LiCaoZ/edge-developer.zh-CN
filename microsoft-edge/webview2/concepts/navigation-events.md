---
title: WebView2 应用的导航事件
description: WebView2 的导航事件：NavigationStarting、SourceChanged、ContentLoading、HistoryChanged、DOMContentLoaded 和 NavigationCompleted。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/28/2021
ms.openlocfilehash: 5440985a0d70f329d6bbbc4ae6cc38c23808321d
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668711"
---
# <a name="navigation-events-for-webview2-apps"></a>WebView2 应用的导航事件
<!-- old title: # Navigation events for WebView2 -->

<!--
maintenance links (keep)
This, main page:
* [Navigation events for WebView2 apps](../concepts/navigation-events.md) - main copy; update it and then propagate/copy to these h2 sections:
Derivative copies of this page's content, or links to this page:
* [Get started with WebView2 in Win32 apps](../get-started/win32.md#step-12---navigation-events)
* [Get started with WebView2 in WinForms apps](../get-started/winforms.md#step-7---navigation-events)
* [Get started with WebView2 in WinUI 2 (UWP) apps](../get-started/winui2.md#step-7---navigation-events)
* [Get started with WebView2 in WinUI 3 (Windows App SDK) apps](../get-started/winui.md#step-7---navigation-events)
* [Get started with WebView2 in WPF apps](../get-started/wpf.md#step-6---navigation-events)
-->

支持的平台：Win32、Windows 窗体、WinUi、WPF。

本文介绍 WebView2 应用的导航事件。  当 WebView2 实例中显示的内容发生特定的异步操作时，会运行导航事件。  例如，当 WebView2 用户导航到新网站时，本机内容通过侦听事件来 `NavigationStarting` 侦听更改。  导航操作完成后， `NavigationCompleted` 运行。

有关导航事件的示例，请参阅 [WebView2 入](../get-started/get-started.md)门。

导航事件的正常顺序是：
1. `NavigationStarting`
1. `SourceChanged`
1. `ContentLoading`
1. `HistoryChanged`
1. `BasicAuthenticationRequested`
1. `DOMContentLoaded`
1. `NavigationCompleted`


以下事件描述每个导航操作期间 WebView2 的状态：

![WebView2 导航事件。](../media/navigation-graph.png)

| 序列 | 事件名称 | 详细信息 |
| --- | --- | --- |
| 1 | `NavigationStarting` |  WebView2 开始导航，导航生成网络请求。  主机可能会在事件期间禁止请求。 |
| 2 | `SourceChanged` |  WebView2 的源更改为新 URL。  该事件可能是由于不导致网络请求（如片段导航）的导航操作导致的。 |
| 3 | `ContentLoading` |  WebView2 开始加载新页面的内容。 |
| 4 | `HistoryChanged` |  导航会导致 WebView2 的历史记录更新。 |
| 5 | `DOMContentLoaded` |  WebView2 完成对 DOM 内容的分析，但尚未完成加载页面上的所有图像、脚本和其他内容。 |
| 6 | `NavigationCompleted` |  WebView2 完成在新页面上加载内容。 |

上图显示了在相应事件参数上具有相同 `NavigationId` 属性的导航事件。

使用事件) 中提供的导航 ID (跟踪每个新文档的 `NavigationId` 导航事件。  `NavigationId`每次成功导航到新文档时，WebView2 事件都会更改。

具有不同事件实例的 `NavigationId` 导航事件可能重叠。  例如，启动导航事件时，必须等待相关 `NavigationStarting` 事件。  如果随后启动另一个导航，则会看到以下顺序：
1. `NavigationStarting`第一个导航的事件。
1. 第 `NavigationStarting` 二个导航的事件。
1. `NavigationCompleted`第一个导航的事件。
1. 第二个导航的所有相应导航事件的其余部分。

在错误情况下，可能存在或可能不会发生 `ContentLoading` 事件，具体取决于导航是否继续到错误页面。

如果发生 HTTP 重定向，则一行中有多个 `NavigationStarting` 事件，其中以后的事件参数具有 `IsRedirect` 属性集;但是， `NavigationId` 该事件保持不变。

同一`NavigationStarting`文档导航事件（例如导航到同一文档中的片段）不会导致事件，也不会增加事件。`NavigationId`

若要监视或取消 WebView2 实例中子帧中的导航事件，请使用这些 `FrameNavigationStarting` 事件和 `FrameNavigationCompleted` 事件。  这些事件的行为类似于等效的非帧对应事件。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
* [另请参阅](../index.md#see-also) _Microsoft Edge WebView2 简介_。
