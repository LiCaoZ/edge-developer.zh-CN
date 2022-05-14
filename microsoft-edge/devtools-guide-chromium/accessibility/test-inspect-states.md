---
title: 验证元素的所有状态的可访问性
description: 使用“切换元素状态”检查样式窗格中所有元素状态（例如悬停状态期间的文本对比度）的可访问性。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 6dd30e1aba9336df764363765faf90f0991fbe4e
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12513822"
---
# <a name="verify-accessibility-of-all-states-of-elements"></a>验证所有元素状态可访问性

<!-- 5. STYLES: TOGGLE STATE -->

检查元素的所有状态（如状态期间的文本颜色对比度）的 `hover` 辅助功能。  “ **检查** ”工具一次报告一个状态的辅助功能问题。  若要检查各种元素状态的可访问性，请在“ **样式”** 选项卡中，选择 **\：hov** (**切换元素状态**) ，如本文所述。

我们首先演示为何需要使用 **“检查** ”工具进行状态模拟，然后演示如何使用状态模拟。


<!-- ====================================================================== -->
## <a name="checking-text-color-contrast-in-the-default-state"></a>检查默认状态下的文本颜色对比度

<!-- Inspect tool: information overlay: Accessibility section: Contrast row -->

除了 **问题** 工具中的自动颜色对比度测试外，还可以使用 **“检查** ”工具检查各个页面元素是否有足够的对比度。  如果有对比度信息可用， **则检查** 覆盖显示对比度和复选框项。  绿色复选标记图标指示有足够的对比度，黄色警报图标指示没有足够的对比度。

例如，边栏导航菜单中的链接具有足够的对比度，如 **“检查** ”覆盖层中所示：

:::image type="content" source="../media/a11y-testing-enough-contrast.msft.png" alt-text="边栏导航菜单中的链接具有足够的对比度，如“检查”覆盖层中所示。" lightbox="../media/a11y-testing-enough-contrast.msft.png":::

**“捐赠状态**”部分中的绿色**狗**列表项没有足够的对比度，因此会在 **“检查**”覆盖层中通过警告进行标记：

:::image type="content" source="../media/a11y-testing-not-enough-contrast.msft.png" alt-text="检查覆盖层中的警告标记了没有足够的对比度的元素" lightbox="../media/a11y-testing-not-enough-contrast.msft.png":::


<!-- ====================================================================== -->
## <a name="hovering-when-the-inspect-tool-is-active-doesnt-show-the-text-color-contrast-for-the-hover-state"></a>当检查工具处于活动状态时悬停不会显示悬停状态的文本颜色对比度

**检查**工具的信息覆盖仅表示单个状态。  页面上的元素可以具有不同的状态，所有这些状态都需要测试。  例如，将鼠标指针悬停在辅助功能测试演示页菜单上时，会获得更改颜色的动画。

首先，确认动画在未使用“检查”工具时运行：

1. 在新窗口或选项卡中打开 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击网页中的任意位置，然后选择 **“检查**”。  或者按 `F12`。  DevTools 将在网页旁边打开。

1. 在呈现的网页中，将鼠标悬停在侧栏导航菜单中的蓝色菜单项上。  请注意，每个项都有一个动画。

   :::image type="content" source="../media/a11y-testing-hover.msft.png" alt-text="鼠标指针位于其上时显示不同颜色的菜单项。" lightbox="../media/a11y-testing-hover.msft.png":::

接下来，使用“检查”工具确认动画未运行：

1. 单击“ **检查** ”工具 (![“检查”工具图标。](../media/inspect-tool-icon-light-theme.png)) DevTools 左上角的按钮。

   突出显示了 **“检查** ”工具图标;例如，它从灰色更改为蓝色。

   使用“检查”工具时，当将鼠标悬停在菜单项上时，菜单项上的动画将不会运行。  使用“检查”工具时，无法访问 `hover` 菜单项上的状态来测试对比度比率，因为 `hover` 不会触发样式中的状态。

1. 在呈现的网页中，将鼠标悬停在侧栏导航菜单上的蓝色链接上。  菜单项的动画不运行。  而是使用弹性框覆盖的颜色突出显示来显示菜单项。

