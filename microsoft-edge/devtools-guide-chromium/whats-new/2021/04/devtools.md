---
description: 波浪下划线突出显示了元素工具、服务工作进程更新日程表等中的代码问题。
title: DevTools 中的新增功能 (Microsoft Edge 91)
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/06/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: fce34a73cfc303c794020bc8d3a398de714ace3e15de7272e98509a9cf0071ee
ms.sourcegitcommit: 841e41de1a32501ece862399fa56170c022127c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2021
ms.locfileid: "11807117"
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
# <a name="whats-new-in-devtools-microsoft-edge-91"></a>DevTools 中的新增功能 (Microsoft Edge 91)  

[!INCLUDE [contact DevTools team note](../../includes/edge-whats-new-note.md)]  

## <a name="wavy-underlines-highlight-code-issues-and-improvements-in-elements-tool"></a>波浪下划线突出显示元素工具中的代码问题和改进项  

<!--  Title: Get code hints in Elements tool  -->  
<!--  Subtitle: Wavy underlines like the ones you see in Visual Studio Code now display in the Elements tool.  Underlines alert you to code issues related to accessibility, compatibility, security, performance, and  so on.  -->  

在大多数新式 IDE 中，文本下的波浪下划线指示语法错误。   在 Microsoft Edge 版本 91 或更高版本中，波浪下划线显示在 **元素** 工具的 **DOM** 视图中的 HTML 下。  波浪下划线指示与辅助功能、兼容性、性能等相关的代码问题和建议。  有关如何查看和编辑问题的详细信息，请导航到 [使用问题工具查找和解决问题][DevtoolsIssuesIndex]。  

要打开 **问题** 工具并详细了解问题及其修复方法，请完成以下操作之一。  

*   选择并按住“`Shift`”，然后选择任何波浪下划线。  
*   完成以下操作。  
    1.  将鼠标悬停在任何波浪下划线上。  
    1.  打开上下文菜单\（右键单击\）。  
    1.  选择“**在问题中显示**”。  
        
:::row:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/elements-iframe-highlight-issues.msft.png" alt-text="在元素工具中选择带下划线的错误" lightbox="../../media/2021/04/elements-iframe-highlight-issues.msft.png":::
         在 **元素** 工具中选择带下划线的错误  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/elements-iframe-highlight-issues-focus.msft.png" alt-text="在问题工具中显示错误详细信息" lightbox="../../media/2021/04/elements-iframe-highlight-issues-focus.msft.png":::
         在 **问题** 工具中显示错误详细信息  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

## <a name="learn-about-devtools-with-informative-tooltips"></a>通过信息丰富的工具提示了解 DevTools  

:::image type="icon" source="../../media/2020/06/experimental-tag-14px.msft.png":::  

<!--  Title: Learn more about DevTools with DevTools Tooltips  -->  
<!--  Subtitle: Informative overlays are now available in the default DevTools interface.  -->  

DevTools 工具提示功能可帮助你了解 DevTools 中所有不同的工具和窗格。  要关闭工具提示，请选择“`Esc`”。  要打开工具提示，请完成以下操作之一。  

*   选择 `Ctrl` +`Shift`+`H` \(Windows、Linux\) 或 `Cmd`+`Shift`+`H` \(macOS\)。  
*   [打开命令菜单][DevtoolsCommandMenuIndexOpenCommandMenu]，然后键入 `tooltips`。  
*   选择“**自定义和控制 DevTools** \（`...`\）”>“**帮助**” > “**切换 DevTools 工具提示**”。  

此外，如果启用 [焦点模式和 DevTools 工具提示][DevtoolsWhatsNew202102DevtoolsGroupToolsTogetherInFocusMode] 试验，还可以选择**活动栏** 底部的“**切换 DevTools 工具提示**”\（`?`\）按钮。  

要显示有关如何使用 DevTools 的详细信息，请打开工具提示，然后将鼠标悬停在 DevTools 的每个轮廓区域上。  

:::image type="complex" source="../../media/2021/04/elements-issues-focus-mode-tooltips.msft.png" alt-text="将鼠标悬停在问题工具突出显示区域中的任意位置，以显示更多详细信息" lightbox="../../media/2021/04/elements-issues-focus-mode-tooltips.msft.png":::
   将鼠标悬停在 **问题** 工具突出显示区域中的任意位置，以显示更多详细信息  
:::image-end:::  

## <a name="service-worker-update-timeline"></a>服务工作进程更新日程表  

<!--todo:  Update the linked [Service Worker improvements][DevtoolsServiceWorkerIndex] article.  -->  

<!--  Title: The tasks associated with your Service Worker  -->  
<!--  Subtitle: Debug with Service Worker Update Cycle  -->  

在 Microsoft Edge 版本 91 或更高版本中，如果你是渐进式 Web 应用或服务工作进程开发人员，请在 **应用程序** 工具中将服务工作进程的更新生命周期显示为日程表。  此功能可帮助你了解服务工作进程在以下每个阶段花费的时间。  

