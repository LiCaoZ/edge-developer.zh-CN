---
title: 创建扩展教程，第 1 部分
description: 构建一个扩展，弹出美国宇航局当天的图片。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
ms.openlocfilehash: 8285fe5cabf2828a65d7b2b6bac7bc5110446ef0
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522222"
---
# <a name="create-an-extension-tutorial-part-1"></a>创建扩展教程，第 1 部分


<!-- ====================================================================== -->
## <a name="overview"></a>概述

本教程的目标是从空目录开始生成Microsoft Edge扩展。  你正在构建一个扩展，弹出美国宇航局当天的照片。  在本教程中，你将了解如何通过以下方式创建扩展：

*   `manifest.json`创建文件。
*   添加图标。
*   打开默认弹出对话框。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

若要测试在本教程中生成的已完成扩展，请下载 [源代码](https://github.com/MicrosoftEdge/MicrosoftEdge-Extensions-Demos/tree/master/extension-getting-started-part1/part1)。<!-- changing master to main doesn't work 5/19/2022 -->


<!-- ====================================================================== -->
## <a name="step-1-create-a-manifestjson-file"></a>步骤 1：创建 manifest.json 文件

每个扩展包都必须有一个 `manifest.json` 位于根目录的文件。  清单提供扩展、扩展包版本、扩展名称和说明等的详细信息。

以下代码片段概述了文件中 `manifest.json` 所需的基本信息。

```json
{
    "name": "NASA picture of the day viewer",
    "version": "0.0.0.1",
    "manifest_version": 2,
    "description": "An extension to display the NASA picture of the day."
}
```


<!-- ====================================================================== -->
## <a name="step-2-add-icons"></a>步骤 2：添加图标

通过在项目中创建`icons`目录来存储图标图像文件来"开始"菜单。  这些图标用于用户选择启动扩展的按钮的背景图像。

:::image type="complex" source="./media/part1-badge1.png" alt-text="用于打开扩展的工具栏上的图标。":::
   用于打开扩展的工具栏上的图标
:::image-end:::

对于图标：
*  建议使用`PNG`格式，但也可以使用 `ICO` `BMP``GIF`或`JPEG`使用格式。
*  建议使用 128 x 128 px 的图像，如有必要，浏览器会调整其大小。

项目的目录应类似于以下结构。

```shell
└── part1
    ├── _manifest.json
    └── icons
        ├── nasapod16x16.png
        ├── nasapod32x32.png
        ├── nasapod48x48.png
        └── nasapod128x128.png
```

接下来，将图标添加到 `manifest.json` 文件。 `manifest.json`使用图标信息更新文件，使其与以下代码片段匹配。 `png`以下代码中列出的文件在本文前面提到的下载文件中可用。

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
    }
}
```


<!-- ====================================================================== -->
## <a name="step-3-open-a-default-pop-up-dialog"></a>步骤 3：打开默认弹出对话框

现在，创建要 `HTML` 在用户启动扩展时运行的文件。  创建在命名`popup`目录中命名`popup.html`的 HTML 文件。  当用户选择要启动扩展的图标时， `popup/popup.html` 将显示为模式对话框。

添加以下代码片段中的代码以 `popup.html` 显示星形图像。

```html
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>NASA picture of the day</title>
    </head>
    <body>
        <div>
            <img src="/images/stars.jpeg" alt="Display the stars image" />
        </div>
    </body>
</html>
```

确保将映像文件添加到映像文件 `images/stars.jpeg` 夹。  项目的目录应类似于以下结构。

```shell
└── part1
    ├── _manifest.json
    ├── icons
    │   ├── nasapod16x16.png
    │   ├── nasapod32x32.png
    │   ├── nasapod48x48.png
    │   └── nasapod128x128.png
    ├── images
    │   └── stars.jpeg
    └── popup
        └── popup.html
```

最后，请确保在 `manifest.json` 下面 `browser_action`注册弹出窗口，如以下代码片段中所示。

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
    }
}
```


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

这是开发工作扩展所需的一切。  现在，继续旁加载和测试扩展。  有关详细信息，请参阅 [旁加载扩展](extension-sideloading.md)。
