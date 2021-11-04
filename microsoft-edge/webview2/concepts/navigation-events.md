---
description: WebView2 的导航事件：NavigationStarting、SourceChanged、ContentLoading、HistoryChanged、DOMContentLoaded 和 NavigationCompleted。
title: WebView2 的导航事件
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、wpf 应用、wpf、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: a2ffac5b3061094e30636b553b2c2dfd0f4c30ff
ms.sourcegitcommit: 5c9e13989cd2ea1598c8ce69192babe63ab78ac3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12154946"
---
# <a name="navigation-events-for-webview2"></a>WebView2 的导航事件

支持的平台：Win32、Windows Forms、WinUi、WPF。

导航事件在 WebView2 实例中显示的内容发生特定异步操作时运行。  例如，当 WebView2 用户导航到新网站时，本机内容通过侦听事件来侦听 `NavigationStarting` 更改。  导航操作完成后，运行 `NavigationCompleted` 。  有关导航事件的良好示例，请参阅 [入门](../index.md#get-started)。

<!--todo:  Move the relevant information out of the get started guide to better focus the content and leave the most concise elements in the get started guide.  -->

导航事件的正常顺序为：
1. `NavigationStarting`
1. `SourceChanged`
1. `ContentLoading`
1. `HistoryChanged`
1. `DOMContentLoaded`
1. `NavigationCompleted`

以下事件描述每次导航操作期间 WebView2 的状态：

:::row:::
   :::column span="1":::
      :::image type="content" source="../media/navigation-graph.png" alt-text="WebView2 Microsoft Edge事件。" lightbox="../media/navigation-graph.png":::
   :::column-end:::
   :::column span="2":::
      | Sequence | 事件名称 | 详细信息 |
      |:--- |:--- |:--- |
      | 1 | `NavigationStarting` |  WebView2 开始导航，导航结果为网络请求。  在事件期间，主机可能会禁止该请求。 |
      | 2 | `SourceChanged` |  WebView2 的源将更改到新的 URL。  该事件可能由不会导致网络请求（如片段导航）的导航操作导致。 |
      | 3 | `ContentLoading` |  WebView2 开始加载新页面的内容。 |
      | 4 | `HistoryChanged` |  导航导致 WebView2 的历史记录更新。 |
      | 5 | `DOMContentLoaded` |  WebView2 已完成对 DOM 内容进行分析，但尚未在页面上加载所有图像、脚本和其他内容。 |
      | 6 | `NavigationCompleted` |  WebView2 完成新页面上的内容加载。 |
   :::column-end:::
:::row-end:::

上图显示了在各自的事件参数上具有相同的属性 `NavigationId` 的导航事件。

使用事件记录中提供的导航 ID (跟踪每个新文档的 `NavigationId` 导航) 。  `NavigationId`每次成功导航到新文档时，WebView2 的事件都会更改。

具有不同事件实例的 `NavigationId` 导航事件可能会重叠。  例如，启动导航事件时，必须等待相关 `NavigationStarting` 事件。  如果随后启动另一个导航，你将看到以下序列：
1. 第 `NavigationStarting` 一个导航的事件。
1. 第 `NavigationStarting` 二个导航的事件。
1. 第 `NavigationCompleted` 一个导航的事件。
1. 第二个导航的所有其他相应导航事件。

在错误情况下，可能（也可能没有）事件， `ContentLoading` 具体取决于导航是否继续导航到错误页面。

如果发生 HTTP 重定向，则一行中有多个事件，其中更高版本的事件参数设置了属性;但是， `NavigationStarting` `IsRedirect` `NavigationId` 该事件保持不变。

同文档导航事件（如导航到同一文档中的片段）不会导致事件，并且 `NavigationStarting` 不会增加 `NavigationId` 事件。

若要监视或取消 WebView2 实例中的子框架内的导航事件，请使用 和 `FrameNavigationStarting` `FrameNavigationCompleted` 事件。  这些事件与等效的非帧对应事件类似。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebView2 入门指南](../index.md#get-started)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
