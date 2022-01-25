---
title: CSS-in-JS 框架的样式编辑
description: 以针对 JavaScript 设置格式并准备粘贴到 JavaScript 文件中的方式复制样式规则的声明。  编辑最初由 CSSOM 函数定义的样式规则。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/25/2021
ms.openlocfilehash: 0fb85caa29ed59ac47ae696c11880cd7d3c57114
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12318924"
---
<!-- Copyright Alex Rudenko

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License. -->
# <a name="style-editing-for-css-in-js-frameworks"></a>CSS-in-JS 框架的样式编辑

在 **"样式** "选项卡中，您可以复制样式规则的声明，其格式为 JavaScript 并准备粘贴到 JavaScript 文件中。  这包括由 CSS-in-JS 函数调用定义的样式规则。  还可以编辑最初由 CSS-in-JS 函数调用定义的样式规则。


<!-- ====================================================================== -->
## <a name="copying-style-rule-declarations-to-paste-them-with-javascript-syntax"></a>复制样式规则声明以使用 JavaScript 语法粘贴它们

从 **"样式** "窗格中，您可以复制样式规则的声明，其格式为 JavaScript 并准备粘贴到 JavaScript 文件中。

使用 CSS-in-JS 库时，可以将 CSS 声明 (CSS 属性和值) 以便它们会自动格式化为 JavaScript。  不必手动编辑复制的 CSS 以匹配 JavaScript 的语法。  可以在样式规则中复制单个 CSS 声明或所有声明，然后将其直接粘贴到 JavaScript 文件中，而不会遇到语法问题。

将样式规则复制为 JavaScript：

1. 在**元素**工具的**样式**窗格中，打开样式规则中声明的上下文菜单（右键单击）。

1. 选择**将声明复制为 JS** 或**将所有声明复制为 JS** 。

1. 将复制的 CSS 粘贴到文本编辑器中的 JavaScript 文件中，例如Visual Studio Code。  例如：`'--more-link': 'lime'`。

:::image type="complex" source="images/copy-declaration-as-js.msft.png" alt-text="样式规则的上下文菜单，包括&quot;将声明复制为 JS&quot;和&quot;将所有声明复制为 JS&quot;命令" lightbox="images/copy-declaration-as-js.msft.png":::
   样式规则的上下文菜单，包括 **复制声明为 JS** 和 **复制所有声明作为 JS** 命令
:::image-end:::

此功能从版本 93 Microsoft Edge开始提供。 <!-- delete statement sometime after September 2, 2021 --> 若要详细了解如何查看和更改 CSS，请导航到 [CSS 功能参考](reference.md)。


<!-- ====================================================================== -->
## <a name="editing-style-rules-that-were-initially-defined-by-a-cssom-function"></a>编辑最初由 CSSOM 函数定义的样式规则

<!-- from https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/whats-new/2020/06/devtools#style-editing-for-css-in-js-frameworks -->

