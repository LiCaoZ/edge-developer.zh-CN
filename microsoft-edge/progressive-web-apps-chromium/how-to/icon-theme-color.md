---
title: 定义图标和主题颜色
description: 了解如何为应用窗口定义PWA图标、标题栏的主题颜色以及应用窗口的背景色。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/27/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， 边缘， Windows， 主题， 颜色， 图标
ms.openlocfilehash: d790d6e327fedd884fee1f6b4663588d21a824a9
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12156464"
---
# <a name="define-icons-and-a-theme-color"></a>定义图标和主题颜色

安装在 PBA Windows能够自定义它们在网站没有的操作系统中的显示方式。 它们可以为标题栏定义一组图标和主题颜色。


<!-- ====================================================================== -->
## <a name="define-icons"></a>定义图标

在Windows中，用户可以使用其图标识别应用。 图标显示在任务栏、"开始"菜单和其他位置（如系统设置）中。

用户可以PWA操作系统应该使用哪些图像文件在这些不同位置显示图标。 可以针对操作系统提供多个图像进行选择，具体取决于上下文。

在 Web 应用清单文件中，应用图标使用 成员 `icons` 定义：

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

数组中的 `icons` 每个图标应至少具有 和 `src` 属性， `sizes` 但也可以具有 `type` 和 `purpose` 属性。

| 属性 | 描述 |
|:--- |:--- |
| `src` | 图像文件的路径，可以是应用根文件夹的相对路径或绝对 URL。 |
| `sizes` | 一个以空格分隔的大小列表，对应图像可用于这些大小。 |
| `type` | 操作系统快速检测映像类型的可选提示 |
| `purpose` | 操作系统根据上下文选择正确映像的可选提示。 这可以是 `monochrome` 、 `maskable` 或 `any` 。 |

详细了解图标 [成员](https://developer.mozilla.org/docs/Web/Manifest/icons)。

<!-- TODO: add information about which sizes Windows require at a minimum, and which sizes are used where -->


<!-- ====================================================================== -->
## <a name="choose-a-theme-color"></a>选择主题颜色

在Windows，PWA 具有自己的应用程序窗口，标题栏包含应用名称和系统关键关闭、最大化和最小化按钮。

由模板创建的 web PWA填充窗口的整个图面区域，标题栏区域除外，可以使用主题颜色自定义该区域。

下图显示了在PWA主题颜色以及使用与主要应用颜色相匹配的颜色时应用的外观。

:::image type="content" source="../media/app-theme-color-before-after.png" alt-text="不使用和使用主题颜色的区别。" lightbox="../media/app-theme-color-before-after.png":::

定义主题颜色，使用 Web `theme_color` 应用清单成员，如下所示：

```json
{
    "theme_color": "#0d4c73"
}
```

各个网页还可使用 meta 标记定义[ `theme-color` 主题颜色](https://developer.mozilla.org/docs/Web/HTML/Element/meta/name/theme-color)。 当页面上存在此 meta 标记时，其定义的颜色将替代在 Web 应用清单中发现的颜色。

> [!NOTE]
> 可以使用窗口 [控件覆盖功能](./window-controls-overlay.md) 在标题栏区域中显示应用内容。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [PWABuilder 图像生成器](https://www.pwabuilder.com/imageGenerator)
