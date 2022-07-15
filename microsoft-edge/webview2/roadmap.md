---
title: WebView2 路线图
description: 了解 WebView2 的下一步操作。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 01/07/2021
ms.openlocfilehash: aee1b52a559ea898f30d93c7cec51a87951c917a
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668886"
---
# <a name="webview2-roadmap"></a>WebView2 路线图

Microsoft Edge WebView2 控件允许你在本机应用程序中嵌入 Web 技术。  本文概述了 WebView2 的预期路线图。

WebView2 正在积极开发中，根据市场变化和客户反馈，路线图将继续发展。  此处概述的计划并不详尽，可能会发生变化。

如果对路线图有疑问或疑问，请在 [反馈存储库中提供反馈](https://github.com/MicrosoftEdge/WebViewFeedback)。

WebView2 团队正在规划未来更新的以下主要工作：

* UWP 预览版
* MacOS 预览版
* Xbox 预览版
* HoloLens 预览版
* Linux 预览版


<!-- ====================================================================== -->
## <a name="webview2-runtime-and-installer"></a>WebView2 运行时和安装程序

常青分发模式允许你将 WebView2 运行时定向或链接安装到用户的计算机上。  Evergreen WebView2 运行时和安装程序已 (正式版正式发布) 。  有关详细信息，请参阅 [“分发应用”和“WebView2 运行时](concepts/distribution.md)”。


<!-- ====================================================================== -->
## <a name="fixed-version"></a>固定版本

使用固定版本分发模式可以打包 Microsoft Edge 二进制文件 <!--(a specific version of the WebView2 Runtime)--> 在本机应用程序中。  固定版本已 (正式版) 正式发布。  有关详细信息，请参阅 [“分发应用”和“WebView2 运行时](concepts/distribution.md)”。


<!-- ====================================================================== -->
## <a name="general-availability"></a>正式发布

以下技术已 (正式发布) 。

### <a name="win32-cc"></a>Win32 C/C++

Win32 C/C++ SDK 已到达 GA。

### <a name="net"></a>.NET

.NET SDK 已到达 GA。

### <a name="windows-ui-library-3"></a>Windows UI 库 3

可以将 [Windows UI 库 3 (WinUI 3) 与Windows 应用 SDK](/uwp/toolkits/winui3/index)一起访问应用程序中的 WebView2 控件。  目前为预览版。 有关详细信息，请参阅[Windows 应用 SDK路线图](https://github.com/microsoft/WindowsAppSDK/blob/main/docs/roadmap.md)。
