---
title: 在任何网页上运行 JavaScript 的代码片段
description: 代码段是可以在开发人员工具的源工具中创作和运行Microsoft Edge脚本。  可以从任何网页访问和运行资源。  当你运行代码片段时，它是通过当前打开网页的上下文运行。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
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
# <a name="run-snippets-of-javascript-on-any-webpage"></a>在任何网页上运行 JavaScript 的代码片段

如果在[控制台](../console/index.md)中重复运行相同的代码，请考虑换成将代码另存为代码片段。  代码片段是在[源](../sources/index.md)工具中创作的脚本。  代码段有权访问网页的 JavaScript 上下文，并且您可以在任何网页上运行代码段。  大多数网页的安全设置会阻止在代码片段中加载其他脚本。  因此，必须将所有代码都包括在一个文件中。

代码段是 [bookmarklet](https://en.wikipedia.org/wiki/Bookmarklet) 的替代方法，区别在于代码段仅在 DevTools 中运行，并且不限于 URL 的允许长度。

使用代码片段在第三方网页进行少许内容更改的绝佳方法。  将代码片段中的代码更改添加到当前网页，并在同一上下文中运行。  有关更改网页的现有代码的信息，请参阅 [替代](./overrides.md)。

下图显示了左侧的 DevTools 主页和右侧一些代码段源代码。

运行代码段之前的网页：

:::image type="content" source="../media/javascript-sources-snippets-split-screen.msft.png" alt-text="运行代码段之前的网页。" lightbox="../media/javascript-sources-snippets-split-screen.msft.png":::

运行代码段之前网页的代码段源代码：

```javascript
console.log('Hello, Snippets!');
document.body.innerHTML = '';
var p = document.createElement('p');
p.textContent = 'Hello, Snippets!';
document.body.appendChild(p);
```

下图所示为运行代码片段后出现的网页。  将弹出**控制台抽屉式选项卡**显示代码片段记录的 `Hello, Snippets!` 消息，并且网页的内容全部更改。

:::image type="content" source="../media/javascript-sources-snippets-split-screen-after.msft.png" alt-text="运行代码段后的网页。" lightbox="../media/javascript-sources-snippets-split-screen-after.msft.png":::


<!-- ====================================================================== -->
## <a name="open-the-snippets-tab"></a>打开"代码段"选项卡

左侧**导航**器窗格中的"代码**** 段"选项卡列出了您的代码段。  当您要编辑代码段时，您需要从"代码段"选项卡 **中打开** 它。

:::image type="content" source="../media/javascript-sources-snippets-pane.msft.png" alt-text="&quot;代码段&quot;选项卡。" lightbox="../media/javascript-sources-snippets-pane.msft.png":::

### <a name="open-the-snippets-tab-with-a-mouse"></a>用鼠标打开"代码段"选项卡

1. 选择" **源"** 选项卡。 将显示 **"源** "工具。

   :::image type="content" source="../media/javascript-sources-page-pane.msft.png" alt-text="左侧打开&quot;页面&quot;选项卡的&quot;源&quot;工具。" lightbox="../media/javascript-sources-page-pane.msft.png":::

1. 在左侧**导航器** (窗格中，) 代码**段"** 选项卡。 若要访问 **"代码段**"选项，您可能需要****![单击"更多选项卡" (更多选项卡](../media/more-tabs-icon.msft.png)) 按钮。

### <a name="open-the-snippets-tab-with-the-command-menu"></a>使用命令菜单打开"代码段"选项卡

1. 在 DevTools 中选择任何内容，以便 DevTools 具有焦点。

1. 按 `Control`++`Shift``P` (Windows、Linux) 或`P` `Command`+`Shift`+ (macOS) 打开命令菜单。

1. 键入 `Snippets`，选择 **"显示代码**段"，然后按 `Enter` 以运行命令。

   :::image type="content" source="../media/javascript-search-show-snippets.msft.png" alt-text="&quot;显示代码段&quot;命令。" lightbox="../media/javascript-search-show-snippets.msft.png":::


<!-- ====================================================================== -->
## <a name="create-snippets"></a>创建代码片段

### <a name="create-a-snippet-through-the-sources-tool"></a>通过"源"工具创建代码段

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 单击 **"新建代码段"**。

1. 输入代码段的名称，然后按 `Enter`。

   :::image type="content" source="../media/javascript-sources-snippets-naming.msft.png" alt-text="命名代码段。" lightbox="../media/javascript-sources-snippets-naming.msft.png":::

### <a name="create-a-snippet-through-the-command-menu"></a>通过命令菜单创建代码片段

1. 将光标停在 DevTools 中的任一位置。

1. 按 `Control`++`Shift``P` (Windows、Linux) 或`P` `Command`+`Shift`+ (macOS) 打开命令菜单。

1. 开始键入 ，选择`snippet`**创建新代码段**，然后按 `Enter`。

   :::image type="content" source="../media/javascript-search-create-new-snippet.msft.png" alt-text="用于创建新代码段的命令。" lightbox="../media/javascript-search-create-new-snippet.msft.png":::

若要使用自定义名称重命名新代码段，请参阅 [重命名代码段](#rename-snippets)。


<!-- ====================================================================== -->
## <a name="edit-snippets"></a>编辑代码片段

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 在 **"代码段** "选项卡中，选择要编辑的代码段的名称。  代码片段将在**代码编辑器**中打开。

   :::image type="content" source="../media/javascript-sources-snippets-editor-saved.msft.png" alt-text="代码编辑器。" lightbox="../media/javascript-sources-snippets-editor-saved.msft.png":::

1. 使用**代码编辑器**将 JavaScript 添加到代码片段。

1. 当代码片段名称旁边出现星号时，表示有代码未保存。  按 `Control`+`S` (Windows、Linux) 或 `Command`+`S` (macOS) 保存。

   :::image type="content" source="../media/javascript-sources-snippets-editor-unsaved.msft.png" alt-text="代码段名称旁边的星号表示未保存的代码。" lightbox="../media/javascript-sources-snippets-editor-unsaved.msft.png":::


<!-- ====================================================================== -->
## <a name="run-snippets"></a>运行代码片段

### <a name="run-a-snippet-from-the-sources-tool"></a>从源工具运行代码段

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 单击要运行的代码段的名称。  代码片段将在**代码编辑器**中打开。

1. 单击 **"运行代码段** (![运行代码段](../media/run-snippet-icon.msft.png) "。) 。

### <a name="run-a-snippet-with-the-command-menu"></a>使用命令菜单运行代码片段

1. 将光标停在 DevTools 中的任一位置。

1. 按 `Control`++`Shift``P` (Windows、Linux) 或`P` `Command`+`Shift`+ (macOS) 打开命令菜单。

1. 删除 `>` 字符并在要运行的代码片段名称后键入 `!` 字符。

   :::image type="content" source="../media/javascript-search-run-command.msft.png" alt-text="从命令菜单运行代码段。" lightbox="../media/javascript-search-run-command.msft.png":::

1. 按 `Enter` 以运行代码段。


<!-- ====================================================================== -->
## <a name="rename-snippets"></a>重命名代码片段

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 右键单击代码段名称，然后选择"重命名 **"**。


<!-- ====================================================================== -->
## <a name="delete-snippets"></a>删除代码片段

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 右键单击代码段名称，然后选择"删除 **"**。


<!-- ====================================================================== -->
## <a name="save-snippets"></a>保存代码段

默认情况下，代码段仅在 DevTools 中可用，但您也可以将它们保存到磁盘。

1. [打开"代码段"选项卡](#open-the-snippets-tab)。

1. 右键单击代码段名称，然后选择" **另存为"**。

1. 当系统提示时，输入文件名和位置。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/snippets)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
