---
title: 处理渐进式 Web 应用中的协议
description: 如何将你的 PWA注册为协议处理程序，以将其与其他应用程序在操作系统中深入集成。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， 协议
ms.date: 09/29/2021
ms.openlocfilehash: 893adcbbb434655c7e776a28d0556fd4b0d82e82
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284915"
---
# <a name="handle-protocols-in-progressive-web-apps"></a>处理渐进式 Web 应用中的协议

为了创建更具吸引力的体验，渐进式 Web 应用可以处理多个协议。  统一资源定位 (URL) 是一个字符串，客户端可标识 Web 上的资源。 URL 的第一部分是 _协议_，如 或 `http` `mailto` ，它可让客户端了解如何检索资源。

使用协议处理，PWA时，PWA可以注册以处理某些允许的协议。  例如，电子邮件客户端应用可以注册以处理协议，或者地理位置 `mailto` 应用可以注册以处理 `geo` 协议。

如果自定义协议注册以前缀开头PWA，也可以处理 `web+` 自定义协议。

若要详细了解其他现有协议，请参阅 [URI 方案列表](https://en.wikipedia.org/wiki/List_of_URI_schemes)。


<!-- ====================================================================== -->
## <a name="enable-protocol-handling"></a>启用协议处理

协议处理是一项实验性功能。  要打开协议处理，请进行：

1.  转到 `edge://flags` "Microsoft Edge"。
1.  选择 **"搜索标志**"，然后键入"协议处理"。
1.  选择 **"默认**  >  **启用重启**  >  **"。**

:::image type="content" source="../media/enable-protocol-handling-experiment.png" alt-text="启用&quot;协议处理&quot;API 实验。":::

协议处理也是 Microsoft Edge 中的一个Microsoft Edge。 了解如何 [在源试用版中注册网站](./origin-trials.md#enroll-your-site-in-an-origin-trial)。


<!-- ====================================================================== -->
## <a name="register-protocols-to-handle"></a>注册要处理的协议

若要使用协议处理，请声明你的应用处理的协议。 这是通过使用 数组成员 [在](./web-app-manifests.md)应用清单文件中 `protocol_handlers` 完成。

数组的每个 `protocol_handlers` 条目都包含 `protocol` 一个字符串和一 `url` 个字符串：

```json
{
    "protocol_handlers": [
        {
            "protocol": "mailto",
            "url": "/newEmail?to=%s"
        }
    ]
}
```

在以上示例中，应用注册为处理 `mailto` 协议。  当操作系统启动应用以响应协议时，应用将导航到 URL，将占位符替换为正在 `mailto` `/newEmail` `%s` 处理的完整 URL。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [PBA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)
