---
title: 检查动画
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/01/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: 6466c7f0e1f8680a2429b565e8022d152d05d733
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10564143"
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





# <span data-ttu-id="e3dc7-103">检查动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-103">Inspect animations</span></span>   



<span data-ttu-id="e3dc7-104">通过 Microsoft Edge DevTools 动画检查器检查和修改动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-104">Inspect and modify animations with the Microsoft Edge DevTools Animation Inspector.</span></span>  

> ##### <span data-ttu-id="e3dc7-105">图 1</span><span class="sxs-lookup"><span data-stu-id="e3dc7-105">Figure 1</span></span>  
> <span data-ttu-id="e3dc7-106">动画检查器</span><span class="sxs-lookup"><span data-stu-id="e3dc7-106">Animation inspector</span></span>  
> ![动画检查器][ImageAnimationInspector]  

### <span data-ttu-id="e3dc7-108">摘要</span><span class="sxs-lookup"><span data-stu-id="e3dc7-108">Summary</span></span>  

*   <span data-ttu-id="e3dc7-109">通过打开 "动画检查器" 捕获动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-109">Capture animations by opening the Animation Inspector.</span></span>  <span data-ttu-id="e3dc7-110">动画检查器会自动检测动画并将其排序为多个组。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-110">The Animation Inspector automatically detects and sorts animations into groups.</span></span>  
*   <span data-ttu-id="e3dc7-111">通过减速、重放每个动画或查看源代码来检查动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-111">Inspect animations by slowing down each one, replaying each one, or viewing the source code.</span></span>  
*   <span data-ttu-id="e3dc7-112">通过更改计时、延迟、持续时间或关键帧偏移来修改动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-112">Modify animations by changing the timing, delay, duration, or keyframe offsets.</span></span>  

## <span data-ttu-id="e3dc7-113">概述</span><span class="sxs-lookup"><span data-stu-id="e3dc7-113">Overview</span></span>   

<span data-ttu-id="e3dc7-114">Microsoft Edge DevTools 动画检查器有两个主要用途。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-114">The Microsoft Edge DevTools Animation Inspector has two main purposes.</span></span>  

*   <span data-ttu-id="e3dc7-115">检查动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-115">Inspecting animations.</span></span>  <span data-ttu-id="e3dc7-116">你希望减慢、重播或检查动画组的源代码。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-116">You want to slow down, replay, or inspect the source code for an Animation Group.</span></span>  
*   <span data-ttu-id="e3dc7-117">修改动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-117">Modifying animations.</span></span>  <span data-ttu-id="e3dc7-118">要修改动画组的计时、延迟、持续时间或关键帧偏移量。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-118">You want to modify the timing, delay, duration, or keyframe offsets of an Animation Group.</span></span>  <span data-ttu-id="e3dc7-119">当前不支持贝塞尔编辑和关键帧编辑。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-119">Bezier editing and keyframe editing are currently not supported.</span></span>  

<span data-ttu-id="e3dc7-120">动画检查器支持 CSS 动画、CSS 转换和 web 动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-120">The Animation Inspector supports CSS animations, CSS transitions, and web animations.</span></span>  `requestAnimationFrame` <span data-ttu-id="e3dc7-121">当前不支持动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-121">animations are currently not supported.</span></span>  

### <span data-ttu-id="e3dc7-122">什么是动画组？</span><span class="sxs-lookup"><span data-stu-id="e3dc7-122">What is an Animation Group?</span></span>  

<span data-ttu-id="e3dc7-123">动画组是可能相互关联的一组动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-123">An Animation Group is a group of animations that may be related to each other.</span></span>  <span data-ttu-id="e3dc7-124">目前，web 没有组动画的真正概念，因此动画设计器和开发人员必须编写和时间单个动画，以便动画呈现为一个连贯的视觉效果。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-124">Currently, the web has no real concept of a group animation, so motion designers and developers have to compose and time individual animations so that the animations render as one coherent visual effect.</span></span>  <span data-ttu-id="e3dc7-125">动画检查器会预测哪些动画基于开始时间 \ （不包括延迟等）相关。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-125">The Animation Inspector predicts which animations are related based on start time \(excluding delays, and so on\).</span></span>  <span data-ttu-id="e3dc7-126">动画检查器还会并排对动画进行分组。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-126">The Animation Inspector also groups the animations side-by-side.</span></span>  
<span data-ttu-id="e3dc7-127">换句话说，在同一脚本块中同时触发的一组动画将组合在一起。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-127">In other words, a set of animations that are all triggered in the same script block are grouped together.</span></span>  <span data-ttu-id="e3dc7-128">如果动画是异步的，则将其放置在单独的组中。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-128">If an animation is asynchronous, it is placed in a separate group.</span></span>  

