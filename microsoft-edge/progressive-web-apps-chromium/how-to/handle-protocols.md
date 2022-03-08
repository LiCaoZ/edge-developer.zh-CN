---
title: 处理渐进式 Web 应用中的协议
description: 如何将你的 PWA注册为协议处理程序，以将其与其他应用程序更加深入地集成在操作系统中。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 01/12/2022
ms.openlocfilehash: b8ef9034f5e90e976ff00a59330b29de2e0e7451
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431149"
---
# <a name="handle-protocols-in-progressive-web-apps"></a>处理渐进式 Web 应用中的协议

为了创建更具吸引力的体验，渐进式 Web 应用可以处理多个协议。  统一资源定位 (URL) 是一个字符串，客户端可标识 Web 上的资源。 URL 的第一部分是 _协议_，如 `http` 或 `mailto`，它可让客户端了解如何检索资源。

使用协议处理，PWA时，PWA可以注册以处理某些允许的协议。  例如，电子邮件客户端应用可以注册以处理 `mailto` 协议，或者地理位置应用可以注册以处理 `geo` 协议。

如果自定义协议注册以前缀开头PWA，也可以处理`web+`自定义协议。

若要详细了解其他现有协议，请参阅 [URI 方案列表](https://en.wikipedia.org/wiki/List_of_URI_schemes)。


<!-- ====================================================================== -->
## <a name="register-protocols-to-handle"></a>注册要处理的协议

若要使用协议处理，请声明你的应用处理的协议。 此操作在应用清单[文件中使用](web-app-manifests.md)`protocol_handlers`数组成员完成。

数组的每个条目 `protocol_handlers` 都包含一个 `protocol` 字符串和一个 `url` 字符串：

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

在以上示例中，应用注册为处理 `mailto` 协议。  当操作系统启动`mailto``/newEmail`应用以响应协议时，应用将导航到 URL`%s`，将占位符替换为正在处理的完整 URL。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Web 应用的协议处理程序入门](https://blogs.windows.com/msedgedev/2022/01/20/getting-started-url-protocol-handlers-microsoft-edge/)
*  [PBA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)
