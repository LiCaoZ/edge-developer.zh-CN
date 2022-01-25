---
title: 搜索面板
description: DevTools Microsoft Edge中的搜索工具可帮助查找源文件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/28/2021
ms.openlocfilehash: c12bdace3d8f14cff109cd3b4183b8a396f2f3cb
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12317804"
---
# <a name="the-search-panel"></a>搜索面板

使用 **搜索** 工具查找网页的特定源文件。

网页主要是浏览器用来显示内容的 HTML 文件。  但网页通常需要 HTML 文件（如 CSS、JavaScript 或图像文件）之外的其他资源，以提供更丰富的内容。

在 **"源**"**工具中，** 导航器窗格[](../sources/index.md#using-the-navigator-pane-to-select-files)的"页面"选项卡显示网页下载的所有资源。  但是，当有许多资源时，在资源中 _搜索可能会_ 很有用。  若要在网页的所有资源中执行文本和正则表达式搜索，请使用 **搜索** 工具。


<!-- ====================================================================== -->
## <a name="open-the-search-tool-by-using-a-keyboard-shortcut"></a>使用键盘快捷方式打开搜索工具

若要快速打开 **搜索工具** ，请执行以下操作：

1.  [打开 DevTools](../open/index.md) (`F12`) 。

1.  按 `Control` + `Shift` + `F` (Windows/Linux) 或 `Command` + `Option` + `F` (macOS) 。

The **Search** tool appears in the **Drawer**， and shows the search toolbar：

:::image type="content" source="../media/search-tool/search-tool-first-open-reduced.png" alt-text="搜索工具，包含搜索工具栏。" lightbox="../media/search-tool/search-tool-first-open.png":::

另请参阅 [全局键盘快捷方式](../shortcuts/index.md#global-keyboard-shortcuts)。


<!-- ====================================================================== -->
## <a name="open-the-search-tool-by-using-the-command-menu"></a>使用命令菜单打开搜索工具

若要从 **命令菜单** 打开搜索 **工具**：

1.  [打开 DevTools](../open/index.md) (`F12`) 。

1.  打开命令[菜单](../command-menu/index.md)，按 `Control` + `Shift` + `P` (Windows/Linux) 或 (`Command` + `Shift` + `P` macOS) 。

1.  键入 `search` ，然后按 `Enter` 。

:::image type="content" source="../media/search-tool/open-search-tool.png" alt-text="选择了&quot;显示搜索&quot;项的命令菜单。":::


<!-- ====================================================================== -->
## <a name="search-for-text"></a>搜索文本

若要搜索当前网页中的文本及其资源文件，

1. 焦点搜索输入字段。
1. 键入要搜索的文本。
1. 按 `Enter` 。

搜索 **工具** 显示匹配资源的列表，并突出显示相应的文本行。  匹配文件和行的数量也指示在工具底部。

:::image type="content" source="../media/search-tool/search-tool-search-results.png" alt-text="搜索结果显示在搜索工具中，匹配文本以黄色突出显示。":::

<!-- The search results are pretty-printed. -->


<!-- ====================================================================== -->
## <a name="match-case-lowercase-or-uppercase-characters"></a>匹配大小写 (小写或大写) 

默认情况下， **搜索** 工具不区分大小写。  搜索词匹配该词的出现次数，无论小写还是大写字符。

若要仅查找与特定大小写匹配的结果 (小写或大写) ，请单击搜索工具栏中的"区分大小写****" () " `Aa` 按钮。


<!-- ====================================================================== -->
## <a name="search-for-regular-expressions"></a>搜索正则表达式

可以使用正则表达式（包括 [JavaScript 正则表达式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)）查找匹配结果。  若要使用正则表达式，请单击工具栏中的"**** 使用正则表达式 () "按钮，在搜索输入字段中输入有效的 `.*` 正则表达式。

:::image type="content" source="../media/search-tool/search-tool-regexp.png" alt-text="搜索正则表达式。":::


<!-- ====================================================================== -->
## <a name="open-a-found-file-in-the-sources-tool"></a>在"源"工具中打开找到的文件

执行搜索后，单击结果行以打开相应的文件。  源 **工具** 在主面板中打开并加载资源文件，滚动到匹配行。

:::image type="content" source="../media/search-tool/search-tool-open-in-sources.png" alt-text="单击搜索行将打开&quot;源&quot;工具并加载相应的资源。" lightbox="../media/search-tool/search-tool-open-in-sources.png":::


<!-- ====================================================================== -->
## <a name="update-search-results"></a>更新搜索结果

网页加载完成后可以继续请求资源，因此"搜索"面板中显示的结果可能在一段时间之后**** 过期。

若要更新搜索结果，请执行下列任一操作：
*  再次搜索，在搜索输入字段中键入术语。
*  单击工具栏 **中的"** 刷新 ![ (刷新搜索 ](../media/search-tool/search-tool-refresh.png)) 按钮。


<!-- ====================================================================== -->
## <a name="clear-a-search"></a>清除搜索

若要清除搜索结果，请单击工具栏 **中的"清除** (![ 清除 ](../media/search-tool/search-tool-clear.png)) "按钮。
