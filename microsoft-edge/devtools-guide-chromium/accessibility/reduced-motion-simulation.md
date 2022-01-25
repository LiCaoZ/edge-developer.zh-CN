---
title: 减少运动模拟
description: 使用开发人员工具模拟运动减少。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/07/2021
ms.openlocfilehash: d3a6e13ca4c6cf33a60ded39e7f5d29034da6a6c
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318105"
---
# <a name="reduced-motion-simulation"></a>减少运动模拟

Web 产品中的动画可能是一个辅助功能问题。  操作系统通过包括关闭动画的选项来解决此问题，以避免用户混淆和潜在的健康相关问题，例如触发癫痫。

在网页上，您可以使用 [首选的减少](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-reduced-motion) 运动 CSS 媒体查询来检测用户是否喜欢显示任何动画。  然后在测试中包装动画代码，以有条件地运行动画。

```css
@media (prefers-reduced-motion: reduce) {
  /* in case the .header element has an animation, turn it off */
  .header {
    animation: none;
  }
}
```

然后测试代码，如下所示。

若要模拟操作系统的缩减运动设置，而无需更改操作系统设置：

1.  在 `Control` + `Shift` + `P` Windows/Linux 或 macOS 上键入 `Command` + `Shift` + `P` 以打开**命令菜单**。
    
    > [!div class="mx-imgBorder"]
    > ![打开命令菜单](../media/reduced-motion-open-command-menu.png)

1.  键入 `reduced` ，以打开和关闭模拟。  选择 **模拟 CSS prefers-reduced-motion** 选项并按 `Enter` 。

    > [!div class="mx-imgBorder"]
    > !["命令"菜单中的"模拟 CSS 首选减少运动"选项](../media/reduced-motion-command-menu-entry.png)

1.  刷新网页并检查动画是否运行。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [验证页面是否可用，](test-reduced-ui-motion.md) 关闭 UI 动画 - 使用演示页面的演练，并给出说明。
