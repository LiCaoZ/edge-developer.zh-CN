---
description: 使用 Microsoft Edge 开发人员工具扩展Visual Studio Code。
title: Microsoft Edge适用于开发人员的 DevTools Visual Studio Code
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/21/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， vs code， visual studio code， Microsoft Edge 开发人员工具， Microsoft Edge 开发人员工具扩展
ms.openlocfilehash: c4840662bb025ba2cb38464adb5dd3028e1acee2
ms.sourcegitcommit: 0eca205728eeca1bd54b3ca34dfc81ec57cf16d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2021
ms.locfileid: "12083021"
---
# <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>Microsoft Edge适用于开发人员的 DevTools Visual Studio Code

使用 Microsoft Edge DevTools 扩展Visual Studio Code，你可以从 Visual Studio Code 内使用浏览器的元素工具和**** 网络Visual Studio Code。 ****  如果不离开Visual Studio Code，Microsoft Edge DevTools 连接到具有以下功能的 Microsoft Edge 实例：
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
<!-- follow this global convention for consistency; this is a quote of the UI tab name "Edge DevTools", but adding "Microsoft" -->


<!-- ====================================================================== -->
## <a name="installing-the-microsoft-edge-devtools-extension"></a>安装 Microsoft Edge DevTools 扩展

若要从内部安装扩展Visual Studio Code，请导航到 Microsoft Edge [DevTools 扩展Visual Studio Code。](index.md#the-microsoft-edge-devtools-extension-for-visual-studio-code) <!-- in the article _Visual Studio Code overview_. -->

或者，你可以[从 Microsoft Edge 应用商店下载 Visual Studio DevTools][VisualstudioMarketplaceElementsMicrosoftEdgeChromium]扩展。  您可以在以下[时间查看GitHub。][checkSourceCode]

### <a name="updating-the-extension"></a>更新扩展

Microsoft Visual Studio Code 会自动更新扩展。  若要手动更新扩展，请导航到"[手动更新扩展"。][VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]


<!-- ====================================================================== -->
## <a name="opening-microsoft-edge-devtools-within-visual-studio-code"></a>打开Microsoft Edge中的 DevTools Visual Studio Code

若要打开工具面板，请在活动**栏中**选择"工具Microsoft Edge**图标**。

使用 Microsoft Edge DevTools 扩展，可以轻松启动 Edge 实例或生成文件以自动 `launch.json` 执行调试工作流。

:::image type="complex" source="./media/edge-devtools-for-vscode-extension-icon.png" alt-text="Microsoft Edge开发工具Visual Studio Code扩展" lightbox="./media/edge-devtools-for-vscode-extension-icon.png":::
   Microsoft Edge开发工具Visual Studio Code扩展
:::image-end:::

选择 **"启动实例**"将打开浏览器窗口，并打开"Edge **DevTools"** 选项卡Visual Studio Code。

:::image type="complex" source="./media/edge-devtools-for-vscode-launch-instance.png" alt-text="选择&quot;启动实例&quot;以在 Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-launch-instance.png":::
   选择 **"启动实例**"以在 Visual Studio Code
:::image-end:::

使用 Microsoft Edge 中的 DevTools 扩展Visual Studio Code检查 HTML 元素Microsoft Edge。 例如，选择成功 **！** 在浏览器中，请注意，"元素"工具将打开，并突出显示 HTML。

:::image type="complex" source="./media/edge-devtools-for-vscode-elements.png" alt-text="突出显示 HTML 的元素工具" lightbox="./media/edge-devtools-for-vscode-elements.png":::
   突出显示 **HTML** 的元素工具
:::image-end:::


<!-- ====================================================================== -->
## <a name="modes-for-using-microsoft-edge-devtools-in-visual-studio-code"></a>在开发人员Microsoft Edge开发人员工具Visual Studio Code

<!-- todo: relate/link this list to the subsequent sections -->
可以在以下三种模式之一中使用此扩展：
* 在Microsoft Edge中启动 Web 应用程序，然后导航到 Web 应用程序。
* 附加到运行实例的 Microsoft Edge。
* 在文件内打开Microsoft Edge的新Visual Studio Code。

