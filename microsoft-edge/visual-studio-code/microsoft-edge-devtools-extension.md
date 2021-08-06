---
description: 如何使用 Microsoft Edge 开发人员工具Visual Studio Code扩展
title: Microsoft Edge开发人员工具Visual Studio Code扩展
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/30/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， vs code， visual studio code， Microsoft Edge 开发人员工具， Microsoft Edge 开发人员工具扩展
ms.openlocfilehash: 223e13ab943e6c9344c8d72bd08115d93c13254ad70fed07f7b09bf8286e1485
ms.sourcegitcommit: 841e41de1a32501ece862399fa56170c022127c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2021
ms.locfileid: "11805853"
---
# <a name="microsoft-edge-developer-tools-for-visual-studio-code-extension"></a>Microsoft Edge开发人员工具Visual Studio Code扩展  

the Microsoft Edge Developer Tools for Visual Studio Code extension allows you to use the browser's Elements and Network tool from within the editor. 如果不离开Visual Studio Code，Microsoft Edge开发人员工具 (DevTools) 使用以下功能连接到 Microsoft Edge 实例。
* 查看运行时 HTML 结构。
* 更改布局。
* 更改 CSS (样式) 。
* 读取控制台消息。
* 查看网络请求。 

> [!NOTE]
> 此扩展仅适用于 Microsoft Edge (80.0.361.48 及更高版本) 。

有两种方法可以打开Microsoft Edge工具。
* 从活动栏中Visual Studio Code。
* 来自 Visual Studio Code 中的 JavaScript 调试Visual Studio Code。

本文介绍 Microsoft Edge 开发人员工具Visual Studio Code扩展。 [下载扩展][downloadExtension]和[检查源代码][checkSourceCode]。

## <a name="opening-microsoft-edge-developer-tools-with-visual-studio-code"></a>打开Microsoft Edge开发人员工具Visual Studio Code  

若要打开工具面板，请从活动Microsoft Edge选择"工具"图标。

借助Microsoft Edge开发人员工具Visual Studio Code扩展，可以启动 Edge 实例或生成文件以自动 `launch.json` 执行调试工作流。 

:::image type="complex" source="./media/edge-devtools-for-vscode-extension-icon.png" alt-text="Microsoft Edge用于开发人员扩展Visual Studio Code工具" lightbox="./media/edge-devtools-for-vscode-extension-icon.png":::
   Microsoft Edge用于开发人员扩展Visual Studio Code工具  
:::image-end:::

选择 **"启动实例**"将在浏览器中打开浏览器窗口和Visual Studio Code。   

:::image type="complex" source="./media/edge-devtools-for-vscode-launch-instance.png" alt-text="选择"启动实例"以在浏览器中打开Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-launch-instance.png":::
   选择"启动实例"以在浏览器中打开Visual Studio Code  
:::image-end:::

使用中开发人员工具扩展VS Code中检查 HTML 元素Microsoft Edge。 例如，选择成功 **！** 在浏览器中，注意"元素"工具将打开，并突出显示 HTML。 

:::image type="complex" source="./media/edge-devtools-for-vscode-elements.png" alt-text="元素工具打开，突出显示 HTML" lightbox="./media/edge-devtools-for-vscode-elements.png":::
   元素工具打开，突出显示 HTML  
:::image-end:::

## <a name="using-microsoft-edge-developer-tools-in-visual-studio-code"></a>在Microsoft Edge开发人员工具Visual Studio Code  

可以在以下三种模式之一中使用此扩展：
* 在Microsoft Edge中启动 Web 应用程序，然后导航到 Web 应用程序。
* 附加到运行实例的 Microsoft Edge。
* 打开新实例的 Microsoft Edge 内部Visual Studio Code。 

每种模式都要求您从本地 Web 服务器（从任务或命令行Visual Studio Code Web 应用程序提供服务）。 使用文件内的 URL `launch.json` 参数告知用户Visual Studio Code打开哪个 URL。

### <a name="open-a-new-browser-instance"></a>打开新的浏览器实例

完成以下步骤以从浏览器Visual Studio Code。 

1. 在"活动栏"上 **，Microsoft Edge"** 工具"以打开"Microsoft Edge工具： 目标"面板。

