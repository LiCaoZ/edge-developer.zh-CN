---
title: WPF 应用中的 WebView2 入门
description: 适用于 Windows Presentation Foundation (WPF) 应用的 WebView2 入门指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 09/19/2022
ms.openlocfilehash: 9144e67d685806872aeb867d351240c2f969a3ee
ms.sourcegitcommit: 2667d1792515420ba462e12f7b3c00b36bfd70ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2022
ms.locfileid: "12760290"
---
# <a name="get-started-with-webview2-in-wpf-apps"></a>WPF 应用中的 WebView2 入门

本文介绍如何设置开发工具并为Windows Presentation Foundation (WPF) 创建初始 WebView2 应用，并了解 WebView2 概念。

在本教程中，你将使用 **WPF 应用程序**或 **WPF 应用 (.NET Framework) **项目模板创建 WPF 应用，然后为项目安装 WebView2 SDK 以添加 WebView2。


#### <a name="completed-project"></a>已完成的项目

已完成的版本<!--TODO: what date?--> 此教程项目的 **WebView2Samples** 存储库中提供：
*  示例名称： **WPF_GettingStarted**
*  存储库目录： [WPF_GettingStarted](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/GettingStartedGuides/WPF_GettingStarted#readme)
*  解决方案文件： **WPFSample.sln**


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio-with-net-support"></a>步骤 1 - 使用 .NET 支持安装 Visual Studio

本教程需要 Microsoft Visual Studio，而不是 Microsoft Visual Studio Code。  本文主要介绍如何使用 Visual Studio 2022。

1. 安装 [Visual Studio](https://visualstudio.microsoft.com)。<!--strong default is 2022-->  安装 **.NET 桌面开发** 支持，以获取所需的项目模板，如下所示。

1. 如果在 Visual Studio 启动屏幕中，请滚动到 **“创建新项目** ”对话框的底部，然后单击链接 **“打开而不使用代码**”。  Visual Studio 随即打开。

1. 在 Visual Studio 中，选择 **“工具** > **获取工具和功能**”。  将打开**Visual Studio 安装程序窗口**，并打开 **“修改**”对话框。

1. 选择 **.NET 桌面开发** 工作负载，以便其上有一个复选标记。

1. 在右侧**包含****的“安装详细信息** > **.NET 桌面开发** > ”部分中，确保**列出了 .NET 桌面开发工具**和 **.NET Framework 4.7.2 开发工具**，其旁边有一个复选标记。

1. 在右侧的 **“安装详细信息** > **.NET 桌面开发** > **可选** ”部分中：

   * 如果使用的是 Visual Studio 2022，请确保选择了 **适用于 .NET 的开发工具** ：

   ![Visual Studio 2022“修改”对话框，用于安装用于“.NET 桌面开发”的模板](wpf-images/install-dotnet-support-project-templates.png)

   * 如果使用的是 Visual Studio 2019，请确保选择了 **.NET 开发工具** ：

   ![Visual Studio 2019“修改”对话框，用于安装用于“.NET 桌面开发”的模板](wpf-images/install-dotnet-support-project-templates-2019.png)

1. 单击“ **修改”** 按钮。

本教程还适用于 Visual Studio 2017。  请参阅 [Visual Studio 旧版下载](https://visualstudio.microsoft.com/vs/older-downloads/)。  安装 .NET 支持，以获取所需的项目模板，类似于上述步骤。


<!-- ====================================================================== -->
## <a name="step-2---install-a-preview-channel-of-microsoft-edge"></a>步骤 2 - 安装 Microsoft Edge 的预览频道

1. 在受支持的操作系统 [上下载任何 Microsoft Edge 预览体验成员 (预览) 频道](https://www.microsoftedgeinsider.com/download) (Beta、Dev 或 Canary) ， (OS) ：
   *  Windows 7
   *  Windows 8.1
   *  Windows 10
   *  Windows 11

   建议使用 Microsoft Edge 的 Canary 通道。  所需的最低版本为 82.0.488.0。


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-window-webview2-app"></a>步骤 3 - 创建单窗口 WebView2 应用

首先创建包含单个主窗口的基本桌面项目。

1. 决定是否 (较新) 创建 **.NET Core/5/6** 项目，还是 (较旧 **) 创建 WPF 应用 (.NET Framework) **项目。  有关详细信息，请参阅：
   * [什么是 .NET 中的 .NET 历史记录](/dotnet/core/introduction#net-history)_？简介和概述_。
   * 维基百科的 [.NET](https://en.wikipedia.org/wiki/.NET)。

1. 请按照以下适用部分进行操作。


#### <a name="creating-a-net-core56-project"></a>创建 .NET Core/5/6 项目

如果要创建 .NET Core/5/6 项目，请执行以下步骤。  否则，请跳到[创建 WPF 应用 (.NET Framework) 项目](#creating-a-wpf-app-net-framework-project)。

1. 打开 Microsoft Visual Studio，例如 Visual Studio 2022。

1. 在打开面板中，单击 **“新建项目**”。  或者，在 Visual Studio 主窗口中，选择 **“文件** > **新建** > **项目**”。  将打开 **“创建新项目** ”对话框。

1. 在 **“搜索模板** ”文本框中，键入 `WPF Application`。  **“新建项目**”面板显示与输入的文本匹配的已安装项目模板。  本文演示 C# 而不是 VB 对话框;WebView2 支持这两种语言。

1. 如果使用的是 Visual Studio 2022，请单击标题为 **WPF 应用程序** 的项目模板和用于 **创建 .NET WPF 应用程序的说明文本 A 项目**：

   ![在 2022“创建新项目”对话框中选择模板“WPF 应用程序：.NET Core WPF 应用程序”](wpf-images/template-wpf-app-core-2022.png)

   如果使用的是 Visual Studio 2019，请单击标题为 **WPF 应用程序** 的项目模板和用于 **创建 .NET Core WPF 应用程序的说明文本 A 项目**：

   ![在 2019“创建新项目”对话框中选择模板“WPF 应用程序：.NET Core WPF 应用程序”](media/wpf-getting-started-wpf-core.png)
   <!--todo: after move png to article's dedicated images dir, change filename like for vs2022 above -->

   如果未列出上述项目模板，请 [参阅步骤 1 - 使用上面的 .NET 支持安装 Visual Studio](#step-1---install-visual-studio-with-net-support) ，以安装 **.NET 桌面开发工具**。

1. 单击“下一步”**** 按钮。

   “ **配置新项目：WPF 应用程序** ”对话框随即打开：

   ![.NET Core/5/6 项目的“配置新项目：WPF 应用程序”对话框](wpf-images/config-new-core-project-2022.png)
   <!-- ok to delete png media/wpf-getting-started-create-core.png -->

1. 在 **“项目名称** ”文本框中，输入项目名称，例如 **MyWpfDotnetCoreWv2App**。

1. 在 **“位置** ”文本框中，选择本地驱动器上的路径，例如 `C:\Users\myusername\Documents\MyProjects`，然后单击“ **下一步** ”按钮。

   随即显示“ **其他信息** ”对话框，其中包含 **“目标框架”** 下拉列表：

   ![包含“目标框架”下拉列表的“其他信息”对话框](media/wpf-getting-started-create-core-add-info.png)

1. 选择 **.NET Core 3.1** 或更高版本，例如 **.NET 6.0**。   (请勿选择 **.NET Core 3.0**.) 然后单击 **“创建”** 按钮。

   初始 .NET Core WPF 应用程序项目在 Visual Studio 中打开：

   ![使用 .NET Core WPF 应用程序模板在 Visual Studio 2022 中初始项目](wpf-images/initial-project-core-2022.png)

跳到 [步骤 4 - 在下面没有 WebView2 的情况下生成并运行初始项目](#step-4---build-and-run-the-initial-project-without-webview2) 。


<!-- project template title: WPF App (.NET Framework) -->
#### <a name="creating-a-wpf-app-net-framework-project"></a>创建 WPF 应用 (.NET Framework) 项目

如果要创建 WPF 应用 (.NET Framework) 项目，请执行以下步骤。  否则，请跳到 [步骤 4 - 在没有 WebView2 的情况下生成并运行初始项目](#step-4---build-and-run-the-initial-project-without-webview2)。

1. 打开 Microsoft Visual Studio，例如 Visual Studio 2022。

1. 在打开面板中，单击 **“新建项目**”。  或者，在 Visual Studio 主窗口中，选择 **“文件** > **新建** > **项目**”。  将打开 **“创建新项目** ”对话框。
   <!-- resume here, using 2022 ~ -->

1. 在 **“搜索模板** ”文本框中，键入 `WPF App`。  **“新建项目**”面板显示与输入的文本匹配的已安装项目模板。  本文演示 C# 而不是 VB 对话框;WebView2 支持这两种语言。

1. 单击标题为 **WPF 应用 (.NET Framework) **的项目模板，并在**客户端应用程序Windows Presentation Foundation**说明文本：

   ![在 2022“创建新项目”对话框中选择模板“WPF 应用”](wpf-images/select-fw-project-template-2022.png)

   如果未列出上述项目模板，请 [参阅步骤 1 - 使用上面的 .NET 支持安装 Visual Studio](#step-1---install-visual-studio-with-net-support) ，以安装 **.NET 桌面开发工具**。

1. 单击“下一步”**** 按钮。

   “**配置新项目：WPF 应用 (.NET Framework) **”对话框随即打开：

   ![“配置新项目：WPF 应用 (.NET Framework) ”对话框](media/wpf-getting-started-create-fw.png)

1. 在 **“项目名称** ”文本框中，输入项目名称，例如 **MyWpfDotnetFwkWv2App**。

1. 在 **“位置** ”文本框中，选择本地驱动器上的路径，例如 `C:\Users\myusername\Documents\MyProjects`。

1. 在 **“框架”** 下拉列表中，选择 **.NET Framework 4.6.2** 或更高版本。

1. 单击 **“创建”** 按钮。

   初始 WPF 应用 (.NET Framework) 项目在 Visual Studio 中打开：

   ![使用 WPF 应用 (.NET Framework) 模板在 Visual Studio 2022 中初始项目](wpf-images/initial-project-dotnet-framework-2022.png)


<!-- ====================================================================== -->
## <a name="step-4---build-and-run-the-initial-project-without-webview2"></a>步骤 4 - 在没有 WebView2 的情况下生成并运行初始项目

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

   项目运行，并显示一个空窗口：

   ![没有 WebView2 的空应用窗口](wpf-images/empty-app-without-webview2.png)

   可能需要安装选定的.NET Framework版本，如下所示。

1. 如果应用未打开，请选择 **“调试** > **开始而不调试**”。

   如果尚未安装所选版本的.NET Framework，可能会收到以下对话框：“无法启动此应用程序。  应用程序需要以下.NET Framework版本之一：NETFramework，Version=v4.8.1 - 是否立即安装此.NET Framework版本？

1. 如果收到这样的对话框，请转到[“下载.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework)并下载，然后安装所需的开发**人员包**版本 (而不是**运行时**) 。  例如，下载 `ndp481-devpack-enu.exe` 到 `C:\Users\username\Downloads`文件，然后双击该文件进行安装。

1. 如果出现提示，请重启计算机：

   ![重新启动以安装.NET Framework](wpf-images/restart-to-install-dotnet-framework.png)

1. 转到下载的文件（如 `ndp481-devpack-enu.exe` in`C:\Users\username\Downloads`），然后再次双击下载的文件以安装.NET Framework开发人员包。  将显示 **“成功** ”对话框：

   ![安装成功以安装.NET Framework](wpf-images/dotnet-framework-setup-successful.png)

1. 如果出现提示，请重新启动计算机。

1. 打开 Visual Studio，并打开创建的解决方案。

1. 按 `F5` 下以运行初始应用 (如) 上所示，但不包括 WebView2 SDK。

1. 关闭初始应用。


<!-- maintenance link; keep: main copy:
[Install the WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) in _Set up your Dev environment for WebView2_
-->
<!-- ====================================================================== -->
## <a name="step-5---install-the-webview2-sdk"></a>步骤 5 - 安装 WebView2 SDK

在 Visual Studio 中，使用 NuGet 包管理器将 WebView2 SDK 添加到项目，如下所示：

1. 在**解决方案资源管理器**中，右键单击基于 .NET (Core) 或.NET Framework项目模板) 的项目名称 (，然后选择 **“管理 NuGet 包**”：

   ![右键单击菜单上的“管理 NuGet 包”命令](./wpf-images/manage-nuget-packages-menuitem.png)

1. 在左上角，单击“ **浏览”** 选项卡。 在搜索栏中键入 `Microsoft.Web.WebView2`，然后单击 **Microsoft.Web.WebView2** 包。

   NuGet 包管理器对话框显示搜索结果，包括 **Microsoft.Web.WebView2** 包。  对话框具有版本号和 **“安装”** 按钮。
   
   ![NuGet 包管理器对话框显示 Microsoft.Web.WebView2 包](media/install-nuget.png)

1. 接受默认版本，然后单击 **“安装** ”按钮。

1. 在 **“预览更改** ”对话框中，单击 **“确定”** 按钮。

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

   项目运行，并显示一个空窗口。  这会验证 WebView2 是否已安装并正常工作，尽管 WebView2 尚无要显示的内容：

   ![使用 WebView2 SDK 的空应用窗口](wpf-images/empty-app-with-webview2-sdk.png)

1. 关闭应用。


<!-- ====================================================================== -->
## <a name="step-6---create-a-single-webview2-control"></a>步骤 6 - 创建单个 WebView2 控件

将 WebView2 控件添加到应用。

1. 在文件中 `MainWindow.xaml` ，若要添加 WebView2 XAML 命名空间，请在标记中 `<Window/>` 插入以下行：

   ```xml
   xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
   ```

1. 请确保其中 `MainWindow.xaml` 的代码类似于以下代码：

   ```xml
   <Window x:Class="WPF_Getting_Started.MainWindow"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
         xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:local="clr-namespace:{YOUR PROJECT NAME}"
         xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
         mc:Ignorable="d"
         Title="MainWindow"
         Height="450"
         Width="800"
   >
      <Grid>

      </Grid>
   </Window>
   ```

1. 若要添加 WebView2 控件，请将 `<Grid>` 标记替换为以下代码。  该 `Source` 属性设置 WebView2 控件中显示的初始 URI。

   ```xml
   <DockPanel>
      <wv2:WebView2 Name="webView"
                     Source="https://www.microsoft.com"
      />
   </DockPanel>
   ```

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

1. 确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com)：

   ![WebView2 控件，显示来自 microsoft.com 的网页内容](media/wpf-getting-started-microsoft.png)


<!-- ====================================================================== -->
## <a name="step-7---navigation"></a>步骤 7 - 导航

通过向应用添加地址栏，使用户能够更改 WebView2 控件显示的 URL。

1. 在文件中 `MainWindow.xaml` ，通过复制并粘贴包含 WebView2 控件的 `<DockPanel>` 以下代码来添加地址栏。  将现有代码保留在新代码片段下方。

   ```xml
   <DockPanel DockPanel.Dock="Top">
       <Button x:Name="ButtonGo"
                 DockPanel.Dock="Right"
                 Click="ButtonGo_Click"
                 Content="Go"
       />
       <TextBox Name="addressBar"/>
   </DockPanel>
   ```

1. 确保 `<DockPanel>` 文件的 `MainWindow.xaml` 节与以下代码匹配：

   ```xml
   <DockPanel>
       <DockPanel DockPanel.Dock="Top">
           <Button x:Name="ButtonGo" DockPanel.Dock="Right" Click="ButtonGo_Click" Content="Go"/>
           <TextBox Name = "addressBar"/>
       </DockPanel>
       <wv2:WebView2 Name = "webView"
                     Source = "https://www.microsoft.com"
       />
   </DockPanel>
   ```

1. 在 `MainWindow.xaml.cs`其中，若要添加 `CoreWebView2` 命名空间，请在文件顶部插入以下代码：

   ```csharp
   using Microsoft.Web.WebView2.Core;
   ```

1. 在文件中 `MainWindow.xaml.cs`，复制以下代码以创建 `ButtonGo_Click` 该方法。  此代码将 WebView2 控件导航到地址栏中输入的 URL。

   ```csharp
   private void ButtonGo_Click(object sender, RoutedEventArgs e)
   {
       if (webView != null && webView.CoreWebView2 != null)
       {
           webView.CoreWebView2.Navigate(addressBar.Text);
       }
   }
   ```

1. 直接在声明之后 `Public MainWIndow` 粘贴代码，如以下代码所示：
    
   ```csharp
   namespace WpfApp1
   {
      /// <summary>
      /// Interaction logic for MainWindow.xaml
      /// </summary>
      public partial class MainWindow : Window
      {
         public MainWindow()
         {
               InitializeComponent();
         }
         void ButtonGo_Click(object sender, RoutedEventArgs e)
         {
               if (webView != null && webView.CoreWebView2 != null)
               {
                  webView.CoreWebView2.Navigate(addressBar.Text);
               }
         }
      }
   }
   ```

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

1. 在地址栏中键入新 URL，然后选择 **“Go**”。  例如，键入 `https://www.bing.com`。

1. 确保 WebView2 控件打开输入的 URL。

   请确保在地址栏中输入完整的 URL。  应用生成 URL `ArgumentException` 未以或`https://`开头`http://`的 URL。

   示例应用在地址栏中显示包含 URL `https://www.bing.com` 的必应网站：

   ![应用显示必应网站](media/wpf-getting-started-bing.png)


<!--
maintenance link (keep)
* [Navigation events for WebView2 apps](../concepts/navigation-events.md) - main copy; update it and then propagate/copy to these h2 sections:
-->
<!-- ====================================================================== -->
## <a name="step-8---navigation-events"></a>步骤 8 - 导航事件

在网页导航期间，WebView2 控件会引发事件。 托管 WebView2 控件的应用侦听以下事件：

*  `NavigationStarting`
*  `SourceChanged`
*  `ContentLoading`
*  `HistoryChanged`
*  `NavigationCompleted`

![导航事件，从新文档到导航启动，通过导航完成](../media/navigation-events.png)

上图显示了事件序列。  导航事件以新文档开头。

### <a name="success-path"></a>成功路径

成功的路径包括事件的完整序列：
1. 导航开始。
1. 源已更改，可能来自同一文档的输入。
1. 内容加载。
1. 历史记录更改。
1. 导航已完成。

有关详细信息，请参阅 [WebView2 应用的导航事件](../concepts/navigation-events.md)。


### <a name="failure-path"></a>故障路径

如果出现故障，则故障路径将直接从导航开始，到导航完成，跳过干预事件。

发生错误时，会引发以下事件，并且可能依赖于导航到错误网页：

* `SourceChanged`
* `ContentLoading`
* `HistoryChanged`


### <a name="redirection"></a>重 定向

如果发生 HTTP 重定向，则一行中有多个 `NavigationStarting` 事件。


### <a name="example-demonstrating-navigation-events"></a>演示导航事件的示例

若要演示如何使用事件，请为此 `NavigationStarting` 注册处理程序，取消任何非 HTTPS 请求，如下所示。

1. 在文件中 `MainWindow.xaml.cs` ，修改构造函数以匹配以下代码的上一部分。  在构造函数下方添加函数 `EnsureHttps` ：

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        webView.NavigationStarting += EnsureHttps;
    }
    
    void EnsureHttps(object sender, CoreWebView2NavigationStartingEventArgs args)
    {
        String uri = args.Uri;
        if (!uri.StartsWith("https://"))
        {
            args.Cancel = true;
        }
    }
    ```
    
   在构造函数中， `EnsureHttps` 在 WebView2 控件上 `NavigationStarting` 注册为事件处理程序。

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

1. 尝试打开 HTTP 站点。  确保 WebView2 控件保持不变。<!--clarify, blocks site?  what happens in UI?-->

1. 尝试打开 HTTPS 站点。  使用 WebView2 控件可以打开 HTTPS 站点。


<!-- ====================================================================== -->
## <a name="step-9---scripting"></a>步骤 9 - 脚本

可以在运行时使用主机应用将 JavaScript 代码注入 WebView2 控件。  可以让 WebView2 运行任意 JavaScript 或添加初始化脚本。  注入的 JavaScript 适用于所有新的顶级文档和任何子帧，直到删除 JavaScript。

注入的 JavaScript 使用特定的计时运行：

*   创建全局对象后运行它。
*   在运行 HTML 文档中包含的任何其他脚本之前运行它。

例如，添加在用户导航到非 HTTPS 站点时发送警报的脚本，如下所示：

1. 修改函数以 `EnsureHttps` 将脚本注入使用 [ExecuteScriptAsync 方法的](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync) Web 内容。

   ```csharp
   void EnsureHttps(object sender, CoreWebView2NavigationStartingEventArgs args)
   {
      String uri = args.Uri;
      if (!uri.StartsWith("https://"))
      {
         webView.CoreWebView2.ExecuteScriptAsync($"alert('{uri} is not safe, try an https link')");
         args.Cancel = true;
      }
   }
   ```

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

1. 导航到不使用 HTTPS 的网站时，请确保应用显示警报。

   ![显示 http： URL 不安全的消息，并建议尝试 https：URL](media/wpf-getting-started-https.png)


<!-- ====================================================================== -->
## <a name="step-10---communication-between-host-and-web-content"></a>步骤 10 - 主机和 Web 内容之间的通信

主机和 Web 内容可以使用以下方式进行 `postMessage`通信：

*  WebView2 控件中的 Web 内容可以使用 `window.chrome.webview.postMessage`以下方式将消息发布到主机。  主机使用在主机上注册 `WebMessageReceived` 的任何消息来处理消息。

*  主机使用或`CoreWebView2.PostWebMessageAsJSON`将消息发布到 WebView2 控件`CoreWebView2.PostWebMessageAsString`中的 Web 内容。 邮件由添加到 `window.chrome.webview.addEventListener`的处理程序捕获。

通信机制使用本机功能将消息从 Web 内容传递到主机。

在项目中，当 WebView2 控件导航到 URL 时，它会在地址栏中显示 URL，并向 WebView2 控件中显示的 URL 用户发出警报。

1. 在 `MainWindow.xaml.cs`其中，更新构造函数并创建一个 `InitializeAsync` 函数以匹配以下代码。  函 `InitializeAsync` 数等待 [EnsureCoreWebView2Async](/dotnet/api/microsoft.web.webview2.wpf.webview2.ensurecorewebview2async)，因为初始化是异步的 `CoreWebView2` 。

   ```csharp
   public MainWindow()
   {
      InitializeComponent();
      webView.NavigationStarting += EnsureHttps;
      InitializeAsync();
   }

   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
   }
   ```

1. **初始化 CoreWebView2** 后，注册要响应`WebMessageReceived`的事件处理程序。  在 `MainWindow.xaml.cs`中，使用以下代码更新 `InitializeAsync` 和添加 `UpdateAddressBar` ：

   ```csharp
   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
      webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;
   }

   void UpdateAddressBar(object sender, CoreWebView2WebMessageReceivedEventArgs args)
   {
      String uri = args.TryGetWebMessageAsString();
      addressBar.Text = uri;
      webView.CoreWebView2.PostWebMessageAsString(uri);
   }
   ```

1. 对于要发送和响应 Web 消息的 WebView2 控件，初始化后 `CoreWebView2` ，主机将执行以下操作：
    1. 将脚本注入到注册处理程序以从主机打印消息的 Web 内容。
    1. 将脚本注入到将 URL 发布到主机的 Web 内容。

1. 在 `MainWindow.xaml.cs`其中，更新 `InitializeAsync` 以匹配以下代码：

   ```csharp
   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
      webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

      await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
      await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
   }
   ```

1. 选择“**全部保存****文件** > ”以保存项目。

1. 按 **F5** 生成并运行项目。

1. 打开新 URI 时，WebView2 控件会在地址栏中显示 URI。

   示例应用在地址栏和 Microsoft 网站中显示 URI， https://www.microsoft.com:

   ![示例应用在地址栏和 Microsoft 网站中显示 URI](media/wpf-getting-started-searchbar.png)

恭喜你，你构建了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

developer.microsoft.com：
* [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2) - developer.microsoft.com 的 WebView2 功能的初始简介。

本地页面：
* [WPF 示例应用](../samples/webview2wpfbrowser.md)
* [管理用户数据文件夹](../concepts/user-data-folder.md)
* [WebView2 示例代码](../code-samples-links.md) - 存储库指南 `WebView2Samples` 。
* [WebView2 应用的开发最佳做法](../concepts/developer-guide.md)
* [另请参阅](../index.md#see-also) _Microsoft Edge WebView2 简介_。

API 参考：
* [API 参考：WebView2.Wpf 命名空间中的 WebView2 类](/dotnet/api/microsoft.web.webview2.wpf.webview2)
* [API 参考：WebView2.Wpf 命名空间](/dotnet/api/microsoft.web.webview2.wpf)

GitHub：
* [WebView2Samples 存储库> WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser)
