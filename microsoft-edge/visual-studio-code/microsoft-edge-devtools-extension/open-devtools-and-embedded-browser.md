---
title: 打开 DevTools 和 DevTools 浏览器
description: 打开“Edge DevTools”选项卡和“Edge DevTools：浏览器”选项卡 (Microsoft Edge 开发人员工具扩展中用于Visual Studio Code的嵌入式浏览器) 。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/11/2022
ms.openlocfilehash: 34b6ce022dab732d2aa25236ac7bc467345e110e
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12815919"
---
# <a name="opening-devtools-and-the-devtools-browser"></a>打开 DevTools 和 DevTools 浏览器

可以通过多种方式打开 **“DevTools** ”选项卡和 **“Edge DevTools：浏览器”** 选项卡：

| 方法 | 描述 |
|---|---|
| 单击 **“启动实例** ”按钮。 | 不使用任何 `launch.json` 文件。  在非调试模式下打开 DevTools。  如果不想调试，请使用此方法。 |
| 右键单击 `.html` 文件。 | 不使用任何 `launch.json` 文件。  在调试模式下打开 DevTools。  如果要调试，并且 Web 应用可以从文件系统而不是 Web 服务器运行，请使用此方法。 |
| 单击 **“启动项目”** 按钮。 | `launch.json`使用文件。  在调试模式下打开 DevTools。  如果要调试，并且 Web 应用使用需要在 Web 服务器上运行它的 API，请使用此方法。 |

下面介绍了这些方法。  有关使用 Demos 存储库的详细步骤，请参阅[用于 Visual Studio Code 的 DevTools 扩展入](./get-started.md)门。


<!-- ====================================================================== -->
## <a name="opening-devtools-by-clicking-the-launch-instance-button"></a>单击“启动实例”按钮打开 DevTools

此方法在非调试模式下打开 DevTools 选项卡，并且在不需要调试工具栏时非常有用。

这些步骤假定最初未在Visual Studio Code中打开文件夹，而您打开的文件夹没有`launch.json`文件。

