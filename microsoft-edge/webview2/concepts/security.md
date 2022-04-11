---
title: 开发安全的 WebView2 应用
description: 如何开发安全的 WebView2 应用程序。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/14/2020
ms.openlocfilehash: 765b519e85e50286668fd3ee91e90c6b6b70e0c2
ms.sourcegitcommit: 5351b3950b3bb7bc698415a2e5608816f1f9fca4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2022
ms.locfileid: "12473799"
---
# <a name="develop-secure-webview2-apps"></a>开发安全的 WebView2 应用
<!-- old title: # Best practices for developing secure WebView2 applications -->

[WebView2 控件](../index.md)允许开发人员在本机应用程序中托管 Web 内容。  正确使用时，托管 Web 内容会提供多种优势，例如使用基于 Web 的 UI、访问 Web 平台的功能、跨平台共享代码等。  若要避免托管 Web 内容可能产生的漏洞，请确保设计 WebView2 应用程序以密切监视 Web 内容与主机应用程序之间的交互。

*  将所有 Web 内容视为不安全：

   *  在使用 Web 消息和主机对象参数之前验证它们，因为 Web 消息和参数可能在无意中或恶意)  (格式不正确，并可能导致应用行为意外。

   *  请始终检查在 WebView2 中运行的文档的来源，并评估内容的可信度。

*  设计特定的 Web 消息和主机对象交互，而不是使用泛型代理。

*  通过修改 [ICoreWebView2Settings (Win32) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings) 或 [CoreWebView2Settings (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)，设置以下选项以限制 Web 内容功能：

   *  如果不希望 Web 内容访问主机对象，请将其设置 `AreHostObjectsAllowed` 为 `false`”

   *  `false`如果不希望 Web 内容将 Web 消息发布到本机应用程序，请将其设置`IsWebMessageEnabled`为”

   *  `false`如果不希望 Web 内容运行脚本，则设置`IsScriptEnabled`为 (例如，在显示静态 HTML 内容) 时。

   *  如果不希望 Web 内容显示`alert`或`prompt`对话框，请设置`AreDefaultScriptDialogsEnabled`为`false`”

*  根据新页面的来源更新设置：

   *  若要防止应用程序导航到某些页面，请使用 `NavigationStarting` 和 `FrameNavigationStarting` 事件检查页面或帧导航，然后有条件地阻止导航。

   *  导航到新页面时，可能需要根据前面所述调整 [ICoreWebView2Settings (Win32) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings) 或 [CoreWebView2Settings (.NET) ](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)上的属性值。

*  导航到新文档时，请使用该 `ContentLoading` 事件并 `RemoveHostObjectFromScript` 删除公开的主机对象。

*  WebView2 不能作为系统用户运行。  此限制会阻止生成凭据提供程序等方案。


<!-- ====================================================================== -->
<!--
## Security

Always check the Source property of the WebView2 control before using `ExecuteScript`, `PostWebMessageAsJson`, `PostWebMessageAsString`, or any other method to send information into the WebView2 control. The WebView2 control may have navigated to another page via the end user interacting with the page or script in the page causing navigation. Similarly, be very careful with `AddScriptToExecuteOnDocumentCreated`. All future `navigations` run the same script and if it provides access to information intended only for a certain origin, any HTML document may have access.

When examining the result of an `ExecuteScript` method call, a `WebMessageReceived` event, always check the Source of the sender, or any other mechanism of receiving information from an HTML document in a WebView2 control validate the URI of the HTML document is what you expect.

When constructing a message to send into a WebView2 control, prefer using `PostWebMessageAsJson` and construct the JSON string parameter using a JSON library. This avoids any potential accidents of encoding information into a JSON string or script and ensure no attacker controlled input can modify the rest of the JSON message or run arbitrary script. -->
