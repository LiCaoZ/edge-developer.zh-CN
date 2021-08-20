---
description: 了解 WebView2 接下来将做什么
title: WebView 2 Microsoft Edge路线图
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/07/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: c91c445d6c741f00180f3571f5098018051faf7f
ms.sourcegitcommit: 01ed086305c06b4e3a0436586524986700276148
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "11893903"
---
# <a name="microsoft-edge-webview2-roadmap"></a>Microsoft EdgeWebView2 路线图  

> [!NOTE]
> Last Updated： July 2021  

WebView2 控件允许开发人员在其本机应用程序中嵌入 Web 技术。  以下页面概述了 WebView2 的潜在路线图。  

> [!NOTE]
> WebView2 正在积极开发，路线图将继续根据市场变化和客户反馈不断发展，因此请注意，此处概述的计划并不详尽，可能会发生更改。  

如果你对路线图有疑问或疑问，请从反馈存储库 [提供反馈][GithubMicrosoftedgeWebviewfeedbackMain]。  

WebView2 团队正在计划以下主要工作，用于将来的更新。  

* UWP 预览版
* MacOS 预览版
* Xbox 预览版
* HoloLens预览

## <a name="webview2-runtime-and-installer"></a>WebView2 运行时和安装程序  

使用常青分发模式，你可以将 WebView2 运行时的目标或链安装到用户计算机上。  Evergreen WebView2 运行时和安装程序已到达通用版本 \(GA\) 。  有关详细信息，请导航到分发 [WebView2 应用和 WebView2 运行时][ConceptDistribution]。


## <a name="fixed-version"></a>固定版本  

固定版本分发模式允许你打包Microsoft Edge二进制文件 <!--(a specific version of the WebView2 Runtime)--> 在本机应用程序中。  固定版本已达到通用版本 \(GA\) 。  有关详细信息，请导航到分发 [WebView2 应用和 WebView2 运行时][ConceptDistribution]。


## <a name="general-availability"></a>通用  

### <a name="win32-cc"></a>Win32 C/C++  

Win32 C/C++ SDK 已到达 GA。  

### <a name="net"></a>.NET  

.NET SDK 已到达 GA。 

### <a name="windows-ui-library-3"></a>WindowsUI 库 3

可以使用 Windows App SDK 的[WinUI (3][UwpToolkitsWinui3Index] Windows UI 库 3) WebView2 Windows WebView2 控件。 This is currently in preview. 有关详细信息，请导航到 Windows [App SDK 路线图][WindowsAppSDK|::ref1::|]。

 
<!-- links -->  
[ConceptDistribution]: ./concepts/distribution.md "分发 WebView2 应用和 WebView2 运行时|Microsoft Docs"  
<!-- external links -->
[WindowsAppSDKRoadmap]: https://github.com/microsoft/WindowsAppSDK/blob/main/docs/roadmap.md "路线图"

[UwpToolkitsWinui3Index]: /uwp/toolkits/winui3/index "WindowsUI Library 3.0 Preview 1 (2020 年 5 月) |Microsoft Docs"  

[GithubMicrosoftedgeWebviewfeedbackMain]: https://github.com/MicrosoftEdge/WebViewFeedback "WebView 反馈 - MicrosoftEdge/WebViewFeedback | GitHub"  

[GithubMicrosoftUiXamlRoadmap]: https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md "WindowsUI 库路线图 - microsoft/microsoft-ui-xaml |GitHub"  
