---
description: 自定义键盘快捷方式，包括匹配来自Visual Studio Code。
title: 在 DevTools 中自定义键盘快捷方式
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/10/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， 开发工具， 自定义， 快捷方式， 键盘， visual studio 代码
ms.openlocfilehash: d2b02531c8608ca4cee787c75f9e7f0a268918546030848b20ab2050c3411c7e
ms.sourcegitcommit: 841e41de1a32501ece862399fa56170c022127c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2021
ms.locfileid: "11799660"
---
# <a name="customize-keyboard-shortcuts-in-devtools"></a>在 DevTools 中自定义键盘快捷方式  

在******设置**的"快捷方式"页中，可以查看 Microsoft Edge DevTools 的定义快捷方式、为特定操作定义你自己的快捷方式或使用预设来匹配 Microsoft Visual Studio Code 中的默认快捷方式。

有关列出所有默认快捷方式设置的文章，请参阅Microsoft Edge[开发人员工具键盘快捷方式][DevToolsShortcuts]。  另请参阅 [自定义 DevTools][DevToolsCustomizeSettings]。


## <a name="match-keyboard-shortcuts-from-visual-studio-code"></a>匹配键盘快捷方式Visual Studio Code

若要将开发人员工具中的键盘快捷方式Microsoft Edge开发人员工具中的等效操作Visual Studio Code：

1.  [打开 DevTools，][DevtoolsOpenMain]例如通过选择 `F12` 。
1.  打开[设置，][DevToolsCustomizeSettings]例如，选择主工具栏中的齿轮图标，或选择 `Shift` + `?` 。  
1.  选择 **"快捷方式设置** "页。
1.  在右上角的"从预设**匹配**快捷方式"下拉列表中，选择"Visual Studio Code"**** 而不是 **"DevTools (默认) "。 **
    
    :::image type="complex" source="../media/match-keyboard-shortcuts-visual-studio-code.msft.png" alt-text="将 DevTools 中的键盘快捷方式与Visual Studio Code" lightbox="../media/match-keyboard-shortcuts-visual-studio-code.msft.png":::
       将 DevTools 中的键盘快捷方式与Visual Studio Code  
    :::image-end:::  
    
例如，若要暂停或继续运行脚本Visual Studio Code，请选择 `F5` 。  但是，使用 **"DevTools ** (默认) 预设，若要暂停或继续运行脚本，请选择 `F8` 。  当你将预设更改为**Visual Studio Code**时，你现在还可以在 DevTools 中选择，就像在 Visual Studio Code `F5` 中一样。

### <a name="see-also"></a>另请参阅

* [Microsoft Visual Studio代码][VisualStudioCode]
* [Visual Studio Code PDF 文件Windows (][VisualStudioCodeShortcutsKeyboardWindows]键盘) 


## <a name="edit-the-keyboard-shortcut-for-a-devtools-action"></a>编辑 DevTools 操作键盘快捷方式

1.  [打开 DevTools，][DevtoolsOpenMain]例如通过选择 `F12` 。
1.  打开[设置，][DevToolsCustomizeSettings]例如，选择主工具栏中的齿轮图标，或选择 `Shift` + `?` 。  
1.  选择 **"快捷方式设置** "页。
1.  选择要自定义的操作。  例如，在" **调试器** "部分，选择 **"暂停脚本执行"** 操作。  
1.  选择 **Edit** \ (![ EditKeyboardShortcut ](../media/edit-keyboard-shortcut-icon.msft.png) \) 图标。  
    
    :::image type="complex" source="../media/experiments-custom-keyboard-shortcuts-select-action.msft.png" alt-text="Select the action to customize from the Shortcuts page in 设置" lightbox="../media/experiments-custom-keyboard-shortcuts-select-action.msft.png":::
       Select the action to customize from the **Shortcuts** page in**设置**
    :::image-end:::  
    
1.  若要将快捷键绑定到操作，请确保操作旁边的文本框具有焦点，然后使用键盘选择快捷键。  
1.  若要将多个快捷方式组合绑定到某个操作，请选择"添加**** 快捷方式"，确保操作旁边的文本框具有焦点，然后使用键盘选择快捷键。  
    
    :::image type="complex" source="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png" alt-text="选择要分配给该操作的密钥" lightbox="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png":::
       选择要分配给该操作的密钥  
    :::image-end:::  
    
1.  若要保存新的键盘快捷方式，请选择选中标记 \ (![CheckmarkKeyboardShortcut](../media/checkmark-keyboard-shortcut-icon.msft.png)）图标。
    
    :::image type="complex" source="../media/experiments-custom-keyboard-shortcuts-save-shortcut.msft.png" alt-text="选择选中标记图标以保存新的键盘快捷方式" lightbox="../media/experiments-custom-keyboard-shortcuts-enter-key.msft.png":::
       选择选中标记图标以保存新的键盘快捷方式  
    :::image-end:::  
    
1.  选择新的键盘快捷方式以在 DevTools 中触发操作。  
    
在 **"快捷方式"** 页上 **，自定义键盘** 快捷方式 \ (![ CustomKeyboardShortcut ](../media/custom-keyboard-shortcut-icon.msft.png) \) 图标显示已自定义的键盘快捷方式。  若要重置所有快捷方式，请选择"**还原默认快捷方式"。**  

编辑某个动作的键盘快捷方式时，若要放弃所做的更改，请选择 X \ (![ XKeyboardShortcut ](../media/discard-changes-keyboard-shortcut-icon.msft.png) \) 图标。  若要删除特定操作快捷方式，请选择 Delete **快捷方式** \ (![ DeleteKeyboardShortcut ](../media/delete-keyboard-shortcut-icon.msft.png) \) 图标。  

> [!NOTE]
> 如果当前为一个操作分配了键盘快捷方式，则阻止将其保存为另一个操作。  请改为从上一操作中删除键盘快捷方式，然后将其添加到新操作。  

<!-- links -->  
[DevToolsCustomizeSettings]: ./index.md#settings "设置 - 自定义 Microsoft Edge DevTools | Microsoft Docs"  
[DevtoolsOpenMain]: ../open/index.md "打开 Microsoft Edge DevTools | Microsoft Docs"  
[DevToolsShortcuts]: ../shortcuts/index.md "Microsoft Edge DevTools 键盘快捷方式|Microsoft Docs"  
<!-- external links -->
[VisualStudioCode]: https://code.visualstudio.com "Microsoft Visual Studio代码"  
[VisualStudioCodeShortcutsKeyboardWindows]: https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf "Visual Studio Code键盘快捷方式Windows |Microsoft Visual Studio代码"  
