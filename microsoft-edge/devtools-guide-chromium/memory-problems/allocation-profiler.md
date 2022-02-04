---
title: 在时间线上使用分配检测
description: 使用时间线上的分配检测查找未正确进行垃圾回收的对象，并继续保留内存。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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
   limitations under the License. -->
# <a name="use-allocation-instrumentation-on-timeline"></a>在时间线上使用分配检测

<!-- title in other repo:
How to Use the Allocation Profiler Tool -->

在 **内存** 工具中，使用时间线上的 **分配** 检测单选按钮查找未正确进行垃圾回收的对象，并继续保留内存。


<!-- ====================================================================== -->
## <a name="how-allocation-instrumentation-on-timeline-works"></a>时间线上的分配检测的工作原理

**时间线上的分配检测**将堆探查器的详细快照信息与[](heap-snapshots.md)性能工具的增量更新和**跟踪**相结合。  同样，跟踪对象的堆分配涉及启动记录、执行一系列操作以及停止记录进行分析。

<!--todo: add profile memory problems (heap profiler) section when available  -->
<!--todo: add profile evaluate performance (Performance tool) section when available  -->

**时间线上的分配检测** 在整个记录过程中定期获取堆快照 (频率与记录结束时每 50 毫秒) 一次最终快照的频率一样。

:::image type="content" source="../media/memory-problems-memory-allocation-timeline-snapshot-highlighted.msft.png" alt-text="日程表上的分配检测。" lightbox="../media/memory-problems-memory-allocation-timeline-snapshot-highlighted.msft.png":::

> [!NOTE]
> 后的编号 `@` 是对象 ID，在录制会话期间获取的多个快照中保留。  通过永久性对象 ID，可以在堆状态之间进行精确比较。  对象在垃圾回收期间移动，因此显示对象的地址没有任何意义。


<!-- ====================================================================== -->
## <a name="enable-allocation-instrumentation-on-timeline"></a>在时间线上启用分配检测

若要在时间线 **上开始使用 Allocation instrumentation**：

1. [打开 DevTools](../open/index.md)。

1. 打开 **内存** 工具。

1. 选择" **日程表上的分配检测"** 单选按钮。

1. 开始录制。

记录堆分配探查器：

:::image type="content" source="../media/memory-problems-memory-allocation-instrumentation-on-timeline-selected.msft.png" alt-text="记录堆分配探查器。  使用&quot;内存&quot;工具中的&quot;时间线上的分配检测&quot;单选按钮。" lightbox="../media/memory-problems-memory-allocation-instrumentation-on-timeline-selected.msft.png":::


<!-- ====================================================================== -->
## <a name="read-a-heap-allocation-timeline"></a>读取堆分配时间线

堆分配时间线显示对象的创建位置，并标识保留路径。  在下图中，顶部的条形指示何时在堆中发现新对象。

每个栏的高度对应于最近分配的对象的大小，而条形的颜色指示这些对象是否仍位于最终堆快照中。  蓝色条指示仍位于时间线末尾的对象，灰色条指示在时间线期间分配但之后已被垃圾回收的对象。

:::image type="content" source="../media/memory-problems-memory-allocation-timelines-snapshot.msft.png" alt-text="时间线快照上的分配检测。" lightbox="../media/memory-problems-memory-allocation-timelines-snapshot.msft.png":::

<!-- In the following figure, an action was performed 3 times.  The sample program caches five objects, so the last five blue bars are expected.  But the left-most blue bar indicates a potential problem. -->
<!-- todo: redo figure 4 with multiple click actions -->

可以使用上述时间线中的滑块放大该特定快照并查看此时最近分配的对象：

:::image type="content" source="../media/memory-problems-memory-allocation-timeline-snapshot-highlighted-annotated.msft.png" alt-text="放大快照。" lightbox="../media/memory-problems-memory-allocation-timeline-snapshot-highlighted-annotated.msft.png":::

单击堆中的特定对象将显示堆快照底部部分的保留树。  检查对象的保留路径应为您提供足够的信息来了解未收集对象的原因，并且应进行必要的代码更改以删除不必要的引用。


<!-- ====================================================================== -->
## <a name="view-memory-allocation-by-function"></a>按功能查看内存分配

可以通过 JavaScript 函数查看内存分配。  请参阅 [按功能调查内存分配](./index.md#investigate-memory-allocation-by-function)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/memory-problems/allocation-profiler) 由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
