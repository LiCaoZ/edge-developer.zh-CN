---
description: 打开传感器工具并导航到"方向"部分。
title: 使用 DevTools Microsoft Edge设备方向
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: ec06a31d09299c84406004b6717c4051fc4841a7
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141689"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="simulate-device-orientation-with-microsoft-edge-devtools"></a>使用 DevTools Microsoft Edge设备方向

完成以下操作以模拟来自 DevTools 的不同Microsoft Edge方向。

<!--todo: update device orientation section when available -->

1.  选择 `Control` + `Shift` + `P` (Windows、Linux) 或 `Command` + `Shift` + `P` (macOS) 打开命令**菜单**。

    :::image type="complex" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单" lightbox="../media/device-mode-console-command-menu.msft.png":::
       **命令菜单**
    :::image-end:::

1.  键入 `sensors` ，选择 **显示传感器**，然后选择 `Enter` 。  传感器 **工具** 将在 DevTools 窗口底部打开。
1.  从 **"方向**"列表中，选择预设方向之一（如 ）或选择"自定义方向" `Portrait upside down` 来提供你自己的精确方向。 ****

    :::row:::
       :::column span="":::
          :::image type="complex" source="../media/device-mode-console-sensors-orientation-portrait-upside-down.msft.png" alt-text="从&quot;方向&quot;列表中选择&quot;纵向&quot;向下" lightbox="../media/device-mode-console-sensors-orientation-portrait-upside-down.msft.png":::
             从 `Portrait upside down` "**入职培训"列表中选择** :::image-end:::
       :::column-end:::
       :::column span="":::
          选择" **自定义方向"后**，将启用 、 `alpha` 和 `beta` `gamma` 字段。
          <!--To understand how each axis works, navigate to [Alpha][alpha], [Beta][beta], and [Gamma][gamma].  -->
          <!--todo: update links to alpha, beta, and gamma section when available -->
          您还可以通过拖动方向模型来设置 **自定义方向**。  在 `Shift` 拖动以沿轴旋转之前 `alpha` 按住。

          :::image type="complex" source="../media/device-mode-console-sensors-orientation-custom.msft.png" alt-text="方向模型" lightbox="../media/device-mode-console-sensors-orientation-custom.msft.png":::
             方向 **模型**
          :::image-end:::
       :::column-end:::
    :::row-end:::


<!-- ====================================================================== -->
<!-- links -->
<!--
[WebFundamentasNativeHardwareDeviceOrientationIndex]: /web/fundamentals/native-hardware/device-orientation/index "Device Orientation & Motion"
[WebFundamentasNativeHardwareDeviceOrientationIndexAlpha]: /web/fundamentals/native-hardware/device-orientation/index#alpha "Alpha - Device Orientation & Motion"
[WebFundamentasNativeHardwareDeviceOrientationIndexBeta]: /web/fundamentals/native-hardware/device-orientation/index#beta "Beta - Device Orientation & Motion"
[WebFundamentasNativeHardwareDeviceOrientationIndexGamma]: /web/fundamentals/native-hardware/device-orientation/index#gamma "Gamma - Device Orientation & Motion"
-->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/orientation)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [][KayceBasques]

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
