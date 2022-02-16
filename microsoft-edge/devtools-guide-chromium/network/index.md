---
title: 检查网络活动
description: 有关 Microsoft Edge DevTools 中最受欢迎的网络相关功能的教程。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 0cf133975ca2c480281603d466e9c0f3e5da4e1a
ms.sourcegitcommit: f1676f5c435e7272af5b552190e4641c771351b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2022
ms.locfileid: "12350627"
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
   limitations under the License. -->
# <a name="inspect-network-activity"></a>检查网络活动

这是网络工具的分步教程演练，用于检查页面的网络活动。****

有关与网络相关的 DevTools 功能的概述，请参阅 [网络功能参考](./reference.md)。

<!-- TODO: entire section needs a Microsoft Edge DevTools rewrite  -->

<!-- Read on, or watch the video version of this tutorial: [!VIDEO embed/e1gAyQuIFQo] -->


<!-- ====================================================================== -->
## <a name="when-to-use-the-network-panel"></a>何时使用网络面板

一般情况下，当您需要确保资源正在下载或上传时，请使用网络面板。  网络面板的最常见 **用例** 包括：

*  确保资源上载或下载实际正在进行。

*  检查单个资源的属性，如 HTTP 标头、内容、大小等。

如果要寻找提高页面加载性能的方法，请不要从网络 **工具开始** 。  有许多类型的负载性能问题与网络活动不相关。  从 **Lighthouse** 工具开始，因为它为你提供了如何改进页面的目标建议。  请参阅 [使用 Lighthouse 优化网站速度](../speed/get-started.md)。


<!-- ====================================================================== -->
## <a name="open-the-network-panel"></a>打开网络面板

若要了解本教程的最多内容，请打开演示并试用演示页面上的功能。

