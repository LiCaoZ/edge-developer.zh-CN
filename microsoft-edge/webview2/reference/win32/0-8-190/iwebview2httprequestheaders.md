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
ms.openlocfilehash: aea00f37f28034e1b7a33d4fd11c5ed78f779d00
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653092"
---
# interface IWebView2HttpRequestHeaders 

> [!NOTE]
> 此接口可能会在 SDK 版本0.8.355 后更改或不可用。 请参阅[参考](../../../webview2-api-reference.md)了解最新的 API 参考。

```
interface IWebView2HttpRequestHeaders
  : public IUnknown
```

HTTP 请求标头。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[GetHeader](#getheader) | 获取与名称匹配的标头值。
[Contains](#contains) | 检查标题是否包含与标头名称匹配的条目。
[SetHeader](#setheader) | 添加或更新与名称匹配的标题。
[RemoveHeader](#removeheader) | 删除与名称匹配的标题。
[GetIterator](#getiterator) | 获取请求标头集合上的迭代器。

用于检查 WebResourceRequested 事件和 NavigationStarting 事件上的 HTTP 请求。 注意，你可以从 WebResourceRequested 事件（而不是从 NavigationStarting 事件）修改 HTTP 请求标头。

## 成员

#### GetHeader 

获取与名称匹配的标头值。

> 公共 HRESULT [GetHeader](#getheader)（LPCWSTR NAME，LPWSTR * value）

#### Contains 

检查标题是否包含与标头名称匹配的条目。

> public HRESULT[包含](#contains)（LPCWSTR NAME，BOOL * 包含）

#### SetHeader 

添加或更新与名称匹配的标题。

> 公共 HRESULT [SetHeader](#setheader)（LPCWSTR NAME，LPCWSTR 值）

#### RemoveHeader 

删除与名称匹配的标题。

> 公共 HRESULT [RemoveHeader](#removeheader)（LPCWSTR name）

#### GetIterator 

获取请求标头集合上的迭代器。

> 公共 HRESULT [GetIterator](#getiterator)（[IWebView2HttpHeadersCollectionIterator](IWebView2HttpHeadersCollectionIterator.md) * * 迭代器）
