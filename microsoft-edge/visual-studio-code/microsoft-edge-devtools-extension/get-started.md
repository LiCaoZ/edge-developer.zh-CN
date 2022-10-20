---
title: 开始将 DevTools 扩展用于Visual Studio Code
description: 有关打开和关闭 DevTools 并使用它来修改 CSS 和调试 JavaScript 的分步教程。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: c0b8c31b5e18384b96951903e719afa5a7038ee5
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816081"
---
# <a name="get-started-using-the-devtools-extension-for-visual-studio-code"></a>开始将 DevTools 扩展用于Visual Studio Code

这是一个分步教程，介绍如何打开和关闭 DevTools 并使用它来修改 CSS 和调试 JavaScript。  请按照此处从上到下的步骤进行常规介绍，并确保计算机已设置为使用 DevTools。


<!-- ====================================================================== -->
## <a name="step-1-install-devtools-and-prerequisites"></a>步骤 1：安装 DevTools 和先决条件

1. 执行安装 [Visual Studio Code 的 DevTools 扩展](./install.md)中的步骤，然后继续执行以下操作。


<!-- ====================================================================== -->
## <a name="step-2-start-devtools-by-clicking-the-launch-instance-button-for-the-default-page"></a>步骤 2：单击默认页面的“启动实例”按钮启动 DevTools

此方法在非调试模式下打开 DevTools 选项卡，在不想使用Visual Studio Code的调试功能时非常有用。  这种打开 DevTools 的方式支持的方案：

*  如果使用文件路径，则无需在Visual Studio Code中打开文件夹;仍可使用 CSS 镜像编辑来编辑 CSS 源文件。

*  如果未打开文件夹，并且想要检查使用 URL 指定的页面。

*  如果未打开文件夹，并且想要尝试在使用 URL 指定的页面上更改 CSS，而不使用 CSS 镜像编辑。

单击 **“启动实例** ”按钮不会直接转到文件;必须粘贴文件路径或 URL。  此方法在 UI 中非常突出，你需要知道如何关闭已以这种方式打开的 DevTools 实例。  还应了解如何编辑“成功”页面，以便开始操作。

   **打开“DevTools”选项卡：**

1. 在 Visual Studio 中，选择 **“文件** > **新建”窗口**。  最初，未打开任何文件夹。

1. 在活动栏中，单击 **Microsoft Edge Tools** (![Microsoft Edge Tools 图标](./get-started-images/microsoft-edge-tools-icon.png)) 。  **Microsoft Edge 工具**侧栏随即打开。

1. 单击 **“启动实例** ”按钮。  “ **Edge DevTools** ”选项卡随即打开，“ **Edge DevTools：浏览器** ”选项卡随即打开，显示默认的“成功”页。  在 DevTools 浏览器的地址栏中，有一个 `file:///` 路径 (而不是 URL) ，例如 `file:///C:/Users/myusername/.vscode/extensions/ms-edgedevtools.vscode-edge-devtools-2.1.1/out/startpage/index.html`。

   调试工具栏未打开，**调试控制台**未在底部打开，并且“使用**监视**”窗格的 **“运行和调试**”侧栏未打开。  这表示Visual Studio Code未处于调试模式。

   可以修改本地文件的 CSS，并且可以在地址栏中输入本地文件路径或 localhost URL，并与本地 Web 应用页交互。

   **打开文件夹：**

   请注意，Visual Studio Code中未打开任何文件夹。  在许多情况下，若要使用 DevTools 进行编辑，而不是仅仅检查网页，必须打开包含与显示的网页匹配的源文件的文件夹。  打开文件夹具有最大的灵活性，因此可以在 **Edge DevTools：Browser** 选项卡的地址栏中打开 URL 或文件路径，并具有完整的 DevTools 功能。  打开文件夹可让你有机会向文件夹授予信任，以便在尝试更改源文件时不会收到错误消息。

   否则，你可能会收到错误消息，因为包含“成功”页的文件夹不受信任，CSS 镜像编辑正在尝试编辑该文件夹中的源文件中的 `index.html` CSS。

