---
title: 将 Chrome 扩展移植到Microsoft Edge
description: 将 Chrome 扩展移植到 Microsoft Edge。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: 8db869d5571899c0989aa1cd60a2b0197886c445
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432624"
---
# <a name="port-a-chrome-extension-to-microsoft-edge"></a>将 Chrome 扩展移植到Microsoft Edge

只需进行很少的更改，Microsoft Edge 便可支持你将 Chrome 扩展移植到 Microsoft Edge。  Chrome 支持的扩展 API 和清单密钥与 Microsoft Edge。  有关受 API 支持Microsoft Edge，请参阅 [API 支持](api-support.md)。

移植 Chrome 扩展：

1. 查看扩展中使用的 Chrome 扩展 API 和Microsoft Edge支持[扩展的 API](api-support.md) 列表。

   > [!NOTE]
   > 如果你的扩展使用的 API 不受 Microsoft Edge，它可能不会直接移植。

1. 在清单文件中，将字段 `update_URL` 设置为 `https://edge.microsoft.com/extensionwebstorebase/v1/crx`。  值指向加载项网站`.crx`中扩展Microsoft Edge文件，并允许Microsoft Edge检查扩展更新。

1. 如果在 `Chrome` 扩展的名称或说明中使用的，则使用 重新命名扩展 `Microsoft Edge`。  若要通过认证过程，需要更改。

1. 通过旁加载扩展，测试扩展Microsoft Edge[是否正常工作](../getting-started/extension-sideloading.md)。

1. 如果你面临任何问题，可以使用 DevTools 在 Microsoft Edge中调试扩展，或[联系我们](mailto:ext_dev_support@microsoft.com)。

1. 按照[发布指南在](../publish/publish-extension.md)加载项网站上Microsoft Edge扩展。


<!-- ====================================================================== -->
## <a name="setting-allowed_origins-for-a-native-app"></a>为allowed_origins应用设置应用

如果扩展使用 与本机应用交换邮件`chrome.runtime.connectNative`，请确保在`allowed_origins``extension://[Microsoft-Catalog-extensionID]`本机消息传递主机清单文件中设置为 。  该设置允许应用标识你的扩展。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

准备好在加载项网站中发布扩展Microsoft Edge，创建开发者帐户并[发布扩展](../publish/publish-extension.md)。 [](../publish/create-dev-account.md)
