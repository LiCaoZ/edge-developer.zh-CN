---
title: 具有 Visual Composition 的 Win32 示例应用
description: 此 WebView2 示例演示如何创建在 Win32 本机应用程序中嵌入 WebView2 控件的应用程序。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 06/14/2022
ms.openlocfilehash: 9e6f28118eafa1d80062fed017b63bfa3ce91408
ms.sourcegitcommit: 43f79138241aa7906f6631759aa0a2165e0e8ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2022
ms.locfileid: "12668550"
---
# <a name="win32-sample-app-with-visual-composition"></a>具有 Visual Composition 的 Win32 示例应用

此 WebView2 示例演示如何创建在 Win32 本机应用程序中嵌入 WebView2 控件的应用程序。

它构建为 Win32 Visual Studio 2019 项目，在 WebView2 环境中同时使用 C++ 和 HTML/CSS/JavaScript。

它还使用Windows 运行时组合 API (也称为视觉对象层) ，以利用 Windows UI 功能，在 C++ Win32 应用程序中创建更好的外观、感觉和功能。

&amp; `.sln`目录：**WebView2SampleWinComp/WebView2SampleWinComp.sln**。


**若要使用此示例 (常规用途步骤) ：**

当前页面上的步骤是通用的。  请参阅 README 部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述文件

