---
title: '将 DevTools 放置 (Undock，将扩展坞更改为底部，将扩展坞更改为左侧) '
description: 如何将 Microsoft Edge DevTools 移动到视区底部或左侧或单独的窗口。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: d952a4a70dd66adec315850347cb4f2b302da3fb
ms.sourcegitcommit: fd3b79a0570cfefc2a40107b223569210cb2c2d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2021
ms.locfileid: "12268953"
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
# <a name="change-devtools-placement-undock-dock-to-bottom-dock-to-left"></a>将 DevTools 放置 (Undock，将扩展坞更改为底部，将扩展坞更改为左侧) 

默认情况下，Microsoft Edge DevTools 固定在视口窗口 (右侧) 。  还可以将 DevTools 停靠在窗口底部或左侧，或者将 DevTools 停靠到单独的窗口。

DevTools 固定到窗口左侧：

:::image type="content" source="../media/customize-elements-styles-right-docked.msft.png" alt-text="DevTools 固定到窗口的左侧。" lightbox="../media/customize-elements-styles-right-docked.msft.png":::

DevTools 固定到窗口底部：

:::image type="content" source="../media/customize-elements-styles-bottom-docked.msft.png" alt-text="DevTools 固定到窗口底部。" lightbox="../media/customize-elements-styles-bottom-docked.msft.png":::

DevTools 可以撤消停靠到单独的窗口，你可以移动到单独的监视器。  浏览器随后具有自己的专用窗口，没有 DevTools，已取消停靠：

:::image type="content" source="../media/customize-elements-styles-options-dock-side-highlight-browser.msft.png" alt-text="没有 DevTools 的其自己的专用窗口中的浏览器，已取消停靠。" lightbox="../media/customize-elements-styles-options-dock-side-highlight-browser.msft.png":::

然后，DevTools 将撤消停靠到其自己的单独专用窗口中：

:::image type="content" source="../media/customize-elements-styles-options-dock-side-highlight-devtools.msft.png" alt-text="DevTools 已取消停靠到其自己的单独专用窗口中。" lightbox="../media/customize-elements-styles-options-dock-side-highlight-devtools.msft.png":::


<!-- ====================================================================== -->
## <a name="change-placement-from-the-main-menu"></a>从主菜单更改位置

1.  单击"自定义和控制**DevTools** () "，然后选择"撤消停靠到单独的窗口" ("撤消停靠) "，选择"停靠到底部 (扩展坞到底部) "，或选择"扩展坞向左 (扩展坞向左 `...` **** ![ ](../media/undock-icon.msft.png) **** ![ ](../media/bottom-icon.msft.png) **** ![ ](../media/left-icon.msft.png)) "。

:::image type="content" source="../media/customize-elements-styles-options-dock-side-highlight.msft.png" alt-text="选择&quot;撤消停靠到单独的窗口&quot;。" lightbox="../media/customize-elements-styles-options-dock-side-highlight.msft.png":::


<!-- ====================================================================== -->
## <a name="change-placement-from-the-command-menu"></a>从命令菜单更改位置

1.  [打开命令菜单](../command-menu/index.md)，选择 `Shift` + `Ctrl` + `P` "Windows/Linux"或 `Command` + `Shift` + `P` macOS。
1.  在 `>` 字符后输入 `dock` ，然后选择以下命令之一：

    *  **扩展坞到底部**
    *  **扩展坞向左**
    *  **扩展坞向右**
    *  **还原最后一个扩展坞位置**
    *  **撤消停靠到单独的窗口中**

    您还可以从主菜单访问 [这些命令](#change-placement-from-the-main-menu)。

    :::image type="content" source="../media/customize-elements-styles-command-menu-undo.msft.png" alt-text="Undock 命令。" lightbox="../media/customize-elements-styles-command-menu-undo.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/customize/placement)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors#kayce-basques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
