---
title: 查看和编辑会话存储
description: 如何使用会话存储窗格和控制台查看和编辑 sessionStorage。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 82cd717ce419a20c65353fb07177793e1201cc98
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631341"
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

若要查看、编辑和删除 [sessionStorage](https://developer.mozilla.org/docs/Web/API/Window/sessionStorage) 键值对，请 **使用应用程序工具** 。


<!-- ====================================================================== -->
## <a name="view-sessionstorage-keys-and-values"></a>查看 sessionStorage 的键和值

1. 在 DevTools 中，单击“ **应用程序** ”选项卡 **打开应用程序工具** 。  默认显示**清单**面板。

   ![清单窗格。](../media/storage-application-manifest.msft.png)

1. 展开**会话存储**菜单。

   ![会话存储菜单。](../media/storage-application-storage-session-storage.msft.png)

1. 单击域可查看键值对。

   ![sessionStorage 键值对。](../media/storage-application-storage-session-storage-domain.msft.png)

1. 单击表的一行可在表下方的查看器中查看值。

   ![查看 x-sid 键的值。](../media/storage-application-storage-session-storage-domain-key-value-selected.msft.png)


<!-- ====================================================================== -->
## <a name="create-a-new-sessionstorage-key-value-pair"></a>新建 sessionStorage 键值对

1. [查看域的 sessionStorage 键值对](#view-sessionstorage-keys-and-values)。

1. 双击表的空白部分。  DevTools 将新建行，并将光标停留在**键**列。

   ![要双击表的空部分以创建新的键值对。](../media/storage-application-storage-session-storage-domain-key-value-new.msft.png)


<!-- ====================================================================== -->
## <a name="edit-sessionstorage-keys-or-values"></a>编辑 sessionStorage 键或值

1. [查看域的 sessionStorage 键值对](#view-sessionstorage-keys-and-values)。

1. 双击**键**或**值**列以编辑该键或值。

   ![编辑 sessionStorage 密钥。](../media/storage-application-storage-session-storage-domain-key-value-edit.msft.png)


<!-- ====================================================================== -->
## <a name="delete-sessionstorage-key-value-pairs"></a>删除 sessionStorage 的键值对

1. [查看域的 `sessionStorage` 键值对](#view-sessionstorage-keys-and-values)。

1. 单击要删除的键值对。  DevTools 会以蓝色将其突出显示以表示其已选中。

1. 按 `Delete` 或单击 **“删除选定** (![删除已选中。](../media/delete-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="delete-all-sessionstorage-key-value-pairs-for-a-domain"></a>删除域的所有 sessionStorage 键值对

1. [查看域的 `sessionStorage` 键值对](#view-sessionstorage-keys-and-values)。

1. 单击 **“全部清除** (![全部清除。](../media/clear-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="interact-with-sessionstorage-from-the-console"></a>通过控制台与 sessionStorage 交互

由于可以在**控制台**中运行 JavaScript，并且由于**控制台**有权访问页面的 JavaScript 上下文，因此可以从**控制台**进行交`sessionStorage`互。

1. 如果要访问除了你所在页面以外域的 `sessionStorage` 键值对，可以使用 **JavaScript 上下文**菜单更改**控制台**的 JavaScript 上下文。

   ![更改控制台的 JavaScript 上下文。](../media/storage-console-domain-selection.msft.png)

1. 使用**控制台**运行 `sessionStorage` 表达式，与 JavaScript 一样。

   ![从控制台与 sessionStorage 交互。](../media/storage-console-session-storage-keys.msft.png)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/storage/sessionstorage/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
