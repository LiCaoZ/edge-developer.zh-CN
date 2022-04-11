---
title: WebView2 示例代码
description: GitHub上托管的 WebView2 示例代码的链接。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/21/2021
ms.openlocfilehash: 38fd6e7c7de9eef7a98aa71bf0644bceb42dc4ca
ms.sourcegitcommit: 5351b3950b3bb7bc698415a2e5608816f1f9fca4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2022
ms.locfileid: "12473953"
---
# <a name="sample-code-for-webview2"></a>WebView2 示例代码

本文介绍 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)中的示例、`.sln`文件和`README.md`文件。


<!-- ====================================================================== -->
## <a name="sample-code-for-get-started-guides"></a>入门指南的示例代码

WebView2 入门指南可帮助你创建与存储库中`WebView2Samples`相同的已完成的工作项目，你可以下载或克隆这些项目。

| 平台 | 文章 | 代码 |
|---|---|---|
| Win32 | [Win32 应用中的 WebView2 入门](get-started/win32.md) | [WebView2Samples > Win32_GettingStarted的](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted)初学者代码 |
| WinForms | [WinForms 应用中的 WebView2 入门](get-started/winforms.md) | [WebView2Samples > WinForms_GettingStarted](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinForms_GettingStarted)上的 .NET 初学者代码 |
| WinUI 2 | [WinUI 2 (UWP) 应用中的 WebView2 入门（公共预览版）](get-started/winui2.md) | 使用 WinUI 2 NuGet包。  没有示例代码。 |
| WinUI 3 | [在 WinUI 3 (Windows 应用 SDK) 应用中使用 WebView2 开始](get-started/winui.md) | [WebView2Samples > WinUI3_GettingStarted的](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted)初学者代码 |
| WPF | [WPF 应用中的 WebView2 入门](get-started/wpf.md) | [WebView2Samples 上的](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted) .NET 初学者代码> WPF_GettingStarted |


<!-- ====================================================================== -->
## <a name="apps-in-the-webview2samplessln-file"></a>WebView2Samples.sln 文件中的应用

存储 `WebView2Samples` 库包含演示 Win32、WPF、WinForms 和 WinUI 的 WebView2 控件和 WebView2 API 的示例。  这些示例是使用 Microsoft Edge WebView2 控件的混合应用程序。

