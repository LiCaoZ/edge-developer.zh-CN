---
title: 查看和编辑本地存储
description: 如何使用"本地管理"窗格和控制台查看和编辑 localStorage 键值对存储值对。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: d5c85422f4ef3fc2f1414c637bd5dfd2e74a7102
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430127"
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
# <a name="view-and-edit-local-storage"></a>查看和编辑本地存储

若要查看、编辑和删除 [localStorage 键](https://developer.mozilla.org/docs/Web/API/Window/localStorage) 值对，请使用 **Application** 工具。


<!-- ====================================================================== -->
## <a name="view-localstorage-keys-and-values"></a>查看 localStorage 键和值

1. 单击" **应用程序"** 选项卡以打开 **"应用程序"** 工具。  “**清单**”窗格默认显示。

   :::image type="content" source="../media/storage-application-manifest.msft.png" alt-text="&quot;清单&quot;窗格。" lightbox="../media/storage-application-manifest.msft.png":::

1. 展开“**本地存储**”菜单。

   :::image type="content" source="../media/storage-application-local-storage.msft.png" alt-text="&quot;本地存储菜单。" lightbox="../media/storage-application-local-storage.msft.png":::

1. 单击域以查看键值对。

   :::image type="content" source="../media/storage-application-local-storage-view-key-value.msft.png" alt-text="https://www.bing.com域的 localStorage 键值对" lightbox="../media/storage-application-local-storage-view-key-value.msft.png":::

1. 单击表格的一行以查看表格下方的查看器中的值。

   :::image type="content" source="../media/storage-application-local-storage-view-key-value-selected.msft.png" alt-text="查看键eventLogQueue_Online值。" lightbox="../media/storage-application-local-storage-view-key-value-selected.msft.png":::


<!-- ====================================================================== -->
## <a name="create-a-new-localstorage-key-value-pair"></a>创建新的 localStorage 键值对

1. [查看域的 localStorage 键值对](#view-localstorage-keys-and-values)。

1. 双击表的空白部分。  DevTools 将新建行，并将光标停留在**键**列。

   :::image type="content" source="../media/storage-application-local-storage-new-key-value.msft.png" alt-text="要双击以创建新的键值对的表的空部分。" lightbox="../media/storage-application-local-storage-new-key-value.msft.png":::


<!-- ====================================================================== -->
## <a name="edit-localstorage-keys-or-values"></a>编辑 localStorage 键或值

1. [查看域的 localStorage 键值对](#view-localstorage-keys-and-values)。

1. 双击“**键**”或“**值**”列中的单元格以编辑该键或值。

   :::image type="content" source="../media/storage-application-local-storage-edit-key-value.msft.png" alt-text="编辑 localStorage 密钥。" lightbox="../media/storage-application-local-storage-edit-key-value.msft.png":::


<!-- ====================================================================== -->
## <a name="delete-localstorage-key-value-pairs"></a>删除 localStorage 键值对

1. [查看域的`localStorage`键值对](#view-localstorage-keys-and-values)。

1. 单击要删除的键值对。  DevTools 会以蓝色将其突出显示以表示其已选中。

1. 按 `Delete`，或单击 **"删除所选** (![删除所选内容](../media/delete-icon.msft.png) 。) 。


<!-- ====================================================================== -->
## <a name="delete-all-localstorage-key-value-pairs-for-a-domain"></a>删除域的所有`localStorage`键值对

1. [查看域的`localStorage`键值对](#view-localstorage-keys-and-values)。

1. 单击 **"清除所有 (**![全部清除"。](../media/clear-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="interact-with-localstorage-from-the-console"></a>通过控制台与 localStorage 交互

由于可以在控制台中运行 JavaScript，**** 并且控制台可以访问页面的 **** JavaScript `localStorage` 上下文，因此可以从控制台**进行交互**。

1. 如果要访问除了显示页面以外域的`localStorage`键值对，使用“**JavaScript 上下文**”菜单更改**控制台**的 JavaScript 上下文。

   :::image type="content" source="../media/storage-console-local-storage.msft.png" alt-text="更改控制台的 JavaScript 上下文。" lightbox="../media/storage-console-local-storage.msft.png":::

1. 在控制台中运行`localStorage`表达式，与在 JavaScript 中一样。

:::image type="content" source="../media/storage-console-local-storage-interaction.msft.png" alt-text="从控制台与 localStorage 交互。" lightbox="../media/storage-console-local-storage-interaction.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/localstorage)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
