---
title: 时间线事件参考
description: 时间线事件模式显示在进行录制时触发的所有事件。  使用时间线事件引用详细了解每个时间线事件类型。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 0660fe3bdf9256dc5cbea46b4a76a1c77c77bf7e
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631422"
---
<!-- Copyright Meggin Kearney and Flavio Copes

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="timeline-event-reference"></a>时间线事件参考

时间线事件模式显示在进行录制时触发的所有事件。  使用时间线事件引用详细了解每个时间线事件类型。


<!-- ====================================================================== -->
## <a name="common-timeline-event-properties"></a>常见时间线事件属性

所有类型的事件中都存在某些详细信息，而某些详细信息仅适用于某些事件类型。  本部分列出了不同事件类型的常见属性。  后面那些事件类型的引用中列出了特定于某些事件类型的属性。

| 属性 | 显示时间 |
|:--- |:--- |
| 聚合时间 | 对于包含 **嵌套事件的事件**，每个事件类别所花的时间。 |
| 调用堆栈 | 对于 **具有子事件的事件**，每个事件类别所用的时间。 |
| CPU 时间 | 记录的事件占用了多少 CPU 时间。 |
| 详细信息 | 有关事件的其他详细信息。 |
| 时间戳) 的持续时间 ( | 活动花了多长时间才与所有子级一起完成;时间戳是事件发生的时间，相对于录制开始的时间。 |
| 自我时间 | 事件花了多长时间没有它的孩子。 |
| 已用堆大小 | 记录事件时应用程序使用的内存量，自上次采样以来，使用堆大小的增量 (+/-) 更改。 |

<!--todo: add nested and child events (timelinetool) section when available -->


<!-- ====================================================================== -->
## <a name="loading-events"></a>加载事件

本部分列出属于加载类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 分析 HTML |  Microsoft Edge 运行了 HTML 分析算法。 |
| 完成加载 |  网络请求已完成。 |
| 接收数据 |  已收到请求的数据。  有一个或多个接收数据事件。 |
| 接收响应 |  来自请求的初始 HTTP 响应。 |
| 发送请求 |  已发送网络请求。 |

### <a name="loading-event-properties"></a>加载事件属性

| 属性 | 描述 |
|:--- |:--- |
| 资源 | 请求的资源的 URL。 |
| 预览 | 仅)  (所请求的资源的预览。 |
| Request 方法 | 用于请求 (`GET` 或 `POST`) 的 HTTP 方法。 |
| 状态代码 | HTTP 响应代码。 |
| MIME 类型 | 请求资源的 MIME 类型。 |
| 编码的数据长度 | 请求的资源的长度（以字节为单位）。 |


<!-- ====================================================================== -->
## <a name="scripting-events"></a>脚本事件

本部分列出属于脚本类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 已触发动画帧 | 触发了计划的动画帧，并调用了回调处理程序。 |
| 取消动画帧 |  已取消计划的动画帧。 |
| GC 事件 |  发生了垃圾回收。 |
| DOMContentLoaded |  浏览器触发 [了 DOMContentLoaded 事件](https://developer.mozilla.org/docs/Web/Events/DOMContentLoaded) 。  加载和分析页面的所有 DOM 内容时，会触发此事件。 |
| 评估脚本 | 评估了脚本。 |
| 事件 | 例如 `mousedown`，JavaScript 事件 (或 `key`) 。 |
| 函数调用 |  (仅当浏览器进入 JavaScript 引擎) 时，才会显示顶级 JavaScript 函数调用。 |
| 安装计时器 | 使用 [setInterval () ](https://developer.mozilla.org/docs/Web/API/WindowTimers/setInterval) 或 [setTimeout () ](https://developer.mozilla.org/docs/Web/API/WindowTimers/setTimeout)创建计时器。 |
| 请求动画帧 | 呼叫 `requestAnimationFrame()` 计划了一个新帧。 |
| 删除计时器 | 已清除以前创建的计时器。 |
| 时间 |  名为 [console.time () ](/microsoft-edge/devtools-guide-chromium/console/api#time)的脚本。 |
| 时间结束 | 名为 [console.timeEnd () ](/microsoft-edge/devtools-guide-chromium/console/api#timeend)的脚本。 |
| 计时器已触发 | 一个计时器触发，计划与 `setInterval()` 或 `setTimeout()`。 |
| XHR 就绪状态更改 | XMLHTTPRequest 的就绪状态已更改。 |
| XHR 加载 | 已 `XMLHTTPRequest` 完成加载。 |

### <a name="scripting-event-properties"></a>脚本事件属性

| 属性 | 描述 |
|:--- |:--- |
| 计时器 ID | 计时器 ID。 |
| 超时 | 计时器指定的超时。 |
| 重复 | 指定计时器是否重复的布尔值。 |
| 函数调用 | 调用的函数。 |


<!-- ====================================================================== -->
## <a name="rendering-events"></a>呈现事件

本部分列出属于呈现类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 布局无效 | 页面布局因 DOM 更改而失效。 |
| 布局 | 页面布局已完成。 |
| 重新计算样式 | Microsoft Edge 重新计算元素样式。 |
| 滚动 | 嵌套视图的内容已滚动。 |

### <a name="rendering-event-properties"></a>呈现事件属性

| 属性 | 描述 |
|:--- |:--- |
| 布局失效 | 对于布局记录，导致布局失效的代码的堆栈跟踪。 |
| 需要布局的节点 | 对于布局记录，在中继启动之前标记为需要布局的节点数。  这些节点通常是开发人员代码失效的节点，外加一个向上到中继根的路径。 |
| 布局树大小 | 对于布局记录，中继根 (Microsoft Edge 启动中继) 的节点下的节点总数。 |
| 布局范围 | 可能的值 `Partial` (重新布局边界是 DOM) 或 `Whole document`的一部分。 |
| 受影响的元素 | 对于重新计算样式记录，受样式重新计算影响的元素数。 |
| 样式无效 | 对于重新计算样式记录，请提供导致样式失效的代码的堆栈跟踪。 |


<!-- ====================================================================== -->
## <a name="painting-events"></a>绘制事件

本部分列出属于“绘图”类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 复合层 | Microsoft Edge 呈现引擎的复合映像层。 |
| 图像解码 | 映像资源已解码。 |
| 图像调整大小 | 图像的原生维度调整了其大小。 |
| 画图 | 复合层被绘制到显示的区域。  将鼠标悬停在画图记录上突出显示已更新的显示区域。 |

### <a name="painting-event-properties"></a>绘制事件属性

| 属性 | 说明 |
|:--- |:--- |
| 位置 | 对于画图事件，油漆矩形的 x 和 y 坐标。 |
| 尺寸 | 对于画图事件，绘制区域的高度和宽度。 |


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在此](https://developer.chrome.com/docs/devtools/evaluate-performance/performance-reference/) 处找到，由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 和 [Flavio Copes](https://developers.google.com/web/resources/contributors#flavio-copes) (Full Stack 开发人员) 创作。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
