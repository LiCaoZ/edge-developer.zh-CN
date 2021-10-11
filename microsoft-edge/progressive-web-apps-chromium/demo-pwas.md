---
description: 可用于了解有关如何使用 PWA 生成可编程 Web 应用 (示例) 。
title: 示例 PWA
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/28/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: 渐进式 Web 应用， PWA， 演示， 示例
ms.openlocfilehash: 277a8d1f9abdb137c2712a890ce4f54c9db8563d
ms.sourcegitcommit: 242e9611f73507f587d1669af24d0e3423f722dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2021
ms.locfileid: "12087221"
---
# <a name="sample-pwas"></a>示例 PWA

使用此示例应用列表可了解有关如何使用PWA API 的信息。

## <a name="webboard"></a>Webboard

智能白板应用。

[应用][|::ref1::|]、 [源代码][WebboardSourceCode]。

功能：

*  [快捷方式][FeatureShortcut]
*  [Web 共享][FeatureShare]
*  [共享目标][FeatureShareTarget]

:::image type="content" source="./media/webboard.png" alt-text="Webboard 绘图应用程序。" lightbox="./media/webboard.png":::

## <a name="devtools-tips"></a>DevTools 使用技巧

DevTools 的提示和技巧列表。

[应用][DevToolsTips]、 [源代码][DevToolsTipsSourceCode]。

功能：

*  [Web 共享][FeatureShare]
*  [URL 处理][FeatureUrlHandling]
*  [后台同步][FeatureBackgroundSync]
*  [定期后台同步][FeaturePeriodicBackgroundSync]
*  [通知][FeatureNotifications]

:::image type="content" source="./media/devtools-tips.png" alt-text="devtools-tips 应用。" lightbox="./media/devtools-tips.png":::

## <a name="my-tracks"></a>My Tracks

GPS 跟踪可视化应用。

[应用][MyTracks]、 [源代码][MyTracksSourceCode]。

功能：

*  [窗口控件覆盖][FeatureWindowControlsOverlay]
*  [协议处理][FeatureProtocolHandling]
*  [快捷方式][FeatureShortcut]
*  [文件处理][FeatureFileHandling]

:::image type="content" source="./media/my-tracks.png" alt-text="&quot;我的跟踪&quot;应用。" lightbox="./media/my-tracks.png":::

## <a name="my-movies"></a>我的电影

搜索和存储电影。

[应用][MyMovies]、 [源代码][MyMoviesSourceCode]。

功能：

*  [后台同步][FeatureBackgroundSync]
*  [通知][FeatureNotifications]

:::image type="content" source="./media/my-movies.png" alt-text="我的电影应用。" lightbox="./media/my-movies.png":::

## <a name="yahtzee"></a>Yahtzee

播放 Yahtzee。

[应用][|::ref2::|]、 [源代码][YahtzeeSourceCode]。

功能：

*  [窗口控件覆盖][FeatureWindowControlsOverlay]

:::image type="content" source="./media/yahtzee.png" alt-text="Yahtzee 应用。" lightbox="./media/yahtzee.png":::

## <a name="bpm-techno"></a>BPM 一年

实时的PMB 计数器。

[应用][BPMTechno]、 [源代码][BPMTechnoSourceCode]。

功能：

*  [快捷方式][FeatureShortcut]
*  [URL 处理][FeatureUrlHandling]
*  [文件处理][FeatureFileHandling]
*  [协议处理][FeatureProtocolHandling]
*  [共享目标][FeatureShareTarget]

:::image type="content" source="./media/bpm-techno.png" alt-text="&quot;下一次开发&quot;应用。" lightbox="./media/bpm-techno.png":::


<!-- ====================================================================== -->
<!-- Links -->
[Webboard]: https://webboard.app/ "Webboard"
[WebboardSourceCode]: https://github.com/pwa-builder/web-whiteboard "Webboard |GitHub"
[DevToolsTips]: https://devtoolstips.org "DevTools 使用技巧"
[DevToolsTipsSourceCode]: https://github.com/captainbrosset/devtools-tips "DevTools 使用技巧 |GitHub"
[MyTracks]: https://captainbrosset.github.io/mytracks/ "My Tracks"
[MyTracksSourceCode]: https://github.com/captainbrosset/mytracks "我的曲目|GitHub"
[MyMovies]: https://quirky-rosalind-ac1e65.netlify.app/ "我的电影"
[MyMoviesSourceCode]: https://github.com/captainbrosset/movies-db-pwa "我的电影|GitHub"
[Yahtzee]: https://yahtzee-pwa.glitch.me/ "Yahtzee"
[YahtzeeSourceCode]: https://glitch.com/edit/#!/yahtzee-pwa "Yahtzee |小故障"
[BPMTechno]: https://bpmtech.no/ "适用于 DJ 的 Real-Time - 免费 Online Real-Time版版"
[BPMTechnoSourceCode]: https://github.com/webmaxru/bpm-counter "|GitHub"

[FeatureShortcut]: ./how-to/shortcuts.md "定义应用快捷方式|Microsoft Docs"
[FeatureShare]: ./how-to/share.md#sharing-content "共享内容|Microsoft Docs"
[FeatureShareTarget]: ./how-to/share.md#receiving-shared-content "接收共享内容|Microsoft Docs"
[FeatureUrlHandling]: ./how-to/handle-urls.md "在渐进式 Web 应用应用程序中处理|Microsoft Docs"
[FeatureWindowControlsOverlay]: ./how-to/window-controls-overlay.md "显示标题栏中的内容|Microsoft Docs"
[FeatureProtocolHandling]: ./how-to/handle-protocols.md "在渐进式 Web 应用应用程序中处理|Microsoft Docs"
[FeatureFileHandling]: ./how-to/handle-files.md "在渐进式 Web 应用应用程序中处理|Microsoft Docs"
[FeaturePeriodicBackgroundSync]: ./how-to/background-syncs.md#regularly-get-fresh-content-with-the-periodic-background-sync-api "定期后台同步 API 应用定期获取|Microsoft Docs"
[FeatureBackgroundSync]: ./how-to/background-syncs.md#synchronize-data-with-the-server-with-the-background-sync-api "使用后台同步 API 设置将数据与服务器|Microsoft Docs"
[FeatureNotifications]: ./how-to/notifications-badges.md#display-notifications-in-the-action-center "在操作中心内显示|Microsoft Docs"
