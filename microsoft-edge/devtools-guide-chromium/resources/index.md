---
description: 按帧、域、类型或其他条件组织资源。
title: 查看页面资源
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 13e94c971e12c1e54e8857374a11e2a15839bd6b
ms.sourcegitcommit: 9920f4826b1d16ee0e4842703844437a6d22e816
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2021
ms.locfileid: "12170265"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="view-page-resources"></a>查看页面资源

资源是页面为了正确显示而需要的文件。  资源示例包括：
*  CSS 文件。
*  JavaScript 文件。
*  HTML 文件。
*  图像文件。

可以从多个工具或面板中查看包含网页的资源。

本指南假定你熟悉 Web 开发和开发工具Microsoft Edge[基础知识](../../devtools-guide-chromium/index.md)。 [](https://developer.mozilla.org/docs/Learn)


<!-- ====================================================================== -->
## <a name="open-resources-from-the-command-menu"></a>从命令菜单中打开资源

当您知道要检查的资源的名称时，"命令菜单"提供了一种**** 快速打开资源的方法。

1.  选择 `Control` + `P` (Windows、Linux) 或 `Command` + `P` (macOS) 。  将 **打开"打开文件** "对话框。

    :::image type="complex" source="../media/resources-command-menu-empty.msft.png" alt-text="&quot;打开文件&quot;对话框" lightbox="../media/resources-command-menu-empty.msft.png":::
       " **打开文件"** 对话框
    :::image-end:::

1.  从下拉列表中选择文件，或开始键入文件名，在自动完成框中突出显示正确的文件后 `Enter` 选择。

    :::image type="complex" source="../media/resources-command-menu-file-search.msft.png" alt-text="在&quot;打开文件&quot;对话框中键入文件名" lightbox="../media/resources-command-menu-file-search.msft.png":::
       在"打开文件" **对话框中键入** 文件名
    :::image-end:::


<!-- ====================================================================== -->
## <a name="open-resources-in-the-network-tool"></a>在"网络"工具中打开资源

导航 [到检查资源的详细信息](../network/index.md#inspect-the-details-of-the-resource)。

:::image type="complex" source="../media/resources-network-response.msft.png" alt-text="检查网络工具中的资源" lightbox="../media/resources-network-response.msft.png":::
   检查网络工具 **中的** 资源
:::image-end:::

### <a name="reveal-resources-in-the-network-tool-from-other-panels"></a>显示来自其他面板的网络工具中的资源

下一部分 ["浏览网络"](#browse-resources-in-the-network-panel)面板中的资源 显示如何查看来自 DevTools UI 各个部分的资源。  若要在"网络 **"工具中**检查资源，请右键单击该资源，然后选择"网络 **"面板中的"展示"。**

:::image type="complex" source="../media/resources-sources-page-reveal-in-network-panel.msft.png" alt-text="&quot;网络&quot;面板中的&quot;展示&quot;" lightbox="../media/resources-sources-page-reveal-in-network-panel.msft.png":::
   **"网络"面板中的"展示"**
:::image-end:::


<!-- ====================================================================== -->
## <a name="browse-resources-in-the-network-panel"></a>浏览"网络"面板中的资源

导航到 [记录网络](../network/index.md#log-network-activity)。

:::image type="complex" source="../media/resources-network-resources.msft.png" alt-text="网络日志中的页面资源" lightbox="../media/resources-network-resources.msft.png":::
   网络日志中 **的页面** 资源
:::image-end:::


<!-- ====================================================================== -->
## <a name="browse-resources-by-directory-in-the-sources-tool"></a>在"源"工具中按目录浏览资源

查看按目录组织的网页的资源：

1.  打开 DevTools。

1.  选择 **"源**"工具，然后在左上角的****"导航器"窗格中，选择"**页面"** 选项卡。

1.  单击"**页面**" (...) "按钮的"更多选项"，然后选择"按**文件夹分组"。** ****

    :::image type="complex" source="../media/resources-sources-page-empty.msft.png" alt-text="&quot;源&quot;工具的&quot;导航器&quot;窗格中的&quot;页面&quot;选项卡" lightbox="../media/resources-sources-page-empty.msft.png":::
       " **源** "工具的"导航 **器"** 窗格中的" **页面"** 选项卡
    :::image-end:::

    下面细目了上图中的不明显项。

    | 页面项 | 描述 |
    |:--- |:--- |
    | `top` | 主文档 [浏览上下文](https://developer.mozilla.org/docs/Web/HTML/Element/iframe)。 |
    | `airhorner.com` | 域。  嵌套在它下的所有资源都来自该域。  例如，文件的完整 URL `comlink.global.j` 可能是 `https://airhorner.com/scripts/comlink.global.js` 。 |
    | `scripts` | 目录。 |
    | `(index)` | 主 HTML 文档。 |
    | `sw.js` | 服务工作线程运行时上下文。 |

1.  选择一个资源，在编辑器中查看 **它**。

    :::image type="complex" source="../media/resources-sources-page-resource.msft.png" alt-text="在编辑器中查看文件" lightbox="../media/resources-sources-page-resource.msft.png":::
       在编辑器中查看 **文件**
    :::image-end:::


<!-- ====================================================================== -->
## <a name="browse-resources-by-filename-in-the-sources-tool"></a>在"源"工具中按文件名浏览资源

默认情况下，" **页面"** 选项卡按目录对资源进行分组。  若要将每个域的资源显示为一个简单列表，而不是按目录分组：

1.  转到" **源"** 工具。

1.  在左侧 **导航器** (窗格中，) " **页面"** 选项卡。

1.  单击 **"更多选项** `...` "，然后清除 **"按文件夹分组"** 复选框。

    :::image type="complex" source="../media/resources-sources-page-resource-group-by-folder.msft.png" alt-text="&quot;按文件夹分组&quot;选项" lightbox="../media/resources-sources-page-resource-group-by-folder.msft.png":::
       " **按文件夹分组"** 选项
    :::image-end:::

    资源按文件类型进行组织。  在每个文件类型内，资源按字母顺序进行组织。

    :::image type="complex" source="../media/resources-sources-page-resources-empty-not-grouped-by-folder.msft.png" alt-text="清除&quot;按文件夹分组&quot;复选框后的&quot;页面&quot;选项卡" lightbox="../media/resources-sources-page-resources-empty-not-grouped-by-folder.msft.png":::
       清除 **"** 按文件夹分组"复选框后的"页面 **"** 选项卡
    :::image-end:::


<!-- ====================================================================== -->
## <a name="browse-resources-by-file-type-in-the-application-tool"></a>在应用程序工具中按 **文件类型浏览** 资源

根据资源文件类型将资源分组在一起：

1.  选择" **应用程序"** 选项卡。 应用程序 **工具** 将打开。  默认情况下，清单 **窗格** 通常首先打开。

    :::image type="complex" source="../media/resources-application-mainfest-airhorner.msft.png" alt-text="应用程序工具" lightbox="../media/resources-application-mainfest-airhorner.msft.png":::
       **应用程序**工具
    :::image-end:::

1.  向下滚动到"框架 **"** 窗格。

    :::image type="complex" source="../media/resources-application-mainfest-airhorner-frames-expanded.msft.png" alt-text="&quot;框架&quot;窗格" lightbox="../media/resources-application-mainfest-airhorner-frames-expanded.msft.png":::
       " **框架"** 窗格
    :::image-end:::

1.  展开感兴趣的部分。

1.  选择一个资源进行查看。

    :::image type="complex" source="../media/resources-application-mainfest-airhorner-expanded-resources.msft.png" alt-text="在&quot;应用程序&quot;面板中查看资源" lightbox="../media/resources-application-mainfest-airhorner-expanded-resources.msft.png":::
       在"应用程序"面板 **中查看** 资源
    :::image-end:::


<!-- ====================================================================== -->
## <a name="browse-files-by-type-in-the-network-panel"></a>在"网络"面板中按类型浏览文件

请参阅 [按资源类型筛选](../network/index.md#filter-by-resource-type)。

:::image type="complex" source="../media/resources-network-resources-filter-css.msft.png" alt-text="在网络日志中筛选 CSS" lightbox="../media/resources-network-resources-filter-css.msft.png":::
   在网络 **日志中筛选** CSS
:::image-end:::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/resources/index)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors#kayce-basques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
