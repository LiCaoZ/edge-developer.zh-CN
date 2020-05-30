---
description: 在 Microsoft Edge 中使用 Puppeteer 自动处理和测试
title: Puppeteer
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/27/2020
ms.topic: article
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge，web 开发，开发人员，工具，自动化，测试
ms.openlocfilehash: a78bdc0eb96db018818ef122c772bc9023adac46
ms.sourcegitcommit: 4187d4c3fbf4ef99a3b8a63db8a182355c84c1f9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "10601935"
---
# <span data-ttu-id="df842-104">Puppeteer</span><span class="sxs-lookup"><span data-stu-id="df842-104">Puppeteer</span></span>  

<span data-ttu-id="df842-105">[Puppeteer][|::ref1::|Main]是一个[节点][NodejsMain]库，它提供了一个高级别 API，可通过[DevTools 协议][GithubChromedevtoolsProtocol]控制 Microsoft Edge \ （Chromium \）。</span><span class="sxs-lookup"><span data-stu-id="df842-105">[Puppeteer][|::ref1::|Main] is a [Node][NodejsMain] library which provides a high-level API to control Microsoft Edge \(Chromium\) over the [DevTools Protocol][GithubChromedevtoolsProtocol].</span></span>  <span data-ttu-id="df842-106">默认情况下，Puppeteer 运行无[头][WikiHeadlessBrowser]，这意味着你看不到 UI，而是必须使用命令行。</span><span class="sxs-lookup"><span data-stu-id="df842-106">Puppeteer runs [headless][WikiHeadlessBrowser] by default, which means that you do not see a UI, and instead must use the command-line.</span></span>  <span data-ttu-id="df842-107">您也可以将 Puppeteer 配置为同时运行完整 \ （非外设 \） Microsoft Edge 或 Chromium。</span><span class="sxs-lookup"><span data-stu-id="df842-107">You may also configure Puppeteer to run full \(non-headless\) Microsoft Edge or Chromium as well.</span></span>  

<span data-ttu-id="df842-108">默认情况下，当你安装 Puppeteer 时，安装程序将下载[Chromium][ChromiumHome]的最新版本，[还会生成 Microsoft Edge][MicrosoftBlogsWindowsExperience20181206]的 "开放源代码浏览器"。</span><span class="sxs-lookup"><span data-stu-id="df842-108">By default, when you install Puppeteer, the installer downloads a recent version of [Chromium][ChromiumHome], the open-source browser that [Microsoft Edge is also built upon][MicrosoftBlogsWindowsExperience20181206].</span></span>  <span data-ttu-id="df842-109">如果安装了 Microsoft Edge \ （Chromium \），则可以使用[puppeteer-core][PuppeteerApivscore]。</span><span class="sxs-lookup"><span data-stu-id="df842-109">If you have Microsoft Edge \(Chromium\) installed, you may use [puppeteer-core][PuppeteerApivscore].</span></span>  `puppeteer-core` <span data-ttu-id="df842-110">是一种轻量级版本的 Puppeteer，用于启动现有的浏览器安装，如 Microsoft Edge \ （Chromium \）。</span><span class="sxs-lookup"><span data-stu-id="df842-110">is a lightweight version of Puppeteer that launches an existing browser installation, like Microsoft Edge \(Chromium\).</span></span>  <span data-ttu-id="df842-111">若要下载 Microsoft Edge \ （Chromium \），请参阅[下载 Microsoft Edge 预览体验成员频道][MicrosoftedgeinsiderDownload]。</span><span class="sxs-lookup"><span data-stu-id="df842-111">To download Microsoft Edge \(Chromium\), see [Download Microsoft Edge Insider Channels][MicrosoftedgeinsiderDownload].</span></span>

## <span data-ttu-id="df842-112">安装 puppeteer</span><span class="sxs-lookup"><span data-stu-id="df842-112">Installing puppeteer-core</span></span>  

<span data-ttu-id="df842-113">你可以 `puppeteer-core` 通过以下命令之一添加到你的网站或应用。</span><span class="sxs-lookup"><span data-stu-id="df842-113">You may add `puppeteer-core` to your website or app with one of the following commands.</span></span>  

```shell
npm i puppeteer-core
```  

```shell
yarn add puppeteer-core
```  

## <span data-ttu-id="df842-114">通过 puppeteer 启动 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="df842-114">Launch Microsoft Edge with puppeteer-core</span></span>  

> [!NOTE]
> `puppeteer-core` <span data-ttu-id="df842-115">依赖于节点 v 8.9.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="df842-115">relies on Node v8.9.0 or later.</span></span>  <span data-ttu-id="df842-116">下面的示例使用 `async` / `await` 了仅在节点 v 7.6.0 或更高版本中才受支持的示例。</span><span class="sxs-lookup"><span data-stu-id="df842-116">The example below uses `async`/`await` which is only supported in Node v7.6.0 or later.</span></span>  <span data-ttu-id="df842-117">`node -v`从命令行运行以确保你有兼容的 node.js 版本。</span><span class="sxs-lookup"><span data-stu-id="df842-117">Run `node -v` from the command-line to ensure you have a compatible version of Node.js.</span></span>  

