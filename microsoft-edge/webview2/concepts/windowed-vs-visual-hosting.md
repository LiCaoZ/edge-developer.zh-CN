---
title: Windowsed 与 WebView2 的视觉托管
description: 决定是否让应用使用窗口托管与 WebView2 控件的视觉托管。  在窗口化或可视化环境中托管 WebView2。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/24/2022
ms.openlocfilehash: 56d4ab2946b107f1bb27bb278e07c8c3bf2a3027
ms.sourcegitcommit: 42587f4e556d04c2052eae35dfdd91de8ad8645f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2022
ms.locfileid: "12821300"
---
# <a name="windowed-vs-visual-hosting-of-webview2"></a>Windowsed 与 WebView2 的视觉托管

在应用中托管 Microsoft Edge WebView2 控件有两个选项：窗口托管和视觉对象托管。

如果使用窗口式托管，这是大多数应用的良好起点，则无需阅读本文。  若要 (UX) 提供更自定义的用户体验，并且想要使用可视托管，请阅读本文。

| 方法 | 描述 | 针对 |
|---|---|---|
| 窗口托管 | WebView2 控件从操作系统 (操作系统) 获取输入。  OS 将输入发送到 WebView2。 | 快速轻松地显示 Web 内容，而无需包含输入、输出和辅助功能的功能。 |
| 视觉托管 | 主机应用从用户获取空间输入 (，例如鼠标或触摸输入) 。  应用将此输入发送到 WebView2 控件。 | 更精细地控制布局。  例如，可以控制 WebView2 控件在页面中的定位。  应用需要对窗口管理和呈现 API 进行特定的处理。 |

