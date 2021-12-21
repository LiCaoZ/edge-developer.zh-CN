---
title: Visual Studio Code 概述
description: Microsoft Edge 和 Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， vs code， visual studio code， 调试程序， webhint
ms.date: 08/24/2021
ms.openlocfilehash: 4be37420c9c47aa738761479771736d2a394b1d2
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285237"
---
# <a name="visual-studio-code-overview"></a>Visual Studio Code 概述

Visual Studio Code JavaScript、TypeScript 和 Node.js支持，因此对于 Web 开发人员来说，这是一个很好的工具。  Visual Studio Code是一款轻型但强大的源代码编辑器，可用于 Windows、Linux 和 macOS。  本文概述了为开发人员工具Visual Studio Code用户添加功能的Microsoft Edge扩展。

*  [下载Visual Studio Code](https://code.visualstudio.com)
*  [入门](https://code.visualstudio.com/Docs)- Visual Studio Code


<!-- ====================================================================== -->
## <a name="the-microsoft-edge-devtools-extension-for-visual-studio-code"></a>适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

借助**Microsoft Edge DevTools** Visual Studio Code，可以在 Visual Studio Code 内使用 Microsoft Edge**** 浏览器的 Elements Visual Studio Code。  使用"元素"工具可以：
*   附加到实例或启动 Microsoft Edge。
*   显示运行时 HTML 结构。
*   更新布局。
*   修复样式设置问题。

:::image type="complex" source="./media/microsoft-edge-tools-for-visual-studio-code.png" alt-text="适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展" lightbox="./media/microsoft-edge-tools-for-visual-studio-code.png":::
   适用于 Visual Studio Code 的 **Microsoft Edge DevTools** 扩展
:::image-end:::

若要安装 Microsoft Edge DevTools 扩展：
1. In Visual Studio Code， navigate to **Extensions** (select `Ctrl` + `Shift` + `X` on Windows/Linux or `Command` + `Shift` + `X` on macOS) .
1. 在 Marketplace 中搜索扩展**Microsoft Edge Tools for VS Code，** 选择扩展，然后选择"安装 **"。**

:::image type="complex" source="./media/vscode-edge-tools-install.png" alt-text="安装 Microsoft Edge 开发人员的 DevTools Visual Studio Code" lightbox="./media/vscode-edge-tools-install.png":::
   安装 Microsoft Edge **DevTools**扩展Visual Studio Code
:::image-end:::

### <a name="see-also"></a>另请参阅

*  [Microsoft Edge开发工具扩展 -Visual Studio Code](./microsoft-edge-devtools-extension.md) - 使用扩展。
*  [Microsoft Edge工具Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) - 有关扩展的信息，请参阅 Visual Studio Marketplace。


<!-- ====================================================================== -->
## <a name="the-webhint-extension-for-visual-studio-code"></a>webhint 扩展Visual Studio Code

使用 [Webhint（](https://webhint.io)一个可自定义的 Lint 工具）可改进网站的以下功能。

*   辅助功能
*   性能
*   跨浏览器兼容性
*   PWA兼容性
*   安全

Webhint 工具会检查代码的编码实践和常见错误。  Webhint 开放源代码项目最初由 Microsoft Edge 开发，现在是[OpenJS Foundation 的一部分](https://openjsf.org)。  Microsoft Edge团队将继续与社区中的 Web 开发人员一起为 webhint 做贡献。

通过添加[webhint](https://marketplace.visualstudio.com/items?itemName=webhint.vscode-webhint)扩展以识别并修复网站中Visual Studio Code。  提示检查 HTML、CSS、JavaScript、TypeScript 等。  提示在文本编辑器中显示为波浪下划线，并汇总在"问题 **"** 窗格中。

:::image type="complex" source="./media/webhint-extension.png" alt-text="webhint 扩展Visual Studio Code" lightbox="./media/webhint-extension.png":::
   **webhint**扩展Visual Studio Code
:::image-end:::

安装 Webhint 扩展：
1. In Visual Studio Code， navigate to **Extensions** (select `Ctrl` + `Shift` + `X` on Windows/Linux or `Command` + `Shift` + `X` on macOS) .
1. 在 Marketplace 中搜索**Webhint 扩展**，选择该扩展，然后选择"安装 **"。**

:::image type="complex" source="./media/visual-studio-code-extension-webhint.msft.png" alt-text="Webhint Visual Studio Code扩展" lightbox="./media/visual-studio-code-extension-webhint.msft.png":::
   **Webhint Visual Studio Code**扩展
:::image-end:::

### <a name="see-also"></a>另请参阅

*  [webhint extension for Visual Studio Code](./webhint.md) - 如何在 webhint Visual Studio Code。
*  [webhint](https://webhint.io)
