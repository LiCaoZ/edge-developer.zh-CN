---
title: DevTools (Microsoft Edge 81) 中的新增功能
description: 3D 视图、Visual Studio与 Microsoft Edge 的集成等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 5edb89813b4c29ebd459d6849e116d1a8b92cf41
ms.sourcegitcommit: 3c588824bd8c7484fa31acae4857405a7eec5e36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2022
ms.locfileid: "12506991"
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
# <a name="whats-new-in-devtools-microsoft-edge-81"></a>DevTools (Microsoft Edge 81) 中的新增功能


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

以下部分列出了你可能从 Microsoft Edge DevTools 团队遗漏的公告。  查看公告以尝试 DevTools、Microsoft Visual Studio 代码扩展等新功能。  若要了解有关开发人员工具中的所有最新功能和最强大功能的最新动态，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download)并[在 Twitter 上关注我们](https://twitter.com/EdgeDevTools)。

### <a name="accessibility-improvements-to-the-devtools"></a>DevTools 的辅助功能改进

DevTools 团队为Chromium提供了 170 项更改，以解决 DevTools 中影响很大的颜色对比度、键盘和屏幕阅读器问题。  生成 Web 的每个开发人员都应能够使用 DevTools。

:::image type="content" source="../../images/2020/01/a11y-performance-tool.msft.gif" alt-text="使用键盘导航和屏幕阅读器改进的 DevTools 中的性能工具。" lightbox="../../images/2020/01/a11y-performance-tool.msft.gif":::

想要了解如何使您的网页可供所有用户访问？  下载[辅助功能Insights](https://accessibilityinsights.io)和 [webhint](https://webhint.io/docs/user-guide/extensions/extension-browser) 扩展，以便Microsoft Edge入门。

如果你使用屏幕阅读器或键盘浏览 DevTools，请通过[发推](https://twitter.com/intent/tweet?text=@EdgeDevTools)或单击**反馈**图标向我们发送你的反馈！

Chromium 问题 [#963183](https://crbug.com/963183)

### <a name="using-the-devtools-in-other-languages"></a>在其他语言中使用 DevTools

许多开发人员使用其他开发人员工具（如 StackOverflow 和 Visual Studio Code）的本机语言，而不仅仅是英语。  我们很高兴地宣布 DevTools 的本地化，你现在可以使用除英语以外的 10 种语言之一：

* 中文 (简体) - &#20013;&#25991;&#65288;&#31616;&#20307;&#65289;
* 中国 (传统) - &#20013;&#25991;&#65288;&#32321;&#39636;&#65289;
* 法语 – fran&#231;ais
* 德语 - 德国
* 意大利语 - 意大利语
* 日语 - &#26085;&#26412;&#35486;
* 韩语 - &#54620;&#44397;&#50612;
* 葡萄牙语 - 波尔图古&#234;s
* 俄语 – &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;
* 西班牙语 - espa&#241;ol

<!--
|  |  |
|:--- |:--- |
| Chinese (Simplified) - 中文(简体)（简体）| Chinese (Traditional) - 中文(繁體)（繁體）|
| French – français | German - deutsch |
| Italian - italiano | Portuguese - português |
| Korean - 한국어 | Japanese - 日本語 |
| Russian – русский | Spanish - español |
-->

DevTools 会自动匹配用于Microsoft Edge的`edge://settings/languages`语言。

如果希望Microsoft Edge使用一种语言，并且 DevTools 保持英语，请在 DevTools 中选择`F1`打开[设置](../../../customize/index.md#settings)并禁用 **Match 浏览器语言**。

:::image type="content" source="../../images/2020/01/localized-devtools.msft.png" alt-text="德语中的 DevTools。" lightbox="../../images/2020/01/localized-devtools.msft.png":::

**控制台** 消息未本地化。  只有 DevTools UI 中使用的字符串才会以用于Microsoft Edge的语言显示。

如果要使用不同于可用语言的 DevTools，请 [向我们发微博](https://twitter.com/intent/tweet?text=@EdgeDevTools) 或单击 **“发送反馈** ”图标。

Chromium问题 [#941561](https://crbug.com/941561)

### <a name="webhint-microsoft-edge-extension"></a>webhint Microsoft Edge扩展

通过 webhint Microsoft Edge 扩展，可以轻松扫描网页，并在 DevTools 中获取有关辅助功能、浏览器兼容性、安全性、性能等的反馈。  阅读有关内容的详细信息 [https://webhint.io](https://webhint.io)。

:::image type="content" source="../../images/2020/01/webhint-browser-extension.msft.png" alt-text="安装 Webhint 浏览器扩展时，DevTools 中的提示工具。" lightbox="../../images/2020/01/webhint-browser-extension.msft.png":::

[在Microsoft Edge中尝试 webhint 浏览器扩展](https://microsoftedge.microsoft.com/addons/detail/webhint/mlgfbihcfnkaenjpdcngdnhcpkdmcdee)。  安装扩展后，打开 DevTools 并选择 **“提示”** 工具。  在此处，运行可自定义的站点扫描。  转到 [webhint.io](https://webhint.io/docs/user-guide/extensions/extension-browser) 了解详细信息。

### <a name="3d-view"></a>3D 视图

通过浏览文[档对象模型 (DOM) ](https://developer.mozilla.org/docs/Web/API/Document_Object_Model)或 [z 索](https://developer.mozilla.org/docs/Web/CSS/z-index)引堆栈上下文，使用 **3D 视图**调试 Web 应用程序。

:::image type="content" source="../../images/2020/01/3dview.msft.png" alt-text="DevTools 中的 3D 视图。" lightbox="../../images/2020/01/3dview.msft.png":::

若要访问 3D 视图，请按`Ctrl`+`Shift``P`+下以打开命令菜单，开始键入`3d view`，然后选择 **“显示 3D 视图**”。

Microsoft Edge团队正在 UI 上与Chromium团队合作，并向 3D 视图添加更多功能，因此请使用 **“发送反馈**”图标！

Chromium问题 [#987787](https://crbug.com/987787)

### <a name="visual-studio-code-extensions"></a>Visual Studio Code扩展

DevTools 团队还发布了[一些用于Visual Studio Code](https://code.visualstudio.com)的扩展，可让你直接从文本编辑器使用 DevTools 的功能！ 请查看以下扩展：

#### <a name="elements-for-microsoft-edge"></a>用于Microsoft Edge的元素

通过添加Microsoft Edge Visual Studio Code扩展的元素，从Visual Studio Code中使用 [Elements](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) 工具。

:::image type="content" source="../../images/2020/01/elements-for-edge.msft.png" alt-text="Visual Studio Code中使用元素进行扩展Microsoft Edge元素的元素工具。" lightbox="../../images/2020/01/elements-for-edge.msft.png":::

有关详细信息，请查看[Microsoft Edge Visual Studio Code扩展的元素](../../../../visual-studio-code/elements-for-edge.md)。

#### <a name="debugger-for-microsoft-edge"></a>Microsoft Edge调试器

使用[用于VS Code Visual Studio Code扩展的Microsoft Edge工具](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)，直接从Visual Studio Code调试Microsoft Edge中运行的 JavaScript。

:::image type="content" source="../../images/2020/01/vscode-debugger.msft.png" alt-text="Visual Studio Code中Microsoft Edge扩展的调试器。" lightbox="../../images/2020/01/vscode-debugger.msft.png":::

有关详细信息，请查看[如何从Visual Studio Code调试Microsoft Edge](../../../../visual-studio-code/debugger-for-edge.md)。

#### <a name="webhint"></a>webhint

[Webhint](https://marketplace.visualstudio.com/items?itemName=webhint.vscode-webhint) Visual Studio Code 扩展用于`webhint`在编写网页时改进网页。  此扩展基于 `webhint` 分析在工作区文件上运行和报告诊断。

:::image type="content" source="../../images/2020/01/webhint-vscode-extension.msft.png" alt-text="在Visual Studio Code中分析 .tsx 文件的 webhint Visual Studio Code扩展名。" lightbox="../../images/2020/01/webhint-vscode-extension.msft.png":::

[详细了解Visual Studio Code webhint 扩展](https://webhint.io/docs/user-guide/extensions/vscode-webhint)。

### <a name="visual-studio-integration"></a>Visual Studio集成

在 Visual Studio 2019 版本 16.2 或更高版本中，使用 Visual Studio 调试器调试在 Microsoft Edge 中运行的 JavaScript。  [下载 Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 以试用此功能！

:::image type="content" source="../../images/2020/01/vs.msft.png" alt-text="Visual Studio，可以选择在 canary、Dev 或 Beta Microsoft Edge启动 Web 应用" lightbox="../../images/2020/01/vs.msft.png":::

[详细了解如何从Visual Studio调试Microsoft Edge](../../../../visual-studio/index.md)。

### <a name="tracking-prevention-console-messages"></a>跟踪预防控制台消息

跟踪防护是Microsoft Edge中的一项独特功能，可保护你免受以前未访问过的网站的跟踪。  默认跟踪防护设置是均衡模式，它阻止第三方跟踪器和已知的恶意跟踪器，以获得平衡隐私和 Web 兼容性的体验。  若要更深入地了解某些跟踪器被阻止时网页的兼容性，在阻止跟踪器时， **会在控制台** 中添加警告消息。

:::image type="content" source="../../images/2020/01/tracking-prevention.msft.png" alt-text="跟踪防护时控制台中的消息阻止了对跟踪器存储的访问。" lightbox="../../images/2020/01/tracking-prevention.msft.png":::

[详细了解如何跟踪防护以及隐私与 Web 兼容性之间的平衡](https://blogs.windows.com/msedgedev/2019/12/03/improving-tracking-prevention-microsoft-edge-79)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下各节将公布Microsoft Edge 81 中为开放源代码 Chromium项目提供的其他功能。

### <a name="moto-g4-support-in-device-mode"></a>设备模式下的 Moto G4 支持

[启用设备工具栏](../../../device-mode/index.md#simulate-a-mobile-viewport)后，从**设备**列表模拟 Moto G4 视区维度。

:::image type="content" source="../../images/2020/01/motog4.msft.png" alt-text="模拟 Moto G4 视区。" lightbox="../../images/2020/01/motog4.msft.png":::

单击 [“显示设备框架](../../../device-mode/index.md#show-device-frame) ”以显示视区周围的 Moto G4 硬件。

:::image type="content" source="../../images/2020/01/motog4frame.msft.png" alt-text="显示 Moto G4 硬件。" lightbox="../../images/2020/01/motog4frame.msft.png":::

相关功能：

*  打开 [命令菜单](../../../command-menu/index.md) 并运行 `Capture screenshot` 命令，以在启用 **“显示设备帧** ”) 后，创建包含 Moto G4 硬件 (的视区屏幕截图。
* [限制网络和 CPU](../../../device-mode/index.md#throttle-the-network-and-cpu) 以更准确地模拟移动用户的 Web 浏览条件。

Chromium问题 [#924693](https://crbug.com/924693)

### <a name="cookie-related-updates"></a>与 Cookie 相关的更新

#### <a name="blocked-cookies-in-the-cookies-pane"></a>Cookie 窗格中阻止的 Cookie

应用程序面板中的 Cookie 窗格现在显示带有黄色背景的阻止 Cookie。

:::image type="content" source="../../images/2020/01/blockedcookies.msft.png" alt-text="应用程序面板的 Cookie 窗格中阻止的 Cookie。" lightbox="../../images/2020/01/blockedcookies.msft.png":::

Chromium问题 [#1030258](https://crbug.com/1030258)  <!-- inaccessible  -->

#### <a name="cookie-priority-in-the-cookie-pane"></a>Cookie 窗格中的 Cookie 优先级

**网络**和**应用程序**工具中的 Cookie 表现在包含“**优先级”** 列。

> [!CAUTION]
> Chromium浏览器（如Microsoft Edge）是唯一支持 Cookie 优先级的浏览器。

Chromium问题 [#1026879](https://crbug.com/1026879)

#### <a name="edit-all-cookie-values"></a>编辑所有 Cookie 值

Cookie 表中的所有单元格现在都可以编辑， **但 Size** 列中的单元格除外，因为该列代表 Cookie 的网络大小（以字节为单位）。  有关每个列的说明，请参阅 [“字段](../../../storage/cookies.md#fields)”。

:::image type="content" source="../../images/2020/01/editcookie.msft.png" alt-text="编辑 Cookie 值。" lightbox="../../images/2020/01/editcookie.msft.png":::

#### <a name="copy-as-nodejs-fetch-to-include-cookie-data"></a>复制为Node.js提取以包含 Cookie 数据

若要`fetch`获取包含 Cookie 数据的表达式，请右键单击网络请求，然后选择 **CopyCopy** >  **作为Node.js提取**。

:::image type="content" source="../../images/2020/01/fetchcookies.msft.png" alt-text="复制为Node.js提取。" lightbox="../../images/2020/01/fetchcookies.msft.png":::

Chromium问题 [#1029826](https://crbug.com/1029826)

### <a name="more-accurate-web-app-manifest-icons"></a>更准确的 Web 应用清单图标

以前，应用程序面板中的“清单”窗格发送了自己的请求，以显示 Web 应用清单图标。  DevTools 现在显示Microsoft Edge使用的完全相同的清单图标。

:::image type="content" source="../../images/2020/01/manifesticons.msft.png" alt-text="清单窗格中的图标。" lightbox="../../images/2020/01/manifesticons.msft.png":::

Chromium问题 [#985402](https://crbug.com/985402)

### <a name="hover-on-css-content-properties-to-display-unescaped-values"></a>将鼠标悬停在 CSS 内容属性上以显示未转义的值

将鼠标悬停在属性的 `content` 值上以显示该值的未转义版本。

例如，在此 [演示](https://mathiasbynens.github.io/css-dbg-stories/css-escapes.html) 中，检查 `p::after` 伪元素时，“ **样式** ”窗格中会显示转义字符串：

:::image type="content" source="../../images/2020/01/escapedstring.msft.png" alt-text="转义的字符串。" lightbox="../../images/2020/01/escapedstring.msft.png":::

将鼠标悬停在值上 `content` 时，将显示未转义的值。

:::image type="content" source="../../images/2020/01/unescapedstring.msft.png" alt-text="未转义的值。" lightbox="../../images/2020/01/unescapedstring.msft.png":::

### <a name="more-detailed-source-map-errors-in-the-console"></a>控制台中更详细的源映射错误

控制台现在提供有关源映射无法加载或分析的原因的更多详细信息。  以前，它只是提供了一个错误，但没有解释出了什么问题。

:::image type="content" source="../../images/2020/01/sourcemap.msft.png" alt-text="控制台中的源映射加载错误。" lightbox="../../images/2020/01/sourcemap.msft.png":::

### <a name="setting-for-disabling-scrolling-past-the-end-of-a-file"></a>禁用滚动到文件末尾的设置

打开[设置](../../../customize/index.md#settings)，然后禁用 **PreferencesSourcesAllow** > **** >  **滚动过一端的文件**，以禁用默认 UI 行为，该行为允许你在 **“源**”面板中滚动到文件的末尾。

:::image type="content" source="../../images/2020/01/settings.msft.png" alt-text="禁用允许滚动到文件末尾。" lightbox="../../images/2020/01/settings.msft.png":::

:::image type="content" source="../../images/2020/01/scrollingsources.msft.png" alt-text="现在，在“源”面板中禁用滚动到文件的末尾。" lightbox="../../images/2020/01/scrollingsources.msft.png":::


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/blog/new-in-devtools-81)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
