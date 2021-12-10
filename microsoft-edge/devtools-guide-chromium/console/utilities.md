---
title: 控制台实用工具 API 参考
description: 开发人员工具控制台中提供的便利Microsoft Edge引用。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: 5f8ba983da512131899d47d762ecf17929a644cb
ms.sourcegitcommit: fd3b79a0570cfefc2a40107b223569210cb2c2d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2021
ms.locfileid: "12269415"
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
# <a name="console-utilities-api-reference"></a>控制台实用工具 API 参考

控制台实用程序 API 包含一组用于执行常见任务的便利函数，例如：
*   选择并检查 DOM 元素。
*   以可读格式显示数据。
*   停止并启动探查器。
*   监视 DOM 事件。

> [!WARNING]
> 以下命令仅适用于开发人员Microsoft Edge**控制台**。  如果从脚本运行，则命令不起作用。

有关 和 方法以及方法其余部分的信息， `console.log()` `console.error()` `console.*` 请导航到"控制台 API[参考"。](api.md)


<!-- ====================================================================== -->
## <a name="recently-evaluated-expression"></a>最近计算表达式

`$_` 返回最近计算表达式的值。

### <a name="syntax"></a>语法

```console
$_
```

### <a name="example"></a>示例

在下图中，将计算 () `2 + 2` 表达式。  然后 `$_` 计算属性，其中包含相同的值。

:::image type="content" source="../media/console-arithmatic.msft.png" alt-text="$_ 是最近评估的表达式。" lightbox="../media/console-arithmatic.msft.png":::
   `$_` 是最近计算表达式
:::image-end:::

在下图中，计算表达式最初包含一个名称数组。  计算 以查找数组的长度，存储在 中的值 `$_.length` `$_` 将成为最新的计算表达式 `4` 。

`$_` 在计算新命令时更改：

:::image type="content" source="../media/console-array-length.msft.png" alt-text="$_ 在评估新命令时发生更改。" lightbox="../media/console-array-length.msft.png":::

---


<!-- ====================================================================== -->
## <a name="recently-chosen-element-or-javascript-object"></a>最近选择的元素或 JavaScript 对象

`$0` 返回最近选择的元素或 JavaScript 对象。  `$1` 返回第二个最近选择一个，等等。  、 、 和 命令用作对在元素工具中检查的最后五个 DOM 元素或内存工具中选定的最后五个 JavaScript 堆对象 `$0` `$1` `$2` `$3` `$4` **的历史**引用。 ****

### <a name="syntax"></a>语法

```console
$0
```

### <a name="example"></a>示例

在下图中， `img` 在"元素"工具中选择了 **一个元素** 。  在 **控制台** 箱中 `$0` ，已进行评估并显示相同的元素：

:::image type="content" source="../media/console-image-highlighted-$0.msft.png" alt-text="$0 命令。" lightbox="../media/console-image-highlighted-$0.msft.png":::

在下图中，图像显示在同一网页中选择的不同元素。  `$0`现在引用新选择的元素，而 `$1` 返回之前选择的元素。

:::image type="content" source="../media/console-image-highlighted-$1.msft.png" alt-text="$1 命令。" lightbox="../media/console-image-highlighted-$1.msft.png":::

---


<!-- ====================================================================== -->
## <a name="query-selector"></a>查询选择器

