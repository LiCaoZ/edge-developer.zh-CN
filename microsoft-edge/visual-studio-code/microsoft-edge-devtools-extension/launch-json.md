---
title: DevTools 扩展的 launch.json 文件
description: 适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展的 launch.json 文件，用于调试配置的高级自定义。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 7c311c795cd7f211014c10c5072364b835881170
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816036"
---
# <a name="the-launchjson-file-for-the-devtools-extension"></a>DevTools 扩展的 launch.json 文件

Visual Studio Code使用`launch.json`文件来定义调试配置。  若要使用 DevTools 扩展， `launch.json` 仅当您想要使用调试器且网页需要在 Web 服务器上运行（而不仅仅是本地文件系统）时，才需要一个文件。  在大多数情况下，如果选择) 使用 DevTools 生成 `launch.json` 的文件 (的内容，你唯一需要知道的就是需要在多个位置的字符串中 `"url"` 输入所需的 URL。  如果要使用自定义高级调试配置，请阅读本文。

如果要使用 Visual Studio Code 的 UI（`F5`例如启动 **DevTools** 选项卡以及调试模式），打开的文件夹 (工作区) 必须在目录中`.vscode`包含 DevTools 生成的 (与 DevTools 兼容的) `launch.json`文件。

下面是有关文件格式的 `launch.json` 详细信息。  通常无需更改文件中的任何内容，只需替换 URL 字符串的多个实例，如打开 DevTools 中所述，方法是在_打开 DevTools 和 DevTools 浏览器_中[单击“启动项目”按钮](./open-devtools-and-embedded-browser.md#opening-devtools-by-clicking-the-launch-project-button)。


<!-- ====================================================================== -->
## <a name="where-the-name-strings-appear-in-the-ui"></a>名称字符串显示在 UI 中的位置

`"name"`每个调试配置的字符串在多个位置填充下拉列表。

1. 选择 **“文件** > **关闭文件夹**”。

1. 选择 **“最近** > `C:\Users\myusername\Documents\GitHub\Demos\demo-to-do\index.html`打开**的文件** > ”，每个步骤 5 克隆：在_安装用于Visual Studio Code的 DevTools 扩展_时[克隆演示存储库](./install.md#step-5-clone-the-demos-repo)。

   假设目录中`.vscode`不存在任何`launch.json`文件。

1. 选择活动栏> **Microsoft Edge Tools** >单击 **“生成 launch.json** ”按钮。

1. 在活动栏> **资源管理器**中，双击 `index.html` 将其打开。

1. 选择活动栏> **运行和调试** >单击 **“运行和调试** ”按钮。

   在左上角的 **“运行和调试** ”边栏中，字符串为 **“启动边缘无头”，并附加 DevTools** 和 **Launch Edge 并附加 DevTools**。  在Visual Studio Code窗口的底部，字符串为 **“启动边缘无头”并附加 DevTools**。  这些是文件中`.json`复合配置的名称，告知Visual Studio Code调试器打开两个 **DevTools** 选项卡，或者使用 **DevTools** 选项卡和外部浏览器：

   ```json
    "compounds": [
        {
            "name": "Launch Edge Headless and attach DevTools",
            "configurations": [
                "Launch Microsoft Edge in headless mode",
                "Open Edge DevTools"
            ]
        },
        {
            "name": "Launch Edge and attach DevTools",
            "configurations": [
                "Launch Microsoft Edge",
                "Open Edge DevTools"
            ]
        }
    ]
   ```

   ![运行和调试侧栏左上角的配置](./launch-json-images/run-debug-upper-left.png)

   在右下角的 **调试控制台** 中，字符串在 **无头模式下启动 Microsoft Edge**。  这是一个字符串，不是关于 **Edge DevTools** 选项卡，而是关于 **Edge DevTools：Browser** 选项卡。 它是单个配置的名称，而不是复合配置的名称：

   ```json
       "configurations": [
        ...
        {
            "type": "pwa-msedge",
            "name": "Launch Microsoft Edge in headless mode",
            "request": "launch",
            "runtimeArgs": [
                "--headless",
                "--remote-debugging-port=9222"
            ],
            "url": "file://c:\\Users\\collabera\\Documents\\GitHub\\Demos\\demo-to-do\\index.html",
            "presentation": {
                "hidden": true
            }
        },
   ```

   ![右下角调试控制台中的配置](./launch-json-images/run-debug-lower-right.png)

1. 在 **“运行和调试** ”边栏中，单击 **“开始调试**”。  打开两**个 DevTools** 选项卡，Visual Studio Code进入调试模式。  此方法是用于启动调试器的内置Visual Studio Code UI，而不是[在打开 DevTools 和 DevTools 浏览器中所述的 DevTools](./open-devtools-and-embedded-browser.md) UI。
<!-- todo: copy the above steps to F5 area of Debugging article - temp linked from there to here -->


<!-- ====================================================================== -->
## <a name="where-the-launchjson-file-is-placed"></a>放置 launch.json 文件的位置

1. 在Visual Studio Code的 **“资源管理器”** 窗格中，`launch.json`文件放置在`.vscode`打开的文件夹根目录的文件夹中。

   *  对于存储库（如 Demos 存储库），如果打开整个存储库文件夹，“ **生成 launch.json** ”按钮会在根目录附近为整个存储库目录创建一个 `\.vscode\launch.json` 文件。

   *  如果打开特定的较小文件夹，例如 `\Demos\demo-to-do\`，“ **生成 launch.json** ”按钮仅将文件 `launch.json` 放入该文件夹中。

Visual Studio Code使用`launch.json`文件来配置和自定义调试器。  `launch.json` 是调试器配置文件。  此文件还控制要与调试器一起使用的 Web 浏览器。  例如，在通过单击网页中的按钮以使 JavaScript 代码运行来测试网页时，Visual Studio Code调试器会侦听浏览器，并逐步执行网页的 JavaScript 代码。

下面是单击扩展中的 **“创建 launch.json**”按钮后的副本`launch.json`。

默认情况下，最初定义了三个 _配置_ 和两个 _复合体_ ：

*  `configurations` - 在 Visual Studio Code UI 中，这些配置名称显示在调试器 UI 中：

   * **启动 Microsoft Edge** - 这是一个“launch”类型配置。

   * **在无头模式下启动 Microsoft Edge** - 这是一个“launch”类型配置。

   * **Open Edge DevTools** - 这是“debug”类型 (或“attach”类型) 配置。

*  `compounds` - 在Visual Studio Code UI 中，这些内容显示在调试工具栏中：

   * **启动 Edge 无头和附加 DevTools**

   * **启动 Edge 并附加 DevTools**


<!-- ====================================================================== -->
## <a name="intellisense-and-autocomplete"></a>Intellisense 和 autocomplete

将鼠标悬停在 JSON 名称或值上以显示工具提示：

![将鼠标悬停在 JSON 名称或值上时的 Intellisense 工具提示](./launch-json-images/intellisense-tooltip.png)

开始键入双引号，查看可用 JSON 属性和说明的自动完成列表：

![launch.json 的自动完成](./launch-json-images/autocomplete.png)<!--no comma yet-->

保存文件时，请务必提供格式正确的 JSON，包括逗号。


<!-- ====================================================================== -->
## <a name="configuration-types-launch-vs-debug"></a>配置类型：启动与调试

这两种不同类型的配置都在此`.json`文件中为Visual Studio Code调试器定义。


<!-- ====================================================================== -->
## <a name="configurations"></a>配置

以下文件部分`launch.json`来自扩展的 v2.1.1，位于 Windows 上Visual Studio Code的默认安装位置。


#### <a name="configuration-1-launch-microsoft-edge"></a>配置 1：启动 Microsoft Edge

这是一个“启动浏览器”类型配置。  此配置控制浏览器组件，例如 `.html` 在 UI 中未选择 **无头** 文件时要显示的文件。

此配置名称不会直接显示在 UI 中。  下面的复合配置使用此配置。

```json
        {
            "type": "pwa-msedge",
            "name": "Launch Microsoft Edge",
            "request": "launch",
            "runtimeArgs": [
                "--remote-debugging-port=9222"
            ],
            "url": "c:\\Users\\myusername\\.vscode\\extensions\\ms-edgedevtools.vscode-edge-devtools-2.1.1\\out\\startpage\\index.html", // Provide your project's url to finish configuring
            "presentation": {
                "hidden": true
            }
        },
```


#### <a name="configuration-2-launch-microsoft-edge-in-headless-mode"></a>配置 2：在无头模式下启动 Microsoft Edge

这是一个“启动浏览器”类型配置。  此配置控制浏览器组件，例如在 Edge DevTools >**“设置”** 页中选择**无头**时要显示的文件`.html`，就像默认情况下一样。

此配置名称 **“在无头模式下启动 Microsoft Edge** ”显示在 UI 中，例如在调试工具栏和 **调试控制台**中。  如果启动多个实例，则会将一个数字追加到 UI 中的其他实例，例如 **在无头模式 2 下启动 Microsoft Edge**。  下面的复合配置使用此配置。

```json
        {
            "type": "pwa-msedge",
            "name": "Launch Microsoft Edge in headless mode",
            "request": "launch",
            "runtimeArgs": [
                "--headless",
                "--remote-debugging-port=9222"
            ],
            "url": "c:\\Users\\myusername\\.vscode\\extensions\\ms-edgedevtools.vscode-edge-devtools-2.1.1\\out\\startpage\\index.html", // Provide your project's url to finish configuring
            "presentation": {
                "hidden": true
            }
        },
```


#### <a name="configuration-3-open-edge-devtools"></a>配置 3：Open Edge DevTools

这是一个“附加调试器”类型配置。  此配置控制 **Edge DevTools** 选项卡 (窗格) ，例如哪个 `.html` 文件填充 **元素** 工具。

此配置名称不会直接显示在 UI 中。  下面的复合配置使用此配置。

```json
        {
            "type": "vscode-edge-devtools.debug",
            "name": "Open Edge DevTools",
            "request": "attach",
            "url": "c:\\Users\\myusername\\.vscode\\extensions\\ms-edgedevtools.vscode-edge-devtools-2.1.1\\out\\startpage\\index.html", // Provide your project's url to finish configuring
            "presentation": {
                "hidden": true
            }
        }
```


<!-- ====================================================================== -->
## <a name="compound-configurations"></a>复合配置

`launch.json`部分`compounds`定义复合配置。

每个复合配置都引用两种配置：一种是在 Visual Studio Code 中打开 **Edge DevTools** 选项卡的配置，另一种配置用于打开 **Edge DevTools：浏览器**选项卡 (有时调用_屏幕广播_或_无头浏览器_) ，或者同时调用 **Edge DevTools：浏览器**选项卡和整个 Microsoft Edge 浏览器窗口。

在 **“Microsoft Edge Tools”** 窗格的 **“目标** ”部分中，单击目标右侧的 **“切换屏幕截图** ”按钮。  无头嵌入 **式 Edge DevTools：浏览器** 选项卡 (窗格) 关闭或打开。

在 **“Microsoft Edge 工具”** 窗格的 **“目标** ”部分中，单击目标右侧的 **“附加”并打开“Microsoft Edge Tools”** 按钮。


#### <a name="compound-configuration-1-launch-edge-headless-and-attach-devtools"></a>复合配置 1：启动 Edge 无头和附加 DevTools

此复合配置启动以下组件：

*  Visual Studio Code中的 **“Edge DevTools：浏览器**”选项卡 (窗格) 。  这由上面具有 `name` “在无头模式下启动 Microsoft Edge”的配置定义。

*  Visual Studio Code中的“**边缘开发工具**”选项卡 (窗格) 。  这由上面具有 `name` “Open Edge DevTools”的配置定义。


```json
        {
            "name": "Launch Edge Headless and attach DevTools",
            "configurations": [
                "Launch Microsoft Edge in headless mode",
                "Open Edge DevTools"
            ]
        },
```

此复合配置的名称“**启动 Edge 无头和附加 DevTools**”显示在Visual Studio Code的调试工具栏中。


#### <a name="compound-configuration-2-launch-edge-and-attach-devtools"></a>复合配置 2：启动 Edge 并附加 DevTools

此复合配置启动以下组件：

*  Visual Studio Code中的 **“Edge DevTools：浏览器**”选项卡 (窗格) 。  这由上面具有“启动 Microsoft Edge”的 `name` 配置定义。

*  Microsoft Edge 浏览器窗口。  这由上面具有“启动 Microsoft Edge”的 `name` 配置定义。

*  Visual Studio Code中的“**边缘开发工具**”选项卡 (窗格) 。  这由上面具有 `name` “Open Edge DevTools”的配置定义。

```json
        {
            "name": "Launch Edge and attach DevTools",
            "configurations": [
                "Launch Microsoft Edge",
                "Open Edge DevTools"
            ]
        }
```

此复合配置的名称 **Launch Edge 和 attach DevTools** 显示在 Visual Studio Code 调试工具栏的 UI 中。


<!-- ====================================================================== -->
## <a name="adding-configurations"></a>添加配置

可以定义自己的其他调试配置。  单击“ **添加配置** ”按钮。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。
* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)

#### <a name="launchjson-for-other-platforms"></a>针对其他平台的 launch.json

* 在Visual Studio Code文档中[配置 C/C++ 调试](https://code.visualstudio.com/docs/cpp/launch-json-reference)。
* 在Visual Studio Code文档_的Visual Studio Code中使用React_配置[调试器](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial#_configure-the-debugger)。
