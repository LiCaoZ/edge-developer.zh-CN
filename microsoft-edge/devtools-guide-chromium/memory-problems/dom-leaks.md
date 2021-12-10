---
title: 调试 DOM 内存泄漏
description: 使用 DevTools Microsoft Edge分离的元素工具查找和修复 DOM 内存泄漏。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/30/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， 开发工具， 分离的元素， 文档对象模型， dom， 内存， 泄漏， 节点
ms.openlocfilehash: 2ff7292af7ff78618c3fdcfcf5d2c2ae9ef0b9a5
ms.sourcegitcommit: ccccb41b1695469774df7d3e0718184d0cea360f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2021
ms.locfileid: "12260906"
---
# <a name="debug-dom-memory-leaks-with-the-detached-elements-tool"></a>使用分离的元素工具调试 DOM 内存泄漏

当元素不再附加到文档对象模型 (DOM) 树，但仍由页面上运行的一些 JavaScript 引用时，应用程序中可能会发生内存泄漏。 这些元素称为 *分离元素*。 对于在已分离元素 (GC) 进行垃圾回收的浏览器，不得从 DOM 树或 JavaScript 代码引用该元素。

本文介绍如何使用 Microsoft Edge DevTools 中的分离元素工具查找浏览器无法在演示应用程序中 GC 的分离元素，并确定仍在引用已分离元素的 JavaScript。 **** 通过更改 JavaScript 以释放 元素，可以减少页面上的分离元素数量。

有关堆快照和分离元素详细信息，请阅读使用堆快照发现分离 [的 DOM 树内存泄漏](index.md#discover-detached-dom-tree-memory-leaks-with-heap-snapshots)。


<!-- ====================================================================== -->
## <a name="open-the-detached-elements-tool"></a>打开分离的元素工具

默认情况下 **，分离的元素**工具在 Microsoft Edge 97 及更高版本中可用。 通过进入 Microsoft Edge检查你的版本 `edge://version` 。 如果你的版本小于 97，请阅读打开或[](../experimental-features/index.md#turning-an-experiment-on-or-off)关闭实验，了解打开分离**元素实验**的说明。

打开分离 **的元素工具** ：

1. 打开 [演示应用程序](https://microsoftedge.github.io/Demos/detached-elements/)。

1. [打开 DevTools](../open/index.md)。

1. 单击 **+** 工具栏中的按钮。

1. 单击 **分离的元素**。

:::image type="content" source="./images/open-detached-elements.msft.png" alt-text="打开分离的元素工具。" lightbox="./images/open-detached-elements.msft.png":::


<!-- ====================================================================== -->
## <a name="get-detached-elements"></a>获取分离的元素

"**获取**分离元素 ("获取分离的元素"图标。"分离的元素"工具中的") "按钮在网页上查找并显示所有分离 ![ ](images/get-detached-elements-icon-light-mode.png) 的元素。 ****

若要查找分离的元素：

1. 在演示应用程序中，确保选中"会议室 **1"** 按钮。

1. 在演示应用程序中，单击" **模拟高流量"** 按钮。

1. 在演示应用程序中生成并显示某些消息后，单击演示的"停止 **"** 按钮。

:::image type="content" source="./images/detached-elements-demo-app.msft.png" alt-text="在演示应用程序中生成一些消息。" lightbox="./images/detached-elements-demo-app.msft.png":::

1. 单击 **"会议室 2"** 按钮。

1. 在"**分离的元素"** 工具中，单击****"获取分离的元素 ![ (""分离的元素"图标。) ](images/get-detached-elements-icon-light-mode.png) 图标。

:::image type="content" source="./images/get-detached-elements.msft.png" alt-text="使用分离的元素工具获取分离的元素。" lightbox="./images/get-detached-elements.msft.png":::

分离 **的元素** 工具显示页面的所有分离元素。  在演示应用程序中切换到 **Room 2** 时，会议室 **1** 中生成的消息不再附加到 DOM，但仍由 JavaScript 引用。


<!-- ====================================================================== -->
## <a name="trigger-garbage-collection"></a>触发垃圾回收

接下来，在浏览器中 (GC) 垃圾回收：

1. 在"**分离的元素"** 工具中，单击****"收集 (垃圾回收"图标。) ![ ](images/collect-garbage-icon-light-mode.png) 图标。

1. 单击" **获取分离的元素** ![ ("分离的元素"图标。) ](images/get-detached-elements-icon-light-mode.png) 图标。

选择" **收集垃圾"时**，浏览器将运行垃圾回收。 选择"**获取分离的元素**"时，"**** 分离的元素"工具将显示无法进行垃圾回收的所有已分离元素。 如果应用程序不会重用这些分离的元素，则这些分离的元素可能是内存泄漏。


<!-- ====================================================================== -->
## <a name="identify-the-javascript-code-that-retains-detached-elements"></a>标识保留已分离元素的 JavaScript 代码

