---
title: 使用焦点模式简化 DevTools
description: 了解如何使用新的焦点模式实验用户界面来降低 DevTools 的复杂性，使其更紧凑，并且更易于打开和关闭工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/28/2022
ms.openlocfilehash: ca1ff4dbe515053b39c7a944d42470c4958afa30
ms.sourcegitcommit: d753bc98ca50acdcdb7a8bf911af3465d3228058
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2022
ms.locfileid: "12465210"
---
# <a name="simplify-devtools-using-focus-mode"></a>使用焦点模式简化 DevTools

焦点模式是 DevTools 的新用户界面。 它旨在减少 DevTools 的混乱和复杂性，而不会损害其功能集。

焦点模式将选项卡的主行替换为活动 **栏**，即具有独特图标的紧凑工具栏。 利用 **活动栏** ，可以固定、重新排列和打开常用工具以便快速访问。 它还允许访问用户设置、帮助和其他功能。

焦点模式还提供了快速 **视图** 列表，以在活动栏中已选择的工具旁边打开第 **二个工具**。

![使用焦点模式实验在其自己的窗口中取消停靠的 DevTools 的屏幕截图](media/focus-mode.png)


<!-- ====================================================================== -->
## <a name="enable-focus-mode"></a>启用焦点模式

团队Microsoft Edge为部分用户启用专注模式以收集早期反馈。 默认情况下，某些用户将启用焦点模式，而其他用户需要先启用它。

若要检查是否已启用焦点模式，或者启用或禁用它：

1. 按`F1`以打开**设置**。

1. 单击 **实验** 并向下滚动到焦点 **模式** 复选框。

   如果选中此复选框，则焦点模式已启用。 选择或清除它以启用或禁用焦点模式。

    ![DevTools 中"设置"页面的屏幕截图，显示"实验"选项卡，向下滚动到"焦点模式"复选框](media/focus-mode-pref.png)

1. 关闭**设置页**。 如果更改了焦点模式实验状态，请单击 **"重新加载 DevTools** "按钮，更改将生效。


<!-- ====================================================================== -->
## <a name="main-differences-from-the-default-user-interface"></a>与默认用户界面的主要区别

下面是 DevTools 默认用户界面和焦点模式之间的主要区别。

### <a name="activity-bar"></a>活动栏

活动 **栏** 是默认用户界面最明显的区别。 使用它打开工具、帮助功能和设置。

默认情况下，活动栏 **的位置根据** DevTools 窗口的位置进行调整。 如果 DevTools 已取消停靠或固定到浏览器底部，活动 **栏** 将是水平活动的。 如果 DevTools 固定到浏览器的一侧，活动栏将为垂直**** 方向，并且工具名称将不可见。 这样，当屏幕宽度受限时，可以更快地访问工具。

具有顶部对齐的活动栏在 **** DevTools 停靠的焦点模式。

![焦点模式顶部对齐的活动栏（已停靠 DevTools）的屏幕截图](media/focus-mode-docked.png)

DevTools 弹出窗口中**** 具有顶部对齐活动栏的焦点模式。

![焦点模式顶部对齐的活动栏与 DevTools 弹出窗口的屏幕截图](media/focus-mode-undocked.png)

### <a name="warning-and-error-indicators"></a>警告和错误指示器

在默认的 DevTools 用户界面中，主工具栏中将显示一个计数器，其中显示诸如"问题"建议**** 和"控制台警告"**的消息**数。 当生成许多消息时，计数器可能会变大，占用 DevTools 中宝贵的空间。

![默认 DevTools 工具栏"问题"和"控制台消息指示器"](media/devtools-toolbar-message-indicator.png)

在焦点模式下，此计数器已删除。 相反，小型指示器会 **覆盖** 问题和 **控制台** ，以显示消息是否已由各自的工具报告。

![问题和控制台中的焦点模式消息覆盖](media/focus-mode-message-indicator.png)

### <a name="quick-view"></a>快速视图

  " **快速视图** "列表包含可在活动栏中选择的一个工具旁边 **显示的所有工具**。

  **快速视图** 从默认用户界面替换箱工具栏。

  ![焦点模式下快速视图列表的屏幕截图，在底部窗格中选择并打开工具](media/focus-mode-quick-view.png)

### <a name="devtools-customization-and-settings"></a>DevTools 自定义和设置

  多个自定义功能和 DevTools 设置现在组合在一起，在活动栏中的自定义和控制 **DevTools** (**...**) 按钮提供的单个 **菜单下**。 这些功能和设置显示在默认用户界面中的多个位置。

  * **扩展坞** 位置允许你更改 DevTools 在浏览器窗口中的位置。
  * **活动栏位置**允许你更改活动栏在 DevTools 中的位置。****
  * **主题** 允许你更改颜色主题。
  * **设置**提供对 DevTools 设置的访问权限。
  * **键盘快捷方式** 允许你查看和更改键盘快捷方式。

  ![焦点模式下菜单的屏幕截图](media/focus-mode-menu.png)

