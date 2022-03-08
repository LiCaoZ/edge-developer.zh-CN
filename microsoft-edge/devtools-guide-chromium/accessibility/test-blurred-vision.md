---
title: 验证页面是否在视觉模糊时可用
description: 若要验证网页是否可使用模糊视觉，在"呈现"工具中，使用"模拟视觉缺陷"下拉列表。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: a56b66679eac43e3d402f93169b02240b7de21a1
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430939"
---
# <a name="verify-that-a-page-is-usable-with-blurred-vision"></a>验证页面是否在视觉模糊时可用

<!-- Rendering tool: Emulate vision deficiencies: Blurred vision -->

若要模拟模糊的视觉，在 **呈现工具** 中，使用 **"模拟视觉缺陷"** 菜单。  当您将此功能与演示网页一同使用时，可以看到上菜单中文本的投影使阅读菜单项变得困难。

若要检查网页是否具有模糊的视觉，请进行查看：

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 按 **Esc** 打开 DevTools 底部的"箱"。  **+** 单击"箱"顶部的图标以显示工具列表，然后选择"呈现 **"**。

1. 在" **模拟视觉缺陷** "下拉列表中，选择" **模糊的视觉"**。

   ![模拟模糊的页面。](../media/a11y-testing-simulating-blur.msft.png)

    请注意， `text-shadow` CSS 属性使上方菜单上的菜单项文本难以阅读。 例如，请参阅 **Home、****Adopt a Pb** 和其他菜单项。

1. 在 **呈现工具的** " **模拟视觉缺陷"** 中，选择"无 **模拟** "以删除模糊的视觉模拟。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [模仿视觉缺陷](emulate-vision-deficiencies.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
