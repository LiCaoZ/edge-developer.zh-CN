---
description: 呈现模拟用户的深色或浅色方案操作系统设置或浏览器设置的网页，而无需更改你自己的计算机设置。  将 CSS 媒体查询与 DevTools 呈现选项一起用于 prefers-color-scheme。
title: 模拟呈现页面中的深色或浅色方案
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/03/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: a4a32215cd45aedc7f9b7261fa3a441f269939ba
ms.sourcegitcommit: 01ed086305c06b4e3a0436586524986700276148
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "11893003"
---
# <a name="emulate-dark-or-light-schemes-in-the-rendered-page"></a>模拟呈现页面中的深色或浅色方案

许多操作系统都有一种方法来以较暗或更浅的颜色显示任何应用程序。  在深色操作系统中具有浅色方案的网页产品可能难以阅读，并且对于一些用户可能是一个辅助功能问题。  

若要测试当用户选择深色或浅色模式时网页的呈现方式，而不是更改你自己的计算机深色模式或浅色模式设置，可以在 Microsoft Edge DevTools 中选择模拟**CSS 首选**配色方案：深色或**** 浅色。  可以从命令菜单或呈现工具**** 执行此操作，如下所述****。

或者，也可以使网页根据计算机上自己的首选设置自动选择深色或浅色模式，选择"无 **模拟**"，这是默认设置。

若要指定用于浅色和深色方案 CSS，请使用首选配色 [方案][MDNPrefersColorScheme] CSS 媒体查询来检测用户是否希望以深色或浅色配色方案显示产品，然后自动选择您自己的自定义浅色或深色模式 CSS。  示例 CSS 代码显示在检查深色主题和浅色 [主题的对比度问题中](test-dark-mode.md)。

本文介绍更改开发中网页的外观。  若要改为更改 DevTools 的显示方式，请导航到 [将颜色主题应用到 DevTools][DevtoolsCustomizeTheme]。


## <a name="emulating-dark-or-light-mode-using-the-rendering-tool"></a>使用呈现工具模拟深色或浅色模式

1.  在 DevTools 中，打开 **呈现** 工具。  为此，您可能需要选择主工具栏上的"更多工具****" (+) 图标，然后选择"呈现 **"。**

1.  在模拟 **CSS 媒体功能 prefers-color-scheme** 下拉列表中，选择 **prefers-color-scheme： dark** or **prefers-color-scheme： light**。

    :::image type="complex" source="../media/css-elements-styles-qs-simulated-light-mode.msft.png" alt-text="使用呈现工具模拟深色或浅色模式" lightbox="../media/css-elements-styles-qs-simulated-light-mode.msft.png":::
       使用呈现工具模拟深色或 **浅色** 模式
    :::image-end:::  

1.  刷新页面以显示呈现的结果。

    现在，您可以修改 CSS，并像查看任何其他网页一样查看呈现的结果。  有关详细信息，请导航到开始[查看和更改 CSS。][DevtoolsCssIndex]  

1.  若要还原该设置，请在"**** 呈现"工具中的"**模拟 CSS 媒体功能首选-** 配色方案"下拉列表中，选择"无**模拟"。**  刷新页面时，将应用你自己的用于浅色或深色模式首选项的操作系统或浏览器设置。


## <a name="emulating-dark-or-light-mode-using-the-command-menu"></a>使用命令菜单模拟深色或浅色模式

1.  当 DevTools 具有焦点时****，通过选择 `Ctrl` + `Shift` + `P` \ (Windows/Linux\) 或 `Command` + `Shift` + `P` \ (macOS\) 打开命令菜单。  

1.  键入"dark"、"light"或"emulate"。  然后选择呈现 **：模拟 CSS 首选配色方案：深色** 或呈现 **：模拟 CSS 首选配色方案：浅**色，然后选择 **Enter**。

    :::image type="complex" source="../media/css-console-command-menu-rendering.msft.png" alt-text="使用命令菜单上的"呈现：模拟 CSS prefers-color-scheme"命令模拟深色或浅色模式" lightbox="../media/css-console-command-menu-rendering.msft.png":::
        使用呈现模拟深色或浅色 **模式：模拟命令** 菜单上的 CSS 首选配色方案命令
    :::image-end:::  

    选择" **呈现"** 命令而不是 **"外观"** 命令。  " **呈现** "命令会影响开发中呈现的网页。  Appearance **** 命令会改为影响窗口的 DevTools 部分。

1.  刷新页面以显示呈现的结果。
   
    现在，您可以修改 CSS，并像查看任何其他网页一样查看呈现的结果。  有关详细信息，请导航到开始[查看和更改 CSS。][DevtoolsCssIndex]  

1.  若要还原该设置，请在"命令菜单"中键入"模拟"或"方案"，然后选择"呈现 **：不模拟 CSS 首选颜色方案"。**  刷新页面时，将应用你自己的用于浅色或深色模式首选项的操作系统或浏览器设置。


<!-- links -->  
[DevtoolsIndex]: ../index.md "Microsoft Edge (Chromium) 开发人员工具 | Microsoft Docs"  
[DevtoolsCustomizeTheme]: ../customize/theme.md "将颜色主题应用到 DevTools |Microsoft Docs"
[DevtoolsCssIndex]: ../css/index.md "开始查看和更改 CSS |Microsoft Docs"  
<!-- external links -->
[MDNPrefersColorScheme]: https://developer.mozilla.org/docs/Web/CSS/@media/prefers-color-scheme "prefers-color-scheme |MDN"  
