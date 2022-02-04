---
title: 验证页面是否在关闭 UI 动画时可用
description: 使用"呈现"工具中的"模拟 CSS 媒体) 首选"减少运动"下拉列表，检查网页是否可用，关闭 UI 动画 (减少运动效果。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
---
# <a name="verify-that-a-page-is-usable-with-ui-animation-turned-off"></a>验证页面是否在关闭 UI 动画时可用

网页不应向在操作系统中关闭动画的用户显示动画。  动画可以帮助产品的可用性，但它们也会导致干扰、混淆或混乱。

若要检查网页是否可使用关闭 UI 动画 (减少运动) ，请在"呈现"工具中，使用"模拟 CSS 媒体"**** 功能**首选**"减少运动"下拉列表。

在辅助功能测试演示网页中，关闭操作系统中的动画或使用 DevTools 模拟该设置时，当您选择边栏导航菜单的链接时，网页不会使用平滑滚动。  这是通过以下方法实现的：在媒体查询中将平滑滚动设置包装在 CSS 中，然后使用 **呈现** 工具模拟操作系统设置，以减小动画效果。

若要检查页面是否可用，请关闭动画：

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 在 DevTools 顶部，选择"源"**** 工具，然后在左侧的"导航****"窗格中，选择 `styles.css`。  CSS 文件显示在"编辑器 **"** 窗格中。

1. 按 `Ctrl`+`F` Windows/Linux 或`F` `Command`+macOS，然后输入 。`@media`  将显示以下 CSS 媒体查询，用于确认它在网页上使用。

    ```css
    @media (prefers-reduced-motion: no-preference) {
      html {
        scroll-behavior: smooth;
      }
    }
    ```

    接下来，模拟操作系统设置以减少动画，如下所示。

1. 按 `Esc` 打开 DevTools 底部的"箱"。  Click the **More tools** () **+** button at the top of the Drawer to see the list of tools， and then select **Rendering**.

1. 在" **模拟 CSS 媒体功能首选-减少** 运动"下拉列表中，选择 **"首选减少运动：减少"**。

   :::image type="content" source="../media/a11y-testing-simulating-reduced-motion.msft.png" alt-text="模拟减少的动作和 CSS，以确保仅在用户需要时发生平滑滚动。" lightbox="../media/a11y-testing-simulating-reduced-motion.msft.png":::

1. 在网页中，单击蓝色菜单项，如 **"云** "或" **Alpacas"**。  现在，网页立即滚动到选定部分，而不是使用平滑滚动动画。

1. 在 **呈现工具** 中，在" **模拟 CSS 媒体功能首选减少运动**"下，选择"无 **模拟** "以删除此设置。

请注意，即使使用上述媒体查询和模拟设置，演示网页仍运行以下动画。 生成 Web 产品时，请确保修复所有类似的动画：
*  将鼠标悬停在蓝色菜单项上的动画。
*  将鼠标悬停在"更多"**** 链接上的圆圈的动画。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [减少运动模拟](reduced-motion-simulation.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
