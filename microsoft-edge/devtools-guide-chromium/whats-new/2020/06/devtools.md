---
description: CSS 网格调试功能、使用网络控制台编辑和重播请求等。
title: 'DevTools (Microsoft Edge 85) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: a3a6dd9236bee5285366cc13261e7136b7d5d3c4
ms.sourcegitcommit: 9920f4826b1d16ee0e4842703844437a6d22e816
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2021
ms.locfileid: "12170370"
---
<!-- Copyright Jecelyn Yeen

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="whats-new-in-devtools-microsoft-edge-85"></a>DevTools 85 (Microsoft Edge中的新增) 


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

以下各节列出了你可能错过的来自 DevTools Microsoft Edge通知。  请查看公告以试用 DevTools、Microsoft Visual Studio代码扩展等中的新功能。  若要随时了解开发人员工具中所有最新且最重要的功能，请下载[Microsoft Edge 预览](https://www.microsoftedgeinsider.com/download/)频道，并按照 Twitter 上的[Microsoft Edge DevTools 团队进行跟踪](https://twitter.com/EdgeDevTools)。

### <a name="css-grid-debugging-features"></a>CSS 网格调试功能

:::image type="complex" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="试验功能":::
   试验功能
:::image-end:::

开发人员Microsoft Edge团队与 Chrome DevTools 团队和 Chromium 社区协作，将新的 CSS 网格调试功能添加到 DevTools。  现在，你可以将网格线号、网格间隔和扩展网格线显示为页面上覆盖。  此外，即将推出对网格工具的更多改进。

:::image type="complex" source="../../media/2020/06/experiments-grid.msft.png" alt-text="CSS 网格调试功能" lightbox="../../media/2020/06/experiments-grid.msft.png":::
   CSS 网格调试功能
:::image-end:::

> [!NOTE]
> 若要启用实验，请导航到打开 [实验](../../../experimental-features/index.md#turning-on-experimental-features) 功能，并选中启用新的 CSS 网格调试功能 **旁边的复选框**。
>
> 若要使用示例试用实验，请导航到 [CSS 网格规划器示例](https://codepen.io/hxlnt/full/YzwBzKM)。

Chromium问题[#1047356](https://crbug.com/1047356)

### <a name="edit-and-replay-requests-with-the-network-console"></a>使用网络控制台编辑和重播请求

:::image type="complex" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="试验功能":::
   试验功能
:::image-end:::

你现在可以使用网络控制台**在**网络日志中对请求使用[编辑和](../../../network/index.md#log-network-activity)**重播**。

:::image type="complex" source="../../media/2020/06/experiments-network-console-edit-and-replay.msft.png" alt-text="使用网络控制台在 NetworkLog 中编辑和重播请求" lightbox="../../media/2020/06/experiments-network-console-edit-and-replay.msft.png":::
   使用网络控制台在 [NetworkLog](../../../network/index.md#log-network-activity) 中编辑和 **重播请求**
:::image-end:::

网络控制台是一个新 **面板，它将** 在 [DevTools"](../../../customize/index.md#drawer) 箱"中打开，并自动填充 HTTP 请求的信息。  若要显示从服务器返回的响应，请编辑请求 (并) 发送 **"。**

您还可以使用网络 **控制台** 直接从 DevTools 创建和发送 HTTP 请求。

:::image type="complex" source="../../media/2020/06/experiments-network-console.msft.png" alt-text="网络控制台面板" lightbox="../../media/2020/06/experiments-network-console.msft.png":::
   网络 **控制台** 面板
:::image-end:::

> [!TIP]
> To display **Network Console** in the main (top) panel instead of the [DevTools Drawer，](../../../customize/index.md#drawer)navigate to [moving tools between panels](#move-tools-between-panels).

> [!NOTE]
> 若要启用实验，请导航到 [打开实验](../../../experimental-features/index.md#turning-on-experimental-features) 功能，然后选择启用网络控制台旁边的 **复选框**。
>
> 打开网络[日志](../../../network/index.md#log-network-activity)，打开上下文菜单 (右键单击") "，然后选择"编辑和**重播"。**

Chromium问题[#1093687](https://crbug.com/1093687)

### <a name="service-worker-respondwith-events-in-the-timing-tab"></a>服务工作者 respondWith"计时"选项卡中的事件

网络**工具****的"** 计时"选项卡现在包括 `respondWith` 服务工作器事件。  服务工作线程事件显示从服务工作进程事件处理程序开始运行前一段时间到处理程序承诺得到实现的时间 `respondWith` `fetch` `respondWith` `fetch` 的持续时间。

:::image type="complex" source="../../media/2020/06/timing-tab.msft.png" alt-text="&quot;网络&quot;面板的&quot;计时&quot;选项卡中的 respondWith 服务工作线程事件" lightbox="../../media/2020/06/timing-tab.msft.png":::
   网络 `respondWith` 工具的" **计时"** 选项卡中的服务 **工作器** 事件
:::image-end:::

展开 **收到的响应** 以显示来自响应的其他信息， `fetch` 如 `CacheStorageCacheName` 、 `serviceWorkerResponseSource` 和 `ResponseTime` 。

:::image type="complex" source="../../media/2020/06/timing-tab2.msft.png" alt-text="展开收到的响应以显示提取响应中的附加信息" lightbox="../../media/2020/06/timing-tab2.msft.png":::
   展开 **收到的响应** 以显示来自响应的其他 `fetch` 信息
:::image-end:::

Chromium问题[#1066579](https://crbug.com/1066579)

### <a name="webhint-feedback-in-the-issues-panel"></a>问题面板中的 webhint 反馈

:::image type="complex" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="试验功能":::
   试验功能
:::image-end:::

[webhint](https://webhint.io) 是一个开放源代码工具，提供有关网站的辅助功能、跨浏览器兼容性、安全性、性能、PWA 和其他常见 Web 开发问题实时反馈。  查看"问题"面板中的 [webhint](../../../issues/index.md) 反馈。

:::image type="complex" source="../../media/2020/06/experiments-webhint.msft.png" alt-text="问题面板中的 webhint 反馈" lightbox="../../media/2020/06/experiments-webhint.msft.png":::
   问题面板中的 webhint 反馈
:::image-end:::

> [!NOTE]
> 若要启用实验，请导航到打开 [实验](../../../experimental-features/index.md#turning-on-experimental-features) 功能，然后选择启用 **Webhint 旁边的复选框**。
>
> 打开" [问题](../../../issues/index.md) "面板以显示来自 Webhint 的反馈。

Chromium问题[#1070378](https://crbug.com/1070378)

### <a name="move-tools-between-panels"></a>在面板之间移动工具

:::image type="complex" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="试验功能":::
   试验功能
:::image-end:::

通常，仅在 DevTools**** 的顶部 (打开元素和网络) 等工具。 ****  同样，诸如**3D 视图**和**** 问题等工具可能只能在 DevTools (底部的) 箱中打开。  现在，你能够通过在顶部和底部面板之间移动工具来自定义 DevTools 布局。

:::image type="complex" source="../../media/2020/06/experiments-move-panels.msft.png" alt-text="在面板之间移动工具" lightbox="../../media/2020/06/experiments-move-panels.msft.png":::
   在面板之间移动工具
:::image-end:::

> [!NOTE]
> 若要启用实验，请导航到打开 [实验](../../../experimental-features/index.md#turning-on-experimental-features) 功能，然后选择启用支持以在面板之间 **移动选项卡旁边的复选框**。

Chromium问题[#897944](https://crbug.com/897944)

### <a name="improved-initiator-tooltip-in-the-network-panel"></a>网络面板中改进的发起人工具提示

在 Microsoft Edge 83 和 84 中，"发起者"列的工具提示显示在使用水平滚动条显示的"网络日志[](../../../network/index.md#log-network-activity)"中，显示资源请求的原因。  你仅能够在工具提示中水平滚动来显示发起请求的调用堆栈。

:::image type="complex" source="../../media/2020/06/initiator-tooltip-84.msft.png" alt-text="84 中的发起Microsoft Edge提示" lightbox="../../media/2020/06/initiator-tooltip-84.msft.png":::
   84 中的发起Microsoft Edge提示
:::image-end:::

从 Microsoft Edge 85 开始，现在可以在工具提示中显示 Initiator 调用堆栈，而无需水平滚动。

:::image type="complex" source="../../media/2020/06/initiator-tooltip-85.msft.png" alt-text="85 中的发起Microsoft Edge提示" lightbox="../../media/2020/06/initiator-tooltip-85.msft.png":::
   85 中的发起Microsoft Edge提示
:::image-end:::

Chromium问题[#1069404](https://crbug.com/1069404)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下各节宣布 85 Microsoft Edge开放源代码管理项目中提供的其他Chromium功能。

### <a name="style-editing-for-css-in-js-frameworks"></a>CSS-in-JS 框架的样式编辑

现在 **，"** 样式"窗格可以更好地支持使用 CSS 对象模型和 [CSSOM ](https://drafts.csswg.org/cssom) (API 创建的) 样式。  许多 CSS-in-JS 框架和库在构建样式的底层使用 CSSOM API。

现在您可以使用可构造样式表编辑在 JavaScript 中添加 [的样式](https://wicg.github.io/construct-stylesheets/)。  可构造的样式表是使用 Shadow DOM 时创建和分发可重用样式 [的一种新方式](https://developer.mozilla.org/docs/Web/Web_Components/Using_shadow_DOM)。

例如，使用 `h1` CSSOM API `CSSStyleSheet` (的) 以前不可编辑。  样式现在在"样式"面板中 **可** 编辑。

:::image type="complex" source="../../media/2020/06/css-in-js.msft.png" alt-text="将随 CSSStyleSheet 一起添加的 h1 样式的背景属性从粉色更改为浅色" lightbox="../../media/2020/06/css-in-js.msft.png":::
   将 `background` 随 一起 `h1` 添加的样式 `CSSStyleSheet` 的属性从 更改 `pink` 到 `lightblue` 。
:::image-end:::

通过使用 [CSS-in-JS](https://codepen.io/zoherghadyali/full/abdGrPZ)的示例试用此功能。  有关详细信息，请导航到 [STYLE editing for CSS-in-JS frameworks](../../../css/css-in-js.md)。

Chromium问题[#946975](https://crbug.com/946975)

### <a name="lighthouse-6-in-the-lighthouse-panel"></a>Lighthouse 面板中的"浅楼 6"

**Lighthouse**面板现在运行 Lighthouse 6。  有关所有更改的完整列表，请导航到 [v6.0.0 发行说明](https://github.com/GoogleChrome/lighthouse/releases/tag/v6.0.0)。

Lighthouse 6.0 向报告引入了三个新指标：最大内容量 画图 (LCP) 、累积布局班次 (CLS) 和总阻止时间 (TBT) 。

性能分数公式也进行了重新加权，以更好地反映用户的加载体验。

Chromium问题[#772558](https://crbug.com/772558)

#### <a name="first-meaningful-paint-deprecation"></a>First Meaningful 画图弃用

First Meaningful 画图 (FMP) is deprecated in Lighthouse 6.0.  FMP 也从"性能" **面板中删除** 。  **最大的 Contentful 画图**FMP 的建议替代项。  <!--For an explanation of why it was deprecated, navigate to [First Meaningful Paint](https://web.dev/first-meaningful-paint).  -->

<!--todo: add Largest Contentful Paint when section available  -->
<!--todo: add First Meaningful Paint link and note when available  -->

Chromium问题[#1096008](https://crbug.com/1096008)

### <a name="support-for-new-javascript-features"></a>支持新的 JavaScript 功能

DevTools 现在更好地支持一些最新的 JavaScript 语言功能。

:::row:::
   :::column span="1":::
      [可选链接](https://v8.dev/features/optional-chaining) 语法自动完成
   :::column-end:::
   :::column span="2":::
      控制台中的属性自动 **完成现在支持** 可选的链接语法，例如，除了 和 之外，  `name?.` 现在也可以 `name.` `name[` 正常工作。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      用于私有字段 [的语法突出显示](https://v8.dev/features/class-fields#private-class-fields)
   :::column-end:::
   :::column span="2":::
      私有类字段现在在"源"面板中正确突出显示了语法 **并非常打印** 。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      Nullish [并集运算符的语法突出显示](https://v8.dev/features/nullish-coalescing)
   :::column-end:::
   :::column span="2":::
      DevTools 现在可以在"源"面板中正确打印空的"并 **排"运算符** 。
   :::column-end:::
:::row-end:::

Chromium问题[#1073903](https://crbug.com/1073903)， [#1083214](https://crbug.com/1083214)， [#1083797](https://crbug.com/1083797)

### <a name="new-app-shortcut-warnings-in-the-manifest-pane"></a>清单窗格中的新应用快捷方式警告

**应用快捷方式** 可帮助用户在 Web 应用中快速启动常见任务或推荐任务。

<!--todo: add App shortcuts when section is live  -->

" **清单** "窗格现在显示针对以下条件的警告。

* 应用快捷方式图标小于 96x96 像素
* 应用快捷方式图标和清单图标不是 (，因为会忽略这些) 

:::image type="complex" source="../../media/2020/06/app-shortcut-warnings.msft.png" alt-text="应用快捷方式警告" lightbox="../../media/2020/06/app-shortcut-warnings.msft.png":::
   应用快捷方式警告
:::image-end:::

Chromium问题[#955497](https://crbug.com/955497)

### <a name="consistent-display-of-the-computed-pane"></a>"计算"窗格的一致显示

现在 **，"** 元素"工具**** 中的"计算"窗格在所有视口大小中一致地显示为一个窗格。  以前 **，当**DevTools**** 视口的宽度较窄时，计算窗格合并在"样式"窗格中。

:::image type="complex" source="../../media/2020/06/computed-pane.msft.png" alt-text="即使 DevTools 较窄，计算窗格也一致显示为单独的窗格" lightbox="../../media/2020/06/computed-pane.msft.png":::
   即使**** DevTools 较窄，计算窗格也一致显示为单独的窗格。
:::image-end:::

Chromium问题[#1073899](https://crbug.com/1073899)

### <a name="bytecode-offsets-for-webassembly-files"></a>WebAssembly 文件的字节码偏移

DevTools 现在使用字节码偏移来显示 Wasm 反汇编的行号。
行号使查看二进制数据更加清晰，并且与 Wasm 运行时引用位置的方式更加一致。

Chromium问题[#1071432](https://crbug.com/1071432)

### <a name="line-wise-copy-and-cut-in-sources-panel"></a>在"源面板"中按照行进行复制和剪切

当在"源"面板编辑器中执行复制[](../../../sources/index.md#using-the-editor-pane-to-view-or-edit-files)或剪切操作时，DevTools 将复制或剪切当前内容行。

:::image type="complex" source="../../media/2020/06/line-wise-cut.msft.png" alt-text="当光标位于第 5 行的末尾时，从 DevTools pen.js复制整行并粘贴到Visual Studio Code" lightbox="../../media/2020/06/line-wise-cut.msft.png":::
   当光标位于第 5 行的末尾时，从 DevToolspen.js复制整行，并粘贴到 Visual Studio Code [。](https://code.visualstudio.com/) ****
:::image-end:::

Chromium问题[#800028](https://crbug.com/800028)

### <a name="console-settings-updates"></a>控制台设置更新

#### <a name="ungroup-same-console-messages"></a>取消同一控制台消息的组

控制台**和控制台**中的组设置现在适用于重复消息。  以前，它只应用于类似的邮件。

例如，以前，DevTools 未取消对邮件进行分组，即使未取消选中" `hello` **组** 相似"。  现在， `hello` 邮件已取消组合。

:::image type="complex" source="../../media/2020/06/ungroup-similar.msft.png" alt-text="取消选中&quot;类似组&quot;时，hello 消息将取消分组" lightbox="../../media/2020/06/ungroup-similar.msft.png":::
   取消 **选中"类似** 组"时 `hello` ，邮件将取消分组
:::image-end:::

通过向控制台发送重复消息的示例尝试 [此功能](https://codepen.io/zoherghadyali/full/zYrjgdJ)。

Chromium问题[#1082963](https://crbug.com/1082963)

### <a name="persisting-selected-context-only-settings"></a>持久化"仅选定上下文"设置

控制台**控制台中的"** 所选上下文设置现在保留。  以前，每次关闭并重新打开 DevTools 时，设置都会重置。  更改使设置行为与其他控制台选项设置一。

:::image type="complex" source="../../media/2020/06/selected-context.msft.png" alt-text="选定的仅上下文设置" lightbox="../../media/2020/06/selected-context.msft.png":::
   **选定的仅上下文** 设置
:::image-end:::

Chromium问题[#1055875](https://crbug.com/1055875)

### <a name="performance-panel-updates"></a>性能面板更新

#### <a name="javascript-compilation-cache-information-in-performance-tool"></a>性能工具中的 JavaScript **编译缓存** 信息

[JavaScript 编译缓存信息](https://v8.dev/blog/code-caching-for-devs) 现在始终显示在"性能 **"工具的** "摘要 **"面板** 中。  以前，如果未发生代码缓存，DevTools 不会显示与代码缓存相关的任何内容。

:::image type="complex" source="../../media/2020/06/js-compilation-cache.msft.png" alt-text="JavaScript 编译缓存信息" lightbox="../../media/2020/06/js-compilation-cache.msft.png":::
   JavaScript 编译缓存信息
:::image-end:::

Chromium问题[#912581](https://crbug.com/912581)

#### <a name="navigation-timing-alignment-in-the-performance-panel"></a>"性能"面板中的导航计时对齐方式

用于 **根据** 录制开始的时间在标尺中显示时间的性能面板。  用户导航的录制时间现已更改，其中 DevTools 现在显示相对于导航的标尺时间。

:::image type="complex" source="../../media/2020/06/nav-timing.msft.png" alt-text="在性能工具中对齐导航计时" lightbox="../../media/2020/06/nav-timing.msft.png":::
   在性能工具中 **对齐导航** 计时
:::image-end:::

First 画图、First Contentful 画图 和 Largest Contentful 画图 事件的时间更新为相对于导航的开始，这意味着计时与 报告 `DOMContentLoaded` 的时间匹配 `PerformanceObserver` 。

Chromium问题[#974550](https://crbug.com/974550)

### <a name="new-icons-for-breakpoints-conditional-breakpoints-and-logpoints"></a>断点、条件断点和登录点的新图标

" **源** "面板具有针对断点、条件断点和日志的新设计。  断点用红色圆圈表示，就像[](https://visualstudio.microsoft.com/)Visual Studio Code Visual Studio。 [](https://code.visualstudio.com/)  添加图标以区分条件断点和日志点。

:::image type="complex" source="../../media/2020/06/breakpoints.msft.png" alt-text="断点" lightbox="../../media/2020/06/breakpoints.msft.png":::
   断点
:::image-end:::

Chromium 问题 [#1041830](https://crbug.com/1041830)


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download/) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-85)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。

