---
description: 如何指定一Microsoft Edge预览通道，以测试预发布包中的实验性 API。
title: 切换到预览频道以测试即将推出的 API 和功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/03/2021
ms.topic: how-to
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: 40e435a4f6ae1df9f20ea7b09ca54b764b511fe6
ms.sourcegitcommit: 09975d536fb4673442f2ac6629e1787f14f110e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2021
ms.locfileid: "12035346"
---
# <a name="switch-to-a-preview-channel-to-test-upcoming-apis-and-features"></a>切换到预览频道以测试即将推出的 API 和功能

WebView2 Evergreen Runtime 的更新通常包括新的 API 和功能。  其中某些更新可能会破坏 WebView2 应用。  若要提前测试实验性 API 并确保应用的向前兼容性，你应该使用 Microsoft Edge 预览通道以及 WebView2 SDK 的预发布版本执行兼容性测试。

测试预发布 SDK 包时，需要指示应用程序使用 Microsoft Edge (Beta、Dev 或 Canary) 的预览频道，而不是默认使用 WebView2 运行时。  下面介绍了几种执行此操作的方法。

WebView2 运行时没有实验性 WebView2 API。  若要在预发布 SDK 中使用实验性 API 时运行 WebView2 代码，开发计算机上客户端 (需要具有) 预览Microsoft Edge通道。  建议使用 Canary 预览频道，因为它位于其他频道之前，并且具有最新的实验 API。

预发布 SDK 与预览频道协同工作，如下所示：
*  WebView2 SDK 的预发布版本包含实验性 API 的方法签名，这允许你在应用中使用实验性 WebView2 API 编写代码。
*  应用的预览Microsoft Edge包含Microsoft Edge和呈现应用（包括实验性 API 的实现）所需的二进制文件。

有关 SDK 版本如何与 WebView2 运行时或 Microsoft Edge 预览频道结合使用的详细信息，请导航到了解[WebView2 SDK 版本][WebView2ConceptsVersioning]。


## <a name="downloading-the-prerelease-sdk-and-a-preview-channel"></a>下载预发布 SDK 和预览频道

若要使用实验性 API，请从 [Microsoft.Web.WebView2](https://www.nuget.org/packages/Microsoft.Web.WebView2)程序包下载 WebView2 SDK 的预发布版本。

若要获取预览Microsoft Edge，请导航到"Microsoft Edge[预览体验成员频道"。][MicrosoftedgeinsiderDownload]


<!-- intro/overview of 4 approaches -->
## <a name="approaches-to-making-your-app-use-a-specific-browser-channel"></a>使应用使用特定浏览器通道的方法

有几种方法使 WebView2 应用使用指定的预览频道Microsoft Edge：
*  通过调用函数。
*  使用组策略。
*  通过使用注册表替代。
*  通过使用环境变量。

下面介绍了这些方法。

### <a name="default-channel-search-order"></a>默认通道搜索顺序

本节适用于使用组策略、注册表替代或环境变量。

默认通道搜索顺序为：
1.  WebView2 运行时。
1.  Microsoft Edge Beta 渠道。
1.  开发人员的开发人员Microsoft Edge。
1.  Canary 通道的Microsoft Edge。

如果设置浏览器可执行文件夹，将覆盖上述搜索顺序。

如果使用组策略、注册表替代或环境变量来设置发布通道首选项，这将使用默认搜索顺序的相反顺序。


<!-- 1. Code ===============================================================-->
## <a name="using-code"></a>使用代码

如果要使应用程序通过调用 函数Microsoft Edge预览通道，请完成以下步骤。

此方法仅适用于本地测试，不应交付。  这是因为此方法需要查找 Edge 浏览器安装路径，该路径可能会在将来的更新中更改。

### <a name="win32c"></a>Win32\/C++

我们将使用 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample) 演示此过程。

1.  在开发计算机上，查找包含预览Microsoft Edge路径。  例如：

    `C:\\Users\\myname\\AppData\\Local\\Microsoft\\Edge SxS\\Application\\93.0.929.0`

1.  克隆 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库。

1.  打开 **WebView2APISample** 项目，然后在 **"源文件"** 中打开 `AppWindow.cpp` 文件。

1.  查找 [调用 CreateCoreWebView2EnvironmentWithOptions][Webview2RefWin32GlobalsCreateCoreWebView2EnvironmentWithOptions] 的地方。  例如：

    ```cpp
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, m_userDataFolder.c_str(), options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
    ```

1.  将 `subFolder` 变量替换为您想要使用Microsoft Edge预览频道的文件夹路径。  例如：

    ```cpp
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        L"C:\\Users\\myname\\AppData\\Local\\Microsoft\\Edge SxS\\Application\\93.0.929.0", m_userDataFolder.c_str(), options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
    ```

### <a name="winforms"></a>WinForms

WinForms 使用的方法与上述 Win32/C++ 方法类似。

