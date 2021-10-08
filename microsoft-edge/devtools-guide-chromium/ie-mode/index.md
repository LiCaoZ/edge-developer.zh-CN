---
description: IE 模式和Microsoft Edge DevTools。
title: 在开发人员模式下使用 Internet Explorer工具
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/10/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， Web 开发， f12 工具， devtools， ie11， Internet Explorer 11， ie 模式
ms.openlocfilehash: 1d2f38fbc2d07f7729f1b930d4fb49d1117742ab
ms.sourcegitcommit: 0eca205728eeca1bd54b3ca34dfc81ec57cf16d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2021
ms.locfileid: "12082923"
---
# <a name="use-devtools-in-internet-explorer-mode"></a>在开发人员模式下使用 Internet Explorer工具

Internet Explorer开发人员 (开发人员工具) IE 模式Microsoft Edge集成。   IE 模式允许企业指定仅在 11 Internet Explorer工作的网站列表。  当您导航到 Microsoft Edge 中的这些网站时，Internet Explorer 11 的实例将运行并在选项卡中呈现网站。 IE 模式允许企业管理与当前与任何新式 Web 浏览器不兼容的技术的兼容性。

IE 模式中包含对以下技术的支持：

*   IE 文档模式。
*   ActiveX控件。
*   其他旧版组件。

在 IE 模式下，呈现过程基于 Internet Explorer 11。  Microsoft Edge进程管理器处理呈现过程的生命周期。  呈现过程被限制到特定网站集或应用选项卡 (生命周期) 。  当选项卡以 IE 模式呈现时，IE 模式指示器图标将显示在特定选项卡的地址栏中。

:::image type="complex" source="../media/ie-mode-badge.msft.png" alt-text="地址栏中的 IE 模式指示器图标" lightbox="../media/ie-mode-badge.msft.png":::
   地址栏中的 IE 模式指示器图标
:::image-end:::

IE 模式在 Windows 10 2019 年 5 月 (1903) 版本 1903 上可用，并且适用于所有受支持的 Windows 平台。


## <a name="open-devtools-on-a-tab-in-ie-mode"></a>在 IE 模式下打开选项卡上的 DevTools

如果管理员将网站配置为以 IE 模式Enterprise，则 IE 模式指示器图标将显示在地址栏中。  若要在 IE 模式下查看网站的文档模式，请选择地址栏中的 IE 模式指示器图标。

:::image type="complex" source="../media/ie-mode-badge-doc-mode.msft.png" alt-text="使用 IE 模式指示器图标查看文档模式" lightbox="../media/ie-mode-badge-doc-mode.msft.png":::
   使用 IE 模式指示器图标查看文档模式
:::image-end:::

如果选项卡使用 IE 模式，则选项卡具有以下限制：

*  某些 DevTools 面板不起作用，如网络和性能，**** 因为呈现**** 引擎从 Chromium 切换到 Internet Explorer 11。
*  **Inspect 元素** 在上下文菜单上不可见 (右键单击) 。
*  打开上下文菜单 (右键单击) 并选择"**查看**源启动"记事本。
*  选择 `F12` 或 `Ctrl` + `Shift` + `I` 打开开发人员工具Microsoft Edge空白实例，并显示以下消息：开发人员工具在Internet Explorer**不可用。 若要调试页面，请从 Internet Explorer 11 中打开它。**

:::image type="complex" source="../media/ie-mode-devtools.msft.png" alt-text="在 IE 模式下启动的 DevTools" lightbox="../media/ie-mode-devtools.msft.png":::
   在 IE 模式下启动的 DevTools
:::image-end:::

如果Internet Explorer不可用，若要调试 IE 模式选项卡的内容，请使用 IEChooser 打开 Internet Explorer DevTools，如下所示：

1.  在Windows中，打开"**运行**"对话框。  例如，按 `Windows logo key`  +  `R` 。
1.  输入 `%systemroot%\system32\f12\IEChooser.exe` ，然后选择"确定 **"。**
1.  在 IEChooser 中，选择"IE 模式"选项卡的条目。


## <a name="remote-debugging-in-ie-mode"></a>IE 模式下的远程调试

启动Microsoft Edge，同时从命令行界面启用远程调试。  Microsoft Visual Studio、Microsoft Visual Studio 代码和其他开发工具通常运行命令以启动Microsoft Edge。  以下命令启动Microsoft Edge将远程调试端口设置为 `9222` 。

