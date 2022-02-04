---
title: 分析运行时性能入门
description: 介绍如何在 DevTools 中评估运行时Microsoft Edge教程。
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
# <a name="get-started-analyzing-runtime-performance"></a>分析运行时性能入门

_运行时_ 性能是页面运行时（而不是加载）运行时的执行方式。  以下教程指导你如何使用 DevTools **性能** 工具分析运行时性能。

在 **RAIL** 模型方面，你在本教程中学习的技能对于分析页面的响应、动画和空闲阶段很有用。

另请参阅 [使用 Lighthouse 优化网站速度](../speed/get-started.md)。

<!--todo: add rail link when section is ready -->


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

在下面的教程中，你将在"反应动画"演示页面上打开 DevTools，并使用性能工具**** 在页面上查找性能瓶颈。

1. 在 **InPrivate 模式**中打开 Microsoft Edge。  InPrivate 模式可确保 Microsoft Edge 以干净的状态运行。  例如，如果安装了大量扩展，则扩展可能会在性能测量中产生噪音。

   <!--TODO: replace section when updated for Chromium-based Edge  -->

1. 在 InPrivate 窗口中加载以下"反应动画"演示页面。  你将配置文件此页面，其中显示数量可变的图标向上和向下移动。

   ```https
   https://microsoftedge.github.io/Demos/devtools-performance-get-started/
   ```

    <!-- You can view the source files for the "Sluggish Animation" demo page at the [MicrosoftEdge/Demos > devtools-performance-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-performance-get-started) repo folder. -->

1. 按 `Control`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 打开 DevTools。

   :::image type="content" source="../media/evaluate-performance-get-started-side-by-side.msft.png" alt-text="左侧为演示，右侧为 DevTools" lightbox="../media/evaluate-performance-get-started-side-by-side.msft.png":::

对于下面的其余屏幕截图，DevTools 将取消停靠到单独的[](../customize/placement.md)窗口，以更好地关注内容。


### <a name="simulate-a-mobile-cpu"></a>模拟移动 CPU

与台式机和笔记本电脑相比，移动设备的 CPU 功率更小。  每当你分析页面时，都可使用 CPU 节流来模拟页面在移动设备上的表现。

1. 在 DevTools 中，打开 **性能** 工具。

1. 选中"屏幕截图"旁边的 **复选框**。

1. 单击 **"捕获设置 (**![捕获设置。) ](../media/capture-settings-icon.msft.png)。  DevTools 显示了有关如何捕获效果指标的设置。

1. 对于 "**CPU**"，选择 **4x 减速**。  DevTools 将 CPU 限制为比平时慢 4 倍。

   :::image type="content" source="../media/evaluate-performance-performance-capture-settings.msft.png" alt-text="CPU 限制。" lightbox="../media/evaluate-performance-performance-capture-settings.msft.png":::

   在测试其他页面时；如果想确保每个页面在低端移动设备上都能很好的运行，将CPU限制设置为**6倍减速**。  演示在速度慢 6 倍时运行不顺利，因此它仅使用 4 倍减速进行说明。


### <a name="set-up-the-demo"></a>设置演示

很难创建一个运行时性能演示，该演示对网站的所有读者都一致。  以下部分允许你自定义演示，以确保你的体验与屏幕截图和说明相对一致，而不管您的特定设置如何。

1. 单击" **添加 10"** 按钮，直到蓝色图标移动明显慢于以前。  在高端计算机上，你可以单击它大约 20 次。

1. 单击 "**优化**"。  蓝色图标移动速度更快、更平稳。

1. 为了更好地显示优化版本和未优化版本之间的差异，请多次单击"减去 **10** "按钮，然后重试。  如果添加的蓝色图标过多，您可能会占用过多的 CPU，然后可能不会发现这两个版本的结果主要不同。

1. 单击 "**取消优化**"。  蓝色图标移动速度变慢，而且又更加迟钝。


### <a name="record-runtime-performance"></a>记录运行时性能

运行优化版本的页面时，蓝色图标会移动得更快。  为什么？  两种版本都应该在相同的时间内将图标移动相同的空间。  在性能工具 **中** 录制，了解如何检测未优化版本中的性能瓶颈。

1. 在 DevTools 中 **，单击"** 记录 (![记录](../media/record-icon.msft.png) "。) 。  页面运行时，DevTools 将捕获效果指标。

   :::image type="content" source="../media/evaluate-performance-performance-profiling.msft.png" alt-text="配置文件页面。" lightbox="../media/evaluate-performance-performance-profiling.msft.png":::

1. 稍等几秒钟。

1. 单击**停止**。  DevTools 停止录制，处理数据，然后在性能工具 **中显示** 结果。

   :::image type="content" source="../media/evaluate-performance-performance-capture-results.msft.png" alt-text="配置文件的结果。" lightbox="../media/evaluate-performance-performance-capture-results.msft.png":::

这是一个难以承受的数据量，但很快就会更合理。


<!-- ====================================================================== -->
## <a name="analyze-the-results"></a>分析结果