1. 在 **“Edge DevTools：浏览器”** 选项卡的地址栏中，选择并复制文件路径，但不选择文件名，例如 `C:/Users/myusername/.vscode/extensions/ms-edgedevtools.vscode-edge-devtools-2.1.1/out/startpage/`。

1. 在活动栏> **资源管理器**中，单击 **“打开文件夹”** 按钮。  在 **“打开文件夹** ”对话框中，粘贴或选择上面复制的路径。  若要粘贴，在 Windows 上，可能需要更改 `/` 为 `\` 整个路径。 然后单击“ **选择文件夹”** 按钮。

   首次打开文件夹时，必须确认信任此文件夹中文件的作者：

   ![是否信任此文件夹文件中的作者？](./get-started-images/trust.png)

1. 单击“ **是”，我信任作者** 按钮。

   可能需要再次启动 DevTools，如下所示。

1. 在活动栏中，单击 **Microsoft Edge Tools** (![Microsoft Edge Tools 按钮](./get-started-images/microsoft-edge-tools-icon.png)) 。  **Microsoft Edge 工具**侧栏随即打开。

1. 单击 **“启动实例** ”按钮。

   “ **Edge DevTools** ”选项卡随即打开，“ **Edge DevTools：浏览器** ”选项卡随即打开，显示默认的“成功”页。  “成功”页源文件是驱动器上的目录中的自包含 `.html` 文件。  这是一个包含元素) 中 (的 CSS 规则的单 `.html` 个 `<style>` 文件。  它还包括元素) 中的 `<script>` JavaScript `console` 语句 (。

   **编辑 CSS：**

1. 在 **“Edge DevTools** ”选项卡中，单击 **页面中的“选择元素”以检查它** (![“检查工具”图标](./open-devtools-and-embedded-browser-images/inspect-tool-icon.png)) 按钮，有时调用“ **检查** ”按钮。

1. 在 **“Edge DevTools：浏览器”** 选项卡中，将鼠标悬停在页面的不同部分上，同时观看 **元素** 工具的 DOM 树展开和更新。

1. 单击 **“成功！** 标题，这是一个 `<h2>` 元素。

1. 在 **Edge DevTools** 选项卡中 **“元素**”工具的“样**式**”选项卡中，在非斜体 h2 声明部分中，单击规则右侧`margin-bottom`。

1. 输入新的 CSS 规则， `font-size: 5em`然后按 `Enter`。  拼写类似于其下方用户代理样式表的斜体 h2 部分中显示的规则。

   `index.html` 打开后，由 CSS 镜像编辑自动编辑以添加行 `font-size: 5em;`。  在 h2 部分中滚动到该行。

   **排列选项卡：**

1. 在 **“Edge DevTools”** 选项卡的非斜体 h2 部分中，单击输入的 `font-size` CSS 规则，然后按`Up Arrow`下。`Down Arrow`  CSS 镜像编辑会自动编辑其中 `index.html` 的值。

1. 在 **“Edge DevTools”** 选项卡中，单击“ **切换屏幕广播** ”按钮几次。  **Edge DevTools：“浏览器”** 选项卡打开并关闭，从而节省空间。

1. 在 **“Edge DevTools：浏览器”** 选项卡中，单击“ **关闭 DevTools** ”或“ **打开 DevTools** ”按钮几次。  其他 **DevTools** 选项卡会打开并关闭，从而节省空间。

1. 在Visual Studio Code顶部，右键单击选项卡并将其排列为同时显示各种选项卡： 

   *  侧栏，显示 **Microsoft Edge 工具** > **目标**。
   *  编辑 `index.html` 器。
   *  “ **Edge DevTools”** 选项卡。
   *  **Edge DevTools：“浏览器”** 选项卡。

   ![成功页面编辑 h2 CSS 大小](./open-devtools-and-embedded-browser-images/success-page-edit-h2-css.png)

   **查看 JavaScript：**

1. 在 **“Edge DevTools”** 选项卡中，单击 **“控制台** ”工具的选项卡。  `index.html` 包含包含 `<script>` JavaScript 语句的元素，该语句 `console.info('Hello from the startpage!')`输出“Hello from the startpage！”

   **关闭 DevTools：**

1. 单击 **“边缘开发工具**”选项卡和 **“Edge DevTools：浏览器**”选项卡中的 **“关闭**” (**x**) （如果这些选项卡处于打开状态）。

1. > **Microsoft Edge 工具**选择活动栏。  如果 **“目标”** 部分列出了任何目标，请将鼠标悬停在目标实例右侧，然后单击 **“关闭** ”实例 (**x**) 。  将显示 **“启动实例** ”按钮，指示所有 DevTools 实例都已关闭。

1. 关闭 `index.html` 而不保存更改。

1. 选择 **“文件** > **关闭文件夹**”。


<!-- ====================================================================== -->
## <a name="step-3-start-devtools-by-clicking-launch-instance-button-for-demo-to-do"></a>步骤 3：单击“启动实例”按钮以执行演示操作来启动 DevTools

1. 在 Visual Studio 中，选择 **“文件** > **打开文件夹**”。  `\Demos\demo-to-do\`打开克隆的 Demos 存储库的文件夹，例如 `C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`。

1. 如果出现提示，请单击 **“是”，我相信作者** 按钮。  除了授予信任之外，如果在 DevTools 浏览器中指定文件路径而不是 URL， **则启动实** 例方法实际上不需要打开文件夹。

1. 活动栏> **资源管理器** >右键单击 `\demo-to-do\index.html` > **“复制路径**”。

1. 在 Visual Studio 的 **“Edge DevTools：浏览器**”选项卡的地址栏中，粘贴上面获取的本地文件路径，例如“'C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\index.htmlfile:/// `.  The **demo-to-do** app opens.  In the address bar, the `` prefix is added and Windows backslashes are changed to forward slashes; for example: `file:///C:/Users/myusername/Documents/GitHub/Demos/demo-to-do/index.html'。

   或者，如果 localhost 服务器正在运行，请粘贴 localhost URL，例如 [http://localhost:8080/](http://localhost:8080/) 或 [http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/)。  如果要使用 CSS 镜像编辑来编辑源文件，则需要在Visual Studio Code中打开一个文件夹;否则，请在 **Edge DevTools** 选项卡的 **“元素**”工具的“**样式**”选项卡中清除 **CSS 镜像编辑**复选框。 在 DevTools 中尝试更改 CSS 并且尚未为 DevTools 提供 CSS 源文件时，清除复选框可防止出现有关映射和镜像编辑的错误消息。

   或者，粘贴 github.io 服务器 URL。 [https://microsoftedge.github.io/Demos/demo-to-do/](https://microsoftedge.github.io/Demos/demo-to-do/)

1. 在演示应用中，输入任务，例如 **测试**。

1. 在 **“元素”** 工具的“ **样式”** 选项卡中，更改 CSS 值，例如：单击点大小 `body { font-size: 11pt;}` ，然后更改值。  打开的文件夹中的相应 `.css` 文件会自动编辑，以匹配在“ **样式** ”选项卡中所做的更改 (但不会保存) 。

   ![启动实例>文件路径>非调试模式](./get-started-images/launch-instance-filepath-non-debug-mode.png)


   **关闭 DevTools：**

1. 单击 **“边缘开发工具**”选项卡和 **“Edge DevTools：浏览器**”选项卡中的 **“关闭**” (**x**) （如果这些选项卡处于打开状态）。

*  > **Microsoft Edge 工具**选择活动栏。  如果 **“目标”** 部分列出了任何目标，请将鼠标悬停在目标实例右侧，然后单击 **“关闭** ”实例 (**x**) 。  将显示 **“启动实例** ”按钮，指示所有 DevTools 实例都已关闭。

1. 关闭 `index.html` 而不保存更改。

1. 选择 **“文件** > **关闭文件夹**”。


<!-- ====================================================================== -->
## <a name="step-4-start-devtools-by-right-clicking-an-html-file"></a>步骤 4：右键单击 HTML 文件启动 DevTools

<!-- the equivalent section in Opening is more general than this section, which uses Demos repo -->

当网页不需要在 Web 服务器上运行时，右键单击`.html`Visual Studio Code资源**管理器**中的文件是打开 DevTools 的主要方式。

*  与 **“启动实例** ”按钮不同，此方法在调试模式下打开 DevTools。

*  与稍后将使用的 **“启动项目** ”按钮不同，此方法不需要生成 `launch.json` 文件。


我们将通过打开 **演示即用** Web 应用进行演示：

1. 在Visual Studio Code中，选择 **“文件** > **打开文件夹**”。

1. 转到克隆 Demos 存储库的目录，打开 **演示待办** 应用的特定目录，例如 `C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`，然后单击“ **选择文件夹** ”按钮：

   ![打开文件夹：演示待执行](./get-started-images/open-folder-demo-todo.png)

1. 选择**活动栏** > **资源管理器** (![资源管理器图标](./get-started-images/explorer-icon.png)) >右键单击`index.html`，然后使用**DevTools** 选择 **“使用 Edge** >  打开浏览器打开”：

   ![右键单击>使用 DevTools 打开浏览器](./get-started-images/open-browser-with-devtools.png)

   *  “ **Edge DevTools”** 选项卡随即打开。

   *  “ **Edge DevTools：浏览器”** 选项卡随即打开，显示右键单击的网页。

   *  将打开Visual Studio Code调试工具栏，调**试控制台**在底部打开，**然后打开“运行**”窗格。  这些功能指示Visual Studio Code处于调试模式：

   ![两个 Edge DevTools 选项卡和调试工具栏](./get-started-images/devtools-extension-v211.png)

   **DevTools 选项卡的布局：**

1. 在 **Edge DevTools** 选项卡的左上角，单击“ **切换屏幕广播** ”按钮几次：

   ![交叉切换打开和关闭两个选项卡](./get-started-images/cross-toggling-tabs.png)

1. 在 **“Edge DevTools：浏览器** ”选项卡右上角，单击“ **关闭 DevTools** ”或 **“打开 DevTools** ”按钮几次。  打开并关闭两个 DevTools 选项卡时会自动定位。


<!-- ====================================================================== -->
## <a name="step-5-edit-css-in-devtools-updating-the-css-file-automatically"></a>步骤 5：在 DevTools 中编辑 CSS，自动更新 .css 文件

在 **“Edge DevTools”** 选项卡的 **“元素** ”工具> **“样式** ”选项卡中，可以编辑 CSS 选择器、规则和值。  默认情况下会选中 **CSS 镜像编辑** 复选框，因此 `.css` 会自动编辑文件，但不会保存编辑，以便你决定是否保存更改。

1. 在 **“元素”** 工具的“ **样式”** 选项卡中，单击 CSS 值，例如正文字体大小。

1. 更改 CSS 值，例如使用鼠标滚轮或按下`Up Arrow`。`Down Arrow`  关联 `.css` 的文件会打开，例如 `to-do-styles.css` 滚动到定义 CSS 值的行，并自动编辑 `.css` 文件，但不保存更改：

   ![CSS 镜像编辑](./get-started-images/css-mirror.png)

1. 关闭文件 `.css` 。  Visual Studio Code提示是否保存更改。

1. 单击 **“不保存** ”按钮。


<!-- ====================================================================== -->
## <a name="step-6-step-through-javascript-code-in-the-debugger"></a>步骤 6：在调试器中逐步执行 JavaScript 代码

1. 选择活动栏>资源管理器 (![活动栏中的资源管理器图标](./get-started-images/explorer-icon.png)).

1. 在 **演示待办** 目录中，单击 **to-do.js** 将其打开。  向下滚动到函 `changeTask` 数，然后单击行号左侧以设置断点：

   ![调试演示应用](./get-started-images/debugging-the-demo-app.png)

1. 如果未显示 **“运行和调试** ”侧栏，请选择 **“视图** > **运行**”。  **运行和调试**边栏包括 **“监视**”窗格和其他调试器窗格。

1. 在 **Edge DevTools：浏览器** 选项卡中呈现的演示应用中，输入任务，例如 **测试**。  Visual Studio Code调试器在文件的`to-do.js`断点处暂停：

   ![在演示应用中单步执行 JavaScript](./get-started-images/debugging-the-demo-app.png)

1. 在“调试”工具栏中，或使用 **“运行”** 菜单或按键，在其中单步执行几行代码 `to-do.js`。

1. 在 **Edge DevTools：浏览器** 选项卡中呈现的演示应用中，单击测试任务旁边的“完成”圆圈。  Visual Studio Code调试器在文件的`to-do.js`断点处暂停。

1. 接下来，若要结束调试，请在调试工具栏中单击“ **停止** () `Shift`+`F5` 按钮。  或者，在 **“运行** ”菜单上，选择 **“停止调试**”：

   ![调试工具栏中的“停止”按钮](./get-started-images/stop-button-debug-toolbar.png)

   Edge **DevTools** 选项卡关闭， **边缘 DevTools：浏览器** 选项卡关闭。

继续以下教程步骤。


<!-- ====================================================================== -->
## <a name="step-7-start-devtools-by-clicking-the-launch-project-button"></a>步骤 7：单击“启动项目”按钮启动 DevTools

接下来，我们将在将该按钮指向 localhost URL（例如[http://localhost:8080/](http://localhost:8080/)或[http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/)）后，使用**演示待**执行应用演示 **“启动项目**”按钮。  与以前一样，这会在调试模式下启动 DevTools。  这是在网页需要在 Web 服务器上运行时打开 DevTools 的主要方式。  作为初步步骤，我们将创建文件 `launch.json` 并编辑其中的 URL，以指向提供 **演示到操作示** 例应用的 localhost。

你可能不需要使用此方法，因为在许多情况下，右键单击 HTML 文件的工作原理。  但是，许多网页使用要求网页在 Web 服务器上运行的 API，因此可以执行以下特定步骤。


<!-- ====================================================================== -->
## <a name="step-8-start-the-web-server"></a>步骤 8：启动 Web 服务器

本部分支持单击 **“启动项目”** 按钮。

1. 设置并启动 Web 服务器，从 Demos 存储库中提供 **演示到操作** 应用。  为此，请参阅步骤 6：在_安装适用于 Visual Studio Code 的 DevTools 扩展_时[设置 localhost 服务器](./install.md#step-6-set-up-a-localhost-server)。

1. 在Visual Studio Code中，选择 **“查看** > **终端**”。

1. `cd` 进入要通过 http 服务的特定文件夹中： `Demos\demo-to-do\`

   例如，在 Windows 上：

   ```
   cd C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\
   ```

1. 输入命令 `npx http-server`。  本地 Web 服务器从端口 8080 开始。

   ```
   npx http-server
   ```
   
   将显示有关服务器和 localhost URL 的信息，例如：

   ```
   Starting up http-server, serving ./
   
   Available on:
   http://10.0.1.8:8080
   http://127.0.0.1:8080
   Hit CTRL-C to stop the server
   ```

   显示的 URL 等效于 `http://localhost` 或 `http://localhost:8080`
   <!-- http://localhost/demos/demo-to-do/ -->


