---
title: 用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展
description: 将 Microsoft Edge 开发人员工具扩展用于Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 8b7ad993684b1cca58bc72137f54c3d460b23103
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12815806"
---
# <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

<!-- main page for DevTools extension -->

<!-- lexicon (except ui strings):
Microsoft Edge DevTools extension for Visual Studio Code
Microsoft Edge DevTools extension
CSS Mirroring
CSS mirror editing (lowercased in UI, init capped at github)
-->

借助适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展，可以直接从Visual Studio Code中使用 Microsoft Edge DevTools 和 Microsoft Edge 浏览器（包括设备仿真）的嵌入版本。  Visual Studio Code是适用于 Windows、Linux 和 macOS 的轻型但功能强大的源代码编辑器。  Visual Studio Code包括对 JavaScript、TypeScript 和 Node.js 的内置支持，因此它是 Web 开发人员的绝佳工具，尤其是使用此 DevTools 扩展。

DevTools 扩展提供许多相同的工具，这些工具位于 Microsoft Edge 浏览器中的 DevTools 中，位于Visual Studio Code内。  Visual Studio Code具有强大的 Web 开发功能：
*  Visual Studio Code是一个完整的 IDE (集成开发环境) 。
*  借助其 CSS 镜像编辑，可以控制是否保存对文件所做的 `.css` 更改。

![Visual Studio Code中的 Microsoft Edge 开发人员工具和浏览器预览](microsoft-edge-devtools-extension-images/devtools-extension-v211.png)

使用用于Visual Studio Code的 DevTools 扩展可以：

*  开发网页并使用 DevTools 而无需离开Visual Studio Code。  此扩展提供了在浏览器窗口中使用 DevTools 进行网页开发的替代方法。

*  模拟设备，例如在开发过程中以各种视区大小显示网页。

*  从Visual Studio Code中测试网页的可访问性。

*  实时编辑 CSS 和 SASS，并在编辑实际源文件时立即在浏览器实例中看到所反映的更改。  DevTools 会打开并编辑`.css`文件，但不会自动保存文件，以便你可以决定是否保存在 **“元素**”工具的“**样式**”选项卡中所做的更改。


<!-- ====================================================================== -->
## <a name="approaches-compared"></a>比较的方法

用于Visual Studio Code的 DevTools 扩展是使用 DevTools 更改本地文件的几种不同方法之一。