```shell
start msedge --remote-debugging-port=9222
```

使用命令行Microsoft Edge启动 IE 模式后，IE 模式将不可用。  你仍然可以导航到网站 (或) 以其他方式显示在 IE 模式下的应用。  使用 (11) 呈现内容的网站Chromium或Internet Explorer应用。  依赖于 11 Internet Explorer的网页的某些部分ActiveX控件）可能无法正确呈现。  IE 模式指示器图标不会显示在地址栏中。

在关闭并重新启动 IE 模式之前，IE 模式Microsoft Edge。


## <a name="replace-internet-explorer-automation"></a>替换Internet Explorer自动化

如果您有一个使用 [InternetExplorer][InternetExplorerObject] 对象自动执行 Internet Explorer 11 的现有应用程序，但 Internet Explorer 11 桌面应用程序不可用，则您的应用程序将不起作用。  Internet Explorer 11 将于 2022 年 6 月 15 日停用。  有关详细信息，请导航到"Internet Explorer[上的Windows 10"Microsoft Edge"。][BlogsWindowsExperienceFutureOfIEEdge]

Microsoft Edge不支持通过 对象自动执行 IE 模式，因此，需要更新依赖此对象的应用程序，使用下面建议的备选方法 `InternetExplorer` 之一。  使用 [WebBrowser][WebBrowserControl] 控件的应用程序将继续工作，并且不受 11 Internet Explorer的影响。

如果自动化应用程序不需要 IE 模式，网站 (或应用) 内容正常运行，我们建议更新应用程序以使用 Microsoft Edge 而不是 Internet Explorer 11。  许多可用的自动化工具都Microsoft Edge，包括 WebDriver 和 Playwright。  若要详细了解如何使用 WebDriver 自动Microsoft Edge，请导航到"使用[WebDriver 自动Microsoft Edge"。][WebDriverIndex]  若要详细了解如何使用 Playwright，请导航到"使用 Playwright 自动执行和测试[Microsoft Edge"。][PlaywrightIndex]

需要 IE 模式的网站或应用 (内容) 的应用程序应使用此 `WebBrowser` 控件。  该控件使用 Internet Explorer 平台 (MSHTML/Trident) 呈现 Web 内容，即使 Internet Explorer 11 桌面应用程序不可用，该控件也将正常工作。 `WebBrowser`


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [什么是 Internet Explorer (IE) 模式？][EnterpriseWhatIsIEMode]
*  [配置 IE 模式策略][EnterpriseConfigureIEModePolicies]
*  [使用文档模式和企业模式站点列表修复 Web 兼容性问题][IEDocumentModes]


<!-- ====================================================================== -->
<!-- links -->
[PlaywrightIndex]: ../../playwright/index.md "使用 Playwright 自动执行和测试Microsoft Edge |Microsoft Edge开发人员文档"
[WebDriverIndex]: ../../webdriver-chromium/index.md "使用 WebDriver 自动Microsoft Edge |Microsoft Edge开发人员文档"
<!-- external links -->
[EnterpriseWhatIsIEMode]: /deployedge/edge-ie-mode "IE Internet Explorer (模式) 是什么？|Microsoft Edge Enterprise文档"
[EnterpriseConfigureIEModePolicies]: /deployedge/edge-ie-mode-policies "配置 IE 模式策略|Microsoft Edge Enterprise文档"
[IEDocumentModes]: /internet-explorer/ie11-deploy-guide/fix-compat-issues-with-doc-modes-and-enterprise-mode-site-list "使用文档模式和模式站点列表Enterprise修复 Web 兼容性|Internet Explorer文档"

[BlogsWindowsExperienceFutureOfIEEdge]: https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/ "Internet Explorer Windows 10的未来Microsoft Edge |Windows体验博客"

[PreviousVersionsWindowsInternetExplorerDeveloperSamplesbg182326]: /previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v%3dvs.85) "使用 F12 开发人员工具|已存档Microsoft Edge开发人员文档"

[InternetExplorerObject]: /previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752084(v=vs.85) "InternetExplorer 对象 (Windows) |已存档Microsoft Edge开发人员文档"
[WebBrowserControl]: /previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85) "WebBrowser 控件 (Internet Explorer) |已存档Microsoft Edge开发人员文档"
