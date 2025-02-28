---
title: 查看、编辑和删除 Cookie
description: 在 Microsoft Edge DevTools 中，使用应用程序工具的 Cookie 窗格查看、编辑和删除网页的 HTTP Cookie。  HTTP Cookie 用于管理用户会话、存储用户个性化首选项和跟踪用户行为。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/09/2022
ms.openlocfilehash: 5f84ce0e45537853f3a30b944603c8388624e122
ms.sourcegitcommit: b04ee1e1cf86cb9ad732bc242a8cd23a9112c31f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2022
ms.locfileid: "12752652"
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

_HTTP Cookie_ 主要用于管理用户会话、存储用户个性化首选项和跟踪用户行为。  使用**应用程序**工具的 **Cookie** 窗格查看、编辑和删除网页的 HTTP cookie。

请参阅[使用 HTTP Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies)。


<!-- ====================================================================== -->
## <a name="open-the-cookies-pane"></a>打开“Cookie”窗格

1. 在要编辑的网页上打开 DevTools。  例如，右键单击页面，然后选择 **“检查**”或“按下 `F12`”。  有关其他方法，请参阅 [Open DevTools](/microsoft-edge/devtools-guide-chromium/open)。

2. 单击“ **应用程序** ”选项卡打开“ **应用程序** ”工具。 **Manifest**窗格随即打开：

   ![清单窗格](cookies-images/pick-application-no-manifest.png)

3. 在“**存储**“下，展开 “**Cookie**”，然后选择一个源:

   ![“Cookie”窗格](cookies-images/open-cookies-select-source.png)

<!-- ====================================================================== -->
## <a name="fields"></a>字段

**Cookies** 表包含以下字段:

*  **名称**。  Cookie 的名称。

*  **值**。  Cookie 的值。

*  **域**。  允许接收 Cookie 的主机。  请参阅[Cookie 的作用域](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Scope_of_cookies)。

*  **路径**。  URL 必须存在于请求的 URL 中以发送 `Cookie` 标头。  请参阅[Cookie 的作用域](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Scope_of_cookies)。

*  **到期日期/最长期限**.  Cookie 的到期日期或最长期限。  请参阅“[永久 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Permanent_cookies)。  对于[会话 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Session_cookies)，此值始终为 `Session`。

*  **大小**。  Cookie 的大小（以字节为单位）。

*  **HttpOnly**。  如果 `true`此字段指示 Cookie 仅应通过 HTTP 使用，并且不允许使用 JavaScript 修改。  请参阅 [HttpOnly Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Secure_and_HttpOnly_cookies)。

*  **安全**。  如果 `true`，此字段指示 Cookie 必须仅通过安全的 HTTPS 连接发送到服务器。  请参阅[安全 Cookie](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Secure_and_HttpOnly_cookies)。

*  **SameSite**。  包含 `strict`，当 Cookie 使用实验性 [Samesite](https://developer.mozilla.org/docs/Web/HTTP/Cookies#SameSite_cookies) 属性时包含 `lax`。

*  **SameParty**。 此属性为 Web 开发人员提供了一种对允许在同一方跨站点上下文中设置或发送的 Cookie 进行批注的方法。 

*  **分区键**。 _分区键_是文档中的属性或路径，可用于在文档中分发数据，但将数据存储在一起。 分布在文档中且具有相同分区键值的多个数据片段在逻辑上分组在一起并存储在同一物理分区中。

*  **优先级**。  包含 `low`、 `medium` (默认) 或 `high` Cookie 是否使用已弃用的 [Cookie Priority](https://bugs.chromium.org/p/chromium/issues/detail?id=232693) 属性。


<!-- ====================================================================== -->
## <a name="filter-cookies"></a>筛选 Cookie

使用“**筛选器**”文本框按**名称**或**值**筛选 Cookie:

![筛选出不包含文本 ID 的任何 Cookie](cookies-images/filter-cookies-name.png)

**注意：** 不支持按其他字段进行筛选。

<!-- ====================================================================== -->
## <a name="edit-a-cookie"></a>编辑 Cookie

**名称**、**值**、**域**、**路径**和**过期日期/最长期限**字段是可编辑的。  双击字段进行编辑：

![将 Cookie 的名称设置为"DEVTOOLS！"](cookies-images/rename-cookie.png)

<!-- ====================================================================== -->
## <a name="delete-cookies"></a>删除 Cookie

若要删除特定 Cookie，请单击 Cookie，然后单击“ **删除选定** (![删除所选](cookies-images/delete-cookie-icon.png)) ：

![正在删除特定 Cookie。](cookies-images/delete-selected-cookie.png)

若要删除所有 Cookie，请单击 **“清除所有 Cookie** (![清除所有 Cookie 图标](cookies-images/clear-all-cookies-icon.png)) ：

![清除所有 Cookie](cookies-images/clear-all-cookies.png)



<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/storage/cookies/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
