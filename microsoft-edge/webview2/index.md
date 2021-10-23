---
description: 使用 Microsoft Edge WebView2 控件在 Win32、.NET 以及 UWP 应用中托管 web 内容
title: Microsoft Edge WebView2 简介
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/06/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、CoreWebView2、ICoreWebView2Host、浏览器控件、edge html、Windows Forms、WinForms、WPF、.NET、WinUI、Project Reunion
ms.openlocfilehash: 1a76da8248ad6725f5aef81d3c1722fe6ca4a560
ms.sourcegitcommit: 97b32870897c702eed52d9fbbd13cfff2046ad87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2021
ms.locfileid: "12107994"
---
# <a name="introduction-to-microsoft-edge-webview2"></a>Microsoft Edge WebView2 简介

WebView2 Microsoft Edge WebView2 控件允许你将 Web 技术 (HTML、CSS 和 JavaScript) 本机应用中。  WebView2 控件使用[Microsoft Edge][MicrosoftedgeinsiderMain]作为呈现引擎，以在本机应用中显示 Web 内容。  使用 WebView2，可以在本机应用的不同部分嵌入 Web 代码，或在单个 WebView 实例中生成所有本机应用。  要了解如何开始生成 WebView2 应用，请导航到 [入门](#get-started)。

:::image type="complex" source="./media/WebView2/what-webview.png" alt-text="什么是 WebView?" lightbox="./media/WebView2/what-webview.png":::
   什么是 WebView?
:::image-end:::


<!-- ====================================================================== -->
## <a name="hybrid-app-approach"></a>混合应用方法

开发人员通常必须决定是生成 web 应用还是本机应用。  此决定取决于范围和电源之间的权衡。
*  Web 应用的范围可以很广。  作为 Web 开发人员，您可以跨不同平台重用大部分代码。
*  若要访问本机平台的所有功能，请使用本机应用。

:::image type="complex" source="./media/WebView2/web-native.png" alt-text="Web 本机" lightbox="./media/WebView2/web-native.png":::
   Web 本机
:::image-end:::

混合应用使开发人员可以充分利用这两个世界：Web 平台的功能和强度，以及本机平台的强大功能和完整功能。


<!-- ====================================================================== -->
## <a name="webview2-benefits"></a>WebView2 优势

<!--
In the below table, keep two trailing spaces after each image line and after each heading line, to keep card elements tight but not concatenated.
Similar table: [Overview of Progressive Web Apps (PWAs)](..\progressive-web-apps-chromium\index.md#characteristics-of-a-pwa)
-->

:::row:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-web-ecosystem-skillset-small.msft.png":::  
        **Web 生态系统 & 技能集**  
        利用 web 生态系统中存在的整个 web 平台、库、工具以及人才。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-rapid-innovation-small.msft.png":::  
        **快速创新**  
        Web 开发允许快速部署和迭代。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-windows-7-8-10-support-small.msft.png":::  
        **Windows 7、8 以及 10 支持**  
        支持跨 Windows 7、Windows 8 以及 Windows 10 的一致用户体验。
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-native-capabilities-small.msft.png":::  
        **本机功能**  
        访问完整的本机 API 集。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-code-sharing-small.msft.png":::  
        **代码共享**  
        向代码库添加 web 代码可以增加跨多个平台的重用。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-microsoft-support-small.msft.png":::  
        **Microsoft 支持**  
        当 WebView2 发布一般可用版 \(GA\) 时，Microsoft 会提供支持并添加新功能请求。
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-evergreen-small.msft.png":::  
        **常青分布**  
        依赖带有定期平台更新和安全修补的最新版 Chromium。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-fixed-small.msft.png":::  
        **固定版本分布**  
        （可选）将特定版本的 Chromium打包到应用中。
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/webview-reasons-incremental-adoption-small.msft.png":::  
        **增量采用**  
        将 Web 组件分片添加到应用。
    :::column-end:::
:::row-end:::

<!-- In the above table, keep two trailing spaces after each image line and after each heading line, to keep card elements tight but not concatenated. -->


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

要使用 WebView2 控件生成并测试应用，需要 <!--both [Microsoft Edge][MicrosoftedgeinsiderDownload] and -->安装 [WebView2 SDK][NugetPackagesMicrosoftWebWebView2]。  选择以下其中一个选项以开始使用。

*   [在 Win32 应用中开始使用 WebView2][Webview2GetStartedWin32]
*   [WPF 应用中的 WebView2 入门][Webview2GetStartedWpf]
*   [WinForms 应用中的 WebView2 入门][Webview2GetStartedWinforms]
*   [WinUI 2 应用和预览版中的 WebView2 (入门) ][Webview2GetStartedWinui2]
*   [WinUI 3 应用和预览版中的 WebView2 (入门) ][Webview2GetStartedWinui]

[WebView2 示例][GithubMicrosoftedgeWebview2samples] 存储库包含演示所有 WebView2 SDK 功能和 API 使用模式的示例。  随着更多功能添加到 WebView2 SDK 中，示例应用将相应更新。


<!-- ====================================================================== -->
## <a name="supported-platforms"></a>受支持的平台

通用 \ (GA\) WebView2 预览版可用于以下编程环境。

*   Win32 C/C++ \(GA\)
*   .NET Framework 4.5 或更高版本
*   .NET Core 3.1 或更高版本
*   .NET 5
*   .NET 6 (Preview) 
*   [WinUI 3.0][UwpToolkitsWinui3]

WebView2 应用可以在以下版本的 Windows。

*   Windows 10
*   Windows 10 IoT 企业版LTSC x32 2019
*   Windows 10 IoT 企业版LTSC x64 2019
*   Windows 10 IoT 企业版 21h1 x64
*   Windows 8.1
*   Windows 7 \*\*
*   Windows Server 2019
*   Windows Server 2016
*   Windows Server 2012
*   Windows Server 2012 R2
*   Windows Server 2008 R2 \*\*

> [!IMPORTANT]
> \*\* 对 Windows 7 和 Windows Server 2008 R2 的 WebView2 支持与 Microsoft Edge 的支持周期相同。  有关详细信息，请导航到 [Microsoft Edge 支持的操作系统][DeployedgeMicrosoftEdgeSupportedOS]。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [了解 WebView2 SDK 版本][Webview2ConceptsVersioning]
*  [分发 WebView2 应用和 WebView2 运行时][Webview2ConceptsDistribution]
*  [开发安全的 WebView2 应用的最佳做法][Webview2ConceptsSecurity]
*  [在 WebView2 应用中管理用户数据文件夹][Webview2ConceptsUserDataFolder]
*  [如何使用 WebView2 进行调试][Webview2HowToDebug]
*  [使用 Microsoft Edge 驱动程序自动执行并测试 WebView2][Webview2HowToWebdriver]


<!-- ====================================================================== -->
<!-- links -->
[Webview2ConceptsDistribution]: ./concepts/distribution.md "分发 WebView2 应用和 WebView2 运行时|Microsoft Docs"
[Webview2ConceptsSecurity]: ./concepts/security.md "开发安全的 WebView2 应用的最佳做法 | Microsoft Docs"
[Webview2ConceptsUserDataFolder]: ./concepts/user-data-folder.md "管理用户数据文件夹 | Microsoft Docs"
[Webview2ConceptsVersioning]: ./concepts/versioning.md "了解 WebView2 SDK 版本 | Microsoft Docs"

[Webview2GetStartedWin32]: ./get-started/win32.md "在 Win32 应用和应用中开始使用 WebView2 |Microsoft Docs"
[Webview2GetStartedWinforms]: ./get-started/winforms.md "WinForms 应用和应用中的 WebView2 |Microsoft Docs"
[Webview2GetStartedWinui2]: ./get-started/winui2.md "WinUI 2 应用和应用中的 WebView2 |Microsoft Docs"
[Webview2GetStartedWinui]: ./get-started/winui.md "WinUI 3 应用和预览版中的 WebView2 (入门) |Microsoft Docs"
[Webview2GetStartedWpf]: ./get-started/wpf.md "WPF 应用和应用中的 WebView2 |Microsoft Docs"

[Webview2HowToDebug]: ./how-to/debug.md "开始调试 WebView2 应用|Microsoft Docs"
[Webview2HowToWebdriver]: ./how-to/webdriver.md "使用 Microsoft Edge 驱动程序自动执行并测试 WebView2 | Microsoft Docs"
[Webview2ReleaseNotes]: ./release-notes.md "WebView2 SDK 发行说明 | Microsoft Docs"
<!-- external links -->
[UwpToolkitsWinui3]: /uwp/toolkits/winui3/index "Windows UI 库 3 预览版 2(2020 年 7 月) | Microsoft Docs"
[DeployedgeMicrosoftEdgeSupportedOS]: /deployedge/microsoft-edge-supported-operating-systems "Microsoft Edge 支持的操作系统 | Microsoft Docs"

[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"
[GithubMicrosoftedgeWebviewfeddback]: https://github.com/MicrosoftEdge/WebViewFeedback "WebView 反馈 - MicrosoftEdge/WebViewFeedback | GitHub"

[MicrosoftedgeinsiderMain]: https://www.microsoftedgeinsider.com "Microsoft Edge 预览体验成员"

[NugetPackagesMicrosoftWebWebView2]: https://www.nuget.org/packages/Microsoft.Web.WebView2 "Microsoft.Web.WebView2 | NuGet Gallery"
