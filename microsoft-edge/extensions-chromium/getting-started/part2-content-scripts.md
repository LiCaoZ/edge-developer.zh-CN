---
title: 创建扩展教程，第 2 部分
description: 使用内容脚本在页面正文标记下动态插入 NASA 图片。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
ms.openlocfilehash: b4ae6642e30fdb8d6924f41d72c8e979eae45204
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522327"
---
# <a name="create-an-extension-tutorial-part-2"></a>创建扩展教程，第 2 部分

[已完成此部件的扩展包源](https://github.com/MicrosoftEdge/MicrosoftEdge-Extensions-Demos/tree/master/extension-getting-started-part2/extension-getting-started-part2)<!-- changing master to main doesn't work 5/19/2022 -->


<!-- ====================================================================== -->
## <a name="overview"></a>概述

本教程介绍以下扩展技术：
*   将 JavaScript 库注入扩展。
*   将扩展资产公开到浏览器选项卡。
*   在现有浏览器选项卡中包括内容页。
*   让内容页侦听弹出窗口中的消息并做出响应。

你将了解如何更新弹出菜单，将静态星形图像替换为标题和标准 HTML 按钮。  选中该按钮时，将嵌入在扩展中的星形图像传递到内容页。  该图像将插入到活动浏览器选项卡中。请按照以下步骤了解更多详细信息。

1.  从弹出窗口中删除图像，并将其替换为按钮。

首先，使用显示标题和按钮的简单标记更新 `popup.html` 文件。  你将很快对该按钮进行编程，但目前只需包含对空 JavaScript 文件 `popup.js`的引用即可。  下面是更新后的 HTML：

```html
<html>
    <head>
        <meta charset="utf-8" />
        <style>
            body {
                width: 500px;
            }
            button {
                background-color: #336dab;
                border: none;
                color: white;
                padding: 15px 32px;
                text-align: center;
                font-size: 16px;
            }
        </style>
    </head>
    <body>
        <h1>Display the NASA picture of the day</h1>
        <h2>(select the image to remove)</h2>
        <button id="sendmessageid">Display</button>
        <script src="popup.js"></script>
    </body>
</html>
```

更新并打开扩展后，将打开带有显示按钮的弹出窗口。

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="popup.html选择“扩展”图标后显示。":::
   选择“扩展”图标后popup.html显示
:::image-end:::

<!--![popup.html display after selecting the Extension icon] -->

2.  更新策略以在浏览器选项卡顶部显示图像

添加按钮后，下一个任务是使其在活动选项卡页顶部显示 `images/stars.jpeg` 图像文件。

请记住，每个选项卡页在其自己的线程中运行。 此外，该扩展使用不同的线程。  首先，创建注入到选项卡页的内容脚本。  然后，将弹出窗口中的消息发送到选项卡页上运行的内容脚本。 内容脚本接收消息，该消息描述应显示哪个图像。

3. 创建弹出式 JavaScript 以发送消息

首先，创建 `popup/popup.js` 并添加代码以将消息发送到尚未创建的内容脚本，必须暂时创建该脚本并将其注入浏览器选项卡中。 为此，以下代码将事件 `onclick` 添加到弹出式显示按钮。

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
  sendMessageId.onclick = function() {
    // do something
  };
}
```

在该 `onclick` 事件中，找到当前浏览器选项卡。 然后，使用 `chrome.tabs.sendmessage` 扩展 API 将消息发送到该选项卡。

在该消息中，必须包含要显示的图像的 URL。  此外，发送要分配给插入的图像的唯一 ID。  你可以让内容插入 JavaScript 生成该映像 ID，但由于后来变得明显的原因，你将在此 `popup.js`处生成该唯一 ID，然后将该 ID 传递给尚未创建的内容脚本。

以下代码概述了更新后的代码 `popup/popup.js`。  你还将传递当前选项卡 ID，本文稍后将使用该 ID。

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
    sendMessageId.onclick = function() {
        chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
            chrome.tabs.sendMessage(
                tabs[0].id,
                {
                    url: chrome.extension.getURL("images/stars.jpeg"),
                    imageDivId: `${guidGenerator()}`,
                    tabId: tabs[0].id
                },
                function(response) {
                    window.close();
                }
            );
            function guidGenerator() {
                const S4 = function () {
                    return (((1 + Math.random()) * 0x10000) | 0).toString(16).substring(1);
                };
                return (S4() + S4() + "-" + S4() + "-" + S4() + "-" + S4() + "-" + S4() + S4() + S4());
            }
        });
    };
}
```

4. 通过任何浏览器选项卡使 stars.jpeg 可用

你可能想知道为什么，在传递 `images/stars.jpeg` 时必须使用 `chrome.extension.getURL` 部件版式扩展 API，而不是仅仅传入相对 URL 而不使用上一部分中所述的额外前缀。  顺便说一句，附加图像后 `getUrl` 返回的额外前缀如下所示。

```http
extension://inigobacliaghocjiapeaaoemkjifjhp/images/stars.jpeg
```

原因是要使用 `src` 元素的属性 `img` 将图像注入内容页。  内容页在一个与运行扩展的线程不同的唯一线程上运行。  必须将静态映像文件公开为 Web 资产才能正常工作。

