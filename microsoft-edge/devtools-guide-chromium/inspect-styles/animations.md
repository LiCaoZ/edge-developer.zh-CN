---
title: 检查和修改 CSS 动画效果
description: 使用动画工具中的动画检查器检查和修改 CSS 动画效果。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/11/2021
ms.openlocfilehash: a937f5d957c4d827857cb3008f07eb53a158e489
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431709"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="inspect-and-modify-css-animation-effects"></a>检查和修改 CSS 动画效果
<!-- orig title: # Inspect animations -->

使用动画工具中的动画检查器检查和**** 修改 CSS **动画**效果。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-completed.msft.png" alt-text="动画工具。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-completed.msft.png":::

### <a name="summary"></a>摘要

*  通过打开动画工具 **捕获** 动画。  **动画工具**自动检测动画并按组排序。

*  通过减慢动画的速度、重播每个动画或查看源代码来检查动画。

*  通过更改计时、延迟、持续时间或关键帧偏移来修改动画。


<!-- ====================================================================== -->
## <a name="overview"></a>概述

**动画工具**有两个主要用途：

*  检查动画。  你可以减慢、重播或检查动画组的源代码。

*  修改动画。  你可以修改动画组的计时、延迟、持续时间或关键帧偏移。  贝塞尔编辑和关键帧编辑当前不受支持。

动画检查器支持 CSS 动画、CSS 过渡和 Web 动画。  `requestAnimationFrame` 动画当前不受支持。

### <a name="whats-an-animation-group"></a>什么是动画组？

动画 _组_ 是一组相互相关的动画。  目前，Web 没有组动画的实际概念，因此动画设计人员和开发人员必须撰写各个动画并设置动画时间，以便动画呈现为一致的视觉效果。  动画检查器根据开始时间以及排除延迟 (等来预测与哪些动画) 。  动画检查器还会将动画并排分组。

换句话说，在同一脚本块中触发的一组动画会被组合在一起。  如果动画是异步动画，它会被放置在单独的组中。


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

若要打开动画检查器，请使用以下任一方法，在 DevTools 中：

*  从主**工具栏或**"箱"**** 上：单击"****![更多工具 (更多工具"图标](../media/more-tools-icon-light-theme.png)。) 按钮，然后选择"**动画"**。

   :::image type="content" source="../media/inspect-styles-elements-styles-more-tools-animations.msft.png" alt-text="使用主菜单的动画。" lightbox="../media/inspect-styles-elements-styles-more-tools-animations.msft.png":::

*  从"**自定义"** 菜单中：单击"自定义和控制 **DevTools** ![ (自定义"图标****](../media/customize-devtools-icon-light-theme.png)。) 菜单按钮，指向"更多工具"子菜单，然后选择"**动画"**。

*  **** 从命令**菜单中：当** DevTools `Shift``P`+`Ctrl`+具有焦点时，按 Windows/Linux`P``Shift`++`Command` 或 macOS 打开命令菜单，开始键入 `animations`，然后选择"箱： 显示**动画"**。

默认情况下， **动画工具** 在控制台工具旁边的 **"箱**" **中** 打开。  通过使用"**箱"上的"** 动画"**** 工具，可以像使用主工具栏上的另一个工具一样使用它。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations.msft.png" alt-text="空动画检查器。" lightbox="../media/inspect-styles-elements-styles-drawer-animations.msft.png":::

动画检查器分为四个主要部分 (或窗格) 。  本指南按以下方式指代每个窗格：

| 索引 | 窗格 | 描述 |
|:--- |:--- |:--- |
| 1 | **控件** | 你可以在此处清除所有当前捕获的动画组，或更改当前选定的动画组的速度。 |
| 2 | **概述** | 选择此处的动画组以检查和修改详细信息 **窗格中的** 动画组。 |
| 3 | **时间线** | 从此处暂停并启动动画，或跳转到动画中的特定点。 |
| 4 | **详细信息** | 检查和修改当前选定的动画组。 |

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png" alt-text="批注动画检查器。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png":::

若要捕获动画，只需执行在动画检查器打开时触发动画的交互。  如果在页面加载时触发了动画，请刷新页面，同时打开动画检查器以检测动画。

<!--  old link: <video src="animations/capture-animations.mp4" autoplay loop muted controls></video>  -->

<!--  import the video to ACOM using https://review.docs.microsoft.com/en-us/help/contribute/contribute-video-publish?branch=master  -->

<!--  > [!VIDEO animations/capture-animations.mp4]  -->


<!-- ====================================================================== -->
## <a name="inspect-animations"></a>检查动画

捕获动画后，有多种方式可以重播它：

*  将鼠标悬停在“**概述**”窗格中的缩略图上，查看缩略图的预览。
*  Select the Animation Group from the **Overview** pane (so that it is displayed in the **Details** pane) ， and then click the **replay** (![replay icon.](../media/replay-button-icon.msft.png)) icon.  动画会在视区中重播。  单击动画**速度 (**![动画速度图标](../media/animation-speed-buttons-icon.msft.png)。) 图标可更改当前选定的动画组的预览速度。  可以使用红色竖线更改当前位置。
*  单击并拖动红色竖线以清理视区动画。

### <a name="view-animation-details"></a>查看动画详细信息

捕获动画组后，从"概述"窗格中 **单击它以查看** 详细信息。  在" **详细信息** "窗格中，将每个单独的动画分配给一行。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png" alt-text="动画组详细信息。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png":::

将鼠标悬停在动画上以在视区中突出显示它。  单击动画以在"元素"工具 **中选择** 它。

:::image type="content" source="../media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png" alt-text="将鼠标悬停在动画上以在视口中突出显示它。" lightbox="../media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png":::

动画最左侧较暗的部分就是其定义。  右侧更淡出的部分表示迭代。  例如，在下图中，第二节和第三节表示第一节的迭代：

:::image type="content" source="../media/inspect-styles-glitch-display-animations-highlight.msft.png" alt-text="动画迭代关系图。" lightbox="../media/inspect-styles-glitch-display-animations-highlight.msft.png":::

如果两个元素应用了相同的动画，则动画检查器会为元素分配相同的颜色。  颜色是随机的，没有意义。  例如，在下图中`div.cwccw.earlier` `div.ccwcw.earlier` `div.cwccw.later` `spinrightleft` `div.ccwcw.later`，这两个元素应用了相同的动画 () 和 元素一样。

:::image type="content" source="../media/inspect-styles-glitch-display-animations.msft.png" alt-text="颜色编码的动画。" lightbox="../media/inspect-styles-glitch-display-animations.msft.png":::


<!-- ====================================================================== -->
## <a name="modify-animations"></a>修改动画

有三种方法可以使用动画检查器修改动画：

*  动画持续时间。
*  关键帧计时。
*  开始时间延迟。

对于此部分，假设下面的屏幕截图表示原始动画：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations.msft.png" alt-text="修改前的原始动画。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations.msft.png":::

若要更改动画的持续时间，请单击并拖动第一个或最后一个圆。

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png" alt-text="修改的持续时间。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png":::

如果动画定义任何关键帧规则，则这些规则表示为白色填充的内部圆。  单击并拖动一个白色填充的内部圆以更改关键帧的计时：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png" alt-text="修改后的关键帧。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png":::

若要向动画添加延迟，请单击除圆圈以外的任何位置的动画，然后拖动：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png" alt-text="修改后的延迟。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/animations)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
