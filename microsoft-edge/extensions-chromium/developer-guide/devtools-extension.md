---
title: 创建自定义 DevTools UI 的扩展
description: 本教程介绍如何生成扩展 DevTools 的 Microsoft Edge 扩展。 在本教程结束时，你应该有一个有效的 DevTools 扩展，用于创建自己的面板并与 DevTools 扩展 API 交互。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: extensions
ms.date: 9/27/2022
ms.openlocfilehash: 0fb2fd1485326fea6d2a192bc78e4198e2d5dee7
ms.sourcegitcommit: 52f7011a27eaecd2d71da54fb97b42eeabcc05f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2022
ms.locfileid: "12765466"
---
# <a name="create-an-extension-that-customizes-the-devtools-ui"></a>创建自定义 DevTools UI 的扩展

本教程介绍如何从头开始生成自己的 DevTools 扩展。 这是体验典型开发所需的一切的好方法。 本教程结束时，你将拥有一个工作扩展，用于创建自己的面板并与 DevTools API 交互。

首先查看先决条件。 然后从 [“解决方案”](#solution) 部分下载并运行最终扩展，以查看本教程中要生成的内容。 否则，从 [步骤 1 开始 - 创建基本 DevTools 扩展](#step-1---create-a-basic-devtools-extension) 以从头开始生成扩展。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

* 要运行扩展的 [Microsoft Edge 浏览器](https://www.microsoft.com/edge)。
* 一个代码编辑器[，如Visual Studio Code](https://code.visualstudio.com/)与本教程一起操作。


<!-- ====================================================================== -->
## <a name="solution"></a>解决方案

在本部分中，你将下载并运行本教程其余部分将教你生成的扩展的最终状态。 稍后，你将从头开始学习编写代码以创建自己的扩展。

1. 通过 [下载此 zip 文件](https://codeload.github.com/MicrosoftEdge/Demos/zip/refs/heads/main) 并将其内容提取到计算机上的文件夹来获取最终扩展代码。

1. 打开 Microsoft Edge 并转到 `edge://extensions/`。

1. 打开  **开发人员模式** 切换。

1. 单击 **“卸包加载** ”并导航到提取 zip 文件的文件夹。 在此文件夹中，选择 **Demos-main** > **devtools-extension** > **示例 4**，然后单击 **“选择文件夹**”。

  ![Microsoft Edge 中的 edge://extensions 页，显示开发人员模式和“加载解包”按钮。](./devtools-extensions-images/edge-extensions-page.png)

现在应加载 DevTools 扩展。 在 Microsoft Edge 中打开新选项卡，然后按下 `F12`打开 DevTools。

扩展在 DevTools 窗口中创建一个“ **示例面板** ”选项卡：

![Microsoft Edge 在一侧显示 DevTools，其中选择了扩展的示例面板。](./devtools-extensions-images/solution-sample-panel.png)


<!-- ====================================================================== -->
## <a name="step-1---create-a-basic-devtools-extension"></a>步骤 1 - 创建基本的 DevTools 扩展

基本 DevTools 扩展包含两个文件，如 [步骤 1 代码](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-extension/sample%201)中所示：

1. 清单文件。

    ```json
    {
        "name": "DevTools Sample Extension",
        "description": "A Basic DevTools Extension",
        "manifest_version": 3,
        "version": "1.0",
        "devtools_page": "devtools.html"
    }
    ```

    | 属性 | 说明 |
    |----------|-------------|
    | name | 将显示在下 `edge://extensions/`的扩展名。 |
    | description | 将在扩展名下显示的扩展的说明。 |
    | version | 将显示在扩展名旁边的扩展的版本。 |
    | manifest_version | 确定扩展将使用的一组功能，例如服务辅助角色或网络请求修改。 当前版本为版本 `3`。 若要详细了解此版本以及版本 `2`的差异，请参阅迁移 [到清单 V3 的概述和时间线](./manifest-v3.md)。 |
    | devtools_page | 每次打开 DevTools UI 时将执行的 HTML 文件的路径。 尽管页面未在 DevTools 中呈现，但它将用于加载扩展所需的 JavaScript 文件。 |

1. 与清单文件中的字段匹配 `devtools_page` 的 html 文件。

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="UTF-8" />
      </head>
      <body>
        A Basic DevTools Extension.
      </body>
    </html>
    ```

若要在 Microsoft Edge 中加载和测试 DevTools 扩展，请使用 **开发人员模式**：

1. 在 Microsoft Edge 中，转到 `edge://extensions/`.

1. 打开  **开发人员模式** 切换。

1. 单击 **“卸包加载**”，导航到为扩展编写代码的文件夹，然后单击 **“选择”文件夹**。

现在已加载 DevTools 扩展。 打开新选项卡，然后打开 DevTools (`F12`) 。

扩展已加载，但尚未显示在 DevTools 中，因为尚未为扩展创建面板。


<!-- ====================================================================== -->
## <a name="step-2---add-a-devtools-panel"></a>步骤 2 - 添加 DevTools 面板

在此步骤中，你将在 DevTools 中创建一个新面板。 可以在 [步骤 2 代码](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-extension/sample%202)中找到此步骤的代码，或按照以下说明自行编写。

_面板_是 DevTools 中主工具栏中的选项卡，类似于下面所示的**元素**、**控制台**和**源**工具：

![DevTools 面板和边栏](./devtools-extensions-images/devtools-main-toolbar-tabs.png)

在此步骤中，我们将使用示例面板创建基本的 DevTools 扩展。

1. `devtools.js`使用以下代码创建文件：

    ```javascript
    chrome.devtools.panels.create("Sample Panel", "icon.png", "panel.html", panel => {
        // code invoked on panel creation
    });
    ```

    该`create`方法需要四个参数：`title`、`pagePath``iconpath`和一个回调函数。 请注意，虽然面板的图标是必需的参数，但当前不会显示在 Microsoft Edge DevTools 中。

    若要详细了解 `chrome.devtools.panels` 扩展 API，请参阅 [chrome.devtools.panel API 参考](https://developer.chrome.com/docs/extensions/reference/devtools_panels/)。

1. 通过在源代码中添加`script`元素，从之前在清单字段中`devtools_page`指定的 HTML 页加载文件 (`devtools.html`文件) 。

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="UTF-8" />
      </head>
      <body>
        <script src="devtools.js"></script>
      </body>
    </html>
    ```

1. 创建在上一`panel.html``chrome.devtools.panels.create`个方法调用中引用的文件。 此网页将包含扩展添加到 DevTools 的面板的用户界面。

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="UTF-8" />
      </head>
      <body>
        <h1>A Basic DevTools Extension with Panel</h1>
      </body>
    </html>
    ```

若要测试 Microsoft Edge 中的更改，请从 `edge://extensions/` 页面重新加载扩展：

1. 导航 (或返回到页面) `edge://extensions/` 。

1. 查找在步骤 1 中加载的未打包扩展条目。

1. 单击 **“重新加载**”。

   ![显示“重载”按钮所在位置的 Microsoft Edge 扩展页](./devtools-extensions-images/edge-extensions-page-reload-button.png)

现在应重新加载 DevTools 扩展。 在 Microsoft Edge 中打开新选项卡，然后打开 DevTools (`F12`) 。 DevTools 扩展面板应显示在 DevTools 中：

![Microsoft Edge，侧面有 DevTools，显示新的扩展面板](./devtools-extensions-images/devtools-extension-with-panel.png)


<!-- ====================================================================== -->
## <a name="step-3---call-extension-apis-from-a-devtools-extension"></a>步骤 3 - 从 DevTools 扩展调用扩展 API

在此步骤中，你将使用扩展 API 在 DevTools 面板中显示内存信息。  为此，我们需要更新 `permissions` 清单文件、面板接口和开发工具脚本。 可以在 [步骤 3 代码](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-extension/sample%203)中找到此步骤的源代码，或按照以下说明自行编写。

1. `permissions`在文件中`manifest.json`使用清单成员。 此成员定义扩展需要用户的权限。 使用某些扩展 API 需要某些权限。

    ```json
    "permissions": [
      "system.memory",
    ]
    ```

    `system-memory`使用扩展 API 需要该权限，我们将在本教程的后面部分使用。 若要了解有关可用 API 和关联权限的详细信息，请参阅 [API 参考](https://developer.chrome.com/docs/extensions/reference/)。

1. 将以下内容添加到文件中的正文， `panel.html` 以在面板中显示数据。

    ```html
    <div>
      Available Memory Capacity: <span id="availableMemoryCapacity"></span>
    </div>
    <div>
      Total Memory Capacity: <span id="totalMemoryCapacity"></span>
    </div>
    ```

1. `devtools.js`使用以下代码更新文件。

    ```javascript
    let availableMemoryCapacity;
    let totalMemoryCapacity;

    chrome.devtools.panels.create("Sample Panel", "icon.png", "panel.html", panel => {
        // code invoked on panel creation
        panel.onShown.addListener((extPanelWindow) => {
            availableMemoryCapacity = extPanelWindow.document.querySelector('#availableMemoryCapacity');
            totalMemoryCapacity = extPanelWindow.document.querySelector('#totalMemoryCapacity');
        });
    });

    setInterval(() => {
        chrome.system.memory.getInfo((data) => {
            if (availableMemoryCapacity) {
                availableMemoryCapacity.innerHTML = data.availableCapacity;
            }
            if (totalMemoryCapacity) {
                totalMemoryCapacity.innerHTML = data.capacity;
            }
        });
    }, 1000);
    ```

上述代码片段执行以下操作：

1. 它在 DevTools 中创建一个新面板 `Sample Panel` 。

1. 当面板显示 (`panel.onShown` 侦听器) 时， `availableMemoryCapacity` 将从 DOM 中检索和 `totalMemoryCapacity` 元素。

1. 接下来，计时器设置为在显示面板后每秒执行一次代码。

1. 当计时器触发时， `chrome.system.memory.getInfo` 该方法用于检索设备的可用和总内存容量，这些值显示在相应的 DOM 元素中。

若要测试 Microsoft Edge 中的更改，请从 `edge://extensions/` 页面重新加载扩展：

1. 导航 (或返回到页面) `edge://extensions/` 。

1. 查找在步骤 1 中加载的未打包扩展条目。

1. 单击 **“重新加载**”。

现在应重新加载 DevTools 扩展。 打开新选项卡，然后打开 DevTools (`F12`) 。 DevTools 扩展面板现在应显示可用和总内存容量。

![DevTools 中的新扩展面板，显示内存信息](./devtools-extensions-images/devtools-extension-with-memory-info.png)

可以在 [API 参考](https://developer.chrome.com/docs/extensions/reference/) 页中找到更多扩展 API。


<!-- ====================================================================== -->
## <a name="step-4---interact-with-the-inspected-webpage"></a>步骤 4 - 与检查的网页交互

在本教程的这一步骤中，你将添加与已检查网页交互的代码。 该代码将：

1. 侦听单击网页上发生的事件，并将其记录到 DevTools **控制台** 工具中。
1. 显示 DevTools 扩展面板中的鼠标单击位置。
1. 当用户单击 DevTools 扩展面板中的按钮时，在检查的页面中显示问候语警报。

可以在 [步骤 4 代码](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-extension/sample%204)中找到此步骤的源代码，或按照以下说明自行编写。

遗憾的是，刚刚创建的 DevTools 面板无法直接访问已检查的网页，并且在 DevTools 打开之前不会运行。 为此，你将使用内容脚本和后台服务辅助角色。

* 内容脚本在已检查网页的上下文中运行，与页面加载其他脚本的方式相同，它们有权访问 DOM 并可以更改它。
* 后台服务辅助角色是浏览器在单独的线程中运行并有权访问扩展 API 的脚本。

下图概述了 DevTools 页面、已检查的页面、内容脚本和后台服务辅助角色如何在扩展中结合使用。

![DevTools 扩展的解剖](./devtools-extensions-images/overall_screenshot_mv3.png)

在本教程的这一部分中，你将使用内容脚本检测用户单击网页。  内容脚本会将此信息中继到 `devtools.js` 将在控制台和 DevTools 扩展面板中显示数据的文件。

1. 将以下内容追加到文件中`manifest.json`

    ```json
    "content_scripts": [{
      "matches": [
        "http://*/*",
        "https://*/*"
      ],
      "run_at": "document_idle",
      "js": [
        "content_script.js"
      ]
    }],
    "background": {
        "service_worker": "background.js"
    }
    ```

    | 属性 | 值 |
    |----------|-------|
    | 比赛 | 指定将此内容脚本注入到哪些页面。 |
    | run_at | 指示浏览器何时将脚本注入页面。 |
    | Js | 要注入的 javascript 文件。 |

1. 创建包含以下内容的文件 `content_script.js` ：

    ```javascript
    document.addEventListener("click", (event) => {
      chrome.runtime.sendMessage({
          click: true,
          xPosition: event.clientX + document.body.scrollLeft,
          yPosition: event.clientY + document.body.scrollTop
        },
        response => {
          console.log("Received response", response);
        }
      );
    });
    ```

    上述代码片段在页面中注入脚本时将消息输出到控制台。 它还向页面添加一个单击事件侦听器，该侦听器将使用 `chrome.runtime.sendMessage` API 在检查的页面中使用鼠标单击位置发送消息。

1. 在文件中 `panel.html` ，添加一个 `sayHello` 按钮和一个 `youClickedOn` 标签。 这两个元素用于演示检查的页面、DevTools 面板和后台服务辅助角色之间的交互。 当用户单击 `sayHello` DevTools 扩展中的按钮时，它将在检查的窗口中显示问候消息。 当用户单击检查的页面中的任意位置时，它将显示一条消息，显示 DevTools 扩展面板中的鼠标单击位置。

    ```html
    <button id="sayHello">Say Hello to the inspected page!</button>
    <h2><span id="youClickedOn"></span></h2>
    ```

1. 在文件中`devtools.js``chrome.runtime.connect`，使用该方法创建与后台服务辅助角色的连接，然后使用`backgroundPageConnection.postMessage`该方法将检查的窗口`tabId`发送给服务辅助角色。 最后，将事件侦听器添加到`sayHello`文件中`panel.html`定义的按钮和`youClickedOn`标签。

    ```javascript
    let youClickedOn; 
    chrome.devtools.panels.create("Sample Panel", "icon.png", "panel.html", panel => {
        // code invoked on panel creation
        panel.onShown.addListener( (extPanelWindow) => {
            let sayHello = extPanelWindow.document.querySelector('#sayHello');
            youClickedOn = extPanelWindow.document.querySelector('#youClickedOn');
            sayHello.addEventListener("click", () => {
                // show a greeting alert in the inspected page
                chrome.devtools.inspectedWindow.eval('alert("Hello from the DevTools extension");');
            });             
        });
    });

    chrome.runtime.onMessage.addListener((request, sender, sendResponse) => {
        // Messages from content scripts should have sender.tab set
        if (sender.tab && request.click == true) {
            console.log('I am here!');
            if (youClickedOn) {
                youClickedOn.innerHTML = `You clicked on position (${request.xPosition}, ${request.yPosition}) in the inspected page.`;
            }
            sendResponse({
                xPosition: request.xPosition,
                yPosition: request.yPosition
            });
        }
    });

    // Create a connection to the background service worker
    const backgroundPageConnection = chrome.runtime.connect({
        name: "devtools-page"
    });

    // Relay the tab ID to the background service worker
    backgroundPageConnection.postMessage({
        name: 'init',
        tabId: chrome.devtools.inspectedWindow.tabId
    });
    ```

    当用户单击`sayHello`该按钮时，DevTools 扩展将通过调用`eval()`检查窗口的方法`chrome.devtools.inspectedWindow`来执行检查窗口中的代码片段`alert("Hello from the DevTools Extension");`。

    当用户单击检查窗口中的任意位置时，DevTools 扩展将收到来自后台服务辅助角色的消息以及 `request.click == true` 鼠标位置信息。

1. 创建文件并向 `background.js` 其添加以下代码：

    ```javascript
    let id = null;
    const connections = {};

    chrome.runtime.onConnect.addListener(devToolsConnection => {
        // Assign the listener function to a variable so we can remove it later
        let devToolsListener = (message, sender, sendResponse) => {
            if (message.name == "init") {
                id = message.tabId;
                connections[id] = devToolsConnection;
                // Send a message back to DevTools
                connections[id].postMessage("Connected!");
            }
        };

        // Listen to messages sent from the DevTools page
        devToolsConnection.onMessage.addListener(devToolsListener);

        devToolsConnection.onDisconnect.addListener(() => {
            devToolsConnection.onMessage.removeListener(devToolsListener);
        });
    });
    ```

    上面的代码片段将后台服务辅助角色与 DevTools 页面连接。 它侦听 DevTools 页面何时连接、保存连接，并将响应发送回 DevTools 页面。

    当后台服务辅助角色正在收集数据或在后台执行要在 DevTools 扩展中可用的任务时，这非常有用。

若要测试新 `sayHello` 按钮，请执行以下操作：

1. 转到 `edge://extensions/`。

1. 查找在步骤 1 中加载的未打包扩展条目。

1. 单击 **“重新加载** ”按钮。

1. 打开新的浏览器选项卡，打开 DevTools (`F12`) ，然后单击“ **示例面板** ”选项卡。

1. `"Say Hello to The Inspected Page!"`单击面板中的按钮。 应在检查的页面中看到警报，如下所示。

    ![Microsoft Edge，在一侧的 DevTools 中显示新的扩展面板，以及警报对话框窗口](./devtools-extensions-images/devtools-extension-show-greeting.png)

若要了解有关内容脚本的详细信息，请参阅 [内容脚本文档](https://developer.chrome.com/docs/extensions/mv3/content_scripts/)。

若要测试标签，请执行以下 `youClickedOn` 操作：

1. 单击 **“确定** ”关闭在上一步中打开的警报窗口。

1. 单击检查页面中的任意位置。 A **你单击了所检查页面消息中 (x，y) ** 的位置应显示在扩展面板中。

    ![DevTools 中的示例面板，其中显示了单击的位置消息](./devtools-extensions-images/devtools-extension-show-position.png)

1. 打开 **控制台** 工具。 类似上一步的消息也应显示在  **控制台** 工具中。

    ![显示单击位置消息的 DevTools 控制台工具](./devtools-extensions-images/devtools-extension-show-position-in-console.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [清单 V3](https://developer.chrome.com/docs/extensions/mv3)
* [扩展 DevTools](https://developer.chrome.com/docs/extensions/mv3/devtools/)
* [CDP API 参考](https://developer.chrome.com/docs/extensions/reference/)
