---
title: 定义应用快捷方式
description: 了解如何在任务栏的上下文菜单中Windows应用的常见任务。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/13/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， 边缘， Windows， 任务栏， 跳转列表， 快捷方式
ms.openlocfilehash: 9a524f8aa5b9465f172f59eb2fd9b04ef4e9e28a
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087093"
---
# <a name="define-app-shortcuts"></a>定义应用快捷方式

应用快捷方式使用户能够更快、更轻松地完成常见任务，并可以提升他们对应用的参与度。

在移动设备上，快捷方式通常可以通过长按应用图标来访问。 在Windows，快捷方式作为 Jumplist 集成。 Jumplists define popup menus that appear when you use the context menu (right-click) on a tile in the Start Menu or an icon in the Taskbar.

:::row:::
    :::column span="1":::
        :::image type="content" source="../media/edge-ios-shortcuts.png" alt-text="iOS 上Microsoft Edge快捷方式。" lightbox="../media/edge-ios-shortcuts.png":::
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../media/pwa-shortcuts-in-taskbar.png" alt-text="Twitter 应用上的 Jumplist Windows。" lightbox="../media/pwa-shortcuts-in-taskbar.png":::
    :::column-end:::
:::row-end:::

PWA 还可以将常见任务定义为 [Web 应用清单中的快捷方式](./web-app-manifests.md)。


<!-- ====================================================================== -->
## <a name="define-shortcuts"></a>定义快捷方式

使用清单成员定义 `shortcuts` 快捷方式。 此成员是一个可以包含多个快捷方式的数组。 每个快捷方式实质上都是在使用快捷方式和启动应用时请求的 URL。

```json
{
    "shortcuts" : [
        {
            "name": "Today's agenda",
            "url": "/today",
            "description": "List of events planned for today"
        },
        {
            "name": "New event",
            "url": "/create/event"
        },
        {
            "name": "New reminder",
            "url": "/create/reminder"
        }
    ]
}
```

可以使用下列属性：

| 属性 | 详细信息 |
|---|---|
| `name` | 在跳转列表或上下文 **菜单上向** 用户显示的字符串。 |
| `short_name` | 当空间不足，无法显示快捷方式的完整名称时显示的字符串。 |
| `description` | 一个描述快捷方式用途的字符串。  该字符串可通过辅助技术访问。 |
| `url` | 激活快捷方式时打开的 Web 应用中的 URI。 |
| `icons` | 一组表示快捷方式的图标。 |

若要了解更多信息，请参阅 [快捷方式 MDN 文档](https://developer.mozilla.org/docs/Web/Manifest/shortcuts)。


<!-- ====================================================================== -->
## <a name="debug-shortcuts"></a>调试快捷方式

通过使用 DevTools 的应用程序面板，可以测试快捷方式是否正确**** 配置。

1.   [打开 DevTools，](../../devtools-guide-chromium/open/index.md)例如通过选择 `F12` 。
1.   导航到**应用程序**  >  **清单**。
1.   向下滚动以显示快捷方式列表。

:::image type="content" source="../media/devtools-debug-shortcuts.png" alt-text="快捷方式在应用程序面板中列出。" lightbox="../media/devtools-debug-shortcuts.png":::

若要了解有关使用应用程序面板调试 PWA 的信息，请参阅调试 [渐进 Web 应用](../../devtools-guide-chromium/progressive-web-apps/index.md)。
