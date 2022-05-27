---
title: 模仿视觉缺陷
description: 模拟 Microsoft Edge DevTools 中的视力缺陷。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 96ca408c28933e1a748ee80fcb4d9753b4450992
ms.sourcegitcommit: cceea19c69eddaad5ba7d6cece07fbca2b02614e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2022
ms.locfileid: "12551517"
---
# <a name="emulate-vision-deficiencies"></a>模仿视觉缺陷

为了更好地满足视力[不足 (色](https://www.colourblindawareness.org)盲) 或视力模糊的用户的需求，[Microsoft Edge DevTools](../index.md) 允许你模拟模糊的视觉和特定的色视觉缺陷。  **模拟视觉缺陷**工具模拟以下类别：

| 色视觉缺陷 | 详细信息 |
|:--- |:--- |
| 视力 | 用户难以专注于详细信息。 |
| 红色盲 | 用户无法感知任何红灯。 |
| 绿色盲 | 用户无法看到任何绿灯。 |
| 黄蓝色盲 | 用户无法感知任何蓝光。 |
| 全色盲 | 用户无法感知任何颜色，这会将所有颜色都减为灰色阴影。 |

**模拟视觉缺陷**工具模拟每个缺陷患者如何看到你的产品的近似值。  每个人是不同的，因此视力缺陷在严重性上因人而异。  为了更好地满足用户的需求，请避免任何可能出现问题的颜色组合。  **模拟视觉缺陷**工具不提供产品的完全辅助功能评估，但提供了一个很好的第一步来避免问题。


<!-- ====================================================================== -->
## <a name="open-the-rendering-tool"></a>打开呈现工具

若要模拟视力缺陷患者如何查看网页，请打开 [呈现工具](../rendering-tools/index.md)。

1. 单击工具栏中的 **“自定义”并控制 DevTools** (`...`) 。

1. 转到 **“更多工具** > **呈现** ”，打开抽屉中的 **呈现** 面板。

   > [!div class="mx-imgBorder"]
   > ![从“更多工具”菜单打开呈现面板。](../media/getting-to-the-rendering-tools.msft.png)

1. 向下滚动到 **“模拟视觉缺陷** ”部分，单击 **“无仿真”** 下拉列表，然后选择一个选项。

   > [!div class="mx-imgBorder"]
   > ![呈现面板中的“模拟视觉缺陷”部分。](../media/accessibility-emulate-vision-menu-options.msft.png)

1. 浏览器窗口模拟当前页面上所选的视觉缺陷。

   > [!div class="mx-imgBorder"]
   > ![浏览器窗口，网页中已修改颜色，用于模拟所选颜色视觉缺陷。](../media/accessibility-blurred-vision-emulation.msft.png)


<!-- ====================================================================== -->
## <a name="use-the-command-menu"></a>使用命令菜单

作为替代方法，可以使用 **命令菜单** 访问不同的模拟。

1. 按“`Ctrl`+`Shift`+`P`”(Windows、Linux)或“`Command`+`Shift`+`P`”(macOS)以打开“**命令菜单**”。

1. 键 **入模拟**，选择要模拟的视觉缺陷类型，然后按下 `Enter`。

   > [!div class="mx-imgBorder"]
   > ![显示不同类型的视觉缺陷的命令菜单。](../media/accessibility-emulation-command-menu-results.msft.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [验证页面是否在视觉模糊时可用](test-blurred-vision.md)
