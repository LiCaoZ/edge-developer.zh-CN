---
title: 使用 Microsoft Edge 开发网页版
description: 使用 Microsoft Edge DevTools、Microsoft Edge 扩展、渐进式Web 应用、WebDriver 自动化、WebView2 等为 Web 开发。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 02/14/2022
ms.openlocfilehash: e37250e24e730d64362e0fcbcb47cad82b830210
ms.sourcegitcommit: 96614dbe082df25981cb375fa240eb4bc9b028cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2022
ms.locfileid: "12760886"
---
# <a name="develop-for-the-web-with-microsoft-edge"></a>使用 Microsoft Edge 开发网页版

使用 Microsoft Edge DevTools、Microsoft Edge 扩展、渐进式Web 应用、WebDriver 自动化、WebView2 等为 Web 开发。


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools"></a>Microsoft Edge 开发工具
<!-- ====================================================================== -->
<!-- keep sync'd:
* [Overview of DevTools](devtools-guide-chromium/overview.md) - intro section
* [Microsoft Edge DevTools](../develop-web-microsoft-edge.md#microsoft-edge-devtools) in _Develop for the web with Microsoft Edge_
-->

Microsoft Edge 浏览器附带内置 Web 开发工具，称为 Microsoft Edge DevTools。  DevTools 是一组 Web 开发工具，显示在浏览器中呈现的网页旁边。  DevTools 提供了一种用于检查和调试网页和 Web 应用的强大方法。  甚至可以在 DevTools 环境中编辑源文件并创建网站项目。

使用 DevTools 可以执行以下操作：

*  使用具有可视界面的 实时工具检查、调整和更改网页中元素的样式。  检查浏览器存储内容以构造网页的位置，包括`.html``.css``.js`文件格式和`.png`文件格式。

*  模拟网页在不同设备上的行为方式，并模拟具有不同网络条件的移动环境。  检查网络流量并查看问题的位置。

*  使用断点调试和实时控制台 调试JavaScript。  查找 Web 应用的内存问题和呈现问题。

*  查找产品中的辅助功能、性能、兼容性和安全问题，并使用 DevTools 修复找到的辅助功能问题。

*  使用开发环境将 DevTools 中的更改与文件系统和 Web 同步。

<!-- /keep sync'd -->

请参阅 [DevTools 概述](devtools-guide-chromium/overview.md)。


<!-- ====================================================================== -->
## <a name="microsoft-edge-extensions"></a>Microsoft Edge 扩展
   
为 Microsoft Edge 创建扩展，以添加或修改浏览器的功能。  扩展可改进浏览器体验，从而提供对目标受众非常重要的专用函数。

如果你的想法或产品基于特定 Web 浏览器或特定网页功能的改进，则可以创建 Microsoft Edge 扩展。 配套体验的示例包括广告拦截器和密码管理器。

Microsoft Edge 扩展的结构与常规 Web 应用类似，通常包括：

*  包含基本平台信息的应用程序清单 JSON 文件。
*  一个 JavaScript 文件，用于定义浏览器扩展的行为。
*  定义用户界面的 HTML 和 CSS 文件。

请参阅 [Microsoft Edge 扩展概述](extensions-chromium/index.md)。


<!-- ====================================================================== -->
## <a name="progressive-web-apps"></a>渐进式 Web 应用

渐进式Web 应用使用开放式 Web 技术来提供跨平台互操作性。  它们的工作方式类似于支持平台上的本机应用，并像其他浏览器上的常规网站一样工作。

渐进式Web 应用结合了最好的 Web 和已编译的应用，为用户提供类似应用的体验，为其设备自定义。  渐进式 Web 应用是一个逐渐增强的网站，可以像安装的本机应用一样在支持平台上运行，同时像其他浏览器上的常规网站一样运行。

渐进式Web 应用的跨平台开发成本比编译的应用要低得多，这些应用需要每个平台的特定代码库，例如针对 Android、iOS 和每个桌面操作系统的单独代码库。

请参阅[渐进式Web 应用 (PVA) 概述](progressive-web-apps-chromium/index.md)。


<!-- ====================================================================== -->
## <a name="webview2"></a>WebView2

WebView2 控件由 Microsoft Edge 提供支持，使你可以在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) 。  将 Web 平台的普遍性与本机平台的完整功能相结合。

![应用示意图，其中本机 UI 区域位于左上角，WebView2 UI 区域位于右上角底部。](media/webview-panels.png)

下图显示了从最大覆盖范围到最大功率的应用范围：

![应用的范围，从最大覆盖范围但更少的功率，到最佳混合，最大功率但较少覆盖范围。](media/web-hybrid-native.png)
<!-- png copy used in main article is named "web-native.png" -->

位于范围中间的混合应用使开发人员能够体验两种优势：Web 平台的通用性和强大性，以及本机平台的强大功能和全部功能。

请参阅 [Microsoft Edge WebView2 简介](webview2/index.md)。


<!-- ====================================================================== -->
## <a name="test-and-automation"></a>测试和自动化

以下是在 Microsoft Edge 中自动执行测试的工具：

