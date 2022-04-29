---
title: 测试即将推出的 API 和功能
description: 如何指定要使用的Microsoft Edge预览频道，以测试预发行包中的试验性 API。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 7d4fee6d9588bad84b87a0e687aaf8cc9941edf3
ms.sourcegitcommit: b2062efd99182cb0b6c3115439fb45838841b276
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497105"
---
# <a name="test-upcoming-apis-and-features"></a>测试即将推出的 API 和功能
<!-- old title: # Switch to a preview channel to test upcoming APIs and features -->

若要测试即将推出的 API 和功能，请切换到预览频道，如下所示。

WebView2 Evergreen 运行时的更新通常包括新的 API 和功能。  其中一些更新可能会破坏 WebView2 应用。  若要提前测试实验性 API 并确保应用的前向兼容性，应使用预览版Microsoft Edge通道以及 WebView2 SDK 的预发行版本执行兼容性测试。

测试预发行版 SDK 包时，需要指示应用程序使用 Microsoft Edge (Beta、Dev 或 Canary) 的预览通道，而不是默认使用 WebView2 运行时。  下面介绍了执行此操作的几种方法。

WebView2 运行时没有最新的实验性 WebView2 API。  若要在预发行版 SDK 中使用实验性 API 时运行 WebView2 代码，客户端 (开发计算机上) 需要有一个Microsoft Edge预览频道。  建议使用 Canary 预览频道，因为它领先于其他通道并具有最新的实验性 API。

预发行版 SDK 与预览频道协同工作，如下所示：

*  WebView2 SDK 的预发行版本包含实验性 API 的方法签名，允许你使用应用中的试验性 WebView2 API 编写代码。

*  Microsoft Edge的预览频道包含运行和呈现应用所需的Microsoft Edge二进制文件，包括实验性 API 的实现。

有关 SDK 版本如何与 WebView2 运行时或Microsoft Edge的预览频道协同工作的详细信息，请参阅[了解不同的 WebView2 SDK 版本](../concepts/versioning.md)。


<!-- ====================================================================== -->
## <a name="downloading-the-prerelease-sdk-and-a-preview-channel"></a>下载预发行版 SDK 和预览频道

