---
description: '通过 Microsoft Edge WebView2 控件在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) '
title: CoreWebView2NavigationCompletedEventArgs 中的 WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/10/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、Core、WebView2、web 视图、新、wpf、winforms、app、edge、CoreWebView2、CoreWebView2Controller、浏览器控件、边缘 html、、浏览器控件、边缘 html、WebView2
ms.openlocfilehash: dfa6aedb10e60a2af15c7b098c479f8537d6c747
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "11011630"
---
# CoreWebView2NavigationCompletedEventArgs 类的 WebView2 

命名空间： Microsoft WebView2 \
程序集： Microsoft.Web.WebView2.Core.dll

NavigationCompleted 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[IsSuccess](#issuccess) | 导航成功时为 True。
[NavigationId](#navigationid) | 导航的 ID。
[WebErrorStatus](#weberrorstatus) | 导航失败时的错误代码。

## 成员

#### IsSuccess 

导航成功时为 True。

> 公共 bool [IsSuccess](#issuccess)

这对于在错误页面中结束的导航是错误的，因为没有网络、DNS 查找失败、HTTP 服务器通过 4xx) 做出响应，但对于诸如 window 之类的其他方案也可能是 false (。停止在导航页上调用 ( # A3。

#### NavigationId 

导航的 ID。

> 公共 ulong [NavigationId](#navigationid)

#### WebErrorStatus 

导航失败时的错误代码。

> 公共 CoreWebView2WebErrorStatus [WebErrorStatus](#weberrorstatus)
