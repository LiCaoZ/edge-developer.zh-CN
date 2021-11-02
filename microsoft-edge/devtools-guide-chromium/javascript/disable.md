---
description: 打开命令菜单并运行"禁用 JavaScript"命令。
title: 使用 DevTools Microsoft Edge JavaScript
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: e5c933332d058e1796a50c0f79574c56bf8a7310
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12139554"
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
# <a name="disable-javascript-with-microsoft-edge-devtools"></a>使用 DevTools Microsoft Edge JavaScript

若要在浏览器不支持 JavaScript 时查看网页的呈现效果，请暂时关闭 JavaScript。

完成以下操作以检查网页在关闭 JavaScript 时如何显示和行为。

1.  [打开 Microsoft Edge DevTools][DevToolsOpen]。
1.  选择 `Control` + `Shift` + `P` (Windows、Linux) 或 `Command` + `Shift` + `P` (macOS) 打开命令**菜单**。

    :::image type="complex" source="../media/javascript-console-command.msft.png" alt-text="命令菜单" lightbox="../media/javascript-console-command.msft.png":::
       **命令菜单**
    :::image-end:::

1.  开始键入 ， `javascript` 选择 **"禁用 JavaScript"，** 然后选择 `Enter` 运行命令。  JavaScript 现已禁用。

    :::image type="complex" source="../media/javascript-console-command-javascript.msft.png" alt-text="在命令菜单中选择&quot;禁用 JavaScript&quot;" lightbox="../media/javascript-console-command-javascript.msft.png":::
       在 **命令菜单中选择** "禁用 **JavaScript"**
    :::image-end:::

    源旁边的黄色 **警告图标提醒** 你 JavaScript 已禁用。

    :::image type="complex" source="../media/javascript-console-javascript-disabled-warning.msft.png" alt-text="&quot;源&quot;旁边的警告图标" lightbox="../media/javascript-console-javascript-disabled-warning.msft.png":::
       "源"旁边的警告 **图标**
    :::image-end:::

只要打开 DevTools，JavaScript 在选项卡中就保持禁用状态。

你可能想要刷新页面，以检查网页在加载时是否以及如何依赖于 JavaScript。

若要重新启用 JavaScript，请完成以下操作。

*   再次 **打开命令菜单** 并运行 `Enable JavaScript` 命令。
*   关闭 DevTools。


<!-- ====================================================================== -->
<!-- links -->
[DevToolsOpen]: ../open/index.md "打开 Microsoft Edge 开发人员工具 | Microsoft Docs"


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/disable)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [][KayceBasques]

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
