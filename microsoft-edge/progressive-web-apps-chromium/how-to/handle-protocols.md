---
title: 处理渐进式Web 应用中的协议
description: 如何将 PWA 注册为协议处理程序，以便将 PWA 与其他应用程序更深入地集成到操作系统中。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 01/12/2022
ms.openlocfilehash: 06519772b3a7d667ffcded1c5fcafe4fff48851e
ms.sourcegitcommit: 4923b594019786756244d8d7db2987c5b895fea5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2022
ms.locfileid: "12735525"
---
# <a name="handle-protocols-in-progressive-web-apps"></a>处理渐进式Web 应用中的协议

为了创建更具吸引力的体验，渐进式Web 应用可以处理多个协议。  统一资源定位器 (URL) 是允许客户端在 Web 上标识资源的字符串。 URL 的第一部分是 _协议_，例如 `http` ， `mailto`它让客户端知道如何检索资源。

使用协议处理时，安装 PWA 时，PWA 可以注册以处理某些允许的协议。  例如，电子邮件客户端应用可以注册以处理 `mailto` 协议，或者地理位置应用可以注册以处理 `geo` 协议。

如果 PWA 注册以前缀开头 `web+` 的协议，也可以处理自定义协议。

若要详细了解其他现有协议，请参阅 [URI 方案列表](https://en.wikipedia.org/wiki/List_of_URI_schemes)。


<!-- ====================================================================== -->
## <a name="register-protocols-to-handle"></a>注册要处理的协议

若要使用协议处理，请声明应用处理的协议。 这是通过使用数组成员在 Web 应用 [清单文件](web-app-manifests.md)中完成的 `protocol_handlers` 。

数组中的 `protocol_handlers` 每个条目都包含一个 `protocol` 字符串和一个 `url` 字符串：

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

在上面的示例中，应用已注册以处理 `mailto` 协议。  当操作系统启动应用以 `mailto` 响应协议时，应用将导航到 `/newEmail` URL，将 `%s` 占位符替换为正在处理的完整 URL。

## <a name="test-protocols-with-the-devtools"></a>使用 DevTools 测试协议

可以使用 Microsoft Edge DevTools 中的 **应用程序工具来** 验证 Microsoft Edge 是否已成功将应用注册为 Web 应用清单中定义的协议的处理程序。  还可以测试协议，并使用不同的 URL 和终结点启动 PWA。  有关详细信息，请参阅 [测试渐进式 Web 应用 (PWA) 协议处理](../../devtools-guide-chromium/progressive-web-apps/protocol-handlers.md)。

<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Web 应用的协议处理程序入门](https://blogs.windows.com/msedgedev/2022/01/20/getting-started-url-protocol-handlers-microsoft-edge/)
*  [PVA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)
*  [测试渐进式 Web 应用 (PWA) 协议处理](../../devtools-guide-chromium/progressive-web-apps/protocol-handlers.md)
