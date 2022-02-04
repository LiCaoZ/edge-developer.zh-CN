---
title: 旁加载扩展
description: 如何在浏览器中旁加载扩展来测试扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/24/2020
---
# <a name="sideload-an-extension"></a>旁加载扩展

在开发期间，可以使用Microsoft Edge浏览器安全地运行和调试扩展。  通过在你的浏览器中本地旁加载扩展，你可以运行和测试扩展。  本文介绍如何将扩展旁加载到Microsoft Edge。

旁加载扩展：

1. 通过选择 `edge://extensions` 浏览器顶部的三个点，然后选择"扩展"打开 **页面**。

   :::image type="content" source="./media/part1-threedots.png" alt-text="打开 edge://extensions 页。":::

1. 在扩展管理页面上的 `edge://extensions`**，使用页面**左下角的开关打开开发人员模式。

   :::image type="content" source="./media/part1-developermode-toggle.png" alt-text="打开开发人员模式。":::

1. 首次安装扩展时，选择" **加载已解压缩"**。  系统将提示你输入包含扩展源文件的目录。  你的扩展安装在浏览器中，类似于从应用商店安装的扩展。

   :::image type="content" source="./media/part1-installed-extension.png" alt-text="已安装的扩展页，显示旁加载的扩展。":::

在开发过程中，可能还需要执行以下操作：

* 更新扩展。  转到 ， `edge://extensions`然后选择" **重新加载** "以更新扩展。

* 从浏览器中删除扩展。  转到 ， `edge://extensions`然后在扩展 `Remove` 上选择 。
