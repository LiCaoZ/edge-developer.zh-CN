---
description: 适用于 WinForms 应用的 WebView2 入门指南
title: WinForms 应用中的 WebView2 入门
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/20/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview2、WebView、webview、winforms 应用、winforms、edge、CoreWebView2、浏览器控件、edge html、入门、入门、.NET、windows 窗体
ms.openlocfilehash: b1c0d451ab048800f395fd250ded24ac27a3202d
ms.sourcegitcommit: f2c56030b2141eba01b534984579762421eff6aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2021
ms.locfileid: "12034077"
---
# <a name="get-started-with-webview2-in-winforms-apps"></a>WinForms 应用中的 WebView2 入门

本文将开始创建你的第一个 WebView2 应用，并了解 [WebView2 的主要功能][MicrosoftDeveloperMicrosoftEdgeWebview2]。  有关各个 API 的信息，请导航到 [API 参考][DotnetApiMicrosoftWebWebview2Winforms]。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

安装以下必备组件列表，然后再继续。

*   [WebView2][MicrosoftDeveloperMicrosoftEdgeWebview2]运行时或任何[Microsoft Edge Insider (preview) Channel (][MicrosoftedgeinsiderDownload] Beta、Dev 或 Canary) 安装在受支持的 OS (当前为 Windows 10、Windows 8.1 和 Windows 7) 。

    > [!NOTE]
    > WebView 团队建议使用 Canary 通道，最低要求版本为 82.0.488.0。

*   [Visual Studio][MicrosoftVisualstudioMain] 2017 或更高版本。


<!-- ====================================================================== -->
## <a name="step-1---create-a-single-window-app"></a>步骤 1 - 创建单窗口应用

从包含单个主窗口的基本桌面项目开始。

1. 打开 Visual Studio。 在打开的面板中， **选择新建项目**。

    :::image type="complex" source="./media/winforms-opening-panel.png" alt-text="Visual Studio打开面板" lightbox="./media/winforms-opening-panel.png":::
       Visual Studio打开面板 :::image-end:::

1. 选择**C# Windows Forms .NET Framework App"，** 然后选择"下一**步"。**

    :::image type="complex" source="./media/winforms-new-project.png" alt-text="新建项目" lightbox="./media/winforms-new-project.png":::
       新建项目 :::image-end:::

1.  输入 name 和**Location** Project**值**。  选择 **.NET Framework 4.7.2**或更高版本。

    :::image type="complex" source="./media/winforms-start-proj.png" alt-text="启动项目" lightbox="./media/winforms-start-proj.png":::
       启动项目
    :::image-end:::

1.  选择**创建**。


<!-- ====================================================================== -->
## <a name="step-2---install-webview2-sdk"></a>步骤 2 - 安装 WebView2 SDK

使用 NuGet 将 WebView2 SDK 添加到项目中。

