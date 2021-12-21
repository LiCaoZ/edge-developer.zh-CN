---
title: 处理渐进式 Web 应用中的 URL
description: 如何将你的 PWA注册为 URL 处理程序，以将其与其他应用程序在操作系统中深入集成。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， URL
ms.date: 09/29/2021
ms.openlocfilehash: fc29b345ebee40e57859bd882655ea28c4d94906
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284516"
---
# <a name="handle-urls-in-progressive-web-apps"></a>处理渐进式 Web 应用中的 URL

许多操作系统上的本机应用程序都可以与 URL 相关联。 当激活关联的 URL 时，它们可以请求启动，而不是浏览器。

渐进式 Web 应用也可以以相同方式处理 URL，这样做可以创建更具吸引力的体验。

> [!NOTE]
> 目前，浏览器内页面导航不会触发PWA URL 处理。


<!-- ====================================================================== -->
## <a name="enable-url-handling"></a>启用 URL 处理

URL 处理仍处于实验阶段，若要启用它：

1.  转到 `edge://flags` "Microsoft Edge"。
1.  选择 **"搜索标志** "并键入"url 处理"。
1.  选择 **"默认**  >  **启用重启**  >  **"。**

    :::image type="content" source="../media/enable-url-handling-experiment.png" alt-text="启用 URL 处理 API 实验。":::

URL 处理也是 Microsoft Edge 中的一种Microsoft Edge。 了解如何 [在源试用版中注册网站](./origin-trials.md#enroll-your-site-in-an-origin-trial)。


<!-- ====================================================================== -->
## <a name="define-which-urls-your-app-handles"></a>定义应用处理哪些 URL

首先要声明应用处理哪些 URL。 此操作在应用清单 [文件中使用](./web-app-manifests.md) `url_handlers` 数组成员完成。

数组的每个 `url_handlers` 条目都包含一 `origin` 个字符串，该字符串是匹配原点的模式。

```json
{
    "url_handlers": [
        {
            "origin": "https://contoso.com"
        },
        {
            "origin": "https://*.contoso.com"
        },
        {
            "origin": "https://conto.so"
        }
    ]
}
```

在以上示例中，注册应用以处理其源设置为 或其任何子域以及 的 `contoso.com` `conto.so` URL。


<!-- ====================================================================== -->
## <a name="verify-the-origin-ownership"></a>验证源所有权

Microsoft Edge验证已PWA URL 的所有权，以成功启动应用。 当处理的 URL 和 PWA位于同一源上时和它们不在同一源上时，这是必需的。 在大多数情况下，PWA将处理同一来源的 URL，但这不是必需的。

源所有权通过 JSON 文件建立，该 JSON 文件Microsoft Edge验证证书和 `web-app-origin-association` URL 之间的PWA握手。

让我们以尝试处理和 URL PWA托管的示例 `https://app.contoso.com` `https://contoso.com` `https://partnerapp.com` 。

*  若要建立PWA源的所有权，以下 JSON 内容 `contoso.com` 需要在 中提供 `https://contoso.com/.well-known/web-app-origin-association` 。

    ```json
    {
        "web_apps": [
            {
                "manifest": "https://app.contoso.com/manifest.json",
                "details": {
                    "paths": [
                        "/*"
                    ]
                }
            }
        ]
    }
    ```

*  若要建立PWA源的所有权，需要在 中提供相同的 `partnerapp.com` JSON 内容 `https://partnerapp.com/.well-known/web-app-origin-association` 。

    ```json
    {
        "web_apps": [
            {
                "manifest": "https://app.contoso.com/manifest.json",
                "details": {
                    "paths": [
                        "/*"
                    ]
                }
            }
        ]
    }
    ```

若要详细了解 中的有效成员 `web-app-origin-association` ，请参阅 URL [Handlers explainer](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md#web-app-origin-association-file)。


<!-- ====================================================================== -->
## <a name="testing-url-handling"></a>测试 URL 处理

从 Web 浏览器测试应用的 URL 处理将不起作用，因为浏览器内页面导航不会触发操作系统级别的 URL 处理。

若要测试该功能，请向自己发送聊天消息应用或桌面电子邮件客户端（如 Windows 邮件）中的 URL。 还可使用"运行Windows应用：

*  按 `Windows logo key`  +  `R` 。
*  输入应用处理的 URL。
*  按 `Enter` 。

> [!NOTE]
> 目前，只有从默认系统浏览器安装的 PWA 可以处理 URL。


<!-- ====================================================================== -->
## <a name="demo"></a>演示版

[DevTools 使用技巧](https://devtoolstips.org/)是一PWA，用于处理其自己的域的 URL，以便应用在使用时（而不是网站）打开。

若要在 DevTools 应用程序上测试 URL 使用技巧：

*  [启用 Microsoft Edge。](#enable-url-handling)
*  转到[DevTools 使用技巧](https://devtoolstips.org/)。
*  在本地安装应用。
*  按 `Windows logo key`  +  `R` 以打开"Windows运行"应用。
*  输入指向网站上提示之一的 URL，例如 https://devtoolstips.org/tips/en/find-css-changes/
*  按 `Enter` 。

Windows已注册应用以处理此 URL，并要求你选择想要使用的应用。 选择 DevTools 使用技巧应用。 您还可以选择" **记住我的选择** "以避免每次看到此对话框。

:::image type="content" source="../media/devtools-tips-url-handling-app-selection.png" alt-text="选择要处理 URL 的应用程序Windows。":::

应用启动并显示提示页面。

可以在上[找到源代码GitHub。](https://github.com/captainbrosset/devtools-tips/) 特别是，应用在 [manifest.json](https://github.com/captainbrosset/devtools-tips/blob/main/src/manifest.json) 文件中注册已处理的 URL，网站在 [web-app-origin-association](https://github.com/captainbrosset/devtools-tips/blob/main/src/.well-known/web-app-origin-association) 文件中建立应用的所有权。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [处理 PBA 中的 URL 视频](https://www.youtube.com/watch?v=jYc7ih9Xwqw)。
*  [作为 URL 处理程序的 PWA。](https://web.dev/pwa-url-handler/)
