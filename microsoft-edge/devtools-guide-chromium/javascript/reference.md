---
title: JavaScript 调试功能
description: 在此 Microsoft Edge DevTools 调试功能的全面参考中发现新的调试工作流。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 66df4125bd5515618ce7922bf0ff011885a585c4
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432416"
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
# <a name="javascript-debugging-features"></a>JavaScript 调试功能

本文介绍了如何在 DevTools Microsoft Edge调试器，包括如何设置代码行断点。  若要设置其他类型的断点，请参阅 [使用断点暂停代码](breakpoints.md)。

若要了解调试的基础知识，请参阅开始调试 [JavaScript](index.md)，这是一个使用基于表单的现有网页的教程。  本教程具有屏幕捕获，因此你可以浏览它。  您可以使用演示网页轻松试用调试器功能。


<!-- ====================================================================== -->
## <a name="view-and-edit-javascript-code"></a>查看和编辑 JavaScript 代码

修复 Bug 时，经常希望尝试对 JavaScript 代码进行一些更改。  无需在外部编辑器或 IDE 中进行更改，将文件重新上载到服务器，然后刷新页面;相反，若要测试更改，可以直接在 DevTools 中编辑 JavaScript 代码并立即查看结果。

查看和编辑 JavaScript 文件：

1. 选择 **"源"** 工具。

1. 在 **"导航器"** 窗格中，选择文件，以在"编辑器"窗格中 **打开** 它。

1. 在" **编辑器"** 窗格中，编辑文件。

1. 按 `Ctrl`+`S` (Windows、Linux) 或 `Command`+`S` (macOS) 保存。  然后，DevTools 将 JavaScript 文件加载至 Microsoft Edge。

   :::image type="content" source="../media/javascript-sources-html-minified.msft.png" alt-text="&quot;编辑器&quot;窗格。" lightbox="../media/javascript-sources-html-minified.msft.png":::


<!-- ====================================================================== -->
## <a name="reformat-a-minified-javascript-file-with-pretty-print"></a>使用非常打印重新设置缩小的 JavaScript 文件

**** 若要使缩小的文件可读，请单击![](../media/format-icon.msft.png)"设置 (格式"。) "窗格底部的"设置格式 **"** 按钮。

:::image type="content" source="../media/javascript-sources-html-non-minified.msft.png" alt-text="&quot;格式&quot;按钮。" lightbox="../media/javascript-sources-html-non-minified.msft.png":::


<!-- ====================================================================== -->
## <a name="set-a-breakpoint-to-pause-code"></a>设置断点以暂停代码

若要在运行时期间暂停代码，请设置一个断点。  最基本的和已知的断点类型是代码行断点。

知道需要调查的确切代码区域时，使用代码行断点。  DevTools 始终在指定的代码行暂停，然后再运行它。

设置代码行断点：

1. 选择 **"源"** 工具。

1. 打开包含代码行的文件。

1. 单击代码行的行号左侧的区域。  或者，右键单击行号，然后选择" **添加断点"**。  然后，行号旁边会出现一个红色圆圈，指示断点。

   :::image type="content" source="../media/javascript-sources-page-js-breakpoint-30.msft.png" alt-text="代码行断点。" lightbox="../media/javascript-sources-page-js-breakpoint-30.msft.png":::

代码行断点设置效率可能很低，尤其是在您不知道具体查找位置或代码库较大时。  若要在调试时节省时间，请了解如何以及何时使用其他类型的断点。  请参阅 [使用断点暂停代码](breakpoints.md)。


<!-- ====================================================================== -->
## <a name="step-through-code"></a>单步执行代码

在断点暂停代码后，逐步执行代码，一次一行，一直调查控制流和属性值。

### <a name="step-over-line-of-code"></a>逐步执行代码

在包含与正在调试的问题不相关的函数的一行代码上暂停时，单击"单步**执行 (** ![](../media/step-over-icon.msft.png) 单步执行"。单击) 按钮，无需单步执行即可运行函数。

