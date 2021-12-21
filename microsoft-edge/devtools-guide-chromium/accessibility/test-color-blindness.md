---
title: 验证页面是否对色盲者可用
description: 使用呈现工具中的"模拟视觉缺陷"下拉列表，检查具有色盲的人是否可使用此网页。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 06/07/2021
ms.openlocfilehash: 9d56e2337e3755f21200275eb7bbd6c84ab741f4
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285496"
---
# <a name="verify-that-a-page-is-usable-by-people-with-color-blindness"></a>验证页面是否对色盲者可用

<!-- Rendering tool: Emulate vision deficiencies: Protanopia -->

若要检查网页是否由色盲人士使用，请在"呈现"工具中****，使用"模拟视力**缺陷"下拉列表**。

在辅助功能测试演示网页上，不同的接收状态使用颜色作为区别的唯一方法。
*  绿色表示已收到大量资金。
*  黄色表示已收到中等金额的笔款。
*  红色表示已收到少量资金。

但是，你无法预期你的所有用户都如预期体验这些颜色。  通过使用呈现**工具的"** 模拟视觉缺陷"功能****，你可以模拟不同视觉的人如何理解你的设计，发现此设计不够好。


检查网页是否由色盲用户使用：

1.  在 [浏览器的新选项卡中](https://microsoftedge.github.io/DevToolsSamples/a11y-testing/page-with-errors.html) 打开辅助功能测试演示网页，然后选择 **F12** 以打开 DevTools。

1.  选择 **Esc** 打开 DevTools 底部的"箱"。  Select the **+** icon at the top of the Drawer to see the list of tools， and then select **Rendering**.

1.  在"**模拟视力**障碍"下拉列表中，选择 **"Protanopia"。**  _Protanopia_ 对红色光的敏感度降低，使得难以区分绿色、红色和黄色。

    :::image type="complex" source="../media/a11y-testing-simulating-protanopia.msft.png" alt-text="将文档作为具有 protanopia 的人显示将会看到它" lightbox="../media/a11y-testing-simulating-protanopia.msft.png":::
        将文档作为具有 protanopia 的人显示将会看到它
    :::image-end:::

1.  在 **呈现工具的** " **模拟视觉缺陷"下**，选择"无 **模拟** "以删除模拟。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [模拟视觉](./emulate-vision-deficiencies.md)缺陷 - 定义"模拟视觉缺陷****"下拉列表中的项目，包括 Protanopia、Deuteranopia、Tritanopia 和 Achromatopia。
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
