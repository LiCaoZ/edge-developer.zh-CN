---
title: WinUI 3 中的 WebView2 入门 (Windows App SDK) 应用
description: 适用于 WinUI 3 的 WebView2 (Windows App SDK) 指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/05/2021
ms.openlocfilehash: 4ea27866af6b7f613a85c25e5dd7e8ab1b0eb031
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432501"
---
# <a name="get-started-with-webview2-in-winui-3-windows-app-sdk-apps"></a>WinUI 3 中的 WebView2 入门 (Windows App SDK) 应用

本文介绍了如何设置开发工具并创建适用于 WinUI 3 (Windows App SDK) 的初始 WebView2 应用，并一直了解 WebView2 概念。


* 有关入门示例，GitHub：[WinUI3 (WinUI3_GettingStarted/WinUI_Sample.sln 中的 WebView2) ](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/GettingStartedGuides/WinUI3_GettingStarted/README.md)


<!-- ====================================================================== -->
## <a name="step-1---install-visual-studio-and-the-windows-app-sdk"></a>步骤 1 - 安装 Visual Studio 和 Windows App SDK

即使已安装Visual Studio，请阅读以下页面，并可能更新软件。

1. 在新的窗口或选项卡中，打开 [Windows App SDK](/windows/apps/windows-app-sdk/set-up-your-development-environment) 的"安装工具"页面，然后按照该页上的步骤安装 Microsoft Visual Studio，如 Visual Studio 2022。
<!-- clickable: https://docs.microsoft.com/en-us/windows/apps/windows-app-sdk/set-up-your-development-environment -->

