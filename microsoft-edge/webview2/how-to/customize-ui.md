---
title: 在 WebView2 应用中自定义 UI
description: 自定义 WebView2 应用中的 UI。  将自定义右键单击菜单 (WebView2) 上下文菜单，或者添加和删除默认 WebView2 上下文菜单中的项。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/08/2022
ms.openlocfilehash: 54ccb4efe0e072031849ad81b0f5a1ee4272dc55
ms.sourcegitcommit: 2631c3835d23d9adaa28c19198319588baf9d8c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2022
ms.locfileid: "12439782"
---
# <a name="customizing-the-ui-in-webview2-apps"></a>在 WebView2 应用中自定义 UI

<!-- presently omitted from TOC -->


<!-- ====================================================================== -->
## <a name="customize-the-context-menus-of-your-webview2-app"></a>自定义 WebView2 应用的上下文菜单

使用 **ContextMenuRequested** API 自定义 WebView2 (右键单击菜单) 菜单。  使用此 API，你可以：

*  添加和删除默认 WebView2 上下文菜单中的项。

*  使用从 WebView2 控件传递到应用的数据创建自己的上下文菜单。

请参阅 [自定义 WebView2 中的上下文菜单](context-menus.md)。
