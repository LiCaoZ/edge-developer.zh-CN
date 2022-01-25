---
title: Puppeteer 概述
description: 使用安装者自动执行和测试Microsoft Edge。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 11/17/2021
ms.openlocfilehash: 4d1dc21e63d083119f6caa00f301c5c93c5530fa
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319687"
---
# <a name="puppeteer-overview"></a>Puppeteer 概述

[部署程序](https://pptr.dev)是一[个节点](https://nodejs.org)库，它提供高级 API 以使用[DevTools Microsoft Edge控制应用程序](https://chromedevtools.github.io/devtools-protocol)。  默认情况下，安装 [者启动无](https://en.wikipedia.org/wiki/Headless_browser) 头浏览器。  无头浏览器不会在 UI (用户界面) ，因此必须使用命令行。  还可以将一个安装器配置为在无 (运行完整) Microsoft Edge。

默认情况下，当你安装工具时，安装程序会下载最新版本的[Chromium](https://www.chromium.org/Home)，开放源代码浏览器Microsoft Edge[也基于](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration)构建。

如果已安装Microsoft Edge，可以使用[用户核心](https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-puppeteer-vs-puppeteer-core)。  `puppeteer-core` 是启动现有浏览器安装的一个轻型版本的一个（如 Microsoft Edge）。  若要下载Microsoft Edge，请转到下载[Microsoft Edge预览体验成员频道"](https://www.microsoftedgeinsider.com/download)。


<!-- ====================================================================== -->
## <a name="installing-puppeteer-core"></a>安装安装程序核心

可以使用以下命令之一 `puppeteer-core` 添加到网站或应用：

```shell
npm i puppeteer-core
```

```shell
yarn add puppeteer-core
```


<!-- ====================================================================== -->
## <a name="launch-microsoft-edge-with-puppeteer-core"></a>启动Microsoft Edge核心发布

`puppeteer-core` 类似于其他浏览器测试框架，如[WebDriver。](../webdriver-chromium/index.md)  创建浏览器实例，打开网页，然后使用安装工具 API 操作网页。

若要用于 `puppeteer-core` 启动Microsoft Edge：

1.  `puppeteer-core` 需要 Node v8.9.0 或更高版本。  确保你拥有兼容的版本Node.js。  为此，请 `node -v` 从命令行运行。  另外，下面的示例使用 `async` / `await` ，它仅在 Node v7.6.0 或更高版本中受支持。

1.  在下面的代码示例中， `puppeteer-core` 启动 Microsoft Edge，转到 `https://www.microsoftedgeinsider.com` ，将屏幕截图保存为 `example.png` 。  复制以下代码段并将其另存为 `example.js` ：

    ```javascript
    const puppeteer = require('puppeteer-core');
    
    (async () => {
      const browser = await puppeteer.launch({
        executablePath: 'C:\\Program Files (x86)\\Microsoft\\Edge Dev\\Application\\msedge.exe'
      });
      const page = await browser.newPage();
      await page.goto('https://www.microsoftedgeinsider.com');
      await page.screenshot({path: 'example.png'});
    
      await browser.close();
    })();
    ```
    
1.  按照后续步骤查找可执行路径，然后更改为指向安装的 `executablePath` Microsoft Edge。  例如，在 macOS 上 `executablePath` ，Microsoft Edge Canary 应设置为 `/Applications/Microsoft\ Edge\ Canary.app/` 。

1.  若要查找 `executablePath` ，一个简单的手动方法是转到 `edge://version` 并复制该 **页面上的可执行** 文件路径。

1.  或者，若要以编程方式查找可执行路径，请首先通过[](https://www.npmjs.com/package/edge-paths)运行以下命令之一安装边缘路径包：

    ```shell
    npm i edge-paths
    ```
    
    ```shell
    yarn add edge-paths
    ```
    
1.  然后，如果使用 查找可执行 `edge-paths` 路径，请运行类似以下示例的代码。 它使用[边缘路径](https://www.npmjs.com/package/edge-paths)包以编程方式查找在操作系统上安装Microsoft Edge路径：

    ```javascript
    const edgePaths = require("edge-paths");
    
    const EDGE_PATH = edgePaths.getEdgePath();
    ```
    
1.  现在，你已经找到可执行路径， (或以编程方式) ，在 `example.js` 中设置 `executablePath: EDGE_PATH` 。  保存更改。

1.  从 `example.js` 命令行运行：

    ```shell
    node example.js
    ```

    `puppeteer-core` 启动Microsoft Edge，转到 `https://www.microsoftedgeinsider.com` ，并保存网页的屏幕截图。  可以通过调用 [page.setViewport () 来自定义屏幕截图大小 ](https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-pagesetviewportviewport)。

     以下 `example.png` 文件由 生成 `example.js` ：

     :::image type="content" source="./media/puppeteer-example.png" alt-text="由example.png生成的example.js。" lightbox="./media/puppeteer-example.png":::

前面的示例演示了可以使用一个和 介绍的基本自动化和测试方案 `puppeteer-core` 。  有关一线用户及其工作方式的信息，请参阅[一下"一线用户"。](https://pptr.dev)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebDriver](../webdriver-chromium/index.md)
*  [WebDriver (EdgeHTML)](/archive/microsoft-edge/legacy/developer/webdriver/index)
*  [Chrome 开发人员工具协议查看器GitHub](https://chromedevtools.github.io/devtools-protocol)
*  [Microsoft Edge：通过 Microsoft 体验博客上的更多开放源代码协作改善 Web](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration)
*  [下载 Microsoft Edge Insider Channels](https://www.microsoftedgeinsider.com/download)
*  [Chromium"Chromium项目"](https://www.chromium.org/Home)
*  [Node.js](https://nodejs.org)
*  [Puppeteer](https://pptr.dev)
*  [一对多核](https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-puppeteer-vs-puppeteer-core)
*  [Page.setViewport () on 一台（位于百利场上）](https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-pagesetviewportviewport)
*  [维基百科上的无头浏览器](https://en.wikipedia.org/wiki/Headless_browser)
*  [联系 Microsoft Edge DevTools](../devtools-guide-chromium/contact.md)团队，发送有关使用开发工具、处理器核心和Microsoft Edge。