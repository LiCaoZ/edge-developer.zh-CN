---
description: 了解如何管理 WebView2 应用程序
title: 管理 WebView2 应用程序
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/21/2020
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html、企业、组策略、可管理性
ms.openlocfilehash: 318c2da28f9e02c0dd70619070b059e6fbc0e06a
ms.sourcegitcommit: 01ed086305c06b4e3a0436586524986700276148
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "11893616"
---
# <a name="managing-webview2-applications"></a>管理 WebView2 应用程序  

[WebView2][WebView2Landing] 是开发人员用于构建其应用程序的一个组件，开发人员可以将自更新的 Evergreen WebView2 运行时部署到用户设备上，以支持其应用程序。  本文档讨论 IT 管理员如何管理 WebView2 应用程序和 WebView2 运行时。  欢迎 IT 管理员和开发人员在 [WebView2 反馈存储库上提供反馈][GithubMicrosoftedgeWebviewfeddback]。  


## <a name="group-policies-for-webview2"></a>WebView2 的组策略  

IT 管理员可以使用组策略对象 \ (GPO\) 配置 WebView2 的策略设置。  以下策略与 WebView2 相关。

*   [Microsoft Edge -][EdgeUpdatePolicies]更新策略可供 IT 管理员管理 WebView2 运行时的安装和更新方面。  浏览器Microsoft Edge WebView2 运行时使用相同的更新机制进行更新。  除非策略（如 ）特定于通道，否则它同时适用于 `Update` 浏览器和 WebView2 运行时。  例如，允许 IT 管理员设置每天的时间，以禁止浏览器和 `UpdateSuppressed` WebView2 运行时自动更新。  这使 IT 管理员能够为浏览器和 WebView2 运行时配置一次首选项和代理，以控制其网络带宽/流量或用于其他目的。  IT 管理员可以按照Microsoft Edge[指南配置][ConfigureMicrosoftEdge]Microsoft Edge - 更新策略。  

*   [Microsoft Edge - 浏览器][EdgeBrowserPolicies]策略不适用于 WebView2 应用程序。  这是设计使的，因为应用和浏览器具有不同的用例，并且 IT 管理员可能不知道哪些应用程序使用 WebView2。  在 WebView2 上应用浏览器策略会产生意外结果。  例如，IT 管理员可以在浏览器中阻止 JavaScript，这将破坏使用 JavaScript 的 WebView2 应用。  为了防止出现此问题，浏览器策略独立于 WebView2 策略。

*   [WebView2 特定的][WebView2Policies] 策略可供你使用<!--dev, or admin?--> 直接管理 WebView2。  但是，我们建议 WebView2 应用开发人员实施自己的组策略来管理 WebView2 的使用，因为管理员能够更轻松地管理应用，而不是直接管理 WebView2。  


## <a name="see-also"></a>另请参阅

*  [分发 WebView2 应用和 WebView2 运行时][Webview2ConceptsDistribution] - 关于常青、自更新的 WebView2 运行时。


<!-- links -->
[Webview2ConceptsDistribution]: ./distribution.md "分发 WebView2 应用和 WebView2 运行时|Microsoft Docs"  
[WebView2Landing]: ../index.md "WebView2 Microsoft Edge预览 (简介) |Microsoft Docs"  
<!-- external links -->
[EdgeUpdatePolicies]: /deployedge/microsoft-edge-update-policies "Microsoft Edge - 更新策略|Microsoft Docs"  
[EdgeBrowserPolicies]: /deployedge/microsoft-edge-policies "Microsoft Edge - 浏览器策略|Microsoft Docs"  
[ConfigureMicrosoftEdge]: /deployedge/configure-microsoft-edge "在Microsoft Edge上配置策略Windows |Microsoft Docs"  
[WebView2Policies]: /deployedge/microsoft-edge-webview-policies "Microsoft EdgeWebView2 策略文档|Microsoft Docs" 

[GithubMicrosoftedgeWebviewfeddback]: https://github.com/MicrosoftEdge/WebViewFeedback "WebView 反馈 - MicrosoftEdge/WebViewFeedback | GitHub"  