1. 在Visual Studio Code中，执行以下任一操作：

   *  在“资源管理器”按钮](./open-devtools-and-embedded-browser-images/explorer-icon.png) (![选择**活动栏** > **资源管理器**) >单击 **“打开文件夹**”按钮。
   *  选择 **“文件** > **打开文件夹**”。
   *  选择“**最近打开****的文件** > ”。

   若要使用所有 DevTools 功能，包括在 DevTools 中编辑 CSS 时本地源文件的 CSS 镜像编辑，请打开一个文件夹，其中包含与要在 DevTools 中显示的网页匹配的源文件。

1. 在活动栏中，单击 **“Microsoft Edge Tools** (![Microsoft Edge Tools”按钮](./open-devtools-and-embedded-browser-images/microsoft-edge-tools-icon.png)) 按钮，然后单击 **“启动实例** ”按钮。

   ![Microsoft Edge DevTools for Visual Studio Code 扩展](./open-devtools-and-embedded-browser-images/extension-icon.png)

   如果有 **“启动项目”** 按钮而不是 **“启动实例** ”按钮，则表示该文件夹包含文件 `launch.json` 。  检查文件中 `launch.json` 指定的 URL，并考虑单击 **“启动项目**”，如 [“打开 DevTools”中所述，单击“启动项目”按钮](#opening-devtools-by-clicking-the-launch-project-button)。  或者，如果要了解 **“启动实例** ”按钮的工作原理，可以删除该 `launch.json` 文件并在以后生成新 `launch.json` 文件。

   ![单击“启动实例”按钮](./open-devtools-and-embedded-browser-images/devtools-extension-new-browser-instance.png)

   *  “ **Edge DevTools** ”选项卡随即打开，最初包含有关“成功”页的信息，例如 `C:\Users\myusername\.vscode\extensions\ms-edgedevtools.vscode-edge-devtools-2.1.1\out\startpage\index.html`。
   *  “ **Edge DevTools：浏览器”选项卡** (嵌入式浏览器) 打开，最初显示“成功”页。
   *  Visual Studio Code的调试工具栏和调试 UI 未打开。
   *  在 **“Microsoft Edge 工具** ”窗格中，“ **目标”** 部分将打开，列出目标，并删除 **“启动实例** ”按钮。

1. 在 **“Edge DevTools：浏览器”** 选项卡的地址栏中，粘贴与Visual Studio Code中打开的文件夹匹配的文件路径或 URL。

   若要获取文件路径，请在Visual Studio Code >活动栏>**资源管理器** (![资源管理器按钮](./open-devtools-and-embedded-browser-images/explorer-icon.png)) >右键单击`.html`>**复制路径**的文件。

   如果要粘贴 URL，典型的示例包括：
   * [http://localhost:8080](http://localhost:8080)
   * [http://127.0.0.1:8080](http://127.0.0.1:8080)
   * [http://10.0.1.8:8080](http://10.0.1.8:8080)
   * [http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/) 如果从 Demos 存储库的根目录启动服务器。

   输入 (（例如，) `npx http-server` 在本地运行 Web 服务器）时，命令行上会显示类似的 URL。

   指定的网页显示在 **“边缘 DevTools：浏览器”选项卡** 中， (嵌入式浏览器) 。  Edge **DevTools** 选项卡显示有关网页的信息。


另请参阅：
* 步骤 2：通过单击“_开始使用 DevTools 扩展进行Visual Studio Code_”的[默认页面的“启动实例”按钮启动 DevTools](./get-started.md#step-2-start-devtools-by-clicking-the-launch-instance-button-for-the-default-page)。


<!-- ====================================================================== -->
## <a name="opening-devtools-by-right-clicking-an-html-file"></a>通过右键单击 HTML 文件打开 DevTools

此方法在调试模式下打开 DevTools 选项卡，建议使用，除非网页需要在 Web 服务器上运行，如某些 API 一样。

若要打开 DevTools 和嵌入式浏览器，以及硬盘上 HTML 文件的调试工具栏：

1. 在Visual Studio Code中，执行以下任一操作：

   *  单击“**打开文件夹**”按钮](./open-devtools-and-embedded-browser-images/explorer-icon.png)) >![选择**活动栏** > **资源管理器** (资源管理器按钮。
   *  选择 **“文件** > **打开文件夹**”。
   *  选择“**最近打开****的文件** > ”。

1. 打开包含 Web 应用源文件的文件夹。

1. 在Visual Studio Code中，在**资源管理器**中，右键单击文件`.html`，选择 **“使用 Edge 打开**”，然后选择 **“使用 DevTools 打开浏览器**”：

   ![右键单击资源管理器中的 HTML 文件以使用 Edge 打开它，无论是否使用 DevTools](./open-devtools-and-embedded-browser-images/context-menu-open-in-code.png)

   DevTools 随即打开：

   ![Visual Studio Code中的嵌入式浏览器实例](./open-devtools-and-embedded-browser-images/embedded-browser.png)

   以下组件在Visual Studio Code中打开：
   *  “ **Edge DevTools** ”选项卡，包括 **“元素”** 选项卡和其他工具选项卡。
   *  **Edge DevTools：“浏览器”** 选项卡。
   *  调试工具栏。
   *  调试控制台。
   *  “ **视图** > **运行** (**运行和调试**) 窗格。
   *  在此方法中， **活动栏** > **Microsoft Edge 工具** > **目标**中未列出实例。

   ![使用 DevTools 选择 Open Browser 的 DevTools 组件](./open-devtools-and-embedded-browser-images/devtools-extension-v211.png)

使用活动栏中的 **资源管理器** 侧栏在调试网页期间打开 `.js` 文件。

**Edge DevTools：浏览器**选项卡包含设备仿真工具栏。  此选项卡包含具有 DevTools 功能的嵌入式 Web 浏览器。  此浏览器有时称为 DevTools _的屏幕广播_ 或 _无头浏览器_ 。


另请参阅[步骤 4：通过右键单击使用 DevTools 扩展Visual Studio Code入门中的 HTML 文件启动 DevTools](./get-started.md#step-4-start-devtools-by-right-clicking-an-html-file)。__


<!-- ====================================================================== -->
## <a name="opening-devtools-by-clicking-the-launch-project-button"></a>单击“启动项目”按钮打开 DevTools

此方法在调试模式下打开 DevTools 选项卡，如果网页需要在 Web 服务器上运行，则建议使用某些 API 运行。

总结：
1. 打开包含 Web 应用源文件的本地文件夹。
1. 单击 **“生成 launch.json** ”按钮。
1. 在文件中 `.json` 添加 localhost URL。
1. 单击 **“启动项目”** 按钮。

这些步骤假定运行的是 localhost Web 服务器，如步骤 6 中所述：在_安装用于Visual Studio Code的 DevTools 扩展_时[设置 localhost 服务器](./install.md#step-6-set-up-a-localhost-server)。

单击 **“启动项目** ”按钮打开 DevTools：


   **打开包含 Web 应用源文件的本地文件夹：**

1. 在Visual Studio Code中，执行以下任一操作：

   *  在“资源管理器”图标](./open-devtools-and-embedded-browser-images/explorer-icon.png) (![选择**活动栏** > **资源管理器**) >单击 **“打开文件夹”** 按钮。
   *  选择 **“文件** > **打开文件夹**”。
   *  选择“**最近打开****的文件** > ”。

   选择包含网页源文件的目录。
   
1. 在活动栏中，单击 **Microsoft Edge Tools** (![Microsoft Edge Tools 图标](./open-devtools-and-embedded-browser-images/microsoft-edge-tools-icon.png)) 。  “ **Microsoft Edge 工具** ”窗格随即打开。

   *  如果该文件夹尚未包含 `.vscode` 包含某个 `launch.json file`目录， **则 Microsoft Edge 工具** 侧栏包含 **启动实例** 按钮和 **“生成 launch.json** ”按钮。

   *  如果 **Microsoft Edge 工具** 侧栏包含 **“启动项目”** 按钮，则打开的文件夹 `.vscode` 目录中包含一个 `launch.json` 文件，你可能想要检查或更改 `url` 该文件中的字符串，如下所述。

1. 单击 **“生成 launch.json** ”按钮：

   ![DevTools 扩展的“生成 launch.json”按钮](./get-started-images/launch-instance-button.png)

   新 `launch.json` 文件随即打开。

1. 在文件中的 `launch.json` 多个位置，在每个 `"url"` 行上，向右滚动，并记下注释“提供项目的 URL 以完成配置”：

   ```js
   "url": "c:\\Users\\username\\.vscode\\extensions\\ms-edgedevtools.vscode-edge-devtools-2.1.1\\out\\startpage\\index.html", 
   // Provide your project's url to finish configuring
   ```

   典型示例：
   * [http://localhost:8080](http://localhost:8080)
   * [http://127.0.0.1:8080](http://127.0.0.1:8080)
   * [http://10.0.1.8:8080](http://10.0.1.8:8080)
   * [http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/) 如果从 Demos 存储库的根目录启动服务器。

   输入 `npx http-server`时，命令行上会显示类似的 URL。

1. 将引号路径字符串内的路径粘贴到其中一个字符串中 `"url"` 。  例如：

   ```js
   "url": "http://localhost/demo-to-do/", // Provide your project's url to finish configuring
   ```

   URL 字符串可以是本地文件路径，但在这种情况下， `launch.json` 不需要文件;可以右键单击 `.html` 文件。

   如果按原样保留 URL，则会显示默认 **的“成功** ”页，并且可以将 localhost URL 或文件路径粘贴到 **Edge DevTools：浏览器** 选项卡的地址栏中。

1. 将修改后的 URL 行复制并粘贴到文件中 `launch.json` 的其他位置。  若要同时修改所有实例，可以复制更新后的 URL 字符串，然后选择初始 URL 字符串的实例，按`Ctrl`++`Shift``L`下以选择所有实例，然后粘贴更新后的字符串。

1. 保存 `launch.json` 文件。


   **单击“启动项目”按钮：**

1. 在Visual Studio Code中，在活动栏中，单击 **“Microsoft Edge Tools** (![Microsoft Edge Tools”图标](./get-started-images/microsoft-edge-tools-icon.png)) 按钮。  此时将打开 **“Microsoft Edge Tools** ”窗格，其中包含 (的 **“启动项目** ”按钮，而不是) 的 **“启动实例** ”按钮，并且不再包含 **“生成 launch.json 文件** ”按钮：

   ![存在 launch.json 文件时的目标窗格](./get-started-images/targets-pane-when-launch-json-exists.png)

1. 单击 **“启动项目”** 按钮。

   “ **Edge DevTools** ”选项卡和 **“Edge DevTools：浏览器”** 选项卡在单独的窗格中打开，显示在以下内容中 `launch.json`指定的 Web 应用 URL：

   ![在 Edge DevTools：浏览器选项卡中运行的演示到操作 Web 应用](./get-started-images/demo-app-running-in-extension-browser.png)


另请参阅：
* 步骤 7：通过单击“_开始使用 DevTools 扩展进行Visual Studio Code_”中的[“启动项目”按钮启动 DevTools](./get-started.md#step-7-start-devtools-by-clicking-the-launch-project-button)。


<!-- ====================================================================== -->
## <a name="mapping-url-files-to-the-opened-folder"></a>将 URL 文件映射到打开的文件夹

如果 DevTools 能够关联并建立从服务器下载的文件与打开的文件夹中的文件之间的工作区映射，则 DevTools 将提供其完整功能，包括在 DevTools 中更改 CSS 时对本地源文件进行 CSS 镜像编辑。

如果 DevTools 无法将 **Edge DevTools：浏览器**选项卡中的文件映射到在 Visual Studio Code 资源管理器中打开的文件夹中的文件，则可以检查网页，并且可以更改它们，例如在 **Edge DevTools** 选项卡的 **“元素**”工具的 **“源**”选项卡中更改 CSS 值。 但是，在这种情况下，不能使用 CSS 镜像编辑来让 DevTools 自动编辑源文件。  选项包括： 
*  清除“**样式**”选项卡中的 **CSS 镜像编辑**复选框，并继续试验 CSS 更改。
*  打开包含与网页匹配的源文件的文件夹。
*  通过在Visual Studio Code中打开文件夹来授予对该文件夹的信任。

例如：

1. 打开演示存储库的本地副本中的文件夹，例如`C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`，在[开始使用用于Visual Studio Code的 DevTools 扩展](./get-started.md)时所述。

1. 打开 DevTools，如上所述。

1. 在 **“Edge DevTools：浏览器”** 选项卡的地址栏中，粘贴远程 `github.io` URL，例如 [https://microsoftedge.github.io/Demos/demo-to-do/](https://microsoftedge.github.io/Demos/demo-to-do/)。

   该地址的文件实际上作为源文件驻留在 GitHub [https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do](https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do)处，而不是驱动器上。

   现在可以在 **Elements** 工具中更改 CSS 值，因为在 Visual Studio Code 的**资源管理器**中，打开一个文件夹，其中包含 DevTools 能够映射到构成网页的下载资源文件的源文件：

   ![如果打开可修改的文件夹，则能够更改 CSS 值](./open-devtools-and-embedded-browser-images/edit-css-when-folder-opened.png)

   接下来，尝试更改未打开文件夹的 CSS：

1. 选择 **“文件** > **关闭文件夹**”。

1. 单击 **“启动实例** ”按钮启动 DevTools，如上所述。

1. 在 **“Edge DevTools：浏览器”** 选项卡的地址栏中，粘贴远程 `github.io` URL，例如 [https://microsoftedge.github.io/Demos/demo-to-do/](https://microsoftedge.github.io/Demos/demo-to-do/)。

   现在，包含源文件的文件夹已关闭，如果尝试更改 **Elements** 工具中的 CSS 值，则会收到 DevTools 错误消息。  可以检查网页，但不能编辑它们。  可以使用 **Edge DevTools：浏览器** 选项卡底部的“设备仿真”工具栏，与页面交互，并在不同的设备和呈现状态中查看它。 还可以检查 CSS 和 HTML。  但是，如果尝试更改页面，会收到错误，例如 **镜像时出错**：

   ![如果无法打开可修改的文件夹，则无法更改 CSS 值的资源管理器](./open-devtools-and-embedded-browser-images/edit-css-when-no-folder-opened.png)

   作为该方案的另一个视角，下面是单击 **“启动实例**”按钮时的 **Microsoft Edge 工具**侧栏，当查看 URL 时，未打开包含与 URL 网页资源匹配的源文件的文件夹：

   ![查看 URL 时的 Microsoft Edge 工具侧栏](./open-devtools-and-embedded-browser-images/limited-css-edit-ability-for-remote-url.png)

本例中的选项包括： 

*  清除“**样式**”选项卡中的 **CSS 镜像编辑**复选框，然后继续试验 CSS 更改 (，而无需自动编辑源文件) 中的 CSS。  这可防止有关映射到源文件以进行 CSS 镜像编辑的更多错误消息。

*  打开包含与网页匹配的源文件的文件夹，以便在源文件中自动编辑 CSS。

*  在 DevTools 尝试编辑源文件但Visual Studio Code未授予对包含文件夹的信任的情况下，请在Visual Studio Code中打开该文件夹以授予对该文件夹的信任。

另请参阅：
* [DevTools 扩展疑难解答](./troubleshooting.md)


#### <a name="urls-file-paths-and-opening-a-matching-folder"></a>URL、文件路径和打开匹配的文件夹

在某些情况下，对于文件路径，DevTools 的行为不同于 URL 的行为。

*  如果在 DevTools 浏览器的地址栏中输入文件路径，并在 DevTools 中编辑 CSS，则浏览器知道在哪里可以找到源文件。  可能需要打开该文件夹以授予对它的信任，以便能够使用 CSS 镜像编辑。  或者，清除 **CSS 镜像编辑** 复选框。

*  如果在 DevTools 浏览器的地址栏中输入 URL，则浏览器知道在何处可以找到源文件的下载副本（如果只是检查网页并尝试使用 CSS）。  如果要使用 CSS 镜像编辑 (在源文件) 中编辑 CSS，则必须选中 **CSS 镜像编辑**复选框，并且必须在包含与网页匹配的源文件的Visual Studio Code中打开一个文件夹。


<!-- ====================================================================== -->
## <a name="closing-devtools"></a>关闭 DevTools

使用以下任一方法关闭 DevTools 实例：

*  如果Visual Studio Code处于调试模式，请单击“调试”工具栏中的 **“停止**”按钮，或选择 **“运行** > **停止调试**”：

   ![调试工具栏中的“停止”按钮](./get-started-images/stop-button-debug-toolbar.png)

   **Edge DevTools** 和 **Edge DevTools：浏览器**选项卡关闭。

*  如果“ **Edge DevTools** ”选项卡处于打开状态，请单击选项卡上的 **“关闭** (**x**) ”。

*  如果“ **Edge DevTools：浏览器”** 选项卡处于打开状态，请单击选项卡上的 **“关闭** ” (**x**) 。

*  > **Microsoft Edge 工具**选择活动栏。  如果 **“目标”** 部分列出了任何目标，请将鼠标悬停在目标实例右侧，然后单击 **“关闭** ”实例 (**x**) ：

   ![单击“启动实例”按钮关闭 DevTools（如果打开）](./open-devtools-and-embedded-browser-images/close-devtools-opened-by-launch-instance.png)

   然后显示 **“启动实例** ”或“ **启动项目** ”按钮。

*  选择 **“文件** > **关闭文件夹**”。

*  关闭Visual Studio Code窗口。

*  如果 DevTools 扩展打开了外部自动化控制的浏览器，请关闭外部浏览器窗口。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
