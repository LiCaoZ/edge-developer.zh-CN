---
title: 检查和修改 CSS 动画效果
description: 使用动画工具中的动画检查器检查和修改 CSS 动画效果。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/11/2021
ms.openlocfilehash: 7318aec723f2ac663dcdac359f76718eecfd9794
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12514704"
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

使用动画工具中的 **动画检查器** 检查和修改 CSS **动画** 效果。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-completed.msft.png" alt-text="动画工具。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-completed.msft.png":::

### <a name="summary"></a>摘要

*  通过打开动画工具捕获 **动画** 。  **动画**工具会自动检测动画并将其排序为组。

*  通过减慢动画的速度、重播每个动画或查看源代码来检查动画。

*  通过更改计时、延迟、持续时间或关键帧偏移来修改动画。


<!-- ====================================================================== -->
## <a name="overview"></a>概述

**动画**工具有两个主要用途：

*  检查动画。  可以减速、重播或检查动画组的源代码。

*  修改动画。  你可以修改动画组的计时、延迟、持续时间或关键帧偏移。  贝塞尔编辑和关键帧编辑当前不受支持。

动画检查器支持 CSS 动画、CSS 过渡和 Web 动画。  `requestAnimationFrame` 动画当前不受支持。

### <a name="whats-an-animation-group"></a>什么是动画组？

_动画组_是一组可能彼此相关的动画。  目前，Web 没有组动画的实际概念，因此动画设计人员和开发人员必须撰写各个动画并设置动画时间，以便动画呈现为一致的视觉效果。  动画检查器根据开始时间 (排除延迟等) 预测哪些动画相关。  动画检查器还会将动画并排分组。

换句话说，在同一脚本块中触发的一组动画会被组合在一起。  如果动画是异步动画，它会被放置在单独的组中。


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

若要打开动画检查器，请在 DevTools 中使用以下任何方法：

*  在 **主工具栏** 或 **抽屉**上：单击 **“更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮，然后选择 **“动画**”。

   :::image type="content" source="../media/inspect-styles-elements-styles-more-tools-animations.msft.png" alt-text="使用主菜单的动画。" lightbox="../media/inspect-styles-elements-styles-more-tools-animations.msft.png":::

*  在 **“自定义”** 菜单中：单击 **“自定义并控制 DevTools** ” (![“自定义”图标。](../media/customize-devtools-icon-light-theme.png)) 菜单按钮，指向 **“更多工具** ”子菜单，然后选择 **“动画**”。

*  从**命令菜单**：当 DevTools 具有焦点时，按`Shift``P`++`Ctrl`Windows/Linux 或`P`++`Command``Shift`macOS打开**命令菜单**，开始键入`animations`，然后选择 **“抽屉：显示动画**”。

默认情况下，“**动画**”工具会在“**控制台**”工具旁边的**抽屉**中打开。  通过在**抽屉**上使用**动画**工具，可以在主工具栏上使用其他工具的同时使用它。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations.msft.png" alt-text="空动画检查器。" lightbox="../media/inspect-styles-elements-styles-drawer-animations.msft.png":::

动画检查器分为四个主要部分 (或窗格) 。  本指南按以下方式指代每个窗格：

| 索引 | 窗格 | 描述 |
|:--- |:--- |:--- |
| 1 | **控件** | 可在此处清除所有当前捕获的动画组，或更改当前所选动画组的速度。 |
| 2 | **概述** | 在此处选择动画组以在 **“详细信息** ”窗格中检查和修改它。 |
| 3 | **时间线** | 从此处暂停并启动动画，或跳转到动画中的特定点。 |
| 4 | **详细信息** | 检查和修改当前选定的动画组。 |

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png" alt-text="带批注的动画检查器。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png":::

若要捕获动画，只需执行在动画检查器打开时触发动画的交互。  如果在页面加载时触发了动画，请刷新页面，同时打开动画检查器以检测动画。

<!--  old link: <video src="animations/capture-animations.mp4" autoplay loop muted controls></video>  -->

<!--  import the video to ACOM using https://review.docs.microsoft.com/help/contribute/contribute-video-publish?branch=master  -->

<!--  > [!VIDEO animations/capture-animations.mp4]  -->


<!-- ====================================================================== -->
## <a name="inspect-animations"></a>检查动画

捕获动画后，有多种方式可以重播它：

*  将鼠标悬停在“**概述**”窗格中的缩略图上，查看缩略图的预览。
*  从“ **概述** ”窗格 (中选择动画组，以便在“ **详细信息** ”窗格) 中显示，然后单击 **重播** (![重播图标。](../media/replay-button-icon.msft.png)) 图标。  动画会在视区中重播。  单击 **动画速度** (![动画速度图标。](../media/animation-speed-buttons-icon.msft.png)) 图标可更改当前所选动画组的预览速度。  可以使用红色垂直条更改当前位置。
*  单击并拖动红色垂直条以擦洗视区动画。

### <a name="view-animation-details"></a>查看动画详细信息

捕获动画组后，从“ **概述** ”窗格单击它以查看详细信息。  在 **“详细信息”** 窗格中，每个动画都分配给一行。

:::image type="content" source="../media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png" alt-text="动画组详细信息。" lightbox="../media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png":::

将鼠标悬停在动画上以在视区中突出显示它。  单击动画以在 **“元素** ”工具中选择它。

:::image type="content" source="../media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png" alt-text="将鼠标悬停在动画上以在视区中突出显示它。" lightbox="../media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png":::

动画最左侧较深的部分是其定义。  右侧更淡出的部分表示迭代。  例如，在下图中，第二节和第三节表示第一节的迭代：

:::image type="content" source="../media/inspect-styles-glitch-display-animations-highlight.msft.png" alt-text="动画迭代图。" lightbox="../media/inspect-styles-glitch-display-animations-highlight.msft.png":::

如果两个元素应用了相同的动画，动画检查器会为元素分配相同的颜色。  颜色是随机的，没有意义。  例如，在下图中，两个元素`div.cwccw.earlier`的动画 (`spinrightleft` 应用) `div.ccwcw.later` `div.ccwcw.earlier` `div.cwccw.later`和元素相同。

:::image type="content" source="../media/inspect-styles-glitch-display-animations.msft.png" alt-text="颜色编码动画。" lightbox="../media/inspect-styles-glitch-display-animations.msft.png":::


<!-- ====================================================================== -->
## <a name="modify-animations"></a>修改动画

可以通过三种方式使用动画检查器修改动画：

*  动画持续时间。
*  关键帧计时。
*  开始时间延迟。

对于本部分，假设以下屏幕截图表示原始动画：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations.msft.png" alt-text="修改前的原始动画。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations.msft.png":::

若要更改动画的持续时间，请单击并拖动第一个或最后一个圆圈。

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png" alt-text="修改的持续时间。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png":::

如果动画定义了任何关键帧规则，则这些规则表示为填充白色的内圆。  单击并拖动一个填充白色的内圈以更改关键帧的计时：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png" alt-text="修改了关键帧。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png":::

若要向动画添加延迟，请单击圆圈以外的任意位置的动画，然后将其拖动：

:::image type="content" source="../media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png" alt-text="修改后的延迟。" lightbox="../media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/animations)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
