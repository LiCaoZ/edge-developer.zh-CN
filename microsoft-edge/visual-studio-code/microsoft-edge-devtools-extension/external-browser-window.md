---
title: 使用外部浏览器窗口
description: 使用外部浏览器窗口，而不是嵌入的 (无头) Edge DevTools：Microsoft Edge 开发人员工具扩展中用于Visual Studio Code的浏览器选项卡。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: fdc13bdd14859790b606b1929ba727f86afd589c
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816034"
---
# <a name="using-an-external-browser-window"></a>使用外部浏览器窗口

默认情况下，DevTools 会在 Visual Studio Code 中打开 **Edge DevTools：Browser** 选项卡。  另一种方法是让 DevTools 打开由自动化控制的外部 Microsoft Edge 窗口。


<!-- ====================================================================== -->
## <a name="external-browser-window"></a>外部浏览器窗口

_外部浏览器窗口_ 意味着，使用 Edge DevTools 扩展启动浏览器实例时，将打开包含完整 UI 的整个 Microsoft Edge 窗口，由 DevTools 测试自动化控制：

![单独的 Microsoft Edge 窗口](./external-browser-window-images/success-page-external-browser.png)

打开外部浏览器窗口时，“ **Edge DevTools：浏览器** ”选项卡在启动 DevTools 时不会打开：

![Visual Studio Code外部浏览器启动 (且没有调试工具栏) ](./external-browser-window-images/vscode-when-external-browser.png)

如果随后在 **“Edge DevTools**”选项卡中单击“**切换屏幕广播**”按钮，“**Edge DevTools：浏览器”** 选项卡随即打开，显示**选项卡处于非活动状态**：

![Tab 非活动状态](./external-browser-window-images/tab-inactive.png)


<!-- ====================================================================== -->
## <a name="the-embedded-devtools-browser"></a>嵌入的 DevTools 浏览器

默认情况下，DevTools 会在Visual Studio Code中打开 **Edge DevTools：浏览器**选项卡，而不是打开外部浏览器窗口。  **Edge DevTools：浏览器**选项卡底部包含设备仿真工具栏：

![嵌入式浏览器](./external-browser-window-images/embedded-browser.png)

此选项卡也称为：
*  **设置**中的_无头浏览器_。
*  在工具提示中 _进行屏幕广播_。
*  _嵌入式浏览器_。
*  _DevTools 浏览器_。
*  _嵌入的 DevTools 浏览器_。


<!-- ====================================================================== -->
## <a name="changing-the-setting"></a>更改设置

若要更改或检查要使用哪种类型的浏览器窗口的设置：

1. 在Visual Studio Code中，选择“活动栏”> **Microsoft Edge 工具**。  **Microsoft Edge 工具**侧栏随即打开。

1. 将鼠标悬停在 **目标**右侧，然后单击“ **更多操作** (**...**) > **打开设置**。

   ![将扩展设置为使用嵌入式浏览器](./external-browser-window-images/settings-headless.png)

1. 如果要在Visual Studio Code中使用 **Edge DevTools：浏览器**选项卡，请选中 **“无头”** 复选框。

   或者，如果要使用外部自动化控制的浏览器窗口，请清除 **无头** 复选框。

1. 关闭 DevTools。  请参阅_打开 DevTools 和 DevTools 浏览器_中的[关闭 DevTools](./open-devtools-and-embedded-browser.md#closing-devtools)。

1. 打开 DevTools。  请参阅 [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
* [在 Visual Studio Code 中调试 Microsoft Edge](../debugger-for-edge.md)

**外部文章：**

* [VS Code 中的浏览器调试](https://code.visualstudio.com/docs/nodejs/browser-debugging)
