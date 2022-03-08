---
title: 使用检查工具分析页面
description: 如何使用 DevTools 中的"检查"工具Microsoft Edge HTML 页面。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/16/2021
ms.openlocfilehash: cddfee32e2c1fc40cc71d3da1aaede44a7da9317
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430484"
---
# <a name="analyze-pages-using-the-inspect-tool"></a>使用检查工具分析页面

使用 **Inspect** 工具查看有关已呈现网页中的项目的信息。

* 当 **Inspect 工具** 处于活动状态时， _将鼠标_ 悬停在网页中的项目上，DevTools 在网页上添加信息覆盖信息和网格突出显示。

* 当您单击__ 网页中的项目时，"元素"工具中的 DOM 树**** 将自动更新为显示与所呈现网页中单击的项目对应的 DOM 元素，以及"样式"选项卡中的 CSS 样式。****


<!-- ====================================================================== -->
## <a name="activating-the-inspect-tool"></a>激活 Inspect 工具

若要试用 **Inspect 工具** ：

1. 打开新 [窗口或](https://microsoftedge.github.io/Demos/devtools-inspect) 选项卡中的"检查演示"页。

1. 右键单击演示网页中的任意位置， **然后选择"检查**"以打开 DevTools。

1. 在 DevTools 的左上角，单击****!["检查工具 (检查工具图标](../media/inspect-tool-icon-light-theme.png)。) 按钮。  或者，当 DevTools `Ctrl`++`Shift``C` 具有焦点时，按 (Windows、Linux) 或`C` `Command`+`Shift`+ (macOS) 。

   ![DevTools 左上角的"检查工具"按钮。](images/inspect-tool-button.msft.png)

   按钮图标将蓝色 ![ ("](../media/inspect-tool-icon-blue-light-theme.png) 检查"图标) ，指示 **"** 检查"工具处于活动状态。

1. 在呈现的网页中，将鼠标悬停在项目上方并观看信息覆盖和网格突出显示。

1. 单击呈现的网页中的项目。

   "元素"工具中的 DOM 树会自动更新，以显示与呈现网页中单击的项目相对应的 DOM 元素，以及"样式"选项卡中的 **CSS 样式。** **** 在网页中单击还会在网页**中**关闭"检查"模式。


<!-- ====================================================================== -->
## <a name="getting-element-information-from-the-inspect-overlay"></a>从 Inspect 覆盖层获取元素信息

当 **Inspect 工具** 处于活动状态时，将鼠标悬停在呈现网页上的任何元素上将显示 **Inspect** 覆盖。  " **检查** "覆盖层显示有关该元素的常规和辅助功能信息。

!["检查"工具覆盖在呈现的页面上，显示有关"h1"标题元素的信息。](images/inspect-tool-padding-margin.msft.png)

当您将鼠标悬停在呈现的页面上的页面元素上时，DOM 树会自动扩展以突出显示您悬停在的元素上。

**Inspect 覆盖**层显示有关元素的以下信息：

* 元素的名称。
* 元素的维度（以像素为单位）。
* 元素的颜色，作为十六进制值和颜色样本。
* 元素的字体设置。
* 元素的边距和填充（以像素为单位）。

显示哪些信息取决于元素的类型以及应用于它的样式。  如果元素是使用 CSS 网格或 CSS 弹性框定位的，则"检查"覆盖层中元素名称旁边将显示不同的图标：

![使用 CSS 弹性框的元素在 Inspect 覆盖中的名称旁边有一个额外的图标。](images/inspect-tool-flexbox-element.msft.png)

" **检查"** 覆盖 **层的** "辅助功能"部分显示有关以下信息：

* 文本颜色对比度。
* 报告给辅助技术的元素的名称和角色。
* 元素是否可聚焦键盘。

例如，在"[检查演示](https://microsoftedge.github.io/Demos/devtools-inspect)`Bad Contrast`"页中，对于按钮，**"检查**"覆盖层在对比度值 1.77 旁边有一个警告图标。  " **检查** "覆盖层还显示按钮无法通过键盘对焦。  无法通过`<div>``button`键盘导航到该按钮，因为该按钮实现为类为 的元素，而不是作为 元素实现`<button>`。

![缺乏足够对比度的元素具有警告图标。](images/inspect-tool-bad-contrast.msft.png)


<!-- ====================================================================== -->
## <a name="inspecting-non-accessible-elements"></a>检查不可访问的元素

CSS 属性为 的元素 `pointer-events: none` 不适用于 **Inspect** 工具。  在" [检查演示](https://microsoftedge.github.io/Demos/devtools-inspect) "页中，将 `Overlay Button` `div.wrapper` 鼠标悬停在 上，你将看到父元素 () 显示而不是 `Overlay Button`。

![无法选择 CSS 属性为"pointer events： none"的元素。](images/inspect-tool-element-element-without-pointer-events.msft.png)

若要检查 CSS 属性为 `pointer-events: none`的元素，请将鼠标 `Shift` 悬停在 元素上时按 。  页面布局区域上还有颜色覆盖，指示你位于高级选择模式。

![在页面上选择元素时按 Shift 键，可以选择 CSS 样式属性为"pointer-events： none"的元素。](images/inspect-tool-with-shift.msft.png)


<!-- ====================================================================== -->
## <a name="selecting-the-element-and-terminating-inspect-mode"></a>选择元素并终止 Inspect 模式

单击呈现页面中的元素时：

*  " **检查** "工具已停用。
*  突出显示相应的 DOM 节点。
*  **样式工具**显示应用于 元素的 CSS。

![在呈现的页面中单击某个元素时，"样式"工具将显示应用于该元素的样式。](images/inspect-tool-highlighted-styles.msft.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用"检查"工具将鼠标悬停在网页上以检测辅助功能问题](../accessibility/test-inspect-tool.md)
* [使用 DevTools 的](../accessibility/accessibility-testing-in-devtools.md) 辅助功能测试概述 - 长文章是以上链接文章的超集。
