---
title: 使用 Inspect 工具分析 HTML 页面
description: 如何使用 DevTools 中的"检查"工具Microsoft Edge HTML 页面。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 12/16/2021
ms.openlocfilehash: 79d0b92254c5a68a42ed572edb1d8228244bbc69
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284355"
---
# <a name="analyze-html-pages-using-the-inspect-tool"></a>使用 Inspect 工具分析 HTML 页面

本文演示如何使用 **Inspect** 工具预览有关元素的信息，以及如何在当前文档中选择元素。  若要立即试用**Inspect**工具，请在阅读[](https://microsoftedge.github.io/DevToolsSamples/inspector/inspector-demo.html)本文时，打开其他选项卡或窗口中的"检查演示"页。


<!-- ====================================================================== -->
## <a name="activating-the-inspect-tool"></a>激活 Inspect 工具

" **检查** 工具"按钮位于 DevTools 的左上角。  选择" **检查工具"** 按钮时，该按钮将变为蓝色，指示 **"检查** "工具处于活动状态。

![DevTools 左上角的"检查工具"按钮。](images/inspect-tool-button.msft.png)

或者， `Control` + `Shift` + `C` 按 (Windows、Linux) `Command` + `Shift` + `C` 或 (macOS) ，以激活**Inspect**工具。


<!-- ====================================================================== -->
## <a name="getting-element-information-from-the-inspect-overlay"></a>从 Inspect 覆盖层获取元素信息

当 **Inspect 工具** 处于活动状态时，将鼠标悬停在呈现网页上的任何元素上将显示 **Inspect** 覆盖。  " **检查** "覆盖层显示有关该元素的常规和辅助功能信息。

!["检查"工具覆盖在呈现的页面上，显示有关"h1"标题元素的信息。](images/inspect-tool-padding-margin.msft.png)

当您将鼠标悬停在呈现的页面上的页面元素上时，DOM 树会自动扩展以突出显示您悬停在的元素上。

Inspect **** 覆盖层显示有关元素的以下信息：

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

例如，在"[检查演示](https://microsoftedge.github.io/DevToolsSamples/inspector/inspector-demo.html)"页中，对于按钮，"检查"覆盖层在对比度值 `Bad Contrast` 1.77 旁边有一个警告图标。 ****  " **检查** "覆盖层还显示按钮无法通过键盘对焦。  无法通过键盘导航到该按钮，因为该按钮实现为类为 的元素，而不是作为 元素 `<div>` `button` `<button>` 实现。

![缺乏足够对比度的元素具有警告图标。](images/inspect-tool-bad-contrast.msft.png)


<!-- ====================================================================== -->
## <a name="inspecting-non-accessible-elements"></a>检查不可访问的元素

CSS 属性为 的元素 `pointer-events: none` 不适用于 **Inspect** 工具。  在" [检查演示](https://microsoftedge.github.io/DevToolsSamples/inspector/inspector-demo.html) "页中，将鼠标悬停在 上，你将看到父元素 () `Overlay Button` `div.wrapper` 显示而不是 `Overlay Button` 。

![无法选择 CSS 属性为"pointer events： none"的元素。](images/inspect-tool-element-element-without-pointer-events.msft.png)

若要检查 CSS 属性为 的元素， `pointer-events: none` 请将鼠标悬停在 元素上 `Shift` 时按 。  页面布局区域上还有颜色覆盖，指示你位于高级选择模式。

![在页面上选择元素时按 Shift 键，可以选择 CSS 样式属性为"pointer-events： none"的元素。](images/inspect-tool-with-shift.msft.png)


<!-- ====================================================================== -->
## <a name="selecting-the-element-and-terminating-inspect-mode"></a>选择元素并终止 Inspect 模式

单击呈现页面中的元素时：

*  " **检查** "工具已停用。
*  突出显示相应的 DOM 节点。
*  样式 **工具** 显示应用于 元素的 CSS。

![在呈现的页面中单击某个元素时，"样式"工具将显示应用于该元素的样式。](images/inspect-tool-highlighted-styles.msft.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用"检查"工具将鼠标悬停在网页上以检测辅助功能问题](../accessibility/test-inspect-tool.md)
* [使用 DevTools 的](../accessibility/accessibility-testing-in-devtools.md) 辅助功能测试概述 - 长文章是以上链接文章的超集。
