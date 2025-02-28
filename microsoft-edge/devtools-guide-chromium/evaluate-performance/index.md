---
title: 分析运行时性能入门
description: 有关如何在 Microsoft Edge DevTools 中评估运行时性能的教程。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/10/2022
ms.openlocfilehash: ba9d632afed1abff397023522c3419ac65a45fce
ms.sourcegitcommit: 81c0b3c87d152858f76a5f1b1cf8a742fd6b69e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2022
ms.locfileid: "12813554"
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

_运行时性能_ 是页面在运行时的表现，而不是加载。  以下教程介绍如何使用 DevTools **性能** 工具分析运行时性能。

在 **RAIL** 模型方面，你在本教程中学习的技能对于分析页面的响应、动画和空闲阶段很有用。

另请参阅 [使用 Lighthouse 优化网站速度](../speed/get-started.md)。

<!--todo: add rail link when section is ready -->


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

在以下教程中，在“缓慢动画”演示页上打开 DevTools，并使用 **性能** 工具在页面上查找性能瓶颈。

1. 在 **InPrivate 模式**中打开 Microsoft Edge。  InPrivate 模式可确保 Microsoft Edge 以干净的状态运行。  例如，如果安装了大量扩展，则扩展可能会在性能测量中产生噪音。

   <!--TODO: replace section when updated for Chromium-based Edge  -->

1. 在 InPrivate 窗口中加载以下“缓慢动画”演示页。  你将分析此页面，其中显示上下移动的图标数量可变。

   ```https
   https://microsoftedge.github.io/Demos/devtools-performance-get-started/
   ```

    <!-- You can view the source files for the "Sluggish Animation" demo page at the [MicrosoftEdge/Demos > devtools-performance-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-performance-get-started) repo folder. -->

1. 按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 打开 DevTools。

   ![左侧为演示，右侧为 DevTools](../media/evaluate-performance-get-started-side-by-side.msft.png)

对于下面的其余屏幕截图，DevTools 将 [取消连接到单独的窗口](../customize/placement.md)，以便更好地关注内容。


### <a name="simulate-a-mobile-cpu"></a>模拟移动 CPU

与台式机和笔记本电脑相比，移动设备的 CPU 功率更小。  每当你分析页面时，都可使用 CPU 节流来模拟页面在移动设备上的表现。

1. 在 DevTools 中，打开 **“性能** ”工具。

1. 选择 **屏幕截图旁边的**复选框。

1. 单击 **“捕获设置** (![捕获设置。](../media/capture-settings-icon.msft.png)) 。  DevTools 显示了有关如何捕获效果指标的设置。

1. 对于 "**CPU**"，选择 **4x 减速**。  DevTools 将 CPU 限制为比平时慢 4 倍。

   ![CPU 限制。](../media/evaluate-performance-performance-capture-settings.msft.png)

   在测试其他页面时；如果想确保每个页面在低端移动设备上都能很好的运行，将CPU限制设置为**6倍减速**。  演示在 6 倍减速时效果不好，因此它只使用 4 倍减速进行说明。


### <a name="set-up-the-demo"></a>设置演示

很难创建一个运行时性能演示，该演示适用于网站的所有读者。  以下部分允许你自定义演示，以确保你的体验与屏幕截图和说明相对一致，而不考虑你的特定设置。

1. 单击 **“添加 10”** 按钮，直到蓝色图标的移动速度明显比以前慢。  在高端计算机上，可以单击它大约 20 次。

1. 单击 "**优化**"。  蓝色图标移动速度更快、更平稳。

1. 若要更好地显示优化版本和未优化版本之间的差异，请单击“ **减去 10”** 按钮几次，然后重试。  如果添加了太多的蓝色图标，则可能会最大化 CPU，然后可能无法观察到这两个版本的结果存在重大差异。

1. 单击 "**取消优化**"。  蓝色图标移动速度变慢，而且又更加迟钝。


### <a name="record-runtime-performance"></a>记录运行时性能

运行优化版本的页面时，蓝色图标会移动得更快。  为什么？  两种版本都应该在相同的时间内将图标移动相同的空间。  在 **性能** 工具中进行录制，了解如何检测未优化版本中的性能瓶颈。

1. 在 DevTools 中，单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  页面运行时，DevTools 将捕获效果指标。

   ![分析页面。](../media/evaluate-performance-performance-profiling.msft.png)

