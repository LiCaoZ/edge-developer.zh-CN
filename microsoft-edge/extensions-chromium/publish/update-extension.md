---
title: 更新Microsoft Edge扩展
description: 更新或删除加载项Microsoft Edge扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: 86b914e328948b7efd31c95ad3fdf3bf61496d43
ms.sourcegitcommit: fa1b0662af7c59a37f96260e5aba1922343d1ae7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2022
ms.locfileid: "12437482"
---
# <a name="update-a-microsoft-edge-extension"></a>更新Microsoft Edge扩展

你随时都可以更新提交的扩展或删除Microsoft Edge加载项网站中的已发布扩展列表。

> [!NOTE]
> 更新扩展的认证过程可能需要几个小时到几天的时间。


<!-- ====================================================================== -->
## <a name="update-an-existing-extension-in-the-microsoft-edge-add-ons-website"></a>更新加载项网站Microsoft Edge扩展

若要更新应用商店上的扩展，请进行以下操作：

1.  导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择要更新的扩展。

1.  更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本。

2.  进行更改后，选择" **发布"** 以更新扩展列表，并开始认证过程。

3.  `Status`列显示后`In the store`，你的扩展更新将在Microsoft Edge加载项网站上提供。

<!-- todo: uncomment after the API is available for use.
After your extension has been initially created, you will be able to update it programmatically by [Using the Microsoft Edge Add-ons API (in private preview)](api/using-addons-api.md).
-->


<!-- ====================================================================== -->
## <a name="update-your-extension-during-the-certification-step"></a>在认证步骤中更新扩展

虽然扩展仍处于认证阶段，且在将其发布到 Microsoft Edge 加载项网站之前，你可以更新它。 如果你的扩展未能通过认证过程，你可能还需要更新扩展。

若要检查扩展的状态，请导航到与合作伙伴中心上的一览相关联的 [仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)。

若要编辑提交：

1.  导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择要更新的扩展。  将显示你在上一次提交期间填写的信息。

1.  若要打开 **扩展概述** 部分，请使用左侧导航栏。  若要取消当前提交，请选择" **取消提交"**。

1.  移动到其他部分并更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本，以匹配自上一个程序包版本以来的更改。

2.  进行更改后，选择"发布 **"**。

> [!IMPORTANT]
> 此过程会停止当前提交并从 Microsoft Edge 扩展认证管道中删除你的当前提交，并且新评审从最新提交开始。


<!-- ====================================================================== -->
## <a name="update-your-extension-after-it-failed-the-certification"></a>在认证失败后更新扩展

扩展失败认证过程后，你需要更新扩展并重新提交包含反馈的扩展。

编辑扩展：

1.  导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) 并选择未通过认证过程的扩展。

1.  更新扩展包或包含从认证过程收到的反馈的元数据。  如果更新扩展包，请确保增加清单文件中的版本。

2.  进行更改后，选择"发布 **"**。


<!-- ====================================================================== -->
## <a name="remove-an-extension-from-the-microsoft-edge-add-ons-website"></a>从加载项网站Microsoft Edge扩展

若要从加载项网站Microsoft Edge扩展：

1.  导航到开发人员 [仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)。  从"仪表板"页中，选择要删除的一览。

1.  选择 **一览上的扩展** 概述。

1.  选择 **"取消发布**"以从加载项Microsoft Edge列表中删除列表。

扩展现已从加载项Microsoft Edge中删除。  已安装扩展的用户可以继续使用它，但新用户找不到它。
