---
title: 'DevTools (Microsoft Edge 86) '
description: 将键盘快捷方式与Visual Studio Code、模拟 Surface Duo 和 Samsung 则折叠、CSS 网格覆盖改进等匹配。
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
# <a name="whats-new-in-devtools-microsoft-edge-86"></a>DevTools 86 (Microsoft Edge中的新增) 


<!-- ====================================================================== -->
## <a name="announcements-from-the-microsoft-edge-devtools-team"></a>来自 Microsoft Edge 开发人员工具团队公告

[!INCLUDE [contact DevTools team note](../../includes/edge-whats-new-note.md)]

### <a name="match-keyboard-shortcuts-in-devtools-to-visual-studio-code"></a>将 DevTools 中的键盘快捷方式与Visual Studio Code

在 Microsoft Edge 86 中，你可以将 DevTools 中的键盘快捷方式与"代码"中的Microsoft Visual Studio[匹配](https://code.visualstudio.com)。

:::image type="content" source="../../media/2020/08/keyboard-shortcut.msft.png" alt-text="将 DevTools 中的键盘快捷方式与Visual Studio Code。" lightbox="../../media/2020/08/keyboard-shortcut.msft.png":::

若要激活此功能，请参阅在 [DevTools 中自定义键盘快捷方式](../../../customize/shortcuts.md)。

例如，用于暂停或继续运行脚本的键盘快捷方式在 [Visual Studio Code 为](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) `F5`。  使用 **DevTools (Default) ** 预设，DevTools `F8`中的同一快捷方式是 ，但在选择 **Visual Studio Code** 预设`F5`时，该快捷方式现在也是 。

Chromium问题 [#174309](https://crbug.com/174309)

### <a name="emulate-surface-duo-and-samsung-galaxy-fold"></a>模拟 Surface Duo 和 Samsung Galaxy Fold

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

现在，你能够在两台新设备上测试网站或应用的外观：[Surface Duo](https://www.microsoft.com/surface/devices/surface-duo) 和 [Samsung 一](https://www.samsung.com/us/mobile/galaxy-fold)Microsoft Edge。

为了帮助增强用于双屏和可折叠设备的网站或应用，在模拟设备时使用以下 [功能](../../../device-mode/index.md)：

* [跨越](../../../device-mode/dual-screen-and-foldables.md)，即你的网站（或应用）跨两个屏幕显示。

* [呈现接缝](/dual-screen/introduction#how-to-work-with-the-seam)，即两个屏幕之间的空间。

*  启用实验性 Web 平台 API 以访问新的 [CSS 媒体](/dual-screen/web/css-media-spanning) 屏幕跨越功能以及 [JavaScript getWindowSegments API](/dual-screen/web/javascript-getwindowsegments)。

:::image type="content" source="../../media/2020/08/surface-duo-device-emulation.msft.png" alt-text="Surface Duo 的设备仿真。" lightbox="../../media/2020/08/surface-duo-device-emulation.msft.png":::

若要启用此实验功能，请参阅打开[](../../../experimental-features/index.md#turning-an-experiment-on-or-off)或关闭实验，并选中模拟 **：支持双屏模式旁边的复选框**。

有关此功能详细信息，请参阅在 [DevTools](../../../device-mode/dual-screen-and-foldables.md) 中模拟双屏幕和可折叠Microsoft Edge设备。

Chromium问题： [#1054281](https://crbug.com/1054281)

### <a name="css-grid-overlay-improvements-and-new-experimental-grid-features"></a>CSS 网格覆盖改进和新的实验网格功能

感谢你提供有关改进的 CSS 网格覆盖的正面反馈。  CSS 网格覆盖现在默认启用，不需要你启用实验。

:::image type="content" source="../../media/2020/08/css-grid-overlay-article.msft.png" alt-text="article 元素的 CSS 网格覆盖。" lightbox="../../media/2020/08/css-grid-overlay-article.msft.png":::

> [!NOTE]
> 有关网格覆盖层详细信息，请参阅 [CSS 网格调试功能](../06/devtools.md#css-grid-debugging-features)。

开发人员Microsoft Edge团队和 Chrome DevTools 团队共同协作开发其他功能。  新功能包括多个覆盖，这些覆盖是永久性的，并且通过"元素"**** 工具上的新"布局"窗格**可配置**。

若要启用此实验功能，请参阅打开[](../../../experimental-features/index.md#turning-an-experiment-on-or-off)或关闭实验，并选中"重启后元素"中的"布局边栏"窗格中"启用新的 **CSS 网格调试功能 (配置**选项"旁边的复选框) 。

有关此功能详细信息，请参阅检查开发人员工具Microsoft Edge [CSS 网格](../../../css/grid.md)。

Chromium问题： [#1047356](https://crbug.com/1047356)

### <a name="table-copied-from-the-console-preserves-formatting"></a>从控制台复制的表保留格式

在 Microsoft Edge 85 或更早版本中，复制的格式丢失`console.table`。  如果从表控制台 API 复制并粘贴[](../../../console/api.md#table)了输出，则仅保留表的文本。

`table` Microsoft Edge 85 或更早版本中的控制台 API 输出：

:::image type="content" source="../../media/2020/08/console-table-beta.msft.png" alt-text="表 85 或Microsoft Edge控制台 API 输出。" lightbox="../../media/2020/08/console-table-beta.msft.png":::

`table` 粘贴到 Microsoft Edge 85 或更早版本中的控制台 API Visual Studio Code：

:::image type="content" source="../../media/2020/08/console-table-beta-paste-visual-studio-code.msft.png" alt-text="表 粘贴到 Microsoft Edge 85 或更早版本中的控制台 API Visual Studio Code。" lightbox="../../media/2020/08/console-table-beta-paste-visual-studio-code.msft.png":::

在 Microsoft Edge 86 或更高版本中，从**控制台**复制表时，格式设置现已保留。

`table` Microsoft Edge 86 或更高版本中的控制台 API 输出：

:::image type="content" source="../../media/2020/08/console-table-canary.msft.png" alt-text="表 86 或Microsoft Edge控制台 API 输出。" lightbox="../../media/2020/08/console-table-canary.msft.png":::

`table` 86 或更高版本Microsoft Edge的控制台 API 输出粘贴到Visual Studio Code：

:::image type="content" source="../../media/2020/08/console-table-canary-paste-visual-studio-code.msft.png" alt-text="表 86 或更高版本Microsoft Edge控制台 API 输出粘贴到 Visual Studio Code。" lightbox="../../media/2020/08/console-table-canary-paste-visual-studio-code.msft.png":::

Chromium问题： [#1115011](https://crbug.com/1115011)

### <a name="source-order-viewer-for-easier-accessibility-testing"></a>源订单查看器，便于辅助功能测试

:::image type="content" source="../../media/2020/06/experimental-tag-14px.msft.png" alt-text="实验性功能。":::

新的辅助功能帮助程序显示源中元素的顺序。

:::image type="content" source="../../media/2020/08/source-order-viewer.msft.png" alt-text="激活 显示源顺序。" lightbox="../../media/2020/08/source-order-viewer.msft.png":::

利用此功能，可以更轻松地测试屏幕阅读器和键盘用户体验网站或应用的方式。  屏幕阅读器和键盘导航取决于网站或应用的源代码中按特定顺序放置的内容，以便与呈现的页面匹配。  源顺序查看器显示呈现的页面和源代码之间潜在的顺序差异。

若要启用此实验功能 [，请参阅打开](../../../experimental-features/index.md#turning-an-experiment-on-or-off) 或关闭实验，并选中"启用源 **订单查看器"旁边的复选框**。

有关此实验详细信息，请参阅源 [订单查看器](../../../experimental-features/index.md#source-order-viewer)。

Chromium问题： [#1094406](https://crbug.com/1094406)

<!--
### DevTools language enhancements

Your feedback and internal discoveries uncovered which text strings used in the Microsoft Edge feedback should remain untranslated or create confusion when translated.

Microsoft Edge DevTools 85 and earlier in Traditional Chinese:

:::image type="content" source="../../media/2020/08/localization-improvements-chinese-complex-stable.msft.png" alt-text="Microsoft Edge DevTools in Traditional Chinese." lightbox="localization-improvements-chinese-complex-stable.msft.png":::

Microsoft Edge DevTools 86 or later in Traditional Chinese:

:::image type="content" source="../../media/2020/08/localization-improvements-chinese-complex-canary.msft.png" alt-text="Microsoft Edge DevTools in Japanese." lightbox="../../media/2020/08/localization-improvements-chinese-complex-canary.msft.png":::

To meet your translation needs, the Microsoft Edge DevTools team is focused on improving translation quality.

The current effort to improve translation quality enables easier support for more languages in the future.
-->

### <a name="highlight-all-search-results-in-elements-tool"></a>在"元素"工具中突出显示所有搜索结果

在 Microsoft Edge 84 和 85 中，"元素"工具的第一个搜索结果未突出显示****。  其余搜索结果已正确突出显示。

感谢你发送反馈并帮助改进Chromium。  您的反馈发现了开源[1103316](https://crbug.com/1103316)中的问题Chromium问题。

:::image type="content" source="../../media/2020/08/elements- search-highlight-fixed.msft.png" alt-text="在 84 或更高版本的&quot;元素&quot;Microsoft Edge突出显示第一个搜索结果。" lightbox="../../media/2020/08/elements- search-highlight-fixed.msft.png":::

此问题现已在所有版本的 Microsoft Edge 中Microsoft Edge。

Chromium问题： [#1103316](https://crbug.com/1103316)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

[!INCLUDE [contact DevTools team note](../../includes/chromium-whats-new-note.md)]

### <a name="new-media-tool"></a>新媒体工具

DevTools 现在在媒体工具中显示媒体 [播放器](../../../media-panel/index.md) 信息。

若要打开新的 **媒体** 工具，请选择"自定义和控制 **DevTools** `...` () > **更多工具** > **""媒体"**。

:::image type="content" source="../../media/2020/08/media-panel.msft.png" alt-text="新媒体工具。" lightbox="../../media/2020/08/media-panel.msft.png":::

在 DevTools 中的新 **媒体** 工具之前，有关视频播放器的日志记录和调试信息位于" **最近使用播放器"** 设置下。  若要打开 **"最近的玩家** "设置，请转到 `edge://media-internals` ，然后选择 **"玩家"** 工具。

更快查看实时内容并检查潜在问题，包括以下示例。

*  为什么丢弃帧？
*  为什么 JavaScript 以意外方式与玩家交互？

### <a name="capture-node-screenshots-using-the-elements-tool-context-menu"></a>使用"元素"工具上下文菜单捕获节点屏幕截图

现在，可以使用"元素"工具中的上下文菜单捕获 **节点屏幕截图** 。

例如，若要获取目录的屏幕截图，请右键单击 元素，然后选择捕获 **节点屏幕截图**。

:::image type="content" source="../../media/2020/08/capture-node-screenshot.msft.png" alt-text="捕获节点屏幕截图。" lightbox="../../media/2020/08/capture-node-screenshot.msft.png":::

Chromium问题： [#1100253](https://crbug.com/1100253)

### <a name="issues-tool-updates"></a>问题工具更新

控制台工具上的" **问题"警告** 栏现已替换为常规消息。

<!--todo: update this figure -->

:::image type="content" source="../../media/2020/08/issue-console-msg.msft.png" alt-text="控制台消息中的问题。" lightbox="../../media/2020/08/issue-console-msg.msft.png":::

默认情况下，第三方 Cookie 问题在"问题"工具中 **处于隐藏** 状态。  启用新的 **"包含第三方 Cookie 问题** "复选框以查看问题。

:::image type="content" source="../../media/2020/08/third-party-cookies.msft.png" alt-text="第三方 Cookie 问题复选框。" lightbox="../../media/2020/08/third-party-cookies.msft.png":::

Chromium问题：[1096481](https://crbug.com/1096481)、[1068116](https://crbug.com/1068116)、[1080589](https://crbug.com/1080589)

### <a name="emulate-missing-local-fonts"></a>模拟缺少的本地字体

打开 ["呈现"工具](../../../evaluate-performance/reference.md#analyze-rendering-performance-with-the-rendering-tool) 并使用新的 **"禁用本地字体"功能** 模拟规则中 `local()` 缺少的 `@font-face` 源。

例如，当`Rubik`字体安装在`@font-face src``local()`设备上且规则使用它作为字体时，Microsoft Edge使用设备中的本地字体文件。

启用 **"禁用** 本地字体"后，DevTools `local()` 将忽略字体，并提取网络的每个字体。

:::image type="content" source="../../media/2020/08/disable-font.msft.png" alt-text="模拟缺少的本地字体。" lightbox="../../media/2020/08/disable-font.msft.png":::

如果在开发过程中使用同一字体的两个不同副本，例如以下示例。

*  设计工具的本地字体。
*  代码的 Web 字体。

使用 **"禁用本地字体** "可以更轻松地：

*  调试并度量 Web 字体的加载性能和优化。
*  验证 CSS 规则的准确性 `@font-face` 。
*  发现设备上安装的本地版本与 Web 字体之间的差异。

Chromium问题： [#384968](https://crbug.com/384968)

### <a name="emulate-inactive-users"></a>模拟非活动用户

空闲 [检测 API](https://web.dev/idle-detection) 允许开发人员检测非活动用户，并响应空闲状态更改。  你现在可以使用 DevTools 在 **传感器** 工具中模拟用户状态和屏幕状态中的空闲状态更改，而不是等待实际空闲状态更改。  You can open the **Sensors** tool from the [Drawer](../../../customize/index.md#drawer).

:::image type="content" source="../../media/2020/08/emulate-idle.msft.png" alt-text="模拟非活动用户。" lightbox="../../media/2020/08/emulate-idle.msft.png":::

Chromium问题： [#1090802](https://crbug.com/1090802)

### <a name="emulate-prefers-reduced-data"></a>模拟 prefers-reduced-data

> [!NOTE]
> 在 Microsoft Edge 86 `edge://flags#enable-experimental-web-platform-features` 中，若要启用此功能，请转到 并打开"实验**性 Web 平台功能"** 标志。  模拟选项仅在启用标志时显示。

首选 [的缩减数据](https://drafts.csswg.org/mediaqueries-5#descdef-media-prefers-reduced-data) 媒体查询可检测减少数据的用户内容首选项。  如果选中，用户将接收使用较少数据的备用页面内容。

你现在可以使用 DevTools 模拟媒体 `prefers-reduced-data` 查询。

:::image type="content" source="../../media/2020/08/emulate-prefers-reduced-data.msft.png" alt-text="模拟首选的缩减数据。" lightbox="../../media/2020/08/emulate-prefers-reduced-data.msft.png":::

Chromium问题： [#1096068](https://crbug.com/1096068)

### <a name="support-for-new-javascript-features"></a>支持新的 JavaScript 功能

DevTools 现在更好地支持以下 JavaScript 语言功能。

| JavaScript 语言功能 | 详细信息 |
|:--- |:--- |
| [逻辑赋值运算符](https://v8.dev/features/logical-assignment) | DevTools 现在支持使用控制台和`&&=``||=``??=`源工具中的新 、 和 **运算符进行逻辑****分配。**  |
| 彩色数字 [分隔符](https://v8.dev/features/numeric-separators) | DevTools 现在在"源"工具中正确打印数字 **分隔** 符。  |

Chromium问题：[1086817](https://crbug.com/1086817)、[1080569](https://crbug.com/1080569)

### <a name="lighthouse-62-in-the-lighthouse-panel"></a>Lighthouse 面板中的 Lighthouse 6.2

**Lighthouse** 工具现在运行 Lighthouse 6.2。  有关更改的完整列表，请参阅 [Lighthouse 发行说明](https://github.com/GoogleChrome/lighthouse/releases/tag/v6.2.0)。

Chromium问题： [#772558](https://crbug.com/772558)

### <a name="deprecation-of-other-origins-listing-in-the-service-workers-pane"></a>在"服务工作者"窗格中弃用其他源列表

DevTools 现在从服务工作者窗格 (**** 应用程序工具>**服务**工作者窗格 ****) 提供了一个链接，用于查看来自其他来源的服务工作者的完整列表。  若要在不打开 DevTools 的情况下访问列表，请转到 `edge://service-worker-internals/?devtools`。

以前，DevTools 显示一个嵌套在"**** 应用程序工具""服务>**窗格下**的列表。

:::image type="content" source="../../media/2020/08/sw-other-origins.msft.png" alt-text="链接到其他源。" lightbox="../../media/2020/08/sw-other-origins.msft.png":::

Chromium问题： [#807440](https://crbug.com/807440)

### <a name="show-coverage-summary-for-filtered-items"></a>显示已筛选项目的范围摘要

DevTools 现在动态重新计算并显示覆盖信息的摘要。  在覆盖工具中应用筛选器时， [将触发动态](../../../coverage/index.md) 显示。  在 **覆盖工具** 始终显示所有覆盖信息的摘要之前。

在下图的第`344 kB of 1.7 MB (20%) used so far.  1.4 MB unused.``26.8 kB of 408 kB (7%) used so far.  381 kB unused.`一个中，摘要最初显示，在下图的第二个汇总中，将在应用 CSS 筛选后显示摘要。

覆盖摘要：

:::image type="content" source="../../media/2020/08/coverage-compare.msft.png" alt-text="覆盖摘要。" lightbox="../../media/2020/08/coverage-compare.msft.png":::

已筛选项目的范围摘要：

:::image type="content" source="../../media/2020/08/coverage-compare-css-filter.msft.png" alt-text="已筛选项目的范围摘要。" lightbox="../../media/2020/08/coverage-compare-css-filter.msft.png":::

Chromium问题： [#1061385](https://crbug.com/1090802)

### <a name="new-frame-details-view-in-application-panel"></a>应用程序面板中的新帧详细信息视图

DevTools 现在显示每个帧的详细视图。  若要访问详细视图，请单击"应用程序"工具中" **框架"菜单** 下的 **图** 文框。

:::image type="content" source="../../media/2020/08/frame-details.msft.png" alt-text="应用程序面板中框架的新详细视图。" lightbox="../../media/2020/08/frame-details.msft.png":::

Chromium问题： [#1093247](https://crbug.com/1093247)

#### <a name="frame-details-for-opened-windows"></a>打开的窗口的帧详细信息

打开窗口，弹出窗口现在也显示在框架树下。  打开的窗口的详细视图包括其他安全信息。

:::image type="content" source="../../media/2020/08/window-opener.msft.png" alt-text="打开的窗口的新框架详细视图。" lightbox="../../media/2020/08/window-opener.msft.png":::

Chromium问题： [#1107766](https://crbug.com/1107766)

#### <a name="security-and-isolation-information"></a>安全和隔离信息

安全上下文、 [Cross-Origin-Embedder-Policy (COEP) ](https://web.dev/coop-coep)和 [Cross-Origin-Opener-Policy (COOP) ](https://web.dev/coop-coep) 现在显示在帧详细信息中。

:::image type="content" source="../../media/2020/08/coep-coop.msft.png" alt-text="安全和隔离信息。" lightbox="../../media/2020/08/coep-coop.msft.png":::

将来，Microsoft Edge开发工具团队和 Chrome DevTools 团队计划向框架详细信息添加更多安全信息。

Chromium问题： [#1051466](https://crbug.com/1051466)

### <a name="elements-and-network-panel-updates"></a>元素和网络面板更新

#### <a name="accessible-color-suggestion-in-the-styles-pane"></a>"样式"窗格中的可访问颜色建议

DevTools 现在为低颜色对比度文本提供颜色建议。

在下面的示例中，具有 `h1` 低对比度文本。  若要修复此问题，请打开"样式 `color` "窗格中属性 **的颜色选取** 器。  展开"对比率 **"部分** 后，DevTools 将提供 AA 和 AAA 颜色建议。  选择建议的颜色以应用该颜色。

:::image type="content" source="../../media/2020/08/contrast-color-suggestion.msft.png" alt-text="颜色选取器建议 AA 和 AAA 颜色建议。" lightbox="../../media/2020/08/contrast-color-suggestion.msft.png":::

Chromium问题： [#1093227](https://crbug.com/1093227)

#### <a name="reinstate-properties-pane-in-the-elements-panel"></a>恢复"元素"面板中的"属性"窗格

" **属性** "窗格已返回。  [84 年 8 月Microsoft Edge弃用](../05/devtools.md#deprecation-of-the-properties-pane-in-the-elements-panel)。  开发人员Microsoft Edge团队和 Chrome DevTools 团队正在计划改进以检查元素的属性。

:::image type="content" source="../../media/2020/08/properties-pane.msft.png" alt-text="&quot;元素&quot;面板中的&quot;属性&quot;窗格。" lightbox="../../media/2020/08/properties-pane.msft.png":::

Chromium问题： <!-- [#1105205](https://crbug.com/1105205), --> [#1116085](https://crbug.com/1116085)

<!--
#### Human-readable X-Client-Data header values in the Network panel

When inspecting a network resource in the Network panel, DevTools now formats any `X-Client-Data` header values in **Headers** pane as code.

The `X-Client-Data` HTTP header contains a list of experiment IDs and Microsoft Edge flags that are enabled in your browser.  The raw header values look like opaque strings since the values are `base-64-encoded`, serialized [protocol buffers](https://developers.google.com/protocol-buffers).  To make the contents more transparent to developers, DevTools now shows the decoded values.

:::image type="content" source="../../media/2020/08/x-client-data.msft.png" alt-text="Human-readable `X-Client-Data` header values" lightbox="../../media/2020/08/x-client-data.msft.png":::

Chromium issue: [#1103854](https://crbug.com/1103854)
-->

#### <a name="autocomplete-custom-fonts-in-the-styles-pane"></a>在"样式"窗格中自动完成自定义字体

现在，在"样式"窗格中编辑属性时，导入的字体将添加到 CSS `font-family` **自动完成** 列表中。

例如，如果 `monospace` 是在本地计算机上安装的自定义字体，则它将显示在 CSS 完成列表中。  在早期版本的 Microsoft Edge 中，不显示字体。

:::image type="content" source="../../media/2020/08/font-auto-complete.msft.png" alt-text="自动完成自定义字体。" lightbox="../../media/2020/08/font-auto-complete.msft.png":::

Chromium问题： [#1106221](https://crbug.com/1106221)

#### <a name="consistently-display-resource-type-in-network-panel"></a>在网络面板中一致地显示资源类型

DevTools 现在一`/ Redirect`致地显示与原始网络请求相同的资源类型，当重定向 HTTP 状态代码**** 为 302 时 (附加到 Type 列) 值。

以前，DevTools 有时将类型更改为 `Other` 。

:::image type="content" source="../../media/2020/08/network-redirect.msft.png" alt-text="显示重定向资源类型。" lightbox="../../media/2020/08/network-redirect.msft.png":::

Chromium问题： [#997694](https://crbug.com/997694)

#### <a name="clear-buttons-in-the-elements-and-network-tools"></a>"元素和网络"工具中的"清除"按钮

以下文本框现在具有 **"清除"** 按钮：

*  "样式"窗格和"网络 **"** 工具中的 **筛选器** 文本框。
*  元素工具中的 DOM **搜索文本框** 。

单击" **清除"** 按钮可删除任何输入的文本。

**"** 元素"工具中的 **"清除"** 按钮：

:::image type="content" source="../../media/2020/08/clear-button-elements.msft.png" alt-text="清除&quot;元素&quot;面板中的按钮。" lightbox="../../media/2020/08/clear-button-elements.msft.png":::

**清除** 网络工具  **中的** 按钮：

:::image type="content" source="../../media/2020/08/clear-button-network.msft.png" alt-text="清除网络面板中的按钮。" lightbox="../../media/2020/08/clear-button-network.msft.png":::

Chromium问题： [#1067184](https://crbug.com/1067184)


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

If you're on Windows or macOS， consider using the [Microsoft Edge preview channels](https://www.microsoftedgeinsider.com/download) as your default development browser.  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-86)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