在文件中 `manifest.json` 添加另一个条目，声明图像可用于所有浏览器选项卡。  该条目如下 (在添加即将) 的内容脚本声明时，应在下面的完整 `manifest.json` 文件中看到该条目。

```json
"web_accessible_resources": [
    "images/*.jpeg"
]
```

现在，你已在文件中 `popup.js` 编写代码，将消息发送到嵌入在当前活动选项卡页上的内容页，但尚未创建并注入该内容页。  立即执行此操作。

5.  更新 manifest.json 以进行内容和 Web 访问

`manifest.json`更新后，包括和`content-scripts``web_accessible_resources`如下所示。

```json
{
    "name": "NASA picture of the day viewer",
    "version": "0.0.0.1",
    "manifest_version": 2,
    "description": "An extension to display the NASA picture of the day.",
    "icons": {
        "16": "icons/nasapod16x16.png",
        "32": "icons/nasapod32x32.png",
        "48": "icons/nasapod48x48.png",
        "128": "icons/nasapod128x128.png"
    },
    "browser_action": {
        "default_popup": "popup/popup.html"
    },
    "content_scripts": [
        {
            "matches": [
              "<all_urls>"
            ],
            "js": ["lib/jquery.min.js","content-scripts/content.js"]
        }
    ],
    "web_accessible_resources": [
        "images/*.jpeg"
    ]
}
```

你添加的部分是 `content_scripts`。  该 `matches` 属性设置为 `<all_urls>`，这意味着在 `content_scripts` 加载每个选项卡时，所有文件都注入到所有浏览器选项卡页中。  可以注入的允许文件类型是 JavaScript 和 CSS。  你还添加了 `libjquery.min.js`。  可以从节顶部提到的下载中包含该内容。

6. 添加 jQuery 并了解关联的线程

在要注入的内容脚本中，计划使用 jQuery (`$`) 。  你添加了一个已缩小的 jQuery 版本，并将其放入扩展包中。`lib\jquery.min.js`  这些内容脚本在单个沙盒中运行，这意味着注入页面的 `popup.js` jQuery 不会与内容共享。

请记住，即使浏览器选项卡在加载的网页上运行 JavaScript，注入的任何内容也无法访问。  注入的 JavaScript 仅有权访问在该浏览器选项卡中加载的实际 DOM。

7. 添加内容脚本消息侦听器

下面是`content-scripts\content.js`根据你的`manifest.json``content-scripts`分区注入到每个浏览器选项卡页的文件。

```javascript
chrome.runtime.onMessage.addListener(function(request, sender, sendResponse) {
    $("body").prepend(
        `<img  src="${request.url}" id="${request.imageDivId}"
               class="slide-image" /> `
    );
    $("head").prepend(
        `<style>
          .slide-image {
              height: auto;
              width: 100vw;
          }
        </style>`
    );
    $(`#${request.imageDivId}`).click(function() {
        $(`#${request.imageDivId}`).remove(`#${request.imageDivId}`);
    });
    sendResponse({ fromcontent: "This message is from content.js" });
});
```

请注意，上述所有 JavaScript 都是使用`chrome.runtime.onMessage.addListener`扩展 API 方法注册`listener`的。  此侦听器等待消息，如前面`chrome.tabs.sendMessage`所述的扩展 API 方法发送`popup.js`的消息。

该方法的第一个参数 `addListener` 是一个函数，其第一个参数请求是传入的消息的详细信息。  请记住，使用 `popup.js`该方法时 `sendMessage` ，第一个参数的这些属性是 `url` 和 `imageDivId`。

侦听器处理事件时，将运行第一个参数的函数。  该函数的第一个参数是具有分配的属性的 `sendMessage`对象。  该函数只处理三个 jQuery 脚本行。

*   第一个脚本行动态插入到 DOM 标头中， **\<style\>** 必须将该节分配为元素的 `slide-image` 类 `img` 。
*   第二个脚本行在浏览器选项卡下方`body`追加一个`img`元素，该元素分配了`slide-image`类以及`imageDivId`该映像元素的 ID。
*   第三个脚本行添加了一个 `click` 事件，该事件涵盖整个图像，允许用户在图像的任意位置进行选择，并且该图像从页面 (以及事件侦听器) 中删除。

8. 添加功能以在选择时删除显示的图像

现在，浏览到任何页面并选择 **“扩展** ”图标时，弹出菜单将按如下所示显示。

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="popup.html选择“扩展”图标后显示。":::
   选择“扩展”图标后popup.html显示
:::image-end:::

<!-- ![popup.html display after selecting the Extension icon] -->

选择按 `Display` 钮时，将获得以下内容。  如果选择图像上的 `stars.jpeg` 任意位置，则会删除该图像元素，并且选项卡页会折叠回最初显示的内容。

:::image type="complex" source="./media/part2-showingimage.png" alt-text="显示在浏览器中的图像。":::
   浏览器中显示的图像
:::image-end:::

你已创建一个扩展，该扩展已成功从扩展图标弹出窗口发送消息，并在浏览器选项卡上动态插入作为内容运行的 JavaScript。 注入的内容设置图像元素以显示静态星 `.jpeg` 形文件。