1.  设置为 `CreationProperties.BrowserExecutableFolder` 指向包含 Canary 或 Dev Microsoft Edge路径。  为此，在 **WebView2Samples** 解决方案中的 **WebView2WpfBrowser** 项目中，打开文件 `MainWindow.xaml.cs` 。

1.  查找 `CreationProperties.BrowserExecutableFolder` 。  例如：

    ```csharp
    WebView2 GetReplacementControl(bool useNewEnvironment)
    {
        WebView2 replacementControl = new WebView2();
        ((System.ComponentModel.ISupportInitialize)(replacementControl)).BeginInit();
        // Setup properties and bindings.
        if (useNewEnvironment)
        {
            // Create a new CoreWebView2CreationProperties instance so the environment
            // is made anew.
            replacementControl.CreationProperties = new CoreWebView2CreationProperties();
            replacementControl.CreationProperties.BrowserExecutableFolder = webView.CreationProperties.BrowserExecutableFolder;
            replacementControl.CreationProperties.Language = webView.CreationProperties.Language;
            replacementControl.CreationProperties.UserDataFolder = webView.CreationProperties.UserDataFolder;
            shouldAttachEnvironmentEventHandlers = true;
        }
    ```

### <a name="wpf"></a>WPF

WPF 使用的方法与上述 Win32/C++ 方法类似。

