---
title: WebView2 示例：WinForms 浏览器应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WinForms 应用中实现 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: b960da1903287f902fe29d0d4d5f9fc430fdc6cf
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522236"
---
# <a name="webview2-sample-winforms-browser-app"></a>WebView2 示例：WinForms 浏览器应用

此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WinForms 应用中实现 Web 浏览器。

Directory &amp; .sln： **WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln**。


<!-- ====================================================================== -->
## <a name="step-1---view-the-readme"></a>步骤 1 - 查看自述文件

当前页面上的步骤是通用的。  请参阅 README 部分中特定于示例的步骤，这些步骤可能会覆盖当前页面。

若要使用此示例，请按顺序执行以下步骤。

1. 在单独的窗口或选项卡中，读取此项目的呈现 README.md 文件GitHub：[WebView2WindowsFormsBrowser 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser#readme)。  然后返回到此页面，并继续执行以下步骤。

   * [自述文件>先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser#prerequisites)

   * [自述>生成 WebView2 Windows 窗体浏览器](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser#build-the-webview2-windows-forms-browser)

   还可以查看Visual Studio中未呈现)  (README.md 源文件。  在**文件管理器**或Visual Studio > 解决方案资源管理器中，打开该文件：<!-- todo: is there a .md preview capability locally? -->

   `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/README.md`

   或者：

   `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WindowsFormsBrowser/README.md`


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio"></a>步骤 2 - 安装Visual Studio

Microsoft Visual Studio是必需的。  此示例不支持Microsoft Visual Studio代码。

1. 如果尚未安装Visual Studio (所需的最低版本) ，请在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-a-preview-channel-of-microsoft-edge"></a>步骤 3 - 安装预览频道Microsoft Edge

1. 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发人员环境_时[安装Microsoft Edge预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-4---download-or-clone-the-webview2samples-repo"></a>步骤 4 - 下载或克隆 WebView2Samples 存储库

1. 如果尚未完成，请将存储库下载或克隆 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-5---open-sln-in-visual-studio"></a>步骤 5 - 在 Visual Studio 中打开 .sln

1. 在本地驱动器上`.sln`，在目录中打开Visual Studio中的文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

<!-- ====================================================================== -->
## <a name="step-6---install-workloads-if-prompted"></a>步骤 6 - 如果出现提示，请安装工作负载

1. 如果出现提示，请安装请求的任何Visual Studio工作负荷。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装Visual Studio工作负荷](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-7---view-the-opened-project"></a>步骤 7 - 查看打开的项目

   解决方案资源管理器显示 **WebView2WindowsFormsBrowser** 项目。

   <!-- Solution Explorer shows the **WebView2WindowsFormsBrowser** project: -->

   <!-- ![The WebView2WindowsFormsBrowser sample opened in Visual Studio in Solution Explorer.](media/webview2windowsformsbrowser-in-solution-explorer.png) -->
   <!--todo: create png-->


<!-- ====================================================================== -->
## <a name="step-8---install-or-update-the-webview2-sdk"></a>步骤 8 - 安装或更新 WebView2 SDK

<!-- checking comment at repo says "Update projects to use latest WebView2 SDK 1.0.781-prerelease (#74)" -->

1. **WebView2 SDK** - 在项目节点上安装或更新 WebView2 SDK， (不是解决方案资源管理器中) 的解决方案节点。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   <!-- this same png is used multiple times in this file -->
   ![Visual Studio中的 WebView2WindowsFormsBrowser 项目](media/webview2windowsformsbrowser-in-visual-studio.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="step-9---install-net-framework-462-developer-pack"></a>步骤 9 - 安装 .NET Framework 4.6.2 开发人员包

若要生成此项目，需要.NET Framework 4.6.2 开发人员包。

若要测试是否安装了 .NET Framework 4.6.2 开发人员包，请执行以下操作：

在Visual Studio顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WindowsFormsBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.vcxproj`。  这可能需要几分钟时间。

   如果收到有关缺少 .NET Framework 4.6.2 开发人员包的错误消息，请执行以下步骤。  否则，请跳到下面的下一个主要部分。

1. 转到[“下载.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/)”，选择 v4.6.2，然后单击“**下载.NET Framework 4.6.2 开发人员包**”按钮：

   ![下载 .NET Framework 4.6.2 开发人员包](media/webview2windowsformsbrowser-dl-net-fwk.png)

1. 在Microsoft Edge中，在文件夹图标中选择**设置和更多** > **DownloadsShow** > ：****

   ![下载.NET Framework开发人员包](media/webview2windowsformsbrowser-thx-dl-net-fwk.png)

1. 在文件夹中 `Downloads` ，双击文件，例如 `ndp462-devpack-kb3151934-enu.exe`。

   **“Microsoft .NET Framework开发人员包**许可协议”对话框随即显示：

   ![Microsoft .NET Framework开发人员包许可证协议对话框。](media/webview2windowsformsbrowser-net-fwk-license-462.png)
   <!-- ![The Microsoft .NET Framework Developer Pack license agreement dialog box.](media/webview2windowsformsbrowser-net-fwk-license.png) 4.8, keep as-in, in case needed -->

1. 选中 **“我同意许可条款和条件** ”复选框，然后单击“ **安装** ”按钮。

   此时会显示一个 **“用户帐户控制** ”窗口，询问“是否允许此应用对设备进行更改？”

1. 单击**是**按钮。

   “Microsoft .NET Framework开发人员包**安装成功**”对话框随即显示：

   ![Microsoft .NET Framework开发人员包“安装成功”对话框。](media/webview2windowsformsbrowser-net-dev-pak-success-462.png)
   <!-- ![The Microsoft .NET Framework Developer Pack 'Setup Successful' dialog box.](media/webview2windowsformsbrowser-net-dev-pak-success.png) 4.8, keep as-in, in case needed -->

1. 单击**关闭**按钮。

Microsoft .NET Framework 4.6.2 开发人员工具包现已安装在计算机上。


<!-- ====================================================================== -->
## <a name="step-10---build-the-project"></a>步骤 10 - 生成项目

1. 如果刚才安装.NET Framework上面的 4.6.2 开发人员包，请关闭Visual Studio，然后从目录Visual Studio再次打开解决方案文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

在Visual Studio顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WindowsFormsBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.vcxproj`。


<!-- ====================================================================== -->
## <a name="step-11---run-debug-the-project"></a>步骤 11 -) 项目运行 (调试

1. 在Visual Studio中，选择“**调试** > **"开始"菜单调试** () `F5` 。

   随即打开示例应用窗口：

   ![WebView2WindowsFormsBrowser 应用窗口。](media/webview2windowsformsbrowser-app-window.png)

1. 使用示例应用;请参阅 [WebView2WindowsFormsBrowser 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser#readme)。

1. 在Visual Studio中，选择 **“调试** > **Stop调试**”。  Visual Studio关闭应用。


<!-- ====================================================================== -->
## <a name="step-12---inspect-the-code"></a>步骤 12 - 检查代码

1. 在Visual Studio代码编辑器中，检查代码：

   <!-- this same png is used multiple times in this file -->
   ![Visual Studio中的 WebView2WindowsFormsBrowser 项目](media/webview2windowsformsbrowser-in-visual-studio.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WinForms 应用中的 WebView2 入门](../get-started/winforms.md)
