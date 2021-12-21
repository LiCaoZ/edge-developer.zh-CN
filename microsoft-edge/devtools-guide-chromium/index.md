---
title: Microsoft Edge 开发人员工具概述
description: 了解开发人员Microsoft Edge工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge， Web 开发， f12 工具， 开发工具， Microsoft Edge 开发人员工具
ms.date: 09/23/2021
ms.openlocfilehash: 111335454c53827f47c85113778a69f5f0a4c615
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284810"
---
# <a name="microsoft-edge-developer-tools-overview"></a>Microsoft Edge 开发人员工具概述

安装Microsoft Edge时，不仅会获得浏览器，还会获得开发人员工具，这提供了一种用于检查、调试甚至创建 Web 项目的强大方法。  随Microsoft Edge附带的开发人员工具部分基于 Chromium 开源项目中的工具，因此你可能已经熟悉其中一些工具。  Microsoft Edge 开发人员工具也称为_Microsoft Edge DevTools，_ 或只是_DevTools。_

使用 DevTools 可以执行以下操作：
*   检查并更改浏览器中的当前 网页。
*   模拟产品在不同设备上的行为方式，并模拟具有不同网络条件的移动环境。
*   使用具有可视界面的 实时工具检查、调整和更改网页中元素的样式。
*   使用断点调试和实时控制台 调试JavaScript。
*   在 产品中查找 辅助功能、性能、兼容性和安全问题，并了解如何使用 DevTools 修复每个问题。
*   检查网络流量 并查看问题的位置。
*   检查浏览器以不同格式存储 内容的位置。
*   评估产品的性能，以查找内存问题和呈现问题。
*   使用开发环境将 DevTools 中的更改与文件系统和 Web 同步。


<!-- ====================================================================== -->
## <a name="opening-devtools"></a>打开 DevTools

若要打开 DevTools，请右键单击网页上的任何项目，然后单击 **"检查"**。

*  或者，按 `F12`， 或按 `Ctrl`+`Shift`+<>`I`（在 Windows/Linux 上）或 `Command`+`Option`+`I`（在 macOS 上）。

DevTools 随即打开，其中选择了 **元素**工具。

:::image type="content" source="./media/devtools-intro-inspect.msft.png" alt-text="若要打开 DevTools，请右键单击网页上的任何项目，然后单击&quot;检查&quot;。":::

:::image type="content" source="./media/devtools-intro-inspect-devtools-open.png" alt-text="DevTools 随即打开，在 Elements 工具中突出显示了右键单击的元素。":::

可通过两种主要方式与 DevTools 进行交互。
*   使用鼠标。
*   “键盘快捷方式”。  这些提供了访问功能的快速方法，并且是辅助功能所必需的。  Microsoft Edge DevTools 团队致力于使用键盘和辅助技术（如屏幕阅读器）提供所有工具。  请参阅 [键盘快捷方式](./shortcuts/index.md)。

另请参阅 [Open Microsoft Edge DevTools](./open/index.md) - 如何在 DevTools 中打开不同的功能。


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
## <a name="changing-where-devtools-is-docked-in-the-browser"></a>更改 DevTools 停靠在浏览器中的位置

若要更改 DevTools 放置在浏览器窗口中的位置，请执行以下操作：
1.  选择" **自定义和控制 DevTools** (`...`) "按钮。
1.  在相对于页面（**扩展坞端**）**的 DevTools**放置的右侧，选择布局选项。

:::image type="content" source="./media/devtools-intro-docking-menu.msft.png" alt-text="DevTools 中&quot;扩展坞&quot;菜单的屏幕截图。":::

**停靠到左侧** 或 **停靠到右侧** 时，DevTools 与 Web 产品并排，在 [模拟移动设备](device-mode/index.md)时非常出色。  **停靠到左侧**，**停靠到右侧**选项与高分辨率显示效果最佳。

**停靠到右侧** 是 DevTools 的默认位置：

