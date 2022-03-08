---
title: 关于工具列表
description: 关于 DevTools 中的工具列表。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/02/2022
ms.openlocfilehash: 3eb97f5ae354352353280b2e047b078ed72ef004
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430599"
---
# <a name="about-the-list-of-tools"></a>关于工具列表

DevTools 提供 35 种工具：
*  两个工具栏**** 图标，用于!["检查"工具 ("检查"工具图标](media/inspect-tool-icon-light-theme.png)。**) 设备仿真** ("设备仿真](media/device-emulation-icon-light-theme.png)"![图标。) 。
*  3 个永久工具栏选项卡，用于**元素****、控制台**和**源**工具。
*  30 个可选工具栏选项卡，用于可选工具。

默认工具，包括工具栏图标、工具栏选项卡和"更多选项卡" (**** 选项卡](media/more-tabs-icon-light-theme.png)图标上的工具。![) 菜单：

![DevTools 的所有默认工具，包括 2 个工具栏图标和 11 个工具栏选项卡或"更多选项卡"菜单。](media/all-default-tools.png)

默认情况下未打开的可选工具，****![位于"更多工具" ("](media/more-tools-icon-light-theme.png)工具"图标上。) 菜单：

![DevTools 的所有可选工具（在"更多工具"菜单上）包含 22 个可选工具。](media/all-optional-tools.png)

以下功能是访问工具的其他方式：
*  The **Drawer** is an additional toolbar and area to hold tool tabs.
*  命令 **菜单** 是直接使用工具功能的一种方法。
*  **设置页面**可以打开工具的其他功能。


<!-- ====================================================================== -->
## <a name="overview-of-all-tools"></a>所有工具概述

Microsoft Edge DevTools 包括以下工具。

| 工具 | 用途 | 文章 |
| --- | --- | --- |
| **3D 视图** 工具 | 浏览翻译为 3D 视角的网页。  通过浏览 DOM 或 z 索引堆栈上下文调试网页。 | [使用 3D 视图工具导航 z 索引、DOM 和层](3d-view/index.md) |
| **动画** 工具 | 使用动画工具中的动画检查器检查和**** 修改 CSS **动画**效果。 | [检查和修改 CSS 动画效果](inspect-styles/animations.md) |
| **应用程序** 工具 | _HTTP Cookie_ 用于管理用户会话、存储用户个性化首选项和跟踪用户行为。  使用**应用程序工具**的"Cookie"**** 窗格查看、编辑和删除网页的 HTTP Cookie。 | [查看、编辑和删除 Cookie](storage/cookies.md) |
| **更改** 工具 | 跟踪你在 DevTools 中对 CSS 或 JavaScript 进行的任何更改。  显示使用 DevTools 修改从服务器发送的网页文件后对实际源文件进行哪些更改。 | [使用更改工具跟踪对文件的更改](changes/changes-tool.md) |
| **控制台** 工具 | DevTools 中的智能、丰富的命令行。  用于其他工具的出色的配套工具。  提供一种功能强大的脚本功能、检查当前网页和使用 JavaScript 操作当前网页的方法。 | [控制台概述](console/index.md) |
| **覆盖** 工具 | 帮助你查找未使用的 JavaScript 和 CSS 代码，以加快页面加载速度并保存移动用户手机网络数据。 | [使用覆盖工具查找未使用的 JavaScript 和 CSS 代码](coverage/index.md) |
| **CSS 概述** 工具 | 帮助你更好地了解页面的 CSS 并确定潜在的改进。 | [CSS 概述工具](css/css-overview-tool.md) |
| **分离的元素** 工具 | 为了提升页面性能，此工具查找浏览器无法进行垃圾回收的已分离元素，并标识仍在引用已分离元素的 JavaScript 对象。  通过更改 JavaScript 以释放 元素，可以减少页面上的分离元素数量，从而提升页面性能和响应能力。 | [使用分离的元素工具调试 DOM 内存泄漏](memory-problems/dom-leaks.md) |
| **开发人员资源** | 显示网页的资源 URL。 | [开发人员资源工具](developer-resources/developer-resources.md) |
| **设备仿真** | 使用 **设备仿真** 工具（有时称为 _设备_模式）大致了解你的页面在移动设备上的外观和响应方式。 | [模拟移动设备（设备仿真）](device-mode/index.md) |
| **元素** 工具 | 检查、编辑和调试 HTML 和 CSS。  可以在浏览器中实时显示更改时在工具中进行编辑。  使用 DOM 树调试 HTML，并检查并处理网页的 CSS。 | [使用 Elements 工具检查、编辑和调试 HTML 和 CSS](elements-tool/elements-tool.md) |
| **检查** 工具 | 使用 **Inspect** 工具查看有关已呈现网页中的项目的信息。  当 **Inspect 工具** 处于活动状态时， _将鼠标_ 悬停在网页中的项目上，DevTools 在网页上添加信息覆盖信息和网格突出显示。 | [使用检查工具分析页面](css/inspect.md) |
| **问题** 工具 | 问题 **工具** 将自动分析当前网页，报告按类型分组的问题，并提供文档以帮助解释和解决问题。 | [使用问题工具查找和修复问题](issues/index.md) |
| **JavaScript Profiler** 工具 | 此工具已被性能工具和**内存****工具取代**。 | [JavaScript Profiler 工具](javascript-profiler/javascript-profiler-tool.md) |
| **图层** 工具 | **Layers 工具**表示 3D 空间中的网页。  **图层工具**基本上已替换为 **3D 视图**工具。 | [图层工具](layers/layers-tool.md) |
| **Lighthouse** 工具 | 使用 Lighthouse 工具识别和修复影响网站性能、辅助功能和用户体验的常见问题。 | [Lighthouse 工具](lighthouse/lighthouse-tool.md) |
| **媒体** 工具 | 使用此工具可查看信息并按浏览器选项卡调试媒体播放器。 | [查看和调试媒体播放器信息](media-panel/index.md) |
| **内存** 工具 | 查找影响页面性能的内存问题，包括内存泄漏、内存不足和频繁垃圾回收。 | [修复内存问题](memory-problems/index.md) |
| **内存检查器** 工具 | 使用内存检查器检查 JavaScript ArrayBuffer。 | [使用内存检查器工具检查 JavaScript ArrayBuffer](memory-inspector/memory-inspector-tool.md) |
| **网络** 工具 | 使用 **"** 网络"工具确保资源已如期下载或上载。  检查单个资源的属性，如 HTTP 标头、内容或大小。 | [检查网络活动](network/index.md) |
| **网络条件** 工具 | 使用 **网络条件** 工具禁用浏览器缓存、设置网络限制、设置用户代理字符串和设置内容编码（如 deflate、gzip 和 br）。 | [网络条件工具](network-conditions/network-conditions-tool.md) |
| **网络控制台** 工具 | 使用 **网络控制台** 工具对网络请求 (网络) 查看失败的原因。  更改和重播任何网络请求，并详细调用网络 API。  | [网络控制台工具](network-console/network-console-tool.md) |
| **网络请求阻止** 工具 | 使用 **网络请求阻止** 工具测试阻止对指定 URL 模式的网络请求，并查看网页的行为方式。 | [网络请求阻止工具](network-request-blocking/network-request-blocking-tool.md) |
| **性能** 工具 | 分析运行时性能，这是页面在运行时（而不是加载）时的执行方式。 | [分析运行时性能入门](evaluate-performance/index.md) |
| **性能监视器** 工具 | 提供网页的运行时性能实时视图，以确定性能问题来自何处，使网站运行缓慢。  查找问题来自高内存或 CPU 使用率、布局和样式计算过于频繁，还是 DOM 节点和事件侦听器过多。 | [使用性能监视器工具度量页面的运行时性能](performance-monitor/performance-monitor-tool.md) |
| **快速源** 工具 | 使用 **"源"** 工具外的其他工具时，使用"快速源"工具 **显示或编辑** 源文件。 | [使用快速源工具显示或编辑源文件](quick-source/quick-source-tool.md) |
| **呈现** 工具 | 使用 **呈现** 工具通过不同的显示选项或视觉缺陷查看网页的外观。 | [在呈现的页面中模拟深色或浅色方案](accessibility/preferred-color-scheme-simulation.md) |
| **搜索** 工具 | 使用 **搜索** 工具查找网页的特定源文件，包括 HTML、CSS、JavaScript 和图像文件。 | [使用搜索工具查找页面的源文件](search/search-tool.md) |
| **安全** 工具 | 检查页面的安全性。 | [使用安全工具了解安全问题](security/index.md) |
| **传感器** 工具 | 模拟不同的设备方向。 | [使用传感器工具模拟设备方向](device-mode/orientation.md) |
| **Source 地图 Monitor** 工具 | 使用 **Source 地图 Monitor** 工具监视源地图。 | [Source 地图 Monitor 工具](source-maps-monitor/source-maps-monitor-tool.md) |
| **源** 工具 | 使用 **"源** "工具查看、修改和调试前端 JavaScript 代码，并检查和编辑包含当前网页的 HTML 和 CSS 文件。 | [源工具概述](sources/index.md) |
| **WebAudio** 工具 | 使用 **WebAudio** 工具监视 WebAudio 流量。  **WebAudio** 工具使用 WebAudio API。 | [WebAudio 工具](webaudio/webaudio-tool.md) |
| **WebAuthn** 工具 | 使用 **WebAuthn** 工具创建基于软件的虚拟验证器并与之交互。 | [模拟身份验证器并调试 WebAuthn](webauthn/index.md) |
| **欢迎**工具 | 首次 **打开** DevTools 时将打开欢迎工具。  它显示指向开发人员文档、最新功能、发行说明的链接，以及联系开发人员工具Microsoft Edge选项。 | [欢迎工具](welcome/welcome-tool.md) |


<!-- ====================================================================== -->
## <a name="the-more-tools-menus"></a>"更多工具"菜单

" **更多工具** (**+**) 工具栏和"箱"工具栏上的"更多工具"菜单是动态的：它省略了该工具栏上打开的任何选项卡工具。

自定义 **和控制** **DevTools** ![ (自定义](media/customize-devtools-icon-light-theme.png) 图标中的"更多工具"菜单。) 菜单是静态的：它始终列出所有可选工具。  如果所选工具是面板工具，则打开主工具栏;如果是"箱"工具，则打开在"箱"中。  可以右键单击工具的选项卡以将其移动到其他工具栏。


<!-- ====================================================================== -->
## <a name="panel-tools-vs-drawer-tools"></a>面板工具与箱式工具

在命令 **菜单中**：

* _面板工具_ 是默认在主工具栏中打开的工具。

* _"箱工具_ "是默认情况下在 DevTools 底部的"箱"工具栏中打开的工具。  按 `Esc` 显示或隐藏"箱"。

" **命令菜单** "首先列出面板工具，然后列出"箱"工具：

![命令菜单，显示组合在一起的面板工具，然后是"箱"工具。](media/command-menu-panel-vs-drawer-tools.png)

若要将工具移动到另一个工具栏，请右键单击该工具的选项卡，然后选择"移动到 **底部** "或" **移动到顶部"**。

若要打开命令**菜单**，请按 `Ctrl`++`Shift``P` (Windows/Linux) 或 (`P` `Command`+`Shift`+macOS) 。  或者，单击"自定义和控制 **DevTools** ![ (自定义"图标](media/customize-devtools-icon-light-theme.png) 。) 按钮，然后选择"运行 **"命令**。


