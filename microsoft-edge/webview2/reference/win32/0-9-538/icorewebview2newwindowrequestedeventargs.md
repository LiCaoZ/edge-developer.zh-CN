---
description: 通过 Microsoft Edge WebView2 控件在 Win32 应用中托管 web 内容
title: 适用于 Win32 应用的 Microsoft Edge WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/05/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html
ms.openlocfilehash: af8df8ff67a0fbe7fd4ec9308b1562b9ef987933
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "10698571"
---
# interface ICoreWebView2NewWindowRequestedEventArgs 

```
interface ICoreWebView2NewWindowRequestedEventArgs
  : public IUnknown
```

Webview.newwindowrequested 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | 获取 NewWindowRequestedEvent 是否由 host 处理。
[get_IsUserInitiated](#get_isuserinitiated) | 通过用户笔势（如单击带有目标的定位点标记）启动新的窗口请求时，IsUserInitiated 为 true。
[get_NewWindow](#get_newwindow) | 获取新窗口。
[get_Uri](#get_uri) | NewWindowRequest 的目标 uri。
[GetDeferral](#getdeferral) | 获取[ICoreWebView2Deferral](icorewebview2deferral.md)对象并将事件置于延迟状态。
[put_Handled](#put_handled) | 设置 NewWindowRequestedEvent 是否由主机处理。
[put_NewWindow](#put_newwindow) | 将 Web 视图设置为 NewWindowRequest 的结果。

如果 web 视图中的内容请求打开一个新窗口（通过 "打开" （）等），将引发此事件。

## 成员

#### get_Handled 

获取 NewWindowRequestedEvent 是否由 host 处理。

> 公共 HRESULT [get_Handled](#get_handled)（BOOL * 已处理）

#### get_IsUserInitiated 

通过用户笔势（如单击带有目标的定位点标记）启动新的窗口请求时，IsUserInitiated 为 true。

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)（BOOL * IsUserInitiated）

#### get_NewWindow 

获取新窗口。

> 公共 HRESULT [get_NewWindow](#get_newwindow)（[ICoreWebView2](icorewebview2.md) * * NewWindow）

#### get_Uri 

NewWindowRequest 的目标 uri。

> 公共 HRESULT [get_Uri](#get_uri)（LPWSTR * Uri）

#### GetDeferral 

获取[ICoreWebView2Deferral](icorewebview2deferral.md)对象并将事件置于延迟状态。

> 公共 HRESULT [GetDeferral](#getdeferral)（[ICoreWebView2Deferral](icorewebview2deferral.md) * * 延迟）

你可以使用[ICoreWebView2Deferral](icorewebview2deferral.md)对象在以后的时间完成窗口打开请求。 当此事件延迟时，opener 窗口将返回到 unnavigated 窗口的 WindowProxy，该窗口将在延迟完成时进行导航。

#### put_Handled 

设置 NewWindowRequestedEvent 是否由主机处理。

> 公共的 HRESULT [put_Handled](#put_handled)（BOOL 已处理）

如果此参数为 false 且未设置 NewWindow，则 Web 视图将打开一个弹出窗口，并且该窗口将以打开的 WindowProxy 的形式返回。 如果设置为 true 且没有为窗口设置 NewWindow，则打开的 WindowProxy 将针对虚拟窗口对象，并且不会加载任何窗口。 默认值为 false。

#### put_NewWindow 

将 Web 视图设置为 NewWindowRequest 的结果。

> 公共 HRESULT [put_NewWindow](#put_newwindow)（[ICoreWebView2](icorewebview2.md) * NewWindow）

不应导航目标 web 视图。 如果设置了 NewWindow，其顶级窗口将返回为打开的 WindowProxy。
