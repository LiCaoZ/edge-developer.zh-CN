---
title: 分析边栏菜单中键盘焦点的缺失
description: 分析边栏菜单中缺少键盘焦点指示，因为链接上的焦点状态缺少 CSS 伪类规则，再加上该链接没有大纲设置。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
---
# <a name="analyze-the-lack-of-indication-of-keyboard-focus-in-a-sidebar-menu"></a>分析边栏菜单中键盘焦点的缺失

<!-- Inspect tool, and CSS rules: pseudo-classes for states -->

在辅助功能测试演示页面中，使用键盘时，包含蓝色链接的边栏导航菜单不会直观地指示哪个链接具有焦点。  为了找出为什么边栏菜单使键盘用户感到困惑，我们将查找适用于 和 状态的 CSS `hover` `focus` 伪类规则，以及链接大纲的 CSS 属性。

此分析发现页面的边栏导航菜单的链接中缺少键盘焦点指示的原因是：
*  链接 `a` 的 CSS 属性设置为 `outline: none`。
*  这些 `a` 链接缺少状态 CSS 伪类 `:focus` 规则。

若要导航到 CSS，我们将使用 **Inspect** 工具突出显示页面边栏导航菜单上的蓝色链接，然后查看定义该链接的元素的 DOM 树和 CSS `a` 。

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 单击 **"检查** ![](../media/inspect-tool-icon-light-theme.png) (检查"图标。) 位于 DevTools 左上角的"检查"按钮，使按钮以蓝色 (突出显示) 。

1. 将鼠标悬停在页面边栏导航菜单中的蓝色 **"猫** "链接上。  将显示 Inspect 覆盖层，显示 `a` 元素是可键盘聚焦的。  但是覆盖层不会显示当链接具有焦点时没有视觉指示。

   接下来，我们将检查此链接的 CSS 样式。

1. 单击边栏导航菜单中的 **"猫** "链接。  检查 **工具** 将关闭， **并且元素** 工具将打开，突出显示 `a` DOM 树中的节点。

1. 在 DevTools 中，选择 **"样式"** 选项卡。 将显示 CSS 规则 `#sidebar nav li a` ，以及指向 中行号的链接 `styles.css`。

   :::image type="content" source="../media/a11y-testing-menu-link.msft.png" alt-text="检查菜单中的链接的源代码和应用样式。" lightbox="../media/a11y-testing-menu-link.msft.png":::

1. 单击链接 `styles.css` 。  CSS 文件在"源" **工具中** 打开。

   :::image type="content" source="../media/a11y-testing-menu-link-styles.msft.png" alt-text="应用于&quot;源&quot;工具中链接的样式。" lightbox="../media/a11y-testing-menu-link-styles.msft.png":::

   页面样式具有 CSS 伪类 `hover` 规则，用于指示在使用鼠标时位于哪个菜单项上 `#sidebar nav li a:hover`：。  但是，没有 CSS 伪类 `focus` 规则，当使用键盘时，状态会直观地指示您位于哪个菜单项上，例如 `#sidebar nav li a:focus`。

   此外，请注意链接的 CSS 属性设置为 `outline: none`。  这是一种常见做法，当你使用键盘关注元素时，删除浏览器自动添加到元素的大纲。  不使用 `focus` 样式设置会导致用户混淆。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [跟踪哪些元素有焦点](focus.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
