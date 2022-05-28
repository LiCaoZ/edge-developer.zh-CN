---
title: 使用本地副本替代网页资源（“替代”选项卡）
description: 替代功能是 Microsoft Edge DevTools 的“源”工具中的一项功能，可用于将网页资源复制到硬盘驱动器。  刷新网页时，DevTools 不会加载资源，而是将其替换为本地副本。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/11/2020
ms.openlocfilehash: 645ff24f0e993aa496c9a8ec6ac3cea2d56d72e3
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12552586"
---
# <a name="override-webpage-resources-with-local-copies-overrides-tab"></a>使用本地副本替代网页资源（“替代”选项卡）

有时，你需要尝试一些可能的网页修复，但你无法访问源文件，或者更改页面需要缓慢而复杂的生成过程。  可以在 DevTools 中调试和修复所有类型的问题。  但是这些变化不会持续下去;刷新本地文件后，所有工作都已完成。  [“源](../sources/index.md)”工具中的“替代”功能可帮助你解决此问题。

现在可以获取当前网页的资源，并将其存储在本地。  刷新网页时，浏览器不会从服务器加载资源。  浏览器会将服务器资源替换为资源的本地副本。


<!-- ====================================================================== -->
## <a name="setting-up-your-local-folder-to-store-overrides"></a>设置本地文件夹以存储替代

1. 导航到 **“源** ”工具。
1. 在左侧)  (**导航器** 窗格中，单击“ **替代”** 选项卡。 如果未显示 **“替代** ”选项卡，请单击 <code>&#x0226B;</code><!--`≫`--> 图标。

    空间不足以显示 **“替代**”选项卡的 **“源**”工具：

   ![空间不足以显示替代选项的源工具。](../media/javascript-overrides-overflow-menu.msft.png)

    选择“ **替代** ”选项卡：

   ![选择“替代”选项卡。](../media/javascript-overrides-menu.msft.png)

1. 在本地计算机上选择一个文件夹来存储要替换的资源文件。  若要搜索文件夹，请单击 **“+ 选择”文件夹以进行重写**。

   ![选择要用于替代的文件夹。](../media/javascript-overrides-select-folder.msft.png)

1. DevTools 警告您，该文件夹必须具有完全访问权限，并且不应显示任何敏感信息。  选择 **“允许** ”以授予访问权限。

   ![授予 DevTools 对文件夹的访问权限。](../media/javascript-overrides-give-access-to-folder.msft.png)

1. 在“ **替代** ”选项卡中，“ **启用本地覆盖”** 旁边会显示一个复选框。  **启用本地替代**的右侧是一个 **Clear 配置**图标，可用于删除本地替代设置。  现在，你已完成文件夹的设置，并已准备好将实时资源替换为本地资源。

   ![成功设置重写文件夹。](../media/javascript-overrides-folder-setup-complete.msft.png)


<!-- ====================================================================== -->
## <a name="adding-files-to-your-overrides-folder"></a>将文件添加到 Overrides 文件夹

若要将文件添加到替代文件夹，请打开 **Elements** 工具并检查网页。  若要编辑，请在 **样式检查器** 中单击 CSS 文件的名称。

在 **样式检查器** 中选择文件：

![在样式检查器中选择文件。](../media/javascript-overrides-select-css-file.msft.png)

在 **“源** ”编辑器中，右键单击文件名，然后单击 **“保存以进行替代**”。

在“源”编辑器中，将文件的名称添加到替代列表：

![在“源”编辑器中，将文件的名称添加到替代列表。](../media/javascript-overrides-file-name.msft.png)

右键单击文件名，然后选择 **“保存以替代**”

![右键单击文件名，然后选择“保存以进行替代”。](../media/javascript-overrides-save-for-overrides.msft.png)

该文件存储在替代文件夹中。  验证 DevTools 是否创建了一个文件夹，该文件夹使用文件的 URL 和正确的目录结构进行命名。  文件存储在内部。  编辑器中的文件名现在还显示一个紫色点，指示文件是本地的，而不是实时的。

已成功将文件存储在替代文件夹中：

![已成功将文件存储在替代文件夹中。](../media/javascript-overrides-file-stored.msft.png)

在以下示例中，现在可以更改网页的样式。  若要在文件周围添加红色边框，请在 **Styles 编辑器** 上复制以下样式，并将其添加到正文元素。

```css
border: 10px solid firebrick
```

该文件会自动保存在计算机上。  如果刷新文件，则会显示边框，并且不会丢失任何工作。

通过编辑替代文件夹中的文件，永久更改网页样式：

![通过编辑替代文件夹中的文件，永久更改网页样式。](../media/javascript-overrides-changing-styles.msft.png)

在 **“源** ”工具的 **“页面** ”部分中，右键单击文件，然后将其添加到替代。  已在替代文件夹中的文件在图标上具有紫色点。

从 **源** 工具中选择文件以替代：

![从源工具中选择要重写的文件。](../media/javascript-overrides-safe-from-sources.msft.png)

或者，在 **网络** 工具上，右键单击某个文件，然后将其添加到替代。  当重写生效时，位于计算机上而不是来自实时网页的文件。  当重写生效时，在 **网络** 工具上，找到文件名旁边的警告图标。

从 **网络** 工具中选择文件以替代：

![从网络工具中选择要重写的文件。](../media/javascript-overrides-network.msft.png)


<!-- ====================================================================== -->
## <a name="two-way-interaction-of-overrides"></a>替代的双向交互

使用与 DevTools 的 **源** 工具或要更改文件的任何编辑器一起提供的编辑器。  更改会在访问覆盖文件夹中文件的所有产品中同步。
