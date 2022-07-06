---
title: 更新 Microsoft Edge 扩展
description: 更新或删除 Microsoft Edge 加载项网站中的扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: d2957df94d7b4ed91198df400d3ddb94387988de
ms.sourcegitcommit: 108b9a0673be978d89bc99d923582f569a43f6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2022
ms.locfileid: "12635414"
---
# <a name="update-a-microsoft-edge-extension"></a>更新 Microsoft Edge 扩展

可以随时从 Microsoft Edge 加载项网站更新提交的扩展或删除已发布的扩展列表。

更新到扩展的认证过程最多可能需要 7 个工作日。


<!-- ====================================================================== -->
## <a name="update-an-existing-extension-in-the-microsoft-edge-add-ons-website"></a>更新 Microsoft Edge 加载项网站中的现有扩展

若要更新应用商店上的扩展，请执行以下操作：

1.  导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择要更新的扩展。

1.  更新扩展包或扩展的元数据。  如果更新扩展包，请确保在清单文件中增加版本。

1.  进行更改后，选择 **“发布** ”以更新扩展列表，并启动认证过程。

1.  `Status`列显示`In the store`后，扩展更新在 Microsoft Edge 加载项网站上可用。

在最初创建扩展后，你将能够 [使用 Microsoft Edge 加载项 API (Beta) ](api/using-addons-api.md)以编程方式更新它。


<!-- ====================================================================== -->
## <a name="update-your-extension-during-the-certification-step"></a>在认证步骤期间更新扩展

虽然你的扩展仍处于认证阶段，并且在发布到 Microsoft Edge 加载项网站之前，你可以更新它。 如果扩展在认证过程中失败，则可能需要更新扩展。

若要检查扩展的状态，请导航到与 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)列表关联的仪表板。

若要编辑提交，

1. 导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择要更新的扩展。  显示在上一次提交期间填写的信息。

1. 若要打开 **“扩展概述** ”部分，请使用左侧导航栏。  若要取消当前提交，请选择 **“取消提交**”。

1. 移动到其他部分并更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本以匹配自上一个包版本以来的更改。

1. 进行更改后，选择 **“发布**”。

> [!IMPORTANT]
> 此过程会停止并从 Microsoft Edge 扩展认证管道中删除当前提交，新的评审从最新提交开始。


<!-- ====================================================================== -->
## <a name="update-your-extension-after-it-failed-the-certification"></a>在认证失败后更新扩展

在扩展失败后，需要更新扩展并重新提交包含反馈的扩展。

编辑扩展：

1. 导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择认证过程失败的扩展。

1. 更新扩展包或包含从认证过程中收到的反馈的元数据。  如果更新扩展包，请确保在清单文件中增加版本。

1. 进行更改后，选择 **“发布**”。


<!-- ====================================================================== -->
## <a name="remove-an-extension-from-the-microsoft-edge-add-ons-website"></a>从 Microsoft Edge 加载项网站中删除扩展

若要从 Microsoft Edge 加载项网站中删除扩展，请执行以下操作：

1. 导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)。  在“仪表板”页上，选择要删除的列表。

1. 在列表中选择 **“扩展概述** ”。

1. 选择 **“取消发布** ”以从 Microsoft Edge 加载项网站中删除列表。

此扩展现已从 Microsoft Edge 加载项网站中删除。  已安装扩展的用户可以继续使用它，但新用户找不到它。
