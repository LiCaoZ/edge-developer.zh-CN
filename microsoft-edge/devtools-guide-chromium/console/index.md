---
title: 控制台概述
description: 控制台工具在开发人员工具Microsoft Edge简介。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
ms.openlocfilehash: 44b463e11b945c23d99a97129126fc557aed929d
ms.sourcegitcommit: 392c0c34ca43bb2b14f93ff4e24b3713ac505013
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2022
ms.locfileid: "12339185"
---
# <a name="console-overview"></a>控制台概述

DevTools 的控制台工具可帮助你完成多项任务：****

*   了解为什么某些内容在当前项目中无法工作， [并跟踪问题](console-debug-javascript.md)。
*   [以日志消息获取有关浏览器中](console-filters.md) Web 项目的信息。
*   [将信息](console-log.md) 记录在脚本中以便进行调试。
*   [尝试 JavaScript 表达式](console-javascript.md) 在 [REPL 环境中](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 活动。
*   使用 JavaScript [与浏览器中](console-dom-interaction.md)的 Web 项目交互。

控制台 **是** 一款很好的配套工具，可用于其他工具。  控制台 **提供了** 一种使用 JavaScript 编写功能、检查和处理当前网页的功能强大的方法。

控制台 **工具** 在上方面板中打开：

:::image type="content" source="../media/console-intro-console-main.msft.png" alt-text="控制台工具在上方面板中打开。" lightbox="../media/console-intro-console-main.msft.png":::

下 **面板** 中"元素"工具的 **控制台** 在它上方打开：

:::image type="content" source="../media/console-intro-console-panel.msft.png" alt-text="下面板中的&quot;控制台&quot;和&quot;元素&quot;工具在它上方打开。" lightbox="../media/console-intro-console-panel.msft.png":::

直接打开**** 控制台的`Control``J``Shift`++最快方法为选择 (Windows、Linux) 或`J` `Command`+`Option`+ (macOS) 。


<!-- ====================================================================== -->
## <a name="error-reports-and-the-console"></a>错误报告和控制台

**控制台是**报告 JavaScript 和连接错误的默认位置。  如果发生任何错误，"**** 问题"计数器将显示在 DevTools 中提供错误和警告**设置**图标旁边。  选择 **"问题"** 计数器以打开 **"问题** "工具并显示问题。  有关详细信息，请参阅修复控制台中 [报告的 JavaScript 错误](console-debug-javascript.md)。

DevTools 提供有关控制台中错误 **的详细信息**：

:::image type="content" source="../media/console-debug-displays-error.msft.png" alt-text="DevTools 提供有关控制台中错误的详细信息。" lightbox="../media/console-debug-displays-error.msft.png":::


<!-- ====================================================================== -->
## <a name="look-up-error-messages-on-the-web-from-the-console"></a>从控制台查找 Web 上的错误消息

从 DevTools **中** ，在 Web 中搜索控制台错误消息。  在 **控制台中**，许多错误消息在 **"Web** "按钮上都有"搜索此消息"，显示为放大镜。  当您选择" **在 Web 上搜索此消息** "按钮时，将在浏览器中打开一个新选项卡，并会显示错误消息的搜索结果。

控制台 **中的错误消息上的"在 Web** 上搜索此消息" **按钮**：

:::image type="content" source="../media/search-console-icon.msft.png" alt-text="**Console** 中的错误消息上的&quot;在 Web 上搜索此消息&quot;按钮。" lightbox="../media/search-console-icon.msft.png":::

对于错误 `Failed to load resource` ，新选项卡包含消息"未能加载资源"的 Web 搜索结果， (引号) 。

从搜索控制台错误 **功能打开的新** 选项卡：

:::image type="content" source="../media/search-console-new-tab.msft.png" alt-text="从搜索控制台错误功能打开的新选项卡。" lightbox="../media/search-console-new-tab.msft.png":::

此功能是在 94 Microsoft Edge引入的。


<!-- ====================================================================== -->
## <a name="inspect-and-filter-information-on-the-current-webpage"></a>检查和筛选当前网页上的信息

当您在网页上打开 DevTools 时，控制台中可能会显示大量 **信息**。  当您需要识别重要信息时，信息量将成为一个问题。  若要查看需要采取措施的重要信息，请使用 DevTools [中的问题](../issues/index.md) 工具。

问题正在逐渐从控制台**移动到****问题工具**。  但是，控制台中仍有很多信息，这就是为什么在控制台中**** 了解自动日志和筛选器**选项是一**个好主意。  有关详细信息，请参阅筛选器 [控制台消息](console-filters.md)。

包含控制台的完整 **消息** 的 DevTools：

:::image type="content" source="../media/console-intro-noise.msft.png" alt-text="包含控制台的 DevTools，包含全部消息。" lightbox="../media/console-intro-noise.msft.png":::


<!-- ====================================================================== -->
## <a name="log-information-to-display-in-the-console"></a>要显示在控制台中的日志信息

控制台最常见的用例****`console.log()`是使用 方法或其他类似方法从脚本中记录信息。  若要试用，请进行以下尝试：

1.  若要打开控制台 **，** 请选择 (Windows `Control`++`Shift``J` 、Linux) 或 (`J` `Command`+`Option`+macOS) 。
1.  请参阅 [控制台消息示例：日志、信息、错误和警告](https://microsoftedge.github.io/Demos/devtools-console/logging-demo.html)，或在控制台中复制并运行以下 **代码**。

    ```javascript
    console.log('This is a log message');
    console.info('This is some information');
    console.error('This is an error');
    console.warn('This is a warning');
    console.log(document.body.getBoundingClientRect());
    console.table(document.body.getBoundingClientRect());
    let technologies = ["HTML", "CSS", "SVG", "ECMAScript"];
    console.groupCollapsed('Technolgies');
    technologies.forEach(tech => {console.info(tech);})
    console.groupEnd('Technolgies');
    ```

1.  **控制台显示**由演示代码导致的结果消息：

    :::image type="content" source="../media/console-intro-logging.msft.png" alt-text="控制台已满由演示代码导致的消息。" lightbox="../media/console-intro-logging.msft.png":::

使用控制台时，可以使用许多有用的 **方法**。  有关详细信息，请参阅在 [控制台工具中记录消息](console-log.md)。


<!-- ====================================================================== -->
## <a name="try-your-javascript-live-in-the-console"></a>在控制台中尝试 JavaScript 实时

**控制台**不仅仅是记录信息的位置。  **控制台是**一个 [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 环境。  在控制台中编写任何 JavaScript **时**，代码会立即运行。  你会发现测试一些新的 JavaScript 功能或执行一些快速计算会很有用。  此外，还可以从新式编辑环境获取所有预期功能，如自动完成、语法突出显示和历史记录。

尝试在控制台中运行 JavaScript：

1.  打开“**控制台**”。
1.  键入 `2 + 2`。

**控制台**会在您键入`2 + 2`实时内容时显示结果，`4`在下面的行中显示结果：

:::image type="content" source="../media/console-javascript-eager-evaluation.msft.png" alt-text="在键入时，控制台将显示 2 + 2 实时的结果。" lightbox="../media/console-javascript-eager-evaluation.msft.png":::

此 **"期待** "评估功能可用于调试和验证代码中没有出错。

若要在控制台中运行 JavaScript 表达式**** 并选择性地显示结果，请选择 `Enter`。  然后，你可以编写下一个 JavaScript 代码以在控制台 **中运行**。

连续运行多行 JavaScript 代码：

:::image type="content" source="../media/console-javascript-several-expressions.msft.png" alt-text="连续运行几行 JavaScript 代码。" lightbox="../media/console-javascript-several-expressions.msft.png":::

默认情况下，在单行中运行 JavaScript 代码。  若要运行一行，请键入 JavaScript，然后选择 `Enter`。  若要绕绕单行限制，请选择 而不是 `Shift``Enter`+`Enter`。

与其他命令行体验类似，若要访问之前的 JavaScript 命令，请选择 `Arrow-Up`。  控制台的自动完成 **功能是了解** 不熟悉的方法的一种很好的方法。

尝试自动完成：

1.  打开“**控制台**”。
1.  键入 `doc`。
1.  从 `document` 下拉菜单中选择。
1.  选择密钥 `tab` 进行选择。
1.  键入 `.bo`。
1.  选择 `tab` 获取 `document.body`。
1.  键入另 `.` 一个，以显示当前网页正文中可用的属性和方法的完整列表。

有关使用控制台的所有方法详细信息，请参阅[作为 JavaScript 环境的控制台](console-javascript.md)。****

控制台中 JavaScript 表达式的自动**完成：**

:::image type="content" source="../media/console-javascript-autocomplete.msft.png" alt-text="JavaScript 表达式的控制台自动完成。" lightbox="../media/console-javascript-autocomplete.msft.png":::


<!-- ====================================================================== -->
## <a name="interact-with-the-current-webpage-in-the-browser"></a>在浏览器中与当前网页交互

**控制台**有权访问浏览器[的 Window](https://developer.mozilla.org/docs/Web/API/Window) 对象。  您可以编写与当前网页交互的脚本。

尝试编写与当前页面交互的脚本：

1.  打开“**控制台**”。
1.  复制并粘贴以下代码：

    ```javascript
    document.querySelector('h1').innerHTML
    ```

复制顶部标题 (`h1`) DOM 中的内容，在控制台中显示表达式计算 **结果**：

:::image type="content" source="../media/console-intro-reading-DOM.msft.png" alt-text="将顶部标题 (h1) DOM 中的内容，在控制台中显示表达式计算结果。" lightbox="../media/console-intro-reading-DOM.msft.png":::

还可以更改页面，而不是仅从网页中读取。  若要尝试更改网页，

1.  打开“**控制台**”。
1.  复制并粘贴以下代码：

    ```javascript
    document.querySelector('h1').innerHTML = 'Rocking the Console';
    ```

在控制台中将文本写入 DOM **：**

:::image type="content" source="../media/console-intro-wrtiting-DOM.msft.png" alt-text="在控制台中将文本写入 DOM。" lightbox="../media/console-intro-wrtiting-DOM.msft.png":::

将网页的主要标题更改为 **"摇动控制台"**。  控制台 **实用程序** 方法使访问和操作当前网页变得容易。  有关详细信息，请参阅控制台 [实用程序 API 参考](utilities.md)。

例如，在当前网页中所有链接周围添加绿色边框：

1.  打开“**控制台**”。
1.  复制并粘贴以下代码：

    ```javascript
    $$('a').forEach(a => a.style.border='1px solid lime');
    ```

使用控制台操作选定 **元素**：

:::image type="content" source="../media/console-intro-changing-styles.msft.png" alt-text="使用控制台操作选定元素。" lightbox="../media/console-intro-changing-styles.msft.png":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用控制台与 DOM 交互](console-dom-interaction.md)。
*  [控制台功能参考](reference.md)
*  [控制台实用工具 API 参考](utilities.md)
*  [控制台 API 参考](api.md)