`$(selector)` 返回对具有指定 CSS 选择器的第一个 DOM 元素的引用。  此方法是 [document.querySelector () 方法的别名 ](https://developer.mozilla.org/docs/Web/API/Document/querySelector) 。

### <a name="syntax"></a>语法

```console
$(selector, [startNode])
```

### <a name="example"></a>示例

在下图中， `$('img')` 返回对网页 `<img>` 中第一个元素的引用：

:::image type="content" source="../media/console-element-selector-image.msft.png" alt-text="$ ( img') 返回对网页中第一<img> 元素的引用。" lightbox="../media/console-element-selector-image.msft.png":::

若要查找 DOM 中的第一个元素，或查找并显示在网页上：

1.  右键单击返回的结果。
1.  单击 **"元素面板"中的"展示"。**

在下图中，将返回对当前选择的元素的引用， `src` 并显示 属性：

结果 `$('img').src` 为：

:::image type="content" source="../media/console-element-selector-image-source.msft.png" alt-text="$ ( img') .src 的结果。" lightbox="../media/console-element-selector-image-source.msft.png":::

此方法还支持第二个参数 ，用于指定要搜索的元素或 `startNode` 节点。  参数的默认值为 `document` 。

在下图中，找到 `img` 元素后的第一个元素 `title--image` ，并返回 `src` `img` 元素的 属性。

结果 `$('img', document.querySelector('title--image')).src` 为：

:::image type="content" source="../media/console-element-selector-image-filter-source.msft.png" alt-text="$ ('img'， document.querySelector ('title--image') ) .src 的结果。" lightbox="../media/console-element-selector-image-filter-source.msft.png":::

> [!NOTE]
> 如果使用的库（如 jQuery）使用 ，则功能将被覆盖，并且对应于该库中 `$` `$` 的实现。

---


<!-- ====================================================================== -->
## <a name="query-selector-all"></a>查询选择器全部

`$$(selector)` 返回一个匹配指定 CSS 选择器的元素数组。  此方法等效于运行 [document.querySelectorAll () ](https://developer.mozilla.org/docs/Web/API/Document/querySelectorAll) 方法。

### <a name="syntax"></a>语法

```console
$$(selector, [startNode])
```

### <a name="example"></a>示例

在下面的代码和图中，使用 创建当前网页中所有元素的数组 `$$()` `<img>` 并显示每个 `src` 元素的 属性值。

```console
var images = $$('img');
for (each in images) {
    console.log(images[each].src);
}
```

Using `$$()` to choose all images in the webpage and display the sources：

:::image type="content" source="../media/console-element-selector-image-all.msft.png" alt-text="使用 $$ () 选择网页中的所有图像并显示源。" lightbox="../media/console-element-selector-image-all.msft.png":::

此方法还支持第二个参数 ，用于指定要搜索的元素或 `startNode` 节点。  参数的默认值为 `document` 。

在下面的代码示例和图中，上一个代码示例和图的修改版本用于创建一个数组，该数组包含在当前网页中所选节点之后 `$$()` `<img>` 显示的所有元素。

```console
var images = $$('img', document.querySelector(`title--image`));
for (each in images) {
   console.log(images[each].src);
}
```

用于 `$$()` 选择网页中指定元素之后显示的所有图像 `<div>` 并显示源：

:::image type="content" source="../media/console-element-selector-image-filter-all.msft.png" alt-text="使用 $$ () 选择显示在网页中的 <div> 元素后显示的所有图像，并显示源。" lightbox="../media/console-element-selector-image-filter-all.msft.png":::

> [!NOTE]
> 在 `Shift` + `Enter` 控制台**中选择，** 在不运行脚本的情况下启动新行。

---


<!-- ====================================================================== -->
## <a name="xpath"></a>XPath

`$x(path)` 返回一个匹配指定 XPath 表达式的 DOM 元素数组。

### <a name="syntax"></a>语法

```console
$x(path, [startNode])
```

### <a name="example"></a>示例

在下面的代码示例和图中，将返回 `<p>` 网页上的所有元素。

```console
$x("//p")
```

使用 XPath 选择器：

:::image type="content" source="../media/console-array-xpath.msft.png" alt-text="使用 XPath 选择器。" lightbox="../media/console-array-xpath.msft.png":::

在下面的代码示例和图中，将返回 `<p>` 包含元素 `<a>` 的所有元素。

```console
$x("//p[a]")
```

使用更复杂的 XPath 选择器：

:::image type="content" source="../media/console-array-xpath-sub-element.msft.png" alt-text="使用更复杂的 XPath 选择器。" lightbox="../media/console-array-xpath-sub-element.msft.png":::

与其他选择器命令类似，具有可选的第二个参数 ，用于指定要搜索的元素或 `$x(path)` `startNode` 节点。

将 XPath 选择器与 `startNode` 一同使用：

:::image type="content" source="../media/console-array-xpath-startnode.msft.png" alt-text="将 XPath 选择器与 startNode 一同使用。" lightbox="../media/console-array-xpath-startnode.msft.png":::

---


<!-- ====================================================================== -->
## <a name="clear"></a>clear

`clear()` 清除其历史记录的控制台。

### <a name="syntax"></a>语法

```console
clear()
```

### <a name="example"></a>示例

```console
clear()
```


<!-- ====================================================================== -->
## <a name="copy"></a>copy

`copy(object)` 将指定对象的字符串表示形式复制到剪贴板。

### <a name="syntax"></a>语法

```console
copy(object)
```

### <a name="example"></a>示例

```console
copy($0)
```

---


<!-- ====================================================================== -->
## <a name="debug"></a>调试

调用指定的函数时，将调用调试程序，并中断"源"面板上的函数。  然后，你可以逐步执行代码并调试它。

### <a name="syntax"></a>语法

```console
debug(method)
```

>[!NOTE]
> 问题[Chromium #1050237](https://crbug.com/1050237)跟踪函数的 `debug()` Bug。  如果遇到问题，请尝试改为 [使用断](../javascript/breakpoints.md) 点。

### <a name="example"></a>示例

```console
debug("debug");
```

:::image type="content" source="../media/console-debug-text.msft.png" alt-text="使用 debug () 在方法内中断。" lightbox="../media/console-debug-text.msft.png":::
   在方法内使用 `debug()`
:::image-end:::

用于 `undebug(method)` 停止方法上的中断，或使用 UI 关闭所有断点。

有关断点的信息，请导航到"[使用断点暂停代码"。](../javascript/breakpoints.md)

---


<!-- ====================================================================== -->
## <a name="dir"></a>dir

`dir(object)` 显示指定对象的所有属性的对象样式列表。  此方法是 [console.dir () 方法的别名 ](https://developer.mozilla.org/docs/Web/API/Console/dir) 。

### <a name="syntax"></a>语法

```console
dir(object)
```

在 `document.head` 控制台 **中进行评估** ，以显示 和 标记 `<head>` 之间的 `</head>` HTML。

### <a name="example"></a>示例

在下面的代码示例和图中，在控制台 中使用 后将显示对象 `console.dir()` 样式 **列表**。

```console
document.head;
dir(document.head);
```

:::image type="content" source="../media/console-dir-document-head-expanded.msft.png" alt-text="使用 dir () 方法记录 document.head。" lightbox="../media/console-dir-document-head-expanded.msft.png":::
   使用 `document.head` 方法 `dir()` 日志记录
:::image-end:::

有关详细信息，请导航到控制台 API 中的 [console.dir () ](api.md#dir) 。

---


<!-- ====================================================================== -->
## <a name="dirxml"></a>dirxml

`dirxml(object)` 打印指定对象的 XML 表示形式，如 **元素** 工具中显示。  此方法等效于 [console.dirxml () ](https://developer.mozilla.org/docs/Web/API/Console/dirxml) 方法。

### <a name="syntax"></a>语法

```console
dirxml(object)
```

---


<!-- ====================================================================== -->
## <a name="inspect"></a>inspect

`inspect(object/method)` 在相应的面板中打开并选择指定的元素或对象：DOM 元素的 **Elements** 工具或 JavaScript 堆对象的 **Memory** 工具。

### <a name="syntax"></a>语法

```console
inspect(object/method)
```

### <a name="example"></a>示例

在下面的代码示例和图中，将在 `document.body` "元素"工具 **中** 打开 。

### <a name="example"></a>示例

```console
inspect(document.body);
```

使用 检查元素 `inspect()` ：

:::image type="content" source="../media/console-inspect-document-body.msft.png" alt-text="使用 inspect () 检查元素。" lightbox="../media/console-inspect-document-body.msft.png":::

传递要检查的方法时，该方法将在 **"** 源"工具中打开网页供你检查。

---


<!-- ====================================================================== -->
## <a name="geteventlisteners"></a>getEventListeners

`getEventListeners(object)` 返回在指定对象上注册的事件侦听器。  返回值是包含每个已注册事件类型（如 或) ） (`click` 数组 `keydown` 的对象。  每个数组的成员是描述为每种类型注册的侦听器的对象。

### <a name="syntax"></a>语法

```console
getEventListeners(object)
```

### <a name="example"></a>示例

下面的代码和图列出了在 对象上注册的所有事件 `document` 侦听器。

```console
getEventListeners(document);
```

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document.msft.png" alt-text="使用 getEventListeners 文档库 (输出) 。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document.msft.png":::
   使用 的结果 `getEventListeners(document)`
:::image-end:::

如果指定对象上注册了多个侦听器，则数组将包含每个侦听器的成员。  在下图中，在 事件的 元素上注册了两 `document` 个 `click` 事件侦听器：

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document-expanded-1.msft.png" alt-text="在&quot;document&quot;元素上为&quot;click&quot;事件注册多个事件侦听器。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document-expanded-1.msft.png":::

可以进一步展开以下每个对象来浏览其属性。  下面是侦听器对象的扩展视图：

:::image type="content" source="../media/console-elements-event-listeners-console-get-event-listeners-document-2.msft.png" alt-text="侦听器对象的扩展视图。" lightbox="../media/console-elements-event-listeners-console-get-event-listeners-document-2.msft.png":::

---


<!-- ====================================================================== -->
## <a name="keys"></a>键

`keys(object)` 返回一个数组，其中包含属于指定对象的属性的名称。  若要获取相同属性的关联值，请使用 `values()` 。

### <a name="syntax"></a>语法

```console
keys(object)
```

### <a name="example"></a>示例

例如，假设应用程序定义了以下对象。

```console
var player1 = {"name": "Ted", "level": 42}
```

在下面的代码示例和图中，为了简单起见， (在键入和在控制台中) 在全局命名空间中 `player1` `keys(player1)` `values(player1)` 定义结果。

```console
keys(player1)

values(player1)
```

和 `keys()` `values()` 命令：

:::image type="content" source="../media/console-keys-values.msft.png" alt-text="键 () 和值 () 命令。" lightbox="../media/console-keys-values.msft.png":::

---


<!-- ====================================================================== -->
## <a name="monitor"></a>监视器

`monitor(method)` 将一条消息记录到控制台，指示方法名称以及作为请求的一部分传递给方法的参数。

### <a name="syntax"></a>语法

```console
monitor(method)
```

### <a name="example"></a>示例

```console
function sum(x, y) {
    return x + y;
}
monitor(sum);
```

`monitor()`方法：

:::image type="content" source="../media/console-function-monitor-sum.msft.png" alt-text="monitor () 方法。" lightbox="../media/console-function-monitor-sum.msft.png":::

若要结束监视，请使用 `unmonitor(method)` 。

---


<!-- ====================================================================== -->
## <a name="monitorevents"></a>monitorEvents

当指定对象上发生指定事件之一时，该事件对象将记录到控制台。  可以指定要监视的单个事件、事件数组或映射到预定义的事件集合中的一个泛型事件类型。

### <a name="syntax"></a>语法

```console
monitorEvents(object[, events])
```

### <a name="example"></a>示例

下面监视 window 对象上的所有调整大小事件。

```console
monitorEvents(window, "resize");
```

监视窗口调整大小事件：

:::image type="content" source="../media/console-monitor-events-resize-window.msft.png" alt-text="监视窗口调整大小事件。" lightbox="../media/console-monitor-events-resize-window.msft.png":::

以下代码定义一个数组，用于监视窗口对象上的 和 `resize` `scroll` 事件。

```console
monitorEvents(window, ["resize", "scroll"]);
```

还可以指定一种可用的事件类型，即映射到预定义的事件集的字符串。  下表显示可用的事件类型和关联的事件映射。

| 事件类型 | 相应的映射事件 |
|:--- |:--- |
| `mouse` | "click"、"dblclick"、"mousedown"、"mousemove"、"mouseout"、"mouseover"、"mouseup"、"mousewheel" |
| `key` | "keydown"、"keypress"、"keyup"、"textInput" |
| `touch` | "touchcancel"、"touchend"、"touchmove"、"touchstart" |
| `control` | "blur"、"change"、"focus"、"reset"、"resize"、"scroll"、"select"、"submit"、"zoom" |

In the following code， the `key` event type corresponding to `key` events on an input text field are currently chosen in the **Elements** tool.

```console
monitorEvents($0, "key");
```

下图显示了在文本字段中键入字符后的示例输出。  监视关键事件：

:::image type="content" source="../media/console-monitor-events-type-t-y.msft.png" alt-text="监视关键事件。" lightbox="../media/console-monitor-events-type-t-y.msft.png":::

---


<!-- ====================================================================== -->
## <a name="profile"></a>profile

`profile()` 使用可选名称启动 JavaScript CPU 分析会话。  [profileEnd () ](#profileend)方法完成配置文件，在"内存"工具**中显示**结果。  <!--Navigate to [Speed Up JavaScript Runtime](../rendering-tools/js-runtime.md).  -->

### <a name="syntax"></a>语法

```console
profile([name])
```

### <a name="example"></a>示例

1.  运行 `profile()` 方法以开始分析。

    ```console
    profile("My profile")
    ```

1.  运行 [profileEnd () ](#profileend) 方法停止分析和在内存工具 **中显示** 结果。

配置文件也可以嵌套。  在下面的代码和图中，无论顺序如何，结果都是相同的。

```console
profile('A');
profile('B');
profileEnd('A');
profileEnd('B');
```

> [!NOTE]
> 多个 CPU 配置文件可以同时运行，并且不需要按照创建顺序关闭每个配置文件。

---


<!-- ====================================================================== -->
## <a name="profileend"></a>profileEnd

`profileEnd()` 完成 JavaScript CPU 分析会话，并显示内存 **工具中** 的结果。  必须运行 [配置文件 () ](#profile) 方法。  <!--Navigate to [Speed Up JavaScript Runtime](../rendering-tools/js-runtime.md).  -->

### <a name="syntax"></a>语法

```console
profileEnd([name])
```

### <a name="example"></a>示例

1.  运行 [profile () ](#profile) 方法以开始分析。
1.  运行 `profileEnd()` 方法以停止分析，在内存工具中 **显示** 结果。

    ```console
    profileEnd("My profile")
    ```

配置文件也可以嵌套。  在下面的代码中，无论顺序如何，结果都是相同的。

```console
profile('A');
profile('B');
profileEnd('A');
profileEnd('B');
```

结果在内存工具中显示为堆 **快照，包含** 分组的配置文件：

:::image type="content" source="../media/console-memory-multiple-cpu-profiles.msft.png" alt-text="分组配置文件。" lightbox="../media/console-memory-multiple-cpu-profiles.msft.png":::

> [!NOTE]
> 多个 CPU 配置文件可以同时运行，并且不需要按照创建顺序关闭每个配置文件。

---


<!-- ====================================================================== -->
## <a name="queryobjects"></a>queryObjects

`queryObjects(Constructor)` 返回使用指定构造函数创建的对象数组。  的范围 `queryObjects()` 是控制台 中当前选择的运行时 **上下文**。

### <a name="syntax"></a>语法

```console
queryObjects(Constructor)
```

### <a name="example"></a>示例

* `queryObjects(promise)` 返回 的所有实例 `Promise` 。

* `queryObjects(HTMLElement)` 返回所有 HTML 元素。

*  `queryObjects(functionName)` 返回使用 实例化的所有对象 `new functionName()` 。

---


<!-- ====================================================================== -->
## <a name="table"></a>table

`table(data[, columns])` 使用带可选列标题的数据对象记录表格式的对象数据。

### <a name="syntax"></a>语法

```console
table(data[, columns])
```

### <a name="example"></a>示例

以下代码使用控制台中的表显示名称列表：

```console
var names = {
    0:  {
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

方法 `table()` 的结果：

:::image type="content" source="../media/console-table-display.msft.png" alt-text="table () 方法的结果。" lightbox="../media/console-table-display.msft.png":::

---


<!-- ====================================================================== -->
## <a name="undebug"></a>undebug

`undebug(method)` 停止对指定方法的调试。 因此，当请求该方法时，将不再调用调试器。

### <a name="syntax"></a>语法

```console
undebug(method)
```

### <a name="example"></a>示例

```console
undebug(getData);
```

---


<!-- ====================================================================== -->
## <a name="unmonitor"></a>unmonitor

`unmonitor(method)` 停止对指定方法的监视。  此方法与监视器 [ () ](#monitor) 方法一同使用。

### <a name="syntax"></a>语法

```console
unmonitor(method)
```

### <a name="example"></a>示例

```console
unmonitor(getData);
```

---


<!-- ====================================================================== -->
## <a name="unmonitorevents"></a>unmonitorEvents

`unmonitorEvents(object[, events])` 停止指定对象和事件的监视事件。

### <a name="syntax"></a>语法

```console
unmonitorEvents(object[, events])
```

### <a name="example"></a>示例

以下代码停止对象上的所有事件 `window` 监视：

```console
unmonitorEvents(window);
```

还可以有选择地停止监视对象上的特定事件。  例如，以下代码开始监视当前所选元素上的所有事件，然后停止监视事件 (以减小控制台输出元素中的 `mouse` `mousemove`) 。

```console
monitorEvents($0, "mouse");
unmonitorEvents($0, "mousemove");
```

---


<!-- ====================================================================== -->
## <a name="values"></a>values

`values(object)` 返回一个数组，其中包含属于指定对象的所有属性的值。

### <a name="syntax"></a>语法

```console
values(object)
```

### <a name="example"></a>示例

```console
values(object);
```

---


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/console/utilities)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors#kayce-basques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
