---
description: 适用于渐进式 Web 应用和 PA 的新功能 (源) 。
title: 渐进式 Web 应用程序中的新增功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/11/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， pwas， pwa， 渐进式 Web 应用， 源试用版
ms.openlocfilehash: ee5fad81ec1e5211afdd87d1ed466106f654e52f
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12157446"
---
# <a name="whats-new-in-progressive-web-apps"></a>渐进式 Web 应用程序中的新增功能

[!INCLUDE [contact DevTools team note](includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-96"></a>Microsoft Edge 96 中的新增功能

### <a name="new-hub-design-for-managing-your-installed-web-apps"></a>用于管理已安装的 Web 应用的新中心设计

Microsoft EdgeCanary 于 2021 年 10 月 5 日达到版本 96。  对于部分用户，我们正在测试新设计，以更好地管理已安装的 Web 应用。  当你在浏览器中转到时，它现在将显示重新设计的中心，将已安装 `edge://apps` 的 PWA 和网站作为应用列出。

你可以按以下任一方式对应用进行排序：
*  最近使用。
*  按字母顺序，基于标题。
*  安装日期。

还可以在列表或网格视图中排列应用。

:::image type="content" source="media/edgeapps-redesign.jpg" alt-text="Microsoft Edge现在具有新的应用管理页面。" lightbox="media/edgeapps-redesign.jpg":::

此外，你可以轻松将应用固定到任务栏或"开始 **"** 菜单。  你可以创建快捷方式，并启用应用以在用户登录时运行。

此外，现在还有一种轻松访问以下内容的方法：
*  关联源的权限和隐私详细信息。
*  有关应用程序的更多详细信息。

:::image type="content" source="media/edgeapps-details.jpg" alt-text="Microsoft Edge应用程序详细信息页面。" lightbox="media/edgeapps-details.jpg":::


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-95"></a>Microsoft Edge 95 中的新增功能

Microsoft Edge版本 95 于 2021 年 9 月 28 日移动到 Beta 渠道。
对于以下功能，源试用版保持活动状态：
*  [适用于桌面 PWA 的窗口控件覆盖](#window-controls-overlay-origin-trials)层。
*  [URL 处理程序](#url-handlers-origin-trial)。

我们希望协议 [处理程序源试用版于](#protocol-handlers-origin-trial) 2021 年 10 月 21 日结束。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-94"></a>Microsoft Edge 94 中的新增功能

Microsoft Edge 94 在 2021 年 9 月 23 日移动到 Stable。 此发布周期很短，只是<!-- em dash --> 从 Microsoft Edge 93 Stable 到 Microsoft Edge 94 Stable 的 3 周，因为我们贴靠到新的[4 周发布周期](https://blogs.windows.com/msedgedev/2021/03/12/new-release-cycles-microsoft-edge-extended-stable/)。  这一新的发布节奏与加速 Chrome 的发布周期Chromium里程碑[的新节奏相匹配](https://blog.chromium.org/2021/03/speeding-up-release-cycle.html)。

由于版本 94 的发布周期缩短Microsoft Edge，我们侧重于稳定发布周期后勤工作，我们将功能开发转移到 Microsoft Edge版本 95。

对于以下功能，源试用版保持活动状态：
*  [适用于桌面 PWA 的窗口控件覆盖](#window-controls-overlay-origin-trials)层。
*  [URL 处理程序](#url-handlers-origin-trial)。

我们希望协议[处理程序源试用版](#protocol-handlers-origin-trial)以 Microsoft Edge版本 94 结束，因为我们获取最终反馈并准备好将协议处理程序功能移动到 Stable。  如果你已注册协议处理程序的源试用版，我们计划在版本 94 之后结束Microsoft Edge试用期。  然后，我们将确定此功能何时变为稳定。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-93"></a>Microsoft Edge 93 中的新增功能

Microsoft Edge版本 93 在 2021 年 9 月 2 Microsoft Edge稳定渠道。 本文从开发人员和使用者的角度) 对渐进 Web 应用 (PA 进行了更新。

### <a name="measure-usage-of-your-store-installed-pwa"></a>测量应用商店安装的应用商店的使用情况PWA

Microsoft Edge现在包含引用器标头，其中包含对安装有 Microsoft Store 的第一个导航PWA。

此功能在 91 Microsoft Edge首次引入，我们在版本 93 中Microsoft Edge Bug 修复程序。

有关详细信息，请[从将渐进式 Web 应用发布到Microsoft Store。](../how-to/microsoft-store.md#measure-usage-of-your-store-installed-pwa)

### <a name="window-controls-overlay-origin-trials"></a>窗口控件覆盖原点试用

若要对当前在独立显示模式下显示的标题栏区域进行更多控制，可能需要试验窗口控件覆盖。 窗口控件覆盖 (WCO) 是一组协同工作的功能，它们仅提供应用窗口所需的基本控件。 此布局为 Web 内容层释放了更多空间。 WCO 可用于安装的桌面 PBA。

了解有关在渐进 Web 应用和 PBA (实验功能中试验窗口[控件覆盖) 。 ](../how-to/window-controls-overlay.md)

在我们的源试用版开发人员控制台 中注册 **Web 应用窗口控件覆盖** 试用版 [的来源](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-window-controls-overlay/registration/)。

### <a name="url-handlers-origin-trial"></a>URL 处理程序源试用版

开发人员现在可以在源试用版中使用实验功能 Web App URL 处理程序。 此功能允许注册已安装的应用PWA从引用其作用域的其他应用中打开链接。

若要详细了解如何试验 URL 处理程序，请通过渐进式 Web 应用和 PBA (实验[) 。 ](../how-to/handle-urls.md)

在我们的源试用版开发人员控制台 中注册你的域，以试用 Web 应用 **URL** [处理程序](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-url-handlers/registration/)。

### <a name="support-for-the-share-api-on-macos"></a>对 macOS 上的共享 API 的支持

我们已实现对 `navigator.share` 适用于 macOS 的 API 的支持。 未来几周内，此功能Microsoft Edge macOS 上的稳定浏览器。

详细了解 [navigator.share () API](https://developer.mozilla.org/docs/Web/API/Navigator/share)。


<!-- ====================================================================== -->
## <a name="whats-new-in-microsoft-edge-92"></a>Microsoft Edge 92 中的新增功能

Microsoft Edge 92 版本在 2021 年 7 月 22 Microsoft Edge成为稳定渠道。 本文从开发人员和使用者的角度) 对渐进 Web 应用 (PA 进行了更新。

### <a name="protocol-handlers-origin-trial"></a>协议处理程序来源试用版

现在，你可以注册PWA主机操作系统处理特定协议。 现在Windows协议处理程序的试用版。 可以在源试用注册页面 注册 **你的** 源，以使用 Web 应用协议处理程序 [试用版](https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-protocol-handler-registration/registration)。

若要详细了解如何对应用程序使用协议处理程序PWA，请通过渐进式 Web 应用和[PWA (实验) 。 ](../how-to/handle-protocols.md)

### <a name="streamlined-app-info-menu"></a>"简化应用信息"菜单

当用户在应用的标题栏中 (省略号) ..."按钮时，**** 将显示"应用**信息**"菜单。  我们更新了"应用**** 信息"菜单，并采用以下方式简化了用户体验，以提供与浏览器 UI 更像桌面应用的用户体验：
*  将应用**Publisher**信息移动到顶级，并作为用户首先看到的信息。

   :::image type="content" source="media/app-info.png" alt-text="简化的新应用信息菜单" lightbox="media/app-info.png":::

*  将隐私信息和控件移动到专用的第 2 级"隐私 **"** 菜单中。

   :::image type="content" source="media/privacy-menu.png" alt-text="专用&quot;隐私&quot;菜单中的隐私控件。" lightbox="media/privacy-menu.png":::

*  将与内容相关的工具移到专用的第 2 级"更多工具 **"** 菜单中。

   :::image type="content" source="media/more-tools.png" alt-text="现在，可以在&quot;更多工具&quot;菜单中找到与内容相关的工具。" lightbox="media/more-tools.png":::

### <a name="post-install-flyout-dialog-box"></a>安装后弹出对话框

在 PWA 上的 Microsoft Edge 浏览器安装 Windows 后，用户现在可以从四个选项中进行选择以轻松启动其应用：
*  **固定到任务栏**
*  **固定到“开始”**
*  **创建桌面快捷方式**
*  **设备登录时自动启动**

为方便起见，此弹出对话框在首次启动应用时显示。

:::image type="content" source="media/post-install-flyout.png" alt-text="安装后弹出对话框，包含&quot;固定到任务栏&quot;、&quot;固定到开始&quot;、&quot;创建桌面快捷方式&quot;和&quot;在设备登录时自动启动&quot;选项" lightbox="media/post-install-flyout.png":::

此功能将逐步向所有用户推出。  在此期间，如果你想要使用此功能，请转到 并启用标记 `edge://flags` Web Apps Post Install **Dialog**。

### <a name="restore-web-apps"></a>还原 Web 应用

在意外关闭之前运行的已安装网站和 PWA 现在 (，即当系统恢复) 将重新启动它们。

由于进程故障、系统重新启动或断电，可能会发生意外关闭。 在此更改之前，已安装的网站和 PWA 在系统还原时具有不确定的行为。


<!-- ====================================================================== -->
<!--[ArchiveMicrosoftEdgeLegacyDeveloperPWAsIndexRequirements]: /archive/microsoft-edge/legacy/developer/progressive-web-apps/index#requirements "Requirements - Progressive Web Apps (EdgeHTML) on Windows | Microsoft Docs"  -->
