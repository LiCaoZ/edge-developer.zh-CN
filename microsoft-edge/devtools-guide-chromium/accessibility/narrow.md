---
description: 作为辅助功能测试的一部分，验证网页布局在较窄时是否可用。
title: 验证网页布局在较窄时是否可用
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/19/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 5fa83746b625c17e4be392115e003757cfbcf3ad
ms.sourcegitcommit: 9920f4826b1d16ee0e4842703844437a6d22e816
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2021
ms.locfileid: "12170701"
---
# <a name="verify-that-the-webpage-layout-is-usable-when-narrow"></a>验证网页布局在较窄时是否可用

辅助功能的一个重要部分是确保 Web 产品在较窄的视口上良好工作。 许多用户需要缩放页面才能使用它，这意味着没有太多空间。 当空间不足时，多列布局应转换为单列布局，内容按可理解的顺序放置。 这意味着将最重要的内容放在页面顶部，将其他内容放置在页面的更下一层。

通过缩小浏览器窗口范围，使用箭头键滚动页面，可以看到演示页面的顶部导航栏具有一些辅助功能问题。  顶部导航栏与 **"** 搜索"窗体重叠，如上图所示，需要修复该问题。

可以通过调整浏览器窗口的大小来模拟较窄的视区，但测试设计响应性更好的方法就是使用 **设备仿真** 工具。  以下是设备仿真 **工具的一** 些功能，可帮助你查找任何网站的辅助功能问题：

*  无需调整浏览器窗口的大小，即可调整页面大小并测试 CSS [媒体](../device-mode/index.md#show-media-queries) 查询是否触发布局更改。
*  检查是否使用鼠标的依赖项。 默认情况下，设备仿真假定为触摸设备。 这意味着产品依赖于悬停交互的任何功能将不起作用。
*  通过模拟不同的设备、缩放级别和像素比率执行视觉测试。
*  测试产品在不可靠连接或用户脱机时的行为方式。  在低速连接上向用户显示最重要的交互也是辅助功能注意事项。

若要了解有关设备仿真**工具**的信息，请参阅在[DevTools](../device-mode/index.md)中模拟Microsoft Edge移动设备。