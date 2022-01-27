---
title: '使用"文件系统"选项卡 ("工作区"编辑) '
description: 如何将在 DevTools 中所做的更改保存到磁盘。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: aad997a28a2ea7a4bf49d3c9e6f81e5ae262f508
ms.sourcegitcommit: 9caa4aac0a339a76e7f1e0f0f5d6d85a2492ea8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "12326038"
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
# <a name="edit-files-with-workspaces-filesystem-tab"></a>使用"文件系统"选项卡 ("工作区"编辑) 

本教程提供设置和使用 Workspace 的动手实践。  将文件添加到 Workspace 后，在 DevTools 中的源代码中所做的更改将保存在本地计算机上，并且在您刷新网页后将保留。

在开始本教程之前，你应知道如何执行以下操作：
* [使用 html、CSS 和 JavaScript 构建网页](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web)
* [使用 DevTools 对 CSS 进行基本更改](../css/index.md)
* [运行本地 HTTP Web 服务器](https://developer.mozilla.org/docs/Learn/Common_questions/set_up_a_local_testing_server#Running_a_simple_local_HTTP_server)


<!-- ====================================================================== -->
## <a name="overview"></a>概述

工作区使你可以将你在 Devtools 中更改的内容保存到计算机上同一文件的本地副本中。  对于本教程，计算机上应具有以下设置。

* 桌面上具有网站的源代码。

* 您从源代码目录运行本地 Web 服务器，以便可从 访问网站 `localhost:8080` 。

* 在 `localhost:8080` Microsoft Edge 中打开，并且使用 DevTools 更改网站的 CSS。

启用工作区后，在 DevTools 中所做的更改 CSS 将保存到桌面上的源代码中。


<!-- ====================================================================== -->
## <a name="limitations"></a>限制

如果你使用的是新式框架，它可能会将源代码从易于维护的格式转换为经过优化以尽快运行的格式。

工作区通常能够借助源映射 将优化的代码映射回原始 [源代码](https://blog.teamtreehouse.com/introduction-source-maps)。  但在每个框架使用源映射方面，框架之间有很多差异。  Devtools 不支持所有变体。

"工作区"功能不能与"创建应用React一起使用。

<!-- If you run into issues while using Workspaces with your framework of choice, or you get it working after some custom configuration, please [start a thread in the mailing list](https://groups.alphabet.com/forum/#!forum/alphabet-browser-developer-tools) or [ask a question on Stack Overflow](https://stackoverflow.com/questions/ask?tags=alphabet-browser-devtools) to share your knowledge with the rest of the DevTools community.  -->


<!-- ====================================================================== -->
## <a name="related-feature-local-overrides"></a>相关功能：本地覆盖

**本地覆盖** 是另一项类似于 Workspaces 的 DevTools 功能。  当您想要尝试对网页所做的更改，并且需要跨网页加载显示更改，但您不关心将更改映射到网页的源代码时，请使用本地替代。

<!--Todo: add section when content is ready  -->


<!-- ====================================================================== -->
## <a name="step-1-set-up"></a>步骤 1：设置

我们将设置演示，然后设置 DevTools。

### <a name="set-up-the-demo"></a>设置演示

1.  [打开演示源代码](https://github.com/MicrosoftEdge/Demos/tree/main/workspaces)。

1.  在 `app` 桌面上创建目录。  将 、 和 文件 `index.html` `styles.css` `script.js` 的副本从演示源代码保存到 `app` 目录中。  在本教程的其余部分中，目录称为 `~/Desktop/app` 。

1.  在 中启动本地 Web 服务器 `~/Desktop/app` 。  下面是一些用于启动的示例代码 `SimpleHTTPServer` ，但您可以使用您喜欢的任何服务器。

   ```bash
   cd ~/Desktop/app
   python -m SimpleHTTPServer # Python 2
   ```
   
   ```bash
   cd ~/Desktop/app
   python -m http.server # Python 3
   ```

1.  打开网站Microsoft Edge并导航到本地托管的网站版本。  你应该能够使用 URL（如 或 ） `localhost:8080` 访问 `http://0.0.0.0:8080` 它。  确切的 [端口号](https://en.wikipedia.org/wiki/Port_(computer_networking)#Use_in_URLs) 可能不同。

    :::image type="complex" source="../media/workspaces-workspaces-demo.msft.png" alt-text="演示。" lightbox="../media/workspaces-workspaces-demo.msft.png":::
       演示
    :::image-end:::

### <a name="set-up-devtools"></a>设置 DevTools

1.  选择 `Control` + `Shift` + `J` (Windows、Linux) 或 `Command` + `Option` + `J` (macOS) 打开 DevTools**** 的控制台面板。

    :::image type="complex" source="../media/workspaces-workspaces-demo-console.msft.png" alt-text="控制台面板。" lightbox="../media/workspaces-workspaces-demo-console.msft.png":::
       控制台**面板**
    :::image-end:::

1.  导航到 **"源"** 工具。

1.  在左侧 **导航器** (窗格中 **，) "文件系统"** 选项卡。

    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem.msft.png" alt-text="&quot;文件系统&quot;选项卡。" lightbox="../media/workspaces-workspaces-demo-sources-filesystem.msft.png":::
       " **文件系统"** 选项卡
    :::image-end:::

1.  选择 **"将文件夹添加到工作区"。**

1.  键入 `~/Desktop/app`。

1.  选择 **"** 允许"以授予 DevTools 读取和写入目录的权限。

    在" **文件系统"** 选项卡中，现在，、 和 旁边将出现 `index.html` `script.js` 一个绿色点 `styles.css` 。  绿色点表示 DevTools 已建立页面的网络资源与 中的文件之间的映射 `~/Desktop/app` 。

    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem-folder.msft.png" alt-text="&quot;文件系统&quot;选项卡现在指示本地文件和网络文件之间的映射。" lightbox="../media/workspaces-workspaces-demo-sources-filesystem-folder.msft.png":::
       " **文件系统** "选项卡现在指示本地文件和网络文件之间的映射
    :::image-end:::


<!-- ====================================================================== -->
## <a name="step-2-save-a-css-change-to-disk"></a>步骤 2：将 CSS 更改保存到磁盘

1.  打开 `styles.css`。

    > [!NOTE]
    > `color`元素的 `h1` 属性设置为 `fuchsia` 。

    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem-css.msft.png" alt-text="在文本编辑器中查看 styles.css。" lightbox="../media/workspaces-workspaces-demo-sources-filesystem-css.msft.png":::
       在 `styles.css` 文本编辑器中查看
    :::image-end:::

1.  选择“**元素**”工具。

1.  将 元素的 `color` 属性值 `<h1>` 更改为你最喜爱的颜色。
    请记住，您需要选择 DOM 树中的 元素，才能在"样式"窗格中显示应用于它的 `<h1>` CSS**** 规则。 ****  旁边是绿色 `styles.css:1` 点，表示你进行的任何更改都映射到 `~/Desktop/app/styles.css` 。

    :::image type="complex" source="../media/workspaces-workspaces-demo-elements-styles-css.msft.png" alt-text="文件链接的绿色指示器。" lightbox="../media/workspaces-workspaces-demo-elements-styles-css.msft.png":::
       文件链接的绿色指示器
    :::image-end:::

1.  再次 `styles.css` 在文本编辑器中打开。  `color`属性现在设置为你最喜爱的颜色。

1.  刷新页面。  元素的颜色 `<h1>` 仍设置为你最喜爱的颜色。  更改将在整个刷新中保留，因为进行更改时 DevTools 将更改保存到磁盘。  然后，在刷新页面时，本地服务器从磁盘提供文件的修改副本。


<!-- ====================================================================== -->
## <a name="step-3-save-an-html-change-to-disk"></a>步骤 3：将 HTML 更改保存到磁盘

可以使用"元素"工具更改 HTML 标记，但为了能够保存编辑，我们将使用"源"工具。


### <a name="change-html-from-the-elements-panel"></a>从元素面板更改 HTML

可以在 Element 工具中更改 HTML 内容，但是对 DOM 树的更改不会保存到磁盘，并且只影响当前浏览器会话。

DOM 树不是 HTML 源标记。

<!--### Try changing HTML from the Elements panel

> [!WARNING]
> The workflow that you are about to try does not work.  You are trying it now so that you do not waste time later trying to figure out why it is not working.

1.  Choose the **Elements** tool.
1.  Choose and edit the text content of the `h1` element, which says `Workspaces Demo`, and replace it with `I ❤️  Cake`.

    :::image type="complex" source="../media/workspaces-workspaces-demo-change-h1.msft.png" alt-text="Attempt to change html from the DOM Tree of the Elements panel." lightbox="../media/workspaces-workspaces-demo-change-h1.msft.png":::
       Attempt to change html from the DOM Tree of the **Elements** tool
    :::image-end:::

1.  Open `~/Desktop/app/index.html` in a text editor.  The change that you just made does not appear.
1.  Refresh the page.  The page reverts to the original title.

#### Optional: Why it is not working

> [!NOTE]
> This section describes why the workflow from [Try changing html from the Elements panel](#try-changing-html-from-the-elements-panel) does not work.  You should skip this section if you do not care why.

*   The tree of nodes that are displayed on the **Elements** tool represents the [DOM](https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction) of the page.
*   To display a page, a browser fetches html over the network, parses the html, and then converts it into a tree of DOM nodes.
*   If the page has any JavaScript, that JavaScript may add, delete, or change DOM nodes.  CSS may change the DOM, too, using the [`content`](https://developer.mozilla.org/docs/Web/CSS/content) property.
*   The browser eventually uses the DOM to determine what content it should present to browser users.
*   Therefore, the final state of the webpage displayed for users may be very different from the html that the browser fetched.
*   This makes it difficult for DevTools to resolve where a change made in the **Elements** tool should be saved, because the DOM is affected by HTML, JavaScript, and CSS.

In short, the **DOM Tree** `!==` HTML.
-->

### <a name="change-html-from-the-sources-tool"></a>从"源"工具更改 HTML

如果要保存对网页的 HTML 更改， **请使用"源** "工具。

1.  导航到 **"源"** 工具。

1.  在左侧 **导航器** (窗格中，) " **页面"** 选项卡。

1.  选择** (索引) 。 **  将打开页面的 HTML。

1.  将`<h1>Workspaces Demo</h1>`替换为`<h1>I ❤️  Cake</h1>`。  查看下图。

1.  选择 `Control` + `S` (Windows、Linux) 或 (`Command` + `S` macOS) 保存更改。

1.  刷新页面。  `<h1>`刷新页面后，元素将继续显示新文本。

    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-page-h1.msft.png" alt-text="从&quot;源&quot;工具更改 HTML。" lightbox="../media/workspaces-workspaces-demo-sources-page-h1.msft.png":::
       从"源"工具 **更改** HTML
    :::image-end:::

1.  打开 `~/Desktop/app/index.html`。  元素 `<h1>` 包含新文本。


<!-- ====================================================================== -->
## <a name="step-4-save-a-javascript-change-to-disk"></a>步骤 4：将 JavaScript 更改保存到磁盘

使用 DevTools 的代码编辑器的主要位置是 **源** 工具。  但有时你需要在编辑文件时访问其他工具，如**元素**工具或控制台面板。 ****  当 **任何** 工具打开时，快速源工具仅为你提供 **源** 工具中的编辑器。

若要与其他工具一起打开 DevTools 代码编辑器，请执行下列操作：

1.  导航到 **"元素"** 工具。

1.  按`Control`+`Shift`+`P`（Windows、Linux）或 `Command`+`Shift`+`P` （macOS）。  命令 **菜单将** 打开。

1.  键入 `quick` ，然后选择"显示**快速源"。**  在"DevTools"窗口的底部，将显示"**** 快速源"工具，其中显示 的内容，这是你在"源"工具中编辑的最后 `index.html` **一**个文件。

    :::image type="content" source="../media/workspaces-workspaces-demo-search-show-quick-source.msft.png" alt-text="使用命令菜单打开&quot;快速源&quot;工具。" lightbox="../media/workspaces-workspaces-demo-search-show-quick-source.msft.png":::

1.  按 `Control` + `P` (Windows、Linux) 或 `Command` + `P` (macOS) 打开"打开**文件**"对话框，如下所示。

1.  键入 `script` ，然后选择 **"app/script.js"。 **

    :::image type="content" source="../media/workspaces-workspaces-demo-search-script.msft.png" alt-text="使用script.js文件&quot;对话框打开文件。" lightbox="../media/workspaces-workspaces-demo-search-script.msft.png":::

    > [!NOTE]
    > 该 `Save Changes To Disk With Workspaces` 演示中的链接会定期设置样式。

1.  使用快速源工具将以下 ** 代码script.js** 库 **的底部** 。

    ```javascript
    console.log('greetings from script.js');
    document.querySelector('a').style = 'font-style:italic';
    ```

1.  选择 `Control` + `S` (Windows、Linux) 或 (`Command` + `S` macOS) 保存更改。

1.  刷新页面。

    > [!NOTE]
    > 页面上的链接现在为 italicized。

    :::image type="complex" source="../media/workspaces-workspaces-demo-elements-styles-quick-source-script.msft.png" alt-text="页面上的链接现在为 italicized。" lightbox="../media/workspaces-workspaces-demo-elements-styles-quick-source-script.msft.png":::
       页面上的链接现在为 italicized
    :::image-end:::


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

使用本教程中学到的内容在你自己的项目中设置工作区。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/workspaces/index)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
