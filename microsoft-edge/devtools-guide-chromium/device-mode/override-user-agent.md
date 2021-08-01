---
description: 打开"网络条件"工具，禁用"自动选择"，然后从列表中选择或输入自定义字符串。
title: 替代 DevTools 中的Microsoft Edge字符串
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/19/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 06ec6905b11d01ec0e7c03fb8c4c9c843923a881
ms.sourcegitcommit: 57f52b3edb34b8eb5389b746ff0970f7fd3b9a82
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2021
ms.locfileid: "11710702"
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
# <a name="override-the-user-agent-string-from-microsoft-edge-devtools"></a>替代 DevTools 中的Microsoft Edge字符串  

若要覆盖[DevTools 中的][MDNUserAgent]用户Microsoft Edge字符串：  

1. 选择 `Control`+`Shift`+`P` \(Windows、Linux\) 或 `Command`+`Shift`+`P` \(macOS\) 打开**命令菜单**。  
    
    :::image type="complex" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单" lightbox="../media/device-mode-console-command-menu.msft.png":::
       **命令菜单**  
    :::image-end:::  
    
1. 键入 `network conditions` ，选择 **"显示网络条件**"，然后选择 `Enter` 以打开 **"网络条件"** 工具。  
1. 在" **用户代理"** 部分，清除" **使用浏览器默认"** 复选框。  
    
    :::image type="complex" source="../media/device-mode-console-network-conditions-user-agent-select-automatically-deselected.msft.png" alt-text="关闭"自动选择"" lightbox="../media/device-mode-console-network-conditions-user-agent-select-automatically-deselected.msft.png":::
       清除 **"使用浏览器默认复选框** " :::image-end:::  
    
1. 从下拉列表中选择用户代理或输入自定义用户代理。
1. 选择 **"用户代理客户端提示** "查看和更改这些值，如网络 [分析参考中所述](../network/reference.md)。
    
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[MDNUserAgent]: https://developer.mozilla.org/docs/Glossary/User_agent "用户代理|MDN"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/override-user-agent)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques  
