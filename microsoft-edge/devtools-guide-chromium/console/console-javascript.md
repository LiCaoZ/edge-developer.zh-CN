---
title: 在控制台中运行 JavaScript
description: 将控制台工具用作 JavaScript Microsoft Edge开发人员工具简介。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
---
# <a name="run-javascript-in-the-console"></a>在控制台中运行 JavaScript

可以在控制台中输入任何 JavaScript 表达式、语句或代码段，并且**** 它会在键入时立即以交互方式运行。  这是可行的，因为 DevTools 中的控制台工具是一个 [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 环境。****  _REPL_ 代表 Read、Evaluate、Print 和 Loop。

**控制台：**
1. 读取您键入的 JavaScript。
1. 评估代码。
1. 输出表达式的结果。
1. 循环回第一步。


若要在控制台中以交互方式输入 JavaScript 语句和表达式：

1. 在网页中右键单击，然后选择"检查 **"**。  将打开 DevTools。  或者，按 `Control`++`Shift``J` \ (Windows、Linux\) 或`J` `Command`+`Option`+\ (macOS\) 直接打开 DevTools 控制台。

1. 如有必要，请在 DevTools 中单击以赋予其焦点，然后按 `Esc` 以打开 **控制台**。

1. 在控制台 **中单击**，然后键入 `2+2`，而无需按 `Enter`。

   键入 **时** ，控制台会立即在 `4` 下一行上显示结果。  该功能 `Eager evaluation` 可帮助你编写有效的 JavaScript。  **无论** JavaScript 是否正确以及是否存在有效结果，控制台都会在键入时显示结果。

   :::image type="content" source="../media/console-javascript-eager-evaluation.msft.png" alt-text="控制台将在您键入表达式&quot;2 + 2&quot;时以交互方式显示该表达式的结果。" lightbox="../media/console-javascript-eager-evaluation.msft.png":::

1. 按 时`Enter`，控制台将**** 运行 JavaScript 命令 (表达式或语句) ，显示结果，然后向下移动光标以允许您输入下一个 JavaScript 命令。

   :::image type="content" source="../media/console-javascript-several-expressions.msft.png" alt-text="连续运行多个 JavaScript 表达式。" lightbox="../media/console-javascript-several-expressions.msft.png":::


<!-- ====================================================================== -->
## <a name="autocompletion-to-write-complex-expressions"></a>编写复杂表达式的自动完成

控制台 **可帮助** 你使用自动完成编写复杂的 JavaScript。  此功能是了解以前不知道的 JavaScript 方法的一种好方法。

在编写多部分表达式时尝试自动完成：

1. 键入 `doc`。

1. 按箭头键在下拉菜单 `document` 上突出显示。

1. 按 `Tab` 以选择 `document`。

1. 键入 `.bo`。

1. 按 `Tab` 以选择 `document.body`。

1. 键入另 `.` 一个，获取当前网页正文中可用的可能属性和方法的大型列表。

   :::image type="content" source="../media/console-javascript-autocomplete.msft.png" alt-text="JavaScript 表达式的控制台自动完成。" lightbox="../media/console-javascript-autocomplete.msft.png":::


<!-- ====================================================================== -->
## <a name="console-history"></a>控制台历史记录

与许多其他命令行环境一样，输入的命令历史记录也可供重复使用。  按 `Up Arrow` 以显示之前输入的命令。  

同样，自动完成会保留以前键入的命令的历史记录。  可以键入之前命令的前几个字母，之前的选择将显示在文本框中。

此外， **控制台** 还提供了很多实用程序 [方法](utilities.md) ，可简化您的生活。  例如， `$_` 始终包含你在控制台中运行的最后一个表达式 **的结果**。

:::image type="content" source="../media/console-javascript-console-history.msft.png" alt-text="控制台中的 $_ 表达式始终包含最后的结果。" lightbox="../media/console-javascript-console-history.msft.png":::


<!-- ====================================================================== -->
## <a name="multiline-edits"></a>多行编辑

默认情况下， **控制台只** 为你提供一行来编写 JavaScript 表达式。  按 时，代码将运行 `Enter`。 单行限制可能会使您费时无用。  若要绕绕 1 行限制，请按 `Shift`+`Enter` 而不是 。`Enter`  在下面的示例中，显示的值是运行顺序 (语句) 的结果：

:::image type="content" source="../media/console-javascript-multiline.msft.png" alt-text="按 Shift+Enter 可编写几行 JavaScript。  生成的值为 output。" lightbox="../media/console-javascript-multiline.msft.png":::

如果在控制台中启动多行语句，将自动识别**** 代码块并缩进。  例如，如果通过输入大括号来启动块语句，则下一行将自动缩进：

:::image type="content" source="../media/console-javascript-automatic-lineindent.msft.png" alt-text="控制台使用大括号和缩进识别多行表达式。" lightbox="../media/console-javascript-automatic-lineindent.msft.png":::


<!-- ====================================================================== -->
## <a name="network-requests-using-top-level-await"></a>使用顶级 await () 的网络请求

除了在你自己的脚本中， **控制台** 还 [支持顶级 await](https://github.com/tc39/proposal-top-level-await) 在它内运行任意异步 JavaScript。  例如，使用 API 时 `fetch` 无需使用 `await` async 函数包装语句。

若要获取最近 50 个在 Microsoft Edge [开发人员工具中Visual Studio Code GitHub](https://github.com/microsoft/vscode-edge-devtools)存储库：

1. 在 DevTools 中，打开 **控制台**。

1. 复制并粘贴以下代码段，获取包含 10 个条目的对象：

   ```javascript
   await ( await fetch(
   'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
   )).json();
   ```

   :::image type="content" source="../media/console-javascript-top-level-await.msft.png" alt-text="控制台显示顶级异步提取请求的结果。" lightbox="../media/console-javascript-top-level-await.msft.png":::

   这 10 个条目很难识别，因为会显示大量信息。

1. （可选）使用 `console.table()` log 方法仅接收您感兴趣的信息：

   :::image type="content" source="../media/console-javascript-filtered-with-table.msft.png" alt-text="使用&quot;console.table&quot;以可读格式显示最后的结果。" lightbox="../media/console-javascript-filtered-with-table.msft.png":::

   若要重用从表达式返回的数据，请使用 `copy()` 控制台的实用程序 **方法**。

   <!-- todo: test: -->

1. 粘贴以下代码。  它将发送请求并将响应数据复制到剪贴板：

   ```javascript
   copy(await (await fetch(
   'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
   )).json())
   ```
   
**控制台**是练习 JavaScript 和执行一些快速计算的一种很好的方法。  真正的功能是，您有权访问 [window](https://developer.mozilla.org/docs/Web/API/Window) 对象。  请参阅 [使用控制台与 DOM 进行交互](console-dom-interaction.md)。
