---
title: 使用控制台与 DOM 交互
description: 如何使用控制台工具与浏览器中的当前网页进行交互。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
ms.openlocfilehash: b0938e693e18e840df1720a7346be9cf6bf26d02
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431380"
---
# <a name="interact-with-the-dom-using-the-console"></a>使用控制台与 DOM 交互

**控制台**工具是在浏览器中与网页交互的一种很好的方法。<!-- todo: add intro explanation -->  控制台 **与** Inspect 工具的脚本环境 [版本类似](../css/inspect.md)。<!-- todo: add intro explanation -->


<!-- ====================================================================== -->
## <a name="read-from-the-dom"></a>从 DOM 读取

引用网页的标题：

1. 打开 DevTools **控制台**。  若要从网页中执行此操作，可以按 `Ctrl`++`Shift``J` (Windows、Linux) 或`J` `Command`+`Option`+ (macOS) 。

1. 在控制台中键入或粘贴以下 **代码**，然后按 `Enter`：

   ```javascript
   document.querySelector('header')
   ```

   :::image type="content" source="../media/console-dom-get-reference.msft.png" alt-text="若要在控制台中获取对标头的引用，请使用&quot;document.querySelector&quot;。" lightbox="../media/console-dom-get-reference.msft.png":::

1. 在控制台 **中**，将鼠标悬停在生成的 HTML `<header>` 元素上，或按 `Shift`+`Tab`。  在呈现的网页中，DevTools 突出显示标题：

   :::image type="content" source="../media/console-dom-highlight-element.msft.png" alt-text="DevTools 突出显示你在控制台中选择的部分。" lightbox="../media/console-dom-highlight-element.msft.png":::


<!-- ====================================================================== -->
## <a name="manipulate-the-dom"></a>操作 DOM

可以从控制台操作 **网页，如下所示**。  本示例使用控制台在 DOM 中设置一个值，以影响网页样式：在页眉周围添加绿色边框。

1. 按`Ctrl`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  控制台将在 DevTools 中的当前网页旁边打开。

1. 将以下代码粘贴到**控制台：**

   ```javascript
   document.querySelector('header').style.border = '2em solid green'
   ```

   标题周围会出现绿色边框：

   :::image type="content" source="../media/console-dom-add-border.msft.png" alt-text="使用控制台向元素添加边框。" lightbox="../media/console-dom-add-border.msft.png":::


### <a name="get-a-direct-reference-an-element"></a>获取元素的直接引用

根据网页的复杂性，可能很难找到正确的要操作的元素。  但是，您可以使用 **Inspect** 工具来帮助你。  假设您要处理呈现的页面标题中的 **Documentation** 区域：

:::image type="content" source="../media/console-dom-highlight-documentation.msft.png" alt-text="显示您在屏幕上检查的元素。" lightbox="../media/console-dom-highlight-documentation.msft.png":::


若要获取对要操作的元素的直接引用，请进行以下操作：

1. 在 DevTools 中，单击 **"检查** "工具，然后在呈现的网页中，将鼠标悬停在 元素上：

   :::image type="content" source="../media/console-dom-use-inspector-to-get-element.msft.png" alt-text="若要选择元素，请使用 Inspect 工具" lightbox="../media/console-dom-use-inspector-to-get-element.msft.png":::

1. 单击页面上的元素，DevTools 将跳转到 **"元素"** 工具。

1. `...`单击 DOM 树中元素旁边的菜单：

   :::image type="content" source="../media/console-dom-overflow-menu-in-elements.msft.png" alt-text="单击的元素将显示在&quot;元素&quot;工具的 DOM 树中。  单击溢出菜单，获取更多功能。" lightbox="../media/console-dom-overflow-menu-in-elements.msft.png":::

1. 右键单击 DOM 树中的 元素，然后选择 **CopyCopy** >  **JS 路径**。

   :::image type="content" source="../media/console-dom-copy-JS-path.msft.png" alt-text="从&quot;元素&quot;工具的 DOM 树中的元素复制 JavaScript 路径。" lightbox="../media/console-dom-copy-JS-path.msft.png":::

   <!-- could be useful to have code listings.  test this:
   Here's the JS path you copied:

   ```javascript
   document.querySelector("#headerAreaHolder > header > div:nth-child(1) > div.nav-bar-item.is-hidden-tablet > div > button > span")
   ```

   Here's the result after you add text content:

   ```javascript
   document.querySelector("#headerAreaHolder > header > div:nth-child(1) > div.nav-bar-item.is-hidden-tablet > div > button > span").textContent = "My Playground"
   ``` -->

1. 在 **控制台中**，粘贴已复制但尚未按下 `Enter` 的 JavaScript 路径。

