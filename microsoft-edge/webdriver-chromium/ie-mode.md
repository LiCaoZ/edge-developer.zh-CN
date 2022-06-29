---
title: 使用 Internet Explorer 驱动程序在 Microsoft Edge 中自动执行 IE 模式
description: 如何在 Microsoft Edge 的 IE 模式下测试旧版网站或应用。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 11/23/2021
ms.openlocfilehash: 5bdf4c4182e103f71567e31a0d03c9dd3b808c32
ms.sourcegitcommit: a02ef65caa79bb47e969f369f9f1eb86cc8faa37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631656"
---
# <a name="use-internet-explorer-driver-to-automate-ie-mode-in-microsoft-edge"></a>使用 Internet Explorer 驱动程序在 Microsoft Edge 中自动执行 IE 模式

如果拥有业务关键型旧版网站或应用，则可能需要在 Microsoft Edge 的 Internet Explorer (IE) 模式下测试内容。  本文介绍如何开始使用 Internet Explorer 驱动程序 (IEDriver) 在 Microsoft Edge 中自动执行 IE 模式。

对于仍需要 Internet Explorer 11 的组织而言，Microsoft Edge 中的 IE 模式是一项功能，用于旧版网站或应用的向后兼容性。  若要详细了解 IE 模式，请阅读 [什么是 Internet Explorer (IE) 模式？](/deployedge/edge-ie-mode)

从 **2022 年 6 月 15** 日开始，某些版本的 Windows 10 将不再支持 Internet Explorer 11。 有关详细信息，请阅读 [Internet Explorer 11 桌面应用停用常见问题解答](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549)。


<!-- ====================================================================== -->
## <a name="download-internet-explorer-driver-iedriver"></a>下载 Internet Explorer 驱动程序 (IEDriver) 

