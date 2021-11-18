---
description: Microsoft Edge DevTools 中的最新试验功能
title: 试验功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/16/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools, 试验
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
- Match keyboard shortcuts in the DevTools to Microsoft Visual Studio Code
- Edit keyboard shortcuts for any action in the DevTools
- Turn on new CSS grid debugging features
- 'Emulation: Support dual screen mode'
ms.openlocfilehash: bd538c65daa6b1da48da699ca503875e41b1280b
ms.sourcegitcommit: 9c31ae7307cf595a2ac2e655524e187777714765
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2021
ms.locfileid: "12184041"
---
# <a name="experimental-features"></a>试验功能

Microsoft Edge DevTools 提供对仍在开发中的试验功能的访问权限。  可以在发布每个功能之前试用 [这些功能并提供](../contact.md) 反馈。

组织的所有频道Microsoft Edge实验性功能。  可以使用以下方法获取最新的实验Microsoft Edge Canary 渠道。  本文仅介绍所选实验功能。  有关完整列表，请参阅****  >  **** DevTools 设置实验"页面。


<!-- ====================================================================== -->
## <a name="experimental-features-which-are-turned-on-by-default"></a>默认情况下打开的实验性功能

自 Microsoft Edge 96 起，默认情况下会启用以下实验功能。  这意味着可以马上使用这些功能，而无需更改任何设置。  如果需要，可以关闭这些默认实验功能。

