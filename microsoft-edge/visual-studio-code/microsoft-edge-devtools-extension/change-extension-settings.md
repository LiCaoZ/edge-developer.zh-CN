---
title: 更改扩展设置
description: 关于适用于Visual Studio Code的 Microsoft Edge 开发人员工具扩展的第 1 条。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: c977bc6614a7c1e5d7eb9b592c28c85323a5cb06
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816050"
---
# <a name="changing-the-extension-settings"></a>更改扩展设置

可以根据需要自定义Visual Studio Code扩展。

1. 在Visual Studio Code中，在**活动栏**上，单击 **“Microsoft Edge 工具**”。

1. 在 **Microsoft Edge 工具** > **目标**中，单击“目标 **”一**词右侧的“**更多操作** (...) ”，然后选择 **“打开设置”** 菜单。

   ![Microsoft Edge 工具：目标面板上的“更多操作”图标，用于更改 DevTools 扩展的设置](./change-extension-settings-images/edge-tools-open-settings.png)

   **将显示“设置”** 页，筛选为仅显示 **vscode-edge-devtools** 设置。

1. 滚动浏览可用设置。


<!-- ====================================================================== -->
## <a name="list-of-settings"></a>设置列表

DevTools v2.1.1 的 **“设置”** 页包含这些设置。  有关详细信息，请参阅 **“设置”** 页。

* **浏览器 Args**
* **浏览器风格**
* **默认入口点**
* **默认 URL**
* **无头**
* **主机 名**
* **路径映射**
* **端口**
* **显示辅助角色**
* **源映射路径替代**
* **源地图**
* **超时**
* **使用 Https**
* **用户数据 Dir**
* **Webhint**
* **Web 根**
* **Bottom**
* **Top**
* **拖放时拆分**
* **忽略的扩展**
* **HTML：自定义数据**


<!-- ====================================================================== -->
## <a name="reloading-the-extension-after-changing-settings"></a>更改设置后重新加载扩展

某些设置具有一个说明，用于读 ** 取更改) 后所需的 (重载 **。  若要使此类设置生效，请关闭 DevTools 的任何实例。  请参阅_打开 DevTools 和 DevTools 浏览器_中的[关闭 DevTools](./open-devtools-and-embedded-browser.md#closing-devtools)。

然后再次打开 DevTools 以使用新设置。  请参阅 [打开 DevTools 和 DevTools 浏览器](./open-devtools-and-embedded-browser.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
