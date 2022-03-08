---
title: WebView2 示例：WPF .NET 浏览器应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WPF .NET 应用中实现 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: 634ebdd8fd943bf98fd9beb25a6931943d791b2f
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433653"
---
# <a name="webview2-sample-wpf-net-browser-app"></a>WebView2 示例：WPF .NET 浏览器应用

此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WPF .NET 应用中实现 Web 浏览器。

&amp; 目录 .sln：**WebView2WpfBrowser/WebView2WpfBrowser.sln**。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述

当前页面上的步骤是通用步骤。  请参阅自述文件部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. 在单独的窗口或选项卡中，README.md [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser#readme) 的 GitHub：自述文件上读取此项目的呈现文件。  然后返回到此页面并继续以下步骤。

   * [自述>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser#prerequisites)

   * [自述>生成 WebView2 WPF 浏览器](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser#build-the-webview2-wpf-browser)

   还可以在 README.md 中 (呈现) 文件Visual Studio。  在 **"文件管理器**"Visual Studio >"解决方案资源管理器"中，打开文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WpfBrowser/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-master/SampleApps/WebView2WpfBrowser/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装Visual Studio

Microsoft Visual Studio是必填项。  Microsoft Visual Studio不支持代码。

1. 如果Visual Studio (尚未安装) 版本，请参阅设置 _WebView2_ 的开发人员环境中中的安装 Visual Studio。[](../how-to/machine-setup.md#install-visual-studio)  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装预览频道Microsoft Edge

1.如果尚未在单独的窗口或选项卡中安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅为 _WebView2_ 设置开发环境中的安装 [Microsoft Edge](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge) 预览频道。  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请下载存储库 `WebView2Sample` 或将存储库克隆到本地驱动器。  在单独的窗口或选项卡中，请参阅设置 WebView2 的开发人员环境中的下载 [WebView2Samples](../how-to/machine-setup.md#download-the-webview2samples-repo) _存储库_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
## <a name="step-5---open-sln-in-visual-studio"></a>步骤 5 - 在"文件"中打开Visual Studio

1. 在本地驱动器上，在 Visual Studio `.sln` 中的 目录中打开文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-master/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`


<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 安装工作负载（如果提示）

1. 如果系统提示，请Visual Studio所有请求的工作负荷。  在单独的窗口或选项卡中，请参阅[](../how-to/machine-setup.md#install-visual-studio-workloads)为 _WebView2 Visual Studio开发人员环境"中的安装新工作负载_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。

   **WebView2WpfBrowser** 项目将在以下Visual Studio：

   ![WebView2WpfBrowser 项目中Visual Studio。](media/webview2wpfbrowser-project-opened.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_


<!-- ====================================================================== -->
## <a name="step-7---install-or-update-the-webview2-sdk"></a>步骤 7 - 安装或更新 WebView2 SDK

1. 在项目节点（而不是解决方案资源管理器 (解决方案节点）) WebView2 SDK。  在单独的窗口或选项卡中，请参阅为 [WebView2](../how-to/machine-setup.md#install-the-webview2-sdk) 设置开发环境 _中的安装 WebView2 SDK_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
## <a name="step-8---build-the-project"></a>步骤 8 - 生成项目

在项目顶部Visual Studio设置生成目标，如下所示：

1. 在" **解决方案配置"** 下拉列表中，选择" **调试"** 或"发布 **"**。

1. 在" **解决方案平台"** 下拉列表中，选择" **任何 CPU"**。

1. 在 **"解决方案资源管理器**"中，右键单击 **"WebView2WpfBrowser** "项目，然后选择"生成 **"**。

   这将生成项目文件 `WebView2WpfBrowser.csproj`。


<!-- ====================================================================== -->
## <a name="step-9---run-debug-the-project"></a>步骤 9 - () 调试项目

1. In Visual Studio， select **DebugStart** >  **Debugging** (`F5`) .

   示例应用窗口将打开：

   ![WebView2WpfBrowser 示例应用。](media/webview2wpfbrowser-sample-app.png)

1. 使用示例应用;请参阅 [WebView2WpfBrowser 的](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser#readme)自述文件。

1. 在Visual Studio中，选择 **"调试** > **""停止调试"**。  Visual Studio关闭应用。


<!-- ====================================================================== -->
## <a name="step-10---inspect-the-code"></a>步骤 10 - 检查代码

1. 在Visual Studio编辑器中，检查代码：

   ![WebView2WpfBrowser 项目中Visual Studio。](media/webview2wpfbrowser-code.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WPF 应用中的 WebView2 入门](../get-started/wpf.md)
