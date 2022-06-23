---
title: 查看和编辑本地存储
description: 如何使用“本地存储”窗格和控制台查看和编辑 localStorage 键值对。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: e160c83b2b68b2acee04c4379c7581e448aafb42
ms.sourcegitcommit: 92a0cd0a86cc8ef49e4f90ea660d43106a4d19b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2022
ms.locfileid: "12610840"
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

若要查看、编辑和删除 [localStorage](https://developer.mozilla.org/docs/Web/API/Window/localStorage) 键值对，请 **使用应用程序工具** 。


<!-- ====================================================================== -->
## <a name="view-localstorage-keys-and-values"></a>查看 localStorage 键和值

1. 单击“ **应用程序** ”选项卡打开“ **应用程序** ”工具。  “**清单**”窗格默认显示。

   ![清单窗格。](../media/storage-application-manifest.msft.png)

1. 展开“**本地存储**”菜单。

   ![“本地存储”菜单。](../media/storage-application-local-storage.msft.png)

1. 单击域可查看键值对。

   ![https://www.bing.com域的 localStorage 键值对](../media/storage-application-local-storage-view-key-value.msft.png)

1. 单击表的一行可在表下方的查看器中查看值。

   ![查看eventLogQueue_Online键的值。](../media/storage-application-local-storage-view-key-value-selected.msft.png)


<!-- ====================================================================== -->
## <a name="create-a-new-localstorage-key-value-pair"></a>创建新的 localStorage 键值对

1. [查看域的 localStorage 键值对](#view-localstorage-keys-and-values)。

1. 双击表的空白部分。  DevTools 将新建行，并将光标停留在**键**列。

   ![要双击表的空部分，以便创建新的键值配对。](../media/storage-application-local-storage-new-key-value.msft.png)


<!-- ====================================================================== -->
## <a name="edit-localstorage-keys-or-values"></a>编辑 localStorage 键或值

1. [查看域的 localStorage 键值对](#view-localstorage-keys-and-values)。

1. 双击“**键**”或“**值**”列中的单元格以编辑该键或值。

   ![编辑 localStorage 密钥。](../media/storage-application-local-storage-edit-key-value.msft.png)


<!-- ====================================================================== -->
## <a name="delete-localstorage-key-value-pairs"></a>删除 localStorage 键值对

1. [查看域的`localStorage`键值对](#view-localstorage-keys-and-values)。

1. 单击要删除的键值配对。  DevTools 会以蓝色将其突出显示以表示其已选中。

1. 按 `Delete`下，或单击“ **删除选定** (![删除已选中。](../media/delete-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="delete-all-localstorage-key-value-pairs-for-a-domain"></a>删除域的所有`localStorage`键值对

1. [查看域的`localStorage`键值对](#view-localstorage-keys-and-values)。

1. 单击 **“全部清除** (![全部清除。](../media/clear-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="interact-with-localstorage-from-the-console"></a>通过控制台与 localStorage 交互

由于可以在**控制台**中运行 JavaScript，并且**由于控制台**有权访问页面的 JavaScript 上下文，因此可以从**控制台**进行交`localStorage`互。

1. 如果要访问除了显示页面以外域的`localStorage`键值对，使用“**JavaScript 上下文**”菜单更改**控制台**的 JavaScript 上下文。

   ![更改控制台的 JavaScript 上下文。](../media/storage-console-local-storage.msft.png)

1. 在控制台中运行`localStorage`表达式，与在 JavaScript 中一样。

![从控制台与 localStorage 交互。](../media/storage-console-local-storage-interaction.msft.png)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/storage/localstorage/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
