---
title: 源工具概述
description: 使用"源"工具查看、修改和调试服务器返回的 JavaScript，并检查包含当前网页的资源。  若要将"源"工具用作开发环境，请向 Workspace 中添加源文件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/20/2021
ms.openlocfilehash: 1aa0dc2d608d526f2bbeb83ef034125394279edc
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432150"
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
# <a name="sources-tool-overview"></a>源工具概述

使用 **"** 源"工具查看、修改和调试前端 JavaScript 代码，并检查包含当前网页的资源。  " **源** "工具具有三个窗格：

| 窗格 | 操作 |
|---|---|
| **导航器** 窗格 | 在从服务器返回的资源之间导航以构建当前网页。  选择文件、图像和其他资源，并查看其路径。  （可选）设置本地 Workspace 以将更改直接保存到源文件。 |
| **编辑器** 窗格 | 查看从服务器返回的 JavaScript、HTML、CSS 和其他文件。  对 JavaScript 或 CSS 进行实验性编辑。  在刷新页面之前，所做的更改将一直保留;如果使用 Workspaces 保存到本地文件，则页面刷新后将保留所做的更改。 使用 Workspaces 或 Overrides 时，也可以编辑 HTML 文件。 |
| **调试器** 窗格 | 使用 JavaScript 调试器设置断点、暂停运行 JavaScript，并逐步执行代码，包括你进行的任何编辑，同时观察你指定的任何 JavaScript 表达式。  观察并手动更改当前代码行范围内变量的值。 |

下图显示了 **导航器** 窗格，其中突出显示了 DevTools 左上角的红色框，右上角突出显示了 **编辑器** 窗格，底部突出显示了 **调试器** 窗格。  最左侧是浏览器窗口的主要部分，显示呈现的网页灰显，因为调试程序暂停在断点上：

:::image type="content" source="../media/sources-panes-narrow-layout.msft.png" alt-text="&quot;源&quot;工具的窗格，布局较窄" lightbox="../media/sources-panes-narrow-layout.msft.png":::

当 DevTools 宽时， **调试** 器窗格放置在右侧，并包括 **作用域** 和 **监视**：

:::image type="content" source="../media/sources-panes-wide-layout.msft.png" alt-text="导航、查看、编辑和调试服务器返回的 JavaScript" lightbox="../media/sources-panes-wide-layout.msft.png":::

若要最大化"源"工具的大小，请取消停靠"DevTools"到单独的窗口，并可以选择将"DevTools"窗口移动到单独的监视器。  请参阅[更改 DevTools 放置位置（取消停靠，停靠到底部，停靠到左侧）](../customize/placement.md)。

若要加载上面显示的调试演示网页，请参阅下面的使用 [调试器的基本](#the-basic-approach-to-using-a-debugger)方法。


<!-- ====================================================================== -->
## <a name="using-the-navigator-pane-to-select-files"></a>使用导航器窗格选择文件

使用 **左侧 (** 导航器窗格) 导航从服务器返回的资源之间导航以构建当前网页。  选择文件、图像和其他资源，并查看其路径。

:::image type="content" source="../media/navigator-pane.msft.png" alt-text="导航器窗格。" lightbox="../media/navigator-pane.msft.png":::

若要访问导航器窗格的任何隐藏选项卡，请选择"更多 ![选项卡"。](../media/more-tabs-icon.msft.png)  (**更多选项卡) ** 。

