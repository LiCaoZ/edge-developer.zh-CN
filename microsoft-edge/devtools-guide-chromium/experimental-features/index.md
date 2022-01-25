---
title: 实验性功能
description: DevTools 中的最新Microsoft Edge功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
no-loc:
- Enable webhint
- Enable Network Console
- Source Order Viewer
- Enable Composited Layers in 3D View
- Enable new Font Editor tool within the Styles pane
- Enable new CSS Flexbox debugging features
- Enable + button tab menus to open more tools
- Enable Welcome tab
- 3D View
- Turn on support to move tabs between panels
- Match keyboard shortcuts in DevTools to Microsoft Visual Studio Code
- Edit keyboard shortcuts for any action in DevTools
- Turn on new CSS grid debugging features
- 'Emulation: Support dual screen mode'
ms.date: 11/30/2021
ms.openlocfilehash: 20894a79818a0fd05b350e2fd7ee8cfea4714d77
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12317818"
---
# <a name="experimental-features"></a>试验功能

<!-- 
Policies for maintaining this page:
Cover the latest Canary version.
Keep h2 sections in same order as Microsoft Edge DevTools > Experiments page.
In the heading and UI steps, keep the checkbox label UI string as-is.
Include an h2 section for every checkbox that's in public-facing Microsoft Edge DevTools > Experiments page.
If no info is an an h2 section, comment out the h2 heading & section.
When a checkbox is removed from all the preview channels, move its section down to "Previously Experimental features which are now regular features" and comment it out.
-->

Microsoft Edge DevTools 提供对仍在开发中的试验功能的访问权限。  本文列出并介绍了最新版本的 Canary 预览频道中的大多数实验Microsoft Edge。

