---
title: 使用应用程序调试 WebView2 Visual Studio
description: 如何使用 webView2 应用调试Microsoft Visual Studio。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/11/2022
ms.openlocfilehash: 1abc25b23874213d510f992c8a9d456edab8e78f
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433673"
---
# <a name="debug-webview2-apps-with-visual-studio"></a>使用应用程序调试 WebView2 Visual Studio

Microsoft Visual Studio WebView2 应用中的 Web 和本机代码的各种调试工具，以调试 Win32 应用或加载项中的 web 和Office代码。 本文重点介绍调试 WebView 控件。  其他调试方法Visual Studio也可用。


<!-- ====================================================================== -->
## <a name="open-devtools-using-an-approach-other-than-f12"></a>使用 F12 外的方法打开 DevTools

当你在附加了本机调试Visual Studio`F12`中调试应用时，按可能会触发本机调试器，而不是开发人员工具。  若要避免这种情况，请按 `Ctrl``I`+`Shift`+。  或者，右键单击该页面，然后选择 `Inspect`。


<!-- ====================================================================== -->
## <a name="requirements"></a>要求

*  若要调试脚本，必须从应用程序内启动Visual Studio。

*  无法将调试器附加到正在运行的 WebView2 进程。

*  安装 Visual Studio 2019 版本 16.4 预览版 2 或更高版本。


若要调试代码，请首先根据以下两个部分在 Visual Studio 中安装和设置脚本调试器工具。


<!-- ====================================================================== -->
## <a name="install-the-javascript-diagnostics-component"></a>安装 JavaScript 诊断组件

首先，使用 **C++** 在桌面开发中安装 **JavaScript** 诊断组件，如下所示。

1. 在"Windows资源管理器"栏中，键入 `Visual Studio Installer`。

1. 选择**Visual Studio 安装程序**打开它。

1. In the Visual Studio 安装程序， on the installed version， click the **More** button， and then select **Modify**.

1. In Visual Studio， under **Workloads**， select the **Desktop Development with C++** setting：

   :::image type="content" source="./media/workloads.png" alt-text="Visual Studio修改工作负载屏幕。" lightbox="./media/workloads.png":::

1. 选择 **顶部的"** 单个组件"。

1. 在搜索框中，输入 `JavaScript diagnostics`。

1. 选择 **"JavaScript 诊断"** 设置。

1. 单击 **"修改"**。

   :::image type="content" source="./media/indiv-comp.png" alt-text="Visual Studio：修改&quot;单个组件&quot;选项卡中的值。" lightbox="./media/indiv-comp.png":::


<!-- ====================================================================== -->
## <a name="enable-script-debugging-for-webview2-apps"></a>为 WebView2 应用启用脚本调试

其次，为 WebView2 应用启用脚本调试，如下所示。

1. 右键单击 WebView2 项目，然后选择"属性 **"**。

1. 在" **配置属性"下**，选择 **"调试"**。

1. 在调试 **器类型下**，选择 **"JavaScript (WebView2) " **。

   :::image type="content" source="./media/enb-js.png" alt-text="中&quot;调试&quot;配置Visual Studio。" lightbox="./media/enb-js.png":::


<!-- ====================================================================== -->
## <a name="debug-your-webview2-app"></a>调试 WebView2 应用

执行上述设置后，调试 WebView2 应用，如下所示。

1. 若要在源代码中设置断点，请将鼠标悬停在行号的左侧，然后单击以设置断点。  JS/TS 调试适配器不执行源路径映射。  必须打开与 WebView2 关联的完全相同的路径。

   :::image type="content" source="./media/breakpoint.png" alt-text="在 Visual Studio 中添加断Visual Studio。" lightbox="./media/breakpoint.png":::

1. 若要运行调试器，请选择平台的位大小，然后单击"本地调试器"旁边的绿色"播放Windows**按钮**。  应用运行，调试程序连接到创建的第一个 WebView2 进程。

   :::image type="content" source="./media/run.png" alt-text="本地Windows调试器Visual Studio。" lightbox="./media/run.png":::

1. 在 **调试控制台中**，查找调试器的输出。

   :::image type="content" source="./media/console.png" alt-text="在 Visual Studio 中调试控制台。" lightbox="./media/console.png":::


<!-- ====================================================================== -->
## <a name="troubleshooting"></a>疑难解答

### <a name="virtual-source-path-mapping-not-supported-in-visual-studio-2019"></a>Visual Studio 2019 中不支持虚拟源路径映射

如果使用 WebView2 [SetVirtualHostNameToFolderMapping](/dotnet/api/microsoft.web.webview2.core.corewebview2.setvirtualhostnametofoldermapping) 方法，Visual Studio 2019 中的调试程序将不能理解虚拟源路径映射，因此断点无法正常工作。

在 中使用调试器时，虚拟源路径映射可以正常工作 <!-- Visual Studio 2022 or? -->Visual Studio Code。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2 入门](../get-started/get-started.md)
* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) - WebView2 功能的综合示例。
* [WebView2 API 参考](../webview2-api-reference.md)
* [另请参阅](../index.md#see-also) _WebView2 Microsoft Edge简介_。
