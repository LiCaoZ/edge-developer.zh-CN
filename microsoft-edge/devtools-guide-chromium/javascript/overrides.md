---
title: 使用本地副本替代网页资源（“替代”选项卡）
description: 替代功能是 DevTools Microsoft Edge源工具中的一项功能，允许你将网页资源复制到硬盘驱动器。  刷新网页时，DevTools 不会加载资源，而是将其替换为本地副本。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/11/2020
---
# <a name="override-webpage-resources-with-local-copies-overrides-tab"></a>使用本地副本替代网页资源（“替代”选项卡）

有时你需要尝试一些可能的网页修补程序，但你无法访问源文件，或者更改页面需要一个缓慢而复杂的生成过程。  可以在 DevTools 中调试和修复所有类型的问题。  但更改不会保留;而是刷新本地文件后，所有工作都消失。  源 [工具中的替代](../sources/index.md) 功能可帮助你解决此问题。

现在，您可以利用当前网页的资源，并在本地存储该资源。  刷新网页时，浏览器不会从服务器加载资源。  相反，浏览器会用你的本地资源副本替换服务器资源。


<!-- ====================================================================== -->
## <a name="setting-up-your-local-folder-to-store-overrides"></a>将本地文件夹设置为存储替代

1. 导航到 **"源"** 工具。
1. 在左侧 **导航器** (窗格中，) " **替代"** 选项卡。 如果未 **显示"替代** "选项卡，请单击 <code>&#x0226B;</code><!--`≫`--> 图标。

    " **源** "工具没有足够的空间来显示 **"替代"** 选项卡：

   :::image type="content" source="../media/javascript-overrides-overflow-menu.msft.png" alt-text="显示替代选项的空间不足的源工具。" lightbox="../media/javascript-overrides-overflow-menu.msft.png":::

    选择 **"替代"** 选项卡：

   :::image type="content" source="../media/javascript-overrides-menu.msft.png" alt-text="选择&quot;替代&quot;选项卡。" lightbox="../media/javascript-overrides-menu.msft.png":::

1. 在本地计算机上选择一个文件夹，以存储要替换的资源文件。  若要搜索文件夹，请单击 **" + 选择文件夹"进行替代**。

   :::image type="content" source="../media/javascript-overrides-select-folder.msft.png" alt-text="选择要用于替代的文件夹。" lightbox="../media/javascript-overrides-select-folder.msft.png":::

1. DevTools 警告你必须具有对文件夹的完全访问权限，并且不应显示任何敏感信息。  选择 **"允许** "以授予访问权限。

   :::image type="content" source="../media/javascript-overrides-give-access-to-folder.msft.png" alt-text="授予 DevTools 对文件夹的访问权限。" lightbox="../media/javascript-overrides-give-access-to-folder.msft.png":::

1. 在 **"覆盖"** 选项卡中，"启用本地覆盖"旁边 **会显示一个复选框**。  "启用本地覆盖 **"右侧****是"清除**配置"图标，可用于删除本地覆盖设置。  现在，你已完成文件夹设置，并且已准备好将实时资源替换为本地资源。

   :::image type="content" source="../media/javascript-overrides-folder-setup-complete.msft.png" alt-text="成功设置替代文件夹。" lightbox="../media/javascript-overrides-folder-setup-complete.msft.png":::


<!-- ====================================================================== -->
## <a name="adding-files-to-your-overrides-folder"></a>将文件添加到 Overrides 文件夹

若要将文件添加到替代文件夹，请打开 **"元素** "工具并检查网页。  若要编辑，请单击样式检查器中的 CSS **文件** 的名称。

在样式检查器 **中选择** 文件：

:::image type="content" source="../media/javascript-overrides-select-css-file.msft.png" alt-text="在样式检查器中选择文件。" lightbox="../media/javascript-overrides-select-css-file.msft.png":::

在 **"源** "编辑器中，右键单击所选文件的文件名，然后单击"保存 **替代"**。

在"源"编辑器中，将文件的名称添加到替代列表中：

:::image type="content" source="../media/javascript-overrides-file-name.msft.png" alt-text="在&quot;源&quot;编辑器中，将文件的名称添加到替代列表。" lightbox="../media/javascript-overrides-file-name.msft.png":::

右键单击文件名，然后选择" **保存替代"**：

:::image type="content" source="../media/javascript-overrides-save-for-overrides.msft.png" alt-text="右键单击文件名，然后选择&quot;保存替代&quot;。" lightbox="../media/javascript-overrides-save-for-overrides.msft.png":::

该文件存储在替代文件夹中。  验证 DevTools 是否使用具有正确目录结构的文件的 URL 创建名为 的文件夹。  文件存储在内部。  编辑器中的文件名现在还显示一个紫色点，指示文件是本地文件，而不是实时文件。

已成功将该文件存储在 overrides 文件夹中：

:::image type="content" source="../media/javascript-overrides-file-stored.msft.png" alt-text="已成功将该文件存储在 overrides 文件夹中。" lightbox="../media/javascript-overrides-file-stored.msft.png":::

在下面的示例中，现在可以更改网页的样式。  若要在文件周围添加红色边框，在 **"** 样式"编辑器上复制以下样式，并将其添加到 body 元素中。

```css
border: 10px solid firebrick
```

该文件将自动保存在您的计算机上。  如果刷新该文件，将显示边框，并且不会丢失任何工作。

通过编辑替代文件夹中的文件来永久更改网页样式：

:::image type="content" source="../media/javascript-overrides-changing-styles.msft.png" alt-text="通过编辑替代文件夹中的文件来永久更改网页样式。" lightbox="../media/javascript-overrides-changing-styles.msft.png":::

在 **"源** "工具的" **页面** "部分，右键单击某个文件，然后将其添加到替代项。  已位于替代文件夹中的文件在图标上有一个紫色点。

从"源"工具 **中选择** 文件进行替代：

:::image type="content" source="../media/javascript-overrides-safe-from-sources.msft.png" alt-text="从&quot;源&quot;工具中选择文件进行替代。" lightbox="../media/javascript-overrides-safe-from-sources.msft.png":::

或者，在 **"网络"** 工具上，右键单击某个文件，然后将其添加到覆盖中。  当替代生效时，位于您的计算机而不是实时网页中的文件。  当替代生效时，在 **"** 网络"工具上，找到文件名旁边的警告图标。

从网络工具 **中选择** 文件进行替代：

:::image type="content" source="../media/javascript-overrides-network.msft.png" alt-text="从网络工具中选择一个文件进行替代。" lightbox="../media/javascript-overrides-network.msft.png":::


<!-- ====================================================================== -->
## <a name="two-way-interaction-of-overrides"></a>覆盖的双向交互

使用 DevTools 的 **"** 源"工具提供的编辑器或要更改文件的任何编辑器。  更改将跨访问覆盖文件夹中文件的所有产品进行同步。
