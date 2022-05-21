---
title: 用于 Web 开发的Visual Studio Code
description: Microsoft Edge和Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/19/2022
ms.openlocfilehash: d760b72e64c77551d539f4669b1f9e7a25eea4a4
ms.sourcegitcommit: 56d88962483dab8374f3dccb67f546df1c26ec17
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2022
ms.locfileid: "12522095"
---
# <a name="visual-studio-code-for-web-development"></a>用于 Web 开发的Visual Studio Code

Visual Studio Code包括对 JavaScript、TypeScript 和 Node.js 的内置支持，因此它是 Web 开发人员的绝佳工具。  Visual Studio Code是一个轻型但功能强大的源代码编辑器，可用于Windows、Linux 和macOS。


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

Visual Studio Code的 Microsoft Edge DevTools 扩展允许你从Visual Studio Code中使用Microsoft Edge浏览器的 **Elements** 工具和**网络**工具。

无需离开Visual Studio Code，请使用 Microsoft Edge DevTools 连接到 Microsoft Edge 实例，然后：
* 查看运行时 HTML 结构。
* 更改布局。
* 更改 CSS)  (样式。
* 读取控制台消息。
* 查看网络请求。

参阅[适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](microsoft-edge-devtools-extension.md)。


<!-- ====================================================================== -->
## <a name="open-source-files-in-visual-studio-code"></a>在 Visual Studio Code 中的打开源文件

**Visual Studio Code试验中的开源文件**允许你使用 Microsoft Edge DevTools，但随后在 Visual Studio Code 而不是 DevTools **源**工具的代码编辑器中编辑文件。

使用此试验时，如果使用Visual Studio Code，并且使用 DevTools 更改 CSS 规则，则不再需要在 DevTools 的源工具中使用代码编辑器。  只需在Visual Studio Code中使用代码编辑器即可。  启用此试验时，本地文件将获得不同的处理方法。<!--TODO: be specific-->

请参阅[Visual Studio Code中打开源文件](../devtools-guide-chromium/sources/opening-sources-in-vscode.md)。


<!-- ====================================================================== -->
## <a name="debug-microsoft-edge-in-visual-studio-code"></a>在Visual Studio Code中调试Microsoft Edge

[Visual Studio Code](https://code.visualstudio.com)包含用于Microsoft Edge的内置调试器，它可以启动浏览器或附加到已运行的浏览器。

借助此内置调试器，可以逐行调试前端 JavaScript 代码，并直接从Visual Studio Code查看`console.log()`语句。

请参阅[Visual Studio Code中的调试Microsoft Edge](debugger-for-edge.md)。


<!-- what to do with this section?  present page is supposed to have h2 for each child page of TOC node, where h2 contains only 1 paragraph and link to child page -->
<!-- ====================================================================== -->
## <a name="the-webhint-extension-for-visual-studio-code"></a>Visual Studio Code的 webhint 扩展

使用 Webhint（一种可自定义的 Linting 工具）来改进网站的功能，包括：

*   辅助功能。
*   性能。
*   跨浏览器兼容性。
*   PWA兼容性。
*   安全性。

webhint 检查代码是否存在最佳做法和常见错误。  识别并修复文件中的问题，包括 HTML、CSS、JavaScript 和 TypeScript。  提示在文本编辑器中显示为波浪下划线，并汇总在 **“问题** ”窗格中。

<!-- todo: don't have png files in this nav page.  delete png (only used here) -->
<!-- ![The webhint extension for Visual Studio Code.](media/webhint-extension.png) -->

请参阅 [Microsoft Edge Visual Studio Code 的 DevTools 扩展](microsoft-edge-devtools-extension.md)，而不是 webhint。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [下载Visual Studio Code](https://code.visualstudio.com)
*  [入门](https://code.visualstudio.com/Docs) - Visual Studio Code文档。