这些方法有不同的要求、约束和优势。  与视觉托管相比，窗口托管的实现更简单。  视觉托管需要窗口托管所需的所有 API 调用，并且视觉托管对它正确呈现有额外的要求。  API 调用列在 [窗口托管](#windowed-hosting) 和 [视觉对象托管](#visual-hosting)中，如下所示。


<!-- ====================================================================== -->
## <a name="scenarios-for-selecting-the-hosting-approach"></a>选择托管方法的方案

在应用中托管 WebView2 控件的这两种方法在功能上是相似的，但它们符合不同的需求，具体取决于应用要求。


#### <a name="windowed-hosting-for-displaying-content-quickly-and-easily"></a>窗口托管：用于快速轻松地显示内容

“Windowed”表示在应用中，HWND 从操作系统继承许多默认属性。

在某些情况下，你可能希望在应用中尽可能快速、轻松地集中显示 Web 内容。  窗口托管允许解决方案快速显示 Web 内容，而无需包含输入、输出和辅助功能的功能。


#### <a name="visual-hosting-for-more-granular-control-over-layout"></a>视觉托管：为更精细地控制布局

视觉托管允许 (，并且需要) 更精细的布局控制。  使用此方法时，应用需要特定的窗口管理和呈现 API 处理。

例如，使用视觉托管时，必须选择用户调整窗口大小时，Web 视图与整个页面的缩放方式（例如，如果希望 Web 视图的缩放是应用的两倍）。


<!-- ====================================================================== -->
## <a name="compatibility-and-constraints"></a>兼容性和约束

关键兼容性限制包括操作系统以及框架和非框架应用中的呈现。


<!-- ------------------------------ -->
#### <a name="operating-systems"></a>操作系统

Windows 7 和Windows 8只能执行窗口托管，而不能执行视觉对象托管。


<!-- ------------------------------ -->
#### <a name="rendering-webview2-in-framework-and-non-framework-apps"></a>在框架和非框架应用中呈现 WebView2

如果使用的是应用的 UI 框架，则应对该 UI 框架使用相应的 WebView2 元素。  如果不对应用使用 UI 框架， (如 Win32 或 React Native) ，或者 UI 框架没有 WebView2 元素，则需要创建`CoreWebView2Controller`该框架并将其呈现到所需的应用中。

**注意：** 如果应用的 UI 是使用 `DirectComposition` 或 `Windows.UI.Composition`生成的，则应使用 `CoreWebView2CompositionController`，否则应使用 `CoreWebView2Controller`。

属性 `CoreWebView2Controller` 和方法：

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.CoreWebView2 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.corewebview2)
* [CoreWebView2Controller.Close 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.close)
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2controllerasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.CoreWebView2 属性](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_corewebview2)
* [CoreWebView2Controller.Close 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#close)
* [CoreWebView2Environment.CreateCoreWebView2ControllerAsync 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2controllerasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：CoreWebView2 属性](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_corewebview2)<!--no put-->
* [ICoreWebView2Controller：：Close 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#close)
* [ICoreWebView2Environment：：CreateCoreWebView2Controller 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment#createcorewebview2controller)

---


<!-- ====================================================================== -->
## <a name="windowed-hosting"></a>窗口托管

窗口托管可描述为存储信息的 HWND。  应用中可以有多个 HWND，每个 HWND 将用作 WebView 组件来访问 Web 内容。  某些输出/输入命令由所选框架处理;但是，仍需要处理窗口管理。

窗口托管的优点包括：

* 缩放和光栅化缩放 (例如，菜单、上下文菜单等) 也会自动缩放到应用的父级 `HWND`。 它还处理 WebView 在到达最终元素时如何管理专注和自选选项卡。

* 应用在 WebView 中处理键盘快捷方式和键盘快捷方式。 例如，`Ctrl+C`在 WebView 中，你将知道您正在尝试在 WebView 中复制内容，而不是按下和`C`单独进行`Ctrl`复制。

* 无需管理各种基于合成的呈现 (，例如，如果不想，则输入、输出和辅助功能控件) 。

有关窗口管理和功能的 `HWND` 一般信息， [请参阅关于 Windows](/windows/win32/winmsg/about-windows)。


<!-- ------------------------------ -->
#### <a name="window-management"></a>窗口管理

窗口管理的以下方面在窗口托管环境中进行处理。


<!-- ---------- -->
###### <a name="sizing-positioning-and-visibility"></a>调整大小、定位和可见性

`CoreWebView2Controller` 采用父 `HWND`级。  相对 `Bounds` 于父 `HWND`级的属性大小和位置 WebView2。  可以通过使用 `IsVisible`来切换 WebView2 的可见性。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.Bounds 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.bounds#microsoft-web-webview2-core-corewebview2controller-bounds)
* [CoreWebView2Controller.IsVisible 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.isvisible)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.Bounds 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#bounds)
* [CoreWebView2Controller.IsVisible 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#isvisible)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：Bounds 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_bounds)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_bounds)
* [ICoreWebView2Controller：：IsVisible 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_isvisible)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_isvisible)

---


<!-- ---------- -->
###### <a name="zooming"></a>缩放

WebView2 `ZoomFactor` 用于仅缩放 Web 内容。  当用户通过 `Ctrl` + 鼠标轮缩放内容时，也会更新此功能。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.ZoomFactor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.zoomfactor#microsoft-web-webview2-core-corewebview2controller-zoomfactor)
* [CoreWebView2Controller.ZoomFactorChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.zoomfactorchanged)
* [CoreWebView2Controller.SetBoundsAndZoomFactor 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.setboundsandzoomfactor)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.ZoomFactor 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#zoomfactor)
* [CoreWebView2Controller.ZoomFactorChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#zoomfactorchanged)
* [CoreWebView2Controller.SetBoundsAndZoomFactor 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#setboundsandzoomfactor)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：ZoomFactor 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_zoomfactor)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_zoomfactor)
* [ICoreWebView2Controller：：ZoomFactorChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_zoomfactorchanged)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_zoomfactorchanged)
* [ICoreWebView2Controller：：SetBoundsAndZoomFactor 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#setboundsandzoomfactor)

---


<!-- ------------------------------ -->
#### <a name="rasterization-scale"></a>光栅化规模

API `RasterizationScale` 缩放所有 WebView2 UI，包括上下文菜单、工具提示和弹出窗口。  应用可以设置 WebView2 是否应检测监视器规模更改并自动更新。`RasterizationScale`  `BoundsMode` 用于配置属性是 `Bounds` 解释为原始像素，还是将需要由 `RasterizationScale`) 缩放的 DIP (。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.BoundsMode 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.boundsmode#microsoft-web-webview2-core-corewebview2controller-boundsmode)
  * [CoreWebView2BoundsMode 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2boundsmode)
* [CoreWebView2Controller.RasterizationScale 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.rasterizationscale)
* [CoreWebView2Controller.RasterizationScaleChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.rasterizationscalechanged)
* [CoreWebView2Controller.ShouldDetectMonitorScaleChanges 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.shoulddetectmonitorscalechanges)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.BoundsMode 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#boundsmode)
  * [CoreWebView2BoundsMode 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2boundsmode)
* [CoreWebView2Controller.RasterizationScale 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#rasterizationscale)
* [CoreWebView2Controller.RasterizationScaleChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#rasterizationscalechanged)
* [CoreWebView2Controller.ShouldDetectMonitorScaleChanges 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#shoulddetectmonitorscalechanges)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：BoundsMode 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller#get_bounds)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#put_bounds)
  * [COREWEBVIEW2_BOUNDS_MODE枚举](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_bounds_mode)
* [ICoreWebView2Controller：：RasterizationScale 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#get_rasterizationscale)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#put_rasterizationscale)
* [ICoreWebView2Controller：：RasterizationScaleChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#add_rasterizationscalechanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#remove_rasterizationscalechanged)
* [ICoreWebView2Controller：：ShouldDetectMonitorScaleChanges 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#get_shoulddetectmonitorscalechanges)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller3#put_rasterizationscale)

---


<!-- ---------- -->
###### <a name="focus-and-tabbing"></a>焦点和制表

WebView2 引发事件，让应用知道何时获得或失去焦点。  对于选项卡，有一个要将焦点移到 WebView2 的 API，还有一个 WebView2 事件，用于请求应用重新获取焦点。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.MoveFocus 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.movefocus)
  * [CoreWebView2MoveFocusReason 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2movefocusreason)
* [CoreWebView2Controller.MoveFocusRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.movefocusrequested)
  * [CoreWebView2MoveFocusRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2movefocusrequestedeventargs)
* [CoreWebView2Controller.GotFocus 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.gotfocus)
* [CoreWebView2Controller.LostFocus 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.lostfocus)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.MoveFocus 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#movefocus)
  * [CoreWebView2MoveFocusReason 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2movefocusreason)
* [CoreWebView2Controller.MoveFocusRequested 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#movefocusrequested)
  * [CoreWebView2MoveFocusRequestedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2movefocusrequestedeventargs)
* [CoreWebView2Controller.GotFocus 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#gotfocus)
* [CoreWebView2Controller.LostFocus 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#lostfocus)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：MoveFocus 方法](/microsoft-edge/webview2/reference/win32/icorewebview2controller#movefocus)
  * [COREWEBVIEW2_MOVE_FOCUS_REASON枚举](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_move_focus_reason)
* [ICoreWebView2Controller：：MoveFocusRequested 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_movefocusrequested)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_movefocusrequested)
  * [ICoreWebView2MoveFocusRequestedEventArgs 接口](/microsoft-edge/webview2/reference/win32/icorewebview2movefocusrequestedeventargs)
* [ICoreWebView2Controller：：GotFocus 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_gotfocus)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_gotfocus)
* [ICoreWebView2Controller：：LostFocus 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_lostfocus)， [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_lostfocus)

---


<!-- ---------- -->
###### <a name="parent-window"></a>父窗口

WebView2 可以重新父级为其他父 `HWND`级。 当应用在屏幕上的位置发生更改时，还需要通知 WebView2。


##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.NotifyParentWindowPositionChanged 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.notifyparentwindowpositionchanged)
* [CoreWebView2Controller.ParentWindow 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.notifyparentwindowpositionchanged)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.NotifyParentWindowPositionChanged 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.notifyparentwindowpositionchanged)
* [CoreWebView2Controller.ParentWindow 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.parentwindow)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：：NotifyParentWindowPositionChanged 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#notifyparentwindowpositionchanged)
* [ICoreWebView2Controller：:P arentWindow 属性 (获取) ](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2controller#parentwindow)<!--no put-->

---


<!-- ---------- -->
###### <a name="keyboard-accelerators"></a>键盘加速键

当 WebView2 具有焦点时，它会直接从用户接收输入。 应用可能想要截获和处理某些加速器键组合，或禁用正常的浏览器加速器键行为。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.arebrowseracceleratorkeysenabled)
* [CoreWebView2Controller.AcceleratorKeyPressed 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.acceleratorkeypressed)
  * [CoreWebView2AcceleratorKeyPressedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2acceleratorkeypressedeventargs)
  * [CoreWebView2KeyEventKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2keyeventkind)
  * [CoreWebView2PhysicalKeyStatus 结构](/dotnet/api/microsoft.web.webview2.core.corewebview2physicalkeystatus)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Settings.AreBrowserAcceleratorKeysEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.arebrowseracceleratorkeysenabled)
* [CoreWebView2Controller.AcceleratorKeyPressed 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.acceleratorkeypressed)
  * [CoreWebView2AcceleratorKeyPressedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2acceleratorkeypressedeventargs)
  * [CoreWebView2KeyEventKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2keyeventkind)
  * [CoreWebView2PhysicalKeyStatus 结构](/dotnet/api/microsoft.web.webview2.core.corewebview2physicalkeystatus)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Settings：：AreBrowserAcceleratorKeysEnabled 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings3#get_arebrowseracceleratorkeysenabled)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings3#put_arebrowseracceleratorkeysenabled)
* [ICoreWebView2Controller：：AcceleratorKeyPressed 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2controller#add_acceleratorkeypressed)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller#remove_acceleratorkeypressed)
  * [ICoreWebView2AcceleratorKeyPressedEventArgs 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2acceleratorkeypressedeventargs)
  * [ICoreWebView2KeyEventKind 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2keyeventkind)
  * [ICoreWebView2PhysicalKeyStatus 结构](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2physicalkeystatus)

---


<!-- ---------- -->
###### <a name="default-background-color"></a>默认背景色

WebView2 可以指定默认背景色。 这可以是任何不透明的颜色或透明颜色。 如果网页未设置自己的背景色，将使用此颜色。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2Controller.DefaultBackgroundColor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.defaultbackgroundcolor)
  * [CoreWebView2Color 结构](/dotnet/api/microsoft.web.webview2.core.corewebview2color)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2Controller.DefaultBackgroundColor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2controller.defaultbackgroundcolor#microsoft-web-webview2-core-corewebview2controller-defaultbackgroundcolor)
  * [CoreWebView2Color 结构](/dotnet/api/microsoft.web.webview2.core.corewebview2color)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2Controller：:D efaultBackgroundColor 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2controller2#get_defaultbackgroundcolor)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2controller2#put_defaultbackgroundcolor)
  * [COREWEBVIEW2_COLOR结构](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_color)

---


<!-- ====================================================================== -->
## <a name="visual-hosting"></a>视觉托管

在视觉托管中，内容嵌入到应用程序上的给定位置。 当用户与应用程序交互时，此位置必须处理内容在应用中的缩放和行为方式。  除了为窗口托管描述的窗口管理外，视觉对象托管还需要应用在收到任何用户交互时管理基于合成的呈现。  有关视觉对象托管的详细信息，请参阅 [在桌面应用中使用视觉对象层](/windows/apps/desktop/modernize/visual-layer-in-desktop-apps)。

如果 WebView2 应用使用可视托管：

* 输入将路由到应用， `HWND` 并且必须配置为发送空间输入 (例如，鼠标、触摸和笔) 基于位置， _而不是_ 当前具有焦点的内容，例如键盘。

在视觉托管环境中配置 WebView2 时，可以使用以下 API：


<!-- ------------------------------ -->
#### <a name="composition-based-rendering"></a>基于合成的呈现

对于基于合成的 WebView2 呈现，请使用它 `CoreWebView2Environment` 来创建一个 `CoreWebView2CompositionController`。 实现 `CoreWebView2CompositionController` 所有 API， `CoreWebView2Controller`但包括特定于基于合成的呈现的其他 API。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController 类](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2compositioncontrollerasync)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController 类](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller)
* [CoreWebView2Environment.CreateCoreWebView2CompositionControllerAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2compositioncontrollerasync)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController 接口](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller)
* [ICoreWebView2Environment：：CreateCoreWebView2CompositionController 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment3#createcorewebview2compositioncontroller)

---


<!-- ------------------------------ -->
#### <a name="output"></a>输出

WebView2 可以将其合成树连接到或`IDCompositionTarget``Windows::UI::Composition::ContainerVisual`连接到 `IDCompositionVisual`。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.RootVisualTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.rootvisualtarget)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController.RootVisualTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.rootvisualtarget)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController：：RootVisualTarget 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_rootvisualtarget)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#put_rootvisualtarget)

---


<!-- ------------------------------ -->
#### <a name="input"></a>输入

应用接收鼠标、触摸或笔等空间输入，必须发送到 WebView2。 WebView2 会在光标应根据输入设备的位置进行更新时通知应用。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2CompositionController.Cursor 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.cursor)
* [CoreWebView2CompositionController.CursorChanged 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.cursorchanged)
* [CoreWebView2CompositionController.SystemCursorId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.systemcursorid)
* [CoreWebView2CompositionController.SendMouseInput 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.sendmouseinput)
  * [CoreWebView2MouseEventKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2mouseeventkind)
  * [CoreWebView2MouseEventVirtualKeys 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2mouseeventvirtualkeys)
* [CoreWebView2CompositionController.SendPointerInput 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2compositioncontroller.sendpointerinput)
  * [CoreWebView2PointerEventKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2pointereventkind)
* [CoreWebView2Environment.CreateCoreWebView2PointerInfo 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcorewebview2pointerinfo)
  * [CoreWebView2PointerInfo 类](/dotnet/api/microsoft.web.webview2.core.corewebview2pointerinfo)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2CompositionController.Cursor 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#cursor)
* [CoreWebView2CompositionController.CursorChanged 事件](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#cursorchanged)
* [CoreWebView2CompositionController.SendMouseInput 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#sendmouseinput)
  * [CoreWebView2MouseEventKind 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2mouseeventkind)
  * [CoreWebView2MouseEventVirtualKeys 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2mouseeventvirtualkeys)
* [CoreWebView2CompositionController.SendPointerInput 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2compositioncontroller#sendpointerinput)
  * [CoreWebView2PointerEventKind 枚举](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2mouseeventkind)
* [CoreWebView2Environment.CreateCoreWebView2PointerInfo 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#createcorewebview2pointerinfo)
  * [CoreWebView2PointerInfo 类](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2pointerinfo)

<!--TODO - not found, omitted:
* `CoreWebView2CompositionController.SystemCursorId` Property-->

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController：：Cursor 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_cursor)<!--no put-->
* [ICoreWebView2CompositionController：：CursorChanged 事件 (添加](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#add_cursorchanged)、 [删除) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#remove_cursorchanged)
* [ICoreWebView2CompositionController：：SystemCursorId 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#get_systemcursorid)<!--no put-->
* [ICoreWebView2CompositionController：：SendMouseInput 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#sendmouseinput)
  * [COREWEBVIEW2_MOUSE_EVENT_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_mouse_event_kind)
  * [COREWEBVIEW2_MOUSE_EVENT_VIRTUAL_KEYS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_mouse_event_virtual_keys)
* [ICoreWebView2CompositionController：：SendPointerInput 方法](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller#sendpointerinput)
  * [COREWEBVIEW2_POINTER_EVENT_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_pointer_event_kind)
* [ICoreWebView2Environment：：CreateCoreWebView2PointerInfo 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment3#createcorewebview2pointerinfo)
  * [ICoreWebView2PointerInfo 接口](/microsoft-edge/webview2/reference/win32/icorewebview2pointerinfo)

---


<!-- ------------------------------ -->
#### <a name="accessibility"></a>辅助功能

默认情况下，WebView2 将作为父 `HWND`级的子级显示在辅助功能树中。  WebView2 提供了一个 API，用于更好地定位相对于应用中其他元素的 WebView2 内容。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

不适用。

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

不适用。

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2CompositionController：：AutomationProvider 属性 (获取) ](/microsoft-edge/webview2/reference/win32/icorewebview2compositioncontroller2#get_automationprovider)<!--no put-->
* [ICoreWebView2Environment：：GetAutomationProviderForWindow 方法](/microsoft-edge/webview2/reference/win32/icorewebview2environment4#getautomationproviderforwindow)

---


<!-- ====================================================================== -->
<!-- ## See also -->

<!--
* []()
-->
