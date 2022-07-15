---
title: WebView2 的主要类：环境、控制器和核心
description: 顶级 WebView2 类或接口如何协同工作概述：CoreWebView2Environment、CoreWebView2Controller 和 CoreWebView2。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 06/24/2022
ms.openlocfilehash: 1c4808388d294db68942ae0ccb4b890992fcac6b
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668592"
---
# <a name="main-classes-for-webview2-environment-controller-and-core"></a>WebView2 的主要类：环境、控制器和核心

<!-- keep sync'd:
* [Main classes: Environment, Controller, and Core](overview-features-apis.md#main-classes-environment-controller-and-core) in _Overview of WebView2 features and APIs_.
* [Main classes for WebView2: Environment, Controller, and Core](environment-controller-core.md) - topmost content.
-->

`CoreWebView2Controller``CoreWebView2` (`CoreWebView2Environment`或等效接口的类) 协同工作，以便应用可以托管 WebView2 浏览器控件并访问其浏览器功能。  这三个大类公开了主机应用可以访问的各种 API，为用户提供许多类别的浏览器相关功能。

*  该 `CoreWebView2Environment` 类表示一组 WebView2 控件，这些控件共享同一 WebView2 浏览器进程、用户数据文件夹和呈现器。  在此类 `CoreWebView2Environment` 中，你将创建对 `CoreWebView2Controller` 和 `CoreWebView2` 实例。
*  该 `CoreWebView2Controller` 类负责托管相关功能，例如窗口焦点、可见性、大小和输入，应用在其中托管 WebView2 控件。
*  该 `CoreWebView2` 类适用于 WebView2 控件的特定于 Web 的部分，包括网络、导航、脚本以及分析和呈现 HTML。

<!-- / keep sync'd -->

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


跨平台 API 实现：大多数 WebView2 API 最初是针对 C++开发的，然后大多数 C++ API 都包装为 C# API。  这样，平台和编程语言之间就具有一致的并行性和等效性。


#### <a name="overview-of-the-top-level-classes"></a>顶级类概述

概述：
* `CoreWebView2Environment`
* `CoreWebView2`
* `CoreWebView2Controller` `WebView2`与特定于 UI 框架的 WebView2 元素类（例如 WPF、WinForms 或 WinUI `WebView2` 类）) 类 (类。

或者，等效：
* `ICoreWebView2Environment`
* `ICoreWebView2`
* `ICoreWebView2Controller`

`CoreWebView2Environment` 表示一组 WebView2 控件，所有控件都共享以下内容：
*  它们共享相同的 WebView2 浏览器过程。
*  它们共享相同的用户数据文件夹。
*  它们可能共享 WebView2 呈现器和其他 WebView2 进程。

从中 `CoreWebView2Environment`创建 `CoreWebView2Controller` 并 `CoreWebView2` 配对。  他们总是走到一起作为一个 `CoreWebView2Controller` 和相应的 `CoreWebView2`。
*  负责 `CoreWebView2Controller` 所有与托管相关的功能，例如焦点、可见性、大小和输入。
*  适用于 `CoreWebView2` WebView2 控件的特定于 Web 的部分，包括网络、导航、脚本以及分析和呈现 HTML。


#### <a name="ui-framework-specific-webview2-element-class-such-as-wpf-winforms-or-winui-webview2-classes"></a>特定于 UI 框架的 WebView2 元素类，如 WPF、WinForms 或 WinUI WebView2 类

如果使用的是特定于 UI 框架的 WebView2 元素类（例如 WPF、WinForms 或 WinUI WebView2 类），则会有所不同。 

然后，WebView2 类可以选择使用， `CoreWebView2Environment` 否则会创建默认值 `CoreWebView2Environment`。  在内部，WebView2 类创建其和`CoreWebView2Controller``CoreWebView2`从中`CoreWebView2Environment`创建 。  公开 `WebView2` 其 `CoreWebView2` 作为 `CoreWebView2` 属性，但 `CoreWebView2Controller` 该属性对类保持私密 `WebView2` 性。  这是因为 `WebView2` 该类负责将所有 `CoreWebView2Controller` 功能连接到 UI 框架。


<!-- ====================================================================== -->
<!-- ## See also -->

<!--
* []()
* []()
-->
