---
title: DevTools 扩展疑难解答
description: 错误消息以及如何以避免错误消息的方式重启 DevTools。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 5ccec1e0cc2cb662fde4dcb739dcee74142217ec
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816018"
---
# <a name="troubleshooting-the-devtools-extension"></a>DevTools 扩展疑难解答

* 请确保以受支持的方式或方案之一打开 DevTools。  请参阅 [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。


<!-- ====================================================================== -->
## <a name="controlling-css-mirror-editing"></a>控制 CSS 镜像编辑

默认情况下，在 **Edge DevTools** 选项卡的 **“元素**”工具的“**样式**”选项卡中选择 **CSS 镜像编辑**复选框。 如果使用 DevTools 更改 CSS 值，但 DevTools 在工作区 (文件夹中找不到) 在Visual Studio Code中打开的匹配文件，则会显示有关映射到源文件以进行 CSS 镜像编辑的错误消息。

如果要在 DevTools 中更改 CSS，请执行以下操作：

   *  选择 **CSS 镜像编辑** 复选框，然后打开一个文件夹，其中包含与要使用 DevTools 检查的网页匹配的源文件。

   *  或者，清除 **CSS 镜像编辑** 复选框，以防止出现此类错误消息。

另请参阅：
* “样式”选项卡内的“更新 .css 文件”中的 [CSS 镜像编辑复选框](./css-mirror-editing-styles-tab.md#the-css-mirror-editing-checkbox)_ (CSS 镜像编辑) _
* [将 URL 文件映射到](./open-devtools-and-embedded-browser.md#mapping-url-files-to-the-opened-folder)_打开的 DevTools 和 DevTools 浏览器_中打开的文件夹。


<!-- ====================================================================== -->
## <a name="restarting-devtools"></a>重启 DevTools

重启 DevTools 的一种强大方法是关闭并重新打开文件夹：

1. 在Visual Studio Code中，选择 **“文件** > **关闭文件夹**”。

1. 如果在Visual Studio Code中使用终端启动 Web 服务器，请重启 Web 服务器，例如通过运行`npx http-server`。  或者，可以从Visual Studio Code外部的命令提示符启动 Web 服务器，以便它继续运行。  有关详细信息，请参阅步骤 6：在_安装用于Visual Studio Code的 DevTools 扩展_时[设置 localhost 服务器](./install.md#step-6-set-up-a-localhost-server)。

1. 在Visual Studio Code中，选择 **“最近****打开**的文件 > ”，然后打开包含网页源文件的文件夹。


<!-- ====================================================================== -->
## <a name="closing-all-instances-of-devtools"></a>关闭 DevTools 的所有实例

通常，关闭两 **个 DevTools** 选项卡会关闭 DevTools 和 DevTools 浏览器的任何实例。  如果“调试”工具栏处于打开状态，请单击 **“停止”** 按钮。

若要重置 DevTools 的状态，请关闭 DevTools 的所有实例。  请确保“**启动实例**”按钮显示在Visual Studio Code >活动栏> **Microsoft Edge 工具**侧栏中。  这表示未运行任何 DevTools 实例。

如有必要，请关闭所有Visual Studio Code实例，然后打开Visual Studio Code，并确保“**启动实例**”按钮显示在活动栏> **Microsoft Edge Tools** 侧栏中。


<!-- ====================================================================== -->
## <a name="error-messages"></a>错误消息

大多数错误消息的解决方案是使用建议的方法之一打开 DevTools。  请确保打开一个文件夹，其中包含 DevTools 可以映射到 DevTools 浏览器使用的文件路径或 URL 的网页源文件。

DevTools 浏览器使用你指定任何各种方式的 URL 或文件路径：

| 打开 DevTools 的方式 | 指定文件路径或 URL 的位置 |
|---|---|
| 单击 **“启动实例** ”按钮。 | 在 DevTools 浏览器的地址栏中指定的 URL 或文件路径。 |
| 右键单击 `.html` 文件。 | 右键单击的文件路径 `.html` 。 |
| 单击 **“启动项目”** 按钮。 | 你在 `launch.json`其中指定的 URL 或文件路径。 |

如果在 DevTools 浏览器的地址栏中输入其他 URL 或文件路径，则为 DevTools 提供本地源文件的自动 CSS 镜像编辑，还必须打开一个文件夹，该文件夹包含与在 DevTools 浏览器中指定的网页 (文件路径或 URL) 匹配的文件。

假设单击 **“启动实例** ”按钮，然后将 localhost URL 粘贴到地址栏中，例如 [http://localhost:8080/](http://localhost:8080/) 或 [http://localhost/demos/demo-to-do/](http://localhost/demos/demo-to-do/)，但本地源文件文件夹未打开。  然后，在“元素”工具的“ **样式** ”选项卡中，尝试更改 CSS 值。  可能会出现错误消息，例如：

*  **将内容镜像到文档时出错。  无法镜像对文档所做的更改。  找不到工作区映射。**

*  **无法在编辑器中打开文件。**

*  **在编辑器中打开文件时出错。**

*  **提取时出错。**

*  **无法附加到主目标。**

*  **提取可用目标列表时出错。  没有要附加的可用目标。**

![无工作区映射](./troubleshooting-images/no-workspace-mapping.png)

如果在尝试指向文件路径时遇到错误，而不是使用 `launch.json` 文件，请尝试右键单击 `.html` 该文件：

![无法附加到主目标](./troubleshooting-images/could-not-attach-main-target.png)

请参阅 [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。


<!-- ====================================================================== -->
## <a name="deleting-or-re-creating-launchjson"></a>删除或重新创建 launch.json

除了关闭重新打开的文件夹外，如果要重置要与 DevTools 配合使用的项目，还可以删除并选择性地重新创建 `launch.json`。  `launch.json` 定义调试配置。

对于 DevTools 扩展，以下 `launch.json` 文件太短。  它是由Visual Studio Code创建的，无需使用 DevTools 扩展。  演示存储库在[演示到操作](https://github.com/MicrosoftEdge/Demos/tree/main/demo-to-do)中没有`launch.json`，因此你可能想要删除该文件：

![删除错误的 launch.json 文件](./troubleshooting-images/wrong-launch-json.png)

若要为 DevTools 重新创建新 `launch.json` 文件，请执行以下操作：

1. 创建文件的 `launch.json` 备份副本。

1. 在Visual Studio Code >活动栏>**资源管理器**中，右键单击`launch.json` > **“删除**”。

   > **Microsoft Edge Tools** 的活动栏现在显示 **“启动实例** ”按钮和“ **生成 launch.json** ”按钮。

1. 如果要将文件用于 `launch.json` DevTools，请确保在资源**管理**器Visual Studio Code >活动栏>中打开所需的文件夹，然后单击 **“生成 launch.json**”按钮。  单击 _“打开 DevTools”和“DevTools”浏览器_中的[“启动项目”按钮，查看“打开 DevTools](./open-devtools-and-embedded-browser.md#opening-devtools-by-clicking-the-launch-project-button)”。


<!-- ====================================================================== -->
## <a name="launchjson-requires-well-formed-json"></a>launch.json 需要格式正确的 JSON

如果活动栏> **Microsoft Edge Tools** 包含配置 **launch.json** 按钮，而不是在打开的文件夹中存在 DevTools 生成`launch.json`的文件时预期的**启动项目**按钮，则这可能是由于添加缺少逗号或空引号的行导致的。  请确保 `launch.json` 包含格式正确的 JSON。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
* [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)
