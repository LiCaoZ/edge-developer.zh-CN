---
title: 查看和调试媒体播放器信息
description: 使用媒体工具查看信息并按浏览器选项卡调试媒体播放器。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: a8b1cdcdfa2638a9a3b4315e6d2a946309c7c910
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431849"
---
<!-- Copyright Jecelyn Yeen

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="view-and-debug-media-players-information"></a>查看和调试媒体播放器信息

使用 **媒体工具** 查看信息并按浏览器选项卡调试媒体播放器。


<!-- ====================================================================== -->
## <a name="open-the-media-tool"></a>打开媒体工具

**媒体工具**是 DevTools 中用于检查网页的媒体播放器的主要位置。

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"**媒体"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

   :::image type="content" source="../media/media-panel-empty.msft.png" alt-text="媒体面板。" lightbox="../media/media-panel-empty.msft.png":::


<!-- ====================================================================== -->
## <a name="view-media-players-information"></a>查看媒体播放器信息

1. 导航到包含媒体播放器的网页，如以下网页。

    [使用边缘开发人员工具最大程度地提高工作效率](https://www.bing.com/videos/search?view=detail&mid=DE0BA14EC0E0D18C06C8DE0BA14EC0E0D18C06C8)

1. 在" **玩家"** 菜单下，将显示媒体播放器。

1. 单击玩家。  " **属性** "面板显示媒体播放器的属性。

   :::image type="content" source="../media/media-panel-view.msft.png" alt-text="媒体属性。" lightbox="../media/media-panel-view.msft.png":::

1. 若要查看所有媒体播放器事件，请单击 **"事件"** 面板。

   :::image type="content" source="../media/media-panel-events.msft.png" alt-text="媒体事件。" lightbox="../media/media-panel-events.msft.png":::

1. 若要查看媒体播放器消息日志，请单击"消息 **"** 面板。  可以按日志级别或字符串筛选消息。

   :::image type="content" source="../media/media-panel-messages.msft.png" alt-text="媒体消息。" lightbox="../media/media-panel-messages.msft.png":::

1. 在时间线 **面板** 上，媒体播放和缓冲区状态实时显示。

   :::image type="content" source="../media/media-panel-timeline.msft.png" alt-text="媒体时间线。" lightbox="../media/media-panel-timeline.msft.png":::

### <a name="remote-debugging"></a>远程调试

在 Android 设备上从计算机或 macOS Windows媒体播放器信息。

1. 若要设置远程调试，请参阅远程 [调试 Android 设备入门](../remote-debugging/index.md)。

1. 远程查看媒体播放器信息。

    <!-- TODO: recreate image using an Android device -->
    <!--
   :::image type="content" source="../media/media-panel-remote-debug.msft.png" alt-text="Remote debugging." lightbox="../media/media-panel-remote-debug.msft.png":::
    -->


<!-- ====================================================================== -->
## <a name="hide-and-show-media-players"></a>隐藏和显示媒体播放器

有时，您可以在一个网页上运行多个媒体播放器，或者使用同一浏览器选项卡浏览不同的网页，每个网页都使用媒体播放器。

你可以隐藏 (或) 每个媒体播放器，以便更轻松地进行调试：

1. 使用同一浏览器选项卡浏览到多个不同的视频网页。

1. 隐藏媒体播放器：
    *  若要隐藏单个媒体播放器，请右键单击媒体播放器，然后选择"隐藏 **播放器"**。
    *  若要隐藏所有其他媒体播放器，请右键单击媒体播放器，然后选择"隐藏 **所有其他播放器"**。

:::image type="content" source="../media/media-panel-hide-show.msft.png" alt-text="隐藏媒体播放器。" lightbox="../media/media-panel-hide-show.msft.png":::


<!-- ====================================================================== -->
## <a name="export-media-player-information"></a>导出媒体播放器信息

*  若要将媒体播放器信息下载为 JSON 文件，请右键单击媒体播放器，然后选择" **保存播放器信息"**。

:::image type="content" source="../media/media-panel-save.msft.png" alt-text="导出媒体信息。" lightbox="../media/media-panel-save.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/media-panel/index)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
