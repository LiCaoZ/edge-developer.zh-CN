---
title: 将用户从Internet Explorer移动到Microsoft Edge
description: 将用户从 Internet Explorer 移动到Microsoft Edge。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 2/8/2022
ms.openlocfilehash: 5fb5f918167b0652c54dd9998d4b18ba32952a9b
ms.sourcegitcommit: 8aee95757de12c62f4a74d37649ad5979f9e0ba9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2022
ms.locfileid: "12550799"
---
# <a name="move-users-to-microsoft-edge-from-internet-explorer"></a>将用户从Internet Explorer移动到Microsoft Edge

许多新式网站的设计与 Internet Explorer 不兼容。  当 Internet Explorer 用户访问不兼容的公共网站时，网站可能会指示用户网站与 Internet Explorer 不兼容，并且用户必须切换到更现代的浏览器才能使用该网站。

为了最大程度地减少中断，Microsoft Edge支持自动重定向用户的新功能。  当 Internet Explorer 用户转到与 Internet Explorer 不兼容的网站时，Windows可以自动将用户重定向到Microsoft Edge。  仅重定向属于[“需要Microsoft Edge”列表](https://edge.microsoft.com/neededge/v1)的网站。


<!-- ====================================================================== -->
## <a name="redirection-experience"></a>重定向体验

重定向到Microsoft Edge时，用户会在下一个屏幕截图中显示一次性对话框。  对话框为用户提供以下信息：
*  它解释了网站被重定向的原因。
*  它会提示用户同意将浏览数据和首选项从 Internet Explorer 复制到Microsoft Edge。

导入以下浏览数据：
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

如果用户未通过从 Internet Explorer 复选框中选择 **“始终引入我的浏览数据和首选项** ”来表示同意，则用户可以选择 **“继续浏览** ”以继续浏览会话。

最后，每个重定向的地址栏下会显示网站不兼容性横幅。  下图显示了网站不兼容性横幅的示例。

:::image type="content" source="../media/neededge-banner.msft.png" alt-text="有关新式网站的通知，以及将 Microsoft Edge 设置为默认浏览器或浏览 Microsoft Edge 的提示。" lightbox="../media/neededge-banner.msft.png":::

网站不兼容性横幅向用户提供以下详细信息。

*   建议用户切换到Microsoft Edge。
*   将Microsoft Edge设置为默认浏览器的产品/服务。
*   为用户提供浏览Microsoft Edge的选项。

当网站从 Internet Explorer 重定向到 Microsoft Edge 时，将发生以下操作之一。

*   如果活动 Internet Explorer 选项卡没有以前的内容，则会关闭它。
*   如果活动 Internet Explorer 选项卡具有以前的内容，则会导航到 [Microsoft 支持页面，该页面解释了网站重定向到 Microsoft Edge 的原因](https://support.microsoft.com/office/the-website-you-were-trying-to-reach-doesn-t-work-with-internet-explorer-8f5fc675-cd47-414c-9535-12821ddfc554)。

> [!NOTE]
> 重定向后，用户可能会继续对不在 Internet Explorer 兼容性列表中的网站使用 Internet Explorer。


<!-- ====================================================================== -->
## <a name="request-an-update-to-the-internet-explorer-compatibility-list"></a>请求更新 Internet Explorer 兼容性列表

Internet Explorer 兼容性列表是 [microsoft.com](https://www.microsoft.com) 上的 XML 文件。  该列表会定期更新，以响应用户和网站开发人员要求添加或删除网站的请求。  对列表的更新会自动下载到用户计算机。

通过电子邮件将以下信息发送到 [ietoedge@microsoft.com](mailto:ietoedge@microsoft.com) ，以便从 Internet Explorer 兼容性列表中添加或删除您的网站。

*   所有者名称
*   公司游戏
*   电子邮件地址
*   公司名称
*   街道地址
*   网站地址

Internet Explorer 兼容性列表通常在一周内更新。 如果你遇到超过一周的等待时间，我们可能正在解决服务中断。

> [!NOTE]
> Internet Explorer 兼容性列表旨在仅适用于公共网站。
