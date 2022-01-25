---
title: DevTools 中的新增功能 (Microsoft Edge 92)
description: “更多工具”按钮、开始使用 DevTools 扩展的上下文文档、对控制台中屏幕阅读器的增强支持等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.localizationpriority: high
ms.date: 06/02/2021
ms.openlocfilehash: 4b13b2322888ea659a8e9db170f9882c2b38b568
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318714"
---
# <a name="whats-new-in-devtools-microsoft-edge-92"></a>DevTools 中的新增功能 (Microsoft Edge 92)

[!INCLUDE [contact DevTools team note](../../includes/edge-whats-new-note.md)]

> [!TIP]
> **Microsoft Build 2021**会议于 5 月 25-27 日召开。  下面是来自 Build 关于 DevTools 最新消息的视频：[Microsoft Edge｜平台现状](https://www.youtube.com/watch?v=sU0WRZ0kkNo) - Microsoft Edge 为开发人员提供了具有吸引力和一致性的平台。  随着旧版浏览器逐步退出支持，Edge 即将成为 Microsoft 在 Windows 10 或更高版本中支持的唯一浏览器。  加入我们，了解有关 Edge 平台、工具和 Web 应用的最新信息。


<!-- ====================================================================== -->
## <a name="the-close-button-is-no-longer-hidden-when-devtools-is-narrow"></a>当 DevTools 变窄时，“关闭”按钮不再隐藏

<!-- Title: DevTools is now easier to close -->
<!-- Subtitle: The Close button in DevTools is always displayed, even when DevTools is docked to the right and the DevTools viewport is narrow. -->

在 Microsoft Edge 版本 91 或更早版本中，当 DevTools 视区较窄时，不会显示用于关闭 DevTools 的**关闭**按钮。  在 Microsoft Edge 版本 92 中，无论 DevTools 视区宽度如何，DevTools 中的**关闭**按钮始终存在。

:::image type="complex" source="../../media/2021/05/close-devtools-button-always-displayed.msft.png" alt-text="即使视区较窄，现在也存在“关闭”DevTools 按钮" lightbox="../../media/2021/05/close-devtools-button-always-displayed.msft.png":::
   即使视区较窄， 现在也存在**关闭** DevTools 按钮
:::image-end:::


<!-- ====================================================================== -->
## <a name="add-tools-quickly-with-the-new-more-tools-button"></a>使用新的“更多工具”按钮快速添加工具

<!-- Title: Add tools quickly with the new More Tools button -->
<!-- Subtitle: Learn about a new convenient way to open tools in Microsoft Edge DevTools. -->

有一种在 Microsoft Edge DevTools 中打开更多工具的新方法：**更多工具** (`+`) 菜单。 **更多工具**菜单显示在主面板的工具栏和抽屉的工具栏中。 从**更多工具**菜单中选择工具会将该工具添加到工具栏。

若要将任一工具栏中的选项卡重新排序，请选择并拖动选项卡。

**更多工具**菜单在 Microsoft Edge 版本 89 中作为试验提供，始终存在。

:::image type="complex" source="../../media/2021/05/more-tools-button.msft.png" alt-text="上部工具栏和抽屉工具栏中的“更多工具”按钮" lightbox="../../media/2021/05/more-tools-button.msft.png":::
   上部工具栏和抽屉工具栏中的“**更多工具**”按钮
:::image-end:::

:::image type="complex" source="../../media/2021/05/more-tools-menu.msft.png" alt-text="“更多工具”菜单" lightbox="../../media/2021/05/more-tools-menu.msft.png":::
   “**更多工具**”菜单
:::image-end:::


<!-- ====================================================================== -->
## <a name="improvements-for-hovering-selecting-and-closing-tools"></a>悬停、选择、关闭工具的改进

<!-- Title: Improvements to tab interactions -->
<!-- Subtitle: Interactions related to hovering, selecting, and closing tools are more predictable. -->

已重新格式化每个工具的选项卡，以减少意外关闭工具的可能性。  在主工具栏和抽屉工具栏中的每个选项卡上，我们添加了：
*  选项卡周围的间距。
*  选项卡中关闭 (`x`) 按钮周围的间距。
*  将鼠标悬停在选项卡上方时的背景色。
*  选项卡的关闭 (`x`) 按钮的工具提示。
*  选项卡的关闭 (`x`) 按钮的对比度更高。

例如，当你在**性能**工具中并将鼠标悬停在**网络**工具的选项卡上时，这些改进有助于防止意外关闭**网络**工具。

重新格式化之前的选项卡:

:::image type="content" source="../../media/2021/05/hovering-on-tool-tab-before.msft.png" alt-text="重新格式化之前的选项卡" lightbox="../../media/2021/05/hovering-on-tool-tab-before.msft.png":::

重新格式化后的选项卡:

:::image type="content" source="../../media/2021/05/hovering-on-tool-tab-after.msft.png" alt-text="重新格式化后的选项卡" lightbox="../../media/2021/05/hovering-on-tool-tab-after.msft.png":::

这些改进尤其适用于本地化 DevTools 的用户，在这些用户中，选项卡可能更窄且更易于意外关闭。

:::image type="complex" source="../../media/2021/05/hovering-reduced-chance-of-closing-tab.msft.png" alt-text="具有窄选项卡的本地化 DevTools" lightbox="../../media/2021/05/hovering-reduced-chance-of-closing-tab.msft.png":::
   具有窄选项卡的本地化 DevTools
:::image-end:::

我们还通过向主工具栏和抽屉工具栏添加“[更多工具菜单](#add-tools-quickly-with-the-new-more-tools-button)”，简化了重新添加已关闭的工具的操作。


<!-- ====================================================================== -->
## <a name="better-support-for-screen-readers-in-the-console"></a>更好地支持控制台中的屏幕阅读器

<!-- Title: Better screen reader support in the Console -->
<!-- Subtitle: Assistive technologies can now announce autocomplete suggestions and evaluated expressions in the Console. -->

在 Microsoft Edge 版本 92 之前，在**控制台**中，屏幕阅读器等辅助技术未公布自动完成建议或已评估表达式的结果。 已修复此问题。

在**控制台**中，屏幕阅读器现在会播报当前选择的自动完成建议:

:::image type="content" source="../../media/2021/05/screen-reader-support-in-console-autocomplete.msft.png" alt-text="在控制台中，屏幕阅读器现在会播报当前选择的自动完成建议" lightbox="../../media/2021/05/screen-reader-support-in-console-autocomplete.msft.png":::

在**控制台**中，屏幕阅读器现在将播报计算表达式的结果:

:::image type="content" source="../../media/2021/05/screen-reader-support-in-console-evaluated-expression.msft.png" alt-text="在控制台中，屏幕阅读器现在将播报计算表达式的结果" lightbox="../../media/2021/05/screen-reader-support-in-console-evaluated-expression.msft.png":::


<!-- ====================================================================== -->
## <a name="source-order-viewer"></a>源订单查看器

<!--  Title: Source Order Viewer -->
<!--  Subtitle: The new Source Order Viewer displays numbers on the webpage indicating the order of page elements in the source file, independently of how the page sections are positioned by CSS. -->

现在可以查看呈现的网页上覆盖的源元素的顺序，以便更好地进行辅助功能检查。

HTML 文档中的内容顺序对于搜索引擎优化和辅助功能非常重要。  CSS 允许开发人员创建其屏幕顺序与 HTML 源文档中的顺序不同的内容。  这是一个辅助功能问题，因为屏幕阅读器用户可能会有困惑的体验。

:::image type="complex" source="../../media/2021/05/source-order-viewer.msft.png" alt-text="激活源订单查看器将源中的元素顺序显示为页面上的覆盖层" lightbox="../../media/2021/05/source-order-viewer.msft.png":::
   激活**源订单查看器** 将源中的元素顺序显示为页面上的覆盖层
:::image-end:::

有关详细信息，请导航到[使用源订单查看器测试键盘支持](../../../accessibility/test-tab-key-source-order-viewer.md)。

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1094406](https://crbug.com/1094406)。


<!-- ====================================================================== -->
## <a name="user-agent-client-hints-for-devices-in-the-network-conditions-tab"></a>网络条件选项卡中设备的用户代理客户端提示

<!--  Title: User-Agent Client Hints -->
<!--  Subtitle: Access information about a user's browser in an ergonomic way that preserves privacy. -->

用户代理客户端提示现在应用于**网络条件**工具的**用户代理**字段中的设备。  用户代理客户端提示是客户端提示 API 的新扩展，使你能够以保留隐私的人体工学方式访问有关用户浏览器的信息。

:::image type="complex" source="../../media/2021/05/user-agent.msft.png" alt-text="用户代理" lightbox="../../media/2021/05/user-agent.msft.png":::
   用户代理
:::image-end:::

有关详细信息，请导航到[用户代理客户端提示](../../../../web-platform/user-agent-guidance.md#user-agent-client-hints)。

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1174299](https://crbug.com/1174299)。


<!-- ====================================================================== -->
## <a name="microsoft-edge-developer-tools-for-visual-studio-code-version-118"></a>适用于 Visual Studio Code 版本 1.1.8 的 Microsoft Edge 开发人员工具

[适用于 Visual Studio Code 的 Microsoft Edge 开发人员工具](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)针对 Microsoft Visual Studio Code 的扩展版本 1.1.8 自上一个版本以来有以下更改。  Microsoft Visual Studio Code 会自动更新扩展。  要手动更新到版本 1.1.8，请导航至“[手动更新扩展](https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually)”。

你可以在 [vscode-edge-devtools GitHub repo](https://github.com/microsoft/vscode-edge-devtools) 上提交问题并参与扩展的改进。

### <a name="in-context-documentation-and-ui-to-make-it-easier-to-use-the-devtools-extension"></a>通过上下文文档和 UI 更轻松地使用 DevTools 扩展

<!-- Title: In-context documentation and UI make it easier to get started using the Developer Tools extension -->
<!-- Subtitle: The Microsoft Edge Developer Tools for Visual Studio Code extension now presents helpful text, buttons, and links, and opens a documentation page with guidance on how to get started. -->

[针对 Visual Studio Code 的 Microsoft Edge 开发人员工具](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)版本 1.1.8 现在提供了更简单的方法来启动新的 Microsoft Edge 实例，方法是提供说明、按钮、链接、文档页作为指南。

*  在 Visual Studio Code的“**活动栏**”中选择“**Microsoft Edge 工具**”按钮时，“**Microsoft Edge 工具：目标**”面板现在会显示说明性文本、按钮和链接，而不是空白面板。

*  从 Visual Studio Code 中打开 Microsoft Edge 的新实例时，Microsoft Edge 现在会显示一个起始页，说明如何使用开发人员工具扩展，而不是空白页。

*  **Microsoft Edge 工具：目标**面板现在具有**生成 launch.json**按钮和说明，以帮助启动项目以在 Microsoft Edge 中进行调试。

有关详细信息，请导航至[使用工具](https://microsoft.github.io/vscode-edge-devtools/using.html)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

[!INCLUDE [contact DevTools team note](../../includes/chromium-whats-new-note.md)]


### <a name="css-grid-editor"></a>CSS 网格编辑器

现在可以使用新的 CSS 网格编辑器预览和创作 CSS 网格布局。

当页面上的 HTML 元素 `display: grid` 或 `display: inline-grid` 应用到该元素时，**样式**选项卡中会显示其旁边的网格图标。单击网格图标以显示或隐藏 CSS 网格编辑器。 在 CSS 网格编辑器中，选择任何图标（如 `justify-content: space-around`）以预览呈现页面中的布局。  弹性布局的工作方式类似。

:::image type="complex" source="../../media/2021/05/css-grid-editor.msft.png" alt-text="CSS 网格编辑器" lightbox="../../media/2021/05/css-grid-editor.msft.png":::
   CSS 网格编辑器
:::image-end:::

<!-- screenshot uses https://jec.fyi -->

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1203241](https://crbug.com/1203241)。


### <a name="support-for-const-redeclarations-in-the-console"></a>在控制台中支持常量重新声明

除了现有的 `let` 和 `class` 重新声明外，控制台现在支持在单独的 REPL 脚本（例如在控制台中运行语句时）重新声明 `const` 变量。  借助此支持，可以在不刷新页面的情况下试验 `const` 变量的不同声明。  以前，如果重新声明了 `const` 绑定，则 DevTools 会引发语法错误。

请参阅以下示例。 `const` 在单独的 REPL 脚本中支持重新声明（请参阅变量 `a`）。  请注意，设计上不支持以下方案：

*  `const` REPL 脚本中不允许重新声明页脚本。
*  `const` 不允许在同一 REPL 脚本中重新声明（请参阅变量 `b`）。

:::image type="complex" source="../../media/2021/05/support-for-const-redeclaration.msft.png" alt-text="控制台中允许重新声明常量变量" lightbox="../../media/2021/05/support-for-const-redeclaration.msft.png":::
   控制台中允许重新声明常量变量
:::image-end:::

若要了解如何运行单个 REPL 脚本或多行 REPL 脚本，请导航到[在控制台中运行JavaScript](../../../console/console-javascript.md)。

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1076427](https://crbug.com/1076427)。


### <a name="new-shortcut-to-view-iframe-details"></a>查看 iframe 详细信息的新快捷方式

若要快速查看`iframe`详细信息，现在可以在**元素**工具中右键单击`iframe`元素，然后选择**显示 iframe 详细信息**。

:::image type="complex" source="../../media/2021/05/show-iframe-details.msft.png" alt-text="iframe 详细信息视图" lightbox="../../media/2021/05/show-iframe-details.msft.png":::
   iframe 详细信息视图
:::image-end:::

这将显示**应用程序**工具中有关`iframe`的详细信息。  在**应用程序**工具中，可以检查文档详细信息、安全和隔离状态、权限策略等，以调试潜在问题。

:::image type="complex" source="../../media/2021/05/show-iframe-details-application-tool.msft.png" alt-text="应用程序工具中的帧详细信息" lightbox="../../media/2021/05/show-iframe-details-application-tool.msft.png":::
   **应用程序**工具中的帧详细信息
:::image-end:::

<!-- demo page: https://wolfib.github.io/web-demos/ esp https://wolfib.github.io/web-demos/jsIframe.html -->

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1192084](https://crbug.com/1192084)。


### <a name="enhanced-cors-debugging-support"></a>增强的 CORS 调试支持

跨源资源共享(CORS)错误现在显示在**问题**选项卡中。 CORS 错误有多种潜在原因。  单击以展开每个问题以了解潜在原因和解决方案。

:::image type="complex" source="../../media/2021/05/cors-debugging-support.msft.png" alt-text="“问题”选项卡中的 CORS 问题" lightbox="../../media/2021/05/cors-debugging-support.msft.png":::
   “问题”选项卡中的 CORS 问题
:::image-end:::

<!-- screenshot uses http://cors-errors.glitch.me -->

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1141824](https://crbug.com/1141824)。


### <a name="renamed-xhr-filter-to-fetchxhr"></a>已将 XHR 筛选器重命名为 Fetch\/XHR

在**网络**工具中，**XHR**筛选器现已重命名为 **Fetch/XHR**。 此更改更清楚地表明，此筛选器同时包含 `XMLHttpRequest` 和 `Fetch` API 网络请求。

:::image type="complex" source="../../media/2021/05/fetch-xhr.msft.png" alt-text="网络工具现在显示 Fetch/XHR 而不是 XHR" lightbox="../../media/2021/05/fetch-xhr.msft.png":::
   **网络**工具现在显示 **Fetch/XHR**，而不是 **XHR**
:::image-end:::

有关详细信息，请导航至：
*  [XMLHttpRequest spec](https://xhr.spec.whatwg.org)
*  [提取规范](https://fetch.spec.whatwg.org)

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1201398](https://crbug.com/1201398)。


### <a name="filter-wasm-resource-type-in-the-network-tool"></a>在网络工具中筛选 Wasm 资源类型

在**网络**工具中，现在可以选择新的 **Wasm** 筛选器来筛选 WebAssembly 网络请求。

:::image type="complex" source="../../media/2021/05/wasm-network-requests.msft.png" alt-text="按 Wasm 筛选" lightbox="../../media/2021/05/wasm-network-requests.msft.png":::
   按 Wasm 筛选
:::image-end:::

<!-- screenshot uses http://memory-inspector.glitch.me/demo-wasm.html -->

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1103638](https://crbug.com/1103638)。


### <a name="compute-intersections-are-now-included-in-the-performance-tool"></a>计算交集现在包含在性能工具中

在**性能**工具中，DevTools 现在在火形图中显示**计算交集**。 这些更改有助于识别交集观察程序事件并调试交集观察程序的潜在性能开销。

:::image type="complex" source="../../media/2021/05/compute-intersections-in-perf-tool.msft.png" alt-text="性能工具中的计算交集" lightbox="../../media/2021/05/compute-intersections-in-perf-tool.msft.png":::
   **性能**工具中的计算交集
:::image-end:::

<!-- screenshot uses https://googlechrome.github.io/samples/intersectionobserver -->

有关交集观察程序的详细信息，请导航至[信任良好，观察效果更好：交集观察程序 v2](https://web.dev/intersectionobserver-v2)。  有关使用火形图的信息，请导航到[分析性能记录](../../../evaluate-performance/reference.md#analyze-a-performance-recording)。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1199137](https://crbug.com/1199137)。


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download)作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-92)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
