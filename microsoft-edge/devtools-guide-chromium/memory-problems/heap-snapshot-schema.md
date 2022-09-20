---
title: 堆快照文件格式
description: 从内存工具导出时堆快照文件的结构
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 9/16/2022
ms.openlocfilehash: ddd1114c8a5b4c28e1847415ea1913ad273876b1
ms.sourcegitcommit: a955b0025aa97ed6165ebc4201d22bdea8614bb0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2022
ms.locfileid: "12755952"
---
# <a name="the-heap-snapshot-file-format"></a>堆快照文件格式

调查 Web 应用程序中的内存使用情况可能很困难。 使用 DevTools **内存** 工具，可以通过拍摄堆快照来浏览 Web 应用程序在内存中分配的所有对象。 此信息对于性能调查非常有用，因为你可以找出哪些对象占用的内存最多。

但是，有时可能需要关注 **内存** 工具未显示的内存数据的特定部分。 在这种情况下，请使用 DevTools 将整个内存数据集导出为 `.heapsnapshot` JSON 文件。

本文介绍 JSON 文件的 `.heapsnapshot` 结构和内容，以便可以生成自己的可视化效果和分析工具。


<!-- ====================================================================== -->
## <a name="record-a-heap-snapshot"></a>记录堆快照

若要导出 `.heapsnapshot` 文件，首先需要在 **内存** 工具中记录堆快照，如下所示：

1. 在 Microsoft Edge 中，导航到要从中导出数据的网站。

1. 按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 打开 Devtools。

1. 打开 **内存** 工具。

1. 选择 **堆快照** ，然后单击 **“拍摄快照**”。

有关详细信息，请参阅 [使用内存工具的记录堆快照](heap-snapshots.md)。


<!-- ====================================================================== -->
## <a name="export-and-view-a-heapsnapshot-file"></a>导出 `.heapsnapshot` 和查看文件

记录堆快照后，可以导出它。

1. 在 **内存** 工具左侧栏中，单击刚录制的堆快照项旁边的 **“保存** ”。

1. 将文件扩展名更改 `.heapsnapshot` 为 `.json`，以便更轻松地在文本编辑器中打开文件。

1. 在文本编辑器中打开已保存的文件，例如Visual Studio Code。

1. 若要使 JSON 更易于阅读，请在Visual Studio Code中右键单击代码中的任意位置，然后选择 **“格式”文档**。

通常，每次记录和导出堆快照时，生成 `.heapsnapshot` 的文件会有所不同。 堆快照是根据当前在 DevTools 中检查的 Web 应用程序的内容动态生成的。


<!-- ====================================================================== -->
## <a name="overview-of-the-heapsnapshot-file-format"></a>文件格式概述`.heapsnapshot`

