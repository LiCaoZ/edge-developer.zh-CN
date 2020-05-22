---
description: 通过 Microsoft Edge WebView2 控件在 Win32 应用中托管 web 内容
title: 适用于 Win32 应用的 Microsoft Edge WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/09/2019
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge
ms.openlocfilehash: 0314c796865d3d745b831d050498f59868e38e8f
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653140"
---
# interface IWebView2NewVersionAvailableEventArgs 

> [!NOTE]
> 此接口可能会在 SDK 版本0.8.355 后更改或不可用。 请参阅[参考](../../../webview2-api-reference.md)了解最新的 API 参考。

```
interface IWebView2NewVersionAvailableEventArgs
  : public IUnknown
```

NewVersionAvailable 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[get_NewVersion](#get_newversion) | 当前[IWebView2Environment](IWebView2Environment.md)的浏览器版本信息。

## 成员

#### get_NewVersion 

当前[IWebView2Environment](IWebView2Environment.md)的浏览器版本信息。

> 公共 HRESULT [get_NewVersion](#get_newversion)（LPWSTR * 新版）
