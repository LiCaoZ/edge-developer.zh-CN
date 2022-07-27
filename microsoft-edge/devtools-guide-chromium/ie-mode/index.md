---
title: 在 Internet Explorer 模式（IE 模式）中使用开发工具
description: 在 Internet Explorer 模式 (IE 模式) 下使用 Microsoft Edge 开发工具。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/10/2021
ms.openlocfilehash: e8f19374ada5f33654da92783dd553ff4742f473
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12552690"
---
# <a name="use-devtools-in-internet-explorer-mode-ie-mode"></a>在 Internet Explorer 模式（IE 模式）中使用开发工具

Internet Explorer 模式 (IE 模式) 与 Microsoft Edge 开发工具集成。   IE 模式允许企业指定仅在 Internet Explorer 11 中工作的网站列表。 在 Microsoft Edge 中导航到这些网站时，Internet Explorer 11 实例将运行并在选项卡中呈现该网站。

IE 模式允许企业管理当前与任何现代 Web 浏览器不兼容的技术的兼容性。

IE 模式中包含对以下技术的支持：
*  IE 文档模式。
*  ActiveX 控件。
*  其他旧组件。

在 IE 模式下，呈现过程基于 Internet Explorer 11。 Microsoft Edge 进程管理器处理呈现过程的生存期。  呈现过程受限于特定站点 (或应用) 选项卡的生存期。  当选项卡以 IE 模式呈现时，IE 模式指示器图标将显示在特定选项卡的地址栏中。

![地址栏中的 IE 模式指示器图标。](../media/ie-mode-badge.msft.png)

IE 模式在 Windows 10 版本 1903（2019 年 5 月更新）上可用，并且即将在所有受支持的 Windows 平台上推出。


<!-- ====================================================================== -->
## <a name="open-devtools-on-a-tab-in-ie-mode"></a>在 IE 模式下的选项卡上打开开发工具

如果企业管理员已将网站配置为以 IE 模式显示，则 IE 模式指示器图标将显示在地址栏中。  若要在 IE 模式下查看网站的文档模式，请在地址栏中选择 IE 模式指示器图标。

![使用 IE 模式指示器图标查看文档模式。](../media/ie-mode-badge-doc-mode.msft.png)

如果选项卡使用 IE 模式，则该选项卡具有以下限制：

*  某些开发工具面板不起作用，例如“**网络**”和“**性能**”，因为呈现引擎从 Chromium 切换到 Internet Explorer 11。

*  “**检查元素**”在右键单击菜单上不可见。

*  右键单击，然后选择“**查看源**”启动记事本。

*  按“`F12`”或“`Ctrl`+`Shift`+`I`”打开 Microsoft Edge 开发工具的空白实例，并显示以下消息：**开发人员工具在 Internet Explorer 模式下不可用。若要调试该页面，请在 Internet Explorer 11 中将其打开。**

![在 IE 模式下已启动开发工具。](../media/ie-mode-devtools.msft.png)

如果 Internet Explorer 在计算机上不可用，若要调试 IE 模式选项卡的内容，请使用 IEChooser 打开 Internet Explorer 开发工具，如下所示：

1. 在 Windows 中，打开“**运行**”对话框。  例如，按“`Windows logo key` + `R`”。

1. 输入“`%systemroot%\system32\f12\IEChooser.exe`”，然后单击“**确定**”。

1. 在 IEChooser 中，选择“IE 模式”选项卡的条目。


<!-- ====================================================================== -->
## <a name="remote-debugging-in-ie-mode"></a>IE 模式下的远程调试

在命令行界面打开远程调试的情况下启动 Microsoft Edge。  Microsoft Visual Studio、Microsoft Visual Studio 代码和其他开发工具通常运行命令来启动 Microsoft Edge。  以下命令启动 Microsoft Edge，并将远程调试端口设置为 `9222`。

```shell
start msedge --remote-debugging-port=9222
```

使用命令行参数启动 Microsoft Edge 后，IE 模式不可用。  仍可导航到以 IE 模式显示的网站 (或应用)。  网站 (或应用) 内容使用 Chromium 呈现，而不是 Internet Explorer 11。 依赖 Internet Explorer 11 的部分网页 (如 ActiveX 控件) 可能无法正确呈现。  IE 模式指示器图标不会显示在地址栏中。

在关闭并重启 Microsoft Edge 之前，IE 模式仍然不可用。


<!-- ====================================================================== -->
## <a name="replace-internet-explorer-automation"></a>替换 Internet Explorer 自动化

如果现有应用程序使用 [InternetExplorer](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752084(v=vs.85)) 对象自动执行 Internet Explorer 11，但 Internet Explorer 11 桌面应用程序不可用，则应用程序将不起作用。  Internet Explorer 11 将于 2022 年 6 月 15 日停用。  请参阅 [Windows 10 上 Internet Explorer 的未来在 Microsoft Edge 中](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/)。

Microsoft Edge 不支持通过 `InternetExplorer` 对象自动执行 IE 模式，因此需要使用下面推荐的替代方法之一更新依赖于此对象的应用程序。  使用 [WebBrowser](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)) 控件的应用程序将继续工作，并且不会受到删除 Internet Explorer 11 的影响。

如果自动化应用程序不需要 IE 模式来使网站 (或应用) 内容正常运行，建议更新应用程序以使用 Microsoft Edge 而不是 Internet Explorer 11。 许多可用的自动化工具支持 Microsoft Edge，包括 WebDriver 和 Playwright。

*  若要了解有关使用 WebDriver 自动执行 Microsoft Edge 的详细信息，请参阅 [使用 WebDriver 自动执行Microsoft Edge](../../webdriver-chromium/index.md)。
*  若要了解有关使用 Playwright 的详细信息，请参阅 [使用 Playwright 在 Microsoft Edge 中自动执行和测试](../../playwright/index.md)。

需要 IE 模式才能使网站 (或应用) 内容正常运行的应用程序应使用 `WebBrowser` 控件。  该 `WebBrowser` 控件使用 Internet Explorer 平台 (MSHTML/Trident) 来呈现 Web 内容，即使 Internet Explorer 11 桌面应用程序不可用，也可正常工作。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [什么是 Internet Explorer (IE) 模式?](/deployedge/edge-ie-mode)
*  [配置 IE 模式策略](/deployedge/edge-ie-mode-policies)
*  [使用文档模式和企业模式站点列表修复 Web 兼容性问题](/internet-explorer/ie11-deploy-guide/fix-compat-issues-with-doc-modes-and-enterprise-mode-site-list)
