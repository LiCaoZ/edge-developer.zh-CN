---
title: 与Visual Studio Code调试集成
description: 将扩展与 Microsoft Edge 开发人员工具扩展中用于Visual Studio Code的Visual Studio Code调试工作流配合使用。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 641d5c1f9be53177c73858d03d25476e217db6d9
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816090"
---
# <a name="integration-with-visual-studio-code-debugging"></a>与Visual Studio Code调试集成

若要使用 DevTools UI 在调试模式下Visual Studio Code打开 DevTools，请右键单击`.html`文件或单击 **“启动项目”** 按钮，如[打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)中所述。  如果通过单击 **Microsoft Edge** 工具侧栏中的 **“生成 launch.json**”按钮来定义与 **DevTools** 兼容`launch.json`的文件，还可以使用 Visual Studio Code UI 启动调试器，例如`F5`，打开 DevTools 选项卡。

![从资源管理器中右键单击.html文件打开的选项卡](./debugging-a-webpage-images/tabs-from-right-click-html-explorer.png)

在调试模式下Visual Studio Code打开 DevTools 时，将打开以下 UI 组件：
*  “ **Edge DevTools”** 选项卡。
*  **Edge DevTools：“浏览器”** 选项卡。
*  调试工具栏。
*  **运行** (调试器) 侧栏，包括 **“监视”** 窗格。
*  窗口底部的 **调试控制台** 。