### <a name="help-links"></a>帮助链接

  " **帮助** "菜单包含指向 DevTools 文档和发行说明的链接，以及一个向团队发送反馈的按钮。 这些链接和按钮之前嵌套在默认用户界面中的 **"自定义和控制 DevToolsHelp** > "下。****

  ![焦点模式下帮助菜单的屏幕截图](media/focus-mode-help.png)


<!-- ====================================================================== -->
## <a name="open-tools-from-the-activity-bar"></a>从活动栏中打开工具

默认情况下，活动 **栏** 包含以下模式和工具：

*  **检查** 模式 (![检查工具图标。](../media/inspect-tool-icon-light-theme.png)) 切换按钮。

*  **设备仿真模式** (!["设备仿真"图标](../media/device-emulation-icon-light-theme.png) 。) 按钮。

*  **欢迎** 工具 (![欢迎工具图标](media/focus-mode-welcome.png) 。) 。

*  **元素** 工具 (![元素工具图标。](media/focus-mode-elements.png)) 。

*  **控制台** 工具 (![控制台工具图标。](media/focus-mode-console.png)) 。

*  **源** 工具 (![源工具图标。](media/focus-mode-sources.png)) 。

*  **网络** 工具 (![网络工具图标。](media/focus-mode-network.png)) 。

*  **问题** 工具 (![问题工具图标。](media/focus-mode-issues.png)) 。

*  **性能** 工具 (![性能工具图标。](media/focus-mode-performance.png)) 。

*  **内存** 工具 (![内存工具图标。](media/focus-mode-memory.png)) 。

*  **应用程序** 工具 (![应用程序工具图标。](media/focus-mode-application.png)) 。


<!-- ====================================================================== -->
## <a name="pin-and-rearrange-tools-in-the-activity-bar"></a>固定和重新排列活动栏中的工具

通过固定或取消固定工具，可以选择**** 在活动栏中显示的工具。 这允许你自定义首选工作流的 DevTools。

![焦点模式下"更多工具"菜单的屏幕截图](media/focus-mode-more-tools.png)

单击 **"更多 (** **+**) "以列出所有可用的工具。 选择工具会将其固定到 **活动栏**。 默认情况下，每次打开 DevTools 时都会显示它。

如果活动栏中的空间不足，无法显示所有**** 固定的工具，某些工具可能会溢出到"更多**工具"** 菜单中。

![当窗口较短时，焦点模式下的更多工具菜单的屏幕截图，导致某些图标显示在菜单而不是活动栏中](media/focus-mode-overflow-tools.png)

若要从活动栏中取消固定工具 **，** 请右键单击该工具，然后选择" **从活动栏中删除"**。

![从活动栏中取消固定工具的上下文菜单屏幕截图](media/focus-mode-remove-tool.png)

目前，无法从活动栏取消固定 **以下工具**：

* **元素** 工具
* **控制台** 工具
* **源** 工具


<!-- ====================================================================== -->
## <a name="open-tools-from-quick-view"></a>从快速视图打开工具

使用 **"快速视图"** 列表打开活动栏中已选定的工具旁边的另一 **个工具**。

1. 从活动栏中 **选择工具**。

1. 单击 **"快速视图"** 列表，然后从列表中选择其他工具。

以下屏幕截图并 **排显示了网络** 工具和 **控制台** 工具。

![位于顶部的网络工具以及底部的控制台工具的焦点模式的屏幕截图](media/focus-mode-quick-view-tool.png)

可以通过单击折叠快速**视图****** / **Expand 快速**视图或按 Escape 键来隐藏或展开**快速**视图。 ![ (快速视图 V 形切换图标) ](media/focus-mode-chevron.png)。


<!-- ====================================================================== -->
## <a name="customize-focus-mode"></a>自定义焦点模式

活动 **栏** 可以垂直或水平方向，以最大化各种 DevTools 窗口位置中的可用屏幕空间。

若要更改活动栏的位置，**** 请单击"自定义和控制 **DevTools**"，**然后单击"活动**栏位置"，然后选择其中一个位置。

![焦点模式下"活动栏位置"菜单的屏幕截图](media/focus-mode-activity-bar-location.png)

* **适应默认 (** 位置) ：活动栏将采用水平或垂直方向，**** 具体取决于 DevTools 的停靠位置。

  * 如果 DevTools 固定在浏览器窗口的左侧或右侧，活动 **栏** 将为垂直。

  * 如果 DevTools 固定到浏览器窗口的底部，或在其自己的窗口中取消停靠，活动 **栏将是水平** 活动的。

* **Top**： **活动栏** 将始终为水平。

* **左侧**： **活动栏** 将始终为垂直。

当 **活动栏是** 水平显示的时，如果有足够的空间来显示工具图标，工具名称将显示在工具图标旁边。

以下屏幕截图显示了在其自己的窗口中取消停靠的 DevTools，水平活动栏显示一**** 些选项卡（包含工具图标和名称）和一些选项卡仅包含图标。

![具有水平活动栏的焦点模式的屏幕截图](media/focus-mode-horizontal.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [DevTools：](https://github.com/MicrosoftEdge/DevTools/blob/main/explainers/FocusMode/explainer.md)焦点模式 UI 是此实验性功能的初始解释器，位于 Microsoft Edge Tools 存储库。
