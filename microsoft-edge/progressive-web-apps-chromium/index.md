---
title: 渐进式 Web 应用 （PWA） 概述
description: 渐进式 Web (PBA) 在 Windows 10 或更高版本上运行。  作为 Web 开发人员，以下是您需要了解的关于 PWA 的所有信息。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进 Web 应用、PWA、Edge、JavaScript、UWP、Microsoft Store
ms.date: 11/17/2021
ms.openlocfilehash: cd72fa246ea50b56d3df3e255bb9dab0c661e5c0
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12287064"
---
# <a name="overview-of-progressive-web-apps-pwas"></a>渐进式 Web 应用 （PWA） 概述

渐进式 Web (PBA) 提供对开放 Web 技术的访问权限，以提供跨平台互操作性。  PWA 为用户提供了针对其设备自定义的类似应用的体验。

PWA 是一些网站**[](https://alistapart.com/article/understandingprogressiveenhancement)**，其功能逐渐增强，如安装在支持平台上的本机应用，同时与其他浏览器上的常规网站一样运行。

网站质量PWA Web 和已编译应用**的最佳组合**。 PBA 在浏览器（如网站）中运行。  但是，PWA 也有权访问应用功能;例如：
*  PWA脱机时，设备仍可运行。
*  可以在操作系统上安装 PWA。
*  PWA 支持推送通知和定期更新。
*  PWA 可以访问硬件功能。

安装后，PWA**与 Windows 上的其他应用Windows。**  例如：
*  A PWA can be added to the Start Menu.
*  可以将PWA固定到任务栏。
*  PWA 可以处理文件。
*  PBA 可以在用户登录时运行。
*  可以将**PWA**提交到 Microsoft Store数百万Windows用户可以发现并轻松地将它们与其他 Windows 应用一起安装。

PWA 与 **网站具有相同的范围**：
*  PBA 可通过搜索引擎编制索引。
*  可以将PWA链接至的项。
*  a PWA can work on all devices， from a single codebase.

PBA 的**** 跨平台开发成本比编译的应用要低得多，这些应用需要针对每个平台使用特定代码库，例如适用于 Android、iOS 和每个桌面操作系统的单独代码库。


<!-- ====================================================================== -->
## <a name="characteristics-of-a-progressive-web-app-pwa"></a>渐进式 Web 应用应用 (PWA) 

功能齐全的渐进式 Web 应用为用户提供了以下优势。

| 特征 | 描述 |
| --- | --- |
| [可发现](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Discoverable) | 该应用从 Web 搜索结果和支持的应用商店中可发现。 |
| [可安装](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Installable) | 从主屏幕、"开始"菜单和任务栏固定并启动应用。 |
| [重新参与](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Re-engageable) | 应用可以接收推送通知，即使应用不活动。 |
| [与网络无关](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Network_independent) | 应用在脱机和低网络条件下工作。 |
| [渐进](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Progressive) | 应用的用户体验通过设备功能向上或向下扩展。 |
| [保险箱](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Safe) | 该应用提供安全的 HTTPS 终结点和其他用户安全措施。 |
| [响应](https://developer.mozilla.org/Apps/Progressive/Advantages#Responsive) | 应用适应用户的屏幕大小或方向和输入方法。 |
| [可链接](https://developer.mozilla.org/Apps/Progressive/Advantages#Linkable) | 通过标准链接共享和启动应用。 |


<!-- ====================================================================== -->
## <a name="pwas-on-desktop"></a>桌面上的 PWA

渐进式 Web (PBA) 并不限于在移动主屏幕上显示网站。 PWA 基于标准、跨浏览器、Web 技术，可允许安装它们，并可以在许多不同的环境中运行。

在几年中，桌面浏览已增长，并且桌面计算仍然是许多用户的主要生产力环境。  PWA 可以在继承该环境优势的桌面操作系统上提供完全定制的可安装体验。  但是，PWA 仍通过支持浏览器内和移动体验的相同代码和服务器跨平台工作。

Microsoft Edge 和 Windows 添加了许多新的 Web 功能和特性。  这些新 Web 开发功能提供了构建与桌面操作系统深度集成沉浸式体验的很好的机会。  仅使用 Web 技术可确保你的应用在其他浏览器、操作系统和设备中运行。

您可能完全不需要使用专有技术，因为 Web 已开发处理应用的许多方面的功能，例如：
*  文件系统
*  视频
*  音频
*  高性能代码
*  数据库
*  USB
*  蓝牙

使用PWA，可以使用在网站、移动应用和桌面应用之间共享的单个基本代码， (操作系统) 。  通过使用跨平台共享的单个基本代码，您可以降低开发成本。  你的应用也可以发布在 Microsoft Store，以便用户Windows和安装它更熟悉和可信。

详细了解[PWA 如何与 Windows 集成](ux.md)。


<!-- ====================================================================== -->
## <a name="bridging-the-gap-between-web-and-desktop-apps"></a>弥补 Web 应用和桌面应用之间的空白

Microsoft Edge内置了许多新功能，这些功能可以使 Web 应用在桌面平台上更加集成。  这些功能跨 Web 和桌面平台提供了更具吸引力的体验。  使用渐进 Web 应用 (PA) ，您可以：
*   处理文件。
*   与其他应用共享内容。
*   访问剪贴板。
*   同步数据并在后台提取资源。
*   访问设备硬件，蓝牙和 USB。
*   将内容存储在数据库中。
*   利用硬件加速图形。
*   使用 CSS 布局、动画和筛选器创建高级设计。
*   使用 WebAssembly 运行近编译的性能代码。

现在，使用 Web 技术无法执行很多工作。  借助Microsoft Edge，桌面上的 PWA 可以充分利用 Web 技术，以交付用户期望桌面应用执行哪些操作。

有关 [PWA 可以](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition) 执行哪些功能的信息，请参阅向 PWA 提供一些信息。


<!-- ====================================================================== -->
## <a name="the-microsoft-store"></a>the Microsoft Store

由于渐进式 Web (PA) 与[Microsoft Store](https://www.microsoft.com/store/apps/windows)中其他应用一样，因此用户可以与它们完全互动（从发现、安装到执行）而无需<!-- em dashes--> 曾经打开浏览器。

the Microsoft Store app is the most used app on PC.  该Microsoft Store为用户提供了可信赖且熟悉的安装应用的体验。  此外，你可以查看详细的使用情况统计信息和图表，以便你了解应用中Microsoft Store方式。

了解如何将[你的PWA发布到Microsoft Store。](how-to/microsoft-store.md)


<!-- ====================================================================== -->
## <a name="success-stories"></a>成功案例

使用渐进的 Web App (PWA) 技术是使应用安全、可发现、**** 可链接****、易于安装和**** 更新、响应**** 迅速且独立于网络的一种******很好的方法**。  许多企业都成功使用 PBA。  例如：

*   该百PWA每天增加两次活动用户。  桌面上的订单率几乎与移动 ([源) 。](https://twitter.com/davidbrunelle/status/993960071406080000)
*   Trivago 发现向主屏幕添加其PWA用户增加了 150%。  预订增加导致到酒店产品/服务（源产品/服务）的 ([增加了](https://www.thinkwithgoogle.com/intl/en-gb/marketing-strategies/app-and-mobile/trivago-embrace-progressive-web-apps-as-the-future-of-mobile/) 97) 。
*   Tinder 使用其技术将负载时间从 11.91 秒剪切到 4.68 PWA。  该应用比已编译的 Android 应用小 90%， ([源) 。](https://medium.com/@addyosmani/a-tinder-progressive-web-app-performance-case-study-78919d98ece0)

在"统计数据"网站上PWA[成功](https://www.pwastats.com/)案例。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [MDN Web](https://developer.mozilla.org/Apps/Progressive) Docs 的渐进 Web 应用。
*  [Microsoft Build 2020 PWA会话](https://www.youtube.com/watch?v=y4p_QHZtMKM)
*  [百万亿美元 PBA](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition)
*  [渐进式 Web 应用的渐进路线图](https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app)
*  [使用渐进 Web 应用的脱机 POS](https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895)
*  [PWA问答&](https://www.aaron-gustafson.com/notebook/pwa-qa)
*  [Web 上的百年](https://joreteg.com/blog/betting-on-the-web)
*  [命名渐进式 Web 应用](https://fberriman.com/2017/06/26/naming-progressive-web-apps)
*  [设计和生成不带框架的渐进式 Web (第 1) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1)
*  [设计和生成不带框架的渐进式 Web (第 2 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2)
*  [设计和生成不带框架的渐进式 Web (第 3 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3)
*  [什么是良好的渐进式 Web 应用？](https://web.dev/pwa-checklist)
