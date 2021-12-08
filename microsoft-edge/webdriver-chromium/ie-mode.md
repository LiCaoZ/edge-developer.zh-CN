---
description: 了解如何在 IE 模式下测试旧版网站或Microsoft Edge。
title: 使用Internet Explorer驱动程序在 IE 模式下自动Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge， Web 开发， html， css， javascript， 开发人员， webdriver， selenium， 测试， 工具， 自动化， 测试， ie， Internet Explorer， ie 模式
ms.openlocfilehash: 367e18716d8f938814a653dbff7c35db801145ea
ms.sourcegitcommit: bc66f7178f405fc3ae0061172f9736eab16760b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2021
ms.locfileid: "12268307"
---
# <a name="use-internet-explorer-driver-to-automate-ie-mode-in-microsoft-edge"></a>使用Internet Explorer驱动程序在 IE 模式下自动Microsoft Edge

如果你有业务关键型的旧网站或应用，你可能需要在 IE Internet Explorer (模式下) 测试内容Microsoft Edge。  本文介绍如何开始使用 IEDriver Internet Explorer驱动程序 (IEDriver) 自动执行 IE Microsoft Edge。

iE mode in Microsoft Edge is a feature for organizations that still need Internet Explorer 11 for backward compatibility for legacy websites or apps.  若要详细了解 IE 模式，请阅读什么是 [iE Internet Explorer (IE) 模式？](/deployedge/edge-ie-mode)

从**2022 年 6 月 15**Internet Explorer 11 将不再支持某些版本的 Windows 10。 有关详细信息，请阅读Internet Explorer [11 桌面应用停用常见问题解答](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549)。


<!-- ====================================================================== -->
## <a name="download-internet-explorer-driver-iedriver"></a>下载Internet Explorer驱动程序 (IEDriver) 