每种模式都需要从本地 Web 服务器（从任务或命令行Visual Studio Code Web 服务器启动）为 Web 应用程序提供服务。  使用文件内的 URL 参数 `launch.json` 告知用户Visual Studio Code打开哪个 URL。


<!-- ====================================================================== -->
## <a name="opening-a-new-browser-instance"></a>打开新的浏览器实例

若要从网站打开浏览器Visual Studio Code：

1. 在活动**栏上**，选择 **"Microsoft Edge工具"。**

1. 在 **"Microsoft Edge：目标"面板**上，选择"**启动实例"。**  Microsoft Edge打开，并显示包含详细信息指南的默认页面。  此外 **，Edge DevTools**面板显示在 Visual Studio Code，其中包含**欢迎**、**元素****和网络**工具。

    :::image type="complex" source="./media/edge-devtools-for-vscode-targets-launch.png" alt-text="Microsoft Edge和 DevTools 面板在 Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-targets-launch.png":::
       Microsoft Edge和 DevTools 面板在 Visual Studio Code :::image-end:::

1. 在Microsoft Edge地址栏中，导航到要调试的项目的 URL。


<!-- ====================================================================== -->
## <a name="changing-the-default-page-to-your-project-website"></a>将默认页面更改到项目网站

若要调试项目，您可能需要更改在 Visual Studio Code 中打开的默认Microsoft Edge页面。  若要将默认页面更改为项目的网站，请执行以下操作：
1.  在Visual Studio Code中，选择"**文件**  >  **""新建窗口"。**  请注意，没有打开的文件夹。
1.  在活动**栏上**，选择 **"Microsoft Edge工具"。**
1.  在 **"Microsoft Edge：目标"** 面板中，选择**打开文件夹**链接。
1.  选择具有新的默认页面的项目文件夹，以在 Visual Studio Code 中开始调试。

    第一次打开文件夹时，必须确认信任此文件夹中文件的作者。  还可以选中"信任 **父文件夹中所有文件的作者"复选框**。

    :::image type="complex" source="./media/edge-devtools-for-vscode-trust.png" alt-text="是否信任此文件夹的文件的作者？" lightbox="./media/edge-devtools-for-vscode-trust.png":::
       是否信任此文件夹的文件的作者？
    :::image-end:::

    第一次完成此过程时，还必须再次选择Microsoft Edge**工具**"。

    The **Microsoft Edge Tools： Targets** panel now displays two buttons： Launch **Instance** and **Generate launch.json**.

    :::image type="complex" source="./media/edge-devtools-for-vscode-targets-buttons.png" alt-text="&quot;Microsoft Edge工具： 目标&quot;面板显示&quot;启动实例&quot;和&quot;生成 launch.json&quot;按钮" lightbox="./media/edge-devtools-for-vscode-targets-buttons.png":::
       The **Microsoft Edge Tools： Targets** panel displays Launch **Instance** and **Generate launch.json** buttons
    :::image-end:::

1.  选择 **"生成 launch.json"** 以 `launch.json` 在项目中创建 。
1.  在 `launch.json` 中，添加项目的 URL。 如果将 URL 留空，将显示默认页面。
1.  保存 `launch.json`。
1.  选择 **"Project"** 以验证Microsoft Edge是否打开并显示您输入的 URL。  此外，DevTools 将在 Visual Studio Code。


<!-- ====================================================================== -->
## <a name="changing-the-extension-settings"></a>更改扩展设置

在版本 1.1.6 或更高版本中，可以在扩展中自定义 Visual Studio Code 工具。

自定义设置：

1.  In Visual Studio Code， on the **Activity Bar，** select **Microsoft Edge Tools**.

