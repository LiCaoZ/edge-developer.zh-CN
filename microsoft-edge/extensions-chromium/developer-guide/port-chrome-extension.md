---
description: 将 Chrome 扩展移植到 Microsoft Edge
title: 将 Chrome 扩展移植到Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/17/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: 82a96215a0b25be6b2b56227fb77eea09314157f
ms.sourcegitcommit: dc445eae30234af1ad3fa42645aabb940529912b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "11934289"
---
# <a name="port-a-chrome-extension-to-microsoft-edge"></a>将 Chrome 扩展移植到Microsoft Edge

Microsoft Edge允许你将 Chrome 扩展移植到Microsoft Edge更改最少。  Chrome 支持的扩展 API 和清单密钥与 Microsoft Edge。  有关受 API 支持的列表Microsoft Edge，请导航到 API[支持][ExtensionApiSupport]。  

若要移植 Chrome 扩展，请完成以下步骤。  

1.  查看扩展中使用的 Chrome 扩展 API 和Microsoft Edge支持扩展[的 API][ExtensionApiSupport]列表。  
    
    > [!NOTE]
    > 如果你的扩展使用的 API 不受 Microsoft Edge，它可能不会直接移植。  
    
1.  在清单文件中，将 `update_URL` 字段设置为 `https://edge.microsoft.com/extensionwebstorebase/v1/crx` 。  值指向加载项网站中扩展Microsoft Edge文件，并允许Microsoft Edge检查 `.crx` 扩展更新。  
1.  如果在 `Chrome` 扩展的名称或说明中使用的，则使用 重新命名扩展 `Microsoft Edge` 。  若要通过认证过程，需要更改。  
1.  通过旁加载扩展 来测试扩展Microsoft Edge[在扩展中是否正常工作][ExtensionsGettingStartedExtensionSideloading]。  
1.  如果你面临任何问题，可以使用 DevTools 在 Microsoft Edge中调试扩展，或[联系我们][mailtoExtensionMicrosoft]。  
1.  按照[发布指南在][ExtensionsPublishPublishExtension]加载项网站上Microsoft Edge扩展。  
    
    > [!NOTE]
    > 如果扩展使用 与本机应用交换邮件，请确保在本机消息传递主机清单文件中设置为 `chrome.runtime.connectNative` `allowed_origins` `extension://[Microsoft-Catalog-extensionID]` 。  该设置允许应用标识你的扩展。  
    
## <a name="next-steps"></a>后续步骤  

准备好在加载项网站中发布扩展Microsoft Edge，创建开发人员[帐户并][ExtensionsPublishCreateDevAccount][发布扩展][ExtensionsPublishPublishExtension]。  

<!-- links -->  

[ExtensionApiSupport]: ./api-support.md "API 支持|Microsoft Docs"  
[ExtensionsGettingStartedExtensionSideloading]: ../getting-started/extension-sideloading.md "旁加载扩展|Microsoft Docs"  
[ExtensionsPublishCreateDevAccount]: ../publish/create-dev-account.md "注册为Microsoft Edge开发人员|Microsoft Docs"  
[ExtensionsPublishPublishExtension]: ../publish/publish-extension.md "发布扩展|Microsoft Docs"  

[ChromeDeveloperWebStorePayments]: https://developer.chrome.com/webstore/one_time_payments "一次付款|Chrome 开发人员"  

[mailtoExtensionMicrosoft]: mailto:ext_dev_support@microsoft.com "ext_dev_support@microsoft.com"  
