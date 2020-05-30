---
title: 使用 Microsoft Edge DevTools 中的 "覆盖范围" 选项卡查找未使用的 JavaScript 和 CSS 代码
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/25/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: ebb8ae15a6888ce2227ec1dc18f307b03ddf9319
ms.sourcegitcommit: 5cdc1626d5581b79c0f2ac4ea62e7f1974ebfa57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "10601717"
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





# <span data-ttu-id="f3ebf-103">使用 Microsoft Edge DevTools 中的 "覆盖范围" 选项卡查找未使用的 JavaScript 和 CSS 代码</span><span class="sxs-lookup"><span data-stu-id="f3ebf-103">Find Unused JavaScript And CSS Code With The Coverage Tab In Microsoft Edge DevTools</span></span>   



<span data-ttu-id="f3ebf-104">Microsoft Edge DevTools 中的 "覆盖范围" 选项卡可帮助你查找未使用的 JavaScript 和 CSS 代码。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-104">The Coverage tab in Microsoft Edge DevTools helps you find unused JavaScript and CSS code.</span></span>  <span data-ttu-id="f3ebf-105">删除未使用的代码可能会加速你的页面加载和保存移动用户手机网络数据。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-105">Removing unused code may speed up your page load and save your mobile users cellular data.</span></span>  

> ##### <span data-ttu-id="f3ebf-106">图 1</span><span class="sxs-lookup"><span data-stu-id="f3ebf-106">Figure 1</span></span>  
> <span data-ttu-id="f3ebf-107">分析代码覆盖率</span><span class="sxs-lookup"><span data-stu-id="f3ebf-107">Analyzing code coverage</span></span>  
> ![分析代码覆盖率][ImageExample]  

> [!WARNING]
> <span data-ttu-id="f3ebf-109">查找未使用的代码相对简单。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-109">Finding unused code is relatively easy.</span></span>  <span data-ttu-id="f3ebf-110">但要重构基本代码，以便每个页面仅提供它所需的 JavaScript 和 CSS。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-110">But refactoring a codebase so that each page only ships the JavaScript and CSS that it needs may be difficult.</span></span>  <span data-ttu-id="f3ebf-111">本指南不介绍如何重构基本代码以避免未使用的代码，因为这些 refactors 高度依赖于你的技术堆栈。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-111">This guide does not cover how to refactor a codebase to avoid unused code because these refactors depend highly on your technology stack.</span></span>  

## <span data-ttu-id="f3ebf-112">概述</span><span class="sxs-lookup"><span data-stu-id="f3ebf-112">Overview</span></span>   

