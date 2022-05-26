---
title: PWA 的用户体验
description: Microsoft Edge和Windows上的 PVA 用户体验概述。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/15/2021
ms.openlocfilehash: 1ee3b3ace5cafe12a7c8f0d308e35d6c69ed3cab
ms.sourcegitcommit: 8aee95757de12c62f4a74d37649ad5979f9e0ba9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2022
ms.locfileid: "12550723"
---
# <a name="the-user-experience-of-pwas"></a>PWA 的用户体验

Windows，渐进式Web 应用 (PVA) 与其他应用一样。  运行Microsoft Edge的任何设备都可以完全访问渐进式Web 应用的技术和特征。


<!-- ====================================================================== -->
## <a name="installing-a-pwa"></a>安装PWA

当Microsoft Edge确定网站是可安装的渐进式 Web 应用 (PWA) 时，**可用的应用** (![“可用应用”图标。](media/app-available-icon.png)地址栏中将显示) 图标。

1.  单击 **“可用应用**”图标](media/app-available-icon.png) (![应用。) 图标安装PWA。

    ![Microsoft Edge中的安装提示。](./media/edge-app-install-flyout.png)

1.  单击 **“安装**”以完成安装并在Windows中运行PWA。

Microsoft Store上也存在许多 PVA，可以直接从那里安装，无需打开Microsoft Edge。

若要从Microsoft Store安装PWA，请选择 **“获取**应用”页：

![从Microsoft Store安装应用。](./media/install-webboard-microsoft-store.png)


<!-- ====================================================================== -->
## <a name="managing-pwas"></a>管理 PVA

若要在Microsoft Edge中查找已安装的渐进式Web 应用 (PVA) 列表，请转到 `edge://apps`。  在此页面上，可以通过单击“ **打开**”打开任何应用。  若要详细了解应用或卸载它，请单击 **“详细信息**”。

![edge://apps 中已安装的应用的列表。](./media/edge-apps-listing.png)

还可以像其他Windows应用一样，在**应用&功能**系统设置中管理 PVA。

1.  在Windows中，选择 **"开始"菜单** > **设置**。
1.  在“ **查找设置** 搜索”字段中键入“应用”，然后选择 **“添加或删除程序**”。
1.  在应用列表中查找要管理的PWA，然后选择它以查找更多信息或将其删除。

![Windows上安装的应用列表也会显示 PVA。](./media/pwa-in-apps-and-features-settings.png)


<!-- ====================================================================== -->
## <a name="windows-integration"></a>Windows 集成

渐进式Web 应用 (PVA) 显示为Windows上的本机应用。 它们显示在任务栏 (中，可以在其中固定) 、"开始"菜单或在应用`Alt`+`Tab`之间切换时。

PVA 和本机应用可以并排驻留在任务栏中， (此处用红色框指示 PVA) ：

![任务栏中的 PVA 和本机应用并行运行。](./media/pwas-in-the-taskbar.png)

使用 (PVA 在窗口 `Alt`+`Tab` 之间切换时，会显示 PVA 和本机应用，此处用红色框) ：

![使用 Alt+Tab 在窗口之间切换时，将显示 PVA 和本机应用。](./media/pwas-in-alttab.png)

PVA 还可以将常见任务作为应用右键单击菜单中显示的快捷方式向用户公开：

![任务栏的右键单击菜单中列出了常见任务。](./media/pwa-shortcuts-in-taskbar.png)

详细了解 [如何定义快捷方式](how-to/shortcuts.md)。

PVA 还可以在操作系统自己的通知服务中显示通知。 这可帮助用户重新参与你的应用。 详细了解 [如何使用通知、推送消息和徽章](how-to/notifications-badges.md)。

### <a name="starting-pwas-when-the-user-signs-in"></a>用户登录时启动 PVA

Windows上的 PVA 可以在用户登录时自动启动，以便他们可以立即与应用互动。

若要将已安装的PWA设置为在登录到Windows时自动启动：

1.  打开 Microsoft Edge。
1.  转到 `edge://apps`。  “ **应用** ”页列出已安装的应用。
1.  在要配置的应用上，单击“ **更多选项** ” (![“更多选项”按钮。](media/edge-apps-more-options.png)) 按钮，然后 **在设备登录时选择“自动启动**”。

![使用“更多选项”菜单打开Microsoft Edge中的“设备登录时自动启动”功能。](./media/turn-on-run-on-os-login-flag.png)

在安装PWA期间，用户还有机会设置自动启动的PWA。

若要将PWA设置为在登录到Windows时自动启动，同时安装PWA：

1.  在安装应用期间，在帖子安装对话框中，在**设备登录时选择“自动启动**”：

![安装应用后，帖子安装对话框会自动打开。](./media/post-install-run-on-os-login.png)


<!-- ====================================================================== -->
## <a name="app-info-menu"></a>应用信息菜单

当用户在渐进式Web 应用 (PWA) 的标题栏中选择省略号 (**...**) 按钮时，将显示 **“应用信息**”菜单：

![“应用信息”菜单。](./media/app-info-menu.png)

**“应用信息**”菜单包含有关应用的有用信息，例如：

*  应用图标、名称和发布者。
*  已授予的各种应用权限。
*  隐私信息，例如使用的 Cookie 数。
*  可在应用中使用的扩展和工具列表。
