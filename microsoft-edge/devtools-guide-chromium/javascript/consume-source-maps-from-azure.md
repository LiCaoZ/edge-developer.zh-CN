---
title: 使用Azure Artifacts符号服务器源映射安全地调试原始代码
description: 了解如何将 DevTools 配置为使用来自 Azure Artifacts 符号服务器的源地图，以在 DevTools 中安全调试原始源代码。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/02/2022
ms.openlocfilehash: a9ed028c7dded5baf985dbbf3e23050b9e1ba20f
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433737"
---
# <a name="securely-debug-original-code-by-using-azure-artifacts-symbol-server-source-maps"></a>使用Azure Artifacts符号服务器源映射安全地调试原始代码

若要安全地在 DevTools 中查看和使用原始开发源代码，而不是 Web 服务器返回的已编译、缩小和捆绑的生产代码，可以使用在 Azure Artifacts 符号服务器上发布的源映射。

源映射将编译的生产代码映射到原始开发源文件。 在 DevTools 中，你可以查看并处理熟悉的开发源文件，而不是已编译的代码。 若要了解有关源映射和在 DevTools 中使用源映射的信息，请参阅将处理的代码映射到原始 [源代码，以便进行调试](source-maps.md)。

通过从符号服务器Azure Artifacts源地图，可以安全地检索原始开发源代码来调试生产网站。


<!-- ====================================================================== -->
## <a name="prerequisite-publish-source-maps-to-the-azure-artifacts-symbol-server"></a>先决条件：将源映射发布到Azure Artifacts符号服务器

若要在 DevTools Azure Artifacts符号服务器使用源映射，需要先将源映射发布到服务器。

若要了解如何发布源地图，请参阅通过将源映射发布到符号服务器来安全调试[Azure Artifacts代码](publish-source-maps-to-azure.md)。


<!-- ====================================================================== -->
## <a name="step-1-generate-a-personal-access-token-for-azure-devops"></a>步骤 1：为用户生成个人访问Azure DevOps

为了从 Azure Artifacts 符号服务器获取源映射，DevTools 使用提取协议与 Azure DevOps 通信，这需要有效的个人访问令牌 (PAT) 。

若要生成一个 PAT，Azure DevOps：

1. 通过进入 Azure DevOps登录到组织`https://dev.azure.com/{yourorganization}`。

1. In Azure DevOps， go to **User settingsPerson** >  **access tokens**：
    
   !["用户设置"菜单Azure DevOps，包含"个人访问令牌"命令。](images/ado-pat-settings.png)

   将显示 **"个人访问令牌"** 页：

   ![页面中的"个人访问令牌"Azure DevOps。](images/ado-pat-page.png)

1. 单击 **"新建令牌"**。  将 **打开"创建新的个人访问令牌** "对话框：

   !["创建新的个人访问令牌"对话框，选中符号的"读取"范围。](images/ado-pat-config-read.png)

1. 在 **"名称** "文本框中，输入 PAT 的名称，如 **DevTools 源映射**。

1. 在" **到期** "部分，输入 PAT 的到期日期。

1. 在" **范围"** 部分，单击 **"显示所有范围"** 以展开该部分。

1. 向下滚动到 **"符号"**，然后选中"读取 **"** 复选框。

1. 单击" **创建"** 按钮。  成功 **！** 将显示对话框：

   !["成功！"。 要复制的 PAT 对话框。](images/ado-pat-success-copy-clipboard.png)

1. 单击" **复制到剪贴板"** 按钮以复制 PAT。  请务必复制令牌，将其存储在安全的位置。 为了安全，它不会再次显示。

若要了解有关 PAT 的更多信息，请参阅 [使用个人访问令牌](/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)。


<!-- ====================================================================== -->
## <a name="step-2-configure-devtools"></a>步骤 2：配置 DevTools

现在，需要使用 PAT 配置 DevTools，以成功检索源地图。

配置 DevTools：

1. 若要打开 DevTools，请在Microsoft Edge中右键单击网页，然后选择"检查 **"**。  或者，按 `Ctrl`++`Shift``I` (Windows、Linux) 或 (`I` `Command`+`Option`+macOS) 。

1. 在 DevTools 中，**** 单击设置 (设置![图标](../media/settings-gear-icon-light-theme.png)。) >**符号服务器"**。

1. 在"**Azure DevOps组织**"文本框中，输入Azure DevOps创建 PAT 的组织。

1. 在"**Azure DevOps访问令牌**"文本框中，粘贴 PAT。

   ![DevTools 设置中的符号服务器配置屏幕](images/ado-pat-devtools.png)

1. 单击**右上角的 x** 以关闭**设置面板，** 然后单击"**重新加载 DevTools"** 按钮。


<!-- ====================================================================== -->
## <a name="step-3-retrieve-original-code-in-devtools"></a>步骤 3：在 DevTools 中检索原始代码

执行上述设置步骤后，在使用 DevTools 处理已发布符号的网站内部版本时，现在可以看到原始源代码，而不是转换后的代码。

*  在 **控制台工具** 中，从日志消息到源文件的链接将转到原始文件，而不是已编译的文件。

*  单步执行"源"**** 工具中的代码时，原始文件将列在左侧**** 的"导航器"窗格中。

*  在 **"源**"工具中，指向显示在"调试器"窗格**** 的"调用堆栈"中的**源文件的链接将**打开原始源文件。


<!-- ====================================================================== -->
## <a name="check-the-status-of-downloaded-source-maps"></a>检查已下载源地图的状态

可以使用 Source 地图 **Monitor 工具检查**源地图的状态。

若要了解有关 Source **地图 Monitor** 工具及其如何帮助监视请求的源映射的源文件以及是否已加载这些源映射，请参阅 Source [地图 Monitor 工具](../source-maps-monitor/source-maps-monitor-tool.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [通过将源映射发布到Azure Artifacts符号服务器来安全地调试原始代码](publish-source-maps-to-azure.md)
* [将已处理的代码映射到原始源代码，以便进行调试](source-maps.md)
* [源地图监视器工具](../source-maps-monitor/source-maps-monitor-tool.md)
