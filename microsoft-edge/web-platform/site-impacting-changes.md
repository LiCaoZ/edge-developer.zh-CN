---
title: Microsoft Edge 中影响网站兼容性的更改
description: 针对可能影响网站兼容性的Microsoft Edge计划进行的高影响更改摘要。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/24/2022
ms.openlocfilehash: 69c81af1dcc66b60757eb605cfa7676e4e1bb301
ms.sourcegitcommit: b2062efd99182cb0b6c3115439fb45838841b276
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497119"
---
# <a name="site-compatibility-impacting-changes-coming-to-microsoft-edge"></a>Microsoft Edge 中影响网站兼容性的更改

本文列出了Microsoft Edge与Chromium项目的更改计划与Microsoft Edge团队特别密切跟踪的高影响更改之间的差异。

Web 平台是用于生成网页的技术集合，包括 HTML、CSS、JavaScript 和许多其他开放标准。  Web 平台不断改进，以改善用户体验、安全和隐私。  在某些情况下，更改可能会影响现有网页的功能。

出于功能和兼容性的原因，Microsoft Edge采用几乎所有Chromium项目对 Web 平台所做的更改。  Microsoft 仍完全控制Microsoft Edge浏览器，并可能推迟或拒绝更改。  Microsoft Edge团队决定更改是否有利于浏览器用户。

