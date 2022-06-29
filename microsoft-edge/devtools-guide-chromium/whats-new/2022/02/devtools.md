---
title: DevTools (Microsoft Edge 98) 中的新增功能
description: 2021 年回顾博客文章。  使用 Internet Explorer 驱动程序自动执行 IE 模式。  模拟强制颜色模式。  性能工具事件日志中活动图标的工具提示。  内存工具中的浅层大小现在显示为十进制值。  现在可以调整网络工具的搜索文本框的大小。  以及更多。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/02/2022
ms.openlocfilehash: 18c81d58ee8ae007e9f95972be3d591c1ea29901
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631625"
---
# <a name="whats-new-in-devtools-microsoft-edge-98"></a>DevTools (Microsoft Edge 98) 中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="catch-up-on-the-latest-and-greatest-features-in-microsoft-edge"></a>了解 Microsoft Edge 中最新和最强大的功能


<!-- Title: Year-in-review: Microsoft Edge for developers -->
<!-- Subtitle: Catch up on the latest in developer tooling from Microsoft Edge. -->

2021年，面向 Microsoft Edge 的开发人员工具实现了巨大的飞跃。  Visual Studio Code、DevTools 和浏览器现在提供多个集成工作流，用于 JavaScript 调试、镜像 CSS 更改以及从浏览器进行屏幕广播。  在焦点模式、对 Visual Studio Code 主题的支持和进一步的自定义选项之间，Microsoft Edge 团队正在努力使 DevTools 更易于使用。

