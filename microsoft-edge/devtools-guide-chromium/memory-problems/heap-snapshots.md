---
title: 使用内存工具记录堆快照
description: 如何使用 DevTools 堆Microsoft Edge分析器记录堆快照，以及使用内存工具查找内存泄漏。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/24/2022
ms.openlocfilehash: fdaa416ab28f291e7b851344778c3f1b75736e3c
ms.sourcegitcommit: 7264a26c08b6b60d29b8bd3b105820a849030506
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2022
ms.locfileid: "12467697"
---
<!-- Copyright Meggin Kearney

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="record-heap-snapshots-using-the-memory-tool"></a>使用内存工具记录堆快照

使用内存 **工具中的堆** 探查器执行以下操作：
*  记录 JS (JavaScript 堆) 快照。
*  分析内存图。
*  比较快照。
*  查找内存泄漏。

DevTools 堆探查器显示页面的 JavaScript 对象和相关 DOM 节点使用的内存分布。  另请参阅[内存术语中的](memory-101.md#objects-retaining-tree)) _保留树的对象。_

<!-- You can view the source files for the Heap Snapshots demo pages at the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->
<!-- 21 hits on "devtools-memory-heap-snapshot" in this article -->


<!-- ====================================================================== -->
## <a name="take-a-snapshot"></a>拍摄快照

<!--
1. Open the __ demo page in a new tab or window.
-->

1. 在 DevTools 中，打开 **内存** 工具。

1. 在" **选择分析类型"部分** ，选择 **"堆快照"** 选项按钮。

1. 单击" **拍摄快照"** 按钮，然后单击"开始 **"**。  或者，按 `Ctrl`+`E` (Windows、Linux) 或 (`Cmd`+`E` macOS) 。

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots.msft.png" alt-text="在内存工具中选择&quot;堆快照&quot;分析类型。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots.msft.png":::

**快照** 最初存储在呈现器进程内存中。  单击快照图标进行查看时，快照会按需传输到 DevTools。

将快照加载到 DevTools 并进行分析后，将显示快照标题下方的数字，并显示可到达 [的 JavaScript 对象的总大小](memory-101.md#object-sizes)。

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-all.msft.png" alt-text="可到达对象的总大小。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-all.msft.png":::

> [!NOTE]
> 快照中仅包含可到达的对象。  此外，拍摄快照始终从垃圾回收开始。


<!-- ====================================================================== -->
## <a name="clear-snapshots"></a>清除快照

单击 **"清除所有配置文件** "图标，从 DevTools (与呈现器进程关联的任何内存中删除快照) 。

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-all-hover-clear-all-profiles.msft.png" alt-text="删除快照。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-all-hover-clear-all-profiles.msft.png":::

关闭 DevTools 窗口不会从与呈现器进程关联的内存中删除配置文件。  重新打开 DevTools 时，以前获取的所有快照将重新出现于快照列表中。

> [!NOTE]
> 试用此散 [点对象示例，](https://microsoftedge.github.io/Demos/devtools-memory-heap-snapshot/example-03.html) 然后使用堆探查器进行配置文件。  将显示 (分配) 对象。

<!-- You can view the source files for the Heap Snapshots demo pages at the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->


<!-- ====================================================================== -->
## <a name="view-snapshots"></a>查看快照

从不同的角度查看不同任务的快照。

**摘要视图** 显示按构造函数名称分组的对象。  使用它来搜寻对象 (和内存使用) 按构造函数名称分组的类型。  **摘要视图** 对于跟踪 **DOM 泄露尤其有用**。

<!--todo: add profile memory problems memory diagnosis (tracking down DOM leaks) section when available  -->

**比较视图**。  显示两个快照之间的差值。  使用它来比较操作 (和) 两个或多个内存快照。  通过检查释放的内存和引用计数中的增量，你可以确认内存泄漏的存在和原因。

**包含视图**。  允许浏览堆内容。  **包含视图** 提供了更好的对象结构视图，帮助分析全局命名空间 (窗口中) 对象，以找出对象周围的内容。  使用它来分析关闭，并深入到较低级别的对象中。

若要在视图之间切换，请使用视图顶部的选择器。

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-view-dropdown.msft.png" alt-text="切换视图选择器。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-view-dropdown.msft.png":::

> [!NOTE]
> 并非所有属性都存储在 JavaScript 堆上。  不会捕获使用运行本机代码的 getter 实现的属性。  此外，不会捕获数字等非字符串值。

### <a name="summary-view"></a>摘要视图

最初，快照在摘要视图中打开，并显示对象总数，可以展开它以显示实例：

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-constructor-retainers.msft.png" alt-text="摘要视图。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-constructor-retainers.msft.png":::

顶级条目是"total"行。

| 顶级条目 | 说明 |
|:--- |:--- |
| **构造函数** | 表示使用此构造函数创建的所有对象。  |
| **距离** | 使用节点的最短简单路径显示到根之间的距离。  |
| **浅表大小** | 显示由特定构造函数函数创建的所有对象的浅表大小的总和。  浅表大小是由对象存储的内存大小 (，数组和字符串具有较大的浅表) 。  请参阅 [对象大小](memory-101.md#object-sizes)。  |
| **保留大小** | 显示同一组对象中保留的最大大小。  在删除对象后可以释放的内存大小 (使从属对象不再可用) 称为保留大小。  请参阅 [对象大小](memory-101.md#object-sizes)。  |

<!--| **Number of object instances** | Displayed in the # column.  |  -->

展开上视图中的总行后，将显示所有实例。  对于每个实例，浅表和保留的大小显示在相应的列中。  字符后的编号 `@` 是对象的唯一 ID，使你可以基于每个对象比较堆快照。

* 黄色对象具有 JavaScript 引用。
* 红色对象是分离的节点。  从具有黄色背景的节点引用分离的节点。

**堆探查器中的 (器) 条目对应的不同构造函数是什么？**

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-constructor-highlight.msft.png" alt-text="构造函数组。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-constructor-highlight.msft.png":::

| 构造函数 (组) 条目 | 说明 |
|:--- |:--- |
| ** (全局属性) ** | 全局对象之间的中间对象 (， `window`) 对象和它引用的对象。  如果对象是使用构造函数创建的 `Person` ，并且由全局对象保留，则保留路径将表示为 `[global] > (global property) > Person`。  这与标准相反，其中对象直接相互引用。  存在中间对象以提高性能。  会定期修改全局设置，并且属性访问优化对非全局对象很适用，而不适用于全局对象。  |
| ** (根) ** | 保留树视图中的根条目是引用所选对象的实体。  这些引用还可以是引擎出于自身目的创建的引用。  引擎具有缓存哪些引用对象，但所有此类引用都是弱引用，并且不会阻止收集对象，因为不存在真正的强引用。  |
| ** (关闭) ** | 通过函数关闭对一组对象的引用计数。 |
| ** (数组、字符串、数字、regexp) ** | 具有引用 Array、String、Number 或正则表达式的属性的对象类型列表。 |
| ** (编译的代码) ** | 与已编译代码相关的所有内容。  脚本类似于函数，但对应于正文 `<script>` 。  SharedFunctionInfos (SFI) 是位于函数和已编译代码之间的对象。  函数通常具有上下文，而 SFIs 没有上下文。 |
| **HTMLDivElement**、 **HTMLAnchorElement**、 **DocumentFragment** 等。  | 对代码引用的特定类型元素或文档对象的引用。 |

<!--todo: add heap profiling summary section when available -->

### <a name="comparison-view"></a>比较视图

通过将多个快照相互比较来查找泄露的对象。  通常，一对直接和反向操作（如打开文档然后关闭文档）不应留下任何垃圾。

若要验证特定应用程序操作是否未创建泄漏，请执行：

1. 在操作之前拍摄堆快照。

1. 执行一个操作。  也就是说，以可能导致泄露的方式与页面交互。

1. 执行反向操作。  也就是说，执行相反的交互并重复几次。

1. 拍摄第二个堆快照，将此快照的视图更改为 **Comparison**，比较快照 **1**。

在 **"比较** "视图中，将显示两个快照之间的差值。  展开总条目时，将显示添加和删除的对象实例。

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-comparison-dropdown.msft.png" alt-text="比较视图。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-comparison-dropdown.msft.png":::

<!--todo: add HeapProfilingComparison section when available  -->

### <a name="containment-view"></a>包含视图

" **包含** "视图实质上是应用程序的对象结构的"鸟眼视图"。  它使你可以速览函数关闭，观察虚拟机 (VM) 内部对象，这些内部对象共同组合 JavaScript 对象，并了解应用程序在非常低的级别使用的内存量。

| 包含视图入口点 | 说明 |
|:--- |:--- |
| **DOMWindow 对象** | JavaScript 代码的全局对象。  |
| **GC 根** | VM 的垃圾回收使用的实际 GC 根。  GC 根由内置对象映射、符号表、VM 线程堆栈、编译缓存、处理范围和全局句柄组成。  |
| **本机对象** | JavaScript VM (JavaScript 虚拟机中的浏览器) 推送"，以允许自动化，例如 DOM 节点、CSS 规则。  |

:::image type="content" source="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-containment-dropdown.msft.png" alt-text="包含视图。" lightbox="../media/memory-problems-gh-nodejs-benchmarks-run-memory-heap-snapshots-containment-dropdown.msft.png":::

<!--todo: add heap profiling containment section when available  -->

### <a name="naming-functions-to-differentiate-between-closures-in-the-snapshot"></a>用于区分快照中关闭的命名函数

命名函数，以便可以轻松地区分快照中的关闭。  例如，此示例不使用命名函数：

```javascript
function createLargeClosure() {
    var largeStr = new Array(1000000).join('x');
    var lC = function() { // this is NOT a named function
        return largeStr;
    };
    return lC;
}
```

以下代码使用命名函数轻松区分快照中的关闭：

```javascript
function createLargeClosure() {
    var largeStr = new Array(1000000).join('x');
    var lC = function lC() { // this IS a named function
        return largeStr;
    };
    return lC;
}
```

#### <a name="demo-impact-of-closures-on-memory"></a>演示：关闭对内存的影响

若要分析关闭对[`eval`](https://microsoftedge.github.io/Demos/devtools-memory-heap-snapshot/example-07.html)内存的影响，请试用此示例：打开演示网页为什么正在新窗口或选项卡中打开。

<!-- You can view the source files for the Heap Snapshots demo pages in the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->

#### <a name="demo-recording-heap-allocations"></a>演示：记录堆分配

你可能还有兴趣使用本示例跟踪上面的演示，该示例将你了解记录堆分配：在一个新窗口或选项卡中打开演示网页 [堆](https://microsoftedge.github.io/Demos/devtools-memory-heap-snapshot/example-08.html) 分配。

<!-- You can view the source files for the Heap Snapshots demo pages in the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->

<!--
:::image type="content" source="../media/memory-problems-domleaks.msft.png" alt-text="Name functions to distinguish between closures." lightbox="../media/memory-problems-domleaks.msft.png":::
-->


<!-- ====================================================================== -->
## <a name="filter-a-heap-snapshot-by-node-type"></a>按节点类型筛选堆快照

使用筛选器专注于堆快照的特定部分。  例如，如果你只对堆栈中的字符串或数组感兴趣，你可以按节点类型进行筛选。

在内存工具中查看堆快照中所有对象时，**** 可能很难专注于特定对象或保留路径。  查看 **堆** 快照时，请使用节点类型筛选器，只关注特定类型的节点。  例如，若要仅查看堆中的数组和字符串对象，请选择"节点类型"筛选器中的 **"数组**"**** 和"字符串 **"** 条目。

![内存工具中堆快照中的节点类型。](heap-snapshots-images/node-types-heap-snapshot.png)


<!-- ====================================================================== -->
## <a name="look-up-color-coding"></a>查找颜色编码

对象的属性和属性值具有不同的类型，并相应地进行着色。  每个属性有四种类型之一：

| 属性类型 | 说明 |
|:--- |:--- |
| **a： property** | 具有名称的 `.` 常规属性，可通过 (点) `[` `]` 运算符访问，或通过 (方括号) 表示法访问，例如 `["foo bar"]`。  |
| **0：元素** | 具有数值索引的常规属性， `[` `]` 可通过 (括号) 表示法。  |
| **a： context var** |  函数上下文中的变量，可通过函数关闭内部的变量名称访问。  |
| **a： system prop** | JavaScript VM 添加的属性，无法通过 JavaScript 代码访问。  |

指定为 的对象 `System` 没有相应的 JavaScript 类型。  每个虚拟机都是 Javascript VM 的对象系统实现一部分。  V8 在用户 JS 对象相同的堆中分配大部分内部对象。  因此，这些只是 V8 内部。


<!-- ====================================================================== -->
## <a name="find-a-specific-object"></a>查找特定对象

若要在收集的堆中查找对象，可以使用 搜索并 `Ctrl`+`F` 给出对象 ID。


<!-- ====================================================================== -->
## <a name="uncover-dom-leaks"></a>发现 DOM 泄漏

堆探查器能够反映浏览器本机对象与 DOM 节点、CSS 规则 (JavaScript) 之间的双向依赖关系。  这有助于发现因忘记分离的 DOM 子树四处浮动而发生的不可见泄露。

DOM 泄露可能大于您想象中。  请考虑以下示例。  何时进行 `#tree` 垃圾回收？

```javascript
var select = document.querySelector;
var treeRef = select("#tree");
var leafRef = select("#leaf");
var body = select("body");

body.removeChild(treeRef);

//#tree in not GC yet due to treeRef
treeRef = null;

//#tree is not GC yet due to indirect reference from leafRef

leafRef = null;
//#NOW can be #tree GC
```

`#leaf`保留对相关的父 (parentNode) `#tree`并递归到 的引用`leafRef`，因此只有当为 nullified `#tree` 时，作为垃圾回收 (GC) 的候选项下的整个树。

:::image type="content" source="../media/memory-problems-tree-gc.msft.png" alt-text="DOM 子树。" lightbox="../media/memory-problems-tree-gc.msft.png":::


### <a name="example-leaking-dom-nodes"></a>示例：泄露 DOM 节点

尝试此泄露 [DOM](https://microsoftedge.github.io/Demos/devtools-memory-heap-snapshot/example-06.html) 节点示例，了解 DOM 节点可能泄露在哪里以及如何检测此类泄露。

<!-- You can view the source files for the Heap Snapshots demo pages at the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->


### <a name="example-dom-leaks-being-bigger-than-expected"></a>示例：DOM 泄漏大于预期

此外，尝试 [此 DOM 泄漏示例大于预期](https://microsoftedge.github.io/Demos/devtools-memory-heap-snapshot/example-09.html)。

<!-- You can view the source files for the Heap Snapshots demo pages at the [MicrosoftEdge/Demos > devtools-memory-heap-snapshot](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-memory-heap-snapshot) repo folder. -->


若要了解有关 DOM 泄漏和内存分析基础的更多信息，请参阅通过 Gonzalo Ruiz de 则使用 [Microsoft Edge DevTools 查找和](https://slid.es/gruizdevilla/memory)调试内存泄漏。

<!-- Example: Try this **demo** to play with detached DOM trees. -->

<!-- todo: add heap profiling dom leaks section when available -->


<!-- ====================================================================== -->
<!--[heap profiling comparison](https://developer.alphabet.com/devtools/docs/heap-profiling-comparison) -->
<!--[heap profiling containment](https://developer.alphabet.com/devtools/docs/heap-profiling-containment) -->
<!--[heap profiling DOM leaks](https://developer.alphabet.com/devtools/docs/heap-profiling-dom-leaks) -->
<!--[heap profiling summary](https://developer.alphabet.com/devtools/docs/heap-profiling-summary) -->
<!--[narrow down causes of memory leaks](../profile/memory-problems/memory-diagnosis#narrow-down-causes-of-memory-leaks) -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots) 由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