<!-- ====================================================================== -->
## <a name="step-9-set-up-launchjson"></a>步骤 9：设置 launch.json

本部分支持单击 **“启动项目”** 按钮。

   1. 在 Visual Studio 中，选择 **“文件** > **打开文件夹**”。  选择包含在演示存储库中克隆的**演示到操作**示例的项目目录`index.html`，例如`C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`。
   
   1. 在活动栏中，单击 **Microsoft Edge Tools** (![Microsoft Edge Tools 图标](./get-started-images/microsoft-edge-tools-icon.png)) 。  “ **Microsoft Edge 工具** ”窗格随即打开。

   1. 单击 **“生成 launch.json** ”按钮：

   ![DevTools 扩展的“生成 launch.json”按钮](./get-started-images/launch-instance-button.png)

   新 `launch.json` 文件随即打开。

1. 在文件的 `launch.json` 多个位置，在每个 `"url"` 行上，向右滚动，并记下注释“提供项目的 URL”：

   ```js
   "url": "c:\\Users\\username\\.vscode\\extensions\\ms-edgedevtools.vscode-edge-devtools-2.1.1\\out\\startpage\\index.html", 
   // Provide your project's url to finish configuring
   ```

1. 在 Web 浏览器中`http://localhost/`，转到**演示到**`.html`操作文件位于服务器上的 URL，例如[http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/)。

