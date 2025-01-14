---
title: 使用传感器工具模拟设备方向
description: 使用传感器工具的“方向”部分模拟设备方向。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 738296817a516be603a6864bb632a0b21d12d3b3
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631149"
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

从 DevTools 中模拟不同的设备方向。

<!--todo: update device orientation section when available -->

1. 按“`Ctrl`+`Shift`+`P`”(Windows、Linux)或“`Command`+`Shift`+`P`”(macOS)以打开“**命令菜单**”。

   ![命令菜单。](../media/device-mode-console-command-menu.msft.png)

1. 键入 `sensors`，选择 **“显示传感器**”，然后按下 `Enter`。  **传感器**工具在 DevTools 窗口底部打开。

1. 在 **“方向** ”列表中，选择一个预设方向，例如 `Portrait upside down`，或选择 **“自定义方向** ”以提供自己的确切方向。

![从方向列表中选择“纵向倒置”。](../media/device-mode-console-sensors-orientation-portrait-upside-down.msft.png)

如果选择 **“自定义方向**”`alpha``beta`，则启用旋转轴字段和`gamma`旋转轴字段。
<!--To understand how each axis works, see [Device Orientation & Motion - Rotation data](https://web.dev/native-hardware-device-orientation/#rotation-data). -->
<!-- todo: link to a local copy of that article section when available; see "original page" below -->
还可以通过拖动 **方向模型**来设置自定义方向。  例如，若要沿 `alpha` 轴旋转，请在拖动前按住 `Shift` ：

![方向模型。](../media/device-mode-console-sensors-orientation-custom.msft.png)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/device-mode/orientation/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
