---
description: 使用 Playwright 自动执行和测试Microsoft Edge。
title: 使用 Playwright 自动执行和测试Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/24/2020
ms.topic: article
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge， Web 开发， 开发人员， 工具， 自动化， 测试， playwright， 节点， javascript， npm
ms.openlocfilehash: 87a8c61d1fc285adc1d759bbfedd5320b03c18d1
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141809"
---
# <a name="use-playwright-to-automate-and-test-in-microsoft-edge"></a>使用 Playwright 自动执行和测试Microsoft Edge

[Playwright](https://playwright.dev/docs/intro)是[一Node.js](https://nodejs.org) API 自动[Chromium、Firefox](https://www.mozilla.org/firefox)和[WebKit](https://webkit.org)的一个库。 [](https://www.chromium.org/Home)  Playwright 构建为启用常青、功能可靠且快速的跨浏览器 Web 自动化。  由于[Microsoft Edge构建于开放源代码Chromium，](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration)因此 Playwright 还能够自动Microsoft Edge。

默认情况下，Playwright [启动无](https://en.wikipedia.org/wiki/Headless_browser) 头浏览器。  无头浏览器不显示 UI，因此你必须使用命令行。  还可以将 Playwright 配置为 (无头) Microsoft Edge运行。


<!-- ====================================================================== -->
## <a name="install-playwright-and-browsers"></a>安装 Playwright 和浏览器

> [!NOTE]
> [Playwright](https://playwright.dev/docs/intro) 需要Node.js版本 12 或以上版本。 从 `node -v` 命令行运行，以确保具有兼容的 Node.js。  适用于 Chromium、Firefox 和 WebKit 的浏览器二进制文件跨 Windows、macOS 和 Linux 工作。 有关详细信息，请参阅 [Playwright 系统要求](https://playwright.dev/docs/library#system-requirements)。

首先，安装 [Playwright 测试](https://playwright.dev/docs/intro) 以测试网站或应用：

```console
npm i -D @playwright/test
```

若要安装浏览器，请运行以下命令，该命令[Chromium、Firefox](https://www.mozilla.org/firefox)[和](https://www.chromium.org/Home) [WebKit：](https://webkit.org)

```console
npx playwright install 
```


<!-- ====================================================================== -->
## <a name="run-a-basic-test"></a>运行基本测试

其他浏览器测试框架（如 [WebDriver](../webdriver-chromium/index.md) 或一台）的用户将熟悉 [Playwright 使用的方法](../puppeteer/index.md)。  可以创建浏览器实例，在浏览器中打开页面，然后使用 [Playwright API](https://playwright.dev/docs/api/class-playwright)操作页面。

[Playwright Test](https://playwright.dev/docs/intro)是 Playwright 的测试运行程序，可启动浏览器和上下文。 然后，将隔离页面传递到每个测试，如以下基本测试所示：

```typescript
// tests/foo.spec.ts
import { test, expect } from '@playwright/test';

test('basic test', async ({ page }) => {
  await page.goto('https://playwright.dev/');
  const title = page.locator('.navbar__inner .navbar__title');
  await expect(title).toHaveText('Playwright');
});
```

现在运行测试，如下所示：

```console
npx playwright test
```

有关运行测试的信息，请参阅 [Playwright >入门](https://playwright.dev/docs/intro)。


<!-- ====================================================================== -->
## <a name="run-tests-in-microsoft-edge"></a>在 Microsoft Edge

若要在 Microsoft Edge 中运行测试，你需要为 Playwright 配置文件创建一个测试，例如 `playwright.config.ts` 。  在配置文件内，使用 Microsoft Edge Beta 渠道创建一个项目。  (目前，没有适用于 Linux.Microsoft Edge Stable 渠道) 

```typescript
// playwright.config.ts
import { PlaywrightTestConfig } from '@playwright/test';

const config: PlaywrightTestConfig = {
  projects: [
    {
      name: 'Microsoft Edge',
      use: {
        // Supported Microsoft Edge channels are: msedge, msedge-beta, msedge-dev, msedge-canary
        channel: 'msedge-beta',
      },
    },
  ],
};

export default config
```

如果Microsoft Edge Beta尚未在系统中安装，请通过 Playwright 进行安装，如下所示：

```console
npx playwright install msedge-beta
```

使用上述文件时 `playwright.config.ts` ，Playwright Test Microsoft Edge运行测试，如下所示：

```console
npx playwright test --headed
```


<!-- ====================================================================== -->
## <a name="use-playwright-as-a-library"></a>将 Playwright 用作库

还可以将 Playwright 用作库，如以下代码所示。  此方法允许您使用不同的测试运行程序。

```javascript
// example.js
const playwright = require('playwright');

(async () => {
  const browser = await playwright.chromium.launch({
    channel: 'msedge-beta',
  });
  const context = await browser.newContext();
  const page = await context.newPage();
  await page.goto('https://www.microsoft.com/edge');
  await page.screenshot({ path: 'example.png' });

  await browser.close();
})();
```

:::image type="content" source="../media/playwright-example.png" alt-text="由example.png生成的文件example.js。" lightbox="../media/playwright-example.png":::

`example.js` 是 Playwright 启用的自动化和测试方案的简单演示。  若要在其他 Web 浏览器中拍摄屏幕截图，将上述代码从 `await playwright.chromium.launch` 更改为以下代码：

Firefox： 

```javascript
  const browser = await playwright.firefox.launch({
```

WebKit： 

```javascript
  const browser = await playwright.webkit.launch({
```

有关 Playwright 和 Playwright 测试的信息，请转到 [Playwright 网站](https://playwright.dev/docs/intro)。  请查看上[一个 Playwright](https://github.com/microsoft/playwright) GitHub。  若要通过 Playwright 共享有关自动执行和测试网站或应用的反馈， [请提交问题](https://github.com/microsoft/playwright/issues/new/choose)。
