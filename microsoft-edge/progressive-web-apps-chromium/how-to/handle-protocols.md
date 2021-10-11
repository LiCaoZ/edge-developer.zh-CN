---
title: 处理渐进式 Web 应用中的协议
description: 了解如何将你的PWA注册为协议处理程序，以将其与其他应用程序在操作系统中深入集成。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/29/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， 协议
ms.openlocfilehash: e2f50876a9bbfd68bdc77cc4cca48f5803de1180
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087127"
---
# <a name="handle-protocols-in-progressive-web-apps"></a>处理渐进式 Web 应用中的协议

渐进式 Web 应用可以处理协议来创建更具吸引力的体验。

URL (或统一资源定位器) 是一个字符串，它允许客户端识别 Web 上的资源，并且它包含初始部分（协议）使客户端了解如何检索资源。

协议示例包括：

| 协议 | 示例 |
|:--- |:--- |
| `http` | http://contoso.com/ |
| `mailto` | mailto:contact@contoso.com |

借助协议处理，PWA 可以在安装时注册以处理某些允许的协议。 例如，电子邮件客户端应用可以注册以处理协议，或者地理位置应用 `mailto` 可以注册以处理 `geo` 协议。

如果自定义协议注册以前缀开头PWA，也可以处理 `web+` 自定义协议。

若要详细了解其他现有协议，请参阅维基百科 [的 URI 方案](https://en.wikipedia.org/wiki/List_of_URI_schemes) 列表。


<!-- ====================================================================== -->
## <a name="enable-protocol-handling"></a>启用协议处理

协议处理是一项实验性功能，可启用该功能：

1.  转到 `edge://flags` "Microsoft Edge"。
1.  选择 **"搜索标志** "并键入"协议处理"。
1.  选择 **"默认**  >  **启用重启**  >  **"。**

:::image type="content" source="../media/enable-protocol-handling-experiment.png" alt-text="启用&quot;协议处理&quot;API 实验。" lightbox="../media/enable-protocol-handling-experiment.png":::

协议处理也是 Microsoft Edge 中的一个源Microsoft Edge。 了解如何 [在源试用版中注册网站](./origin-trials.md#enroll-your-site-in-an-origin-trial)。


<!-- ====================================================================== -->
## <a name="register-protocols-to-handle"></a>注册要处理的协议

若要使用协议处理，请声明你的应用处理的协议。 此操作在应用清单 [文件中使用](./web-app-manifests.md) `protocol_handlers` 数组成员完成。

数组的每个 `protocol_handlers` 条目都包含一 `protocol` 个字符串和一 `url` 个字符串：

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

在以上示例中，应用注册为处理协议，当操作系统启动应用以响应它时，它会导航到 URL，将占位符替换为正在处理的完整 `mailto` `/newEmail` `%s` URL。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [PBA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)
