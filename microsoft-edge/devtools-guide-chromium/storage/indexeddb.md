---
title: 查看和更改 IndexedDB 数据
description: 如何使用应用程序面板和代码段查看和更改 IndexedDB 数据。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 29a657fe44e7f764324fae7841540bb64ff35f5a
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12630492"
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
# <a name="view-and-change-indexeddb-data"></a>查看和更改 IndexedDB 数据

若要查看和更改 [IndexedDB](https://developer.mozilla.org/docs/Web/API/IndexedDB_API) 数据，请 **使用应用程序工具** 。


<!-- ====================================================================== -->
## <a name="view-indexeddb-data"></a>查看 IndexedDB 数据

1. 在 DevTools 中，单击“ **应用程序** ”选项卡 **打开应用程序工具** 。  通常默认**清单**窗格打开。

   ![清单窗格。](../media/storage-application-manifest-empty.msft.png)

1. 展开 “**IndexedDB**” 菜单，查看哪些数据库可用。

   ![IndexedDB 菜单。](../media/storage-application-storage-indexeddb.msft.png)

   * ![ (数据库图标。](../media/database-icon.msft.png)) `notes - https://mdn.github.io`表示数据库，其中`notes`是数据库的名称，`https://mdn.github.io`是访问数据库的源。

   * ![ (对象存储图标。](../media/object-store-icon.msft.png)) `notes`是对象存储。

   *  **标题**和 **正文**是[索引](https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Using_IndexedDB#Using_an_index)。

   > [!NOTE]
   > **已知限制**  第三方数据库不可见。  例如，如果在页面上使用嵌 `<iframe>` 入广告，且广告网络使用 IndexedDB，则广告网络的 IndexedDB 数据不可见。  请参阅 [问题 #943770](https://crbug.com/943770)。

1. 选择数据库，查看源和版本号。

   ![备注数据库。](../media/storage-application-storage-indexeddb-notes_db.msft.png)

1. 单击对象存储，查看键值对。

   > [!NOTE]
   > IndexedDB 数据不会实时更新。  请参阅 [Refresh IndexedDB 数据](#refresh-indexeddb-data)。

   ![备注对象存储。](../media/storage-application-storage-indexeddb-notes_db-notes_os.msft.png)

   *  **总条目数**是对象存储中键值对的总数。

   *  **密钥生成器值**是下一个可用密钥。  此字段仅在使用[密钥生成器](https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Basic_Concepts_Behind_IndexedDB#gloss_keygenerator)时显示。

1. 单击 **“值** ”列中的单元格以展开该值。

   ![查看 IndexedDB 值。](../media/storage-application-storage-indexeddb-notes_db-notes_os-edge-chromium.msft.png)

1. 单击索引（如下图中的 **标题** 或 **正文** ）以根据该索引的值对对象存储进行排序。

   ![按索引对对象存储进行排序。](../media/storage-application-storage-indexeddb-notes_db-notes_os-title.msft.png)


<!-- ====================================================================== -->
## <a name="refresh-indexeddb-data"></a>刷新 IndexedDB 数据

**应用程序**工具中的 IndexedDB 值不会实时更新。

*  若要刷新数据，请查看对象存储，然后单击 **“刷新** ” (![刷新。](../media/reload-icon.msft.png)) 。
*  若要刷新所有数据，请查看数据库，然后单击 **“刷新数据库**”。

![查看数据库。](../media/storage-application-storage-indexeddb-notes_db-notes_os-refresh-database.msft.png)


<!-- ====================================================================== -->
## <a name="edit-indexeddb-data"></a>编辑 IndexedDB 数据

无法从 **应用程序工具编辑** IndexedDB 密钥和值。  但是，由于 DevTools 有权访问页面上下文，因此可以在 DevTools 中运行 JavaScript 代码来编辑 IndexedDB 数据。

### <a name="edit-indexeddb-data-with-snippets"></a>使用代码段编辑 IndexedDB 数据

[代码段](../javascript/snippets.md)是一种在 DevTools 中存储和运行 JavaScript 代码的方法。  运行代码段时，结果将记录到**控制台**。  可以使用代码片段运行 JavaScript 代码来编辑 IndexedDB 数据库。

![使用代码片段与 IndexedDB 交互。](../media/storage-sources-snippets-indexeddb-output.msft.png)


<!-- ====================================================================== -->
## <a name="delete-indexeddb-data"></a>删除 IndexedDB 数据

### <a name="delete-an-indexeddb-key-value-pair"></a>删除 IndexedDB 键值对

1. [查看 IndexedDB 对象存储](#view-indexeddb-data)。

1. 单击要删除的键值对。  DevTools 会突出显示它以表明已选中。

   ![单击键值对以将其删除。](../media/storage-application-storage-indexeddb-notes_db-notes_os2.msft.png)

1. 按 `Delete` 或单击 **“删除选定** (![删除已选中。](../media/delete-icon.msft.png)) 。

   ![对象存储在删除键值对后的外观。](../media/storage-application-storage-indexeddb-notes_db-notes_os-delete-selected.msft.png)

### <a name="delete-all-key-value-pairs-in-an-object-store"></a>删除对象存储中所有键值对

1. [查看 IndexedDB 对象存储](#view-indexeddb-data)。

   ![查看对象存储。](../media/storage-application-storage-indexeddb-notes_db-notes_os-clear-object-store.msft.png)

1. 单击 **“清除对象存储** (![清除对象存储。](../media/clear-icon.msft.png)) 。

### <a name="delete-an-indexeddb-database"></a>删除 IndexedDB 数据库

1. [查看要删除的 IndexedDB 数据库](#view-indexeddb-data)。

1. 单击 **“删除数据库**”。

   ![“删除数据库”按钮。](../media/storage-application-storage-indexeddb-notes_db-delete-database.msft.png)

### <a name="delete-all-indexeddb-storage"></a>删除所有 IndexedDB 存储

1. 打开“**清除存储**”窗格。

1. 确保已启用 **IndexedDB** 复选框。

1. 单击 **“清除站点数据**”。

   ![“清除存储”窗格。](../media/storage-application-clear-storage-indexeddb-clear-site-data.msft.png)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/storage/indexeddb/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
