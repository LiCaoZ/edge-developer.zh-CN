---
title: WebView2 示例代码
description: 指向托管在 webView2 示例代码GitHub。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/21/2021
ms.openlocfilehash: 8a45a84c8e33bd2f785ad33fe3722cce92f6b972
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319106"
---
# <a name="webview2-sample-code"></a>WebView2 示例代码

以下 WebView2 示例在 WebView2 入门和[WebView2 示例](https://github.com/MicrosoftEdge/WebView2Samples)存储库的指南中提供。


<!-- ====================================================================== -->
## <a name="sample-code-for-get-started-guides"></a>指南入门代码

WebView2 入门指南使用 Win32、Windows Presentation Foundation (WPF) 、WinForms 和 WinUI 的入门代码。

| 平台 | 文章 | 代码 |
|---|---|---|
| Win32 | [Win32 应用中的 WebView2 入门](./get-started/win32.md) | [WebView2 示例 Win32 入门指南中的入门 (github.com) ](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted) |
| WPF | [WPF 应用中的 WebView2 入门](./get-started/wpf.md) | WebView2 示例 WPF 入门中的 .NET [初学者 (github.com) ](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted) |
| WinForms | [WinForms 应用中的 WebView2 入门](./get-started/winforms.md) | WebView2 示例[WinForms 入门](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinForms_GettingStarted)指南中的 .NET 初学者 (github.com)  |
| WinUI 3 | [WinUI 3 应用 SDK (Windows中的 WebView2) ](./get-started/winui.md) | [WebView2 示例 WinUI 入门指南中的入门 (github.com) ](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted) |
| WinUI 2 | [WinUI 2 应用指南中的 WebView2 入门](./get-started/winui2.md) | 使用 WinUI 2 NuGet包。  没有示例代码。 |


<!-- ====================================================================== -->
## <a name="apps-in-the-webview2-samples-repo"></a>WebView2 示例存储库的应用

[WebView2 示例存储库包括](https://github.com/MicrosoftEdge/WebView2Samples)Win32、WPF、WinForms 和 WinUI 的示例项目。  这些示例是使用 WebView2 Microsoft Edge混合应用程序。

克隆 WebView2 示例存储库，然后打开解决方案文件[WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln) Microsoft Visual Studio。  当您在解决方案资源管理器中打开解决方案Visual Studio，解决方案资源管理器**将包含**以下 WebView2 示例作为项目：

:::image type="content" source="media/solution-file-webview2samples.png" alt-text="WebView2Samples 存储库的解决方案资源管理器，将 WebView2 示例作为项目显示。" lightbox="media/solution-file-webview2samples.png":::

WebView2 示例存储库包含以下项目中 `WebView2Samples.sln` 的项目：

| 示例类型 | 示例Project | 描述 |
|---|---|---|
| Win32 C++ | [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample) | 在 Win32 本机应用程序中嵌入 WebView2。  阐述一系列 WebView2 事件处理程序和 API 方法，这些方法允许本机 Win32 应用程序直接与 WebView 交互，反之亦然。<br/><br/>  在[2019](https://visualstudio.microsoft.com/vs/)年 3 月Visual Studio Win32 项目。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| 具有可视合成的 Win32 C++ | [WebView2SampleWinComp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp) | 在 Win32 本机应用程序中嵌入 WebView2。  使用[Windows](/uwp/api/windows.ui.composition)运行时合成 API（也称为可视化层）利用最新的 Windows 10 或更高版本的 UI 功能，在 C++ Win32 应用程序中创建更好的外观和功能。<br/><br/>  在 2019 年 3 月Visual Studio Win32 项目。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| WinForms | [WebView2WindowsFormsBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WindowsFormsBrowser) | 将 WebView2 嵌入 Windows Forms 应用程序中。<br/><br/>  在 2019 Windows表单项目Visual Studio构建。  在 WebView2 环境中C#和 HTML/CSS/JavaScript。 |
| Windows Presentation Foundation (.NET) WPF | [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser) | 在 WPF 应用程序中嵌入 WebView2。<br/><br/>  在 2019 年 3 月Visual Studio WPF 项目。  在 WebView2 环境中C#和 HTML/CSS/JavaScript。 |
| WPF 中的 Chrome DevTools (CDP)  | [WV2CDPExtensionWPFSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample) | 使用 Chrome [DevTools 协议](../devtools-protocol-chromium\index.md) 函数，使用 `DevToolsProtocolHelper` WebView2 中的对象。  演示 WPF 中 WebView2 CDP 扩展的使用模式。  此应用程序是使用定义所有 CDP 方法、事件和类型的 [WebView2 CDP 扩展](https://aka.ms/webviewcdp) 构建的。<br/><br/>  在 2019 年 3 月Visual Studio WPF 项目。  在 C#2 环境中使用 WebView2。 |
| 部署运行时的 WiX 刻录捆绑包 | [WV2DeploymentWiXBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md) | 为[WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md)创建[WiX](https://wixtoolset.org/)安装程序，并使用[WiX 刻录捆绑](https://wixtoolset.org/documentation/manual/v3/bundle/)包链安装 Evergreen WebView2 运行时。<br/><br/>  在将 [Evergreen WebView2 运行时与你的应用一](concepts/distribution.md) 起部署时使用。 |
| 部署运行时的 WiX 自定义操作 | [WV2DeploymentWiXCustomActionSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXCustomActionSample/README.md) | 为 创建 WiX 安装程序， `WebView2APISample` 并使用 [WiX 自定义操作](https://wixtoolset.org/documentation/manual/v3/wixdev/extensions/authoring_custom_actions.html) 链接安装 Evergreen WebView2 运行时。<br/><br/>  在将 Evergreen WebView2 运行时与你的应用一起部署时使用。 |


<!-- ====================================================================== -->
## <a name="uwpwinui-samples"></a>UWP/WinUI 示例

WinUI 控件库中提供了适用于 UWP/WinUI 的全面 API [示例](https://github.com/microsoft/Xaml-Controls-Gallery/tree/winui3preview)。

此 WinUI 控件库示例以交互式格式显示所有 XAML 控件。  此应用是 Fluent[设计](/windows/uwp/design/basics/)指南的交互式助手，它显示了 UWP XAML API 和 UWP UI Windows [API](/uwp/toolkits/winui/) Toolkit用法。


<!-- ====================================================================== -->
## <a name="deploy-the-evergreen-webview2-runtime"></a>部署 Evergreen WebView2 运行时

[WV2DeploymentVSInstallerSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentVSInstallerSample/README.md)使用适用于 Visual Studio 的[Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects)扩展，为[WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md)创建安装程序并链安装 Evergreen WebView2 Runtime。

此示例是单独的安装程序。 这不是存储库的 `WebView2Samples` 一部分。
