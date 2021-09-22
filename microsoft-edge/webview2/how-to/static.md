---
description: 了解如何静态链接 WebView2 加载程序库。
title: 如何静态链接 WebView2 加载程序库
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/06/2021
ms.topic: how-to
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: 83cdd9c50a6f77a8a2fdccb9ba15d842815e1aa6
ms.sourcegitcommit: f2c56030b2141eba01b534984579762421eff6aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2021
ms.locfileid: "12033536"
---
# <a name="statically-link-the-webview2-loader-library"></a>静态链接 WebView2 加载程序库

你可能希望使用单个可执行文件（而不是许多文件的包）来分发应用程序。 若要创建单个可执行文件或减小程序包的大小，应静态链接 WebView2Loader 文件。 WebView2 SDK 包含头文件 、 `WebView2Loader.dll` 和 `IDL` 文件。 `WebView2Loader.dll` 是一个小型组件，可帮助应用在设备上找到 WebView2 运行时Microsoft Edge预览通道。

对于不希望提供 的应用， `WebView2Loader.dll` 请完成以下步骤。

1.  在 `.vcxproj` 文本编辑器（如文本编辑器）中打开应用Visual Studio Code。

    > [!NOTE]
    > 项目 `.vcproj` 文件可能是隐藏文件，这意味着它不会显示在Visual Studio。  使用命令行查找隐藏文件。

1.  在包含 WebView2 程序包目标文件的代码中找到NuGet部分。  代码中的位置在下图中突出显示。

    :::image type="complex" source="./media/insert-here.png" alt-text="Project文件代码段" lightbox="./media/insert-here.png":::
       Project文件代码段
    :::image-end:::

1.  复制以下代码段并将其粘贴到包含 `Microsoft.Web.WebView2.targets` 位置。

    ```xaml
    <PropertyGroup>
        <WebView2LoaderPreference>Static</WebView2LoaderPreference>
    </PropertyGroup>
    ```

    :::image type="complex" source="./media/static-lib.png" alt-text="插入的代码段" lightbox="./media/static-lib.png":::
       插入的代码段
    :::image-end:::

1.  编译并运行应用。

## <a name="getting-in-touch-with-the-webview2-team"></a>与 WebView2 团队联系

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]

## <a name="see-also"></a>另请参阅

*   若要开始使用 WebView2，请导航到["WebView2 入门指南"。][Webview2MainGetStarted]
*   有关 WebView2 功能的综合示例，请导航到[WebView2 示例][GithubMicrosoftedgeWebview2samples]GitHub。
*   有关 WebView2 API 的更多详细信息，请导航到 [API 参考][Webview2ApiReference]。
*   有关 WebView2 的信息，请导航到["WebView2 资源"。][Webview2MainNextSteps]

<!-- links -->

[DevtoolsGuideChromiumMain]: ../index.md "Microsoft Edge (Chromium) 开发人员工具 | Microsoft Docs"

[Webview2ApiReference]: ../webview2-api-reference.md "Microsoft EdgeWebView2 API 参考|Microsoft Docs"
[Webview2MainNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 |Microsoft Docs"
[Webview2MainGetStarted]: ../index.md#get-started "入门 - WebView2 Microsoft Edge简介|Microsoft Docs"

[GithubMicrosoftedgeWebviewfeedbackMain]: https://github.com/MicrosoftEdge/WebViewFeedback "WebView 反馈 - MicrosoftEdge/WebViewFeedback | GitHub"
[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples | GitHub"

[GithubMicrosoftVscodeJSDebugWhatsNew]: https://github.com/microsoft/vscode-js-debug#whats-new "新增功能- 适用于 Visual Studio Code 的 JavaScript 调试程序 - microsoft/vscode-js-debug |GitHub"

[GithubMicrosoftVscodeEdgeDebug2ReadmeChromiumWebviewApplications]: https://github.com/microsoft/vscode-edge-debug2/blob/master/README.md#microsoft-edge-chromium-webview-applications "Microsoft Edge (Chromium) WebView 应用程序 - Visual Studio Code - 调试器 for Microsoft Edge - microsoft/vscode-edge-debug2 |GitHub"
