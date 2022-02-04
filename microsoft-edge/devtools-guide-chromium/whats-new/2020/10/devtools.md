---
title: 'DevTools (Microsoft Edge 87 中的新增) '
description: 新的 CSS 网格调试工具、Webauthn 工具、可移动工具和计算边栏面板。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
---
<!-- Copyright Jecelyn Yeen

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="whats-new-in-devtools-microsoft-edge-87"></a>DevTools 87 (Microsoft Edge中的新增) 

[!INCLUDE [contact DevTools team note](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="improving-devtools-localization"></a>改进 DevTools 本地化

为了满足翻译需求，Microsoft Edge团队侧重于提高翻译质量。  从 Microsoft Edge版本 87 开始，多个字符串和术语已被锁定且不会更改，即使其他语言的 DevTools 的其余部分也一样。  受影响字符串和术语的列表包括：

*  **Lighthouse 工具中的**字符串。
*  `service worker`术语 。
*  一些 **网络工具** 筛选器，如 `URL`、 `XHR`、 `JS`和 `CSS`。
*  [$0](../../../console/utilities.md#recently-selected-element-or-javascript-object) 控制台实用程序 API。

[现在，](../../../console/utilities.md#recently-selected-element-or-javascript-object) 在控制台中 [为](../../../console/index.md) 使用 DevTools 本地化版本的用户提供 $0。   感谢全球开发人员社区帮助改进开发人员工具Microsoft Edge本地化。  继续 [发送本地化质量反馈](../../../contact.md) ，以改进在所有区域设置中对 DevTools 的支持。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1136655](https://crbug.com/1136655)。

:::image type="content" source="../../media/2020/10/bing-network-japanese.msft.png" alt-text="具有非本地化筛选器的网络工具。" lightbox="../../media/2020/10/bing-network-japanese.msft.png":::


<!-- ====================================================================== -->
## <a name="move-tools-between-top-and-bottom-panels"></a>在顶部和底部面板之间移动工具

DevTools 现在支持在顶部和底部面板之间移动工具。  通过同时查看两个工具的任意组合来自定义 DevTools 并提高工作效率。  例如，将 **"源"** 工具移动到****"源" (查看"元素"和"源") ****。  有关开放源代码项目中此功能的Chromium，请参阅 Issue [#1075732](https://crbug.com/1075732)。

若要将任何顶部工具移动到底部，请右键单击某个选项卡，然后选择" **移动到底部"**。

:::image type="content" source="../../media/2020/10/move-to-bottom.msft.png" alt-text="移至底部。" lightbox="../../media/2020/10/move-to-bottom.msft.png":::

若要将任何底部工具移动到顶部，请右键单击某个选项卡，然后选择" **移动到顶部"**。

:::image type="content" source="../../media/2020/10/move-to-top.msft.png" alt-text="移动到顶部。" lightbox="../../media/2020/10/move-to-top.msft.png":::


<!-- ====================================================================== -->
## <a name="save-and-export-using-the-network-console"></a>使用网络控制台保存和导出

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

网络 **控制台** 工具现在改进了与 [Postman v2.1](https://schema.getpostman.com/json/collection/v2.1.0/docs/index.html) 和 [OpenAPI v2 架构](https://swagger.io/specification/v2) 的兼容性。  若要启用实验，请参阅打开或关闭 [实验](../../../experimental-features/index.md#turning-an-experiment-on-or-off) ，并选中"启用网络控制台 **"旁边的复选框**。  有关网络控制台 **详细信息，请参阅**启用 [网络控制台实验功能](../../../experimental-features/index.md#enable-network-console)。

此实验现在支持以下操作：

*  保存和导出集合和环境。
*  在网络控制台工具中编辑和导出 **环境变量** 集。

有关开放源代码项目中此功能Chromium，请参阅问题 [#1093687](https://crbug.com/1093687)。

输入新环境的名称：

:::image type="content" source="../../media/2020/10/network-console-environments-new-name.msft.png" alt-text="输入新环境的名称。" lightbox="../../media/2020/10/network-console-environments-new-name.msft.png":::

选择新环境的格式：

:::image type="content" source="../../media/2020/10/network-console-environments-new-format.msft.png" alt-text="选择新环境的格式。" lightbox="../../media/2020/10/network-console-environments-new-format.msft.png":::


<!-- ====================================================================== -->
## <a name="improved-css-grid-tooling"></a>改进的 CSS 网格工具

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

开发人员Microsoft Edge工具现在支持以下功能来检查、查看和调试 CSS 网格。

*  使用 Inspect 工具显示简化的网格 **覆盖，或** 获取有关永久性覆盖的更多详细信息。

*  若要启用持久网格覆盖，请单击"元素"工具中网格容器元素旁边的网格图标，**** 或单击"布局 **"工具中的**网格。

*  你可以为多个网格启用永久性覆盖。

*  新的 **布局** 工具允许你轻松切换网格覆盖，并为每个覆盖层配置外观和内容。

默认情况下，这些功能为打开状态。  有关功能详细信息，请参阅 [CSS 网格](../../../css/grid.md)。  有关开放源代码项目中此功能的Chromium，请参阅问题 [#1047356](https://crbug.com/1047356)。  此外，Microsoft Edge开发人员工具团队正在与 Chrome DevTools 团队和 Chromium 社区协作，向 DevTools 添加新的弹性框工具功能。  有关开放源代码项目中弹性Chromium的更新，请参阅 Issue [#1136394](https://crbug.com/1136394)。

:::image type="content" source="../../media/2020/10/grid-layout-pane.msft.png" alt-text="具有网格的布局工具。" lightbox="../../media/2020/10/grid-layout-pane.msft.png":::


<!-- ====================================================================== -->
## <a name="customize-keyboard-shortcuts-in-settings"></a>在“设置”中自定义键盘快捷方式

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

现在，你可以为 DevTools 中任何操作自定义键盘快捷方式。  自Microsoft Edge版本 84 起，你可以选择在 Visual Studio Code 和 **DevTools (键盘**) [预设。](../../../customize/shortcuts.md)****  从 Microsoft Edge版本 87 开始，你可以打开启用**键盘快捷方式编辑器**实验以进一[步自定义键盘快捷方式](../../../customize/shortcuts.md#edit-the-keyboard-shortcut-for-a-devtools-action)。

若要启用实验 [，请参阅打开](../../../experimental-features/index.md#turning-an-experiment-on-or-off) 或关闭实验，并选中启用键盘快捷方式 **编辑器旁边的复选框**。  有关自定义和编辑快捷方式的信息，请参阅编辑 [DevTools](../../../customize/shortcuts.md#edit-the-keyboard-shortcut-for-a-devtools-action) 中任何操作键盘快捷方式。  有关开放源代码项目中此功能Chromium，请参阅问题 [#174309](https://crbug.com/174309)。

:::image type="content" source="../../media/2020/10/custom-shortcut-pause-script.msft.png" alt-text="用于暂停脚本的自定义快捷方式。" lightbox="../../media/2020/10/custom-shortcut-pause-script.msft.png":::

<!-- [enable the keyboard shortcut editor](../../../experimental-features/index.md#enable-keyboard-shortcut-editor) -->


<!-- ====================================================================== -->
## <a name="introducing-the-microsoft-edge-tools-for-visual-studio-code-extension"></a>Microsoft Edge工具扩展Visual Studio Code介绍

现在 **，Visual Studio Code**和 **Network for Visual Studio Code** 的 Elements 将合并到新的 Microsoft Edge [Developer Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) 扩展中。  将 Microsoft Edge DevTools 用于以下活动，而无需保留Microsoft Visual Studio代码。

*  调试 DOM
*  编辑 CSS
*  检查网络流量

借助扩展，Microsoft Edge浏览器，连接到浏览器的现有实例，或者直接从编辑器使用无头浏览器。  若要开始提供和归档有关此扩展的反馈问题，请参阅 Microsoft Edge [上的 Visual Studio Code 开发人员](https://github.com/Microsoft/vscode-edge-devtools)GitHub。

在完整浏览器模式下使用扩展：

:::image type="content" source="../../media/2020/10/microsoft-edge-tools-full-browser.msft.png" alt-text="在完整浏览器模式下使用扩展。" lightbox="../../media/2020/10/microsoft-edge-tools-full-browser.msft.png":::

在无头模式下使用扩展：

:::image type="content" source="../../media/2020/10/microsoft-edge-tools-headless.msft.png" alt-text="在无头模式下使用扩展。" lightbox="../../media/2020/10/microsoft-edge-tools-headless.msft.png":::


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

[!INCLUDE [contact DevTools team note](../../includes/chromium-whats-new-note.md)]

### <a name="new-webauthn-tool"></a>新 WebAuthn 工具

在早期版本的 Microsoft Edge，没有本机 WebAuthn 调试支持。  您需要物理验证器来使用 Web 身份验证 [API 测试 Web 应用程序](https://w3c.github.io/webauthn)。  使用新的 **WebAuthn** 工具，无需使用任何物理验证器即可执行以下操作：

*  模拟验证器。
*  自定义验证器的属性。
*  检查验证器状态。

有关 **WebAuthn 功能详细信息** ，请参阅 [模拟验证器和调试 WebAuthn](../../../webauthn/index.md)。

您可以使用新的 [WebAuthn](../../../webauthn/index.md) 工具模拟验证器[并](https://w3c.github.io/webauthn)调试 Web 身份验证 API。  若要打开 **WebAuthn** 工具，请单击"自定义和控制 **DevTools** `...` " () "图标>**更多** **toolsWebAuthn** > "。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1034663](https://crbug.com/1034663)。

打开 **WebAuthn** 工具：

:::image type="content" source="../../media/2020/10/more-tools-webauthn.msft.png" alt-text="打开 WebAuthn 工具。" lightbox="../../media/2020/10/more-tools-webauthn.msft.png":::

**WebAuthn** 工具：

:::image type="content" source="../../media/2020/10/webauthn-enable-virtual-auth.msft.png" alt-text="WebAuthn 工具。" lightbox="../../media/2020/10/webauthn-enable-virtual-auth.msft.png":::

### <a name="elements-tool-updates"></a>“元素”工具更新

#### <a name="view-the-computed-sidebar-pane-in-the-styles-pane"></a>查看"样式"窗格中的"计算边栏"窗格

切换 **"样式"** 窗格中的"计算 **"** 窗格。  默认情况下 **，"****样式"窗格中**的计算窗格是折叠的。  若要切换它，请单击按钮。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1073899](https://crbug.com/1073899)。

打开 **"计算边栏"** 窗格：

:::image type="content" source="../../media/2020/10/computed-sidebar-pane.msft.png" alt-text="打开&quot;计算边栏&quot;窗格。" lightbox="../../media/2020/10/computed-sidebar-pane.msft.png":::

" **计算边栏"** 窗格：

:::image type="content" source="../../media/2020/10/computed-sidebar-pane-open.msft.png" alt-text="计算边栏窗格。" lightbox="../../media/2020/10/computed-sidebar-pane-open.msft.png":::

#### <a name="grouping-css-properties-in-the-computed-panel"></a>在计算面板中对 CSS 属性进行分组

若要以更少的滚动量查看应用的 CSS，请按"计算"窗格中的类别对 CSS **属性进行** 分组。  在检查 CSS 时，还可以有选择地专注于一组相关属性。  从" **元素"** 工具中，选择一个元素。  若要对 (或取消) CSS 属性进行分组，请切换 **"组"** 复选框。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1096230](https://crbug.com/1096230)、 [#1084673](https://crbug.com/1084673) 和 [#1106251](https://crbug.com/1106251)。

:::image type="content" source="../../media/2020/10/grouping-css-prop.msft.png" alt-text="对 CSS 属性进行分组。" lightbox="../../media/2020/10/grouping-css-prop.msft.png":::

### <a name="lighthouse-64-in-the-lighthouse-tool"></a>Lighthouse 工具中的 Lighthouse 6.4

**Lighthouse** 工具现在运行 Lighthouse 6.4。  有关更改的完整列表，请参阅 [Lighthouse 发行说明](https://github.com/GoogleChrome/lighthouse/releases/v6.4.1)。  有关开放源代码项目中此功能Chromium，请参阅问题 [#772558](https://crbug.com/772558)。

### <a name="performancemark-events-in-the-timings-section"></a>"计时"部分中的 performance.mark () 事件

现在 **，性能** 工具中的录制的 ["计时"](../../../evaluate-performance/reference.md) 部分会标记 `performance.mark()` <!--[performance mark](https://jec.fyi/demo/perf-mark) -->事件。  若要试用此功能并度量 JavaScript 代码的性能，请向 `performance.mark()` 代码添加事件。  例如，以下代码 `for` 段在循环之前和之后添加标记，该循环使用增量 7 从 0 循环到 1000。

```javascript
performance.mark('start');
for (var i = 0; i < 1000; i+=7;){
  console.log(i);
}
performance.mark('end');
```

然后，打开 ["性能"](../../../evaluate-performance/reference.md) 工具并查看" **计时** "部分以记录 JavaScript 代码。  您 `performance.mark()` 添加的事件现在将显示在录制中。

:::image type="content" source="../../media/2020/10/perf-mark.msft.png" alt-text="Performance.mark 事件。" lightbox="../../media/2020/10/perf-mark.msft.png":::

### <a name="new-resource-type-and-url-filters-in-the-network-tool"></a>网络工具中的新资源类型和 URL 筛选器

使用 Network `resource-type` 工具 `url` 中的 new 和 **关键字** 筛选网络请求。  例如，使用 `resource-type:image` 将焦点放在作为图像的网络请求上。

:::image type="content" source="../../media/2020/10/network-resource-type-filter.msft.png" alt-text="资源类型筛选器。" lightbox="../../media/2020/10/network-resource-type-filter.msft.png":::

若要发现更多特殊关键字（如 `resource-type` 和 `url`），请参阅 [按属性筛选请求](../../../network/reference.md#filter-requests-by-properties)。  有关开放源代码项目中此功能Chromium更新，请参阅问题 [#1121141](https://crbug.com/1121141) 和 [#1104188](https://crbug.com/1104188)。

### <a name="frame-details-view-updates"></a>框架详细信息视图更新

#### <a name="display-coep-and-coop-reporting-to-endpoint"></a>向终结点显示 COEP 和 COOP 报告

在"安全与隔离"部分 (跨源嵌入器策略) 和跨源打开器策略 (COOP) `reporting to` **&** 终结点。  报告 [API](https://developer.mozilla.org/docs/Web/API/Reporting_API) 定义 `Report-To`一个新的 HTTP 标头，它为你提供了一种指定浏览器服务器终结点以发送警告和错误的方法。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1051466](https://crbug.com/1051466)。

:::image type="content" source="../../media/2020/10/https_first_party_test_glitch_me_coop-1.msft.png" alt-text="报告到终结点。" lightbox="../../media/2020/10/https_first_party_test_glitch_me_coop-1.msft.png":::

#### <a name="display-coep-and-coop-report-only-mode"></a>显示 COEP 和 COOP 仅报告模式

DevTools 现在显示 `report-only` 设置为模式的 COEP 和 COOP `report-only` 的标签。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1051466](https://crbug.com/1051466)。

:::image type="content" source="../../media/2020/10/https_first_party_test_glitch_me_coop-2.msft.png" alt-text="仅报告模式标签。" lightbox="../../media/2020/10/https_first_party_test_glitch_me_coop-2.msft.png":::

### <a name="view-and-fix-color-contrast-issues-in-the-css-overview-tool"></a>在 CSS 概述工具中查看和修复颜色对比度问题

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

CSS **概述** 工具现在显示页面上具有颜色对比度问题的元素列表。  CSS [概述可访问颜色演示](https://css-overview-accessible-colors-demo.glitch.me) 页面包含颜色对比度问题的示例。

若要启用此实验，**请在** > "设置 **"下**选中 **"CSS 概述"** 复选框。  若要查看具有颜色对比度问题的元素的列表，请在"对比度问题" **上单击"** 文本 **"**。  若要在"元素"工具 **中打开元素** ，请单击列表中的元素。  为了帮助修复对比度问题，Microsoft Edge开发人员工具[自动提供颜色建议](../08/devtools.md#accessible-color-suggestion-in-the-styles-pane)。  有关开放源代码项目中此功能Chromium，请参阅问题 [#1120316](https://crbug.com/1120316)。

:::image type="content" source="../../media/2020/10/css-overview.msft.png" alt-text="低色对比度问题。" lightbox="../../media/2020/10/css-overview.msft.png":::


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows 或 macOS，请考虑使用 [ Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-87)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
