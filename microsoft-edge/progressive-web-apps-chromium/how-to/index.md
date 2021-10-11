---
description: 渐进式 Web 应用和 PBA (的基础知识) 以及用于构建渐进式 Web 应用Windows。
title: 渐进式 Web 应用入门
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/15/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: 渐进式 Web 应用， PWA， Edge， Windows， PWABuilder， Web 清单， 服务工作者， 推送
ms.openlocfilehash: 1d0626d75da7a5694c754133ec967732eec64eea
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087112"
---
# <a name="get-started-with-progressive-web-apps"></a>渐进式 Web 应用入门

<!-- todo: make sure screenshots of DevTools are up-to-date -->

渐进式 Web (PWA) 是逐渐增强的 Web [应用][WikiProgressiveEnhancement]。  渐进式增强功能包括类似应用的功能，如安装、脱机支持和推送通知。  还可以打包应用商店PWA，如 Microsoft Store、Google Play 和 Mac 应用商店。  the Microsoft Store is the commercial app store that's built into Windows 10.

在此概述PWA，创建一个简单的 Web 应用，并作为一个PWA。  已完成的项目适用于新式浏览器。

> [!TIP]
> 可以使用[PWABuilder][PwaBuilder]创建新PWA、增强现有PWA或打包PWA应用商店的程序包。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

*   使用[Visual Studio Code][VisualstudioCodeMain]编辑您的PWA源代码。
*   使用 [Node.js][NodejsMain] 作为本地 Web 服务器。


<!-- ====================================================================== -->
## <a name="creating-a-basic-web-app"></a>创建基本 Web 应用

若要创建空的 Web 应用，请按照 [Node Express App Generator][ExpressjsApplicationGenerator]中的步骤操作，并命名你的应用 `MySamplePwa` 。

在提示符中，运行以下命令。

```shell
npx express-generator --no-view
```

```shell
npm install
```

这些命令会创建一个空的 Web 应用并安装任何依赖项。

现在，你拥有一个简单的功能性 Web 应用。  若要启动 Web 应用，请运行以下命令。

```shell
npm start
```

现在浏览 `http://localhost:3000` 到 以查看新的 Web 应用。

:::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="在 localhost PWA新服务器。" lightbox="../media/visual-studio-nodejs-express-index.png":::


<!-- ====================================================================== -->
## <a name="getting-started-building-a-pwa"></a>开始构建PWA

