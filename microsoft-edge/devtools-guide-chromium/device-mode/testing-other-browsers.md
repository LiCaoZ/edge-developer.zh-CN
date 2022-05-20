---
title: 模拟和测试其他浏览器
description: 你的作业不会以确保网站在Microsoft Edge和Android中运行出色而结束。  尽管设备仿真 (设备模式) 可以模拟一系列其他设备，例如智能手机，但我们鼓励你查看其他浏览器提供的仿真解决方案。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 4f0b41162f1ef027e1dbe7388fd09795e92aa6e3
ms.sourcegitcommit: 1b70a2b8fa6649a1aa423b047c64f3df972150cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2022
ms.locfileid: "12520883"
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

你的作业不会以确保网站在Microsoft Edge和Android中运行出色而结束。  即使 [设备仿真](index.md) 工具可以模拟一系列其他设备，如智能手机，我们鼓励你查看其他浏览器提供的仿真解决方案。

### <a name="summary"></a>摘要

*  如果没有特定设备或想要对某项内容进行抽查时，最佳选择是在浏览器中模拟设备。

*  通过设备仿真器和模拟器，你可以从工作站模拟一系列设备上的开发站点。

*  通过基于云的仿真器，可跨不同平台自动执行站点的单元测试。


<!-- ====================================================================== -->
## <a name="browser-emulators"></a>浏览器模拟器

浏览器仿真器非常适合测试站点的响应能力。  但是，浏览器模拟器不能模拟 API、CSS 支持以及仅在实际设备上的移动浏览器上显示的某些行为的差异。  在实际设备上运行的浏览器上测试站点，确定所有内容的行为都按预期方式进行。

### <a name="firefox-responsive-design-view"></a>Firefox 响应式设计视图

