---
title: 使用应用程序调试 WebView2 Visual Studio Code
description: 如何使用代码调试 WebView2 Microsoft Visual Studio代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/11/2022
ms.openlocfilehash: e8dfa32961306324c682059a14bad39f942402b8
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433508"
---
# <a name="debug-webview2-apps-with-visual-studio-code"></a>使用应用程序调试 WebView2 Visual Studio Code

使用Microsoft Visual Studio代码调试在 WebView2 控件中运行的脚本。  <!-- Make sure you're using Visual Studio Code version [insert build here] or later. -->


<!-- ====================================================================== -->
## <a name="create-a-launchjson-file"></a>创建 launch.json 文件

若要调试代码，项目需要具有文件 `launch.json` 。  如果您的项目没有文件，`launch.json``launch.json`请创建一个新文件，然后将以下代码粘贴到该文件中：

```json
"name": "Hello debug world",
"type": "pwa-msedge",
"port": 9222, // The port value is optional, and the default value is 9222.
"request": "launch",
"runtimeExecutable": "C:/path/to/your/webview2/app.exe",
"env": {
   // Customize for your app location if needed
   "Path": "%path%;e:/path/to/your/app/location; "
},
"useWebView": true,
// The following two lines set up source path mapping, where `url` is the start page
// of your app, and `webRoot` is the top level directory with all your code files.
"url": "file:///${workspaceFolder}/path/to/your/toplevel/foo.html",
"webRoot": "${workspaceFolder}/path/to/your/assets"
```

### <a name="command-line-url-parameter-passed-in"></a>传入的命令行 URL 参数

Visual Studio Code源路径映射现在需要 URL`url`，因此你的应用现在在启动时会收到命令行参数。  如果需要，可以安全地 `url` 忽略参数。


<!-- ====================================================================== -->
## <a name="debug-your-code"></a>调试代码

1. 若要在源代码中设置断点，请单击一行代码，然后按 `F9`：

   :::image type="content" source="./media/breakpoint-vs.png" alt-text="在 Visual Studio Code 中设置的断Visual Studio Code。" lightbox="./media/breakpoint-vs.png":::

1. 在" **运行** "选项卡上，从下拉菜单中选择启动配置。

1. 单击 **启动调试**，这是启动配置下拉列表旁边的绿色三角形。

   :::image type="content" source="./media/run-vs.png" alt-text="&quot;运行&quot;选项卡Visual Studio Code。" lightbox="./media/run-vs.png":::

1. 若要查看调试输出和错误，请打开调试 **控制台**。

   :::image type="content" source="./media/results-vs.png" alt-text="调试控制台Visual Studio Code。" lightbox="./media/results-vs.png":::


<!-- ====================================================================== -->
## <a name="targeted-webview-debugging"></a>目标 WebView 调试

在某些 WebView2 应用中，您可能会使用多个 WebView2 控件。  若要选择在这种情况下要调试的 WebView2 控件，可以使用目标 WebView2 调试。

打开 `launch.json` 并完成以下操作以使用目标 Webview 调试。

1. 确认参数 `useWebview` 设置为 `true`。

1. 添加 参数 `urlFilter` 。  当 WebView2 控件导航到 URL `urlFilter` 时，参数值用于比较 URL 中出现的字符串。

```json
"useWebview": "true",
"urlFilter": "*index.ts",

// Options for "urlFilter":
// Match any url that ends with "index.ts":
"urlFilter": "*index.ts",
// Match any url that contains "index" anywhere in the URL:
"urlFilter": "*index*",
// Explicitly match a file named "index.ts":
"urlFilter": "file://C:/path/to/my/index.ts",
```

在调试应用时，你可能需要从呈现过程开始逐步调试代码。 如果您在网站上呈现 `?=value` 网页，但无法访问源代码，可以使用 选项，因为网页将忽略无法识别的参数。


### <a name="cannot-debug-two-webview2-controls-at-the-same-time"></a>无法同时调试两个 WebView2 控件

在 URL 中发现第一个匹配项后，调试程序将停止。  不能同时调试两个 WebView2 控件，因为 CDP 端口由所有 WebView2 控件共享，并且使用单个端口号。


<!-- ====================================================================== -->
## <a name="debug-running-processes"></a>调试正在运行的进程

你可能需要将调试器附加到运行 WebView2 进程。  为此，在 `launch.json`中更新 参数 `request` ，将参数的值更改为 `attach`：

```json
"name": "Hello debugging world",
"type": "pwa-msedge",
"port": 9222,
"request": "attach",
"runtimeExecutable": "C:/path/to/your/webview2/app.exe",
"env": {
   "Path": "%path%;e:/path/to/your/build/location; "
},
"useWebView": true
```

WebView2 控件必须打开 CDP 端口以允许调试 WebView2 控件。  必须生成代码，以确保在启动调试程序之前，只有一个 WebView2 控件具有打开的 Chrome 开发人员协议 (CDP) 打开。


<!-- ====================================================================== -->
## <a name="debug-tracing-options"></a>调试跟踪选项

若要启用调试跟踪，请向 `trace` 添加 参数 `launch.json` ，如下所示：

1. 添加 参数 `trace` ：

```json
"name": "Hello debugging world",
"type": "pwa-msedge",
"port": 9222,
"request": "attach",
"runtimeExecutable": "C:/path/to/your/webview2/app.exe",
"env": {
"Path": "%path%;e:/path/to/your/build/location; "
},
"useWebView": true
,"trace": true  // Turn on debug tracing, and save the output to a log file.
```

将调试输出保存为日志文件：

:::image type="content" source="./media/trace-log.png" alt-text=" 将调试输出保存到日志文件。" lightbox="./media/trace-log.png":::
      
```json
,"trace": "verbose"  // Turn on verbose tracing in the Debug Output pane.
```

Visual Studio Code详细跟踪打开后调试输出：

:::image type="content" source="./media/verbose.png" alt-text="Visual Studio Code&quot;调试输出&quot;，并打开详细跟踪。" lightbox="./media/verbose.png":::


<!-- ====================================================================== -->
## <a name="debug-office-add-ins"></a>调试Office加载项

如果要调试加载项Office，请打开加载项源代码，在加载项的单独实例中Visual Studio Code。  在 `launch.json` WebView2 应用中打开。  将以下代码添加到 `launch.json`，以将调试器附加到Office加载项：

```json
,"debugServer": 4711
```


<!-- ====================================================================== -->
## <a name="troubleshoot-the-debugger"></a>调试器疑难解答

使用调试器时可能会遇到这些情况。


### <a name="doesnt-stop-at-breakpoint"></a>在断点处不停止

如果调试器未在断点停止，并且你有调试输出： 

若要解决此问题，请确认断点为的文件与 WebView2 控件所使用的文件相同。  调试程序不执行源路径映射。


### <a name="cant-attach-to-running-process"></a>无法附加到正在运行的进程

如果无法附加到正在运行的进程，并且收到超时错误：

若要解决此问题，请确认 WebView2 控件打开了 CDP 端口。  请确保注册表 `additionalBrowserArguments` 中的值正确，或者选项正确。  请参阅 [additionalBrowserArguments for dotnet](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.additionalbrowserarguments) 和 [additionalBrowserArguments for Win32](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
