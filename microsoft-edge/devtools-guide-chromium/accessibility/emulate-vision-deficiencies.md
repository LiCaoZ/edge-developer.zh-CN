---
description: 在 DevTools 中模拟Microsoft Edge缺陷。
title: '在 DevTools Microsoft Edge色盲 (中模拟视觉缺陷) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/07/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 97530fed874dfd915e3081c935509a6ae97b4321
ms.sourcegitcommit: 0eca205728eeca1bd54b3ca34dfc81ec57cf16d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2021
ms.locfileid: "12082587"
---
# <a name="emulate-vision-deficiencies"></a>模仿视觉缺陷

为了更好地满足色盲[\ (][ColorblindawarenessMain]色盲\) 或模糊视觉的用户的需求[，Microsoft Edge DevTools][DevtoolsIndex]允许你模拟模糊的视觉和特定的颜色视觉缺陷。  模拟 **视觉缺陷工具** 可模拟以下类别。

| 色盲 | 详细信息 |
|:--- |:--- |
| 模糊的视觉 | 用户很难专注于细节。 |
| 红色盲 | 用户无法感知任何红色光。 |
| 绿色盲 | 用户无法感知任何绿色光。 |
| 黄蓝色盲 | 用户无法感知任何蓝色光。 |
| 全色盲 | 用户无法感知任何颜色，这会降低所有颜色为灰色底纹。 |


<!-- ====================================================================== -->
## <a name="open-the-rendering-tool"></a>打开呈现工具

若要模拟对 Web 产品应用的视觉缺陷，请打开["呈现工具"。][DevtoolsRenderingToolsIndex]

1.  若要打开呈现工具，请选择 `...` 工具栏中的菜单项。
1.  选择 **"更多工具"。**
1.  选择 **"呈现"。**

    :::image type="complex" source="../media/getting-to-the-rendering-tools.msft.png" alt-text="打开呈现工具" lightbox="../media/getting-to-the-rendering-tools.msft.png":::
       打开 **呈现** 工具
    :::image-end:::

" **呈现** "菜单显示在箱中。

1.  向下滚动到 `Emulate vision deficiencies` 菜单项并选择下拉菜单以显示选项。

    :::image type="complex" source="../media/accessibility-emulate-vision-menu.msft.png" alt-text="呈现工具上的&quot;模拟视觉缺陷&quot;菜单" lightbox="../media/accessibility-emulate-vision-menu.msft.png":::
       呈现 **工具上的** "模拟视觉缺陷 **"** 菜单
    :::image-end:::

1.  选择一个选项。

    :::image type="complex" source="../media/accessibility-emulate-vision-menu-options.msft.png" alt-text="&quot;模拟视觉缺陷&quot;菜单选项" lightbox="../media/accessibility-emulate-vision-menu-options.msft.png":::
       " **模拟视觉缺陷"** 菜单选项
    :::image-end:::

1.  主窗口显示对应用于当前页面的选定选项的模拟。

    :::row:::
       :::column span="":::
          :::image type="complex" source="../media/accessibility-blurred-vision-emulation.msft.png" alt-text="使用模糊视觉模拟显示" lightbox="../media/accessibility-blurred-vision-emulation.msft.png":::
             使用**模糊视觉模拟显示** :::image-end:::
       :::column-end:::
       :::column span="":::
          :::image type="complex" source="../media/accessibility-achromatopsia-emulation.msft.png" alt-text="使用 Achromatop进行模拟显示" lightbox="../media/accessibility-achromatopsia-emulation.msft.png":::
             使用**Achromatop进行模拟显示** :::image-end:::
       :::column-end:::
    :::row-end:::


<!-- ====================================================================== -->
## <a name="use-the-command-menu"></a>使用命令菜单

作为替代方法，可以使用命令 **菜单** 访问不同的模拟。

1.  选择 `Ctrl` + `Shift` + `P` \ (Windows/Linux\) 或 `Command` + `Shift` + `P` \ (macOS\) 打开命令**菜单**。

    :::image type="complex" source="../media/css-console-command-menu-rendering.msft.png" alt-text="命令菜单" lightbox="../media/css-console-command-menu-rendering.msft.png":::
       **命令菜单**
    :::image-end:::

1.  键入 `emulate` ，选择要模拟的，然后选择 `Enter` 。

    :::image type="complex" source="../media/accessibility-emulation-command-menu-results.msft.png" alt-text="命令菜单中提供的不同模拟选项" lightbox="../media/accessibility-emulation-command-menu-results.msft.png":::
       命令菜单中提供的不同 **模拟选项**
    :::image-end:::

> [!IMPORTANT]
> " **模拟视觉缺陷"** 工具模拟每个缺陷人士可能如何查看你的产品的近似值。  每个人是不同的，因此视觉缺陷的严重性因人而异。  为了更好地满足用户的需求，请避免任何可能导致问题的颜色组合。  模拟 **视觉缺陷** 工具不是产品的完整辅助功能评估。  相反 **，"模拟视觉缺陷"** 工具应为您提供良好的第一步以避免出现问题。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [验证页面是否可借助模糊视图](test-blurred-vision.md)


<!-- ====================================================================== -->
<!-- links -->
[DevToolsIndex]: ../index.md "Microsoft Edge (Chromium) 开发人员工具 | Microsoft Docs"
[DevtoolsRenderingToolsIndex]: ../rendering-tools/index.md "分析运行时性能|Microsoft Docs"

[ColorblindawarenessMain]: https://www.colourblindawareness.org "光盲意识组织"

[AmfcbMain]: https://www.amfcb.org "American Foundation for the Color Blind (AFCB) "
