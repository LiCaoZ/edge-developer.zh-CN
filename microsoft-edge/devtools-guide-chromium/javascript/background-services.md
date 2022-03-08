---
title: 调试后台服务
description: 如何使用 Microsoft Edge DevTools 调试后台提取、后台同步、通知和推送通知。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: b6a4b5ae1c0f9ea72be3ec7e8f27843932ca287a
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432066"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="debug-background-services"></a>调试后台服务

Microsoft Edge **** DevTools 的后台服务部分是 JavaScript API 的工具集合，使你的网站能够在用户未打开网站时发送和接收更新。  后台服务在功能上类似于 [后台进程](https://en.wikipedia.org/wiki/Background_process)。

Microsoft Edge DevTools 将以下每个 API 都作为后台服务：

*  [后台提取](#background-fetch)
*  [后台同步](#background-sync)
*  [通知](#notifications)
*  [推送消息](#push-messages)

Microsoft Edge DevTools 可能会将后台服务事件记录 3 天，即使 DevTools 未打开。  后台服务事件日志可帮助你确保事件已根据预期发送和接收。  您还可以检查每个事件的详细信息。

:::image type="content" source="../media/javascript-application-background-services-push-messaging.msft.png" alt-text="&quot;推送消息&quot;窗格。" lightbox="../media/javascript-application-background-services-push-messaging.msft.png":::


<!-- ====================================================================== -->
## <a name="background-fetch"></a>后台提取

**后台提取 API**使**服务工作进程**能够可靠地下载大型资源（如电影或播客）作为后台服务。  若要将后台提取事件记录 3 天，即使 DevTools 未打开：

<!--Todo: add background fetch api section when available -->

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"**应用程序"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

1. 在左侧的"后台服务 **"部分** ，选择" **后台提取"**。  将 **打开"后台提取** "页。

   :::image type="content" source="../media/javascript-application-background-services-background-fetch-empty.msft.png" alt-text="&quot;后台提取&quot;面板。" lightbox="../media/javascript-application-background-services-background-fetch-empty.msft.png":::

1. 单击 **"记录** (![记录"。](../media/record-icon.msft.png)) 。
   触发某些后台提取活动后，DevTools 记录事件到表中。

   :::image type="content" source="../media/javascript-application-background-services-background-fetch.msft.png" alt-text="后台提取面板中的事件日志。" lightbox="../media/javascript-application-background-services-background-fetch.msft.png":::

1. 单击事件以查看表下方空白区域的详细信息。

   :::image type="content" source="../media/javascript-application-background-services-background-fetch-details.msft.png" alt-text="在&quot;后台提取&quot;窗格中查看事件的详细信息。" lightbox="../media/javascript-application-background-services-background-fetch-details.msft.png":::


<!-- ====================================================================== -->
## <a name="background-sync"></a>后台同步

**后台同步 API**使脱机**服务工作进程**能够在重新建立可靠 Internet 连接后向服务器发送数据。  若要将后台同步事件记录 3 天，即使 DevTools 未打开：

<!--Todo: add background sync api section when available -->

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"**应用程序"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

1. 在左侧的"后台服务 **"部分** ，选择" **后台同步"**。 将 **打开"后台同步** "页。

   :::image type="content" source="../media/javascript-application-background-services-background-sync-empty.msft.png" alt-text="&quot;后台同步&quot;窗格。" lightbox="../media/javascript-application-background-services-background-sync-empty.msft.png":::

1. 单击 **"记录** (![记录"。](../media/record-icon.msft.png)) 。  触发某些后台同步活动后，DevTools 记录事件到表中。

   :::image type="content" source="../media/javascript-application-background-services-background-sync.msft.png" alt-text="后台同步窗格中的事件日志。" lightbox="../media/javascript-application-background-services-background-sync.msft.png":::

1. 选择一个事件，在表下方的空白区域查看其详细信息。

   :::image type="content" source="../media/javascript-application-background-services-background-sync-details.msft.png" alt-text="在&quot;后台同步&quot;窗格中查看事件的详细信息。" lightbox="../media/javascript-application-background-services-background-sync-details.msft.png":::


<!-- ====================================================================== -->
## <a name="notifications"></a>通知

**服务工作进程**从服务器接收一条[推送消息](https://developer.mozilla.org/docs/Web/API/Push_API)后，服务工作进程使用[通知 API](https://developer.mozilla.org/docs/Web/API/Notifications_API)向用户显示数据。  若要将通知记录 3 天，即使 DevTools 未打开：

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"**应用程序"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

1. 在左侧的"后台服务 **"部分，** 选择" **通知"**。  将 **打开"通知** "页。

   :::image type="content" source="../media/javascript-application-background-services-notifications-empty.msft.png" alt-text="&quot;通知&quot;窗格。" lightbox="../media/javascript-application-background-services-notifications-empty.msft.png":::

1. 单击 **"记录** (![记录"。](../media/record-icon.msft.png)) 。  触发某些通知活动后，DevTools 记录事件到表中。

   :::image type="content" source="../media/javascript-application-background-services-notifications.msft.png" alt-text="通知窗格中的事件日志。" lightbox="../media/javascript-application-background-services-notifications.msft.png":::

1. 单击事件以查看表下方空白区域的详细信息。

   :::image type="content" source="../media/javascript-application-background-services-notifications-details.msft.png" alt-text="在通知窗格中查看事件的详细信息。" lightbox="../media/javascript-application-background-services-notifications-details.msft.png":::


<!-- ====================================================================== -->
## <a name="push-messages"></a>推送消息

若要向用户显示推送通知，**服务工作进程**必须先使用[推送消息 API](https://developer.mozilla.org/docs/Web/API/Push_API)从服务器接收数据。  当服务工作进程准备好显示通知时，它将使用[通知 API](https://developer.mozilla.org/docs/Web/API/Notifications_API)。  若要将推送通知记录 3 天，即使 DevTools 未打开：

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"**应用程序"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

1. 在左侧的"后台服务 **"** 部分，选择" **推送消息"**。  将 **打开"推送消息"** 页。

   :::image type="content" source="../media/javascript-application-background-services-push-messaging-empty.msft.png" alt-text="打开&quot;推送消息&quot;窗格。" lightbox="../media/javascript-application-background-services-push-messaging-empty.msft.png":::

1. 单击 **"记录** (![记录"。](../media/record-icon.msft.png)) 。  触发某些推送消息活动后，DevTools 记录事件到表中。

   :::image type="content" source="../media/javascript-application-background-services-push-messaging.msft.png" alt-text="&quot;推送消息&quot;窗格中的事件日志。" lightbox="../media/javascript-application-background-services-push-messaging.msft.png":::

1. 单击事件以查看表下方空间的详细信息。

   :::image type="content" source="../media/javascript-application-background-services-push-messaging-details.msft.png" alt-text="在&quot;推送消息&quot;窗格中查看事件的详细信息。" lightbox="../media/javascript-application-background-services-push-messaging-details.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/background-services)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。
[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
