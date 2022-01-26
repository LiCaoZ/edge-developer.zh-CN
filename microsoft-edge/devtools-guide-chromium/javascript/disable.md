---
title: 禁用 JavaScript
description: 若要在 DevTools 中禁用 JavaScript，请打开命令菜单并运行"禁用 JavaScript"命令。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: a1712c3cee4b4972d9d03c6bbbae6d164bdf83b8
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12322954"
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
# <a name="disable-javascript"></a>禁用 JavaScript

若要在浏览器不支持 JavaScript 时查看网页的呈现效果，请暂时关闭 JavaScript。

完成以下操作以检查网页在关闭 JavaScript 时如何显示和行为。

1.  [打开 Microsoft Edge DevTools](../open/index.md)。
1.  选择 `Control`+`Shift`+`P` (Windows、Linux)或 `Command`+`Shift`+`P` (macOS)以打开 **命令菜单**。

    :::image type="complex" source="../media/javascript-console-command.msft.png" alt-text="命令菜单。" lightbox="../media/javascript-console-command.msft.png":::
       **命令菜单**
    :::image-end:::

1.  开始键入 ， `javascript` 选择 **"禁用 JavaScript"，** 然后选择 `Enter` 运行命令。  JavaScript 现已禁用。

    :::image type="complex" source="../media/javascript-console-command-javascript.msft.png" alt-text="在&quot;命令&quot;菜单中选择&quot;禁用 JavaScript&quot;。" lightbox="../media/javascript-console-command-javascript.msft.png":::
       在 **命令菜单中选择** "禁用 **JavaScript"**
    :::image-end:::

    源旁边的黄色 **警告图标提醒** 你 JavaScript 已禁用。

    :::image type="complex" source="../media/javascript-console-javascript-disabled-warning.msft.png" alt-text="&quot;源&quot;旁边的警告图标。" lightbox="../media/javascript-console-javascript-disabled-warning.msft.png":::
       "源"旁边的警告 **图标**
    :::image-end:::

只要打开 DevTools，JavaScript 在选项卡中就保持禁用状态。

你可能想要刷新页面，以检查网页在加载时是否以及如何依赖于 JavaScript。

若要重新启用 JavaScript，请完成以下操作。

*   再次 **打开命令菜单** 并运行 `Enable JavaScript` 命令。
*   关闭 DevTools。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/disable)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![Creative Commons License。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
