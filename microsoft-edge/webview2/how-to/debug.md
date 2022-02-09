---
title: 开始调试 WebView2 应用
description: 了解如何调试 WebView2 控件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 09/15/2021
ms.openlocfilehash: 32348a8453bed15de80b9bd05d869e650e6300eb
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345658"
---
# <a name="get-started-debugging-webview2-apps"></a>开始调试 WebView2 应用

WebView2 Microsoft Edge的目标是将 Web 和本机应用开发功能和工具的最佳组合在一起。  开发 WebView2 应用时，应调试应用。

本文概述了用于调试 Web 代码和 WebView2 应用中的本机代码的不同工具。


<!-- ====================================================================== -->

## [<a name="microsoft-edge-devtools"></a>Microsoft Edge 开发工具](#tab/devtools)

使用[Microsoft Edge工具](../index.md)调试 WebView2 控件中显示的 Web 内容，方式与调试 WebView2 控件中显示的其他网页Microsoft Edge。

若要在查看 WebView2 应用时打开 DevTools，将焦点放在 WebView 控件上，然后执行下列操作之一：

*  按 `F12`。
*  按 `Ctrl`++`Shift``I`。
*  右键单击页面，然后选择 `Inspect`。

请参阅 [DevTools 概述](../index.md)。

<!-- keep lightbox -->
:::image type="content" source="./media/f12.png" alt-text="DevTools 调试。" lightbox="./media/f12.png":::


<!-- ====================================================================== -->

## [<a name="visual-studio"></a>Visual Studio](#tab/visualstudio)

Visual Studio WebView2 应用中为 Web 和本机代码提供各种调试工具。  在Visual Studio部分中，主要焦点是调试 WebView 控件，但其他调试方法Visual Studio一样可用。  使用以下过程仅调试 Win32 应用或 Office中的 Web 和本机代码。

> [!IMPORTANT]
> 当你在附加了本机调试Visual Studio`F12`中调试应用时，按可能会触发本机调试器，而不是开发人员工具。  若要避免这种情况，请按 或`Ctrl`++`Shift``I`右键单击。


开始之前，请确保满足以下要求：

*  若要调试脚本，必须从应用程序内启动Visual Studio。

*  无法将调试器附加到正在运行的 WebView2 进程。

*  安装 Visual Studio 2019 版本 16.4 预览版 2 或更高版本。


安装并设置脚本调试器工具，Visual Studio：

1. 使用 C **++ 在桌面开发中安装 JavaScript** **诊断**组件，如下所示：

   1. 在"Windows资源管理器"栏中，键入 `Visual Studio Installer`。

   1. 选择**Visual Studio 安装程序**打开它。

   1. In the Visual Studio 安装程序， on the installed version， click the **More** button， and then select **Modify**.

   1. In Visual Studio， under **Workloads**， select the **Desktop Development with C++** setting：

      :::image type="content" source="./media/workloads.png" alt-text="Visual Studio修改工作负载屏幕。" lightbox="./media/workloads.png":::

   1. 选择 **顶部的"** 单个组件"。

   1. 在搜索框中，输入 `JavaScript diagnostics`。

   1. 选择 **"JavaScript 诊断"** 设置。

   1. 单击 **"修改"**。

      :::image type="content" source="./media/indiv-comp.png" alt-text="Visual Studio：修改&quot;单个组件&quot;选项卡中的值。" lightbox="./media/indiv-comp.png":::

1. 为 WebView2 应用启用脚本调试。

   1. 右键单击 WebView2 项目，然后选择"属性 **"**。

   1. 在" **配置属性"下**，选择 **"调试"**。

   1. 在调试 **器类型下**，选择 **"JavaScript (WebView2) " **。

      :::image type="content" source="./media/enb-js.png" alt-text="中&quot;调试&quot;配置Visual Studio。" lightbox="./media/enb-js.png":::


调试 WebView2 应用：

1. 若要在源代码中设置断点，请将鼠标悬停在行号的左侧，然后单击以设置断点。  JS/TS 调试适配器不执行源路径映射。  必须打开与 WebView2 关联的完全相同的路径。

   :::image type="content" source="./media/breakpoint.png" alt-text="在 Visual Studio 中添加断Visual Studio。" lightbox="./media/breakpoint.png":::

1. 若要运行调试器，请选择平台的位大小，然后单击"本地调试器"旁边的绿色"播放Windows**按钮**。  应用运行，调试程序连接到创建的第一个 WebView2 进程。

   :::image type="content" source="./media/run.png" alt-text="本地Windows调试器Visual Studio。" lightbox="./media/run.png":::

1. 在 **调试控制台中**，查找调试器的输出。

   :::image type="content" source="./media/console.png" alt-text="调试 Visual Studio 中的控制台。" lightbox="./media/console.png":::

> [!NOTE]
> 如果使用 WebView2 [SetVirtualHostNameToFolderMapping](/dotnet/api/microsoft.web.webview2.core.corewebview2.setvirtualhostnametofoldermapping) 方法，Visual Studio 2019 中的调试器将不能理解虚拟源路径映射，因此断点无法正常工作。  此源路径映射在运行调试器时Visual Studio Code。


