---
description: 自定义 DevTools Microsoft Edge列表
title: 自定义 Microsoft Edge DevTools
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: ae54eb9a0c100a6dc1b6608dc05ddad5d655ee02
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12140989"
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
# <a name="customize-microsoft-edge-devtools"></a>自定义 Microsoft Edge DevTools

此页面列出了自定义 DevTools Microsoft Edge的方法。


<!-- ====================================================================== -->
## <a name="settings"></a>“设置”

**设置**  > **首选项**包含许多用于自定义 DevTools 的选项。

有两种方法可以打开设置。

*   Select the**设置**icon (![ 设置 icon ](../media/settings-icon-dark.msft.png)) .
*   当 DevTools 具有焦点时，选择 `F1` 。

:::image type="complex" source="../media/customize-settings-preferences.msft.png" alt-text="设置" lightbox="../media/customize-settings-preferences.msft.png":::
   **设置**
:::image-end:::


<!-- ====================================================================== -->
## <a name="drawer"></a>"箱"

The **Drawer** is a second panel where you can choose which tools to display.

若要打开 (或关闭) **收银机"，** 请选择 `Escape` 。

:::image type="complex" source="../media/customize-drawer-open.msft.png" alt-text="The Drawer" lightbox="../media/customize-drawer-open.msft.png":::
   The **Drawer**
:::image-end:::

可以在主面板和箱之间移动工具。

*   若要将工具从工具箱移动到主面板，请将鼠标悬停在工具上，打开上下文菜单 (右键单击") 然后选择"移动到**顶部"。**

    :::image type="complex" source="../media/move-from-drawer.msft.png" alt-text="将工具从&quot;箱&quot;移到主面板" lightbox="../media/move-from-drawer.msft.png":::
       将工具从 **"箱"** 移到主面板
    :::image-end:::

*   若要将工具从主面板移动到箱中，请将鼠标悬停在工具上，打开上下文菜单 (右键单击") 然后选择"移动到**底部"。**

    :::image type="complex" source="../media/move-to-drawer.msft.png" alt-text="将工具从主面板移动到&quot;箱&quot;" lightbox="../media/move-to-drawer.msft.png":::
       将工具从主面板移动到"箱 **"**
    :::image-end:::


<!-- ====================================================================== -->
## <a name="reorder-tools"></a>对工具重新排序

选择并拖动工具以更改排序。  你的自定义工具顺序在整个 DevTools 会话中持续存在。

> [!NOTE]
> 默认情况下， **网络工具** 通常是主工具栏上的第五个选项卡。  在下图中， **网络** 工具将移动为主工具栏的第一个选项卡。

:::image type="complex" source="../media/customize-network-first-position.msft.png" alt-text="面板中 Devtools 的自定义顺序" lightbox="../media/customize-network-first-position.msft.png":::
   面板中 Devtools 的自定义顺序
:::image-end:::


<!-- ====================================================================== -->
## <a name="open-and-close-tools"></a>打开和关闭工具

若要简化 DevTools 接口，默认情况下不会打开许多工具。 若要在主面板或"箱"中打开**** 工具，请选择选项卡**** 右边的"更多工具 (更多工具) 按钮，然后从列表中选择 ![ 一个 ](../media/open-tab-icon.png) 工具。

:::image type="complex" source="../media/open-tool-in-main-panel-or-drawer.png" alt-text="&quot;更多工具 (+) &quot;按钮以打开新工具" lightbox="../media/open-tool-in-main-panel-or-drawer.png":::
   " **更多工具** `+` () "按钮打开新工具
:::image-end:::

若要关闭工具，请选择工具 (**** 中的"关闭) ![ ](../media/close-tab-icon.png) 关闭工具"按钮。

:::image type="complex" source="../media/close-tool-in-main-panel-or-drawer.png" alt-text="选项卡的&quot;关闭&quot;按钮" lightbox="../media/close-tool-in-main-panel-or-drawer.png":::
   选项卡的" **关闭"** 按钮
:::image-end:::


<!-- ====================================================================== -->
## <a name="change-devtools-placement"></a>更改 DevTools 放置

导航到 [Change DevTools placement (Undock， Dock to bottom， Dock to left) ][DevToolsPlacement].

:::image type="complex" source="../media/customize-dev-tools-dock-side.msft.png" alt-text="移除的开发人员工具" lightbox="../media/customize-dev-tools-dock-side.msft.png":::
   移除的开发人员工具
:::image-end:::


<!-- ====================================================================== -->
## <a name="color-themes"></a>颜色主题

导航到 [将颜色主题应用到 DevTools][Theme]。

:::image type="complex" source="./media/customize-theme-setting.png" alt-text="选择其他颜色主题" lightbox="./media/customize-theme-setting.png":::
   选择其他颜色主题
:::image-end:::


<!-- ====================================================================== -->
## <a name="restore-default-settings"></a>还原默认设置

若要还原默认主题、放置、工具顺序和任何其他自定义设置，请选择"设置****  >  ****  >  **首选项""还原默认值并刷新"。**

:::image type="complex" source="../media/restore-default-settings.png" alt-text="还原默认设置" lightbox="../media/restore-default-settings.png":::
   还原默认设置
:::image-end:::


<!-- ====================================================================== -->
<!-- links -->
[DevToolsPlacement]: ./placement.md "更改 Microsoft Edge DevTools 放置 | Microsoft Docs"
[Theme]: ./theme.md "将颜色主题应用到 DevTools |Microsoft Docs"
<!-- image links -->
[ImageMoreIcon]: ../media/more-icon.msft.png


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/customize/index)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [][KayceBasques]

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