<!-- listed in order of the Settings > Experiments pane -->
*  源订单查看器
*  启用前向缓存调试支持
*  [Emulation: Support dual screen mode](../device-mode/dual-screen-and-foldables.md)从 90 开始，默认Microsoft Edge打开。
*  启用实验性隐藏问题菜单
*  在 \<length\> "样式"窗格中启用 CSS 创作工具
*  Enable webhint
*  在元素中显示问题
*  Enable Composited Layers in 3D View
*  DevTools 工具提示
*  VS Code开发工具的主题 <!-- literal checkbox label -->
*  在 Visual Studio Code 中的打开源文件
*  启用键盘快捷方式编辑器 - 默认从 [Edit keyboard shortcuts for any action in the DevTools](../customize/shortcuts.md#edit-the-keyboard-shortcut-for-a-devtools-action) 89 Microsoft Edge打开。

<!-- *  Detached Elements - in 96 this checkmark is only present when a corpnet account is hooked up -->

<!-- *  Enable dynamic Welcome content - turned on by default in v97 & v98, not v96 -->


<!-- ====================================================================== -->
## <a name="turning-on-experimental-features"></a>打开实验性功能

若要打开或关闭实验性功能，Microsoft Edge：

1.  [打开 DevTools](../open/index.md)。  为此，在"Microsoft Edge"中，设置**更多** (...) >**工具**  >  **"。**

1.  打开[devTools](../customize/index.md#settings)设置窗格。  为此，请选择 **"设置 (** 齿轮) 图标。

1.  在"实验"窗格**设置，** 选择"实验 **"** 部分。

    :::image type="content" source="../media/experiments-devtools.msft.png" alt-text="设置中的试验页面" lightbox="../media/experiments-devtools.msft.png":::

1.  在 **实验** 页面上，滚动浏览所有可用实验功能的列表，并选中要测试的每个功能旁边的复选框。  某些实验默认打开。

1.  选择右上角的**X**以关闭**设置。**

1.  选择" **重新加载 DevTools"** 按钮。

> [!NOTE]
> 实验性功能会不断更新，并且可能会导致性能问题。  若要关闭试验功能，请打开“**试验**”页面并清除要关闭的试验功能的复选框。


<!-- ====================================================================== -->
<!-- ====================================================================== -->
<!-- Keep h2 sections in same order as Microsoft Edge DevTools > Experiments page. -->
<!-- Include an h2 section for every checkbox that's in Microsoft Edge DevTools > Experiments page, many of them commented out.  Keep in mind which version the rendered page targets.  If a checkbox has been removed, move its section to the bottom section of this page. -->


<!-- ====================================================================== -->
<!-- ## Allow extensions to load custom stylesheets -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Capture node creation stacks -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Automatically pretty print in the Sources Panel -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Protocol Monitor -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Show CSP Violations view -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Record coverage while performance tracing -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Show option to take heap snapshot where globals are treated as root -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
## <a name="source-order-viewer"></a>源订单查看器
<!-- present in 96, 98 -->

**Source Order Viewer** 是显示网页源中元素顺序的试验。  屏幕显示顺序可以不同于源的顺序，这会使屏幕阅读器和键盘用户混淆。  使用 **Source Order Viewer** 试验查找屏幕显示顺序和源顺序之间的差异。

若要使用 **Source Order Viewer** ：
1.  打开“**元素**”工具。
1.  在" **样式"选项卡** 的右侧，选择 **"辅助功能"** 选项卡。
1.  在部分 **Source Order Viewer** 下，选中" **显示源订单"** 复选框。
1.  突出显示任何 HTML 元素，以显示该网页源中顺序的覆盖。

:::image type="content" source="../media/experiments-source-order-viewer.msft.png" alt-text=":::no-loc (源订单查看器) ：：： 在辅助功能窗格中" lightbox="../media/experiments-source-order-viewer.msft.png"：：：

此实验从版本 86 Microsoft Edge开始提供，并且默认打开。


<!-- ====================================================================== -->
<!-- ## Enable back-forward cache debugging support -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: event initiators -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: WebGL-based flamechart -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## WebAssembly Debugging: Enable DWARF support -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Emulation: Support dual screen mode -->
<!-- present in 96, 98 -->

<!-- [Emulation: Support dual screen mode](../device-mode/dual-screen-and-foldables.md) -->


<!-- ====================================================================== -->
<!-- ## Enable new Advanced Perceptual Contrast Algorithm (APCA) replacing previous contrast ratio and AA/AAA guidelines -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable full accessibility tree view in the Elements panel -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
## <a name="enable-new-font-editor-tool-within-the-styles-pane"></a>Enable new Font Editor tool within the Styles pane.
<!-- keep period, per literal checkbox label>
<!-- present in 96, 98 -->

现在，可以使用新的可视 [字体编辑器来](../inspect-styles/edit-fonts.md) 编辑字体。  使用它来定义字体和字体特征。  可视 **字体编辑器** 可帮助您执行以下操作：

*   在不同字体属性的单位之间切换
*   在不同字体属性的关键字之间切换
*   转换单位
*   生成准确的 CSS 代码

若要使用新的可视化**字体编辑器：**
1.  打开“**元素**”工具。
1.  打开“**样式**”窗格。
1.  选择" **字体编辑器"** 图标。

有关新的可视字体编辑器 **的详细信息**，请参阅 [DevTools](../inspect-styles/edit-fonts.md)中的样式窗格中编辑 CSS 字体样式和设置。

:::image type="complex" source="../media/font-editor-open.msft.png" alt-text="突出显示可视内容字体编辑器窗格" lightbox="../media/font-editor-open.msft.png":::
   突出显示可视内容**字体编辑器**窗格
:::image-end:::

此实验从版本 89 Microsoft Edge开始提供。


<!-- ====================================================================== -->
<!-- ## Enable automatic contrast issue reporting via the Issues Panel -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable experimental cookie features -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable experimental hide issues menu -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Allow grouping and hiding of issues by IssueKind -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable Reporting API panel in the Application panel -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable CSS \<length\> authoring tool in the Styles pane (https://goo.gle/length-feedback) -->
<!-- present in 96, 97, 98 -->
<!-- in 97 & 98 the label is shorter: -->
<!-- ## Enable CSS \<length\> authoring tool in the Styles pane -->


<!-- ====================================================================== -->
<!-- ## Log DevTools uncaught exceptions to Console -->
<!-- present in 96, 98 -->


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

此实验从版本 85 Microsoft Edge开始提供，并且默认打开。


<!-- ====================================================================== -->
<!-- ## Show issues in Elements -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
## Enable Composited Layers in 3D View
<!-- present in 96, 98 -->

您可以将 Layers 与 z 索引和文档对象模型一起可视化 (DOM) 。  此功能可帮助你进行调试，而无需频繁切换上下文。  你发现减少上下文切换是一个主要的痛点。  不能始终弄清楚你编写的代码对 Web 应用有何影响。  为了获得全面的视觉调试体验，现在已将 3D View 和复合层组合到一起。

若要使用**复合层**，请完成以下步骤。

1.  在 **"箱"** 上，选择 **3D View** 工具。
1.  打开“**复合层**”窗格。
1.  此时将显示应用的所有绘制层。  使用你自己的 Web 应用试用此功能。

:::image type="content" source="../media/experiments-layers.msft.png" alt-text="复合层窗格" lightbox="../media/experiments-layers.msft.png":::

此实验从版本 87 Microsoft Edge开始，并且默认打开。


<!-- ====================================================================== -->
## Enable Network Console
<!-- present in 96, 98 -->

**网络控制台**是试验通过 HTTP 提出综合网络请求的工作主题。  可以使用网络 **控制台实验** 发送 Web API 请求。

若要使用**网络控制台**，请完成以下步骤。

1.  打开“**网络**”窗格。
1.  查找要更改和重新发送的网络请求。
1.  打开上下文菜单 (右键单击") "，然后选择"编辑**和重播"。**
1.  当**网络控制台**打开时，编辑网络请求信息。
1.  选择 **"发送"。**

:::image type="content" source="../media/network-network-console.msft.png" alt-text="控制台工具箱中的网络控制台" lightbox="../media/network-network-console.msft.png":::

此实验从版本 85 Microsoft Edge开始提供。


<!-- ====================================================================== -->
## <a name="focus-mode"></a>焦点模式

<!-- present in 96, 98 -->

焦点模式实验提供了一 **个活动**栏，它是一个紧凑的水平或垂直工具栏，可使 DevTools UI 保持干净，并且适用于较小的窗口。  将当前主工具固定到活动栏。

:::image type="content" source="../media/experimental-features/focus-mode.png" alt-text="焦点模式，包括活动栏。":::

另请参阅 [存储库的 DevTools：](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/main/DevTools/FocusMode/explainer.md) 焦点模式 `MSEdgeExplainers` UI。


<!-- ====================================================================== -->
<!-- ## DevTools Tooltips -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Detached Elements -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## VS Code themes for the DevTools -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
## <a name="open-source-files-in-visual-studio-code"></a>在 Visual Studio Code 中的打开源文件
<!-- present in 96, 98 -->

实验**中的开放源文件**Visual Studio Code源工具的代码编辑器替换为用于编辑Visual Studio Code文件的代码编辑器。  打开此实验时，开发人员工具会检测何时编辑本地文件，并提示你选择一个用作工作区的文件夹。

选择要用作工作区的文件夹后，在 DevTools 中选择某个文件的任何链接将在 Visual Studio Code 中打开该文件，而不是在 DevTools 中源工具的代码编辑器中打开。

:::image type="content" source="../media/experiment-sources-in-code-editor-open.msft.png" alt-text="在&quot;样式&quot;工具中选择文件链接将打开Visual Studio Code" lightbox="../media/experiment-sources-in-code-editor-open.msft.png":::

现在，你在 DevTools 中执行的任何编辑都将更改硬盘驱动器上的文件，并实时Visual Studio Code。  有关设置工作区的阅读，请参阅在文件打开[Visual Studio Code。](../sources/opening-sources-in-vscode.md)

此实验从版本 96 Microsoft Edge开始提供。


<!-- ====================================================================== -->
<!-- Microsoft Edge automatically pretty print in the Sources Panel -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ====================================================================== -->
<!-- "WARNING: These experiments are particularly unstable:" -->


<!-- ====================================================================== -->
<!-- ## Ignore List for JavaScript frames on Timeline -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Input events on Timeline overview -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Live heap profile -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Sampling heap profiler timeline -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable keyboard shortcut editor -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: invalidation tracking -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: show all events -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: V8 Runtime Call Stats on Timeline -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Timeline: Replay input events -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ## Enable dynamic Welcome content -->
<!-- present in 96, 98 -->


<!-- ====================================================================== -->
<!-- ====================================================================== -->
## <a name="previously-experimental-features-which-are-now-regular-features"></a>以前作为常规功能的实验性功能

<!-- todo: move these sections into regular articles -->

这些功能已从实验提升为常规功能，并且已从实验**设置**  >  **中删除**。

*  [Turn on new CSS grid debugging features](../css/grid.md)- 从 89 开始从实验Microsoft Edge中删除。

*  [Match keyboard shortcuts from Microsoft Visual Studio Code](../customize/shortcuts.md#match-keyboard-shortcuts-from-visual-studio-code) - removed from Experimental status starting from Microsoft Edge 86.

*  [Turn on support to move tabs between panels](../customize/index.md)- 从实验状态中删除，从 Microsoft Edge 85 开始。

*  [3D View](../3d-view/index.md)- 从实验状态中删除，从 Microsoft Edge 83 开始。

*  以下子节中的项目。

### Enable + button tab menus to open more tools

这是从版本 89 Microsoft Edge的试验，自版本 94 起是一项常规功能。<!-- which release changed this from Experimental?-->

现在，可以使用新的"更多工具"图标**** 打开 `+` () 工具。  打开实验并重新加载 DevTools 后， () 在 **Enable + button tab menus to open more tools** DevTools 顶部的选项卡组右侧显示加号 `+` 。  若要显示可添加到选项卡栏的其他工具的列表，请单击"更多工具" () **** `+` 图标。

:::image type="content" source="../media/experiments-more-tools-button.msft.png" alt-text="顶部窗格中的更多工具。" lightbox="../media/experiments-more-tools-button.msft.png":::

### Enable Welcome tab

这是从版本 89 Microsoft Edge的试验，自版本 94 起是一项常规功能。<!-- which release changed this from Experimental?-->

此试验使用新的**欢迎**工具替换**新增功能**工具。  它显示以下内容的更新设计。

*   指向开发人员文档的链接
*   最新功能
*   发行说明
*   用于联系 Microsoft Edge DevTools 团队的选项

每次更新 Microsoft Edge 后，**欢迎**工具都会自动打开。  若要防止每次更新后显示**欢迎**工具，请清除“**欢迎**”标题下“**每次更新后打开选项卡**”旁边的复选框。

:::image type="content" source="../media/experiments-welcome.msft.png" alt-text="欢迎工具" lightbox="../media/experiments-welcome.msft.png":::


<!-- ====================================================================== -->
### Enable new CSS Flexbox debugging features

这是从版本 89 Microsoft Edge的试验，自版本 94 起是一项常规功能。<!-- which release changed this from Experimental?-->

此功能提供了许多新的可视化效果，可帮助你调试 CSS Flexbox 布局。

#### <a name="displaying-persistent-overlays-on-flexbox-layouts-with-the-inspect-tool"></a>使用 Inspect 工具在 Flexbox 布局上显示永久性覆盖

**检查**工具提供了一种快速识别和可视化网站 CSS 弹性框布局的方法，通过将鼠标悬停该布局上方来实现这一点。  选择 **"检查** (![ 工具 ](../media/inspect-icon.msft.png)) 左上角的"检查项目"图标。  然后，在调试网站时，将鼠标悬停在弹性容器上方以在其周围显示轮廓。

:::image type="content" source="../media/flexbox-hover.msft.png" alt-text="使用检查工具显示弹性框容器" lightbox="../media/flexbox-hover.msft.png":::

#### <a name="displaying-persistent-overlays-on-flexbox-layouts"></a>在 Flexbox 布局上显示永久性覆盖

在 Microsoft Edge版本 89 或更高版本中，CSS Flexbox 功能提供在 Flexbox 布局上打开永久性覆盖的选项。  永久性覆盖具有以下优点：
*   滚动、移动鼠标和使用 DevTools 的其他功能时，持久覆盖层在网页上仍然可见。
*   可以同时使用多个永久性覆盖，以便你可以一次查看多个 Flexbox 布局。
*   持久覆盖层提供颜色配置选项。

若要切换 Flexbox 布局上的永久性覆盖，请执行下列任一操作：
*   选择 **"元素"** 工具的 DOM 树中显示的任何 Flexbox 容器旁边的 Flexbox **椭圆图标** 。
*   打开位于"**元素**"工具中的新布局**** 面板，并选中要突出显示的每个 Flexbox 容器旁边的复选框。

:::image type="content" source="../media/flexbox-overlay.msft.png" alt-text="DevTools 中的弹性图标和布局面板" lightbox="../media/flexbox-overlay.msft.png":::

#### <a name="configuring-persistent-overlays"></a>配置永久性覆盖

若要为 CSS 网格或弹性框布局配置持久覆盖层的选项，请使用“**布局**”窗格。  “**布局**”窗格位于“**样式**”和“**计算**”窗格旁边的“**元素**”工具中。

:::image type="content" source="../media/flexbox-layout.msft.png" alt-text="布局面板" lightbox="../media/flexbox-layout.msft.png":::