:::image type="content" source="../media/javascript-source-page-debugger-step-over-next-function-call.msft.png" alt-text="单击&quot;逐步执行&quot;。" lightbox="../media/javascript-source-page-debugger-step-over-next-function-call.msft.png":::

例如，假设您正在调试以下代码段。

```javascript
function updateHeader() {
    var day = new Date().getDay();
    var name = getName(); // A
    updateName(name); // D
}
function getName() {
    var name = app.first + ' ' + app.last; // B
    return name; // C
}
```

你已在 `A` 上暂停。  单击"单步 **执行"** 后，DevTools 将运行要单步执行的函数中的所有代码，即 和 `B` `C`。  DevTools 随后在 `D` 上暂停。

### <a name="step-into-line-of-code"></a>逐行执行代码

当暂停**** ![](../media/step-into-icon.msft.png) 包含与正在调试的问题相关的函数调用的代码行时，请单击"单步执行 (单步执行") 按钮以进一步调查该函数。

:::image type="content" source="../media/javascript-source-page-debugger-step-into-next-function-call.msft.png" alt-text="单击&quot;进入&quot;。" lightbox="../media/javascript-source-page-debugger-step-into-next-function-call.msft.png":::

例如，假设您正在调试以下代码：

```javascript
function updateHeader() {
    var day = new Date().getDay();
    var name = getName(); // A
    updateName(name);
}
function getName() {
    var name = app.first + ' ' + app.last; // B
    return name;
}
```

你已在 `A` 上暂停。  单击"进入 **"后**，DevTools 将运行此代码行，然后在 上暂停 `B`。

### <a name="step-out-of-line-of-code"></a>执行剩余代码

当暂停在与正在调试的问题不相关的函数内时，单击"**步骤 (** ![](../media/step-out-icon.msft.png) 步骤"。) 按钮以运行函数的其余代码。

:::image type="content" source="../media/javascript-source-page-debugger-step-out-of-current-function.msft.png" alt-text="单击&quot;退出&quot;。" lightbox="../media/javascript-source-page-debugger-step-out-of-current-function.msft.png":::

例如，假设您正在调试以下代码：

```javascript
function updateHeader() {
    var day = new Date().getDay();
    var name = getName();
    updateName(name); // C
}
function getName() {
    var name = app.first + ' ' + app.last; // A
    return name; // B
}
```

你已在 `A` 上暂停。  在单击 **"步骤"** 后，DevTools `getName()``B` 将运行 中代码的其余部分，该代码仅在此示例中运行，然后在 上暂停`C`。

### <a name="run-all-code-up-to-a-specific-line"></a>运行所有代码到特定行

调试长函数时，可能有许多代码与正在调试的问题不相关。

*  您可以逐一浏览所有行，但很繁琐。

*  稍微好一些，可以在感兴趣的行上设置代码行断点，然后单击 Resume **脚本**![执行 (Resume 脚本](../media/resume-script-run-icon.msft.png)执行。) 按钮。

*  但有一种更快的方法：右键单击代码行，然后选择"继续 **在此处"**。  DevTools 会运行所有代码，一直运行到该处，然后暂停到该行。

:::image type="content" source="../media/javascript-source-page-continue-to-here.msft.png" alt-text="选择&quot;继续&quot;至此处。" lightbox="../media/javascript-source-page-continue-to-here.msft.png":::

### <a name="restart-the-top-function-of-the-call-stack"></a>重新启动调用的顶部函数

若要暂停调用堆栈中顶级函数的第一行，同时在一行代码上暂停，请右键单击"调用堆栈"窗格****，然后选择"**重新启动帧"**。  top 函数是最后一个运行的函数。

以下代码是一个分步执行示例：

```javascript
function factorial(n) {
    var product = 0; // B
    for (var i = 1; i <= n; i++) {
      product += i;
    }
    return product; // A
}
```

你已在 `A` 上暂停。  选择" **重新启动帧**"后，应暂停 on `B`，而不会设置断点或选择 **"恢复脚本执行"**。

