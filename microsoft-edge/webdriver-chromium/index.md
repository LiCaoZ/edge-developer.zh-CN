---
title: 使用 WebDriver 自动执行 Microsoft Edge
description: 如何在 Microsoft Edge 中测试网站或应用，以及如何使用 WebDriver 自动执行浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 01/20/2022
ms.openlocfilehash: 0ff2e099c1fbb22b3fe209cd77dc7d6364719b99
ms.sourcegitcommit: 722cef4ac26d133d73474bae4ad57c51628b30db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2022
ms.locfileid: "12477707"
---
# <a name="use-webdriver-to-automate-microsoft-edge"></a>使用 WebDriver 自动执行 Microsoft Edge

WebDriver 允许你通过模拟用户交互来自动执行 Microsoft Edge。  使用 WebDriver 的测试相比于在浏览器中运行的 JavaScript 单元测试有一些优势：

*   WebDriver 可以使用在浏览器中运行的 JavaScript 不可使用的功能和信息。

*   WebDriver 比 JavaScript 单元测试更准确地模拟用户事件或 OS 级事件。

*   WebDriver 管理单个测试会话中的多个窗口、选项卡、网页。

*   WebDriver 在特定计算机上运行多个 Microsoft Edge 会话。


<!-- ====================================================================== -->
## <a name="relationship-between-webdriver-and-other-software"></a>WebDriver 和其他软件之间的关系

若要使用 WebDriver 自动化 Microsoft Edge 以模拟用户交互，需要三个组件：

*  Microsoft Edge 的详细信息。
*  Microsoft Edge WebDriver。
*  WebDriver 测试框架。

这些组件之间的功能关系如下所示：

| 技术 | 角色 |
|---|---|
| WebDriver | 平台和非特定语言网络协议的 W3C 标准。  此协议允许进程外程序远程指示 Web 浏览器的行为。 |
| Microsoft Edge WebDriver | Microsoft 专门用于 Microsoft Edge 的 WebDriver 协议的实现。  测试作者编写使用 WebDriver 命令Microsoft Edge WebDriver 接收的测试。  然后，Edge WebDriver 负责将该命令传达给浏览器。 |
| WebDriver 测试框架 | 测试作者使用测试框架编写端到端测试并自动执行浏览器。  提供特定于语言的接口，将代码转换为发送到 Edge WebDriver 的命令。  WebDriver 测试框架适用于所有主要平台和语言。  其中一个框架是 Selenium。 |
| Internet Explorer 驱动程序 | 专门用于 Internet Explorer 的 WebDriver 协议的开源实现。  若要针对 Internet Explorer 模式运行旧的端到端测试，建议使用 Internet Explorer 驱动程序。 |
| Microsoft WebDriver (旧版)  | 上一个特定于浏览器的 Microsoft Edge (EdgeHTML) 驱动程序，也称为Microsoft Edge 旧版。 |

以下部分介绍如何开始使用 WebDriver for Microsoft Edge。


<!-- ====================================================================== -->
## <a name="download-microsoft-edge-webdriver"></a>下载 Microsoft Edge WebDriver

若要开始编写自动测试，请确保安装的 Edge WebDriver 版本与浏览器版本匹配，如下所示：

1.  转到 `edge://settings/help` 并记下你的 Microsoft Edge 版本。

    :::image type="content" source="./media/microsoft-edge-version.msft.png" alt-text="2021 年 4 月 15 日 Microsoft Edge 的内部版本号。" lightbox="./media/microsoft-edge-version.msft.png":::

