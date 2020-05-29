---
ms.assetid: 1e5c42a7-4604-46ac-ad7b-a65390e5b36a
description: 了解如何在 Microsoft Edge 中构建、设计和测试易于访问的网站。
title: 辅助功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/16/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: 辅助功能，面向开发人员的辅助功能，辅助网站，边缘，web 开发，ARIA，开发人员，UIA，UI 自动化
ms.openlocfilehash: 6ad95e9c250aa6a4a61ca09470cea86efd715427
ms.sourcegitcommit: 9169d784485e3cb0b1987a8f395c4bb688bd9b2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2020
ms.locfileid: "10583103"
---
# <span data-ttu-id="7ebae-104">辅助功能</span><span class="sxs-lookup"><span data-stu-id="7ebae-104">Accessibility</span></span>  

> <span data-ttu-id="7ebae-105">"\ [T] 他对残疾的影响在网上有了很多变动，因为 Web 在物理世界中消除了许多人面临的沟通和交互障碍。"</span><span class="sxs-lookup"><span data-stu-id="7ebae-105">"\[T\]he impact of disability is radically changed on the Web because the Web removes barriers to communication and interaction that many people face in the physical world."</span></span> [<span data-ttu-id="7ebae-106">（辅助功能 |W3C</span><span class="sxs-lookup"><span data-stu-id="7ebae-106">(Accessibility | W3C)</span></span>][W3CAccessibility]  

<span data-ttu-id="7ebae-107">[世界健康组织][WHODisabilities]将残疾定义为 "一人的身体功能与他们的居住环境的功能之间的交互不匹配"。</span><span class="sxs-lookup"><span data-stu-id="7ebae-107">The [World Health Organization][WHODisabilities] defines disability as "a mismatch in interaction between the features of a person's body and the features of the environment in which they live".</span></span>  <span data-ttu-id="7ebae-108">残疾范围从形势障碍（如在手机上保持婴儿或明亮的阳光）到其他物理、听觉、视觉或年龄相关障碍等方面的残障人士。</span><span class="sxs-lookup"><span data-stu-id="7ebae-108">Disabilities range from situational disabilities, like limited mobility while holding a baby or bright sunlight on a phone, to other physical, auditory, visual, or age-related impairments.</span></span>  

<span data-ttu-id="7ebae-109">设计包含的网站和其他技术可使每个人体验愉快。</span><span class="sxs-lookup"><span data-stu-id="7ebae-109">Designing websites and other technologies for inclusion creates an experience enjoyable by every person.</span></span>  <span data-ttu-id="7ebae-110">非独占设计和 web 辅助功能可帮助和帮助每个人使用 web。</span><span class="sxs-lookup"><span data-stu-id="7ebae-110">Inclusive design and web accessibility empowers and assists everyone to use the web.</span></span>  

<span data-ttu-id="7ebae-111">下面是一些最佳做法、代码示例和进一步的资源，可让你了解有关在 Microsoft Edge 中[设计][AccessibilityDesign]、[构建][AccessibilityBuild]和[测试][AccessibilityTest]易于访问的网站的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7ebae-111">Here are some best practices, code samples, and further resources for you to learn more about [Designing][AccessibilityDesign], [Building][AccessibilityBuild], and [Testing][AccessibilityTest] accessible websites in Microsoft Edge.</span></span>  

## <span data-ttu-id="7ebae-112">Microsoft Edge 中的辅助功能</span><span class="sxs-lookup"><span data-stu-id="7ebae-112">Accessibility in Microsoft Edge</span></span>  

<span data-ttu-id="7ebae-113">在 Microsoft Edge 中，我们引入了新式[UI 自动化 API][WindowsWin32AutoEntryui] \ （UIA API \）。</span><span class="sxs-lookup"><span data-stu-id="7ebae-113">In Microsoft Edge, we introduced modern [UI Automation API][WindowsWin32AutoEntryui] \(UIA API\).</span></span>  <span data-ttu-id="7ebae-114">对 UIA 的更改是浏览器辅助功能的主要投资，它为依赖于 Windows 10 中的辅助技术的用户提供了更多包含 web 体验的基础。</span><span class="sxs-lookup"><span data-stu-id="7ebae-114">The change to UIA was a major investment in browser accessibility, and it lays the foundation for a more inclusive web experience for users who depend on assistive technology in Windows 10.</span></span>  <span data-ttu-id="7ebae-115">用户还将受益于 Chromium 引擎的长绿性质。</span><span class="sxs-lookup"><span data-stu-id="7ebae-115">Users also benefit from the evergreen nature of the Chromium engine.</span></span>  

<span data-ttu-id="7ebae-116">Microsoft Edge 中的辅助功能系统本身支持新式 web 标准，包括 ARIA、HTML5 和 CSS3。</span><span class="sxs-lookup"><span data-stu-id="7ebae-116">The accessibility system in Microsoft Edge inherently supports modern web standards including ARIA, HTML5, and CSS3.</span></span>  <span data-ttu-id="7ebae-117">下面的简化的浏览器管道关系图将网页内容置于可访问的演示文稿层中。</span><span class="sxs-lookup"><span data-stu-id="7ebae-117">The following diagram of the simplified browser pipeline follows webpage content into an accessible presentation layer.</span></span>  

