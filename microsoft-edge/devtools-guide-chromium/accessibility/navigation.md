---
title: 使用辅助技术导航开发工具
description: 有关使用辅助技术（如屏幕阅读器）导航 Microsoft Edge 开发工具的指南。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 1cf2070f24c7733647edba0cbeb9d4b1bd181f18
ms.sourcegitcommit: 2e0ec25e3cfc01b58fdddd5f4ac270632cb9b962
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2022
ms.locfileid: "12348234"
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

本文可帮助主要依赖辅助技术的用户（如屏幕阅读器）使用 [Microsoft Edge DevTools](../../devtools-guide-chromium/index.md)。  DevTools 是内置于 Web 浏览器的一Microsoft Edge工具。

有关改善网页辅助功能的 DevTools 功能，请参阅辅助功能测试功能和使用 [DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)。[](reference.md)

本指南将指导你完成最可访问的工具和选项卡，并突出显示你可能会遇到的问题。

DevTools 分为一系列工具。   (在命令菜单中，工具**** 称为 _panels_。) 工具组织到主工具栏和箱工具栏上的 [ARIA](https://www.w3.org/TR/wai-aria-1.1/#tablist) 选项卡列表中。

以下是工具示例：

*  元素 **工具** 允许你 [查看和更改 DOM 节点](../dom/index.md#navigate-the-dom-tree-with-a-keyboard) 或 [CSS](../css/index.md)。

*  控制台 **工具** 允许你读取 JavaScript 日志和实时编辑对象。  有关详细信息，请参阅控制台 [概述](../console/index.md)。

在每个工具中，都有一组或多组选项卡。  例如， **Elements** 工具包含一组选项卡，包括 **Styles**、 **Event Listeners** 和 **Accessibility**。


<!-- ====================================================================== -->
## <a name="keyboard-shortcuts"></a>键盘快捷方式

有关 DevTools 的默认键盘快捷方式，请参阅 [键盘快捷方式](../shortcuts/index.md)。  请务必在浏览不同的工具时为它添加书签并引用回它。


<!-- ====================================================================== -->
## <a name="open-devtools"></a>打开开发工具

若要开始，请参阅 [Open DevTools](../open/index.md)。  开发工具有多种打开方式，可以通过键盘快捷方式，也可通过菜单项将其打开。


<!-- ====================================================================== -->
## <a name="navigate-between-tools"></a>在工具之间导航

可以使用键盘导航键或命令菜单在工具间移动。

### <a name="navigate-by-keyboard"></a>使用键盘导航

*  打开 DevTools 后，按 (Windows、Linux) +`]` `Command`或 (macOS) 将焦点移到主工具栏上的下一个工具。`Control`+`]`
*  按 `Control`+`[` (Windows、Linux) 或 `Command`+`[` (macOS) 将焦点移到主工具栏上的上一个工具。
*  按 `Tab` 或 `Shift`+`Tab` 重复按，直到焦点移到主工具栏或箱工具栏的选项卡，然后使用箭头键在工具之间移动。

#### <a name="known-issues"></a>已知问题

*  一旦选择控制台**和性能**工具，某些**** 工具（如控制台和性能工具）可能会将焦点移到工具的内容区域中。  这可能使得使用箭头键导航更加困难。

*  选定工具的名称将公布，但仅在宣布该工具中重点内容后公布。  此通知序列可能会轻松错过工具的名称。

### <a name="navigate-by-command-menu"></a>按命令菜单导航

若要选择特定工具，请使用命令 [菜单](../command-menu/index.md)。  在命令菜单中，工具称为面板_或__箱_项目。

1. 打开 DevTools `Control``Shift``P`++后，按 (Windows、Linux) `Command``Shift`++`P` 或 (macOS) 打开**命令菜单**。

   命令 **菜单** 是一个模糊搜索自动完成组合框。

1. 键入面板名称 (工具) ， `Down Arrow` 然后使用键盘上的 导航到正确的选项。

1. 按 `Enter` 以运行命令。


若要打开 **"元素"** 工具，请执行以下操作：

1. 打开“**命令菜单**”。

1. 开始键入 ， `elements`选择"显示 **>"命令，** 然后按 `Enter`。

这样打开工具会将焦点放在工具的内容区域中。  对于 Elements **工具，焦点** 将移动到 **DOM 树中**。


<!-- ====================================================================== -->
## <a name="the-elements-tool"></a>元素工具

### <a name="inspect-an-element-on-the-page"></a>检查页面上的元素

1. 使用屏幕阅读器中的光标转到要检查的元素。

1. 右键单击元素，然后选择"检查 **"** 选项。  这将 [打开 Elements 工具并聚焦 DOM 树中的 元素](../dom/index.md#view-dom-nodes)。

“**DOM 树**”已布局为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)。  有关示例，请参阅 [使用 **键盘导航 DOM** 树](../dom/index.md#navigate-the-dom-tree-with-a-keyboard)。

### <a name="copy-the-code-for-an-element-in-the-dom-tree"></a>复制 DOM 树中元素的代码

1. 右键单击 **DOM 树中的节点**。

1. 展开“**复制**”选项。

1. 选择 **"复制 outerHTML"**。

#### <a name="known-issues"></a>已知问题

*  **复制 outerHTML** 通常不会选择当前节点，而是选择父节点。  但是，元素的内容仍应处于复制的 中 `outerHTML`。

### <a name="modify-the-attributes-of-an-element-in-the-dom-tree"></a>修改 DOM 树中元素的属性

*  焦点在 **DOM 树中的节点上时**，按 `Enter` 使其可编辑。

*  按 `Tab` 键在属性值之间移动。  当你听到"空格"时，你将位于空文本输入内，可以键入新的属性值。

*  按 `Control`+`Enter` (Windows、Linux) 或 `Command`+`Enter` (macOS) 接受更改并听到元素的全部内容。

#### <a name="known-issues"></a>已知问题

*  当你键入文本输入时，你未收到任何反馈。  如果你输入了拼写错误并使用箭头键来浏览你的输入，你同样不会收到反馈。  检查工作最简单的方法是接受更改，然后收听要播报的整个元素。

### <a name="edit-the-html-of-an-element-in-the-dom-tree"></a>编辑 DOM 树中元素的 HTML

*  焦点在 **DOM 树中的节点上时**，按 `Enter` 使其可编辑。

*  按 `Tab` 键在属性值之间移动。  当你听到 元素的名称 `h2`时，例如 ，你位于文本输入内部，并且可以更改 元素的类型。

*  按 `Control`+`Enter` (Windows、Linux) 或 `Command`+`Enter` (macOS) 接受更改。

例如，当你`h3`+`Control``Enter`键入然后按 (Windows、Linux) +`Command``Enter` 或 (macOS) `h3` 时，元素的起始标记和结束标记会更改。


<!-- ====================================================================== -->
## <a name="tabs-in-the-elements-tool"></a>元素工具中的选项卡

**元素工具**包含用于检查应用于元素的 CSS 或辅助功能树中相关位置等内容的其他选项卡。

*  焦点在 **DOM 树中的节点上时**，按直到 `Tab` 您听到已选择 **样式** 窗格。

*  按 `Right Arrow` 以浏览其他可用的选项卡。

**DOM 树**将具有属性`href`的元素转换为`Tab`可聚焦链接，因此您可能需要多次按以到达 **"样式"** 窗格。

### <a name="known-issues"></a>已知问题

**DOM 断点**和**属性**选项卡不可通过键盘访问。


### <a name="styles-pane"></a>样式窗格

" **样式** "窗格包含用于筛选样式、切换元素 (如 [：active](https://developer.mozilla.org/docs/Web/CSS/:active) 和 [：focus](https://developer.mozilla.org/docs/Web/CSS/:focus)) 、切换类以及添加新类的控件。  此外，还有一个强大的样式检查工具，可用于浏览和修改当前应用于 DOM 树中具有焦点的元素 **的样式**。

了解“**样式**”窗格的关键概念是它只显示“**DOM 树**”窗格中当前选中节点的样式。  例如，假设您已完成对节点 `<header>` 样式的检查，现在您想要查看节点的样式 `<footer>` 。  若要执行该操作，首先需要在“**DOM 树**”中选择 `<footer>` 节点。

您可能会发现，使用"检查"工作流[](#inspect-an-element-on-the-page)检查节点 (（例如页脚) 中用于聚焦 **DOM** 树）内的链接，然后使用键盘导航到您感兴趣的精确节点会更快。`footer`

#### <a name="navigate-the-styles-pane"></a>导航“样式”窗格

由于所有样式工具都以某种方式连接到“**样式**”窗格中，因此首先掌握此工具的使用具有重要意义。

*  焦点在" **样式"** 窗格上时，按 `Tab` 以将焦点移到内部并浏览内容。

*  按 `Tab` 直到第一个样式变为活动状态。  如果你使用的是屏幕阅读器，则第一个样式将宣布为 `element.style {}`。

*  按 `Down Arrow` 以特定顺序导航样式列表。  屏幕阅读器将读出每个样式，播报以 CSS 文件名开头，再依次报出样式所在的行号以及样式的名称。  例如，`main.css:233 .card__img {}`。

*  按 `Enter` 以更详细地检查样式。  焦点从样式名称的可编辑版本开始。

*  按 `Tab` 在每个 CSS 属性的可编辑版本和相应的值之间移动。  每个样式块的末尾都是一个空白的可编辑文本字段，可用于添加其他 CSS 属性。

*  你可以继续按以 `Tab` 在 `Escape` 样式列表中移动，或者按退出模式并返回通过箭头键导航。

有关其他快捷方式，请参阅 [样式窗格键盘参考](../shortcuts/index.md#styles-pane-keyboard-shortcuts)。

##### <a name="known-issues"></a>已知问题

*  如果使用" **可编辑的筛选器** "文本字段，则不能导航样式列表。

#### <a name="toggle-element-state"></a>切换元素状态

若要切换元素的状态，如 `:active` 或 `:focus`：

1. 转到" **样式"** 窗格并按， `Tab` 直到 **"切换元素状态"** 按钮具有焦点。

1. 按 `Enter` 展开元素状态的集合。  元素状态将显示为一组复选框。

1. 按 `Tab` ，直到第一个状态 具有 `:active`焦点。

1. 按 `Spacebar` 以启用它。  如果 DOM 树中当前选定的元素具有 `:active` 样式，则现在应用该样式。

1. 按住 `Tab` 以浏览所有可用状态。

#### <a name="add-an-existing-class"></a>添加现有类别

“**元素类别**”按钮与“**切换元素状态**”按钮相邻。  若要将焦点移到它，请按 ， `Tab` 然后按 `Enter`。  焦点移到标记为添加新类的 **编辑文本字段中**。

“**元素类别**”按钮主要用于向元素添加现有类别。  例如，如果您的样式`.clearfix``.` `Down Arrow` `.clearfix`表包含一个名为 的帮助程序类，您可以在编辑文本字段内按以显示类的建议列表，并使用 查找建议。  或者，自己键入类名称并按 `Enter` 以应用它。

#### <a name="add-a-new-style-rule"></a>添加新的样式规则

“**新样式规则**”按钮与“**元素类别**”按钮相邻。  若要将焦点移到它，请按 ， `Tab` 然后按 `Enter`。  焦点将移到样式检查器内的可编辑文本字段中。  该字段的初始文本内容是在“**DOM 树**”中所选元素的标记名称。
您可以在此字段中键入任何想要键入的类名，然后按 `Tab` 以为其分配 CSS 属性。


### <a name="computed-tab"></a>已计算选项卡

焦点在" **计算"** 选项卡上时，按 `Tab` 以将焦点移到内部并浏览内容。  在“**已计算**”选项卡中，有一些控件用于浏览哪些 CSS 属性实际上是按特定性顺序应用于元素的。

<!--todo: add Computed tab section when available  -->

#### <a name="explore-all-computed-styles"></a>浏览所有已计算的样式

按 `Tab` 直到您到达计算样式的集合。  计算样式作为 [ARIA 树呈现](https://www.w3.org/TR/wai-aria-1.1/#tree)。  展开列表框会显示哪些 CSS 选择器正在应用已计算样式。  这些选择器按特定性进行整理。  屏幕阅读器将播报已计算的值、当前哪个 CSS 选择器正在匹配、包含该选择器的样式表文件名以及选择器行号。

**已知问题**

*  如果使用" **筛选器"** 文本字段，则无法再检查样式。


### <a name="event-listeners-tab"></a>"事件侦听器"选项卡

若要检查应用于元素的事件侦听器，请选择"元素"工具，然后选择"**** 事件侦听器"选项卡 ("**** 样式"选项卡) 。****

当焦点位于" **样式"选项卡** 上时，按 `Right Arrow` 以导航到" **事件侦听器"** 选项卡。

#### <a name="explore-event-listeners"></a>浏览事件侦听器

事件侦听器将显示为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)。  可以使用箭头键导航它们。  屏幕阅读器将播报事件侦听器所附加到的 DOM 对象名称，以及定义事件侦听器的文件名和行号。


### <a name="accessibility-tab"></a>"辅助功能"选项卡

在" `Tab` 元素"工具的"辅助功能 **"** 选项卡内选择要四 **处移动的** 键。

" **辅助功能"** 选项卡位于"样式" **选项卡** 附近。在"辅助功能"选项卡上，有一些控件用于探索辅助功能树、应用于元素的 ARIA 属性以及计算的辅助功能属性。  请参阅 [使用辅助功能选项卡测试辅助功能](accessibility-tab.md)。

#### <a name="accessibility-tree"></a>辅助功能树

**辅助功能树** 显示为 [ARIA 树](https://www.w3.org/TR/wai-aria-1.1/#tree)，其中每个 `treeitem` 对应 DOM 中的一个元素。  树将播报选定节点的已计算角色。  通用元素（如 `div` 和 `span`）将在树中播报为 “GenericContainer”。  使用箭头键来遍历树并浏览父子级关系。

**已知问题**

*  对于 macOS 屏幕阅读器（如 VoiceOver****）来说，"辅助功能"选项卡Microsoft Edge [ARIA](https://www.w3.org/TR/wai-aria-1.1/#tree) 树的类型可能未正确公开。  订阅 [Chromium 问题 #868480](https://bugs.chromium.org/p/chromium/issues/detail?id=868480) 以获取有关此问题进展的通知。
*  每个 **ARIA 属性** 和 **计算属性** 部分都标记为 [ARIA](https://www.w3.org/TR/wai-aria-1.1/#tree) 树，但每个部分当前没有焦点管理，并且不能通过键盘操作。


<!-- ====================================================================== -->
## <a name="the-lighthouse-tool"></a>Lighthouse 工具

**Lighthouse** 对网站运行一系列测试，以检查与性能、辅助功能、SEO 和大量其他类别相关的常见问题。

### <a name="configure-and-generate-a-report"></a>配置和生成报告

1. 在 DevTools 中首次打开 **Lighthouse** 工具时，焦点将放置在"生成报告 **"按钮** 上。  默认情况下，表单配置为在模拟 3G 连接上使用移动模拟来运行每个类别的报告。

1. 若要更改报告设置，请使用 `Shift`+`Tab` 将焦点放在 **"Lighthouse**"设置上，或导航回"浏览"模式。

1. 准备好运行报告后，导航回"生成报告 **"** 按钮，然后按 `Enter`。

1. 焦点将移动到使用具有“**取消**”按钮的模式窗口，该按钮允许退出审核。  审核运行并多次刷新页面时，可能会听到一系列有声提示。

#### <a name="known-issues"></a>已知问题

*  配置表单的不同部分当前没有使用 元素进行 `fieldset` 标记。  在浏览模式下导航它们可能会更方便地了解与每个部分关联的控件。
*  审核结束运行后，不会发布任何有声提示或实时区域公告。  通常，审核需要大约 30 秒，在此之后，你将能够导航到结果。  使用浏览模式可能是获取结果的最简单方法。

### <a name="navigate-the-lighthouse-report"></a>导航"浅楼"报表

Lighthouse 报告分为与每个审核类别对应的部分。  报告打开时显示每个类别的分数列表。  这些分数也是可用于跳到相关部分的链接。  每个章节内有可展开的 `details`元素，这些元素包含与审核通过或失败有关的信息。  默认情况下，仅显示失败的审核。  每节以最后一个 `details` 元素结尾，该元素包含所有通过的审核。

若要运行新审核，请使用 `Shift`+`Tab` 退出报告并选择"生成 **报告"** 按钮。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [键盘快捷方式](../shortcuts/index.md)
* [自定义键盘快捷方式](../customize/shortcuts.md)
* [在“命令”菜单中运行命令](../command-menu/index.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/accessibility/navigation) 由 [Rob Dodson](https://developers.google.com/web/resources/contributors#rob-dodson) (Contributor、Google WebFundamentals) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
