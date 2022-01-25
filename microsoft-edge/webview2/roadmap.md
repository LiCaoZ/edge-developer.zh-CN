---
title: WebView2 路线图
description: 了解 WebView2 接下来将做什么。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 01/07/2021
ms.openlocfilehash: 7c058898124b3e7e58c6a1aacd29e89e51ec834b
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319582"
---
# <a name="webview2-roadmap"></a>WebView2 路线图

WebView2 Microsoft Edge WebView2 控件允许你在本机应用程序中嵌入 Web 技术。  本文概述了 WebView2 的潜在路线图。

WebView2 正在积极开发中，路线图将继续根据市场变化和客户反馈不断发展。  此处列出的计划并不详尽，可能会发生变化。

如果你对路线图有疑问或疑问，请从反馈存储库 [提供反馈](https://github.com/MicrosoftEdge/WebViewFeedback)。

WebView2 团队正在计划以下主要工作，用于将来的更新：

* UWP 预览版
* MacOS 预览版
* Xbox 预览版
* HoloLens 预览版
* Linux 预览版


<!-- ====================================================================== -->
## <a name="webview2-runtime-and-installer"></a>WebView2 运行时和安装程序

使用常青分发模式，你可以将 WebView2 运行时目标或链安装到用户计算机上。  Evergreen WebView2 运行时和安装程序已使用 GA (通用) 。  有关详细信息，请参阅分发 [WebView2 应用和 WebView2 运行时](./concepts/distribution.md)。


<!-- ====================================================================== -->
## <a name="fixed-version"></a>固定版本

固定版本分发模式允许你打包Microsoft Edge二进制文件 <!--(a specific version of the WebView2 Runtime)--> 在本机应用程序中。  固定版本已进入通用版本 (GA) 。  有关详细信息，请参阅分发 [WebView2 应用和 WebView2 运行时](./concepts/distribution.md)。


<!-- ====================================================================== -->
## <a name="general-availability"></a>通用

以下技术已进入通用通用 (GA) 。

### <a name="win32-cc"></a>Win32 C/C++

Win32 C/C++ SDK 已到达 GA。

### <a name="net"></a>.NET

.NET SDK 已到达 GA。

### <a name="windows-ui-library-3"></a>Windows UI 库 3

可以使用 Windows App SDK 的[WinUI3](/uwp/toolkits/winui3/index) (UI 库 3) 应用程序中Windows WebView2 控件。  This is currently in preview. 有关详细信息，请参阅应用[Windows SDK 路线图](https://github.com/microsoft/WindowsAppSDK/blob/main/docs/roadmap.md)。
