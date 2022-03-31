---
title: 用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展
description: 使用 Microsoft Edge 开发人员工具扩展Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/26/2021
ms.openlocfilehash: c7ddadd7d4dcd3e13192c168a146115c29370072
ms.sourcegitcommit: ccb3555dd66d7cb51b9e5647fd057fb7a65e4a09
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2022
ms.locfileid: "12463825"
---
# <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

<!-- lexicon (except when quoting a UI string):
Microsoft Edge DevTools extension for Visual Studio Code
Microsoft Edge DevTools extension
-->

使用 Microsoft Edge DevTools 扩展Visual Studio Code，你可以从 Visual Studio Code 内使用浏览器的元素工具和网络Visual Studio Code。**** ****  如果不离开Visual Studio Code，Microsoft Edge DevTools 使用以下功能连接到 Microsoft Edge 实例：
* 查看运行时 HTML 结构。
* 更改布局。
* 更改 CSS (样式) 。
* 读取控制台消息。
* 查看网络请求。

> [!NOTE]
> 开发人员Microsoft Edge开发人员工具扩展需要Microsoft Edge。  此扩展在 Microsoft Edge 80.0.361.48 及更高版本中受支持。

在Visual Studio Code中，有多种方法可以打开 Microsoft Edge DevTools 扩展：
* 从**活动栏中。**
* 来自 JavaScript 调试器。

在Visual Studio Code中，此扩展由多个变体引用：
*  **Microsoft Edge开发人员工具Visual Studio Code** - 如扩展市场详细信息中所示**的全名**。
*  **Microsoft Edge工具VS Code**扩展 - 在扩展市场中搜索时列出的**扩展**。
*  **Microsoft Edge工具** - 活动栏中的图标**工具提示**。
*  **Edge DevTools** - 选项卡名称。

本文使用名称"Microsoft Edge DevTools 扩展"，UI 文本除外。


<!-- ====================================================================== -->
## <a name="installing-the-microsoft-edge-devtools-extension"></a>安装 Microsoft Edge DevTools 扩展

