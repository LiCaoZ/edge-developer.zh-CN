---
title: 键盘快捷方式
description: Microsoft Edge DevTools 的默认键盘快捷方式。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: b44ed1eaf56f41c593c09e5aa841d31ea0ce0cd9
ms.sourcegitcommit: 0d14dd864518c5b10cb844c14d80ea1cb589481c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2022
ms.locfileid: "12759715"
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
# <a name="keyboard-shortcuts"></a>键盘快捷方式

这些是 Microsoft Edge DevTools 的默认键盘快捷方式。

在 DevTools 中，将鼠标悬停在图标上时，工具提示通常会显示键盘快捷方式。

另请参阅 [使用辅助技术导航 DevTools](../accessibility/navigation.md) 和 [自定义键盘快捷方式](../customize/shortcuts.md)。


<!-- ====================================================================== -->
## <a name="keyboard-shortcuts-for-opening-devtools"></a>打开开发工具的键盘快捷方式

若要打开 DevTools，请在光标聚焦于浏览器视区时按以下键盘快捷方式：

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 打开上次使用的窗格 | `F12` 或 `Ctrl`+`Shift`+`I` | `Command`+`Option`+`I` |
| 打开“**控制台**”工具 | `Ctrl`+`Shift`+`J` | `Command`+`Option`+`J` |
| 打开“**元素**”工具。 | `Ctrl`+`Shift`+`C` | `Command`+`Shift`+`C` 或 `Command`+`Option`+`C` |


<!-- ====================================================================== -->
## <a name="global-keyboard-shortcuts"></a>全局键盘快捷方式

