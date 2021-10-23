---
ms.assetid: 1b3ebc25-d023-4f23-bbba-dce066c20de8
description: ARIA 应用程序的最佳方案 (ARIA) 如何共同创建可访问的网站。
title: 有关构建可访问网站的资源
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/11/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: 辅助功能， 开发人员辅助功能， 可访问的网站， 边缘， Web 开发， ARIA， 开发人员， UIA， UI 自动化
ms.custom: seodec18
ms.openlocfilehash: ce742d0126008b47bcacb2ad164f76e1feb5cb3b
ms.sourcegitcommit: 97b32870897c702eed52d9fbbd13cfff2046ad87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2021
ms.locfileid: "12107784"
---
# <a name="resources-about-building-accessible-websites"></a>有关构建可访问网站的资源

Web 填充了动态且复杂的网站、应用程序和用户界面，这些网站、应用程序和用户界面是使用 HTML、CSS 和 JavaScript 的组合构建的。  但是，当设计和构建时没有考虑辅助功能时，依赖辅助技术来浏览 Web 的人很难使用这些复杂的网站。 [](https://webaim.org/articles/motor/assistive)

构建可供残障人士访问的网站需要有关用户界面的语义信息。  可访问的网站允许辅助技术（如屏幕阅读器）传达必要的信息，以帮助具有各种功能的人使用网站。

访问[HTML5Accessibility，](https://html5accessibility.com)了解哪些新 HTML5 功能可供 Microsoft Edge。


<!-- ====================================================================== -->
## <a name="how-accessibility-works"></a>辅助功能的工作原理

辅助技术添加计算机通常没有的功能。  例如，低视力用户可能将键盘与辅助技术（如屏幕阅读器）结合使用，而不是直接将浏览器与鼠标和屏幕结合使用。  

对于 Microsoft 平台和 Web 上的应用程序，辅助技术与以下任意组合交互：
*  Microsoft [UI 自动化](/windows/win32/winauto/uiauto-specandcommunitypromise)。
*  特定于应用程序的对象模型，如文档对象模型 (DOM) 中Microsoft Edge。

对于 Web 开发人员，某些 HTML 元素会映射到 UI 自动化对象，因此在选择这些 HTML 元素时，开发人员可以使用内置于这些元素的辅助功能属性和事件。  开发网站时，通常只需确保 API 正确写入或指定了适当的元素，应用程序就可访问。

有关详细信息，[请参阅 ARIA 和 Microsoft Edge](./aria-and-ui-automation.md) UI 自动化。  辅助通用Windows平台 (UWP) 在[辅助功能中进行了](/windows/uwp/design/accessibility/accessibility)Windows 开发人员中心。

通过良好的编码实践，可以解决与动态内容有关的许多常见辅助功能问题。  [WCAG 2.0](https://www.w3.org/TR/WCAG20)文档包括许多技术和最佳实践，可帮助你创建更易于访问的动态 Web 应用程序。  但是，即使正确编码，也不必访问动态内容。  [可访问的富 Internet 应用程序 (ARIA) ](#aria) 可帮助解决此问题。

有关 Web 辅助功能详细信息，请参阅 Web[](https://www.w3.org/WAI/intro/accessibility.php)辅助功能计划为 WEB 辅助功能简介[ (一) 。 ](https://www.w3.org/WAI)


<!-- ====================================================================== -->
## <a name="aria"></a>ARIA

W3C 的 Web 辅助功能计划 ([ARIA) ARIA](https://www.w3.org/TR/wai-aria)规范定义为使[](https://www.w3.org/WAI)所有人员均可访问的动态 Web 内容和自定义用户界面的语法。  ARIA 通过使用其他属性来扩展 HTML (、属性和状态) 旨在传达自定义语义。  浏览器使用这些属性将控件的状态和角色传递到辅助功能 API。

### <a name="roles-properties-and-states"></a>角色、属性和状态

ARIA 角色使用 [role](https://developer.mozilla.org/docs/Web/HTML/Reference) 属性在元素上设置，以提供有关元素的辅助技术和辅助功能 API 信息。  例如，分配以下 `<li>` 元素以 `role="menuitem"` 表示它是菜单中的项。

```html
<li role="menuitem">Home</li>
```

ARIA 状态和属性是 aria 前缀的属性，可提供有关对象的特定信息，以帮助形成角色的性质的定义。  属性是对象的性质所必不可少的属性，如 [aria-readonly](https://developer.mozilla.org/docs/Web/Accessibility/ARIA) 和 [aria-haspopup](https://developer.mozilla.org/docs/Web/Accessibility/ARIA)。  更改属性会影响对象的含义。

在下面的示例中，属性在菜单项上设置 `aria-haspopup="true"` `<li>` ，以表明它具有弹出窗口：

```html
<li role="menuitem" aria-haspopup="true">Open</li>
```

状态不会更改对象的性质，但表示与对象关联的信息，或用户与该对象的交互，如 [aria 隐藏或](https://developer.mozilla.org/docs/Web/Accessibility/ARIA) [aria 检查](https://developer.mozilla.org/docs/Web/Accessibility/ARIA)。  例如，以下示例中的状态表示已清除复选框 `aria-checked="false"` ，而不是选中：

```html
<div role="checkbox" aria-checked="false">Accept</div>
```

若要查看角色、属性和状态的完整列表，请转到 W3C 上 [的角色](https://www.w3.org/TR/wai-aria-1.1#roles) 模型。


<!-- ====================================================================== -->
## <a name="assistive-technology-compatibility-testing"></a>辅助技术兼容性测试

验证要构建的网站是否使用真实的辅助技术是确保为残障用户提供良好体验的最佳方法。  由于许多辅助技术都使用键盘，因此测试网站的键盘辅助功能是一个很好的起点。

[键盘兼容性](https://www.w3.org/WAI/perspective-videos/keyboard) 测试验证用户是否无需鼠标即可访问所有交互式控件。  Microsoft [Accessibility Insights for Web](https://accessibilityinsights.io/docs/web/overview)是适用于 Microsoft Edge 和 Chrome 的浏览器扩展，可指导你并展示一些常见问题。

一旦确信你的网站能很好地使用键盘，请通过其他辅助技术（如屏幕阅读器）试用它。  此测试可发现以下问题：

*   您的 HTML、ARIA 和 CSS。
*   对功能或技术的辅助技术的支持级别。

不同的浏览器可能将元素映射到平台辅助功能 API 的方式不同于Microsoft Edge API。  在构建接口时，考虑每个差异非常重要。

WebAIM 与屏幕[阅读器](https://webaim.org/projects/screenreadersurvey8)和低视力[](https://webaim.org/projects/lowvisionsurvey2)用户进行调查，帮助你确定要测试的辅助技术和浏览器。

### <a name="learning-how-to-test"></a>Learning测试

辅助技术是复杂的工具。  不要假定无需先了解辅助技术的工作原理，即可立即开始使用辅助技术进行测试。  Learning屏幕阅读器进行测试时，学习曲线尤其弯曲。  一位屏幕阅读器的新手可能会认为屏幕阅读器存在 Bug，而该问题实际上可能是使用屏幕阅读器时出错。

在 WebAIM[中通过](https://webaim.org/articles/screenreader_testing)屏幕阅读器进行测试提供了有关学习使用辅助技术进行测试的信息。

### <a name="testing-locally"></a>本地测试

大多数设备包括内置于操作系统的辅助技术。  Microsoft Windows包括Windows[讲述](https://support.microsoft.com/help/22798)人屏幕阅读器和Windows[放大镜](https://support.microsoft.com/windows/414948ba-8b1c-d3bd-8615-0e5e32204198)。  可以下载第三方辅助技术，如[NVDA、FreedomscientificSoftwareJaws](https://www.freedomscientific.com/products/software/jaws)和[ZoomText。](https://www.freedomscientific.com/products/software/zoomtext) [](https://www.nvaccess.org/about-nvda)  Apple macOS 包括 [VoiceOver](https://www.apple.com/accessibility/mac/vision) 屏幕阅读器。  iOS、Android 和 Linux 都支持各种辅助技术。

### <a name="testing-in-virtual-machines-and-emulators"></a>在虚拟机和仿真器中进行测试

在 macOS 下，如果你希望使用仅适用于 Windows 的辅助技术（如 Windows 讲述人或 NVDA）进行测试，Windows虚拟机。  具有 Microsoft Edge (EdgeHTML) 和 IE 的虚拟机可用于虚拟机下载页面上的 VirtualBox 和[VMWare。](https://developer.microsoft.com/microsoft-edge/tools/vms)

[Android Studio](https://developer.android.com/sdk/installing/studio.html) 包含一个仿真器，用于测试 Android 辅助功能套件 [中的辅助技术](https://play.google.com/store/apps/details?id=com.google.android.marvin.talkback)。  按照说明 [设置虚拟设备](https://developer.android.com/tools/devices/managing-avds.html) 并启动 [仿真](https://developer.android.com/tools/devices/emulator.html)器，然后从 GooglePlay 商店安装 [Android](https://play.google.com/store/apps/details?id=com.google.android.marvin.talkback) 辅助功能套件。

> [!NOTE]
> iOS 模拟器当前不包括 VoiceOver。

### <a name="cloud-based-testing-tools"></a>基于云的测试工具

如果辅助技术在你的操作系统上不可用，或者你无法将辅助技术安装在虚拟机或仿真器上，则基于云的辅助技术测试工具是下一个最佳工具。

*  [Assistiv Labs](https://assistivlabs.com) (一种商业) ，使你能够通过任何新式 Web 浏览器手动测试辅助技术。  选择辅助技术和浏览器，它将你与可以交互的虚拟机、仿真器或真实设备相连接。

另请参阅 [基于云的模拟器和模拟器](../../devtools-guide-chromium/device-mode/testing-other-browsers.md#cloud-based-emulators-and-simulators)。


<!-- ====================================================================== -->
## <a name="resources-for-accessibility-basics"></a>辅助功能基础知识资源

这些是辅助功能项目和计划。

### <a name="the-a11y-project"></a>A11Y 项目

[A11Y Project](http://a11yproject.com)社区推动的一项工作，用于简化 Web 辅助功能。  请查看[A11Y](https://a11yproject.com) Project了解基本的辅助功能原则、辅助功能模式和小组件库，以及辅助功能软件、博客、书籍[](https://a11yproject.com/patterns)和工具上的资源[](http://a11yproject.com/resources.html)。

### <a name="web-accessibility-initiative-wai"></a>Web 辅助功能计划 (使用) 

W3C [Web 辅助功能 (一) ，旨在 ](https://w3.org/WAI) 帮助改善 Web 的辅助功能。  他们的网站为 Web 辅助功能入门[](https://www.w3.org/WAI/gettingstarted/Overview.html)、包含设计、教程和演示文稿[](https://www.w3.org/WAI/users/Overview.html)等[提供了](https://www.w3.org/WAI/train.html)各种资源。


<!-- ====================================================================== -->
## <a name="accessibility-blogs"></a>辅助功能博客

这些是有关辅助功能的博客。

### <a name="tpgi-llc"></a>TPGi、LLC

[TPGi， LLC](https://www.tpgi.com/blog) 为世界各地的组织提供咨询服务和技术解决方案，以确保其客户在满足政府标准和国际标准的同时有效且高效地接触所有受众。  他们的博客涵盖了 Web 辅助功能最佳实践、辅助功能工具和辅助功能趋势等主题。

### <a name="simply-accessible"></a>易于访问

[Simply Accessible](http://simplyaccessible.com/articles) 是一个辅助功能专家团队，提供辅助功能培训、咨询等，以更改对 Web 上的辅助功能感知。  他们 [的文章](http://simplyaccessible.com/articles) 部分讨论了 Web 辅助功能、辅助设计等的最佳实践。

### <a name="level-access"></a>级别访问

[Level Access](https://www.levelaccess.com/blog) 是一家数字辅助功能公司，支持其客户开发并部署可访问的产品和服务。  他们的博客介绍 ARIA 最佳实践、辅助功能趋势、网络研讨会等主题。


<!-- ====================================================================== -->
## <a name="accessible-examples"></a>辅助示例

以下是辅助功能的库和示例。

### <a name="allyjs---tutorials"></a>ally.js - 教程

JavaScript 库，通过简化辅助功能帮助现代 Web 应用程序解决辅助功能问题。  有关详细信息，请转到"ally.js [- 教程"。](http://allyjs.io/tutorials)

### <a name="openajax-examples"></a>OpenAjax 示例

[OpenAjax 联盟网站](http://oaa-accessibility.org)是验证一项用于验证一些适用于一些用户、用户和

### <a name="patterns"></a>模式

[A11Y Project](http://a11yproject.com)提供了一个可访问小组件和模式（如菜单、按钮、工具提示等）的库。  有关详细信息， [请转到模式](http://a11yproject.com/patterns.html)。


<!-- ====================================================================== -->
## <a name="accessibility-techniques-and-tools"></a>辅助功能技术和工具

这些是改进辅助功能的技术和工具。

### <a name="accessibility-creating-accessible-extension-icons-for-microsoft-edge"></a>辅助功能：为用户创建辅助扩展Microsoft Edge

获取有关为用户创建辅助扩展图标Microsoft Edge。  有关详细信息，请转到辅助功能：为用户创建辅助[扩展Microsoft Edge。](/archive/microsoft-edge/legacy/developer/extensions/guides/accessibility)

### <a name="accessible-name-and-description-computation-and-mappings-11"></a>辅助名称和说明：计算和映射 1.1

此 W3C 映射文档介绍了浏览器如何确定 Web 内容语言中的可访问对象的名称和说明，以及如何在辅助功能 API 中公开它们。  有关详细信息，请转到辅助名称和说明 [：计算和映射 1.1](https://www.w3.org/TR/accname-1.1)。

### <a name="accessibility-evaluation-resources"></a>辅助功能评估资源

辅助功能评估资源是由 W3C 提供的多页资源，概述了用于评估网站辅助功能的不同方法。  有关详细信息，请转到辅助功能 [评估资源](https://www.w3.org/WAI/eval/Overview.html)。

### <a name="assistive-technology-compatibility-tests"></a>辅助技术兼容性测试

显示不同内容类型和标准在 AT 和 AT 辅助技术（如屏幕阅读器 () 的行为的测试结果。  有关详细信息，请转到辅助 [技术兼容性测试](http://www.powermapper.com/tests)。

### <a name="building-accessible-websites-just-got-a-lot-easier"></a>构建可访问的网站变得更加简单

本 .NET Web 开发和工具博客文章Visual Studio[扩展 Web 辅助功能检查器](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebAccessibilityChecker)。  有关详细信息，请转到构建 [可访问的网站，只需简单得多](https://devblogs.microsoft.com/aspnet/building-accessible-websites-just-got-a-lot-easier)。

### <a name="core-accessibility-api-mappings-11"></a>核心辅助功能 API 映射 1.1

此 W3C 映射文档说明如何向辅助功能 API 公开 Web 内容语言的语义。  有关详细信息，请转到核心辅助功能 [API 映射 1.1](https://www.w3.org/TR/core-aam-1.1)。

### <a name="easy-checks--a-first-review-of-web-accessibility"></a>轻松检查 – Web 辅助功能的首次评审

一系列由一系列由用户进行快速检查的（该快速检查可帮助你了解网页的辅助功能）。  有关详细信息，请转到轻松检查 [- Web 辅助功能的首次评审](https://www.w3.org/WAI/eval/preliminary.html)。

### <a name="how-to-meet-wcag-20"></a>如何满足 WCAG 2.0

快速参考 Web 内容辅助功能指南 (WCAG) 2.0 要求 (成功) 和技术。  有关详细信息，请转到如何开会 [WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref)。

### <a name="html-accessibility-api-mappings-10"></a>HTML 辅助功能 API 映射 1.0

此 W3C 映射文档说明了 HTML5.1 元素和属性如何映射到平台辅助功能 API。  有关详细信息，请转到 HTML [辅助功能 API 映射 1.0](https://www.w3.org/TR/html-aam-1.0)。

### <a name="quick-tips"></a>快速使用技巧

[A11Y](http://a11yproject.com)网站中有关辅助功能的快速 Web 开发Project。  有关详细信息，请转到[快速使用技巧。](http://a11yproject.com#Quick-tips)

### <a name="site-scan"></a>网站扫描

中心上的网站Microsoft Edge Dev检查过期库、布局问题和辅助功能问题。  有关详细信息，请转到"网站[扫描"。](https://developer.microsoft.com/microsoft-edge/tools)

### <a name="techniques-for-wcag-20"></a>WCAG 2.0 的技术

W3C 中的技术，为 Web 开发人员提供有关满足 Web 内容辅助功能指南 ([WCAG) 2.0 成功](https://w3.org/TR/WCAG20) 标准的指导。  有关详细信息，请转到 [WCAG 2.0 的技术](https://www.w3.org/TR/WCAG20-TECHS/Overview.html)。

### <a name="tips-on-developing-for-web-accessibility"></a>使用技巧 Web 辅助功能开发

使用技巧 W3C 中有关开发残障人士更容易访问的 Web 内容的信息。  有关详细信息，请转到"使用技巧[Web 辅助功能"上的"开发"。](https://w3.org/WAI/gettingstarted/tips/developing.html)

### <a name="wai-aria-authoring-practices-11"></a>WAI-ARIA 创作实践 1.1

W3C 提供的一个文档，使读者能够了解如何使用 WIDGET-ARIA 1.1，并推荐使用 WIDGET-ARIA 角色、状态和属性使小组件、导航和行为可供访问的方法。  有关详细信息，请转到 ["一.一一的一些操作](http://w3c.github.io/aria-practices)方法"。

### <a name="wai-guidelines-and-techniques"></a>一些指南和技术

由一系列由一系列 WEB 辅助功能指南和由一些用户制定的标准。  有关详细信息，请转到["一些指南和技术"。](https://w3.org/WAI/guid-tech.html)

### <a name="web-accessibility-evaluation-tools-list"></a>Web 辅助功能评估工具列表

可帮助确定网站是否满足辅助功能指南的 Web 辅助功能评估工具列表。  有关详细信息，请转到 Web [辅助功能评估工具列表](https://www.w3.org/WAI/ER/tools/index.html)。

### <a name="web-accessibility-perspectives-explore-the-impact-and-benefits-for-everyone"></a>Web 辅助功能角度：探索对所有人的影响和好处

W3C 关于辅助功能的影响和每个人的权益的一系列简短情境视频。  有关详细信息，请转到 Web [辅助功能角度：探索对所有人的影响和好处](https://w3.org/WAI/perspectives)。
