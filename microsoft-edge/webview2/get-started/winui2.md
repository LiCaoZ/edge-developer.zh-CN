---
title: '在 WinUI 2 和 UWP 应用中开始使用 WebView2 (UWP) 应用 (公共预览) '
description: 适用于 WinUI 2 应用的 WebView2 入门指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/05/2021
---
# <a name="get-started-with-webview2-in-winui-2-uwp-apps-public-preview"></a>在 WinUI 2 和 UWP 应用中开始使用 WebView2 (UWP) 应用 (公共预览) 

本文将开始在 WinUI 2 和 UWP () 创建第一个 WebView2 应用，并了解 WebView2 的主要功能。 有关各个 WebView2 API 的信息，请参阅 Microsoft Edge [WebView2 API 参考](../webview2-api-reference.md)，然后选择 WinRT 引用链接。 请注意，WinUI2 仅支持 UWP。

> [!NOTE]
> [WinUI 2 程序包](https://www.nuget.org/packages/Microsoft.UI.Xaml/2.8.0-prerelease.210927001)依赖预发布 WebView2 程序包。 为了完全实现 API 兼容性，请使用预览浏览器通道作为运行时，如预览版的 Beta、Dev 或 Canary Microsoft Edge。

> [!Important]
> WebView2 WinUI 2 控件正在积极开发中。 有些功能将丢失或断开。 其中一些包括：
> * 下载 UI -- 虽然下载 UI 功能当前不起作用，但修复问题后，此功能可能会自动显示在应用的 UI 中。  若要保持兼容性，应手动通过截获下载开始事件来禁用 [下载 UI 功能](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2downloadstartingeventargs)。
> * 自动填充 UI
> * 文件选取器对话框
> * 后台音频
> * 打印为 PDF
> * 打印预览
> * 将 COM 对象 (WinRT AddHostObject) 
> * Playready DRM
> * 20H2 Windows之前的设备上的服务工作人员

## <a name="step-0---prerequisites"></a>步骤 0 - 先决条件

1.  安装[Microsoft Visual Studio 2019 版本 16.9](/visualstudio/releases/2019/release-notes-v16.9) 或更高版本。 接受默认值。

1.  默认情况下，Visual Studio代码编辑器中不会显示行号。 若要启用行号，请选择 **"工具** > **""选项"** > **"文本编辑器"** > **"所有语言** > **""行号"**。  然后选择" **确定"**。


## <a name="step-1---install-workloads"></a>步骤 1 - 安装工作负载

1. 打开 Microsoft Visual Studio。
 
1. 单击 **"工具** > **""Get Tools and Features"**。  将**Visual Studio 安装程序**窗口。

1. 在" **工作负载"选项卡** 上，单击 **".NET 桌面开发"**。

1. 单击 **"使用 C++ 进行桌面开发"**。

1. 单击 **"通用Windows平台开发"**。

1. 在右侧，**** > 展开"安装详细信息通用Windows**平台**开发"，然后单击 **"C++ (v142) 通用 Windows工具"**。

   修改 Visual Studio 2019 对话框将显示卡和安装详细信息。  通用平台Windows的安装详细信息显示包含和可选项。

   :::image type="content" source="media/winui2-getting-started-install-workloads.png" alt-text="&quot;修改 Visual Studio 2019&quot;对话框显示卡和安装详细信息。" lightbox="media/winui2-getting-started-install-workloads.png":::

1. 单击 **"修改"**。  Visual Studio安装所选功能。


## <a name="step-2---create-a-uwp-app"></a>步骤 2 - 创建 UWP 应用

1.  在Visual Studio中，单击"**文件** > **"** > **"新建Project"**。  或使用项目的启动Visual Studio，然后选择"**新建项目"**。  将显示 **"新建项目** "对话框。

1.  在" **所有语言** "下拉列表中，单击"C# **"**。

1.  在"**所有平台"** 下拉列表中，单击"Windows **"**。

1.  在" **所有项目类型"** 下拉列表中，单击 **"UWP"**。  选择筛选器后，将列出几种类型的应用模板。

1.  在应用模板列表中，单击"空白**应用 (通用Windows) "**。

    :::image type="complex" source="media/winui2-getting-started-create-project.png" alt-text="&quot;创建新项目&quot;对话框将显示空白应用 (通用窗口) 卡片。" lightbox="media/winui2-getting-started-create-project.png":::
       将显示"新建项目"对话框。  筛选条件以红色突出显示。 通用窗口 (空白应用) 以红色突出显示。
    :::image-end:::

1.  单击“下一步”****。

    将显示 **"配置新项目"** 对话框，用于"空白**应用 (通用Windows) "**。

1.  在"**Project**名称"文本框中，输入项目名称，如 `UWPSampleProject`。

    :::image type="complex" source="media/winui2-getting-started-config-new-project.png" alt-text="&quot;配置新项目&quot;对话框显示空白应用和通用 (文本框Windows) 。" lightbox="media/winui2-getting-started-config-new-project.png":::
       "配置新项目"对话框显示空白应用和通用 (文本框Windows) 。 显示的文本框包括项目名称、位置、解决方案和解决方案名称。
    :::image-end:::

1.  单击“创建”****。  将显示 **"新建通用Windows平台Project**对话框。

1.  单击“确定”****。  如果**设置**几个步骤，则"设置"窗口可能会打开。

1.  在"开发人员 **模式"** 部分，单击" **打开"**。  " **使用开发人员功能** "对话框将打开，以确认打开开发人员模式。

1.  单击 **"是**"**，然后关闭**设置窗口。

    Visual Studio 显示解决方案和项目。

    :::image type="complex" source="media/new-project-created.msft.png" alt-text="生成的项目。" lightbox="media/new-project-created.msft.png":::
        生成的项目
    :::image-end:::

## <a name="step-3---install-the-winui-2-nuget-package"></a>步骤 3 - 安装 WinUI 2 NuGet包

1.  右键单击"解决方案资源管理器"中的项目，然后选择"管理**NuGet包"**。

1.  选择" **浏览"** 选项卡。

1.  选中 **"包括预发布"** 复选框。

1.  在" **搜索"** 框中，输入 `Microsoft.UI.Xaml`，然后选择 **"Microsoft.UI.Xaml"**。  确保" **版本"** 是最新的预发布，然后选择"安装 **"**。

    :::image type="complex" source="media/winui2-nuget-package.msft.png" alt-text="程序包NuGet包管理器。" lightbox="media/winui2-nuget-package.msft.png":::
       NuGet包管理器
    :::image-end:::

    将显示 **"预览** 更改"对话框。

1.  单击“确定”****。 WebView2 SDK 依赖项随 WinUI 2 一起安装。

    <!-- "Microsoft.UI.Xaml" here is equiv to WinUI 2; same team -->

1.  将显示 **"许可证** 接受"对话框。  单击 **"我接受"**。  将显示 `readme.txt` 。

<!-- note: install halted after only WinUI 2 component, it didn't seem to install WebView2 even though that was the 2nd item listed.  assume that's ok now on my machine. -->


## <a name="step-4---instantiate-the-webview2-control-in-xaml-code"></a>步骤 4 - 在 XAML 代码中实例化 WebView2 控件

### <a name="add-the-project-reference-for-the-webview2-control"></a>添加 WebView2 控件的项目引用

1.  `MainPage.xaml`在 文件的 元素中`<Page>`，将以下属性添加到其他属性`xmlns:`的下方。

    ```xml
    xmlns:control="using:Microsoft.UI.Xaml.Controls"
    ```

### <a name="add-the-webview2-control-to-the-grid"></a>将 WebView2 控件添加到网格

1.  `MainPage.xaml`在 文件的 元素中`<Grid>`，添加以下元素：

    ```xml
    <control:WebView2 x:Name="wv2" Source="https://bing.com"/>
    ```

1.  保存文件。 在代码 `MainPage.xaml` 编辑器中的文件上方，将显示 WebView2 内容的预览。

    :::image type="complex" source="media/winui2-getting-started-preview-webview2-content.png" alt-text="WebView2 内容的预览。" lightbox="media/winui2-getting-started-preview-webview2-content.png":::
       WebView2 内容的预览
    :::image-end:::

### <a name="build-and-test-the-webview2-project"></a>生成和测试 WebView2 项目

1.  单击 **"调试** > **""开始调试"**。  应用程序窗口将打开，并简要显示 WebView2 WebUI 网格。

    :::image type="complex" source="media/winui2-getting-started-webview2-grid.png" alt-text="网格在调试期间短暂显示。" lightbox="media/winui2-getting-started-webview2-grid.png":::
       网格在调试期间短暂显示。
    :::image-end:::

1.  片刻之后，应用窗口在 WebUI 2 必应 WebView2 控件中显示网站。

    :::image type="complex" source="media/winui2-getting-started-webview2-with-content.png" alt-text="示例应用显示必应网站。" lightbox="media/winui2-getting-started-webview2-with-content.png":::
       具有 WebView2 控件的示例应用将显示必应网站。 http://www.bing.com
    :::image-end:::

1.  在Visual Studio中，单击 **"调试** > **""停止调试**"以关闭应用窗口。

现在，你可以更改 WebView2 控件的内容以添加你自己的内容。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  [WebView2 开发的最佳做法](../concepts/developer-guide.md)
*  [WebView2 UWP 示例应用](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/webview2_sample_uwp) - WebView2 功能的综合示例。
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
*  [问题 - microsoft-ui-xaml 存储库](https://github.com/microsoft/microsoft-ui-xaml/issues) - 输入特定于 WinUI 的功能请求或 Bug。
