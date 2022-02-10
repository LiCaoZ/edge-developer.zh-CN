---
title: 将用户从Microsoft Edge移动Internet Explorer
description: 将用户从Microsoft Edge移动Internet Explorer。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 2/8/2022
ms.openlocfilehash: 8d73bfa50eb54871bf42388b2a99d7b8d83bb312
ms.sourcegitcommit: 82de2fa19bf9c925ff5faafe8be6b24d21767e03
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2022
ms.locfileid: "12346314"
---
# <a name="move-users-to-microsoft-edge-from-internet-explorer"></a>将用户从Microsoft Edge移动Internet Explorer

许多新式网站的设计与 Internet Explorer 不兼容。

当 Internet Explorer用户访问不兼容的公共网站时，网站可能会指示用户该网站与 Internet Explorer 不兼容，并且用户必须切换到更现代浏览器才能使用该网站。

为了最大限度地减少中断，Microsoft Edge自动重定向用户的新功能。  当用户Internet Explorer网站与网站不兼容时，Internet Explorer Windows自动将用户重定向到Microsoft Edge。  仅重定向属于"需要"列表[Microsoft Edge](https://edge.microsoft.com/neededge/v1)网站。


<!-- ====================================================================== -->
## <a name="redirection-experience"></a>重定向体验

当重定向到Microsoft Edge时，用户会显示下一张屏幕截图中的一次对话框。  该对话框为用户提供以下信息：
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

如果用户未通过选中"始终从 Internet Explorer 显示我的浏览数据和首选项"复选框来同意，用户可以选择"继续**浏览"****** 以继续浏览会话。

最后，网站不兼容横幅将显示在每个重定向的地址栏下。  下图显示了网站不兼容横幅的示例。

:::image type="complex" source="../media/neededge-banner.msft.png" alt-text="有关新式网站的通知，以及将 Microsoft Edge 设置为默认浏览器或浏览 Microsoft Edge 的提示。" lightbox="../media/neededge-banner.msft.png":::
   有关新式网站的通知，并提示将Microsoft Edge设置为默认浏览器或浏览Microsoft Edge
:::image-end:::

网站不兼容横幅为用户提供了以下详细信息。

*   建议用户切换到Microsoft Edge。
*   产品/Microsoft Edge设置为默认浏览器。
*   为用户提供浏览Microsoft Edge。

将网站从 Internet Explorer Microsoft Edge 时，将发生以下操作之一。

*   如果活动"Internet Explorer"选项卡没有之前的内容，则关闭该选项卡。
*   如果活动Internet Explorer选项卡包含之前的内容，它将导航到 Microsoft 支持页面，说明网站重定向到 [Microsoft Edge 的原因](https://support.microsoft.com/office/the-website-you-were-trying-to-reach-doesn-t-work-with-internet-explorer-8f5fc675-cd47-414c-9535-12821ddfc554)。

> [!NOTE]
> 重定向后，用户可能会继续使用Internet Explorer兼容性列表中未包含Internet Explorer网站。


<!-- ====================================================================== -->
## <a name="request-an-update-to-the-internet-explorer-compatibility-list"></a>请求更新兼容性Internet Explorer列表

该Internet Explorer兼容性列表是一个 XML 文件，位于 [microsoft.com](https://www.microsoft.com)。  此列表会定期更新，以响应用户和网站开发人员有关添加或删除网站的请求。  对列表的更新会自动下载到用户计算机。

将以下信息通过电子邮件发送 [ietoedge@microsoft.com](mailto:ietoedge@microsoft.com) ，以添加或删除网站Internet Explorer兼容性列表。

*   所有者名称
*   公司标题
*   电子邮件地址
*   公司名称
*   街道地址
*   网站地址

兼容性Internet Explorer一周内更新。

> [!NOTE]
> 此Internet Explorer兼容性列表仅适用于公共网站。
