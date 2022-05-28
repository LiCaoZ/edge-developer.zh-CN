---
title: 使用搜索工具查找页面的源文件
description: Microsoft Edge DevTools 中的搜索工具有助于查找源文件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/28/2021
ms.openlocfilehash: 8fd9a0f69a9f6675ab5ea9805f8e72fbc0635fdf
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12553279"
---
# <a name="find-source-files-for-a-page-using-the-search-tool"></a>使用搜索工具查找页面的源文件

使用 **搜索** 工具查找网页的特定源文件，包括 HTML、CSS、JavaScript 和映像文件。

网页主要是浏览器用来显示内容的 HTML 文件。  但是，除了 HTML 文件（如 CSS、JavaScript 或图像文件）之外，网页通常还需要其他资源来提供更丰富的内容。

在 **“源**”工具中，“[导航器”窗格](../sources/index.md#using-the-navigator-pane-to-select-files)的 **“页面**”选项卡显示网页下载的所有资源。  但是，当有许多资源时， _搜索_ 这些资源会很有用。  若要跨网页的所有资源执行文本和正则表达式搜索，请使用 **搜索** 工具。


<!-- ====================================================================== -->
## <a name="open-the-search-tool-by-using-a-keyboard-shortcut"></a>使用键盘快捷方式打开搜索工具

若要快速打开 **搜索** 工具，请执行以下操作：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 中，按 `Esc` 下以打开抽屉，然后在抽屉工具栏上选择 **“搜索** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

   或者，按“`Ctrl`+`Shift`+`F`”(Windows、Linux)或“`Command`+`Option`+`F`”(macOS)。

**搜索**工具显示在**抽屉**中，其中包含搜索工具栏：

:::image type="content" source="../media/search-tool/search-tool-first-open-reduced.png" alt-text="带有搜索工具栏的搜索工具。" lightbox="../media/search-tool/search-tool-first-open.png":::

另请参阅 [全局键盘快捷方式](../shortcuts/index.md#global-keyboard-shortcuts)。


<!-- ====================================================================== -->
## <a name="open-the-search-tool-by-using-the-command-menu"></a>使用命令菜单打开搜索工具

从**命令菜单**打开**搜索**工具：

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 按++`Ctrl``P``Shift` (Windows、Linux) 或`Command``P`++`Shift` (macOS) 打开[命令菜单](../command-menu/index.md)。

1. 键 `search`入，然后按 `Enter`。

![“命令”菜单，其中选择了“显示搜索”项。](../media/search-tool/open-search-tool.png)


<!-- ====================================================================== -->
## <a name="search-for-text"></a>搜索文本

若要在当前网页及其资源文件中搜索文本，请执行以下操作：

1. 将焦点放在搜索输入字段中。
1. 输入要搜索的文本，然后按 `Enter`下。

**搜索**工具显示匹配资源的列表，并突出显示相应的文本行。  匹配文件和行的数量也指示在工具的底部。

![搜索工具中显示的搜索结果，匹配文本以黄色突出显示。](../media/search-tool/search-tool-search-results.png)

<!-- The search results are pretty-printed. -->


<!-- ====================================================================== -->
## <a name="match-case-lowercase-or-uppercase-characters"></a>匹配大小写 (小写或大写字符) 

默认情况下， **搜索** 工具不区分大小写。  无论小写或大写字符如何，对术语的搜索都与该术语的匹配。

若要仅查找与特定事例匹配的结果 (小写或大写字符) ，请单击搜索工具栏中的 **“匹配案例** (`Aa`) ”按钮。


<!-- ====================================================================== -->
## <a name="search-for-regular-expressions"></a>搜索正则表达式

可以使用正则表达式（包括 [JavaScript 正则表达式）](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions)来查找匹配的结果。  若要使用正则表达式，请单击工具栏中的“ **使用正则表达式** (`.*`) 按钮，并在搜索输入字段中输入有效的正则表达式。

![搜索正则表达式。](../media/search-tool/search-tool-regexp.png)


<!-- ====================================================================== -->
## <a name="open-a-found-file-in-the-sources-tool"></a>在“源”工具中打开找到的文件

执行搜索后，单击结果行以打开相应的文件。  **源**工具在主面板中打开，并加载资源文件，并滚动到匹配的行。

![单击搜索行将打开“源”工具并加载相应的资源。](../media/search-tool/search-tool-open-in-sources.png)


<!-- ====================================================================== -->
## <a name="update-search-results"></a>更新搜索结果

网页在完成加载后可以继续请求资源，因此 **搜索面板中** 显示的结果可能会在一段时间后过时。

若要更新搜索结果，请执行以下任一操作：
*  通过在搜索输入字段中键入术语再次搜索。
*  单击 **“刷新** (![”搜索按钮。](../media/search-tool/search-tool-refresh.png)) 工具栏中的按钮。


<!-- ====================================================================== -->
## <a name="clear-a-search"></a>清除搜索

若要清除搜索结果，请单击 **“清除** (![”搜索按钮。](../media/search-tool/search-tool-clear.png)) 工具栏中的按钮。