:::image type="content" source="../media/javascript-source-page-debugger-restart-frame.msft.png" alt-text="选择重启帧。" lightbox="../media/javascript-source-page-debugger-restart-frame.msft.png":::

### <a name="resume-script-runtime"></a>恢复脚本运行时

若要在脚本暂停后继续运行时，请单击 Resume **脚本**![执行 (Resume 脚本](../media/resume-script-run-icon.msft.png)执行。) 按钮。  DevTools 将一直运行脚本，直到下一个断点（如果有）。

:::image type="content" source="../media/javascript-sources-get-started-js-resume-script-runtime.msft.png" alt-text="单击&quot;恢复脚本执行&quot;按钮。" lightbox="../media/javascript-sources-get-started-js-resume-script-runtime.msft.png":::

#### <a name="force-script-runtime"></a>强制脚本运行时

若要忽略所有断点**** 并强制脚本继续运行，请单击并按住 Resume **脚本**执行 (![Resume 脚本执行](../media/resume-script-run-icon.msft.png)。) ![按钮，然后单击"强制脚本执行 (强制脚本](../media/force-script-run-icon.msft.png)执行"。) 按钮。

:::image type="content" source="../media/javascript-sources-get-started-js-force-script-runtime.msft.png" alt-text="单击&quot;强制脚本执行&quot;按钮。" lightbox="../media/javascript-sources-get-started-js-force-script-runtime.msft.png":::

### <a name="change-thread-context"></a>更改线程上下文

使用 Web 工作人员或服务工作者时，单击"线程"窗格中列出的上下文以**** 切换到该上下文。  蓝色箭头图标表示当前选定的上下文。

:::image type="content" source="../media/javascript-sources-main-min-js-threads.msft.png" alt-text="&quot;线程&quot;窗格。" lightbox="../media/javascript-sources-main-min-js-threads.msft.png":::

例如，你在主脚本和服务工作进程脚本的断点上暂停。  您希望查看服务工作器上下文的本地和全局属性，但 **Sources** 工具显示主脚本上下文。  若要切换到服务工作器上下文，请在" **线程** "窗格中，单击服务工作器条目。


<!-- ====================================================================== -->
## <a name="view-and-edit-properties-and-variables"></a>查看和编辑属性和变量

在代码行上暂停时，使用“**范围**”窗格查看和编辑本地、关闭和全局范围中的属性和变量的值。

*  双击某个属性值以更改该值。
*  不可枚举的属性显示为灰色。

:::image type="content" source="../media/javascript-sources-get-started-js-scope.msft.png" alt-text="&quot;范围&quot;窗格。" lightbox="../media/javascript-sources-get-started-js-scope.msft.png":::


<!-- ====================================================================== -->
## <a name="watch-the-values-of-javascript-expressions"></a>观看 JavaScript 表达式的值

使用“**监视**”窗格观察自定义表达式的值。  你可以观看任何有效的 JavaScript 表达式。

:::image type="content" source="../media/javascript-sources-get-started-js-watch.msft.png" alt-text="&quot;监视&quot;窗格。" lightbox="../media/javascript-sources-get-started-js-watch.msft.png":::

*  若要创建新的监视表达式，请单击"****![添加监视表达式 (添加监视](../media/add-expression-icon.msft.png)表达式) 按钮。

