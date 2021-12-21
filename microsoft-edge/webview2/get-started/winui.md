---
title: 'WinUI 3 应用 SDK (Windows 中的 WebView2) '
description: 适用于 WinUI 3 的 WebView2 (Windows App SDK) 指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview2、WebView、webview、winui 应用、winui、edge、CoreWebView2、浏览器控件、edge html、入门、入门、.NET
ms.date: 11/05/2021
ms.openlocfilehash: 6771ff6ddd02055bb082d296a4ad0a1deee280e9
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286210"
---
# <a name="get-started-with-webview2-in-winui-3-windows-app-sdk"></a>WinUI 3 应用 SDK (Windows 中的 WebView2) 

本文将开始在 WinUI 3 应用 SDK (Windows创建第一个 WebView2) 。 了解 [WebView2 的主要功能](../index.md)。 有关各个 API 详细信息，请参阅 [API 参考](https://github.com/microsoft/microsoft-ui-xaml-specs/blob/master/active/WebView2/WebView2_spec.md)。


## <a name="step-0---set-up-development-environment"></a>步骤 0 - 设置开发环境

1. 按照设置开发环境的步骤 1-4 安装 Visual Studio、配置 NuGet 程序包源并安装 Windows App SDK Extension for Visual Studio。 [](/windows/apps/project-reunion/set-up-your-development-environment)

1. 安装安装在 Windows 10 版本 1803 (版本 17134 或更高版本) [WebView](https://developer.microsoft.com/microsoft-edge/webview2) [Microsoft Edge 2](https://www.microsoftedgeinsider.com/download)运行时或任何非) 渠道。  有关更新或Windows 10，请参阅Windows[更新：常见问题](https://support.microsoft.com/help/12373)。

1.  若要访问所有特定于开发人员Visual Studio功能，请打开开发人员[模式](/windows/uwp/get-started/enable-your-device-for-development)。


## <a name="step-1---create-project"></a>步骤 1 - 创建Project

从包含单个主窗口的基本桌面项目开始。

1.  在Visual Studio中，单击 **"新建项目"。**
1.  在项目筛选器菜单中，选择 **"C#"。** **Windows**、 和**WinUI**。

    :::image type="complex" source="./media/winui-getting-started-selections.png" alt-text="使用项目创建一个新的 WinUI Visual Studio。" lightbox="./media/winui-getting-started-selections.png":::
        使用项目创建一个新的 WinUI Visual Studio
    :::image-end:::

1.  单击 **"空白应用，打包 (桌面设备中的 WinUI) **  >  **下一步"。**
1.  输入项目名称。
1.  根据需要**更改****位置**和解决方案名称默认值。
1.  单击“创建”****。
1.  在 **"新建通用Windows平台Project**中，选择以下值。
    *   **目标版本****：Windows 10版本 1903 (版本 18362**) 或更高版本
    *   **最低版本****：Windows 10版本 1803 (版本 17134) **

1. 单击“确定”****。

    :::image type="complex" source="./media/winui-getting-started-project-type.png" alt-text="&quot;新建通用Windows平台Project&quot;对话框，包含&quot;目标版本&quot;和&quot;最低版本&quot;的选定值。" lightbox="./media/winui-getting-started-project-type.png":::
       "新建通用Windows平台Project"对话框，包含"目标版本"和"最低版本"的选定值。
    :::image-end:::

    解决方案资源管理器显示生成的两个新项目：
    *   **你的项目名称 (桌面) 。 **  桌面项目包含你的应用的代码。  `App.xaml.cs`该文件定义一个 `Application` 表示应用实例的类。 `MainWindow.xaml.cs`该文件定义一个 `MainWindow` 类，该类表示应用实例显示的主窗口。  这些类派生自 `Microsoft.UI.Xaml` WinUI 命名空间中的类型。
    *   **你的项目名称 (包) 。 **  包项目是一Windows应用程序打包Project，配置为将应用构建到 MSIX 包中进行部署。 该项目包含应用的程序包清单，并且默认情况下是解决方案的启动项目。 有关详细信息，请参阅在 Visual Studio 中为[MSIX](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)打包设置桌面应用程序[Windows 10。](/uwp/schemas/appxpackage/uapmanifestschema/schema-root)

1.  在"解决方案资源管理器"中， `MainWindow.xaml` 打开 文件以显示代码。

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

## <a name="step-2---add-a-webview2-control-to-your-project"></a>步骤 2 - 将 WebView2 控件添加到项目中

将 `MainWindow.xaml` 和 `MainWindow.xaml.cs` 文件编辑到示例应用的 WebView2 控件。

1.  在 `MainWindow.xaml` 文件中，若要添加 WebView2 XAML 命名空间，在 标记内插入以下 `<Window/>` 行。

    ```xml
    xmlns:controls="using:Microsoft.UI.Xaml.Controls"
    ```

    确保 中的 `MainWindow.xaml` 代码类似于以下代码段。

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

1.  若要添加 WebView2 控件，请将 `<StackPanel>` 标记替换为以下代码段。  属性 `Source` 设置 WebView2 控件中显示的初始 URI。

    ```xml
    <Grid>

        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>

        <controls:WebView2 x:Name="MyWebView"  Grid.Row="1" Grid.ColumnSpan="2"
            Source="https://www.microsoft.com" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" />

    </Grid>
    ```

1.  在 `MainWindow.xaml.cs` 文件中，注释掉以下行。

    ```xml
        // myButton.Content = "Clicked";
    ```

1.  单击 **"**  >  **文件""保存 (Ctrl+Shift+S) **"以保存项目。

1.  按 **F5**生成并运行项目。

1.  确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com) 。

    :::image type="complex" source="./media/winui-getting-started-part-3.png" alt-text="示例应用显示 Microsoft 网站。" lightbox="./media/winui-getting-started-part-3.png":::
       具有 WebView2 控件的示例应用程序将显示 Microsoft 网站 https://www.microsoft.com 。
    :::image-end:::

## <a name="step-3---add-navigation-controls"></a>步骤 3 - 添加导航控件

若要允许用户控制 WebView2 控件中显示的网页，请向示例应用添加地址栏，如下所示。

1.  在文件中，将以下代码段复制并粘贴 `MainWindow.xaml` 到包含 `<Grid>` 元素的元素 `WebView2` 中。

    ```xml
        <TextBox Name="addressBar" Grid.Column="0"/>
        <Button x:Name="myButton" Grid.Column="1" Click="myButton_Click">Go</Button>
    ```

    请确保文件中 `<Grid>` 元素 `MainWindow.xaml` 与以下代码段匹配。

    ```xml
    <Grid>

        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>

        <TextBox Name="addressBar" Grid.Column="0"/>
        <Button x:Name="myButton" Grid.Column="1" Click="myButton_Click">Go</Button>

        <WebView2 x:Name="MyWebView"  Grid.Row="1" Grid.ColumnSpan="2"
            Source="https://www.microsoft.com" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" />

    </Grid>
    ```

1.  在 `MainWindow.xaml.cs` 文件中，将以下代码段复制到 `myButton_Click` 中。 此代码将 WebView2 控件导航到地址栏中输入的 URL。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  在地址栏中输入新 URL，然后选择"转到 **"。**  例如，输入 `https://www.bing.com` 。

    > [!NOTE]
    > 请确保在地址栏中输入完整 URL。  `ArgumentException` 如果 URL 不以 或 为起始，则会引发 `http://` 异常 `https://` 。

    :::image type="complex" source="./media/winui-getting-started-bing.png" alt-text="示例应用显示必应网站。" lightbox="./media/winui-getting-started-bing.png":::
       示例应用显示必应网站。 地址栏显示 URL https://www.bing.com 。
    :::image-end:::

## <a name="step-4---navigation-events"></a>步骤 4 - 导航事件

在此部分中，您将添加用于导入 WebView2 核心库的代码。

1.  将以下行添加到 的顶部 `MainWindow.xaml.cs` ：

    ```csharp
    using Microsoft.Web.WebView2.Core;
    ```

    承载 WebView2 控件的应用在网页导航过程中侦听 WebView2 控件所引发以下事件：

    *   `NavigationStarting`
    *   `SourceChanged`
    *   `ContentLoading`
    *   `HistoryChanged`
    *   `NavigationCompleted`
    
    > [!NOTE]
    > 如果发生 HTTP 重定向，则一行 `NavigationStarting` 中有多个事件。
    
    有关详细信息，请参阅 [WebView2 的导航事件](../concepts/navigation-events.md)。
    
    发生错误时，将引发以下事件，并显示错误网页：

    *   `SourceChanged`
    *   `ContentLoading`
    *   `HistoryChanged`

    作为如何使用事件的示例，请注册用于取消任何非 `NavigationStarting` HTTPS 请求的处理程序。

1.  在 `MainWindow.xaml.cs` 中，修改构造函数以注册 `EnsureHttps` ，并添加 `EnsureHttps` 函数，以便与以下代码段匹配。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  确保阻止导航到 HTTP 网站，并且允许 HTTPS 网站导航。

> [!NOTE]
> WinRT `CoreWebView2` 对象可能不适用于 WebView2 API 版本。  [WebView2 规范](https://github.com/microsoft/microsoft-ui-xaml-specs/blob/master/active/WebView2/WebView2_spec.md)列出了哪些 API 可用于 WebView2。


## <a name="step-5---scripting"></a>步骤 5 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。 你可以任务 WebView2 运行任意 JavaScript 或添加初始化脚本。 在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。 注入的 JavaScript 以特定计时运行，以：

*   创建全局对象后运行注入的 JavaScript。
*   运行注入的 JavaScript，然后再运行 HTML 文档中包含的任何其他脚本。

例如，添加在用户尝试打开非 HTTPS 网站时发送通知的脚本，如下所示：

1.  修改 `EnsureHttps` 函数以将脚本注入到使用 [ExecuteScriptAsync](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync)的 Web 内容中。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1. 尝试打开非 HTTPS 网站，如 `http://www.bing.com` 。 确保应用在您尝试打开非 HTTPS 网站时显示警告。

:::image type="complex" source="./media/winui-getting-started-script.png" alt-text="示例应用 WebView2 控件显示非 HTTPS 网站的警报对话框。" lightbox="./media/winui-getting-started-script.png":::
   示例应用 WebView2 控件显示非 HTTPS 网站的警报对话框。 警报对话框显示文本，指出非 https 站点不安全，请尝试 https 链接。
:::image-end:::

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  [WebView2 开发的最佳做法](../concepts/developer-guide.md)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
*  [问题 - microsoft-ui-xaml 存储库](https://github.com/microsoft/microsoft-ui-xaml/issues) - 输入特定于 WinUI 的功能请求或 Bug。