若要使用实验性 API，请从 [Microsoft.Web.WebView2 包](https://www.nuget.org/packages/Microsoft.Web.WebView2)下载 WebView2 SDK 的预发行版本。

若要下载Microsoft Edge预览频道，[请参阅Microsoft Edge预览体验成员频道](https://www.microsoftedgeinsider.com/download)。


<!-- intro/overview of 4 approaches ======================================= -->
## <a name="approaches-to-making-your-app-use-a-specific-browser-channel"></a>使应用使用特定浏览器通道的方法

初始化 WebView2 时，它将尝试在计算机上查找要使用的有效运行时。 这可以是 WebView2 运行时、Microsoft Edge的预览通道或包含固定版本二进制文件的指定位置。 可以在 [“分发应用”和“WebView2 运行时](../concepts/distribution.md)”中详细了解支持的运行时。

可以通过多种方式使 WebView2 应用使用指定的预览频道Microsoft Edge：
*  通过调用函数。
*  通过使用组策略。
*  通过使用注册表替代。
*  使用环境变量。

下面介绍了这些方法。

### <a name="browser-executable-folder"></a>浏览器可执行文件夹

一种方法是使用浏览器可执行文件夹。  在此方法中，指定包含运行时二进制文件的文件夹。 此文件夹可以是以下任一位置：
*  WebView2 运行时的安装位置。
*  Microsoft Edge的预览频道。
*  包含已自行部署到计算机的固定版本二进制文件的文件夹。

如果将浏览器可执行文件夹设置为特定的Microsoft Edge预览频道，则需要在该预览频道更新到较新版本时更新该位置。 这是因为该位置包含版本号作为其路径的一部分。 因此，我们建议仅将此方法用于本地测试。

### <a name="default-channel-search-order"></a>默认通道搜索顺序

本部分适用于使用组策略、注册表重写或环境变量。

如果未指定特定的浏览器可执行文件夹，则 WebView2 将尝试从已知的默认位置之一加载运行时。

默认通道搜索顺序为：
1. WebView2 运行时。
1. Microsoft Edge的 Beta 通道。
1. Microsoft Edge的开发通道。
1. Microsoft Edge的金丝雀通道。

如果使用组策略、注册表重写或环境变量将发布通道首选项设置为 `1` ，则使用默认搜索顺序的反向。


<!-- 1. Code ============================================================== -->
## <a name="using-code"></a>使用代码

如果要通过调用函数使应用程序使用特定运行时，请完成以下步骤。

### <a name="win32c"></a>Win32\/C++

我们将使用 [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample) 来演示此过程。

1. 在开发计算机上，找到包含Microsoft Edge预览频道的路径。  例如：

   `C:\\Users\\myname\\AppData\\Local\\Microsoft\\Edge SxS\\Application\\93.0.929.0`

1. 克隆 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库。

1. 打开 **WebView2APISample** 项目，然后在 **源文件**中打开文件 `AppWindow.cpp` 。

1. 查找 [调用 CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions) 的位置。  例如：

   ```cpp
   HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
       subFolder, m_userDataFolder.c_str(), options.Get(),
       Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
           this, &AppWindow::OnCreateEnvironmentCompleted)
           .Get());
   ```

1. `subFolder`将变量替换为要使用的Microsoft Edge预览通道的文件夹路径。  例如：

   ```cpp
   HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
       L"C:\\Users\\myname\\AppData\\Local\\Microsoft\\Edge SxS\\Application\\93.0.929.0", m_userDataFolder.c_str(), options.Get(),
       Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
           this, &AppWindow::OnCreateEnvironmentCompleted)
           .Get());
   ```

### <a name="winforms"></a>WinForms

WinForms 使用类似于上述 Win32/C++ 方法的方法。

1. 设置`CreationProperties.BrowserExecutableFolder`为指向包含Microsoft Edge Canary 或 Dev 通道的路径。  为此，请在 **WebView2Samples** 解决方案中的 **WebView2WpfBrowser** 项目中打开文件 `MainWindow.xaml.cs`。

1. 查找 `CreationProperties.BrowserExecutableFolder`。  例如：

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

WPF 使用类似于上述 Win32/C++ 方法的方法。

请参阅 [CoreWebView2CreationProperties.BrowserExecutableFolder 属性](/dotnet/api/microsoft.web.webview2.wpf.corewebview2creationproperties.browserexecutablefolder#Microsoft_Web_WebView2_Wpf_CoreWebView2CreationProperties_BrowserExecutableFolder)。


<!-- 2. Group Policy ====================================================== -->
## <a name="using-a-group-policy"></a>使用组策略

如果要让应用程序使用Microsoft Edge预览频道，请使用组策略将 ADMX 和 ADML 文件复制到`PolicyDefinitions`文件夹，如下所示。

1. 从[“下载”下载策略文件并部署业务Microsoft Edge](https://www.microsoft.com/edge/business/download)。

1. 将 ADMX 文件复制到策略定义模板文件夹中，例如 `C:\Windows\PolicyDefinitions`。

1. 将 ADML 文件复制到文件夹中的 `Policy Definitions` 匹配区域设置文件夹中，例如 `C:\Windows\PolicyDefinitions\en-us` 文件夹。

1. 打开**本地组策略编辑器**。  为此，请在Windows搜索栏中键入“组策略”，然后选择 **“编辑组策略**”。

1. 展开 **本地计算机策略**，然后展开 **计算机配置** 或 **用户配置**。  然后展开**管理模板** > **Microsoft Edge WebView2**。

   :::image type="content" source="media/local-group-policy-editor.png" alt-text="本地组策略编辑器对话框。":::

1. 选择 **“浏览器可执行文件夹**”。  以下屏幕截图适用于设置 **浏览器可执行文件夹**。  或者，选择使用类似对话框的 **“发布通道首选**项”。

   :::image type="content" source="media/browser-executable-folder.png" alt-text="设置浏览器可执行文件夹。":::

1. 选择 **“显示** ”按钮。

1. 填写“ **显示内容** ”对话框。  在 **“值名称** ”列中，输入一个星号以应用于所有 WebView2 应用，或 `.exe` 输入仅影响指定 WebView2 应用的文件名。  在 **“值** ”列中，输入 WebView2 应用的可执行文件的路径。

   :::image type="content" source="media/show-contents.png" alt-text="“显示内容”对话框。":::

1. 选择 **“确定** ”以关闭对话框。

有关详细信息，请参阅[配置Microsoft Edge策略设置](/deployedge/configure-microsoft-edge)。


<!-- 3. Registry Override ================================================= -->
## <a name="using-a-registry-override"></a>使用注册表替代

使用注册表替代指定预览频道时，有两个选项：
*  更改浏览器可执行文件夹。
*  更改发布通道首选项。

下面介绍了这两种方法。

### <a name="registry-override-browser-executable-folder"></a>注册表重写：浏览器可执行文件夹

若要使应用程序使用Microsoft Edge预览通道，请使用设置浏览器可执行文件夹的注册表替代：

1. 打开 PowerShell 终端或启用了 PowerShell 的命令提示符。

1. 修改并运行以下命令：

   `REG ADD HKLM\Software\Policies\Microsoft\Edge\WebView2\BrowserExecutableFolder /v * /t REG_SZ /d "C:\Users\myname\AppData\Local\Microsoft\Edge SxS\Application\88.0.680.0"`

   星号 (*) 值名称使此替代应用于所有 WebView2 应用。  如果只想将此替代应用到特定的 WebView2 应用，请将星号替换为应用的可执行文件的文件名。

   替换`C:\Users\myname\AppData\Local\Microsoft\Edge SxS\Application\88.0.680.0`为所需Microsoft Edge预览频道的路径。

#### <a name="resuming-using-the-default-webview2-evergreen-runtime"></a>使用默认的 WebView2 Evergreen 运行时恢复

若要撤消上述设置，请运行以下命令：

`REG DELETE HKLM\Software\Policies\Microsoft\Edge\WebView2\BrowserExecutableFolder /f`

### <a name="registry-override-release-channel-preference"></a>注册表重写：发布通道首选项

若要使应用程序使用Microsoft Edge预览频道，请使用注册表替代，通过更改搜索通道的顺序来更改发布通道首选项：

1. 打开 PowerShell 终端或启用了 PowerShell 的命令提示符。

1. 修改并运行以下命令：

   `REG ADD HKLM\Software\Policies\Microsoft\Edge\WebView2\ReleaseChannelPreference /v * /t REG_SZ /d "1"`

   星号 (*) 值名称使此替代应用于所有 WebView2 应用。  如果只想将此替代应用到特定的 WebView2 应用，请将星号替换为应用的可执行文件的文件名。

#### <a name="resuming-using-the-default-webview2-evergreen-runtime"></a>使用默认的 WebView2 Evergreen 运行时恢复

若要 `ReleaseChannelPreference` 删除注册表重写，请运行以下命令：

`REG DELETE HKLM\Software\Policies\Microsoft\Edge\WebView2\ReleaseChannelPreference /f`


<!-- 4. Environment Variable ============================================== -->
## <a name="using-an-environment-variable"></a>使用环境变量

若要使应用程序使用Microsoft Edge预览通道，请使用环境变量：

1. 在Windows搜索栏中，输入“环境”，然后选择 **“编辑系统环境变量**”。

   :::image type="content" source="media/search-bar-edit-sys-env-vars.png" alt-text="使用Windows搜索栏查找编辑环境变量的位置。":::

1. 在 **“系统属性** ”对话框中，选择 **“高级** ”选项卡，然后选择 **“环境变量** ”按钮。

   :::image type="content" source="media/system-properties-env-vars.png" alt-text="“系统属性”对话框中的“环境变量”按钮。":::

1. 在 **“环境变**量”对话框的“**用户变量**”部分中，选择 **“新建**”。

1. 在 **“新建用户变量**”对话框中，将**变量名称**设置为`WEBVIEW2_BROWSER_EXECUTABLE_FOLDER`**，并将变量值**设置为首选浏览器通道或固定版本二进制文件的路径。

   或者，将**变量名称**设置为`WEBVIEW2_RELEASE_CHANNEL_PREFERENCE`**，并将 Variable 值**设置为`1`反转搜索顺序，以便先使用 beta、Dev 或 Canary (预览频道) 。 除任何值外，任何值都 `1` 指示默认搜索顺序。

1. 单击 **“确定** ”关闭对话框。

   :::image type="content" source="media/env-vars-new-user-variable.png" alt-text="将新环境变量添加为用户变量。":::

### <a name="which-app-is-affected"></a>哪个应用受到影响

上述方法为所有 WebView2 应用设置环境变量，而不仅仅是要测试的应用。  若要仅为要测试的 WebView2 应用设置此环境变量，如果要从命令提示符运行应用，请设置环境变量 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE=1`。  这仅针对当前 `cmd.exe` 命令提示符进程和来自该 `cmd.exe` 实例的任何新子进程设置环境变量。  然后，环境变量仅适用于要测试的 WebView2 应用。

如果使用 `WEBVIEW2_RELEASE_CHANNEL_PREFERENCE` 环境变量，可以将其设置为以下值。

| 值 | 描述 |
|---|---|
| `1` | 反转搜索顺序，首先在 WebView2 运行时之前使用 [预览频道](https://www.microsoftedgeinsider.com/download) 。 |
| `0` 或其他非值 `1` | 使用 [默认通道搜索顺序](#default-channel-search-order)，即在预览频道之前使用 WebView2 运行时。 |

### <a name="applying-the-new-environment-variable-to-running-processes"></a>将新环境变量应用于正在运行的进程

设置环境变量后，环境变量将应用于创建的任何新进程。  环境变量不适用于已运行的进程。  若要确保所有进程都使用新的环境变量，可能需要重启Visual Studio，或者注销Windows，然后再次登录。