1. 将链接的文本更改为 `My Playground`。  为此，请添加到 `.textContent = "My Playground"` 之前粘贴的 JavaScript 路径：

   :::image type="content" source="../media/console-dom-change-content.msft.png" alt-text="使用控制台更改元素的内容。" lightbox="../media/console-dom-change-content.msft.png":::

在控制台中，使用你需要的任何 JavaScript DOM **操作**。  为了更方便， **控制台** 附带了一些帮助程序实用程序方法。


<!-- ====================================================================== -->
## <a name="helpful-console-utility-methods"></a>有用的控制台实用程序方法

控制台实用程序提供了许多便利的方法和 [快捷方式](utilities.md)。  有些方法非常强大，比 using 语句更有效 `console.log()` 。


### <a name="the-power-of-the--functions"></a>$ 函数的功能

控制台 `$` 中具有特殊 **功能**，你可能从 jQuery 中记住这一点。

*  `$_` 存储最后一个命令的结果。  因此，如果你键入 并 `2+2` 按 `Enter`，然后键入 ， `$_`控制台 **将显示** `4`。

*  `$0` 是 `$4` 最后检查的元素的堆栈。  `$0` 始终是最新的。  因此，在上一示例中，只需选择 **Inspect** `$0.textContent = "My Playground"` 工具中的 元素并键入 ，以获得相同的效果。

*  `$x()` 允许您使用 XPATH 选择 DOM 元素。

*  `$()` 和 `$$()` 是 和 的较短 `document.querySelector()` 版本 `document.querySelectorAll()`。


### <a name="example-extracting-all-links-from-a-page-as-a-sortable-table"></a>示例：从页面中提取所有链接，作为可排序表

1. 输入以下代码，该代码检索网页中的所有链接，然后将链接显示为可排序表，以将 (复制并粘贴到Excel) ：

   ```javascript
   console.table($$('a'),['href','text']);
   ```
   
   `$$('a')` 是 的短。`document.querySelectorAll('a')`

   :::image type="content" source="../media/console-dom-get-all-links.msft.png" alt-text="获取网页中所有的链接，将结果显示为表格。" lightbox="../media/console-dom-get-all-links.msft.png":::

   但是，假设您不希望显示所有信息，但希望将其作为数据获取，然后仅选择部分数据。

   快捷方式 `$$('a')` 可帮助实现此要求：它选择定位链接和每个定位链接的所有属性。  但问题是您只需要定位链接和相关文本，而不是定位链接的所有属性。

   :::image type="content" source="../media/console-dom-too-much-link-information.msft.png" alt-text="$$ 快捷方式返回的信息过多。" lightbox="../media/console-dom-too-much-link-information.msft.png":::

   为解决此问题，快捷方式`$$`具有一`NodeList` `$$` `document.querySelectorAll()``Array`项有趣的额外功能：快捷方式提供了所有方法，包括 ，而不是返回纯 like 。`map()`

1. `map()`使用 对象的 方法`Array`将信息减少为你需要的信息：

   ```javascript
   $$('a').map(a => {
      return {url: a.href, text: a.innerText}
   })
   ```

   上面的代码返回所有 `Array` 链接的 ，作为 对象和 `url` `text` 属性。

   :::image type="content" source="../media/console-dom-filter-link-data.msft.png" alt-text="使用 $$ 上的映射将信息筛选到最低值。" lightbox="../media/console-dom-filter-link-data.msft.png":::

   你尚未完成;多个链接是网页的内部链接或具有空文本。

1. `filter`使用 方法删除内部链接：

   ```javascript
   $$('a').map(a => {
      return {text: a.innerText, url: a.href}
   }).filter(a => {
      return a.text !== '' && !a.url.match('docs.microsoft.com')
   })
   ```

   :::image type="content" source="../media/console-dom-filter-out-empty-links.msft.png" alt-text="获取不为空且外部的链接。" lightbox="../media/console-dom-filter-out-empty-links.msft.png":::

   通过控制台中的发出语句操作 DOM，可以在呈现的网页**** 中更改这些元素。

1. 例如，输入以下代码，该代码在所有外部链接周围添加绿色边框：

   ```javascript
   $$('a[href^="https://"]').forEach(
      a => a.style.border = '1px solid green'
   )
   ```

   :::image type="content" source="../media/console-dom-highlight-links.msft.png" alt-text="若要突出显示所有外部链接，请在每个链接周围添加绿色边框。" lightbox="../media/console-dom-highlight-links.msft.png":::

使用 CSS 选择器功能，而不是编写复杂的 JavaScript 来筛选结果。


### <a name="creating-a-table"></a>创建表

若要为网页上不是`src``alt`内嵌图像的所有图像创建 和 信息的表，请：

1. 打开“**控制台**”。

