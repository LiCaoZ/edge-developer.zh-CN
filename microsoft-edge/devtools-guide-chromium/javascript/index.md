---
title: 调试 JavaScript 入门
description: 了解如何使用 Microsoft Edge 开发工具查找并修复 JavaScript bug。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 5e67aa9950f3e0e09b4abc174eb9fc60c274d591
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12513836"
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
# <a name="get-started-debugging-javascript"></a>调试 JavaScript 入门

本文指导你如何在开发工具中调试 JavaScript 问题的基本工作流程。


<!-- ====================================================================== -->
## <a name="step-1-reproduce-the-bug"></a>步骤 1：重现 Bug

调试的第一步是查找一系列持续重现 bug 的操作。

1. 在新窗口或选项卡[中入门调试 JavaScript](https://microsoftedge.github.io/Demos/devtools-js-get-started/) 打开演示网页。 为此，请右键单击链接。  或者，按住`Ctrl` (Windows、Linux) 或`Command` (macOS) ，然后单击链接。

   <!-- You can view the source files for the Debugging demo at the [MicrosoftEdge/Demos > devtools-js-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-js-get-started) repo folder. -->

1. 在“**数字 1 **”文本框中输入 `5`。

1. 在“**数字 2 **”文本框中输入 `1`。

1. 单击 **“添加 1 号”和“数字 2**”。  按钮下方的标签显示 `5 + 1 = 51`。  结果应为 `6`。  接下来，修复作为 bug 的加法错误。

   :::image type="content" source="../media/javascript-js-demo-bad.msft.png" alt-text="5 + 1 的结果为 51，但应为 6" lightbox="../media/javascript-js-demo-bad.msft.png":::


<!-- ====================================================================== -->
## <a name="step-2-get-familiar-with-the-sources-tool-ui"></a>步骤 2：熟悉源工具 UI

开发工具为不同的任务提供了许多工具。  不同的任务包括更改 CSS、分析页面加载性能以及监视网络请求。  **源**工具是调试 JavaScript 的地方。

1. 若要在 DevTools 中打开**控制台**工具，请按 `Ctrl`++`Shift``J` (Windows、Linux) 或`J``Command`+`Option`+ (macOS) 。

   :::image type="content" source="../media/javascript-console-empty.msft.png" alt-text="控制台工具。" lightbox="../media/javascript-console-empty.msft.png":::

1. 选择 **“源** ”工具。

   :::image type="content" source="../media/javascript-sources-sections.msft.png" alt-text="源工具。" lightbox="../media/javascript-sources-sections.msft.png":::

**源**工具 UI 有三个部分。

:::image type="content" source="../media/javascript-sources-sections-annotated.msft.png" alt-text="源工具 UI 的 3 个部分。" lightbox="../media/javascript-sources-sections-annotated.msft.png":::

*  ) 左上角的 **“导航器** ”窗格 (。  此处列出了网页请求的所有文件。

*  ) 右上角的“ **编辑器** ”窗格 (。  在 **导航器** 窗格中选择文件后，此窗格将显示文件的内容。

*  调 **试器** 窗格 (底部) 。  此窗格提供用于检查网页 JavaScript 的工具。  如果 DevTools 窗口很宽，则此窗格将显示在 **编辑** 器窗格的右侧。


<!-- ====================================================================== -->
## <a name="step-3-pause-the-code-with-a-breakpoint"></a>步骤 3：使用断点暂停代码

调试此类问题的常见方法是在代码中插入多个 `console.log()` 语句，然后在脚本运行时检查值。  例如：

```javascript
function updateLabel() {
    var addend1 = getNumber1();
    console.log('addend1:', addend1);
    var addend2 = getNumber2();
    console.log('addend2:', addend2);
    var sum = addend1 + addend2;
    console.log('sum:', sum);
    label.textContent = addend1 + ' + ' + addend2 + ' = ' + sum;
}
```

该 `console.log()` 方法可能会完成作业，但 **断点** 可以更快地完成作业。  断点允许在运行时中间暂停代码，并检查此时的所有值。  与`console.log()`方法相比，断点具有以下优点。

*  使用 `console.log()`，需要手动打开源代码，找到相关代码，插入 `console.log()` 语句，然后刷新网页以在**控制台**中显示消息。  使用断点可以暂停相关代码，而无需知道代码的结构。

*  在 `console.log()` 语句中，需要显式指定要检查的每个值。  通过断点，开发工具会及时显示所有变量的值。  有时，影响代码的变量被隐藏和混淆。

简而言之，断点可以帮助你比 `console.log()` 方法更快地查找和修复 bug。


### <a name="event-listener-breakpoints"></a>事件侦听器断点

如果退后一步并思考应用的工作原理，你可能会根据需要猜测，错误 () `5 + 1 = 51` 在与 **“添加数字 1”和“数字 2**”按钮关联的事件侦听器中`click`计算出不正确的总和。  因此，可能想在 `click` 侦听器运行期间暂停代码。  **使用事件侦听器断点** 可以执行以下操作：

1. 在 **“调试器** ”窗格中，单击 **“事件侦听器断点** ”以展开该部分。  开发工具显示可展开事件类别的列表，如**动画**和**剪贴板**。

1. 在 **鼠标** 事件类别旁边，单击 **“展开** (![”图标。](../media/expand-icon.msft.png)) 。  开发工具显示鼠标事件的列表，如**单击**和**鼠标按下**。  每个事件旁边都有一个复选框。

1. 选择 **单击**旁边的复选框。  现在开发工具设置为在运行任何 `click` 事件侦听器时自动暂停。

   :::image type="content" source="../media/javascript-sources-event-listener-breakpoint-mouse-click.msft.png" alt-text="选择单击旁边的复选框。" lightbox="../media/javascript-sources-event-listener-breakpoint-mouse-click.msft.png":::

1. 返回演示，再次单击 **“添加数字 1”和“数字 2** ”。  开发工具暂停演示并在“**源**”具中突出显示一行代码。  开发工具应该暂停在 `get-started.js` 中的第 16 行。

    ```javascript
    if (inputsAreEmpty()) {
    ```

    如果在其他代码行上暂停，请单击“ **恢复脚本执行** (![恢复脚本执行。](../media/resume-script-run-icon.msft.png)) 直到在正确的行上暂停。

    > [!NOTE]
    > 如果在另一行暂停，则将拥有一个浏览器扩展，此扩展会在你访问的每个网页上注册一个 `click` 事件侦听器。  你已在扩展的 `click` 侦听器中暂停。  如果使用 InPrivate 模式 **以私密方式浏览**，从而禁用所有扩展，你可能会看到每次在所需的代码行上暂停。

<!--todo: add inprivate section when available in this repo [InPrivate](https://support.alphabet.com/alphabet-browser/answer/95464) -->

**事件侦听器断点**只是开发工具中提供的许多类型的断点之一。  记住所有不同的类型，以帮助你尽快调试不同的方案。  若要了解何时以及如何使用每种类型，请参阅 [使用断点暂停代码](breakpoints.md)。


<!-- ====================================================================== -->
## <a name="step-4-step-through-the-code"></a>步骤 4：单步执行代码

Bug 的一个常见原因是脚本以错误的顺序运行。  单步执行代码允许你演练代码的运行时。  一次浏览一行，以准确确定代码的位置以与不同的顺序运行。  立即尝试：

1. 单击 **下一个函数调用** (![下一个函数调用的步骤。](../media/step-over-icon.msft.png)) 。  DevTools 无需步入即可运行以下代码。

    ```javascript
    if (inputsAreEmpty()) {
    ```

    > [!NOTE]
    > 开发工具跳过几行代码。  这是因为 `inputsAreEmpty()` 计算结果为 false，因此该语句的代码 `if` 块不会运行。

1. 在 DevTools 的 **“源** ”工具上，单击“ **步骤进入下** 一个函数调用 (![步入下一个函数调用。](../media/step-into-icon.msft.png)) 一次单行逐步完成函 `updateLabel()` 数的运行时。

这是逐步执行代码的基本理念。  如果查看其中的代码 `get-started.js`，可以看到 bug 可能位于函数的 `updateLabel()` 某个位置。  可以使用另一种类型的断点 (_代码行断点_) ，而不是单步执行每行代码，以将代码暂停到 bug 的可能位置。


<!-- ====================================================================== -->
## <a name="step-5-set-a-line-of-code-breakpoint"></a>步骤 5：设置代码行断点

代码行断点是最常见的断点类型。  到达要暂停的特定代码行时，使用代码行断点。

1. 查看 `updateLabel()` 中的最后一行代码：

    ```javascript
    label.textContent = addend1 + ' + ' + addend2 + ' = ' + sum;
    ```

1. 在左侧，此特定代码行的编号显示为 **34**。  单击第 **34 行**。  DevTools (或最近显示一个红色圆圈，一个蓝色矩形) **34** 的左侧。  红色圆圈 (或蓝色矩形) 指示代码行断点在此行上。  开发工具始终在运行此代码行之前暂停。

1. 单击 **“恢复脚本执行** (![恢复脚本执行。](../media/resume-script-run-icon.msft.png)) 。  脚本继续运行，直到达到第 34 行。  在第 31、32 和 33 行上，开发工具在每行的分号右边打印`addend1`、`addend2` 和 `sum` 的值。

   :::image type="content" source="../media/javascript-sources-breakpoint-paused.msft.png" alt-text="DevTools 会在第 34 行的代码行断点上暂停。" lightbox="../media/javascript-sources-breakpoint-paused.msft.png":::


<!-- ====================================================================== -->
## <a name="step-6-check-variable-values"></a>步骤 6：检查变量值

`addend1`、`addend2` 和 `sum` 的值看起来可疑。  这些值用引号括起来。  引号表示此值是一个字符串，这是解释错误原因的一个很好的假设。  收集有关情况的更多信息。  开发工具提供了许多用于检查变量值的工具。

### <a name="method-1-the-scope-pane"></a>方法 1：范围窗格

如果在代码行上暂停， **则“范围** ”窗格将显示当前定义的本地变量和全局变量以及每个变量的值。  如果适用，它还会显示关闭变量。  双击变量值进行编辑。  如果不在代码行上暂停，则“ **范围** ”窗格为空。

:::image type="content" source="../media/javascript-sources-breakpoint-paused-scope.msft.png" alt-text="“范围”窗格。" lightbox="../media/javascript-sources-breakpoint-paused-scope.msft.png":::

### <a name="method-2-watch-expressions"></a>方法 2：监视表达式

使用 **“监视** ”窗格可以监视变量的值 (，例如 `sum`) 或表达式 (，例如 `typeof sum`) 。  可以在监视表达式中存储任何有效的 JavaScript 表达式。

1. 选择“ **监视”** 选项卡。

1. 单击 **“添加监视表达式** (![添加监视表达式。](../media/add-expression-icon.msft.png)) 。

1. 键入 `typeof sum`。

1. 按 `Enter`。  DevTools 显示 `typeof sum: "string"`。  冒号右边的值是监视表达式的结果。

> [!NOTE]
> 在下图中 `typeof sum` ，监视表达式显示在 **“监视** ”窗格中。  如果 DevTools 窗口很宽， **则“监视** ”窗格将显示在 **调试器** 窗格中，然后显示在右侧。

:::image type="content" source="../media/javascript-sources-breakpoint-paused-watch.msft.png" alt-text="“监视”窗格。" lightbox="../media/javascript-sources-breakpoint-paused-watch.msft.png":::

正如猜想的那样，如果应为数字， `sum` 被评估为字符串。  现在确认值类型是 Bug 的原因。

### <a name="method-3-the-console"></a>方法 3：控制台

**使用控制台**可以查看`console.log()`输出。  还可以使用 **控制台** 在调试器在代码语句处暂停时评估任意 JavaScript 语句。  对于调试，可以使用 **控制台** 测试 bug 的潜在修补程序。

1. 如果 **控制台** 工具已关闭，请按 `Esc` 下以打开它。  **控制台**工具在 DevTools 窗口的下窗格中打开。

1. 在**控制台**中，键入 `parseInt(addend1) + parseInt(addend2)`。  工具的语句暂停在作用域为 `addend1` 和 `addend2` 的代码行上。

1. 按 `Enter`。  开发工具将评估该语句并打印 `6`，这是预期演示生成的结果。

   :::image type="content" source="../media/javascript-sources-breakpoint-paused-console.msft.png" alt-text="评估 parseInt (addend1) + parseInt (addend2) 后的控制台工具" lightbox="../media/javascript-sources-breakpoint-paused-console.msft.png":::


<!-- ====================================================================== -->
## <a name="step-7-apply-a-fix"></a>步骤 7：应用修补程序

我们已确定 bug 的可能修复方法。  接下来，直接在 DevTools UI 中编辑 JavaScript 代码，然后重新运行演示以测试修补程序，如下所示。

1. 单击 **“恢复脚本执行** (![恢复脚本执行。](../media/resume-script-run-icon.msft.png)) 。

1. 在 **“编辑器** ”窗格中，将行 `var sum = addend1 + addend2` 替换为 `var sum = parseInt(addend1) + parseInt(addend2)`。

1. 按`Ctrl`+`S` (Windows、Linux) 或`Command`+`S` (macOS) 保存更改。

1. 单击 **“停用断点** (![停用断点。](../media/deactivate-breakpoints-button-icon.msft.png)) 。  它将更改蓝色，以指示选项处于活动状态。  设置“**停用断点**”时，开发工具会忽略你设置的任何断点。

1. 尝试使用具有不同值的演示。  演示现在计算正确。

> [!CAUTION]
> 此工作流仅对从服务器发送的代码的本地副本应用修补程序。  调试项目时，在确定修复后，仍需将该修补程序应用到服务器上的代码，例如编辑本地源代码，然后将固定代码重新部署到服务器。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

祝贺你！  现在，你已了解如何在调试 JavaScript 时充分利用 Microsoft Edge 开发工具。  本文中学习的工具和方法可以为你节省很多时间。

本文演示了设置断点的两种方法。  DevTools 还提供了在满足特定条件时设置断点以暂停代码的方法，例如：

*  仅在提供的条件为 true 时触发的条件断点。
*  已捕获或未捕获异常的断点。
*  请求的 URL 与提供的子字符串匹配时触发的 XHR 断点。

有关何时以及如何使用每种类型的详细信息，请参阅 [使用断点暂停代码](breakpoints.md)。

本文不介绍几个代码单步执行控件。  有关详细信息，请参阅“JavaScript 调试功能”中的[代码行。](reference.md#step-through-code)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [JavaScript 调试功能](reference.md) - 在“源”工具中使用调试器的 UI。
*  [源工具概述](../sources/index.md) - 介绍 JavaScript 调试器和代码编辑器。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
