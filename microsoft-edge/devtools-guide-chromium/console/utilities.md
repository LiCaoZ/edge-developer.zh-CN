---
title: 控制台工具实用功能和选择器
description: 在开发人员工具的控制台工具中提供的便利实用程序函数、命令和 DOM Microsoft Edge，但不能通过 JavaScript 源文件使用。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 1a23d1e4909c1099e3e7bfe3b7255f2d2dbf2adf
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431814"
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
# <a name="console-tool-utility-functions-and-selectors"></a>控制台工具实用功能和选择器
<!-- orig:
# Console Utilities API reference
-->

控制台实用程序 API 包含一组用于执行常见任务的便利函数，例如：
*  选择并检查 DOM 元素。
*  以可读格式显示数据。
*  停止并启动探查器。
*  监视 DOM 事件。

这些命令仅能直接输入到 DevTools **控制台中**;无法从脚本调用这些命令。


<!-- ====================================================================== -->
## <a name="summary"></a>摘要

| 函数 | 说明 |
|---|---|
| [$_](#recently-evaluated-expression) | 返回最近计算表达式的值。 |
| [$0 - $4](#recently-selected-element-or-javascript-object) | 返回最近选定的元素或 JavaScript 对象。 |
| [$ (选择器) ](#query-selector) | 查询选择器;返回对具有指定 CSS 选择器的第一个 DOM 元素的引用，如 `document.querySelector()`。 |
| [$$ (选择器 [startNode]) ](#query-selector-all) | 查询选择器全部;返回匹配指定 CSS 选择器的元素数组，如 `document.querySelectorAll()`。 |
| [$x (路径 [startNode]) ](#xpath) | 返回一个匹配指定 XPath 表达式的 DOM 元素数组。 |
| [clear () ](#clear) | 清除其历史记录的控制台。 |
| [复制 (对象) ](#copy) | 将指定对象的字符串表示形式复制到剪贴板。 |
| [调试 (函数) ](#debug) | 调用指定的函数时，将调用调试程序，并中断"源"面板上的函数。 |
| [dir (对象) ](#dir) | 显示指定对象的所有属性的对象样式列表，如 `console.dir()`。 |
| [dirxml (对象) ](#dirxml) | 打印指定对象的 XML 表示形式，如 在 **元素** 工具中显示 `console.dirxml()`。 |
| [检查 (对象/函数) ](#inspect) | 在"元素"工具中打开并选择指定的 DOM **** 元素，或在"内存"工具中打开并选择指定的 JavaScript **堆**对象。 |
| [getEventListeners (对象) ](#geteventlisteners) | 返回在指定对象上注册的事件侦听器。 |
| [键 (对象) ](#keys) | 返回一个数组，其中包含属于指定对象的属性的名称。 |
| [monitor (function) ](#monitor) | 向控制台记录一条消息，指示函数名称，以及作为请求的一部分传递给函数的参数。 |
| [monitorEvents (对象[， events]) ](#monitorevents) | 当指定对象上发生指定事件之一时，该事件对象将记录到控制台。 |
| [配置文件 ([name]) ](#profile) | 使用可选名称启动 JavaScript CPU 分析会话。 |
| [profileEnd ([name]) ](#profileend) | 完成 JavaScript CPU 分析会话，并显示内存工具 **中** 的结果。 |
| [queryObjects (构造函数) ](#queryobjects) | 返回由指定构造函数创建的对象的数组。 |
| [table (data[， columns]) ](#table) | 记录指定数据对象的对象数据（格式化为带列标题的表）。 |
| [undebug (function) ](#undebug) | 停止对指定函数的调试，以便请求该函数时，不再调用调试程序。 |
| [unmonitor (function) ](#unmonitor) | 停止对指定函数的监视。 |
| [unmonitorEvents (object[， events]) ](#unmonitorevents) | 停止监视指定对象和事件的事件。 |
| [值 (对象) ](#values) | 返回一个数组，其中包含属于指定对象的所有属性的值。 |

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="recently-evaluated-expression"></a>最近计算表达式
<!-- planned new heading to troubleshoot: -->
<!-- ## $_ (Recent expression value) -->

<!-- summary to bubble up: -->
返回最近计算表达式的值。

### <a name="syntax"></a>语法

```javascript
$_
```

### <a name="example"></a>示例

在下图中，计算一个 () `2+2` 表达式。  然后 `$_` 计算属性，其中包含相同的值：

:::image type="content" source="../media/console-arithmatic.msft.png" alt-text="$_ 是最近评估的表达式。" lightbox="../media/console-arithmatic.msft.png":::

在下图中，计算表达式最初包含一个名称数组。  计算以`$_.length`查找数组的长度`$_`，存储在 中的值现在将成为最新的计算表达式： `4`

:::image type="content" source="../media/console-array-length.msft.png" alt-text="$_ 在评估新命令时发生更改。" lightbox="../media/console-array-length.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="recently-selected-element-or-javascript-object"></a>最近选择的元素或 JavaScript 对象
<!-- planned new heading to troubleshoot: -->
<!-- ## $0 - $4 -->

<!-- summary to bubble up: -->
返回最近选定的元素或 JavaScript 对象。

<!-- add'l info -->
`$0` 返回最近选择的元素或 JavaScript 对象 `$1` ，返回第二个最近选择的元素，等等。  `$1`、 `$0`、 `$2`和 `$3``$4` 命令用作对在 **Elements** 工具中检查的最后五个 DOM 元素或内存工具中选定的最后五个 JavaScript 堆对象**的历史引用。**

### <a name="syntax"></a>语法

```javascript
$0
```

### <a name="example"></a>示例

在下图中，在 `img` "元素"工具中 **选择了元素** 。  在 **控制台** 箱中 `$0` ，已进行评估并显示相同的元素：

:::image type="content" source="../media/console-image-highlighted-$0.msft.png" alt-text="$0 命令。" lightbox="../media/console-image-highlighted-$0.msft.png":::

下图显示了在同一网页中选定的不同元素。  现在 `$0` 引用新选择的元素，而 `$1` 返回之前选择的元素：

:::image type="content" source="../media/console-image-highlighted-$1.msft.png" alt-text="$1 命令。" lightbox="../media/console-image-highlighted-$1.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="query-selector"></a>查询选择器
<!-- planned new heading to troubleshoot: -->
<!-- ## $(selector) -->

<!-- summary to bubble up: -->
查询选择器;返回对具有指定 CSS 选择器的第一个 DOM 元素的引用，如 `document.querySelector()`。

<!-- add'l info -->
此函数是 [document.querySelector () 函数的 ](https://developer.mozilla.org/docs/Web/API/Document/querySelector) 别名。

### <a name="syntax"></a>语法

```javascript
$(selector, [startNode])
```

### <a name="example"></a>示例

在下图中， `$('img')` 返回对网页中第一 `<img>` 个元素的引用：

:::image type="content" source="../media/console-element-selector-image.msft.png" alt-text="$ ( img') 返回对网页中第一<img> 元素的引用。" lightbox="../media/console-element-selector-image.msft.png":::

右键单击返回的结果，然后选择"元素面板 **中的** 展示"以在 DOM 中查找它，或滚动到 **视图** 以显示在页面上。

### <a name="example"></a>示例

以下示例返回对当前选定元素的引用并显示其 `src` 属性：

```javascript
$('img').src
```

结果：

:::image type="content" source="../media/console-element-selector-image-source.msft.png" alt-text="$ ( img') .src 的结果。" lightbox="../media/console-element-selector-image-source.msft.png":::

此函数还支持第二个参数 `startNode`，用于指定要搜索元素的元素或节点。  参数的默认值为 `document`。

### <a name="example"></a>示例

```javascript
$('img', document.querySelector('title--image')).src
```

Result：找到 `img` 元素后的第一 `title--image` 个元素， `src` 并 `img` 返回 元素的 属性：

:::image type="content" source="../media/console-element-selector-image-filter-source.msft.png" alt-text="$ ('img'， document.querySelector ('title--image') ) .src 的结果。" lightbox="../media/console-element-selector-image-filter-source.msft.png":::

> [!NOTE]
> 如果使用的库（如 jQuery `$`）使用 ， `$` 则功能将被覆盖，并且对应于该库中的实现。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="query-selector-all"></a>查询选择器全部
<!-- planned new heading to troubleshoot: -->
<!-- ## \$\$(selector, \[startNode\]) -->

<!-- summary to bubble up: -->
查询选择器全部;返回匹配指定 CSS 选择器的元素数组，如 `document.querySelectorAll()`。

<!-- add'l info -->
此函数等效于 [document.querySelectorAll () ](https://developer.mozilla.org/docs/Web/API/Document/querySelectorAll)。

### <a name="syntax"></a>语法

```javascript
$$(selector, [startNode])
```

### <a name="example"></a>示例

在下面的示例中，创建 `$$()` 当前 `<img>` 网页中所有元素的数组， `src` 并显示每个元素的 属性值：

```javascript
var images = $$('img');
for (each in images) {
    console.log(images[each].src);
}
```

结果：

:::image type="content" source="../media/console-element-selector-image-all.msft.png" alt-text="使用 $$ () 选择网页中所有图像并显示源。" lightbox="../media/console-element-selector-image-all.msft.png":::

此查询选择器函数还支持第二 `startNode`个参数 ，用于指定要搜索的元素或节点。  参数的默认值为 `document`。

### <a name="example"></a>示例

以下示例的以下`$$()``<img>`修改版本用于创建一个数组，该数组包含当前网页中选定节点之后出现的所有元素：

```javascript
var images = $$('img', document.querySelector(`title--image`));
for (each in images) {
   console.log(images[each].src);
}
```

结果如下。  `$$()` 选择网页中指定元素之后 `<div>` 显示的所有图像，并显示源：

:::image type="content" source="../media/console-element-selector-image-filter-all.msft.png" alt-text="使用 $$ () 选择在网页中的 <div> 元素后显示的所有图像并显示源。" lightbox="../media/console-element-selector-image-filter-all.msft.png":::

> [!NOTE]
> 在 `Shift`+`Enter` 控制台 **中按** 以启动新行，而不运行脚本。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="xpath"></a>XPath
<!-- planned new heading to troubleshoot: -->
<!-- ## \$x(path, \[startNode\]) -->

<!-- summary to bubble up: -->
返回一个匹配指定 XPath 表达式的 DOM 元素数组。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
$x(path, [startNode])
```

### <a name="example"></a>示例

在下面的示例中，将返回 `<p>` 网页上的所有元素：

```javascript
$x("//p")
```

结果：

:::image type="content" source="../media/console-array-xpath.msft.png" alt-text="使用 XPath 选择器。" lightbox="../media/console-array-xpath.msft.png":::

### <a name="example"></a>示例

在下面的示例中，将返回 `<p>` 包含元素的所有 `<a>` 元素：

```javascript
$x("//p[a]")
```

结果：

:::image type="content" source="../media/console-array-xpath-sub-element.msft.png" alt-text="使用更复杂的 XPath 选择器。" lightbox="../media/console-array-xpath-sub-element.msft.png":::

与其他选择器命令类似 `$x(path)` ，具有 `startNode`可选的第二个参数 ，用于指定要搜索的元素或节点：

:::image type="content" source="../media/console-array-xpath-startnode.msft.png" alt-text="将 XPath 选择器与 startNode 一同使用。" lightbox="../media/console-array-xpath-startnode.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="clear"></a>clear
<!-- planned new heading to troubleshoot: -->
<!-- ## clear() -->

<!-- summary to bubble up: -->
清除其历史记录的控制台。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
clear()
```

### <a name="example"></a>示例

```javascript
clear()
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="copy"></a>copy
<!-- ## copy(object) -->

<!-- summary to bubble up: -->
将指定对象的字符串表示形式复制到剪贴板。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
copy(object)
```

### <a name="example"></a>示例

```javascript
copy($0)
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="debug"></a>调试
<!-- ## debug(function) -->

<!-- summary to bubble up: -->
调用指定的函数时，将调用调试程序，并中断"源"面板上的函数。

<!-- add'l info -->
暂停调试程序后，你可以逐步执行代码并调试它。

### <a name="syntax"></a>语法

```javascript
debug(function)
```

>[!NOTE]
> 错误[Chromium #1050237](https://crbug.com/1050237)跟踪函数的 `debug()` Bug。  如果遇到问题，请尝试改为 [使用断](../javascript/breakpoints.md) 点。

### <a name="example"></a>示例

```javascript
debug("debug");
```

结果：

:::image type="content" source="../media/console-debug-text.msft.png" alt-text="使用 debug () 在函数内中断。" lightbox="../media/console-debug-text.msft.png":::

用于 `undebug(function)` 停止在 函数上中断，或使用 UI 关闭所有断点。

有关断点详细信息，请参阅 [使用断点暂停代码](../javascript/breakpoints.md)。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="dir"></a>dir
<!-- ## dir(object) -->

<!-- summary to bubble up: -->
显示指定对象的所有属性的对象样式列表，如 `console.dir()`。

<!-- add'l info -->
此函数是 [console.dir () 的别名 ](https://developer.mozilla.org/docs/Web/API/Console/dir)。

### <a name="syntax"></a>语法

```javascript
dir(object)
```

在 `document.head` 控制台 **中进行评估** ，以显示 和 标记之间的 `<head>` `</head>` HTML。

### <a name="example"></a>示例

在下面的示例中，在控制台使用 `console.dir()` 后将显示对象样式 **列表**：

```javascript
document.head;
dir(document.head);
```

结果：

:::image type="content" source="../media/console-dir-document-head-expanded.msft.png" alt-text="使用&quot;dir () &quot;函数记录&quot;document.head&quot;。" lightbox="../media/console-dir-document-head-expanded.msft.png":::

有关详细信息，请参阅控制台 API 中的 [console.dir () ](api.md#dir) 。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="dirxml"></a>dirxml
<!-- ## dirxml(object) -->

<!-- summary to bubble up: -->
打印指定对象的 XML 表示形式，如 在 **元素** 工具中显示 `console.dirxml()`。

<!-- add'l info -->
此函数等效于 [console.dirxml () ](https://developer.mozilla.org/docs/Web/API/Console/dirxml)。

### <a name="syntax"></a>语法

```javascript
dirxml(object)
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="inspect"></a>inspect
<!-- ## inspect(object/function) -->

<!-- summary to bubble up: -->
在"元素"工具中打开并选择指定的 DOM **** 元素，或在"内存"工具中打开并选择指定的 JavaScript **堆**对象。

<!-- add'l info -->
* 对于 DOM 元素，此函数在"元素"工具中打开 **并选择指定的** DOM 元素。
* 对于 JavaScript 堆对象，此函数在 Memory 工具中打开指定的 JavaScript **堆** 对象。

### <a name="syntax"></a>语法

```javascript
inspect(object/function)
```

### <a name="example"></a>示例

在下面的示例中，将在 `document.body` "元素"工具 **中** 打开：

```javascript
inspect(document.body);
```

结果：

:::image type="content" source="../media/console-inspect-document-body.msft.png" alt-text="使用 inspect () 检查元素。" lightbox="../media/console-inspect-document-body.msft.png":::

传递要检查的函数时，该函数将在 **"** 源"工具中打开网页供你检查。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="geteventlisteners"></a>getEventListeners
<!-- ## getEventListeners(object) -->

<!-- summary to bubble up: -->
返回在指定对象上注册的事件侦听器。

<!-- add'l info -->
返回值是包含每个已注册事件类型（如 或) ） (`click` 数组 `keydown` 的对象。  每个数组的成员是描述为每种类型注册的侦听器的对象。

### <a name="syntax"></a>语法

```javascript
getEventListeners(object)
```

### <a name="example"></a>示例

在下面的示例中，将 `document` 列出在对象上注册的所有事件侦听器：

```javascript
getEventListeners(document);
```

结果：

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document.msft.png" alt-text="使用 getEventListeners 文档 (输出) 。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document.msft.png":::

如果指定对象上注册了多个侦听器，则数组将包含每个侦听器的成员。  在下图中，在 事件的 `document` 元素上注册了两个事件 `click` 侦听器：

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document-expanded-1.msft.png" alt-text="在&quot;document&quot;元素上为&quot;click&quot;事件注册多个事件侦听器。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document-expanded-1.msft.png":::

可以进一步展开以下每个对象来浏览其属性。  下面是侦听器对象的扩展视图：

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document-2.msft.png" alt-text="侦听器对象的扩展视图。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document-2.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="keys"></a>键
<!-- ## keys(object) -->

<!-- summary to bubble up: -->
返回一个数组，其中包含属于指定对象的属性的名称。

<!-- add'l info -->
若要获取相同属性的关联值，请使用 `values()`。

### <a name="syntax"></a>语法

```javascript
keys(object)
```

### <a name="example"></a>示例

假设应用程序定义了以下对象：

```javascript
var player1 = {"name": "Ted", "level": 42}
```

在下面的代码中，`player1`为了简单起见， (在键入和在控制台) 全局`keys(player1)``values(player1)`命名空间中定义结果：

```javascript
keys(player1)

values(player1)
```

结果：

:::image type="content" source="../media/console-keys-values.msft.png" alt-text="键 () 和值 () 命令。" lightbox="../media/console-keys-values.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="monitor"></a>监视器
<!-- ## monitor(function) -->

<!-- summary to bubble up: -->
向控制台记录一条消息，指示函数名称，以及作为请求的一部分传递给函数的参数。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
monitor(function)
```

### <a name="example"></a>示例

```javascript
function sum(x, y) {
    return x + y;
}
monitor(sum);
```

结果：

:::image type="content" source="../media/console-function-monitor-sum.msft.png" alt-text="监视器 () 函数的结果。" lightbox="../media/console-function-monitor-sum.msft.png":::

若要结束监视，请使用 `unmonitor(function)`。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="monitorevents"></a>monitorEvents
<!-- ## monitorEvents(object\[, events\]) -->

<!-- summary to bubble up: -->
当指定对象上发生指定事件之一时，该事件对象将记录到控制台。

<!-- add'l info -->
可以指定要监视的单个事件、事件数组或映射到预定义的事件集合中的一个泛型事件类型。

### <a name="syntax"></a>语法

```javascript
monitorEvents(object[, events])
```

### <a name="example"></a>示例

以下代码监视 window 对象上的所有调整大小事件：

```javascript
monitorEvents(window, "resize");
```

结果：

:::image type="content" source="../media/console-monitor-events-resize-window.msft.png" alt-text="监视窗口调整大小事件。" lightbox="../media/console-monitor-events-resize-window.msft.png":::

### <a name="example"></a>示例

以下代码定义一个数组，用于`resize``scroll`监视窗口对象上的 和 事件：

```javascript
monitorEvents(window, ["resize", "scroll"]);
```

### <a name="specifying-an-event-type"></a>指定事件类型

还可以指定一种可用的事件类型，即映射到预定义的事件集的字符串。  下表显示了可用的事件类型和关联的事件映射：

| 事件类型 | 相应的映射事件 |
|:--- |:--- |
| `mouse` | "click"、"dblclick"、"mousedown"、"mousemove"、"mouseout"、"mouseover"、"mouseup"、"mousewheel" |
| `key` | "keydown"、"keypress"、"keyup"、"textInput" |
| `touch` | "touchcancel"、"touchend"、"touchmove"、"touchstart" |
| `control` | "blur"、"change"、"focus"、"reset"、"resize"、"scroll"、"select"、"submit"、"zoom" |

### <a name="example"></a>示例

In the following code， the `key` event type corresponding to `key` events on an input text field are currently selected in the **Elements** tool：

```javascript
monitorEvents($0, "key");
```

下面是在文本字段中键入字符后的示例输出：

:::image type="content" source="../media/console-monitor-events-type-t-y.msft.png" alt-text="监视关键事件。" lightbox="../media/console-monitor-events-type-t-y.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="profile"></a>profile
<!-- ## profile([name]) -->

<!-- summary to bubble up: -->
使用可选名称启动 JavaScript CPU 分析会话。

<!-- add'l info -->
若要完成配置文件并显示内存工具 **中的结果，** 请调用 [profileEnd () ](#profileend)。  <!-- See [Speed Up JavaScript Runtime](../rendering-tools/js-runtime.md).  -->

### <a name="syntax"></a>语法

```javascript
profile([name])
```

### <a name="example"></a>示例

若要开始分析，请调用 `profile()`：

```javascript
profile("My profile")
```

若要停止分析和在内存工具中 **显示** 结果，请调用 [profileEnd () ](#profileend)。

还可以嵌套配置文件：

```javascript
profile('A');
profile('B');
profileEnd('A');
profileEnd('B');
```

无论顺序如何，结果都是相同的。  结果在内存工具中显示为堆 **快照，包含** 分组的配置文件：

:::image type="content" source="../media/console-memory-multiple-cpu-profiles.msft.png" alt-text="分组配置文件。" lightbox="../media/console-memory-multiple-cpu-profiles.msft.png":::

> [!NOTE]
> 多个 CPU 配置文件可以同时运行，并且不需要按照创建顺序关闭每个配置文件。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="profileend"></a>profileEnd
<!-- ## profileEnd([name]) -->

<!-- summary to bubble up: -->
完成 JavaScript CPU 分析会话，并显示内存工具 **中** 的结果。

<!-- add'l info -->
若要调用此函数，必须运行 [profile () ](#profile) 函数。  <!-- See [Speed Up JavaScript Runtime](../rendering-tools/js-runtime.md).  -->

### <a name="syntax"></a>语法

```javascript
profileEnd([name])
```

### <a name="example"></a>示例

1. 运行 [profile () ](#profile) 函数以开始分析。

1. 运行 函数 `profileEnd()` 以停止分析，在内存工具 **中显示** 结果：

    ```javascript
    profileEnd("My profile")
    ```

有关详细信息，请参阅 [上面的配置文件](#profile)。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="queryobjects"></a>queryObjects
<!-- ## queryObjects(Constructor) -->

<!-- summary to bubble up: -->
返回由指定构造函数创建的对象的数组。

<!-- add'l info -->
的范围 `queryObjects()` 是控制台中当前选择的运行时 **上下文**。

### <a name="syntax"></a>语法

```javascript
queryObjects(Constructor)
```

### <a name="example"></a>示例

* `queryObjects(promise)` 返回 的所有实例 `Promise`。

* `queryObjects(HTMLElement)` 返回所有 HTML 元素。

*  `queryObjects(functionName)` 返回使用 实例化的所有对象 `new functionName()`。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="table"></a>table
<!-- ## table(data\[, columns\]) -->

<!-- summary to bubble up: -->
记录指定数据对象的对象数据（格式化为带列标题的表）。

<!-- add'l info: n/a -->
例如，使用此函数，可以在控制台中将人员姓名列表显示为 **表**。

### <a name="syntax"></a>语法

```javascript
table(data[, columns])
```

### <a name="example"></a>示例

以下代码使用控制台中的表显示名称列表，列标题默认为变量名称：

```javascript
var names = {
    0: {
        firstName:  "John",
        lastName:  "Smith"
    },
    1:  {
        firstName:  "Jane",
        lastName:  "Doe"
    }
};
table(names);
```

结果：

:::image type="content" source="../media/console-table-display.msft.png" alt-text="table () 函数的结果。" lightbox="../media/console-table-display.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="undebug"></a>undebug
<!-- ## undebug(function) -->

<!-- summary to bubble up: -->
停止对指定函数的调试，以便请求该函数时，不再调用调试程序。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
undebug(function)
```

### <a name="example"></a>示例

```javascript
undebug(getData);
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="unmonitor"></a>unmonitor
<!-- ## unmonitor(function) -->

<!-- summary to bubble up: -->
停止对指定函数的监视。

<!-- add'l info -->
此函数与 [monitor () 一同使用 ](#monitor)。

### <a name="syntax"></a>语法

```javascript
unmonitor(function)
```

### <a name="example"></a>示例

```javascript
unmonitor(getData);
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="unmonitorevents"></a>unmonitorEvents
<!-- ## unmonitorEvents(object\[, events\]) -->

<!-- summary to bubble up: -->
停止监视指定对象和事件的事件。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
unmonitorEvents(object[, events])
```

### <a name="example"></a>示例

以下代码停止对象上的所有事件 `window` 监视：

```javascript
unmonitorEvents(window);
```

还可以有选择地停止监视对象上的特定事件。  例如，`mouse``mousemove`以下代码开始监视当前选定元素上的所有事件，然后停止监视事件 (以减小控制台输出元素中的) ：

```javascript
monitorEvents($0, "mouse");
unmonitorEvents($0, "mousemove");
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="values"></a>values
<!-- ## values(object) -->

<!-- summary to bubble up: -->
返回一个数组，其中包含属于指定对象的所有属性的值。

<!-- add'l info: n/a -->

### <a name="syntax"></a>语法

```javascript
values(object)
```

### <a name="example"></a>示例

```javascript
values(object);
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

<!-- if an article's title is adequately descriptive, and the article is in the same TOC bucket as the present article, don't much need a link here: -->
* [控制台功能参考](reference.md)
* [控制台对象 API 参考](api.md) - `console.*` 函数，如 `console.log()` 和 `console.error()`。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/console/utilities)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
