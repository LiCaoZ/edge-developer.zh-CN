---
description: 了解如何使用 Microsoft Edge DevTools 的网络面板检测网络问题。
title: 网络问题指南
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge，web 开发，f12 工具，devtools
ms.openlocfilehash: 5650be5a5cb8b997140eeaa5d1521993c380b15c
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141381"
---
<!-- Copyright Kayce Basques and Jonathan Garbee

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="network-issues-guide"></a>网络问题指南

本指南将演示如何使用 Microsoft Edge DevTools 的网络面板检测网络问题或优化机会。

若要了解**网络**工具的基础知识，请导航到[入门][NetworkPerformance]。


<!-- ====================================================================== -->
## <a name="queued-or-stalled-requests"></a>请求排队或暂停

**症状**

六个请求正在同时下载。  之后，一系列的请求处于排队或暂停状态。  一旦前六个请求中完成一个，队列中的一个请求开始下载。

在下图的**瀑布图**中，`edge-iconx1024.msft.png` 资产的前六个请求同时开始。  后续请求将保持暂停，直到原来的六个请求中的一个完成。

:::image type="complex" source="../media/network-network-disabled-cache-resources-queue.msft.png" alt-text="网络面板中排队或暂停系列的示例" lightbox="../media/network-network-disabled-cache-resources-queue.msft.png":::
   **Network** 工具中排队或暂停系列的示例
:::image-end:::

**原因**

对单个域提出的请求过多。  在 HTTP/1.0 或 HTTP/1.1 连接上，Microsoft Edge 允许每个主机最多同步六个 TCP 连接。

**修补程序**

*   如果必须使用 HTTP/1.0 或 HTTP/1.1，则实施域分片。
*   使用 HTTP/2。  不要将域分片用于 HTTP/2。
*   删除或延迟不必要的请求，以便提前下载关键请求。


<!-- ====================================================================== -->
## <a name="slow-time-to-first-byte-ttfb"></a>第一字节时间 (TTFB) 缓慢

**症状**

请求等待接收服务器的第一个字节的时间过长。

下图中，**瀑布图**中的绿色条形图表示请求等待了很长时间。  这是使用限制网速并添加延迟的配置文件进行的模拟。

:::image type="complex" source="../media/network-network-resources-using-dial-up-profile.msft.png" alt-text="第一字节时间缓慢的请求示例" lightbox="../media/network-network-resources-using-dial-up-profile.msft.png":::
   第一字节时间缓慢的请求示例
:::image-end:::

**原因**

*   客户端和服务器之间的连接速度很慢。
*   服务器响应缓慢。  在本地托管服务器，以确定是连接速度慢还是服务器速度慢。  如果您在访问本地服务器时仍 (到第一字节) TTFB，则服务器速度很慢。

**修补程序**

*   如果连接速度缓慢，请考虑在 CDN 上托管内容或更改托管提供者。
*   如果服务器运行缓慢，请考虑优化数据库查询，同时实现缓存或修改服务器配置。


<!-- ====================================================================== -->
## <a name="slow-content-download"></a>内容下载缓慢

**症状**

下载请求需要很长时间。

下图中，png 旁**瀑布图**的蓝色条形图表示下载花费了很长时间。

:::image type="complex" source="../media/network-network-resources-edge-devtools.msft.png" alt-text="下载耗时较长的请求示例" lightbox="../media/network-network-resources-edge-devtools.msft.png":::
   下载耗时较长的请求示例
:::image-end:::

**原因**

*   客户端和服务器之间的连接速度很慢。
*   正在下载大量内容。

**修补程序**

*   请考虑在 CDN 上托管内容或更改托管提供者。
*   通过优化请求发送更少的字节。

<!-- ## Contribute knowledge  / Getting in touch

Do you have a network issue that should be added to this guide?

*   Send a tweet to [@EdgeDevTools][MicrosoftEdgeTweet].
*   Choose **Send Feedback** (![Send Feedback](../media/smile-icon.msft.png)) in the DevTools or select `Alt`+`Shift`+`I` (Windows, Linux) or `Option`+`Shift`+`I` (macOS) to provide feedback or feature requests.
*   [Open an issue][WebFundamentalsIssue] on the docs repo.  -->


<!-- ====================================================================== -->
<!-- links -->
[NetworkPerformance]: ./index.md "使用 Microsoft Edge DevTools 检测网络活动 | Microsoft Docs"

[MicrosoftEdgeTweet]: https://twitter.com/intent/tweet?text=@EdgeDevTools%20[Network%20Issues%20Guide%20Suggestion]

[WebFundamentalsIssue]: https://github.com/MicrosoftDocs/edge-developer/issues/new?title=%5BDevTools%20Network%20Issues%20Guide%20Suggestion%5D "新问题 - MicrosoftDocs/edge-developer"


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于此处，[](https://developers.google.com/web/tools/chrome-devtools/network/issues)由 (技术撰稿人[、Chrome][KayceBasques] DevTools \& Lighthouse) 和[House Garbee][JonathanGarbee] (Google Developer Expert for Web Technology) 创作。

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
[JonathanGarbee]: https://developers.google.com/web/resources/contributors#jonathan-garbee
