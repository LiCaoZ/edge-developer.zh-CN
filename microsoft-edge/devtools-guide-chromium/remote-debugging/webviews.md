---
title: 远程调试 Android WebViews
description: 使用 DevTools 在本机 Android 应用中远程调试 WebView Microsoft Edge入门。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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

使用开发人员工具在本机 Android 应用中Microsoft Edge Android WebView。

在 Android 4.4 (KitKat) 或更高版本上，使用 DevTools 调试本机 Android 应用中的 WebView 内容。

### <a name="summary"></a>摘要

*  在本机 Android 应用中打开 Android WebView 调试;在 DevTools Microsoft Edge Android WebViews。
*  若要显示启用调试的 Android WebView 列表，请转到 `edge://inspect`。
*  使用通过远程调试调试网页的相同方式调试 Android [WebView。](./index.md)


<!-- ====================================================================== -->
## <a name="configure-android-webviews-to-debug"></a>将 Android WebViews 配置为调试

必须在你的应用中打开 Android WebView 调试。  若要启用 Android WebView 调试，请对类运行 [setWebContentsDebuggingEnabled](https://developer.android.com/reference/android/webkit/WebView.html#setWebContentsDebuggingEnabled(boolean)) 静态 `WebView` 方法。

```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
    WebView.setWebContentsDebuggingEnabled(true);
}
```

该设置适用于应用的所有 Android WebView。

> [!TIP]
> Android WebView 调试不受应用 `debuggable` 清单中标志状态的影响。  如果你希望仅在标志为 时启用 Android WebView `debuggable` 调试 `true`，请在运行时测试标志。
>
> ```java
> if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
>     if (0 != (getApplicationInfo().flags & ApplicationInfo.FLAG_DEBUGGABLE))
>    { WebView.setWebContentsDebuggingEnabled(true); }
> }
> ```


<!-- ====================================================================== -->
## <a name="open-an-android-webview-in-devtools"></a>在 DevTools 中打开 Android WebView

若要显示 Android WebView 列表，并打开在设备上运行的调试功能，请转到 `edge://inspect`。

若要开始调试，请在要调试的 Android WebView 下，单击"检查 **"**。  使用 DevTools 的方式与使用远程浏览器选项卡的方式相同。

<!--
:::image type="content" source=".images/webview-debugging.msft.png" alt-text="Inspecting elements in an Android WebView." lightbox=".images/webview-debugging.msft.png":::

The gray graphics listed with the Android WebView represent its size and position relative to the screen of the device.  If your Android WebViews have titles set, the titles are listed as well.
-->


<!-- ====================================================================== -->
## <a name="troubleshoot"></a>疑难解答

如果你的 Android WebView 未显示在页面上 `edge://inspect` ：

*  验证已针对你的应用打开 Android WebView 调试。

*  在你的设备上，使用你想要调试的 Android WebView 打开应用。  然后，刷新 `edge://inspect`。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](http://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/webviews) 由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](http://creativecommons.org/licenses/by/4.0)获得许可。
