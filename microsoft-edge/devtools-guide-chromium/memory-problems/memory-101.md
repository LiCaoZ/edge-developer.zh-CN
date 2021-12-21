---
title: 内存术语
description: 内存分析中使用的常用术语，适用于适用于不同语言的各种内存分析工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: d59ee21f3d7a6972fa369501c222ba8f9aea2963
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286364"
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
# <a name="memory-terminology"></a>内存术语

本文介绍内存分析中使用的常见术语，适用于不同语言的各种内存分析工具。

此处介绍的术语和概念是指内存 [面板](./heap-snapshots.md)。  如果你曾经使用过 Java、.NET 或其他一些内存探查器，那么本文可能是一个刷新程序。


<!-- ====================================================================== -->
## <a name="object-sizes"></a>对象大小

将内存视为包含基元类型的图形 (数字和字符串) 关联数组 (对象) 。  它可能会显示为具有许多互连点的图形，如下图所示。

:::image type="complex" source="../media/memory-problems-thinkgraph.msft.png" alt-text="内存的视觉表示形式" lightbox="../media/memory-problems-thinkgraph.msft.png":::
   内存的视觉表示形式
:::image-end:::

对象可能以两种方式保留内存：

*   直接由 对象。
*   隐式保留对其他对象的引用，从而阻止垃圾收集器自动释放这些对象。

在使用 DevTools 中的内存面板 (发现的内存问题的工具在 Memory **) **下找到时，你可能会发现自己正在查看一些不同的信息列。 [](./heap-snapshots.md)  两个突出的"浅 **表** 大小"和 **"保留大小**"，但这表示什么？

:::image type="complex" source="../media/memory-problems-shallow-retained.msft.png" alt-text="浅表和保留大小" lightbox="../media/memory-problems-shallow-retained.msft.png":::
   浅表和保留大小
:::image-end:::

### <a name="shallow-size"></a>浅表大小

这是对象所持有的内存大小。

典型的 JavaScript 对象会保留一些内存以供其说明和存储即时值。  通常，只有数组和字符串才能具有明显的浅表大小。  但是，字符串和外部数组通常具有呈现器内存中的主存储，从而在 JavaScript 堆上只公开一个小包装对象。

呈现器内存是呈现已检查页面的过程的所有内存：页面的本机内存 + JS 堆内存以及页面启动的所有专用工作者的 JS 堆内存。  但是，即使一个小对象，也能够间接地保留大量内存，防止自动垃圾回收过程释放其他对象。

### <a name="retained-size"></a>保留大小

这是在对象删除后释放的内存大小，以及从垃圾回收器根目录无法访问的从属 **对象**。

**垃圾回收器根** 由在本地 **或** 全局 (创建) 从本机代码引用 V8 外部的 JavaScript 对象时创建的句柄。  可以在 GC 根下的堆快照内找到所有此类**** 句柄  >  **处理范围**和**GC 根**  >  **全局句柄**。  在本文档中介绍句柄而不深入介绍浏览器实现的详细信息可能会令人困惑。  垃圾回收器根和句柄都不需要担心。

存在大量内部垃圾回收器根，其中大多数对用户不感兴趣。  从应用程序的角度来看，有以下类型的根。

*   窗口全局对象 (iframe 对象) 。  在堆快照中，字段指示窗口最短保留 `distance` 路径上的属性引用数。
*   文档 DOM 树，由通过遍历文档可到达的所有本机 DOM 节点组成。  并非所有节点都有 JavaScript 包装器，但如果节点有包装器，则节点在文档处于活动状态时处于活动状态。
*   有时，对象由源工具和控制台中的调试上下文保留****，例如控制台评估**** 之后。  使用清除的控制台工具 **创建** 堆快照，在"源"工具的调试器中没有活动的 **断** 点。

>[!TIP]
> 在"内存"工具中拍摄堆 [快照之前，](./heap-snapshots.md) 请清除 **"** 控制台"工具，并停用"源"工具中的 **断** 点。  若要清除 **控制台工具** ，请运行 `clear()` 方法。

内存图以根开头，该根可能是浏览器的对象或Node.js `window` `Global` 对象。  您不控制如何垃圾回收根对象。

:::image type="complex" source="../media/memory-problems-dontcontrol.msft.png" alt-text="你无法控制如何对根对象进行垃圾回收。" lightbox="../media/memory-problems-dontcontrol.msft.png":::
   你无法控制如何对根对象进行垃圾回收。
:::image-end:::

从根目录无法到达的任何对象都会进行垃圾回收。

