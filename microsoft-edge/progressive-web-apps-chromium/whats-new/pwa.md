---
title: 渐进式 Web 应用中的新增功能
description: 适用于渐进式 Web 应用和 PA 的新功能 (源) 。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/23/2022
ms.openlocfilehash: cf9d53b85b4842b46bb199a8ec80a83a81e69490
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12432174"
---
# <a name="whats-new-in-progressive-web-apps"></a>渐进式 Web 应用中的新增功能

此页面列出了来自) Web Apps 团队的渐进式 Web (PA Microsoft Edge Web Apps 和 Web Apps 的更新。  若要试用新功能，请阅读这些通知。  若要了解最新且最最好的功能，请下载 Beta、[Microsoft Edge](https://www.microsoftedgeinsider.com/download) 和 Canary (预览) 。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-100"></a>Microsoft Edge 100 中的新增功能

Microsoft Edge Dev Canary 频道在 2022 年 2 月 9 日移动到版本 100。  在此里程碑中，我们将测试以下新的 Web 应用功能。  我们希望这些新功能在测试阶段后推出到稳定。


### <a name="app-sync"></a>应用同步

支持收藏夹、设置、历史记录等功能的同步服务已扩展为包括已安装的 Web 应用，即 PBA 和作为应用安装的网站。  当你登录到你的配置文件并且已选择加入同步时，同步服务将正常工作。

随着我们测试并逐步发布此功能，****`edge://apps`已选择同步的用户将开始在页面中看到可用应用部分以及重新设计**的应用菜单。**


### <a name="the-_your-available-apps_-section"></a>可用 _应用_ 部分

"**你的可用**应用"部分将显示你安装在具有相同登录配置文件的其他设备上（当前未安装在你使用的 Microsoft Edge 实例中）的任何应用。  可用应用将在其自己的部分中显示，并包含灰色图标。  单击 **应用** 上的"安装"按钮以在该设备中安装该应用：

!["应用"页上显示的可用应用，突出显示了安装按钮。](media/available-app-install.png)

在此阶段，应用同步仅在桌面设备上可用。  若要使应用跨设备保持同步，在一台设备上添加应用会将其添加到其他设备的可用应用部分****。  卸载一台设备上的应用会将其从其他设备中删除。


### <a name="redesigned-apps-menu"></a>重新设计的应用菜单

在Microsoft Edge中，将重新设计设置******菜单和更多**菜单中的"应用"命令：
*  " **应用** "菜单图标可以添加到工具栏中，以便快速访问。
*  弹出菜单可以固定为边栏打开，以在 Web 内容旁边显示应用。
*  添加了可自定义的视图和排序选项以及"我的可用应用 **"部分以支持** 应用同步功能。

用户可以在工具栏上显示" **应用** "菜单图标，以便快速访问：

> [!div class="mx-imgBorder"]
> !["应用"图标可以显示在工具栏上，以便快速访问。](media/apps-toolbar-icon.png)

用户可以将"应用 **"** 菜单固定为边栏打开：

> [!div class="mx-imgBorder"]
> ![用户可以将"应用"菜单作为边栏固定打开。](media/pin-apps-menu.png)

用户可以在列表或网格视图之间选择：

> [!div class="mx-imgBorder"]
> ![用户可以选择应用的列表视图或网格视图。](media/apps-view-options.png)

用户可以选择其应用的排序顺序：

> [!div class="mx-imgBorder"]
> ![用户可以选择其应用的排序顺序。](media/apps-sort-options.png)


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-97"></a>Microsoft Edge 97 中的新增功能

Microsoft Edge版本 96 计划于 2021 年 11 月 18 日成为 Stable 版本。  Microsoft Edge版本 97 将在该日期之后从 Dev 转移到 Beta 预览频道。


### <a name="store-apps-registered-as-url-handlers-hide-custom-tab-ui"></a>作为 URL 处理程序注册的应用商店应用隐藏自定义选项卡 UI 

从 PWA 的域重定向到具有不同顶级域 (TLD) 的匹配域名时，参与 [URL](#url-handlers-origin-trial) 处理程序源试用版的应用商店安装的 PWA 将不再显示 Chrome 自定义选项卡 (CCT) 。 此重定向通常发生在具有特定于区域设置域的应用中;例如，加拿大用户从`contoso.com``contoso.ca`重定向到 。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-96"></a>Microsoft Edge 96 中的新增功能


### <a name="url-protocol-handlers-moves-to-stable"></a>URL 协议处理程序移至稳定

源试用已结束。  URL 协议处理程序功能现已在 Microsoft Edge 96 Stable 中交付。

另请参阅：
*  [协议处理程序来源试用版](#protocol-handlers-origin-trial)
*  [处理渐进式 Web 应用中的协议](../how-to/handle-protocols.md)
*  [PBA 的 URL 协议处理程序注册](https://web.dev/url-protocol-handler/)


### <a name="new-hub-design-for-managing-your-installed-web-apps"></a>用于管理已安装的 Web 应用的新中心设计

Microsoft Edge Canary 于 2021 年 10 月 5 日达到版本 96。  通过部分用户，我们正在测试新设计，以更好地管理已安装的 Web 应用。  当你在浏览器中转到 `edge://apps` 时，它现在将显示重新设计的中心，将已安装的 PWA 和网站作为应用列出。


#### <a name="sort-order"></a>排序顺序

你可以按以下任一方式对应用进行排序：
*  最近使用。
*  按字母顺序，基于标题。
*  安装日期。


#### <a name="list-view-or-grid-view"></a>列表视图或网格视图

可以使用"查看为"下拉列表在列表或网格 **视图中排列** 应用。  在此图像中， **选择了网格** 视图：

![应用程序中新的应用管理Microsoft Edge。](media/edgeapps-redesign.jpg)

_若要缩放：右键单击>新选项卡中的"打开图像"。_


#### <a name="pin-apps-create-shortcuts-to-apps-run-app-on-login"></a>固定应用、创建应用的快捷方式、登录时运行应用

你可以轻松地将应用固定到任务栏或"开始 **"** 菜单。  你可以创建快捷方式，并启用应用以在用户登录时运行。


#### <a name="app-details-page"></a>应用详细信息页面

现在，有一个应用详细信息页面，它提供轻松访问以下内容的方法：
*  关联源的权限和隐私详细信息。
*  有关应用程序的更多详细信息。

应用详细信息页面：

![应用程序中的应用程序详细信息Microsoft Edge。](media/edgeapps-details.jpg)


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-95"></a>Microsoft Edge 95 中的新增功能

Microsoft Edge版本 95 于 2021 年 9 月 28 日移动到 Beta 渠道。  对于以下功能，源试用版保持活动状态：
*  [适用于桌面 PBA 的窗口控件覆盖](#window-controls-overlay-origin-trials)层。
*  [URL 处理程序](#url-handlers-origin-trial)。

我们希望协议 [处理程序源试用版于](#protocol-handlers-origin-trial) 2021 年 10 月 21 日结束。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-94"></a>Microsoft Edge 94 中的新增功能

Microsoft Edge版本 94 于 2021 年 9 月 23 日移动到 Stable。 此发布周期很短，只是<!-- em dash --> 3 周，从 Microsoft Edge 93 Stable 到 Microsoft Edge 94 Stable，因为我们已贴靠到新的 [4 周发布周期](https://blogs.windows.com/msedgedev/2021/03/12/new-release-cycles-microsoft-edge-extended-stable/)。  此新版本节奏与加速 Chrome 发布周期Chromium里程碑的新节奏[相匹配](https://blog.chromium.org/2021/03/speeding-up-release-cycle.html)。

由于版本 94 的发布周期缩短Microsoft Edge，我们侧重于稳定发布周期后勤工作，我们将功能开发转移到 Microsoft Edge 版本 95。

对于以下功能，源试用版保持活动状态：
*  [适用于桌面 PBA 的窗口控件覆盖](#window-controls-overlay-origin-trials)层。
*  [URL 处理程序](#url-handlers-origin-trial)。

我们希望协议[处理程序源试用版](#protocol-handlers-origin-trial)以 Microsoft Edge版本 94 结束，因为我们获取最终反馈并准备好将协议处理程序功能移动到 Stable。  如果你已注册协议处理程序的源试用版，我们计划在版本 94 之后结束Microsoft Edge试用期。  然后，我们将确定此功能何时变为稳定。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-93"></a>Microsoft Edge 93 中的新增功能

Microsoft Edge版本 93 在 2021 年 9 月 2 Microsoft Edge稳定渠道。 本文从开发人员和使用者的角度列出了我们对渐进式 Web (PA) 进行的更新。


### <a name="measure-usage-of-your-store-installed-pwa"></a>测量应用商店安装的应用商店的使用情况PWA

Microsoft Edge包含引用器标头，其中包含对已安装的 Microsoft Store 的第一个导航PWA。

此功能在 91 Microsoft Edge首次引入，我们在版本 93 中Microsoft Edge Bug 修复。

有关详细信息，请[从将渐进 Web 应用发布到Microsoft Store](../how-to/microsoft-store.md#measure-usage-of-your-pwa-installed-from-the-microsoft-store)。


### <a name="window-controls-overlay-origin-trials"></a>窗口控件覆盖原点试用版

若要对当前在独立显示模式下显示的标题栏区域进行更多控制，可能需要试验窗口控件覆盖。 窗口控件 (WCO) 是一组协同工作的功能，它们仅提供应用窗口所需的基本控件。 此布局为 Web 内容层释放了更多空间。 WCO 可用于安装的桌面 PBA。

了解有关在渐进 Web 应用和 PBA (实验功能中试验窗口 [控件覆盖) ](../how-to/window-controls-overlay.md)。

在我们的源试用版开发人员控制台中注册 **Web 应用窗口控件覆盖**[试用版的来源](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-window-controls-overlay/registration/)。


### <a name="url-handlers-origin-trial"></a>URL 处理程序源试用版

开发人员现在可以在源试用版中使用实验性功能 Web App URL 处理程序。 此功能允许注册已安装的应用PWA从引用其作用域的其他应用中打开链接。

若要详细了解如何试验 URL 处理程序，请通过渐进 [式 Web ](../how-to/handle-urls.md)应用和 PBA (实验) 。

在我们的源试用版开发人员控制台 **中** 注册你的域，以试用 Web [应用 URL 处理程序](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-url-handlers/registration/)。


### <a name="support-for-the-share-api-on-macos"></a>对 macOS 上的共享 API 的支持

我们已实现对适用于 `navigator.share` macOS 的 API 的支持。 未来几周内，此功能Microsoft Edge macOS 上的稳定浏览器。

详细了解 [navigator.share () API](https://developer.mozilla.org/docs/Web/API/Navigator/share)。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-92"></a>Microsoft Edge 92 中的新增功能

Microsoft Edge版本 92 在 2021 年 7 Microsoft Edge成为稳定渠道。 本文从开发人员和使用者的角度列出了我们对渐进式 Web (PA) 进行的更新。


### <a name="protocol-handlers-origin-trial"></a>协议处理程序来源试用版

现在，你可以注册PWA主机操作系统处理特定协议。 现在Windows协议处理程序的试用版。 可以在源试用注册页面注册你的源，以使用 **Web 应用** 协议处理程序 [试用版](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-protocol-handler-registration/registration)。

有关将协议处理程序与 PWA一起使用， ([PA 中的](../how-to/handle-protocols.md)实验) 。


### <a name="streamlined-app-info-menu"></a>简化的应用信息菜单

当用户在应用的标题栏中 (省略号) ..."按钮时，**** 将显示"应用**信息**"菜单。  我们更新了"应用**** 信息"菜单，并采用以下方式简化了用户体验，以提供与浏览器 UI 更像桌面应用的用户体验：

*  将应用**Publisher**信息移动到顶级，并作为用户首先看到的信息：

   ![简化的新应用信息菜单。](media/app-info.png)

*  将隐私信息和控件移动到专用的第 2 级"隐私 **"** 菜单：

   ![专用"隐私"菜单中的隐私控件。](media/privacy-menu.png)

*  将与内容相关的工具移动到专用的 2nd 级 **"更多工具"** 菜单：

   ![现在，可以在"更多工具"菜单中找到与内容相关的工具。](media/more-tools.png)


### <a name="post-install-flyout-dialog-box"></a>安装后弹出对话框

从 PWA 浏览器安装Microsoft Edge应用程序后Windows，用户现在可以从四个选项中进行选择以轻松启动其应用：
*  **固定到任务栏**
*  **固定到“开始”**
*  **创建桌面快捷方式**
*  **设备登录时自动启动**

为方便起见，此弹出对话框在首次启动应用时显示：

![安装后弹出对话框，包含"固定到任务栏"、"固定到开始"、"创建桌面快捷方式"和"在设备登录时自动启动"选项。](media/post-install-flyout.png)

此功能将逐步向所有用户推出。  在此期间，如果你想要 `edge://flags` 使用此功能，请转到 并启用标记 **Web Apps 安装后对话框**。


### <a name="restore-web-apps"></a>还原 Web 应用

在意外关闭之前运行的已安装网站和 PWA 现在 (，即当系统恢复) 将重新启动它们。

由于进程故障、系统重新启动或断电，可能会发生意外关闭。 在此更改之前，已安装的网站和 PWA 在系统还原时具有不确定的行为。
