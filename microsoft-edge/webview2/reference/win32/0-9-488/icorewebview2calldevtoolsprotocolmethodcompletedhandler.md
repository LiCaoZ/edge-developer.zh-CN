---
description: 通过 Microsoft Edge WebView2 控件在 Win32 应用中托管 web 内容
title: 适用于 Win32 应用的 Microsoft Edge WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/28/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html
ms.openlocfilehash: fda3ab31405a7d6353af1a670a2804e973577c8e
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653010"
---
# interface ICoreWebView2CallDevToolsProtocolMethodCompletedHandler 

```
interface ICoreWebView2CallDevToolsProtocolMethodCompletedHandler
  : public IUnknown
```

调用方实现此接口以接收 CallDevToolsProtocolMethod 完成结果。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[调用](#invoke) | 调用以向实施者提供相应的异步方法调用的完成状态和结果。

## 成员

#### 调用 

调用以向实施者提供相应的异步方法调用的完成状态和结果。

> 公共 HRESULT[调用](#invoke)（hresult ERRORCODE，LPCWSTR returnObjectAsJson）
