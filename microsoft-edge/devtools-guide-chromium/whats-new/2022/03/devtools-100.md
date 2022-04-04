---
title: 'DevTools (Microsoft Edge 100) '
description: 新的 DevTools 存储库位于 GitHub，以发送反馈。 使用筛选器专注于堆快照的各个部分。 捷克语和越南语 UI。 网络工具显示如何满足请求。 性能配置文件中的链接将映射到原始代码。 网络工具的瀑布视图与Visual Studio Code匹配。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/31/2022
ms.openlocfilehash: fbb02e815f32add69072d337b88fde8c357e3e61
ms.sourcegitcommit: 7264a26c08b6b60d29b8bd3b105820a849030506
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2022
ms.locfileid: "12467729"
---
# <a name="whats-new-in-devtools-microsoft-edge-100"></a>DevTools (Microsoft Edge 100) 

以下部分列出了 Microsoft Edge 开发人员工具团队的公告。  若要试用 Microsoft Edge Tools 的最新功能和适用于 Microsoft Visual Studio 和 Visual Studio Code 的边缘 DevTools 扩展，请参阅这些通知。  若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。

If you're on Windows， Linux， or macOS， consider using the Canary preview channel of Microsoft Edge as your default development browser.  Beta、Dev 和 Canary Microsoft Edge (预览频道) 让你能够访问 Microsoft Edge Tools 的最新功能。