:::image type="content" source="media/devtools-intro-docking-right.msft.png" alt-text="停靠在右侧的 DevTools 的屏幕截图。":::

**停靠到左侧** 是另一个并行选项：

:::image type="content" source="media/devtools-intro-docking-left.msft.png" alt-text="停靠在左侧的 DevTools 的屏幕截图。":::

当你没有足够的水平显示空间，或者你想在 DOM 或 **Console** 中调试长文本时，**停靠到底部**可以帮助你：

:::image type="content" source="media/devtools-intro-docking-bottom.msft.png" alt-text="停靠在底部的 DevTools 的屏幕截图。":::

**取消停靠到单独的窗口** 可帮助你使用多个监视器，或者如果需要使用全屏应用：

:::image type="content" source="media/devtools-intro-docking-own-window.msft.png" alt-text="已取消停靠到单独窗口的 DevTools 的屏幕截图。":::

请参阅[更改 DevTools 放置位置（取消停靠，停靠到底部，停靠到左侧）](customize/placement.md)。


<!-- ====================================================================== -->
## <a name="the-main-tools-on-the-toolbar"></a>工具栏上的主要工具

DevTools 为您提供了一项令人惊叹的功能，可以检查、调试和更改浏览器中当前显示的 Web 产品。  大多数工具实时显示更改。  实时更新使工具非常有用，无需刷新或生成即可优化 Web 项目的外观和导航或功能。  DevTools 还允许你更改计算机上基于 Web 的第三方产品。


### <a name="main-tools-tabs-on-the-toolbar"></a>工具栏上的主要工具（选项卡）

有两个工具栏：DevTools 顶部的主工具栏，以及底部的 **抽屉**（如果选择 `Esc`）。  主工具栏通常具有以下选项卡（或工具或面板）：

*  **欢迎**。  包括有关 DevTools 的新功能、如何联系团队的信息，并提供有关某些功能的信息。  此工具先放置。

接下来，工具栏上始终存在以下工具，无法关闭：
*  **元素**。  允许您编辑或检查 HTML 和 CSS。  可以在浏览器中实时显示更改时在工具中进行编辑。
*  [控制台](console/index.md)。  允许您显示和筛选日志消息。  日志消息是浏览器的自动日志，如网络请求和开发人员生成的日志。  您也可以在当前窗口或框架的上下文中直接在**控制台**中运行JavaScript。
*  [源](./sources/index.md)。  代码编辑器和 JavaScript 调试程序。  可以编辑项目、维护代码段和调试当前项目。
*  [网络](./network/index.md)。  允许从网络和浏览器缓存中监视和检查请求或响应。  可以筛选请求和响应，以满足你的需求并模拟不同的网络条件。

最后，默认情况下，这些更专用的工具（选项卡）位于工具栏上：
* **性能**
* **内存**
* **应用程序**
* **安全**
* **Lighthouse**


### <a name="tool-tab-or-panel"></a>工具、选项卡或面板

通常可以互换使用单词"tool"、"tab"或"panel"。  在命令菜单中，这些工具称为 _面板_;例如，" **元素** "工具称为 **"元素** "面板。  若要切换到 **"元素** "工具，请选择" **元素"** 选项卡。 有一个 **"更多工具"** 按钮和列表，工具栏上有一个 **"更多选项卡** "按钮，这两个选项卡都用于选择工具，也称为 _面板_。


### <a name="sections-of-the-toolbar"></a>工具栏的各部分

DevTools 中的主工具栏包含以下部分：

:::image type="complex" source="./media/devtools-intro-menu-bar.msft.png" alt-text="DevTools 的菜单栏，其中包含用于解释不同部分的标签。  顺序为：检查工具、设备仿真工具、工具选项卡组、JavaScript 错误、问题、设置、反馈、自定义和关闭。" lightbox="./media/devtools-intro-menu-bar.msft.png":::
   DevTools 的菜单栏，其中包含用于解释不同部分的标签。  顺序为：检查工具、设备仿真工具、工具选项卡组、JavaScript 错误、问题、设置、反馈、自定义和关闭。