1. 在**Microsoft Edge工具**目标"中，选择"更多操作 (...) 目标"一词的右侧，然后选择  >  ****"打开**设置"。** **** ****  注意：如果使用鼠标，若要访问"其他操作" (...) ，请选择"目标"窗格或将鼠标悬停在**** 该窗格上。 ****

    :::image type="complex" source="./media/edge-tools-open-settings-icon.msft.png" alt-text="&quot;工具Microsoft Edge目标&quot;面板上的&quot;更多操作&quot;图标，用于更改 DevTools 扩展的设置" lightbox="./media/edge-tools-open-settings-icon.msft.png":::
       "**工具**Microsoft Edge**目标**"面板上的"更多操作"图标，用于更改 DevTools 扩展的设置 :::image-end:::

### <a name="reloading-the-extension-after-changing-settings"></a>更改设置后重新加载扩展

某些设置有一条注释 **， (更改后需要重新加载) 。 **  使此类设置生效：

1.  关闭扩展打开的浏览器，或在"工具Microsoft Edge**** 窗格中，选择"关闭实例  >  ******** `X` () "。  此操作还会自动关闭 **"Edge DevTools"** 选项卡。

1.  在 **"Microsoft Edge**  >  **目标"** 窗格中，选择 **"启动实例"** 按钮。  Microsoft Edge，并显示 **"Edge DevTools"** 选项卡。


<!-- ====================================================================== -->
## <a name="viewing-the-changelog-for-changes-made-to-the-extension"></a>查看更改日志，查看对扩展所做的更改

可以查看对扩展所做的更改。 若要查看更改日志，请执行以下步骤。

1.  In Visual Studio Code， on the **Activity Bar，** select **Microsoft Edge Tools**.

1. 在**Microsoft Edge目标**"中，选择"更多操作 (...) 目标"一词的右侧，然后选择  >  ****"**查看更改日志"。** **** ****  注意：如果使用鼠标，若要访问"其他操作" (...) ，请选择"目标"窗格或将鼠标悬停在**** 该窗格上。 ****

    :::image type="complex" source="./media/view-changelog-menuitem.msft.png" alt-text="&quot;查看更改日志&quot;菜单项，以查看对扩展所做的更改" lightbox="./media/view-changelog-menuitem.msft.png":::
       " **查看更改日志** "菜单项，以查看对扩展所做的更改 :::image-end:::

或者，在浏览器中，导航到存储库中的 [更改][GithubMicrosoftVscodeEdgeDevtoolsChangelog] `vscode-edge-devtools` 日志文件。


<!-- ====================================================================== -->
## <a name="changing-to-headless-mode"></a>更改为无头模式

默认情况下，扩展启动Microsoft Edge新窗口中，这将在任务栏上显示另一个浏览器图标。

选择 **"切换屏幕视频** "在编辑器中显示浏览器，或隐藏浏览器（如果已显示）。

:::image type="complex" source="./media/edge-devtools-for-vscode-toggle-screencast.png" alt-text="切换屏幕视频以在编辑器内查看浏览器" lightbox="./media/edge-devtools-for-vscode-toggle-screencast.png":::
   切换屏幕视频以在编辑器内查看浏览器
:::image-end:::

若要仅在视频内使用屏幕**Visual Studio Code，设置**  >  **无头模式。**

:::image type="complex" source="./media/edge-devtools-for-vscode-settings-headless.png" alt-text="若要仅在视频内使用屏幕Visual Studio Code，设置 >无头模式" lightbox="./media/edge-devtools-for-vscode-settings-headless.png":::
   若要仅在视频内使用屏幕**Visual Studio Code，设置**  >  **无头模式**
:::image-end:::


<!-- ====================================================================== -->
## <a name="opening-source-files-from-the-elements-tool"></a>从"元素"工具打开源文件

**Elements**工具的一个功能是，它显示将样式和事件处理程序应用到 DOM 树中选定节点的源文件。  源文件以指向 URL 的链接的形式显示。  选择链接将在编辑器中打开Visual Studio Code文件。

:::image type="complex" source="./media/edge-devtools-for-vscode-elements-files.png" alt-text="从元素工具打开源文件" lightbox="./media/edge-devtools-for-vscode-elements-files.png":::
   从元素工具打开源文件
:::image-end:::


