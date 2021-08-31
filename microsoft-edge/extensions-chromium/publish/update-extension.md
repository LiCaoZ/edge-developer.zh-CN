---
description: 更新或删除加载项Microsoft Edge扩展。
title: 更新Microsoft Edge扩展
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/17/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: 11d844327d2d4a652745cb73b311f4a97b6174d7
ms.sourcegitcommit: dc445eae30234af1ad3fa42645aabb940529912b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "11934310"
---
# <a name="update-a-microsoft-edge-extension"></a>更新Microsoft Edge扩展  

你随时都可以更新提交的扩展或删除Microsoft Edge加载项网站中的已发布扩展列表。  

> [!NOTE]
> 更新扩展的认证过程可能需要几个小时到几天的时间。

## <a name="update-an-existing-extension-in-the-microsoft-edge-add-ons-website"></a>更新加载项网站Microsoft Edge扩展  

若要更新应用商店上的扩展，请进行以下操作：

1.  导航到 [开发人员仪表板][MicrosoftPartnerCenter] ，然后选择要更新的扩展。  

1.  更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本。  

1.  进行更改后，选择"保存**发布**"以  >  **** 更新扩展列表，并开始认证过程。  

1.  列 `Status` 显示后 `In the store` ，你的扩展更新将在 Microsoft Edge 加载项网站上提供。  

<!-- todo: uncomment after the API is available for use.
After your extension has been initially created, you will be able to update it programmatically by [Using the Microsoft Edge Add-ons API][UsingAddonsAPI].
-->


## <a name="update-your-extension-during-the-certification-step"></a>在认证步骤中更新扩展  

虽然扩展仍处于认证阶段，且在将其发布到 Microsoft Edge 加载项网站之前，你可以更新它。 如果你的扩展未能通过认证过程，你可能还需要更新你的扩展。    

若要检查扩展的状态，请导航到与合作伙伴中心上的一览 [相关联的仪表板][MicrosoftPartnerCenter]。  

若要编辑提交：

1.  导航到 [开发人员仪表板][MicrosoftPartnerCenter] ，然后选择要更新的扩展。  将显示你在上一次提交期间填写的信息。  

1.  若要打开 **扩展概述** 部分，请使用左侧导航栏。  若要取消当前提交，请选择"取消**提交"。**  

1.  移动到其他部分，并更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本，以匹配自上一个程序包版本以来的更改。  

1.  进行更改后，选择"保存**发布**  >  **"。**  
    
> [!IMPORTANT]
> 此过程会停止当前提交，并从 Microsoft Edge扩展认证管道中删除你的当前提交，并且新评审从最新提交开始。  


## <a name="update-your-extension-after-it-failed-the-certification"></a>在认证失败后更新扩展  

扩展失败认证过程后，你需要更新扩展并重新提交包含反馈的扩展。  

编辑扩展：

1.  导航到 [开发人员仪表板][MicrosoftPartnerCenter] 并选择未通过认证过程的扩展。  

1.  更新扩展包或包含从认证过程收到的反馈的元数据。  如果更新扩展包，请确保增加清单文件中的版本。  

1.  进行更改后，选择"保存**发布**  >  **"。**  

    
## <a name="remove-an-extension-from-the-microsoft-edge-add-ons-website"></a>从加载项网站Microsoft Edge扩展

若要从加载项网站Microsoft Edge扩展：

1.  导航到开发人员 [仪表板][MicrosoftPartnerCenter]。  从"仪表板"页中，选择要删除的一览。  

1.  选择 **一览上的扩展** 概述。  

1.  选择 **"取消发布**"以从加载项Microsoft Edge列表中删除列表。  
    
扩展现已从加载项Microsoft Edge中删除。  已安装扩展的用户可以继续使用它，但新用户找不到它。  

<!-- links -->
[UsingAddonsAPI]: api/using-addons-api.md "使用Microsoft Edge加载项 API |Microsoft Docs"
<!-- external links -->
[MicrosoftPartnerCenter]: https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd "合作伙伴中心"  
