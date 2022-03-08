---
title: 使用 Tab 和 Enter 键检查键盘支持
description: 使用 Tab 键和 Enter 键检查键盘支持。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: 1014679309da87666d12a338ea72eebc2c109b46
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430946"
---
# <a name="check-for-keyboard-support-by-using-the-tab-and-enter-keys"></a>使用 Tab 和 Enter 键检查键盘支持

并非所有用户都有指针或触摸设备，并且并非所有用户都可以查看我们创建的 Web 项目。  这就是为什么用户界面至少与键盘一起工作非常重要的原因。  确保可以使用键 `Tab` 将焦点移到网页上的每个表单控件，并确保可以使用 `Enter` 该键提交表单。

可以通过多种方式测试键盘用户的网页可用性：
*  通过使用键盘，尤其是 `Tab`、`Tab``Shift`+ 和 `Enter` 键。  本文中介绍了此方法。
*  使用 Inspect 工具检查单个元素的 **键盘** 支持。  检查工具的信息覆盖包括一个 **辅助功能** 部分，其中包括 **一个键盘可聚焦** 的行。
*  检查 **问题报告的** 辅助功能 **部分** ，了解键盘支持问题。

若要使用键盘而不是鼠标检查演示页面的辅助功能问题，请运行以下命令：

1. 打开 [新窗口或选项卡中的](https://microsoftedge.github.io/Demos/devtools-a11y-testing/) 辅助功能测试演示网页。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

1. 使用键盘导航演示文档，使用 `Tab` 和 `Shift`+`Tab` 键从元素跳到另一个元素。  在演示网页上，该 `Tab` 密钥首先将焦点移到部分中的搜索 `header` 表单。

1. 按 `Tab` 将焦点放在按钮上，然后按 `Enter` 以单击聚焦按钮。  例如，在演示页面中，按 `Tab` 将焦点放在 **"** 搜索"字段上，然后按 `Enter` 以提交搜索。  此方法将产生与选择"开始" **按钮相同的结果** 。  选择 `Enter` 发送搜索 **表单** 可以正常工作。

1. 再次 `Tab` 按。  您重点关注的下一个元素是网页部分的第一个 **"**`content`更多"链接，如大纲所指示。

   :::image type="content" source="../media/a11y-testing-keyboard-focus-on-element.msft.png" alt-text="使用键盘和&quot;Tab&quot;键导航文档。 焦点显示在文档中的链接上。" lightbox="../media/a11y-testing-keyboard-focus-on-element.msft.png":::

1. 按 `Tab` 多次，直到传递最后一个 **"更多"** 链接。  页面向上滚动，你似乎位于页面的某个元素上，但无法判断它是哪个元素。

1. 请注意左下角的 URL。  如果你查看屏幕左下角 (或者如果你使用屏幕阅读器) ，你意识到你位于带蓝色链接的边栏导航菜单上，因为浏览器显示"猫"链接指向 () 的 URL。**** `#cats`

   :::image type="content" source="../media/a11y-testing-lack-of-focus-style.msft.png" alt-text="缺少焦点样式使无法知道您当前在文档中的什么位置。 唯一的提示是在屏幕左下角显示链接目标。" lightbox="../media/a11y-testing-lack-of-focus-style.msft.png":::

1. 再次 `Tab` 按 ，以到达"捐赠"窗体中的条目字段。  但是，无法通过选择 来到达文本框上方的按钮 `Tab`。 你不能使用键盘将焦点放在 **50**、 **100** 或 **200** 按钮上，然后选择它们。  此外，选择 `Enter` 时不会提交该捐赠表单。

   :::image type="content" source="../media/a11y-testing-form-field-with-outline.msft.png" alt-text="在资金表单中，唯一一个可通过键盘访问的元素是文本输入字段。" lightbox="../media/a11y-testing-form-field-with-outline.msft.png":::

1. 再次`Tab`选择会将焦点放在页面的顶部导航栏上，并包含"主页"、"******采用**动物"、**"** 花形"、"**作业**"和"关于**我们"的菜单按钮**。  按 `Tab` 或 `Shift`+`Tab` 将焦点放在菜单按钮上，如焦点轮廓所指示。  然后按 `Enter` 以访问网页的该部分。

   :::image type="content" source="../media/a11y-testing-menu-with-outline.msft.png" alt-text="主菜单具有突出显示和焦点轮廓，因此是键盘可访问的。" lightbox="../media/a11y-testing-menu-with-outline.msft.png":::

基于上述演练，我们发现需要修复的以下问题。

*  使用键盘时，边栏导航菜单的蓝色链接不会直观地指示哪个链接具有焦点。  请参阅 [分析边栏菜单中缺少键盘焦点的指示](test-analyze-no-focus-indicator.md)。

*  在"资金"表单中，金额按钮和 **"四** 分百"按钮不能与键盘一起使用。  请参阅 [分析表单中缺少键盘支持](test-analyze-no-keyboard-support.md)。

*  键盘通过页面各部分访问的顺序不正确。  在到达 **边栏导航** 菜单之前，可以浏览文档中的所有"更多"链接。  当键将 `Tab` 焦点放在边栏导航菜单上时，你已遍历所有页面内容。 边栏导航菜单旨在提供对页面内容的轻松访问。

   若要详细了解如何解决此问题，请参阅使用源订单查看器测试 [键盘支持](test-tab-key-source-order-viewer.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 DevTools 的辅助功能测试概述](accessibility-testing-in-devtools.md)
