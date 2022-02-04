---
title: 将颜色主题应用于开发工具
description: 如何将不同的颜色主题应用于 Microsoft Edge DevTools。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/03/2021
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
# <a name="apply-a-color-theme-to-devtools"></a>将颜色主题应用于开发工具

你可以将各种颜色主题应用到 Microsoft Edge Tools，包括多个来自 Visual Studio Code 的主题，[例如](https://code.visualstudio.com) Monokai 和大光深色。  主题影响窗格、按钮和代码语法突出显示的颜色。

:::image type="content" source="./media/all-devtools-themes.png" alt-text="各种 DevTools 颜色主题。" lightbox="./media/all-devtools-themes.png":::

本文介绍更改 DevTools 的外观。  若要改为更改开发中网页的显示方式，请参阅模拟呈现页面中的深色 [或浅色方案](../accessibility/preferred-color-scheme-simulation.md)。


<!-- ====================================================================== -->
## <a name="available-themes"></a>可用主题

默认情况下，DevTools 主题设置为系统首选项 (也称为******系统首选颜色**主题) 。  如果你的操作系统设置为浅色主题，DevTools 将使用 **浅色+** 主题。  如果你的操作系统设置为深色主题，DevTools 将使用 **深色+** 主题。  但是，你可以将 DevTools 更改为任何其他主题，以便当将操作系统设置为浅色或深色主题时，DevTools 不会受到影响。

浅色主题：
- 浅色+ (默认) 
- Chromium浅
- 安静光
- 太阳能化光

深色主题：
- 深色+ (默认) 
- 深渊
- Chromium深
- 金月深色
- Monokai
- Mono kai Dimmed
- 红色
- 太阳能化深色
- 明晚蓝色


<!-- ====================================================================== -->
## <a name="changing-the-color-theme-from-settings"></a>更改颜色主题设置

1. 打开 DevTools，**然后选择设置 (** 齿轮图标) 。

   :::image type="content" source="./media/setting-button.png" alt-text="The 设置 (gear) icon" lightbox="./media/setting-button.png":::

1. 选择 **首选项**，然后在"外观 **"部分，** 从"主题"下拉列表 **中选择** 主题。

:::image type="content" source="./media/customize-theme-setting.png" alt-text="在首选项中选择主题。" lightbox="./media/customize-theme-setting.png":::


<!-- ====================================================================== -->
## <a name="changing-the-color-theme-from-the-command-menu"></a>从命令菜单更改颜色主题

若要使用命令菜单更改应用于 DevTools 的颜色主题：

1. [打开“命令”菜单](../command-menu/index.md)。

1. 键入 `theme`，然后选择一个 **Appearance** 命令，例如 **Appearance： Switch to Abyss theme** or **Appearance： Switch to Light+ (Default) theme**.

1. 按 `Enter`。

:::image type="content" source="./media/customize-theme-command-menu.png" alt-text="命令菜单中的主题列表。" lightbox="./media/customize-theme-command-menu.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/customize/dark-theme)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
