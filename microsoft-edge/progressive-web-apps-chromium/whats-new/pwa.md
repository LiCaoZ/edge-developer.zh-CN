---
description: 渐进式 Web 应用和 PBA (新功能) 。
title: 渐进式 Web 应用程序中的新增功能
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/09/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， pwas， pwa， 渐进式 Web 应用
ms.openlocfilehash: 9643c8846ccea373c3051b137cc4299ba617dad7
ms.sourcegitcommit: 01ed086305c06b4e3a0436586524986700276148
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "11893519"
---
# <a name="whats-new-in-progressive-web-apps"></a>渐进式 Web 应用程序中的新增功能

[!INCLUDE [contact DevTools team note](includes/edge-whats-new-note.md)]


## <a name="whats-new-in-microsoft-edge-93"></a>Microsoft Edge 93 中的新增功能

Microsoft Edge版本 93 在 2021 年 8 月 3 Microsoft Edge Beta 渠道。 本文从开发人员和使用者的角度 (对渐进 Web 应用) PA 进行了更新。

## <a name="window-controls-overlay-origin-trials"></a>窗口控件覆盖原点试用

若要对当前在独立显示模式下显示的标题栏区域进行更多控制，可能需要试验窗口控件覆盖。 窗口控件覆盖 (WCO) 是一组协同工作的功能，它们仅提供应用窗口所需的基本控件。 此布局为 Web 内容层释放了更多空间。 WCO 可用于安装的桌面 PBA。 

了解有关在渐进式 Web 应用和 PBA (实验功能中试验[窗口控件覆盖) 。 ][ExpWCO]

在我们的源试用版开发人员控制台 中注册窗口控件覆盖 [试用版的来源][WCOOT]。

## <a name="url-handlers-origin-trial"></a>URL 处理程序源试用版

开发人员现在可以在源试用版中使用实验功能 Web App URL 处理程序。 此功能允许注册已安装的应用PWA从引用其作用域的其他应用中打开链接。

若要详细了解如何试验 URL 处理程序，请通过渐进式 Web 应用和[PWA (实验) 。 ][ExpURLHandler]

在我们的源试用版开发人员控制台 中注册你的域 [以试用][URLHandlerOT]URL。

## <a name="support-for-the-share-api-on-macos"></a>对 macOS 上的共享 API 的支持

我们已实现对 `navigator.share` 适用于 macOS 的 API 的支持。 未来几周内，此功能Microsoft Edge macOS 上的稳定浏览器。 

详细了解[navigator.share () API。][mdnShareAPI]


## <a name="whats-new-in-microsoft-edge-92"></a>Microsoft Edge 92 中的新增功能

Microsoft Edge版本 92 在 2021 年 7 Microsoft Edge成为稳定渠道。 本文从开发人员和使用者的角度 (对渐进 Web 应用) PA 进行了更新。

## <a name="protocol-handlers-origin-trial"></a>协议处理程序来源试用版 

现在，你可以注册PWA主机操作系统处理特定协议。 现在Windows协议处理程序的试用版。 你可以从源试用注册页面 注册你的源 [作为][MicrosoftDeveloperMicrosoftEdgeOriginTrialsWebAppProtocolHandlerRegistrationRegistration]试用版。

若要详细了解如何对项目使用协议处理程序PWA，请通过[渐进式 Web 应用和 PWA ][ExpProtocolHandlers] (实验) 。

## <a name="streamlined-app-info-menu"></a>"简化应用信息"菜单

当用户在应用的标题栏中 (**省略** 号) ..."按钮时，将显示" **应用信息** "菜单。  我们更新了"应用**** 信息"菜单，并采用以下方式简化了用户体验，以提供与浏览器 UI 更像桌面应用的用户体验：
*  将应用**Publisher**信息移动到顶级，并作为用户首先看到的信息。

   :::image type="complex" source="media/app-info.png" alt-text="简化的新应用信息菜单" lightbox="media/app-info.png":::
      简化的新应用 **信息** 菜单
   :::image-end:::

