---
title: 处理指向渐进式Web 应用的链接
description: 如何通过应用而不是 Web 浏览器来处理指向渐进式 Web 应用 (PWA) 的链接。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/15/2022
ms.openlocfilehash: 7e32a4919da03ff0d0ff927c25c7ab4ac27e01e6
ms.sourcegitcommit: 0d14dd864518c5b10cb844c14d80ea1cb589481c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2022
ms.locfileid: "12759724"
---
# <a name="handle-links-to-your-progressive-web-apps"></a>处理指向渐进式Web 应用的链接

许多操作系统上的本机应用程序可以处理链接。 当激活关联的 URL 时，本机应用程序可以请求启动（而不是 Web 浏览器）来为这些应用程序创建更具吸引力的体验。

渐进式Web 应用 (PVA) 也可以以类似的方式处理链接。


<!-- ====================================================================== -->
## <a name="automatic-link-handling"></a>自动链接处理

使用 Microsoft Edge 安装 PWA 时，引用此 PWA 范围内内容的所有链接都将自动启动它，而不是 Web 浏览器。

自动链接处理无需任何代码即可正常工作，但最终用户可以选择退出自动链接处理。 若要选择退出自动链接处理，请执行以下操作：

1. 在 Microsoft Edge 中，导航到 `edge://apps`。

1. 找到要禁用自动链接处理的 PWA，然后单击 **“详细信息**”。

1. 在“PWA 详细信息”页上的 **“链接处理”** 部分下，单击“切换”按钮。

![PWAmp 音乐播放器应用的 edge://apps 详细信息页，显示链接处理切换按钮的位置](../media/link-handling-opt-out.png)


<!-- ====================================================================== -->
## <a name="handle-links-from-other-origins-with-scope-extensions"></a>使用范围扩展处理来自其他源的链接

PWA 的清单定义了 PWA 所限托管域的哪个部分。 例如， `www.contoso.com` 域名下可能定义 `www.contoso.com/app` 了一个 PWA，其范围设置为 `/app`。 在这种情况下，路径中 `www.contoso.com/app` 提供的所有网页都是 PWA 范围的一部分。 但是，路径中的 `www.contoso.com/foo` 网页不是 PWA 范围的一部分。 此外，在 PWA 范围内提供 `bar.contoso.com/app` 或 `www.contoso.co.uk` 不属于 PWA 范围的网页。

通过作用域扩展，PWA 可以捕获到路径、子域甚至其自身范围以外的站点的导航。 这对于跨多个域以实现本地化的 PVA 非常有用。 例如，PWA 可能跨度 `contoso.com`， `contoso.co.uk`以及 `contoso.fr`.

**注意**：作用域扩展功能处于活动开发阶段，尚未准备好使用。 若要在Chromium中详细了解此功能的开发状态，请查看 Chrome 平台状态下[的 Web 应用范围扩展功能](https://chromestatus.com/feature/5746537956114432)。

在 Microsoft Edge 中使用该功能后，我们将在此处记录它。 同时，若要详细了解范围扩展的工作原理，请参阅 [WICG 存储库上的说明文](https://github.com/WICG/manifest-incubations/blob/gh-pages/scope_extensions-explainer.md)档。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [作为 URL 处理程序的 PVA](https://web.dev/pwa-url-handler/)。