*  若要刷新所有现有表达式的值，请单击****!["刷新" ("](../media/refresh-icon.msft.png)刷新) 按钮。  逐步执行代码时，值将自动刷新。

*  若要删除监视表达式，请右键单击该表达式****![，然后选择"删除监视表达式 (删除监视](../media/delete-expression-icon.msft.png)表达式。) 。


<!-- ====================================================================== -->
## <a name="view-the-call-stack"></a>查看调用堆栈

在代码行上暂停时，使用“**调用堆叠**”窗格查看让你到达此点的调用堆叠。

<!--If you are working with async code, check the **Async** checkbox to enable async call stacks.  -->

单击一个条目以跳转到调用该函数的代码行。  蓝色箭头图标表示 DevTools 当前突出显示的函数。

:::image type="content" source="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty.msft.png" alt-text="&quot;调用堆栈&quot;窗格。" lightbox="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty.msft.png":::

> [!NOTE]
> 当未在代码行上暂停时，“**调用堆叠**”窗格为空。

### <a name="copy-stack-trace"></a>复制堆叠跟踪

<!--
This should be moved to an "Export debug data" H2 section when there is enough content for that, but there isn't right now, so it is here.
-->

若要将当前调用堆栈复制到剪贴板，请右键单击"**** 调用堆栈"窗格，然后选择"**复制堆栈跟踪"**。

:::image type="content" source="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-copy-stack-trace.msft.png" alt-text="复制堆栈跟踪命令。" lightbox="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-copy-stack-trace.msft.png":::

以下代码是一个输出示例：

```javascript
getNumber1 (get-started.js:35)
inputsAreEmpty (get-started.js:22)
onClick (get-started.js:15)
```


<!-- ====================================================================== -->
## <a name="ignore-a-script-or-pattern-of-scripts"></a>忽略脚本或脚本模式

若你想要在调试时忽略该脚本，请将脚本标记为库代码。  被标记为库代码时，脚本会在“**调用堆叠**”窗格中被遮盖，且你在单步执行代码时绝不会单步执行脚本的函数。

例如，在下面的代码段中，行 `A` 使用 `lib`，这是第三方库。  如果您确信正在调试的问题与第三方库不相关，那么将脚本标记为库代码 **是有意义的**。

```javascript
function animate() {
    prepare();
    lib.doFancyStuff(); // A
    render();
}
```

### <a name="mark-a-script-as-library-code-from-the-editor-pane"></a>在编辑器窗格中将脚本标记为库代码

若要从编辑器窗格中**将脚本标记为****库代码：**

1. 打开文件。

1. 右键单击文件中的任何位置，然后选择"添加脚本****"以忽略之前 (标记为库**代码) **。

   :::image type="content" source="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-editor-mark-as-library-code.msft.png" alt-text="从编辑器窗格中将脚本标记为库代码。" lightbox="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-editor-mark-as-library-code.msft.png":::

### <a name="mark-a-script-as-library-code-from-the-call-stack-pane"></a>从调用堆叠窗格中将脚本标记为库代码

若要从"调用堆栈 **"窗格中将** 脚本 **标记为库** 代码：

*  右键单击脚本中的函数，然后选择"添加脚本****"以忽略之前 (标记为**库代码的列表**) 。

   :::image type="content" source="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-call-stack-mark-as-library-code.msft.png" alt-text="从&quot;调用堆栈&quot;窗格中将脚本标记为库代码。" lightbox="../media/javascript-glitch-debug-js-sources-get-started-inputs-are-empty-call-stack-mark-as-library-code.msft.png":::

### <a name="mark-a-script-as-library-code-from-settings"></a>在设置中将脚本标记为库代码

若要标记单个脚本或脚本模式，**设置**：

1. 打开“[设置](../customize/index.md)”。

1. 导航到“**库代码**”设置。

1. 单击 **"添加模式"**。

1. 输入脚本名称或脚本名称的正则表达式模式，以标记为**库代码**。

1. 单击**添加**。

   :::image type="content" source="../media/javascript-framework-library-code.msft.png" alt-text="将脚本标记为库中的库设置。" lightbox="../media/javascript-framework-library-code.msft.png":::


<!-- ====================================================================== -->
## <a name="run-snippets-of-debug-code-from-any-page"></a>从任何页面运行调试代码的代码段

如果你的控制台一次又一次地运行相同的调试代码，请考虑使用代码段。  代码段是你在 DevTools 中创作、存储和运行的运行时脚本。

请参阅 [在任何网页上运行 JavaScript 代码段](snippets.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [JavaScript 调试入门](index.md) - 使用现有代码的简单简短教程，包含屏幕捕获。
*  [源工具概述](../sources/index.md) - **源工具** 包括 JavaScript 调试程序和编辑程序。
*  [禁用 JavaScript](disable.md)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
