---
title: Win32 示例应用
description: 此 WebView2 示例演示如何使用 WebView2 控件和 WebView2 API 向 Win32 C++ 应用添加功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 07/29/2022
ms.openlocfilehash: 951e4a0f6f975f4f20daeb417cbc9a2b58679b2d
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754435"
---
# <a name="win32-sample-app"></a>Win32 示例应用

此示例 **WebView2APISample** 演示如何使用 WebView2 控件和 WebView2 API 向 Win32 C++ 应用添加功能。

*  示例名称： **WebView2APISample**
*  存储库目录： [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample)
*  解决方案文件：位于父目录中的 **WebView2Samples.sln** (， `\SampleApps\`) 
*  解决方案资源管理器中的项目名称：**WebView2APISample**

**WebView2APISample** 在 Win32 本机应用程序中嵌入 WebView2 控件。

此示例是作为 Win32 Visual Studio 2019 项目生成的。  它在 WebView2 环境中使用 C++ 和 HTML/CSS/JavaScript。
<!-- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/) -->

**WebView2APISample** 展示了一系列 WebView2 的事件处理程序和 API 方法，这些方法允许本机 Win32 应用程序直接与 WebView2 控件交互，反之亦然。

此示例及其解决方案文件是唯一的：它包含解决方案资源管理器中的其他示例的副本。

**WebView2APISample** 是使用 Microsoft Edge WebView2 控件构建的混合应用程序;也就是说，此应用合并了本机端和浏览器 Web 应用端。  请参阅 _Microsoft Edge WebView2 简介_中的[混合应用方法](../index.md#hybrid-app-approach)。

正在运行的 **WebView2APISample** 应用窗口显示 WebView2 SDK 版本以及 WebView2 运行时版本和路径。  提供了许多有用的菜单和菜单：

![显示 WebView2 SDK 版本和 WebView2 运行时版本和路径的 WebView2APISample 应用窗口](./webview2apissample-images/webview2apisample-app-window.png)
<!-- old:
![Sample App Snapshot](https://raw.githubusercontent.com/MicrosoftEdge/WebView2Samples/master/SampleApps/WebView2APISample/documentation/screenshots/sample-app-screenshot.png)
-->

如果这是你第一次使用 WebView，我们建议先遵循 [在 Win32 应用中开始使用 WebView2](../get-started/win32.md) 的教程，该教程介绍如何创建 WebView2 应用并演练一些基本的 WebView2 功能。  该特定教程不是从使用项目模板创建新的 Win32 项目开始的;而是从 WebView2Samples 存储库中的已完成项目开始，并指导你完成如何选择性地重新添加 WebView2 代码。
<!-- the getstart tut should probably create new app from project template, but, currently starts from existing project, that is provided now as a finished project -->

有关 WebView2 中的事件和 API 处理程序的详细信息， [请参阅 WebView2 API 参考](../webview2-api-reference.md)。


<!-- ====================================================================== -->
## <a name="step-1---install-a-preview-channel-of-microsoft-edge"></a>步骤 1 - 安装 Microsoft Edge 的预览频道

接下来，确保已在受支持的 OS 上安装 Microsoft Edge 的预览通道。  目前，我们建议使用最新版本的 Canary 通道。

1. 如果尚未安装 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，请参阅在_为 WebView2 设置开发环境_时[安装 Microsoft Edge 的预览频道](../how-to/machine-setup.md#install-a-preview-channel-of-microsoft-edge)。  按照该部分中的步骤操作，然后返回到此页并继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-visual-studio-2019"></a>步骤 2 - 安装 Visual Studio 2019

Microsoft Visual Studio 是必需的。  此示例不支持 Microsoft Visual Studio Code。  此存储库示例是一个 Visual Studio 2019 项目。

1. 如果 Visual Studio 2019 (未在 C++ 支持下安装最小必需版本) ，请参阅在单独的窗口或选项卡中，在_为 WebView2 设置开发环境_时[安装 Visual Studio](../how-to/machine-setup.md#install-visual-studio)。  按照该部分中的步骤在 C++ 支持下安装 Visual Studio 2019，然后返回到此页面并继续执行以下步骤。

如果要使用 Visual Studio 2017，请在 Visual Studio 2017 中打开解决方案后，将项目的平台工具集更改 **为 Project Properties > Configuration 属性>常规>平台工具集**。

若要使用 Visual Studio 2017，可能需要在计算机上安装最近的 Windows SDK。


<!-- ====================================================================== -->
## <a name="step-3---clone-the-webview2samples-repo"></a>步骤 3 - 克隆 WebView2Samples 存储库

1. 如果尚未完成，请将 `WebView2Sample` 存储库克隆到本地驱动器。  在单独的窗口或选项卡中，请参阅“_为 WebView2 设置开发环境_”中的“[下载 WebView2Samples 存储库](../how-to/machine-setup.md#download-the-webview2samples-repo)”。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

1. 如果之前克隆了存储库，请将最新提交拉取到存储库的本地副本。


<!-- ====================================================================== -->
## <a name="step-4---open-the-solution-in-visual-studio"></a>步骤 4 - 在 Visual Studio 中打开解决方案

1. 在本地驱动器上 `.sln` ，在 Visual Studio 中打开该文件：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2Samples.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2Samples.sln`

**WebView2APISample** 示例和项目是 Win32 的主要示例。

与其他一些示例不同，示例存储库目录中没有包含此示例自述文件的专用 `.sln` 文件。  相反， `.sln` 此示例的文件 (包括其他示例项目以及) 位于父目录中。

![解决方案中的所有项目解决方案资源管理器](./webview2apissample-images/all-projects-in-solution-explorer.png)


<!-- ====================================================================== -->
## <a name="step-5---install-workloads-if-prompted"></a>步骤 5 - 如果出现提示，请安装工作负载

1. **Visual Studio 工作负荷** - 如果出现提示，请安装请求的任何 Visual Studio 工作负荷。  在单独的窗口或选项卡中，请参阅在_为 WebView2 设置开发人员环境_时[安装 Visual Studio 工作负载](../how-to/machine-setup.md#install-visual-studio-workloads)。  按照该部分中的步骤操作，然后返回到此页，然后继续下文。

   <!-- The **Review project changes** dialog might open, indicating that the WiX deployment projects in Solution Explorer are Unsupported: -->

   <!-- ![Review project changes > Unsupported > .wixproj](./webview2apissample-images/review-project-changes-unsupported-wix.png) -->

<!-- 1. Click the **OK** button. -->

<!-- You don't need to install WiX to continue.  Installing WiX is covered in [WiX Burn Bundle to deploy the WebView2 Runtime](./wv2deploymentwixburnbundlesample.md). -->

继续执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-6---view-the-opened-project"></a>步骤 6 - 查看打开的项目

1. 在本地驱动器上，在设置的同一版本的 Visual Studio 中再次打开 **WebView2Samples** 解决方案，例如 Visual Studio 2019：

   *  `<your-repos-directory>/WebView2Samples/SampleApps/WebView2Samples.sln`

   或者：

   *  `<your-repos-directory>/WebView2Samples-main/SampleApps/WebView2Samples.sln`

   <!-- The Unsupported dialog might open: -->

   <!-- ![Review project changes > Unsupported > .wixproj](./webview2apissample-images/review-project-changes-unsupported-wix.png) -->

1. 单击 **“确定”** 按钮。  “ **重定向项目** ”对话框可能打开：

   ![“重定向项目”对话框](./webview2apissample-images/retarget-projects.png)

   已安装版本的示例：

   ![Retarget - 已安装 SDK](./webview2apissample-images/retarget-projects-22621.png)

1. 单击 **“确定”** 按钮。

解决方案资源管理器显示多个项目，包括 **WebView2APISample** 项目：

![解决方案资源管理器中的 WebView2APISample 项目](./webview2apissample-images/webview2apisample-in-solution-explorer.png)

<!-- ![WebView2APISample project Solution Explorer](./webview2apissample-images/solution-opened.png) -->


<!-- ====================================================================== -->
## <a name="step-7---build-the-project-using-the-installed-sdk-version"></a>步骤 7 - 使用安装的 SDK 版本生成项目

在 Visual Studio 顶部设置生成目标，如下所示：

1. 在 **“解决方案配置”** 下拉列表中，选择 **“调试** ”或 **“发布**”。

1. 在 **“解决方案平台** ”下拉列表中，选择 **x86**、 **x64** 或 **ARM64**。

1. 在**解决方案资源管理器**中，右键单击 **WebView2APISample** 项目，然后选择 **“生成**”。

   ![在解决方案资源管理器中选择的 WebView2APISample 项目](./webview2apissample-images/webview2apisample-project-selected.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_

   这会生成项目文件 `SampleApps/WebView2APISample/WebView2APISample.vcxproj`。


<!-- ====================================================================== -->
## <a name="step-8---run-debug-the-project"></a>步骤 8 -) 项目运行 (调试

1. 选择 **“调试** > **开始调试** ” () `F5` 。  

   故障排除：如果跳过生成步骤，并立即选择“ **调试** > **开始调试** ” () `F5` ，则可能会显示一个对话框“无法启动程序：找不到指定的路径”：

   ![对话框：无法启动程序：找不到指定的路径](./webview2apissample-images/webview2apisample-unable-to-start-program-cannot-find-path.png)

   若要解决此问题：**在解决方案资源管理器**中，右键单击 **WebView2APISample** 项目，然后选择 **“生成**”。

   **WebView2APISample 应用窗口随即**打开：

   ![WebView2APISample 应用窗口](./webview2apissample-images/webview2apisample-app-window.png)

   _若要缩放，请右键单击> **在新选项卡中打开图像**。_

1. 使用示例应用。  请参阅 [WebView2 API 示例的自述文件](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample#readme)，这是有关此示例中代码的长自述文件。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-9---update-the-prerelease-webview2-sdk"></a>步骤 9 - 更新预发行版 WebView2 SDK

最初生成&运行此项目后，更新 WebView2 SDK，然后重新生成项目。

若要快速查看在 GitHub 的示例应用的存储库副本中安装了哪个版本的 WebView2 SDK，请参阅 [packages.config](https://github.com/MicrosoftEdge/WebView2Samples/blob/main/SampleApps/WebView2APISample/packages.config)。

此示例的存储库版本已安装 WebView2 SDK 的预发布版本。  下面，你将将其更新到 WebView2 SDK 的最新预发布版本，或确认已安装最新的 SDK。  使用预发行 SDK 可以访问最新功能。

检查并更新已安装的 NuGet 包，如下所示：

1. 在解决方案资源管理器中，右键单击 **WebView2APISample** 项目 (而不是它上面的解决方案节点) ，然后选择 **“管理 NuGet 包**”。

   **NuGet 包管理器**面板在 Visual Studio 中打开。

1. 在搜索文本框的右侧，选中 **“包括预发行版** ”复选框。

1. 在 **NuGet 包管理器**中，单击 **“已安装** ”选项卡。 在每个包的右侧，检查是否列出了较新的版本号以及现有的版本号。

1. 单击“ **更新”** 选项卡。 如果 WebView2 或 WIL 包提供更新，如果需要，可以在此处更新包。
 
1. 在右侧的 **“版本** ”下拉列表中，如果希望能够尝试最新的 API，请确保选择了 **最新预发行** 版：

   ![已选择 WebView2 SDK 预发行版的 NuGet 包管理器](./webview2apissample-images/webview2apisample-pkg-mgr-prerelease-webview2.png)

   _上面的图像来自另一个项目，但相似。  若要缩放，请右键单击> **在新选项卡中打开图像**。_

1. 单击 **“更新”** 按钮。

   将显示 **“预览更改** ”对话框：

   ![WebView2 NugGet 包的“预览更改”对话框](./webview2apissample-images/webview2apisample-webview2-pkg-preview-changes.png)

   _上面的图像来自另一个项目，但相似。_

1. 单击 **“确定”** 按钮。

现已为此项目安装最新版本的 WebView2 SDK。


<!-- ====================================================================== -->
## <a name="step-10---build-and-run-the-project-with-updated-sdk"></a>步骤 10 - 使用更新的 SDK 生成并运行项目


1. 在**解决方案资源管理器**中，右键单击 **WebView2APISample** 项目，然后选择 **“生成**”。

   ![解决方案资源管理器中选择的 WebView2APISample 项目](./webview2apissample-images/webview2apisample-project-selected.png)

1. 选择 **“调试** > **开始调试** ” () `F5` 。  

   **WebView2APISample 应用窗口随即**打开：

   ![WebView2APISample 应用窗口](./webview2apissample-images/webview2apisample-app-window.png)

1. 使用示例应用。

1. 在 Visual Studio 中，选择 **“调试** > **停止调试**”。  Visual Studio 关闭应用。


<!-- ====================================================================== -->
## <a name="step-11---inspect-the-code"></a>步骤 11 - 检查代码

1. 在 Visual Studio 代码编辑器中，根据以下部分检查代码。


<!-- ====================================================================== -->
## <a name="application-architecture"></a>应用程序体系结构

API 示例应用是混合应用程序的示例。 它包含两个部分：Win32 本机部件和 WebView 部件。
*  Win32 部件可以访问本机 Windows API。
*  WebView 容器可以利用标准 Web 技术 (HTML、CSS、JavaScript) 。

通过这种混合方法，可以使用 Web 技术更快地创建和迭代，同时仍能利用本机功能。 示例应用专门演示了两个组件如何相互交互。

示例应用的这两个部分都显示在下图中：

![混合应用](./webview2apissample-images/sample-app-layout-diagram.png)
<!-- todo: remove from PR 140: ![alt text](https://raw.githubusercontent.com/MicrosoftEdge/WebView2Samples/master/SampleApps/WebView2APISample/documentation/screenshots/sample-app-layout-diagram.png) -->


1. 第一部分：示例应用的顶部是用 C++ 编写的 Win32 组件。 应用程序的这一部分接受用户的 UI 输入，并使用它们来控制 WebView。

2. 第 2 部分：示例应用的主要部分是可以使用标准 Web 技术 (HTML/CSS/JavaScript) 重用的 Web 视图。 可以导航到网站或本地内容。


<!-- ====================================================================== -->
## <a name="project-files"></a>项目文件

本部分简要介绍了存储库中的一些关键文件。 WebView2APISample 垂直划分为组件，而不是水平划分为层。  每个组件实现一类示例功能的整个工作流，从侦听菜单命令，到调用 WebView API 方法来实现它们。

#### <a name="1-appcpp"></a>1. App.cpp

这是运行示例应用的顶级文件。 它读取命令行选项，设置进程环境，并处理应用的线程模型。

#### <a name="2-appwindowcpp"></a>2. AppWindow.cpp

此文件实现应用程序窗口。 在此文件中，我们首先设置所有 Win32 控件。 其次，我们初始化 WebView 环境和 WebView。 第三，我们将一些事件处理程序添加到 WebView，并创建处理应用程序的各种功能的所有组件。 类 `AppWindow` 本身处理应用程序的“窗口”菜单中的命令。

#### <a name="3-filecomponentcpp"></a>3. FileComponent.cpp

此组件处理“文件”菜单中的命令 (退出) `DocumentTitleChanged` 以及事件除外。

#### <a name="4-scriptcomponentcpp"></a>4. ScriptComponent.cpp

此组件处理脚本菜单中的命令，其中包括通过注入 JavaScript、发布 WebMessage、将本机对象添加到网页或使用 DevTools 协议与网页通信来与 WebView 交互。

#### <a name="5-processcomponentcpp"></a>5. ProcessComponent.cpp

此组件处理“进程”菜单中的命令，这涉及到与浏览器进程的交互。 它还处理 ProcessFailed 事件，以防浏览器进程或其中一个呈现过程崩溃或无响应。

#### <a name="6-settingscomponentcpp"></a>6. SettingsComponent.cpp

此组件处理“设置”菜单中的命令，并且还负责在创建新 WebView 时从旧 WebView 复制设置。 可以在此处找到与接口交互的 `ICoreWebView2Settings` 大多数代码。

#### <a name="7-viewcomponentcpp"></a>7. ViewComponent.cpp

此组件处理视图菜单中的命令，以及与 WebView 的大小和可见性相关的任何功能。 当应用窗口调整大小、最小化或还原时， `ViewComponent` 将调整大小、隐藏或显示 WebView 作为响应。 它还响应 `ZoomFactorChanged` 事件。

#### <a name="8-scenariowebmessagecpp-and-scenariowebmessagehtml"></a>8. ScenarioWebMessage.cpp 和 ScenarioWebMessage.html

选择“方案/Web 消息”菜单项时，将创建此组件。 它实现具有 C++ 部件和 HTML+JavaScript 部件的示例应用程序，该部件通过异步发布和接收消息相互通信。

![Web 消息：发布和接收消息](./webview2apissample-images/sample-app-webmessaging-screenshot.png)
<!-- todo: remove from PR 140: ![alt text](https://raw.githubusercontent.com/MicrosoftEdge/WebView2Samples/master/SampleApps/WebView2APISample/documentation/screenshots/sample-app-webmessaging-screenshot.png) -->


#### <a name="9-scenarioaddhostobjectcpp-and-scenarioaddhostobjecthtml"></a>9. ScenarioAddHostObject.cpp 和 ScenarioAddHostObject.html

选择“方案/主机对象”菜单项时，将创建此组件。 它演示了本机应用与 HTML 网页之间通过主机对象注入进行的通信。  主机对象的接口在 `HostObjectSample.idl`其中声明，对象本身在 `HostObjectSampleImpl.cpp`其中实现。


<!-- ====================================================================== -->
## <a name="key-functions"></a>密钥函数

以下部分简要介绍了示例应用中的一些关键函数。


### <a name="appwindowcpp"></a>AppWindow.cpp

#### <a name="initializewebview"></a>InitializeWebView () 

在 AppWindow 文件中，我们使用 InitializeWebView () 函数通过使用 [CreateCoreWebView2EnvironmentWithOptions 创建 WebView2](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions) 环境。

创建环境后，我们将使用以下方式 `CreateCoreWebView2Controller`创建 WebView。

若要查看这些正在运行的 API 调用，请参阅以下代码片段 `InitializeWebView()`。

```cpp
HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
    subFolder, nullptr, options.Get(),
    Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
        this, &AppWindow::OnCreateEnvironmentCompleted)
        .Get());
if (!SUCCEEDED(hr))
{
    if (hr == HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND))
    {
        MessageBox(
            m_mainWindow,
            L"Couldn't find Edge installation. "
            "Do you have a version installed that's compatible with this "
            "WebView2 SDK version?",
            nullptr, MB_OK);
    }
    else
    {
        ShowFailure(hr, L"Failed to create webview environment");
    }
}
```

#### <a name="oncreateenvironmentcompleted"></a>OnCreateEnvironmentCompleted () 

此回调函数将传递到 `CreateCoreWebView2EnvironmentWithOptions` 其中 `InitializeWebView()`。  它存储环境指针，然后使用它创建新的 WebView。

```cpp
HRESULT AppWindow::OnCreateEnvironmentCompleted(
    HRESULT result, ICoreWebView2Environment* environment)
{
    CHECK_FAILURE(result);

    m_webViewEnvironment = environment;

    CHECK_FAILURE(m_webViewEnvironment->CreateCoreWebView2Controller(
        m_mainWindow, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
                            this, &AppWindow::OnCreateCoreWebView2ControllerCompleted)
                            .Get()));
    return S_OK;
}
```

#### <a name="oncreatecorewebview2controllercompleted"></a>OnCreateCoreWebView2ControllerCompleted () 

此回调函数将传递到 `CreateCoreWebView2Controller` 其中 `InitializeWebView()`。 在这里，我们初始化与 WebView 相关的状态，注册一些事件处理程序，并创建应用组件。

#### <a name="registereventhandlers"></a>RegisterEventHandlers () 

此函数在其中 `CreateCoreWebView2Controller`调用。 它设置应用程序使用的一些事件处理程序，并将其添加到 WebView。

若要详细了解 WebView2 中的事件处理程序，可以参阅此 [文档](/microsoft-edge/webview2/reference/win32/icorewebview2)。

下面是代码 `RegisterEventHandlers()`片段，我们在其中为 `NewWindowRequested` 事件设置了事件处理程序。 当网页中的 JavaScript 调用 `window.open()`时，会触发此事件，并且我们的处理程序会发出一个新 `AppWindow` 操作，并将新窗口的 WebView 传递回浏览器，以便它可以从 `window.open()` 调用中返回它。 不像我们的调用 `CreateCoreWebView2EnvironmentWithOptions` 和 `CreateCoreWebView2Controller`，而不是提供回调的方法，我们只是提供一个C++ lambda当时和那里。

```cpp
CHECK_FAILURE(m_webView->add_NewWindowRequested(
    Callback<ICoreWebView2NewWindowRequestedEventHandler>(
        [this](
            ICoreWebView2* sender,
            ICoreWebView2NewWindowRequestedEventArgs* args) {
            wil::com_ptr<ICoreWebView2Deferral> deferral;
            CHECK_FAILURE(args->GetDeferral(&deferral));

            auto newAppWindow = new AppWindow(L"");
            newAppWindow->m_isPopupWindow = true;
            newAppWindow->m_onWebViewFirstInitialized = [args, deferral, newAppWindow]() {
                CHECK_FAILURE(args->put_NewWindow(newAppWindow->m_webView.get()));
                CHECK_FAILURE(args->put_Handled(TRUE));
                CHECK_FAILURE(deferral->Complete());
            };

            return S_OK;
        })
        .Get(),
    nullptr));
```

### <a name="scenariowebmessage"></a>ScenarioWebMessage

这些 `ScenarioWebMessage` 文件显示 Win32 主机如何修改 WebView、WebView 如何修改 Win32Host，以及 WebView 如何通过访问 Win32 主机中的信息来修改自身。 这是异步完成的。

以下部分演示每个离散函数如何使用示例应用工作，然后说明如何实现此功能。

首先，使用以下步骤导航到示例应用中的 ScenarioWebMessage 应用程序：

1. 打开示例应用
2. 单击“方案”
3. 单击“Web 消息传送”

WebView 应显示标题为“WebMessage 示例页”的简单网页。 可以在文件中找到此页面的 `ScenarioWebMessage.html` 代码。

![用于发布和接收消息的 Web 消息](./webview2apissample-images/sample-app-webmessaging-screenshot.png)

若要更好地了解 ScenarioWebMessage 功能，可以按照页面上的说明或下面详述的步骤操作。

#### <a name="1-posting-messages-win32-host-to-webview"></a>1. 将消息 (Win32 主机发布到 WebView) 

以下步骤演示 Win32 主机如何修改 WebView。 在此示例中，将文本变为蓝色：

1. 单击工具栏中的脚本
2. 单击“发布 Web 消息 JSON”

应显示包含预写代码 `{"SetColor":"blue"}` 的对话框。

3. 单击“确定”

“发布消息”下的文本现在应为蓝色。

工作原理如下：

1. 在其中 `ScriptComponent.cpp`，我们使用 [PostWebMessageAsJson](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasjson) 将用户输入发布到 `ScenarioMessage.html` Web 应用程序。

```cpp
// Prompt the user for some JSON and then post it as a web message.
void ScriptComponent::SendJsonWebMessage()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Post Web Message JSON",
        L"Web message JSON:",
        L"Enter the web message as JSON.",
        L"{\"SetColor\":\"blue\"}");
    if (dialog.confirmed)
    {
        m_webView->PostWebMessageAsJson(dialog.input.c_str());
    }
}
```

2. 在 Web 应用程序中，事件侦听器用于接收和响应 Web 消息。 下面的代码片段来自 `ScenarioWebMessage.html`。 如果事件侦听器读取“SetColor”，则会更改文本的颜色。

```js
window.chrome.webview.addEventListener('message', arg => {
    if ("SetColor" in arg.data) {
        document.getElementById("colorable").style.color = arg.data.SetColor;
    }
});
```

#### <a name="2-receiving-messages-webview-to-win32-host"></a>2. (WebView 接收到 Win32 主机) 的消息

以下步骤演示 WebView 如何通过更改 Win32 应用的标题来修改 Win32 主机应用：

1. 找到示例应用的标题 - 图标旁边窗口左上角。
2. 在“接收消息”部分下，使用所选的新标题填写表单。
3. 单击“发送”

找到示例应用的标题，它应该已更改为刚输入的游戏。

工作原理如下：

1. 在其中 `ScenarioWebMessage.html`，我们调用 [window.chrome.webview.postMessage () ](https://developer.mozilla.org/docs/Web/API/Window/postMessage) 将用户输入发送到主机应用程序。 请参阅下面的代码片段：

```js
function SetTitleText() {
    let titleText = document.getElementById("title-text");
    window.chrome.webview.postMessage(`SetTitleText ${titleText.value}`);
}
```

2. 在其中 `ScenarioWebMessage.cpp`，我们使用 [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived) 注册事件处理程序。 当我们收到事件时，验证输入后，我们将更改应用窗口的标题。

```cpp
// Setup the web message received event handler before navigating to
// ensure we don't miss any messages.
CHECK_FAILURE(m_webview->add_WebMessageReceived(
    Microsoft::WRL::Callback<ICoreWebView2WebMessageReceivedEventHandler>(
        [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
{
    wil::unique_cotaskmem_string uri;
    CHECK_FAILURE(args->get_Source(&uri));

    // Always validate that the origin of the message is what you expect.
    if (uri.get() != m_sampleUri)
    {
        return S_OK;
    }
    wil::unique_cotaskmem_string messageRaw;
    CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
    std::wstring message = messageRaw.get();

    if (message.compare(0, 13, L"SetTitleText ") == 0)
    {
        m_appWindow->SetTitleText(message.substr(13).c_str());
    }
    return S_OK;
}).Get(), &m_webMessageReceivedToken));
```

#### <a name="3-roundtrip-webview-to-webview"></a>3. 将 WebView (到 WebView 的往返) 

以下步骤演示 WebView 如何通过显示 Win32 应用的大小从 Win32 主机获取信息并对其进行修改。

1. 在 RoundTrip 下，单击“GetWindowBounds”

按钮下方的框应显示示例应用的边界。

工作原理如下：

1. 单击“获取窗口边界”按钮时，将调用其中的 `GetWindowBounds` 函数 `ScenarioWebMessage.html` 。 它使用 [window.chrome.webview.postMessage () ](https://developer.mozilla.org/docs/Web/API/Window/postMessage) 将消息发送到主机应用程序。

```js
function GetWindowBounds() {
    window.chrome.webview.postMessage("GetWindowBounds");
 }
```

2. 在其中 `ScenarioWebMessage.cpp`，我们使用 [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived) 注册收到的事件处理程序。 验证输入后，事件处理程序会从应用窗口获取窗口边界。 [PostWebMessageAsJson](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasjson) 将边界发送到 Web 应用程序。

```cpp
if (message.compare(L"GetWindowBounds") == 0)
{
    RECT bounds = m_appWindow->GetWindowBounds();
    std::wstring reply =
        L"{\"WindowBounds\":\"Left:" + std::to_wstring(bounds.left)
        + L"\\nTop:" + std::to_wstring(bounds.top)
        + L"\\nRight:" + std::to_wstring(bounds.right)
        + L"\\nBottom:" + std::to_wstring(bounds.bottom)
        + L"\"}";
    CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
}
```

3. 在其中 `ScenarioWebMessage.html`，事件侦听器响应 WindowBounds 消息并显示窗口的边界：

```js
window.chrome.webview.addEventListener('message', arg => {
    if ("WindowBounds" in arg.data) {
        document.getElementById("window-bounds").value = arg.data.WindowBounds;
    }
});
```


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Win32 应用中的 WebView2 入门](../get-started/win32.md)