<!-- ====================================================================== -->
## <a name="setting-up-your-project-to-show-live-changes-in-the-extension"></a>设置项目以显示扩展中的实时更改

默认情况下，Microsoft Edge开发人员工具扩展不会在编写代码时跟踪实时更改。  如果希望浏览器在您更改文件时自动刷新，请设置实时 _重新加载_ 环境，如下所示。

本示例显示硬盘驱动器上名为 的生产文件文件夹 `my-project` 。  在以下步骤中，如果不同 `my-project` ，请更改为文件夹名称。

1. 安装Node.js `reload` 和 npm 程序包，如下所示：
    1. 下载并安装 [Node.js][NodeJS]。
    1. 若要安装 [重新加载 npm 包][NPM]，请打开命令提示符并运行 `npm install reload -g` 以全局安装该包。

1. 将扩展附加到实时重新加载项目，如下所示：
    1. 导航到 `my-project` 终端窗口中的文件夹，然后运行 `reload` 以启动本地服务器。
    1. 在Visual Studio Code中，打开 `my-project` 文件夹。
    1. 转到扩展并启动Microsoft Edge浏览器实例。
    1. 在Microsoft Edge中，将扩展导航到 `localhost:8080/{file name you want to open}` 。

保存在此文件夹中的所有更改现在将触发浏览器刷新。


<!-- ====================================================================== -->
## <a name="syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing"></a>使用 CSS 镜像编辑同步样式工具中的实时更改

DevTools Microsoft Edge样式工具非常适用于调试和调整 CSS 属性样式。  一个问题就是，虽然这些更改在浏览器中实时显示，但是它们不会反映在源文件中。  这意味着在 CSS 调试会话结束时，您需要将更改的内容复制并粘贴回源文件中。

CSS 镜像编辑是开发人员工具扩展的实验Microsoft Edge，可解决此问题。  打开镜像编辑时，在 DevTools 的样式工具中进行的任何更改也会更改工作区中的文件。

在下面的示例中，我们当前在 Visual Studio Code 中打开，并且 `index.html` Edge DevTools 扩展处于打开状态。  当我们在 CSS 选择器中选择弹性框图标并将 更改为 时，我们不仅会在浏览器和 `.searchbar` `flex-direction` `column` DevTools 中看到更改，VS Code 还会自动导航到正确的样式表文件和相应的行号，并插入 `flex-direction: column` CSS 代码。

:::image type="complex" source="./media/css-mirror-editing-start.msft.png" alt-text="在样式工具中选择弹性框图标以创建 CSS 更改" lightbox="./media/css-mirror-editing-start.msft.png":::
   在样式工具中选择弹性框图标以创建 CSS 更改
:::image-end:::

:::image type="complex" source="./media/css-mirror-editing-changed-file.msft.png" alt-text="更改 CSS 设置在正确的 CSS 源文件中创建了一个新代码行" lightbox="./media/css-mirror-editing-changed-file.msft.png":::
   更改 CSS 设置在正确的 CSS 源文件中创建了一个新代码行
:::image-end:::

可以在样式工具中编辑任何选择器或创建新选择器，所有更改都将镜像到正确的 CSS 源文件中。 扩展名仅更改文件，不会自动将更改保存回硬盘。 这是一种安全措施，用于确保不会意外覆盖任何代码。

您可以使用扩展的目标窗格中的按钮，或者通过使用命令菜单并查找 来启用和禁用 CSS 镜像编辑 `mirror` 。

:::image type="complex" source="./media/css-mirror-editing-button.msft.png" alt-text="在扩展面板中，可以找到 CSS 镜像编辑的快速说明、打开和关闭功能的按钮以及向我们提供反馈的链接。" lightbox="./media/css-mirror-editing-button.msft.png":::
   在扩展面板中，可以找到 CSS 镜像编辑的快速说明、打开和关闭功能的按钮以及向我们提供反馈的链接。
:::image-end:::

:::image type="complex" source="./media/css-mirror-editing-command.msft.png" alt-text="使用命令菜单并搜索镜像，可以聚焦 CSS 镜像编辑视图并启用和关闭功能。" lightbox="./media/css-mirror-editing-command.msft.png":::
   使用命令菜单并搜索镜像，可以聚焦 CSS 镜像编辑视图并启用和关闭功能。
