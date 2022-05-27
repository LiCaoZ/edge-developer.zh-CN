---
title: 使用检查工具分析页面
description: 如何在 Microsoft Edge DevTools 中使用“检查”工具分析 HTML 页面。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/16/2021
ms.openlocfilehash: 993feb535cf3746fa77eda53423e61c3fcbe256a
ms.sourcegitcommit: cceea19c69eddaad5ba7d6cece07fbca2b02614e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2022
ms.locfileid: "12551546"
---
# <a name="analyze-pages-using-the-inspect-tool"></a>使用检查工具分析页面

使用 **“检查** ”工具查看有关呈现网页中的项的信息。

* 当 **检查** 工具处于活动状态时，将 _鼠标悬停在_ 网页中的项上，DevTools 会在网页上添加信息覆盖信息和网格突出显示。

* 在网页中 _单击_ 某个项时， **元素** 工具中的 DOM 树会自动更新，以显示与呈现的网页中单击的项相对应的 DOM 元素，以及“ **样式** ”选项卡中的 CSS 样式。


<!-- ====================================================================== -->
## <a name="activating-the-inspect-tool"></a>激活“检查”工具

若要试用 **“检查** ”工具，请执行以下操作：

1. 在新窗口或选项卡中打开 [“检查演示](https://microsoftedge.github.io/Demos/devtools-inspect) ”页。

1. 右键单击演示网页中的任意位置，然后选择 **“检查**”以打开 DevTools。

1. 在 DevTools 的左上角，单击“ **检查”工具** (![“检查”工具图标。](../media/inspect-tool-icon-light-theme.png)) 按钮。  或者，当 DevTools 具有焦点时，请按`Ctrl`++`Shift``C` (Windows、Linux) 或`C``Command`+`Shift`+ (macOS) 。

   ![DevTools 左上角的“检查”工具按钮。](images/inspect-tool-button.msft.png)

   按钮图标 (![“检查”图标变为蓝色。](../media/inspect-tool-icon-blue-light-theme.png)) ，指示 **“检查** ”工具处于活动状态。

1. 在呈现的网页中，将鼠标悬停在项上，并观看信息覆盖和网格突出显示。

1. 单击呈现的网页中的项。

   **元素**工具中的 DOM 树会自动更新，以显示与呈现的网页中的单击项相对应的 DOM 元素，以及“**样式**”选项卡中的 CSS 样式。 在网页中单击也会关闭网页中的 **“检查**”模式。


<!-- ====================================================================== -->
## <a name="getting-element-information-from-the-inspect-overlay"></a>从“检查”覆盖层获取元素信息

当 **“检查** ”工具处于活动状态时，悬停在呈现的网页上的任何元素上会显示 **“检查** ”覆盖层。  **检查**覆盖显示有关该元素的常规和辅助功能信息。

![“检查”工具覆盖在呈现的页面上，其中显示了有关“h1”标题元素的信息。](images/inspect-tool-padding-margin.msft.png)

将鼠标悬停在呈现的页面上的页面元素上时，DOM 树会自动展开，以突出显示你悬停在上面的元素。

**“检查**”覆盖显示有关该元素的以下信息：

* 元素的名称。
* 元素的维度（以像素为单位）。
* 元素的颜色，作为十六进制值和颜色监视器。
* 元素的字体设置。
* 元素的边距和填充（以像素为单位）。

显示的信息取决于元素的类型和应用于它的样式。  如果元素是使用 CSS 网格或 CSS 弹性框定位的，则在“检查”覆盖层中元素名称旁边会显示另一个图标：

![使用 CSS 弹性框的元素在“检查”覆盖层的名称旁边有一个额外的图标。](images/inspect-tool-flexbox-element.msft.png)

**“检查**”覆盖的 **“辅助功能**”部分显示以下相关信息：

* 文本颜色对比度。
* 报告给辅助技术的元素的名称和角色。
* 元素是否可对键盘进行焦点处理。

例如，在 [“检查演示](https://microsoftedge.github.io/Demos/devtools-inspect) ”页中，对于 `Bad Contrast` 按钮，“ **检查** ”覆盖层在对比度值 1.77 旁边有一个警告图标。  “ **检查** ”覆盖层还显示按钮无法通过键盘聚焦。  无法通过键盘导航到该按钮，因为按钮是作为具有 `<div>` 类的元素实现的 `button`，而不是作为 `<button>` 元素实现的。

![缺乏足够对比度的元素具有警告图标。](images/inspect-tool-bad-contrast.msft.png)


<!-- ====================================================================== -->
## <a name="inspecting-non-accessible-elements"></a>检查不可访问的元素

具有 CSS 属性的 `pointer-events: none` 元素对 **“检查** ”工具不可用。  在 [“检查演示](https://microsoftedge.github.io/Demos/devtools-inspect) ”页中，将鼠标悬停在该页上 `Overlay Button` ，你将看到父元素 (`div.wrapper`) 显示，而不是 `Overlay Button`显示。

![无法选择具有“指针事件：无”的 CSS 属性的元素。](images/inspect-tool-element-element-without-pointer-events.msft.png)

若要检查具有 CSS 属性的 `pointer-events: none`元素，请在将鼠标悬停在元素上时按 `Shift` 下。  页面布局区域上还有一个颜色覆盖，指示处于高级选择模式。

![在页面上选择元素时按 Shift 键可选择具有 CSS 样式属性为“pointer-events： none”的元素。](images/inspect-tool-with-shift.msft.png)


<!-- ====================================================================== -->
## <a name="selecting-the-element-and-terminating-inspect-mode"></a>选择元素并终止“检查”模式

单击呈现的页面中的元素时：

*  **“检查**”工具已停用。
*  突出显示了相应的 DOM 节点。
*  样 **式** 工具显示应用于元素的 CSS。

![单击呈现页面中的元素时，“样式”工具会显示应用于元素的样式。](images/inspect-tool-highlighted-styles.msft.png)


<!-- ====================================================================== -->
## <a name="persisting-the-inspect-tools-tooltip-and-grid-color-overlay"></a>保留检查工具的工具提示和网格颜色覆盖
<!-- keep sync'd:
* [Persisting the Inspect tool's tooltip and grid color overlay](../accessibility/navigation.md#persisting-the-inspect-tools-tooltip-and-grid-color-overlay) in _Navigate DevTools with assistive technology_ -->

使用 **“检查** ”工具并在呈现的网页周围移动时，可以保留当前的 **“检查** ”覆盖层。  在呈现的网页中四处移动时，按住`Ctrl`+`Alt` (Windows、Linux) 或`Ctrl`+`Option` (macOS) 。  将鼠标悬停在呈现网页的不同部分时，“ **检查** ”工具的现有工具提示和网格颜色覆盖仍会显示。


<!-- ====================================================================== -->
## <a name="temporarily-hiding-the-inspect-element-tooltip"></a>暂时隐藏“检查”元素工具提示

若要在将鼠标指针移到呈现的网页上时隐藏 **检查** 工具的覆盖，请按住 `Ctrl`。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用"检查"工具将鼠标悬停在网页上以检测辅助功能问题](../accessibility/test-inspect-tool.md)
* [使用 DevTools 进行辅助功能测试的概述](../accessibility/accessibility-testing-in-devtools.md) - 上述链接文章的超集长文。
