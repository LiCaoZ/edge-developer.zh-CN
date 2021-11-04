---
description: 提供可能会影响站点兼容性的高影响更改的摘要
title: Microsoft Edge 中影响网站兼容性的更改
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/20/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， 兼容性， Web 平台
ms.openlocfilehash: ae6f19f7ef6259850cc628c7cee36ae1cfa7c165
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12155316"
---
# <a name="site-compatibility-impacting-changes-coming-to-microsoft-edge"></a>Microsoft Edge 中影响网站兼容性的更改

Web 平台是一组用于构建网页的技术。  这些技术包括 HTML、CSS、JavaScript 和许多其他开放标准。  Web 平台不断发展以改进用户体验、安全性和隐私。  在某些情况下，更改可能会影响现有网页的功能。  有关即将推出的项目 Web Chromium更改的信息，请导航到 Chrome[平台状态发布时间线](https://www.chromestatus.com/features/schedule)。

Microsoft Edge项目对 Web 平台进行几乎所有上游Chromium更改。  原因包括功能和兼容性原因。  Microsoft 保持对浏览器的完全Microsoft Edge，并可以延迟或拒绝更改。  该Microsoft Edge团队决定更改是否对浏览器用户的好处。  下表中Microsoft Edge计划Chromium时间或行为更改的功能区域。  该表还突出显示了团队正在跟踪Microsoft Edge影响大的更改。

经常查看本文。  当Microsoft Edge发展、日程表稳定以及宣布新更改时，团队会更新本文。

| “更改” | 稳定渠道 | 实验 | 其他信息 |
|:--- |:--- |:--- |:--- |
| 禁止在页面 `XmlHttpRequest` 内同步解除 | [Chrome+1](#release-comments) (Edge v83)  |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  匹配 Chrome，Microsoft Edge提供在 Edge v88 之前关闭此更改的组策略。  有关详细信息，包括 Google 为此更改计划的时间线，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/4664843055398912)。  |
| 显示通知权限请求的细微提示 | Edge v84 |  | 安静通知请求在使用 或 API 请求的网站通知权限的地址栏中显示一个细微的请求图标，以替换完整或 `Notifications` `Push` 标准权限飞出提示 UI。  此功能当前为所有用户启用。  若要选择退出安静通知请求，请导航到 `edge://settings/content/notifications` 。  将来，Microsoft Edge团队可能会探索在某些情况下重新启用完整的飞出通知提示。  |
| 关闭 TLS/1.0 和 TLS/1.1 | Edge v84 |  |  |
| Cookie 默认为 `SameSite=Lax` 和 `SameSite=None-requires-Secure` | [Chrome+1](#release-comments) (Edge v86)   | Canary v82，Dev v82 | 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，包括 Google 为此更改计划的时间线，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/5088147346030592)。  |
| 引用者策略：默认为 `strict-origin-when-cross-origin` | [Chrome+1](#release-comments) (Edge v86)   | Canary v79，Dev v79 | 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，包括 Google 为此更改计划的时间线，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/6251880185331712)。  |
| 弃用 AppCache | [Chrome+1](#release-comments) (Edge v86)   |  | 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请导航到 [WebDev 文档](https://web.dev/appcache-removal)。  Microsoft 推出计划弃用计划计划在 Chrome 后的一个版本中发布。  请求 [AppCache OriginTrial 令牌](https://developers.chrome.com/origintrials/#/view_trial/1776670052997660673) 允许站点继续使用已弃用 API，直到 Edge v90。  |
| 阻止第三方 Cookie 时不允许 HTTP 身份验证  | Edge v87  |  | 从 Edge v87 开始，当阻止第三方请求的 Cookie 时，使用 [BlockThirdPartyCookies](/deployedge/microsoft-edge-policies#blockthirdpartycookies) 策略或 中的开关也会禁止 `edge://settings` HTTP 身份验证。 如果托管列表的终结点Enterprise HTTP[](/deployedge/edge-ie-mode-policies#configure-using-the-use-the-enterprise-mode-ie-website-list-policy)身份验证，此更改可能会影响 Internet Explorer 模式站点列表下载。  若要允许将 Cookie 和 HTTP 身份验证同时用于Enterprise站点列表下载，请向[CookiesAllowedForURLs](/deployedge/microsoft-edge-policies#cookiesallowedforurls)策略添加匹配的 URL 模式。  |
| 删除 Adobe Flash | Edge v88  |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请导航到[Adobe Flash Chromium路线图](https://www.chromium.org/flash-roadmap#TOC-Flash-Support-Removed-from-Chromium-Target:-Chrome-88---Jan-2021-)。  |
| 删除 FTP 支持 | Edge v88  | Beta v87 | 在 Edge v88 中，完全删除了 FTP 支持。  此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/6246151319715840)。  具有仍然需要 FTP 支持的网站的企业可以通过将站点配置为使用 [IE](/deployedge/edge-ie-mode)模式来继续使用 FTP。  |
| 自动升级混合内容图像 | Edge v88  |  | 对图像 (安全) HTTP 文件会自动升级到 HTTPS;如果图像无法通过 HTTPS 访问，则图像下载将失败。 组 [策略](/deployedge/microsoft-edge-policies#insecurecontentallowedforurls) 可用于控制此功能。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 有关详细信息，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/4926989725073408)。  |
| 在 TLS 中删除 3DES  | Edge v93  |  | 从 Edge v93 开始，将TLS_RSA_WITH_3DES_EDE_CBC_SHA密码套件的支持。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 有关详细信息，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/6678134168485888)。 此外，在 Edge v93 中，兼容性策略可用于支持需要保留与过时服务器的兼容性的方案。 此兼容性策略将过时，并停止在 Edge v95 中运行。 请确保在此之前更新受影响的服务器。 |
| 弃用 WebRTC 的计划 B SDP 语义 | [Chrome+1](#release-comments) (TBA)   |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 此更改将弃用名为计划 B (SDP) 旧会话描述协议。此 SDP 格式将由统一计划取代，统一计划是一种符合规格且跨浏览器兼容的 SDP 格式。 有关详细信息，请导航到 [Chrome](https://www.chromestatus.com/feature/5823036655665152)平台状态条目 [、PSA：计划 B SDP](https://groups.google.com/g/discuss-webrtc/c/UBtZfawdIAA/m/-UVQQcubBQAJ)弃用和删除的时间线 - 请迁移到统一计划 ，以及 PSA：计划 B 抛出仅限于 [M93 中的 Canary (而不是 ](https://groups.google.com/g/discuss-webrtc/c/DRRAnej3BTE/m/EqIhrLleBgAJ)在 Stable) 中引发。 Microsoft 推出计划弃用计划计划在 Chrome 后的一个版本中发布。 请求 [WebRTC 计划 B 反向源试用令牌](https://developer.chrome.com/origintrials/#/view_trial/3892235977954951169) 允许网站继续使用已弃用 API，直到 Edge v96。 |
| 将专用网络请求限制为保护上下文  | Edge v94  |  | 从 Edge v94 开始，从 internet (访问本地 intranet) 需要通过 HTTPS 传递这些页面。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 有关详细信息，请导航到 [Chrome 平台状态条目](https://chromestatus.com/feature/5436853517811712)。 可使用两个兼容性策略支持需要保留与非安全页面的兼容性的方案：[InsecurePrivateNetworkRequestAllowed](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowed) 和 [InsecurePrivateNetworkRequestAllowedForUrls](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowedforurls)。 |
| 阻止混合内容下载 | Edge v94  |  | HTTPS 页面上将阻止从 HTTP URL 下载文件。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请导航到 [Google 安全博客条目](https://security.googleblog.com/2020/02/protecting-users-from-insecure_6.html)。 |
| 删除跨源子框架 JavaScript 对话框 | [Chrome+1](#release-comments) (Edge v99)   |  | 从 `window.alert` 跨 `window.prompt` 源 iFrame 中删除 、 `window.confirm` 和 。 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请导航到"[意图要删除：跨源子框架 JS 对话框"。](https://groups.google.com/a/chromium.org/g/blink-dev/c/hTOXiBj3D6A/m/JtkdpDd1BAAJ) |

##### <a name="release-comments"></a>发布注释

:::row:::
   :::column span="1":::
      Chrome+1
   :::column-end:::
   :::column span="2":::
      根据用户和开发人员的反馈，指示的功能或更改在 Chrome 后发布一次。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      Chrome 或 Chrome+1
   :::column-end:::
   :::column span="2":::
      根据用户和开发人员的反馈，指示的功能或更改同时提供，或在 Chrome 发布后的一个版本中提供。
   :::column-end:::
:::row-end:::
