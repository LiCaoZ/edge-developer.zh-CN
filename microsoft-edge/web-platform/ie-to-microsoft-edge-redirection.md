---
title: 将用户从Microsoft Edge移动Internet Explorer
description: 将用户从Microsoft Edge移动Internet Explorer。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/13/2020
---
# <a name="move-users-to-microsoft-edge-from-internet-explorer"></a>将用户从Microsoft Edge移动Internet Explorer

许多新式网站的设计与 Internet Explorer 不兼容。  当Internet Explorer访问不兼容的公共网站时，用户可能会收到一条消息。  该消息表明该网站与浏览器不兼容。  消息显示后，用户需要手动切换到新式浏览器。

为了最大限度地减少中断，从版本 84 开始，Microsoft Edge自动重定向用户的新功能。  当Internet Explorer用户转到与网站不兼容Internet Explorer时，Windows会自动将用户重定向到Microsoft Edge。  有关重定向的网站列表，请参阅需要Microsoft Edge[列表](https://edge.microsoft.com/neededge/v1)。

本文介绍以下概念：

*  网站添加到重定向列表的原因。
*  用于重定向的用户体验。
*  请求更新列表。


<!-- ====================================================================== -->
## <a name="why-is-a-website-added-to-the-internet-explorer-compatibility-list"></a>为什么将网站添加到兼容性Internet Explorer列表？

兼容性Internet Explorer列表仅在发生以下操作时添加网站。

*   向Internet Explorer显示一条消息，建议出于兼容性原因，用户应使用不同的浏览器。
*   所有者请求将网站添加到兼容性Internet Explorer列表。


<!-- ====================================================================== -->
## <a name="redirection-experience"></a>重定向体验

重定向到Microsoft Edge时，用户会显示下一张屏幕截图中的一次对话框。  该对话框为用户提供以下信息：
*  它说明了重定向网站的原因。
*  它会提示用户同意将浏览数据和首选项从 Internet Explorer 复制到Microsoft Edge。

将导入以下浏览数据：
*  收藏夹
*  密码
*  搜索引擎
*  打开选项卡
*  历史记录
*  “设置”
*  Cookie
*  主页

浏览通知并提示导入数据和首选项：

:::image type="content" source="../media/neededge-dialog1.msft.png" alt-text="浏览通知并提示导入数据和首选项。" lightbox="../media/neededge-dialog1.msft.png":::

如果用户未通过选中"始终显示我的浏览数据和首选项从 Internet Explorer"复选框同意，用户可以**** 选择"继续**浏览"** 以继续浏览会话。

最后，网站不兼容横幅将显示在每个重定向的地址栏下。  下图显示了网站不兼容横幅的示例。

:::image type="complex" source="../media/neededge-banner.msft.png" alt-text="有关新式网站的通知，以及将 Microsoft Edge 设置为默认浏览器或浏览 Microsoft Edge 的提示。" lightbox="../media/neededge-banner.msft.png":::
   有关新式网站的通知，并提示将Microsoft Edge设置为默认浏览器或浏览Microsoft Edge
:::image-end:::

网站不兼容横幅为用户提供了以下详细信息。

*   建议用户切换到Microsoft Edge。
*   产品/Microsoft Edge设置为默认浏览器。
*   为用户提供浏览Microsoft Edge。

当网站从 Internet Explorer Microsoft Edge 时，将发生以下操作之一。

*   如果活动"Internet Explorer"选项卡没有之前的内容，则关闭该选项卡。
*   如果活动Internet Explorer选项卡包含之前的内容，它将导航到 Microsoft 支持页面，说明网站重定向到 [Microsoft Edge 的原因](https://support.microsoft.com/office/the-website-you-were-trying-to-reach-doesn-t-work-with-internet-explorer-8f5fc675-cd47-414c-9535-12821ddfc554)。

> [!NOTE]
> 重定向后，用户可能会继续使用Internet Explorer兼容性列表中未包含Internet Explorer网站。


<!-- ====================================================================== -->
## <a name="request-an-update-to-the-internet-explorer-compatibility-list"></a>请求更新兼容性Internet Explorer列表

该Internet Explorer兼容性列表是一个 [XML 文件 microsoft.com](https://www.microsoft.com)。  此列表会定期更新，以响应用户和网站开发人员有关添加或删除网站的请求。  对列表的更新会自动下载到用户计算机。

将以下信息通过电子邮件发送 [ietoedge@microsoft.com](mailto:ietoedge@microsoft.com) ，以从兼容性列表中添加或删除Internet Explorer网站。

*   所有者名称
*   公司标题
*   电子邮件地址
*   公司名称
*   街道地址
*   网站地址

兼容性Internet Explorer一周内更新。

> [!NOTE]
> 此Internet Explorer兼容性列表仅适用于公共网站。
