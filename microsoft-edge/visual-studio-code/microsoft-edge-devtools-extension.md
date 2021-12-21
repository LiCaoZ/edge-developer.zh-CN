---
title: 用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展
description: 使用 Microsoft Edge 开发人员工具扩展Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， vs code， visual studio code， Microsoft Edge 开发人员工具， Microsoft Edge 开发人员工具扩展
ms.date: 10/26/2021
ms.openlocfilehash: 793707c6f93ace5711b9de870797bcd8277ec0fe
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286833"
---
# <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

<!-- lexicon (except when quoting a UI string):
Microsoft Edge DevTools extension for Visual Studio Code
Microsoft Edge DevTools extension
-->

开发人员Microsoft Edge开发人员工具Visual Studio Code允许你从浏览器内使用浏览器的元素工具和网络Visual Studio Code。 **** ****  如果不离开Visual Studio Code，Microsoft Edge DevTools 使用以下功能连接到 Microsoft Edge 实例：
* 查看运行时 HTML 结构。
* 更改布局。
* 更改 CSS (样式) 。
* 读取控制台消息。
* 查看网络请求。

> [!NOTE]
> 开发人员Microsoft Edge开发人员工具扩展需要Microsoft Edge。  此扩展在 Microsoft Edge 80.0.361.48 及更高版本中受支持。

在Visual Studio Code中，有多种方法可以打开 Microsoft Edge DevTools 扩展：
* 从**活动栏 。**
* 来自 JavaScript 调试器。

在Visual Studio Code中，此扩展由多个变体引用：
*  **Microsoft Edge开发人员工具Visual Studio Code** - 如扩展市场的详细信息中所示**的全名**。
*  **Microsoft Edge工具VS Code**扩展 - 在扩展市场中搜索时列出的**扩展**。
*  **Microsoft Edge工具**- 活动栏中的图标**工具提示**。
*  **Edge DevTools** - 选项卡名称。

本文使用名称"Microsoft Edge DevTools 扩展"，UI 文本除外。


<!-- ====================================================================== -->
## <a name="installing-the-microsoft-edge-devtools-extension"></a>安装 Microsoft Edge DevTools 扩展