1. 如果需要，请参阅设置 _WebView2_ 的开发人员Visual Studio中的[](../how-to/machine-setup.md#install-visual-studio)安装工具。

从该页面返回并继续以下步骤。


**打开开发人员模式：**

1. 当Visual Studio在本文的步骤中的某些时间点打开时，系统可能会提示你为计算机打开开发人员模式。  有关详细信息，请参阅为设备启用开发，[](/windows/apps/get-started/enable-your-device-for-development)请参阅生成桌面应用以_开发Windows_。


<!-- ====================================================================== -->
## <a name="step-2---install-a-preview-channel-of-microsoft-edge"></a>步骤 2 - 安装预览频道Microsoft Edge

1. 安装 [WebView2](https://developer.microsoft.com/microsoft-edge/webview2) 运行时或任何 [Microsoft Edge 预览](https://www.microsoftedgeinsider.com/download)频道 (Beta、Dev 或 Canary) ，安装在 Windows 10 版本 1803 (版本 17134) 或更高版本上。

从该页面返回并继续以下步骤。

<!--
Or, install the WebView2 Runtime, as follows:

1. In a new window or tab, see [Install the WebView2 Runtime](../how-to/machine-setup.md#install-the-webview2-runtime) in _Set up your Dev environment for WebView2_.

Return here and continue with the steps below.
-->


<!-- ====================================================================== -->
## <a name="step-3---create-the-project-in-visual-studio"></a>步骤 3 - 在 Visual Studio

若要创建 WebView2 应用，请首先创建一个基本桌面项目，以创建包含单个主窗口的桌面应用：

1. 打开Visual Studio (，Visual Studio Code) 。

1. 在Visual Studio中，单击 **"新建项目"**。

1. 在项目筛选器菜单中，选择"C# **"**。 **Windows** 和 **WinUI**。

   ![使用项目创建一个新的 WinUI Visual Studio。](media/winui-getting-started-selections.png)

1. Click **Blank App， Packaged (WinUI in Desktop) ** > **Next**.

1. 输入项目名称。

1. 根据需要**更改****位置**和解决方案名称默认值。

1. 单击“创建”****。

1. 在 **"新建通用Windows平台Project**中，选择以下值：

   *  **目标版本**：**Windows 10版本 1903 (版本 18362 **) 或更高版本。

   *  **最低版本**：**Windows 10版本 1803 (版本 17134) **。

1. 单击“确定”****。

   "新建通用Windows平台Project"对话框，包含"目标版本"和"最低版本"的选定值：

   !["新建通用Windows平台Project"对话框，包含"目标版本"和"最低版本"的选定值。](media/winui-getting-started-project-type.png)
       
   解决方案资源管理器显示生成的两个新项目：

   *  **你的项目名称 (桌面) **。  桌面项目包含你的应用的代码。  该文件 `App.xaml.cs` 定义一个 `Application` 表示应用实例的类。 该文件 `MainWindow.xaml.cs` 定义一个 `MainWindow` 类，该类表示应用实例显示的主窗口。  这些类派生自 `Microsoft.UI.Xaml` WinUI 命名空间中的类型。

   *  **你的项目名称 (包) **。  包项目是一Windows应用程序打包Project，配置为将应用构建到 MSIX 包中进行部署。 该项目包含应用的程序包清单，并且默认情况下是解决方案的启动项目。  有关详细信息，请参阅在 Visual Studio 中为 [MSIX](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net) 打包设置桌面应用程序和 [Windows 10。](/uwp/schemas/appxpackage/uapmanifestschema/schema-root)

1. 在解决方案资源管理器中，打开 `MainWindow.xaml`。

1. Select **FileSave** **** >  All () `S` `Ctrl`+`Shift`+to save the project.

1. 按 **F5** 生成并运行项目。


<!-- maintenance link; keep: main copy:
[Install the WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) in _Set up your Dev environment for WebView2_
-->
<!-- ====================================================================== -->
## <a name="step-4---install-the-webview2-sdk"></a>步骤 4 - 安装 WebView2 SDK

WebView2 SDK 在以上步骤中自动安装，因为它作为所安装的 WinUI 程序包的依赖项。  确认为项目安装了 WebView2 SDK，如下所示：

1. 在**NuGet 程序包管理器**步骤中打开的"添加"复选框中，确保选中"包括**预发布"** 复选框。  搜索 **Microsoft.Web.WebView2** (预发布) 然后单击搜索框下方的卡片。  如果需要，请在右侧单击"安装 ("**** 或 **"** 更新) 按钮。

如果需要，请参阅设置 WebView2 的开发人员环境中的安装 [WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) ，然后按照步骤操作。如果需要，请参阅安装 _WebView2_ SDK。  从该页面返回并继续以下步骤。


<!-- ====================================================================== -->
## <a name="step-5---add-a-webview2-control-to-your-project"></a>步骤 5 - 将 WebView2 控件添加到项目中

将 和 `MainWindow.xaml` `MainWindow.xaml.cs` 文件编辑到示例应用的 WebView2 控件，如下所示。

1. 在Visual Studio"资源管理器"中`MainWindow.xaml`，选择在代码编辑器中打开它。

   添加 WebView2 XAML 命名空间，如下所示：

1. 在 文件中 `MainWindow.xaml` ，在 标记内插入以下 `<Window/>` 行：

   ```xml
   xmlns:controls="using:Microsoft.UI.Xaml.Controls"
   ```

   请确保 中的代码 `MainWindow.xaml` 类似于以下内容：

   ```xml
   <Window
         x:Class="WinUI_Sample.MainWindow"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:local="using:WinUI_Sample"
         xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
         xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
         mc:Ignorable="d"
         xmlns:controls="using:Microsoft.UI.Xaml.Controls"
         >

         <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center">
         <Button x:Name="myButton" Click="myButton_Click">Click Me</Button>
         </StackPanel>

   </Window>
   ```

1. 若要添加 WebView2 控件，请将 `<StackPanel>` 标记替换为以下代码。  属性 `Source` 设置在 WebView2 控件中显示的初始 URI。

   ```xml
   <Grid>

      <Grid.RowDefinitions>
         <RowDefinition Height="Auto"/>
         <RowDefinition Height="*"/>
      </Grid.RowDefinitions>
      <Grid.ColumnDefinitions>
         <ColumnDefinition Width="*"/>
         <ColumnDefinition Width="Auto"/>
      </Grid.ColumnDefinitions>

      <controls:WebView2 x:Name="MyWebView"  Grid.Row="1" Grid.ColumnSpan="2"
         Source="https://www.microsoft.com" HorizontalAlignment="Stretch" VerticalAlignment="Stretch"/>

   </Grid>
   ```

1. 在 `MainWindow.xaml.cs`中，注释掉以下行：

   ```xml
      // myButton.Content = "Clicked";
   ```

1. Select **FileSave** >  **All (Ctrl+Shift+S) **， to save the project.

1. 按 **F5** 生成并运行项目。

1. 确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com)。

具有 WebView2 控件的示例应用程序将显示 Microsoft 网站， https://www.microsoft.com:

![示例应用显示 Microsoft 网站。](media/winui-getting-started-part-3.png)


<!-- ====================================================================== -->
## <a name="step-6---add-navigation-controls"></a>步骤 6 - 添加导航控件

若要允许用户控制 WebView2 控件中显示的网页，请向示例应用添加地址栏，如下所示：

1. 在 `MainWindow.xaml`中，将以下代码粘贴 `<Grid>` 到包含 元素的元素 `WebView2` 中：

   ```xml
      <TextBox Name="addressBar" Grid.Column="0"/>
      <Button x:Name="myButton" Grid.Column="1" Click="myButton_Click">Go</Button>
   ```

   请确保文件中 `<Grid>` 元素 `MainWindow.xaml` 与以下内容匹配：

   ```xml
   <Grid>

      <Grid.RowDefinitions>
         <RowDefinition Height="Auto"/>
         <RowDefinition Height="*"/>
      </Grid.RowDefinitions>
      <Grid.ColumnDefinitions>
         <ColumnDefinition Width="*"/>
         <ColumnDefinition Width="Auto"/>
      </Grid.ColumnDefinitions>

      <TextBox Name="addressBar" Grid.Column="0"/>
      <Button x:Name="myButton" Grid.Column="1" Click="myButton_Click">Go</Button>

      <WebView2 x:Name="MyWebView"  Grid.Row="1" Grid.ColumnSpan="2"
         Source="https://www.microsoft.com" HorizontalAlignment="Stretch" VerticalAlignment="Stretch"/>

   </Grid>
   ```

1. 在 `MainWindow.xaml.cs`中，将以下代码复制到 `myButton_Click`。  此代码将 WebView2 控件导航到地址栏中输入的 URL。

   ```csharp
   private void myButton_Click(object sender, RoutedEventArgs e)
   {
      try
      {
         Uri targetUri = new Uri(addressBar.Text);
         MyWebView.Source = targetUri;
      }
      catch (FormatException ex)
      {
         // Incorrect address entered.
      }
   }
   ```

1. Select **FileSave** **** >  All () `S` `Ctrl`+`Shift`+to save the project.

1. 按 **F5** 生成并运行项目。

1. 在地址栏中输入新 URL，然后选择"转到 **"**。  例如，输入 `https://www.bing.com`。

   示例应用显示必应网站。 地址栏显示 URL https://www.bing.com:

   ![示例应用显示必应网站。](media/winui-getting-started-bing.png)

1. 在地址栏中输入不完整的 URL，例如 `bing.com`。

   引发`ArgumentException`异常，因为 URL 不以 或 `http://` 作为起始。`https://`

1. 关闭应用。


<!--
maintenance link (keep)
* [Navigation events for WebView2 apps](../concepts/navigation-events.md) - main copy; update it and then propagate/copy to these h2 sections:
-->
<!-- ====================================================================== -->
## <a name="step-7---navigation-events"></a>步骤 7 - 导航事件

在此部分中，您将添加用于导入 WebView2 核心库的代码。

1. 将以下行添加到 的顶部 `MainWindow.xaml.cs`：

   ```csharp
   using Microsoft.Web.WebView2.Core;
   ```

   承载 WebView2 控件的应用在网页导航过程中侦听 WebView2 控件所引发以下事件：

   * `NavigationStarting`
   * `SourceChanged`
   * `ContentLoading`
   * `HistoryChanged`
   * `NavigationCompleted`
    
   > [!NOTE]
   > 如果发生 HTTP 重定向，则一行中 `NavigationStarting` 有多个事件。
    
   有关详细信息，请参阅 [WebView2 应用的导航事件](../concepts/navigation-events.md)。
    
   发生错误时，将引发以下事件，并显示错误网页：

   * `SourceChanged`
   * `ContentLoading`
   * `HistoryChanged`

   作为如何使用事件的示例 `NavigationStarting` ，请注册用于取消任何非 HTTPS 请求的处理程序，如下所示：

1. 在 `MainWindow.xaml.cs`中，修改构造函数以注册 `EnsureHttps`，并添加 `EnsureHttps` 函数，以便其与以下内容匹配：

   ```csharp
   public MainWindow()
   {
      InitializeComponent();
      MyWebView.NavigationStarting += EnsureHttps;
   }
   
   private void EnsureHttps(WebView2 sender, CoreWebView2NavigationStartingEventArgs args)
   {
      String uri = args.Uri;
      if (!uri.StartsWith("https://"))
      {
         args.Cancel = true;
      }
      else
      {
         addressBar.Text = uri;
      }
   }
   ```

1. Select **FileSave** **** >  All () `S` `Ctrl`+`Shift`+to save the project.

1. 按 **F5** 生成并运行项目。

1. 输入 HTTP URL，例如 `http://microsoft.com`。

   导航被阻止到 HTTP 网站。

1. 输入 HTTPS URL，例如 `https://microsoft.com`。

   HTTPS 网站允许导航。


### <a name="winrt-corewebview2-object-availability"></a>WinRT CoreWebView2 对象可用性

WinRT `CoreWebView2` 对象可能不适用于 WebView2 API 版本。  [WebView2 规范](https://github.com/microsoft/microsoft-ui-xaml-specs/blob/master/active/WebView2/WebView2_spec.md)列出了哪些 API 可用于 WebView2。


<!-- ====================================================================== -->
## <a name="step-8---scripting"></a>步骤 8 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。 你可以任务 WebView2 运行任意 JavaScript 或添加初始化脚本。 在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。 注入的 JavaScript 以特定计时运行，以：

*  创建全局对象后运行注入的 JavaScript。

*  运行注入的 JavaScript，然后再运行 HTML 文档中包含的任何其他脚本。

例如，接下来，添加在用户尝试打开非 HTTPS 网站时发送通知的脚本。  为此，需要将脚本注入到使用 [ExecuteScriptAsync 的 Web 内容中](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync)。

1. 按如下所示 `EnsureHttps` 修改 函数：

   ```csharp
   private void EnsureHttps(WebView2 sender, CoreWebView2NavigationStartingEventArgs args)
   {
      String uri = args.Uri;
      if (!uri.StartsWith("https://"))
      {
         MyWebView.ExecuteScriptAsync($"alert('{uri} is not safe, try an https link')");
         args.Cancel = true;
      }
      else
      {
         addressBar.Text = uri;
      }
   }
   ```

1. Select **FileSave** **** >  All () `S` `Ctrl`+`Shift`+to save the project.

1. 按 **F5** 生成并运行项目。

1. 尝试打开非 HTTPS URL，例如 `http://www.bing.com`。

   应用的 WebView2 控件显示非 HTTPS 网站的警报对话框，指出非 HTTPS `uri` 不安全：

   ![示例应用 WebView2 控件显示非 HTTPS 网站的警报对话框。](media/winui-getting-started-script.png)

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2) - 有关 WebView2 功能的初始 developer.microsoft.com。

本地页面：
* [WebView2 Microsoft Edge](../index.md)简介 - 功能概述。
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
* [管理用户数据文件夹](../concepts/user-data-folder.md)
* [WebView2 的示例代码](../code-samples-links.md) - 存储库 `WebView2Samples` 指南。
* [WebView2 应用的开发最佳做法 开发最佳做法](../concepts/developer-guide.md)

GitHub：
* [WinUI3 中的 WebView2 入门](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/WinUI3_GettingStarted#readme)
* [Spec：WebView2 Xaml 控件](https://github.com/microsoft/microsoft-ui-xaml-specs/blob/master/active/WebView2/WebView2_spec.md) - WebView 控件的 WinUI 3.0 版本。
* [microsoft-ui-xaml 存储库>](https://github.com/microsoft/microsoft-ui-xaml/issues) 问题 - 输入特定于 WinUI 的功能请求或 Bug。

<!--
state why this link is in this tutorial page and what its relevance is, or else delete:
* [Windows Update: FAQ](https://support.microsoft.com/help/12373).
-->
