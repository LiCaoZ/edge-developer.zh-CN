---
title: DevTools (Microsoft Edge 99) 中的新增功能
description: 主机源映射Azure DevOps符号服务器上，以便安全地调试原始源代码。  使用源映射来取消对性能配置文件进行非管理。  DevTools 扩展现在用于Microsoft Visual Studio。  3D 视图工具替换 Layers 工具。  改进了网络控制台和 3D 视图工具中的辅助功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/09/2022
ms.openlocfilehash: 5fcd59d920fc5829f5c58bd51bf809597ed6c5f9
ms.sourcegitcommit: 83d9ab6020896e397154672eae9089dba15f4bda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2022
ms.locfileid: "12593601"
---
# <a name="whats-new-in-devtools-microsoft-edge-99"></a>DevTools (Microsoft Edge 99) 中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="securely-debug-your-production-code-with-source-maps-from-azure-artifacts-symbol-server"></a>使用符号服务器Azure Artifacts源映射安全调试生产代码

<!-- Title: Debug JavaScript with source maps more easily -->
<!-- Subtitle: Publish your source maps to Azure Artifacts Symbol Server and connect DevTools to it for an easier debugging experience. -->

Azure Artifacts符号服务器现在支持存储生成过程在编译、缩小和捆绑代码时生成的源映射。  现在可以将源映射发布到安全Azure Artifacts符号服务器，而不是在公共服务器上托管源映射。  然后，将 DevTools 连接到符号服务器，让 DevTools 自动提取源映射。 

通过使用源映射，可以在 DevTools 中查看和调试原始源代码，而不必使用服务器返回的已编译、细化和捆绑生产代码。  在Azure Artifacts符号服务器上托管源映射可让你安全、私密地查看和使用源代码，而不是将源映射放在服务器上并公开显示原始代码。

若要尝试此功能，请执行以下操作：
1. [将源映射发布到Azure Artifacts符号服务器](../../../javascript/publish-source-maps-to-azure.md)。
1. 通过输入Azure DevOps组织和个人访问令牌，打开 DevTools **> 设置** > **Symbol Server** 并将 DevTools 连接到Azure Artifacts符号服务器。

![DevTools 设置中的“符号服务器”页，在其中输入Azure DevOps个人访问令牌。](../../media/2022/03/ado-pat-devtools.png)

另请参阅：
*  [将已处理的代码映射到原始源代码，以便进行调试](../../../javascript/source-maps.md)
*  [通过将源映射发布到Azure Artifacts符号服务器来安全地调试原始代码](../../../javascript/publish-source-maps-to-azure.md)
*  [使用Azure Artifacts符号服务器源映射安全地调试原始代码](../../../javascript/consume-source-maps-from-azure.md)


<!-- ====================================================================== -->
## <a name="microsoft-edge-devtools-extension-for-visual-studio"></a>Microsoft Edge Visual Studio 的 DevTools 扩展

<!-- Title: Debug your ASP.NET projects in Visual Studio with the Edge Developer Tools -->
<!-- Subtitle: Get the Edge Developer Tools extension for VS today! -->

