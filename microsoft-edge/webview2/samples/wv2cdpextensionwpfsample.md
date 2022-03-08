---
title: WebView2 示例：WPF 应用中的 Chrome DevTools 协议扩展
description: 此 WebView2 示例演示如何使用 WebView2 CDP 扩展在 WPF 应用中使用 DevTools 协议。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: 4c37991ec79df87d8b4d7fa644730c749eae25d2
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433434"
---
# <a name="webview2-sample-chrome-devtools-protocol-extension-in-a-wpf-app"></a>WebView2 示例：WPF 应用中的 Chrome DevTools 协议扩展

此 WebView2 示例演示如何使用 WebView2 CDP 扩展在 WPF 应用中使用 Chrome DevTools 协议。

&amp; 目录 .sln：**WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln**。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述

当前页面上的步骤是通用步骤。  请参阅自述文件部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. 在单独的窗口或选项卡中，在 [wV2CDPExtensionWPFSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample#readme) GitHub：自述文件上读取此项目呈现的 README.md 文件。  然后返回到此页面并继续以下步骤。

   * [自述>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample#prerequisites)

   * [自述>生成 WebView2 WPF 浏览器](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample#build-the-webview2-wpf-browser)

   还可以在 README.md 中 (呈现) 文件Visual Studio。  在 **"文件管理器**"Visual Studio >"解决方案资源管理器"中，打开文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WV2CDPExtensionWPFSample/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-master/SampleApps/WV2CDPExtensionWPFSample/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装Visual Studio

Microsoft Visual Studio是必填项。  Microsoft Visual Studio不支持代码。

1. 如果Visual Studio (尚未安装) 版本，请参阅设置 _WebView2_ 的开发人员环境中中的安装 Visual Studio。[](../how-to/machine-setup.md#install-visual-studio)  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装预览频道Microsoft Edge

1.  如果尚未在单独的窗口或选项卡中安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅为 _WebView2_ 设置开发环境中的安装 [Microsoft Edge](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge) 预览频道。  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请下载存储库 `WebView2Sample` 或将存储库克隆到本地驱动器。  在单独的窗口或选项卡中，请参阅设置 WebView2 的开发人员环境中的下载 [WebView2Samples](../how-to/machine-setup.md#download-the-webview2samples-repo) _存储库_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
## <a name="step-5---open-sln-in-visual-studio"></a>步骤 5 - 在"文件"中打开Visual Studio

1. 在本地驱动器上，在 Visual Studio `.sln` 中的 目录中打开文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-master/SampleApps/WV2CDPExtensionWPFSample/WV2CDPExtensionWPFSample.sln`


<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 安装工作负载（如果提示）

1. 如果系统提示，请Visual Studio所有请求的工作负荷。  在单独的窗口或选项卡中，请参阅[](../how-to/machine-setup.md#install-visual-studio-workloads)为 _WebView2 Visual Studio开发人员环境"中的安装新工作负载_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。

   **WV2CDPExtensionWPFSample** 项目将在Visual Studio：

   ![WV2CDPExtensionWPFSample 示例在解决方案Visual Studio中打开。](media/wv2cdpextensionwpfsample-opened.png)


<!-- ====================================================================== -->
## <a name="step-7---install-or-update-the-webview2-sdk"></a>步骤 7 - 安装或更新 WebView2 SDK

1. 在项目节点（而不是解决方案资源管理器 (解决方案节点）) WebView2 SDK。  在单独的窗口或选项卡中，请参阅为 [WebView2](../how-to/machine-setup.md#install-the-webview2-sdk) 设置开发环境 _中的安装 WebView2 SDK_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。

   在项目顶部Visual Studio设置生成目标，如下所示：


<!-- ====================================================================== -->
## <a name="step-8---build-the-project"></a>步骤 8 - 生成项目

1. 在" **解决方案配置"** 下拉列表中，选择" **调试"** 或"发布 **"**。

1. 在" **解决方案平台"** 下拉列表中，选择" **任何 CPU"**。

1. 在 **"解决方案资源管理器**"中，右键单击 **"WV2CDPExtensionWPFSample** "项目，然后选择"生成 **"**。

   这将生成项目文件 `WV2CDPExtensionWPFSample.csproj`。<!--readme is missing "WPF" there, vs dir listing-->


<!-- ====================================================================== -->
## <a name="step-9---run-debug-the-project"></a>步骤 9 - () 调试项目

1. In Visual Studio， select **DebugStart** >  **Debugging** (`F5`) .

   示例应用窗口将打开：

   ![WV2CDPExtensionWPFSample 示例应用程序。](media/wv2cdpextensionwpfsample-app-running.png)

1. 使用示例应用;请参阅 [WV2CDPExtensionWPFSample 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2CDPExtensionWPFSample#readme)。

1. 在Visual Studio中，选择 **"调试** > **""停止调试"**。  Visual Studio关闭应用。


<!-- ====================================================================== -->
## <a name="step-10---inspect-the-code"></a>步骤 10 - 检查代码

1. 在Visual Studio编辑器中，检查代码：

   ![WV2CDPExtensionWPFSample 项目中Visual Studio。](media/wv2cdpextensionwpfsample-code.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WinUI 2 (UWP) 应用中的 WebView2 入门（公共预览版）](../get-started/winui2.md)
