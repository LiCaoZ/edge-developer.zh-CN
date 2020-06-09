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
ms.openlocfilehash: 54e2c06ef65f64560fbd5687148eace253352203
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "10698419"
---
# CoreWebView2NewWindowRequestedEventArgs 类的 WebView2 

命名空间： Microsoft WebView2 \
程序集： Microsoft WebView2

Webview.newwindowrequested 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[Handled](#handled) | NewWindowRequestedEvent 是否由主机处理。
[IsUserInitiated](#isuserinitiated) | 通过用户笔势（如单击带有目标的定位点标记）启动新的窗口请求时，IsUserInitiated 为 true。
[NewWindow](#newwindow) | 获取新窗口。
[Uri](#uri) | NewWindowRequest 的目标 uri。
[WindowFeatures](#windowfeatures) | 窗口指定的窗口功能。打开通话。
[GetDeferral](#getdeferral) | 获取 CoreWebView2Deferral 对象并将事件置于延迟状态。

如果 web 视图中的内容请求打开一个新窗口（通过 "打开" （）等），将引发此事件。

## 成员

#### Handled 

NewWindowRequestedEvent 是否由主机处理。

> 公共 bool 已[处理](#handled)

如果此参数为 false 且未设置 NewWindow，则 Web 视图将打开一个弹出窗口，并且该窗口将以打开的 WindowProxy 的形式返回。 如果设置为 true 且没有为窗口设置 NewWindow，则打开的 WindowProxy 将针对虚拟窗口对象，并且不会加载任何窗口。 默认值为 false。

#### IsUserInitiated 

通过用户笔势（如单击带有目标的定位点标记）启动新的窗口请求时，IsUserInitiated 为 true。

> 公共 bool [IsUserInitiated](#isuserinitiated)

#### NewWindow 

获取新窗口。

> 公共 CoreWebView2 [NewWindow](#newwindow)

#### Uri 

NewWindowRequest 的目标 uri。

> 公共字符串[Uri](#uri)

不应导航目标 web 视图。 如果设置了 NewWindow，其顶级窗口将返回为打开的 WindowProxy。

#### WindowFeatures 

> [!NOTE]
> 这是我们的 SDK 版本[0.9.538](../../../releasenotes.md#09538)预发布版附带的[实验性 API](../../../concepts/versioning.md#experimental-apis) 。

窗口指定的窗口功能。打开通话。

> 公共 CoreWebView2WindowFeatures [WindowFeatures](#windowfeatures)

可将这些功能考虑到新的 web 视图窗口的位置和大小调整。

#### GetDeferral 

获取 CoreWebView2Deferral 对象并将事件置于延迟状态。

> 公共 CoreWebView2Deferral [GetDeferral](#getdeferral)（）

你可以使用 CoreWebView2Deferral 对象在以后的时间完成窗口打开请求。 当此事件延迟时，opener 窗口将返回到 unnavigated 窗口的 WindowProxy，该窗口将在延迟完成时进行导航。
