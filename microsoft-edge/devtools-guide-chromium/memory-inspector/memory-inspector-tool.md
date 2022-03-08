---
title: 使用内存检查器工具检查 JavaScript ArrayBuffer
description: DevTools 中Microsoft Edge检查器工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 02/15/2022
ms.openlocfilehash: f0e0199a770284313dce243426e2ff0a00682d9d
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433732"
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
# <a name="inspect-a-javascript-arraybuffer-with-the-memory-inspector-tool"></a>使用内存检查器工具检查 JavaScript ArrayBuffer


<!-- this page's content so far is the entry from
https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/whats-new/2021/04/devtools#new-memory-inspector-tool
-->



使用新的 **内存检查器** 工具检查 JavaScript 和 Wasm 内存中的 `ArrayBuffer`。

1. 打开演示网页 在新窗口或选项卡 (JS 中的 JS) 内存检查 [ArrayBuffers ](https://memory-inspector.glitch.me/demo-js.html) 。

   下面的步骤列表派生自该网页上的说明。

1. 若要打开 DevTools，请右键单击该网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。  将打开 DevTools。

1. 在 DevTools 中，在主工具栏上，选择"源 **"** 选项卡。 如果该选项卡不可见，请单击"更多选项卡" (**** 更多选项卡"图标](../media/more-tabs-icon-light-theme.png)。****) 按钮![，或单击"更多工具 (更多工具"图标。) 按钮。](../media/more-tools-icon-light-theme.png) ![

1. 在左侧 **的"** 页面"选项卡中，选择文件 `demo-js.js`。 <!-- `memory-write-wasm`-->

1. 在循环正文的第 18 行设置断点。

1. 刷新网页。

1. 在调试器中的"范围 **"部分** ，展开" **本地"**。

   ![内存检查器工具。](../media/memory-inspector-tool.png)

1. 展开缓冲区 **以显示** 模块 **作用域**。

1. 在缓冲区名称**** 的![右侧****，单击"内存检查器中的展示"面板 ("内存检查器面板"图标](../media/reveal-in-memory-inspector-panel-icon.png)。) 图标。  或者，右键单击缓冲区，然后选择"内存 **检查器"面板中的"展示"**。

1. " **内存检查器** "工具将在"箱"中打开。  在 **内存检查器** 工具中，检查 **缓冲区**。

1. 若要检查 **Uint8Array b2**， <!-- expand that node to see the buffer, and then select the **Memory** icon (or-->右键单击 **b2**，然后选择"内存 **检查器"面板中的"展示"**。

1. 若要检查 **Uint8Array b1**， <!-- expand that node to see the buffer, and then select the **Memory** icon (or-->右键单击 **b1**，然后选择"内存 **检查器"面板中的"展示"**。  该焦点重新放在第 **一** 个缓冲区的"内存"选项卡上。

1. 在调试器中，逐步查看内存检查器工具 **中的缓冲区更新** 。




<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处，](https://developer.chrome.com/blog/memory-inspector/) 由 [Kim-Anh Tran](https://developer.chrome.com/authors/kimanh/) (Chrome DevTools) 。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