*   **安装**  
*   **等待**  
*   **激活**  
    
:::image type="complex" source="../../media/2021/04/application-service-workers-update-cycle-version-73-focus.msft.png" alt-text="查看服务工作进程更新周期中的日程表" lightbox="../../media/2021/04/application-service-workers-update-cycle-version-73-focus.msft.png":::
   查看服务工作进程 **更新周期** 中的 **日程表**  
:::image-end:::  

有关服务工作进程生命周期的详细信息，请导航到 [服务工作进程生命周期][ProgressiveWebAppsServiceworkerServiceWorkerLifecycle]。  有关 DevTools 中渐进式 Web 应用和服务工作进程调试工具的详细信息，请导航到 [服务工作进程改进][DevtoolsServiceWorkerIndex]。  要在 Chromium 开源项目中查看此功能的实时更新，请导航至问题 [1066604][CR1066604]。  

## <a name="progressive-web-apps-no-longer-display-warnings-for-non-square-icons"></a>渐进式 Web 应用不再显示非方形图标的警告  

<!--  Title: Non-square icons in app manifest no longer produce warnings  -->  
<!--  Subtitle: As long as square icons are included in the app manifest, non-square icons no longer produce warnings  -->  

在 [Microsoft Edge 版本 90][DevtoolsWhatsNew202102Devtools] 或更早版本中，如果 PWA 的 Web 应用清单包含非方形图标，则在 **错误和警告** 部分中显示针对每个非方形图标的警告。  在 Microsoft Edge 版本 91 或更高版本中，如果至少提供了一个方形图标，则 **应用程序** 工具中的 **清单** 部分不显示任何警告。  如果未提供任何方形图标，则会显示一条如下警告消息。  

```output
Most operating systems require square icons.  Please include at least one square icon in the array.  
```  

:::row:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/edge89-application-manifest-errors-and-warnings.msft.png" alt-text="在 Microsoft Edge 版本 90 或更早版本中，每个非正方形图标都会显示错误" lightbox="../../media/2021/04/edge89-application-manifest-errors-and-warnings.msft.png":::
         在 Microsoft Edge 版本 90 或更早版本中，每个非正方形图标都会显示错误  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/edge91-application-manifest-errors-and-warnings.msft.png" alt-text="在 Microsoft Edge 版本 91 或更高版本中，如果提供至少一个方形图标，则不会显示任何错误" lightbox="../../media/2021/04/edge91-application-manifest-errors-and-warnings.msft.png":::
         在 Microsoft Edge 版本 91 或更高版本中，如果提供至少一个方形图标，则不会显示任何错误  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

要查看 Web 应用清单中的错误和警告，请导航到 **应用程序** 工具，然后选择“**清单**”部分。  错误和警告列在 **错误和警告** 标题下。  有关 Web 应用清单的详细信息，请导航到 [使用 Web 应用清单将渐进式 Web 应用集成到操作系统][ProgressiveWebAppsWebappmanifests]。  要创建要包含在 Web 应用清单中的图标，请导航到 [PWABuilder 映像生成器][PwabuilderImagegenerator]。  要在 Chromium 开源项目中查看此功能的实时更新，请导航至问题 [1185945][CR1185945]。  

## <a name="localized-devtools-now-supported-in-chromium-based-browsers"></a>基于 Chromium 的浏览器现在支持本地化的 DevTools  

<!--  Title: Localization for all  -->  
<!--  Subtitle: Match browser language enabled to all Chromium-based browsers  -->  

从 [Microsoft Edge 版本 81][DevtoolsWhatsNew202001DevtoolsUsingDevtoolsInOtherLanguages] 开始，Microsoft Edge DevTools 以你自己的语言显示。  许多开发人员使用自己母语版本的其他开发人员工具（如 StackOverflow 和 Visual Studio Code），而不仅仅是英语版本。  Microsoft Edge DevTools 团队、Chrome DevTools 团队和 Google Lighthouse 团队通力协作，在所有基于 Chromium 的浏览器中提供相同的体验。  有关如何在你的语言中使用 DevTools 的详细信息，请导航到 [更改 DevTools 语言设置][DevtoolsCustomizeLocalization]。  有关 Chromium 开源项目中此功能的协作方面的详细信息，请导航到 [1136655][CR1136655]。  

:::image type="complex" source="../../media/2021/04/japanese-browser-japanese-navigation-elements-3d-view.msft.png" alt-text="Microsoft Edge 浏览器和 DevTools 设置为日语" lightbox="../../media/2021/04/japanese-browser-japanese-navigation-elements-3d-view.msft.png":::
   Microsoft Edge 浏览器和 DevTools 设置为日语  
:::image-end:::  

## <a name="use-the-keyboard-to-navigate-to-css-variables"></a>使用键盘导航到 CSS 变量  

<!--  Title: Navigate to CSS variables with the arrow keys  -->  
<!--  Subtitle: In the Styles pane, use the arrow keys to choose CSS variables.  Select `Enter` to see the variable definition.  -->  