<span data-ttu-id="f3ebf-113">装运未使用的 JavaScript 或 CSS 是 web 开发中的常见问题。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-113">Shipping unused JavaScript or CSS is a common problem in web development.</span></span>  <span data-ttu-id="f3ebf-114">例如，假设您想要在您的页面上使用 "[引导" 按钮组件][BootstrapButtons]。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-114">For example, suppose that you want to use [Bootstrap button component][BootstrapButtons] on your page.</span></span>  <span data-ttu-id="f3ebf-115">若要使用按钮组件，需要在 HTML 中添加指向引导样式表的链接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3ebf-115">To use the button component you need to add a link to the Bootstrap stylesheet in your HTML, like this:</span></span>  

```html
...
<head>
    ...
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    ...
</head>
...
```  

<span data-ttu-id="f3ebf-116">此样式表不仅仅包含按钮组件的代码。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-116">This stylesheet does not just include the code for the button component.</span></span>  <span data-ttu-id="f3ebf-117">它包含**所有**引导组件的 CSS。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-117">It contains the CSS for **all** of the Bootstrap components.</span></span>  <span data-ttu-id="f3ebf-118">但您没有使用任何其他的引导组件。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-118">But you are not using any of the other Bootstrap components.</span></span>  <span data-ttu-id="f3ebf-119">因此，你的页面将下载一组不需要的 CSS。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-119">So your page is downloading a bunch of CSS that it does not need.</span></span>  <span data-ttu-id="f3ebf-120">此额外的 CSS 是一个问题，原因如下。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-120">This extra CSS is a problem for the following reasons.</span></span>  

*   <span data-ttu-id="f3ebf-121">额外的代码将减慢页面负载。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-121">The extra code slows down your page load.</span></span>  <!--See [Render-Blocking CSS][render].  -->  
*   <span data-ttu-id="f3ebf-122">如果用户在移动设备上访问页面，则额外的代码将使用其手机网络数据。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-122">If a user accesses the page on a mobile device, the extra code uses up their cellular data.</span></span>  

<!--[render]: /web/fundamentals/performance/critical-rendering-path/render-blocking-css  -->  

## <span data-ttu-id="f3ebf-123">打开 "覆盖范围" 选项卡</span><span class="sxs-lookup"><span data-stu-id="f3ebf-123">Open the Coverage tab</span></span>   

1.  <span data-ttu-id="f3ebf-124">[打开 "命令" 菜单][DevToolsCommandMenu]。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-124">[Open the Command Menu][DevToolsCommandMenu].</span></span>  
1.  <span data-ttu-id="f3ebf-125">开始键入 `coverage` ，选择 "**显示覆盖率**" 命令，然后按 `Enter` 运行命令。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-125">Start typing `coverage`, select the **Show Coverage** command, and then press `Enter` to run the command.</span></span>  <span data-ttu-id="f3ebf-126">"**覆盖范围**" 选项卡将在**抽屉**中打开。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-126">The **Coverage** tab opens in the **Drawer**.</span></span>  

    > ##### <span data-ttu-id="f3ebf-127">图 2</span><span class="sxs-lookup"><span data-stu-id="f3ebf-127">Figure 2</span></span>  
    > <span data-ttu-id="f3ebf-128">"**覆盖范围**" 选项卡</span><span class="sxs-lookup"><span data-stu-id="f3ebf-128">The **Coverage** tab</span></span>  
    > !["覆盖范围" 选项卡][ImageCoverage]  

## <span data-ttu-id="f3ebf-130">记录代码覆盖率</span><span class="sxs-lookup"><span data-stu-id="f3ebf-130">Record code coverage</span></span>   

1.  <span data-ttu-id="f3ebf-131">单击 "**覆盖范围**" 选项卡中的以下按钮之一：</span><span class="sxs-lookup"><span data-stu-id="f3ebf-131">Click one of the following buttons in the **Coverage** tab:</span></span>  
    *   <span data-ttu-id="f3ebf-132">如果要查看加载页面所需的代码，请单击 "**开始检测覆盖率" 并重新加载页面**" ![ 开始检测覆盖率" 和 "重新加载页面" ][ImageReloadIcon] 。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-132">Click **Start Instrumenting Coverage And Reload Page** ![Start Instrumenting Coverage And Reload Page][ImageReloadIcon] if you want to see what code is needed to load the page.</span></span>  
    *   <span data-ttu-id="f3ebf-133">**Instrument Coverage** ![ ][ImageRecordIcon] 如果想要查看在与页面交互之后使用的代码，请单击 "检测覆盖率检测覆盖率"。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-133">Click **Instrument Coverage** ![Instrument Coverage][ImageRecordIcon] if you want to see what code is used after interacting with the page.</span></span>  
1.  <span data-ttu-id="f3ebf-134">单击 "**停止检测覆盖率" 并显示结果** ![ 停止检测覆盖率，并 ][ImageStopIcon] 在希望停止记录代码覆盖率时显示结果。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-134">Click **Stop Instrumenting Coverage And Show Results** ![Stop Instrumenting Coverage And Show Results][ImageStopIcon] when you want to stop recording code coverage.</span></span>  

## <span data-ttu-id="f3ebf-135">分析代码覆盖率</span><span class="sxs-lookup"><span data-stu-id="f3ebf-135">Analyze code coverage</span></span>   

<span data-ttu-id="f3ebf-136">"**覆盖率**" 选项卡中的表显示分析了哪些资源，以及每个资源中使用了多少代码。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-136">The table in the **Coverage** tab shows you what resources were analyzed, and how much code is used within each resource.</span></span> <span data-ttu-id="f3ebf-137">单击某一行以在 "**源**" 面板中打开该资源，并查看所使用的代码和未使用的代码的逐行划分。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-137">Click a row to open that resource in the **Sources** panel and see a line-by-line breakdown of used code and unused code.</span></span>  

