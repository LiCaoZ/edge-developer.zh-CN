---
title: 自定义键盘快捷方式
description: 自定义键盘快捷方式，包括匹配来自Visual Studio Code。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/10/2021
---
# <a name="customize-keyboard-shortcuts"></a>自定义键盘快捷方式

在 **设置** 的"快捷方式"页中，可以查看 Microsoft Edge DevTools 定义的快捷方式、为特定操作定义你自己的快捷方式或使用预设来匹配 Microsoft Visual Studio Code 中的默认快捷方式。****

有关默认键盘快捷方式，请参阅 [键盘快捷方式](../shortcuts/index.md)。  另请参阅 [自定义 DevTools](./index.md#settings)。


<!-- ====================================================================== -->
## <a name="match-keyboard-shortcuts-from-visual-studio-code"></a>匹配键盘快捷方式Visual Studio Code

若要在开发人员工具中Microsoft Edge等效操作中的键盘快捷方式，Visual Studio Code：

1. [打开 DevTools](../open/index.md)，例如按 `F12`。

1. 打开[设置](./index.md#settings)，例如，选择主工具栏中的齿轮图标，或按 `Shift`+`?`。

1. 选择 **"快捷方式设置** "页。

1. 在右上角的"从预设匹配**** 快捷方式"下拉列表中，选择"Visual Studio Code"**** 而不是"**DevTools (默认) "**。

   :::image type="content" source="../media/match-keyboard-shortcuts-visual-studio-code.msft.png" alt-text="将 DevTools 中的键盘快捷方式与Visual Studio Code。" lightbox="../media/match-keyboard-shortcuts-visual-studio-code.msft.png":::

例如，若要暂停或继续运行脚本Visual Studio Code，请选择 `F5`。  但是，使用 **DevTools (Default **) 预设，若要暂停或继续运行脚本，请按 `F8`。  当你将预设**更改为Visual Studio Code**`F5`时，你现在也在 DevTools 中按下，就像在Visual Studio Code。

### <a name="see-also"></a>另请参阅

* [Microsoft Visual Studio 代码](https://code.visualstudio.com)
* [Visual Studio Code PDF 文件Windows (](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)键盘) 


<!-- ====================================================================== -->
## <a name="edit-the-keyboard-shortcut-for-a-devtools-action"></a>编辑 DevTools 操作键盘快捷方式

1. [打开 DevTools](../open/index.md)，例如按 `F12`。

1. 打开[设置](./index.md#settings)，例如单击主工具栏中的齿轮图标或按 `Shift`+`?`。

1. 选择 **"快捷方式设置** "页。

1. 选择要自定义的操作。  例如，在" **调试器** "部分，选择 **"暂停脚本执行"** 操作。

1. 单击 EditKeyboardShortcut (**** ![EditKeyboardShortcut。](../media/edit-keyboard-shortcut-icon.msft.png)) 图标。

   :::image type="content" source="../media/experiments-custom-keyboard-shortcuts-select-action.msft.png" alt-text="Select the action to customize from the Shortcuts page in 设置." lightbox="../media/experiments-custom-keyboard-shortcuts-select-action.msft.png":::

1. 若要将快捷键绑定到操作，请确保操作旁边的文本框具有焦点，然后使用键盘选择快捷键。

1. 若要将多个快捷方式组合绑定到某个操作，请选择"添加**** 快捷方式"，确保操作旁边的文本框具有焦点，然后使用键盘选择快捷键。

   :::image type="content" source="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png" alt-text="选择要分配给该操作的键。" lightbox="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png":::

1. 若要保存新的键盘快捷方式，请选择选中标记 (![CheckmarkKeyboardShortcut。](../media/checkmark-keyboard-shortcut-icon.msft.png)) 图标。

   :::image type="content" source="../media/experiments-custom-keyboard-shortcuts-save-shortcut.msft.png" alt-text="选择选中标记图标以保存新的键盘快捷方式。" lightbox="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png":::

1. 选择新的键盘快捷方式以在 DevTools 中触发操作。


### <a name="icons-and-buttons"></a>图标和按钮

<!-- keep in same order as screenshot: -->

*  如果 CustomKeyboardShortcut **** ![](../media/custom-keyboard-shortcut-icon.msft.png) 旁边 (自定义键盘快捷方式。) 旁边显示的图标表示已自定义键盘快捷方式。

*  若要在编辑某个动作的****![键盘快捷方式时删除某个动作的键盘快捷方式，请单击"删除 (DeleteKeyboardShortcut](../media/delete-keyboard-shortcut-icon.msft.png)"。) 图标。

*  若要在编辑某个操作键盘快捷方式时为某个操作添加其他键盘快捷方式，请单击"添加快捷方式"链接，或****![单击"自定义键盘快捷方式 **" (** CustomKeyboardShortcut](../media/custom-keyboard-shortcut-icon.msft.png)。) 图标。

*  若要在编辑某个动作的键盘快捷方式时保存已修改或添加的键盘快捷方式，请单击选中 (![CheckmarkKeyboardShortcut。](../media/checkmark-keyboard-shortcut-icon.msft.png)) 图标。

*  若要在编辑某个操作键盘快捷方式时放弃所做的更改，请单击"X" (![XKeyboardShortcut。](../media/discard-changes-keyboard-shortcut-icon.msft.png)) 图标。

*  若要重置所有快捷方式，请单击"还原 **默认快捷方式"** 按钮。

> [!NOTE]
> 如果当前为一个操作分配了键盘快捷方式，则阻止你将其保存为另一个操作。  请改为从上一操作中删除键盘快捷方式，然后将其添加到新操作。