:::image-end:::

*   选择 **"检查** "工具时，可以选择当前网页上的元素。  当 **"检查** "工具处于活动状态时，可以将鼠标移动到网页的不同部分，以获取有关页面元素的详细信息，以及显示页面元素的布局尺寸、填充和边距的多色覆盖。

    :::image type="content" source="./media/devtools-intro-inspect-tool.msft.png" alt-text="将鼠标悬停在上方时显示本文的第一个标题的&quot;检查&quot;工具。":::

*   [设备仿真工具](device-mode/index.md)显示当前 Web 产品处于仿真设备模式下。  **设备仿真工具**允许你在调整浏览器大小时运行和测试产品的反应。  它还为你提供移动设备上的布局和行为估计。

    :::image type="content" source="./media/devtools-intro-device-emulation.msft.png" alt-text="在仿真移动电话中显示本文的 DevTools。":::

*   主工具栏包含各种方案中使用的工具的选项卡。  可以自定义每个工具，并且工具的内容可以根据上下文进行更改。  若要显示隐藏的选项卡上的工具，请选择" **更多"选项卡** （`>>`）按钮。   若要将工具添加到主工具栏或抽屉的工具栏，请选择**更多工具**（`+`）按钮。  下面介绍了每个工具。

*   "工具"选项卡组旁边是可选错误和问题快捷方式。  在当前网页上出现 JavaScript 错误或问题时，会显示快捷方式。  打开**控制台以查看 # 个错误，# 个警告****（JavaScript 错误**）按钮显示一个红色圆圈，其中包含`X`，后跟 JavaScript 错误数。  若要打开 [控制台](console/index.md) 并了解错误，请选择 **"JavaScript 错误** "按钮。  " **打开问题以查看问题数** （**问题**）"按钮是蓝色消息图标，后跟问题数。  若要打开["问题 "](./issues/index.md) 工具，请选择" **问题"** 按钮。

*   " **设置** "按钮显示齿轮图标。  若要打开"DevTools **设置"** 网页，请选择 **"设置 "** 按钮。  " **设置** "网页显示一个菜单，用于更改 **首选项**、打开 **实验**等。

*   " **发送反馈** "按钮显示旁边有一个聊天气泡的 torso。  若要打开" **发送反馈** "对话框，请选择" **发送反馈"** 按钮。  " **发送反馈** "对话框允许你输入描述所发生情况的信息，并自动包含屏幕截图。  使用 **"发送反馈** "与 DevTools 团队联系，报告问题、问题或提出建议。

*   " **自定义和控制 Devtools**(`...`) "按钮将打开一个下拉菜单。  它允许你定义停靠 DevTools、搜索、打开不同工具等的位置。


<!-- ====================================================================== -->
## <a name="power-tip-use-the-command-menu"></a>电源提示：使用命令菜单

DevTools 提供了许多要用于 Web 产品的特性和功能。  可以通过多种方式访问 DevTools 的不同部分，但通常使用命令菜单是一种快速方法。

在命令菜单中，工具称为"面板";例如，" **元素** "工具称为 **"元素** "面板。  若要切换到 **"元素** "工具，请选择" **元素"** 选项卡。

若要打开命令菜单，请执行以下任一操作：

*   按`Control`+`Shift`+`P`（Windows、Linux）或 `Command`+`Shift`+`P` （macOS）。
*   单击 **自定义并控制 DevTools**(`...`) ， 然后选择 **"运行"命令**.

:::image type="content" source="./media/devtools-intro-command-menu.msft.png" alt-text="DevTools 中命令菜单的屏幕截图。":::