> [!NOTE]
> "[浅表大小"](#shallow-size)[和"保留大小"](#retained-size)列均表示以字节为单位的数据。


<!-- ====================================================================== -->
## <a name="objects-retaining-tree"></a>保留树的对象

堆是互连对象的网络。  在数学世界，此结构称为 **图形或** 内存图。  图形由**通过边缘连接的**节点构造，两者都是**** 给定的标签。

*   **节点** (**或**) 使用用于构建这些节点或对象的构造函数函数的名称进行标记。 ****
*   **边缘** 使用属性 的名称 **标记**。

了解如何 [使用堆配置文件器记录配置文件](./heap-snapshots.md)。  在下图中，内存工具中堆快照记录中的一些 [值得注意的事项包括](./heap-snapshots.md) 距离：垃圾回收器根之间的距离。  如果几乎同一类型的所有对象都位于同一距离，而其中一些对象距离较大，那么这一点值得研究。

:::image type="complex" source="../media/memory-problems-root.msft.png" alt-text="与根之间的距离" lightbox="../media/memory-problems-root.msft.png":::
   与根之间的距离
:::image-end:::


<!-- ====================================================================== -->
## <a name="dominators"></a>Dominators

Dominator 对象由树结构组成，因为每个对象只有一个管理程序。  对象的管理者可能缺少对它所控制的对象的直接引用;也就是说，管理器的树不是图形的跨越树。

在下图中，以下语句为 true。

*   节点 1 控制节点 2
*   节点 2 控制节点 3、4 和 6
*   节点 3 与节点 5
*   节点 5 控制节点 8
*   节点 6 与节点 7

:::image type="complex" source="../media/memory-problems-dominatorsspanning.msft.png" alt-text="Dominator 树结构" lightbox="../media/memory-problems-dominatorsspanning.msft.png":::
   Dominator 树结构
:::image-end:::

在下图中，node 是 的管理程序，但也存在于从垃圾回收器到 `#3` `#10` `#7` 的每个简单路径 `#10` 中。  因此，如果 B 存在于从根到对象 A 的每一个简单路径中，则对象 B 是对象 A 的管理者。

:::image type="complex" source="../media/memory-problems-dominators.msft.gif" alt-text="动画管理程序图示" lightbox="../media/memory-problems-dominators.msft.gif":::
   动画管理程序图示
:::image-end:::


<!-- ====================================================================== -->
## <a name="v8-specifics"></a>V8 特定内容

分析内存时，了解堆快照为何以特定方式显示非常有用。  本节介绍一些与内存相关的主题，这些主题专门与 **V8 VM** 或 VM (V8 JavaScript 虚拟机) 。

### <a name="javascript-object-representation"></a>JavaScript 对象表示形式

有三种基元类型：

*   数字 `3.14159...` (例如) 
*   布尔值 (`true` 或 `false`) 
*   字符串 `"Werner Heisenberg"` (例如) 

基元无法引用其他值，并且始终是叶节点或终止节点。

**数字** 可以存储为：

*   一个称为小整数的直接 31**** 位整数 (**SMI**) ，或
*   堆对象，称为 **堆数**。 堆编号用于存储不适合 SMI 表单的值（如双精度数）或需要对**** 值进行装箱时（例如设置其属性）。 ****

**字符串** 可以存储在：

*   **VM 堆**， 或
*   在呈现 **器的内存外部**。  创建 **包装** 对象并用于访问外部存储，例如，存储从 Web 接收的脚本源和其他内容，而不是复制到 VM 堆。

新 JavaScript 对象的内存从专用 JavaScript 堆或 VM (**分配) 。**  这些对象由 V8 中的垃圾回收器管理，因此，只要至少有一个对对象的强引用，它们就保持活动状态。

不在 JavaScript 堆中任何内容都称为 **本机对象**。  与堆对象相反，本机对象在生命周期内不由 V8 垃圾回收器管理，并且只能使用 JavaScript 包装对象从 JavaScript 访问。

**Cons string** 是一个包含存储然后联接的字符串对的对象，它是连接的结果。  仅根据需要 **联接 cons 字符串** 内容。  例如，需要构造联接字符串的子字符串时。

例如，如果连接 和 `a` ，则 `b` 得到一个表示连接结果 `(a, b)` 的字符串。  如果稍后连接了 `d` 该结果，则得到另一个 **cons 字符串**： `((a, b, d)` 。

**Array** 是一个包含数字键的对象。 **数组** 在 V8 VM 中广泛使用，用于存储大量数据。 键值对集（如字典）由数组 **进行备份**。

典型的 JavaScript 对象仅存储为两种数组类型 **之** 一：

*   命名属性和
*   数值元素

当有少量属性时，这些属性将内部存储在 JavaScript 对象中。

**Map** 是描述对象种类和布局的对象。 例如，映射用于描述用于快速属性访问的隐式 [对象层次结构](https://v8.dev/blog/fast-properties)。

### <a name="object-groups"></a>对象组

每个 **本机对象** 组由相互引用的对象所共同决定。  例如，考虑一个 DOM 子树，其中每个节点都有一个指向相对父级的链接和指向下一个子级和下一个同级元素的链接，因此形成一个连接的图形。

> [!NOTE]
> 本机对象不表示在 JavaScript 堆中。  缺少表示是本机对象的大小为零的原因。 相反，会创建包装对象。

每个包装对象保存对相应本机对象的引用，用于将命令重定向到该对象。  反过来，对象组会保留包装对象。  但是，这不会创建一个不可存储的循环，因为垃圾回收器足够智能，可以释放不再引用其包装器的对象组。  但忘记释放单个包装会保留整个组和关联的包装器。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/memory-problems/memory-101) 由技术编写人员 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (创作) 。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
