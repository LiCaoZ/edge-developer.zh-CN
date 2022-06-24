---
title: 将 Chrome 扩展移植到Microsoft Edge
description: 将 Chrome 扩展移植到Microsoft Edge的过程。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: 98ea2752b4f92ed105c803e35c4de7b8455cb3bd
ms.sourcegitcommit: 5438bc89031609ad4045a96476ae29718561bac0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2022
ms.locfileid: "12612194"
---
# <a name="port-a-chrome-extension-to-microsoft-edge"></a>将 Chrome 扩展移植到Microsoft Edge

只需进行很少的更改，Microsoft Edge 便可支持你将 Chrome 扩展移植到 Microsoft Edge。  Chrome 支持的扩展 API 和清单密钥与Microsoft Edge兼容代码。  有关Microsoft Edge支持的 API 列表，请参阅 [API 支持](api-support.md)。

移植 Chrome 扩展：

1. 查看扩展中使用的 Chrome 扩展 API，其中包含[Microsoft Edge扩展支持的 API](api-support.md) 列表。

   > [!NOTE]
   > 如果扩展使用Microsoft Edge不支持的 API，则可能无法直接移植。

1. `update_URL`从清单文件中删除字段。

1. 如果 `Chrome` 在扩展的名称或说明中使用，请使用 `Microsoft Edge`>a0/a0> 重新命名扩展。  若要通过认证过程，需要进行更改。

1. 通过[旁加载](../getting-started/extension-sideloading.md)扩展来测试扩展，检查扩展是否在Microsoft Edge中工作。

1. 如果遇到任何问题，可以使用 DevTools 在Microsoft Edge中调试扩展，或[与我们联系](mailto:ext_dev_support@microsoft.com)。

1. 按照[发布指南](../publish/publish-extension.md)在Microsoft Edge加载项网站上发布扩展。


<!-- ====================================================================== -->
## <a name="setting-allowed_origins-for-a-native-app"></a>为本机应用设置allowed_origins

如果扩展使用`chrome.runtime.connectNative`本机应用交换消息，请确保已设置为`allowed_origins``chrome-extension://[Microsoft-Catalog-extensionID]`本机消息传送主机清单文件中。  此设置允许应用标识扩展。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

扩展包准备好在Microsoft Edge加载项网站中发布后，[创建开发人员帐户](../publish/create-dev-account.md)并[发布扩展](../publish/publish-extension.md)。
