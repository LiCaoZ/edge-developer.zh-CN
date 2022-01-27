---
title: 强制打印预览模式
description: 打开"呈现"工具，然后选择"模拟 CSS 媒体>打印"。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
ms.openlocfilehash: fb15707cfd330c08e0d1e1a6f32b2e14682e146d
ms.sourcegitcommit: 9caa4aac0a339a76e7f1e0f0f5d6d85a2492ea8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2022
ms.locfileid: "12325226"
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
# <a name="force-print-preview-mode"></a>强制打印预览模式

打印 [媒体查询](https://developer.mozilla.org/docs/Web/CSS/Media_Queries/Using_media_queries) 控制页面在打印时的外观。  若要强制页面进入打印预览模式：

1.  按 `Control` + `Shift` + `P` (Windows、Linux) 或 `Command` + `Shift` + `P` (macOS) 打开命令**菜单**。

    > [!div class="mx-imgBorder"]
    > ![打开命令菜单。](../media/print-preview-open-command-menu.png)

1.  键入 `rendering` ，选择 **"显示呈现"** 选项，然后按 `Enter` 。
1.  " **呈现"** 面板在"箱" **中打开**。
1.  在 **"模拟 CSS 媒体类型"下，** 选择"**打印"。**

    > [!div class="mx-imgBorder"]
    > ![已选择打印 CSS 媒体类型的呈现面板。](../media/print-preview-css-media-type.png)

可以在此处显示和更改 CSS，就像任何其他网页一样。  请参阅[开始查看和更改 CSS。](./index.md)


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [使用性能功能参考中的呈现工具](../evaluate-performance/reference.md#analyze-rendering-performance-with-the-rendering-tool)_分析呈现性能_

呈现工具还用于以下内容：

* [检查深色主题和浅主题的对比度问题](../accessibility/test-dark-mode.md)
* [验证页面是否对色盲者可用](../accessibility/test-color-blindness.md)
* [验证页面是否在视觉模糊时可用](../accessibility/test-blurred-vision.md)
* [验证页面是否在关闭 UI 动画时可用](../accessibility/test-reduced-ui-motion.md)
* [模仿视觉缺陷](../accessibility/emulate-vision-deficiencies.md)
* [模拟呈现页面中的深色或浅色方案](../accessibility/preferred-color-scheme-simulation.md)
* [模拟运动减少](../accessibility/reduced-motion-simulation.md)


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/css/print-preview)，由 [Kayce Basques](https://developers.google.com/web/resources/contributors#kayce-basques)\（Chrome DevTools 和 Lighthouse 的技术作家）撰写。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
