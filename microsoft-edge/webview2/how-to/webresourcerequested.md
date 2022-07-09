---
title: 网络请求的自定义管理
description: 在 WebView2 应用中使用 WebResourceRequested 事件和 WebResourceResponseReceived 事件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/29/2022
ms.openlocfilehash: dc8570d2591757b5be0f42b447eac5fcf73bb481
ms.sourcegitcommit: 61d541b18043bdc4b2a6d65d6eb7422d54da2c2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2022
ms.locfileid: "12639922"
---
# <a name="custom-management-of-network-requests"></a>网络请求的自定义管理
<!--
# Custom management of network requests and responses in WebView2
# Managing network requests in WebView2
# Navigating with web resource request and response events
-->

<!-- todo
writer: add arrows to diagrams
writer: read through body content
-->

Microsoft Edge WebView2 控件允许你与网络请求进行交互和修改。  可以使用这些和`WebResourceResponseReceived`事件提供响应或修改网络请求`WebResourceRequested`。  还有一些特殊功能，可用于使用 `NavigateWithWebResourceRequest API`特定的网络请求进行导航。

本文介绍如何修改网络请求。  使用此 API 和方法可执行以下操作：
* 将本地文件内容上传到应用，以添加对脱机功能的支持。
* 阻止网页中的内容，例如特定图像。
* 微调特定页面的身份验证。

**术语：**

| 术语 | 定义 |
|---|---|
| 拦截 | 主机应用可以截获从 WebView2 控件发送到 HTTP 服务器的请求，读取或修改请求，然后将未更改或修改的请求发送到 HTTP 服务器 (或本地代码，而不是 HTTP 服务器) 。 |
| 覆盖 | 主机应用可以替代从 HTTP 服务器发送到 WebView2 控件的响应，并将自定义响应发送到 WebView2 控件，而不是原始响应。 |


<!-- ====================================================================== -->
## <a name="when-to-use-custom-vs-basic-approaches"></a>何时使用自定义方法与基本方法

该 `WebResourceRequested` 事件是一个低级别 API，它提供更多的控制，但需要更多的编码，并且使用起来很复杂。  对于某些常见方案，我们提供更易于使用的 API，并针对这些特定方案进行了优化，建议使用这些 API，而不是本文中讨论的 API。

