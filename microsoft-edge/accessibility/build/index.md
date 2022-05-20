---
title: 有关构建辅助网站的资源
description: " (ARIA) 的最佳做法和易于访问的富 Internet 应用程序如何汇集在一起创建可访问的网站。"
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.assetid: 1b3ebc25-d023-4f23-bbba-dce066c20de8
ms.custom: seodec18
ms.date: 05/11/2021
ms.openlocfilehash: dbcb406b31dc8887b9a606251f2e362b72c27b55
ms.sourcegitcommit: 1b70a2b8fa6649a1aa423b047c64f3df972150cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2022
ms.locfileid: "12520876"
---
# <a name="resources-about-building-accessible-websites"></a>有关构建辅助网站的资源

Web 上填充了使用 HTML、CSS 和 JavaScript 组合生成的动态和复杂的网站、应用程序和用户界面。  但是，在设计和构建时，在不考虑辅助功能的情况下，依赖 [辅助技术](https://webaim.org/articles/motor/assistive) 浏览 Web 的用户很难使用这些复杂的网站。

构建可供残障人士访问的网站需要有关用户界面的语义信息。  辅助网站允许辅助技术（如屏幕阅读器）传达必要的信息，以帮助具有各种能力的用户使用该网站。

请访问 [HTML5Accessibility](https://html5accessibility.com)，了解Microsoft Edge可访问哪些新 HTML5 功能。


<!-- ====================================================================== -->
## <a name="how-accessibility-works"></a>辅助功能的工作原理

辅助技术会添加计算机通常没有的功能。  例如，视力低下的用户可能会将键盘与辅助技术（如屏幕阅读器）结合使用，而不是直接将浏览器与鼠标和屏幕结合使用。  

对于 Microsoft 平台和 Web 上的应用程序，辅助技术与以下任意组合进行交互：
*  Microsoft [UI 自动化](/windows/win32/winauto/uiauto-specandcommunitypromise)。
*  特定于应用程序的对象模型，例如文档对象模型 (Microsoft Edge中的 DOM) 。

对于 Web 开发人员，某些 HTML 元素映射到UI 自动化对象，因此在选择这些 HTML 元素时，开发人员可以使用内置到这些元素的辅助功能属性和事件。  开发网站时，通常只需确保 API 正确写入或指定了相应的元素即可访问应用程序。

有关详细信息，请查看 [Microsoft Edge 中的 ARIA 和 UI 自动化](aria-and-ui-automation.md)。  可访问通用 Windows 平台 (UWP) 应用在 Windows 开发人员中心 中的[辅助功能](/windows/uwp/design/accessibility/accessibility)中介绍。

通过良好的编码实践，可以解决动态内容的许多常见辅助功能问题。  [WCAG 2.0](https://www.w3.org/TR/WCAG20) 文档包含许多技术和最佳做法，可帮助你创建更易于访问的动态 Web 应用程序。  但是，即使编码正确，动态内容也不一定可访问。  [可访问富 Internet 应用程序 (ARIA) ](#aria) 有助于克服此问题。

有关 Web 辅助功能的详细信息，请查看 [Web 辅助功能计划 (WAI) 的 Web 辅助功能](https://www.w3.org/WAI)[简介](https://www.w3.org/WAI/intro/accessibility.php)。


<!-- ====================================================================== -->
## <a name="aria"></a>ARIA

W3C 的 [Web 辅助功能计划](https://www.w3.org/WAI)[提供的可访问丰富 Internet 应用程序 (ARIA) ](https://www.w3.org/TR/wai-aria)规范定义为使动态 Web 内容和自定义用户界面可供所有人访问的语法。  ARIA 通过使用其他特性来扩展 HTML， (角色、属性和状态) 旨在传达自定义语义。  浏览器使用这些属性将控件的状态和角色传递给辅助功能 API。

### <a name="roles-properties-and-states"></a>角色、属性和状态

ARIA 角色设置在使用 [角色](https://developer.mozilla.org/docs/Web/HTML/Reference) 属性的元素上，以提供有关元素的辅助技术和辅助功能 API 信息。  例如，分配以下 `<li>` 元素 `role="menuitem"` 以表示它是菜单中的项。

```html
<li role="menuitem">Home</li>
```

ARIA 状态和属性是 aria 前缀属性，提供有关对象的特定信息，以帮助形成角色性质的定义。  属性是对象性质必不可少的属性，如 [aria-readonly](https://developer.mozilla.org/docs/Web/Accessibility/ARIA) 和 [aria-haspopup](https://developer.mozilla.org/docs/Web/Accessibility/ARIA)。  更改属性会影响对象的含义。

在下面的示例中，该属性 `aria-haspopup="true"` 设置在菜单项上 `<li>` ，以表示它具有弹出窗口：

```html
<li role="menuitem" aria-haspopup="true">Open</li>
```

状态不会更改对象的性质，但表示与对象相关联的信息，或与对象的用户交互（如 [aria 隐藏](https://developer.mozilla.org/docs/Web/Accessibility/ARIA) 或 [aria-checked）](https://developer.mozilla.org/docs/Web/Accessibility/ARIA)。  例如，下面示例中的状态 `aria-checked="false"` 表示已清除复选框，而不是选中：

```html
<div role="checkbox" aria-checked="false">Accept</div>
```

若要查看角色、属性和状态的完整列表，请转到 W3C [上的角色模型](https://www.w3.org/TR/wai-aria-1.1#roles) 。


<!-- ====================================================================== -->
## <a name="assistive-technology-compatibility-testing"></a>辅助技术兼容性测试

验证正在构建的网站是否适用于真正的辅助技术，是确保为残障用户提供良好体验的最佳方式。  由于许多辅助技术都使用键盘，因此测试网站的键盘辅助功能是一个不错的开始位置。

[键盘兼容性测试](https://www.w3.org/WAI/perspective-videos/keyboard) 验证用户是否有权访问所有交互式控件，而无需鼠标。  适用于 [Web 的 Microsoft 辅助功能Insights](https://accessibilityinsights.io/docs/web/overview)是Microsoft Edge和 Chrome 的浏览器扩展，可指导你并揭示几个常见问题。

一旦你确信你的网站能够很好地使用键盘，请尝试使用其他辅助技术，如屏幕阅读器。  此测试可发现以下问题：

*   HTML、ARIA 和 CSS。
*   对功能或技术的辅助技术的支持级别。

不同的浏览器可能会以不同的方式将元素映射到平台辅助功能 API，Microsoft Edge映射它们。  生成接口时，请务必考虑每个差异。

WebAIM 与 [屏幕阅读器](https://webaim.org/projects/screenreadersurvey8) 和 [低视力](https://webaim.org/projects/lowvisionsurvey2) 用户一起进行调查，帮助你确定要测试的辅助技术和浏览器。

### <a name="learning-how-to-test"></a>Learning如何测试

辅助技术是复杂的工具。  不要假定你能够立即开始使用辅助技术进行测试，而无需先了解辅助技术的工作原理。  Learning使用屏幕阅读器进行测试具有特别陡峭的学习曲线。  屏幕阅读器的新手用户可能会认为屏幕阅读器有 bug，而问题实际上可能是使用屏幕阅读器时出错。

使用 WebAIM [的屏幕阅读器进行测试](https://webaim.org/articles/screenreader_testing)可提供有关学习辅助技术测试的详细信息。

### <a name="testing-locally"></a>在本地测试

大多数设备包括内置到 OS 的辅助技术。  Microsoft Windows包含[Windows 讲述人](https://support.microsoft.com/help/22798)屏幕阅读器和[Windows放大镜](https://support.microsoft.com/windows/414948ba-8b1c-d3bd-8615-0e5e32204198)。  第三方辅助技术（如 [NVDA](https://www.nvaccess.org/about-nvda)、 [FreedomscientificSoftwareJaws](https://www.freedomscientific.com/products/software/jaws) 和 [ZoomText](https://www.freedomscientific.com/products/software/zoomtext) ）可供下载。  Apple macOS包含 [VoiceOver](https://www.apple.com/accessibility/mac/vision) 屏幕阅读器。  iOS、Android和 Linux 都支持各种辅助技术。

### <a name="testing-in-virtual-machines-and-emulators"></a>在虚拟机和仿真器中进行测试

在macOS下，如果要使用仅适用于Windows的辅助技术（如Windows 讲述人或 NVDA）进行测试，请创建Windows虚拟机。  具有 Microsoft Edge (EdgeHTML) 和 IE 的虚拟机在[虚拟机下载页面](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms)上可用于 VirtualBox 和 VMWare。<!-- temp keep /en-us, delete it later when omitting it ends up at right url -->

[Android Studio](https://developer.android.com/sdk/installing/studio.html)包含一个模拟器，可用于在[Android辅助功能套件](https://play.google.com/store/apps/details?id=com.google.android.marvin.talkback)中测试辅助技术。  按照说明[设置虚拟设备](https://developer.android.com/tools/devices/managing-avds.html)并[启动模拟器](https://developer.android.com/tools/devices/emulator.html)，然后从 GooglePlay 商店安装[Android辅助功能套件](https://play.google.com/store/apps/details?id=com.google.android.marvin.talkback)。

> [!NOTE]
> iOS模拟器当前不包括 VoiceOver。

### <a name="cloud-based-testing-tools"></a>基于云的测试工具

如果 OS 上没有辅助技术，或者你无法在虚拟机或仿真器上安装辅助技术，则基于云的辅助技术测试工具是下一个最佳功能。

*  [辅助实验室](https://assistivlabs.com) (商业产品) 使你可以通过任何新式 Web 浏览器手动测试辅助技术。  选择辅助技术和浏览器，它会将你与虚拟机、模拟器或可交互的实际设备连接起来。

另请参阅 [基于云的模拟器和模拟器](../../devtools-guide-chromium/device-mode/testing-other-browsers.md#cloud-based-emulators-and-simulators)。


<!-- ====================================================================== -->
## <a name="resources-for-accessibility-basics"></a>辅助功能基础知识的资源

这些是辅助功能的项目和计划。

### <a name="the-a11y-project"></a>A11Y 项目

[A11Y Project](http://a11yproject.com)是社区驱动的一项工作，旨在简化 Web 辅助功能。  查看 [A11Y Project](https://a11yproject.com)网站，了解基本辅助功能原则、可访问模式和小组件[库](https://a11yproject.com/patterns)，以及辅助功能软件、博客、书籍和工具上的[资源](http://a11yproject.com/resources.html)。

### <a name="web-accessibility-initiative-wai"></a>WEB 辅助功能计划 (WAI) 

W3C [Web 辅助功能计划 (WAI) ](https://w3.org/WAI) 有助于提高 Web 的辅助功能。  他们的网站提供了各种资源，用于[入门 Web 辅助功能](https://www.w3.org/WAI/gettingstarted/Overview.html)、[设计包含](https://www.w3.org/WAI/users/Overview.html)功能、[教程和演示文稿](https://www.w3.org/WAI/train.html)等。


<!-- ====================================================================== -->
## <a name="accessibility-blogs"></a>辅助功能博客

这些是有关辅助功能的博客。

### <a name="tpgi-llc"></a>TPGi、LLC

[TPGi、LLC](https://www.tpgi.com/blog) 向世界各地的组织提供咨询和技术解决方案，以确保其客户在符合政府和国际标准的同时有效地接触所有受众。  他们的博客涵盖了 Web 辅助功能最佳做法、辅助功能工具和辅助功能趋势等主题。

### <a name="simply-accessible"></a>简单易于访问

[简单易于访问](http://simplyaccessible.com/articles) 是一个辅助功能专家团队，提供辅助功能培训、咨询等，以更改对 Web 上的辅助功能的看法。  他们的 [“文章”](http://simplyaccessible.com/articles) 部分讨论了有关 Web 辅助功能、辅助设计等的最佳做法。

### <a name="level-access"></a>级别访问

[Level Access](https://www.levelaccess.com/blog) 是一家数字辅助功能公司，支持其客户端开发和部署可访问的产品和服务。  他们的博客介绍了 ARIA 最佳做法、辅助功能趋势、网络研讨会等主题。


<!-- ====================================================================== -->
## <a name="accessible-examples"></a>辅助示例

这些是可访问性的库和示例。

### <a name="allyjs---tutorials"></a>ally.js - 教程

JavaScript 库，通过使辅助功能更简单，帮助具有辅助功能问题的新式 Web 应用程序。  有关详细信息，请转到 [ally.js - 教程](http://allyjs.io/tutorials)。

### <a name="openajax-examples"></a>OpenAjax 示例

[OpenAjax 联盟网站](http://oaa-accessibility.org)是验证 WAI-ARIA 规则的极佳资源，并提供了许多 WAI-ARIA 实现示例。

### <a name="patterns"></a>模式

[A11Y Project](http://a11yproject.com)提供可访问的小组件和模式库，如菜单、按钮、工具提示等。  有关详细信息，请转到 [“模式](http://a11yproject.com/patterns.html)”。


<!-- ====================================================================== -->
## <a name="accessibility-techniques-and-tools"></a>辅助功能技术和工具

这些是用于改进辅助功能的技术和工具。

### <a name="accessibility-creating-accessible-extension-icons-for-microsoft-edge"></a>辅助功能：为Microsoft Edge创建辅助扩展图标

获取有关为Microsoft Edge创建辅助扩展图标的指南。  有关详细信息，请转到[“辅助功能：为Microsoft Edge创建辅助扩展图标](/archive/microsoft-edge/legacy/developer/extensions/guides/accessibility)。

### <a name="accessible-name-and-description-computation-and-mappings-11"></a>可访问的名称和说明：计算和映射 1.1

此 W3C 映射文档介绍浏览器如何确定来自 Web 内容语言的辅助对象的名称和说明，并在辅助功能 API 中公开它们。  有关详细信息，请转到 [可访问的名称和说明：计算和映射 1.1](https://www.w3.org/TR/accname-1.1)。

### <a name="accessibility-evaluation-resources"></a>辅助功能评估资源

辅助功能评估资源是 W3C 提供的多页资源，它概述了评估网站辅助功能的不同方法。  有关详细信息，请转到 [辅助功能评估资源](https://www.w3.org/WAI/eval/Overview.html)。

### <a name="assistive-technology-compatibility-tests"></a>辅助技术兼容性测试

测试结果显示不同的内容类型和标准在辅助技术中的行为方式 (AT) 如屏幕阅读器。  有关详细信息，请转到 [辅助技术兼容性测试](http://www.powermapper.com/tests)。

### <a name="building-accessible-websites-just-got-a-lot-easier"></a>构建易于访问的网站变得容易得多

此 .NET Web 开发和工具博客帖子介绍Visual Studio扩展 [Web 辅助功能检查器](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebAccessibilityChecker)。  有关详细信息，请转到 [“构建辅助网站”会变得容易得多](https://devblogs.microsoft.com/aspnet/building-accessible-websites-just-got-a-lot-easier)。

### <a name="core-accessibility-api-mappings-11"></a>核心辅助功能 API 映射 1.1

此 W3C 映射文档介绍如何向辅助功能 API 公开 Web 内容语言的语义。  有关详细信息，请转到 [Core 辅助功能 API 映射 1.1](https://www.w3.org/TR/core-aam-1.1)。

### <a name="easy-checks--a-first-review-of-web-accessibility"></a>轻松检查 – 首次查看 Web 辅助功能

WAI 提供的一系列快速检查可帮助你了解网页的辅助功能。  有关详细信息，请转到 [简易检查 - Web 辅助功能的首次评审](https://www.w3.org/WAI/eval/preliminary.html)。

### <a name="how-to-meet-wcag-20"></a>如何满足 WCAG 2.0

快速参考 Web 内容辅助功能指南 (WCAG) 2.0 要求 (成功标准) 和技术。  有关详细信息，请转 [到“如何满足 WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref)”。

### <a name="html-accessibility-api-mappings-10"></a>HTML 辅助功能 API 映射 1.0

此 W3C 映射文档介绍 HTML5.1 元素和属性如何映射到平台辅助功能 API。  有关详细信息，请转到 [HTML 辅助功能 API 映射 1.0](https://www.w3.org/TR/html-aam-1.0)。

### <a name="quick-tips"></a>快速使用技巧

[A11Y Project](http://a11yproject.com)提供的辅助功能快速 Web 开发提示列表。  有关详细信息，请转到[快速使用技巧](http://a11yproject.com#Quick-tips)。

### <a name="site-scan"></a>站点扫描

Microsoft Edge Dev中心的站点扫描工具检查过期库、布局问题和辅助功能问题。  有关详细信息，请转到 [“站点扫描](https://developer.microsoft.com/en-us/microsoft-edge/tools)”。<!-- temp keep /en-us, delete it later when omitting it ends up at right url -->

### <a name="techniques-for-wcag-20"></a>WCAG 2.0 技术

W3C 提供的技术，为 Web 开发人员提供有关满足 [WC) AG (2.0 成功标准的 Web 内容辅助功能指南](https://w3.org/TR/WCAG20) 的指导。  有关详细信息，请转到 [WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/Overview.html) 技术。

### <a name="tips-on-developing-for-web-accessibility"></a>有关开发 Web 辅助功能的使用技巧

使用技巧从 W3C 开发残疾人更容易访问的 Web 内容。  有关详细信息，请转到[有关开发 Web 辅助功能的使用技巧](https://w3.org/WAI/gettingstarted/tips/developing.html)。

### <a name="wai-aria-authoring-practices-11"></a>WAI-ARIA 创作实践 1.1

W3C 提供的文档，让读者了解如何使用 WAI-ARIA 1.1，并建议使用 WAI-ARIA 角色、状态和属性访问小组件、导航和行为的方法。  有关详细信息，请转到 [WAI-ARIA 创作实践 1.1](http://w3c.github.io/aria-practices)。

### <a name="wai-guidelines-and-techniques"></a>WAI 准则和技术

WAI 制定的一系列 Web 辅助功能指南和标准。  有关详细信息，请转到 [WAI 准则和技术](https://w3.org/WAI/guid-tech.html)。

### <a name="web-accessibility-evaluation-tools-list"></a>Web 辅助功能评估工具列表

Web 辅助功能评估工具列表，以帮助确定网站是否符合辅助功能准则。  有关详细信息，请转到 [Web 辅助功能评估工具列表](https://www.w3.org/WAI/ER/tools/index.html)。

### <a name="web-accessibility-perspectives-explore-the-impact-and-benefits-for-everyone"></a>Web 辅助功能透视：探索每个人的影响和好处

W3C 提供的一系列简短情景视频，内容涉及辅助功能的影响和每个人的优势。  有关详细信息，请转到 [Web 辅助功能视角：探索每个人的影响和好处](https://w3.org/WAI/perspectives)。
