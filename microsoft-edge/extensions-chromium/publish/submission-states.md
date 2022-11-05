---
title: Microsoft Edge 加载项网站中扩展的提交状态
description: 了解向 Microsoft Edge 加载项网站提交扩展时的不同状态。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/04/2022
ms.openlocfilehash: fa5b6496d70c3fe3bdba12c4377e8c71c3c290c9
ms.sourcegitcommit: 4191964fa3c15e4133667be285a9373bed5cb6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2022
ms.locfileid: "12854868"
---
# <a name="submission-states-for-extensions-in-the-microsoft-edge-add-ons-website"></a>Microsoft Edge 加载项网站中扩展的提交状态

合作伙伴中心的概述页显示扩展在整个提交流中的状态。  本文介绍在提交和认证过程中，扩展随时可能处于的不同状态。

| # |  State |  详细信息 |
|:--- |:--- |:--- |
| 1 |  草稿中 |  创建提交并将草稿保存到帐户。  你尚未提交要发布到 Microsoft Edge 加载项网站的扩展包和提交表单详细信息。  处于此状态的用户无法使用扩展。  |
| 2|  审阅中 |  你已提交扩展。  Microsoft 会审核你的扩展包和提交表单详细信息。  处于此状态的用户无法使用扩展。  |
| 3|  正在等待发布 |  扩展评审完成后，提交将处于此状态，并且你的扩展正在准备在 Microsoft Edge 加载项网站上发布。  此状态是 和 `In the store`之间的`In review`中间状态。  并非所有提交都会出现此状态。  |
| 4|  在应用商店中 |  评审现已完成，你的扩展已发布在 Microsoft Edge 加载项网站上。  你的扩展可在你指定的市场中的 Microsoft Edge 加载项网站上获得。  |
| 5 |  在应用商店中。  审阅中的更新 |  你的扩展将发布到 Microsoft Edge 加载项网站，并且你已提交由 Microsoft 审查的更新。  |
| 6 |  审阅失败 |  如果扩展未通过评审，则提交将处于此状态。  在初始评审或更新期间，评审可能会失败。  需要采取纠正措施并重新提交扩展。  |
| 7 |  在商店中不可用 |  当扩展显示此状态时，有三种可能的方案：  **“已从存储中未发布**”、“ **从存储中删除”** 和 **“已阻止**”。  这三种状态中的每一种的描述在 8、9 和 10 中指定。  |
| 8 |  从存储中取消发布 |  你已从合作伙伴中心的 Microsoft Edge 加载项网站取消发布扩展。  在合作伙伴中心，你在扩展提交页上选择了 **“取消发布** ”。  取消发布扩展后，Microsoft Edge 加载项网站上不再提供可供新用户下载的扩展，但现有用户可以继续使用其扩展副本。  |
| 9 |  从存储中删除 |  如果发现你的扩展违反了 Microsoft Edge 加载项网站的条款和条件，Microsoft 可能会将其从 Microsoft Edge 加载项网站中删除，然后状态会更改为此状态。  <br />  Microsoft 删除扩展后，Microsoft Edge 加载项网站上不再提供扩展供新用户下载，但现有用户可以继续使用其扩展副本。  |
| 10 |  阻止 |  如果你的扩展被发现是恶意的，并损害了用户的安全和隐私，Microsoft 有权阻止你的扩展从 Microsoft Edge 加载项网站，并且状态会更改为此状态。  如果扩展被阻止，则会从 Microsoft Edge 加载项网站和所有用户设备中删除该扩展。  |
