---
title: 在呈现的页面中模拟深色或浅色方案
description: 呈现模拟用户的深色或浅色方案操作系统设置或浏览器设置的网页，而无需更改自己的计算机设置。  将 CSS 媒体查询与 DevTools 呈现选项一起用于 prefers-color-scheme。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/03/2021
ms.openlocfilehash: aebe45020329d5216d7c9fbf2e71d65a052e1079
ms.sourcegitcommit: cceea19c69eddaad5ba7d6cece07fbca2b02614e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2022
ms.locfileid: "12551473"
---
# <a name="emulate-dark-or-light-schemes-in-the-rendered-page"></a>在呈现的页面中模拟深色或浅色方案

使用 **渲染** 工具查看网页的外观，并显示不同的显示选项或视觉缺陷。

许多操作系统都能够以较深或较浅的颜色显示任何应用程序。  在深色模式操作系统中拥有浅色方案的网站可能很难读取，并且可能会成为某些用户的辅助功能问题。

若要测试当用户选择深色或浅色模式时网页的呈现方式，你可以选择**模拟 CSS prefer-color-scheme：深**色或**浅色**，Microsoft Edge DevTools。  可以从 **呈现** 工具或 **命令菜单**执行此操作，如下所述。

或者，可以通过选择 **“无仿真**”（即默认设置），使网页根据计算机上的首选设置自动选择深色或浅色模式。

若要指定用于浅色和深色方案的 CSS，请使用 [首选配色方案](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-color-scheme) CSS 媒体查询来检测用户是否倾向于在深色或浅色配色方案中显示产品，然后自动选择自己的自定义浅色或深色模式 CSS。  示例 CSS 代码显示在 [Check 中，以了解深色主题和浅色主题的对比度问题](test-dark-mode.md)。

本文介绍如何更改正在开发的网页的外观。  若要更改 DevTools 的显示方式，请 [参阅将颜色主题应用于 DevTools](../customize/theme.md)。


<!-- ====================================================================== -->
## <a name="emulating-dark-or-light-mode-using-the-rendering-tool"></a>使用呈现工具模拟深色或浅色模式

1. 在 DevTools 中，打开 **呈现** 工具。  为此，请单击主工具栏或抽屉上的“ **更多工具** (+) ”图标，然后选择 **“呈现**”。

   或者，如果渲染工具已打开但已隐藏，请单击工具栏上的 **“更多”选项卡** (>>) 图标，然后选择 **“呈现**”。

1. 在 **模拟 CSS 媒体功能首选配色方案** 下拉列表中，选择 **首选配色方案：深** 色或 **首选配色方案：浅色**。

   ![使用呈现工具模拟深色或浅色模式。](../media/css-elements-styles-qs-simulated-light-mode.msft.png)

1. 刷新页面以显示呈现的结果。

   现在，可以修改 CSS 并以与任何其他网页相同的方式查看呈现的结果。  请参阅[开始查看和更改 CSS](../css/index.md)。

1. 若要还原设置，请在 **渲染** 工具的 **模拟 CSS 媒体功能首选配色方案** 下拉列表中，选择 **“无仿真**”。  刷新页面时，将应用自己的操作系统或浏览器设置以获得浅色或深色模式首选项。


<!-- ====================================================================== -->
## <a name="emulating-dark-or-light-mode-using-the-command-menu"></a>使用命令菜单模拟深色或浅色模式

1. 当 DevTools 具有焦点时，通过选择++`Ctrl``P``Shift` (Windows、Linux) 或`Command``P`++`Shift` (macOS) 打开**命令菜单**。

1. 键入 **深色**、 **浅色**或 **仿真**，选择 **“呈现”：模拟 CSS 首选配色方案：深色** 或 **渲染：模拟 CSS 首选配色方案：浅色**，然后按 **Enter**。

   ![使用命令菜单上的“呈现：模拟 CSS 首选配色方案”命令模拟深色或浅色模式。](../media/css-console-command-menu-rendering.msft.png)

   选择 **“呈现”** 命令，而不是 **“外观** ”命令。  **呈现**命令会影响正在开发的呈现网页。  **相反，外观**命令会影响窗口的 DevTools 部分。

1. 刷新页面以显示呈现的结果。

   现在，可以修改 CSS 并以与任何其他网页相同的方式查看呈现的结果。  请参阅[开始查看和更改 CSS](../css/index.md)。

1. 若要还原设置，请在命令菜单中键入 **模拟** 或 **方案** ，然后选择 **“呈现：不要模拟 CSS prefers-color-scheme**”。  刷新页面时，将应用自己的操作系统或浏览器设置以获得浅色或深色模式首选项。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* 使用性能_功能参考_中的[呈现工具分析呈现性能](../evaluate-performance/reference.md#analyze-rendering-performance-with-the-rendering-tool)

呈现工具也用于以下内容：

* [检查深色主题和浅主题的对比度问题](test-dark-mode.md)
* [验证页面是否对色盲者可用](test-color-blindness.md)
* [验证页面是否在视觉模糊时可用](test-blurred-vision.md)
* [验证页面是否在关闭 UI 动画时可用](test-reduced-ui-motion.md)
* [模仿视觉缺陷](emulate-vision-deficiencies.md)
* [模拟运动减少](reduced-motion-simulation.md)