1. 打开新 [选项卡或窗口中的](https://microsoftedge.github.io/Demos/network-tutorial/) 检查网络活动演示。

   :::image type="content" source="../media/network-glitch-inspect-network-activity-demo.msft.png" alt-text="演示。" lightbox="../media/network-glitch-inspect-network-activity-demo.msft.png":::

   <!-- You can view the source files for this demo in the [MicrosoftEdge/Demos > devtools-css-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/network-tutorial) repo folder. -->

   <!--
   :::image type="content" source="../media/network-tutorial/windows.msft.png" alt-text="The demo in one window and this tutorial in a different window." lightbox="../media/network-tutorial/windows.msft.png":::
   -->

1. 若要[打开 DevTools](../open/index.md)，请按 `Control`++`Shift``J` (Windows、Linux) 或`J` `Command`+`Option`+ (macOS) 。  将 **打开控制台** 工具。

   :::image type="content" source="../media/network-glitch-console.msft.png" alt-text="控制台。" lightbox="../media/network-glitch-console.msft.png":::

   你可能希望 [将 DevTools 停靠到窗口底部](../customize/placement.md)：

   :::image type="content" source="../media/network-glitch-console-bottom.msft.png" alt-text="DevTools 固定到窗口底部。" lightbox="../media/network-glitch-console-bottom.msft.png":::

1. 打开 **"网络"** 工具。

:::image type="content" source="../media/network-glitch-network-bottom.msft.png" alt-text="DevTools 中的网络工具，DevTools 固定在窗口底部。" lightbox="../media/network-glitch-network-bottom.msft.png":::

现在， **网络** 工具为空。  DevTools 仅在打开网络活动后记录网络活动，并且自打开 DevTools 后未发生任何网络活动。


<!-- ====================================================================== -->
## <a name="log-network-activity"></a>记录网络活动

查看页面导致的网络活动：

1. 刷新网页。  网络 **面板** 在网络日志中记录所有 **网络活动**。

   :::image type="content" source="../media/network-glitch-network.msft.png" alt-text="网络日志。" lightbox="../media/network-glitch-network.msft.png":::

   **网络日志**的每一行表示一个资源。  默认情况下，按时间顺序列出资源。  顶部资源通常是主 HTML 文档。  底部资源是最后请求的任何资源。

   每个列表示有关资源的信息。  在上图中，将显示默认列。

    *  **状态**。  响应的 HTTP 状态代码。

    *  **类型**。  资源类型。

    *  **发起程序**。  资源请求的原因。  单击"发起者"列中 **的链接** 将进入导致请求的源代码。

    *  **时间**。  请求的持续时间。

    *  **粘滞键**。  请求的不同阶段的图形表示形式。  若要显示细目，请将鼠标悬停在瀑布 **上**。

    > [!NOTE]
    > 网络日志**上方的图形****称为概述。**  本教程中不会使用 **"** 概述"图，因此可以隐藏它。  请参阅 [隐藏概述窗格](./reference.md#hide-the-overview-pane)。

   打开 DevTools 后，它会在网络日志中记录 **网络活动**。

1. 若要演示这一点，请首先查看**网络日志** 的底部，并记下上一次活动。

1. 现在，单击 **演示中的"获取** 数据"按钮。

1. 再次查看**网络日志** 的底部。  将显示名为 的新 `getstarted.json` 资源：

:::image type="content" source="../media/network-glitch-network-new-resource.msft.png" alt-text="网络日志中的新资源。" lightbox="../media/network-glitch-network-new-resource.msft.png":::


<!-- ====================================================================== -->
## <a name="show-more-information"></a>显示详细信息

网络日志的列是可配置的。  可以隐藏您未使用的列。  还有许多默认隐藏的列，你可能会发现这些列很有用。

1. 右键单击"网络日志"表的标题，然后选择"域 **"**。  现在将显示每个资源的域。

:::image type="content" source="../media/network-glitch-network-edit-column.msft.png" alt-text="启用&quot;域&quot;列。" lightbox="../media/network-glitch-network-edit-column.msft.png":::

1. To see the full URL of a resource， hover over its cell in the **Name** column.


<!-- ====================================================================== -->
## <a name="simulate-a-slower-network-connection"></a>模拟较慢的网络连接

用于构建站点的计算机的网络连接可能比用户的移动设备的网络连接速度快。  通过限制页面，可以更好地了解页面在移动设备上加载所花的时间。

1. 选择 **"限制"** 下拉列表，该列表默认设置为" **无** 限制"。

1. 选择 **慢速 3G。**

   :::image type="content" source="../media/network-glitch-network-throttling-slow-3g.msft.png" alt-text="选择&quot;慢速 3G&quot;。" lightbox="../media/network-glitch-network-throttling-slow-3g.msft.png":::

1. 长按 **"重新加载**![ (重新加载](../media/refresh-icon.msft.png)"。) 选择"空缓存"和"**硬重新加载"**。

:::image type="content" source="../media/network-glitch-empty-cache-and-hard-reset.msft.png" alt-text="空缓存和硬重新加载。" lightbox="../media/network-glitch-empty-cache-and-hard-reset.msft.png":::

在重复访问时，浏览器通常会从[缓存](https://developer.mozilla.org/docs/Web/HTTP/Caching)中提供一些文件，从而加快页面加载速度。  **空缓存和硬重新加载** 会强制浏览器访问所有资源的网络。  使用它来显示第一次访问者如何体验页面加载。

**空缓存和硬重新加载**工作流仅在 DevTools 打开时可用。


<!-- ====================================================================== -->
## <a name="capture-screenshots"></a>捕获屏幕截图

屏幕截图显示网页在加载时的外观。

1. 单击" (![网络设置](../media/settings-icon.msft.png) "。) "按钮，然后选中" **捕获屏幕截图"** 复选框。

   :::image type="content" source="../media/network-glitch-network-screenshots-setting.msft.png" alt-text="&quot;网络设置&quot;中的&quot;捕获屏幕截图&quot;复选框。" lightbox="../media/network-glitch-network-screenshots-setting.msft.png":::

1. 使用"空缓存"和"硬重新加载 **"工作流再次刷新** 页面。  如果需要有关操作方式的提醒，请参阅“[模拟较慢的连接](#simulate-a-slower-network-connection)”。

   **Screenshots** panel provides thumbnails of how the page looked at various points during the loading process：

   :::image type="content" source="../media/network-glitch-network-screenshots.msft.png" alt-text="页面加载的屏幕截图。" lightbox="../media/network-glitch-network-screenshots.msft.png":::

1. 单击第一个缩略图。  DevTools 显示当时发生的网络活动。

   :::image type="content" source="../media/network-glitch-network-screenshots-first.msft.png" alt-text="第一张屏幕截图期间发生的网络活动。" lightbox="../media/network-glitch-network-screenshots-first.msft.png":::

1. 单击 (![网络设置](../media/settings-icon.msft.png) "。) 并关闭"捕获屏幕截图 **"复选框以** 关闭 **"屏幕截图"** 窗格。

1. 再次刷新页面。


<!-- ====================================================================== -->
## <a name="inspect-the-details-of-the-resource"></a>检查资源的详细信息

选择资源以了解有关它详细信息。

1. 选择 `network-tutorial/`。  将显示 **"标题** "面板。  使用此面板检查 HTTP 标头。

   :::image type="content" source="../media/network-glitch-network-resources-headers.msft.png" alt-text="&quot;标题&quot;面板。" lightbox="../media/network-glitch-network-resources-headers.msft.png":::

1. 选择 **预览** 面板。  将显示 HTML 的基本呈现。

   :::image type="content" source="../media/network-glitch-network-resources-preview.msft.png" alt-text="预览面板。" lightbox="../media/network-glitch-network-resources-preview.msft.png":::

    当 API 以 HTML 格式返回错误代码时，面板非常有用。  你可能会发现，读取呈现的 HTML 比读取 HTML 源代码更容易，或者在检查图像时更容易读取呈现的 HTML。

1. 选择 **响应** 面板。  将显示 HTML 源代码。

   :::image type="content" source="../media/network-glitch-network-resources-response.msft.png" alt-text="响应面板。" lightbox="../media/network-glitch-network-resources-response.msft.png":::

    > [!TIP]
    > **** 缩小文件时![](../media/format-icon.msft.png)，选择"设置 (格式"。) 面板底部的"设置格式"按钮以重新设置文件内容的格式，实现**** 可读性。

1. 选择 **计时** 面板。  将显示资源的网络活动的细分。

   :::image type="content" source="../media/network-glitch-network-resources-timing.msft.png" alt-text="&quot;计时&quot;面板。" lightbox="../media/network-glitch-network-resources-timing.msft.png":::

1. 单击 **"** (![关闭](../media/close-icon.msft.png) "。) 再次查看网络日志。

   :::image type="content" source="../media/network-glitch-network-resources-close-tabs.msft.png" alt-text="&quot;关闭&quot;按钮。" lightbox="../media/network-glitch-network-resources-close-tabs.msft.png":::


<!-- ====================================================================== -->
## <a name="search-network-headers-and-responses"></a>搜索网络标头和响应

当您需要搜索特定字符串或正则表达式的所有资源的 HTTP 标头和响应时，请使用“**搜索**”窗格。

例如，假设你想要验证你的资源是否使用了合理的**缓存策略**。<!--[cache policies](../../../web/tools/lighthouse/audits/cache-policy) -->

<!--TODO: add cache policies section when available  -->

1. 选择 **"搜索**![ (搜索"。](../media/search-icon.msft.png)) 。  搜索窗格将打开到网络日志的左侧。

   :::image type="content" source="../media/network-glitch-network-search-empty.msft.png" alt-text="&quot;搜索&quot;窗格。" lightbox="../media/network-glitch-network-search-empty.msft.png":::

