---
title: Visual Studio Web 开发
description: Microsoft Edge和Visual Studio Web 开发。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/27/2021
ms.openlocfilehash: 5f5f095c71f2bcb607d838e2f445e239605f5a0c
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12324627"
---
# <a name="visual-studio-for-web-development"></a>Visual Studio Web 开发

Microsoft [Visual Studio](https://visualstudio.microsoft.com/vs)是一个集成开发环境， (IDE) 。   使用它来编辑、调试、生成和发布 Web 应用。  它是一个功能丰富的程序，可用于 Web 开发的许多方面。  在大多数 IDEs 提供的标准编辑器和调试器之上，Visual Studio以下功能以便于开发过程。

*   编译器
*   代码完成工具
*   图形设计器
*   更多

如果您尚未使用 Visual Studio，请导航到"[下载Visual Studio](https://visualstudio.microsoft.com/downloads)下载它。

目前，Visual Studio 2019 支持在 Microsoft Edge 中调试 ASP.NET Framework 和 ASP.NET Core JavaScript。  完成以下步骤以使用Visual Studio调试Microsoft Edge。


<!-- ====================================================================== -->
## <a name="launch-microsoft-edge"></a>启动Microsoft Edge

Visual Studio生成 ASP.NET 和 ASP.NET Core 应用、启动 Web 服务器、启动 Microsoft Edge，以及使用单个Visual Studio连接 Visual Studio 调试器。

通过简化的工作流，您可以调试直接从 IDE Microsoft Edge中运行的 JavaScript。

### <a name="create-a-new-aspnet-core-web-app"></a>创建新的 web ASP.NET Core Web 应用

1.  Open Visual Studio 2019 and select **Create a new project**.

1.  在下一屏幕的搜索框中，输入 **react**。

1.  从**ASP.NET Core中选择React.js**模板"，然后选择"下一**步"。**

:::image type="complex" source="./media/create-new-project.png" alt-text="使用 ASP.NET Core 新建 web React.js。" lightbox="./media/create-new-project.png":::
   使用 ASP.NET Core 新建 web React.js
:::image-end:::

此**React.js**模板指定如何将React.js与 ASP.NET Core集成。

### <a name="launch-microsoft-edge-from-visual-studio"></a>从Microsoft Edge启动Visual Studio

创建项目后，使用Visual Studio调试 JavaScript。

1.  打开 `ClientApp/src/components/Counter.js`。

1.  选择绿色"播放"按钮旁边的下拉列表 **，然后选择****IIS Express"**。

    :::image type="complex" source="./media/vs-dropdown.png" alt-text="绿色&quot;播放&quot;按钮旁边的下拉列表IIS Express。" lightbox="./media/vs-dropdown.png":::
       绿色"播放"按钮**旁边的下拉列表IIS Express** ****
    :::image-end:::

1.  选择 **"启用脚本调试**  >  **"。**

    :::image type="complex" source="./media/enable-script-debugging.png" alt-text="在脚本调试中启用Visual Studio。" lightbox="./media/enable-script-debugging.png":::
       在脚本调试中Visual Studio
    :::image-end:::

1.  在同一下拉列表中，>希望 Visual Studio启动的 Microsoft Edge 预览频道（如 Microsoft Edge Canary、Dev 或 Beta）中的 **"Web**浏览器"。  如果你尚未使用其中一个预览Microsoft Edge，请导航到"Microsoft Edge[预览体验成员频道"](https://www.microsoftedgeinsider.com/download)下载一个。

    :::image type="complex" source="./media/set-web-browser.png" alt-text="选择要启动Microsoft Edge的预览Visual Studio频道。" lightbox="./media/set-web-browser.png":::
       选择要启动Microsoft Edge的预览Visual Studio频道
    :::image-end:::

1.  选择绿色" **播放"** 按钮。  Visual Studio生成应用、启动 Web 服务器、启动 Microsoft Edge，然后导航到 或 中 `https://localhost:44362/` 指定的任何端口 `launchSettings.json` 。

    :::image type="complex" source="./media/edge-launch.png" alt-text="Microsoft Edge启动Visual Studio。" lightbox="./media/edge-launch.png":::
       Microsoft Edge启动Visual Studio
    :::image-end:::

### <a name="debug-javascript-running-in-microsoft-edge"></a>调试在客户端中运行的 JavaScript Microsoft Edge

切换回Visual Studio设置断点。

1.  在 `Counter.js` 中，通过选择第 13 行旁边的装订线设置断点。

    :::image type="complex" source="./media/set-breakpoint.png" alt-text="Select the gutter next to Line 13 in Counter.js to set a breakpoint in Visual Studio." lightbox="./media/set-breakpoint.png":::
       选择"第 13 行"旁边的装订线， `Counter.js` 以在 Visual Studio
    :::image-end:::

1.  切换回已启动Microsoft Edge Visual Studio的实例。

1.  在**网页**顶部的导航菜单中选择"计数器"，然后选择"增量 **"。**

    :::image type="complex" source="./media/edge-counter.png" alt-text="我们的 Web 应用中的&quot;计数器 ASP.NET Core页。" lightbox="./media/edge-counter.png":::
       ASP.NET Core Web 应用中的"计数器"页
    :::image-end:::

1.  中 JavaScript 调试Visual Studio命中你在 中设置的断点 `Counter.js` 。  Visual Studio现在暂停在 Microsoft Edge 中运行的 JavaScript 的运行时，你可以逐行执行脚本。

    :::image type="complex" source="./media/hit-breakpoint.png" alt-text="Visual Studio暂停 JavaScript 在 Microsoft Edge 中运行。" lightbox="./media/hit-breakpoint.png":::
       Visual Studio暂停 JavaScript 在 Microsoft Edge
    :::image-end:::

该示例只是对 Visual Studio 中可用功能的一个Visual Studio。  有关 Visual Studio 2019 中功能Visual Studio[文档](/visualstudio/windows/index)。


<!-- ====================================================================== -->
## <a name="attach-to-microsoft-edge"></a>附加到Microsoft Edge

以前，你从Microsoft Edge启动Visual Studio。  或者，你可以将Visual Studio附加到一个Microsoft Edge实例，如下所示。

1.  首先，确保没有正在运行的 Microsoft Edge。

1.  从命令行运行以下命令。

    ```console
    start msedge --remote-debugging-port=9222
    ```

1.  在Visual Studio中，选择"**调试**  >  **附加到进程"或** `Ctrl` + `Alt` + `P` 。

    :::image type="complex" source="./media/attach-to-process.png" alt-text="选择&quot;附加到进程&quot;Visual Studio。" lightbox="./media/attach-to-process.png":::
       选择 **"附加到进程"Visual Studio**
    :::image-end:::

1.  在"**附加到进程"** 对话框中，将 **"连接**类型"设置为 **"Chrome devtools 协议 websocket (，) "。 **

1.  在" **连接目标** "文本框中，键入 `http://localhost:9222/` 并选择 `Enter` 。

1.  查看"可用进程"部分中Microsoft Edge打开的**选项卡**列表。

    :::image type="complex" source="./media/attach-to-process-dialog.png" alt-text="配置&quot;附加到进程&quot;对话框Visual Studio。" lightbox="./media/attach-to-process-dialog.png":::
       配置"**附加到进程"** 对话框Visual Studio
    :::image-end:::

1.  从列表中选择要调试的选项卡，然后选择"附加 **"。**

1.  在"**选择代码类型**"对话框中，选择 **"JavaScript (Microsoft Edge - Chromium) "，然后选择**"确定 **"。**

现在Visual Studio调试器附加到Microsoft Edge。  您可以暂停 JavaScript 的运行，直接在 Visual Studio 的"调试 `console.log()` **输出**"窗口中设置断点和查看Visual Studio。


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-visual-studio-team"></a>与团队联系Microsoft Visual Studio联系

Microsoft Visual Studio和Microsoft Edge团队希望了解有关如何在 JavaScript 中Visual Studio。  若要发送反馈，请选择"发送**** 反馈"图标Visual Studio或推文 @VisualStudio and @EdgeDevTools](https://twitter.com/intent/tweet?text= [@VisualStudio+@EdgeDevTools) 。

:::image type="content" source="./media/feedback-icon.png" alt-text="&quot;发送反馈&quot;图标Visual Studio。" lightbox="./media/feedback-icon.png":::