<!-- ====================================================================== -->

## [<a name="visual-studio-code"></a>Visual Studio Code](#tab/visualstudiocode)

使用Microsoft Visual Studio代码调试在 WebView2 控件中运行的脚本。  <!--Ensure that you're using Visual Studio Code version [insert build here] or later.  -->

在Visual Studio Code中，完成以下操作以调试代码。

1. 您的项目需要具有文件 `launch.json` 。  如果项目没有文件，请`launch.json``launch.json`创建一个新文件，并复制以下代码：

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
        // The following two lines setup source path mapping, where `url` is the start page of your app, and `webRoot` is the top level directory with all your code files.
        "url": "file:///${workspaceFolder}/path/to/your/toplevel/foo.html",
        "webRoot": "${workspaceFolder}/path/to/your/assets"
    ```

    > [!NOTE]
    > Visual Studio Code源路径映射现在需要 URL，因此你的应用现在在启动时接收命令行参数。  如果需要，可以安全地 `url` 忽略参数。



1. 若要在源代码中设置断点，请单击一行代码，然后按 `F9`：

   :::image type="content" source="./media/breakpoint-vs.png" alt-text="在 Visual Studio Code 中设置的断Visual Studio Code。" lightbox="./media/breakpoint-vs.png":::

1. 运行代码，如下所示：

   1. 在" **运行** "选项卡上，从下拉菜单中选择启动配置。

   1. 若要开始调试你的应用，请单击启动配置**** 下拉列表旁边的绿色三角形"开始调试"。

      :::image type="content" source="./media/run-vs.png" alt-text="&quot;运行&quot;选项卡Visual Studio Code。" lightbox="./media/run-vs.png":::

1. 打开 **调试控制台** 以查看调试输出和错误。

   :::image type="content" source="./media/results-vs.png" alt-text="调试控制台Visual Studio Code。" lightbox="./media/results-vs.png":::

**高级设置**：

*  目标 Web 视图调试。

   在某些 WebView2 应用中，您可能会使用多个 WebView2 控件。  若要选择在这种情况下要调试的 WebView2 控件，可以使用目标 WebView2 调试。

   打开 `launch.json` 并完成以下操作以使用目标 Webview 调试。

   1. 确认参数 `useWebview` 设置为 `true`。

   1. 添加 参数 `urlFilter` 。  当 WebView2 控件导航到 URL `urlFilter` 时，参数值用于比较 URL 中出现的字符串。

   ```json
   "useWebview": "true",
   "urlFilter": "*index.ts",

   // Other urlFilter options.
   urlFilter="*index.ts"    // Match any url that ends with index.ts, and ignore all leading characters.
   urlFilter="*index*"      // Match any url that contains the string index anywhere in the URL.
   urlFilter="file://C:/path/to/my/index.ts," // To match explicit file called index.ts.
   ```

   在调试应用时，你可能需要从呈现过程开始逐步调试代码。 如果您在网站上呈现 `?=value` 网页，但无法访问源代码，可以使用 选项，因为网页将忽略无法识别的参数。

   > [!IMPORTANT]
   > 在 URL 中发现第一个匹配项后，调试程序将停止。  无法同时调试两个 WebView2 控件，因为 CDP 端口由所有 WebView2 控件共享，并且使用单个端口号。

*  调试正在运行的进程

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

   WebView2 控件必须打开 CDP 端口以允许调试 WebView2 控件。  必须生成代码，以确保在启动调试程序之前，只有一个 WebView2 控件在 CDP (打开 Chrome 开发人员协议) 打开。

*  调试跟踪选项

   添加 参数 `trace` 以启用 `launch.json` 调试跟踪，如下所示：

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

      :::image type="content" source="./media/verbose.png" alt-text="Visual Studio Code启用详细跟踪功能调试输出。" lightbox="./media/verbose.png":::

*  调试Office加载项。

   如果要调试加载项Office，请打开加载项源代码，在加载项的单独实例中Visual Studio Code。  在 `launch.json` WebView2 应用中打开。  将以下代码添加到 `launch.json`，以将调试器附加到Office加载项：

   ```json
   ,"debugServer": 4711
   ```

*  调试器疑难解答

   使用调试器时可能会遇到以下情形：

   *  调试程序不会在断点停止，并且你有调试输出。  若要解决此问题，请确认断点为的文件与 WebView2 控件所使用的文件相同。  调试程序不执行源路径映射。

   *  无法附加到正在运行的进程，并且收到超时错误。  若要解决此问题，请确认 WebView2 控件打开了 CDP 端口。  请确保注册表 `additionalBrowserArguments` 中的值正确，或者选项正确。  请参阅 [additionalBrowserArguments for dotnet](/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.additionalbrowserarguments) 和 [additionalBrowserArguments for Win32](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions)。


* * *


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
