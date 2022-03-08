---
title: WPF 应用中的 WebView2 入门
description: 适用于 WPF 应用的 WebView2 Windows Presentation Foundation (入门) 指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/05/2021
ms.openlocfilehash: bcca560e8a4f3cceb2caa1db650da63066045fc8
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432096"
---
# <a name="get-started-with-webview2-in-wpf-apps"></a>WPF 应用中的 WebView2 入门

本文介绍了如何设置开发工具并创建适用于 Windows Presentation Foundation (WPF) 的初始 WebView2 应用，并一起了解 WebView2 概念。

* 有关入门示例，GitHub：[WPF (WPF_GettingStarted/WPFSample.sln ](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WPF_GettingStarted#readme)) 


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio"></a>步骤 1 - 安装Visual Studio

本教程要求Microsoft Visual Studio代码，Microsoft Visual Studio代码。

1. 安装 [Visual Studio](https://visualstudio.microsoft.com) 2017 或更高版本。  可以接受默认值。


<!-- ====================================================================== -->
## <a name="step-2---install-a-preview-channel-of-microsoft-edge"></a>步骤 2 - 安装预览频道Microsoft Edge

1. 在受支持的[Microsoft Edge](https://www.microsoftedgeinsider.com/download)操作系统 (操作系统) Beta (、Dev 或 Canary) 下载预览体验成员 (预览) ：
   *  Windows 7
   *  Windows 8.1
   *  Windows 10
   *  Windows 11

   我们建议使用 Canary 通道的 Microsoft Edge。  最低要求版本为 82.0.488.0。

<!-- Or, download the [WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/#download-section), or  -->


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-window-webview2-app"></a>步骤 3 - 创建单窗口 WebView2 应用

从包含单个主窗口的基本桌面项目开始。

1. 打开 Microsoft Visual Studio。 

1. 在打开的面板中，单击 **"新建项目"**。  或者，在主窗口Visual Studio，选择 **"文件** > **"** > **"新建Project"**。

1. `WPF App`搜索 。
 
   " **新建项目"** 面板显示搜索结果的筛选 `WPF App` 结果。

1. 单击) 下面首先显示的 **WPF** 应用程序卡 (以使用 **.NET Core/5/6**，或单击) 下面第二个显示的 **WPF 应用 (.NET Framework) ** 卡 (以使用 **.NET Framework**，然后单击"下一步 **"**：

   下图中突出显示的卡片是 **WPF 应用程序：.NET Core WPF 应用程序**：
    
   ![The 'Create a new project' panel with the card selected， 'WPF Application： .NET Core WPF Application'.](media/wpf-getting-started-wpf-core.png)

   或者，下图中突出显示的卡片是 **WPF 应用 (.NET Framework) ：Windows Presentation Foundation客户端应用程序**：

   !["创建新项目"面板，选择卡片"WPF 应用 (.NET Framework) ：Windows Presentation Foundation客户端应用程序"。](media/wpf-getting-started-wpf-fw.png)

   将显示 **"配置新项目** WPF 应用程序"对话框。

   !["配置新项目"WPF 应用程序对话框。](media/wpf-getting-started-create-core.png)

1. 输入**名称Project****位置的值**，然后单击"下一步 **"**。

   将显示 **"其他** 信息"对话框，并包含" **目标框架** "下拉列表：

   ![包含"目标框架"下拉列表的"其他信息"对话框。](media/wpf-getting-started-create-core-add-info.png)

1. 选择 **.NET Core 3.1**、 **5.0**、 **6.0** 或更高版本 (**3.0**) 。  然后，单击“下一步”****。

   将显示 **"配置新项目"** 对话框，针对 **WPF 应用 (.NET 框架) **：

   ![配置新项目 WPF 应用 .NET framework 对话框显示项目名称、位置和解决方案名称文本框。](media/wpf-getting-started-create-fw.png)

1. 输入名称Project**位置****的值**。

1. 在"**框架**"下拉列表中，.NET Framework **4.6.2** 或更高版本。

1. 单击" **创建"** 按钮。

   Visual Studio创建项目。


<!-- maintenance link; keep: main copy:
[Install the WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) in _Set up your Dev environment for WebView2_
-->
<!-- ====================================================================== -->
## <a name="step-4---install-the-webview2-sdk"></a>步骤 4 - 安装 WebView2 SDK

使用 NuGet将 WebView2 SDK 添加到项目中。

1. 在 **"解决方案资源管理器**"中，右键单击项目名称，然后选择"管理NuGet**包：**

   ![右键单击NuGet"管理程序包"命令。](media/wpf-getting-started-mng-nuget.png)

   <!-- todo: The above image is supposed to show the WPF project instead of the WinForms project.  generally, avoid sharing images across multiple .md files -->
   _ (上面的图像应显示 WPF 项目，而不是 WinForms 项目。) _

1. 在左上角，单击"浏览 **"** 选项卡。 在搜索栏中，键入 `Microsoft.Web.WebView2`，然后单击 **Microsoft.Web.WebView2** 卡。

   The NuGet package manager dialog box displays search results， including a **Microsoft.Web.WebView2** card.  该对话框具有版本号和"安装 **"** 按钮。
   
   ![NuGet程序包管理器"对话框显示 Microsoft.Web.WebView2 卡。](media/install-nuget.png)

1. 接受默认版本，然后单击"安装 **"** 按钮。

1. 在" **预览更改** "对话框中，单击"确定 **"**。

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

   项目运行并显示一个空窗口。  这将验证 WebView2 已安装并正常工作，尽管 WebView2 尚未显示任何内容：

   ![空应用窗口。](media/winforms-empty-app.png)


<!-- ====================================================================== -->
## <a name="step-5---create-a-single-webview"></a>步骤 5 - 创建单个 WebView

将 WebView2 控件添加到你的应用。

1. 在 文件中 `MainWindow.xaml` ，若要添加 WebView2 XAML 命名空间，在 标记内插入以下 `<Window/>` 行：

   ```xml
   xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
   ```

1. 确保 中的代码 `MainWindow.xaml` 类似于以下代码：

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

1. 若要添加 WebView2 控件，请将 `<Grid>` 标记替换为以下代码。  属性 `Source` 设置 WebView2 控件中显示的初始 URI。

   ```xml
   <DockPanel>
      <wv2:WebView2 Name="webView"
                     Source="https://www.microsoft.com"
      />
   </DockPanel>
   ```

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

1. 确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com)：

   ![WebView2 控件，用于显示网页 microsoft.com。](media/wpf-getting-started-microsoft.png)


<!-- ====================================================================== -->
## <a name="step-6---navigation"></a>步骤 6 - 导航

允许用户通过向应用添加地址栏来更改 WebView2 控件显示的 URL。

1. 在 文件中 `MainWindow.xaml` ，通过复制并粘贴包含 WebView 的 中的 `<DockPanel>` 以下代码来添加地址栏。  将现有代码保持在新代码段的下方。

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

1. 确保文件的 `<DockPanel>` 部分 `MainWindow.xaml` 与以下代码匹配：

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

1. 在 `MainWindow.xaml.cs`中，若要添加 `CoreWebView2` 命名空间，请将以下代码插入文件顶部：

   ```csharp
   using Microsoft.Web.WebView2.Core;
   ```

1. `MainWindow.xaml.cs`在 文件中，复制以下代码以创建 `ButtonGo_Click` 方法。  此代码将 WebView2 控件导航到地址栏中输入的 URL。

   ```csharp
   private void ButtonGo_Click(object sender, RoutedEventArgs e)
   {
       if (webView != null && webView.CoreWebView2 != null)
       {
           webView.CoreWebView2.Navigate(addressBar.Text);
       }
   }
   ```

1. 将代码直接粘贴到声明 `Public MainWIndow` 后，如以下代码所示：
    
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

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

1. 在地址栏中键入新 URL，然后选择"转到 **"**。  例如，键入 `https://www.bing.com`。

1. 确保 WebView2 控件打开您输入的 URL。

   请确保在地址栏中输入完整 URL。  如果 URL 不 `ArgumentException` 以 或 为起始，应用将生成 `http://` `https://`。

   示例应用程序在地址必应 URL `https://www.bing.com` 显示网站：

   ![应用显示必应网站。](media/wpf-getting-started-bing.png)


<!--
maintenance link (keep)
* [Navigation events for WebView2 apps](../concepts/navigation-events.md) - main copy; update it and then propagate/copy to these h2 sections:
-->
<!-- ====================================================================== -->
## <a name="step-7---navigation-events"></a>步骤 7 - 导航事件

在网页导航期间，WebView2 控件将引发事件。 承载 WebView2 控件的应用侦听以下事件：

*  `NavigationStarting`
*  `SourceChanged`
*  `ContentLoading`
*  `HistoryChanged`
*  `NavigationCompleted`

![导航事件，从新文档到导航开始，到导航完成。](../media/navigation-events.png)

上图显示了事件序列。  导航事件以新文档开始。

### <a name="success-path"></a>成功路径

成功的路径包括完整的事件序列：
1. 导航开始。
1. 源已更改，可能来自同一文档的输入。
1. 内容加载。
1. 历史记录更改。
1. 导航已完成。

有关详细信息，请参阅 [WebView2 应用的导航事件](../concepts/navigation-events.md)。


### <a name="failure-path"></a>失败路径

如果失败，故障路径将直接从导航开始到导航完成，并跳过中间的事件。

发生错误时，将引发以下事件，并可能依赖于导航到错误网页：

* `SourceChanged`
* `ContentLoading`
* `HistoryChanged`


### <a name="redirection"></a>重定向

如果发生 HTTP 重定向，则一行中 `NavigationStarting` 有多个事件。


### <a name="example-demonstrating-navigation-events"></a>演示导航事件的示例

若要演示如何使用事件，请注册用于 `NavigationStarting` 取消任何非 HTTPS 请求的处理程序，如下所示。

1. `MainWindow.xaml.cs`在 文件中，修改构造函数以匹配以下代码的顶部。  在构造函数下方，添加 `EnsureHttps` 函数：

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
    
   在构造函数中， `EnsureHttps` 注册为 WebView2 控件 `NavigationStarting` 上事件的事件处理程序。

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

1. 尝试打开 HTTP 网站。  确保 WebView2 控件保持不变。<!--clarify, blocks site?  what happens in UI?-->

1. 尝试打开 HTTPS 网站。  WebView2 控件允许你打开 HTTPS 网站。


<!-- ====================================================================== -->
## <a name="step-8---scripting"></a>步骤 8 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。  你可以任务 WebView2 运行任意 JavaScript 或添加初始化脚本。  在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。

注入的 JavaScript 以特定计时运行：

*   创建全局对象后运行它。
*   在运行 HTML 文档中包含的任何其他脚本之前运行它。

例如，添加在用户导航到非 HTTPS 网站时发送警报的脚本，如下所示：

1. 修改 函数 `EnsureHttps` 以将脚本注入到使用 [ExecuteScriptAsync](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync) 方法的 Web 内容中。

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

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

1. 当你导航到不使用 HTTPS 的网站时，请确保应用显示一个警报。

   ![显示 http： URL 不安全的消息，建议改为尝试 https： URL。](media/wpf-getting-started-https.png)


<!-- ====================================================================== -->
## <a name="step-9---communication-between-host-and-web-content"></a>步骤 9 - 主机和 Web 内容之间的通信

主机和 Web 内容可以使用以下方式进行通信 `postMessage`：

*  WebView2 控件中的 Web 内容可以使用 向主机发布消息 `window.chrome.webview.postMessage`。  主机使用主机上注册的任何消息 `WebMessageReceived` 处理邮件。

*  使用 或 将消息张贴到 WebView2 控件中的 Web `CoreWebView2.PostWebMessageAsString` 内容 `CoreWebView2.PostWebMessageAsJSON`。 消息被添加到 的处理程序捕获 `window.chrome.webview.addEventListener`。

通信机制使用本机功能将来自 Web 内容的消息传递给主机。

在项目中，当 WebView2 控件导航到 URL 时，它会在地址栏中显示 URL，并通知用户 WebView2 控件中显示的 URL。

1. 在 `MainWindow.xaml.cs`中，更新构造函数并创建函数 `InitializeAsync` 以匹配以下代码。  函数 `InitializeAsync` awaits [EnsureCoreWebView2Async](/dotnet/api/microsoft.web.webview2.wpf.webview2.ensurecorewebview2async)，因为 的初始化 `CoreWebView2` 是异步的。

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

1. 初始化 **CoreWebView2** 后，注册事件处理程序以响应 `WebMessageReceived`。  在 `MainWindow.xaml.cs`中， `InitializeAsync` 使用下面的代码 `UpdateAddressBar` 更新和添加：

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

1. 对于要发送和响应 Web 消息的 WebView2 `CoreWebView2` 控件，在初始化后，主机将执行以下操作：
    1. 将脚本注入 Web 内容，用于注册处理程序以从主机打印消息。
    1. 将脚本注入到将 URL 张贴到主机的 Web 内容。

1. 在 `MainWindow.xaml.cs`中，更新 `InitializeAsync` 以匹配以下代码：

   ```csharp
   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
      webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

      await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
      await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
   }
   ```

1. 选择 **"文件** > **""全部** 保存"以保存项目。

1. 按 **F5** 生成并运行项目。

1. 打开新的 URI 时，WebView2 控件将在地址栏中显示 URI。

   示例应用在地址栏和 Microsoft 网站中显示 URI， https://www.microsoft.com:

   ![示例应用在地址栏和 Microsoft 网站中显示 URI。](media/wpf-getting-started-searchbar.png)

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2) - 有关 WebView2 功能的初始 developer.microsoft.com。

本地页面：
* [WebView2 示例：WPF .NET 浏览器应用](../samples/webview2wpfbrowser.md)
* [管理用户数据文件夹](../concepts/user-data-folder.md)
* [WebView2 的示例代码](../code-samples-links.md) - 存储库 `WebView2Samples` 指南。
* [WebView2 应用的开发最佳做法](../concepts/developer-guide.md)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。

API 参考：
* [API 参考：WebView2.Wpf 命名空间中的 WebView2 类](/dotnet/api/microsoft.web.webview2.wpf.webview2)
* [API 参考：WebView2.Wpf 命名空间](/dotnet/api/microsoft.web.webview2.wpf)

GitHub：
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
