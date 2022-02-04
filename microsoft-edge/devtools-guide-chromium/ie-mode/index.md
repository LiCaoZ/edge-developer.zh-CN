---
title: 在 Internet Explorer 模式（IE 模式）中使用开发工具
description: 在 Microsoft Edge 模式下使用 Internet Explorer DevTools (IE 模式) 。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/10/2021
---
# <a name="use-devtools-in-internet-explorer-mode-ie-mode"></a>在 Internet Explorer 模式（IE 模式）中使用开发工具

Internet Explorer开发人员 (集成后) IE 模式Microsoft Edge IE 模式。   IE 模式允许企业指定仅在 11 Internet Explorer的网站列表。 当您导航到 Microsoft Edge 中的这些网站时，Internet Explorer 11 的实例将运行并在选项卡中呈现网站。

IE 模式允许企业管理与当前与任何新式 Web 浏览器不兼容的技术的兼容性。

IE 模式中包含对以下技术的支持：
*  IE 文档模式。
*  ActiveX控件。
*  其他旧版组件。

在 IE 模式下，呈现过程基于 Internet Explorer 11。 Microsoft Edge进程管理器处理呈现过程的生命周期。  呈现过程被限制到特定网站集或应用选项卡 (生命周期) 。  当选项卡以 IE 模式呈现时，IE 模式指示器图标将显示在特定选项卡的地址栏中。

:::image type="content" source="../media/ie-mode-badge.msft.png" alt-text="地址栏中的 IE 模式指示器图标。" lightbox="../media/ie-mode-badge.msft.png":::

IE 模式在 2019 年 5 Windows 10 1903 (Update) 上可用，并且适用于所有受支持的 Windows 平台。


<!-- ====================================================================== -->
## <a name="open-devtools-on-a-tab-in-ie-mode"></a>在 IE 模式下打开选项卡上的 DevTools

如果 IE 管理员已配置网站以在 IE 模式下Enterprise，则地址栏中将显示 IE 模式指示器图标。  若要在 IE 模式下查看网站的文档模式，请选择地址栏中的 IE 模式指示器图标。

:::image type="content" source="../media/ie-mode-badge-doc-mode.msft.png" alt-text="使用 IE 模式指示器图标查看文档模式。" lightbox="../media/ie-mode-badge-doc-mode.msft.png":::

如果选项卡使用 IE 模式，则选项卡具有以下限制：

*  某些 DevTools 面板不起作用，如网络和性能，因为呈现**** 引擎从 **** Chromium 切换到 Internet Explorer 11。

*  **Inspect** 元素在右键单击菜单上不可见。

*  右键单击并选择"查看**源**"将启动记事本。

*  按`F12`或`Ctrl`++`Shift``I`打开 DevTools Microsoft Edge空白实例，并显示以下消息：开发人员工具在Internet Explorer**不可用。 若要调试页面，请从 11 Internet Explorer页面。**

:::image type="content" source="../media/ie-mode-devtools.msft.png" alt-text="在 IE 模式下启动的 DevTools。" lightbox="../media/ie-mode-devtools.msft.png":::

如果Internet Explorer不可用，若要调试 IE 模式选项卡的内容，请使用 IEChooser 打开 Internet Explorer DevTools，如下所示：

1. 在Windows中，打开"**运行**"对话框。  例如，按 `Windows logo key` + `R`。

1. 输入 `%systemroot%\system32\f12\IEChooser.exe`，然后单击"确定 **"**。

1. 在 IEChooser 中，选择"IE 模式"选项卡的条目。


<!-- ====================================================================== -->
## <a name="remote-debugging-in-ie-mode"></a>IE 模式下的远程调试

启动Microsoft Edge，同时从命令行界面启用远程调试。  Microsoft Visual Studio、Microsoft Visual Studio 代码和其他开发工具通常运行命令以启动Microsoft Edge。  以下命令启动Microsoft Edge将远程调试端口设置为 。`9222`

```shell
start msedge --remote-debugging-port=9222
```

使用命令行Microsoft Edge启动 IE 模式后，IE 模式将不可用。  你仍然可以导航到网站 (或) 以其他方式显示在 IE 模式下的应用。  网站 (或) 内容使用 Chromium 呈现，Internet Explorer 11。 依赖于 11 Internet Explorer的网页的某些部分ActiveX控件）可能无法正确呈现。  IE 模式指示器图标不会显示在地址栏中。

在关闭并重新启动 IE 模式之前，IE 模式Microsoft Edge。


<!-- ====================================================================== -->
## <a name="replace-internet-explorer-automation"></a>替换Internet Explorer自动化

如果现有应用程序使用 [InternetExplorer](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752084(v=vs.85)) 对象自动执行 Internet Explorer 11，但 Internet Explorer 11 桌面应用程序不可用，则应用程序将不起作用。  Internet Explorer 11 将于 2022 年 6 月 15 日停用。  请参阅[Internet Explorer Windows 10中Microsoft Edge](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/)。

Microsoft Edge不支持通过 对象自动执行 IE `InternetExplorer` 模式，因此，将需要使用下面建议的备选方法之一更新依赖此对象的应用程序。  使用 [WebBrowser](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)) 控件的应用程序将继续工作，并且不受 11 Internet Explorer的影响。

如果自动化应用程序不需要 IE 模式，网站 (或应用) 内容正常运行，我们建议更新应用程序以使用 Microsoft Edge 而不是 Internet Explorer 11。 许多可用的自动化工具都Microsoft Edge，包括 WebDriver 和 Playwright。

*  若要详细了解如何使用 WebDriver 自动Microsoft Edge，请参阅使用 [WebDriver 自动Microsoft Edge](../../webdriver-chromium/index.md)。
*  若要详细了解如何使用 Playwright，请参阅使用 [Playwright](../../playwright/index.md) 自动执行和测试 Microsoft Edge。

需要 IE 模式的网站或应用 (内容) 的应用程序应使用此 `WebBrowser` 控件。  `WebBrowser`该控件使用 Internet Explorer 平台 (MSHTML/Trident) 呈现 Web 内容，即使 Internet Explorer 11 桌面应用程序不可用，该控件也将正常工作。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [什么是 Internet Explorer (IE) 模式?](/deployedge/edge-ie-mode)
*  [配置 IE 模式策略](/deployedge/edge-ie-mode-policies)
*  [使用文档模式和企业模式站点列表修复 Web 兼容性问题](/internet-explorer/ie11-deploy-guide/fix-compat-issues-with-doc-modes-and-enterprise-mode-site-list)
