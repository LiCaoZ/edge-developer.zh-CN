---
description: 了解开发人员Microsoft Edge工具
title: Microsoft Edge开发人员工具概述
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/23/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge， Web 开发， f12 工具， devtools， Microsoft Edge 开发人员工具
ms.openlocfilehash: 001803883978b31fb566ef9040f23dade5aca7c6
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141283"
---
# <a name="microsoft-edge-developer-tools-overview"></a>Microsoft Edge开发人员工具概述

安装 Microsoft Edge 时，不仅会获取浏览器，还可以获取开发人员工具，这提供了检查、调试甚至创建 Web 项目的强大方法。  Microsoft Edge附带的开发人员工具部分基于 Chromium 开放源代码项目中的工具，因此您可能已经熟悉其中一些工具。  开发人员Microsoft Edge工具也称为Microsoft Edge_开发工具"_ 或 _"DevTools"。_

使用 DevTools，可以执行以下操作：
*   检查并更改浏览器中的当前 网页。
*   模拟你的产品在不同的设备上的行为方式并模拟移动环境，并使用不同的网络条件。
*   使用具有可视界面的 实时工具检查、调整和更改网页中元素的样式。
*   使用断点调试和实时控制台 调试JavaScript。
*   在 产品中查找 辅助功能、性能、兼容性和安全问题，并了解如何使用 DevTools 修复每个问题。
*   检查网络流量 并查看问题的位置。
*   检查浏览器以不同格式存储 内容的位置。
*   评估产品的性能，以查找内存问题和呈现问题。
*   使用开发环境将 DevTools 中的更改与文件系统和 Web 同步。


<!-- ====================================================================== -->
## <a name="opening-devtools"></a>打开 DevTools

若要打开 DevTools，请右键单击网页上的任何项目， **然后单击检查**。

*  或者，在 macOS (上的 `F12` `Ctrl` + `Shift` + `I` Windows/Linux `Command` + `Option` + `I`) 或 (上按) 。

将打开 DevTools，并 **选中"元素** "工具。

:::image type="content" source="./media/devtools-intro-inspect.msft.png" alt-text="若要打开 DevTools，请右键单击网页上的任何项目，然后单击&quot;检查&quot;。":::

:::image type="content" source="./media/devtools-intro-inspect-devtools-open.png" alt-text="DevTools 随即打开，在&quot;元素&quot;工具中突出显示右键单击的元素。":::

有两种主要方式可以与 DevTools 进行交互。
*   使用鼠标。
*   “键盘快捷方式”。  它们提供了快速访问功能的方法，并且辅助功能需要。  Microsoft Edge DevTools 团队致力于使用键盘和辅助技术（如屏幕阅读器）提供所有工具。  请参阅 [键盘快捷方式][DevtoolsGuideShortcutsIndex]。

另请参阅[Open Microsoft Edge DevTools][DevtoolsGuideOpenIndex] - 如何在 DevTools 中打开不同功能。


<!-- ====================================================================== -->
<!-- ## Tools in DevTools -->
<!-- pending PR 1504, which adds destination articles -->
<!-- Tools are also called panels.  Most tools have a tab on the toolbar.

| Tool | Purpose | Article |
|---|---|---|
| Welcome |  |  |
| Elements |  |  |
| Console |  |  |
| Sources |  |  |
| Network |  |  |
| Performance |  |  |
| Memory |  |  |
| Application |  |  |
| Security |  |  |
| Lighthouse |  |  |
| 3D View |  |  |
| Animations |  |  |
| Changes |  |  |
| Coverage |  |  |
| Developer Resources |  |  |
| Issues |  |  |
| JavaScript Profiler |  |  |
| Layers |  |  |
| Media |  |  |
| Memory Inspector |  |  |
| Network conditions |  |  |
| Network request blocking |  |  |
| Performance monitor |  |  |
| Quick source |  |  |
| Rendering |  |  |
| Search |  |  |
| Sensors |  |  |
| WebAudio |  |  |
| WebAuthn |  |  |
| Inspect |  |  | -->
 

<!-- ====================================================================== -->
## <a name="changing-where-devtools-is-docked-in-the-browser"></a>更改 DevTools 在浏览器中的停靠位置

若要更改 DevTools 在浏览器窗口中的位置：：
1.  选择" **自定义和控制 DevTools** `...` () 按钮。
1.  在"开发工具**** 相对于扩展坞 (**放置) ，** 选择布局选项。

:::image type="content" source="./media/devtools-intro-docking-menu.msft.png" alt-text="DevTools 中扩展坞侧菜单的屏幕截图。":::

**扩展坞****向左或向右**，使 DevTools 与 Web 产品并排运行，并且当你模拟移动设备时[，它非常出色](device-mode/index.md)。  **停靠到左侧**，**停靠到右侧**选项与高分辨率显示效果最佳。

