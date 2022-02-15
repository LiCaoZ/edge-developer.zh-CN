---
title: 键盘快捷方式
description: 开发人员工具的默认Microsoft Edge快捷方式。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: 37e05971c06d4a279203b44b198eccc8d189409a
ms.sourcegitcommit: 2e0ec25e3cfc01b58fdddd5f4ac270632cb9b962
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2022
ms.locfileid: "12348247"
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

这些是开发人员工具的默认Microsoft Edge快捷方式。

在 DevTools 中，将鼠标悬停在图标上时，工具提示通常显示键盘快捷方式。

另请参阅[使用辅助技术导航 DevTools 和](../accessibility/navigation.md)[自定义键盘快捷方式](../customize/shortcuts.md)。


<!-- ====================================================================== -->
## <a name="keyboard-shortcuts-for-opening-devtools"></a>打开开发工具的键盘快捷方式

若要打开 DevTools，当光标聚焦在浏览器视口上时，请按以下键盘快捷方式：

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 打开上次使用的窗格 | `F12` 或 `Control`+`Shift`+`I` | `Command`+`Option`+`I` |
| 打开“**控制台**”工具 | `Control`+`Shift`+`J` | `Command`+`Option`+`J` |
| 打开“**元素**”工具。 | `Control`+`Shift`+`C` | `Command`+`Shift`+`C` 或 `Command`+`Option`+`C` |


<!-- ====================================================================== -->
## <a name="global-keyboard-shortcuts"></a>全局键盘快捷方式