1. 在"Microsoft Edge："目标"面板上，选择"**启动实例"。** Microsoft Edge显示默认页面，并显示详细信息指南。 此外，DevTools 面板将在 Visual Studio Code。
  
    :::image type="complex" source="./media/edge-devtools-for-vscode-targets-launch.png" alt-text="Microsoft Edge中打开开发人员面板Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-targets-launch.png":::
       Microsoft Edge中打开开发人员面板Visual Studio Code :::image-end:::

1. 在Microsoft Edge地址栏中，导航到要调试的项目的 URL。

### <a name="change-the-default-page-to-your-project-website"></a>将默认页面更改为项目网站
若要调试项目，您可能需要更改在 Microsoft Edge 中打开的默认Visual Studio Code。 若要将默认页面更改为项目的网站，请完成以下步骤。 
1. In Visual Studio Code， choose **File**  >  **New Window**. 请注意，没有打开的文件夹。 
1. 在活动栏上，选择 **"Microsoft Edge开发人员工具"。**
1. 在"Microsoft Edge：目标"面板中，选择 **"打开文件夹"** 链接。 
1. 选择具有新的默认页面的项目文件夹，以在 Visual Studio Code 中开始调试。

    第一次打开文件夹时，必须确认信任此文件夹中文件的作者。 还可以选中"信任父文件夹中所有文件的作者"复选框。

    :::image type="complex" source="./media/edge-devtools-for-vscode-trust.png" alt-text="是否信任此文件夹的文件的作者？" lightbox="./media/edge-devtools-for-vscode-trust.png":::
       是否信任此文件夹的文件的作者？  
    :::image-end:::

    第一次完成此过程时，还必须再次Microsoft Edge**开发人员工具**"。

    The Microsoft Edge Tools： Targets panel now displays two buttons： **Launch Instance** and Generate **launch.json**.

    :::image type="complex" source="./media/edge-devtools-for-vscode-targets-buttons.png" alt-text="Microsoft Edge工具：目标面板显示"启动实例"和launch.js按钮上的"生成实例"" lightbox="./media/edge-devtools-for-vscode-targets-buttons.png":::
       Microsoft Edge工具：目标面板显示"启动实例"和launch.js按钮上的"生成实例"  
    :::image-end:::

1. 选择 **"launch.js"** 以在 `launch.json` 项目中创建 。
1. 在 `launch.json` 中，添加项目的 URL。 如果将 URL 留空，将显示默认页面。 
1. 保存 `launch.json`。
1. Choose **Launch Project** to verify that Microsoft Edge opens and displays the URL you entered. 此外，DevTools 将在Visual Studio Code。

## <a name="change-the-extension-settings"></a>更改扩展设置

在版本 1.1.6 或更高版本中，你可以自定义 Visual Studio Code 扩展中的 DevTools。 若要自定义设置，在"工具Microsoft Edge目标"面板中，选择 **"..."，** 然后选择"打开**设置"。**

还可以查看对扩展所做的更改。 若要查看更改日志，在"Microsoft Edge工具： 目标"面板中，选择 **"..."，** 然后选择"查看**更改日志"。**

### <a name="change-to-headless-mode"></a>更改为无头模式

默认情况下，扩展启动Microsoft Edge新窗口中，这将在任务栏上显示另一个浏览器图标。

选择 **"切换屏幕视频** "在编辑器内显示浏览器，或隐藏浏览器（如果已显示）。 

:::image type="complex" source="./media/edge-devtools-for-vscode-toggle-screencast.png" alt-text="切换屏幕视频以在编辑器内查看浏览器" lightbox="./media/edge-devtools-for-vscode-toggle-screencast.png":::
   切换屏幕视频以在编辑器内查看浏览器
:::image-end:::

还可以选择无**设置**  >  **模式**，以仅使用屏幕视频Visual Studio Code。

:::image type="complex" source="./media/edge-devtools-for-vscode-settings-headless.png" alt-text="Choose 设置 > Headless to use only the screencast browser inside Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-settings-headless.png":::
   Choose 设置 > Headless to use only the screencast browser inside Visual Studio Code  
:::image-end:::

