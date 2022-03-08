---
title: 'DevTools (Microsoft Edge 98) '
description: 2021 年回顾博客文章。  使用 IE 驱动程序自动Internet Explorer IE 模式。  模拟强制颜色模式。  性能工具事件日志中的活动图标的工具提示。  内存工具中的浅表大小现在显示为十进制值。  网络工具的"搜索"文本框现在可以调整大小。  等等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/02/2022
ms.openlocfilehash: 02abe0f6687a70b606bdec590866cd2d1487d6e7
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431730"
---
# <a name="whats-new-in-devtools-microsoft-edge-98"></a>DevTools (Microsoft Edge 98) 

以下部分列出了 Microsoft Edge 开发人员工具团队的公告。  要尝试 DevTools 的最新功能以及适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展，请阅读以下公告。  若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。

如果你使用的是 Windows、Linux 或 macOS，请考虑将 Microsoft Edge Canary 预览渠道用作默认开发浏览器。  通过预览渠道，可以访问 Microsoft Edge DevTools 的最新功能。


<!-- ====================================================================== -->
## <a name="catch-up-on-the-latest-and-greatest-features-in-microsoft-edge"></a>了解最新且最重要的Microsoft Edge

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Year-in-review: Microsoft Edge for developers -->
<!-- Subtitle: Catch up on the latest in developer tooling from Microsoft Edge. -->

2021 年，Microsoft Edge开发人员工具实现了巨大进步。  Visual Studio Code、DevTools 和浏览器现在提供了多个集成工作流，用于 JavaScript 调试、镜像 CSS 更改和从浏览器进行屏幕广播。  在焦点模式、Visual Studio Code主题和更多自定义选项之间，Microsoft Edge团队正在努力使 DevTools 更易于使用。

