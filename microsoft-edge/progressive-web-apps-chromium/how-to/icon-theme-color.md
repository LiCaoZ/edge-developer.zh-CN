---
title: 定义图标和主题颜色
description: 了解如何为PWA定义应用图标、标题栏的主题颜色和应用窗口的背景色。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/27/2021
ms.openlocfilehash: 80208fec22b8db071be1f726b4224248d5ddcc8f
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12553692"
---
# <a name="define-icons-and-a-theme-color"></a>定义图标和主题颜色

Windows上安装的 PVA 可以按照它们在操作系统 (OS) 中显示的方式进行自定义。  PWA可以为标题栏定义一组图标和主题颜色。


<!-- ====================================================================== -->
## <a name="define-icons"></a>定义图标

在Windows中，用户可通过其图标识别应用。 图标显示在任务栏、"开始"菜单菜单和其他位置（如系统设置）中。

PWA可以配置操作系统应用于在这些不同位置显示图标的图像文件。  可以提供多个映像供 OS 选择，具体取决于上下文。

在 Web 应用清单文件中，使用成员定义 `icons` 应用图标：

```json
{
    "icons": [
        {
            "src": "/icons/icon-192x192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        {
            "src": "/icons/icon-256x256.png",
            "sizes": "256x256",
            "type": "image/png"
        },
        {
            "src": "/icons/icon-384x384.png",
            "sizes": "384x384",
            "type": "image/png"
        },
        {
            "src": "/icons/icon-512x512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ]
}
```

数组中的 `icons` 每个图标应至少附带属性 `src` 和 `sizes` 属性。  图标还可以具有这些 `type` 属性和 `purpose` 属性。

| 属性 | 描述 |
|:--- |:--- |
| `src` | 图像文件的路径，可以是应用根文件夹中的相对路径，也可以是绝对 URL。 |
| `sizes` | 可用于相应映像的大小的空格分隔列表。 |
| `type` | OS 快速检测图像类型的可选提示。 |
| `purpose` | 一个可选提示，可帮助 OS 根据上下文选择正确的图标图像。  值可以是 `monochrome`， `maskable`或者 `any`。 |

详细了解 [图标成员](https://developer.mozilla.org/docs/Web/Manifest/icons)。

<!-- TODO: add information about which sizes Windows require at a minimum, and which sizes are used where -->


<!-- ====================================================================== -->
## <a name="choose-a-theme-color"></a>选择主题颜色

在Windows上，PVA 有自己的应用程序窗口，标题栏包含应用名称和系统**关闭**、**最大化**和**最小化**图标。

PWA创建的 Web 内容填充窗口的整个外围区域，标题栏区域除外，该区域可使用主题颜色进行自定义。

下图显示了PWA的标题栏在不使用主题颜色以及使用与应用主要颜色匹配的主题颜色时的外观：

![不使用和使用主题颜色之间的区别。](../media/app-theme-color-before-after.png)

若要定义主题颜色，请使用 `theme_color` Web 应用清单成员：

```json
{
    "theme_color": "#0d4c73"
}
```

单个网页也可以使用 [`theme-color` 元标记](https://developer.mozilla.org/docs/Web/HTML/Element/meta/name/theme-color)定义主题颜色。 当页面上存在此元标记时，其定义的颜色将替代在 Web 应用清单中找到的颜色。

> [!NOTE]
> 可以使用 [窗口控件覆盖](window-controls-overlay.md) 功能在标题栏区域中显示应用内容。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [PWABuilder 映像生成器](https://www.pwabuilder.com/imageGenerator)
