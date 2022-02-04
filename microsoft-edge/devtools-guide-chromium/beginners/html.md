---
title: HTML 和 DOM 入门
description: HTML 和 DOM 入门。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/06/2021
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
# <a name="get-started-with-html-and-the-dom"></a>HTML 和 DOM 入门

这是一系列教程中第一个介绍 Web 开发基础知识的教程。 了解一组名为 Microsoft Edge DevTools 的 Web 开发人员工具，这些工具将提高工作效率。

本教程介绍 HTML 和 [文档对象模型](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) （DOM）。 HTML 是 Web 开发的核心技术之一。 它是控制网页结构和内容的语言。 DOM 还与网页的结构和内容相关，我们稍后将了解相关内容。


<!-- ====================================================================== -->
## <a name="goals"></a>目标

你将通过构建网站来学习 Web 开发。  完成 **DevTools for Beginners** 系列中的所有教程后，完成的网站将如下图所示。

:::image type="content" source="media/beginners-html-finished.msft.png" alt-text="已完成的网站。" lightbox="media/beginners-html-finished.msft.png":::

本教程结束时，你将了解以下概念：

*  HTML 和 DOM 如何创建网页上显示的内容。
*  Microsoft Edge DevTools 如何帮助你试验 HTML 和 DOM 更改。
*  HTML 和 DOM 的区别。

你还将具有一个工作网站。  可以使用该网站托管简历或博客。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

执行本教程之前：