1.  将鼠标悬停在项目上，打开上下文菜单 (右键单击") "，然后选择"管理NuGet**包"。**

    :::image type="complex" source="./media/wpf-getting-started-mng-nuget.png" alt-text="管理 NuGet 包":::
       管理 NuGet 包
    :::image-end:::

1.  选择"**浏览"。**  在搜索栏中，键入 `Microsoft.Web.WebView2` ，然后选择 **"Microsoft.Web.WebView2"。**

    :::image type="complex" source="./media/install-nuget.png" alt-text="NuGet" lightbox="./media/install-nuget.png":::
       NuGet
    :::image-end:::

1. 接受默认版本，然后选择"安装 **"。**

    :::image type="complex" source="./media/winforms-install-webview2-preview.png" alt-text="预览更改" lightbox="./media/winforms-install-webview2-preview.png":::
       预览更改 :::image-end:::

1. 选择 **"确定** "继续。

    开始使用 WebView2 API 开发应用。  若要生成并运行项目，请选择 `F5` 。  正在运行的项目显示一个空窗口。

    :::image type="complex" source="./media/winforms-empty-app.png" alt-text="空应用" lightbox="./media/winforms-empty-app.png":::
       空应用 :::image-end:::


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-webview"></a>步骤 3 - 创建单个 WebView

将 WebView 添加到你的应用。

1. 选择**Project**  >  **添加窗体 (Windows窗体) 。 **
1. 在"**添加新项**"**面板**中，C#"Windows"窗体" (Windows") "  >  ****  >  ****  >  **** 添加 **"。**
1. 选择 **"视图**  >  **工具箱"。**
1. 在**工具箱中**，选择 **"WebView2 Windows窗体控件"** 以展开选项。

    > [!NOTE]
    > 如果使用的是 Visual Studio 2017，默认情况下**WebView2**不会显示在工具箱**中**。 若要使**WebView2**显示在工具箱中****，请选择"**** 工具""选项""常规  >  ****  >  ****>"自动**填充工具箱**"设置设置为 `True` 。

1. 将**WebView2 控件**拖放到 Windows Forms App。

    :::image type="complex" source="./media/winforms-toolbox.png" alt-text="显示 WebView2 的工具箱" lightbox="./media/winforms-toolbox.png":::
       显示 WebView2 的工具箱 :::image-end:::

1. 关闭 **工具箱**。

1. 在" **属性** "面板中， (** Name) ** 设置为 **webView**。 根据需要 **使用"分类** " **和** "字母顺序"排序选项查找属性。

    :::image type="complex" source="./media/winforms-properties.png" alt-text="WebView2 控件的属性" lightbox="./media/winforms-properties.png":::
       WebView2 控件的属性 :::image-end:::

1.  Source **** 属性设置 WebView2 控件中显示的初始 URI。 将 **Source 属性** 设置为 `https://www.microsoft.com` 。

1. 选择 **F5** 生成并运行项目。

    确保 WebView2 控件显示 [https://www.microsoft.com][|::ref1::|Main] 。

    :::image type="complex" source="./media/winforms-hello-webview.png" alt-text="hello webview" lightbox="./media/winforms-hello-webview.png":::
       hello webview :::image-end:::

    > [!NOTE]
    > 如果正在处理高分辨率监视器，可能需要将 Windows [Forms 应用配置为高 DPI 支持][DotnetFrameworkWinformsHighDpiSupportWindowsFormsConfiguringYourWindowsFormsAppForHighDpiSupport]。


<!-- ====================================================================== -->
## <a name="step-4---add-controls-and-process-window-resize-events"></a>步骤 4 - 添加控件并处理窗口大小事件

将更多控件添加到工具箱Windows窗体，然后处理窗口大小事件，如下所示。

1. 选择 **"视图**  >  **工具箱"。**
1. 在"**工具箱"中**，选择 **"常用控件"。**
1. 将**TextBox 控件拖放**到"Windows"应用中。
1. 在"**属性**"面板中，将 (**名称) ****地址栏"**。
1. 将"按钮"**控件**拖放到"Windows"应用中。
1. 在"**属性**"面板中，将 (**名称) ****更改为 goButton**。
1. 将 **Text 属性** 更改为 **Go！**
1. 根据需要调整按钮的大小以显示文本。
1. 将文本框排列到按钮的左侧，按如下所示的文本对齐。

    :::image type="complex" source="./media/winforms-designer.png" alt-text="WinForms 设计器" lightbox="./media/winforms-designer.png":::
       WinForms 设计器 :::image-end:::

1. 调整文本框的大小，如下所示。

    :::image type="complex" source="./media/winforms-designer-txtbtn.png" alt-text="WinForms 设计器文本框和按钮" lightbox="./media/winforms-designer-txtbtn.png":::
       WinForms 设计器文本框和按钮 :::image-end:::

1. 选择 **"**  >  **查看**代码"打开 `Form1.cs` 文件。

    定义 `Form_Resize` 以在调整应用窗口大小时保持控件就位，如下所示。

1. 将以下代码：

    ```csharp
        public Form1()
    {
        InitializeComponent();
    }
    ```

    with：

    ```csharp
    public Form1()
    {
        InitializeComponent();
        this.Resize += new System.EventHandler(this.Form_Resize);
    }

    private void Form_Resize(object sender, EventArgs e)
    {
        webView.Size = this.ClientSize - new System.Drawing.Size(webView.Location);
        goButton.Left = this.ClientSize.Width - goButton.Width;
        addressBar.Width = goButton.Left - addressBar.Left;
    }
    ```

1. 选择 **F5** 生成并运行项目。

    确保应用显示类似于下图。

:::image type="complex" source="./media/winforms-app.png" alt-text="应用" lightbox="./media/winforms-app.png":::
   应用
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-5---navigation"></a>步骤 5 - 导航

添加允许用户通过向应用添加地址栏来更改 WebView2 控件显示的 URL 的能力。

1.  选择 `F5` 以生成并运行项目。  确认应用显示类似于以下屏幕截图。

    :::image type="complex" source="./media/winforms-app.png" alt-text="WinForms 应用" lightbox="./media/winforms-app.png":::
       WinForms 应用
    :::image-end:::

1.  在 `Form1.cs` 文件中，若要添加 `CoreWebView2` 命名空间，请将以下代码段插入顶部。
1.  在 `Form1.cs` 添加 `CoreWebView2` 命名空间时，在 的顶部插入以下代码段 `Form1.cs` 。

    ```csharp
    using Microsoft.Web.WebView2.Core;
    ```

1.  在 **"Windows设计器**"中，双击按钮 `Go!` 以 `goButton_Click` 在文件中创建 `Form1.cs` 方法。  复制以下代码段并将其粘贴到 函数中。  现在， `goButton_Click` 函数将 WebView 导航到地址栏中输入的 URL。

    ```csharp
    private void goButton_Click(object sender, EventArgs e)
    {
        if (webView != null && webView.CoreWebView2 != null)
        {
            webView.CoreWebView2.Navigate(addressBar.Text);
        }
    }
    ```

若要生成并运行项目，请选择 `F5` 。  在地址栏中输入新 URL，然后选择"转到 **"。**  例如，输入 `https://www.bing.com` 。  确保 WebView2 控件导航到 URL。

> [!NOTE]
> 确保在地址栏中输入完整 URL。  如果 `ArgumentException` URL 不以 或 为起始，则 `http://` 会引发 。 `https://`

:::image type="complex" source="./media/winforms-bing.png" alt-text="bing.com" lightbox="./media/winforms-bing.png":::
   bing.com
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-6---navigation-events"></a>步骤 6 - 导航事件

在网页导航期间，WebView2 控件将引发事件。  承载 WebView2 控件的应用侦听以下事件。

*   `NavigationStarting`
*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`
*   `NavigationCompleted`

有关详细信息，请导航到["导航事件"。][Webview2ConceptsNavigationEvents]

:::image type="complex" source="../media/navigation-events.png" alt-text="导航事件":::
   导航事件
:::image-end:::

发生错误时，将引发以下事件，并可能依赖于导航到错误网页。

*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`

> [!NOTE]
> 如果发生 HTTP 重定向，则一行 `NavigationStarting` 中有多个事件。

若要演示如何使用事件，请首先注册一个处理程序，以取消不使用 `NavigationStarting` HTTPS 的任何请求。

在 `Form1.cs` 文件中，更新构造函数以匹配以下代码段并添加 `EnsureHttps` 函数。

```csharp
public Form1()
{
    InitializeComponent();
    this.Resize += new System.EventHandler(this.Form_Resize);

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

若要生成并运行项目，请选择 `F5` 。  在导航到 HTTP 网站时，确保 WebView 保持不变。  但是，WebView 将导航到 HTTPS 网站。


<!-- ====================================================================== -->
## <a name="step-7---scripting"></a>步骤 7 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。  你可以任务 WebView 运行任意 JavaScript 或添加初始化脚本。  在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。  注入的 JavaScript 以特定计时运行。

*   创建全局对象后运行它。
*   在运行 HTML 文档中包含的任何其他脚本之前运行它。

例如，添加在用户导航到非 HTTPS 网站时发送警报的脚本。  修改 `EnsureHttps` 函数以将脚本注入到使用 [ExecuteScriptAsync][DotnetApiMicrosoftWebWebview2WinformsWebview2Executescriptasync] 方法的 Web 内容中。

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

若要生成并运行项目，请选择 `F5` 。  当你导航到不使用 HTTPS 的网站时，请确保应用显示一个警报。

:::image type="complex" source="./media/winforms-https.png" alt-text="https" lightbox="./media/winforms-https.png":::
   https
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-8---communication-between-host-and-web-content"></a>步骤 8 - 主机和 Web 内容之间的通信

主机和 Web 内容可用于相互 `postMessage` 通信，如下所示：

*   WebView2 控件中的 Web 内容可用于 `window.chrome.webview.postMessage` 向主机发布消息。  主机使用主机上注册的任何消息 `WebMessageReceived` 处理邮件。
*   使用 或 将消息张贴到 WebView2 控件中的 `CoreWebView2.PostWebMessageAsString` Web 内容 `CoreWebView2.PostWebMessageAsJSON` 。  添加到 的处理程序会捕获这些消息 `window.chrome.webview.addEventListener` 。

通信机制使用本机功能将来自 Web 内容的消息传递给主机。

在项目中，当 WebView2 控件导航到 URL 时，它会在地址栏中显示 URL，并通知用户 WebView2 控件中显示的 URL。

1.  在 `Form1.cs` 文件中，更新构造函数并创建 `InitializeAsync` 一个函数以匹配以下代码段。  函数 `InitializeAsync` awaits [EnsureCoreWebView2Async，][DotnetApiMicrosoftWebWebview2WinformsWebview2Ensurecorewebview2async] 因为 的初始化 `CoreWebView2` 是异步的。

    ```csharp
    public Form1()
    {
        InitializeComponent();
        this.Resize += new System.EventHandler(this.Form_Resize);
        webView.NavigationStarting += EnsureHttps;
        InitializeAsync();
    }

    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
    }
    ```

1.  初始化 `CoreWebView2` 后，注册事件处理程序以响应 `WebMessageReceived` 。  在 `Form1.cs` 文件中， `InitializeAsync` 使用下面的代码 `UpdateAddressBar` 段更新和添加。

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

1.  为了使 WebView 能够发送和响应 Web 消息，在初始化后，主机将 Web 内容中的脚本注入 `CoreWebView2` 到：
    1.  使用 将 URL 发送到主机 `postMessage` 。
    1.  注册事件处理程序以打印从主机发送的消息。

在 `Form1.cs` 文件中，进行更新 `InitializeAsync` 以匹配以下代码段。

```csharp
async void InitializeAsync()
{
    await webView.EnsureCoreWebView2Async(null);
    webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

    await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
    await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
}
```

若要生成并运行应用，请选择 `F5` 。  现在，地址栏在 WebView2 控件中显示 URI。  此外，当你成功导航到新 URL 时，WebView 会向用户通知 WebView 中显示的 URL。

:::image type="complex" source="./media/winforms-final-app.png" alt-text="最终应用" lightbox="./media/winforms-final-app.png":::
   最终应用
:::image-end:::

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  [WebView2 开发的最佳做法][WV2BestPractices]
*  [WebView2Samples][GithubMicrosoftedgeWebview2samplesMain] - WebView2 功能的综合示例。
*  [接下来的步骤][Webview2IndexNextSteps] - 有关构建和部署 WebView2 应用的概念和操作说明文章。
*  [WebView2 API 参考][DotnetApiMicrosoftWebWebview2WinformsWebview2]


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]


<!-- ====================================================================== -->
<!-- links -->
[WV2BestPractices]: ../concepts/developer-guide.md "WebView2 开发最佳实践|Microsoft Docs"
[Webview2IndexNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 |Microsoft Docs"
[Webview2ConceptsNavigationEvents]: ../concepts/navigation-events.md "导航事件|Microsoft Docs"
<!-- external links -->
[DotnetApiMicrosoftWebWebview2Winforms]: /dotnet/api/microsoft.web.webview2.winforms "Microsoft.Web.WebView2.WinForms 命名空间|Microsoft Docs"
[DotnetApiMicrosoftWebWebview2WinformsWebview2]: /dotnet/api/microsoft.web.webview2.winforms.webview2 "WebView2 类|Microsoft Docs"
[DotnetApiMicrosoftWebWebview2WinformsWebview2Ensurecorewebview2async]: /dotnet/api/microsoft.web.webview2.winforms.webview2.ensurecorewebview2async "WebView2.EnsureCoreWebView2Async (CoreWebView2Environment) 方法|Microsoft Docs"
[DotnetApiMicrosoftWebWebview2WinformsWebview2Executescriptasync]: /dotnet/api/microsoft.web.webview2.winforms.webview2.executescriptasync "WebView2.ExecuteScriptAsync (String) 方法|Microsoft Docs"

[DotnetFrameworkWinformsHighDpiSupportWindowsFormsConfiguringYourWindowsFormsAppForHighDpiSupport]: /dotnet/framework/winforms/high-dpi-support-in-windows-forms#configuring-your-windows-forms-app-for-high-dpi-support "Configuring your Windows Forms app for high DPI support - Windows Forms |Microsoft Docs"

[GithubMicrosoftedgeWebview2samplesMain]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"

[MicrosoftedgeinsiderDownload]: https://www.microsoftedgeinsider.com/download "下载 Microsoft Edge 预览体验成员频道"

[MicrosoftDeveloperMicrosoftEdgeWebview2]: https://developer.microsoft.com/microsoft-edge/webview2 "WebView2 |Microsoft Edge开发人员"

[MicrosoftMain]: https://www.microsoft.com "Microsoft"

[MicrosoftVisualstudioMain]: https://visualstudio.microsoft.com "Visual Studio"
