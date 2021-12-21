---
title: 'DevTools (Microsoft Edge 96) '
description: 焦点模式和垂直活动栏。  自动最小化控制台。  在网站中Visual Studio Code网页、模拟设备，以及查看编辑时的问题。  源工具在无法加载源图时通知你。  如果 Sources 已打开，则使用源，而不是Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 11/16/2021
ms.openlocfilehash: 5219c39754b621fec918894561bb8944c2fc1fcd
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286637"
---
# <a name="whats-new-in-devtools-microsoft-edge-96"></a>DevTools 96 (Microsoft Edge中的新增) 

以下部分列出了 Microsoft Edge 开发人员工具团队的公告。  若要试用 DevTools 的最新功能和适用于 Microsoft Edge 的 DevTools Visual Studio Code，请阅读这些通知。  若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 Microsoft Edge Canary 预览通道作为默认开发浏览器。  预览频道使你可以访问开发人员工具Microsoft Edge功能。


<!-- ====================================================================== -->
## <a name="new-devtools-ui-available-in-preview"></a>预览版中提供的新 DevTools (UI) 

<!-- Title: New DevTools UI available (in preview) -->
<!-- Subtitle: A more minimal, modern UI is coming to Microsoft Edge DevTools. Enable the "Focus Mode" experiment to preview new UI features such a more compact toolbar that keeps DevTools uncluttered and better adapts to small window sizes. -->

开发人员Microsoft Edge团队正在试验新的 DevTools UI：焦点**模式**。  焦点模式通过更现代、更简化的布局减少干扰和混乱。  新的活动栏允许你在水平或垂直工具栏中固定常用工具，以更有效地使用屏幕空间。

若要在 Microsoft Edge 版本 96 中试用此新 UI，设置 (**** ![ DevTools) > ](../../../media/settings-gear-icon-light-mode.png) **实验**  >  **** 焦点模式中的 设置 齿轮图标。

从Microsoft Edge版本 96 开始，实验的复选框标记为焦点模式，而不是焦点**** 模式和开发人员工具**提示**。

