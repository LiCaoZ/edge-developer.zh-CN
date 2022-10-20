---
title: '从“样式”选项卡中更新 .css 文件 (CSS 镜像编辑) '
description: 在适用于Visual Studio Code的 Microsoft Edge 开发人员工具扩展中使用 CSS 镜像编辑从“样式”选项卡同步实时更改。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/06/2022
ms.openlocfilehash: 10f9cd4c5485616d513416bc5b8effb5c4f10f17
ms.sourcegitcommit: 87adf3723b7434231f3e65663846eb8b404a92e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2022
ms.locfileid: "12816089"
---
# <a name="update-css-files-from-within-the-styles-tab-css-mirror-editing"></a>从“样式”选项卡中更新 .css 文件 (CSS 镜像编辑) 

CSS 镜像编辑提供双向交互，以便你可以通过以下任一方式更改 CSS：

*  在代码编辑器中`.css`编辑文件，更改将镜像在 **Edge DevTools** 选项卡中的 **“元素**”工具中。

*  在 **“Edge DevTools**”选项卡中的 **“元素**”工具中，更改会在代码编辑器的文件中`.css`进行镜像。

默认情况下，会在扩展中启用 CSS 镜像编辑。  因此，在 DevTools 扩展的 **“元素**”工具的“**样式**”选项卡中，更改 CSS 选择器、规则或值时，会在更改值时自动编辑本地`.css`文件。

例如，选择正文元素的点大小值，然后按下`Up Arrow`，或者`Down Arrow`，如果打开`.css`文件，则可以在更改“**样式**”选项卡中的`.css`值时实时看到该值自动更改：

![更改“样式”选项卡中的值时，实时编辑 .css 文件](./css-mirror-editing-styles-tab-images/live-mirror-editing.png)

如果没有 CSS 镜像编辑，Microsoft Edge DevTools 中的“样 **式** ”选项卡非常适合调试和调整 CSS 选择器和 CSS 规则。  但是，尽管这些更改会立即在 Web 浏览器中呈现，但不会反映在文件 `.css` 中。  这意味着在“ **样式** ”选项卡中更改 CSS 后，需要将更改复制并粘贴回 `.css` 文件中。

CSS 镜像编辑是 Microsoft Edge DevTools 扩展的一项功能，可解决此问题。  在“**样式**”选项卡中所做的任何更改也会自动更改`.css`Visual Studio Code中打开的文件夹中的文件。  可以在“ **样式** ”选项卡中编辑任何 CSS 选择器或创建新的 CSS 选择器，并且所有更改都会在正确的 `.css` 文件中自动镜像。

CSS 镜像编辑还适用于 `.html` 包含 `<style>` 元素的文件，例如“成功”页。  步骤 2：通过单击“_开始使用 DevTools 扩展进行Visual Studio Code”_ 中的[默认页面的“启动实例”按钮来演示这一点： 启动 DevTools](./get-started.md#step-2-start-devtools-by-clicking-the-launch-instance-button-for-the-default-page)。


#### <a name="the-css-mirror-editing-checkbox"></a>CSS 镜像编辑复选框

如果使用 URL (而不是文件路径) ，则 CSS 镜像编辑需要在Visual Studio Code中打开网页源文件的文件夹，扩展插件可以映射到输入到地址栏或`launch.json`文件中的 URL 的网页资源。  如果没有本地源文件，但想要在 DevTools 中更改 CSS，请清除 **CSS 镜像编辑** 复选框，以防止有关映射和镜像编辑的错误消息。  请参阅下面的 [“启用 CSS 镜像编辑](#enabling-css-mirror-editing)”。


#### <a name="saving-the-changes-to-the-css-file"></a>保存对 .css 文件的更改

扩展不会自动保存它在编辑器中所做的更改。  编辑器中的文件选项卡上 `.css` 会显示一个白色圆圈;如果要保留这些更改，则需要手动保存这些更改。

如果关闭 Visual Studio 或当前文件夹或 `.css` 文件，Visual Studio 会提示保存更改。


<!-- ====================================================================== -->
## <a name="example-of-mirroring-changes-from-the-styles-tab-to-a-css-file"></a>从“样式”选项卡到 .css 文件的镜像更改示例

在以下示例中， `index.html` Visual Studio Code打开，并且 Microsoft Edge DevTools 扩展处于打开状态。  在 CSS 选择器中 `.searchbar` 选择弹性框图标，然后将该 `flex-direction` 图标更改为 `column`。

更改反映在 **“Edge DevTools** ”选项卡和 **“Edge DevTools：浏览器”** 选项卡中：

![在“样式”选项卡中选择弹性框图标以创建 CSS 更改](./css-mirror-editing-styles-tab-images/css-mirror-editing-start.png)

由于 CSS 镜像编辑，Visual Studio Code还会自动导航到正确的`.css`文件和相应的行号，并插入 `flex-direction: column` CSS 代码：

![更改 CSS 设置在正确的 .css 文件中创建了新的代码行](./css-mirror-editing-styles-tab-images/css-mirror-editing-changed-file.png)


<!-- ====================================================================== -->
## <a name="enabling-css-mirror-editing"></a>启用 CSS 镜像编辑

如果有可写、受信任的源文件，并且希望在源文件中自动编辑 DevTools 中的 CSS 更改，请选择 **CSS 镜像编辑** 复选框。  默认情况下会选择它。

如果仅在进行试验，则清除 **CSS 镜像编辑** 复选框，在 **“Edge DevTools：浏览器** ”选项卡的地址栏中存在 URL 而不是文件路径，并且没有通过活动栏> **资源管理器** 在本地使用源文件> **打开文件夹** 按钮，并且不希望出现有关映射和镜像编辑的错误消息。

若要启用或禁用 CSS 镜像编辑，请执行以下操作：

1. 在 **“Edge DevTools** ”选项卡的 **“元素”** 选项卡中，转到 **“样式”** 选项卡。

1. 选中或清除 **CSS 镜像编辑** 复选框：

   ![“元素”工具的“样式”面板中的复选框，用于启用或禁用 CSS 镜像](./css-mirror-editing-styles-tab-images/css-mirror-editing-checkbox.png)

   或者，打开命令菜单，开始键入 **“镜像**”一词，然后选择 **“Microsoft Edge Tools：切换镜像编辑|在工作区中对 CSS 文件进行关闭**：

   ![使用命令菜单聚焦 CSS 镜像编辑视图并打开或关闭 CSS 镜像编辑](./css-mirror-editing-styles-tab-images/css-mirror-editing-command.png)


<!-- ====================================================================== -->
## <a name="sourcemap-support"></a>Sourcemap 支持

在设置项目以生成源地图时，CSS 镜像还支持 Sass 或 CSS in-JS 等抽象。  我们在 GitHub 上存在跟踪问题，并欢迎有关如何改进此功能的任何反馈： [使用源图进行 CSS 镜像编辑：已知问题和反馈](https://github.com/microsoft/vscode-edge-devtools/issues/965)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [开始将 DevTools 扩展用于Visual Studio Code](./get-started.md)
* [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../microsoft-edge-devtools-extension.md)
