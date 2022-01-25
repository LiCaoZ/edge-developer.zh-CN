---
title: 替代用户代理字符串
description: 打开"网络条件"工具，禁用"自动选择"，然后从列表中选择或输入自定义字符串。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/19/2021
ms.openlocfilehash: 2a68f4f23c26c001f692ee60dd710b66b5c02d95
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12320884"
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
# <a name="override-the-user-agent-string"></a>替代用户代理字符串

若要替代[DevTools 中的](https://developer.mozilla.org/docs/Glossary/User_agent)用户Microsoft Edge字符串：

1. 按 `Control` + `Shift` + `P` (Windows、Linux) 或 (`Command` + `Shift` + `P` macOS) 打开命令**菜单**。

   :::image type="content" source="../media/device-mode-console-command-menu.msft.png" alt-text="命令菜单":::
    
1. 键入 `network conditions` ，选择 **"显示网络条件**"，然后按 `Enter` 以打开 **"网络条件"** 工具。

1. 在" **用户代理"** 部分，清除" **使用浏览器默认"** 复选框。

   :::image type="content" source="../media/clear-use-browser-default-checkbox.png" alt-text="清除&quot;使用浏览器默认值&quot;复选框。":::

1. 从下拉列表中选择用户代理，或输入自定义用户代理。

1. 单击 **"用户代理客户端提示** "查看和更改这些值，如网络功能 [参考中所述](../network/reference.md)。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/override-user-agent)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
