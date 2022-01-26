---
title: 在 WebView2 中使用 Chrome DevTools 协议
description: 如何使用 Microsoft Edge WebView2 Chrome DevTools 协议包在 WebView2 应用中使用 Chrome NuGet协议。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
ms.openlocfilehash: c03a2465932915ac66751efd4891915115b22757
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12324340"
---
# <a name="use-the-chrome-devtools-protocol-in-webview2"></a>在 WebView2 中使用 Chrome DevTools 协议

[Chrome DevTools 协议](https://chromedevtools.github.io/devtools-protocol)提供用于检测、检查、调试和配置文件Chromium浏览器的 API。  Chrome DevTools 协议是开发工具Microsoft Edge的基础。  对 WebView2 平台中未实现的功能使用 Chrome DevTools 协议。

若要在 WebView2 应用中使用 Chrome DevTools 协议 API，请执行下列任一操作：

*   安装并使用[Microsoft.Web.WebView2.DevToolsProtocolExtension (Preview) NuGet](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension)包 (.NET) 。
*   运行下列方法之一。
    *   [.NET：CallDevToolsProtocolAsync](/dotnet/api/microsoft.web.webview2.core.corewebview2.calldevtoolsprotocolmethodasync?view=webview2-dotnet-1.0.774.44&preserve-view=true#Microsoft_Web_WebView2_Core_CoreWebView2_CallDevToolsProtocolMethodAsync_System_String_System_String_) [、GetDevToolsProtocolEventReceiver](/dotnet/api/microsoft.web.webview2.core.corewebview2.getdevtoolsprotocoleventreceiver?view=webview2-dotnet-1.0.774.44&preserve-view=true)
    *   Win32  [C/C++：CallDevToolsProtocolMethod](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-1.0.774.44&preserve-view=true#calldevtoolsprotocolmethod) [、ICoreWebView2DevToolsProtocolEventReceiver](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-1.0.774.44&preserve-view=true)


<!-- ====================================================================== -->
## <a name="use-devtoolsprotocolhelper"></a>使用 DevToolsProtocolHelper

> [!NOTE]
> [Microsoft.Web.WebView2.DevToolsProtocolExtension](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension) NuGet目前处于技术预览阶段。  在预览版中，请勿在生产应用中使用程序包。

[Microsoft.Web.WebView2.DevToolsProtocolExtension (Preview) ](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension)是 WebView2 团队创建的 NuGet 程序包，可轻松访问 Chrome DevTools 协议功能。  以下示例介绍如何在 WebView2 控件的 Chrome DevTools 协议中使用地理位置功能。  你可以遵循类似的模式来使用其他 Chrome DevTools 协议功能。


<!-- ====================================================================== -->
## <a name="step-1-create-a-webpage-to-find-your-geolocation"></a>步骤 1：创建网页以查找地理位置

若要创建 `HTML file` 以查找地理位置，请完成以下操作。

1.  打开Visual Studio Code (选择的任何 IDE 或 IDE) 。
1.  创建新 `.html` 文件。
1.  将以下代码段复制并粘贴到新 `.html` 文件中。

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <title>Geolocation Finder</title>
    </head>
    <body>
        <button id="display">Display Location</button>
        <div id="message"></div>
    </body>

    <script>
        const btn = document.getElementById('display');
        // Find the user location.
        btn.addEventListener('click', function () {
            navigator.geolocation.getCurrentPosition(onSuccess, onError);
        });

        // Update message to display the latitude and longitude coordinates.
        function onSuccess(position) {
            const {latitude, longitude} = position.coords;
            message.textContent = `Your location: (${latitude},${longitude})`;
        }

        function onError() {
            message.textContent = `Operation Failed`;
        }
    </script>
    </html>
    ```

1.  使用 `.html` 文件名 保存文件 `geolocation.html` 。
1.  打开 Microsoft Edge。
1.  打开 `geolocation.html` 文件。
1.  若要显示纬度和经度坐标，请选择"显示 **位置"** 按钮。  若要验证和比较地理位置，请将坐标复制并粘贴到 中 [https://www.bing.com/maps](https://www.bing.com/maps) 。

    :::image type="complex" source="./media/geolocater-browser.png" alt-text="在用户位置中显示用户的地理位置Microsoft Edge。" lightbox="./media/geolocater-browser.png":::
       在用户位置中显示用户的地理位置Microsoft Edge
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-2-display-geolocationhtml-in-a-webview2"></a>步骤 2：geolocation.html WebView2 中的视图

1.  若要创建 WebView2 应用，请使用入门指南或 WebView2 示例。
    *   [入门](../index.md#get-started)
    *   [WebView2 示例](https://github.com/MicrosoftEdge/WebView2Samples)

1.  将 WebView2 控件的初始导航设置为 `geolocation.html` 。

    ```csharp
    webView.CoreWebView2.Navigate(@"C:\{path\to\file}\geolocation.html");
    ```

1.  确保 `geolocation.html` 文件显示在 WebView2 控件应用中。

    :::image type="complex" source="./media/initial-geolocate.png" alt-text="在 WebView2 geolocater.html显示文件。" lightbox="./media/initial-geolocate.png":::
       在 `geolocation.html` WebView2 控件应用中显示文件
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-3-install-the-devtoolsprotocolhelper-nuget-package"></a>步骤 3：安装 DevToolsProtocolHelper NuGet包

使用 NuGet 下载 `Microsoft.Web.WebView2.DevToolsProtocolExtension` 。  若要安装程序包，请完成以下操作。

1.  选择**Project**  >  **管理NuGet程序包**  >  **浏览"。**
1.  键入 `Microsoft.Web.WebView2.DevToolsProtocolExtension` 并选择 **"Microsoft.Web.WebView2.DevToolsProtocolExtension**  >  **安装"。**

:::image type="complex" source="./media/cdp-nuget.png" alt-text="确保 Microsoft.Web.WebView2.DevToolsProtocolExtension 显示在Visual Studio NuGet 程序包管理器。" lightbox="./media/cdp-nuget.png":::
   确保**Microsoft.Web.WebView2.DevToolsProtocolExtension**显示在Visual Studio NuGet 程序包管理器
:::image-end:::


<!-- ====================================================================== -->
## <a name="step-4-use-devtools-protocol-helper"></a>步骤 4：使用 DevTools 协议帮助程序

1.  将 `DevToolsProtocolExtension` 命名空间添加到项目中。

    ```csharp
    using Microsoft.Web.WebView2.Core;
    using Microsoft.Web.WebView2.Core.DevToolsProtocolExtension;
    ```

1.  实例化 `DevToolsProtocolHelper` 对象并导航到 `geolocation.html` 。

    ```csharp
    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
        DevToolsProtocolHelper helper = webView.CoreWebView2.GetDevToolsProtocolHelper();

        webView.CoreWebView2.Navigate(@"C:\{path\to\file}\geolocation.html");
    }
    ```

1.  运行 [setGeoLocationOverrideAsync](https://chromedevtools.github.io/devtools-protocol/tot/Emulation/#method-setGeolocationOverride) 方法。  有关详细信息，请导航到 [setGeolocationOverride](https://chromedevtools.github.io/devtools-protocol/tot/Emulation/#method-setGeolocationOverride)。

    ```csharp
    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
        DevToolsProtocolHelper helper = webview.CoreWebView2.GetDevToolsProtocolHelper();

        webView.CoreWebView2.Navigate(@"C:\{path\to\file}\geolocation.html");

        // Latitude and longitude for Paris, France.
        double latitude = 48.857024082572565;
        double longitude = 2.3161581601457386;
        double accuracy = 1;
        await helper.Emulation.setGeolocationOverrideAsync(latitude, longitude, accuracy);

    }
    ```

1.  运行应用。
1.  若要显示法国巴黎的坐标，请选择" **显示位置"** 按钮。

    :::image type="complex" source="./media/final-location-cdp.png" alt-text="在 WebView2 .html显示坐标为 Paris 的 WebView2 文件。" lightbox="./media/final-location-cdp.png":::
       在 `.html` WebView2 控件中显示文件以及巴黎的坐标
    :::image-end:::


<!-- ====================================================================== -->
## <a name="file-a-bug-or-feature-request-for-the-chrome-devtools-protocol"></a>提出 Chrome DevTools 协议的 Bug 或功能请求

若要请求 WebView2 平台功能，请在 [WebView2Feedback](https://github.com/MicrosoftEdge/WebView2Feedback)存储库输入新问题。

若要提交有关 Chrome DevTools 协议的 bug，请提交错误报告Chromium [Bug 数据库](https://bugs.chromium.org/p/chromium/issues/entry?components=Platform%3EDevTools%3EPlatform)。

Chrome DevTools 协议由开放源代码Chromium维护，而不是由 Microsoft Edge WebView2 团队维护。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [Microsoft Edge DevTools 协议概述](../../devtools-protocol-chromium/index.md)
*  [WebView2 示例](https://github.com/MicrosoftEdge/WebView2Samples)