`puppeteer-core` <span data-ttu-id="df842-118">应熟悉其他浏览器测试框架（如[WebDriver][WebDriverEdgehtmlMain]）的用户。</span><span class="sxs-lookup"><span data-stu-id="df842-118">should be familiar to users of other browser-testing-frameworks like [WebDriver][WebDriverEdgehtmlMain].</span></span>  <span data-ttu-id="df842-119">创建一个浏览器实例，打开一个页面，然后使用 Puppeteer API 对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="df842-119">You create an instance of the browser, open a page, and then manipulate it with the Puppeteer API.</span></span>  <span data-ttu-id="df842-120">在以下代码示例中， `puppeteer-core` 启动 Microsoft Edge \ （Chromium \），导航到 `https://www.microsoftedgeinsider.com` 并将屏幕截图另存为 `example.png` 。</span><span class="sxs-lookup"><span data-stu-id="df842-120">In the following code sample, `puppeteer-core` launches Microsoft Edge \(Chromium\), navigates to `https://www.microsoftedgeinsider.com`, and saves a screenshot as `example.png`.</span></span>  

<span data-ttu-id="df842-121">复制下面的代码示例并将其另存为 `example.js` 。</span><span class="sxs-lookup"><span data-stu-id="df842-121">Copy the code sample below and save it as `example.js`.</span></span>  

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

<span data-ttu-id="df842-122">更改 `executablePath` 以指向 Microsoft Edge \ （Chromium \）的安装。</span><span class="sxs-lookup"><span data-stu-id="df842-122">Change `executablePath` to point to your installation of Microsoft Edge \(Chromium\).</span></span>  <span data-ttu-id="df842-123">例如，在 macOS 上，" `executablePath` Microsoft Edge" 的 "关于" 应设置为 `/Applications/Microsoft\ Edge\ Canary.app/` 。</span><span class="sxs-lookup"><span data-stu-id="df842-123">For example, on macOS, the `executablePath` for Microsoft Edge Canary should be set to `/Applications/Microsoft\ Edge\ Canary.app/`.</span></span>  <span data-ttu-id="df842-124">若要查找 `executablePath` ，请导航到 `edge://version` 。</span><span class="sxs-lookup"><span data-stu-id="df842-124">To find the `executablePath`, navigate to `edge://version`.</span></span>  <span data-ttu-id="df842-125">保存更改。</span><span class="sxs-lookup"><span data-stu-id="df842-125">Save your changes.</span></span>  

> [!NOTE]
> <span data-ttu-id="df842-126">Microsoft Edge \ （EdgeHTML \）不起作用 `puppeteer-core` 。</span><span class="sxs-lookup"><span data-stu-id="df842-126">Microsoft Edge \(EdgeHTML\) does not work with `puppeteer-core`.</span></span>  <span data-ttu-id="df842-127">必须安装[Microsoft Edge 预览体验成员频道][MicrosoftedgeinsiderDownload]才能继续关注此示例。</span><span class="sxs-lookup"><span data-stu-id="df842-127">You must install the [Microsoft Edge Insider channels][MicrosoftedgeinsiderDownload] to continue following this example.</span></span>  

<span data-ttu-id="df842-128">现在 `example.js` 从命令行运行。</span><span class="sxs-lookup"><span data-stu-id="df842-128">Now run `example.js` from the command-line.</span></span>  

```shell
node example.js
```  

`puppeteer-core` <span data-ttu-id="df842-129">启动 Microsoft Edge，导航到 `https://www.microsoftedgeinsider.com` 页面的 800px x 600px 屏幕截图并将其保存。</span><span class="sxs-lookup"><span data-stu-id="df842-129">launches Microsoft Edge, navigates to `https://www.microsoftedgeinsider.com` and saves an 800px x 600px screenshot of the page.</span></span>  <span data-ttu-id="df842-130">你可以通过[setViewport （）][PuppeteerApipagesetviewport]自定义页面大小。</span><span class="sxs-lookup"><span data-stu-id="df842-130">You are able to customize the page size with [page.setViewport()][PuppeteerApipagesetviewport].</span></span>  

:::image type="complex" source="./media/puppeteer-example.png" alt-text="示例 .js 生成的 .png 文件。":::
   <span data-ttu-id="df842-132">图1： `example.png` 生成的文件</span><span class="sxs-lookup"><span data-stu-id="df842-132">Figure 1:  The `example.png` file produced by</span></span> `example.js`  
:::image-end:::  

<!--  
> ##### Figure 1  
> The `example.png` file produced by `example.js`  
> ![The example.png file produced by example.js](./media/puppeteer-example.png)  
-->  

