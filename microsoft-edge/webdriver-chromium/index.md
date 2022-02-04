---
title: 使用 WebDriver 自动Microsoft Edge
description: 如何在 webDriver 中测试网站或Microsoft Edge，以及如何使用 WebDriver 自动执行浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 01/20/2022
---
# <a name="use-webdriver-to-automate-microsoft-edge"></a>使用 WebDriver 自动Microsoft Edge

通过 WebDriver，你可以Microsoft Edge用户交互来自动执行登录。  WebDriver 测试和模拟与 JavaScript 单元测试在以下方面有所不同：

*   WebDriver 访问在浏览器中运行的 JavaScript 不可用的功能和信息。

*   WebDriver 比 JavaScript 单元测试更准确地模拟用户事件或操作系统级事件。

*   WebDriver 在单个测试会话中管理多个窗口、选项卡和网页。

*   WebDriver 可运行特定Microsoft Edge多个会话。


<!-- ====================================================================== -->
## <a name="relationship-between-webdriver-and-other-software"></a>WebDriver 和其他软件之间的关系

若要自动Microsoft Edge WebDriver 自动执行用户交互，您需要三个组件：

*  Microsoft Edge 的详细信息。
*  Microsoft Edge驱动程序。
*  WebDriver 测试框架。

这些组件之间的功能关系如下所示：

| 技术 | 角色 |
|---|---|
| WebDriver | 适用于平台和中性语言的线路协议的 W3C 标准。  此协议允许进程外程序远程指示 Web 浏览器的行为。 |
| Microsoft Edge 驱动程序 | Microsoft 专为用户实现 WebDriver 协议Microsoft Edge。  测试作者编写使用驱动程序收到的 WebDriver Microsoft Edge的测试。  Microsoft Edge驱动程序随后负责将该命令与浏览器通信。 |
| WebDriver 测试框架 | 测试作者使用测试框架编写端到端测试并自动化浏览器。  提供特定语言的接口，该接口将代码转换为发送到驱动程序Microsoft Edge命令。  WebDriver 测试框架适用于所有主要平台和语言。  这样的框架之一是 Selenium。 |
| Internet Explorer驱动程序 | 专用于 webDriver 协议的开放源代码Internet Explorer。  若要为测试模式运行传统的端到端测试Internet Explorer，我们建议使用 Internet Explorer 驱动程序。 |

以下各节介绍如何开始使用 WebDriver for Microsoft Edge。


<!-- ====================================================================== -->
## <a name="download-microsoft-edge-driver"></a>下载 Microsoft Edge 驱动程序

若要开始编写自动测试，请确保Microsoft Edge驱动程序版本与浏览器版本匹配，如下所示：

1.  转到 并`edge://settings/help`记下你的Microsoft Edge。

    :::image type="content" source="./media/microsoft-edge-version.msft.png" alt-text="2021 Microsoft Edge 2021 年 4 月 15 日。" lightbox="./media/microsoft-edge-version.msft.png":::

