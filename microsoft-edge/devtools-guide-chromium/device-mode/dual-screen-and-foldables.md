---
title: 模拟双屏幕和可折叠设备
description: 使用Microsoft Edge中的虚拟设备增强双屏和可折叠设备的网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 6a129ead4ef1fd04c0d43a65420a1ed1d21c8481
ms.sourcegitcommit: a5aa193a2267019251d2447a2bdb088d979c6045
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2022
ms.locfileid: "12568626"
---
# <a name="emulate-dual-screen-and-foldable-devices"></a>模拟双屏幕和可折叠设备

可以在 Microsoft Edge DevTools 中模拟以下双屏和可折叠设备。

* [Surface Duo](https://www.microsoft.com/surface/devices/surface-duo)
* [Samsung Galaxy Fold](https://www.samsung.com/global/galaxy/galaxy-fold)

模拟设备并在以下姿势之间切换：

*  单屏或折叠的姿势。
*  双屏或展开的姿势。

![在 Microsoft Edge 中模拟 Surface Duo。](../media/experiments-surface-duo-emulation.msft.png)


<!-- ====================================================================== -->
## <a name="test-on-foldable-and-dual-screen-devices"></a>在可折叠设备和双屏设备上进行测试

在Microsoft Edge中以双屏姿势模拟 [Surface Duo](https://www.microsoft.com/surface/devices/surface-duo) 时， (两个屏幕之间的空间的接缝) 通过网站或应用绘制。

模拟的显示与网站 (或应用) 在 [Surface Duo](https://www.microsoft.com/surface/devices/surface-duo) 上运行时在[Microsoft Edge Android应用](https://play.google.com/store/apps/details?id=com.microsoft.emmx)中呈现的方式相匹配。  可能需要更新网站 (或应用) 才能在接缝上更好地显示。  有关将网站 (或应用) 适应接缝的详细信息，请参阅 [如何使用接缝](/dual-screen/introduction#how-to-work-with-the-seam)。

[设备工具栏](../device-mode/index.md#simulate-a-mobile-viewport)具有其他功能，可帮助你以多种姿势和方向测试网站或应用。  单击 **“旋转** (![旋转。](../media/rotate-dark-icon.msft.png)) 将视区旋转为横向。 将该功能与 **Span** (Span 组合在一 ![起。](../media/span-dark-icon.msft.png)) 在单屏、折叠和双屏或展开的姿势之间切换。  通过这些功能，你可以以所有四种可能的姿势和方向测试网站或应用。

![双屏和可折叠设备的姿势和方向矩阵。](../media/experiments-dual-screen-emulation-rotate-span.msft.png)

**实验 Web 平台功能** (![ExperimentalApis。](../media/experimental-apis-dark-icon.msft.png)) 图标显示**实验 Web 平台功能**标志的状态。  如果打开标志，则突出显示该图标。  如果标志已关闭，则不会突出显示该图标。  若要打开 (或关闭) 标志，请单击图标或转到 `edge://flags` 并切换标志。

### <a name="known-issues"></a>已知问题

#### <a name="pointer-shaking-or-stuttering"></a>指针摇晃或口吃

使用[Microsoft 远程桌面客户](/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients)端连接到远程电脑并模拟 [Surface Duo](https://www.microsoft.com/surface/devices/surface-duo) 或 [Samsung Galaxy Fold](https://www.samsung.com/global/galaxy/galaxy-fold) 时，指针可能会摇动或口吃。  如果遇到此问题，请联系 Microsoft Edge DevTools 团队。


<!-- ====================================================================== -->
## <a name="additional-resources"></a>其他资源

下面是可帮助你增强双屏设备的网站 (或应用) 的其他资源。

*  有关双屏设备上的 Web 开发的详细信息，请参阅 [双屏 Web 体验](/dual-screen/web/index)。

*  安装 [Surface Duo 仿真器](/dual-screen/android/use-emulator)。  Surface Duo 模拟器不同于Microsoft Edge中的模拟器、运行Android以及与[Android Studio](https://developer.android.com/studio/)集成。  请参阅 [“获取 Surface Duo SDK](/dual-screen/android/get-duo-sdk)”。