1. 从地址栏复制 URL。

1. 在 `launch.json`每个 URL 字符串中，粘贴 **演示到操作** 应用的克隆副本的 URL，例如： `http://localhost/demos/demo-to-do/`

1. 将引号路径字符串内的路径粘贴到其中一个字符串中 `"url"` 。  例如：

   ```js
   "url": "http://localhost/demo-to-do/", // Provide your project's url to finish configuring
   ```

1. 将修改后的 URL 行复制并粘贴到文件中 `launch.json` 的其他位置。  若要同时修改所有实例，可以复制更新后的 URL 字符串，然后选择初始 URL 字符串的实例，按`Ctrl`++`Shift``L`下以选择所有实例，然后粘贴更新后的字符串。

1. 保存 `launch.json` 文件。


<!-- ====================================================================== -->
## <a name="step-10-click-the-launch-project-button"></a>步骤 10：单击“启动项目”按钮

1. 在Visual Studio Code中，在活动栏中，单击 **“Microsoft Edge Tools** (![Microsoft Edge Tools”图标](./get-started-images/microsoft-edge-tools-icon.png)) 按钮。  此时将打开 **“Microsoft Edge 工具** ”窗格，其中包含 **“启动项目** ”按钮，但不包含 **“生成 launch.json 文件** ”按钮：

   ![存在 launch.json 文件时的目标窗格](./get-started-images/targets-pane-when-launch-json-exists.png)