若要从内部安装扩展Visual Studio Code，请参阅 Microsoft Edge Web 开发Visual Studio Code中的 Visual Studio Code [DevTools](index.md#microsoft-edge-devtools-extension-for-visual-studio-code) _扩展_。

或者，你可以[从 Microsoft Edge 应用商店下载 Visual Studio DevTools](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) 扩展。  您可以在以下[时间查看GitHub](https://github.com/microsoft/vscode-edge-devtools)。

### <a name="updating-the-extension"></a>更新扩展

Microsoft Visual Studio Code 会自动更新扩展。  若要手动更新扩展，请参阅 [手动更新扩展](https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually)。


<!-- ====================================================================== -->
## <a name="opening-microsoft-edge-devtools-within-visual-studio-code"></a>打开Microsoft Edge中的 DevTools Visual Studio Code

若要打开工具面板，请在活动**栏中**选择"工具Microsoft Edge**图标**。

使用 Microsoft Edge DevTools 扩展，可以轻松启动 Edge `launch.json` 实例或生成文件以自动执行调试工作流：

![Microsoft Edge开发人员工具Visual Studio Code扩展。](media/edge-devtools-for-vscode-extension-icon.png)

选择 **"启动实例**"将打开浏览器窗口，并打开"Edge **DevTools**"选项卡，Visual Studio Code：

![选择"启动实例"以在 Visual Studio Code 中打开浏览器。](media/edge-devtools-for-vscode-launch-instance.png)

使用 Microsoft Edge中的 DevTools 扩展Visual Studio Code检查该元素中的 HTML Microsoft Edge。 例如，单击成功 **！** 标题在浏览器中， **"元素** "工具打开，同时展开 DOM 树：

![突出显示 HTML 的元素工具。](media/edge-devtools-for-vscode-elements.png)


<!-- ====================================================================== -->
## <a name="modes-for-using-microsoft-edge-devtools-in-visual-studio-code"></a>在开发人员Microsoft Edge开发人员工具Visual Studio Code

可以在以下三种模式之一中使用此扩展：
* 启动Microsoft Edge窗口中的 Web 应用程序，然后转到 Web 应用程序。
* 附加到运行实例的 Microsoft Edge。
* 打开新实例的 Microsoft Edge 内部Visual Studio Code。

每种模式都需要从本地 Web 服务器（从任务或命令行Visual Studio Code Web 应用程序提供服务）。  使用文件内的 URL 参数`launch.json`可以Visual Studio Code打开哪个 URL。


<!-- ====================================================================== -->
## <a name="opening-a-new-browser-instance"></a>打开新的浏览器实例

若要从网站打开浏览器Visual Studio Code：

1. 在活动**栏上**，选择"**Microsoft Edge工具"**。

1. 在"**Microsoft Edge：目标"面板上**，选择"**启动实例"**。  Microsoft Edge打开，并显示包含详细信息指南的默认页面。  此外，**Edge DevTools** 选项卡和面板显示在Visual Studio Code，其中包含**欢迎**、元素**和网络**工具： ****

   ![Microsoft Edge和 DevTools 面板在 Visual Studio Code 中打开。](media/edge-devtools-for-vscode-targets-launch.png)

1. 在Microsoft Edge地址栏中，转到要调试的项目的 URL。


<!-- ====================================================================== -->
## <a name="changing-the-default-page-to-your-project-website"></a>将默认页面更改到项目网站

若要调试项目，您可能需要更改在 Visual Studio Code 中打开的默认Microsoft Edge页面。  若要将默认页面更改为项目的网站，请执行以下操作：

1. 在Visual Studio Code中，选择"**文件** > **""新建窗口"**。  请注意，没有打开的文件夹。

1. 在活动**栏上**，选择"**Microsoft Edge工具"**。

1. 在"**Microsoft Edge：目标"** 面板中，选择 **"打开文件夹"** 链接。

1. 选择具有新的默认页面的项目文件夹，以在 Visual Studio Code 中开始调试。

   第一次打开文件夹时，必须确认信任此文件夹中文件的作者。  还可以选中"信任 **父文件夹中所有文件的作者"复选框**：

   ![是否信任此文件夹的文件的作者？](media/edge-devtools-for-vscode-trust.png)

   第一次完成此过程时，还必须再次选择Microsoft Edge**工具**"。

   The **Microsoft Edge Tools： Targets** panel now displays two buttons： **Launch Instance** and **Generate launch.json**：

   !["Microsoft Edge工具： 目标"面板显示"启动实例"和"生成 launch.json"按钮。](media/edge-devtools-for-vscode-targets-buttons.png)

1. 选择 **"生成 launch.json** "以在 `launch.json` 项目中创建 。

1. 在 `launch.json`中，添加项目的 URL。 如果将 URL 留空，将显示默认页面。

1. 保存 `launch.json`。

1. 选择 **"Project**"以验证Microsoft Edge并显示您输入的 URL。  此外，DevTools 将在Visual Studio Code。


<!-- ====================================================================== -->
## <a name="changing-the-extension-settings"></a>更改扩展设置

可以在扩展中自定义 devTools Visual Studio Code。

自定义设置：

1. 在Visual Studio Code中的"活动**栏**"上，选择"Microsoft Edge**工具"**。

1. 在**Microsoft Edge工具** > **目标**"中，选择"目标 ( **** ) "右边的"其他操作"，然后选择"打开设置 **"**。****

   如果使用鼠标，若要访问"其他操作"**** (...) ，请选择"目标"窗格或将鼠标悬停在**** 该窗格上：

   !["工具Microsoft Edge目标"面板上的"更多操作"图标，用于更改 DevTools 扩展的设置。](media/edge-tools-open-settings-icon.msft.png)


### <a name="reloading-the-extension-after-changing-settings"></a>更改设置后重新加载扩展

某些设置有一条注释， ** 指出 (需要重新加载) **。  使此类设置生效：

1. 关闭扩展打开的**** > 浏览器，或在"工具Microsoft Edge**窗格中，** **** `X` 选择"关闭实例 () "。  此操作还会自动关闭 **"Edge DevTools"** 选项卡。

1. 在"**Microsoft Edge** >  **Targets"** 窗格中，选择"**启动实例"** 按钮。  Microsoft Edge，并显示 **"Edge DevTools**"选项卡。


<!-- ====================================================================== -->
## <a name="viewing-the-changelog-for-changes-made-to-the-extension"></a>查看更改日志，查看对扩展所做的更改

可以查看对扩展所做的更改。

若要查看更改日志，请进行以下设置：

1. 在Visual Studio Code中的"活动**栏**"上，选择"Microsoft Edge**工具"**。

1. 在**Microsoft Edge工具** > **目标**"中，选择"更多操作****" (...) "目标"一词的右侧，然后选择"**查看更改日志"**：****

   !["查看更改日志"菜单项，以查看对扩展所做的更改。](media/view-changelog-menuitem.msft.png)

或者，在浏览器中，转到[存储库中的更改](https://github.com/microsoft/vscode-edge-devtools/blob/main/CHANGELOG.md)`vscode-edge-devtools`日志文件。


<!-- ====================================================================== -->
## <a name="changing-to-headless-mode"></a>更改为无头模式

默认情况下，扩展启动Microsoft Edge新窗口中，这将在任务栏上显示另一个浏览器图标。

若要在代码编辑器内显示浏览器，或隐藏浏览器（如果已显示）：

1. 单击 **切换屏幕广播** 按钮：

   ![切换屏幕视频，在编辑器内查看浏览器。](media/edge-devtools-for-vscode-toggle-screencast.png)


若要仅在视频内使用屏幕Visual Studio Code：

1. 选择**设置** > **无标题模式**：

![若要仅在视频内使用屏幕Visual Studio Code，设置 >无头模式。](media/edge-devtools-for-vscode-settings-headless.png)


<!-- ====================================================================== -->
## <a name="opening-source-files-from-the-elements-tool"></a>从"元素"工具打开源文件

**Elements** 工具的一个功能是，它显示将样式和事件处理程序应用到 DOM 树中选定节点的源文件。  源文件以指向 URL 的链接的形式显示。  选择链接将在编辑器中打开Visual Studio Code文件：

![从"元素"工具打开源文件。](media/edge-devtools-for-vscode-elements-files.png)


<!-- ====================================================================== -->
## <a name="setting-up-your-project-to-show-live-changes-in-the-extension"></a>设置项目以显示扩展中的实时更改

默认情况下，Microsoft Edge开发人员工具扩展不会在编写代码时跟踪实时更改。  如果希望浏览器在您更改文件时自动刷新，请设置实时 _重新加载_ 环境，如下所示。

本示例显示硬盘驱动器上名为 的生产文件文件夹 `my-project`。  在以下步骤中，如果 `my-project` 不同，请更改为文件夹名称。

安装Node.js `reload` 和 npm 程序包，如下所示：

1. 下载并安装 [Node.js](https://www.nodejs.org)。

1. 若要安装 [重新加载 npm 包，](https://www.npmjs.com/package/reload?activeTab=readme)请打开命令提示符 `npm install reload -g` 并运行 以全局安装该包。

   接下来，将扩展附加到实时重新加载项目：

1. 导航到终端 `my-project` 窗口中的文件夹，然后运行 `reload` 以启动本地服务器。

1. 在Visual Studio Code中，打开`my-project`文件夹。

1. 转到扩展并启动Microsoft Edge浏览器实例。

1. 在Microsoft Edge中，转到 `localhost:8080/{file name you want to open}`。

保存在此文件夹中的所有更改现在将触发浏览器刷新。


<!-- ====================================================================== -->
## <a name="syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing"></a>使用 CSS 镜像编辑同步样式工具中的实时更改

DevTools Microsoft Edge样式工具非常适用于调试和调整 CSS 属性样式。  一个问题就是，虽然这些更改在浏览器中实时显示，但是它们不会反映在源文件中。  这意味着在 CSS 调试会话结束时，您需要将更改的内容复制并粘贴回源文件中。

CSS 镜像编辑是开发人员工具扩展的实验Microsoft Edge，可解决此问题。  打开镜像编辑时，在 DevTools 的样式工具中进行的任何更改也会更改工作区中的文件。

在下面的示例中，我们已在 `index.html` Visual Studio Code 中打开，Microsoft Edge DevTools 扩展处于打开状态。  When we select the flexbox icon in the `.searchbar` CSS selector and change the `flex-direction` to `column`， we only see the change in the browser and in DevTools， but Visual Studio Code also automatically navigates to the correct style sheet file and the appropriate line number， and inserts the `flex-direction: column` CSS code：

![选择样式工具中的弹性框图标以创建 CSS 更改。](media/css-mirror-editing-start.msft.png)

更改 CSS 设置在正确的 CSS 源文件中创建了一个新代码行：

![更改 CSS 设置在正确的 CSS 源文件中创建了一个新代码行。](media/css-mirror-editing-changed-file.msft.png)

可以在样式工具中编辑任何选择器或创建新选择器，所有更改都将镜像到正确的 CSS 源文件中。 扩展仅更改文件，不会自动将更改保存回硬盘驱动器。 这是一种安全措施，用于确保不会意外覆盖任何代码。

您可以启用和禁用 CSS 镜像编辑，方法是单击扩展的"目标"**** 窗格中的按钮，或者使用"命令菜单"查找 ：`mirror`

![在扩展面板中，可以找到 CSS 镜像编辑的快速说明、打开和关闭功能的按钮以及向我们提供反馈的链接。](media/css-mirror-editing-button.msft.png)

使用命令菜单打开或关闭 CSS 镜像编辑：

![使用命令菜单聚焦 CSS 镜像编辑视图，并打开或关闭 CSS 镜像编辑。](media/css-mirror-editing-command.msft.png)

我们将继续改进此功能，并针对 CSS 镜像编辑设置GitHub[跟踪](https://github.com/microsoft/vscode-edge-devtools/issues/476)问题，我们欢迎您提供反馈。


<!-- ====================================================================== -->
## <a name="device-emulation-in-the-screencast"></a>屏幕广播中的设备模拟

设备仿真是编辑器中屏幕广播浏览器的一项功能。  这允许你模拟手机或平板电脑等设备。  这可用于在不同设备上测试网站的布局：

!["Edge DevTools： Screencast"选项卡中的"设备"下拉列表。](media/edge-devtools-for-vscode-device-dropdown.msft.png)

你可以从不同设备列表中选择，以在地址栏旁边的屏幕广播中模拟：

![可以在扩展的屏幕广播中打开可模拟的设备列表。](media/edge-devtools-for-vscode-device-list.msft.png)

默认设备是台式计算机。  如果选择模拟的设备是触摸设备，屏幕视频将自动切换到触摸屏模式。 可以通过单击列表旁边的按钮来旋转模拟设备的方向：

![显示仿真文档 5 中当前文档的屏幕iPhone大小正确且具有模拟触摸界面。](media/edge-devtools-for-vscode-simulated-iphone.msft.png)


<!-- ====================================================================== -->
## <a name="inline-and-live-issue-analysis"></a>内联和实时问题分析

源代码中的问题用波浪下划线突出显示。 可以检查该问题并获取有关问题所在、如何修复以及在何处查找详细信息的详细信息。  若要检查该问题，请选择具有波浪下划线的代码：

![在代码段内报告的辅助功能问题，显示如何解决该问题以及在何处查找详细信息。](media/edge-devtools-for-vscode-inline-issue-reporting.msft.png)

若要查看文件的所有问题，请选择" **查看问题"**：

![源代码中一个突出显示的问题，其中具有一个导航栏，用于解释该问题以及要移动到下一个和之前问题的按钮。](media/edge-devtools-for-vscode-navigating-issues.msft.png)

**下面板**中的"问题"选项卡列出了在当前项目中发现的所有问题：

![项目面板下面板中的"Visual Studio Code"选项卡，其中列出了在项目文件中发现的所有问题。](media/edge-devtools-for-vscode-issues-in-lower-panel.msft.png)

编辑代码时，会实时评估问题。  键入时，将获取有关发现的任何问题以及如何修复它们的反馈：

![在输出元素上说明的可能问题。](media/edge-devtools-for-vscode-live-issue-reporting.msft.png)


<!-- ====================================================================== -->
## <a name="browser-debugging-with-microsoft-edge-devtools-integration-in-visual-studio-code"></a>使用 Microsoft Edge 中的 DevTools 集成进行浏览器Visual Studio Code

JavaScript 调试内置于Visual Studio Code。  可以在 Chrome、Microsoft Edge或 Node.js中调试，而无需安装任何其他扩展。  如果你使用 Microsoft Edge 调试，你可以从 JavaScript Microsoft Edge启动 DevTools。

1. 若要开始调试，请执行下列任一操作：
   *  按 **F5**，或在菜单栏上选择" **调试** "图标，然后选择" **运行和调试"**。
   *  打开"Visual Studio Code"命令调色板，然后选择"**调试： 打开链接"**。
    
   ![从 javaScript Microsoft Edge启动 DevTools。](media/edge-devtools-for-vscode-start-session.png)

1. 选择 **"边缘"**。  在调试工具栏上，注意" **检查"** 按钮：

   ![调试工具栏上的"检查"按钮。](media/edge-devtools-for-vscode-inspect-button.png)

1. 选择 **"检查**"以Microsoft Edge开发人员工具Visual Studio Code。

   首次选择"检查 **"** 时，编辑器会提示你安装扩展，Microsoft Edge[开发人员工具Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)。

   安装 Microsoft Edge DevTools 扩展后，当你选择"检查"时，Microsoft Edge**** 将打开以下Visual Studio Code：

   !["检查"按钮Microsoft Edge开发人员工具Visual Studio Code。](media/edge-devtools-for-vscode-tools-inside.png)

   现在，您可以检查 DOM、更改 CSS，并查看浏览器中运行的项目的网络请求，而无需离开Visual Studio Code。

   您还可以使用编辑器中的调试控制台与浏览器中的文档进行交互。  你可以完全访问 window 对象，并且可以使用 [控制台实用程序 API](/microsoft-edge/devtools-guide-chromium/console/utilities)：

   ![编辑器中的调试控制台与浏览器中打开的文档交互。](media/edge-devtools-for-vscode-debug-console.png)


### <a name="automatically-attaching-to-microsoft-edge-and-launching-devtools-in-visual-studio-code"></a>自动附加到 Microsoft Edge并启动开发人员工具Visual Studio Code

1. 如果你想要自动附加到 Microsoft Edge，Microsoft Edge Visual Studio Code 中的 DevTools`launch.json`，请执行上述步骤，然后创建一个文件，如下所示。

   选择**Microsoft Edge**类型作为调试类型。  在文件中 `launch.json` ，将 指定为 `pwa-msedge` 类型：

   ```json
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
   ```

1. 在 `http://localhost:8080` 以上代码中更改 ，并确保变量 `{workspaceFolder}` 解析。

1. 选择" **检查"** 图标。  如果尚未安装适用于 Microsoft Edge 的 DevTools Visual Studio Code，"扩展"选项卡将打开并自动显示要安装的**** 扩展。

#### <a name="see-also"></a>另请参阅

* [在调试](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)_文章中启动_配置Visual Studio Code。


<!-- ====================================================================== -->
## <a name="console-integration"></a>控制台集成

[控制台工具](/microsoft-edge/devtools-guide-chromium/console/)在扩展内可用，你可以执行在浏览器中使用 DevTools 时所使用的一切操作。 

![扩展内的 DevTools 控制台作为自己的选项卡。](media/edge-devtools-for-vscode-console-full.png)

你可以查看日志 [消息、](/microsoft-edge/devtools-guide-chromium/console-log)访问 `window` 对象并使用 [DOM 交互便利方法](/microsoft-edge/devtools-guide-chromium/console-dom-interaction)。 还可以筛选[控制台并设置](/microsoft-edge/devtools-guide-chromium/console-filters)[实时表达式](/microsoft-edge/devtools-guide-chromium/live-expressions)。 

如果在下面板中打开控制台，还可以在"元素"工具旁边使用控制台：

![扩展内的 DevTools 控制台以及元素工具。](media/edge-devtools-for-vscode-console-in-elements.png)

如果从"运行和调试"工作流启动扩展，[Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) 的调试控制台会为你提供 Visual Studio Code 内的 DevTools [控制台](/microsoft-edge/devtools-guide-chromium/console/)大部分功能，但没有筛选选项和更基本的结果显示：

![当从运行和调试工作流启动扩展时，DevTools 控制台可用。](media/edge-devtools-for-vscode-console-integration.png)


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-extension-team"></a>与开发人员工具扩展Microsoft Edge联系

通过向存储库 [提交问题](https://github.com/Microsoft/vscode-edge-devtools/issues/new) 发送 `vscode-edge-devtools` 反馈。

欢迎你做出贡献，帮助你更好地Microsoft Edge开发工具扩展。  在 [vscode-edge-devtools](https://github.com/Microsoft/vscode-edge-devtools) 存储库查找入门所需的一切。