## <a name="opening-source-files-from-the-elements-tool"></a>从"元素"工具打开源文件
Elements 工具的一个功能是，它显示将样式和事件处理程序应用到 DOM 树中选定节点的源文件。 源文件以指向 URL 的链接的形式显示。 选择链接将在编辑器中打开Visual Studio Code文件。

:::image type="complex" source="./media/edge-devtools-for-vscode-elements-files.png" alt-text=""元素"工具中的开放源文件" lightbox="./media/edge-devtools-for-vscode-elements-files.png":::
   "元素"工具中的开放源文件  
:::image-end:::

## <a name="setting-up-your-project-to-show-live-changes-in-the-extension"></a>设置项目以显示扩展中的实时更改
默认情况下，扩展不会在编写代码时跟踪实时更改。 如果希望浏览器在您更改文件时自动刷新，请设置实时重新加载环境。 这需要您Node.js [Node.js][NodeJS] 和 [NPM][NPM]。
以下示例显示硬盘驱动器上名为 的生产文件文件夹 `my-project` 。 根据需要更改您的环境的文件名和位置。

1. 安装Node.js重新加载 NPM 包。
    1. 下载并安装 [Node.js][NodeJS]。
    1. 若要安装 [reload NPM package][NPM]，请打开命令提示符并运行 以 `npm install reload -g` 全局安装该包。
1. 将扩展附加到实时重新加载项目。
    1. 导航到 `my-project` 终端窗口中的文件夹，然后运行 `reload` 以启动本地服务器。
    1. 在Visual Studio Code中，打开 `my-project` 文件夹。
    1. 转到扩展并启动Microsoft Edge浏览器实例。
    1. 在Microsoft Edge中，将扩展导航到 `localhost:8080/{file name you want to open}` 。
    1. 保存在此文件夹中的所有更改现在将触发浏览器刷新。

## <a name="browser-debugging-with-microsoft-edge-developer-tools-integration-in-visual-studio-code"></a>浏览器调试Microsoft Edge开发人员工具集成在 Visual Studio Code
JavaScript 调试现已内置到 Visual Studio Code。 从版本 1.5.7 Visual Studio Code，无需安装任何其他扩展，即可在 Chrome、Microsoft Edge 或 Node.js 中调试。 如果使用 Microsoft Edge 调试，Microsoft Edge JavaScript 调试器启动开发人员工具。
1. 若要启动会话，请使用以下任一方法：
    * 选择**F5，** 或在菜单栏上选择"**调试**"图标，然后选择"**运行和调试"。**
    * 打开"Visual Studio Code"命令调色板，然后选择"**调试： 打开链接"。**

    :::image type="complex" source="./media/edge-devtools-for-vscode-start-session.png" alt-text="启动Microsoft Edge JavaScript 调试器安装开发人员工具" lightbox="./media/edge-devtools-for-vscode-start-session.png":::
       启动Microsoft Edge JavaScript 调试器安装开发人员工具  
    :::image-end:::

1. 选择"**边缘"。**
    在调试工具栏上，注意新的"检查"按钮 

    :::image type="complex" source="./media/edge-devtools-for-vscode-inspect-button.png" alt-text="调试工具栏上现在显示的"检查"按钮" lightbox="./media/edge-devtools-for-vscode-inspect-button.png":::
       调试工具栏上现在显示的"检查"按钮 :::image-end:::

1. 选择 **"检查**"以Microsoft Edge开发人员工具Visual Studio Code。
    首次选择"检查 **"** 时，编辑器会提示你安装 [Microsoft Edge Developer Tools for Visual Studio Code][ https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools ]。

    安装完成后，当您选择"检查"**时，它将**Microsoft Edge开发人员工具Visual Studio Code。

    :::image type="complex" source="./media/edge-devtools-for-vscode-tools-inside.png" alt-text=""检查"按钮Microsoft Edge开发人员工具Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-tools-inside.png":::
       "检查"按钮Microsoft Edge开发人员工具Visual Studio Code :::image-end:::

    现在，你可以检查 DOM、更改 CSS，并查看在浏览器中运行的项目的网络请求，而无需离开Visual Studio Code。
    
    您还可以使用编辑器中的调试控制台与浏览器中的文档进行交互。 你可以完全访问窗口对象，并且可以使用 [控制台实用程序 API][ConsoleUtilitiesAPI]。

    :::image type="complex" source="./media/edge-devtools-for-vscode-debug-console.png" alt-text="编辑器中的调试控制台与浏览器中打开的文档交互" lightbox="./media/edge-devtools-for-vscode-debug-console.png":::
       编辑器中的调试控制台与浏览器中打开的文档交互  
    :::image-end:::

