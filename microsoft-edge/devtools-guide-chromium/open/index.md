---
title: 打开开发工具
description: 在 DevTools 中打开Microsoft Edge所有方法。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 07/01/2021
ms.openlocfilehash: 1865a4725280314bfb839397a3ef1128aee0bb6a
ms.sourcegitcommit: 9caa4aac0a339a76e7f1e0f0f5d6d85a2492ea8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "12325555"
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
   limitations under the License. -->
# <a name="open-devtools"></a>打开开发工具

有几种方法可以打开 Microsoft Edge Tools，以快速访问 DevTools UI 的不同部分：

*   使用 Microsoft Edge UI。
    *  在Microsoft Edge"中，**选择"设置""更多 () >"** `...` **工具**  >   **开发人员工具"。**

*   使用键盘。
    *   按 `F12` 或 `Control` + `Shift` + `I` (Windows、Linux) 或 `Command` + `Option` + `I` (macOS) 。

另请参阅 [键盘快捷方式](../shortcuts/index.md)。

:::image type="content" source="../media/bing-customize-more-tools-developer-tools-transparent.msft.png" alt-text="从主菜单打开 Microsoft Edge DevTools。" lightbox="../media/bing-customize-more-tools-developer-tools-transparent.msft.png":::


<!-- ====================================================================== -->
## <a name="open-the-elements-panel-to-inspect-the-dom-or-css"></a>打开"元素"面板以检查 DOM 或 CSS

在浏览器中查看呈现的网页时，若要检查文档对象模型 [ (](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) DOM) 节点的样式或属性，请执行下列任一操作：
*   右键单击呈现的网页中的 元素，然后选择"检查 **"。**
*   按`Control`+`Shift`+`C`（Windows、Linux）或 `Command`+`Option`+`C` （macOS）。  请参阅 [键盘快捷方式](../shortcuts/index.md)。

请参阅 [适用于初学者的 DevTools：CSS 入门](../beginners/css.md)。

<!-- :::image type="content" source="../media/bing-right-click-inspect.msft.png" alt-text="The Inspect option." lightbox="../media/bing-right-click-inspect.msft.png"::: -->


<!-- ====================================================================== -->
## <a name="open-the-console-panel"></a>打开控制台面板

若要打开控制台[面板](../console/index.md)以查看记录的消息或运行 JavaScript，请按 `Control` + `Shift` + `J` (Windows、Linux) 或 `Command` + `Option` + `J` (macOS) 。  请参阅 [键盘快捷方式](../shortcuts/index.md)。


<!-- ====================================================================== -->
## <a name="open-the-previous-panel"></a>打开上一个面板

若要跳转到之前打开的面板，请按 `Control` + `Shift` + `I` (Windows、Linux) 或 (`Command` + `Option` + `I` macOS) 。  请参阅 [键盘快捷方式](../shortcuts/index.md)。


<!-- ====================================================================== -->
## <a name="auto-open-devtools-on-every-new-tab"></a>自动打开每个新选项卡上的 DevTools

若要自动打开每个新选项卡上的 DevTools，Microsoft Edge命令行中打开"开发工具"并传递 `--auto-open-devtools-for-tabs` 标志。

### [<a name="cmd-windows"></a>CMD (Windows) ](#tab/cmd-Windows/)

```cmd
start msedge --auto-open-devtools-for-tabs
```

### [<a name="powershell-windows"></a>PowerShell (Windows) ](#tab/powershell-Windows/)

```powershell
Start-Process -FilePath "msedge" -ArgumentList "--auto-open-devtools-for-tabs"
```

### [<a name="bash-macos"></a>bash (macOS) ](#tab/bash-macos/)

```bash
/Applications/Microsoft\ Edge\ Beta.app/Contents/MacOS/Microsoft\ Edge\ Beta --auto-open-devtools-for-tabs
```

### [<a name="bash-linux"></a>Bash (Linux) ](#tab/bash-linux/)

```bash
microsoft-edge-dev --auto-open-devtools-for-tabs
```

* * *


<!-- ====================================================================== -->
## <a name="toggle-the-f12-keyboard-shortcut-on-or-off"></a>打开或关闭 F12 键盘快捷方式

若要更改 `F12` 打开 DevTools 的键盘快捷方式设置，请完成以下操作：

1.  转到 `edge://settings/system` 。
1.  In `Developer Tools` ， choose Open the **DevTools when the F12 key is pressed** to toggle the setting to off or on. 将设置切换为关闭以停止 `F12` 键盘快捷方式打开 DevTools。
1.  将开关设置为关闭后，验证 `F12` 是否不再打开 DevTools。

    > [!NOTE]
    > 在关闭"按 F12 键时打开 **DevTools"** 后，再次打开"DevTools"。  例如，按 `Ctrl` + `Shift` + `I` 或右键单击网页，然后选择"检查 **"。**


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/open)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
