---
description: 从 Visual Studio Code 应用颜色主题，使用新的分离元素工具调试 DOM 节点内存泄漏，Microsoft Edge 开发人员工具 for Visual Studio Code 现在与 Visual Studio Code 调试器工作流集成，等等。
title: 'DevTools (Microsoft Edge 93 中的新增) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/30/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 8661096171f7e40f06d7a2d018193ee61f8b0313e3ab376bad8fad9997cf2219
ms.sourcegitcommit: 841e41de1a32501ece862399fa56170c022127c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2021
ms.locfileid: "11806341"
---
# <a name="whats-new-in-devtools-microsoft-edge-93"></a>DevTools (Microsoft Edge 93 中的新增) 

[!INCLUDE [note about What's New announcements from the Microsoft Edge DevTools team](../../includes/edge-whats-new-note.md)]


## <a name="apply-themes-from-visual-studio-code-to-devtools"></a>将主题从 Visual Studio Code应用到 DevTools

<!-- Title: Apply themes from Visual Studio Code to DevTools -->
<!-- Subtitle: You can now use some of the most popular color themes from Visual Studio Code, such as Monokai and Solarized Dark, in Microsoft Edge DevTools. -->

除了现有浅色和深色主题之外，Microsoft Edge开发人员工具现在还支持来自 Visual Studio Code 的一些最受欢迎的颜色主题。  若要选择颜色主题，请导航到**设置，然后**从"主题"下拉列表**中选择**主题。

:::image type="complex" source="../../media/2021/07/all-devtools-themes.msft.png" alt-text="DevTools 的颜色主题" lightbox="../../media/2021/07/all-devtools-themes.msft.png":::
   DevTools 的颜色主题
:::image-end:::

支持Visual Studio Code主题包括：

浅色主题：
*  太阳光
*  安静光

深色主题：
*  Abyss
*  Kimbie Dark
*  单声道
*  Monokai Dimmed
*  浅色深
*  红色
*  明天晚上蓝色

有关详细信息，请导航到 [将颜色主题应用到 DevTools][CustomizeDarkTheme]。


## <a name="debug-dom-node-memory-leaks-with-the-new-detached-elements-tool"></a>使用新的分离元素工具调试 DOM 节点内存泄漏

:::image type="icon" source="../../media/2020/06/experimental-tag-14px.msft.png":::  

<!-- Title: Introducing the Detached Elements tool -->
<!-- Subtitle: Use the Detached Elements tool to find and fix DOM node memory leaks. -->

如果 DOM 节点不再附加到 DOM 的任何元素，但仍被其他元素保留在内存中，则认为该节点Microsoft Edge。 浏览器无法对元素进行垃圾回收，因为某些 JavaScript 仍在引用元素，即使它不再位于页面上或 DOM 的一部分。

新的 **分离元素工具** 查找页面上的所有分离元素并显示它们。 可以展开和折叠分离的元素，以查看同时保留的父节点和子节点。 通过选择"收集垃圾"并验证当无法对**** 分离的元素进行垃圾回收时是否具有内存泄漏，可以触发浏览器的垃圾回收。 最后，可以通过使用"分析"按钮拍摄堆快照，跳转到引用已分离元素的 JavaScript。 ****

:::image type="complex" source="../../media/2021/07/detached-elements-tool.msft.png" alt-text="分离的元素工具" lightbox="../../media/2021/07/detached-elements-tool.msft.png":::

   分离 **的元素** 工具
:::image-end:::

若要打开此实验，请导航到 **"设置**  >  **实验**"，然后选中"分离**元素"旁边的复选框**。

<!-- For more information, navigate to [Detached elements][ExperimentalFeaturesDetachedElements]. -->
<!-- todo: link directly to the subheading in the page, when available; test the subheading link -->


## <a name="the-visual-studio-code-debugger-now-integrates-with-the-devtools-extension"></a>现在Visual Studio Code调试程序与 DevTools 扩展集成

<!-- Title: While debugging, launch the DevTools extension by selecting the Inspect button -->
<!-- Subtitle: Microsoft Edge DevTools for Visual Studio Code now integrates seamlessly with the JavaScript debugging workflow in the editor. -->

如果你使用 Visual Studio Code 中的 JavaScript 调试，你现在可以通过选择"检查Microsoft Edge启动 Visual Studio Code**开发人员**工具扩展。 ****

:::image type="complex" source="../../media/2021/07/inspect-button.msft.png" alt-text="启动 DevTools Visual Studio Code中的"检查"按钮" lightbox="../../media/2021/07/inspect-button.msft.png":::
   启动**** DevTools Visual Studio Code中的"检查"按钮
:::image-end:::

此功能将 DOM 和 CSS 调试与 Visual Studio Code 中的 JavaScript 调试集成。 如果没有安装 DevTools 扩展，选择"检查"按钮时，Visual Studio Code**** 提示你安装扩展。

其他新功能包括：
*  当你在不同调试目标之间切换时，工具会自动刷新。
*  多个 Bug 修复。
*  扩展的更详细的文档。

有关改进和修复的更多详细信息，请查看 [存储库][GithubMicrosoftVscodeEdgeDevtoolsChangelog] 中的 `vscode-edge-devtools` 更改日志文件。

:::image type="complex" source="../../media/2021/07/extension-integrated-debugger.msft.png" alt-text="与调试器工作流Visual Studio Code DevTools 扩展" lightbox="../../media/2021/07/extension-integrated-debugger.msft.png":::
   与调试器工作流Visual Studio Code DevTools 扩展
:::image-end:::

有关详细信息，请从 JS 调试器工作流导航到启动 Edge [DevTools。][GithubVscodeEdgeDevtoolsDebuggerIntegration]  获取[Microsoft Edge 开发人员工具Visual Studio Code扩展][VisualstudioMarketplaceMsEdgedevtoolsVscodeEdgeDevtools]。  Microsoft Visual Studio代码将自动更新扩展;若要手动更新此扩展，请导航到"[手动更新扩展"。][VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]  你可以在 [vscode-edge-devtools GitHub repo][GithubMicrosoftVscodeEdgeDevtools] 上提交问题并参与扩展的改进。


## <a name="new-fluent-ui-icons-for-devtools"></a>DevTools Fluent UI 图标

<!-- Title: New look for buttons and menus in Microsoft Edge DevTools -->
<!-- Subtitle: DevTools has adopted Fluent UI, giving it a more modern look that better aligns with the rest of the Microsoft Edge browser. -->

Microsoft EdgeDevTools 采用了[Fluent UI，][FluentUI]为按钮和菜单提供更现代的外观，从而更好地与浏览器Microsoft Edge一致。

:::image type="complex" source="../../media/2021/07/fluent-ui.msft.png" alt-text="使用自定义 UI 设计Fluent的 DevTools" lightbox="../../media/2021/07/fluent-ui.msft.png":::
   使用自定义 UI 设计Fluent的 DevTools
:::image-end:::


## <a name="change-the-devtools-display-language-directly-from-settings"></a>直接从用户更改 DevTools 显示设置

<!-- Title: DevTools Settings now includes display language -->
<!-- Subtitle: You can now skip the browser settings and change the DevTools display language directly within DevTools Settings. -->

以前，若要在 DevTools 中更改显示语言，必须更改浏览器语言。  现在，你可以轻松地在 DevTools**设置**切换显示语言，而无需更改浏览器设置。  为此，**请设置"，** 然后在 **"首选项**"中，从"语言"**下拉列表中选择一**种语言。

:::image type="complex" source="../../media/2021/07/settings-browser-ui-language.msft.png" alt-text="直接从 DevTools **设置** 更改 DevTools 显示语言" lightbox="../../media/2021/07/settings-browser-ui-language.msft.png":::
   直接从 DevTools 项目更改 DevTools 显示**设置**
:::image-end:::

默认情况下，DevTools 与浏览器的显示语言匹配。  有关详细信息，请导航到"[更改 DevTools 语言设置"。][CustomizeLocalization]  若要在开放源代码项目中查看Chromium历史记录，请导航到"问题[2882756"。][CR2882756]