**"停靠到右侧** "是 DevTools 的默认位置：

:::image type="content" source="media/devtools-intro-docking-right.msft.png" alt-text="停靠在右侧 DevTools 的屏幕截图。":::

**停靠到左侧** 是另一个并排选项：

:::image type="content" source="media/devtools-intro-docking-left.msft.png" alt-text="停靠在左侧的 DevTools 的屏幕截图。":::

**当你没有足够的** 水平显示空间，或者你想要在 DOM 或控制台中调试长文本时，停靠到底部会 **有所帮助**：

:::image type="content" source="media/devtools-intro-docking-bottom.msft.png" alt-text="固定到底部的 DevTools 的屏幕截图。":::

**在单独的窗口中取消** 停靠可帮助你处理多个监视器，或者如果你需要在全屏应用上工作：

:::image type="content" source="media/devtools-intro-docking-own-window.msft.png" alt-text="DevTools 撤消停靠到单独窗口中的屏幕截图。":::

另请参阅 [DevTools placement (Undock， Dock to bottom， Dock to left) ](customize/placement.md)。


<!-- ====================================================================== -->
## <a name="the-main-tools-on-the-toolbar"></a>工具栏上的主要工具

DevTools 为您提供了一项令人惊叹的功能，可以检查、调试和更改浏览器中当前显示的 Web 产品。  大多数工具实时显示更改。  实时更新使工具非常有用，无需刷新或生成即可优化 Web 项目的外观和导航或功能。  DevTools 还允许你更改计算机上基于 Web 的第三方产品。


### <a name="main-tools-tabs-on-the-toolbar"></a>主要工具 (工具栏) 选项卡

有两个工具栏：DevTools 顶部的主工具栏和底部的"箱"（如果选择**** `Esc` ）。  主工具栏通常具有以下选项卡 (工具或面板) ：

*  **欢迎**。  包括有关 DevTools 的新功能、如何联系团队的信息，并提供有关某些功能的信息。  首先放置此工具。

接下来，工具栏上始终存在以下工具，并且无法关闭：
*  **元素**。  允许您编辑或检查 HTML 和 CSS。  可以在浏览器中实时显示更改时在工具中编辑。
*  [控制台](console/index.md)。  允许您显示和筛选日志消息。  日志消息是浏览器的自动日志，如网络请求和开发人员生成的日志。  还可以在当前窗口或框架的上下文中直接在**** 控制台中运行 JavaScript。
*  [源][DevtoolsGuideSourcesIndex]。  代码编辑器和 JavaScript 调试程序。  可以编辑项目、维护代码段和调试当前项目。
*  [网络][DevtoolsGuideNetworkIndex]。  允许从网络和浏览器缓存中监视和检查请求或响应。  可以筛选请求和响应以满足您的需求并模拟不同的网络条件。

最后，默认情况下，这些 (选项卡) 工具栏上：
* **性能**
* **内存**
* **应用程序**
* **安全**
* **Lighthouse**


### <a name="tool-tab-or-panel"></a>工具、选项卡或面板

通常，"tool"、"tab"或"panel"可以互换使用。  在命令菜单中，这些工具称为 _"面板";_ 例如 **，Elements** 工具称为" **元素"** 面板。  若要切换到"**元素"** 工具，请选择"**元素"** 选项卡。 有一个 **"更多工具**"按钮和列表，工具栏上还有一**** 个"更多选项卡"按钮，这两个按钮都用于选择工具，这也称为 _"面板"。_


### <a name="sections-of-the-toolbar"></a>工具栏的各个部分

DevTools 中的主工具栏包含以下部分：

:::image type="complex" source="./media/devtools-intro-menu-bar.msft.png" alt-text="包含说明不同部分的标签的 DevTools 菜单栏。  顺序为：检查工具、设备仿真工具、工具选项卡组、JavaScript 错误、问题、设置、反馈、自定义和关闭。" lightbox="./media/devtools-intro-menu-bar.msft.png":::
   包含说明不同部分的标签的 DevTools 菜单栏。  顺序为：检查工具、设备仿真工具、工具选项卡组、JavaScript 错误、问题、设置、反馈、自定义和关闭。
:::image-end:::

*   选择" **检查"** 工具时，可以选择当前网页上的某个元素。  当 **Inspect** 工具处于活动状态时，您可以将鼠标移动到网页的不同部分，以获取有关页面元素的详细信息，以及显示页面元素的布局尺寸、填充和边距的多色覆盖层。

    :::image type="content" source="./media/devtools-intro-inspect-tool.msft.png" alt-text="悬停在本文第一个标题的&quot;检查&quot;工具上。":::

