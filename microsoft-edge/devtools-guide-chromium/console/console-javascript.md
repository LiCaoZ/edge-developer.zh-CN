---
title: 在控制台中运行 JavaScript
description: 将控制台工具用作 JavaScript Microsoft Edge开发人员工具简介。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge， JavaScript， Web 开发， f12 工具， devtools
ms.date: 04/13/2021
ms.openlocfilehash: af2a374298e924a797d65a0a4c5c7a383bbd2e84
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285188"
---
# <a name="run-javascript-in-the-console"></a>在控制台中运行 JavaScript

浏览器**** DevTools 中的控制台工具是一个[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)环境。  REPL 代表 Read、Evaluate、Print 和 Loop。 控制台 **读取** 您键入的 JavaScript，评估代码，输出表达式的结果，然后循环回第一步。  这意味着可以在控制台中编写立即运行的任何 JavaScript。 ****

若要试用，请进行以下尝试：

1.  打开“**控制台**”。  例如，按 `Control` + `Shift` + `J` \ (Windows、Linux\) 或 `Command` + `Option` + `J` \ (macOS\) 。

1.  键入 `2 + 2`。

    键入 **时** ，控制台会立即 `4` 在下一行上显示结果。  该功能 `Eager evaluation` 可帮助你编写有效的 JavaScript。  无论您的 JavaScript 是否正确以及是否存在有效结果，它都会在键入时显示结果。

:::image type="complex" source="../media/console-javascript-eager-evaluation.msft.png" alt-text="控制台在键入时显示 2 + 2 实时的结果" lightbox="../media/console-javascript-eager-evaluation.msft.png":::
   **控制台** 在键入 `2 + 2` 实时内容时显示结果
:::image-end:::

如果按 `Enter` ， **控制台** 将运行 JavaScript 命令，为你提供结果，并允许你编写下一个命令。

:::image type="complex" source="../media/console-javascript-several-expressions.msft.png" alt-text="连续运行多个 JavaScript 表达式" lightbox="../media/console-javascript-several-expressions.msft.png":::
   连续运行多个 JavaScript 表达式
:::image-end:::


<!-- ====================================================================== -->
## <a name="autocompletion-to-write-complex-expressions"></a>编写复杂表达式的自动完成

控制台 **可帮助** 你使用自动完成编写复杂的 JavaScript。  此功能是了解以前不知道的方法的一种好方法。

若要试用，请进行以下尝试：

1.  键入 `doc`。
1.  按箭头键在 `document` 下拉菜单上突出显示。
1.  按 `Tab` 键选择 `document` 。
1.  键入 `.bo`。
1.  按 `Tab` 以输入 `document.body` 。
1.  键入另 `.` 一个，获取当前网页正文中可用的可能属性和方法的大型列表。

:::image type="complex" source="../media/console-javascript-autocomplete.msft.png" alt-text="JavaScript 表达式的控制台自动完成" lightbox="../media/console-javascript-autocomplete.msft.png":::
   **** JavaScript 表达式的控制台自动完成
:::image-end:::


<!-- ====================================================================== -->
## <a name="console-history"></a>控制台历史记录

与许多其他命令行体验一样，您也有命令历史记录。  按 `Up Arrow` 以显示之前输入的命令。  自动完成还会保留以前键入的命令的历史记录。  可以键入之前命令的前几个字母，之前的选项会显示在文本框中。

此外， **控制台** 还提供了很多实用程序 [方法](utilities.md) ，可简化您的生活。  例如， `$_` 始终包含控制台 中运行的最后一个表达式 **的结果**。

:::image type="complex" source="../media/console-javascript-console-history.msft.png" alt-text="控制台中的 $_ 表达式始终包含最后的结果" lightbox="../media/console-javascript-console-history.msft.png":::
    控制台 `$_` 中的表达式 **始终** 包含最后的结果
:::image-end:::


<!-- ====================================================================== -->
## <a name="multiline-edits"></a>多行编辑

默认情况下， **控制台只** 为你提供一行来编写 JavaScript 表达式。  按 时，代码将运行 `Enter` 。 单行限制可能会使您费时无用。  若要绕绕一行限制，请按 `Shift` + `Enter` 而不是 `Enter` 。  在下面的示例中，显示的值是按顺序运行的所有行的结果。

:::image type="content" source="../media/console-javascript-multiline.msft.png" alt-text="按 Shift+Enter 写入几行 JavaScript，并按顺序运行生成的值" lightbox="../media/console-javascript-multiline.msft.png":::

如果在控制台中启动多行 **语句，它**将自动识别并缩进。  例如，如果启动带大括号的块语句。

:::image type="complex" source="../media/console-javascript-automatic-lineindent.msft.png" alt-text="控制台已使用大括号和缩进来识别多行表达式" lightbox="../media/console-javascript-automatic-lineindent.msft.png":::
    **控制台** 已使用大括号和缩进来识别多行表达式
:::image-end:::


<!-- ====================================================================== -->
## <a name="network-requests-using-top-level-await"></a>使用顶级 await () 的网络请求

除了在你自己的脚本中， **控制台** 还 [支持顶级 await](https://github.com/tc39/proposal-top-level-await) 在它内运行任意异步 JavaScript。  例如，使用 API 时 `fetch` 无需使用 `await` async 函数包装语句。

若要获取最近 50 个在 Microsoft Edge[开发人员工具中Visual Studio Code GitHub](https://github.com/microsoft/vscode-edge-devtools)存储库：

1.  打开“**控制台**”。
1.  复制并粘贴以下代码段，获取包含 10 个条目的对象。

    ```javascript
    await ( await fetch(
    'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
    )).json();
    ```

:::image type="complex" source="../media/console-javascript-top-level-await.msft.png" alt-text="控制台显示顶级异步提取请求的结果" lightbox="../media/console-javascript-top-level-await.msft.png":::
    **控制台** 显示顶级异步请求 `fetch` 的结果
:::image-end:::

这 10 个条目很难识别，因为会显示大量信息。  可以使用 log `console.table()` 方法仅接收您感兴趣的信息。

:::image type="complex" source="../media/console-javascript-filtered-with-table.msft.png" alt-text="使用 console.table 以人工可读格式显示最后的结果" lightbox="../media/console-javascript-filtered-with-table.msft.png":::
    使用 可读格式显示最后的结果 `console.table`
:::image-end:::

若要重用从表达式返回的数据，可以使用 `copy()` 控制台 的实用程序 **方法**。  以下代码段发送请求并将响应数据复制到剪贴板。

```javascript
copy(await (await fetch(
'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
)).json())
```

使用 **控制台** 作为实践 JavaScript 和进行一些快速计算的一种好方法。  真正的功能是，您有权访问 [window](https://developer.mozilla.org/docs/Web/API/Window) 对象。  可以使用 [控制台与 DOM 进行交互](console-dom-interaction.md)。
