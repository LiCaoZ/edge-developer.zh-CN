---
title: 模拟和测试其他浏览器
description: 你的作业不会以确保你的网站在 Android 和 Microsoft Edge运行结束。  尽管设备模式可以模拟一系列其他设备（如智能手机），但我们鼓励你查看由其他浏览器提供的模拟解决方案。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: f5b9e59fb917bd3e45339e825b7fddd810eedc2c
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12323745"
---
<!-- Copyright Meggin Kearney and Paul Bakaus

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="emulate-and-test-other-browsers"></a>模拟和测试其他浏览器

你的作业不会以确保你的网站在 Android 和 Microsoft Edge运行结束。  尽管 **设备模式** 可以模拟一系列其他设备（如智能手机），但我们鼓励你查看由其他浏览器提供的模拟解决方案。

### <a name="summary"></a>摘要

*   当你没有特定设备，或者想要对某些内容进行专线检查时，最好选择在浏览器内模拟该设备。
*   通过设备仿真器和模拟器，你可以从工作站模拟各种设备上的开发网站。
*   基于云的仿真器使你可以跨不同平台自动执行网站单元测试。


<!-- ====================================================================== -->
## <a name="browser-emulators"></a>浏览器仿真器

浏览器仿真器非常适用于测试网站的响应性。  但浏览器仿真器不会模拟 API、CSS 支持和某些仅在实际设备上移动浏览器上显示的行为的差异。  在真实设备上运行的浏览器上测试网站，确保一切按预期方式运行。

### <a name="firefox-responsive-design-view"></a>Firefox 响应式设计视图