*  如果不熟悉 HTML，请阅读 [HTML 文档入门](https://developer.mozilla.org/docs/Learn/HTML/Introduction_to_HTML/Getting_started)。

*  下载 [Microsoft Edge](https://www.microsoftedgeinsider.com) Web 浏览器。  本教程使用一组内置于 Microsoft Edge 中的 Web 开发工具（称为 Microsoft Edge DevTools）。


<!-- ====================================================================== -->
## <a name="set-up-your-code"></a>设置代码

你将在 Glitch 联机代码编辑器中构建一个网站。

1. 打开[源代码](https://glitch.com/edit/#!/alluring-shock?path=index.html)。 在本教程中，此选项卡称为" **编辑器"** 选项卡。

   :::image type="content" source="media/beginners-html-setup1.msft.png" alt-text="编辑器选项卡。" lightbox="media/beginners-html-setup1.msft.png":::

1. 选择 **"诱人-休克**"。 “**项目选项**”菜单将打开。

   :::image type="content" source="media/beginners-html-setup2.msft.png" alt-text="&quot;Project 选项&quot;菜单。" lightbox="media/beginners-html-setup2.msft.png":::

1. 选择**Remix Project**。 Glitch 创建项目的副本，你可以编辑该项目并随机生成项目的新名称。 内容与之前相同。

   :::image type="content" source="media/beginners-html-setup3.msft.png" alt-text="重新混合的项目。" lightbox="media/beginners-html-setup3.msft.png":::

1. 如果计划完成本系列中的下一教程，请选择使用 Facebook、GitHub 或 Google 帐户 **登录**故障；或向自己发送一个神奇链接。 如果不登录帐户，则关闭编辑器选项卡后无法编辑项目。

1.  > **在新建窗口中**选择**显示**。  将打开一个新选项卡，显示实时页面。  在本教程中，此选项卡称为实时**选项卡**。

   :::image type="content" source="media/beginners-html-setup4.msft.png" alt-text="动态选项卡。" lightbox="media/beginners-html-setup4.msft.png":::


<!-- ====================================================================== -->
## <a name="add-content"></a>添加内容

你的网站需要更多信息。  添加一些内容：

1. 在**编辑器选项卡**，将`<!-- You're "About Me" will go here.  -->`替换`<h1>About Me</h1>`。

    ```html
   <body>
      <p> Your site!</p>
            <main>
               <h1>About Me</h1>
            </main>
    ```

   :::image type="content" source="media/beginners-html-add1.msft.png" alt-text="新代码在编辑器选项卡中突出显示。" lightbox="media/beginners-html-add1.msft.png":::

1. 在**实时选项**卡中查看更改。文本`About Me`在页面上可见。 文本大于周围文本，因为`<h1>`元素表示“标题 1”。 Web 浏览器自动为标题设置更大字体的样式。

   :::image type="content" source="media/beginners-html-add2.msft.png" alt-text="新标题显示在活动选项卡中。" lightbox="media/beginners-html-add2.msft.png":::

1. 返回到**编辑器选项卡中**，在`<h1>About Me</h1>`下面的行插入`<p>I am learning web development. Recent accomplishments:</p>`。

    ```html
   <body>
      <p> Your site!</p>
            <main>
               <h1>About Me</h1>
               <p>I am learning web development. Recent accomplishments:</p>
            </main>
    ```

   :::image type="content" source="media/beginners-html-add3.msft.png" alt-text="更新后的代码在编辑器选项卡中突出显示。" lightbox="media/beginners-html-add3.msft.png":::

1. 在**实时选项卡**中查看更改。

1. 返回到**编辑器选项卡**，使用下面的代码添加你的成就列表。

   ```html
   <p>I am learning web development.  Recent accomplishments:</p>
      <ul>
         <li>Learned how to set up my code in Glitch.</li>
         <li>Added content to my HTML.</li>
         <li>TODO: Learn how to use Microsoft Edge DevTools to experiment with content changes.</li>
         <li>TODO: Learn the difference between HTML and the DOM.</li>
      </ul>
   ```

   :::image type="content" source="media/beginners-html-add4.msft.png" alt-text="更新后的代码还会在编辑器选项卡中突出显示。" lightbox="media/beginners-html-add4.msft.png":::

1. 查看 **实时选项卡** 以确保新内容正确显示。

   :::image type="content" source="media/beginners-html-add5.msft.png" alt-text="新列表在活动选项卡中可见。" lightbox="media/beginners-html-add5.msft.png":::


<!-- ====================================================================== -->
## <a name="experiment-with-content-changes-in-microsoft-edge-devtools"></a>在 Microsoft Edge 开发人员工具中试验内容更改

如果要开发包含大量 HTML 的页面，在编辑器选项卡和实时选项卡之间来回切换查看更改将变得繁琐。 Microsoft Edge 开发人员工具有助于尝试内容更改，而无需离开实时**选项卡**。

### <a name="learn-the-difference-between-html-and-the-dom"></a>了解 HTML 和 DOM 的区别

在编辑 Microsoft Edge 开发人员工具内容之前，让我们了解 HTML 和 DOM 的区别。 继续执行以下步骤以从示例中学习。

1. 导航到 **实时选项卡**。在页面底部，显示文本 `A new element!?!` 。

    <!--
      :::image type="content" source="media/beginners-html-dom1.msft.png" alt-text="At the bottom of the page, the text 'A new element!?!' is displayed." lightbox="media/beginners-html-dom1.msft.png":::
    -->

1. 打开**编辑器选项卡** ，并尝试在`index.html`中查找文本。 文本不会在此视图中显示。

    <!--
      :::image type="content" source="media/beginners-html-dom2.msft.png" alt-text="The mystery text 'A new element!?!' isn't found in index.html." lightbox="media/beginners-html-dom2.msft.png":::
    -->

1. 打开活动**选项卡，** 右键单击 `A new element!?!`，**然后选择检查。**

   :::image type="content" source="media/beginners-html-dom3.msft.png" alt-text="检查一些文本。" lightbox="media/beginners-html-dom3.msft.png":::

   DevTools 将随页面一起打开。  `<div>A new element!?!</div>` 突出显示。  尽管 DevTools 中的此结构类似于 HTML，但它实际上是 **DOM 树**。

   :::image type="content" source="media/beginners-html-dom4.msft.png" alt-text="DevTools 与页面一起打开。" lightbox="media/beginners-html-dom4.msft.png":::

加载页面时，浏览器使用 HTML 创建页面的初始内容。  DOM 表示页面的当前内容，该内容可能会随时间而变化。

由于 HTML 底部的`<script src="new.js"></script>`标记，内容`<div>A new element!?!</div>`将添加到页面。  此标记会导致某些 JavaScript 代码运行。 在[稍后的教程](../javascript/index.md)中了解有关 JavaScript 的更多内容。

现在，将其视为可以更改页面内容的脚本语言。  在这种情况下，JavaScript 代码将`<div>A new element!?!</div>`添加到你的页面。 这就是此文本显示在**实时**选项卡中，而不是 HTML 中的原因。

### <a name="edit-the-dom"></a>编辑 DOM

若要在不离开活动选项卡的情况下快速试验内容更改：

1. 在 DevTools 中，右键单击 `Your site!`，然后选择"编辑 **为 HTML"**。

1. 将`<p>Your site!</p>`替换为下面的代码。

   ```html
   <header>
      <p><b>Welcome to my site!</b></p>
      <button>Download my resume</button>
   </header>
   ```

   :::image type="content" source="media/beginners-html-edit2.msft.png" alt-text="将节点更新为 HTML。" lightbox="media/beginners-html-edit2.msft.png":::

1. 按`Control`+`Enter` (Windows、Linux) 或 `Command`+`Enter` (macOS) 保存更改，或在框外选择。 更改将自动显示在页面实时视图中。 文本 `Your site!` 已替换为新内容。

   :::image type="content" source="media/beginners-html-edit3.msft.png" alt-text="新内容会立即显示在页面上。" lightbox="media/beginners-html-edit3.msft.png":::

此工作流仅适用于试验内容更改。  如果刷新页面或关闭选项卡，更改将丢失。  如果要保存更改，请手动将代码复制到 HTML 文件中。 接下来的几节将介绍从 DOM 树更改内容的更多方法。


<!-- ====================================================================== -->
## <a name="reorder-nodes"></a>对节点重新排序

还可以更改 DOM 节点的顺序。 例如，在网页上，导航菜单靠近底部。

将导航菜单移到顶部：

1. 在 DevTools 的** DOM 树**中查找`<nav>`节点。

   :::image type="content" source="media/beginners-html-reorder1.msft.png" alt-text="导航节点在 DevTools 中突出显示。" lightbox="media/beginners-html-reorder1.msft.png":::

1. 将`<nav>`节点拖动到顶部，以便该节点是`<body>`节点后的第一个子节点。

   :::image type="content" source="media/beginners-html-reorder3.msft.png" alt-text="导航节点位于页面顶部。" lightbox="media/beginners-html-reorder3.msft.png":::

### <a name="delete-a-node"></a>删除节点

从 DOM 树中删除节点：

1. 在** DOM 树**中，选择 `<div>A new element!?!</div>`。 DevTools 突出显示节点。

1. 按 `Delete`。  将从 DOM 树中删除`<div>A new element!?!</div>`节点。

   :::image type="content" source="media/beginners-html-delete2.msft.png" alt-text="节点已删除。" lightbox="media/beginners-html-delete2.msft.png":::


<!-- ====================================================================== -->
## <a name="copy-your-changes"></a>复制更改

你已接近完成。 你在 DevTools 中对页面进行了一些更改，但它们不会保存到源代码中。

1. 刷新**实时选项卡**。在 DOM 树中所做的更改将消失。 具体而言，文本 `Your site!` 返回页首，文本 `A new element!?!` 返回页面底部。

   :::image type="content" source="media/beginners-html-copy1.msft.png" alt-text="你所做的更改已消失。" lightbox="media/beginners-html-copy1.msft.png":::

1. 复制以下代码：

   ```html
   <!DOCTYPE html>
   <html lang="en">
      <head>
         <meta charset="utf-8">
         <meta http-equiv="X-UA-Compatible" content="IE=edge">
         <meta name="viewport" content="width=device-width, initial-scale=1">
      </head>
      <body>
         <header>
               <p>Welcome to my site!</p>
         </header>
         <nav>
               <ul>
                  <li><a href="/">Home</a></li>
                  <li><a href="/contact.html">Contact</a></li>
               </ul>
         </nav>
         <main>
               <h1>About Me</h1>
               <p>I am learning web development.  Recent accomplishments:</p>
               <ul>
                  <li>Learned how to set up my code in Glitch.</li>
                  <li>Added content to my HTML.</li>
                  <li>Learned how to use Microsoft Edge DevTools to experiment with content changes.</li>
                  <li>Learned the difference between HTML and the DOM.</li>
               </ul>
         </main>
      </body>
   </html>
   ```
    
1. 返回到**编辑器选项卡** ，将`index.html`文件内容替换为复制的代码。

   :::image type="content" source="media/beginners-html-copy2.msft.png" alt-text="文件index.html的外观。" lightbox="media/beginners-html-copy2.msft.png":::


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

*  完成此系列中的下一教程 [CSS](css.md) 入门，了解如何设置页面样式，以及如何在 DevTools 中试验样式Microsoft Edge更改。

*  阅读[ DOM 简介](https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction)，详细了解 DOM。

*  查看诸如 Web 开发 [简介等](https://www.coursera.org/learn/web-development)课程，以获得有关 Web 开发的其他动手体验。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 在https://developers.google.com/web/tools/chrome-devtools/beginners/html找到原始页面 <!-- 404 now --> 由 [Katherine 并](https://developers.google.com/web/resources/contributors#katherine-jackson) 创作（技术编写员，Chrome DevTools）。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
