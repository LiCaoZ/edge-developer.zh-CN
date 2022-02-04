---
title: Microsoft Edge 中影响网站兼容性的更改
description: 针对可能会影响网站兼容性的Microsoft Edge更改摘要。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/24/2022
---
# <a name="site-compatibility-impacting-changes-coming-to-microsoft-edge"></a>Microsoft Edge 中影响网站兼容性的更改

Web 平台是一组用于构建网页的技术。  这些技术包括 HTML、CSS、JavaScript 和许多其他开放标准。  Web 平台不断发展以改进用户体验、安全性和隐私。  在某些情况下，更改可能会影响现有网页的功能。  有关即将推出的 Project Web Chromium更改的信息，请参阅 [Chrome 平台状态发布时间线](https://www.chromestatus.com/features/schedule)。

出于功能和兼容性原因，Microsoft Edge几乎采用项目Chromium Web 平台的所有更改。  Microsoft 保持对浏览器的完全Microsoft Edge，并可以延迟或拒绝更改。  更改Microsoft Edge决定更改是否对浏览器用户的好处。

下表中Microsoft Edge计划Chromium发布时间或行为上偏离计划的功能区域。  此表还突出显示了团队正在跟踪Microsoft Edge影响大的更改。

经常查看本文。  当Microsoft Edge发展、日程表稳定以及宣布新更改时，团队会更新本文。


<!-- ====================================================================== -->
## <a name="differences-from-the-chromium-schedule-and-high-impact-changes"></a>与计划Chromium高影响更改之间的差异

| “更改” | 稳定渠道 | 实验 | 其他信息 |
| --- | --- | --- | --- |
| 禁止在页面 `XmlHttpRequest` 内同步解除 | v83 (Chrome+1)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  匹配 Chrome，Microsoft Edge提供在 v88 之前关闭此更改的组策略。  有关详细信息，包括 Google 为此更改计划的时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/4664843055398912)。 |
| 显示通知权限请求的细微提示 | v84 | | 安静通知请求在使用 `Notifications` `Push` 或 API 请求的网站通知权限的地址栏中显示一个细微的请求图标，以替换完整或标准权限飞出提示 UI。  此功能当前为所有用户启用。  若要选择退出安静通知请求，请参阅 `edge://settings/content/notifications`。  将来，Microsoft Edge团队可能会探索在某些情况下重新启用完整的飞出通知提示。 |
| 关闭 TLS/1.0 和 TLS/1.1 | v84 | | |
| Cookie 默认为 和`SameSite=Lax` `SameSite=None-requires-Secure` | v86 (Chrome+1)  | Canary v82，Dev v82 | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 为此更改计划的时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5088147346030592)。 |
| 引用者策略：默认为 `strict-origin-when-cross-origin` | v86 (Chrome+1)  | Canary v79，Dev v79 | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 为此更改计划的时间线，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6251880185331712)。 |
| 弃用 AppCache | v86 (Chrome+1)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [WebDev 文档](https://web.dev/appcache-removal)。  Microsoft 推出计划弃用计划计划在 Chrome 后的一个版本中发布。  请求 [AppCache OriginTrial 令牌](https://developers.chrome.com/origintrials/#/view_trial/1776670052997660673) 允许站点继续使用已弃用 API，直到 v90。 |
| 阻止第三方 Cookie 时不允许 HTTP 身份验证 | v87 | | 从 v87 开始，当阻止第三方请求使用 [BlockThirdPartyCookies](/deployedge/microsoft-edge-policies#blockthirdpartycookies) `edge://settings`策略或 中的切换时，也会禁止 HTTP 身份验证。  如果托管Enterprise终结点需要使用 HTTP 身份验证，[](/deployedge/edge-ie-mode-policies#configure-using-the-use-the-enterprise-mode-ie-website-list-policy)此更改可能会影响Internet Explorer模式站点列表下载。  若要允许将 Cookie 和 HTTP 身份验证用于Enterprise站点列表下载，请向 [CookiesAllowedForURLs](/deployedge/microsoft-edge-policies#cookiesallowedforurls) 策略添加匹配的 URL 模式。 |
| 删除 Adobe Flash | v88 | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Adobe Flash Chromium路线图](https://www.chromium.org/flash-roadmap#TOC-Flash-Support-Removed-from-Chromium-Target:-Chrome-88---Jan-2021-)。 |
| 删除 FTP 支持 | v88 | Beta v87 | 在 v88 中，完全删除了 FTP 支持。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6246151319715840)。  具有仍然需要 FTP 支持的网站的企业可以通过将站点配置为使用 IE 模式来继续使用 [FTP](/deployedge/edge-ie-mode)。 |
| 自动升级混合内容图像 | v88 | | 对图像 (非) HTTP 文件会自动升级到 HTTPS。  如果图像无法通过 HTTPS 使用，则图像下载将失败。  组 [策略](/deployedge/microsoft-edge-policies#insecurecontentallowedforurls) 可用于控制此功能。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/4926989725073408)。 |
| 在 TLS 中删除 3DES | v93 | | 从 v93 开始，将TLS_RSA_WITH_3DES_EDE_CBC_SHA密码套件的支持。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/6678134168485888)。  此外，在 v93 中，兼容性策略可用于支持需要保留与过时服务器的兼容性的方案。  此兼容性策略将过时，在 v95 中停止运行。  请确保在更新之前更新受影响的服务器。 |
| 弃用 WebRTC 的计划 B SDP 语义 | v98 (Chrome+2)  | | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  此更改将弃用名为"计划 B"的 (SDP) 旧会话描述协议。 此 SDP 格式将由统一计划取代，统一计划是一种符合规格且跨浏览器兼容的 SDP 格式。  有关详细信息，请参阅 [Chrome](https://www.chromestatus.com/feature/5823036655665152) 平台状态条目 [PSA： Plan B should throw in M96 Beta and Stable](https://groups.google.com/g/discuss-webrtc/c/zRIgxG18D80/m/k4ZPzBO3AAAJ)和 [PSA： Plan B throwing in Stable and Extended Deprecation Trial End Date](https://groups.google.com/u/1/g/discuss-webrtc/c/gEHrZyYKsfU)。  Microsoft 推出计划弃用计划为 Chrome 后的两个版本。  请求 [WebRTC 计划 B 反向源试用](https://developer.chrome.com/origintrials/#/view_trial/3892235977954951169) 令牌允许网站继续使用已弃用 API，直到 v101。 |
| 将专用网络请求限制为保护上下文 | v94 | | 从 v94 开始，从 internet (访问本地) Intranet 上的资源需要通过 HTTPS 传递这些页面。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5436853517811712)。  可使用两个兼容性策略支持需要保留与非安全页面的兼容性的方案：[InsecurePrivateNetworkRequestAllowed](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowed) 和 [InsecurePrivateNetworkRequestAllowedForUrls](/deployedge/microsoft-edge-policies#insecureprivatenetworkrequestsallowedforurls)。 |
| 阻止混合内容下载 | v94 | | HTTPS 页面上将阻止从 HTTP URL 下载文件。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Google 安全博客条目](https://security.googleblog.com/2020/02/protecting-users-from-insecure_6.html)。 |
| 阻止第三方上下文中的 WebSQL | v97 | | 将阻止使用第三方框架使用旧的 WebSQL 功能。  一Enterprise [WebSQLInThirdPartyContextEnabled](/deployedge/microsoft-edge-policies#websqlinthirdpartycontextenabled) 将作为选择退出，直到 v101。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅 [Chrome 平台状态条目](https://chromestatus.com/feature/5684870116278272)。 |
| 字符串中的三User-Agent版本号 | v100 | | 从 v100 开始Microsoft Edge，User-Agent标头中发送三位数的版本号，例如 `Edg/100`。 这可能会导致使用错误分析程序确定字符串版本号的脚本或User-Agent混淆。 从 v97 开始，网站所有者可以在 v100 之前通过启用 中的实验标志来模拟此 `#force-major-version-to-100` 条件 `edge://flags`。 |
| 删除跨源子框架 JavaScript 对话框 | v103 (Chrome+1)  | | `window.alert`从跨源 `window.prompt``window.confirm` iframe 中删除 、 和 。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请参阅意图 [删除：跨源子框架 JS 对话框](https://groups.google.com/a/chromium.org/g/blink-dev/c/hTOXiBj3D6A/m/JtkdpDd1BAAJ)。 |


<!-- ====================================================================== -->
## <a name="notation-for-browser-versions"></a>浏览器版本的表示法

本文对浏览器版本号使用下列表示法。

| 表示法 | 描述 |
| --- | --- |
| v123 | 功能或更改在版本 123 Microsoft Edge提供。 |
| v123 (Chrome+1)  | 功能或更改在版本 123 Microsoft Edge，它是 Chrome 版本 122 中提供功能或更改后的一个版本。 |
| v123 (Chrome+2)  | 功能或更改在版本 123 中Microsoft Edge，这是 Chrome 版本 121 中提供功能或更改后的两个版本。 |
| Beta v123 | 功能或更改在 Microsoft Edge Beta 预览频道的版本 123 中提供。 | 
| Dev v123 | 功能或更改在版本 123 的开发人员预览频道中提供Microsoft Edge。 | 
| Canary v123 | 功能或更改在 Canary 预览频道的版本 123 中提供Microsoft Edge。 | 
