---
title: 在 DevTools 中模拟双屏幕和可折叠Microsoft Edge设备
description: 使用 Microsoft Edge 中的虚拟设备来增强用于双屏幕和可折叠设备的网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: b32ef05b7e966b22d5c9f33622354641d8a19f16
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319071"
---
# <a name="emulate-dual-screen-and-foldable-devices-in-microsoft-edge-devtools"></a>在 DevTools 中模拟双屏幕和可折叠Microsoft Edge设备

你可以模拟 DevTools 中的以下双屏幕和可折叠Microsoft Edge设备。

*   [Surface Duo](https://www.microsoft.com/surface/devices/surface-duo)
*   [Samsung Galaxy Fold](https://www.samsung.com/global/galaxy/galaxy-fold)

模拟设备，并切换以下状态。

*   单屏或折叠状态
*   双屏或展开状态

打开实验性[Web 平台 API，](#turn-on-experimental-apis)并使用[CSS 媒体](/dual-screen/web/css-media-spanning)屏幕跨区功能以及[JavaScript getWindowSegments API](/dual-screen/web/javascript-getwindowsegments)增强适用于双屏和可折叠设备的网站 (或应用) 。

:::image type="complex" source="../media/experiments-surface-duo-emulation.msft.png" alt-text="模拟 Surface Duo Microsoft Edge" lightbox="../media/experiments-surface-duo-emulation.msft.png":::
   模拟 Surface Duo Microsoft Edge
:::image-end:::


<!-- ====================================================================== -->
## <a name="turn-on-experimental-apis"></a>打开实验性 API

若要使用[CSS 媒体屏幕跨区](/dual-screen/web/css-media-spanning)功能以及[JavaScript getWindowSegments API，](/dual-screen/web/javascript-getwindowsegments)请打开 `Experimental Web Platform features` Microsoft Edge。  完成以下步骤。

1.  导航到 `edge://flags`。
1.  在"**搜索标志**"文本框中，输入 `Experimental Web Platform features` ，选择"**实验性 Web 平台功能**"标志，将"**已禁用"更改为****"已启用"。**
1.  重启 Microsoft Edge。

:::image type="complex" source="../media/experiments-dual-screen-emulation-edge-flags.msft.png" alt-text="打开&quot;实验性 Web 平台功能&quot;标志" lightbox="../media/experiments-dual-screen-emulation.msft.png":::
   打开" **实验性 Web 平台功能"** 标志
:::image-end:::

> [!NOTE]
> 如果使用[CSS](/dual-screen/web/css-media-spanning)媒体查询或[JavaScript Windows Segment](/dual-screen/web/javascript-getwindowsegments)枚举 API 增强 Surface Duo 的网站或应用，还必须在 Surface [Duo](https://www.microsoft.com/surface/devices/surface-duo)设备上的 Android [Microsoft Edge](https://play.google.com/store/apps/details?id=com.microsoft.emmx)应用中打开实验**性 Web**平台功能[](https://www.microsoft.com/surface/devices/surface-duo)标志。
>
> 如果在桌面[Microsoft Edge](https://www.microsoft.com/edge)中打开实验性**Web**平台功能标志，并且在[Android Microsoft Edge](https://play.google.com/store/apps/details?id=com.microsoft.emmx)应用中关闭，则桌面 Microsoft Edge 的 Surface Duo 模拟器中的网站或应用的行为与 Android [Microsoft Edge 应用不匹配](https://play.google.com/store/apps/details?id=com.microsoft.emmx)在[Surface Duo 上](https://www.microsoft.com/surface/devices/surface-duo)。  确保标志在 Android 和桌面Microsoft Edge匹配，以在桌面设备上成功使用 Surface Duo [Microsoft Edge。](https://www.microsoft.com/edge)


<!-- ====================================================================== -->
## <a name="test-on-foldable-and-dual-screen-devices"></a>在可折叠和双屏设备上测试

当你在 Microsoft Edge 中模拟双屏状态中的[Surface Duo](https://www.microsoft.com/surface/devices/surface-duo)时， (两个屏幕之间的空间) 在网站或应用上绘制。

模拟显示与在 Surface Duo (Android) [在 Microsoft Edge 应用中](https://play.google.com/store/apps/details?id=com.microsoft.emmx)呈现你的[网站或应用的方式相匹配](https://www.microsoft.com/surface/devices/surface-duo)。  你可能必须更新你的网站或 (应用) ，以更好地显示在一起。  若要详细了解如何调整网站 (或应用) 适应变化，请导航到"如何处理["。](/dual-screen/introduction#how-to-work-with-the-seam)

设备 [工具栏](../device-mode/index.md#simulate-a-mobile-viewport) 具有其他功能，可帮助你在多个状态和方向中测试你的网站或应用。  选择 **旋转** (![ 旋转 ](../media/rotate-dark-icon.msft.png)) 将视口旋转到横向。 将该功能与 **Span** (Span) 结合使用，可在单屏或折叠、双屏或展开状态 ![ ](../media/span-dark-icon.msft.png) 之间进行切换。  这些功能共同允许你在所有四种可能状态和方向中测试网站或应用。

:::image type="complex" source="../media/experiments-dual-screen-emulation-rotate-span.msft.png" alt-text="双屏幕和可折叠设备的状态和方向矩阵" lightbox="../media/experiments-dual-screen-emulation-rotate-span.msft.png":::
   双屏幕和可折叠设备的状态和方向矩阵
:::image-end:::

ExperimentalApis (的"实验性 **Web**) ![ 功能"图标显示"实验性 Web ](../media/experimental-apis-dark-icon.msft.png) **平台功能"标志** 的状态。  如果此标志已打开，则突出显示该图标。  如果关闭标志，则不突出显示图标。  若要在标志 (或) ，请选择图标或导航到 并 `edge://flags` 切换标志。

> [!NOTE]
> 以下是当前已知问题的列表。
>
> *   当你使用[Microsoft 远程桌面](/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients)客户端连接到远程电脑并模拟 Surface [Duo](https://www.microsoft.com/surface/devices/surface-duo)或[Samsung 用户折叠](https://www.samsung.com/global/galaxy/galaxy-fold)时，指针可能会抖动或抖动。  如果遇到问题，请与开发人员Microsoft Edge联系。


<!-- ====================================================================== -->
## <a name="additional-resources"></a>其他资源

下面是可以帮助你增强用于双屏幕设备的 (或) 应用的其他资源。

*   有关在双屏设备上进行 Web 开发的信息，请导航到 [双屏幕 Web 体验](/dual-screen/web/index)。
*   安装 [Surface Duo 仿真器](/dual-screen/android/use-emulator)。  Surface Duo 模拟器不同于 Microsoft Edge 中的仿真器，运行 Android，并且与[Android Studio 集成](https://developer.android.com/studio/)。  有关详细信息，请导航到[获取 Surface Duo SDK](/dual-screen/android/get-duo-sdk)。
