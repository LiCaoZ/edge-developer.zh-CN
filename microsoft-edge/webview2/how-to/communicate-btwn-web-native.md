---
description: 使用 WebView2 将 Web 内容嵌入本机应用程序中
title: 将 Web 内容嵌入本机应用程序中
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/15/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、webview、WebView2 消息、WebView2 JavaScript、WebView2 本机对象
ms.openlocfilehash: 82844f3b789b239427d5e4c614b2b5b6b44fdd11
ms.sourcegitcommit: 97b32870897c702eed52d9fbbd13cfff2046ad87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2021
ms.locfileid: "12108675"
---
# <a name="embed-web-content-into-native-applications"></a>将 Web 内容嵌入本机应用程序中

使用 Microsoft Edge WebView2 控件，可以将 Web 内容嵌入本机应用程序中。  您可以根据需要完成的任务以不同方式使用 WebView2。  本文介绍如何使用简单消息、JavaScript 代码和本机对象进行通信。

一些常见用例包括：
* 导航到其他网站后更新本机主机窗口标题。
* 从 Web 应用发送本机相机对象并使用其方法。
* 在应用程序的 Web 端运行专用的 JavaScript 文件。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

本教程将分步演示示例应用代码，以演示 WebView2 中的一些通信功能。  克隆 [WebView2 示例应用](https://github.com/MicrosoftEdge/WebView2Samples)、生成和运行以继续操作。


<!-- ====================================================================== -->
## <a name="scenario-simple-messaging"></a>应用场景：简单消息传递

WebView2 控件让你在应用程序的 Web 和本机之间交换简单消息。  可以使用或 等数据类型在主机应用程序和 `JSON` `String` WebView2 之间发送消息。

### <a name="send-messages-from-the-host-app-to-webview2"></a>将消息从主机应用发送到 WebView2

此示例展示了示例应用如何根据主机应用的消息更改前端文本的颜色。

To see messaging in action， run the sample app， then select the **Scenario** tab and select the **Web Messaging** option.  将显示以下屏幕：

:::image type="content" source="../media/ScenarioWebMessaging.png" alt-text="Web 消息示例页，其中演示使用 Web 消息在主机应用和 WebView2 实例之间的基本交互。" lightbox="../media/ScenarioWebMessaging.png":::

请注意标题为 的第一节 `Posting Messages` 。  按照说明操作，然后选择**脚本**  >  **Post Message JSON**。  然后单击"**确定"。** 邮件变为蓝色。

:::image type="content" source="../media/postmessagejson.png" alt-text="&quot;Post Web Message JSON&quot;演示。" lightbox="../media/postmessagejson.png":::

我们如何更改文本颜色？  示例首先在本机创建按钮。  然后，该示例添加以下代码，以在单击按钮时发布 Web 消息。  此代码将 Web 文本的颜色更改为蓝色。

1. 该示例包含 C++ 代码，用于创建Windows时 `SendJsonWebMessage()` 调用的按钮。

    有关使用 C++ 创建按钮的信息，请参阅 [如何创建按钮](/windows/win32/controls/create-a-button)。

1. 单击按钮时，它会从 [ScriptComponent.cpp 调用以下代码](https://github.com/MicrosoftEdge/WebView2Samples/blob/c7d7c75184dec0c46634f27a8f4beba320b04618/SampleApps/WebView2APISample/ScriptComponent.cpp)。

    ```cpp
    // Prompt the user for some JSON and then post it as a web message.
    void ScriptComponent::SendJsonWebMessage()
    {
        TextInputDialog dialog(
            m_appWindow->GetMainWindow(),
            L"Post Web Message JSON",
            L"Web message JSON:",
            L"Enter the web message as JSON.",
            L"{\"SetColor\":\"blue\"}");
        if (dialog.confirmed)
        {
            m_webView->PostWebMessageAsJson(dialog.input.c_str());
        }
    }
    ```

    > [!NOTE]
    > 本教程的其余部分使用 `ScenarioWebMessage.html` WebView2 示例中的文件。  在您工作时比较您自己的 HTML 文件，或复制并粘贴来自 [ScenarioWebMessage.html](https://github.com/MicrosoftEdge/WebView2Samples/blob/a12bfcc2bc8a1155529c35c7bd4645036f492ca0/SampleApps/WebView2APISample/assets/ScenarioWebMessage.html)的内容。

    此示例使用 Web 上的 JavaScript 事件侦听器。

1. `ScenarioWebMessage.html` 标头中包含以下 JavaScript。

    ```JavaScript
    window.chrome.webview.addEventListener('message', arg => {
        if ("SetColor" in arg.data) {
            document.getElementById("colorable").style.color = arg.data.SetColor;
        }
    });
    ```

    事件侦听器 *侦听* 邮件事件，使邮件文本可着色。

    HTML 文件的内容描述了消息传递练习。

    ```html
    <h1>WebMessage sample page</h1>
    <p>This page demonstrates basic interaction between the host app and the webview by
    means of Web Messages.</p>

    <h2>Posting Messages</h2>
    <p id="colorable">Messages can be posted from the host app to the webview using the
    functions <code>ICoreWebView2::PostWebMessageAsJson</code> and
    <code>ICoreWebView2::PostWebMessageAsString</code>. Try selecting the menu item
    "Script > Post Message JSON" to send the message <code>{"SetColor":"blue"}</code>.
    It should change the text color of this paragraph.</p>
    ```

1. 该 `Post Message JSON` 菜单项位于生成的资源Microsoft Visual C++文件[WebView2APISample.rc 中](https://github.com/MicrosoftEdge/WebView2Samples/blob/c7d7c75184dec0c46634f27a8f4beba320b04618/SampleApps/WebView2APISample/WebView2APISample.rc)。

    ```xml
    MENUITEM "Post Message JSON",           IDM_POST_WEB_MESSAGE_JSON
    ```

1. 脚本文件反过来在 `IDM_POST_WEB_MESSAGE_JSON` [ScriptComponent.cpp 中调用大小写](https://github.com/MicrosoftEdge/WebView2Samples/blob/c7d7c75184dec0c46634f27a8f4beba320b04618/SampleApps/WebView2APISample/ScriptComponent.cpp)。

    ```cpp
    case IDM_POST_WEB_MESSAGE_JSON:
        SendJsonWebMessage();
        return true;
    ```

这完成显示 WebView2 如何通过简单消息进行通信的示例。

### <a name="receive-message-strings-via-postmessage"></a>通过 postMessage 接收邮件字符串

本示例在 `Receiving Messages` 网页的 部分之后更改标题栏的文本。  主机应用从 WebView2 接收包含新标题栏文本的消息。

C++ 文件处理标题文本，并作为字符串将文本传达给主机应用。

1. 单击按钮时，WebView2 使用 中的 方法将邮件从网页传输到 `window.chrome.webview.postMessage` [本机ScenarioWebMessage.html。 ](https://github.com/MicrosoftEdge/WebView2Samples/blob/a12bfcc2bc8a1155529c35c7bd4645036f492ca0/SampleApps/WebView2APISample/assets/ScenarioWebMessage.html)

    ```html
    function SetTitleText() {
        let titleText = document.getElementById("title-text");
        window.chrome.webview.postMessage(`SetTitleText ${titleText.value}`);
    }
    ```

    HTML 文件包含一个文本框和按钮，用于向主机应用发送消息。

    ```html
    <h2>Receiving Messages</h2>
    <p>The host app can receive messages by registering an event handler with
    <code>ICoreWebView2::add_WebMessageReceived</code>. If you enter text and click
    "Send", this page will send a message to the host app which will change the text of
    the title bar.</p>
    <input type="text" id="title-text"/>
    <button onclick="SetTitleText()">Send</button>
    ```

1. [ScenarioWebMessage.cpp](https://github.com/MicrosoftEdge/WebView2Samples/blob/a12bfcc2bc8a1155529c35c7bd4645036f492ca0/SampleApps/WebView2APISample/ScenarioWebMessage.cpp)中的事件处理程序处理新的标题文本字符串，并作为字符串与主机应用通信。

    ```cpp
    // Setup the web message received event handler before navigating to
    // ensure we don't miss any messages.
    CHECK_FAILURE(m_webView->add_WebMessageReceived(
        Microsoft::WRL::Callback<ICoreWebView2WebMessageReceivedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Source(&uri));

        // Always validate that the origin of the message is what you expect.
        if (uri.get() != m_sampleUri)
        {
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetTitleText(message.substr(13).c_str());
        }
        else if (message.compare(L"GetWindowBounds") == 0)
        {
            RECT bounds = m_appWindow->GetWindowBounds();
            std::wstring reply =
                L"{\"WindowBounds\":\"Left:" + std::to_wstring(bounds.left)
                + L"\\nTop:" + std::to_wstring(bounds.top)
                + L"\\nRight:" + std::to_wstring(bounds.right)
                + L"\\nBottom:" + std::to_wstring(bounds.bottom)
                + L"\"}";
            CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
        }
        return S_OK;
    }).Get(), &m_webMessageReceivedToken));
    ```

### <a name="round-trip-messages"></a>往返邮件

此示例遵循 `<h2>Round trip</h2>` WebMessage 示例页的 部分，ScenarioWebMessage.html。 [ ](https://github.com/MicrosoftEdge/WebView2Samples/blob/a12bfcc2bc8a1155529c35c7bd4645036f492ca0/SampleApps/WebView2APISample/assets/ScenarioWebMessage.html) 此示例显示从 WebView2 到主机应用和从主机应用到后端的往返消息。  主机应用从 WebView2 接收请求并返回活动窗口的界限。

当主机应用请求时，C++ 文件获取窗口边界，并将数据作为 JSON Web 消息发送到 WebView2。

1. 当用户单击该按钮时，WebView2 使用 将消息从网页传输到本机应用程序 `window.chrome.webview.postMessage` 。

    ```html
    function GetWindowBounds() {
        window.chrome.webview.postMessage("GetWindowBounds");
    }
    ```

    HTML 文件包含一个按钮，用于从主机应用获取窗口边界。

    ```html
    <h2>Round trip</h2>
    <p>The host app can send messages back in response to received messages. If you click the <b>Get window bounds</b> button, the host app reports back the bounds of its window, which are displayed in the text box.</p>
    <button onclick="GetWindowBounds()">Get window bounds</button><br>
    <textarea id="window-bounds" rows="4" readonly></textarea>
    ```

1. [ScenarioWebMessage.cpp](https://github.com/MicrosoftEdge/WebView2Samples/blob/a12bfcc2bc8a1155529c35c7bd4645036f492ca0/SampleApps/WebView2APISample/ScenarioWebMessage.cpp)中的事件处理程序获取窗口边界，然后使用 将数据发送到主机应用 `TryGetWebMessageAsString` ：

     ```cpp
    // Setup the web message received event handler before navigating to
    // ensure we don't miss any messages.
    CHECK_FAILURE(m_webView->add_WebMessageReceived(
        Microsoft::WRL::Callback<ICoreWebView2WebMessageReceivedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2WebMessageReceivedEventArgs* args)
    {
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_Source(&uri));

        // Always validate that the origin of the message is what you expect.
        if (uri.get() != m_sampleUri)
        {
            return S_OK;
        }
        wil::unique_cotaskmem_string messageRaw;
        CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
        std::wstring message = messageRaw.get();

        if (message.compare(0, 13, L"SetTitleText ") == 0)
        {
            m_appWindow->SetTitleText(message.substr(13).c_str());
        }
        else if (message.compare(L"GetWindowBounds") == 0)
        {
            RECT bounds = m_appWindow->GetWindowBounds();
            std::wstring reply =
                L"{\"WindowBounds\":\"Left:" + std::to_wstring(bounds.left)
                + L"\\nTop:" + std::to_wstring(bounds.top)
                + L"\\nRight:" + std::to_wstring(bounds.right)
                + L"\\nBottom:" + std::to_wstring(bounds.bottom)
                + L"\"}";
            CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
        }
        return S_OK;
    }).Get(), &m_webMessageReceivedToken));
    ```

1. 主机应用使用生成的资源脚本Microsoft Visual C++ `Inject Script` [WebView2APISample.rc](https://github.com/MicrosoftEdge/WebView2Samples/blob/c7d7c75184dec0c46634f27a8f4beba320b04618/SampleApps/WebView2APISample/WebView2APISample.rc)中的菜单项将窗口边界发送回网页。

    ```xml
        MENUITEM "Inject Script",               IDM_INJECT_SCRIPT
    ```

1. 脚本文件反过来调用 `IDM_INJECT_SCRIPT` [ScriptComponent.cpp 中的大小写](https://github.com/MicrosoftEdge/WebView2Samples/blob/c7d7c75184dec0c46634f27a8f4beba320b04618/SampleApps/WebView2APISample/ScriptComponent.cpp)：

    ```cpp
        case IDM_INJECT_SCRIPT:
            InjectScript();
            return true;
    ```

1. 窗口边界显示在网页上。


<!-- ====================================================================== -->
## <a name="scenario-send-javascript-code"></a>方案：发送 JavaScript 代码

此方案演示如何在 Web 端运行 JavaScript。  在此方法中，主机应用指定要运行的 JavaScript 代码，并通过 将代码传递给 `ExecuteScriptAsync` Web。  函数 `ExecuteScriptAsync` 将 JavaScript 结果返回给 `ExecuteScript` 调用方。

有关详细信息，请参阅在[WebView2 应用中使用 JavaScript。](javascript.md)


<!-- ====================================================================== -->
## <a name="scenario-send-native-objects"></a>方案：发送本机对象

将本机对象传递到 Web。 然后从 Web 调用对象的方法。

若要使用表示方法调用的消息，请使用 `AddHostObjectToScript` API。  在高级别上，此 API 允许你将本机 (主机) 对象公开到 Web 端并充当代理。  使用 访问这些对象 `window.chrome.webview.hostObjects.{name}` 。

将本机对象传递到应用程序的 Web 端在接口[ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2)的[AddHostObjectToScript](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript)部分中进行了介绍。

祝贺你！ 已成功将 Web 内容嵌入本机应用程序中。
