---
title: WebView2 SDK 发行说明
description: 适用于 Win32、WPF 和 WinForms 的 Microsoft Edge WebView2 的发行说明。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/03/2022
ms.openlocfilehash: 5301530da8a20aa7057da941e627f28412f70a6c
ms.sourcegitcommit: 8a4a8c685bd5b68d95d879a12c642e435e000d86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2022
ms.locfileid: "12854483"
---
# <a name="release-notes-for-the-webview2-sdk"></a>WebView2 SDK 发行说明

WebView2 团队以四周的节奏更新 [WebView2 SDK](https://www.nuget.org/packages/Microsoft.Web.WebView2) 。 本文包含有关产品公告、添加、修改和 API 中断性变更的最新信息。

通常，发行说明适用于 [WebView2 API 参考](webview2-api-reference.md)中列出的受支持平台。

WebView2 bug 修复（如下面列出的修复程序）是特定于运行时的或特定于 SDK 的。


#### <a name="recommended-browser-channel-and-runtime"></a>推荐的浏览器通道和运行时

更新 WebView2 SDK NuGet 包后，请确保重新编译 WebView2 应用。  WebView2 团队建议以下内容：

* 使用 WebView2 SDK 包的预发行版进行开发时，请使用 Microsoft Edge 的 Canary 预览通道。  Canary 是推荐的预览频道，因为它以最快的节奏提供，并且具有最新的 API。

* 使用发布版本的 WebView2 SDK 包时，请使用 Evergreen WebView2 运行时。

有关详细信息，请参阅 [将运行时版本与 SDK 版本匹配](concepts/versioning.md#matching-the-runtime-version-with-the-sdk-version)。


#### <a name="minimum-version-of-the-browser-or-runtime-to-load-webview2"></a>用于加载 WebView2 的浏览器或运行时的最低版本

若要加载 WebView2，Microsoft Edge 或 WebView2 运行时的最低版本为 86.0.616.0。  仅当 Web 平台中发生中断性变更时，加载 WebView2 的最低版本才会更改。

若要将预发布 SDK 与 Microsoft Edge 预览频道一起使用，请参阅 [测试即将推出的 API 和功能](how-to/set-preview-channel.md)。


<!-- ====================================================================== -->
## <a name="10141822"></a>1.0.1418.22

发布日期：2022 年 10 月 31 日

[用于 WebView2 SDK 1.0.1418.22 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1418.22)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 107.0.1418.22 或更高版本。

### <a name="general"></a>概要

此 WebView2 SDK 版本具有与 WebView2 SDK 1.0.1466-prerelease 中相同的 bug 修复。 请参阅以下部分中的 **Bug 修复** 。


<!-- ====================================================================== -->
## <a name="101466-prerelease"></a>1.0.1466-prerelease

发布日期：2022 年 10 月 31 日

[用于 WebView2 SDK 1.0.1466-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1466-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 109.0.1466.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

* 添加了对创建具有指定大小的基于共享内存的缓冲区的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2SharedBuffer 类](/dotnet/api/microsoft.web.webview2.core.corewebview2sharedbuffer?view=webview2-dotnet-1.0.1466-prerelease&preserve-view=true)
    * `Buffer`
    * `FileMappingHandle`
    * `Size`
    * `Close`
    * `Dispose`
    * `OpenStream`

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2SharedBuffer 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2sharedbuffer?view=webview2-winrt-1.0.1466-prerelease&preserve-view=true)
    * `Buffer`
    * `Size`
    * `Close`
    * `OpenStream`

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ExperimentalSharedBuffer 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsharedbuffer?view=webview2-1.0.1466-prerelease&preserve-view=true)
    * `Close`
    * `get_Buffer`
    * `get_FileMappingHandle`
    * `get_Size`
    * `OpenStream`

---

*  添加了对从主帧或 `iframe`的脚本访问共享缓冲区对象的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PostSharedBufferToScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.postsharedbuffertoscript?view=webview2-dotnet-1.0.1466-prerelease&preserve-view=true)
* [CoreWebView2Frame.PostSharedBufferToScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2frame.postsharedbuffertoscript?view=webview2-dotnet-1.0.1466-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PostSharedBufferToScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1466-prerelease&preserve-view=true#postsharedbuffertoscript)
* [CoreWebView2Frame.PostSharedBufferToScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2frame?view=webview2-winrt-1.0.1466-prerelease&preserve-view=true#postsharedbuffertoscript)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Experimental18：:P ostSharedBufferToScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental18?view=webview2-1.0.1466-prerelease&preserve-view=true#postsharedbuffertoscript)
* [ICoreWebView2ExperimentalFrame4：:P ostSharedBufferToScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe4?view=webview2-1.0.1466-prerelease&preserve-view=true#postsharedbuffertoscript)

---

*  在当前顶级文档中添加了对从 `JavaScript` 参数运行 JavaScript 代码的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2ScriptException 类](/dotnet/api/microsoft.web.webview2.core.corewebview2scriptexception?view=webview2-dotnet-1.0.1466-prerelease&preserve-view=true)
   * `ColumnNumber`
   * `LineNumber`
   * `Message`
   * `Name`
   * `ToJson`

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2ScriptException 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2scriptexception?view=webview2-winrt-1.0.1466-prerelease&preserve-view=true)
   * `ColumnNumber`
   * `LineNumber`
   * `Message`
   * `Name`
   * `ToJson`

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ExperimentalScriptException 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalscriptexception?view=webview2-1.0.1466-prerelease&preserve-view=true)
   * `get_ColumnNumber`
   * `get_LineNumber`
   * `get_Message`
   * `get_Name`
   * `get_ToJson`

---

#### <a name="bug-fixes"></a>Bug 修复