在我们的年度回顾博客文章 [2021](https://blogs.windows.com/msedgedev/2022/01/19/looking-back-at-microsoft-edge-for-developers-in-2021/) 中查看开发人员的 Microsoft Edge了解所有这些新闻和更多内容。

[![Sblog post： Looking back at Microsoft Edge for developers in 2021.](../../media/2022/02/blog-post-edge-devs-2021.png)](https://blogs.windows.com/msedgedev/2022/01/19/looking-back-at-microsoft-edge-for-developers-in-2021/)


<!-- ====================================================================== -->
## <a name="automate-ie-mode-with-internet-explorer-driver"></a>使用 IE 驱动程序自动Internet Explorer IE 模式

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: New support for automating IE mode -->
<!-- Subtitle: Test your legacy websites and apps by automating IE mode with Internet Explorer Driver. -->

从 2022 年 6 月 15 Internet Explorer 11 将不再支持某些版本的 Windows 10。 IE 模式是一项Microsoft Edge，适用于仍然需要使用 11 Internet Explorer与旧网站或应用兼容的组织。 为了支持测试这些旧网站和应用，你现在可以使用 Selenium 4 自动执行 IE 模式Internet Explorer驱动程序。 若要开始，请参阅在 Internet Explorer [驱动程序中自动执行 IE Microsoft Edge](../../../../webdriver-chromium/ie-mode.md)。


<!-- ====================================================================== -->
## <a name="emulate-forced-colors-mode"></a>模拟强制颜色模式

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Emulation of forced colors in the Rendering tool -->
<!-- Subtitle: You can now do a spot check of what your product will look like on a device running in forced-colors mode, without having to change your operating system settings. -->

除了模拟当前网页的深色、浅色和打印模式之外，现在还可以查看网页中已启用强制颜色模式的用户的外观。  强制颜色模式是操作系统的辅助功能。  它会强制将网页上的颜色缩小为有限的调色板，例如Windows高对比度模式。  模拟强制颜色模式允许你执行专色检查，而无需更改你自己的系统设置。

若要启用强制颜色模拟，请在 DevTools 中打开 **呈现** 工具，然后在"模拟 CSS 媒体功能 **强制颜色** "下拉列表中，选择 **"强制颜色： 活动"**。

在未启用强制颜色模拟的情况下，以下网页针对不同的背景颜色具有几种不同的文本颜色：

![呈现工具中未启用强制颜色模拟的网页。](../../media/2022/02/emulate-forced-colors-not-applied.png)

在呈现工具中启用强制颜色 **模拟后，** 网页将变成白色背景上的黑色文本：

![在呈现工具中启用强制颜色模拟的网页。  文本在白色背景上更改为黑色文本。](../../media/2022/02/emulate-forced-colors-applied.png)


<!-- ====================================================================== -->
## <a name="activity-icons-in-the-event-log-of-the-performance-tool-now-have-tooltips"></a>性能工具的事件日志中的活动图标现在具有工具提示

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Analyze runtime performance better with the Event Log in the Performance tool -->
<!-- Subtitle: Activity icons in the Event Log now have tooltips indicating the type of activity for each event, such as Scripting, Rendering, or Painting. -->

在早期版本的 Microsoft Edge 中，"性能"工具中的****"事件日志"选项卡**** 显示颜色编码的图标，这些图标表示每个事件的活动类型。  但是，事件日志不显示有关每种颜色表示哪种类型的活动的信息。  在 Microsoft Edge 98 中，工具提示已添加到"事件日志"选项卡中的活动事件，指示每个事件的**** 脚本、呈现、**绘制**、******系统和**空闲时间。 ********

![在事件日志中，选定的活动事件有一个表示 Painting 事件的绿色框，现在工具提示明确显示"Painting"。](../../media/2022/02/activity-event-tooltip.png)

有关记录性能配置文件详细信息，请参阅 [记录运行时性能](../../../evaluate-performance/reference.md#record-runtime-performance)。


<!-- ====================================================================== -->
## <a name="shallow-sizes-in-the-memory-tool-are-now-represented-as-decimal-values"></a>现在，内存工具中的浅表大小表示为十进制值

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Better understand shallow sizes in the Memory tool -->
<!-- Subtitle: The Memory tool has been updated to report shallow size in decimal values as a percentage of the heap. -->

在早期版本的 Microsoft Edge 中，内存工具中堆快照中的浅表大小通常报告为 0%，因为浅表大小相对于堆的总大小而言太小。  在 Microsoft Edge 98 中，如果浅表大小在堆的 0% 到 1% 之间，则现在报告为十进制值。

![在堆快照中，堆中 0% 到 1% 之间的"浅表大小"列值现在显示为具有一个或两个小数位数的小数值。](../../media/2022/02/shallow-size-decimal-values.png)

若要详细了解内存工具中的堆快照，请参阅 [记录堆快照](../../../memory-problems/heap-snapshots.md)。


<!-- ====================================================================== -->
## <a name="fix-the-search-text-box-in-the-network-tool-can-now-be-resized"></a>修复：现在可以调整网络工具中的"搜索"文本框的大小

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Fix: Resize the Search text box in the Network tool -->
<!-- Subtitle: Now, resizing the Search pane in the Network tool also resizes the Search text box, so that the Refresh and Clear buttons remain visible. -->

在早期版本的 Microsoft Edge 中，在"网络"工具中****，当您更改窗格**** 的宽度时，"搜索"文本框不会调整大小。  当窗格较窄时 **，不显示"** 刷新****"和"清除"按钮。  在 Microsoft Edge 98 中，此问题已修复。

![在"网络"工具中，"搜索"文本框现在会调整大小以显示"刷新"和"清除"按钮，即使窗格较窄。](../../media/2022/02/network-tool-search-text-box-resizes.png)

若要了解"网络 **"** 工具中的"搜索" **窗格，请参阅** 检查网络活动 [中的](../../../network/index.md#search-network-headers-and-responses) 搜索网络标头 _和响应_。


<!-- ====================================================================== -->
## <a name="fix-icons-for-service-workers-and-script-tags-in-the-elements-tool-are-now-aligned"></a>修复：服务工作者的图标和"元素"工具中的脚本标记现已对齐

<!-- careful changing h2 wording: Welcome tool potentially links to it -->

<!-- Title: Fix: Icons and tags in the DevTools are now aligned -->
<!-- Subtitle: Icons for service workers and script tags in the Elements tool now appear as expected. -->

在早期版本****![的 Microsoft Edge 中，展开 (展开/**** ****](../../media/2022/02/expand-collapse-triangle-icon.png) 折叠三角形图标。应用程序工具的"服务工作人员"部分中的) 图标未对齐。  更新周期表中的**版本号**已切断**展开图标。**  在 Microsoft Edge 98 中，此问题已修复。

![应用程序工具的"服务工作人员"部分中的图标现已对齐，因此"展开/折叠"图标现在完全可见。](../../media/2022/02/service-worker-icons-aligned-expand-icon-visible.png)

此外，在 **"元素**"工具中****，!["展开 ("DOM 树](../../media/2022/02/elements-dom-expand-icon-light-mode.png)`<script>`的"展开"图标。) 标记的图标未对齐。  在 Microsoft Edge 98 中，此问题已修复。

![在"元素"工具中，\<script\> 标记的"展开"图标现已正确对齐。](../../media/2022/02/elements-script-tag-expand-icons-aligned.png)

若要了解有关在 DevTools 中调试服务工作者的信息，请参阅服务 [工作者](../../../progressive-web-apps/index.md#service-workers)。  若要详细了解 Elements `<script>` 工具中的 **标记** ，请参阅 [HTML 和 DOM 入门](../../../beginners/html.md)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge版本 98 还包括来自 Chromium 项目的以下更新：

* [预览功能：全页辅助功能树](https://developer.chrome.com/blog/new-in-devtools-98/#a11y-tree)

* ["更改"选项卡中更精确的更改](https://developer.chrome.com/blog/new-in-devtools-98/#changes)

* [使用"后退/转发缓存"选项卡确保页面可缓存](https://developer.chrome.com/blog/new-in-devtools-98/#bfcache)

* ["新建属性"窗格筛选器](https://developer.chrome.com/blog/new-in-devtools-98/#properties)

* [在悬停命令上显示标尺](https://developer.chrome.com/blog/new-in-devtools-98/#show-rulers)

* [在 Flexbox 编辑器中支持行反向和列反向](https://developer.chrome.com/blog/new-in-devtools-98/#flexbox-editor)

* [新的键盘快捷方式，用于重播 XHR 并展开所有搜索结果](https://developer.chrome.com/blog/new-in-devtools-98/#shortcuts)

   * [在网络面板中重播 XHR 的键盘快捷方式](https://developer.chrome.com/blog/new-in-devtools-98/#replay-xhr)

   * [用于展开所有搜索结果的键盘快捷方式](https://developer.chrome.com/blog/new-in-devtools-98/#toggle-search-result)


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
[![Creative Commons License.](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
-->
