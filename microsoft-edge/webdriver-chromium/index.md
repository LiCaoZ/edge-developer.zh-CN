---
description: 了解如何在 WebDriver 中测试网站或Microsoft Edge或自动执行浏览器
title: 使用 WebDriver 自动Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/24/2021
ms.topic: article
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge， Web 开发， html， css， javascript， 开发人员， webdriver， selenium， 测试， 工具， 自动化， 测试
ms.openlocfilehash: 9059842c8c28bea923203d6753f18d7553d6fdd7
ms.sourcegitcommit: 1778d99be7de1fb2f5fda50b0891415922dc5b38
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2021
ms.locfileid: "12177050"
---
# <a name="use-webdriver-to-automate-microsoft-edge"></a>使用 WebDriver 自动Microsoft Edge

WebDriver 允许开发人员通过Microsoft Edge用户交互来自动执行部署。  WebDriver 测试和模拟与 JavaScript 单元测试在以下方面有所不同。

*   访问在浏览器中运行的 JavaScript 不可用的功能和信息。
*   更精确地模拟用户事件或操作系统级事件。
*   在单个测试会话中管理多个窗口、选项卡和网页。
*   运行特定计算机上Microsoft Edge会话的会话。


<!-- ====================================================================== -->
## <a name="relationship-between-webdriver-and-other-software"></a>WebDriver 和其他软件之间的关系

若要自动Microsoft Edge WebDriver 自动执行用户交互，您需要三个组件：

*  Microsoft Edge
*  Microsoft Edge 驱动程序
*  WebDriver 测试框架

这些组件之间的功能关系如下所示。

| 技术 | 角色 |
|---|---|
| WebDriver | 适用于平台和中性语言的线路协议的 W3C 标准。  此协议允许进程外程序远程指示 Web 浏览器的行为。 |
| Microsoft Edge 驱动程序 | Microsoft 专为用户实现 WebDriver 协议Microsoft Edge。  测试作者编写使用 Driver 接收的 WebDriver Microsoft Edge的测试。  Microsoft Edge驱动程序随后负责将该命令与浏览器通信。 |
| WebDriver 测试框架 | 测试作者使用测试框架编写端到端测试并自动化浏览器。  提供一个特定语言的接口，该接口将你的代码转换为驱动程序在Microsoft Edge中运行Microsoft Edge。  WebDriver 测试框架适用于所有主要平台和语言。  这样的框架之一是 Selenium。 |
| Internet Explorer驱动程序 | 专用于 webDriver 协议的实现Internet Explorer。  若要为最终用户运行传统端到端测试Internet Explorer，我们建议使用 Internet Explorer Driver。 |

以下各节介绍如何开始使用 WebDriver for Microsoft Edge。


<!-- ====================================================================== -->
## <a name="download-microsoft-edge-driver"></a>下载 Microsoft Edge 驱动程序

若要开始自动执行测试，请确保安装的 WebDriver 版本与浏览器版本匹配，如下所示。

1.  转到 并 `edge://settings/help` 记下你的Microsoft Edge。

    :::image type="content" source="./media/microsoft-edge-version.msft.png" alt-text="2021 年 4 Microsoft Edge 15 日。" lightbox="./media/microsoft-edge-version.msft.png":::

