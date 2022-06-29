---
title: 跟踪哪些元素有焦点
description: 打开控制台，创建一个动态表达式，然后将表达式设置为document.activeElement。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: cee42a0633ecff51fbce05a7bc20846d9f8d0665
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12630629"
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

假设你正在测试页面的键盘导航辅助功能。  通过按下`Tab``Shift`+`Tab`浏览呈现的网页时，网页中的焦点环指示器有时会消失，因为具有焦点的元素是隐藏的。  解决方案是在 DevTools **控制台**中创建实时表达式，并观看该表达式，然后右键单击它以展开 **Elements** 工具中的 DOM 树。

这就是您可以确定已使用 `Tab` 密钥导航到的页面中的哪个项的方式，即使具有焦点的元素处于隐藏状态且未显示在呈现的页面上。

`Tab`通过页面时，DOM 树不会自动更新以选择相应的 DOM 树节点。  但实时表达式输出会更改，至少当你从一种页面元素转到另一种页面元素时。  若要查看密钥所关注的确切元素 `Tab` (而不仅仅是) 的元素 _类型_ ，请右键单击实时表达式 (下的实时表达式) 的结果，转到 **Elements** 工具中 DOM 树的特定节点。


## <a name="defining-a-live-expression-to-be-able-to-determine-which-dom-node-has-focus"></a>定义实时表达式以确定哪个 DOM 节点具有焦点

使用实时表达式在 DevTools 中的**控制台**中跟踪`Tab`重点元素：

1. 在新窗口或选项卡中打开 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击网页中的任意位置，然后选择 **“检查**”。  或者按 `F12`。  DevTools 将在网页旁边打开。

1. 在 DevTools 中，打开 **控制台**。

1. 单击 **“创建实时表达** 式 (![创建实时表达式。](../media/create-live-expression-icon.msft.png)) 。

   ![创建实时表达式。](../media/accessibility-console-create-live-expression-empty.msft.png)

1. 键入以下内容： **document.activeElement**

1. 单击 **实时表达式** UI 外部以保存实时表达式。

1. 在呈现的网页中单击以将焦点放在它上，然后按下 `Tab` 或 `Shift`+`Tab` 移动呈现网页中的焦点。

   下面 `document.activeElement` 显示的值是表达式的结果。  它不会在每次您 `Tab` 在网页中切换到新的 UI 项时都明显更改;当你移动到新类型的页面元素时，它会明显更改。

   由于实时更新了该表达式 `document.activeElement` ，因此其输出结果始终表示当前重点元素，因此现在可以在 DevTools **控制台**中始终跟踪哪个元素具有焦点。  需要右键单击实时表达式输出，如下所示：

1. 在 DevTools **控制台**中，将鼠标悬停在实时表达式的结果 (实时表达式) 下方 `document.activeElement` 。

   焦点元素在视区 (中突出显示，即呈现的网页) 。

1. 在 DevTools **控制台**中，右键单击实时表达式的结果 (“实时表达式”) 下方 `document.activeElement` ，然后 **在“元素”面板中选择“显示**”。 

   在 **Elements** 工具中，DOM 树会自动展开并选择活动元素 (DOM 树节点) 。  _活动元素_是通过按下和按`Tab``Shift`+`Tab`下导航到的网页项的 DOM 树表示形式。

   <!-- Another right-click command on the Live Expression result is **Store outerHTML as global variable**, which is different than the command discussed below.  If you select that command, an expandable element such as `<input id="freedonation" class="smallinput">` is output in the **Console**. -->

1. 创建变量引用<!--why do we call it a "variable reference"? is that wording correct? --> 对于可在 **控制台**中使用的节点，右键单击实时表达式结果，然后选择 **Store outerHTML 作为全局变量**。<!--upstream doc (click "here" below) omits "outerHTML".  which is correct?-->

   在 **控制台**中，将生成新的输出，例如 `<a href="#alpacas">Alpacas</a>`。

1. 右键单击新输出，然后选择 **“复制”** > **元素**。<!--correct; do these steps make sense?-->

<!--
how is it "outer HTML"?
what are we supposed to do w/ this "global variable"?
what are we supposed to use this "global variable" for?
why is it called a "global variable"?
what's the name of the global variable?
-->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [分析边栏菜单中键盘焦点的缺失](test-analyze-no-focus-indicator.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在此](https://developer.chrome.com/docs/devtools/accessibility/focus/) 处找到，由 [Kayce Basques](https://developers.google.com/web/resources/contributors/kaycebasques) (Technical Writer、Chrome DevTools & Lighthouse) 创作。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
