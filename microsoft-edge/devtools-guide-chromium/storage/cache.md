---
description: 如何从 Microsoft Edge DevTools 的应用程序面板查看缓存数据。
title: 使用 Microsoft Edge DevTools 查看缓存数据
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: bcd94f18e03ca042e9499c817c0effa8a14a927d
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12155505"
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
# <a name="view-cache-data-with-microsoft-edge-devtools"></a>使用 Microsoft Edge DevTools 查看缓存数据

本指南将演示如何使用 [Microsoft Edge DevTools](../../devtools-guide-chromium/index.md) 检查[缓存](https://developer.mozilla.org/docs/Web/API/Cache)数据。

如果要尝试检查 http [缓存](https://developer.mozilla.org/docs/Web/HTTP/Caching) 数据，则这不是你想要的指南。  在"网络日志"字段的 **大小** 列中 **信息**。  导航到 [记录网络](../network/index.md#log-network-activity)。


<!-- ====================================================================== -->
## <a name="view-cache-data"></a>查看缓存数据

1.  选择**应用程序**选项卡打开**应用程序**工具。  通常默认**清单**窗格打开。

    :::image type="complex" source="../media/storage-application-manifest.msft.png" alt-text="清单窗格" lightbox="../media/storage-application-manifest.msft.png":::
       **清单**窗格
    :::image-end:::

1.  展开 **缓存存储** 部分以查看可用的缓存。

    :::image type="complex" source="../media/storage-application-cache-storage.msft.png" alt-text="可用缓存" lightbox="../media/storage-application-cache-storage.msft.png":::
       可用缓存
    :::image-end:::

1.  选择缓存以查看内容。

    :::image type="complex" source="../media/storage-application-cache-storage-domain-root-headers.msft.png" alt-text="查看缓存的内容" lightbox="../media/storage-application-cache-storage-domain-root-headers.msft.png":::
       查看缓存的内容
    :::image-end:::

1.  选择资源以查看表下部分中的 HTTP 标题。

    :::image type="complex" source="../media/storage-application-cache-storage-index-headers.msft.png" alt-text="查看资源的 HTTP 标题" lightbox="../media/storage-application-cache-storage-index-headers.msft.png":::
       查看资源的 HTTP 标题
    :::image-end:::

1.  选择 **预览** 以查看资源的内容。

    :::image type="complex" source="../media/storage-application-cache-storage-domain-js-preview.msft.png" alt-text="查看资源的内容" lightbox="../media/storage-application-cache-storage-domain-js-preview.msft.png":::
       查看资源的内容
    :::image-end:::


<!-- ====================================================================== -->
## <a name="refresh-a-resource"></a>刷新资源

1.  [查看缓存](#view-cache-data)。
1.  选择要刷新的资源。  DevTools 会突出显示它以表明已选中。

    :::image type="complex" source="../media/storage-application-cache-storage-domain-refresh.msft.png" alt-text="选择要刷新的资源" lightbox="../media/storage-application-cache-storage-domain-refresh.msft.png":::
       选择要刷新的资源
    :::image-end:::

1.  选择 **"刷新** (![ 刷新 ](../media/refresh-icon.msft.png)) 。


<!-- ====================================================================== -->
## <a name="filter-resources"></a>筛选资源

1.  [查看缓存](#view-cache-data)。
1.  使用 **路径筛选"** 文本框来筛选与提供的路径不匹配的资源。

    :::image type="complex" source="../media/storage-application-cache-storage-filter.msft.png" alt-text="筛选与指定路径不匹配的资源" lightbox="../media/storage-application-cache-storage-filter.msft.png":::
       筛选与指定路径不匹配的资源
    :::image-end:::


<!-- ====================================================================== -->
## <a name="delete-a-resource"></a>删除资源

1.  [查看缓存](#view-cache-data)。
1.  选择要删除的资源。  DevTools 会突出显示它以表明已选中。

    :::image type="complex" source="../media/storage-application-cache-storage-delete-selected.msft.png" alt-text="选择要删除的资源" lightbox="../media/storage-application-cache-storage-delete-selected.msft.png":::
       选择要删除的资源
    :::image-end:::

1.  Choose **Delete Selected (** Delete selected ![ ](../media/delete-icon.msft.png)) .


<!-- ====================================================================== -->
## <a name="delete-all-cache-data"></a>删除所有缓存数据

1.  打开**应用程序** > **存储空间**。
1.  确保已启用" **缓存存储** 复选框。

    :::image type="complex" source="../media/storage-application-clear-storage-cache-storage-checkbox.msft.png" alt-text="缓存存储复选框" lightbox="../media/storage-application-clear-storage-cache-storage-checkbox.msft.png":::
       **缓存存储** 复选框
    :::image-end:::

1.  选择**清除网站数据**。

    :::image type="complex" source="../media/storage-application-clear-storage-cache-storage-checkbox-clear-site-data-button.msft.png" alt-text="清除网站数据按钮" lightbox="../media/storage-application-clear-storage-cache-storage-checkbox-clear-site-data-button.msft.png":::
       **清除网站数据**按钮
    :::image-end:::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/cache)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors#kayce-basques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
