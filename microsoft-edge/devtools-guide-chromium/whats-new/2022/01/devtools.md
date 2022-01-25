---
title: 'DevTools (Microsoft Edge 97 中的新增) '
description: 默认情况下，"分离的元素"工具现已打开。  焦点模式的改进和 Bug 修复。  3D 视图工具现在支持在 DevTools 中更改颜色主题。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/14/2022
ms.openlocfilehash: 7f616430f059707ee14f4e769aa483cff4b3ffc5
ms.sourcegitcommit: 397717e6a3d19933703d0fc31baa57edab6d7702
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/13/2022
ms.locfileid: "12293909"
---
# <a name="whats-new-in-devtools-microsoft-edge-97"></a>DevTools (Microsoft Edge 97 中的新增) 

以下部分列出了 Microsoft Edge 开发人员工具团队的公告。  若要试用 DevTools 的最新功能和适用于 Microsoft Edge 的 DevTools Visual Studio Code，请阅读这些通知。  若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。

如果你使用的是 Windows、Linux 或 macOS，请考虑将 Microsoft Edge Canary 预览通道用作默认开发浏览器。  预览频道使你可以访问开发人员工具Microsoft Edge功能。


<!-- ====================================================================== -->
## <a name="introducing-the-detached-elements-tool"></a>分离的元素工具介绍

<!-- Title: Check out the new Detached Elements tool -->
<!-- Subtitle: The new Detached Elements tool is now available by default in Microsoft Edge 97. -->

如果 DOM 节点__ 不再附加到 DOM 的任何元素，但仍被其他元素保留在内存中，则认为该节点Microsoft Edge。  浏览器无法对分离的元素进行垃圾回收，因为某些 JavaScript 对象仍在引用该元素，即使该元素不再位于页面上或不再是 DOM 的一部分。

新的 **分离元素** 工具在页面上查找所有分离的元素并显示它们。  可以展开和折叠分离的元素，以查看同时保留的父节点和子节点。  可以通过单击"收集垃圾"图标来触发浏览器的垃圾回收****，然后确认当无法对分离的元素进行垃圾回收时出现内存泄漏。  若要跳转到引用已分离元素的 JavaScript 代码，请单击"分析"按钮**** 以拍摄堆快照。

分离**的元素工具**最初在版本[93](../../2021/07/devtools.md#debug-dom-node-memory-leaks-with-the-new-detached-elements-tool)中作为实验Microsoft Edge提供。  该工具现在默认在版本 97 Microsoft Edge可用。

![分离的元素工具。](../../media/2022/01/detached-elements-tool.png)

另请参阅：
* [使用分离的元素工具调试 DOM 内存泄漏](../../../memory-problems/dom-leaks.md)
* [使用分离的元素工具Microsoft Edge内存泄漏 - YouTube](https://www.youtube.com/watch?v=v2iy17ptmBk&ab_channel=MicrosoftEdge)


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools-extension-for-visual-studio-code"></a>用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展

有关此扩展的常规信息，请参阅[Microsoft Edge DevTools extension for Visual Studio Code](../../../../visual-studio-code/microsoft-edge-devtools-extension.md)。

### <a name="screencast-enhancements-deprecation-warnings-and-new-launch-options-for-microsoft-edge"></a>屏幕广播增强功能、弃用警告和适用于 Microsoft Edge

<!-- Title: Screeencast improvements and launch options for Microsoft Edge in the Visual Studio Code extension -->
<!-- Subtitle: The correct list of emulated devices is shown for the screeencast, the correct device emulation is displayed, and there are now launch arguments for the browser. -->

当前版本的 Microsoft Edge DevTools Visual Studio Code修复了社区报告的一些问题：

*  屏幕广播中的仿真设备列表现在与浏览器中的仿真设备列表相同。

*  设备模拟现在添加正确的用户代理字符串，以触发正确的显示。

*  现在，当你使用已弃用版本的 Microsoft Edge 时，你收到一条警告，指示你错过功能。

*  现在，你可以为启动的浏览器实例提供参数，以防你需要进行特殊设置：

![用于指定启动参数的扩展Microsoft Edge。](../../media/2022/01/extension-settings-launch-arguments.png)


<!-- ====================================================================== -->
## <a name="improvements-and-bug-fixes-for-focus-mode"></a>焦点模式的改进和 Bug 修复

<!-- Title: Have you tried Focus Mode? -->
<!-- Subtitle: To de-clutter and simplify the DevTools interface to focus on debugging web apps, enable Focus Mode in DevTools settings. -->

由于早期反馈，我们一直在针对开发人员工具的新焦点模式接口进行改进Microsoft Edge Bug 修复。  焦点模式是一个新的 UI 选项，允许你将工具停靠在 DevTools 窗口的顶部或一侧，并从工具栏中删除混乱邮件。

使用焦点模式时，所有相同的工具和 [自定义主题](../../../customize/theme.md) 都可用，就像在现有的 DevTools UI 中一样。  了解有关焦点模式[UI 的更多信息](../../../experimental-features/index.md#focus-mode)，或者通过启用 DevTools 设置实验来******尝试**  >  **它**。

![焦点模式 UI。](../../media/2022/01/focus-mode.png)


<!-- ====================================================================== -->
## <a name="3d-view-tool-supports-changing-color-themes-in-devtools"></a>3D 视图工具支持在 DevTools 中更改颜色主题

<!-- Title: 3D View better integrates with different themes in DevTools -->
<!-- Subtitle: The 3D View tool now works when you select a different color theme in DevTools. -->

在早期版本的 Microsoft Edge，在 DevTools 中更改主题，然后打开 3D 视图工具会导致面板空白。  This issue has now been fixed， in Microsoft Edge 97.  若要了解更多信息，请参阅 [向 DevTools](../../../customize/theme.md) 和 [3D 视图应用颜色主题](../../../3d-view/index.md)。

![3D 视图工具现在支持更改颜色主题。](../../media/2022/01/3d-view-with-color-theme.png)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge版本 97 还包括来自 Chromium 项目的以下更新：

* [在设备模式下刷新设备列表](https://developer.chrome.com/blog/new-in-devtools-97/#device)
* [以 HTML 格式编辑自动完成](https://developer.chrome.com/blog/new-in-devtools-97/#code-completion)
* [改进的代码调试体验](https://developer.chrome.com/blog/new-in-devtools-97/#debugging)


<!-- > [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New In DevTools (Chrome 97)](https://developer.chrome.com/blog/new-in-devtools-97) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google).

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0). -->