1. 单击 **“启动项目”** 按钮。

   Edge **DevTools** 选项卡和 **Edge DevTools：浏览器** 选项卡在单独的窗格中打开，显示 **演示待执行 Web** 应用：

   ![在“Edge DevTools：浏览器”选项卡中运行的演示到操作 Web 应用](./get-started-images/demo-app-running-in-extension-browser.png)

此时，可以使用调试器中的 CSS 编辑或逐步执行代码，如上述 [步骤 4：通过右键单击 HTML 文件启动 DevTools 部分](#step-4-start-devtools-by-right-clicking-an-html-file)所述。


<!-- ====================================================================== -->
## <a name="step-11-close-devtools"></a>步骤 11：关闭 DevTools

1. 接下来，若要结束调试，请在调试工具栏中单击“ **停止** () `Shift`+`F5` 按钮：

   ![调试工具栏中的“停止”按钮](./get-started-images/stop-button-debug-toolbar.png)

   或者，在 **“运行** ”菜单上，选择 **“停止调试**”。  或者，关闭两个 DevTools 选项卡。  调试工具栏关闭。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)

**GitHub：**

* [演示到操作](https://microsoftedge.github.io/Demos/demo-to-do/) - 在服务器上运行的 `github.io` 演示 Web 应用。
* [演示到操作的源代码](https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do)
* [MicrosoftEdge/Demos 存储库](https://github.com/MicrosoftEdge/Demos)

<!--
**Often-needed strings:**

C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\index.html
git bash: cd C:/Users/myusername/Documents/GitHub/Demos/demo-to-do/
npx http-server
C:/Users/myusername/Documents/GitHub/Demos/demo-to-do/index.html
http://localhost:8080/
https://microsoftedge.github.io/Demos/demo-to-do/
-->
