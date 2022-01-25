---
title: 'DevTools (Microsoft Edge 81) '
description: 3D 视图Visual Studio与Microsoft Edge集成等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: db8ed0d9acc83831ed93a9b4816efe0bd0ece8fc
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12320751"
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
# <a name="whats-new-in-devtools-microsoft-edge-81"></a>DevTools （Microsoft Edge 81）中的新增功能


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

以下各节列出了你可能错过的来自 DevTools Microsoft Edge通知。  请查看公告以试用 DevTools、Microsoft Visual Studio代码扩展等中的新功能。  若要了解有关开发人员工具中的所有最新功能和最强大功能的最新动态，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download)并[在 Twitter 上关注我们](https://twitter.com/EdgeDevTools)。

### <a name="accessibility-improvements-to-the-devtools"></a>对 DevTools 的辅助功能改进

DevTools 团队已对 Chromium 进行 170 次更改，以解决 DevTools 中的高影响颜色对比度、键盘和屏幕阅读器问题。  每个生成 Web 的开发人员都应能够使用 DevTools。

:::image type="complex" source="../../images/2020/01/a11y-performance-tool.msft.gif" alt-text="具有键盘导航和屏幕阅读器改进的 DevTools 中的性能工具" lightbox="../../images/2020/01/a11y-performance-tool.msft.gif":::
   具有 **键盘** 导航和屏幕阅读器改进的 DevTools 中的性能工具
:::image-end:::

想要了解如何使网页可供所有用户访问？  下载[辅助功能Insights](https://accessibilityinsights.io) [Webhint](https://webhint.io/docs/user-guide/extensions/extension-browser)扩展，Microsoft Edge开始操作。

如果你使用屏幕阅读器或键盘浏览 DevTools，请通过[发推](https://twitter.com/intent/tweet?text=@EdgeDevTools)或单击**反馈**图标向我们发送你的反馈！

Chromium 问题 [#963183](https://crbug.com/963183)

### <a name="using-the-devtools-in-other-languages"></a>以其他语言使用 DevTools

许多开发人员使用其他开发人员工具（如 StackOverflow 和 Visual Studio Code，使用其本地语言，而不只是使用英语。  我们很高兴宣布 DevTools 的本地化，你现在可以使用英语之外 10 种语言之一：

* 简 (简体) - &#20013;&#25991;&#65288;&#31616;&#20307;&#65289;
* 繁体 (中文) - &#20013;&#25991;&#65288;&#32321;&#39636;&#65289;
* 法语 –&#231;语
* 德语 - 德语
* 意大利语 - 意大利语
* 日语 - &#26085;&#26412;&#35486;
* 朝鲜语 - &#54620;&#44397;&#50612;
* 葡萄牙语 - 图卢&#234;语
* 俄语 – &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;
* 西班牙语 - 电子邮件&#241;ol

<!--
|  |  |
|:--- |:--- |
| Chinese (Simplified) - 中文(简体)（简体）| Chinese (Traditional) - 中文(繁體)（繁體）|
| French – français | German - deutsch |
| Italian - italiano | Portuguese - português |
| Korean - 한국어 | Japanese - 日本語 |
| Russian – русский | Spanish - español |
-->

DevTools 会自动匹配你在 中用于Microsoft Edge的语言 `edge://settings/languages` 。

如果你希望Microsoft Edge一种语言，并且你的 DevTools 保持为英语，请在 DevTools 中选择以打开设置 `F1` 并禁用[](../../../customize/index.md#settings)**匹配浏览器语言**。

:::image type="complex" source="../../images/2020/01/localized-devtools.msft.png" alt-text="德语的 DevTools" lightbox="../../images/2020/01/localized-devtools.msft.png":::
   德语的 DevTools
:::image-end:::

**控制台** 消息未本地化。  只有 DevTools UI 中使用的字符串以你用于开发Microsoft Edge。

如果你想要以与可用版本不同的语言使用 DevTools，请通过我们的推文或选择[](https://twitter.com/intent/tweet?text=@EdgeDevTools)"发送反馈 **"** 图标。

Chromium问题[#941561](https://crbug.com/941561)

### <a name="webhint-microsoft-edge-extension"></a>webhint Microsoft Edge扩展

Webhint Microsoft Edge扩展允许你在 DevTools 中轻松扫描网页并获取有关辅助功能、浏览器兼容性、安全性、性能等的反馈。  有关详细信息，请参阅 [https://webhint.io](https://webhint.io) 。

:::image type="complex" source="../../images/2020/01/webhint-browser-extension.msft.png" alt-text="安装 Webhint 浏览器扩展时 DevTools 中的 Hints 工具" lightbox="../../images/2020/01/webhint-browser-extension.msft.png":::
   安装 **Webhint** 浏览器扩展时 DevTools 中的 Hints 工具
:::image-end:::

[尝试 webhint 浏览器扩展Microsoft Edge。](https://microsoftedge.microsoft.com/addons/detail/webhint/mlgfbihcfnkaenjpdcngdnhcpkdmcdee)  安装扩展后，打开 DevTools 并选择 **提示** 工具。  从此处运行可自定义的网站扫描。  请 [前往](https://webhint.io/docs/user-guide/extensions/extension-browser) webhint.io 了解更多信息。

### <a name="3d-view"></a>3D 视图

使用 **3D** (视图通过浏览文档对象模型或 [DOM ](https://developer.mozilla.org/docs/Web/API/Document_Object_Model)) [或 z 索引](https://developer.mozilla.org/docs/Web/CSS/z-index) 堆栈上下文来调试 Web 应用程序。

:::image type="complex" source="../../images/2020/01/3dview.msft.png" alt-text="DevTools 中的 3D 视图" lightbox="../../images/2020/01/3dview.msft.png":::
   DevTools 中的 3D 视图
:::image-end:::

若要访问 3D 视图，请选择 `Ctrl`  +  `Shift`  +  `P` ，键入**3D 视图，** 然后选择**显示 3D 视图**。

Microsoft Edge团队正在与 UI 上的 Chromium 团队合作，并将更多功能添加到 3D 视图，因此请使用"发送反馈 **"** 图标！

Chromium问题[#987787](https://crbug.com/987787)

### <a name="visual-studio-code-extensions"></a>Visual Studio Code扩展

DevTools 团队还发布了一些适用于 Visual Studio Code[](https://code.visualstudio.com)的扩展，让你可以直接从文本编辑器使用 DevTools 功能！ 请查看以下扩展：

#### <a name="elements-for-microsoft-edge"></a>用于Microsoft Edge

通过添加元素来Visual Studio Code元素扩展，从[Microsoft Edge Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)工具。

:::image type="complex" source="../../images/2020/01/elements-for-edge.msft.png" alt-text="元素工具Visual Studio Code元素扩展Microsoft Edge元素" lightbox="../../images/2020/01/elements-for-edge.msft.png":::
   元素**工具**Visual Studio Code元素扩展Microsoft Edge元素
:::image-end:::

有关详细信息，请查看元素[的扩展Microsoft Edge Visual Studio Code元素](../../../../visual-studio-code/elements-for-edge.md)。

#### <a name="debugger-for-microsoft-edge"></a>调试程序Microsoft Edge

使用[调试器 for Microsoft Edge](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-edge) Visual Studio Code 扩展，直接从 Microsoft Edge 调试在 Visual Studio Code 中运行的 JavaScript。

:::image type="complex" source="../../images/2020/01/vscode-debugger.msft.png" alt-text="Visual Studio Code 中的 Microsoft Edge Extension 调试器" lightbox="../../images/2020/01/vscode-debugger.msft.png":::
   Visual Studio Code 中的 Microsoft Edge Extension 调试器
:::image-end:::

有关详细信息，请查看如何从 Microsoft Edge[调试Visual Studio Code。](../../../../visual-studio-code/debugger-for-edge.md)

#### <a name="webhint"></a>webhint

[Webhint](https://marketplace.visualstudio.com/items?itemName=webhint.vscode-webhint) Visual Studio Code在编写网页 `webhint` 时用于改进网页。  此扩展将运行，并基于分析报告工作区文件的 `webhint` 诊断。

:::image type="complex" source="../../images/2020/01/webhint-vscode-extension.msft.png" alt-text="Webhint Visual Studio Code扩展，用于分析网站中的 .tsx Visual Studio Code" lightbox="../../images/2020/01/webhint-vscode-extension.msft.png":::
   Webhint Visual Studio Code分析 `.tsx` 文件中文件的扩展Visual Studio Code
:::image-end:::

[详细了解 webhint Visual Studio Code 。](https://webhint.io/docs/user-guide/extensions/vscode-webhint)

### <a name="visual-studio-integration"></a>Visual Studio集成

在 Visual Studio 2019 版本 16.2 或更高版本中，使用 Visual Studio 调试程序调试在 Microsoft Edge 中运行的 JavaScript。  [下载Visual Studio 2019](https://visualstudio.microsoft.com/downloads)以试用此功能！

:::image type="complex" source="../../images/2020/01/vs.msft.png" alt-text="Visual Studio Canary、Dev 或 Beta Microsoft Edge启动 Web 应用的选项" lightbox="../../images/2020/01/vs.msft.png":::
   Visual Studio Canary、Dev 或 Beta Microsoft Edge启动 Web 应用的选项
:::image-end:::

[详细了解如何从 Microsoft Edge 调试Visual Studio。](../../../../visual-studio/index.md)

### <a name="tracking-prevention-console-messages"></a>跟踪防护控制台消息

跟踪防护是网站中Microsoft Edge一项功能，可保护你免受之前未访问过的网站的跟踪。  默认跟踪防护设置为平衡模式，可阻止第三方跟踪器和已知的恶意跟踪器，从而获得平衡隐私和 Web 兼容性的体验。  为了让你深入了解阻止某些跟踪程序时网页的兼容性，当跟踪器被阻止时，控制台中添加了警告消息。 ****

:::image type="complex" source="../../images/2020/01/tracking-prevention.msft.png" alt-text="跟踪防护时控制台中的邮件阻止访问跟踪器的存储" lightbox="../../images/2020/01/tracking-prevention.msft.png":::
   跟踪防护 **时控制台** 中的邮件阻止访问跟踪器的存储
:::image-end:::

[阅读有关跟踪防护以及隐私与 Web 兼容性之间平衡的详细信息](https://blogs.windows.com/msedgedev/2019/12/03/improving-tracking-prevention-microsoft-edge-79)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下各节宣布 Microsoft Edge 81 中提供的其他功能已参与开放源代码Chromium项目。

### <a name="moto-g4-support-in-device-mode"></a>设备模式下的 Moto G4 支持

启用 [设备工具栏后](../../../device-mode/index.md#simulate-a-mobile-viewport)，从设备列表中模拟 Moto G4 **视口** 的尺寸。

:::image type="complex" source="../../images/2020/01/motog4.msft.png" alt-text="模拟 Moto G4 视口" lightbox="../../images/2020/01/motog4.msft.png":::
   模拟 Moto G4 视口
:::image-end:::

选择 ["显示设备框架](../../../device-mode/index.md#show-device-frame) "以在视口周围显示 Moto G4 硬件。

:::image type="complex" source="../../images/2020/01/motog4frame.msft.png" alt-text="显示 Moto G4 硬件" lightbox="../../images/2020/01/motog4frame.msft.png":::
   显示 Moto G4 硬件
:::image-end:::

相关功能：

*   打开命令 [菜单](../../../command-menu/index.md) 并运行命令，在启用"显示设备框架"菜单后，为包含 `Capture screenshot` Moto G4 硬件 (**的视** 口拍摄) 。
*   [限制网络和 CPU](../../../device-mode/index.md#throttle-the-network-and-cpu) 以更精确地模拟移动用户的 Web 浏览条件。

Chromium问题[#924693](https://crbug.com/924693)

### <a name="cookie-related-updates"></a>与 Cookie 相关的更新

#### <a name="blocked-cookies-in-the-cookies-pane"></a>"Cookie"窗格中阻止的 Cookie

"应用程序"面板中的"Cookie"窗格现在显示带黄色背景的阻止的 Cookie。

:::image type="complex" source="../../images/2020/01/blockedcookies.msft.png" alt-text="&quot;应用程序&quot;面板的&quot;Cookie&quot;窗格中阻止的 Cookie" lightbox="../../images/2020/01/blockedcookies.msft.png":::
   "应用程序"面板的"Cookie"窗格中阻止的 Cookie
:::image-end:::

Chromium问题[#1030258](https://crbug.com/1030258)  <!-- inaccessible  -->

#### <a name="cookie-priority-in-the-cookie-pane"></a>Cookie 窗格中的 Cookie 优先级

网络和应用程序 **工具中的** Cookie **表现在** 包含"优先级 **"** 列。

> [!CAUTION]
> Chromium的浏览器（如 Microsoft Edge）是唯一支持 Cookie 优先级的浏览器。

Chromium问题[#1026879](https://crbug.com/1026879)

#### <a name="edit-all-cookie-values"></a>编辑所有 Cookie 值

Cookie 表中的所有单元格现在均可编辑 **，"大小** "列中的单元格除外，因为该列表示 Cookie 的网络大小（以字节为单位）。  有关每列的说明，请导航到"[字段"。](../../../storage/cookies.md#fields)

:::image type="complex" source="../../images/2020/01/editcookie.msft.png" alt-text="编辑 Cookie 值" lightbox="../../images/2020/01/editcookie.msft.png":::
   编辑 Cookie 值
:::image-end:::

#### <a name="copy-as-nodejs-fetch-to-include-cookie-data"></a>复制为Node.js提取以包含 Cookie 数据

若要获取包含 Cookie 数据的表达式，请将鼠标悬停在网络请求上，打开上下文菜单 (右键单击") "，然后选择"复制复制Node.js `fetch` ****  >  **提取"。**

:::image type="complex" source="../../images/2020/01/fetchcookies.msft.png" alt-text="作为提取Node.js复制" lightbox="../../images/2020/01/fetchcookies.msft.png":::
   作为提取Node.js复制
:::image-end:::

Chromium问题[#1029826](https://crbug.com/1029826)

### <a name="more-accurate-web-app-manifest-icons"></a>更准确的 Web 应用清单图标

以前，应用程序面板中的"清单"窗格发送了自己的请求，以显示 Web 应用清单图标。  DevTools 现在显示与开发人员使用完全相同Microsoft Edge图标。

:::image type="complex" source="../../images/2020/01/manifesticons.msft.png" alt-text="清单窗格中的图标" lightbox="../../images/2020/01/manifesticons.msft.png":::
   清单窗格中的图标
:::image-end:::

Chromium问题[#985402](https://crbug.com/985402)

### <a name="hover-on-css-content-properties-to-display-unescaped-values"></a>将鼠标悬停在 CSS 内容属性上以显示未转义的值

将鼠标悬停在 `content` 属性的值上可显示该值的未转义版本。

例如，在此 [演示中](https://mathiasbynens.github.io/css-dbg-stories/css-escapes.html) ，检查伪元素时，转义字符串 `p::after` 将显示在" **样式** "窗格中：

:::image type="complex" source="../../images/2020/01/escapedstring.msft.png" alt-text="转义字符串" lightbox="../../images/2020/01/escapedstring.msft.png":::
   转义字符串
:::image-end:::

当您将鼠标悬停在 `content` 该值上时，将显示未转义的值。

:::image type="complex" source="../../images/2020/01/unescapedstring.msft.png" alt-text="未转义值" lightbox="../../images/2020/01/unescapedstring.msft.png":::
   未转义值
:::image-end:::

### <a name="more-detailed-source-map-errors-in-the-console"></a>控制台中更详细的源映射错误

控制台现在提供有关源映射无法加载或分析的原因的更多详细信息。  以前，它只是提供了一个错误，而没有解释错误。

:::image type="complex" source="../../images/2020/01/sourcemap.msft.png" alt-text="控制台中的源映射加载错误" lightbox="../../images/2020/01/sourcemap.msft.png":::
   控制台中的源映射加载错误
:::image-end:::

### <a name="setting-for-disabling-scrolling-past-the-end-of-a-file"></a>用于禁用滚动过文件末尾的设置

打开[设置，](../../../customize/index.md#settings)然后禁用首选项源**** 允许滚动到文件末尾，以禁用默认 UI 行为，该行为允许你在"源"面板中的文件末尾良好  >  ****  >  **** 滚动。 ****

:::image type="complex" source="../../images/2020/01/settings.msft.png" alt-text="禁用 允许滚动到文件的末尾" lightbox="../../images/2020/01/settings.msft.png":::
   禁用**允许滚动到文件末尾设置**
:::image-end:::

:::image type="complex" source="../../images/2020/01/scrollingsources.msft.png" alt-text="滚动过文件末尾现在在&quot;源&quot;面板中处于禁用状态" lightbox="../../images/2020/01/scrollingsources.msft.png":::
   滚动过文件末尾现在在"源"面板中处于禁用状态
:::image-end:::


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/blog/new-in-devtools-81)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
