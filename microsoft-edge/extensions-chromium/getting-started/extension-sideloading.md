---
description: 在浏览器中旁加载扩展来测试扩展
title: 旁加载扩展
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/24/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: edge-chromium， Web 开发， html， css， javascript， 开发人员， 扩展
ms.openlocfilehash: 7070878b9608e6d239179078390f2315e0b289a1
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976635"
---
# <a name="sideload-an-extension"></a>旁加载扩展

在开发期间，可以使用 Microsoft Edge \ (Chromium\) 浏览器安全运行和调试扩展。 通过在你的浏览器中本地旁加载扩展，你可以运行和测试扩展。 本文介绍如何将扩展旁加载到Microsoft Edge。

若要旁加载扩展，请按照以下步骤操作。

1.  通过 `edge://extensions` 选择浏览器顶部的三个点，然后选择扩展打开 **页面**。

       :::image type="complex" source="./media/part1-threedots.png" alt-text="打开&quot;edge://extensions 页":::
          打开"edge://extensions 页 :::image-end:::

1.  在扩展管理页面上的 `edge://extensions` ，使用页面**** 左下角的开关打开开发人员模式。

       :::image type="complex" source="./media/part1-developermode-toggle.png" alt-text="打开开发人员模式":::
          打开开发人员模式 :::image-end:::

1.  首次安装扩展时，选择"**加载未打包"。**  系统将提示你输入包含扩展源文件的目录。  你的扩展安装在浏览器中，类似于从应用商店安装的扩展。  

       :::image type="complex" source="./media/part1-installed-extension.png" alt-text="显示旁加载扩展的已安装扩展页":::
          显示旁加载扩展的已安装扩展页 :::image-end:::

在开发过程中，可能还需要执行以下任务。
* 更新扩展。 导航到 `edge://extensions` ，然后选择" **重新加载** "以更新扩展。  
* 从浏览器中删除扩展。 导航到 `edge://extensions` ，然后在 `Remove` 扩展上选择 。