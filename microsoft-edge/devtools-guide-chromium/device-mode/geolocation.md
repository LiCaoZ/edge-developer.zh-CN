---
description: 在 DevTools 中打开传感器工具，然后从"地理位置"列表中选择坐标。
title: 使用传感器工具替代地理位置
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: a0364b2644b533ceb6d1f486a096d075bf60313f
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12140961"
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

如果您要构建的 UI 根据用户所在的位置而更改，您可能需要确保网站在世界各地的不同位置正常运行。  若要在 DevTools 中Microsoft Edge地理位置，请完成以下操作。

1.  选择 `Control` + `Shift` + `P` (Windows、Linux) 或 `Command` + `Shift` + `P` (macOS) 打开命令**菜单**。

    :::image type="content" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单的屏幕截图。":::

1.  键入 `sensors` ，选择 **面板：显示传感器**，然后选择 `Enter` 。  传感器 **工具** 在 DevTools 窗口底部打开。
1.  从"**** 地理位置"列表中选择预设城市之一（如 ），或选择"自定义位置"以输入自定义经度和纬度坐标，或选择"位置不可用"以显示网站在用户位置不可用时的行为方式。 `Tokyo` **** ****

    :::image type="content" source="../media/device-mode-console-sensors-geolocation-tokyo.msft.png" alt-text="从地理位置列表中选择东京的屏幕截图。":::

<!-- /web/fundamentals/native-hardware/user-location/index -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/geolocation)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [][KayceBasques]

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
