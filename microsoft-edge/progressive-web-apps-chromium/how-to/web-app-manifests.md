---
title: 使用 Web 应用清单将渐进式 Web 应用集成到操作系统
description: 了解如何使用 Web 应用清单将渐进式 Web 应用集成到操作系统中。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/07/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用、PWA、Edge、JavaScript、Windows、UWP、Microsoft Store
ms.openlocfilehash: ef92b1fc3652aebbc7d6100dd012263512c25c40
ms.sourcegitcommit: 418eca66278525e923fecaf9cc30fc9b09bb98f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2021
ms.locfileid: "12235605"
---
# <a name="use-a-web-app-manifest-to-integrate-a-progressive-web-app-into-the-operating-system"></a>使用 Web 应用清单将渐进式 Web 应用集成到操作系统

网站的 Web 应用清单控制渐进式 Web (PWA) 在设备上安装时的外观和行为。 Web 应用清单提供了一些信息，如应用名称、系统菜单中表示应用的图标文件位置，以及操作系统 (OS) 在标题栏中使用的主题颜色。

Web 应用程序清单是必须使用清单链接从网站的 HTML 页引用的 JSON 文件。 在网站的 HTML 页的 和 标记之间插入以下代码， `<head>` `</head>` 以链接到清单文件：

```html
<link rel="manifest" href="/manifest.json">
```

> [!NOTE]
> 清单文件的内容必须是有效的 JSON，但该文件也可以命名为 ，如 `app_name.webmanifest` 。 如果选择使用扩展，请验证 HTTP 服务器是否提供 `webmanifest` `application/manifest+json` MIME 类型。

清单文件至少应包含以下信息：

```json
{
    "name": "My Sample PWA",
    "lang": "en-US",
    "start_url": "/"
}
```

可以使用PWA清单成员进一步自定义清单，如下所示：

| 成员 | 描述 |
|:--- |:--- |
| `name` | 应用的名称，由操作系统用于在应用的图标旁边显示。 |
| `short_name` | 这可用于在空间不足时显示应用名称 `name` 。 |
| `lang` | 应用的主要语言。 |
| `start_url` | 操作系统启动你的应用时应导航到的首选 URL。 |
| `scope` | 定义应用的导航范围。 在此范围之外，访问的页面将还原为普通网页，而不是PWA。 这默认为 `start_url` 。 |
| `display` | 应用应的外观。 这将更改向用户显示多少浏览器 UI。 |
| `theme_color` | 应用的默认主题颜色。 这会影响操作系统显示网站。 |
| `background_color` | 应用样式表前启动应用的窗口的背景颜色。 |
| `orientation` | 在支持设备上，这将定义应用应用的默认 (如横向或纵向) 。 |
| `icons` | 由操作系统在不同上下文中使用的图标图像对象数组。 |
| `description` | 应用是什么。 |

以下清单文件使用上述清单成员：

```json
{
    "name": "My Sample PWA",
    "lang": "en-us",
    "short_name": "SamplePWA",
    "description": "A sample PWA for testing purposes",
    "start_url": "/",
    "scope": "/",
    "display": "standalone",
    "theme_color": "#2f3d58",
    "background_color": "#2f3d58",
    "orientation": "any",
    "icons": [
        {
            "src": "/icon512.png",
            "sizes": "512x512"
        }
    ]
}
```

若要了解有关清单成员的信息，请参阅 [MDN 的 Web](https://developer.mozilla.org/docs/Web/Manifest) 应用清单。

使用清单还可以解锁允许应用像本机应用一样运行的强大功能，例如添加应用快捷方式或标识为共享目标。

<!-- todo: when these experimental features land in the manifest and so are no longer experimental, move the "URI Protocol Handling" & "URL Link Handling" sections from article [Experimental features in Progressive Web Apps (PWAs)](experimental-features/index.md) into the present article, but preserve the two headings there, move them to the bottom, with a link pointing to the moved sections in this article. -->


<!-- ====================================================================== -->
## <a name="use-shortcuts-to-provide-quick-access-to-features"></a>使用快捷方式快速访问功能

大多数操作系统都通过使用连接到应用图标的右键菜单上的快捷方式快速访问关键应用功能。  若要在 Web 应用程序中PWA，请 `shortcuts` 包含 Web 应用清单中的 属性。

以下代码演示如何在 Web 应用清单中定义快捷方式。

```json
"shortcuts": [
    {
        "name": "Play Later",
        "description": "View the list of podcasts you saved for later",
        "url": "/play-later",
        "icons": [
            {
                "src": "/icons/play-later.svg",
                "type": "image/svg+xml",
                "purpose": "any"
            }
        ]
    },
    {
        "name": "Subscriptions",
        "description": "View the list of podcasts available in your subscription",
        "url": "/subscriptions?sort=desc"
    }
]
```

若要了解更多信息，请参阅 [定义应用快捷方式](shortcuts.md)。


<!-- ====================================================================== -->
## <a name="identify-your-app-as-a-share-target"></a>将应用标识为共享目标

若要使用户能够快速与本机应用程序共享链接和文件，请使用 Web `share_target` 应用程序清单中的 对象。  页面 `action` 类似于窗体。  在 对象中，定义要传递到页面的页面 `share_target` `action` 和 `action` 参数。

```json
"share_target": {
    "action": "/share.html",
    "params": {
        "title": "name",
        "text": "description",
        "url": "link"
    }
}
```

上述 `share_target` 对象建立 `/share.html` 为 `action` 共享页面。  此示例还定义了将传递到该页面的三个参数 `action` ：、 `title` `text` 和 `url` 。

若要详细了解如何使用"共享目标"功能，请参阅 [与其他应用共享内容](share.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [渐进式 Web 应用 (研讨会) 。 ](https://noti.st/aarongustafson/co3b5z/getting-started-with-progressive-web-apps-workshop)
