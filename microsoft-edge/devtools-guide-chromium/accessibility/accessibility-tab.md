---
title: 使用"辅助功能"选项卡测试辅助功能
description: 使用"辅助功能"选项卡测试辅助功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 482b999fe225d05514640d142de9e06dda65c3cf
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318238"
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
# <a name="test-accessibility-using-the-accessibility-tab"></a>使用"辅助功能"选项卡测试辅助功能

" **辅助功能"** 选项卡是查看 DOM 节点的辅助功能树、ARIA 属性和计算辅助功能属性的地方。

若要打开 **"辅助功能"选项卡** ：

1.  选择" **元素"** 工具。
1.  在 **DOM 树**中，选择要检查的元素。
1.  选择 **"辅助功能"** 选项卡。 可能需要先选择"更多选项卡" ("更多选项卡"按钮) "样式"选项卡右边的**** ![ ](../media/more-tabs-icon.msft.png) "更多**选项卡"** 按钮。

:::image type="complex" source="../media/accessibility-elements-accessibility.msft.png" alt-text="检查&quot;辅助功能&quot;选项卡中的 DevTools 主页的 h1 元素" lightbox="../media/accessibility-elements-accessibility.msft.png":::
   检查 `h1` "辅助功能"选项卡中的 DevTools **主页** 元素
:::image-end:::


<!-- ====================================================================== -->
## <a name="view-the-position-of-an-element-in-the-accessibility-tree"></a>查看元素在辅助功能树中的位置

[辅助功能树](https://developer.mozilla.org/docs/Glossary/AOM)是 DOM 树的子集。  辅助功能树仅包含 DOM 树中的元素，这些元素对于通过屏幕阅读器等辅助技术显示页面内容非常有用。

从"辅助功能"选项卡检查元素在辅助功能 **树中** 的位置。

:::image type="complex" source="../media/accessibility-elements-accessibility-tree.msft.png" alt-text="辅助功能树部分" lightbox="../media/accessibility-elements-accessibility-tree.msft.png":::
   **辅助功能树**部分
:::image-end:::


<!-- ====================================================================== -->
## <a name="view-the-aria-attributes-of-an-element"></a>查看元素的 ARIA 属性

ARIA 属性确保辅助技术（如屏幕阅读器）具有为了正确表示页面内容而需要的所有信息。

在"辅助功能"选项卡中查看元素 **的** ARIA 属性。

:::image type="complex" source="../media/accessibility-elements-accessibility-aria-attributes.msft.png" alt-text="ARIA 属性部分" lightbox="../media/accessibility-elements-accessibility-aria-attributes.msft.png":::
   **ARIA 属性**部分
:::image-end:::


<!-- ====================================================================== -->
## <a name="view-the-computed-accessibility-properties-of-an-element"></a>查看元素的计算出的属性

部分辅助功能属性由浏览器动态计算。  这些属性显示在"辅助功能"选项卡**** 的"计算**属性"** 部分。

在"辅助功能"选项卡中查看元素的计算 **辅助功能** 属性。

> [!NOTE]
> 对于计算 CSS 属性，请使用" [计算"](../css/reference.md#view-only-the-css-that-is-actually-applied-to-an-element) 选项卡。

:::image type="complex" source="../media/accessibility-elements-accessibility-computed-properties.msft.png" alt-text="&quot;辅助功能&quot;选项卡的&quot;计算属性&quot;部分" lightbox="../media/accessibility-elements-accessibility-computed-properties.msft.png":::
   " **辅助功能"选项卡** 的" **计算属性"** 部分
:::image-end:::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors/kaycebasques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
