---
title: 使用 Lighthouse 优化网站速度
description: 如何在 DevTools 中使用 Lighthouse 来查找使网站加载速度更快的方法。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 334a7bdf8334377cecf985da1ba3aedfba945445
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12630862"
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
# <a name="optimize-website-speed-using-lighthouse"></a>使用 Lighthouse 优化网站速度

本教程介绍如何使用 DevTools 来查找使网站加载速度更快的方法。

<!-- terminology hit counts as of 1/26/2022:
audit: 93 hits
lighthouse: 9 -->
本教程使用 **Lighthouse** 工具。  **Lighthouse** 工具提供指向第三方网站上托管的内容的链接。  Microsoft 不负责也不控制这些网站的内容，并且可能会收集任何数据。

**Lighthouse** 工具以前称为 **“审核**”工具。  “审核面板”的含义与“Lighthouse 工具”相同。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

*  你应具备基本的 Web 开发体验，类似此[Web 开发类简介](https://www.coursera.org/learn/web-development#syllabus)中所教授的内容。

*  无需了解任何有关负载性能的信息。  本教程介绍负载性能。


<!-- ====================================================================== -->
## <a name="introduction"></a>简介

这是 Tony。  Tony 在猫界很有名。  他建立了一个网站，以便他的粉丝们可以了解他最喜欢的食物。  虽然粉丝们很喜欢这个网站，但 Tony 不断听到有关网站加载缓慢的抱怨。  Tony 要求你帮忙加快站点速度。

![猫托尼](../media/speed-tony.msft.png)


<!-- ====================================================================== -->
## <a name="step-1-audit-the-site"></a>步骤 1：审核站点

无论何时开始改进站点的加载性能，始终都从审核开始。

审核有两个重要功能：

*  创建**基线**，便于参照并测量后续更改。

*  提供有关哪些更改最具影响的**可操作提示**。

### <a name="setup"></a>安装

首先，必须设置网站，以便稍后可以对其进行更改。

1. [打开站点的源代码](https://glitch.com/edit/#!/tony)。  此选项卡称为**编辑器选项卡**。

   ![编辑器选项卡。](../media/speed-glitch-tony-server-js.msft.png)

1. 单击 **“tony**”。  将显示菜单。

   ![单击“tony”后显示的菜单。](../media/speed-glitch-tony-server-js-remix-project.msft.png)

1. 单击 **“混音项目**”。  项目的名称从 **tony** 更改为随机生成的名称。  现在，你拥有了自己的可编辑代码副本。  稍后，可以对此代码进行更改。

1. 单击 **“显示** ”，然后选择 **“新建窗口**”。  演示将在新选项卡中打开。 此选项卡称为**演示选项卡**。 站点加载可能需要一段时间。

   ![演示选项卡。](../media/speed-glitch-tony-show-live.msft.png)

1. 按`Ctrl`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 随呈现的演示网页一起打开。

   ![DevTools 和演示。](../media/speed-glitch-tony-show-live-console.msft.png)

对于本教程中的其余屏幕截图，开发人员工具显示在单独窗口中。  按 `Ctrl``P`+`Shift`+ (Windows、Linux) 或`P``Shift`++`Command` (macOS) 打开命令菜单，键入`Undock`，然后将 **Undock 选择为单独的窗口**。

![DevTools 已撤并到单独的窗口中。](../media/speed-console.msft.png)

### <a name="establish-a-baseline"></a>建立基线

基线是指在改进性能之前有关站点执行情况的记录。

1. 选择 **Lighthouse** 工具。  它可能隐藏在 **更多工具** (![“更多”工具后面。](../media/more-panels-icon.msft.png)) 按钮。

   ![Lighthouse 工具。](../media/speed-audits-performance.msft.png)

   <!--todo: add link to Lighthouse when section is available  -->
   <!-- /web/tools/lighthouse  -->

1. 将审核配置设置与上图中的设置相匹配。  以下是不同选项的说明：

   *  **设备**。  设置为**移动**，更改用户代理字符串并模拟移动视口。  设置为**桌面**，几乎可以关闭**移动**更改。

   *  **审核**。  关闭类别可以防止**审核**面板运行这些审核，并在报告中相应排除。  如果希望显示提供的建议类型，请保留其他类别为"打开"。  关闭类别可以略微加快审核流程。

   *  **限制**。  设置为**模拟慢速 4G、4x CPU 减速**，模拟在移动设备上浏览的典型条件。  它被命名为“模拟”，因为 **审核** 面板实际上不会在审核过程中限制。  相反，它只是推断移动条件下加载页面花费的时间。  另一方面，**应用...** 设置实际上会限制 CPU 和网络，折衷了较长的审核流程。

   *  **清除存储**。  打开复选框，在每次审核前清除与页面相关的所有存储。  如果希望审核站点首次访问者的体验，请保留此设置。  希望重复访问体验时，请关闭此设置。

1. 单击 **“运行审核**”。  10 到 30 秒后，**审核**面板将显示站点性能报告。

   ![网站性能审核面板的报告。](../media/speed-glitch-tony-remix-audits-performance-metrics-collapsed.msft.png)

#### <a name="handling-report-errors"></a>处理报告错误

如果你曾在“审核”面板报告中收到错误，请尝试从**InPrivate**窗口运行演示选项卡，且不打开其他选项卡。  这可以确保在干净状态运行 Microsoft Edge。  尤其是，Microsoft Edge 扩展经常会干扰审核流程。

<!--todo: add screen capture for error in audit -->
<!--
![A report that errored out.](../media/speed-.msft.png)
-->

### <a name="understand-your-report"></a>了解报告

报告顶部的数字是站点的总体性能分数。  稍后，当你对代码进行更改时，显示的数字应上升。  分数越高表示性能越好。

![总体性能分数。](../media/speed-glitch-tony-remix-audits-performance-metrics-collapsed-metrics-highlighted.msft.png)

**指标**部分提供站点性能的定量测量。  每个指标提供对性能不同方面的见解。  例如，**首次内容绘制**会告知内容首次绘制到屏幕的时间，这是用户感知页面加载的重要里程碑，而**可交互时间**则会标记页面似乎准备就绪，足以处理用户交互的时间点。

![“指标”部分。](../media/speed-glitch-tony-remix-audits-performance-metrics-collapsed-highlighted.msft.png)

单击下图中突出显示的切换按钮以显示每个指标的说明。  然后单击 **“了解详细** 信息”阅读相关文档。

![单击突出显示的切换按钮以展开“指标”项。](../media/speed-glitch-tony-remix-audits-performance-metrics-expanded.msft.png)

以下"指标"是页面加载外观屏幕截图的集合。

![加载时页面的显示方式。](../media/speed-glitch-tony-remix-audits-performance-view-trace.msft.png)

**机会**部分提供如何改进此特定页面加载性能的特定提示。

![“机会”部分。](../media/speed-glitch-tony-remix-audits-performance-view-trace.msft.png)

单击机会了解详细信息。

![消除呈现阻止资源的机会。](../media/speed-glitch-tony-remix-audits-performance-opportunities-expanded.msft.png)

单击 **“了解详细** 信息”以显示有关机会重要原因的文档，以及有关如何修复该机会的具体建议。

![消除呈现阻止资源机会的文档。](../media/speed-web-dev-performance-audits.msft.png)

**诊断**部分提供影响页面加载时间的因素的详细信息。

![“诊断”部分。](../media/speed-glitch-tony-remix-audits-performance-diagnostics.msft.png)

**通过审核**部分显示站点正确执行的内容。  单击以展开该部分。

![“已通过的审核”部分。](../media/speed-glitch-tony-remix-audits-performance-passed-audits.msft.png)


<!-- ====================================================================== -->
## <a name="step-2-experiment"></a>步骤 2：试验

审核报告中的机会部分提供如何改进页面性能的提示。  在此部分，你将对基本代码实施建议性更改，并在每次更改后审核站点，从而测量更改对站点速度的影响。

### <a name="enable-text-compression"></a>启用文本压缩

你的报告表明，避免大量网络负载是改进页面性能的一个首要机会。  启用文本压缩是改进页面性能的机会。

文本压缩是指在网络上发送文本文件之前，减少或压缩文本文件的大小。  此压缩类似于发送目录之前如何存档目录以减小大小。

在启用压缩前，以下是手动检查文本资源是否压缩的几种方法。

1. 单击 **“网络** ”工具。

   ![网络面板。](../media/speed-glitch-tony-remix-network.msft.png)

1. 单击 **“网络设置** ”图标。

1. 单击 **“使用大型请求行”** 复选框。  网络请求表中行的高度将增加。

   ![网络请求表中的大行。](../media/speed-glitch-tony-remix-network-use-large-request-rows.msft.png)

1. 如果未显示网络请求表中的 **“大小**”列，请单击“大小”>表**标题。**

每个**大小** 单元格将显示两个值。  顶部值是已下载资源的大小。  底部值是未压缩资源的大小。  如果这两个值相同，则在通过网络发送资源时不会对其进行压缩。  例如，在上图中，`bundle.js`顶部和底部的值为`1.2 MB`和`1.2 MB`。

通过检查资源的 HTTP 标头检查压缩：

1. 单击 `bundle.js`”

1. 单击 **“标头”** 面板。

   ![“标头”面板。](../media/speed-glitch-tony-remix-network-use-large-request-rows-bundle-js.msft.png)

1. 在**响应标头**部分搜索`content-encoding` 标头。  `content-encoding`未显示标题，这意味着`bundle.js`未压缩。  压缩资源时，此标头通常设置为 `gzip`、`deflate`或`br`。  有关值的说明，请参阅 [指令](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Encoding#Directives)。

说明已足够;是时候进行一些更改了。  通过添加几行代码来启用文本压缩，如下所示。

1. 在编辑器选项卡中，选择 **server.js**。

   ![编辑server.js。](../media/speed-glitch-tony-remix-server-js.msft.png)

1. 将以下代码添加到**server.js**。  请确保将 `app.use(express.static('build'))`置于`app.use(compression())`之前。

   ```javascript
   const express = require('express');
   const app = express();
   const fs = require('fs');
   const compression = require('compression');
   app.use(compression());
   app.use(express.static('build'));
   const listener = app.listen(process.env.PORT || 1234, function () {
      console.log(`Listening on port ${listener.address().port}`);
   });
   ```

   > [!NOTE]
   > 通常，你必须通过`npm i -S compression`等方式安装`compression`包，但此操作已为你完成。

1. 等待 Glitch 部署站点的新内部版本。  **工具**旁边的奇特动画意味着正在重新生成和部署站点。  当**工具**旁边的动画消失时， 更改已准备就绪。  单击 **“显示** ”，然后再次选择 **“新建窗口** ”。

   <!--
   ![The animation that indicates that the site is getting built.](../media/speed-glitch-tony-remix-server-js-edited.msft.png)
   -->

按照你之前了解的工作流，手动检查压缩是否工作：

1. 返回到演示选项卡并刷新页面。  现在，**大小**列应显示`bundle.js`等文本资源的 2 个不同值。  在下图中，`bundle.js``256 KB`的顶部值是在网络中发送的文件的大小，而`1.2 MB`的底部值是未压缩文件的大小。

   ![“大小”列现在显示文本资源的两个不同的值。](../media/speed-glitch-tony-remix-network-main.msft.png)

1. “ **响应标头** ”部分 `bundle.js` 现在包含一个 `content-encoding: gzip` 标头：

   ![“响应标头”部分现在包含“内容编码”标头。](../media/speed-glitch-tony-remix-network-bundle-js-headers-response.msft.png)

再次审核页面，测量文本压缩对页面加载性能的影响类型：

1. 选择 **灯塔** 工具 (以前称为审核工具) 。

1. 单击 **“执行审核** (![执行审核。](../media/perform-icon.msft.png)) 。

1. 将设置与之前保持相同。

1. 单击 **“运行审核**”。

   ![启用文本压缩后的审核报告。](../media/speed-glitch-tony-remix-updated-audits-performance.msft.png)

总体性能分数应已提高，这意味着站点速度加快。

#### <a name="text-compression-in-the-real-world"></a>现实世界中的文本压缩

大多数服务器都有用于启用压缩的简单修补程序。  搜索如何配置用于压缩文本的任何服务器。

### <a name="resize-images"></a>调整图像大小

你的报告表明，避免大量网络负载是改进页面性能的一个首要机会。  调整图像大小有助于减少网络负载的大小。  如果用户在宽度为 500 像素的移动设备上查看图像，则发送宽度为 1500 像素的图像就豪无意义。  理想情况下，最多发送宽度为 500 像素的图像。

1. 在报表中，选择 **“避免巨大的网络有效负载** ”以显示应调整其大小的图像。  看起来其中两个 `.jpg` 文件超过 2000 KB，比需要的要大。

   <!--
   ![Details about the properly size images opportunity.](../media/speed-glitch-tony-remix-updated-audits-performance-opportunities-expanded.msft.png)
   -->

1. 返回到编辑器选项卡，打开`src/model.js`。

1. 将`const dir = 'big'`替换为`const dir = 'small'`。  此目录包含已调整大小的相同图像的副本。

1. 再次审核页面，了解更改如何影响负载性能。

   ![调整图像大小后的审核报告。](../media/speed-glitch-compression-small-images-audits-performance.msft.png)

此更改仅对整体性能分数产生轻微影响。  但是，分数没有清楚地显示的一件事是你要为用户节省多少网络数据。  旧照片的总大小约为5.3兆字节，而现在只有0.18兆字节左右。

#### <a name="resizing-images-in-the-real-world"></a>在现实世界中调整图像大小

对于小型应用，执行一次性调整大小可能足够好。  但对于大型应用，这是不可缩放的。  以下是一些在大型应用中管理图像的策略：

*  在编译流程中调整图像大小。

*  在编译流程中创建每个图像的多个大小，然后在`srcset`代码中使用。  在运行时，浏览器会负责选择最适合设备的大小。  <!-- See [Responsive images](https://web.dev/responsive-images/). -->

*  使用图像 CDN，可以在发出请求时动态调整图像大小。

*  至少，可以优化每个图像。  这通常会产生巨大的节省。

优化是指通过减少图像文件大小的特殊程序运行图像。  有关详细提示，请参阅 [基本图像优化](https://images.guide)。

### <a name="eliminate-render-blocking-resources"></a>消除阻止渲染资源

你的最新报告显示，现在，消除阻止渲染资源是最大机会。

阻止渲染资源是外部 JavaScript 或 CSS 文件，浏览器必须在显示页面前下载、分析和运行此文件。  目标是只运行正确显示页面所需的 CSS 和 JavaScript 核心代码。

然后，第一个任务是查找不需要在页面加载时运行的代码。

1. 单击 **“消除呈现阻止资源** ”以显示正在阻止的资源： `lodash.js` 和 `jquery.js`。

   ![有关消除呈现阻止资源机会的详细信息。](../media/speed-glitch-tony-remix-updated-audits-performance-oppportunities-expanded.msft.png)

1. 按 `Ctrl``P`+`Shift`+ (Windows、Linux) 或`P``Shift`++`Command` (macOS) 打开命令菜单，开始键入`Coverage`，然后选择 **“显示覆盖范围**”。

   ![从“审核”面板打开命令菜单。](../media/speed-glitch-tony-remix-updated-audits-performance-oppportunities-expanded-command-coverage.msft.png)

   ![覆盖工具。](../media/speed-glitch-tony-remix-updated-audits-performance-oppportunities-expanded-drawer-coverage.msft.png)

1. 单击 **“刷新** (![刷新。](../media/reload-icon.msft.png)) 。  **覆盖**工具概述了加载页面时 `bundle.js`、`jquery.js`和`lodash.js`中运行的代码量。  在下图中，大约 76% 和 30% 的 jQuery 和 Lodash 文件未分别使用。

   ![覆盖报告。](../media/speed-glitch-tony-remix-updated-audits-performance-oppportunities-expanded-drawer-coverage-reloaded.msft.png)

1. 单击该行 `jquery.js` 。  DevTools 会在 **“源** ”工具中打开该文件。  如果运行了一行代码，则其旁边会显示一条蓝色条形图。  红色条形图表示代码行未运行，并且在加载网页时绝对不需要。

   ![在“源”工具中查看 jQuery 文件。](../media/speed-glitch-tony-remix-updated-sources-drawer-coverage-reloaded-jquery-js.msft.png)

1. 滚动浏览 jQuery 代码。  运行的某些行实际上只是注释。  若要删除注释并减小文件大小，请通过缩小器应用或脚本运行代码。

简言之，使用自己的代码时， **覆盖** 范围工具可帮助你逐行分析代码，并且仅提供页面加载所需的代码。

加载页面时是否需要`jquery.js`和`lodash.js`文件？  **请求阻止**工具显示资源不可用时会发生什么情况：

1. 选择 **网络** 工具。

1. 按 `Ctrl`++`Shift``P` (Windows、Linux) 或`P` `Command`+`Shift`+ (macOS) 再次打开命令菜单。

1. 开始键入 `blocking`，然后选择 **“显示请求阻止**”。

   ![请求阻止工具。](../media/speed-glitch-tony-remix-updated-network-drawer-request-blocking-empty.msft.png)

1. 单击 **“添加模式** (![添加模式。](../media/add-pattern-icon.msft.png)) 键 `/libs/*`入，然后按下 `Enter` 确认。

   ![添加一个模式来阻止对 libs 目录的任何请求。](../media/speed-glitch-tony-remix-updated-network-drawer-request-blocking-added.msft.png)

1. 刷新页面。  jQuery 和 Lodash 请求为红色，意味着请求被阻止。   页面仍然加载且是交互式的，因此看起来不需要这些资源！

   ![“网络”面板显示请求已被阻止。](../media/speed-glitch-tony-remix-updated-network-reloaded-drawer-request-blocking-added.msft.png)

1. 单击 **“删除所有模式** (![删除所有模式。](../media/remove-icon.msft.png)) 删除 `/libs/*` 阻止模式。

通常， **请求阻止** 工具可用于模拟页面在任何给定资源不可用时的行为方式。

现在，从代码中删除这些文件的引用并再次审核页面：

1. 返回到编辑器选项卡，打开`template.html`。

1. 删除`<script src="/libs/lodash.js">`和`<script src="/libs/jquery.js"></script>`。

1. 等待站点重新生成和部署。

1. 从**审核**工具再次审核页面。  总体分数应再次提高。

   ![删除呈现阻止资源后的审核报告。](../media/speed-glitch-tony-remix-updated-2-audits-performance.msft.png)

#### <a name="optimizing-the-critical-rendering-path-in-the-real-world"></a>在现实世界优化关键渲染路径

**关键渲染路径**是指加载页面所需的代码。  通常，在页面加载期间仅交付关键代码，然后延迟加载其他所有内容，可以加快页面加载速度。

<!-- [Critical Rendering Path](/web/fundamentals/performance/critical-rendering-path/) -->

*  不太可能找到可以直接删除的脚本，但你可能会发现在页面加载期间不需要请求的许多脚本，而可以异步请求这些脚本。  <!-- See [Using async or defer](/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript/#use_async_or_defer). -->

*  如果使用的是框架，请检查它是否具有生产模式。  此生产模式可能使用 [树摇动](https://webpack.js.org/guides/tree-shaking) 等功能来消除阻止关键呈现的不必要的代码。

### <a name="do-less-main-thread-work"></a>减少主线程工作

最新报告的机会部分表明存在一些细微的潜在节省，但如果往下查看"诊断"部分，似乎最大的瓶颈是主线程活动过多。

在主线程中，浏览器执行显示页面所需的多数工作，例如分析和运行 HTML、CSS 和 JavaScript。

目标是使用“性能”面板分析页面加载时主线程执行的工作，并找到延迟或删除不必要工作的方法。

1. 选择 **“性能** ”工具。

1. 单击 **“捕获设置** (![捕获设置。](../media/capture-icon.msft.png)) 。

1. 将**网络**设置为**慢速 3G**，**CPU**设置为**6x 减速**。  移动设备的硬件约束通常比笔记本电脑或台式机多，因此这些设置可以让你就像使用不那么强大的设备一样体验页面加载。

1. 单击 **“刷新** (![刷新。](../media/reload-icon.msft.png)) 。  开发人员工具会刷新页面，然后生成加载页面所执行的所有工作的可视化效果。  此可视化效果称为**跟踪**。

   ![页面加载的性能工具跟踪。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu.msft.png)

跟踪从左到右，按时间顺序显示活动。  顶部的 FPS、CPU 和 NET 图表概述了每秒帧数、CPU 活动以及网络活动。  下图中黄色突出显示的信息块表明，CPU 完全忙于脚本活动。  这表明你可以减少 JavaScript 工作，从而加快页面加载速度。

![跟踪的“概述”部分。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu-main-highlight.msft.png)

调查跟踪，查找减少 JavaScript 工作的方法：

1. 单击 **“计时”** 部分以展开它。  基于React可能有大量[计时度量](https://developer.mozilla.org/docs/Web/API/User_Timing_API)值，Tony 的应用似乎正在使用React的开发模式。  切换到 React 的生产模式可能会产生一些简单的性能优势。

   ![“计时”部分。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu-timings.msft.png)

1. 再次单击 **“计时** ”以折叠该部分。

1. 浏览**主要**部分。  此部分从左到右，按时间顺序显示了主线程活动的记录。  y 轴（从上到下）表示事件发生的原因。  例如，在下图中，`Evaluate Script`事件导致`(anonymous)`函数运行，继而导致`(anonymous)`运行，然后导致`__webpack__require__`运行，以此类推。

  ![Main 部分。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu-main.msft.png)

1. 向下滚动到**主要**部分的底部。  使用框架时，多数上部活动由框架引起，框架通常无法控制。  你的应用引起的活动通常位于底部。  在此应用中，名为`App`的函数似乎引起了对`mineBitcoin`函数的大量请求。  听起来托尼可能在利用他的粉丝的设备来挖掘加密货币...

   ![将鼠标悬停在 mineBitcoin 活动上。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu-timings-minebitcoin.msft.png)

   > [!NOTE]
   > 尽管框架发出的请求通常不受你控制，但有时可能会以导致框架运行效率低下的方式来构建应用。  重构应用、高效使用框架是减少主线程工作的一种方法。  但是，这要求深入了解框架的工作方式，以及对代码进行哪些更改可以更有效地使用框架。

1. 展开**自上而下**部分。  此选项卡将分解占用时间最多的活动。  如果“ **自下而上** ”部分中未显示任何内容，请单击 **Main** 节的标签。  **自上而下**部分只显示当前选择的活动或活动组的信息。  例如，如果选择`mineBitcoin`中的一个活动，则**自上而下**部将只显示该活动的信息。 

   ![“Bottom-Up”选项卡。](../media/speed-glitch-tony-remix-performance-slow-network-slow-cpu-timings-summary-minebitcoin.msft.png)

**自我时间**列显示每个活动直接花费的时间。  例如，在下图中，约 63% 的主线程时间用于`mineBitcoin`函数。

是时候看看使用生产模式和减少 JavaScript 活动是否会加速页面加载。  从生产模式开始：

1. 在编辑器选项卡中，打开`webpack.config.js`。

1. 将`"mode":"development"`更改为`"mode":"production"`。

1. 等待新内部版本部署。

1. 再次审核页面。

   ![将 Webpack 配置为使用生产模式后的审核报告。](../media/speed-glitch-tony-remix-updated-3-audits-performance.msft.png)

通过删除对`mineBitcoin`的请求减少 JavaScript 活动：

1. 在编辑器选项卡中，打开`src/App.jsx`。

1. 在`constructor`中，为对`this.mineBitcoin(1500)`的请求添加备注。

1. 等待新内部版本部署。

1. 再次审核页面。

   ![删除不必要的 JavaScript 工作后的审核报告。](../media/speed-glitch-tony-remix-updated-4-audits-performance.msft.png)

最后更改似乎大幅提升了性能！

本部分提供了对性能工具的简要介绍。  若要详细了解如何分析页面性能，请参阅 [性能功能参考) ](../evaluate-performance/reference.md)。

#### <a name="doing-less-main-thread-work-in-the-real-world"></a>在现实世界中减少主线程工作

**性能**工具是了解网站在加载时执行哪些活动的最常见方法，并找到删除不必要的活动的方法。

如果你倾向于更像`console.log()`的方法，则[用户计时 API](https://developer.mozilla.org/docs/Web/API/User_Timing_API)将允许你任意标记应用生命周期的某些阶段，从而跟踪每个阶段花费的时间。


<!-- ====================================================================== -->
## <a name="summary"></a>摘要

*  无论何时开始优化站点的加载性能，始终都从审核开始。  审核会建立基线，并提供如何改进的提示。
*  一次进行一个更改，并在每次更改后审核网页，从而显示独立更改对性能的影响。


<!-- ====================================================================== -->
<!--
## Next steps

*  Run audits on your own site!  If you need help interpreting your report, or finding ways to improve your load performance, check out [Feedback](#feedback) for ways to get help from the DevTools community.  Stack Overflow, the mailing list, or Twitter are probably best for these types of questions.
*  Please leave [feedback](#feedback) on this tutorial.  The data is used to make better tutorials.
-->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/speed/get-started/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
