---
title: 更新 Microsoft Edge 扩展
description: 从 Microsoft Edge 加载项网站更新或删除扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/04/2022
ms.openlocfilehash: c9127b3aa14a8e2ba474efbc6f82172d84c21df4
ms.sourcegitcommit: 4191964fa3c15e4133667be285a9373bed5cb6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2022
ms.locfileid: "12854861"
---
# <a name="update-a-microsoft-edge-extension"></a>更新 Microsoft Edge 扩展

可以随时从 Microsoft Edge 加载项网站更新提交的扩展或删除已发布的扩展列表。


<!-- ====================================================================== -->
## <a name="update-an-existing-extension-in-the-microsoft-edge-add-ons-website"></a>更新 Microsoft Edge 加载项网站中的现有扩展

若要在应用商店中更新扩展，请执行以下步骤：

1.  转到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，选择要更新的扩展。

1.  更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本号。

1.  进行更改后，选择“ **发布** ”以更新扩展列表，并开始认证过程。

    > [!NOTE]
    > 更新扩展的认证过程最多可能需要 7 个工作日。

1.  列 `Status` 显示 `In the store`后，Microsoft Edge 加载项网站上提供了扩展更新。

> [!TIP]
> 最初创建扩展后，你将能够 [使用 Microsoft Edge 加载项 API (Beta) ](api/using-addons-api.md)以编程方式更新它。


<!-- ====================================================================== -->
## <a name="update-your-extension-during-the-certification-step"></a>在认证步骤中更新扩展

当你的扩展处于认证阶段，并在它发布到 Microsoft Edge 加载项网站之前，你可以更新它。 如果扩展未通过认证过程，可能还需要更新扩展。

若要检查扩展的状态，请转到与 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)上一览关联的仪表板。

若要编辑提交，请执行以下步骤：

1. 转到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，选择要更新的扩展。  将显示你在上一次提交期间填写的信息。

1. 若要打开 **“扩展概述** ”部分，请使用左侧导航栏。  若要取消当前提交，请选择“ **取消提交**”。

1. 转到其他部分并更新扩展包或扩展的元数据。  如果更新扩展包，请确保增加清单文件中的版本号，以匹配自上一个包提交以来的更改。

1. 完成更改后，选择“ **发布**”。

> [!IMPORTANT]
> 该过程将停止，并从 Microsoft Edge 扩展认证管道中删除当前提交，新的评审从最新提交开始。


<!-- ====================================================================== -->
## <a name="update-your-extension-after-it-failed-the-certification"></a>在认证失败后更新扩展

扩展未通过认证过程后，需要更新扩展并重新提交扩展，并合并获得的反馈。

若要编辑扩展，请执行以下步骤：

1. 导航到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，选择认证过程失败的扩展。

1. 更新扩展包或元数据，并合并从认证过程收到的反馈。  如果更新扩展包，请确保在清单文件中增加版本。

1. 进行更改后，选择“ **发布**”。


<!-- ====================================================================== -->
## <a name="remove-an-extension-from-the-microsoft-edge-add-ons-website"></a>从 Microsoft Edge 加载项网站中删除扩展

若要删除扩展，请执行以下步骤：

1. 转到 [开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)。  从“仪表板”页中，选择要删除的列表。

1. 在列表上选择“ **扩展概述** ”。

1. 选择“ **取消发布** ”以从 Microsoft Edge 加载项网站中删除列表。

此扩展现已从 Microsoft Edge 加载项网站中删除。  已安装扩展的用户可以继续使用它，但该扩展对新用户不可用。
