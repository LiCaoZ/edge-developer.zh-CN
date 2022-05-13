---
title: 迁移到清单 V3 的概述和日程表
description: 从清单 V2 迁移到 V3 有助于减少开发人员的 Web 碎片，并增强最终用户的隐私、安全和性能。 本文介绍从清单 V2 迁移到 V3 的概述和时间线。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: extensions
ms.date: 5/09/2022
ms.openlocfilehash: 68ff06b88f31f8383ce3d4076e95ec5ba480f3e3
ms.sourcegitcommit: 59e8749cdca66da97bbe9f7bbde42d8c491231ca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2022
ms.locfileid: "12513283"
---
# <a name="overview-and-timelines-for-migrating-to-manifest-v3"></a>迁移到清单 V3 的概述和日程表

清单文件是扩展的蓝图。 它包括诸如扩展版本号、扩展标题和运行扩展所需的权限等信息。 从清单 V2 迁移到 V3 会对浏览器处理扩展的方式带来一些结构性更改。

2020 年 10 月，Microsoft 宣布 [决定采用清单 V3](https://blogs.windows.com/msedgedev/2020/10/14/extension-manifest-chromium-edge/) ，以帮助减少所有开发人员的 Web 碎片，并增强最终用户的隐私、安全和性能。

清单 V3 是[Chromium项目的](https://www.chromium.org/Home/)一项计划。 清单 V2 支持将于 2023 年 6 月结束，适用于所有基于 Chromium 的浏览器。

有关更改的概述，如 [清单 V3 概述 - Chrome 开发人员](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-overview/)中所述：

* 服务工作者将替换后台页面。

* 网络请求修改将由新 `declarativeNetRequest` API 处理。

* 不再允许远程托管代码。 扩展将只能执行包含在其自己的包中的 JavaScript。

* 承诺支持将添加到许多方法。 回调仍可作为替代方法提供支持。

* 清单 V3 中还将引入一些次要功能改进。

若要帮助你进行规划，请考虑 Microsoft 合作伙伴中心的以下计划并Microsoft Edge更改。

此时间线可能会更改。 随着里程碑的临近，本文将更新为共享确切详细信息。

| 时间 | Microsoft 合作伙伴中心更改 | Microsoft Edge更改 |
|--- |--- |--- |
| 2022 年 7 月 | Microsoft 合作伙伴中心将不再接受新的清单 V2 扩展，其可见性设置为 `Hidden` 或 `Public`。 | 无更改。 |
| 2023 年 1 月 | Microsoft 合作伙伴中心将不再接受对现有清单 V2 扩展的更新。 开发人员可以提交更新以将 V2 扩展迁移到 V3。 | Microsoft Edge停止运行清单 V2 扩展。 企业可以使用Enterprise策略允许清单 V2 扩展在Microsoft Edge上运行。 |
| 2023 年 6 月 | 无更改。 | 清单 V2 扩展将不再在Microsoft Edge中运行，即使使用Enterprise策略。 |

Microsoft 继续以迭代方式改进平台并解决扩展开发人员共享的反馈问题。

在 Twitter [@MSEdgeDev](https://twitter.com/msedgedev/)上或通过  [TechCommunity Microsoft Edge 预览体验论坛](https://techcommunity.microsoft.com/t5/articles/manifest-v3-changes-are-now-available-in-microsoft-edge/m-p/1780254)与团队分享你的问题、评论和关注。
