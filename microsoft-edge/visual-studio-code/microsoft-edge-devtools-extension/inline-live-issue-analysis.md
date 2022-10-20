---
title: 内联和实时问题分析
description: 适用于Visual Studio Code的 Microsoft Edge 开发人员工具扩展中的内联和实时问题分析。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 0296bc9651de652af2b4370eb1736efaf5b6f491
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816012"
---
# <a name="inline-and-live-issue-analysis"></a>内联和实时问题分析

源代码 (或`.js`文件) `.html``.css`中的问题用波浪下划线突出显示。  可以检查问题并获取有关问题所在内容、如何解决该问题以及在何处查找详细信息的详细信息。  若要检查问题，请单击具有波浪下划线的代码：

![显示如何修复问题的代码中报告的辅助功能问题，以及在何处查找详细信息](./inline-live-issue-analysis-images/inline-issue-reporting.png)

此功能需要Node.js和 npm (节点包管理器) 。  请参阅[步骤 4：安装Node.js和节点包管理器 (npm) ](./install.md#step-4-install-nodejs-and-node-package-manager-npm)，以_安装用于Visual Studio Code的 DevTools 扩展_。

默认情况下，此功能处于启用状态;在 **“设置**”中选中 **Webhint** 复选框。  若要打开或关闭此功能，请选择活动栏> **Microsoft Edge Tools** >将鼠标悬停在 **目标** > **更多操作** (右侧 **...**) > **打开设置** >选择或清除 **Webhint** 复选框：

![设置中的 Webhint 复选框](./inline-live-issue-analysis-images/webhint-checkbox-settings.png)


若要查看文件中的所有问题，请单击 **“查看问题**”：

![源代码中突出显示的问题，其中包含一个导航栏，用于解释问题以及要移动到下一个问题和上一个问题的按钮](./inline-live-issue-analysis-images/navigating-issues.png)

下面板中的 **“问题** ”选项卡列出了 DevTools 在当前打开的文件中发现的所有问题：

![Visual Studio Code下面板中的“问题”选项卡，列出项目文件中找到的所有问题](./inline-live-issue-analysis-images/issues-in-lower-panel.png)


<!-- ====================================================================== -->
## <a name="live-updating-of-issues-reporting"></a>实时更新报告的问题

编辑代码时会实时评估问题。  键入时，你将获得有关找到的任何问题以及如何解决这些问题的反馈：

![在输出元素上解释的可能问题](./inline-live-issue-analysis-images/live-issue-reporting.png)


<!-- ====================================================================== -->
## <a name="automated-quick-fixes-and-issue-filtering"></a>自动快速修复和问题筛选

<!--
bold "Quick Fix" when focusing on the UI
the UI label string is "Quick Fix", not "Quick Fixes"
-->

适用于Visual Studio Code的 Microsoft Edge DevTools 扩展包括**快速修复**功能。  通过使用快速修复，可以自定义扩展的错误报告以满足当前项目的需求。

将鼠标悬停在有问题的元素上时，会获得灯泡 (![灯泡图标](./inline-live-issue-analysis-images/light-bulb-icon.png)) 图标，指示有可用的快速修复：

![一个定位点元素，其特定于协议的 href 属性突出显示为问题，由上面的波浪下划线和灯泡图标显示](./inline-live-issue-analysis-images/light-bulb.png)

单击灯泡图标会显示选项列表。 例如，如果添加了具有协议相对 URL 的链接，则可从以下 **快速修复** 列表中进行选择：

![在定位点元素旁边打开的“快速修复”面板出现错误，提供多个快速修复选项](./inline-live-issue-analysis-images/quick-fix-options.png)

可以选择要使用哪种 **快速修复** 来解决问题或停止将其报告为问题：

* **修复了“no-protocol-relative-urls”问题** - 将缺少的 URL 前缀 `https://` 添加到链接。

* **禁用此项目中的“no-protocol-relative-url”提示** - 在项目文件夹中创建配置 `.hintrc` 文件 (如果) 尚不存在，并告知扩展名不要为此项目报告此问题。

* **编辑此项目的 .hintrc** - 打开 `.hintrc` 配置文件，以便可以对其进行编辑以自定义扩展的错误报告。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用问题工具查找和修复问题](../../devtools-guide-chromium/issues/index.md)
* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
