---
description: 本指南概述了 PA 在 Microsoft Edge 和 Windows 上的用户体验。
title: PWA 的用户体验
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/15/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: 渐进式 Web 应用， PWA， edge， Windows， 桌面， 安装， 集成， microsoft store， ux
ms.openlocfilehash: 68d8701e592b6b5acf5060c0bd6454058ae8312d
ms.sourcegitcommit: 31762489bb17d6cdd75b99a54dbaa054e9286850
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2021
ms.locfileid: "12186028"
---
# <a name="the-user-experience-of-pwas"></a>PWA 的用户体验

在Windows，PWA 与其他应用一样。  任何运行 Microsoft Edge都完全可以访问渐进式 Web 应用的技术和特征。


<!-- ====================================================================== -->
## <a name="installing-a-pwa"></a>安装PWA

当Microsoft Edge网站是可安装PWA时， ("可用应用程序"图标。) 图标**** 显示在地址 ![ ](media/app-available-icon.png) 栏中。

1.  单击"**可用应用 ("** 应用"图标。) ![ ](media/app-available-icon.png) 图标安装PWA。
1.  单击 **"** 安装"以完成安装，PWA运行Windows。

:::image type="content" source="./media/edge-app-install-flyout.png" alt-text="Microsoft Edge 中的安装提示。" lightbox="./media/edge-app-install-flyout.png":::

许多 PA 也存在于 Microsoft Store可以直接安装，甚至无需打开 Microsoft Edge。

若要从PWA安装Microsoft Store，**请选择应用页面上**的"获取"。

:::image type="content" source="./media/install-webboard-microsoft-store.png" alt-text="从应用程序安装Microsoft Store。" lightbox="./media/install-webboard-microsoft-store.png":::


<!-- ====================================================================== -->
## <a name="managing-pwas"></a>管理 PWA

若要在列表中查找已安装的 PWA Microsoft Edge，请转到 `edge://apps` 。 在此页面上，可以通过单击"打开"打开任何 **应用**。  若要了解有关应用或卸载应用的详细信息，请单击"详细信息 **"。**

:::image type="content" source="./media/edge-apps-listing.png" alt-text="应用程序中已安装的应用 edge://apps。" lightbox="./media/edge-apps-listing.png":::

还可以像管理其他应用一样 **，** 在应用和功能&管理 Windows PWA。

1.  在Windows中，选择"**开始设置"**  >  ****。
1.  在"查找设置"搜索**字段中键入"apps"，** 然后选择"**添加或删除程序"。**
1.  在PWA中查找要管理的应用，然后选择它以查找详细信息或删除它。

:::image type="content" source="./media/pwa-in-apps-and-features-settings.png" alt-text="应用程序上安装的应用列表Windows显示 PWA。" lightbox="./media/pwa-in-apps-and-features-settings.png":::


<!-- ====================================================================== -->
## <a name="windows-integration"></a>Windows 集成

PWA 像本机应用一样显示在 Windows。 它们显示在任务栏中 (，可在其中固定) 菜单，或者使用 在应用之间切换 `Alt` + `Tab` 时。

:::image type="content" source="./media/pwas-in-the-taskbar.png" alt-text="任务栏中的 PBA 和本机应用并排显示。":::

:::image type="content" source="./media/pwas-in-alttab.png" alt-text="当使用 Alt+Tab 在窗口之间切换时，将显示 PWA 和本机应用。":::

PWA 还可以将常见任务公开给用户，作为快捷方式显示在应用的图标上下文菜单中 (右键单击) 。 详细了解如何 [定义快捷方式](./how-to/shortcuts.md)。

:::image type="content" source="./media/pwa-shortcuts-in-taskbar.png" alt-text="常见任务在任务栏上下文菜单中列出。" lightbox="./media/pwa-shortcuts-in-taskbar.png":::

PWA 还可以在操作系统自己的通知服务中显示通知。 这有助于用户重新参与你的应用。 详细了解使用 [通知、推送通知和锁屏提醒](./how-to/notifications-badges.md)。

### <a name="starting-pwas-when-the-user-logs-in"></a>在用户登录时启动 PBA

WINDOWS上的 PA 可在用户登录时自动启动，以便他们可以立即使用应用。

若要为已安装的组启用此功能PWA：

1.  打开 Microsoft Edge。
1.  转到 `edge://apps` 。
1.  在要配置的应用上，单击"更多选项****" ("更多选项"按钮。) 按钮，然后选择"在设备登录时 ![ ](./media/edge-apps-more-options.png) **自动启动"。**

:::image type="content" source="./media/turn-on-run-on-os-login-flag.png" alt-text="Use the more options menu to turn on the 'Auto-start on device login' feature in Microsoft Edge." lightbox="./media/turn-on-run-on-os-login-flag.png":::

安装应用后，用户还可以在安装后对话框中打开该功能。

:::image type="content" source="./media/post-install-run-on-os-login.png" alt-text="安装应用后，将自动打开安装后对话框。" lightbox="./media/post-install-run-on-os-login.png":::


<!-- ====================================================================== -->
## <a name="app-info-menu"></a>应用信息菜单

当用户在应用的标题栏中 (省略号) ..."按钮时，**** 将显示"应用**信息**"菜单。 此菜单包含有关应用的有用信息，例如：

*  应用图标、名称和发布者。
*  已授予的各种应用程序权限。
*  隐私信息，如使用的 Cookie 数量。
*  可在应用中使用的扩展和工具列表。

:::image type="content" source="./media/app-info-menu.png" alt-text="&quot;应用信息&quot;菜单。" lightbox="./media/app-info-menu.png":::
