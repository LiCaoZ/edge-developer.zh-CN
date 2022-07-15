---
title: 用于部署 WebView2 运行时的 WiX 燃烧捆绑包
description: 演示如何使用 WiX 燃烧捆绑包部署 WebView2 运行时的 WebView2 示例。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: dcaf46819bffe9bbc5c21401c6cb9a132cfed068
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668473"
---
# <a name="wix-burn-bundle-to-deploy-the-webview2-runtime"></a>用于部署 WebView2 运行时的 WiX 燃烧捆绑包

这是一个 WebView2 示例，演示如何使用 WiX 燃烧捆绑包部署 WebView2 运行时。

目录& .proj： **WV2DeploymentWiXBurnBundleSample/WV2DeploymentWiXBurnBundleSample.wixproj** (no .sln) 


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述文件

当前页面上的步骤是通用的。  请参阅 README 部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. **README** - 在单独的窗口或选项卡中，在 GitHub： [WV2DeploymentWiXBurnBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample#readme) 读取此项目的呈现 README.md 文件。  然后返回到此页面，并继续执行以下步骤。

   * [自述文件>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample#prerequisites)

   * [自述>生成步骤](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample#build-steps)

   还可以在 Visual Studio 中查看 README.md 源文件 (未呈现的) 。  在**文件管理器**或 Visual Studio > 解决方案资源管理器中，打开该文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-main/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装 Visual Studio

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

1. 如果 Visual Studio (尚未安装所需的最低版本) ，请在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装 Microsoft Edge 的预览频道

1. 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请将存储库下载或克隆 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
<!-- ## Step 5 - Open .sln in Visual Studio -->

<!-- 1. On your local drive, open the `.sln` file in Visual Studio, in the directory:

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WV2DeploymentWiXBurnBundleSample/WV2DeploymentWiXBurnBundleSample.sln`

   or:

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WV2DeploymentWiXBurnBundleSample/WV2DeploymentWiXBurnBundleSample.sln` -->


<!-- ====================================================================== -->
<!-- 1. **Visual Studio workloads** - If prompted, install any Visual Studio workloads that are requested.  In a separate window or tab, see [Install Visual Studio workloads](../how-to/machine-setup.md#install-visual-studio-workloads) in _Set up your Dev environment for WebView2_.  Follow the steps in that section, and then return to this page and continue below. -->


<!-- ====================================================================== -->
   <!-- Solution Explorer shows the **WV2DeploymentWiXBurnBundleSample** project. -->

   <!-- ![The WV2DeploymentWiXBurnBundleSample sample opened in Visual Studio in Solution Explorer.](media/wv2deploymentwiXburnbundlesample-in-solution-explorer.png) -->
   <!--todo: create png-->


<!-- ====================================================================== -->
## <a name="step-5---install-or-update-the-webview2-sdk"></a>步骤 5 - 安装或更新 WebView2 SDK

1. 如果需要，请在项目节点上) WebView2 SDK 安装 (或更新， (解决方案资源管理器中) 解决方案节点。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  可以按照以下步骤确定是否为项目安装了 WebView2 SDK。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- 1. In Visual Studio, select **Debug** > **Start Debugging** (`F5`). -->

   <!-- The sample app window opens. -->

<!-- 1. In the sample app window, use the sample app.  In the Visual Studio code editor, inspect the code; see [README file for WV2DeploymentWiXBurnBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample#readme). -->

<!-- 1. Close the sample app window. -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

[WV2DeploymentWiXBurnBundleSample 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample#readme)
