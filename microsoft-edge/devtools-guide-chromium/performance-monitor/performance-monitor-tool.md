---
title: 性能监视器
description: DevTools 中的性能监视器工具提供实时性能指标，以帮助调查性能问题。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 10/28/2021
ms.openlocfilehash: 9393ce7bf725b79cbb6653627763e49ae0775ea2
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284201"
---
# <a name="performance-monitor"></a>性能监视器

在**DevTools** Microsoft Edge性能监视器工具，可实时查看网页的运行时性能。

性能 **监视器** 工具可帮助确定性能问题来自何处。  网站运行缓慢的原因有多种。  此工具提供了一些线索，用于了解这些问题是否与原因相关，例如：
*  高内存或 CPU 使用率。
*  布局和样式计算过于频繁。
*  DOM 节点和事件侦听器过多。


<!-- ====================================================================== -->
## <a name="open-the-performance-monitor-tool"></a>打开性能监视器工具

打开性能监视器：

1. [打开 DevTools，](../open/index.md)例如按 `F12` 。

1. 单击 **"其他** `+` () "，然后选择"性能**监视器"。**

:::image type="content" source="../media/performance-monitor-tool/open-performance-monitor.png" alt-text="&quot;更多工具&quot;菜单，显示&quot;性能监视器&quot;菜单命令。":::

性能监视器显示实时更新的各种性能指标的图形。

:::image type="content" source="../media/performance-monitor-tool/performance-monitor-first-open.png" alt-text="首次打开性能监视器工具时的外观。" lightbox="../media/performance-monitor-tool/performance-monitor-first-open.png":::


<!-- ====================================================================== -->
## <a name="select-performance-metrics-to-monitor"></a>选择要监视的性能指标

默认情况下 **，性能** 监视器工具显示三个性能指标，并且提供了其他指标。

| 性能指标 | 描述 |
|---|---|
| **CPU 使用率** | 网页使用的 CPU 百分比。  默认情况下显示。 |
| **JS 堆大小** | 页面上 JavaScript 程序使用的内存量。  默认情况下显示。 |
| **DOM 节点** | 浏览器中跨选项卡的 DOM 节点 (个) 。  默认情况下显示。 |
| **JS 事件侦听器** | 浏览器中跨选项卡的 JavaScript 事件侦听器 (数) 。 |
| **文档** | 浏览器中跨选项卡显示的文档 (数) 。 |
| **文档框架** | 浏览器上的文档框架数 (选项卡) 。 |
| **布局/秒** | 浏览器引擎每秒构造页面布局次数。 |
| **样式重新计算/秒** | 浏览器引擎每秒计算页面的 CSS 样式次数。 |

若要启用或禁用任何可用的性能指标，请单击侧栏中的标签。

:::image type="content" source="../media/performance-monitor-tool/performance-monitor-metrics.png" alt-text="性能监视器边栏，显示可切换的各种指标。" lightbox="../media/performance-monitor-tool/performance-monitor-metrics.png":::