<!-- ====================================================================== -->
## <a name="closing-tool-tabs"></a>关闭工具选项卡

若要关闭工具栏上的工具选项卡，

*  单击 **选项卡上的 x** 。

   无法**关闭"** 元素 **"**、****"控制台"和"源"工具选项卡。


一次关闭所有可选选项卡：

*  右键单击工具栏上的可选选项卡 (包含 **x** 按钮的选项卡) ，然后选择"全部 **关闭"**。

   只有**元素****、控制台****和源**保留在主工具栏上。   (**"箱"** 工具栏不受影响。) 

   如果关闭了"收银机"上 **的所有**选项卡，则只有" **控制台"选项卡** 仍保留在"收银 **机"** 工具栏上。   (主工具栏不受影响。) 


<!-- ====================================================================== -->
## <a name="restoring-the-default-tool-tabs"></a>还原默认工具选项卡

还原主工具栏上的所有默认选项卡：

1. 在 DevTools 中，**设置** (设置![图标](media/settings-gear-icon-light-theme.png)。) >**首选项"**。

1. 单击" **还原默认值并刷新"** 按钮。

   主工具栏再次包含所有默认选项卡。  然后 **，"** 箱"仅具有 **"控制台"** 选项卡。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅
 
* [DevTools](overview.md) 概述 - 与当前文章类似，但范围更广，主要介绍了 DevTools。
* [实验功能](experimental-features/index.md#focus-mode)中 _的焦点模式_。  在**焦点模式下**，**活动**栏是主工具栏的精简替换，而快速视图列表是****"箱"工具栏上的选项卡的替换。
