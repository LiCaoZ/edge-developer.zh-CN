---
title: 静态链接 WebView2 加载程序库
description: 如何静态链接 WebView2 加载程序库。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
---
# <a name="statically-link-the-webview2-loader-library"></a>静态链接 WebView2 加载程序库

你可能希望使用单个可执行文件（而不是许多文件的包）来分发应用程序。  若要创建单个可执行文件或减小程序包的大小，应静态链接 WebView2Loader 文件。  WebView2 SDK 包含头文件 `WebView2Loader.dll`、和 `IDL` 文件。 `WebView2Loader.dll` 是一个小型组件，可帮助应用在设备上找到 WebView2 运行时Microsoft Edge预览通道。

对于不希望提供 的应用， `WebView2Loader.dll`请完成以下步骤。

1.  `.vcxproj`在文本编辑器（如文本编辑器）中打开应用Visual Studio Code。

    > [!NOTE]
    > 项目`.vcproj`文件可能是一个隐藏文件，这意味着该文件不会显示在Visual Studio。  使用命令行查找隐藏文件。

1.  在包含 WebView2 程序包目标文件的代码中找到NuGet部分。  代码中的位置在下图中突出显示。

    :::image type="complex" source="./media/insert-here.png" alt-text="Project文件代码段。" lightbox="./media/insert-here.png":::
       Project文件代码段
    :::image-end:::

1.  复制以下代码段并将其粘贴到包含 `Microsoft.Web.WebView2.targets` 位置。

    ```xaml
    <PropertyGroup>
        <WebView2LoaderPreference>Static</WebView2LoaderPreference>
    </PropertyGroup>
    ```

    :::image type="complex" source="./media/static-lib.png" alt-text="插入的代码段。" lightbox="./media/static-lib.png":::
       插入的代码段
    :::image-end:::

1.  编译并运行应用。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [WebView2 入门指南](../index.md#get-started)
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
*  [WebView2 API 参考](../webview2-api-reference.md)
*  [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