若要开始在 IE 模式下在 Microsoft Edge 自动执行测试，[请下载 IEDriver](https://www.selenium.dev/downloads/)。  请确保你下载的 IEDriver 版本是或 `4.0.0.0` 更大。

:::image type="content" source="./media/iedriver-install.msft.png" alt-text="Selenium 的下载页面的 IEDriver 部分。" lightbox="./media/iedriver-install.msft.png":::


## <a name="required-configuration"></a>所需配置

若要正确配置 IEDriver、Windows和 Microsoft Edge，请完成[Selenium 的必需配置的要求](https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver#required-configuration)。  

<!-- ====================================================================== -->
## <a name="automate-ie-mode-in-microsoft-edge"></a>自动执行 IE 模式Microsoft Edge

以下各节将介绍使用 Selenium 在 IE 模式下Microsoft Edge。

> [!NOTE]
> 本文提供了有关使用 Selenium 框架的说明，但您可以使用任何支持 WebDriver 的库、框架和编程语言。  若要使用另一个框架完成相同的任务，请参阅文档中的选择框架。

若要在 IE Microsoft Edge IEDriver 中启动应用：

1.  使用 `InternetExplorerOptions` 指向浏览器的其他属性Microsoft Edge定义。

1.  启动 实例 `InternetExplorerDriver` 并传递 `InternetExplorerOptions` 。  IEDriver 启动Microsoft Edge，然后在 IE 模式下加载 Web 内容。

下一节显示完整示例，随后各节将重点介绍上面列出的每个主要步骤。


<!-- ====================================================================== -->
## <a name="the-complete-sample"></a>完整示例

以下示例在 IE Microsoft Edge启动文件，导航到 bing.com [，然后](https://www.bing.com/)搜索"WebDriver"。

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

以下各节更详细地介绍了此示例中的步骤。

<!-- ====================================================================== -->
## <a name="define-internetexploreroptions-with-additional-properties-for-microsoft-edge"></a>使用其他属性定义 InternetExplorerOptions Microsoft Edge

使用 `InternetExplorerOptions` 指向浏览器的其他属性Microsoft Edge定义。

### [<a name="c"></a>C#](#tab/c-sharp/)

1. 通过调用 定义一 `ieOptions` 个新变量 `InternetExplorerOptions()` 。

1. 将 `ieOptions.AttachToEdgeChrome` 属性设置为 `true` ， 和 设置为可执行 `ieOptions.EdgeExecutablePath` 文件Microsoft Edge路径。

```csharp
var ieOptions = new InternetExplorerOptions();
ieOptions.AttachToEdgeChrome = true;
//change the path accordingly
ieOptions.EdgeExecutablePath = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe";
```

### [<a name="python"></a>Python](#tab/python/)

1. 通过调用 定义一 `ie_options` 个新变量 `webdriver.IeOptions()` 。

1. 将 `ie_options.attach_to_edge_chrome` 属性设置为 `True` ， 和 设置为可执行 `ie_options.edge_executable_path` 文件Microsoft Edge路径。

```python
ie_options = webdriver.IeOptions()
ie_options.attach_to_edge_chrome = True
ie_options.edge_executable_path = "C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe"
```

### [<a name="java"></a>Java	](#tab/java/)

1. 通过调用 定义类型 `ieOptions` 的新 `InternetExplorerOptions` 变量 `new InternetExplorerOptions()` 。

1. 使用 `ieOptions.attachToEdgeChrome()` `ieOptions.withEdgeExecutablePath()` 可执行文件的路径调用 和 Microsoft Edge 。

```java
InternetExplorerOptions ieOptions = new InternetExplorerOptions();
ieOptions.attachToEdgeChrome();
ieOptions.withEdgeExecutablePath("C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe");
```

### [<a name="javascript"></a>JavaScript](#tab/javascript/)

1. 通过调用 定义一 `ieOptions` 个新变量 `Options()` 。

1. 使用 `ieOptions.setEdgeChromium()` 值 `true` 和 `ieOptions.setEdgePath()` 可执行文件的路径Microsoft Edge调用。

```javascript
let ieOptions = new Options();
ieOptions.setEdgeChromium(true);
ieOptions.setEdgePath('C:/Program Files (x86)/Microsoft/Edge/Application/msedge.exe');
```

* * *


<!-- ====================================================================== -->
## <a name="start-iedriver"></a>启动 IEDriver

启动 IEDriver。  IEDriver 启动Microsoft Edge，然后在 IE 模式下加载 Web 内容。

### [<a name="c"></a>C#](#tab/c-sharp/)

启动 `InternetExplorerDriver` 并传递之前定义的 `ieOptions` 。  IEDriver 在 IE Microsoft Edge启动 IE 模式。  所有页面导航和后续交互均在 IE 模式下发生。

```csharp
var driver = new InternetExplorerDriver(ieOptions);
```

### [<a name="python"></a>Python](#tab/python/)

通过调用并传递之前定义的 ，启动 IEDriver。 `webdriver.Ie` `ie_options`  IEDriver 在 IE Microsoft Edge启动 IE 模式。  所有页面导航和后续交互均在 IE 模式下发生。

```python
driver = webdriver.Ie(options=ie_options)
```

### [<a name="java"></a>Java	](#tab/java/)

通过调用并传递之前定义的 ，启动 IEDriver。 `new InternetExplorerDriver()` `ieOptions`  IEDriver 在 IE Microsoft Edge启动 IE 模式。  所有页面导航和后续交互均在 IE 模式下发生。

```java
WebDriver driver = new InternetExplorerDriver(ieOptions);
```

### [<a name="javascript"></a>JavaScript](#tab/javascript)

通过调用 和 启动 `Builder.forBrowser('ie')` IEDriver。 `setIeoptions(ieOptions)`  IEDriver 在 IE Microsoft Edge启动 IE 模式。  所有页面导航和后续交互均在 IE 模式下发生。

```javascript
let driver = await new Builder().
                       forBrowser('ie').
                       setIeOptions(ieOptions).
                       build();
```

* * *


<!-- ====================================================================== -->
## <a name="known-limitations"></a>已知限制

本节介绍以前使用 IEDriver 和 IE11 桌面应用程序的已知方案，但在 IE 模式下将 IEDriver 与 Microsoft Edge一起使用时需要解决方法。

### <a name="opening-new-windows"></a>打开新窗口

如果你的测试代码使用这些方法之一创建新的浏览器窗口，你可能需要在之后添加一个短等待操作，以确保 IEDriver 检测到新窗口：

- 使用在页面脚本中 [执行的 window.open](https://developer.mozilla.org/docs/Web/API/Window/open) 打开新窗口。
- 使用 WebDriver"新建窗口 ["命令打开新](https://w3c.github.io/webdriver/#new-window) 窗口。

若要确保已成功创建新窗口并且 IEDriver 检测到它，必须持续检查"获取窗口 [句柄](https://www.w3.org/TR/webdriver2/#get-window-handles) "命令的结果，直到该命令包含新窗口的句柄。

以下示例演示了在打开新窗口时等待检测到新窗口句柄的可能方法。

### [<a name="c"></a>C#](#tab/c-sharp/)

在打开新窗口的按钮上调用该方法后，测试代码必须等到包含 `Click` `driver.WindowHandles` 新窗口句柄。

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

在打开新窗口的按钮上调用该方法后，测试代码必须等到包含 `click` `driver.window_handles` 新窗口句柄。

```python
initial_handle_count = len(driver.window_handles)
driver.find_element(By.ID, "<Id of the button that will open a new window>").click()
new_handles = driver.window_handles
while len(new_handles) == initial_handle_count:
    new_handles = driver.window_handles
```

### [<a name="java"></a>Java	](#tab/java/)

在打开新窗口的按钮上调用该方法后，测试代码必须等到包含 `click` `driver.getWindowHandles()` 新窗口句柄。

```java
int initialHandleCount = driver.getWindowHandles().size();
driver.findElement(By.id("<Id of the button that will open a new window>")).click();        
Set<string> newHandles = driver.getWindowHandles();
while (newHandles.size() == initialHandleCount) {
    newHandles = driver.getWindowHandles();
}
```

### [<a name="javascript"></a>JavaScript](#tab/javascript/)

在打开新窗口的按钮上调用 方法后 `click` ，IEDriver 必须等待 `await driver.getAllWindowHandles()` 。

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

如果测试代码在同一窗口的多个选项卡之间切换Microsoft Edge，则处于非活动状态的选项卡可能不包含在 Get [Window Handles](https://www.w3.org/TR/webdriver2/#get-window-handles)返回的句柄列表中。  在 Internet Explorer 11 桌面应用程序中，IEDriver 将返回 IE 中所有选项卡的句柄，而不考虑激活状态。  在 IE 模式下使用 Microsoft Edge 时，如果你的测试将焦点从某个选项卡切换开，并且希望以后能够切换回该选项卡，则必须存储该选项卡的窗口句柄的副本。

<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 WebDriver 自动Microsoft Edge](/microsoft-edge/webdriver-chromium) - 使用 WebDriver Microsoft Edge实现自动化的概述。
*  [Selenium 文档](https://www.selenium.dev/documentation) - 有关 Selenium 上下文中的 WebDriver 以及如何使用 Selenium 编写自动 WebDriver 测试的信息。
*  联系[Microsoft Edge DevTools](../devtools-guide-chromium/contact.md)团队，发送有关使用 WebDriver、WebDriver 测试框架 (如 Selenium) 和 Microsoft Edge 的反馈。
