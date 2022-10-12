---
title: 使用扩展将自定义 UI 添加到 DevTools
description: 了解如何使用或创建 Microsoft Edge 扩展在 DevTools 主工具栏中添加自定义面板。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/30/2022
ms.openlocfilehash: 17a2d68606c1b2192aaf6d03c7413a30d5cb834d
ms.sourcegitcommit: 52f7011a27eaecd2d71da54fb97b42eeabcc05f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2022
ms.locfileid: "12765478"
---
# <a name="add-custom-ui-to-devtools-using-extensions"></a>使用扩展将自定义 UI 添加到 DevTools

除了 Microsoft Edge DevTools 中可用的工具外，还可以通过安装 Microsoft EDge 扩展来添加新工具，或为特定用例生成自己的扩展。

Microsoft Edge 扩展可以在 DevTools 的主工具栏中插入新选项卡。


<!-- ====================================================================== -->
## <a name="install-extensions-in-devtools"></a>在 DevTools 中安装扩展

通过导航到 [Edge 加载项](https://microsoftedge.microsoft.com/addons/)在 Microsoft Edge 中安装扩展。 

这些扩展通常使用新按钮和面板扩展 Microsoft Edge 用户界面，但也可以通过在主工具栏中添加新选项卡来扩展 Microsoft Edge 中的 DevTools。

没有办法知道扩展是否扩展了 DevTools 主工具栏，而无需查看其源代码。 但 Edge 加载项网站有一个**开发人员工具**类别，其中包含通常扩展 DevTools 的扩展。 有关更多详细信息，请参阅 Edge 加载项网站上的[开发人员工具类别](https://microsoftedge.microsoft.com/addons/category/Developer-Tools)。

若要安装 DevTools 扩展，

1. 导航到要在 Edge 加载项网站上安装的扩展。 例如，转到[React开发人员工具](https://microsoftedge.microsoft.com/addons/detail/react-developer-tools/gpphkfbcpidddadnkolkpfckpihlkkil)扩展。

1. 单击 **“获取”** 按钮，然后确认安装对话框：

    ![Edge 加载项网站上的“React开发人员工具”页面](extensions-images/react-add-on-listing.png)

1. 打开新选项卡并转到使用React的页面。 例如，使用 [TodoMVC React示例页](https://todomvc.com/examples/react/#/)。

1. 按下 `F12`打开 DevTools。 主工具栏中显示两个新选项卡： **组件** 和 **探查器**。 如果看不到新选项卡，请使 DevTools 窗口更宽，或者单击 **“更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 。

    ![DevTools，显示 2 个新的React扩展面板](extensions-images/react-extensions-panels.png)

1. 单击**组件**或**探查器**以使用React开发人员工具扩展。


<!-- ====================================================================== -->
## <a name="create-a-devtools-extension"></a>创建 DevTools 扩展

可以创建自己的 DevTools 扩展，在主工具栏中添加新选项卡，并与检查的页面交互。

若要了解如何创建 DevTools 扩展，请导航到 [“创建 DevTools 扩展](../../extensions-chromium/developer-guide/devtools-extension.md)”。
