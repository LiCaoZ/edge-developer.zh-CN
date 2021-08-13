---
description: 使用驱动程序自动化和测试 WebView2 Microsoft Edge
title: 使用驱动程序自动化和测试 WebView2 Microsoft Edge驱动程序
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/14/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、edge、ICoreWebView2、ICoreWebView2Controller、Selenium、Microsoft Edge Driver
ms.openlocfilehash: 3fe9661f6d1a34def6d969deaf5f87d8e9aba312
ms.sourcegitcommit: 14f24d1af5a39c890467c337468b76c7a00429d2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676754"
---
# <a name="automate-and-test-webview2-with-microsoft-edge-driver"></a>使用驱动程序自动化和测试 WebView2 Microsoft Edge驱动程序  

由于 WebView2 使用 Microsoft Edge \(Chromium\) Web 平台，因此 WebView2 开发人员可以利用标准 Web 工具进行调试和自动化。  Selenium 是此类工具之一。  它实现 W3C [WebDriver][W3cWebdriver2] API。  可以使用 Selenium 创建自动测试来模拟用户交互。  

开始执行以下步骤。  

## <a name="step-1-download-the-webview2api-sample"></a>步骤 1：下载 WebView2API 示例  

如果你没有现有的 WebView2 项目，请下载 [WebView2API 示例][GithubMicrosoftedgewebview2samplesSampleappsWebview2apisample]应用，这是最新的 WebView2 SDK 的全面示例。  确保你已满足 [WebView2API 示例应用的先决条件][GithubMicrosoftedgeWebview2samplesSampleappsWebview2apisamplePrerequisites]。  

克隆存储库后，在"文件"中生成Visual Studio。  它应如下图所示。  

:::image type="complex" source="../media/webdriver/sample-app.png" alt-text="WebView2API 示例应用" lightbox="../media/webdriver/sample-app.png":::
   WebView2API 示例应用  
:::image-end:::    

## <a name="step-2-install-microsoft-edge-driver"></a>步骤 2：安装Microsoft Edge驱动程序  

按照说明安装驱动程序[Microsoft Edge驱动程序][WebdriverChromiumDownloadMicrosoftEdgeDriver]。  Microsoft EdgeDriver 是 Selenium 自动化和测试 WebView2 所需的特定于浏览器的驱动程序。  

确保驱动程序的版本Microsoft Edge你的应用使用的 WebView2 运行时的版本相匹配。  若要使 WebView2API 示例正常工作，请确保你的 WebView2 运行时版本大于或等于最新 WebView2 SDK 版本的受支持版本。

*  若要查找最新的 WebView2 SDK 版本，请导航到 [WebView2 SDK 的发行说明][Webview2ReleaseNotes]。
*  若要了解当前具有的 WebView2 运行时版本，请导航到 `edge://settings/help` 。  

## <a name="step-3-add-selenium-to-the-webview2api-sample"></a>步骤 3：将 Selenium 添加到 WebView2API 示例  

此时，你已安装 WebView2 运行时，生成了 WebView2 项目，并Microsoft Edge驱动程序。  接下来，开始使用 Selenium，如下所示。

> [!NOTE]
> Selenium 支持 C\#、Java、Python、Javascript 和 Ruby。  但是，以下指南是使用 C\# 编写的。  

1.  首先，在**Visual Studio**新建C# .NET Framework**项目**。  选择 **右** 下角的"下一步"继续。  
    
    :::image type="complex" source="../media/webdriver/new-project.png" alt-text="创建新项目" lightbox="../media/webdriver/new-project.png":::
       创建新项目  
    :::image-end:::  
    
1.  为**项目命名**Project，将其保存到首选**位置**，然后选择"创建 **"。**  
    
    :::image type="complex" source="../media/webdriver/app-create.png" alt-text="配置新项目" lightbox="../media/webdriver/app-create.png":::
       配置新项目  
    :::image-end:::  
    
    将创建一个新项目，并放入文件的所有 `Program.cs` 代码。  
    
    :::image type="complex" source="../media/webdriver/start-app.png" alt-text="新建项目" lightbox="../media/webdriver/start-app.png":::
       新建项目  
    :::image-end:::  
    
1.  接下来，将 Selenium 添加到项目中;使用 Selenium.WebDriver NuGet安装 Selenium，如下所示。  若要下载 Selenium.WebDriver NuGet程序包，请在"Visual Studio"Project管理NuGet********  >  **程序包"。**

1.  选择" **浏览"** 选项卡。 将显示以下屏幕。  
    
    :::image type="complex" source="../media/webdriver/download-nuget.png" alt-text="下载NuGet包" lightbox="../media/webdriver/download-nuget.png":::
       下载NuGet包  
    :::image-end:::  
    
1.  在"**程序包源**"下拉列表中，选择 **"nuget.org"。**

1.  选中 **"包括预发布"** 复选框。

1.  在 `Selenium.WebDriver` 搜索**栏中键入**，然后从结果中选择**Selenium.WebDriver。**

1.  在右侧的详细信息窗口中，确保"**版本**"设置为**4.0.0-beta4**或更高版本，然后选择"安装 **"。**  NuGet将 Selenium 下载到计算机。  
    
    :::image type="complex" source="../media/webdriver/nuget.png" alt-text="管理NuGet包" lightbox="../media/webdriver/nuget.png":::
       管理NuGet包  
    :::image-end:::  
    
    若要了解有关 Selenium.WebDriver NuGet包的详细信息，请导航到[Selenium.WebDriver 4.0.0-beta4。][NugetSeleniumWebdriver700beta4]  
    