有关即将Chromium项目 Web 平台更改的信息，请参阅 [Chrome 平台状态发布时间线](https://www.chromestatus.com/features/schedule)。

请经常查看本文。  随着思维的发展、时间线的巩固和新更改的公布，Microsoft Edge团队将更新本文。


<!-- ====================================================================== -->
## <a name="differences-from-the-chromium-schedule-and-high-impact-changes"></a>与Chromium计划的差异和影响很大的更改

此表列出：
*  Microsoft Edge的推出计划不同于上游Chromium项目的更改。
*  Microsoft Edge团队正在密切跟踪的高影响更改。
<!-- This table doesn't include low-impact changes which are unlikely to have compatibility impact. -->

| “更改” | 稳定渠道 | 实验 | 其他信息 |
| --- | --- | --- | --- |
| 禁止在页面解聘中同步`XmlHttpRequest` | v83 (Chrome+1)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  与 Chrome 匹配，Microsoft Edge提供了一个组策略，用于在 v88 之前关闭此更改。  有关详细信息，包括 Google 针对此更改的计划时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/4664843055398912)。 |
| 显示通知权限请求的微妙提示 | v84 | | 静默通知请求在地址栏中显示一个微妙的请求图标，用于使用 `Notifications` 该或 `Push` API 请求的站点通知权限，替换完整或标准权限浮出提示 UI。  此功能当前已为所有用户启用。  若要选择退出静默通知请求，请参阅 `edge://settings/content/notifications`。  将来，Microsoft Edge团队可能会在某些情况下探索重新启用完整浮出控件通知提示。 |
| 关闭 TLS/1.0 和 TLS/1.1 | v84 | | HTTPS 网站使用的 TLS 协议版本 1.0 和 1.1 现已过时，在现代浏览器中不可用。 |
| Cookie 默认为 `SameSite=Lax` 和 `SameSite=None-requires-Secure` | v86 (Chrome+1)  | Canary v82、Dev v82 | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 针对此更改的计划时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5088147346030592)。 |
| 引用器策略：默认值为 `strict-origin-when-cross-origin` | v86 (Chrome+1)  | Canary v79、Dev v79 | 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，包括 Google 针对此更改的计划时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6251880185331712)。 |
| 弃用 AppCache | v86 (Chrome+1)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [WebDev 文档](https://web.dev/appcache-removal)。  Microsoft 的弃用计划计划在 Chrome 之后的一个版本中进行。  请求 [AppCache OriginTrial 令牌](https://developers.chrome.com/origintrials/#/view_trial/1776670052997660673) 允许站点在 v90 之前继续使用已弃用的 API。 |
| 阻止第三方 Cookie 时不允许 HTTP 身份验证 | v87 | | 从 v87 开始，当第三方请求阻止 Cookie 时，也不允许使用 [BlockThirdPartyCookies](/deployedge/microsoft-edge-policies#blockthirdpartycookies) 策略或切换 `edge://settings`器进行 HTTP 身份验证。  如果托管列表的终结点需要使用 HTTP 身份验证，则此更改可能会影响 [Internet Explorer 模式的Enterprise模式站点列表下载](/deployedge/edge-ie-mode-policies#configure-using-the-use-the-enterprise-mode-ie-website-list-policy)。  若要允许将 cookie 和 HTTP 身份验证用于Enterprise模式站点列表下载，请将匹配的 URL 模式添加到 [CookiesAllowedForURLs](/deployedge/microsoft-edge-policies#cookiesallowedforurls) 策略。 |
| 删除 Adobe Flash | v88 | | 此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请参阅 [Adobe Flash Chromium路线图](https://www.chromium.org/flash-roadmap#TOC-Flash-Support-Removed-from-Chromium-Target:-Chrome-88---Jan-2021-)。 |
| 删除 FTP 支持 | v88 | Beta v87 | 在 v88 中，FTP 支持已完全删除。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6246151319715840)。  拥有仍需要 FTP 支持的站点的企业可以通过将站点配置为使用 [IE 模式](/deployedge/edge-ie-mode)来继续使用 FTP。 |
| 自动升级混合内容图像 | v88 | | 非安全 (HTTP) 对映像的引用会自动升级到 HTTPS。  如果映像在 HTTPS 上不可用，则映像下载会失败。  [组策略](/deployedge/microsoft-edge-policies#insecurecontentallowedforurls)可用于控制此功能。  此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/4926989725073408)。 |
| 在 TLS 中删除 3DES | v93 | | 从 v93 开始，将删除对TLS_RSA_WITH_3DES_EDE_CBC_SHA密码套件的支持。  此更改发生在 Microsoft Edge 基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6678134168485888)。  此外，在 v93 中，将提供兼容性策略，以支持需要保持与过时服务器兼容的方案。  此兼容性策略将过时并停止在 v95 中工作。  请确保在此之前更新受影响的服务器。 |
| 弃用 WebRTC 的计划 B SDP 语义 | v98 (Chrome+2)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  此更改将弃用旧的会话说明协议 (SDP) 名为“计划 B”的方言。 此 SDP 格式正被统一计划所取代，统一计划是一种兼容规范且跨浏览器兼容的 SDP 格式。  有关详细信息，请参阅 [Chrome 平台状态条目](https://www.chromestatus.com/feature/5823036655665152)、 [PSA：计划 B 应在 M96 Beta 和 Stable 中引发](https://groups.google.com/g/discuss-webrtc/c/zRIgxG18D80/m/k4ZPzBO3AAAJ)，以及 [PSA：计划 B 在稳定和扩展弃用试用结束日期中引发](https://groups.google.com/u/1/g/discuss-webrtc/c/gEHrZyYKsfU)。  Microsoft 的弃用计划计划在 Chrome 之后的两个版本中进行。  请求 [WebRTC 计划 B 反向源试用令牌](https://developer.chrome.com/origintrials/#/view_trial/3892235977954951169) 允许站点在 v101 之前继续使用已弃用的 API。 |
| 限制专用网络请求以保护上下文 | v94 | | 从 v94 开始，从 Internet 上的页面访问本地 (intranet) 网络上的资源需要通过 HTTPS 传递这些页面。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5436853517811712)。  可使用两个兼容性策略支持需要保留与非安全页面的兼容性的方案：[InsecurePrivateNetworkRequestAllowed](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowed) 和 [InsecurePrivateNetworkRequestAllowedForUrls](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowedforurls)。 |
| 阻止混合内容下载 | v94 | | HTTPS 页面上将阻止从 HTTP URL 下载文件。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Google 安全博客条目](https://security.googleblog.com/2020/02/protecting-users-from-insecure_6.html)。 |
| 阻止第三方上下文中的 WebSQL | v97 | | 旧版 WebSQL 功能的使用将从第三方帧中阻止。  Enterprise策略 [WebSQLInThirdPartyContextEnabled](/deployedge/microsoft-edge-policies#websqlinthirdpartycontextenabled) 将在 v101 之前作为选择退出提供。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5684870116278272)。 |
| 发送 CORS 预检请求以进行专用网络访问 | v98 | | 从 v98 开始，Microsoft Edge在允许来自 Internet 的页面从本地网络 (intranet) 请求资源之前发送 CORS [预飞行](https://developer.chrome.com/blog/private-network-access-preflight/)请求。  Intranet 服务器应通过提供访问资源的显式权限来响应预检。  此检查的结果尚未强制执行。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5737414355058688)。  可使用两个兼容性策略来取消 CORS 预检请求： [InsecurePrivateNetworkRequestAllowed](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowed) 和 [InsecurePrivateNetworkRequestAllowedForUrls](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowedforurls)。 |
| User-Agent字符串中的三位数版本号 | v100 | | 从 v100 开始，Microsoft Edge将在User-Agent标头中发送一个三位数的版本号，例如`Edg/100`。 这可能会混淆使用错误分析器来确定 User-Agent 字符串版本号的脚本或服务器端分析。 从 v97 开始，站点所有者可以通过在 v100 中启用试验标志`#force-major-version-to-100``edge://flags`来模拟此条件。 |
| 默认情况下阻止沙盒帧中的外部协议 | v103 | | 阻止使用外部协议 (与从沙盒 iframe) 的非浏览器应用程序交互，除非框架上的属性显式授予 `sandbox` 权限。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5680742077038592)。 |
| 删除跨源子帧 JavaScript 对话框 | v107 (Chrome+1)  | | `window.alert``window.prompt`从跨源 iframe 中删除和`window.confirm`删除。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [“删除意向：跨源子帧 JS”对话框](https://groups.google.com/a/chromium.org/g/blink-dev/c/hTOXiBj3D6A/m/JtkdpDd1BAAJ)。 |


<!-- ====================================================================== -->
## <a name="notation-for-browser-versions"></a>浏览器版本的表示法

本文对浏览器版本号使用以下表示法。

| 符号 | 描述 |
| --- | --- |
| v123 | 此功能或更改在版本 123 中Microsoft Edge。 |
| v123 (Chrome+1)  | 此功能或更改在 123 Microsoft Edge版本中提供，这是功能或更改在 Chrome 版本 122 中附带的一个版本。 |
| v123 (Chrome+2)  | 此功能或更改在 123 Microsoft Edge版本中提供，这是在功能或在 Chrome 版本 121 中更改后的两个版本。 |
| Beta v123 | 此功能或更改在 Microsoft Edge 的 Beta 预览频道版本 123 中提供。 | 
| Dev v123 | 此功能或更改在 Microsoft Edge 的开发人员预览频道版本 123 中提供。 | 
| Canary v123 | 该功能或更改在Microsoft Edge的 Canary 预览频道版本 123 中提供。 | 
