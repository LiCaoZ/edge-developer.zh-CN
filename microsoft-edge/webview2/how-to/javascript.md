---
title: 在 WebView 中对扩展方案使用 JavaScript
description: 如何在 WebView2 应用中的复杂方案中使用 JavaScript。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.date: 05/06/2021
ms.openlocfilehash: c8e350941112a06b694c0112acf6256f87e608bc
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12286189"
---
# <a name="use-javascript-in-webview-for-extended-scenarios"></a>在 WebView 中对扩展方案使用 JavaScript

使用 WebView2 控件中的 JavaScript，可以自定义本机应用以满足你的要求。  本文探讨如何在 WebView2 中使用 JavaScript，并回顾如何使用高级 WebView2 特性和功能进行开发。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

本文假定您已有一个工作项目。  如果你没有项目，并且想要继续，请参阅 [WebView2 入门指南](../index.md#get-started)。


<!-- ====================================================================== -->
## <a name="basic-webview2-functions"></a>基本 WebView2 函数

使用以下函数开始在 WebView 应用中嵌入 JavaScript。

| API  | 描述  |
|:--- |:--- |
| [ExecuteScriptAsync](/dotnet/api/microsoft.web.webview2.wpf.webview2.executescriptasync) | 在 WebView 控件中运行 JavaScript。 有关详细信息，请导航到入门教程。 |
| [OnDocumentCreatedAsync](/microsoft-edge/webview2/reference/win32/icorewebview2#addscripttoexecuteondocumentcreated) | 创建文档对象模型或 DOM (时) 运行。 |


<!-- ====================================================================== -->
## <a name="scenario-running-a-dedicated-script-file"></a>方案：运行专用脚本文件

在此部分中，你将从 WebView2 控件访问专用的 JavaScript 文件。

> [!NOTE]
> 尽管内联编写 JavaScript 对于快速 JavaScript 命令可能非常高效，但会丢失 JavaScript 颜色主题和行格式，这使得在 JavaScript 中编写大量代码Visual Studio。

若要解决此问题，请用代码创建单独的 JavaScript 文件，然后使用 参数传递对该文件 `ExecuteScriptAsync` 的引用。

1.  在 `.js` 项目中创建文件，并添加要运行的 JavaScript 代码。  例如，创建一个称为 的文件 `script.js` 。
1.  将 JavaScript 文件转换为传递给 的字符串 `ExecuteScriptAsync` 。
    1.  若要将 JavaScript 文件转换为字符串，请复制以下代码段。

        ```csharp
        string text = System.IO.File.ReadAllText(@"C:\PATH_TO_YOUR_FILE\script.js");
        ```

    1.  将代码粘贴到 `MainWindow.xaml.cs` 中。
1.  使用 传递文本变量 `ExecuteScriptAsync` 。

    ```csharp
    await webView.CoreWebView2.ExecuteScriptAsync(text);
    ```


<!-- ====================================================================== -->
## <a name="scenario-removing-drag-and-drop-functionality"></a>方案：删除拖放功能

在此部分中，使用 JavaScript 从 WebView2 控件中删除拖放功能。

首先，了解当前的拖放功能：

1.  创建 `.txt` 文件以拖放。  例如，创建一个名为 的文件 `contoso.txt` ，并添加文本。

1.  运行项目。

1.  将文件拖放到 `contoso.txt` WebView 控件上。  将打开一个新窗口，这是示例项目中代码的结果。

    :::image type="content" source="./media/drag-text.png" alt-text="拖放操作的结果contoso.txt。" lightbox="./media/drag-text.png":::

接下来，添加代码以从 WebView2 控件中删除拖放功能：

1.  将以下代码段复制并粘贴到 `InitializeAsync()` 中 `MainWindow.xaml.cs` 。

    ```csharp
    await webView.CoreWebView2.ExecuteScriptAsync("window.addEventListener('dragover',function(e){e.preventDefault();},false);");

    await webView.CoreWebView2.ExecuteScriptAsync("window.addEventListener('drop',function(e){" +
    "e.preventDefault();" +
    "console.log(e.dataTransfer);" +
    "console.log(e.dataTransfer.files[0])" +
    "}, false);");
    ```

1.  运行项目。

1.  尝试拖放 `contoso.txt` 。  确认你无法拖放。


<!-- ====================================================================== -->
## <a name="scenario-removing-the-context-menu"></a>方案：删除上下文菜单

在此部分中，从 WebView2 控件 (右键单击菜单) 默认上下文菜单。

若要开始，请浏览右键单击菜单的当前功能：

1.  运行项目。

1.  右键单击 WebView2 控件上的任意位置。  上下文菜单显示默认的右键单击菜单命令。

    :::image type="content" source="./media/context-menu.png" alt-text="右键单击菜单，显示默认命令。" lightbox="./media/context-menu.png":::

现在，添加代码以从 WebView2 控件中删除上下文菜单功能。

1.  将以下代码段复制并粘贴到 `InitializeAsync()` 中 `MainWindow.xaml.cs` 。

    ```csharp
    await webView.CoreWebView2.ExecuteScriptAsync("window.addEventListener('contextmenu', window => {window.preventDefault();});");
    ```

1.  再次运行代码。  确认无法打开上下文菜单 (右键单击) 。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebView2 入门指南](../index.md#get-started)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [WebView2 API 参考](../webview2-api-reference.md)
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
