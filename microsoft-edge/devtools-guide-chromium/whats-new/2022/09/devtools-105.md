---
title: DevTools (Microsoft Edge 105) 中的新增功能
description: 焦点模式：改进了 DevTools、活动栏、快速视图和改进了问题工具中可靠性的位置控制。 以及更多。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/01/2022
ms.openlocfilehash: 7b2e201c2d8269b51abf2fb78672f94b2bd70baf
ms.sourcegitcommit: f5f3e4febdef33e036f0c6946eab0f419d50d28d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2022
ms.locfileid: "12746598"
---
# <a name="whats-new-in-devtools-microsoft-edge-105"></a>DevTools (Microsoft Edge 105) 中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="test-your-pwas-protocol-handlers-from-the-application-tool"></a>从应用程序工具测试 PWA 的协议处理程序

<!-- Title: Test your PWA's protocol handlers from the Application tool -->
<!-- Subtitle: From the Manifest section of the Application tool, you can now provide custom protocols to launch your PWA. -->

在 Microsoft Edge 105 中， **应用程序** 工具现在支持测试协议处理程序。  自 Microsoft Edge 96 以来，你已能够在渐进式 Web 应用 (PWA) 的应用程序清单中定义协议处理程序。  现在，如果安装了 PWA，可以从 DevTools 中的 **应用程序工具本身** 测试这些协议。

为 PWA 打开 DevTools：

1. 打开“**应用程序**”工具。
1. 在左侧展开并选择 **应用程序** > **清单** > **协议处理程序**。
1. 在 **“协议处理程序”** 页的 **“协议处理程序** ”下拉列表中，选择要测试的协议。
1. 在文本框中，输入要测试的 URL 或终结点。
1. 单击 **“测试协议** ”按钮。

**应用程序工具**将尝试使用指定的协议和 URL 启动 PWA。  浏览器请求打开应用程序的权限，然后提示你确认是否要处理要启动的协议和应用。 如果授予权限，应用将使用指定的内容打开。

![协议处理程序](./devtools-105-images/protocol-handler.png)

另请参阅：

* [测试渐进式 Web 应用 (PWA) 协议处理](../../../progressive-web-apps/protocol-handlers.md)
* [处理渐进式Web 应用中的协议](../../../../progressive-web-apps-chromium/how-to/handle-protocols.md)


<!-- ====================================================================== -->
## <a name="edit-and-resend-network-requests-more-reliably-in-the-network-console-tool"></a>在网络控制台工具中更可靠地编辑和重新发送网络请求

<!-- Title: Edit and resend network requests more reliably in the Network Console tool  -->
<!-- Subtitle: Modify and resend network requests that have been logged in the Network tool with the Network Console tool. -->

以前在 Microsoft Edge 中，从网络工具选择 **“编辑并重新发送** ”网络请求可能无法可靠地打开 **网络控制台** 工具，并使用请求中的值对其进行预填充。

在 Microsoft Edge 105 中，此问题已在默认 UI 中修复。  在将来的版本中，焦点 [模式](../../../experimental-features/focus-mode.md) 下也会修复此问题。  **现在，编辑并重新填充****网络控制台**工具，并预填充要重新发送的网络请求的值。  在从 **网络控制台** 工具发送请求之前，可以继续修改这些值。  感谢你向我们发送有关此问题的反馈！

右键单击要更改和重新发送的网络请求，然后选择 **“编辑”和“重新发送**”：

![编辑和重新发送](./devtools-105-images/edit-and-resend.png)

在 **网络控制台**中编辑网络请求信息，然后单击“ **发送** ”按钮：

![网络控制台编辑和发送](./devtools-105-images/networkconsole-edit.png)

