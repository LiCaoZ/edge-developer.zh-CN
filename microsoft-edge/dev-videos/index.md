---
title: 有关使用 Microsoft Edge 进行 Web 开发的视频
description: 观看有关 Microsoft Edge Web 开发技术（如 DevTools、渐进式 Web 应用、Web 平台功能、WebView2 等）的公告和演示视频。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/24/2022
ms.openlocfilehash: 1d111bddd20c99299a55e2d7cfc7e3bf31c1ee54
ms.sourcegitcommit: 8a284be9a060a8b09121275a2491a30eda9156b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2022
ms.locfileid: "12584605"
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
## <a name="devtools---use-your-preferred-language-in-devtools"></a>DevTools - 在 DevTools 中使用首选语言

_发布于 2022 年 6 月 9 日。_

[![TDevTools 本地化视频的 humbnail 图像](./images/devtools-localization.png)](https://www.youtube.com/watch?v=AeF0AvWpUO8)

Microsoft Edge DevTools 支持 13 种不同的语言。 在此视频中，团队演示如何选择最适合编码和调试的语言。

若要详细了解如何更改 DevTools 语言设置，请查看 [更改 DevTools 语言设置](../devtools-guide-chromium/customize/localization.md)。

若要报告任何翻译错误，请查看[Microsoft Edge DevTools 团队](../devtools-guide-chromium/contact.md)。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-102"></a>DevTools - DevTools 102 中的新增功能

_发布日期：2022 年 6 月 1 日。_

[![T102 视频中的 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-102.png)](https://www.youtube.com/watch?v=JY6DfhSdr_A)

在 [DevTools 102 中的新增](../devtools-guide-chromium/whats-new/2022/05/devtools-102.md)功能中，从 Microsoft Edge DevTools 团队了解有关我们的最新公告的详细信息。


<!-- ====================================================================== -->
## <a name="web-platform---fully-style-the-drop-down-part-of-a-select-with-the-new-selectmenu-element"></a>Web 平台 - 使用新`<selectmenu>`元素完全设置下拉部分的`<select>`样式

_发布于 2022 年 5 月 31 日。_

[![Tselectmenu 视频的 humbnail 图像](./images/selectmenu.png)](https://www.youtube.com/watch?v=Ts7jvRyQACY)

样式 `<select>` 元素具有挑战性。 实验 `<selectmenu>` 元素有望通过使 Web 开发人员能够设置元素的所有部分的样式来克服剩余的限制。

若要详细了解样式元素`<select>`和新`<selectmenu>`元素，请参阅博客帖子[真实样式`<select>`元素](https://blogs.windows.com/msedgedev/2022/05/05/styling-select-elements-for-real/)。


<!-- ====================================================================== -->
## <a name="devtools---advanced-issues-filtering-in-edge-devtools-and-vscode"></a>DevTools - Edge DevTools 和 VSCode 中的高级问题筛选

_发布于 2022 年 5 月 20 日。_

[![TDevTools 问题筛选视频的 humbnail 图像](./images/advanced-issues-filtering.png)](https://www.youtube.com/watch?v=_dePgo89bq0)

每个 Web 产品都有问题。 Microsoft Edge DevTools **问题**工具按类型（包括辅助功能、兼容性、性能等）分析当前网页和报告问题。

如果已VS Code，则VS Code的 Microsoft Edge DevTools 扩展会直接在源代码中提供问题。

发布的产品也可能有很多问题。 根据你的反馈，我们添加了有用的方法来筛选问题。 例如，可以禁用来自第三方库的问题，并选择要查看相关问题的浏览器。

若要详细了解“问题”工具，请 [参阅使用“问题”工具查找和解决问题](../devtools-guide-chromium/issues/index.md)。

若要详细了解VS Code的 Microsoft Edge DevTools 扩展，请[参阅 Microsoft Edge Visual Studio Code 的 DevTools 扩展](../visual-studio-code/microsoft-edge-devtools-extension.md)。


<!-- ====================================================================== -->
## <a name="web-platform---create-a-scroll-linked-animation-without-javascript"></a>Web 平台 - 创建没有 JavaScript 的滚动链接动画

_发布于 2022 年 5 月 12 日。_

[![T滚动链接动画 API 视频的 humbnail 图像](./images/scroll-linked-animations.png)](https://www.youtube.com/watch?v=Q0nhiHVVnvI)

了解即将推出的 CSS 滚动链接动画功能，以及如何在不使用 JavaScript 的情况下在网页上创建读取进度指示器。

CSS 滚动链接动画是Microsoft Edge中的一项实验性功能。  若要尝试此功能，请转到 `edge://flags` 并启用 **实验性 Web 平台功能** 设置。

若要播放视频中显示的演示应用程序，请参阅呈现的 [阅读器演示](https://microsoftedge.github.io/Demos/reader/) 及其 [源代码](https://github.com/MicrosoftEdge/Demos/tree/main/reader)。

若要详细了解 CSS 滚动链接动画功能，请参阅 MDN [中的@scroll时间线](https://developer.mozilla.org/en-US/docs/Web/CSS/@scroll-timeline) 。


<!-- ====================================================================== -->
## <a name="devtools---customizing-microsoft-edge-developer-tools-and-quick-feature-access"></a>DevTools - 自定义Microsoft Edge开发人员工具和快速功能访问

_发布于 2022 年 5 月 5 日。_

[![TDevTools 自定义视频的 humbnail 图像](./images/customize-devtools.png)](https://www.youtube.com/watch?v=ypRzEBYNptQ)

了解如何根据需要自定义 DevTools。

此视频介绍如何停靠或撤换 DevTools、打开新工具以及关闭不需要的工具。 它介绍如何在底部抽屉中移动工具并自定义文本大小和主题。 该视频还介绍了如何使用命令菜单键盘快捷方式快速自定义 DevTools。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-101"></a>DevTools - DevTools 101 中的新增功能

_发布于 2022 年 4 月 28 日。_

[![T101 视频中的 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-101.png)](https://www.youtube.com/watch?v=kv6Q8a9bsbA)

在 [DevTools 101](../devtools-guide-chromium/whats-new/2022/04/devtools-101.md) 的新增功能中，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="web-platform---highlight-text-on-the-web-with-the-css-custom-highlight-api"></a>Web 平台 - 使用 CSS 自定义突出显示 API 突出显示 Web 上的文本

_发布于 2022 年 4 月 28 日。_

[![TCSS 自定义突出显示 API 视频的 humbnail 图像](./images/css-custom-highlight-api.png)](https://www.youtube.com/watch?v=1qldqyT324o)

在 Web 上设置文本的样式范围非常有用，但从历史上看，这是一件复杂的事情。

新的 [CSS 自定义突出显示 API](https://www.w3.org/TR/css-highlight-api-1/) 是突出显示 Web 上的文本范围的未来。 它为 Web 开发人员提供 JavaScript 和 CSS 功能，使其更轻松、更高效地设置任意文本范围的样式。

有关详细信息，请参阅 [CSS 自定义突出显示 API：在 Web 上突出显示文本范围的未来](https://css-tricks.com/css-custom-highlight-api-early-loo/)。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-100"></a>DevTools - DevTools 100 中的新增功能

_发布于 2022 年 4 月 19 日。_

[![T100 视频中的 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-100.png)](https://www.youtube.com/watch?v=aP6d2PIU7hc)

在 [DevTools 100](../devtools-guide-chromium/whats-new/2022/03/devtools-100.md) 中的新增功能上，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-99"></a>DevTools - DevTools 99 中的新增功能

_发布于 2022 年 3 月 21 日。_

[![T99 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-99.png)](https://www.youtube.com/watch?v=Z5-tEE_cNTo)

在 [DevTools 99](../devtools-guide-chromium/whats-new/2022/03/devtools.md) 的新增功能中，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-98"></a>DevTools - DevTools 98 中的新增功能

_发布于 2022 年 2 月 23 日。_

[![T98 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-98.png)](https://www.youtube.com/watch?v=HpaRDwU_AZI)

在 [DevTools 98](../devtools-guide-chromium/whats-new/2022/03/devtools.md) 的新增功能中，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-97"></a>DevTools - DevTools 97 中的新增功能

_发布于 2022 年 2 月 1 日。_

[![T97 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-97.png)](https://www.youtube.com/watch?v=qbDLtE0a_yQ)

在 [DevTools 97](../devtools-guide-chromium/whats-new/2022/01/devtools.md) 的新增功能中，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-96"></a>DevTools - DevTools 96 中的新增功能

_发布于 2021 年 12 月 9 日。_

[![T96 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-96.png)](https://www.youtube.com/watch?v=H6dYeoGOIDk)

在 [DevTools 96](../devtools-guide-chromium/whats-new/2021/11/devtools.md) 的新增功能中，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。


<!-- ====================================================================== -->
## <a name="devtools---debug-memory-leaks-with-the-microsoft-edge-detached-elements-tool"></a>DevTools - 使用Microsoft Edge分离的元素工具调试内存泄漏

_发布于 2021 年 12 月 9 日。_

[![T分离元素视频的 humbnail 图像](./images/detached-elements.png)](https://www.youtube.com/watch?v=v2iy17ptmBk)

我们很高兴在 Microsoft Edge DevTools 中宣布新的分离元素工具，帮助你调查和解决 DOM 内存泄漏。

当应用程序的 JavaScript 代码在内存中保留越来越多的对象，而不是为浏览器释放对象以进行垃圾回收时，会发生内存泄漏。
我们与Microsoft Teams开发人员一起构建了此工具，它已帮助我们查找并修复了许多自己的网站和应用的内存泄漏。

有关详细信息，请参阅使用[分离元素工具调试 DOM 内存泄漏](../devtools-guide-chromium/memory-problems/dom-leaks.md)，并阅读相应的博客帖子使用[Microsoft Edge分离元素工具调试内存泄漏](https://blogs.windows.com/msedgedev/2021/12/09/debug-memory-leaks-detached-elements-tool-devtools/)。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-95"></a>DevTools - DevTools 95 中的新增功能

_发布于 2021 年 12 月 8 日。_

[![T95 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-95.png)](https://www.youtube.com/watch?v=JsnW0CU1l80)

在 [DevTools 95](../devtools-guide-chromium/whats-new/2021/10/devtools.md) 中的新增功能中，从 Microsoft Edge DevTools 团队了解有关我们的最新公告的详细信息。


<!-- ====================================================================== -->
## <a name="web-platform---the-eyedropper-api"></a>Web 平台 - EyeDropper API

_发布于 2021 年 11 月 22 日。_

[![T眼投影机 API 视频的 humbnail 图像](./images/eyedropper-api.png)](https://www.youtube.com/watch?v=XZUEnUbI7dE)

Microsoft Edge团队与Chromium开源项目合作指定并实施了新的 EyeDropper API。 提供 [有关问题的反馈 - WICG/眼球| github.com](https://github.com/WICG/eyedropper-api/issues)。

许多创造性的应用程序使用户能够从应用窗口的各个部分，甚至从整个屏幕中选择颜色，通常使用眼球隐喻。 通过 EyeDropper API，作者可以在 Web 上构建自定义颜色选取器时使用浏览器提供的眼滴。

有关详细信息，请参阅使用 [EyeDropper API | web.dev 和 EyeDropper API 选取屏幕上任何像素的颜色](https://web.dev/eyedropper/) [- Web API |MDN developer.mozilla.org](https://developer.mozilla.org/docs/Web/API/EyeDropper_API)。


<!-- ====================================================================== -->
## <a name="devtools---whats-new-in-devtools-94"></a>DevTools - DevTools 94 中的新增功能

_发布于 2021 年 11 月 12 日。_

[![T94 视频中 DevTools 新增功能的 humbnail 图像](./images/devtools-whatsnew-94.png)](https://www.youtube.com/watch?v=S-g1E_W9wQQ)

在 [DevTools 94](../devtools-guide-chromium/whats-new/2021/09/devtools.md) 的新增功能上，从 Microsoft Edge DevTools 团队详细了解我们的最新公告。
