---
title: 验证页面是否在关闭 UI 动画时可用
description: 使用渲染工具中的模拟 CSS 媒体功能 prefer-reduced-motion 下拉列表 (使用模拟 CSS 媒体功能 (减少) 运动，检查网页是否可用于关闭 UI 动画。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: a02a3959a053b2d12a3584506774fc1f84c7d91c
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12553289"
---
# <a name="verify-that-a-page-is-usable-with-ui-animation-turned-off"></a>验证页面是否在关闭 UI 动画时可用

网页不应向在操作系统中关闭动画的用户显示动画。  动画可以帮助产品可用性，但它们也会造成干扰、混乱或恶心。

若要检查网页是否可用于关闭 UI 动画 (减少运动) ，请在 **渲染** 工具中使用 **模拟 CSS 媒体功能 prefers-reduced-motion** 下拉列表。

在辅助功能测试演示网页中，在操作系统中关闭动画或使用 DevTools 模拟设置时，选择边栏导航菜单的链接时，网页不会使用平滑滚动。  这是通过在媒体查询中包装 CSS 中的平滑滚动设置，然后使用 **呈现** 工具模拟操作系统设置以减少动画来实现的。

若要检查页面是否可在已关闭的动画中使用：

1. 在新窗口或选项卡中打开 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击网页中的任意位置，然后选择 **“检查**”。  或者按 `F12`。  DevTools 将在网页旁边打开。

1. 在 DevTools 的顶部，选择 **“源** ”工具，然后在左侧的 **“导航** ”窗格中选择 `styles.css`。  CSS 文件显示在 **“编辑器** ”窗格中。

1. 按`Ctrl`+`F`Windows/Linux 或`F``Command`+macOS，然后输入。`@media`  将显示以下 CSS 媒体查询，确认它已在网页上使用。

    ```css
    @media (prefers-reduced-motion: no-preference) {
      html {
        scroll-behavior: smooth;
      }
    }
    ```

    接下来，模拟操作系统设置以减少动画，如下所示。

1. 按 `Esc` 下以打开 DevTools 底部的抽屉。  单击抽屉顶部的“ **更多工具** (**+**) ”按钮，查看工具列表，然后选择 **“呈现**”。

1. 在 **模拟 CSS 媒体功能首选-减动作** 下拉列表中，选择 **“首选-缩减”运动：减少**。

   ![模拟减小运动和 CSS，确保仅在用户需要时才会进行平滑滚动。](../media/a11y-testing-simulating-reduced-motion.msft.png)

1. 在网页中，单击蓝色菜单项，如 **“马** ”或 **“羊驼**”。  现在，网页会立即滚动到所选部分，而不是使用平滑滚动动画。

1. 在 **“渲染** ”工具的“ **模拟 CSS 媒体功能首选-减动”** 下，选择 **“无仿真** ”以删除此设置。

请注意，演示网页仍然运行以下动画，即使具有上述媒体查询和仿真设置。 生成网站时，请确保修复所有类似的动画：
*  将鼠标悬停在蓝色菜单项上的动画。
*  将鼠标悬停在“ **更多** ”链接上的圆圈的动画。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [运动模拟减少](reduced-motion-simulation.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
