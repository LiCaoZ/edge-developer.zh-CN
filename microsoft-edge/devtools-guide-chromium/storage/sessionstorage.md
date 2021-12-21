---
title: 查看和编辑会话存储
description: 如何使用会话存储窗格和控制台查看和编辑 sessionStorage。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: 89c9e3cbfc49064c2886a1a116781e1c732c381a
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286665"
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
# <a name="view-and-edit-session-storage"></a>查看和编辑会话存储

本指南将演示如何使用 [Microsoft Edge DevTools](../../devtools-guide-chromium/index.md) 查看、编辑和删除 [sessionStorage](https://developer.mozilla.org/docs/Web/API/Window/sessionStorage) 键值对。


<!-- ====================================================================== -->
## <a name="view-sessionstorage-keys-and-values"></a>查看 sessionStorage 的键和值

1.  选择**应用程序**选项卡打开**应用程序**工具。  默认显示**清单**面板。

    :::image type="complex" source="../media/storage-application-manifest.msft.png" alt-text="清单窗格" lightbox="../media/storage-application-manifest.msft.png":::
       **清单**窗格
    :::image-end:::

1.  展开**会话存储**菜单。

    :::image type="complex" source="../media/storage-application-storage-session-storage.msft.png" alt-text="会话存储菜单" lightbox="../media/storage-application-storage-session-storage.msft.png":::
       **会话存储**菜单
    :::image-end:::

1.  选择域以查看键值对。

    :::image type="complex" source="../media/storage-application-storage-session-storage-domain.msft.png" alt-text="sessionStorage 的键值对" lightbox="../media/storage-application-storage-session-storage-domain.msft.png":::
       `sessionStorage` 的键值对
    :::image-end:::

1.  选择表的行以查看该表下方的查看器中的值。

    :::image type="complex" source="../media/storage-application-storage-session-storage-domain-key-value-selected.msft.png" alt-text="查看 x-sid 键的值" lightbox="../media/storage-application-storage-session-storage-domain-key-value-selected.msft.png":::
       查看 `x-sid` 键的值
    :::image-end:::


<!-- ====================================================================== -->
## <a name="create-a-new-sessionstorage-key-value-pair"></a>新建 sessionStorage 键值对

1.  [查看域的 sessionStorage 键值对](#view-sessionstorage-keys-and-values)。
1.  双击表的空白部分。  DevTools 将新建行，并将光标停留在**键**列。

    :::image type="complex" source="../media/storage-application-storage-session-storage-domain-key-value-new.msft.png" alt-text="为了新建键值对要双击的表的空白部分" lightbox="../media/storage-application-storage-session-storage-domain-key-value-new.msft.png":::
       为了新建键值对要双击的表的空白部分
    :::image-end:::


<!-- ====================================================================== -->
## <a name="edit-sessionstorage-keys-or-values"></a>编辑 sessionStorage 键或值

1.  [查看域的 sessionStorage 键值对](#view-sessionstorage-keys-and-values)。
1.  双击**键**或**值**列以编辑该键或值。

    :::image type="complex" source="../media/storage-application-storage-session-storage-domain-key-value-edit.msft.png" alt-text="编辑 sessionStorage 键" lightbox="../media/storage-application-storage-session-storage-domain-key-value-edit.msft.png":::
       编辑 `sessionStorage` 键
    :::image-end:::


<!-- ====================================================================== -->
## <a name="delete-sessionstorage-key-value-pairs"></a>删除 sessionStorage 的键值对

1.  [查看域的 `sessionStorage` 键值对](#view-sessionstorage-keys-and-values)。
1.  选择要删除的键值对。  DevTools 会以蓝色将其突出显示以表示其已选中。
1.  Select the `Delete` key or choose Delete Selected ** (** Delete ![ Selected ](../media/delete-icon.msft.png)) .


<!-- ====================================================================== -->
## <a name="delete-all-sessionstorage-key-value-pairs-for-a-domain"></a>删除域的所有 sessionStorage 键值对

1.  [查看域的 `sessionStorage` 键值对](#view-sessionstorage-keys-and-values)。
1.  Choose **Clear All (** Clear All ![ ](../media/clear-icon.msft.png)) .


<!-- ====================================================================== -->
## <a name="interact-with-sessionstorage-from-the-console"></a>通过控制台与 sessionStorage 交互

由于你通过**控制台**运行 JavaScript，并且**控制台**有权访问页面的 JavaScript 上下文，因此可以通过**控制台**与 `sessionStorage` 交互。

1.  如果要访问除了你所在页面以外域的 `sessionStorage` 键值对，可以使用 **JavaScript 上下文**菜单更改**控制台**的 JavaScript 上下文。

    :::image type="complex" source="../media/storage-console-domain-selection.msft.png" alt-text="更改控制台的 JavaScript 上下文" lightbox="../media/storage-console-domain-selection.msft.png":::
       更改**控制台**的 JavaScript 上下文
    :::image-end:::

1.  使用**控制台**运行 `sessionStorage` 表达式，与 JavaScript 一样。

    :::image type="complex" source="../media/storage-console-session-storage-keys.msft.png" alt-text="通过控制台与 sessionStorage 交互" lightbox="../media/storage-console-session-storage-keys.msft.png":::
       通过**控制台**与 `sessionStorage` 交互
    :::image-end:::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/sessionstorage)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
