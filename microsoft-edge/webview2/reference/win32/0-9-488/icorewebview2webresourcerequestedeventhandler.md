---
description: 通过 Microsoft Edge WebView2 控件在 Win32 应用中托管 web 内容
title: 适用于 Win32 应用的 Microsoft Edge WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/07/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html
ms.openlocfilehash: 2f3effd612303d1532c7220d566791a800753b37
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "10652842"
---
# interface ICoreWebView2WebResourceRequestedEventHandler 

```
interface ICoreWebView2WebResourceRequestedEventHandler
  : public IUnknown
```

在 web 视图中发出 HTTP 请求时激发。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[调用](#invoke) | 调用以向实施者提供对应事件的事件参数。

主机可以替代请求、响应标头和响应内容。

## 成员

#### 调用 

调用以向实施者提供对应事件的事件参数。

> 公共 HRESULT[调用](#invoke)（[ICoreWebView2](icorewebview2.md) * sender、 [ICoreWebView2WebResourceRequestedEventArgs](icorewebview2webresourcerequestedeventargs.md) * 参数）