Firefox 具有 [响应式设计视图](https://developer.mozilla.org/docs/Tools/Responsive_Design_View) ，可鼓励你停止对特定设备的思考，而是通过拖动窗口的边缘来探索设计如何以常见的屏幕大小或自己的屏幕大小进行更改。

### <a name="edgehtml-emulation"></a>EdgeHTML 仿真

若要模拟Windows电话，请使用 Microsoft Edge (EdgeHTML) [内置仿真](/archive/microsoft-edge/legacy/developer/devtools-guide/emulation)。

使用 [IE 11 仿真](/previous-versions/windows/internet-explorer/ie-developer/samples/dn255001(v=vs.85)) 模拟页面在较旧版本的 Internet Explorer 中的外观。


<!-- ====================================================================== -->
## <a name="device-emulators-and-simulators"></a>设备模拟器和模拟器

设备模拟器和模拟器不仅模拟浏览器环境，还模拟整个设备。  每个模拟器都可用于测试需要 OS 集成的东西，例如使用虚拟键盘的表单输入。

### <a name="android-emulator"></a>Android模拟器

<!--
:::image type="content" source="../media/device-mode-android-emulator-stock-browser.msft.png" alt-text="Stock Browser in Android Emulator." lightbox="../media/device-mode-android-emulator-stock-browser.msft.png":::
-->

目前，无法在Android模拟器上安装Microsoft Edge。  但是，可以使用 Android 浏览器、Chromium Content Shell 和 Firefox for Android，本文稍后将对此进行回顾。  Chromium Content Shell 运行与Microsoft Edge相同的Chromium呈现引擎，但不使用特定于浏览器的功能。

Android模拟器随附Android SDK，需要将其作为[Android Studio](https://developer.android.com/sdk/installing/studio.html)的一部分下载。  然后按照说明 [设置虚拟设备](https://developer.android.com/tools/devices/managing-avds.html) 并 [启动模拟器](https://developer.android.com/tools/devices/emulator.html)。
启动模拟器后，选择 **“浏览器**”图标，并在旧的“股票浏览器”上测试站点以进行Android。

#### <a name="chromium-content-shell-on-android"></a>Android上Chromium内容 shell

<!--
:::image type="content" source="../media/device-mode-android-avd-contentshell.msft.png" alt-text="Android Emulator Content Shell." lightbox="../media/device-mode-android-avd-contentshell.msft.png":::
-->

若要安装用于Android的 Chromium Content Shell，请保持模拟器运行并运行以下命令：

```shell
git clone https://github.com/PaulKinlan/chromium-android-installer.git
chmod u+x ./chromium-android-installer/*.sh
./chromium-android-installer/install-chromeandroid.sh
```

现在，可以使用 Chromium Content Shell 测试网站。

#### <a name="firefox-on-android"></a>Android上的 Firefox

<!--
:::image type="content" source="../media/device-mode-ff-on-android-emulator.msft.png" alt-text="Firefox Icon on Android Emulator." lightbox="../media/device-mode-ff-on-android-emulator.msft.png":::
-->

与 Chromium Content Shell 类似，可以获取用于将 Firefox 安装到模拟器上的 APK。

[下载正确的 .apk 文件](https://www.mozilla.org/firefox/all/#product-android-beta)。

若要将文件安装到打开的模拟器或连接Android设备上，请运行以下命令：

```shell
adb install <path_to_APK>/fennec-XX.X.XX.android-arm.apk
```

### <a name="ios-simulator"></a>iOS模拟器

用于Mac OS X的iOS模拟器随附Xcode，[这是从App Store安装的](https://itunes.apple.com/app/xcode/id497799835)。

完成后，通过 [Apple 开发人员文档](https://help.apple.com/simulator/mac/current)了解如何使用模拟器。

> [!NOTE]
> 若要避免每次想要使用iOS模拟器时都必须打开Xcode，请打开 <!--Xcode, or iOS Simulator?-->然后，右键单击码头中的iOS模拟器图标，然后选择 **“保留在码头中**”。  现在只需在需要时单击该图标即可。

### <a name="microsoft-edge-edgehtml"></a>Microsoft Edge (EdgeHTML) 

:::image type="content" source="../media/device-mode-modern-ie-vm.msft.png" alt-text="现代。IE VM。" lightbox="../media/device-mode-modern-ie-vm.msft.png":::

Microsoft Edge (EdgeHTML) 虚拟机 (VM) 使你能够通过 VirtualBox (或 VMWare) 访问计算机上的不同版本的 EdgeHTML 和 Internet Explorer。  在 [下载页上选择虚拟机](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms)。<!-- temp keep /en-us, delete it later when omitting it ends up at right url -->


<!-- ====================================================================== -->
## <a name="cloud-based-emulators-and-simulators"></a>基于云的模拟器和模拟器

如果无法使用仿真器，并且无法访问实际设备，则基于云的仿真器是下一个最佳功能。  基于云的仿真器比实际设备和本地仿真器有很大优势，你可以跨不同的平台自动执行站点的单元测试。

下面的列表是基于云的仿真器和测试站点的示例。 查看选择测试站点时要考虑的功能或功能的说明。 进行自己的搜索，以根据需要找到基于云的最佳模拟器。

* [BrowserStack](https://www.browserstack.com/automate) 可帮助你执行手动测试。  选择要浏览的操作系统、浏览器版本、设备类型和 URL，然后 BrowserStack 将启动可与之交互的托管虚拟机。  可以在同一屏幕中运行多个仿真器，同时在多个设备上测试应用的外观。

* [Mobileum](https://www.sigos.com/app-experience/) 不使用仿真器，而是可远程控制的实际设备。  当需要在特定设备上重现问题且某些报表中可能未出现问题时，这非常有用。

* [HeadSpin](https://www.headspin.io/) 可帮助你在数千台实际设备、浏览器和操作系统上执行手动跨浏览器测试。  可以通过 Slack、JIRA 等集成来录制复杂 bug 的视频并共享它们。  通过并行测试，快速推进市场推广。

* [LambdaTest](https://www.lambdatest.com/) 可帮助你在各种浏览器和操作系统的组合上执行手动跨浏览器测试。  可以通过集成（如 Microsoft Teams、Slack 等）录制复杂 bug 的视频并共享它们。  可以通过并行运行测试来加快测试速度。

* [SauceLabs](https://saucelabs.com) 使你能够在模拟器内部运行单元测试，这对于编写流通过站点的脚本以及在各种设备上观看视频录制非常有用。  还可以使用站点进行手动测试。

* [TestingBot](https://testingbot.com/) 可帮助你在各种浏览器和操作系统组合上进行手动测试和自动测试。  在 TestingBot 的仿真器和物理设备上测试网站和移动应用。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在这里](https://developers.google.com/web/tools/chrome-devtools/device-mode/testing-other-browsers) 找到，由 [梅金·科尔尼](https://developers.google.com/web/resources/contributors#meggin-kearney) (技术作家) 和 [保罗·巴考斯](https://developers.google.com/web/resources/contributors#paul-bakaus) (开放 Web 开发大使在谷歌|工具、性能、动画、UX) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