了解Visual Studio Code集成的成功后，现在还可以在Microsoft Visual Studio中嵌入Microsoft Edge开发人员工具以实时调试 ASP.NET 项目。  下载[用于Visual Studio的Microsoft Edge开发人员工具](https://aka.ms/edgetools-for-vs)并试用。 

若要尝试此功能，请执行以下操作：
1. 确保已安装Visual Studio 2022 和 ASP.NET 工作负荷。
1. 如[Microsoft Edge开发人员](https://aka.ms/edgetools-for-vs)工具Visual Studio中所述，将 Web Live Preview 设置为默认Web Forms设计器。
1. 在 ASP.NET 项目中，在“**设计**”窗口中打开项目的网页。
1. 在 **“设计”** 窗口左上角，单击 **“Open Edge DevTools** (![Open Edge DevTools”图标。](../../media/2022/03/open-edge-dev-tools-v-s-icon.png)) 按钮：

![ASP.NET 项目，打开 Edge DevTools。](../../media/2022/03/devtools-extension-v-s-web-forms-designer.png)

将打开用于Visual Studio的 Edge DevTools，其中选择了 **“元素**”工具：

![Microsoft Edge开发人员工具Visual Studio：DevTools 的元素工具。](../../media/2022/03/devtools-extension-visual-studio-elements.png)

默认情况下， **网络** 工具也可用：

![Microsoft Edge开发人员工具Visual Studio：DevTools 的网络工具。](../../media/2022/03/devtools-extension-visual-studio-network.png)

检查 **工具** (![检查工具图标。](../../media/2022/03/v-s-edge-devtools-inspect-tool-icon.png)) 和 **切换屏幕截图** (![切换屏幕广播图标。](../../media/2022/03/v-s-edge-devtools-toggle-screencast-icon.png)) 可用， **“更多工具** (![更多工具”图标。](../../media/2022/03/more-tools-v-s-icon.png)) 菜单提供 [“问题](../../../issues/index.md)”、“ [网络条件](../../../network-conditions/network-conditions-tool.md)”和 [“网络请求阻止](../../../network-request-blocking/network-request-blocking-tool.md) ”工具。

另请参阅：

* Visual Studio DevBlogs [中用于Visual Studio (预览版) 的边缘开发人员工具](https://devblogs.microsoft.com/visualstudio/?p=237066&preview=1&_ppp=7aa7aef54f)。
* [适用于Visual Studio的 Edge DevTools 扩展](../../../../visual-studio/index.md#edge-devtools-extension-for-visual-studio)。


<!-- ====================================================================== -->
## <a name="layers-in-3d-view"></a>3D 视图中的层

<!-- Title: Layers in 3D View -->
<!-- Subtitle: The Layers tool isn't going away - find it in the 3D View tool today. -->

自 [Microsoft Edge 88](../../2020/11/devtools.md#composited-layers-are-now-in-3d-view) 起，**3D 视图**工具提供了**改进的 Layers** 工具版本。  现在，在 Microsoft Edge 99 中，**层**工具中的功能已被删除，而 **“图层**”工具则包含一个链接，可将你重定向到 **3D 视图**工具中的复合层视图。  可以在 **3D 视图**工具中找到以前在 **“层**”工具中的所有功能，以及更多功能。

更新：图 **层** 工具现已删除。

![“图层”工具现在链接到 3D 视图工具。](../../media/2022/03/layers-3d-view-tool.png)
<!-- work item > layersmove.gif -->

另请参阅：
* [使用 3D 视图工具导航网页层、z 索引和 DOM](../../../3d-view/index.md)


<!-- ====================================================================== -->
## <a name="use-your-source-maps-to-display-original-function-names-in-performance-profiles"></a>使用源映射在性能配置文件中显示原始函数名称

<!-- Title: The Performance tool can now display unminified function names in the flame chart -->
<!-- Subtitle: Use the new Unminify button in the Performance tool to download an unminified version of the performance profile you recorded. -->

在“性能”工具中录制性能配置文件会生成一个细化的火焰图。  在早期版本的Microsoft Edge中，即使你在服务器上托管了源映射，火焰图也没有使用源映射来显示原始函数名称。

从Microsoft Edge版本 99 开始，可以在性能配置文件中显示原始函数名称，如下所示：
1. 在 **“性能** ”工具中记录配置文件。
1. 单击“取消管理”图标](../../media/2022/03/unminify-icon.png) (![新的 **“取消明**示”。) 按钮创建和下载未指定的性能配置文件。
1. 加载 ()  (![“负载配置文件”图标导入。](../../media/2022/03/load-profile-icon.png)) “ **性能** ”工具中未指定的性能配置文件。

**“取消管理”** 按钮将使用源映射（前提是它们与生产代码并排托管）在**性能**工具的火焰图中取消区分函数名称。

**“性能**”工具中的火焰图最初显示的函数名称为 **b**、**O**、**Xt** 和 **bn**，取自 Web 服务器返回的细化生产代码：

![性能工具中火焰图中的已缩小函数名称。](../../media/2022/03/minified-call-stack-performance-tool.png)

单击 **“取消明 (**![”取消排序图标后。](../../media/2022/03/unminify-icon.png)) **加载配置文件** (![“加载配置文件”图标。](../../media/2022/03/load-profile-icon.png)) ，**性能**工具中的火焰图现在显示标记有有意义的名称的函数：**invokeFunc (b) **、**executeAction (O) **、**endBatch (Xt) **，以及从源映射中检索到**的 runReactions (bn) **：

![性能工具中火焰图中的非显式函数名称。](../../media/2022/03/unminified-call-stack-performance-tool.png)

另请参阅：
* 在 [Microsoft Edge 博客中取消区分 DevTools 性能配置文件](https://blogs.windows.com/msedgedev/2022/02/03/unminifying-function-names-in-devtools-performance-profiles/)中的函数名称。
* [在性能配置文件中显示原始函数名称](../../../evaluate-performance/unminify.md)。


<!-- ====================================================================== -->
## <a name="improved-accessibility-for-network-console-and-3d-view"></a>改进了网络控制台和 3D 视图的辅助功能

<!-- Title: Improvements for using assistive technology with DevTools -->
<!-- Subtitle: Screen readers now announce better information in the Network Console and 3D View tools. -->

在早期版本的Microsoft Edge中，辅助技术在网络控制台工具中提供自定义持有者令牌时宣布了不正确的信息。  在 Microsoft Edge 版本 99 中，此问题已修复。  选择用于提供自定义持有者令牌的文本框时，辅助技术现在将宣布“令牌编辑文本请求视图组”。

![网络控制台工具。](../../media/2022/03/network-console-tool.png)

在早期版本的Microsoft Edge中，辅助技术只会在 3D 视图工具中读出单选按钮文本，而不会宣布按钮所属的组名。  在 Microsoft Edge 版本 99 中，此问题已修复。  例如，当焦点位于 **“使用屏幕纹理** ”单选按钮上时，辅助技术现在将宣布：“颜色类型单选组，使用屏幕纹理，单选按钮，已选中”。

![3D 视图工具。](../../media/2022/03/3d-view-tool.png)

另请参阅：
* [使用辅助技术导航开发工具](../../../accessibility/navigation.md)


<!-- ====================================================================== -->
## <a name="improved-source-folder-tree-in-the-sources-panel"></a>改进了“源”面板中的源文件夹树

在 **“源**”工具的 **“页面**”选项卡中，源文件夹的树现在得到改进，文件夹的命名和轮廓中的杂乱无章。  不需要的路径前缀，例如 `../` 已 `./` 删除。  通过合并等效的重复文件夹简化了树结构。

![“源”工具的“页面”选项卡中的更简洁文件夹轮廓。](../../media/2022/03/folders-page-tab-sources-tool.png)

有关Chromium开源项目中此功能的历史记录，[请参阅问题1284737](https://crbug.com/1284737)。

<!-- https://developer.chrome.com/blog/new-in-devtools-99/#source-tree -->

另请参阅：
* [使用“页面”选项卡浏览]() 在 _“源”工具概述_中构造当前网页的资源。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge版本 99 还包括Chromium项目的以下更新：

* [限制 WebSocket 请求](https://developer.chrome.com/blog/new-in-devtools-99/#websocket)
* [应用程序面板中的“新建报告 API”窗格](https://developer.chrome.com/blog/new-in-devtools-99/#reporting-api)
* [更好的控制台样式设置、格式设置和筛选](https://developer.chrome.com/blog/new-in-devtools-99/#console)
   * [使用 ANSI 转义代码正确设置日志消息的样式](https://developer.chrome.com/blog/new-in-devtools-99/#console-styling)
   * [正确支持 %s、%d、%i 和 %f 格式说明符](https://developer.chrome.com/blog/new-in-devtools-99/#console-format)
* [源图改进](https://developer.chrome.com/blog/new-in-devtools-99/#sourcemap) <!-- redundant w/ above?-->
   * [使用源映射文件调试扩展插件](https://developer.chrome.com/blog/new-in-devtools-99/#extension)
   * [在“源”面板中显示辅助角色源文件](https://developer.chrome.com/blog/new-in-devtools-99/#worker-sourcemap)
* [触摸友好颜色选取器和拆分窗格](https://developer.chrome.com/blog/new-in-devtools-99/#touch-friendly)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> Chromium项目的公告原始页面是 [DevTools (Chrome 99) 中的新增](https://developer.chrome.com/blog/new-in-devtools-99)功能，由在 Google) 上处理 Chrome DevTools 的开发人员倡导者 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (创作。


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