1. 键入 并 `no-cache` 按 `Enter`。  “搜索”窗格列出它在资源标头或内容 `no-cache` 中查找到的所有实例。

   :::image type="content" source="../media/network-glitch-network-search-cache-control.msft.png" alt-text="无缓存的搜索结果。" lightbox="../media/network-glitch-network-search-cache-control.msft.png":::

1. 单击结果以查看找到结果的资源。  如果要查看资源的详细信息，请选择直接转到它的结果。  例如，如果在标头中发现查询，则 **标题面板** 将打开。   如果在内容中发现查询，将打开 **"响应"** 面板。

   :::image type="content" source="../media/network-glitch-network-search-cache-control-headers-response-headers.msft.png" alt-text="&quot;标题&quot;面板中突出显示的搜索结果。" lightbox="../media/network-glitch-network-search-cache-control-headers-response-headers.msft.png":::

1. 关闭"搜索"窗格和 **"标题"** 面板。


<!-- ====================================================================== -->
## <a name="filter-resources"></a>筛选资源

DevTools 提供了许多工作流，用于筛选出与当前任务不相关的资源。

:::image type="content" source="../media/network-glitch-network-filter-empty.msft.png" alt-text="&quot;筛选器&quot;工具栏。" lightbox="../media/network-glitch-network-filter-empty.msft.png":::

默认情况下 **应** 打开"筛选器"工具栏。  If the **Filters** toolbar isn't on， click **Filter** (![Filter.](../media/filter-icon.msft.png)) to show it.

### <a name="filter-by-string-regular-expression-or-property"></a>按字符串、正则表达式或属性筛选