*   [设备仿真工具](device-mode/index.md)显示当前 Web 产品处于仿真设备模式下。  **设备仿真工具**允许你在调整浏览器大小时运行和测试产品的反应。  它还为你提供移动设备上的布局和行为估计。

    :::image type="content" source="./media/devtools-intro-device-emulation.msft.png" alt-text="DevTools 在仿真移动电话中显示本文。":::

*   主工具栏包含用于各种方案的工具的选项卡。  您可以自定义每个工具，并且工具的内容可能会基于上下文更改。  若要在隐藏的选项卡上显示工具，请选择"更多选项卡 () **** `>>` 按钮。   To add a tool to the main toolbar or to the drawer's toolbar， select the **More tools** (`+`) button.  下面介绍了每个工具。

*   "工具"选项卡组旁边是可选错误和问题快捷方式。  在当前网页上出现 JavaScript 错误或问题时，会显示快捷方式。  " **打开控制台以查看 # 错误， # 警告** (**JavaScript** 错误) "按钮显示一个红色圆圈，后跟 `X` JavaScript 错误数。  若要打开 [控制台并了解](console/index.md) 错误，请选择 **"JavaScript 错误"** 按钮。  "**查看 # 问题** (问题) 按钮是**** 一个蓝色消息图标，后跟问题数。  若要打开" [问题"][DevtoolsGuideIssuesIndex] 工具，请选择" **问题"** 按钮。

*   " **设置** "按钮显示齿轮图标。  若要在网页中**设置**DevTools，**请选择"设置**按钮。  " **设置** "网页显示一个菜单，用于更改 **首选项**、打开 **实验**等。

*   " **发送反馈** "按钮旁边会显示一个聊天气泡的 Torso。  若要打开" **发送反馈** "对话框，请选择" **发送反馈"** 按钮。  " **发送反馈** "对话框允许你输入描述所发生情况的信息，并自动包含屏幕截图。  使用 **发送反馈** 与 DevTools 团队联系，以报告问题、问题或建议想法。

*   " **自定义和控制 DevTools** `...` () 按钮将打开一个下拉菜单。  它允许你定义扩展 DevTools、搜索、打开不同工具等位置。


<!-- ====================================================================== -->
## <a name="power-tip-use-the-command-menu"></a>电源提示：使用命令菜单

DevTools 提供了许多要用于 Web 产品的特性和功能。  可以通过多种方式访问 DevTools 的不同部分，但通常一种快速的方式是使用命令菜单。

在命令菜单中，这些工具称为"面板";例如 **，Elements** 工具称为" **元素"** 面板。  若要切换到" **元素"** 工具，请选择" **元素"** 选项卡。

若要打开命令菜单，请执行下列任一操作：

*   按 `Control` + `Shift` + `P` (Windows、Linux) `Command` + `Shift` + `P` 或 (macOS) 。
*   单击 **"自定义和控制 DevTools** `...` () "，然后选择"运行**命令"。**

:::image type="content" source="./media/devtools-intro-command-menu.msft.png" alt-text="DevTools 中命令菜单的屏幕截图。":::

命令菜单允许你键入命令以在 DevTools 中显示、隐藏或运行功能。  打开命令菜单后，输入单词**changes**，然后选择"**箱： 显示更改"。**  The **Changes** tool opens, which is useful when you edit CSS.  在这种情况下，命令菜单提供了快速替代方法，选择"更多工具" (...) ，然后选择"更改"，或在"源"**** 工具中编辑文件，然后右键单击并选择"本地修改**** `.js` **"。** ****

键入 后，命令菜单将显示选项 `changes` ：

:::image type="content" source="./media/devtools-intro-command-menu-show-changes.msft.png" alt-text="键入更改后，命令菜单将显示选项。":::

打开"更改" **工具的** DevTools：

:::image type="content" source="./media/devtools-intro-showing-changes.msft.png" alt-text="打开&quot;更改&quot;工具的 DevTools。":::

另请参阅[使用开发人员工具Microsoft Edge菜单运行命令](command-menu/index.md)。


<!-- ====================================================================== -->
## <a name="customizing-devtools"></a>自定义 DevTools

你可以自定义 DevTools 以满足你对工作方式的需求。  若要更改设置，请执行下列任一操作：
*   选择**设置 (** 右上角的齿轮图标) 。
*   选择 `F1` 或 `?`。

在 **首选项部分中** ，你可以更改 DevTools 的几个部分。  例如，可以使用"匹配浏览器语言 **"设置** 在 DevTools 中使用浏览器中使用的相同语言。  有关另一个示例，请使用 **Theme** 设置更改 DevTools 的颜色主题。

:::image type="content" source="media/devtools-intro-all-settings.msft.png" alt-text="DevTools 中所有设置的屏幕截图。":::

您还可以更改高级功能的设置，例如：
*   [工作区][DevtoolsGuideWorkspacesIndex]。
*   具有 **"忽略列表"** 的筛选器库代码。
*   定义 **设备** 模拟和测试模式下要包括的设备。  有关详细信息，请参阅在[DevTools 中模拟Microsoft Edge移动设备](device-mode/index.md)。
*   选择网络 **限制** 配置文件。
*   定义模拟 **位置**。
*   自定义键盘 **快捷方式**。  例如，若要在 DevTools 中使用相同的快捷方式，Visual Studio Code预设选项中的"匹配****  >  **Visual Studio Code"。**

    :::image type="content" source="./media/devtools-intro-match-keys.msft.png" alt-text="所有键盘快捷方式和菜单的屏幕截图，用于将每个快捷方式与 Visual Studio Code。":::


<!-- ====================================================================== -->
## <a name="trying-experimental-features"></a>尝试实验性功能

DevTools 团队在 DevTools _中提供_ 新功能作为实验。  你可以打开或关闭每个实验。  To see the full list of [Experimental features](experimental-features/index.md)， in DevTools， select**设置 (** the gear icon) ， and then select **Experimental**.

若要预览即将[在 DevTools 中][DevtoolsGuideWhatsNew202102Devtools]提供的最新功能，请[下载Microsoft Edge Canary，][MicrosoftedgeinsiderDownload]它夜间生成。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [适用于初学者的 DevTools：入门 HTML 和 DOM](beginners/html.md)
*   [检查并更改当前网页](dom/index.md)
*   [模拟你的产品在不同设备上的行为方式](device-mode/index.md)
*   [检查、调整和更改元素的样式][DevtoolsGuideInspectStylesEditFonts]
*   [调试 JavaScript][DevtoolsGuideJavascriptIndex]
*   [实时控制台](console/index.md)
*   [辅助功能、性能、兼容性和安全问题][DevtoolsGuideIssuesIndex]
*   [检查网络流量][DevtoolsGuideNetworkIndex]
*   [检查浏览器存储内容的位置][DevtoolsGuideStorageSessionstorage]
*   [评估性能](evaluate-performance/index.md)
*   [内存问题](memory-problems/index.md)
*   [呈现问题][DevtoolsGuideRenderingToolsIndex]
*   [使用开发环境][DevtoolsGuideSourcesIndex]
*   [将 DevTools 中的更改与文件系统同步][DevtoolsGuideWorkspacesIndex]
*   [替代 Web 中的文件][DevtoolsGuideJavascriptOverrides]


<!-- ====================================================================== -->
<!-- links -->
[DevtoolsGuideInspectStylesEditFonts]: ./inspect-styles/edit-fonts.md "在&quot;样式&quot;窗格中编辑 CSS 字体样式|Microsoft Docs"
[DevtoolsGuideIssuesIndex]: ./issues/index.md "使用问题工具查找并修复问题 | Microsoft Docs"
[DevtoolsGuideJavascriptIndex]: ./javascript/index.md "在 Microsoft Edge 开发工具中调试 JavaScript 入门 | Microsoft Docs"
[DevtoolsGuideJavascriptOverrides]: ./javascript/overrides.md "使用 Microsoft Edge DevTools 应用替代具有本地副本的网页|Microsoft Docs"
[DevtoolsGuideNetworkIndex]: ./network/index.md "使用 Microsoft Edge DevTools 检测网络活动 | Microsoft Docs"
[DevtoolsGuideOpenIndex]: ./open/index.md "打开 Microsoft Edge 开发人员工具 | Microsoft Docs"
[DevtoolsGuideRenderingToolsIndex]: ./rendering-tools/index.md "分析运行时性能|Microsoft Docs"
[DevtoolsGuideShortcutsIndex]: ./shortcuts/index.md "键盘快捷方式|Microsoft Docs"
[DevtoolsGuideSourcesIndex]: ./sources/index.md "源工具概述 | Microsoft Docs"
[DevtoolsGuideStorageSessionstorage]: ./storage/sessionstorage.md "使用 Microsoft Edge DevTools 工具查看和编辑|Microsoft Docs"
[DevtoolsGuideWhatsNew202102Devtools]: ./whats-new/2021/02/devtools.md "DevTools （Microsoft Edge 90） 中的新增功能|Microsoft Docs"
[DevtoolsGuideWorkspacesIndex]: ./workspaces/index.md "使用工作区编辑文件 | Microsoft Docs"
<!-- external links -->
[MicrosoftEdgeAddonsExtensions]: https://microsoftedge.microsoft.com/addons/category/Edge-Extensions "Microsoft Edge 加载项"
[MicrosoftedgeinsiderDownload]: https://www.microsoftedgeinsider.com/download "下载 Microsoft Edge 预览体验成员频道"
[GoogleChromeWebstoreExtensions]: https://chrome.google.com/webstore/category/extensions "扩展|Chrome Web Store"