通过命令菜单，可以键入命令以在 DevTools 中显示、隐藏或运行功能。  打开命令菜单后，输入 **"更改"** 一词，然后选择"**箱:显示更改"**。  **更改**工具随即打开，这在编辑 CSS 时非常有用。  在这种情况下，命令菜单提供了一个快速替代方法，即选择 **"更多工具**"（...），然后选择"**更改**"，或在"**源**"工具中编辑`.js`文件，然后右键单击并选择 **"本地修改**"。

键入 `changes`后，命令菜单将显示选项：

:::image type="content" source="./media/devtools-intro-command-menu-show-changes.msft.png" alt-text="键入更改后，命令菜单将显示选项。":::

打开 **"更改** "工具的 DevTools：

:::image type="content" source="./media/devtools-intro-showing-changes.msft.png" alt-text="打开&quot;更改&quot;工具的 DevTools。":::

另请参阅[使用 Microsoft Edge 开发人员工具命令菜单运行命令](command-menu/index.md)。


<!-- ====================================================================== -->
## <a name="customizing-devtools"></a>自定义 DevTools

可以自定义 DevTools 以满足工作方式的需求。  若要更改设置，请执行以下任一操作：
*   选择 **"设置"（** 右上角的齿轮图标）。
*   选择 `F1` 或 `?`。

在 **"首选项"** 部分中，可以更改 DevTools 的多个部分。  例如，可以使用 **"匹配浏览器语言** "设置在 DevTools 中使用浏览器中使用的相同语言。  有关另一个示例，请使用 **Theme** 设置更改 DevTools 的主题。

:::image type="content" source="media/devtools-intro-all-settings.msft.png" alt-text="DevTools 中所有设置的屏幕截图。":::

还可以更改高级功能的设置，例如：
*   [工作区](./workspaces/index.md)。
*   具有 **"忽略列表"** 的筛选器库代码。
*   定义 **设备** 模拟和测试模式下要包括的设备。  有关详细信息，请导航到 [在Microsoft Edge DevTools中模拟移动设备](device-mode/index.md)。
*   选择网络 **限制** 配置文件。
*   定义模拟 **位置**。
*   自定义键盘**快捷方式**。  例如，若要在 DevTools 中使用与在 Visual Studio Code 中相同的快捷方式，请**从预设中选择"匹配快捷方式** > **"Visual Studio Code。**

    :::image type="content" source="./media/devtools-intro-match-keys.msft.png" alt-text="与Visual Studio Code中的快捷方式匹配的所有键盘快捷方式和菜单的屏幕截图。":::


<!-- ====================================================================== -->
## <a name="trying-experimental-features"></a>正在尝试试验性功能

DevTools 团队在 DevTools 中提供新功能作为_实验_。  可以打开或关闭每个试验。  若要查看[体验功能](experimental-features/index.md)的完整列表，请在 DevTools 中选择**设置**（齿轮图标），然后选择**实验**。

若要预览 [即将推出的 DevTools 最新功能](./whats-new/2021/02/devtools.md)，请下载 [Microsoft Edge Canary，](https://www.microsoftedgeinsider.com/download)该功能在夜间生成。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [面向初学者的 DevTools：HTML 和 DOM 入门](beginners/html.md)
*   [检查并更改当前网页](dom/index.md)
*   [模拟产品在不同设备上的行为方式](device-mode/index.md)
*   [检查、调整和更改元素的样式](./inspect-styles/edit-fonts.md)
*   [调试 JavaScript](./javascript/index.md)
*   [实时主机](console/index.md)
*   [辅助功能、性能、兼容性和安全问题](./issues/index.md)
*   [检查网络流量](./network/index.md)
*   [检查浏览器存储内容的位置](./storage/sessionstorage.md)
*   [评估性能](evaluate-performance/index.md)
*   [内存问题](memory-problems/index.md)
*   [呈现问题](./rendering-tools/index.md)
*   [使用开发环境](./sources/index.md)
*   [将 DevTools 中的更改与文件系统同步](./workspaces/index.md)
*   [从 Web 覆盖文件](./javascript/overrides.md)
