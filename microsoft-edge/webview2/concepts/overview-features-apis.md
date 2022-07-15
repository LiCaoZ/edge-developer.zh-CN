---
title: WebView2 功能和 API 概述
description: WebView2 功能和 API 概述。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 07/12/2022
ms.openlocfilehash: bd4c852a8be59a1e51b1265b6011590f92e1f3e2
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668697"
---
# <a name="overview-of-webview2-features-and-apis"></a>WebView2 功能和 API 概述

在应用中嵌入 WebView2 控件可让应用访问通过 WebView2 类或接口提供的各种方法和属性。  WebView2 拥有数百个 API，提供大量功能，从增强应用的本机平台功能到使应用能够修改浏览器体验。  本文提供 WebView2 API 的高级分组，以帮助你了解可以使用 WebView2 执行的不同操作。

托管 WebView2 控件时，应用有权访问以下功能和 API：

| 功能区域 | 用途 |
|---|---|
| [主类：环境、控制器和核心](#main-classes-environment-controller-and-core) | `CoreWebView2Controller``CoreWebView2` (`CoreWebView2Environment`或等效接口的类) 协同工作，以便应用可以托管 WebView2 浏览器控件并访问其浏览器功能。  这些大型类公开了主机应用可以访问的各种 API，为用户提供以下类别的浏览器相关功能。 |
| [Web/本机互操作](#webnative-interop) | 将 Web 内容嵌入本机应用程序。  使用简单消息、JavaScript 代码和本机对象在本机代码和 Web 代码之间进行通信。 |
| [浏览器功能](#browser-features) | WebView2 控件允许应用访问许多浏览器功能。  可以修改这些浏览器功能并将其打开或关闭。 |
| [进程管理](#process-management) | 获取有关运行 WebView2 进程、退出进程和失败进程的信息，以便应用可以相应地采取措施。 |
| [导航到页面并管理已加载的内容](#navigate-to-pages-and-manage-loaded-content) | 管理网页导航和管理网页中加载的内容。 |
| [iFrames](#iframes) | 将其他网页嵌入到自己的网页中。  检测何时创建嵌入的网页、检测嵌入网页导航的时间，以及选择性地绕过 x 帧选项。 |
| [Authentication](#authentication) | 应用可以使用 WebView2 控件处理基本身份验证。  _基本身份验证_ 是属于 HTTP 协议的特定身份验证方法。 |
| [在非框架应用中呈现 WebView2](#rendering-webview2-in-non-framework-apps) | 如果主机应用不使用 UI 框架，请使用这些 API 设置 WebView2 呈现系统。  此呈现设置控制 WebView2 如何将输出呈现到主机应用，以及 WebView2 如何处理输入、焦点和辅助功能。 |
| [使用合成呈现 WebView2](#rendering-webview2-using-composition) | 对于基于合成的 WebView2 呈现，请使用 `CoreWebView2Environment` 它来创建一个 `CoreWebView2CompositionController`。  `CoreWebView2CompositionController` 提供与之相同的 API `CoreWebView2Controller`，但也包括用于基于合成的呈现的 API。 |
| [用户数据](#user-data) | 管理用户数据文件夹 (UDF) （即用户计算机上的文件夹）。  UDF 包含与主机应用和 WebView2 相关的数据。  WebView2 应用使用用户数据文件夹来存储浏览器数据，例如 Cookie、权限和缓存资源。 |
| [性能和调试](#performance-and-debugging) | 分析和调试性能、处理与性能相关的事件，以及管理内存使用情况，以提高应用的响应能力。 |
| [Chrome 开发人员协议 (CDP) ](#chrome-developer-protocol-cdp) | 检测、检查、调试和配置文件Chromium浏览器。  Chrome DevTools 协议是 Microsoft Edge DevTools 的基础。  对于未在 WebView2 平台中实现的功能，请使用 Chrome DevTools 协议。 |


<!-- ====================================================================== -->
## <a name="main-classes-environment-controller-and-core"></a>主类：环境、控制器和核心

<!-- keep sync'd:
* [Main classes: Environment, Controller, and Core](overview-features-apis.md#main-classes-environment-controller-and-core) in _Overview of WebView2 features and APIs_.
* [Main classes for WebView2: Environment, Controller, and Core](environment-controller-core.md) - topmost content.
-->

`CoreWebView2Controller``CoreWebView2` (`CoreWebView2Environment`或等效接口的类) 协同工作，以便应用可以托管 WebView2 浏览器控件并访问其浏览器功能。  这三个大类公开了主机应用可以访问的各种 API，为用户提供许多类别的浏览器相关功能。

*  该 `CoreWebView2Environment` 类表示一组 WebView2 控件，这些控件共享相同的 WebView2 浏览器进程、用户数据文件夹和呈现器进程。  在此类 `CoreWebView2Environment` 中，你将创建对 `CoreWebView2Controller` 和 `CoreWebView2` 实例。
*  该 `CoreWebView2Controller` 类负责托管相关功能，例如窗口焦点、可见性、大小和输入，应用在其中托管 WebView2 控件。
*  该 `CoreWebView2` 类适用于 WebView2 控件的特定于 Web 的部分，包括网络、导航、脚本以及分析和呈现 HTML。

<!-- / keep sync'd -->

另请参阅：
* [WebView2 的主要类：环境、控制器和核心](environment-controller-core.md)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)
* [CoreWebView2Controller 类](/dotnet/api/microsoft.web.webview2.core.corewebview2controller)
* [CoreWebView2Environment 类](/dotnet/api/microsoft.web.webview2.core.corewebview2environment)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2)
* [CoreWebView2Controller 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller)
* [CoreWebView2Environment 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2)
* [ICoreWebView2Controller](/microsoft-edge/webview2/reference/win32/icorewebview2controller)
* [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment)

---


<!-- ====================================================================== -->
## <a name="webnative-interop"></a>Web/本机互操作

Microsoft Edge WebView2 控件允许你将 Web 内容嵌入本机应用程序。 可以使用简单的消息、JavaScript 代码和本机对象在本机代码和 Web 代码之间进行通信。 

一些常见用例包括：
*  导航到其他网站后，更新本机主机窗口标题。
*  从 Web 应用发送本机相机对象并使用其方法。
*  在应用程序的 Web 端运行专用 JavaScript 文件。

有关详细信息，请参阅：
* [本机和 Web 端代码的互操作](../how-to/communicate-btwn-web-native.md)
* [从本机代码调用 Web 端代码](../how-to/javascript.md)
* [从 Web 端代码调用本机代码](../how-to/hostobject.md)

以下是用于在 Web 和本机代码之间通信的主要 API。


<!-- ------------------------------ -->
#### <a name="hostweb-object-sharing"></a>主机/Web 对象共享

WebView2 允许在本机代码中定义的对象传递到应用的 Web 端代码。  _主机对象_ 是在本机代码中定义的任何对象，你选择将这些对象传递给应用的 Web 端代码。

主机对象可以投影到 JavaScript 中，以便可以从应用的 Web 端代码调用本机对象方法 (或其他 API) 。  例如，应用可以调用此类 API，因为用户在应用的 Web 端进行交互。 这样，就不需要在 Web 端代码中重新实现本机对象的 API，例如方法或属性。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addhostobjecttoscript)
* [CoreWebView2.RemoveHostObjectFromScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.removehostobjectfromscript)
* [CoreWebView2Settings.AreHostObjectsAllowed 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.arehostobjectsallowed)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#addhostobjecttoscript)
* [CoreWebView2.RemoveHostObjectFromScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#removehostobjectfromscript)
* [CoreWebView2Settings.AreHostObjectsAllowed 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#arehostobjectsallowed)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript)
* [ICoreWebView2：：RemoveHostObjectFromScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#removehostobjectfromscript)
* [ICoreWebView2Settings：：AreHostObjectsAllowed 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_arehostobjectsallowed)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_arehostobjectsallowed)

---


<!-- ------------------------------ -->
#### <a name="script-execution"></a>脚本执行

允许主机应用在 WebView2 控件的 Web 内容中添加 JavaScript。 

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addscripttoexecuteondocumentcreatedasync)
* [CoreWebView2.ExecuteScriptAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.executescriptasync)
* [CoreWebView2.RemoveScriptToExecuteOnDocumentCreated 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.removescripttoexecuteondocumentcreated)
* [CoreWebView2Settings.IsScriptEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isscriptenabled)
* [CoreWebView2Frame.ExecuteScriptAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.executescriptasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#addscripttoexecuteondocumentcreatedasync)
* [CoreWebView2.ExecuteScriptAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#executescriptasync)
* [CoreWebView2.RemoveScriptToExecuteOnDocumentCreated 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#removescripttoexecuteondocumentcreated)
* [CoreWebView2Settings.IsScriptEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#isscriptenabled)
* [CoreWebView2Frame.ExecuteScriptAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#executescriptasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：AddScriptToExecuteOnDocumentCreated 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#addscripttoexecuteondocumentcreated)
* [ICoreWebView2：：ExecuteScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#executescript)
* [ICoreWebView2：：RemoveScriptToExecuteOnDocumentCreated 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#removescripttoexecuteondocumentcreated)
* [ICoreWebView2Settings：：IsScriptEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_isscriptenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_isscriptenabled)
* [ICoreWebView2Frame2：：ExecuteScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#executescript)

---


<!-- ------------------------------ -->
#### <a name="web-messaging"></a>Web 消息传送

你的应用可以将消息发送到 WebView2 控件内的 Web 内容，并从该 Web 内容接收消息。  消息以字符串或 JSON 对象形式发送。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PostWebMessageAsJson 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.postwebmessageasjson)
* [CoreWebView2.PostWebMessageAsString 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.postwebmessageasstring)
* [CoreWebView2.WebMessageReceived 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.webmessagereceived)
   * [CoreWebView2WebMessageReceivedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webmessagereceivedeventargs)
* [CoreWebView2Settings.IsWebMessageEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.iswebmessageenabled)
* [CoreWebView2Frame.PostWebMessageAsJson 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.postwebmessageasjson)
* [CoreWebView2Frame.PostWebMessageAsString 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.postwebmessageasstring)
* [CoreWebView2Frame.WebMessageReceived 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.webmessagereceived)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PostWebMessageAsJson 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#postwebmessageasjson)
* [CoreWebView2.PostWebMessageAsString 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#postwebmessageasstring)
* [CoreWebView2.WebMessageReceived 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#webmessagereceived)
   * [CoreWebView2WebMessageReceivedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2webmessagereceivedeventargs)
* [CoreWebView2Settings.IsWebMessageEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#iswebmessageenabled)
* [CoreWebView2Frame.PostWebMessageAsJson 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#postwebmessageasjson)
* [CoreWebView2Frame.PostWebMessageAsString 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#postwebmessageasstring)
* [CoreWebView2Frame.WebMessageReceived 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#webmessagereceived)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：:P ostWebMessageAsJson 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasjson)
* [ICoreWebView2：:P ostWebMessageAsString 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasstring)
* [ICoreWebView2：：WebMessageReceived 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_webmessagereceived)
   * [ICoreWebView2WebMessageReceivedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventargs)
* [ICoreWebView2Settings：：IsWebMessageEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_iswebmessageenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_iswebmessageenabled)
* [ICoreWebView2Frame2：:P ostWebMessageAsJson 方法](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#postwebmessageasjson)
* [ICoreWebView2Frame2：:P ostWebMessageAsString 方法](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#postwebmessageasstring)
* [ICoreWebView2Frame2：：WebMessageReceived 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#add_webmessagereceived)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#remove_webmessagereceived)

---


<!-- ------------------------------ -->
#### <a name="script-dialogs"></a>脚本对话框

托管 WebView2 时，应用可以管理不同的 JavaScript 对话框、禁止使用这些对话或将其替换为自定义对话框。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.ScriptDialogOpening 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.scriptdialogopening)
   * [CoreWebView2ScriptDialogOpeningEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2scriptdialogopeningeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.ScriptDialogOpening 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#scriptdialogopening)
   * [CoreWebView2ScriptDialogOpeningEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2scriptdialogopeningeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：ScriptDialogOpening 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_scriptdialogopening)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_scriptdialogopening)
   * [ICoreWebView2ScriptDialogOpeningEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2scriptdialogopeningeventargs)

---


<!-- ====================================================================== -->
## <a name="browser-features"></a>浏览器功能

WebView2 控件允许应用访问许多浏览器功能。  可以修改这些浏览器功能并将其打开或关闭。

<!-- ------------------------------ -->
#### <a name="printing"></a>打印

可以配置自定义打印设置并打印到 PDF。  

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PrintToPdfAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.printtopdfasync)
* [CoreWebView2Environment.CreatePrintSettings 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createprintsettings)
* [CoreWebView2PrintSettings 类](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PrintToPdfAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#printtopdfasync)
* [CoreWebView2Environment.CreatePrintSettings 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createprintsettings)
* [CoreWebView2PrintSettings 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_7：:P rintToPdf 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_7#printtopdf)
* [ICoreWebView2Environment6：：CreatePrintSettings 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment6#createprintsettings)
* [ICoreWebView2PrintSettings 接口](/microsoft-edge/webview2/reference/win32/icorewebview2printsettings)

---


<!-- ------------------------------ -->
#### <a name="cookies"></a>Cookie

可以在 WebView2 中使用 Cookie 来管理用户会话、存储用户个性化首选项和跟踪用户行为。

另请参阅：
* [查看、编辑和删除 Cookie](/microsoft-edge/devtools-guide-chromium/storage/cookies)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Cookie 类](/dotnet/api/microsoft.web.webview2.core.corewebview2cookie)
* [CoreWebView2CookieList 类](/dotnet/api/microsoft.web.webview2.core.corewebview2cookielist)
* [CoreWebView2.CookieManager 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.cookiemanager#microsoft-web-webview2-core-corewebview2-cookiemanager)
   * [CoreWebView2CookieManager 类](/dotnet/api/microsoft.web.webview2.core.corewebview2cookiemanager)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Cookie 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2cookie)
* [CoreWebView2.CookieManager 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#cookiemanager)
   * [CoreWebView2CookieManager 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2cookiemanager)

<!-- TODO: not found, omit?
* [CoreWebView2CookieList Class]()
-->

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Cookie 接口](/microsoft-edge/webview2/reference/win32/icorewebview2cookie)
* [ICoreWebView2CookieList 接口](/microsoft-edge/webview2/reference/win32/icorewebview2cookielist)
* [ICoreWebView2_2.CookieManager 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_2#get_cookiemanager)
   * [ICoreWebView2CookieManager 接口](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager)

---


<!-- ------------------------------ -->
#### <a name="image-capture"></a>图像捕获

通过托管 WebView2，你的应用可以捕获屏幕截图并指示用于保存图像的格式。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.CapturePreviewAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.capturepreviewasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.CapturePreviewAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#capturepreviewasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2.CapturePreview 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#capturepreview)

---


<!-- ------------------------------ -->
#### <a name="downloads"></a>下载

你的应用可以在 WebView2 中管理下载体验。  你的应用可以：
*  允许或阻止基于不同元数据的下载。
*  更改下载位置。
*  配置自定义下载 UI。
*  自定义默认 UI。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

一般：
* [CoreWebView2.IsDefaultDownloadDialogOpenChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.isdefaultdownloaddialogopenchanged)
* [CoreWebView2.IsDefaultDownloadDialogOpen 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.isdefaultdownloaddialogopen)
* [CoreWebView2.OpenDefaultDownloadDialog 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.opendefaultdownloaddialog)
* [CoreWebView2.CloseDefaultDownloadDialog 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.closedefaultdownloaddialog)

修改默认体验：
* [CoreWebView2.DefaultDownloadDialogCornerAlignment 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.defaultdownloaddialogcorneralignment)
* [CoreWebView2.DefaultDownloadDialogMargin 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.defaultdownloaddialogmargin)
* [CoreWebView2Profile.DefaultDownloadFolderPath 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.defaultdownloadfolderpath)

自定义下载体验：
* [CoreWebView2.DownloadStarting 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.downloadstarting)
   * [CoreWebView2DownloadStartingEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2downloadstartingeventargs)
* [CoreWebView2DownloadOperation 类](/dotnet/api/microsoft.web.webview2.core.corewebview2downloadoperation)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

一般：
* [CoreWebView2.IsDefaultDownloadDialogOpenChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#isdefaultdownloaddialogopenchanged)
* [CoreWebView2.IsDefaultDownloadDialogOpen 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#isdefaultdownloaddialogopen)
* [CoreWebView2.OpenDefaultDownloadDialog 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#opendefaultdownloaddialog)
* [CoreWebView2.CloseDefaultDownloadDialog 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#closedefaultdownloaddialog)

修改默认体验：
* [CoreWebView2.DefaultDownloadDialogCornerAlignment 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#defaultdownloaddialogcorneralignment)
* [CoreWebView2.DefaultDownloadDialogMargin 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#defaultdownloaddialogmargin)
* [CoreWebView2Profile.DefaultDownloadFolderPath 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2profile#defaultdownloadfolderpath)

自定义下载体验：
* [CoreWebView2.DownloadStarting 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#downloadstarting)
   * [CoreWebView2DownloadStartingEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2downloadstartingeventargs)
* [CoreWebView2DownloadOperation 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2downloadoperation)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

一般：
* [ICoreWebView2_9：：IsDefaultDownloadDialogOpen 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_9#get_isdefaultdownloaddialogopen)<!--no put-->
* [ICoreWebView2_9：：OpenDefaultDownloadDialog 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_9#opendefaultdownloaddialog)
* [ICoreWebView2_9：：IsDefaultDownloadDialogOpenChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_9#add_isdefaultdownloaddialogopenchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_9#remove_isdefaultdownloaddialogopenchanged)
* [ICoreWebView2_9：：CloseDefaultDownloadDialog 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_9#closedefaultdownloaddialog)

修改默认体验：
* [ICoreWebView2_9：:D efaultDownloadDialogCornerAlignment 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2_9#get_defaultdownloaddialogcorneralignment)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2_9#put_defaultdownloaddialogcorneralignment)
* [ICoreWebView2_9：:D efaultDownloadDialogMargin 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2_9#get_defaultdownloaddialogmargin)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2_9#put_defaultdownloaddialogmargin)
* [ICoreWebView2Profile：:D efaultDownloadFolderPath 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2profile#get_defaultdownloadfolderpath)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2profile#put_defaultdownloadfolderpath)

自定义下载体验：
* [ICoreWebView2_4：:D ownloadStarting 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_4#add_downloadstarting)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_4#remove_downloadstarting)
   * [ICoreWebView2DownloadStartingEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2downloadstartingeventargs)
* [ICoreWebView2DownloadOperation 接口](/microsoft-edge/webview2/reference/win32/icorewebview2downloadoperation)

---


<!-- ------------------------------ -->
#### <a name="permissions"></a>权限

不同的网页可能会要求你获得访问某些特权资源的权限，例如地理位置传感器、照相机和麦克风。  主机应用可以以编程方式响应权限请求，并可将默认权限 UI 替换为其自己的 UI。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PermissionRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.permissionrequested)
   * [CoreWebView2PermissionRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2permissionrequestedeventargs)
* [CoreWebView2Frame.PermissionRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.permissionrequested)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PermissionRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#permissionrequested)
   * [CoreWebView2PermissionRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2permissionrequestedeventargs)
* [CoreWebView2Frame.PermissionRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#permissionrequested)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：:P ermissionRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_permissionrequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_permissionrequested)
   * [ICoreWebView2PermissionRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2permissionrequestedeventargs)
* [ICoreWebView2Frame3：:P ermissionRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame3#add_permissionrequested)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame3#remove_permissionrequested)

---


<!-- ------------------------------ -->
#### <a name="context-menus"></a>上下文菜单

WebView2 控件提供默认上下文菜单 (右键单击菜单) 可以自定义或禁用，还可以创建自己的上下文菜单。 

另请参阅：
* [自定义 WebView2 中的上下文菜单](../how-to/context-menus.md)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Environment.CreateContextMenuItem 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcontextmenuitem)
* [CoreWebView2ContextMenuItem 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem)
* [CoreWebView2ContextMenuTarget 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutarget)
* [CoreWebView2.ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)
   * [CoreWebView2ContextMenuRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs)
* [CoreWebView2Settings.AreDefaultContextMenusEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.aredefaultcontextmenusenabled)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Environment.CreateContextMenuItem 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcontextmenuitem)
* [CoreWebView2ContextMenuItem 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2contextmenuitem)
* [CoreWebView2ContextMenuTarget 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2contextmenutarget)
* [CoreWebView2.ContextMenuRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#contextmenurequested)
   * [CoreWebView2ContextMenuRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2contextmenurequestedeventargs)
* [CoreWebView2Settings.AreDefaultContextMenusEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#aredefaultcontextmenusenabled)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Environment9：：CreateContextMenuItem 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment9#createcontextmenuitem)
* [ICoreWebView2ContextMenuItem 接口](/microsoft-edge/webview2/reference/win32/icorewebview2contextmenuitem)
   * [ICoreWebView2ContextMenuItemCollection 接口](/microsoft-edge/webview2/reference/win32/icorewebview2contextmenuitemcollection)
* [ICoreWebView2ContextMenuTarget 接口](/microsoft-edge/webview2/reference/win32/icorewebview2contextmenutarget)
* [ICoreWebView2_11：：ContextMenuRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_11#add_contextmenurequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_11#remove_contextmenurequested)
   * [ICoreWebView2ContextMenuRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2contextmenurequestedeventargs)
* [ICoreWebView2Settings：：AreDefaultContextMenusEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_aredefaultcontextmenusenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_aredefaultcontextmenusenabled)

---


<!-- ------------------------------ -->
#### <a name="status-bar"></a>状态栏

状态栏位于页面左下角，显示正在显示的网页的状态。 在 WebView2 中，可以启用/禁用状态栏，获取状态栏中的文本，并了解状态栏文本何时更改。 

<!--
See also:
-->

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.StatusBarTextChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.statusbartextchanged)
* [CoreWebView2.StatusBarText 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.statusbartext)
* [CoreWebView2Settings.IsStatusBarEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isstatusbarenabled)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.StatusBarTextChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#statusbartextchanged)
* [CoreWebView2.StatusBarText 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#statusbartext)
* [CoreWebView2Settings.IsStatusBarEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#isstatusbarenabled)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_12：：StatusBarTextChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_12#add_statusbartextchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_12#remove_statusbartextchanged)
* [ICoreWebView2_12：：StatusBarText 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_12#get_statusbartext)
* [ICoreWebView2Settings：：IsStatusBarEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_isstatusbarenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_isstatusbarenabled)

---


<!-- ------------------------------ -->
#### <a name="user-agent"></a>User Agent
<!-- alt for "Learn how to" -->
<!-- why would you do this, what is benefit for end user, what's involved?  Your app can detect which XYZ and then ABC so that the X is Y. -->
用户代理是一个字符串，代表代表用户的程序标识，例如浏览器名称。 在 WebView2 中，可以设置用户代理。

另请参阅：
* [使用用户代理客户端提示检测 Windows 11](../../web-platform/how-to-detect-win11.md)
* [替代用户代理字符串](../../devtools-guide-chromium/device-mode/override-user-agent.md)


##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.UserAgent 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.useragent)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.UserAgent 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#useragent)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings2：：UserAgent 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings2#get_useragent)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings2#put_useragent)

---


<!-- ------------------------------ -->
#### <a name="autofill"></a>自动填充

应用可以独立控制浏览器的自动填充功能是针对常规信息还是密码启用。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.IsGeneralAutofillEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isgeneralautofillenabled)
* [CoreWebView2Settings.IsPasswordAutosaveEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.ispasswordautosaveenabled)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.IsGeneralAutofillEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#isgeneralautofillenabled)
* [CoreWebView2Settings.IsPasswordAutosaveEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#ispasswordautosaveenabled)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings4：：IsGeneralAutofillEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings4#get_isgeneralautofillenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings4#put_isgeneralautofillenabled)
* [ICoreWebView2Settings4：：IsPasswordAutosaveEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings4#get_ispasswordautosaveenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings4#put_ispasswordautosaveenabled)

---


<!-- ------------------------------ -->
#### <a name="audio"></a>音频

你的应用可以静音和取消所有音频，并找出音频播放时间。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.IsDocumentPlayingAudioChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.isdocumentplayingaudiochanged)
* [CoreWebView2.IsMutedChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.ismutedchanged)
* [CoreWebView2.IsDocumentPlayingAudio 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.isdocumentplayingaudio)
* [CoreWebView2.IsMuted 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.ismuted)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.IsDocumentPlayingAudioChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#isdocumentplayingaudiochanged)
* [CoreWebView2.IsMutedChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#ismutedchanged)
* [CoreWebView2.IsDocumentPlayingAudio 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#isdocumentplayingaudio)
* [CoreWebView2.IsMuted 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#ismuted)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_8：：IsDocumentPlayingAudioChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_8#add_isdocumentplayingaudiochanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_8#remove_isdocumentplayingaudiochanged)
* [ICoreWebView2_8：：IsMutedChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_8#add_ismutedchanged)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_8#remove_ismutedchanged)
* [ICoreWebView2_8：：IsDocumentPlayingAudio 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_8#get_isdocumentplayingaudio)
* [ICoreWebView2_8：：IsMuted 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2_8#get_ismuted)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2_8#put_ismuted)

---


<!-- ------------------------------ -->
#### <a name="swipe-gesture-navigation"></a>轻扫手势导航

通过托管 WebView2 控件，应用可以在启用触摸输入的设备上启用或禁用轻扫手势导航。 此手势允许最终用户：
*  向左/向右轻扫 (水平轻扫) 导航到导航历史记录中的上一页或下一页。
*  拉取以刷新 () 当前页面垂直轻扫。

此功能当前在浏览器中默认禁用。  若要在 WebView2 中启用此功能，请设置 `AdditionalBrowserArguments` 属性，指定 `--pull-to-refresh` 开关。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.IsSwipeNavigationEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isswipenavigationenabled)
* [CoreWebView2EnvironmentOptions.AdditionalBrowserArguments 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.additionalbrowserarguments)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.IsSwipeNavigationEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#isswipenavigationenabled)
* [CoreWebView2EnvironmentOptions.AdditionalBrowserArguments 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environmentoptions#additionalbrowserarguments)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings6：：IsSwipeNavigationEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings6#get_isswipenavigationenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings6#put_isswipenavigationenabled)
* [ICoreWebView2EnvironmentOptions：：AdditionalBrowserArguments 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#get_additionalbrowserarguments)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#put_additionalbrowserarguments)

---


<!-- ------------------------------ -->
#### <a name="document-title"></a>文档标题

应用可以检测当前顶级文档的标题何时更改。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.DocumentTitle 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.documenttitle)
* [CoreWebView2.DocumentTitleChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.documenttitlechanged)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.DocumentTitle 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#documenttitle)
* [CoreWebView2.DocumentTitleChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#documenttitlechanged)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：:D ocumentTitle 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_documenttitle)<!--no put-->
* [ICoreWebView2：:D ocumentTitleChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_documenttitlechanged)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_documenttitlechanged)

---


<!-- ------------------------------ -->
#### <a name="fullscreen"></a>全屏

在 WebView2 中，可以找出 HTML 元素何时进入或离开全屏视图。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.ContainsFullScreenElement 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.containsfullscreenelement)
* [CoreWebView2.ContainsFullScreenElementChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.containsfullscreenelementchanged)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.ContainsFullScreenElement 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#containsfullscreenelement)
* [CoreWebView2.ContainsFullScreenElementChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#containsfullscreenelementchanged)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：ContainsFullScreenElement 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_containsfullscreenelement)<!--no put-->
* [ICoreWebView2：：ContainsFullScreenElementChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_containsfullscreenelementchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_containsfullscreenelementchanged)

---

<!-- ------------------------------ -->
#### <a name="pdf-toolbar"></a>PDF 工具栏

在浏览器 PDF 查看器中，顶部有一个特定于 PDF 的工具栏。  在 WebView2 中，可以隐藏 PDF 查看器工具栏中的某些项。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.HiddenPdfToolbarItems 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.hiddenpdftoolbaritems)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.HiddenPdfToolbarItems 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#hiddenpdftoolbaritems)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings7：：HiddenPdfToolbarItems 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings7#get_hiddenpdftoolbaritems)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings7#put_hiddenpdftoolbaritems)

---

<!-- ------------------------------ -->
#### <a name="theming"></a>主题

在 WebView2 中，可以将颜色主题自定义为系统、浅色或深色。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Profile.PreferredColorScheme 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.preferredcolorscheme)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Profile.PreferredColorScheme 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2profile#preferredcolorscheme)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Profile：:P referredColorScheme 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2profile#get_preferredcolorscheme)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2profile#put_preferredcolorscheme)

---

<!-- ------------------------------ -->
#### <a name="language"></a>语言

可以设置适用于浏览器 UI (（如上下文菜单和对话) ）的 WebView2 的默认显示语言，以及设置 `accept-language` WebView2 发送到网站的 HTTP 标头。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2EnvironmentOptions.Language 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.language)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2EnvironmentOptions.Language 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environmentoptions#language)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2EnvironmentOptions：：语言属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#get_language)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#put_language)

---

<!-- ------------------------------ -->
#### <a name="new-window"></a>“新建”窗口

WebView2 提供用于处理 JavaScript 函数 `window.open()`的功能。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.NewWindowRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.newwindowrequested)
   * [CoreWebView2NewWindowRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2newwindowrequestedeventargs)
   * [CoreWebView2WindowFeatures 类](/dotnet/api/microsoft.web.webview2.core.corewebview2windowfeatures)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.NewWindowRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#newwindowrequested)
   * [CoreWebView2NewWindowRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2newwindowrequestedeventargs)
   * [CoreWebView2WindowFeatures 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2windowfeatures)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：NewWindowRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_newwindowrequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_newwindowrequested)
   * [ICoreWebView2NewWindowRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs)
   * [ICoreWebView2WindowFeatures 接口](/microsoft-edge/webview2/reference/win32/icorewebview2windowfeatures)

---


<!-- ------------------------------ -->
#### <a name="close-window"></a>关闭窗口

WebView2 提供用于处理 JavaScript 函数 `window.close()`的功能。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.Close 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.close)
* [CoreWebView2.WindowCloseRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.windowcloserequested)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.Close 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#close)
* [CoreWebView2.WindowCloseRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#windowcloserequested)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：Close 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#close)
* [ICoreWebView2：：WindowsCloseRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_windowcloserequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_windowcloserequested)

---


<!-- ====================================================================== -->
## <a name="process-management"></a>进程管理

获取有关运行 WebView2 进程、退出进程和失败进程的信息，以便应用可以相应地采取措施。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

信息：
* [CoreWebView2.BrowserProcessId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.browserprocessid)
* [CoreWebView2Environment.GetProcessInfos 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.getprocessinfos)
* [CoreWebView2Environment.ProcessInfosChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.processinfoschanged)
* [CoreWebView2ProcessInfo 类](/dotnet/api/microsoft.web.webview2.core.corewebview2processinfo)

退出：
* [CoreWebView2Environment.BrowserProcessExited 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.browserprocessexited)
   * [CoreWebView2BrowserProcessExitedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2browserprocessexitedeventargs)

失败：
* [CoreWebView2.ProcessFailed 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.processfailed)
   * [CoreWebView2ProcessFailedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2processfailedeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

信息：
* [CoreWebView2.BrowserProcessId 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#browserprocessid)
* [CoreWebView2Environment.GetProcessInfos 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#getprocessinfos)
* [CoreWebView2Environment.ProcessInfosChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#processinfoschanged)
* [CoreWebView2ProcessInfo 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2processinfo)

退出：
* [CoreWebView2Environment.BrowserProcessExited 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#browserprocessexited)
   * [CoreWebView2BrowserProcessExitedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2browserprocessexitedeventargs)

失败：
* [CoreWebView2.ProcessFailed 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#processfailed)
   * [CoreWebView2ProcessFailedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2processfailedeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

信息：
* [ICoreWebView2：：BrowserProcessId 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_browserprocessid)<!--no put-->
* [ICoreWebView2Environment8：：GetProcessInfos 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment8#getprocessinfos)
* [ICoreWebView2Environment8：:P rocessInfosChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2environment8#add_processinfoschanged)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2environment8#remove_processinfoschanged)
* [ICoreWebView2ProcessInfo 接口](/microsoft-edge/webview2/reference/win32/icorewebview2processinfo)
* [ICoreWebView2ProcessInfoCollection 接口](/microsoft-edge/webview2/reference/win32/icorewebview2processinfocollection)

退出：
* [ICoreWebView2Environment5：：BrowserProcessExited 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2environment5#add_browserprocessexited)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2environment5#remove_browserprocessexited)
   * [ICoreWebView2BrowserProcessExitedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2browserprocessexitedeventargs)

失败：
* [ICoreWebView2：:P rocessFailed 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_processfailed)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_processfailed)
   * [ICoreWebView2ProcessFailedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2processfailedeventargs)

---


<!-- ====================================================================== -->
## <a name="navigate-to-pages-and-manage-loaded-content"></a>导航到页面并管理已加载的内容

通过 WebView2 控件，应用可以管理网页导航和管理网页中加载的内容。


<!-- ------------------------------ -->
#### <a name="manage-content-loaded-into-webview2"></a>管理加载到 WebView2 中的内容

这些 API 加载、停止加载内容并将内容重新加载到 WebView2。  加载的内容可以是：
*  URL 中的内容。
*  HTML 字符串。
*  通过虚拟主机名到本地文件夹映射的本地内容。
*  来自构造网络请求的内容。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.Navigate 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigate)
* [CoreWebView2.NavigateToString 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigatetostring)
* [CoreWebView2.NavigateWithWebResourceRequest 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigatewithwebresourcerequest)
* [CoreWebView2.Stop 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.stop)
* [CoreWebView2.Reload 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.reload)
* [CoreWebView2.SetVirtualHostNameToFolderMapping 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.setvirtualhostnametofoldermapping)
* [CoreWebView2.ClearVirtualHostNameToFolderMapping 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.clearvirtualhostnametofoldermapping)
* [CoreWebView2Settings.IsBuiltInErrorPageEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isbuiltinerrorpageenabled#microsoft-web-webview2-core-corewebview2settings-isbuiltinerrorpageenabled)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.Navigate 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#navigate)
* [CoreWebView2.NavigateToString 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#navigatetostring)
* [CoreWebView2.NavigateWithWebResourceRequest 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#navigatewithwebresourcerequest)
* [CoreWebView2.Stop 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#stop)
* [CoreWebView2.Reload 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#reload)
* [CoreWebView2.SetVirtualHostNameToFolderMapping 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#setvirtualhostnametofoldermapping)
* [CoreWebView2.ClearVirtualHostNameToFolderMapping 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#clearvirtualhostnametofoldermapping)
* [CoreWebView2Settings.IsBuiltInErrorPageEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#isbuiltinerrorpageenabled)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：Navigate 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#navigate)
* [ICoreWebView2：：NavigateToString 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#navigatetostring)
* [ICoreWebView2_2：：NavigateWithWebResourceRequest 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_2#navigatewithwebresourcerequest)
* [ICoreWebView2：：Stop 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#stop)
* [ICoreWebView2：：Reload 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#reload)
* [ICoreWebView2_3：：SetVirtualHostNameToFolderMapping 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_3#setvirtualhostnametofoldermapping)
* [ICoreWebView2_3：：ClearVirtualHostNameToFolderMapping 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_3#clearvirtualhostnametofoldermapping)
* [ICoreWebView2Settings：：IsBuiltInErrorPageEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_isbuiltinerrorpageenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_isbuiltinerrorpageenabled)

---


<!-- ------------------------------ -->
#### <a name="navigation-history"></a>导航历史记录

历史记录方法允许在 WebView2 中进行后退和向前导航，历史记录事件提供有关历史记录和 WebView2 当前源中更改的信息。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.Source 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.source)
* [CoreWebView2.SourceChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.sourcechanged)
   * [CoreWebView2SourceChangedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2sourcechangedeventargs)
* [CoreWebView2.HistoryChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.historychanged)
* [CoreWebView2.CanGoBack 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.cangoback)
   * [CoreWebView2.GoBack 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.goback)
* [CoreWebView2.CanGoForward 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.cangoforward)
   * [CoreWebView2.GoForward 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.goforward)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.Source 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#source)
* [CoreWebView2.SourceChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#sourcechanged)
   * [CoreWebView2SourceChangedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2sourcechangedeventargs)
* [CoreWebView2.HistoryChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#historychanged)
* [CoreWebView2.CanGoBack 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#cangoback)
   * [CoreWebView2.GoBack 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#goback)
* [CoreWebView2.CanGoForward 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#cangoforward)
   * [CoreWebView2.GoForward 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#goforward)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：源属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_source)<!--no put-->
* [ICoreWebView2：：SourceChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_sourcechanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_sourcechanged)
   * [ICoreWebView2SourceChangedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2sourcechangedeventargs)
* [ICoreWebView2：：HistoryChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_historychanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_historychanged)
* [ICoreWebView2：：CanGoBack 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_cangoback)<!--no put-->
   * [ICoreWebView2：：GoBack 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#goback)
* [ICoreWebView2：：CanGoForward 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2#get_cangoforward)<!--no put-->
   * [ICoreWebView2：：GoForward 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#goforward)

---


<!-- ------------------------------ -->
#### <a name="block-unwanted-navigating"></a>阻止不需要的导航

该 `NavigationStarting` 事件允许应用取消导航到 WebView2 中的指定 URL，包括帧。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.NavigationStarting 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigationstarting)
   * [CoreWebView2NavigationStartingEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2navigationstartingeventargs)
* [CoreWebView2.FrameNavigationStarting 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.framenavigationstarting)
* [CoreWebView2Frame.NavigationStarting 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.navigationstarting)
   * [CoreWebView2NavigationStartingEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2navigationstartingeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.NavigationStarting 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#navigationstarting)
   * [CoreWebView2NavigationStartingEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2navigationstartingeventargs)
* [CoreWebView2.FrameNavigationStarting 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#framenavigationstarting)
* [CoreWebView2Frame.NavigationStarting 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#navigationstarting)
   * [CoreWebView2NavigationStartingEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2navigationstartingeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：NavigationStarting 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_navigationstarting)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_navigationstarting)
   * [ICoreWebView2NavigationStartingEventArgs2 接口](/microsoft-edge/webview2/reference/win32/icorewebview2navigationstartingeventargs2)<!--v2-->
* [ICoreWebView2：：FrameNavigationStarting 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_framenavigationstarting)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_framenavigationstarting)
* [ICoreWebView2Frame2：：NavigationStarting 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#add_navigationstarting)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#remove_navigationstarting)
   * [ICoreWebView2NavigationStartingEventArgs2 接口](/microsoft-edge/webview2/reference/win32/icorewebview2navigationstartingeventargs2)<!--v2-->

---


<!-- ------------------------------ -->
#### <a name="navigation-events"></a>导航事件

对于 `NavigationStarting` 其他导航事件，可以通知应用 WebView2 中的导航状态。  _导航_是加载新 URL 的过程。

另请参阅：
* [WebView2 应用的导航事件](navigation-events.md)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.ContentLoading 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contentloading)
   * [CoreWebView2ContentLoadingEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contentloadingeventargs)
* [CoreWebView2.DOMContentLoaded 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.domcontentloaded)
   * [CoreWebView2DOMContentLoadedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2domcontentloadedeventargs)
* [CoreWebView2.NavigationCompleted 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigationcompleted)
   * [CoreWebView2NavigationCompletedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2navigationcompletedeventargs)
* [CoreWebView2.FrameNavigationCompleted 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.framenavigationcompleted)
* [CoreWebView2Frame.ContentLoading 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.contentloading)
* [CoreWebView2Frame.DOMContentLoaded 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.domcontentloaded)
* [CoreWebView2Frame.NavigationCompleted 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.navigationcompleted)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.ContentLoading 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#contentloading)
   * [CoreWebView2ContentLoadingEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2contentloadingeventargs)
* [CoreWebView2.DOMContentLoaded 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#domcontentloaded)
   * [CoreWebView2DOMContentLoadedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2domcontentloadedeventargs)
* [CoreWebView2.NavigationCompleted 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#navigationcompleted)
   * [CoreWebView2NavigationCompletedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2navigationcompletedeventargs)
* [CoreWebView2.FrameNavigationCompleted 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#framenavigationcompleted)
* [CoreWebView2Frame.ContentLoading 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#contentloading)
* [CoreWebView2Frame.DOMContentLoaded 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#domcontentloaded)
* [CoreWebView2Frame.NavigationCompleted 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame#navigationcompleted)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：ContentLoading 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_contentloading)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_contentloading)
   * [ICoreWebView2ContentLoadingEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2contentloadingeventargs)
* [ICoreWebView2_2：:D OMContentLoaded 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_2#add_domcontentloaded)， [请删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_2#remove_domcontentloaded)
   * [ICoreWebView2DOMContentLoadedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2domcontentloadedeventargs)
* [ICoreWebView2：：NavigationCompleted 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_navigationcompleted)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_navigationcompleted)
   * [ICoreWebView2NavigationCompletedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2navigationcompletedeventargs)
   * [ICoreWebView2NavigationCompletedEventArgs2 接口](/microsoft-edge/webview2/reference/win32/icorewebview2navigationcompletedeventargs2)
* [ICoreWebView2：：FrameNavigationCompleted 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_framenavigationcompleted)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_framenavigationcompleted)
* [ICoreWebView2Frame2：：ContentLoading 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#add_contentloading)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#remove_contentloading)
* [ICoreWebView2Frame2：:D OMContentLoaded 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#add_domcontentloaded)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#remove_domcontentloaded)
* [ICoreWebView2Frame2：：NavigationCompleted 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#add_navigationcompleted)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2frame2#remove_navigationcompleted)

---


<!-- ------------------------------ -->
#### <a name="manage-network-requests-in-webview2"></a>在 WebView2 中管理网络请求

该 `WebResourceRequested` 事件允许应用截获并覆盖 WebView2 中的所有网络请求。  该 `WebResourceResponseReceived` 事件允许应用监视发送到的请求以及从网络接收的响应。

另请参阅：
* [网络请求的自定义管理](/microsoft-edge/webview2/how-to/webresourcerequested)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.WebResourceRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested)
   * [CoreWebView2WebResourceRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcerequestedeventargs)
* [CoreWebView2.WebResourceResponseReceived 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourceresponsereceived)
   * [CoreWebView2WebResourceResponseReceivedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourceresponsereceivedeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.WebResourceRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#webresourcerequested)
   * [CoreWebView2WebResourceRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2webresourcerequestedeventargs)
* [CoreWebView2.WebResourceResponseReceived 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#webresourceresponsereceived)
   * [CoreWebView2WebResourceResponseReceivedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2webresourceresponsereceivedeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：WebResourceRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webresourcerequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2#remove_webresourcerequested)
   * [ICoreWebView2WebResourceRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2webresourcerequestedeventargs)
* [ICoreWebView2_2：：WebResourceResponseReceived 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_2#add_webresourceresponsereceived)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_2#remove_webresourceresponsereceived)
   * [ICoreWebView2WebResourceResponseReceivedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponsereceivedeventargs)

---


<!-- ------------------------------ -->
#### <a name="client-certificates"></a>客户端证书

在 WebView2 中，可以使用客户端证书 API 在应用程序级别选择客户端证书。  使用此 API 可以：
*  根据需要向用户显示 UI。
*  替换默认的客户端证书对话提示。
*  以编程方式查询证书。
*  当 WebView2 向需要客户端证书进行 HTTP 身份验证的 HTTP 服务器发出请求时，从列表中选择证书以响应服务器。 

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2ClientCertificate 类](/dotnet/api/microsoft.web.webview2.core.corewebview2clientcertificate)
* [CoreWebView2.ClientCertificateRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.clientcertificaterequested)
   * [CoreWebView2ClientCertificateRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2clientcertificaterequestedeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2ClientCertificate 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2clientcertificate)
* [CoreWebView2.ClientCertificateRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#clientcertificaterequested)
   * [CoreWebView2ClientCertificateRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2clientcertificaterequestedeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ClientCertificate 接口](/microsoft-edge/webview2/reference/win32/icorewebview2clientcertificate)
   * [ICoreWebView2ClientCertificateCollection 接口](/microsoft-edge/webview2/reference/win32/icorewebview2clientcertificatecollection)<!--n/a for c#-->
* [ICoreWebView2_5：：ClientCertificateRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_5#add_clientcertificaterequested)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_5#remove_clientcertificaterequested)
   * [ICoreWebView2ClientCertificateRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2clientcertificaterequestedeventargs)

---

<!-- ------------------------------ -->
#### <a name="server-certificates"></a>服务器证书

在 WebView2 中，可以使用服务器证书 API 在应用程序级别信任服务器的 TLS 证书。  这样，主机应用就可以呈现页面，而无需提示用户出现 TLS 错误，或者主机应用可以自动取消请求。 

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.ServerCertificateErrorDetected 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.servercertificateerrordetected)
* [CoreWebView2.ClearServerCertificateErrorActionsAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.clearservercertificateerroractionsasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.ServerCertificateErrorDetected 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#servercertificateerrordetected)
* [CoreWebView2.ClearServerCertificateErrorActionsAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#clearservercertificateerroractionsasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_14：：ServerCertificateErrorDetected 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_14#add_servercertificateerrordetected)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_14#remove_servercertificateerrordetected)
* [ICoreWebView2_14：：ClearServerCertificateErrorActions 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_14#clearservercertificateerroractions)

---


<!-- ====================================================================== -->
## <a name="iframes"></a>iFrames

通过 iFrame，可以将其他网页嵌入到自己的网页中。  在 WebView2 中，可以：
*  了解何时创建 iFrame。
*  了解 iFrame 导航的时间。
*  允许绕过 x 帧选项。

<!-- wording per overview table:
Embed other webpages into your own webpage.  Detect when embedded webpages are created, detect when embedded webpages are navigating, and optionally bypass x-frame options. -->

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Frame 类](/dotnet/api/microsoft.web.webview2.core.corewebview2frame)
* [CoreWebView2FrameInfo 类](/dotnet/api/microsoft.web.webview2.core.corewebview2frameinfo)
* [CoreWebView2.FrameCreated 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.framecreated)
   * [CoreWebView2FrameCreatedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2framecreatedeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Frame 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame)
* [CoreWebView2FrameInfo 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frameinfo)
* [CoreWebView2.FrameCreated 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#framecreated)
   * [CoreWebView2FrameCreatedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2framecreatedeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Frame 接口](/microsoft-edge/webview2/reference/win32/icorewebview2frame)
* [ICoreWebView2FrameInfo 接口](/microsoft-edge/webview2/reference/win32/icorewebview2frameinfo)
   * [ICoreWebView2FrameInfoCollection 接口](/microsoft-edge/webview2/reference/win32/icorewebview2frameinfocollection)<!--n/a for c#-->
   * [ICoreWebView2FrameInfoCollectionIterator 接口](/microsoft-edge/webview2/reference/win32/icorewebview2frameinfocollectioniterator)<!--n/a for c#-->
* [ICoreWebView2_4：：FrameCreated 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_4#add_framecreated)， [请删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_4#remove_framecreated)
   * [ICoreWebView2FrameCreatedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2framecreatedeventargs)

---


<!-- ====================================================================== -->
## <a name="authentication"></a>Authentication

<!-- selling point / value prop: easy configuration of WebView2 apps - support user accounts -->

应用可以使用 WebView2 控件处理基本身份验证。  _基本身份验证_ 是属于 HTTP 协议的特定身份验证方法。

<!-- what's the benefit for end users?  how does it essentially work? what's involved? -->

另请参阅：
* [WebView2 应用的基本身份验证](basic-authentication.md)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2HttpRequestHeaders 类](/dotnet/api/microsoft.web.webview2.core.corewebview2httprequestheaders)
* [CoreWebView2.BasicAuthenticationRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.basicauthenticationrequested)
   * [CoreWebView2BasicAuthenticationRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2basicauthenticationrequestedeventargs)
* [CoreWebView2BasicAuthenticationResponse 类](/dotnet/api/microsoft.web.webview2.core.corewebview2basicauthenticationresponse)
   * [CoreWebView2HttpResponseHeaders 类](/dotnet/api/microsoft.web.webview2.core.corewebview2httpresponseheaders)
* [CoreWebView2HttpHeadersCollectionIterator 类](/dotnet/api/microsoft.web.webview2.core.corewebview2httpheaderscollectioniterator)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2HttpRequestHeaders 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2httprequestheaders)
* [CoreWebView2.BasicAuthenticationRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#basicauthenticationrequested)
   * [CoreWebView2BasicAuthenticationRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2basicauthenticationrequestedeventargs)
* [CoreWebView2BasicAuthenticationResponse 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2basicauthenticationresponse)
   * [CoreWebView2HttpResponseHeaders 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2httpresponseheaders)
* [CoreWebView2HttpHeadersCollectionIterator 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2httpheaderscollectioniterator)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2HttpRequestHeaders 接口](/microsoft-edge/webview2/reference/win32/icorewebview2httprequestheaders)
* [ICoreWebView2_10：：BasicAuthenticationRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_10#add_basicauthenticationrequested)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_10#remove_basicauthenticationrequested)
   * [ICoreWebView2BasicAuthenticationRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2basicauthenticationrequestedeventargs)
* [ICoreWebView2BasicAuthenticationResponse 接口](/microsoft-edge/webview2/reference/win32/icorewebview2basicauthenticationresponse)
   * [ICoreWebView2HttpResponseHeaders 接口](/microsoft-edge/webview2/reference/win32/icorewebview2httpresponseheaders)
* [ICoreWebView2HttpHeadersCollectionIterator 接口](/microsoft-edge/webview2/reference/win32/icorewebview2httpheaderscollectioniterator)

---


<!-- ====================================================================== -->
## <a name="rendering-webview2-in-non-framework-apps"></a>在非框架应用中呈现 WebView2

如果主机应用不使用 UI 框架，请使用这些 API 设置 WebView2 呈现系统。  此呈现设置控制 WebView2 如何将输出呈现到主机应用，以及 WebView2 如何处理输入、焦点和辅助功能。

* **UI 框架** - 如果使用的是应用的 UI 框架，则应使用该 UI 框架提供的 WebView2 元素，而不是使用这些 API。

* **没有 UI 框架，也不使用 Composition** - 例如，如果你未对应用使用 UI 框架 (例如，如果使用纯 Win32 直接) ，或者 UI 框架没有 WebView2 元素，则需要使用本部分中的这些 API 创建 `CoreWebView2Controller` 并将其呈现到应用中。

* **没有 UI 框架，并且使用合成** - 如果应用 UI 是使用 [DirectComposition](/windows/win32/directcomp/directcomposition-portal) 或 [Windows.UI.Composition](/uwp/api/Windows.UI.Composition) 生成的，则应使用 `CoreWebView2CompositionController` 而不是使用这些 API;请参阅下面 [的“使用合成呈现 WebView2](#rendering-webview2-using-composition)”。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.CoreWebView2 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.corewebview2)
* [CoreWebView2Controller.Close 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.close)
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2controllerasync)<!--2 overloads-->

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.CoreWebView2 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#corewebview2)
* [CoreWebView2Controller.Close 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#close)
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2controllerasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：CoreWebView2 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_corewebview2)<!--no put-->
* [ICoreWebView2Controller：：Close 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#close)
* [ICoreWebView2Environment：：CreateCoreWebView2Controller 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment#createcorewebview2controller)

---


<!-- ------------------------------ -->
#### <a name="sizing-positioning-and-visibility"></a>调整大小、定位和可见性

<!-- from the removed "window mgmt" h2 section:
WebView2 gives your app access to window-specific attributes, such as positioning, focus, and keyboard accelerators. -->

`CoreWebView2Controller` 采用父 `HWND`级。 相对 `Bounds` 于父 `HWND`级的属性大小和位置 WebView2。 可以使用 `IsVisible`WebView2 的可见性进行切换。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.Bounds 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.bounds)
* [CoreWebView2Controller.IsVisible 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.isvisible)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.Bounds 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#bounds)
* [CoreWebView2Controller.IsVisible 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#isvisible)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：Bounds 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_bounds)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_bounds)
* [ICoreWebView2Controller：：IsVisible 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_isvisible)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_isvisible)

---


<!-- ------------------------------ -->
#### <a name="zooming"></a>缩放

WebView2 `ZoomFactor` 用于仅缩放窗口的 Web 内容。  当用户通过在旋转鼠标滚轮时按 `Ctrl` 下缩放内容时，UI 缩放也会更新。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.ZoomFactor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.zoomfactor)
* [CoreWebView2Controller.ZoomFactorChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.zoomfactorchanged)
* [CoreWebView2Controller.SetBoundsAndZoomFactor 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.setboundsandzoomfactor)

浏览器/手势/缩放功能：<!-- moved from Rendering section - fits best in "gestures", or "zoom" list? -->
* [CoreWebView2Settings.IsPinchZoomEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.ispinchzoomenabled)
* [CoreWebView2Settings.IsZoomControlEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.iszoomcontrolenabled)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.ZoomFactor 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#zoomfactor)
* [CoreWebView2Controller.ZoomFactorChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#zoomfactorchanged)
* [CoreWebView2Controller.SetBoundsAndZoomFactor 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#setboundsandzoomfactor)

浏览器/手势/缩放功能：
* [CoreWebView2Settings.IsPinchZoomEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#ispinchzoomenabled)
* [CoreWebView2Settings.IsZoomControlEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#iszoomcontrolenabled)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：ZoomFactor 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_zoomfactor)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_zoomfactor)
* [ICoreWebView2Controller：：ZoomFactorChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_zoomfactorchanged)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_zoomfactorchanged)
* [ICoreWebView2Controller：：SetBoundsAndZoomFactor 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#setboundsandzoomfactor)

浏览器/手势/缩放功能：
* [ICoreWebView2Settings5：：IsPinchZoomEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings5#get_ispinchzoomenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings5#put_ispinchzoomenabled)
* [ICoreWebView2Settings：：IsZoomControlEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_iszoomcontrolenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_iszoomcontrolenabled)

---


<!-- ------------------------------ -->
#### <a name="rasterization-scale"></a>光栅化规模

RasterizationScale API 缩放所有 WebView2 UI，包括上下文菜单、工具提示和弹出窗口。  应用可以设置 WebView2 是否应检测监视规模更改并自动更新 RasterizationScale。  `BoundsMode` 用于配置 Bounds 属性是解释为原始像素，还是将需要由 `RasterizationScale`) 缩放的 DIP (。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.BoundsMode 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.boundsmode)
* [CoreWebView2Controller.RasterizationScale 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.rasterizationscale)
* [CoreWebview2Controller.RasterizationScaleChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.rasterizationscalechanged)
* [CoreWebview2Controller.ShouldDetectMonitorScaleChanges 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.shoulddetectmonitorscalechanges)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.BoundsMode 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#boundsmode)
* [CoreWebView2Controller.RasterizationScale 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#rasterizationscale)
* [CoreWebview2Controller.RasterizationScaleChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#rasterizationscalechanged)
* [CoreWebview2Controller.ShouldDetectMonitorScaleChanges 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#shoulddetectmonitorscalechanges)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller3：：BoundsMode 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#get_boundsmode)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#put_boundsmode)
* [ICoreWebView2Controller3：：RasterizationScale 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#get_rasterizationscale)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#put_rasterizationscale)
* [ICoreWebView2Controller3：：RasterizationScaleChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#add_rasterizationscalechanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#remove_rasterizationscalechanged)
* [ICoreWebView2Controller3：：ShouldDetectMonitorScaleChanges 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#get_shoulddetectmonitorscalechanges)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#put_shoulddetectmonitorscalechanges)

---


<!-- ------------------------------ -->
#### <a name="focus-and-tabbing"></a>焦点和制表

WebView2 控件会引发事件，让应用知道控件何时获得焦点或失去焦点。 对于制表 (按 `Tab` 键) ，有一个 API 要将焦点移到 WebView2 中，还有一个 WebView2 事件用于请求应用重新获取焦点。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebview2Controller.MoveFocus 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.movefocus)
* [CoreWebview2Controller.MoveFocusRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.movefocusrequested)
   * [CoreWebView2MoveFocusRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2movefocusrequestedeventargs)
* [CoreWebview2Controller.GotFocus 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.gotfocus)
* [CoreWebview2Controller.LostFocus 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.lostfocus)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebview2Controller.MoveFocus 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#movefocus)
* [CoreWebview2Controller.MoveFocusRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#movefocusrequested)
   * [CoreWebView2MoveFocusRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2movefocusrequestedeventargs)
* [CoreWebview2Controller.GotFocus 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#gotfocus)
* [CoreWebview2Controller.LostFocus 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#lostfocus)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebview2Controller：：MoveFocus 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#movefocus)
* [ICoreWebview2Controller：：MoveFocusRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_movefocusrequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_movefocusrequested)
   * [ICoreWebView2MoveFocusRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2movefocusrequestedeventargs)
* [ICoreWebview2Controller：：GotFocus 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_gotfocus)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_gotfocus)
* [ICoreWebview2Controller：：LostFocus 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_lostfocus)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_lostfocus)

---


<!-- ------------------------------ -->
#### <a name="parent-window"></a>父窗口

WebView2 可以重新向不同的父窗口句柄 () `HWND` 。  当应用在屏幕上的位置发生更改时，还需要通知 WebView2。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebview2Controller.NotifyParentWindowPositionChanged 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.notifyparentwindowpositionchanged)
   * [CoreWebview2Controller.ParentWindow 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.parentwindow)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebview2Controller.NotifyParentWindowPositionChanged 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#notifyparentwindowpositionchanged)
   * [CoreWebview2Controller.ParentWindow 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#parentwindow)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebview2Controller：：NotifyParentWindowPositionChanged 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#notifyparentwindowpositionchanged)
   * [ICoreWebview2Controller：:P arentWindow 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_parentwindow)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_parentwindow)

---


<!-- ------------------------------ -->
#### <a name="keyboard-accelerators"></a>键盘加速键

当 WebView2 具有焦点时，它会直接接收来自用户的输入。 应用可能想要截获和处理某些加速器键组合，或禁用正常的浏览器加速器键行为。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.arebrowseracceleratorkeysenabled)
* [CoreWebView2Controller.AcceleratorKeyPressed 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.acceleratorkeypressed)
   * [CoreWebView2AcceleratorKeyPressedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2acceleratorkeypressedeventargs)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#arebrowseracceleratorkeysenabled)
* [CoreWebView2Controller.AcceleratorKeyPressed 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#acceleratorkeypressed)
   * [CoreWebView2AcceleratorKeyPressedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2acceleratorkeypressedeventargs)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings3：：AreBrowserAcceleratorKeysEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings3#get_arebrowseracceleratorkeysenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings3#put_arebrowseracceleratorkeysenabled)
* [ICoreWebView2Controller：：AcceleratorKeyPressed 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_acceleratorkeypressed)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_acceleratorkeypressed)
   * [ICoreWebView2AcceleratorKeyPressedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2acceleratorkeypressedeventargs)

---


<!-- ------------------------------ -->
#### <a name="default-background-color"></a>默认背景色

WebView2 可以指定默认背景色。  颜色可以是任何不透明的颜色，也可以是透明的。  如果 HTML 页面未设置其自己的背景色，则将使用此颜色。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.DefaultBackgroundColor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.defaultbackgroundcolor)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.DefaultBackgroundColor 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#defaultbackgroundcolor)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller2：:D efaultBackgroundColor 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller2#get_defaultbackgroundcolor)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller2#put_defaultbackgroundcolor)

---


<!-- ====================================================================== -->
## <a name="rendering-webview2-using-composition"></a>使用合成呈现 WebView2

对于基于合成的 WebView2 呈现，请使用 `CoreWebView2Environment` 它来创建一个 `CoreWebView2CompositionController`。  `CoreWebView2CompositionController` 提供与之相同的 API `CoreWebView2Controller`，但也包括用于基于合成的呈现的 API。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController 类](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2compositioncontrollerasync)<!--2 overloads-->

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2compositioncontrollerasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController 接口](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller)
* [ICoreWebView2Environment3：：CreateCoreWebview2CompositionController 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment3#createcorewebview2compositioncontroller)

---


<!-- ------------------------------ -->
#### <a name="connecting-to-the-visual-tree"></a>连接到可视化树

WebView2 可以将其合成树连接到 [IDCompositionVisual](/windows/win32/api/dcomp/nn-dcomp-idcompositionvisual)、 [IDCompositionTarget](/windows/win32/api/dcomp/nn-dcomp-idcompositiontarget) 或 `Windows::UI::Composition::ContainerVisual`。<!--link these?  both plats?  not linked in wv2 api ref.  these are c++ not .net links -->

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.RootVisualTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.rootvisualtarget)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController.RootVisualTarget 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#rootvisualtarget)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController：：RootVisualTarget 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_rootvisualtarget)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#put_rootvisualtarget)

---

<!-- ------------------------------ -->
#### <a name="forwarding-input"></a>转发输入

应用程序接收 (鼠标、触摸、笔) 的空间输入，必须发送到 WebView2。  当光标应基于鼠标位置进行更新时，WebView2 会通知应用。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.Cursor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.cursor)
* [CoreWebView2CompositionController.CursorChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.cursorchanged)
* [CoreWebView2CompositionController.SystemCursorId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.systemcursorid)
* [CoreWebView2CompositionController.SendMouseInput 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.sendmouseinput)
* [CoreWebView2CompositionController.SendPointerInput 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.sendpointerinput)
* [CoreWebView2Environment.CreateCoreWebView2PointerInfo 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2pointerinfo)
   * [CoreWebView2PointerInfo 类](/dotnet/api/microsoft.web.webview2.core.corewebview2pointerinfo)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController.Cursor 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#cursor)
* [CoreWebView2CompositionController.CursorChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#cursorchanged)
* [CoreWebView2CompositionController.SendMouseInput 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#sendmouseinput)
* [CoreWebView2CompositionController.SendPointerInput 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#sendpointerinput)
* [CoreWebView2Environment.CreateCoreWebView2PointerInfo 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2pointerinfo)
   * [CoreWebView2PointerInfo 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2pointerinfo)

<!--TODO - not found, omit?
* `CoreWebView2CompositionController.SystemCursorId` Property
-->

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController：：Cursor 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_cursor)<!--no put-->
* [ICoreWebView2CompositionController：：CursorChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#add_cursorchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#remove_cursorchanged)
* [ICoreWebView2CompositionController：：SystemCursorId 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_systemcursorid)<!--no put-->
* [ICoreWebView2CompositionController：：SendMouseInput 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#sendmouseinput)
* [ICoreWebView2CompositionController：：SendPointerInput 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#sendpointerinput)
* [ICoreWebView2Environment3：：CreateCoreWebView2PointerInfo 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment3#createcorewebview2pointerinfo)
   * [ICoreWebView2PointerInfo 接口](/microsoft-edge/webview2/reference/win32/icorewebview2pointerinfo)

---

<!-- ------------------------------ -->
#### <a name="accessibility"></a>辅助功能

默认情况下，对于 Win32/C++ 应用，WebView2 将作为父 HWND 的子级显示在辅助功能树中。  WebView2 提供 API，以便更好地定位相对于应用程序中其他元素的 WebView2 内容。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

不适用。

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

不适用。

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController2：：AutomationProvider 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller2#get_automationprovider)<!--no put-->
* [ICoreWebView2Environment4：：GetAutomationProviderForWindow 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment4#getautomationproviderforwindow)<!--not in c#-->

---

<!-- ====================================================================== -->
## <a name="user-data"></a>用户数据

管理用户数据文件夹 (UDF) （即用户计算机上的文件夹）。  UDF 包含与主机应用和 WebView2 相关的数据。  WebView2 应用使用用户数据文件夹来存储浏览器数据，例如 Cookie、权限和缓存资源。

另请参阅：
* [管理用户数据文件夹](user-data-folder.md)

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)
* [CoreWebView2EnvironmentOptions.ExclusiveUserDataFolderAccess 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.exclusiveuserdatafolderaccess)
* [CoreWebView2Profile.ClearBrowsingDataAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2compositioncontrollerasync)
* [CoreWebView2Environment.CreateCoreWebView2ControllerOptions 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2controlleroptions)
* [CoreWebView2Environment.CreateCoreWebView2ControllerWithOptions 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2controllerasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Environment.UserDataFolder 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#userdatafolder)
* [CoreWebView2EnvironmentOptions.ExclusiveUserDataFolderAccess 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environmentoptions#exclusiveuserdatafolderaccess)
* [CoreWebView2Profile.ClearBrowsingDataAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2profile#clearbrowsingdataasync)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2compositioncontrollerasync)
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync (选项) 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2controllerasync)<!-- c#: might ~=CreateCoreWebView2CompositionControllerAsync -->
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2controllerasync-1)
* [CoreWebView2Environment.CreateCoreWebView2ControllerOptions 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2controlleroptions)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Environment7：：UserDataFolder 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2environment7#get_userdatafolder)<!--no put-->
* [ICoreWebView2EnvironmentOptions2：：ExclusiveUserDataFolderAccess 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2#get_exclusiveuserdatafolderaccess)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2#put_exclusiveuserdatafolderaccess)
* [ICoreWebView2Profile2：：ClearBrowsingData 方法](/microsoft-edge/webview2/reference/win32/icorewebview2profile2#clearbrowsingdata)
* [ICoreWebView2Profile2：：ClearBrowsingDataAll 方法](/microsoft-edge/webview2/reference/win32/icorewebview2profile2#clearbrowsingdataall)
* [ICoreWebView2Profile2：：ClearBrowsingDataInTimeRange 方法](/microsoft-edge/webview2/reference/win32/icorewebview2profile2#clearbrowsingdataintimerange)
* [ICoreWebView2Environment10：：CreateCoreWebView2CompositionControllerWithOptions 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment10#createcorewebview2compositioncontrollerwithoptions)<!-- c#: might ~=CreateCoreWebView2CompositionControllerAsync -->
* [ICoreWebView2Environment10：：CreateCoreWebView2ControllerOptions 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment10#createcorewebview2controlleroptions)
* [ICoreWebView2Environment10：：CreateCoreWebView2ControllerWithOptions 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment10#createcorewebview2controllerwithoptions)

---


<!-- ====================================================================== -->
## <a name="performance-and-debugging"></a>性能和调试

分析和调试性能、处理与性能相关的事件，以及管理内存使用情况，以提高应用的响应能力。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.MemoryUsageTargetLevel 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.memoryusagetargetlevel)
* [CoreWebView2.TrySuspendAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.trysuspendasync)
   * [CoreWebView2.IsSuspended 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.issuspended)
   * [CoreWebView2.Resume 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.resume)
* [CoreWebView2.OpenTaskManagerWindow 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.opentaskmanagerwindow) 

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.MemoryUsageTargetLevel 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#memoryusagetargetlevel)
* [CoreWebView2.TrySuspendAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#trysuspendasync)
   * [CoreWebView2.IsSuspended 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#issuspended)
   * [CoreWebView2.Resume 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#resume)
* [CoreWebView2.OpenTaskManagerWindow 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#opentaskmanagerwindow)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Experimental5：：MemoryUsageTargetLevel 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2experimental5#get_memoryusagetargetlevel)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimental5#put_memoryusagetargetlevel)
* [ICoreWebView2_3：：TrySuspend 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_3#trysuspend)
   * [ICoreWebView2_3：：IsSuspended 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_3#get_issuspended)<!--no put-->
   * [ICoreWebView2_3：：Resume 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_3#resume)
* [ICoreWebView2_6：：OpenTaskManagerWindow 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_6#opentaskmanagerwindow)

---


<!-- ====================================================================== -->
## <a name="chrome-developer-protocol-cdp"></a>Chrome 开发人员协议 (CDP) 

Chrome DevTools 协议提供用于检测、检查、调试和配置文件Chromium浏览器的 API。  Chrome DevTools 协议是 Microsoft Edge DevTools 的基础。  对于未在 WebView2 平台中实现的功能，请使用 Chrome DevTools 协议。

另请参阅：
* [在 WebView2 应用中使用 Chrome DevTools 协议](../how-to/chromium-devtools-protocol.md)
* [Chrome DevTools 协议](https://chromedevtools.github.io/devtools-protocol)


##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

开放：
* [CoreWebView2Settings.AreDevToolsEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.aredevtoolsenabled)
* [CoreWebView2.OpenDevToolsWindow 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.opendevtoolswindow)

叫：
* [CoreWebView2.CallDevToolsProtocolMethodAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.calldevtoolsprotocolmethodasync)
* [CoreWebView2.CallDevToolsProtocolMethodForSessionAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.calldevtoolsprotocolmethodforsessionasync)

接收机：
* [CoreWebView2.GetDevToolsProtocolEventReceiver 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.getdevtoolsprotocoleventreceiver)
   * [CoreWebView2DevToolsProtocolEventReceivedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2devtoolsprotocoleventreceivedeventargs)
   * [CoreWebView2DevToolsProtocolEventReceiver 类](/dotnet/api/microsoft.web.webview2.core.corewebview2devtoolsprotocoleventreceiver)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

开放：
* [CoreWebView2Settings.AreDevToolsEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#aredevtoolsenabled)
* [CoreWebView2.OpenDevToolsWindow 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#opendevtoolswindow)

叫：
* [CoreWebView2.CallDevToolsProtocolMethodAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#calldevtoolsprotocolmethodasync)
* [CoreWebView2.CallDevToolsProtocolMethodForSessionAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#calldevtoolsprotocolmethodforsessionasync)

接收机：
* [CoreWebView2.GetDevToolsProtocolEventReceiver 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#getdevtoolsprotocoleventreceiver)
   * [CoreWebView2DevToolsProtocolEventReceivedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2devtoolsprotocoleventreceivedeventargs)
   * [CoreWebView2DevToolsProtocolEventReceiver 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2devtoolsprotocoleventreceiver)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

开放：
* [ICoreWebView2Settings：：AreDevToolsEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_aredevtoolsenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_aredevtoolsenabled)
* [ICoreWebView2：：OpenDevToolsWindow 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#opendevtoolswindow)

叫：
* [ICoreWebView2：：CallDevToolsProtocolMethod 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#calldevtoolsprotocolmethod)
* [ICoreWebView2_11：：CallDevToolsProtocolMethodForSession 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_11#calldevtoolspotocolmethodforsession)

接收机：
* [ICoreWebView2：：GetDevToolsProtocolEventReceiver 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#getdevtoolsprotocoleventreceiver)
   * [ICoreWebView2DevToolsProtocolEventReceiver 接口](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver)
   * [ICoreWebView2DevToolsProtocolEventReceivedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceivedeventargs)

---

<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Microsoft Edge WebView2 简介](../index.md)
* [WebView2 API 参考](../webview2-api-reference.md) - 其他平台和语言（如 WinRT/C++ (COM) ）的 API 参考链接。
