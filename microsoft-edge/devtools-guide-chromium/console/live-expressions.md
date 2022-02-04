---
title: 使用实时表达式监视 JavaScript 中的更改
description: 使用 Live Expressions 实时观看 JavaScript 表达式值。  如果发现自己在控制台中重复键入相同的JavaScript表达式，请尝试使用动态表达式。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
---
# <a name="monitor-changes-in-javascript-using-live-expressions"></a>使用实时表达式监视 JavaScript 中的更改

<!-- very short article in other repo:
Watch JavaScript values in real-time with Live Expressions -->

**实时表达式** 是监视进行大量更改的 JavaScript 表达式的一种很好的方法。  你可以 **将特定** JavaScript 表达式固定到控制台顶部，而不是生成许多要读取和导航的控制台 **消息**。


<!-- ====================================================================== -->
## <a name="add-a-new-live-expression"></a>添加新实时表达式


1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 在 DevTools 中，打开控制台。

1. 在控制台中，单击"创建 **实时** 表达式" (!["](../media/create-live-expression-light-mode.png) 创建实时表达式"图标) **筛选器** 文本框旁边的图标。

   将打开一个文本框：

   :::image type="content" source="../media/console-live-expressions-new.msft.png" alt-text="单击&quot;新建实时表达式&quot;按钮以打开文本框以键入表达式。" lightbox="../media/console-live-expressions-new.msft.png":::

1. 在文本框中输入 `document.activeElement` JavaScript 表达式。  Live **Expression 可以是** 任何有效的 JavaScript 表达式。

1. 若要保存表达式，`Control`+`Enter`请按 (Windows、Linux) 或 (`Command`+`Enter` macOS) 。  或者，单击 **Live Expression 文本框** 外部。

   表达式现在为活动表达式，并显示 `body` 为结果：

   <!-- update the captures, they assume that you're not reading the present article or accessibility demo page, but are reading the Dev Tools Overview article: -->

   :::image type="content" source="../media/console-live-expressions-document-active-element.msft.png" alt-text="document.activeElement 的 Live 表达式将显示&quot;body&quot;作为结果。" lightbox="../media/console-live-expressions-document-active-element.msft.png":::

1. 单击网页的不同部分，或者按 `Tab` 和`Tab` `Shift`+在网页中四处移动，`document.activeElement`Live Expression 值将发生更改。

   在辅助功能测试演示网页`Tab`中，当您将焦点放在"支持"部分中的****"其他"文本框上**** 时，Live Expression 值将读取 `input#freedonation.smallinput`。

   <!-- revise the step & the capture after it: -->

1. 在同一窗口中，转到网页"[DevTools](../index.md) 概述"，然后单击左上角的"文档"**** 按钮。

   Live Expression 值将更改为 `button.nav-bar-button.focus-visible`：

   :::image type="content" source="../media/console-live-expressions-document-active-element-nav-button.msft.png" alt-text="若要更改 Live Expression 的值，请与网页上的不同元素交互。" lightbox="../media/console-live-expressions-document-active-element-nav-button.msft.png":::

1. 若要再次更改该值，请打开并单击网页上**** 的"搜索"文本框。

   Live Expression 值将更改为 `input#site-search-input.autocomplete-input.input.is-small.focus-visible`：

   :::image type="content" source="../media/console-live-expressions-document-active-element-search.msft.png" alt-text="导航到网页中的不同元素以更新 Live Expression。" lightbox="../media/console-live-expressions-document-active-element-search.msft.png":::


<!-- ====================================================================== -->
## <a name="remove-live-expressions"></a>删除 Live Expressions

只要 **使 Live Expression** 保持活动状态，它就可用。

*  若要删除 Live **Expression，** 请单击它旁边的 `x` 。

   :::image type="content" source="../media/console-live-expressions-remove.msft.png" alt-text="若要删除 Live Expressions，请单击其旁边的&quot;x&quot;。" lightbox="../media/console-live-expressions-remove.msft.png":::


<!-- ====================================================================== -->
## <a name="replace-console-logging-with-live-expressions"></a>将控制台日志记录替换为 Live Expressions

你可以创建尽可能多的 Live Expression，并跨浏览器会话和窗口保留每个 Live Expression。  实时表达式是一种减少调试工作流中的噪音的方法。


### <a name="using-console-logging-to-display-mouse-coordinates"></a>使用控制台日志记录显示鼠标坐标

监视当前网页中的鼠标移动：

1. 打开演示网页 [记录新窗口或](https://microsoftedge.github.io/Demos/devtools-console/mousemove.html) 选项卡中的鼠标移动演示。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  在演示网页旁的 DevTools 中打开控制台。

1. 将鼠标移过呈现的演示网页。

   许多日志消息输出在控制台 **中显示**：

   :::image type="content" source="../media/console-live-expression-mouse-logging.msft.png" alt-text="控制台显示大量有关鼠标位置的消息。" lightbox="../media/console-live-expression-mouse-logging.msft.png":::

大量信息会减慢调试过程，并且难以查看您尝试监视的更改。  由于 **控制台** 在移动鼠标时显示的消息更多，因此您希望看到的值将滚动到屏幕上。


### <a name="using-live-expressions-to-display-mouse-coordinates"></a>使用 Live Expressions 显示鼠标坐标

使用 Live Expressions 监视当前网页中的鼠标移动，而无需依赖详细的日志消息。

若要使用 Live Expressions 以避免过多的控制台日志消息：

1. 打开演示网页 [，而无需记录](https://microsoftedge.github.io/Demos/devtools-console/mousemove-no-log.html) 新窗口或选项卡中的演示的鼠标移动。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  在演示网页旁的 DevTools 中打开控制台。

1. 四处移动鼠标。  不输出日志消息。

   输入两个 Live Expressions：表达式 `x`和 表达式 `y`，如下所示：

1. 在控制台中，单击"创建 **实时** 表达式" (!["](../media/create-live-expression-light-mode.png) 创建实时表达式"图标) **筛选器** 文本框旁边的图标。

1. 在文本框中输入 `x` JavaScript 表达式，然后单击 **Live Expression** 文本框外部。  对 重复。`y`  如果需要，请参阅 [上面的添加新实时](#add-a-new-live-expression)表达式。

1. 四处移动鼠标。

   现在，在 DevTools 控制台中，Live Expression 值在 Live Expression `x` 下方更新，显示鼠标 `y` 的 和 坐标：

   :::image type="content" source="../media/console-live-expressions-x-and-y.msft.png" alt-text="将鼠标的&quot;x&quot;和&quot;y&quot;坐标显示为实时表达式。" lightbox="../media/console-live-expressions-x-and-y.msft.png":::

使用 **Live Expressions 时**，始终在屏幕的同一部分获取信息，并保留控制台日志，以获得**** 不会更改太多的值。

**Live Expressions** 以独占方式在计算机上运行，无需在代码中更改任何内容来显示表达式及其结果。  **实时** 表达式是确保您仅显示要调试的信息的一种很好的方法。  Live Expressions 还可以帮助您限制用户计算机上的噪音。