Web 应用程序使用的内存由 V8 组织为图形，V8 是 Microsoft Edge 使用的 JavaScript 引擎。 图形是一种数据类型，由图形) 上的 _节点_ (点和 _边缘_ 组成， (点) 之间的链接。

文件中 `.heapsnapshot` 的数据表示高效图形的 Web 应用内存，并使浏览器进程和 DevTools 之间传输数据组更加容易。 该 `.heapsnapshot` 文件包含节点和边缘之间关系的平展表示形式，作为包含数字和字符串数组的 JSON 对象。 该文件具有 `.heapsnapshot` 文件扩展名，并包含 JSON 格式的数据。

数据包含两个主要部分：

* 元数据，其中包含分析表示内存图的数据数组所需的所有信息。
* 数组数据，其中包含重新创建图形所需的实际数据。

#### <a name="updating-this-data-format-documentation"></a>更新此数据格式文档

如下所述，文件的 `.heapsnapshot` 格式可能会随着 V8 和 DevTools 的发展而更改。 如果在文档中发现差异，请在 [MicrosoftDocs/edge-developer 存储库](https://github.com/MicrosoftDocs/edge-developer/issues)中提供反馈。


<!-- ====================================================================== -->
## <a name="schema-of-the-heapsnapshot-data"></a>数据的 `.heapsnapshot` 架构

#### <a name="top-level-structure"></a>顶级结构

`.heapsnapshot` JSON 数据包含具有以下属性的根对象：

```json
{
    "snapshot": {},
    "nodes": [],
    "edges": [],
    "trace_function_infos": [],
    "trace_tree": [],
    "samples": [],
    "locations": [],
    "strings": []
}
```

| 属性 | 描述 | 格式 |
| --- | --- | --- |
| `snapshot` | 包含有关内存图数据格式及其大小的所有信息。 | `Object` |
| `nodes` | 重新创建图形节点所需的所有信息。 若要分析此数据，请使用 `snapshot.meta.node_types` 和 `snapshot.meta.node_fields`。 | `Array` |
| `edges` | 重新创建图形边缘所需的所有信息。 若要分析此数据，请使用 `snapshot.meta.edge_types` 和 `snapshot.meta.edge_fields`。 | `Array` |
| `trace_function_infos` | _尚未记录_ | `Array` |
| `trace_tree` | _尚未记录_ | `Array` |
| `samples` | _尚未记录_ | `Array` |
| `locations` | _尚未记录_ | `Array` |
| `strings` | 内存中保存的所有字符串的数组。 这些字符串可以是任何字符串，例如用户定义的字符串或代码。 | `Array` |

#### <a name="snapshot"></a>快照

```json
{
    "snapshot": {     
        "meta": {},
        "node_count": 123,
        "edge_count": 456,
        "trace_function_count": 0
    }
    ...
}
```

| 属性 | 描述 | 格式 |
| --- | --- | --- |
| `meta` | 包含有关内存图数据中包含的每个对象的形状和大小的信息的属性。 | `Object` |
| `node_count` | 内存图中的节点总数。 | `Number` |
| `edge_count` | 内存图中的边缘总数。 | `Number` |
| `trace_function_count` | 内存图中的跟踪函数总数。 | `Number` |

#### <a name="snapshot-metadata"></a>快照元数据

```json
{
    "snapshot": {
        "meta": {
            "node_fields": [],
            "node_types": [],
            "edge_fields": [],
            "edge_types": []
        }
    }
    ...
}
```

| 属性 | 描述 | 格式 |
| --- | --- | --- |
| `node_fields` | 重新创建节点所需的所有属性的列表。 | `Array` |
| `node_types` | 重新创建节点所需的所有属性的类型。 类型数与在 `node_fields`其中定义的属性数相同。 | `Array` |
| `edge_fields` | 重新创建边缘所需的所有属性的列表。 | `Array` |
| `edge_types` | 重新创建边缘所需的所有属性的类型。 类型数与属性数 `edge_fields`相同。 | `Array` |

下面是元数据对象的示例：

```json
{
    "snapshot": {
        "meta": {
            "node_fields": [
                "type",
                "name",
                "id",
                "self_size",
                "edge_count",
                "trace_node_id",
                "detachedness"
            ],
            "node_types": [
                [
                    "hidden",
                    "array",
                    "string",
                    "object",
                    "code",
                    "closure",
                    "regexp",
                    "number",
                    "native",
                    "synthetic",
                    "concatenated string",
                    "sliced string",
                    "symbol",
                    "bigint",
                    "object shape"
                ],
                "string",
                "number",
                "number",
                "number",
                "number",
                "number"
            ],
            "edge_fields": [
                "type",
                "name_or_index",
                "to_node"
            ],
            "edge_types": [
                [
                    "context",
                    "element",
                    "property",
                    "internal",
                    "hidden",
                    "shortcut",
                    "weak"
                ],
                "string_or_number",
                "node"
            ]
        }
    }
}
```

#### <a name="nodes"></a>节点

数 `nodes` 组位于数据的 `.heapsnapshot` 顶层，包含重新创建内存图节点所需的所有信息。

若要分析此数组，需要以下信息：

* `snapshot.node_count`，知道有多少个节点。
* `snapshot.meta.node_fields`，了解每个节点有多少个字段。

数组中的每个节点都由一系列 `snapshot.meta.node_fields.length` 数字表示。 因此，数组`snapshot.node_count`中的`nodes`元素总数乘以 `snapshot.meta.node_fields.length`。

若要重新创建节点，请按大小`snapshot.meta.node_fields.length`组从数`nodes`组中读取数字。

以下代码片段显示 `node_fields` 图形中前两个节点的元数据和数据：

```json
{
    "snapshot": {
        "meta": {
            "node_fields": [
                "type",
                "name",
                "id",
                "self_size",
                "edge_count",
                "trace_node_id",
                "detachedness"
            ]
            ...
        }
        ...
    },
    "nodes": [
        9,1,1,0,10,0,0,
        2,1,79,12,1,0,0,
        ...
    ]
    ...
}
```

| 节点组中的索引 | 名称 | 描述 |
| --- | --- | --- |
| `0` | `type` | 节点的类型。 请参阅下面 [的节点类型](#node-types)。 |
| `1` | `name` | 节点的名称。 这是一个数字，它是顶级 `strings` 数组中的索引。 若要查找实际名称，请使用索引号查找顶级 `strings` 数组中的字符串。 |
| `2` | `id` | 节点的唯一 ID。 |
| `3` | `self_size` | 节点的大小（以字节为单位）。 |
| `4` | `edge_count` | 连接到此节点的边缘数。 |
| `5` | `trace_node_id` | 跟踪节点的 ID <!--todo: more detail --> |
| `6` | `detachedness` | 是否可以从 `window` 全局对象访问此节点。 `0` 表示节点未分离;可以从 `window` 全局对象访问节点。 `1` 表示节点已分离;无法从 `window` 全局对象访问节点。 |

#### <a name="node-types"></a>节点类型

数组中节点的数字组中 `nodes` 的第一个数字与其类型相对应。 此数字是一个索引，可用于查找数组中的 `snapshot.meta.node_types[0]` 类型名称。

| 节点类型 | 描述 |
| --- | --- |
| Hidden | 与用户可控制的 JavaScript 对象不直接对应的 V8 内部元素。 在 DevTools 中，所有这些都显示在类别名称 ** (系统) **下。 即使这些对象是内部对象，它们也可以是保留器路径的重要组成部分。 |
| 对象 | 任何用户定义的对象，例如 `{ x: 2 }` 或 `new Foo(4)`。 上下文以 **系统/上下文**形式显示在 DevTools 中，保留必须在堆上分配的变量，因为它们由嵌套函数使用。 |
| 本地 | Blink 呈现引擎（而不是 V8）分配的对象。 这些大多是 DOM 项，例如 `HTMLDivElement` 或 `CSSStyleRule`。 |
| 串联字符串 | 将两个字符串与 `+` 运算符串联的结果。 V8 不是创建包含两个源字符串中所有数据的副本的新字符串，而是创建一个包含指向两个 `ConsString` 源字符串的指针的对象。 从 JavaScript 的角度来看，它的行为就像任何其他字符串一样，但从内存分析的角度来看，它不同。 |
| 切片字符串 | 子字符串操作的结果，如 using `String.prototype.substr` 或 `String.prototype.substring`. V8 通过创建指向 `SlicedString`原始字符串并指定起始索引和长度的字符串数据来避免复制字符串数据。 从 JavaScript 的角度来看，切片字符串的作用类似于任何其他字符串，但从内存分析的角度来看，它不同。 |
| 阵 列 | 各种内部列表，这些列表显示在 DevTools 中，其类别名称 ** (数组) **。 与“隐藏”一样，此类别将各种内容组合在一起。 此处的许多对象 ** (对象属性命名) ** 或 ** (对象元素) **，指示它们包含 JavaScript 对象的字符串键或数值键属性。 |
| 代码 | 与脚本量和/或函数运行次数成比例增长的内容。 |
| 合成 | 合成节点与内存中实际分配的任何节点不对应。 它们用于区分不同类型的垃圾回收 (GC) 根。 |

#### <a name="edges"></a>边缘

与数 `nodes` 组类似， `edges` 顶级数组包含重新创建内存图边缘所需的所有元素。

也类似于节点，可以通过乘以`snapshot.edge_count``snapshot.meta.edge_fields.length`来计算边缘总数。 边缘也存储为数字序列，需要按大小 `snapshot.meta.edge_fields.length`组循环访问。

但是，若要正确读取数 `edges` 组，首先需要读取数 `nodes` 组，因为每个节点知道它有多少边缘。 

若要重新创建边缘，需要三条信息：

* 边缘类型。
* 边缘名称或索引。
* 边缘连接到的节点。

例如，如果读取数组中`nodes`的第一个节点，并且其`edge_count`属性设置为 4，则数组中的`edges`前四组`snapshot.meta.edge_fields.length`数字对应于此节点的四个边缘。

| 边缘组中的索引 | 名称 | 描述 |
| --- | --- | --- |
| `0` | `type` | 边缘的类型。 请参阅 [Edge 类型](#edge-types) ，了解可能的类型是什么。 |
| `1` | `name_or_index` | 可以是数字或字符串。 如果是数字，则它对应于顶级 `strings` 数组中的索引，可在其中找到边缘的名称。 |
| `2` | `to_node` | 此边缘连接到的 `nodes` 数组中的索引。 |

#### <a name="edge-types"></a>边缘类型

数组中边缘的数字组中 `edges` 的第一个数字与其类型相对应。 此数字是一个索引，可用于查找数组中的 `snapshot.meta.edge_types[0]` 类型名称。

| Edge 类型 | 描述 |
| --- | --- |
| 内置 | 与 JavaScript 可见名称不对应但仍然重要的边缘。 例如，函数实例具有一个“上下文”，表示在定义函数的范围内的变量的状态。 JavaScript 代码无法直接读取函数的“上下文”，但在调查保留程序时需要这些边缘。 |
| 弱 | 弱边缘不会使它们连接到的节点保持活动状态，因此会从“保留器”视图中省略。 垃圾回收 (GC) 可以丢弃任何仅具有弱边缘的对象。 |
| Hidden | 与内部类似，这些边缘没有唯一名称，而是按增量顺序进行编号。 |
| 快捷方式 | 其他一些路径的易于读取的表示形式。 此类型很少使用。 例如，如果使用`Function.prototype.bind`某些绑定参数创建绑定函数，V8 将创建一个`JSBoundFunction``FixedArray`指向内部类型)  (，该函数指向每个绑定参数。 生成快照时，V8 会将绑定函数中的快捷方式边缘直接添加到每个绑定参数，绕过该 `FixedArray`参数。 |
| 元素 | 键为数字的对象属性。 |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* 若要`.heapsnapshot`详细了解文件格式，请参阅生成文件的代码，即[`HeapSnapshotGenerator`类`heap-snapshot-generator.h`](https://chromium.googlesource.com/external/v8/+/master/src/heap-snapshot-generator.h#142)。