1. 将以下代码粘贴到 **控制台中**，然后按 `Enter`：

   ```javascript
   console.table($$('img:not([src^=data])'), ['src','alt'])
   ```

   :::image type="content" source="../media/console-dom-complex-css-selector.msft.png" alt-text="若要以编程方式选择一组元素，请使用复杂的 CSS 选择器。" lightbox="../media/console-dom-complex-css-selector.msft.png":::

<!-- mystery wiggly line preventer -->


### <a name="example-getting-all-page-headings-and-anchor-urls"></a>示例：获取所有页面标题和定位 URL

准备好进行更复杂的示例了吗？  与本文一样，通过 Markdown 标记生成的 HTML 网页具有每个标题的自动 ID 值，以允许您直接深层链接到该网页的该部分。  例如，Markdown `# New features` 源文件中的 h1 标题在 `<h1 id="new-features">New features</h1>` HTML 文件中变为。

列出要复制和粘贴的所有自动标题：

1. 打开“**控制台**”。

1. 复制并粘贴以下代码：

   ```javascript
   let out = '';
   $$('#main [id]').filter(
      elm => {return elm.nodeName.startsWith('H')}
   ).forEach(elm => {
      out += elm.innerText + "\n" +
            document.location.href + '#' +
            elm.id + "\n";
   });
   console.log(out);
   ```
    
   结果是包含每个标题的内容的文本，后跟指向该标题的完整 URL。

   :::image type="content" source="../media/console-dom-get-generated-headings.msft.png" alt-text="从网页获取所有标题和生成的 URL。" lightbox="../media/console-dom-get-generated-headings.msft.png":::


### <a name="clean-up-with-clear-and-copy"></a>清除并复制

在控制台中 **开发时**，情况可能会变得混乱。  可能很难选择要复制和粘贴的结果。  以下两种实用程序方法可帮助您：

* `copy()` 将你提供的任何内容复制到剪贴板。  将 `copy()` 方法与 混合使用时 `$_`尤其有用，这将复制最后的结果。

* `clear()` 清除 **控制台**。


### <a name="read-and-monitor-events"></a>读取和监视事件

**Console** 的另外两种有趣的实用程序方法处理事件处理：

* `getEventListeners(node)` 列出节点的所有事件侦听器。

* `monitorEvents(node, events)` 监视并记录节点上发生的事件。


列出分配给网页中第一个表单的所有事件侦听器：

1. 在 DevTools 中，打开 **控制台**。

1. 将以下代码键入或粘贴到 **控制台中**：

   ```javascript
   getEventListeners($('form'));
   ```

   :::image type="content" source="../media/console-dom-get-form-events.msft.png" alt-text="获取网页中第一个表单的所有事件侦听器。" lightbox="../media/console-dom-get-form-events.msft.png":::

监视时，每次对指定元素进行更改时，都会**** 在控制台中收到通知。  将要侦听的事件定义为第二个参数。  定义要监视的事件非常重要，否则将报告元素发生的任何事件。


若要每次滚动时在 **控制台** 中获取通知，请调整窗口大小，或在用户在搜索表单中类型时：

1. 在 DevTools 中，打开 **控制台**。

1. 将以下代码粘贴到**控制台：**

   ```javascript
   monitorEvents(window, ['resize', 'scroll']);
   monitorEvents($0, 'keyup');
   ```

   :::image type="content" source="../media/console-dom-monitor-events.msft.png" alt-text="控制台显示 Window 上发生的每个滚动事件。" lightbox="../media/console-dom-monitor-events.msft.png":::

1. 若要记录当前所选元素上的任何键操作，请专注于标题中的搜索表单并按一些键。

   :::image type="content" source="../media/console-dom-monitor-key-events.msft.png" alt-text="控制台显示窗体上发生的&quot;键更新&quot;事件。" lightbox="../media/console-dom-monitor-key-events.msft.png":::

1. 若要停止日志记录，请删除设置的监视，请在控制台中输入以下 **代码**：

   ```javascript
   unmonitorEvents(window, ['resize', 'scroll']);
   unmonitorEvents($0, 'key');
   ```
   

<!-- ====================================================================== -->
## <a name="reuse-dom-manipulation-scripts"></a>重用 DOM 操作脚本

您可能会发现从控制台操作 DOM **非常有用**。  你可能很快遇到控制台作为开发 **平台** 的限制。  好消息是，DevTools [中的"](../sources/index.md) 源"工具提供了功能齐全的开发环境。  在 **"源** "工具中，您可以：

*  将控制台脚本 **存储** 为代码段;请参阅 [在任何网页上运行 JavaScript 代码段](../javascript/snippets.md)。

*  使用键盘快捷方式或编辑器在网页中运行脚本。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [在控制台工具中记录消息](console-log.md)
* [在控制台中运行 JavaScript](console-javascript.md)
