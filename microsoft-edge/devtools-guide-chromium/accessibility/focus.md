---
title: 跟踪哪些元素有焦点
description: 打开控制台，创建一个动态表达式，然后将表达式设置为document.activeElement。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: ecfc49e9d4cd816098e895d21312f16b7f230172
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318203"
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

假设正在测试页面的键盘导航辅助功能。  使用`Tab`键浏览页面时，聚焦环有时会消失，因为具有焦点的元素被隐藏。

若要跟踪 DevTools 中聚焦的元素：

1.  打开“**控制台**”。
1.  Choose **Create live expression (** Create live expression ![ ](../media/create-live-expression-icon.msft.png)) .

    :::image type="complex" source="../media/accessibility-console-create-live-expression-empty.msft.png" alt-text="创建动态表达式" lightbox="../media/accessibility-console-create-live-expression-empty.msft.png":::
       创建动态表达式
    :::image-end:::

1.  键入 `document.activeElement`。
1.  若要保存表达式，请选择活动表达式之外。

`document.activeElement` 下面显示的值是表达式的结果。

由于该表达式始终代表着焦点的元素，因此现在可以始终跟踪哪个元素具有焦点。

*   将鼠标悬停在结果上，以在视区中突出显示焦点元素。
*   将鼠标悬停在结果上，右键单击 () 上下文菜单，然后选择"元素"面板中的"**** 展示"，在"元素"工具上的"DOM 树"中**显示元素。**
*   将鼠标悬停在结果上，右键单击" (") "，然后选择"存储"作为全局变量****，以创建对可以在控制台中使用的节点的变量**引用**。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [分析边栏菜单中键盘焦点的缺失](test-analyze-no-focus-indicator.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference)，由技术编写 (、Chrome DevTools & Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors/kaycebasques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
