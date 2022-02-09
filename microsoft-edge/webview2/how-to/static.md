---
title: 静态链接 WebView2 加载程序库
description: 如何静态链接 WebView2 加载程序库。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
ms.openlocfilehash: 5fa01acb30de0c89c5a3f5804f557c217e1299f6
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345889"
---
# <a name="statically-link-the-webview2-loader-library"></a>静态链接 WebView2 加载程序库

你可能希望使用单个可执行文件（而不是许多文件的包）来分发应用程序。  若要创建单个可执行文件或减小程序包的大小，应静态链接 WebView2Loader 文件。  WebView2 SDK 包含头文件 `WebView2Loader.dll`、和 `IDL` 文件。 `WebView2Loader.dll` 是一个小型组件，可帮助应用在设备上找到 WebView2 运行时Microsoft Edge预览通道。

对于未发货的应用， `WebView2Loader.dll`请执行下列操作：

1. `.vcxproj`在文本编辑器（如文本编辑器）中打开应用Visual Studio Code。

   项目`.vcproj`文件可能是隐藏文件，这意味着该文件不会显示在Visual Studio。  若要查找隐藏文件，请使用命令行。

1. 在包含 WebView2 程序包目标文件的代码中找到NuGet部分。  代码中的位置在下图中突出显示：

   :::image type="content" source="./media/insert-here.png" alt-text="Project文件代码。" lightbox="./media/insert-here.png":::

1. 复制以下代码并将其粘贴到包含 `Microsoft.Web.WebView2.targets` 位置：

   ```xaml
   <PropertyGroup>
       <WebView2LoaderPreference>Static</WebView2LoaderPreference>
   </PropertyGroup>
   ```

   插入的代码如下所示：

   :::image type="content" source="./media/static-lib.png" alt-text="插入的代码。" lightbox="./media/static-lib.png":::

1. 编译并运行应用。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
