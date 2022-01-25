---
title: WebView2 的线程模型
description: 在 WebView2 线程模型中，必须在具有消息等待的 UI 线程上创建 WebView2。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 09/21/2021
ms.openlocfilehash: a7b055de51d03c61c5c1859c99964b91cd254956
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12319624"
---
# <a name="threading-model-for-webview2"></a>WebView2 的线程模型

支持的平台：Win32、Windows Forms、WinUi、WPF。

WebView2 控件基于组件对象模型 [ (COM) ](/windows/win32/com/the-component-object-model) 并且必须在单个线程处理线程上 (STA [) ](/windows/win32/com/single-threaded-apartments) 线程。


<!-- ====================================================================== -->
## <a name="thread-safety"></a>线程安全

WebView2 必须在使用消息线索的 UI 线程上创建。  所有回调都发生在该线程上，并且必须在该线程上完成对 WebView2 的请求。  从另一个线程使用 WebView2 不安全。

唯一的例外是 `Content` 属性 `CoreWebView2WebResourceRequest` 。  从 `Content` 后台线程读取属性流。  该流应为敏捷流，或应该从后台 STA 创建，以防止 UI 线程的性能下降。

> [!NOTE]
> 对象属性是单线程的。  例如，从除 (之外的其他线程调用将成功，即返回 `CoreWebView2CookieManager.GetCookiesAsync(null)` cookie) ;但是，在此类调用之后尝试访问 cookie 的属性 (如) 将引发 `Main` `c.Domain` 异常。


<!-- ====================================================================== -->
## <a name="reentrancy"></a>Reentrancy

回调（包括事件处理程序和完成处理程序）将串行运行。  运行事件处理程序并开始消息循环后，事件处理程序或完成回调将无法以重新进入的方式运行。  如果 WebView2 应用尝试在 WebView 事件处理程序内同步创建嵌套消息循环或模式 UI，则此方法将导致尝试重新运行。  WebView2 中不支持此类重新执行，并且会无限期地将事件处理程序留在堆栈中。

例如，不支持以下编码方法。

```csharp
private void Btn_Click(object sender, EventArgs e)
{
   // Post web message when button is clicked
   this.webView2Control.ExecuteScriptAsync("window.chrome.webview.postMessage(\"Open Dialog\");");
}

private void CoreWebView2_WebMessageReceived(object sender, CoreWebView2WebMessageReceivedEventArgs e)
{
   string msg = e.TryGetWebMessageAsString();
   if (msg == "Open Dialog")
   {
      Form1 form = new Form1(); // Create a new form that contains a new WebView when web message is received.
      form.ShowDialog(); // This will cause a reentrancy issue and cause the newly created WebView inside the modal dialog to hang.
   }
}
```

相反，请安排在事件处理程序完成后进行适当的工作，如以下代码所示。

```csharp
private void CoreWebView2_WebMessageReceived(object sender, CoreWebView2WebMessageReceivedEventArgs e)
{
   string msg = e.TryGetWebMessageAsString();
   if (msg == "Open Dialog")
   {
      // Show a modal dialog after the current event handler is completed, to avoid potential reentrancy caused by running a nested message loop in the WebView2 event handler.
      System.Threading.SynchronizationContext.Current.Post((_) => {
         Form1 form = new Form1();
         form.ShowDialog();
         form.Closed();
      }, null);
   }
}
```

> [!NOTE]
> 对于 WinForms 和 WPF 应用，若要获取用于调试的完全调用堆栈，你必须为 WebView2 应用启用本机代码调试，如下所示。
> 1.  在 WebView2 项目中打开Visual Studio。
> 1.  在 **"解决方案资源管理器**"中，右键单击"WebView2"项目，然后选择"属性 **"。**
> 1.  选择" **调试** "选项卡，然后选中" **启用本机代码调试"** 复选框，如下所示。

:::image type="complex" source="../media/webview-enable-native-debug.png" alt-text="在脚本中启用本机代码Visual Studio" lightbox="../media/webview-enable-native-debug.png":::
   在脚本中启用本机代码Visual Studio
:::image-end:::