1. 若要自动附加到Microsoft Edge中启动开发人员Visual Studio Code，请创建 `launch.json` 一个文件。 有关详细信息，请导航到[启动配置|在 Visual Studio Code][launchJSON] 中调试。

    如果复制以下代码，请务必更改 并确保 `http://localhost:8080` 变量 `{workspaceFolder}` 解析。 如果尚未安装此扩展，选择图标将打开"VS Code扩展"选项卡，并自动显示要安装的扩展。

    若要使用此选项，请选择"Microsoft Edge"作为调试类型。 在 `launch.json` 文件中，将 `pwa-msedge` 指定为 类型：

    ```JSON
    {
        "version": "0.2.0",
        "configurations": [
            {
                "type": "pwa-msedge",
                "request": "launch",
                "name": "Launch Edge",
                "url": "http://localhost:8080",
                "webRoot": "${workspaceFolder}"
            }
        ]
    }
    
## Console integration
If you launch the extension from the Run and Debug workflow, the [Debug Console of Visual Studio Code][DebugConsoleVSCode] gives you all the functions of the [Microsoft Edge Developer Tools Console][EdgeDevToolsConsole]. You have direct access to the Window object of the instance of Edge and can use all the [Console Utilities][ConsoleUtilities].

:::image type="complex" source="./media/edge-devtools-for-vscode-console-integration.png" alt-text="Microsoft Edge Developer Tools Console available when extension launched from Run and Debug workflow" lightbox="./media/edge-devtools-for-vscode-console-integration.png":::
   Microsoft Edge Developer Tools Console available when extension launched from Run and Debug workflow  
:::image-end:::

## Getting in touch with the Microsoft Edge DevTools for Visual Studio Code extension team  

Send your feedback by [filing an issue][GithubMicrosoftVscodeEdgeDevtoolsNewIssue] on the [microsoft/vscode-edge-devtools GitHub repo][GithubMicrosoftVscodeEdgeDevtools] of the extension.  

If you want to help make <!--the Microsoft Edge DevTools for Visual Studio Code -->this extension better, your contributions are welcome.  Find everything you need to get started in the [microsoft/vscode-edge-devtools GitHub repo][GithubMicrosoftVscodeEdgeDevtools] of the extension. 

<!--links -->  

[VisualstudioCode]: https://code.visualstudio.com "Visual Studio Code"  
[VisualStudioCodeDocs]: https://code.visualstudio.com/Docs "Documentation | Visual Studio Code"   

[GithubMicrosoftVscodeEdgeDevtools]: https://github.com/Microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | GitHub"  
[GithubMicrosoftVscodeEdgeDevtoolsNewIssue]: https://github.com/Microsoft/vscode-edge-devtools/issues/new "New Issue - microsoft/vscode-edge-devtools | GitHub"

[VisualstudioMarketplaceElementsMicrosoftEdgeChromium]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Tools for Visual Studio Code"  

[ConsoleUtilitiesAPI]: /microsoft-edge/devtools-guide-chromium/console/utilities "Console Utilities API reference | Microsoft Docs"

[downloadExtension]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Tools for VS Code | Visual Studio Marketplace"

[checkSourceCode]: https://github.com/microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | github"

[launchJSON]: https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations "Launch Configurations | Debugging in Visual Studio Code"

[DebugConsoleVSCode]: https://code.visualstudio.com/Docs/editor/debugging "Debugging in Visual Studio Code"

[EdgeDevToolsConsole]: /microsoft-edge/devtools-guide-chromium/console/ "Use the Console | Microsoft Docs"

[ConsoleUtilities]: /microsoft-edge/devtools-guide-chromium/console/utilities "Console Utilities API reference | Microsoft Docs"

[NodeJS]: https://www.nodejs.org "Node.js"

[NPM]: https://www.npmjs.com/package/reload?activeTab=readme "reload - npm"
