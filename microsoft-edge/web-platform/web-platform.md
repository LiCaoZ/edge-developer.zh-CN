---
title: Web 平台概述
description: 测试即将进行的更改，这些更改可能会影响网站与 Microsoft Edge 的兼容性。  将用户从 Internet Explorer。  设置跟踪防护。  检测Microsoft Edge网站中的内容。 通过Windows 11客户端User-Agent检测数据。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 02/14/2022
ms.openlocfilehash: 96722cd6188a52c175215ec9ef75c4713e31a7cc
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433435"
---
# <a name="web-platform-overview"></a>Web 平台概述

以下是开发 Web 平台（特别是针对 Web 平台）的网站Microsoft Edge：

*  测试即将进行的更改，这些更改可能会影响网站与Microsoft Edge。
*  将用户从Microsoft Edge移动到Internet Explorer。
*  在 Microsoft Edge 中配置跟踪Microsoft Edge。
*  检测Microsoft Edge网站中的内容。
*  使用Windows 11客户端提示检测User-Agent。
*  自定义密码 **显示** 按钮。

下面介绍了开发 Web 平台的这些方面。


<!-- ====================================================================== -->
## <a name="site-compatibility-impacting-changes-coming-to-microsoft-edge"></a>Microsoft Edge 中影响网站兼容性的更改

本文列出了项目更改计划Microsoft Edge与Chromium项目之间的差异，以及团队Microsoft Edge跟踪的显著变化。

Web 平台是一组用于构建网页的技术，包括 HTML、CSS、JavaScript 和许多其他开放标准。  Web 平台不断发展以改进用户体验、安全性和隐私。  在某些情况下，更改可能会影响现有网页的功能。

请参阅[即将对网站进行的网站兼容性Microsoft Edge](site-impacting-changes.md)。


<!-- ====================================================================== -->
## <a name="move-users-to-microsoft-edge-from-internet-explorer"></a>将用户从Internet Explorer移动到Microsoft Edge

许多新式网站的设计与 Internet Explorer 不兼容。  当 Internet Explorer 用户访问不兼容的公共网站时，网站可能会指示用户该网站与 Internet Explorer 不兼容，并且用户必须切换到更现代浏览器才能使用该网站。

为了最大限度地减少中断，Microsoft Edge自动重定向用户的新功能。  当Internet Explorer用户转到与网站不兼容Internet Explorer时，Windows会自动将用户重定向到Microsoft Edge。  仅重定向属于"需要"_Microsoft Edge的网站。_

请参阅[将用户移动到Microsoft Edge Internet Explorer](ie-to-microsoft-edge-redirection.md)。


<!-- ====================================================================== -->
## <a name="tracking-prevention-in-microsoft-edge"></a>Microsoft Edge 中的跟踪防护

跟踪防护功能Microsoft Edge跟踪器访问基于浏览器的存储和网络的功能，从而防止用户进行联机跟踪。

跟踪防护功能专为实现浏览器Microsoft Edge承诺而构建，同时还确保__ 默认情况下对网站兼容性或 Web 经济适用性没有影响。

请参阅[跟踪Microsoft Edge](tracking-prevention.md)。


<!-- ====================================================================== -->
## <a name="detect-microsoft-edge-from-your-website"></a>从网站检测 Microsoft Edge

Microsoft Edge网站检索用户代理信息。  您可以使用用户代理信息为每个用户的浏览器正确呈现网页。  浏览器为网站提供用于检测浏览器信息（如品牌、版本号和主机操作系统）的机制。

*  **用户代理客户端提示** 是检索浏览器信息的改进机制。

*  **用户代理字符串是** 旧版的;它们已过时，并且具有导致网站兼容性问题的历史记录。

你可能希望基于用户的浏览器为用户提供不同的体验。  例如，如果包含有关如何配置浏览器或Microsoft Edge浏览器以用于您的网站的步骤，您可能需要检测浏览器，然后显示相应的内容。

请参阅[检测Microsoft Edge网站中的内容](user-agent-guidance.md)。


<!-- ====================================================================== -->
## <a name="detect-windows-11-using-user-agent-client-hints"></a>使用用户代理客户端提示检测 Windows 11

通过使用 UA-CH Windows 11 UA-CH Windows 10客户端User-Agent，网站可以区分 (用户) 。  浏览器User-Agent客户端提示格式向网站提供用户代理信息。

网站可以使用从浏览器发送的用户代理信息检测以下信息：
*  浏览器品牌。
*  浏览器版本号。
*  运行浏览器的设备平台。

网站有两种访问用户代理信息的方法：

*  User-Agent旧版 (字符串) 。
*  User-Agent客户端提示 (推荐) 。

请参阅[使用Windows 11客户端User-Agent检测应用](how-to-detect-win11.md)。


<!-- ====================================================================== -->
## <a name="customize-the-password-reveal-button"></a>自定义“密码显示”按钮

其中`password`输入控件Microsoft Edge密码**显示**按钮。  若要确保正确输入**** 密码，用户可以`Alt`+`F8`单击密码显示按钮或按 ，以显示密码字段中的字符。  你可以删除密码 **显示** 控件，或自定义控件样式。

请参阅 [自定义密码显示按钮](password-reveal.md)。