## <span data-ttu-id="e3dc7-129">开始行动</span><span class="sxs-lookup"><span data-stu-id="e3dc7-129">Get started</span></span>  

<span data-ttu-id="e3dc7-130">可通过两种方式打开 "动画" 检查器：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-130">There are two ways to open the Animation Inspector:</span></span>  

*   <span data-ttu-id="e3dc7-131">打开 "**自定义和控制" DevTools**菜单</span><span class="sxs-lookup"><span data-stu-id="e3dc7-131">Open the **Customize and Control DevTools** menu</span></span>  
    1.  <span data-ttu-id="e3dc7-132">导航到 "**更多工具**" 子菜单。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-132">Navigate to the **More tools** sub-menu.</span></span>  
    1.  <span data-ttu-id="e3dc7-133">选择 "**动画**"：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-133">Select **Animations**:</span></span>  
        
        > ##### <span data-ttu-id="e3dc7-134">图 2</span><span class="sxs-lookup"><span data-stu-id="e3dc7-134">Figure 2</span></span>  
        > <span data-ttu-id="e3dc7-135">通过主菜单的动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-135">Animations via Main Menu</span></span>  
        > ![通过主菜单的动画][ImageAnimationsViaMainMenu]  
        
*   <span data-ttu-id="e3dc7-137">打开 "**命令" 菜单**</span><span class="sxs-lookup"><span data-stu-id="e3dc7-137">Open the **Command Menu**</span></span>  
    1.  <span data-ttu-id="e3dc7-138">键入 `Drawer: Show Animations`。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-138">Type `Drawer: Show Animations`.</span></span>  

<span data-ttu-id="e3dc7-139">"动画" 检查器将在控制台抽屉旁边的选项卡中打开。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-139">The Animation Inspector opens up as a tab next to the Console Drawer.</span></span>  <span data-ttu-id="e3dc7-140">由于动画检查器是一个抽屉选项卡，因此您可以使用任何 DevTools 面板中的动画检查器。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-140">Since the Animation Inspector is a Drawer tab, you may use the Animation Inspector from any DevTools panel.</span></span>  

> ##### <span data-ttu-id="e3dc7-141">图 3</span><span class="sxs-lookup"><span data-stu-id="e3dc7-141">Figure 3</span></span>  
> <span data-ttu-id="e3dc7-142">清空动画检查器</span><span class="sxs-lookup"><span data-stu-id="e3dc7-142">Empty Animation Inspector</span></span>  
> ![清空动画检查器][ImageEmptyAnimationInspector]  

<span data-ttu-id="e3dc7-144">动画检查器分为四个主要部分： "（" 或 "窗格 \"）。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-144">The Animation Inspector is grouped into four main sections \(or panes\).</span></span>  <span data-ttu-id="e3dc7-145">本指南按如下方式引用每个窗格：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-145">This guide refers to each pane as follows:</span></span>  

| | <span data-ttu-id="e3dc7-146">窗格</span><span class="sxs-lookup"><span data-stu-id="e3dc7-146">Pane</span></span> | <span data-ttu-id="e3dc7-147">描述</span><span class="sxs-lookup"><span data-stu-id="e3dc7-147">Description</span></span> |  
| --- |:--- |:--- |  
| <span data-ttu-id="e3dc7-148">raid-1</span><span class="sxs-lookup"><span data-stu-id="e3dc7-148">1</span></span> | **<span data-ttu-id="e3dc7-149">控件</span><span class="sxs-lookup"><span data-stu-id="e3dc7-149">Controls</span></span>** | <span data-ttu-id="e3dc7-150">你可以从此处清除当前捕获的所有动画组，或更改当前所选动画组的速度。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-150">From here you may clear all currently captured Animation Groups, or change the speed of the currently selected Animation Group.</span></span> |  
| <span data-ttu-id="e3dc7-151">ppls-2</span><span class="sxs-lookup"><span data-stu-id="e3dc7-151">2</span></span> | **<span data-ttu-id="e3dc7-152">概述</span><span class="sxs-lookup"><span data-stu-id="e3dc7-152">Overview</span></span>** | <span data-ttu-id="e3dc7-153">在此处选择一个动画组以在 "**详细信息**" 窗格中检查和修改它。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-153">Select an Animation Group here to inspect and modify it in the **Details** pane.</span></span> |  
| <span data-ttu-id="e3dc7-154">三维空间</span><span class="sxs-lookup"><span data-stu-id="e3dc7-154">3</span></span> | **<span data-ttu-id="e3dc7-155">时间线</span><span class="sxs-lookup"><span data-stu-id="e3dc7-155">Timeline</span></span>** | <span data-ttu-id="e3dc7-156">在此处暂停和启动动画，或跳转到动画中的特定点。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-156">Pause and start an animation from here, or jump to a specific point in the animation.</span></span> |  
| <span data-ttu-id="e3dc7-157">第</span><span class="sxs-lookup"><span data-stu-id="e3dc7-157">4</span></span> | **<span data-ttu-id="e3dc7-158">详细信息</span><span class="sxs-lookup"><span data-stu-id="e3dc7-158">Details</span></span>** | <span data-ttu-id="e3dc7-159">检查和修改当前所选的动画组。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-159">Inspect and modify the currently selected Animation Group.</span></span> |  

