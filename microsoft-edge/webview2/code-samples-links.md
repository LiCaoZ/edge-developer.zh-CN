---
title: WebView2 的示例代码
description: 指向托管在 WebView2 示例代码GitHub。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/21/2021
ms.openlocfilehash: f353f97aa1711d747847b18d304c53604f6e7605
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433081"
---
# <a name="sample-code-for-webview2"></a>WebView2 的示例代码

本文介绍 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples)`.sln` `README.md` 存储库包含哪些示例、文件和文件。


<!-- ====================================================================== -->
## <a name="sample-code-for-get-started-guides"></a>指南入门代码

WebView2 入门`WebView2Samples`指南可帮助你创建与存储库相同的已完成工作项目，你可以下载或克隆这些项目。

| 平台 | 文章 | 代码 |
|---|---|---|
| Win32 | [Win32 应用中的 WebView2 入门](get-started/win32.md) | [WebView2Samples > Win32_GettingStarted](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted) |
| WinForms | [WinForms 应用中的 WebView2 入门](get-started/winforms.md) | [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinForms_GettingStarted) 网站的 .NET 初学者> WinForms_GettingStarted |
| WinUI 2 | [WinUI 2 (UWP) 应用中的 WebView2 入门（公共预览版）](get-started/winui2.md) | 使用 WinUI 2 NuGet包。  没有示例代码。 |
| WinUI 3 | [WinUI 3 中的 WebView2 入门 (Windows App SDK) 应用](get-started/winui.md) | [WebView2Samples > WinUI3_GettingStarted](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted) |
| WPF | [WPF 应用中的 WebView2 入门](get-started/wpf.md) | [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted) 网站的 .NET 初学者> WPF_GettingStarted |


<!-- ====================================================================== -->
## <a name="apps-in-the-webview2samplessln-file"></a>WebView2Samples.sln 文件中的应用程序

存储库 `WebView2Samples` 包括演示 Win32、WPF、WinForms 和 WinUI 的 WebView2 控件和 WebView2 API 的示例。  这些示例是使用 WebView2 Microsoft Edge混合应用程序。