1. 稍等几秒钟。

1. 单击**停止**。  DevTools 停止录制、处理数据，然后在 **“性能** ”工具中显示结果。

   ![配置文件的结果。](../media/evaluate-performance-performance-capture-results.msft.png)

这是大量的数据，但很快就会更有意义。


<!-- ====================================================================== -->
## <a name="analyze-the-results"></a>分析结果

录制页面的性能后，可以评估页面的性能并查找任何性能问题的原因。

1. **CPU** 图表沿顶部显示。  **CPU** 图表中的颜色对应于 **“性能**”工具底部**摘要**面板中的颜色。  **CPU** 图表显示这些区域占了很大的区域，这意味着在录制过程中 CPU 已用完。  每当 CPU 长时间用完时，这一指示你应找到减少工作的方法。

   ![CPU 图表和摘要面板。](../media/evaluate-performance-performance-cpu-chart.msft.png)

1. 将鼠标悬停在 **CPU** 或 **NET** 图表上。  DevTools 将显示该时间点处的页面截图。  左右移动鼠标以重播录音。  该操作称为 _“擦洗_”，可用于手动分析性能录制的进度。

   ![将鼠标悬停在框架上。](../media/evaluate-performance-performance-frame-hover.msft.png)

显示器指示网页性能不佳。  在实际情况下，页面是否运行良好可能不太清楚，因此，让所有用于进行度量的工具都派上用场。


#### <a name="bonus-open-the-fps-meter"></a>附赠：打开 FPS 计数

另一个非常方便的工具是 FPS 计数，可在页面运行时提供对 FPS 的实时估计。

1. 按“`Ctrl`+`Shift`+`P`”(Windows、Linux)或“`Command`+`Shift`+`P`”(macOS)以打开“**命令菜单**”。

1. 开始在**命令菜单**中键`Rendering`入，然后单击 **“显示呈现**”。

1. 在呈现**工具** 中，打开 **FPS 指示器**。  新的叠加层将显示在视线的右上角。

   ![FPS 计量。](../media/evaluate-performance-fps-meter-overlay.msft.png)

1. 关闭 **FPS 计量** 并按 `Escape` 下以关闭 **呈现** 工具。  本教程中未使用 **FPS 计量** 。


### <a name="find-the-bottleneck"></a>查找瓶颈

测量并验证动画性能不佳后，下一步是回答“为什么？”问题。

1. 如果未选择任何事件， **摘要** 面板将显示活动的细目。  页面大部分时间都在渲染。  由于性能是减少工作量的艺术，因此你的目标是减少花费在进行绘制工作上的时间。

   ![摘要面板。](../media/evaluate-performance-performance-summary-tab.msft.png)

1. 展开**重点**部分。  DevTools 将显示一段时间内主线程上活动的帧图表。  x 轴表示一段时间内的记录。  每个条形表示一个事件。  宽条表示该事件花费了更长的时间。  Y 轴表示调用堆叠。  当事件堆叠在一起时，这意味着上面的事件导致了下面的事件。

   ![Main 部分。](../media/evaluate-performance-performance-main.msft.png)

1. 录制中有很多数据。  若要缩放到单个事件，请单击、按住光标并拖动光标， **该概述**是包含 **FPS**、 **CPU** 和 **NET** 图表的部分。  “ **主** ”部分和 **“摘要”** 面板仅显示所选录制部分的信息。

   ![放大事件。](../media/evaluate-performance-performance-main-zoomed.msft.png)

   缩放的另一种方法是将焦点放在 **Main** 部分，单击背景或事件，然后按`W`下，`A``S`或`D`。

1. 重点关注**动画帧触发**事件右上角的红色三角形。  每当显示红色三角形时，都会显示一个警告，指出可能存在与事件相关的问题。

   每当运行 [requestAnimationFrame()](https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame) 时，将发生 **动画帧触发**事件。

1. 单击**动画帧触发**事件。  “**摘要**”面板现在将显示有关该事件的信息。  请注意“**显示**”链接。  单击后，DevTools 将突出显示启动 **动画帧触发** 事件的事件。  另外，请关注**app.js:95**链接。  单击后，将显示源代码中的相关行。

   ![有关动画帧触发事件的详细信息。](../media/evaluate-performance-performance-animation-frame-fired.msft.png)

   单击事件后，使用箭头键选择旁边的事件。

