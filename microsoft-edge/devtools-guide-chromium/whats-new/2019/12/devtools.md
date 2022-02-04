---
title: 'DevTools (Microsoft Edge 80) '
description: 辅助功能改进、在其他语言中使用 DevTools 等。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/13/2021
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
# <a name="whats-new-in-devtools-microsoft-edge-80"></a>DevTools (Microsoft Edge 80) 


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

以下各节列出了你可能从 DevTools 团队中错过Microsoft Edge通知。  查看通知以试用 DevTools、Microsoft Visual Studio代码扩展等中的新功能。  若要了解有关开发人员工具中的所有最新功能和最强大功能的最新动态，请下载 [Microsoft Edge 预览频道](https://aka.ms/microsoftedge)并[在 Twitter 上关注我们](https://aka.ms/twitter/edgedevtools)。

### <a name="accessibility-improvements-to-the-devtools"></a>对 DevTools 的辅助功能改进

DevTools 团队已对 Chromium 进行 170 次更改，以解决 DevTools 中的高影响颜色对比度、键盘和屏幕阅读器问题。  每个生成 Web 的开发人员都应能够使用 DevTools。

![具有键盘导航和屏幕阅读器改进的 DevTools 中的性能工具。](../../media/2019/12/a11y-performance-tool.msft.png)

想要了解如何使网页可供所有用户访问？  下载[辅助功能Insights](https://aka.ms/a11yinsights)和 [Webhint](https://aka.ms/webhint/browser-extension) 扩展Microsoft Edge开始操作。

如果你使用屏幕阅读器或键盘在 DevTools 中导航，请通过向我们发推文或[](https://aka.ms/tweet/edgedevtools)选择发送反馈[图标发送反馈](../../../contact.md)！

Chromium 问题 [#963183](https://crbug.com/963183)

### <a name="using-the-devtools-in-other-languages"></a>以其他语言使用 DevTools

许多开发人员使用其他开发人员工具（如 StackOverflow 和 Visual Studio Code，使用其本地语言，而不只是使用英语。  我们很高兴宣布 DevTools 的本地化，你现在可以使用英语之外 10 种语言之一：

* 简 (中文) - &#20013;&#25991;&#65288;&#31616;&#20307;&#65289;
* 繁 (中文) - &#20013;&#25991;&#65288;&#32321;&#39636;&#65289;
* 法语 – 法属&#231;语
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
| Chinese (Simplified) - 中文（简体）| Chinese (Traditional) - 中文（繁體）|
| French – français | German - deutsch |
| Italian - italiano | Portuguese - português |
| Korean - 한국어 | Japanese - 日本語 |
| Russian – русский | Spanish - español |
-->

转到 ， `edge://flags` 将" **启用本地化开发人员工具"标志** 设置为 **"已启用"**。  此外，将 **开发人员工具实验标志** 设置为 **已启用**。  重新启动Microsoft Edge并打开 DevTools。  <!-- Select `F1` in the DevTools or go to Settings > Experiments and check the **Match browser language** checkbox.  -->  DevTools 与用于在 中Microsoft Edge语言`edge://settings/languages`匹配。

:::image type="content" source="../../images/2019/12/localized-devtools.msft.png" alt-text="德语的 DevTools。" lightbox="../../images/2019/12/localized-devtools.msft.png":::

如果你想要以与可用版本不同的语言使用 DevTools，请通过我们的推文或单击"[](https://aka.ms/tweet/edgedevtools)发送反馈["图标](../../../contact.md)。

Chromium问题 [#941561](https://crbug.com/941561)

### <a name="webhint-microsoft-edge-extension"></a>webhint Microsoft Edge扩展

Webhint Microsoft Edge扩展允许你在 DevTools 中轻松扫描网页并获取有关辅助功能、浏览器兼容性、安全性、性能等的反馈。  有关详细信息，请参阅 [https://webhint.io](https://aka.ms/webhint)。

:::image type="content" source="../../images/2019/12/webhint-browser-extension.msft.png" alt-text="安装 Webhint 浏览器扩展时 DevTools 中的 Hints 工具。" lightbox="../../images/2019/12/webhint-browser-extension.msft.png":::

[尝试 webhint 浏览器扩展Microsoft Edge](https://aka.ms/webhint/edge-extension)。  安装扩展后，打开 DevTools，然后选择 **提示** 工具。  从此处运行可自定义的网站扫描。  请 [前往 webhint.io](https://aka.ms/webhint/browser-extension) 了解更多信息。

### <a name="3d-view"></a>3D 视图

使用 **3D 视图** 通过浏览文档对象模型或 [DOM (或 ](https://developer.mozilla.org/docs/Web/API/Document_Object_Model) [z 索引](https://developer.mozilla.org/docs/Web/CSS/z-index)) 调试 Web 应用程序。

:::image type="content" source="../../images/2019/12/3dview.msft.png" alt-text="DevTools 中的 3D 视图。" lightbox="../../images/2019/12/3dview.msft.png":::

若要访问 3D 视图，请转到 并确保 `edge://flags` 开发人员 **工具** 实验标记设置为 **已启用**。  重新启动Microsoft Edge并打开 DevTools。  在 `F1` DevTools 中选择或打开 **设置** > **Experiments 部分**，然后打开"启用 **3D 视图"** 复选框。  现在，按 ，`Ctrl` + `Shift``P` + 在 **3D 视图中键入 ，** 然后选择 **"显示 3D 视图"**。

We're working on the UI and adding more functionality to the 3D View so please send us your [feedback](../../../contact.md).

Chromium问题 [#987787](https://crbug.com/987787)

### <a name="visual-studio-code-extensions"></a>Visual Studio Code扩展

DevTools 团队还发布了一些适用于 Visual Studio Code 的扩展[](https://aka.ms/vscode)，让你可以直接从文本编辑器使用 DevTools 功能。 请查看以下扩展。

#### <a name="elements-for-microsoft-edge"></a>用于Microsoft Edge

通过将元素添加到 Visual Studio Code 扩展，从 Microsoft Edge [Visual Studio Code ](https://aka.ms/elements4code) 使用 Elements 工具。

:::image type="content" source="../../images/2019/12/elements-for-edge.msft.png" alt-text="中的 Elements Visual Studio Code使用 Elements for Microsoft Edge 扩展。" lightbox="../../images/2019/12/elements-for-edge.msft.png":::

有关详细信息，请查看适用于扩展[Microsoft Edge Visual Studio Code元素](../../../../visual-studio-code/elements-for-edge.md)。

#### <a name="debugger-for-microsoft-edge"></a>调试程序Microsoft Edge

使用[调试器Microsoft Edge](https://aka.ms/debugger4code) Visual Studio Code，直接从 Visual Studio Code 调试在 Microsoft Edge 中运行的 JavaScript。

:::image type="content" source="../../images/2019/12/vscode-debugger.msft.png" alt-text="用于 Microsoft Edge Extension 的调试Visual Studio Code。" lightbox="../../images/2019/12/vscode-debugger.msft.png":::

有关详细信息，请查看[如何从Microsoft Edge调试Visual Studio Code](../../../../visual-studio-code/debugger-for-edge.md)。

#### <a name="webhint"></a>webhint

[Webhint](https://aka.ms/webhint4code) Visual Studio Code`webhint`在编写网页时用于改进网页！ 此扩展将运行，并基于分析报告工作区文件的 `webhint` 诊断。

:::image type="content" source="../../images/2019/12/webhint-vscode-extension.msft.png" alt-text="Webhint Visual Studio Code扩展，用于分析 Visual Studio Code 中的 .tsx 文件。" lightbox="../../images/2019/12/webhint-vscode-extension.msft.png":::

[详细了解 webhint Visual Studio Code扩展](https://aka.ms/webhint/code-extension)。

### <a name="visual-studio-integration"></a>Visual Studio集成

在 Visual Studio 2019 版本 16.2 或更高版本中，使用 Visual Studio 调试程序调试在 Microsoft Edge 中运行的 JavaScript。  [下载Visual Studio 2019](https://aka.ms/vs/download) 以试用此功能。

:::image type="content" source="../../images/2019/12/vs.msft.png" alt-text="Visual Studio Canary、Dev 或 Beta Microsoft Edge启动 Web 应用的选项" lightbox="../../images/2019/12/vs.msft.png":::

[阅读我们的博客文章，了解如何从Microsoft Edge调试Visual Studio](https://aka.ms/vs/debug-edge)。

### <a name="tracking-prevention-console-messages"></a>跟踪防护控制台消息

跟踪防护是网站中Microsoft Edge一项功能，可阻止你在访问网站之前被网站跟踪。  默认跟踪防护设置为平衡模式，可阻止第三方跟踪器和已知的恶意跟踪器，从而获得平衡隐私和 Web 兼容性的体验。  为了让你深入了解阻止某些跟踪程序时网页的兼容性，Microsoft Edge 团队在控制台中添加了跟踪程序被阻止时警告消息。****

:::image type="content" source="../../images/2019/12/tracking-prevention.msft.png" alt-text="跟踪防护时控制台中的邮件阻止访问跟踪器的存储。" lightbox="../../images/2019/12/tracking-prevention.msft.png":::

[阅读有关跟踪防护以及隐私与 Web 兼容性之间平衡的详细信息](https://aka.ms/microsoftedge/tracking-prevention-blog)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下各节宣布 80 Microsoft Edge开放源代码管理项目中提供的其他Chromium功能。

### <a name="support-for-let-and-class-redeclarations-in-the-console"></a>支持控制台中的 let 和类重新声明

**控制台现在**支持重新声明 和 `let` `class` 语句。  对于使用控制台试验新 JavaScript 代码的 Web 开发人员来说，无法重新声明是常见的麻烦。

> [!WARNING]
> 在控制台外部或`let``class`单个控制台输入中的脚本中重新声明 或 语句仍会导致 。`SyntaxError`

例如，之前，当使用 重新声明本地变量 `let`时，控制台会出错：

:::image type="content" source="../../images/2019/12/letbefore.msft.png" alt-text="79 中的Microsoft Edge显示允许重新声明失败。" lightbox="../../images/2019/12/letbefore.msft.png":::

现在，控制台允许重新声明：

:::image type="content" source="../../images/2019/12/letafter.msft.png" alt-text="80 中的Microsoft Edge显示允许重新声明成功。" lightbox="../../images/2019/12/letafter.msft.png":::

Chromium问题 [#1004193](https://crbug.com/1004193)

### <a name="improved-webassembly-debugging"></a>改进的 WebAssembly 调试

DevTools 已开始支持 DEBUGG 调试标准，这意味着增加了对在 DevTools 中单步执行代码、设置断点和解析源语言中的堆栈跟踪的支持。

<!-- [TODO: Add this link back] -->
<!--Check out [Improved WebAssembly debugging in Microsoft Edge DevTools](201912Webassembly) for the full story.  -->

<!-- [TODO: Replace this image with screenshot in Edge] -->
<!--
:::image type="content" source="../../images/2019/12/wasm.msft.png" alt-text="The new DWARF-powered WebAssembly debugging." lightbox="../../images/2019/12/wasm.msft.png":::
-->

### <a name="network-panel-updates"></a>网络面板更新

#### <a name="request-initiator-chains-in-the-initiator-panel"></a>发起者面板中的请求发起人链

现在，你能够以嵌套列表查看网络请求的发起方和依赖项。  这可以帮助您了解请求资源的原因，或特定资源活动（如 (脚本）) 活动。

:::image type="content" source="../../images/2019/12/initiators.msft.png" alt-text="发起者面板中的请求发起人链。" lightbox="../../images/2019/12/initiators.msft.png":::

在 ["网络"面板中](../../../network/index.md)记录网络活动后，选择一个资源，然后转到发起 **人** 面板以查看 **请求发起人链**：

*  已 **检查的资源为** 粗体。  在以上屏幕截图中， `ai.2.min.js` 是已检查的资源。
*  已检查资源上方的资源是 **发起者**。  在以上屏幕截图中， `https://www.microsoftedgeinsider.com` 是 的发起人 `ai.2.min.js`。  换句话说，导致 `https://www.microsoftedgeinsider.com` 对 的网络请求 `ai.2.min.js`。
*  已检查资源下方的资源 **是依赖项**。  在以上屏幕截图中， `https://dc.services.visualstudio.com/v2/track` 是 的依赖项 `ai.2.min.js`。  换句话说，导致 `ai.2.min.js` 对 的网络请求 `https://dc.services.visualstudio.com/v2/track`。

> [!NOTE]
> 通过按住然后将鼠标悬停在网络 `Shift` 资源上，也可以访问发起方和依赖关系信息。  请参阅 [查看发起方和依赖项](../../../network/reference.md#display-initiators-and-dependencies)。

Chromium问题 [#842488](https://crbug.com/842488)

#### <a name="highlight-the-selected-network-request-in-the-overview"></a>在概述中突出显示所选的网络请求

选择要检查的网络资源后，"网络"面板现在在"概述"中为资源设置蓝色 **边框**。  这可以帮助您检测网络请求是早于还是晚于预期发生。

:::image type="content" source="../../images/2019/12/overview.msft.png" alt-text="突出显示已检查资源的&quot;概述&quot;窗格。" lightbox="../../images/2019/12/overview.msft.png":::

Chromium问题 [#988253](https://crbug.com/988253)

#### <a name="url-and-path-columns-in-the-network-panel"></a>网络面板中的 URL 和路径列

使用"**网络"****工具****中的新"** 路径"和"URL"列显示每个网络资源的绝对路径或完整 URL。

:::image type="content" source="../../images/2019/12/columns.msft.png" alt-text="&quot;网络&quot;面板中的新&quot;路径&quot;和&quot;URL&quot;列。" lightbox="../../images/2019/12/columns.msft.png":::

若要显示新列，请右键单击 **"瀑布** 表"标题，然后选择" **路径** "或" **URL"**。

Chromium问题 [#993366](https://crbug.com/993366)

#### <a name="updated-user-agent-strings"></a>更新User-Agent字符串

DevTools 支持通过"网络User-Agent设置 **自定义** 字符串。  the User-Agent string affects the `User-Agent` HTTP header attached to network resources， and the value of `navigator.userAgent`.

预定义User-Agent字符串已更新，以反映新式浏览器版本。

:::image type="content" source="../../images/2019/12/useragent.msft.png" alt-text="&quot;网络条件&quot;面板中的&quot;用户代理&quot;菜单。" lightbox="../../images/2019/12/useragent.msft.png":::

若要访问**网络条件**[，请打开命令菜单](../../../command-menu/index.md)并运行`Show Network Conditions`命令。

> [!NOTE]
> 还可以在 [设备User-Agent设置字符串](../../../device-mode/index.md#simulate-a-mobile-viewport)。

Chromium问题 [#1029031](https://crbug.com/1029031)

### <a name="audits-panel-updates"></a>审核面板更新

#### <a name="new-configuration-ui"></a>新配置 UI

配置 UI 具有新的响应式设计，并且限制配置选项已简化。  有关限制 UI 更改的信息，请参阅审核 [面板限制](https://github.com/GoogleChrome/lighthouse/blob/master/docs/throttling.md#devtools-audits-panel-throttling)。

:::image type="content" source="../../images/2019/12/start.msft.png" alt-text="新配置 UI。" lightbox="../../images/2019/12/start.msft.png":::

### <a name="coverage-tool-updates"></a>覆盖工具更新

#### <a name="per-function-or-per-block-coverage-modes"></a>按功能或按块覆盖模式

[覆盖工具](../../../coverage/index.md)具有新的下拉菜单，可让你指定是按函数还是按块**收集代码****覆盖数据**。  **每个块** 覆盖更加详细，但收集成本也更高。  默认情况下，DevTools **现在按** 功能范围使用。

> [!CAUTION]
> 你可能会注意到 HTML 文件的代码覆盖差异很大，具体取决于是按函数还是**按块模式**使用。****  在按 **函数模式使用** 时，HTML 文件中内联脚本被视为函数。  如果脚本完全运行，DevTools 将整个脚本标记为已用代码。  如果脚本完全不运行，DevTools 将脚本标记为未使用的代码。

:::image type="content" source="../../images/2019/12/modes.msft.png" alt-text="覆盖模式下拉菜单。" lightbox="../../images/2019/12/modes.msft.png":::

#### <a name="coverage-must-now-be-initiated-by-a-page-refresh"></a>现在必须通过页面刷新启动覆盖

由于覆盖数据不可靠，因此在未刷新页面的情况下切换代码覆盖已被删除。  例如，如果运行时在很长一段时间之前且 V8 垃圾回收器已清理它，函数可能会报告为未使用。

Chromium问题 [#1004203](https://crbug.com/1004203)


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://aka.ms/microsoftedge) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/blog/new-in-devtools-80)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
