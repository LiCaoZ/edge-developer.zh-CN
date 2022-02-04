---
title: 性能功能参考
description: 在 Microsoft Edge DevTools 中记录和分析性能所有方法的参考。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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
# <a name="performance-features-reference"></a>性能功能参考

此页面全面引用了与分析性能相关的 DevTools 功能。

有关如何使用性能工具分析页面性能的分步教程，请参阅开始[分析运行时性能](./index.md)。****


<!-- ====================================================================== -->
## <a name="record-performance"></a>记录性能

### <a name="record-runtime-performance"></a>记录运行时性能

当你想在页面运行时 (而非加载时) 分析其性能时，将记录运行时性能。

1. 转到要分析的页面。

1. 单击 DevTools 中的"性能"工具。****

1. 单击"**录制 (**!["图标。) ](../media/record-icon.msft.png)按钮。

   :::image type="content" source="../media/evaluate-performance-performance-record-highlight.msft.png" alt-text="记录。" lightbox="../media/evaluate-performance-performance-record-highlight.msft.png":::

1. 与页面交互。  DevTools 将记录由于交互而发生的所有页面活动。

1. 再次 **单击"录制** "或单击 **"停止** "停止录制。

### <a name="record-load-performance"></a>记录加载性能

当你想在页面加载时 (而非运行时) 分析其性能时，将记录加载时性能。

1. 转到要分析的页面。

1. 在 DevTools 中，打开 **性能** 工具。

