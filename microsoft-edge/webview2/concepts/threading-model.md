---
description: 在 WebView2 线程模型中，必须在具有消息等待的 UI 线程上创建 WebView2。
title: WebView2 的线程模型
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/28/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、wpf 应用、wpf、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: fdedb23f3398d0ee6b19cdcea309f48d3d284cd1
ms.sourcegitcommit: 57f52b3edb34b8eb5389b746ff0970f7fd3b9a82
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2021
ms.locfileid: "11710674"
---
# <a name="threading-model-for-webview2"></a>WebView2 的线程模型

:::row:::
   :::column span="1":::
      支持的平台：
   :::column-end:::
   :::column span="2":::
      Win32、Windows Forms、WinUi、WPF
   :::column-end:::
:::row-end:::  

WebView2 控件基于组件对象模型 [ (COM) ][WindowsWin32ComTheComponentObjectModel] 并且必须在单个线程的 Sta (STA [) ][WindowsWin32ComSingleThreadedApartments] 上运行。  

## <a name="thread-safety"></a>线程安全  

WebView2 必须在使用消息线索的 UI 线程上创建。  所有回调都发生在该线程上，并且必须在该线程上完成对 WebView2 的请求。  从另一个线程使用 WebView2 不安全。  

唯一的例外是 `Content` 属性 `CoreWebView2WebResourceRequest` 。  从 `Content` 后台线程读取属性流。  该流应为敏捷流，或应该从后台 STA 创建，以防止 UI 线程的性能下降。  

## <a name="re-entrancy"></a>重新entrancy  

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

相反，应安排在事件处理程序完成后进行适当的工作，如以下代码所示。

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

## <a name="deferrals"></a>Deferrals  

某些 WebView2 事件读取在相关事件参数上设置的值，或在事件处理程序完成后启动一些操作。  如果还需要运行异步操作（如事件处理程序），请对关联事件的事件参数 `GetDeferral` 使用 方法。  返回的对象可确保在请求 的 方法之前不会认为事件 `Deferral` `Complete` `Deferral` 处理程序已完成。  

例如，可以使用 事件在事件处理程序完成时提供 作为子 `NewWindowRequested` `CoreWebView2` 窗口进行连接的 。  但是，如果需要异步创建 ，应在 `CoreWebView2` 上 `GetDeferral` 请求 方法 `NewWindowRequestedEventArgs` 。  在 异步创建 后，在 上设置 属性，该方法返回的对象上的 `CoreWebView2` `NewWindow` `NewWindowRequestedEventArgs` `Complete` `Deferral` `GetDeferral` 请求。  

## <a name="block-the-ui-thread"></a>阻止 UI 线程  

WebView2 依赖 UI 线程的消息处理器来运行事件处理程序回调和异步方法完成回调。  如果使用阻止消息发送的方法（如 或 ），则 WebView2 事件处理程序和 `Task.Result` `WaitForSingleObject` async-method 完成处理程序不会运行。  例如，以下代码无法完成，因为邮件在等待完成时 `Task.Result` 停止消息 `ExecuteScriptAsync` 等待。  由于阻止了消息拦截， `ExecuteScriptAsync` 无法完成 。

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

## <a name="see-also"></a>另请参阅  

*   若要开始使用 WebView2，请导航到["WebView2 入门指南"。][Webview2IndexGetStarted]  
*   有关 WebView2 功能的综合示例，请导航到[webView2Samples][GithubMicrosoftedgeWebview2samples]存储库GitHub。  
*   有关 WebView2 API 的更多详细信息，请导航到 [API 参考][DotnetApiMicrosoftWebWebview2WpfWebview2]。  
*   有关 WebView2 的信息，请导航到["WebView2 资源"。][Webview2IndexNextSteps]  

## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>联系 Microsoft Edge WebView 团队  

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]  

<!-- links -->  
[Webview2IndexGetStarted]: ../index.md#get-started "入门 - WebView2 Microsoft Edge简介|Microsoft Docs"  
[Webview2IndexNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 |Microsoft Docs"  
<!-- external links -->
[DotnetApiMicrosoftWebWebview2WpfWebview2]: /dotnet/api/microsoft.web.webview2.wpf.webview2 "WebView2 类|Microsoft Docs"  

[WindowsWin32ComSingleThreadedApartments]: /windows/win32/com/single-threaded-apartments "单线程处理|Microsoft Docs"  
[WindowsWin32ComTheComponentObjectModel]: /windows/win32/com/the-component-object-model "组件对象模型|Microsoft Docs"  

[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"  