## <a name="copy-a-declaration-in-the-styles-pane-for-css-in-js-libraries"></a>复制 CSS-in-JS 库的"样式"窗格中的声明

<!-- Title: Better support for CSS-in-JS libraries -->
<!-- Subtitle: Copy a single declaration or all declarations for a style rule from the Styles pane, formatted for JavaScript. -->

以前，在使用 CSS-in-JS 库时，无法将 CSS 声明 (为 JavaScript 格式化) CSS 属性和值。 您必须编辑复制的 CSS 以匹配 JavaScript 的语法。

现在，Microsoft Edge版本 93 中，您可以复制样式规则中的单个 CSS 声明或所有声明，并将其直接粘贴到 JavaScript 文件中，而无需语法问题。 若要试用此功能，请进行以下设置：

1. 在 **"元素"** 工具的****"样式"窗格中，打开上下文菜单 \ (右键单击\) 样式规则中的声明。
1. 选择 **"将声明复制为 JS"** 或 **"复制所有声明为 JS"。**
1. 将复制的 CSS 粘贴到文本编辑器中的 JavaScript 文件中，如Visual Studio Code。  例如：`'--more-link': 'lime'`。

:::image type="complex" source="../../media/2021/07/copy-declaration-as-js.msft.png" alt-text="样式规则的上下文菜单，包括"Copy declaration as JS"和"Copy all declarations as JS"命令" lightbox="../../media/2021/07/copy-declaration-as-js.msft.png":::
   样式规则的上下文菜单，包括 **Copy declaration as JS** 和 Copy all **declarations as JS** commands
