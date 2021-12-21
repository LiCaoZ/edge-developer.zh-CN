---
title: PWA 的用户体验
description: A overview of the user experience of PWA on Microsoft Edge and Windows.
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: 渐进式 Web 应用， PWA， edge， Windows， 桌面， 安装， 集成， microsoft store， ux
ms.date: 09/15/2021
ms.openlocfilehash: a69ee70c9b7f8d2d49a602287610b458a07f8dd8
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284110"
---
# <a name="the-user-experience-of-pwas"></a>PWA 的用户体验

在Windows中， (PA) 的渐进 Web 应用与其他应用一样。  任何运行 Microsoft Edge都完全可以访问渐进式 Web 应用的技术和特征。


<!-- ====================================================================== -->
## <a name="installing-a-pwa"></a>安装PWA

当Microsoft Edge网站是可安装的渐进式 Web 应用 (PWA) 时， ("应用可用"图标。) 图标显示在地址**** 栏中 ![ ](media/app-available-icon.png) 。

1.  单击"**应用 ("** 可用"图标。) ![ ](media/app-available-icon.png) 图标安装PWA。

    :::image type="content" source="./media/edge-app-install-flyout.png" alt-text="Microsoft Edge 中的安装提示。":::

1.  单击 **"** 安装"以完成安装，PWA运行Windows。

许多 PA 也存在于Microsoft Store中，可以直接从该位置安装，而无需打开Microsoft Edge。

若要从PWA安装Microsoft Store，**请选择应用页面上**的"获取"：

:::image type="content" source="./media/install-webboard-microsoft-store.png" alt-text="从应用程序安装Microsoft Store。":::


<!-- ====================================================================== -->
## <a name="managing-pwas"></a>管理 PWA

若要查找已安装的渐进式 Web 应用 (PA) Microsoft Edge，请转到 `edge://apps` 。  在此页面上，可以通过单击"打开"打开任何 **应用**。  若要了解有关应用或卸载应用的详细信息，请单击"详细信息 **"。**

:::image type="content" source="./media/edge-apps-listing.png" alt-text="应用程序中已安装的应用 edge://apps。":::

还可以像管理其他应用一样 **，在**"应用和功能&设置中管理WINDOWS PA。

1.  在Windows中，选择"**开始**  >  **设置"。**
1.  在"查找设置"搜索**字段中键入"apps"，** 然后选择"**添加或删除程序"。**
1.  在PWA中查找要管理的应用，然后选择它以查找详细信息或删除它。

:::image type="content" source="./media/pwa-in-apps-and-features-settings.png" alt-text="应用程序上安装的应用列表Windows显示 PWA。":::


<!-- ====================================================================== -->
## <a name="windows-integration"></a>Windows 集成

渐进式 Web (PA) 像本机应用一样显示在 Windows。 它们显示在任务栏中 (可以固定到其中) 菜单，或者使用 在应用之间切换 `Alt` + `Tab` 时。

PWA 和本机应用可以并排驻留在任务栏中， (此处用红色框表示) ：

:::image type="content" source="./media/pwas-in-the-taskbar.png" alt-text="任务栏中的 PBA 和本机应用并排显示。":::

在使用 PA 在窗口之间切换时，将显示 PBA 和本机 (此处用红色框表示 `Alt` + `Tab` ，) ：

:::image type="content" source="./media/pwas-in-alttab.png" alt-text="当使用 Alt+Tab 在窗口之间切换时，将显示 PWA 和本机应用。":::

PWA 还可以向用户公开常见任务，作为显示在应用的右键单击菜单中的快捷方式：

:::image type="content" source="./media/pwa-shortcuts-in-taskbar.png" alt-text="常见任务在任务栏的右键单击菜单中列出。":::

详细了解如何 [定义快捷方式](./how-to/shortcuts.md)。

PWA 还可以在操作系统自己的通知服务中显示通知。 这有助于用户重新参与你的应用。 详细了解使用 [通知、推送通知和锁屏提醒](./how-to/notifications-badges.md)。

### <a name="starting-pwas-when-the-user-signs-in"></a>在用户登录时启动 PBA

WINDOWS上的 PA 可在用户登录时自动启动，以便他们可以立即使用应用。

若要将已安装的 PWA设置为在登录时自动启动Windows：

1.  打开 Microsoft Edge。
1.  转到 `edge://apps` 。  " **应用** "页列出了已安装的应用。
1.  在要配置的应用上，单击"更多选项****" ("更多选项"按钮。) 按钮，然后选择"在设备登录时 ![ ](./media/edge-apps-more-options.png) **自动启动"。**

:::image type="content" source="./media/turn-on-run-on-os-login-flag.png" alt-text="Use the More Options menu to turn on the 'Auto-start on device login' feature in Microsoft Edge.":::

在安装PWA时，用户还可以设置一个PWA自动启动。

若要设置PWA登录时自动启动，Windows安装PWA：

1.  在安装应用期间，在安装后对话框中，选择"设备登录**时自动启动"：**

:::image type="content" source="./media/post-install-run-on-os-login.png" alt-text="安装应用后，将自动打开安装后对话框。":::


<!-- ====================================================================== -->
## <a name="app-info-menu"></a>应用信息菜单

当用户在渐进 Web 应用 (标题栏中)  (PWA) 省略**** 号"..."按钮时，将显示"应用信息"菜单： ****

:::image type="content" source="./media/app-info-menu.png" alt-text="&quot;应用信息&quot;菜单。":::

" **应用信息** "菜单包含有关应用的有用信息，例如：

*  应用图标、名称和发布者。
*  已授予的各种应用程序权限。
*  隐私信息，如使用的 Cookie 数量。
*  可在应用中使用的扩展和工具列表。