> ##### <span data-ttu-id="f3ebf-138">图 3</span><span class="sxs-lookup"><span data-stu-id="f3ebf-138">Figure 3</span></span>  
> <span data-ttu-id="f3ebf-139">"代码覆盖率" 报表</span><span class="sxs-lookup"><span data-stu-id="f3ebf-139">A code coverage report</span></span>  
> !["代码覆盖率" 报表][ImageExample]  

*   <span data-ttu-id="f3ebf-141">**Url**列是已分析资源的 url。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-141">The **URL** column is the URL of the resource that was analyzed.</span></span>  
*   <span data-ttu-id="f3ebf-142">"**类型**" 列显示资源是否包含 CSS 和/或 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-142">The **Type** column says whether the resource contains CSS, JavaScript, or both.</span></span>  
*   <span data-ttu-id="f3ebf-143">"**字节总数**" 列是资源的总大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-143">The **Total Bytes** column is the total size of the resource in bytes.</span></span>  
*   <span data-ttu-id="f3ebf-144">"**未使用的字节**" 列表示未使用的字节数。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-144">The **Unused Bytes** column is the number of bytes that were not used.</span></span>  
*   <span data-ttu-id="f3ebf-145">最后一个未命名的列是 "**字节总数**" 和 "**未使用的字节**" 列的可视化。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-145">The last, unnamed column is a visualization of the **Total Bytes** and **Unused Bytes** columns.</span></span>  <span data-ttu-id="f3ebf-146">条的红色部分是未使用的字节。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-146">The red section of the bar is unused bytes.</span></span>  <span data-ttu-id="f3ebf-147">绿色部分使用字节。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-147">The green section is used bytes.</span></span>  

 



<!-- image links -->  

[ImageReloadIcon]: /microsoft-edge/devtools-guide-chromium/media/reload-icon.msft.png  
[ImageRecordIcon]: /microsoft-edge/devtools-guide-chromium/media/record-icon.msft.png  
[ImageStopIcon]: /microsoft-edge/devtools-guide-chromium/media/stop-icon.msft.png  

[ImageExample]: /microsoft-edge/devtools-guide-chromium/media/coverage-sources-resource-drawer-coverage.msft.png "图1：分析代码覆盖率"  
[ImageCoverage]: /microsoft-edge/devtools-guide-chromium/media/coverage-console-drawer-coverage-empty.msft.png "图2： "覆盖范围" 选项卡"  
[ImageExample]: /microsoft-edge/devtools-guide-chromium/media/coverage-sources-resource-drawer-coverage-selected.msft.png "图3： "代码覆盖率" 报表"  

<!-- links -->  

[DevToolsCommandMenu]: /microsoft-edge/devtools-guide-chromium/command-menu/index "通过 Microsoft Edge DevTools 命令菜单运行命令"  

[BootstrapButtons]: https://getbootstrap.com/docs/4.3/components/buttons "按钮-引导"  

> [!NOTE]
> <span data-ttu-id="f3ebf-153">此页面的某些部分是基于[由 Google][GoogleSitePolicies]创建和共享的工作的修改，并根据 "[创造性 Commons 归属4.0 国际许可证][CCA4IL]" 中所述的条款使用。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-153">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="f3ebf-154">原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/coverage/index)，由[Kayce Basques][KayceBasques] \ （技术作者、Chrome DevTools \ & Lighthouse \）创作。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-154">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/coverage/index) and is authored by [Kayce Basques][KayceBasques] \(Technical Writer, Chrome DevTools \& Lighthouse\).</span></span>  

[![创造性 Commons 许可证][CCby4Image]][CCA4IL]  
<span data-ttu-id="f3ebf-156">此作品通过 [Creative Commons Attribution 4.0 国际许可证][CCA4IL]获得许可。</span><span class="sxs-lookup"><span data-stu-id="f3ebf-156">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  