1.  转到 [Microsoft Edge WebDriver](https://developer.microsoft.com/microsoft-edge/tools/webdriver)。

1.  在**获取页面的最新版本**部分，在频道中选择与 Microsoft Edge 版本号匹配的平台。

    :::image type="content" source="./media/microsoft-edge-driver-install.msft.png" alt-text="Microsoft Edge WebDriver 网页的“获取最新版本”部分。" lightbox="./media/microsoft-edge-driver-install.msft.png":::

1.  下载完成后，将 `msedgedriver` 可执行文件提取到首选位置。 将可执行文件所在的文件夹添加到你的 `PATH` 环境变量。


<!-- ====================================================================== -->
## <a name="choose-a-webdriver-testing-framework"></a>选择 WebDriver 测试框架

下载 Edge WebDriver 后，必须下载的最后一个组件是 WebDriver 测试框架。  测试作者使用 WebDriver 测试框架编写端到端测试并自动执行浏览器。  WebDriver 测试框架提供特定于语言的接口，用于将代码转换为 Edge WebDriver 在 Microsoft Edge 中运行的命令。  WebDriver 测试框架适用于所有主要平台和语言，例如 Python、Java、C#、Ruby、JavaScript。

本文提供了有关使用 Selenium 框架的说明，但你可以使用任何支持 WebDriver 的库、框架、编程语言。  若要使用除 Selenium 以外的 WebDriver 测试框架完成相同的任务，请参阅官方文档了解所选框架。

### <a name="using-selenium-4"></a>使用 Selenium 4

Selenium WebDriver 是一个开放源代码测试框架，可在任何平台上使用，并为 Java、Python、C#、Ruby、JavaScript 提供语言绑定。

Microsoft Edge 团队建议使用 [Selenium 4](https://www.nuget.org/packages/Selenium.WebDriver)，因为 Selenium 4 内置支持 Microsoft Edge (Chromium)。  若要安装 Selenium 4，请参阅[安装 Selenium 库](https://www.selenium.dev/documentation/en/selenium_installation/installing_selenium_libraries)。

### <a name="upgrading-from-selenium-3"></a>从 Selenium 3 升级

Microsoft Edge 团队建议将现有的 Selenium 3 测试升级到 Selenium 4，因为 Selenium 项目不再维护 Selenium 3。  若要了解有关升级到 Selenium 4 的详细信息，请参阅[升级到 Selenium 4](https://www.selenium.dev/documentation/webdriver/getting_started/upgrade_to_selenium_4/)。

如果使用 [Selenium Tools for Microsoft Edge](https://github.com/microsoft/edge-selenium-tools) 将Microsoft Edge (Chromium) 支持添加到 Selenium 3 浏览器测试，请按如下所示更新测试：

1. 从项目中删除[用于 Microsoft Edge](https://github.com/microsoft/edge-selenium-tools) 的 Selenium 工具。  无需将 Selenium Tools 用于 Selenium 4 的 Microsoft Edge，因为 Selenium 4 已内置支持 Microsoft Edge (Chromium)。

1. 更新测试以改用内置的 `EdgeDriver` 和 Selenium 4 提供的相关类。

1. 删除 `EdgeOptions.UseChromium` 属性的所有用法。  Selenium 4 中不再存在此属性，因为 Selenium 4 仅支持 Microsoft Edge (Chromium)。

<!-- apparently decorative only; not a tab-end indicator: -->

* * *


<!-- ====================================================================== -->
## <a name="automate-microsoft-edge-with-webdriver"></a>使用 WebDriver 自动化 Microsoft Edge

若要使用 WebDriver 自动执行浏览器，必须首先使用 WebDriver 测试框架启动 WebDriver 会话。  WebDriver _会话_是通过 WebDriver 命令控制的浏览器的单个运行实例。

启动 WebDriver 会话以启动新的浏览器实例。  启动的浏览器实例将保持打开状态，直到关闭 WebDriver 会话。

以下部分逐步讲解如何使用 Selenium 4 通过 Microsoft Edge 启动 WebDriver 会话。

> [!NOTE]
> 本文提供了有关使用 Selenium 框架的说明，但你可以使用任何支持 WebDriver 的库、框架、编程语言。  若要使用另一个框架完成相同的任务，请查阅所选框架的文档。

### <a name="automate-microsoft-edge"></a>自动化 Microsoft Edge

Selenium 使用 `EdgeDriver` 类来管理 Microsoft Edge 会话。  以下代码：
1. 启动 Microsoft Edge 会话。
1. 指示 Microsoft Edge 转到必应。
1. 搜索“WebDriver”。
1. 休眠几秒钟，以便查看结果。

若要开始使用 WebDriver 自动化 Microsoft Edge，请复制并粘贴首选语言的代码片段：

#### [<a name="c"></a>C#](#tab/c-sharp/)

```csharp
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using System.Threading;

namespace EdgeDriverSample
{
    class Program
    {
        static void Main(string[] args)
        {
            var driver = new EdgeDriver();
            try
            {
                driver.Url = "https://bing.com";

                var element = driver.FindElement(By.Id("sb_form_q"));
                element.SendKeys("WebDriver");
                element.Submit();

                Thread.Sleep(5000);
            }
            finally
            {
                driver.Quit();
            }
        }
    }
}
```

#### [<a name="python"></a>Python](#tab/python/)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Edge()

driver.get('https://bing.com')

element = driver.find_element(By.ID, 'sb_form_q')
element.send_keys('WebDriver')
element.submit()

time.sleep(5)
driver.quit()
```

#### [<a name="java"></a>Java	](#tab/java/)

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;

public class EdgeDriverSample {
    public static void main(String[] args) throws Exception {
        EdgeDriver driver = new EdgeDriver();
        try {
            driver.navigate().to("https://bing.com");

            WebElement element = driver.findElement(By.id("sb_form_q"));
            element.sendKeys("WebDriver");
            element.submit();

            Thread.sleep(5000);
        } finally {
            driver.quit();
        }
    }
}
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

```javascript
const { Builder, By } = require('selenium-webdriver');

(async () => {
    const driver = await new Builder().forBrowser('MicrosoftEdge').build();
    try {
        await driver.get('https://bing.com');

        const element = await driver.findElement(By.id('sb_form_q'));
        await element.sendKeys('WebDriver');
        await element.submit();

        await driver.sleep(5000);
    } finally {
        await driver.quit();
    }
})();
```

* * *

### <a name="manage-and-configure-the-edge-webdriver-service"></a>管理和配置 Edge WebDriver 服务

创建新`EdgeDriver`对象以启动Microsoft Edge会话时，Selenium 会启动该对象与之通信的新 Edge WebDriver 进程`EdgeDriver`。  调用对象`Quit`的方法时，`EdgeDriver`Edge WebDriver 进程将关闭。  如果有多个测试，让每个 `EdgeDriver` 对象管理自己的驱动程序进程可能效率低下，因为每个测试都必须等待新的驱动程序进程启动。  相反，可以创建单个 Edge WebDriver 进程，然后将其重复用于多个测试。

Selenium 使用该 `EdgeDriverService` 类来管理 Edge WebDriver 进程。  可以在运行测试之前创建 `EdgeDriverService` 一次， 然后，在创建新的 `EdgeDriver` 对象时，将此 `EdgeDriverService` 对象传递给 `EdgeDriver` 构造函数。  将 `EdgeDriverService` 传递到 `EdgeDriver` 构造函数时，`EdgeDriver` 对象将使用此 `EdgeDriverService`，而不是创建新类。

还可以使用 `EdgeDriverService` 它来配置 Edge WebDriver 进程的命令行选项，如下所示。

以下代码片段会创建新的 `EdgeDriverService` 并启用详细日志输出：

#### [<a name="c"></a>C#](#tab/c-sharp/)

```csharp
var service = EdgeDriverService.CreateDefaultService();
service.UseVerboseLogging = true;

var driver = new EdgeDriver(service);
```

#### [<a name="python"></a>Python](#tab/python/)

```python
from selenium import webdriver
from selenium.webdriver.edge.service import Service

service = Service(verbose = True)

driver = webdriver.Edge(service = service)
```

#### [<a name="java"></a>Java	](#tab/java/)

```java
System.setProperty("webdriver.edge.verboseLogging", "true");
EdgeDriverService service = EdgeDriverService.createDefaultService();

EdgeDriver driver = new EdgeDriver(service);
```

#### [<a name="javascript"></a>JavaScript](#tab/javascript/)

```javascript
const edge = require('selenium-webdriver/edge');

const service = new edge.ServiceBuilder().enableVerboseLogging().build();

const options = new edge.Options();
const driver = edge.Driver.createSession(options, service);
```

* * *

### <a name="configure-microsoft-edge-options"></a>配置 Microsoft Edge 选项

可以将 `EdgeOptions` 对象传递给 `EdgeDriver` 构造函数，以便为 Microsoft Edge 浏览器进程配置额外的选项。  以下部分演示如何将 `EdgeOptions` 用于某些常见方案。  有关支持的选项的完整列表，请参阅[功能和 EdgeOptions](capabilities-edge-options.md)。

#### <a name="choose-specific-browser-binaries"></a>选择特定浏览器二进制文件

可以使用特定 Microsoft Edge 二进制文件启动 WebDriver 会话。  例如，可以使用 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download)（如Microsoft Edge Beta、开发人员或 Canary）运行测试。

##### [<a name="c"></a>C#](#tab/c-sharp/)

```csharp
var options = new EdgeOptions();
options.BinaryLocation = @"C:\Program Files (x86)\Microsoft\Edge Beta\Application\msedge.exe";

var driver = new EdgeDriver(options);
```

##### [<a name="python"></a>Python](#tab/python/)

```python
from selenium import webdriver
from selenium.webdriver.edge.options import Options

options = Options()
options.binary_location = r"C:\Program Files (x86)\Microsoft\Edge Beta\Application\msedge.exe"

driver = webdriver.Edge(options = options)
```

##### [<a name="java"></a>Java	](#tab/java/)

```java
EdgeOptions options = new EdgeOptions();
options.setBinary("C:\\Program Files (x86)\\Microsoft\\Edge Beta\\Application\\msedge.exe");

EdgeDriver driver = new EdgeDriver(options);
```

##### [<a name="javascript"></a>JavaScript](#tab/javascript/)

```javascript
const edge = require('selenium-webdriver/edge');

let options = new edge.Options();
options.setBinaryPath("C:\\Program Files (x86)\\Microsoft\\Edge Beta\\Application\\msedge.exe");

let driver = edge.Driver.createSession(options);
```

* * *

#### <a name="pass-extra-command-line-arguments"></a>传递额外的命令行参数

可以使用 `EdgeOptions` 配置将在创建会话时传递给 Microsoft Edge 浏览器进程的命令行参数。  例如，可以将浏览器配置为在无外设模式下运行。

##### [<a name="c"></a>C#](#tab/c-sharp/)

```csharp
var options = new EdgeOptions();
options.AddArgument("headless");

var driver = new EdgeDriver(options);
```

##### [<a name="python"></a>Python](#tab/python/)

```python
from selenium import webdriver
from selenium.webdriver.edge.options import Options

options = Options()
options.add_argument("headless")

driver = webdriver.Edge(options = options)
```

##### [<a name="java"></a>Java	](#tab/java/)

```java
EdgeOptions options = new EdgeOptions();
options.addArguments("headless");

EdgeDriver driver = new EdgeDriver(options);
```

##### [<a name="javascript"></a>JavaScript](#tab/javascript/)

```javascript
const edge = require('selenium-webdriver/edge');

let options = new edge.Options();
options.addArguments("headless");

let driver = edge.Driver.createSession(options);
```

* * *


<!-- ====================================================================== -->
## <a name="other-webdriver-installation-options"></a>其他 WebDriver 安装选项

### <a name="docker"></a>Docker

如果使用 [Docker](https://hub.docker.com)，请运行以下命令下载预配置的图像，该映像已预安装Microsoft Edge和 [Edge WebDriver](https://developer.microsoft.com/microsoft-edge/tools/webdriver)。

```console
docker run -d -p 9515:9515 mcr.microsoft.com/msedge/msedgedriver
```

有关详细信息，请参阅 [Docker Hub 上的 msedgedriver 容器](https://hub.docker.com/_/microsoft-msedge-msedgedriver?tab=description)。


<!-- ====================================================================== -->
## <a name="application-guard"></a>应用程序防护

使用Microsoft Defender 应用程序防护的受信任站点可以使用 Edge WebDriver 自动化。  简而言之，Microsoft Defender 应用程序防护也称为_应用程序防护_。

使用 Application Guard 的不受信任的站点不能使用 Edge WebDriver 进行自动化或操作。  Application Guard 在容器中启动不受信任的站点，并且此容器不会公开 Edge WebDriver 与站点通信所需的远程调试端口。

你的企业管理员定义什么是受信任的站点，包括云资源和内部网络。  不在受信任站点列表中的网站被视为_不受信任_。  Edge WebDriver 可以自动执行 InPrivate 窗口和受信任网站列表中的站点。

有关应用程序防护的详细信息，请参阅：

*  [Microsoft Edge 对 Microsoft Defender 应用程序防护的支持](/deployedge/microsoft-edge-security-windows-defender-application-guard)。
*  [Microsoft Defender 应用程序防护概述](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)。


<!-- ====================================================================== -->
## <a name="opt-out-of-diagnostic-data-collection"></a>选择退出诊断数据收集

默认情况下，Edge WebDriver 会将诊断数据（例如 [“新建会话 WebDriver”命令](https://www.w3.org/TR/webdriver2/#new-session) 的状态）发送到 Microsoft。  若要关闭 Edge WebDriver 的诊断数据收集，请将 `MSEDGEDRIVER_TELEMETRY_OPTOUT` 环境变量设置为 `1`。  有关 Edge WebDriver 收集的数据的详细信息，请参阅[Microsoft Edge隐私白皮书](/microsoft-edge/privacy-whitepaper#microsoft-edge-webdriver)。


<!-- ====================================================================== -->
## <a name="legacy-microsoft-webdriver-for-edgehtml"></a>旧版 Microsoft WebDriver for EdgeHTML

Microsoft WebDriver 是基于 EdgeHTML 的旧版 WebDriver 实现Microsoft Edge。  Microsoft WebDriver 作为可选Windows组件分发，因为旧版 Microsoft Edge (EdgeHTML) 已使用 OS 进行更新。  Microsoft WebDriver 与基于Chromium的最新版本的Microsoft Edge不兼容。  Microsoft WebDriver 仍适用于为 UWP 应用编写基于 WebDriver 的测试的开发人员，因为这些测试依赖于 EdgeHTML，但不再建议使用 Microsoft WebDriver。

请参阅 [WebDriver (EdgeHTML) ](/archive/microsoft-edge/legacy/developer/webdriver/)。


<!-- ====================================================================== -->
## <a name="troubleshooting"></a>疑难解答

以下是使用 WebDriver 自动执行 Microsoft Edge 时的疑难解答注意事项。

### <a name="developer-tools-availability-policy"></a>开发人员工具可用性策略

如果 IT 管理员已将 [DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability) 策略设置为`2`“[Edge WebDriver](https://developer.microsoft.com/microsoft-edge/tools/webdriver)”，则会阻止其Microsoft Edge，因为驱动程序使用 [Microsoft Edge DevTools](../devtools-guide-chromium/overview.md)。  若要自动执行 Microsoft Edge，请确保将 [DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability) 策略设置为 `0` 或 `1`。

### <a name="upgrading-from-selenium-3-to-selenium-4"></a>从 Selenium 3 升级到 Selenium 4

如果使用 Selenium 4，则无需使用用于 Microsoft Edge 的 Selenium 工具。  用于 Microsoft Edge 的 Selenium 工具仅适用于 Selenium 3。  如果尝试将 Selenium 4 与 Selenium Tools for Microsoft Edge 配合使用，并尝试创建新的 `EdgeDriver` 实例，则会收到以下错误：`System.MissingMethodException: 'Method not found: 'OpenQA.Selenium.Remote.DesiredCapabilities OpenQA.Selenium.DriverOptions.GenerateDesiredCapabilities(Boolean)'`。

如果使用 Selenium 4 并收到此错误，请从项目中删除 `Microsoft.Edge.SeleniumTools`， 并确保使用 `EdgeOptions` 命名空间中的官方 `EdgeDriver` 和 `OpenQA.Selenium.Edge` 类。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Selenium 文档](https://www.selenium.dev/documentation) - 有关 Selenium 上下文中 WebDriver 的信息，以及如何使用 Selenium 编写自动 WebDriver 测试。
*  [请联系 Microsoft Edge WebDriver 团队](contact.md)，发送有关使用 WebDriver、WebDriver 测试框架（如 Selenium）和 Microsoft Edge 的反馈。