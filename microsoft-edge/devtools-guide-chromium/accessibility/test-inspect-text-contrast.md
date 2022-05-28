---
title: 使用检查工具检查默认状态下的文本颜色对比度
description: 使用“检查”工具在页面上的信息叠加（包含对比度信息的辅助功能部分）检查默认状态下的文本颜色对比度。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 5e8dddf228d5a0654b1ecb2db81269bd30bd4712
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12553048"
---
# <a name="check-text-color-contrast-in-the-default-state-using-the-inspect-tool"></a>使用检查工具检查默认状态下的文本颜色对比度

<!-- Inspect tool: information overlay: Accessibility section: Contrast row -->

使用“ **检查** ”工具检查默认状态下的文本颜色对比度。  **“检查**”工具在网页上的信息覆盖具有包含**对比**度信息的**辅助功能**部分。

<!-- Inspect tool -->
对于包含文本的元素， **检查** 工具的信息覆盖显示以下内容：
*  文本与背景颜色的对比度。
*  具有足够对比度的元素的绿色复选标记图标。
*  没有足够的对比度的元素的黄色警报图标。

在某些情况下，将浏览器设置为浅色主题或深色主题会影响对比度。

例如，在演示页上，边栏导航菜单的蓝色链接具有足够的对比度，但 **“捐赠状态**”部分中的绿色**狗**链接没有足够的对比度。  使用 **“检查** ”工具查看这些元素，如下所示：

1. 在新窗口或选项卡中打开 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击网页中的任意位置，然后选择 **“检查**”。  或者按 `F12`。  DevTools 将在网页旁边打开。

1. 单击“ **检查** (![检查”按钮。](../media/inspect-tool-icon-light-theme.png)) DevTools 左上角的按钮，使图标 (蓝色) 突出显示。

1. 在呈现的网页中，将鼠标悬停在侧栏导航菜单的蓝色 **猫** 链接上。  将显示 **“检查** ”工具的信息覆盖层。  在信息覆盖的 **“辅助功能** ”部分， **对比度** 行上会显示一个绿色复选标记，指示此元素具有足够的文本颜色与背景颜色的对比度。

   ![菜单项具有足够的对比度，如“检查”工具中所示。](../media/a11y-testing-enough-contrast.msft.png)

1. 在呈现的网页中的 **“捐赠状态”** 部分中，将鼠标悬停在 **“狗** ”链接上。  **检查**工具的信息覆盖显示**对比度**行上的橙色感叹号，指示此元素没有足够的文本与背景颜色的对比度。

   ![一个没有足够对比度的元素，如“检查”工具中的警告所示。](../media/a11y-testing-not-enough-contrast.msft.png)


<!-- ====================================================================== -->
## <a name="different-options-to-inspect-text-color-contrast-in-devtools"></a>用于检查 DevTools 中的文本颜色对比度的不同选项

使用以下 DevTools 功能检查文本颜色对比度。

*  使用 **“检查** ”工具 (作为网页) 上的信息覆盖，检查单个页面元素是否有足够的文本颜色对比度。  **“检查**”工具的信息覆盖包含一个具有**对比度**信息行的**辅助功能**部分。  “ **检查** ”工具仅显示当前状态的文本对比度信息。  此方法在当前文章中进行了介绍。

*  当文本和背景颜色的对比度不够时，“ **问题** ”工具会自动报告整个网页的任何颜色对比度问题。  验证 [文本颜色是否具有足够的对比度](test-issues-tool.md#verify-that-text-colors-have-enough-contrast)时介绍了此方法。

*  模拟非默认状态，例如 `hover` 状态。  为此，请单击“**样式**”窗格中的“**切换元素状态**”按钮，其中显示 **“Force 元素状态**”复选框部分。  验证 [所有元素状态的可访问性](test-inspect-states.md)中介绍了此功能。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [验证所有元素状态可访问性](test-inspect-states.md)
*  [使用"检查"工具将鼠标悬停在网页上以检测辅助功能问题](test-inspect-tool.md)
*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
