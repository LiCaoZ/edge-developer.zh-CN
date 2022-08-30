---
title: 测试渐进式 Web 应用 (PWA) 协议处理
description: 使用应用程序工具测试在 PWA Web 应用清单中定义的协议。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/23/2022
ms.openlocfilehash: 6a44d0762f26f57c3bb4e0c4d1760e7d0853f2a5
ms.sourcegitcommit: 4923b594019786756244d8d7db2987c5b895fea5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2022
ms.locfileid: "12735543"
---
# <a name="test-progressive-web-app-pwa-protocol-handling"></a>测试渐进式 Web 应用 (PWA) 协议处理

本文假设你已在 PWA Web 应用清单中定义了协议处理程序，并且正在使用 DevTools 调试应用。 若要了解如何在 PWA 中定义和注册协议，请参阅[渐进式Web 应用中的句柄协议](../../progressive-web-apps-chromium/how-to/handle-protocols.md)。  

使用 **应用程序工具** 验证和测试 Microsoft Edge 是否已成功将应用注册为 Web 应用清单中定义的协议的处理程序。


<!-- ====================================================================== -->
## <a name="verify-that-protocol-handlers-are-defined-correctly"></a>验证是否正确定义了协议处理程序

如果尚未在 PWA Web 应用清单中定义协议的处理程序，则 **应用程序工具将** 注意到协议尚未定义，并将提供有关如何更新 Web 应用清单的其他信息。

如果已在 Web 应用清单中正确定义了协议， **则应用程序工具** 将报告 Microsoft Edge 已找到有效的协议处理程序注册，并且可以使用已安装的 PWA 测试这些协议处理程序。

若要验证是否已正确定义协议处理程序，请执行以下操作：

1. 在 Microsoft Edge 中导航到 PWA。 可以使用 [PWAmp 演示应用程序](https://microsoftedge.github.io/Demos/pwamp/)。
1. 打开 DevTools (`F12`) 。
1. 打开“**应用程序**”工具。
1. 单击 **“清单** ”以展开下拉列表。
1. 单击 **协议处理程序**。

如果未在 Web 应用清单中定义协议处理程序或定义不正确，将显示以下消息：

![清单窗格中未定义协议的协议处理程序部分。](./images/protocol-handlers-not-defined.png)

如果在 Web 应用清单中成功定义了协议处理程序，将显示以下消息：

![“清单”窗格中定义了协议的协议处理程序部分。](./images/protocol-handlers-defined.png)

“ **协议处理程序** ”部分还允许测试已定义的协议处理程序。


<!-- ====================================================================== -->
## <a name="test-protocols-from-the-application-tool"></a>从应用程序工具测试协议

若要从 **应用程序工具测试** 协议处理程序，必须已安装 PWA。 若要了解如何安装 PWA，请参阅 [安装 PWA](../../progressive-web-apps-chromium/ux.md#installing-a-pwa)。

**应用程序工具**检测 Web 应用清单中的所有协议处理程序。 若要测试处理程序，请执行以下操作：

1. 导航到 Microsoft Edge 中的 PWA 并打开 DevTools (`F12`) 。 可以使用 [PWAmp 演示应用程序](https://microsoftedge.github.io/Demos/pwamp/)。
1. 打开 **应用程序工具** ，然后单击 **清单** > **协议处理程序**。
1. 从下拉列表中选择要测试的协议。
1. 在文本中输入其余 URI，然后单击 **“测试协议**”。 这将启动 PWA。 根据操作系统 (操作系统) ，可能需要允许 Microsoft Edge 打开 PWA 并接受任何 OS 级别的权限，以便将应用注册为协议的处理程序。

在以下屏幕截图中 `web+amp://files.freemusicarchive.org/storage-freemusicarchive-org/music/no_curator/Kevin_MacLeod/Jazz_Sampler/Kevin_MacLeod_-_AcidJazz.mp3` ，正在测试 URI。

![从应用程序工具测试自定义 Web+amp 协议。](./images/test-protocol-handlers.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [调试渐进式 Web 应用 (PWA)](./index.md)
*  [处理渐进式Web 应用中的协议](../../progressive-web-apps-chromium/how-to/handle-protocols.md)
*  [Web 应用的协议处理程序入门](https://blogs.windows.com/msedgedev/2022/01/20/getting-started-url-protocol-handlers-microsoft-edge/)
*  [PVA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)