另请参阅步骤 6：使用 _DevTools 扩展开始使用 Visual Studio Code_ 的[调试器中的 JavaScript 代码](./get-started.md#step-6-step-through-javascript-code-in-the-debugger)。


<!-- ====================================================================== -->
## <a name="ways-to-start-the-debugger-along-with-the-devtools-tabs"></a>使用 DevTools 选项卡启动调试器的方法

其中大多数方法都需要一个 DevTools 生成 `launch.json` 的文件，其中包含你的 URL。


#### <a name="devtools-ui-features-to-open-devtools-in-debug-mode"></a>在调试模式下打开 DevTools 的 DevTools UI 功能

*  右键单击`.html`“使用**Edge 打开****资源管理器** > ”中的文件。  此方法基本上使用文件路径而不是 URL，并且不需要生成 `launch.json` 文件。

*  活动栏> **Microsoft Edge Tools** >单击 **“启动项目”** 按钮。


#### <a name="visual-studio-code-ui-features-to-open-devtools-in-debug-mode"></a>Visual Studio Code UI 功能以在调试模式下打开 DevTools

*  按 `F5`。

*  在活动栏上，单击“ **运行和调试** ”图标 (![“运行和调试”按钮](./debugging-a-webpage-images/run-and-debug-icon.png)) ，然后在 **“运行和调试** 侧栏”中，单击 **“运行和调试** ”按钮。

*  打开Visual Studio Code命令面板，开始键入调**试**字词，**>** 然后选择 **“调试：打开链接**”。  请参阅 _VS Code 中浏览器调试中的_[“打开链接”命令](https://code.visualstudio.com/docs/nodejs/browser-debugging#_open-link-command)。


<!-- ====================================================================== -->
## <a name="opening-the-browser-as-part-of-a-debugging-session"></a>在调试会话中打开浏览器

可以打开 **“Edge DevTools：浏览器** ”选项卡 (嵌入的 DevTools 浏览器) 调试会话的一部分。  DevTools 扩展在Visual Studio Code中将新浏览器作为嵌入式浏览器打开。  此 **Devtools：浏览器** 选项卡可在编辑器中的任意位置移动。  可以与源代码并行使用此选项卡，或拆分窗格，并在代码下方提供浏览器预览：

![扩展在Visual Studio Code显示源代码下方的浏览器预览和右侧的 DevTools](./debugging-a-webpage-images/browser-split-down.png)

可以将 DevTools 扩展与通常的Visual Studio Code调试 UI/工作流一起使用，如下所示。  在此方法中，若要进入调试模式，我们不使用 DevTools UI;我们不会右键单击 `.html` 文件以选择 **“使用 Edge 打开**”，并且不会单击“活动栏> **Microsoft Edge 工具** > **启动项目** ”按钮。

JavaScript 调试内置为Visual Studio Code;可以在 Chrome、Microsoft Edge 或 Node.js 中进行调试，而无需安装扩展。  如果通过将 Microsoft Edge 选项与Visual Studio Code调试功能和 UI 配合使用进行调试，则可以从 JavaScript 调试器启动 Microsoft Edge DevTools。  如果未安装 DevTools 扩展，系统会提示你选择性地安装它。

DevTools 扩展提供其他功能，例如具有设备仿真工具栏的嵌入式 DevTools 浏览器，并提供在Visual Studio Code中进入调试模式的其他方法。

若要与 DevTools 一起启动Visual Studio Code调试器，请使用Visual Studio Code的常用 UI：

1. 打开新的Visual Studio Code窗口。  工作区) 未打开 (文件夹， **并且 DevTools** 选项卡未打开。

1. 打开工作区)  (文件夹。  例如，选择 **“最近****打开** > `C:\Users\myusername\Documents\GitHub\Demos\demo-to-do`的文件 > ”。  **“DevTools**”选项卡未打开。

1. 打开文件 `.html` 。

1. `.html`单击编辑器中的文件，然后执行以下任一 UI 操作，以通常的方式启动Visual Studio Code调试器：

   *  按 **F5**。

   *  在活动栏上，单击“ **运行和调试** ”图标 (![“运行和调试”图标](./debugging-a-webpage-images/run-and-debug-icon.png)) ，然后在 **“运行和调试** 侧栏”中单击 **“运行和调试** ”按钮，如下所示。

   *  打开Visual Studio Code命令面板，开始键入“**调试**”一词，然后选择 **“调试：打开链接**”。
    
   ![从 JavaScript 调试器启动 Microsoft Edge DevTools](./debugging-a-webpage-images/start-session.png)

   **Microsoft Edge Tools** 不会显示在上面的屏幕截图中，因为对于此屏幕截图，DevTools 已卸载。

1. 选择 **Web 应用 (Edge) **。

1. 在“调试”工具栏上，单击“ **检查** ”按钮，该按钮具有 **打开浏览器 DevTools** 的工具提示：

   ![调试工具栏上的“检查”按钮](./debugging-a-webpage-images/inspect-button.png)

   首次单击“调试”工具栏上的“ **检查** ”按钮时，“ **扩展：市场** 端栏”将打开，其中包含 **适用于 VS Code 的 Microsoft Edge 工具**：

   ![从“检查”图标安装 DevTools](./debugging-a-webpage-images/install-extension-from-inspect-icon-tooltip.png)

1. 单击 **用于 VS Code** > **安装**的 Microsoft Edge 工具。

1. 关闭每个 [关闭 DevTools 的 DevTools](./open-devtools-and-embedded-browser.md#closing-devtools)。

1. 打开文件夹和 `.html` 文件。

   **生成面向 DevTools 的 launch.json：**

   假设打开的文件夹不包含 `.vscode` 已包含 `launch.json` 文件的文件夹：

1. 选择活动栏> **Microsoft Edge Tools** >单击 **“生成 launch.json** ”按钮，然后按下 `F5`。  或者，请参阅 [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。

   安装 DevTools 扩展后，打开`.html`文件，然后单击调试工具栏上的 **“检查**”按钮时，**Edge DevTools** 选项卡会在Visual Studio Code中打开：

   ![“检查”按钮将在Visual Studio Code中打开 Microsoft Edge DevTools](./debugging-a-webpage-images/tools-inside.png)

   在上面的屏幕截图中，文件夹中有一个`launch.json`资源**管理器**中`.vscode`的文件，在窗口底部有一个来自该文件的字符串，**即启动 Edge 无头和附加 DevTools**，因为 DevTools 是由使用 DevTools 生成`launch.json`的文件等`F5`Visual Studio Code功能打开的。

1. 如果需要，请在 **Edge DevTools** 选项卡左上角单击 **“切换屏幕广播** ”按钮：

   ![单击“切换屏幕广播”按钮打开“DevTools 浏览器”选项卡](./debugging-a-webpage-images/toggle-screencast-after-install.png)

   “ **Edge DevTools：浏览器”** 选项卡随即打开。

   在上面的屏幕截图中，文件夹中没有`launch.json`**资源管理器**中`.vscode`的文件，并且没有字符串，例如在窗口底部**启动 Edge 无头和附加 DevTools**，因为 DevTools 是通过右键单击`.html`**资源管理器**中的文件打开的。


有关其他 UI 步骤和屏幕截图，请参阅 [UI 中显示的名称字符串的位置](./launch-json.md#where-the-name-strings-appear-in-the-ui)。  在大多数情况下，你唯一需要知道的关于 DevTools 生成 `launch.json` 的文件的内容的事项是，你需要在几个位置在字符串中 `"url"` 输入所需的 URL。


<!-- ====================================================================== -->
## <a name="automatically-opening-the-browser-and-devtools-when-debugging-in-visual-studio-code"></a>在Visual Studio Code中调试时自动打开浏览器和 DevTools

若要调试项目，可能需要更改在 Visual Studio Code 的 Microsoft Edge 中打开的默认页面。  若要将默认页面更改为项目的网站，请执行以下操作：

1. 在Visual Studio Code中，选择 **“文件** > **新建”窗口**。  请注意，未打开任何文件夹。

1. 在 **活动栏**上，选择 **“Microsoft Edge 工具**”。

1. 在 **“Microsoft Edge 工具：目标”** 面板中，单击 **打开的文件夹** 链接。

1. 在Visual Studio Code中开始调试时，选择项目文件夹，其中包含要显示的新默认页面。

   首次打开文件夹时，必须确认信任此文件夹中文件的作者：

   ![是否信任此文件夹文件中的作者？](./debugging-a-webpage-images/trust.png)

1. （可选）选中 **“信任父文件夹中所有文件的作者”的**复选框，然后单击“ **是，我相信作者”** 按钮：

   首次执行此过程时，还必须再次> **Microsoft Edge 工具** 选择活动栏。

   **Microsoft Edge 工具：目标**面板现在显示两个按钮：**启动实例**和**生成 launch.json**：

   ![“Microsoft Edge 工具：目标”面板显示“启动实例”和“生成 launch.json”按钮](./debugging-a-webpage-images/targets-buttons.png)

   **生成面向 DevTools 的 launch.json：**

1. 选择 **“生成 launch.json** ”以在项目中创建一个 `launch.json` 。  这必须是 DevTools 创建的较长文件，如 [DevTools 扩展的 launch.json 文件](./launch-json.md)中所示，而不是由 Visual Studio Code 创建的较短、更通用的文件。  另请参阅在 _DevTools 扩展疑难解答_中[删除或重新创建 launch.json](./troubleshooting.md#deleting-or-re-creating-launchjson)。

1. 在 `launch.json`其中，添加项目的 URL。 如果将 URL 留空，则会显示默认页面。

1. 保存 `launch.json`。

选择在 Visual Studio Code 中调试项目时，无论是使用 DevTools UI 功能还是通常的 Visual Studio Code UI 功能，它都会自动启动浏览器并打开开发人员工具，显示在文件中指定的 `launch.json` URL。


<!-- ====================================================================== -->
## <a name="if-you-see-the-success-page-but-want-your-own-webpage-instead"></a>如果看到“成功”页，但想要自己的网页

   打开哪个网页是在 DevTools 中设置 `launch.json` 的，前提是该文件存在于工作区中 (打开的文件夹) 。  因此，可以在打开自己的`.html`文件时按`F5`下，但在 **DevTools** 选项卡中看到默认**的“成功**”页。  在这种情况下，选项包括：

   *  在打开的文件夹中编辑 `launch.json` 以指向通常) 或文件路径 (URL。  然后可以使用Visual Studio Code调试器工作流/UI，例如`F5`。

   *  或者，删除 `launch.json`活动栏> **资源管理器** >右键单击文件 `.html` >选择 **“使用 Edge 打开**”。  此方法不使用Visual Studio Code调试器工作流/UI，例如`F5`。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [DevTools 扩展的 launch.json 文件](./launch-json.md)
* [在 Visual Studio Code 中调试 Microsoft Edge](../debugger-for-edge.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
* [Visual Studio Code调试器现在与 DevTools](../../devtools-guide-chromium/whats-new/2021/07/devtools.md#the-visual-studio-code-debugger-now-integrates-with-the-devtools-extension) (_Microsoft Edge 93) 中的“新增功能”中的 DevTools _扩展集成。
<!--todo: incorporate pov from what's new; update present article, then remove this link.  Explain: The tools refresh automatically when you switch between different debugging targets.-->

**外部页面：**

* 在Visual Studio Code调_试_文章中[启动配置](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)。
* [VS Code 中的浏览器调试](https://code.visualstudio.com/docs/nodejs/browser-debugging)