Firefox 具有[](https://developer.mozilla.org/docs/Tools/Responsive_Design_View)响应式设计视图，鼓励您停止就特定设备进行思考，而是通过拖动窗口的边缘来浏览设计在常见屏幕大小或您自己的屏幕大小上的变化。

### <a name="edgehtml-emulation"></a>EdgeHTML 模拟

若要模拟Windows Phones，请使用 Microsoft Edge (EdgeHTML) [内置模拟](/archive/microsoft-edge/legacy/developer/devtools-guide/emulation)。

使用 [IE 11 模拟](/previous-versions/windows/internet-explorer/ie-developer/samples/dn255001(v=vs.85)) 模拟页面在早期版本的 Internet Explorer。


<!-- ====================================================================== -->
## <a name="device-emulators-and-simulators"></a>设备仿真器与模拟器

设备模拟器和仿真器不仅模拟浏览器环境，还模拟整个设备。  每个模拟器都可用于测试需要操作系统集成（如使用虚拟键盘的表单输入）的项。

### <a name="android-emulator"></a>Android 仿真器

<!--
:::image type="complex" source="../media/device-mode-android-emulator-stock-browser.msft.png" alt-text="Stock Browser in Android Emulator." lightbox="../media/device-mode-android-emulator-stock-browser.msft.png":::
   Stock Browser in Android Emulator
:::image-end:::
-->

目前，无法将 Microsoft Edge Android 仿真器上。  但是，您可以使用 Android 浏览器、Chromium命令行管理程序以及适用于 Android 的 Firefox，我们将在本文的稍后部分介绍这些内容。  Chromium内容命令行管理程序在Chromium引擎中运行Microsoft Edge，但不带特定于浏览器的功能。

Android 仿真器附带 Android SDK，你需要下载为 Android [Studio](https://developer.android.com/sdk/installing/studio.html)的一部分。  然后按照说明[设置虚拟设备并](https://developer.android.com/tools/devices/managing-avds.html)[启动仿真器](https://developer.android.com/tools/devices/emulator.html)。
启动仿真器后，选择 **浏览器图标，** 在适用于 Android 的旧股票浏览器上测试你的网站。

#### <a name="chromium-content-shell-on-android"></a>Chromium Android 上的内容 shell

<!--
:::image type="complex" source="../media/device-mode-android-avd-contentshell.msft.png" alt-text="Android Emulator Content Shell." lightbox="../media/device-mode-android-avd-contentshell.msft.png":::
   Android Emulator Content Shell
:::image-end:::
-->

若要安装适用于 Android Chromium命令行管理程序，请保持仿真器运行并运行以下命令：

```shell
git clone https://github.com/PaulKinlan/chromium-android-installer.git
chmod u+x ./chromium-android-installer/*.sh
./chromium-android-installer/install-chromeandroid.sh
```

现在，您可以使用内容命令行管理程序测试Chromium网站。

#### <a name="firefox-on-android"></a>Android 上的 Firefox

<!--
:::image type="complex" source="../media/device-mode-ff-on-android-emulator.msft.png" alt-text="Firefox Icon on Android Emulator." lightbox="../media/device-mode-ff-on-android-emulator.msft.png":::
   Firefox Icon on Android Emulator
:::image-end:::
-->

与内容Chromium类似，您可以获取 APK 以将 Firefox 安装到仿真器上。

[下载正确的 .apk 文件](https://www.mozilla.org/firefox/all/#product-android-beta)。

若要将文件安装到打开的仿真器或连接的 Android 设备上，请运行以下命令：

```shell
adb install <path_to_APK>/fennec-XX.X.XX.android-arm.apk
```

### <a name="ios-simulator"></a>iOS 模拟器

适用于 Mac OS X 的 iOS 模拟器附带 Xcode，从 [应用商店安装](https://itunes.apple.com/app/xcode/id497799835)。

完成后，了解如何通过 Apple 开发人员文档使用 [模拟器](https://help.apple.com/simulator/mac/current)。

> [!NOTE]
> 若要避免每次想要使用 iOS 模拟器时都打开 Xcode，请将其打开，将鼠标悬停在扩展坞中的 iOS 模拟器图标上，打开上下文菜单 (右键单击) ，然后选择"在扩展坞中**保留"。**  现在只要需要图标即可。

### <a name="microsoft-edge-edgehtml"></a>Microsoft Edge (EdgeHTML) 

:::image type="complex" source="../media/device-mode-modern-ie-vm.msft.png" alt-text="新式 IE VM。" lightbox="../media/device-mode-modern-ie-vm.msft.png":::
   新式 IE VM
:::image-end:::

Microsoft Edge (使用 EdgeHTML) 虚拟机 (VM) ，可以通过 VirtualBox (或 VMWare) 访问计算机上不同版本的 EdgeHTML 和 Internet Explorer。  在下载 [页面上选择虚拟机](https://developer.microsoft.com/microsoft-edge/tools/vms)。


<!-- ====================================================================== -->
## <a name="cloud-based-emulators-and-simulators"></a>基于云的模拟器和模拟器

如果你无法使用仿真器，并且无法访问真实设备，则基于云的仿真器是下一个最佳选择。  与实际设备和本地仿真器不同，基于云的模拟器的一大优势是，可以跨不同平台自动执行网站单元测试。

以下产品是基于云的仿真器和相关产品的示例。  这些说明来自产品的信息网站，并用作要考虑的特性或功能的示例。

*   [BrowserStack](https://www.browserstack.com/automate) 可帮助你执行手动测试。  选择操作系统、浏览器版本、设备类型和要浏览的 URL，然后 BrowserStack 将旋转可与之交互的托管虚拟机。  你可以在同一个屏幕中运行多个仿真器，以同时跨多个设备测试你的应用的外观。

*   [设备 Anywhere](https://www.sigos.com/app-experience/) 不使用仿真器，而是能够远程控制的真实设备。  当你需要在特定的设备上重现问题，并且某些报告中可能不会显示问题时，这非常有用。

*   [LambdaTest](https://www.lambdatest.com/) 可帮助你在各种浏览器和操作系统的组合上执行手动跨浏览器测试。  你可以录制复杂 Bug 的视频，并通过集成（如 Microsoft Teams、Slack 等）共享它们。  可以通过并行运行测试来加快测试速度。

*   [使用操作](https://saucelabs.com) 标签，可以在仿真器内运行单元测试，这可用于编写通过网站的流脚本，并随后在各种设备上观看此内容的视频录制。  您还可以对网站执行手动测试。

*   [TestingBot](https://testingbot.com/) 可帮助你在各种浏览器和操作系统组合上执行手动测试和自动测试。  在 TestingBot 的仿真器和物理设备上测试你的网站和移动应用。

 (此列表因加法而关闭。) 


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于此处，[](https://developers.google.com/web/tools/chrome-devtools/device-mode/testing-other-browsers)由[Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 和[Paul Bakaus](https://developers.google.com/web/resources/contributors#paul-bakaus) (Google |工具、性能、动画、UX) 。

[![Creative Commons License。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
