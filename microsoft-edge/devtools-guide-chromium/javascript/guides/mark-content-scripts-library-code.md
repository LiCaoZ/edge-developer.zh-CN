---
description: 从框架库代码启用"将内容脚本标记为设置 >库代码"。
title: 将内容脚本标记为库代码
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 1ab8e2e4a63ea169e87d0016472cededf798f074
ms.sourcegitcommit: 09975d536fb4673442f2ac6629e1787f14f110e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2021
ms.locfileid: "12034618"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="mark-content-scripts-as-library-code"></a>将内容脚本标记为库代码

使用 **"源"** 工具逐步执行 [代码时][DevToolsJavascriptStepThroughCode]，有时会对无法识别的代码暂停。  您可能暂停了已安装的一个 Microsoft Edge 扩展的代码。  若要不在扩展代码上暂停，请完成以下操作。

1.  在 DevTools 的右上角，选择齿轮图标** (设置) 。**  此时将出现**设置**页面。
1.  在 **"设置"** 下，选择"**忽略列表"。**  将显示 **"框架**库代码 **"设置**部分。
1.  打开" **将内容脚本标记为库代码"** 复选框。

    :::image type="complex" source="../../media/javascript-settings-library-code-mark-content-scripts-library-code.msft.png" alt-text="启用&quot;将内容脚本标记为库代码&quot;复选框" lightbox="../../media/javascript-settings-library-code-mark-content-scripts-library-code.msft.png":::
       启用" **将内容脚本标记为库代码"** 复选框
    :::image-end:::

## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队

[!INCLUDE [contact DevTools team note](../../includes/contact-devtools-team-note.md)]

<!-- links -->

[DevToolsJavascriptStepThroughCode]: ../index.md#step-4-step-through-the-code "步骤 4：逐步完成代码 - 开始在 DevTools Microsoft Edge中调试 JavaScript |Microsoft Docs"

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/guides/blackbox-chrome-extension-scripts)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
