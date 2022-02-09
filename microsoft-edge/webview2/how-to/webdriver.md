---
title: 使用驱动程序自动化和测试 WebView2 Microsoft Edge
description: 使用驱动程序自动化和测试 WebView2 Microsoft Edge。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 12/01/2021
ms.openlocfilehash: 426f99581d50a3ed37ca2a5a97627cbc68df9653
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345791"
---
# <a name="automate-and-test-webview2-apps-with-microsoft-edge-driver"></a>使用驱动程序自动化和测试 WebView2 Microsoft Edge

本文介绍如何使用 Selenium 框架实现浏览器测试自动化，通过 Microsoft Edge 驱动程序自动执行和测试 WebView2 应用。

本文提供了有关使用 Selenium 框架和 C#的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用除 Selenium 外的其他 WebDriver 测试框架完成相同的任务，请参考您所选择的框架的官方文档。

若要为 WebView2 应用创建模拟用户交互的自动测试，可以使用Microsoft Edge驱动程序。  Microsoft Edge驱动程序是 Microsoft 对 W3C [WebDriver 协议的](https://www.w3.org/TR/webdriver2)实现。  W3C WebDriver 协议允许程序控制 Web 浏览器的行为。

测试作者编写使用 WebDriver 命令告诉浏览器执行特定操作的测试。  Microsoft Edge驱动程序接收这些命令，然后要求浏览器执行请求的操作。  Microsoft Edge驱动程序支持自动执行 Microsoft Edge 浏览器和 WebView2 应用。

有关 WebDriver 协议、Microsoft Edge驱动程序作为该协议的实现以及 Selenium 测试框架之间的关系，请参阅 [WebDriver 概述](../../webdriver-chromium/index.md#relationship-between-webdriver-and-other-software)。


<!-- ====================================================================== -->
## <a name="step-1-download-the-webview2api-sample"></a>步骤 1：下载 WebView2API 示例

如果你没有现有的 WebView2 项目，请下载 [WebView2API 示例](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample)应用，这是最新的 WebView2 SDK 的全面示例。  确保你满足 [WebView2API 示例应用的先决条件](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#prerequisites)。

克隆存储库后，在"文件"中生成Visual Studio。  它应如下图所示。

:::image type="content" source="../media/webdriver/sample-app.png" alt-text="WebView2API 示例应用。" lightbox="../media/webdriver/sample-app.png":::


<!-- ====================================================================== -->
## <a name="step-2-install-microsoft-edge-driver"></a>步骤 2：安装Microsoft Edge驱动程序

按照说明安装驱动程序[Microsoft Edge驱动程序](../../webdriver-chromium/index.md#download-microsoft-edge-driver)。  Microsoft Edge驱动程序是 Selenium 自动化和测试 WebView2 所需的特定于浏览器的驱动程序。

确保驱动程序的版本Microsoft Edge你的应用使用的 WebView2 运行时的版本相匹配。  若要使 WebView2API 示例正常工作，请确保你的 WebView2 运行时版本大于或等于最新 WebView2 SDK 版本的受支持版本。

*  若要查找最新的 WebView2 SDK 版本，请参阅 [WebView2 SDK 发行说明](../release-notes.md)。

*  若要了解你当前拥有哪个版本的 WebView2 运行时，请转到 `edge://settings/help`。


<!-- ====================================================================== -->
## <a name="step-3-add-selenium-to-the-webview2api-sample"></a>步骤 3：将 Selenium 添加到 WebView2API 示例

此时，你已安装 WebView2 运行时，生成了 WebView2 项目，并Microsoft Edge驱动程序。  接下来，开始使用 Selenium，如下所示。

1. 首先在 **Visual Studio 中新建**C# .NET Framework**项目**。  选择 **右** 下角的"下一步"继续。

   :::image type="content" source="../media/webdriver/new-project.png" alt-text="创建新项目。" lightbox="../media/webdriver/new-project.png":::

1. 为**项目指定Project**名称，将其保存到首选**位置**，然后选择"创建 **"**。

   :::image type="content" source="../media/webdriver/app-create.png" alt-text="配置新项目。" lightbox="../media/webdriver/app-create.png":::

   将创建一个新项目，所有代码都放置在文件中 `Program.cs` 。

   :::image type="content" source="../media/webdriver/start-app.png" alt-text="新建项目。" lightbox="../media/webdriver/start-app.png":::

1. 接下来，将 Selenium 添加到项目中;使用 Selenium.WebDriver NuGet安装 Selenium，如下所示。  若要下载 Selenium.WebDriver NuGet程序包，请在"**Visual Studio"****** > Project**管理NuGet程序包"**。

1. 选择" **浏览"** 选项卡。 将显示以下屏幕。

   :::image type="content" source="../media/webdriver/download-nuget.png" alt-text="下载NuGet程序包。" lightbox="../media/webdriver/download-nuget.png":::

1. 在" **程序包源** "下拉列表中，选择"nuget.org **"**。

1. 选中 **"包括预发布"** 复选框。

1. 在 `Selenium.WebDriver` 搜索 **栏中键入** ，然后从结果中选择 **Selenium.WebDriver** 。

1. 在右侧的详细信息窗口中，确保" **版本** "设置为 **4.0.0** 或更高版本，然后选择"安装 **"**。  NuGet将 Selenium 下载到你的计算机。

   :::image type="content" source="../media/webdriver/nuget.png" alt-text="管理NuGet包。" lightbox="../media/webdriver/nuget.png":::

   若要了解有关 Selenium.WebDriver 程序包NuGet，请参阅 [Selenium.WebDriver](https://www.nuget.org/packages/Selenium.WebDriver)。

1. 通过 `OpenQA.Selenium.Edge` 添加文件 `using OpenQA.Selenium.Edge;` 开头的 语句来使用 `Program.cs`：

   ```csharp
   using OpenQA.Selenium.Edge;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using System.Threading.Tasks;
   ```

现在，你已设置一个Visual Studio Selenium 测试的空项目。  接下来，使用"启动"方法或"附加"方法将 Selenium 配置为驱动 WebView2。


<!-- ====================================================================== -->
## <a name="step-4-choosing-whether-microsoft-edge-driver-should-launch-your-app-or-attach-to-it"></a>步骤 4：选择Microsoft Edge驱动程序应启动应用还是附加到应用

决定是否使用"启动"或"附加"方法将 Selenium 配置为驱动 WebView2。

*  "启动"方法：在某些情况下，适合让驱动程序Microsoft Edge启动 WebView2 应用。
Microsoft Edge驱动程序启动 WebView2 应用，并自动附加到应用创建的第一个可用的 WebView2 实例。

*  "附加"方法：在其他方案中，适合将Microsoft Edge驱动程序附加到正在运行的 WebView2 实例。  在驱动程序之外启动Microsoft Edge，然后将Microsoft Edge驱动程序附加到正在运行的 WebView2 实例。  此"附加"方法适用于与"启动"方法不兼容的 WebView2 应用。

### <a name="approach-1-letting-microsoft-edge-driver-launch-your-webview2-app"></a>方法 1：让Microsoft Edge驱动程序启动 WebView2 应用
<!-- preferred phrase -->

如果你有一个用于创建单个 WebView2 实例且该实例在启动后立即处于活动状态的简单应用，可以使用"启动"方法;使用[步骤 4a：Microsoft Edge驱动程序启动 WebView2 应用](#step-4a-letting-microsoft-edge-driver-launch-your-webview2-app)。

在此方案中，有一个 WebView2 实例，可在启动时使用，而无需在任何本机 UI 中导航。

### <a name="approach-2-attaching-microsoft-edge-driver-to-a-running-webview2-app"></a>方法 2：将Microsoft Edge驱动程序附加到正在运行的 WebView2 应用
<!-- preferred phrase -->

如果你有任何不符合上述"启动"方案的情况，你应该将 Microsoft Edge 驱动程序附加到正在运行的 WebView2 实例 (而不是让 Microsoft Edge 驱动程序处理 WebView2 启动) ;使用步骤 [4b：将 Microsoft Edge 驱动程序附加到正在运行的 WebView2](#step-4b-attaching-microsoft-edge-driver-to-a-running-webview2-app) 应用。

一些不符合"启动"方案的方案示例如下：
*  创建 WebView2 实例之前，你需要在一些本机 UI 中导航。
*  你的应用将创建多个 WebView2 实例，并且你想要附加到特定实例。

在这种情况下，我们建议附加到 WebView2 的特定实例，因为让 Microsoft Edge 驱动程序启动 WebView2 应用仅适用于相对简单的方案。  当Microsoft Edge驱动程序启动你的应用时，它会自动附加到所创建的第一个 WebView2 实例，如果未找到 WebView2 实例，它将失败。

无论使用"启动"还是"附加"方法，都必须下载 Microsoft Edge Driver，并确保版本与应用使用的 WebView2 运行时版本匹配。  配置 WebDriver 框架应用程序（如 Selenium (）的初始步骤) "启动"与"附加"方法不同。

完成启动应用或附加到 WebView2 实例的初始步骤后，你将能够使用任何受支持的 WebDriver 命令与该 WebView2 实例进行交互。


<!-- ====================================================================== -->
## <a name="step-4a-letting-microsoft-edge-driver-launch-your-webview2-app"></a>步骤 4a：Microsoft Edge驱动程序启动 WebView2 应用
<!-- old title: Drive WebView2 with Selenium and Microsoft Edge Driver -->

如果你拥有创建单个 WebView2 实例且该实例在启动后立即处于活动状态的简单应用，请使用此"启动"方法。  在此方案中，有一个 WebView2 实例，可在启动时使用，而无需在任何本机 UI 中导航。

若要使用 Selenium 和 Microsoft Edge驱动程序驱动 WebView2：

1. `EdgeOptions`通过复制并粘贴以下代码创建对象：

   ```csharp
   static void Main(string[] args)
   {
      EdgeOptions eo = new EdgeOptions();
   ```

   接下来，我们将添加执行以下操作的代码：

   *  将 选项 `EdgeOptions` 设置为 ，将实例配置为使用 `UseWebView` `true`WebView2。
   *  设置为 `eo.BinaryLocation` WebView2 应用二进制文件的文件路径。
   *  使用 实例 `EdgeDriver` 创建 `EdgeOptions` 对象。

1. 复制以下代码并将其粘贴到声明行 `eo` 下方：

   ```csharp
   //Set the EdgeOptions instance to use WebView2
   eo.UseWebView = true;

   //Set the BinaryLocation to the filepath of the WebView2API Sample runtime
   eo.BinaryLocation = @"C:\path\to\your\webview2\project.exe";
   EdgeDriver e = new EdgeDriver(eo);
   ```

1. 在以上代码中，指定项目运行时的正确文件路径和Microsoft Edge驱动程序运行时。

   `EdgeDriver` 现在已配置为驱动项目中的 WebView2。  例如，如果你使用的是 **WebView2API 示例**`https://microsoft.com``e.Url = @"https://www.microsoft.com";`，则现在可以通过运行 命令转到代码，如下一个代码列表所示。

1. 验证 Selenium 能否驱动 WebView2。  为此，请在此行上设置一个断点 `e.Url = @"https://www.microsoft.com";`，然后运行该项目。

   ```csharp
      //Navigate the WebView2API Sample from bing.com to microsoft.com
      e.Url = @"https://www.microsoft.com";

      //Exit Microsoft Edge Driver
      e.Quit();
   }
   ```

   :::image type="content" source="../media/webdriver/microsoft.png" alt-text="运行 WebView2 的 Selenium。" lightbox="../media/webdriver/microsoft.png":::

祝贺你！  根据"启动"方法，你已使用 Selenium 和 Microsoft Edge Driver 成功自动化了 WebView2 项目和驱动 WebView2。

如果使用的是"启动"方法，那么本文将结束。


<!-- ====================================================================== -->
## <a name="step-4b-attaching-microsoft-edge-driver-to-a-running-webview2-app"></a>步骤 4b：将Microsoft Edge驱动程序附加到正在运行的 WebView2 应用
<!-- description: Automating a WebView2 instance in an already-running application by attaching Edge Driver to the WebView2 app. -->

本部分介绍如何将驱动程序Microsoft Edge一个已运行的 WebView2 实例。  如果还没有单个 WebView2 实例，或者 WebView2 实例需要在某些本机 UI 中导航，请使用此部分和方法。

一个问题就是，若要自动化基于 WebView2 的应用，有时首先需要在本机 GUI 中执行一些操作才能启动 WebView2 控件。  作为一种解决方案，你需要在驱动程序之外Microsoft Edge本机 UI，并以某种方式确保 WebView2 实例显示，如下所示。

在此方案中，你需要导航一些本机 UI，你将使用 Microsoft Edge Driver（如命令行脚本）或单独的工具（如 WinAppDriver）来启动你的应用。 启动应用进程后，触发 WebView2 实例化，然后将Microsoft Edge驱动程序附加到正在运行的 WebView2 实例。

Microsoft Edge驱动程序不处理本机 UI 自动化，但下面是一些导航本机 UI 和显示要自动处理的 WebView2 实例的其他方法：

*  Windows应用程序驱动程序 ([WinAppDriver](https://github.com/Microsoft/WinAppDriver)) 是一项支持 Windows 应用程序上的 Selenium 类似 UI 测试自动化的服务。  此服务支持在 Windows 10 PC 上测试通用 Windows 平台 (UWP) 、Windows Forms (WinForms) 、Windows Presentation Foundation (WPF) 和经典 Windows (Win32) 应用。

*  直接使用 Microsoft Native UI 自动化。  [Microsoft UI 自动化](/windows/win32/winauto/entry-uiauto-win32)框架允许自动测试脚本与 UI 进行交互。  Microsoft UI 自动化使Windows应用程序能够提供和使用有关用户界面和 UI (编程) 。  它提供对桌面上大多数 UI 元素的编程访问。  它使辅助技术产品（如屏幕阅读器）能够向最终用户提供有关 UI 的信息，并按标准输入和标准输入外的其他方式操作 UI。 <!-- condense that; 1st para -->

* 使用命令行参数或环境变量等标志告诉应用直接启动到 WebView2 实例，以避免导航本机 UI。  根据您的方案，这或许可以使用步骤 [4a：让驱动程序启动 WebView2 Microsoft Edge中所述的"启动"方法](#step-4a-letting-microsoft-edge-driver-launch-your-webview2-app)。  <!-- create a special test mode that displays x. -->

除了确保激活 WebView2 实例之外，还需要设置其 `--remote-debugging-port` 命令行参数。  我们将在以下步骤中完成此操作。  Microsoft Edge驱动程序将使用此远程调试端口连接到 WebView2 实例。

### <a name="launching-the-webview2-app-with-remote-debugging-enabled"></a>启用远程调试后启动 WebView2 应用

当你对应用进行编码时，将执行下一步。  实例化 WebView2 控件时，需要提供此额外的命令行参数。  启用远程调试，如下所示。

1. 在 WebView2 Win32 `--remote-debugging-port=<port>` C++ 参考中，使用 Globals 中推荐的方法之一，使用附加命令行参数配置 [WebView2 实例](/microsoft-edge/webview2/reference/win32/0-9-538/webview2-idl)。  为此参数选择可用的端口号。

1. 启动你的应用。  如何启动应用取决于你使用的其他本机 UI 测试工具。

此时，你的应用正在运行，并且 `--remote-debugging-port` 已设置其命令行参数。  接下来，我们将驱动程序Microsoft Edge启动的 WebView2 应用。

### <a name="attaching-microsoft-edge-driver-to-the-launched-webview2-app"></a>将Microsoft Edge驱动程序附加到启动的 WebView2 应用

1. `EdgeOptions.DebuggerAddress`使用 属性告诉Microsoft Edge驱动程序连接到你之前指定的远程调试端口，而不是启动新应用程序：

```csharp
EdgeOptions eo = new EdgeOptions();
eo.UseWebView = true;
eo.DebuggerAddress = "localhost:9222";
EdgeDriver e = new EdgeDriver(eo);
```

上面 `localhost:9222` ，此行上给出的端口号应该与以上设置时选择的端口号 `--remote-debugging-port` 匹配。

有关对象的属性 `DebuggerAddress` 详细信息 `EdgeOptions` ，请参阅 [EdgeOptions 对象](../../webdriver-chromium/capabilities-edge-options.md#edgeoptions-object)。

祝贺你！  通过使用 Selenium 和 Microsoft Edge Driver，将 Microsoft Edge Driver 附加到正在运行的 WebView2 应用，你已成功自动化 WebView2 项目和驱动 WebView2。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Selenium 文档中的 WebDriver](https://www.selenium.dev/documentation/en/webdriver) - API Selenium 如何驱动 WebView2 或 Microsoft Edge。
* [WebView2 Microsoft Edge](../index.md)简介 - 如何使用 WebView2 控件在本机应用中嵌入 Web 内容。
* [使用 WebDriver 实现测试自动化](../../webdriver-chromium/index.md) - 自动化Microsoft Edge。