| 方法 | 优点和缺点 | 文章 |
|---|---|---|
| 浏览器> DevTools > **Elements** 工具 | 必须手动将 DevTools 中的更改复制到源文件中。 | [使用 Elements 工具检查、编辑和调试 HTML 和 CSS](/microsoft-edge/devtools-guide-chromium/elements-tool/elements-tool.md) |
| 浏览器> DevTools > **源** 工具> **文件系统** 选项卡来定义 **工作区** | 始终保存更改，这可能会阻止试验 | [使用“文件系统”选项卡在](/microsoft-edge/devtools-guide-chromium/sources/index.md#using-the-filesystem-tab-to-define-a-local-workspace)_“源”工具概述_中定义本地工作区 |
| 浏览器> DevTools >**设置** > **试验** > **开源文件Visual Studio Code** | 始终保存更改，这可能会阻止试验 | > Visual Studio Code[中打开源文件的](/microsoft-edge/devtools-guide-chromium/sources/opening-sources-in-vscode.md)试验。 |
| 用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展 | 自动打开并编辑 CSS 源文件，但不会自动保存文件，因此可以选择是否保存编辑。 | 本文。 |


<!-- ====================================================================== -->
## <a name="2-way-editing"></a>双向编辑

更改反映在打开的文件夹、 **Edge DevTools** 选项卡和 **Edge DevTools：Browser** 选项卡中的源文件中，如下所示。


#### <a name="css"></a>CSS

通过 CSS 镜像编辑，可以在 **Edge DevTools** 选项卡中更改 CSS，并在或`.css`源文件中`.html`自动更改，并反映在 **Edge DevTools：浏览器**选项卡中。 DevTools 允许你决定是否保存更改，从而允许你进行试验。

可以在或`.html`源文件中`.css`更改 CSS，保存更改，然后在 **Edge DevTools：浏览器**选项卡中重新加载网页，该选项卡还会更新 **Edge DevTools** 选项卡。


#### <a name="html"></a>HTML

可以在 **Edge DevTools** 选项卡中编辑 DOM 树 (如更改 `<h2>Success!</h2>` 为 `<h2>CSS Success!</h2>`) ，然后按下 `Enter`，然后刷新 **Edge DevTools：浏览器** 选项卡以查看更改。   (这不会自动编辑 `.html` 源文件。) 

可以在源文件中 `.html` 更改 HTML，保存更改，然后在 **Edge DevTools：浏览器** 选项卡中重新加载网页，该选项卡还会更新 **Edge DevTools** 选项卡。


<!--js-->


<!-- ====================================================================== -->
## <a name="tasks-supported-by-the-developer-tools"></a>开发人员工具支持的任务

Visual Studio Code的 DevTools 扩展允许执行以下操作：

| 任务 | 文章 |
|---|---|
| 获取源代码中问题的实时分析。 | [内联和实时问题分析](./microsoft-edge-devtools-extension/inline-live-issue-analysis.md) |
| 使用项目的 DevTools 启动新的浏览器实例。 | [打开 DevTools 和 DevTools 浏览器](./microsoft-edge-devtools-extension/open-devtools-and-embedded-browser.md) |
| 模拟不同的设备，并在不同的显示模式下查看项目。 | [设备和状态仿真](./microsoft-edge-devtools-extension/device-state-emulation.md) |
| 使用 **Elements** 工具查看页面的运行时 DOM 结构和布局。 | [从 Elements 工具打开源文件](./microsoft-edge-devtools-extension/opening-source-files-from-elements-tool.md) |
| 使用项目的源文件的实时预览和实时更改来分析和更改项目的 CSS 样式。 | [从 Styles 工具中更新 .css 文件 (CSS 镜像编辑) ](./microsoft-edge-devtools-extension/css-mirror-editing-styles-tab.md) |
| 使用 **网络** 工具分析站点流量。 | [网络工具集成](./microsoft-edge-devtools-extension/network-tool-integration.md) |
| 记录信息，试用 JavaScript，并使用 **控制台** 工具访问 Window/DOM。 | [控制台集成](./microsoft-edge-devtools-extension/console-integration.md) |
| 使用 **应用程序工具** 检查存储和服务辅助角色。 | [应用程序工具集成](./microsoft-edge-devtools-extension/application-tool-integration.md) |
| 使用Visual Studio Code调试工作流中的扩展。 | [在Visual Studio Code中调试时自动打开浏览器和 DevTools](./microsoft-edge-devtools-extension/debugging-a-webpage.md) |


<!-- ====================================================================== -->
## <a name="overview-of-the-tools-in-the-devtools-extension"></a>DevTools 扩展中的工具概述

以下工具包含在用于Visual Studio Code的 DevTools 扩展中。  以下文章不是专门针对 Visual Studio Code 的 DevTools 扩展，而是针对 Microsoft Edge 浏览器 DevTools。

| 工具 | 用途 | 文章 |
| --- | --- | --- |
| **元素**工具 | 检查、编辑、调试 HTML 和 CSS。  可以在浏览器中实时显示更改时在工具中进行编辑。  使用 DOM 树调试 HTML，并检查和处理网页的 CSS。 | [使用 Elements 工具检查、编辑和调试 HTML 和 CSS](../devtools-guide-chromium/elements-tool/elements-tool.md) |
| **控制台**工具 | DevTools 中智能、丰富的命令行。  一个很好的帮手工具，可与其他工具一起使用。  提供了一种编写功能脚本、检查当前网页以及使用 JavaScript 操作当前网页的强大方法。 | [控制台概述](../devtools-guide-chromium/console/index.md) |
| **网络**工具 | 使用 **网络** 工具确保正在按预期下载或上传资源。  检查单个资源的属性，例如 HTTP 标头、内容或大小。 | [检查网络活动](../devtools-guide-chromium/network/index.md) |
| **应用程序**工具 | 使用**应用程序**工具管理 Web 应用页面的存储，包括清单、服务辅助角色、本地存储、Cookie、缓存存储和后台服务。 | [用于管理存储的应用程序工具](../devtools-guide-chromium/storage/application-tool.md) |
| **问题** 工具 | **问题**工具会自动分析当前网页，按类型报告问题，并提供关于解释和解决问题的文档。 | [使用问题工具查找和修复问题](../devtools-guide-chromium/issues/index.md) |
| **网络条件**工具 | 使用**网络条件**工具禁用浏览器缓存、设置网络限制、设置用户代理字符串，以及设置 Content-Encoding（如 deflate、gzip、br）。 | [网络条件工具](../devtools-guide-chromium/network-conditions/network-conditions-tool.md) |
| **网络请求阻止**工具 | 使用**网络请求阻止**工具测试对指定 URL 模式的阻止网络请求，并查看网页的行为方式。 | [网络请求阻止工具](../devtools-guide-chromium/network-request-blocking/network-request-blocking-tool.md) |
| **检查**工具 | 使用**检查**工具查看呈现的网页中的项的相关信息。  当 **“检查** ”工具处于活动状态时，将 _鼠标悬停在_ 网页中的项上，DevTools 会在网页上添加信息覆盖和网格突出显示。 | [使用检查工具分析页面](../devtools-guide-chromium/css/inspect.md) |
| **设备仿真** | 使用 **设备仿真** 工具（也称为 _设备模拟模式_ 或 _设备模式）_ 来大致了解页面在移动设备上的外观和响应方式。 | [模拟移动设备（设备仿真）](../devtools-guide-chromium/device-mode/index.md) |

有关 DevTools 的 Microsoft Edge 浏览器版本中的所有工具的列表，请参阅 _“关于工具”列表_中[的所有工具的概述](../devtools-guide-chromium/about-tools.md#overview-of-all-tools)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./microsoft-edge-devtools-extension/get-started.md)
* [打开 DevTools 和 DevTools 浏览器](./microsoft-edge-devtools-extension/open-devtools-and-embedded-browser.md)

**外部页面：**

* [超级收费 VS Code Live Server](https://dev.to/codepo8/supercharging-vs-code-live-server-1bgi) - 如果在 Visual Studio Code 中使用 [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 扩展来实时查看 Web 产品中的更改，则可以使用 Microsoft Edge DevTools 扩展将浏览器和 DevTools 嵌入到Visual Studio Code Visual Studio Code，从而进一步改善体验。
* [入门](https://code.visualstudio.com/Docs) - Visual Studio Code文档。
* [vscode-edge-devtools 存储库](https://github.com/microsoft/vscode-edge-devtools) - 适用于 Visual Studio Code 的 Microsoft Edge 开发人员工具扩展的源代码。
   * [Changelog 文件](https://github.com/microsoft/vscode-edge-devtools/blob/main/CHANGELOG.md)。
* 适用于 Visual Studio 市场中[Visual Studio Code的 Microsoft Edge DevTools 扩展](https://aka.ms/devtools-for-code)。
