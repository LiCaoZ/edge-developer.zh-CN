---
title: 跟踪哪些元素有焦点
description: 打开控制台，创建一个动态表达式，然后将表达式设置为document.activeElement。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 0be319af338e66437e56b3350db73223a43bb6f5
ms.sourcegitcommit: 9caa4aac0a339a76e7f1e0f0f5d6d85a2492ea8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "12325604"
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
# <a name="track-which-element-has-focus"></a>跟踪哪些元素有焦点

假设您正在测试页面的键盘导航辅助功能。  使用`Tab`键浏览页面时，聚焦环有时会消失，因为具有焦点的元素被隐藏。

若要跟踪 DevTools 中聚焦的元素：

1.  打开“**控制台**”。

1.  单击 **"创建实时表达式 (** ![ 创建实时表达式 ](../media/create-live-expression-icon.msft.png) "。) 。

    :::image type="content" source="../media/accessibility-console-create-live-expression-empty.msft.png" alt-text="创建 Live Expression。" lightbox="../media/accessibility-console-create-live-expression-empty.msft.png":::

1.  键入 `document.activeElement`。

1.  单击 Live **Expression** UI 外部以保存。

`document.activeElement` 下面显示的值是表达式的结果。

由于该表达式始终代表着焦点的元素，因此现在可以始终跟踪哪个元素具有焦点。

* 将鼠标悬停在结果上，以在视区中突出显示焦点元素。

* 右键单击结果，然后选择"元素 **"面板中的**"展示"，以显示"元素"面板上的**DOM 树****中的**元素。

* 右键单击结果并选择"存储 **"作为** 全局变量，以创建对可在控制台中使用的节点的变量 **引用**。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [分析边栏菜单中键盘焦点的缺失](test-analyze-no-focus-indicator.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/accessibility/focus/)，由技术编写 (、Chrome DevTools & Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors/kaycebasques)

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