1. 单击"**刷新"页 (**!["刷新](../media/refresh-page-icon.msft.png)页面"。) "按钮。  DevTools 在页面刷新时记录性能指标，然后在加载完成后几秒钟自动停止记录。

:::image type="content" source="../media/evaluate-performance-performance-refresh-button.msft.png" alt-text="刷新页面。" lightbox="../media/evaluate-performance-performance-refresh-button.msft.png":::

DevTools 会自动放大大部分活动发生的记录部分。

:::image type="content" source="../media/evaluate-performance-performance-refreshed.msft.png" alt-text="页面加载录制。" lightbox="../media/evaluate-performance-performance-refreshed.msft.png":::

### <a name="capture-screenshots-while-recording"></a>录制时捕获屏幕截图

若要在录制时捕获每个帧的屏幕截图，请选中 **"屏幕截图"** 复选框。

:::image type="content" source="../media/evaluate-performance-performance-capture-screenshots-checkbox.msft.png" alt-text="&quot;屏幕截图&quot;复选框。" lightbox="../media/evaluate-performance-performance-capture-screenshots-checkbox.msft.png":::

若要了解如何与屏幕截图进行交互，请参阅 [查看屏幕截图](#view-a-screenshot)。

### <a name="force-garbage-collection-while-recording"></a>录制时强制收集垃圾

在记录页面时，单击****!["收集垃圾 (收集垃圾图标](../media/collect-garbage-icon.msft.png)。) 强制进行垃圾回收。

:::image type="content" source="../media/evaluate-performance-performance-collect-garbage-button.msft.png" alt-text="收集垃圾。" lightbox="../media/evaluate-performance-performance-collect-garbage-button.msft.png":::

### <a name="show-recording-settings"></a>显示录制设置

单击**捕获 (**![捕获](../media/capture-settings-icon.msft.png)设置。) 公开与 DevTools 如何捕获性能记录相关的更多设置。

:::image type="content" source="../media/evaluate-performance-performance-capture-settings-button-open-drawer.msft.png" alt-text="&quot;捕获设置部分。" lightbox="../media/evaluate-performance-performance-capture-settings-button-open-drawer.msft.png":::

### <a name="disable-javascript-samples"></a>禁用 JavaScript 示例

默认情况下，录制的 **主** 部分会显示录音期间调用的 JavaScript 函数的详细调用栈。  禁用以下调用堆栈:

1. 打开 **“捕获设置”** 菜单。  请参阅 [显示录制设置](#show-recording-settings)。

1. 打开 **“禁用 JavaScript 示例”** 复选框。

1. 记录页面。

以下两个图显示了禁用和启用 JavaScript 示例的区别。  当禁用取样时，录音的**主**部分要短得多，因为它省略了所有的 JavaScript 调用堆栈。

禁用 JS 示例时录制的示例：

:::image type="content" source="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-on.msft.png" alt-text="禁用 JS 示例时录制的示例。" lightbox="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-on.msft.png":::

启用 JS 示例时录制的示例：

:::image type="content" source="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off.msft.png" alt-text="启用 JS 示例时录制的示例。" lightbox="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off.msft.png":::

### <a name="throttle-the-network-while-recording"></a>在录制时限制网络

若要在录制时限制网络:

1. 打开 **“捕获设置”** 菜单。  请参阅 [显示录制设置](#show-recording-settings)。

1. 将 **“网络”** 设置为所需的限制级别。

### <a name="throttle-the-cpu-while-recording"></a>录制时限制 CPU

若要在录制时限制 CPU:

1. 打开 **“捕获设置”** 菜单。  请参阅 [显示录制设置](#show-recording-settings)。

1. 将 **“CPU”** 设置为所需的限制级别。

限制是相对于计算机的功能而言的。  例如，**两倍减速** 选项使 CPU 运行速度比正常情况下慢两倍。  DevTools 不会真正模拟移动设备的 CPU，因为移动设备的体系结构与台式机和笔记本电脑的体系结构完全不同。

### <a name="turn-on-advanced-paint-instrumentation"></a>启用高级画图检测工具

查看详细画图检测工具:

1. 打开 **“捕获设置”** 菜单。  请参阅 [显示录制设置](#show-recording-settings)。

1. 选中 **“启用画图检测工具 (慢速)”** 复选框。

若要了解如何与绘制信息进行交互，请参阅查看 [图层](#view-layers-information) 和 [查看画图探查器](#view-paint-profiler)。


<!-- ====================================================================== -->
## <a name="save-a-recording"></a>保存录制内容

若要保存录制，请右键单击该录制，然后选择"保存 **配置文件"**。

:::image type="content" source="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-save-profile.msft.png" alt-text="保存配置文件。" lightbox="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-save-profile.msft.png":::


<!-- ====================================================================== -->
## <a name="load-a-recording"></a>加载录制

若要加载录制，请右键单击该录制，然后选择" **加载配置文件"**。

:::image type="content" source="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-load-profile.msft.png" alt-text="加载配置文件。" lightbox="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-load-profile.msft.png":::


<!-- ====================================================================== -->
## <a name="clear-the-previous-recording"></a>清除上一记录

录制后，单击 **"清除录制** (![清除录制"](../media/clear-recording-icon.msft.png) 图标。) "性能"工具清除 **该** 录制。

:::image type="content" source="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-clear-button.msft.png" alt-text="清除录制。" lightbox="../media/evaluate-performance-performance-refreshed-disable-javascript-samples-checkbox-off-clear-button.msft.png":::


<!-- ====================================================================== -->
## <a name="analyze-a-performance-recording"></a>分析性能录制

在 [录制运行性能](#record-runtime-performance) 或 [录制加载性能](#record-load-performance) 之后， **性能** 面板将提供许多数据以分析刚发生的操作的性能。

### <a name="select-a-portion-of-a-recording"></a>选择录制的一部分

在 **“概述”** 上向左或向右拖动鼠标，以选择一段录音的一部分。  **概述** 是包含 **FPS**、**CPU** 和 **NET** 图表的部分。

:::image type="content" source="../media/evaluate-performance-performance-zoom-highlighted.msft.png" alt-text="将鼠标拖动到概述中可缩放。" lightbox="../media/evaluate-performance-performance-zoom-highlighted.msft.png":::

若要使用键盘选择一部分:

1. 选择"**主"部分**的背景或它旁边的任何部分，如"**交互**"、网络或 **GPU**。 ****  此键盘工作流仅在其中一个分区为焦点时有效。

1. 使用 `W`、`A`、`S`、`D` 键分别进行放大、向左移动、缩小和向右移动。

若要使用跟踪板选择部分：

1. 将鼠标悬停在 **“概述”** 部分或 **“详细信息”** 上。  **概述** 部分是包含 **FPS**、**CPU** 和 **NET** 图表的区域。  **详细信息** 部分是包含 **主** 部分、**交互** 部分等的区域。

1. 使用两根手指，向上轻扫进行缩小，向左轻扫向左移动，向下轻扫进行放大，向右轻扫向右移动。

若要在"主"部分或任何元素**** 中滚动长图表，请在向上和向下拖动时单击并按住。  向左和向右拖动，移动录音中所选的部分。

### <a name="search-activities"></a>搜索活动

按 `Ctrl`+`F` (Windows、Linux) 或`F` `Command`+ (macOS) 打开"性能"面板底部的**搜索**框。

:::image type="content" source="../media/evaluate-performance-performance-search-regex.msft.png" alt-text="搜索框。" lightbox="../media/evaluate-performance-performance-search-regex.msft.png":::

导航与查询匹配的活动:

1. 单击"上**一 (**!["。](../media/previous-icon.msft.png)**) "下**一 (!["下](../media/next-icon.msft.png)一) 按钮。

1. 若要选择下一个活动，请按 `Enter`。  若要选择上一个活动，请按 `Shift`+`Enter`。

修改查询设置:

*  若要使查询区分大小写，请单击****!["区分大小写 (区分大小写](../media/search-case-icon.msft.png)。) 按钮。

*  若要在查询中使用正则表达式，请单击****!["正则表达式 (正则表达式](../media/search-regex-icon.msft.png)") 按钮。

若要隐藏搜索框，请单击"取消 **"**。

### <a name="view-main-thread-activity"></a>查看主线程活动

使用 **主** 部分查看出现在页面主线程上的活动。

:::image type="content" source="../media/evaluate-performance-performance-main-zoomed.msft.png" alt-text="&quot;主&quot;部分。" lightbox="../media/evaluate-performance-performance-main-zoomed.msft.png":::

在"摘要"面板中选择一个事件以查看其 **详细信息** 。  DevTools 概括了所选事件。

:::image type="content" source="../media/evaluate-performance-performance-summary-me.msft.png" alt-text="有关&quot;摘要&quot;面板中的匿名函数详细信息。" lightbox="../media/evaluate-performance-performance-summary-me.msft.png":::

DevTools 使用火焰图表示主线程活动。  x 轴表示一段时间内的记录。  Y 轴表示调用堆叠。  顶部事件将导致其下方事件。

:::image type="content" source="../media/evaluate-performance-performance-main-flame-chart.msft.png" alt-text="绘制图表。" lightbox="../media/evaluate-performance-performance-main-flame-chart.msft.png":::

在上一图中，`click` 事件在 53 行的 `activitytabs.js` 中造成了 `Function Call`。  在 `Function Call` 下面，查看匿名函数运行。  匿名函数请求 `Minor GC`的请求 `wait`的请求 `a`。

DevTools 为脚本随机分配颜色。  在上图中，请求来自脚本的函数请求染成为浅绿色。  来自另一个脚本的请求以米色表示。  深黄色代表脚本活动，紫色事件代表渲染活动。  这些深黄色和紫色事件在所有记录中都是一致的。

如果要隐藏 JavaScript 请求的详细图表，请参阅上面的 [禁用 JavaScript](#disable-javascript-samples) 示例。
禁用 JS 示例后`Event: click``Function Call`，仅处理上图中的和等高级事件 <!--`str` (?)--> 显示。
<!--When JS samples are disabled, you only see high-level events such as `Event (click)` and `Function Call` (script_foot_closure.js:53) from Figure 16.-->


### <a name="view-activities-in-a-table"></a>查看表格中的活动

录制页面后，无需仅依赖"主 **"部分来** 分析活动。  DevTools 还提供了三种用于分析活动的表格视图。  每个视图提供对待活动的不同视角:

*  若要查看导致工作最多的根活动，请使用"调用树 ["](#the-call-tree-tab) 选项卡。

*  若要查看直接花费时间最多的活动，请使用" [底部向上"](#the-bottom-up-panel) 选项卡。

*  若要按记录期间活动发生的顺序查看活动，请使用" [事件日志"](#the-event-log-panel) 选项卡。


#### <a name="root-activities"></a>根活动

打开新 [窗口或选项卡](https://microsoftedge.github.io/Demos/devtools-performance-activitytabs/) 中的活动选项卡演示网页。

<!-- You can view the source files for the Activity Tabs Demo in the [MicrosoftEdge/Demos > devtools-performance-activitytabs](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-performance-activitytabs) repo folder. -->

下面是"呼叫树"面板、****"底部向上"面板和"事件**** 日志"面板中**** 提及的根活动**概念**的说明。

_根_ 活动是导致浏览器执行某些工作的活动。  例如，当您单击某个网页时，浏览器将运行一 `Event` 个活动作为根活动。  `Event` 可能会导致处理程序运行等。

在 **主** 部分的火焰图中，根活动位于图表顶部。  在 **“调用树”** 和 **“活动日志”** 面板中，根活动是顶级项目。

有关根活动的示例，请参阅下一节"调用树选项卡"。

#### <a name="the-call-tree-tab"></a>"呼叫树"选项卡

打开新 [窗口或选项卡](https://microsoftedge.github.io/Demos/devtools-performance-activitytabs/) 中的活动选项卡演示网页。

使用" **呼叫树** "选项卡可查看 [哪些根活动](#root-activities) 导致工作最多。

" **呼叫树** "选项卡仅显示在录制的选定部分期间的活动。  请参阅 [选择录音的一部分](#select-a-portion-of-a-recording) ，了解如何选择部分。

:::image type="content" source="../media/evaluate-performance-performance-call-tree.msft.png" alt-text="&quot;呼叫树&quot;面板。" lightbox="../media/evaluate-performance-performance-call-tree.msft.png":::

在上图中，**“活动”** 列中的顶级项目，如 `Evaluate Script` 和 `Parse HTML` 是根活动。  嵌套表示调用堆栈。  例如，在上图中，导致 `Compile Script` 和 `(anonymous)` 的 `Evaluate Script` 的 `Parse HTML`。

**“自我时间”** 表示直接用于该活动的时间。  **“总时间”** 表示花在该活动或任何子项上的时间。

单击 **"自时间****、总**时间"或 **"活动**"按该列对表进行排序。

使用 **“筛选器”** 文本框按活动名称筛选事件。

默认情况下，**“分组”** 菜单设置为 **“无分组”**。  使用 **“分组”** 菜单，根据各种条件对活动表进行排序。

单击 **"显示最**![ (堆栈") 显示"](../media/show-heaviest-stack-icon.msft.png)活动"表**右侧的另一**个表。  单击活动以填充 **"最富堆栈"** 表。  **“最重堆栈”** 表显示所选活动的子项需要最长的运行时间。

#### <a name="the-bottom-up-panel"></a>自下而上面板

打开新 [窗口或选项卡](https://microsoftedge.github.io/Demos/devtools-performance-activitytabs/) 中的活动选项卡演示网页。

使用 **“自下而上”** 面板查看直接采用聚合时间的活动。

**“自下向上”** 面板仅在录制的选定部分期间显示活动。  请参阅 [选择录音的一部分](#select-a-portion-of-a-recording) ，了解如何选择部分。

:::image type="content" source="../media/evaluate-performance-performance-bottoms-up.msft.png" alt-text="&quot;Bottom-Up面板。" lightbox="../media/evaluate-performance-performance-bottoms-up.msft.png":::

在上 **图** 的主节绘制图中，可以看到几乎所有的时间都用于运行 `Parse HTML`。  前图中 **“自下而上”** 面板中最上面的活动是 `Parse HTML`。  <!-- in orig article: In the flame chart of the previous figure, the yellow below the calls to `wait` are actually thousands of `Minor GC` calls.  -->  In the **Bottom-Up** tab， the next most expensive activity is `Layout`.

**“自我时间”** 列表示跨越发生的所有直接用于该活动的聚合时间。

**“总时间”** 列表示花在该活动或任何子项上的聚合时间。

#### <a name="the-event-log-panel"></a>事件日志面板

使用 **“事件日志”** 面板按记录期间发生的顺序查看活动。

**“事件日志”** 面板仅显示录制的选定部分期间的活动。  请参阅 [选择录音的一部分](#select-a-portion-of-a-recording) ，了解如何选择部分。

:::image type="content" source="../media/evaluate-performance-performance-event-log.msft.png" alt-text="&quot;事件日志&quot;面板。" lightbox="../media/evaluate-performance-performance-event-log.msft.png":::

**“开始时间”** 列表示活动开始时与录制开始相对的点。  例如，上图中所选项目 `175.7 ms` 的开始时间意味着录制开始 175.7 毫秒后活动开始。

**“自我时间”** 列表示直接用于该活动的时间。

**“总时间”** 列表示直接用于该活动或任何子项中的时间。

单击 **"开始时间****"、**"开始时间"**或"总**时间"按该列对表进行排序。

使用 **“筛选”** 文本框按名称筛选活动。

使用 **“持续时间”** 菜单筛选出所有耗时少于 1 毫秒或 15 毫秒的活动。  默认情况下，**“持续时间”** 菜单设置为 **“全部”**，这意味着会显示所有活动。

禁用 **加载**、 **脚本**、 **渲染**或 **绘制** 复选框以筛选这些类别中的所有活动。

### <a name="view-gpu-activity"></a>查看 GPU 活动

在 **GPU** 部分查看 GPU 活动。

:::image type="content" source="../media/evaluate-performance-performance-gpu-zoomed.msft.png" alt-text="GPU 部分。" lightbox="../media/evaluate-performance-performance-gpu-zoomed.msft.png":::

### <a name="view-raster-activity"></a>查看光栅活动

在**光栅** 部分中查看光栅活动。

:::image type="content" source="../media/evaluate-performance-performance-raster.msft.png" alt-text="&quot;Raster&quot;部分。" lightbox="../media/evaluate-performance-performance-raster.msft.png":::

### <a name="view-interactions"></a>查看交互

使用 **“交互”** 部分查找和分析在录制期间发生的用户交互。

:::image type="content" source="../media/evaluate-performance-performance-interactions-animation.msft.png" alt-text="&quot;交互&quot;部分。" lightbox="../media/evaluate-performance-performance-interactions-animation.msft.png":::

交互底部的红线表示等待主线程所花费的时间。

单击交互，在摘要面板中查看 **有关它** 的信息。

### <a name="analyze-frames-per-second-fps"></a>分析每秒帧数 (FPS)

DevTools 提供了许多方法，以分析每秒帧数:

*  使用 [FPS 图](#the-fps-chart) 在录制期间获取 FPS 的概述。
*  使用 [帧部分](#the-frames-section) 查看特定帧所需的时间。
*  在页面运行时，使用 **FPS 计数** 来实时估计 FPS。  请参阅 [使用 FPS 指示器实时查看每秒帧数](#view-frames-per-second-in-realtime-with-the-fps-meter)。

#### <a name="the-fps-chart"></a>FPS 图表

**FPS** 图表提供整个录制期间的帧率概况。  一般来说，绿条越高，帧率越好。

**FPS** 图上方的红色条形是警告，说明帧率降得太低，很可能会损害用户的体验。

:::image type="content" source="../media/evaluate-performance-performance-fps-highlight.msft.png" alt-text="FPS 图表。" lightbox="../media/evaluate-performance-performance-fps-highlight.msft.png":::

#### <a name="the-frames-section"></a>”帧“ 部分

**“帧”** 部分会准确告知特定帧所需的时间。

将鼠标悬停在框架上，查看工具提示，详细了解它。

:::image type="content" source="../media/evaluate-performance-performance-frames-hover.msft.png" alt-text="将鼠标悬停在图框上。" lightbox="../media/evaluate-performance-performance-frames-hover.msft.png":::

在摘要面板中选择一个帧以查看有关 **帧** 详细信息。  DevTools 用蓝色勾勒出所选框架的轮廓。

:::image type="content" source="../media/evaluate-performance-performance-frames-summary.msft.png" alt-text="在摘要面板中查看帧。" lightbox="../media/evaluate-performance-performance-frames-summary.msft.png":::

### <a name="view-network-requests"></a>查看网络请求

展开 **“网络”** 部分，以查看录制期间发生的网络请求瀑布图。

:::image type="content" source="../media/evaluate-performance-performance-network.msft.png" alt-text="&quot;网络&quot;部分。" lightbox="../media/evaluate-performance-performance-network.msft.png":::

请求的颜色编码如下:
*  HTML: 蓝色
*  CSS: 紫色
*  JS: 黄色
*  图像: 绿色

单击请求以查看"摘要"选项卡中**有关它**的信息。 例如，在上图中，"摘要"**** 选项卡显示有关在"网络"部分选择的蓝色**请求详细信息。**

在请求的左上方有一个深蓝色的方块，意味着它是一个优先级较高的请求。  浅蓝色的方块表示优先级较低。  比如上图中，蓝色所选的请求是优先级较高的，而下方绿色的请求为优先级较低的。

在下面的第一个 `www.bing.com` 图中，对 的请求表示为左侧的一行、中间有深色部分的条形和浅色部分，以及右边的一条线。  下图显示了网络工具的"计时"选项卡中相同请求的相应**表示**形式。****

下面将说明这两种表示形式如何相互映射：

*  左行是到事件的 `Connection Start` 组的所有内容 (包括)。  换句话说，它是之前的所有内容，不包括 `Request Sent`。

*  条形图的浅部分为 `Request Sent` 和 `Waiting (TTFB)`。

*  条形图的深色部分为 `Content Download`。

*  右行基本上是等待主线程所花的时间。  This isn't represented in the **Timing** tab.

请求的线栏表示 `www.bing.com` 形式：

:::image type="content" source="../media/evaluate-performance-bing-performance-network.msft.png" alt-text="请求的线 www.bing.com 表示。" lightbox="../media/evaluate-performance-bing-performance-network.msft.png":::

**网络工具**：

:::image type="content" source="../media/evaluate-performance-bing-network-timing.msft.png" alt-text="网络工具。" lightbox="../media/evaluate-performance-bing-network-timing.msft.png":::

### <a name="view-memory-metrics"></a>查看内存指标

打开 **“内存”** 复选框以查看上次记录中的内存指标。

:::image type="content" source="../media/evaluate-performance-performance-memory-highlight.msft.png" alt-text="&quot;内存&quot;复选框。" lightbox="../media/evaluate-performance-performance-memory-highlight.msft.png":::

DevTools 在 **“摘要”** 面板上方显示新的 **“内存”** 图表。  **NET** 图表下方还有一个新的图表，称为 **“HEAP”**。  **“HEAP”** 图表提供的信息与 **“内存”** 表中的 **“JS Heap”** 行相同。

:::image type="content" source="../media/evaluate-performance-performance-memory-chart.msft.png" alt-text="内存指标。" lightbox="../media/evaluate-performance-performance-memory-chart.msft.png":::

图表上的彩色线条会映射到图表上方的彩色复选框上。  清除复选框以在图表中隐藏该类别。

图表只显示当前选择的记录区域。  例如，在上一个图中， **内存** 图表仅显示从 400 毫秒标记上下到 1750 毫秒标记左右的内存使用情况。

### <a name="view-the-duration-of-a-portion-of-a-recording"></a>查看部分录制的持续时间

当分析像 **网络** 或者 **主** 这样的部分时，有时你需要更精确地估计某些事件花了多长时间。  按住 `Shift`、单击并按住，然后向左或向右拖动以选择录制的一部分。  在所选内容底部，DevTools 显示该部分所话费的时间。

:::image type="content" source="../media/evaluate-performance-performance-main-duration.msft.png" alt-text="查看录制的一部分的持续时间。" lightbox="../media/evaluate-performance-performance-main-duration.msft.png":::

### <a name="view-a-screenshot"></a>查看屏幕截图

请参阅 [录制时捕获](#capture-screenshots-while-recording) 屏幕截图，了解如何打开屏幕截图。

将鼠标悬停在 **"概述** "上可查看该录制期间页面外观的屏幕截图。  **“概述”** 是包含 **CPU**、**FPS** 和 **NET** 图表的部分。

:::image type="content" source="../media/evaluate-performance-performance-screenshots-hover.msft.png" alt-text="查看屏幕截图。" lightbox="../media/evaluate-performance-performance-screenshots-hover.msft.png":::

您还可以通过在"框架"部分中选择框架 **来查看屏幕截图** 。  DevTools 在 **“摘要”** 面板中显示小版本的截图。

:::image type="content" source="../media/evaluate-performance-performance-summary-preview.msft.png" alt-text="在摘要面板中查看屏幕截图。" lightbox="../media/evaluate-performance-performance-summary-preview.msft.png":::

单击"摘要" **面板中的** 缩略图，放大屏幕截图。

:::image type="content" source="../media/evaluate-performance-performance-summary-preview-select.msft.png" alt-text="放大&quot;摘要&quot;面板中的屏幕截图。" lightbox="../media/evaluate-performance-performance-summary-preview-select.msft.png":::

### <a name="view-layers-information"></a>查看图层信息

查看框架的高级图层信息:

1. [启用高级画图检测工具](#turn-on-advanced-paint-instrumentation)。

1. 选择"框架" **部分中的** 框架。  DevTools 在"事件日志"选项卡旁的新"图层 **"选项卡中** 显示有关 **图层** 的信息。

:::image type="content" source="../media/evaluate-performance-layers-all.msft.png" alt-text="&quot;层&quot;窗格。" lightbox="../media/evaluate-performance-layers-all.msft.png":::

将鼠标悬停在图层上以在图表中突出显示它。

:::image type="content" source="../media/evaluate-performance-performance-frames-document-nav-bar-highlighted.msft.png" alt-text="突出显示图层。" lightbox="../media/evaluate-performance-performance-frames-document-nav-bar-highlighted.msft.png":::

若要移动图表:

*  选择 **"平移** (![平移模式](../media/pan-mode-icon.msft.png) "。) 沿 X 和 Y 轴移动。

*  选择**旋转模式**![ (旋转模式](../media/rotate-mode-icon.msft.png)。) 沿 Z 轴旋转。

*  选择 **"重置转换** (![重置转换](../media/reset-transform-icon.msft.png)) 将图表重置为原始位置。

### <a name="view-paint-profiler"></a>查看绘图探查器

查看有关绘图事件的高级信息:

1. [打开](#turn-on-advanced-paint-instrumentation)。

1. Select a **画图** event in the **Main** section.

"**画图配置文件器"** 面板：

:::image type="content" source="../media/evaluate-performance-paint-profiler.msft.png" alt-text="&quot;画图配置文件器&quot;面板。" lightbox="../media/evaluate-performance-paint-profiler.msft.png":::


<!-- ====================================================================== -->
## <a name="analyze-rendering-performance-with-the-rendering-tool"></a>使用 "渲染" 工具分析渲染性能

使用 **“渲染”** 面板的功能来帮助可视化页面的渲染性能。

若要打开 **“渲染”** 工具:

1. [打开“命令”菜单](../command-menu/index.md#open-the-command-menu)。

1. 开始键入 `Rendering` 并选择 `Show Rendering`。  DevTools 会在 DevTools 窗口的底部显示**渲染**工具。

:::image type="content" source="../media/evaluate-performance-console-drawer-rendering.msft.png" alt-text="呈现工具。" lightbox="../media/evaluate-performance-console-drawer-rendering.msft.png":::

### <a name="view-frames-per-second-in-realtime-with-the-fps-meter"></a>使用 FPS 计数实时查看每秒帧数。

**FPS 计数** 是出现在视区右上角的叠加。  它提供了页面运行时 FPS 的实时估计。  若要打开 **FPS 计数**:

1. 打开 **渲染** 工具。  [使用 “渲染” 工具分析渲染性能](#analyze-rendering-performance-with-the-rendering-tool)。

1. 选中 **"FPS 指示器"** 复选框。

:::image type="content" source="../media/evaluate-performance-jank-console-rendering-frame-rate.msft.png" alt-text="FPS 指示器。" lightbox="../media/evaluate-performance-jank-console-rendering-frame-rate.msft.png":::

### <a name="view-painting-events-in-realtime-with-paint-flashing"></a>使用“画图闪烁”实时查看画图事件

使用“画图闪烁”可实时查看页面上的所有画图事件。  每当重新绘制页面的一部分时，DevTools 就会用绿色勾勒出该部分的轮廓。

若要打开画图闪烁：

1. 打开 **渲染** 工具。  请参阅 [使用呈现工具分析呈现性能](#analyze-rendering-performance-with-the-rendering-tool)。

1. 选中"**画图闪烁"** 复选框。

   :::image type="content" source="../media/evaluate-performance-jank-console-rendering-paint-flashing.msft.png" alt-text="画图闪烁。" lightbox="../media/evaluate-performance-jank-console-rendering-paint-flashing.msft.png":::

### <a name="view-an-overlay-of-layers-with-layer-borders"></a>使用 “图层边框” 查看图层的叠加

使用 **“图层边框”** 可查看页面顶部的图层边框和图块的叠加。

若要打开图层边框，请进行设置：

1. 打开 **渲染** 工具。  请参阅 [使用呈现工具分析呈现性能](#analyze-rendering-performance-with-the-rendering-tool)。

1. 选中" **图层边框"** 复选框。

:::image type="content" source="../media/evaluate-performance-devtools-console-rendering-layer-borders.msft.png" alt-text="图层边框。" lightbox="../media/evaluate-performance-devtools-console-rendering-layer-borders.msft.png":::

有关颜色编码 [的说明，请参阅 debug_colors.cc](https://cs.chromium.org/chromium/src/cc/debug/debug_colors.cc) 中的注释。

### <a name="find-scroll-performance-issues-in-realtime"></a>实时查找滚动性能问题

使用滚动性能问题来识别页面中具有与滚动相关的事件监听器的元素，这些元素可能会损害页面的性能。  DevTools 以青绿色概述了可能存在问题的元素。

若要查看滚动性能问题，请执行：

1. 打开 **渲染** 工具。  请参阅 [使用呈现工具分析呈现性能](#analyze-rendering-performance-with-the-rendering-tool)。

1. 选中" **滚动性能问题"** 复选框。

:::image type="content" source="../media/evaluate-performance-bing-console-drawer-rendering-scrolling-performance-issues.msft.png" alt-text="滚动性能问题指示非层视口约束的对象可能会损害滚动性能。" lightbox="../media/evaluate-performance-bing-console-drawer-rendering-scrolling-performance-issues.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
