---
title: DevTools 的示例代码
description: Microsoft Edge DevTools 的示例代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/03/2022
ms.openlocfilehash: 7683f261c9ec21ce0a098c7c2e2a3aa06ae081e3
ms.sourcegitcommit: 5438bc89031609ad4045a96476ae29718561bac0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2022
ms.locfileid: "12612257"
---
# <a name="sample-code-for-devtools"></a>DevTools 的示例代码

DevTools 文档使用的示例代码主要在 GitHub 处的 [MicrosoftEdge/Demos](https://github.com/MicrosoftEdge/Demos) 存储库中。

<!-- A few demos are at other locations, such as Glitch. -->


<!-- ====================================================================== -->
## <a name="demo-webpage-with-accessibility-issues"></a>具有辅助功能问题的演示网页

此演示网页可用于探索各种 DevTools 功能。

1. 在新窗口或选项卡中打开 [具有辅助功能问题的演示网页](https://MicrosoftEdge.github.io/Demos/devtools-a11y-testing/) 。

1. 右键单击呈现网页中的任意位置，然后选择 **“检查**”。  DevTools 将在演示网页旁边打开。

   <!-- Or, press `F12`, `Ctrl`+`Shift`+`I` (on Windows/Linux), or `Command`+`Option`+`I` (on macOS). -->

![“具有辅助功能问题的演示网页”。](../media/demo-page-with-accessibility-issues.png)


### <a name="articles"></a>文章

这些文章逐步讲解如何使用此演示网页：

* [使用 DevTools 的辅助功能测试概述](../accessibility/accessibility-testing-in-devtools.md) - 长文章，其中包含演示如何使用各种 DevTools 功能执行辅助功能测试的部分，方法是使用“具有辅助功能问题的演示网页”。

* [使用“检查”工具通过将鼠标悬停在网页上来检测辅助功能问题](../accessibility/test-inspect-tool.md) - 派生自上述文章部分的多个简短文章之一。

* [辅助功能测试功能](../accessibility/reference.md) - DevTools 的辅助功能测试功能列表，其中包含一些文章的链接，这些文章使用“演示网页和辅助功能问题”。


### <a name="source-code-repo"></a>源代码存储库

这是存储此演示网页文件的源代码存储库及其目录：

* [MicrosoftEdge/Demos > devtools-a11y-testing](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-a11y-testing) - 包含文件，包括：

   * `index.html` - 演示网页，包括将数据发送到 JavaScript 文件的 `buttons.js` 页面部分和输入表单。  若要查看呈现的网页，请使用上面的演示网页链接。

   * `buttons.js` - 包含演示网页使用的 JavaScript 代码。

   * `styles.css`、 `light-theme.css`和 `dark-theme.css` - 控制演示网页演示的演示的 CSS 文件。

   * 演示网页中使用的图像文件。


<!-- ====================================================================== -->
## <a name="demo-webpage-debugging-javascript-with-devtools"></a>演示网页：使用 DevTools 调试 JavaScript

此演示网页可用于浏览 **“源** ”工具，尤其是 JavaScript 调试器。

1. 在新窗口或选项卡[中打开演示网页开始使用 DevTools 调试 JavaScript](https://MicrosoftEdge.github.io/Demos/devtools-js-get-started/)。

1. 右键单击呈现网页中的任意位置，然后选择 **“检查**”。  DevTools 将在演示网页旁边打开。

   <!-- Or, press `F12`, `Ctrl`+`Shift`+`I` (on Windows/Linux), or `Command`+`Option`+`I` (on macOS). -->

![“开始使用 DevTools 调试 JavaScript”演示网页。](../media/using-debug-js-demo-page.png)


### <a name="articles"></a>文章

这些文章或文章部分逐步讲解如何使用此演示网页：

* 在 _“源”工具概述_中[使用调试器的基本方法](../sources/index.md#the-basic-approach-to-using-a-debugger)。  本文部分简要介绍了在 **“源** ”工具中使用 JavaScript 调试器查找演示网页中的 bug 的步骤。  若要修复 bug，请在添加输入字符串之前将它们转换为数字。

* [开始调试 JavaScript](../javascript/index.md) - 使用演示网页和调试器、演示调试器的各种功能以及设置不同类型的断点的更深入演练。


### <a name="source-code-repo"></a>源代码存储库

这是存储此演示网页文件的源代码存储库及其目录：

* [MicrosoftEdge/Demos > devtools-js-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-js-get-started) - 包含文件：

   *  `README.md` - 包含指向演示网页和有关使用演示网页的深入教程文章的链接。

   *  `index.html` - 具有将数据发送到 JavaScript 文件并显示 JavaScript 结果的输入窗体的网页。

   *  `get-started.js` - 演示网页中窗体使用的 JavaScript 文件。


<!-- ====================================================================== -->
## <a name="url-patterns-for-rendered-demo-webpages-and-source-code"></a>呈现的演示网页和源代码的 URL 模式

若要在呈现的演示网页的 URL 与源代码的 URL 之间进行转换，GitHub，模式如下所示。


### <a name="pattern"></a>模式

*  呈现的演示网页的 URL： `https://[org].github.io/[repo]/[path]`

*  网页源代码的 URL： `https://github.com/[org]/[repo]/tree/main/[path]`

不区分大小写。


### <a name="example"></a>示例

*  呈现的演示网页的 URL： `https://MicrosoftEdge.github.io/Demos/devtools-a11y-testing/`

*  网页源代码的 URL： `https://github.com/MicrosoftEdge/Demos/tree/main/devtools-a11y-testing/`

*  Org = `MicrosoftEdge`
*  存储库 = `Demos`
*  路径 = `/devtools-a11y-testing/`
