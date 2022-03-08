---
title: 在 WebView2 应用中使用 Chrome DevTools 协议
description: 如何使用 Microsoft Edge WebView2 Chrome DevTools 协议包在 WebView2 应用中使用 Chrome NuGet协议。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
ms.openlocfilehash: 1188a83350c4a8a4d5af18ddfb143be0b22fb4a7
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432206"
---
# <a name="use-the-chrome-devtools-protocol-in-webview2-apps"></a>在 WebView2 应用中使用 Chrome DevTools 协议

Chrome [DevTools 协议](https://chromedevtools.github.io/devtools-protocol)提供用于检测、检查、调试和配置文件的 API Chromium基于浏览器。  Chrome DevTools 协议是开发工具Microsoft Edge的基础。  对 WebView2 平台中未实现的功能使用 Chrome DevTools 协议。

若要在 WebView2 应用中使用 Chrome DevTools 协议 API，请执行下列任一操作：

*  安装并使用 [Microsoft.Web.WebView2.DevToolsProtocolExtension (Preview) NuGet ](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension) 包 (.NET) 。

*  或者，运行以下方法之一：

   *  .NET： [CallDevToolsProtocolAsync](/dotnet/api/microsoft.web.webview2.core.corewebview2.calldevtoolsprotocolmethodasync?view=webview2-dotnet-1.0.774.44&preserve-view=true#Microsoft_Web_WebView2_Core_CoreWebView2_CallDevToolsProtocolMethodAsync_System_String_System_String_)、 [GetDevToolsProtocolEventReceiver](/dotnet/api/microsoft.web.webview2.core.corewebview2.getdevtoolsprotocoleventreceiver?view=webview2-dotnet-1.0.774.44&preserve-view=true)

   *  Win32 C/C++： [CallDevToolsProtocolMethod](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-1.0.774.44&preserve-view=true#calldevtoolsprotocolmethod)、 [ICoreWebView2DevToolsProtocolEventReceiver](/microsoft-edge/webview2/reference/win32/icorewebview2devtoolsprotocoleventreceiver?view=webview2-1.0.774.44&preserve-view=true)


<!-- ====================================================================== -->
## <a name="use-devtoolsprotocolhelper"></a>使用 DevToolsProtocolHelper

[Microsoft.Web.WebView2.DevToolsProtocolExtension (Preview) ](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension) 是 WebView2 团队创建的 NuGet 程序包，可轻松访问 Chrome DevTools 协议功能。  以下示例介绍如何在 WebView2 控件的 Chrome DevTools 协议中使用地理位置功能。  若要使用其他 Chrome DevTools 协议功能，你可以遵循类似的模式。

### <a name="dont-use-the-preview-package-in-production-apps"></a>不要在生产应用中使用预览包

[Microsoft.Web.WebView2.DevToolsProtocolExtension](https://www.nuget.org/packages/Microsoft.Web.WebView2.DevToolsProtocolExtension) NuGet目前处于技术预览阶段。  在预览版中，请勿在生产NuGet使用此程序包。


<!-- ====================================================================== -->
## <a name="step-1-create-a-webpage-to-find-your-geolocation"></a>步骤 1：创建网页以查找地理位置

若要创建 `HTML file` 以查找地理位置，请完成以下操作。

1. 打开Visual Studio Code (选择的任何 IDE 或 IDE) 。

1. `.html`创建新文件。

1. 将以下代码粘贴到新 `.html` 文件中：

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

1. `.html`使用文件名 保存文件`geolocation.html`。

1. 打开 Microsoft Edge。

1. 打开 `geolocation.html`。

1. 若要显示纬度和经度坐标，请单击"显示 **位置"** 按钮。  若要验证和比较地理位置，请将坐标复制并粘贴到 中 [https://www.bing.com/maps](https://www.bing.com/maps)。

   :::image type="content" source="./media/geolocater-browser.png" alt-text="在资源位置中显示用户的Microsoft Edge。" lightbox="./media/geolocater-browser.png":::


<!-- ====================================================================== -->
## <a name="step-2-display-geolocationhtml-in-a-webview2"></a>步骤 2：geolocation.html WebView2 中的视图

1. 若要创建 WebView2 应用，请使用入门指南或 WebView2 示例：

   * [WebView2 入门](../get-started/get-started.md)

   * [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)

1. 将 WebView2 控件的初始导航设置为 `geolocation.html`：

   ```csharp
   webView.CoreWebView2.Navigate(@"C:\{path\to\file}\geolocation.html");
   ```

1. 确保文件 `geolocation.html` 显示在 WebView2 控件应用中：

   :::image type="content" source="./media/initial-geolocate.png" alt-text="WebView2 geolocation.html应用程序中显示的列表文件。" lightbox="./media/initial-geolocate.png":::


<!-- ====================================================================== -->
## <a name="step-3-install-the-devtoolsprotocolhelper-nuget-package"></a>步骤 3：安装 DevToolsProtocolHelper NuGet包

使用 NuGet 下载 `Microsoft.Web.WebView2.DevToolsProtocolExtension`。

若要安装程序包，请运行以下设置：

1. 选择**Project** >  **Manage NuGet** **PackagesBrowse** > "。

1. 键入 `Microsoft.Web.WebView2.DevToolsProtocolExtension` ，然后选择 **"Microsoft.Web.WebView2.DevToolsProtocolExtensionInstall** > **"**。

1. 确保 **Microsoft.Web.WebView2.DevToolsProtocolExtension** 显示在Visual Studio NuGet 程序包管理器：

   :::image type="content" source="./media/cdp-nuget.png" alt-text="确保 Microsoft.Web.WebView2.DevToolsProtocolExtension 显示在Visual Studio NuGet 程序包管理器。" lightbox="./media/cdp-nuget.png":::


<!-- ====================================================================== -->
## <a name="step-4-use-devtools-protocol-helper"></a>步骤 4：使用 DevTools 协议帮助程序

1. 将命名空间 `DevToolsProtocolExtension` 添加到你的项目：

   ```csharp
   using Microsoft.Web.WebView2.Core;
   using Microsoft.Web.WebView2.Core.DevToolsProtocolExtension;
   ```

1. 实例化对象 `DevToolsProtocolHelper` 并导航到 `geolocation.html`：

   ```csharp
   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
      DevToolsProtocolHelper helper = webView.CoreWebView2.GetDevToolsProtocolHelper();

      webView.CoreWebView2.Navigate(@"C:\{path\to\file}\geolocation.html");
   }
   ```

1. 运行 [setGeoLocationOverrideAsync](https://chromedevtools.github.io/devtools-protocol/tot/Emulation/#method-setGeolocationOverride) 方法：

   ```csharp
   async void InitializeAsync()
   {
      await webView.EnsureCoreWebView2Async(null);
      DevToolsProtocolHelper helper = webview.CoreWebView2.GetDevToolsProtocolHelper();

      // Latitude and longitude for Paris, France.
      double latitude = 48.857024082572565;
      double longitude = 2.3161581601457386;
      double accuracy = 1;
      await helper.Emulation.setGeolocationOverrideAsync(latitude, longitude, accuracy);
   }
   ```

   有关详细信息，请参阅 [setGeolocationOverride](https://chromedevtools.github.io/devtools-protocol/tot/Emulation/#method-setGeolocationOverride)。

1. 运行应用。

1. 若要显示法国巴黎的坐标，请单击" **显示位置"** 按钮：

   :::image type="content" source="./media/final-location-cdp.png" alt-text="在 WebView2 .html显示坐标为 Paris 的 WebView2 文件。" lightbox="./media/final-location-cdp.png":::


<!-- ====================================================================== -->
## <a name="file-a-bug-or-feature-request-for-the-chrome-devtools-protocol"></a>提出 Chrome DevTools 协议的 Bug 或功能请求

若要请求 WebView2 平台功能，请在 [WebView2Feedback 存储库输入新问题](https://github.com/MicrosoftEdge/WebView2Feedback)。

若要提交有关 Chrome DevTools 协议的 bug，在错误数据库中Chromium [Bug 报告](https://bugs.chromium.org/p/chromium/issues/entry?components=Platform%3EDevTools%3EPlatform)。

Chrome DevTools 协议由开源开发人员项目Chromium，而不是由 Microsoft Edge WebView2 团队维护。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [Microsoft Edge DevTools 协议概述](../../devtools-protocol-chromium/index.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)