1.  转到["Microsoft Edge驱动程序"](https://developer.microsoft.com/microsoft-edge/tools/webdriver)。

1.  在**页面的"获取最新版本**"部分，在频道中选择一个与你的版本编号相匹配的平台Microsoft Edge。

    :::image type="content" source="./media/microsoft-edge-driver-install.msft.png" alt-text="The 'Get the latest version' section of the Microsoft Edge Driver webpage." lightbox="./media/microsoft-edge-driver-install.msft.png":::

1.  下载完成后，将可执行 `msedgedriver` 文件提取到首选位置。 将可执行文件所在的文件夹添加到环境 `PATH` 变量中。


<!-- ====================================================================== -->
## <a name="choose-a-webdriver-testing-framework"></a>选择 WebDriver 测试框架

下载驱动程序Microsoft Edge，必须下载的最后一个组件是 WebDriver 测试框架。  测试作者使用 WebDriver 测试框架编写端到端测试并自动化浏览器。  WebDriver 测试框架提供特定语言的接口，将代码转换为命令，Microsoft Edge驱动程序在 Microsoft Edge 中运行。  WebDriver 测试框架适用于所有主要平台和语言，如 Python、Java、C#、Ruby 和 JavaScript。

本文提供了有关使用 Selenium 框架的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用除 Selenium 外的其他 WebDriver 测试框架完成相同的任务，请参考您所选择的框架的官方文档。

### <a name="using-selenium-4"></a>使用 Selenium 4

Selenium WebDriver 是一个可在任何平台上使用的开源测试框架，为 Java、Python、C#、Ruby 和 JavaScript 提供语言绑定。

该Microsoft Edge建议使用 [Selenium 4](https://www.nuget.org/packages/Selenium.WebDriver)，因为 Selenium 4 内置了对 Microsoft Edge (Chromium) 的支持。  若要安装 Selenium 4，请参阅 [安装 Selenium 库](https://www.selenium.dev/documentation/en/selenium_installation/installing_selenium_libraries)。

### <a name="upgrading-from-selenium-3"></a>从 Selenium 3 升级

该Microsoft Edge团队建议将现有 Selenium 3 测试升级到 Selenium 4，因为 Selenium 项目不再维护 Selenium 3。  若要详细了解如何升级到 Selenium 4，请参阅 [升级到 Selenium 4](https://www.selenium.dev/documentation/webdriver/getting_started/upgrade_to_selenium_4/)。

如果你使用 [Selenium Tools for Microsoft Edge](https://github.com/microsoft/edge-selenium-tools)为 Selenium 3 Microsoft Edge (Chromium) 添加支持，请更新测试，如下所示：

1. 从[项目中删除适用于Microsoft Edge Selenium](https://github.com/microsoft/edge-selenium-tools) 工具。  无需将 Selenium Tools for Microsoft Edge Selenium 4，因为 Selenium 4 已经内置了对 Microsoft Edge (Chromium) 的支持。

1. 更新测试以改为使用 `EdgeDriver` Selenium 4 提供的内置和相关类。

1. 删除属性的所有 `EdgeOptions.UseChromium` 用法。  此属性在 Selenium 4 中不再存在，因为 Selenium 4 仅支持Microsoft Edge (Chromium) 。

<!-- apparently decorative only; not a tab-end indicator: -->

* * *


<!-- ====================================================================== -->
## <a name="automate-microsoft-edge-with-webdriver"></a>使用 WebDriver Microsoft Edge自动执行部署

若要使用 WebDriver 自动化浏览器，必须先使用 WebDriver 测试框架启动 WebDriver 会话。  WebDriver _会话_ 是通过 WebDriver 命令控制的单个正在运行的浏览器实例。

启动 WebDriver 会话以启动新的浏览器实例。  在关闭 WebDriver 会话之前，启动的浏览器实例保持打开状态。

下一节将指导你使用 Selenium 4 通过 Microsoft Edge 启动 WebDriver 会话。

> [!NOTE]
> 本文提供了有关使用 Selenium 框架的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用另一个框架完成相同的任务，请参阅文档中的选择框架。

### <a name="automate-microsoft-edge"></a>自动Microsoft Edge

Selenium 使用 `EdgeDriver` 类管理Microsoft Edge会话。  以下代码：
1. 启动Microsoft Edge会话。
1. 指示Microsoft Edge转到必应。
1. 搜索"WebDriver"。
1. 休眠几秒钟，以便你可以看到结果。

若要开始使用 WebDriver 自动Microsoft Edge代码段，请复制并粘贴首选语言的代码段：

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

### <a name="manage-and-configure-the-microsoft-edge-driver-service"></a>管理和配置 Microsoft Edge 驱动程序服务

当你创建新对象以`EdgeDriver`启动Microsoft Edge会话时，Selenium 会启动Microsoft Edge与`EdgeDriver`该对象通信的新驱动程序进程。  调用Microsoft Edge方法时，将`EdgeDriver`关闭驱动程序进程`Quit`。  如果有很多 `EdgeDriver` 测试，则让每个对象管理自己的驱动程序进程可能效率低下，因为每个测试必须等待新的驱动程序进程启动。  相反，你可以创建单个驱动程序Microsoft Edge，然后重复使用它进行多个测试。

Selenium 使用 `EdgeDriverService` 类管理Microsoft Edge驱动程序进程。  可以在运行测试`EdgeDriverService`之前创建`EdgeDriverService``EdgeDriver`一次，然后在创建新对象时将该对象传递给构造函数`EdgeDriver`。  将 传递到 `EdgeDriverService` 构造函数时 `EdgeDriver` ， `EdgeDriver` 对象将使用此 `EdgeDriverService`，而不是创建新的构造函数。

还可使用 为`EdgeDriverService`驱动程序进程配置命令行Microsoft Edge选项，如下所示。

以下代码段创建新的并 `EdgeDriverService` 启用详细日志输出：

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

### <a name="configure-microsoft-edge-options"></a>配置Microsoft Edge选项

可以将对象传递给`EdgeOptions`构造函数`EdgeDriver`，以配置用于浏览器Microsoft Edge选项。  下一节演示如何用于 `EdgeOptions` 一些常见方案。  有关受支持的选项的完整列表，请参阅 [功能和 EdgeOptions](capabilities-edge-options.md)。

#### <a name="choose-specific-browser-binaries"></a>选择特定浏览器二进制文件

可以使用特定的二进制文件启动 WebDriver Microsoft Edge会话。  例如，可以使用预览Microsoft Edge（如 Microsoft Edge Beta、[](https://www.microsoftedgeinsider.com/download)Dev 或 Canary）运行测试。

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

可以使用 配置`EdgeOptions`命令行参数，这些参数将在创建会话时Microsoft Edge浏览器进程。  例如，可以将浏览器配置为在无头模式下运行。

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

如果使用 [Docker，](https://hub.docker.com)请运行以下命令以下载预配置映像，该映像Microsoft Edge并Microsoft Edge[驱动程序](https://developer.microsoft.com/microsoft-edge/tools/webdriver)预安装。

```console
docker run -d -p 9515:9515 mcr.microsoft.com/msedge/msedgedriver
```

有关详细信息，请参阅 [Docker Hub 上的 msedgedriver 容器](https://hub.docker.com/_/microsoft-msedge-msedgedriver?tab=description)。


<!-- ====================================================================== -->
## <a name="application-guard"></a>应用程序防护

使用受信任站点Microsoft Defender 应用程序防护驱动程序自动Microsoft Edge驱动程序。  Microsoft Defender 应用程序防护也称为_应用程序_防护。

使用应用程序防护的不受信任的站点无法使用应用程序驱动程序自动Microsoft Edge操作。  应用程序防护在容器中启动不受信任的站点，并且此容器不会公开驱动程序与Microsoft Edge通信所需的远程调试端口。

企业管理员定义什么是受信任的站点，包括云资源和内部网络。  不在受信任站点列表中的网站被视为 _不受信任的网站_。  Microsoft Edge驱动程序可以自动执行 InPrivate 窗口和受信任站点列表中的站点。

有关应用程序防护详细信息，请参阅：

*  [Microsoft Edge支持Microsoft Defender 应用程序防护](/deployedge/microsoft-edge-security-windows-defender-application-guard)。
*  [Microsoft Defender 应用程序防护概述](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)。


<!-- ====================================================================== -->
## <a name="opt-out-of-diagnostic-data-collection"></a>选择退出诊断数据收集

默认情况下，Microsoft Edge 驱动程序会向 Microsoft 发送诊断数据，如[新建会话 WebDriver 命令](https://www.w3.org/TR/webdriver2/#new-session)的状态。  若要关闭驱动程序的诊断Microsoft Edge，将环境`MSEDGEDRIVER_TELEMETRY_OPTOUT`变量设置为 `1`。  有关驱动程序收集的数据Microsoft Edge，请参阅Microsoft Edge[隐私白皮书](/microsoft-edge/privacy-whitepaper#microsoft-edge-driver)。


<!-- ====================================================================== -->
## <a name="troubleshooting"></a>疑难解答

这些是使用 WebDriver 自动执行 Microsoft Edge。

### <a name="developer-tools-availability-policy"></a>开发人员工具可用性策略

如果你的 IT 管理员将 [DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability) `2`策略设置为 ，Microsoft Edge [驱动程序](https://developer.microsoft.com/microsoft-edge/tools/webdriver)被阻止驱动 Microsoft Edge，因为驱动程序使用 Microsoft Edge [DevTools](../devtools-guide-chromium/index.md)。  若要自动Microsoft Edge，请确保 [DeveloperToolsAvailability](/deployedge/microsoft-edge-policies#developertoolsavailability) 策略设置为 `0` 或 `1`。

### <a name="upgrading-from-selenium-3-to-selenium-4"></a>从 Selenium 3 升级到 Selenium 4

如果使用 Selenium 4，则无需使用 Selenium Tools for Microsoft Edge。  适用于 Microsoft Edge 的 Selenium 工具仅适用于 Selenium 3。  如果您尝试将 Selenium 4 与 Selenium Tools for Microsoft Edge`EdgeDriver`并尝试创建新实例，则收到以下错误： `System.MissingMethodException: 'Method not found: 'OpenQA.Selenium.Remote.DesiredCapabilities OpenQA.Selenium.DriverOptions.GenerateDesiredCapabilities(Boolean)'`。

如果你使用的是 Selenium 4 `Microsoft.Edge.SeleniumTools` 并收到此错误，请从项目中删除 ，并确保你正在使用命名空间中的 official `EdgeOptions` `EdgeDriver` `OpenQA.Selenium.Edge` 和 类。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Selenium 文档](https://www.selenium.dev/documentation) - 有关 Selenium 上下文中的 WebDriver 以及如何使用 Selenium 编写自动 WebDriver 测试的信息。
*  联系 [Microsoft Edge DevTools](../devtools-guide-chromium/contact.md) 团队，发送有关使用 WebDriver、WebDriver 测试框架 (如 Selenium) 和 Microsoft Edge。
