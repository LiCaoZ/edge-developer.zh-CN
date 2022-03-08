---
title: WebView2 示例：部署运行时的 WiX 刻录捆绑包
description: 一个 WebView2 示例，演示如何使用 WiX 刻录捆绑包部署 WebView2 运行时。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: 0e35df16202d607da91d3398a91a1cf0dd2a5994
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433491"
---
# <a name="webview2-sample-wix-burn-bundle-to-deploy-runtime"></a>WebView2 示例：部署运行时的 WiX 刻录捆绑包

这是一个 WebView2 示例，演示如何使用 WiX 消耗捆绑包部署 WebView2 运行时。

Directory& .proj： **WV2DeploymentWiXBundleSample/WV2DeploymentWiXBundleSample.wixproj** (no .sln) 


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述

当前页面上的步骤是通用步骤。  请参阅自述文件部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. **自**述文件 - 在单独的窗口或选项卡中，在 GitHub：[WV2DeploymentWiXBundleSample 的自](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#readme)述文件上读取此项目的呈现 README.md 文件。  然后返回到此页面并继续以下步骤。

   * [自述>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#prerequisites)

   * [自述>生成步骤](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#build-steps)

   还可以在 README.md 中 (呈现) 文件Visual Studio。  在 **"文件管理器**"Visual Studio >"解决方案资源管理器"中，打开文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-master/SampleApps/WV2DeploymentWiXBurnBundleSample/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装Visual Studio

Microsoft Visual Studio是必填项。  Microsoft Visual Studio不支持代码。

1. 如果Visual Studio (尚未安装) 版本，请参阅设置 _WebView2_ 的开发人员环境中中的安装 Visual Studio。[](../how-to/machine-setup.md#install-visual-studio)  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装预览频道Microsoft Edge

1. 如果尚未在单独的窗口或选项卡中安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅为 _WebView2_ 设置开发环境中的安装 [Microsoft Edge](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge) 预览频道。  按照该部分中的步骤操作，然后返回此页面并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请下载存储库 `WebView2Sample` 或将存储库克隆到本地驱动器。  在单独的窗口或选项卡中，请参阅设置 WebView2 的开发人员环境中的下载 [WebView2Samples](../how-to/machine-setup.md#download-the-webview2samples-repo) _存储库_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
<!-- ## Step 5 - Open .sln in Visual Studio -->

<!-- 1. On your local drive, open the `.sln` file in Visual Studio, in the directory:

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WV2DeploymentWiXBurnBundleSample/WV2DeploymentWiXBurnBundleSample.sln`

   or:

   *  `<your-repos-directory>/WebView2Samples-master/SampleApps/WV2DeploymentWiXBurnBundleSample/WV2DeploymentWiXBurnBundleSample.sln` -->


<!-- ====================================================================== -->
<!-- 1. **Visual Studio workloads** - If prompted, install any Visual Studio workloads that are requested.  In a separate window or tab, see [Install Visual Studio workloads](../how-to/machine-setup.md#install-visual-studio-workloads) in _Set up your Dev environment for WebView2_.  Follow the steps in that section, and then return to this page and continue below. -->


<!-- ====================================================================== -->
   <!-- Solution Explorer shows the **WV2DeploymentWiXBurnBundleSample** project. -->

   <!-- ![The WV2DeploymentWiXBurnBundleSample sample opened in Visual Studio in Solution Explorer.](media/wv2deploymentwiXburnbundlesample-in-solution-explorer.png) -->
   <!--todo: create png-->


<!-- ====================================================================== -->
## <a name="step-5---install-or-update-the-webview2-sdk"></a>步骤 5 - 安装或更新 WebView2 SDK

1. 如果需要，请 (WebView2 SDK) WebView2 SDK， ("解决方案资源管理器"中的解决方案) 节点。  在单独的窗口或选项卡中，请参阅为 [WebView2](../how-to/machine-setup.md#install-the-webview2-sdk) 设置开发环境 _中的安装 WebView2 SDK_。  可以按照以下步骤确定是否为项目安装了 WebView2 SDK。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- 1. In Visual Studio, select **Debug** > **Start Debugging** (`F5`). -->

   <!-- The sample app window opens. -->

<!-- 1. In the sample app window, use the sample app.  In the Visual Studio code editor, inspect the code; see [README file for WV2DeploymentWiXBurnBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#readme). -->

<!-- 1. Close the sample app window. -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

[WV2DeploymentWiXBundleSample 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WV2DeploymentWiXBurnBundleSample#readme)