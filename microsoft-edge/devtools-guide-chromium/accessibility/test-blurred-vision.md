---
title: 验证页面是否在视觉模糊时可用
description: 若要验证网页是否可使用模糊视觉，在"呈现"工具中，使用"模拟视觉缺陷"下拉列表。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: efcc340ec814c379b18aeada8feb44f69cc389cc
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318049"
---
# <a name="verify-that-a-page-is-usable-with-blurred-vision"></a>验证页面是否在视觉模糊时可用

<!-- Rendering tool: Emulate vision deficiencies: Blurred vision -->

若要模拟模糊的视觉，在 **呈现工具** 中，使用 **"模拟视觉缺陷"** 菜单。  当您将此功能与演示网页一同使用时，可以看到上菜单中文本的投影使阅读菜单项变得困难。

若要检查网页是否具有模糊的视觉，请进行查看：

1.  在 [浏览器的新选项卡中](https://microsoftedge.github.io/DevToolsSamples/a11y-testing/page-with-errors.html) 打开辅助功能测试演示网页，然后选择 **F12** 以打开 DevTools。

1.  选择 **Esc** 打开 DevTools 底部的"箱"。  Select the **+** icon at the top of the Drawer to display the list of tools， and then select **Rendering**.

1.  在"**模拟视觉缺陷**"下拉列表中，选择"**模糊的视觉"。**

    :::image type="complex" source="../media/a11y-testing-simulating-blur.msft.png" alt-text="模拟模糊的页面" lightbox="../media/a11y-testing-simulating-blur.msft.png":::
        模拟模糊的页面
    :::image-end:::

    请注意，CSS 属性使上方菜单上的菜单项文本难以 `text-shadow` 阅读。 例如，查看 **"主页"、"****采用动物**"和其他菜单项。

1.  在 **呈现工具** 的" **模拟视觉缺陷"** 中，选择"无 **模拟** "以删除模糊的视觉模拟。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [模仿视觉缺陷](emulate-vision-deficiencies.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
