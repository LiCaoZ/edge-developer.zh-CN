---
title: 准备将扩展从清单 V2 更新到 V3
description: 将扩展从清单 V2 更新到 V3。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/26/2021
ms.openlocfilehash: 05f16dc7f039bd3ae30acc8a64b1823865f78adc
ms.sourcegitcommit: 89516f583a23b3df03aaddd73a67b1897be70e27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2022
ms.locfileid: "12551827"
---
# <a name="prepare-to-update-your-extensions-from-manifest-v2-to-v3"></a>准备将扩展从清单 V2 更新到 V3

本文列出了作为清单 V3 的一部分实现的重要更改，该 V3 是Chromium扩展平台的下一个版本。  有关将扩展迁移到清单 V3 的指南，请参阅 [清单 V3 - Chrome 开发人员概述](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-overview/)。


<!-- ====================================================================== -->
## <a name="remotely-hosted-code"></a>远程托管代码

目前，扩展代码的某些部分是远程托管的，在验证过程中不会作为扩展包的一部分包含在内。  虽然这提供了在不将扩展重新提交到存储区的情况下更改代码的灵活性，但安装后可以利用代码。  为了确保[Microsoft Edge加载项](https://microsoftedge.microsoft.com/addons)列出已验证的扩展，Microsoft Edge扩展团队禁止扩展使用远程托管代码。  此更改使扩展更安全。

开发人员需要打包并提交扩展使用的所有代码进行验证。  或者，可以在[沙盒环境中](https://developer.chrome.com/docs/extensions/mv2/sandboxingEval)使用该`eval()`函数。


<!-- ====================================================================== -->
## <a name="run-time-host-permissions"></a>运行时主机权限

在安装时，扩展可以请求访问所有站点和内容的权限。  这些权限允许扩展在最小干预下运行，因此会给用户隐私和安全带来风险。  为了提高透明度，Microsoft Edge扩展团队提供了允许用户允许或限制在运行时访问网站的控件。


<!-- ====================================================================== -->
## <a name="cross-origin-requests-in-content-scripts"></a>内容脚本中的跨源请求

目前，内容脚本可以请求访问任何源，包括网站不允许的源。  此行为会破坏跨源原则。  今后，Microsoft Edge扩展团队要求内容脚本具有与向其中注入脚本的网页相同的权限。  此要求消除了潜在的安全漏洞。

若要执行跨源请求，需要使用后台脚本将响应中继回内容脚本。  这些更改可用，并且位于标志后面。  有关详细信息，请参阅 [Chrome 扩展内容脚本中对跨源请求的更改](https://www.chromium.org/Home/chromium-security/extension-content-script-fetches)。


<!-- ====================================================================== -->
## <a name="web-request-api"></a>Web 请求 API

Microsoft Edge扩展团队通过[声明性 Net 请求 API](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest) 替换 [Web 请求 API](https://developer.chrome.com/docs/extensions/reference/webRequest)，但我们继续保留 Web 请求 API 的观察功能。  我们建议仅使用声明性 Net 请求 (DNR) API，而不是 Web 请求 API，但某些特定方案除外，其中扩展需要 Web 请求 API 的观察功能。

此更改将对使用功能丰富的声明性功能的扩展产生积极影响。  随着更多扩展转换为声明性 Net Request API，此更改将改善用户隐私，从而有助于信任扩展的使用。

企业可以继续对通过企业策略管理的扩展使用 Web 请求 API 的阻止行为。  有关扩展策略的详细信息，请参阅 _Microsoft Edge - 策略_中的[扩展](/deployedge/microsoft-edge-policies#extensions)。


<!-- ====================================================================== -->
## <a name="background-service-workers"></a>后台服务工作者

服务工作者可以在Microsoft Edge的 Canary 预览频道中进行测试。  若要将扩展从后台页面迁移到服务工作者，请参阅 [从后台页面迁移到服务辅助角色](https://developer.chrome.com/docs/extensions/mv3/migrating_to_service_workers)。  Microsoft Edge扩展团队正在评估和调查此更改对开发人员和用户的影响。


<!-- ====================================================================== -->
## <a name="when-are-these-changes-available-in-microsoft-edge"></a>这些更改何时可用Microsoft Edge

当前的声明性 Net 请求 API 实现在“稳定”和“Beta”通道Microsoft Edge提供。  请测试更改并提供反馈。

Microsoft Edge扩展团队在我们的博客上发布更新。  可以通过 Microsoft Tech Community提供有关更改的反馈;请参阅[清单 V3 更改现已在Microsoft Edge中提供](https://techcommunity.microsoft.com/t5/articles/manifest-v3-changes-are-now-available-in-microsoft-edge/m-p/1780254)。
