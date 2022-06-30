---
title: 使用更改工具跟踪对文件的更改
description: “更改”工具跟踪你对 Microsoft Edge DevTools 中的 CSS 或 JavaScript 所做的任何更改。  它显示成功使用 DevTools 修改从服务器发送的网页文件后对实际源文件所做的更改。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/28/2021
ms.openlocfilehash: fe171eca981ef6806b18471fc02bb78be17dcb81
ms.sourcegitcommit: b140f9beedaed9763d40de34234274b342894b76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2022
ms.locfileid: "12632715"
---
# <a name="track-changes-to-files-using-the-changes-tool"></a>使用更改工具跟踪对文件的更改

**“更改”工具**跟踪你在 DevTools 中对 CSS 或 JavaScript 所做的任何更改。  它显示成功使用 DevTools 修改从服务器发送的网页文件后对实际源文件所做的更改。

使用 **“更改** ”工具快速显示所有更改，以便将这些更改重新应用到集成开发环境中的编辑器 (中的实际源文件;IDE) 。

![显示已修改的三个文件以及所选文件的修改的“更改”工具](changes-tool-images/changes-tool-open.png)

在 DevTools 中，使用以下任一方法打开 **“更改** ”工具。  **更改工具**是**抽屉**工具;默认情况下，它将在**抽屉**中打开。


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-right-clicking-in-a-changed-file"></a>通过右键单击已更改的文件打开“更改”工具

在 [“源](../sources/index.md) ”工具中，右键单击任何显示已更改的文件，然后选择 **“本地修改**”：

![右键单击修改后的文件，然后选择“本地修改”命令](changes-tool-images/changes-tool-from-sources.png)


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-clicking-the-more-tools-icon"></a>单击“更多工具”图标打开“更改”工具

在主工具栏或 **抽屉** 工具栏上，单击“ **更多工具** ” () `+` 图标，然后选择 **“更改**”：

![主工具栏中的“更多工具” (+) 图标和菜单，其中选择了“更改”工具](changes-tool-images/changes-tool-via-plus-menu.png)

**更改**工具显示在主工具栏或**抽屉**中，具体取决于使用的工具栏。


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-clicking-the-customize-devtools-icon"></a>单击“自定义 DevTools”图标打开“更改”工具

单击 **“自定义并控制 DevTools** ” (`...`) ，指向 **“更多”工具**，然后选择 **“更改**”：

![单击“自定义并控制 DevTools”按钮打开“更多工具”菜单](changes-tool-images/changes-tool-via-overflow-menu.png)


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-using-the-command-menu"></a>使用命令菜单打开“更改”工具

在 Windows/Linux 或 `Command``P`++`Shift`Mac 上按下+`P`+`Ctrl``Shift`命令[菜单](../command-menu/index.md)，然后键入**更改**。  突出显示了 **“显示更改**”命令;按 。`Enter`

![在命令菜单中，开始键入“更改”，然后选择“显示更改”命令](changes-tool-images/changes-tool-command-menu.png)


<!-- ====================================================================== -->
## <a name="interpret-added-lines-removed-lines-and-differences-in-a-line"></a>解释添加的行、删除的行以及行中的差异

侧窗格中列出了每个已修改的文件。  选择文件将修改显示为 `diff` 视图。  对于上下文，不会看到整个文件，但只会看到已更改的行，以及更改的行上方和下方的几行。

文件的差异视图显示文件的不同部分有两个修改。  一个更改是删除和插入，一个更改是已删除的行。

![差异视图](changes-tool-images/changes-tool-diff-view.png)

| 更改类型 | 指标 |
|---|--|
| 删除的行 | 从代码中删除的每一行前面都有一个 `-` 颜色为红色。 |
| 添加的行 | 每条新线前面都有一个 `+` ，颜色为绿色。 |
| 已更改的行 | 相邻的一对线，带有一 `-` 条线，然后是一 `+` 条线。 |

更改表示为在行号的两列中插入或删除单行代码。  左列表示旧文件中的行号，右列表示新文件中的行号。


<!-- ====================================================================== -->
## <a name="open-a-changed-file-in-the-sources-tool"></a>在“源”工具中打开已更改的文件

单击 **“更改** ”工具中的修改行会打开 [“源](../sources/index.md) ”工具中的文件，并滚动到修改后的行。


<!-- ====================================================================== -->
## <a name="undo-all-changes"></a>撤消所有更改

若要撤消所有更改，请单击 `Revert all changes to the current file` 按钮，显示为圆形箭头。

![还原更改](changes-tool-images/changes-tool-undo-all.png)


<!-- ====================================================================== -->
## <a name="horizontally-scroll-entries"></a>水平滚动条目

对已缩小的文件进行更改后，“ **更改”工具** 允许你水平滚动以显示所有已缩小的代码。  若要水平滚动，请单击水平滚动条或按箭头键。

![显示一长串代码](changes-tool-images/changes.png)
