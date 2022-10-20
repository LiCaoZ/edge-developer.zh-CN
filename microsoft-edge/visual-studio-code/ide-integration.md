---
title: Microsoft Edge IDE 集成
description: Microsoft Edge、Visual Studio Code 和 Visual Studio 的 IDE 集成。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/05/2022
ms.openlocfilehash: f70827d44996df597df7cb3a646098455c27a56e
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12815846"
---
# <a name="microsoft-edge-ide-integration"></a>Microsoft Edge IDE 集成

Microsoft 工具的各种功能提供使用 Microsoft Edge、Visual Studio Code 和 Visual Studio 进行开发的集成，以开发在 Microsoft Edge 中使用和使用完全集成的产品、网页和 Web 应用。


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

<!-- keep this section short and similar to top of linked article: -->

用于Visual Studio Code的 Microsoft Edge DevTools 扩展允许你从Visual Studio Code中使用 Microsoft Edge 浏览器的 **Elements** 工具和**网络**工具。

无需离开Visual Studio Code，请使用 Microsoft Edge DevTools 附加到实例或启动 Microsoft Edge 实例，然后：
* 查看运行时 HTML 结构。
* 更改网页布局。
* 更改 CSS 样式并修复样式问题。
* 读取控制台消息。
* 查看网络请求。

参阅[适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](microsoft-edge-devtools-extension.md)。


<!-- ====================================================================== -->
## <a name="open-source-files-in-visual-studio-code"></a>在 Visual Studio Code 中的打开源文件

**Visual Studio Code试验中的开源文件**允许你使用 Microsoft Edge DevTools，但随后在 Visual Studio Code 而不是 DevTools **源**工具的代码编辑器中编辑文件。

使用此试验时，如果使用Visual Studio Code，并且使用 DevTools 更改 CSS 规则，则不再需要在 DevTools 的源工具中使用代码编辑器。  只需在Visual Studio Code中使用代码编辑器即可。  启用此试验时，本地文件将获得不同的处理方法。<!--TODO: be specific-->

请参阅[Visual Studio Code中打开源文件](../devtools-guide-chromium/sources/opening-sources-in-vscode.md)。


<!-- ====================================================================== -->
## <a name="debug-microsoft-edge-in-visual-studio-code"></a>在 Visual Studio Code 中调试 Microsoft Edge

[Visual Studio Code](https://code.visualstudio.com)包含 Microsoft Edge 的内置调试器，可启动浏览器或附加到已运行的浏览器。

借助此内置调试器，可以逐行调试前端 JavaScript 代码，并直接从Visual Studio Code查看`console.log()`语句。

请参阅[Visual Studio Code中的“调试 Microsoft Edge](debugger-for-edge.md)”。


<!-- what to do with this section?  present page is supposed to have h2 for each child page of TOC node, where h2 contains only 1 paragraph and link to child page -->
<!-- ====================================================================== -->
## <a name="the-webhint-extension-for-visual-studio-code"></a>Visual Studio Code的 webhint 扩展
<!-- keep in sync:
[webhint extension for Visual Studio Code](../test-and-automation/webhint.md)
[The webhint extension for Visual Studio Code]() in _Visual Studio Code for web development_.
-->

使用 Webhint（一种可自定义的 Linting 工具）来改进网站的功能，包括：

*   辅助功能。
*   性能。
*   跨浏览器兼容性。
*   PWA 兼容性。
*   安全性。

webhint 检查代码是否存在最佳做法和常见错误。  识别并修复文件中的问题，包括 HTML、CSS、JavaScript 和 TypeScript。  提示在文本编辑器中显示为波浪下划线，并汇总在 **“问题** ”窗格中。

**注意：** 自 2022 年 4 月起，不再维护Visual Studio Code的 webhint 扩展。  参阅[适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](microsoft-edge-devtools-extension.md)。


<!-- ====================================================================== -->
## <a name="visual-studio-for-web-development"></a>用于 Web 开发的Visual Studio

Microsoft [Visual Studio](https://visualstudio.microsoft.com/vs) 是 IDE)  (集成开发环境。   使用它来编辑、调试、生成和发布 Web 应用。  这是一个功能丰富的程序，可用于 Web 开发的许多方面。

除了大多数 IDE 提供的标准编辑器和调试器外，Visual Studio 还包括用于简化开发过程的功能，包括：

*   编译 器。
*   代码完成工具。
*   图形设计器。
*   还有更多功能。

请参阅 [Visual Studio 进行 Web 开发](../visual-studio/index.md)。
