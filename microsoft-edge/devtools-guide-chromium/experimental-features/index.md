---
title: 实验功能
description: Microsoft Edge DevTools 中的最新实验性功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
no-loc:
- Enable webhint
ms.date: 10/31/2022
ms.openlocfilehash: c9f66979eed9c5e8822e7f5b77d371c7e31bca22
ms.sourcegitcommit: b15c540b2c48da3887d23e401e8543f297d178fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2022
ms.locfileid: "12849304"
---
# <a name="experimental-features"></a>试验功能

<!-- 
Policies to keep this page comprehensive and maintainable: 
*  Favor Canary over Stable re: sequencing.
*  Include a visible h2 section for every checkbox that's in public-facing Microsoft Edge DevTools > Experiments page.  If no info, write a tautology as a starting point.  Add as needed, each month.
*  Keep h2 sections in same order as DevTools > Settings > Experiments.
*  In the heading and UI steps, keep the checkbox label UI string as it appears in the UI; do not revise or "fix" it.
*  Don't change h2 text, that might break a link from UI.
*  When a checkbox is removed from all the channels, delete its section.

Steps to maintain this page monthly: For latest Canary, and for latest Stable:
1. Go to edge://settings/help, update if needed.
1. In DevTools, select Settings > Preferences > Restore Defaults > Reload DevTools.
1. In DevTools, go to Settings > Experiments.
1. In the "Experiments which are turned on by default" section below, update the Edge Canary list & Edge Stable list at top.
   *  In that section, link down to the h2; do not link to a different article.
1. Make sure the article has an h2 for each checkbox.
1. In each h2 section, update the presence or absence of "not", and update the version #:
This checkbox is|is not present in Microsoft Edge Canary 123.
This checkbox is|is not present in Microsoft Edge Stable 123.
-->

Microsoft Edge DevTools 提供对仍在开发中的试验功能的访问权限。  本文列出并介绍了以下任一项中的实验性功能：
*  最新版本的 Microsoft Edge Canary 预览频道。
*  最新版本的 Microsoft Edge 稳定版。

