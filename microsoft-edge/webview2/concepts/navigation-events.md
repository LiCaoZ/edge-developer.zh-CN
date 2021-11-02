---
description: 导航
title: 导航|WebView 2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/06/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、wpf 应用、wpf、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: 470324b1474019a758b6aa3b9b25378be9554ad2
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141507"
---
# <a name="navigation-events"></a>导航事件

支持的平台：Win32、Windows Forms、WinUi、WPF。

导航事件在 WebView2 实例中显示的内容发生特定异步操作时运行。  例如，当 WebView2 用户导航到新网站时，本机内容会使用 事件侦听 `NavigationStarting` 更改。  导航操作完成后，运行 `NavigationCompleted` 。  有关导航事件的良好示例，请导航到[WebView2][Webview2IndexGetStarted]入门指南。

<!--todo:  Move the relevant information out of the get started guide to better focus the content and leave the most concise elements in the get started guide.  -->

导航事件的正常顺序为 `NavigationStarting` `SourceChanged` 、、、 `ContentLoading` `HistoryChanged` 和 `NavigationCompleted` 。  以下事件描述每次导航期间 WebView2 的状态。

:::row:::
   :::column span="1":::
      :::image type="complex" source="../media/navigation-graph.png" alt-text="WebView2 Microsoft Edge事件" lightbox="../media/navigation-graph.png":::
         WebView2 Microsoft Edge事件 :::image-end:::

      > [!NOTE]
      > 该图表示导航事件，这些事件 `NavigationId` 在各自的 event 参数上具有相同的属性。
   :::column-end:::
   :::column span="2":::
      | Sequence | 事件名称 | 详细信息 |
      |:--- |:--- |:--- |
      | 1 | `NavigationStarting`  |  WebView2 开始导航，导航结果为网络请求。  在事件期间，主机可能会禁止该请求。  |
      | 2 | `SourceChanged`  |  WebView2 的源将更改到新的 URL。  该事件可能由不会导致网络请求（如片段导航）的导航操作导致。  |
      | 3 | `ContentLoading`  |  WebView 开始加载新页面的内容。  |
      | 4 | `HistoryChanged`  |  导航导致 WebView2 的历史记录更新。  |
      | 5 | `NavigationCompleted`  |  WebView2 完成新页面上的内容加载。  |
   :::column-end:::
:::row-end:::

使用导航 ID 跟踪每个新文档的导航事件 (`NavigationId` 事件) 。  每次 `NavigationId` 成功导航到新文档时，WebView 事件都会更改。

 具有不同事件实例的 `NavigationId` 导航事件可能会重叠。  例如，启动导航事件时，必须等待相关 `NavigationStarting` 事件。  如果随后启动另一个导航，则应该会看到第一个导航的事件，后跟第二个导航的事件，然后是第一个导航的事件，然后是第二个导航的所有其他相应导航事件。 `NavigationStarting` `NavigationStarting` `NavigationCompleted`

 在错误情况下，根据导航是否继续导航到错误页面，可能（也可能没有 `ContentLoading` ）事件。

 如果 HTTP 重定向发生，则一行中有多个事件，其中更高版本的事件参数设置了属性，但是 `NavigationStarting` `IsRedirect` `NavigationId` 该事件保持不变。

 相同的文档导航事件（如导航到片段）不会导致事件， `NavigationStarting` 并且不会增加 `NavigationId` 事件。

若要监视或取消 WebView2 实例中的子框架内的导航事件，请使用 和 事件，这些事件与等效的非 `FrameNavigationStarting` `FrameNavigationCompleted` 帧对应事件类似。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebView2 入门指南][Webview2IndexGetStarted]
*  [WebView2Samples 存储库][GithubMicrosoftedgeWebview2samples] - WebView2 功能的综合示例。
*  [WebView2 API 参考][DotnetApiMicrosoftWebWebview2WpfWebview2]
*  [另请参阅][Webview2IndexNextSteps] _WebView2 Microsoft Edge简介_。


<!-- ====================================================================== -->
<!-- links -->
[Webview2IndexGetStarted]: ../index.md#get-started "入门 - WebView2 Microsoft Edge简介|Microsoft Docs"
[Webview2IndexNextSteps]: ../index.md#see-also "另请参阅 - WebView2 Microsoft Edge简介|Microsoft Docs"

[DotnetApiMicrosoftWebWebview2WpfWebview2]: /dotnet/api/microsoft.web.webview2.wpf.webview2 "WebView2 类|Microsoft Docs"

[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"