找到无法进行垃圾回收的分离元素后，可以使用分离元素工具中的"分析"按钮识别**** 仍在引用已分离**** 元素的页面上运行的 JavaScript 代码。 "**分析**"按钮获取堆快照，并使用已分离元素在堆中的位置填充该元素的**ID。** 有关堆快照详细信息，请阅读 [记录堆快照](heap-snapshots.md)。

:::image type="content" source="./images/analyze-detached-elements.msft.png" alt-text="分析分离的元素工具中的分离元素。" lightbox="./images/analyze-detached-elements.msft.png":::

若要标识引用已分离元素的 JavaScript 代码，请执行以下操作：

1. 在分离 **的元素工具** 中， **单击分析 (** 分析图标。) ![ ](images/analyze-icon-light-mode.png) 图标。

    内存 **工具** 将在 DevTools 的底部面板中打开。

1. 从 **"分离的元素"** 工具中，选择已分离元素的 **Id** 字段。

   底部 **面板** 中的"内存"工具会自动选择堆中引用已分离元素的对象。 我们将这些对象称为 **"保留者"。**

   :::image type="content" source="./images/detached-elements-heap-snapshot.msft.png" alt-text="从分离的元素工具引用堆快照。" lightbox="./images/detached-elements-heap-snapshot.msft.png":::

1. 在底部**面板**的内存工具中，选择链接 **"room.js：13"。**

   " **源** "工具在顶部面板中打开到文件的第 13 ** 行 **room.js。

1. 在room.js函数中，演示应用程序的 JavaScript 代码会将会议室中的每条消息 `hide()` 添加到**** `unmounted` 数组中。 `unmounted`数组是引用已分离元素的对象。

:::image type="content" source="./images/detached-elements-javascript-retainers.msft.png" alt-text="标识保留已分离元素的 JavaScript。" lightbox="./images/detached-elements-javascript-retainers.msft.png":::

现在，你已确定阻止浏览器对已分离元素进行垃圾回收的保留器！


<!-- ====================================================================== -->
## <a name="identify-the-dom-node-causing-others-to-be-retained"></a>标识导致其他保留的 DOM 节点

由于 DOM 是一个完全连接的图形，因此当 JavaScript 将一个 DOM 节点保留在内存中时，它可能导致其他 DOM 节点随它一起保留。

若要标识导致保留整个树的已分离树中的原因节点：

1.  单击" **分离** 元素 ("分离元素"图标。单击) "图标以破坏分离树内的 ![ ](images/detach-elements-icon-light-mode.png) 父子链接。

    :::image type="content" source="./images/detached-elements-remove-links.msft.png" alt-text="分离的元素工具中的分离元素按钮。" lightbox="./images/detached-elements-remove-links.msft.png":::

1.  单击收集 **垃圾 ("** ![ 收集垃圾"图标。) ](images/collect-garbage-icon-light-mode.png) 图标。

父子链接在分离的树内删除。


<!-- ====================================================================== -->
## <a name="change-the-selected-target-to-a-different-origin"></a>将所选目标更改为其他源

可以使用"选定目标"下拉列表检查不同源或不同帧的 **分离** 元素。 

1.  单击" **选定的目标** "下拉列表。

    :::image type="content" source="./images/detached-elements-target-dropdown.msft.png" alt-text="&quot;选择的目标&quot;下拉列表允许你选择不同的来源。" lightbox="./images/detached-elements-target-dropdown.msft.png":::

1.  选择其他源。

新源显示在分离 **的元素工具** 中。

   
<!-- ====================================================================== -->
## <a name="additional-considerations"></a>其他注意事项

在查找内存泄漏时，请记住泄露可能取决于应用程序的上下文。 对于演示应用程序，你发现了浏览器无法垃圾回收的已分离元素，并且你标识了保留已分离元素的 JavaScript。 但是，在演示应用程序的上下文中，保留聊天消息列表是有意义的，这样，如果用户切换回会议室 **1，** 则保留消息日志。

下图以消息形式显示分离的元素，当用户从会议室 **2** 导航回会议室 1 时，会 **重新附加这些元素**。 

:::image type="content" source="./images/detached-elements-reattached.msft.png" alt-text="切换回会议室 1 时，分离的元素会重新连接至 DOM。" lightbox="./images/detached-elements-reattached.msft.png":::

同样，当用户滚动过去时，社交媒体中的源可能会分离元素，当用户向后滚动时，再将它们重新附加到 DOM。 分离的元素并不总是指示内存泄漏，内存泄漏并不总是由分离的元素导致。

对于长时间运行的应用，仅泄露几千字节的小内存可能会随着时间的推移显著降低性能。 使用此 React 框架的 Web 开发人员知道React维护 DOM 的虚拟化副本。 无法正确卸载组件可能会导致应用程序泄露虚拟 DOM 的较大部分。

此演示应用及其泄漏是人为的。 在生产网站或应用上测试分离的元素工具。 如果发现分离元素工具的潜在问题，请与 Microsoft Edge [DevTools](../contact.md)团队联系，以发送有关分离元素工具和内存泄漏**** 调试的反馈。