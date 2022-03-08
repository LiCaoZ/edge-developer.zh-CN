---
title: 使用更改工具跟踪对文件的更改
description: The Changes tool tracks any changes you've made to CSS or JavaScript in Microsoft Edge DevTools.  它显示成功使用 DevTools 修改从服务器发送的网页文件后，对实际源文件进行哪些更改。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/28/2021
ms.openlocfilehash: 22684ee18ef1ba5129514eb09ce34f8650d02c93
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431338"
---
# <a name="track-changes-to-files-using-the-changes-tool"></a>使用更改工具跟踪对文件的更改

The **Changes tool** tracks any changes you've made to CSS or JavaScript in DevTools.  它显示成功使用 DevTools 修改从服务器发送的网页文件后，对实际源文件进行哪些更改。

使用 **"更改** "工具可快速显示所有更改，以便将这些更改重新应用到集成开发环境中编辑器 (源文件;IDE) 。

:::image type="content" source="../media/changes-tool/changes-tool-open-reduced.msft.png" alt-text="&quot;更改&quot;工具在箱中打开的开发人员工具显示三个已修改的文件和所选文件的修改。" lightbox="../media/changes-tool/changes-tool-open.msft.png":::

在 DevTools 中，使用以下任一方法打开 **"更改"** 工具。  The **Changes tool** is a **Drawer** tool;默认情况下，它将在"箱 **"中打开**。


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-right-clicking-in-a-changed-file"></a>右键单击已更改的文件，打开"更改"工具

在" [源](../sources/index.md) "工具中，右键单击任何显示已更改的文件，然后选择" **本地修改"**：

:::image type="content" source="../media/changes-tool/changes-tool-from-sources-reduced.msft.png" alt-text="若要打开&quot;更改&quot;工具，请在&quot;源&quot;工具中右键单击修改后的文件，然后选择&quot;本地修改&quot;命令。" lightbox="../media/changes-tool/changes-tool-from-sources.msft.png":::


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-clicking-the-more-tools-icon"></a>通过单击"更多工具"图标打开"更改"工具

在主工具栏**或"箱**"工具栏**** `+` 上，单击"更多工具" () 图标，然后选择"更改 **"**：

:::image type="content" source="../media/changes-tool/changes-tool-via-plus-menu-reduced.msft.png" alt-text="&quot;更多工具 (+) 主工具栏中的图标和菜单，同时选择&quot;更改&quot;工具。" lightbox="../media/changes-tool/changes-tool-via-plus-menu.msft.png":::

The **Changes** tool appears in the main toolbar or in the **Drawer**， depending on which toolbar you used.


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-clicking-the-customize-devtools-icon"></a>通过单击"自定义 DevTools"图标打开"更改"工具

单击 **"自定义和控制 DevTools** `...` () "，指向"更多 **工具**"，然后选择"更改 **"**：

:::image type="content" source="../media/changes-tool/changes-tool-via-overflow-menu-reduced.msft.png" alt-text="单击&quot;自定义和控制 DevTools&quot; (...) ，指向&quot;更多工具&quot;，然后选择&quot;更改&quot;。" lightbox="../media/changes-tool/changes-tool-via-overflow-menu.msft.png":::


<!-- ====================================================================== -->
## <a name="open-the-changes-tool-by-using-the-command-menu"></a>使用命令菜单打开"更改"工具

按"[命令菜单"](../command-menu/index.md)，`Ctrl`+`P`+`Shift`Windows/Linux `Command``Shift`++`P` 或 Mac，然后键入**更改**。  突出显示 **"显示更改** "命令;按 `Enter`。

:::image type="content" source="../media/changes-tool/changes-tool-command-menu-reduced.msft.png" alt-text="在命令菜单中，开始键入&quot;更改&quot;，然后选择&quot;显示更改&quot;命令。" lightbox="../media/changes-tool/changes-tool-command-menu.msft.png":::


<!-- ====================================================================== -->
## <a name="interpret-added-lines-removed-lines-and-differences-in-a-line"></a>解释添加的行、删除的行和行的差异

每个修改后的文件都列在侧窗格中。  选择文件将修改作为视图 `diff` 显示。  对于上下文，你将看不到整个文件，但只会看到已更改的行以及更改行上方和下方的几行。

:::image type="content" source="../media/changes-tool/changes-tool-diff-view-reduced.msft.png" alt-text="文件的不同视图，显示文件的不同部分有两处修改。  一个更改是删除和插入，一个更改是已删除行。" lightbox="../media/changes-tool/changes-tool-diff-view.msft.png":::

| 更改类型 | 指示器 |
|---|--|
| 删除的行 | 从代码中删除的每一行前面都有 `-` ，并且颜色为红色。 |
| 添加了行 | 每一条新线条 `+` 的前面都有 一个 ，并且颜色为绿色。 |
| 更改的行 | 相邻的一对线条，后 `-` 接一 `+` 条线。 |

更改表示为在两列行号中插入或删除各个代码行。  左列表示旧文件的行号，右列表示新文件的行号。


<!-- ====================================================================== -->
## <a name="open-a-changed-file-in-the-sources-tool"></a>在"源"工具中打开已更改的文件

单击"更改"工具中的修改**** 行将在"源"工具中[](../sources/index.md)打开文件，滚动到修改的行。


<!-- ====================================================================== -->
## <a name="undo-all-changes"></a>撤消所有更改

若要撤消所有更改，请单击 `Revert all changes to the current file` 显示为圆形箭头的按钮。

:::image type="content" source="../media/changes-tool/changes-tool-undo-all-reduced.msft.png" alt-text="若要撤消对当前文件进行的所有更改，请单击按钮&quot;将所有更改还原到当前文件&quot;。" lightbox="../media/changes-tool/changes-tool-undo-all.msft.png":::


<!-- ====================================================================== -->
## <a name="horizontally-scroll-entries"></a>水平滚动条目

对缩小文件进行更改后，"更改"工具允许您水平滚动**** 以显示所有缩小代码。  若要水平滚动，请单击水平滚动条或按箭头键。

:::image type="content" source="../media/changes-tool/changes-reduced.msft.png" alt-text="若要在&quot;更改&quot;工具中显示长行代码，请按箭头键。" lightbox="../media/changes-tool/changes.msft.png":::
