---
description: 轻松在 Web 上搜索控制台错误消息字符串，Visual Studio Code 的 DevTools 扩展现在具有最新的工具和主题支持，断点图标现在在使用 Visual Studio Code 主题时显示，并且可以使用键盘导航到"更多工具"按钮。
title: 'DevTools 94 (Microsoft Edge中的新增) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/03/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 2a079469a50aad83b388ff7401de12087e7ede4e
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12140793"
---
# <a name="whats-new-in-devtools-microsoft-edge-94"></a>DevTools 94 (Microsoft Edge中的新增) 

[!INCLUDE [note about What's New announcements from the Microsoft Edge DevTools team](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="search-for-console-errors-on-the-web"></a>搜索 Web 上的控制台错误

<!-- Title: Quickly debug console errors with our new integrated search feature -->
<!-- Subtitle: Now you can quickly search for console errors directly from the Console. -->

在 DevTools **中** ，在 Web 中搜索控制台错误。  在 **控制台中**，许多错误现在在 **"Web"** 按钮上显示"搜索此消息"，显示为放大镜。  当您选择" **在 Web 上搜索此消息** "按钮时，将在浏览器中打开一个新选项卡，并显示错误的搜索结果。

有关详细信息，请导航到["从控制台查找 Web 上的错误消息"。][LookupErrorsWebFromConsole]

:::image type="complex" source="../../media/2021/09/search-console-icon.msft.png" alt-text="**Console 中错误的&quot;在 Web 上搜索此消息&quot;按钮" lightbox="../../media/2021/09/search-console-icon.msft.png":::
   控制台 **出错时"在 Web** 上搜索此消息" **按钮**
:::image-end:::


<!-- ====================================================================== -->
## <a name="devtools-extension-for-visual-studio-code-includes-the-latest-tools-theme-support-and-helpful-links"></a>适用于开发人员的 DevTools Visual Studio Code包括最新的工具、主题支持和有用链接

<!-- Title: Microsoft Edge DevTools for Visual Studio Code now supports themes and uses the most recent codebase -->
<!-- Subtitle: The Microsoft Edge DevTools extension for Visual Studio Code now uses the same version of the Developer Tools as your Microsoft Edge browser. We also added ways to learn more and for you to tell us what we could do better from within Visual Studio Code. -->

在最新版本的 Microsoft Edge DevTools 扩展中Visual Studio Code我们发布了以下更新或新功能。
*  共享用于基于浏览器的 DevTools 的相同代码库。
*  支持随主题一起Visual Studio Code。
*  在"**工具"** 边栏中Microsoft Edge"有用链接"部分，并添加"文档"、"**报告**Bug"和"**请求功能"按钮**。 **** ****
*  在"**工具** () "窗格中添加"关闭Microsoft Edge"按钮，以关闭扩展 `X` ****  >  **** 打开的浏览器。
*  添加对与远程工作区的 JavaScript 调试器连接的支持。

有关详细信息，请导航到 Microsoft Edge [DevTools 扩展Visual Studio Code。][EdgeDevToolsExtensionForVSCode]

:::image type="complex" source="../../media/2021/09/devtools-extension-dark-theme.msft.png" alt-text="内部运行的扩展Visual Studio Code，与主题的深色主题Visual Studio Code，以及新的&quot;有用链接&quot;边栏" lightbox="../../media/2021/09/devtools-extension-dark-theme.msft.png":::
   内部运行的扩展Visual Studio Code、匹配主题的深色Visual Studio Code以及新的"**有用**链接"边栏
:::image-end:::

还支持Visual Studio Code浅色主题。

:::image type="complex" source="../../media/2021/09/devtools-extension-light-theme.msft.png" alt-text="内部运行的扩展Visual Studio Code，与主题的浅色主题Visual Studio Code，以及新的&quot;有用链接&quot;边栏" lightbox="../../media/2021/09/devtools-extension-light-theme.msft.png":::
   内部运行的扩展Visual Studio Code，与主题的浅色Visual Studio Code和新的"**有用**链接"边栏匹配
:::image-end:::


<!-- ====================================================================== -->
## <a name="breakpoint-icons-are-now-displayed-when-using-visual-studio-code-themes"></a>断点图标现在在使用主题时Visual Studio Code显示

<!-- Title: Breakpoint icons are now displayed when using themes from Visual Studio Code -->
<!-- Subtitle: Setting, removing, and viewing breakpoints is now easier in Microsoft Edge. -->

在 Microsoft Edge 版本 93 中，可以将 Visual Studio Code 中使用的主题应用到 DevTools 扩展。  有关此功能详细信息，请导航到将 [颜色主题应用到 DevTools][ApplyColorThemesToDevTools]。

以前，在 DevTools Visual Studio Code主题时，源工具中代码左边距上的断点图标不会显示。 ****  从 Microsoft Edge 94 开始，断点图标现在按预期方式显示。

若要了解有关使用断点调试 JavaScript 代码的信息，请导航到如何在[DevTools][PauseCodeWithBreakpoints]中暂停包含断点Microsoft Edge代码。

:::image type="complex" source="../../media/2021/09/breakpoint-icons-displayed-in-vs-code-themes.msft.png" alt-text="断点图标现在在使用主题时Visual Studio Code显示" lightbox="../../media/2021/09/breakpoint-icons-displayed-in-vs-code-themes.msft.png":::
   断点图标现在在使用主题时Visual Studio Code显示
:::image-end:::


<!-- ====================================================================== -->
## <a name="navigate-to-the-more-tools-button-with-the-keyboard"></a>使用键盘导航到"更多工具"按钮

<!-- Title: Use the arrow keys to navigate to the + button to open more tools -->
<!-- Subtitle: To open more tools, we have improved keyboard accessibility using the arrow keys on the main DevTools toolbar. -->

以前，当工具栏具有焦点时，你**** 无法使用键盘上的箭头键导航到 `+` DevTools () 工具"按钮。  使用箭头键时，到达工具栏中的最后一个工具后，焦点将循环回第一个工具，或显示"更多 **选项卡"菜单** 。

从 Microsoft Edge版本 93 开始，**** 当焦点位于工具栏上时，可以使用箭头键选择"更多选项卡" () "按钮和"更多工具" `>>` 按钮。 ****

若要详细了解如何使用键盘导航 DevTools，请导航Microsoft Edge[开发人员工具键盘快捷方式][DevToolsKeyboardShortcuts]。

:::image type="complex" source="../../media/2021/09/nav-to-more-tools-button-with-keyboard.msft.png" alt-text="使用箭头键将焦点放在 **更多选项卡** 或 **更多工具** 按钮上" lightbox="../../media/2021/09/nav-to-more-tools-button-with-keyboard.msft.png":::
   使用箭头键将焦点放在"更多选项卡 **"或** " **更多工具"** 按钮上
:::image-end:::


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows、Linux 或 macOS，请考虑使用 [ Microsoft Edge 预览频道][MicrosoftEdgePreviewChannels]作为默认开发浏览器。  预览频道使你能够访问最新的 DevTools 功能。


<!-- ====================================================================== -->
<!-- links -->
[EdgeDevToolsExtensionForVSCode]: ../../../../visual-studio-code/microsoft-edge-devtools-extension.md "Microsoft Edge适用于开发人员的 DevTools Visual Studio Code |Microsoft Docs"
[LookupErrorsWebFromConsole]: ../../../console/index.md#look-up-error-messages-on-the-web-from-the-console "从控制台查找 Web 上的错误消息 - 使用控制台|Microsoft Docs"
[DevToolsKeyboardShortcuts]: ../../../shortcuts/index.md "Microsoft Edge DevTools 键盘快捷方式 | Microsoft Docs"
[ApplyColorThemesToDevTools]: ../../../customize/theme.md "将颜色主题应用到 DevTools |Microsoft Docs"
[PauseCodeWithBreakpoints]: ../../../javascript/breakpoints.md "如何在 Microsoft Edge 开发工具中使用断点暂停代码 | Microsoft Doc"

<!-- external links -->
[MicrosoftEdgePreviewChannels]: https://www.microsoftedgeinsider.com/download "Microsoft Edge 预览频道"

[VisualstudioMarketplaceMsEdgedevtoolsVscodeEdgeDevtools]: https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools "Microsoft Edge Developer Tools for Visual Studio Code | Visual Studio Marketplace"


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/new-in-devtools-94) ，由 [Jecelyn Yeen][JecelynYeen] 和开发人员 (Chrome DevTools) 。

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[JecelynYeen]: https://developers.google.com/web/resources/contributors#jecelynyeen
