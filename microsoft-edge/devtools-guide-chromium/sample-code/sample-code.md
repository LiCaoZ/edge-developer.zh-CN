---
title: DevTools 的示例代码
description: 开发人员工具Microsoft Edge代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/01/2022
ms.openlocfilehash: d816bc35cd683783ddc97d1496b7ff6067656a24
ms.sourcegitcommit: c63325d520191ce4b4e707fb680c84afce4eab54
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2022
ms.locfileid: "12338857"
---
# <a name="sample-code-for-devtools"></a>DevTools 的示例代码

DevTools 文档使用大多数示例代码都存储在以下GitHub中。


<!-- ====================================================================== -->
## <a name="github-repos-for-samples"></a>GitHub示例的 repos

[MicrosoftEdge/Demos](https://github.com/MicrosoftEdge/Demos) 存储库包含文档使用大部分演示页面或示例代码。

[MicrosoftEdge/DevToolsSamples](https://github.com/MicrosoftEdge/DevToolsSamples) 存储库包含文档使用的几个演示，包括**用于 3D** 视图、**检查**工具、控制台和辅助功能测试。 ****

下面的演示页面存储在这些资源中，可用于探索元素和源**等****工具**。


<!-- ====================================================================== -->
## <a name="demo-webpage-with-accessibility-issues"></a>演示包含辅助功能问题的网页

此演示网页可用于探索各种 DevTools 功能，如**元素和****源工具**。

* 打开新 [窗口或选项卡](https://microsoftedge.github.io/DevToolsSamples/a11y-testing/page-with-errors.html) 中具有辅助功能问题的演示页面。 右键单击呈现的网页中的任意项目，然后选择"检查 **"**。  或者，按 `F12`。  将在演示网页旁边打开 DevTools。

!["包含辅助功能问题的演示页面"。](../media/demo-page-with-accessibility-issues.png)

### <a name="articles"></a>文章

这些文章将介绍使用此演示页面：

* [Overview of accessibility testing using DevTools](../accessibility/accessibility-testing-in-devtools.md) - Long article with sections that demonstrate using various DevTools features to do accessibility testing， by using the "Demo page with accessibility issues".

* [使用 Inspect 工具，通过将](../accessibility/test-inspect-tool.md) 鼠标悬停在网页上方来检测辅助功能问题 - 从以上文章中的部分派生的一些短文章之一。

* [辅助功能测试功能](../accessibility/reference.md) - DevTools 的辅助功能测试功能列表，包含指向使用"包含辅助功能问题的演示页面"的几个文章的链接。

### <a name="source-code-repo"></a>源代码存储库

这是存储此演示网页文件的源代码存储库及其目录：

* [MicrosoftEdge/DevToolsSamples > a11y 测试](https://github.com/MicrosoftEdge/DevToolsSamples/tree/master/docs/a11y-testing) - 包含包括：

   * `page-with-errors.html` - 演示网页，包括向 JavaScript 文件发送数据的页面部分和输入 `buttons.js` 表单。  若要查看呈现的网页，请使用上面的演示网页链接。

   * `buttons.js` - 包含演示网页使用的 JavaScript 代码。

   * `styles.css`、 `light-theme.css`和 `dark-theme.css` - 控制演示网页演示文稿的 CSS 文件。

   * 演示网页中使用的图像文件。


<!-- ====================================================================== -->
## <a name="demo-webpage-debugging-javascript-with-devtools"></a>演示网页：使用 DevTools 调试 JavaScript

此演示网页可用于探索 **源** 工具，尤其是 JavaScript 调试程序。

* 打开演示页面 [开始使用新窗口或选项卡中的 DevTools 调试 JavaScript](https://microsoftedge.github.io/Demos/devtools-js-get-started/) 。 右键单击呈现的网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在演示网页旁边打开 DevTools。

!["使用 DevTools 调试 JavaScript 入门"演示页面。](../media/using-debug-js-demo-page.png)

### <a name="articles"></a>文章

以下文章或文章部分将介绍使用此演示页面：

* [源工具概述中的使用](../sources/index.md#the-basic-approach-to-using-a-debugger)_调试器的基本方法_。  本文部分简要介绍了使用源工具中的 JavaScript 调试器在演示页面中查找 Bug 的步骤。****  若要修复 Bug，在添加输入字符串之前将其转换为数字。

* [JavaScript](../javascript/index.md) 调试入门 - 将演示页面与调试器一同使用、演示调试程序的各种功能以及设置不同类型的断点的更深入演练。

### <a name="source-code-repo"></a>源代码存储库

这是存储此演示网页文件的源代码存储库及其目录：

* [microsoftEdge/Demos > devtools-js-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-js-get-started) - 包含以下文件：

   *  `README.md` - 包含指向呈现的演示网页的链接，以及有关使用演示网页的深入教程文章。

   *  `index.html` - 包含输入表单的网页，该输入表单将数据发送到 JavaScript 文件，并显示 JavaScript 的结果。

   *  `get-started.js` - 演示网页中的表单使用的 JavaScript 文件。
