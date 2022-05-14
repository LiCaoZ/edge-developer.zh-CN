---
title: 辅助功能测试功能
description: 要测试的网页辅助功能方面以及 Microsoft DevTools 中的相应功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 0ede71e373cdc99c4d6f6a519a2c69dcc5d091d2
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12513815"
---
# <a name="accessibility-testing-features"></a>辅助功能测试功能

若要测试网页的辅助功能，请先列出要测试的辅助功能方面的清单，然后使用相关的 DevTools 功能来检查每一个方面。


<!-- ====================================================================== -->
## <a name="alt-text-for-images"></a>图像替换文字

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证图像是否具有替换文字 | **报** 表> **辅助功能** 部分的问题工具 | [验证图像是否具有替换文字](test-issues-tool.md#verify-that-images-have-alt-text) |


<!-- ====================================================================== -->
## <a name="keyboard-support"></a>键盘支持

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证键盘支持 | **检查** 覆盖> **辅助功能** 部分的工具 | [使用“检查”工具通过将鼠标悬停在网页上](test-inspect-tool.md)并[使用“检查”工具分析 HTML 页面](../css/inspect.md)来检测辅助功能问题 |
| 验证键盘支持 | `Tab`、 `Shift+Tab`和 `Enter` 密钥 | [使用 Tab 和 Enter 键检查键盘支持](test-tab-enter-keys.md) |
| 验证键盘支持：验证是否指示焦点 | **“检查** 工具”、“ **样式”** 选项卡和 **“源”** 工具 | [分析边栏菜单中键盘焦点的缺失](test-analyze-no-focus-indicator.md) |
| 验证键盘支持：验证窗体按钮是否可与键盘一起使用 | “**元素**”工具中的 **“检查**工具”、“**DOM 树**”和 **“事件侦听器”** 选项卡 | [分析窗体中键盘支持缺失](test-analyze-no-keyboard-support.md) |
| 验证键盘支持：验证 `Tab` 密钥顺序 | **源订单查看器**>**“辅助功能**”选项卡>**元素**工具 | [使用源订单查看器测试键盘支持](test-tab-key-source-order-viewer.md) |


<!-- ====================================================================== -->
## <a name="text-contrast"></a>文本对比度

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证文本是否已自动 (整个页面的对比度)  | **报** 表> **辅助功能** 部分的问题工具 | [验证文本颜色是否有足够的对比度](test-issues-tool.md#verify-that-text-colors-have-enough-contrast) |
| 验证文本是否有足够的对比度 | **颜色****选取器**>“**样式**”选项卡>元素工具 | [使用颜色选取器测试文本颜色对比度](color-picker.md) |
| 验证文本是否有足够的对比度 | **检查**覆盖>**对比**度行的工具>**辅助功能**部分 | [使用“检查”工具通过将鼠标悬停在网页上](test-inspect-tool.md)并[使用“检查”工具分析 HTML 页面](../css/inspect.md)来检测辅助功能问题 |
| 验证文本是否有足够的对比度：处于悬停状态 | **“元素** 工具> **样式”** 选项卡> **切换元素状态** (显示 **Force 元素状态** 复选框)  | [验证所有元素状态可访问性](test-inspect-states.md) |
| 验证文本是否有足够的对比度：深色主题 (深色模式) 和浅色主题 | **呈现** 工具> **模拟 CSS 媒体功能首选配色方案** | [检查深色主题和浅主题的对比度问题](test-dark-mode.md) |


<!-- ====================================================================== -->
## <a name="screen-reader-support"></a>屏幕阅读器支持

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证屏幕阅读器支持：验证输入字段是否具有标签 | **报** 表> **辅助功能** 部分的问题工具 | [验证输入字段是否具有标签](test-issues-tool.md#verify-that-input-fields-have-labels) |
| 验证屏幕阅读器支持 | **检查**覆盖>**名称**和**角色**的工具>**辅助功能**部分 | [使用“检查”工具通过将鼠标悬停在网页上](test-inspect-tool.md)并[使用“检查”工具分析 HTML 页面](../css/inspect.md)来检测辅助功能问题 |
| 验证屏幕阅读器支持 | **辅助****功能树**>“**辅助功能**”选项卡>元素工具 | [检查辅助功能树是否支持键盘和屏幕阅读器](test-accessibility-tree.md)，以及 [使用辅助功能选项卡测试辅助功能](accessibility-tab.md) |


<!-- ====================================================================== -->
## <a name="vision-deficiencies"></a>视觉缺陷

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证网页是否可由色盲患者使用 | **呈现** 工具> **模拟视力缺陷** 下拉列表 | [验证页面是否对色盲者可用](test-color-blindness.md) |
| 验证网页是否可使用模糊视觉 | **呈现** 工具> **模拟视力缺陷** 下拉列表 | [验证页面是否在视觉模糊时可用](test-blurred-vision.md) |
| 验证网页是否可用，UI 动画已关闭 (运动)  | **渲染** 工具> **模拟 CSS 媒体功能首选减动** | [验证页面是否在关闭 UI 动画时可用](test-reduced-ui-motion.md) |


<!-- ====================================================================== -->
## <a name="usable-when-narrow"></a>在缩小时可用

| 要检查的辅助功能方面 | DevTools 的功能 | 文章或子标题 |
|---|---|---|
| 验证网页布局在缩小时是否可用 | **设备仿真** 工具 | [验证网页布局在窄时是否可用](accessibility-testing-in-devtools.md#verify-that-the-webpage-layout-is-usable-when-narrow)，并在设备 [仿真 (模拟移动设备) ](../device-mode/index.md) |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
*  [使用辅助技术导航开发工具](navigation.md)
*  [辅助功能测试](../../accessibility/test.md)
*  [辅助功能原则和最佳做法](https://developer.mozilla.org/docs/Web/Accessibility)
*  [屏幕阅读器](https://developer.mozilla.org/docs/Glossary/Screen_reader)
