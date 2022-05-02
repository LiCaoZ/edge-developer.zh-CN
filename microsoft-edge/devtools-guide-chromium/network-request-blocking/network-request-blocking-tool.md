---
title: 网络请求阻止工具
description: 使用 Microsoft Edge DevTools 中的网络请求阻止工具阻止选定的网络请求，了解某些资源不可用时网页的外观和行为。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/23/2022
ms.openlocfilehash: 535b9a0dbe880455d3244f73e48c4d73c552b9c8
ms.sourcegitcommit: 10b22f12f9e7ac118dd681c68d42766fb1524343
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2022
ms.locfileid: "12498211"
---
# <a name="network-request-blocking-tool"></a>网络请求阻止工具

使用 **网络请求阻止** 工具检查某些资源不可用时网页的外观和行为，例如图像文件、JavaScript 文件、字体或 CSS 样式表。  使用此工具测试对指定 URL 模式的阻止网络请求，并查看网页的行为方式。

当网页依赖于托管在 HTML 网页以外的其他服务器上的 _外部资源_ 时，有时这些服务器可能无响应或某些用户不可用。 发生这种情况时，Web 浏览器可能不会检索网页所依赖的某些资源。  请务必检查外部资源无法加载时网页的行为。  测试网页是正常处理缺失资源，还是对用户显示损坏。

创建阻止的网络请求并测试网页后，可以编辑或删除被阻止的网络请求。


<!-- ====================================================================== -->
## <a name="block-a-network-request"></a>阻止网络请求

阻止网络请求：

1. 转到要阻止网络请求的网页。

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。

1. 在 DevTools 的主工具栏上，单击 **“网络请求阻止** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 单击 **“添加模式** (![”模式图标。](media/add-pattern-icon.png)) 按钮。  自动选中 **“启用网络请求阻止** ”复选框。

1. 在 **阻止网络请求文本框的“文本”模式** 中，键入要阻止的网络请求的 URL。  可以键入完整的 URL，只需域名即可阻止来自此域的所有请求，也可以将其 `*` 部分替换为通配符模式匹配。
   
   例如， `contoso.com` 匹配 URL，例如：

   * `https://contoso.com`
   * `https://subdomain.contoso.com`
   * `https://subdomain.contoso.com/path/to/resource`

   并 `*.png` 匹配 URL，如下所示：
   
   * `https://www.contoso.com/resource.png`
   * `http://third-party.com/6469272/163348534-b90ea1a3-c33cbeb1aed8.png`

1. 单击“ **添加** ”按钮：

   ![阻止网络请求阻止工具中的 https：//*.contoso.com/* URL 模式。](media/block-network-request.png)


<!-- ====================================================================== -->
## <a name="delete-a-blocked-network-request"></a>删除阻止的网络请求

若要删除特定的网络阻止请求，请执行以下操作：

*  在 **网络请求阻止** 表中，将鼠标悬停在网络阻止请求上，然后单击“ **删除** (![删除阻止的请求图标](media/remove-blocked-request-icon.png)) 按钮：

   ![删除阻止的请求](media/remove-blocked-request.png)


一次性删除所有网络阻止请求：

*  在工具栏中，单击“ **删除所有模式** (![删除所有被阻止的请求图标](media/remove-all-blocked-requests-icon.png)) 按钮。


<!-- ====================================================================== -->
## <a name="modify-a-blocked-network-request"></a>修改阻止的网络请求

若要更改现有的已阻止网络请求，请执行以下操作：

*  在 **网络请求阻止** 表中，将鼠标悬停在被阻止的网络请求上，然后单击“ **编辑** (![编辑阻止的请求图标](media/edit-blocked-request-icon.png)) ：

   ![编辑阻止的请求](media/edit-blocked-request.png)


<!-- ====================================================================== -->
## <a name="toggle-network-request-blocking"></a>切换网络请求阻止

若要切换网络请求阻止，而无需删除并重新创建所有已阻止的网络请求：

*  在工具栏中，选择或清除 **“启用网络请求阻止”** 复选框：

   ![切换网络请求阻止](media/toggle-request-blocking.png)


<!-- ====================================================================== -->
## <a name="block-a-network-request-by-using-the-network-tool"></a>使用网络工具阻止网络请求

可以使用网络 **请求阻止** 工具或使用网络工具阻止网页发出的 **网络** 请求。

若要使用网络工具阻止 **网络** 请求，请执行以下操作：

1. 转到要阻止网络请求的网页。

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，单击“ **网络** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

1. 在底部窗格中的网络请求表中，找到要阻止的网络请求。

1. 右键单击网络请求，然后单击 **“阻止请求 URL** ”阻止此特定资源，或 **阻止请求域** 阻止来自同一域的所有资源：

   ![阻止网络工具](media/block-request-from-network-tool.png)


<!-- ====================================================================== -->
## <a name="try-the-network-request-blocking-tool"></a>试用网络请求阻止工具

若要尝试 **网络请求阻止** 工具，

1. 在单独的窗口或选项卡中，转到 [辅助功能测试演示网页](https://microsoftedge.github.io/Demos/devtools-a11y-testing/)。

1. 要打开 DevTools，请右击网页，然后选择“**检查**”。  或者，按“`Ctrl`+`Shift`+`I`”(Windows、Linux)或“`Command`+`Option`+`I`”(macOS)。  DevTools 随即打开。

1. 在 DevTools 的主工具栏上，选择 **“网络请求阻止** ”选项卡。 如果该选项卡不可见，请单击“ **更多”选项卡** (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 按钮，或者“ **更多工具** (![更多工具”图标。](../media/more-tools-icon-light-theme.png)) 按钮。

   将显示页面内容：

   ![网络请求阻止工具，不阻止任何 URL 模式，显示网页内容。](../media/network-request-blocking-tool-not-blocked.png)

1. 在 **“网络请求阻止** ”面板中，单击 **“添加模式** ” (![“更多”选项卡图标。](../media/more-tabs-icon-light-theme.png)) 图标或 **“添加模式** ”按钮（如果已显示）。

1. 在 **“文本”模式中阻止匹配的请求** 文本框，粘贴以下 URL 路径，然后单击“ **添加** ”按钮：

   ```http
   https://microsoftedge.github.io/Demos/
   ```
   
1.  刷新页面。  现在未显示页面的大多数元素，并且许多网络请求被指示为已阻止：

    ![网络请求阻止工具，阻止 DevTools GitHub Demos 服务器。](../media/network-request-blocking-tool.png)

1. 单击 **“删除所有模式** (![删除所有模式图标。](../media/network-request-blocking-tool-remove-all-patterns-icon.png)) 图标，然后单击 **”刷新**”。  页面内容将重新显示。