现在你已拥有一个简单的 Web 应用，请通过添加 PBA 的三个要求PWA扩展它作为应用程序[：HTTPS、Web](#step-1---use-https) [App Manifest](#step-2---create-a-web-app-manifest)和服务[辅助程序](#step-3---add-a-service-worker)。


<!-- ====================================================================== -->
## <a name="step-1---use-https"></a>步骤 1 - 使用 HTTPS

应用程序平台的关键PWA（如[服务][MDNServiceWorkerApi]工作者）需要使用 HTTPS。  当PWA上时，必须将其发布到 HTTPS URL。  许多主机现在默认提供 HTTPS，但如果主机未提供 HTTPS，那么"加密"会提供创建所需证书的免费替代方案。

出于调试目的，Microsoft Edge `http://localhost` 还允许使用 PWA API。  本教程介绍如何生成 `http://localhost` PWA。

[将 Web 应用发布为实时网站][VisualStudioNodejsTutorialPublishAzureAppService]，但请确保服务器配置为 HTTPS。  例如，你可以创建 Azure [免费帐户][AzureCreateFreeAccount]。  在应用程序服务上Microsoft Azure网站[，][AzureWebApps]默认情况下它通过 HTTPS 提供。


<!-- ====================================================================== -->
## <a name="step-2---create-a-web-app-manifest"></a>步骤 2 - 创建 Web 应用程序清单

[Web 应用清单][MDNWebAppManifest]是一个 JSON 文件，其中包含有关应用的元数据，如名称、说明、图标等。

若要将应用部件清单添加到 Web 应用，请运行以下操作：

1.  在Visual Studio Code中，选择"**文件**  >  **""** 打开文件夹"，然后选择之前 `MySamplePwa` 创建的目录。
1.  选择 `Ctrl` + `N` 以创建新文件，并粘贴以下代码段。

    ```json
    {
        "lang": "en-us",
        "name": "My Sample PWA",
        "short_name": "SamplePWA",
        "description": "A sample PWA for testing purposes",
        "start_url": "/",
        "background_color": "#2f3d58",
        "theme_color": "#2f3d58",
        "orientation": "any",
        "display": "standalone",
        "icons": [
            {
                "src": "/icon512.png",
                "sizes": "512x512"
            }
        ]
    }
    ```

1.  将文件另存为 `/MySamplePwa/public/manifest.json` 。
1.  将名为 的 512x512 应用图标图像 `icon512.png` 添加到 `/MySamplePwa/public/images` 。  您可以使用示例 [图像](../media/progressive-web-app.png) 进行测试。
1.  在 Visual Studio Code 中，打开 `/public/index.html` ，在 标记内添加以下 `<head>` 代码段。

    ```html
    <link rel="manifest" href="/manifest.json">
    ```


<!-- ====================================================================== -->
## <a name="step-3---add-a-service-worker"></a>步骤 3 - 添加服务工作线程

服务工作者是 PBA 背后的关键技术，支持以前仅限于本机应用的方案，例如脱机支持、高级缓存和运行后台任务。

服务工作人员是专门 [负责截获][MDNWebWorkers] 来自 Web 应用程序的网络请求的 Web 工作人员。 服务工作人员可以运行任务，即使PWA运行，包括：

*   为来自缓存的请求资源提供服务。
*   发送推送通知。
*   运行后台提取任务。
*   标记图标。

服务工作者在一个特殊的 JavaScript 文件中定义，如 [使用服务][MDNUsingServiceWorkers] 工作者和服务工作者 [API 中所述][MDNServiceWorkerApi]。

若要在项目中生成服务工作器，请使用来自**** PWA Builder 的缓存第一网络服务工作器方法，如下所示。

1. 将[源文件pwabuilder-sw-register.js并][PwaBuilderServiceWorkerRegisterJS][pwabuilder-sw.js][PwaBuilderServiceWorkerJS] Web 应用 `public` 项目中的文件夹。

1.  在Visual Studio Code中， `/public/index.html` 打开 并添加 标记中的以下代码 `<head>` 段。

    ```html
    <script type="module" src="/pwabuilder-sw-register.js"></script>
    ```

您的 Web 应用现在具有使用缓存第一策略的服务工作器。  新服务工作线程首先从缓存获取资源，然后仅根据需要从网络获取资源。  缓存的资源包括图像、JavaScript、CSS 和 HTML。

确认服务工作线程是否运行，如下所示：

1.  转到 Web 应用，网址 `http://localhost:3000` 为 。  如果 Web 应用不可用，请运行以下命令。

    ```shell
    npm start
    ```

1.  在Microsoft Edge中， `F12` 选择打开 DevTools。  选择 **"应用程序**"，然后选择" **服务** 工作人员"以查看服务工作人员。  如果未显示服务工作线程，则刷新页面。

    :::image type="content" source="../media/devtools-sw-overview.png" alt-text="DevTools Service Worker 概述。" lightbox="../media/devtools-sw-overview.png":::

1.  展开"缓存"以查看服务工作器**缓存存储****选择"pwabuilder-precache"。**  应显示服务工作线程缓存的所有资源。  服务工作者缓存的资源包括应用程序图标、应用程序清单、CSS 和 JavaScript 文件。

    :::image type="content" source="../media/devtools-cache.png" alt-text="DevTools 中的服务工作器缓存。" lightbox="../media/devtools-cache.png":::

1.  尝试PWA应用，如下所示。  在 DevTools 中，选择"**网络**"，然后将状态从 **"联机**"更改为 **"脱机"。**

    :::image type="content" source="../media/devtools-offline.png" alt-text="在 DevTools 中将应用设置为脱机模式。" lightbox="../media/devtools-offline.png":::

1.  刷新应用。  它应显示用于从缓存提供应用资源的脱机机制。

    :::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="一PWA脱机运行。" lightbox="../media/visual-studio-nodejs-express-index.png":::

<!-- todo: add an ending of the article here. Say that the app can now be installed, show a breakdown of what the service worker does. -->


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

若要构建可靠的实际PWA，请考虑以下 Web 最佳做法：

:::row:::
   :::column span="1":::
      [跨浏览器兼容性][MDNCrossBrowserTesting]
   :::column-end:::
   :::column span="2":::
      确保你的PWA，[通过在不同的][MicrosoftDeveloperEdgeToolsRemote]浏览器和环境中测试它。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      [响应式设计][WikiResponsiveWebDesign]
   :::column-end:::
   :::column span="2":::
      采用流畅的布局和灵活的图像。  响应式设计包括以下使用户体验适应用户设备的元素：

      *   CSS [网格][MDNCssGridLayout]
      *   [flexbox][MDNCssFlexibleBoxLayout]
      *   [媒体查询][MDNMediaQueries]
      *   [响应式图像][MDNResponsiveImages]

      使用[浏览器的设备仿真][DevToolsGuideDeviceModeTestingOtherBrowsers]工具在本地测试，或在 Windows[或 Android][DevtoolsRemoteDebuggingIndex]上创建远程调试会话[][DevtoolsRemoteDebuggingWindows]，以在目标设备上直接进行测试。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      [深度链接][WikiDeepLinking]
   :::column-end:::
   :::column span="2":::
      将网站的每个页面路由到唯一 URL，以便现有用户可以通过社交媒体共享来吸引更广泛的受众。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      [脱机体验](./offline.md)
   :::column-end:::
   :::column span="2":::
      安装后，无论用户的连接状态如何，都能正常工作，并提供自定义脱机页面，而不是使用浏览器的默认脱机页面。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      [验证和测试实践][Webhint]
   :::column-end:::
   :::column span="2":::
      使用 [Webhint][Webhint] linter 等代码质量工具优化应用的效率、稳定性、安全性和辅助功能。
   :::column-end:::
:::row-end:::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [MDN Web 文档上的渐进 Web 应用][MDNProgressiveWebApps]
*   [渐进式 Web 应用 web.dev][WebDevProgressiveWebApps]
*   [作为渐进式 Web 应用的][HackerNewsProgressiveWebApps]黑客新闻阅读器 - 比较用于实现黑客新闻阅读器示例PWA (框架和性能) 。
*   [百万亿美元 PBA][Davrous20191018MythBustingPwasNewEdgeEdition]
*   [渐进式 Web 应用的渐进路线图][CloudfourThinksProgressiveRoadmapYourWebApp]
*   [使用渐进 Web 应用的脱机 POS][MediumWebEdgeOfflinePostsProgressiveWebApps]
*   [PWA问答&][AaronGustafsonNotebookPwaQa]
*   [Web 上的百年][JoretegBlogBettingWeb]
*   [命名渐进式 Web 应用][Fberriman20170626NamingProgressiveWebApps]
*   [设计和构建不带框架的渐进式 Web (第 1) ][Smashingmagazine201907ProgressiveWebApplicationFrameworkPart1]
*   [设计和生成不带框架的渐进式 Web (第 2) ][Smashingmagazine201907ProgressiveWebApplicationFrameworkPart2]
*   [设计和构建不带框架的渐进式 Web (第 3) ][Smashingmagazine201907ProgressiveWebApplicationFrameworkPart3]


<!-- ====================================================================== -->
<!-- links -->
<!-- todo: find how many hits in this file, move to new push .md file if 0 -->
[VisualStudioNodejsTutorialPublishAzureAppService]: /azure/javascript/tutorial-vscode-azure-app-service-node-03 "使用 Node.js 将应用部署到 Azure Visual Studio Code |Microsoft Docs"

[AzureCreateFreeAccount]: https://azure.microsoft.com/free "创建 Azure 免费帐户|Microsoft Azure"
[AzureWebApps]: https://azure.microsoft.com/services/app-service/web "Web 应用|Microsoft Azure"

[VisualstudioCodeMain]: https://code.visualstudio.com "Visual Studio 代码"

[AaronGustafsonNotebookPwaQa]: https://www.aaron-gustafson.com/notebook/pwa-qa "PWA问答&"

[BrowserStackTestEdgeBrowser]: https://www.browserstack.com/test-on-microsoft-edge-browser "Microsoft Edge上的免费浏览器Windows 10 |BrowserStack"

[CloudfourThinksProgressiveRoadmapYourWebApp]: https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app "渐进式 Web 应用的渐进路线图"

[Davrous20191018MythBustingPwasNewEdgeEdition]: https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition "百年计划 PBA – 新边缘版本"

[ExpressjsApplicationGenerator]: https://expressjs.com/starter/generator.html "Express 应用程序生成器|Express"

[Fberriman20170626NamingProgressiveWebApps]: https://fberriman.com/2017/06/26/naming-progressive-web-apps "命名渐进式 Web 应用"

[HackerNewsProgressiveWebApps]: https://hnpwa.com "作为渐进式 Web 应用的黑客新闻阅读器"

[JoretegBlogBettingWeb]: https://joreteg.com/blog/betting-on-the-web "Web 上的百年"

<!-- MDN links -->
[MDNDedicatedWorkerGlobalScopePostMessage]: https://developer.mozilla.org/docs/Web/API/
[MDNProgressiveWebApps]: https://developer.mozilla.org/Apps/Progressive "渐进式 Web (PBA) |MDN"
[MDNServiceWorkerApi]: https://developer.mozilla.org/docs/Web/API/Service_Worker_API "服务工作线程 API |MDN"
[MDNUsingServiceWorkers]: https://developer.mozilla.org/docs/Web/API/Service_Worker_API/Using_Service_Workers "使用服务工作人员|MDN"
[MDNWebAppManifest]: https://developer.mozilla.org/docs/Web/Manifest "Web 应用清单|MDN"
[MDNCrossBrowserTesting]: https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing "跨浏览器测试|MDN"
[MDNWebWorkers]: https://developer.mozilla.org/docs/Web/API/Web_Workers_API "Web 工作人员 API - Web API |MDN"

[MediumWebEdgeOfflinePostsProgressiveWebApps]: https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895 "使用渐进 Web 应用的脱机 POS"

[NodejsMain]: https://nodejs.org "Node.js"

[NPMWebPushEncrypt]: https://www.npmjs.com/package/web-push#encryptuserpublickey-userauth-payload-contentencoding "encrypt (userPublicKey， userAuth， payload， contentEncoding) - web-push |NPM"

[ProgressiveWebApps]: https://pwa.rocks "渐进式 Web 应用"

[PwaBuilder]: https://www.pwabuilder.com "PWA生成器"

<!-- 404
[PwaBuilderServiceWorker]: https://www.pwabuilder.com/serviceworker "Service Worker | PWA Builder" -->

[PwaBuilderServiceWorkerJS]: https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw.js "pwabuilder-serviceworkers/pwabuilder-sw.js |GitHub"

[PwaBuilderServiceWorkerRegisterJS]: https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw-register.js "pwabuilder-serviceworkers/pwabuilder-sw-register.js |GitHub"

[Smashingmagazine201907ProgressiveWebApplicationFrameworkPart1]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1 "设计和构建不带框架的渐进式 Web (第 1) "

[Smashingmagazine201907ProgressiveWebApplicationFrameworkPart2]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2 "设计和构建不带框架的渐进式 Web 应用程序 (第 2) "

[Smashingmagazine201907ProgressiveWebApplicationFrameworkPart3]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3 "设计和构建不带框架的渐进式 Web (第 3 部分) "

[Webhint]: https://webhint.io "webhint"

[WebDevProgressiveWebApps]: https://developers.google.com/web/progressive-web-apps "渐进式 Web 应用|web.dev"

[WikiProgressiveEnhancement]: https://en.wikipedia.org/wiki/Progressive_enhancement "渐进式|Wikipedia"
[WikiResponsiveWebDesign]: https://en.wikipedia.org/wiki/Responsive_web_design "响应式 Web 设计 - 维基百科"
[WikiDeepLinking]: https://en.wikipedia.org/wiki/Deep_linking "深层链接 - Wikipedia"

[MicrosoftDeveloperEdgeToolsRemote]: https://developer.microsoft.com/microsoft-edge/tools/remote "即时测试"
[MDNCssFlexibleBoxLayout]: https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout "CSS 弹性框布局|MDN"
[MDNCssGridLayout]: https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout "CSS 网格布局 | MDN"
[MDNMediaQueries]: https://developer.mozilla.org/docs/Web/CSS/Media_Queries "媒体查询|MDN"
[MDNResponsiveImages]: https://developer.mozilla.org/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images "响应式|MDN"
[DevToolsGuideDeviceModeTestingOtherBrowsers]: ../../devtools-guide-chromium/device-mode/testing-other-browsers.md "模拟和测试其他浏览器|Microsoft Docs"
[DevtoolsRemoteDebuggingWindows]: ../../devtools-guide-chromium/remote-debugging/windows.md "远程调试 Windows 10 设备|Microsoft Docs"
[DevtoolsRemoteDebuggingIndex]: ../../devtools-guide-chromium/remote-debugging/index.md "Android 设备远程调试入门 | Microsoft Docs"