请参阅 [CoreWebView2CreationProperties.BrowserExecutableFolder 属性](/dotnet/api/microsoft.web.webview2.wpf.corewebview2creationproperties.browserexecutablefolder#Microsoft_Web_WebView2_Wpf_CoreWebView2CreationProperties_BrowserExecutableFolder)。


<!-- 2. Group Policy =======================================================-->
## <a name="using-a-group-policy"></a>使用组策略

如果你想要让应用程序使用组策略Microsoft Edge预览通道，请复制 ADMX 和 ADML 文件到该 `PolicyDefinitions` 文件夹，如下所示。

1.  从下载并部署适用于Microsoft Edge[下载策略文件](https://www.microsoft.com/edge/business/download)。

1.  将 ADMX 文件复制到策略定义模板文件夹，例如 `C:\Windows\PolicyDefinitions` 。

1.  将 ADML 文件复制到文件夹内的匹配区域设置 `Policy Definitions` 文件夹中，例如 `C:\Windows\PolicyDefinitions\en-us` 文件夹。

1.  打开本地 **组策略编辑器**。  为此，请在"搜索Windows，键入"组策略"，然后选择"编辑**组策略"。**

1.  展开 **"本地计算机策略"，** 然后展开"**计算机配置"或**"**用户配置"。**  然后展开 **"管理模板**  >  **Microsoft Edge WebView2"。**

    :::image type="complex" source="./media/local-group-policy-editor.png" alt-text="&quot;本地组策略编辑器&quot;对话框" lightbox="./media/local-group-policy-editor.png":::
       **"本地组策略编辑器** "对话框
    :::image-end:::

1.  选择 **"浏览器可执行文件夹"。**  以下屏幕截图适用于设置浏览器可执行 **文件夹**。  或者，选择 **"发布频道首选项"，** 这将使用类似的对话框。

    :::image type="complex" source="./media/browser-executable-folder.png" alt-text="设置浏览器可执行文件夹" lightbox="./media/browser-executable-folder.png":::
       设置 **浏览器可执行文件夹**
    :::image-end:::

1.  选择" **显示"** 按钮。

1.  填写" **显示内容"** 对话框。  在 **"值名称** "列中，输入要应用于所有 WebView2 应用的星号，或仅影响指定 `.exe` WebView2 应用的文件名。  在 **"值** "列中，输入 WebView2 应用的可执行文件的路径。

    :::image type="complex" source="./media/show-contents.png" alt-text="&quot;显示内容&quot;对话框" lightbox="./media/show-contents.png":::
       " **显示内容"** 对话框
    :::image-end:::

1.  选择 **"** 确定"关闭对话框。

有关详细信息，请参阅配置策略[Microsoft Edge设置。](/deployedge/configure-microsoft-edge)


<!-- 3. Registry Override ==================================================-->
## <a name="using-a-registry-override"></a>使用注册表替代

使用注册表替代指定预览频道时，有两个选项：
*  更改浏览器可执行文件夹。
*  更改发布频道首选项。

下面介绍了这两种方法。

### <a name="registry-override-browser-executable-folder"></a>注册表替代：浏览器可执行文件夹

若要使应用程序使用设置浏览器Microsoft Edge文件夹的注册表替代，请使用预览通道：

1.  打开 PowerShell 终端或启用 PowerShell 的命令提示符。

1.  修改并运行以下命令：

    `REG ADD HKLM\Software\Policies\Microsoft\Edge\WebView2\BrowserExecutableFolder /v * /t REG_SZ /d "C:\Users\myname\AppData\Local\Microsoft\Edge SxS\Application\88.0.680.0"`

    星号 (*) 作为值名称，因此此替代适用于所有 WebView2 应用。  如果只想将此替代应用于特定的 WebView2 应用，请将星号替换为应用的可执行文件的文件名。

    将 `C:\Users\myname\AppData\Local\Microsoft\Edge SxS\Application\88.0.680.0` 替换为所需预览Microsoft Edge路径。

#### <a name="resuming-using-the-default-webview2-evergreen-runtime"></a>使用默认的 WebView2 Evergreen Runtime 恢复

若要撤消上述设置，请运行以下命令：

`REG DELETE HKLM\Software\Policies\Microsoft\Edge\WebView2\BrowserExecutableFolder /f`

### <a name="registry-override-release-channel-preference"></a>注册表替代：发布通道首选项

若要使应用程序使用Microsoft Edge预览通道，请通过更改频道的搜索顺序来更改发布频道首选项的注册表替代：

1.  打开 PowerShell 终端或启用 PowerShell 的命令提示符。

1.  修改并运行以下命令：

    `REG ADD HKLM\Software\Policies\Microsoft\Edge\WebView2\ReleaseChannelPreference /v * /t REG_SZ /d "1"`

    星号 (*) 作为值名称，因此此替代适用于所有 WebView2 应用。  如果只想将此替代应用于特定的 WebView2 应用，请将星号替换为应用的可执行文件的文件名。

#### <a name="resuming-using-the-default-webview2-evergreen-runtime"></a>使用默认的 WebView2 Evergreen Runtime 恢复

若要删除 `ReleaseChannelPreference` 注册表替代，请运行以下命令：

`REG DELETE HKLM\Software\Policies\Microsoft\Edge\WebView2\ReleaseChannelPreference /f`


<!-- 4. Environment Variable ========================================================================-->
## <a name="using-an-environment-variable"></a>使用环境变量

若要使应用程序使用环境变量Microsoft Edge预览通道：

1.  在"Windows"栏中，输入"environment"，然后选择"**编辑系统环境变量"。**

    :::image type="complex" source="./media/search-bar-edit-sys-env-vars.png" alt-text="使用Windows搜索栏查找编辑环境变量的地方" lightbox="./media/search-bar-edit-sys-env-vars.png":::
       使用Windows搜索栏查找编辑环境变量的地方
    :::image-end:::

1.  在" **系统属性** "对话框中，选择" **高级"选项卡** ，然后选择" **环境变量"** 按钮。

    :::image type="complex" source="./media/system-properties-env-vars.png" alt-text="&quot;系统属性&quot;对话框中的&quot;环境变量&quot;按钮" lightbox="./media/system-properties-env-vars.png":::
       " **系统属性"** 对话框中的" **环境变量"** 按钮
    :::image-end:::

1.  在"**环境变量"****对话框的"** 用户变量"部分，选择"新建 **"。**

1.  在"**新建用户变量**"对话框中，将"**** 变量名称"设置为 ，将"变量"值设置为首选 `WEBVIEW2_BROWSER_EXECUTABLE_FOLDER` 浏览器通道的路径。 ****

    或者，将 **"变量名称"** 设置为 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE` ，将 **"变量"值设置为** `1` 。

1.  选择 **"** 确定"关闭对话框。

    :::image type="complex" source="./media/env-vars-new-user-variable.png" alt-text="将新的环境变量作为用户变量添加" lightbox="./media/env-vars-new-user-variable.png":::
       将新的环境变量作为用户变量添加
    :::image-end:::

> [!NOTE]
> 此方法可设置所有 WebView2 应用的环境变量，而不只是要测试的应用。  若要仅为要测试的 WebView2 应用设置此环境变量，如果从命令提示符运行应用，请设置环境变量 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE=1` 。  这仅针对当前命令提示符进程和该实例中任何新的 `cmd.exe` 子进程设置环境 `cmd.exe` 变量。  然后，环境变量仅适用于你正在测试的 WebView2 应用。

> [!NOTE]
> 通过此方式设置环境变量后，环境变量将应用于创建的任何新进程。  环境变量不适用于已在运行的进程。  为了确保所有进程都使用新的环境变量，您可能需要重新启动Visual Studio或注销Windows然后重新登录。


<!--========================================================================-->
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]

<!-- links -->
[WebView2ConceptsVersioning]: ../concepts/versioning.md "了解 WebView2 SDK 版本 | Microsoft Docs"
<!-- external links -->
[Webview2RefWin32GlobalsCreateCoreWebView2EnvironmentWithOptions]: /microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions "CreateCoreWebView2EnvironmentWithOptions - 全局|Microsoft Docs"
[MicrosoftedgeinsiderDownload]: https://www.microsoftedgeinsider.com/download "下载 Microsoft Edge 预览体验成员频道"