> ##### <span data-ttu-id="e3dc7-160">图 4</span><span class="sxs-lookup"><span data-stu-id="e3dc7-160">Figure 4</span></span>  
> <span data-ttu-id="e3dc7-161">带批注的动画检查器</span><span class="sxs-lookup"><span data-stu-id="e3dc7-161">Annotated Animation Inspector</span></span>  
> ![带批注的动画检查器][ImageAnnotatedAnimationInspector]  

<span data-ttu-id="e3dc7-163">若要捕获动画，只需在动画检查器打开的情况下执行触发动画的交互。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-163">To capture an animation, just perform the interaction that triggers the animation while the Animation Inspector is open.</span></span>  <span data-ttu-id="e3dc7-164">如果动画是在页面加载时触发的，请使用动画检查器打开来重新加载页面以检测动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-164">If an animation is triggered on page load, reload the page with the Animation Inspector open to detect the animation.</span></span>  

<!--  old link: <video src="animations/capture-animations.mp4" autoplay loop muted controls></video>  -->  

<!--  import the video to ACOM using https://review.docs.microsoft.com/en-us/help/contribute/contribute-video-publish?branch=master  -->  

<!--  > [!VIDEO animations/capture-animations.mp4]  -->  

## <span data-ttu-id="e3dc7-165">检查动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-165">Inspect animations</span></span>   

<span data-ttu-id="e3dc7-166">捕获动画后，有几种方法可以重播它：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-166">After you capture an animation, there are a few ways to replay it:</span></span>  

*   <span data-ttu-id="e3dc7-167">将鼠标悬停在 "**概述**" 窗格的缩略图上以查看它的预览。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-167">Hover over the thumbnail in the **Overview** pane to view a preview of it.</span></span>  
*   <span data-ttu-id="e3dc7-168">从 "**概述**" 窗格中选择 "动画" 组 \ （以便它显示在 "**详细信息**" 窗格 \）中，然后按 "**重播** ![ 重播" 图标 ][ImageReplayButtonIcon] 图标。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-168">Select the Animation Group from the **Overview** pane \(so that it is displayed in the **Details** pane\) and press the **replay** ![replay icon][ImageReplayButtonIcon] icon.</span></span>  <span data-ttu-id="e3dc7-169">将在视区中重播动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-169">The animation is replayed in the viewport.</span></span>  <span data-ttu-id="e3dc7-170">单击**动画速度** ![ 动画速度图标 ][ImageAnimationSpeedButtonsIcon] 图标以更改当前所选动画组的预览速度。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-170">Click on the **animation speed** ![animation speed icons][ImageAnimationSpeedButtonsIcon] icons to change the preview speed of the currently selected Animation Group.</span></span>  <span data-ttu-id="e3dc7-171">您可以使用红色垂直条更改您的当前位置。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-171">You may use the red vertical bar to change your current position.</span></span>  
*   <span data-ttu-id="e3dc7-172">单击并拖动红色垂直条以擦除视区动画。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-172">Click and drag the red vertical bar to scrub the viewport animation.</span></span>  

### <span data-ttu-id="e3dc7-173">查看动画详细信息</span><span class="sxs-lookup"><span data-stu-id="e3dc7-173">View animation details</span></span>  

<span data-ttu-id="e3dc7-174">捕获动画组后，从 "**概述**" 窗格中单击它以查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-174">After you capture an Animation Group, click on it from the **Overview** pane to view the details.</span></span>  <span data-ttu-id="e3dc7-175">在 "**详细信息**" 窗格中，每个单独的动画都分配有一行。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-175">In the **Details** pane each individual animation is assigned the a row.</span></span>  

