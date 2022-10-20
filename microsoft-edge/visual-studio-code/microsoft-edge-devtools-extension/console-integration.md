---
title: 控制台集成
description: 适用于Visual Studio Code的 Microsoft Edge 开发人员工具扩展中的控制台集成。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 405bf583c57fef583e12714a877fc9d1916e20d3
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816032"
---
# <a name="console-integration"></a>控制台集成

在使用此扩展Visual Studio Code的 **Edge DevTools** 选项卡的**控制台**工具中，你可以执行在浏览器中使用 Microsoft Edge DevTools 时可以执行的所有操作。

![扩展内的 DevTools 控制台作为自己的选项卡](./console-integration-images/console-full.png)

您可以：
*  查看 [日志消息](/microsoft-edge/devtools-guide-chromium/console-log)。
*  `window`访问对象并使用 [DOM 交互便利方法](/microsoft-edge/devtools-guide-chromium/console-dom-interaction)。
*  [筛选控制台](/microsoft-edge/devtools-guide-chromium/console-filters) 并设置 [实时表达式](/microsoft-edge/devtools-guide-chromium/live-expressions)。


<!-- ====================================================================== -->
## <a name="console-side-by-side-with-other-tools"></a>与其他工具并排控制台

可以通过在 **Edge DevTools** 选项卡的下面板中打开**控制台**，将**控制台**与**元素**工具一起使用：

![扩展内的 DevTools 控制台和元素工具](./console-integration-images/console-in-elements.png)


<!-- ====================================================================== -->
## <a name="console-during-run-and-debug"></a>运行和调试期间的控制台

如果从“运行”和“调试”工作流启动 DevTools 扩展，Visual Studio Code调**试控制台**将提供 **Edge DevTools** 选项卡**控制台**工具的大部分功能，但无需筛选选项，并且显示的结果比 **Edge DevTools** 选项卡的**控制台**工具更基本：

![从运行和调试工作流启动扩展时，DevTools 控制台可用](./console-integration-images/console-integration.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [控制台概述](/microsoft-edge/devtools-guide-chromium/console/index.md)
* [调试](https://code.visualstudio.com/Docs/editor/debugging) - Visual Studio Code的调试控制台。
* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
