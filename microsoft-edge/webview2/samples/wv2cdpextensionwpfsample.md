---
title: 具有 CDP 扩展的 WPF 示例应用
description: 此 WebView2 示例演示如何使用 WebView2 CDP 扩展在 WPF 应用中使用 DevTools 协议。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 07/20/2022
ms.openlocfilehash: da8978edd08ca11b90a7147c65f15b6c36320f94
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754380"
---
# <a name="wpf-sample-app-with-cdp-extension"></a>具有 CDP 扩展的 WPF 示例应用

<!-- todo: after copying the "summary / which project/ which lang" info to top of each Sample .md file, merge into here the Readme sections: Prereq, Build. -->
<!-- todo: global: like readmes PR in samples repo, add a tangible representative "finished result" screenshot at top of each sample or getstart. -->

此 WebView2 示例演示如何使用 WebView2 CDP 扩展在 WPF 应用中使用 Chrome DevTools 协议。

*  示例名称： **WV2CDPExtensionWPFSample**
*  存储库目录： [WV2CDPExtensionWPFSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2CDPExtensionWPFSample)
*  解决方案文件： **WV2CDPExtensionWPFSample.sln**

此示例 **WV2CDPExtensionWPFSample** 是使用 WebView2 CDP 扩展 (**Microsoft.Web.WebView.DevToolsProtocolExtension** NuGet 包) 生成的。  此示例对 WebView2 中的对象调用 Chrome DevTools 协议 (CDP) 方法 `DevToolsProtocolHelper` 。

此示例是作为 WPF Visual Studio 2019 项目生成的。  它在 WebView2 环境中使用 C#。

![WV2CDPExtensionWPFSample 示例应用](media/wv2cdpextensionwpfsample-app-running.png)

**“DevTools 命令**”菜单：

![WV2CDPExtensionWPFSample 应用的 DevTools 命令菜单](./wv2cdpextensionwpfsample-images/devtools-commands-menu.png)

**“DevTools 事件**”菜单：

![WV2CDPExtensionWPFSample 应用的 DevTools 事件菜单](./wv2cdpextensionwpfsample-images/devtools-events-menu.png)


如果这是你第一次使用 WebView2，建议先遵循 [WPF 应用教程中的 WebView2 入](../get-started/wpf.md) 门教程。  本教程逐步讲解如何创建 WebView2 并添加一些基本的 WebView2 功能。


<!-- ====================================================================== -->
## <a name="step-1---install-a-preview-channel-of-microsoft-edge"></a>步骤 1 - 安装 Microsoft Edge 的预览频道

<!-- readme said "Prerequisites: Microsoft Edge (Chromium) installed on a supported OS. Currently we recommend the latest version of the Edge Canary channel." -->

建议使用最新版本的 Canary 通道。

1.  如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio-with-net-support"></a>步骤 2 - 使用 .NET 支持安装 Visual Studio

