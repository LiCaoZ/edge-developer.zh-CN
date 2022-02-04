---
title: 使用覆盖工具查找未使用的 JavaScript 和 CSS 代码
description: 如何在 Microsoft Edge DevTools 中查找和分析未使用的 JavaScript 和 CSS 代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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
# <a name="find-unused-javascript-and-css-code-with-the-coverage-tool"></a>使用覆盖工具查找未使用的 JavaScript 和 CSS 代码

覆盖工具可以帮助你找到未使用的 JavaScript 和 CSS 代码。  删除未使用的代码可以加快页面加载速度并保存移动用户的手机网络数据。

:::image type="content" source="../media/coverage-sources-resource-drawer-coverage.msft.png" alt-text="分析代码范围。" lightbox="../media/coverage-sources-resource-drawer-coverage.msft.png":::

查找未使用的代码相对容易。  但重构代码库以便每个页面仅提供所需的 JavaScript 和 CSS 可能非常困难。  本指南未涵盖如何重构基本代码以避免未使用的代码，因为此重构取决于您的技术堆栈。


<!-- ====================================================================== -->
## <a name="overview"></a>概述

寄送未使用的 JavaScript 或 CSS 是 web 开发中的一个常见问题。  例如，假设你想要使用页面上 [的 Bootstrap](https://getbootstrap.com/docs/4.3/components/buttons) 按钮组件。  若要使用按钮组件，你需要在 HTML 中添加指向 Bootstrap 样式表的链接，如下所示：

```html
<head>
    ...
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    ...
</head>
```

此样式表并不只是包含按钮组件的代码。  它包含_所有_Bootstrap 组件的 CSS。  但是，你未使用任何其他 Bootstrap 组件。  因此，你的页面正在下载一组不需要的 CSS。

此额外的 CSS 是一个问题，原因如下：

*  额外的代码会降低页面加载速度。  <!-- See [Render-Blocking CSS](/web/fundamentals/performance/critical-rendering-path/render-blocking-css). -->

*  如果用户在移动设备上访问页面，则额外的代码会使用其手机网络数据。


<!-- ====================================================================== -->
## <a name="open-the-coverage-tool"></a>打开"覆盖"工具

1. [打开“命令”菜单](../command-menu/index.md)。

1. 开始键入 ， `coverage`选择显示 **覆盖命令** ，然后按 `Enter`。  " **覆盖** "工具将在"箱" **中打开**。

   :::image type="content" source="../media/coverage-console-drawer-coverage-empty.msft.png" alt-text="覆盖工具。" lightbox="../media/coverage-console-drawer-coverage-empty.msft.png":::


<!-- ====================================================================== -->
## <a name="record-code-coverage"></a>记录代码覆盖范围

1. 单击"覆盖"工具中的以下 **按钮之** 一：

   *  单击**开始检测覆盖范围和重新加载页面 (**![检测覆盖范围和重新加载页面。) ](../media/reload-icon.msft.png)<!--todo: check UI string--> 如果您想要查看加载页面所需的代码。

   *  如果要**在** (![](../media/record-icon.msft.png) 页面) 使用哪些代码，请单击检测覆盖范围和检测覆盖。

1. 单击**停止检测覆盖，然后 (**![检测范围和](../media/stop-icon.msft.png)显示结果) <!--todo: check UI string--> 当你希望停止记录代码覆盖范围时。


<!-- ====================================================================== -->
## <a name="analyze-code-coverage"></a>分析代码覆盖范围

覆盖工具 **中的** 表显示已分析的资源，以及每个资源中使用的代码数。  单击一行以在"源"工具**** 中打开该资源，并显示已用代码和未使用代码的行细分。

代码覆盖报告：

:::image type="content" source="../media/coverage-sources-resource-drawer-coverage-selected.msft.png" alt-text="代码覆盖报告。" lightbox="../media/coverage-sources-resource-drawer-coverage-selected.msft.png":::

代码覆盖率报告中的列：

| 列 | 描述 |
| --- | --- |
| **URL** | 已分析资源的 URL。 |
| **类型** | 资源是否包含 CSS、JavaScript 或两者。 |
| **总字节数** | 资源的总大小（以字节为单位）。 |
| **未使用的字节数** | 未使用的字节数。 |
| 最后一个未命名列 | 总字节数 **和** 未使用 **字节数列的** 可视化。  条形图的红色部分是未使用字节数。  绿色部分是已使用字节数。 |


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/coverage/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