以下子部分涵盖导航器窗格：
* [使用"页面"选项卡浏览构建当前网页的资源](#using-the-page-tab-to-explore-resources-that-construct-the-current-webpage)
* [使用"文件系统"选项卡定义本地 Workspace](#using-the-filesystem-tab-to-define-a-local-workspace)
* [使用"覆盖"选项卡覆盖包含本地文件的服务器文件](#using-the-overrides-tab-to-override-server-files-with-local-files)
* [将"内容脚本"选项卡用于Microsoft Edge扩展](#using-the-content-scripts-tab-for-microsoft-edge-extensions)
* [使用"代码段"选项卡在任何页面上运行 JavaScript 代码段](#using-the-snippets-tab-to-run-javascript-code-snippets-on-any-webpage)
* [使用命令菜单打开文件](#using-the-command-menu-to-open-files)


### <a name="using-the-page-tab-to-explore-resources-that-construct-the-current-webpage"></a>使用"页面"选项卡浏览构建当前网页的资源

使用**导航器**窗格的"**页**"选项卡浏览从服务器返回的文件系统以构造当前网页。  选择要查看、编辑和调试的 JavaScript 文件。  " **页面** "选项卡列出了页面已加载的所有资源。

:::image type="content" source="../media/sources-page-tab.msft.png" alt-text="&quot;源&quot;工具的&quot;导航器&quot;窗格中的&quot;页面&quot;选项卡。" lightbox="../media/sources-page-tab.msft.png":::

若要在"编辑器"窗格中 **显示** 文件，请在"页面"选项卡 **中选择** 一个文件。 对于图像，将显示图像的预览。

若要显示资源的 URL 或路径，请将鼠标悬停在资源上。

若要将文件加载到浏览器的新选项卡中，或显示其他操作，请右键单击文件名。


#### <a name="icons-in-the-page-tab"></a>"页面"选项卡中的图标

" **页面** "选项卡使用下列图标：
*  窗口 **图标** 与标签一起表示主 `top` 文档框架，即 [HTML 框架](https://w3.org/TR/html401/present/frames.html)。
*  云 **图标** 表示原 [点](https://html.spec.whatwg.org/multipage/origin.html#origin)。
*  文件夹 **图标** 表示目录。
*  页面 **图标** 表示资源。


#### <a name="group-files-by-folder-or-as-a-flat-list"></a>按文件夹或文件夹对文件进行分组简单列表

" **页面** "选项卡显示按服务器和目录分组的文件或资源，或作为简单列表。

若要更改资源的分组时间，请进行配置：

1. 在导航器窗格（左侧）选项卡旁边，选择 **...** （**更多选项**）"按钮。  将显示菜单。
1. 选择或清除" **按文件夹分组"** 选项。


### <a name="using-the-filesystem-tab-to-define-a-local-workspace"></a>使用"文件系统"选项卡定义本地 Workspace

使用**导航器**窗格的"**文件系统**"选项卡将文件添加到工作区，以便在 DevTools 中所做的更改保存到本地文件系统。

Workspace 中的文件在整个 DevTools 中由文件名旁边的绿色点指示。

:::image type="content" source="../media/sources-filesystem-tab.msft.png" alt-text="工作区的&quot;文件系统&quot;选项卡" lightbox="../media/sources-filesystem-tab.msft.png":::

默认情况下，在 **源** 工具中编辑文件时，刷新网页时将放弃更改。  **Sources**工具使用 Web 服务器返回的前端资源的副本。  修改服务器返回的这些前端文件时，更改不会保留，因为您未更改源文件。  您还需要在实际源代码中应用您的编辑，然后重新部署到服务器。

相比之下，使用 Workspace 时，刷新网页时，对前端代码所做的更改将保留。  对于 Workspace，当您编辑服务器返回的前端代码时，"源"工具还会将编辑应用于本地源代码。  然后，对于其他用户查看更改，只需将已更改的源文件重新部署到服务器。

如果服务器返回的 JavaScript 代码与本地 JavaScript 源代码相同，工作区可正常工作。  当工作流涉及源代码转换（如缩小或 [TypeScript](https://www.typescriptlang.org) 编译）时，工作区不能正常工作。

有关详细信息，请参阅使用 [Workspaces 和 Filesystem 选项卡 (编辑) ](../workspaces/index.md)。


### <a name="using-the-overrides-tab-to-override-server-files-with-local-files"></a>使用"覆盖"选项卡覆盖包含本地文件的服务器文件

使用**导航器**窗格的"**替代"** 选项卡，使用本地文件夹中的文件替代页面资产（如图像）。

此选项卡中的项目会覆盖服务器发送到浏览器的内容，即使服务器已发送资产。

:::image type="content" source="../media/overrides-tab.msft.png" alt-text="导航器窗格的&quot;替代&quot;选项卡。" lightbox="../media/overrides-tab.msft.png":::

替代 **功能** 类似于工作区。  当您要尝试对网页所做的更改，并且需要在刷新网页后保留更改，但您不关心将更改映射到网页的源代码时，请使用 Overrides。

覆盖服务器返回的文件的文件在整个 DevTools 中由文件名旁边的紫色点指示。


#### <a name="see-also"></a>另请参阅

*  [使用本地副本替代网页资源（“替代”选项卡）](../javascript/overrides.md)
*  [将处理的代码映射到原始源代码，以便进行调试](../javascript/source-maps.md)


### <a name="using-the-content-scripts-tab-for-microsoft-edge-extensions"></a>将"内容脚本"选项卡用于Microsoft Edge扩展

使用**导航器**窗格的**内容脚本**选项卡查看已安装的Microsoft Edge扩展插件加载的任何内容脚本。

:::image type="content" source="../media/content-scripts-tab.msft.png" alt-text="导航器窗格的&quot;内容脚本&quot;选项卡。" lightbox="../media/content-scripts-tab.msft.png":::

当调试程序进入你无法识别的代码时，你可能希望将代码标记为库代码，以避免单步执行该代码。  请参阅 [将内容脚本标记为库代码](../javascript/guides/mark-content-scripts-library-code.md)。


#### <a name="see-also"></a>另请参阅

* [内容脚本](https://developer.mozilla.org/Add-ons/WebExtensions/Content_scripts)
* [创建扩展教程，第 2 部分](../../extensions-chromium/getting-started/part2-content-scripts.md)


### <a name="using-the-snippets-tab-to-run-javascript-code-snippets-on-any-webpage"></a>使用"代码段"选项卡在任何网页上运行 JavaScript 代码段

使用**导航器**窗格的**代码片段**选项卡创建和保存 JavaScript 代码片段，以便可以在任何网页上轻松运行这些代码片段。

:::image type="content" source="../media/snippet.msft.png" alt-text="将 jQuery 库插入网页的代码段。" lightbox="../media/snippet.msft.png":::

例如，假设您经常在 **控制台**中输入以下代码，以将 jQuery 库插入页面，以便可以从控制台运行 jQuery **命令**：

```javascript
let script = document.createElement('script');
script.src = 'https://code.jquery.com/jquery-3.2.1.min.js';
script.crossOrigin = 'anonymous';
script.integrity = 'sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=';
document.head.appendChild(script);
```

相反，您可以将此代码保存在 **代码** 段中，然后随时轻松地运行它。  按 (Windows `Ctrl`+`S` /Linux) +`Command``S` 或 (macOS) 时，DevTools 会将**代码段**保存到文件系统。

有多种方法可以运行代码段：
*  在 **导航器窗格中** ，选择" **代码** 段"选项卡，然后选择代码段文件将其打开。  然后在"编辑器"窗格底部，选择****!["运行 ("运行](../media/run-snippet-icon.msft.png)"按钮。) 。
*  当 DevTools `Ctrl``P`+具有焦点时，按 (Windows/Linux) 或`P`+`Command` (macOS) 打开命令[菜单](../command-menu/index.md)，然后键入 。`!`

代码段 类似于小书签。


#### <a name="see-also"></a>另请参阅

* [在任何网页上运行 JavaScript 的代码片段](../javascript/snippets.md)


### <a name="using-the-command-menu-to-open-files"></a>使用命令菜单打开文件

若要打开文件，除了在**源**工具中使用**导航器**窗格外，还可以从 DevTools 中的任意位置使用命令菜单。

*  在 DevTools 中的任何位置，`Ctrl`+`P`按 Windows/Linux 或 `Command`+`P` macOS。  将显示"命令"菜单，并列出**源**工具的"**导航器"** 窗格选项卡中的所有资源。
*  或者，在**源**工具的"**导航器**"窗格的选项卡旁，选择"**...**（**更多选项**）"按钮，然后选择 **"打开文件**"。

若要显示并选取所有文件.js，请键入 `.js` 。

:::image type="content" source="../media/sources-command-menu-to-open-file.msft.png" alt-text="使用命令菜单打开文件。" lightbox="../media/sources-command-menu-to-open-file.msft.png":::

如果键入 `?` ，则命令菜单将显示几个命令，包括 **...打开文件**。  如果选择清除 `Backspace` "命令菜单"，将显示文件列表。

有关详细信息，请参阅 Run [commands with the Microsoft Edge DevTools Command Menu](../command-menu/index.md)。


<!-- ====================================================================== -->
## <a name="using-the-editor-pane-to-view-or-edit-files"></a>使用编辑器窗格查看或编辑文件

使用 **"** 编辑器"窗格查看从服务器返回的前端文件，以撰写当前网页，包括 JavaScript、HTML、CSS 和图像文件。  在 **编辑器** 窗格中编辑前端文件时，DevTools 会更新网页以运行修改后的代码。

:::image type="content" source="../media/editor-pane.msft.png" alt-text="&quot;源&quot;工具中的&quot;编辑器&quot;窗格。" lightbox="../media/editor-pane.msft.png":::

" **编辑器** "窗格对各种文件类型的支持级别如下：

| 文件类型 | 支持的操作 |
|---|---|
| JavaScript | 查看、编辑和调试。 |
| CSS | 查看和编辑。 |
| HTML | 查看和编辑。 |
| 图片 | “查看”。 |

默认情况下，刷新网页时将放弃编辑。  若要了解如何将更改保存到文件系统，请参阅上面的使用"文件系统"选项卡[定义本地 Workspace。](#using-the-filesystem-tab-to-define-a-local-workspace)

以下子部分涵盖"编辑器"窗格：
* [编辑 JavaScript 文件](#editing-a-javascript-file)
* [使用非常打印重新格式化缩小的 JavaScript 文件](#reformatting-a-minified-javascript-file-with-pretty-print)
* [将缩小代码映射到源代码以显示可读代码](#mapping-minified-code-to-your-source-code-to-show-readable-code)
* [从源代码转换到编译的前端代码](#transformations-from-source-code-to-compiled-front-end-code)
* [编辑 CSS 文件](#editing-a-css-file)
* [编辑 HTML 文件](#editing-an-html-file)
* [访问行号或函数](#going-to-a-line-number-or-function)
* [使用不同的工具时显示源文件](#displaying-source-files-when-using-a-different-tool)


### <a name="editing-a-javascript-file"></a>编辑 JavaScript 文件

若要在 DevTools 中编辑 JavaScript 文件，请在**源**工具中使用**编辑器**窗格。

:::image type="content" source="../media/editing-js-in-editor-pane.msft.png" alt-text="在&quot;编辑器&quot;窗格中编辑 JavaScript。" lightbox="../media/editing-js-in-editor-pane.msft.png":::

若要将文件加载到"编辑器"窗格中，请使用**导航器**窗格（左侧）中的"**页**"选项卡。  或使用“**命令菜单**”，如下所示: 在 DevTools 的右上角，选择“**自定义和控制 DevTools**”(`...`)，然后选择“**打开文件**”。


#### <a name="save-and-undo"></a>保存和撤消

若要使 JavaScript 更改`Ctrl`+`S`生效，请按 (Windows、Linux) 或 (`Command`+`S` macOS) 。

如果更改文件，文件名旁边将出现一个星号。
*  若要保存更改，请按 `Ctrl`+`S` Windows/Linux 或 `Command`+`S` macOS。
*  若要撤消更改，请按 `Ctrl`+`Z` Windows/Linux 或 `Command`+`Z` macOS。

默认情况下，刷新网页时将放弃您的编辑。  若要详细了解如何在本地文件系统中保存更改，请参阅使用 [Workspaces (Filesystem 选项卡编辑) ](../workspaces/index.md)。


#### <a name="find-and-replace"></a>查找和替换

**** 若要在当前文件中查找文本`Ctrl`+`F`，请选择"编辑器"窗格赋予其焦点，然后按 Windows/Linux `Command`+`F` 或 macOS。

:::image type="content" source="../media/find-replace.msft.png" alt-text="在&quot;源&quot;工具的&quot;编辑器&quot;窗格中查找和替换" lightbox="../media/find-replace.msft.png":::

若要查找和替换文本，请选择"**** 查找"文本框 (**A-\>B) "** 按钮。**** 查看 **可** (**文件时) "A-\>B"** 按钮。


#### <a name="showing-the-changes-you-made"></a>显示所做的更改

To review the changes you made to a file， right-click in the **Editor** pane and then select **Local Modifications**.

The **Drawer** opens at the bottom of DevTools， showing your changes within the **Changes** tab.

:::image type="content" source="../media/local-modifications.msft.png" alt-text="在&quot;箱&quot;的&quot;更改&quot;选项卡中显示本地修改" lightbox="../media/local-modifications.msft.png":::


#### <a name="changes-inside-a-function-take-effect"></a>函数中的更改生效

DevTools 不会重新运行脚本，因此唯一生效的 JavaScript 更改是你在函数内所做的更改。  例如，在下图中，我们向服务器返回的 JavaScript 添加了以下代码：
*  我们在任何函数 `console.log('A')` 之外添加了 语句。
*  我们在 函数 `console.log('B')` 中添加了 `onClick` 语句。
然后保存更改，在窗体中输入数字，然后选择窗体按钮以发送窗体。

提交表单（位于全局范围）后，不会运行，但在函数内，会运行 ， `console.log('A')` `console.log('B')` `onClick` 输出 `B` 到控制台：

:::image type="content" source="../media/edit-js.msft.png" alt-text="全局范围的 JavaScript 不会重新运行。" lightbox="../media/edit-js.msft.png":::


### <a name="reformatting-a-minified-javascript-file-with-pretty-print"></a>使用非常打印重新格式化缩小的 JavaScript 文件

若要使用"花式打印"重新设置文件的格式，使其可读，请在"编辑器****"窗格底部选择"花式打印"按钮" (![格式](../media/format-icon.msft.png)"。) 显示为大括号。  或者，如果 **"编辑器"** 窗格顶部显示"非常打印"按钮，您可以选择该按钮。

:::image type="content" source="../media/minified.msft.png" alt-text="&quot;非常不错&quot;的打印按钮。" lightbox="../media/minified.msft.png":::

重新格式化的文件显示在新选项卡中， `:formatted` 并附加到文件名后面。  重新格式化的代码是只读的。

:::image type="content" source="../media/pretty-printed.msft.png" alt-text="用 JavaScript 文件重新格式化 (的) 非常打印的字体" lightbox="../media/pretty-printed.msft.png":::

若要使重新格式化的文件滚动到在缩小文件中选择的代码：
1.  如果已重新格式化的文件选项卡已打开，请关闭它。
1.  在"编辑器"窗格中的缩小文件中选择一些代码。
1.  选择 **"彩色打印"** 按钮。
格式化的代码显示在新选项卡中，并滚动到所选的代码。

有关详细信息，请参阅使用非常打印 [重新设置缩小的 JavaScript 文件](../javascript/reference.md#reformat-a-minified-javascript-file-with-pretty-print)。


### <a name="mapping-minified-code-to-your-source-code-to-show-readable-code"></a>将缩小代码映射到源代码以显示可读代码

来自预处理器的源映射会导致 DevTools 加载原始 JavaScript 源文件以及服务器返回的缩小的转换后的 JavaScript 文件。  然后，在设置断点并逐步执行代码时查看原始源文件。  同时，Microsoft Edge运行缩小代码。

在 **"编辑器**"窗格中，如果右键单击 JavaScript 文件，然后选择"添加**** 源映射"，将出现一个弹出框，包含"源**映射 URL**"文本框和"添加 **"** 按钮。

即使组合、缩小或编译前端代码，源映射方法也保持其可读和可调试性。
有关详细信息，请参阅 [将处理的代码映射到原始源代码，以便进行调试](../javascript/source-maps.md)。


### <a name="transformations-from-source-code-to-compiled-front-end-code"></a>从源代码转换到编译的前端代码

如果使用转换 JavaScript 文件（如 React）的框架，则本地源 JavaScript 可能不同于服务器返回的前端 JavaScript。  此方案不支持工作区，但在此方案中支持源代码映射。

在开发环境中，服务器可能包括源地图和原始或 `.ts` `.jsx` 用于React。  源 **工具** 显示这些文件，但不允许编辑这些文件。  当你设置断点并使用调试器时，DevTools 将显示原始或文件，但实际上是分步调试 `.ts` `.jsx` JavaScript 文件缩小版本。

在此方案中， **源** 工具可用于检查和逐步执行从服务器返回的转换的前端 JavaScript。  使用调试器定义 Watch 表达式，并使用控制台输入 JavaScript 表达式以操作范围内的数据。


### <a name="editing-a-css-file"></a>编辑 CSS 文件

在 DevTools 中编辑 CSS 的方法有两种：
*  在 **"元素** "工具中，通过用户界面控件一次处理一个 CSS 设置。  在大多数情况下，建议使用此方法。  有关详细信息，请参阅"样式"窗格中[的"编辑 CSS 字体样式和设置"。](../inspect-styles/edit-fonts.md)
*  在 **"源** "工具中，使用文本编辑器。

源工具支持直接编辑 CSS 文件。  例如，如果编辑教程使用 [Workspaces (Filesystem 选项卡) ](../workspaces/index.md) 编辑 CSS 文件以 `H1` 匹配下面的样式规则，则呈现的网页左上角的元素将更改为绿色：

```css
h1 {
  color: green;
}
```

:::image type="content" source="../media/edit-css.msft.png" alt-text="编辑编辑器窗格中的 CSS，将 H1 标题的文本颜色更改为绿色。" lightbox="../media/edit-css.msft.png":::

CSS 更改会立即生效;无需手动保存更改。


#### <a name="see-also"></a>另请参阅

* [在“样式”窗格中编辑 CSS 字体样式和设置](../inspect-styles/edit-fonts.md)

* [适用于初学者的 DevTools：CSS 入门](../beginners/css.md) - 教程


### <a name="editing-an-html-file"></a>编辑 HTML 文件

在 DevTools 中编辑 HTML 的方法有两种：
*  在 **"元素** "工具中，通过用户界面控件一次处理一个 HTML 元素。
*  在 **"源** "工具中，使用文本编辑器。

:::image type="content" source="../media/sources-html-editor.msft.png" alt-text="源工具的 HTML 编辑器。" lightbox="../media/sources-html-editor.msft.png":::

与 JavaScript 或 CSS 文件不同，无法在"源"工具中直接编辑 Web 服务器返回的 HTML 文件。  若要使用"源"工具的编辑器编辑 HTML 文件，HTML 文件必须位于"工作区"或" **替代"** 选项卡上。 请参阅当前文章的以下子部分：
* [使用"文件系统"选项卡定义本地 Workspace](#using-the-filesystem-tab-to-define-a-local-workspace)
* [使用"覆盖"选项卡覆盖包含本地文件的服务器文件](#using-the-overrides-tab-to-override-server-files-with-local-files)

若要保存更改，请按 `Ctrl`+`S` Windows/Linux 或 `Command`+`S` macOS。  编辑后的文件标有星号。

若要查找文本，请按 `Ctrl`+`F` Windows/Linux 或 `Command`+`F` macOS。

若要撤消编辑，请按 `Ctrl`+`Z` Windows/Linux 或 `Command`+`Z` macOS。

若要在编辑 HTML 文件时查看其他命令，请在"编辑器"窗格中右键单击 HTML 文件。

您还可以使用 HTML 编辑器（而不是 DevTools）编辑 HTML。  例如，文章 [DevTools for beginners： Get started with HTML and the DOM](../beginners/html.md) uses a website that enables HTML editing within the webpage.


### <a name="going-to-a-line-number-or-function"></a>访问行号或函数

若要转到行号或符号 (如编辑器窗格中打开的文件中的函数名称) ，可以使用命令菜单，而不是滚动整个文件。

1.  在 **导航器** 窗格中，选择省略号 （...）（**更多选项**），然后选择 **打开文件**。  将显示"命令菜单"。
1.  键入下列字符之一：

| Character | 命令名称 | 用途 |
|---|---|---|
| \: | **转到行** | 转到行号。 |
| \@ | **转到符号** | 转到函数。  键入 时，命令菜单会列出在"编辑器"窗格中打开的 `@` JavaScript 文件中找到的函数。 |

有关详细信息，请参阅 Run [commands with the Microsoft Edge DevTools Command Menu](../command-menu/index.md)。


### <a name="displaying-source-files-when-using-a-different-tool"></a>使用不同的工具时显示源文件

在 DevTools 中查看源文件的主要位置是源**工具。**  但有时需要在查看或编辑源文件时访问其他工具，例如 **元素** 或 **控制台**。  使用" **箱"中的** 快速源 [工具，该工具](../customize/index.md#drawer)显示在 DevTools 的底部。

若要使用 **快速源工具** ，请执行以下操作：

1. 选择除"源"工具 **外** 的其他工具，如 **"元素"** 工具。

1. 按`Ctrl`+`Shift`+`P`（Windows、Linux）或 `Command`+`Shift`+`P` （macOS）。  命令菜单将打开。

1. 键入 `quick`，然后选择" **显示快速源"**。

    在"DevTools"窗口底部，将显示"箱"，并选中 **"快速源"** 工具。  快速**源**工具包含你在源工具中编辑的最后一个文件，**** 该文件位于 DevTools 代码编辑器的精简版本中。

1. 按`Ctrl`+`P` (Windows、Linux) 或+`Command``P` (macOS) 打开 **"打开文件"** 对话框。


<!-- ====================================================================== -->
## <a name="using-the-debugger-pane-to-debug-javascript-code"></a>使用调试器窗格调试 JavaScript 代码

使用 JavaScript 调试程序逐步调试服务器返回的 JavaScript 代码。
调试器包括 **调试器** 窗格，以及在 **编辑器** 窗格中的代码行上设置的断点。

借助调试器，你可以逐步调试代码，同时观察你指定的任何 JavaScript 表达式。  观察并手动更改变量值，并自动显示当前语句范围内哪些变量。

:::image type="content" source="../media/sources-paused-breakpoint-highlight-debug-pane.msft.png" alt-text="源工具 的调试器窗格。" lightbox="../media/sources-paused-breakpoint-highlight-debug-pane.msft.png":::

调试器支持标准调试操作，例如：
*  设置断点以暂停代码。
*  逐步执行代码。
*  查看和编辑属性和变量。
*  监视 JavaScript 表达式的值。
*  查看调用堆栈（到目前为止函数调用的序列）。

DevTools 中的调试器旨在外观、感觉和工作，如[Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)中的调试器[Visual Studio。](/visualstudio/debugger/navigating-through-code-with-the-debugger)

以下小节包括调试：
* [使用调试器的基本方法](#the-basic-approach-to-using-a-debugger)
* [调试器监视和作用域比 console.log 的优点](#advantages-of-the-debuggers-watch-and-scope-over-consolelog)
* [直接从Visual Studio Code调试](#debug-from-visual-studio-code-directly)
* [有关调试的文章](#articles-about-debugging)


### <a name="the-basic-approach-to-using-a-debugger"></a>使用调试器的基本方法

若要对 JavaScript 代码进行故障排除，可以在" `console.log()` 编辑器"窗格中 **插入** 语句。  另一种更强大的方法是使用 DevTools Microsoft Edge调试器。  熟悉调试器方法后，使用调试器实际上可以比 `console.log()` 更简单。

若要在网页上使用调试器，通常设置断点，然后从网页发送表单，如下所示：

1. 打开"[演示：入门](https://microsoftedge.github.io/Demos/devtools-js-get-started/)窗口或选项卡Microsoft Edge开发人员工具"网页调试 JavaScript。

   <!-- You can view the source code for the demo page at the [MicrosoftEdge/Demos > devtools-js-get-started](https://github.com/MicrosoftEdge/Demos/tree/main/devtools-js-get-started) repo folder. -->

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在 **演示网页旁边打开 DevTools** 窗口。

1. 在 DevTools 中，选择" **源"** 选项卡。

1. 在 **导航器** 窗格（左侧）中，选择 **页** 选项卡，然后选择 JavaScript 文件，例如 `get-started.js`。

1. 在 **"编辑器** "窗格中，选择可疑代码行附近的行号，以在该行上设置断点。  在下图中，在 行 上设置了断点 `var sum = addend1 + addend2;`。

1. 在网页中，输入值并提交表单。  例如，输入数字，如 `5` 和 `1` ，然后选择按钮添加数字 **1 和数字 2**。

    调试程序运行 JavaScript 代码，然后在断点处暂停。  调试程序现在进入暂停模式，因此你可以检查范围内属性的值，并逐步执行代码。

   :::image type="content" source="../media/sources-paused-breakpoint-highlights.msft.png" alt-text="进入调试器暂停模式。" lightbox="../media/sources-paused-breakpoint-highlights.msft.png":::

    在上图中，我们添加了 Watch 表达式和 ，并跨 `sum` `typeof sum` 断点添加了两行。

1. 检查"范围"窗格中 **的值，** 其中显示当前断点范围内的所有变量或属性及其值。

   此时，您可以在"监视" **窗格中添加表达式** 。  这些表达式与在语句中编写以调试代码 `console.log` 的表达式相同。

   若要运行 JavaScript 命令以在当前上下文中操作数据，请使用 **控制台**。  如果要在 DevTools 底部的"箱"中打开控制台，请按 `Esc`。

1. 使用 **调试器** 窗格顶部的控件逐步执行代码，例如 **步骤** （`F9`）。

    此演示中的 Bug 是你需要首先将输入数据从字符串转换为数字。

1.  若要修复 Bug，请刷新页面以重置网页表单，然后更改行：

    ```javascript
    var sum = addend1 + addend2;
    ```

    自：

    ```javascript
    var sum = parseInt(addend1) + parseInt(addend2);
    ```

1.  按 `Ctrl`+`S` (Windows、Linux) 或 `Command`+`S` (macOS) 将更改保存到本地缓存文件中。

1.  在 `5` 网页 `1` 中输入 和 ，然后单击"添加 **"** 按钮。  现在 **ScopeLocalsum** > **** > **：** 是数字 6，而不是字符串"51"。


#### <a name="see-also"></a>另请参阅

* [JavaScript 调试入门](../javascript/index.md) - 使用包含一些表单控件的现有简单网页的教程。


### <a name="advantages-of-the-debuggers-watch-and-scope-over-consolelog"></a>调试器监视和作用域比 console.log 的优点

这三种方法是等效的：

*  临时添加 语句 `console.log(sum)` 和 `console.log(typeof sum)` 代码，其中 `sum` 位于范围内。

*  当调试器在`sum`在范围内时暂停时，在 DevTools 的**控制台**窗格中发出语句`sum`和`console.log(typeof sum)`。

*  设置 **监视表达式** `sum` 和 `typeof sum` 调试 **器窗格中** 的。

当变量`sum`在范围内时，`sum`及其值将自动显示在**调试器**窗格的"**范围**"部分中，并且也会覆盖在计算`sum`的编辑器窗格中。  因此，您可能不需要为 定义 Watch 表达式 `sum`。

调试程序提供比语句更丰富、更灵活的显示 `console.log` 和环境。  例如，在调试器中，在逐步调试代码时，可以显示和更改所有当前定义的属性和变量的值。  还可以在 **控制台**中发出 JavaScript 语句，例如更改范围内数组中的值。   (显示控制台，请按 `Esc`.) 

刷新网页时，将保留断点和监视表达式。


### <a name="debug-from-visual-studio-code-directly"></a>直接从Visual Studio Code调试

若要使用功能更全的 Visual Studio Code 调试程序而不是 DevTools 调试器，请使用适用于 Visual Studio Code 的 **Microsoft Edge DevTools**扩展。

:::image type="content" source="../media/microsoft-edge-tools-for-vs-code-extension.msft.png" alt-text="Microsoft Edge开发人员的 DevTools Visual Studio Code。" lightbox="../media/microsoft-edge-tools-for-vs-code-extension.msft.png":::

此扩展提供从 Microsoft Visual Studio Code 中访问 Microsoft Edge DevTools 的 **Elements** 和 **网络** 工具。

有关详细信息，请参阅 [Visual Studio Code Web](../../visual-studio-code/index.md) 开发和 GitHub 自述Microsoft Edge开发人员工具[Visual Studio Code](https://github.com/microsoft/vscode-edge-devtools)。


### <a name="articles-about-debugging"></a>有关调试的文章

以下文章涵盖调试 **器** 窗格和断点：

* [JavaScript 调试](../javascript/index.md) 入门 - 使用 (简单的项目) 屏幕捕获的教程。

* [JavaScript 调试功能](../javascript/reference.md) - 如何使用调试器设置断点、逐步调试代码、查看和修改变量值、观看 JavaScript 表达式以及查看调用堆栈。

* [使用断点暂停代码](../javascript/breakpoints.md) - 如何在调试器中设置基本和专用断点。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/sources)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors/kaycebasques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
