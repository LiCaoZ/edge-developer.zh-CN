---
description: 适用于 Win32 应用的 WebView2 入门指南
title: 在 Win32 应用中开始使用 WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/09/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html
ms.openlocfilehash: c6bfc321681888308f1e52add801dda55ae9df3b
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12157374"
---
# <a name="get-started-with-webview2-in-win32-apps"></a>在 Win32 应用中开始使用 WebView2

本文将开始创建你的第一个 WebView2 应用，并了解 [WebView2 的主要功能](https://developer.microsoft.com/microsoft-edge/webview2)。  有关单个 WebView2 API 的信息，请导航到 [API 参考](/microsoft-edge/webview2/reference/win32)。

> [!NOTE]
> 本教程引用 WebView2 示例。 若要查看或复制示例代码，请导航到 [WebView2 示例代码](https://github.com/MicrosoftEdge/WebView2Samples)。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

请确保先安装以下必备组件列表，然后再继续。

*   [WebView2](https://developer.microsoft.com/microsoft-edge/webview2)运行时或任何[Microsoft Edge Insider (preview) Channel (](https://www.microsoftedgeinsider.com/download) Beta、Dev 或 Canary) 安装在当前受支持的操作系统 (Windows 10、Windows 8.1 和 Windows 7) 上。

*   [Visual Studio](https://visualstudio.microsoft.com)安装有 C++ 支持的 2015 或更高版本。


<!-- ====================================================================== -->
## <a name="step-1---create-a-single-window-app"></a>步骤 1 - 创建单窗口应用

从包含单个主窗口的基本桌面项目开始。

> [!IMPORTANT]
> 为了更好地关注演练，请使用演练：为示例应用创建传统的 Windows 桌面应用程序 ([C++](/cpp/windows/walkthrough-creating-windows-desktop-applications-cpp?view=vs-2019&preserve-view=true)) 中修改的示例代码。  若要下载修改后的示例并开始，请导航到["WebView2 示例"。](https://github.com/MicrosoftEdge/WebView2Samples#1-getting-started-guide)

1.  在Visual Studio中，打开 `WebView2GettingStarted.sln` 。
    如果使用早期版本的 Visual Studio，请将鼠标悬停在**WebView2GettingStarted**项目上，打开上下文菜单 (右键单击") "，然后选择"**属性"。**  在**配置属性**  >  **常规**下 **，Windows SDK**版本和平台**** 工具集，以使用 Win10 SDK 和Visual Studio可用的工具集。

:::image type="complex" source="../media/tool-version.png" alt-text="工具版本" lightbox="../media/tool-version.png":::
   工具版本
:::image-end:::

Visual Studio显示错误，因为项目缺少 WebView2 头文件。  应在步骤 [2 之后修复错误](#step-2---install-webview2-sdk)。


<!-- ====================================================================== -->
## <a name="step-2---install-webview2-sdk"></a>步骤 2 - 安装 WebView2 SDK

将 WebView2 SDK 添加到项目中。  使用 NuGet 安装 Win32 SDK。

1.  将鼠标悬停在项目上，打开上下文菜单 (右键单击") "，然后选择"管理NuGet**包"。**

    :::image type="complex" source="../media/manage-nuget-packages.png" alt-text="管理 NuGet 程序包" lightbox="../media/manage-nuget-packages.png":::
       管理 NuGet 程序包
    :::image-end:::

1.  安装Windows库。
    1.  在搜索栏中，键入 `Microsoft.Windows.ImplementationLibrary` ">**选择"Microsoft.Windows"。ImplementationLibrary**。
    1.  在右侧窗口中，选择"安装 **"。**  NuGet将库下载到计算机。

        > [!NOTE]
        > 实现[Windows库](https://github.com/Microsoft/wil)和 Windows[运行时 C++ 模板](/cpp/cppcx/wrl/windows-runtime-cpp-template-library-wrl?view=vs-2019&preserve-view=true)库是可选的，并且使使用 COM 更容易作为示例。

        :::image type="complex" source="../media/wil.png" alt-text="Windows实现库" lightbox="../media/wil.png":::
           Windows实现库
        :::image-end:::

1.  安装 WebView2 SDK。
    1.  在搜索栏中，键入"> `Microsoft.Web.WebView2` **选择"Microsoft.Web.WebView2"。**
    1.  在右侧窗口中，选择"安装 **"。**  NuGet将 SDK 下载到计算机。

        :::image type="complex" source="../media/nuget.png" alt-text="NuGet 程序包管理器" lightbox="../media/nuget.png":::
           NuGet 程序包管理器
        :::image-end:::

1.  将 WebView2 标头添加到项目中。

    :::row:::
       :::column span="1":::
          在 `HelloWebView.cpp` 文件中，复制以下代码段并将其粘贴到最后一 `#include` 行之后。

          ```cpp
          // include WebView2 header
          #include "WebView2.h"
          ```
       :::column-end:::
       :::column span="1":::
          include 部分应类似于以下代码段。

          ```cpp
          ...
          #include <wrl.h>
          #include <wil/com.h>
          // include WebView2 header
          #include "WebView2.h"
          ```
       :::column-end:::
    :::row-end:::

准备好使用 WebView2 API 并生成。

### <a name="build-your-empty-sample-app"></a>生成空示例应用

若要生成并运行示例应用，请选择 `F5` 。  你的应用显示一个空窗口。

:::image type="complex" source="../media/empty-app.png" alt-text="空应用" lightbox="../media/empty-app.png":::
   空应用
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-3---create-a-single-webview-within-the-parent-window"></a>步骤 3 - 在父窗口中创建单个 WebView

将 WebView 添加到主窗口。

使用 `CreateCoreWebView2Environment` 方法设置环境，并找到Microsoft Edge控件的浏览器。  如果要指定浏览器位置、用户文件夹、浏览器标志等，也可以使用此方法，而不是 `CreateCoreWebView2EnvironmentWithOptions` 使用默认设置。  完成该方法后，在回调中运行 方法并运行 `CreateCoreWebView2Environment` `ICoreWebView2Environment::CreateCoreWebView2Controller` `ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler` `ICoreWebView2Controller::get_CoreWebView2` 方法，获取关联的 WebView。

在回调中，设置一些设置，调整 WebView 的大小以使用 100% 的父窗口，然后导航到必应。

复制以下代码段，并粘贴 `HelloWebView.cpp` 到注释之后 `// <-- WebView2 sample code starts here -->` 和注释 `// <-- WebView2 sample code ends here -->` 之前。

```cpp
// Step 3 - Create a single WebView within the parent window
// Locate the browser and set up the environment for WebView
CreateCoreWebView2EnvironmentWithOptions(nullptr, nullptr, nullptr,
    Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
        [hWnd](HRESULT result, ICoreWebView2Environment* env) -> HRESULT {

            // Create a CoreWebView2Controller and get the associated CoreWebView2 whose parent is the main window hWnd
            env->CreateCoreWebView2Controller(hWnd, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
                [hWnd](HRESULT result, ICoreWebView2Controller* controller) -> HRESULT {
                if (controller != nullptr) {
                    webviewController = controller;
                    webviewController->get_CoreWebView2(&webviewWindow);
                }

                // Add a few settings for the webview
                // The demo step is redundant since the values are the default settings
                ICoreWebView2Settings* Settings;
                webviewWindow->get_Settings(&Settings);
                Settings->put_IsScriptEnabled(TRUE);
                Settings->put_AreDefaultScriptDialogsEnabled(TRUE);
                Settings->put_IsWebMessageEnabled(TRUE);

                // Resize WebView to fit the bounds of the parent window
                RECT bounds;
                GetClientRect(hWnd, &bounds);
                webviewController->put_Bounds(bounds);

                // Schedule an async task to navigate to Bing
                webviewWindow->Navigate(L"https://www.bing.com/");

                // Step 4 - Navigation events

                // Step 5 - Scripting

                // Step 6 - Communication between host and web content

                return S_OK;
            }).Get());
        return S_OK;
    }).Get());
```

### <a name="build-your-bing-sample-app"></a>生成必应示例应用

若要生成并运行应用，请选择 `F5` 。  现在，你有一个 WebView 窗口，必应页面。

:::image type="content" source="../media/bing-window.png" alt-text="必应窗口" lightbox="../media/bing-window.png":::


<!-- ====================================================================== -->
## <a name="step-4---navigation-events"></a>步骤 4 - 导航事件

WebView2 团队已在上一步中介绍了使用 `ICoreWebView2::Navigate` 方法导航到 URL 的内容。  在导航过程中，WebView 会触发主机可以侦听的一系列事件。

1.  `NavigationStarting`
1.  `SourceChanged`
1.  `ContentLoading`
1.  `HistoryChanged`
1.  `NavigationCompleted`

有关详细信息，请参阅 [WebView2 的导航事件](../concepts/navigation-events.md)。

:::image type="content" source="../media/navigation-events.png" alt-text="导航事件" lightbox="../media/navigation-events.png":::

在错误情况下，可能会发生以下一个或多个事件，具体取决于导航是否继续错误网页。

*   `SourceChanged`
*   `ContentLoading`
*   `HistoryChanged`

> [!NOTE]
> 如果发生 HTTP 重定向，则一行 `NavigationStarting` 中有多个事件。

作为使用事件的示例，为事件注册处理程序以取消 `NavigationStarting` 任何非 https 请求。  复制以下代码段并粘贴到 `HelloWebView.cpp` 中。

```cpp
// register an ICoreWebView2NavigationStartingEventHandler to cancel any non-https navigation
EventRegistrationToken token;
webviewWindow->add_NavigationStarting(Callback<ICoreWebView2NavigationStartingEventHandler>(
    [](ICoreWebView2* webview, ICoreWebView2NavigationStartingEventArgs * args) -> HRESULT {
        PWSTR uri;
        args->get_Uri(&uri);
        std::wstring source(uri);
        if (source.substr(0, 5) != L"https") {
            args->put_Cancel(true);
        }
        CoTaskMemFree(uri);
        return S_OK;
    }).Get(), &token);
```

现在，应用不会导航到任何非 https 网站。  您可以使用类似的机制完成其他任务，例如将导航限制到您自己的域中。


<!-- ====================================================================== -->
## <a name="step-5---scripting"></a>步骤 5 - 脚本

你可以在运行时使用主机应用将 JavaScript 代码注入 WebView2 控件。  你可以任务 WebView 运行任意 JavaScript 或添加初始化脚本。  在删除 JavaScript 之前，注入的 JavaScript 适用于所有新的顶级文档和任何子框架。  注入的 JavaScript 以特定计时运行。

*   创建全局对象后运行它。
*   在运行 HTML 文档中包含的任何其他脚本之前运行它。

复制以下代码段并粘贴到 `HelloWebView.cpp` 中。

```cpp
// Schedule an async task to add initialization script that freezes the Object object
webviewWindow->AddScriptToExecuteOnDocumentCreated(L"Object.freeze(Object);", nullptr);
// Schedule an async task to get the document URL
webviewWindow->ExecuteScript(L"window.document.URL;", Callback<ICoreWebView2ExecuteScriptCompletedHandler>(
    [](HRESULT errorCode, LPCWSTR resultObjectAsJson) -> HRESULT {
        LPCWSTR URL = resultObjectAsJson;
        //doSomethingWithURL(URL);
        return S_OK;
    }).Get());
```

现在，WebView 应始终冻结 `Object` 对象并返回页面文档一次。

> [!NOTE]
> 脚本注入 API (一些其他 WebView2) 异步的，如果代码必须按特定顺序运行，则应该使用回调。


<!-- ====================================================================== -->
## <a name="step-6---communication-between-host-and-web-content"></a>步骤 6 - 主机和 Web 内容之间的通信

主机和 Web 内容还可通过 方法相互 `postMessage` 通信。  WebView 中运行的 Web 内容可以通过 方法发布给主机，消息由主机上注册的任何 `window.chrome.webview.postMessage` `ICoreWebView2WebMessageReceivedEventHandler` 事件处理程序处理。  同样，主机可能通过 或 方法发送 Web 内容消息，由从侦听器添加的 `ICoreWebView2::PostWebMessageAsString` `ICoreWebView2::PostWebMessageAsJSON` 处理程序捕获 `window.chrome.webview.addEventListener` 。  通信机制允许 Web 内容通过传递消息要求主机运行本机 API 来使用本机功能。

作为了解该机制的示例，当您尝试在 WebView 中输出文档 URL 时，将执行以下步骤。

1.  主机注册处理程序以将收到的消息返回给 Web 内容
1.  主机将脚本注入 Web 内容，Web 内容注册处理程序以从主机打印消息
1.  主机向将 URL 张贴到主机的 Web 内容注入脚本
1.  将触发主机处理程序，并返回消息 (Web) URL
1.  将触发 Web 内容的处理程序，并输出来自主机的消息 (URL) 

复制以下代码段并粘贴到 `HelloWebView.cpp` 中。

```cpp
// Set an event handler for the host to return received message back to the web content
webviewWindow->add_WebMessageReceived(Callback<ICoreWebView2WebMessageReceivedEventHandler>(
    [](ICoreWebView2* webview, ICoreWebView2WebMessageReceivedEventArgs * args) -> HRESULT {
        PWSTR message;
        args->TryGetWebMessageAsString(&message);
        // processMessage(&message);
        webview->PostWebMessageAsString(message);
        CoTaskMemFree(message);
        return S_OK;
    }).Get(), &token);

// Schedule an async task to add initialization script that
// 1) Add an listener to print message from the host
// 2) Post document URL to the host
webviewWindow->AddScriptToExecuteOnDocumentCreated(
    L"window.chrome.webview.addEventListener(\'message\', event => alert(event.data));" \
    L"window.chrome.webview.postMessage(window.document.URL);",
nullptr);
```

### <a name="build-your-display-url-sample-app"></a>生成显示 URL 示例应用程序

若要生成并运行应用，请选择 `F5` 。  在导航到网页之前，URL 将显示在弹出窗口中。

:::image type="complex" source="../media/show-url.png" alt-text="显示 URL" lightbox="../media/show-url.png":::
   显示 URL
:::image-end:::

恭喜！你生成了第一个 WebView2 应用！


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

有关本文未涵盖的其他 WebView2 功能，请参阅以下资源。

*  [MicrosoftEdge/WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/GettingStartedGuides/Win32_GettingStarted) - 本教程中使用的代码。
*  [WebView2 开发的最佳做法](../concepts/developer-guide.md)
*  [WebView2 API 示例](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2APISample/README.md) - WebView2 功能的综合示例。
*  [WebView2Browser](https://github.com/MicrosoftEdge/WebView2Browser) - WebView2 示例应用。
*  [WebView2 API 参考](/microsoft-edge/webview2/reference/win32)
