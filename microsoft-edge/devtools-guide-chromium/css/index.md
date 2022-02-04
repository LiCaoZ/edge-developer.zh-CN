---
title: 查看和更改 CSS 入门
description: 了解如何使用 Microsoft Edge工具查看和更改页面的 CSS。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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
# <a name="get-started-viewing-and-changing-css"></a>查看和更改 CSS 入门

按照这些交互式教程部分了解使用 DevTools 查看和更改页面 CSS 的基础知识。


<!-- ====================================================================== -->
## <a name="view-the-css-for-an-element"></a>查看元素的 CSS

1. 打开新窗口或选项卡中的["CSS](https://microsoftedge.github.io/Demos/devtools-css-get-started/) 示例"演示页。 为此，请右键单击`Control`该链接，或长按 (Windows、Linux) `Command` 或 (macOS) 然后单击该链接。

   <!-- You can view the source files for the CSS Examples demo page at the [MicrosoftEdge/Demos > devtools-css-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-css-get-started) repo folder. -->

1. 右键单击文本 `Inspect Me!` ，然后选择"检查 **"**。

   在 DevTools 中，在 **"元素**"工具的 **"DOM 树**`Inspect Me!`"面板中，元素突出显示。

   :::image type="content" source="../media/css-elements-inspect-me.msft.png" alt-text="检查的元素在 DOM 树中突出显示。" lightbox="../media/css-elements-inspect-me.msft.png":::

1. `Inspect Me!`在 元素中，找到 属性的值并`data-message`复制它。

1. 在页面上的" **值"`data-message`** 文本框中，输入值。

1. 右键单击文本 `Inspect Me!` ，然后选择"检查 **"**。

1. 在 DevTools 中的" **元素"** 工具上，选择 **"样式"** 面板。  在 **"样式"** 面板中， `Inspect Me!` 元素突出显示。

1. 在 元素 `Inspect Me!` 中，查找类 `aloha` 规则。  显示此规则，因为它将应用于 `Inspect Me!` 元素。

1. `aloha`在 类中，查找样式的值`padding`并复制它。

   :::image type="content" source="../media/css-elements-inspect-me-styles.msft.png" alt-text="CSS 类应用于检查的元素在&quot;样式&quot;面板中突出显示。" lightbox="../media/css-elements-inspect-me-styles.msft.png":::

1. 在页面上的" **值"`padding`** 文本框中，输入值。


<!-- ====================================================================== -->
## <a name="add-a-css-declaration-to-an-element"></a>向元素添加 CSS 声明

当您 **要更改** CSS 声明或将 CSS 声明添加到元素时，请使用"样式"面板。

1. 首先，我们建议执行上述 [查看元素的 CSS](#view-the-css-for-an-element) 教程部分。

1. 打开新窗口或选项卡中的 ["CSS](https://microsoftedge.github.io/Demos/devtools-css-get-started/) 示例"演示页。

1. 右键单击文本 `Add A Background Color To Me!` ，然后选择"检查 **"**。

1. 单击 `element.style` "样式"面板 **顶部** 附近。

1. 键入 `background-color` ，然后按 `Enter`。

1. 键入 `honeydew` ，然后按 `Enter`。  在 **DOM 树**中，将显示应用于元素的内联样式声明。

    使用`background-color:honeydew`"样式"面板的 部分`element.style`将声明**应用于 元素：**

   :::image type="content" source="../media/css-elements-add-background-color-to-me-styles-p.msft.png" alt-text="使用&quot;样式&quot;面板向 元素添加 CSS 声明。" lightbox="../media/css-elements-add-background-color-to-me-styles-p.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-css-class-to-an-element"></a>将 CSS 类添加到元素

若要显示 CSS 类应用于元素或从元素中删除 CSS 类时元素的外观，请参阅 **样式** 面板。

1. 首先，我们建议执行上述 [查看元素的 CSS](#view-the-css-for-an-element) 教程部分。

1. 打开新窗口或选项卡中的 ["CSS](https://microsoftedge.github.io/Demos/devtools-css-get-started/) 示例"演示页。

1. 右键单击文本 `Add A Class To Me!` ，然后选择"检查 **"**。

1. 单击 **".cls"**。  DevTools 显示一个文本框，可在其中将 CSS 类添加到正在检查的页面元素中。

1. 在 `color_me` "添加新 **类"** 文本框中键入 ，然后按 `Enter`。  "添加新 **类"文本框** 下方将出现一个复选框，可在其中打开和关闭该类。  `Add A Class To Me!`如果元素应用了任何其他类，则还可以在此处切换每个类。

   类`color_me`使用"样式"面板的 **.cls** 部分**应用到 元素：**

   :::image type="content" source="../media/css-elements-add-a-class-to-me-styles-cls.msft.png" alt-text="将 color_me 类应用到 元素。" lightbox="../media/css-elements-add-a-class-to-me-styles-cls.msft.png":::


<!-- ====================================================================== -->
## <a name="add-a-pseudostate-to-a-class"></a>向类添加伪状态

使用 **"样式** "面板将 CSS 伪状态永久应用到元素。  DevTools 支持 `:active`、 `:focus`、 `:hover`和 `:visited`。

1. 首先，我们建议执行上述 [查看元素的 CSS](#view-the-css-for-an-element) 教程部分。

1. 打开新窗口或选项卡中的 ["CSS](https://microsoftedge.github.io/Demos/devtools-css-get-started/) 示例"演示页。

1. 将鼠标悬停在文本 `Hover Over Me!` 上。  背景色更改。

1. 右键单击文本 `Hover Over Me!` ，然后选择"检查 **"**。

1. 在" **样式"** 面板中，单击 **"：hov"**。

1. 选中" **：hover** "复选框。  背景颜色会像以前一样更改，即使你实际上没有将鼠标悬停在元素上。

   下面是切换元素 `:hover` 上的伪状态的结果：

   :::image type="content" source="../media/css-elements-hover-over-me-styles-hov-hover.msft.png" alt-text="切换元素上的悬停伪状态。" lightbox="../media/css-elements-hover-over-me-styles-hov-hover.msft.png":::


<!-- ====================================================================== -->
## <a name="change-the-dimensions-of-an-element"></a>更改元素的维度

使用 **"样式** " **面板中的"** 方框模型"交互式图表可更改元素的宽度、高度、填充、边距或边框长度。

1. 首先，我们建议执行上述 [查看元素的 CSS](#view-the-css-for-an-element) 教程部分。

1. 打开新窗口或选项卡中的 ["CSS](https://microsoftedge.github.io/Demos/devtools-css-get-started/) 示例"演示页。

1. 右键单击文本 `Change My Margin!` ，然后选择"检查 **"**。

1. 在" **样式"面板** 的"方框模型 **"** 图表中，将鼠标悬停在 **填充上**。  元素的填充在视口中突出显示。

   根据 DevTools 窗口的大小，可能需要滚动到"样式"面板底部才能显示 **"框模型"**。****

1. 双击 Box 模型中****`-`的左边距，当前具有 的值 ，这意味着元素没有 。`margin-left`

1. 键入 并 `100px` 按 `Enter`。  方框 **模型** 默认为像素，但它也接受其他值，如 `25%`或 `10vw`。

   将鼠标悬停在元素的填充上：

   :::image type="content" source="../media/css-elements-change-my-margin-styles-padding.msft.png" alt-text="将鼠标悬停在元素的填充上。" lightbox="../media/css-elements-change-my-margin-styles-padding.msft.png":::

   更改元素的左边距：

   :::image type="content" source="../media/css-elements-change-my-margin-styles-margin-edit.msft.png" alt-text="更改元素的左边距。" lightbox="../media/css-elements-change-my-margin-styles-margin-edit.msft.png":::


<!-- ====================================================================== -->
## <a name="debugging-media-queries"></a>调试媒体查询

[媒体查询](https://developer.mozilla.org/docs/Web/CSS/Media_Queries/Using_media_queries) 是一种使 Web 产品对每个用户的配置设置更改做出反应的方法。  最重要的用例是，根据视口尺寸为产品提供不同的 CSS 布局。

当有更多的屏幕空间可用时，使用单独的布局允许移动设备使用单列布局和多列布局。

若要调试或测试在 CSS 中定义的媒体查询，请执行以下操作：

1. 打开 DevTools。  为此，可以在网页中右键单击，然后选择"检查 **"**。

1. 单击"**切换设备仿真 (**!["设备仿真"图标](../media/device-emulation-icon-light-theme.png)。) 按钮。  或者，当 DevTools 具有焦点时，`Ctrl``Shift`++`M``M`+`Cmd`+`Shift`在 macOS (按) 。

   <!-- todo: update to show new tooltip: -->

   :::image type="content" source="../media/css-elements-media-queries-open-device-toolbar.msft.png" alt-text="打开设备工具栏。" lightbox="../media/css-elements-media-queries-open-device-toolbar.msft.png":::

1. 打开设备工具栏后，单击 `...` 右上方的菜单，然后选择" **显示媒体查询"**：

   :::image type="content" source="../media/css-elements-media-queries-showing-mq.msft.png" alt-text="在设备工具栏中显示媒体查询。" lightbox="../media/css-elements-media-queries-showing-mq.msft.png":::

   网页上方的彩色条表示不同的媒体查询。
       
1. 将鼠标悬停在条形的边界上，以显示不同媒体查询的值。  单击每个媒体查询值以调整网页大小以匹配。

   :::image type="content" source="../media/css-elements-media-queries-select-bar.msft.png" alt-text="从预览栏中选择媒体查询。" lightbox="../media/css-elements-media-queries-select-bar.msft.png":::

1. 若要调试媒体查询，然后在编辑器中打开 CSS `Sources` 文件，请右键单击条段，然后选择 `reveal in source code`。

   :::image type="content" source="../media/css-elements-media-queries-reveal-in-sources.msft.png" alt-text="在源编辑器中显示媒体查询。" lightbox="../media/css-elements-media-queries-reveal-in-sources.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/css/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