" **样式** "窗格支持使用 CSS 对象模型和 [CSSOM ](https://drafts.csswg.org/cssom) (API 创建的) 样式。  许多 CSS-in-JS 框架和库在构建样式的底层使用 CSS 对象模型 API。

您可以使用可构造样式表编辑在 JavaScript [中添加的样式](https://wicg.github.io/construct-stylesheets/)。  可构造的样式表是使用 Shadow DOM 时创建和分发可重用样式 [的一种方法](https://developer.mozilla.org/docs/Web/Web_Components/Using_shadow_DOM)。

### <a name="example"></a>示例

在此示例代码中，样式规则最初通过调用 CSS 对象模型 (CSSOM) 函数进行定义，然后使用"样式"窗格编辑 **样式** 规则。  对象 `CSSStyleSheet` 包含 CSSOM API，例如 `insertRule()` 。  然后 `h1` ，最初由函数添加的 `CSSStyleSheet` 样式在"样式"窗格中可编辑。 ****

```javascript
//Add CSS-in-JS button

function addStyle() {
  const sheet = new CSSStyleSheet();
  sheet.insertRule(`h1 {
    background: pink;
    text-transform: uppercase;
  }`);
  document.adoptedStyleSheets = [sheet];
}
```

此示例演示如何更改由 CSS 对象模型函数 `background` `h1` 添加的样式的属性 `insertRule()` 。  颜色最初通过调用 CSS 对象模型函数进行设置，然后可以使用"样式"窗格从 更改为 `background` `pink` `lightblue` 。 ****

:::image type="complex" source="../media/css-in-js.msft.png" alt-text="将随 CSSStyleSheet 一起添加的 h1 样式的背景属性从粉色更改为浅色" lightbox="../media/css-in-js.msft.png":::
   将 `background` 随 一起 `h1` 添加的样式 `CSSStyleSheet` 的属性从 更改 `pink` 到 `lightblue` 。
:::image-end:::

通过使用 [CSS-in-JS](https://codepen.io/zoherghadyali/full/abdGrPZ)的示例试用此功能。


<!-- ====================================================================== -->
## <a name="what-is-css-in-js"></a>什么是 CSS-in-JS？

本节摘自 DevTools 中的博客文章 [CSS-in-JS 支持](https://developers.google.com/web/updates/2021/02/css-in-js)。

下面是 _CSS-in-JS_的含义，以及它不同于常规 CSS 的方式。  _CSS-in-JS_的定义有点模糊。  从广泛的意义上说，这是一种使用 JavaScript 管理 CSS 代码的方法。  例如，这可能意味着 CSS 内容是使用 JavaScript 定义的，而最终的 CSS 输出由应用进行生成。

在 DevTools 上下文中 _，CSS-in-JS_ 意味着 CSS 内容通过 CSS 对象模型 API 注入页面。  常规 CSS 使用 或 元素进行注入，并且具有静态源 (如 DOM 节点或网络 `<style>` `<link>` 资源) 。  相比之下，CSS-in-JS 通常没有静态源。  此处的一个特例是，可以使用 CSS 对象模型 API 更新元素的内容，从而导致源与实际的 `<style>` CSS 样式表不同步。

如果使用任何 CSS-in-JS 库 (如样式组件、百年计划或 JSS) ，该库可能会使用 CSS 对象模型 API 在底层注入样式，具体取决于开发模式和浏览器。

我们来看看如何使用 CSS 对象模型 API 注入样式表的一些示例，类似于某些 CSS-in-JS 库使用的方法。

```javascript
// Insert new rule to an existing CSS stylesheet
const element = document.querySelector('style');
const stylesheet = element.sheet;
stylesheet.replaceSync('.some { color: blue; }');
stylesheet.insertRule('.some { color: green; }');
```

您还可以创建一个全新样式表：

```javascript
// Create a completely new stylesheet
const sheet = new CSSStyleSheet();
stylesheet.replaceSync('.some { color: blue; }');
stylesheet.insertRule('.some { color: green; }');
```

```javascript
// Apply constructed stylesheet to the document
document.adoptedStyleSheets = [...document.adoptedStyleSheets, sheet];
```

### <a name="css-support-in-devtools"></a>DevTools 中的 CSS 支持

在 DevTools 中，处理 CSS 时最常用的功能是" **样式"** 窗格。  在 **"样式** "窗格中，您可以查看哪些 CSS-in-JS 规则适用于特定元素。  还可以编辑 CSS-in-JS 规则并实时查看页面上的更改。

" **样式** "窗格支持可以使用 CSS 对象模型 API 修改的 CSS 规则。  CSS-in-JS 样式有时被描述__ 为构造样式，以指示这些样式是使用 Web API 构建的。

<!-- video https://storage.googleapis.com/chrome-gcs-uploader.appspot.com/video/dPDCek3EhZgLQPGtEG3y0fTn4v82/Jy8q9gPbQknRturLyCsq.mp4 -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/blog/css-in-js/) ，由 [Alex 以](https://developers.google.com/web/resources/contributors#alex-rudenko) 技术编写 (Chrome DevTools \& Lighthouse) 。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
