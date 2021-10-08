---
description: 如何将不同的颜色主题应用到 Microsoft Edge Tools。
title: 将颜色主题应用到 DevTools
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/03/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 27bdc38ba0ff426ece03023611cd16c6e1224e6c
ms.sourcegitcommit: 0eca205728eeca1bd54b3ca34dfc81ec57cf16d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2021
ms.locfileid: "12082398"
---
<!-- Copyright Kayce Basques
   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at
       https://www.apache.org/licenses/LICENSE-2.0
   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="apply-color-themes-to-devtools"></a>将颜色主题应用到 DevTools

你可以将各种颜色主题应用到 Microsoft Edge Tools，包括多个来自 Visual Studio Code 的主题，[例如][VSCode]Monokai 和大光深色。  主题影响窗格、按钮和代码语法突出显示的颜色。

:::image type="complex" source="./media/all-devtools-themes.png" alt-text="各种 DevTools 颜色主题" lightbox="./media/all-devtools-themes.png":::
   各种 DevTools 颜色主题
:::image-end:::

> [!NOTE]
> 在[93 Microsoft Edge][WhatsNew93]之前，DevTools 只有浅色和深色主题。

本文介绍更改 DevTools 的外观。  若要改为更改开发中网页的显示方式，请导航到在呈现的页面中模拟深色 [或浅色方案][AccessibilityPreferredColorSchemeSimulation]。


## <a name="available-themes"></a>可用主题

默认情况下，DevTools 主题设置为系统首选项 (**** 也称为**系统首选颜色主题**) 。  如果你的操作系统设置为浅色主题，DevTools 将使用 **浅色+** 主题。  如果你的操作系统设置为深色主题，DevTools 将使用 **深色+** 主题。  但是，你可以将 DevTools 更改为任何其他主题，以便当将操作系统设置为浅色或深色主题时，DevTools 不会受到影响。

浅色主题：
- 浅色+ (默认) 
- Chromium浅色
- 安静光
- 太阳光

深色主题：
- 深色+ (默认) 
- Abyss
- Chromium深色
- Kimbie Dark
- 单声道
- Monokai Dimmed
- 红色
- 浅色深
- 明天晚上蓝色

## <a name="changing-the-color-theme-from-settings"></a>更改颜色主题设置

1.  打开 DevTools，**然后选择设置 (** 齿轮图标) 。

    :::image type="complex" source="./media/setting-button.png" alt-text="The 设置 (gear) icon" lightbox="./media/setting-button.png":::
       The**设置 (** gear) icon
    :::image-end:::

1.  选择 **首选项**，然后在"外观 **"** 部分，从"主题"下拉列表 **中选择** 主题。

    :::image type="complex" source="./media/customize-theme-setting.png" alt-text="在首选项中选择主题" lightbox="./media/customize-theme-setting.png":::
       在首选项 **中选择主题**
    :::image-end:::


## <a name="changing-the-color-theme-from-the-command-menu"></a>从命令菜单更改颜色主题

若要使用命令菜单更改应用于 DevTools 的颜色主题：

1.  [打开“命令”菜单][DevtoolsCommandMenu]。
1.  键入单词"theme"。
1.  为 **你想要** 使用的主题选择一个"外观"命令。  例如 **，Appearance： Switch to Abyss theme** or **Appearance： Switch to Light+ (Default) theme**.
1.  选择 `Enter` 以运行命令。

    :::image type="complex" source="./media/customize-theme-command-menu.png" alt-text="命令菜单中的主题列表" lightbox="./media/customize-theme-command-menu.png":::
       命令菜单中的主题 **列表**
    :::image-end:::


<!-- ====================================================================== -->
<!-- links -->
[DevtoolsCommandMenu]: ../command-menu/index.md "命令菜单|Microsoft Docs"
[WhatsNew93]: ../whats-new/2021/07/devtools.md "DevTools (Microsoft Edge 93 中的新增) |Microsoft Docs"
[VSCode]: https://code.visualstudio.com
[AccessibilityPreferredColorSchemeSimulation]: ../accessibility/preferred-color-scheme-simulation.md "模拟呈现的页面布局中的深色或浅色|Microsoft Docs"

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/customize/dark-theme)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。
[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。
