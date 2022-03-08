---
title: 检查 CSS 网格
description: 使用 Microsoft Edge DevTools 查看和更改页面 CSS 的 CSS。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: bcc3819df76d9bcf5d151e04243951679b805387
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430589"
---
# <a name="inspect-css-grid"></a>检查 CSS 网格

本文将引导你识别网站上的 CSS 网格并使用可自定义的网格叠加层来调试网格布局问题。

本文中的图表中使用的示例取自以下网页：
* [水果盒](https://jec.fyi/demo/css-grid-fruit)
* [小吃盒](https://jec.fyi/demo/css-grid-snack)


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>开始之前

CSS 网格是一种强大的 Web 布局范例。  可通过 MDN 上的 [CSS 网格布局指南](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout)开始了解 CSS 网格和许多功能。


<!-- ====================================================================== -->
## <a name="discover-css-grids"></a>探索 CSS 网格

当页面上的 HTML 元素具有`display: grid``display: inline-grid`或应用于`grid`该元素时，"元素"工具的旁边会显示**锁**屏提醒：

:::image type="content" source="../media/grid-discover-grid.msft.png" alt-text="发现网格。" lightbox="../media/grid-discover-grid.msft.png":::

单击锁屏提醒切换页面上网格覆盖的显示。  叠加层显示在元素上方，布局类似于网格，可显示网格线和轨道的位置：

:::image type="content" source="../media/grid-highlight-grid.msft.png" alt-text="切换网格锁屏提醒。" lightbox="../media/grid-highlight-grid.msft.png":::

打开“**布局**”窗格。  当网格包含在页面上时，“**布局**”窗格将包括“**网格**”部分，其中包含许多用于查看网格的选项。

:::image type="content" source="../media/grid-layout-pane.msft.png" alt-text="布局窗格。" lightbox="../media/grid-layout-pane.msft.png":::

" **布局** "窗格中的" **网格** "部分包含以下 2 个子部分：

*  叠加层显示设置
*  网格叠加层

<!--todo: verify the details for each of the sub-sections -->


<!-- ====================================================================== -->
## <a name="overlay-display-settings"></a>叠加层显示设置

在" **布局** "选项卡的" **可展开网格** "部分，" **覆盖显示设置"** 部分包含以下 UI。

### <a name="dropdown-list"></a>下拉列表

从下拉列表中选择以下选项之一：

| 线条选项 | 详细信息 |
|:--- |:--- |
| **隐藏线条标签** | 隐藏每个网格叠加层的线条标签。 |
| **显示线条编号** | 显示默认选中的每个网格覆盖 (的行) 。 |
| **显示线条名称** | 显示每个网格叠加层的线条名称（倘若提供了名称）。 |

以下各节介绍 **覆盖显示设置** 下拉列表命令。

#### <a name="hide-line-labels"></a>隐藏线条标签

在下拉列表中，选择" **隐藏线条** 标签"以隐藏每个网格覆盖线的标签。

:::image type="content" source="../media/grid-hide-line-labels.msft.png" alt-text="隐藏行标签。" lightbox="../media/grid-hide-line-labels.msft.png":::

#### <a name="show-line-numbers"></a>显示线条编号

在下拉列表中，选择"显示**** 行号"以显示默认选中的每个网格覆盖 (行) 。

默认情况下，网格叠加层上会显示正数和负数线条编号。

有关网格覆盖层中的负数详细信息，请参阅使用 [CSS Grid](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout/Line-based_Placement_with_CSS_Grid) 的基于行的位置。

:::image type="content" source="../media/grid-show-line-numbers.msft.png" alt-text="显示行号。" lightbox="../media/grid-show-line-numbers.msft.png":::

#### <a name="show-line-names"></a>显示线条名称

在下拉列表中，选择" **显示行** 名称"以查看行名称而不是数字;当提供名称时，将显示每个网格覆盖层的线条名称。  在示例中，4 条线的名称为：`left`、`middle1`、`middle2` 和 `right`。

有关网格覆盖层中的线条名称详细信息，请参阅 [使用命名网格线的布局](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout/Layout_using_Named_Grid_Lines)。

<!--In the demo, **orange** element spans from left to right, with `grid-column: left` and `grid-column: right` CSS.  Showing line names makes it easier to visualize the start and end position of the element.  -->

:::image type="content" source="../media/grid-show-line-names.msft.png" alt-text="显示行名称。" lightbox="../media/grid-show-line-names.msft.png":::

### <a name="checkboxes"></a>复选框

选择覆盖显示设置部分 **的任何复选框** ：

| 选项 | 详细信息 |
|:--- |:--- |
| **显示轨道大小**  | 显示 (或) 轨的大小。 |
| **显示区域名称** | 当 (名称) 时，显示区域名称或隐藏区域名称。 |
| **延伸网格线** | 显示 (或隐藏) 沿每个轴的网格尺寸的扩展。  默认情况下，网格线仅在设置了 `display: grid` 或 `display: inline-grid` CSS 的元素内显示。 |

以下各节介绍了这些复选框。

#### <a name="show-track-sizes"></a>显示轨道大小

选中 **"显示轨大小** "复选框，以查看网格的轨大小。

开发人员工具在每个线条标签中显示 `[authored size]` 和 `[computed size]`。

| 大小 | 详细信息 |
|:--- |:--- |
| **创作大小** | 如果尚未定义样式表 (，则省略) 。 |
| **计算大小** | 屏幕上的实际大小。 |

在演示中，`snack-box` 列大小在 `grid-template-columns:1fr 2fr;` CSS 中定义。  因此，列线条标签显示了创作大小和计算大小。

| 轨道大小 | 创作大小 | 计算大小 |
|:--- |:--- |:--- |
| **1fr** &#x2022; **96.66px** | 1fr | 96.66px |
| **2fr** &#x2022; **193.32px** | 2fr | 193.32px |

行线条标签仅显示计算大小，因为样式表中未定义行大小。

| 轨道大小 | 创作大小 | 计算大小 |
|:--- |:--- |:--- |
| **80px** | &nbsp;| 80px |
| **80px** | &nbsp;| 80px |

:::image type="content" source="../media/grid-show-track-sizes.msft.png" alt-text="显示轨大小。" lightbox="../media/grid-show-track-sizes.msft.png":::

#### <a name="show-area-names"></a>显示区域名称

若要查看区域名称，请选中"显示 **区域名称"** 复选框。  在示例中，网格中有 3 个区域：**top**、**bottom1** 和 **bottom2**。

:::image type="content" source="../media/grid-show-area-names.msft.png" alt-text="显示区域名称。" lightbox="../media/grid-show-area-names.msft.png":::

#### <a name="extend-grid-lines"></a>延伸网格线

选中" **扩展网格线** "复选框以沿每个轴将网格线扩展到视口的边缘。

:::image type="content" source="../media/grid-extend-grid-lines.msft.png" alt-text="扩展网格线。" lightbox="../media/grid-extend-grid-lines.msft.png":::


<!-- ====================================================================== -->
## <a name="grid-overlays"></a>网格叠加层

“**网格叠加层**”部分包含页面上存在的网格列表，每个网格都带有一个复选框以及各种选项。

### <a name="enable-overlay-views-of-multiple-grids"></a>启用多个网格的叠加视图

若要显示多个网格的覆盖网格，请选中每个网格名称旁边的复选框。  在示例中，有 2 个网格覆盖已启用，每个网格覆盖用不同的颜色表示：

*  `main`
*  `div.snack-box`

:::image type="content" source="../media/grid-grid-overlays.msft.png" alt-text="启用多个网格的覆盖视图。" lightbox="../media/grid-grid-overlays.msft.png":::

### <a name="customize-the-grid-overlay-color"></a>自定义网格叠加层颜色

若要打开颜色选取器并自定义网格覆盖颜色，请单击网格覆盖名称旁边的框：

:::image type="content" source="../media/grid-grid-overlays-color.msft.png" alt-text="自定义网格覆盖颜色。" lightbox="../media/grid-grid-overlays-color.msft.png":::

### <a name="highlight-the-grid"></a>突出显示网格

若要在 **"** **** ![元素"工具中突出显示 HTML 元素并滚动到网页上，请单击"元素"面板中的"显示元素" ("元素"面板图标中的"](../media/show-element-in-element-panel-icon.msft.png)显示元素"。) 图标。

:::image type="content" source="../media/grid-grid-overlays-highlight.msft.png" alt-text="突出显示网格。" lightbox="../media/grid-grid-overlays-highlight.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/css/grid)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
