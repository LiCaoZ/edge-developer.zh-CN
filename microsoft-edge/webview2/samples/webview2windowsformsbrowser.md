---
title: WinForms 示例应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 在 WinForms 应用中实现 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 42ea065f71f527d9468dc1f0c743518c08497de9
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754719"
---
# <a name="winforms-sample-app"></a>WinForms 示例应用

<!-- todo: paste/merge into here from corresp Readme https://github.com/MicrosoftEdge/WebView2Samples/pull/140/files -->

此示例 **WebView2WindowsFormsBrowser** 演示如何使用 WebView2 控件和 WebView2 API 在 WinForms 应用中实现 Web 浏览器。

*  示例名称： **WebView2WindowsFormsBrowser**
*  存储库目录： [WebView2WindowsFormsBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser)
*  解决方案文件： **WebView2WindowsFormsBrowser.sln**

![WebView2WindowsFormsBrowser 应用窗口](media/webview2windowsformsbrowser-app-window.png)

*  “ **控制** ”菜单具有“ **加速器密钥** ”和“ **允许外部删除**”的切换菜单。
*  “ **视图** ”菜单具有 **“缩放** ”和 **“背景色** ”子菜单。
*  “ **事件** ”按钮将打开 **EventMonitor** 窗口。


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio"></a>步骤 1 - 安装 Visual Studio

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

1. 如果 Visual Studio (尚未安装所需的最低版本) ，请在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-a-preview-channel-of-microsoft-edge"></a>步骤 2 - 安装 Microsoft Edge 的预览频道

1. 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---clone-or-download-the-webview2samples-repo"></a>步骤 3 - 克隆或下载 WebView2Samples 存储库

1. 如果尚未完成，请将存储库克隆或下载 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-4---open-sln-in-visual-studio"></a>步骤 4 - 在 Visual Studio 中打开 .sln

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中的目录中打开该文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

<!-- ====================================================================== -->
## <a name="step-5---install-workloads-if-prompted"></a>步骤 5 - 如果出现提示，请安装工作负载

1. 如果出现提示，请安装请求的任何 Visual Studio 工作负载。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-6---build-and-run-the-project"></a>步骤 6 - 生成并运行项目

从执行上述步骤开始， **WebView2WindowsFormsBrowser** 项目现已在 Visual Studio 中打开。  在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WindowsFormsBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.vcxproj`。  这可能需要几分钟时间。

   如果收到有关缺少 .NET Framework 4.6.2 开发人员包的错误消息，请执行以下步骤。  否则，请跳到下面的下一个主要部分。

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WebView2WindowsFormsBrowser 应用窗口](media/webview2windowsformsbrowser-app-window.png)

1. 使用示例应用;请参阅 [WebView2WindowsFormsBrowser 的 README 文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WindowsFormsBrowser#readme)。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-7---install-net-framework-462-developer-pack"></a>步骤 7 - 安装.NET Framework 4.6.2 开发人员包

如果生成 **WebView2WindowsFormsBrowser** 项目并收到有关缺少 .NET Framework 4.6.2 开发人员包的错误消息，请按照以下步骤操作。  否则，请跳到下面的下一个主要部分。

1. 转到[“下载.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/)”，选择 v4.6.2，然后单击“**下载.NET Framework 4.6.2 开发人员包**”按钮：

   ![下载 .NET Framework 4.6.2 开发人员包](media/webview2windowsformsbrowser-dl-net-fwk.png)

1. 在 Microsoft Edge 中，选择 **“设置”和“更多** > **下载** > **显示在文件夹”** 图标中：

   ![下载.NET Framework开发人员包](media/webview2windowsformsbrowser-thx-dl-net-fwk.png)

1. 在文件夹中 `Downloads` ，双击文件，例如 `ndp462-devpack-kb3151934-enu.exe`。

   **“Microsoft .NET Framework开发人员包**许可协议”对话框随即显示：

   ![“Microsoft .NET Framework开发人员包许可证协议”对话框](media/webview2windowsformsbrowser-net-fwk-license-462.png)
   <!-- ![The Microsoft .NET Framework Developer Pack license agreement dialog box](media/webview2windowsformsbrowser-net-fwk-license.png) 4.8, keep as-in, in case needed -->

1. 选中 **“我同意许可条款和条件** ”复选框，然后单击“ **安装** ”按钮。

   此时会显示一个 **“用户帐户控制** ”窗口，询问“是否允许此应用对设备进行更改？”

1. 单击**是**按钮。

   “Microsoft .NET Framework开发人员包**安装成功**”对话框随即显示：

   ![Microsoft .NET Framework开发人员包“安装成功”对话框](media/webview2windowsformsbrowser-net-dev-pak-success-462.png)
   <!-- ![The Microsoft .NET Framework Developer Pack 'Setup Successful' dialog box](media/webview2windowsformsbrowser-net-dev-pak-success.png) 4.8, keep as-in, in case needed -->

1. 单击**关闭**按钮。

Microsoft .NET Framework 4.6.2 开发人员工具包现已安装在计算机上。


<!-- ====================================================================== -->
## <a name="step-8---update-or-install-the-webview2-sdk"></a>步骤 8 - 更新或安装 WebView2 SDK

<!-- a checkin comment at repo says "Update projects to use latest WebView2 SDK 1.0.781-prerelease (#74)" -->

1. **WebView2 SDK** - 更新或安装项目节点上的 WebView2 SDK， (解决方案资源管理器中) 解决方案节点。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   <!-- this same png is used multiple times in this file -->
   ![Visual Studio 中的 WebView2WindowsFormsBrowser 项目](media/webview2windowsformsbrowser-in-visual-studio.png)


<!-- ====================================================================== -->
## <a name="step-9---build-and-run-the-updated-project"></a>步骤 9 - 生成并运行更新的项目

1. 如果刚才安装.NET Framework上面的 4.6.2 开发人员包，请关闭 Visual Studio，然后从目录再次在 Visual Studio 中打开解决方案文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.sln`

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **“任何 CPU**”。

1. 在**解决方案资源管理器**中，右键单击 **WebView2WindowsFormsBrowser** 项目，然后选择 **“生成**”。

   这会生成项目文件 `SampleApps/WebView2WindowsFormsBrowser/WebView2WindowsFormsBrowser.vcxproj`。

1. 在 Visual Studio 中，选择 **“调试** > **开始调试** ” () `F5` 。

   随即打开示例应用窗口：

   ![WebView2WindowsFormsBrowser 应用窗口](media/webview2windowsformsbrowser-app-window.png)

   *  “ **控制** ”菜单具有“ **加速器密钥** ”和“ **允许外部删除**”的切换菜单。
   *  “ **视图** ”菜单具有 **“缩放** ”和 **“背景色** ”子菜单。
   *  “ **事件** ”按钮将打开 **EventMonitor** 窗口。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-10---inspect-the-code"></a>步骤 10 - 检查代码

1. 在 Visual Studio 代码编辑器中，检查代码：

   <!-- this same png is used multiple times in this file -->
   ![Visual Studio 中的 WebView2WindowsFormsBrowser 项目](media/webview2windowsformsbrowser-in-visual-studio.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WinForms 应用中的 WebView2 入门](../get-started/winforms.md)