:::image-end:::

若要详细了解如何查看和更改 CSS，请导航到["CSS 引用"。][CssReference]


## <a name="easier-customization-of-user-agent-client-hints"></a>更轻松地自定义User-Agent客户端提示

<!-- Title: Send as many (or as few) Client Hints as you want -->
<!-- Subtitle: Updated UI for User-Agent Client Hints in Emulated Devices settings and in the Network conditions tool. -->

User-Agent客户端提示使浏览器信息比以分号分隔的字符串User-Agent，并提高网站兼容性。  最初，User-Agent客户端提示测试和调试非常耗时。  对客户端提示的控制较少，必须正确填充客户端提示，表单正常运行。

在此版本中，我们重新设计了调试体验，以便你可以轻松User-Agent多个单独字段和控件的 UI 修改客户端提示。  此外，你现在可以同时测试自定义User-Agent提示和User-Agent字符串。  你现在可以在User-Agent网络条件工具中为自定义设备**设置客户端****提示**。

:::image type="complex" source="../../media/2021/07/ua-client-hints-in-settings.msft.png" alt-text="为User-Agent中的自定义设备定义客户端设置" lightbox="../../media/2021/07/ua-client-hints-in-settings.msft.png":::
   为User-Agent中的自定义设备定义客户端**设置**
:::image-end:::

有关在客户端中定义提示**设置，** 请导航到"设置[用户代理客户端提示"。][DeviceModeIndexSetUach]

您还可以使用User-Agent条件工具替代当前页面的客户端 **提示** 。

:::image type="complex" source="../../media/2021/07/ua-client-hints-in-network-conditions.msft.png" alt-text="在User-Agent条件工具中为自定义设备定义客户端提示" lightbox="../../media/2021/07/ua-client-hints-in-network-conditions.msft.png":::
   在User-Agent条件工具中为自定义设备**定义客户端提示**
:::image-end:::

有关在网络条件工具中定义 **提示的信息，** 请导航到设置 [用户代理客户端提示][NetworkReferenceSetUach]。  要在 Chromium 开源项目中查看此功能的历史记录，请导航到问题 [1174299][CR1174299]。


## <a name="screen-readers-now-announce-errors-warnings-and-issues-in-toolbar-and-console"></a>屏幕阅读器现在在工具栏和控制台中声明错误、警告和问题

<!-- Title: Better support for errors, warnings, and issues with assistive technology -->
<!-- Subtitle: Screen readers now correctly announce the number and the type of notification for errors, warnings, and issues in the DevTools toolbar. -->

以前，屏幕阅读器的用户只会听到 DevTools 工具栏中宣布的错误、警告或问题的数量。  不包括通知类型的其他信息，例如"错误"、"警告"或"问题"。 例如，如果 DevTools 报告了 3 个错误，屏幕阅读器将只宣布"3"。

现在，Microsoft Edge版本 93 中，屏幕阅读器正确声明通知的类型和数量;错误、警告或问题。  例如，如果 DevTools 报告 3 个错误和 5 个警告，屏幕阅读器现在会宣布"3 个错误，5 个警告"。  此修补程序已应用于 DevTools 工具栏和控制台中的通知。

:::image type="complex" source="../../media/2021/07/screen-reader-errors-warnings-issues.msft.png" alt-text="工具栏和控制台中的错误、警告和问题 UI" lightbox="../../media/2021/07/screen-reader-errors-warnings-issues.msft.png":::
   工具栏和控制台中的错误、警告和问题 UI ****
:::image-end:::

<!-- It'd be good to have a video of this a11y fix where the text that the screen reader announces is displayed -->

有关调试控制台错误的信息，请导航到" [调试控制台"中报告的错误][ConsoleConsoleDebugJavascript]。  有关 DevTools 发现的问题以及你可以对网页进行改进的信息，请导航到使用问题工具查找并 [修复问题][IssuesIndex]。  若要在开放源代码项目中查看此功能Chromium，请导航到"问题[1223208"。][CR1223208]


## <a name="copy-as-powershell-in-the-network-tool-now-includes-cookies"></a>"网络"工具中的"复制为 PowerShell"现在包含 Cookie

<!-- Title: Generate PowerShell commands for network requests in the Network tool -->
<!-- Subtitle: The Copy as PowerShell context menu option now correctly sets the user-agent string and cookies when generating PowerShell network requests. -->

