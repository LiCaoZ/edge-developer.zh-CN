---
title: 筛选控制台消息
description: 使用 DevTools 控制台的筛选器选项来减少过多控制台日志消息的干扰，以更好地查看要查找的日志消息的类型。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
ms.openlocfilehash: 8c0421ca11f3eda6abafe0be1a4e01df81327bdd
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431317"
---
# <a name="filter-console-messages"></a>筛选控制台消息

使用 DevTools **控制台** 的筛选器选项来减少过多控制台日志消息的干扰，以更好地查看要查找的日志消息的类型。

当您转到各种网页时，您可能会发现控制台中会大量显示**** 各种信息。  通常信息不相关，例如有关其他开发人员记录的页面的信息。  或者，你可能会看到有关当前网站性能的违反和警告的记录信息，你无法更改这些信息。  

可以通过多种方式筛选控制台日志消息：
*  按日志级别筛选。
*  按文本筛选。
*  按正则表达式筛选。
*  按邮件源筛选。


<!-- ====================================================================== -->
## <a name="filter-by-log-level"></a>按记录级别筛选

对象的每个方法 `console` 都有一个附加到它的严重级别。  严重性级别为 、`Verbose``Info`、`Warning`或 `Error`。  显示 API 文档中的严重性 [级别](api.md)。  例如， `console.log()` 是 `Info`-level 邮件，但 `console.error()` 是 `Error`-level 邮件。

若要在控制台中 **筛选消息**，请使用" **日志级别"** 下拉菜单。  你可以切换每个级别的状态。  若要关闭每个级别，请删除每个级别旁边的选中标记。

:::image type="content" source="../media/console-filter-dropdown.msft.png" alt-text="下拉菜单使用日志级别筛选控制台消息。" lightbox="../media/console-filter-dropdown.msft.png":::

由于未应用筛选器，下图显示数十条消息。  接下来，减少和管理邮件数量。

:::image type="content" source="../media/console-filter-displays-all.msft.png" alt-text="没有筛选器集意味着可以显示许多控制台消息。" lightbox="../media/console-filter-displays-all.msft.png":::

若要隐藏所有警告级别的消息以在噪音上向下删除，请单击"日志级别****"下拉列表，然后清除`Warnings`该级别。

:::image type="content" source="../media/console-filter-hide-warning.msft.png" alt-text="隐藏控制台中所有警告级别的消息以筛选大部分噪音。" lightbox="../media/console-filter-hide-warning.msft.png":::


<!-- ====================================================================== -->
## <a name="filter-by-text"></a>按文本筛选

若要查看更多详细信息，若要使用文本筛选邮件，在"筛选器"文本框 **中键入** 字符串。  例如，在框中 **键入 block** ，以仅显示有关浏览器阻止资源加载的消息。

:::image type="content" source="../media/console-filter-text.msft.png" alt-text="显示包含单词&quot;block&quot;的邮件。" lightbox="../media/console-filter-text.msft.png":::


<!-- ====================================================================== -->
## <a name="filter-by-regular-expression"></a>按正则表达式筛选

[正则表达式是](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions) 筛选邮件的一种强大方法。  例如，在"`/^Tracking/`**筛选器"文本框中**键入 ，以仅显示以术语 开始的邮件`Tracking`。  如果你不熟悉正则表达式，那么 RegExr.com 正则表达式是一[](https://regexr.com)个很好的资源。

:::image type="content" source="../media/console-filter-regex.msft.png" alt-text="使用&quot;筛选器&quot;文本框中的正则表达式显示以单词&quot;filter&quot;开始的邮件。" lightbox="../media/console-filter-regex.msft.png":::


<!-- ====================================================================== -->
## <a name="filter-by-message-source"></a>按邮件源筛选

可以使用控制台的边栏定义要显示的消息类型以及每个消息**的来源。******

1. 单击" **显示控制台边栏"** 按钮：

   :::image type="content" source="../media/console-filter-sidebar-icon.msft.png" alt-text="若要打开边栏，请单击&quot;显示控制台边栏&quot;图标。" lightbox="../media/console-filter-sidebar-icon.msft.png":::

   当 **边栏** 打开时，可以显示消息的个数以及每个消息的来源。  选项包括 、`All messages``User Messages`、、`Errors``Warnings`、 `Info`和 `Verbose`。

   :::image type="content" source="../media/console-filter-sidebar-open.msft.png" alt-text="控制台边栏显示邮件来源的不同源。" lightbox="../media/console-filter-sidebar-open.msft.png":::

1. 选择任意选项以仅显示该类型的消息。  例如，若要显示用户消息，请单击"用户消息"选项来显示更少的噪音。

   :::image type="content" source="../media/console-filter-select-user-messages.msft.png" alt-text="使用边栏中的筛选器在控制台中仅显示用户消息。" lightbox="../media/console-filter-select-user-messages.msft.png":::

1. 若要筛选更多并展开邮件类别，请单击邮件类别旁边的三角形图标。

   :::image type="content" source="../media/console-filter-sidebar-open-arrow.msft.png" alt-text="单击箭头图标以展开邮件类别。" lightbox="../media/console-filter-sidebar-open-arrow.msft.png":::

1. 显示并列出各个源。  选择一个源，以仅显示源自该源的邮件：

   :::image type="content" source="../media/console-filter-user-message-by-source.msft.png" alt-text="选择任何显示的选项，按邮件类型和来源筛选邮件。" lightbox="../media/console-filter-user-message-by-source.msft.png":::
