---
title: 安装用于Visual Studio Code的 DevTools 扩展
description: 安装适用于Visual Studio Code的 Microsoft Edge 开发人员工具扩展、克隆 Demos 存储库，以及设置 localhost 服务器以使用 Demos 存储库。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 594a696b3df9fca1422cb1c45c41491270dc3596
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816071"
---
# <a name="installing-the-devtools-extension-for-visual-studio-code"></a>安装用于Visual Studio Code的 DevTools 扩展

本文将指导你完成 DevTools 扩展的初始设置。  安装 DevTools 后，可以按照“[开始使用 DevTools 扩展Visual Studio Code](./get-started.md)中的步骤进行操作。

本文可帮助你：

* 安装 DevTools 扩展。

* 克隆演示存储库，其中包括 **演示到操作** Web 应用。

* 启动 Web 服务器，以便可以在 Visual Studio Code 中的 DevTools 扩展中使用 localhost URL。


<!-- ====================================================================== -->
## <a name="step-1-install-visual-studio-code"></a>步骤 1：安装Visual Studio Code

1. 如果尚未完成，请在单独的窗口或选项卡中转到[“下载Visual Studio Code](https://code.visualstudio.com/Download)并下载并安装Visual Studio Code。


<!-- ====================================================================== -->
## <a name="step-2-install-microsoft-edge"></a>步骤 2：安装 Microsoft Edge

对于 Visual Studio Code 的 DevTools 扩展，需要 Microsoft Edge。

在 Windows 上，已安装 Microsoft Edge。  在 macOS 或 Linux 上，按如下所示安装 Microsoft Edge：

1. 转到 Microsoft.com [处的 Edge](https://www.microsoft.com/edge) 页面。


<!-- ====================================================================== -->
## <a name="step-3-install-the-microsoft-edge-devtools-extension"></a>步骤 3：安装 Microsoft Edge DevTools 扩展

安装适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展，如下所示：

1. 打开Visual Studio Code。

1. 在左侧的活动栏中，单击“ **扩展** (![”图标](./get-started-images/extensions-icon.png)) 按钮。  或者，在 Windows/Linux 或`X``Shift`++`Command` macOS 上按`X``Ctrl`+`Shift`+下。  “ **扩展** 市场”窗格随即打开。

1. 在市场文本框 **中的搜索扩展中** ，输入 **适用于 VS Code 的 Microsoft Edge 工具**。

1. 选择 **适用于 VS Code 的 Microsoft Edge 工具**，然后单击“ **安装** ”按钮：

   ![安装适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](./get-started-images/vscode-edge-tools-install.png)

作为替代方法，可以使用浏览器从 Visual Studio 市场网站下载 Microsoft Edge DevTools 扩展。  转到[适用于Visual Studio Code的 Microsoft Edge 开发人员工具](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)。


<!-- ====================================================================== -->
## <a name="step-4-install-nodejs-and-node-package-manager-npm"></a>步骤 4：安装Node.js和节点包管理器 (npm) 

若要实时 (实时) 代码分析，以指示问题，如波浪下划线，并提供快速修复，必须安装Node.js和节点包管理器 (npm) 。

DevTools 扩展显示用于安装 Node.js 和 npm 的弹出式建议。  建议文本类似于：“安装Node.js & npm？  (建议，因为你安装了此扩展) ”。

1. 单击弹出窗口中的链接（如果打开）。

1. 从Node.js>下载> LTS 安装 [ Node.js ](https://nodejs.org) 和 npm (长期稳定)  (或当前) 。

   在 Windows 上，将下载.msi文件，例如 `node-v16.17.1-x64.msi`。

1. 在浏览器的“下载”窗格中，单击 **“在文件夹中显示**”。  运行下载的文件。  将打开Node.js安装向导。  单击“下一步”**** 按钮。  请按照提示操作。  

   确认已安装Node.js和 npm：

1. 在Visual Studio Code中，选择 **“查看** > **终端**”。  在命令提示符处，输入 `npm version`。  显示一个版本号`npm``node`，表示已安装节点包管理器和Node.js，以支持内联和实时问题分析：

   ```
   $ npm version
   {
   npm: '8.15.0',
   node: '16.17.1',
   ...
   }
   ```

另请参阅：
* [内联和实时问题分析](./inline-live-issue-analysis.md)


<!-- ====================================================================== -->
## <a name="step-5-clone-the-demos-repo"></a>步骤 5：克隆演示存储库

克隆演示存储库是可选的。  演示存储库可用于关注各种 DevTools 文档。  如果需要，可以打开现有项目目录（如果有）而不是克隆存储库。

另一种选择是，只能下载 **演示到操作** 目录，而不是克隆整个目录。  例如，转到 [https://download-directory.github.io/](https://download-directory.github.io/) 并粘贴 URL [https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do](https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do)。  该 `.zip` 文件将放置在下载目录中。  将这些网页源文件解压缩到合适的位置。  教程[开始使用用于Visual Studio Code的 DevTools 扩展](./get-started.md)使用示例位置：

`C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`


若要克隆 **Demos** 存储库以使用本教程 **的演示到操作** 示例，请执行以下操作：

1. 转到 [MicrosoftEdge/Demos 存储库](https://github.com/MicrosoftEdge/Demos/)。

1. 如果未显示绿色**代码**按钮，请单击左上角**的 Microsoft Edge** / **演示**路径中的**演示**，转到存储库的主页。

1. 单击绿色 **的“代码”** 按钮，然后选择“ **复制** ”按钮。  本文假定你在Visual Studio Code中使用**源代码管理**功能。  或者，如果知道要改用该方法，则可以使用所提供的其他方法之一：
   *  **使用 GitHub Desktop 打开**
   *  **使用 Visual Studio 打开**
   *  **下载 ZIP**

   ![克隆 MicrosoftEdge/Demos 存储库](./get-started-images/clone-repo.png)

1. 在Visual Studio Code中，在活动栏中，单击 **“源代码管理** (![源控件”图标](./get-started-images/source-control-icon.png)) 按钮，然后单击 **“克隆存储库**”按钮。

1. 在 **“提供存储库 URL** ”文本框中，粘贴复制的 URL： **https://github.com/MicrosoftEdge/Demos.git** 然后按 `Enter`下。  将打开文件夹选择对话框。

   ![Visual Studio Code中的“克隆存储库”按钮](./get-started-images/clone-repository-button.png)

1. 导航到所需的路径，例如 `C:\Users\myusername\Documents\GitHub` 或 `Users/myusername/GitHub`，然后单击“ **选择存储库位置** ”按钮。

1. 将显示“ **克隆 git 存储库** ”消息，系统会提示你打开克隆的存储库。  单击 **“打开** ”按钮：

   ![提示打开克隆的存储库](./get-started-images/prompt-open-cloned-repo.png)

1. 如果出现提示 **，请信任...**，单击“ **是** ”按钮。  或者，单击 **“否** ”按钮并继续执行本演练的大多数部分。

   **资源管理器**树列出了许多演示，包括**演示即用**。

1. 在 Visual Studio 中，选择 **“文件** > **关闭文件夹**”。

1. 在Visual Studio Code中，在活动栏中，单击 **“Microsoft Edge Tools** (![Microsoft Edge Tools”图标](./get-started-images/microsoft-edge-tools-icon.png)) 按钮。  “ **Microsoft Edge 工具** ”窗格随即打开。

1. 在 **“Microsoft Edge 工具** > **目标** ”窗格中，单击 **“打开文件夹”** 按钮。  打开“ **打开文件夹** ”对话框。  导航到你克隆的 `demo-to-do` 演示存储库中的文件夹，选择该文件夹或转到其中，然后单击“ **选择文件夹** ”按钮：

   ![选择演示到操作文件夹](./get-started-images/select-demo-to-do-folder.png)

   上面显示了已克隆 **Demos** 存储库的存储库位置的示例。  克隆`demo-to-do`的 **Demos** 存储库的文件夹在Visual Studio Code资源管理器中打开，但尚不存在任何`launch.json`文件：

   ![最初打开演示到操作文件夹](./get-started-images/opened-demo-to-do-folder-initially.png)


<!-- ====================================================================== -->
## <a name="step-6-set-up-a-localhost-server"></a>步骤 6：设置 localhost 服务器

在许多情况下，无需输入 URL 或运行 localhost 服务器。  例如，你可以：
*  打开包含网页源文件的文件夹，然后右键单击文件 `.html` 。
*  在地址栏中输入本地文件路径，例如 `C:/Users/myusername/.vscode/extensions/ms-edgedevtools.vscode-edge-devtools-2.1.1/out/startpage/index.html` (默认的“成功”页) 。
*  在地址栏中输入远程服务器 URL，例如 [https://microsoftedge.github.io/Demos/demo-to-do/](https://microsoftedge.github.io/Demos/demo-to-do/)。

如果你的网页使用某些 API，这些 API 要求网页在 Web 服务器上运行，以使用 DevTools，则必须启动本地 Web 服务器进行测试。  如果未在 Web 服务器上提供项目，但仅使用本地文件，仍可以通过右键单击本地 `.html` 文件使用具有调试功能的 DevTools。  专门要求应用在服务器上的应用的功能将不起作用，DevTools 的实用工具有限。

如果安装Node.js和 npm（如上所述） `npx http-server` 是启动本地 Web 服务器的简单方法。  有关信息，请参阅 [http-server：一个简单的静态 HTTP 服务器](https://www.npmjs.com/package/http-server)。


**若要设置 http-server，**

1. 在Visual Studio Code中，选择 **“文件** > **打开文件夹**”>打开包含`.html``.css`网页的目录和`.js`文件，例如`C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\`。

   在上面的示例路径中：
   *  `\Documents\GitHub\` 是存储库克隆到的位置 `Demos` 。
   *  `\Demos\` 是用于 Microsoft Edge 开发人员文档中示例的 GitHub 存储库。
   *  `\demo-to-do\` 是存储库中的示例目录之一。

1. 在Visual Studio Code中，选择 **“查看** > **终端**”。  或者，若要使 Web 服务器无论 Visual Studio 的状态如何运行，请在Visual Studio Code之外打开命令提示符，例如`git bash`。

1. `cd` 进入要通过 http 提供的文件夹。

   例如，在 **终端**的 Windows 上：

   ```
   cd C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\
   ```

   在 git bash shell 中的 Windows 上，使用正斜杠：

   ```
   cd C:/Users/myusername/Documents/GitHub/Demos/demo-to-do/
   ```


<!-- if you cd to 
C:\Users\myusername\Documents\GitHub\Demos\
you would then specify
http://localhost:8080/demo-to-do/
but it's fine usually to serve out a single sample dir
but serving out the entire \Demos\ dir gives a useful dir listing at:
   http://10.0.1.8:8080
   http://127.0.0.1:8080
-->

   **启动服务器 (npx http-server) ：**

1. 输入命令 `npx http-server`：

   ```
   npx http-server
   ```

   本地 Web 服务器从端口 8080 开始。

   你可能会收到如下所示的消息：

   ```
   Need to install the following packages:
     http-server@14.1.1
   Ok to proceed? (y)
   ```

1. 输入 **y**。

   Windows 提示是否允许节点在网络上通信：

   ![允许节点在网络上通信](./install-images/allow-node-communicate-network.png)

1. 选中 **“专用网络** ”复选框，然后单击“ **允许访问** ”按钮。

   将显示有关服务器和 localhost URL 的信息，例如：

   ```
   Starting up http-server, serving ./
   
   Available on:
   http://10.0.1.8:8080
   http://127.0.0.1:8080
   Hit CTRL-C to stop the server
   ```
   
   显示的 URL 等效于 [http://localhost:8080/](http://localhost:8080/)。

接下来，请参阅[为Visual Studio Code使用 DevTools 扩展开始](./get-started.md)进行分步演练。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