从 [Microsoft Edge 版本 88][DevtoolsWhatsNew202011DevtoolsCssVariableDefinitionsInStylesPane] 开始，**样式** 窗格显示 CSS 变量，并直接提供指向每个变量定义的链接。  在 Microsoft Edge 版本 91 或更高版本中，可以使用箭头键轻松导航到 CSS 变量。  要在 **样式** 窗格中打开定义，请将鼠标悬停在变量上，然后选择“`Enter`”。  有关 CSS 变量的详细信息，请导航到 [使用 CSS 自定义属性（变量）][MdnDocsWebCssUsingCssCustomProperties]。  要在 Chromium 开源项目中查看此功能的实时更新，请导航至问题 [1187735][CR1187735]。  

:::image type="complex" source="../../media/2021/04/elements-styles-body-background-color-theme-body-background.msft.png" alt-text="样式窗格中突出显示的 --theme-body-background CSS 变量" lightbox="../../media/2021/04/elements-styles-body-background-color-theme-body-background.msft.png":::
   **样式** 窗格中突出显示的 `--theme-body-background` CSS 变量  
:::image-end:::  

## <a name="issues-are-automatically-sorted-by-severity"></a>问题按严重性自动排序  

<!-- Title: Display Issues in severity order  -->  
<!-- Subtitle: Entries in the Issues tool now display in severity order and allow you to focus your updates on the most important issues. -->  

**Issue** 工具显示改进网站的建议，包括辅助功能、性能、安全性等。 根据你的反馈，问题现在按严重性自动排序。  在每个反馈类别中，首先显示标记为 **错误** 的每个问题，后跟标记为 **警告** 的每个问题，然后显示标记为 **提示** 的每个问题。  为了帮助优化问题，我们计划为将来的更新提供额外的筛选器选项。  有关如何查看问题的详细信息，请导航到 [使用问题工具查找和解决问题][DevtoolsIssuesIndex]。  

:::image type="complex" source="../../media/2021/04/elements-issues-ordered-issues.msft.png" alt-text="问题工具按严重性排序显示问题" lightbox="../../media/2021/04/elements-issues-ordered-issues.msft.png":::
   **问题** 工具按严重性排序显示问题  
:::image-end:::  

## <a name="microsoft-edge-developer-tools-for-visual-studio-code-version-117"></a>Microsoft Edge 开发人员工具 for Visual Studio Code 版本 1.1.7  

<!-- Title: Microsoft Edge DevTools for Visual Studio version 1.1.7  -->  
<!-- Subtitle: Increased target closure reliability, automatically update the side panel, new contextual menu for settings and Changelog, and more. -->  

[Microsoft Edge 工具 for Visual Studio Code 扩展][VisualstudioMarketplaceMsEdgedevtoolsVscodeEdgeDevtools] 版本 1.1.7 提供 [Microsoft Edge 版本 88][DevtoolsWhatsNew202011Devtools] 中的 DevTools。  此扩展现在支持 ARM 设备，并且不再依赖于 [Microsoft Edge 调试程序][VisualstudioMarketplaceMsjsdiagDebuggerForEdge] 扩展。  版本 1.1.7 包括以下 bug 修复和改进。  

*   更新了目标关闭的可靠性。  
*   更新了侧面板，以在调试创建或销毁的目标时自动刷新。  
*   添加了一个新的上下文菜单，可让你更快地访问扩展设置和最新的 Changelog。  
*   更新并简化了扩展文档（包括最新功能）的发布。  
    
要手动更新到版本 1.1.7，请导航至“[手动更新扩展][VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]”。  你可以在 [vscode-edge-devtools GitHub repo][GithubMicrosoftVscodeEdgeDevtools] 上提交问题并参与提升扩展。  

## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告  

[!INCLUDE [contact DevTools team note](../../includes/chromium-whats-new-note.md)]  

### <a name="visualize-css-scroll-snap"></a>可视化 CSS 滚动贴靠  

现在可以在 **元素** 工具中切换 `scroll-snap` 徽章，以检查 CSS 滚动贴靠对齐方式。  当网页上的 HTML 元素将 `scroll-snap-type` 应用到它时，**元素** 工具中在其附近会显示一个 `scroll-snap` 徽章。  选择该徽章以打开 \（或关闭）网页上滚动贴靠放置文件夹的显示。  要查看示例网页，请导航到 [滚动贴靠演示][GlitchMicrosoftEdgeChromiumDevtoolsCssDbgStoriesCssScrollSnapHtml]。  在该示例中，点显示在贴靠边缘上。  滚动端口具有实心轮廓，而对齐项具有短划线轮廓。  滚动填充以绿色填充，而滚动边距则填充为橙色。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [862450][CR862450]。  

:::image type="complex" source="../../media/2021/04/elements-scroll-snap-highlight.msft.png" alt-text="CSS 滚动贴靠" lightbox="../../media/2021/04/elements-scroll-snap-highlight.msft.png":::
   CSS 滚动贴靠  
:::image-end:::  

