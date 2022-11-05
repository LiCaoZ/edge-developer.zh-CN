---
title: 扩展托管
description: 在企业中托管和发布 Microsoft Edge 扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/04/2022
ms.openlocfilehash: 288974a1a3f037437a6ade61396c629ed6891aa3
ms.sourcegitcommit: dd668d16163d750f0dd23fd3379dfac9b2382b99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2022
ms.locfileid: "12854799"
---
# <a name="extension-hosting"></a>扩展托管

大多数扩展都发布到 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/insider-addons/category/EdgeExtensions)，以保护用户免受恶意扩展的侵害。


<!-- ====================================================================== -->
## <a name="publish-options-for-extensions"></a>扩展的发布选项

所有扩展都作为特殊存档 (`.zip` 带有 `.crx` 后缀的) 文件分发给用户。  发布到 Microsoft Edge 加载项网站的扩展将作为 `.zip` 文件上传。  发布过程会自动将 `.zip` 文件转换为 `.crx` 文件。

以下两种方案不需要在 Microsoft Edge 加载项网站上发布扩展。

*   使用企业策略分发的扩展。
*   当 Microsoft Edge 处于开发人员模式时，在本地计算机上使用解压缩的扩展目录。

在这两种情况下，Microsoft Edge 都会定期检查扩展主机是否有新版本的已安装扩展，并在用户不干预的情况下自动更新它们。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在此处](https://developer.chrome.com/extensions/hosting)找到。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
