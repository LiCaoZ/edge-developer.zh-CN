---
title: 查看、编辑和删除 Cookie
description: 如何使用 DevTools 查看、编辑和删除页面的 HTTP Microsoft Edge Cookie。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: e33276d40cc9726f3e050cc51622841715ab4cbb
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12317832"
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
# <a name="view-edit-and-delete-cookies"></a>查看、编辑和删除 Cookie

[HTTP Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies) 主要用于管理用户会话、存储用户个性化首选项和跟踪用户行为。  Cookie 也是导致各种网页上出现麻烦的 **此页面使用 Cookie** 许可表单的源头。  以下指南将指导你如何使用 [Microsoft Edge DevTools](/microsoft-edge/devtools-guide-chromium) 查看、编辑和删除网页的 HTTP Cookie。


<!-- ====================================================================== -->
## <a name="open-the-cookies-pane"></a>打开“Cookie”窗格

1.  [打开 DevTools](/microsoft-edge/devtools-guide-chromium/open)。
1.  选择“**应用程序**”选项卡以打开“**应用程序**”面板。  “**清单**”窗格应打开。

    :::image type="complex" source="../media/storage-application-manifest-empty.msft.png" alt-text="清单窗格" lightbox="../media/storage-application-manifest-empty.msft.png":::
       图 1：清单窗格
    :::image-end:::

1.  在“**存储**“下，展开 “**Cookie**”，然后选择一个源。

    :::image type="complex" source="../media/storage-application-storage-cookies-selected.msft.png" alt-text="“Cookie”窗格" lightbox="../media/storage-application-storage-cookies-selected.msft.png":::
       图 2：“Cookie” 窗格
    :::image-end:::


<!-- ====================================================================== -->
## <a name="fields"></a>字段

**Cookies** 表包含以下字段。

*   **名称**。  Cookie 的名称。
*   **值**。  Cookie 的值。
*   **域**。  允许接收 Cookie 的主机。  导航到 [Cookie 的范围](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Scope_of_cookies)。
*   **路径**。  URL 必须存在于请求的 URL 中以发送 `Cookie` 标头。  导航到 [Cookie 的范围](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Scope_of_cookies)。
*   **到期日期/最长期限**.  Cookie 的到期日期或最长期限。  导航到“[永久 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Permanent_cookies)。  对于[会话 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Session_cookies)，此值始终为 `Session`。
*   **大小**。  Cookie 的大小（以字节为单位）。
*   **HTTP**。  如果为 true，则此字段指示应仅通过 HTTP 使用 Cookie，不允许 JavaScript 修改。  导航到 [HttpOnly Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Secure_and_HttpOnly_cookies)。
*   **安全**。  如果为 true，则此字段指示必须通过安全的 HTTPS 连接将 Cookie 发送到服务器。  导航到“[安全 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Secure_and_HttpOnly_cookies)”。
*   **SameSite**。  包含 `strict`，当 Cookie 使用实验性 [Samesite](https://developer.mozilla.org/docs/Web/HTTP/Cookies#SameSite_cookies) 属性时包含 `lax`。
*   **优先级**。  包含 `low` `medium` 、 (默认) ，或者 Cookie 是否使用已弃 `high` 用 [Cookie Priority](https://bugs.chromium.org/p/chromium/issues/detail?id=232693) 属性。


<!-- ====================================================================== -->
## <a name="filter-cookies"></a>筛选 Cookie

使用“**筛选器**”文本框按**名称**或**值**筛选 Cookie。  不支持按其他字段筛选。

:::image type="complex" source="../media/storage-application-storage-cookies-filter-id.msft.png" alt-text="筛选出任何不包含文本 ID 的 Cookie" lightbox="../media/storage-application-storage-cookies-filter-id.msft.png":::
   图 3：筛选出任何不包含文本的 Cookie `ID`
:::image-end:::


<!-- ====================================================================== -->
## <a name="edit-a-cookie"></a>编辑 Cookie

**名称**、**值**、**域**、**路径**和**过期日期/最长期限**字段是可编辑的。
双击某个字段进行编辑。

:::image type="complex" source="../media/storage-application-storage-cookies-rename.msft.png" alt-text="将 Cookie 的名称设置为 DEVTOOLS！" lightbox="../media/storage-application-storage-cookies-rename.msft.png":::
   图 4：将 Cookie 的名称设置为 `DEVTOOLS!`
:::image-end:::


<!-- ====================================================================== -->
## <a name="delete-cookies"></a>删除 Cookie

Choose a cookie and choose **Delete Selected (** Delete Selected) to delete the specific ![ ](../media/delete-icon.msft.png) cookie.

:::image type="complex" source="../media/storage-application-storage-cookies-delete-selected.msft.png" alt-text="删除特定 Cookie" lightbox="../media/storage-application-storage-cookies-delete-selected.msft.png":::
   图 5：删除特定 Cookie
:::image-end:::

Choose **Clear All (** Clear All) to delete all ![ ](../media/clear-icon.msft.png) cookies.

:::image type="complex" source="../media/storage-application-storage-cookies-clear-all.msft.png" alt-text="清除所有 Cookie" lightbox="../media/storage-application-storage-cookies-clear-all.msft.png":::
   图 6：清除所有 Cookie
:::image-end:::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/cookies)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
