---
description: Microsoft Edge (Chromium) 和 Visual Studio Code
title: Visual Studio Code
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/26/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， vs code， visual studio code， 调试程序， webhint
ms.openlocfilehash: 33ad223f7991eca1b87b7cb9db9c3fd9d159b557
ms.sourcegitcommit: 8924ea959b1e246aa1a3db8730cd35227abe73dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2021
ms.locfileid: "11925206"
---
# <a name="visual-studio-code-overview"></a>Visual Studio 代码概述  

[Visual Studio Code][VisualStudioCodeDocs]是一个轻型但功能强大的源代码编辑器。  [Visual Studio Code][VisualStudioCodeDocs]适用于 Windows、Linux 和 macOS。  它包括对 JavaScript、TypeScript 和 Node.js 的内置支持，因此在自定义之前，它是 Web 开发人员的一个很好的工具。  如果尚未使用它，[请下载][VisualstudioCode]Visual Studio Code。  

## <a name="extensions"></a>Extensions  

<!--todo: We want to put something like the tiles for extensions Visual Studio Code uses on this page https://code.visualstudio.com/Docs#top-extensions but I don't think this is a markdown page.  I think it's a web page.  I couldn't find anything in https://github.com/Microsoft/vscode-docs that looks like this page. In the meantime, here's what I've come up with: -->  

若要获取下面突出显示的任何扩展，请导航到 (**** 在 Windows/Linux 上或在 Visual Studio Code 中的 `Ctrl` + `Shift` + `X` `Command` + `Shift` + `X` macOS\) 选择。  

在 Marketplace 中搜索扩展，选择扩展，然后选择"安装 **"。**  

:::image type="complex" source="./media/vscode-edge-tools-install.png" alt-text="安装 Microsoft Edge Tools for Visual Studio Code 扩展" lightbox="./media/vscode-edge-tools-install.png":::
   安装**Microsoft Edge Tools** Visual Studio Code 扩展  
:::image-end:::  

:::row:::
   :::column span="1":::
      :::image type="complex" source="./media/visual-studio-code-extension-microsoft-edge-tools-for-visual-studio-code.msft.png" alt-text="Microsoft Edge扩展Visual Studio Code Visual Studio Code工具" lightbox="./media/visual-studio-code-extension-microsoft-edge-tools-for-visual-studio-code.msft.png":::
         **Microsoft Edge工具Visual Studio Code Visual Studio Code**扩展  
      :::image-end:::  
      [Microsoft Edge工具Visual Studio Code](#microsoft-edge-tools-for-visual-studio-code)  
   :::column-end:::
   :::column span="1":::
      :::image type="complex" source="./media/visual-studio-code-extension-webhint.msft.png" alt-text="webhint Visual Studio Code扩展" lightbox="./media/visual-studio-code-extension-webhint.msft.png":::
         **webhint** Visual Studio Code扩展  
      :::image-end:::  
      [webhint](#webhint)  
   :::column-end:::
:::row-end:::  

## <a name="microsoft-edge-tools-for-visual-studio-code"></a>Microsoft Edge工具Visual Studio Code

使用[Microsoft Edge Tools for Visual Studio Code][VisualstudioMarketplaceMicrosoftEdgeToolsVisualStudioCode] Visual Studio Code 扩展，请使用 Microsoft Edge 浏览器的**** Elements Visual Studio Code。  用于以下操作。  

*   附加到实例或启动 Microsoft Edge。  
*   显示运行时 HTML 结构。  
*   更新布局。  
*   修复样式设置问题。  
    
有关详细信息，请导航到 Microsoft Edge [Tools for Visual Studio Code Visual Studio Code 扩展][VisualStudioCodeMicrosoftEdgeDevtoolsExtension]。  <!--  Choose the following image to see the extension in action.  -->  
      
:::image type="complex" source="./media/microsoft-edge-tools-for-visual-studio-code.png" alt-text="Microsoft Edge适用于Visual Studio Code Visual Studio Code扩展的工具" lightbox="./media/microsoft-edge-tools-for-visual-studio-code.png":::
   **Microsoft Edge工具Visual Studio Code Visual Studio Code**扩展  
:::image-end:::  

## <a name="webhint"></a>webhint  
      
使用 [Webhint（][WebhintMain]一个可自定义的 Lint 工具）可改进网站的以下功能。  

*   辅助功能
*   性能
*   跨浏览器兼容性
*   PWA兼容性
*   安全性

Webhint 检查代码的编码实践和常见错误。 Webhint 开放源代码项目最初由 Microsoft Edge 开发，现在是[OpenJS Foundation 的一部分][OpenjsFoundation]。  Microsoft Edge团队将继续与社区中的 Web 开发人员一起为 webhint 做贡献。  <!--  Choose the following image to see the extension in action.  -->  
      
:::image type="complex" source="./media/webhint-extension.png" alt-text="Webhint 扩展Visual Studio Code屏幕截图" lightbox="./media/webhint-extension.png":::
   **Webhint 扩展Visual Studio Code**屏幕截图  
:::image-end:::  
      
通过添加[webhint][VisualstudioMarketplaceWebhint]扩展以识别并修复网站中Visual Studio Code。  提示检查 HTML、CSS、JavaScript、TypeScript 等。  提示在文本编辑器中显示为波浪下划线，并汇总在"问题 **"** 窗格中。  
      
有关详细信息，请导航到如何在[webhint][VisualStudioCodeWebhint]Visual Studio Code 。  

<!--links -->  
 
[VisualStudioCodeMicrosoftEdgeDevtoolsExtension]: ./microsoft-edge-devtools-extension.md "Microsoft Edge用于开发人员扩展Visual Studio Code的 devTools |Microsoft Docs"  
[VisualStudioCodeWebhint]: ./webhint.md "Webhint Visual Studio Code Extension |Microsoft Docs"  

[VisualstudioCode]: https://code.visualstudio.com "Visual Studio Code"  
[VisualStudioCodeDocs]: https://code.visualstudio.com/Docs "文档|Visual Studio Code"   

[VisualstudioMarketplaceDebuggerMicrosoftEdge]: https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-edge "调试程序Microsoft Edge |Visual StudioMarketplace"  
[VisualstudioMarketplaceMicrosoftEdgeToolsVisualStudioCode]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Tools for Visual Studio Code | Visual Studio Marketplace"  

[VisualstudioMarketplaceWebhint]: https://marketplace.visualstudio.com/items?itemName=webhint.vscode-webhint "webhint |Visual StudioMarketplace"  

[WebhintMain]:  https://webhint.io "webhint"  
[OpenjsFoundation]:  https://openjsf.org "OpenJS Foundation"  
