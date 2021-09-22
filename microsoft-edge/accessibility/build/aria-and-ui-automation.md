---
ms.assetid: ffd1bc60-2ef1-4f11-8156-b63544cede77
description: 了解如何Microsoft Edge ARIA 信息，然后向随后可以使用 Microsoft UI 自动化 API 的辅助技术公开该信息。
title: ARIA 和 UI 自动化Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/05/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: 辅助功能， 开发人员辅助功能， 可访问的网站， 边缘， Web 开发， ARIA， 开发人员， UIA， UI 自动化
ms.custom: seodec18
ms.openlocfilehash: 1937806035d8904986b88d06be1940f669e1780a
ms.sourcegitcommit: d2098f7f400614e2ba8eee8317abaa2e043c0594
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2021
ms.locfileid: "12033121"
---
# <a name="aria-and-ui-automation-in-microsoft-edge"></a>ARIA 和 UI 自动化Microsoft Edge

W3C 将可访问的富 Internet 应用程序 (ARIA) ARIA 定义为使动态 Web 内容和自定义 UI 可供访问的语法。  Microsoft Edge识别 ARIA 角色、状态和属性信息，并公开给辅助技术，辅助技术又可以使用[Microsoft UI 自动化 API](https://blogs.msdn.microsoft.com/winuiautomation/)检索信息。 

访问[HTML5Accessibility，](https://html5accessibility.com)了解哪些新 HTML5 功能可供 Microsoft Edge。

该Microsoft Edge引擎构建网页的可访问投影，符合以下 W3C 规范：

1. [HTML 辅助功能 API 映射](https://w3.org/TR/html-aam-1.0/)规范定义 HTML 元素和属性如何映射到 ARIA 和 UI 自动化对象。
   * [工作草稿](https://w3.org/TR/html-aam-1.0/) - 规范的稳定版本。
   * [编辑器的草稿](https://w3c.github.io/html-aam/) - 正在进行中。  请注意，尽管此规范具有最新的更改，但这些更改可能尚未Microsoft Edge可用。

2. 核心 [辅助功能 API 映射](https://w3.org/TR/core-aam-1.1/) 规范定义了生成辅助功能树以及将 ARIA 元素和属性映射到 UI 自动化对象的一般原则。
   * [工作草稿](https://w3.org/TR/core-aam-1.1/) - 规范的稳定版本。
   * [编辑器的草稿](https://w3c.github.io/core-aam/) - 正在进行中。  请注意，尽管此规范具有最新的更改，但这些更改可能尚未Microsoft Edge可用。  

3. [辅助名称和](https://w3.org/TR/accname-aam-1.1/)说明：计算和 API 映射规范定义如何计算可访问对象的名称和说明（给定可用于辅助元素的 HTML 和 ARIA 元素和属性值）。
   * [工作草稿](https://w3.org/TR/accname-aam-1.1/) - 规范的稳定版本。
   * [编辑器的草稿](https://w3c.github.io/accname/) - 正在进行中。  请注意，尽管此规范具有最新的更改，但这些更改可能尚未Microsoft Edge可用。   


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [构建更易于访问的 Web 平台](https://blogs.windows.com/msedgedev/2016/04/20/building-a-more-accessible-web-platform/)- 有关网站中的辅助功能体系结构的Microsoft Edge。

* 使用 HTML5 和[UIA](https://blogs.windows.com/msedgedev/2016/05/12/accessible-ux-with-html5-and-uia/)构建更易于访问的用户体验 - 标记如何定义使用屏幕阅读器等辅助技术进行导航的体验的示例，以及体系结构如何改善最终用户体验的示例。
