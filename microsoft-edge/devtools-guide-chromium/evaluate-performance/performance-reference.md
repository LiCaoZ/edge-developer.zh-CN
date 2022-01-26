---
title: 时间线事件参考
description: 时间线事件模式显示录制时触发的所有事件。  使用时间线事件引用了解有关每个时间线事件类型更多信息。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 512856ca405d831d5f451be8f05ad2e8a8d1b62c
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12324081"
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

时间线事件模式显示录制时触发的所有事件。  使用时间线事件引用了解有关每个时间线事件类型更多信息。


<!-- ====================================================================== -->
## <a name="common-timeline-event-properties"></a>常见时间线事件属性

某些详细信息存在于所有类型的事件，而某些仅适用于特定事件类型。  本节列出了不同事件类型通用的属性。  特定于特定事件类型的属性在后续事件类型的引用中列出。

| 属性 | 何时显示 |
|:--- |:--- |
| 聚合时间 | 对于具有 **嵌套事件的事件**，每个事件类别所花时间。 |
| 调用堆栈 | 对于具有 **子事件的事件**，表示每个事件类别所花时间。 |
| CPU 时间 | 记录的事件占用的 CPU 时间。 |
| 详细信息 | 有关事件的其他详细信息。 |
| 时间戳 (的持续时间)  | 事件及其所有子项完成所用时间;timestamp 是事件发生的时间，相对于录制的开始时间。 |
| 自时间 | 事件在没有任何子事件的情况下所发生时间。 |
| 使用的堆大小 | 记录事件时应用程序使用的内存量，以及自上次采样 (使用的堆 (+/-) 更改的增量。 |

<!--todo: add nested and child events (timelinetool) section when available -->


<!-- ====================================================================== -->
## <a name="loading-events"></a>加载事件

此部分列出了属于 Loading 类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 分析 HTML |  Microsoft Edge HTML 分析算法。 |
| 完成加载 |  网络请求已完成。 |
| 接收数据 |  已接收请求的数据。  有一个或多个接收数据事件。 |
| 接收响应 |  来自请求的初始 HTTP 响应。 |
| 发送请求 |  已发送网络请求。 |

### <a name="loading-event-properties"></a>加载事件属性

| 属性 | 描述 |
|:--- |:--- |
| 资源 | 所请求资源的 URL。 |
| 预览 | 仅预览请求的资源 (图像) 。 |
| Request 方法 | 用于请求请求的 HTTP (或 ，例如 `GET` `POST`) 。 |
| 状态代码 | HTTP 响应代码。 |
| MIME 类型 | 所请求资源的 MIME 类型。 |
| 编码数据长度 | 请求的资源的长度（以字节为单位）。 |


<!-- ====================================================================== -->
## <a name="scripting-events"></a>脚本事件

本节列出了属于"脚本"类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 触发的动画帧 | 触发计划动画帧，并调用其回调处理程序。 |
| 取消动画帧 |  已取消计划的动画帧。 |
| GC 事件 |  发生垃圾回收。 |
| DOMContentLoaded |  [DOMContentLoaded 事件](https://developer.mozilla.org/docs/Web/Events/DOMContentLoaded)由浏览器触发。  加载和分析页面的所有 DOM 内容时，将触发此事件。 |
| 评估脚本 | 已评估脚本。 |
| 事件 | JavaScript 事件 (例如 、 或 `mousedown` `key`) 。 |
| 函数调用 | 仅在浏览器进入 JavaScript 引擎或 (，才出现顶级 JavaScript 函数) 。 |
| 安装计时器 | 计时器是使用 [setInterval () ](https://developer.mozilla.org/docs/Web/API/WindowTimers/setInterval) 或 [setTimeout () 创建的 ](https://developer.mozilla.org/docs/Web/API/WindowTimers/setTimeout)。 |
| 请求动画帧 | 安排 `requestAnimationFrame()` 新帧的呼叫。 |
| 删除计时器 | 已清除之前创建的计时器。 |
| 时间 |  一个称为 [console.time () 的脚本 ](/microsoft-edge/devtools-guide-chromium/console/api#time)。 |
| 时间结束 | 一个称为 [console.timeEnd () 的脚本 ](/microsoft-edge/devtools-guide-chromium/console/api#timeend)。 |
| 计时器触发 | 使用 或 计划触发的 `setInterval()` 计时器 `setTimeout()` 。 |
| XHR 就绪状态更改 | XMLHTTPRequest 的就绪状态已更改。 |
| XHR Load | 已完成 `XMLHTTPRequest` 加载。 |

### <a name="scripting-event-properties"></a>脚本事件属性

| 属性 | 描述 |
|:--- |:--- |
| 计时器 ID | 计时器 ID。 |
| 超时 | 计时器指定的超时。 |
| 重复 | 指定计时器是否重复的布尔值。 |
| 函数调用 | 已调用的函数。 |


<!-- ====================================================================== -->
## <a name="rendering-events"></a>呈现事件

此部分列出了属于"呈现"类别及其属性的事件。

| 事件 | 描述 |
|:--- |:--- |
| 无效布局 | 页面布局因 DOM 更改而无效。 |
| 布局 | 已完成页面布局。 |
| 重新计算样式 | Microsoft Edge重新计算的元素样式。 |
| 滚动 | 已滚动嵌套视图的内容。 |

### <a name="rendering-event-properties"></a>呈现事件属性

| 属性 | 描述 |
|:--- |:--- |
| 布局无效 | 对于布局记录，是导致布局失效的代码堆栈跟踪。 |
| 需要布局的节点 | 对于布局记录，表示在启动中继之前标记为需要布局的节点数。  这些节点通常是开发人员代码无效的节点，以及中继根的向上路径。 |
| 布局树大小 | 对于布局记录，中继根节点下的节点总数 (启动中继Microsoft Edge节点) 。 |
| 布局范围 | 可能的值 `Partial` (重新布局边界是 DOM 或 的一 `Whole document`) 。 |
| 受影响的元素 | 对于"重新计算样式记录"，为受样式重新计算影响的元素数。 |
| 样式无效 | 对于"重新计算样式"记录，提供导致样式无效的代码的堆栈跟踪。 |


<!-- ====================================================================== -->
## <a name="painting-events"></a>Painting 事件

此部分列出了属于 Painting 类别的事件及其属性。

| 事件 | 描述 |
|:--- |:--- |
| 复合层 | 用于呈现引擎的复合Microsoft Edge层。 |
| 图像解码 | 已解码图像资源。 |
| 图像调整大小 | 从图像本机尺寸调整了图像的大小。 |
| 画图 | 复合层绘制到屏幕的一个区域。  将鼠标悬停在画图可突出显示已更新的屏幕区域。 |

### <a name="painting-event-properties"></a>Painting 事件属性

| 属性 | 说明 |
|:--- |:--- |
| 位置 | 对于画图，绘制矩形的 x 和 y 坐标。 |
| 维度 | 对于画图事件，绘制区域的高度和宽度。 |


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于此处，[](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/performance-reference)由[Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) and [Flavio 一](https://developers.google.com/web/resources/contributors#flavio-copes) (Full Stack Developer) 创作。

[![Creative Commons License。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