*   修复了打印设置中的自定义标题可能错误的 bug。  ([问题 #2093](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2093)) 
*   以字符串的形式`Base64`在事件中`add_ClientCertificateRequested`显示`AllowedCertificateAuthorities`。  (运行时)  ([问题 #2346](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2346)) 
*   修复了打印设置中缺少默认页脚 URI 的 bug。  ([问题 #2851](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2851)) 
*   修复了生成与打印设置相关的 null 指针异常的 bug。  (运行时)  ([问题 #2858](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2858)) 
*   修复了在重定向到已配置了客户端证书身份验证的服务器以及订阅事件时 `WebResourceRequested` 报告导航失败的 bug。  (运行时) 
*   修复了以下 `AddHostObjectToScript` bug：当 JavaScript 调用异步方法，然后调用同步方法时，异步方法调用可能会失败。


<!-- ====================================================================== -->
## <a name="10137028"></a>1.0.1370.28

发布日期：2022 年 10 月 11 日

[用于 WebView2 SDK 1.0.1370.28 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1370.28)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 106.0.1370.28 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*  拖放 API：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.DragLeave 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.dragleave?view=webview2-dotnet-1.0.1370.28&preserve-view=true#microsoft-web-webview2-core-corewebview2compositioncontroller-dragleave)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [ICoreWebView2CompositionControllerInterop2.DragEnter 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1370.28&preserve-view=true#dragenter)
* [ICoreWebView2CompositionControllerInterop2.DragLeave 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1370.28&preserve-view=true#dragleave)
* [ICoreWebView2CompositionControllerInterop2.DragOver 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1370.28&preserve-view=true#dragover)
* [ICoreWebView2CompositionControllerInterop2.Drop 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1370.28&preserve-view=true#drop)
* [CoreWebView2CompositionController.DragLeave 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller?view=webview2-winrt-1.0.1370.28&preserve-view=true#dragleave)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController3：:D ragEnter 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1370.28&preserve-view=true#dragenter)
* [ICoreWebView2CompositionController3：:D ragLeave 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1370.28&preserve-view=true#dragleave)
* [ICoreWebView2CompositionController3：:D ragOver 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1370.28&preserve-view=true#dragover)
* [ICoreWebView2CompositionController3：:D rop 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1370.28&preserve-view=true#drop)

---


<!-- ====================================================================== -->
## <a name="101414-prerelease"></a>1.0.1414-prerelease

发布日期：2022 年 10 月 11 日

[用于 WebView2 SDK 1.0.1414-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1414-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 107.0.1414.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了对打印 API 的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PrintAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.printasync?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
* [CoreWebView2.PrintToPdfStreamAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.printtopdfstreamasync?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
* [CoreWebView2.ShowPrintUI 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.showprintui?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
* [CoreWebView2PrintSettings 类](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.Collation 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.collation?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.ColorMode 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.colormode?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.Copies 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.copies?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2printsettings-copies)
   * [CoreWebView2PrintSettings.Duplex 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.duplex?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.MediaSize 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.mediasize?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.PageRanges 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.pageranges?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.PagesPerSide 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.pagesperside?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.PrinterName 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2printsettings.printername?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PrintAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#printasync)
* [CoreWebView2.PrintToPdfStreamAsync](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#printtopdfstreamasync)
* [CoreWebView2.ShowPrintUI 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#showprintui)
* [CoreWebView2PrintSettings 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true)
   * [CoreWebView2PrintSettings.Collation 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#collation)
   * [CoreWebView2PrintSettings.ColorMode 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#colormode)
   * [CoreWebView2PrintSettings.Copies 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#copies)
   * [CoreWebView2PrintSettings.Duplex 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#duplex)
   * [CoreWebView2PrintSettings.MediaSize 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#mediasize)
   * [CoreWebView2PrintSettings.PageRanges 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#pageranges)
   * [CoreWebView2PrintSettings.PagesPerSide 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#pagesperside)
   * [CoreWebView2PrintSettings.PrinterName 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2printsettings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#printername)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Experimental17：:P rint 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental17?view=webview2-1.0.1414-prerelease&preserve-view=true#print)
* [ICoreWebView2Experimental17：:P rintToPdfStream 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental17?view=webview2-1.0.1414-prerelease&preserve-view=true#printtopdfstream)
* [ICoreWebView2Experimental17：：ShowPrintUI 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental17?view=webview2-1.0.1414-prerelease&preserve-view=true#showprintui)
* [ICoreWebView2ExperimentalPrintCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintcompletedhandler?view=webview2-1.0.1414-prerelease&preserve-view=true)
* [ICorewebView2ExperimentalPrintToPdfStreamCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprinttopdfstreamcompletedhandler?view=webview2-1.0.1414-prerelease&preserve-view=true)
* [ICoreWebView2ExperimentalPrintSettings2 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true)
   * [ICoreWebView2ExperimentalPrintSettings2：：Collation 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_collation)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_collation)
   * [ICoreWebView2ExperimentalPrintSettings2：：ColorMode 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_colormode)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_colormode)
   * [ICoreWebView2ExperimentalPrintSettings2：：Copies 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_copies)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_copies)
   * [ICoreWebView2ExperimentalPrintSettings2：:D uplex 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_duplex)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_duplex)
   * [ICoreWebView2ExperimentalPrintSettings2：：MediaSize 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_mediasize)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_mediasize)
   * [ICoreWebView2ExperimentalPrintSettings2：:P ageRanges 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_pageranges)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_pageranges)
   * [ICoreWebView2ExperimentalPrintSettings2：:P agesPerSide 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_pagesperside)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_pagesperside)
   * [ICoreWebView2ExperimentalPrintSettings2：:P rinterName 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_printername)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprintsettings2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_printername)

---

*  添加了对 SmartScreen API 的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.IsReputationCheckingRequired 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.isreputationcheckingrequired?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2settings-isreputationcheckingrequired)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.IsReputationCheckingRequired 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#isreputationcheckingrequired)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ExperimentalSettings7：：IsReputationCheckingRequired 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings7?view=webview2-1.0.1414-prerelease&preserve-view=true#get_isreputationcheckingrequired)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings7?view=webview2-1.0.1414-prerelease&preserve-view=true#put_isreputationcheckingrequired)

---

*  添加了对自定义崩溃报告 API 的支持：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2EnvironmentOptions.IsCustomCrashReportingEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.iscustomcrashreportingenabled?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2environmentoptions-iscustomcrashreportingenabled)

* [CoreWebView2Environment.FailureReportFolderPath 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.failurereportfolderpath?view=webview2-dotnet-1.0.1414-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2environment-failurereportfolderpath)


##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2EnvironmentOptions.IsCustomCrashReportingEnabled 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environmentoptions?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#iscustomcrashreportingenabled)
* [CoreWebView2Environment.FailureReportFolderPath 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment?view=webview2-winrt-1.0.1414-prerelease&preserve-view=true#failurereportfolderpath)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ExperimentalEnvironmentOptions2：：IsCustomCrashReportingEnabled 属性 (get](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions2?view=webview2-1.0.1414-prerelease&preserve-view=true#get_iscustomcrashreportingenabled)， [put) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions2?view=webview2-1.0.1414-prerelease&preserve-view=true#put_iscustomcrashreportingenabled)
* [ICoreWebView2ExperimentalEnvironment：：FailureReportFolderPath 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment?view=webview2-1.0.1414-prerelease&preserve-view=true#get_failurereportfolderpath)<!--no put-->

---

#### <a name="bug-fixes"></a>Bug 修复

*   从下载页面删除了链接断开的三点菜单。  (运行时)  ([问题 #2753](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2753)) 
*   修复了 WebView2 WinRT JS 投影工具 (wv2winrt) C++20 项目编译失败的 bug。   ([问题 #2768](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2768)) 
*   修复了在订阅任何事件（尤其是事件）时关闭 WebView2 时 WebView2 WinRT API 可能发生的 `CoreWebView2.GetDevToolsEventReceiver` 崩溃。 这是仅限 SDK 的更改。
*   修复了在最小化窗口后无法关闭下载弹出窗口的 bug。  (运行时) 


<!-- ====================================================================== -->
## <a name="10134322"></a>1.0.1343.22

发布日期：2022 年 9 月 6 日

[用于 WebView2 SDK 1.0.1343.22 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1343.22)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 105.0.1343.22 或更高版本。

### <a name="general"></a>概要

此 WebView2 SDK 版本具有与 WebView2 SDK 1.0.1369-prerelease 中相同的 bug 修复。  请参阅以下部分中的 **Bug 修复** 。


<!-- ====================================================================== -->
## <a name="101369-prerelease"></a>1.0.1369-prerelease

发布日期：2022 年 9 月 6 日

[用于 WebView2 SDK 1.0.1369-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1369-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 106.0.1369.0 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*  拖放 API：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.DragLeave 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.dragleave?view=webview2-dotnet-1.0.1369-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2compositioncontroller-dragleave)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [ICoreWebView2CompositionControllerInterop2.DragEnter 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1369-prerelease&preserve-view=true#dragenter)
* [ICoreWebView2CompositionControllerInterop2.DragLeave 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1369-prerelease&preserve-view=true#dragleave)
* [ICoreWebView2CompositionControllerInterop2.DragOver 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1369-prerelease&preserve-view=true#dragover)
* [ICoreWebView2CompositionControllerInterop2.Drop 方法](/microsoft-edge/webview2/reference/winrt/interop/icorewebview2compositioncontrollerinterop2?view=webview2-winrt-1.0.1369-prerelease&preserve-view=true#drop)
* [CoreWebView2CompositionController.DragLeave 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller?view=webview2-winrt-1.0.1369-prerelease&preserve-view=true#dragleave)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController3.DragEnter 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1369-prerelease&preserve-view=true#dragenter)
* [ICoreWebView2CompositionController3.DragLeave 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1369-prerelease&preserve-view=true#dragleave)
* [ICoreWebView2CompositionController3.DragOver 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1369-prerelease&preserve-view=true#dragover)
* [ICoreWebView2CompositionController3.Drop 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller3?view=webview2-1.0.1369-prerelease&preserve-view=true#drop)

---

#### <a name="bug-fixes"></a>Bug 修复

*  修复了关闭带有 WebView2 的窗口时 WPF 应用崩溃的 bug。  ([问题 #640](https://github.com/MicrosoftEdge/WebView2Feedback/issues/640)) 

*  修复了 (运行时) 同时生成 WebView 创建失败的 bug。 [问题 #2703](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2703)

*  修复了打印设置纸张大小，以支持小到 0.01 英寸 (运行时) 的尺寸。

*  修复了 WebView2 打印对话框每次将 **“缩放** ”设置重置为 **“适合可打印区域”** 的 bug。  ([问题 #2523](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2523)) 

*  修复了 **wv2winrt** 工具中某些项目中未引用 WinMD 文件的 bug。


<!-- ====================================================================== -->
## <a name="10129344"></a>1.0.1293.44

发布日期：2022 年 8 月 8 日

[用于 WebView2 SDK 1.0.1293.44 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1293.44)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 104.0.1293.44 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

* The Favicon API:

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.FaviconChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.faviconchanged?view=webview2-dotnet-1.0.1293.44&preserve-view=true)
* [CoreWebView2.FaviconUri 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.faviconuri?view=webview2-dotnet-1.0.1293.44&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.FaviconChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1293.44&preserve-view=true#faviconchanged)
* [CoreWebView2.FaviconUri 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1293.44&preserve-view=true#faviconuri)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_15：：FaviconChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1293.44&preserve-view=true#add_faviconchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1293.44&preserve-view=true#remove_faviconchanged)
* [ICoreWebView2_15：：FaviconUri 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1293.44&preserve-view=true#get_faviconuri)<!--no put-->

---


<!-- ====================================================================== -->
## <a name="101340-prerelease"></a>1.0.1340-prerelease

发布日期：2022 年 8 月 8 日

[用于 WebView2 SDK 1.0.1340-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1340-prerelease)

为了完全兼容 API，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 105.0.1340.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了对 `WebResourceRequested` 辅助角色的支持，允许设置筛选器，以便接收 `WebResourceRequested` 服务辅助角色、共享辅助角色和不同源 iFrame 的事件。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.AddWebResourceRequestedFilter (RequestSourceKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter?view=webview2-dotnet-1.0.1340-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2-addwebresourcerequestedfilter(system-string-microsoft-web-webview2-core-corewebview2webresourcecontext-microsoft-web-webview2-core-corewebview2webresourcerequestsourcekinds))
* [CoreWebView2.RemoveWebResourceRequestedFilter (RequestSourceKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.removewebresourcerequestedfilter?view=webview2-dotnet-1.0.1340-prerelease&preserve-view=true#microsoft-web-webview2-core-corewebview2-removewebresourcerequestedfilter(system-string-microsoft-web-webview2-core-corewebview2webresourcecontext-microsoft-web-webview2-core-corewebview2webresourcerequestsourcekinds))
* [CoreWebView2WebResourceRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcerequestedeventargs?view=webview2-dotnet-1.0.1340-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.AddWebResourceRequestedFilter (requestSourceKinds) 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1340-prerelease&preserve-view=true#addwebresourcerequestedfilter)
* [CoreWebView2.RemoveWebResourceRequestedFilter (requestSourceKinds) 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1340-prerelease&preserve-view=true#removewebresourcerequestedfilter)
* [CoreWebView2WebResourceRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2webresourcerequestedeventargs?view=webview2-winrt-1.0.1340-prerelease&preserve-view=true)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Experimental16.AddWebResourceRequestedFilterWithRequestSourceKinds 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental16?view=webview2-1.0.1340-prerelease&preserve-view=true#addwebresourcerequestedfilterwithrequestsourcekinds)
* [ICoreWebView2Experimental16.RemoveWebResourceRequestedFilterWithRequestSourceKinds 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimental16?view=webview2-1.0.1340-prerelease&preserve-view=true#removewebresourcerequestedfilterwithrequestsourcekinds)
* [ICoreWebView2ExperimentalWebResourceRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourcerequestedeventargs?view=webview2-1.0.1340-prerelease&preserve-view=true)

---

*  添加了对自定义方案注册的支持，使 WebView2 应用能够处理 `WebResourceRequested` 具有指定方案的请求的事件，并能够将 WebView2 控件导航到自定义方案。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2EnvironmentOptions 类](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions?view=webview2-dotnet-1.0.1340-prerelease&preserve-view=true)
* [CoreWebView2CustomSchemeRegistration 类](/dotnet/api/microsoft.web.webview2.core.corewebview2customschemeregistration?view=webview2-dotnet-1.0.1340-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2EnvironmentOptions 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environmentoptions?view=webview2-winrt-1.0.1340-prerelease&preserve-view=true)
* [CoreWebView2CustomSchemeRegistration 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2customschemeregistration?view=webview2-winrt-1.0.1340-prerelease&preserve-view=true)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2ExperimentalEnvironmentOptions 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-1.0.1340-prerelease&preserve-view=true)
* [ICoreWebView2ExperimentalCustomSchemeRegistration 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcustomschemeregistration?view=webview2-1.0.1340-prerelease&preserve-view=true)

---

#### <a name="bug-fixes"></a>Bug 修复

*   为开发人员添加了显式指定从中加载WebView2Loader.dll的路径的功能。  ([问题 #767](https://github.com/MicrosoftEdge/WebView2Feedback/issues/767)) 

*   在使用 `CallDevToolsProtocolMethod`时添加了有用的错误消息。  ([问题 #1609](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1609)) 

*   修复了在某些 .NET 应用中查找和加载 `WebView2Loader.dll` 的 bug。  ([问题 #2372](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2372)) 

*   修复了重试下载时未触发事件的 bug `DownloadStarting` 。  ([问题 #2489](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2489)) 

*   修复了路径太长时服务辅助角色缓存中的问题。  ([问题 #1900](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1900)) 

*   改进了 **JavaScript 中的 wv2winrt** `IMap` 和 `IMapView` 投影的性能。

*   添加对用作 WebView2 父窗口的HWND_MESSAGE的支持，以支持无外设方案。   ([问题 #202](https://github.com/MicrosoftEdge/WebView2Feedback/issues/202)) 

*   改进了以管理员用户应用身份运行的处理。

*   修复了在 UWP 应用中使用 WebView2 时的联机/脱机状态和通知。

*   现在可以为 WebView2 启用 GDI 缩放。  WebView2 将遵循托管应用程序的 GDI 缩放设置，而无需应用执行其他工作。   ([问题 #1700](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1700)) 

*   修复了关闭窗口模式的查找栏后焦点未返回到应用程序的 bug。  ([问题 #1225](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1225)) 


<!-- ====================================================================== -->
## <a name="10126442"></a>1.0.1264.42

发布日期：2022 年 7 月 4 日

[WebView2 SDK 1.0.1264.42 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1264.42)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 103.0.1264.42 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*  添加了 `ContextMenuRequested`API，使主机应用能够创建或修改其自己的上下文菜单。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested?view=webview2-dotnet-1.0.1264.42&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.ContextMenuRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1264.42&preserve-view=true#contextmenurequested)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_11：：add_ContextMenuRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1264.42&preserve-view=true#add_contextmenurequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1264.42&preserve-view=true#remove_contextmenurequested)

---


<!-- ====================================================================== -->
## <a name="101305-prerelease"></a>1.0.1305-prerelease

发布日期：2022 年 7 月 4 日

[用于 WebView2 SDK 1.0.1305-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1305-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 105.0.1305.0 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

* The Favicon API:

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.FaviconChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.faviconchanged?view=webview2-dotnet-1.0.1305-prerelease&preserve-view=true)
* [CoreWebView2.FaviconUri 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.faviconuri?view=webview2-dotnet-1.0.1305-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.FaviconChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1305-prerelease&preserve-view=true#faviconchanged)
* [CoreWebView2.FaviconUri 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1305-prerelease&preserve-view=true#faviconuri)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_15：：FaviconChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1305-prerelease&preserve-view=true#add_faviconchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1305-prerelease&preserve-view=true#remove_faviconchanged)
* [ICoreWebView2_15：：FaviconUri 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2_15?view=webview2-1.0.1305-prerelease&preserve-view=true#get_faviconuri)<!--no put-->

---

#### <a name="bug-fixes"></a>Bug 修复

*  修复了可能长时间挂起的问题 `PrintToPdfAsync` 。  ([问题 #1974](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1974)) 

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.PrintToPdfAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.printtopdfasync?view=webview2-dotnet-1.0.1305-prerelease&preserve-view=true)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.PrintToPdfAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2?view=webview2-winrt-1.0.1305-prerelease&preserve-view=true#printtopdfasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2_7：:P rintToPdf 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_7?view=webview2-1.0.1305-prerelease&preserve-view=true#printtopdf)

---

* 修复了当 WebView2 可见时 WebView2 从应用窃取焦点的回归。  ([问题 #862](https://github.com/MicrosoftEdge/WebView2Feedback/issues/862)) 


<!-- ====================================================================== -->
## <a name="10124522"></a>1.0.1245.22

发布日期：2022 年 6 月 14 日

[用于 WebView2 SDK 1.0.1245.22 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1245.22)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 102.0.1245.22 或更高版本。

没有相应的预发行版包。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

* [服务器证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_14?view=webview2-1.0.1245.22&preserve-view=true)，提供在应用程序级别信任服务器的 TLS 证书的选项。 它会呈现页面，而不会提示用户有关 TLS 或提供取消 Web 请求的功能。

*  [ClearBrowsingData API](/microsoft-edge/webview2/reference/win32/icorewebview2profile2?view=webview2-1.0.1245.22&preserve-view=true) 允许开发人员在一定期限内以编程方式清除特定数据类型：
   * `ClearBrowsingData`
   * `ClearBrowsingDataAll`
   * `ClearBrowsingDataInTimeRange`

*  [HttpStatusCode API](/microsoft-edge/webview2/reference/win32/icorewebview2navigationcompletedeventargs2?view=webview2-1.0.1245.22&preserve-view=true)，它为事件中的`NavigationCompleted`导航请求提供 HTTP 状态代码。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了屏幕键盘的问题，即通过单击 **X** 按钮关闭键盘后键盘不会重新出现。 还修复了当用户在 WebView2 中从一个编辑控件切换到另一个编辑控件时键盘被关闭的问题。  ([问题 #460](https://github.com/MicrosoftEdge/WebView2Feedback/issues/460)) 
*  修复了在脚本中使用代理 `AddHostObjectToScript` 时出现的问题。  如果调用 `setHostProperty` 失败，则可能收到了内部错误消息结构，而不是 JavaScript Error 对象。
*  修复了当 WebView2 可见时 WebView2 从应用窃取焦点的回归。   ([问题 #862](https://github.com/MicrosoftEdge/WebView2Feedback/issues/862)) 
*  修复了使用大数据的事件导致内存使用率 `WebResourceRequested` 增加的 bug。   ([问题 #2171](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2171)) 
*  修复 `StatusBarTextChanged` 了回归。 [再次使 StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1245.22&preserve-view=true) 与以前的版本兼容。  ([问题 #2414](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2414)) 
*  更好地支持以管理员身份运行的应用。 ([问题 #2356](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2356)) 


<!-- ====================================================================== -->
## <a name="10121039"></a>1.0.1210.39

发布日期：2022 年 5 月 9 日

[用于 WebView2 SDK 1.0.1210.39 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1210.39)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 101.0.1210.39 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

* 支持 WebView2 中的 [多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2environment10?view=webview2-1.0.1210.39&preserve-view=true) 。

* [主题 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1210.39&preserve-view=true) 提供了一种将 WebView2 颜色主题自定义为 `light`、 `dark`或 `system`的方法。

* [默认下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1210.39&preserve-view=true) ，提供自定义默认下载位置的方法。

<!-- ====================================================================== -->
## <a name="101248-prerelease"></a>1.0.1248-prerelease

发布日期：2022 年 5 月 9 日

[用于 WebView2 SDK 1.0.1248-prelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1248-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 102.0.1248.0 或更高版本。

### <a name="general"></a>概要

* 通过在 NuGet 包中添加 WinRT JS 投影工具 (**wv2winrt**) ，向 JavaScript 添加了对 WinRT 对象投影的支持。 有关使用 WinRT JS 投影工具的说明，请参阅 [从 Web 端代码调用本机端 WinRT 代码](/microsoft-edge/webview2/how-to/winrt-from-js)。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

* [服务器证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_14?view=webview2-1.0.1248-prerelease&preserve-view=true) 提供在应用程序级别信任服务器的 TLS 证书的选项，并在不提示用户有关 TLS 或提供取消 Web 请求的功能的情况下呈现页面。

* [ClearBrowsingData API](/microsoft-edge/webview2/reference/win32/icorewebview2profile2?view=webview2-1.0.1248-prerelease&preserve-view=true) 允许开发人员在一定期限内以编程方式清除特定数据类型：
   * `clearBrowsingDataInTimeRange`
   * `clearBrowsingDataAll`

#### <a name="bug-fixes"></a>Bug 修复

* 修复了 WPF 控件 `OnWindowPositionChanged` 的 事件中不可避免的崩溃。  ([问题 #1531](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1531)) 

* 修复了在 .NET SDK 中无法正常工作的问题 `CoreWebView2EnvironmentOptions.ExclusiveUserDataFolderAccess` 。  ([问题 #2363](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2363)) 

* 修复了导致某些使用主机对象的 Office 加载项在以前正常工作的操作期间崩溃的运行时回归。  ([问题 #2337](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2337)) 

* 修复了在具有不同缩放的监视器之间移动时 WebView2 内容可能变得模糊的问题。

* 修复了回归，以确保 WebView2 创建快速失败， `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` 而不是超时。

* 修复了Chromium更改破坏 WebView2 背景色的 bug。


<!-- ====================================================================== -->
## <a name="10118539"></a>1.0.1185.39

发布日期：2022 年 4 月 12 日

[用于 WebView2 SDK 1.0.1185.39 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1185.39)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 100.0.1185.39 或更高版本。

### <a name="general"></a>概要

* 已 `ICoreWebView2Certificate` 重命名为 `ICoreWebView2ClientCertificate`。

#### <a name="promotions"></a>促销

以下项现已稳定：

* 支持 `sessionId` CDP 方法调用的 [CallDevToolsProtocolMethodForSession API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1185.39&preserve-view=true#calldevtoolsprotocolmethodforsession)。

* [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1185.39&preserve-view=true)：
    *  `add_StatusBarTextChanged`
    *  `get_StatusBarText`
    *  `remove_StatusBarTextChanged`

* 支持启用/禁用外部放置操作的 [AllowExternalDrop API](/microsoft-edge/webview2/reference/win32/icorewebview2controller4?view=webview2-1.0.1185.39&preserve-view=true) 。

* [HiddenPdfToolbarItems API](/microsoft-edge/webview2/reference/win32/icorewebview2settings7?view=webview2-1.0.1185.39&preserve-view=true) 可用于自定义 PDF 工具栏项。

* [ExclusiveUserDataFolderAccess API](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2?view=webview2-1.0.1185.39&preserve-view=true) 允许控制其他进程是否可以使用`WebView2Environment`同一用户数据文件夹创建 WebView2，从而共享相同的 WebView 浏览器进程实例。

* 请求 [对 iframe 的权限支持](/microsoft-edge/webview2/reference/win32/icorewebview2frame3?view=webview2-1.0.1185.39&preserve-view=true)：
    * `add_PermissionRequested`
    * `remove_PermissionRequested`


<!-- ====================================================================== -->
## <a name="101222-prerelease"></a>1.0.1222-prerelease

发布日期：2022 年 4 月 12 日

[用于 WebView2 SDK 1.0.1222-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1222-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 102.0.1222.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

* 添加了 [服务器证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental15?view=webview2-1.0.1222-prerelease&preserve-view=true) ，它提供了一个选项，用于在应用程序级别信任服务器的 TLS 证书，并在不提示用户有关 TLS 或提供取消 Web 请求的功能的情况下呈现页面。

* 添加了 [Favicon API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental12?view=webview2-1.0.1222-prerelease&preserve-view=true) ，它提供了一种在网站更改或设置时获取 favicon 的方法。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

* 支持 WebView2 中的 [多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2environment10?view=webview2-1.0.1222-prerelease&preserve-view=true) 。

* [主题 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1222-prerelease&viewFallbackFrom=webview2-1.0.1185.39&preserve-view=true) 提供了一种将 WebView2 颜色主题自定义为 `light`、 `dark`或 `system`的方法。

* [默认下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2profile?view=webview2-1.0.1222-prerelease&viewFallbackFrom=webview2-1.0.1185.39&preserve-view=true) ，提供自定义默认下载位置的方法。

#### <a name="bug-fixes"></a>Bug 修复

* 修复了 `ZoomFactor` 在超出边界时将值错误地设置为 `ZoomFactor` 最大值的问题。

* 修复了在具有不同缩放的监视器之间移动时 WebView2 内容可能变得模糊的问题。

* 修复了在视觉托管模式下和 `MouseEvent.movementY` 始终为 **0** 的 bug`MouseEvent.movementX`。  ([问题 #2220](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2220)) 

* 修复了 WebView2 中密码回归导致的登录问题。  ([问题 #2291](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2291)) 

* 修复了用户打开新应用窗口且网页未分配导航项时出现的故障。

* 进行了运行时更改，修复了 WinUI 2 (UWP) 中未显示自有窗口的 bug。

* 修复了 `ICoreWebView2Frame::PostWebMessage` 源更新后的功能。  ([问题 #2267](https://github.com/MicrosoftEdge/WebView2Feedback/issues/2267)) 


<!-- ====================================================================== -->
## <a name="10115038"></a>1.0.1150.38

发布日期：2022 年 3 月 10 日

[用于 WebView2 SDK 1.0.1150.38 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1150.38)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 99.0.1150.38 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*   [BasicAuthentication API](/microsoft-edge/webview2/reference/win32/icorewebview2_10?view=webview2-1.0.1150.38&preserve-view=true)，使开发人员能够处理基本 HTTP 身份验证请求和响应。


<!-- ====================================================================== -->
## <a name="101189-prerelease"></a>1.0.1189-prerelease

发布日期：2022 年 3 月 10 日

[用于 WebView2 SDK 1.0.1189-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1189-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 100.0.1189.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*   添加了 [ContextMenuRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true) ，使主机应用能够创建或修改自己的上下文菜单。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

*    [CallDevToolsProtocolMethodForSession API](/microsoft-edge/webview2/reference/win32/icorewebview2_11?view=webview2-1.0.1189-prerelease&preserve-view=true#calldevtoolsprotocolmethodforsession)，它支持用于 CDP 方法调用的 sessionId。
*   [StatusBarText API](/microsoft-edge/webview2/reference/win32/icorewebview2_12?view=webview2-1.0.1189-prerelease&preserve-view=true)：
    *  `add_StatusBarTextChanged`
    *  `get_StatusBarText`
    *  `remove_StatusBarTextChanged`
*   支持启用/禁用外部 [删除的 AllowExternalDrop API](/microsoft-edge/webview2/reference/win32/icorewebview2controller4?view=webview2-1.0.1189-prerelease&preserve-view=true) 。
*    [HiddenPdfToolbarItems API](/microsoft-edge/webview2/reference/win32/icorewebview2settings7?view=webview2-1.0.1189-prerelease&preserve-view=true) 可用于自定义 PDF 工具栏项。
*  [ExclusiveUserDataFolderAccess API](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions2?view=webview2-1.0.1189-prerelease&preserve-view=true) 允许控制其他进程是否可以使用相同的用户数据文件夹创建 WebView2。

#### <a name="bug-fixes"></a>Bug 修复

*   修复了 WebView2 应用偶尔在 UWP 中卡住的 bug。
*   修复了关闭窗口模式的 **“查找** 栏”后焦点未返回到应用程序的 bug。
*   修复了在单页应用中未引发向后/向前导航的事件的 bug `DocumentTitleChanged` 。
*   修复了未为 Iframe 导航引发事件的 bug `HistoryChanged` 。


<!-- ====================================================================== -->
## <a name="10110844"></a>1.0.1108.44

发布日期：2022 年 2 月 6 日

[用于 WebView2 SDK 1.0.1108.44 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1108.44)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 98.0.1108.44 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*  [AdditionalAllowedFrameAncestors API](/microsoft-edge/webview2/reference/win32/icorewebview2navigationstartingeventargs2?view=webview2-1.0.1108.44&preserve-view=true)，使开发人员能够提供其他允许的帧上级。
*  [ProcessInfo API](/microsoft-edge/webview2/reference/win32/icorewebview2processinfo?view=webview2-1.0.1108.44&preserve-view=true) 提供有关 WebView2 进程和进程集合的详细信息。
*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame2?view=webview2-1.0.1108.44&preserve-view=true&preserve-view=true)：
   *  `add_NavigationStarting`
   *  `remove_NavigationStarting`
   *  `add_ContentLoading`
   *  `remove_ContentLoading`
   *  `add_NavigationCompleted`
   *  `remove_NavigationCompleted`
   *  `add_DOMContentLoaded`
   *  `remove_DOMContentLoaded`
   *  `ExecuteScript`
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`


<!-- ====================================================================== -->
## <a name="101158-prerelease"></a>1.0.1158-prerelease

发布日期：2022 年 2 月 6 日

[用于 WebView2 SDK 1.0.1158-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1158-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 100.0.1158.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [状态栏 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental13?view=webview2-1.0.1158-prerelease&preserve-view=true) ，用于在 webiew 显示状态消息、URL 或空字符串时提供信息。
*  添加了 [CDP API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental14?view=webview2-1.0.1158-prerelease&preserve-view=true) ，为开发人员提供了在 WebView2 中具有多个 `DevToolsProtocol` 目标的可能性。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

*  将 ICoreWebView2ClientCertificate 重命名为 [ICoreWebView2Certificate](/microsoft-edge/webview2/reference/win32/icorewebview2certificate?view=webview2-1.0.1158-prerelease&preserve-view=true)。
*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2frame3?view=webview2-1.0.1158-prerelease&preserve-view=true)：
   *  `add_PermissionRequested`
   *  `remove_PermissionRequested`

#### <a name="bug-fixes"></a>Bug 修复

*  修复了导致 Visual Studio 错误列表窗口中出现错误警告的问题。   ([问题 #1722](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1722)) 
*  修复了打开 PDF 下载时未引发 NewWindowRequested 的 bug。
*  解决了 WinUI 3 中不显示选择下拉列表的 bug。   ([问题 #1693](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1693)) 
*  添加了切换 WebView2 静音状态的功能，即使没有音频播放也是如此。


<!-- ====================================================================== -->
## <a name="10107254"></a>1.0.1072.54

发布日期：2022 年 1 月 13 日

[用于 WebView2 SDK 1.0.1072.54 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1072.54)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 97.0.1072.54 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

以下项现已稳定：

*  媒体 [API](/microsoft-edge/webview2/reference/win32/icorewebview2_8?view=webview2-1.0.1072.54&preserve-view=true#summary) ，使开发人员能够在 WebView2 中将媒体静音/取消静音。
*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2_9?view=webview2-1.0.1072.54&preserve-view=true) 可实现：
   *  更改下载对话框相对于 WebView2 边界的位置。  可以将下载对话框定位到“ **下载** ”按钮，而不是默认位置（右上角）。
   *  以编程方式打开和关闭默认下载对话框。
   *  做出更改以响应打开和关闭对话框。


<!-- ====================================================================== -->
## <a name="101133-prerelease"></a>1.0.1133-prerelease

发布日期：2022 年 1 月 13 日

[用于 WebView2 SDK 1.0.1133-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1133-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 99.0.1133.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [对主题](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile2?view=webview2-1.0.1133-prerelease&preserve-view=true) (整体配色方案的支持 - 浅色、深色、WebView2 的系统) 。
*  添加了设置 [默认下载路径](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile3?view=webview2-1.0.1133-prerelease&preserve-view=true)的方法。
*  添加了对 [清除浏览器数据](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4?view=webview2-1.0.1133-prerelease&preserve-view=true)的支持。
*  添加了对 iframe [请求的权限](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe3?view=webview2-1.0.1133-prerelease&preserve-view=true) 支持。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

*  [适用于 iframe 的新 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1133-prerelease&preserve-view=true)：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`
*  ProcessInfo API 提供有关 WebView2 [进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1133-prerelease&preserve-view=true) 和 [进程集合](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1133-prerelease&preserve-view=true)的详细信息。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1133-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 `Set-Cookies` 阻止标头显示在事件中的 `WebResourceResponseReceived` bug。
*  解决了弹出窗口和拥有的窗口在关闭之前会跳到其他位置而不是随应用窗口一起关闭的 bug。 此 bug 仅在很短的时间内处于活动状态。
*  修复了关闭文件选取器对话框后的焦点问题。
*  修复了 WebView2 可见性不随 WebView2 可见性更改页面上的“查找”UI 可见性的 bug。
*  修复了无法找到/加载 `WebView2Loader.dll`的 bug`GetAvailableBrowserVersionString()`。  ([问题 #1236](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1236)) 
*  固定了未处理事件时`NewWindowRequested`使用 `window.open` 创建的新窗口的大小和位置。  ([问题 #1343](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1343)) 
*  修复了禁用上下文菜单时，迷你菜单仍显示在所选文本上的 bug。 此更改特定于运行时。  ([问题 #1345](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1345)) 
*  修复了在 WinForms 中切换应用后焦点返回到错误位置的 bug。


<!-- ====================================================================== -->
## <a name="101083-prerelease"></a>1.0.1083-prerelease

发布日期：2021 年 11 月 29 日

[用于 WebView2 SDK 1.0.1083-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1083-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 97.0.1083.0 或更高版本。

### <a name="experimental-features"></a>实验功能

* 在 WebView2 中 [为 iframe](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe2?view=webview2-1.0.1083-prerelease&preserve-view=true) 添加了以下 API：
   *  `PostWebMessageAsJson`
   *  `PostWebMessageAsString`
   *  `add_WebMessageReceived`
   *  `remove_WebMessageReceived`

* 添加了 ProcessInfo API，以提供有关 WebView2 [进程](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfo?view=webview2-1.0.1083-prerelease&preserve-view=true) 和 [进程集合](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprocessinfocollection?view=webview2-1.0.1083-prerelease&preserve-view=true)的详细信息。

### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：

*  媒体 [API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1083-prerelease&preserve-view=true#summary) ，使开发人员能够在 WebView2 中将媒体静音/取消静音。
*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1083-prerelease&preserve-view=true)。  此 API 可实现：
   *  更改下载对话框相对于 WebView2 边界的位置。  可以将下载对话框定位到“ **下载** ”按钮，而不是默认位置（右上角）。
   *  以编程方式打开和关闭默认下载对话框。
   *  做出更改以响应打开和关闭对话框。

### <a name="bug-fixes"></a>Bug 修复

*  修复了关闭文件选取器对话框后焦点问题。
*  修复了 WebView2 在初始启动时不接收空间输入的 bug。
*  修复了 WebView2 中阻止单一登录的问题。
*  解决了下载对话框未随 WPF 和 WinForms 上的窗口移动的 bug。
*  更新了兼容的命令行检查，以防止需要对可选开关进行版本检查。
*  修复了导致“Microsoft Edge”品牌显示在辅助功能树中的错误。


<!-- ====================================================================== -->
## <a name="10105431"></a>1.0.1054.31

发布日期：2021 年 11 月 29 日

[用于 WebView2 SDK 1.0.1054.31 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1054.31)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 96.0.1054.31 或更高版本。

### <a name="general"></a>概要

*  常规可靠性修复。

### <a name="bug-fixes"></a>Bug 修复

*  关闭了 v96 WebView2 运行时的控制流强制技术 (CET) 阴影堆栈功能。
*  修复了在 .NET 单文件应用程序中启动时导致启动时间变慢的问题。  ([问题 #1909](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1909)) 
*  修复了由于 Microsoft Edge 浏览器策略错误地应用于 WebView2 而导致的崩溃。  ([问题 #1860](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1860)) 
*  修复了关闭包含下载对话框的弹出窗口时发生的崩溃。  ([问题 #1765](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1765)) & ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 


<!-- ====================================================================== -->
## <a name="101056-prerelease"></a>1.0.1056-prerelease

发布日期：2021 年 10 月 29 日

[用于 WebView2 SDK 1.0.1056-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1056-prerelease)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 Microsoft Edge 版本 97.0.1056.0 或更高版本。

### <a name="general"></a>概要

*  常规可靠性改进。

#### <a name="experimental-features"></a>实验功能

*  [下载定位和定位 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental11?view=webview2-1.0.1056-prerelease&preserve-view=true)。  此 API 可实现：
   *  更改下载对话框相对于 WebView2 边界的位置。  可以将下载对话框定位到“ **下载** ”按钮，而不是默认位置（右上角）。
   *  以编程方式打开和关闭默认下载对话框。
   *  做出更改以响应打开和关闭对话框。
*  [HTTP 身份验证 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental10?view=webview2-1.0.1056-prerelease&preserve-view=true)。

#### <a name="bug-fixes"></a>Bug 修复

*  实际进程退出代码现在作为 中提供`ExitCode``ICoreWebView2ProcessFailedEventArgs2`，用于`COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED`处理进程失败。
*  现在`AdditionalBrowserArguments`，在 `--js-flags` 中提供的 `CoreWebView2EnvironmentOptions`中采用开关。
*  修复了对 `name` JavaScript 中主机对象的 属性的访问。  ([问题 #641](https://github.com/MicrosoftEdge/WebView2Feedback/issues/641)) 
*  `InvalidCastException`修复了在事件循环启动之前隐式初始化 WPF 控件中的 。  ([问题 #1577](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1577)) 


<!-- ====================================================================== -->
## <a name="10102030"></a>1.0.1020.30

发布日期：2021 年 10 月 25 日

[用于 WebView2 SDK 1.0.1020.30 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1020.30)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 95.0.1020.30 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  更新 `EnsureCoreWebView2Async` 为在设置 WPF 源属性时不引发异常。  ([问题 #1781](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1781)) 
*  修复了 WebView2 在与显示下载 UI 的多个窗口交互后崩溃的 bug。  ([问题 #1723](https://github.com/MicrosoftEdge/WebView2Feedback/issues/1723)) 

#### <a name="promotions"></a>促销

以下项现已稳定：
*  [PrintToPdf API](/microsoft-edge/webview2/reference/win32/icorewebview2_7?view=webview2-1.0.1020.30&preserve-view=true#printtopdf)。


<!-- ====================================================================== -->
## <a name="1099228"></a>1.0.992.28

发布日期：2021 年 9 月 27 日

[用于 WebView2 SDK 1.0.992.28 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.992.28)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 94.0.992.31 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了缺少 WebView2 DLL (导致初始化失败) `PlatformTarget` 未在用户的 .NET 项目中设置的问题。  ([问题 #1061](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1061)) 

#### <a name="promotions"></a>促销

以下项现已稳定：
*  [OpenTaskManagerWindow API](/microsoft-edge/webview2/reference/win32/icorewebview2_6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [isSwipeNavigationEnabled 属性](/microsoft-edge/webview2/reference/win32/icorewebview2settings6?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  [BrowserProcessExited API](/microsoft-edge/webview2/reference/win32/icorewebview2browserprocessexitedeventargs?view=webview2-1.0.992.28&preserve-view=true#summary)。
*  接口上的`ICoreWebView2NewWindowRequestedEventArgs2`[get_Name属性](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs2?view=webview2-1.0.992.28#get_name&preserve-view=true#summary)。


<!-- ====================================================================== -->
## <a name="101018-prerelease"></a>1.0.1018-prerelease

发布日期：2021 年 9 月 20 日

[用于 WebView2 SDK 1.0.1018-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1018-prerelease)

为了完全实现 API 兼容性，此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 95.0.1018.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [一个媒体 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental9?view=webview2-1.0.1018-prerelease&preserve-view=true#summary) ，使开发人员能够在 WebView2 中将媒体静音/取消静音。
*  添加了对 WebView2 [的多个用户配置文件](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment8?view=webview2-1.0.1018-prerelease&preserve-view=true) 的支持。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了当应用跨监视器且监视器缩放发生更改时 WebView2 停止呈现的 bug。
*  修复了在打开多个下载窗口时关闭下载 UI 时 WebView2 崩溃的 bug。  ([问题 #1723](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1723)) 
*  修复了未在用户的 .NET 项目中设置 PlatformTarget 时出现生成/初始化错误。  ([问题 #730](https://github.com/MicrosoftEdge/WebViewFeedback/issues/730) 和 [问题 #1548](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1548)) 


<!-- ====================================================================== -->
## <a name="101010-prerelease"></a>1.0.1010-prerelease

发布日期：2021 年 9 月 14 日

[用于 WebView2 SDK 1.0.1010-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.1010-prerelease)

为了完全实现 API 兼容性，此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 95.0.1010.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  可靠性修复。  ([问题 #1605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1605) 和 [问题 #1678](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1678)) 
*  在启动期间和主机应用位于前台时，添加了性能改进。

#### <a name="experimental-features"></a>实验功能

*  通过使用 `EnsureCoreWebView2Async`删除了无提示故障，当多次调用时，使用不兼容的参数引发 `ArgumentException` 。
*  更改了环境对象中 [UserDataFolder](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment5?view=webview2-1.0.1010-prerelease&preserve-view=true#get_userdatafolder) 属性的默认处理。

   > [!CAUTION]
   > **中断性变更**：如果用户数据文件夹的默认处理方式（如果开发人员未指定放置位置）将发生更改。  请参阅 [公告：用户目录文件夹默认处理更新](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1410)。

*  为 iframe 添加了 [导航&脚本 API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.1010-prerelease&preserve-view=true) 。
*  添加了 [MemoryUsageTargetLevel](/microsoft-edge/webview2/reference/win32/icorewebview2experimental5?view=webview2-1.0.1010-prerelease&preserve-view=true) ，它允许开发人员指定内存消耗级别，例如低或正常。
*  向环境选项添加了 [ExclusiveUserDataFolderAccess](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-1.0.1010-prerelease&preserve-view=true) 。
*  添加了 [HiddenPdfToolbarItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.1010-prerelease&preserve-view=true) 以自定义 PDF 工具栏项。
*  添加了 [PrintToPdf](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprinttopdfcompletedhandler?view=webview2-1.0.1010-prerelease&preserve-view=true)，允许将当前页打印为 PDF。 此外，还可以通过此新 API 使用可选的自定义设置。
*  添加了 [AllowExternalDrop](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.1010-prerelease&preserve-view=true) 属性，以允许从 WebView2 控件外部拖放对象。
*  添加了允许自定义 WebView2 上下文菜单的 [ContextMenu API](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem?view=webview2-1.0.1010-prerelease&preserve-view=true) 。

#### <a name="bug-fixes"></a>Bug 修复

*  改进了在 JavaScript 代码中捕获主机对象异常的方式。
*  已将 WebView2 图标替换为 DevTools 窗口中的通用图标。
*  使用 时 `MediaDevices.getDisplayMedia()` 打开选项卡屏幕共享选项。  ([问题 #1566](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1566)) 
*  修复了未选择正确证书时客户端证书 API 中的 bug。 这是运行时更改。  ([问题 #1666](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1666)) 
*  修复了同一父域的新窗口中不可用的 bug `window.chrome.webview` 。 此更改特定于运行时。  ([问题 #1144](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1144)) 
*  修复了下拉菜单或列表显示在具有焦点的窗口后面的错误。  ([问题 #411](https://github.com/MicrosoftEdge/WebViewFeedback/issues/411)) 
*  修复了使用 `put_IsVisible(false)`时的焦点问题。  ([问题 #238](https://github.com/MicrosoftEdge/WebViewFeedback/issues/238)) 
*  修复了应用于 `SetVirtualHostNameToFolderMapping` 弹出窗口的 bug。
*  修复了将对象返回为 `IUnknown`的 bug`IDispatch`。

#### <a name="promotions"></a>促销

在此预发布 SDK 中，以下 API 将提升为稳定：
*  `IsSwipeNavigationEnabled`
*  `BrowserProcessExited`
*  `OpenBrowserTaskManager`


<!-- ====================================================================== -->
## <a name="1096133"></a>1.0.961.33

发布日期：2021 年 9 月 8 日

[用于 WebView2 SDK 1.0.961.33 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.961.33)

为了完全兼容 API，此版本的 WebView2 SDK 需要 WebView2 运行时版本 93.0.961.44 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 `ERR_SSL_CLIENT_AUTH_CERT_NEEDED` 导致错误的 bug。 这是运行时更改。
*  修复了无法使用 关闭`AreBrowserAcceleratorKeysEnabled`特殊浏览器键（如 **“刷新****”、“开始****”、“后退”** 等）的 bug。 此更改特定于运行时。
*  修复了不呈现透明背景色的 bug。
*  修复了加载 WebView2 时导致白色闪烁的 bug。
*  修复了 WebView2 .NET 控件中的 bug，其中 WebView2 窗口在后台创建时为空。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 
*  修复了用户导航到或新窗口显示 `about:blank` 页面时设置未更新的 bug。 这是运行时更改。

#### <a name="promotions"></a>促销

以下项现已稳定：
*  [客户端证书 API](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.961.33&preserve-view=true#add_clientcertificaterequested)。


<!-- ====================================================================== -->
## <a name="10955-prerelease"></a>1.0.955-prerelease

发布日期：2021 年 7 月 26 日

[用于 WebView2 SDK 1.0.955-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.955-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK 需要 Microsoft Edge 版本 93.0.967.0 或更高版本。

### <a name="general"></a>概要
*  WebView2 性能改进。
*  添加了 Windows (ETW 的部分事件跟踪) 支持。
*  从 `edge://history`中删除了 Microsoft 品牌。
*  新的默认下载 UI。

#### <a name="experimental-features"></a>实验功能

*  添加了 [OpenTaskManagerWindow](/microsoft-edge/webview2/reference/win32/icorewebview2experimental4?view=webview2-1.0.955-prerelease&preserve-view=true#opentaskmanagerwindow) 以启动 WebView2 浏览器任务管理器。
*  添加了 [NewWindowRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-1.0.955-prerelease&preserve-view=true#get_name)。
*  添加了对虚拟主机名映射的支持，以使用服务辅助角色。
*  添加了 [HiddenPdfToolbarItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings6?view=webview2-1.0.955-prerelease&preserve-view=true#get_hiddenpdftoolbaritems) 以自定义 PDF 工具栏项。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了破坏 和 `edge://history` 页的 `edge://downloads` bug。 此更改特定于运行时。
*  修复了 bug 以提高WebView2Loader.dll的可靠性。
*  修复了事件处理程序在 `NewWindowRequested` 处理使用 `target=_blank`的链接时启动两个窗口的 bug。
*  修复了 WebView2 视觉对象托管在启动前闪烁的 bug。
*  修复了在使用 `add_NewWindowRequested`创建的 WebView2 控件上不起作用时的 `add_WebResourceRequested` bug。  ([问题 #616](https://github.com/MicrosoftEdge/WebViewFeedback/issues/616)) 
*  允许主机应用在不同的应用程序上设置前台，以响应事件，包括 `NavigationStarting`、 `AddHostObjectToScript` 方法、 `WebMessageReceived`和 `NewWindowRequested`。  ([问题 #1092](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1092)) 
*  修复 bug 以触发 `PermissionRequested` 麦克风的事件。 此更改是特定于运行时的. ([问题 #1462](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1462)) 
*  修复了几次成功运行后被阻止的 `ExecuteScriptAsync` bug。 此更改特定于运行时。  ([问题 #1348](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1348)) 
*  修复了阻止在 中使用 `ResultFilePath` 非 ASCII 文件名的 `DownloadStartingEventArgs`bug。  ([问题 #1428](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1428)) 
*  修复了默认弹出窗口上的标题栏未完全显示的问题。 此更改特定于运行时。  ([问题 #1016](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1016)) 

#### <a name="promotions"></a>促销
*  [add_ClientCertificateRequested](/microsoft-edge/webview2/reference/win32/icorewebview2_5?view=webview2-1.0.955-prerelease&preserve-view=true#add_clientcertificaterequested) 被提升为稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 WebView2 .NET API 参考文档中导致仅显示第一个异常的问题。
*  .NET Core 库现在以发布模式生成。 若要调试，请确保清除“ **仅我的代码** ”复选框。
*  修复了在具有子窗体的窗体上导致 WebView2 崩溃的 bug。 打开页栏中的“查找”的子窗体导致 WebView2 在关闭子窗体时崩溃。  ([问题 #1097](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1097)) 


<!-- ====================================================================== -->
## <a name="1090249"></a>1.0.902.49

发布日期：2021 年 7 月 26 日

[用于 WebView2 SDK 1.0.902.49 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902.49)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 92.0.902.49 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复
*  修复了破坏 `IsBuiltInErrorPageEnabled` 属性的 bug，该 bug 关闭了导航失败或呈现进程失败时显示的错误页。  此更改特定于运行时。  ([问题 #634](https://github.com/MicrosoftEdge/WebViewFeedback/issues/634)) 
*  修复了 WebView2 控件将焦点从用户焦点移开的问题。
*  修复了在子窗口上不起作用时的 `AddScriptToExecuteOnDocumentCreated` bug。  ([问题 #935](https://github.com/MicrosoftEdge/WebViewFeedback/issues/935)) 
*  修复了导致非活动选项卡自动丢弃的 bug。  ([问题 #637](https://github.com/MicrosoftEdge/WebViewFeedback/issues/637)) 
*  修复了导航事件被另一个导航事件中断导致事件的导航 ID 不正确时出现的 `NavigationCompleted` bug。  ([问题 #1142](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1142)) 

#### <a name="promotions"></a>促销

以下项现在处于稳定状态：

*  [add_FrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902.49&preserve-view=true#add_framecreated)。
*  [get_IsGeneralAutofillEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902.49&preserve-view=true#get_isgeneralautofillenabled)。
*  [get_IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902.49&preserve-view=true#get_ispinchzoomenabled)。
*  [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting)。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 支持 iFrame 元素的 API。


<!-- ====================================================================== -->
## <a name="10902-prerelease"></a>1.0.902-prerelease

发布日期：2021 年 6 月 1 日

[用于 WebView2 SDK 1.0.902-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.902-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK 需要 Microsoft Edge 版本 92.0.902.0 或更高版本。

### <a name="general"></a>概要

*  改进了 WebView2 启动性能和磁盘占用情况。

#### <a name="experimental-features"></a>实验功能

*  添加了 [IsSwipeNavigationEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_isswipenavigationenabled) 属性，以启用或禁用最终用户在支持触摸输入的设备上使用轻扫手势在 WebView2 中导航的功能。
*  添加了 [BrowserProcessExited](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment4?view=webview2-1.0.902-prerelease&preserve-view=true#add_browserprocessexited) 事件。
*  添加了 [add_ClientCertificateRequested API](/microsoft-edge/webview2/reference/win32/icorewebview2experimental3?view=webview2-1.0.902-prerelease&preserve-view=true#add_clientcertificaterequested)。 它允许在需要时显示客户端证书对话框提示，并允许访问所需的元数据来替换默认的客户端证书对话框提示。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了鼠标左键单击不关闭上下文菜单的 bug。 此更改特定于运行时。
*  修复了当共享同一用户数据文件夹的应用的 exe 文件的版本信息不一致时，WebView2 创建失败的 bug。
*  修复了一个 bug，`Home`即 、 和 `Back` 等`Refresh`特殊浏览器键不能被 `AreBrowserAcceleratorKeysEnabled`禁用。 此更改特定于运行时。
*  修复了 WebView2 .NET 控件中的 bug，其中 WebView2 窗口在后台创建时为空。  ([问题 #1077](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1077)) 。
*  通过使用 WebView2 控件按 `Enter` 或 `Esc` 不再崩溃 WPF 应用程序来关闭文件选取器对话框。  ([问题 #1099](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1099)) 。
*  修复了附加事件处理程序时 `WebResourceRequested` [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions#get_allowsinglesignonusingosprimaryaccount) 无法与 WebView2 正常工作的 bug。 此更改特定于运行时。  ([问题 #1183](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1183)) 。
*  下载文件不再破坏 WebView2 `DefaultBackgroundColor` 透明度。 此更改特定于运行时。  ([问题 #1108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1108)) 。
*  删除了包含 Microsoft 品牌的屏幕共享媒体选取器消息。  ([问题 #940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 WebView2 WinForm 控件中的 bug：隐藏父窗体不会隐藏 WebView2 控件 ([问题 #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828) 和 [问题 #1079](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1079)) 。
*  向 WebView2 的 WPF 窗口添加了静态WS_CLIPCHILDREN样式。  ([问题 #1013](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1013)) 。
*  修复了右键单击链接导致 WebView2 主机应用崩溃的 bug。 此更改特定于运行时。
*  修复了在迁移到较新的 Edge WebView2 运行时版本时可能会使主机应用进程崩溃的可靠性 bug。
*  **弃用**：正式弃用了适用于 Windows 7 的 `DefaultBackgroundColor` API。

#### <a name="promotions"></a>促销

*  [下载 API](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_downloadstarting) 现已提升为稳定。
*  [PinchZoom API](/microsoft-edge/webview2/reference/win32/icorewebview2settings5?view=webview2-1.0.902-prerelease&preserve-view=true#get_ispinchzoomenabled) 现已提升为稳定。
*  [AddFrameCreated](/microsoft-edge/webview2/reference/win32/icorewebview2_4?view=webview2-1.0.902-prerelease&preserve-view=true#add_framecreated) 现已提升为稳定。
*  [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2frame?view=webview2-1.0.902-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 通过 iFrame 元素支持提升为稳定 API。
*  [自动填充 API](/microsoft-edge/webview2/reference/win32/icorewebview2settings4?view=webview2-1.0.902-prerelease&preserve-view=true#get_isgeneralautofillenabled) 现已提升为稳定。
   > [!NOTE]
   > 当前没有用于删除本地存储的常规自动填充和密码自动保存信息的 API。  请提供删除数据的控件，这将涉及删除整个用户数据文件夹。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 WebView2 WinForm 控件中的 bug，即在释放父窗口后 WebView2 窗口可见性未正确更新。  ([问题 #1282](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1282) 和 [问题 #828](https://github.com/MicrosoftEdge/WebViewFeedback/issues/828)) 。
*  修复了 WebView2 WPF 控件中的 Bug：WPF OneWay 绑定模式下的源属性绑定无法正常工作。  ([问题 #619](https://github.com/MicrosoftEdge/WebViewFeedback/issues/619) 和 [问题 #608](https://github.com/MicrosoftEdge/WebViewFeedback/issues/608)) 。


<!-- ====================================================================== -->
## <a name="1086435"></a>1.0.864.35

发布日期：2021 年 5 月 31 日

[用于 WebView2 SDK 1.0.864.35 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.864.35)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 91.0.864.35 或更高版本。

### <a name="general"></a>概要

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在迁移到较新的 Edge WebView2 运行时版本时可能会使主机应用进程崩溃的可靠性 bug。
*  修复了在某些情况下阻止内存清除的 bug。 此更改特定于运行时。
*  修复了 818 SDK 发布包中项目找不到该文件的错误 `WebView2.h` 。  ([问题 #1209](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1209)) 。
*  修复了导致某些具有二进制体的请求删除 WebResourceRequested 事件的 bug。
*  改进 `NewWindowRequested` 文档。  ([问题 #448](https://github.com/MicrosoftEdge/WebViewFeedback/issues/448)) 。

#### <a name="promotions"></a>促销
*  [UserAgent API](/microsoft-edge/webview2/reference/win32/icorewebview2settings2?view=webview2-1.0.864.35&preserve-view=true#get_useragent) 现已稳定。
*  [AreBrowserkeysenabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings3?view=webview2-1.0.864.35&preserve-view=true#get_arebrowseracceleratorkeysenabled) 现已稳定。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复
*  修复了 WebView2 .NET 控件中循环访问 `CoreWebView2WebResourceRequest` 标头集合时缺少第一个标头的 bug。  ([问题 #1123](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1123)) 。


<!-- ====================================================================== -->
## <a name="10865-prerelease"></a>1.0.865-prerelease

发布日期：2021 年 4 月 26 日

[用于 WebView2 SDK 1.0.865-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.865-prerelease)

为了完全实现 API 兼容性，此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 91.0.865.0 或更高版本。

### <a name="general"></a>概要

#### <a name="experimental-features"></a>实验功能

*  添加了 [IsPinchZoomEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings4?view=webview2-1.0.865-prerelease&preserve-view=true#ispinchzoomenabled) 设置。 它允许在设置中打开或关闭页面缩放控件。
*  添加了自定义 [add_DownloadStarting](/microsoft-edge/webview2/reference/win32/icorewebview2experimental2?view=webview2-1.0.865-prerelease&preserve-view=true#add_downloadstarting) API。  它允许你阻止下载，保存到其他路径，并访问所需的元数据来生成自定义下载 UI。
*  从 [AddHostObjectToScriptWithOrigins](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalframe?view=webview2-1.0.865-prerelease&preserve-view=true#addhostobjecttoscriptwithorigins) 添加了`iframe`元素支持。
*  添加了 [WPF 示例应用](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser) 的示例代码，以使用 API 关闭浏览器函数键。
*  添加了 [UpdateRuntime](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment3?view=webview2-1.0.865-prerelease&preserve-view=true#updateruntime) API，以轻松更新 WebView2 运行时。

#### <a name="bug-fixes"></a>Bug 修复

*  修复了 WebView2 中具有`POST`二进制数据的消息的处理程序`Chromium DevTools Protocol`。
*  关闭了 `OpenSaveAsAwareness` 下载 UI，因为它包含指向 `edge://settings`的链接。   ([问题 #1120](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1120)) 。
*  从屏幕共享对话框中删除了品牌。   ([问题 #940](https://github.com/MicrosoftEdge/WebViewFeedback/issues/940)) 。
*  修复了 [SetWindowDisplayAffinity](/windows/win32/api/winuser/nf-winuser-setwindowdisplayaffinity) 函数在 WebView2 应用中停止屏幕捕获时中断 WebView2 的 bug。   ([问题 #841](https://github.com/MicrosoftEdge/WebViewFeedback/issues/841)) 。
*  修复了在将任何笔输入发送到 WebView2 时鼠标输入停止工作的合成宿主的 bug。
*  修复了在任何笔输入后中断鼠标输入的 bug。  此更改特定于运行时。

### <a name="net"></a>.NET

#### <a name="experimental-features"></a>实验功能

*  向 WPF 工具箱添加了 WebView2 设计器工具。   ([问题 #210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  在 .NET 设计器模式下添加了 WebView2 UI 元素。

#### <a name="bug-fixes"></a>Bug 修复

*  通过将每个说明包装在更详细的 .NET 异常中，改进了 COM 异常说明。   ([问题 #338](https://github.com/MicrosoftEdge/WebViewFeedback/issues/338)) 。  此更改特定于运行时。
*  修复了在 Microsoft Visual Studio Tools for Office中选择`Tab`转移焦点导致 WebView2 控件崩溃时引发的 bug。   ([问题 #589](https://github.com/MicrosoftEdge/WebViewFeedback/issues/589) 和 [问题 #933](https://github.com/MicrosoftEdge/WebViewFeedback/issues/933)) 。  此更改特定于运行时。
*  改进了 .NET Framework 加载程序级别，以增强可靠性。   ([问题 #946](https://github.com/MicrosoftEdge/WebViewFeedback/issues/946)) 。
*  修复了在完成第一个导航之前尝试刷新时导致崩溃的 bug。   ([问题 #1011](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1011)) 。
*  修复了初始化，以便在 期间 `CoreWebView2InitializationCompleted`进行导航。   ([问题 #1050](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1050)) 。
*  改进了 .NET 浏览器进程崩溃错误处理。  现在可以在处理 `ProcessFailed` 事件后重新创建控件，而不会发生崩溃。   ([问题 #996](https://github.com/MicrosoftEdge/WebViewFeedback/issues/996)) 。


<!-- ====================================================================== -->
## <a name="1081841"></a>1.0.818.41

发布日期：2021 年 4 月 21 日

[用于 WebView2 SDK 1.0.818.41 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.818.41)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 90.0.818.41 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在为非呈现器子进程和帧呈现器引发。
*  添加了 `iframe` 对 的 `AddScriptToExecuteOnDocumentCreated`元素支持。
*  改进了 WebView2 代码，以更灵活地应对 `.exe` 格式不正确的版本信息的应用程序文件。   ([问题 #850](https://github.com/MicrosoftEdge/WebViewFeedback/issues/850)) 。
*  从 WebView2 浏览器进程命令行中删除 `--winhttp-proxy-resolver` ，并打开 WebView2 的其他代理命令行选项。


<!-- ====================================================================== -->
## <a name="10824-prerelease"></a>1.0.824-prerelease

发布日期：2021 年 3 月 8 日

[用于 WebView2 SDK 1.0.824-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.824-prerelease)

为了完全实现 API 兼容性，此预发布版本的 WebView2 SDK 需要 Microsoft Edge 版本 91.0.824.0 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  扩展了 `ProcessFailed` 事件。  它现在为非呈现器子进程和帧呈现器引发。
*  添加了实验 [性 AreBrowserAcceleratorKeysEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings2?view=webview2-1.0.824&preserve-view=true#get_arebrowseracceleratorkeysenabled) 设置。  可以阻止浏览器响应与导航、打印、保存和其他特定于浏览器的功能相关的键盘快捷方式。
*  添加了 `iframe` 对 的 `AddScriptToExecuteOnDocumentCreated`元素支持。

#### <a name="promotion"></a>推广

*  [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) API 现在已提升为稳定。
*  光栅化缩放 API ([RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性、  [RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件、 [BoundsMode 属性](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode)和 [ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性) 现已提升为 Stable。

#### <a name="bug-fixes"></a>Bug 修复

*  扩展了支持的 C++ 和 .NET 项目类型，例如 MFC 和 ATL。   ([问题 #506](https://github.com/MicrosoftEdge/WebViewFeedback/issues/506)、 [问题 #669](https://github.com/MicrosoftEdge/WebViewFeedback/issues/669) 和 [问题 #851](https://github.com/MicrosoftEdge/WebViewFeedback/issues/851)) 。
*  修复了 Evergreen WebView2 运行时泄漏入站防火墙条目的 bug。
*  修复了事件期间 `WebResourceRequested` 响应的设置。   ([问题 #568](https://github.com/MicrosoftEdge/WebViewFeedback/issues/568)) 。
*  修复了导航到 导致 `edge://` 浏览器进程退出的 bug。   ([问题 #604](https://github.com/MicrosoftEdge/WebViewFeedback/issues/604)) 。
*  修复了在可视化托管模式下将 WebView2 限制为屏幕大小的 bug。


<!-- ====================================================================== -->
## <a name="1077444"></a>1.0.774.44

发布日期：2021 年 3 月 8 日

[用于 WebView2 SDK 1.0.774.44 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.774.44)

为了完全实现 API 兼容性，此版本的 WebView2 SDK 需要 WebView2 运行时版本 89.0.774.44 或更高版本。

### <a name="general"></a>概要

#### <a name="features"></a>功能

*  在 WebView2 中关闭了各种 Microsoft Edge 浏览器服务。
*  视觉对象托管 API 现已正式发布。

#### <a name="promotions"></a>促销

*  以下实验性 API 现在已提升为稳定 API。
   *  [DPI 支持](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived) 相关 API
   *  视觉对象托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)
   *  [TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend)
   *  [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor)

#### <a name="bug-fixes"></a>Bug 修复

*  修复了在可视化托管模式下将 WebView2 限制为屏幕大小的 bug。


<!-- ====================================================================== -->
## <a name="10790-prerelease"></a>1.0.790-prerelease

发布日期：2021 年 2 月 10 日

[用于 WebView2 SDK 1.0.790-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.790-prerelease)

此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **中断性变更**：已弃用 WebView2 预发行版包 1.0.781。  停止使用包 1.0.781 进行开发。

> [!IMPORTANT]
> WebView2 预发行版包 0.9.430 已弃用，并随下一个版本一起删除。  如果 WebView2 应用使用该包，WebView2 团队建议你移动到较新的包。

#### <a name="features"></a>功能

*  添加了 [TrySuspend 和 Resume](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#trysuspend) 方法以暂停和恢复 WebViews。
*  添加了 [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping) 方法，该方法将虚拟主机名映射到目录路径。   ([问题 #37](https://github.com/MicrosoftEdge/WebViewFeedback/issues/37)、 [问题 #161](https://github.com/MicrosoftEdge/WebViewFeedback/issues/161) 和 [问题 #212](https://github.com/MicrosoftEdge/WebViewFeedback/issues/212)) 。
*  添加了 [DefaultBackgroundColor](/microsoft-edge/webview2/reference/win32/icorewebview2controller2?view=webview2-1.0.790-prerelease&preserve-view=true#get_defaultbackgroundcolor) 属性，用于设置背景的颜色和 alpha 通道。   ([问题 #414](https://github.com/MicrosoftEdge/WebViewFeedback/issues/414)) 。
*  添加了 [UserAgent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalsettings?view=webview2-1.0.790-prerelease&preserve-view=true#get_useragent) 属性来获取或设置用户代理。   ([问题 #122](https://github.com/MicrosoftEdge/WebViewFeedback/issues/122)) 。
*  已将 `CreateCookieWithCookie` 方法替换为 `CopyCookie` 方法。
*  添加了使用 [ICoreWebView2CompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller?view=webview2-1.0.790-prerelease&preserve-view=true) 接口的可视化托管支持，该接口使用 中的`ICoreWebView2Environment3`新`CreateCoreWebView2CompositionController`方法创建。

#### <a name="bug-fixes"></a>Bug 修复

*  已关闭 WebView2 中的 Microsoft Edge 购物功能。
*  在 为 时`AreDefaultContextMenusEnabled``false`关闭了 PDF 查看器中的上下文菜单。   ([问题 #605](https://github.com/MicrosoftEdge/WebViewFeedback/issues/605)) 。
*  修复了 `E_NOINTERFACE` 查询 `ICoreWebView2` 时返回的 `ICoreWebView2Experimental`bug。   ([问题 #691](https://github.com/MicrosoftEdge/WebViewFeedback/issues/691)) 。
*  修复了当 设置为 `false`时`CoreWebView2NavigationStartingEventArgs.Cancel`允许使用格式不正确的 URI 进行导航的 bug。   ([问题 #400](https://github.com/MicrosoftEdge/WebViewFeedback/issues/400)) 。
*  修复了在弹出窗口上阻止的 `window.print()` bug，该窗口的事件处理程序附加到 `NewWindowRequested` 事件。   ([问题 #409](https://github.com/MicrosoftEdge/WebViewFeedback/issues/409)) 。
*  修复了在不同监视器之间移动应用时的动态 DPI 问题。   ([问题 #58](https://github.com/MicrosoftEdge/WebViewFeedback/issues/58)) 
*  `HRESULT`改进了 [ICoreWebView2WebResourceResponseViewGetContentCompletedHandler：：Invoke](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponseviewgetcontentcompletedhandler?view=webview2-1.0.790-prerelease&preserve-view=true#invoke) 传递的实例。
*  已关闭自动填充管理按钮。   ([问题 #585](https://github.com/MicrosoftEdge/WebViewFeedback/issues/585)) 。
*  修复了在多个窗口中托管时运行时 `WebView2.Dispose` Visual Studio 崩溃的问题。   ([问题 #816](https://github.com/MicrosoftEdge/WebViewFeedback/issues/816)) 和 [问题 #442](https://github.com/MicrosoftEdge/WebViewFeedback/issues/442)) 。
*  修复了在 Visual Studio 工具箱中显示 WebView2 控件的 bug。   ([问题 #210](https://github.com/MicrosoftEdge/WebViewFeedback/issues/210)) 。
*  减少了 CPU 使用率过高的问题。   ([问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。
*  修复了已弃用的 1.0.781-prerelease 包的问题。   ([问题 #875](https://github.com/MicrosoftEdge/WebViewFeedback/issues/875) 和 [问题 #878](https://github.com/MicrosoftEdge/WebViewFeedback/issues/878)) 。

#### <a name="promotions"></a>促销

*  以下实验性 API 现在已提升为稳定：
   *  视觉对象托管 API
   *  [SetVirtualHostNameToFolderMapping](/microsoft-edge/webview2/reference/win32/icorewebview2_3?view=webview2-1.0.790-prerelease&preserve-view=true#setvirtualhostnametofoldermapping)

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  修复了使用 WPF SDK 的 WebView2 应用崩溃的 bug。  选择 `F4` 关闭窗口时发生崩溃。   ([问题 #399](https://github.com/MicrosoftEdge/WebViewFeedback/issues/399)) 。
*  WebView2 初始化屏幕现在是透明的，而不是灰色的。   ([问题 #196](https://github.com/MicrosoftEdge/WebViewFeedback/issues/196)) 。


<!-- ====================================================================== -->
## <a name="1070550"></a>1.0.705.50

发布日期：2021 年 1 月 25 日

[用于 WebView2 SDK 1.0.705.50 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.705.50)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

#### <a name="promotions"></a>促销

*  以下实验性 API 现在已提升为稳定：
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)


<!-- ====================================================================== -->
## <a name="10721-prerelease"></a>1.0.721-prerelease

发布日期：2020 年 12 月 8 日

[用于 WebView2 SDK 1.0.721-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.721-prerelease)

此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **中断性变更**：WebView2 预发布包 1.0.707 和包 0.9.628 已弃用。  停止使用包 1.0.707 和包 0.9.628 进行开发。

#### <a name="features"></a>功能

*  添加了 [WebView2 组策略](/deployedge/microsoft-edge-webview-policies)。  有关最佳做法，请参阅 [WebView2 的组策略](concepts/enterprise.md#group-policies-for-webview2)。
*  > [!IMPORTANT]
   > **中断性变更**：已弃用旧的注册表位置。
   >
   > ```text
   > {Root}\Software\Policies\Microsoft\EmbeddedBrowserWebView\LoaderOverride\{AppId}
   > ```

*  添加了对 WebView2 中的 [拖放](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller3?view=webview2-1.0.721-prerelease&preserve-view=true) 支持。
*  添加了用于处理 DPI 支持的 API。
   *  添加了 [RasterizationScale](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_rasterizationscale) 属性以更改 WebView2 内容和 UI 弹出窗口的 DPI 比例，以及关联的 [RasterizationScaleChanged](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#add_rasterizationscalechanged) 事件。
   *  添加了 [ShouldDetectMonitorScaleChanges](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_shoulddetectmonitorscalechanges) 属性，以便根据需要自动更新 `RasterizationScale` 属性。
   *  添加了 [BoundsMode 属性](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontroller?view=webview2-1.0.721-prerelease&preserve-view=true#get_boundsmode) ，以指定边界是逻辑像素并允许 WebView2 用于 `RasterizationScale` WebView2 像素显示，WebView2 将 `RasterizationScale` 与 一起使用 `Bounds` 以获取物理大小。
*  更新了`NewWindowRequested`要处理 `Ctrl``click`+和 `Shift`+`click`的事件。   ([问题 #168](https://github.com/MicrosoftEdge/WebViewFeedback/issues/168) 和 [问题 #371](https://github.com/MicrosoftEdge/WebViewFeedback/issues/371)) 。
*  以下实验性 API 现在已提升为稳定 API。
   *  [WebResourceResponseReceived API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_webresourceresponsereceived)
   *  [NavigateWithWebResourceRequest API](/microsoft-edge/webview2/reference/win32/icorewebview2environment2?view=webview2-1.0.721-prerelease&preserve-view=true#createwebresourcerequest)
   *  [Cookie 管理 API](/microsoft-edge/webview2/reference/win32/icorewebview2cookiemanager?view=webview2-1.0.721-prerelease&preserve-view=true)
   *  [DOMContentLoaded API](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#add_domcontentloaded)
   *  [Environment 属性](/microsoft-edge/webview2/reference/win32/icorewebview2_2?view=webview2-1.0.721-prerelease&preserve-view=true#get_environment)

### <a name="net"></a>.NET

#### <a name="features"></a>功能

*  在 .NET Core 3.1+ 和 .NET 5 中打开 WinForms 设计器。
*  改进了 .NET Cookie 管理。   ([问题 #611](https://github.com/MicrosoftEdge/WebViewFeedback/issues/611)) 。
*  已替换为 `CoreWebView2Ready` [CoreWebView2InitializationCompleted](/dotnet/api/microsoft.web.webview2.core.corewebview2initializationcompletedeventargs)。

#### <a name="bug-fixes"></a>Bug 修复

*  添加了 [AcceleratorKeyPressed](/dotnet/api/microsoft.web.webview2.wpf.webview2.acceleratorkeypressed) 事件以支持 `AcceleratorKey` 在 WebView2 中选择。   ([问题 #288](https://github.com/MicrosoftEdge/WebViewFeedback/issues/288)) 。
*  删除了将不必要的文件输出到 WebView2 文件夹。   ([问题 #461](https://github.com/MicrosoftEdge/WebViewFeedback/issues/461)) 。
*  改进了主机对象 API。   ([问题 #335](https://github.com/MicrosoftEdge/WebViewFeedback/issues/335) 和 [问题 #525](https://github.com/MicrosoftEdge/WebViewFeedback/issues/525)) 。


<!-- ====================================================================== -->
## <a name="1066437"></a>1.0.664.37

发布日期：2020 年 11 月 20 日

[用于 WebView2 SDK 1.0.664.37 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.664.37)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：.NET WPF/WinForms WebView2 SDK 现已正式发布 (GA) 。  从此版本开始，发布 SDK 向前兼容。  有关详细信息，请参阅 [GA 公告博客文章](https://devblogs.microsoft.com/dotnet/announcing-general-availability-for-microsoft-edge-webview2-for-net-and-fixed-distribution-method)。

#### <a name="features"></a>功能

*  .NET WPF/WinForms WebView2 现已正式发布 (GA) 。
*  固定分发 (自带) 模式已进入正式版。

### <a name="net"></a>.NET

#### <a name="bug-fixes"></a>Bug 修复

*  `CoreWebView2NewWindowRequestedEventArgs.Handled` 防止打开新窗口。   ([问题 #549](https://github.com/MicrosoftEdge/WebViewFeedback/issues/549) 和 [问题 #560](https://github.com/MicrosoftEdge/WebViewFeedback/issues/560)) 。


<!-- ====================================================================== -->
## <a name="10674-prerelease"></a>1.0.674-prerelease

发布日期：2020 年 10 月 19 日

[用于 WebView2 SDK 1.0.674-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.674-prerelease)

此 WebView2 SDK 的预发行版需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  添加了 [NavigateWithWebResourceRequest](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#navigatewithwebresourcerequest) 方法，用于在导航期间提供发布数据或其他请求标头。
*  添加了在加载和分析初始 HTML 文档时运行的 [DOMContentLoaded](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_domcontentloaded) 事件。
*  在 WebView2 上添加了 [Environment](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_environment) 属性。  此属性公开创建 WebView2 实例的 WebView2 环境。
*  添加了允许开发人员对 WebView2 会话进行身份验证或从 WebView2 检索 Cookie 以对其他工具进行身份验证的 [Cookie 管理](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#get_cookiemanager) API。  WebView2 团队计划进行特定于语言或框架的改进。  请参阅 [API 评审：Cookie 管理](https://github.com/MicrosoftEdge/WebView2Announcement/issues/2)。
*  更新了 [WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-1.0.674-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件，并将不可变 [的 WebResourceResponseView](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true) 和 [WebResourceResponseReceivedEventArgs：:P opulateResponseContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponsereceivedeventargs?view=webview2-0.9.628-prerelease&preserve-view=true#populateresponsecontent) 添加到 [WebResourceResponseView：：GetContent](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwebresourceresponseview?view=webview2-1.0.674-prerelease&preserve-view=true#getcontent)。
*  在 WebView2 中[关闭Microsoft Defender 应用程序防护 (WDAG) ](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)。
*  为 Visual Hosting 添加了 [SystemCursorId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller2?view=webview2-1.0.674-prerelease&preserve-view=true#get_systemcursorid) 。
*  添加了针对 Visual Hosting 中的输入法修复的 bug。
*  删除了在使用 WebView2 静态库时对 `version.lib` 的要求。

### <a name="net"></a>.NET

*  更新了 [CoreWebView2](/dotnet/api/microsoft.web.webview2.core.corewebview2) 类以公开 `CoreWebView2Environment` 变量。
*  将命名空间中 `Microsoft.Web.WebView2.Core` 自定义 EventArgs 类的实现更改为 [System.EventArgs](/dotnet/api/system.eventargs) 或 [System.ComponentModel.CancelEventArgs](/dotnet/api/system.componentmodel.canceleventargs) 的子类。   ([问题 #250](https://github.com/MicrosoftEdge/WebViewFeedback/issues/250)) 
*  在 WinForms 中添加了对 [CoreWebView2CreationProperties](/dotnet/api/microsoft.web.webview2.winforms) 的支持。   ([问题 #204](https://github.com/MicrosoftEdge/WebViewFeedback/issues/204)) 。
*  添加了 [WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) .NET API。   ([问题 #219](https://github.com/MicrosoftEdge/WebViewFeedback/issues/219)) 。
*  已将 WinForms Designer [Source](/dotnet/api/microsoft.web.webview2.winforms.webview2.source) 属性更新为默认值或重置为 null。   ([问题 #177](https://github.com/MicrosoftEdge/WebViewFeedback/issues/177)) 。
*  更新了 WebView2.Init () 中的 WebView2 边界，以支持小于 100% 的 DPI 模式。   ([问题 #432](https://github.com/MicrosoftEdge/WebViewFeedback/issues/432)) 。
*  更新了 [BuildWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.buildwindowcore) 和 [DestroyWindowCore](/dotnet/api/microsoft.web.webview2.wpf.webview2.destroywindowcore) 以提高可靠性。   ([问题 #382](https://github.com/MicrosoftEdge/WebViewFeedback/issues/382)) 。
*  更新了 .NET 加载程序基础，以在进程位而不是操作系统体系结构上进行加载。   ([问题 #431](https://github.com/MicrosoftEdge/WebViewFeedback/issues/431)) 。
*  已 `EdgeNotFoundException` 重命名为 [WebView2RuntimeNotFoundException](/dotnet/api/microsoft.web.webview2.core.webview2runtimenotfoundexception)。


<!-- ====================================================================== -->
## <a name="1062222"></a>1.0.622.22

发布日期：2020 年 10 月 19 日

[用于 WebView2 SDK 1.0.622.22 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.622.22)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

> [!IMPORTANT]
> **公告**：Win32 C/C++ WebView2 现已正式发布 (GA) 。  从此版本开始，发布 SDK 可向前兼容。  请参阅 [GA 公告博客文章](https://blogs.windows.com/msedgedev/edge-webview2-general-availability)。

*  Evergreen WebView2 运行时和安装程序已正式发布。  引导程序、引导程序下行链接和 Evergreen WebView2 运行时的独立安装程序在 [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) 上可用。  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)中还提供了安装工作流的示例代码。

有关运行时、Evergreen 分发和固定版本分发的详细信息，请参阅 [分发应用和 WebView2 运行时](concepts/distribution.md)。


<!-- ====================================================================== -->
## <a name="0962211"></a>0.9.622.11

发布日期：2020 年 9 月 10 日

[用于 WebView2 SDK 0.9.622.11 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.622.11)

此版本的 WebView2 SDK 需要 WebView2 运行时版本 86.0.616.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：此 SDK 是 WebView2 Win32 C/C++ GA 的候选版本。  正式版应使用相同的 API 接口和功能。

*  已断开连接 [的浏览器策略](/deployedge/microsoft-edge-policies)。
*  在 WebView2 环境选项上添加了 [AllowSingleSignOnUsingOSPrimaryAccount](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#get_allowsinglesignonusingosprimaryaccount) 属性，以启用 WebView2 的条件访问。
*  更新 `ICoreWebView2NewWindowRequestedEventArgs` 为包括 [WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.622&preserve-view=true#get_windowfeatures) 属性和关联的 [ICoreWebView2WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2windowfeatures?view=webview2-0.9.622&preserve-view=true)。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  更新 `System.Windows.Rect`  为使用 `System.Drawing.Rectangle` 而不是 `System.Windows.Rect` ([问题 #235](https://github.com/MicrosoftEdge/WebViewFeedback/issues/235)) 。
*  更新了 NewWindowRequested 事件以处理 `window.open()` 不带参数的请求。   ([问题 #293](https://github.com/MicrosoftEdge/WebViewFeedback/issues/293)) 。
*  使用 `ICoreWebView2EnvironmentOptions` 指定的 [AdditionalBrowserArguments](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.622&preserve-view=true#put_additionalbrowserarguments) 不会用环境变量或注册表值替代。  请参阅 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.622&preserve-view=true#createcorewebview2environmentwithoptions)。


<!-- ====================================================================== -->
## <a name="09579"></a>0.9.579

发布日期：2020 年 7 月 20 日

[用于 WebView2 SDK 0.9.579 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.579)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 86.0.579.0 或更高版本。

### <a name="general"></a>概要

*  > [!IMPORTANT]
   > **公告**：Evergreen WebView2 运行时和安装程序已发布预览版。  请参阅 [分发应用和 WebView2 运行时](concepts/distribution.md)。

*  > [!IMPORTANT]
   > **公告**：下一个 SDK 版本发布后，不再支持以下 WebView2 SDK 版本：
   >
   > *  [0.8.190](#08190)
   > *  [0.8.230](#08230)
   > *  [0.8.270](#08270)
   > *  [0.8.314](#08314)
   > *  [0.8.355](#08355)
   >
   > WebView2 SDK 版本在 nuget.org 上也标记为已弃用。 WebView2 建议随时了解最新版本的 WebView2。

*  添加了 WebView2 工作线程改进。   ([问题 #318](https://github.com/MicrosoftEdge/WebViewFeedback/issues/318)) 。
*  已关闭 WebView2 中的弹出窗口阻止程序。  请参阅 事件中的 `NewWindowRequested` [IsUserInitiated](/microsoft-edge/webview2/reference/win32/icorewebview2newwindowrequestedeventargs?view=webview2-0.9.538&preserve-view=true#get_isuserinitiated) 属性。
*  确保为 `about:blank`运行 WebView2 导航启动事件。  现在，`NavigationStarting`所有导航都运行事件，但不支持和忽略 元素的 `iframe` 或 `srcdoc` 取消`about:blank`。
*  阻止了 WebView2 中的某些 `edge://` URI 方案。
*  在 WebView2 环境选项上添加了试验性 [IsSingleSignOnUsingOSPrimaryAccountEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironmentoptions?view=webview2-0.9.538-prerelease&preserve-view=true#get_issinglesignonusingosprimaryaccountenabled) 属性，以启用 WebView2 的条件访问。
*  添加了试验 [性 WebResourceResponseReceived](/microsoft-edge/webview2/reference/win32/icorewebview2experimental?view=webview2-0.9.538-prerelease&preserve-view=true#add_webresourceresponsereceived) 事件，该事件在 WebView2 接收并处理来自 WebResource 请求的响应后运行。  身份验证标头（如果有）包含在响应对象中。

### <a name="net"></a>.NET

*  改进了 WPF 焦点处理。   ([问题 #185](https://github.com/MicrosoftEdge/WebViewFeedback/issues/185)) 。
*  在 WPF Webview2 控制器上添加了 `ZoomFactor` 属性。


<!-- ====================================================================== -->
## <a name="09538"></a>0.9.538

[用于 WebView2 SDK 0.9.538 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.538)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 85.0.538.0 或更高版本。

### <a name="general"></a>概要

*  放弃对 WebView2 SDK 版本 [0.8.149 的支持](#08149)。  WebView2 建议随时了解最新版本的 WebView2。
*  更新了组策略，以考虑何时修改 Microsoft Edge 浏览器的配置文件路径 ([#179](https://github.com/MicrosoftEdge/WebViewFeedback/issues/179)) 。

### <a name="win32-cc"></a>Win32 C/C++

*  添加了 [ICoreWebView2ExperimentalNewWindowRequestedEventArgs：：get_WindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalnewwindowrequestedeventargs?view=webview2-0.9.538-prerelease&preserve-view=true#get_windowfeatures)，它运行并与 [ICoreWebView2ExperimentalWindowFeatures](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalwindowfeatures?view=webview2-0.9.538-prerelease&preserve-view=true) ([#70](https://github.com/MicrosoftEdge/WebViewFeedback/issues/70)) 关联时`window.open()`触发。
*  > [!IMPORTANT]
   > **中断性变更**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) ，并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.538&preserve-view=true#createcorewebview2environmentwithoptions)。

*  > [!IMPORTANT]
   > **中断性变更**：为确保 WebView2 API 符合 Windows API 命名约定，WebView2 团队更新了以下名称。
   >
   > *  [AreRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_areremoteobjectsallowed) 现在是 [AreHostObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.538&preserve-view=true#get_arehostobjectsallowed)。

*  更新了 [AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.538&preserve-view=true#addhostobjecttoscript)。  原始主机对象序列化程序标记现在设置为代理对象。  然后，在 JavaScript 回调 ([#148) ](https://github.com/MicrosoftEdge/WebViewFeedback/issues/148) 中作为参数传递时，主机对象序列化程序标记作为主机对象重新序列化。

### <a name="net-09538-prerelease"></a>.NET (0.9.538 预发行版) 

*  已发布 WinForms 和 WPF WebView2API 示例，它们是 WebView2 SDK 的综合指南。  请参阅 [示例存储库](https://github.com/MicrosoftEdge/WebView2Samples)。
*  添加了对视觉对象托管和窗口功能 [实验 API 的支持](concepts/versioning.md#experimental-apis)。
*  > [!IMPORTANT]
   > **中断性变更**：以下延迟现在实现 IDisposable：  [ScriptDialogOpening](/dotnet/api/microsoft.web.webview2.core.corewebview2.scriptdialogopening)、 [NewWindowRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.newwindowrequested)、 [WebResourceRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested) 和 [PermissionRequested](/dotnet/api/microsoft.web.webview2.core.corewebview2.permissionrequested)。

*  添加了 [GetAvailableBrowserVersionString](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.getavailablebrowserversionstring) 和 [CompareBrowserVersions](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.comparebrowserversions) 作为 [CoreWebView2Environment](/dotnet/api/microsoft.web.webview2.core.corewebview2environment) 静态。


<!-- ====================================================================== -->
## <a name="09515-prerelease"></a>0.9.515-prerelease

[用于 WebView2 SDK 0.9.515-prerelease 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.515-prerelease)

此 WebView2 SDK 的预发行版需要 Microsoft Edge 版本 84.0.515.0 或更高版本。

*  > [!IMPORTANT]
   > **公告**：WebView2 现在支持**预发行版包**中.NET Framework 4.6.2 或更高版本和 .NET Core 3.0 或更高版本上的Windows 窗体和 WPF。

*  有关生成 WPF 应用的详细信息，请参阅 WPF [应用中的 WebView2 入门](get-started/wpf.md) 和 WPF 特定 API 的 WebView2 WPF [参考](/dotnet/api/microsoft.web.webview2.wpf) 。
*  有关生成Windows 窗体应用的详细信息，请参阅 [WinForms 应用中的 WebView2 入门](get-started/winforms.md)和用于Windows 窗体特定 API 的 WebView2 [Windows 窗体参考](/dotnet/api/microsoft.web.webview2.winforms)。
*  有关 CoreWebView2 API 的详细信息，请参阅 [.NET 参考](/dotnet/api/microsoft.web.webview2.core)。
*  > [!CAUTION]
   > **已知问题**：WebView2 团队知道预发行版中的一些问题正在将来的版本中解决。
   >
   > *  **DPI 感知**：WPF 的 WebView2 当前不是 DPI 感知。  在高 DPI 监视器上初始化 WebView2 时，存在一个已知问题，即 WebView2 控件首先初始化为窗口的一小部分，直到调整窗口大小。
   > *  **WPF 设计器**：目前不支持 WPF 设计器。  通过在文本编辑器中直接修改相应的 XAML，在应用中添加 WebView2 控件。


<!-- ====================================================================== -->
## <a name="09488"></a>0.9.488

[用于 WebView2 SDK 0.9.488 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.488)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 84.0.488.0 或更高版本。

*  > [!IMPORTANT]
   > **公告**：从即将推出的 Microsoft Edge 版本 83 开始，Evergreen WebView2 不再面向稳定浏览器通道。  相反，它面向另一组二进制文件（品牌为 Evergreen WebView2 Runtime），你可以通过 WebView2 团队当前正在开发的安装程序进行链式安装。  请参阅 [分发应用和 WebView2 运行时](concepts/distribution.md)。

*  > [!IMPORTANT]
   > **公告**：今后，WebView2 团队将发布两个包：一个包含实验性 API 的预发行版包 (供你试用) ，一个具有稳定 API 的稳定发布包 (，) 信心十足。  若要了解差异，请参阅 [了解浏览器版本和 WebView2](concepts/versioning.md)。

*  > [!IMPORTANT]
   > **中断性变更**：为确保 WebView2 API 符合 Windows API 命名约定，WebView2 团队更新了以下接口的名称。
   >
   > *  `CORE_WEBVIEW2_*` 前缀现在 `COREWEBVIEW2_*`为 。
   > *  [GetCoreWebView2BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.430&preserve-view=true#getcorewebview2browserversioninfo) 现在是 [GetAvailableCoreWebView2BrowserVersionString](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#getavailablecorewebview2browserversionstring)。
   > *  [get_BrowserVersionInfo](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.430&preserve-view=true#get_browserversioninfo) 现已 [get_BrowserVersionString](/microsoft-edge/webview2/reference/win32/icorewebview2environment?view=webview2-0.9.488&preserve-view=true#get_browserversionstring)。
   > *  [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 现在是 [AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#addhostobjecttoscript)。
   > *  [RemoveRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#removeremoteobject) 现在是 [RemoveHostObjectFromScript](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#removehostobjectfromscript)。
   > *  `chrome.webview.remoteObjects` 现在 `chrome.webview.hostObjects`为 。

*  > [!IMPORTANT]
   > **中断性变更**： `AddRemoteObject` JS 代理方法也会重命名。
   >
   > *  `getLocal` 现在 `getLocalProperty`为 。
   > *  `setLocal` 现在 `setLocalProperty`为 。
   > *  `getRemote` 现在 `getHostProperty`为 。
   > *  `setRemote` 现在 `setHostProperty`为 。
   > *  `applyRemote` 现在 `applyHostFunction`为 。

*  > [!IMPORTANT]
   > **中断性变更**：已弃用 [CreateCoreWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithdetails) ，并替换为 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.9.488&preserve-view=true#createcorewebview2environmentwithoptions)。

*  添加了 [FrameNavigationCompleted](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_framenavigationcompleted) 事件。  现在，当元素 `iframe` 完成导航时，将运行事件并返回导航的成功和导航 ID。
*  添加了 [ICoreWebView2EnvironmentOptions](/microsoft-edge/webview2/reference/win32/icorewebview2environmentoptions?view=webview2-0.9.488&preserve-view=true) 接口，可用于确定应用面向的 Evergreen WebView2 运行时的版本。
*  添加了 [IsBuiltInErrorPageEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.488&preserve-view=true#get_isbuiltinerrorpageenabled) 设置。  现在，你可以选择打开或关闭内置的错误网页，以导致导航失败和呈现进程失败。
*  更新了远程对象注入以支持 .NET `IDispatch` 实现 ([#113](https://github.com/MicrosoftEdge/WebViewFeedback/issues/113)) 。
*  更新 [了 NewWindowRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.488&preserve-view=true#add_newwindowrequested) 事件以处理来自上下文菜单的请求 ([#108](https://github.com/MicrosoftEdge/WebViewFeedback/issues/108)) 。
*  发布了第一个单独的 WebView2 预发行版包，可在其中访问可视托管 API。  WebView2 团队更新了 [APISample](https://github.com/MicrosoftEdge/WebView2Samples) 以包含新的实验 API。
   *  添加了 [ICoreWebView2ExperimentalCompositionController](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller?view=webview2-0.9.488-prerelease&preserve-view=true) 接口，用于连接到合成树并为 WebView2 控件提供输入。
   *  添加了 [ICoreWebView2ExperimentalPointerInfo](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalpointerinfo?view=webview2-0.9.488-prerelease&preserve-view=true)，其中包含来自 `POINTER_INFO`的所有信息。  此对象传递给 SendPointerInput，以将指针输入注入 WebView2。
   *  添加了 [ICoreWebView2ExperimentalCursorChangedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcursorchangedeventhandler?view=webview2-0.9.488-prerelease&preserve-view=true)，它告知应用何时应更改 WebView2 控件上的鼠标光标。  当鼠标悬停在 WebView2 中的文本框上时，光标将从箭头更改为选择器。  上的 `cursor` `CompositionController` 属性指示应用当前应为 WebView2 的鼠标光标。


<!-- ====================================================================== -->
## <a name="09430"></a>0.9.430

[用于 WebView2 SDK 0.9.430 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.9.430)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 82.0.430.0 或更高版本。

WebView2 SDK 是官方的 Win32 C++ Beta 版本，其中包含来自反馈的多个功能请求。  WebView2 团队尝试使用中断性变更来限制发布的数量。  随着正式版的临近，Beta 版中将合并了一些重大中断性变更。

*  > [!IMPORTANT]
   > **中断性变更**：随着最终版本的临近，WebView2 团队将前缀`IWebView2WebView``ICoreWebView2`重命名为，以确保 WebView2 API 符合 Windows API 命名约定。  此外，为了从 UI 框架利用 WebView2 SDK，WebView2 团队分为 `ICoreWebView2` [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true) 和 [ICoreWebView2Host](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true)。  `ICoreWebView2Host` 支持调整大小、显示和隐藏、聚焦以及与开窗和合成相关的其他功能。  ICoreWebView2 支持所有其他 WebView2 功能。  若要了解有关合并更改的详细信息，请参阅 WebView2 [APISample](https://github.com/MicrosoftEdge/WebView2Samples) 项目中的 WebView2 [拉取请求](https://github.com/MicrosoftEdge/WebView2Samples/pull/17)。

*  > [!IMPORTANT]
   > **中断性变更**：将 [DocumentStateChanged](/microsoft-edge/webview2/reference/win32/iwebview2webview?view=webview2-0.8.355&preserve-view=true#add_documentstatechanged) 拆分为三个组件：  [SourceChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_sourcechanged)、 [ContentLoading](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_contentloading) 和 [HistoryChanged](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_historychanged)。  现在，当源 URL 更改时， `SourceChanged` 将运行事件。  更改历史记录状态时，将 `HistoryChanged` 运行事件。  加载新文档时，事件 `ContentLoading` 在初始脚本之前运行。

*  添加了对 ARM64 体系结构的支持。
*  添加了对触摸屏设备的软输入面板 (SIP) 支持。
*  添加了对 Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 和 Windows Server 2016 的支持。
*  为状态栏添加了 [NotifyParentWindowPositionChanged](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#notifyparentwindowpositionchanged) ，以在窗口模式中跟随窗口。  此外，在无窗口模式下实现更改，以便辅助功能正常工作。
*  添加了 [AreRemoteObjectsAllowed](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_areremoteobjectsallowed) 设置，以全局控制网页是否可以由任何远程对象访问。  默认情况下， `AreRemoteObjectsAllowed` 处于打开状态，因此可从网页访问 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#addremoteobject) 添加的远程对象。  关闭 后 `AreRemoteObjectsAllowed` ，无法从网页访问对象。  更改将应用于下一个导航事件。
*  添加了 [IsZoomControlEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings?view=webview2-0.9.430&preserve-view=true#get_iszoomcontrolenabled) 设置，以防止用户使用 和+`-` `ctrl` (或 `ctrl`+ 鼠标滚轮) 影响 WebView2 控件`ctrl`+`+`的缩放。  关闭设置时，仍可使用 [put_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#put_zoomfactor) 来设置缩放。
*  已将 ZoomFactor 更改为仅适用于当前 WebView2 控件。  对当前 WebView2 控件的缩放更改不会影响使用同一原点网站导航到的其他 WebView。  请参阅 [get_ZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#get_zoomfactor)。
*  Hid ZoomView UI for WebView2 控件 ([#95](https://github.com/MicrosoftEdge/WebViewFeedback/issues/95)) 。
*  添加了 [SetBoundsAndZoomFactor](/microsoft-edge/webview2/reference/win32/icorewebview2host?view=webview2-0.9.430&preserve-view=true#setboundsandzoomfactor)。  现在，可以同时设置 WebView2 控件的缩放因子和边界。
*  添加了 [WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) 事件。  请参阅 [add_WindowCloseRequested](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#add_windowcloserequested) ([#119](https://github.com/MicrosoftEdge/WebViewFeedback/issues/119)) 。
*  添加了对 `beforeunload` JavaScript 对话框事件的对话框类型的支持，并添加了 [CORE_WEBVIEW2_SCRIPT_DIALOG_KIND_BEFOREUNLOAD](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-0.9.430&preserve-view=true#core_webview2_script_dialog_kind) 枚举项。
*  向 HttpRequestHeaders 添加了 [GetHeaders](/microsoft-edge/webview2/reference/win32/icorewebview2httprequestheaders?view=webview2-0.9.430&preserve-view=true#getheaders) ，向 HttpResponseHeaders 添加了 [GetHeader](/microsoft-edge/webview2/reference/win32/icorewebview2httpresponseheaders?view=webview2-0.9.430&preserve-view=true#getheader) ，并向 HttpHeadersCollectionIterator [添加了 get_HasCurrentHeader](/microsoft-edge/webview2/reference/win32/icorewebview2httpheaderscollectioniterator?view=webview2-0.9.430&preserve-view=true#get_hascurrentheader) 属性。
*  > [!IMPORTANT]
   > **中断性变更**：修改 `DevToolsProtocolEventReceived` 的行为。  现在，可以为特定的 [DevTools 协议事件创建 DevToolsProtocolEventReceiver](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true)，并使用 [add_DevToolsProtocolEventReceived remove_DevToolsProtocolEventReceived](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#add_devtoolsprotocoleventreceived)/ 订阅/取消订阅此类事件。[](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-0.9.430&preserve-view=true#remove_devtoolsprotocoleventreceived)

*  > [!IMPORTANT]
   > **中断性变更**：将 [get_WebMessageAsString](/microsoft-edge/webview2/reference/win32/iwebview2webmessagereceivedeventargs?view=webview2-0.8.355&preserve-view=true#get_webmessageasstring) 属性更改为 `WebMessageReceivedEventArgs` [TryGetWebMessageAsString](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventargs?view=webview2-0.9.430&preserve-view=true#trygetwebmessageasstring) 方法。

*  > [!IMPORTANT]
   > **中断性变更**：将 [Handle](/microsoft-edge/webview2/reference/win32/iwebview2acceleratorkeypressedeventargs?view=webview2-0.8.355&preserve-view=true#handle) 方法更改为`AcceleratorKeyPressedEventArgs`[get_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2acceleratorkeypressedeventargs?view=webview2-0.9.430&preserve-view=true#get_handled)属性。


<!-- ====================================================================== -->
## <a name="08355"></a>0.8.355

[用于 WebView2 SDK 0.8.355 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.355)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 80.0.355.0 或更高版本。

*  已发布 WebView2API 示例，这是 WebView2 SDK 的综合指南。  请参阅 [API 示例](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample)。
*  添加了对除英语 ([#30](https://github.com/MicrosoftEdge/WebViewFeedback/issues/30)) 以外的所有语言的 IME 支持。
*  更新了事件的 API 图面， `WebResourceRequested` 以响应 bug 报告。  现在已弃用在创建时同时指定筛选器和事件。  若要创建请求的 Web 资源事件，请使用 [add_WebResourceRequested](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#add_webresourcerequested) 添加事件，使用 [AddWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#addwebresourcerequestedfilter) 添加筛选器。  [RemoveWebResourceRequestedFilter](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#removewebresourcerequestedfilter) 删除筛选器 ([#36](https://github.com/MicrosoftEdge/WebViewFeedback/issues/36))  ([#74](https://github.com/MicrosoftEdge/WebViewFeedback/issues/74)) 。
*  > [!IMPORTANT]
   > **中断性变更**：修改的全屏行为。  已弃用 [的 IsFullScreenAllowed](/microsoft-edge/webview2/reference/win32/iwebview2settings?view=webview2-0.8.355&preserve-view=true#get_isfullscreenallowed_deprecated)。  现在，默认情况下，如果 WebView2 控件中的元素 (（如视频) ）设置为全屏，则会填充 WebView2 控件的边界。  使用 [ContainsFullScreenElementChanged](/microsoft-edge/webview2/reference/win32/iwebview2containsfullscreenelementchangedeventhandler?view=webview2-0.8.355&preserve-view=true) 事件和 [get_ContainsFullScreenElement](/microsoft-edge/webview2/reference/win32/iwebview2webview5?view=webview2-0.8.355&preserve-view=true#get_containsfullscreenelement) 指定如果元素想要进入全屏模式，应用应如何调整 WebView2 控件的大小。


<!-- ====================================================================== -->
## <a name="08314"></a>0.8.314

[用于 WebView2 SDK 0.8.314 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.314)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 80.0.314.0 或更高版本。

### <a name="changes"></a>更改

*  添加了对 Windows 7、Windows 8和Windows 8.1的支持。
*  添加了对 WebView2 的 Visual Studio 和Visual Studio Code调试支持。  现在，直接从 IDE 在 WebView2 中调试脚本。  请参阅 [如何使用 WebView2 控件进行开发时进行调试](how-to/debug.md)。
*  为 WebView2 中的运行脚本添加了 `Native Object Injection` ，以便从应用的 Win32 组件访问 IDispatch 对象并访问 IDispatch 对象的属性。  请参阅 [AddRemoteObject](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#addremoteobject) ([#17](https://github.com/MicrosoftEdge/WebViewFeedback/issues/17)) 。
*  添加了 `AcceleratorKeyPressed` 事件。  请参阅 [add_AcceleratorKeyPressed](/microsoft-edge/webview2/reference/win32/iwebview2webview4?view=webview2-0.8.355&preserve-view=true#add_acceleratorkeypressed) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  已关闭 `Context Menus`。  请参阅 [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/iwebview2settings2?view=webview2-0.8.355&preserve-view=true#put_aredefaultcontextmenusenabled) ([#57](https://github.com/MicrosoftEdge/WebViewFeedback/issues/57)) 。
*  更新了 `DPI Awareness`。  现在，WebView2 控件的 DPI 感知与主机应用的 DPI 感知相同。

   > [!NOTE]
   > 如果使用与原始 WebView2 控件实例不同的 DPI 感知启动另一个混合应用，则如果 `user data folder` 是相同的 ([#1](https://github.com/MicrosoftEdge/WebViewFeedback/issues/1)) ，则不会启动新的 WebView2 控件实例。

*  更新 `Notification Change Behavior` 后，WebView2 会自动拒绝 WebView2 控件中托管的 Web 内容提示的通知权限请求。


<!-- ====================================================================== -->
## <a name="08270"></a>0.8.270

[用于 WebView2 SDK 0.8.270 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.270)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 78.0.270.0 或更高版本。

### <a name="changes"></a>更改

*  添加了 `DocumentTitleChanged` 事件以指示文档标题更改 ([问题 #27](https://github.com/MicrosoftEdge/WebViewFeedback/issues/27)) 。

*  添加了 `GetWebView2BrowserVersionInfo` API ([问题 #18](https://github.com/MicrosoftEdge/WebViewFeedback/issues/18)) 。

*  添加了 `NewWindowRequested` 事件。

*  更新 `CreateWebView2EnvironmentWithDetails` 了函数以删除 `releaseChannelPreference`。  有关函数 `CreateWebView2EnvironmentWithDetails` 的详细信息，请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  仍支持注册表和环境变量替代。  除非重写，否则使用默认通道首选项。

   在通道搜索期间，WebView2 团队会跳过任何与 WebView2 SDK 不兼容的先前频道版本。

   WebView2 团队选择更稳定的通道，以确保最终用户的行为最一致。  使用最新的 Canary 内部版本进行测试时，应在启动应用之前创建一个脚本来 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE` 将环境变量 `1` 设置为 。  请参阅 [测试即将推出的 API 和功能](how-to/set-preview-channel.md)。

*  更新了函数， `CreateWebView2EnvironmentWithDetails` 其中包含用于在未指定时选择的 `userDataFolder` 逻辑。  有关函数 `CreateWebView2EnvironmentWithDetails` 的详细信息，请参阅 [CreateWebView2EnvironmentWithDetails](/microsoft-edge/webview2/reference/win32/webview2-idl?view=webview2-0.8.355&preserve-view=true#createwebview2environmentwithdetails)。  如果以前使用了默认 `userDataFolder` 位置，则切换到新 SDK 时，将重置默认值 `userDataFolder` (设置为主机代码目录中的新位置) 并且状态也会重置。  如果主机进程没有写入指定目录的权限，则 `CreateWebView2EnvironmentWithDetails` 函数可能会失败。  可以将数据从旧 `user data folder` 目录复制到新目录。


<!-- ====================================================================== -->
## <a name="08230"></a>0.8.230

[用于 WebView2 SDK 0.8.230 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.230)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 77.0.230.0 或更高版本。

### <a name="changes"></a>更改

*  添加了 `Stop` API 以停止所有导航和挂起的资源提取 ([问题 #28](https://github.com/MicrosoftEdge/WebViewFeedback/issues/28)) 。
*  向 NuGet 包添加了 `.tlb` 文件 ([问题 #22](https://github.com/MicrosoftEdge/WebViewFeedback/issues/22)) 。
*  向 NuGet 包中的安装程序列表添加了 .NET 项目 ([问题 #32](https://github.com/MicrosoftEdge/WebViewFeedback/issues/32)) 。


<!-- ====================================================================== -->
## <a name="08190"></a>0.8.190

[用于 WebView2 SDK 0.8.190 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.190)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 77.0.190.0 或更高版本。

*  添加了 `get_AreDevToolsEnabled`/`put_AreDevToolsEnabled` 以控制用户是否可以打开 DevTools ([问题 #16](https://github.com/MicrosoftEdge/WebViewFeedback/issues/16)) 。
*  添加了 `get_IsStatusBarEnabled`/`put_IsStatusBarEnabled` 以控制是否显示状态栏 ([问题 #19](https://github.com/MicrosoftEdge/WebViewFeedback/issues/19)) 。
*  添加了`get_CanGoBack``get_CanGoForward``GoForward`/`GoBack`//用于在导航历史记录中后退和前进。
*  添加了 HTTP 标头类型 (`IWebView2HttpHeadersCollectionIterator`//`IWebView2HttpRequestHeaders``IWebView2HttpRequestHeaders`) ，用于在 WebView2 中查看和修改 HTTP 标头。
*  在 64 位计算机上添加了 32 位 WebView2 支持 ([问题 #13](https://github.com/MicrosoftEdge/WebViewFeedback/issues/13)) 。
*  已将 WebView2 IDL 添加到 SDK ([问题 #14](https://github.com/MicrosoftEdge/WebViewFeedback/issues/14)) 。
*  添加了 lib 以支持 `IID\_\*` 接口 ID 对象 ([问题 #12](https://github.com/MicrosoftEdge/WebViewFeedback/issues/12)) 。
*  在 SDK 中向 NuGet `TARGET` 文件添加了包含路径、链接和自动复制 DLL 文件。
*  在脚本中启用请求 `window.open()` 。


<!-- ====================================================================== -->
## <a name="08149"></a>0.8.149

[用于 WebView2 SDK 0.8.149 的 NuGet 包](https://www.nuget.org/packages/Microsoft.Web.WebView2/0.8.149)

此版本的 WebView2 SDK 需要 Microsoft Edge 版本 76.0.149.0 或更高版本。

初始开发人员预览版。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [联系 Microsoft Edge WebView2 团队](contact.md)