<span data-ttu-id="df842-133">这只是由 Puppeteer 和的自动化和测试方案所支持的简单示例 `puppeteer-core` 。</span><span class="sxs-lookup"><span data-stu-id="df842-133">This is just a simple example of the automation and testing scenarios enabled by Puppeteer and `puppeteer-core`.</span></span>  <span data-ttu-id="df842-134">有关 Puppeteer 及其工作原理的详细信息，请参阅[Puppeteer][|::ref2::|Main]。</span><span class="sxs-lookup"><span data-stu-id="df842-134">For more information about Puppeteer and how it works, see [Puppeteer][|::ref2::|Main].</span></span>  

## <span data-ttu-id="df842-135">发送反馈</span><span class="sxs-lookup"><span data-stu-id="df842-135">Send Feedback</span></span>  

<span data-ttu-id="df842-136">Edge 开发人员团队渴望听到有关使用 Puppeteer、 `puppeteer-core` 和 Microsoft Edge 的反馈。</span><span class="sxs-lookup"><span data-stu-id="df842-136">The Edge Developer team is eager to hear your feedback about using Puppeteer, `puppeteer-core`, and Microsoft Edge.</span></span>  <span data-ttu-id="df842-137">使用 Microsoft Edge DevTools 或 tweet [@EdgeDevTools][TwitterIntentTweetEdgedevtools]中的 "**发送反馈**" 图标，让 Microsoft edge 团队知道您的想法。</span><span class="sxs-lookup"><span data-stu-id="df842-137">Use the **Send Feedback** icon in the Microsoft Edge DevTools or tweet [@EdgeDevTools][TwitterIntentTweetEdgedevtools] to let the Microsoft Edge team know what you think.</span></span>  


:::image type="complex" source="./devtools-guide-chromium/media/devtools-feedback.png" alt-text="Microsoft Edge DevTools 中的 "反馈" 图标":::
   <span data-ttu-id="df842-139">图2： Microsoft Edge DevTools 中的 "**反馈**" 图标</span><span class="sxs-lookup"><span data-stu-id="df842-139">Figure 2:  The **Feedback** icon in the Microsoft Edge DevTools</span></span>  
:::image-end:::  

<!--  
> ##### Figure 2  
> The **Feedback** icon in the Microsoft Edge DevTools  
> ![The Feedback icon in the Microsoft Edge DevTools](./devtools-guide-chromium/media/devtools-feedback.png)  
-->  

<!--## See also  

*   [WebDriver (Chromium)][WebdriverChromiumMain]  
*   [WebDriver (EdgeHTML)][WebdriverEdgehtmlMain]  
*   [Chrome DevTools Protocol Viewer on GitHub][GithubChromedevtoolsProtocol]  
*   [Microsoft Edge: Making the web better through more open source collaboration on Microsoft Experience Blog][MicrosoftBlogsWindowsExperience20181206]  
*   [Download Microsoft Edge Insider Channels][MicrosoftedgeinsiderDownload]  
*   [Chromium on The Chromium Projects][ChromiumHome]  
*   [Node.js][NodejsMain]  
*   [Puppeteer][PuppeteerMain]  
*   [puppeteer vs. puppeteer-core][PuppeteerApivscore]  
*   [page.setViewport() on Puppeteer][PuppeteerApipagesetviewport]  
*   [Headless browser on Wikipedia][WikiHeadlessBrowser]  -->  

<!-- image links -->  

<!-- links -->  

[WebdriverChromiumMain]: ./webdriver-chromium.md "WebDriver (Chromium)"  
[WebdriverEdgehtmlMain]: ./webdriver.md "WebDriver (EdgeHTML)"  

[GithubChromedevtoolsProtocol]: https://chromedevtools.github.io/devtools-protocol "Chrome DevTools 协议查看器 |GitHub"  

[MicrosoftBlogsWindowsExperience20181206]: https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration "Microsoft Edge：通过更多打开源协作提高 web 效果 |Microsoft 体验博客"  

[MicrosoftedgeinsiderDownload]: https://www.microsoftedgeinsider.com/download "下载 Microsoft Edge 预览体验成员频道"  

[ChromiumHome]: https://www.chromium.org/Home "Chromium |Chromium 项目"  

[NodejsMain]: https://nodejs.org "Node.js"  

[PuppeteerMain]: https://pptr.dev "Puppeteer"  
[PuppeteerApivscore]: https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-puppeteer-vs-puppeteer-core "puppeteer 与 puppeteer-核心 |Puppeteer"  
[PuppeteerApipagesetviewport]: https://pptr.dev/#?product=Puppeteer&version=v2.0.0&show=api-pagesetviewportviewport "setViewport （视口） |Puppeteer"  

[TwitterIntentTweetEdgedevtools]: https://twitter.com/intent/tweet?text=@EdgeDevTools "@EdgeDevTools 发布 Tweet |Twitter"  

[WikiHeadlessBrowser]: https://en.wikipedia.org/wiki/Headless_browser "无外设浏览器 |科"  