此 UI 仍处于开发阶段，可能在将来版本的 Microsoft Edge。  我们期待听到你有关此新 DevTools UI 的反馈。  通过推文将反馈发送给我们[@EdgeDevTools。](https://twitter.com/edgedevtools)  或者，在打开**** 焦点模式实验后，在活动栏底部，选择"**** 帮助 **" ("** 焦点模式的活动栏中的"帮助"图标) >反馈"，以显示"发送反馈 ![ ](../../../media/help-icon-of-focus-mode.png) "窗口****。 ****

:::image type="content" source="../../media/2021/11/focus-mode.png" alt-text="焦点模式，包括活动栏。":::

另请参阅：
*  [实验功能](../../../experimental-features/index.md#focus-mode)_中的焦点模式_。
*  [DevTools：存储库的焦点](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/main/DevTools/FocusMode/explainer.md) 模式 `MSEdgeExplainers` UI。


<!-- ====================================================================== -->
## <a name="console-can-once-again-appear-in-the-top-and-bottom-panels"></a>控制台可以再次显示在顶部和底部面板中

<!-- Title: Fix: Console can be quickly toggled in top or bottom panel -->
<!-- Subtitle: By popular demand, you can now easily show or collapse Console in the bottom panel without having to move the tool. -->

自[Microsoft Edge版本 87](../../2020/10/devtools.md#move-tools-between-top-and-bottom-panels)起，你已在顶部和底部面板之间移动任何工具，包括控制台工具。  但是，我们从开发人员得知，重复移动控制台工具很麻烦。  自 Microsoft Edge 版本 96 起，控制台工具的默认体验已恢复，使你可以快速切换顶部面板) 中的控制台 (的全屏视图和拆分屏幕视图 (控制台显示在底部面板) 中，而无需移动控制台工具。

当 **另** 一个工具打开时，可在 **" (") ** 底部面板中打开控制台：

:::image type="content" source="../../media/2021/11/console-displayed-when-elements-tab-selected.png" alt-text="在主工具栏中选择除控制台外的工具时，&quot;箱&quot;将打开并显示控制台。":::

在 **顶部** 面板中选择"控制台"时，如果底部面板显示控制台，则底部面板将自动 **最小化**：

:::image type="content" source="../../media/2021/11/console-hidden-when-console-tab-selected.png" alt-text="在主工具栏中选择&quot;控制台&quot;时，如果&quot;箱&quot;显示控制台，则自动最小化&quot;箱&quot;。":::

如果你希望仅允许控制台工具在单个位置打开，可以配置控制台的行为。  在主工具栏或"**箱"** 工具栏中，右键单击"控制台 **"选项卡，** 然后选择"配置**控制台"。**  将显示**设置**  >  **首选项**"页。  在"**控制台"** 部分，清除"**** 在主面板和收银机中显示控制台"**** 选项卡复选框，然后单击"关闭 (**x) "** 。


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools-visual-studio-code-extension"></a>Microsoft Edge DevTools Visual Studio Code扩展

有关此扩展的常规信息，请参阅 Microsoft Edge [DevTools extension for Visual Studio Code。](../../../../visual-studio-code/microsoft-edge-devtools-extension.md)

<!-- Title: Dockable browser screencast, device emulation, and live issue reporting, and in Microsoft Edge DevTools for Visual Studio Code -->
<!-- Subtitle: Display your web project inside the editor, simulate different devices, and get notified about issues with your code while you develop it. --> 

### <a name="display-your-web-project-inside-the-editor-and-simulate-different-devices"></a>在编辑器中显示 Web 项目，并模拟不同的设备

适用于 Microsoft Edge 扩展的 Visual Studio Code Tools 现在具有可停靠的屏幕广播和设备仿真：

:::image type="content" source="../../media/2021/11/edge-devtools-for-vscode-toggle-screencast.png" alt-text="单击屏幕广播图标以查看浏览器Visual Studio Code。":::

您可以在 Web 项目的专用选项卡中查看 Visual Studio Code，还可以模拟各种设备：

:::image type="content" source="../../media/2021/11/edge-devtools-for-vscode-simulated-iphone-red-boxes.png" alt-text="显示仿真文档 5 中当前文档的屏幕iPhone大小正确且具有模拟触摸屏界面。":::

有关设备仿真的详细信息，请参阅屏幕广播 [中的设备仿真](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#device-emulation-in-the-screencast)。

### <a name="live-inline-issue-reporting"></a>实时内联问题报告

扩展现在还具有实时内联问题报告功能。  无需在单独的工具中找出问题，Visual Studio Code突出显示源代码中的问题，并实时报告它们，同时输入代码：

:::image type="content" source="../../media/2021/11/edge-devtools-for-vscode-inline-issue-reporting-addl-red.png" alt-text="一段代码内报告的辅助功能问题，用于显示如何修复该问题以及在何处查找详细信息。":::

有关详细信息，请参阅 [内联和实时问题分析](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#inline-and-live-issue-analysis)。


<!-- ====================================================================== -->
## <a name="sources-tool-now-notifies-you-when-sourcemaps-cant-be-loaded"></a>源工具现在将在无法加载源图时通知你

<!-- Title: Get notified when DevTools cannot load your sourcemaps correctly -->
<!-- Subtitle: The Sources tool now provides several places in the UI when DevTools can't fetch or parse your sourcemaps. -->

在 Microsoft Edge版本 96 中****，当 DevTools 无法加载源图时，源工具现在在 UI 中提供几个指示。  在"**源"** 工具中****"导航器"窗格的****"页面"选项卡中，DevTools 无法加载源图的文件具有一个警告图标来表示文件图标。  

选择带警告图标的文件将在"源"工具中打开该文件，其中显示一个信息栏，指示 DevTools 无法从服务器正确获取源图或无法正确分析源图：

:::image type="content" source="../../media/2021/11/source-map-not-found-buttons.png" alt-text="源工具现在将在无法加载源图时在&quot;问题&quot;选项卡中通知你。":::

从信息栏中，可以通过选择"在问题中打开"按钮了解有关 **问题** 详细信息。  然后 **，"** 问题"工具在****"箱"中打开，并提供有关如何在 DevTools 中解决问题和正确加载源图的信息：

:::image type="content" source="../../media/2021/11/source-map-not-found.png" alt-text="源工具现在将在无法加载源图时在&quot;问题&quot;选项卡中通知你。":::

若要防止有关源图的信息栏使"源"工具变得**** 混乱，请选择"**不要再次显示"** 按钮。  若要防止与源图相关的问题使"问题"工具变得**** 混乱，请清除"**** 问题"工具中的"包括第三方问题 **"** 复选框。  若要了解有关 DevTools 如何提取和分析源图的更多信息，请参阅将 [预处理的代码映射到源代码](../../../javascript/source-maps.md)。


<!-- ====================================================================== -->
## <a name="opening-source-files-in-visual-studio-code-now-integrates-better-with-the-sources-tool"></a>现在，在Visual Studio Code源文件与"源"工具更好地集成

<!-- Title: Open source files directly in Visual Studio Code from DevTools -->
<!-- Subtitle: The "Open source files in Visual Studio Code" experiment now works more intuitively with the Sources tool. -->

在早期版本的 Microsoft Edge中，如果已在 DevTools 中使用"源"工具Visual Studio Code打开 Visual Studio Code 试验中的"源"文件****，则发生意外行为。 ****  设置断点将指导你Visual Studio Code文档以正确配置实验。

在 Microsoft Edge 版本 96 中，Visual Studio Code**中的开放**源文件现在与"源"工具**更好地**集成。

*  如果"**** 源"工具已打开，然后打开**Visual Studio Code**实验中的"开放源文件"，那么设置断点或打开文件现在将打开"**** 源"工具，而不是Visual Studio Code或文档以正确配置实验。

   :::image type="content" source="../../media/2021/11/sources-tool-versus-open-in-vs-code.png" alt-text="如果&quot;源&quot;工具已打开，设置断点或打开文件将打开&quot;源&quot;工具，即使随后打开&quot;打开 Visual Studio Code 文件&quot;实验。":::

*  与早期版本的 Microsoft Edge 一样，如果源工具**** 未在 DevTools 中打开，然后打开 Visual Studio Code 实验中的开放源文件，设置断点或从除"源"工具外的其他工具打开文件将在**Visual Studio Code**中打开文件。 ****

若要了解有关 DevTools 如何与 Visual Studio Code 集成，请参阅在 Visual Studio Code[中打开源文件](../../../sources/opening-sources-in-vscode.md)。


<!-- ====================================================================== -->
## <a name="selecting-the-dropdown-triangle-icon-in-the-devtools-ui-now-opens-the-menu"></a>选择 DevTools UI 中的下拉三角形图标现在将打开菜单

<!-- Title: Dropdown menus in the DevTools UI are now more intuitive -->
<!-- Subtitle: Select the triangle icon to expand any dropdown menu in the DevTools UI. -->

在早期版本的 Microsoft Edge DevTools 中，选择下拉菜单旁边的三角形图标不显示下拉菜单。  若要打开下拉菜单，必须单击三角形图标左侧当前选择的菜单项，例如"**无限制"：**

:::image type="content" source="../../media/2021/11/clicking-triangle-didnt-open-dropdown.png" alt-text="单击下拉列表的三角形图标未打开下拉列表。":::

在 Microsoft Edge 96 版本中，此问题已修复。  选择 DevTools 中任何下拉菜单的三角形图标现在将打开下拉菜单：

:::image type="content" source="../../media/2021/11/clicking-triangle-opens-dropdown.png" alt-text="单击三角形图标现在将打开下拉列表。":::

<!-- This fix applies to various tools, including:
* Performance
* Memory
* Network
* Console
* Device Emulation. -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> Chromium 项目中通知的原始页面是[What's New in DevTools (Chrome 96) ，](https://developer.chrome.com/blog/new-in-devtools-96)由[Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer（在 Google) 上处理 Chrome DevTools 的开发人员宣传）创作。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