> ##### <span data-ttu-id="e3dc7-176">图 5</span><span class="sxs-lookup"><span data-stu-id="e3dc7-176">Figure 5</span></span>  
> <span data-ttu-id="e3dc7-177">动画组详细信息</span><span class="sxs-lookup"><span data-stu-id="e3dc7-177">Animation Group details</span></span>  
> ![动画组详细信息][ImageAnimationGroupDetails]  

<span data-ttu-id="e3dc7-179">将鼠标悬停在某个动画上，将其在视区中突出显示。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-179">Hover over an animation to highlight it in the viewport.</span></span>  <span data-ttu-id="e3dc7-180">单击动画以在 "**元素**" 面板中选择它。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-180">Click on the animation to select it in the **Elements** panel.</span></span>  

> ##### <span data-ttu-id="e3dc7-181">图 6</span><span class="sxs-lookup"><span data-stu-id="e3dc7-181">Figure 6</span></span>  
> <span data-ttu-id="e3dc7-182">将鼠标悬停在动画上以在视区中突出显示</span><span class="sxs-lookup"><span data-stu-id="e3dc7-182">Hover over the animation to highlight it in viewport</span></span>  
> ![将鼠标悬停在动画上以在视区中突出显示][ImageHoverOverAnimationHighlightViewport]  