*  将隐私信息和控件移动到专用的第 2 级"隐私 **"** 菜单中。

   :::image type="complex" source="media/privacy-menu.png" alt-text="专用"隐私"菜单中的隐私控件" lightbox="media/privacy-menu.png":::
      专用"隐私"菜单中 **的隐私** 控件
   :::image-end:::

*  将与内容相关的工具移到专用的第 2 级"更多工具 **"** 菜单中。

   :::image type="complex" source="media/more-tools.png" alt-text="现在，可以在"更多工具"菜单中找到与内容相关的工具" lightbox="media/more-tools.png":::
      现在，可以在"更多工具"菜单中找到与 **内容相关的** 工具
   :::image-end:::


## <a name="post-install-flyout-dialog-box"></a>安装后弹出对话框

从 PWA 浏览器安装Microsoft Edge应用程序后Windows，用户现在可以从四个选项中进行选择以轻松启动其应用： 
*  **固定到任务栏** 
*  **固定到“开始”**
*  **创建桌面快捷方式**
*  **设备登录时自动启动**

为方便起见，此弹出对话框在首次启动应用时显示。

:::image type="complex" source="media/postInstallFlyout.png" alt-text="安装后弹出对话框，包含"固定到任务栏"、"固定到开始"、"创建桌面快捷方式"和"在设备登录时自动启动"选项" lightbox="media/postInstallFlyout.png":::
   安装后弹出对话框，包含"固定**到**任务栏"、"固定到开始******"、"创建**桌面快捷方式"和"在设备登录时**自动启动"选项**
:::image-end:::

此功能将逐步向所有用户推出。 在此期间，如果你想要使用此功能，请导航到 并启用标记 `edge://flags` Web Apps Post Install **Dialog**。

## <a name="restore-web-apps"></a>还原 Web 应用

在意外关闭之前运行的已安装的站点和 PWA 现在 (，即当系统恢复) 将重新启动它们。

由于进程故障、系统重新启动或断电，可能会发生意外关闭。 在此更改之前，已安装的网站和 PWA 在系统还原时具有不确定的行为。  

<!-- links -->  

<!--[ArchiveMicrosoftEdgeLegacyDeveloperPWAsIndexRequirements]: /archive/microsoft-edge/legacy/developer/progressive-web-apps/index#requirements "Requirements - Progressive Web Apps \(EdgeHTML\) on Windows | Microsoft Docs"  -->  

[ExpWCO]: ../experimental-features/index.md#window-controls-overlay-for-installed-desktop-web-apps "已安装桌面 Web 应用的窗口控件覆盖 - 实验功能"

[ExpProtocolHandlers]: ../experimental-features/index.md#uri-protocol-handling "URI 协议处理 - 实验性功能"

[ExpURLHandler]: ../experimental-features/index.md#url-link-handling "URL 链接处理 - 实验性功能"

[MicrosoftDeveloperMicrosoftEdgeOriginTrials]: https://developer.microsoft.com/microsoft-edge/origin-trials "源试用版|Microsoft Edge开发人员"

[MicrosoftDeveloperMicrosoftEdgeOriginTrialsWebAppProtocolHandlerRegistrationRegistration]: https://developer.microsoft.com/microsoft-edge/origin-trials/web-app-protocol-handler-registration/registration "注册 Web 应用协议处理程序|Microsoft 开发人员"  

[URLHandlerOT]: https://developer.microsoft.com/en-us/microsoft-edge/origin-trials/web-app-url-handlers/registration/ "注册 Web 应用 URL 处理程序|Microsoft 开发人员" 

[WCOOT]: https://developer.microsoft.com/en-us/microsoft-edge/origin-trials/web-app-window-controls-overlay/registration/ "注册 Web 应用窗口控件覆盖"

[mdnShareAPI]: https://developer.mozilla.org/en-US/docs/Web/API/Navigator/share