### <a name="new-memory-inspector-tool"></a>新建内存检查器工具  

使用新的 **内存检查器** 工具检查 JavaScript 和 Wasm 内存中的 `ArrayBuffer`。  打开 [JS 中内存][GlitchMemoryInspectorDemoJsHtml] 演示网页。  在 **源** 工具中，打开 `memory-write-wasm` 文件，并在行 `0x03c` 处设置断点。  刷新网页。  展开调试程序窗格中的“**范围**”部分。  新图标显示在 **缓冲区** 值 的旁边。  选择它以打开新的 **内存检查器** 工具。  

要了解在 **源** 工具中调试的详细信息，请导航到 [使用调试程序窗格调试 JavaScript 代码][DevtoolsSourcesUsingDebuggerPaneToDebugJavascriptCode]。  要在 Chromium 开源项目中查看此功能的历史记录，请导航至问题 [1166577][CR1166577]。  

:::image type="complex" source="../../media/2021/04/sources-memory-write-wasm-breakpoint-scope-reveal-in-memory-inspector-panel.msft.png" alt-text="内存检查器工具" lightbox="../../media/2021/04/sources-memory-write-wasm-breakpoint-scope-reveal-in-memory-inspector-panel.msft.png":::
   **内存检查器** 工具  
:::image-end:::  

### <a name="new-badge-settings-pane-in-the-elements-tool"></a>元素工具中的新建徽章设置窗格  

现在，使用 **元素** 工具中的 **徽章设置** 来打开\（或关闭\）单个徽章。  在检查网页时，使用此功能自定义并对重要徽章保持关注。  要在 **元素** 工具顶部显示徽章设置窗格，请完成以下操作。  

1.  将鼠标悬停在任何元素上。  
1.  打开上下文菜单\（右键单击\）。  
1.  选择“**徽章设置...**”。  
    
要显示\（或隐藏\）徽章，请选择\（或删除\）徽章名称旁边的复选框。  

<!--  To review the history of this feature in the Chromium open-source project, navigate to Issue [1066772][CR1066772].  -->  

:::image type="complex" source="../../media/2021/04/elements-contextual-menu-badge-settings.msft.png" alt-text="元素工具中的徽章设置窗格" lightbox="../../media/2021/04/elements-contextual-menu-badge-settings.msft.png":::
   **元素** 工具中的 **徽章设置** 窗格  
:::image-end:::  

### <a name="enhanced-image-preview-with-aspect-ratio-information"></a>使用纵横比信息增强的图像预览  

已增强 DevTools 中的图像预览以显示更多信息，包括以下详细信息。  

*   呈现的大小  
*   呈现的纵横比  
*   内部大小  
*   内部纵横比  
*   文件大小  
    
该信息可帮助你更好地了解图像并应用优化。  选择图像预览时，**网络** 工具中也提供了图像纵横比信息。  

:::row:::
   :::column span="":::
      在 **元素** 工具中，图像预览现在显示有关图像的详细信息。  
   :::column-end:::
   :::column span="":::
      此外，当你选择图像预览时，**网络** 工具中提供了图像纵横比信息。  
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/elements-inspect-image-src-hover-preview.msft.png" alt-text="元素工具中包含纵横比信息的图像预览" lightbox="../../media/2021/04/elements-inspect-image-src-hover-preview.msft.png":::
         **元素**工具中包含纵横比信息的图像预览  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/network-img-name-filters-preview.msft.png" alt-text="网络工具中的图像纵横比信息" lightbox="../../media/2021/04/network-img-name-filters-preview.msft.png":::
         **网络** 工具中的图像纵横比信息  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1149832][CR1149832] and [1170656][CR1170656]。  

### <a name="new-options-to-configure-content-encodings-in-the-network-conditions-tool"></a>用于在网络条件工具中配置 Content-Encoding 的新选项 

在 **网络** 工具中，选择 **限制** 下拉菜单旁边的新“**更多网络条件...**”按钮，以打开 **网络条件** 工具。  要测试是否为不支持 [gzip][GnuSoftwareGzipManual]、[brotli][|::ref1::|Main] 或其他将来 `Content-Encoding` 的浏览器正确编码服务器响应，请完成以下操作。  

1.  打开“**网络条件**”工具。
1.  导航到 **接受的 Content-Encoding**。 
1.  删除要测试的 `Content-Encoding` 旁边的复选框。  
    
要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1162042][CR1162042]。  

:::image type="complex" source="../../media/2021/04/network-more-network-conditions-accepted-content-encodings.msft.png" alt-text="新的更多网络条件...按钮打开用于配置 Content-Encoding 的网络条件工具" lightbox="../../media/2021/04/network-more-network-conditions-accepted-content-encodings.msft.png":::
   新“**更多网络条件...**”按钮打开 **网络条件** 工具以进行配置 `Content-Encoding`  
:::image-end:::  

### <a name="styles-pane-enhancements"></a>样式窗格增强功能  

#### <a name="new-shortcut-to-display-computed-value-in-the-styles-pane"></a>在样式窗格中显示计算值的新快捷方式  

