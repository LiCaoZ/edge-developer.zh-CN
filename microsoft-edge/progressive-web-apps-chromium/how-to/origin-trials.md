---
title: 实验功能和来源试用
description: 了解如何在 PWA测试实验性网站Microsoft Edge并注册站点源试用版，以便与用户一起在生产中使用这些功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/15/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进 Web 应用， PWA， Microsoft Edge， 实验， 源试用版
ms.openlocfilehash: fb72f0ebdd35c308c1d88714cf7b7f41ba015e17
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087089"
---
# <a name="experimental-features-and-origin-trials"></a>实验功能和来源试用

PWA中的某些Microsoft Edge仍处于实验阶段。 实验功能可通过两种方式使用：

*   通过启用 Microsoft Edge。
*   在源试用版中注册网站，以便与用户一起测试生产中的功能。


<!-- ====================================================================== -->
## <a name="toggle-experimental-features"></a>切换实验功能

打开或关闭实验性功能：

1.  打开 Microsoft Edge。
1.  转到 `edge://flags` 。
1.  导航到相关实验。
1.  选择实验说明旁边的下拉菜单，然后选择启用以打开该功能，**** 或选择**禁用以将其**关闭。

    :::image type="content" source="../media/turn-on-experimental-flag.png" alt-text="选择启用以打开实验。" lightbox="../media/turn-on-experimental-flag.png":::


<!-- ====================================================================== -->
## <a name="enroll-your-site-in-an-origin-trial"></a>在源试用版中注册网站

Microsoft Edge有时使用源试用版来测试特定域或网站的功能。 你可能想要对网站使用源试用版来应用特定功能。 如果你是网站所有者，你可以注册源试用版。 源试用版向访问你的Microsoft Edge的用户提供一定比例的功能。

有关源试用版详细信息，请参阅Microsoft Edge[源试用版开发人员控制台][MicrosoftDeveloperMicrosoftEdgeOriginTrials]。


<!-- ====================================================================== -->
## <a name="features-that-are-available-to-test"></a>可供测试的功能

以下列表介绍了实验性 Web 应用功能，这些功能可用于测试和验证Microsoft Edge。 若要启用这些功能，请转到切换 [实验功能](#toggle-experimental-features)。

| 功能 | 平台 |
|:--- |:--- |
| [URI 协议处理][FeatureProtocolHandling] | Windows 和 Linux |
| [URL 链接处理][FeatureUrlHandling] | Windows |
| [适用于桌面应用的窗口控件覆盖层][FeatureWindowControlsOverlay] | 全部 |
| [文件处理][FeatureFileHandling] | 所有桌面 |

<!-- Links -->

[MicrosoftDeveloperMicrosoftEdgeOriginTrials]: https://developer.microsoft.com/microsoft-edge/origin-trials "源试用版|Microsoft Edge开发人员"
[FeatureWindowControlsOverlay]: ./window-controls-overlay.md "显示标题栏中的内容|Microsoft Docs"
[FeatureUrlHandling]: ./handle-urls.md "处理渐进式 Web 应用应用程序中|Microsoft Docs"
[FeatureProtocolHandling]: ./handle-protocols.md "在渐进式 Web 应用应用程序中处理|Microsoft Docs"
[FeatureFileHandling]: ./handle-files.md "在渐进式 Web 应用应用程序中处理|Microsoft Docs"
