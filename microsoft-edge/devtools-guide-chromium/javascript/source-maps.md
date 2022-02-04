---
title: 将预处理的代码映射到源代码
description: 即使组合、缩小或编译客户端代码，也保持其可读和可调试。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
---
<!-- Copyright Meggin Kearney and Paul Bakaus

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="map-preprocessed-code-to-source-code"></a>将预处理的代码映射到源代码

即使组合、缩小或编译客户端代码，也保持其可读和可调试。  使用源映射将源代码映射到已编译的代码。

### <a name="summary"></a>摘要

*  使用 Source 地图将缩小代码映射到源代码。  然后，您能够读取和调试原始源中的已编译代码。
*  只能使用能够生成源处理器的预处理器地图。
*  验证 Web 服务器能否为源服务器地图。

<!--
no longer in original file:
todo: add link to preprocessors capable of producing Source Maps when section is available
/web/tools/setup/setup-preprocessors?#supported_preprocessors
-->


<!-- ====================================================================== -->
## <a name="get-started-with-preprocessors"></a>预处理器入门

本文介绍如何在 DevTools 源工具地图 JavaScript 源应用程序交互。  <!--For a first overview of what preprocessors are, how each may help, and how Source Maps work; see Set Up CSS & JS Preprocessors.  -->

<!--
no longer in original file:
todo: add link to Set Up CSS & JS Preprocessors when section is available
/web/tools/setup/setup-preprocessors#debugging-and-editing-preprocessed-content
-->


<!-- ====================================================================== -->
## <a name="use-a-supported-preprocessor"></a>使用受支持的预处理器

使用能够创建源地图的微型程序。  <!--For the most popular options, see the preprocessor support section.  -->  有关扩展视图，请参阅源 [地图：语言、工具和其他信息](https://github.com/ryanseddon/source-map/wiki/Source-maps:-languages,-tools-and-other-info) Wiki 页面。

<!--
no longer in original file:
todo: add link to display the preprocessor support section when section is available
/web/tools/setup/setup-preprocessors?#supported_preprocessors
-->

通常将以下类型的预处理器与 Source 地图：

*  使用 ([、Traceur 和](https://babeljs.io) [) ](https://github.com/google/traceur-compiler/wiki/Getting-Started) 。
*  编译器 ([关闭编译器](https://github.com/google/closure-compiler)、 [TypeScript](https://www.typescriptlang.org)、 [CoffeeScript](https://coffeescript.org)、 [) ](https://www.dartlang.org) 。
*  [UglifyJS](https://github.com/mishoo/UglifyJS) (微型) 。


<!-- ====================================================================== -->
## <a name="source-maps-in-devtools-sources-tool"></a>DevTools 地图工具中的源源

来自地图的源文件会导致 DevTools 加载原始文件以及缩小的文件。  然后，使用原始文件设置断点并逐步执行代码。  同时，Microsoft Edge运行缩小代码。  通过运行代码，你可以错觉运行生产中的开发网站。

在 DevTools 地图源版本时，应该注意到 JavaScript 未编译，并且它引用的所有单个 JavaScript 文件都显示出来。  DevTools 地图源映射使用的是源映射，但基础功能实际上运行已编译的代码。

任何错误、日志和断点都映射到开发人员代码，以便进行出色的调试。  实际上，它让你产生一种在生产中运行开发网站的错觉。

### <a name="enable-source-maps-in-settings"></a>在设置地图源应用程序

默认情况下地图源应用程序。<!-- (as of Microsoft Edge 39)-->

若要确保启用源地图：

1. 打开 DevTools。

1. 选择**自定义和控制 DevTools (**) > `...` **设置**。

1. 在首选项**窗格的**"源"**下**，选择 **"启用 JavaScript 源地图**"。  还可以启用"启用 **CSS 源"地图**。

:::image type="content" source="../media/javascript-settings-preferences-sources-enable-javascript-source-maps.msft.png" alt-text="启用源地图。" lightbox="../media/javascript-settings-preferences-sources-enable-javascript-source-maps.msft.png":::

### <a name="debugging-with-source-maps"></a>使用 Source 地图

调试[代码并启用](index.md#step-4-step-through-the-code)地图时，源地图显示在两处：

*  在控制台中。  指向源的链接是原始文件，而不是生成的文件。

*  单步执行代码时。  调用堆栈中的链接将打开原始源文件。


<!-- ====================================================================== -->
## <a name="sourceurl-and-displayname"></a>@sourceURL 和 displayName

尽管这不是 Source Map `@sourceURL` 规范的一部分，但 允许您在使用 evals 时更轻松地进行开发。  帮助程序显示类似于 属性 `//# sourceMappingURL` ，并提及源地图 V3 规范。

通过在你的代码中包括以下特殊注释（已对此进行评论）可以命名评论和内联脚本和样式，以便每个脚本和样式在 DevTools 中显示为更符合逻辑的名称。

```javascript
//# sourceURL=source.coffee
```

1. 打开新 [浏览器窗口](https://www.thecssninja.com/demo/source_mapping/compile.html) 或选项卡中的命名这些浏览演示页面。

1. 打开 DevTools 并转到"源 **"** 工具。

1. 在" **命名代码：** 输入"字段中，输入文件名。

1. 单击" **编译"** 按钮。

   将出现警报，显示来自 CoffeeScript 源的评估和。

1. 展开" **源"** 子面板。  将显示新文件，并包含您之前输入的自定义文件名。

1. 双击该文件以打开它。

   该文件包含原始源的已编译 JavaScript。  但是，最后一行是指示 `// @sourceURL` 原始源文件的注释。  这有助于你在使用语言抽象时进行调试。

:::image type="content" source="../media/javascript-sources-page-coffeeeeeeee.msft.png" alt-text="使用 sourceURL。" lightbox="../media/javascript-sources-page-coffeeeeeeee.msft.png":::


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于此处，[](https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps)由 [Meggin Kearney](https://developers.google.com/web/resources/contributors#meggin-kearney) (Technical Writer) 和 [Paul Bakaus](https://developers.google.com/web/resources/contributors#paul-bakaus) (Open Web Developer Advocate、Google：Tools、Performance、Animation 和 UX) 创作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