组织[的所有频道Microsoft Edge](/deployedge/microsoft-edge-channels)实验性功能。 可以使用以下方法获取最新的实验[Microsoft Edge Canary 渠道。](https://www.microsoftedgeinsider.com/welcome?channel=canary) 若要查看最新版本中提供的完整列表Microsoft Edge，请参阅****  >  DevTools 设置**实验**"页面。

<!-- no Warning formatting, because UI already contains red "WARNING" at top -->
这些实验可能不稳定或不可靠，可能需要重启 DevTools。


<!-- ====================================================================== -->
## <a name="experiments-which-are-turned-on-by-default"></a>默认情况下打开的实验

默认情况下，以下实验性功能为打开状态。 你可以马上使用这些功能，而无需更改任何设置。 如果需要，可以关闭这些默认实验功能。

<!-- listed in order of the Settings > Experiments pane -->
*  源订单查看器。
*  启用前向缓存调试支持。
*  [Emulation: Support dual screen mode](../device-mode/dual-screen-and-foldables.md).
*  启用实验性隐藏问题菜单。
*  Enable webhint.
*  在元素中显示问题。
*  Enable Composited Layers in 3D View.
*  DevTools 工具提示。
*  VS Code开发工具的主题。 <!-- preserve literal UI string, including "VS" & "the" -->
*  open source files in Visual Studio Code.
*  启用键盘快捷方式编辑器 - [Edit keyboard shortcuts for any action in DevTools](../customize/shortcuts.md#edit-the-keyboard-shortcut-for-a-devtools-action) 。
*  启用动态欢迎内容，默认为现在关闭，但在版本 97 中Microsoft Edge启用。

<!-- don't place a comment line between list item lines, above; that would create a gap -->

<!-- Don't list this checkbox in this article; it's being removed: -->
<!-- *  Enable CSS \<length\> authoring tool in the Styles pane -->

<!-- *  Detached Elements 
Is the Detached Elements experiment checkbox intended to be present for external users?
Is the Detached Elements experiment checkbox intended to be turned on by default, for external users?
-->


<!-- ====================================================================== -->
## <a name="turning-an-experiment-on-or-off"></a>打开或关闭实验

实验性功能会不断更新，并且可能会导致性能问题。  这是你可能想要关闭实验的一个原因。

若要打开或关闭实验，Microsoft Edge：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  单击 **"设置 (** 齿轮) 图标打开 DevTools 设置窗格。 [](../customize/index.md#settings)

1.  在"实验"窗格**设置，** 单击"实验 **"** 部分。

    :::image type="content" source="../media/experiments-devtools.msft.png" alt-text="设置中的试验页面" lightbox="../media/experiments-devtools.msft.png":::

1.  在实验 **页面上** ，选中或清除实验的复选框。 默认情况下，某些实验 (选中) 打开。

1.  单击 **"** 关闭 ("中的"关闭"图标。> 设置) 右上方的"关闭"图标以关闭 ![ ](../media/settings-close-icon-light-theme.png) "DevTools**设置"。**

1.  单击" **重新加载 DevTools"** 按钮。


<!-- ====================================================================== -->
## <a name="restoring-defaults-for-which-experiments-are-selected"></a>还原已选择实验的默认值

若要还原打开实验功能的默认设置，请：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  选择**设置 (** ![ 开发人员设置中的") >" ](../media/settings-gear-icon-light-mode.png) **图标。**

1.  单击"**还原默认值并刷新**"按钮，然后单击"关闭**** (DevTools > 设置 中的"关闭 ![ "图标 ](../media/settings-close-icon-light-theme.png) 。) 。

<!-- For more information about customizing settings, see [Settings](../customize/index.md#settings) in _Customize Microsoft Edge DevTools_. -->


<!-- ====================================================================== -->
## <a name="filtering-the-experiments"></a>筛选实验

你可以按标题中包含的文本筛选实验性功能。

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  选择**设置 (** 开发设置中的 ![ ") >" ](../media/settings-gear-icon-light-mode.png) **图标**。

1.  在"筛选器 **"文本框** 中单击并输入文本，如 **时间线**。  键入时，只有匹配的复选框显示在实验 **页面中** 。

1.  若要结束筛选，请清除 **"筛选器"** 文本框。


<!-- ====================================================================== -->
## <a name="providing-feedback-about-the-experiments"></a>提供有关实验的反馈

我们期待收到有关实验功能的反馈。

* 请通过发布推文 [@EdgeDevTools](https://twitter.com/edgedevtools) 向我们发送反馈。

* [联系开发人员Microsoft Edge团队](../contact.md)。

* 打开焦点**模式**实验后，在活动栏底部，选择"帮助****" (焦点模式**** 的活动栏中的"帮助"图标) >反馈"，以显示"发送反馈 ![ ](../media/help-icon-of-focus-mode.png) "窗口。 **** ****


<!-- ====================================================================== -->
## <a name="list-of-experiments"></a>实验列表

下面列出了在最新版本的 Canary 预览频道中显示Microsoft Edge实验。


<!-- ====================================================================== -->
## <a name="allow-extensions-to-load-custom-stylesheets"></a>允许扩展加载自定义样式表
<!-- present in 96, 98 -->

某些Microsoft Edge加载项可以定义 DevTools 的自定义颜色主题。 如果安装具有主题的加载项，则需要启用"允许扩展加载自定义样式表****"实验来查看加载项主题。


<!-- ====================================================================== -->
## <a name="capture-node-creation-stacks"></a>捕获节点创建堆栈
<!-- present in 96, 98 -->

若要在运行时将 DOM 节点添加到 DOM 时捕获 JavaScript 堆栈跟踪，请启用此实验。 捕获的堆栈跟踪显示在"元素"面板的"**堆栈****跟踪"** 窗格中。


<!-- ====================================================================== -->
## <a name="automatically-pretty-print-in-the-sources-panel"></a>在"源面板"中自动打印
<!-- present in 96, 98 -->

打开此实验时，当你在"源"面板中显示缩小文件时，该文件在"源"面板中的单个选项卡中打开，非常打印。

关闭此实验后，带按钮的 UI 提示会询问你是否要以设计方式打印文件。  文件在附加后缀为 **：formatted**的其他选项卡中打开。

*  缩小 _文件_ 将连接为一个长行。
*  相比之下， _更智能的_ 打印以缩进、更可读的格式呈现文件的内容。


<!-- ====================================================================== -->
## <a name="protocol-monitor"></a>协议监视器
<!-- present in 96, 98 -->

DevTools 使用 DevTools 协议与检查的页面通信。

若要监视 DevTools 发送和接收的消息以调试检查的页面：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  在 DevTools 中，选择 **"设置**  >  **实验"。**

1.  选中"**协议监视器**"复选框，然后单击"**** 关闭 (DevTools > 设置 中的"关闭"图标。) 关闭 ![ ](../media/settings-close-icon-light-theme.png) 设置。 ****

1.  打开命令**菜单** `Control` + `Shift` + `P` () ，然后在文本框中键入协议。 ****

1.  选择 **"显示协议监视器"。**  将出现以下消息："一个或多个设置已更改，要求重新加载生效。"

1.  单击 **显示在邮件旁边的"重新加载 DevTools"** 按钮。

1.  协议**监视器**工具显示在 DevTools 底部的"箱"中。 ****


<!-- ====================================================================== -->
<!-- ## Show CSP Violations view -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Record coverage while performance tracing -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Show option to take heap snapshot where globals are treated as root -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
## <a name="source-order-viewer"></a>源订单查看器
<!-- present in 96, 98 -->

**Source Order Viewer** 是显示网页源中元素顺序的试验。 屏幕显示顺序可以不同于源的顺序，这会使屏幕阅读器和键盘用户混淆。 使用 **Source Order Viewer** 试验查找屏幕显示顺序和源顺序之间的差异。

若要使用 **Source Order Viewer** ：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  打开“**元素**”工具。

1.  在" **样式"选项卡** 的右侧，单击 **"辅助功能"** 选项卡。

1.  在部分 **Source Order Viewer** 下，选中" **显示源订单"** 复选框。

1.  突出显示任何 HTML 元素以显示网页源中订单的覆盖。

:::image type="content" source="../media/experiments-source-order-viewer.msft.png" alt-text=":::no-loc (源订单查看器) ：：： 在辅助功能窗格中" lightbox="。。/media/experiments-source-order-viewer.msft.png"：：：

此实验默认打开。

有关详细信息，[请参阅使用 Source Order Viewer ](../accessibility/test-tab-key-source-order-viewer.md)


<!-- ====================================================================== -->
## <a name="enable-back-forward-cache-debugging-support"></a>启用前向缓存调试支持
<!-- present in 96, 98 -->

前向缓存或 *bfcache*。 在内存中保存已访问网页的快照，加快浏览历史记录的浏览速度。

无法缓存某些网页。 启用此实验以将" **前向缓存"** 部分添加到" **应用程序"** 面板。  启用前向缓存调试提供有关无法存储在 中的网页的信息 `bfcache` 。


<!-- ====================================================================== -->
<!-- ## WebAssembly Debugging: Enable DWARF support -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
## Emulation: Support dual screen mode
<!-- present in 96, 98 -->

有关详细信息，请参阅 [Emulation: Support dual screen mode](../device-mode/dual-screen-and-foldables.md)。


<!-- ====================================================================== -->
<!-- ## Enable new Advanced Perceptual Contrast Algorithm (APCA) replacing previous contrast ratio and AA/AAA guidelines -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Enable full accessibility tree view in the Elements panel -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
## Enable new Font Editor tool within the Styles pane

<!-- present in 96, 98 -->

现在，可以使用新的可视 [字体编辑器来](../inspect-styles/edit-fonts.md) 编辑字体。  使用它来定义字体和字体特征。  可视 **字体编辑器** 可帮助您执行以下操作：

*   在不同字体属性的单位之间切换
*   在不同字体属性的关键字之间切换
*   转换单位
*   生成准确的 CSS 代码

若要使用新的可视化**字体编辑器：**

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  打开“**元素**”工具。

1.  打开“**样式**”窗格。

1.  选择" **字体编辑器"** 图标。

有关新的可视字体编辑器 **的详细信息，** 请参阅在样式窗格中编辑 [CSS 字体样式和设置](../inspect-styles/edit-fonts.md)。

:::image type="complex" source="../media/font-editor-open.msft.png" alt-text="突出显示可视内容字体编辑器窗格" lightbox="../media/font-editor-open.msft.png":::
   突出显示可视内容**字体编辑器**窗格
:::image-end:::

有关详细信息，请参阅"样式"窗格中[的"编辑 CSS 字体样式和设置"。](../inspect-styles/edit-fonts.md)


<!-- ====================================================================== -->
<!-- ## Enable automatic contrast issue reporting via the Issues Panel -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Enable experimental cookie features -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
## <a name="enable-reporting-api-panel-in-the-application-panel"></a>在应用程序面板中启用报告 API 面板
<!-- present in 96, 98 -->

使用报告 API 捕获某些错误，如安全违反或已弃用 API 调用。 这些错误在用户访问您的网站并发送到服务器终结点时发生。 启用此实验以在应用程序面板中添加**报告**API**** 部分，其中列出了发送到终结点的所有报告。

<!-- ====================================================================== -->
<!-- ## Log DevTools uncaught exceptions to Console -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
## Enable webhint
<!-- present in 96, 98 -->

[webhint](https://webhint.io) 是一个开源代码工具，可为网站和本地网页提供实时反馈。  Webhint 提供 [的反馈类型](https://webhint.io) 包括：

*   辅助功能
*   跨浏览器兼容性
*   安全
*   性能
*   渐进式 Web 应用 (PWA)
*   其他常见的 Web 开发问题

[Webhint](https://webhint.io) 试验在“[问题](../issues/index.md)”面板中显示 webhint 反馈。  选择一个问题，在网站上显示有关解决方案的文档和受影响资源的列表。  选择资源链接以在 DevTools******中**打开**** 相关的"网络、源"或"元素"窗格。

:::image type="content" source="../media/experiments-webhint.msft.png" alt-text="问题面板中的 webhint 反馈" lightbox="../media/experiments-webhint.msft.png":::

此实验默认打开。


<!-- ====================================================================== -->

## <a name="show-issues-in-elements"></a>在元素中显示问题
<!-- present in 96, 98 -->

启用此实验，在"元素"工具的 **"DOM"** 视图中查看 HTML 下的 **语法** 错误。 有关详细信息，请参阅 [元素工具 中的波浪下划线突出显示代码问题和改进](../whats-new/2021/04/devtools.md#wavy-underlines-highlight-code-issues-and-improvements-in-elements-tool)。

<!-- ====================================================================== -->
## Enable Composited Layers in 3D View
<!-- present in 96, 98 -->

您可以将 Layers 与 z 索引和文档对象模型一起可视化 (DOM) 。 为了获得全面的视觉调试体验，现在已将 3D View 和复合层组合到一起。

此功能可帮助你进行调试，而无需频繁切换上下文。 减少上下文切换可解决开发人员的一个主要问题。 此功能可明确您编写的代码对 Web 应用有何影响。

若要使用 **复合层**：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  按 `Esc` 以显示 **"箱"。**

1.  在 **"箱"** 上，选择 **3D View** 工具。

1.  打开“**复合层**”窗格。

1.  此时将显示应用的所有绘制层。  使用你自己的 Web 应用试用此功能。

:::image type="content" source="../media/experiments-layers.msft.png" alt-text="复合层窗格" lightbox="../media/experiments-layers.msft.png":::

此实验默认打开。


<!-- ====================================================================== -->
## Enable Network Console
<!-- present in 96, 98 -->

**网络控制台**是试验通过 HTTP 提出综合网络请求的工作主题。  可以使用网络 **控制台实验** 发送 Web API 请求。

若要使用 **网络控制台**：

1.  [打开 DevTools](../open/index.md)。  例如，在 `Ctrl` + `Shift` + `I` macOS (上的 Windows/Linux) 或 (`Command` + `Option` + `I` 按) 。

1.  打开“**网络**”窗格。

1.  右键单击要更改和重新发送的网络请求，然后选择"编辑和**重播"。**

1.  在 **网络控制台中**，编辑网络请求信息。

1.  单击**发送**。

:::image type="content" source="../media/network-network-console.msft.png" alt-text="控制台工具箱中的网络控制台" lightbox="../media/network-network-console.msft.png":::


<!-- ====================================================================== -->
## <a name="focus-mode"></a>焦点模式

焦点模式实验提供了一 **个活动**栏，它是一个紧凑的水平或垂直工具栏，可使 DevTools UI 保持干净，并且适用于较小的窗口。  将当前主工具固定到活动栏。

:::image type="content" source="../media/experimental-features/focus-mode.png" alt-text="焦点模式，包括活动栏。":::

另请参阅 [存储库的 DevTools：](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/main/DevTools/FocusMode/explainer.md) 焦点模式 `MSEdgeExplainers` UI。


<!-- ====================================================================== -->
## <a name="devtools-tooltips"></a>DevTools 工具提示
<!-- present in 96, 98 -->

启用此实验可查看 DevTools 中所有不同工具和窗格的工具提示。 有关详细信息，请参阅了解[包含信息性工具提示的 DevTools。](../whats-new/2021/04/devtools.md#learn-about-devtools-with-informative-tooltips)


<!-- ====================================================================== -->
## <a name="detached-elements"></a>分离的元素
<!-- present in 96, 98 -->

<!-- maintainers: see notes about this experiment, in the list of experiments which are turned on by default, at top of article -->

Web 应用程序中的内存泄漏可能难以查找和修复。

DevTools Microsoft Edge分离的元素面板可帮助调查和解决内存泄漏的常见源。 ****

当应用程序的 JavaScript 代码在内存中保留数量不断增加的对象时，会发生内存泄漏。 JavaScript 代码应释放这些对象，以便浏览器可以重用内存空间。

有关详细信息，请参阅使用分离的元素工具 [调试 DOM 内存泄漏](../memory-problems/dom-leaks.md)


<!-- ====================================================================== -->
## <a name="vs-code-themes-for-the-devtools"></a>VS Code开发工具的主题
<!-- present in 96, 98 -->
<!-- preserve literal UI string, including "VS" & "the" -->

若要在 devTools Visual Studio主题，请VS Code**开发工具实验的主题**。 有关详细信息，请参阅向 [DevTools 应用颜色主题](../customize/theme.md)。


<!-- ====================================================================== -->
## <a name="open-source-files-in-visual-studio-code"></a>在 Visual Studio Code 中的打开源文件
<!-- present in 96, 98 -->

实验**中的开放源文件**Visual Studio Code源工具的代码编辑器替换为用于编辑Visual Studio Code文件的代码编辑器。 打开此实验时，开发人员工具会检测何时编辑本地文件，并提示你选择一个用作工作区的文件夹。

选择要用作工作区的文件夹时，在 DevTools 中选择指向文件的任何链接将在 Visual Studio Code。  在早期版本的 Microsoft Edge 中，此操作在 DevTools 中的源工具的代码编辑器中打开文件。

:::image type="content" source="../media/experiment-sources-in-code-editor-open.msft.png" alt-text="在&quot;样式&quot;工具中选择文件链接将打开Visual Studio Code" lightbox="../media/experiment-sources-in-code-editor-open.msft.png":::

现在，你在 DevTools 中执行的任何编辑都更改硬盘上的文件，并实时与Visual Studio Code。 可以在打开数据源中的源文件中阅读有关[Visual Studio Code。](../sources/opening-sources-in-vscode.md)


<!-- ====================================================================== -->
<!-- >> [!WARNING]
> These experiments are particularly unstable. Enable at your own risk. -->


<!-- ====================================================================== -->
<!-- ## Ignore List for JavaScript frames on Timeline
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Input events on Timeline overview -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Live heap profile -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Sampling heap profiler timeline -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Enable keyboard shortcut editor -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- ## Enable dynamic Welcome content -->
<!-- present in 96, 98 -->

<!-- Needs content. -->


<!-- ====================================================================== -->
<!-- todo: move these sections into regular articles
## Previously Experimental features which are now regular features

These features have been promoted from experimental to regular features, and have been removed from **Settings** > **Experiments**.

*  [Turn on new CSS grid debugging features](../css/grid.md) - removed from experimental status starting with Microsoft Edge 89.

*  [Match keyboard shortcuts from Microsoft Visual Studio Code](../customize/shortcuts.md#match-keyboard-shortcuts-from-visual-studio-code) - removed from experimental status starting with Microsoft Edge 86.

*  [Turn on support to move tabs between panels](../customize/index.md) - removed from experimental status starting with Microsoft Edge 85.

*  [3D View](../3d-view/index.md) - removed from experimental status starting with Microsoft Edge 83.

*  The items in the following subsections.

### Enable + button tab menus to open more tools

This experiment started with Microsoft Edge version 89, and is a regular feature as of version 94.

You can now open more tools using the new **More Tools** (![The 'More Tools' icon.](../media/more-tools-icon-light-theme.png)) icon.  After you turn on the **Enable + button tab menus to open more tools** experiment and reload DevTools, a plus sign (![The 'More Tools' icon.](../media/more-tools-icon-light-theme.png)) appears to the right of the tab group at the top of DevTools.  To display a list of other tools that you can add to the tab bar, click the **More Tools** (![The 'More Tools' icon.](../media/more-tools-icon-light-theme.png)) icon.

:::image type="content" source="../media/experiments-more-tools-button.msft.png" alt-text="More Tools in the top pane." lightbox="../media/experiments-more-tools-button.msft.png":::

### Enable Welcome tab

The Welcome tab was an experiment starting with Microsoft Edge version 89. It is a regular feature as of version 94.

This experiment replaces the **What's New** tool with the new **Welcome** tool.  It displays a refreshed design for the following content.

*   Links to developer docs
*   Latest features
*   Release notes
*   Option to contact the Microsoft Edge DevTools team

The **Welcome** tool opens automatically after each update to Microsoft Edge.  To prevent the display of the **Welcome** tool after each update, clear the checkbox next to **Open tab after each update** under the **Welcome** tool title.

:::image type="content" source="../media/experiments-welcome.msft.png" alt-text="Welcome tool" lightbox="../media/experiments-welcome.msft.png":::

### Enable new CSS Flexbox debugging features

This was an experiment starting with Microsoft Edge version 89, and is a regular feature as of version 94.

This feature provides many new visualizations to help you debug CSS Flexbox layouts.

#### Displaying persistent overlays on Flexbox layouts with the Inspect tool

The **Inspect** tool provides a quick way to identify and visualize CSS Flexbox layouts in a website by hovering on them with the mouse.  Select the **Inspect** (![Inspect](../media/inspect-icon.msft.png)) icon in the top-left corner of DevTools.  Then, while debugging the website, hover on a flex container to display outlines around the flex container.

:::image type="content" source="../media/flexbox-hover.msft.png" alt-text="Display Flexbox containers with the Inspect tool" lightbox="../media/flexbox-hover.msft.png":::

#### Displaying persistent overlays on Flexbox layouts

In Microsoft Edge version 89 or later, the CSS Flexbox feature offers the option to turn on persistent overlays on Flexbox layouts.  Persistent overlays provide the following benefits:
*   Persistent overlays remain visible on the webpage as you scroll, move your mouse, and use other features of DevTools.
*   Multiple persistent overlays can be used at the same time, to allow you to review several Flexbox layouts at once.
*   Persistent overlays offer color configuration options.

To toggle persistent overlays on Flexbox layout, do either of the following:
*   Select the **Flexbox** oval icon next to any Flexbox container displayed in the DOM tree of the **Elements** tool.
*   Open the new **Layout** panel located in the **Elements** tool, and select the checkbox next to each Flexbox container you want to highlight.

:::image type="content" source="../media/flexbox-overlay.msft.png" alt-text="Flex icons and Layout panel in DevTools" lightbox="../media/flexbox-overlay.msft.png":::

#### Configuring persistent overlays

To configure options for persistent overlays for CSS grids or Flexbox layouts, use the **Layout** pane.  The **Layout** pane is located in the **Elements** tool next to the **Styles** and **Computed** panes.

:::image type="content" source="../media/flexbox-layout.msft.png" alt-text="Layout panel" lightbox="../media/flexbox-layout.msft.png":::
-->
