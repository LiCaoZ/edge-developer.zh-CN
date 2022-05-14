---
title: 有关使用 Microsoft Edge 进行 Web 开发的视频
description: 观看有关 Microsoft Edge Web 开发技术（如 DevTools、渐进式 Web 应用、Web 平台功能、WebView2 等）的公告和演示视频。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/05/2022
ms.openlocfilehash: 1e39d0d88457aac67f5ee12f063d815c93d8d50f
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12514067"
---
# <a name="videos-about-web-development-with-microsoft-edge"></a>有关使用 Microsoft Edge 进行 Web 开发的视频

发现并了解新的Microsoft Edge Web 开发技术和产品，包括 DevTools、Web 平台 API 和功能、渐进式Web 应用和 WebView2。

此页面包含指向短视频的链接，每个视频只关注一项功能，包括演示。

Microsoft 定期在 [Microsoft Edge YouTube 频道](https://www.youtube.com/channel/UCIGx7oT8p6-jUpOfg98yelA)上发布新视频，这些视频也列在下面。

单击以下列表中的缩略图，观看 YouTube 上的相应视频。

<!--
To add a new video:
- Create a thumbnail image for the video: 300px wide, no faces of people, big blue play button.
- Place the video thumbnail image in the ./images folder next to this page.
- Prepare the YouTube URL, title, and description.
- Add a new H2 heading below this comment, with the title of the video.
- Add the publish date next (same as the one on YouTube).
- Add a markdown image below the date, with the thumbnail you added before, and link this image tag to the YouTube video.
- Place the description below that, fixing any links that came from YouTube and that might have been shortened.
-->


<!-- ====================================================================== -->
## <a name="devtools---customizing-microsoft-edge-developer-tools-and-quick-feature-access"></a>DevTools - 自定义Microsoft Edge开发人员工具和快速功能访问

_发布于 2022 年 5 月 5 日。_

[![TDevtools 自定义视频的 humbnail 图像](./images/customize-devtools.png)](https://www.youtube.com/watch?v=ypRzEBYNptQ)

了解如何根据需要自定义 DevTools。

此视频介绍如何停靠或撤换 DevTools、打开新工具以及关闭不需要的工具。 它介绍如何在底部抽屉中移动工具并自定义文本大小和主题。 该视频还介绍了如何使用命令菜单键盘快捷方式快速自定义 DevTools。


<!-- ====================================================================== -->
## <a name="web-platform---highlight-text-on-the-web-with-the-css-custom-highlight-api"></a>Web 平台 - 使用 CSS 自定义突出显示 API 突出显示 Web 上的文本

_发布于 2022 年 4 月 28 日。_

[![TCSS 自定义突出显示 API 视频的 humbnail 图像](./images/css-custom-highlight-api.png)](https://www.youtube.com/watch?v=1qldqyT324o)

在 Web 上设置文本的样式范围非常有用，但从历史上看，这是一件复杂的事情。

新的 [CSS 自定义突出显示 API](https://www.w3.org/TR/css-highlight-api-1/) 是突出显示 Web 上的文本范围的未来。 它为 Web 开发人员提供 JavaScript 和 CSS 功能，使其更轻松、更高效地设置任意文本范围的样式。

有关详细信息，请参阅 [CSS 自定义突出显示 API：在 Web 上突出显示文本范围的未来](https://css-tricks.com/css-custom-highlight-api-early-loo/)。


<!-- ====================================================================== -->
## <a name="devtools---debug-memory-leaks-with-the-microsoft-edge-detached-elements-tool"></a>DevTools - 使用Microsoft Edge分离的元素工具调试内存泄漏

_发布于 2021 年 12 月 9 日。_

[![T分离元素视频的 humbnail 图像](./images/detached-elements.png)](https://www.youtube.com/watch?v=v2iy17ptmBk)

我们很高兴在 Microsoft Edge DevTools 中宣布新的分离元素工具，帮助你调查和解决 DOM 内存泄漏。

当应用程序的 JavaScript 代码在内存中保留越来越多的对象，而不是为浏览器释放对象以进行垃圾回收时，会发生内存泄漏。
我们与Microsoft Teams开发人员一起构建了此工具，它已帮助我们查找并修复了许多自己的网站和应用的内存泄漏。

有关详细信息，请参阅使用[分离元素工具调试 DOM 内存泄漏](../devtools-guide-chromium/memory-problems/dom-leaks.md)，并阅读相应的博客帖子使用[Microsoft Edge分离元素工具调试内存泄漏](https://blogs.windows.com/msedgedev/2021/12/09/debug-memory-leaks-detached-elements-tool-devtools/)。


<!-- ====================================================================== -->
## <a name="web-platform---the-eyedropper-api"></a>Web 平台 - EyeDropper API

_发布于 2021 年 11 月 22 日。_

[![T眼投影机 API 视频的 humbnail 图像](./images/eyedropper-api.png)](https://www.youtube.com/watch?v=XZUEnUbI7dE)

Microsoft Edge团队与Chromium开源项目合作指定并实施了新的 EyeDropper API。 提供 [有关问题的反馈 - WICG/眼球| github.com](https://github.com/WICG/eyedropper-api/issues)。

许多创造性的应用程序使用户能够从应用窗口的各个部分，甚至从整个屏幕中选择颜色，通常使用眼球隐喻。 通过 EyeDropper API，作者可以在 Web 上构建自定义颜色选取器时使用浏览器提供的眼滴。

有关详细信息，请参阅使用 [EyeDropper API | web.dev 和 EyeDropper API 选取屏幕上任何像素的颜色](https://web.dev/eyedropper/) [- Web API |MDN developer.mozilla.org](https://developer.mozilla.org/docs/Web/API/EyeDropper_API)。
