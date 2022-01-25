---
title: 使用 Lighthouse 测试辅助功能
description: 在 DevTools 内使用 Lighthouse 测试辅助功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: cd8640060a450d7b4fdd88a3d3b6154ca9deaee3
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318182"
---
<!-- this article was created on 05/11/2021 by moving a section out from the "Accessibility reference" article (reference.md) -->
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
# <a name="test-accessibility-using-lighthouse"></a>使用 Lighthouse 测试辅助功能

可以在 DevTools 内使用 Lighthouse 审核页面的辅助功能并生成报告。 可以使用 Lighthouse 工具确定：

*   是否已为屏幕阅读器正确标记页面。
*   页面上的文本元素是否具有足够的对比率（使用颜色选取器）。 有关详细信息，请导航到使用颜色选取器 [测试文本颜色对比度](color-picker.md)。

> [!NOTE]
> **Lighthouse**工具提供指向第三方网站上承载的内容的链接。  Microsoft 不负责也不控制这些网站的内容，并且可能会收集任何数据。

若要使用 Lighthouse 工具审核页面，请执行以下步骤。

1.  导航到要审核的 URL。
1.  在 DevTools 中，选择 **"Lighthouse"** 工具。  将显示配置选项。

    :::image type="complex" source="../media/accessibility-lighthouse.msft.png" alt-text="浅色配置选项" lightbox="../media/accessibility-lighthouse.msft.png":::
       浅色配置选项
    :::image-end:::

1.  对于 **"** 设备 **"，** 如果要模拟移动设备，请选择"移动"。  此选项将更改用户代理字符串并调整视口的大小。  此选项可能会影响审核结果。
1.  在"**类别"** 部分，选择 **"辅助功能"。**
1.  选择 **"生成报告"。** 10 到 30 秒后，DevTools 将显示一个报告。  该报告提供了有关如何提高页面辅助功能的提示。

    :::image type="complex" source="../media/accessibility-lighthouse-result.msft.png" alt-text="辅助功能类别的 Lighthouse 报告" lightbox="../media/accessibility-lighthouse-result.msft.png":::
       辅助功能类别的 Lighthouse**报告**
    :::image-end:::

1.  选择报告中的某个项目以了解有关它的详细信息。

    :::image type="complex" source="../media/accessibility-lighthouse-result-issue-expanded.msft.png" alt-text="Lighthouse 报告中的扩展问题" lightbox="../media/accessibility-lighthouse-result-issue-expanded.msft.png":::
       Lighthouse 报告中的扩展问题
    :::image-end:::

1.  选择 **"了解更多** "链接以查看问题的文档。

    :::image type="complex" source="../media/accessibility-web-dev-accessibility-audits-learn-more.msft.png" alt-text="查看问题的文档" lightbox="../media/accessibility-web-dev-accessibility-audits-learn-more.msft.png":::
       查看问题的文档
    :::image-end:::

1.  若要返回到配置选项，请在 DevTools 中选择"**** 执行审核 `+` () 。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors/kaycebasques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
