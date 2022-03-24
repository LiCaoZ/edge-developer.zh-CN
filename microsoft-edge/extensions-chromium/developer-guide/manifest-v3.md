---
title: 迁移到清单 V3 的概述和日程表
description: 从清单 V2 迁移到 V3 有助于减少开发人员的 Web 碎片，并增强最终用户的隐私、安全性和性能。 本文介绍了从清单 V2 迁移到 V3 的概述和日程表。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: extensions
ms.date: 3/11/2022
ms.openlocfilehash: 078d3d7923f542d37431654409ad73aa501c5bc0
ms.sourcegitcommit: 84f082d551d165ad46811e7d761a474ed6c1dd6f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2022
ms.locfileid: "12463498"
---
# <a name="overview-and-timelines-for-migrating-to-manifest-v3"></a>迁移到清单 V3 的概述和日程表

清单文件是扩展的蓝图。 其中包括诸如扩展的版本号、扩展标题以及运行扩展所需的权限等信息。 从清单 V2 迁移到 V3 将给浏览器处理扩展的方式带来一些结构性更改。

2020 年 10 月，Microsoft 宣布决定采用清单 [V3](https://blogs.windows.com/msedgedev/2020/10/14/extension-manifest-chromium-edge/) ，以帮助所有开发人员减少 Web 碎片，并提高最终用户的隐私、安全性和性能。

清单 V3 是项目Chromium[计划](https://www.chromium.org/Home/)。 清单 V2 支持将于 2023 年 6 月结束，适用于Chromium浏览器。

相关更改的概述，如清单 [V3 - Chrome 开发人员概述中所述](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-overview/)：

* 服务工作人员将替换背景页。

* 网络请求修改将由新 API 处理 `declarativeNetRequest` 。

* 不再允许远程托管的代码。 扩展将只能执行包含在其自己的包中的 JavaScript。

* 承诺支持将添加到许多方法中。 回调仍将作为替代方法受到支持。

* 清单 V3 中还将引入一些次要功能改进。

为帮助你进行规划，请考虑以下 Microsoft 合作伙伴中心计划，Microsoft Edge更改。

此时间线可能会更改。 本文将进行更新，以随着里程碑的临近而共享确切详细信息。

| 时间范围 | Microsoft 合作伙伴中心更改 | Microsoft Edge更改 |
|--- |--- |--- |
| 2022 年 6 月 | Microsoft 合作伙伴中心将不再接受可见性设置为 或 的新清单 V2 `Hidden` 扩展 `Public`。 | 没有变化。 |
| 2023 年 1 月 | Microsoft 合作伙伴中心将不再接受对现有清单 V2 扩展的更新。 开发人员可以提交更新，以将 V2 扩展迁移到 V3。 | Microsoft Edge停止运行清单 V2 扩展。 企业可以允许清单 V2 扩展使用Microsoft Edge在Enterprise运行。 |
| 2023 年 6 月 | 没有变化。 | 清单 V2 扩展将不再Microsoft Edge，即使使用策略Enterprise。 |

Microsoft 将继续反复改进平台并解决扩展开发人员共享的反馈。

在 Twitter 上或通过  [TechCommunity](https://techcommunity.microsoft.com/t5/articles/manifest-v3-changes-are-now-available-in-microsoft-edge/m-p/1780254) 上的预览体验成员@MSEdgeDev分享你的[](https://twitter.com/msedgedev/)问题、意见和问题Microsoft Edge团队。
