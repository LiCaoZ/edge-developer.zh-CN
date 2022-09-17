---
title: WPF 示例应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WPF .NET 应用中实现 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 17fcbd1606becc20df3ff8d4f15221f0b48ac7c3
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754817"
---
# <a name="wpf-sample-app"></a>WPF 示例应用

<!-- todo: paste/merge into here from corresp Readme https://github.com/MicrosoftEdge/WebView2Samples/pull/140/files -->

此示例 **WebView2WpfBrowser** 是一个 WPF .NET 应用，演示如何嵌入 WebView2 控件并使用 WebView2 API 实现 Web 浏览器。

*  示例名称： **WebView2WpfBrowser**
*  存储库目录： [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser)
*  解决方案文件： **WebView2WpfBrowser.sln**

此示例是作为 WPF Visual Studio 2019 项目生成的。  它在 WebView2 环境中使用 C# 和 HTML/CSS/JavaScript。

此示例展示了一系列 WebView2 的事件处理程序和 API 方法，这些方法允许 WPF 应用程序直接与 WebView 交互，反之亦然。

![WebView2WpfBrowser 示例应用](media/webview2wpfbrowser-sample-app.png)

**WebView2WpfBrowser** 示例应用包含以下菜单，其中包含许多有用的菜单：
*  **文件**
*  **视图**
*  **“设置”**
*  **方案**

如果这是你第一次使用 WebView2，我们建议先遵循入门教程，该教程介绍如何创建 WebView2 并演练一些基本的 WebView2 功能。  请参阅 [WPF 应用中的 WebView2 入](../get-started/wpf.md)门。

有关 WebView2 中的事件和 API 处理程序的详细信息， [请参阅 WebView2 API 参考](/microsoft-edge/webview2/webview2-api-reference)。


<!-- ====================================================================== -->
## <a name="step-1---install-a-preview-channel-of-microsoft-edge"></a>步骤 1 - 安装 Microsoft Edge 的预览频道

1. 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio-2019-with-net-support"></a>步骤 2 - 使用 .NET 支持安装 Visual Studio 2019

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

1. 如果 Visual Studio 2019 (尚未安装具有 .NET 支持的最低必需版本) ，请参阅在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤在 .NET 支持下安装 Visual Studio 2019，然后返回到此页面并继续执行以下步骤。
<!-- could show selecting .NET support -->


<!-- ====================================================================== -->
## <a name="step-3---clone-or-download-the-webview2samples-repo"></a>步骤 3 - 克隆或下载 WebView2Samples 存储库

1. 如果尚未完成，请将存储库克隆或下载 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-4---open-the-solution-in-visual-studio"></a>步骤 4 - 在 Visual Studio 中打开解决方案

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中的目录中打开该文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`


<!-- ====================================================================== -->
## <a name="step-5---install-workloads-if-prompted"></a>步骤 5 - 如果出现提示，请安装工作负载

1. 如果出现提示，请安装请求的任何 Visual Studio 工作负载。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   **WebView2WpfBrowser** 项目在 Visual Studio 中打开：

   ![Visual Studio 中的 WebView2WpfBrowser 项目](media/webview2wpfbrowser-project-opened.png)


<!-- ====================================================================== -->
## <a name="step-6---build-and-run-the-project"></a>步骤 6 - 生成并运行项目

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WpfBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `WebView2WpfBrowser.csproj`。

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WebView2WpfBrowser 示例应用](media/webview2wpfbrowser-sample-app.png)

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-7---update-the-webview2-sdk"></a>步骤 7 - 更新 WebView2 SDK

1. 更新项目节点上的预发行 WebView2 SDK (解决方案资源管理器中) 的解决方案节点。  安装 WebView2 SDK 的最新预发行版，以便可以尝试使用最新功能。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

1. 再次生成并运行项目。


<!-- ====================================================================== -->
## <a name="step-8---explore-the-menus-and-inspect-the-code"></a>步骤 8 - 浏览菜单并检查代码

1. 浏览 **WebView2WpfBrowser** 示例应用的菜单，其中包含许多有用的菜单：
   *  **文件**
   *  **视图**
   *  **“设置”**
   *  **方案**
   
1. 在 Visual Studio 代码编辑器中，检查代码：

   ![Visual Studio 中的 WebView2WpfBrowser 项目的代码](media/webview2wpfbrowser-code.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WPF 应用中的 WebView2 入门](../get-started/wpf.md)
