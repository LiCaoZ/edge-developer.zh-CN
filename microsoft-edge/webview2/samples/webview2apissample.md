---
title: WebView2 示例：Win32 C++ 应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 向 Win32 C++ 应用添加功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: 4c231e9cb9cf8d6911acd619d2e1c2e987abc85c
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433426"
---
# <a name="webview2-sample-win32-c-app"></a>WebView2 示例：Win32 C++ 应用

此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 向 Win32 C++ 应用添加功能。

WebView2APISample 是在 Win32 本机应用程序中嵌入 WebView 的应用程序示例。 它构建为 Win32 Visual Studio项目，并使用 WebView2 环境中 C++ 和 HTML/CSS/JavaScript。

API 示例展示了一系列 WebView2 的事件处理程序和 API 方法，允许本机 Win32 应用程序直接与 WebView 交互，反之亦然。

Directory &amp; .sln： **WebView2APISample / WebView2Samples.sln (父目录) **。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述

当前页面上的步骤是通用步骤。  请参阅自述文件部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

1. 在单独的窗口或选项卡中，README.md [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) 的 GitHub：自述文件上读取此项目的呈现文件。  然后返回到此页面并继续以下步骤。

   * [自述>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#prerequisites)

   * [自述>生成 WebView2 API 示例](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#build-the-webview2-api-sample)

   还可以在 README.md 中 (呈现) 文件Visual Studio。  在 **"文件管理器**"Visual Studio >"解决方案资源管理器"中，打开文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-master/SampleApps/README.md`


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
## <a name="step-5---open-sln-in-visual-studio"></a>步骤 5 - 在"文件"中打开Visual Studio

1. 在本地驱动器上，在 Visual Studio `.sln` 中的 目录中打开文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2Samples.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-master/SampleApps/WebView2Samples.sln`


<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 安装工作负载（如果提示）

1. **Visual Studio工作负载** - 如果系统提示，Visual Studio任何请求的工作负荷。  在单独的窗口或选项卡中，请参阅[](../how-to/machine-setup.md#install-visual-studio-workloads)为 _WebView2 Visual Studio开发人员环境"中的安装新工作负载_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
## <a name="step-7---view-the-opened-project"></a>步骤 7 - 查看打开的项目

解决方案资源管理器显示多个项目，包括 **WebView2APISample** 项目：

![WebView2APISample 在Visual Studio资源管理器中打开。](media/webview2apisample-in-solution-explorer.png)


<!-- ====================================================================== -->
## <a name="step-8---install-or-update-the-prerelease-webview2-sdk"></a>步骤 8 - 安装或更新预发布 WebView2 SDK

安装或更新 _项目的预发布_ WebView2 SDK，如下所示：

1. 在"解决方案资源管理器"中，右键单击项目 (而不是其上方的解决方案节点) ，然后选择"管理NuGet**包"**。

   the **NuGet 程序包管理器** panel opens in Visual Studio.

1. 在"**NuGet 程序包管理器**中，单击"**浏览"** 选项卡。

1. 在搜索文本框的右侧，选中" **包括预发布"** 复选框。

1. 在搜索文本框中，输入 **Microsoft.Web.WebView2**。

   **Microsoft.Web.WebView2** 卡将显示在搜索结果中。

1. 单击 **搜索框下方的 Microsoft.Web.WebView2** 卡。

1. 在右侧，在" **版本** "下拉列表中，确保 **已选择"最新** 预发布"：

   ![NuGet 程序包管理器选择 WebView2 SDK 预发布。](media/webview2apisample-pkg-mgr-prerelease-webview2.png)

   _上面的图像来自另一个项目，但相似。  若要缩放，请右键> **新选项卡中的"打开图像"**。_

1. 单击" **安装** (**或更新**) 按钮。

   将显示 **"预览** 更改"对话框：

   ![WebView2 NugGet 程序包的"预览更改"对话框。](media/webview2apisample-webview2-pkg-preview-changes.png)

   _上面的图像来自另一个项目，但相似。_

1. 单击" **确定"** 按钮。

现在已为此项目安装了 WebView2 SDK。


<!-- ====================================================================== -->
## <a name="step-9---build-the-project"></a>步骤 9 - 生成项目

在项目顶部Visual Studio设置生成目标，如下所示：

1. 在" **解决方案配置"** 下拉列表中，选择" **调试"** 或"发布 **"**。

1. 在" **解决方案平台"** 下拉列表中，选择 **x86**、 **x64** 或 **ARM64**。

1. 在 **"解决方案资源管理器**"中，右键单击 **"WebView2APISample** "项目，然后选择"生成 **"**。

   ![在"解决方案资源管理器"中选择的 WebView2APISample 项目。](media/webview2apisample-project-selected.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_

   这将生成项目文件 `SampleApps/WebView2APISample/WebView2APISample.vcxproj`。


<!-- ====================================================================== -->
## <a name="step-10---run-debug-the-project"></a>步骤 10 - () 调试项目

1. 选择 **"调试** > **""开始调试** (`F5`) "。  

   疑难解答：如果跳过生成步骤并立即选择"**** 调试""开始调试 () "无法启动程序：找不到指定路径"：**** `F5` > 

   ![对话框：无法启动程序：找不到指定的路径。](media/webview2apisample-unable-to-start-program-cannot-find-path.png)

   若要解决此问题：在 **"解决方案资源管理器**"中，右键单击 **"WebView2APISample** "项目，然后选择"生成 **"**。

   **WebView2APISample** 应用窗口将打开：

   ![WebView2APISample 应用窗口。](media/webview2apisample-app-window.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_

1. 使用示例应用。  请参阅 [WebView2 API](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme) 示例的自述文件

1. 在Visual Studio中，选择 **"调试** > **""停止调试"**。  Visual Studio关闭应用。


<!-- ====================================================================== -->
## <a name="step-11---inspect-the-code"></a>步骤 11 - 检查代码

1. 在Visual Studio编辑器中，检查代码。


<!--
Note: The `.sln` file is not in the sample repo directory that contains this sample's [README.md file](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#readme), or the equivalent local filesystem directory.  Instead, the `.sln` file for this sample is in the parent directory that corresponds to the [SampleApps](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps) repo directory.
-->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Win32 应用中的 WebView2 入门](../get-started/win32.md)
