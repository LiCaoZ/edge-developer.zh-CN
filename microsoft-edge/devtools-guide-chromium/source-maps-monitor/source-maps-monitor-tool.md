---
title: 源地图监视器工具
description: 如何在 DevTools 地图 Source Microsoft Edge Monitor 工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/15/2022
ms.openlocfilehash: e99f36913ccb663cf4c2078c924c55441e48b950
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433801"
---
# <a name="source-maps-monitor-tool"></a>源地图监视器工具

使用 **Source 地图 Monitor** 工具监视网页上请求加载源地图的源文件，以及是否已加载源映射。  如果你的网页使用源地图将重新处理的代码映射到原始源代码，此工具将非常有用。  _源_ 映射使您能够查看和调试原始源代码，而不必使用服务器返回的代码的重新处理版本。


若要尝试此功能，请执行以下操作：

1. 在新的选项卡或窗口中，按照将处理的代码映射到原始源代码中的说明进行 [调试](../javascript/source-maps.md)，然后继续下面的操作。

1. 关闭演示打开的弹出对话框。

1. 在 **"源** "工具的" **页面** "选项卡中，选择演示为用户创建的文件， ** 例如 **Coffee2.js。

1. 在 DevTools 中的主工具栏上，单击"更多**工具 (**![更多工具"图标](../media/more-tools-icon-light-theme.png)。) 按钮，然后选择"源地图**监视器"** 工具。

   ![Source 地图 Monitor 工具。](../media/source-maps-monitor-tool.png)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [将已处理的代码映射到原始源代码，以便进行调试](../javascript/source-maps.md)
* [通过将源映射发布到Azure Artifacts符号服务器来安全地调试原始代码](../javascript/publish-source-maps-to-azure.md)
* [使用Azure Artifacts符号服务器源映射安全地调试原始代码](../javascript/consume-source-maps-from-azure.md)
* [源工具现在将在源图](../whats-new/2021/11/devtools.md#sources-tool-now-notifies-you-when-sourcemaps-cant-be-loaded)无法加载到 _What's new in DevTools (Microsoft Edge 96) 中通知你_。
