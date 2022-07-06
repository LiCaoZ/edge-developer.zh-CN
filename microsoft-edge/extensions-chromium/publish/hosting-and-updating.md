---
title: 扩展托管
description: 在适用于 Microsoft Edge 的企业中托管和发布扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/10/2021
ms.openlocfilehash: b48bd6af61499e47ba5b9cc5d387f0d7698dfdcb
ms.sourcegitcommit: 108b9a0673be978d89bc99d923582f569a43f6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2022
ms.locfileid: "12635444"
---
# <a name="extension-hosting"></a>扩展托管

大多数扩展将发布到 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/insider-addons/category/EdgeExtensions)，以保护用户免受恶意扩展的影响。


<!-- ====================================================================== -->
## <a name="publish-options-for-extensions"></a>扩展的发布选项

所有扩展将作为特殊存档分发给用户 (`.zip` 具有后缀的) 文件 `.crx` 。  发布到 Microsoft Edge 加载项网站的扩展将作为 `.zip` 文件上传。  发布过程会自动将 `.zip` 文件转换为 `.crx` 文件。

以下两种方案不需要在 Microsoft Edge 加载项网站上发布扩展。

*   使用企业策略分发的扩展。
*   当 Microsoft Edge 处于开发人员模式时，在本地计算机上使用未打包的扩展目录。

在这两种情况下，Microsoft Edge 都会定期检查扩展主机是否安装了新版本的扩展，并在不进行用户干预的情况下自动更新它们。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/extensions/hosting)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
