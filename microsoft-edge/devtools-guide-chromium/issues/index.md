---
title: 使用问题工具查找和修复问题
description: 使用问题工具识别和修复当前网页的问题。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/24/2021
ms.openlocfilehash: 990a59d5f5603158526dc6834edf4530f7c8fca2
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431688"
---
<!-- Copyright Sam Dutton

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="find-and-fix-problems-using-the-issues-tool"></a>使用问题工具查找和修复问题

问题 **工具** 将自动分析当前网页，报告按类型分组的问题，并提供文档以帮助解释和解决问题。

问题 **工具** 提供以下类别的反馈：
*  辅助功能。
*  跨浏览器的兼容性。
*  性能。
*  渐进式 Web 应用。
*  安全性。
*  其他。

问题工具**中**的反馈由多个源提供，包括 Chromium 平台、Deque 轴、MDN 浏览器兼容性数据和 webhint。  有关填充问题工具的这些反馈源 **的信息** ，请参阅：
*  [axe 工具概述](https://www.deque.com/axe)
*  [browser-compat-data 存储库](https://github.com/mdn/browser-compat-data)
*  [webhint](https://webhint.io)


<!-- ====================================================================== -->
## <a name="opening-the-issues-tool"></a>打开问题工具

1. 转到包含要修复的问题的网页。  例如，在一 [个新选项卡或窗口中](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 打开辅助功能测试演示页。

1. 打开 DevTools。  几秒钟后，"**** ![](../media/issues-counter-icon.msft.png) 问题" ("问题"计数器。) 显示在 DevTools 的右上角。

1. 刷新页面，因为根据网络请求报告某些问题。  请注意"问题"计数器中的 **更新计数**。

1. 选择" **问题"计数器**。  " **问题** "工具将打开，并分组为不同类别的问题。

   :::image type="content" source="../media/issues-tool-categories.msft.png" alt-text="演示页上的&quot;问题&quot;工具中的问题类别。" lightbox="../media/issues-tool-categories.msft.png":::


### <a name="other-ways-to-open-the-issues-tool"></a>打开问题工具的其他方法

有几种其他方法可以打开 **问题** 工具：
*  单击主**面板或** (**+**) "菜单中的"更多工具"菜单，然后选择"问题 **"**。****
*  选择**自定义和控制 DevTools** >  **更多工具** > **Issues**。
*  在"元素"工具的 DOM **树中**`Shift`，按下并单击带波浪下划线的元素名称。  或者，在带波浪下划线的元素上打开上下文菜单，然后选择" **查看问题"**。


### <a name="issues-are-automatically-ordered-by-severity"></a>问题按严重性自动排序

在每个问题类别中，首先列出错误，然后列出警告，然后列出提示。

:::image type="content" source="../media/issues-ordered-by-severity.msft.png" alt-text="&quot;问题&quot;工具显示按严重性排序的性能问题。" lightbox="../media/issues-ordered-by-severity.msft.png":::

### <a name="include-third-party-issues"></a>包括第三方问题

若要包含由第三方网站导致的问题，请在"问题"工具顶部，选中****"包括第三方问题 **"** 复选框。


<!-- ====================================================================== -->
## <a name="expand-entries-in-the-issues-tool"></a>展开问题工具中的条目

**问题工具**提供了适用于每个问题的其他文档和推荐的修补程序。  若要展开问题以获得此附加信息，请选择一个问题，如下所示。

1. 打开新 [窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示页面，然后打开 DevTools。

1. 打开" **问题"** 工具，选择"问题 **"** (!["计数器](../media/issues-counter-icon.msft.png) 。) 。

1. 选择问题，以展开问题。

   :::image type="content" source="../media/issues-tool-initial-view-accessibility-page.msft.png" alt-text="问题工具，显示有关如何修复该问题的其他信息。" lightbox="../media/issues-tool-initial-view-accessibility-page.msft.png":::

每个显示的问题都具有以下组件：

*  描述问题的标题。

*  提供更多上下文和建议的解决方案的说明。

*  **链接到** DevTools 中的资源的受影响的资源部分，如**元素**、源或**网络**工具。 ****

*  指向更多文档的链接。


<!-- ====================================================================== -->
## <a name="view-issues-in-context-of-an-associated-tool"></a>查看关联工具上下文中的问题

问题工具**中**的问题可能包括打开不同工具（如元素、源或网络工具）的**一个或多个链接**。 ******** 可以打开其中一个工具来执行其他疑难解答步骤。

若要从"问题"工具打开 **链接** 的工具，请执行以下操作：

1. 如上一部分所述，打开演示页面，然后在问题工具 **中展开问题** 。

1. 在 **"受影响的资源** > **打开"中**，选择工具名称。  受影响的资源显示在所选工具中：

   :::image type="content" source="../media/issues-tool-affected-resource-opens-elements-tool.msft.png" alt-text="选择一个工具，从&quot;问题&quot;工具中打开受影响的资源。" lightbox="../media/issues-tool-affected-resource-opens-elements-tool.msft.png":::

    展开的问题可能有"网络 **"** 链接，以在"网络"工具中 **显示受影响的** 资源：

   :::image type="content" source="../media/issues-tab-view-issue.msft.png" alt-text="选择网络资源链接时，将打开&quot;网络&quot;工具。" lightbox="../media/issues-tab-view-issue.msft.png":::


<!-- ====================================================================== -->
## <a name="open-issues-from-the-dom-tree"></a>打开 DOM 树中的问题

如果元素具有关联问题，则 **"** 元素"工具中的 DOM 树在元素名称下显示波浪下划线。  右键单击元素，然后选择" **查看问题"**。  或者，长按 `Shift` ，然后单击带波浪下划线的元素。

若要显示 DOM 树中带波浪下划线的元素的问题：

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 在 DevTools 中，选择" **元素"** 选项卡。

1. 在 DOM 树中，展开 `<body>` >  > `<header>``<form>`。  请注意，元素 `<input>` 具有波浪下划线。

   :::image type="content" source="../media/issues-wavy-underlines-dom-tree.msft.png" alt-text="&quot;元素&quot;工具中 DOM 树中带波浪下划线的问题。" lightbox="../media/issues-wavy-underlines-dom-tree.msft.png":::

1. 将鼠标悬停在 元素 `<input>` 上。  工具提示显示有关该问题的信息。

1. 打开带波浪下划线的元素上的上下文菜单，然后选择" **查看问题"**。  " **问题** "工具将打开并显示与该元素关联的问题。

   :::image type="content" source="../media/issues-opened-from-dom-tree-wavy-underline.msft.png" alt-text="有关 DOM 树中带波浪线下划线的元素的问题的详细信息。" lightbox="../media/issues-opened-from-dom-tree-wavy-underline.msft.png":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [自动测试网页中的辅助功能问题](../accessibility/test-issues-tool.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/issues/index) 由 [Sam Dutton](https://developers.google.com/web/resources/contributors#sam-dutton) (Developer Advocate) 。
[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
