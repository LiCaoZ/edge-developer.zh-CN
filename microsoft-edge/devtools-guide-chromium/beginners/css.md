---
title: CSS 入门
description: 用于开始使用 CSS 的 DevTools 教程。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/26/2021
ms.openlocfilehash: cc18effd31e61bbda78fce00b8c485bfd7ec8526
ms.sourcegitcommit: 855d6986920b5d231e68a453bc8e5b31180f3026
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2022
ms.locfileid: "12506783"
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
# <a name="get-started-with-css"></a>CSS 入门

本教程介绍如何使用 CSS 设置网页样式。  此外，还了解如何使用 Microsoft Edge DevTools 试验 CSS 更改。

本文是一系列教程的一部分，这些教程介绍 Web 开发和开发工具Microsoft Edge的基础知识。  通过实际构建自己的网站，可以获得实践体验。  完成本教程之前，无需完成前面的教程。

本教程专为绝对初学者设计，专注于 Web 开发 **的** 基础知识和使用 DevTools 进行 CSS 测试的基础知识。  如果想要仅关注 DevTools 的教程，请参阅[开始查看和更改 CSS](../css/index.md)。

在教程的开头，网站应如下图所示：

:::image type="content" source="../media/beginners-css-intro1.msft.png" alt-text="网站当前的外观。" lightbox="../media/beginners-css-intro1.msft.png":::

完成本教程后，网站应如下图所示：

:::image type="content" source="../media/beginners-css-intro2.msft.png" alt-text="本教程末尾的网站应如下所示。" lightbox="../media/beginners-css-intro2.msft.png":::


<!-- ====================================================================== -->
## <a name="goals"></a>目标

请遵循本教程，更好地了解以下概念和任务：

*  如何使用 CSS 设置网页样式。
*  如何使用 Microsoft Edge DevTools 对 CSS 进行试验。
*  CSS 和 CSS 框架的区别。

你正在构建一个真正的网站。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

在执行本教程之前：

