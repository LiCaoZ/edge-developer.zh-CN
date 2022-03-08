---
title: 开发安全的 WebView2 应用
description: 如何开发安全的 WebView2 应用程序。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/14/2020
ms.openlocfilehash: a704bf3a0ab58623e36758b15433dbb7f96cfa1f
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432283"
---
# <a name="develop-secure-webview2-apps"></a>开发安全的 WebView2 应用
<!-- old title: # Best practices for developing secure WebView2 applications -->

[WebView2 控件允许](../index.md)开发人员在本机应用程序中承载 Web 内容。  正确使用时，承载 Web 内容具有多项优势，例如使用基于 Web 的 UI、访问 Web 平台的功能、跨平台共享代码等。  为了避免承载 Web 内容时可能出现的漏洞，请确保设计 WebView2 应用程序以密切监视 Web 内容和主机应用程序之间的交互。

*  将所有 Web 内容视为不安全：

   *  使用 Web 消息和主机对象参数之前验证它们，因为 Web 消息和参数可能格式不正确 (无意或恶意) 并可能导致应用发生意外行为。

   *  始终检查在 WebView2 内运行的文档的来源，并评估内容可信度。

*  设计特定的 Web 消息和主机对象交互，而不是使用泛型代理。

*  设置以下选项以通过修改 [ICoreWebView2Settings (Win32) 或 ](/microsoft-edge/webview2/reference/win32/icorewebview2settings) [CoreWebView2Settings (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)来限制 Web 内容功能：

   *  `false`如果`AreHostObjectsAllowed`不希望 Web 内容访问主机对象，则设置为 。

   *  `false`如果`IsWebMessageEnabled`不希望 Web 内容向本机应用程序发布 Web 消息，请设置为 。

   *  `false`设置为 `IsScriptEnabled` ，如果您不希望 Web 内容运行脚本， (，例如，在显示静态 HTML 内容) 。

   *  如果`AreDefaultScriptDialogsEnabled`不希望显示 Web 内容或对话框，则设置为 `alert` `prompt` 。`false`

*  根据新页面的来源更新设置：

   *  若要阻止应用程序导航到特定页面 `NavigationStarting` ，请使用 和 `FrameNavigationStarting` 事件检查页面或框架导航，然后有条件地阻止导航。

   *  导航到新页面时，你可能需要调整 [ICoreWebView2Settings (Win32) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings) 或 [CoreWebView2Settings (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)上的属性值，如前面所述。

*  导航到新文档时，请使用 `ContentLoading` 事件并 `RemoveHostObjectFromScript` 删除公开的主机对象。

*  WebView2 无法作为系统用户运行。  此限制可阻止构建凭据提供程序等方案。


<!-- ====================================================================== -->
<!--
## Security

Always check the Source property of the WebView before using `ExecuteScript`, `PostWebMessageAsJson`, `PostWebMessageAsString`, or any other method to send information into the WebView. The WebView may have navigated to another page via the end user interacting with the page or script in the page causing navigation. Similarly, be very careful with `AddScriptToExecuteOnDocumentCreated`. All future `navigations` run the same script and if it provides access to information intended only for a certain origin, any HTML document may have access.

When examining the result of an `ExecuteScript` method call, a `WebMessageReceived` event, always check the Source of the sender, or any other mechanism of receiving information from an HTML document in a WebView validate the URI of the HTML document is what you expect.

When constructing a message to send into a WebView, prefer using `PostWebMessageAsJson` and construct the JSON string parameter using a JSON library. This avoids any potential accidents of encoding information into a JSON string or script and ensure no attacker controlled input can modify the rest of the JSON message or run arbitrary script. -->
