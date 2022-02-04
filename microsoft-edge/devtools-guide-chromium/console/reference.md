---
title: 控制台功能参考
description: 针对开发人员工具中控制台 UI 的每种功能Microsoft Edge全面参考。
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
# <a name="console-features-reference"></a>控制台功能参考

本文概述了控制台 **的功能**。

**内容：**

* [打开控制台](#open-the-console)
   * [打开控制台工具](#open-the-console-tool)
   * [打开工具箱中的控制台工具](#open-the-console-tool-in-the-drawer)
   * [打开控制台设置](#open-console-settings)
   * [打开控制台边栏](#open-the-console-sidebar)
* [查看消息](#view-messages)
   * [关闭邮件分组](#turn-off-message-grouping)
   * [记录 XHR 和 Fetch 请求](#log-xhr-and-fetch-requests)
   * [跨页面加载保留消息](#persist-messages-across-page-loads)
   * [隐藏网络消息](#hide-network-messages)
* [筛选邮件](#filter-messages)
   * [筛选出浏览器消息](#filter-out-browser-messages)
   * [按记录级别筛选](#filter-by-log-level)
   * [按 URL 筛选消息](#filter-messages-by-url)
   * [筛选出不同上下文的消息](#filter-out-messages-from-different-contexts)
   * [筛选出与正则表达式模式不匹配的邮件](#filter-out-messages-that-dont-match-a-regular-expression-pattern)
* [运行 JavaScript](#run-javascript)
   * [从历史记录重新运行表达式](#rerun-expressions-from-history)
   * [使用 Live Expressions 实时监视表达式的值](#watch-the-value-of-an-expression-in-real-time-with-live-expressions)
   * [关闭"期待评估"](#turn-off-eager-evaluation)
   * [从历史记录中关闭自动完成](#turn-off-autocomplete-from-history)
   * [选择 JavaScript 上下文](#select-javascript-context)
* [清除控制台](#clear-the-console)


<!-- ====================================================================== -->
## <a name="open-the-console"></a>打开控制台

可以将控制台 **作为** 工具 [在上窗格中打开，](#open-the-console-tool) 也可以作为工具在"箱 ["中打开](#open-the-console-tool-in-the-drawer)。


### <a name="open-the-console-tool"></a>打开控制台工具

按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。

:::image type="content" source="../media/console-hello-console.msft.png" alt-text="控制台工具。" lightbox="../media/console-hello-console.msft.png":::

若要从命令**菜单**打开控制台工具[](../command-menu/index.md)，请键入 `Console` ，然后运行旁边有******面板**锁屏提醒的显示控制台命令。

:::image type="content" source="../media/console-command-menu-show-console.msft.png" alt-text="运行命令以显示控制台工具。" lightbox="../media/console-command-menu-show-console.msft.png":::


### <a name="open-the-console-tool-in-the-drawer"></a>打开工具箱中的控制台工具

按 `Esc`。  或者，单击 **"自定义和控制 DevTools** (`...`) "，然后选择"显示控制台 **箱"**。

:::image type="content" source="../media/console-elements-customize-control-devtools-show-console-drawer.msft.png" alt-text="显示控制台箱。" lightbox="../media/console-elements-customize-control-devtools-show-console-drawer.msft.png":::

The Drawer pops up in the bottom of the DevTools window， with the **Console** tool open.

:::image type="content" source="../media/console-elements-console-drawer-hello-world.msft.png" alt-text="&quot;箱&quot;中的控制台工具。" lightbox="../media/console-elements-console-drawer-hello-world.msft.png":::

若要从命令**菜单中**打开控制台工具[](../command-menu/index.md)，请键入 `Console` ，然后运行旁边有****"箱"**锁屏提醒**的"显示控制台"命令。

:::image type="content" source="../media/console-command-menu-show-console.msft.png" alt-text="运行命令以在&quot;箱&quot;中显示 **Console** 工具。" lightbox="../media/console-command-menu-show-console.msft.png":::


### <a name="open-console-settings"></a>打开控制台设置

单击控制台**设置** (![控制台设置图标](../media/settings-button-icon.msft.png)。) 按钮。

:::image type="content" source="../media/console-settings-group-similar-empty.msft.png" alt-text="控制台设置。" lightbox="../media/console-settings-group-similar-empty.msft.png":::


### <a name="open-the-console-sidebar"></a>打开控制台边栏

若要显示边**栏，请单击**"显示**控制台边**![栏 (显示控制台边](../media/show-console-sidebar-icon.msft.png)栏。) 。  **边栏**可帮助你进行筛选。

:::image type="content" source="../media/console-sidebar-drawer-empty.msft.png" alt-text="控制台边栏。" lightbox="../media/console-sidebar-drawer-empty.msft.png":::


<!-- ====================================================================== -->
## <a name="view-messages"></a>查看消息

此部分包含更改消息在控制台中的显示方式的功能。  有关实际操作演练，请参阅查看 [邮件](index.md#inspect-and-filter-information-on-the-current-webpage)。


### <a name="turn-off-message-grouping"></a>关闭邮件分组

若要关闭控制台的默认邮件分组行为，请单击控制台 **设置** (![控制台 设置 图标****](../media/settings-button-icon.msft.png)。) 按钮，然后选中"类似组"旁边的**复选框。**  有关示例，请参阅 [Log XHR and Fetch requests](#log-xhr-and-fetch-requests)。


### <a name="log-xhr-and-fetch-requests"></a>记录 XHR 和 Fetch 请求

To log all `XMLHttpRequest` and `Fetch` requests to the **Console** as each happens， click the **Console 设置** (![Console 设置 icon.](../media/settings-button-icon.msft.png)) button and then select the checkbox next to **Log XMLHttpRequests**.

:::image type="content" source="../media/console-xhr-fetch.msft.png" alt-text="记录 XMLHttpRequest 和 Fetch 请求。" lightbox="../media/console-xhr-fetch.msft.png":::

上图中的顶部消息显示了**控制台**的默认分组行为。  <!--  In the following figure, the same log is displayed after you [turn off message grouping](#turn-off-message-grouping).  -->

<!--
> ##### Old Figure 9
> How the logged `XMLHttpRequest` and `Fetch` requests look after ungrouping
> :::image type="content" source="../media/console-xhr-fetch-all.msft.png" alt-text="How the logged XMLHttpRequest and Fetch requests look after ungrouping." lightbox="../media/console-xhr-fetch-all.msft.png":::
-->

<!--todo: add example for ungrouping console items  -->


### <a name="persist-messages-across-page-loads"></a>跨页面加载保留消息

加载新网页时，默认操作会清除 **控制台**。  若要在页面加载时**** 保留![消息，请单击"控制台设置 (控制台设置图标](../media/settings-button-icon.msft.png)。) 按钮，然后选中"保留日志"旁边的**复选框**。


### <a name="hide-network-messages"></a>隐藏网络消息

用户的默认操作Microsoft Edge将网络消息记录到**控制台**。  在下图中，选定的消息表示 `429` 的 HTTP 状态代码。

:::image type="content" source="../media/console-show-network.msft.png" alt-text="控制台中的&quot;429&quot;消息。" lightbox="../media/console-show-network.msft.png":::

隐藏网络消息：

1. 单击控制台**设置** (![控制台设置图标](../media/settings-button-icon.msft.png)。) 按钮。

1. 选中隐藏网络 **旁边的复选框**。


<!-- ====================================================================== -->
## <a name="filter-messages"></a>筛选邮件

有多种方法可以筛选出控制台中的 **邮件**。


### <a name="filter-out-browser-messages"></a>筛选出浏览器消息

若要仅显示来自网页的 JavaScript 的消息，请打开 [控制台边](#open-the-console-sidebar) 栏，然后单击 **" # 用户消息"**。

:::image type="content" source="../media/console-sidebar-drawer-user-messages.msft.png" alt-text="显示用户消息。" lightbox="../media/console-sidebar-drawer-user-messages.msft.png":::


### <a name="filter-by-log-level"></a>按记录级别筛选

DevTools 为每个方法分配 `console.*` 四个严重性级别之一：

*  `Error`
*  `Info`
*  `Verbose`
*  `Warning`

例如， `console.log()` 位于 组中 `Info` ，但 `console.error()` 位于 `Error` 组中。  控制台 [对象 API 参考](api.md) 介绍了每个适用方法的严重性级别。  浏览器记录到控制台的每条消息也具有严重性级别。

你可以隐藏你不感兴趣的任何级别的邮件。  例如，如果只对邮件感兴趣 `Error` ，可以隐藏其他三个组。

若要筛选消息，请单击"**日志级别**"下拉列表，然后选择、`Verbose``Info`、或 `Warning``Error`。

:::image type="content" source="../media/console-log-level-default-levels.msft.png" alt-text="&quot;日志级别&quot;下拉列表。" lightbox="../media/console-log-level-default-levels.msft.png":::

若要使用日志级别进行筛选，请[打开控制台边](#open-the-console-sidebar)栏，然后选择 **"错误**、警告****、**信息**"或"**详细"**。

:::image type="content" source="../media/console-sidebar-warnings.msft.png" alt-text="使用边栏查看警告。" lightbox="../media/console-sidebar-warnings.msft.png":::


### <a name="filter-messages-by-url"></a>按 URL 筛选消息

键入 `url:` 后跟 URL，以便仅查看来自该 URL 的邮件。  键入 后， `url:`DevTools 将显示所有相关 URL。  也可以使用域。  例如，如果 和 `https://example.com/a.js` `https://example.com/b.js` 正在记录消息， `url:https://example.com` 则你可以专注于这两个脚本中的消息。

:::image type="content" source="../media/console-filter-text.msft.png" alt-text="URL 筛选器。" lightbox="../media/console-filter-text.msft.png":::

若要从 URL 隐藏邮件，请键入 `-url:`。  这是一个负 URL 筛选器。

:::image type="content" source="../media/console-negative-filter-text.msft.png" alt-text="隐藏与 URL 匹配的所有邮件的 https://b.wal.co 负 URL 筛选器。" lightbox="../media/console-negative-filter-text.msft.png":::

显示来自单个 URL 的消息：

1. [打开控制台边栏](#open-the-console-sidebar)。

1. 展开 **" # 用户消息"** 部分。

1. 选择包含要关注的消息的脚本的 URL。

:::image type="content" source="../media/console-filter-text-specified.msft.png" alt-text="显示来自邮件wp-ad.min.js。" lightbox="../media/console-filter-text-specified.msft.png":::


### <a name="filter-out-messages-from-different-contexts"></a>筛选出不同上下文的消息

假设您网页上有一个 (广告) 广告。  广告嵌入在 中 `<iframe>` ，在控制台中生成许多 **消息**。  由于广告在不同的 [JavaScript](#select-javascript-context) 上下文中运行，因此隐藏消息的一个方法就是单击控制台 **设置** (![控制台 设置 图标****](../media/settings-button-icon.msft.png)。) 按钮，然后选中"仅选定上下文"旁边的复选框。


### <a name="filter-out-messages-that-dont-match-a-regular-expression-pattern"></a>筛选出与正则表达式模式不匹配的邮件

在"筛选器"文本框`/[gm][ta][mi]/`中键入正则表达式****，以筛选出任何与模式不匹配的邮件。  DevTools 检查是在消息文本中还是导致记录消息的脚本中发现了模式。

:::image type="content" source="../media/console-filter-regex.msft.png" alt-text="筛选出与正则表达式不匹配的任何邮件。" lightbox="../media/console-filter-regex.msft.png":::


<!-- ====================================================================== -->
## <a name="run-javascript"></a>运行 JavaScript

本部分包含与在控制台中运行 JavaScript **相关的功能**。  有关实际操作演练，请参阅运行 [JavaScript](console-javascript.md)。


### <a name="rerun-expressions-from-history"></a>从历史记录重新运行表达式

按 `Up Arrow` 以循环访问之前在控制台中运行 JavaScript 表达式 **的历史记录**。  按 `Enter` 以再次运行该表达式。


### <a name="watch-the-value-of-an-expression-in-real-time-with-live-expressions"></a>使用 Live Expressions 实时监视表达式的值

如果你发现自己在控制台中重复键入相同的 JavaScript 表达式，你可能会**** 发现创建 Live **表达式更容易**。  使用 **Live Expressions**，键入表达式一次，然后将其固定到控制台 **顶部**。  表达式的值几乎可以实时更新。  请参阅 [使用实时表达式Real-Time JavaScript 表达式值](live-expressions.md)。


### <a name="turn-off-eager-evaluation"></a>关闭"期待评估"

**当您在** 控制台中键入 JavaScript 表达式时，"期待评估"将显示返回值的 **预览**。  若要关闭返回值预览，

1. 单击控制台**设置 (**![控制台设置图标](../media/settings-button-icon.msft.png)。) 按钮。
1. 清除"期望评估" **旁边的复选框**。


### <a name="turn-off-autocomplete-from-history"></a>从历史记录中关闭自动完成

键入表达式时，控制台的自动完成弹出窗口将显示之前运行表达式。****  表达式使用 字符预先绘制 `>` 。  若要停止显示历史记录中的表达式，请单击控制台 **设置** (![控制台 设置 图标](../media/settings-button-icon.msft.png)。) 按钮，然后清除"从历史记录自动**完成**"复选框旁边的复选框。

在下图中，`document.querySelector('a')` 和 `document.querySelector('img')` 是之前评估的表达式。

:::image type="content" source="../media/console-filter-text-autofilter-history.msft.png" alt-text="自动完成弹出菜单显示历史记录中的表达式。" lightbox="../media/console-filter-text-autofilter-history.msft.png":::


### <a name="select-javascript-context"></a>选择 JavaScript 上下文

默认情况下，" **JavaScript 上下文** "下拉列表设置为 **顶部**，表示主网页的 [浏览上下文](https://developer.mozilla.org/docs/Glossary/Browsing_context)。

:::image type="content" source="../media/console-dom-level-top.msft.png" alt-text="&quot;JavaScript 上下文&quot;下拉列表。" lightbox="../media/console-dom-level-top.msft.png":::

假设您的网页中嵌入 `<iframe>`了一则广告，并且想要运行 JavaScript 来调整广告的 DOM。  单击 **"JavaScript 上下文** "下拉列表，然后选择广告的浏览上下文：

:::image type="content" source="../media/console-dom-level-multiple.msft.png" alt-text="选择不同的 JavaScript 上下文。" lightbox="../media/console-dom-level-multiple.msft.png":::


<!-- ====================================================================== -->
## <a name="clear-the-console"></a>清除控制台

若要清除控制台，请使用以下任一方法：

*  单击 **"清除控制台 (**![清除控制台](../media/clear-console-button-icon.msft.png)"。) 。

*  右键单击消息，然后选择" **清除控制台"**。

*  在 `clear()` 控制台中键入 ，然后按 `Enter`。

*  从 `console.clear()` 网页的 JavaScript 中调用。

*  在 `Control`+`L` 控制台聚焦时按。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

<!-- if an article's title is adequately descriptive, and the article is in the same TOC bucket as the present article, don't much need a link here: -->
* [在控制台工具中记录消息](console-log.md) - 如何在控制台中筛选日志消息，如信息、警告和错误。
* [开始在控制台中运行 JavaScript](console-javascript.md) - 指导你在控制台中发布 JavaScript 语句和表达式的步骤。
* [控制台对象 API 参考](api.md) - 可以在控制台中输入以将消息写入控制台的函数和表达式，例如 `console.log()`。
* [控制台工具实用程序函数和选择器](utilities.md) - 可在控制台工具中输入的便利函数，**** 例如`monitorEvents()`。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/console/reference)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
