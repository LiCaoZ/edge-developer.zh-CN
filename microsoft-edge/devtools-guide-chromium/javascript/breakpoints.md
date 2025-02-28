---
title: 使用断点暂停代码
description: 了解在 Microsoft Edge DevTools 中暂停代码的所有方法。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 0b3e8211be1d85dfac5bac71b221c69fd44c8c5a
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631037"
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
# <a name="pause-code-with-breakpoints"></a>使用断点暂停代码

使用断点暂停 JavaScript 代码。  本文介绍 DevTools 中可用的每种类型的断点，以及何时使用以及如何设置每种类型。

有关使用现有网页的介绍性教程，请 [参阅开始调试 JavaScript](index.md)。


<!-- ====================================================================== -->
## <a name="overview-of-when-to-use-each-breakpoint-type"></a>何时使用各断点类型的概述

最著名的断点类型是代码行。  但是，代码行断点的设置可能效率低下，特别是如果你不知道确切的查找位置，或者是否正在使用大型代码库。  可以通过了解如何以及何时使用其他类型的断点来节省调试时间。

| 断点类型 | 使用此类型，如果希望暂停... |
|:--- |:--- |
| [代码行](#line-of-code-breakpoints) | 在代码的准确区域上。  |
| [条件代码行](#conditional-line-of-code-breakpoints) | 在代码的准确区域上，但仅在某些其他条件为 true 时。  |
| [DOM](#dom-change-breakpoints) | 在更改或删除特定 DOM 节点或子节点的代码上。  |
| [XHR](#xhrfetch-breakpoints) | XHR URL 包含字符串模式时。  |
| [事件侦听器](#event-listener-breakpoints) | 在发生事件后运行的代码上，例如 `click`，运行。  |
| [异常](#exception-breakpoints) | 在引发已捕获或未捕获异常的代码行上。  |
| [函数](#function-breakpoints) | 每当运行特定的命令、函数或方法时。  |


<!-- ====================================================================== -->
## <a name="line-of-code-breakpoints"></a>代码行断点

知道需要调查的确切代码区域时，使用代码行断点。  开发工具始终在运行此代码行之前暂停。

在开发工具中设置代码行断点：

1. 选择 **“源** ”工具。

1. 打开包含要中断的代码行的文件。

1. 转到代码行。

1. 代码行的左侧是行号列。  单击它。  一个红色图标 (或最近，一个蓝色矩形箭头) 显示在行号列旁边：

   ![代码行断点。](../media/javascript-sources-page-js-breakpoint-30.msft.png)

### <a name="line-of-code-breakpoints-in-your-code"></a>代码中的代码行断点

从代码运行 `debugger` 方法，以暂停在此行。  这与[代码行断点](#line-of-code-breakpoints)等效，只是断点在代码中设置，而不是在开发工具 UI 中设置的。

```javascript
console.log('a');
console.log('b');
debugger;
console.log('c');
```

### <a name="conditional-line-of-code-breakpoints"></a>条件代码行断点

如果知道需要调查的确切代码区域时，但仅在某些其他条件为 true 时才想暂停，请使用条件代码行断点。

设置条件代码行断点：

1. 选择 **“源** ”工具。

1. 打开包含要中断的代码行的文件。

1. 转到代码行。

1. 代码行的左侧是行号列。  右键单击它。

1. 选择 **“添加条件断点**”。  对话框显示在代码行下方。

1. 在对话框中输入条件。

1. 按 `Enter` 下以激活断点。  红色钻石 (或最近，一个橙色图标) 显示在行号列的顶部：

   ![条件代码行断点。](../media/javascript-sources-page-js-conditional-breakpoint.msft.png)

### <a name="manage-line-of-code-breakpoints"></a>管理代码行断点

使用“**断点**”窗格可禁用或删除单个位置中的代码行断点。

![断点面板。](../media/javascript-sources-page-js-breakpoints-16-33.msft.png)

*  选中条目旁边的复选框以禁用该断点。

*  右键单击条目以删除该断点。

*  右键单击 **“断点** ”窗格中的任意位置，以停用所有断点、禁用所有断点或删除所有断点。  禁用所有断点等效于取消选中每个断点。  取消激活所有断点将指示开发工具忽略所有代码行断点，但也要保持启用状态，以使每个断点都与重新激活每个断点时的状态相同。

![断点窗格中已停用的断点。](../media/javascript-sources-page-js-breakpoints-deactivate-breakpoints.msft.png)


<!-- ====================================================================== -->
## <a name="dom-change-breakpoints"></a>DOM 更改断点

想要暂停更改 DOM 节点或子级的代码时，请使用 DOM 更改断点。

设置 DOM 更改断点类型：

1. 选择 **“元素”** 工具。

1. 转到要设置断点的元素。

1. 右键单击元素，指向 **“中断”**，然后选择 **“子树修改**”、“ **属性修改**”或 **“删除节点**”。

   ![用于创建 DOM 更改断点的上下文菜单。](../media/javascript-elements-break-on-subtree-modifications.msft.png)

### <a name="types-of-dom-change-breakpoints"></a>DOM 更改断点类型

*  **子树修改**。  当删除或添加当前所选节点的子节点或更改子节点的内容时触发。  未在子节点属性更改或当前所选节点的任何更改上触发。

*  **属性修改**：在当前选定的节点上添加或删除属性或在属性值更改时触发。

*  **节点删除**：删除当前选定的节点时触发。


<!-- ====================================================================== -->
## <a name="xhrfetch-breakpoints"></a>XHR/Fetch 断点

当 XHR 的请求 URL 包含指定字符串时，若要中断，请使用 XHR 断点。  开发工具将在 XHR 运行 `send()` 方法的代码行上暂停。

> [!NOTE]
> 此功能还适用于 [Fetch API](https://developer.mozilla.org/docs/Web/API/Fetch_API) 请求。

例如，当网页请求 URL 不正确，并且希望快速找到导致错误请求的 AJAX 或 Fetch 源代码时，这非常有用。

设置 XHR 断点：

1. 选择 **“源** ”工具。

1. 展开“**XHR 断点**”窗格。

1. 单击 **“添加断点**”。

1. 输入要中断的字符串。  当此字符串存在于 XHR 请求 URL 中的任何位置时，开发工具将暂停。

1. 按 `Enter` 下以确认。

![创建 XHR 断点。](../media/javascript-sources-page-js-xhr-fetch-breakpoints-org.msft.png)


<!-- ====================================================================== -->
## <a name="event-listener-breakpoints"></a>事件侦听器断点

如果想在事件触发后运行的事件侦听器代码上暂停时，请使用事件侦听器断点。  可以选择特定事件（例如 `click`）或事件类别，例如所有鼠标事件。

1. 选择 **“源** ”工具。

1. 展开“**事件侦听器断点**”窗格。  开发工具显示事件类别的列表，如 **动画**。

1. 检查这些类别之一可在触发该类别的任何事件时暂停，或展开该类别并检查特定事件。

![创建事件侦听器断点。](../media/javascript-sources-page-js-event-listener-breakpoints-device-deviceorientation.msft.png)


<!-- ====================================================================== -->
## <a name="exception-breakpoints"></a>异常断

想要暂停引发已捕获或未捕获异常的代码行时，请使用异常断点。

1. 选择 **“源** ”工具。

1. 单击“ **暂停异常** (![在异常时暂停。](../media/pause-on-exceptions-icon.msft.png)) 。  图标在启用时变为蓝色。

   ![“暂停异常”按钮。](../media/javascript-sources-page-js-pause-on-exceptions.msft.png)

1. **选：** 如果还希望暂停捕获 **的异常** ，以及未捕获的异常，请选中“暂停捕获异常”复选框。

   ![在未捕获异常时暂停。](../media/javascript-sources-page-js-paused-on-exception.msft.png)


<!-- ====================================================================== -->
## <a name="function-breakpoints"></a>函数断点

如果要在运行特定功能时暂停，请运行 `debug(method)` 方法，其中 `method` 是要调试的命令、函数或方法。  可以插入 `debug()` 代码 (（如 `console.log()` 语句) ）或从 DevTools 控制台运行该方法。

`debug()` 等效于在函数第一行上“[代码行断点](#line-of-code-breakpoints)”设置。

```javascript
function sum(a, b) {
    let result = a + b; // DevTools pauses on this line.
    return result;
}
debug(sum); // Pass the function object, not a string.
sum();
```

### <a name="make-sure-the-target-function-is-in-scope"></a>确保目标函数在作用域内

如果要调试的函数不在范围内，则 DevTools 会引发一个 `ReferenceError` 。

```javascript
(function () {
    function hey() {
        console.log('hey');
    }
    function yo() {
        console.log('yo');
    }
    debug(yo); // This works.
    yo();
})();
debug(hey); // This doesn't work.  hey() is out of scope.
```

从 DevTools 控制台调用 `debug()` 时，下面是一种确保目标函数在范围内的技术：

1. 在函数作用域内的某个位置设置[代码行断点](#line-of-code-breakpoints)。

1. 触发断点。  代码在断点处暂停，当前函数的变量在范围内。

1. 在 DevTools 控制台中调用 `debug()` ，而代码仍然在代码行断点上暂停。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [JavaScript 调试功能](reference.md) - 在 **“源** ”工具中使用调试器的 UI。
*  [开始调试 JavaScript](index.md) - 使用现有网页的介绍性教程。
*  [源工具概述](../sources/index.md) - 调试器是 **源** 工具的一部分，其中包括 JavaScript 编辑器。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/javascript/breakpoints/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