如果可行，最好使用以下其他方法，而不是使用 WebResourceRequested API：
* [基本身份验证](/microsoft-edge/webview2/concepts/basic-authentication?tabs=csharp)
* [常规导航](/microsoft-edge/webview2/concepts/navigation-events) 
* [在 WebView2 中管理 Cookie](/microsoft-edge/webview2/reference/win32/icorewebview2)
* 设置用户代理字符串。  请参阅 [UserAgent 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#useragent)。

**注意：** 对于具有虚拟主机名的 URL，不支持使用 `WebResourceRequested` 该事件。  这是因为 `WebResourceRequested` 不会为 [SetVirtualHostNameToFolderMapping 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_3#setvirtualhostnametofoldermapping)触发事件。<!-- or ClearVirtualHostNameToFolderMapping. -->


### <a name="how-your-host-app-the-webview2-control-and-the-http-server-interact"></a>主机应用、WebView2 控件和 HTTP 服务器的交互方式

WebView2 控件位于主机应用和 HTTP 服务器之间。  当主机应用导航到 URI 时，WebView2 控件会向 HTTP 服务器发送请求。  然后，HTTP 服务器将响应发送到 WebView2 控件。

<!-- lexicon for the 3 actors:
the HTTP server
the WebView2 control
the host app
-->


<!-- ====================================================================== -->
## <a name="intercepting-a-request-to-monitor-or-modify-it"></a>截获请求，监视或修改请求

主机应用可以 _截获_ 从 WebView2 控件发送到 HTTP 服务器的请求，读取或修改请求，然后将未更改或修改的请求发送到 HTTP 服务器 (或本地代码，而不是 HTTP 服务器) 。 

通过截获请求，可以自定义标头内容、URL 或 GET/POST 方法。  主机应用可能想要截获请求以提供可选 POST 内容作为请求的一部分。

主机应用可以使用此 API 更改请求的属性：

# [<a name="net"></a>.NET](#tab/dotnet)

* [CoreWebView2WebResourceRequest 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcerequest)

# [<a name="win32"></a>Win32](#tab/win32)

* [ICoreWebView2WebResourceRequest](/microsoft-edge/webview2/reference/win32/icorewebview2webresourcerequest)

---

### <a name="what-you-can-do-with-headers"></a>可使用标头执行的操作

HTTP 标头提供有关请求或响应的重要信息和元数据。  通过更改 [标头](https://developer.mozilla.org/docs/Glossary/HTTP_header) ，可以在网络上执行强大的操作。 

[请求标头](https://developer.mozilla.org/docs/Glossary/Request_header)可用于指示响应 (的格式，例如`Accept-*`标头) 、设置身份验证令牌、读取和写入 cookie (敏感信息) 、修改用户代理等。  [响应标头](https://developer.mozilla.org/docs/Glossary/Response_header)可用于提供响应的更多上下文。

### <a name="filtering-the-webresourcerequested-event-based-on-url-and-resource-type"></a>根据 URL 和资源类型筛选 WebResourceRequested 事件

为了接收 `WebResourceRequested` 事件，请根据 URL 和资源类型为主机应用感兴趣的请求指定筛选器。

例如，假设主机应用正在尝试替换映像。  在这种情况下，主机应用只对图像的事件感兴趣 `WebResourceRequested` 。  主机应用仅通过为图像指定 `resourceContext` 筛选器来获取图像的事件。

另一个示例是，如果主机应用只对网站下的所有请求感兴趣，例如 `https://example.com`。  然后，应用可以指定 URL 筛选器 `https://example.com/*` 来获取与该网站关联的事件。

# [<a name="net"></a>.NET](#tab/dotnet)

* [CoreWebView2.AddWebResourceRequestedFilter 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter)

# [<a name="win32"></a>Win32](#tab/win32)

* [AddWebResourceRequestedFilter 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#addwebresourcerequestedfilter)

---


有关 URL 筛选器工作原理的详细信息，请参阅 [CoreWebView2.AddWebResourceRequestedFilter 方法>备注](/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter#remarks)


### <a name="why-would-you-want-to-intercept-requests-that-are-sent-from-webview2"></a>为何要截获从 WebView2 发送的请求？  

通过截获从 WebView2 发送的请求，可以进一步配置请求。 主机应用可能希望提供可选内容，作为 WebView2 控件本身不知道的请求的一部分。 某些方案包括：
*  你正在登录到页面，并且应用具有凭据，因此应用可以提供身份验证标头，而无需用户输入这些凭据。  
*  需要应用中的脱机功能，以便在未检测到 Internet 连接时将 URL 重定向到本地文件路径。
*  需要通过 POST 请求将本地文件内容上传到请求服务器。


### <a name="sequence-for-modifying-requests"></a>修改请求的序列

<!-- wiki page that points to the Visio source file: Documentation > "Notes about specific image files" -->
![用于修改请求的序列图。](webresourcerequested-images/sequence-for-modifying-requests.png)

1. 主机应用设置 `WebResourceRequested` 筛选器。
1. 主机应用为其定义事件处理程序，并`WebResourceResponseReceived`定义该处理程序`WebResourceRequested`。
1. 主机应用将 WebView2 控件导航到网页。
1. WebView2 控件为网页所需的资源创建请求。
1. WebView2 控件向主机应用触发 `WebResourceRequested` 事件。
1. 主机应用侦听并处理 `WebResourceRequested` 事件。
1. 此时，主机应用可以修改标头。  主机应用还可以推迟 `WebResourceRequested` 事件，这意味着主机应用需要更多时间来决定要执行的操作。
1. 例如，WebView2 网络堆栈可以添加更多标头 (可以添加 cookie 和授权标头) 。
1. WebView2 控件将请求发送到 HTTP 服务器。
1. HTTP 服务器将响应发送到 WebView2 控件。
1. WebView2 控件触发事件 `WebResourceResponseReceived` 。
1. 主机应用侦听 `WebResourceResponseReceived` 事件并处理它。<!-- todo: arrow: "The WebView2 control creates a request for a resource that's needed for the webpage." -->


<!-- ====================================================================== -->
### <a name="example-intercepting-a-request-to-monitor-or-modify-it"></a>示例：截获请求，监视或修改请求
<!-- ## Example: Header modification when making a request -->

<!-- this example doesn't exist in the sample repo -->

<!-- note: the below intro is based on copying the main h2's Sentence 1 from above: -->
在以下示例中，主机应用 _截获_ 从 WebView2 控件发送到 `http://www.example.com` HTTP 服务器的文档请求，添加自定义标头值并发送请求。  

# [<a name="net"></a>.NET](#tab/dotnet)

```csharp
// Add a filter to select all resource types under http://www.example.com
webView.CoreWebView2.AddWebResourceRequestedFilter(
      "http://www.example.com/*", CoreWebView2WebResourceContext.All);
webView.CoreWebView2.WebResourceRequested += delegate (
   object sender, CoreWebView2WebResourceRequestedEventArgs args) {
   CoreWebView2WebResourceContext resourceContext = args.ResourceContext;
   // Only intercept the document resources
   if (resourceContext != CoreWebView2WebResourceContext.Document)
   {
      return;
   }
   CoreWebView2HttpRequestHeaders requestHeaders = args.Request.Headers;
   requestHeaders.SetHeader("Custom", "Value");
}
```

# [<a name="win32"></a>Win32](#tab/win32)

```cpp
// Add a filter to select all resource types under http://www.example.com
m_webView->AddWebResourceRequestedFilter(
      L"http://www.example.com/*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_ALL);
m_webView->add_WebResourceRequested(
      Callback<ICoreWebView2WebResourceRequestedEventHandler>(
         [this](
            ICoreWebView2* sender,
            ICoreWebView2WebResourceRequestedEventArgs* args) {
            COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
            CHECK_FAILURE(args->get_ResourceContext(&resourceContext));
            // Only intercept the document resources
            if (resourceContext != COREWEBVIEW2_WEB_RESOURCE_CONTEXT_DOCUMENT)
            {
               return S_OK;
            }

            // Set a custom header to the document request.
            wil::com_ptr<ICoreWebView2WebResourceRequest> request;
            CHECK_FAILURE(args->get_Request(&request));
            wil::com_ptr<ICoreWebView2HttpRequestHeaders> headers;
            request->get_Headers(&headers);
            headers->SetHeader(L"Custom", L"Value");
            return S_OK;
         })
         .Get(),
      &m_webResourceRequestedToken);
```  

---

<!-- ====================================================================== -->
## <a name="overriding-a-response-to-proactively-replace-it"></a>重写响应，主动替换响应
<!-- Overriding and providing new responses to WebView2 -->
<!-- ## Overriding the response and providing a different, custom response to the WebView2 control -->

默认情况下，HTTP 服务器将响应发送到 WebView2 控件。  主机应用可以 _替代_ 从 HTTP 服务器发送到 WebView2 控件的响应，并将自定义响应发送到 WebView2 控件，而不是原始响应。


### <a name="sequence-for-overriding-responses"></a>替代响应的序列

<!-- wiki page that points to the Visio source file: Documentation > "Notes about specific image files" -->
![用于重写响应的序列图。](webresourcerequested-images/sequence-for-overriding-responses.png)

1. 主机应用设置 `WebResourceRequested` 筛选器。
1. 主机应用为其定义事件处理程序，并`WebResourceResponseReceived`定义该处理程序`WebResourceRequested`。
1. 主机应用将 WebView2 控件导航到网页。
1. WebView2 控件为网页所需的资源创建请求。
1. WebView2 控件向主机应用触发 `WebResourceRequested` 事件。
1. 主机应用侦听并处理 `WebResourceRequested` 事件。
1. 主机应用设置对事件处理程序的 `WebResourceRequested` 响应。  主机应用还可以推迟 `WebResourceRequested` 事件，这意味着主机应用需要更多时间来决定要执行的操作。
1. WebView2 控件将响应呈现为资源。
<!-- todo: remove "then" from diagram step 8 -->


### <a name="example-overriding-a-response-to-proactively-replace-it"></a>示例：重写响应，以主动替换响应

# [<a name="net"></a>.NET](#tab/dotnet)

```csharp
// Add a filter to select all image resources
webView.CoreWebView2.AddWebResourceRequestedFilter(
      "*", CoreWebView2WebResourceContext.Image);
webView.CoreWebView2.WebResourceRequested += delegate (
   object sender, CoreWebView2WebResourceRequestedEventArgs args) {
    
   // Replace the remote image resource with a local one specified at the path customImagePath.
   // If response is not set, the request will continue as it is.
   FileStream fs = File.Open(customImagePath, FileMode.Open);
   CoreWebView2WebResourceResponse response = webView.CoreWebView2.Environment.CreateWebResourceResponse(fs, 200, "OK", "Content-Type: image/jpeg");
   args.Response = response;
};
```

# [<a name="win32"></a>Win32](#tab/win32)

```cpp
// Add a filter to select all image resources
m_webView->AddWebResourceRequestedFilter(
                L"*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE);
m_webView->add_WebResourceRequested(
   Callback<ICoreWebView2WebResourceRequestedEventHandler>(
      [this](
         ICoreWebView2* sender,
         ICoreWebView2WebResourceRequestedEventArgs* args) {
         COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
         args->get_ResourceContext(&resourceContext);

         // Replace the remote image resource with a local one specified at the path customImagePath.
         // If response is not set, the request will continue as it is.
         wil::com_ptr<IStream> stream;
         SHCreateStreamOnFileEx(
               customImagePath, STGM_READ, FILE_ATTRIBUTE_NORMAL,
               FALSE, nullptr, &stream);
         wil::com_ptr<ICoreWebView2WebResourceResponse> response;
         wil::com_ptr<ICoreWebView2Environment> environment;
         wil::com_ptr<ICoreWebView2_2> webview2;
         m_webView->QueryInterface(IID_PPV_ARGS(&webview2));
         webview2->get_Environment(&environment);
         environment->CreateWebResourceResponse(
               stream.get(), 200, L"OK", L"Content-Type: image/jpeg", &response);
         args->put_Response(response.get());
         return S_OK;
      })
      .Get(),
   &m_webResourceRequestedToken);
```

---


<!-- ====================================================================== -->
## <a name="constructing-a-custom-request-and-navigating-using-that-request"></a>构造自定义请求并使用该请求导航
<!-- ## Constructing a custom request and navigating the WebView2 control using that request -->
<!-- ## Navigating with custom requests  -->
<!-- use-case: Navigating (vs. Overriding or Intercepting) -->

该 `NavigateWithWebResourceRequest` 方法允许主机应用使用自定义 `WebResourceRequest`导航 WebView2 控件。  可以使用此 API 创建具有自定义标头和内容的 GET 或 POST 请求。  然后，WebView2 控件将使用此自定义请求进行导航。

# [<a name="net"></a>.NET](#tab/dotnet)

* [CoreWebView2.NavigateWithWebResourceRequest (CoreWebView2WebResourceRequest) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigatewithwebresourcerequest)

# [<a name="win32"></a>Win32](#tab/win32)

* [接口ICoreWebView2_2：：NavigateWithWebResourceRequest 方法](/microsoft-edge/webview2/reference/win32/icorewebview2_2#navigatewithwebresourcerequest)

---

<!-- ====================================================================== -->
### <a name="example-constructing-a-custom-request-and-navigating-using-that-request"></a>示例：构造自定义请求并使用该请求导航

<!-- This is an existing example in the Win32 sample app. -->

<!-- CreateWebResourceRequest and NavigateWithWebResourceRequest -->

<!-- the code listings below were not copied from the sample app; they were copied from the spec.  ok?
from https://github.com/MicrosoftEdge/WebView2Feedback/blob/main/specs/NavigateWithWebResourceRequest.md#examples -->


<!-- -------------------------------------------------- -->

# [<a name="net"></a>.NET](#tab/dotnet)

```csharp
// This code posts text input=Hello to the POST form page in W3Schools.

// Need to convert post data to UTF-8 as required by the application/x-www-form-urlencoded Content-Type 
UTF8Encoding utfEncoding = new UTF8Encoding();
byte[] postData = utfEncoding.GetBytes("input=Hello");

MemoryStream postDataStream = new MemoryStream(postData.Length);
postDataStream.Write(postData, 0, postData.Length);
postDataStream.Seek(0, SeekOrigin.Begin);

// This acts as a HTML form submit to https://www.w3schools.com/action_page.php
CoreWebView2WebResourceRequest webResourceRequest = 
environment.CreateWebResourceRequest("https://www.w3schools.com/action_page.php",
                                     "POST",
                                     postDataStream,
                                    "Content-Type: application/x-www-form-urlencoded");
webView.CoreWebView2.NavigateWithWebResourceRequest(webResourceRequest);
```

<!-- -------------------------------------------------- -->

# [<a name="win32"></a>Win32](#tab/win32)

```cpp
// This code posts text input=Hello to the POST form page in W3Schools.

// Need to convert post data to UTF-8 as required by the application/x-www-form-urlencoded Content-Type 
std::wstring postData = std::wstring(L"input=Hello");
int sizeNeededForMultiByte = WideCharToMultiByte(
   CP_UTF8, 0, postData.c_str(), postData.size(), nullptr,
   0, nullptr, nullptr);

std::unique_ptr<char[]> postDataBytes = std::make_unique<char[]>(sizeNeededForMultiByte);
WideCharToMultiByte(
   CP_UTF8, 0, postData.c_str(), postData.size(), postDataBytes.get(),
   sizeNeededForMultiByte, nullptr, nullptr);

wil::com_ptr<ICoreWebView2WebResourceRequest> webResourceRequest;
wil::com_ptr<IStream> postDataStream = SHCreateMemStream(
      reinterpret_cast<const BYTE*>(postDataBytes.get()), sizeNeededForMultiByte);

// This acts as a HTML form submit to https://www.w3schools.com/action_page.php
webviewEnvironment->CreateWebResourceRequest(
   L"https://www.w3schools.com/action_page.php", L"POST", postDataStream.get(),
   L"Content-Type: application/x-www-form-urlencoded", &webResourceRequest);
webview->NavigateWithWebResourceRequest(webResourceRequest.get());
```

---


<!-- ====================================================================== -->
## <a name="monitoring-the-requests-and-responses-via-the-webresourceresponsereceived-event"></a>通过 WebResourceResponseReceived 事件监视请求和响应

可以通过事件监视请求和响应 `WebResourceResponseReceived` ，以读取任何标头值。


### <a name="example-monitoring-the-requests-and-responses-via-the-webresourceresponsereceived-event"></a>示例：通过 WebResourceResponseReceived 事件监视请求和响应

此示例演示如何通过 `WebResourceResponseReceived` 事件监视请求和响应来读取授权标头值。

以下代码演示如何使用事件 `WebResourceResponseReceived` 。
<!-- from https://github.com/MicrosoftEdge/WebView2Feedback/blob/main/specs/WebResourceResponseReceived.md#examples -->


<!-- -------------------------------------------------- -->

# [<a name="net"></a>.NET](#tab/dotnet)

```csharp
WebView.WebResourceResponseReceived += WebView_WebResourceResponseReceived;

// Note: modifications made to request are set but have no effect on WebView processing it.
private async void WebView_WebResourceResponseReceived(object sender, CoreWebView2WebResourceResponseReceivedEventArgs e)
{
    // Actual headers sent with request
    foreach (var current in e.Request.Headers)
    {
        Console.WriteLine(current);
    }

    // Headers in response received
    foreach (var current in e.Response.Headers)
    {
        Console.WriteLine(current);
    }

    // Status code from response received
    int status = e.Response.StatusCode;
    if (status == 200)
    {
        Console.WriteLine("Request succeeded!");

        // Get response body
        try
        {
            System.IO.Stream content = await e.Response.GetContentAsync();
            // Null will be returned if no content was found for the response.
            if (content != null)
            {
                DoSomethingWithResponseContent(content);
            }
        }
        catch (COMException ex)
        {
            // A COMException will be thrown if the content failed to load.
        }
    }
}
```

<!-- -------------------------------------------------- -->

# [<a name="win32"></a>Win32](#tab/win32)

COM 示例，使用 `ICoreWebView2WebResourceRequest`.

```cpp
EventRegistrationToken m_webResourceResponseReceivedToken = {};

m_webView->add_WebResourceResponseReceived(
    Callback<ICoreWebView2WebResourceResponseReceivedEventHandler>(
        [this](ICoreWebView2* webview, ICoreWebView2WebResourceResponseReceivedEventArgs* args)
            -> HRESULT {
            // The request object as committed
            wil::com_ptr<ICoreWebView2WebResourceRequest> webResourceRequest;
            args->get_Request(&webResourceRequest);
            // The response object as received
            wil::com_ptr<ICoreWebView2WebResourceResponseView> webResourceResponse;
            args->get_Response(&webResourceResponse);
            
            // Get body content for the response
            webResourceResponse->GetContent(
                Callback<
                    ICoreWebView2WebResourceResponseViewGetContentCompletedHandler>(
                    [this, webResourceRequest, webResourceResponse](HRESULT result, IStream* content) {
                        // The response content might have failed to load.
                        bool getContentSucceeded = SUCCEEDED(result);

                        // The stream will be null if no content was found for the response.
                        if (content) {
                            DoSomethingWithContent(content);
                        }
                        
                        return S_OK;
                    })
                    .Get());

            return S_OK;
        })
        .Get(),
    &m_webResourceResponseReceivedToken);
```

---


<!-- ====================================================================== -->
## <a name="api-reference-overview"></a>API 参考概述

<!-- -------------------------------------------------- -->

# [<a name="net"></a>.NET](#tab/dotnet)


**请求：**

* [CoreWebView2.AddWebResourceRequestedFilter 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter)
* [CoreWebView2.NavigateWithWebResourceRequest 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.navigatewithwebresourcerequest)
* [CoreWebView2.RemoveWebResourceRequestedFilter 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.removewebresourcerequestedfilter)
* [CoreWebView2.WebResourceRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourcerequested)
* [CoreWebView2Environment.CreateWebResourceRequest 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createwebresourcerequest)
* [CoreWebView2WebResourceContext 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcecontext)
* [CoreWebView2WebResourceRequest 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcerequest)
   * `Content`
   * `Headers`
   * `Method`
   * `Uri`
* [CoreWebView2WebResourceRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourcerequestedeventargs)
   * `Request`
   * `ResourceContext`
   * `Response`
   * `GetDeferral`

**响应：**

* [CoreWebView2.WebResourceResponseReceived 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.webresourceresponsereceived)
* [CoreWebView2Environment.CreateWebResourceResponse 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createwebresourceresponse)
* [CoreWebView2WebResourceResponse 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourceresponse)
   * `Content`
   * `Headers`
   * `ReasonPhrase`
   * `StatusCode`
* [CoreWebView2WebResourceResponseReceivedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourceresponsereceivedeventargs)
   * `Request`
   * `Response`
* [CoreWebView2WebResourceResponseView 类](/dotnet/api/microsoft.web.webview2.core.corewebview2webresourceresponseview)
   * `Headers`
   * `ReasonPhrase`
   * `StatusCode`
   * `GetContentAsync`

<!-- -------------------------------------------------- -->

# [<a name="win32"></a>Win32](#tab/win32)

**请求：**

* [ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2)
   * `add_WebResourceRequested`
   * `AddWebResourceRequestedFilter`
   * `remove_WebResourceRequested`
   * `RemoveWebResourceRequestedFilter`
* [ICoreWebView2Environment2](/microsoft-edge/webview2/reference/win32/icorewebview2environment2)
   * `CreateWebResourceRequest`   
* [ICoreWebView2WebResourceRequest](/microsoft-edge/webview2/reference/win32/icorewebview2webresourcerequest)
   * `get_Content`
   * `get_Headers`
   * `get_Method`
   * `get_Uri`
   * `put_Content`
   * `put_Method`
   * `put_Uri`
* [ICoreWebView2WebResourceRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2webresourcerequestedeventargs)
   * `get_Request`
   * `get_ResourceContext`
   * `get_Response`
   * `GetDeferral`
   * `put_Response`
* [ICoreWebView2WebResourceRequestedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2webresourcerequestedeventhandler)
   * `Invoke`

**响应：**

* [ICoreWebView2_2](/microsoft-edge/webview2/reference/win32/icorewebview2_2)
   * `add_WebResourceResponseReceived`
   * `NavigateWithWebResourceRequest`
   * `remove_WebResourceResponseReceived`
* [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment)
   * `CreateWebResourceResponse`
* [ICoreWebView2WebResourceResponse](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponse)
   * `get_Content`
   * `get_Headers`
   * `get_ReasonPhrase`
   * `get_StatusCode`
   * `put_Content`
   * `put_ReasonPhrase`
   * `put_StatusCode`
* [ICoreWebView2WebResourceResponseReceivedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponsereceivedeventargs)
   * `get_Request`
   * `get_Response`
* [ICoreWebView2WebResourceResponseReceivedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponsereceivedeventhandler)
   * `Invoke`
* [ICoreWebView2WebResourceResponseView](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponseview)
   * `get_Headers`
   * `get_ReasonPhrase`
   * `get_StatusCode`
   * `GetContent`
* [ICoreWebView2WebResourceResponseViewGetContentCompletedHandler](/microsoft-edge/webview2/reference/win32/icorewebview2webresourceresponseviewgetcontentcompletedhandler)
   * `Invoke`

---


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [从 Web 端代码调用本机代码](hostobject.md)
* _WebView2 功能和 API 概述中的 Web_[/本机互操作](../concepts/overview-features-apis.md#webnative-interop)。

<!-- 
* [NavigateWithWebResourceRequest spec](https://github.com/MicrosoftEdge/WebView2Feedback/blob/main/specs/NavigateWithWebResourceRequest.md)
* [WebResourceResponseReceived event spec](https://github.com/MicrosoftEdge/WebView2Feedback/blob/main/specs/WebResourceResponseReceived.md) -->
