---
title: 处理渐进式 Web 应用中的文件
description: 如何将你的 PWA注册为文件处理程序，以将其更深入地集成到操作系统中。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/01/2021
ms.openlocfilehash: 9b60abbfb53ed845fd3727f6fcccc15b8c6544f8
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432899"
---
# <a name="handle-files-in-progressive-web-apps"></a>处理渐进式 Web 应用中的文件

可处理文件的渐进式 Web 应用感觉更为用户本机，并且更好地集成到操作系统中。

网站已允许用户[`<input type="file">`](https://developer.mozilla.org/docs/Web/API/File/Using_files_from_web_applications)使用 或 拖放上传文件，但 PWA 进一步操作，并可在操作系统上注册为文件处理程序。

当PWA注册为某些文件类型的文件处理程序时，操作系统可以在用户打开这些文件时自动启动该应用，这类似于Microsoft Word文件`.docx`的方式。


<!-- ====================================================================== -->
## <a name="enable-the-file-handling-api"></a>启用文件处理 API

文件处理功能是实验性的。

若要启用文件处理功能，

1.  转到"`edge://flags`Microsoft Edge"。
1.  选择 **"搜索标志** "并键入"文件处理 API"。
1.  选择 ******DefaultEnabledRestart** > **** > 。

    :::image type="content" source="../media/enable-file-handling-experiment.png" alt-text="启用&quot;文件处理 API&quot;实验。":::


<!-- ====================================================================== -->
## <a name="define-which-files-your-app-handles"></a>定义应用处理的文件

首先要声明应用处理哪些类型的文件。 此操作在应用清单[文件中使用](web-app-manifests.md)`file_handlers`数组成员完成。

数组的每个条目 `file_handlers` 都需要有两个属性：

*  `action`：操作系统在启动应用时应导航到PWA。
*  `accept`：接受文件类型的对象。 键是 MIME 类型 `*` (，使用通配符符号接受部分类型，) ，值是接受的文件扩展名的数组。

请考虑以下示例：

```json
{
    "file_handlers": [
        {
            "action": "/openFile",
            "accept": {
                "text/*": [
                    ".txt"
                ]
            }
        }
    ]
}
```

此示例中，应用为接受文本文件的单个文件处理程序注册。 `.txt`例如，当用户通过双击桌面上的图标来打开文件时，操作系统会使用该 URL 启动`/openFile`应用。


<!-- ====================================================================== -->
## <a name="detect-whether-the-file-handling-api-is-available"></a>检测文件处理 API 是否可用

在处理文件之前，你的应用需要检查文件处理 API 在设备和浏览器中是否可用。

若要检查文件处理 API 是否可用，请测试 `launchQueue` 对象是否存在，如下所示：

```javascript
if ('launchQueue' in window) {
    console.log('File Handling API is supported!');
} else {
    console.error('File Handling API is not supported!');
}
```


<!-- ====================================================================== -->
## <a name="handle-files-on-launch"></a>在启动时处理文件

当应用在打开文件后 `launchQueue` 由操作系统启动时，可以使用 对象访问文件内容。

使用以下 JavaScript 代码处理文本内容：

```javascript
if ('launchQueue' in window) {
    console.log('File Handling API is supported!');

    launchQueue.setConsumer(launchParams => {
        handleFiles(launchParams.files);
    });
} else {
    console.error('File Handling API is not supported!');
}

async function handleFiles(files) {
    for (const file of files) {
        const blob = await file.getFile();
        blob.handle = file;
        const text = await blob.text();

        console.log(`${file.name} handled, content: ${text}`);
    }
}
```

对象 `launchQueue` 将所有启动的文件排队，直到使用 设置使用者 `setConsumer`。 若要详细了解 和 `launchQueue` `launchParams` 对象，请转到文件 [处理说明器](https://github.com/WICG/file-handling/blob/main/explainer.md#launch)。


<!-- ====================================================================== -->
## <a name="demo"></a>演示版

"我的PWA是一款使用文件处理功能处理文件的主要演示`.gpx`应用。 若要试用此演示应用的功能：

*  [在"管理"](#enable-the-file-handling-api)中Microsoft Edge。
*  转到 ["我的跟踪"](https://captainbrosset.github.io/mytracks/) 并安装应用。
*  在计算机上下载 GPX 文件。 可以使用此测试 [GPX 文件](https://www.visugpx.com/download.php?id=okB1eM4fzj)。
*  打开下载的 GPX 文件。

请注意，应用会自动启动，Microsoft Edge请求你处理此文件的权限。

:::image type="content" source="../media/my-tracks-allow-file-handling.png" alt-text="&quot;打开文件？&quot;。 权限请求对话框。":::

如果你允许应用处理文件，应用的边栏中会显示一个新条目，你可以单击它旁边的复选框来可视化相应的 GPS 轨。

:::image type="content" source="../media/my-tracks-new-file.png" alt-text="由&quot;我的跟踪&quot;应用处理的新 GPS 轨。":::

可以在"我的跟踪"存储库上访问此应用程序[GitHub代码](https://github.com/captainbrosset/mytracks)。

* [manifest.json](https://github.com/captainbrosset/mytracks/blob/main/mytracks/manifest.json) 源文件使用 数组`file_handlers`请求处理`.gpx`文件。
* 文件 [file.js](https://github.com/captainbrosset/mytracks/blob/main/src/file.js) 文件 `launchQueue` 使用 对象来处理传入文件。
