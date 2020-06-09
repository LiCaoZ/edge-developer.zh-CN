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
ms.openlocfilehash: 93e662088ae1561b5dcb33390f46a41c19ca0aaf
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "10698416"
---
# CoreWebView2ScriptDialogOpeningEventArgs 类的 WebView2 

命名空间： Microsoft WebView2 \
程序集： Microsoft WebView2

ScriptDialogOpening 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[DefaultText](#defaulttext) | 第二个参数传递到 JavaScript 提示对话框。
[Kind](#kind) | "JavaScript 类型" 对话框。
[消息](#message) | 对话框的消息。
[ResultText](#resulttext) | 如果调用 Accept，则返回 JavaScript 提示函数的值。
[Uri](#uri) | 请求对话框的页面的 URI。
[接受](#accept) | 宿主可以调用此方法来响应 "确定" 以确认、提示和 beforeunload 对话框，或者不调用此方法来指示 "取消"。
[GetDeferral](#getdeferral) | 可调用 GetDeferral 以返回 CoreWebView2Deferral 对象。

## 成员

#### DefaultText 

第二个参数传递到 JavaScript 提示对话框。

> 公共字符串[DefaultText](#defaulttext)

这是提示 JavaScript 函数的结果所使用的默认值。

#### Kind 

"JavaScript 类型" 对话框。

> 公共 CoreWebView2ScriptDialogKind[种类](#kind)

接受、确认、提示或 beforeunload。

#### 消息 

对话框的消息。

> 公共字符串[消息](#message)

从 JavaScript 中，这是传递给 alert、confirm 和 prompt 的第一个参数，对于 beforeunload 是空的。

#### ResultText 

如果调用 Accept，则返回 JavaScript 提示函数的值。

> 公共字符串[ResultText](#resulttext)

对于除提示之外的对话框类型，忽略此操作。 如果未调用 "接受"，则忽略此值，并从 prompt 返回 false。

#### Uri 

请求对话框的页面的 URI。

> 公共字符串[Uri](#uri)

#### 接受 

宿主可以调用此方法来响应 "确定" 以确认、提示和 beforeunload 对话框，或者不调用此方法来指示 "取消"。

> 公共 void [Accept](#accept)（）

从 JavaScript 中，这意味着如果调用 Accept，则 confirm 函数和 beforeunload 函数将返回 true。 对于提示函数，如果 "接受" 被调用，则返回 ResultText 的值，否则返回 false。

#### GetDeferral 

可调用 GetDeferral 以返回 CoreWebView2Deferral 对象。

> 公共 CoreWebView2Deferral [GetDeferral](#getdeferral)（）

稍后可使用此操作完成事件。
