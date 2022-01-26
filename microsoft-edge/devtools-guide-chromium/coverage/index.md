---
title: 使用"覆盖"面板查找未使用的 JavaScript 和 CSS 代码
description: 如何在 Microsoft Edge DevTools 中查找和分析未使用的 JavaScript 和 CSS 代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: fffe3771dd7677be6ce6b8de7e5066a268515998
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12324347"
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
# <a name="find-unused-javascript-and-css-code-with-the-coverage-panel"></a>使用"覆盖"面板查找未使用的 JavaScript 和 CSS 代码

Microsoft Edge DevTools 中的“**覆盖范围**”面板可帮助你查找未使用的 JavaScript 和 CSS 代码。  删除未使用的代码可能会加快页面加载速度并保存移动用户的手机网络数据。

:::image type="complex" source="../media/coverage-sources-resource-drawer-coverage.msft.png" alt-text="分析代码范围。" lightbox="../media/coverage-sources-resource-drawer-coverage.msft.png":::
   正在分析代码覆盖范围
:::image-end:::

> [!WARNING]
> 查找未使用的代码相对容易。  但重构代码库以便每个页面仅提供所需的 JavaScript 和 CSS 可能非常困难。  本指南未涵盖如何重构基本代码以避免未使用的代码，因为这些重构高度依赖于你的技术堆叠。


<!-- ====================================================================== -->
## <a name="overview"></a>概述

寄送未使用的 JavaScript 或 CSS 是 web 开发中的一个常见问题。  例如，假设你想要在页面上使用“[Bootstrap 按钮组件](https://getbootstrap.com/docs/4.3/components/buttons)”。  若要使用按钮组件，你需要在 HTML 中添加指向 Bootstrap 样式表的链接，如下所示：

```html
...
<head>
    ...
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    ...
</head>
...
```

此样式表不仅包括按钮组件的代码。  它包含**所有**Bootstrap 组件的 CSS。  但是，你未使用任何其他 Bootstrap 组件。  因此，你的页面正在下载一组不需要的 CSS。  由于以下原因，此额外的 CSS 是一个问题。

*   额外的代码会降低页面加载速度。  <!--Navigate to [Render-Blocking CSS](/web/fundamentals/performance/critical-rendering-path/render-blocking-css).  -->
*   如果用户在移动设备上访问页面，则额外的代码会使用其手机网络数据。


<!-- ====================================================================== -->
## <a name="open-the-coverage-panel"></a>打开“覆盖范围”面板

1.  [打开“命令”菜单](../command-menu/index.md)。
1.  开始键入`coverage`，选择“**显示覆盖范围**”命令，然后选择`Enter`以运行该命令。  在“**工具箱**”中打开“**覆盖范围**”面板。

    :::image type="complex" source="../media/coverage-console-drawer-coverage-empty.msft.png" alt-text="覆盖面板。" lightbox="../media/coverage-console-drawer-coverage-empty.msft.png":::
       “**覆盖范围**”面板
    :::image-end:::


<!-- ====================================================================== -->
## <a name="record-code-coverage"></a>记录代码覆盖范围

1.  在“**覆盖范围**”面板中选择以下按钮之一。
    *   Choose **Start Instrumenting Coverage and Reload Page** (Start ![ Instrumenting Coverage and Reload Page. ](../media/reload-icon.msft.png)) if you want to review what code needed to load the page.
    *   Choose **Instrument Coverage** (Instrument ![ Coverage.) if you want to review ](../media/record-icon.msft.png) what code is used after interacting with the page.
1.  选择 **停止检测覆盖和** 显示结果 (停止检测覆盖和显示结果。) 停止记录代码 ![ ](../media/stop-icon.msft.png) 覆盖范围时显示。


<!-- ====================================================================== -->
## <a name="analyze-code-coverage"></a>分析代码覆盖范围

“**覆盖范围**”面板中的表显示已分析的资源，以及每个资源中使用的代码数。  选择一行以在"源"工具**** 中打开该资源，并查看已用代码和未使用代码的行细分。

:::image type="complex" source="../media/coverage-sources-resource-drawer-coverage-selected.msft.png" alt-text="代码覆盖报告。" lightbox="../media/coverage-sources-resource-drawer-coverage-selected.msft.png":::
   代码覆盖范围报告
:::image-end:::

*   “**URL**”列是已分析资源的 URL。
*   “**类型**”列显示资源是否包含 CSS、JavaScript 还是同时包含两者。
*   “**字节总数**”列是资源的总大小（以字节为单位）。
*   “**未使用字节数**”列是没有使用的字节数。
*   最后一个未命名列是“**总字节数**”和“**未使用字节数**”列的可视化效果。  条形图的红色部分是未使用字节数。  绿色部分是已使用字节数。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/coverage/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![Creative Commons License。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