若要从内部安装扩展Visual Studio Code，请参阅 Microsoft Edge [DevTools 扩展Visual Studio Code。](index.md#the-microsoft-edge-devtools-extension-for-visual-studio-code)

或者，你可以[从 Microsoft Edge 应用商店下载 Visual Studio DevTools](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)扩展。  您可以在以下[时间查看GitHub。](https://github.com/microsoft/vscode-edge-devtools)

### <a name="updating-the-extension"></a>更新扩展

Microsoft Visual Studio Code 会自动更新扩展。  若要手动更新扩展，请参阅 [手动更新扩展](https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually)。


<!-- ====================================================================== -->
## <a name="opening-microsoft-edge-devtools-within-visual-studio-code"></a>打开Microsoft Edge中的 DevTools Visual Studio Code

若要打开工具面板，请在活动**栏中**选择"工具Microsoft Edge**图标**。

使用 Microsoft Edge DevTools 扩展，可以轻松启动 Edge 实例或生成文件以 `launch.json` 自动执行调试工作流。

:::image type="content" source="./media/edge-devtools-for-vscode-extension-icon.png" alt-text="Microsoft Edge开发人员工具Visual Studio Code扩展" lightbox="./media/edge-devtools-for-vscode-extension-icon.png":::

选择 **"启动实例**"将打开浏览器窗口，并打开"Edge **DevTools"** 选项卡Visual Studio Code。

:::image type="content" source="./media/edge-devtools-for-vscode-launch-instance.png" alt-text="选择&quot;启动实例&quot;以在浏览器中打开Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-launch-instance.png":::

使用 Microsoft Edge中的 DevTools 扩展Visual Studio Code中检查 HTML 元素Microsoft Edge。 例如，选择成功 **！** 在浏览器中，注意"元素"工具将打开，并突出显示 HTML。

:::image type="content" source="./media/edge-devtools-for-vscode-elements.png" alt-text="突出显示 HTML 的元素工具" lightbox="./media/edge-devtools-for-vscode-elements.png":::


<!-- ====================================================================== -->
## <a name="modes-for-using-microsoft-edge-devtools-in-visual-studio-code"></a>在开发人员Microsoft Edge开发人员工具Visual Studio Code

可以在以下三种模式之一中使用此扩展：
* 启动Microsoft Edge窗口中的 Web 应用程序，然后转到 Web 应用程序。
* 附加到运行实例的 Microsoft Edge。
* 打开新实例的 Microsoft Edge 内部Visual Studio Code。

每种模式都需要您从本地 Web 服务器（从任务或命令行Visual Studio Code Web 应用程序提供服务）。  使用文件内的 URL 参数 `launch.json` 告知用户Visual Studio Code打开哪个 URL。


<!-- ====================================================================== -->
## <a name="opening-a-new-browser-instance"></a>打开新的浏览器实例

若要从网站打开浏览器Visual Studio Code：

1. 在活动**栏上**，选择 **"Microsoft Edge工具"。**

1. 在 **"Microsoft Edge：目标"面板上**，选择"**启动实例"。**  Microsoft Edge打开，并显示包含详细信息指南的默认页面。  此外 **，Edge DevTools**选项卡和面板显示在 Visual Studio Code，其中包含**欢迎**、**元素****和网络**工具。

    :::image type="content" source="./media/edge-devtools-for-vscode-targets-launch.png" alt-text="Microsoft Edge中打开开发人员面板Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-targets-launch.png":::

1. 在Microsoft Edge地址栏中，转到要调试的项目的 URL。


<!-- ====================================================================== -->
## <a name="changing-the-default-page-to-your-project-website"></a>将默认页面更改到项目网站

若要调试项目，您可能需要更改在 Visual Studio Code 中打开的默认Microsoft Edge页面。  若要将默认页面更改为项目的网站，请执行以下操作：

1.  在Visual Studio Code中，选择"**文件**  >  **""新建窗口"。**  请注意，没有打开的文件夹。

1.  在活动**栏上**，选择 **"Microsoft Edge工具"。**

1.  在 **"Microsoft Edge：目标"** 面板中，选择 **"打开文件夹"** 链接。

1.  选择具有新的默认页面的项目文件夹，以在 Visual Studio Code 中开始调试。

    第一次打开文件夹时，必须确认信任此文件夹中文件的作者。  还可以选中"信任 **父文件夹中所有文件的作者"复选框**。

    :::image type="content" source="./media/edge-devtools-for-vscode-trust.png" alt-text="是否信任此文件夹的文件的作者？" lightbox="./media/edge-devtools-for-vscode-trust.png":::

    第一次完成此过程时，还必须再次选择Microsoft Edge**工具**"。

    The **Microsoft Edge Tools： Targets** panel now displays two buttons： Launch **Instance** and **Generate launch.json**.

    :::image type="content" source="./media/edge-devtools-for-vscode-targets-buttons.png" alt-text="&quot;Microsoft Edge工具： 目标&quot;面板显示&quot;启动实例&quot;和&quot;生成 launch.json&quot;按钮" lightbox="./media/edge-devtools-for-vscode-targets-buttons.png":::

1.  选择 **"生成 launch.json"** 以 `launch.json` 在项目中创建 。

1.  在 `launch.json` 中，添加项目的 URL。 如果将 URL 留空，将显示默认页面。

1.  保存 `launch.json`。

1.  选择 **"Project"** 以验证Microsoft Edge是否打开并显示您输入的 URL。  此外，DevTools 将在Visual Studio Code。


<!-- ====================================================================== -->
## <a name="changing-the-extension-settings"></a>更改扩展设置

可以在扩展中自定义 devTools Visual Studio Code。

自定义设置：

1.  在Visual Studio Code"活动**栏"上**，选择"Microsoft Edge**工具"。**

1. 在**Microsoft Edge工具**目标"中，选择"更多操作 (...) 目标"一词的右侧，然后选择  >  ****"打开**设置"。** **** ****  注意：如果使用鼠标，若要访问"其他操作" (...) ，请选择"目标"窗格或将鼠标悬停在**** 该窗格上。 ****

    :::image type="content" source="./media/edge-tools-open-settings-icon.msft.png" alt-text="&quot;工具Microsoft Edge目标&quot;面板上的&quot;更多操作&quot;图标，用于更改 DevTools 扩展的设置" lightbox="./media/edge-tools-open-settings-icon.msft.png":::

### <a name="reloading-the-extension-after-changing-settings"></a>更改设置后重新加载扩展

某些设置有一条注释，**指出 (后需要重新加载) 。 **  使此类设置生效：

1.  关闭扩展打开的浏览器，或在"工具Microsoft Edge**** 窗格中，选择"关闭实例  >  ******** `X` () "。  此操作还会自动关闭 **"Edge DevTools"** 选项卡。

1.  在 **"Microsoft Edge**  >  **目标"** 窗格中，选择"**启动实例"** 按钮。  Microsoft Edge，并显示 **"Edge DevTools"** 选项卡。


<!-- ====================================================================== -->
## <a name="viewing-the-changelog-for-changes-made-to-the-extension"></a>查看更改日志，查看对扩展所做的更改

可以查看对扩展所做的更改。

若要查看更改日志，请进行以下设置：

1.  在Visual Studio Code"活动**栏"上**，选择"Microsoft Edge**工具"。**

1. In **Microsoft Edge Tools**  >  **Targets，** select More **Actions** (...) to the right of the **word TARGETS，** and then select **View Changelog**.  注意：如果使用鼠标，若要访问"其他操作" (...) ，请选择"目标"窗格或将鼠标悬停在**** 该窗格上。 ****

    :::image type="content" source="./media/view-changelog-menuitem.msft.png" alt-text="&quot;查看更改日志&quot;菜单项，以查看对扩展所做的更改" lightbox="./media/view-changelog-menuitem.msft.png":::

或者，在浏览器中，转到 [存储库中的更改](https://github.com/microsoft/vscode-edge-devtools/blob/main/CHANGELOG.md) `vscode-edge-devtools` 日志文件。


<!-- ====================================================================== -->
## <a name="changing-to-headless-mode"></a>更改为无头模式

默认情况下，扩展启动Microsoft Edge新窗口中，该窗口在任务栏上显示另一个浏览器图标。

选择 **"切换屏幕视频** "在编辑器中显示浏览器，或隐藏浏览器（如果已显示）。

:::image type="content" source="./media/edge-devtools-for-vscode-toggle-screencast.png" alt-text="切换屏幕视频以在编辑器内查看浏览器" lightbox="./media/edge-devtools-for-vscode-toggle-screencast.png":::

若要仅在视频内使用屏幕Visual Studio Code，请选择 **"设置**  >  **无头模式"。**

:::image type="content" source="./media/edge-devtools-for-vscode-settings-headless.png" alt-text="若要仅在视频内使用屏幕Visual Studio Code，设置 >无头模式" lightbox="./media/edge-devtools-for-vscode-settings-headless.png":::


<!-- ====================================================================== -->
## <a name="opening-source-files-from-the-elements-tool"></a>从"元素"工具打开源文件

**Elements**工具的一个功能是，它显示将样式和事件处理程序应用到 DOM 树中选定节点的源文件。  源文件以指向 URL 的链接的形式显示。  选择链接将在编辑器中打开Visual Studio Code文件。

:::image type="content" source="./media/edge-devtools-for-vscode-elements-files.png" alt-text="从元素工具打开源文件" lightbox="./media/edge-devtools-for-vscode-elements-files.png":::


<!-- ====================================================================== -->
## <a name="setting-up-your-project-to-show-live-changes-in-the-extension"></a>设置项目以显示扩展中的实时更改

默认情况下，Microsoft Edge开发人员工具扩展不会在编写代码时跟踪实时更改。  如果希望浏览器在您更改文件时自动刷新，请设置实时 _重新加载_ 环境，如下所示。

本示例显示硬盘驱动器上名为 的生产文件文件夹 `my-project` 。  在以下步骤中，如果不同 `my-project` ，请更改为文件夹名称。

1. 安装Node.js `reload` 和 npm 程序包，如下所示：
    1. 下载并安装[Node.js。 ](https://www.nodejs.org)
    1. 若要安装 [重新加载 npm 包](https://www.npmjs.com/package/reload?activeTab=readme)，请打开命令提示符并运行 `npm install reload -g` 以全局安装该包。

1. 将扩展附加到实时重新加载项目，如下所示：
    1. 导航到 `my-project` 终端窗口中的文件夹，然后运行 `reload` 以启动本地服务器。
    1. 在Visual Studio Code中，打开 `my-project` 文件夹。
    1. 转到扩展并启动Microsoft Edge浏览器实例。
    1. 在Microsoft Edge中，转到 `localhost:8080/{file name you want to open}` 。

保存在此文件夹中的所有更改现在将触发浏览器刷新。


<!-- ====================================================================== -->
## <a name="syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing"></a>使用 CSS 镜像编辑同步样式工具中的实时更改

DevTools Microsoft Edge样式工具非常适用于调试和调整 CSS 属性样式。  一个问题就是，虽然这些更改在浏览器中实时显示，但是它们不会反映在源文件中。  这意味着在 CSS 调试会话结束时，您需要将更改的内容复制并粘贴回源文件中。

CSS 镜像编辑是开发人员工具扩展的实验Microsoft Edge，可解决此问题。  打开镜像编辑时，在 DevTools 的样式工具中进行的任何更改也会更改工作区中的文件。

在下面的示例中，我们已在 Visual Studio Code `index.html` 中打开，Microsoft Edge DevTools 扩展处于打开状态。  当我们在 CSS 选择器中选择弹性框图标并将 更改为 时，我们不仅可以看到浏览器和 `.searchbar` `flex-direction` `column` DevTools 中的更改，Visual Studio Code 还会自动导航到正确的样式表文件和相应的行号，并插入 `flex-direction: column` CSS 代码。 

:::image type="content" source="./media/css-mirror-editing-start.msft.png" alt-text="在样式工具中选择弹性框图标以创建 CSS 更改" lightbox="./media/css-mirror-editing-start.msft.png":::

:::image type="content" source="./media/css-mirror-editing-changed-file.msft.png" alt-text="更改 CSS 设置在正确的 CSS 源文件中创建了一个新代码行" lightbox="./media/css-mirror-editing-changed-file.msft.png":::

可以在样式工具中编辑任何选择器或创建新选择器，所有更改都将镜像到正确的 CSS 源文件中。 扩展仅更改文件，不会自动将更改保存回硬盘驱动器。 这是一种安全措施，用于确保不会意外覆盖任何代码。

您可以使用扩展的目标窗格中的按钮，或者通过使用命令菜单并查找 来启用和禁用 CSS 镜像编辑 `mirror` 。

:::image type="content" source="./media/css-mirror-editing-button.msft.png" alt-text="在扩展面板中，可以找到 CSS 镜像编辑的快速说明、打开和关闭功能的按钮以及向我们提供反馈的链接。" lightbox="./media/css-mirror-editing-button.msft.png":::

:::image type="content" source="./media/css-mirror-editing-command.msft.png" alt-text="使用命令菜单并搜索镜像，可以聚焦 CSS 镜像编辑视图并启用和关闭功能。" lightbox="./media/css-mirror-editing-command.msft.png":::

我们将继续改进此功能，并针对 CSS 镜像编辑的 GitHub 设置跟踪问题，我们[](https://github.com/microsoft/vscode-edge-devtools/issues/476)欢迎您提供反馈。


<!-- ====================================================================== -->
## <a name="device-emulation-in-the-screencast"></a>屏幕广播中的设备模拟

设备仿真是编辑器中屏幕广播浏览器的一项功能。  这允许你模拟手机或平板电脑等设备。  这可用于在不同设备上测试网站的布局。

:::image type="content" source="./media/edge-devtools-for-vscode-device-dropdown.msft.png" alt-text="&quot;Edge DevTools： Screencast&quot;选项卡中的&quot;设备&quot;下拉列表。" lightbox="./media/edge-devtools-for-vscode-device-dropdown.msft.png":::

你可以从不同设备列表中选择，以在地址栏旁边的屏幕视频中模拟。  默认设备是台式计算机。

:::image type="content" source="./media/edge-devtools-for-vscode-device-list.msft.png" alt-text="可以在扩展的屏幕广播中打开可模拟的设备列表" lightbox="./media/edge-devtools-for-vscode-device-list.msft.png":::

如果选择模拟的设备是触摸设备，屏幕视频将自动切换到触摸屏模式。 可以通过单击列表旁边的按钮来旋转模拟设备的方向：

:::image type="content" source="./media/edge-devtools-for-vscode-simulated-iphone.msft.png" alt-text="显示仿真文档 5 中当前文档的屏幕iPhone大小正确且具有模拟触摸界面。" lightbox="./media/edge-devtools-for-vscode-simulated-iphone.msft.png":::


<!-- ====================================================================== -->
## <a name="inline-and-live-issue-analysis"></a>内联和实时问题分析

源代码中的问题用波浪下划线突出显示。 可以检查该问题并获取有关问题所在、如何修复以及在何处查找详细信息的详细信息。  若要检查该问题，请选择具有波浪下划线的代码：

:::image type="content" source="./media/edge-devtools-for-vscode-inline-issue-reporting.msft.png" alt-text="一段代码内报告的辅助功能问题，用于显示如何修复该问题以及在何处查找详细信息。" lightbox="./media/edge-devtools-for-vscode-inline-issue-reporting.msft.png":::

若要查看文件的所有问题，请选择"查看**问题"。**

:::image type="content" source="./media/edge-devtools-for-vscode-navigating-issues.msft.png" alt-text="源代码中一个突出显示的问题，其中具有一个导航栏，用于解释该问题以及要移动到下一个和之前问题的按钮。" lightbox="./media/edge-devtools-for-vscode-navigating-issues.msft.png":::

下 **面板** 中的"问题"选项卡列出了在当前项目中发现的所有问题：

:::image type="content" source="./media/edge-devtools-for-vscode-issues-in-lower-panel.msft.png" alt-text="项目面板下面板中的&quot;Visual Studio Code&quot;选项卡，列出在项目文件中发现的所有问题" lightbox="./media/edge-devtools-for-vscode-issues-in-lower-panel.msft.png":::

编辑代码时，会实时评估问题。  键入时，将获取有关发现的任何问题以及如何解决这些问题的反馈。

:::image type="content" source="./media/edge-devtools-for-vscode-live-issue-reporting.msft.png" alt-text="在输出元素上说明的可能问题" lightbox="./media/edge-devtools-for-vscode-live-issue-reporting.msft.png":::


<!-- ====================================================================== -->
## <a name="browser-debugging-with-microsoft-edge-devtools-integration-in-visual-studio-code"></a>使用 Microsoft Edge 中的 DevTools 集成进行浏览器Visual Studio Code

JavaScript 调试内置于Visual Studio Code。  可以在 Chrome、Microsoft Edge或 Node.js调试，而无需安装任何其他扩展。  如果你使用 Microsoft Edge 调试，你可以从 JavaScript Microsoft Edge启动 DevTools。

1.  若要开始调试，请执行下列任一操作：
    * 选择**F5，** 或在菜单栏上选择"**调试**"图标，然后选择"**运行并调试"。**
    * 打开"Visual Studio Code"命令调色板，然后选择"**调试：打开链接"。**

    :::image type="content" source="./media/edge-devtools-for-vscode-start-session.png" alt-text="从 JavaScript Microsoft Edge启动 DevTools" lightbox="./media/edge-devtools-for-vscode-start-session.png":::

1.  选择 **边缘**。  在调试工具栏上，注意" **检查"** 按钮。

    :::image type="content" source="./media/edge-devtools-for-vscode-inspect-button.png" alt-text="调试工具栏上的&quot;检查&quot;按钮" lightbox="./media/edge-devtools-for-vscode-inspect-button.png":::

1.  选择 **"检查**"以Microsoft Edge开发人员工具Visual Studio Code。

    首次选择"检查 **"** 时，编辑器会提示你安装扩展，Microsoft Edge[开发人员工具Visual Studio Code。](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)

    安装 Microsoft Edge工具扩展后，选择"检查"时Microsoft Edge将打开 DevTools Visual Studio Code。 ****

    :::image type="content" source="./media/edge-devtools-for-vscode-tools-inside.png" alt-text="&quot;检查&quot;按钮Microsoft Edge开发人员工具Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-tools-inside.png":::

    现在，您可以检查 DOM，更改 CSS，并查看浏览器中运行的项目的网络请求，而无需离开Visual Studio Code。

    您还可以使用编辑器中的调试控制台与浏览器中的文档进行交互。  你具有窗口对象的完全访问权限，并且可以使用[控制台实用程序 API。](/microsoft-edge/devtools-guide-chromium/console/utilities)

    :::image type="content" source="./media/edge-devtools-for-vscode-debug-console.png" alt-text="编辑器中的调试控制台与浏览器中打开的文档交互" lightbox="./media/edge-devtools-for-vscode-debug-console.png":::


### <a name="automatically-attaching-to-microsoft-edge-and-launching-devtools-in-visual-studio-code"></a>自动连接到 Microsoft Edge，并启动开发人员Visual Studio Code

1.  如果你想要自动附加到 Microsoft Edge，Microsoft Edge Visual Studio Code 中的 DevTools，请执行上述步骤，然后创建一个文件， `launch.json` 如下所示。

    选择**Microsoft Edge**类型。  在 `launch.json` 文件中，将 `pwa-msedge` 指定为 类型：

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

1.  在 `http://localhost:8080` 以上代码中更改 ，并确保变量 `{workspaceFolder}` 解析。

1.  选择" **检查"** 图标。  如果尚未安装 Microsoft Edge DevTools Visual Studio Code，"扩展"选项卡将打开并自动显示**** 要安装的扩展。

#### <a name="see-also"></a>另请参阅

*  [调试文章中](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)的_启动_配置Visual Studio Code。


<!-- ====================================================================== -->
## <a name="console-integration"></a>控制台集成

如果从运行和调试工作流启动扩展，Visual Studio Code[调试控制台](https://code.visualstudio.com/Docs/editor/debugging)会为你提供 DevTools 控制台[的所有功能](/microsoft-edge/devtools-guide-chromium/console/)。  你可以直接访问 Edge 实例的 Window 对象，并且可以使用所有 [控制台实用程序](/microsoft-edge/devtools-guide-chromium/console/utilities)。

:::image type="content" source="./media/edge-devtools-for-vscode-console-integration.png" alt-text="当从运行和调试工作流启动扩展时，DevTools 控制台可用" lightbox="./media/edge-devtools-for-vscode-console-integration.png":::


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-extension-team"></a>与开发人员工具扩展Microsoft Edge联系

通过向存储库 [提交问题](https://github.com/Microsoft/vscode-edge-devtools/issues/new) 发送 `vscode-edge-devtools` 反馈。

欢迎你做出贡献，帮助你更好地Microsoft Edge开发工具扩展。  在 [vscode-edge-devtools](https://github.com/Microsoft/vscode-edge-devtools) 存储库查找入门所需的一切。
