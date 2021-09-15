---
description: 了解如何使用 Microsoft Edge DevTools 查看、编辑和删除页面的 HTTP Cookie。
title: 使用 Microsoft Edge DevTools 查看、编辑和删除 Cookie
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 4f5a352445bd13b82ada82df3a528a1e80aa144e
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976479"
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
# <a name="view-edit-and-delete-cookies-with-microsoft-edge-devtools"></a>使用 Microsoft Edge DevTools 查看、编辑和删除 Cookie  

[HTTP Cookie][MDNHTTPCookies] 主要用于管理用户会话、存储用户个性化首选项和跟踪用户行为。  Cookie 也是导致各种网页上出现麻烦的 **此页面使用 Cookie** 许可表单的源头。  以下指南将指导你如何使用 [Microsoft Edge DevTools][MicrosoftEdgeDevTools] 查看、编辑和删除网页的 HTTP Cookie。  

## <a name="open-the-cookies-pane"></a>打开“Cookie”窗格  

1.  [打开 DevTools][DevToolsOpen]。  
1.  选择“**应用程序**”选项卡以打开“**应用程序**”面板。  “**清单**”窗格应打开。  
    
    :::image type="complex" source="../media/storage-application-manifest-empty.msft.png" alt-text="清单窗格" lightbox="../media/storage-application-manifest-empty.msft.png":::
       图 1：清单窗格  
    :::image-end:::  

1.  在“**存储**“下，展开 “**Cookie**”，然后选择一个源。  
    
    :::image type="complex" source="../media/storage-application-storage-cookies-selected.msft.png" alt-text="“Cookie”窗格" lightbox="../media/storage-application-storage-cookies-selected.msft.png":::
       图 2：“Cookie” 窗格  
    :::image-end:::  

## <a name="fields"></a>字段  

**Cookies** 表包含以下字段。  

*   **名称**。  Cookie 的名称。  
*   **值**。  Cookie 的值。  
*   **域**。  允许接收 Cookie 的主机。  导航到 [Cookie 的范围][MDNHTTPCookiesScope]。  
*   **路径**。  URL 必须存在于请求的 URL 中以发送 `Cookie` 标头。  导航到 [Cookie 的范围][MDNHTTPCookiesScope]。  
*   **到期日期/最长期限**.  Cookie 的到期日期或最长期限。  导航到“[永久 Cookie][MDNHTTPCookiesPermanent]。  对于[会话 Cookie][MDNHTTPCookiesSession]，此值始终为 `Session`。  
*   **大小**。  Cookie 的大小（以字节为单位）。  
*   **HTTP**。  如果为 true，则此字段指示应仅通过 HTTP 使用 Cookie，不允许 JavaScript 修改。  导航到 [HttpOnly Cookie][MDNHTTPCookiesSecure]。  
*   **安全**。  如果为 true，则此字段指示必须通过安全的 HTTPS 连接将 Cookie 发送到服务器。  导航到“[安全 Cookie][MDNHTTPCookiesSecure]”。  
*   **SameSite**。  包含 `strict`，当 Cookie 使用实验性 [Samesite][MDNHTTPCookiesSamesite] 属性时包含 `lax`。  
*   **优先级**。  包含 `low`、`medium` \(default\)，当 Cookie 使用已弃用的 [Cookie Priority][ChromiumIssue232693] 属性时包含 `high`。

## <a name="filter-cookies"></a>筛选 Cookie  

使用“**筛选器**”文本框按**名称**或**值**筛选 Cookie。  不支持按其他字段筛选。  

:::image type="complex" source="../media/storage-application-storage-cookies-filter-id.msft.png" alt-text="筛选出任何不包含文本 ID 的 Cookie" lightbox="../media/storage-application-storage-cookies-filter-id.msft.png":::
   图 3：筛选出任何不包含文本的 Cookie `ID`  
:::image-end:::  

## <a name="edit-a-cookie"></a>编辑 Cookie  

**名称**、**值**、**域**、**路径**和**过期日期/最长期限**字段是可编辑的。  
双击某个字段进行编辑。  

:::image type="complex" source="../media/storage-application-storage-cookies-rename.msft.png" alt-text="将 Cookie 的名称设置为 DEVTOOLS！" lightbox="../media/storage-application-storage-cookies-rename.msft.png":::
   图 4：将 Cookie 的名称设置为 `DEVTOOLS!`  
:::image-end:::  

## <a name="delete-cookies"></a>删除 Cookie  

选择一个 Cookie 然后选择“**删除选中项** (![删除选中项](../media/delete-icon.msft.png)\)” 来删除某个 Cookie。  

:::image type="complex" source="../media/storage-application-storage-cookies-delete-selected.msft.png" alt-text="删除特定 Cookie" lightbox="../media/storage-application-storage-cookies-delete-selected.msft.png":::
   图 5：删除特定 Cookie  
:::image-end:::  

选择“**清除所有** (![清除所有](../media/clear-icon.msft.png)\)” 来删除所有 Cookie。  

:::image type="complex" source="../media/storage-application-storage-cookies-clear-all.msft.png" alt-text="清除所有 Cookie" lightbox="../media/storage-application-storage-cookies-clear-all.msft.png":::
   图 6：清除所有 Cookie  
:::image-end:::  

## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[MicrosoftEdgeDevTools]: /microsoft-edge/devtools-guide-chromium "Microsoft Edge (Chromium) 开发人员工具"  
[DevToolsOpen]: /microsoft-edge/devtools-guide-chromium/open "打开 Microsoft Edge DevTools"  

[ChromiumIssue232693]: https://bugs.chromium.org/p/chromium/issues/detail?id=232693 "Chromium 问题 232693：实现 Cookie 优先字段 | Chromium Bug"  

[MDNHTTPCookies]: https://developer.mozilla.org/docs/Web/HTTP/Cookies "HTTP cookie | MDN"  
[MDNHTTPCookiesPermanent]: https://developer.mozilla.org/docs/Web/HTTP/Cookies#Permanent_cookies "HTTP Cookie - 永久 cookie | MDN"  
[MDNHTTPCookiesSamesite]: https://developer.mozilla.org/docs/Web/HTTP/Cookies#SameSite_cookies "HTTP Cookie - SameSite cookie | MDN"  
[MDNHTTPCookiesScope]: https://developer.mozilla.org/docs/Web/HTTP/Cookies#Scope_of_cookies "HTTP Cookie - Cookie | MDN"  
[MDNHTTPCookiesSecure]: https://developer.mozilla.org/docs/Web/HTTP/Cookies#Secure_and_HttpOnly_cookies "HTTP Cookie - 安全和 HttpOnly Cookie | MDN"  
[MDNHTTPCookiesSession]: https://developer.mozilla.org/docs/Web/HTTP/Cookies#Session_cookies "HTTP Cookie - 会话 cookie | MDN"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/cookies)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques  
