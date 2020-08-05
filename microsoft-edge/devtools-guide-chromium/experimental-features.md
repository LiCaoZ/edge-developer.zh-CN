---
description: Microsoft Edge DevTools 中的最新实验功能
title: 实验功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/21/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools、实验
ms.openlocfilehash: 6b3e1c06d6b8ed79054c28df483fcca93e5751d6
ms.sourcegitcommit: 19ef1422733ef1fd051d2b4f0263ce191e8d67bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "10902852"
---
# 实验功能  

你可以使用 Microsoft Edge DevTools 中仍处于开发阶段的实验功能来测试和[提供反馈](#providing-feedback-on-experimental-features)，然后再广泛发布。  

尽管实验功能可在 Microsoft Edge 的所有信道中使用，但你可能会使用 Microsoft Edge "未完成" 通道获取最新实验功能。  

## 启用实验功能  

使用以下步骤打开 Microsoft Edge 中的 "\" （或 "关闭 \"）实验功能。  

1.  [打开 DevTools][DevtoolsOpen]。  
     *   选择 `Control` + `Shift` + `I` \ （Windows \）或 `Command` + `Option` + `I` \ （macOS \）。  有关详细信息，请参阅[Microsoft Edge DevTools 键盘快捷方式][DevToolsShortcuts]。  
1.  打开 "[设置][DevToolsCustomizeSettings]" 窗格。  
    *   选择 `Shift` + `?` 。  有关详细信息，请参阅[Microsoft Edge DevTools 键盘快捷方式][DevToolsShortcuts]。  
1.  在 "**设置**" 窗格的左侧，选择 "**实验**" 部分。  
    
    :::image type="complex" source="./media/experiments-devtools.png" alt-text="DevTools 设置中的实验列表" lightbox="./media/experiments-devtools.png":::
       DevTools 设置中的实验列表  
    :::image-end:::  
    
1.  在 "**实验**" 页面上，滚动浏览所有可用实验功能的列表，然后选择要测试的每个功能旁边的复选框。  
1.  关闭并重新打开 Microsoft Edge DevTools。  

> [!NOTE]
> 实验性功能将不断更新，并可能导致性能问题。  若要关闭实验功能，请打开 "**试验**" 页面，然后清除要关闭的实验功能的复选框。  

## 突出显示实验功能  

以下部分介绍 Microsoft Edge 中可用的新实验功能。  

| 实验性功能 | Microsoft Edge 版本 |  
|:--- |:--- |  
| [启用自定义键盘快捷方式设置选项卡](#enable-custom-keyboard-shortcuts-settings-tab) | 84或更高版本 |
| [启用新的 CSS 网格调试功能](#enable-new-css-grid-debugging-features) | 85或更高版本 |  
| [启用支持以在面板之间移动选项卡](#enable-support-to-move-tabs-between-panels) | 85或更高版本 |  
| [启用 webhint](#enable-webhint) | 85或更高版本 | 
| [启用网络控制台](#enable-network-console) | 85或更高版本 |

### 启用自定义键盘快捷方式设置选项卡

在[DevTools 设置][DevToolsCustomizeSettings]中提供新的**快捷方式**页面，在 DevTools 中启用匹配的[键盘快捷方式][DevToolsShortcuts][与代码][VisualstudioCode]。  

启用实验后，请使用 select 再次打开[DevTools 设置][DevToolsCustomizeSettings] `Shift` + `?` 。  导航到 "新建**快捷方式**" 页面。  **从 "预设**" 下拉列表中选择 " **DevTools" （默认）** ，然后选择 " **Visual Studio 代码**"。  DevTools 中的键盘快捷方式现在与与 VS 代码中的等效操作的快捷方式相匹配。  

:::image type="complex" source="./media/experiments-keyboard-shortcut.png" alt-text="将 DevTools 中的键盘快捷方式与 VS 代码相匹配" lightbox="./media/experiments-keyboard-shortcut.png":::
   将 DevTools 中的键盘快捷方式与 VS 代码相匹配
:::image-end:::  

例如，在 Windows 上，在[VS 代码][VisualstudioCodeShortcutsKeyboardWindows]中暂停或继续运行脚本的键盘快捷方式是 `F5` 。  通过**DevTools （默认）** 预设，DevTools 中的相同快捷方式 `F8` 。  通过**Visual Studio 代码**预置，快捷方式也是 `F5` 。  

### 启用新的 CSS 网格调试功能  

在调试具有 CSS 网格布局的网站时，改善页面上的可视化效果。  你可以在 DevTools 设置中进一步自定义覆盖。  

:::image type="complex" source="./media/experiments-grid.png" alt-text="CSS 网格调试功能" lightbox="./media/experiments-grid.png":::
   CSS 网格调试功能  
:::image-end:::  

<!--Available in Microsoft Edge version 85 and later.  -->  

### 启用支持以在面板之间移动选项卡  

通常，**元素**和**网络**之类的工具只能在 DevTools 的 main \ （top \）面板中打开。  同样， **3D 视图**和**问题**之类的工具可能仅在 DevTools 的抽屉 \ （底部 \）面板中打开。  选择实验后，你可以通过将工具悬停在选项卡上，打开上下文菜单 \ （右键单击 \），然后选择 "移到**页首**" 或 "**移至底部**"，在顶部和底部面板之间移动工具。   此实验允许你自定义 DevTools 布局。  若要显示或隐藏底部面板，请选择 `Escape` 。  

:::image type="complex" source="./media/experiments-move-panels.png" alt-text="在面板之间移动选项卡" lightbox="./media/experiments-move-panels.png":::
   在面板之间移动选项卡  
:::image-end:::  

<!--Available in Microsoft Edge version 85 and later.  -->  

### 启用 webhint  

[webhint][WebhintMain]是一种开放源工具，可提供有关网站的辅助功能、跨浏览器兼容性、安全性、性能、PWAs 和其他常见 web 开发问题的实时反馈。  [Webhint][WebhintMain]实验将 webhint 反馈引入 "[问题][DevtoolsIssues]" 面板中的 DevTools。  你可以选择该问题以查看有关如何解决该问题的文档和你的网站上受影响的资源列表。  选择资源链接以打开 DevTools 中的相关**网络**、**源**或**元素**窗格。  

:::image type="complex" source="./media/experiments-webhint.png" alt-text="问题 面板中的 webhint 反馈" lightbox="./media/experiments-webhint.png":::
   "问题" 面板中的 webhint 反馈  
:::image-end:::      

<!--Available in Microsoft Edge version 85 and later.  -->  

### 启用网络控制台

**网络控制台**是通过 HTTP 建立综合网络请求的实验的工作标题。  你可以使用**网络控制台**实验来发送 web API 请求。  

启用实验后，确保重新启动 DevTools。 要使用网络控制台，请执行以下操作：
1.  打开 "**网络**" 窗格。
1.  查找要更改和重新发送的网络请求。
1.  打开上下文菜单 \ （右键单击 \），然后选择 "**编辑并重播**"。 
1.  当**网络控制台**打开时，请编辑网络请求信息。
1.  选择 "**发送**"。  

:::image type="complex" source="./media/network-network-console.png" alt-text="控制台抽屉中的网络控制台" lightbox="./media/network-network-console.png":::
控制台抽屉中的网络控制台
:::image-end::: 

<!--Available in Microsoft Edge version 85 and later.  --> 

## 以前的实验功能  

*   [3D 视图][Devtools3dViewIndex]现在可用，在 Microsoft Edge 版本83或更高版本中默认情况下处于打开状态。  

## 提供有关实验功能的反馈  

提供有关 Microsoft Edge DevTools 实验的反馈或与 DevTools 相关的任何其他内容。  

*   使用 DevTools 中的反馈图标发送反馈  
*   Tweet [@EdgeDevTools][TwitterEdgedevtools]  

:::image type="complex" source="./media/devtools-feedback.png" alt-text="Microsoft Edge DevTools 中的反馈图标" lightbox="./media/devtools-feedback.png":::
   Microsoft Edge DevTools 中的反馈图标  
:::image-end:::  

<!-- links -->  

[Devtools3dViewIndex]: ./3d-view/index.md "3D 视图 |Microsoft 文档"  
[DevtoolsIssues]: ./issues/index.md "查找并修复 Microsoft Edge DevTools 问题工具的问题 |Microsoft 文档"  
[DevToolsCustomizeSettings]: ./customize/index.md#settings "设置-自定义 Microsoft Edge DevTools |Microsoft 文档"  
[DevToolsShortcuts]: ./shortcuts.md "Microsoft Edge DevTools 键盘快捷方式 |Microsoft 文档"  
[DevtoolsOpen]: ./open.md "打开 Microsoft Edge DevTools |Microsoft 文档"  

[TwitterEdgedevtools]: https://www.twitter.com/EdgeDevTools "Microsoft Edge DevTools |Twitter"  

[VisualstudioCode]: https://code.visualstudio.com "Visual Studio 代码"  
[VisualstudioCodeShortcutsKeyboardWindows]: https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf "适用于 Windows 的 Visual Studio 代码键盘快捷方式 |Visual Studio 代码"  

[WebhintMain]: https://webhint.io "webhint" 