记录页面性能后，您可以评估页面的性能并找出任何性能问题的原因。


### <a name="analyze-frames-per-second"></a>分析每秒帧数

测量任何动画性能的主要指标是每秒帧数 (FPS) 。  当动画以 60 FPS运行时，用户会觉得很享受。

1. 查看 **FPS** 图表，如下所示。  每当红色条显示在 **FPS** 上方时，这意味着帧速率下降得过低，可能损害用户体验。  通常，绿色条越高，FPS 越高。

   :::image type="content" source="../media/evaluate-performance-performance-fps-chart.msft.png" alt-text="FPS 图表。" lightbox="../media/evaluate-performance-performance-fps-chart.msft.png":::

1. 在 **FPS** 图表下方，显示 **CPU** 图表。  CPU **图表中的颜色对应于**"性能"工具底部的"摘要"**** 面板**中**的颜色。  **CPU** 图表充满颜色意味着在录制过程中 CPU 已达到极限。  只要 CPU 长时间达到最大值，即表示你应该找到减少工作的方法。

   :::image type="content" source="../media/evaluate-performance-performance-cpu-chart.msft.png" alt-text="CPU 图表和摘要面板。" lightbox="../media/evaluate-performance-performance-cpu-chart.msft.png":::

1. 将鼠标悬停在 **FPS**、 **CPU** 或 **NET** 图表上。  DevTools 将显示该时间点处的页面截图。  左右移动鼠标以重播录音。  操作称为 _推移_，它可用于手动分析动画进度。

   :::image type="content" source="../media/evaluate-performance-performance-screenshot-hover.msft.png" alt-text="查看 2500 毫秒记录标记周围的页面屏幕截图。" lightbox="../media/evaluate-performance-performance-screenshot-hover.msft.png":::

1. 在“**框架**”部分，将鼠标悬停在其中一个绿色方块上。  DevTools 将显示该特定帧的 FPS。  每帧可能远低于 60 FPS的目标。

   :::image type="content" source="../media/evaluate-performance-performance-frame-hover.msft.png" alt-text="将鼠标悬停在图框上。" lightbox="../media/evaluate-performance-performance-frame-hover.msft.png":::

显示指示网页运行不佳。  在真实方案中，页面是否运行良好可能不够明确，因此，使用所有工具进行测量就很方便。


#### <a name="bonus-open-the-fps-meter"></a>附赠：打开 FPS 计数

另一个非常方便的工具是 FPS 计数，可在页面运行时提供对 FPS 的实时估计。

1. 按 `Control``P``Shift`++ (Windows、Linux) 或 `Command``Shift`++`P` (macOS) 打开命令**菜单**。

1. 开始在"命令 `Rendering` 菜单" **中键入内容，** 然后单击" **显示呈现"**。

1. 在呈现**工具** 中，打开 **FPS 指示器**。  新的叠加层将显示在视线的右上角。

   :::image type="content" source="../media/evaluate-performance-fps-meter-overlay.msft.png" alt-text="FPS 指示器。" lightbox="../media/evaluate-performance-fps-meter-overlay.msft.png":::

1. 关闭 **FPS 指示器，** 然后按 `Escape` 以关闭 **呈现** 工具。  本教程中未 **使用 FPS** 指示器。


### <a name="find-the-bottleneck"></a>查找瓶颈

测量并验证动画运行不佳后，下一步是回答"为什么？"这一问题。

1. 未选择任何事件时，“**摘要**”面板将显示活动的细目。  页面大部分时间都在渲染。  由于性能是减少工作量的艺术，因此你的目标是减少花费在进行绘制工作上的时间。

   :::image type="content" source="../media/evaluate-performance-performance-summary-tab.msft.png" alt-text="摘要面板。" lightbox="../media/evaluate-performance-performance-summary-tab.msft.png":::

1. 展开**重点**部分。  DevTools 将显示一段时间内主线程上活动的帧图表。  x 轴表示一段时间内的记录。  每个条形表示一个事件。  宽条表示该事件花费了更长的时间。  Y 轴表示调用堆叠。  当事件堆叠在一起时，这意味着上面的事件导致了下面的事件。

   :::image type="content" source="../media/evaluate-performance-performance-main.msft.png" alt-text="&quot;主&quot;部分。" lightbox="../media/evaluate-performance-performance-main.msft.png":::

1. 录制中有很多数据。  To Zoom into a single event， click， hold， and drag your cursor over the **Overview**， which is the section that includes the **FPS**， **CPU**， and **NET** charts.  " **主** 节"和" **摘要** "面板仅显示记录的选定部分的信息。

   :::image type="content" source="../media/evaluate-performance-performance-main-zoomed.msft.png" alt-text="放大事件。" lightbox="../media/evaluate-performance-performance-main-zoomed.msft.png":::

   另一种缩放方式是：将焦点放在 **"主**"部分，单击背景或事件，然后按、`W``A`、、`S`或 `D`。

1. 重点关注**动画帧触发**事件右上角的红色三角形。  每当显示红色三角形时，都会显示一条警告，指出可能有与事件相关的问题。

   每当运行 [requestAnimationFrame()](https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame) 时，将发生 **动画帧触发**事件。