现在，要在 **样式** 窗格中显示计算的 CSS 值，请完成以下操作。  

1.  将鼠标悬停在 CSS 属性上。  
1.  打开上下文菜单\（右键单击\）。  
1.  选择“**查看计算值**”。  
    
要在 Chromium 开源项目中查看此功能的历史记录，请导航至问题 [1076198][CR1076198]。  

:::image type="complex" source="../../media/2021/04/elements-styles-highlight-view-computed-value.msft.png" alt-text="显示计算值的新快捷方式" lightbox="../../media/2021/04/elements-styles-highlight-view-computed-value.msft.png":::
   显示计算值的新快捷方式  
:::image-end:::  

#### <a name="support-for-the-accent-color-keyword"></a>支持强调色关键字  

**样式** 窗格的自动完成 UI 现在检测 `accent-color` CSS 关键字，这允许你为元素生成的 UI 控件指定强调色。  元素生成的 UI 控件示例包括复选框或单选按钮。 有关 Chromium 实现状态的详细信息，请导航到 [功能：强调色 CSS 属性][ChromestatusFeature4752739957473280]。  要启用此功能，请导航到 `edge://flags#enable-experimental-web-platform-features` 并将复选框设置为“**已启用**”。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1092093][CR1092093]。  

:::image type="complex" source="../../media/2021/04/elements-styles-accent-color.msft.png" alt-text="强调色 CSS 关键字" lightbox="../../media/2021/04/elements-styles-accent-color.msft.png":::
   `accent-color` CSS 关键字
:::image-end:::  

### <a name="display-details-about-blocked-features-in-the-frame-details-view"></a>在帧详细信息视图中显示有关被阻止功能的详细信息  

权限策略是一个 Web 平台 API，它使网站能够允许或阻止在单个帧或其嵌入的 `iframe` 中使用浏览器功能。 有关详细信息，请导航到 [权限策略解释器][GithubW3cWebappsecPermissionsPolicyPermissionsPolicyExplainerMd]。  要显示有关阻止功能原因的详细信息，请完成以下操作。  

1.  导航到 [OOPIF 权限策略][GlitchPermissionPolicyDemoMain]。  
1.  导航到 **应用程序** 工具。  
1.  选择一个帧。  
1.  导航到 **权限策略** 部分。  
1.  导航到 **禁用功能** 属性。  
1.  选择“**显示详细信息**”。  
1.  选择每个策略旁边的图标，以导航到 `iframe` 或阻止该功能的网络请求。  
    
要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1158827][CR1158827]。  

:::image type="complex" source="../../media/2021/04/application-frames-top-permission-policy-disabled-features-show-details-highlight.msft.png" alt-text="帧详细信息视图中阻止的功能" lightbox="../../media/2021/04/application-frames-top-permission-policy-disabled-features-show-details-highlight.msft.png":::
   帧详细信息视图中阻止的功能  
:::image-end:::  

### <a name="filter-experiments-in-the-experiments-setting"></a>在试验设置中筛选试验  

使用新的试验筛选器更快地查找试验。  例如，要为代码问题启用新试验，请完成以下操作。
``

1.  导航到“**设置**” > “**试验**”。  
1.  导航到“**筛选器**”文本框。  
1.  键入 `issues`。  
    
:::image type="complex" source="../../media/2021/04/settings-experiments-filter-by-issues.msft.png" alt-text="在试验设置中筛选试验" lightbox="../../media/2021/04/settings-experiments-filter-by-issues.msft.png":::
   在 **试验** 设置中筛选试验  
:::image-end:::  

### <a name="new-vary-header-column-in-the-cache-storage-pane"></a>缓存存储窗格中的新的变化标头列  

使用 **缓存存储** 窗格中的新 `Vary Header` 列显示 [变化][HttpwgSpecsRfc7231HtmlHeaderVary] HTTP 响应标头值。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1186049][CR1186049]。  

:::image type="complex" source="../../media/2021/04/application-cache-cache-storage-highlighted-vary-header.msft.png" alt-text="变化标头列" lightbox="../../media/2021/04/application-cache-cache-storage-highlighted-vary-header.msft.png":::
   变化标头列  
:::image-end:::  

### <a name="sources-tool-improvements"></a>源工具改进  

#### <a name="support-for-new-javascript-features"></a>支持新的 JavaScript 功能  