:::image-end:::

我们将继续改进此功能，并针对 CSS 镜像编辑设置跟踪GitHub[问题][CSSMirrorEditingTracking]，我们欢迎您提供反馈。


<!-- ====================================================================== -->
## <a name="browser-debugging-with-microsoft-edge-devtools-integration-in-visual-studio-code"></a>使用 Microsoft Edge 中的 DevTools 集成的浏览器Visual Studio Code

JavaScript 调试现已内置到 Visual Studio Code。  从版本 1.5.7 Visual Studio Code，无需安装任何其他扩展，即可在 Chrome、Microsoft Edge 或 Node.js 中调试。  如果你使用 Microsoft Edge 调试，你可以从 JavaScript Microsoft Edge启动 DevTools。

1. 若要启动会话，请使用以下任一方法：
    * 选择**F5，** 或在菜单栏上选择"**调试**"图标，然后选择"**运行并调试"。**
    * 打开"Visual Studio Code"命令调色板，然后选择"**调试：打开链接"。**

    :::image type="complex" source="./media/edge-devtools-for-vscode-start-session.png" alt-text="从 JavaScript Microsoft Edge启动 DevTools" lightbox="./media/edge-devtools-for-vscode-start-session.png":::
       从 JavaScript Microsoft Edge启动 DevTools :::image-end:::

1. 选择 **边缘**。  在调试工具栏上，注意" **检查"** 按钮。

    :::image type="complex" source="./media/edge-devtools-for-vscode-inspect-button.png" alt-text="调试工具栏上的&quot;检查&quot;按钮" lightbox="./media/edge-devtools-for-vscode-inspect-button.png":::
       调试 **工具栏** 上的"检查"按钮 :::image-end:::

1. 选择 **"检查**"以Microsoft Edge开发人员工具Visual Studio Code。
    首次选择"检查 **"** 时，编辑器会提示你安装 Microsoft Edge[开发人员工具Visual Studio Code][VisualstudioMarketplaceElementsMicrosoftEdgeChromium]扩展。

    安装 Microsoft Edge工具扩展后，当你选择"检查"时，Microsoft Edge将打开**** DevTools Visual Studio Code。

    :::image type="complex" source="./media/edge-devtools-for-vscode-tools-inside.png" alt-text="&quot;检查&quot;按钮Microsoft Edge开发人员工具Visual Studio Code" lightbox="./media/edge-devtools-for-vscode-tools-inside.png":::
       "**检查"** 按钮Microsoft Edge开发人员工具Visual Studio Code :::image-end:::

    现在，你可以检查 DOM，更改 CSS，并查看在浏览器中运行的项目的网络请求，而无需离开Visual Studio Code。

    您还可以使用编辑器中的调试控制台与浏览器中的文档进行交互。  你具有窗口对象的完全访问权限，并且可以使用[控制台实用程序 API。][ConsoleUtilitiesAPI]

    :::image type="complex" source="./media/edge-devtools-for-vscode-debug-console.png" alt-text="编辑器中的调试控制台与浏览器中打开的文档交互" lightbox="./media/edge-devtools-for-vscode-debug-console.png":::
       编辑器中的调试控制台与浏览器中打开的文档交互 :::image-end:::


### <a name="automatically-attaching-to-microsoft-edge-and-launching-devtools-in-visual-studio-code"></a>自动附加到 Microsoft Edge，并启动开发人员Visual Studio Code

1.  如果你想要自动附加到 Microsoft Edge，Microsoft Edge Visual Studio Code中的 DevTools，请执行上述步骤，然后创建一个文件 `launch.json` ，如下所示。

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
                "webRoot&quot;: &quot;${workspaceFolder}"
            }
        ]
    }
    ```

1.  在 `http://localhost:8080` 以上代码中更改 ，并确保变量 `{workspaceFolder}` 解析。