以下键盘快捷方式在大多数 DevTools 面板中可用。

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 显示“**设置**” | `Shift`+`?` 或  `F1` | `Shift`+`?` 或 `Function`+`F1` |
| 聚焦于下一窗格 | `Ctrl`+`]` | `Command`+`]` |
| 聚焦于上一窗格 | `Ctrl`+`[` | `Command`+`[` |
| 切换回上一次使用的[对接位置](../customize/placement.md)。  如果 DevTools 在整个会话中处于默认位置，则此快捷方式会将 DevTools 撤空到单独的窗口中。 | `Ctrl`+`Shift`+`D` | `Command`+`Shift`+`D` |
| 切换[设备仿真](../device-mode/index.md) | `Ctrl`+`Shift`+`M` | `Command`+`Shift`+`M` |
| 切换**检查元素模式** | `Ctrl`+`Shift`+`C` | `Command`+`Shift`+`C` |
| 打开“[命令菜单](../command-menu/index.md)”。 | `Ctrl`+`Shift`+`P` | `Command`+`Shift`+`P` |
| 切换[抽屉](../customize/index.md#drawer) | `Escape` | `Escape` |
| 正常刷新 | `F5` 或 `Ctrl`+`R` | `Command`+`R` |
| 硬刷新 | `Ctrl`+`F5` 或 `Ctrl`+`Shift`+`R` | `Command`+`Shift`+`R` |
| 在当前窗格中搜索文本。  **审核**、** 应用程序 **和**安全**工具不支持 | `Ctrl`+`F` | `Command`+`F` |
| 在“[抽屉](../customize/index.md#drawer)”中打开“**搜索**”选项卡，可以在所有加载的资源中搜索文本 | `Ctrl`+`Shift`+`F` | `Command`+`Option`+`F` |
| 在 **“源** ”工具中打开文件 | `Ctrl`+`O` 或 `Ctrl`+`P` | `Command`+`O` 或 `Command`+`P` |
| 放大 | `Ctrl`+`Shift`+`+` | `Command`+`Shift`+`+` |
| 缩小 | `Ctrl`+`-` | `Command`+`-` |
| 还原默认缩放级别 | `Ctrl`+`0` | `Command`+`0` |
| 运行代码片段 | 按 `Ctrl`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入 `!` 后跟脚本名称，然后按 `Enter` | 按 `Command`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入 `!` 后跟脚本名称，然后按 `Enter` |

<!-- TODO: make a bug about this UIPlacement link being ambiguous.  -->
<!-- TODO: Link "Inspect Element Mode" when a good section exists.  -->


<!-- ====================================================================== -->
## <a name="elements-tool-keyboard-shortcuts"></a>元素工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 撤消更改 | `Ctrl`+`Z` | `Command`+`Z` |
| 恢复更改 | `Ctrl`+`Y` | `Command`+`Shift`+`Z` |
| 选择当前所选元素上方/下方元素 | `Up Arrow` / `Down Arrow` | `Up Arrow` / `Down Arrow` |
| 展开当前选定的节点。  如果节点已展开，则此快捷方式将选择下方的元素 | `Right Arrow` | `Right Arrow` |
| 折叠当前选定的节点。  如果节点已折叠，则此快捷方式将选择上方的元素 | `Left Arrow` | `Left Arrow` |
| 展开或折叠当前选定的节点及所有子节点 | 按住 `Ctrl`+`Alt`，然后单击元素名称旁边的 **箭头** 图标 | 按住 `Option`，然后单击元素名称旁边的 **箭头** 图标 |
| 在当前选定的元素上切换“**编辑属性**”模式 | `Enter` | `Enter` |
| 进入“**编辑属性**”模式后，选择下一个/上一个属性 | `Tab` / `Shift`+`Tab` | `Tab` / `Shift`+`Tab` |
| 隐藏当前所选元素 | `H` | `H` |
| 在当前选定的元素上切换“**编辑为 HTML**”模式 | `Function`+`F2` | `F2` |

### <a name="styles-pane-keyboard-shortcuts"></a>样式窗格键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 转到声明属性值的行 | 按住 `Ctrl`，然后单击属性值 | 按住 `Command`，然后单击属性值 |
| 循环显示颜色值的 RBGA、HSLA 和 Hex 表示形式 | 按住 `Shift`，然后单击值旁边的 **“颜色预览** ”框 | 按住 `Shift`，然后单击值旁边的 **“颜色预览** ”框 |
| 选择下一个/上一个属性或值 | 单击属性名称或值，然后按 `Tab` / `Shift`+`Tab` | 单击属性名称或值，然后按 `Tab` / `Shift`+`Tab` |
| 将属性值递增/减 0.1 | 单击某个值，然后按下 `Alt`+`Up Arrow` / `Alt`+`Down Arrow` | 单击一个值，然后按 `Option`+`Up Arrow` /Option+向下键 |
| 将属性值递增/减 1 | 单击某个值，然后按下 `Up Arrow` / `Down Arrow` | 单击某个值，然后按下 `Up Arrow` / `Down Arrow` |
| 将属性值递增/减 10 | 单击某个值，然后按下 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` | 单击某个值，然后按下 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` |
| 将属性值递增/减 100 | 单击某个值，然后按下 `Ctrl`+`Up Arrow` / `Ctrl`+`Down Arrow` | 单击某个值，然后按下 `Command`+`Up Arrow` / `Command`+`Down Arrow` |
| 循环浏览)  (度、渐变 (渐变) 、弧度 (半径) ， (转) 角度值的表示形式 | 按住 `Shift` ，然后单击值旁边的 **“角度预览** ”框 | 按住 `Shift` ，然后单击值旁边的 **“角度预览** ”框 |
| 将角度值递增/递减 1 | 单击值旁边的 **“角度预览** ”框，然后按下 `Up Arrow` / `Down Arrow` | 单击值旁边的 **“角度预览** ”框，然后按下 `Up Arrow` / `Down Arrow` |
| 将角度值递增/递减 10 | 单击值旁边的 **“角度预览** ”框，然后按下 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` | 单击值旁边的 **“角度预览** ”框，然后按下 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` |
| 将角度值递增/递减 15 | 单击值旁边的 **“角度预览**”框，然后在 **“角度时钟覆盖**”上单`Shift`击/鼠标幻灯片 | 单击值旁边的 **“角度预览**”框，然后在 **“角度时钟覆盖**”上单`Shift`击/鼠标幻灯片 |


<!-- ====================================================================== -->
## <a name="sources-tool-keyboard-shortcuts"></a>源工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 如果当前) 运行，则暂停脚本运行时 (;如果当前暂停，则 (恢复)  | `F8` 或 `Ctrl`+`\` | `F8` 或 `Command`+`\` |
| 单步跳过下一函数调用 | `F10` 或 `Ctrl`+`'` | `F10` 或 `Command`+`'` |
| 单步执行下一函数调用 | `F11` 或 `Ctrl`+`;` | `F11` 或 `Command`+`;` |
| 跳出当前函数 | `Shift`+`F11` 或 `Ctrl`+`Shift`+`;` | `Shift`+`F11` 或 `Command`+`Shift`+`;` |
| 暂停时继续至指定的代码行[](../javascript/breakpoints.md#line-of-code-breakpoints) | 按住 `Ctrl`，然后单击代码行 | 按住 `Command`，然后单击代码行 |
| 选择当前所选帧下方/上方的调用帧 | `Ctrl`+`.` / `Ctrl`+`,` | `Ctrl`+`.` / `Ctrl`+`,` |
| 保存对本地修改的更改 | `Ctrl`+`S` | `Command`+`S` |
| 保存所有更改 | `Ctrl`+`Alt`+`S` | `Command`+`Option`+`S` |
| 导航到行 | `Ctrl`+`G` | `Ctrl`+`G` |
| 跳转到当前打开的文件的行号 | 按 `Ctrl`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入 `:` 后跟行号，然后按 `Enter` | 按 `Command`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入 `:` 后跟行号，然后按 `Enter` |
| 跳转到当前打开的文件 (列，例如第 5 行第 9 列)  | 按 `Ctrl`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入，然后键 `:`入行号，然后键入另一行 `:`号，然后按列号 `Enter` | 按 `Command`+`O` 下以打开 [命令菜单](../command-menu/index.md)，键入，然后键 `:`入行号，然后键入另一行 `:`号，然后按列号 `Enter` |
| 如果当前文件为 HTML 或脚本，则导航到函数声明。  <br />  如果当前文件是样式表，请导航到规则集。  | 按`Ctrl`++`Shift``O`下，然后键入声明/规则集的名称，或从选项列表中选择它 | 按`Command`++`Shift``O`下，然后键入声明/规则集的名称，或从选项列表中选择它 |
| 关闭活动的选项卡 | `Alt`+`W` | `Option`+`W` |

### <a name="code-editor-keyboard-shortcuts"></a>代码编辑器键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 删除最后一个词中的所有字符，直到到达光标 | `Ctrl`+`Delete` | `Option`+`Delete` |
| 添加或删除[代码行断点](../javascript/breakpoints.md#line-of-code-breakpoints) | 将光标聚焦在行上，然后按 `Ctrl`+`B` | 将光标聚焦在行上，然后按 `Command`+`B` |
| 导航到匹配的括号 | `Ctrl`+`M` | `Ctrl`+`M` |
| 切换单行注释。  如果选择了多行，开发工具将注释添加到每行的起始位置 | `Ctrl`+`/` | `Command`+`/` |
| 打开或关闭下一次出现的任何单词。  每次出现时都同时突出显示 | `Ctrl`+`D` / `Ctrl`+`U` | `Command`+`D` / `Command`+`U` |


<!-- ====================================================================== -->
## <a name="performance-tool-keyboard-shortcuts"></a>性能工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 开始 /停止录制。 | `Ctrl`+`E` | `Command`+`E` |
| 保存录制 | `Ctrl`+`S` | `Command`+`S` |
| 加载录制 | `Ctrl`+`O` | `Command`+`O` |


<!-- ====================================================================== -->
## <a name="memory-tool-keyboard-shortcuts"></a>内存工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 开始 /停止录制。 | `Ctrl`+`E` | `Command`+`E` |


<!-- ====================================================================== -->
## <a name="console-tool-keyboard-shortcuts"></a>控制台工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 接受自动完成建议 | `Right Arrow` 或 `Tab` | `Right Arrow` 或 `Tab` |
| 拒绝自动完成建议 | `Escape` | `Escape` |
| 获取上一语句 | `Up Arrow` | `Up Arrow` |
| 获取下一语句 | `Down Arrow` | `Down Arrow` |
| 聚焦于“**控制台**” | `Ctrl`+ `` ` `` | `Ctrl`+`` ` `` |
| 清除“**控制台**” | `Ctrl`+`L` | `Command`+`K` 或 `Option`+`L` |
| 强制多行输入。  该快捷方式通常是不需要的，因为默认情况下，开发工具应该检测多行方案 | `Shift`+`Enter` | `Command`+`Return` |
| 运行 | `Enter` | `Return` |
| 展开记录到控制台的对象的所有子属性 | 按住 `Alt`，然后单击“ **展开** (![。](../media/expand-icon.msft.png))  | 按住 `Alt`，然后单击“ **展开** (![。](../media/expand-icon.msft.png)) 。 |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用辅助技术导航开发工具](../accessibility/navigation.md)
* [自定义键盘快捷方式](../customize/shortcuts.md)
* [在“命令”菜单中运行命令](../command-menu/index.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developer.chrome.com/docs/devtools/shortcuts/)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
