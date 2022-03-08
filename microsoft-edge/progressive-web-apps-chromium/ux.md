---
title: PWA 的用户体验
description: A overview of the user experience of PWA on Microsoft Edge and Windows.
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/15/2021
ms.openlocfilehash: dcc66e38b05057d928e9a6b85a4365bc7913bfa0
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430099"
---
# <a name="the-user-experience-of-pwas"></a>PWA 的用户体验

在Windows，渐进式 Web (PA) 与其他应用一样。  任何运行 Microsoft Edge都完全可以访问渐进式 Web 应用的技术和特征。


<!-- ====================================================================== -->
## <a name="installing-a-pwa"></a>安装PWA

当Microsoft Edge网站是可安装的渐进式 Web 应用 (PWA) **** ![时， ("可用](media/app-available-icon.png)应用程序"图标。) 图标显示在地址栏中。

1.  单击"**可用应用 (**!["应用"图标](media/app-available-icon.png)。) 图标安装PWA。

    :::image type="content" source="./media/edge-app-install-flyout.png" alt-text="安装提示Microsoft Edge。":::

1.  单击 **"** 安装"以完成安装，PWA运行Windows。

许多 PA 也存在于Microsoft Store中，可以直接从该位置安装，而无需打开Microsoft Edge。

若要从PWA安装Microsoft Store，**请在应用页面上**选择获取：

:::image type="content" source="./media/install-webboard-microsoft-store.png" alt-text="从应用程序安装Microsoft Store。":::


<!-- ====================================================================== -->
## <a name="managing-pwas"></a>管理 PWA

若要查找已安装的渐进式 Web 应用 (PA) Microsoft Edge，请转到 `edge://apps`。  在此页上，可以通过单击"打开"打开任何 **应用**。  若要了解有关应用或卸载应用的详细信息，请单击"详细信息 **"**。

:::image type="content" source="./media/edge-apps-listing.png" alt-text="应用程序中已安装的应用 edge://apps。":::

还可以像管理其他应用一样 **，在**"应用和功能&设置中管理WINDOWS PA。

1.  在Windows中 **，选择"** 开始 > **设置**"。
1.  在"查找设置搜索 **"字段中键入"应用** "，然后选择" **添加或删除程序"**。
1.  在PWA中查找要管理的应用，然后选择它以查找详细信息或删除它。

:::image type="content" source="./media/pwa-in-apps-and-features-settings.png" alt-text="应用程序上安装的应用列表Windows PBA。":::


<!-- ====================================================================== -->
## <a name="windows-integration"></a>Windows 集成

渐进式 Web (PBA) 像本机应用一样显示在 Windows。 它们显示在任务栏中 (，可在其中固定) 、在"开始"菜单应用中切换时。`Alt`+`Tab`

PWA 和本机应用可以并排驻留在任务栏中， (此处由红色框表示) ：

:::image type="content" source="./media/pwas-in-the-taskbar.png" alt-text="任务栏中的 PBA 和本机应用并排显示。":::

在使用 PA `Alt`+`Tab` 在窗口之间切换时，将显示 PBA 和本机 (此处由一个红色框指示) ：

:::image type="content" source="./media/pwas-in-alttab.png" alt-text="当使用 Alt+Tab 在窗口之间切换时，将显示 PWA 和本机应用。":::

PWA 还可以向用户公开常见任务，作为显示在应用的右键单击菜单中的快捷方式：

:::image type="content" source="./media/pwa-shortcuts-in-taskbar.png" alt-text="常见任务在任务栏的右键单击菜单中列出。":::

详细了解如何 [定义快捷方式](how-to/shortcuts.md)。

PWA 还可以在操作系统自己的通知服务中显示通知。 这有助于用户重新参与你的应用。 详细了解使用 [通知、推送通知和锁屏提醒](how-to/notifications-badges.md)。

### <a name="starting-pwas-when-the-user-signs-in"></a>在用户登录时启动 PBA

WINDOWS上的 PA 可在用户登录时自动启动，以便他们可以立即使用应用。

若要将已安装PWA设置为在登录登录时自动启动Windows：

1.  打开 Microsoft Edge。
1.  `edge://apps`转到 。  " **应用** "页列出了已安装的应用。
1.  **** 在要配置的应用上，![](media/edge-apps-more-options.png)单击"更多选项" ("更多选项"按钮) "按钮，然后选择"在设备登录时**自动启动"**。

:::image type="content" source="./media/turn-on-run-on-os-login-flag.png" alt-text="Use the More Options menu to turn on the 'Auto-start on device login' feature in Microsoft Edge.":::

在安装PWA时，用户还可以设置PWA自动启动。

若要设置PWA登录时自动启动Windows安装以下PWA：

1.  在安装应用期间，在安装后对话框中，选择 **"设备登录时自动启动"**：

:::image type="content" source="./media/post-install-run-on-os-login.png" alt-text="安装应用后，将自动打开安装后对话框。":::


<!-- ====================================================================== -->
## <a name="app-info-menu"></a>应用信息菜单

当用户在渐进式 Web 应用 (标题栏中) 省略号"...****"按钮 (PWA) "应用信息"菜单将显示：****

:::image type="content" source="./media/app-info-menu.png" alt-text="&quot;应用信息&quot;菜单。":::

" **应用信息** "菜单包含有关应用的有用信息，例如：

*  应用图标、名称和发布者。
*  已授予的各种应用程序权限。
*  隐私信息，如使用的 Cookie 数量。
*  可在应用中使用的扩展和工具列表。
