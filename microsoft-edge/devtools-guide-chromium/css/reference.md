---
title: CSS 功能参考
description: 在 DevTools 中查看和更改 CSS Microsoft Edge的功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/29/2021
ms.openlocfilehash: 309c675069b704c3843ef149d062479126d7e5e4
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319834"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="css-features-reference"></a>CSS 功能参考

在以下与查看和更改 CSS 相关的 Microsoft Edge DevTools 功能综合参考中发现新的工作流。

若要了解基础知识，请参阅查看和 [更改 CSS 入门](../css/index.md)。


<!-- ====================================================================== -->
## <a name="select-an-element"></a>选择元素

DevTools **元素** 工具可用于一次查看或更改一个元素的 CSS。  所选元素在 **“DOM 树”** 上突出显示。  元素的样式显示在 **“样式”** 窗格中。  有关教程，请参阅[查看元素 的 CSS。](../css/index.md#view-the-css-for-an-element)

下图中，**“DOM 树”** 中突出显示的 `h1` 元素就是所选元素。  在右侧的样式窗格中显示了元素的 **“样式”**。  在左侧，该元素在视口中突出显示，但仅仅是因为鼠标当前正在 DOM 树中悬停在 **该元素上**：

:::image type="content" source="../media/css-elements-styles-h1.msft.png" alt-text="选定元素的示例。" lightbox="../media/css-elements-styles-h1.msft.png":::

选择元素的方法有很多：

*   在呈现的网页中，右键单击页面元素，然后单击"检查 **"。**

*   在 DevTools 中，单击选择元素** (** 选择元素) 或按 ![ ](../media/select-an-element-icon.msft.png) `Control` + `Shift` + `C` (Windows、Linux) 或 `Command` + `Shift` + `C` (macOS) ，然后单击视口中的元素。

*   在 DevTools 中，单击 **DOM 树中的 元素**。

*   在 DevTools 中，像在控制台中一样运行查询，将鼠标悬停在结果上，打开上下文菜单 (右键单击") "，然后单击"元素"面板中的 `document.querySelector('p')` "**展示"。** ****


<!-- ====================================================================== -->
## <a name="view-the-external-stylesheet-where-a-rule-is-defined"></a>查看已定义规则的外部样式表

在 **"样式** "窗格中，单击 CSS 规则旁边的链接以打开定义该规则的外部样式表。  样式表将在"源" **工具的** "编辑器" **窗格中** 打开。

如果样式表缩小，请单击"编辑器"窗格**** (") "设置 ![ ](../media/format-icon.msft.png) 格式"**按钮**。  有关详细信息，请参阅使用非常打印 [重新设置缩小的 JavaScript 文件](../javascript/reference.md#reformat-a-minified-javascript-file-with-pretty-print)。

在下图中，单击后，您将进入 定义 CSS 规则的第 `https://docs.microsoft.com/_themes/docs.theme/master/en-us/_themes/styles/b66bc881.site-ltr.css:2` 2 `https://docs.microsoft.com/_themes/docs.theme/master/en-us/_themes/styles/b66bc881.site-ltr.css` `.content h1:first-of-type` 行。

:::image type="content" source="../media/css-elements-styles-h1-highlight.msft.png" alt-text="查看定义规则的样式表。" lightbox="../media/css-elements-styles-h1-highlight.msft.png":::


<!-- ====================================================================== -->
## <a name="view-only-the-css-that-is-actually-applied-to-an-element"></a>仅查看实际应用于元素的 CSS

**“样式”** 面板显示应用于元素的所有规则，包括已覆盖声明。  当你对覆盖声明不感兴趣时，使用 **“计算”** 面板仅查看实际应用于元素的 CSS。

1.  [选择元素](#select-an-element)。

1.  转到" **元素"工具** 中的"计算 **"** 面板。

在宽的 DevTools 窗口中，**“计算”** 面板不存在。  **“计算”** 面板中的内容会在 **“样式”** 面板中显示。

继承的属性不透明。  若要显示所有继承的值，请选中 **“显示所有”** 复选框。

在下图中，" **计算** "面板显示应用于当前选定元素的 CSS `h1` 属性：

:::image type="content" source="../media/css-elements-computed-h1.msft.png" alt-text="计算面板。" lightbox="../media/css-elements-computed-h1.msft.png":::


<!-- ====================================================================== -->
## <a name="view-css-properties-in-alphabetical-order"></a>按字母顺序查看 CSS 属性

使用 **“计算”** 面板。  请参阅[仅查看实际应用于元素 的 CSS。](#view-only-the-css-that-is-actually-applied-to-an-element)


<!-- ====================================================================== -->
## <a name="view-inherited-css-properties"></a>查看继承的 CSS 属性

选中 **“计算”** 面板中的 **“显示所有”** 复选框。  请参阅[仅查看实际应用于元素 的 CSS。](#view-only-the-css-that-is-actually-applied-to-an-element)


<!-- ====================================================================== -->
## <a name="view-an-elements-box-model"></a>查看元素的框模型

若要查看 [元素的框](https://developer.mozilla.org/docs/Learn/CSS/Introduction_to_CSS/Box_model) 模型，请转到"样式 **"** 面板。  如果 DevTools 窗口较窄，则 **框模型** 图位于面板的底部。

若要更改值，请双击它。

下图中，**“样式”** 面板中的 **“框模型”** 图显示当前所选 `h1` 元素的框模型。

:::image type="content" source="../media/css-elements-styles-h1-2.msft.png" alt-text="方框模型图。" lightbox="../media/css-elements-styles-h1-2.msft.png":::


<!-- ====================================================================== -->
## <a name="search-and-filter-the-css-of-an-element"></a>搜索和筛选元素的 CSS

使用 **“样式”** 和 **“计算”** 面板上的 **“过滤器”** 文本框来搜索特定的 CSS 属性或值。

若要在 **“计算”** 面板中同时搜索继承属性，请选中 **“全部显示”** 复选框。

下图中，筛选 **“样式”** 面板为只显示包含搜索查询的 `color` 规则。

:::image type="content" source="../media/css-elements-styles-filter-color.msft.png" alt-text="筛选&quot;样式&quot;面板。" lightbox="../media/css-elements-styles-filter-color.msft.png":::

下图中，筛选 **“计算”** 面板以仅显示包含搜索查询 `100%` 的声明。

:::image type="content" source="../media/css-elements-computed-filter-100.msft.png" alt-text="筛选&quot;计算&quot;面板。" lightbox="../media/css-elements-computed-filter-100.msft.png":::


<!-- ====================================================================== -->
## <a name="toggle-a-pseudo-class"></a>切换伪类

切换伪类（如 `:active` `:focus` 、、 `:hover` 或 `:visited` ）：

1.  [选择元素](#select-an-element)。
1.  在" **元素"** 工具上，转到" **样式"** 选项卡。
1.  单击 **：hov**。
1.  选择要启用的伪类。

下图显示了切换伪 `:hover` 类。  在视口中，该声明将应用于元素，即使该元素实际上并未 `background-color: cornflowerblue` 悬停在上方。

:::image type="content" source="../media/css-elements-styles-hov-hover.msft.png" alt-text="切换 ：hover 伪类。" lightbox="../media/css-elements-styles-hov-hover.msft.png":::

有关交互式教程，请参阅 [向类添加伪状态](../css/index.md#add-a-pseudostate-to-a-class)。


<!-- ====================================================================== -->
## <a name="view-a-page-in-print-mode"></a>在打印模式下查看页面

在打印模式下查看页面：
1.  打开“[命令菜单](../command-menu/index.md)”。
1.  开始键入， `Rendering` 然后选择"显示**呈现"。**
1.  单击"**模拟 CSS 媒体**"下拉列表，然后选择"打印 **"。**


<!-- ====================================================================== -->
## <a name="view-used-and-unused-css-with-the-coverage-tool"></a>使用覆盖工具查看已使用和未使用的 CSS

**“覆盖”** 工具显示页面实际使用 CSS。

1.  打开命令[菜单](../command-menu/index.md)，按 `Control` + `Shift` + `P` (Windows、Linux) 或 (`Command` + `Shift` + `P` macOS) ，而 DevTools 具有焦点。
1.  开始键入 `coverage` 并选择 **“显示范围”**。  出现 **“覆盖”** 工具。

    从命令菜单打开"覆盖"选项卡：

    :::image type="content" source="../media/css-console-command-menu-coverage.msft.png" alt-text="从命令菜单打开覆盖选项卡。" lightbox="../media/css-console-command-menu-coverage.msft.png":::

    "覆盖"选项卡：

    :::image type="content" source="../media/css-console-qs-coverage-empty.msft.png" alt-text="&quot;覆盖&quot;选项卡。" lightbox="../media/css-console-qs-coverage-empty.msft.png":::

1.  单击 **开始检测覆盖范围并刷新页面** (![ 开始检测范围并刷新页面 ](../media/refresh-icon.msft.png)) 。  页面刷新和"范围"**** 选项卡概述了浏览器加载的每个 (使用的 CSS 和 JavaScript) 。  绿色表示已使用的 CSS。  红色表示未使用的 CSS。

    使用和未使用 CSS (JavaScript) 概述：

    :::image type="content" source="../media/css-console-qs-coverage-run.msft.png" alt-text="使用和未使用 CSS (JavaScript) 概述。" lightbox="../media/css-console-qs-coverage-run.msft.png":::

1.  若要显示使用 CSS 的明细数据，请单击 CSS 文件。

    在下图中，未使用第 145 至 147 行以及 149 到 151 行，而使用 `b66bc881.site-ltr.css` 行 163 至 166：

    :::image type="content" source="../media/css-sources-css-coverage.msft.png" alt-text="已使用和未使用的 CSS 的行细分。" lightbox="../media/css-sources-css-coverage.msft.png":::


<!-- ====================================================================== -->
## <a name="force-print-preview-mode"></a>强制打印预览模式

请参阅 [强制 DevTools 进入打印预览模式](../css/print-preview.md)。


<!-- ## Change CSS -->
<!-- todo s/CSS declaration/declaration/ -->


<!-- ====================================================================== -->
## <a name="add-a-css-declaration-to-an-element"></a>向元素添加 CSS 声明

声明顺序会影响元素的样式，请使用以下列表来帮助以不同方式添加声明。

*   [添加内联声明](#add-an-inline-declaration)。  相当于向元素的 HTML 添加 `style` 属性。
*   [向“样式规则”添加声明](#add-a-declaration-to-a-style-rule)。

**该使用什么工作流?**  多数情况下，可能需要使用内联声明工作流。  内联声明具有比外部声明更高的特定性，因此内联工作流可确保更改在预期元素中生效。  有关特定性详细信息，请参阅选择 [器类型](https://developer.mozilla.org/docs/Web/CSS/Specificity#Selector_Types)。

如果要调试元素的样式，并且需要专门测试在不同位置定义声明时会发生什么情况，请使用其他工作流。

### <a name="add-an-inline-declaration"></a>添加内联声明

添加内嵌声明：

1.  [选择元素](#select-an-element)。
1.  在" **样式"** 窗格中，在 **element.style** 节的括号之间单击。  光标聚焦，以允许输入文本。
1.  输入属性名称，然后按 `Enter` 。
1.  输入该属性的有效值，然后按 `Enter` 。  在 **DOM 树中**， `style` 属性已添加到 元素中。

下图中，`margin-top` 和 `background-color` 属性已应用于所选元素。  在 **DOM 树中**，声明将反映在元素的 `style` 属性中。

:::image type="content" source="../media/css-elements-styles-margin-top-background-color.msft.png" alt-text="添加内嵌声明。" lightbox="../media/css-elements-styles-margin-top-background-color.msft.png":::

### <a name="add-a-declaration-to-a-style-rule"></a>向样式规则添加声明

若要向现有样式规则添加声明：

1.  [选择元素](#select-an-element)。
1.  在 **"样式** "窗格中，在要添加声明的样式规则的括号之间单击。  光标聚焦，以允许输入文本。
1.  输入属性名称，然后按 `Enter` 。
1.  输入该属性的有效值，然后按 `Enter` 。

:::image type="content" source="../media/css-elements-styles-border-bottom-style.msft.png" alt-text="向样式规则添加声明。" lightbox="../media/css-elements-styles-border-bottom-style.msft.png":::


<!-- ====================================================================== -->
## <a name="change-a-declaration-name-or-value"></a>更改声明名称或值

双击声明的名称或值以更改它。  有关 [快速增加](#change-declaration-values-with-keyboard-shortcuts) 或缩小 0.1、1、10 或 100 个单位的快捷方式，请参阅使用键盘快捷方式更改声明值。

:::image type="content" source="../media/css-elements-styles-border-bottom-style-dropdown.msft.png" alt-text="更改声明的值。" lightbox="../media/css-elements-styles-border-bottom-style-dropdown.msft.png":::


<!-- ====================================================================== -->
## <a name="change-declaration-values-with-keyboard-shortcuts"></a>使用键盘快捷方式更改声明值

编辑声明的值时，可以使用以下键盘快捷方式将值增加特定量：

| 键盘快捷方式 | 递增者 |
|---|---|
| `Alt`+`Up` (Windows、Linux) 或 `Option` + `Up` (macOS)  | 0.1 |
| `Up` | 1 (或 0.1（如果当前值介于 -1 和 1 之间)  |
| `Shift`+`Up` | 10 |
| `Shift`+`Page Up` (Windows、Linux) 或 `Shift` + `Command` + `Up` (macOS)  | 100 |

若要缩小，请按 `Down` 键而不是 `Up` 键。


<!-- ====================================================================== -->
## <a name="add-a-class-to-an-element"></a>向元素添加类

若要向元素添加类：

1.  在 ** DOM 树** 中 [选择元素](#select-an-element)。
1.  单击 **".cls"。**
1.  在 **“添加新类”** 文本框中输入类的名称。
1.  按 `Enter` 。

:::image type="content" source="../media/css-elements-styles-filter-classes.msft.png" alt-text="&quot;元素类&quot;窗格。" lightbox="../media/css-elements-styles-filter-classes.msft.png":::


<!-- ====================================================================== -->
## <a name="toggle-a-class"></a>切换类

若要启用或禁用元素上的类，

1.  在 ** DOM 树** 中 [选择元素](#select-an-element)。
1.  打开 **“元素类”** 窗格。  请参阅 [向元素添加类](#add-a-class-to-an-element)。  在 **"添加新类** "文本框下方是应用于此元素的所有类。
1.  切换要启用或禁用的类旁边的复选框。


<!-- ====================================================================== -->
## <a name="add-a-style-rule"></a>添加样式规则

添加新的样式规则：

1.  [选择元素](#select-an-element)。
1.  单击 **"新建样式规则** (![ 新建样式 ](../media/new-style-rule-icon.msft.png) 规则) 。  DevTools 在 **element.style** 规则下方插入新规则。

在下图中，DevTools 在单击"新建样式规则" `h1.devsite-page-title` 后 **添加样式规则**。

:::image type="content" source="../media/css-elements-styles-style-new.msft.png" alt-text="添加新的样式规则。" lightbox="../media/css-elements-styles-style-new.msft.png":::

### <a name="choose-which-stylesheet-to-add-a-rule-to"></a>选择要添加规则的样式表

添加新 [样式规则](#add-a-style-rule)时，单击并按住 New **Style Rule** (New Style Rule) 以选择要向哪个 ![ ](../media/new-style-rule-icon.msft.png) 样式表添加样式规则。

:::image type="content" source="../media/css-elements-styles-style-new-select-existing.msft.png" alt-text="选择样式表。" lightbox="../media/css-elements-styles-style-new-select-existing.msft.png":::

### <a name="add-a-style-rule-to-a-specific-location"></a>向特定位置添加样式规则

若要将样式规则添加到"样式" **面板中的特定** 位置：

1.  将鼠标悬停在要添加新样式规则正上方的样式规则上。

1.  [显示 **“更多操作”** 工具栏](#reveal-the-more-actions-toolbar)。

1.  Select **Insert Style Rule below (** Insert Style Rule below icon ![ ](../media/new-style-rule-icon.msft.png)) .

:::image type="content" source="../media/css-elements-styles-insert-style-rule-below.msft.png" alt-text="在下方插入样式规则。" lightbox="../media/css-elements-styles-insert-style-rule-below.msft.png":::


<!-- ====================================================================== -->
## <a name="reveal-the-more-actions-toolbar"></a>显示“更多操作”工具栏

" **更多操作** "工具栏允许您执行以下操作：
*   直接在所关注样式规则下面插入样式规则。
*   向所关注的样式规则添加`background-color`、`color`、`box-shadow` 或 `text-shadow` 声明。

若要显示" **更多操作"工具栏** ：

1.  在 **“样式”** 面板中，将鼠标悬停在样式规则上。  **样式** `...` () 右下角显示更多操作。

    下图中，将鼠标悬停在 `.header-holder.has-default-focus` 样式规则上，在样式规则部分的右下方会显示出 **“更多操作”**。

    :::image type="content" source="../media/css-elements-styles-new-rule-styles.msft.png" alt-text="显示&quot;更多操作&quot; (...) 。" lightbox="../media/css-elements-styles-new-rule-styles.msft.png":::

1.  将鼠标 **悬停在"更多** `...` () 可显示上述操作。

    将鼠标悬停在 **“更多动作“** 上，就会显示出 **“下方插入样式规则”** 操作。

    :::image type="content" source="../media/css-elements-styles-rule-more-options-insert-style-rule-below.msft.png" alt-text="&quot;更多操作&quot;工具栏。" lightbox="../media/css-elements-styles-rule-more-options-insert-style-rule-below.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-background-color-declaration"></a>添加背景色声明

若要向 `background-color` 元素添加声明：

1.  将鼠标悬停在要添加 `background-color` 声明的样式规则上。

1.  [显示 **“更多操作”** 工具栏](#reveal-the-more-actions-toolbar)。

1.  单击 **添加背景色** (![ 添加背景色图标 ](../media/add-background-color-icon.msft.png)) 。

:::image type="content" source="../media/css-elements-styles-rule-add-background-color.msft.png" alt-text="添加背景色。" lightbox="../media/css-elements-styles-rule-add-background-color.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-color-declaration"></a>添加颜色声明

若要向 `color` 元素添加声明：

1.  将鼠标悬停在要添加 `color` 声明的样式规则上。

1.  [显示 **“更多操作”** 工具栏](#reveal-the-more-actions-toolbar)。

1.  单击 **添加颜色** (![ 添加颜色图标 ](../media/add-color-icon.msft.png)) 。

:::image type="content" source="../media/css-elements-styles-rule-add-color.msft.png" alt-text="添加颜色。" lightbox="../media/css-elements-styles-rule-add-color.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-box-shadow-declaration"></a>添加框阴影声明

若要向 `box-shadow` 元素添加声明：

1.  将鼠标悬停在要添加 `box-shadow` 声明的样式规则上。
1.  [显示 **“更多操作”** 工具栏](#reveal-the-more-actions-toolbar)。
1.  单击 **添加框阴影** (![ 添加框阴影 ](../media/add-box-shadow-icon.msft.png) 图标) 。

:::image type="content" source="../media/css-elements-styles-rule-add-box-shadow.msft.png" alt-text="添加框阴影。" lightbox="../media/css-elements-styles-rule-add-box-shadow.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-text-shadow-declaration"></a>添加文本阴影声明

若要向 `text-shadow` 元素添加声明：

1.  将鼠标悬停在要添加 `text-shadow` 声明的样式规则上。
1.  [显示 **“更多操作”** 工具栏](#reveal-the-more-actions-toolbar)。
1.  单击 **"添加文本阴影** (![ 添加文本阴影图标 ](../media/add-text-shadow-icon.msft.png)) 。

:::image type="content" source="../media/css-elements-styles-rule-add-text-shadow.msft.png" alt-text="添加文本阴影。" lightbox="../media/css-elements-styles-rule-add-text-shadow.msft.png":::


<!-- ====================================================================== -->
## <a name="toggle-a-declaration"></a>切换声明

打开或关闭单个声明：

1.  [选择元素](#select-an-element)。

1.  在 **“样式”** 窗格中，将鼠标悬停在定义声明的规则上。  每个声明旁边将显示复选框。

1.  选中或清除声明旁边的复选框。  当你清除声明时，DevTools 会交叉它，以指示它不再处于活动状态。

下图中，当前选中元素的 `margin-top` 属性已关闭。

:::image type="content" source="../media/css-elements-styles-rule-deactivated.msft.png" alt-text="切换声明。" lightbox="../media/css-elements-styles-rule-deactivated.msft.png":::


<!-- ====================================================================== -->
## <a name="change-colors-with-the-color-picker"></a>使用颜色选取器更改颜色

**颜色选取器** 为更改 `color` 和 `background-color` 声明提供 GUI。

打开颜色 **选取器**：

1.  [选择元素](#select-an-element)。

1.  在 **“样式”** 面板中，找到 `color`、`background-color` 或要更改的类似声明。  在 、 或类似值的左侧，有一个小 `color` `background-color` 正方形，这是颜色的预览。

    下图中，`rgba(0, 0, 0, 0.7)` 左侧的小方块是该颜色的预览。

    :::image type="content" source="../media/css-elements-styles-rule-overlay-color-box.msft.png" alt-text="颜色预览。" lightbox="../media/css-elements-styles-rule-overlay-color-box.msft.png":::

1.  单击预览以打开 **颜色选取器**。

    :::image type="content" source="../media/css-elements-styles-rule-color-picker.msft.png" alt-text="颜色选取器。" lightbox="../media/css-elements-styles-rule-color-picker.msft.png":::

下图和列表描述了颜色选取器的每个 UI **元素**。

:::image type="content" source="../media/css-elements-styles-rule-color-picker-annotated.msft.png" alt-text="添加批注的颜色选取器。" lightbox="../media/css-elements-styles-rule-color-picker-annotated.msft.png":::

| 标注 | 组件 | 描述 |
|---|---|---|
| 1 | **色调** |  |
| 2 | **取色器** | [用“取色器“在页面上打样着色](#sample-a-color-off-the-page-with-the-eyedropper) |
| 3 | **复制到剪贴板** | 将 **“显示值”** 复制到剪贴板。 |
| 4 | **显示值** | 颜色的 RGBA、HSLA 或十六进制表示形式。 |
| 5 | **调色板** | 单击正方形以更改颜色。 |
| 6 | **色调** |  |
| 7 | **不透明度** |  |
| 8 | **显示值切换器** | 在当前颜色的 RGBA、HSLA 和十六进制表示形式之间切换。 |
| 9 | **调色板切换器** | 在 [“材质设计调色板”](https://material.io/guidelines/style/color.html#color-color-palette)、“自定义调色板”或“页面颜色调色板”之间切换。  DevTools 根据在样式表中所找到的颜色来生成页面调色板。 |

### <a name="sample-a-color-off-the-page-with-the-eyedropper"></a>用“取色器“在页面上打样着色

打开颜色**选取器**时， (取色**** 器) ![ ](../media/eyedropper-icon.msft.png) 已打开。

若要将所选颜色更改为页面上的某种其他颜色：

1.  将鼠标悬停在视区中的目标颜色上。

1.  单击以确认。

下图中，**“颜色选取器”** 显示接近黑色的电流 `rgba(0,0,0,0.7)` 颜色值。  单击后，特定颜色将更改到视口中当前突出显示的黑色版本。

:::image type="content" source="../media/css-color-picker-eye-dropper.msft.png" alt-text="使用目视器。" lightbox="../media/css-color-picker-eye-dropper.msft.png":::


<!-- ====================================================================== -->
## <a name="change-angle-value-with-the-angle-clock"></a>使用角度时钟更改角度值

<!--todo: finish formatting this section on the Angle clock.  Add 2 captures.  See What's New 88:
https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/whats-new/2020/11/devtools#new-css-angle-visualization-tools
-->

Angle **Clock** 提供了一个 GUI，用于更改 CSS 属性值中的角度量。

打开角度 **时钟**：

1.  选择包含角度声明的元素。 <!-- For example, select the text below. -->

1.  在 **"样式** "选项卡中， `transform` `background` 查找要更改的 或 声明。  单击 **角度值旁边的** "角度预览"框。

    下图中，左侧的小时钟是 `100deg` 角度的预览。
    <!-- :::image type="content" source="../media/__.png" alt-text="The Angle Clock."::: -->

1.  单击预览以打开 **角度时钟**：

    :::image type="content" source="images/css-angle.msft.png" alt-text="角度预览。":::

1.  通过单击"角度时钟"圆圈或**** 滚动鼠标将角度值增加或减小 1 来更改角度值。

更多键盘快捷方式可更改角度值。  在"样式"窗格 [键盘快捷方式中了解详细信息](../shortcuts/index.md#styles-pane-keyboard-shortcuts)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/css/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
