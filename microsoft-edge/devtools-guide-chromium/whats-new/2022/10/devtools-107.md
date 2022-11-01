---
title: DevTools (Microsoft Edge 107) 中的新增功能
description: 使用 Playwright 自动执行 WebView2。 焦点模式活动栏图标具有工具提示。 命令面板的新快捷键。 内存工具加载更大的堆快照。 应用程序工具中的链接在高对比度模式下呈现。 以及更多。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/31/2022
ms.openlocfilehash: a7826955f756bf23e68fc318f5abb34441b32384
ms.sourcegitcommit: b15c540b2c48da3887d23e401e8543f297d178fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2022
ms.locfileid: "12849941"
---
# <a name="whats-new-in-devtools-microsoft-edge-107"></a>DevTools (Microsoft Edge 107) 中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="automate-webview2-with-playwright"></a>使用 Playwright 自动执行 WebView2

<!-- Subtitle: You can now use Playwright to automate and test web content in the Microsoft Edge WebView2 control. -->

[Playwright](https://playwright.dev) 是一个测试库，支持跨不同浏览器和平台进行可靠的端到端测试。  Playwright 一直支持在 Microsoft Edge 中自动执行和测试 Web 内容，但现在 Playwright 还支持测试 Microsoft Edge WebView2 控件。

Microsoft Edge WebView2 控件允许在本机应用中嵌入 web 技术(HTML、CSS 以及 JavaScript)。  现在可以使用 Playwright 测试 WebView2 中运行的 Web 内容。  若要开始，请参阅 [Playwright 的 WebView2 文档](https://playwright.dev/docs/webview2)。

另请参阅：
* [Microsoft Edge WebView2 简介](../../../../webview2/index.md)
* [在 Microsoft Edge 中使用 Playwright 自动执行和测试](../../../../playwright/index.md)
* [问题 17617：[功能] 添加 Playwright.WebView2.launch () ](https://github.com/microsoft/playwright/issues/17617)


<!-- ====================================================================== -->
## <a name="focus-mode-activity-bar-icons-show-text-label-on-mouse-hover"></a>焦点模式：活动栏图标在鼠标悬停时显示文本标签

<!-- Subtitle: When text labels are not visible in the Activity Bar, the name of the tool will appear while hovering over the icon. -->

从 Microsoft Edge 107 开始，在焦点模式下，将鼠标悬停在工具图标上时，活动栏现在会显示工具提示。  这些工具提示会立即显示，并帮助你快速识别和切换工具：

![活动栏工具提示](./devtools-107-images/activity-bar-tooltips.png)

当活动栏是水平时，当工具图标旁边没有文本标签时，将显示工具提示：

![水平活动栏图标的工具提示](./devtools-107-images/activity-bar-tooltips-horizontal.png)

另请参阅：
* [使用专注模式简化开发工具](../../../experimental-features/focus-mode.md)


<!-- ====================================================================== -->
## <a name="new-keyboard-shortcut-for-the-command-palette-experiment"></a>命令面板试验的新键盘快捷方式

<!-- Subtitle: Enable the Command Palette experiment in Microsoft Edge 107 and open it with Ctrl+Q (Command+Q on macOS). -->

在 [Microsoft Edge 106](../09/devtools-106.md#introducing-the-command-palette) 中，我们引入了命令面板，这是用于访问浏览器管理和开发人员工具命令的实验性功能。  在 Microsoft Edge 107 中，Windows、macOS 和 Linux 上用于打开命令面板的键盘快捷方式已从 `Shift``Ctrl``Spacebar`++更新为 。`Ctrl`+`Q`

若要启用命令面板试验，请参阅使用[命令面板](../../../experimental-features/edge-command-palette.md#enable-command-palette)_通过键盘运行命令中启用命令面板_。  启用命令面板试验后，按 `Ctrl`+`Q` 打开命令面板。

![命令面板](./devtools-107-images/command-palette.png)

感谢你就此问题提供反馈！  通过在 DevTools 存储库中的 [问题 73：[反馈] 命令面板试验](https://github.com/MicrosoftEdge/DevTools/issues/73) 中发布注释，让我们知道你希望在 Microsoft Edge 的未来版本中看到哪些命令！



<!-- ====================================================================== -->
## <a name="the-memory-tool-can-now-load-larger-heap-snapshots"></a>内存工具现在可以加载更大的堆快照

<!-- Subtitle: In Microsoft Edge 107, the Memory tool no longer reports "RangeError: Map maximum size exceeded" messages when loading a large heap snapshot. -->

在早期版本的 Microsoft Edge 中，在 **内存** 工具中加载大型堆快照时，快照将无法加载，并且会记录一 `RangeError: Map maximum size exceeded` 条消息到 **控制台**：

![RangeError 控制台消息](./devtools-107-images/heap-snapshot-rangeerror.png)

在 Microsoft Edge 107 中，此问题已修复。  **内存**工具现在可以成功加载大型堆快照。  此问题是由 V8 中的硬编码限制引起的， (浏览器) 的 JavaScript 引擎，该限制将映射元素的数量限制为 16M。  通过使用地图链接列表， **内存** 工具不再具有硬编码地图限制。

![用于大型堆快照的内存工具中的保留器](./devtools-107-images/retainers.png)

如果在加载大型堆快照时仍遇到问题，请在 [DevTools 存储库](https://github.com/MicrosoftEdge/DevTools/issues/new?assignees=&labels=bug&template=bug.md)中打开问题！

另请参阅：
* [使用内存工具记录堆快照](../../../memory-problems/heap-snapshots.md)
* [问题 9126：FixedArray) 支持的 Map (的硬编码内存限制](https://bugs.chromium.org/p/v8/issues/detail?id=9126)


<!-- ====================================================================== -->
## <a name="links-in-the-application-tool-render-better-in-high-contrast-mode"></a>应用程序工具中的链接在高对比度模式下呈现效果更好

<!-- Subtitle: In previous versions of Microsoft Edge, links in the Application tool weren't rendering correctly. In Microsoft Edge 107, this issue has been fixed. -->

在以前版本的 Microsoft Edge 中， **应用程序** 工具中的链接未在高对比度模式下正确呈现。  链接不可见，并且它们与高对比度设置中定义的颜色不同。  在 Microsoft Edge 107 中，此问题已修复。  **应用程序**工具中的链接现在与高对比度设置中定义的颜色匹配：

![高对比度模式下的链接](./devtools-107-images/high-contrast-links.png)
 
另请参阅：
* [Windows 高对比度模式](/fluent-ui/web-components/design-system/high-contrast)
* [调试渐进式 Web 应用 (PWA)](../../../progressive-web-apps/index.md)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge 107 还包括来自 Chromium 项目的以下更新：

* [使用键盘快捷方式切换浅色和深色主题](https://developer.chrome.com/blog/new-in-devtools-107/#toggle-themes)
* [支持 HAR 导入的完整发起程序信息](https://developer.chrome.com/blog/new-in-devtools-107/#har)
* [按 Enter 后启动 DOM 搜索](https://developer.chrome.com/blog/new-in-devtools-107/#search-type)
* [显示对齐内容 CSS 弹性框属性的开始和结束图标](https://developer.chrome.com/blog/new-in-devtools-107/#flexbox)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- > [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New in DevTools (Chrome 107)](https://developer.chrome.com/blog/new-in-devtools-107) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google). -->


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- [![Creative Commons License](../../../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0). -->