DevTools 现在支持新的 [专用品牌检查 obj 中的 a.k.a. #foo][V8DevFeaturesPrivateBrandChecks] JavaScript 语言功能。  专用品牌检查功能扩展了 [in 运算符][MdnDocsWebJavascriptReferenceOperatorsIn]，以支持在特定对象上的 [专用类字段][V8DevFeaturesClassFieldsPrivateClassFields]。  请在 **控制台** 和 **源** 工具中试用。  此外，若要检查专用字段，请完成以下操作。  

1.  导航到 **调试程序** 窗格。  
1.  导航到 **范围** 部分。  
    
要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [11374][CR11374]。  

:::image type="complex" source="../../media/2021/04/sources-page-pen-js-breakpoint-scope-script-dog.msft.png" alt-text="JavaScript 专用品牌检查" lightbox="../../media/2021/04/sources-page-pen-js-breakpoint-scope-script-dog.msft.png":::
   JavaScript 专用品牌检查  
:::image-end:::  

#### <a name="enhanced-support-for-breakpoints-debugging"></a>对断点调试的增强支持  

新式 JavaScript 捆绑程序（如 [Webpack][WebpackJsMain]）和 [汇总][RollupjsMain] 支持代码拆分。  要了解有关代码拆分的详细信息，请导航到 [代码拆分][JsWebpackGuidesCodeSplittingTextThereAreThreeGeneralApproachesToCodeSplittingSplitCodeViaInlineFunctionCallsWithinModules]。  在 Microsoft Edge 版本 90 或更早版本中，DevTools 仅在单个捆绑包中设置断点。  在 Microsoft Edge 版本 91 或更高版本中，在调试共享组件时，DevTools 会在多个捆绑包中正确设置断点。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1142705][CR1142705]、[979000][CR979000] 和 [1180794][CR1180794]。  

#### <a name="support-hover-preview-with-bracket-notation"></a>支持使用括号表示法的悬停预览  

DevTools 现在支持在 **源** 工具中使用 `[]` 表示法的 JavaScript 成员表达式上进行悬停预览。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1178305][CR1178305]。  

:::image type="complex" source="../../media/2021/04/sources-page-pen.js-breakpoint-arr-i-a.msft.png" alt-text="支持使用 [] 表示法的悬停预览" lightbox="../../media/2021/04/sources-page-pen.js-breakpoint-arr-i-a.msft.png":::
   支持使用 `[]` 表示法的悬停预览  
:::image-end:::  

#### <a name="improved-outline-of-html-files"></a>改进的 HTML 文件大纲  

DevTools 现在对 `.html` 文件具有更好的大纲支持。  在 **源** 工具中，打开 `.html` 文件。  要打开\（或关闭\）代码大纲，请在 Windows/Linux 上选择 `Ctrl`+`Shift`+`O` 或在 macOS 上选择 `Cmd`+`Shift`+`O`。  在下图中，DevTools 现在正确列出了大纲中的所有函数。  以前，DevTools 仅显示一些函数。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [761019][CR761019] 和 [1191465][CR1191465]。  

:::image type="complex" source="../../media/2021/04/sources-page-jobobbx-at.msft.png" alt-text=" 改进的 HTML 文件大纲" lightbox="../../media/2021/04/sources-page-jobobbx-at.msft.png":::
   改进的 HTML 文件大纲  
:::image-end:::  

#### <a name="proper-error-stack-traces-for-wasm-debugging"></a>Wasm 调试的正确错误堆栈跟踪  

在 Microsoft Edge 版本 90 或更早版本中，DevTools 仅在错误堆栈跟踪中显示泛型 Wasm 引用。  在 Microsoft Edge 版本 91 或更高版本中，DevTools 解析内联函数请求，并在 Wasm 调试的错误堆栈跟踪中显示源位置。  要详细了解 **控制台** 中的错误堆栈跟踪，请导航到 [错误][DevtoolsConsoleApiError]。  

在 Microsoft Edge 版本 91 或更高版本中，DevTools 解析内联函数请求，并显示 Wasm 调试的正确错误堆栈跟踪。  

:::row:::
   :::column span="":::
      在 Microsoft Edge 版本 90 及更早版本中，源位置不会显示在错误堆栈跟踪中。  源位置包括 `dsquare`。  
   :::column-end:::
   :::column span="":::
      在 Microsoft Edge 版本 91 及更高版本中，源位置显示在错误堆栈跟踪中。
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error-old.msft.png" alt-text="以前的 Wasm 调试的错误堆栈跟踪" lightbox="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error-old.msft.png":::
         Wasm 调试的正确错误堆栈跟踪  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error.msft.png" alt-text="Wasm 调试的正确错误堆栈跟踪" lightbox="../../media/2021/04/sources-page-inlining-dwarf-wasm-breakpoint-console-new-error.msft.png":::
         Wasm 调试的正确错误堆栈跟踪  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1189161][CR1189161]。  

## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道  

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 [ Microsoft Edge 预览频道][MicrosoftEdgePreviewChannels]作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。  

## <a name="getting-in-touch-with-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队  

[!INCLUDE [contact DevTools team note](../../includes/contact-whats-new-note.md)]

<!-- links -->  

