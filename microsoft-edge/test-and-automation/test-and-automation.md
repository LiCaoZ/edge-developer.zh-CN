---
title: 测试并自动化Microsoft Edge
description: DevTools 协议工具、调试、配置文件浏览器。  试用实验性 API 的源试用版。  通过 1 个 API 实现跨浏览器自动化。  通过 DevTools 协议自动执行安装程序 API。  WebDriver 模拟用户交互。  webhint lint 检查错误，最佳做法。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 02/14/2022
ms.openlocfilehash: 84d62c08af3e17a0a748429e1a19d1ee2e1436c1
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433509"
---
# <a name="test-and-automation-in-microsoft-edge"></a>测试并自动化Microsoft Edge

有许多工具可以自动测试Microsoft Edge：

| 工具 | 说明 |
| --- | --- |
| 开发工具协议 | 检测、检查、调试和配置文件浏览器，包括Microsoft Edge。 |
| 源试验 | 在有限时段内在活动网站上试用实验性 API。 |
| 编剧 | Playwright 库通过单个 API 提供跨浏览器自动化。 |
| Puppeteer | 用户库提供了一个高级 API，以使用 DevTools 协议Microsoft Edge浏览器（包括浏览器）。 |
| WebDriver | 通过模拟用户Microsoft Edge自动执行测试。  提供与 JavaScript 单元测试相比的优势。 |
| webhint | 检查代码的最佳实践和常见错误，以测试并改进网站的辅助功能、性能、跨浏览器PWA兼容性和安全性。 |

这些工具如下所述。


<!-- ====================================================================== -->
## <a name="devtools-protocol"></a>开发工具协议

使用 DevTools 协议检测、检查、调试和配置文件浏览器，包括Microsoft Edge。  The Microsoft Edge DevTools Protocol matches the APIS of the Chrome DevTools Protocol.

请参阅 [DevTools 协议](devtools-protocol.md)。


<!-- ====================================================================== -->
## <a name="origin-trials"></a>源试验

可以使用源试用版在有限时段内在活动网站上试用实验性 API。  使用源试用版时，访问Microsoft Edge的网站的用户可能会运行使用实验性 API 的代码。  若要访问每个用户计算机上实验性 `edge://flags` API，你无需转到 并打开功能标志。

请参阅[使用 Microsoft Edge 中的源Microsoft Edge](../origin-trials/index.md)。


<!-- ====================================================================== -->
## <a name="playwright"></a>编剧

Playwright 库通过单个 API 提供跨浏览器自动化。  Playwright 支持跨浏览器 Web 自动化，该自动化功能常青、功能可靠且快速。

默认情况下，Playwright 以无头模式启动浏览器。  无头浏览器不显示 UI;因此，通常使用命令行 ，但是，还可以将 Playwright 配置为在 UI 中Microsoft Edge运行。

请参阅[使用 Playwright 自动执行和测试Microsoft Edge](../playwright/index.md)。


<!-- ====================================================================== -->
## <a name="puppeteer"></a>Puppeteer

用户库提供了一个高级 API，Chromium开发人员协议控制基于 Chromium 的浏览器，包括 Microsoft Edge 浏览器。

默认情况下，安装者启动无头浏览器。  无头浏览器不显示 UI，因此必须使用命令行。  还可以将安装程序配置为在无 (运行完整) Microsoft Edge。

使用 Microsoft Edge，`puppeteer-core`可以使用 启动现有浏览器安装的轻型版本的一个（如 Microsoft Edge）。

请参阅 [Puperer overview](../puppeteer/index.md)。


<!-- ====================================================================== -->
## <a name="webdriver"></a>WebDriver

通过 WebDriver，你可以Microsoft Edge用户交互来自动执行登录。  与在浏览器中运行的 JavaScript 单元测试相比，使用 WebDriver 的测试有一些优势：

*  访问在浏览器中运行的 JavaScript 不可用的功能和信息。

*  比 JavaScript 单元测试更准确地模拟用户事件或操作系统级事件。

*  在单个测试会话中管理多个窗口、选项卡和网页。

*  运行特定计算机上Microsoft Edge会话。

请参阅[使用 WebDriver 自动Microsoft Edge](../webdriver-chromium/index.md)。


<!-- ====================================================================== -->
## <a name="webhint-extension-for-visual-studio-code"></a>适用于Visual Studio Code的 webhint 扩展

使用 Webhint（一种可自定义的 Lint 工具）可改进网站的辅助功能、性能、跨浏览器PWA兼容性和安全性。  Webhint 扩展会检查代码，以检查最佳做法和常见错误。

请参阅 [webhint extension for Visual Studio Code](webhint.md)。
