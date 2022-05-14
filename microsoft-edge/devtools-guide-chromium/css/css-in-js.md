---
title: CSS-in-JS 框架的样式编辑
description: 以为 JavaScript 设置格式并准备粘贴到 JavaScript 文件的方式复制样式规则的声明。  编辑最初由 CSSOM 函数定义的样式规则。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/25/2021
ms.openlocfilehash: 2c470b3d9b3c478ec321be2ffc65b898f704b674
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12513794"
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

在“ **样式”** 选项卡中，可以以为 JavaScript 设置格式并准备粘贴到 JavaScript 文件的方式复制样式规则的声明。  这包括由 CSS-in-JS 函数调用定义的样式规则。  还可以编辑最初由 CSS in-JS 函数调用定义的样式规则。


<!-- ====================================================================== -->
## <a name="copying-style-rule-declarations-to-paste-them-with-javascript-syntax"></a>复制样式规则声明以将其与 JavaScript 语法粘贴

在“ **样式** ”窗格中，可以以为 JavaScript 设置格式并准备粘贴到 JavaScript 文件的方式复制样式规则的声明。

使用 CSS in-JS 库时，可以复制 CSS 声明 (CSS 属性和值) ，以便自动为 JavaScript 设置格式。  无需手动编辑复制的 CSS 即可匹配 JavaScript 的语法。  可以复制单个 CSS 声明或样式规则中的所有声明，然后将其直接粘贴到 JavaScript 文件中，而不会出现语法问题。

将样式规则复制为 JavaScript：

1. 在 DevTools 中，打开 **“元素”** 工具，然后单击 **“样式”** 选项卡。

1. 在样式规则中右键单击声明，然后选择 **“复制声明”作为 JS** 或 **将所有声明复制为 JS**。

1. 将复制的 CSS 粘贴到文本编辑器中的 JavaScript 文件中，例如Visual Studio Code。  例如：`'--more-link': 'lime'`。

   :::image type="content" source="images/copy-declaration-as-js.msft.png" alt-text="样式规则的上下文菜单，包括“将声明复制为 JS”和“将所有声明复制为 JS”命令。" lightbox="images/copy-declaration-as-js.msft.png":::

此功能从Microsoft Edge版本 93 开始提供。 <!-- delete statement sometime after September 2, 2021 --> 要详细了解如何在 DevTools 中编写 CSS，请参阅 [CSS 功能参考](reference.md)。


<!-- ====================================================================== -->
## <a name="editing-style-rules-that-were-initially-defined-by-a-cssom-function"></a>编辑最初由 CSSOM 函数定义的样式规则

<!-- from https://docs.microsoft.com/microsoft-edge/devtools-guide-chromium/whats-new/2020/06/devtools#style-editing-for-css-in-js-frameworks -->

“ **样式** ”窗格支持使用 [CSS 对象模型 (CSSOM) ](https://drafts.csswg.org/cssom) API 创建的编辑样式。  许多 CSS in-JS 框架和库使用引擎盖下的 CSS 对象模型 API 来构造样式。

可以使用 [可构造样式表](https://wicg.github.io/construct-stylesheets/)编辑 JavaScript 中添加的样式。  可构造样式表是使用 [Shadow DOM](https://developer.mozilla.org/docs/Web/Web_Components/Using_shadow_DOM) 时创建和分发可重用样式的一种方式。

### <a name="example"></a>示例

在此示例代码中，样式规则最初是通过调用 CSS 对象模型 (CSSOM) 函数来定义的，然后使用“ **样式** ”窗格编辑样式规则。  该 `CSSStyleSheet` 对象包含 CSSOM API，例如 `insertRule()`。  `h1`函数最初添加`CSSStyleSheet`的样式随后可在“**样式**”窗格中进行编辑。

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

此示例演示如何更改 `background` CSS 对象模型函`insertRule()`数添加的样式的属性`h1`。  颜色`background`最初是通过调用 CSS 对象模型函数来设置的，然后可以使用“**样式**”窗格进行更改`pink``lightblue`。

:::image type="content" source="../media/css-in-js.msft.png" alt-text="将使用“CSSStyleSheet”添加的 h1 样式的背景属性从“粉红色”更改为“浅蓝色”。" lightbox="../media/css-in-js.msft.png":::

尝试 [使用 CSS in-JS 的示例](https://codepen.io/zoherghadyali/full/abdGrPZ)，尝试使用此功能。


<!-- ====================================================================== -->
## <a name="what-is-css-in-js"></a>什么是 CSS in-JS？

本部分摘自博客帖子 [DevTools 中的 CSS in-JS 支持](https://developers.google.com/web/updates/2021/02/css-in-js)。

以下是 _CSS in-JS_ 的含义，以及它与常规 CSS 有何不同。  _CSS in-JS_ 的定义有些模糊。  从广义上讲，这是一种使用 JavaScript 管理 CSS 代码的方法。  例如，这可能意味着使用 JavaScript 定义 CSS 内容，并且最终的 CSS 输出由应用即时生成。

在 DevTools 的上下文 _中，CSS in-JS_ 表示 CSS 内容由 CSS 对象模型 API 注入到页面中。  常规 CSS 是使用 `<style>` 或 `<link>` 元素注入的，并且它具有静态源 (，例如 DOM 节点或网络资源) 。  相比之下，JSS 中的 CSS 通常没有静态源。

此处的一 `<style>` 个特殊情况是，可以使用 CSS 对象模型 API 更新元素的内容，从而导致源与实际 CSS 样式表不同步。

如果使用任何 CSS in-JS 库 (（例如样式组件、情感或 JSS) ），则库可能会使用 CSS 对象模型 API 在引擎盖下注入样式，具体取决于开发模式和浏览器。

让我们看看一些示例，说明如何使用 CSS 对象模型 API 注入样式表，类似于某些 CSS in-JS 库使用的方法。

```javascript
// Insert new rule to an existing CSS stylesheet
const element = document.querySelector('style');
const stylesheet = element.sheet;
stylesheet.replaceSync('.some { color: blue; }');
stylesheet.insertRule('.some { color: green; }');
```

也可以创建全新的样式表：

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

在 DevTools 中，处理 CSS 时最常用的功能是“ **样式** ”窗格。  在“ **样式** ”窗格中，可以查看适用于特定元素的 CSS-in-JS 规则。  还可以编辑 CSS in-JS 规则，并实时查看页面上的更改。

“ **样式”** 窗格支持可使用 CSS 对象模型 API 修改的 CSS 规则。  CSS in-JS 样式有时被描述为 _构造_，以指示这些样式是使用 Web API 构造的。

<!-- video https://storage.googleapis.com/chrome-gcs-uploader.appspot.com/video/dPDCek3EhZgLQPGtEG3y0fTn4v82/Jy8q9gPbQknRturLyCsq.mp4 -->


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面 [在这里](https://developer.chrome.com/blog/css-in-js/) 找到，由 [亚历克斯·鲁登科](https://developers.google.com/web/resources/contributors#alex-rudenko) (技术作家，Chrome DevTools \& Lighthouse) 创作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
