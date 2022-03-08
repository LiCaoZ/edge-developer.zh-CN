---
title: 在“样式”窗格中编辑 CSS 字体样式和设置
description: 了解如何使用 Microsoft Edge 开发人员工具中的“样式”窗格更改 CSS 字体样式和设置。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
no-loc:
- Enable new font editor tool within the Styles pane
ms.date: 03/11/2021
ms.openlocfilehash: b10331f836f8784081d862104644531c5242b200
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431744"
---
# <a name="edit-css-font-styles-and-settings-in-the-styles-pane"></a>在“样式”窗格中编辑 CSS 字体样式和设置

:::image type="icon" source="../media/experimental-tag-14px.msft.png":::

为了在使用版式时更加轻松，现在"样式"**** 窗格中提供了**可视字体编辑器**。  使用 **字体编辑器**，可以更改字体设置，更改会立即呈现在浏览器中，所有这些更改都无需深入了解 CSS。  The **Elements** tool > **Styles** tab > **Font Editor** icon opens the **Font Editor**， which consists of two parts：

*  字体 **系列** 选择器。
*  **CSS 属性**编辑器。

网页版式是用户体验的重要组成部分。  希望确保字体遵循公司品牌准则，并确保内容在各种设备上按预期方式显示。  必须使用大小和线条高度让文本更易于阅读。  用户可以调整字体大小以满足个人需求。

对于特定字体在用户设备上不可用的情况，你应该提供回退字体选项。

近年来，CSS 为版式提供了更好的支持。  有数十种不同的 CSS 单位可用于定义文本大小。  有几个 CSS 属性可用于控制字体大小、间距、行高和其他排版功能。

目前，["样式"](../experimental-features/index.md#enable-the-font-editor-tool-within-the-styles-pane)窗格功能中的"启用新字体编辑器"工具是实验性的，你需要为开发人员工具Microsoft Edge[该工具](../experimental-features/index.md#turning-an-experiment-on-or-off)。

" **样式"窗格中** 的任何 CSS（字体定义或内联样式）都有"字体 **编辑器"** 图标。  若要打开可视字体 **编辑器，** 请单击" **字体编辑器"** 图标。

:::image type="content" source="../media/font-editor-icon.msft.png" alt-text="&quot;样式&quot;窗格中用于编辑字体设置的图标。" lightbox="../media/font-editor-icon.msft.png":::

" **字体编辑器** "将在"样式"窗格 **顶部** 打开：

:::image type="content" source="../media/font-editor-open.msft.png" alt-text="&quot;字体编辑器&quot;将在&quot;样式&quot;窗格顶部打开。" lightbox="../media/font-editor-open.msft.png":::

可视“**字体编辑器**”中的所有字段都是根据“**样式**”窗格中的 CSS 值填充的。  例如，在`line-height`"**** 样式"窗格中`160%`，定义设置为 ，因此行高文本字段将显示 `160`，而单位下拉列表显示 。`%`  此外，滑块会自动设置为与文本字段的值匹配。


<!-- ====================================================================== -->
## <a name="the-font-family-selector"></a>“字体系列”选择器

“字体系列”选择器位于可视“**字体编辑器**”的上部。  若要选择 CSS 规则的字体，请在 CSS 编辑器中，使用 **"** 字体系列"选择器。  可以针对每个 CSS 规则选择主字体和回退字体。

字体 **编辑器在** "样式" **窗格顶部打开** ，其中突出显示了 **"字体系列** "选择器：

:::image type="content" source="../media/font-editor-font-family.msft.png" alt-text="字体编辑器在&quot;样式&quot;窗格顶部打开，其中突出显示了&quot;字体系列&quot;选择器。" lightbox="../media/font-editor-font-family.msft.png":::

使用 **"字体系列** "下拉列表选择字体。  字体分为四组：

*  **计算字体**，即样式窗格中样式表**提供的字体。**
*  **系统**字体，即当前操作系统上提供的字体。
*  **常规字体系列，** 如 `serif` 或 `sans-serif`。
*  **全局值**，如 `inherit`、 `initial`和 `unset`。

字体 **编辑器在** "样式" **窗格顶部打开** ，其中突出显示了 **"字体系列** "选择器：

:::image type="content" source="../media/font-editor-font-family-list.msft.png" alt-text="字体编辑器在&quot;样式&quot;窗格顶部打开，其中突出显示了&quot;字体系列&quot;选择器。" lightbox="../media/font-editor-font-family-list.msft.png":::

选择字体后，将显示另一个下拉菜单，供你选择回退字体。  你最多可以选择八种回退字体。  若要删除字体，请单击"删除 **字体系列"** 图标。

<!--:::image type="content" source="../media/font-editor-defining-fonts.msft.png" alt-text="The font editor with a defined list of fonts and fallback fonts." lightbox="../media/font-editor-defining-fonts.msft.png":::-->

> [!NOTE]
> 如果选择字体系列全局值，则不会获得另一个下拉菜单，因为 CSS 中没有回退。


<!-- ====================================================================== -->
## <a name="the-css-properties-editor"></a>“CSS 属性”编辑器

您可以在可视字体编辑器的下半部分更改 CSS **字体属性**。  可以使用任何 UI 控件更改字号、行高、字体粗细和字母间距。  所做的更改将立即在浏览器中应用。

" **字体编辑器** "在"样式" **窗格顶部打开** ，其中突出显示了 CSS 属性：

:::image type="content" source="../media/font-editor-css-properties.msft.png" alt-text="&quot;字体编辑器&quot;在&quot;样式&quot;窗格顶部打开，其中突出显示了 CSS 属性。" lightbox="../media/font-editor-css-properties.msft.png":::

您还可以使用可视字体编辑器转换 CSS **单位**。  例如，可以在 CSS 规则（其中字体大小滑块最初设置为 ）上**** 使用此工具`16 pixels`。  现在，使用单位下拉列表并选择值 `em`。  显示的 `1 em` 等于 `16 pixels`。

将字体大小更改为 `16 pixels`：

:::image type="content" source="../media/font-editor-setting-to-16px.msft.png" alt-text="将字体大小更改为 16 像素。" lightbox="../media/font-editor-setting-to-16px.msft.png":::

打开"单位"下拉列表以转换为 `em`：

:::image type="content" source="../media/font-editor-converted-to-em.msft.png" alt-text="打开单位下拉列表以转换为 em。" lightbox="../media/font-editor-converted-to-em.msft.png":::

"单位"下拉列表提供所有可用的数值 CSS 单位。  字体大小、线条高度、字体粗细和间距都使用不同的单位。  当文本框具有焦点时，可以按 `arrow up` 和 `arrow down` 键来微调设置。  若要将滑块与键盘一同使用，请按 `arrow left` 和 `arrow down` 键。

“CSS 属性”编辑器还包括预设关键字。  若要使用预设关键字，请在右侧单击图标 `Toggle Input Type` 。  UI 发生更改，并显示预设关键字的下拉列表。  若要使用滑块和其他 UI 控件返回到 UI，请再次单击 `Toggle Input Type` 该图标。

打开预设关键字界面：

:::image type="content" source="../media/font-editor-preset-font-sizes.msft.png" alt-text="打开预设关键字界面。" lightbox="../media/font-editor-preset-font-sizes.msft.png":::