<span data-ttu-id="e3dc7-184">动画最左边、更暗的部分是定义。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-184">The leftmost, darker section of an animation is the definition.</span></span>  <span data-ttu-id="e3dc7-185">右侧、更淡出的部分表示迭代。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-185">The right, more faded section represents iterations.</span></span>  <span data-ttu-id="e3dc7-186">例如，在[图 7](#figure-7)中，第二部分和第三部分表示第一节的迭代。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-186">For example, in [Figure 7](#figure-7), sections two and three represent iterations of section one.</span></span>  

> ##### <span data-ttu-id="e3dc7-187">图 7</span><span class="sxs-lookup"><span data-stu-id="e3dc7-187">Figure 7</span></span>  
> <span data-ttu-id="e3dc7-188">动画迭代图表</span><span class="sxs-lookup"><span data-stu-id="e3dc7-188">Diagram of animation iterations</span></span>  
> ![动画迭代图表][ImageDiagramAnimationIterations]  

<span data-ttu-id="e3dc7-190">如果两个元素应用了相同的动画，则动画检查器会为元素分配相同的颜色。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-190">If two elements have the same animation applied, the Animation Inspector assigns the same color to the elements.</span></span>  <span data-ttu-id="e3dc7-191">颜色是随机的，没有任何意义。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-191">The color is random and has no significance.</span></span>  <span data-ttu-id="e3dc7-192">例如，[图 8](#figure-8)中的两个元素 `div.cwccw.earlier` 和 `div.cwccw.later` 应用了相同的动画 \ （ `spinrightleft` \），就像处理 `div.ccwcw.earlier` 和 `div.ccwcw.later` 元素一样。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-192">For example, in [Figure 8](#figure-8) the two elements `div.cwccw.earlier` and `div.cwccw.later` have the same animation \(`spinrightleft`\) applied, as do the `div.ccwcw.earlier` and `div.ccwcw.later` elements.</span></span>  

> ##### <span data-ttu-id="e3dc7-193">图 8</span><span class="sxs-lookup"><span data-stu-id="e3dc7-193">Figure 8</span></span>  
> <span data-ttu-id="e3dc7-194">颜色编码的动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-194">Color-coded animations</span></span>  
> ![颜色编码的动画][ImageColorCodedAnimations]  

## <span data-ttu-id="e3dc7-196">修改动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-196">Modify animations</span></span>   

<span data-ttu-id="e3dc7-197">可以通过以下三种方式使用动画检查器修改动画：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-197">There are three ways you are able to modify an animation with the Animation Inspector:</span></span>  

*   <span data-ttu-id="e3dc7-198">动画持续时间。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-198">Animation duration.</span></span>  
*   <span data-ttu-id="e3dc7-199">关键帧计时。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-199">Keyframe timings.</span></span>  
*   <span data-ttu-id="e3dc7-200">开始时间延迟。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-200">Start time delay.</span></span>  

<span data-ttu-id="e3dc7-201">本部分假设[图 9](#figure-9)表示原始动画：</span><span class="sxs-lookup"><span data-stu-id="e3dc7-201">For this section suppose that [Figure 9](#figure-9) represents the original animation:</span></span>  

> ##### <span data-ttu-id="e3dc7-202">图 9</span><span class="sxs-lookup"><span data-stu-id="e3dc7-202">Figure 9</span></span>  
> <span data-ttu-id="e3dc7-203">修改前的原始动画</span><span class="sxs-lookup"><span data-stu-id="e3dc7-203">Original animation before modification</span></span>  
> ![修改前的原始动画][ImageOriginalAnimationBeforeModification]  

<span data-ttu-id="e3dc7-205">若要更改动画的持续时间，请单击并拖动第一个或最后一个圆。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-205">To change the duration of an animation, click and drag the first or last circle.</span></span>  

> ##### <span data-ttu-id="e3dc7-206">图 10</span><span class="sxs-lookup"><span data-stu-id="e3dc7-206">Figure 10</span></span>  
> <span data-ttu-id="e3dc7-207">已修改工期</span><span class="sxs-lookup"><span data-stu-id="e3dc7-207">Modified duration</span></span>  
> ![已修改工期][ImageModifiedDuration]  

<span data-ttu-id="e3dc7-209">如果动画定义了任何关键帧规则，则这些规则表示为白色内圆圈。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-209">If the animation defines any keyframe rules, then these are represented as white inner circles.</span></span>  <span data-ttu-id="e3dc7-210">单击并拖动其中一个以更改关键帧的计时。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-210">Click and drag one of these to change the timing of the keyframe.</span></span>  

> ##### <span data-ttu-id="e3dc7-211">图 11</span><span class="sxs-lookup"><span data-stu-id="e3dc7-211">Figure 11</span></span>  
> <span data-ttu-id="e3dc7-212">修改的关键帧</span><span class="sxs-lookup"><span data-stu-id="e3dc7-212">Modified keyframe</span></span>  
> ![修改的关键帧][ImageModifiedKeyframe]  

<span data-ttu-id="e3dc7-214">若要向动画添加延迟，请单击并将其拖动到除圆圈外的任意位置。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-214">To add a delay to an animation, click and drag it anywhere except the circles.</span></span>  

> ##### <span data-ttu-id="e3dc7-215">图 12</span><span class="sxs-lookup"><span data-stu-id="e3dc7-215">Figure 12</span></span>  
> <span data-ttu-id="e3dc7-216">修改后的延迟</span><span class="sxs-lookup"><span data-stu-id="e3dc7-216">Modified delay</span></span>  
> ![修改后的延迟][ImageModifiedDelay]  

<!--   -->  



<!-- image links -->  

[ImageAnimationSpeedButtonsIcon]: /microsoft-edge/devtools-guide-chromium/media/animation-speed-buttons-icon.msft.png  
[ImageReplayButtonIcon]: /microsoft-edge/devtools-guide-chromium/media/replay-button-icon.msft.png  

[ImageAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-completed.msft.png "图1：动画检查器"  
[ImageAnimationsViaMainMenu]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-more-tools-animations.msft.png "图2：通过主菜单的动画"  
[ImageEmptyAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations.msft.png "图3：清空动画检查器"  
[ImageAnnotatedAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png "图4：带批注的动画检查器"  
[ImageAnimationGroupDetails]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png "图5：动画组详细信息"  
[ImageHoverOverAnimationHighlightViewport]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png "图6：将鼠标悬停在动画上以在视区中突出显示"  
[ImageDiagramAnimationIterations]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-display-animations-highlight.msft.png "图7：动画迭代图表"  
[ImageColorCodedAnimations]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-display-animations.msft.png "图8：颜色编码的动画"  
[ImageOriginalAnimationBeforeModification]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations.msft.png "图9：修改前的原始动画"  
[ImageModifiedDuration]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png "图10：修改的工期"  
[ImageModifiedKeyframe]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png "图11：修改的关键帧"  
[ImageModifiedDelay]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png "图12：修改后的延迟"  

<!-- links -->  

> [!NOTE]
> <span data-ttu-id="e3dc7-230">此页面的某些部分是基于[由 Google][GoogleSitePolicies]创建和共享的工作的修改，并根据 "[创造性 Commons 归属4.0 国际许可证][CCA4IL]" 中所述的条款使用。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-230">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="e3dc7-231">原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/animations)，由[Kayce Basques][KayceBasques] \ （技术作者、Chrome DevTools \ & Lighthouse \）创作。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-231">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/animations) and is authored by [Kayce Basques][KayceBasques] \(Technical Writer, Chrome DevTools \& Lighthouse\).</span></span>  

[![创造性 Commons 许可证][CCby4Image]][CCA4IL]  
<span data-ttu-id="e3dc7-233">此作品通过 [Creative Commons Attribution 4.0 国际许可证][CCA4IL]获得许可。</span><span class="sxs-lookup"><span data-stu-id="e3dc7-233">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  