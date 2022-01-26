---
title: WPF 应用中的 WebView2 入门
description: 适用于 WPF 应用的 WebView2 Windows Presentation Foundation (入门) 指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/05/2021
ms.openlocfilehash: 88670412d50ab0b0a891441fbb9891646e805de0
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12323647"
---
# <a name="get-started-with-webview2-in-wpf-apps"></a>WPF 应用中的 WebView2 入门

在本文中，开始在 WPF Windows Presentation Foundation (WPF) 创建第一个 WebView2 应用，并了解[WebView2 的主要功能](https://developer.microsoft.com/microsoft-edge/webview2)。 有关各个 API 详细信息，请参阅 [API 参考](/dotnet/api/microsoft.web.webview2.wpf)。


<!-- ====================================================================== -->
## <a name="step-0---prerequisites"></a>步骤 0 - 先决条件

安装以下必备组件列表，然后再继续。

1.  [Visual Studio](https://visualstudio.microsoft.com) 2017 或更高版本。

1.  [WebView2](https://developer.microsoft.com/microsoft-edge/webview2)运行时，或任何 Microsoft Edge [Insider (preview) Channel](https://www.microsoftedgeinsider.com/download) (Beta、Dev 或 Canary) 安装在受支持的操作系统 (OS) 。 当前受支持的操作系统列表是 Windows 11、Windows 10、Windows 8.1 和 Windows 7。

    > [!NOTE]
    > WebView2 团队建议使用 Canary 通道，最低要求版本为 82.0.488.0。


<!-- ====================================================================== -->
## <a name="step-1---create-a-single-window-app"></a>步骤 1 - 创建单窗口应用

从包含单个主窗口的基本桌面项目开始。

1.  打开 Microsoft Visual Studio。 

1.  在打开的面板中，单击 **"新建项目**"，或在应用程序中单击 **"新建**  >  ****  >  **Project"。**

1. 搜索 WPF 应用。
 
1. 单击**WPF 应用 (.NET Core) **或**WPF 应用 (.NET Framework) **卡。

    :::image type="complex" source="./media/wpf-getting-started-wpf-core.png" alt-text="创建新项目面板将显示 WPF 应用搜索结果，包括 WPF 核心卡。":::
      创建新项目面板将显示 WPF 应用搜索结果。 突出显示的按钮是 WPF 应用 .NET core Windows Presentation Foundation适用于 C#、XAML、Windows 和桌面的客户端应用程序。 该对话框显示下一个按钮。
    :::image-end:::

    :::image type="complex" source="./media/wpf-getting-started-wpf-fw.png" alt-text="创建新项目面板将显示 WPF 应用搜索结果，包括 WPF 框架卡。":::
      创建新项目面板将显示 WPF 应用搜索结果。 突出显示的按钮是 WPF 应用 .NET core Windows Presentation Foundation客户端应用程序，C#、Windows桌面。 该对话框显示下一个按钮。
          :::image-end:::

1.  对于**WPF 应用 A0.NET 核心) **输入名称Project**位置**的值****，然后单击下一**步**。

    :::image type="complex" source="./media/wpf-getting-started-create-core.png" alt-text="配置新项目 WPF 应用程序对话框将显示项目名称、位置和解决方案名称文本框。":::
      配置新项目 WPF 应用程序对话框将显示项目名称、位置和解决方案名称文本框。 对话框显示"后退"和"下一步"按钮。
    :::image-end:::

    1.  选择 **".NET Core 3.1"** 或"更高版本"。

        :::image type="complex" source="./media/wpf-getting-started-create-core-add-info.png" alt-text="其他信息对话框显示目标框架的下拉菜单。":::
          "其他信息"对话框显示目标框架的下拉菜单。 选项为 .NET core 3.0、3.1。 和 5.0。 对话框显示后退并创建按钮。
        :::image-end:::

1. 对于**WPF 应用 (.NET Framework) **输入 Project**和** **Location**的值，然后选择".NET Framework **4.6.2**或更高版本"。
 
    :::image type="complex" source="./media/wpf-getting-started-create-fw.png" alt-text="配置新项目 WPF 应用 .NET framework 对话框显示项目名称、位置和解决方案名称文本框。":::
      配置新项目 WPF 应用 .NET framework 对话框显示项目名称、位置和解决方案名称文本框。 框架下拉菜单显示 .NET framework 版本，包括 4.6.1 和 4.7.2。 该对话框显示后退并创建按钮。
    :::image-end:::

1.  单击 **"创建** "继续。

    Visual Studio创建项目。


<!-- ====================================================================== -->
## <a name="step-2---install-webview2-sdk"></a>步骤 2 - 安装 WebView2 SDK

使用 NuGet将 WebView2 SDK 添加到项目中。

1. 在 **"解决方案资源管理器**"中，右键单击项目名称，然后选择"管理**NuGet包"。**

    :::image type="complex" source="./media/wpf-getting-started-mng-nuget-reduced.png" alt-text="上下文菜单显示管理NuGet包。" lightbox="./media/wpf-getting-started-mng-nuget.png":::
       上下文菜单显示许多选项，包括"管理NuGet包"。
    :::image-end:::

1.  单击**浏览**。 在搜索栏中，键入 `Microsoft.Web.WebView2` ，然后选择 **"Microsoft.Web.WebView2"。**

    :::image type="complex" source="./media/install-nuget.png" alt-text="NuGet程序包管理器&quot;对话框显示 Microsoft.Web.WebView2 卡。" lightbox="./media/install-nuget.png":::
       The NuGet package manager dialog box displays search results including Microsoft.Web.WebView2 card. 该对话框显示版本和安装按钮。
    :::image-end:::

1.  接受默认版本，然后单击"安装 **"。**

1.  在"预览更改"对话框中，单击"确定 **"。**

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

    正在运行的项目显示一个空窗口。

    :::image type="complex" source="./media/winforms-empty-app.png" alt-text="空应用窗口。" lightbox="./media/winforms-empty-app.png":::
       空的应用程序窗口。 验证 WebView2 已安装且正常工作，但没有任何内容可显示。
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-webview"></a>步骤 3 - 创建单个 WebView

将 WebView2 控件添加到你的应用。

1.  在 `MainWindow.xaml` 文件中，若要添加 WebView2 XAML 命名空间，在 标记内插入以下 `<Window/>` 行。

    ```xml
    xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
    ```

1.  确保 中的代码 `MainWindow.xaml` 类似于以下代码段。

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

1.  若要添加 WebView2 控件，请将 `<Grid>` 标记替换为以下代码段。 属性 `Source` 设置 WebView2 控件中显示的初始 URI。

    ```xml
    <DockPanel>
        <wv2:WebView2 Name="webView"
                      Source="https://www.microsoft.com"
        />
    </DockPanel>
    ```

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com) 。

    :::image type="complex" source="./media/wpf-getting-started-microsoft.png" alt-text="Microsoft.com。":::
       Microsoft.com
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-4---navigation"></a>步骤 4 - 导航

允许用户通过向应用添加地址栏来更改 WebView2 控件显示的 URL。

1.  在 文件中，通过复制并粘贴包含 WebView 的 中的以下代码段 `MainWindow.xaml` `<DockPanel>` 来添加地址栏。 将现有代码保持在新代码段的下方。

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

1.  确保文件的 `<DockPanel>` 部分 `MainWindow.xaml` 与以下代码匹配。

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

1.  在 `MainWindow.xaml.cs` 文件中，若要添加 `CoreWebView2` 命名空间，请将以下代码段插入到文件顶部。

    ```csharp
    using Microsoft.Web.WebView2.Core;
    ```

1.  在 `MainWindow.xaml.cs` 文件中，复制以下代码段以创建 `ButtonGo_Click` 方法。 此代码将 WebView2 控件导航到地址栏中输入的 URL。

    ```csharp
    private void ButtonGo_Click(object sender, RoutedEventArgs e)
    {
        if (webView != null && webView.CoreWebView2 != null)
        {
            webView.CoreWebView2.Navigate(addressBar.Text);
        }
    }
    ```

1.  将代码段直接粘贴到 `Public MainWIndow` 声明之后，如以下代码所示。
    
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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  在地址栏中键入新 URL，然后选择"**转到"。**  例如，键入 `https://www.bing.com`。

1.  确保 WebView2 控件打开您输入的 URL。

    > [!NOTE]
    > 请确保在地址栏中输入完整 URL。 如果 URL 不以 或 为起始， `ArgumentException` 则应用将 `http://` 生成 `https://` 。

    :::image type="complex" source="./media/wpf-getting-started-bing.png" alt-text="应用显示必应网站。":::
       示例应用程序在地址必应 URL https://www.bing.com 显示网站。
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-5---navigation-events"></a>步骤 5 - 导航事件

在网页导航期间，WebView2 控件将引发事件。 承载 WebView2 控件的应用侦听以下事件。

*   `NavigationStarting`
*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`
*   `NavigationCompleted`

有关详细信息，请参阅 [WebView2 的导航事件](../concepts/navigation-events.md)。

:::image type="complex" source="../media/navigation-events.png" alt-text="从新文档到导航的导航事件（从导航完成开始）。":::
   以新文档开始导航事件。 故障路径直接从导航开始导航完成。 成功路径包括导航开始、源更改（可能从同一文档输入内容到历史记录更改，通过导航完成）。
:::image-end:::

发生错误时，将引发以下事件，并可能依赖于导航到错误网页。

*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`

> [!NOTE]
> 如果发生 HTTP 重定向，则一行 `NavigationStarting` 中有多个事件。

若要演示如何使用事件，请注册用于取消任何非 `NavigationStarting` HTTPS 请求的处理程序。

在 `MainWindow.xaml.cs` 文件中，修改构造函数以匹配以下代码段并添加 `EnsureHttps` 函数。

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

在构造函数中 `EnsureHttps` ，注册为 WebView2 控件上事件 `NavigationStarting` 的事件处理程序。

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  尝试打开 HTTP 网站。 确保 WebView2 控件保持不变。 但是，WebView2 控件允许你打开 HTTPS 网站。


<!-- ====================================================================== -->
## <a name="step-6---scripting"></a>步骤 6 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。  你可以任务 WebView2 运行任意 JavaScript 或添加初始化脚本。 在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。 注入的 JavaScript 以特定计时运行。

*   创建全局对象后运行它。
*   在运行 HTML 文档中包含的任何其他脚本之前运行它。

例如，添加在用户导航到非 HTTPS 网站时发送警报的脚本。

1.  修改 `EnsureHttps` 函数以将脚本注入到使用 [ExecuteScriptAsync](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync) 方法的 Web 内容中。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  当你导航到不使用 HTTPS 的网站时，请确保应用显示一个警报。

:::image type="complex" source="./media/wpf-getting-started-https.png" alt-text="HTTPS。":::
   HTTPS
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-7---communication-between-host-and-web-content"></a>步骤 7 - 主机和 Web 内容之间的通信

主机和 Web 内容可能通过以下方式使用 进行通信 `postMessage` 。

*   WebView2 控件中的 Web 内容可以使用 向主机发布消息 `window.chrome.webview.postMessage` 。  主机使用主机上注册的任何消息 `WebMessageReceived` 处理邮件。
*   使用 或 将消息张贴到 WebView2 控件中的 `CoreWebView2.PostWebMessageAsString` Web 内容 `CoreWebView2.PostWebMessageAsJSON` 。 消息被添加到 的处理程序捕获 `window.chrome.webview.addEventListener` 。

通信机制使用本机功能将来自 Web 内容的消息传递给主机。

在项目中，当 WebView2 控件导航到 URL 时，它会在地址栏中显示 URL，并通知用户 WebView2 控件中显示的 URL。

1.  在 `MainWindow.xaml.cs` 文件中，更新构造函数并创建 `InitializeAsync` 一个函数以匹配以下代码段。  函数 `InitializeAsync` awaits [EnsureCoreWebView2Async，](/dotnet/api/microsoft.web.webview2.wpf.webview2.ensurecorewebview2async) 因为 的初始化 `CoreWebView2` 是异步的。

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

1.  初始化 **CoreWebView2** 后，注册事件处理程序以响应 `WebMessageReceived` 。  在 `MainWindow.xaml.cs` 中 `InitializeAsync` ，使用下面的 `UpdateAddressBar` 代码段更新和添加。

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

1.  对于要发送和响应 Web 消息的 WebView2 控件，在初始化后， `CoreWebView2` 主机：
    1.  将脚本注入 Web 内容，用于注册处理程序以从主机打印消息。
    1.  将脚本注入到将 URL 张贴到主机的 Web 内容。

1.  在 `MainWindow.xaml.cs` 文件中，进行更新 `InitializeAsync` 以匹配以下代码段。

    ```csharp
    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
        webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

        await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
        await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
    }
    ```

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **保存项目。

1.  按 **F5** 生成并运行项目。

1.  打开新的 URI 时，WebView2 控件会在地址栏中显示它。

    :::image type="complex" source="./media/wpf-getting-started-searchbar.png" alt-text="示例应用在地址栏和 Microsoft 网站中显示 URI。":::
       示例应用在地址栏和 Microsoft 网站中显示 https://www.microsoft.com URI。
    :::image-end:::

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  [WebView2 开发的最佳做法](../concepts/developer-guide.md)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
