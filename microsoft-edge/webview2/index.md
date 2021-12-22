---
title: Microsoft Edge WebView2 简介
description: 使用 Microsoft Edge WebView2 控件在 Win32、.NET 以及 UWP 应用中托管 web 内容。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.localizationpriority: high
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、CoreWebView2、ICoreWebView2Host、浏览器控件、edge html、Windows Forms、WinForms、WPF、.NET、WinUI、Project Reunion
ms.date: 11/12/2021
ms.openlocfilehash: c492f0a0b7cd46f592a9dac89243398049363b50
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285223"
---
# <a name="introduction-to-microsoft-edge-webview2"></a>Microsoft Edge WebView2 简介

Microsoft Edge WebView2 控件允许在本机应用中嵌入 web 技术(HTML、CSS 以及 JavaScript)。  WebView2 控件使用 [Microsoft Edge](https://www.microsoftedgeinsider.com) 作为绘制引擎，以在本机应用中显示 web 内容。  使用 WebView2 可以在本机应用的不同部分嵌入 Web 代码，或在单个 WebView 实例中生成所有本机应用。  要了解如何开始生成 WebView2 应用，请导航到 [入门](#get-started)。

:::image type="complex" source="./media/WebView2/what-webview.png" alt-text="什么是 WebView?" lightbox="./media/WebView2/what-webview.png":::
   什么是 WebView?
:::image-end:::


<!-- ====================================================================== -->
## <a name="hybrid-app-approach"></a>混合应用方法

开发人员通常必须决定是生成 web 应用还是本机应用。  此决定取决于范围和力量之间的权衡。
*  Web 应用的范围可以很广。  作为 Web 开发人员，你可以跨不同平台重用多数代码。
*  要访问本机平台的所有功能，请使用本机应用。

:::image type="complex" source="./media/WebView2/web-native.png" alt-text="Web 本机" lightbox="./media/WebView2/web-native.png":::
   Web 本机
:::image-end:::

混合应用使开发人员能够享受两方面的优点：Web 平台的通用性和强大性，以及本机平台的强大功能和全部功能。


<!-- ====================================================================== -->
## <a name="webview2-benefits"></a>WebView2 优势

*  **Web 生态系统和技能集**。  利用 web 生态系统中存在的整个 web 平台、库、工具以及人才。

*  **快速创新**。  Web 开发允许快速部署和迭代。

*  **Windows 7、8 以及 10 支持**。  支持跨 Windows 7、Windows 8 以及 Windows 10 的一致用户体验。

*  **本机功能**。  访问完整的本机 API 集。

*  **代码共享**。  向代码库添加 web 代码可以增加跨多个平台的重用。

*  **Microsoft 支持**。  当 WebView2 发布一般可用版 (GA) 时，Microsoft 会提供支持并添加新功能请求。

*  **常青分布**。  依赖带有定期平台更新和安全修补的最新版 Chromium。

*  **已修复版本分布**。  也可以在应用中打包特定版本的 Chromium 位。

*  **增量采用**。  逐步将 web 组件添加到应用。


<!-- ====================================================================== -->
## <a name="get-started"></a>入门

要使用 WebView2 控件生成并测试应用，需要 <!--both Microsoft Edge and -->安装 [WebView2 SDK](https://www.nuget.org/packages/Microsoft.Web.WebView2)。  选择以下其中一个选项以开始使用。

*   [Win32 应用中的 WebView2 入门](./get-started/win32.md)
*   [WPF 应用中的 WebView2 入门](./get-started/wpf.md)
*   [WinForms 应用中的 WebView2 入门](./get-started/winforms.md)
*   [WinUI 2 应用中的 WebView2 入门（预览版）](./get-started/winui2.md)
*   [WinUI 3 应用中的 WebView2 入门（预览版）](./get-started/winui.md)

[WebView2 示例](https://github.com/MicrosoftEdge/WebView2Samples) 存储库包含演示所有 WebView2 SDK 功能和 API 使用模式的示例。  随着更多功能添加到 WebView2 SDK 中，示例应用将相应更新。


<!-- ====================================================================== -->
## <a name="supported-platforms"></a>受支持的平台

WebView2 的正式发布版 (GA) 或预览版适用于以下编程环境。

*   Win32 C/C++ (GA)
*   .NET Framework 4.5 或更高版本
*   .NET Core 3.1 或更高版本
*   .NET 5
*   .NET 6
*   WinUI 2.0（预览版）
*   [WinUI 3.0](/uwp/toolkits/winui3/index)

WebView2 应用可以在以下版本的 Windows 上运行。

*   Windows 11
*   Windows 10
*   Windows 10 IoT 企业版 LTSC x32 2019
*   Windows 10 IoT 企业版 LTSC x64 2019
*   Windows 10 IoT 企业版 21h1 x64
*   Windows 8.1
*   Windows 7 \*\*
*   Windows Server 2019
*   Windows Server 2016
*   Windows Server 2012
*   Windows Server 2012 R2
*   Windows Server 2008 R2 \*\*

> [!IMPORTANT]
> 对 Windows 7 和 Windows Server 2008 R2 的 WebView2 支持将与 Microsoft Edge 的支持时间线相同。  有关详细信息，请参阅 [Microsoft Edge 支持的操作系统](/deployedge/microsoft-edge-supported-operating-systems)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [了解 WebView2 SDK 版本](./concepts/versioning.md)
*  [分发 WebView2 应用和 WebView2 运行时](./concepts/distribution.md)
*  [开发安全的 WebView2 应用的最佳做法](./concepts/security.md)
*  [在 WebView2 应用中管理用户数据文件夹](./concepts/user-data-folder.md)
*  [如何使用 WebView2 进行调试](./how-to/debug.md)
*  [使用 Microsoft Edge 驱动程序自动执行并测试 WebView2](./how-to/webdriver.md)
