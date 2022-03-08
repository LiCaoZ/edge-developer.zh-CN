---
title: WebView2 示例：具有可视合成的 Win32 C++ 应用
description: 此 WebView2 示例演示了创建在 Win32 本机应用程序中嵌入 WebView2 控件的应用程序。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: e82cd779a9dae6cd78e4f78b03571b236fa0221b
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433712"
---
# <a name="webview2-sample-win32-c-app-with-visual-composition"></a>WebView2 示例：具有可视合成的 Win32 C++ 应用

此 WebView2 示例演示了创建在 Win32 本机应用程序中嵌入 WebView2 控件的应用程序。

它构建为 Win32 Visual Studio 2019 项目，并使用 WebView2 环境中 C++ 和 HTML/CSS/JavaScript。

它还使用 Windows 运行时合成 API (也称为可视化层) ，以利用 Windows UI 功能，在 C++ Win32 应用程序中创建更好的外观和功能。

&amp; 目录 .sln：**WebView2SampleWinComp/WebView2SampleWinComp.sln**。


**若要使用此示例， (通用步骤) ：**

当前页面上的步骤是通用步骤。  请参阅自述文件部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述

1. 在单独的窗口或选项卡中，在 README.md：[WebView2SampleWinComp 的自](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp#readme)述文件GitHub呈现的项目文件。  然后返回到此页面并继续以下步骤。

   * [自述>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp#prerequisites)

   * [自述>生成 WebView2 示例 WinComp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp#build-the-webview2-sample-wincomp)

   还可以在 README.md 中 (呈现) 文件Visual Studio。  在 **"文件管理器**"Visual Studio >"解决方案资源管理器"中，打开文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WebView2SampleWinComp/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-master/SampleApps/WebView2SampleWinComp/README.md`


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

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-master/SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.sln`

   可能会 **显示"复查** 解决方案操作"对话框：

   !["查看解决方案操作"对话框。](media/webview2samplewincomp-review-solution-actions.png)

1. 单击" **确定"** 按钮。


<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 安装工作负载（如果提示）

1. 如果系统提示，请Visual Studio所有请求的工作负荷。  在单独的窗口或选项卡中，请参阅[](../how-to/machine-setup.md#install-visual-studio-workloads)为 _WebView2 Visual Studio开发人员环境"中的安装新工作负载_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。

   解决方案资源管理器显示 **WebView2SampleWinComp** 项目。

   <!-- Solution Explorer shows the **WebView2SampleWinComp** project: -->

   <!-- ![The WebView2SampleWinComp sample opened in Visual Studio in Solution Explorer.](media/webview2samplewincomp-in-solution-explorer.png) -->
   <!--todo: create png-->


<!-- ====================================================================== -->
## <a name="step-7---view-the-opened-project"></a>步骤 7 - 查看打开的项目

项目将在以下Visual Studio：

![WebView2SampleWinComp 项目中的 Visual Studio。](media/webview2samplewincomp-project-in-sln-explorer.png)

_若要缩放，请右键> **新选项卡中的"打开图像"**。_


<!-- ====================================================================== -->
## <a name="step-8---install-or-update-the-webview2-sdk"></a>步骤 8 - 安装或更新 WebView2 SDK

<!-- comment on sample says: "Update apps to to 1.0.1056-prerelease (#110)"  Oct 28 2021 -->

1. 在项目节点（而不是解决方案资源管理器 (解决方案节点）) WebView2 SDK。  在单独的窗口或选项卡中，请参阅为 [WebView2](../how-to/machine-setup.md#install-the-webview2-sdk) 设置开发环境 _中的安装 WebView2 SDK_。  按照该部分中的步骤操作，然后返回到此页面，然后继续下一步。


<!-- ====================================================================== -->
## <a name="step-9---build-the-project"></a>步骤 9 - 生成项目

在项目顶部Visual Studio设置生成目标，如下所示：

1. 在" **解决方案配置"** 下拉列表中，选择" **调试"** 或"发布 **"**。

1. 在" **解决方案平台"** 下拉列表中，选择 **x86**、 **x64** 或 **ARM64**。

1. 在 **"解决方案资源管理器**"中，右键单击 **"WebView2SampleWinComp** "项目，然后选择"生成 **"**。

   这将生成项目文件 `SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.vcxproj`。


<!-- ====================================================================== -->
## <a name="step-10---install-or-update-the-microsoftwindowscppwinrt-package"></a>步骤 10 - 安装或更新 Microsoft。Windows。CppWinRT 程序包

在以上步骤中，生成可能会失败，如下所示：

   ```
   Build started...
   1>------ Build started: Project: WebView2SampleWinComp, Configuration: Debug x64 ------
   1>AppWindow.cpp
   1>C:\Program Files (x86)\Windows Kits\10\Include\10.0.19041.0\cppwinrt\winrt\impl\Windows.Foundation.0.h(983,26):
   error C2039: 'wait_for': is not a member of 'winrt::impl'
   1>C:\Program Files (x86)\Windows Kits\10\Include\10.0.19041.0\cppwinrt\winrt\impl\Windows.Foundation.0.h(103):
   message : see declaration of 'winrt::impl'
   1>C:\Program Files (x86)\Windows Kits\10\Include\10.0.19041.0\cppwinrt\winrt\impl\Windows.Foundation.0.h(985):
   message : see reference to class template instantiation 'winrt::impl::consume_Windows_Foundation_IAsyncAction<D>' being compiled
   ...
   1>Generating Code...
   1>Done building project "WebView2SampleWinComp.vcxproj" -- FAILED.
   ========== Build: 0 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========
   ```

1. 若要修复此问题：在"**** 解决方案资源管理器"中，右键单击解决方案的项目节点 (而不是解决方案节点) 然后选择"管理 NuGet **包"**。

   the **NuGet 程序包管理器** tab opens in Visual Studio.

1. 在"**NuGet**窗口中，单击"浏览 **"** 选项卡。

1. 在搜索栏右侧，清除"包含预发行**** (复选框，除非你知道需要 SDK) 。

1. 在左上方的搜索栏中，键入 **Microsoft.Windows。CppWinRT**。

1. 在搜索栏下方，单击 **"Microsoft.Windows"。CppWinRT** 卡。

1. 在右侧窗格中，单击"安装 ("**** 或 **"** 更新) 按钮。  NuGet下载 Microsoft。Windows。CppWinRT 程序包到你的计算机，供此项目使用。

   ![选择"Microsoft"。Windows。NuGet 程序包管理器 中的 CppWinRT Visual Studio。](media/webview2samplewincomp-manage-nuget-cppwinrt.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_

   将 **打开"预览** 更改"对话框：

   !["Microsoft"的"预览更改"对话框。Windows。CppWinRT'程序包。](media/webview2samplewincomp-preview-changes-cppwinrt.png)

1. 单击" **确定"** 按钮。

1. 文件 `readme.txt` 将打开用于 CppWinRT 程序包：

   ![CppWinRT readme.txt包的配置文件。](media/webview2samplewincomp-cppwinrt-readme.png)

Microsoft。Windows。CppWinRT 程序包现已安装或更新。  继续执行以下步骤。

### <a name="see-also"></a>另请参阅

* [NuGet.org > Microsoft。Windows。CppWinRT NuGet程序包](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/)

* [GitHub > microsoft/cppwinrt 存储库>问题>错误 C2039："wait_for"：不是"winrt：：impl"#744 的成员](https://github.com/microsoft/cppwinrt/issues/744)

   <!-- > `impl::wait_for` is defined later in `Windows.Foundation.h:2960`, but other foundation headers (via `2.h`, `1.h` and `0.h`) included earlier require it.
   >
   > The version of C++/WinRT that ships in the Windows SDK is rather old, and fails to compile with the stricter conformance expectations of more recent compilers. You can get a newer version of C++/WinRT here: https://aka.ms/cppwinrt/nuget
   >
   > I ended up running the `cppwinrt.exe` manually, since I couldn't get the `CMake VC_PROJECT_IMPORT` to work.  This works well for me; the headers are all generated in my build folder at generation time. -->


<!-- ====================================================================== -->
## <a name="step-11---build-the-project-again"></a>步骤 11 - 再次生成项目

1. 在 **"解决方案资源管理器**"中，右键单击 **"WebView2SampleWinComp** "项目，然后选择"生成 **"**。

   这将生成项目文件 `SampleApps/WebView2SampleWinComp/WebView2SampleWinComp.vcxproj`。

   <!-- The build might fail:

   ![Build fail: after installing the Microsoft.Windows.CppWinRT package.](media/webview2samplewincomp-build-fail-after-cppwinrt-pkg.png)

   _To zoom, right-click > **Open image in new tab**._ -->


<!-- ====================================================================== -->
## <a name="step-12---run-debug-the-project"></a>步骤 12 - () 调试项目

<!-- retest: -->

1. In Visual Studio， select **DebugStart** >  **Debugging** (`F5`) .

   疑难解答：如果在生成项目之前尝试调试，则可能会显示一个对话框："存在生成错误"：

   !["生成错误"对话框。](media/webview2samplewincomp-build-errors-dialog-box.png)

   单击**是**按钮。  将出现一个对话框："无法启动程序：找不到文件"：

   !["无法启动程序"对话框。](media/webview2samplewincomp-unable-to-start-program.png)

   若要修复此问题，在调试项目之前生成该项目。
   <!-- ------------------------------- -->

   解决生成问题，然后进入调试模式后，将打开示例应用窗口。

   <!-- The sample app window opens: -->
   <!-- ![The WebView2SampleWinComp app window.](media/WebView2SampleWinComp-app-window.png) -->
   <!-- todo: create png -->

1. 使用示例应用;请参阅 [WebView2SampleWinComp 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2SampleWinComp#readme)。

1. 在Visual Studio中，选择 **"调试** > **""停止调试"**。  Visual Studio关闭应用。


<!-- ====================================================================== -->
## <a name="step-13---inspect-the-code"></a>步骤 13 - 检查代码

1. 在Visual Studio编辑器中，检查代码。

   <!--
   1. In the Visual Studio code editor, inspect the code:

   ![The WebView2SampleWinComp project in Visual Studio](media/WebView2SampleWinComp-in-visual-studio.png)

   _To zoom, right-click > **Open image in new tab**._
   -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Win32 应用中的 WebView2 入门](../get-started/win32.md)