1. 在 **app.update** 事件下，有一堆紫色事件。  如果每个紫色事件都比较宽，看起来每个事件上可能都有个红色三角形。

1. 单击其中一个紫色 **布局** 事件。  DevTools 在**摘要**面板中提供了有关事件详细信息。  事实上，对于 _布局_) ，有关于强制重新流 (另一个词的警告。

1. 在 **“摘要**”面板中，单击“**强制布局**”下的 **“app.js：71**”链接。  DevTools 将转到强制布局的代码行。

   ![导致强制布局的代码行。](../media/evaluate-performance-sources-app-update.msft.png)

   这段代码的问题在于，在每个动画帧中，它都会改变每个图标的样式，然后查询每个图标在页面上的位置。  由于样式已更改，因此浏览器不知道每个图标位置是否已更改，因此必须重新布局图标才能计算新位置。
   <!--
   > To learn more, see [Avoid forced synchronous layouts](https://web.dev/avoid-large-complex-layouts-and-layout-thrashing/#avoid-forced-synchronous-layouts).
   -->

这有许多需要学习。  现在，已经为分析运行时性能的基本工作流程打下了坚实的基础。  太棒了。


### <a name="bonus-analyze-the-optimized-version"></a>附赠：分析优化的版本

使用刚刚学习的工作流和工具，单击演示中的 **“优化** ”以打开优化的代码，进行另一个性能录制，然后分析结果。  从改进的帧速率到“**主**”节中绘制图表事件的减少，应用的优化版本执行的工作要少得多，从而产生更好的性能。

即使是优化的版本也不是很好，因为它会操作 `top` 每个图标的属性。  更好的方法是保留仅影响合成的属性。
<!--  > For more information, see [Use transform and opacity changes for animations](https://web.dev/stick-to-compositor-only-properties-and-manage-layer-count/#use-transform-and-opacity-changes-for-animations). todo: add rendering section when available -->


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

<!--The foundation for understanding performance is the RAIL model.  The RAIL model teaches you the performance metrics that are most important to your users.
To learn more, see [Measure Performance With The RAIL Model](https://web.dev/rail/). -->

为了更加熟悉**性能**工具，需要多加练习。  试着对页面进行剖析并分析结果。  如果对结果有任何疑问，请使用 **“发送反馈**”图标，按 `Alt``I``Shift`++ (Windows、Linux) 或`Option``Shift`++`I` (macOS) ，或[在 DevTools 团队中发布推文](https://twitter.com/intent/tweet?text=@EdgeDevTools)。  如果可能，请包括屏幕截图或指向可重现页面的链接。

![Microsoft Edge 开发人员工具中的**反馈**图标](../media/evaluate-performance-feedback-icon.msft.png)

<!-- To really become an expert in runtime performance, you must learn how the browser translates HTML, CSS, and JS into pixels on a screen.  The best place to start is the [Rendering Performance](https://web.dev/rendering-performance/).  [The Anatomy Of A Frame](https://aerotwist.com/blog/the-anatomy-of-a-frame/) dives into even more detail. -->

最后，可通过多种方法来改善运行时性能。  本文重点介绍一个特定的动画瓶颈，让你重点了解 **性能** 工具，但这只是你可能会遇到的许多瓶颈之一。  <!--  The rest of the Rendering Performance series has a lot of good tips for improving various aspects of runtime performance, such as:  -->

<!--
* [Optimize JavaScript execution](https://web.dev/optimize-javascript-execution/)
* [Reduce the scope and complexity of style calculations](https://web.dev/reduce-the-scope-and-complexity-of-style-calculations/)
* [Avoid large, complex layouts and layout thrashing](https://web.dev/avoid-large-complex-layouts-and-layout-thrashing/)
* [Simplify paint complexity and reduce paint areas](https://web.dev/simplify-paint-complexity-and-reduce-paint-areas/)
* [Stick to Compositor-Only Properties and Manage Layer Count](https://web.dev/stick-to-compositor-only-properties-and-manage-layer-count/)
* [Debounce your input handlers](https://web.dev/debounce-your-input-handlers/)
-->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。 原始页面位于[此处](https://developer.chrome.com/docs/devtools/evaluate-performance/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