以这种方式检查足够的文本对比度是不够的，因为页面上的元素可能具有不同的状态。


<!-- ====================================================================== -->
## <a name="use-state-simulation-to-simulate-the-hover-state-of-an-animated-menu-item"></a>使用状态模拟模拟动画菜单项的悬停状态

<!-- Elements tool: Styles pane: "Toggle Element State" icon tooltip; displays "Force element state" section -->

当 **“检查** ”工具处于活动状态时，需要模拟菜单项的状态，而不是将鼠标悬停在动画元素上。  若要模拟菜单项的状态，请在“ **样式** ”窗格中使用状态模拟。  “ **样式”** 窗格有一个 **\：hov** (**“切换元素状态**) ”按钮，该按钮显示标记为 **Force 元素状态**的一组复选框。

使用“检查”工具时打开悬停状态：

1. 在新窗口或选项卡中打开 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击网页中的任意位置，然后选择 **“检查**”。  或者按 `F12`。  DevTools 将在网页旁边打开。

1. 单击“ **检查** (![检查”工具按钮。](../media/inspect-tool-icon-light-theme.png)) DevTools 左上角的按钮，使图标突出显示 (蓝色) 。

1. 在呈现的网页中，选择边栏导航菜单中的蓝色 **猫** 链接。  **“元素**”工具随即打开，其中选择了元素`<a href="#cats">Cats</a>`。

   :::image type="content" source="../media/a11y-testing-inspecting-link-to-hover.msft.png" alt-text="检查元素工具中具有悬停状态的元素。" lightbox="../media/a11y-testing-inspecting-link-to-hover.msft.png":::

1. 选择“ **样式”** 选项卡。 所选 `a` 元素在 CSS 中具有 `hover` 应用于它的状态，但在“ **样式** ”窗格中不可见。

1. 在“**样式**”窗格中，选择样式规则`#sidebar nav li a``styles.css`右侧的链接。  “ **源** ”工具随即打开。  然后找到 CSS 伪类规则 `#sidebar nav li a:hover`。  当 **检查** 工具处于活动状态时，此规则不会运行。  我们将在后续步骤中模拟运行此状态规则。

1. 选择 **“元素”** 工具。  Then in the **Styles** pane, select the **:hov** (**Toggle Element State**) button.  将显示 **Force 元素状态** 复选框部分。

   :::image type="content" source="../media/a11y-testing-state-simulation.msft.png" alt-text="显示所有选项的状态模拟工具。" lightbox="../media/a11y-testing-state-simulation.msft.png":::

1. 单击 **“悬停”** 复选框。  在元素左侧的 `<a href="#cats">Cats</a>`DOM 中，将显示一个黄色点，指示该元素具有模拟状态。  **“猫”** 菜单项现在显示在网页中，就像指针悬停在它上面一样。  菜单项上的动画可能会运行。

   :::image type="content" source="../media/a11y-testing-hover-simulated.msft.png" alt-text="开发工具模拟悬停状态。" lightbox="../media/a11y-testing-hover-simulated.msft.png":::

    应用模拟状态后，当用户将鼠标悬停在元素上时，可以再次使用 **“检查** ”工具检查元素的对比度，如下所示。

1. 选择 **“检查** (![检查器”图标。](../media/inspect-tool-icon-light-theme.png)) DevTools 左上角的按钮，以便在蓝色)  (突出显示该图标。

1. 将鼠标悬停在侧栏导航菜单中的蓝色 **猫** 链接上。  由于模拟悬停动画，此链接现在为浅蓝色。  此时会显示 **“检查** ”工具的信息叠加，显示 **对比度** 行中的橙色感叹号，指示对比度不够高。

   :::image type="content" source="../media/a11y-testing-hover-contrast-testing.msft.png" alt-text="测试处于模拟悬停状态的元素的对比度。" lightbox="../media/a11y-testing-hover-contrast-testing.msft.png":::

状态模拟也是检查是否考虑了不同用户需求（如键盘用户的需求）的好方法。  通过使用 **Force 元素状态** 复选框，可以模拟 `:focus` 状态，以发现当 UI 具有焦点时 UI 保持不变。 当元素具有焦点时缺少指示器是个问题。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