“**筛选器**”文本框支持许多不同类型的筛选。

1. 键入 `png` 到“**筛选器**”文本框。  只显示包含文本 `png` 的文件。  在这种情况下，与筛选器匹配的唯一文件是 PNG 图像。

   :::image type="content" source="../media/network-glitch-network-filter-png.msft.png" alt-text="字符串筛选器。" lightbox="../media/network-glitch-network-filter-png.msft.png":::

1. 键入 `/.*\.[cj]s+$/`。  DevTools 筛选出`j``c`文件名不以 或 结尾，后跟 1 个或多个字符的任何`s`资源。

   :::image type="content" source="../media/network-glitch-network-filter-regex.msft.png" alt-text="正则表达式筛选器。" lightbox="../media/network-glitch-network-filter-regex.msft.png":::

1. 键入 `-main.css`。  DevTools 筛选器出 `main.css`。  如果任何文件与模式匹配，则还会进行筛选。

   :::image type="content" source="../media/network-glitch-network-filter-negative-statement.msft.png" alt-text="负筛选器。" lightbox="../media/network-glitch-network-filter-negative-statement.msft.png":::

1. 键入 `larger-than:1000` 到“**筛选器**”文本框。  DevTools 筛选出响应小于 1000 字节的资源。

   :::image type="content" source="../media/network-glitch-network-filter-property-value.msft.png" alt-text="属性筛选器。" lightbox="../media/network-glitch-network-filter-property-value.msft.png":::

   有关可筛选属性的完整列表，请参阅 [按属性筛选请求](./reference.md#filter-requests-by-properties)。

1. 清除任何文本的“**筛选器**”文本框。

### <a name="filter-by-resource-type"></a>按资源类型筛选

若要专注于某些类型的文件，如样式表：

1. 选择 **CSS**。  所有其他文件类型都筛选掉。

   :::image type="content" source="../media/network-glitch-network-filter-file-type-css.msft.png" alt-text="只显示 CSS 文件。" lightbox="../media/network-glitch-network-filter-file-type-css.msft.png":::

1. 若要同时显示脚本，`Control`请长按 (Windows、Linux) 或 `Command` (macOS) ，然后单击 **JS**。

   :::image type="content" source="../media/network-glitch-network-filter-file-type-css-js.msft.png" alt-text="只显示 CSS 和 JS 文件。" lightbox="../media/network-glitch-network-filter-file-type-css-js.msft.png":::

1. 要删除筛选器并再次显示所有资源，请选择 **全部**。

有关其他筛选工作流，请参阅 [筛选请求](./reference.md#filter-requests)。


<!-- ====================================================================== -->
## <a name="block-requests"></a>阻止请求

当某些页面资源不可用时，页面的外观和行为如何？  它是完全失败，还是仍有点功能？  阻止查找请求：

1. 按 `Control``P``Shift`++ (Windows、Linux) 或 `Command``Shift`++`P` (macOS) 打开命令**菜单**。

1. 键入 ， `block`选择 **"显示请求阻止**"，然后按 `Enter`。

   :::image type="content" source="../media/network-glitch-network-cli-block.msft.png" alt-text="显示请求阻止。" lightbox="../media/network-glitch-network-cli-block.msft.png":::

1. 单击 **添加模式** (![添加模式。](../media/add-icon.msft.png)) 。

1. 键入 `main.css`。

   :::image type="content" source="../media/network-glitch-network-cli-block-add-pattern.msft.png" alt-text="阻止&quot;main.css&quot;。" lightbox="../media/network-glitch-network-cli-block-add-pattern.msft.png":::

1. 单击**添加**。

1. 刷新页面。  与预期一样，页面的样式会稍微混乱，因为主样式表已被阻止。

   在" `main.css` 网络日志"的行中，红色文本表示资源已被阻止。

   :::image type="content" source="../media/network-glitch-network-cli-block-main-css.msft.png" alt-text="main.css 已被阻止。" lightbox="../media/network-glitch-network-cli-block-main-css.msft.png":::

1. 清除" **启用请求阻止"** 复选框。


<!-- ====================================================================== -->
## <a name="conclusion"></a>总结

恭喜，你已完成本教程!  现在，你已了解如何使用 Microsoft Edge DevTools 中的 **网络** 工具。

若要发现更多与检查网络活动相关的 DevTools 功能，请参阅 [网络功能参考](./reference.md)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/network/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