以前，在**网络**工具中，在**** 网络活动日志中为给定网络请求生成 PowerShell 命令时，复制为  >  **PowerShell**上下文菜单选项不包含 Cookie。 这意味着生成的 PowerShell 命令无法成功提出相同的网络请求（如果需要 Cookie）。

现在，Microsoft Edge版本 93 中，"复制为**PowerShell"** 上下文菜单选项正确设置 devTools User-Agent的 User-Agent 字符串和 Cookie。  生成的 PowerShell 命令现在可以成功提出由 DevTools 观察到的相同网络请求，甚至向依赖 Cookie 的服务器发送请求。

:::image type="complex" source="../../media/2021/07/copy-as-powershell.msft.png" alt-text=""复制为 PowerShell"命令" lightbox="../../media/2021/07/copy-as-powershell.msft.png":::
   " **复制为 PowerShell"** 命令
:::image-end:::

有关网络活动日志详细信息，请导航到"网络[分析参考"。][NetworkReference]  若要在开放源代码项目中查看Chromium历史记录，请导航到"问题[932971"。][CR932971]


## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 [ Microsoft Edge 预览频道][MicrosoftEdgePreviewChannels]作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


## <a name="getting-in-touch-with-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队

[!INCLUDE [contact DevTools team note](../../includes/contact-whats-new-note.md)]


<!-- links -->
[CustomizeDarkTheme]: ../../../customize/theme.md "将颜色主题应用到 DevTools |Microsoft Docs"
<!-- todo: link directly to the subheading in the page, when available; test the subheading link:
[ExperimentalFeaturesDetachedElements]: ../../../experimental-features/index.md#detached-elements "Detached elements | Microsoft Docs" -->
[CustomizeLocalization]: ../../../customize/localization.md "更改 DevTools 语言设置 | Microsoft Docs"
[CssReference]: ../../../css/reference.md "CSS 参考|Microsoft Docs"
[DeviceModeIndexSetUach]: ../../../device-mode/index.md#set-user-agent-client-hints "设置用户代理客户端提示|Microsoft Docs"
[NetworkReferenceSetUach]: ../../../network/reference.md#set-user-agent-client-hints "设置用户代理客户端提示|Microsoft Docs"
[ConsoleConsoleDebugJavascript]: ../../../console/console-debug-javascript.md "在控制台控制台中报告的调试|Microsoft Docs"
[IssuesIndex]: ../../../issues/index.md "使用问题工具查找并修复问题 | Microsoft Docs"
[NetworkReference]: ../../../network/reference.md "网络分析参考|Microsoft Docs"

<!-- external links -->
[FluentUI]: https://developer.microsoft.com/en-us/fluentui#/ "FluentUI |developer.microsoft.com"

[CR1174299]: https://bugs.chromium.org/p/chromium/issues/detail?id=1174299 "问题1174299：通过 Chrome DevTools 的网络条件选项卡重写 UA 字符串时 UA 客户端提示丢失 | Chromium bug"
[CR2882756]: https://chromium-review.googlesource.com/c/devtools/devtools-frontend/+/2882756 "问题2882756：\[l10n\] 为用户添加设置以选择 DevTools 区域设置|Chromium Bug"
[CR1223208]: https://bugs.chromium.org/p/chromium/issues/detail?id=1223208 "屏幕阅读器会针对标题页眉中的错误和警告通知不恰当的|Chromium Bug"
[CR932971]: https://bugs.chromium.org/p/chromium/issues/detail?id=932971 "932971 - &quot;网络&quot;选项卡上，&quot;复制为 Powershell == &quot;未正确发送 cookie |Chromium Bug"

[GithubVscodeEdgeDevtoolsDebuggerIntegration]: https://microsoft.github.io/vscode-edge-devtools/debugger-integration.html "从 JS 调试器工作流启动 Edge DevTools - vscode-edge-devtools |GitHub"

[GithubMicrosoftVscodeEdgeDevtools]: https://github.com/microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | GitHub"
[GithubMicrosoftVscodeEdgeDevtoolsChangelog]: https://github.com/microsoft/vscode-edge-devtools/blob/main/CHANGELOG.md "Changelog 文件 - vscode-edge-devtools |GitHub"

[MicrosoftEdgePreviewChannels]: https://www.microsoftedgeinsider.com/download "Microsoft Edge 预览频道"

[VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]: https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually "手动更新扩展 - Extension Marketplace | Visual Studio Code"

[VisualstudioMarketplaceMsEdgedevtoolsVscodeEdgeDevtools]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Developer Tools for Visual Studio Code | Visual Studio Marketplace"

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/blog/new-in-devtools-xx)，并由 [Jecelyn Yeen][JecelynYeen] \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[JecelynYeen]: https://developers.google.com/web/resources/contributors/jecelynyeen
