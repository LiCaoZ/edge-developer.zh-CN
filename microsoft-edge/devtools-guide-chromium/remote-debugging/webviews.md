---
title: 远程调试 Android WebViews
description: 开始使用 Microsoft Edge DevTools 在本机 Android 应用中远程调试 WebView。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 78d0731c1d931c19c21dca5a8c94ad1ad742def6
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631379"
---
<!-- Copyright Meggin Kearney

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="remotely-debug-android-webviews"></a>远程调试 Android WebViews

使用 Microsoft Edge 开发人员工具在本机 Android 应用中调试 Android WebViews。

在 Android 4.4 (KitKat) 或更高版本上，使用 DevTools 调试本机 Android 应用中的 WebView 内容。

Android WebView 与 [Microsoft Edge WebView2](../../webview2/index.md) 无关。


### <a name="summary"></a>摘要

*  在本机 Android 应用中启用 Android WebView 调试;在 Microsoft Edge DevTools 中调试 Android WebViews。
*  若要显示启用调试的 Android WebViews 列表，请转到 `edge://inspect`。
*  调试 Android WebView 的方式与通过 [远程调试调试](index.md)网页的方式相同。


<!-- ====================================================================== -->
## <a name="configure-android-webviews-to-debug"></a>将 Android WebView 配置为调试

必须在应用中启用 Android WebView 调试。  若要启用 Android WebView 调试，请在类上`WebView`运行 [setWebContentsDebuggingEnabled](https://developer.android.com/reference/android/webkit/WebView.html#setWebContentsDebuggingEnabled(boolean)) 静态方法。

```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
    WebView.setWebContentsDebuggingEnabled(true);
}
```

此设置适用于应用的所有 Android WebView。

> [!TIP]
> Android WebView 调试不受应用清单中标志状态 `debuggable` 的影响。  如果只想在标志`true`为标志时`debuggable`启用 Android WebView 调试，请在运行时测试该标志。
>
> ```java
> if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
>     if (0 != (getApplicationInfo().flags & ApplicationInfo.FLAG_DEBUGGABLE))
>    { WebView.setWebContentsDebuggingEnabled(true); }
> }
> ```


<!-- ====================================================================== -->
## <a name="open-an-android-webview-in-devtools"></a>在 DevTools 中打开 Android WebView

若要在设备上显示启用调试的 Android WebViews 列表，请转到 `edge://inspect`。

若要开始调试，请在要调试的 Android WebView 下单击 **“检查**”。  使用 DevTools 的方式与使用远程浏览器选项卡的方式相同。

<!--
![Inspecting elements in an Android WebView.](.images/webview-debugging.msft.png)

The gray graphics listed with the Android WebView represent its size and position relative to the screen of the device.  If your Android WebViews have titles set, the titles are listed as well.
-->


<!-- ====================================================================== -->
## <a name="troubleshoot"></a>疑难解答

如果 Android WebView 未显示在页面上 `edge://inspect` ：

*  验证应用是否已启用 Android WebView 调试。

*  在设备上，使用要调试的 Android WebView 打开应用。  然后，刷新 `edge://inspect`。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](http://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在此](https://developer.chrome.com/docs/devtools/remote-debugging/webviews/) 处找到，由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 创作。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](http://creativecommons.org/licenses/by/4.0)获得许可。
