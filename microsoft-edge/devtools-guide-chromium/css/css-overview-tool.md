---
title: 使用 CSS 概述工具优化 CSS 样式
description: Microsoft Edge DevTools 中的 CSS 概述工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 09/07/2022
ms.openlocfilehash: db04394f35581d0c971869084bf7da243f3cc5a9
ms.sourcegitcommit: f8dd507a7559931578aa6e6a47ff74533012e5cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2022
ms.locfileid: "12746689"
---
# <a name="optimize-css-styles-with-the-css-overview-tool"></a>使用 CSS 概述工具优化 CSS 样式

**CSS 概述**工具捕获网页上使用的 CSS 代码的概述，并显示有关所使用的颜色、字体和媒体查询的报告。 该工具还标识潜在的颜色对比度问题和未使用的 CSS 声明问题。


<!-- ====================================================================== -->
## <a name="open-the-css-overview-tool"></a>打开 CSS 概述工具

若要打开 **CSS 概述** 工具，请执行以下操作：

1. 导航到 Microsoft Edge 中的 [TODO 列表演示应用](https://microsoftedge.github.io/Demos/demo-to-do/) ，或导航到自己的网页。

1. 按`F12`或`Shift``I`+`Ctrl`+ (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 打开 DevTools。

1. 在主工具栏中，单击 **“更多工具** ”，然后从列表中选择 **“CSS 概述** ”。

   ![Microsoft Edge 及其旁边的 TODO 列表演示应用和 DevTools，显示“更多工具”按钮中的工具列表](images/css-overview-tool-open.png)

1. **CSS 概述**工具随即打开并显示欢迎屏幕。

   ![Microsoft Edge，旁边有 TODO 列表演示应用和 DevTools，显示 CSS 概述欢迎屏幕](images/css-overview-tool-welcome.png)


<!-- ====================================================================== -->
## <a name="capture-a-css-overview-report"></a>捕获 CSS 概述报告

通过捕获新报表开始使用该工具。 单击 **“捕获”概述**，将显示概述报表。

![Microsoft Edge 及其旁边的 TODO 列表演示应用和 DevTools，显示该站点的 CSS 概述报告](images/css-overview-tool-report.png)

如果对网页进行更改并希望查看新报表，请单击 **“清除”概述** ，然后捕获新的概述。

![带有 TODO 列表演示应用的 Microsoft Edge 及其旁边的 DevTools 显示 CSS 概述报表，顶部显示“清除概述”按钮](images/css-overview-tool-clear.png)


<!-- ====================================================================== -->
## <a name="understand-the-report"></a>了解报表

概述报告包含几个部分中组织的信息：

* **摘要**：有关页面上的关键 CSS 规则、选择器和媒体查询的统计信息。
* **颜色**：页面上使用的颜色。
* **字体信息**：页面上的字体列表。
* **未使用的声明**：未使用的 CSS 声明列表。
* **媒体查询**：媒体查询列表。

若要查看上述部分，请滚动浏览报表，或使用内容边栏表。

![使用 TODO 列表演示应用和 DevTools 的 Microsoft Edge，在 CSS 概述报告中显示内容表和滚动条](images/css-overview-tool-scroll.png)

### <a name="summary"></a>摘要

摘 **要** 部分可用于快速概述 CSS 代码。 它提供外部和内联样式表的数量、CSS 规则的数量、选择器数及其各种类型以及媒体查询的数量。

这可用于评估给定网页上 CSS 代码库的卷和一致性。 例如，如果决定仅使用类选择器， **则“摘要** ”部分将快速检测其他类型的选择器（如 ID 或属性）。

### <a name="colors"></a>颜色

“ **颜色** ”部分列出了网页上使用的所有颜色，并按背景、文本、填充和边框类别对它们进行分组。

这对于发现使用多种类似颜色而非一种常用颜色的情况很有用。 CSS 自定义属性 (也称为 CSS 变量) 可用于避免在整个 CSS 文件中重复颜色，从而避免此问题。 详细了解 [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)) 上的 CSS 变量。

“ **颜色** ”部分还包含页面上的颜色对比度问题列表。 若要了解详细信息，请参阅 [具有颜色对比度问题的视图元素](#view-elements-with-color-contrast-issues)。

### <a name="font-info"></a>字体信息

“ **字体信息** ”部分列出了网页上使用的所有字体系列，并提供有关每个字体的大小、权重和行高的详细信息。

设计网页时，使用一致的版式设置有助于获得更美观的结果。 **字体信息**部分可用于检测何时使用了太多不同的字体或字体样式。

**“字体信息**”部分中的每个字体都包含其应用到的 DOM 元素的链接。 若要显示给定字体应用于的元素，请执行以下操作：

1. 在概述报表上，单击侧栏 **中的“字体”信息** ，滚动到报表的相关部分。

1. 查找字体系列以及你感兴趣的字体系列、大小、粗细或线高。

1. 单击其旁边 **的 X 匹配项** 链接以显示元素列表。

1. 将鼠标移到列表中的元素上，以在呈现的页面中突出显示它们。

   ![Microsoft Edge，带有 TODO 列表演示应用和 DevTools，显示给定字体大小的元素列表，以及悬停时突出显示的元素](images/css-overview-tool-font-element.png)

1. 单击一个元素以自动打开 **元素** 工具，其中选择了该元素。

   ![Microsoft Edge，其中包含 TODO 列表演示应用和 DevTools，其中显示了“元素”工具，并选择了正确的节点](images/css-overview-tool-elements-tool.png)

### <a name="unused-declarations"></a>未使用的声明

**“未使用的声明**”部分列出了一些对目标元素没有影响的 CSS 声明。

CSS 声明是键/值对，例如 `top: 42px`。 CSS 声明包含在 CSS 规则中，规则针对网页上的特定元素。 根据应用于元素的其他样式，CSS 声明可能没有任何效果。

例如， `top: 42px` 如果声明所面向的元素未定位 `position: absolute` ，或者 `position: relative` 例如，声明将没有任何效果。

这些情况可能很难找到， **并且“未使用的声明** ”部分通过列出其中的一些内容来提供帮助。 请注意，并非所有可能的情况都已列出。 目前，报告以下情况：

<!-- This part of the tool will get refactored when the Authoring Hints feature is completed.
So this list will need to be updated then. -->
* 当静`top``right``bottom`态定位元素上使用这些元素、属性或`left`属性时。
* 当内 `width` 联元素上使用这些或 `height` 属性时。
* 当属性 `vertical-align` 用于不是内联或表单元格的元素时。

### <a name="media-queries"></a>媒体查询

“ **媒体查询** ”部分列出了在网页上找到的 CSS 媒体查询。

CSS 媒体查询可用于应用特定样式，具体取决于媒体类型 (例如 `print` 或 `screen`) 或视区大小。 这通常用于使网页响应可用空间。

当 CSS 代码库变得复杂时，跟踪所有 CSS 媒体查询可能很困难。 “ **媒体查询** ”部分可简化此操作。 该部分中的每个媒体查询还包含一个指向其定义的 CSS 文件的链接。 若要显示该文件，请执行以下操作：

1. 在概述报表上，单击侧栏中的 **媒体查询** 以滚动到报表的相关部分。

1. 在报表中，找到你感兴趣的媒体查询。

1. 单击其旁边 **的 X 匹配项** 链接以显示相应的文件。

   ![使用 TODO 列表演示应用和 DevTools 的 Microsoft Edge，显示概述工具的媒体查询部分，以及包含给定媒体查询的文件列表](images/css-overview-tool-media-query.png)

1. 单击其中一个文件以自动打开打开该文件的 **“源** ”工具。

   ![Microsoft Edge 使用 TODO 列表演示应用和 DevTools，在右线显示“源”工具，其中打开了包含媒体查询的文件](images/css-overview-tool-sources-tool.png)


<!-- ====================================================================== -->
## <a name="view-elements-with-color-contrast-issues"></a>查看具有颜色对比度问题的元素

概述报表的 **“颜色** ”部分还可用于查找网页上的颜色对比度问题。 如果当前网页包含字体颜色与背景色之间的对比度不足的元素，则会显示 **“对比度问题** ”子部分。

查找颜色对比度问题：

1. 在 Microsoft Edge 中导航到存在颜色对比度问题的 [动物收容所](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 演示网站。 或者导航到自己的网站。

1. 按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 打开 DevTools。

1. 在主工具栏中，单击 **“更多工具** ”，然后从列表中选择 **“CSS 概述** ”。

1. 在 **CSS 概述** 工具中，单击 **“捕获概述** ”，然后单击概述报表边栏中的 **“颜色** ”。

1. 向下滚动到 **“对比度问题** ”子部分以查看所有问题。

   ![使用 TODO 列表演示应用和 DevTools 的 Microsoft Edge，在 CSS 概述报告中显示对比度问题列表](images/css-overview-tool-contrast-issues.png)

1. 若要查看具有特定颜色对比度问题的元素，请选择要修复的问题，然后单击 **“文本**”。 列出了相应的元素。

   ![使用 TODO 列表演示应用和 DevTools 的 Microsoft Edge，显示具有颜色对比度问题的元素列表](images/css-overview-tool-contrast-issues-elements.png)

1. 若要在 **Elements** 工具中打开相应的元素，请单击列表中的元素。
  
   ![Microsoft Edge，其中包含 TODO 列表演示应用和 DevTools，其中显示了 Elements 工具，并选择了颜色对比度问题元素](images/css-overview-tool-contrast-issues-elements-tool.png)

若要帮助解决对比度问题，请查看辅助功能测试 DevTools 功能的 [“文本对比](../accessibility/reference.md#text-contrast) 度”部分。