若要报告 DevTools 问题或请求新功能，请查看新的 [MicrosoftEdge > DevTools](https://github.com/MicrosoftEdge/DevTools) 存储库。


<!-- ====================================================================== -->
## <a name="join-the-microsoft-edge-devtools-community-at-github"></a>在 Microsoft Edge 加入开发人员工具GitHub

<!-- Title: Head to the new DevTools repo at GitHub to send ideas, feedback, suggestions, and bugs -->
<!-- Subtitle: You can file feedback, ask questions, and have discussions about DevTools at our GitHub repo. -->

我们很高兴在 > 上宣布新的 [MicrosoftEdge](https://github.com/MicrosoftEdge/DevTools) GitHub！  此新存储库是开发人员社区向我们发送改进 DevTools 的想法、反馈、建议和提示的地方。  我们期待与你讨论 DevTools 如何更好地满足你的需求并解决你每天在构建出色的 Web 体验时所面临的挑战。

![DevTools 反馈存储库。](devtools-100-images/devtools-feedback-repo.png)

前往我们的 DevTools 存储库，GitHub成为 Edge DevTools 社区的一部分。


<!-- ====================================================================== -->
## <a name="filter-heap-snapshots-summary-by-node-type"></a>按节点类型筛选堆快照摘要

<!-- Title: Use new filters to focus on specific parts of a heap snapshot -->
<!-- Subtitle: You can now filter by node type if, for example, you're only interested in the arrays or strings from the heap. -->

在内存工具中查看堆快照中所有对象时，**** 可能很难专注于特定对象或保留路径。  现在，Microsoft Edge 100 中，可以在查看堆快照时使用新的"**** 节点类型"筛选器，以仅关注特定类型的节点。  例如，若要仅查看堆中的数组和字符串对象，请选择"节点类型"筛选器中的 **"数组**"**** 和"字符串 **"** 条目。

![内存工具中堆快照中的节点类型。](devtools-100-images/node-types-heap-snapshot.png)

若要了解有关在 DevTools 中拍摄堆快照和分析堆的更多信息，请参阅使用内存工具记录堆 [快照](../../../memory-problems/heap-snapshots.md)。


<!-- ====================================================================== -->
## <a name="use-devtools-in-czech-and-vietnamese"></a>使用捷克语和越南语中的 DevTools

<!-- Title: DevTools: Now available in Czech and Vietnamese -->
<!-- Subtitle: Try out DevTools in your preferred language!  If we haven't supported it, yet, let us know. -->

自定义和简化开发人员体验包括使工具可供所有人使用，无论其首选语言如何。  我们已将两种新语言（捷克语和越南语）添加到支持的语言列表中，并且将继续添加更多语言。  如果你的首选语言在 DevTools 中不受支持，请告诉我们！

![捷克语和越南语中的 DevTools。](devtools-100-images/czech-vietnamese.png)

有关详细信息，请参阅更改 [DevTools 语言设置](../../../customize/localization.md)。


<!-- ====================================================================== -->
## <a name="the-network-tool-now-displays-how-a-request-was-fulfilled"></a>"网络"工具现在显示请求的实现状态

<!-- Title: You no longer have to wonder if a request was fulfilled by your service worker or cache -->
<!-- Subtitle: The "Fulfilled by" column in the Network tool tells you how a request was fulfilled. -->

在 Microsoft Edge 100 中，**网络**工具在请求日志中支持新的 **Fulfilled by** 列。  如果请求由服务工作者或缓存完成，该信息现在将跟踪在 **"完成者** "列中。  导出请求日志或将请求日志作为文件 `HAR` 导入时，还将包含 **"完成** 者"列中的信息。

![网络工具的请求日志中的"完成者"列。](devtools-100-images/fulfilled-by-request-log.png)
<!--
If you don't have the **Fulfilled by** column, right-click the table headers in the request log and make sure **Fulfilled by** is checked.
-->

若要详细了解 Network 工具中的请求日志，请参阅网络功能参考中的按[属性](../../../network/reference.md#display-a-log-of-requests)_筛选请求_。  有关服务工作者详细信息，请参阅服务 [工作线程改进](../../../service-workers/index.md)。

有关此功能的历史记录，请参阅问题 [#16](https://github.com/MicrosoftEdge/DevTools/issues/16)。


<!-- ====================================================================== -->
## <a name="when-importing-a-performance-profile-links-now-map-to-your-original-code"></a>导入性能配置文件时，现在链接将映射到原始代码

<!-- Title: Use sourcemaps from Azure Artifacts symbol server to better debug performance issues -->
<!-- Subtitle: Links from an imported performance profile now map to your original code because of source maps. -->

在记录性能配置文件时，"性能"工具中的**** 饼图将显示从主线程上的每个事件到"源"工具中相应 JavaScript **函数的链接。**  但是，当您导出和导入性能配置文件时，这些链接会断开。

在 Microsoft Edge 100 中，导入的性能配置文件中的链接现在使用 Azure Artifacts 符号服务器的源映射映射回熟悉的原始源代码。  必须在 Microsoft Edge 100 (或) 中导出性能配置文件，以便配置文件包含解析导出的性能跟踪中的源映射所需的信息。

![导入的性能配置文件使用源映射中的链接会转到你熟悉的原始源代码。](devtools-100-images/links-perf-profile-orig-source-code.png)

若要了解有关在 DevTools 中使用源地图的信息，请参阅将处理的代码映射到原始 [源代码，以便进行调试](../../../javascript/source-maps.md)。

若要开始将源地图存储在Azure Artifacts符号服务器中，然后从 DevTools 连接到它们，请参阅：
*  [通过发布源映射到符号服务器来安全调试Azure Artifacts代码](../../../javascript/publish-source-maps-to-azure.md)。
*  [使用符号服务器源映射Azure Artifacts调试原始代码](../../../javascript/consume-source-maps-from-azure.md)。


<!-- ====================================================================== -->
## <a name="fix-the-waterfall-view-in-the-network-tool-now-matches-visual-studio-code-themes"></a>修复：网络工具中的瀑布视图现在与Visual Studio Code匹配

<!-- Title: Themes from Visual Studio Code now apply to the Waterfall view -->
<!-- Subtitle: The Waterfall view of requests in the Network tool now match the VS Code themes. -->

在早期版本的 Microsoft Edge 中，网络工具中请求的**瀑布**视图与 Visual Studio Code 中应用于其他 **** DevTools 的主题不匹配。  在 Microsoft Edge 100 中，此问题已修复。

在 Microsoft Edge 100 之前，所选主题未在瀑布视图中应用：

![在瀑布视图中未应用所选主题。](devtools-100-images/waterfall-view-requests-network-no-theme.png)

现在，Microsoft Edge 100 中，选定的主题将应用于网络工具中请求的瀑布视图：

![选定的主题现在应用于网络工具中请求的瀑布视图。](devtools-100-images/waterfall-view-requests-network.png)

有关在 DevTools 中Visual Studio Code主题的信息，请参阅将[颜色主题应用到 DevTools](../../../customize/theme.md)。  有关网络工具中请求的瀑布视图详细信息，请参阅 [网络功能参考](../../../network/reference.md#display-the-timing-relationship-of-requests)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

Microsoft Edge版本 100 还包括来自 Chromium 项目的以下更新：

* [查看和编辑@supports样式窗格中的规则](https://developer.chrome.com/blog/new-in-devtools-100/#supports)
* [悬停时预览类/函数属性](https://developer.chrome.com/blog/new-in-devtools-100/#properties)
* [性能面板中的部分呈现帧](https://developer.chrome.com/blog/new-in-devtools-100/#perf)


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- > [!NOTE]
> Portions of this page are modifications based on work created and [shared by Google](https://developers.google.com/terms/site-policies) and used according to terms described in the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0).
> The original page for announcements from the Chromium project is [What's New in DevTools (Chrome 100)](https://developer.chrome.com/blog/new-in-devtools-100) and is authored by [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer advocate working on Chrome DevTools at Google). -->


<!-- ====================================================================== -->
<!-- uncomment if content is copied from developer.chrome.com to this page -->

<!-- [![Creative Commons License.](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0). -->
