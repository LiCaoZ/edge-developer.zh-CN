---
title: Visual Studio Web 开发
description: Microsoft Edge和Visual Studio Web 开发。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/27/2021
ms.openlocfilehash: b24c40986f2f799f18921bc6065fa7cfd1fbf749
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430855"
---
# <a name="visual-studio-for-web-development"></a>Visual Studio Web 开发

Microsoft [Visual Studio](https://visualstudio.microsoft.com/vs)是一个集成开发环境， (IDE) 。  使用它来编辑、调试、生成和发布 Web 应用。  Visual Studio是一个功能丰富的程序，可用于 Web 开发的许多方面。

除了大多数 IDEs 提供的标准编辑器和调试器之外，Visual Studio还包含简化开发过程的功能，包括：

*   编译器。
*   代码完成工具。
*   图形设计器。
*   以及更多功能。

如果你还没有使用 Visual Studio，请转到下载[Visual Studio](https://visualstudio.microsoft.com/downloads)下载它。

目前，Visual Studio 2019 支持在 Microsoft Edge 中为 ASP.NET Framework 和 ASP.NET Core 调试 JavaScript。 若要Visual Studio调试Microsoft Edge，请执行以下步骤。


<!-- ====================================================================== -->
## <a name="launch-microsoft-edge"></a>启动Microsoft Edge

按照本节中的步骤使用Visual Studio执行以下操作：

*  生成 ASP.NET 和 ASP.NET Core应用。
*  启动 Web 服务器。
*  启动Microsoft Edge。
*  连接单个Visual Studio调试器。

通过简化的工作流，您可以调试直接从 IDE Microsoft Edge中运行的 JavaScript。


### <a name="create-a-new-aspnet-core-web-app"></a>创建新的 web ASP.NET Core Web 应用

首先，新建 ASP.NET Core Web 应用，如下所示：

1. Open Visual Studio 2019 and select **Create a new project**.

1. 在下一屏幕的搜索框中，输入 **react**。

1. 选择 **ASP.NET Core模板React.js**，然后选择"下一步 **"**。

![使用 ASP.NET Core 新建 web React.js。](media/create-new-project.png)

此**React.js**模板指定如何将React.js与 ASP.NET Core集成。

现在，你已创建一个 web ASP.NET Core项目。


### <a name="launch-microsoft-edge-from-visual-studio"></a>从Microsoft Edge启动Visual Studio

接下来，在 ASP.NET Core中运行并Visual Studio Web 应用项目，如下所示：

1. 打开 `ClientApp/src/components/Counter.js`。

1. 选择绿色"播放"按钮旁边的**下拉列表，然后选择****IIS Express。**

   ![绿色"播放"按钮旁边的下拉列表IIS Express。](media/vs-dropdown.png)

1. 选择 **"脚本调试** > **""启用"**。

   ![在脚本调试中启用Visual Studio。](media/enable-script-debugging.png)

1. 在同一下拉列表中，>要启动**** 的 Microsoft Edge Visual Studio 预览频道（如 Microsoft Edge Canary、Dev 或 Beta）中的"Web 浏览器"。  如果你还没有使用其中一个预览Microsoft Edge，请转到下载预览Microsoft Edge[预览体验成员](https://www.microsoftedgeinsider.com/download)频道下载一个。

   ![选择要启动的Microsoft Edge预览Visual Studio频道。](media/set-web-browser.png)

1. 选择绿色" **播放"** 按钮。  Visual Studio生成应用、启动 Web 服务器、启动 Microsoft Edge，然后导航到 `https://localhost:44362/` 或 中指定的任何端口`launchSettings.json`。

   ![Microsoft Edge启动Visual Studio。](media/edge-launch.png)

继续执行以下步骤。


### <a name="debug-javascript-code-thats-running-in-microsoft-edge"></a>调试在客户端中运行的 JavaScript Microsoft Edge

1. 切换回Visual Studio设置断点。

1. 在 `Counter.js`中，通过选择第 13 行旁边的装订线设置断点。

   ![Select the gutter next to Line 13 in Counter.js to set a breakpoint in Visual Studio.](media/set-breakpoint.png)

1. 切换回已启动Microsoft Edge Visual Studio实例。

1. 在 **网页** 顶部的导航菜单中选择"计数器"，然后选择"增量 **"**。

   > [!div class="mx-imgBorder"]
   > ![我们的 Web 应用中的"ASP.NET Core页面。](media/edge-counter.png)

1.  中的 JavaScript 调试Visual Studio命中你在 中设置的断点`Counter.js`。  Visual Studio现在暂停在 Microsoft Edge 中运行的 JavaScript 的运行时，你可以逐行执行脚本。

   ![Visual Studio暂停 JavaScript 在 Microsoft Edge 中运行。](media/hit-breakpoint.png)

在以上方法中，从Microsoft Edge启动Visual Studio。  或者，你可以将Visual Studio调试器附加到Microsoft Edge运行的实例，如下所述。

该示例只是对 Visual Studio 中可用功能的一个小Visual Studio。  有关 2019 年 Visual Studio 中功能Visual Studio[文档](/visualstudio/windows/index)。


<!-- ====================================================================== -->
## <a name="attach-visual-studio-debugger-to-a-running-instance-of-microsoft-edge"></a>将Visual Studio调试器附加到正在运行的 Microsoft Edge

若要将Visual Studio调试器附加到Microsoft Edge运行的实例：

1. 请确保没有正在运行的 Microsoft Edge。

1. 从命令行运行以下命令：

   ```console
   start msedge --remote-debugging-port=9222
   ```
    
1. 在Visual Studio中，选择 **"DebugAttach** >  **to Process"或** `Ctrl``P`+`Alt`+。

   ![选择"调试>附加到进程"。Visual Studio。](media/attach-to-process.png)

1. 在" **附加到进程"** 对话框中，将 **"连接** 类型"设置为 **"Chrome devtools 协议 Websocket (，) **"。

1. 在" **连接目标** "文本框中，键入 并选择 `http://localhost:9222/` `Enter`。

1. 查看"可用进程"部分中Microsoft Edge打开的**选项卡**列表。

   ![在 Visual Studio 中配置"附加到进程"Visual Studio。](media/attach-to-process-dialog.png)

1. 从列表中选择要调试的选项卡，然后选择"附加 **"**。

1. 在"**选择代码类型**"对话框中，选择 **"JavaScript (Microsoft Edge - Chromium) **"确定 **"**。

现在Visual Studio调试器附加到Microsoft Edge。  您可以暂停 JavaScript 的运行，设置`console.log()`断点，并直接在"调试输出"窗口中查看**** Visual Studio。


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-visual-studio-team"></a>与团队联系Microsoft Visual Studio联系

Microsoft Visual Studio和Microsoft Edge团队希望了解有关如何在 JavaScript 中Visual Studio。  若要发送反馈，请选择"发送**** 反馈"图标Visual Studio或推文 [@VisualStudio and @EdgeDevTools](https://twitter.com/intent/tweet?text=@VisualStudio+@EdgeDevTools) 。

!["发送反馈"图标Visual Studio。](media/feedback-icon.png)