*  **DevTools 协议** 用于检测、检查、调试和配置文件浏览器。
*  使用 **源试验** 来尝试实验性 API。
*  **Playwright** 通过单个 API 提供跨浏览器自动化。
*  **Puppeteer** 的 API 通过 DevTools 协议控制 Microsoft Edge。
*  **WebDriver** 模拟用户与 Microsoft Edge 的交互。
*  **webhint** Linting 检查代码是否存在错误和最佳做法。

请参阅 [Microsoft Edge 中的测试和自动化](test-and-automation/test-and-automation.md)。


<!-- ====================================================================== -->
## <a name="web-platform"></a>Web 平台

为 Web 平台开发网站和产品的注意事项包括：

*  测试未来可能影响网站与 Microsoft Edge 兼容性的更改。
*  将用户从 Internet Explorer 移动到 Microsoft Edge。
*  在 Microsoft Edge 中配置跟踪防护。
*  从网站检测 Microsoft Edge。
*  自定义“密码显示”按钮。
*  使用User-Agent客户端提示检测Windows 11。

请参阅 [Web 平台](web-platform/web-platform.md)。


<!-- ====================================================================== -->
## <a name="microsoft-edge-ide-integration"></a>Microsoft Edge IDE 集成

Microsoft 工具的各种功能提供使用 Microsoft Edge、Visual Studio Code 和 Visual Studio 进行开发的集成，以开发在 Microsoft Edge 中使用和使用完全集成的产品、网页和 Web 应用。

请参阅 [Microsoft Edge IDE 集成](visual-studio-code/ide-integration.md)。


<!-- ====================================================================== -->
## <a name="accessibility-in-microsoft-edge"></a>Microsoft Edge 中的辅助功能

通过 Microsoft Edge 及其工具生态系统中广泛的辅助功能，可靠地支持开发网页、Web 应用和已启用 Web 的产品。

请参阅 [Microsoft Edge 中的辅助功能](accessibility/index.md)。


<!-- leaf node (article; omit per PR review) -->
<!-- ====================================================================== -->
<!-- ## Privacy whitepaper

The Microsoft Edge _browser privacy promise_ provides you with protection, transparency, control, and respect.  Microsoft Edge has many features and services associated with privacy.  This whitepaper explains how your data is used, how to control the different features, and how to manage your collected data.

See [Microsoft Edge Privacy Whitepaper](privacy-whitepaper/index.md).
-->


<!-- leaf node (article; omit per PR review) -->
<!-- ====================================================================== -->
<!-- ## The Web We Want initiative

The Web We Want initiative is a cross-browser, open initiative focused on identifying missing features and functionalities in the web platform for potential development as web standards or browser features.  Let browser vendors and standards groups know what you think is missing from the web platform.

If you build for the web, you inevitably run into problems.  Perhaps there's no way to achieve an aspect of your design with CSS, or it may require an incredible amount of experimenting with CSS.  Maybe there's a device feature you want to tap into using JavaScript, or there's a needed Developer Tools feature that can make your job easier.

See [The Web We Want initiative](web-we-want/index.md).
-->


<!-- ============================================================================================================================================ -->
<!-- ============================================================================================================================================ -->
## <a name="how-to-use-this-documentation"></a>如何使用此文档

以下是使用 Microsoft Learn 文档 UI 的提示。


<!-- ====================================================================== -->
## <a name="zoom-an-image-in-an-article"></a>缩放文章中的图像

若要查看屏幕截图或图表的详细信息，请参阅：

1. 右键单击该图像，然后 **在新选项卡中选择“打开图像**”。

1. 关闭图像选项卡以返回到文章。

<!-- ====================================================================== -->

## <a name="look-up-key-words-and-terms-in-filter-by-title-text-box"></a>在“按标题筛选”文本框中查找关键字词和术语

“按 **标题** 筛选”的多用途文本框支持：

* 导航 TOC)  (目录。
* 关键字的索引词查找。
* 文档的全文搜索。

在左上角 **的“按标题筛选”** 框中，输入要查找的术语或关键字：

![用于导航目录、搜索文档和关键字的索引字词查找的多用途“按标题筛选”文本框。](media/filter-by-title-ui.png)

如果找不到所需文章，请 **在所有 Microsoft Edge 文档中选择“_搜索术语_”**：

![如果找不到标题字词或索引词，则会为全文搜索所有 Microsoft Edge 文档提供一个选项。](media/full-text-search-fallback.png)

全文搜索页最初搜索所有 _Microsoft Edge_ 文档。  或者，单击 **“查看所有结果** ”链接以进行更广泛的搜索：

![全文搜索页最初搜索所有 Microsoft Edge 文档，也可以单击链接“查看所有结果”以进行更广泛的搜索。](media/full-text-search-page.png)

<!-- ====================================================================== -->

## <a name="provide-feedback-or-report-issues-in-the-microsoft-edge-developer-documentation"></a>在 Microsoft Edge 开发人员文档中提供反馈或报告问题

若要提供反馈或输入问题，

* [联系 Microsoft Edge 开发工具团队](devtools-guide-chromium/contact.md)
* [联系 Microsoft Edge 扩展支持](extensions-chromium/publish/contact-extensions-team.md)
* [联系 WebView2 团队](webview2/contact.md)

若要提交和查看文档特定页面的反馈，请单击页面底部的“ **此页** ”按钮。
