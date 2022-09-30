---
title: DevTools (Microsoft Edge 106) 中的新增功能
description: 命令面板简介。 筛选并自动修复 DevTools 中用于Visual Studio Code的代码问题。 DevTools 现在在缓存源图时使用较少的磁盘空间。 Chromium颜色主题已被弃用。 焦点模式和高对比度模式中的辅助功能改进。 以及更多。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/29/2022
ms.openlocfilehash: 1a57d16507f5407b40348db1a372ee082cf53411
ms.sourcegitcommit: 45320a2c51db77c1e1d77ea04421a8a470ee5d85
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2022
ms.locfileid: "12762691"
---
# <a name="whats-new-in-devtools-microsoft-edge-106"></a>DevTools (Microsoft Edge 106) 中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="introducing-the-command-palette"></a>命令面板简介

<!-- Subtitle: Your favorite browser management and DevTools commands in one place. -->

在 Microsoft Edge 106 中，现在可以启用和使用命令面板试验。  通过命令面板，只需一个键盘快捷方式就可以访问浏览器管理和开发人员工具命令： `Ctrl`+`Shift`+`Spacebar`


若要启用命令面板试验，请执行以下操作：

1. 转到 `edge://flags`。  然后在 **“搜索标志** ”文本字段中，开始键入 **命令面板**。

1. 在 **“命令面板** ”下拉菜单中，选择 **“已启用**”

   <!-- screenshot directly in What's New, to show where to see the keyboard shortcut along with version:-->
   ![版本 106 的标志页中命令面板的键盘快捷方式](./devtools-106-images/command-palette-flags-shortcut-106.png)

   请注意键盘快捷方式，该快捷方式显示在页面上的 **“命令面板** ” `edge://flags` 部分中。
   <!--
   *  In Microsoft Edge 106 and most releases of 107, the keyboard shortcut is `Ctrl`+`Shift`+`Spacebar`.
   *  In Microsoft Edge 108 and later, the shortcut is `Ctrl`+`Q`. -->

