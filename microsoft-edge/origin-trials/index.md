---
title: 在 Microsoft Edge 中使用原始试用版
description: 在固定的时间段内安全地进行试验，并提供有关新平台功能的反馈。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
ms.openlocfilehash: cb974007b55bda6c028ad2e857c9d1b4e4f622a5
ms.sourcegitcommit: 62f55a8303644d4d3f2ea29e624efcc54f465aa1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2022
ms.locfileid: "12521757"
---
# <a name="use-origin-trials-in-microsoft-edge"></a>在 Microsoft Edge 中使用原始试用版

可以使用源试验在有限的时间内在实时网站上试用实验性 API。  使用源试用版时，访问站点的Microsoft Edge用户可以运行使用实验性 API 的代码。  若要访问每个用户计算机上的实验性 API，无需转到 `edge://flags` 并打开功能标志。

有关详细信息，请参阅[Microsoft Edge源试用版开发人员控制台](https://developer.microsoft.com/microsoft-edge/origin-trials)。  还可以提供有关 API 设计、用例或使用 API 浏览器工程师和 Web 标准社区的经验的反馈。


<!-- ====================================================================== -->
## <a name="get-started-using-origin-trials"></a>使用源试用开始

有关Microsoft Edge中提供的实验性 API 的详细信息，请[参阅Microsoft Edge源试验开发人员控制台](https://developer.microsoft.com/microsoft-edge/origin-trials)。  请务必查看Microsoft Edge的最低版本要求和试用结束日期，以评估在网站上使用实验性 API 的适用性。

> [!NOTE]
> 如果发生以下任何情况，则试验可能提前结束：
> *   重大安全事件。
> *   如果收集了足够的反馈，表明需要进行重大重新设计来满足 Web 开发人员的需求。
> 在任一情况下，都会向当前在试验中注册的所有开发人员发送通知电子邮件。

### <a name="register-for-a-trial-of-an-experimental-api"></a>注册试验性 API 的试用版

若要注册试验性 API 的试用版，请执行以下操作：

1. 转到[Microsoft Edge源试用版开发人员控制台](https://developer.microsoft.com/microsoft-edge/origin-trials)。

1. 单击任何可用试验上的 **“注册** ”按钮。

1. 使用GitHub用户名和密码登录到开发人员控制台。

1. 单击 **“授权 MicrosoftEdge**”。

1. 完成窗体。

   > [!NOTE]
   > 若要注册单个或所有子域，请选择将 `Do you need to match all subdomains for the provided origin?` 设置设置为 `Yes`。  例如， `https://dev.contoso.com` 是单个域，并 `https://*.contoso.com` 使用通配符来表示所有子域。

   > [!IMPORTANT]
   > 不允许使用以下源格式。
   > *   在源上指定子文件夹。  例如， `https://contoso.com/path/subfolder`
   >
   > *   将源与查询字符串参数配合使用。  例如， `https://contoso.com/path/feature?query_parameter=12345`

1. 单击 **“接受”并注册**。

### <a name="apply-your-token"></a>应用令牌

令牌会立即生成并在[Microsoft Edge源试用版开发人员控制台](https://developer.microsoft.com/microsoft-edge/origin-trials)上显示。  若要开始在网站上使用试用版，请使用以下任一方法将令牌应用到页面：

*  将 `origin-trial` 属性值和令牌添加到 `meta` 每个使用实验性 API 的页面上的标记。

   ```html
   <meta http-equiv="origin-trial" content="replace-with-your-token">
   ```

*  添加 `Origin-Trial` 到服务器的 HTTP 响应标头。

   ```json
   Origin-Trial: replace-with-your-token
   ```

> [!NOTE]
> 令牌有效期为 6 周。  在试用期结束之前，系统会向你发送提醒电子邮件，要求你提供反馈，并要求你考虑在令牌过期之前续订试用版。

### <a name="opt-out-of-an-experiment"></a>选择退出试验

若要选择退出试验，请使用以下方法之一删除令牌。

*  `meta`从使用试验性 API 的每个页面中删除标记。

   ```html
   <meta http-equiv="origin-trial" content="your-token">
   ```

*  从服务器的 HTTP 响应标头中删除 `Origin-Trial` 。

   ```json
   Origin-Trial: your-token
   ```

### <a name="detect-experimental-features-and-provide-a-fallback"></a>检测实验性功能并提供回退

使用实验性 API 时，请确保为网站的所有访问者提供工作体验。  访问者可能使用不支持添加到代码中的实验性 API 的浏览器。  此外，如果令牌在续订之前过期，则实验性 API 将不再可用，这可能会导致错误。

若要避免这种情况，请确保检测浏览器中可用的功能。  有关详细信息，请参阅 [实现功能检测](https://developer.mozilla.org/docs/learn/tools_and_testing/cross_browser_testing/feature_detection)。

### <a name="roadmap-for-allowed-origins"></a>允许的起源路线图

Microsoft Edge源试验门户目前仅支持已启用 SSL 的源，这意味着网站必须正确实现 HTTPS 才能注册试验。  将来，计划以下安全源：

*  注册 `http://localhost` 为试验的源。  若要立即使用 `http://localhost` ，请转到 `edge://flags` 试验并将其设置为 **“已启用**”。

*  使用带有 `extensions://` 前缀源的扩展注册试验。
