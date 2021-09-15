---
description: 将 WebView2 用于 WinUI 2 应用入门指南。
title: 'WinUI 2 应用中的 WebView2 入门 (公共预览) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/30/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview2、WebView、webview、winui 应用、winui、edge、CoreWebView2、浏览器控件、edge html、入门、入门、.NET
ms.openlocfilehash: 9910190e2d615e8a6b60bfe5448149c218ff2aca
ms.sourcegitcommit: f361ad8939242611a6ecb188b52780876083b7d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2021
ms.locfileid: "12016673"
---
# <a name="get-started-with-webview2-in-winui-2-apps-public-preview"></a>WinUI 2 应用中的 WebView2 入门 (公共预览) 

本文将开始创建你的第一个 WebView2 应用，并了解 WebView2 的主要功能。 有关单个 WebView2 API 的信息，请导航到["Microsoft Edge WebView2 API](../webview2-api-reference.md)参考"，然后选择 WinRT 引用链接。

> [!NOTE]
> WinUI 2 程序包依赖预发布 WebView2 程序包。  为了完全实现 API 兼容性，请使用预览浏览器通道作为运行时 (，即预览版的 Beta、Dev 或 Canary Microsoft Edge) 。


## <a name="step-1-install-visual-studio"></a>步骤 1\：安装Visual Studio

1.  安装Visual Studio版本 16.9 或更高版本。  可以接受默认值。

1.  默认情况下，Visual Studio代码编辑器中不会显示行号。  若要启用行号，请选择"工具 **""**  >  **选项**  >  **""文本编辑器**  >  **""所有语言**  >  **""行号"。**  然后选择"**确定"。**


## <a name="step-2-install-workloads"></a>步骤 2\：安装工作负载

1.  在Visual Studio"中，选择 **"工具**  >  **""获取工具和功能"。**  将**Visual Studio 安装程序**窗口。

1.  在"**工作负载"选项卡**上，选择 **".NET 桌面开发"。**

1.  选择 **"使用 C++ 进行桌面开发"。**

1.  选择**通用Windows平台开发**。  

1. 在右侧，展开"**** 安装详细信息  >  **通用Windows平台开发**"，然后选择 **"C++ (v142) 通用Windows工具"。**

    :::image type="complex" source="media/winui2-getting-started-install-workloads.png" alt-text="选择要为用户安装的Visual Studio" lightbox="media/winui2-getting-started-install-workloads.png":::
       选择要为用户安装的Visual Studio :::image-end:::

1.  选择" **修改"** 按钮。  Visual Studio安装所选功能。


## <a name="step-3-create-a-uwp-app"></a>步骤 3\：创建 UWP 应用

1.  In Visual Studio， select **File**  >  **New**  >  **Project**.  或使用项目的启动屏幕Visual Studio，然后选择创建新**项目**。  将显示 **"新建项目** "对话框。  

1.  在"**所有语言**"下拉列表中，选择 **"C#"。**

1.  在"**所有平台"** 下拉列表中，选择 **"Windows"。**

1.  在"**所有项目类型"** 下拉列表中，选择 **"UWP"。**  选择筛选器后，将列出多种类型的应用模板。

1.  在应用模板列表中，选择"空白**应用 (通用Windows) "。 **

    :::image type="complex" source="media/winui2-getting-started-create-project.png" alt-text="&quot;创建新项目&quot;对话框" lightbox="media/winui2-getting-started-create-project.png":::
       " **新建项目"** 对话框
    :::image-end:::

1.  选择" **下一步"** 按钮。  将显示**对话框的"配置**新项目"页，其中"空白应用" (**通用Windows) 。 **

1.  在 **"Project**名称"文本框中，输入项目名称，例如 `UWPSampleProject` 。

    :::image type="complex" source="media/winui2-getting-started-config-new-project.png" alt-text="&quot;配置新项目&quot;对话框，用于&quot;空白应用 (通用Windows) &quot;" lightbox="media/winui2-getting-started-config-new-project.png":::
       "**为空白应用配置**新项目"对话框** (通用Windows) **
    :::image-end:::

1.  选择" **创建"** 按钮。  将显示 **"新建通用Windows平台Project**对话框。

1.  选择" **确定"** 按钮。  如果**设置**几个步骤，则"设置"窗口可能会打开。

1.  在"开发人员**模式"部分**，选择"**打开"。**  " **使用开发人员功能** "对话框将打开，以确认打开开发人员模式。

1.  选择"**是**"按钮，然后**关闭设置窗口**。

将显示解决方案和项目。

:::image type="complex" source="media/new-project-created.msft.png" alt-text="生成的项目" lightbox="media/new-project-created.msft.png":::
    生成的项目
:::image-end:::


## <a name="step-4-install-the-winui-2-nuget-package"></a>步骤 4\：安装 WinUI 2 NuGet包

1.  右键单击"解决方案资源管理器"中的项目，然后选择"管理NuGet**包"。**

1.  选择" **浏览"** 选项卡。 

1.  选中 **"包括预发布"** 复选框。

1.  在"**搜索"** 框中，输入 `Microsoft.UI.Xaml` ，然后选择 **"Microsoft.UI.Xaml"。**  确保"**版本"** 是最新的预发行版本，然后选择"安装 **"。**

    :::image type="complex" source="media/winui2-nuget-package.msft.png" alt-text="程序包NuGet包管理器" lightbox="media/winui2-nuget-package.msft.png":::
       程序包NuGet包管理器
    :::image-end:::

    将显示 **"预览** 更改"对话框。  选择" **确定"** 按钮。  请注意，WebView2 SDK 依赖项将和 WinUI 2 一起安装。

<!-- "Microsoft.UI.Xaml" here is equiv to WinUI 2; same team -->

1.  将显示 **"许可证** 接受"对话框。  选择 **"我接受"** 按钮。  `readme.txt`将显示。

<!-- note: install halted after only WinUI 2 component, it didn't seem to install WebView2 even though that was the 2nd item listed.  assume that's ok now on my machine. -->


## <a name="step-5-instantiate-the-webview2-control-in-xaml-code"></a>步骤 5\：在 XAML 代码中实例化 WebView2 控件

### <a name="add-the-project-reference-for-the-webview2-control"></a>添加 WebView2 控件的项目引用 

1.  在 `MainPage.xaml` 文件的 元素中 `<Page>` ，将以下属性添加到其他属性 `xmlns:` 的下方。

    ```xml
    xmlns:control="using:Microsoft.UI.Xaml.Controls" 
    ```

### <a name="add-the-webview2-control-to-the-grid"></a>将 WebView2 控件添加到网格

1.  在 `MainPage.xaml` 文件的 元素 `<Grid>` 中，添加以下元素：

    ```xml
    <control:WebView2 x:Name="wv2" Source="https://bing.com"/>
    ```

1.  保存文件。  在 `MainPage.xaml` 代码编辑器中的文件上方，将显示 WebView2 内容的预览。

    :::image type="complex" source="media/winui2-getting-started-preview-webview2-content.png" alt-text="WebView2 内容的预览" lightbox="media/winui2-getting-started-preview-webview2-content.png":::
       WebView2 内容的预览
    :::image-end:::

### <a name="build-and-test-the-webview2-project"></a>生成和测试 WebView2 项目

1.  在"**调试"** 菜单上，选择"**开始调试"。**  应用程序窗口将打开，并简要显示 WebView2 WebUI 网格。

    :::image type="complex" source="media/winui2-getting-started-webview2-grid.png" alt-text="网格在调试过程中暂时显示" lightbox="media/winui2-getting-started-webview2-grid.png":::
       网格在调试过程中暂时显示
    :::image-end:::

1.  片刻之后，应用窗口在 WebUI 2 的 WebView2 控件中显示 必应.com 网站。

    :::image type="complex" source="media/winui2-getting-started-webview2-with-content.png" alt-text="在 WebView2 控件中必应.com 网站的应用窗口" lightbox="media/winui2-getting-started-webview2-with-content.png":::
       在 WebView2 控件中必应.com 网站的应用窗口
    :::image-end:::

1.  In Visual Studio， on the **Debug** menu， select **Stop Debugging**.  应用程序窗口关闭。

现在，你可以将 WebView2 控件的内容更改为你自己的内容。


## <a name="next-steps"></a>后续步骤  

*   若要了解有关生成 WebView2 应用程序的信息，请导航到 [WebView2 开发最佳做法][WV2BestPractices]。  
*   有关 WebView2 功能的综合示例，请导航到 [WebView2Samples][GithubMicrosoftedgeWebview2samplesMain]。  
*   有关 WebView2 的信息，请导航到["WebView2 资源"。][Webview2IndexNextSteps]  
*   有关 WebView2 API 的详细信息，请导航到 [WebView2 spec][GithubMicrosoftMicrosoftUiXamlSpecsWebview2]。  

    
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队  

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]  

若要发送特定于 WinUI 的功能请求或 Bug，请导航到"问题[- microsoft/microsoft-ui-xaml"，][GithubMicrosoftMicrosoftUiXamlIssues]然后选择"**新问题"。**  

<!-- links -->  
[WV2BestPractices]: ../concepts/developer-guide.md "WebView2 开发最佳实践|Microsoft Docs"  
[Webview2IndexNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 |Microsoft Docs"  
<!-- external links -->
[GithubMicrosoftMicrosoftUiXamlIssues]: https://github.com/microsoft/microsoft-ui-xaml/issues "问题 - microsoft/microsoft-ui-xaml |GitHub"  
[GithubMicrosoftMicrosoftUiXamlSpecsWebview2]: https://github.com/microsoft/microsoft-ui-xaml-specs/blob/master/active/WebView2/WebView2_spec.md "WebView2 规范 - microsoft/microsoft-ui-xaml-specs |GitHub"  
[GithubMicrosoftedgeWebview2samplesMain]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"  
