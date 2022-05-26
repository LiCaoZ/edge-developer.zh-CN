---
title: 实验性功能和源试用版
description: 如何在Microsoft Edge中测试试验性PWA功能，并在源试验中注册站点，以便与用户一起在生产环境中使用这些功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 09/15/2021
ms.openlocfilehash: 9b0a4b59fbc1efa72e20c787390091ac8d361280
ms.sourcegitcommit: 8aee95757de12c62f4a74d37649ad5979f9e0ba9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2022
ms.locfileid: "12550826"
---
# <a name="experimental-features-and-origin-trials"></a>实验性功能和源试用版

Microsoft Edge中的一些PWA功能仍是实验性的。 可通过两种方式使用实验性功能：

*   通过在Microsoft Edge中启用相应的标志。
*   通过在源试用版中注册站点，以便与用户一起测试生产中的功能。


<!-- ====================================================================== -->
## <a name="toggle-experimental-features"></a>切换实验功能

打开或关闭实验性功能：

1.  打开 Microsoft Edge。
1.  转到 `edge://flags`。
1.  导航到相关试验。
1.  选择实验说明旁边的下拉菜单，然后选择 **“启用** 以打开功能”或“ **禁用** ”将其关闭。

    ![选择“启用”以启用试验。](../media/turn-on-experimental-flag.png)


<!-- ====================================================================== -->
## <a name="enroll-your-site-in-an-origin-trial"></a>在源试用版中注册站点

Microsoft Edge有时使用源试验来测试特定域或网站的功能。 你可能希望使用网站的源试用版来应用特定功能。 如果你是网站所有者，则可以注册源试用版。 源试用版为访问网站的Microsoft Edge用户的百分比提供功能。

有关源试用版的详细信息，请参阅[Microsoft Edge源试用版开发人员控制台](https://developer.microsoft.com/microsoft-edge/origin-trials)。


<!-- ====================================================================== -->
## <a name="features-that-are-available-to-test"></a>可用于测试的功能

以下列表介绍可用于在Microsoft Edge上测试和验证的实验性 Web 应用功能。 若要启用它们，请转到 [切换实验功能](#toggle-experimental-features)。

| 功能 | 平台 |
|:--- |:--- |
| [URI 协议处理](handle-protocols.md) | Windows和 Linux |
| [URL 链接处理](handle-urls.md) | Windows |
| [桌面应用的窗口控件覆盖](window-controls-overlay.md) | 全部 |
| [文件处理](handle-files.md) | 所有桌面 |

<!-- Links -->
