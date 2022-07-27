---
title: 控制台概述
description: Microsoft Edge 开发人员工具中控制台工具的简介。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
ms.openlocfilehash: 9040f5da4fbbd4bcba299f50d6caa10a58658745
ms.sourcegitcommit: 8aee95757de12c62f4a74d37649ad5979f9e0ba9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2022
ms.locfileid: "12550511"
---
# <a name="console-overview"></a>控制台概述

**控制台**类似于 DevTools 中的智能、丰富的命令行，它是与其他工具配合使用的绝佳帮手工具。  **控制台**提供了一种编写功能脚本、检查当前网页以及使用 JavaScript 操作当前网页的强大方法。

**控制台**工具可帮助执行多个任务，以下文章更详细地介绍了这些任务：

* **跟踪问题**找出当前项目中某些环节无法正常工作的原因。  参阅[修复控制台中报告的 JavaScript 错误](console-debug-javascript.md)。
* 以日志消息的形式在浏览器中**获取有关 Web 项目的信息**。  参阅[筛选控制台消息](console-filters.md)。
* 脚本中关于调试的**日志信息**。  参阅[在控制台工具中记录消息](console-log.md)。
* 在 [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 环境中**试用 JavaScript 表达式**。  参阅[在控制台中运行 JavaScript](console-javascript.md)。
* 使用 JavaScript **与浏览器中的 Web 项目进行交互**。  参阅[使用控制台与 DOM 交互](console-dom-interaction.md)。

可以在 DevTools 的顶部或底部打开**控制台**工具，它会显示在主工具栏的上半部分：

![控制台工具在上面板中打开。](../media/console-intro-console-main.msft.png)

**控制台**显示在 DevTools 的下半部分（**抽屉**），其上方打开了**元素**工具：

![下面板中的控制台，其上方打开了“元素”工具。](../media/console-intro-console-panel.msft.png)

直接打开**控制台**的最快方法是按 `Ctrl`+`Shift`+`J` (Windows、Linux) 或 `Command`+`Option`+`J` (macOS)。


<!-- ====================================================================== -->
## <a name="error-reports-and-the-console"></a>错误报告和控制台

**控制台**是报告 JavaScript 和连接错误的默认位置。  如果出现任何错误，**问题计数器**会显示在 DevTools 中的**设置**图标的旁边，它会提供错误和警告数。  单击**问题计数器**打开**问题**工具并显示问题。  有关详细信息，请参阅[修复控制台中报告的 JavaScript 错误](console-debug-javascript.md)。

DevTools 提供了有关**控制台**中的错误的详细信息：

![DevTools 在控制台中提供有关错误的详细信息。](../media/console-debug-displays-error.msft.png)


<!-- ====================================================================== -->
## <a name="search-the-web-for-a-console-error-message-string"></a>在 Web 上搜索控制台错误消息字符串

从 DevTools 中直接在 Web 上搜索**控制台**错误消息。  在**控制台**中，许多错误消息现在都有一个“**在 Web 上搜索此消息**”的按钮，显示为一个放大镜：

![控制台中出现错误消息时的“在 Web 上搜索此消息”按钮。](../media/search-console-icon.msft.png)
<!-- to set up screenshot, went to 
https://docs.microsoft.com/microsoft-edge/devtools-guide-chromium/console/console-debug-javascript to get a good page that has an error: 
https://microsoftedge.github.io/Demos/devtools-console/error.html -->

当你单击“**在 Web 上搜索此消息**”按钮时，浏览器中会打开一个新选项卡，并显示此错误消息的搜索结果：

![新选项卡中的搜索结果页。](../media/search-console-new-tab.msft.png)


<!-- ====================================================================== -->
## <a name="inspect-and-filter-information-on-the-current-webpage"></a>检查和筛选当前网页上的信息

在网页上打开 DevTools 时，**控制台**中可能存在大量信息。  当你需要识别重要信息时，信息量会成为一个问题。  若要查看需要行动的重要信息，请在 DevTools 中使用[问题](../issues/index.md)工具。

“问题”正逐渐从**控制台**移动到**问题**工具。  但是，**控制台**中仍有大量信息，因此最好了解一下**控制台**中的自动日志和筛选器选项。  有关详细信息，请参阅[筛选控制台消息](console-filters.md)。

具有充满消息的**控制台**的 DevTools：

![具有充满消息的控制台的 DevTools。](../media/console-intro-noise.msft.png)


<!-- ====================================================================== -->
## <a name="log-information-to-display-in-the-console"></a>要在控制台中显示的日志信息

**控制台**最常见的用例是使用 `console.log()` 方法或其他类似方法记录脚本中的信息。


### <a name="example-code"></a>示例代码

```javascript
// prints the text to the console as  a log message
console.log('This is a log message');

// prints the text to the console as an informational message
console.info('This is some information'); 

// prints the text to the console as an error message
console.error('This is an error');

// prints the text to the console as a warning
console.warn('This is a warning');

// prints the geometry of the document body as an object
console.log(document.body.getBoundingClientRect());

// prints the geometry of the document body as a table
console.table(document.body.getBoundingClientRect());

// shows a list of techologies as a collapsed group
let technologies = ["HTML", "CSS", "SVG", "ECMAScript"];
console.groupCollapsed('Technolgies');
technologies.forEach(tech => {console.info(tech);})
console.groupEnd('Technolgies');
```

<!-- typos in the demo page are preserved above, at `Technolgies` -->


若要记录要在控制台中显示的信息：

1. 在新窗口或选项卡中打开演示网页[控制台消息示例：日志、信息、错误、警告](https://microsoftedge.github.io/Demos/devtools-console/logging-demo.html)。

1. 若要打开**控制台**，请按 `Ctrl`+`Shift`+`J` (Windows、Linux) 或 `Command`+`Option`+`J` (macOS)。

   **控制台**显示演示代码导致的结果消息：

   ![充满由演示代码所导致的消息的控制台。](../media/console-intro-logging.msft.png)

1. 将上述代码粘贴到**控制台**，然后按 `Enter`。


   如果收到以下消息：`Uncaught SyntaxError: Identifier 'technologies' has already been declared`：

1. 打开新选项卡或窗口。

1. 若要打开**控制台**，请按 `Ctrl`+`Shift`+`J` (Windows、Linux) 或 `Command`+`Option`+`J` (macOS)。

1. 将上述代码粘贴到**控制台**，然后按 `Enter`。

使用**控制台**时，有许多好用的方法可以使用。  有关详细信息，请参阅[控制台工具中的日志消息](console-log.md)。


<!-- ====================================================================== -->
## <a name="try-your-javascript-live-in-the-console"></a>在控制台中实时试用 JavaScript

**控制台**不仅仅是记录信息的位置。  **控制台**是一种 [REPL 环境](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)。  在**控制台**中编写任何 JavaScript 时，代码将立即运行。  你可能会发现测试一些新的 JavaScript 功能或执行一些快速计算非常有用。  此外，还可从新式编辑环境获得所需的所有功能，例如自动完成、语法突出显示和历史记录。

尝试在控制台中运行 JavaScript：

1. 打开“**控制台**”。

1. 键入 `2+2`。

**控制台**会在你键入时实时显示 `2+2` 的结果，并在以下行上显示结果 `4`：

![控制台会在你键入时实时显示 2+2 的结果。](../media/console-javascript-eager-evaluation.msft.png)

此**预先评估**功能可用于调试和验证代码中是否出错。

若要在**控制台**中运行 JavaScript 表达式并选择性地显示结果，请按 `Enter`。  然后，可以编写下一个 JavaScript 代码以在**控制台**中运行。

连续运行几行 JavaScript 代码：

![连续运行几行 JavaScript 代码。](../media/console-javascript-several-expressions.msft.png)

默认情况下，你在单行上运行 JavaScript 代码。  若要运行一行，请键入 JavaScript，然后按 `Enter`。  若要解决单行限制，请按 `Shift`+`Enter` 而不是 `Enter`。

与其他命令行体验类似，若要访问以前的 JavaScript 命令，请按 `Arrow-Up`。  **控制台**的自动完成功能是了解不熟悉方法的好方法。

若要尝试自动完成：

1. 打开“**控制台**”。
1. 键入 `doc`。
1. 从下拉菜单中选择 `document`。
1. 按 `Tab` 选择 `document`。
1. 键入 `.bo`。
1. 按 `Tab` 选择 `document.body`。
1. 键入另一个 `.` 以显示当前网页正文中可用的属性和方法的完整列表。

有关使用**控制台**的所有方法的详细信息，请参阅[控制台作为 JavaScript 环境](console-javascript.md)。

**控制台**中 JavaScript 表达式自动完成：

![控制台 JavaScript 表达式自动完成。](../media/console-javascript-autocomplete.msft.png)


<!-- ====================================================================== -->
## <a name="interact-with-the-current-webpage-in-the-browser"></a>与浏览器中的当前网页交互

**控制台**有权访问浏览器的[窗口](https://developer.mozilla.org/docs/Web/API/Window)对象。  可以通过从 DOM 读取数据并将数据分配给 DOM 元素来编写与当前网页交互的脚本。


### <a name="reading-from-the-dom-tree-in-the-console"></a>从控制台中的 DOM 树读取

若要使用 JavaScript 表达式通过从 DOM 树读取所选元素从当前页面读取内容：

1. 打开“**控制台**”。

1. 将以下代码粘贴到**控制台**，然后按 `Enter`：

   ```javascript
   document.querySelector('h1').innerHTML
   ```

   此表达式会从 DOM 中选择第一个标题级别 1，然后选择 `<h1>` 开始标记和结束标记之间包含的 HTML 内容。  **控制台**会显示表达式的输出，即标题的文本：

   ![控制台会显示表达式的输出，即标题的文本。](../media/console-intro-reading-DOM.msft.png)

你已从网页的 DOM 表示形式中读取，方法是在**控制台**中输入 JavaScript 表达式，并在**控制台**中显示输出。


### <a name="writing-to-the-dom-tree-and-webpage-from-the-console"></a>从控制台写入 DOM 树和网页

还可以通过将 DOM（或_写入_ DOM）从**控制台**中更改呈现的网页。

若要更改呈现的网页：

1. 打开“**控制台**”。

1. 将以下代码粘贴到**控制台**，然后按 `Enter`：

   ```javascript
   document.querySelector('h1').innerHTML = 'Rocking the Console';
   ```

   上述 JavaScript 表达式使用 `=` 符号将值分配给所选 DOM 项。  在此示例中，表达式的计算值是标题的字符串。  表达式的值（标题字符串）显示在**控制台**和呈现的网页中：

   ![将文本写入控制台中的 DOM。](../media/console-intro-wrtiting-DOM.msft.png)

   你已将网页的主标题更改为**使用控制台**。


### <a name="using-the--console-utility-method-to"></a>使用 $$ 控制台实用工具方法 

**控制台实用工具**方法可以轻松访问和操作当前网页。

例如，若要在当前网页中的所有链接周围添加绿色边框：

1. 打开“**控制台**”。

1. 将以下代码粘贴到**控制台**，然后按 `Enter`：

   ```javascript
   $$('a').forEach(a => a.style.border='1px solid lime');
   ```

   `$$(selector)` 控制台实用工具的函数为 "Query selector all"。  此 DOM 查询选择器函数返回与指定的 CSS 选择器匹配的所有元素的数组，例如 JavaScript 函数 `document.querySelectorAll()`。  在此示例中，我们选择所有 `<a>` 超链接元素，然后在它们周围应用一个绿色框：

   ![使用控制台操作元素的选择。](../media/console-intro-changing-styles.msft.png)

有关详细信息，请参阅[控制台工具实用工具函数和选择器](utilities.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

<!-- if an article's title is adequately descriptive, and the article is in the same TOC bucket as the present article, don't much need a link here: -->
* [使用控制台与 DOM 交互](console-dom-interaction.md)。
* [控制台功能参考](reference.md)
* [控制台对象 API 参考](api.md)
* [控制台工具实用功能和选择器](utilities.md)
