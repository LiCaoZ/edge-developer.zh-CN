---
ms.assetid: ''
description: 在固定时段内安全地进行试验，并提供有关新平台功能的反馈。
title: 原始试验
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/07/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: edge， web development， html， css， origin trials， developer
ms.openlocfilehash: 04e5f8a05cea7c2a83f177088d90f92c6a9f41d7
ms.sourcegitcommit: 09975d536fb4673442f2ac6629e1787f14f110e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2021
ms.locfileid: "12036025"
---
# <a name="use-origin-trials-in-microsoft-edge"></a>在 Microsoft Edge

开发人员可以使用源试用版在有限时段内在活动网站上试用实验性 API。  使用源试用版时，访问Microsoft Edge的网站的用户可能会运行使用实验性 API 的代码。  若要访问每个用户计算机上实验性 API，你无需转到 并 `edge://flags` 打开功能标志。  有关详细信息，请导航到 [实验性 API][DeveloperMicrsoftEdgeOriginTrials]。  此外，你可以向浏览器工程师和 Web 标准社区提供有关 API 设计、用例或使用 API 的体验的反馈。

## <a name="get-started-using-origin-trials"></a>源试用版使用入门

有关实验性 API 在 Microsoft Edge 中可用，Microsoft Edge[源试用版开发人员控制台。][DeveloperMicrsoftEdgeOriginTrials]  确保查看有关实验性 API 的最低Microsoft Edge和试用结束日期，以评估在网站上使用实验性 API 的适用性。

> [!NOTE]
> 如果发生以下任一情况，实验可能会早于计划结束。
> *   重大安全事件。
> *   如果收集的充分反馈表明需要进行重大重新设计以满足 Web 开发人员的需求。
> 无论哪种情况，都向当前在实验中注册的所有开发人员发送通知电子邮件。

### <a name="register-for-a-trial-of-an-experimental-api"></a>注册实验性 API 的试用版

使用以下步骤注册实验性 API 的试用版。

1.  访问Microsoft Edge[试用版开发人员控制台页面][DeveloperMicrsoftEdgeOriginTrials]。
1.  在任何可用实验上选择"注册"按钮。
1.  使用你的帐户用户名和密码GitHub开发人员控制台。
1.  选择 **"授权 MicrosoftEdge"。**
1.  填写表单。

    > [!NOTE]
    > 若要注册单个或所有子域，请选择将 `Do you need to match all subdomains for the provided origin?` 设置设置为 `Yes` 。  例如， `https://dev.contoso.com` 是单个域， `https://*.contoso.com` 并使用通配符表示所有子域。

    > [!IMPORTANT]
    > 不允许使用下列原点格式。
    > *   指定源上的子文件夹。  例如， `https://contoso.com/path/subfolder`
    >
    > *   将源与查询字符串参数一同使用。  例如， `https://contoso.com/path/feature?query_parameter=12345`

1.  选择 **接受并注册**。

### <a name="apply-your-token"></a>应用令牌

将立即生成令牌，并显示在Microsoft Edge[试用版开发人员控制台][DeveloperMicrsoftEdgeOriginTrials]页面上。  若要开始在网站上使用试用版，请使用以下任一方法将令牌应用到你的页面。

*   将属性值和令牌添加到使用实验性 API 的每一页上 `origin-trial` `meta` 的 标记。

    ```html
    <meta http-equiv="origin-trial" content="replace-with-your-token">
    ```

*   添加到 `Origin-Trial` 服务器的 HTTP 响应标头。

    ```json
    Origin-Trial: replace-with-your-token
    ```

> [!NOTE]
> 你的令牌有效期为 6 周。  在试用结束之前，会向用户发送提醒电子邮件，请求你提供反馈，并请求你考虑在令牌过期前续订试用版。

### <a name="opt-out-of-an-experiment"></a>选择退出实验

若要选择退出实验，请使用以下方法之一删除令牌。

*   从 `meta` 使用实验性 API 的每一页中删除 标记。

    ```html
    <meta http-equiv="origin-trial" content="your-token">
    ```

*   从 `Origin-Trial` 服务器的 HTTP 响应标头中删除。

    ```json
    Origin-Trial: your-token
    ```

### <a name="detect-experimental-features-and-provide-a-fallback"></a>检测实验性功能并提供回退

使用实验性 API 时，请确保为网站的所有访问者提供工作体验。  访问者可能会使用不支持您添加到代码中的实验性 API 的浏览器。  此外，如果你的令牌在续订之前过期，实验性 API 将不再可用，这可能会导致错误。  若要避免这种情况，请确保检测到浏览器中可用的功能。  有关详细信息，请导航到["实现功能检测"。][MDNImplementingFeatureDetection]

### <a name="roadmap-for-allowed-origins"></a>允许的来源路线图

现在Microsoft Edge源试用版门户仅支持启用 SSL 的源，这意味着网站必须正确实现 HTTPS 才能注册实验。  将来，将规划以下安全源。

*   注册 `http://localhost` 为实验的原点。  若要使用 `http://localhost` 今天，请导航 `edge://flags` 到 ，将实验设置为 **已启用**。
*   使用具有前缀 `extensions://` 来源的扩展注册实验。

<!-- links -->

[DeveloperMicrsoftEdgeOriginTrials]: https://developer.microsoft.com/microsoft-edge/origin-trials "Microsoft Edge源试用版开发人员控制台|Microsoft Docs"

[MDNImplementingFeatureDetection]: https://developer.mozilla.org/docs/learn/tools_and_testing/cross_browser_testing/feature_detection "实现功能检测|MDN"
