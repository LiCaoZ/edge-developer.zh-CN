---
title: 服务工作进程改进
description: 如何使用每个服务工作者改进。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/19/2021
ms.openlocfilehash: 52fdf88609bfe53636135e9fd45d608742c8a8a8
ms.sourcegitcommit: 82de2fa19bf9c925ff5faafe8be6b24d21767e03
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2022
ms.locfileid: "12346545"
---
# <a name="service-worker-improvements"></a>服务工作进程改进

本文介绍开发人员工具的改进，用于处理服务工作者[](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)以及通过每个服务工作者传递的网络请求。  服务**工作者改进**包括网络 **、****应用程序和****源工具**。

对服务工作者的改进简化了以下任务：

*  根据服务工作者日程表进行调试。
    *  请求开示和启动持续时间。
    *  更新到服务工作者注册。
    *  使用提取事件处理程序 [的请求的](https://developer.mozilla.org/docs/Web/API/FetchEvent) 运行时。
    *  用于加载客户端的所有提取事件的运行时。
*  了解提取事件处理程序、安装事件处理程序和激活事件处理程序的运行时详细信息。
*  使用页面脚本信息进入和退出提取 [事件处理程序](#sources)。

改进的体验跨越三种不同的开发人员工具：

*  [网络工具](#network)。  选择一个通过服务工作器运行的网络请求，并访问计时工具中服务 **工作者的相应时间线** 。

*  [应用程序工具](#application)。  若要调试服务工作者，请转到服务 **工作者** 工具。

*  源 [工具](#sources) 。  单步执行提取事件处理程序时访问页面脚本信息。


<!-- ====================================================================== -->
## <a name="network"></a>网络

:::image type="content" source="../media/sw-network-timeline.msft.png" alt-text="网络工具中的服务工作线程时间线。" lightbox="../media/sw-network-timeline.msft.png":::

可以通过以下任一方式访问 **网络** 工具中的服务工作器调试功能：

*  直接在 **"网络"工具** 中。
*  在应用程序 **工具中** 启动。

### <a name="request-routing"></a>请求传送

为了便于可视化请求传送，日程表现在显示服务工作者的启动和提取 `respondWith` 事件。  调试并可视化通过服务工作者传递的网络请求：

1. 选择通过服务工作者发送的网络请求。
1. 打开 **计时** 工具。

### <a name="fetch-events"></a>Fetch 事件

若要了解有关提取 `respondWith` 事件更多信息，请单击 左侧的下拉箭头 `respondWith`。  若要查找有关原始请求 **和收到的响应** 的 **更多详细信息，请单击**相应的下拉箭头。


<!-- ====================================================================== -->
## <a name="application"></a>应用程序

:::image type="content" source="../media/sw-application-timeline.msft.png" alt-text="应用程序视图。" lightbox="../media/sw-application-timeline.msft.png":::

### <a name="service-worker-update-timeline"></a>服务工作进程更新日程表

开发人员Microsoft Edge开发人员工具团队在**应用程序**工具中添加了时间线，以反映服务工作者的更新生命周期。  此时间线显示安装和激活事件。  每个事件都有相应的下拉箭头，可为您提供更多详细信息。

### <a name="request-routing-and-fetch-events"></a>请求传送和提取事件

现在，可以通过控制台箱中的 **"** 网络"工具访问服务工作者日程表。  此功能有利于性能、最大程度地减少 UI 重复，并创建更全面的调试体验。

1. 打开正在调试的服务工作线程。

1. 单击" **网络** "按钮以打开 [请求路由体验](#network)。

1. 使用 **respondWith** 下拉箭头获取事件请求和响应信息。

**"网络**"工具显示通过正在调试的服务工作者发送的网络请求。  自动筛选器是缩小探索范围的方法。


<!-- ====================================================================== -->
## <a name="sources"></a>源

:::image type="content" source="../media/sw-sources.msft.png" alt-text="DOM 树。" lightbox="../media/sw-sources.msft.png":::

若要查找更多堆栈信息，在提取处理程序中设置一个断点。  详细信息将导致在页面脚本中请求资源。

当调试器在提取处理程序内暂停时，组合的堆栈信息将显示在面板右侧。  之后，可以在堆栈框架中四处移动。

### <a name="future-work"></a>未来工作

开发人员Microsoft Edge DevTools 团队计划进一步开发缓存详细信息，并研究更多方法为渐进[式 Web ](https://developer.mozilla.org/docs/Web/Progressive_web_apps) 应用程序开发人员改进服务工作 (PWA) 体验。
