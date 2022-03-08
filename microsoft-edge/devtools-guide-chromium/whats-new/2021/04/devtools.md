---
title: DevTools 中的新增功能 (Microsoft Edge 91)
description: 波浪下划线突出显示了元素工具、服务工作进程更新日程表等中的代码问题。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/06/2021
ms.openlocfilehash: 3e53029e5b441eb33a9677ea1f869e87e320c60e
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431373"
---
<!-- Copyright Jecelyn Yeen

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="whats-new-in-devtools-microsoft-edge-91"></a>DevTools 91 (Microsoft Edge中的新增) 

[!INCLUDE [contact DevTools team note](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="wavy-underlines-highlight-code-issues-and-improvements-in-elements-tool"></a>波浪下划线突出显示元素工具中的代码问题和改进项

<!--  Title: Get code hints in Elements tool  -->
<!--  Subtitle: Wavy underlines like the ones you see in Visual Studio Code now display in the Elements tool.  Underlines alert you to code issues related to accessibility, compatibility, security, performance, and  so on.  -->

在大多数新式 IDE 中，文本下的波浪下划线指示语法错误。   在 Microsoft Edge 版本 91 或更高版本中，波浪下划线显示在 **元素** 工具的 **DOM** 视图中的 HTML 下。  波浪下划线指示与辅助功能、兼容性、性能等相关的代码问题和建议。  若要详细了解如何查看和编辑问题，请参阅 [使用问题工具查找和修复问题](../../../issues/index.md)。

若要打开 **"问题** "工具，并了解有关此问题以及如何修复该问题的更多信息，请执行以下操作：

* 长按 ， `Shift`然后单击波浪下划线。

* 或者，右键单击波浪下划线，然后选择" **在问题中显示"**。

在"元素"工具中选择 **带下划线** 的错误：

:::image type="content" source="../../media/2021/04/elements-iframe-highlight-issues.msft.png" alt-text="在&quot;元素&quot;工具中选择带下划线的错误。" lightbox="../../media/2021/04/elements-iframe-highlight-issues.msft.png":::

在"问题"工具 **中显示错误** 详细信息：

:::image type="content" source="../../media/2021/04/elements-iframe-highlight-issues-focus.msft.png" alt-text="在&quot;问题&quot;工具中显示错误详细信息。" lightbox="../../media/2021/04/elements-iframe-highlight-issues-focus.msft.png":::


<!-- ====================================================================== -->
## <a name="learn-about-devtools-with-informative-tooltips"></a>通过信息丰富的工具提示了解 DevTools

:::image type="icon" source="../../media/2020/06/experimental-tag-14px.msft.png":::

<!--  Title: Learn more about DevTools with DevTools Tooltips  -->
<!--  Subtitle: Informative overlays are now available in the default DevTools interface.  -->

DevTools 工具提示功能可帮助你了解 DevTools 中所有不同的工具和窗格。  若要关闭工具提示，请按 `Esc`。  若要打开工具提示，请执行下列操作之一： 

*  按 `Ctrl`++`Shift``H` (Windows/Linux) 或 (`H` `Cmd`+`Shift`+macOS) 。
*  [打开命令菜单](../../../command-menu/index.md#open-the-command-menu)，然后键入 `tooltips`。
*  选择 **"自定义和控制 DevTools** 工具 () > `...` **帮助** > **""工具提示"**。

此外，如果你打开焦点模式和 [DevTools](../02/devtools.md#group-tools-together-in-focus-mode) 工具提示实验，还可以单击活动栏底部的"切换 **开发** `?` 工具提示 () " **按钮**。

要显示有关如何使用 DevTools 的详细信息，请打开工具提示，然后将鼠标悬停在 DevTools 的每个轮廓区域上。

:::image type="content" source="../../media/2021/04/elements-issues-focus-mode-tooltips.msft.png" alt-text="将鼠标悬停在&quot;问题&quot;工具突出显示区域的任何位置，以显示更多详细信息。" lightbox="../../media/2021/04/elements-issues-focus-mode-tooltips.msft.png":::


<!-- ====================================================================== -->
## <a name="service-worker-update-timeline"></a>服务工作进程更新日程表

<!--todo:  Update the linked [Service Worker improvements](../../../service-workers/index.md) article.  -->

<!--  Title: The tasks associated with your Service Worker  -->
<!--  Subtitle: Debug with Service Worker Update Cycle  -->

在 Microsoft Edge 版本 91 或更高版本中，如果你是渐进式 Web 应用或服务工作进程开发人员，请在 **应用程序** 工具中将服务工作进程的更新生命周期显示为日程表。  此功能可帮助你了解服务工作进程在以下每个阶段花费的时间。

*  **安装**
*  **等待**
*  **激活**

:::image type="content" source="../../media/2021/04/application-service-workers-update-cycle-version-73-focus.msft.png" alt-text="查看服务工作者的更新周期中的时间线。" lightbox="../../media/2021/04/application-service-workers-update-cycle-version-73-focus.msft.png":::

有关服务工作者的生命周期详细信息，请参阅 [服务工作线程生命周期](../../../../progressive-web-apps-chromium/how-to/service-workers.md#the-service-worker-lifecycle)。  有关在 DevTools 中为渐进式 Web 应用和服务工作者调试工具的信息，请参阅 [服务工作器改进](../../../service-workers/index.md)。  有关开放源代码项目中此功能Chromium，请参阅问题[1066604。](https://crbug.com/1066604)


<!-- ====================================================================== -->
## <a name="progressive-web-apps-no-longer-display-warnings-for-non-square-icons"></a>渐进式 Web 应用不再显示非方形图标的警告

<!--  Title: Non-square icons in app manifest no longer produce warnings  -->
<!--  Subtitle: As long as square icons are included in the app manifest, non-square icons no longer produce warnings  -->

在 [Microsoft Edge 版本 90](../02/devtools.md) 或更早版本中，如果 PWA 的 Web 应用清单包含非方形图标，则在 **错误和警告** 部分中显示针对每个非方形图标的警告。  在 Microsoft Edge 版本 91 或更高版本中，如果至少提供了一个方形图标，则 **应用程序** 工具中的 **清单** 部分不显示任何警告。  如果未提供任何方形图标，则会出现以下警告消息：

```output
Most operating systems require square icons.  Please include at least one square icon in the array.
```

在Microsoft Edge版本 90 或更早版本中，将针对非正方形的每个图标显示错误：

:::image type="content" source="../../media/2021/04/edge89-application-manifest-errors-and-warnings.msft.png" alt-text="在Microsoft Edge版本 90 或更早版本中，每个非正方形图标都将显示错误" lightbox="../../media/2021/04/edge89-application-manifest-errors-and-warnings.msft.png":::

在Microsoft Edge版本 91 或更高版本中，提供至少一个方形图标时不会显示错误：

:::image type="content" source="../../media/2021/04/edge91-application-manifest-errors-and-warnings.msft.png" alt-text="在Microsoft Edge版本 91 或更高版本中，提供至少一个方形图标时不会显示错误" lightbox="../../media/2021/04/edge91-application-manifest-errors-and-warnings.msft.png":::

若要查看 Web 应用程序清单中的错误和警告，请选择"**** 应用程序工具">**"** 应用程序"部分>**清单"**。  错误和警告列在 **错误和警告** 标题下。  有关 Web 应用清单详细信息，请参阅使用 [Web 应用清单将渐进式 Web 应用集成到操作系统](../../../../progressive-web-apps-chromium/how-to/web-app-manifests.md)。  若要创建要包括在 Web 应用程序清单中的图标，请转到 [PWABuilder 映像生成器](https://www.pwabuilder.com/imageGenerator)。  有关开放源代码项目中此功能Chromium，请参阅问题[1185945。](https://crbug.com/1185945)


<!-- ====================================================================== -->
## <a name="localized-devtools-now-supported-in-chromium-based-browsers"></a>基于 Chromium 的浏览器现在支持本地化的 DevTools

<!--  Title: Localization for all  -->
<!--  Subtitle: Match browser language enabled to all Chromium-based browsers  -->

从 [Microsoft Edge版本 81](../../2020/01/devtools.md#using-the-devtools-in-other-languages) 开始，Microsoft Edge开发人员工具 UI 以你自己的语言显示。  许多开发人员使用自己母语版本的其他开发人员工具（如 StackOverflow 和 Visual Studio Code），而不仅仅是英语版本。  Microsoft Edge DevTools 团队、Chrome DevTools 团队和 Google Lighthouse 团队通力协作，在所有基于 Chromium 的浏览器中提供相同的体验。  若要详细了解如何在语言中使用 DevTools，请参阅更改 [DevTools 语言设置](../../../customize/localization.md)。  有关开放源代码项目中有关此功能的协作Chromium，请参阅问题[1136655](https://crbug.com/1136655)。

:::image type="content" source="../../media/2021/04/japanese-browser-japanese-navigation-elements-3d-view.msft.png" alt-text="Microsoft Edge浏览器和 DevTools 设置为日语。" lightbox="../../media/2021/04/japanese-browser-japanese-navigation-elements-3d-view.msft.png":::


<!-- ====================================================================== -->
## <a name="use-the-keyboard-to-navigate-to-css-variables"></a>使用键盘导航到 CSS 变量

<!--  Title: Navigate to CSS variables with the arrow keys  -->
<!--  Subtitle: In the Styles pane, use the arrow keys to select CSS variables.  Press `Enter` to see the variable definition.  -->

从 [Microsoft Edge 版本 88](../../2020/11/devtools.md#css-variable-definitions-in-styles-pane) 开始，**样式** 窗格显示 CSS 变量，并直接提供指向每个变量定义的链接。  在 Microsoft Edge 版本 91 或更高版本中，可以使用箭头键轻松导航到 CSS 变量。  若要在"样式 **"窗格中打开** 定义，请将鼠标悬停在变量上，然后按 `Enter`。  有关 CSS 变量详细信息，请参阅 Using [CSS custom properties (variables) ](https://developer.mozilla.org/docs/Web/CSS/Using_CSS_custom_properties)。  有关开放源代码项目中此功能Chromium，请参阅问题[1187735。](https://crbug.com/1187735)

:::image type="content" source="../../media/2021/04/elements-styles-body-background-color-theme-body-background.msft.png" alt-text="--theme-body-background CSS 变量在&quot;样式&quot;窗格中突出显示。" lightbox="../../media/2021/04/elements-styles-body-background-color-theme-body-background.msft.png":::


<!-- ====================================================================== -->
## <a name="issues-are-automatically-sorted-by-severity"></a>问题按严重性自动排序

<!-- Title: Display Issues in severity order  -->
<!-- Subtitle: Entries in the Issues tool now display in severity order and allow you to focus your updates on the most important issues. -->

**Issue** 工具显示改进网站的建议，包括辅助功能、性能、安全性等。 根据你的反馈，问题现在按严重性自动排序。  在每个反馈类别中，首先显示标记为 **错误** 的每个问题，后跟标记为 **警告** 的每个问题，然后显示标记为 **提示** 的每个问题。  为了帮助优化问题，我们计划为将来的更新提供额外的筛选器选项。  若要详细了解如何查看问题，请参阅 [使用问题工具查找和修复问题](../../../issues/index.md)。

:::image type="content" source="../../media/2021/04/elements-issues-ordered-issues.msft.png" alt-text="&quot;问题&quot;工具显示按严重性排序的问题。" lightbox="../../media/2021/04/elements-issues-ordered-issues.msft.png":::


<!-- ====================================================================== -->
## <a name="microsoft-edge-developer-tools-for-visual-studio-code-version-117"></a>Microsoft Edge 开发人员工具 for Visual Studio Code 版本 1.1.7

<!-- Title: Microsoft Edge DevTools for Visual Studio version 1.1.7  -->
<!-- Subtitle: Increased target closure reliability, automatically update the side panel, new right-click menu for settings and Changelog, and more. -->

[Microsoft Edge 工具 for Visual Studio Code 扩展](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) 版本 1.1.7 提供 [Microsoft Edge 版本 88](../../2020/11/devtools.md) 中的 DevTools。  此扩展现在支持 ARM 设备，并且不再依赖于 [Microsoft Edge 调试程序](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-edge) 扩展。  版本 1.1.7 包括以下 bug 修复和改进。

*  更新了目标关闭的可靠性。

*  更新了侧面板，以在调试创建或销毁的目标时自动刷新。

*  添加了一个新的右键单击菜单，可让你更快地访问扩展设置和最新的 Changelog。

*  更新并简化了扩展文档（包括最新功能）的发布。

若要手动更新到版本 1.1.7，请参阅 [手动更新扩展](https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually)。  你可以在 [vscode-edge-devtools GitHub repo](https://github.com/microsoft/vscode-edge-devtools) 上提交问题并参与扩展的改进。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

[!INCLUDE [contact DevTools team note](../../includes/chromium-whats-new-note.md)]

### <a name="visualize-css-scroll-snap"></a>可视化 CSS 滚动贴靠

现在，可以在"元素"`scroll-snap`工具中**** 切换锁屏提醒，以检查 CSS 滚动对齐方式。  当网页上的 HTML 元素应用于 `scroll-snap-type` 该元素时，" `scroll-snap` 元素"工具的旁边会显示 **锁** 屏提醒。  单击锁屏提醒以 (或) 网页上滚动贴贴的显示。

有关示例网页，请参阅 [滚动贴靠演示](https://mathiasbynens.github.io/css-dbg-stories/css-scroll-snap.html)。  在示例中，点出现在对齐边缘上。  滚动端口具有纯色轮廓，而贴靠项具有虚线边框。  滚动填充填充为绿色，而滚动边距填充为橙色。

<!-- You can view the source files for the Scroll Snap demo at the [mathiasbynens/css-dbg-stories](https://github.com/mathiasbynens/css-dbg-stories) repo. -->

:::image type="content" source="../../media/2021/04/elements-scroll-snap-highlight.msft.png" alt-text="CSS 滚动贴靠。" lightbox="../../media/2021/04/elements-scroll-snap-highlight.msft.png":::

有关开放源代码项目中此功能的Chromium，请参阅问题 [862450](https://crbug.com/862450)。

### <a name="new-memory-inspector-tool"></a>新建内存检查器工具

使用新的 **内存检查器** 工具检查 JavaScript 和 Wasm 内存中的 `ArrayBuffer`。  打开 [JS 中内存](https://memory-inspector.glitch.me/demo-js.html) 演示网页。 该网页提供类似于以下内容的说明。  在" **源** "工具中， `memory-write-wasm` 打开文件，并设置第 18 行的断 () `0x03c` 。  刷新网页。  展开调试程序窗格中的“**范围**”部分。  新图标显示在 **缓冲区** 值 的旁边。  单击它以打开新的 **内存检查器** 工具。  请参阅 [使用内存检查器工具检查 JavaScript ArrayBuffer](../../../memory-inspector/memory-inspector-tool.md)。

若要了解有关"源"工具中的调试 **的详细信息** ，请参阅使用 [调试器窗格调试 JavaScript 代码](../../../sources/index.md#using-the-debugger-pane-to-debug-javascript-code)。  有关开放源代码项目中此功能的Chromium，请参阅 Issue [1166577](https://crbug.com/1166577)。

:::image type="content" source="../../media/2021/04/sources-memory-write-wasm-breakpoint-scope-reveal-in-memory-inspector-panel.msft.png" alt-text="内存检查器工具。" lightbox="../../media/2021/04/sources-memory-write-wasm-breakpoint-scope-reveal-in-memory-inspector-panel.msft.png":::

### <a name="new-badge-settings-pane-in-the-elements-tool"></a>元素工具中的新建徽章设置窗格

现在，使用"元素 **"** 工具中的**** 锁屏提醒设置打开或 (或) 各个锁屏提醒。  在检查网页时，使用此功能自定义并对重要徽章保持关注。  若要在"元素"工具顶部显示锁屏提醒 **设置** 窗格：

1. 右键单击某个元素，然后单击" **锁屏提醒设置"**。

1. 若要显示 (或隐藏) 锁屏提醒， (或) 锁屏提醒名称旁边的复选框。

<!--  For the history of this feature in the Chromium open-source project, see Issue [1066772](https://crbug.com/1066772).  -->

:::image type="content" source="../../media/2021/04/elements-contextual-menu-badge-settings.msft.png" alt-text="&quot;元素&quot;工具中的锁屏提醒设置窗格。" lightbox="../../media/2021/04/elements-contextual-menu-badge-settings.msft.png":::

### <a name="enhanced-image-preview-with-aspect-ratio-information"></a>使用纵横比信息增强的图像预览

DevTools 中的图像预览已增强，可显示更多信息，包括以下详细信息：

*  呈现的大小
*  呈现的纵横比
*  内部大小
*  内部纵横比
*  文件大小

该信息可帮助你更好地了解图像并应用优化。  单击图像预览时，网络工具中也提供**** 图像纵横比信息。

在 **"元素** "工具中，图像预览现在显示有关图像的详细信息，包括纵横比：

:::image type="content" source="../../media/2021/04/elements-inspect-image-src-hover-preview.msft.png" alt-text="使用 Element 工具中的纵横比信息的图像预览。" lightbox="../../media/2021/04/elements-inspect-image-src-hover-preview.msft.png":::

此外，单击图像预览时，网络工具中还会**** 提供图像纵横比信息：

:::image type="content" source="../../media/2021/04/network-img-name-filters-preview.msft.png" alt-text="网络工具中的图像纵横比信息。" lightbox="../../media/2021/04/network-img-name-filters-preview.msft.png":::

有关开放源代码项目中此功能的Chromium，请参阅 Issues [1149832](https://crbug.com/1149832) and [1170656](https://crbug.com/1170656)。

### <a name="new-options-to-configure-content-encodings-in-the-network-conditions-tool"></a>用于在网络条件工具中配置 Content-Encoding 的新选项

在 **"网络**"工具中，单击"限制"下拉菜单旁边的"更多网络**** 条件 **...**"按钮以打开 **"网络条件"** 工具。  测试是否针对不支持 [gzip](https://www.gnu.org/software/gzip/manual)、 [brotli](https://www.brotli.org) 或其他将来的浏览器正确编码服务器响应 `Content-Encoding`：

1. 打开“**网络条件**”工具。

1. 转到 **"接受的内容编码"**。

1. 清除要测试的 `Content-Encoding` 旁边的复选框。

有关开放源代码项目中此功能的Chromium，请参阅 Issue [1162042](https://crbug.com/1162042)。

:::image type="content" source="../../media/2021/04/network-more-network-conditions-accepted-content-encodings.msft.png" alt-text="&quot;更多网络条件&quot;按钮将打开&quot;网络条件&quot;工具以配置&quot;Content-Encoding&quot;。" lightbox="../../media/2021/04/network-more-network-conditions-accepted-content-encodings.msft.png":::

### <a name="styles-pane-enhancements"></a>样式窗格增强功能

#### <a name="new-shortcut-to-display-computed-value-in-the-styles-pane"></a>在样式窗格中显示计算值的新快捷方式

现在，若要在"样式"窗格中显示计算的 **CSS 值：**

1. 右键单击 CSS 属性，然后选择 **"查看计算值"**。

若要查看开放源代码项目中此功能的历史记录Chromium，请参阅 Issue [1076198](https://crbug.com/1076198)。

:::image type="content" source="../../media/2021/04/elements-styles-highlight-view-computed-value.msft.png" alt-text="显示计算值的新快捷方式。" lightbox="../../media/2021/04/elements-styles-highlight-view-computed-value.msft.png":::

#### <a name="support-for-the-accent-color-keyword"></a>支持强调色关键字

**样式** 窗格的自动完成 UI 现在检测 `accent-color` CSS 关键字，这允许你为元素生成的 UI 控件指定强调色。  元素生成的 UI 控件示例包括复选框或单选按钮。 有关实现实现状态Chromium，请参阅[功能：强调文字颜色 CSS 属性](https://chromestatus.com/feature/4752739957473280)。  若要启用此功能，请转到 ， `edge://flags#enable-experimental-web-platform-features` 将复选框设置为 **已启用**。  有关开放源代码项目中此功能的Chromium，请参阅 Issue [1092093](https://crbug.com/1092093)。

:::image type="content" source="../../media/2021/04/elements-styles-accent-color.msft.png" alt-text="强调文字颜色 CSS 关键字。" lightbox="../../media/2021/04/elements-styles-accent-color.msft.png":::

### <a name="display-details-about-blocked-features-in-the-frame-details-view"></a>在帧详细信息视图中显示有关被阻止功能的详细信息

权限策略是一个 Web 平台 API，它使网站能够允许或阻止在单个帧或其嵌入的 `iframe` 中使用浏览器功能。
请参阅 [权限策略解释器](https://github.com/w3c/webappsec-permissions-policy/blob/main/permissions-policy-explainer.md)。  若要显示有关阻止功能的原因的详细信息，请：

1. 转到 ["OOPIF 权限策略"](http://permission-policy-demo.glitch.me)。
1. 导航到 **应用程序** 工具。
1. 单击一个帧。
1. 导航到 **权限策略** 部分。
1. 导航到 **禁用功能** 属性。
1. 单击 **"显示详细信息"**。
1. 单击每个策略旁边的图标以导航到 `iframe` 阻止该功能的 或 网络请求。

若要查看开放源代码项目中此功能的历史记录Chromium，请参阅 Issue [1158827](https://crbug.com/1158827)。

:::image type="content" source="../../media/2021/04/application-frames-top-permission-policy-disabled-features-show-details-highlight.msft.png" alt-text="框架详细信息视图中被阻止的功能。" lightbox="../../media/2021/04/application-frames-top-permission-policy-disabled-features-show-details-highlight.msft.png":::

### <a name="filter-experiments-in-the-experiments-setting"></a>在试验设置中筛选试验

使用新的试验筛选器更快地查找试验。  例如，若要打开针对代码问题的新实验：''

1. 选择**设置** > **Experiments"**。
1. 在" **筛选器"** 文本框中，键入 `issues`。

:::image type="content" source="../../media/2021/04/settings-experiments-filter-by-issues.msft.png" alt-text="在实验设置中筛选实验。" lightbox="../../media/2021/04/settings-experiments-filter-by-issues.msft.png":::

### <a name="new-vary-header-column-in-the-cache-storage-pane"></a>缓存存储窗格中的新的变化标头列

使用 **缓存存储** 窗格中的新 `Vary Header` 列显示 [变化](https://httpwg.org/specs/rfc7231.html#header.vary) HTTP 响应标头值。  有关开放源代码项目中此功能的Chromium，请参阅 Issue [1186049](https://crbug.com/1186049)。

:::image type="content" source="../../media/2021/04/application-cache-cache-storage-highlighted-vary-header.msft.png" alt-text="Vary Header 列。" lightbox="../../media/2021/04/application-cache-cache-storage-highlighted-vary-header.msft.png":::

### <a name="sources-tool-improvements"></a>源工具改进

#### <a name="support-for-new-javascript-features"></a>支持新的 JavaScript 功能

DevTools 现在支持新的 [专用品牌检查 obj 中的 a.k.a. #foo](https://v8.dev/features/private-brand-checks) JavaScript 语言功能。  专用品牌检查功能扩展了 [in 运算符](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/in)，以支持在特定对象上的 [专用类字段](https://v8.dev/features/class-fields#private-class-fields)。  请在 **控制台** 和 **源** 工具中试用。  此外，要检查私有字段：

1. 导航到 **调试程序** 窗格。
1. 导航到 **范围** 部分。

有关开放源代码项目中此功能Chromium，请参阅问题 [11374](https://crbug.com/v8/11374)。

:::image type="content" source="../../media/2021/04/sources-page-pen-js-breakpoint-scope-script-dog.msft.png" alt-text="JavaScript 专用品牌检查。" lightbox="../../media/2021/04/sources-page-pen-js-breakpoint-scope-script-dog.msft.png":::

#### <a name="enhanced-support-for-breakpoints-debugging"></a>对断点调试的增强支持

新式 JavaScript 捆绑程序（如 [Webpack](https://webpack.js.org)）和 [汇总](https://rollupjs.org) 支持代码拆分。  若要详细了解代码拆分，请参阅代码 [拆分](https://webpack.js.org/guides/code-splitting/#:~:text=There%20are%20three%20general%20approaches%20to%20code%20splitting,Split%20code%20via%20inline%20function%20calls%20within%20modules.)。  在 Microsoft Edge 版本 90 或更早版本中，DevTools 仅在单个捆绑包中设置断点。  在 Microsoft Edge 版本 91 或更高版本中，在调试共享组件时，DevTools 会在多个捆绑包中正确设置断点。  有关开放源代码项目中此功能的历史记录Chromium，请参阅问题 [1142705](https://crbug.com/1142705)[、979000](https://crbug.com/979000) 和 [1180794](https://crbug.com/1180794)。

#### <a name="support-hover-preview-with-bracket-notation"></a>支持使用括号表示法的悬停预览

DevTools 现在支持在 **源** 工具中使用 `[]` 表示法的 JavaScript 成员表达式上进行悬停预览。  有关开放源代码项目中此功能的Chromium，请参阅 Issue [1178305](https://crbug.com/1178305)。

:::image type="content" source="../../media/2021/04/sources-page-pen.js-breakpoint-arr-i-a.msft.png" alt-text="支持使用 [] 表示法的悬停预览" lightbox="../../media/2021/04/sources-page-pen.js-breakpoint-arr-i-a.msft.png":::

#### <a name="improved-outline-of-html-files"></a>改进的 HTML 文件大纲

DevTools 现在对 `.html` 文件具有更好的大纲支持。  在 **源** 工具中，打开 `.html` 文件。  若要打开或 (代码) ，`Ctrl`++`Shift``O`请按 Windows/Linux`O` `Cmd`+`Shift`+或 macOS。  在下图中，DevTools 现在正确列出了大纲中的所有函数。  以前，DevTools 仅显示一些函数。  有关开放源代码项目中此功能的Chromium，请参阅 Issues [761019](https://crbug.com/761019) and [1191465](https://crbug.com/1191465)。

:::image type="content" source="../../media/2021/04/sources-page-jobobbx-at.msft.png" alt-text=" 改进了 HTML 文件的大纲。" lightbox="../../media/2021/04/sources-page-jobobbx-at.msft.png":::

#### <a name="proper-error-stack-traces-for-wasm-debugging"></a>Wasm 调试的正确错误堆栈跟踪

在 Microsoft Edge 版本 90 或更早版本中，DevTools 仅在错误堆栈跟踪中显示泛型 Wasm 引用。  在 Microsoft Edge 版本 91 或更高版本中，DevTools 解析内联函数请求，并在 Wasm 调试的错误堆栈跟踪中显示源位置。  若要了解有关控制台中的错误堆栈跟踪**的详细信息，请参阅**[错误](../../../console/api.md#error)。

在 Microsoft Edge 版本 91 或更高版本中，DevTools 解析内联函数请求，并显示 Wasm 调试的正确错误堆栈跟踪。

在Microsoft Edge版本 90 及更早版本中，源位置不会显示在错误堆栈跟踪中。  源位置包括 `dsquare`。  Wasm 调试以前的错误堆栈跟踪：

:::image type="content" source="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error-old.msft.png" alt-text="Wasm 调试以前的错误堆栈跟踪。" lightbox="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error-old.msft.png":::

在Microsoft Edge版本 91 及更高版本中，源位置显示在错误堆栈跟踪中。  Wasm 调试的正确错误堆栈跟踪：

:::image type="content" source="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error.msft.png" alt-text="Wasm 调试的正确错误堆栈跟踪。" lightbox="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error.msft.png":::

有关开放源代码项目中此功能的Chromium，请参阅 Issue [1189161](https://crbug.com/1189161)。


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download)作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-91)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
