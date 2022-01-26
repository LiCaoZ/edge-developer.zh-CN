---
title: 在文件中打开Visual Studio Code
description: 如果你处理本地项目并且已安装Microsoft Visual Studio代码，你可以在此项目中打开文件，而不是源工具，将更改从 DevTools 实时同步到源文件。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 09/22/2021
ms.openlocfilehash: 349d39430d49aaf5ba2f01a382ae4f6f949ac8de
ms.sourcegitcommit: aec518f7d415ebee7a7d9cc177f987b8a86f9483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2022
ms.locfileid: "12324865"
---
# <a name="opening-source-files-in-visual-studio-code"></a>在文件中打开Visual Studio Code

实验 `Open source files in Visual Studio Code` 允许你使用 Microsoft Edge Tools，但在 Visual Studio Code 而不是在 DevTools 源工具的代码编辑器中编辑你的文件。

如果使用 Visual Studio Code并且使用 DevTools 更改 CSS 规则，那么与使用 Visual Studio Code 中的代码编辑器相反，您必须使用 DevTools 的"源"工具中的代码编辑器，这一点似乎有些奇怪。  通过此实验，我们想要更改这一点。  这就是我们将新实验添加到开发人员工具的原因。  当你在实验过程中打开开放源文件**Visual Studio Code，** 本地文件将得到不同的处理。


<!-- ====================================================================== -->
## <a name="setting-up-editing-local-files-in-visual-studio-code"></a>设置编辑本地文件Visual Studio Code

首先，选择"开发工具">设置"**** 实验""打开Visual Studio Code"源文件"，然后重新  >  ****  >  **** 启动 DevTools。

启用此实验后，假设在Microsoft Edge中，转到本地服务器 (或) 打开 `http://localhost` `http://127.0.0.1` 本地文件。

:::image type="complex" source="../media/experiment-sources-in-code-local-project.msft..png" alt-text="Microsoft Edge打开本地文件。" lightbox="../media/experiment-sources-in-code-local-project.msft..png":::
   Microsoft Edge打开本地文件。
:::image-end:::

打开 DevTools 时，系统会提示你标识根文件夹。  你可以选择退出， **选择关闭** `x` () 或选择 `Don't show again` 按钮。  可以通过选择链接获取 `Learn more` 详细信息。

:::image type="complex" source="../media/experiment-sources-in-code-identify-root-folder.msft.png" alt-text="开发人员工具显示一个信息栏，要求您标识根文件夹。" lightbox="../media/experiment-sources-in-code-identify-root-folder.msft.png":::
   开发人员工具显示一个信息栏，要求您标识根文件夹
:::image-end:::

如果选择" **设置根文件夹"** 按钮，操作系统将提示你导航到该文件夹并选择它。

:::image type="complex" source="../media/experiment-sources-in-code-pick-folder.msft.png" alt-text="使用操作系统的文件管理器选取根文件夹的位置。" lightbox="../media/experiment-sources-in-code-pick-folder.msft.png":::
   使用操作系统的文件管理器选取根文件夹的位置
:::image-end:::

选择根文件夹后，需要授予 DevTools 对文件夹的完全访问权限。  工具栏上方有一个包含"**** 允许"**** 或"拒绝"按钮的提示，询问你是否向 DevTools 授予访问文件夹的权限。

:::image type="complex" source="../media/experiment-sources-in-code-allow-access.msft.png" alt-text="要求获取文件夹访问权限的 DevTools。" lightbox="../media/experiment-sources-in-code-allow-access.msft.png":::
   要求获取文件夹访问权限的 DevTools
:::image-end:::

授予权限后，你选择的文件夹将添加为 DevTools 中的 Workspace，位于"源"工具的 **"文件系统****"选项卡**中。  这意味着，在 DevTools 中编辑的任何文件现在Microsoft Visual Studio代码而不是源工具中打开。 作为指示器，我们在文件名 `linked` 旁边显示一个图标。  本示例中，我们将选择"样式 `base.css` "工具 **中** 的链接。

:::image type="complex" source="../media/experiment-sources-in-code-selecting-link.msft.png" alt-text="在&quot;样式&quot;工具中选择文件链接将打开Visual Studio Code。" lightbox="../media/experiment-sources-in-code-selecting-link.msft.png":::
   在"样式"工具**中选择**文件链接将打开Visual Studio Code
:::image-end:::

DevTools 打开一个 Visual Studio Code，并显示根文件夹中的所有文件。  DevTools 还会打开所选的文件，滚动到 CSS 选择器的正确行。

:::image type="complex" source="../media/experiment-sources-in-code-editor-open.msft.png" alt-text="Visual Studio Code打开根文件夹文件，所选文件打开。" lightbox="../media/experiment-sources-in-code-editor-open.msft.png":::
   Visual Studio Code根文件夹文件并打开所选文件后打开
:::image-end:::

现在，你在 DevTools 中对文件进行的任何更改都将同步到Visual Studio Code。  例如，如果将规则添加到正文的样式中，同一 CSS 规则将自动添加到 Visual Studio Code 的代码 `background: green` `base.css` 编辑器中。

:::image type="complex" source="../media/experiment-sources-in-code-code-synced.msft.png" alt-text="现在，样式工具中的代码更改将反映在 Visual Studio Code 中的源代码中。" lightbox="../media/experiment-sources-in-code-code-synced.msft.png":::
   现在，样式工具中的代码更改将反映在 Visual Studio Code
:::image-end:::


<!-- ====================================================================== -->
## <a name="changing-the-workspace-settings"></a>更改工作区设置

如果你通过选择齿轮图标或设置上的设置 (转到 DevTools **** ****) ，你可以更改实验 `Shift + ?` 的行为。  在选择 **"工作区"** 页**设置，** 您有几个选项。

:::image type="complex" source="../media/experiment-sources-in-code-workspace-settings.msft.png" alt-text="工作区的设置窗格显示多个选项。" lightbox="../media/experiment-sources-in-code-workspace-settings.msft.png":::
   显示多个选项的工作区的设置窗格
:::image-end:::

**"设置**  >  **工作区**"页列出了工作区以及配置选项。

*  若要设置是否打开 Visual Studio Code 中的源文件，请选中"在Visual Studio Code**打开源文件**"复选框。

*  若要自动将 DevTools 更改保存到磁盘，请选中" **将 DevTools 更改保存到磁盘"** 复选框。

*  若要自动从工作区文件夹中排除文件夹，请使用 **"文件夹排除模式"** 文本框。

*  若要从特定工作区中排除文件夹，请选择"已**** 排除文件夹"旁边的"**添加"** 按钮。

*  若要添加其他工作区，请选择" **添加文件夹"** 按钮。
