---
title: 使用Visual Studio Code调试 WebView2 应用
description: 如何使用Microsoft Visual Studio代码调试 WebView2 应用。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/11/2022
ms.openlocfilehash: 8a455e8f858581c9cd296f257aecb9b0dbbc5e99
ms.sourcegitcommit: 5351b3950b3bb7bc698415a2e5608816f1f9fca4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2022
ms.locfileid: "12473822"
---
# <a name="debug-webview2-apps-with-visual-studio-code"></a>使用Visual Studio Code调试 WebView2 应用

使用Microsoft Visual Studio代码调试在 WebView2 控件中运行的脚本。  <!-- Make sure you're using Visual Studio Code version [insert build here] or later. -->


<!-- ====================================================================== -->
## <a name="create-a-launchjson-file"></a>创建 launch.json 文件

若要调试代码，项目需要有一个 `launch.json` 文件。  如果项目没有 `launch.json` 文件，请创建一个新 `launch.json` 文件并将以下代码粘贴到其中：

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

Visual Studio Code源路径映射现在需要一个 URL，因此应用现在在启动时接收`url`命令行参数。  如果需要， `url` 可以安全地忽略该参数。


<!-- ====================================================================== -->
## <a name="debug-your-code"></a>调试代码

1. 若要在源代码中设置断点，请单击一行代码，然后按 `F9`下：

   :::image type="content" source="./media/breakpoint-vs.png" alt-text="在Visual Studio Code中设置的断点。" lightbox="./media/breakpoint-vs.png":::

1. 在 **“运行”** 选项卡上，从下拉菜单中选择启动配置。

1. 单击 **“开始调试**”，这是启动配置下拉列表旁边的绿色三角形。

   :::image type="content" source="./media/run-vs.png" alt-text="Visual Studio Code中的“运行”选项卡。" lightbox="./media/run-vs.png":::

1. 若要查看调试输出和错误，请打开 **调试控制台**。

   :::image type="content" source="./media/results-vs.png" alt-text="Visual Studio Code中的调试控制台。" lightbox="./media/results-vs.png":::


<!-- ====================================================================== -->
## <a name="targeted-webview2-debugging"></a>目标 WebView2 调试

在某些 WebView2 应用中，可以使用多个 WebView2 控件。  若要选择在这种情况下要调试的 WebView2 控件，可以使用目标 WebView2 调试。

打开 `launch.json` 并完成以下操作，以使用目标 WebView2 调试。

1. 确认 `useWebview` 参数已设置为 `true`。

1. `urlFilter`添加参数。  当 WebView2 控件导航到 URL 时， `urlFilter` 参数值用于比较 URL 中显示的字符串。

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

调试应用时，可能需要从呈现过程开始逐步完成代码。 如果要在网站上呈现网页，而你无权访问源代码，则可以使用此 `?=value` 选项，因为网页忽略无法识别的参数。


### <a name="cannot-debug-two-webview2-controls-at-the-same-time"></a>无法同时调试两个 WebView2 控件

在 URL 中找到第一个匹配项后，调试器将停止。  不能同时调试两个 WebView2 控件，因为 CDP 端口由所有 WebView2 控件共享，并使用单个端口号。


<!-- ====================================================================== -->
## <a name="debug-running-processes"></a>调试正在运行的进程

可能需要将调试器附加到正在运行的 WebView2 进程。  为此，请在 `launch.json`其中更新 `request` 参数，将其值更改为 `attach`：

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

WebView2 控件必须打开 CDP 端口以允许调试 WebView2 控件。  在启动调试器之前，必须生成代码以确保只有一个 WebView2 控件具有 Chrome 开发人员协议 (CDP) 端口打开。


<!-- ====================================================================== -->
## <a name="debug-tracing-options"></a>调试跟踪选项

若要启用调试跟踪，请将参数添加 `trace` 到 `launch.json` 其中，如下所示：

1. `trace`添加参数：

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

将调试输出保存到日志文件：

:::image type="content" source="./media/trace-log.png" alt-text=" 将调试输出保存到日志文件。" lightbox="./media/trace-log.png":::
      
```json
,"trace": "verbose"  // Turn on verbose tracing in the Debug Output pane.
```

Visual Studio Code启用详细跟踪的调试输出：

:::image type="content" source="./media/verbose.png" alt-text="Visual Studio Code启用详细跟踪的调试输出。" lightbox="./media/verbose.png":::


<!-- ====================================================================== -->
## <a name="debug-office-add-ins"></a>调试Office加载项

如果要调试Office外接程序，请在单独的Visual Studio Code实例中打开加载项源代码。  在 WebView2 应用中打开 `launch.json` 。  将以下代码`launch.json`添加到其中，将调试器附加到Office加载项：

```json
,"debugServer": 4711
```


<!-- ====================================================================== -->
## <a name="troubleshoot-the-debugger"></a>排查调试器问题

使用调试器时，可能会遇到这些情况。


### <a name="doesnt-stop-at-breakpoint"></a>不会在断点处停止

如果调试器未停止在断点，并且你有调试输出： 

若要解决此问题，请确认带断点的文件与 WebView2 控件使用的相同文件。  调试器不执行源路径映射。


### <a name="cant-attach-to-running-process"></a>无法附加到正在运行的进程

如果无法附加到正在运行的进程，则会出现超时错误：

若要解决此问题，请确认 WebView2 控件已打开 CDP 端口。  确保注册 `additionalBrowserArguments` 表中的值正确或选项正确。  请参阅 [其他BrowserArguments for dotnet](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.additionalbrowserarguments) 和 [additionalBrowserArguments for Win32](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also)_Microsoft Edge WebView2 简介_。
