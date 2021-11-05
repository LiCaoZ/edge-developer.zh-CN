---
description: 适用于 WinForms 应用的 WebView2 入门指南
title: WinForms 应用中的 WebView2 入门
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/05/2021
ms.topic: tutorial
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview2、WebView、webview、winforms 应用、winforms、edge、CoreWebView2、浏览器控件、edge html、入门、入门、.NET、windows 窗体
ms.openlocfilehash: 1382fae8420a52eb77babab31e0213fa2aeaa702
ms.sourcegitcommit: a01bd8e1ac92a60fc6b1e202ab299ae2714def11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2021
ms.locfileid: "12158163"
---
# <a name="get-started-with-webview2-in-winforms-apps"></a>WinForms 应用中的 WebView2 入门

本文将开始在 WinForms 中创建你的第一个 WebView2 应用，并了解 [WebView2 的主要功能](https://developer.microsoft.com/microsoft-edge/webview2)。 有关各个 API 详细信息，请参阅 [API 参考](/dotnet/api/microsoft.web.webview2.winforms)。


<!-- ====================================================================== -->
## <a name="step-0---prerequisites"></a>步骤 0 - 先决条件

在继续之前安装以下必备组件。

1.  [Visual Studio](https://visualstudio.microsoft.com) 2017 或更高版本。

1.  [WebView2](https://developer.microsoft.com/microsoft-edge/webview2)运行时，或安装在Microsoft Edge操作系统[ ( (](https://www.microsoftedgeinsider.com/download)操作系统) 上的预览体验成员)  ( (Beta、Dev 或 Canary) 预览版。 当前受支持的操作系统列表是 Windows 11、Windows 10、Windows 8.1 和 Windows 7。

    > [!NOTE]
    > WebView2 团队建议使用 Canary 频道。 最低要求版本为 82.0.488.0。

<!-- ====================================================================== -->
## <a name="step-1---create-a-single-window-app"></a>步骤 1 - 创建单窗口应用

从包含单个主窗口的基本桌面项目开始。

1.  打开 Visual Studio。

1.  单击 **"文件**  >  **""**  >  **新建Project"。**

1.  单击 **"新建项目"。**

    :::image type="content" source="./media/winforms-opening-panel.png" alt-text="打开Visual Studio面板将显示&quot;新建项目&quot;卡片。" lightbox="./media/winforms-opening-panel.png":::

1.  选择**C# Windows Forms App (.NET Framework) "，** 然后单击"下一**步"。**

    :::image type="content" source="./media/winforms-new-project.png" alt-text="在&quot;创建新项目&quot;面板中，选择&quot;C# > Windows Forms App (.NET Framework) &quot;。" lightbox="./media/winforms-new-project.png":::

1.  输入 name 和**location** Project**值**。  在"**框架**"下拉列表中，.NET Framework **4.7.2**或更高版本。

    :::image type="content" source="./media/winforms-start-proj.png" alt-text="填写&quot;配置新项目&quot;面板。" lightbox="./media/winforms-start-proj.png":::

1.  单击“创建”****。


<!-- ====================================================================== -->
## <a name="step-2---install-webview2-sdk"></a>步骤 2 - 安装 WebView2 SDK

使用 NuGet 将 WebView2 SDK 添加到项目中。

1. 在 **"解决方案资源管理器**"中，右键单击项目名称，然后选择"管理NuGet**包"。**

    :::image type="content" source="media/wpf-getting-started-mng-nuget-reduced.png" alt-text="管理NuGet包。" lightbox="media/wpf-getting-started-mng-nuget.png":::

1.  单击**浏览**。

1.  选中 **"包括预发布"** 复选框。

1.  在搜索栏中，键入 `WebView2` ，然后单击 **"Microsoft.Web.WebView2"。**

    :::image type="content" source="./media/install-nuget.png" alt-text="NuGet" lightbox="./media/install-nuget.png":::

1.  接受默认版本，然后选择"安装 **"。**

    :::image type="content" source="./media/winforms-install-webview2-preview.png" alt-text="预览更改" lightbox="./media/winforms-install-webview2-preview.png":::

1.  单击**确定**继续。

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

    正在运行的项目显示一个空窗口。

    :::image type="content" source="./media/winforms-empty-app.png" alt-text="示例应用显示一个空窗口。" lightbox="./media/winforms-empty-app.png":::


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-webview"></a>步骤 3 - 创建单个 WebView

将 WebView2 控件添加到你的应用。

1.  单击**Project**  >  **添加窗体 (Windows窗体) 。 **

1.  在"**添加新项**"面板中，单击"Visual **C# Items**  >  **Web**Windows  >  **Forms**Form (Windows Forms  >  **) "，** 然后单击"添加 **"。**

1.  单击 **"视图**  >  **工具箱"。**

1.  在**工具箱中**，单击 **"WebView2 Windows窗体控件"** 展开选项。

    > [!NOTE]
    > 如果使用的是 Visual Studio 2017，默认情况下 **，WebView2**不会显示在工具箱**中**。 若要使**WebView2**显示在工具箱中****，请选择"**** 工具""选项""常规  >  ****  >  ****>"**自动填充工具箱**"设置设置为 `True` 。

1.  将**WebView2 控件**拖动到 Windows Forms App 中。

    :::image type="content" source="./media/winforms-toolbox.png" alt-text="显示 WebView2 的工具箱" lightbox="./media/winforms-toolbox.png":::

1.  在" **属性** "面板中， (** Name) ** 设置为 **webView**。 根据需要 **使用"分类** " **和** "字母顺序"排序选项查找属性。

    :::image type="content" source="./media/winforms-properties.png" alt-text="WebView2 控件的属性" lightbox="./media/winforms-properties.png":::

1.  Source **** 属性设置 WebView2 控件中显示的初始 URI。 将 **Source 属性** 设置为 `https://www.microsoft.com` 。

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

1.  确保 WebView2 控件显示 [https://www.microsoft.com](https://www.microsoft.com) 。

    :::image type="complex" source="./media/winforms-hello-webview.png" alt-text="示例应用显示 Microsoft 网站。" lightbox="./media/winforms-hello-webview.png":::
       具有 WebView2 控件的示例应用程序将显示 Microsoft 网站 https://www.microsoft.com 。
    :::image-end:::

    > [!NOTE]
    > 如果正在处理高分辨率监视器，可能需要将 Windows [Forms 应用配置为高 DPI 支持](/dotnet/framework/winforms/high-dpi-support-in-windows-forms#configuring-your-windows-forms-app-for-high-dpi-support)。


<!-- ====================================================================== -->
## <a name="step-4---add-controls-and-process-window-resize-events"></a>步骤 4 - 添加控件并处理窗口大小事件

将更多控件添加到工具箱Windows窗体，然后处理窗口大小事件，如下所示。

1.  单击 **"视图**  >  **工具箱"。**

1.  在工具箱**中**，单击 **"常用控件"。**

1.  将**TextBox 控件**拖到"Windows"应用。

1.  在"**属性"** 面板中，将 (**名称) ****地址栏"**。

1.  将"**按钮"** 控件拖到"Windows"应用。

1.  在"**属性**"面板中，将 (**名称) ****更改为 goButton**。

1.  将 **Text 属性** 更改为 **Go！**

1.  根据需要调整按钮的大小以显示文本。

1.  将文本框排列到按钮的左侧，按如下所示的文本对齐。

    :::image type="content" source="./media/winforms-designer.png" alt-text="WinForms 设计器" lightbox="./media/winforms-designer.png":::

1.  调整文本框的大小，如下所示。

    :::image type="content" source="./media/winforms-designer-txtbtn.png" alt-text="WinForms 设计器文本框和按钮" lightbox="./media/winforms-designer-txtbtn.png":::

1. 单击 **"**  >  **查看**代码"打开 `Form1.cs` 文件。

    定义 `Form_Resize` 以在调整应用窗口大小时保持控件就位，如下所示。

1.  删除以下代码。

    ```csharp
        public Form1()
    {
        InitializeComponent();
    }
    ```

1.  在同一位置复制并粘贴此代码段。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

    确保应用如下图所示。

:::image type="content" source="./media/winforms-app.png" alt-text="应用" lightbox="./media/winforms-app.png":::


<!-- ====================================================================== -->
## <a name="step-5---navigation"></a>步骤 5 - 导航

允许用户通过向应用添加地址栏来更改 WebView2 控件显示的 URL。

1.  确保应用按上一 `Form1` 部分所示显示。

1.  在 `Form1.cs` 中， `CoreWebView2` 添加命名空间，方法为在顶部插入以下代码：

    ```csharp
    using Microsoft.Web.WebView2.Core;
    ```

1.  在 **"Windows设计器**"中，双击按钮 `Go!` 以 `goButton_Click` 在文件中创建 `Form1.cs` 方法。  复制并粘贴该方法中的以下代码段。

    ```csharp
    private void goButton_Click(object sender, EventArgs e)
    {
        if (webView != null && webView.CoreWebView2 != null)
        {
            webView.CoreWebView2.Navigate(addressBar.Text);
        }
    }
    ```

    现在 `goButton_Click` ，函数将 WebView2 控件导航到地址栏中输入的 URI。

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

1.  在地址栏中输入新 URL，然后选择"转到 **"。**  例如，输入 `https://www.bing.com` 。  确保 WebView2 控件导航到 URL。

> [!NOTE]
> 在地址栏中输入完整 URL。  如果 `ArgumentException` URL 不以 或 为起始，则 `http://` 会引发 。 `https://`

:::image type="content" source="./media/winforms-bing.png" alt-text="bing.com" lightbox="./media/winforms-bing.png":::


<!-- ====================================================================== -->
## <a name="step-6---navigation-events"></a>步骤 6 - 导航事件

在网页导航期间，WebView2 控件将引发事件。 承载 WebView2 控件的应用侦听以下事件。

*   `NavigationStarting`
*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`
*   `NavigationCompleted`

有关详细信息，请参阅 [WebView2 的导航事件](../concepts/navigation-events.md)。

:::image type="content" source="../media/navigation-events.png" alt-text="导航事件":::

发生错误时，将引发以下事件，并可能依赖于导航到错误网页。

*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`

> [!NOTE]
> 如果发生 HTTP 重定向，则一行 `NavigationStarting` 中有多个事件。

若要演示如何使用事件，请首先注册一个处理程序，以取消不使用 `NavigationStarting` HTTPS 的任何请求。

1.  在 `Form1.cs` 文件中，更新构造函数以匹配以下代码段，并添加 函数 `EnsureHttps` ，如下所示。

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

1.  在导航到 HTTP 网站时，请确保 WebView2 控件保持不变。 转到 HTTPS 网站，注意 WebView2 将打开 HTTPS 网站。


<!-- ====================================================================== -->
## <a name="step-7---scripting"></a>步骤 7 - 脚本

在运行时，可以使用主机应用将 JavaScript 代码注入 WebView2 控件。 你可以任务 WebView2 运行任意 JavaScript 或添加初始化脚本。 在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。 注入的 JavaScript 以特定计时运行。

*   创建全局对象后运行注入的 JavaScript。
*   在 HTML 文档中包含的任何其他脚本运行之前，运行注入的 JavaScript。

1.  例如，添加在用户导航到非 HTTPS 网站时发送警报的脚本。  修改 `EnsureHttps` 函数以将脚本注入到使用 [ExecuteScriptAsync](/dotnet/api/microsoft.web.webview2.winforms.webview2.executescriptasync) 方法的 Web 内容中，如下所示：

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

1.  单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1.  按 **F5** 生成并运行项目。

1.  确保应用在您转到不使用 HTTPS 的网站时显示警报。

:::image type="content" source="./media/winforms-https.png" alt-text="https" lightbox="./media/winforms-https.png":::


<!-- ====================================================================== -->
## <a name="step-8---communication-between-host-and-web-content"></a>步骤 8 - 主机和 Web 内容之间的通信

主机和 Web 内容可用于相互 `postMessage` 通信，如下所示：

*   WebView2 控件中的 Web 内容可用于 `window.chrome.webview.postMessage` 向主机发布消息。  主机使用主机上注册的任何消息 `WebMessageReceived` 处理邮件。
*   使用 或 将消息张贴到 WebView2 控件中的 `CoreWebView2.PostWebMessageAsString` Web 内容 `CoreWebView2.PostWebMessageAsJSON` 。  添加到 的处理程序会捕获这些消息 `window.chrome.webview.addEventListener` 。

通信机制使用本机功能将来自 Web 内容的消息传递给主机。

在项目中，当 WebView2 控件导航到 URL 时，它会在地址栏中显示 URL，并通知用户 WebView2 控件中显示的 URL。

1.  在 `Form1.cs` 文件中，更新构造函数并创建 `InitializeAsync` 一个函数以匹配以下代码段：

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

    函数 `InitializeAsync` awaits [EnsureCoreWebView2Async，](/dotnet/api/microsoft.web.webview2.winforms.webview2.ensurecorewebview2async) 因为 的初始化 `CoreWebView2` 是异步的。

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

1.  对于 WebView2 发送和响应 Web 消息，在初始化后，主机将 Web 内容中的脚本注入 `CoreWebView2` 到：
    1.  使用 将 URL 发送到主机 `postMessage` 。
    1.  注册事件处理程序以打印从主机发送的消息。

1. 在 `Form1.cs` 文件中，更新 `InitializeAsync` 以匹配以下代码段：

    ```csharp
    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
        webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

        await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
        await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
    }
    ```

1. 单击 **"**  >  **文件全部保存 (Ctrl+Shift+S) **以保存项目。

1. 按 **F5** 生成并运行项目。

1.  打开新的 URI 时，WebView2 控件会在地址栏中显示它。

    :::image type="complex" source="./media/winforms-final-app.png" alt-text="应用程序在地址栏中显示 URI。":::
       应用程序在地址栏中显示 URI。 URI 为 https://www.microsoft.com ，并且 Microsoft 网站在窗口中显示。
    :::image-end:::

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  [WebView2 开发的最佳做法](../concepts/developer-guide.md)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [另请参阅](../index.md#see-also) - 有关生成和部署 WebView2 应用的概念和工作说明文章。
*  [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.winforms.webview2)