另请参阅：
* 从 Compose 中的[网络工具开始](../../../network-console/network-console-tool.md#starting-from-the-network-tool)，_使用网络控制台工具发送 Web API 请求_。


<!-- ====================================================================== -->
## <a name="focus-mode-improved-location-controls-for-devtools-activity-bar-and-quick-view"></a>焦点模式：改进了 DevTools、活动栏和快速视图的位置控制

<!-- Title: Focus Mode: Improved location controls for DevTools, Activity Bar, and Quick View -->
<!-- Subtitle: Focus Mode: Improved location controls for DevTools, Activity Bar, and Quick View. -->

在 Microsoft Edge 105 中， [在焦点模式](../../../experimental-features/focus-mode.md)下对位置控件进行了多项改进，包括用于更改 **快速视图**方向的新选项。

**自定义和控制 DevTools** (**...**) 菜单现在直接包含用于设置 DevTools 停靠位置的按钮，而不是需要打开子菜单。  **“停靠位置**”图标现在具有更大的对比度，现在突出显示了当前选择的 **“停靠位置**”按钮。

此菜单现在还直接包含用于设置和指示 **活动栏** 显示位置的按钮，而不是使用子菜单。

在早期版本的 Microsoft Edge 中选择焦点模式下的停靠位置：

![之前的“停靠位置”菜单图标](./devtools-105-images/before-docking-menu.png)

在 Microsoft Edge 105 中选择焦点模式下的停靠位置：

![之后的“停靠位置”菜单图标](./devtools-105-images/after-docking-menu.png)

现在也可以更改 **快速视图** 面板的方向。  若要垂直而不是水平显示 **快速视图** ，请单击 **“停靠快速视图”右侧** 按钮：

![右侧停靠快速视图](./devtools-105-images/quickview-console.png)

若要将 **快速视图** 返回到水平方向，请单击 **“停靠快速视图到底部** ”按钮：

![将快速视图停靠到底部](./devtools-105-images/dock-quick-view-bottom.png)

若要在任一方向最小化 **快速视图** ，请单击“ **折叠快速视图** ”按钮，或按下 `Esc`：

![最大程度地减少快速视图](./devtools-105-images/focus-mode-improved-location-controls.png)

另请参阅：
* [使用专注模式简化开发工具](../../../experimental-features/focus-mode.md)


<!-- ====================================================================== -->
## <a name="fix-search-in-the-sources-and-network-tools-now-works-as-expected-in-focus-mode"></a>修复：在“源”和“网络”工具中搜索现在按预期在焦点模式下工作

<!-- Title: Fix: Search in the Sources and Network tools now works as expected in Focus Mode  -->
<!-- Subtitle: Try Focus Mode, a new, more simplified, and streamlined UI for DevTools! -->

在早期版本的 Microsoft Edge 中，焦点模式试验未在 **“网络**”工具或 **“源**”工具**中的所有文件功能中**正确显示**搜索**功能。  在 Microsoft Edge 105 中，这些问题已得到解决。

现在可以通过搜索图标在 **网络** 工具中 **搜索** ：

![网络搜索](./devtools-105-images/networking-search.png)

若要在 **“源** ”工具中的所有文件中搜索，请在 **“页面** ”部分右键单击 **顶部** 窗口或任何域，然后 **在所有文件中选择“搜索**”：

![网络搜索全部](./devtools-105-images/sources-search-all-files.png)

另请参阅：
* [使用专注模式简化开发工具](../../../experimental-features/focus-mode.md)
* 在 _“检查网络活动_”中[搜索网络标头和响应](../../../network/index.md#search-network-headers-and-responses)。
* [使用搜索工具查找页面的源文件](../../../search/search-tool.md)


<!-- ====================================================================== -->
## <a name="improved-reliability-in-the-issues-tool"></a>改进了问题工具中的可靠性

<!-- Title: Improved reliability in Issues tool -->
<!-- Subtitle: A bug that sometimes resulted in issues not appearing has been fixed. -->

在早期版本的 Microsoft Edge 中，有一个 bug 导致问题未出现在 **“问题** ”工具中。  此 bug 已在 Microsoft Edge 105 中修复。

另请参阅：

* [使用问题工具查找和修复问题](../../../issues/index.md)


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge 105 还包括Chromium项目的以下更新：

* [在运行时附加 Wasm 调试信息](https://developer.chrome.com/blog/new-in-devtools-105/#wasm)
* [在调试期间支持实时编辑](https://developer.chrome.com/blog/new-in-devtools-105/#live-edit)
* [在“样式”窗格中的规则中查看和编辑@scope](https://developer.chrome.com/blog/new-in-devtools-105/#scope)
* [源图改进](https://developer.chrome.com/blog/new-in-devtools-105/#sourcemaps)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- > [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New in DevTools (Chrome 105)](https://developer.chrome.com/blog/new-in-devtools-105) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google). -->


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- [![Creative Commons License.](../../../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0). -->