1. 在单独的窗口或选项卡中，在 GitHub： [WebView2SampleWinComp 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2SampleWinComp#readme)中读取此项目的呈现 README.md 文件。  然后返回到此页面，并继续执行以下步骤。

   * [自述文件>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2SampleWinComp#prerequisites)

   * [自述文件>生成 WebView2 示例 WinComp](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2SampleWinComp#build-the-webview2-sample-wincomp)

   还可以在 Visual Studio 中查看 README.md 源文件 (未呈现的) 。  在**文件管理器**或 Visual Studio > 解决方案资源管理器中，打开该文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WebView2SampleWinComp/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2SampleWinComp/README.md`


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
## <a name="step-5---open-the-solution-and-set-the-windows-sdk-target"></a>步骤 5 - 打开解决方案并设置 Windows SDK 目标

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中的目录中打开该文件：

   * `<your-repos-directory>/WebView2Samples/SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.sln`

   或者：

   * `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.sln`

   可能会打开“ **查看解决方案操作”** 对话框，提示已安装 Windows SDK 的项目重定向到：

   ![“查看解决方案操作”对话框。](webview2samplewincomp-images/review-solution-actions.png)

1. 在 **Windows SDK 版本** 下拉列表中，选择 **10.0.20348.0** 或更高版本，或 **10.0.18362.0** 或更早版本;请勿选择 **10.0.19041.0**。  然后单击 **“确定”** 按钮。  如果这些版本不可用，请执行以下“安装 Windows SDK”部分中的步骤。  否则，请跳到下面的部分。

如果解决方案已打开，可按如下所示更改目标：

*  在**解决方案资源管理器**中，右键单击 **WebView2SampleWinComp** 项目 (解决方案) ，然后单击 **“重定向项目**”。


<!-- ====================================================================== -->
## <a name="step-6---install-the-windows-sdk"></a>步骤 6 - 安装 Windows SDK

默认情况下，此示例应用使用已安装的最新 Window 10 SDK 版本。  Windows 10 SDK 版本 2004 (10.0 存在问题。**19041.0**) ，将阻止此示例应用生成。  如果遇到此问题，请安装 (并将此项目重新定向为使用) 更高版本，例如 Windows 10 SDK 版本 2104 (10.0。**20348.0**) 或更早版本，例如 10.0。**18362.1**.  

若要安装Windows 10 SDK：

1. 转到 [Windows SDK 和仿真器存档](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/)。

1. 在以下行之一中，单击 **“安装 SDK** ”链接：
   *  Windows 10 SDK 版本 2104 (10.0.20348.0)  (或更高版本) 
   *  Windows 10 SDK 版本 1903 (10.0.18362.1) 

   特定于版本的 `winsdksetup.exe` 副本将下载到目录 `Downloads` 。

1. `Downloads`在目录中，打开刚下载的`winsdksetup.exe`副本。

1. **Windows SDK 安装**窗口随即打开：

   ![Windows SDK 设置。](webview2samplewincomp-images/windows-sdk-setup.png)

1. 单击“ **下一步** ”按钮，然后按照提示进行操作。  可以接受默认值。  安装结束时，将显示所选版本的 Windows SDK 欢迎屏幕：

   ![欢迎使用 Windows SDK。](webview2samplewincomp-images/welcome-winsdk.png)

1. 单击**关闭**按钮。

执行上一步“打开解决方案并设置 Windows SDK 目标”。  或者，如果解决方案已打开，**请在解决方案资源管理器**中右键单击 **WebView2SampleWinComp** 项目 (不是解决方案) ，然后单击 **“重定向项目**”。


<!-- ====================================================================== -->
## <a name="step-7---install-workloads-if-prompted"></a>步骤 7 - 如果出现提示，请安装工作负载

*  如果出现提示，请安装请求的任何 Visual Studio 工作负载。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-8---view-the-opened-project"></a>步骤 8 - 查看打开的项目

该项目在 Visual Studio 中打开，在 解决方案资源管理器 中显示 **WebView2SampleWinComp** 项目：

![Visual Studio 中的 WebView2SampleWinComp 项目。](webview2samplewincomp-images/project-in-sln-explorer.png)

_若要缩放屏幕截图，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="step-9---install-or-update-the-webview2-prerelease-sdk"></a>步骤 9 - 安装或更新 WebView2 预发行版 SDK

此步骤可选。  该示例预装了 WebView2 预发行版 SDK 的版本。

1. 在**解决方案资源管理器**中，右键单击 **WebView2SampleWinComp** 项目 (不是解决方案节点) ，然后选择 **“管理 NuGet 包**”。  “ **NuGet 包管理器** ”选项卡随即打开。

1. 选中 **“包括预发行版** ”复选框。

1. 单击**更新**选项卡。

1. 如果列出了 **较新的 Microsoft.Web.WebView2** SDK 预发行版，请单击 **“更新”** 按钮。  预发行版具有“预发行版”后缀，例如 **1.0.1248 预发行版**。  如果想要在单独的窗口或选项卡中查看有关此步骤的详细信息，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

![最初打开 WebView2SampleWinComp 解决方案后，NuGet 包管理器的“更新”选项卡。](webview2samplewincomp-images/updates-tab-initial-state.png)

_若要缩放屏幕截图，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="step-10---install-or-update-the-windows-implementation-libraries-wil"></a>步骤 10 - 安装或更新 WINDOWS 实现库 (WIL) 

此步骤可选。  该示例预装了 WINDOWS 实现库的版本 (WIL) 。

1. 在**解决方案资源管理器**中，右键单击 **WebView2SampleWinComp** 项目 (不是解决方案节点) ，然后选择 **“管理 NuGet 包**”。  “ **NuGet 包管理器** ”选项卡随即打开。

1. 在项目节点上安装或更新 Windows 实现库 (WIL) ， () 解决方案资源管理器中的解决方案节点。  如果 WebView2 预发行版 SDK 已安装，并且更新后的预发行版已在“更新”选项卡中列出，请更新它。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-11---build-the-project"></a>步骤 11 - 生成项目

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **x86**、 **x64** 或 **ARM64**。

1. 在**解决方案资源管理器**中，右键单击 **WebView2SampleWinComp** 项目，然后选择 **“生成**”。

   这会生成项目文件 `SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.vcxproj`。


<!-- ====================================================================== -->
## <a name="step-12---run-debug-the-project"></a>步骤 12 - 运行 (调试) 项目

1. 在 Visual Studio 中，生成项目后，选择 **“调试** > **开始调试** ” (`F5`) 。

   随即打开示例应用窗口：

   ![WebView2SampleWinComp 应用窗口。](webview2samplewincomp-images/app-window.png)

1. 使用示例应用;请参阅 [WebView2SampleWinComp 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2SampleWinComp#readme)。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-13---inspect-the-code"></a>步骤 13 - 检查代码

1. 在 Visual Studio 代码编辑器中，检查代码：

   ![Visual Studio 中的 WebView2SampleWinComp 项目](webview2samplewincomp-images/inspect-code-visual-studio.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Win32 应用中的 WebView2 入门](../get-started/win32.md)