1. 单击 **“重启** ”按钮，在选择“ **已启用**”时，该按钮显示在右下角。

   有关详细信息，请参阅使用_命令面板通过键盘在运行命令_中[启用命令面板](../../../experimental-features/edge-command-palette.md#enable-command-palette)。


若要在启用试验后快速访问可用的浏览器管理命令和 DevTools 命令：

1. 在 Microsoft Edge (中，无论是否使用 DevTools 打开) ，请按 。`Ctrl`+`Shift`+`Spacebar`

1. 开始键入。  命令根据输入字符进行筛选，并分组为“ **建议**”、“ **历史记录**”和 **“DevTools**”等类别：

   ![Microsoft Edge 命令面板](./devtools-106-images/command-palette.png)

1. 若要缩小筛选范围以仅列出 DevTools 命令，请 **>** 键入大于 () 字符：

   ![Microsoft Edge 命令面板输入“>”以选择 DevTools 命令](./devtools-106-images/command-palette-devtools.png)


通过在 **MicrosoftEdge/DevTools** 存储库中发布注释，让我们知道你希望在 Microsoft Edge 的未来版本中看到哪些命令[：[反馈] 命令面板试验](https://github.com/MicrosoftEdge/DevTools/issues/73)！

另请参阅：
* [使用命令面板通过键盘运行命令](../../../experimental-features/edge-command-palette.md)


<!-- ====================================================================== -->
## <a name="filter-and-automatically-fix-code-issues-in-devtools-for-visual-studio-code"></a>筛选并自动修复 DevTools 中用于Visual Studio Code的代码问题

<!-- Subtitle: Let Visual Studio Code fix web issues for you or tell it never to bother you about them again. -->
 
适用于Visual Studio Code的 Microsoft Edge DevTools 扩展现在提供了**快速修复**选项，允许你自动解决问题。

若要访问 **快速修复** 选项，请执行以下操作：

1. 将鼠标悬停在 DevTools 扩展报告的问题上，该问题由代码中的波浪下划线指示。  问题旁边会显示一个灯泡图标。

1. 单击灯泡 (![灯泡图标](./devtools-106-images/lightbulb-icon.png)) 图标。  将显示 **“快速修复** ”菜单：

   ![快速修复选项](./devtools-106-images/quick-fix-options.png)

1. 选择要使用哪种 **快速修复** 来解决问题或停止将其报告为问题。  选择忽略问题会自动创建一个 `.hintrc` 文件，该文件指示扩展名忽略此问题类型，而不是再次报告它。

另请参阅：
* _Microsoft Edge DevTools 扩展中针对 Visual Studio Code_ 的[自动快速修复和问题筛选](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#automated-quick-fixes-and-issue-filtering)


<!-- ====================================================================== -->
## <a name="devtools-now-uses-less-disk-space-when-caching-sourcemaps"></a>DevTools 现在在缓存源图时使用较少的磁盘空间

<!-- Subtitle: In Microsoft Edge 106, sourcemaps are now removed from IndexedDB storage if they haven't been accessed in 30 days. -->

从 [Microsoft Edge 101](../../../whats-new/2022/04/devtools-101.md#source-maps-are-now-cached-with-indexeddb) 开始，DevTools 开始在 IndexedDB 中缓存源地图，以减少提取源地图的网络请求量。  但是，如果从未删除这些源映射，此更改可能会占用大量磁盘空间。

在 Microsoft Edge 106 中，通过删除 30 天内未从 IndexedDB 存储访问的任何源映射，解决了此问题。  此外，还不再缓存从 `localhost` 中提供的源映射。  感谢你向我们发送有关此问题的反馈！

若要了解 DevTools 如何提取和缓存源地图，请在[源地图监视器工具](../../../source-maps-monitor/source-maps-monitor-tool.md)中观看 **“负载状态**”列。  首次加载网页时， **源地图监视器** 工具显示源映射尚未缓存：

![首次加载时，源地图监视器工具](./devtools-106-images/source-maps-indexeddb-first-load.png)

刷新网页时， **源地图监视器** 工具显示使用了缓存的源映射：

![源地图监视器工具，第二次加载时](./devtools-106-images/source-maps-indexeddb-second-load.png)

若要清除 IndexedDB 缓存并强制 DevTools 重新加载源映射，请在命令菜单中运行 **Clear source maps 缓存** 命令。  请参阅 [命令菜单中的“运行”命令](../../../command-menu/index.md)。

有关历史记录，请参阅 [问题 89](https://github.com/MicrosoftEdge/DevTools/issues/89)。

另请参阅：
* [源映射现在与 IndexedDB 一起缓存](../../2022/04/devtools-101.md#source-maps-are-now-cached-with-indexeddb)_在 DevTools (Microsoft Edge 101) _


<!-- ====================================================================== -->
## <a name="chromium-color-themes-have-been-deprecated"></a>Chromium颜色主题已弃用

<!-- Subtitle: Users of Chromium themes in DevTools will be automatically migrated to the default dark or light theme for a more reliable experience. -->

为了提高可靠性，已弃用**Chromium浅****色和Chromium深色**主题。  以前选择过这些主题的用户将分别自动迁移到 **Light+** 或 **Dark+** 主题：

**Light+** 主题中的 DevTools： 

![Light+ 主题中的 DevTools](./devtools-106-images/light-plus-theme.png)

**深色+** 主题中的 DevTools：

![深色+ 主题中的 DevTools](./devtools-106-images/dark-plus-theme.png)

有许多 DevTools 颜色主题可供选择，例如 **Monokai** 和 **Solarized**。  若要更改 DevTools 中的颜色主题，请单击 **“设置** (![”图标](../../../media/settings-gear-icon-light-theme.png)) 按钮，然后在 **“首选项”** 页的 **“主题** ”下拉菜单中，选择一个主题：

![将 DevTools 主题设置为 Monokai](./devtools-106-images/set-theme-monokai.png)

另请参阅：
* [将颜色主题应用于开发工具](../../../customize/theme.md)


<!-- ====================================================================== -->
## <a name="accessibility-improvements-in-focus-mode-and-high-contrast-mode"></a>焦点模式和高对比度模式中的辅助功能改进

<!-- Subtitle: The new Dock location and Activity Bar location buttons in Focus Mode now work better with screen readers, and computed styles are easier to see in high contrast mode. -->


#### <a name="dock-location-and-activity-bar-location-buttons-in-focus-mode-now-work-better-with-screen-readers"></a>焦点模式下的停靠位置和活动栏位置按钮现在在屏幕阅读器中效果更好

在 Microsoft Edge 105 中，焦点模式收到了多项改进，包括新的 **停靠位置** 和 **活动栏位置** 按钮。  在 Microsoft Edge 106 中，这些新按钮现在更适用于辅助技术，例如屏幕阅读器。

屏幕阅读器现在将播报哪个 **“停靠位置** ”按钮或当前选择了哪个 **活动栏位置** 按钮，以及表示可用位置选项的按钮数：

![焦点模式下重新设计的“停靠”菜单](./devtools-106-images/focus-mode-redesigned-docking-menu.png)

另请参阅：
* [使用专注模式简化开发工具](../../../experimental-features/focus-mode.md)
* [使用辅助技术导航开发工具](../../../accessibility/navigation.md)
* 焦点模式：在 _DevTools (Microsoft Edge 105) 中_[改进了 DevTools、活动栏和快速视图的位置控制](../../../whats-new/2022/09/devtools-105.md#focus-mode-improved-location-controls-for-devtools-activity-bar-and-quick-view)。


#### <a name="computed-styles-are-easier-to-see-in-high-contrast-mode"></a>计算样式在高对比度模式下更易于查看

在高对比度模式下，在以前版本的 Microsoft Edge 中，计算样式的展开和折叠按钮在 **“元素**”工具的 **“计算**”选项卡中未正确呈现。  在 Microsoft Edge 106 中，此问题已修复。  展开和折叠按钮现在在高对比度模式下可见：
 
![高对比度模式下的计算样式](./devtools-106-images/computed-styles-high-contrast-mode.png)

另请参阅：
* [Windows 高对比度模式](/fluent-ui/web-components/design-system/high-contrast)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge 106 还包括Chromium项目的以下更新：

* [按“源”面板中的“创作”/“部署”对文件进行分组](https://developer.chrome.com/blog/new-in-devtools-106/#authored)
* [改进的堆栈跟踪](https://developer.chrome.com/blog/new-in-devtools-106/#stack-traces)
  * [用于异步操作的链接堆栈跟踪](https://developer.chrome.com/blog/new-in-devtools-106/#async)
  * [自动忽略已知的第三方脚本](https://developer.chrome.com/blog/new-in-devtools-106/#auto-ignore)
* [改进了调试期间的调用堆栈](https://developer.chrome.com/blog/new-in-devtools-106/#call-stack)
* [在“源”面板中隐藏忽略列出的源](https://developer.chrome.com/blog/new-in-devtools-106/#ignore-nav)
* [在命令菜单中隐藏忽略列出的文件](https://developer.chrome.com/blog/new-in-devtools-106/#ignore-search)
* [“性能”面板中的“新建交互”跟踪](https://developer.chrome.com/blog/new-in-devtools-106/#performance)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- > [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New in DevTools (Chrome 106)](https://developer.chrome.com/blog/new-in-devtools-106) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google). -->


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- [![Creative Commons License](../../../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0). -->