1.  `OpenQA.Selenium.Edge`通过添加文件 `using OpenQA.Selenium.Edge;` 开头的 语句 `Program.cs` 来使用。  
    
    ```csharp
    using OpenQA.Selenium.Edge;
    
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    ```  
    
## <a name="step-4-drive-webview2-with-selenium-and-microsoft-edge-driver"></a>步骤 4：使用 Selenium 和 Microsoft Edge 驱动程序驱动 WebView2  

1.  若要使用 Selenium 和 Microsoft Edge 驱动 WebView2，请首先通过复制并粘贴以下代码段来创建 `EdgeOptions` 对象。  
    
    ```csharp
    static void Main(string[] args)
    {
        EdgeOptions edgeOptions = new EdgeOptions();
    ```  
    
1.  接下来，我们将添加执行以下操作的代码：

    *   将 `edgeOptions` 选项和 Chromium 配置为使用 WebView2 和 `UseChromium` `UseWebView` `true` 。
    *   设置为 `edgeOptions.BinaryLocation` 主机应用二进制文件的文件路径。
    *   使用 `EdgeDriver` 创建对象 `edgeOptions` 。  
    
    复制以下代码并将其粘贴到下方 `edgeOptions` 。

    ```csharp
    //Set edgeOptions to use Chromium and WebView2
    edgeOptions.UseChromium = true;
    edgeOptions.UseWebView = true;

    //Set the BinaryLocation to the filepath of the WebView2API Sample runtime
    edgeOptions.BinaryLocation = @"C:\path\to\your\webview2\project.exe";
    EdgeDriver edgeDriver = new EdgeDriver(edgeOptions);
    ```  

1.  在以上代码中，指定项目运行时的正确文件路径和Microsoft Edge驱动程序运行时。  
    
    `EdgeDriver` 现在已配置为驱动项目中的 WebView2。  例如，如果你使用的是 **WebView2API 示例**，你的代码现在可以通过运行 命令导航到 ，如下一个代码列表 `https://microsoft.com` `e.Url = @"https://www.microsoft.com";` 所示。

1.  通过设置行上的断点并运行项目，验证 Selenium 能否驱动 `e.Url` WebView2。  
    
    ```csharp
        //Navigate the WebView2API Sample from bing.com to microsoft.com
        e.Url = @"https://www.microsoft.com";
        
        //Exit Microsoft Edge Driver
        e.Quit();
    }
    ```  
    
    :::image type="complex" source="../media/webdriver/microsoft.png" alt-text="运行 WebView2 的 Selenium" lightbox="../media/webdriver/microsoft.png":::
       运行 WebView2 的 Selenium  
    :::image-end:::
    
恭喜。  通过使用 Selenium 和 Microsoft Edge Driver 成功自动化了 WebView2 项目和驱动 WebView2。  

> [!Note]
> [edge-selenium-tools][GithubSeleniumProject]是 Microsoft Edge 团队创建的项目，以允许 Selenium 3 用户使用 Selenium 4 中提供的相同 API 驱动 Edge Chromium 和 WebView2。

## <a name="see-also"></a>另请参阅  

*   若要全面了解 API Selenium 如何驱动 WebView2 或 Microsoft Edge \(Chromium\) ，请导航到 Selenium 文档 上的[WebDriver。][SeleniumWebdriver]
*   若要了解有关 WebView2 控件以及如何在本机应用中嵌入 Web 内容时使用它，请导航到"Microsoft Edge [WebView2"。][WebViewIndex]
*   若要了解有关自动执行 Microsoft Edge \(Chromium\) ，请导航到"使用[WebDriver (Chromium) 实现测试自动化"。][WebdriverChromium]
    
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队  

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]  

<!-- links -->  
[WebdriverChromium]: ../../webdriver-chromium/index.md "将 WebDriver (Chromium) 用于测试自动化|Microsoft Docs"  
[WebdriverChromiumDownloadMicrosoftEdgeDriver]: ../../webdriver-chromium/index.md#download-microsoft-edge-driver "下载Microsoft Edge驱动程序 - 使用 WebDriver (Chromium) 测试自动化|Microsoft Docs"  
[WebViewIndex]: ../index.md "WebView2 Microsoft Edge简介 - Microsoft Docs"  
[Webview2ReleaseNotes]: ../release-notes.md "WebView2 SDK |Microsoft Docs"  
<!-- external links -->
[MicrosoftDeveloperMicrosoftEdgeWebDriverDownloads]: https://developer.microsoft.com/microsoft-edge/tools/webdriver#downloads "下载 WebDriver |Microsoft Edge开发人员"  

[GithubMicrosoftedgewebview2samplesSampleappsWebview2apisample]: https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample "WebView2 API 示例 - MicrosoftEdge/WebView2Samples |GitHub"  
[GithubMicrosoftedgeWebview2samplesSampleappsWebview2apisamplePrerequisites]: https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample#prerequisites "先决条件 - WebView2 API 示例|GitHub"  

[NugetSeleniumWebdriver700beta4]: https://www.nuget.org/packages/Selenium.WebDriver/4.0.0-beta4 "Selenium.WebDriver 4.0.0-beta4 |NuGet库"  

[SeleniumWebdriver]: https://www.selenium.dev/documentation/en/webdriver "WebDriver |Selenium"  

[W3cWebdriver2]: https://www.w3.org/TR/webdriver2 "WebDriver |W3C"  

[GithubSeleniumProject]: https://github.com/microsoft/edge-selenium-tools "Selenium Tools for Microsoft Edge"
