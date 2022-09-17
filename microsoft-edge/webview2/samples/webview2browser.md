---
title: Win32 示例 WebView2Browser
description: 使用 Microsoft Edge WebView2 控件生成的 Web 浏览器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 07/18/2022
ms.openlocfilehash: 8da583bdc848ae08a36ef3da9a1a5741957393ba
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754862"
---
# <a name="win32-sample-webview2browser"></a>Win32 示例 WebView2Browser

<!-- copied from:
https://github.com/MicrosoftEdge/WebView2Browser#readme
aka
https://github.com/MicrosoftEdge/WebView2Browser/blob/main/README.md
-->

此示例 **WebView2Browser** 是使用 [Microsoft Edge WebView2](https://aka.ms/webview2) 控件生成的 Web 浏览器。

此示例有自己的专用存储库。

*  示例名称： **WebView2Browser**
*  存储库： [WebView2Browser](https://github.com/MicrosoftEdge/WebView2Browser)
*  解决方案文件： **WebViewBrowserApp.sln**

![WebView2Browser 示例应用](./webview2browser-images/WebView2Browser.png)
<!-- todo: remove png from other repo, in PR 140: -->
<!-- ![WebView2Browser](https://raw.githubusercontent.com/MicrosoftEdge/WebView2Browser/master/screenshots/WebView2Browser.png) -->

<!-- delta: swapped end of sentence: -->
**WebView2Browser** 是一个演示 WebView2 控件功能的 Windows 桌面应用程序示例。  <!-- delta: added sentence: -->**WebView2Browser** 示例应用使用多个 WebView2 实例。

此示例是作为 Win32 [Visual Studio 2019](https://visualstudio.microsoft.com/vs/) 项目生成的。  它在 WebView2 环境中使用 C++ 和 JavaScript。

**WebView2Browser** 显示 WebView2 的一些最简单用途，例如创建和导航 WebView，但也显示一些更复杂的工作流，例如使用 [PostWebMessageAsJson API](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasjson) 在单独的环境中跨 WebView2 控件进行通信。  这是一个丰富的代码示例，用于演示如何使用 WebView2 API 生成自己的应用。


<!-- ====================================================================== -->
## <a name="step-1-install-a-preview-channel-of-microsoft-edge"></a>步骤 1：安装 Microsoft Edge 的预览频道

*  如果尚未安装，请在支持的 OS 上安装 [Microsoft Edge 的预览通道](https://www.microsoftedgeinsider.com/download/) 。


<!-- ====================================================================== -->
## <a name="step-2-install-visual-studio"></a>步骤 2：安装 Visual Studio

1. 安装 [Visual Studio](https://visualstudio.microsoft.com/vs/)，包括 C++ 支持。

建议安装 [WebView2 运行时](https://developer.microsoft.com/microsoft-edge/webview2/) 。<!-- TODO: give actionable steps/instructions.  Why preview channel and also Runtime? -->  最低版本为 86.0.622.38。


<!-- ====================================================================== -->
## <a name="step-3-clone-the-webview2samples-repo"></a>步骤 3：克隆 WebView2Samples 存储库

* 克隆 (或下载为 `.zip` **webView2Samples** 存储库) 。  请参阅在_为 WebView2 设置开发人员环境_时[克隆 WebView2Samples 存储库](../how-to/machine-setup.md#clone-the-webview2samples-repo)。


<!-- ====================================================================== -->
## <a name="step-4-open-the-solution-in-visual-studio"></a>步骤 4：在 Visual Studio 中打开解决方案

1. 在 Visual Studio 2019 中打开解决方案。  WebView2 SDK 已作为 NuGet 包包含在项目中。  如果要使用 Visual Studio 2017，请在常规 > 平台工具集>项目 **属性>配置属性中更改项目的平台工具集**。  可能还需要将 Windows SDK 更改为最新版本。

1. 如果使用的是下面的 Windows 版本，请进行下面列出的更改Windows 10。

#### <a name="using-versions-below-windows-10"></a>使用以下版本Windows 10

如果要在Windows 10之前在 Windows 版本中生成和运行浏览器，请进行以下更改。  这是必需的，因为 DPI 在 Windows 10 和以前版本的 Windows 中处理的方式。

1. 若要在 Windows 版本中生成并运行浏览器，请先Windows 10：在`WebViewBrowserApp.cpp`其中，更改`SetProcessDpiAwarenessContext`为`SetProcessDPIAware`：

```cpp
int APIENTRY wWinMain(_In_ HINSTANCE hInstance,
                      _In_opt_ HINSTANCE hPrevInstance,
                      _In_ LPWSTR    lpCmdLine,
                      _In_ int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    // Call SetProcessDPIAware() instead when using Windows 7 or any version
    // below 1703 (Windows 10).
    SetProcessDpiAwarenessContext(DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2);

    BrowserWindow::RegisterClass(hInstance);

    // ...
```

1. 如果要在 Windows 版本中生成并运行浏览器，请在Windows 10之前：在以下调用`GetDpiForWindow`中`BrowserWindow.cpp`删除或注释：

```cpp
int BrowserWindow::GetDPIAwareBound(int bound)
{
    // Remove the GetDpiForWindow call when using Windows 7 or any version
    // below 1607 (Windows 10). You will also have to make sure the build
    // directory is clean before building again.
    return (bound * GetDpiForWindow(m_hWnd) / DEFAULT_DPI);
}
```


<!-- ====================================================================== -->
## <a name="step-5-build-and-run-the-app"></a>步骤 5：生成并运行应用

1. 设置要生成 (（例如调试或发布）的目标，目标为 x86 或 x64) 。

1. 生成解决方案。

1. ) 应用运行 (或调试。

1. 关闭应用。


<!-- ====================================================================== -->
## <a name="step-6-update-the-webview2-sdk"></a>步骤 6：更新 WebView2 SDK

* 在 Visual Studio 中更新 WebView2 SDK 的版本。  为此，请右键单击项目，然后单击 **“管理 NuGet 包**”。


<!-- ====================================================================== -->
## <a name="step-7-build-and-run-the-app-with-updated-webview2-sdk"></a>步骤 7：使用更新的 WebView2 SDK 生成并运行应用

* 再次生成并运行应用。


<!-- ====================================================================== -->
## <a name="browser-layout"></a>浏览器布局

<!-- added sentence: -->
WebView2Browser 示例应用使用多个 WebView2 实例。

WebView2Browser 具有多 WebView 方法，可将 Web 内容和应用程序 UI 集成到 Windows 桌面应用程序中。 这样，浏览器就可以使用标准 Web 技术 (HTML、CSS、JavaScript) 来点亮接口，但也使应用能够从 Web 中提取代码，并使用 IndexedDB 来存储收藏夹和历史记录。

多 WebView 方法涉及使用两个单独的 WebView 环境 (每个环境都有其自己的用户数据目录) ：一个用于 UI WebView，另一个用于所有内容 WebView。 UI WebViews (控件和选项下拉列表) 使用 UI 环境，而 Web 内容 WebView (每个选项卡) 使用内容环境。

![浏览器布局](./webview2browser-images/layout.png)
<!-- todo: remove png from other repo, in PR 140: 
![Browser layout](https://raw.githubusercontent.com/MicrosoftEdge/WebView2Browser/master/screenshots/layout.png)
-->


<!-- ====================================================================== -->
## <a name="features"></a>功能

**WebView2Browser** 示例提供用于创建基本 Web 浏览器的所有功能，但有足够的空间供你玩。

**WebView2Browser** 示例实现以下功能：
* 返回/forward
* “重新加载”页
* 取消导航
* 多个选项卡
* 历史记录
* 收藏夹
* 从地址栏搜索
* 页面安全状态
* 清除缓存和 Cookie


<!-- ====================================================================== -->
## <a name="webview2-apis"></a>WebView2 API

WebView2Browser 使用 WebView2 中提供的少数 API。 对于此处未使用的 API，可以在 [Microsoft Edge WebView2 参考](/microsoft-edge/webview2/reference/win32)中找到有关这些 API 的详细信息。 以下是最有趣的 API WebView2Browser 使用的列表及其启用的功能。

API | 功能
:--- | :---
`CreateCoreWebView2EnvironmentWithOptions` | 用于为 UI 和内容 WebView 创建环境。 传递不同的用户数据目录以将 UI 与 Web 内容隔离开来。 |
`ICoreWebView2` | WebView2Browser 中有多个 WebView，大多数功能都利用此接口中的成员，下表显示了其使用方式。
`ICoreWebView2DevToolsProtocolEventReceivedEventHandler` | 与add_DevToolsProtocolEventReceived一起用于侦听 CDP 安全事件以更新浏览器 UI 中的锁图标。 |
`ICoreWebView2DevToolsProtocolEventReceiver` | 与add_DevToolsProtocolEventReceived一起用于侦听 CDP 安全事件以更新浏览器 UI 中的锁图标。 |
`ICoreWebView2ExecuteScriptCompletedHandler` | 与 ExecuteScript 一起使用，用于从访问页面获取标题和 favicon。 |
`ICoreWebView2FocusChangedEventHandler` | 与add_LostFocus一起用于在失去焦点时隐藏浏览器选项下拉列表。
`ICoreWebView2HistoryChangedEventHandler` | 与add_HistoryChanged一起用于更新浏览器 UI 中的导航按钮。 |
`ICoreWebView2Controller` | WebView2Browser 中有多个 WebViewController，我们从中提取关联的 WebView。
`ICoreWebView2NavigationCompletedEventHandler` | 与add_NavigationCompleted一起用于更新浏览器 UI 中的重载按钮。
`ICoreWebView2Settings` | 用于在浏览器 UI 中禁用 DevTools。
`ICoreWebView2SourceChangedEventHandler` | 与add_SourceChanged一起用于更新浏览器 UI 中的地址栏。 |
`ICoreWebView2WebMessageReceivedEventHandler` | 这是 WebView2Browser 最重要的 API 之一。 涉及跨 WebView 通信的大多数功能都使用此功能。

ICoreWebView2 API | 功能
:--- | :---
`add_NavigationStarting` | 用于在控件 WebView 中显示取消导航按钮。
`add_SourceChanged` | 用于更新地址栏。
`add_HistoryChanged` | 用于更新后退/前进按钮。
`add_NavigationCompleted` | 用于在导航完成后显示重载按钮。
`ExecuteScript` | 用于获取访问页面的标题和 favicon。
`PostWebMessageAsJson` | 用于通信 WebViews。 所有消息都使用 JSON 传递所需的参数。
`add_WebMessageReceived` | 用于处理发布到 WebView 的 Web 消息。
`CallDevToolsProtocolMethod` | 用于启用侦听安全事件，这会通知文档中的安全状态更改。

ICoreWebView2Controller API | 功能 (的) 
:--- | :---
`get_CoreWebView2` | 用于获取与此 CoreWebView2Controller 关联的 CoreWebView2。
`add_LostFocus` | 用于在用户单击此选项时隐藏选项下拉列表。


<!-- ====================================================================== -->
## <a name="implementing-the-features"></a>实现功能

以下部分介绍如何实现 WebView2Browser 中的某些功能。 可以查看源代码，了解有关此处一切工作原理的更多详细信息。

**内容：**

* [基础知识](#the-basics)
  * [设置环境，创建 WebView](#set-up-the-environment-create-a-webview)
  * [导航到网页](#navigate-to-web-page)
  * [更新地址栏](#updating-the-address-bar)
  * [回去，往前走](#going-back-going-forward)
* [一些有趣的功能](#some-interesting-features)
  * [传达 WebViews](#communicating-the-webviews)
  * [选项卡处理](#tab-handling)
  * [更新安全图标](#updating-the-security-icon)
  * [填充历史记录](#populating-the-history)
* [处理 JSON 和 URI](#handling-json-and-uris)


<!-- ====================================================================== -->
## <a name="the-basics"></a>基础知识

### <a name="set-up-the-environment-create-a-webview"></a>设置环境，创建 WebView

WebView2 允许你在 Windows 应用中托管 Web 内容。 它公开 Globals [CreateCoreWebView2Environment](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environment) 和 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions) ，我们可以从中为浏览器的 UI 和内容创建两个单独的环境。

```cpp
    // Get directory for user data. This will be kept separated from the
    // directory for the browser UI data.
    std::wstring userDataDirectory = GetAppDataDirectory();
    userDataDirectory.append(L"\\User Data");

    // Create WebView environment for web content requested by the user. All
    // tabs will be created from this environment and kept isolated from the
    // browser UI. This environment is created first so the UI can request new
    // tabs when it's ready.
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(nullptr, userDataDirectory.c_str(),
        L"", Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            [this](HRESULT result, ICoreWebView2Environment* env) -> HRESULT
    {
        RETURN_IF_FAILED(result);

        m_contentEnv = env;
        HRESULT hr = InitUIWebViews();

        if (!SUCCEEDED(hr))
        {
            OutputDebugString(L"UI WebViews environment creation failed\n");
        }

        return hr;
    }).Get());
```

```cpp
HRESULT BrowserWindow::InitUIWebViews()
{
    // Get data directory for browser UI data
    std::wstring browserDataDirectory = GetAppDataDirectory();
    browserDataDirectory.append(L"\\Browser Data");

    // Create WebView environment for browser UI. A separate data directory is
    // used to isolate the browser UI from web content requested by the user.
    return CreateCoreWebView2EnvironmentWithOptions(nullptr, browserDataDirectory.c_str(),
        L"", Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            [this](HRESULT result, ICoreWebView2Environment* env) -> HRESULT
    {
        // Environment is ready, create the WebView
        m_uiEnv = env;

        RETURN_IF_FAILED(CreateBrowserControlsWebView());
        RETURN_IF_FAILED(CreateBrowserOptionsWebView());

        return S_OK;
    }).Get());
}
```

环境准备就绪后，我们将使用 [ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler](/microsoft-edge/webview2/reference/win32/icorewebview2createcorewebview2environmentcompletedhandler) 创建 UI WebView。

```cpp
HRESULT BrowserWindow::CreateBrowserControlsWebView()
{
    return m_uiEnv->CreateCoreWebView2Controller(m_hWnd, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
        [this](HRESULT result, ICoreWebView2Controller* controller) -> HRESULT
    {
        if (!SUCCEEDED(result))
        {
            OutputDebugString(L"Controls WebView creation failed\n");
            return result;
        }
        // WebView created
        m_controlsController = controller;
        CheckFailure(m_controlsController->get_CoreWebView2(&m_controlsWebView), L"");

        wil::com_ptr<ICoreWebView2Settings> settings;
        RETURN_IF_FAILED(m_controlsWebView->get_Settings(&settings));
        RETURN_IF_FAILED(settings->put_AreDevToolsEnabled(FALSE));

        RETURN_IF_FAILED(m_controlsController->add_ZoomFactorChanged(Callback<ICoreWebView2ZoomFactorChangedEventHandler>(
            [](ICoreWebView2Controller* controller, IUnknown* args) -> HRESULT
        {
            controller->put_ZoomFactor(1.0);
            return S_OK;
        }
        ).Get(), &m_controlsZoomToken));

        RETURN_IF_FAILED(m_controlsWebView->add_WebMessageReceived(m_uiMessageBroker.Get(), &m_controlsUIMessageBrokerToken));
        RETURN_IF_FAILED(ResizeUIWebViews());

        std::wstring controlsPath = GetFullPathFor(L"wvbrowser_ui\\controls_ui\\default.html");
        RETURN_IF_FAILED(m_controlsWebView->Navigate(controlsPath.c_str()));

        return S_OK;
    }).Get());
}
```

我们在这里设置一些内容。 [ICoreWebView2Settings](/microsoft-edge/webview2/reference/win32/icorewebview2settings) 接口用于在为浏览器控件提供电源的 WebView 中禁用 DevTools。 我们还在为收到的 Web 消息添加处理程序。 当用户与此 WebView 中的控件交互时，此处理程序将使我们能够执行一些操作。


#### <a name="navigate-to-web-page"></a>导航到网页

可以通过在地址栏中输入其 URI 来导航到网页。 按 Enter 时，控件 WebView 会将 Web 消息发布到主机应用，以便它可以将活动选项卡导航到指定位置。 下面的代码显示主机 Win32 应用程序如何处理该消息。

```cpp
        case MG_NAVIGATE:
        {
            std::wstring uri(args.at(L"uri").as_string());
            std::wstring browserScheme(L"browser://");

            if (uri.substr(0, browserScheme.size()).compare(browserScheme) == 0)
            {
                // No encoded search URI
                std::wstring path = uri.substr(browserScheme.size());
                if (path.compare(L"favorites") == 0 ||
                    path.compare(L"settings") == 0 ||
                    path.compare(L"history") == 0)
                {
                    std::wstring filePath(L"wvbrowser_ui\\content_ui\\");
                    filePath.append(path);
                    filePath.append(L".html");
                    std::wstring fullPath = GetFullPathFor(filePath.c_str());
                    CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->Navigate(fullPath.c_str()), L"Can't navigate to browser page.");
                }
                else
                {
                    OutputDebugString(L"Requested unknown browser page\n");
                }
            }
            else if (!SUCCEEDED(m_tabs.at(m_activeTabId)->m_contentWebView->Navigate(uri.c_str())))
            {
                CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->Navigate(args.at(L"encodedSearchURI").as_string().c_str()), L"Can't navigate to requested page.");
            }
        }
        break;
```

WebView2Browser 将针对浏览器页面检查 URI (即收藏夹、设置、历史记录) 并导航到请求的位置或使用提供的 URI 将必应搜索为回退。


#### <a name="updating-the-address-bar"></a>更新地址栏

每次在活动选项卡的文档源中发生更改时，以及切换选项卡时的其他控件都会更新地址栏。 文档状态更改时，每个 WebView 都会触发一个事件，我们可以使用此事件获取更新的新源，并将更改转发到控件 WebView (我们还将更新返回并继续按钮) 。

```cpp
        // Register event handler for doc state change
        RETURN_IF_FAILED(m_contentWebView->add_SourceChanged(Callback<ICoreWebView2SourceChangedEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, ICoreWebView2SourceChangedEventArgs* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabURIUpdate(m_tabId, webview), L"Can't update address bar");

            return S_OK;
        }).Get(), &m_uriUpdateForwarderToken));
```

```cpp
HRESULT BrowserWindow::HandleTabURIUpdate(size_t tabId, ICoreWebView2* webview)
{
    wil::unique_cotaskmem_string source;
    RETURN_IF_FAILED(webview->get_Source(&source));

    web::json::value jsonObj = web::json::value::parse(L"{}");
    jsonObj[L"message"] = web::json::value(MG_UPDATE_URI);
    jsonObj[L"args"] = web::json::value::parse(L"{}");
    jsonObj[L"args"][L"tabId"] = web::json::value::number(tabId);
    jsonObj[L"args"][L"uri"] = web::json::value(source.get());

    // ...

    RETURN_IF_FAILED(PostJsonToWebView(jsonObj, m_controlsWebView.Get()));

    return S_OK;
}

HRESULT BrowserWindow::HandleTabHistoryUpdate(size_t tabId, ICoreWebView2* webview)
{
    // ...

    BOOL canGoForward = FALSE;
    RETURN_IF_FAILED(webview->get_CanGoForward(&canGoForward));
    jsonObj[L"args"][L"canGoForward"] = web::json::value::boolean(canGoForward);

    BOOL canGoBack = FALSE;
    RETURN_IF_FAILED(webview->get_CanGoBack(&canGoBack));
    jsonObj[L"args"][L"canGoBack"] = web::json::value::boolean(canGoBack);

    RETURN_IF_FAILED(PostJsonToWebView(jsonObj, m_controlsWebView.Get()));

    return S_OK;
}
```

我们已将 `MG_UPDATE_URI` 消息和 URI 一起发送到控件 WebView。 现在，我们希望在选项卡状态上反映这些更改，并在必要时更新 UI。

```javascript
        case commands.MG_UPDATE_URI:
            if (isValidTabId(args.tabId)) {
                const tab = tabs.get(args.tabId);
                let previousURI = tab.uri;

                // Update the tab state
                tab.uri = args.uri;
                tab.uriToShow = args.uriToShow;
                tab.canGoBack = args.canGoBack;
                tab.canGoForward = args.canGoForward;

                // If the tab is active, update the controls UI
                if (args.tabId == activeTabId) {
                    updateNavigationUI(message);
                }

                // ...
            }
            break;
```


#### <a name="going-back-going-forward"></a>回去，往前走

每个 WebView 都会保留它所执行的导航的历史记录，因此我们只需要将浏览器 UI 与相应的方法连接。 如果可以向后/向前导航活动选项卡的 WebView，则按钮会在单击时将 Web 消息发布到主机应用程序。

JavaScript 端：

```javascript
    document.querySelector('#btn-forward').addEventListener('click', function(e) {
        if (document.getElementById('btn-forward').className === 'btn') {
            var message = {
                message: commands.MG_GO_FORWARD,
                args: {}
            };
            window.chrome.webview.postMessage(message);
        }
    });

    document.querySelector('#btn-back').addEventListener('click', function(e) {
        if (document.getElementById('btn-back').className === 'btn') {
            var message = {
                message: commands.MG_GO_BACK,
                args: {}
            };
            window.chrome.webview.postMessage(message);
        }
    });
```

主机应用程序端：

```cpp
        case MG_GO_FORWARD:
        {
            CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->GoForward(), L"");
        }
        break;
        case MG_GO_BACK:
        {
            CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->GoBack(), L"");
        }
        break;
```


#### <a name="reloading-stop-navigation"></a>重新加载、停止导航

我们使用 `NavigationStarting` 内容 WebView 触发的事件来更新其在控件 WebView 中关联的选项卡加载状态。 同样，当 WebView 触发 `NavigationCompleted` 事件时，我们将使用该事件指示控件 WebView 更新选项卡状态。 控件 WebView 中的活动选项卡状态将决定是显示重载还是取消按钮。 其中每个选项卡都会在单击时将消息发布回主机应用程序，以便可以相应地重新加载该选项卡的 WebView 或取消其导航。

```javascript
function reloadActiveTabContent() {
    var message = {
        message: commands.MG_RELOAD,
        args: {}
    };
    window.chrome.webview.postMessage(message);
}

 // ...

    document.querySelector('#btn-reload').addEventListener('click', function(e) {
        var btnReload = document.getElementById('btn-reload');
        if (btnReload.className === 'btn-cancel') {
            var message = {
                message: commands.MG_CANCEL,
                args: {}
            };
            window.chrome.webview.postMessage(message);
        } else if (btnReload.className === 'btn') {
            reloadActiveTabContent();
        }
    });
```

```cpp
        case MG_RELOAD:
        {
            CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->Reload(), L"");
        }
        break;
        case MG_CANCEL:
        {
            CheckFailure(m_tabs.at(m_activeTabId)->m_contentWebView->CallDevToolsProtocolMethod(L"Page.stopLoading", L"{}", nullptr), L"");
        }
```


<!-- ====================================================================== -->
## <a name="some-interesting-features"></a>一些有趣的功能


#### <a name="communicating-the-webviews"></a>传达 WebViews

我们需要传达为选项卡和 UI 提供电源的 WebView，以便一个选项卡的 WebView 中的用户交互在另一个 WebView 中具有所需的效果。  WebView2Browser 为此使用一组非常有用的 WebView2 API，包括 [PostWebMessageAsJson](/microsoft-edge/webview2/reference/win32/icorewebview2#postwebmessageasjson)、 [add_WebMessageReceived](/microsoft-edge/webview2/reference/win32/icorewebview2#add_webmessagereceived) 和 [ICoreWebView2WebMessageReceivedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventhandler)。

在 JavaScript 端，我们将使用公开的 `window.chrome.webview` 对象来调用 `postMessage` 该方法，并为接收的消息添加事件列表。

```cpp
HRESULT BrowserWindow::CreateBrowserControlsWebView()
{
    return m_uiEnv->CreateCoreWebView2Controller(m_hWnd, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
        [this](HRESULT result, ICoreWebView2Controller* controller) -> HRESULT
    {
        // ...

        RETURN_IF_FAILED(m_controlsWebView->add_WebMessageReceived(m_uiMessageBroker.Get(), &m_controlsUIMessageBrokerToken));

        // ...

        return S_OK;
    }).Get());
}
```

```cpp
HRESULT BrowserWindow::PostJsonToWebView(web::json::value jsonObj, ICoreWebView2* webview)
{
    utility::stringstream_t stream;
    jsonObj.serialize(stream);

    return webview->PostWebMessageAsJson(stream.str().c_str());
}

// ...

HRESULT BrowserWindow::HandleTabNavStarting(size_t tabId, ICoreWebView2* webview)
{
    web::json::value jsonObj = web::json::value::parse(L"{}");
    jsonObj[L"message"] = web::json::value(MG_NAV_STARTING);
    jsonObj[L"args"] = web::json::value::parse(L"{}");
    jsonObj[L"args"][L"tabId"] = web::json::value::number(tabId);

    return PostJsonToWebView(jsonObj, m_controlsWebView.Get());
}
```

```javascript
function init() {
    window.chrome.webview.addEventListener('message', messageHandler);
    refreshControls();
    refreshTabs();

    createNewTab(true);
}

// ...

function reloadActiveTabContent() {
    var message = {
        message: commands.MG_RELOAD,
        args: {}
    };
    window.chrome.webview.postMessage(message);
}
```

#### <a name="tab-handling"></a>选项卡处理

每当用户单击打开的选项卡右侧 **的新选项卡** 按钮时，都会创建一个新选项卡。 控件的 WebView 将向主机应用程序发布一条消息，为该选项卡创建 WebView，并创建跟踪其状态的对象。

```javascript
function createNewTab(shouldBeActive) {
    const tabId = getNewTabId();

    var message = {
        message: commands.MG_CREATE_TAB,
        args: {
            tabId: parseInt(tabId),
            active: shouldBeActive || false
        }
    };

    window.chrome.webview.postMessage(message);

    tabs.set(parseInt(tabId), {
        title: 'New Tab',
        uri: '',
        uriToShow: '',
        favicon: 'img/favicon.png',
        isFavorite: false,
        isLoading: false,
        canGoBack: false,
        canGoForward: false,
        securityState: 'unknown',
        historyItemId: INVALID_HISTORY_ID
    });

    loadTabUI(tabId);

    if (shouldBeActive) {
        switchToTab(tabId, false);
    }
}
```

在主机应用端，已注册 [的 ICoreWebView2WebMessageReceivedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2webmessagereceivedeventhandler) 将捕获消息并为该选项卡创建 WebView。

```cpp
        case MG_CREATE_TAB:
        {
            size_t id = args.at(L"tabId").as_number().to_uint32();
            bool shouldBeActive = args.at(L"active").as_bool();
            std::unique_ptr<Tab> newTab = Tab::CreateNewTab(m_hWnd, m_contentEnv.Get(), id, shouldBeActive);

            std::map<size_t, std::unique_ptr<Tab>>::iterator it = m_tabs.find(id);
            if (it == m_tabs.end())
            {
                m_tabs.insert(std::pair<size_t,std::unique_ptr<Tab>>(id, std::move(newTab)));
            }
            else
            {
                m_tabs.at(id)->m_contentWebView->Close();
                it->second = std::move(newTab);
            }
        }
        break;
```

```cpp
std::unique_ptr<Tab> Tab::CreateNewTab(HWND hWnd, ICoreWebView2Environment* env, size_t id, bool shouldBeActive)
{
    std::unique_ptr<Tab> tab = std::make_unique<Tab>();

    tab->m_parentHWnd = hWnd;
    tab->m_tabId = id;
    tab->SetMessageBroker();
    tab->Init(env, shouldBeActive);

    return tab;
}

HRESULT Tab::Init(ICoreWebView2Environment* env, bool shouldBeActive)
{
    return env->CreateCoreWebView2Controller(m_parentHWnd, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
        [this, shouldBeActive](HRESULT result, ICoreWebView2Controller* controller) -> HRESULT {
        if (!SUCCEEDED(result))
        {
            OutputDebugString(L"Tab WebView creation failed\n");
            return result;
        }
        m_contentController = controller;
        BrowserWindow::CheckFailure(m_contentController->get_CoreWebView2(&m_contentWebView), L"");
        BrowserWindow* browserWindow = reinterpret_cast<BrowserWindow*>(GetWindowLongPtr(m_parentHWnd, GWLP_USERDATA));
        RETURN_IF_FAILED(m_contentWebView->add_WebMessageReceived(m_messageBroker.Get(), &m_messageBrokerToken));

        // Register event handler for history change
        RETURN_IF_FAILED(m_contentWebView->add_HistoryChanged(Callback<ICoreWebView2HistoryChangedEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, IUnknown* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabHistoryUpdate(m_tabId, webview), L"Can't update go back/forward buttons.");

            return S_OK;
        }).Get(), &m_historyUpdateForwarderToken));

        // Register event handler for source change
        RETURN_IF_FAILED(m_contentWebView->add_SourceChanged(Callback<ICoreWebView2SourceChangedEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, ICoreWebView2SourceChangedEventArgs* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabURIUpdate(m_tabId, webview), L"Can't update address bar");

            return S_OK;
        }).Get(), &m_uriUpdateForwarderToken));

        RETURN_IF_FAILED(m_contentWebView->add_NavigationStarting(Callback<ICoreWebView2NavigationStartingEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, ICoreWebView2NavigationStartingEventArgs* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabNavStarting(m_tabId, webview), L"Can't update reload button");

            return S_OK;
        }).Get(), &m_navStartingToken));

        RETURN_IF_FAILED(m_contentWebView->add_NavigationCompleted(Callback<ICoreWebView2NavigationCompletedEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, ICoreWebView2NavigationCompletedEventArgs* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabNavCompleted(m_tabId, webview, args), L"Can't update reload button");
            return S_OK;
        }).Get(), &m_navCompletedToken));

        // Handle security state updates

        RETURN_IF_FAILED(m_contentWebView->Navigate(L"https://www.bing.com"));
        browserWindow->HandleTabCreated(m_tabId, shouldBeActive);

        return S_OK;
    }).Get());
}
```

该选项卡将注册所有处理程序，以便它可以在事件触发时将更新转发到控件 WebView。 选项卡已准备就绪，将显示在浏览器的内容区域中。 单击控件 WebView 中的选项卡会向主机应用程序发布一条消息，而主机应用程序又会隐藏以前处于活动状态的选项卡的 WebView，并显示单击选项卡的 WebView。

```cpp
HRESULT BrowserWindow::SwitchToTab(size_t tabId)
{
    size_t previousActiveTab = m_activeTabId;

    RETURN_IF_FAILED(m_tabs.at(tabId)->ResizeWebView());
    RETURN_IF_FAILED(m_tabs.at(tabId)->m_contentWebView->put_IsVisible(TRUE));
    m_activeTabId = tabId;

    if (previousActiveTab != INVALID_TAB_ID && previousActiveTab != m_activeTabId)
    {
        RETURN_IF_FAILED(m_tabs.at(previousActiveTab)->m_contentWebView->put_IsVisible(FALSE));
    }

    return S_OK;
}
```

#### <a name="updating-the-security-icon"></a>更新安全图标

我们使用 [CallDevToolsProtocolMethod](/microsoft-edge/webview2/reference/win32/icorewebview2#calldevtoolsprotocolmethod) 来侦听安全事件。 `securityStateChanged`每当触发事件时，我们将使用新状态更新控件 WebView 上的安全图标。

```cpp
        // Enable listening for security events to update secure icon
        RETURN_IF_FAILED(m_contentWebView->CallDevToolsProtocolMethod(L"Security.enable", L"{}", nullptr));

        BrowserWindow::CheckFailure(m_contentWebView->GetDevToolsProtocolEventReceiver(L"Security.securityStateChanged", &m_securityStateChangedReceiver), L"");

        // Forward security status updates to browser
        RETURN_IF_FAILED(m_securityStateChangedReceiver->add_DevToolsProtocolEventReceived(Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
            [this, browserWindow](ICoreWebView2* webview, ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT
        {
            BrowserWindow::CheckFailure(browserWindow->HandleTabSecurityUpdate(m_tabId, webview, args), L"Can't update security icon");
            return S_OK;
        }).Get(), &m_securityUpdateToken));
```

```cpp
HRESULT BrowserWindow::HandleTabSecurityUpdate(size_t tabId, ICoreWebView2* webview, ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args)
{
    wil::unique_cotaskmem_string jsonArgs;
    RETURN_IF_FAILED(args->get_ParameterObjectAsJson(&jsonArgs));
    web::json::value securityEvent = web::json::value::parse(jsonArgs.get());

    web::json::value jsonObj = web::json::value::parse(L"{}");
    jsonObj[L"message"] = web::json::value(MG_SECURITY_UPDATE);
    jsonObj[L"args"] = web::json::value::parse(L"{}");
    jsonObj[L"args"][L"tabId"] = web::json::value::number(tabId);
    jsonObj[L"args"][L"state"] = securityEvent.at(L"securityState");

    return PostJsonToWebView(jsonObj, m_controlsWebView.Get());
}
```

```javascript
        case commands.MG_SECURITY_UPDATE:
            if (isValidTabId(args.tabId)) {
                const tab = tabs.get(args.tabId);
                tab.securityState = args.state;

                if (args.tabId == activeTabId) {
                    updateNavigationUI(message);
                }
            }
            break;
```

#### <a name="populating-the-history"></a>填充历史记录

WebView2Browser 在控件 WebView 中使用 IndexedDB 来存储历史记录项，这只是 WebView2 如何使你能够像在浏览器中一样访问标准 Web 技术的示例。 更新 URI 后，将立即创建导航项。 然后，历史记录 UI 会在使用 `window.chrome.postMessage`这些项的选项卡中检索这些项。

在这种情况下，大多数功能都是在两端使用 JavaScript 实现的， (控制 WebView 和内容 WebView 加载 UI) ，因此主机应用程序仅充当消息代理来传达这些端。

```javascript
        case commands.MG_UPDATE_URI:
            if (isValidTabId(args.tabId)) {
                // ...

                // Don't add history entry if URI has not changed
                if (tab.uri == previousURI) {
                    break;
                }

                // Filter URIs that should not appear in history
                if (!tab.uri || tab.uri == 'about:blank') {
                    tab.historyItemId = INVALID_HISTORY_ID;
                    break;
                }

                if (tab.uriToShow && tab.uriToShow.substring(0, 10) == 'browser://') {
                    tab.historyItemId = INVALID_HISTORY_ID;
                    break;
                }

                addHistoryItem(historyItemFromTab(args.tabId), (id) => {
                    tab.historyItemId = id;
                });
            }
            break;
```

```javascript
function addHistoryItem(item, callback) {
    queryDB((db) => {
        let transaction = db.transaction(['history'], 'readwrite');
        let historyStore = transaction.objectStore('history');

        // Check if an item for this URI exists on this day
        let currentDate = new Date();
        let year = currentDate.getFullYear();
        let month = currentDate.getMonth();
        let date = currentDate.getDate();
        let todayDate = new Date(year, month, date);

        let existingItemsIndex = historyStore.index('stampedURI');
        let lowerBound = [item.uri, todayDate];
        let upperBound = [item.uri, currentDate];
        let range = IDBKeyRange.bound(lowerBound, upperBound);
        let request = existingItemsIndex.openCursor(range);

        request.onsuccess = function(event) {
            let cursor = event.target.result;
            if (cursor) {
                // There's an entry for this URI, update the item
                cursor.value.timestamp = item.timestamp;
                let updateRequest = cursor.update(cursor.value);

                updateRequest.onsuccess = function(event) {
                    if (callback) {
                        callback(event.target.result.primaryKey);
                    }
                };
            } else {
                // No entry for this URI, add item
                let addItemRequest = historyStore.add(item);

                addItemRequest.onsuccess = function(event) {
                    if (callback) {
                        callback(event.target.result);
                    }
                };
            }
        };

    });
}
```


<!-- ====================================================================== -->
## <a name="handling-json-and-uris"></a>处理 JSON 和 URI

WebView2Browser 使用 Microsoft 的 [cpprestsdk (Casablanca) ](https://github.com/Microsoft/cpprestsdk) 处理 C++ 方面的所有 JSON。 IUri 和 CreateUri 还用于将文件路径分析为 URI，也可用于其他 URI。
