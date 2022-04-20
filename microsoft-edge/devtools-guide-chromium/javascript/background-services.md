---
title: 调试后台服务
description: 如何使用 Microsoft Edge DevTools 调试后台提取、后台同步、通知和推送通知。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/06/2022
ms.openlocfilehash: 381b044421b75b430ba8d8e9427bc862a3ec2a5a
ms.sourcegitcommit: 0b577d05632b35e45479b12aecc3f2df90ca90e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2022
ms.locfileid: "12486617"
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

Microsoft Edge DevTools 的 **“后台服务**”部分是 Web API 的工具集合，即使用户未使用您的网站，网站也可发送和接收数据，并使浏览器能够向服务器报告生产问题。

Microsoft Edge DevTools 将以下每个 API 都作为后台服务：

*  [后台提取](#background-fetch)
*  [后台同步](#background-sync)
*  [通知](#notifications)
*  [付款处理程序](#payment-handler)
*  [定期后台同步](#periodic-background-sync)
*  [推送消息](#push-messages)
*  [报告 API](#reporting-api)
<!-- TODO: add a section about Payment Handler -->

“ **后台服务** ”部分记录 API 事件，即使未使用 DevTools，也可帮助确保按预期发送和接收事件。


<!-- ====================================================================== -->
## <a name="background-fetch"></a>后台提取

使用 **后台提取 API** ，渐进式 Web 应用 **的服务工作者** 可以可靠地下载大型资源（如电影或播客）作为后台服务。  记录后台提取事件 3 天，即使 DevTools 未打开：

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“后台提取**”。  “ **背景提取** ”页随即打开。

   ![背景提取面板。](./images/application-background-fetch-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。
   触发某些后台提取活动后，DevTools 记录事件到表中。

   ![后台提取面板中的事件日志。](./images/application-background-fetch-events.png)

1. 单击事件可在表下方的空格中查看其详细信息。

   ![在“后台提取”窗格中查看事件的详细信息。](./images/application-background-fetch-details.png)


<!-- ====================================================================== -->
## <a name="background-sync"></a>后台同步

后 **台同步 API** 使渐进式 Web 应用的脱机 **服务辅助角色** 能够在重新建立可靠的 Internet 连接后将数据发送到服务器。  记录后台同步事件 3 天，即使 DevTools 未打开：

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“后台同步**”。 “ **背景同步** ”页随即打开。

   ![“背景同步”窗格。](./images/application-background-sync-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  触发某些后台同步活动后，DevTools 记录事件到表中。

   ![背景同步窗格中的事件日志。](./images/application-background-sync-events.png)

1. 选择一个事件以在表下方的空间中查看其详细信息。

   ![在“背景同步”窗格中查看事件的详细信息。](./images/application-background-sync-details.png)


<!-- ====================================================================== -->
## <a name="notifications"></a>通知

**服务工作进程**从服务器接收一条[推送消息](https://developer.mozilla.org/docs/Web/API/Push_API)后，服务工作进程使用[通知 API](https://developer.mozilla.org/docs/Web/API/Notifications_API)向用户显示数据。  若要记录通知 3 天，即使 DevTools 未打开，

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“通知**”。  “ **通知** ”页随即打开。

   ![“通知”窗格。](./images/application-notifications-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  触发某些通知活动后，DevTools 记录事件到表中。

   ![“通知”窗格中的事件日志。](./images/application-notifications-events.png)

1. 单击事件可在表下方的空格中查看其详细信息。

   ![在“通知”窗格中查看事件的详细信息。](./images/application-notifications-details.png)


<!-- ====================================================================== -->
## <a name="payment-handler"></a>付款处理程序

[支付处理程序 API](https://web.dev/web-based-payment-apps-overview/) 允许 Web 应用程序代表用户处理付款请求。 若要记录付款请求和响应事件 3 天，即使 DevTools 未打开，

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“付款处理程序**”。  “ **付款处理程序** ”页随即打开。

   ![“付款处理程序”窗格。](./images/application-payment-handler-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  触发某些付款请求后，DevTools 会将事件记录到表。

   ![付款处理程序窗格中的事件日志。](./images/application-payment-handler-events.png)

1. 单击事件可在表下方的空格中查看其详细信息。

   ![在“付款处理程序”窗格中查看事件的详细信息。](./images/application-payment-handler-details.png)


<!-- ====================================================================== -->
## <a name="periodic-background-sync"></a>定期后台同步

**定期后台同步 API** 使渐进式 Web 应用**的服务辅助角色**能够定期从服务器中检索数据，即使网站未打开。 若要详细了解 **定期后台同步 API**，请参阅 [使用定期后台同步 API 定期获取新内容](/microsoft-edge/progressive-web-apps-chromium/how-to/background-syncs#use-the-periodic-background-sync-api-to-regularly-get-fresh-content)。

记录定期后台同步事件 3 天，即使 DevTools 未打开：

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **定期后台同步**。 “ **定期背景同步** ”页随即打开。

   ![定期背景同步窗格。](./images/application-periodic-background-sync-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  触发一些定期后台同步活动后，DevTools 会将事件记录到表。

   ![定期后台同步窗格中的事件日志。](./images/application-periodic-background-sync-events.png)


<!-- ====================================================================== -->
## <a name="push-messages"></a>推送消息

若要向用户显示推送通知，渐进式 Web 应用 **的服务工作者** 必须首先使用 [推送消息 API](https://developer.mozilla.org/docs/Web/API/Push_API) 从服务器接收数据。  当服务工作进程准备好显示通知时，它将使用[通知 API](https://developer.mozilla.org/docs/Web/API/Notifications_API)。  若要记录推送消息 3 天，即使 DevTools 未打开，

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“推送消息传送**”。  “ **推送消息传送”** 页随即打开。

   ![打开“推送消息传送”窗格。](./images/application-push-messaging-empty.png)

1. 单击 **“记录** (![记录。](../media/record-icon.msft.png)) 。  触发某些推送消息活动后，DevTools 记录事件到表中。

   ![“推送消息传送”窗格中的事件日志。](./images/application-push-messaging-events.png)

1. 单击事件可查看表下方空间中的详细信息。

   ![在“推送消息”窗格中查看事件的详细信息](./images/application-push-messaging-details.png)


<!-- ====================================================================== -->
## <a name="reporting-api"></a>报告 API

**报告 API** 使 Web 开发人员能够从其生产网站接收安全违规报告、已弃用的 API 调用和其他报告。

若要查看浏览器使用 **报告 API** 发送的报表，请执行以下操作：

1. 通过右键单击网页并选择 **“检查**”打开 DevTools。  或者按 `Ctrl`++`Shift``I` (Windows、Linux) 或`I` `Command`+`Option`+ (macOS) 。

1. 在 DevTools 的主工具栏上，选择“ **应用程序** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在左侧的 **“后台服务”** 部分中，选择 **“报告 API**”。  “ **报告 API** ”页随即打开。

   ![打开“报告 API”窗格。](./images/application-reporting-api.png)

1. **“报告 API**”页显示顶部表中发送的报表。

   ![“报告 API”窗格中的报表列表](./images/application-reporting-api-reports.png)

1. 单击报表可查看表下方空间中的详细信息。

   ![在“报告 API”窗格中查看报表的详细信息](./images/application-reporting-api-details.png)

1. **“报告 API**”页还会显示通过`Reporting-Endpoints`底部表中的 HTTP 标头配置的报告终结点的列表。

   ![在“报告 API”窗格中查看报告终结点列表](./images/application-reporting-api-endpoints.png)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/background-services)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。
[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