<!-- readme said "Prerequisites: Visual Studio with .NET support installed." -->
需要具有 .NET 支持) 的 Microsoft Visual Studio (。  此示例不支持 Microsoft Visual Studio Code。

1. 如果尚未安装具有 .NET 支持的 Visual Studio (所需的最低版本) ，请在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---clone-or-download-the-webview2samples-repo"></a>步骤 3 - 克隆或下载 WebView2Samples 存储库

1. 如果尚未完成，请将存储库克隆或下载 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-4---open-the-solution-in-visual-studio"></a>步骤 4 - 在 Visual Studio 中打开解决方案

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中的目录中打开该文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln`

如果要使用 Visual Studio 2017，请在 Visual Studio 中更改项目的平台工具集， **>常规>平台工具集>配置属性**。
若要使用 Visual Studio 2017，可能需要安装最近的 Windows SDK。


<!-- ====================================================================== -->
## <a name="step-5---install-workloads-if-prompted"></a>步骤 5 - 如果出现提示，请安装工作负载

1. 如果出现提示，请安装请求的任何 Visual Studio 工作负载。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   **WV2CDPExtensionWPFSample** 项目将在 Visual Studio 中打开：

   ![在 Visual Studio 中打开的 WV2CDPExtensionWPFSample 示例解决方案资源管理器](media/wv2cdpextensionwpfsample-opened.png)


<!-- ====================================================================== -->
## <a name="step-6---build-and-run-the-project-with-installed-version-of-sdks"></a>步骤 6 - 使用已安装的 SDK 版本生成并运行项目

WebView2 SDK 和 WebView2 DevToolsProtocolExtension 的版本作为 NuGet 包包含在此项目中。  在后面的步骤中，你将使用 Visual Studio 的 NuGet 包管理器更新这些内容。<!-- Right-click the project, and then select **Manage NuGet Packages**. -->

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WV2CDPExtensionWPFSample** 项目，然后选择 **“生成**”。

<!--This builds the project file `WV2CDPExtensionWPFSample.csproj`.readme was missing "WPF" there, vs dir listing; readme said: Build the project file: _WV2CDPExtensionSample.csproj_ -->

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WV2CDPExtensionWPFSample 示例应用](media/wv2cdpextensionwpfsample-app-running.png)

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-7---update-the-webview2-sdk"></a>步骤 7 - 更新 WebView2 SDK

<!-- readme said "Prerequisites: Latest version of our WebView2 SDK, which is included in this project."  doesn't specify "release" or "prerelease" -->
1. 在解决方案资源管理器中，右键单击项目 (而不是解决方案节点) ，然后选择 **“管理 NuGet 包**”。  **NuGet 包管理器** 随即打开。

1. 单击 **“已安装**”或 **“汇报**”选项卡。

1. 选中或清除 **“包括预发行版** ”复选框。

   ![更新包](./wv2cdpextensionwpfsample-images/updating-packages.png)

   上面的屏幕截图显示了 Visual Studio 2019，它在概述 **WebView2APIsSample** 解决方案的上下文中显示此示例，而不是当前的独立解决方案。  在此屏幕截图中，存储库具有 WebView2 SDK 的发布版本，并且提供了较新的 SDK 版本和预发行版本。

1. 如果列出了较新版本的 **Microsoft.Web.WebView2** SDK，请单击 **“更新”** 按钮。  预发行版具有“预发行版”后缀，例如 **1.0.1248 预发行版**。  预发行 SDK 允许尝试最新的 WebView2 功能和 API。

如果想要在单独的窗口或选项卡中查看有关此步骤的详细信息，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

有关详细信息，请参阅 [WebView2 SDK NuGet 包](https://aka.ms/webviewnuget)。


<!-- ====================================================================== -->
## <a name="step-8---update-the-webview2-cdp-extension"></a>步骤 8 - 更新 WebView2 CDP 扩展

此示例的先决条件是 WebView2 CDP 扩展的最新版本 (**Microsoft.Web.WebView.DevToolsProtocolExtension**) ，它包含在此项目中。  **Microsoft.Web.WebView.DevToolsProtocolExtension** 包添加了对 Chrome DevTools 协议 API 的支持。

<!-- readme said "Prerequisites: Latest release version of our WebView2 CDP Extension, which is included in this project." -->
1. 在解决方案资源管理器中，右键单击项目，然后选择 **“管理 NuGet 包**”。  **NuGet 包管理器** 随即打开。

1. 单击 **“已安装**”或 **“汇报**”选项卡。

1. 清除 **“包括预发行版** ”复选框。

   ![检查 CDP 扩展包的更新](./wv2cdpextensionwpfsample-images/cdp-extension-package.png)

1. 如果列出了较新版本的 **Microsoft.Web.WebView.DevToolsProtocolExtension** SDK，请单击 **“更新”** 按钮。

有关详细信息，请参阅 [WebView2 CDP 扩展](https://aka.ms/webviewcdpnuget)。


<!-- ====================================================================== -->
## <a name="step-9---build-and-run-the-project-with-updated-packages"></a>步骤 9 - 使用更新的包生成和运行项目

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WV2CDPExtensionWPFSample 应用](media/wv2cdpextensionwpfsample-app-running.png)

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-10---inspect-the-code"></a>步骤 10 - 检查代码

1. 在 Visual Studio 代码编辑器中，检查代码：

   ![Visual Studio 中的 WV2CDPExtensionWPFSample 项目的代码](media/wv2cdpextensionwpfsample-code.png)

   **“DevTools 命令**”菜单：

   ![“DevTools 命令”菜单](./wv2cdpextensionwpfsample-images/devtools-commands-menu.png)

   **“DevTools 事件**”菜单：

   ![“DevTools 事件”菜单](./wv2cdpextensionwpfsample-images/devtools-events-menu.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WinUI 2 (UWP) 应用中的 WebView2 入门](../get-started/winui2.md)
