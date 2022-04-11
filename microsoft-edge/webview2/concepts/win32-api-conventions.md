---
title: Win32 C++ WebView2 API 约定
description: Win32 C++ WebView2 API 约定。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
ms.openlocfilehash: 1320dc54fbc08d01d931840572de2c3868617b50
ms.sourcegitcommit: 5351b3950b3bb7bc698415a2e5608816f1f9fca4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2022
ms.locfileid: "12473931"
---
# <a name="win32-c-webview2-api-conventions"></a>Win32 C++ WebView2 API 约定

支持的平台：Win32。


<!-- ====================================================================== -->
## <a name="prerequisites"></a>必备条件

*  使用 Win32 API 的经验。


<!-- ====================================================================== -->
## <a name="async-methods"></a>异步方法

WebView2 Win32 C++ API 中的异步方法使用委托接口与你联系，原因如下：

*  异步方法已完成。
*  成功或失败代码。
*  异步方法的结果。

所有异步方法的最终参数是指向委托接口的指针，其中提供实现。

委托接口具有单 `Invoke` 个方法，用作成功或失败代码的第一个 `HRESULT` 参数。  此外，如果方法有结果，则可能有第二个参数是该方法的结果。

例如， [ICoreWebView2：：CapturePreview](/microsoft-edge/webview2/reference/win32/icorewebview2#capturepreview) 方法采用 `ICoreWebView2CapturePreviewCompletedHandler` 指针作为最终参数。  若要 `CapturePreview` 发送方法请求，请提供实现的 `ICoreWebView2CapturePreviewCompletedHandler` 指针的实例。

以下代码使用该 `Invoke` 方法实现 `ICoreWebView2CapturePreviewCompletedHandler` 指针：

```cpp
HRESULT Invoke(HRESULT result)
```

实现该`Invoke`方法，然后`CoreWebView2`在请求完成时`CapturePreview`请求方法`Invoke`。  单个参数是 `HRESULT` 描述请求的成功或失败代码 `CapturePreview` 。

或者，为 `ICoreWebView2::ExecuteScript`你提供一个实例，该实例具有一个 `Invoke` 方法，用于提供请求的成功或失败代码 `ExecuteScript` 。  此外，还提供第二个参数，即运行脚本的结果的 JSON。

可以手动实现 `CompleteHandler` 委托接口，也可以使用 [回调函数 (WRL) ](/cpp/cppcx/wrl/callback-function-wrl)。  [回调函数 (WRL) ](/cpp/cppcx/wrl/callback-function-wrl)在以下 WebView2 代码中使用：

```cpp
void ScriptComponent::InjectScript()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Inject Script",
        L"Enter script code:",
        L"Enter the JavaScript code to run in the WebView2 control.",
        L"window.getComputedStyle(document.body).backgroundColor");
    if (dialog.confirmed)
    {
        m_webView->ExecuteScript(dialog.input.c_str(),
            Callback<ICoreWebView2ExecuteScriptCompletedHandler>(
                [](HRESULT error, PCWSTR result) -> HRESULT
        {
            if (error != S_OK) {
                ShowFailure(error, L"ExecuteScript failed");
            }
            MessageBox(nullptr, result, L"ExecuteScript Result", MB_OK);
            return S_OK;
        }).Get());
    }
}
```


<!-- ====================================================================== -->
## <a name="events"></a>事件

WebView2 Win32 C++ API 中的事件使用 `add_EventName` 和 `remove_EventName` 方法对订阅和取消订阅事件。  该 `add_EventName` 方法采用事件处理程序委托接口，并将令牌作为输出参数返回 `EventRegistrationToken` 。  该 `remove_EventName` 方法采用令 `EventRegistrationToken` 牌并取消订阅相应的事件订阅。

### <a name="event-handler-delegate-interfaces"></a>事件处理程序委托接口

事件处理程序委托接口的工作方式与异步方法已完成的处理程序委托接口类似。  实现事件处理程序委托接口，并在 `CoreWebView2` 事件运行时发送回调。  

每个事件处理程序委托接口都有一个 `Invoke` 方法，该方法具有一个发送方参数，后跟事件 args 参数。  发件人是订阅事件的对象的实例。  事件 args 参数是一个接口，其中包含有关当前触发事件的信息。

例如，上`NavigationCompleted``ICoreWebView2`的事件具有`ICoreWebView2::add_NavigationCompleted`和`ICoreWebView2::remove_NavigationCompleted`方法对。  发送请求时，将提供以前实现`Invoke`的方法的`ICoreWebView2NavigationCompletedEventHandler`实例。

`NavigationCompleted`当事件运行时，将请求你`Invoke`的方法：

*  第一个参数运行事件 `NavigationCompleted` 。
*  第二个参数包含有关导航是否成功完成的信息，等等。

与异步方法已完成的处理程序委托接口类似，使用以下操作之一进行设置：

*  直接实现它。

*  使用以下 WebView2 代码中使用的回 [调函数 (WRL) ](/cpp/cppcx/wrl/callback-function-wrl) 函数：

<!-- todo:  what is async method completed handler delegate interface?  Is there a shorter name for it?  -->

```cpp
// Register a handler for the NavigationCompleted event.
// Check whether the navigation succeeded, and if not, do something.
// Also update the Cancel buttons.
CHECK_FAILURE(m_webView->add_NavigationCompleted(
    Callback<ICoreWebView2NavigationCompletedEventHandler>(
        [this](ICoreWebView2* sender, ICoreWebView2NavigationCompletedEventArgs* args)
            -> HRESULT {
            BOOL success;
            CHECK_FAILURE(args->get_IsSuccess(&success));
            if (!success)
            {
                COREWEBVIEW2_WEB_ERROR_STATUS webErrorStatus;
                CHECK_FAILURE(args->get_WebErrorStatus(&webErrorStatus));
                if (webErrorStatus == COREWEBVIEW2_WEB_ERROR_STATUS_DISCONNECTED)
                {
                    // Do something here if you want to handle a specific error case.
                    // In most cases it is not necessary, because the WebView2 control
                    // displays an error page automatically.
                }
            }
            m_toolbar->SetItemEnabled(Toolbar::Item_CancelButton, false);
            m_toolbar->SetItemEnabled(Toolbar::Item_ReloadButton, true);
            return S_OK;
        })
        .Get(),
    &m_navigationCompletedToken));
```


<!-- ====================================================================== -->
## <a name="strings"></a>字符串

字符串输出参数是 `LPWSTR` 以 null 结尾的字符串。  请求者使用 `CoTaskMemAlloc`> 提供字符串。  所有权将转让给请求者，由请求者使用 `CoTaskMemFree`它释放内存。

字符串输入参数是 `LPCWSTR` 以 null 结尾的字符串。  请求者确保字符串在同步函数请求的持续时间内有效。  如果接收方必须在函数请求完成后将值存储到某个点，则接收方必须提供字符串值的关联副本。


<!-- ====================================================================== -->
## <a name="uri-and-json-parsing"></a>URI 和 JSON 分析

各种方法提供或接受 URI 和 JSON 作为字符串。  使用首选库分析和生成字符串。

如果 WinRT 可用于应用，则可以使用`RuntimeClass_Windows_Data_Json_JsonObject`和`IJsonObjectStatics`方法来分析或生成 JSON 字符串，或者`RuntimeClass_Windows_Foundation_Uri``IUriRuntimeClassFactory`使用方法来分析和生成 URI。  这两种方法都适用于 Win32 应用。

如果使用 `IUri` 和 `CreateUri` 分析 URI，可能需要使用以下 URI 创建标志，使 `CreateUri` 行为与 WebView2 控件中的 URI 分析更匹配：

```json
Uri_CREATE_ALLOW_IMPLICIT_FILE_SCHEME | Uri_CREATE_NO_DECODE_EXTRA_INFO
```


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [在 Win32 应用中使用 WebView2 开始](../get-started/win32.md) - WebView2 Win32 C/C++。
* [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
