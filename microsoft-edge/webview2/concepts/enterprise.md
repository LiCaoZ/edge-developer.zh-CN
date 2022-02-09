---
title: 管理 WebView2 应用程序
description: IT 管理员如何管理 WebView2 应用程序和 WebView2 运行时。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 11/12/2021
ms.openlocfilehash: c91cc4f159a89cbba8e2a143d6899fd99defc208
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345952"
---
# <a name="manage-webview2-applications"></a>管理 WebView2 应用程序

[WebView2](../index.md) 是开发人员用于构建其应用程序的一个组件，开发人员可以将自更新的 Evergreen WebView2 运行时部署到用户设备上，以支持其应用程序。  本文讨论 IT 管理员如何管理 WebView2 应用程序和 WebView2 运行时。  

欢迎 IT 管理员和开发人员通过 [WebView2](https://github.com/MicrosoftEdge/WebViewFeedback) 反馈存储库提供反馈。


<!-- ====================================================================== -->
## <a name="group-policies-for-webview2"></a>WebView2 的组策略

IT 管理员可以使用组策略对象 (GPO) WebView2 的策略设置。  以下策略与 WebView2 相关。

### <a name="update-policies"></a>更新策略

[Microsoft Edge -](/deployedge/microsoft-edge-update-policies) 更新策略可供 IT 管理员管理 WebView2 运行时的安装和更新方面。  浏览器Microsoft Edge WebView2 运行时使用相同的更新机制进行更新。  除非策略（如 `Update`）特定于通道，否则它同时适用于浏览器和 WebView2 运行时。

例如， `UpdateSuppressed` 允许 IT 管理员设置每天禁止浏览器和 WebView2 运行时自动更新的时间。  这使 IT 管理员能够为浏览器和 WebView2 运行时配置一次首选项和代理，以控制其网络带宽/流量或用于其他目的。

IT 管理员可以按照Microsoft Edge[指南配置](/deployedge/configure-microsoft-edge) Microsoft Edge - 更新策略。

### <a name="browser-policies"></a>浏览器策略

[Microsoft Edge - 浏览器](/deployedge/microsoft-edge-policies)策略不适用于 WebView2 应用程序。  这是设计使的，因为应用和浏览器具有不同的用例，并且 IT 管理员可能不知道哪些应用程序使用 WebView2。  

在 WebView2 上应用浏览器策略会产生意外结果。  例如，IT 管理员可以在浏览器中阻止 JavaScript，这将破坏使用 JavaScript 的 WebView2 应用。  为了防止出现此问题，浏览器策略独立于 WebView2 策略。

### <a name="webview2-specific-policies"></a>特定于 WebView2 的策略

[WebView2 特定的](/deployedge/microsoft-edge-webview-policies) 策略可供你使用<!--dev, or admin?--> 直接管理 WebView2。  但是，我们建议 WebView2 应用开发人员实施自己的组策略来管理 WebView2 的使用，因为管理员能够更轻松地管理应用，而不是直接管理 WebView2。


<!-- ====================================================================== -->
## <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)

[Windows Server Update Services (WSUS) ](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)使信息技术管理员能够部署最新的 Microsoft 产品更新。 可以使用 WSUS 完全管理通过 Microsoft 更新将发布的 WebView2 更新分发到网络上的计算机。

> [!NOTE]
> 建议使用默认更新程序接收 WebView2 Microsoft Edge更新。 应谨慎修改更新和服务路径。

### <a name="webview2-deployment-and-update-using-wsus"></a>使用 WSUS 的 WebView2 部署和更新

Configuration Manager 中的 WebView2 选项存在于"Microsoft Edge"节点下。 有关详细信息，请访问 Update [Microsoft Edge](/mem/configmgr/apps/deploy-use/deploy-edge)。


## <a name="see-also"></a>另请参阅

*  [分发 WebView2 应用和 WebView2 运行时](./distribution.md) - 关于常青、自更新的 WebView2 运行时。