<!-- ====================================================================== -->
## <a name="deferrals"></a>Deferrals

某些 WebView2 事件读取在相关事件参数上设置的值，或在事件处理程序完成后启动一些操作。  如果还需要运行异步操作（如事件处理程序），请对关联事件的事件参数 `GetDeferral` 使用 方法。  返回的对象可确保在请求 的 方法之前不会认为事件 `Deferral` `Complete` `Deferral` 处理程序已完成。

例如，事件处理程序完成后，可以使用 事件提供 以作为子 `NewWindowRequested` `CoreWebView2` 窗口进行连接。  但是，如果需要异步创建 ，应在 `CoreWebView2` 上 `GetDeferral` 调用 方法 `NewWindowRequestedEventArgs` 。  在 上异步创建 和 设置 属性后，对 方法返回的对象 `CoreWebView2` `NewWindow` 调用 `NewWindowRequestedEventArgs` `Complete` `Deferral` `GetDeferral` 。

### <a name="deferrals-in-c"></a>C 中的延迟#

在 `Deferral` C# 中时，最佳做法是使用它和 `using` 块。 `using`即使块 `Deferral` 中间抛出异常，块也可确保 完成 `using` 。 如果相反，你有代码可显式调用 ，但在调用发生前会引发异常，延迟将等到垃圾回收器最终收集和处理延迟后一段时间才会完成。 `Complete` `Complete` 在这期间，WebView2 将等待应用代码处理事件。

例如，不要执行以下操作，因为如果在调用 前出现异常，该事件不会被视为 `Complete` `WebResourceRequested` "handled"，并阻止 WebView2 呈现该 Web 内容。

```csharp
private async void WebView2WebResourceRequestedHandler(CoreWebView2 sender,
                           CoreWebView2WebResourceRequestedEventArgs eventArgs)
{
   var deferral = eventArgs.GetDeferral();

   args.Response = await CreateResponse(eventArgs);

   // Calling Complete is not recommended, because if CreateResponse
   // throws an exception, the deferral isn't completed.
   deferral.Complete();
}
```

请改为使用 `using` 块，如以下示例所示。 `using`块确保 `Deferral` 已完成，无论 是否有异常。

```csharp
private async void WebView2WebResourceRequestedHandler(CoreWebView2 sender,
                           CoreWebView2WebResourceRequestedEventArgs eventArgs)
{
   // The using block ensures that the deferral is completed, regardless of
   // whether there's an exception.
   using (eventArgs.GetDeferral())
   {
      args.Response = await CreateResponse(eventArgs);
   }
}
```


<!-- ====================================================================== -->
## <a name="block-the-ui-thread"></a>阻止 UI 线程

WebView2 依赖 UI 线程的消息处理器来运行事件处理程序回调和异步方法完成回调。  如果使用阻止消息发送的方法（如 或 ），则 WebView2 事件处理程序和 `Task.Result` `WaitForSingleObject` async-method 完成处理程序不会运行。  例如，以下代码无法完成，因为邮件在等待完成时停止 `Task.Result` 消息 `ExecuteScriptAsync` 等待等待。  由于阻止了消息拦截， `ExecuteScriptAsync` 无法完成 。

例如，下面的代码不起作用，因为它使用 `Task.Result` 。

```csharp
private void Button_Click(object sender, EventArgs e)
{
    string result = webView2Control.CoreWebView2.ExecuteScriptAsync("'test'").Result;
    MessageBox.Show(this, result, "Script Result");
}
```

请改为使用和 等异步机制，该机制不会阻止 `await` `async` `await` 消息的阻塞或 UI 线程。  例如：

```csharp
private async void Button_Click(object sender, EventArgs e)
{
    string result = await webView2Control.CoreWebView2.ExecuteScriptAsync("'test'");
    MessageBox.Show(this, result, "Script Result");
}
```


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebView2 入门指南](../index.md#get-started)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [WebView2 API 参考](/dotnet/api/microsoft.web.webview2.wpf.webview2)
*  [另请参阅](../index.md#see-also)- 在_WebView2 Microsoft Edge简介中_。
