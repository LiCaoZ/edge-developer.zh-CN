---
title: 渐进式 Web 应用入门
description: 渐进式 Web 应用和 PBA (的基础知识) 以及用于构建渐进式 Web 应用Windows。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: 渐进式 Web 应用， PWA， Edge， Windows， PWABuilder， Web 清单， 服务工作者， 推送
ms.date: 11/19/2021
ms.openlocfilehash: 9eaa2f12848da06106bec9798ec1aaaedc3a8080
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285888"
---
# <a name="get-started-with-progressive-web-apps"></a>渐进式 Web 应用入门

<!-- todo: make sure screenshots of DevTools are up-to-date -->

渐进式 Web (PWA) 是逐渐增强的 Web [应用](https://en.wikipedia.org/wiki/Progressive_enhancement)。  渐进式增强功能包括类似应用的功能，如安装、脱机支持和推送通知。

还可以打包应用商店PWA应用商店，如 Microsoft Store、Google Play 和 Mac 应用商店。  The Microsoft Store is the commercial app store that's built into Windows 10 and later.

在此概述PWA，创建一个简单的 Web 应用，并作为一个PWA。  已完成的项目适用于新式浏览器。

> [!TIP]
> 可以使用[PWABuilder](https://www.pwabuilder.com)创建新PWA、增强现有PWA或打包PWA应用商店的程序包。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

*   安装[Visual Studio Code](https://code.visualstudio.com)以编辑PWA源代码。
*   安装 [Node.js](https://nodejs.org) Web 服务器。


<!-- ====================================================================== -->
## <a name="creating-a-basic-web-app"></a>创建基本 Web 应用

若要创建空的 Web 应用，请按照 [Node Express App Generator](https://expressjs.com/starter/generator.html)中的步骤操作，并命名你的应用 `MySamplePwa` 。

在提示符中，运行以下命令，这将创建一个空的 Web 应用并安装任何依赖项：

```Shell
npx express-generator --no-view
```

```Shell
npm install
```

现在，你拥有一个简单的功能性 Web 应用。  若要启动 Web 应用，请运行以下命令：

```Shell
npm start
```

现在浏览 `http://localhost:3000` 到 以查看新的 Web 应用。

:::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="在 localhost PWA新服务器。":::


<!-- ====================================================================== -->
## <a name="getting-started-building-a-pwa"></a>开始构建PWA

现在你已拥有一个简单的 Web 应用，请通过添加 PBA 的三个 (PWA) 将其扩展为渐进式 Web App 应用程序：

*  [HTTPS](#step-1---use-https)。
*  Web [应用清单](#step-2---create-a-web-app-manifest)。
*  服务 [工作线程](#step-3---add-a-service-worker)。


<!-- ====================================================================== -->
## <a name="step-1---use-https"></a>步骤 1 - 使用 HTTPS

渐进式 Web 应用平台的关键部分（如 [服务工作者](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)）需要使用 HTTPS。  当 PWA开始启用时，必须将其发布到 HTTPS URL。  许多主机现在默认提供 HTTPS，但如果你的主机未提供 HTTPS，那么"加密"会提供创建所需证书的免费替代方案。

出于调试目的，Microsoft Edge还 `http://localhost` 允许使用 PWA API。  本教程介绍如何生成 `http://localhost` PWA。

[将 Web 应用发布为实时网站](/azure/javascript/tutorial-vscode-azure-app-service-node-03)，但请确保服务器配置为 HTTPS。  例如，你可以创建 Azure [免费帐户](https://azure.microsoft.com/free)。  如果在应用程序服务上承载Microsoft Azure[网站，](https://azure.microsoft.com/services/app-service/web)则默认情况下通过 HTTPS 提供。


<!-- ====================================================================== -->
## <a name="step-2---create-a-web-app-manifest"></a>步骤 2 - 创建 Web 应用程序清单

[Web 应用清单](https://developer.mozilla.org/docs/Web/Manifest)是一个 JSON 文件，其中包含有关应用的元数据，如名称、说明、图标等。

若要将应用部件清单添加到 Web 应用，请运行以下操作：

1.  在Visual Studio Code中，选择"**文件**  >  **""** 打开文件夹"，然后选择之前 `MySamplePwa` 创建的目录。
1.  按 `Ctrl` + `N` 以创建新文件。
1.  将以下代码复制并粘贴到新文件中：

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
1.  在 Visual Studio Code 中，打开 `/public/index.html` ，在 标记内添加以下 `<head>` 代码。

    ```html
    <link rel="manifest" href="/manifest.json">
    ```


<!-- ====================================================================== -->
## <a name="step-3---add-a-service-worker"></a>步骤 3 - 添加服务工作线程

服务工作人员是 PBA 背后的关键技术。  服务工作人员启用以前仅限于本机应用的方案，包括：
*  脱机支持。
*  高级缓存。
*  运行后台任务。

服务工作人员是专门 [负责截获](https://developer.mozilla.org/docs/Web/API/Web_Workers_API) 来自 Web 应用程序的网络请求的 Web 工作人员。  即使服务工作者未运行PWA也可以运行任务，包括：

*   为来自缓存的请求资源提供服务。
*   发送推送通知。
*   运行后台提取任务。
*   标记图标。

服务工作者在一个特殊的 JavaScript 文件中定义，如 [使用服务](https://developer.mozilla.org/docs/Web/API/Service_Worker_API/Using_Service_Workers) 工作者和服务工作者 [API 中所述](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)。

若要在项目中构建服务工作器，请使用来自生成器的缓存**PWA**工作器方法，如下所示。

1. 将[源文件pwabuilder-sw-register.jspwabuilder-sw.js](https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw-register.js)[复制到](https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw.js)Web 应用 `public` 项目中的 文件夹中。

1.  在Visual Studio Code中，打开 `/public/index.html` 。

1.  在 `<head>` 标记内，添加以下代码。

    ```html
    <script type="module" src="/pwabuilder-sw-register.js"></script>
    ```

您的 Web 应用现在具有使用缓存第一策略的服务工作器。  新服务工作线程首先从缓存获取资源，然后仅根据需要从网络获取资源。  缓存的资源包括图像、JavaScript、CSS 和 HTML。

确认服务工作线程是否运行，如下所示：

1.  转到 Web 应用，网址 `http://localhost:3000` 为 。  如果 Web 应用不可用，请运行以下命令：

    ```Shell
    npm start
    ```

1.  在Microsoft Edge中， `F12` 选择打开 DevTools。  选择 **"应用程序**"，然后选择" **服务** 工作人员"以查看服务工作人员。  如果未显示服务工作线程，则刷新页面。

    :::image type="content" source="../media/devtools-sw-overview.png" alt-text="DevTools Service Worker 概述。" lightbox="../media/devtools-sw-overview.png":::
    <!-- lightbox justified because large, detailed image -->

1.  展开"缓存"以查看服务工作器**缓存存储****选择"pwabuilder-precache"。**  应显示服务工作线程缓存的所有资源。  服务工作者缓存的资源包括应用程序图标、应用程序清单、CSS 和 JavaScript 文件。

    :::image type="content" source="../media/devtools-cache.png" alt-text="DevTools 中的服务工作器缓存。" lightbox="../media/devtools-cache.png":::
    <!-- lightbox justified because large, detailed image -->

1.  尝试PWA应用，如下所示。  在 DevTools 中，选择"**网络**"，然后将状态从 **"联机**"更改为 **"脱机"。**

    :::image type="content" source="../media/devtools-offline.png" alt-text="在 DevTools 中将应用设置为脱机模式。" lightbox="../media/devtools-offline.png":::
    <!-- lightbox justified because large, detailed image -->

1.  刷新应用。  它应显示用于从缓存提供应用资源的脱机机制。

    :::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="一PWA脱机运行。":::

现在可以安装应用。
<!-- todo: Expand the ending of the article or section.  Show a breakdown of what the service worker does. -->


<!-- ====================================================================== -->
## <a name="best-practices-and-next-steps"></a>最佳做法和下一步

若要构建可靠的实际PWA，请考虑以下 Web 应用开发最佳做法。

### <a name="cross-browser-compatibility"></a>跨浏览器兼容性

测试你的应用的 [跨浏览器兼容性](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing)。  通过在不同的浏览器PWA环境中测试，确保应用程序正常工作。  请参阅[开发人员](https://developer.microsoft.com/microsoft-edge/tools/remote)Microsoft Edge_工具_。

### <a name="responsive-design"></a>响应式设计

使用流畅的布局和灵活的图像。  [响应](https://en.wikipedia.org/wiki/Responsive_web_design) 式设计包括以下使用户体验适应用户设备的元素：

*   CSS [网格](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout)。
*   [Flexbox](https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout)。
*   [媒体查询](https://developer.mozilla.org/docs/Web/CSS/Media_Queries)。
*   [响应式图像](https://developer.mozilla.org/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)。

若要在本地测试应用，请使用浏览器 [的设备](../../devtools-guide-chromium/device-mode/testing-other-browsers.md) 仿真工具。  若要在目标设备上直接测试你的应用，请通过 Windows Android[创建远程](../../devtools-guide-chromium/remote-debugging/windows.md)调试[会话](../../devtools-guide-chromium/remote-debugging/index.md)。

### <a name="support-deep-linking"></a>支持深层链接

支持 [深层链接](https://en.wikipedia.org/wiki/Deep_linking)。  将网站的每个页面路由到唯一 URL，以便现有用户可以通过社交媒体共享来吸引更广泛的受众。

### <a name="provide-a-rich-offline-experience"></a>提供丰富的脱机体验

提供丰富的 [脱机体验](./offline.md)。  即使用户设备处于脱机状态，也使应用正常工作。  提供自定义脱机页面，而不是使用浏览器的默认脱机页面。

### <a name="use-validation-and-testing-practices"></a>使用验证和测试实践

使用软件验证和测试实践。  使用代码质量工具（如 [Webhint](https://webhint.io) linter）优化应用的效率、稳定性、安全性和辅助功能。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [MDN Web 文档上的渐进 Web 应用](https://developer.mozilla.org/Apps/Progressive)
*   [渐进式 Web 应用 web.dev](https://developers.google.com/web/progressive-web-apps)
*   [作为渐进 Web 应用的黑客](https://hnpwa.com)新闻阅读器 - 比较用于实现示例 Web 应用的不同框架PWA。
*   [百万亿美元 PBA](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition)
*   [渐进式 Web 应用的渐进路线图](https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app)
*   [使用渐进 Web 应用的脱机 POS](https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895)
*   [PWA问答&](https://www.aaron-gustafson.com/notebook/pwa-qa)
*   [Web 上的百年](https://joreteg.com/blog/betting-on-the-web)
*   [命名渐进式 Web 应用](https://fberriman.com/2017/06/26/naming-progressive-web-apps)
*   [设计和构建不带框架的渐进式 Web (第 1) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1)
*   [设计和构建不带框架的渐进式 Web (第 2) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2)
*   [设计和构建不带框架的渐进式 Web (第 3) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3)