1. 在单独的窗口或选项卡中，请参阅 [WebView2Samples 存储库 (自述文件页) ](https://github.com/MicrosoftEdge/WebView2Samples)。

1. 下载或克隆`WebView2Samples`存储库，如[下载 WebView2 示例存储库](how-to/machine-setup.md#download-the-webview2samples-repo)中所述，或在_为 WebView2 设置开发环境时克隆 WebView2_ [示例存储库](how-to/machine-setup.md#clone-the-webview2samples-repo)。

1. 在生成的存储库目录结构的本地副本中，查找 `*.sln` 文件。

1. 打开其中 `.sln` 一个文件。  例如，打开多平台解决方案文件 [WebView2Samples/SampleApps/WebView2Samples.sln 的](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln)本地副本 (下载为Microsoft Visual Studio中的路径`WebView2Samples-master/SampleApps/WebView2Samples.sln`) 。  在 Visual Studio 中打开该解决方案文件时，**解决方案资源管理器**包含以下 WebView2 示例，作为项目：

   ![解决方案资源管理器 WebView2Samples 存储库，将 WebView2 示例显示为项目。](media/solution-file-webview2samples.png)

此特定`.sln`文件不包括入门项目，这些项目是单独`.sln`的文件，每个平台一个。

存储 `WebView2Samples` 库包含以下项目。  这些项目包含在文件中 `WebView2Samples.sln` ，每个平台也有一个专用 `.sln` 文件。

| 示例类型 | 示例Project | 描述 |
|---|---|---|
| UWP WinUI 2 浏览器 | [webview2_sample_uwp](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/webview2_sample_uwp#readme) | 在 UWP 应用程序中嵌入 WebView2 控件。<br/><br/>  作为 UWP Visual Studio 2019 项目生成。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| Win32 C++ | [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) | 在 Win32 本机应用程序中嵌入 WebView2 控件。  演示了 WebView2 事件处理程序和 API 方法的选择，这些方法允许本机 Win32 应用程序直接与 WebView2 控件交互，反之亦然。<br/><br/>  在 [2019 Visual Studio作为 Win32](https://visualstudio.microsoft.com/vs/) 项目生成。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。<br/><br/>该 `.sln` 文件位于父目录 [SampleApps](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps) 目录中。 |
| 使用 Visual Composition 的 Win32 C++ | [WebView2SampleWinComp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp) | 在 Win32 本机应用程序中嵌入 WebView2 控件。  使用[Windows 运行时组合 API](/uwp/api/windows.ui.composition)（也称为视觉对象层）利用最新的Windows 10或更高版本的 UI 功能，并在 C++ Win32 应用程序中创建更好的外观、感觉和功能。<br/><br/>  在 2019 Visual Studio作为 Win32 项目生成。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| WinForms | [WebView2WindowsFormsBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WindowsFormsBrowser) | 在Windows 窗体应用程序中嵌入 WebView2 控件。<br/><br/>  Visual Studio 2019 年作为Windows 窗体项目生成。  在 WebView2 环境中使用 C# 和 HTML/CSS/JavaScript。 |
| Windows Presentation Foundation (WPF) .NET | [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser) | 在 WPF 应用程序中嵌入 WebView2 控件。<br/><br/>  在 2019 Visual Studio构建为 WPF 项目。  在 WebView2 环境中使用 C# 和 HTML/CSS/JavaScript。 |
| WPF 中的 Chrome DevTools 协议 (CDP)  | [WV2CDPExtensionWPFSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample) | 使用 `DevToolsProtocolHelper` WebView2 中的对象使用 Chrome [DevTools 协议](../devtools-protocol-chromium/index.md)函数。  演示 WPF 中 WebView2 CDP 扩展的使用模式。  此应用程序是使用 [WebView2 CDP 扩展](https://aka.ms/webviewcdp) 构建的，该扩展定义所有 CDP 方法、事件和类型。<br/><br/>  在 2019 Visual Studio构建为 WPF 项目。  在 WebView2 环境中使用 C#。 |
| 用于部署运行时的 WiX 燃烧捆绑包 | [WV2DeploymentWiXBurnBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md) | 为 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md) 创建 [WiX](https://wixtoolset.org/) 安装程序，并使用 [WiX Burn 捆绑包](https://wixtoolset.org/documentation/manual/v3/bundle/)链接安装 Evergreen WebView2 运行时。<br/><br/>  使用应用部署 [Evergreen WebView2 运行时](concepts/distribution.md) 时使用。 |
| 用于部署运行时的 WiX 自定义操作 | [WV2DeploymentWiXCustomActionSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXCustomActionSample/README.md) | 为 `WebView2APISample` WiX 安装程序创建 WiX 安装程序，并使用 [WiX 自定义操作](https://wixtoolset.org/documentation/manual/v3/wixdev/extensions/authoring_custom_actions.html) 链接安装 Evergreen WebView2 运行时。<br/><br/>  使用应用部署 Evergreen WebView2 运行时时使用。 |


<!-- ====================================================================== -->
## <a name="uwpwinui-samples"></a>UWP/WinUI 示例

[WinUI 控件库](https://github.com/microsoft/Xaml-Controls-Gallery/tree/winui3preview)提供了适用于 UWP/WinUI 的综合 API 示例。

此 WinUI 控件库示例以交互式格式显示所有 XAML 控件。  此应用是[Fluent设计指南](/windows/uwp/design/basics/)的交互式配套，显示 UWP XAML API 和 [Windows UI Toolkit](/uwp/toolkits/winui/) API 的用法。


<!-- ====================================================================== -->
## <a name="deploy-the-evergreen-webview2-runtime"></a>部署 Evergreen WebView2 运行时

[WV2DeploymentVSInstallerSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentVSInstallerSample/README.md) 使用[适用于 Visual Studio 的 Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) 扩展，为 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md) 创建安装程序，并链接安装 Evergreen WebView2 运行时。

此示例是一个单独的安装程序。 它不是存储库的一 `WebView2Samples` 部分。

<!--
| WebView2 Deployment VS Installer | [WV2DeploymentVSInstallerSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentVSInstallerSample) | Creates a VS installer that chain-installs the Evergreen WebView2 Runtime. |
-->


<!-- ====================================================================== -->
## <a name="directory-structure-of-the-webview2samples-repo"></a>WebView2Samples 存储库的目录结构

对于一般初始开发人员环境设置，可以从`WebView2Samples`存储库中打开任何`.sln`文件：

*  [GettingStartedGuides 目录](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides)中的四个特定`.sln`于平台的文件之一。

*  [SampleApps 目录](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps)中的多平台`.sln`文件。  具有较长 [的 WebView2 API 示例自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme)。

*  [SampleApps 目录](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps)中五个特定`.sln`于平台的文件之一。  这些演示如何将 WebView2 控件添加到各种平台上的应用。


存储 `WebView2Samples` 库包含两个主要部分：

*  一组入门解决方案 (`.sln`文件及其各种项目文件) 。  每个文件都有`.sln`一个`README.md`文件;其中大多数非常短。  大多数文档都位于当前的一组文章中。

*  一组特定于平台的示例 (每个示例都有其自己的目录和 `.sln` 文件) ，以及一个多平台 `.sln` 文件。


若要下载或克隆此存储库，请参阅 [为 WebView2 设置开发人员环境](how-to/machine-setup.md)。

*  如果克隆存储库，则可以使用 git 命令或各种开发人员应用的功能更新本地副本。

*  如果将存储库下载为 `.zip` 文件，则会获得存储库的快照副本。  然后，可以稍后下载另一个更新的存储库副本。


<!-- ====================================================================== -->
## <a name="local-paths-for-sln-and-readmemd-files"></a>.sln 和 README.md 文件的本地路径

本部分显示下载存储库或将存储库克隆到本地驱动器所产生的每个 `.sln` 和 `README.md` 文件的路径。

存储 `WebView2Samples` 库包含多个 `README.md` 文件和 `.sln` 文件，如下所示。  下载或克隆存储库时，可以在Visual Studio中查看这些`README.md`文件中的任何一个。  或者，在GitHub存储库中联机查看它们。

在下载 `.zip` 的文件中，根目录是命名 `WebView2Samples-master` 的，而不是 `WebView2Samples`表示 `master` 存储库的分支。

在下面的链接中，将显示 .sln 或 README.md 的本地目录路径。  链接将转到GitHub存储库的目录级别，可在其中查看`.sln`目录列表中的或`README.md`文件。  在GitHub时，自述文件会自动追加到包含自述文件的目录的网页。
<!--
pattern for link construction below: 
for the .sln line, link text = local path to .sln
URL for .sln = dir that visibly contains the .sln file
URL for README = dir that visibly contains the README.md file (visible if you scroll up); that URL is appended with #readme
-->


**总体存储库的顶级自述文件：**

*  [WebView2Samples/README.md](https://github.com/MicrosoftEdge/WebView2Samples#readme) - 2 页。  建议的概述类似于当前文章。


**`GettingStartedGuides` 目录：每个平台教程的解决方案和自述文件：**

入门指南有四个特定于平台的解决方案文件：


* Win32 入门： [WebView2Samples/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted)
   *  [WebView2Samples/GettingStartedGuides/Win32_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted#readme)

* WinUI 3 入门： [WebView2Samples/GettingStartedGuides/WinUI3_GettingStarted/WinUI_Sample/WinUI_Sample.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted/WinUI_Sample)
   *  [WebView2Samples/GettingStartedGuides/WinUI3_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted#readme)

* WinForms 入门： [WebView2Samples/GettingStartedGuides/WinForms_GettingStarted/WinForms_GettingStarted.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinForms_GettingStarted)
   *  无 README 文件。

* WPF 入门： [WebView2Samples/GettingStartedGuides/WPF_GettingStarted/WPFSample.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted)
   * [WebView2Samples/GettingStartedGuides/WPF_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted#readme)


**`SampleApps` 目录：解决方案和自述文件：**

有一个多平台解决方案文件：

*  WebView2Samples： [WebView2Samples/SampleApps/WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps) - 此解决方案文件包括多个平台项目。
   *  [WebView2Samples/SampleApps/WebView2APISample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) - “WebView2 API 示例”的推荐长自述文件。  此示例是应用程序在 Win32 本机应用程序中嵌入 WebView2 控件的示例。  它构建为 Win32 Visual Studio 2019 项目，在 WebView2 环境中同时使用 C++ 和 HTML/CSS/JavaScript。  它展示了一系列 WebView2 的事件处理程序和 API 方法，这些方法允许本机 Win32 应用程序直接与 WebView2 控件交互，反之亦然。

有五个特定于平台的解决方案文件：

*  webview2_sample_uwp： [WebView2Samples/SampleApps/webview2_sample_uwp/webview2_sample_uwp.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/webview2_sample_uwp)
   *  [WebView2Samples/SampleApps/webview2_sample_uwp/readme.md](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/webview2_sample_uwp#readme)

*  WebView2WpfBrowser： [WebView2Samples/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser)
   *  [WebView2Samples/SampleApps/WebView2WpfBrowser/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser#readme)

*  WebView2WindowsFormsBrowser： [WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WindowsFormsBrowser)
   *  [WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WindowsFormsBrowser#readme)

*  WebView2SampleWinComp： [WebView2Samples/SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp)
   *  [WebView2Samples/SampleApps/WebView2SampleWinComp/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp#readme)

*  WV2CDPExtensionWPFSample： [WebView2Samples/SampleApps/WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample)
   *  [WebView2Samples/SampleApps/WV2CDPExtensionWPFSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample#readme)


**WIX 和部署安装程序的自述文件：**

这些文件不使用 `.sln` 文件。

*  [WebView2Samples/SampleApps/WV2DeploymentWiXCustomActionSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXCustomActionSample#readme)
*  [WebView2Samples/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#readme)
*  [WebView2Samples/SampleApps/WV2DeploymentVSInstallerSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentVSInstallerSample#readme)


**下载的存储库具有较长的根目录名称**

如果将存储库 (下载为 `.zip` 文件) ，则已追加根目录名称 `-master` 。  若要匹配存储库 () `WebView2Samples` 的名称，可以重命名根目录。


目录中特定于 Win32 的 `GettingStartedGuides` 解决方案具有以下路径：

*  如果下载了存储库： 
   * `WebView2Samples-master/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln`

*  如果克隆了存储库： 
   * `WebView2Samples/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln`


目录中 `SampleApps` 的主要多项目 Win32 解决方案具有以下路径：

*  如果下载了存储库： 
   * `WebView2Samples-master/SampleApps/WebView2Samples.sln`

*  如果克隆了存储库： 
   * `WebView2Samples/SampleApps/WebView2Samples.sln`
