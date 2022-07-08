---
title: 使用 Microsoft Edge DevTools 调试 WebView2 应用
description: 如何在使用 WebView2 应用时打开 Microsoft Edge DevTools。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 07/07/2022
ms.openlocfilehash: 32705123064d6fe2ce41519ce928a30cb809839f
ms.sourcegitcommit: 9cc13dd2d0e0360013a127b8e39b09e535b08f1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2022
ms.locfileid: "12636255"
---
# <a name="debug-webview2-apps-with-microsoft-edge-devtools"></a>使用 Microsoft Edge DevTools 调试 WebView2 应用

使用 Microsoft Edge 开发人员工具调试 WebView2 控件中显示的 Web 内容，就像调试 Microsoft Edge 中显示的另一个网页一样。

![WebView2 控件中的 DevTools 调试。](media/f12.png)

使用 WebView2 应用时，可以通过多种方式打开 DevTools：

*  按 `F12`。
*  按 `Ctrl`++`Shift``I`。
*  右键单击页面，然后选择 `Inspect`。

应用还可以使用 `OpenDevToolsWindow` API 以编程方式打开 DevTools 窗口。  例如，如果已删除上述热键和上下文菜单项，则可以使用此方法。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.OpenDevToolsWindow 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.opendevtoolswindow)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.OpenDevToolsWindow 方法](/en-us/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#opendevtoolswindow)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：OpenDevToolsWindow 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#opendevtoolswindow)

---

如果上述任何方法都不可用，则可以通过环境变量或注册表项添加 `--auto-open-devtools-for-tabs` 到浏览器参数。  创建 WebView2 时，此方法将打开 DevTools 窗口。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [DevTools 概述](../index.md)。
* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also) _Microsoft Edge WebView2 简介_。
