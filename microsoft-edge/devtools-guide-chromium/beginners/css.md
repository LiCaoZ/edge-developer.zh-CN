---
title: 适用于初学者的 DevTools：CSS 入门
description: CSS 入门
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 07/26/2021
ms.openlocfilehash: b03ff5b96c5a266f6494b05e849b5b32c3142e2f
ms.sourcegitcommit: fd3b79a0570cfefc2a40107b223569210cb2c2d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2021
ms.locfileid: "12269198"
---
<!-- Copyright Katherine Jackson

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->

# <a name="devtools-for-beginners-get-started-with-css"></a>适用于初学者的 DevTools：CSS 入门

本教程介绍如何使用 CSS 设置网页样式。  此外，还了解如何使用 Microsoft Edge DevTools 试验 CSS 更改。

本文是一系列教程的一部分，这些教程将指导你 Web 开发和开发工具Microsoft Edge基础知识。  通过实际构建自己的网站，可以获得实践体验。  在执行此操作之前，你不必完成前面的教程。  [设置代码将](#set-up-your-code) 演示如何进行设置。

> [!NOTE]
> 本教程专为绝对初学者设计，专注于 Web 开发 **的** 基础知识和使用 DevTools 进行 CSS 测试的基础知识。  如果你需要一个仅侧重于 DevTools 的教程，请导航到查看和 [更改 CSS 入门](../css/index.md)。

在本教程的开头，您的网站应如下图所示。

:::image type="content" source="../media/beginners-css-intro1.msft.png" alt-text="你的网站当前的外观。" lightbox="../media/beginners-css-intro1.msft.png":::

完成本教程后，您的网站应如下图所示。

:::image type="content" source="../media/beginners-css-intro2.msft.png" alt-text="在本教程的末尾，你的网站应该是什么样。" lightbox="../media/beginners-css-intro2.msft.png":::


<!-- ====================================================================== -->
## <a name="goals"></a>目标

按照本教程可更好地了解以下概念和任务。

*   如何使用 CSS 设置网页样式。
*   如何使用 Microsoft Edge DevTools 对 CSS 进行试验。
*   CSS 和 CSS 框架的区别。

你正在构建一个真实网站。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

完成以下先决条件，然后再执行本教程。

*   使用[入门 DOM](./html.md)完成 HTML 和 DOM 的填写，或确保您已了解 HTML 和 DOM。
*   下载 [Microsoft Edge](https://www.microsoftedgeinsider.com) Web 浏览器。  以下教程使用一组内置于 Microsoft Edge 中的 Web 开发工具（称为 Microsoft Edge DevTools）。


<!-- ====================================================================== -->
## <a name="set-up-your-code"></a>设置代码

若要创建网站，请首先执行以下步骤来设置代码。

> [!NOTE]
> 如果已完成系列的第一个教程，请跳到下一部分。  继续使用上一教程 HTML 和 [DOM 入门中的代码](./html.md)。

1.  打开 [源代码](https://glitch.com/edit/#!/cooked-amphibian?path=index.html)。  当前选择的浏览器选项卡称为" **编辑"选项卡**。

    :::image type="content" source="../media/beginners-css-setup1.msft.png" alt-text="&quot;编辑&quot;选项卡。" lightbox="../media/beginners-css-setup1.msft.png":::

1.  选择 **"cooked-amphibian"。**  弹出一个菜单。

    :::image type="content" source="../media/beginners-css-setup2.msft.png" alt-text="&quot;Project 选项&quot;菜单。" lightbox="../media/beginners-css-setup2.msft.png":::

1.  选择 **"重新混合Project"。**  Glitch 将创建一个可编辑的项目副本。

    > [!NOTE]
    > Glitch 会为新项目生成随机名称。

1.  选择 **"显示**"，然后选择 **"在新建窗口中"。**  打开另一个选项卡，其中显示网站实时视图。  当前选择的浏览器选项卡称为"实时**选项卡"。**

    :::image type="content" source="../media/beginners-css-setup3.msft.png" alt-text="动态选项卡。" lightbox="../media/beginners-css-setup3.msft.png":::


<!-- ====================================================================== -->
## <a name="understand-css"></a>了解 CSS

**CSS** 是控制网页布局和样式的计算机语言。  下图是带边框的段落。

:::image type="content" source="../media/beginners-css-red_paragraph.msft.png" alt-text="文本已使用 CSS 设置样式。" lightbox="../media/beginners-css-red_paragraph.msft.png":::

以下代码段是用于创建上图中段落的 HTML 和 CSS 代码。

```html
<p style="border: 1px dashed red; padding: 5px;">
    This has been styled with CSS.
</p>
```

HTML 属性 `style="border: 1px dashed red; padding: 5px;"` 可能看起来是全新的。  其余部分看起来应该很熟悉。  如果没有，在尝试以下部分之前，请完成 HTML 和 [DOM](./html.md) 入门。


<!-- ====================================================================== -->
## <a name="add-inline-styles"></a>添加内联样式

可以使用 **内联样式将** 样式应用于单个元素。

1.  返回到编辑选项卡并打开`index.html`。

    :::image type="content" source="../media/beginners-css-inline1.msft.png" alt-text="在index.html选项卡中打开&quot;编辑&quot;选项卡。" lightbox="../media/beginners-css-inline1.msft.png":::

1.  在 元素 `style="background-color: aliceblue;"` 中添加 `<nav>` 属性。  在下面的代码块中，只需更改第四行代码。  此处显示了其他代码行，以帮助您将新属性放在正确的位置。

    ```html
    <header>
        <p>Welcome to my site!</p>
    </header>
    <nav style="background-color: aliceblue;">
        <ul>
            <li><a href="/">Home</a></li>
            ...
        ...
    ...
    ```

1.  若要显示更改，请导航到活动 **选项卡**。 分区的背景 `<nav>` 现在为蓝色。

    :::image type="content" source="../media/beginners-css-inline2.msft.png" alt-text="&quot;主页&quot;和&quot;联系人&quot;链接背后的背景色现在为蓝色。" lightbox="../media/beginners-css-inline2.msft.png":::


<!-- ====================================================================== -->
## <a name="reuse-styles-on-a-single-page-with-internal-stylesheets"></a>在包含内部样式表的单个页面上重复使用样式

在之前的代码段中，内联样式将样式应用于单个 `<p>` 标记。

```html
<p style="border: 1px dashed red; padding: 5px;">
    This has been styled with CSS.
</p>
```

如果您希望网页上的所有元素都以相同的方式设置样式 `<p>` ，应该如何？  您必须将代码复制并粘贴到网站上每个标记中，这将需要大量 `<p>` 时间和精力。  如果需要进行编辑，必须再次更改每个标记。  相反，在接下来的步骤中，使用 **Internal 样式** 表编写 CSS 一次，以便它适用于多个元素。

1.  在活动选项卡中，选择 **"联系人"** 以导航到联系人页面。  请注意"主页"和 **"** 联系人 **"链接的** 字体。

    :::image type="content" source="../media/beginners-css-internal1.msft.png" alt-text="&quot;联系人&quot;页。" lightbox="../media/beginners-css-internal1.msft.png":::

1.  在编辑器 **选项卡中，** 打开 `contact.html`。
1.  将以下代码添加到 `contact.html`。  请记住，需要添加以 `<style>` 开始到 `</style>` 结尾的行。  此处显示了其他代码，以便你知道在哪里放入新代码。

    ```html
    ...
        <head>
            ...
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <style>
                li a {
                  font-family: 'Courier New', Courier, Serif;
                }
            </style>
            ...
        </head>
        ...
    ...
    ```

1.  返回到实时 **选项卡**。
1.  选择 **"** 联系人"返回到联系人页面。  请注意，"主页 **"和** " **联系人"链接的** 字体已更改。

    :::image type="content" source="../media/beginners-css-internal2.msft.png" alt-text="&quot;主页&quot;和&quot;联系人&quot;链接的字体已更改。" lightbox="../media/beginners-css-internal2.msft.png":::

### <a name="understand-internal-stylesheets"></a>了解内部样式表

内部样式表使用选择器应用 **样式**。  选择器是可应用于一个或多个 HTML 元素的模式。  前面的代码段添加了以下样式。

```html
<style>
    li a {
      font-family: 'Courier New', Courier, serif;
    }
</style>
```

`li a` 是转换为"任何 `<li>` 包含元素的元素 `<a>` "的选择器。  浏览器会更改 **“主页”** 和 **“联系人”** 链接的字体，因为每个标签组都与模式匹配。

```html
<li><a href="/">Home</a></li>
<li><a href="/contact.html">Contact</a></li>
```

`font-family: 'Courier New', Courier, serif` 是**声明**。  声明由以下两部分组成：

| 部分 | 示例 | 描述 |
| --- | --- | --- |
| **属性** | `font-family` | 属性描述应更改元素的样式。 |
| **value** | `'Courier New', Courier, serif` | 该值准确描述了元素的样式应该如何更改。 |

例如， `font-family: 'Courier New', Courier, serif` 为浏览器提供以下指令："将匹配模式的元素的字体设置为 `li a` `'Courier New'`。  如果该字体不可用，请使用 `Courier` 。  如果两者都不可用，请使用 `serif` 。"

### <a name="add-multiple-selectors-to-a-ruleset"></a>向规则集添加多个选择器

以下 CSS 代码段称为规则 **集**。

```css
li a {
  font-family: 'Courier New', Courier, monospace;
}
```

以下步骤介绍如何使用逗号向规则集添加多个选择器。

1.  在编辑器 **选项卡中，** 打开 `contact.html`。
1.  键入 `li a`类型`, h1` 后。

    ```html
    <style>
        li a, h1 {
          font-family: 'Courier New', Courier, Serif;
        }
    </style>
    ```

    前面的代码段指示浏览器设置元素样式的方式与设置与模式 `<h1>` 匹配的元素的样式相同 `li a`。

1.  导航到实时 **选项卡**。
1.  选择 **"联系人** "链接可返回到联系人页面。  现在， **联系我！** 具有与导航链接相同的字体。

    :::image type="content" source="../media/beginners-css-multiple1.msft.png" alt-text="文本&quot;联系我！&quot;。 现在，字体与&quot;主页&quot;和&quot;联系人&quot;链接相同。" lightbox="../media/beginners-css-multiple1.msft.png":::


<!-- ====================================================================== -->
## <a name="experiment-with-devtools"></a>使用 DevTools 进行试验

当你继续成为 Web 开发方面的专家时，你可能会发现 CSS 很复杂。  您可以编写一些不显示预期内容的代码。  Microsoft Edge开发人员工具通过实时在页面中显示更改来轻松进行试验。

### <a name="add-a-declaration-to-an-existing-ruleset-in-devtools"></a>将声明添加到 DevTools 中的现有规则集

向现有规则集添加声明

1.  将鼠标悬停在**主页链接**上，打开上下文菜单 (右键单击") "检查 **"。**

    :::image type="content" source="../media/beginners-css-add1.msft.png" alt-text="检查&quot;主页&quot;链接。" lightbox="../media/beginners-css-add1.msft.png":::

    DevTools 将在页面旁边打开。  代表"主页"链接的代码在 DOM 树中突出显示 `<a href="/">Home</a>` 为蓝色。  [HTML和DOM入门](./html.md)应该熟悉代码片段和预览。

    在下图中，您之前添加到的声明显示在 DOM 树下方的 `font-family: 'Courier New', Courier, serif` `contact.html` **"样式** "选项卡中：

    :::image type="content" source="../media/beginners-css-add2.msft.png" alt-text="&quot;样式&quot;选项卡位于 DOM 树的下方。" lightbox="../media/beginners-css-add2.msft.png":::

    如果 DevTools 窗口很宽，则"样式"选项卡位于 DOM 树的右侧：

    :::image type="content" source="../media/beginners-css-add3.msft.png" alt-text="&quot;样式&quot;选项卡位于 DOM 树的右侧。" lightbox="../media/beginners-css-add3.msft.png":::

1.  选择下面的空行 `font-family: 'Courier New', Courier, Serif` 以添加新声明。

    :::image type="content" source="../media/beginners-css-add4.msft.png" alt-text="添加新声明。" lightbox="../media/beginners-css-add4.msft.png":::

1.  键入 `color` 并选择 `Enter`。  键入时，自动完成 UI 会推荐选项。

    :::image type="content" source="../media/beginners-css-add5.msft.png" alt-text="键入&quot;color&quot;。" lightbox="../media/beginners-css-add5.msft.png":::

1.  键入 `magenta` 并选择 `Enter`。  联系人页面上的所有文本现在都为洋红色。

    :::image type="content" source="../media/beginners-css-add6.msft.png" alt-text="键入&quot;洋红色&quot;。" lightbox="../media/beginners-css-add6.msft.png":::

### <a name="edit-a-declaration-in-devtools"></a>在 DevTools 中编辑声明

在 DevTools 中编辑现有声明

1.  选择 旁边的洋红色正方形 `magenta` 。  将弹出一个颜色选取器。

    :::image type="content" source="../media/beginners-css-edit1.msft.png" alt-text="颜色选取器。" lightbox="../media/beginners-css-edit1.msft.png":::

1.  使用颜色选取器将字体文本更改为您喜欢的颜色。

    :::image type="content" source="../media/beginners-css-edit2.msft.png" alt-text="使用颜色选取器将字体颜色更改为紫色。" lightbox="../media/beginners-css-edit2.msft.png":::

### <a name="add-a-new-ruleset-in-devtools"></a>在 DevTools 中添加新规则集

在 DevTools 中添加新规则集

1.  Select **New Style Rule** (New Style Rule) which is next to ![ ](../media/new-style-rule-icon.msft.png) **.cls**.  空的规则集将显示为 `a` 选择器。

    :::image type="content" source="../media/beginners-css-rule1.msft.png" alt-text="添加新规则。" lightbox="../media/beginners-css-rule1.msft.png":::

1.  将`a`替换为`a:hover`。

    :::image type="content" source="../media/beginners-css-rule2.msft.png" alt-text="将&quot;a&quot;替换为&quot;a：hover&quot;。" lightbox="../media/beginners-css-rule2.msft.png":::

    `:hover` 是 **伪类**。  对可能进入特殊状态的样式元素使用伪类。  例如，仅在将鼠标悬停在元素上时 `a:hover` ，样式才 `<a>` 生效。

1.  选择括号之间的空白区域以添加新声明。

1.  键入 `background-color` 声明名称并选择 `Enter`。

    :::image type="content" source="../media/beginners-css-rule3.msft.png" alt-text="键入&quot;background-color&quot;。" lightbox="../media/beginners-css-rule3.msft.png":::

1.  键入 `green` 声明值并选择 `Enter`。

    :::image type="content" source="../media/beginners-css-rule4.msft.png" alt-text="键入&quot;green&quot;。" lightbox="../media/beginners-css-rule4.msft.png":::

1.  将鼠标悬停在"主页 **"链接** 上。  链接的背景变为绿色。

    :::image type="content" source="../media/beginners-css-rule5.msft.png" alt-text="将鼠标悬停在&quot;主页&quot;链接上以显示其绿色背景。" lightbox="../media/beginners-css-rule5.msft.png":::


<!-- ====================================================================== -->
## <a name="reuse-styles-across-pages-with-external-stylesheets"></a>使用外部样式表跨页面重用样式

在上一步中，您将以下代码段作为内部样式表添加到 `contact.html`。

```html
...
    ...
        ...
        <style>
            li a, h1 {
              font-family: 'Courier New', Courier, Serif;
            }
        </style>
        ...
    ...
...
```

如果要以相同方式设置 `index.html` 样式，该做什么？  如果您具有大量要应用样式的页面，应怎么做？  您必须将内部样式表复制并粘贴到您的网站上的每个网页中。  以下步骤介绍如何添加外部样式 **表** ，以允许您编写 CSS 一次，并应用到多个页面。

1.  首先，刷新实时选项卡以删除你在 DevTools 中所做的更改。

    :::image type="content" source="../media/beginners-css-external1.msft.png" alt-text=" 刷新页面后，在 DevTools 中所做的更改将消失。" lightbox="../media/beginners-css-external1.msft.png":::

1.  返回到编辑器选项卡 **并** 打开 `contact.html`。

    :::image type="content" source="../media/beginners-css-external2.msft.png" alt-text="contact.html。" lightbox="../media/beginners-css-external2.msft.png":::

1.  删除`<style>`和`</style>` 之间的所有内容，包括`<style>`和`</style>`。

    :::image type="content" source="../media/beginners-css-external3.msft.png" alt-text="样式标记已删除。" lightbox="../media/beginners-css-external3.msft.png":::

1.  打开 `index.html` 并从 标记 `style="background-color: aliceblue;"` 中删除 `<nav>`。  现在，您已删除之前添加到网站的所有 CSS。

    :::image type="content" source="../media/beginners-css-external4.msft.png" alt-text="内联样式已从导航元素中删除。" lightbox="../media/beginners-css-external4.msft.png":::

1.  选择 **"新建文件"。**

    :::image type="content" source="../media/beginners-css-external5.msft.png" alt-text="&quot;新建文件&quot;对话框。" lightbox="../media/beginners-css-external5.msft.png":::

1.  将 `cool-file.js` 替换为 `style.css` ，然后选择"**添加文件"。**

    :::image type="content" source="../media/beginners-css-external6.msft.png" alt-text="类型 style.css。" lightbox="../media/beginners-css-external6.msft.png":::

1.  将以下代码段添加到 `style.css` 你的文件。

    ```css
    li a, h1 {
      font-family: 'Courier New', Courier, Serif;
    }
    a:hover {
      background-color: green;
    }
    nav {
      background-color: aliceblue;
    }
    ```

    :::image type="content" source="../media/beginners-css-external7.msft.png" alt-text="将代码添加到 style.css。" lightbox="../media/beginners-css-external7.msft.png":::

    确保已创建外部样式表。 HTML 不知道它是否存在。

1.  打开 `index.html`。
1.  添加到 `<link rel="stylesheet" href="style.css">` HTML。

    ```html
    <head>
        ...
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="style.css">
    </head>
    ```

    :::image type="content" source="../media/beginners-css-external8.msft.png" alt-text="链接到 style.css。" lightbox="../media/beginners-css-external8.msft.png":::

1.  打开 `contact.html` 文件，并添加链接。

    :::image type="content" source="../media/beginners-css-external9.msft.png" alt-text="链接到 contact.html 中的 style.css。" lightbox="../media/beginners-css-external9.msft.png":::

1.  导航到实时 **选项卡**。 主页上一节和蓝色导航部分现在具有相同的字体。

    :::image type="content" source="../media/beginners-css-external10.msft.png" alt-text="主页。" lightbox="../media/beginners-css-external10.msft.png":::

1.  选择 **"联系人** "链接以导航到联系人页面。  联系人页面的格式与主页的格式相同。

    :::image type="content" source="../media/beginners-css-external11.msft.png" alt-text="联系人页面。" lightbox="../media/beginners-css-external11.msft.png":::


<!-- ====================================================================== -->
## <a name="use-a-css-framework"></a>使用 CSS 框架

**CSS 框架** 是由其他开发人员构建的样式集合，可更轻松地创建极具吸引力的网站。  框架提供了一组可以在页面元素上使用的样式，而不是自己定义样式。

执行以下步骤以将 Bootstrap CSS 框架添加到你的页面。

1.  复制以下代码：

    ```html
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css">
    ```

1.  打开编辑选项卡，然后将代码粘贴到 `contact.html` 中。

    :::image type="content" source="../media/beginners-css-framework1.msft.png" alt-text="链接到 contact.html 中的框架。" lightbox="../media/beginners-css-framework1.msft.png":::

1.  打开 `index.html` 文件，并添加代码。

    :::image type="content" source="../media/beginners-css-framework2.msft.png" alt-text="链接到 index.html 中的框架。" lightbox="../media/beginners-css-framework2.msft.png":::

1.  返回到实时选项卡以查看更改。  虽然 `<nav>` 元素的背景色和 `<li>` 和 `<a>` 的字体相同，但其他元素的字体已更改。

    :::image type="content" source="../media/beginners-css-framework3.msft.png" alt-text="主页上的一些字体由于框架而更改。" lightbox="../media/beginners-css-framework3.msft.png":::

### <a name="use-a-class"></a>使用类

在上一部分中，你向网页添加了 Bootstrap，这更改了网站上某些元素的字体。  CSS 框架可帮助你使用非常少的代码对页面进行重大更改。  执行以下步骤以使用 Bootstrap 的类之一更改标头。

1.  复制以下代码段。

    ```html
    class="jumbotron jumbotron-fluid"
    ```

1.  将前面的代码段添加到 `<header>` 中的 标记 `index.html`。

    :::image type="content" source="../media/beginners-css-jumbotron1.msft.png" alt-text="在 index.html 中添加类。" lightbox="../media/beginners-css-jumbotron1.msft.png":::

1.  将代码添加到 `<header>` 中的 标记 `contact.html`。

    :::image type="content" source="../media/beginners-css-jumbotron2.msft.png" alt-text="在 contact.html 中添加类。" lightbox="../media/beginners-css-jumbotron2.msft.png":::

1.  在实时选项卡中查看更改。 标题周围有一个大的灰色框。

    :::image type="content" source="../media/beginners-css-jumbotron3.msft.png" alt-text="页眉的周围现在有一个大的灰色框。" lightbox="../media/beginners-css-jumbotron3.msft.png":::

### <a name="understand-classes"></a>了解类

类使你可以将样式集合分配给任意元素。  将下列代码片段设置为 `<header>` 属性后，将多个样式应用到 `class` 元素 `jumbotron`。

```css
.jumbotron {
  padding: 2rem 1rem;
  margin-bottom: 2rem;
  background-color: #e9ecef;
  border-radius: .3rem;
}
```

类的一个优点是，它允许您将样式应用到所需的任何元素。  例如，假设你想要将某些元素的背景色设置为 `<p>` 紫色，而不是所有 `<p>` 元素。  使用以下代码段定义类中的样式。

```css
.my-class-name {
  background-color: purple;
}
```

接下来，将类仅 `<p>` 应用于要设置样式的元素。

```html
<p>The text is not purple.</p>
<p class="my-class-name">The text is purple.</p>
<p>The text is not purple.</p>
<p class="my-class-name">The text is purple.</p>
```

### <a name="align-elements"></a>对齐元素

完成以下步骤以使用对对齐元素有用的其他 Bootstrap 类。

1.  返回到编辑器选项卡并打开 `index.html`。
1.  添加到 `class="container-fluid"` 标记 `<body>`。

    :::image type="content" source="../media/beginners-css-align1.msft.png" alt-text="添加容器流类。" lightbox="../media/beginners-css-align1.msft.png":::

1.  在 `<nav>` 中 `<main>` 包 `<div class="row">`元素。  请确保在 后 `</div>` 添加 `</main>` 以正确关闭新标记。

    :::image type="content" source="../media/beginners-css-align2.msft.png" alt-text="添加行。" lightbox="../media/beginners-css-align2.msft.png":::

1.  向 `class="col-3"` 标记添加 `<nav>` ， `class="col-9"` 添加到 `<main>` 标记。

    :::image type="content" source="../media/beginners-css-align3.msft.png" alt-text="添加 col-3 和 col-9 类。" lightbox="../media/beginners-css-align3.msft.png":::

1.  在实时选项卡中查看更改。

    :::image type="content" source="../media/beginners-css-align4.msft.png" alt-text="导航内容现在位于主内容的左侧。" lightbox="../media/beginners-css-align4.msft.png":::


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

恭喜！你已完成！

*   更好地进行 Web 开发的最好办法就是构建更多网站。  不要担心中断工作。  请一直玩得有趣，并尽可能学习。
*   若要了解有关设置网页样式的信息，请导航到 CSS [简介](https://developer.mozilla.org/docs/Learn/CSS/Introduction_to_CSS)。
*   若要详细了解如何在 DevTools 中试验 CSS，请导航到入门[查看和更改 CSS。](../css/index.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/beginners/css) ，由位于 Chrome DevTools (的 [Katherine Writer](https://developers.google.com/web/resources/contributors#katherine-jackson)) 。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
