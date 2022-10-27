---
title: 迁移到清单 V3 的概述和日程表
description: 从清单 V2 迁移到 V3 将有助于减少开发人员的 Web 碎片，并增强最终用户的隐私、安全性和性能。 本文介绍从清单 V2 迁移到 V3 的概述和时间线。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: extensions
ms.date: 5/09/2022
ms.openlocfilehash: ea693feab0449cc4faff1af61498b2b7c4d25227
ms.sourcegitcommit: 31669c03063cb6de515ba9c6d57a9cd8658f445e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2022
ms.locfileid: "12841135"
---
# <a name="overview-and-timelines-for-migrating-to-manifest-v3"></a>迁移到清单 V3 的概述和日程表

清单文件是扩展的蓝图。 它包括扩展的版本号、扩展的标题以及运行扩展所需的权限等信息。 从清单 V2 迁移到 V3 将对浏览器处理扩展的方式进行一些结构性更改。

2020 年 10 月，Microsoft 宣布 [决定采用清单 V3](https://blogs.windows.com/msedgedev/2020/10/14/extension-manifest-chromium-edge/) ，以帮助减少所有开发人员的 Web 碎片，并增强最终用户的隐私、安全性和性能。

清单 V3 是 [Chromium 项目的](https://www.chromium.org/Home/)一项计划。 清单 V2 支持将于 2023 年 6 月结束，所有基于 Chromium 的浏览器。

有关更改的概述，如 [清单 V3 - Chrome 开发人员概述](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-overview/)中所述：

* 服务辅助角色将替换后台页。

* 网络请求修改将由新 `declarativeNetRequest` API 处理。

* 将不再允许远程托管代码。 扩展只能执行其自己的包中包含的 JavaScript。

* 承诺支持将添加到许多方法。 仍将支持回调作为替代方法。

* 清单 V3 中还会引入一些次要功能改进。

为了帮助你进行规划，请考虑以下 Microsoft 合作伙伴中心和 Microsoft Edge 更改计划。

我们目前正在更新 MV3 迁移时间线。

我们知道，Chrome 已修改了清单 V2 日落的时间线，到目前为止，我们将继续遵循Chromium的时间线。 我们将继续分析扩展开发人员提出的问题，并探索 Microsoft Edge 加载项生态系统的最佳路径。 我们将独立决定 Microsoft Edge 加载项的 MV3 迁移时间线，并在此处分享更新。 同时，请参阅[Chromium时间线](https://developer.chrome.com/docs/extensions/mv3/mv2-sunset/)来规划扩展的迁移。


| 时间 | Microsoft 合作伙伴中心更改 | Microsoft Edge 更改 |
|--- |--- |--- |
| 2022 年 7 月 | Microsoft 合作伙伴中心将不再接受将可见性设置为 `Hidden` 或 `Public`的新清单 V2 扩展。 | 无更改。 |
| TBD - 请参阅上面的说明 | Microsoft 合作伙伴中心将不再接受对现有清单 V2 扩展的更新。 开发人员可以提交更新，以便将 V2 扩展迁移到 V3。 | Microsoft Edge 停止运行清单 V2 扩展。 企业可以使用企业策略允许清单 V2 扩展在 Microsoft Edge 上运行。 |
| TBD - 请参阅上面的说明 | 无更改。 | 即使使用企业策略，清单 V2 扩展也不会在 Microsoft Edge 中运行。 |

Microsoft 会继续迭代地改进平台，并解决扩展开发人员共享的反馈。

在 Twitter [@MSEdgeDev](https://twitter.com/msedgedev/) 或通过 [TechCommunity 上的 Microsoft Edge 预览体验成员论坛](https://techcommunity.microsoft.com/t5/articles/manifest-v3-changes-are-now-available-in-microsoft-edge/m-p/1780254)与团队分享你的问题、评论和疑虑。
