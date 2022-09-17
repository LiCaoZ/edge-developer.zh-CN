---
title: 用于部署 WebView2 运行时的 WiX 刻录捆绑包
description: 演示如何使用 WiX 燃烧捆绑包部署 WebView2 运行时的 WebView2 示例。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 13420e2d8df016edd5537086ca36e4a79ead324f
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754524"
---
# <a name="wix-burn-bundle-to-deploy-the-webview2-runtime"></a>用于部署 WebView2 运行时的 WiX 刻录捆绑包

此示例 **WV2DeploymentWiXBurnBundleSample** 演示如何使用 WiX 燃烧捆绑包部署 WebView2 运行时。  执行本文中的步骤，创建一个 WiX 安装程序，该安装程序通过燃烧捆绑包链式安装 Evergreen WebView2 运行时。

*  示例名称： **WV2DeploymentWiXBurnBundleSample**
*  存储库目录： [WV2DeploymentWiXBurnBundleSample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WV2DeploymentWiXBurnBundleSample)
*  项目文件： **WV2DeploymentWiXBurnBundleSample.wixproj**

此示例为 [Win32 示例应用](webview2apissample.md)创建 [WiX](https://wixtoolset.org/) 安装程序。  此示例使用 [WiX Burn 捆绑包](https://wixtoolset.org/documentation/manual/v3/bundle/) 链接安装 Evergreen WebView2 运行时。

<!-- todo: screenshot representing the success state -->

此示例演示了以下两种不同的分发方法，用于为应用分发 WebView2 运行时：
*  通过存储在应用中的链接下载 Evergreen WebView2 运行时引导程序。
*  使用应用打包 Evergreen WebView2 运行时引导程序。

此示例中未演示的另一种方法是将 Evergreen WebView2 运行时独立安装程序打包到应用中。  此方法非常类似于将 Evergreen WebView2 运行时引导程序打包到应用中。

有关这些方法的概述，请参阅在_分发应用和 WebView2 运行时_中[部署 Evergreen WebView2 运行时](../concepts/distribution.md#deploying-the-evergreen-webview2-runtime)。


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio"></a>步骤 1 - 安装 Visual Studio

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。

如果 Visual Studio (尚未安装所需的最低版本) ，并且支持 C++：

1. 在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤安装 Visual Studio，包括 C++ 支持。

然后返回到此页面，并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-wix-toolset-build-tools"></a>步骤 2 - 安装 WiX 工具集生成工具

如果尚未完成，请安装 WiX 工具集：

<!-- todo: how to make "Unsupported" go away?  what to say about it?
If you haven't installed WiX tools, the WiX deployment projects in Solution Explorer are marked as "Unsupported":

![Review project changes > Unsupported > .wixproj](./wv2deploymentwixburnbundlesample-images/review-project-changes-unsupported-wix.png) -->

<!-- Installing WiX is covered in [WiX Burn Bundle to deploy the WebView2 Runtime](./wv2deploymentwixburnbundlesample.md) but it's a good idea to install them for this **WebView2APISample** solution so it's a complete coherent setup.  So, install them, as follows: -->

1. 在新窗口或选项卡中，转到 [WiX 工具集](https://wixtoolset.org/releases/) ，然后下载 **WiX 工具集生成工具**。

   <!-- finding: this would just be an extra, roundabout step: Or, in Visual Studio, select **Extensions > Manage Extensions**.  The **Manage Extensions** dialog opens.  In the **Search** box, enter **wix toolset**, click the **WiX Toolset Build Tools** card, and then click the **Download** button to open the above webpage:  ![Manage Extensions in Visual Studio to install WiX](vs2019-manage-extensions-wix.png) -->

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
## <a name="step-3---install-wix-toolset-visual-studio-extension"></a>步骤 3 - 安装 WiX 工具集 Visual Studio 扩展

如果尚未完成，请安装 WiX 工具集 Visual Studio 2019 扩展：

1. 在新窗口或选项卡中，转到 [WiX 工具集](https://wixtoolset.org/releases/) ，然后下载并安装扩展：
   * WiX 工具集 Visual Studio 2019 扩展 - 下载的安装程序文件： `Votive2019.vsix`
   <!--* WiX Toolset Visual Studio 2022 Extension - downloaded installer file: `Votive2022.vsix`-->

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

1. 关闭 Visual Studio（如果已打开）。


<!-- ====================================================================== -->
## <a name="step-4---clone-or-download-the-webview2samples-repo"></a>步骤 4 - 克隆或下载 WebView2Samples 存储库

1. 如果尚未完成，请将存储库克隆或下载 `WebView2Sample` 到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。

按照该部分中的步骤操作，然后返回到此页，然后继续下文。


<!-- ====================================================================== -->
## <a name="step-5---build-the-deployment-project"></a>步骤 5 - 生成部署项目

1. 在 WebView2Samples 存储库的本地副本中，`<repo-location>\WebView2Samples\SampleApps\WebView2Samples.sln`打开 Visual Studio (不Visual Studio Code) 。

   如果 **不受支持...将显示 wixproj** 对话框，安装 WiX 工具集和 WiX 工具集扩展，如下所示：

   ![不受支持的 wix 项目消息](./media/unsupported-review-project-dialog.png)

1. 此示例是 [WV2DeploymentWiXCustomActionSample](./wv2deploymentwixcustomactionsample.md) 示例的扩展。  在解决方案资源管理器中，展开 **WV2DeploymentWiXCustomActionSample**，然后双击`Product.wxs`。

1. 在`Product.wxs`其中注释掉所有`<Binary>``<CustomAction>`内容和`<Custom>`元素`<!-- Step 4: Config Custom Action to download/install Bootstrapper -->``<!-- Step 5: Config execute sequence of custom action -->`，以便不使用自定义操作。

1. 在项目下打开`Bundle.wxs``WV2DeploymentWiXBurnBundleSample`。  根据要使用的工作流进行编辑 `Bundle.wxs` ：

   **若要使用应用打包 Evergreen WebView2 运行时引导程序，请执行以下操作：**
   *  取消注释下面`<!-- [Package Bootstrapper] ... -->`的`<ExePackage Id="InvokeBootstrapper" ...>`元素，并注释掉其他`<ExePackage>`元素。

   **若要通过应用中的链接下载 Evergreen WebView2 运行时引导程序：**
   *  取消注释下面`<!-- [Download Bootstrapper] ... -->`的`<ExePackage Id="DownloadAndInvokeBootstrapper" ...>`元素，并注释掉其他`<ExePackage>`元素。

1. 如果要将 Evergreen WebView2 运行时引导程序打包到应用中， [请下载](https://developer.microsoft.com/microsoft-edge/webview2/) Bootstrapper 并将其置于封闭 `SampleApps` 文件夹下。

1. `WV2DeploymentWiXBurnBundleSample`生成项目。

<!-- TODO: describe the Done state; explain result: accomplished xyz.  you'll use this result to... distribute runtime with app.

## Next steps
-->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* 在_分发应用和 WebView2 运行时_中[部署 Evergreen WebView2 运行时](../concepts/distribution.md#deploying-the-evergreen-webview2-runtime)。