:::image type="complex" source="./media/accessibilityarchitecture.png" alt-text="转换为引擎模型的内容被投影到视觉对象和辅助功能视图中，显示为视觉对象或易于访问的演示文稿":::
   <span data-ttu-id="7ebae-119">图 1.</span><span class="sxs-lookup"><span data-stu-id="7ebae-119">Figure 1.</span></span>  <span data-ttu-id="7ebae-120">转换为引擎模型的内容被投影到视觉对象和辅助功能视图中，显示为视觉对象或易于访问的演示文稿</span><span class="sxs-lookup"><span data-stu-id="7ebae-120">Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation</span></span>
:::image-end:::

<!--![Figure 1.  Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation][ImageAccessibilityArchitecture]  -->  

<span data-ttu-id="7ebae-121">Microsoft Edge 团队不断与 W3C 和其他浏览器供应商协作，以确保新的 web 平台功能具有足够的内置可访问性。</span><span class="sxs-lookup"><span data-stu-id="7ebae-121">The Microsoft Edge team works with the W3C and other browser vendors on an ongoing basis to ensure that new web platform features have sufficient built-in accessibility.</span></span>  

<span data-ttu-id="7ebae-122">有关 Microsoft Edge 支持的新 HTML5 功能 accessibly 的信息，请访问[HTML5Accessibility][HTML5Accessibility]。</span><span class="sxs-lookup"><span data-stu-id="7ebae-122">For information on which new HTML5 features are accessibly supported by Microsoft Edge, visit [HTML5Accessibility][HTML5Accessibility].</span></span>  

## <span data-ttu-id="7ebae-123">资源</span><span class="sxs-lookup"><span data-stu-id="7ebae-123">Resources</span></span>  

#### <span data-ttu-id="7ebae-124">Microsoft Windows UI 自动化博客</span><span class="sxs-lookup"><span data-stu-id="7ebae-124">Microsoft Windows UI Automation Blog</span></span>  

<span data-ttu-id="7ebae-125">[Microsoft WINDOWS UI 自动化博客][ArchiveBlogsWinuiautomation]介绍与 WINDOWS 自动化 API 相关的主题。</span><span class="sxs-lookup"><span data-stu-id="7ebae-125">The [Microsoft Windows UI Automation blog][ArchiveBlogsWinuiautomation] covers topics related to the Windows Automation API.</span></span>  

#### <span data-ttu-id="7ebae-126">Web 辅助功能计划（WAI-ARIA）</span><span class="sxs-lookup"><span data-stu-id="7ebae-126">Web Accessibility Initiative (WAI)</span></span>  

<span data-ttu-id="7ebae-127">已提供 bt 的[Web 辅助功能计划（wai-aria）][W3CWaiHome] W3C 是帮助改进 Web 辅助功能的一项努力。</span><span class="sxs-lookup"><span data-stu-id="7ebae-127">The [Web Accessibility Initiative (WAI)][W3CWaiHome] provided bt the W3C is an effort to help improve the accessibility of the web.</span></span>  <span data-ttu-id="7ebae-128">网站提供了各种资源来[开始使用 Web 辅助功能][W3CWaiGettingstartedOverview]、[设计包含][W3CWaiFundamentals]、[教程和演示文稿][W3CWaiTeachAdvocate]等。</span><span class="sxs-lookup"><span data-stu-id="7ebae-128">The site provides a variety of resources for [Getting Started with Web Accessibility][W3CWaiGettingstartedOverview], [Designing for Inclusion][W3CWaiFundamentals], [tutorials and presentations][W3CWaiTeachAdvocate], and more.</span></span>  


<!-- image links -->  

<!--[ImageAccessibilityArchitecture]: ./media/accessibilityarchitecture.png "Figure 1: Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation"  -->  

<!-- links -->  

[AccessibilityBuild]: ./accessibility/build.md "构建易于访问的网站"  
[AccessibilityDesign]: ./accessibility/design.md "设计易于访问的网站"  
[AccessibilityTest]: ./accessibility/test.md "辅助功能测试"  

[WindowsWin32AutoEntryui]: /windows/win32/winauto/entry-uiauto-win32 "UI 自动化"  

[ArchiveBlogsWinuiautomation]: /archive/blogs/winuiautomation/ "Microsoft Windows UI 自动化博客"  

[HTML5Accessibility]: https://html5accessibility.com "HTML5 辅助功能"  

[W3CAccessibility]: https://w3.org/standards/webdesign/accessibility "辅助功能 |W3C"  
[W3CWaiFundamentals]: https://w3.org/wai/fundamentals/accessibility-intro "Web 辅助功能简介 |Web 辅助功能计划（WAI-ARIA） |W3C"  
[W3CWaiGettingstartedOverview]: https://w3.org/wai/gettingstarted/Overview "入门：使网站易于访问 |Web 辅助功能计划（WAI-ARIA） |W3C"  
[W3CWaiHome]: https://w3.org/wai "Web 辅助功能计划（WAI-ARIA） |W3C"  
[W3CWaiTeachAdvocate]: https://w3.org/wai/teach-advocate "教授和提倡概述 |Web 辅助功能计划（WAI-ARIA） |W3C"  

[WHODisabilities]: https://who.int/topics/disabilities "残疾 |填写"  