1. 在单独的窗口或选项卡中，请参阅 [WebView2Samples 存储库 (自述 ](https://github.com/MicrosoftEdge/WebView2Samples)) 。

1. 下载或克隆 `WebView2Samples` 存储库，如为 [WebView2](how-to/machine-setup.md#download-the-webview2samples-repo) 设置开发环境中的下载 [WebView2](how-to/machine-setup.md#clone-the-webview2samples-repo) 示例存储库或克隆 _WebView2_ 示例存储库中所述。

1. 在生成的存储库目录结构的本地副本中，查找 `*.sln` 文件。

1. 打开其中一 `.sln` 个文件。  例如，打开多平台解决方案文件 [WebView2Samples/SampleApps/WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln) (`WebView2Samples-master/SampleApps/WebView2Samples.sln` 的本地副本，) Microsoft Visual Studio。  当您在解决方案资源管理器中打开该解决方案文件时Visual Studio，解决方案**资源管理器将包含**以下 WebView2 示例作为项目：

   ![WebView2Samples 存储库的解决方案资源管理器，将 WebView2 示例作为项目显示。](media/solution-file-webview2samples.png)

此特定`.sln`文件不包括单独的入门，每个平台`.sln`一个单独的文件。

存储库 `WebView2Samples` 包含以下项目。  这些项目包含在文件中 `WebView2Samples.sln` ，并且每个平台还具有一个专用 `.sln` 文件。

| 示例类型 | 示例Project | 说明 |
|---|---|---|
| UWP WinUI 2 浏览器 | [webview2_sample_uwp](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/webview2_sample_uwp#readme) | 在 UWP 应用程序中嵌入 WebView2 控件。<br/><br/>  生成为 UWP Visual Studio 2019 项目。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| Win32 C++ | [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) | 在 Win32 本机应用程序中嵌入 WebView2 控件。  阐述一系列 WebView2 事件处理程序和 API 方法，这些方法允许本机 Win32 应用程序直接与 WebView 交互，反之亦然。<br/><br/>  在 [2019 年 3 月Visual Studio Win32 项目](https://visualstudio.microsoft.com/vs/)。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。<br/><br/>该文件 `.sln` 位于父 [SampleApps](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps) 目录中。 |
| 具有可视合成的 Win32 C++ | [WebView2SampleWinComp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp) | 在 Win32 本机应用程序中嵌入 WebView2 控件。  使用 [Windows](/uwp/api/windows.ui.composition) 运行时合成 API（也称为可视化层）利用最新的 Windows 10 或更高版本的 UI 功能，在 C++ Win32 应用程序中创建更好的外观和功能。<br/><br/>  在 2019 年 3 月Visual Studio Win32 项目。  在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。 |
| WinForms | [WebView2WindowsFormsBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WindowsFormsBrowser) | 将 WebView2 控件嵌入 Windows Forms 应用程序中。<br/><br/>  在 2019 年Windows表单项目Visual Studio构建。  在 WebView2 环境中C#和 HTML/CSS/JavaScript。 |
| Windows Presentation Foundation (.NET) WPF | [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser) | 在 WPF 应用程序中嵌入 WebView2 控件。<br/><br/>  在 2019 年 10 月Visual Studio WPF 项目。  在 WebView2 环境中C#和 HTML/CSS/JavaScript。 |
| WPF 中的 Chrome DevTools (CDP)  | [WV2CDPExtensionWPFSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample) | 使用 Chrome [DevTools 协议](../devtools-protocol-chromium/index.md) 函数，使用 `DevToolsProtocolHelper` WebView2 中的对象。  演示 WPF 中 WebView2 CDP 扩展的使用模式。  此应用程序是使用定义所有 CDP 方法、事件和类型的 [WebView2 CDP 扩展](https://aka.ms/webviewcdp) 构建的。<br/><br/>  在 2019 年 10 月Visual Studio WPF 项目。  在 C#2 环境中使用 Web 视图。 |
| 部署运行时的 WiX 刻录捆绑包 | [WV2DeploymentWiXBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md) | 为 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md) 创建 [WiX](https://wixtoolset.org/) 安装程序，并使用 [WiX 刻录捆绑](https://wixtoolset.org/documentation/manual/v3/bundle/)包链安装 Evergreen WebView2 运行时。<br/><br/>  在将 [Evergreen WebView2 运行时与你的应用一](concepts/distribution.md) 起部署时使用。 |
| 部署运行时的 WiX 自定义操作 | [WV2DeploymentWiXCustomActionSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentWiXCustomActionSample/README.md) | 为 创建 WiX 安装程序 `WebView2APISample` ，并使用 [WiX 自定义操作](https://wixtoolset.org/documentation/manual/v3/wixdev/extensions/authoring_custom_actions.html) 链接安装 Evergreen WebView2 运行时。<br/><br/>  在将 Evergreen WebView2 运行时与你的应用一起部署时使用。 |


<!-- ====================================================================== -->
## <a name="uwpwinui-samples"></a>UWP/WinUI 示例

WinUI 控件库中提供了适用于 UWP/WinUI 的全面 API [示例](https://github.com/microsoft/Xaml-Controls-Gallery/tree/winui3preview)。

此 WinUI 控件库示例以交互式格式显示所有 XAML 控件。  此应用是 Fluent [设计](/windows/uwp/design/basics/)指南的交互式配套设备，它显示了 UWP XAML API 和 UWP UI Windows [API Toolkit](/uwp/toolkits/winui/)用法。


<!-- ====================================================================== -->
## <a name="deploy-the-evergreen-webview2-runtime"></a>部署 Evergreen WebView2 运行时

[WV2DeploymentVSInstallerSample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WV2DeploymentVSInstallerSample/README.md) 使用适用于 Visual Studio 的 [Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) 扩展，为 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md) 创建安装程序并链安装 Evergreen WebView2 Runtime。

此示例是单独的安装程序。 这不是存储库的 `WebView2Samples` 一部分。

<!--
| WebView2 Deployment VS Installer | [WV2DeploymentVSInstallerSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentVSInstallerSample) | Creates a VS installer that chain-installs the Evergreen WebView2 Runtime. |
-->


<!-- ====================================================================== -->
## <a name="directory-structure-of-the-webview2samples-repo"></a>WebView2Samples 存储库的目录结构

对于常规的初始开发人员环境设置，你可以 `.sln` 从存储库打开任何 `WebView2Samples` 文件：

*  `.sln` [GettingStartedGuides](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides) 目录中的四个特定于平台的文件之一。

*  `.sln` [SampleApps 目录中的多平台文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps)。  具有一个长 [WebView2 API 示例自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme)。

*  SampleApps 目录中五个 `.sln` 特定于平台 [的文件之一](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps)。  这些演示了将 WebView2 控件添加到不同平台上的应用。


存储库 `WebView2Samples` 有两个主要部分：

*  一组入门解决方案 (`.sln`文件及其各种项目) 。  每个文件 `README.md` 都有一个文件 `.sln` ;其中大多数文件非常短。  大多数文档都位于当前文章集内。

*  一组特定于平台 `.sln` 的示例 (，每个示例都有自己的目录和文件) ，以及一个多平台 `.sln` 文件。


若要下载或克隆此存储库，请参阅 [设置 WebView2 的开发人员环境](how-to/machine-setup.md)。

*  如果你克隆存储库，可以使用 git 命令或各种开发人员应用的功能更新本地副本。

*  如果将存储库下载为文件 `.zip` ，则获取存储库的快照副本。  然后，你可以下载该存储库的另一个更新副本。


<!-- ====================================================================== -->
## <a name="local-paths-for-sln-and-readmemd-files"></a>.sln 和 README.md 文件的本地路径

此部分显示每个 和 `.sln` `README.md` 文件的路径，该路径由下载存储库或将存储库克隆到本地驱动器所生成。

存储库 `WebView2Samples` 包含多个文件和 `README.md` 文件 `.sln` ，如下所示。  在下载或克隆存储库时，可以在`README.md`该文件中查看Visual Studio。  或者，在资源存储库GitHub查看它们。

在下载的 `.zip` 文件中，根目录 `WebView2Samples-master` 命名为 而不是 `WebView2Samples`， `master` 表示存储库的分支。

在下面的链接中，将显示指向 .sln 或 README.md 的本地目录路径。  该链接将GitHub`.sln`存储库的目录级别，可在其中查看目录`README.md`一览中的 或 文件。  在GitHub时，会自动将自述文件追加到包含自述文件的目录的网页。
<!--
pattern for link construction below: 
for the .sln line, link text = local path to .sln
URL for .sln = dir that visibly contains the .sln file
URL for README = dir that visibly contains the README.md file (visible if you scroll up); that URL is appended with #readme
-->


**整个存储库的顶级自述：**

*  [WebView2Samples/README.md](https://github.com/MicrosoftEdge/WebView2Samples#readme) - 2 个页面。  建议概述，类似于本文。


**`GettingStartedGuides` directory： solution and readme files， for the per-platform tutorials：**

有四个特定于平台的解决方案文件用于入门指南：


* Win32 入门： [WebView2Samples/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted)
   *  [WebView2Samples/GettingStartedGuides/Win32_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted#readme)

* WinUI 3 入门： [WebView2Samples/GettingStartedGuides/WinUI3_GettingStarted/WinUI_Sample/WinUI_Sample.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted/WinUI_Sample)
   *  [WebView2Samples/GettingStartedGuides/WinUI3_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted#readme)

* WinForms 入门： [WebView2Samples/GettingStartedGuides/WinForms_GettingStarted/WinForms_GettingStarted.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinForms_GettingStarted)
   *  无自述文件。

* WPF 入门： [WebView2Samples/GettingStartedGuides/WPF_GettingStarted/WPFSample.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted)
   * [WebView2Samples/GettingStartedGuides/WPF_GettingStarted/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted#readme)


**`SampleApps` 目录：解决方案和自述文件：**

有一个多平台解决方案文件：

*  WebView2Samples： [WebView2Samples/SampleApps/WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps) - 此解决方案文件包含多个平台项目。
   *  [WebView2Samples/SampleApps/WebView2APISample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) - 建议用于"WebView2 API 示例"的长自述文件。  此示例是一个在 Win32 本机应用程序中嵌入 WebView 的应用程序示例。  它构建为 Win32 Visual Studio 2019 项目，并使用 WebView2 环境中 C++ 和 HTML/CSS/JavaScript。  它展示 WebView2 的一系列事件处理程序和 API 方法，允许本机 Win32 应用程序直接与 WebView 交互，反之亦然。

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

这些不使用 `.sln` 文件。

*  [WebView2Samples/SampleApps/WV2DeploymentWiXCustomActionSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXCustomActionSample#readme)
*  [WebView2Samples/SampleApps/WV2DeploymentWiXBundleSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#readme)
*  [WebView2Samples/SampleApps/WV2DeploymentVSInstallerSample/README.md](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentVSInstallerSample#readme)


**下载的存储库具有更长的根目录名称**

如果将存储库下载为 (文件) `.zip` ，则根目录名称已 `-master` 追加。  若要将存储库的名称 `WebView2Samples` 与 () ，您可以重命名根目录。


目录中特定于 `GettingStartedGuides` Win32 的解决方案的路径为：

*  如果下载了存储库： 
   * `WebView2Samples-master/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln`

*  如果克隆了存储库： 
   * `WebView2Samples/GettingStartedGuides/Win32_GettingStarted/WebView2GettingStarted.sln`


目录中的主多项目 Win32 `SampleApps` 解决方案路径为：

*  如果下载了存储库： 
   * `WebView2Samples-master/SampleApps/WebView2Samples.sln`

*  如果克隆了存储库： 
   * `WebView2Samples/SampleApps/WebView2Samples.sln`