[DevtoolsWhatsNew202001DevtoolsUsingDevtoolsInOtherLanguages]: ../../2020/01/devtools.md#using-the-devtools-in-other-languages "使用其他语言的 DevTools - DevTools (Microsoft Edge 81) 中的新增功能 | Microsoft Docs"  
[DevtoolsWhatsNew202011Devtools]: ../../2020/11/devtools.md "DevTools 中的新增功能 (Microsoft Edge 88) | Microsoft Docs"  
[DevtoolsWhatsNew202011DevtoolsCssVariableDefinitionsInStylesPane]: ../../2020/11/devtools.md#css-variable-definitions-in-styles-pane "样式窗格中的 CSS 变量定义 - DevTools (Microsoft Edge 88) 中的新增功能 | Microsoft Docs"  
[DevtoolsWhatsNew202102Devtools]: ../02/devtools.md "DevTools (Microsoft Edge 90) 中的新增功能 | Microsoft Docs"  
[DevtoolsWhatsNew202102DevtoolsGroupToolsTogetherInFocusMode]: ../02/devtools.md#group-tools-together-in-focus-mode "专注模式下将工具组合在一起 - DevTools (Microsoft Edge 90) 中的新增功能 | Microsoft Docs"  

[DevtoolsCommandMenuIndexOpenCommandMenu]: ../../../command-menu/index.md#open-the-command-menu "打开命令菜单 - 使用 Microsoft Edge DevTools 命令菜单运行命令 | Microsoft Docs"  
[DevtoolsConsoleApiError]: ../../../console/api.md#error "错误 - 控制台 API 参考 | Microsoft Docs"  
[DevtoolsCustomizeLocalization]: ../../../customize/localization.md "更改 DevTools 语言设置 | Microsoft Docs"  
[DevtoolsIssuesIndex]: ../../../issues/index.md "使用问题工具查找并修复问题 | Microsoft Docs"  
[DevtoolsServiceWorkerIndex]: ../../../service-workers/index.md "服务工作进程改进 | Microsoft Docs"  
[DevtoolsSourcesUsingDebuggerPaneToDebugJavascriptCode]: ../../../sources/index.md#using-the-debugger-pane-to-debug-javascript-code "使用调试器窗格调试 JavaScript 代码 - 源工具概述 |Microsoft Docs"  

[ProgressiveWebAppsServiceworkerServiceWorkerLifecycle]: ../../../../progressive-web-apps-chromium/serviceworker.md#the-service-worker-lifecycle "服务工作进程生命周期 - 使用服务工作进程管理网络请求和推送通知 | Microsoft Docs"  
[ProgressiveWebAppsWebappmanifests]: ../../../../progressive-web-apps-chromium/webappmanifests.md "使用 Web 应用清单将渐进式 Web 应用集成到操作系统 | Microsoft Docs"  

[GithubMicrosoftVscodeEdgeDevtools]: https://github.com/microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | GitHub"  
<!--[GithubMicrosoftVscodeEdgeDevtoolsPullxxx]: https://github.com/microsoft/vscode-edge-devtools/pull/xxx "Pull xxx: Lorem al Ipsum | GitHub"  -->  

[MicrosoftEdgePreviewChannels]: https://www.microsoftedgeinsider.com/download "Microsoft Edge 预览频道"  

[VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]: https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually "手动更新扩展 - Extension Marketplace | Visual Studio Code"  

[VisualstudioMarketplaceMsEdgedevtoolsVscodeEdgeDevtools]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Tools for Visual Studio Code | Visual Studio Marketplace"  
[VisualstudioMarketplaceMsjsdiagDebuggerForEdge]: https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-edge " Microsoft Edge 调试程序 | Visual Studio Marketplace"  

[BrotliMain]: https://www.brotli.org "Brotli"  

[ChromestatusFeature4752739957473280]: https://chromestatus.com/feature/4752739957473280 "功能：强调色 CSS 属性 | Chrome 平台状态"  

[CsswgDraftsCssUi4WidgetAccent]: https://drafts.csswg.org/css-ui-4/#widget-accent "小组件强调色：强调色属性 - CSS 基本用户界面模块级别 4 | CSS 工作组编辑器草稿"  

