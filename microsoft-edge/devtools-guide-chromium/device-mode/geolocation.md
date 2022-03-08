---
title: 使用传感器工具替代地理位置
description: 在 DevTools 中打开传感器工具，然后从"地理位置"列表中选择坐标。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 41d5949602f10701a7e4a291f341514987407b8b
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431051"
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
# <a name="override-geolocation-with-the-sensors-tool"></a>使用传感器工具替代地理位置

许多网站利用用户位置来为用户提供更相关的体验。  例如，在用户授予网站访问当前用户位置的权限后，天气网站可能会显示用户区域中的本地天气预报。

<!--todo: add link to user location section when available -->

如果您要构建的 UI 根据用户所在的位置而更改，您可能需要确保网站在世界各地的不同位置正常运行。  若要在 DevTools 中覆盖Microsoft Edge地理位置：

1. 按 `Ctrl``P``Shift`++ (Windows、Linux) 或 `Command``Shift`++`P` (macOS) 打开命令**菜单**。

   :::image type="content" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单的屏幕截图。":::

1. 键入 `sensors`，选择 **面板：显示传感器**，然后按 `Enter`。  传感器 **工具** 在 DevTools 窗口底部打开。

1. 单击 **"地理位置"** 列表，然后：
   *  选择城市，例如 `Tokyo`。
   *  单击 **"其他** "输入自定义经度和纬度坐标。
   *  单击 **"** 位置不可用"以查看当用户的位置不可用时网站的行为方式。

   :::image type="content" source="../media/device-mode-console-sensors-geolocation-tokyo.msft.png" alt-text="从地理位置列表中选择东京的屏幕截图。":::

<!-- /web/fundamentals/native-hardware/user-location/index -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/geolocation)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
