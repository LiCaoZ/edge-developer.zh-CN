---
title: WPF 示例应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WPF .NET 应用中实现 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 6e55bcb8a72769e4d4c92091925fecbcfbd1fc5b
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668494"
---
# <a name="wpf-sample-app"></a>WPF 示例应用

此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WPF .NET 应用中实现 Web 浏览器。

Directory &amp; .sln： **WebView2WpfBrowser/WebView2WpfBrowser.sln**。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述文件

当前页面上的步骤是通用的。  请参阅 README 部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. 在单独的窗口或选项卡中，在 GitHub： [WebView2WpfBrowser 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser#readme)中读取此项目的呈现 README.md 文件。  然后返回到此页面，并继续执行以下步骤。

   * [自述文件>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser#prerequisites)

   * [自述文件>生成 WebView2 WPF 浏览器](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser#build-the-webview2-wpf-browser)

   还可以在 Visual Studio 中查看 README.md 源文件 (未呈现的) 。  在**文件管理器**或 Visual Studio > 解决方案资源管理器中，打开该文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WpfBrowser/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WpfBrowser/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装 Visual Studio

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

1. 如果 Visual Studio (尚未安装所需的最低版本) ，请在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装 Microsoft Edge 的预览频道

1.如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请将存储库下载或克隆 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-5---open-sln-in-visual-studio"></a>步骤 5 - 在 Visual Studio 中打开 .sln

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中的目录中打开该文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WpfBrowser/WebView2WpfBrowser.sln`


<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 如果出现提示，请安装工作负载

1. 如果出现提示，请安装请求的任何 Visual Studio 工作负载。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   **WebView2WpfBrowser** 项目在 Visual Studio 中打开：

   ![Visual Studio 中的 WebView2WpfBrowser 项目。](media/webview2wpfbrowser-project-opened.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="step-7---install-or-update-the-webview2-sdk"></a>步骤 7 - 安装或更新 WebView2 SDK

1. 在项目节点上安装或更新 WebView2 SDK， (不是解决方案资源管理器中) 的解决方案节点。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-8---build-the-project"></a>步骤 8 - 生成项目

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WpfBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `WebView2WpfBrowser.csproj`。


<!-- ====================================================================== -->
## <a name="step-9---run-debug-the-project"></a>步骤 9 -) 项目运行 (调试

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WebView2WpfBrowser 示例应用。](media/webview2wpfbrowser-sample-app.png)

1. 使用示例应用;请参阅 [WebView2WpfBrowser 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser#readme)。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-10---inspect-the-code"></a>步骤 10 - 检查代码

1. 在 Visual Studio 代码编辑器中，检查代码：

   ![Visual Studio 中的 WebView2WpfBrowser 项目的代码。](media/webview2wpfbrowser-code.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WPF 应用中的 WebView2 入门](../get-started/wpf.md)
