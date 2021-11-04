---
description: 渐进式 Web 应用在本机或Windows 10运行。  下面是作为 Web 开发人员需要知道的所有内容。
title: 渐进式 Web 应用 （PWA） 概述
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/10/2021
ms.topic: article
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用，PWA、Edge、JavaScript、UWP、Microsoft Store
ms.openlocfilehash: 3c6fd0f09de51429b3b11a591d5d331bac1ab8b6
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12157507"
---
# <a name="overview-of-progressive-web-apps-pwas"></a>渐进式 Web 应用 （PWA） 概述

<!-- preserve trailing spaces -->

**[渐进式 Web](https://developer.mozilla.org/Apps/Progressive)** (PBA) 提供对开放 Web 技术的访问权限，实现跨平台互操作性，并为用户提供为设备自定义的类似应用的体验。

PWA 是一些网站 **[，其](https://alistapart.com/article/understandingprogressiveenhancement)** 功能逐渐增强，其功能与支持平台上已安装的应用类似，与其他浏览器上的常规网站类似。

网站质量PWA Web 和已编译应用**的最佳组合**。 PWA 在浏览器（如网站）中运行，但有权访问应用功能（如脱机工作的功能）安装在操作系统上、支持推送通知和定期更新、访问硬件功能等。

安装后 **，PWA 与 Windows 上的其他应用Windows。** 它们可以添加到"开始"菜单、固定到任务栏、处理文件、在用户登录时运行等。

PBA**还可以提交到**Microsoft Store数百万Windows用户可以发现并轻松地将它们与其他 Windows 应用一起安装。


<!-- ====================================================================== -->
## <a name="characteristics-of-a-pwa"></a>项目PWA

PWA 与网站具有相同的范围：它们可以由搜索引擎编制索引，可以链接到同一基本代码的所有设备，并且可在所有设备上运行。 因此，与需要 Android、iOS 和各种桌面操作系统的特定基本代码的已编译应用比，它们的开发成本要低得多。

<!--
In the below table, keep two trailing spaces after each image line and after each heading line, to keep card elements tight but not concatenated.
Similar table: [Introduction to Microsoft Edge WebView2](..\webview2\index.md#webview2-benefits)
-->

:::row:::
    :::column:::
        :::image type="icon" source="./media/i_search-small.png":::  
        **[可发现](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Discoverable)**  
        从 Web 搜索结果和支持的应用商店
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_package-small.png":::  
        **[可安装](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Installable)**  
        从主屏幕、"开始"菜单、任务栏等固定和启动
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_push-notification-small.png":::  
        **[重新参与](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Re-engageable)**  
        发送推送通知，即使应用不处于活动状态
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        :::image type="icon" source="./media/i_offline-small.png":::  
        **[与网络无关](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Network_independent)**  
        在脱机和低网络条件下工作
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_progressive-small.png":::  
        **[渐进](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Progressive)**  
        体验通过 (功能) 向上或向下扩展
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_security-small.png":::  
        **[保险箱](https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Safe)**  
        提供安全的 HTTPS 终结点和其他用户安全措施
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        :::image type="icon" source="./media/i_responsive-small.png":::  
        **[响应](https://developer.mozilla.org/Apps/Progressive/Advantages#Responsive)**  
        适应用户的屏幕大小或方向和输入方法
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_link-small.png":::  
        **[可链接](https://developer.mozilla.org/Apps/Progressive/Advantages#Linkable)**  
        从标准超链接共享和启动
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<!-- In the above table, keep two trailing spaces after each image line and after each heading line, to keep card elements tight but not concatenated. -->


<!-- ====================================================================== -->
## <a name="pwas-on-desktop"></a>桌面上的 PWA

PBA 不限于在移动主屏幕上显示网站。 PWA 基于标准、跨浏览器、Web 技术，可允许安装它们，并可以在许多不同的环境中运行。

在几年中，桌面浏览已增长，并且桌面计算仍然是许多用户的主要生产力环境。 幸运的是，PWA 可以在继承该环境优势的桌面操作系统上提供完全定制的可安装体验，同时仍可从支持浏览器内和移动体验的相同代码和服务器跨平台工作。

借助 Microsoft Edge 和 Windows 中的许多新 Web 功能和新功能，可以构建与桌面操作系统深度集成且沉浸式体验。 仅使用 Web 技术还可确保你的应用在其他浏览器、操作系统和设备中运行。

你可能完全不需要使用专有技术，因为 Web 已经发展了处理文件系统[](#bridging-the-gap-between-web-and-desktop-apps)、视频、音频、高性能代码、数据库、USB、蓝牙等功能。

通过跨操作系统在网站、移动应用和桌面应用之间共享 (，) 降低开发成本。 你的应用还可以发布在 Microsoft Store[上，](#the-microsoft-store)以便用户Windows和安装它更熟悉和可信。

详细了解[PWA 如何与 Windows](./ux.md)集成。


<!-- ====================================================================== -->
## <a name="bridging-the-gap-between-web-and-desktop-apps"></a>弥补 Web 应用和桌面应用之间的空白

内置了许多新的 Web 功能Microsoft Edge这些功能可以使你的应用在桌面上更加集成，并为用户提供极具吸引力的体验。

借助 PBA，你可以：

*   处理文件。
*   与其他应用共享内容。
*   访问剪贴板。
*   同步数据并在后台提取资源。
*   访问设备硬件，如 蓝牙 和 USB。
*   将内容存储在数据库中。
*   利用硬件加速图形。
*   使用 CSS 布局、动画和筛选器创建高级设计。
*   使用 WebAssembly 运行近编译的性能代码。

目前，使用 Web 技术无法执行很多操作，由于 Microsoft Edge，桌面上的 PWA 可以充分利用这一点，从而提供用户期望桌面应用能够执行哪些操作。

有关 [PWA 可以](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition) 执行哪些功能的信息，请参阅向 PWA 提供一些信息。


<!-- ====================================================================== -->
## <a name="the-microsoft-store"></a>The Microsoft Store

由于 PWA 与 Microsoft Store 中[](https://www.microsoft.com/store/apps/windows)其他应用一样，因此用户可以从发现、安装到执行完全参与它们，而无需打开浏览器。

作为电脑中最常用的应用，Microsoft Store为用户安装应用提供可信且熟悉的体验。 此外，你可以查看详细的使用情况统计信息和图表，以便你了解应用中Microsoft Store方式。

了解如何将[你的PWA发布到Microsoft Store。](./how-to/microsoft-store.md)


<!-- ====================================================================== -->
## <a name="success-stories"></a>成功案例

使用PWA技术是使应用安全、可发现、可链接、易于**** 安装和更新****、响应迅速**** 且**独立于网络的一种很好的方法**。 **** **** 许多企业都使用 PWA 并获得成功。

*   每天PWA用户数增加两次，桌面版订单数几乎与移动源 ([的](https://twitter.com/davidbrunelle/status/993960071406080000)) 。
*   Trivago 发现将 PWA 添加到主屏幕的人增加了 150%，参与度增加导致到酒店产品/ (的点击量增加了 97%。) 。 [](https://www.thinkwithgoogle.com/intl/en-gb/marketing-strategies/app-and-mobile/trivago-embrace-progressive-web-apps-as-the-future-of-mobile/)
*   Tinder 使用其 PWA 将加载时间从 11.91 秒剪切到 4.68 秒，并且应用比编译的 Android 应用 (源) [](https://medium.com/@addyosmani/a-tinder-progressive-web-app-performance-case-study-78919d98ece0)小 90%。

在"统计数据"网站上PWA[成功](https://www.pwastats.com/)案例。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [Microsoft Build 2020 PWA会话](https://www.youtube.com/watch?v=y4p_QHZtMKM)
*   [百万亿美元 PBA](https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition)
*   [渐进式 Web 应用的渐进路线图](https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app)
*   [使用渐进 Web 应用的脱机 POS](https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895)
*   [PWA问答&](https://www.aaron-gustafson.com/notebook/pwa-qa)
*   [Web 上的百年](https://joreteg.com/blog/betting-on-the-web)
*   [命名渐进式 Web 应用](https://fberriman.com/2017/06/26/naming-progressive-web-apps)
*   [设计和生成不带框架的渐进式 Web (第 1) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1)
*   [设计和生成不带框架的渐进式 Web 应用 (第 2) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2)
*   [设计和生成不带框架的渐进式 Web (第 3 部分) ](https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3)
*   [什么是良好的渐进式 Web 应用？](https://web.dev/pwa-checklist)


<!-- ====================================================================== -->
<!-- Links -->