1.  选择" **检查"** 图标。  如果尚未安装 Microsoft Edge DevTools Visual Studio Code，"扩展"选项卡将打开并自动显示要**** 安装的扩展。 <!-- this step was stray; move? -->

#### <a name="see-also"></a>另请参阅

*  [在调试][launchJSON]_文章中启动_配置Visual Studio Code。


<!-- ====================================================================== -->
## <a name="console-integration"></a>控制台集成

如果从运行和调试工作流启动扩展，Visual Studio Code[调试控制台][DebugConsoleVSCode]会为你提供 DevTools 控制台[的所有功能][EdgeDevToolsConsole]。  你可以直接访问 Edge 实例的 Window 对象，并且可以使用所有 [控制台实用程序][ConsoleUtilities]。

:::image type="complex" source="./media/edge-devtools-for-vscode-console-integration.png" alt-text="当从运行和调试工作流启动扩展时，DevTools 控制台可用" lightbox="./media/edge-devtools-for-vscode-console-integration.png":::
   当从运行和调试工作流启动扩展时，DevTools 控制台**可用**
:::image-end:::


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-extension-team"></a>与开发人员工具扩展Microsoft Edge联系

通过向存储库 [提交问题][GithubMicrosoftVscodeEdgeDevtoolsNewIssue] 发送 `vscode-edge-devtools` 反馈。

如果你希望帮助使开发工具扩展Microsoft Edge，欢迎你做出贡献。  在 [vscode-edge-devtools][GithubMicrosoftVscodeEdgeDevtools] 存储库查找入门所需的一切。


<!-- ====================================================================== -->
<!-- links -->
[Contact]: ../contact.md "联系Microsoft Edge团队|Microsoft Edge开发人员文档"
[ConsoleUtilitiesAPI]: /microsoft-edge/devtools-guide-chromium/console/utilities "控制台实用程序 API 参考 | Microsoft Docs"
<!-- external links -->
[VisualstudioCode]: https://code.visualstudio.com "Visual Studio 代码"
[VisualStudioCodeDocs]: https://code.visualstudio.com/Docs "文档|Visual Studio Code"
[CSSMirrorEditingTracking]: https://github.com/microsoft/vscode-edge-devtools/issues/476 "CSS 镜像编辑：已知问题和反馈 ·问题#476 ·microsoft/vscode-edge-devtools"
[GithubMicrosoftVscodeEdgeDevtools]: https://github.com/Microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | GitHub"
[GithubMicrosoftVscodeEdgeDevtoolsChangelog]: https://github.com/microsoft/vscode-edge-devtools/blob/main/CHANGELOG.md "Changelog 文件 - vscode-edge-devtools |GitHub"
[GithubMicrosoftVscodeEdgeDevtoolsNewIssue]: https://github.com/Microsoft/vscode-edge-devtools/issues/new "新问题 - microsoft/vscode-edge-devtools |GitHub"
[VisualstudioCodeDocsEditorExtensionGalleryUpdateExtensionManually]: https://code.visualstudio.com/docs/editor/extension-gallery#_update-an-extension-manually "手动更新扩展 - Extension Marketplace | Visual Studio Code"

[VisualstudioMarketplaceElementsMicrosoftEdgeChromium]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Developer Tools for Visual Studio Code | Visual Studio Marketplace"

[checkSourceCode]: https://github.com/microsoft/vscode-edge-devtools "microsoft/vscode-edge-devtools | GitHub"

[launchJSON]: https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations "启动配置|在 Visual Studio Code"

[DebugConsoleVSCode]: https://code.visualstudio.com/Docs/editor/debugging "在 Visual Studio Code"

[EdgeDevToolsConsole]: /microsoft-edge/devtools-guide-chromium/console/ "使用控制台|Microsoft Docs"

[ConsoleUtilities]: /microsoft-edge/devtools-guide-chromium/console/utilities "控制台实用程序 API 参考 | Microsoft Docs"

[NodeJS]: https://www.nodejs.org "Node.js"

[NPM]: https://www.npmjs.com/package/reload?activeTab=readme "重新加载 npm 包|npm"