在年度回顾博客文章中了解所有这些资讯等，[回顾 2021 年面向开发人员的 Microsoft Edge](https://blogs.windows.com/msedgedev/2022/01/19/looking-back-at-microsoft-edge-for-developers-in-2021/)。

[![S博客文章的屏幕截图：回顾 2021 年面向开发人员的Microsoft Edge。](../../media/2022/02/blog-post-edge-devs-2021.png)](https://blogs.windows.com/msedgedev/2022/01/19/looking-back-at-microsoft-edge-for-developers-in-2021/)


<!-- ====================================================================== -->
## <a name="automate-ie-mode-with-internet-explorer-driver"></a>使用 Internet Explorer 驱动程序自动执行 IE 模式

<!-- Title: New support for automating IE mode -->
<!-- Subtitle: Test your legacy websites and apps by automating IE mode with Internet Explorer Driver. -->

从 2022 年 6 月 15 日开始，某些版本的 Windows 10 将不再支持 Internet Explorer 11。  IE 模式是 Microsoft Edge 的一项功能，适用于仍需要 Internet Explorer 11 以与旧版网站或应用兼容的组织。  若要支持测试这些旧版网站和应用，现在可以使用 Selenium 4 和 Internet Explorer 驱动程序自动执行 IE 模式。

另请参阅：
* [使用 Internet Explorer 驱动程序在 Microsoft Edge 中自动执行 IE 模式](../../../../webdriver-chromium/ie-mode.md)


<!-- ====================================================================== -->
## <a name="emulate-forced-colors-mode"></a>模拟强制颜色模式

<!-- Title: Emulation of forced colors in the Rendering tool -->
<!-- Subtitle: You can now do a spot check of what your product will look like on a device running in forced-colors mode, without having to change your operating system settings. -->

除了模拟当前网页的深色、浅色和打印模式外，现在还可以查看已启用强制颜色模式的用户的网页外观。  强制颜色模式是操作系统的一项辅助功能。  它强制将网页上的颜色缩减为有限的调色板，例如 Windows 高对比度模式。  通过模拟强制颜色模式，无需更改自己的系统设置即可执行抽查。

若要启用强制颜色仿真，请在 DevTools 中打开“**绘制**”工具，然后在“**模拟 CSS 媒体功能强制颜色**”下拉列表中，选择“**强制颜色：活动**”。

在未启用强制颜色仿真的情况下，以下网页具有多种不同背景色的文本颜色：

![在绘制工具中未启用强制颜色仿真的网页。](../../media/2022/02/emulate-forced-colors-not-applied.png)

在“**绘制**”工具中启用强制颜色仿真后，网页将更改为白色背景的黑色文本：

![在绘制工具中启用强制颜色仿真的网页。  文本更改为白色背景的黑色文本。](../../media/2022/02/emulate-forced-colors-applied.png)

另请参阅：
* [呈现工具，查看具有不同显示选项或视觉缺陷的网页外观](../../../rendering-tools/rendering-tool.md)


<!-- ====================================================================== -->
## <a name="activity-icons-in-the-event-log-of-the-performance-tool-now-have-tooltips"></a>性能工具的事件日志中的活动图标现在具有工具提示

<!-- Title: Analyze runtime performance better with the Event Log in the Performance tool -->
<!-- Subtitle: Activity icons in the Event Log now have tooltips indicating the type of activity for each event, such as Scripting, Rendering, or Painting. -->

在早期版本的 Microsoft Edge 中，“**性能**”工具中的“**事件日志**”选项卡显示表示每个事件的活动类型的颜色编码图标。  但是，事件日志不会显示有关每种颜色表示的活动类型的信息。  在 Microsoft Edge 98 中，工具提示已添加到“**事件日志**”选项卡中的活动事件，指示每个事件的**脚本**、**绘制**、**绘画**、**系统**和**空闲时间**。

![在事件日志中，所选活动事件有一个表示“绘画”事件的绿色框，现在工具提示将显式显示“绘画”。](../../media/2022/02/activity-event-tooltip.png)

另请参阅：
* [记录运行时性能](../../../evaluate-performance/reference.md#record-runtime-performance)


<!-- ====================================================================== -->
## <a name="shallow-sizes-in-the-memory-tool-are-now-represented-as-decimal-values"></a>内存工具中的浅层大小现在表示为十进制值

<!-- Title: Better understand shallow sizes in the Memory tool -->
<!-- Subtitle: The Memory tool has been updated to report shallow size in decimal values as a percentage of the heap. -->

在早期版本的 Microsoft Edge 中，内存工具中堆快照中的浅层大小通常报告为 0%，因为相对于堆的总大小而言，浅层大小非常小。  在 Microsoft Edge 98 中，如果浅层大小在堆的 0% 和 1% 之间，则浅层大小现在报告为十进制值。

![在堆快照中，堆的 0% 和 1% 之间的浅层大小列值现在显示为带有一位或两位小数的十进制值。](../../media/2022/02/shallow-size-decimal-values.png)

另请参阅：
* [记录堆快照](../../../memory-problems/heap-snapshots.md)


<!-- ====================================================================== -->
## <a name="fix-the-search-text-box-in-the-network-tool-can-now-be-resized"></a>修复：现在可以调整网络工具中的搜索文本框的大小

<!-- Title: Fix: Resize the Search text box in the Network tool -->
<!-- Subtitle: Now, resizing the Search pane in the Network tool also resizes the Search text box, so that the Refresh and Clear buttons remain visible. -->

在早期版本的 Microsoft Edge 中，在“**网络**”工具中更改窗格宽度时，“**搜索**”文本框不会调整大小。  窗格变窄时，不会显示“**刷新**”和“**清除**”按钮。  在 Microsoft Edge 98 中，此问题已解决。

![在“网络”工具中，“搜索”文本框现在会调整大小以显示“刷新”和“清除”按钮，即使窗格较窄。](../../media/2022/02/network-tool-search-text-box-resizes.png)

另请参阅：
* 在 _“检查网络活动_”中[搜索网络标头和响应](../../../network/index.md#search-network-headers-and-responses)。


<!-- ====================================================================== -->
## <a name="fix-icons-for-service-workers-and-script-tags-in-the-elements-tool-are-now-aligned"></a>修复：元素工具中服务工作进程的图标和脚本标记现已对齐

<!-- Title: Fix: Icons and tags in the DevTools are now aligned -->
<!-- Subtitle: Icons for service workers and script tags in the Elements tool now appear as expected. -->

在早期版本的 Microsoft Edge 中，“**应用程序**”工具的“**服务工作进程**”部分中的“**展开**”(![展开/折叠三角形图标。](../../media/2022/02/expand-collapse-triangle-icon.png))图标未对齐。  “**更新周期**”表中的版本号正在切断“**展开**”图标。  在 Microsoft Edge 98 中，此问题已修复：

![应用程序工具的“服务工作进程”部分中的图标现已对齐，因此展开/折叠图标现在完全可见。](../../media/2022/02/service-worker-icons-aligned-expand-icon-visible.png)

此外，在“**元素**”工具中，`<script>` 标记的“**展开**”(![DOM 树展开图标。](../../media/2022/02/elements-dom-expand-icon-light-mode.png)) 图标未对齐。  在 Microsoft Edge 98 中，此问题已修复：

![在元素工具中，\<script\> 标签的“展开”图标现已正确对齐。](../../media/2022/02/elements-script-tag-expand-icons-aligned.png)

另请参阅：
* _调试渐进式Web 应用 (PVA 中的 _ [服务工作者](../../../progressive-web-apps/index.md#service-workers)) - 在 DevTools 中调试服务工作者。
* [HTML 和 DOM](../../../beginners/html.md) - `<script>` 入门 **Elements** 工具中的标记。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge 版本 98 还包括来自 Chromium 项目的以下更新：

* [预览功能：全页辅助功能树](https://developer.chrome.com/blog/new-in-devtools-98/#a11y-tree)

* [“更改”选项卡中的更精确更改](https://developer.chrome.com/blog/new-in-devtools-98/#changes)

* [使用“后退/转发缓存”选项卡确保页面可缓存](https://developer.chrome.com/blog/new-in-devtools-98/#bfcache)

* [“新建属性”窗格筛选器](https://developer.chrome.com/blog/new-in-devtools-98/#properties)

* [在悬停命令上显示标尺](https://developer.chrome.com/blog/new-in-devtools-98/#show-rulers)

* [在 Flexbox 编辑器中支持行反转和列反转](https://developer.chrome.com/blog/new-in-devtools-98/#flexbox-editor)

* [重播 XHR 并展开所有搜索结果的新键盘快捷方式](https://developer.chrome.com/blog/new-in-devtools-98/#shortcuts)

   * [在网络面板中重播 XHR 的键盘快捷方式](https://developer.chrome.com/blog/new-in-devtools-98/#replay-xhr)

   * [展开所有搜索结果的键盘快捷方式](https://developer.chrome.com/blog/new-in-devtools-98/#toggle-search-result)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->
<!--
> [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New in DevTools (Chrome 98)](https://developer.chrome.com/blog/new-in-devtools-98) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google).
-->


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->
<!--
[![Creative Commons License.](../../../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
-->
