---
title: 使用传感器工具模拟设备方向
description: 使用传感器工具的"方向"部分模拟设备方向。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: fe656e205cc98dd2782bf343e2cc2c120d78481b
ms.sourcegitcommit: 9caa4aac0a339a76e7f1e0f0f5d6d85a2492ea8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "12325590"
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
# <a name="simulate-device-orientation-with-the-sensors-tool"></a>使用传感器工具模拟设备方向

模拟来自 DevTools 中的不同设备方向。

<!--todo: update device orientation section when available -->

1.  按 `Control` + `Shift` + `P` (Windows、Linux) 或 (`Command` + `Shift` + `P` macOS) 打开命令**菜单**。

    :::image type="content" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单。" lightbox="../media/device-mode-console-command-menu.msft.png":::

1.  键入 `sensors` ，选择 **显示传感器**，然后选择 `Enter` 。  传感器 **工具** 在 DevTools 窗口底部打开。

1.  从 **"方向**"列表中，选择预设方向之一（如 ）或选择"自定义方向" `Portrait upside down` 来提供你自己的精确方向。 ****

:::image type="content" source="../media/device-mode-console-sensors-orientation-portrait-upside-down.msft.png" alt-text="从&quot;方向&quot;列表中选择&quot;纵向&quot;向下。" lightbox="../media/device-mode-console-sensors-orientation-portrait-upside-down.msft.png":::

如果选择" **自定义方向"，** 则启用 、 和 `alpha` `beta` `gamma` 旋转轴字段。
<!--To understand how each axis works, see [Device Orientation & Motion - Rotation data](https://developers.google.com/web/fundamentals/native-hardware/device-orientation#rotation_data). -->
<!-- todo: link to a local copy of that article section when available; see "original page" below -->
您还可以通过拖动方向模型来设置 **自定义方向**。  例如，若要沿轴 `alpha` 旋转，请按住 `Shift` ，然后再拖动：

:::image type="content" source="../media/device-mode-console-sensors-orientation-custom.msft.png" alt-text="方向模型。" lightbox="../media/device-mode-console-sensors-orientation-custom.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/orientation)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