1. 单击**动画帧触发**事件。  “**摘要**”面板现在将显示有关该事件的信息。  请注意“**显示**”链接。  单击它后，DevTools 将突出显示启动 **动画帧触发事件** 的事件。  另外，请关注**app.js:95**链接。  单击它后，将显示源代码中的相关行。

   :::image type="content" source="../media/evaluate-performance-performance-animation-frame-fired.msft.png" alt-text="有关动画帧触发事件详细信息。" lightbox="../media/evaluate-performance-performance-animation-frame-fired.msft.png":::

   单击事件后，使用箭头键选择它旁边的事件。

1. 在 **app.update** 事件下，有一组紫色事件。  如果每个紫色事件都比较宽，看起来每个事件上可能都有个红色三角形。

1. 单击紫色的 **Layout 事件** 之一。  DevTools 在**摘要**面板中提供了有关事件详细信息。  实际上，存在一条有关强制重排的 (另一个单词的 _布局) _ 。

1. 在摘要 **面板中** ，单击布局强制下的app.js ** ：71** **链接**。  DevTools 将转到强制布局的代码行。

   :::image type="content" source="../media/evaluate-performance-sources-app-update.msft.png" alt-text="导致强制布局的代码行。" lightbox="../media/evaluate-performance-sources-app-update.msft.png":::

   这段代码的问题在于，在每个动画帧中，它都会改变每个图标的样式，然后查询每个图标在页面上的位置。  由于样式发生更改，浏览器不知道每个图标位置是否更改，因此必须重新布局图标才能计算新位置。
   <!--
   > To learn more, see [Avoid forced synchronous layouts](https://developers.google.com/web/fundamentals/performance/rendering/avoid-large-complex-layouts-and-layout-thrashing#avoid_forced_synchronous_layouts).
   -->

这有许多需要学习。  现在，已经为分析运行时性能的基本工作流程打下了坚实的基础。  太棒了。


### <a name="bonus-analyze-the-optimized-version"></a>附赠：分析优化的版本

使用刚学到的工作流和工具，在演示中单击****"优化"以打开优化的代码，执行另一个性能记录，然后分析结果。  从改进的帧速率到“**主**”节中绘制图表事件的减少，应用的优化版本执行的工作要少得多，从而产生更好的性能。

即使优化的版本也不是那么好， `top` 因为它可以操作每个图标的属性。  更好的方法是保留仅影响合成的属性。
<!--  > For more information, see [Use transform and opacity changes for animations](https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count#use_transform_and_opacity_changes_for_animations). todo: add rendering section when available -->


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

<!--The foundation for understanding performance is the RAIL model.  The RAIL model teaches you the performance metrics that are most important to your users.
To learn more, see [Measure Performance With The RAIL Model](https://developers.google.com/web/fundamentals/performance/rail). -->

为了更加熟悉**性能**工具，需要多加练习。  试着对页面进行剖析并分析结果。  如果你**** 对结果`Alt`+`I`+`Shift`有任何疑问，请使用"发送反馈"图标、按 (Windows、Linux) `Option``Shift`++`I` 或 (macOS) 或推文 [DevTools 团队](https://twitter.com/intent/tweet?text=@EdgeDevTools)。  如果可能，请包括屏幕截图或指向可重现页面的链接。

:::image type="content" source="../media/evaluate-performance-feedback-icon.msft.png" alt-text="Microsoft Edge 开发人员工具中的**反馈**图标" lightbox="../media/evaluate-performance-feedback-icon.msft.png":::

<!-- To really become an expert in runtime performance, you must learn how the browser translates HTML, CSS, and JS into pixels on a screen.  The best place to start is the [Rendering Performance Overview](https://developers.google.com/web/fundamentals/performance/rendering).  [The Anatomy Of A Frame](https://aerotwist.com/blog/the-anatomy-of-a-frame/) dives into even more detail. -->

最后，可通过多种方法来改善运行时性能。  本文着重介绍一个特定的动画瓶颈，可让你集中浏览 **Performance** 工具，但它只是你可能遇到的许多瓶颈之一。  <!--  The rest of the Rendering Performance series has a lot of good tips for improving various aspects of runtime performance, such as:  -->

<!--
* [Optimizing JS Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)
* [Reduce The Scope And Complexity Of Style Calculations](https://developers.google.com/web/fundamentals/performance/rendering/reduce-the-scope-and-complexity-of-style-calculations)
* [Avoid Large, Complex Layouts And Layout Thrashing](/web/fundamentals/performance/rendering/avoid-large-complex-layouts-and-layout-thrashing)
* [Simplify Paint Complexity And Reduce Paint Areas](/web/fundamentals/performance/rendering/simplify-paint-complexity-and-reduce-paint-areas)
* [Stick To Compositor-Only Properties And Manage Layer Count](/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count)
* [Debounce Your Input Handlers](/web/fundamentals/performance/rendering/debounce-your-input-handlers)
-->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
