---
title: Microsoft Edge加载项网站中扩展的提交状态
description: 了解向加载项网站提交扩展时Microsoft Edge状态。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: ea6ef685be19864a7568a7b79187c9bc6ad68557
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12320205"
---
# <a name="submission-states-for-extensions-in-the-microsoft-edge-add-ons-website"></a>Microsoft Edge加载项网站中扩展的提交状态

合作伙伴中心的概述页面显示整个提交流中的扩展状态。  本文介绍了你的扩展在提交和认证过程中随时可能处于的不同状态。

| # |  State |  详细信息 |
|:--- |:--- |:--- |
| 1 |  在草稿中 |  创建提交，然后向帐户保存草稿。  你尚未提交要发布到加载项网站的扩展包Microsoft Edge提交表单详细信息。  在此状态中，你的扩展不可用。  |
| 2|  审核中 |  你已提交扩展。  你的扩展包和提交表单详细信息由 Microsoft 查看。  在此状态中，你的扩展不可用。  |
| 3|  等待发布 |  扩展评审完成后，你的提交将进入此状态，并且你的扩展准备在 Microsoft Edge 加载项网站中发布。  此状态是 和 之间的中间 `In review` 状态 `In the store` 。  并非所有提交都显示此状态。  |
| 4|  在应用商店中 |  评论现已完成，您的扩展将发布到 Microsoft Edge 加载项网站。  你的扩展可在你Microsoft Edge的加载项网站上获取。  |
| 5 |  在应用商店中。  正在审查的更新 |  你的扩展将发布到 Microsoft Edge 加载项网站，并且你已提交 Microsoft 正在审查的更新。  |
| 6 |  审阅失败 |  如果扩展未通过审阅，则你的提交将在此状态。  在初始审阅期间或更新过程中，可能会发生失败评审。  你需要采取更正操作并重新提交扩展。  |
| 7 |  在应用商店中不可用 |  当扩展显示此状态时，有三种可能的情况：**** 从应用商店取消发布、从应用商店中删除**** 和**已阻止**。  三种状态分别在 8、9 和 10 中指定说明。  |
| 8 |  从应用商店中取消发布 |  你从合作伙伴中心中的Microsoft Edge加载项网站中取消发布扩展。  在合作伙伴中心中， **你选择在扩展提交** 页面上取消发布。  取消发布扩展后，Microsoft Edge 加载项网站中不再提供扩展供新用户下载，但现有用户可以继续使用其扩展副本。  |
| 9 |  从应用商店中删除 |  如果发现你的扩展违反 Microsoft Edge 加载项网站的条款和条件，Microsoft 可能会将其从 Microsoft Edge 加载项网站中删除，然后状态会更改到此状态。  <br />  Microsoft 删除扩展后，你的扩展在 Microsoft Edge 加载项网站上不再可用供新用户下载，但现有用户可以继续使用其扩展副本。  |
| 10 |  阻止 |  如果发现你的扩展是恶意扩展并损害用户的安全和隐私，Microsoft 有权阻止你的扩展从 Microsoft Edge 加载项网站，并且状态会更改到此状态。  如果你的扩展被阻止，它将从Microsoft Edge加载项网站和从所有用户设备中删除。  |