大多数 DevTools 面板中都提供以下键盘快捷方式。

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 显示“**设置**” | `?` 或 `F1` | `?` 或 `Function`+`F1` |
| 聚焦于下一窗格 | `Control`+`]` | `Command`+`]` |
| 聚焦于上一窗格 | `Control`+`[` | `Command`+`[` |
| 切换回上一次使用的[对接位置](../customize/index.md#change-devtools-placement)。  如果开发工具已处于整个会话的默认位置，则此快捷方式将开发工具撤消到单独的窗口中 | `Control`+`Shift`+`D` | `Command`+`Shift`+`D` |
| 切换[设备仿真](../device-mode/index.md) | `Control`+`Shift`+`M` | `Command`+`Shift`+`M` |
| 切换**检查元素模式** | `Control`+`Shift`+`C` | `Command`+`Shift`+`C` |
| 打开“[命令菜单](../command-menu/index.md)”。 | `Control`+`Shift`+`P` | `Command`+`Shift`+`P` |
| 切换[抽屉](../customize/index.md#drawer) | `Escape` | `Escape` |
| 正常刷新 | `F5` 或 `Control`+`R` | `Command`+`R` |
| 硬刷新 | `Control`+`F5` 或 `Control`+`Shift`+`R` | `Command`+`Shift`+`R` |
| 在当前窗格中搜索文本。  **审核**、** 应用程序 **和**安全**工具不支持 | `Control`+`F` | `Command`+`F` |
| 在“[抽屉](../customize/index.md#drawer)”中打开“**搜索**”选项卡，可以在所有加载的资源中搜索文本 | `Control`+`Shift`+`F` | `Command`+`Option`+`F` |
| 在"源"工具 **中打开** 文件 | `Control`+`O` 或 `Control`+`P` | `Command`+`O` 或 `Command`+`P` |
| 放大 | `Control`+`Shift`+`+` | `Command`+`Shift`+`+` |
| 缩小 | `Control`+`-` | `Command`+`-` |
| 还原默认缩放级别 | `Control`+`0` | `Command`+`0` |
| 运行代码片段 | 按 `Control`+`O` 以打开 ["命令菜单](../command-menu/index.md)"， `!` 键入后跟脚本的名称，然后按 `Enter` | 按 `Command`+`O` 以打开 ["命令菜单](../command-menu/index.md)"， `!` 键入后跟脚本的名称，然后按 `Enter` |

<!-- TODO: make a bug about this UIPlacement link being ambiguous.  -->
<!-- TODO: Link "Inspect Element Mode" when a good section exists.  -->


<!-- ====================================================================== -->
## <a name="elements-tool-keyboard-shortcuts"></a>元素工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 撤消更改 | `Control`+`Z` | `Command`+`Z` |
| 恢复更改 | `Control`+`Y` | `Command`+`Shift`+`Z` |
| 选择当前所选元素上方/下方元素 | `Up Arrow` / `Down Arrow` | `Up Arrow` / `Down Arrow` |
| 展开当前选定的节点。  如果节点已展开，则此快捷方式将选择下方的元素 | `Right Arrow` | `Right Arrow` |
| 折叠当前选定的节点。  如果节点已折叠，则此快捷方式将选择上方的元素 | `Left Arrow` | `Left Arrow` |
| 展开或折叠当前选定的节点及所有子节点 | 保留 `Control`+`Alt`，然后单击 **元素** 名称旁边的箭头图标 | 保留 `Option`，然后单击 **元素** 名称旁边的箭头图标 |
| 在当前选定的元素上切换“**编辑属性**”模式 | `Enter` | `Enter` |
| 进入“**编辑属性**”模式后，选择下一个/上一个属性 | `Tab` / `Shift`+`Tab` | `Tab` / `Shift`+`Tab` |
| 隐藏当前所选元素 | `H` | `H` |
| 在当前选定的元素上切换“**编辑为 HTML**”模式 | `Function`+`F2` | `F2` |

### <a name="styles-pane-keyboard-shortcuts"></a>样式窗格键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 转到声明属性值的行 | 保留 `Control`，然后单击属性值 | 保留 `Command`，然后单击属性值 |
| 循环显示颜色值的 RBGA、HSLA 和 Hex 表示形式 | 保留 `Shift`，然后单击值 **旁边的"颜色** 预览"框 | 保留 `Shift`，然后单击值 **旁边的"颜色** 预览"框 |
| 选择下一个/上一个属性或值 | 单击属性名称或值，然后按 `Tab` / `Shift`+`Tab` | 单击属性名称或值，然后按 `Tab` / `Shift`+`Tab` |
| 将属性值递增/减 0.1 | 单击某个值，然后按 `Alt`+`Up Arrow` / `Alt`+`Down Arrow` | 单击某个值，然后按 `Option`+`Up Arrow` /Option+向下箭头 |
| 将属性值递增/减 1 | 单击某个值，然后按 `Up Arrow` / `Down Arrow` | 单击某个值，然后按 `Up Arrow` / `Down Arrow` |
| 将属性值递增/减 10 | 单击某个值，然后按 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` | 单击某个值，然后按 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` |
| 将属性值递增/减 100 | 单击某个值，然后按 `Control`+`Up Arrow` / `Control`+`Down Arrow` | 单击某个值，然后按 `Command`+`Up Arrow` / `Command`+`Down Arrow` |
| 循环浏览角度值的 (度) 、 ( (grad) 、弧度 (rad) 并旋转角度值的 () 表示形式 | 保留 `Shift` ，然后单击 **值旁边的"角度** 预览"框 | 保留 `Shift` ，然后单击 **值旁边的"角度** 预览"框 |
| 将角度值递增/减 1 | 单击 **值旁边的"角度** 预览"框，然后按 `Up Arrow` / `Down Arrow` | 单击 **值旁边的"角度** 预览"框，然后按 `Up Arrow` / `Down Arrow` |
| 将角度值递增/减 10 | 单击 **值旁边的"角度** 预览"框，然后按 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` | 单击 **值旁边的"角度** 预览"框，然后按 `Shift`+`Up Arrow` / `Shift`+`Down Arrow` |
| 将角度值递增/减 15 | Click the **Angle Preview** box next to the value then press `Shift`， click / mouse slide on the **Angle Clock Overlay** | Click the **Angle Preview** box next to the value then press `Shift`， click / mouse slide on the **Angle Clock Overlay** |


<!-- ====================================================================== -->
## <a name="sources-tool-keyboard-shortcuts"></a>源工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 如果当前正在运行脚本 (，请暂停脚本运行时) 如果当前 (已暂停，请恢复)  | `F8` 或 `Control`+`\` | `F8` 或 `Command`+`\` |
| 单步跳过下一函数调用 | `F10` 或 `Control`+`'` | `F10` 或 `Command`+`'` |
| 单步执行下一函数调用 | `F11` 或 `Control`+`;` | `F11` 或 `Command`+`;` |
| 跳出当前函数 | `Shift`+`F11` 或 `Control`+`Shift`+`;` | `Shift`+`F11` 或 `Command`+`Shift`+`;` |
| 暂停时继续至指定的代码行[](../javascript/breakpoints.md#line-of-code-breakpoints) | 保留 `Control`，然后单击代码行 | 保留 `Command`，然后单击代码行 |
| 选择当前所选帧下方/上方的调用帧 | `Control`+`.` / `Control`+`,` | `Control`+`.` / `Control`+`,` |
| 保存对本地修改的更改 | `Control`+`S` | `Command`+`S` |
| 保存所有更改 | `Control`+`Alt`+`S` | `Command`+`Option`+`S` |
| 导航到行 | `Control`+`G` | `Control`+`G` |
| 跳转到当前打开的文件的行号 | 按 `Control`+`O` 打开命令 [菜单](../command-menu/index.md)，键入 `:` 后跟行号，然后按 `Enter` | 按 `Command`+`O` 打开命令 [菜单](../command-menu/index.md)，键入 `:` 后跟行号，然后按 `Enter` |
| 跳转到当前打开的文件列， (第 5 行，第 9 列)  | 按`Control`+`O`打开命令[菜单](../command-menu/index.md)`:`，键入 ，然后键入行号，然后`:`键入另一个 ，然后按列号 `Enter` | 按`Command`+`O`打开命令[菜单](../command-menu/index.md)`:`，键入 ，然后键入行号，然后`:`键入另一个 ，然后按列号 `Enter` |
| 如果当前文件为 HTML 或脚本，则导航到函数声明。  <br />  如果当前文件是样式表，请导航到规则集。  | 按 `Control`++`Shift``O`，然后键入声明/规则集名称，或者从选项列表中选择它 | press `Command`++`Shift``O`，然后键入声明/规则集的名称，或者从选项列表中选择它 |
| 关闭活动的选项卡 | `Alt`+`W` | `Option`+`W` |

### <a name="code-editor-keyboard-shortcuts"></a>代码编辑器键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 删除最后一个词中的所有字符，直到到达光标 | `Control`+`Delete` | `Option`+`Delete` |
| 添加或删除[代码行断点](../javascript/breakpoints.md#line-of-code-breakpoints) | 将光标聚焦在行上，然后按 `Control`+`B` | 将光标聚焦在行上，然后按 `Command`+`B` |
| 导航到匹配的括号 | `Control`+`M` | `Control`+`M` |
| 切换单行注释。  如果选择了多行，开发工具将注释添加到每行的起始位置 | `Control`+`/` | `Command`+`/` |
| 打开或关闭下一次出现的任何单词。  每次出现时都同时突出显示 | `Control`+`D` / `Control`+`U` | `Command`+`D` / `Command`+`U` |


<!-- ====================================================================== -->
## <a name="performance-tool-keyboard-shortcuts"></a>性能工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 开始 /停止录制。 | `Control`+`E` | `Command`+`E` |
| 保存录制 | `Control`+`S` | `Command`+`S` |
| 加载录制 | `Control`+`O` | `Command`+`O` |


<!-- ====================================================================== -->
## <a name="memory-tool-keyboard-shortcuts"></a>内存工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 开始 /停止录制。 | `Control`+`E` | `Command`+`E` |


<!-- ====================================================================== -->
## <a name="console-tool-keyboard-shortcuts"></a>控制台工具键盘快捷方式

| 操作 | Windows/Linux | macOS |
|---|---|---|
| 接受自动完成建议 | `Right Arrow` 或 `Tab` | `Right Arrow` 或 `Tab` |
| 拒绝自动完成建议 | `Escape` | `Escape` |
| 获取上一语句 | `Up Arrow` | `Up Arrow` |
| 获取下一语句 | `Down Arrow` | `Down Arrow` |
| 聚焦于“**控制台**” | `Control`+ `` ` `` | `Control`+`` ` `` |
| 清除“**控制台**” | `Control`+`L` | `Command`+`K` 或 `Option`+`L` |
| 强制多行输入。  该快捷方式通常是不需要的，因为默认情况下，开发工具应该检测多行方案 | `Shift`+`Enter` | `Command`+`Return` |
| 运行 | `Enter` | `Return` |
| 展开记录到控制台的对象的所有子属性 | 保留 `Alt`， **然后单击"展开** (![展开"。](../media/expand-icon.msft.png))  | 按住 `Alt`，**然后单击展开 (**![展开。](../media/expand-icon.msft.png)) 。 |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用辅助技术导航开发工具](../accessibility/navigation.md)
* [自定义键盘快捷方式](../customize/shortcuts.md)
* [在“命令”菜单中运行命令](../command-menu/index.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/shortcuts)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