1.  转到[Microsoft Edge驱动程序。](https://developer.microsoft.com/microsoft-edge/tools/webdriver)

1.  在**页面的"获取最新版本**"部分，单击频道中与最新版本匹配的平台Microsoft Edge。

    :::image type="content" source="./media/microsoft-edge-driver-install.msft.png" alt-text="The 'Get the latest version' section of the Microsoft Edge Driver webpage." lightbox="./media/microsoft-edge-driver-install.msft.png":::


<!-- ====================================================================== -->
## <a name="choose-a-webdriver-testing-framework"></a>选择 WebDriver 测试框架

下载驱动程序Microsoft Edge，必须下载的最后一个组件是 WebDriver 测试框架。  测试作者使用 WebDriver 测试框架编写端到端测试并自动化浏览器。  该框架提供了一个特定语言的接口，该接口将代码 (（如 Python、Java、C#、Ruby 或 JavaScript) ）转换为 Microsoft Edge Driver 在 Microsoft Edge 中运行的命令。  WebDriver 测试框架适用于所有主要平台和语言。

本文提供了有关使用 Selenium 框架的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用除 Selenium 外的其他 WebDriver 测试框架完成相同的任务，请参考您所选择的框架的官方文档。

如果你使用的是 Selenium，Microsoft Edge推荐[Selenium 4](https://www.nuget.org/packages/Selenium.WebDriver)或更高版本，因为该版本的 Selenium 支持Microsoft Edge。  但是，你可以控制Microsoft Edge Selenium 的所有旧版本（包括 Selenium 3）中的版本。

### <a name="using-selenium-4"></a>使用 Selenium 4

Selenium WebDriver 测试框架可用于任何平台，可用于 Java、Python、C#、Ruby 和 JavaScript。

Selenium 4 内置支持Microsoft Edge。  若要安装 Selenium 4，请参阅 [安装 Selenium 库](https://www.selenium.dev/documentation/en/selenium_installation/installing_selenium_libraries)。

如果使用 Selenium 4，则无需使用 Selenium Tools for Microsoft Edge。  Selenium Tools for Microsoft Edge仅适用于 Selenium 3。  如果您尝试将 Selenium 4 与 Selenium Tools for Microsoft Edge并尝试创建新实例，则 `EdgeDriver` 收到以下错误： `System.MissingMethodException: 'Method not found: 'OpenQA.Selenium.Remote.DesiredCapabilities OpenQA.Selenium.DriverOptions.GenerateDesiredCapabilities(Boolean)'` 。

如果你使用的是 Selenium 4 并收到此错误，请从项目中删除 ，并确保你正在使用命名空间中的 official 和 `Microsoft.Edge.SeleniumTools` `EdgeOptions` `EdgeDriver` `OpenQA.Selenium.Edge` 类。

### <a name="using-selenium-3"></a>使用 Selenium 3

如果你已使用[Selenium 3，](https://www.selenium.dev)你可能已有浏览器测试，并且想要在不更改 Selenium 版本Microsoft Edge添加适用于该浏览器的覆盖范围。  若要使用[Selenium 3](https://www.selenium.dev)为旧版 EdgeHTML 和 Microsoft Edge 编写自动测试，请安装适用于 Microsoft Edge 的[Selenium 工具](https://github.com/microsoft/edge-selenium-tools)程序包以使用更新后的驱动程序。  工具 `EdgeDriver` `EdgeDriverService` 中包含的 和 类与 Selenium 4 中的内置等效项完全兼容。

如果使用的是 Selenium 3，请使用以下步骤将适用于 Microsoft Edge[和 Selenium 3](https://www.selenium.dev)的[Selenium](https://github.com/microsoft/edge-selenium-tools)工具添加到项目中。

#### [<a name="c"></a>C#](#tab/c-sharp/)

<a id="selenium-tools-install"></a>

将[Microsoft.Edge.SeleniumTools](https://www.nuget.org/packages/Microsoft.Edge.SeleniumTools)和[Selenium.WebDriver](https://www.nuget.org/packages/Selenium.WebDriver/3.141.0)包添加到使用 CLI 或 Visual Studio [NuGet 的](https://www.nuget.org/packages/NuGet.CommandLine/).NET[项目](https://visualstudio.microsoft.com/)。

#### [<a name="python"></a>Python](#tab/python/)

<a id="selenium-tools-install"></a>

使用 [管道](https://pypi.org/project/pip/) 安装 [msedge-selenium-tools](https://pypi.org/project/msedge-selenium-tools/) 和 [selenium](https://pypi.org/project/selenium/) 程序包。

```python
pip install msedge-selenium-tools selenium==3.141
```

#### [<a name="java"></a>Java	](#tab/java/)

<a id="selenium-tools-install"></a>

如果您的Java项目使用 Maven，将以下依赖项复制并粘贴到文件以 `pom.xml` 添加 [msedge-selenium-tools-java](https://search.maven.org/artifact/com.microsoft.edge/msedge-selenium-tools-java/3.141.0/jar)。

```xml
<dependency>
    <groupId>com.microsoft.edge</groupId>
    <artifactId>msedge-selenium-tools-java</artifactId>
    <version>[3.141.0,)</version>
</dependency>
```

The Java package is also available to download directly on the [Selenium Tools for Microsoft Edge Releases page](https://github.com/microsoft/edge-selenium-tools/releases).

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

<a id="selenium-tools-install"></a>

使用 [npm](https://www.npmjs.com/) 安装 [edge-selenium-tools](https://www.npmjs.com/package/@microsoft/edge-selenium-tools) 和 [selenium-webdriver](https://www.npmjs.com/package/selenium-webdriver) 程序包。

```javascript
npm install @microsoft/edge-selenium-tools selenium-webdriver
```

* * *


<!-- ====================================================================== -->
## <a name="automate-microsoft-edge-with-webdriver"></a>使用 WebDriver Microsoft Edge自动执行部署

若要使用 WebDriver 自动化浏览器，必须先使用首选的 WebDriver 测试框架启动 WebDriver 会话。  会话是使用 WebDriver 命令控制的浏览器的单个运行实例。  启动 WebDriver 会话以启动新的浏览器实例。  在关闭 WebDriver 会话之前，启动的浏览器实例保持打开状态。

以下内容将引导你使用 Selenium 启动 WebDriver 会话，Microsoft Edge。  可以使用 Selenium 3 或 4 运行这些示例。  若要将 WebDriver 与 Selenium 3 一Microsoft Edge，必须安装[Selenium](https://github.com/microsoft/edge-selenium-tools) Tools for Microsoft Edge程序包。

> [!NOTE]
> 本文提供了有关使用 Selenium 框架的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用另一个框架完成相同的任务，请参阅文档中的选择框架。

### <a name="automate-microsoft-edge"></a>自动Microsoft Edge

Selenium 使用 `EdgeDriver` 类管理Microsoft Edge会话。  若要启动会话并自动Microsoft Edge，请创建一个新对象，并传递一 `EdgeDriver` `EdgeOptions` 个属性设置为 `UseChromium` 的对象 `true` 。

#### [<a name="c"></a>C#](#tab/c-sharp/)

<a id="drive-microsoft-edge-chromium-code"></a>

```csharp
var options = new EdgeOptions();
options.UseChromium = true;

var driver = new EdgeDriver(options);
```

#### [<a name="python"></a>Python](#tab/python/)

<a id="drive-microsoft-edge-chromium-code"></a>

```python
options = EdgeOptions()
options.use_chromium = True

driver = Edge(options = options)
```

#### [<a name="java"></a>Java	](#tab/java/)

<a id="drive-microsoft-edge-chromium-code"></a>

该类 `EdgeDriver` 仅支持 Microsoft Edge (Chromium) ，并且不支持 Microsoft Edge (EdgeHTML) 。  对于基本用法，可以在不提供 `EdgeDriver` 的情况下创建 `EdgeOptions` 。

```java
EdgeDriver driver = new EdgeDriver();
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

<a id="drive-microsoft-edge-chromium-code"></a>

```javascript
let options = new edge.Options();
options.setEdgeChromium(true);

let driver = edge.Driver.createSession(options);
```

* * *

> [!NOTE]
> 如果你的 IT 管理员将[DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability)策略设置为 ，Microsoft Edge Driver 被阻止驱动 Microsoft Edge，因为驱动程序使用 `2` Microsoft Edge [DevTools](../devtools-guide-chromium/index.md)。 [](https://developer.microsoft.com/microsoft-edge/tools/webdriver)  确保[将 DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability)策略设置为 `0` 或 `1` 自动Microsoft Edge。

### <a name="choose-specific-browser-binaries-chromium-only"></a>选择"特定浏览器二进制文件 (Chromium仅) 

可以使用特定的二进制文件启动 WebDriver Microsoft Edge会话。  例如，可以使用预览频道（如[Microsoft Edge）](https://www.microsoftedgeinsider.com/download)运行Microsoft Edge Beta。

#### [<a name="c"></a>C#](#tab/c-sharp/)

<a id="choose-specific-browser-binaries-chrome-only-code"></a>

```csharp
var options = new EdgeOptions();
options.UseChromium = true;
options.BinaryLocation = @"C:\Program Files (x86)\Microsoft\Edge Beta\Application\msedge.exe";

var driver = new EdgeDriver(options);
```

#### [<a name="python"></a>Python](#tab/python/)

<a id="choose-specific-browser-binaries-chrome-only-code"></a>

```python
options = EdgeOptions()
options.use_chromium = True
options.binary_location = r"C:\Program Files (x86)\Microsoft\Edge Beta\Application\msedge.exe"

driver = Edge(options = options)
```

#### [<a name="java"></a>Java	](#tab/java/)

<a id="choose-specific-browser-binaries-chrome-only-code"></a>

```java
EdgeOptions options = new EdgeOptions();
options.setBinary("C:\\Program Files (x86)\\Microsoft\\Edge Beta\\Application\\msedge.exe");

EdgeDriver driver = new EdgeDriver(options);
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

<a id="choose-specific-browser-binaries-chrome-only-code"></a>

```javascript
let options = new edge.Options();
options.setEdgeChromium(true);
options.setBinaryPath("C:\\Program Files (x86)\\Microsoft\\Edge Beta\\Application\\msedge.exe");

let driver = edge.Driver.createSession(options);
```

* * *

### <a name="customize-the-microsoft-edge-driver-service"></a>自定义 Microsoft Edge 驱动程序服务

#### [<a name="c"></a>C#](#tab/c-sharp/)

<a id="customize-microsoft-edge-driver-services-code"></a>

使用 类创建类实例时，它会为旧版 EdgeHTML 或 `EdgeOptions` `EdgeDriver` `EdgeDriverService` Microsoft Edge (Chromium) 。

如果要创建 ，请使用 `EdgeDriverService` 方法创建 `CreateChromiumService()` 一个配置为 Microsoft Edge。  `CreateChromiumService()`当您需要添加自定义项时，该方法非常有用。  例如，以下代码开始详细日志输出：

```csharp
using (var service = EdgeDriverService.CreateChromiumService())
{
    service.UseVerboseLogging = true;

    var driver = new EdgeDriver(service);
}
```

> [!NOTE]
>在传递给实例时，不需要提供 `EdgeOptions` `EdgeDriverService` `EdgeDriver` 对象。  该类 `EdgeDriver` 根据你提供的服务使用旧版 EdgeHTML 或 Microsoft Edge (Chromium) 的默认选项。
> 但是，如果要同时提供 和 类，请确保为同一版本的 `EdgeDriverService` `EdgeOptions` Microsoft Edge。  例如，假设你使用默认的旧版 EdgeHTML 类 `EdgeDriverService` ，Microsoft Edge (Chromium) 类中的属性 `EdgeOptions` 。  `EdgeDriver`该类将引发错误，以阻止使用不同版本的 Microsoft Edge。

#### [<a name="python"></a>Python](#tab/python/)

<a id="customize-microsoft-edge-driver-services-code"></a>

使用 Python 时， `Edge` 对象将创建和管理 `EdgeService` 。  若要配置 `EdgeService` ，请向 对象传递 `Edge` 额外参数，如以下代码所示：

```python
service_args = ['--verbose']
driver = Edge(service_args = service_args)
```

#### [<a name="java"></a>Java	](#tab/java/)

<a id="customize-microsoft-edge-driver-services-code"></a>

使用 `createDefaultService()` 方法可创建 `EdgeDriverService` 一个配置为Microsoft Edge。  使用 Java 系统属性自定义 Java 中的驱动程序服务。  例如，以下代码使用 `"webdriver.edge.verboseLogging"` 属性打开详细日志输出：

```java
System.setProperty("webdriver.edge.verboseLogging", "true");
EdgeDriverService service = EdgeDriverService.createDefaultService();
EdgeOptions options = new EdgeOptions();
EdgeDriver driver = new EdgeDriver(service, options);
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

<a id="customize-microsoft-edge-driver-services-code"></a>

使用 JavaScript 时，请使用 类 `Service` 创建和 `ServiceBuilder` 配置 。  （可选）可以将对象传递给对象，该对象 (`Service` `Driver` 并) 服务。  若要配置 `Service` ，请运行 类中的另一 `ServiceBuilder` 个方法，然后再使用 `build()` 方法。  然后将 作为 `service` 参数在 方法 `Driver.createSession()` 中传递：

```javascript
let service = new edge.ServiceBuilder().enableVerboseLogging().build();
let driver = edge.Driver.createSession(options, service);
```

* * *

### <a name="use-chromium-specific-options"></a>使用Chromium-Specific选项

如果将 属性设置为 ，可以使用 类访问Chromium自动化其他浏览器时所使用的特定属性 `UseChromium` `true` `EdgeOptions` 和方法Chromium方法。 [](capabilities-edge-options.md)

#### [<a name="c"></a>C#](#tab/c-sharp/)

<a id="use-chromium-specific-options-code"></a>

```csharp
var options = new EdgeOptions();
options.UseChromium = true;
options.AddArgument("headless");
options.AddArgument("disable-gpu");
```

#### [<a name="python"></a>Python](#tab/python/)

<a id="use-chromium-specific-options-code"></a>

```python
options = EdgeOptions()
options.use_chromium = True
options.add_argument("headless")
options.add_argument("disable-gpu")
```

#### [<a name="java"></a>Java	](#tab/java/)

<a id="use-chromium-specific-options-code"></a>

```java
EdgeOptions options = new EdgeOptions();
options.addArguments("headless");
options.addArguments("disable-gpu");
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

<a id="use-chromium-specific-options-code"></a>

```javascript
let options = new edge.Options();
options.setEdgeChromium(true);
options.addArguments("headless");
options.addArguments("disable-gpu");
```

* * *

> [!NOTE]
> 如果 `UseChromium` 属性设置为 `true` ，则不能对 EdgeHTML Microsoft Edge (属性) 。


<!-- ====================================================================== -->
## <a name="other-webdriver-installation-options"></a>其他 WebDriver 安装选项

### <a name="docker"></a>Docker

如果你使用[Docker，](https://hub.docker.com)请运行以下命令来下载预配置映像，Microsoft Edge Microsoft Edge[驱动程序](https://developer.microsoft.com/microsoft-edge/tools/webdriver)预安装。

```console
docker run -d -p 9515:9515 mcr.microsoft.com/msedge/msedgedriver
```

有关详细信息，请参阅 Docker Hub 上的 [msedgedriver 容器](https://hub.docker.com/_/microsoft-msedge-msedgedriver?tab=description)。


<!-- ====================================================================== -->
## <a name="testing-internet-explorer"></a>测试Internet Explorer

若要测试需要更新Internet Explorer，Internet Explorer [驱动程序](https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver) 和Internet Explorer。  Internet Explorer驱动程序由 Selenium 项目维护。  即使Microsoft Edge支持 IE 模式，你Microsoft Edge驱动程序Microsoft Edge IE 模式下测试站点。


<!-- ====================================================================== -->
## <a name="application-guard"></a>应用程序防护

使用应用程序防护Microsoft Defender 应用程序防护 (的受) 可以使用驱动程序自动Microsoft Edge站点。

使用应用程序防护的不受信任的站点无法使用应用程序驱动程序自动Microsoft Edge操作。  应用程序防护在容器中启动不受信任的站点，并且此容器不会公开驱动程序与Microsoft Edge通信所需的远程调试端口。

企业管理员定义什么是受信任的站点，包括云资源和内部网络。  不在受信任站点列表中的网站被视为不受信任的网站。  Microsoft Edge驱动程序可以自动执行 InPrivate 窗口和受信任站点列表中的站点。

有关应用程序防护详细信息，请参阅：

*  [Microsoft Edge支持Microsoft Defender 应用程序防护。](/deployedge/microsoft-edge-security-windows-defender-application-guard)
*  [Microsoft Defender 应用程序防护概述](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)。


<!-- ====================================================================== -->
## <a name="opt-out-of-diagnostic-data-collection"></a>选择退出诊断数据收集

默认情况下，Microsoft Edge 驱动程序会向 Microsoft 发送诊断数据，如[新建会话 WebDriver 命令](https://www.w3.org/TR/webdriver2/#new-session)的状态。  若要关闭 Microsoft Edge 驱动程序的诊断数据收集，请将 `MSEDGEDRIVER_TELEMETRY_OPTOUT` 环境变量设置为 `1`。  有关驱动程序收集的数据Microsoft Edge，请参阅隐私Microsoft Edge[白皮书](/microsoft-edge/privacy-whitepaper#microsoft-edge-driver)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Selenium 文档](https://www.selenium.dev/documentation) - 有关 Selenium 上下文中的 WebDriver 以及如何使用 Selenium 编写自动 WebDriver 测试的信息。
*  联系[Microsoft Edge DevTools](../devtools-guide-chromium/contact.md)团队，发送有关使用 WebDriver、WebDriver 测试框架 (如 Selenium) 和 Microsoft Edge。
