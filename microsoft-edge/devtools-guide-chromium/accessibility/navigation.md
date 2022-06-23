---
title: 使用辅助技术导航开发工具
description: 有关使用辅助技术（如屏幕阅读器）导航 Microsoft Edge 开发工具的指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 7da2e64c48d11dbdc3ce0ef26e1782d290db5930
ms.sourcegitcommit: 92a0cd0a86cc8ef49e4f90ea660d43106a4d19b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2022
ms.locfileid: "12610273"
---
<!-- Copyright Rob Dodson

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="navigate-devtools-with-assistive-technology"></a>使用辅助技术导航开发工具

本文通过键盘和屏幕阅读器等辅助技术帮助你使用 DevTools。  本指南将引导你完成最易于访问的工具和选项卡，并突出显示可能遇到的问题。

<!-- DevTools is a suite of web developer tools built into the Microsoft Edge browser. -->

有关与改进网页辅助功能相关的 DevTools 功能，请参阅 [辅助功能测试功能](reference.md) 和 [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)。


### <a name="tabbed-tool-panels-containing-tabs-and-pages"></a>包含选项卡和页面的 Tabbed 工具面板

有关选项卡、工具和面板的术语，请参阅 _“DevTools 概述_”中[包含选项卡和页面的 Tabbed 工具面板](../overview.md#tabbed-tool-panels-containing-tabs-and-pages)。

从技术上讲，选项卡是 [ARIA 选项卡列表](https://www.w3.org/TR/wai-aria-1.1/#tablist)。


<!-- The following are examples of tools:

*  The **Elements** tool lets you [view and change DOM nodes](../dom/index.md#navigate-the-dom-tree-with-a-keyboard) or [CSS](../css/index.md).

*  The **Console** tool lets you read JavaScript logs and live-edit objects.  For more information, see [Console overview](../console/index.md). -->


<!-- ====================================================================== -->
## <a name="keyboard-shortcuts"></a>键盘快捷方式

有关 DevTools 的默认键盘快捷方式，请参阅 [键盘快捷方式](../shortcuts/index.md)。  在浏览不同的工具时，请务必对其进行书签并参考。


<!-- ====================================================================== -->
## <a name="open-devtools"></a>打开开发工具
<!-- keep sync'd:
[Open DevTools](../overview.md#open-devtools) in _Overview of DevTools_
[Open DevTools](accessibility/navigation.md#open-devtools) in _Navigate DevTools with assistive technology_
-->

在Microsoft Edge中，可以通过以下任一方式使用鼠标或键盘打开 DevTools。  打开哪个工具取决于打开 DevTools 的方式。

**主要方式：**

| 操作 | 生成的工具 |
|---|---|
| 右键单击网页上的任何项，然后选择 **“检查**”。 | **“元素**”工具，其中扩展了 DOM 树以显示右键单击的页面元素。 |
| 按`Ctrl`+`Shift`+`I`（Windows、Linux）或 `Command`+`Option`+`I` （macOS）。| 以前使用的工具或 **欢迎** 工具。 |
| 按 `F12`。 | 以前使用的工具或 **欢迎** 工具。 |

**其他方法：**

| 操作 | 生成的工具 |
|---|---|
| 在Microsoft Edge工具栏上，**选择设置和更多** (![“设置和更多”图标。](media/edge-settings-and-more-icon.png)) >**更多工具** >  **开发人员工具**。 | 以前使用的工具或 **欢迎** 工具。 |
| 按`Ctrl`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。 | **控制台**工具。 |
| 按`Ctrl`+`Shift`+`C`（Windows、Linux）或 `Command`+`Option`+`C` （macOS）。 | **“元素**”工具，其中扩展了 DOM 树以显示元素`<body>`。 |
| 按 `Shift`+`F10` 下以打开右键单击菜单。  若要选择 **“检查**”命令，请按下，然后`Enter`按`Up Arrow`。 | **“元素**”工具，其中扩展了 DOM 树以显示元素`<html>`。 |
| 按 `Tab` 下并 `Shift`+`Tab` 将焦点放在页面元素上。  然后按 `Shift`+`F10` 下以打开右键单击菜单。  若要选择 **“检查**”命令，请按下，然后`Enter`按`Up Arrow`。 | **“元素**”工具，其中扩展了 DOM 树以显示重点页面元素。 |

<!-- /keep sync'd -->


<!-- ====================================================================== -->
## <a name="navigate-between-tools"></a>在工具之间导航

可以通过使用键盘导航键或使用命令菜单在工具之间移动。

### <a name="navigate-by-keyboard"></a>使用键盘导航

*  打开 DevTools 后，按 `Ctrl`+`]` (Windows、Linux) 或`Command`+`]` (macOS) 将焦点移到主工具栏上的下一个工具。
*  按`Ctrl`+`[` (Windows、Linux) 或`Command`+`[` (macOS) 将焦点移到主工具栏上的上一个工具。
*  按 `Tab` 或 `Shift`+`Tab` 重复，直到焦点移动到主工具栏或抽屉工具栏的选项卡，然后使用箭头键在工具之间移动。

#### <a name="known-issues"></a>已知问题

*  一旦选择该工具，某些工具（如 **控制台** 和 **性能** 工具）可能会将焦点移动到工具的内容区域。  这可能使得使用箭头键导航更加困难。

*  将公布所选工具的名称，但仅在宣布工具中的重点内容之后才会公布。  这一系列公告可能会很容易错过该工具的名称。

### <a name="navigate-by-command-menu"></a>按命令菜单导航

若要选择特定工具，请使用 [命令菜单](../command-menu/index.md)。  在命令菜单中，工具称为 _面板_ 或 _抽屉_ 项。

1. 打开 DevTools 后，按 `Ctrl``Shift``P`++ (Windows、Linux) 或`Command``Shift`++`P` (macOS) 打开**命令菜单**。

   **命令菜单**是模糊搜索自动完成组合框。

1. 键入面板 (工具) 的名称，然后使用 `Down Arrow` 键盘导航到正确的选项。

1. 按 `Enter` 下以运行命令。


若要打开 **Elements** 工具，请执行以下操作：

1. 打开“**命令菜单**”。

1. "开始"菜单键入`elements`，选择 **“面板>显示元素**”命令，然后按。`Enter`

以这种方式打开工具会将焦点放在工具的内容区域中。  就 **元素** 工具而言，焦点将移到 **DOM 树**中。


<!-- ====================================================================== -->
## <a name="the-elements-tool"></a>Elements 工具

### <a name="inspect-an-element-on-the-page"></a>检查页面上的元素

1. 使用屏幕阅读器中的光标转到要检查的元素。

1. 右键单击该元素，然后选择“ **检查** ”选项。  这将 [打开元素工具，并聚焦 DOM 树中的元素](../dom/index.md#view-dom-nodes)。

“**DOM 树**”已布局为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)。  有关示例，请参阅[使用键盘导航 **DOM 树**](../dom/index.md#navigate-the-dom-tree-with-a-keyboard)。


### <a name="copy-the-code-for-an-element-in-the-dom-tree"></a>复制 DOM 树中元素的代码

1. 右键单击 **DOM 树**中的节点。

1. 展开“**复制**”选项。

1. 选择 **“复制外部HTML**”。

#### <a name="known-issues"></a>已知问题

*  **复制 outerHTML** 通常不会选择当前节点，而是选择父节点。  但是，元素的内容仍应在复制 `outerHTML`中。


### <a name="modify-the-attributes-of-an-element-in-the-dom-tree"></a>修改 DOM 树中元素的属性

*  重点关注 **DOM 树**中的节点时，请按 `Enter` 它使其可编辑。

*  按 `Tab` 下以在属性值之间移动。  听到“空格”时，你位于空文本输入中，并且可以键入新的属性值。

*  按`Ctrl`+`Enter` (Windows、Linux) 或`Command`+`Enter` (macOS) 接受更改并听到元素的整个内容。

#### <a name="known-issues"></a>已知问题

*  键入文本输入时，不会收到任何反馈。  如果创建拼写错误并使用箭头键浏览输入，则也不会收到反馈。  检查工作最简单的方法是接受更改，然后收听要播报的整个元素。


### <a name="edit-the-html-of-an-element-in-the-dom-tree"></a>编辑 DOM 树中元素的 HTML

*  重点关注 **DOM 树**中的节点时，请按 `Enter` 它使其可编辑。

*  按 `Tab` 下以在属性值之间移动。  例如，当你听到元素的名称时， `h2`你位于文本输入的内部，并且可以更改元素的类型。

*  按`Ctrl`+`Enter` (Windows、Linux) 或`Command`+`Enter` (macOS) 接受更改。

例如，键入 **h3**，然后按 `Ctrl`+`Enter` (Windows、Linux) 或`Enter``Command`+ (macOS) 时，元素的`h3`起始标记和结束标记会更改。


<!-- ====================================================================== -->
## <a name="tabs-in-the-elements-tool"></a>元素工具中的选项卡

**“元素**”工具包含用于检查应用到元素或辅助功能树中相关位置的 CSS 之类的内容的其他选项卡。

*  将焦点放在 **DOM 树**中的节点上，按 `Tab` 到听到已选择 **“样式** ”窗格为止。

*  按 `Right Arrow` 下以浏览其他可用选项卡。

**DOM 树**将具有`href`属性的元素转换为可聚焦链接，因此可能需要多次按`Tab`下才能访问“**样式**”窗格。


### <a name="known-issues"></a>已知问题

**DOM 断点**和**属性**选项卡无法通过键盘访问。


### <a name="styles-pane"></a>样式窗格

“ **样式”** 窗格包含用于筛选样式、切换元素状态 (（如 [：active](https://developer.mozilla.org/docs/Web/CSS/:active) 和 [：focus](https://developer.mozilla.org/docs/Web/CSS/:focus)) 、切换类和添加新类）的控件。  还有一个功能强大的样式检查工具，用于探索和修改当前应用于 **DOM 树**中具有焦点的元素的样式。

了解“ **样式** ”窗格的关键概念是，它只显示 **DOM 树**中当前选定节点的样式。  例如，假设你已完成对节点样式的 `<header>` 检查，现在你想要查看节点的 `<footer>` 样式。  若要执行该操作，首先需要在“**DOM 树**”中选择 `<footer>` 节点。

可以更快地使用 [“检查](#inspect-an-element-on-the-page) ”工作流来检查节点 (通常附近的 `footer` 节点，例如页脚) 中的链接，该链接聚焦 **于 DOM 树**，然后使用键盘导航到感兴趣的确切节点。

#### <a name="navigate-the-styles-pane"></a>导航“样式”窗格

由于所有样式工具都以某种方式连接到“**样式**”窗格中，因此首先掌握此工具的使用具有重要意义。

*  在“ **样式** ”窗格上，按 `Tab` 下将焦点移动到内部并浏览内容。

*  按 `Tab` 到第一个样式变为活动状态。  如果使用的是屏幕阅读器，则会将此第一种样式宣布为 `element.style {}`。

*  按 `Down Arrow` 以下方式按特定方式导航样式列表。  屏幕阅读器将读出每个样式，播报以 CSS 文件名开头，再依次报出样式所在的行号以及样式的名称。  例如，`main.css:233 .card__img {}`。

*  按 `Enter` 下以更详细地检查样式。  焦点从样式名称的可编辑版本开始。

*  按 `Tab` 下以在每个 CSS 属性的可编辑版本与相应值之间移动。  每个样式块的末尾是一个空白的可编辑文本字段，可用于添加其他 CSS 属性。

*  可以继续按 `Tab` 下以在样式列表中移动，或按 `Escape` 下退出模式，然后返回到按箭头键导航。

有关其他快捷方式，请参阅 [“样式”窗格键盘参考](../shortcuts/index.md#styles-pane-keyboard-shortcuts)。

##### <a name="known-issues"></a>已知问题

*  如果使用“ **可编辑的筛选器** ”文本字段，则无法导航样式列表。

#### <a name="toggle-element-state"></a>切换元素状态

若要切换元素的状态，如 `:active` 或 `:focus`：

1. 转到“ **样式”** 窗格，按 `Tab` 到 **“切换元素状态** ”按钮具有焦点。

1. 按 `Enter` 下以显示 **Force 元素状态** 部分，其中包含复选框。

1. 按 `Tab` 到第一个状态， `:active`有焦点。

1. 按 `Spacebar` 下以启用它。  如果 DOM 树中当前选定的元素具有 `:active` 样式，则现在应用该样式。

1. 按住 `Tab` 以浏览所有可用状态。

#### <a name="add-an-existing-class"></a>添加现有类别

**“元素类**”按钮位于 **“切换元素状态**”按钮旁边。  若要将焦点移动到 **“元素类** ”按钮，请按 `Tab` 下，然后按下 `Enter`。  焦点移动到标记为 **“添加新类**”的编辑文本字段中。

“**元素类别**”按钮主要用于向元素添加现有类别。  例如，如果样式表包含名为“帮助程序” `.clearfix`类，则可以在编辑文本字段内按 `.` 下以显示类的建议列表，并使用该 `Down Arrow` 列表查找 `.clearfix` 建议。  或者自己键入类名，然后按 `Enter` 下应用。

#### <a name="add-a-new-style-rule"></a>添加新的样式规则

“**新样式规则**”按钮与“**元素类别**”按钮相邻。  若要将焦点移动到它，请按 `Tab` 下，然后按下 `Enter`。  焦点将移到样式检查器内的可编辑文本字段中。  该字段的初始文本内容是在“**DOM 树**”中所选元素的标记名称。
可以在此字段中键入所需的任何类名，然后按下 `Tab` 此字段为其分配 CSS 属性。


### <a name="computed-tab"></a>已计算选项卡

焦点位于 **“计算** ”选项卡上，按 `Tab` 下将焦点移动到内部并浏览内容。  在“**已计算**”选项卡中，有一些控件用于浏览哪些 CSS 属性实际上是按特定性顺序应用于元素的。

<!--todo: add Computed tab section when available  -->

#### <a name="explore-all-computed-styles"></a>浏览所有已计算的样式

按 `Tab` ，直到到达计算样式的集合。  计算样式显示为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)。  展开列表框会显示哪些 CSS 选择器正在应用已计算样式。  这些选择器按特定性进行整理。  屏幕阅读器将播报已计算的值、当前哪个 CSS 选择器正在匹配、包含该选择器的样式表文件名以及选择器行号。

**已知问题**

*  如果使用 **“筛选器** ”文本字段，则无法再检查样式。


### <a name="event-listeners-tab"></a>“事件侦听器”选项卡

若要检查应用于元素的事件侦听器，请选择 **“元素”** 工具，然后选择“ **事件侦听器** ”选项卡 (“ **样式”** 选项卡) 分组。

当焦点位于“ **样式”** 选项卡上时，按 `Right Arrow` 下以导航到 **“事件侦听器”** 选项卡。

#### <a name="explore-event-listeners"></a>浏览事件侦听器

事件侦听器将显示为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)。  可以使用箭头键来导航它们。  屏幕阅读器将播报事件侦听器所附加到的 DOM 对象名称，以及定义事件侦听器的文件名和行号。


### <a name="accessibility-tab"></a>"辅助功能"选项卡

选择要在`Tab`**“元素**”工具的 **“辅助功能**”选项卡内移动的键。

“ **辅助功能** ”选项卡靠近“ **样式”** 选项卡。在“辅助功能”选项卡上，有用于浏览辅助功能树的控件、应用于元素的 ARIA 属性以及计算的辅助功能属性。  [使用“辅助功能”选项卡查看测试辅助功能](accessibility-tab.md)。

#### <a name="accessibility-tree"></a>辅助功能树

**辅助功能树** 显示为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)，其中每个 `treeitem` 对应 DOM 中的一个元素。  树将播报选定节点的已计算角色。  通用元素（如 `div` 和 `span`）将在树中播报为 “GenericContainer”。  使用箭头键来遍历树并浏览父子级关系。

**已知问题**

*  对于 VoiceOver 等macOS屏幕阅读器，**辅助功能**选项卡使用的 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)类型可能无法在Microsoft Edge中正确公开。  订阅 [Chromium 问题 #868480](https://bugs.chromium.org/p/chromium/issues/detail?id=868480) 以获取有关此问题进展的通知。
*  每个 **ARIA 属性** 和 **计算属性** 部分都标记为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)，但每个节当前没有焦点管理，也不具有键盘操作性。


<!-- ====================================================================== -->
## <a name="persisting-the-inspect-tools-tooltip-and-grid-color-overlay"></a>保留检查工具的工具提示和网格颜色覆盖
<!-- keep sync'd:
* [Persisting the Inspect tool's tooltip and grid color overlay](../css/inspect.md#persisting-the-inspect-tools-tooltip-and-grid-color-overlay) in _Analyze pages using the Inspect tool_ -->

单击 **“检查** ”工具按钮并在呈现的网页中四处移动时，“检查”工具提示会更改。  若要保持显示当前工具提示和网格颜色覆盖，请在呈现的网页中四处移动时按住 `Ctrl`+`Alt` (Windows、Linux) 或`Ctrl`+`Option` (macOS) 。

使用屏幕放大镜或其他辅助技术时，此技术很有用。  如果未使“检查”工具的工具提示保持不变，则使用“ **检查”工具** (![“检查”工具按钮时，悬停覆盖层会不断更改。](../media/inspect-tool-icon-light-theme.png)) 。

请 [参阅使用“检查”工具的“分析”页面](../css/inspect.md)。


<!-- ====================================================================== -->
## <a name="the-lighthouse-tool"></a>Lighthouse 工具

**Lighthouse** 针对某个站点运行一系列测试，以检查与性能、辅助功能、SEO 和其他一些类别相关的常见问题。

### <a name="configure-and-generate-a-report"></a>配置并生成报表

1. 当 **Lighthouse** 工具首次在 DevTools 中打开时，焦点将放置在“ **生成报表** ”按钮上。  默认情况下，窗体配置为在模拟的 3G 连接上使用移动仿真为每个类别运行报表。

1. 若要更改报表设置，请使用 `Shift`+`Tab` 将焦点放在 **Lighthouse 设置**上，或在“浏览”模式下导航回来。

1. 准备好运行报表后，导航回“ **生成报表** ”按钮，然后按下 `Enter`。

1. 焦点将移动到使用具有“**取消**”按钮的模式窗口，该按钮允许退出审核。  审核运行并多次刷新页面时，可能会听到一系列有声提示。

#### <a name="known-issues"></a>已知问题

*  配置窗体的不同部分当前未使用 `fieldset` 元素进行标记。  在浏览模式下导航它们可能会更方便地了解与每个部分关联的控件。
*  审核结束运行后，不会发布任何有声提示或实时区域公告。  通常，审核大约需要 30 秒，之后应能够导航到结果。  使用浏览模式可能是获取结果的最简单方法。

### <a name="navigate-the-lighthouse-report"></a>导航 Lighthouse 报表

Lighthouse 报表分为与每个审核类别对应的部分。  报告打开时显示每个类别的分数列表。  这些分数也是可用于跳到相关部分的链接。  每个章节内有可展开的 `details`元素，这些元素包含与审核通过或失败有关的信息。  默认情况下，仅显示失败的审核。  每节以最后一个 `details` 元素结尾，该元素包含所有通过的审核。

若要运行新的审核，请使用 `Shift`+`Tab` 它退出报表并选择 **“生成报表** ”按钮。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [键盘快捷方式](../shortcuts/index.md)
* [自定义键盘快捷方式](../customize/shortcuts.md)
* [在“命令”菜单中运行命令](../command-menu/index.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在此](https://developer.chrome.com/docs/devtools/accessibility/navigation/) 处找到，由 [Rob Dodson](https://developers.google.com/web/resources/contributors#rob-dodson) (参与者、Google WebFundamentals) 创作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
