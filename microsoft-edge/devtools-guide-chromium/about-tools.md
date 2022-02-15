---
title: 关于工具列表
description: 关于 DevTools 中的工具列表。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/02/2022
ms.openlocfilehash: 673db7a75c60c5eaad156edd27e9054a06b9c150
ms.sourcegitcommit: 2e0ec25e3cfc01b58fdddd5f4ac270632cb9b962
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2022
ms.locfileid: "12348312"
---
# <a name="about-the-list-of-tools"></a>关于工具列表

DevTools 提供 35 种工具：
*  两个工具栏图标，用于****![检查工具 (检查](media/inspect-tool-icon-light-theme.png)工具图标。**) 设备**![仿真 (设备仿真](media/device-emulation-icon-light-theme.png)图标。) 。
*  3 个永久工具栏选项卡，用于**元素****、控制台**和**源**工具。
*  30 个可选工具栏选项卡，用于可选工具。

![所有 DevTools 工具，包括 2 个工具栏图标、3 个永久工具栏选项卡和 30 个"更多工具"选项卡。](media/all-tools.png)

以下功能是访问工具的其他方式：
*  The **Drawer** is an additional toolbar and area to hold tool tabs.
*  命令 **菜单** 是直接使用工具功能的一种方法。
*  这些**设置**页面可以打开工具的其他功能。


<!-- ====================================================================== -->
## <a name="the-more-tools-menus"></a>"更多工具"菜单

" **更多工具** (**+**) 工具栏和"箱"工具栏上的"更多工具"菜单是动态的：它省略了该工具栏上打开的任何选项卡工具。

"**自定义和控制** **DevTools** ![](media/customize-devtools-icon-light-theme.png) (自定义"图标中的"更多工具"菜单。) 菜单是静态的：它始终列出所有可选工具。  如果所选工具是面板工具，则打开主工具栏;如果是"箱"工具，则打开在"箱"中。  可以右键单击工具的选项卡以将其移动到其他工具栏。


<!-- ====================================================================== -->
## <a name="panel-tools-vs-drawer-tools"></a>面板工具与箱式工具

在命令 **菜单中**：

* _面板工具_ 是默认在主工具栏中打开的工具。

* _"箱工具_ "是默认情况下在 DevTools 底部的"箱"工具栏中打开的工具。  按 `Esc` 显示或隐藏"箱"。

" **命令菜单** "首先列出面板工具，然后列出"箱"工具：

![命令菜单，显示组合在一起的面板工具，然后是"箱"工具。](media/command-menu-panel-vs-drawer-tools.png)

若要将工具移动到另一个工具栏，请右键单击该工具的选项卡，然后选择"移动到 **底部** "或" **移动到顶部"**。

若要打开命令**菜单**，请按 `Ctrl`++`Shift``P` (Windows/Linux) 或 (`P` `Command`+`Shift`+macOS) 。  或者，单击"自定义和控制 **DevTools** ![ (自定义"图标](media/customize-devtools-icon-light-theme.png) 。) 按钮，然后选择"运行 **命令"**。


<!-- ====================================================================== -->
## <a name="closing-tool-tabs"></a>关闭工具选项卡

若要关闭工具栏上的工具选项卡，

*  单击 **选项卡上的 x** 。

   无法**关闭"** 元素 **"**、****"控制台"和"源"工具选项卡。


一次关闭所有可选选项卡：

*  右键单击工具栏上的可选选项卡 (包含 **x** 按钮的选项卡) ，然后选择"全部 **关闭"**。

   只有**元素****、控制台****和源**保留在主工具栏上。   (" **箱"** 工具栏不受影响。) 

   如果关闭了"收银机"上 **的所有**选项卡，则只有" **控制台"选项卡** 仍保留在"收银 **机"** 工具栏上。   (主工具栏不受影响。) 


<!-- ====================================================================== -->
## <a name="restoring-the-default-tool-tabs"></a>还原默认工具选项卡

还原主工具栏上的所有默认选项卡：

1. 在 DevTools 中，**设置** (设置![图标](media/settings-gear-icon-light-theme.png)。) >**首选项"**。

1. 单击" **还原默认值并刷新"** 按钮。

   主工具栏再次包含所有默认选项卡。  然后 **，"** 箱"仅具有 **"控制台"** 选项卡。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅
 
* [DevTools](index.md) 概述 - 与当前文章类似，但范围更广，主要介绍了 DevTools。
* [实验功能](experimental-features/index.md#focus-mode)中 _的焦点模式_。  在**焦点模式下**，**活动**栏是主工具栏的精简替换，而快速视图列表是****"箱"工具栏上的选项卡的替换。
