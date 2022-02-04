---
title: 准备将扩展从清单 V2 更新到 V3
description: 将扩展从清单 V2 更新到 V3。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/24/2021
---
# <a name="prepare-to-update-your-extensions-from-manifest-v2-to-v3"></a>准备将扩展从清单 V2 更新到 V3

本文列出了作为清单 V3 的一部分实现的重要更改，清单 V3 是下一版本的 Chromium 扩展平台。  有关将扩展迁移到清单 V3 的指南，请参阅 [迁移到清单 V3](https://developer.chrome.com/docs/extensions/mv3/mv3-migration-checklist)。


<!-- ====================================================================== -->
## <a name="remotely-hosted-code"></a>远程托管的代码

目前，扩展代码的某些部分是远程托管的，在验证过程中不会作为扩展包的一部分包含在内。  虽然这提供了在不将扩展重新提交到应用商店的情况下更改代码的灵活性，但安装后可能会利用代码。  为确保加载项[Microsoft Edge](https://microsoftedge.microsoft.com/addons)验证的扩展，Microsoft Edge团队禁止扩展使用远程托管的代码。  此更改使扩展更安全。

开发人员将需要打包并提交扩展使用的所有代码进行验证。  或者，可以在沙 `eval()` 盒环境中使用 [函数](https://developer.chrome.com/docs/extensions/mv2/sandboxingEval)。


<!-- ====================================================================== -->
## <a name="run-time-host-permissions"></a>运行时主机权限

在安装时，扩展可能会请求访问所有网站和内容所需的全面权限。  这些权限允许扩展在最小干预下运行，因此存在用户隐私和安全性风险。  为了提高透明度，Microsoft Edge扩展团队提供了允许用户在运行时允许或限制对网站的访问的控件。


<!-- ====================================================================== -->
## <a name="cross-origin-requests-in-content-scripts"></a>内容脚本中的跨源请求

现在，内容脚本可以请求访问任何源，包括网站不允许的源。  该行为会破坏跨源原则。  今后，Microsoft Edge扩展团队需要内容脚本具有与将脚本注入到的网页相同的权限。  此要求会关闭潜在的安全隐患。

若要执行跨源请求，你需要使用后台脚本将响应中继回内容脚本。  这些更改可用，并且隐藏在标志后面。  有关详细信息，请参阅 [Changes to Cross-Origin Requests in Chrome Extension Content Scripts](https://www.chromium.org/Home/chromium-security/extension-content-script-fetches)。


<!-- ====================================================================== -->
## <a name="web-request-api"></a>Web 请求 API

Microsoft Edge扩展团队将 [Web 请求 API](https://developer.chrome.com/docs/extensions/reference/webRequest) 替换为声明性 Net [请求 API](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest)，但我们将继续保留 Web 请求 API 的观察功能。  我们建议仅使用声明性 Net 请求 (DNR) API，而不是 Web 请求 API，但扩展需要 Web 请求 API 观察功能的一些特定情况除外。

此更改将对使用功能丰富的声明功能的扩展产生积极的影响。  随着更多扩展过渡到声明性 Net 请求 API，此更改将改善用户隐私，从而有助于信任扩展的使用。

对于通过企业策略管理的扩展，企业可以继续使用 Web 请求 API 的阻止行为。  有关扩展策略详细信息，[请参阅 Microsoft Edge](/deployedge/microsoft-edge-policies#extensions) _- 策略中的扩展_。


<!-- ====================================================================== -->
## <a name="background-service-workers"></a>后台服务工作者

服务工作人员可在 Canary 预览频道中测试Microsoft Edge。  若要将扩展从后台页面迁移到服务工作者，请参阅 [从后台页面迁移到服务工作者](https://developer.chrome.com/docs/extensions/mv3/migrating_to_service_workers)。  开发人员Microsoft Edge团队正在评估并调查此更改对开发人员和用户的影响。


<!-- ====================================================================== -->
## <a name="when-are-these-changes-available-in-microsoft-edge"></a>这些更改何时在Microsoft Edge

当前声明性 Net 请求 API 实现在 Microsoft Edge Stable 和 Beta 渠道中可用。  请测试更改并提供反馈。

Microsoft Edge扩展团队将在我们的博客中发布更新。  可以通过 Microsoft Tech Community 提供有关更改的反馈;请参阅清单 [V3](https://techcommunity.microsoft.com/t5/articles/manifest-v3-changes-are-now-available-in-microsoft-edge/m-p/1780254) 更改现已Microsoft Edge。