[CRIssuesList]: https://bugs.chromium.org/p/chromium/issues/list "Chromium bug"  
[CR11374]: https://crbug.com/v8/11374 "问题 11374：实现专用字段的人体工学品牌检查"  
[CR761019]: https://crbug.com/761019 "问题761019：“转到符号”缺少第一个函数，并且如果包含所有类型化字符，则首选更差的匹配项"  
[CR862450]: https://crbug.com/862450 "问题 862450：[css-scroll-snap] 考虑为 css 滚动贴靠添加 Devtools 功能"  
[CR979000]: https://crbug.com/979000 "问题 979000：具有碰撞源路径的源映射不起作用。"  
[CR1066604]: https://crbug.com/1066604 "问题1066604：DevTools：查看有关 ServiceWorker 安装和激活事件的详细信息 | Chromium bug"  
<!--  [CR1066772]: https://crbug.com/1066772 "Issue 1066772: "  locked  -->  
[CR1076198]：https://crbug.com/1076198“问题1076198：[功能请求] 从 `styles` 选项卡跳转到计算属性”  
[CR1092093]：https://crbug.com/1092093“问题 1092093：通过支持‘accent-color’CSS 属性改进窗体控件的颜色样式”  
[CR1136655]：https://crbug.com/1136655“问题1136655：开发工具：本地化 V2 | Chromium bug”  
[CR1142705]：https://crbug.com/1142705“问题 1142705：使用 Webpack 时，当 2 个源映射指向同一虚拟文件时断点停止工作”  
[CR1149832]：https://crbug.com/1149832“问题 1149832：功能请求：图像预览还应显示文件大小”  
[CR1158827]：https://crbug.com/1158827“问题 1158827：[权限策略] 实现对权限策略的 devtool 支持”  
[CR1162042]：https://crbug.com/1162042“问题 1162042：DevTools：支持禁用 gzip/brotli/jxl content-encoding”  
[CR1166577]：https://crbug.com/1166577“问题 1166577：☂️线性内存检查器 1.0”  
[CR1170656]：https://crbug.com/1170656“问题 1170656：显示内部纵横比”  
[CR1178305]：https://crbug.com/1178305“问题 1178305：调试程序在悬停时不显示已索引元素的属性值”  
[CR1180794]：https://crbug.com/1180794“问题 1180794：断点不适用于关闭编译器内联优化”  
[CR1185945]：https://crbug.com/1185945“问题 1185945：清单警告表示所有图标都必须为方形 | Chromium bug”  
[CR1186049]：https://crbug.com/1186049“问题 1186049：缓存存储查看器中的变化：标头的列”  
[CR1187735]：https://crbug.com/1187735“问题 1187735：辅助功能：MAS2.1.1：键盘：无法使用键盘调用‘Var(..)’函数 | Chromium bug”  
[CR1189161]：https://crbug.com/1189161“问题 1189161：`new Error` 堆栈跟踪未通过 DWARF 进行转换”  
[CR1191465]：https://crbug.com/1191465“问题 1191465：HTML 上的 Ctrl+Shift+O 损坏”  

[GithubW3cWebappsecPermissionsPolicyPermissionsPolicyExplainerMd]: https://github.com/w3c/webappsec-permissions-policy/blob/main/permissions-policy-explainer.md "权限策略解释器 | GitHub"  

[GlitchMemoryInspectorDemoJsHtml]: https://memory-inspector.glitch.me/demo-js.html "JS 中的内存 | 故障"  
[GlitchMemoryInspectorDemoWasmHtml]: https://memory-inspector.glitch.me/demo-wasm.html "Wasm 中的内存 | 故障"  

[GlitchMicrosoftEdgeChromiumDevtoolsCssDbgStoriesCssScrollSnapHtml]: https://microsoft-edge-chromium-devtools.glitch.me/css-dbg-stories/css-scroll-snap.html "滚动贴靠演示 | 故障"  

[GlitchPermissionPolicyDemoMain]: http://permission-policy-demo.glitch.me "OOPIF 权限策略 | 故障"  

[GnuSoftwareGzipManual]: https://www.gnu.org/software/gzip/manual "gzip：数据压缩程序 | GNU 操作系统"  

[HttpwgSpecsRfc7231HtmlHeaderVary]: https://httpwg.org/specs/rfc7231.html#header.vary "变化 - 超文本传输协议 (HTTP/1.1)：语义和内容 | IETF HTTP 工作组"  

[JsWebpackGuidesCodeSplittingTextThereAreThreeGeneralApproachesToCodeSplittingSplitCodeViaInlineFunctionCallsWithinModules]: https://webpack.js.org/guides/code-splitting/#:~:text=There%20are%20three%20general%20approaches%20to%20code%20splitting,Split%20code%20via%20inline%20function%20calls%20within%20modules. "有三种可用的常规代码拆分方法：入口点：使用入口配置手动拆分代码。防止重复：使用条目依赖项或 SplitChunksPlugin 来消除和拆分区块。动态导入：通过模块中的内联函数调用拆分代码。- 代码拆分 | webpack"  

[MdnDocsWebCssUsingCssCustomProperties]: https://developer.mozilla.org/docs/Web/CSS/Using_CSS_custom_properties "使用 CSS 自定义属性（变量）| MDN"  

[MdnDocsWebJavascriptReferenceOperatorsIn]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/in "in 运算符 | MDN"  

[PwabuilderImagegenerator]: https://www.pwabuilder.com/imageGenerator "映像生成器 | PWABuilder"  

[RollupjsMain]: https://rollupjs.org "rollup.js"  

[V8DevFeaturesPrivateBrandChecks]: https://v8.dev/features/private-brand-checks "专用品牌检查 obj 中 a.k.a. #foo | V8"  
[V8DevFeaturesClassFieldsPrivateClassFields]: https://v8.dev/features/class-fields#private-class-fields "专用类字段 - 公共和专用类字段 | V8"  

[WebpackJsMain]: https://webpack.js.org "Webpack"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-91)，并由 [Jecelyn Yeen][JecelynYeen] \（开发人员支持者，Chrome DevTools\）制作。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据 [知识共享署名 4.0 国际许可 ][CCA4IL] 获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[JecelynYeen]: https://developers.google.com/web/resources/contributors#jecelyn-yeen  
