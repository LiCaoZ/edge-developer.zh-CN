---
title: 用于部署 WebView2 运行时的 WiX 自定义操作
description: 演示如何使用 WiX 自定义操作部署 WebView2 运行时的 WebView2 示例。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 06568961a833266d317473d99edf9b81571e39ea
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754670"
---
# <a name="wix-custom-action-to-deploy-the-webview2-runtime"></a>用于部署 WebView2 运行时的 WiX 自定义操作

此示例 **WV2DeploymentWiXCustomActionSample** 演示如何使用 WiX 自定义操作部署 WebView2 运行时。

*  示例名称： **WV2DeploymentWiXCustomActionSample**
*  存储库目录： [WV2DeploymentWiXCustomActionSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXCustomActionSample)
*  项目文件： **WV2DeploymentWiXCustomActionSample.wixproj**

<!-- todo: screenshot representing the success state -->

为了帮助你了解如何使用应用部署 Evergreen WebView2 运行时，此示例为 **WebView2APISample** 创建[一个 WiX](https://wixtoolset.org/) 安装程序，并使用 [WiX 自定义操作](https://wixtoolset.org/documentation/manual/v3/wixdev/extensions/authoring_custom_actions.html)链接安装 Evergreen WebView2 运行时。

此示例演示了几种不同的部署方法：
* 使用链接下载 Evergreen WebView2 运行时引导程序。
* 使用应用打包 Evergreen WebView2 运行时引导程序。
* 使用应用打包 Evergreen WebView2 运行时独立安装程序。


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio-2019-with-c-support"></a>步骤 1 - 使用 C++ 支持安装 Visual Studio 2019

<!-- readme says "Prereqs: Visual Studio 2019 with C++ support installed." -->

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

1. **Visual Studio** - 如果尚未安装具有 C++ 支持的 Visual Studio 2019 (所需的最低版本) ，请参阅在单独的窗口或选项卡中 [安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio) 以 _设置 WebView2 的开发环境_。  按照该部分中的步骤在 C++ 支持下安装 Visual Studio 2019，然后返回到此页面并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-a-preview-channel-of-microsoft-edge"></a>步骤 2 - 安装 Microsoft Edge 的预览频道

1. **Microsoft Edge 的预览频道** - 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-3---install-wix-toolset-build-tools"></a>步骤 3 - 安装 WiX 工具集生成工具

如果尚未完成，请安装 WiX 工具集：

1. 在新窗口或选项卡中，转到 [WiX 工具集](https://wixtoolset.org/releases/) ，然后下载 **WiX 工具集生成工具**。

1. 单击该 `wixnnn.exe` 文件，然后单击 **“打开文件**”。

   可能会打开对话框，**需要启用.NET Framework 3.5.1**：

   ![需要.NET Framework对话框](./wv2deploymentwixburnbundlesample-images/wix-requires-dotnet-fwk-351.png)

   如果计算机上已启用 .NET Framework 3.5.1，请跳到前面继续安装此 WiX 组件。

1. 单击 **“确定”** 按钮。  WiX 安装程序窗口关闭。

1. 在键盘上按 **Windows** 键 ![Windows 键徽标](../../media/windows-keyboard-logo.png) ，键入 **Windows 功能**，然后按 **Enter**。  随即显示“ **打开或关闭 Windows 功能** ”对话框。

1. 选.NET Framework **3.5 (包含 .NET 2.0 和 3.0) **复选框：

   ![打开或关闭 Windows 功能> .NET Framework 3.5](./wv2deploymentwixburnbundlesample-images/turn-windows-features-on.png)

   无需选择子项。

1. 单击“确定”****。  系统可能会提示是否允许Windows 更新下载文件。

   有关详细信息，请参阅[在Windows 11、Windows 10、Windows 8.1和Windows 8上安装 .NET Framework 3.5](/dotnet/framework/install/dotnet-35-windows)。

1. 启用.NET Framework 3.5.1 后，再次运行该`wixnnn.exe`文件。  例如，在 Microsoft Edge 中，单击 **“设置”等**，单击 **“下载**”，然后单击下面`wix311.exe`**的“打开文件**”。

1. 单击 WiX 安装程序的 **“安装** ”面板。

1. 在 **“用户帐户控制**”中，单击“ **是”** 按钮。  WiX 安装程序顶部显示“已成功安装”。

另请根据下一部分安装 WiX Visual Studio 组件。


<!-- ====================================================================== -->
## <a name="step-4---install-wix-toolset-visual-studio-extension"></a>步骤 4 - 安装 WiX 工具集 Visual Studio 扩展

如果尚未完成，请安装 WiX 工具集 Visual Studio 2019 扩展：

1. 在新窗口或选项卡中，转到 [WiX 工具集](https://wixtoolset.org/releases/) ，然后下载并安装扩展：
   * WiX 工具集 Visual Studio 2019 扩展 - 下载的安装程序文件： `Votive2019.vsix`

1. 在 **“用户帐户控制**”中，单击“ **是”** 按钮。  将打开适用于 WiX Visual Studio 的 VSIX 安装程序扩展：

   ![适用于 WiX Visual Studio 2019 扩展的 VSIX 安装程序](./wv2deploymentwixburnbundlesample-images/vsix-installer-wix-vs-2019-ext.png)

   <!-- ![VSIX Installer for WiX Visual Studio 2022 extension](./wv2deploymentwixburnbundlesample-images/vsix-installer-wix-vs-2022-ext.png) -->

1. 单击“ **安装** ”按钮。

1. 如果 **正在等待进程关闭** 对话框的 VSIX 打开，请关闭 Visual Studio。  VSIX 安装程序继续操作。

   VSIX 安装程序读取 **安装完成**：

   ![VSIX 安装程序 - 安装完成 - WiX 工具集 Visual Studio 2019 扩展](./wv2deploymentwixburnbundlesample-images/vsix-installer-wix-vs-2019-ext-complete.png)

   <!-- ![VSIX Installer - Install Complete - WiX Toolset Visual Studio 2022 Extension](./wv2deploymentwixburnbundlesample-images/vsix-installer-wix-vs-2022-ext-complete.png) -->
   <!--todo: delete the two above pngs after confirm end-to-end -->

1. 在 VSIX 安装程序中，单击“ **关闭** ”按钮。

1. 在 WiX 安装程序中，单击 **“退出** ”面板。


<!-- ====================================================================== -->
## <a name="step-5---clone-the-webview2samples-repo"></a>步骤 5 - 克隆 WebView2Samples 存储库

1. 如果尚未完成，请将 `WebView2Sample` 存储库克隆到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的[“克隆 WebView2Samples 存储库](../how-to/machine-setup.md#clone-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-6---open-the-solution-in-visual-studio"></a>步骤 6 - 在 Visual Studio 中打开解决方案

1. 在 WebView2Samples 存储库的本地副本中，`<repo-location>\WebView2Samples\SampleApps\WebView2Samples.sln`打开 Visual Studio (不Visual Studio Code) 。


<!-- ====================================================================== -->
## <a name="step-7---edit-productwxs-to-configure-how-to-distribute-the-webview2-runtime"></a>步骤 7 - 编辑 Product.wxs 以配置如何分发 WebView2 运行时

1. 在项目下打开`Product.wxs``WV2DeploymentWiXCustomActionSample`。 

1. 根据要使用的方法进行编辑 `Product.wxs` ：


#### <a name="approach-1-downloading-the-evergreen-webview2-runtime-bootstrapper-through-a-link"></a>方法 1：通过链接下载常青 WebView2 运行时引导程序

如果希望应用通过链接下载 Evergreen WebView2 运行时引导程序 (`MicrosoftEdgeWebview2Setup.exe`) ：

1. 在下面`<!-- Step 4: Config Custom Action to download/install Bootstrapper -->`，取消注释下面`<!-- [Download Bootstrapper] ... -->`的`<CustomAction Id='DownloadAndInvokeBootstrapper' ...>`元素。

1. 注释掉其他 `<Binary>` 和 `<CustomAction>` 下面的元素 `Step 4`。

1. 在下面`<!-- Step 5: Config execute sequence of custom action -->`，取消注释下面`<!-- [Download Bootstrapper] ...-->`的`<Custom Action='DownloadAndInvokeBootstrapper' ...>`元素。

1. 注释掉下`Step 5`的其他`<Custom>`元素。


#### <a name="approach-2-packaging-the-evergreen-webview2-runtime-bootstrapper-with-the-app"></a>方法 2：使用应用打包常青 WebView2 运行时引导程序

如果要将 Evergreen WebView2 运行时启动程序 (`MicrosoftEdgeWebview2Setup.exe`) 与应用打包：

1. 在下面`<!-- Step 4: Config Custom Action to download/install Bootstrapper -->`，取消注释下面`<!-- [Package Bootstrapper] ... -->`的`<Binary Id="MicrosoftEdgeWebview2Setup.exe" ...>`和`<CustomAction Id='InvokeBootstrapper' ...>`元素。

1. 注释掉其他 `<Binary>` 和 `<CustomAction>` 下面的元素 `Step 4`。
        
1. 在下面`<!-- Step 5: Config execute sequence of custom action -->`，取消注释下面`<!-- [Package Bootstrapper] ...-->`的`<Custom Action='InvokeBootstrapper' ...>`元素。

1. 注释掉下`Step 5`的其他`<Custom>`元素。


#### <a name="approach-3-packaging-the-evergreen-webview2-runtime-standalone-installer-with-your-app"></a>方法 3：使用应用打包 Evergreen WebView2 运行时独立安装程序

如果要使用应用打包 Evergreen WebView2 运行时独立安装程序：

1. 在下面`<!-- Step 4: Config Custom Action to download/install Bootstrapper -->`，取消注释下面`<!-- [Package Standalone Installer] ... -->`的`<Binary Id="MicrosoftEdgeWebView2RuntimeInstallerX64.exe" ...>`和`<CustomAction Id='InvokeStandalone' ...>`元素。 

1. 注释掉其他 `<Binary>` 和 `<CustomAction>` 下面的元素 `Step 4`。

1. 如果面向非 X64 设备，可能还需要编辑 `MicrosoftEdgeWebView2RuntimeInstallerX64` 文件名以反映正确的体系结构。

1. 在下面`<!-- Step 5: Config execute sequence of custom action -->`，取消注释下面`<!-- [Package Standalone Installer] ...-->`的`<Custom Action='InvokeStandalone' ...>`元素。

1. 注释掉下`Step 5`的其他`<Custom>`元素。


<!-- ====================================================================== -->
## <a name="step-8---put-bootstrapper-or-installer-in-the-folder"></a>步骤 8 - 在文件夹中放置引导程序或安装程序

如果计划使用应用打包 Bootstrapper (方法 2) 或独立安装程序 (方法 3) ：

1. 下载 Bootstrapper 或独立安装程序。  在 [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) 上，单击 **“立即下载**”，向下滚动到 **“下载 WebView2 运行时** ”部分。

1. 将下载的 Bootstrapper 或独立安装程序置于封闭 `SampleApps` 文件夹下。


<!-- ====================================================================== -->
## <a name="step-9---build-the-installer-project"></a>步骤 9 - 生成安装程序项目

1. `WV2DeploymentVSInstallerSample`生成项目。

<!-- TODO: describe the Done state; explain result: accomplished xyz -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Win32 示例应用](./webview2apissample.md)
* 在_分发应用和 WebView2 运行时_中[部署 Evergreen WebView2 运行时](/microsoft-edge/webview2/concepts/distribution.md#deploying-the-evergreen-webview2-runtime)。
* [WV2DeploymentWiXCustomActionSample 的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXCustomActionSample#readme)。
* [WiX 工具集](https://wixtoolset.org/)
* [WiX >添加自定义操作](https://wixtoolset.org/documentation/manual/v3/wixdev/extensions/authoring_custom_actions.html)
