---
title: 渐进式 Web 应用入门
description: 概述逐步Web 应用 (PVA) 的基础知识，以及在Windows上构建渐进式Web 应用的工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/19/2021
ms.openlocfilehash: a99670f345668d0a5c0d3dba40d2e57381b2f801
ms.sourcegitcommit: 62f55a8303644d4d3f2ea29e624efcc54f465aa1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2022
ms.locfileid: "12521862"
---
# <a name="get-started-with-progressive-web-apps"></a>渐进式 Web 应用入门

<!-- todo: make sure screenshots of DevTools are up-to-date -->

渐进式Web 应用 (PVA) 是[逐步增强的](https://en.wikipedia.org/wiki/Progressive_enhancement) Web 应用。  渐进式增强功能包括类似应用的功能，例如安装、脱机支持和推送通知。

还可以为应用商店打包PWA，例如Microsoft Store、Google Play 和 Mac App Store。  Microsoft Store是内置于Windows 10及更高版本的商业应用商店。

在本PWA基础知识概述中，你将创建一个简单的 Web 应用并将其扩展为PWA。  完成的项目适用于新式浏览器。

> [!TIP]
> 可以使用 [PWABuilder](https://www.pwabuilder.com) 创建新PWA、增强现有PWA或打包应用商店的PWA。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

*   安装[Visual Studio Code](https://code.visualstudio.com)以编辑PWA源代码。
*   [ 将Node.js](https://nodejs.org)安装为本地 Web 服务器。


<!-- ====================================================================== -->
## <a name="creating-a-basic-web-app"></a>创建基本 Web 应用

若要创建空 Web 应用，请按照 [Node Express App Generator](https://expressjs.com/starter/generator.html) 中的步骤操作，并命名应用 `MySamplePwa`。

在提示符下，运行以下命令，这些命令创建空 Web 应用并安装任何依赖项：

```Shell
npx express-generator --no-view
```

```Shell
npm install
```

现在，你有一个简单、功能实用的 Web 应用。  若要启动 Web 应用，请运行以下命令：

```Shell
npm start
```

现在浏览以 `http://localhost:3000` 查看新的 Web 应用。

:::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="在 localhost 上运行新PWA。":::


<!-- ====================================================================== -->
## <a name="getting-started-building-a-pwa"></a>开始构建PWA

现在你有一个简单的 Web 应用，通过添加 PVA 的三个要求来将其扩展为渐进式 Web 应用 (PWA) ：

*  [HTTPS](#step-1---use-https)。
*  [Web 应用清单](#step-2---create-a-web-app-manifest)。
*  [服务辅助角色](#step-3---add-a-service-worker)。


<!-- ====================================================================== -->
## <a name="step-1---use-https"></a>步骤 1 - 使用 HTTPS

渐进式Web 应用平台的关键部分（如[服务辅助角色）](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)需要使用 HTTPS。  当PWA上线时，必须将其发布到 HTTPS URL。  许多主机现在默认提供 HTTPS，但如果主机不提供 HTTPS，让我们加密提供创建必要证书的免费替代方法。

出于调试目的，Microsoft Edge还允许`http://localhost`使用PWA API。  在本教程中，你将使用`http://localhost`它来生成PWA。

[将 Web 应用发布为实时站点](/azure/javascript/tutorial-vscode-azure-app-service-node-03)，但请确保为 HTTPS 配置服务器。  例如，可以创建 [Azure 免费帐户](https://azure.microsoft.com/free)。  如果在[Microsoft Azure App 服务](https://azure.microsoft.com/services/app-service/web)上托管应用站点，则默认情况下会通过 HTTPS 提供该站点。


<!-- ====================================================================== -->
## <a name="step-2---create-a-web-app-manifest"></a>步骤 2 - 创建 Web 应用清单

[Web 应用清单](https://developer.mozilla.org/docs/Web/Manifest)是一个 JSON 文件，其中包含有关应用的元数据，例如名称、说明、图标等。

若要将应用清单添加到 Web 应用，请执行以下操作：

1.  在Visual Studio Code中，选择 **FileOpen** >  **文件夹**，然后选择`MySamplePwa`之前创建的目录。
1.  按 `Ctrl`+`N` 下以创建新文件。
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

1.  将文件另存为 `/MySamplePwa/public/manifest.json`.
1.  添加命名为`icon512.png``/MySamplePwa/public/images`的 512x512 应用图标图像。  可以将 [示例映像](../media/progressive-web-app.png) 用于测试目的。
1.  在Visual Studio Code中，打开`/public/index.html`并添加标记中的`<head>`以下代码。

    ```html
    <link rel="manifest" href="/manifest.json">
    ```


<!-- ====================================================================== -->
## <a name="step-3---add-a-service-worker"></a>步骤 3 - 添加服务辅助角色

服务工作者是 PVA 背后的关键技术。  服务工作者启用以前仅限于本机应用的方案，包括：
*  脱机支持。
*  高级缓存。
*  运行后台任务。

服务工作者是专门的 [Web 辅助角色](https://developer.mozilla.org/docs/Web/API/Web_Workers_API) ，可以截获来自 Web 应用的网络请求。  即使PWA未运行，服务工作者也可以运行任务，包括：

*   从缓存中提供请求的资源。
*   发送推送通知。
*   运行后台提取任务。
*   损坏图标。

服务辅助角色在特殊 JavaScript 文件中定义，在 [使用服务辅助角色](https://developer.mozilla.org/docs/Web/API/Service_Worker_API/Using_Service_Workers) 和 [服务辅助角色 API](https://developer.mozilla.org/docs/Web/API/Service_Worker_API) 中进行了说明。

若要在项目中生成服务辅助角色，请使用来自 PWA Builder **的缓存优先网络**服务辅助角色配方，如下所示。

1. 将源文件 [pwabuilder-sw-register.js](https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw-register.js) 并 [pwabuilder-sw.js](https://github.com/pwa-builder/pwabuilder-serviceworkers/blob/master/serviceWorker6/pwabuilder-sw.js) 到 `public` Web 应用项目中的文件夹。

1.  在Visual Studio Code中，打开`/public/index.html`。

1.  在标记中 `<head>` ，添加以下代码。

    ```html
    <script type="module" src="/pwabuilder-sw-register.js"></script>
    ```

Web 应用现在有一个使用缓存优先策略的服务辅助角色。  新的服务辅助角色首先从缓存中提取资源，并仅根据需要从网络中提取资源。  缓存的资源包括图像、JavaScript、CSS 和 HTML。

确认服务辅助角色是否正在运行，如下所示：

1.  转到 Web 应用 `http://localhost:3000`。  如果 Web 应用不可用，请运行以下命令：

    ```Shell
    npm start
    ```

1.  在Microsoft Edge中，选择`F12`打开 DevTools。  选择 **“应用程序**”，然后选择 **“服务辅助角色** ”以查看服务辅助角色。  如果未显示服务辅助角色，请刷新页面。

    :::image type="content" source="../media/devtools-sw-overview.png" alt-text="DevTools 服务辅助角色概述。" lightbox="../media/devtools-sw-overview.png":::
    <!-- lightbox justified because large, detailed image -->

1.  通过展开**缓存存储**并选择 **pwabuilder-precache** 来查看服务辅助角色缓存。  应显示服务辅助角色缓存的所有资源。  服务辅助角色缓存的资源包括应用图标、应用清单、CSS 和 JavaScript 文件。

    :::image type="content" source="../media/devtools-cache.png" alt-text="DevTools 中的服务辅助角色缓存。" lightbox="../media/devtools-cache.png":::
    <!-- lightbox justified because large, detailed image -->

1.  尝试将PWA作为脱机应用，如下所示。  在 DevTools 中，选择 **“网络**”，然后将状态从 **“联机** ”更改为 **“脱机**”。

    :::image type="content" source="../media/devtools-offline.png" alt-text="在 DevTools 中将应用设置为脱机模式。" lightbox="../media/devtools-offline.png":::
    <!-- lightbox justified because large, detailed image -->

1.  刷新应用。  它应显示脱机机制，以便从缓存中为应用的资源提供服务。

    :::image type="content" source="../media/visual-studio-nodejs-express-index.png" alt-text="脱机运行的PWA。":::

现在可以安装应用。
<!-- todo: Expand the ending of the article or section.  Show a breakdown of what the service worker does. -->


<!-- ====================================================================== -->
## <a name="best-practices-and-next-steps"></a>最佳做法和后续步骤

若要构建可靠的真实PWA，请考虑以下有关 Web 应用开发的最佳做法。

### <a name="cross-browser-compatibility"></a>跨浏览器兼容性

测试应用是否具有 [跨浏览器兼容性](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing)。  通过在不同的浏览器和环境中对其进行测试，确保PWA有效。  请参阅_Microsoft Edge开发人员处的_[工具](https://developer.microsoft.com/microsoft-edge/tools/)。

### <a name="responsive-design"></a>响应式设计

使用流畅的布局和灵活的图像。  [响应式设计](https://en.wikipedia.org/wiki/Responsive_web_design) 包括以下将 UX 适应用户设备的元素：

*   CSS [网格](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout)。
*   [Flexbox](https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout)。
*   [媒体查询](https://developer.mozilla.org/docs/Web/CSS/Media_Queries)。
*   [响应式图像](https://developer.mozilla.org/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)。

若要在本地测试应用，请使用浏览器中的 [设备仿真工具](../../devtools-guide-chromium/device-mode/testing-other-browsers.md) 。  若要直接在目标设备上测试应用，请在[Windows](../../devtools-guide-chromium/remote-debugging/windows.md)或[Android](../../devtools-guide-chromium/remote-debugging/index.md)上创建远程调试会话。

### <a name="support-deep-linking"></a>支持深度链接

支持 [深度链接](https://en.wikipedia.org/wiki/Deep_linking)。  将网站的每一页路由到唯一 URL，以便现有用户可以通过社交媒体共享帮助你吸引更广泛的受众。

### <a name="provide-a-rich-offline-experience"></a>提供丰富的脱机体验

提供丰富的 [脱机体验](offline.md)。  即使用户的设备处于脱机状态，应用也可正常工作。  提供自定义脱机页，而不是使用浏览器的默认脱机页。

### <a name="use-validation-and-testing-practices"></a>使用验证和测试做法

使用软件验证和测试做法。  使用 [Webhint](https://webhint.io) linter 等代码质量工具优化应用的效率、可靠性、安全性和辅助功能。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [MDN Web 文档上的渐进式Web 应用](https://developer.mozilla.org/Apps/Progressive)
*   [web.dev 上的渐进式Web 应用](https://developers.google.com/web/progressive-web-apps)
*   [黑客新闻读者作为渐进式Web 应用](https://hnpwa.com) - 比较实现示例PWA的不同框架和性能模式。
*   [神话破坏 PVA](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition)
*   [渐进式 Web 应用的渐进式路线图](https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app)
*   [带渐进式Web 应用的脱机 POST](https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895)
*   [PWA Q&A](https://www.aaron-gustafson.com/notebook/pwa-qa)
*   [在 Web 上投注](https://joreteg.com/blog/betting-on-the-web)
*   [命名渐进式Web 应用](https://fberriman.com/2017/06/26/naming-progressive-web-apps)
*   [设计和构建没有框架的渐进式 Web 应用程序 (第 1 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1)
*   [设计和构建没有框架的渐进式 Web 应用程序 (第 2 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2)
*   [设计和生成没有框架的渐进式 Web 应用程序 (第 3 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3)
