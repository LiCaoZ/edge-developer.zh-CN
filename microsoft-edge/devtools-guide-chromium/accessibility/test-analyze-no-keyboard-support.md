---
title: 分析窗体上的键盘支持
description: 分析在将 div 元素与"检查工具"和"事件侦听器"选项卡一同使用的表单上缺少键盘支持。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: f10705589b1c906ae760b4c10a0c451af313b694
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430575"
---
# <a name="analyze-keyboard-support-on-forms"></a>分析窗体上的键盘支持

本文使用 **"检查****工具"和**"事件侦听器"选项卡来分析在包含使用该元素的按钮的演示页面上缺少键盘`div`支持。

在 **"百** 万"窗体上，"金额"按钮和 **"** 开始"按钮不能与键盘一起使用。  调试资金表单需要了解为什么缺少焦点样式未标记为问题自动测试工具（如 **问题** 工具）的问题。  本示例使用元素实现 `div` 按钮，这些工具无法将元素识别为窗体上的控件。

若要使用"检查工具"和"事件侦听器"选项卡分析演示页上缺少键盘支持：

<!-- 1. Inspect tool: Accessibility section: keyboard-focusable row -->

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 单击 **"检查** ![](../media/inspect-tool-icon-light-theme.png) (检查"图标。) 工具左上角的"检查"按钮，使按钮突出显示 (蓝色) 。

1. 将鼠标悬停在 **50** 个 **、100** 个和 **200 个"支持** "按钮上。  The Inspect tool appears on the webpage， as an overlay.  " **检查"覆盖** 层的可键盘聚焦行显示，没有一个"支持"金额按钮可通过键盘访问，如带对角线的灰色圆圈所示。  按钮没有名称，`generic``div`并且具有 其角色，因为它们是元素，这意味着辅助技术无法访问按钮。

   :::image type="content" source="../media/a11y-testing-donation-button-info.msft.png" alt-text="检查窗体的按钮时发现它们不能通过键盘访问。" lightbox="../media/a11y-testing-donation-button-info.msft.png":::

1. 当 **"检查**"工具处于活动状态时，在网页上，选择"**开发工具"** 按钮上方的"其他输入 **"文本框。**  将 **打开"** 元素"工具，显示网页的 DOM 树。  `<input id="freedonation" class="smallinput">`元素已选中。

   ```html
   <div class="donationrow">
       <div class="donationbutton">50</div>
       <div class="donationbutton">100</div>
       <div class="donationbutton">200</div>
   </div>
   <div class="donationrow">
       <label for="freedonation">Other</label>
       <input id="freedonation" class="smallinput">
   </div>
   <div class="donationrow">
       <div class="submitbutton">Donate</div>
   </div>
   ```

   在"其他`label`"文本框上使用 和 **** `input` 元素是有效的，这意味着"其他"标签与输入**** 文本框正确链接。  文本框 `input` 还可供键盘访问。  表单的标记的其余部分是 `div` 元素，它们易于设置样式，但没有任何语义含义。

   <!-- 2. Elements tool: Event Listeners tab -->

   表单的功能是使用 JavaScript 创建的，您可以通过检查"事件侦听器"选项卡来测试这一点****，如下所示。

1. 在 DOM `<input id="freedonation" class="smallinput">` 树中仍选择 元素后，选择"样式****"选项卡右边的"事件侦听器"选项卡****，然后展开事件`click`侦听器。

   :::image type="content" source="../media/a11y-testing-event-handlers-on-button.msft.png" alt-text="显示使表单正常工作的 JavaScript 的&quot;事件侦听器&quot;工具。" lightbox="../media/a11y-testing-event-handlers-on-button.msft.png":::

1. 选择链接 `buttons.js:18` 。  将 **打开"** 源"工具，显示应用的 JavaScript。

   :::image type="content" source="../media/a11y-testing-form-handling-javascript.msft.png" alt-text="负责提供表单功能的 JavaScript，如&quot;源&quot;工具中所示。" lightbox="../media/a11y-testing-form-handling-javascript.msft.png":::

   下面是已应用的 JavaScript 的代码列表：

    ```javascript
    donations.addEventListener('click', e => {
      let t = e.target;
      if (t.classList.contains('donationbutton')) {
        if (currentbutton) { currentbutton.classList.remove('current'); }
        t.classList.add('current');
        currentbutton = t;
        e.preventDefault();
      }
      if (t.classList.contains('submitbutton')) {
        alert('Thanks for your donation!')
      }
    })
    ```
    
   `click`使用事件读取按钮是一个不错的做法`click`，因为事件在鼠标指针和键盘交互上触发。  `div`但是，由于元素不可通过键盘访问，并且此 **"**`div`开发工具"按钮作为元素 (`<div class="submitbutton">Donate</div>`) 实现，因此除非使用鼠标或事件的另一个源（例如某些键盘上提供的特殊按钮）否则，此 JavaScript `click` 功能永远不会运行。

这是添加 JavaScript 以创建元素在本机提供的功能的 `button` 经典示例。  通过元素模拟按钮的功能 `div` 最终产生不可访问的体验。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