若要在 Microsoft Edge 的 IE 模式下开始自动执行测试， [请下载 IEDriver](https://www.selenium.dev/downloads/)。  请确保下载的 IEDriver 版本是 `4.0.0.0` 或更高版本。

![适用于 Selenium 的“下载”页的 IEDriver 部分。](media/iedriver-install.msft.png)


<!-- ====================================================================== -->
## <a name="required-configuration"></a>必需配置

若要正确配置 IEDriver、Windows 和 Microsoft Edge，请完成 [Selenium 所需配置](https://www.selenium.dev/documentation/ie_driver_server/#required-configuration)的要求。


### <a name="place-the-driver-executable-in-the-path"></a>将驱动程序可执行文件放在 PATH 中

驱动程序可执行文件需要放置在 PATH 中;请参阅 [IE 驱动程序服务器](https://www.selenium.dev/documentation/ie_driver_server/)。  该页顶部显示：“必须从”下载“页下载独立服务器可执行文件并将其放置在 PATH 中。

如果 PATH 中未包含驱动程序位置，则必须使用 Java 系统属性 `webdriver.ie.driver` 或其他方式设置驱动程序位置。


<!-- ====================================================================== -->
## <a name="automate-ie-mode-in-microsoft-edge"></a>在 Microsoft Edge 中自动执行 IE 模式

以下部分介绍如何使用 Selenium 在 Microsoft Edge 中自动执行 IE 模式。

本文提供了有关使用 Selenium 框架的说明，但你可以使用任何支持 WebDriver 的库、框架、编程语言。  若要使用另一个框架完成相同的任务，请查阅所选框架的文档。

若要使用 IEDriver 在 IE 模式下启动 Microsoft Edge：

1.  使用指向 Microsoft Edge 浏览器的其他属性进行定义 `InternetExplorerOptions` 。

1.  启动并传递它的`InternetExplorerOptions`实例`InternetExplorerDriver`。  IEDriver 启动 Microsoft Edge，然后在 IE 模式下加载 Web 内容。

下一部分显示完整的示例，然后后续部分重点介绍上面列出的每个主要步骤。


<!-- ====================================================================== -->
## <a name="the-complete-sample"></a>完整示例

以下示例在 IE 模式下启动 Microsoft Edge，导航到 [bing.com](https://www.bing.com/)，然后搜索“WebDriver”。

### [<a name="c"></a>C#](#tab/c-sharp/)

```csharp
using System;
using OpenQA.Selenium;
using OpenQA.Selenium.IE;

namespace IEDriverSample
{
    class Program
    {
        static void Main(string[] args)
        {
            var ieOptions = new InternetExplorerOptions();
            ieOptions.AttachToEdgeChrome = true;
            //change the path accordingly
            ieOptions.EdgeExecutablePath = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe";

            var driver = new InternetExplorerDriver(ieOptions);
            driver.Url = "https://bing.com";
            driver.FindElement(By.Id("sb_form_q")).SendKeys("WebDriver");
            driver.FindElement(By.Id("sb_form")).Submit();

            driver.Quit();
        }
    }
}
```

### [<a name="python"></a>Python](#tab/python/)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

ie_options = webdriver.IeOptions()
ie_options.attach_to_edge_chrome = True
ie_options.edge_executable_path = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe"

driver = webdriver.Ie(options=ie_options)

driver.get("http://www.bing.com")
elem = driver.find_element(By.ID, 'sb_form_q')
elem.send_keys('WebDriver' + Keys.RETURN)

driver.quit()
```

### [<a name="java"></a>Java	](#tab/java/)

```java
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.ie.InternetExplorerDriver;
import org.openqa.selenium.ie.InternetExplorerOptions;

public class IEDriverSample {
    public static void main(String[] args) {        
        InternetExplorerOptions ieOptions = new InternetExplorerOptions();
        ieOptions.attachToEdgeChrome();
        ieOptions.withEdgeExecutablePath("C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe");
        
        WebDriver driver = new InternetExplorerDriver(ieOptions);

        driver.get("http://www.bing.com");
        WebElement elem = driver.findElement(By.id("sb_form_q"));
        elem.sendKeys("WebDriver", Keys.RETURN);

        driver.close();
    }
}
```

### [<a name="javascript"></a>JavaScript](#tab/javascript/)

```javascript
const {Builder, By, Key, until} = require('selenium-webdriver');
const {Options} = require('selenium-webdriver/ie');

(async () => {
  let ieOptions = new Options();
  ieOptions.setEdgeChromium(true);
  ieOptions.setEdgePath('C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe');

  let driver = await new Builder().
                         forBrowser('ie').
                         setIeOptions(ieOptions).
                         build();
  try {
    await driver.get('http://www.bing.com');
    let elem = await driver.findElement(By.id('sb_form_q'));
    await elem.sendKeys('WebDriver', Key.RETURN);
    await driver.wait(until.titleIs('WebDriver - Bing'), 1000);
  } finally {
    await driver.quit();
  }
})();
```

* * *

以下部分更详细地介绍了此示例中的步骤。

<!-- ====================================================================== -->
## <a name="define-internetexploreroptions-with-additional-properties-for-microsoft-edge"></a>使用 Microsoft Edge 的其他属性定义 InternetExplorerOptions

使用指向 Microsoft Edge 浏览器的其他属性进行定义 `InternetExplorerOptions` 。

### [<a name="c"></a>C#](#tab/c-sharp/)

1. 通过调用`InternetExplorerOptions()`定义新变量`ieOptions`。

1. 将属性设置`ieOptions.AttachToEdgeChrome`为 `true`Microsoft Edge 可执行文件的路径。`ieOptions.EdgeExecutablePath`

```csharp
var ieOptions = new InternetExplorerOptions();
ieOptions.AttachToEdgeChrome = true;
//change the path accordingly
ieOptions.EdgeExecutablePath = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe";
```

### [<a name="python"></a>Python](#tab/python/)

1. 通过调用`webdriver.IeOptions()`定义新变量`ie_options`。

1. 将属性`ie_options.attach_to_edge_chrome`设置为 `True``ie_options.edge_executable_path` Microsoft Edge 可执行文件的路径。

```python
ie_options = webdriver.IeOptions()
ie_options.attach_to_edge_chrome = True
ie_options.edge_executable_path = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe"
```

### [<a name="java"></a>Java	](#tab/java/)

1. 通过调用`new InternetExplorerOptions()`定义类型`InternetExplorerOptions`的新变量`ieOptions`。

1. 调用 `ieOptions.attachToEdgeChrome()` 和 `ieOptions.withEdgeExecutablePath()` 使用 Microsoft Edge 可执行文件的路径。

```java
InternetExplorerOptions ieOptions = new InternetExplorerOptions();
ieOptions.attachToEdgeChrome();
ieOptions.withEdgeExecutablePath("C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe");
```

### [<a name="javascript"></a>JavaScript](#tab/javascript/)

1. 通过调用`Options()`定义新变量`ieOptions`。

1. 使用值`true`和 `ieOptions.setEdgePath()` Microsoft Edge 可执行文件的路径进行调用`ieOptions.setEdgeChromium()`。

```javascript
let ieOptions = new Options();
ieOptions.setEdgeChromium(true);
ieOptions.setEdgePath('C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe');
```

* * *


<!-- ====================================================================== -->
## <a name="start-iedriver"></a>启动 IEDriver

启动 IEDriver。  IEDriver 启动 Microsoft Edge，然后在 IE 模式下加载 Web 内容。

### [<a name="c"></a>C#](#tab/c-sharp/)

启动 `InternetExplorerDriver` 并传递之前定义 `ieOptions`的 。  IEDriver 在 IE 模式下启动 Microsoft Edge。  所有页面导航和后续交互都以 IE 模式进行。

```csharp
var driver = new InternetExplorerDriver(ieOptions);
```

### [<a name="python"></a>Python](#tab/python/)

通过调用 `webdriver.Ie` 并传递之前定义 `ie_options`的 IEDriver 来启动它。  IEDriver 在 IE 模式下启动 Microsoft Edge。  所有页面导航和后续交互都以 IE 模式进行。

```python
driver = webdriver.Ie(options=ie_options)
```

### [<a name="java"></a>Java	](#tab/java/)

通过调用 `new InternetExplorerDriver()` 并传递之前定义 `ieOptions`的 IEDriver 来启动它。  IEDriver 在 IE 模式下启动 Microsoft Edge。  所有页面导航和后续交互都以 IE 模式进行。

```java
WebDriver driver = new InternetExplorerDriver(ieOptions);
```

### [<a name="javascript"></a>JavaScript](#tab/javascript)

通过调用和`setIeoptions(ieOptions)`启动 `Builder.forBrowser('ie')` IEDriver。  IEDriver 在 IE 模式下启动 Microsoft Edge。  所有页面导航和后续交互都以 IE 模式进行。

```javascript
let driver = await new Builder().
                       forBrowser('ie').
                       setIeOptions(ieOptions).
                       build();
```

* * *


<!-- ====================================================================== -->
## <a name="known-limitations"></a>已知限制

本部分介绍以前与 IEDriver 和 IE11 桌面应用程序配合使用的已知方案，但在 IE 模式下将 IEDriver 与 Microsoft Edge 配合使用时需要解决方法。

### <a name="opening-new-windows"></a>打开新窗口

如果测试代码使用以下方法之一创建新的浏览器窗口，则可能需要在之后添加一个简短的等待操作，以确保 IEDriver 检测到新窗口：

- 打开在页面脚本中执行 [window.open](https://developer.mozilla.org/docs/Web/API/Window/open) 的新窗口。
- 使用 WebDriver [New Window 命令打开新窗口](https://w3c.github.io/webdriver/#new-window) 。

若要确保已成功创建新窗口并检测到 IEDriver，必须持续检查 [Get Window Handles](https://www.w3.org/TR/webdriver2/#get-window-handles) 命令的结果，直到它包含新窗口的句柄。

下面的示例演示了在打开新窗口时等待检测到新窗口句柄的可能方法。

### [<a name="c"></a>C#](#tab/c-sharp/)

在 `Click` 打开新窗口的按钮上调用该方法后，测试代码必须等待，直到 `driver.WindowHandles` 包含新的窗口句柄。

```csharp
var initialHandleCount = driver.WindowHandles.Count;
driver.FindElement(By.Id("<Id of the button that will open a new window>")).Click();
var newHandles = driver.WindowHandles;
while (newHandles.Count == initialHandleCount)
{
    newHandles = driver.WindowHandles;
}
```

### [<a name="python"></a>Python](#tab/python/)

在 `click` 打开新窗口的按钮上调用该方法后，测试代码必须等待，直到 `driver.window_handles` 包含新的窗口句柄。

```python
initial_handle_count = len(driver.window_handles)
driver.find_element(By.ID, "<Id of the button that will open a new window>").click()
new_handles = driver.window_handles
while len(new_handles) == initial_handle_count:
    new_handles = driver.window_handles
```

### [<a name="java"></a>Java	](#tab/java/)

在 `click` 打开新窗口的按钮上调用该方法后，测试代码必须等待，直到 `driver.getWindowHandles()` 包含新的窗口句柄。

```java
int initialHandleCount = driver.getWindowHandles().size();
driver.findElement(By.id("<Id of the button that will open a new window>")).click();        
Set<String> newHandles = driver.getWindowHandles();
while (newHandles.size() == initialHandleCount) {
    newHandles = driver.getWindowHandles();
}
```

### [<a name="javascript"></a>JavaScript](#tab/javascript/)

在 `click` 打开新窗口的按钮上调用该方法后，IEDriver 必须等待 `await driver.getAllWindowHandles()`。

```javascript
const initialHandleCount = (await driver.getAllWindowHandles()).length;
const elem = await driver.findElement(By.id("<Id of the button that will open a new window>"));
await elem.click();
let newHandles = await driver.getAllWindowHandles();
while (newHandles.length == initialHandleCount) {
    newHandles = await driver.getAllWindowHandles();
}
```

* * *

### <a name="creating-and-switching-between-tabs"></a>在选项卡之间创建和切换

如果测试代码在同一 Microsoft Edge 窗口中的多个选项卡之间切换，则“ [获取窗口句柄](https://www.w3.org/TR/webdriver2/#get-window-handles)”返回的句柄列表中可能不包含处于非活动状态的选项卡。  在 Internet Explorer 11 桌面应用程序中，IEDriver 将为 IE 中的所有选项卡返回句柄，而不考虑激活状态。

在 IE 模式下使用 Microsoft Edge 时，如果测试将焦点从某个选项卡切换到某个选项卡，并且希望以后能够切换回该选项卡，则必须存储选项卡窗口句柄的副本。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 WebDriver 自动执行 Microsoft Edge](/microsoft-edge/webdriver-chromium) - 使用 WebDriver 协议自动执行 Microsoft Edge 的概述。
*  [Selenium 文档](https://www.selenium.dev/documentation) - 有关 Selenium 上下文中 WebDriver 的信息，以及如何使用 Selenium 编写自动 WebDriver 测试。
*  [请联系 Microsoft Edge DevTools 团队](../devtools-guide-chromium/contact.md) ，发送有关使用 WebDriver、WebDriver 测试框架 (（如 Selenium) 和 Microsoft Edge）的反馈。