*  使用 [HTML 和 DOM](html.md) 演练教程开始，或确保你已了解 HTML 和 DOM。
*  下载 [Microsoft Edge](https://www.microsoftedgeinsider.com) Web 浏览器。  以下教程使用一组内置于 Microsoft Edge 中的 Web 开发工具（称为 Microsoft Edge DevTools）。


<!-- ====================================================================== -->
## <a name="set-up-your-code"></a>设置代码

若要创建站点，请先执行以下步骤来设置代码。

> [!NOTE]
> 如果已完成系列的第一个教程，请跳到下一部分。  继续使用上一教程中的代码，[开始 HTML 和 DOM](html.md)。

1. 打开[源代码](https://glitch.com/edit/#!/cooked-amphibian?path=index.html)。  当前选择的浏览器选项 **卡称为“编辑”选项卡**。

   :::image type="content" source="../media/beginners-css-setup1.msft.png" alt-text="编辑选项卡。" lightbox="../media/beginners-css-setup1.msft.png":::

1. 选择 **熟食两栖动物**。  弹出一个菜单。

   :::image type="content" source="../media/beginners-css-setup2.msft.png" alt-text="&quot;项目选项&quot;菜单。" lightbox="../media/beginners-css-setup2.msft.png":::

1. 选择**Remix Project**。  Glitch 创建可编辑的项目副本。  Glitch 会为新项目生成随机名称。

1. 选择 **“显示”** ，然后选择 **“新建窗口**”。  打开另一个选项卡，其中显示网站实时视图。  当前选择的浏览器选项 **卡称为“实时”选项卡**。

   :::image type="content" source="../media/beginners-css-setup3.msft.png" alt-text="实时选项卡。" lightbox="../media/beginners-css-setup3.msft.png":::


<!-- ====================================================================== -->
## <a name="understand-css"></a>了解 CSS

**CSS** 是一种控制网页布局和样式的计算机语言。  下图是带边框的段落。

:::image type="content" source="../media/beginners-css-red_paragraph.msft.png" alt-text="文本已使用 CSS 设置样式。" lightbox="../media/beginners-css-red_paragraph.msft.png":::

下面是用于在上图中创建段落的 HTML 和 CSS 代码：

```html
<p style="border: 1px dashed red; padding: 5px;">
    This has been styled with CSS.
</p>
```

HTML 属性 `style="border: 1px dashed red; padding: 5px;"` 可能看起来很新。  其余部分看起来应该很熟悉。  如果没有，请先使用 [HTML 和 DOM 完成开始](html.md)，然后再尝试以下部分。


<!-- ====================================================================== -->
## <a name="add-inline-styles"></a>添加内联样式

可以使用 **内联样式** 将样式应用于单个元素。

1. 返回到编辑选项卡并打开`index.html`。

   :::image type="content" source="../media/beginners-css-inline1.msft.png" alt-text="在编辑选项卡中打开index.html。" lightbox="../media/beginners-css-inline1.msft.png":::

1. 在元素中`<nav>`添加属性`style="background-color: aliceblue;"`。

   在下面的代码中，第四行代码是唯一需要更改的代码。  此处会显示其他代码行，以帮助你将新属性放在正确的位置。

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

1. 若要显示更改，请导航到活动 **选项卡**。 分区的背景 `<nav>` 现在为蓝色。

   :::image type="content" source="../media/beginners-css-inline2.msft.png" alt-text="“开始”和“联系人”链接后面的背景色现在是蓝色的。" lightbox="../media/beginners-css-inline2.msft.png":::


<!-- ====================================================================== -->
## <a name="reuse-styles-on-a-single-page-with-internal-stylesheets"></a>使用内部样式表在单个页面上重复使用样式

在以前的代码中，内联样式将样式应用于单 `<p>` 个标记：

```html
<p style="border: 1px dashed red; padding: 5px;">
    This has been styled with CSS.
</p>
```

如果您希望网页上的所有元素都以相同的方式设置样式 `<p>` ，应该如何？  必须将代码复制并粘贴到站点上的每一个 `<p>` 标记中，这需要花费大量时间和精力。  如果需要进行编辑，则必须再次更改每个标记。  相反，在后续步骤中，可以使用 **内部样式表** 编写 CSS 一次，以便它适用于多个元素。

1. 在实时选项卡中，单击 **“联系人** ”转到联系人页面。  请注意 **“开始** 和 **联系人”** 链接的字体。

   :::image type="content" source="../media/beginners-css-internal1.msft.png" alt-text="“联系人”页。" lightbox="../media/beginners-css-internal1.msft.png":::

1. 在编辑器 **选项卡中，** 打开 `contact.html`。

1. 将以下代码添加到 `contact.html`。

   以行开头 `<style>` 和结尾 `</style>` 是需要添加的行。  此处会显示另一个代码，以便你知道将新代码放到何处。

   ```html
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
    ```

1. 返回到实时 **选项卡**。

1. 单击 **“联系人** ”返回到联系人页面。  请注意，“ **开始** ”和“ **联系人”** 链接的字体已更改：

   :::image type="content" source="../media/beginners-css-internal2.msft.png" alt-text="“开始”和“联系人”链接的字体已更改。" lightbox="../media/beginners-css-internal2.msft.png":::

### <a name="understand-internal-stylesheets"></a>了解内部样式表

内部样式表使用选择器应用 **样式**。  选择器是可应用于一个或多个 HTML 元素的模式。  前面的代码片段添加了以下样式：

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

| 部分 | 示例 | 说明 |
| --- | --- | --- |
| **属性** | `font-family` | 该属性描述应更改元素的样式。 |
| **value** | `'Courier New', Courier, serif` | 该值准确描述了元素的样式应该如何更改。 |

例如， `font-family: 'Courier New', Courier, serif` 为浏览器提供以下指令："将匹配模式的元素的字体设置为 `li a` `'Courier New'`。  如果该字体不可用，请使用 `Courier`。  如果这也不可用，请使用 `serif`。”

### <a name="add-multiple-selectors-to-a-ruleset"></a>向规则集添加多个选择器

以下 CSS 代码称为 **规则集**。

```css
li a {
  font-family: 'Courier New', Courier, monospace;
}
```

以下步骤介绍如何使用逗号将多个选择器添加到规则集。

1. 在编辑器 **选项卡中，** 打开 `contact.html`。

1. 之后 `li a`，键入 `, h1`。

   ```html
   <style>
       li a, h1 {
         font-family: 'Courier New', Courier, Serif;
       }
   </style>
   ```

    前面的代码段指示浏览器设置元素样式的方式与设置与模式 `<h1>` 匹配的元素的样式相同 `li a`。

1. 导航到实时 **选项卡**。

1. 单击 **“联系人** ”链接可返回到联系人页面。  现在， **联系我！** 具有与导航链接相同的字体：

   :::image type="content" source="../media/beginners-css-multiple1.msft.png" alt-text="文本“与我联系！ 现在具有与“开始”和“联系人”链接相同的字体。" lightbox="../media/beginners-css-multiple1.msft.png":::


<!-- ====================================================================== -->
## <a name="experiment-with-devtools"></a>使用 DevTools 进行试验

当你继续成为 Web 开发方面的专家时，你可能会发现 CSS 很复杂。  可以编写一些不显示所需内容的代码。  Microsoft Edge DevTools 可通过实时在页面中显示更改来轻松进行试验。

### <a name="add-a-declaration-to-an-existing-ruleset-in-devtools"></a>将声明添加到 DevTools 中的现有规则集

若要将声明添加到现有规则集，请执行以下操作：

1. 右键单击 **“开始** ”链接，然后选择 **“检查**”。

   :::image type="content" source="../media/beginners-css-add1.msft.png" alt-text="检查“主页”链接。" lightbox="../media/beginners-css-add1.msft.png":::

   DevTools 将在页面旁边打开。  代表"主页"链接的代码在 DOM 树中突出显示 `<a href="/">Home</a>` 为蓝色。  本教程[开始 HTML 和 DOM](html.md) 时，应熟悉代码片段和预览。

   在下图中 `font-family: 'Courier New', Courier, serif` ，之前添加到 `contact.html` 的声明显示在 DOM 树下方 **的“样式”** 选项卡中：

   :::image type="content" source="../media/beginners-css-add2.msft.png" alt-text="“样式”选项卡位于 DOM 树下方。" lightbox="../media/beginners-css-add2.msft.png":::

   如果 DevTools 窗口很宽，则“ **样式”** 选项卡位于 DOM 树的右侧：

   :::image type="content" source="../media/beginners-css-add3.msft.png" alt-text="“样式”选项卡位于 DOM 树的右侧。" lightbox="../media/beginners-css-add3.msft.png":::

1. 选择下面 `font-family: 'Courier New', Courier, Serif` 的空行以添加新声明：

   :::image type="content" source="../media/beginners-css-add4.msft.png" alt-text="添加新声明。" lightbox="../media/beginners-css-add4.msft.png":::

1. 键入 **颜色** ，然后按 `Enter`。  在键入时，自动完成 UI 会建议选项：

   :::image type="content" source="../media/beginners-css-add5.msft.png" alt-text="键入“color”。" lightbox="../media/beginners-css-add5.msft.png":::

1. 键入 **洋红色** ，然后按 `Enter`。  联系人页面上的所有文本现在是洋红色：

   :::image type="content" source="../media/beginners-css-add6.msft.png" alt-text="键入“magenta”。" lightbox="../media/beginners-css-add6.msft.png":::

### <a name="edit-a-declaration-in-devtools"></a>在 DevTools 中编辑声明

若要编辑 DevTools 中的现有声明，请执行以下操作：

1. 选择旁边 `magenta`的洋红色正方形。  弹出颜色选取器：

   :::image type="content" source="../media/beginners-css-edit1.msft.png" alt-text="颜色选取器。" lightbox="../media/beginners-css-edit1.msft.png":::

1. 使用颜色选取器将字体文本更改为你喜欢的颜色：

   :::image type="content" source="../media/beginners-css-edit2.msft.png" alt-text="使用颜色选取器将字体颜色更改为紫色。" lightbox="../media/beginners-css-edit2.msft.png":::

### <a name="add-a-new-ruleset-in-devtools"></a>在 DevTools 中添加新规则集

若要在 DevTools 中添加新规则集，请执行以下操作：

1. 选择 **新样式规则** (![新样式规则。](../media/new-style-rule-icon.msft.png)) **.cls** 旁边。  空的规则集将显示为 `a` 选择器。

   :::image type="content" source="../media/beginners-css-rule1.msft.png" alt-text="添加新规则。" lightbox="../media/beginners-css-rule1.msft.png":::

1. 将`a`替换为`a:hover`。

   :::image type="content" source="../media/beginners-css-rule2.msft.png" alt-text="将“a”替换为“a：hover”。" lightbox="../media/beginners-css-rule2.msft.png":::

   `:hover` 是 **伪类**。  对可能进入特殊状态的样式元素使用伪类。  例如，仅当 `a:hover` 将鼠标悬停在元素上 `<a>` 时，样式才会生效。

1. 单击方括号之间的空区域以添加新声明。

1. 为声明名称键入 **背景色** 并按下 `Enter`。

   :::image type="content" source="../media/beginners-css-rule3.msft.png" alt-text="键入“background-color”。" lightbox="../media/beginners-css-rule3.msft.png":::

1. 为声明值键入**绿色**并按。`Enter`

   :::image type="content" source="../media/beginners-css-rule4.msft.png" alt-text="键入“green”。" lightbox="../media/beginners-css-rule4.msft.png":::

1. 将鼠标悬停在"主页 **"链接** 上。  链接的背景变为绿色。

   :::image type="content" source="../media/beginners-css-rule5.msft.png" alt-text="将鼠标悬停在“主页”链接上以显示其绿色背景。" lightbox="../media/beginners-css-rule5.msft.png":::


<!-- ====================================================================== -->
## <a name="reuse-styles-across-pages-with-external-stylesheets"></a>使用外部样式表跨页面重复使用样式

在上一步中，将以下代码添加为内部样式表，如下 `contact.html`所示：

```html
<style>
    li a, h1 {
        font-family: 'Courier New', Courier, Serif;
    }
</style>
```

如果要以相同方式设置 `index.html` 样式，该做什么？  如果您具有大量要应用样式的页面，应怎么做？  必须将内部样式表复制并粘贴到网站上的每一个网页中。  以下步骤介绍如何添加 **外部样式表** ，以便一次编写 CSS 并将其应用到多个页面。

1. 首先，刷新实时选项卡以删除你在 DevTools 中所做的更改。

   :::image type="content" source="../media/beginners-css-external1.msft.png" alt-text=" 刷新页面后，DevTools 中所做的更改将不复存在。" lightbox="../media/beginners-css-external1.msft.png":::

1. 返回到编辑器选项卡 **并** 打开 `contact.html`。

   :::image type="content" source="../media/beginners-css-external2.msft.png" alt-text="contact.html。" lightbox="../media/beginners-css-external2.msft.png":::

1. 删除`<style>`和`</style>` 之间的所有内容，包括`<style>`和`</style>`。

   :::image type="content" source="../media/beginners-css-external3.msft.png" alt-text="已删除样式标记。" lightbox="../media/beginners-css-external3.msft.png":::

1. 打开 `index.html` 并从 标记 `style="background-color: aliceblue;"` 中删除 `<nav>`。  现在，您已删除之前添加到网站的所有 CSS。

   :::image type="content" source="../media/beginners-css-external4.msft.png" alt-text="内联样式已从导航元素中删除。" lightbox="../media/beginners-css-external4.msft.png":::

1. 选择 **“新建文件**”。

   :::image type="content" source="../media/beginners-css-external5.msft.png" alt-text="“新建文件”对话框。" lightbox="../media/beginners-css-external5.msft.png":::

1. 替换 `cool-file.js` 为 `style.css` 并选择 **“添加文件**”。

   :::image type="content" source="../media/beginners-css-external6.msft.png" alt-text="类型 style.css。" lightbox="../media/beginners-css-external6.msft.png":::

1. 将以下代码添加到 `style.css` 文件：

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

   确保已创建外部样式表。 HTML 不知道它存在。

1. 打开 `index.html`。

1. 添加到 `<link rel="stylesheet" href="style.css">` HTML。

   ```html
   <head>
       ...
       <meta name="viewport" content="width=device-width, initial-scale=1">
       <link rel="stylesheet" href="style.css">
   </head>
   ```

   :::image type="content" source="../media/beginners-css-external8.msft.png" alt-text="指向 style.css 的链接。" lightbox="../media/beginners-css-external8.msft.png":::

1. 打开 `contact.html` 文件，并添加链接。

   :::image type="content" source="../media/beginners-css-external9.msft.png" alt-text="链接到 contact.html 中的 style.css。" lightbox="../media/beginners-css-external9.msft.png":::

1. 导航到实时 **选项卡**。 主页上一节和蓝色导航部分现在具有相同的字体。

   :::image type="content" source="../media/beginners-css-external10.msft.png" alt-text="主页。" lightbox="../media/beginners-css-external10.msft.png":::

1. 选择 **“联系人** ”链接以导航到联系人页面。  联系人页面的格式与主页的格式相同。

   :::image type="content" source="../media/beginners-css-external11.msft.png" alt-text="联系人页面。" lightbox="../media/beginners-css-external11.msft.png":::


<!-- ====================================================================== -->
## <a name="use-a-css-framework"></a>使用 CSS 框架

**CSS 框架** 是由其他开发人员构建的样式集合，可更轻松地创建极具吸引力的网站。  框架不自行定义样式，而是提供可用于页面元素的样式集合。

将 Bootstrap CSS 框架添加到页面，如下所示：

1. 复制以下代码：

   ```html
   <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css">
   ```

1. 打开编辑选项卡，然后将代码粘贴到 `contact.html` 中。

   :::image type="content" source="../media/beginners-css-framework1.msft.png" alt-text="链接到contact.html中的框架。" lightbox="../media/beginners-css-framework1.msft.png":::

1. 打开 `index.html` 文件，并添加代码。

   :::image type="content" source="../media/beginners-css-framework2.msft.png" alt-text="链接到index.html中的框架。" lightbox="../media/beginners-css-framework2.msft.png":::

1. 返回到实时选项卡以查看更改。  虽然 `<nav>` 元素的背景色和 `<li>` 和 `<a>` 的字体相同，但其他元素的字体已更改。

   :::image type="content" source="../media/beginners-css-framework3.msft.png" alt-text="主页上的某些字体因框架而更改。" lightbox="../media/beginners-css-framework3.msft.png":::

### <a name="use-a-class"></a>使用类

在上一部分中，你向网页添加了 Bootstrap，这更改了网站上某些元素的字体。  CSS 框架可帮助你使用非常少的代码对页面进行重大更改。  执行以下步骤，使用 Bootstrap 的一个类来更改标头。

1. 复制以下代码：

   ```html
   class="jumbotron jumbotron-fluid"
   ```

1. 在 `index.html`其中，将前面的代码添加到 `<header>` 标记。

   :::image type="content" source="../media/beginners-css-jumbotron1.msft.png" alt-text="在index.html中添加类。" lightbox="../media/beginners-css-jumbotron1.msft.png":::

1. 在 `contact.html`其中，将前面的代码添加到 `<header>` 标记。

   :::image type="content" source="../media/beginners-css-jumbotron2.msft.png" alt-text="在contact.html中添加类。" lightbox="../media/beginners-css-jumbotron2.msft.png":::

1. 在实时选项卡中查看更改。 页眉周围有一个大的灰色框。

   :::image type="content" source="../media/beginners-css-jumbotron3.msft.png" alt-text="标头周围现在有一个大的灰色框。" lightbox="../media/beginners-css-jumbotron3.msft.png":::

### <a name="understand-classes"></a>了解类

类使你可以将样式集合分配给任意元素。  将属性`jumbotron`设置`class`为以下代码后，使用以下代码将`<header>`多个样式应用于元素：

```css
.jumbotron {
  padding: 2rem 1rem;
  margin-bottom: 2rem;
  background-color: #e9ecef;
  border-radius: .3rem;
}
```

类的一个优点是，它允许您将样式应用到所需的任何元素。  例如，假设你想要将某些元素的背景色设置为 `<p>` 紫色，而不是所有 `<p>` 元素。  使用以下代码在类中定义样式：

```css
.my-class-name {
  background-color: purple;
}
```

接下来，仅将类应用到要设置样式的 `<p>` 元素：

```html
<p>The text is not purple.</p>
<p class="my-class-name">The text is purple.</p>
<p>The text is not purple.</p>
<p class="my-class-name">The text is purple.</p>
```

### <a name="align-elements"></a>对齐元素

使用可用于对齐元素的其他 Bootstrap 类，如下所示：

1. 返回到编辑器选项卡并打开 `index.html`。

1. 添加到 `class="container-fluid"` 标记 `<body>`。

   :::image type="content" source="../media/beginners-css-align1.msft.png" alt-text="添加容器流体类。" lightbox="../media/beginners-css-align1.msft.png":::

1. 在 `<nav>` 中 `<main>` 包 `<div class="row">`元素。  请确保放置 `</div>` 后 `</main>` 正确关闭新标记。

   :::image type="content" source="../media/beginners-css-align2.msft.png" alt-text="添加行。" lightbox="../media/beginners-css-align2.msft.png":::

1. 向 `class="col-3"` 标记添加 `<nav>` ， `class="col-9"` 添加到 `<main>` 标记。

   :::image type="content" source="../media/beginners-css-align3.msft.png" alt-text="添加 col-3 和 col-9 类。" lightbox="../media/beginners-css-align3.msft.png":::

1. 在实时选项卡中查看更改。

   :::image type="content" source="../media/beginners-css-align4.msft.png" alt-text="导航内容现在位于主内容的左侧。" lightbox="../media/beginners-css-align4.msft.png":::


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

恭喜你，你完了！

*  更好地进行 Web 开发的最好办法就是构建更多网站。  不要担心破坏的东西。  请一直玩得有趣，并尽可能学习。

*  若要了解有关设置网页样式的详细信息，请参阅 [CSS 简介](https://developer.mozilla.org/docs/Learn/CSS/Introduction_to_CSS)。

*  若要详细了解如何在 DevTools 中试验 CSS，请[参阅开始查看和更改 CSS](../css/index.md)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面是由[凯瑟琳杰克逊](https://developers.google.com/web/resources/contributors#katherine-jackson) (技术作家实习生，Chrome DevTools) 找到`https://developers.google.com/web/tools/chrome-devtools/beginners/css`和创作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
