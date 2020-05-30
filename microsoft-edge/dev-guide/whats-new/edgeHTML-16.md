---
ms.assetid: 476c4b7a-be24-434b-a051-83f19d741aaf
description: 本指南概述了 Microsoft Edge 中包含的开发人员功能和标准。
title: 开发人员指南
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/05/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: 边缘、web 开发、html、css、javascript、开发人员
ms.openlocfilehash: 36c5e6530ff584a97e4b42910757495362a1960d
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10562648"
---
# <span data-ttu-id="14fff-104">EdgeHTML 16 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="14fff-104">What's new in EdgeHTML 16</span></span>

<span data-ttu-id="14fff-105">下面是[EdgeHTML 16](https://blogs.windows.com/msedgedev/2017/10/17/edgehtml-16-fall-creators-update/) web 平台中提供的新功能和更新功能的列表，作为[Windows 10 秋季创意者更新](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)（10/2017，内部版本16299）的一部分。</span><span class="sxs-lookup"><span data-stu-id="14fff-105">Here's a list of the new and updated features shipped in [EdgeHTML 16](https://blogs.windows.com/msedgedev/2017/10/17/edgehtml-16-fall-creators-update/) web platform, as part of the [Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/) (10/2017, Build 16299).</span></span> <span data-ttu-id="14fff-106">有关特定 Windows 预览体验计划预览版中的更改，请参阅[Microsoft Edge Changelog](https://developer.microsoft.com/microsoft-edge/platform/changelog/)和[EdgeHTML 中的新增功能](../whats-new.md)。</span><span class="sxs-lookup"><span data-stu-id="14fff-106">For changes in specific Windows Insider Preview builds, see the [Microsoft Edge Changelog](https://developer.microsoft.com/microsoft-edge/platform/changelog/) and [What's New in EdgeHTML](../whats-new.md).</span></span>

<span data-ttu-id="14fff-107">下面是以下更改列表的固定链接： [https://aka.ms/devguide_edgehtml_16](https://aka.ms/devguide_edgehtml_16) 。</span><span class="sxs-lookup"><span data-stu-id="14fff-107">Here's the permalink for the following list of changes: [https://aka.ms/devguide_edgehtml_16](https://aka.ms/devguide_edgehtml_16).</span></span>

## <span data-ttu-id="14fff-108">新增功能和更新功能</span><span class="sxs-lookup"><span data-stu-id="14fff-108">New and updated features</span></span>

### <span data-ttu-id="14fff-109">CSS 网格布局</span><span class="sxs-lookup"><span data-stu-id="14fff-109">CSS Grid Layout</span></span>

<span data-ttu-id="14fff-110">Microsoft Edge 现在支持[CSS 网格布局](https://www.w3.org/TR/css-grid-1/)的 unprefixed 实现。</span><span class="sxs-lookup"><span data-stu-id="14fff-110">Microsoft Edge now supports the unprefixed implementation of [CSS Grid Layout](https://www.w3.org/TR/css-grid-1/).</span></span> <span data-ttu-id="14fff-111">[网格布局](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout)定义了一个二维基于网格的布局系统，该布局系统支持更多布局流畅性，使用浮动或脚本进行定位。</span><span class="sxs-lookup"><span data-stu-id="14fff-111">[Grid Layout](https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout) defines a two-dimensional grid-based layout system which enables more layout fluidity than possible with positioning using floats or scripts.</span></span> <span data-ttu-id="14fff-112">下面的示例使用 CSS 网格布局创建基本网页的结构。</span><span class="sxs-lookup"><span data-stu-id="14fff-112">The example below uses CSS Grid Layout to create the structure for a basic web page.</span></span>


<iframe height='303' scrolling='no' title='<span data-ttu-id="14fff-113">CSS 网格布局</span><span class="sxs-lookup"><span data-stu-id="14fff-113">CSS Grid Layout</span></span>' src='//codepen.io/MSEdgeDev/embed/mMQqZX/?height=303&theme-id=23761&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true'><span data-ttu-id="14fff-114"><a href='https://codepen.io/MSEdgeDev/pen/mMQqZX/'> </a> <a href='https://codepen.io/MSEdgeDev'> 在 CodePen 上按 MSEdgeDev （@MSEdgeDev）查看笔 CSS 网格布局 </a> <a href='https://codepen.io'> </a> 。</span><span class="sxs-lookup"><span data-stu-id="14fff-114">See the Pen <a href='https://codepen.io/MSEdgeDev/pen/mMQqZX/'>CSS Grid Layout</a>by MSEdgeDev (<a href='https://codepen.io/MSEdgeDev'>@MSEdgeDev</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


### <span data-ttu-id="14fff-115">CSS `object-fit` 和</span><span class="sxs-lookup"><span data-stu-id="14fff-115">CSS `object-fit` and</span></span> `object-position`

<span data-ttu-id="14fff-116">EdgeHTML 16 引入了对 CSS 属性 [`object-fit`](https://developer.mozilla.org/docs/Web/CSS/object-fit) 和的支持 [`object-position`](https://developer.mozilla.org/docs/Web/CSS/object-position) 。</span><span class="sxs-lookup"><span data-stu-id="14fff-116">EdgeHTML 16 introduces support for CSS properties [`object-fit`](https://developer.mozilla.org/docs/Web/CSS/object-fit) and [`object-position`](https://developer.mozilla.org/docs/Web/CSS/object-position).</span></span>  <span data-ttu-id="14fff-117">这些属性控制替换内容在 "内容" 框中的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="14fff-117">These properties control the position and size of replaced content within the content box.</span></span>  

### <span data-ttu-id="14fff-118">开发人员工具</span><span class="sxs-lookup"><span data-stu-id="14fff-118">Developer Tools</span></span>

<span data-ttu-id="14fff-119">在此版本中，我们启动了一个主要的 Microsoft Edge DevTools 重构措施来改进可靠性和性能，还添加了一组新功能，您可以在[Windows 预览体验计划](https://insider.windows.com/)内部版本上开始使用。</span><span class="sxs-lookup"><span data-stu-id="14fff-119">This release we started a major Microsoft Edge DevTools refactoring effort for improved robustness and performance, and also added a bunch of new features you can start using today on [Windows Insider](https://insider.windows.com/) builds.</span></span>  <span data-ttu-id="14fff-120">有关更改内容的详细信息，请查看[Microsoft Edge DevTools 指南](../../devtools-guide/whats-new.md)！</span><span class="sxs-lookup"><span data-stu-id="14fff-120">Check out the [Microsoft Edge DevTools guide](../../devtools-guide/whats-new.md) for more on what's changed!</span></span>

### <span data-ttu-id="14fff-121">JavaScript</span><span class="sxs-lookup"><span data-stu-id="14fff-121">JavaScript</span></span>

<span data-ttu-id="14fff-122">[EdgeHTML 16 在](https://blogs.windows.com/msedgedev/2017/10/31/optimizations-webassembly-sharedarraybuffer-atomics-edgehtml-16/#FodxEPHxR4WkbtyA.97)早期版本的 Javascript 性能优化的基础上，通过展开 Chakra 引擎能够延迟/重新延迟函数、使用多态内联缓存以及使用*try/finally*块优化函数来优化早期版本。</span><span class="sxs-lookup"><span data-stu-id="14fff-122">[EdgeHTML 16 builds on Javascript performance](https://blogs.windows.com/msedgedev/2017/10/31/optimizations-webassembly-sharedarraybuffer-atomics-edgehtml-16/#FodxEPHxR4WkbtyA.97) optimizations of previous releases by expanding the Chakra engine's ability to defer/re-defer functions, use polymorphic inline caches, and optimize functions with *try/finally* blocks.</span></span>

<span data-ttu-id="14fff-123">此外，EdgeHTML 15 中首先预览的功能在默认情况下是稳定和启用的：</span><span class="sxs-lookup"><span data-stu-id="14fff-123">Additionally, features first previewed in EdgeHTML 15 are now stable and enabled by default:</span></span>

#### <span data-ttu-id="14fff-124">新增功能（默认情况下处于打开状态）</span><span class="sxs-lookup"><span data-stu-id="14fff-124">New features (on by default)</span></span>

* <span data-ttu-id="14fff-125">[WebAssembly](https://developer.microsoft.com/microsoft-edge/platform/status/webassemblymvp/?q=WebAssembly)MVP （[演示](https://webassembly.org/demo/)）</span><span class="sxs-lookup"><span data-stu-id="14fff-125">[WebAssembly](https://developer.microsoft.com/microsoft-edge/platform/status/webassemblymvp/?q=WebAssembly) MVP ([demo](https://webassembly.org/demo/))</span></span>
* [<span data-ttu-id="14fff-126">共享内存和 Atomics</span><span class="sxs-lookup"><span data-stu-id="14fff-126">Shared Memory and Atomics</span></span>](https://developer.microsoft.com/microsoft-edge/platform/status/sharedmemoryandatomics/?q=Atomics)

### <span data-ttu-id="14fff-127">付款请求 API</span><span class="sxs-lookup"><span data-stu-id="14fff-127">Payment Request API</span></span>

<span data-ttu-id="14fff-128">[支付请求 API](../windows-integration/payment-request-api.md)是一个开放的跨浏览器标准，使浏览器能够充当消费者、消费者和支付方式（如信用卡）之间的媒介，消费者已存储在云中。</span><span class="sxs-lookup"><span data-stu-id="14fff-128">The [Payment Request API](../windows-integration/payment-request-api.md) is an open, cross-browser standard that enables browsers to act as an intermediary between merchants, consumers, and payment methods (e.g. credit cards) that consumers have stored in the cloud.</span></span>  <span data-ttu-id="14fff-129">EdgeHTML 16 中的 API 已更新，以匹配最新的 W3C[付款请求 API](https://w3c.github.io/payment-request/)规范。</span><span class="sxs-lookup"><span data-stu-id="14fff-129">The API in EdgeHTML 16 has been updated to match the latest W3C [Payment Request API](https://w3c.github.io/payment-request/) specification.</span></span> <span data-ttu-id="14fff-130">这包括：</span><span class="sxs-lookup"><span data-stu-id="14fff-130">This includes:</span></span>
* <span data-ttu-id="14fff-131">对方法的支持 `canMakePayment()`</span><span class="sxs-lookup"><span data-stu-id="14fff-131">Support for the `canMakePayment()` method</span></span>
* <span data-ttu-id="14fff-132">对属性的支持 `requestId`</span><span class="sxs-lookup"><span data-stu-id="14fff-132">Support for the `requestId` property</span></span>
* <span data-ttu-id="14fff-133">对属性的支持 `id`</span><span class="sxs-lookup"><span data-stu-id="14fff-133">Support for the `id` property</span></span>
* <span data-ttu-id="14fff-134">该 `complete()` 方法的参数的默认值 `result` 从 "" 更改为 "unknown"</span><span class="sxs-lookup"><span data-stu-id="14fff-134">The default value for the `complete()` method's `result` parameter changed from " " to "unknown"</span></span>

### <span data-ttu-id="14fff-135">服务工作人员</span><span class="sxs-lookup"><span data-stu-id="14fff-135">Service Workers</span></span>

<span data-ttu-id="14fff-136">[服务工作人员](https://www.w3.org/TR/service-workers-1/)是在网页的后台运行的事件驱动的脚本。</span><span class="sxs-lookup"><span data-stu-id="14fff-136">[Service Workers](https://www.w3.org/TR/service-workers-1/) are event-driven scripts that run in the background of a web page.</span></span> <span data-ttu-id="14fff-137">服务工作人员仅支持以前的应用（如拦截和处理来自网络的请求、管理和处理后台同步、本地存储和推送通知），以前仅提供本机应用功能。</span><span class="sxs-lookup"><span data-stu-id="14fff-137">Service workers enable functionality previously only available with native apps like intercepting and handling requests from the network, managing and handling background sync, local storage, and push notifications.</span></span> <span data-ttu-id="14fff-138">服务工作人员的支持仍在开发中，但你可以通过我们的实验服务辅助功能在 Microsoft Edge 中测试你的 PWA，方法是在 "**标志**" 中启用服务工作人员功能。</span><span class="sxs-lookup"><span data-stu-id="14fff-138">Support for service worker is still in development, but you can test out your PWA in Microsoft Edge with our experimental service worker support by enabling the service worker feature in **about:flags**.</span></span>

### <span data-ttu-id="14fff-139">WebVR</span><span class="sxs-lookup"><span data-stu-id="14fff-139">WebVR</span></span>
<span data-ttu-id="14fff-140">Microsoft Edge 的 WebVR 已添加了对[运动控制器](https://developer.microsoft.com/windows/mixed-reality/motion_controllers)的支持。</span><span class="sxs-lookup"><span data-stu-id="14fff-140">WebVR for Microsoft Edge has added support for [motion controllers](https://developer.microsoft.com/windows/mixed-reality/motion_controllers).</span></span> <span data-ttu-id="14fff-141">这些控制器在空间中具有精确的位置，允许在虚拟现实中与数字对象进行细微的粒度交互。</span><span class="sxs-lookup"><span data-stu-id="14fff-141">These controllers have a precise position in space, allowing for fine grained interaction with digital objects in virtual reality.</span></span>

![运动控制器](../media/MotionControllers.jpg)

<span data-ttu-id="14fff-143">WebVR 也已经过优化，可支持两种不同类型的体验。</span><span class="sxs-lookup"><span data-stu-id="14fff-143">WebVR has also been optimized to support two different types of experiences.</span></span>

<span data-ttu-id="14fff-144">**Windows Mixed Reality 电脑**-具有集成图形的台式机和笔记本电脑。</span><span class="sxs-lookup"><span data-stu-id="14fff-144">**Windows Mixed Reality PCs** - Desktops and laptops with integrated graphics.</span></span>  <span data-ttu-id="14fff-145">当插入这些设备时，我们的沉浸式耳机将在每秒60帧运行。</span><span class="sxs-lookup"><span data-stu-id="14fff-145">When plugged into these devices, our immersive headsets will run at 60 frames per second.</span></span>  
<span data-ttu-id="14fff-146">**Windows Mixed Reality 超 pc** -具有独立图形的台式机和笔记本电脑。</span><span class="sxs-lookup"><span data-stu-id="14fff-146">**Windows Mixed Reality Ultra PCs** - Desktops and laptops with discrete graphics.</span></span> <span data-ttu-id="14fff-147">当插入这些设备时，我们的沉浸式耳机将在每秒90帧运行。</span><span class="sxs-lookup"><span data-stu-id="14fff-147">When plugged into these devices, our immersive headsets will run at 90 frames per second.</span></span>   

<span data-ttu-id="14fff-148">这两个设置将支持相同的沉浸式视频和游戏体验。</span><span class="sxs-lookup"><span data-stu-id="14fff-148">Both setups will support the same immersive video and gaming experiences.</span></span> 

<span data-ttu-id="14fff-149">有关即将到来的 Windows Mixed Reality 更新的详细信息，请查看[Windows Mixed reality](https://blogs.windows.com/windowsexperience/2017/08/28/windows-mixed-reality-holiday-update/)假日更新博客文章。</span><span class="sxs-lookup"><span data-stu-id="14fff-149">For more info about the upcoming Windows Mixed Reality updates, check out the [Windows Mixed Reality](https://blogs.windows.com/windowsexperience/2017/08/28/windows-mixed-reality-holiday-update/) holiday update blog post.</span></span> 

<span data-ttu-id="14fff-150">有关指南和演示，请转到[WebVR 开发人员指南](https://docs.microsoft.com/microsoft-edge/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="14fff-150">For guides and demos, head over to the [WebVR Developer Guide](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

 > [!NOTE] 
 > <span data-ttu-id="14fff-151">由于 WebVR 规范仍在开发中，Microsoft Edge 的实现可能会在行的后面更改。</span><span class="sxs-lookup"><span data-stu-id="14fff-151">Since the WebVR spec is still in development, Microsoft Edge's implementation may change later down the line.</span></span>

## <span data-ttu-id="14fff-152">EdgeHTML 16 中的新 Api</span><span class="sxs-lookup"><span data-stu-id="14fff-152">New APIs in EdgeHTML 16</span></span>

<span data-ttu-id="14fff-153">下面是 EdgeHTML 16 中新 Api 的完整列表。</span><span class="sxs-lookup"><span data-stu-id="14fff-153">Here's the full list of new APIs in EdgeHTML 16.</span></span> <span data-ttu-id="14fff-154">它们以 **[界面名称] 的格式列出。 [api 名称]**。</span><span class="sxs-lookup"><span data-stu-id="14fff-154">They are listed in the format of **[interface name].[api name]**.</span></span>

> [!NOTE] 
> <span data-ttu-id="14fff-155">虽然在 DOM 中公开以下 Api，但某些 Api 的端到端行为可能仍在开发中。</span><span class="sxs-lookup"><span data-stu-id="14fff-155">Although the following APIs are exposed in the DOM, the end-to-end behavior of some might still be in development.</span></span> <span data-ttu-id="14fff-156">请参阅[Microsoft Edge 平台状态](https://developer.microsoft.com/microsoft-edge/platform/status/)，了解有关功能支持的官方 word 功能。</span><span class="sxs-lookup"><span data-stu-id="14fff-156">Refer to  [Microsoft Edge platform status](https://developer.microsoft.com/microsoft-edge/platform/status/) for the official word on feature support.</span></span>

<iframe height='559' scrolling='no' title='<span data-ttu-id="14fff-157">EdgeHTML 16 中的新 Api</span><span class="sxs-lookup"><span data-stu-id="14fff-157">New APIs in EdgeHTML 16</span></span>' src='//codepen.io/MSEdgeDev/embed/jLGZZY/?height=559&theme-id=23761&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true'><span data-ttu-id="14fff-158">请参阅 <a href='https://codepen.io/MSEdgeDev/pen/jLGZZY/'> </a> CodePen 上的 EdgeHTML MSEdgeDev （@MSEdgeDev）中的笔新 api <a href='https://codepen.io/MSEdgeDev'> </a> <a href='https://codepen.io'> </a> 。</span><span class="sxs-lookup"><span data-stu-id="14fff-158">See the Pen <a href='https://codepen.io/MSEdgeDev/pen/jLGZZY/'>New APIs in EdgeHTML 16</a>by MSEdgeDev (<a href='https://codepen.io/MSEdgeDev'>@MSEdgeDev</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span></iframe></p>

<h2 id="previous-edgehtml-releases"><span data-ttu-id="14fff-159">以前的 EdgeHTML 版本</span><span class="sxs-lookup"><span data-stu-id="14fff-159">Previous EdgeHTML releases</span></span></h2>
<p><a href="https://aka.ms/devguide_edgehtml_12" data-raw-source="[EdgeHTML 12 / Windows build 10240 (7/2015)](https://aka.ms/devguide_edgehtml_12)"><span data-ttu-id="14fff-160">EdgeHTML 12/Windows 内部版本10240（7/2015）</span><span class="sxs-lookup"><span data-stu-id="14fff-160">EdgeHTML 12 / Windows build 10240 (7/2015)</span></span></a>

[<span data-ttu-id="14fff-161">EdgeHTML 13/Windows 内部版本10586（11/2015）</span><span class="sxs-lookup"><span data-stu-id="14fff-161">EdgeHTML 13 / Windows build 10586 (11/2015)</span></span>](https://aka.ms/devguide_edgehtml_13)

[<span data-ttu-id="14fff-162">EdgeHTML 14/Windows 内部版本14393（8/2016）</span><span class="sxs-lookup"><span data-stu-id="14fff-162">EdgeHTML 14 / Windows build 14393 (8/2016)</span></span>](https://aka.ms/devguide_edgehtml_14)

[<span data-ttu-id="14fff-163">EdgeHTML 15/Windows 内部版本15063（4/2017）</span><span class="sxs-lookup"><span data-stu-id="14fff-163">EdgeHTML 15 / Windows build 15063 (4/2017)</span></span>](https://aka.ms/devguide_edgehtml_15)