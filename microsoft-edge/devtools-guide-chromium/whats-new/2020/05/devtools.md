---
title: 'DevTools (Microsoft Edge 84) '
description: 在高对比度模式下Windows DevTools，匹配 DevTools 中的键盘快捷方式以Visual Studio Code等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: 8a85aebcfb1a658b408f32bb836a07d028659da0
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284243"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="whats-new-in-devtools-microsoft-edge-84"></a>DevTools (Microsoft Edge 84) 


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

以下各节列出了你可能错过的来自 DevTools Microsoft Edge通知。  请查看公告以试用 DevTools、Microsoft Visual Studio代码扩展等中的新功能。  若要了解有关开发人员工具中的所有最新功能和最强大功能的最新动态，请下载 [Microsoft Edge 预览频道](https://aka.ms/microsoftedge)并[在 Twitter 上关注我们](https://aka.ms/twitter/edgedevtools)。

### <a name="use-the-devtools-in-windows-high-contrast-mode"></a>在高对比度模式下Windows DevTools

现在Microsoft Edge开发人员工具在高对比度模式下显示Windows高对比度模式。

:::image type="complex" source="../../media/2020/05/high-contrast.msft.png" alt-text="在Microsoft Edge模式下使用 DevTools" lightbox="../../media/2020/05/high-contrast.msft.png":::
   在Microsoft Edge模式下使用 DevTools
:::image-end:::

[按照说明在设置中打开高对比度Windows。](https://support.microsoft.com/help/4026951/windows-10-turn-high-contrast-mode-on-or-off)  若要在"工具"中打开Microsoft Edge，请选择 或 `F12` `Ctrl` + `Shift` + `I` 。  DevTools 以高对比度模式显示。

> [!NOTE]
> 当前Microsoft Edge开发工具在 macOS 上支持Windows高对比度模式。

Chromium问题[#1048378](https://crbug.com/1048378)

### <a name="match-keyboard-shortcuts-in-the-devtools-to-visual-studio-code"></a>将 DevTools 中的键盘快捷方式与Visual Studio Code

从[你的反馈](../../../contact.md)和Chromium[](https://bugs.chromium.org/p/chromium/issues/list)问题跟踪器中，Microsoft Edge DevTools 团队了解到你需要在 DevTools 中自定义键盘快捷方式的能力。  在 Microsoft Edge 84 中，你现在能够将 DevTools 中的键盘快捷方式与[Visual Studio Code](https://code.visualstudio.com/)匹配，这只是团队正致力于进行快捷方式自定义的功能之一。

:::image type="complex" source="../../media/2020/05/keyboard-shortcut.msft.png" alt-text="将 DevTools 中的键盘快捷方式与Visual Studio Code" lightbox="../../media/2020/05/keyboard-shortcut.msft.png":::
   在Microsoft Edge模式下使用 DevTools
:::image-end:::

若要尝试实验：

1. 在 DevTools**** 中，设置选择或选择 `?` DevTools 设置右上角的 ![ "Devtools"图标图标，打开 ](../../../media/settings-icon.msft.png) "开发工具"。

1. 在实验**部分中**，选中复选框启用**自定义键盘快捷方式设置选项卡 (重新加载) 。 **

1. 重新加载 DevTools。

1. 再次**设置"，** 然后选择 **"快捷方式"** 部分。

1. Click the **Match shortcuts from preset** dropdown， select **DevTools (Default) **， and then select **Visual Studio Code**.  

DevTools 中的键盘快捷方式现在与开发人员工具中的等效操作Visual Studio Code。

例如，用于暂停或继续运行脚本的键盘快捷方式在 Visual Studio Code[为](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) `F5` 。  在**DevTools (Default) **预设中，DevTools 中的同一快捷方式是 ，但具有 Visual Studio Code 预设，该快捷方式现在也 `F8` **** `F5` 。

此功能当前作为实验Microsoft Edge 84 中提供，因此请与[团队分享你的](../../../contact.md)反馈！

Chromium问题[#174309](https://crbug.com/174309)

### <a name="remote-debug-surface-duo-emulators"></a>远程调试 Surface Duo 仿真器

现在，你能够使用开发人员工具的完整功能远程调试[在 Surface Duo](/dual-screen/android/use-emulator)仿真器中Microsoft Edge [Web 内容](../../../index.md)。

使用 [Surface Duo 仿真](/dual-screen/android/use-emulator)器，你可以测试 Web 内容在可折叠和双屏幕设备的新类上呈现方式。  仿真器运行 Android 操作系统，并提供[Microsoft Edge Android 应用](https://play.google.com/store/apps/details?id=com.microsoft.emmx)。  在开发人员应用中加载[Microsoft Edge内容，](https://play.google.com/store/apps/details?id=com.microsoft.emmx)然后使用开发人员工具Microsoft Edge[调试它](../../../index.md)。

:::image type="complex" source="../../media/2020/05/surface-duo-emulator.msft.png" alt-text="Surface Duo Microsoft Edge上运行的 Surface Duo 应用" lightbox="../../media/2020/05/surface-duo-emulator.msft.png":::
   Surface Duo 仿真程序上的 Microsoft Edge 应用
:::image-end:::

桌面 `edge://inspect` 实例的页面显示**SurfaceD Microsoft Edge Emulator，** 其中列出了在 Surface Duo 仿真器上运行的已打开选项卡或[](https://www.microsoft.com/edge/)[PWA。](../../../../progressive-web-apps-chromium/index.md) [](/dual-screen/android/use-emulator)

:::image type="complex" source="../../media/2020/05/edge-inspect.msft.png" alt-text="edge://inspect 页面在模拟器上运行的 Microsoft Edge 应用程序中显示打开选项卡的列表" lightbox="../../media/2020/05/edge-inspect.msft.png":::
   `edge://inspect` 页面在模拟器上运行的 Microsoft Edge 应用程序中显示打开选项卡的列表
:::image-end:::

为**要**调试的选项卡或PWA选择"检查"以Microsoft Edge[开发人员工具"。](../../../index.md)  [按照分步指南在 Surface Duo](../../../remote-debugging/surface-duo-emulator.md)模拟器上远程调试 Web 内容。

### <a name="resize-the-devtools-drawer-more-easily"></a>更轻松地调整 DevTools 箱的大小

在 Microsoft Edge 83 或更早版本中，你仅能通过将鼠标悬停在"箱"工具栏内来调整[Devtools"](../../../customize/index.md#drawer)箱"的大小。  The Drawer behavely different than the other resize controls for panes in the DevTools where you hover on the border of the pane to resize it.  选择下图可显示调整"箱"大小在版本 83 或更早版本中Microsoft Edge。

:::image type="complex" source="../../media/2020/05/drawer-83.msft.png" alt-text="调整 83 中 DevTools Microsoft Edge" lightbox="../../media/2020/05/drawer-83.msft.gif":::
   调整 83 中 DevTools Microsoft Edge
:::image-end:::

<!--todo:  create png that represents the gif information  -->

从 Microsoft Edge 84 开始，现在通过将鼠标悬停在"箱"边框上，可以调整"箱"的大小。  此更改将调整 DevTools 箱大小的行为与调整 DevTools 中其他窗格的大小的方式保持一致。  选择以下图像以显示 84 中正在Microsoft Edge大小。

:::image type="complex" source="../../media/2020/05/drawer-84.msft.png" alt-text="调整 84 中 DevTools Microsoft Edge" lightbox="../../media/2020/05/drawer-84.msft.gif":::
   调整 84 中 DevTools Microsoft Edge
:::image-end:::

<!--todo:  create png that represents the gif information  -->

Chromium问题[#1076112](https://crbug.com/1076112)

### <a name="screencasting-navigation-buttons-display-focus"></a>屏幕广播导航按钮显示焦点

远程调试[Android](../../../remote-debugging/index.md)设备[、Windows 10](../../../remote-debugging/windows.md)或更高版本设备或[Surface Duo](../../../remote-debugging/surface-duo-emulator.md)仿真器时，可以使用 ![ DevTools 左上角的切换屏幕视频图标切换屏幕视频 ](../../../media/toggle-screencast-icon.msft.png) 。  启用屏幕广播后，你可以从 DevTools Microsoft Edge在远程设备上导航选项卡。  在 Microsoft Edge 84 中，这些导航按钮现在也可供键盘访问。

:::image type="complex" source="../../media/2020/05/screencasting-nav.msft.png" alt-text="Select Shift+Tab from the screencasted URL bar shows focus on the Refresh button" lightbox="../../media/2020/05/screencasting-nav.msft.png":::
   Select `Shift` + `Tab` from the screencasted URL bar shows focus on the **Refresh** button
:::image-end:::

Chromium问题[#1081486](https://crbug.com/1081486)

### <a name="network-panel-details-pane-is-now-accessible"></a>网络面板 现在可访问详细信息窗格

在 Microsoft Edge 84 中，[](../../../network/index.md#inspect-the-details-of-the-resource)当您在网络日志中**** 为资源打开"网络"工具中的"详细信息"窗格时，它[现在将具有焦点](../../../network/index.md#log-network-activity)。  此更改允许屏幕阅读器读出"详细信息"窗格的内容并 **与之** 交互。

:::image type="complex" source="../../media/2020/05/network-details.msft.png" alt-text="&quot;网络&quot;面板中的&quot;详细信息&quot;窗格在打开时将焦点" lightbox="../../media/2020/05/network-details.msft.png":::
   " **网络** "工具中的" **详细信息** "窗格在打开时将焦点
:::image-end:::

Chromium 问题 [#963183](https://crbug.com/963183)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下各节宣布 84 Microsoft Edge开放源代码管理项目中提供的其他Chromium功能。

### <a name="fix-site-issues-with-the-new-issues-tool-in-the-devtools-drawer"></a>修复开发人员工具箱中新问题工具的网站问题

DevTools"箱"中新增的"问题"工具是为了帮助减少控制台的通知疲劳和**混乱。** ****  目前，**控制台**是网站开发人员、库、框架和网站Microsoft Edge记录消息、警告和错误的中心位置。  "**问题**"工具以结构化、聚合且可操作的方式聚合来自浏览器的警告、指向 Microsoft Edge DevTools 中受影响的资源的链接，并提供有关如何修复问题的指南。  随着时间的推移，问题工具（而不是控制台）Microsoft Edge中显示越来越多的警告，这应该有助于减少**** 控制台中的混乱 **。** ****

To get started， navigate to [Find and fix problems using the Issues tool](../../../issues/index.md).

:::image type="complex" source="../../media/2020/05/issues.msft.png" alt-text="DevTools&quot;箱&quot;中的&quot;问题&quot;工具" lightbox="../../media/2020/05/issues.msft.png":::
   DevTools"箱"中的"问题"工具****
:::image-end:::

Chromium问题[#1068116](https://crbug.com/1068116)

### <a name="view-accessibility-information-in-the-inspect-mode-tooltip"></a>在检查模式工具提示中查看辅助功能信息

检查**模式**工具提示现在指示元素是否具有辅助名称和角色，并且[是键盘可聚焦的](https://webhint.io/docs/user-guide/hints/hint-axe/keyboard/)。 [](https://webhint.io/docs/user-guide/hints/hint-axe/name-role-value/)

<!--todo:  add link inspect mode tooltip (WebdevCls) when section is live  -->
<!--todo:  add link name and role (WebdevLabelsText) when section is live  -->
<!--todo:  add link keyboard-focusable (WebdevControlFocus) when section is live  -->

:::image type="complex" source="../../media/2020/05/a11y.msft.png" alt-text="包含辅助功能信息的检查模式工具提示" lightbox="../../media/2020/05/a11y.msft.png":::
  包含 **辅助功能** 信息的检查模式工具提示
:::image-end:::

Chromium问题[#1040025](https://crbug.com/1040025)

### <a name="performance-panel-updates"></a>性能面板更新

#### <a name="view-total-blocking-time-information-in-the-footer"></a>查看页脚中的总阻止时间信息

记录负载性能后，"性能****"面板现在在页脚 (TBT) 总阻止时间。  TBT 是一种负载性能指标，有助于量化页面使用所花的时间。  它实质上测量页面显示为可用 (因为内容呈现到屏幕布局中) ;但实际上并不可用，因为 JavaScript 会阻止主线程，因此页面不会响应用户输入。  TBT 是估计第一次输入延迟的主要指标。

<!--todo:  add link Total Blocking Time (TBT) (WebdevTbt) when section is live  -->
<!--todo:  add link lab metric (WebdevMeasureSpeedLabField) when section is live  -->
<!--todo:  add link Core Web Vitals (WebdevCoreWebVitals) when section is live  -->

若要获取总阻止时间信息，请不要使用"刷新 **页面**刷新"页面 ![ 图标工作流 ](../../../media/refresh-page-icon.msft.png) 来记录页面加载性能。

相反，选择 **"录制** ![ "图标， ](../../../media/record-icon.msft.png) 手动重新加载页面，等待页面加载，然后停止录制。

如果显示，Microsoft Edge DevTools 未从 Microsoft Edge 中的内部 `Total Blocking Time: Unavailable` 分析数据获取所需信息。

:::image type="complex" source="../../media/2020/05/tbt.msft.png" alt-text="性能面板记录的页脚中的总阻止时间信息" lightbox="../../media/2020/05/tbt.msft.png":::
   性能面板记录的页脚中的总 **阻止时间** 信息
:::image-end:::

Chromium问题[#1054381](https://crbug.com/1054381)

#### <a name="layout-shift-events-in-the-new-experience-section"></a>新"体验"部分中的布局 Shift 事件

"**性能"****面板的新"** 体验"部分可帮助你检测布局变化。  累积布局 (CLS) 是一项指标，可帮助你量化不需要的视觉不稳定。

<!--todo:  add link Core Web Vitals (WebdevCoreWebVitals) when section is live  -->
<!--todo:  add link layout shifts (WebdevCls) when section is live  -->

选择 **"布局班次** "事件，在"摘要"窗格中显示布局 **班次的详细信息** 。  将鼠标悬停在 **"移动位置** "和" **移动到** "字段上，可直观地显示发生布局切换的位置。

:::image type="complex" source="../../media/2020/05/cls.msft.png" alt-text="布局转换的详细信息" lightbox="../../media/2020/05/cls.msft.png":::
   布局转换的详细信息
:::image-end:::

### <a name="more-accurate-promise-terminology-in-the-console"></a>控制台中更准确的承诺术语

记录 时 `Promise` ， **控制台** 错误地提供了设置为 `PromiseStatus` 的值 `resolved` 。

:::image type="complex" source="../../media/2020/05/resolved.msft.png" alt-text="使用旧的已解析术语的控制台示例" lightbox="../../media/2020/05/resolved.msft.png":::
   使用旧 **术语** 的控制台 `resolved` 示例
:::image-end:::

控制台 **现在** 使用术语 `fulfilled` ，该术语与规范 `Promise` 一致。  有关规范详细信息，请导航到"状态"和 `Promise` ["GitHub"。](https://github.com/domenic/promises-unwrapping/blob/master/docs/states-and-fates.md)

:::image type="complex" source="../../media/2020/05/fulfilled.msft.png" alt-text="使用新的已实现术语的控制台示例" lightbox="../../media/2020/05/fulfilled.msft.png":::
  使用新 **术语** 的控制台 `fulfilled` 示例
:::image-end:::

V8 问题 [#6751](https://bugs.chromium.org/p/v8/issues/detail?id=6751)

### <a name="styles-pane-updates"></a>样式窗格更新

#### <a name="support-for-the-revert-keyword"></a>支持 revert 关键字

"样式"窗格的自动完成**** UI 现在检测到[revert](https://developer.mozilla.org/docs/Web/CSS/revert) CSS 关键字，该关键字将属性的级联值还原为之前应用于元素样式的值。

:::image type="complex" source="../../media/2020/05/revert.msft.png" alt-text="设置要还原的属性的值" lightbox="../../media/2020/05/revert.msft.png":::
  设置要还原的属性的值
:::image-end:::

Chromium问题[#1075437](https://crbug.com/1075437)

#### <a name="image-previews"></a>图像预览

将鼠标 `background-image` 悬停在 **"** 样式"窗格中的值上，以在工具提示中显示图像预览。

:::image type="complex" source="../../media/2020/05/image-preview.msft.png" alt-text="将鼠标悬停在背景图像值上" lightbox="../../media/2020/05/image-preview.msft.png":::
  将鼠标悬停在 `background-image` 值上方
:::image-end:::

Chromium问题[#1040019](https://crbug.com/1040019)

#### <a name="color-picker-now-uses-space-separated-functional-color-notation"></a>颜色选取器现在使用空格分隔的功能颜色表示法

[CSS 颜色模块级别 4](https://drafts.csswg.org/css-color#changes-from-3) 指定颜色函数（如 ）应 `rgb()` 支持空格分隔参数。  例如，`rgb(0, 0, 0)` 与 `rbg(0 0 0)` 等效。

当你通过选择值来选择[](../../../css/reference.md#change-colors-with-the-color-picker)颜色选取器或在 **"** 样式"窗格中的颜色表示形式之间交替选择颜色时，将显示空格分隔 `Shift` `background-color` 的参数语法。

:::image type="complex" source="../../media/2020/05/color.msft.png" alt-text="在&quot;样式&quot;窗格中使用空格分隔的参数" lightbox="../../media/2020/05/color.msft.png":::
  在"样式"窗格中使用 **空格分隔** 的参数
:::image-end:::

还应在"计算"窗格和"检查**模式****"工具提示**中显示语法。

Microsoft Edge DevTools 使用的是新语法，因为即将推出的 CSS 功能（如[color () ）](https://drafts.csswg.org/css-color#the-color-property)不支持已弃用的逗号分隔参数语法。

一段时间以来，大多数浏览器都支持空格分隔的参数语法。  有关详细信息，请导航到" [我可以使用：用空格分隔的功能颜色表示法"？](https://caniuse.com/#feat=mdn-css_types_color_space_separated_functional_notation)

Chromium问题[#1072952](https://crbug.com/1072952)

### <a name="deprecation-of-the-properties-pane-in-the-elements-panel"></a>在"元素"面板中弃用"属性"窗格

Elements **** 工具中的"**属性**"窗格已弃用。  改为 `console.dir($0)` 在 **控制台** 中运行。

:::image type="complex" source="../../media/2020/05/properties.msft.png" alt-text="已弃用的属性窗格" lightbox="../../media/2020/05/properties.msft.png":::
   已弃**用的属性窗格**
:::image-end:::

#### <a name="references"></a>参考

*   [console.dir () ](../../../console/api.md#dir)
*   [$0](../../../console/utilities.md#recently-chosen-element-or-javascript-object)

### <a name="app-shortcuts-support-in-the-manifest-pane"></a>清单窗格中的应用程序快捷方式支持

应用快捷方式可帮助用户在 Web 应用中快速启动常见任务或推荐任务。  应用快捷方式菜单只针对安装在用户的桌面或移动设备上的渐进式 [Web](../../../../progressive-web-apps-chromium/index.md) 应用显示。

<!-- For more information, see [Get things done quickly with app shortcuts](https://alphabet-dev/app-shortcuts). -->

<!--todo:  add link Get things done quickly with app shortcuts (WebdevAppShortcuts) when section is live -->

:::image type="complex" source="../../media/2020/05/app-shortcuts.msft.png" alt-text="&quot;清单&quot;窗格中的应用快捷方式" lightbox="../../media/2020/05/app-shortcuts.msft.png":::
  "清单"窗格中 **的应用** 快捷方式
:::image-end:::


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://aka.ms/microsoftedge) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/blog/new-in-devtools-84)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
