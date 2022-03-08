---
title: 使用安全工具了解安全问题
description: 如何使用 DevTools 中的安全面板确保页面受到 HTTPS 的完全保护。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: edafe99b7199bee3757be2dd52e2c589ce9dc0cf
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431926"
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
# <a name="understand-security-issues-using-the-security-tool"></a>使用安全工具了解安全问题

<!--Use the **Security** Panel in DevTools to make sure HTTPS is properly implemented on a page.  See **Why HTTPS Matters** to learn why every website should be protected with HTTPS, even sites that don't handle sensitive user data.  -->

<!--todo: add section when why-https is available -->

使用 **安全** 面板检查页面的安全性。

1. 若要打开 DevTools，请右键单击网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中的主工具栏上，单击"安全 **"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

   安全 **工具** (_或面板_) 打开：

:::image type="content" source="../media/security-security-overview-secure.msft.png" alt-text="安全面板。" lightbox="../media/security-security-overview-secure.msft.png":::


<!-- ====================================================================== -->
## <a name="common-problems"></a>常见问题

### <a name="non-secure-main-origins"></a>非安全主源

当页面的主源不安全时，安全概述显示**此页面不安全**。****

:::image type="content" source="../media/security-security-overview-non-secure.msft.png" alt-text="非安全页面。" lightbox="../media/security-security-overview-non-secure.msft.png":::

当您访问的 URL 通过 HTTP 请求时，会出现此问题。  若要确保安全，您需要通过 HTTPS 请求它。  例如，如果您查看地址栏中的 URL，它可能类似于 `http://example.com`。  若要确保 URL 安全，URL 应为 `https://example.com`。

如果已在服务器上设置 HTTPS，则解决此问题只需将服务器配置为将所有 HTTP 请求重定向到 HTTPS。

如果您尚未在服务器上设置 HTTPS， [Let's Encrypt](https://letsencrypt.org) 提供了一种免费且相对简单的启动过程的方法。  或者，你可以考虑将网站托管在CDN。  默认情况下，HTTPS 上的大多数主要 CDN 都承载网站。

> [!TIP]
> [Webhint](https://webhint.io) 中的"使用 [HTTPS](https://webhint.io/docs/user-guide/hints/hint-https-only)"提示可帮助自动执行确保所有 HTTP 请求都定向到 HTTPS 的过程。

### <a name="mixed-content"></a>混合内容

**混合内容**<!--[mixed content](/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content)--> 表示页面的主源是安全的，但页面从非安全源请求资源。  混合内容页仅部分受保护，因为探查器可以访问 HTTP 内容，并且易受中间人攻击。

:::image type="content" source="../media/security-security-overview-mixed-secure.msft.png" alt-text="混合内容。" lightbox="../media/security-security-overview-mixed-secure.msft.png":::

在上图中，选择"网络"面板中的"**查看 1** 请求"以打开 **"**`mixed-content:displayed`网络"工具并应用筛选器，以便"**网络**日志"只显示非安全资源。

:::image type="content" source="../media/security-network-filter.msft.png" alt-text="网络日志中的混合资源。" lightbox="../media/security-network-filter.msft.png":::


<!-- ====================================================================== -->
## <a name="view-details"></a>查看详细信息

### <a name="view-main-origin-certificate"></a>查看主源证书

从" **安全概述"** 中，单击 **"查看** 证书"以快速检查证书的主来源。

:::image type="content" source="../media/security-security-overview-secure-view-certificate.msft.png" alt-text="主源证书。" lightbox="../media/security-security-overview-secure-view-certificate.msft.png":::

### <a name="view-origin-details"></a>查看源详细信息

单击左侧导航中的某个条目以查看源的详细信息。  在详细信息页中，可以查看连接和证书信息。  证书透明度信息还会在可用时显示。

:::image type="content" source="../media/security-security-overview-mixed-secure-main-origin.msft.png" alt-text="主源详细信息。" lightbox="../media/security-security-overview-mixed-secure-main-origin.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/security/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