[Microsoft Edge 的所有通道](/deployedge/microsoft-edge-channels)都具有试验性功能。 可以使用 [Microsoft Edge Canary 渠道](https://www.microsoftedgeinsider.com/welcome?channel=canary) 获取最新的实验性功能。 若要查看 Microsoft Edge 版本中提供的完整列表，请参阅 DevTools 中的 **“设置****试验**” > 页。

<!-- no Warning formatting, because UI already contains red "WARNING" at top -->
这些试验可能不稳定或不可靠，可能需要重启 DevTools。


<!-- ====================================================================== -->
## <a name="experiments-which-are-turned-on-by-default"></a>默认情况下打开的试验

默认情况下，以下实验性功能处于打开状态。 你可以立即使用这些功能，而无需更改任何设置。 如果需要，可以关闭这些默认的实验性功能。

<!-- listed in order of the Settings > Experiments pane -->

**Microsoft Edge Canary 108 中默认启用：**
* [源订单查看器](#source-order-viewer)
* [启用键盘快捷方式编辑器](#enable-keyboard-shortcut-editor)
* [在“更改”选项卡中显示更精确的更改](#display-more-precise-changes-in-the-changes-tab)
* [使用具有时间跨度和快照模式的 Lighthouse 面板](#use-lighthouse-panel-with-timespan-and-snapshot-modes)
* [“样式”窗格中 CSS 层的工具](#tooling-for-css-layers-in-the-styles-pane)
* [在浏览器窗口外启用颜色选取](#enable-color-picking-outside-the-browser-window)
* [Enable webhint](#enable-webhint)
* [显示元素中的问题](#show-issues-in-elements)
* [在 Visual Studio Code 中的打开源文件](#open-source-files-in-visual-studio-code)

**Microsoft Edge Stable 106 中默认启用：**
* [源订单查看器](#source-order-viewer)
* [在“应用程序”面板中启用“报告 API”面板](#enable-reporting-api-panel-in-the-application-panel)
* [在“更改”选项卡中显示更精确的更改](#display-more-precise-changes-in-the-changes-tab)
* [使用具有时间跨度和快照模式的 Lighthouse 面板](#use-lighthouse-panel-with-timespan-and-snapshot-modes)
* [“样式”窗格中 CSS 层的工具](#tooling-for-css-layers-in-the-styles-pane)
* [在浏览器窗口外启用颜色选取](#enable-color-picking-outside-the-browser-window)
* [在对象属性查看器中突出显示重要的 DOM 属性](#highlight-important-dom-properties-in-the-object-properties-viewer)
* [Enable webhint](#enable-webhint)
* [显示元素中的问题](#show-issues-in-elements)
* [在 Visual Studio Code 中的打开源文件](#open-source-files-in-visual-studio-code)
* [启用键盘快捷方式编辑器](#enable-keyboard-shortcut-editor)

<!-- don't place a comment line between list item lines, above; that would create a gap -->


<!-- ====================================================================== -->
## <a name="turning-an-experiment-on-or-off"></a>打开或关闭试验

实验性功能不断更新，可能会导致性能问题。  这是你可能想要关闭试验的原因之一。

若要在 Microsoft Edge 中打开或关闭试验，请执行以下操作：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，单击 **“设置”** (![“设置”图标。](../media/settings-gear-icon-light-theme.png) “) ”按钮。  或者，按 `Shift`+`?`。

1. 在 **“设置”** 面板左侧，选择“ **试验”** 页。

   ![“设置”中的“试验”页。](../media/experiments-devtools.msft.png)

1. 在 **“试验** ”页上，选中或清除试验的复选框。 默认情况下，某些试验 (选定的) 处于打开状态。

1. 单击“ **关闭** ” (![DevTools >“设置”中的“关闭”图标。](../media/settings-close-icon-light-theme.png)) 右上角关闭“DevTools **设置**”。

1. 单击“ **重新加载 DevTools”** 按钮。


<!-- ====================================================================== -->
## <a name="restoring-defaults-for-which-experiments-are-selected"></a>还原选择了试验的默认值

若要还原为其启用实验功能的默认设置，请执行以下操作：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，单击 **“设置”** (![“设置”图标。](../media/settings-gear-icon-light-theme.png) “) ”按钮。  或者，按 `Shift`+`?`。  **“设置”** 面板随即打开，其中选择了 **“首选项”** 页。

1. 在 **“首选项”** 页底部，单击“ **还原默认值并刷新** ”按钮，然后单击“ **关闭** ” (DevTools > ![“设置”中的“关闭”图标。](../media/settings-close-icon-light-theme.png)) 。

<!-- For more information about customizing settings, see [Settings](../customize/index.md#settings) in _Customize Microsoft Edge DevTools_. -->


<!-- ====================================================================== -->
## <a name="filtering-the-experiments"></a>筛选试验

可以按标题中包含的文本筛选实验性功能。

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，单击 **“设置”** (![“设置”图标。](../media/settings-gear-icon-light-theme.png) “) ”按钮。  或者，按 `Shift`+`?`。  **“设置”** 面板随即打开，其中选择了 **“首选项”** 页。

1. 在 **“设置”** 面板左侧，选择“ **试验”** 页。

1. 在“ **筛选器** ”文本框中单击并输入文本，例如 **时间线**。  键入时，“ **试验** ”页中仅显示匹配的复选框。

1. 若要结束筛选，请清除 **“筛选器** ”文本框。


<!-- ====================================================================== -->
## <a name="providing-feedback-about-the-experiments"></a>提供有关试验的反馈

我们渴望听到你关于实验功能的反馈。  若要与我们共享反馈， [请联系 Microsoft Edge DevTools 团队](../contact.md)。

其中一个 UI 试验添加了提供反馈的新方法：打开 **焦点模式** 试验后，在 **活动栏**底部选择 **“帮助** ” (![“焦点模式”活动栏中的“帮助”图标。](../media/help-icon-of-focus-mode.png)) > **反馈**。


<!-- ====================================================================== -->
## <a name="list-of-experiments"></a>试验列表

下面列出了 Microsoft Edge 的 Canary 预览频道最新版本中显示的试验复选框。  在 Canary 中添加或删除复选框之后，还记下了稳定版本。


<!-- ============================================================================================================================================ -->
<!-- top of list of checkboxes -->
<!-- ============================================================================================================================================ -->


<!-- ====================================================================== -->
## <a name="allow-extensions-to-load-custom-stylesheets"></a>允许扩展加载自定义样式表

某些 Microsoft Edge 加载项可以为 DevTools 定义自定义颜色主题。 如果安装具有主题的加载项，则需要启用 **“允许扩展加载自定义样式表** ”试验以查看加载项主题。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="capture-node-creation-stacks"></a>捕获节点创建堆栈

若要在运行时将 DOM 节点添加到 DOM 时捕获 JavaScript 堆栈跟踪，请启用此试验。 捕获的堆栈跟踪显示在 **“元素**”面板的“**堆栈跟踪**”窗格中。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="automatically-pretty-print-in-the-sources-panel"></a>在“源”面板中自动完成打印

打开此试验后，在“源”面板中显示缩小的文件时，该文件在“源”面板中的单个选项卡中打开，且打印美观。

关闭此试验后，带有按钮的 UI 提示将询问是否对文件进行美观打印。  该文件在附加的选项卡中打开，该选项卡的追加后缀为 **：formatted**。

*  _缩小_的文件串联成一条长行。
*  相比之下， _漂亮的打印_ 以缩进、更易于阅读的格式呈现文件的内容。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="protocol-monitor"></a>协议监视器

DevTools 使用 DevTools 协议与检查的页面通信。

若要监视 DevTools 发送和接收的消息以调试检查的页面，请执行以下操作：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，单击 **“设置”** (![“设置”图标。](../media/settings-gear-icon-light-theme.png) “) ”按钮。  或者，按 `Shift`+`?`。  **“设置”** 面板随即打开，其中选择了 **“首选项”** 页。

1. 在 **“设置”** 面板左侧，选择“ **试验”** 页。

1. 选中“ **协议监视器** ”复选框，然后单击“ **关闭** ” (DevTools > ![“设置”中的“关闭”图标。](../media/settings-close-icon-light-theme.png)) 关闭 **“设置**”。

1. 打开命令**菜单** (`Ctrl`+`P`+`Shift`) ，然后在文本框中键入**协议**。

1. 选择“ **显示协议监视器**”。  将显示消息：“一个或多个设置已更改，需要重新加载才能生效。”

1. 单击消息旁边的 **“重新加载 DevTools** ”按钮。

1. **协议监视器**工具显示在 DevTools 底部的**抽屉**中。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="show-csp-violations-view"></a>显示 CSP 冲突视图

添加 **CSP 违规** 工具，该工具显示所检查网页上检测到的任何内容安全策略 (CSP) 冲突。

![CSP 冲突工具。](index-images/csp-violations-tool.png)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="record-coverage-while-performance-tracing"></a>性能跟踪时的记录覆盖率

记录性能跟踪时的覆盖范围。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="show-option-to-expose-internals-in-heap-snapshots"></a>显示用于在堆快照中公开内部内容的选项

_从 Microsoft Edge 105 起新增功能_

是否显示复选框以在 **内存** 工具的堆快照中公开内部。
<!-- todo: need text -->

另请参阅：
* [使用内存工具记录堆快照](../memory-problems/heap-snapshots.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="source-order-viewer"></a>源订单查看器

正在删除此复选框。  源顺序查看器现在是常规功能，而不是试验。  复选框是选中还是取消选中没有任何区别;无论哪种方式，“源顺序查看器”功能都显示在 DevTools 中。

另请参阅：
* [使用源订单查看器测试键盘支持](../accessibility/test-tab-key-source-order-viewer.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-keyboard-shortcut-editor"></a>启用键盘快捷方式编辑器

是否启用编辑键盘快捷方式。

从 Microsoft Edge 107 开始，此复选框已从 **“特别不稳定** ”部分向上移动到常规部分。

另请参阅：
* [自定义键盘快捷方式](../customize/shortcuts.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框，位于 **“特别不稳定** ”部分。


<!-- ====================================================================== -->
## <a name="timeline-event-initiators"></a>时间线：事件发起方

是否在时间线中包含事件发起方。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="timeline-webgl-based-flamechart"></a>时间线：基于 WebGL 的火焰图

是否在时间线中使用基于 WebGL 的火焰图。

状态：
*  Microsoft Edge Canary 108 中不存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="webassembly-debugging-enable-dwarf-support"></a>WebAssembly 调试：启用 DWARF 支持

启用对 WebAssembly 调试的 DWARF 支持。  请参阅 _DevTools (Microsoft Edge 80) 中的新增功能_中的[改进 WebAssembly 调试](../whats-new/2019/12/devtools.md#improved-webassembly-debugging)。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="console-resolve-variable-names-in-expressions-using-source-maps"></a>控制台：使用源映射解析表达式中的变量名称

在控制台中计算表达式时，使用源映射自动将原始变量名称映射到缩小的变量名称。

有关 [调试，请参阅将处理过的代码映射到原始源代码](../javascript/source-maps.md)。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-new-advanced-perceptual-contrast-algorithm-apca-replacing-previous-contrast-ratio-and-aaaaa-guidelines"></a> (APCA 启用新的高级感知对比度算法，) 替换以前的对比度和 AA/AAA 准则

[高级感知对比度算法 (APCA)](https://w3c.github.io/silver/guidelines/methods/Method-font-characteristic-contrast.html) 取代了颜色选取器中的 [AA](https://www.w3.org/WAI/WCAG21/quickref#contrast-minimum)/[AAA](https://www.w3.org/WAI/WCAG21/quickref#contrast-enhanced) 准则对比率。  颜色选择器在“**元素**”工具的“**样式**”选项卡中使用。

APCA 是一种计算对比度的新方法。  它基于对颜色感知的新式研究。  与 AA/AAA 准则相比，APCA 更依赖于上下文。  对比度是根据文本、颜色和上下文的以下空间属性计算的。

*  文本的空间属性，包括字体粗细和大小。
*  颜色的空间属性，包括文本和背景之间的感知对比度。
*  上下文的空间属性，包括环境光线、周围环境和预期用途。

另请参阅：
* [新的颜色对比度计算 - ](../whats-new/2021/01/devtools.md#new-color-contrast-calculation---advanced-perceptual-contrast-algorithm-apca) _DevTools (Microsoft Edge 89) 中的新增功能中的 _高级感知对比度算法 (APCA) 。
* 使用 _CSS 功能参考_中的[颜色选择器更改颜色](../css/reference.md#change-colors-with-the-color-picker)。
* [使用颜色选取器测试文本颜色对比度](../accessibility/color-picker.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-full-accessibility-tree-view-in-the-elements-panel"></a>在“元素”面板中启用完整的辅助功能树视图

在 **“元素”** 工具中添加一个按钮，用于在 DOM 树和辅助功能树之间切换。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-the-font-editor-tool-within-the-styles-pane"></a>在“样式”窗格中启用“字体编辑器”工具
<!-- keep "Enable the" in heading, though check box label says "Enable new Font Editor tool within the Styles pane".
omit period, even though checkbox label has period -->

可以使用可视 [字体编辑器](../inspect-styles/edit-fonts.md) 编辑字体。  使用它来定义字体和字体特征。  视觉字体 **编辑器** 可帮助你执行以下操作：

*  在不同字体属性的单位之间切换
*  在不同字体属性的关键字之间切换
*  转换单位
*  生成准确的 CSS 代码

若要使用可视 **字体编辑器，请执行以下操作**：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 中，在主工具栏上，选择“ **元素** ”选项卡。 如果“ **元素** ”选项卡不可见，请单击“ **更多选项卡** (![更多选项卡”图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者单击“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在“ **样式** ”选项卡中，选择“ **字体编辑器”** 图标。

   ![突出显示了视觉对象“字体编辑器”窗格。](../media/font-editor-open.msft.png)

某些浏览器频道在 **“样式”窗格中具有复选框标签“启用新的字体编辑器工具”。**

另请参阅：
* [在“样式”窗格中编辑 CSS 字体样式和设置](../inspect-styles/edit-fonts.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-automatic-contrast-issue-reporting-via-the-issues-panel"></a>通过问题面板启用自动对比度问题报告

在“问题”工具中启用自动对比度 **问题** 报告。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-experimental-cookie-features"></a>启用实验性 Cookie 功能

启用实验性 Cookie 功能。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-reporting-api-panel-in-the-application-panel"></a>在“应用程序”面板中启用“报告 API”面板

使用报告 API 捕获某些错误，例如安全冲突或已弃用的 API 调用。 当用户访问站点并发送到服务器终结点时，会发生这些错误。 启用此试验以在 **“应用程序**”面板中添加 **“报告 API**”部分，其中列出了发送到终结点的所有报表。

状态：
*  Microsoft Edge Canary 108 中不存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="display-more-precise-changes-in-the-changes-tab"></a>在“更改”选项卡中显示更精确的更改

请参阅 [“更改”选项卡中的“更精确的更改](https://developer.chrome.com/blog/new-in-devtools-98/#changes)”。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="sync-css-changes-in-the-styles-pane"></a>在“样式”窗格中同步 CSS 更改

是否同步 **“元素**”工具的“**样式**”选项卡中的 CSS 更改。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="local-overrides-for-response-headers"></a>响应标头的本地替代

是否对响应标头使用本地替代。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-css-authoring-hints-for-inactive-rules-deprecated-properties-etc"></a>为非活动规则、弃用的属性等启用 CSS 创作提示。
<!-- keep "etc." in heading, to match UI label -->

_从 Microsoft Edge 105 起新增功能_

是否在 **“元素”** 工具的 **“样式**”面板中启用 CSS 创作提示，以在非活动或已弃用的属性旁边显示信息工具提示。

在 **“样式”** 面板中编写或检查 CSS 时，此功能可提供帮助。  小信息图标显示在处于非活动状态或已弃用的 CSS 属性旁边。  非活动属性是一个正确应用于元素但对它没有影响的属性， (例如， `width:100px` 应用于内联元素) 没有影响。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="use-lighthouse-panel-with-timespan-and-snapshot-modes"></a>使用具有时间跨度和快照模式的 Lighthouse 面板

向 Lighthouse 工具添加一个选择器，以在不同的报告模式之间切换。  目前，支持导航和快照模式。

另请参阅：
* [Lighthouse 工具](../lighthouse/lighthouse-tool.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="tooling-for-css-layers-in-the-styles-pane"></a>“样式”窗格中 CSS 层的工具

在 **“样式**”窗格中增加了对 `@layer` CSS 规则的支持。  “ **样式** ”窗格中的 CSS 规则按它们所属的层进行分组。  此时会显示层概述小组件，该小组件显示当前已检查元素的层树。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-color-picking-outside-the-browser-window"></a>在浏览器窗口外启用颜色选取

允许你在屏幕上的任何位置（而不仅仅是 Microsoft Edge 窗口内）移动鼠标光标作为吸管工具时移动鼠标光标。

在 **“元素”** 工具的“ **样式** ”选项卡中，单击任何颜色预览。  颜色选取器随即打开。  单击“ **切换颜色选取器** (![吸管”图标按钮。](index-images/eyedropper-color-picker-icon.png)) 按钮。  鼠标光标变为吸管。  单击监视器上的任意位置以选择颜色。

<!-- https://developer.chrome.com/blog/new-in-devtools-102/#color-picker -->

另请参阅：
* 使用 _CSS 功能参考_中的[颜色选择器更改颜色](../css/reference.md#change-colors-with-the-color-picker)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="group-sources-into-authored-and-deployed-trees"></a>将源分组到“创作”和“已部署”树中

_Microsoft Edge 104 的新增功能_
<!-- This experiment was shown in the What's New 104 video [Microsoft Edge | What's New in DevTools 104](https://www.youtube.com/watch?v=0_ZprFX8x0I&t=129s) at 2:09. -->

控制是否在 **“源**”工具的“**页面**”选项卡中将资源分组到单独的 **“创作**”树和“**已部署**”树中。  **源**工具中的此功能允许将源文件分组到两个文件夹中，具体取决于这些文件是否为：
*  原始源文件 (创作，即具有本地编辑) 的文件。
*  ) 编译和捆绑源文件后，生产文件 (Web 服务器上部署的文件。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="hide-ignore-listed-code-in-sources-tree-view"></a>隐藏源树视图中忽略列出的代码

_从 Microsoft Edge 106 起新增功能_

是否隐藏或显示“ **源”** 工具树视图中的“忽略”列表中的代码，例如“ **页面** ”选项卡。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="highlight-important-dom-properties-in-the-object-properties-viewer"></a>在对象属性查看器中突出显示重要的 DOM 属性

_从 Microsoft Edge 105 起新增功能_

选中此复选框会突出显示当前所选 DOM 树元素的工具（如 **“元素”** 工具）的“**属性**”选项卡中的重要 DOM 属性。  此新试验使主要属性更易于查看。  某些属性以粗体显示，其他属性以粗体显示，旁边有一个星形图标。

此突出显示很有用，因为在 JavaScript 中，对象继承自父对象，而父对象本身继承自其他上级对象，有时相当于数百个属性。  此试验可帮助你查找主要属性。

对象属性查看器包含多个工具，包括 **元素**、 **源**、 **控制台**和 **网络**。  它提供对象的属性树视图。


#### <a name="in-the-elements-tool"></a>在“元素”工具中

若要在 **“元素** ”工具中查看对象属性查看器，请执行以下操作：

1. 右键单击网页中的项目，然后选择“ **检查**”。  DevTools 随即打开，其中“元素”工具的 DOM 树中选择了页面 **元素** 。

1. 在 **“元素”** 工具中，选择“ **属性** ”选项卡，该选项卡与 **“样式** ”选项卡分组。

   “ **属性** ”选项卡包含所选元素的属性列表。


#### <a name="in-the-sources-tool"></a>在“源”工具中

若要在 **源** 工具中查看对象属性查看器，请执行以下操作：

1. 打开文件 `.js` 。

1. 在文件中的代码 `.js` 行上设置断点。

1. 通过在网页上运行代码，将调试器暂停到该行。

   对象属性显示在右侧边栏中的 **“作用域** ”部分中。  请参阅在 _JavaScript 调试功能_中[查看和编辑属性和变量](../javascript/reference.md#view-and-edit-properties-and-variables)。


状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="log-devtools-uncaught-exceptions-to-console"></a>将 DevTools 未捕获的异常记录到控制台

控制是否在 **控制台** 工具中记录 DevTools 未捕获的异常。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## Enable webhint

[webhint](https://webhint.io) 是一个开源代码工具，可为网站和本地网页提供实时反馈。  [webhint](https://webhint.io) 提供的反馈类型包括：

*  辅助功能
*  跨浏览器兼容性
*  安全
*  性能
*  渐进式 Web 应用 (PWA)
*  其他常见 Web 开发问题

[Webhint](https://webhint.io) 试验在“[问题](../issues/index.md)”面板中显示 webhint 反馈。  选择问题以显示有关解决方案的文档以及网站上受影响的资源列表。  选择资源链接以在 DevTools 中打开相关的 **“网络**”、“ **源**”或“ **元素** ”窗格。

![“问题”面板中的 webhint 反馈。](../media/experiments-webhint.msft.png)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="show-issues-in-elements"></a>显示元素中的问题

启用此试验可在 **“元素”** 工具的 **DOM** 视图中查看 HTML 下的语法错误。 有关详细信息，请参阅 [Wavy 下划线突出显示元素工具中的代码问题和改进](../whats-new/2021/04/devtools.md#wavy-underlines-highlight-code-issues-and-improvements-in-elements-tool)。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="focus-mode"></a>焦点模式

焦点模式是 DevTools 的新用户界面。  焦点模式旨在简化和简化 DevTools UI，而不会影响其功能集。

焦点模式将选项卡的主行替换为 **活动栏**，活动栏是具有独特图标的紧凑工具栏。  **使用活动栏**可以固定、重新排列和打开喜欢的工具，以便快速访问。  **活动栏**还提供对用户设置、帮助和其他功能的访问权限。

焦点模式还提供 **快速视图** 列表，以打开第二个工具以及 **已在活动栏中**选择的工具。

请参阅 [使用焦点模式降低 DevTools 的复杂性](focus-mode.md)。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="open-source-files-in-visual-studio-code"></a>在 Visual Studio Code 中的打开源文件

**Visual Studio Code 中的开放源文件**试验将源工具的代码编辑器替换为Visual Studio Code，用于编辑本地文件。 打开此试验时，开发人员工具会检测何时编辑本地文件，并提示选择要用作工作区的文件夹。

选择要用作工作区的文件夹时，选择 DevTools 中某个文件的任何链接将在 Visual Studio Code 中打开该文件。  在早期版本的 Microsoft Edge 中，此操作在 DevTools 中源工具的代码编辑器中打开了文件。

![在“样式”工具中选择文件链接将在 Visual Studio Code 中打开该文件。](../media/experiment-sources-in-code-editor-open.msft.png)

在 DevTools 中所做的任何编辑现在会更改硬盘驱动器上的文件，并与 Visual Studio Code 实时同步。 有关设置工作区的信息，请参阅在 [Visual Studio Code 中打开源文件](../sources/opening-sources-in-vscode.md)。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ============================================================================================================================================ -->
<!-- >> [!WARNING]
> These experiments are particularly unstable. Enable at your own risk. -->


<!-- ====================================================================== -->
## <a name="ignore-list-for-javascript-frames-on-timeline"></a>忽略时间线上 JavaScript 帧的列表

是否在时间线上包括 JavaScript 帧的忽略列表。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="input-events-on-timeline-overview"></a>时间线上的输入事件概述

控制是否在时间线概述中包含输入事件。
<!-- todo: need text -->

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="live-heap-profile"></a>实时堆配置文件

控制是否实时更新堆配置文件。
<!-- todo: need text -->

另请参阅：
* [使用内存工具记录堆快照](../memory-problems/heap-snapshots.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="sampling-heap-profiler-timeline"></a>采样堆探查器时间线

控制是否显示采样堆探查器时间线。
<!-- todo: need text -->

另请参阅：
* [使用内存工具记录堆快照](../memory-problems/heap-snapshots.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="timeline-invalidation-tracking"></a>时间线：失效跟踪

控制是否在时间线上显示无效跟踪。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="timeline-show-all-events"></a>时间线：显示所有事件

控制是否在时间线上显示所有事件。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="timeline-v8-runtime-call-stats-on-timeline"></a>时间线：时间线上的 V8 运行时调用统计信息

控制是否在时间线上显示 v8 运行时调用统计信息。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="timeline-replay-input-events"></a>时间线：重播输入事件

控制是否重播时间线上的输入事件。

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-instrumentation-breakpoints"></a>启用检测断点

是否在测试断点处停止。  此试验使断点更加可靠。

另请参阅：
* [在检测断点上启用同步](https://chromium-review.googlesource.com/c/devtools/devtools-frontend/+/3470237)
* [首次加载源文件时，断点可能不会触发](https://bugs.chromium.org/p/chromium/issues/detail?id=1133307&q=%22instrumentation%20breakpoints%22&can=2)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。


<!-- ====================================================================== -->
## <a name="enable-re-designed-breakpoint-sidebar-pane-in-the-sources-panel"></a>在源面板中启用重新设计的断点边栏窗格
<!-- preserve heading = UI label -->

_从 Microsoft Edge 106 起新增功能_

是否在 **“源”** 工具中显示“**断点边栏**”窗格的重新设计版本。

另请参阅：
* [使用断点暂停代码](../javascript/breakpoints.md)

状态：
*  Microsoft Edge Canary 108 中存在此复选框。
*  Microsoft Edge Stable 106 中存在此复选框。
