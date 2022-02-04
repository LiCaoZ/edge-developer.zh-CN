---
title: 修复控制台中报告的 JavaScript 错误
description: 调试和解决控制台中报告的与 JavaScript 相关的错误。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
---
# <a name="fix-javascript-errors-that-are-reported-in-the-console"></a>修复控制台中报告的 JavaScript 错误

本文将引导你完成六个演示页面，以演示解决控制台中报告的 JavaScript 错误。


<!-- ====================================================================== -->
## <a name="fix-javascript-errors"></a>修复 JavaScript 错误

使用控制台的第一 **个** 体验可能是脚本中的错误。


### <a name="demo-page-javascript-error-reported-in-the-console-tool"></a>演示页面：控制台工具中报告的 JavaScript 错误

1. 打开控制台工具中新窗口或选项卡中报告的演示网页 [JavaScript](https://microsoftedge.github.io/Demos/devtools-console/error.html) 错误。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

   在 DevTools 的右上方，"打开控制台 **查看** 错误"按钮显示有关网页的错误。

1. 单击右 **上方的"打开控制台** "以查看错误按钮。  在 DevTools **中，控制台** 为你提供有关错误的详细信息：

   :::image type="content" source="../media/console-debug-displays-error.msft.png" alt-text="DevTools 提供有关控制台中错误的详细信息。" lightbox="../media/console-debug-displays-error.msft.png":::

   控制台中的许多错误消息**在****"Web**"按钮上都有"搜索此消息"，显示为放大镜。  此功能是在 94 Microsoft Edge引入的。   (有关详细信息，请参阅从 [Console.) ](index.md#look-up-error-messages-on-the-web-from-the-console)

   此错误消息中的信息表明错误位于文件的第 16 `error.html` 行。

1. `error.html:16`单击控制台中错误消息右侧**的链接**。  " **源** "工具将打开并突出显示代码行，并出现错误：

   :::image type="content" source="../media/console-debug-displays-in-sources.msft.png" alt-text="&quot;源&quot;工具突出显示导致错误的代码行。" lightbox="../media/console-debug-displays-in-sources.msft.png":::

   该脚本尝试获取文档中的第 `h2` 一个元素，并围绕该元素绘制红色边框。  但不存在 `h2` 元素，因此脚本失败。


<!-- ====================================================================== -->
## <a name="find-and-debug-network-issues"></a>查找和调试网络问题

控制台 **还会** 报告网络错误。


### <a name="demo-page-network-error-reported-in-console"></a>演示页面：控制台中报告的网络错误

1. 打开演示网页 [新窗口或](https://microsoftedge.github.io/Demos/devtools-console/network-error.html) 选项卡中的控制台中报告的网络错误。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

   :::image type="content" source="../media/console-debug-network-error.msft.png" alt-text="控制台显示网络和 JavaScript 错误。" lightbox="../media/console-debug-network-error.msft.png":::

   该表显示 `loading`，但网页上没有任何更改，因为永远不会检索数据。  在 **控制台中**，发生了以下两个错误：

   *  以 HTTP 方法开头， `GET` 后跟 URI 的网络错误。

   *  错误 `Uncaught (in promise) TypeError: data.forEach is not a function` 。

1. 单击指向发生错误的网页和代码行的链接，以打开"源"工具。  即，单击 `network-error.html:40` 控制台中 **的链接**：

   :::image type="content" source="../media/console-debug-network-error-code-line.msft.png" alt-text="选择指向发生错误的网页和代码行的链接，以打开&quot;源&quot;工具。" lightbox="../media/console-debug-network-error-code-line.msft.png":::

   将 **打开"** 源"工具。  有问题的代码行突出显示，后跟一个 `error` () `x` 按钮。

1. 单击错误 ** (** `x`) 按钮。  `Failed to load resource: the server responded with a status of 404 ()`将显示消息。

   :::image type="content" source="../media/console-debug-network-error-sources.msft.png" alt-text="若要在 JavaScript 中查找错误，请使用&quot;源&quot;工具。" lightbox="../media/console-debug-network-error-sources.msft.png":::

   此错误通知您找不到请求的 URL。

1. 打开 **"网络** "工具，如下所示：打开 **控制台**，然后单击与错误关联的 URI。

   在未加载资源后，控制台将显示错误的 HTTP 状态代码：

   :::image type="content" source="../media/console-debug-network-error-url.msft.png" alt-text="在资源未加载后，控制台将显示错误的 HTTP 状态代码。" lightbox="../media/console-debug-network-error-url.msft.png":::

   **网络工具**显示有关失败请求详细信息：

   :::image type="content" source="../media/console-debug-network-error-network.msft.png" alt-text="&quot;网络&quot;工具显示有关失败请求详细信息。" lightbox="../media/console-debug-network-error-network.msft.png":::

1. 检查"网络"工具 **中的** 标头，获取更多信息：

   :::image type="content" source="../media/console-debug-network-error-network-detail.msft.png" alt-text="检查&quot;网络&quot;工具中的标头可能会提供更多信息。" lightbox="../media/console-debug-network-error-network-detail.msft.png":::

   问题是什么？  在请求的 `//` URI `repos` () 两个斜杠字符。

1. 打开" **源"** 工具并检查第 26 行。  尾部斜杠 (`/`) URI 的末尾出现。  " **源** "工具显示包含错误的代码行：

   :::image type="content" source="../media/console-debug-network-error-code-error.msft.png" alt-text="&quot;源&quot;工具显示包含错误的代码行。" lightbox="../media/console-debug-network-error-code-error.msft.png":::


### <a name="viewing-the-resulting-page-when-there-are-no-errors-in-the-console"></a>在控制台中没有任何错误时查看生成的页面

接下来，当控制台中没有任何错误时，我们将查看生成的 **页面**。


#### <a name="demo-page-fixed-network-error-reported-in-console"></a>演示页面：修复了控制台中报告的网络错误

1. 打开演示网页 [修复了控制台中新](https://microsoftedge.github.io/Demos/devtools-console/network-error-fixed.html) 窗口或选项卡中报告的网络错误。

   没有任何错误的示例将加载来自GitHub并显示该信息：

   :::image type="content" source="../media/console-debug-network-error-fixed.msft.png" alt-text="没有任何错误的示例将加载来自GitHub并显示该信息。" lightbox="../media/console-debug-network-error-fixed.msft.png":::


#### <a name="demo-page-network-error-reporting-in-console-and-ui"></a>演示页面：控制台和 UI 中的网络错误报告

使用防御性编码技术以避免以前的用户体验。  确保代码捕获错误，并显示控制台中的每个 **错误，如下所示**：

1. 在控制台中打开演示 [网页网络错误报告，在](https://microsoftedge.github.io/Demos/devtools-console/network-error-reported.html) 一个新窗口或选项卡中打开 UI。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

   示例网页演示了这些做法：

   *  向用户提供 UI 以指示出现问题。

   *  在 **控制台中**，从代码提供有关 **网络** 错误的有用信息。

   该示例捕获和报告错误：

   :::image type="content" source="../media/console-debug-network-error-report.msft.png" alt-text="捕获和报告错误的示例。" lightbox="../media/console-debug-network-error-report.msft.png":::

   演示中的以下代码使用 方法 `handleErrors` 捕获和报告错误，特别是 行 `throw Error` ：

   ```javascript
   const handleErrors = (response) => {
      if (!response.ok) {
         let message = 'Could not load the information'
         document.querySelector('tbody').innerHTML = `
         <tr><td colspan=3>Error ${message}</td></tr>
         `;
         throw Error(response.status + ' ' + response.statusText);
      }
      return response;
   };
   ```
   

<!-- ====================================================================== -->
## <a name="create-errors-and-traces-in-the-console"></a>在控制台创建错误和跟踪

除了上 `throw Error` 一部分中的示例，您还可以在控制台中创建不同的错误和跟踪 **问题**。


### <a name="demo-page-creating-error-reports-and-assertions-in-console"></a>演示页：在控制台中创建错误报告和断言

若要在控制台中显示两个创建的 **错误消息**：

1. 打开演示页面 [在](https://microsoftedge.github.io/Demos/devtools-console/error-assert.html) 控制台中的新建窗口或选项卡创建错误报告和断言。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

   控制台中出现 **错误消息**：

   :::image type="content" source="../media/console-debug-error-assert.msft.png" alt-text="控制台中出现错误消息。" lightbox="../media/console-debug-error-assert.msft.png":::

   演示页面使用下面的代码：

    ```javascript
    function first(name) { second(name); }
    function second(name) { third(name); }
    function third(name) {
        if (!name) {
            console.error(`Name isn't defined :(`)
        } else {
            console.assert(
                name.length <= 8,
                `"${name} is not less than eight letters"`
            );
        }
    }
    first();
    first('Console');
    first('Microsoft Edge Canary');
    ```
    
   有三个函数会连续相互请求：

   *  `first()`
   *  `second()`
   *  `third()`

   每个函数向另一 `name` 个函数发送一个参数。  `third()`在 函数中，`name`检查参数是否存在，如果没有，则记录一个未定义该名称的错误。  如果 `name` 已定义 ，则 `assert()` 使用 方法检查参数 `name` 是否少于 8 个字母长。

   使用下列 `first()` 参数请求函数三次：

    *  没有在函数中 `console.error()` 触发方法 `third()` 的参数。

    *  `Console`作为函数参数的`first()``name`术语不会导致错误，因为参数存在且小于八个字母。

    *  用作函数 `Microsoft Edge Canary` 参数的 `first()` 短语会导致 `console.assert()` 方法报告错误，因为参数长于 8 个字母。

   演示使用<!--todo: confirm--> 创建 `console.assert()` 条件错误报告的方法。  以下两个示例具有相同的结果，但其中一个示例需要一个额外的 `if{}` 语句：

    ```javascript
    let x = 20;
    if (x < 40) { console.error(`${x} is too small`) };
    console.assert(x >= 40, `${x} is too small`)
    ```

   代码的第二行和第三行执行相同的测试。  由于断言需要记录一个负结果：

   *  在这种情况下进行测试`x < 40``if`。
   *  测试断言 `x >= 40` 。


### <a name="demo-page-creating-traces-in-console"></a>演示页：在控制台中创建跟踪

如果不确定哪个函数请求 `console.trace()` 另一个函数，请使用 方法跟踪请求的函数，以便访问当前函数。

在控制台中显示**跟踪：**

1. 打开演示页面 [在控制台中的](https://microsoftedge.github.io/Demos/devtools-console/trace.html) 新建窗口或选项卡创建跟踪。

1. 右键单击网页中的任意位置，然后选择"检查 **"**。  或者，按 `F12`。  将在网页旁边打开 DevTools。

   页面使用此代码：

   ```javascript
   function here() {there()}
   function there() {everywhere()}
   function everywhere() {
      console.trace();
   }
   here();
   there();
   ```
    
   结果是一个要显示的名称`here()` `there()` `everywhere()`为 、然后为 的跟踪，并且第二个示例中显示其名为 。`everywhere()`

   下面是在控制台中生成的 **跟踪**：

   :::image type="content" source="../media/console-debug-trace.msft.png" alt-text="显示在控制台中的跟踪。" lightbox="../media/console-debug-trace.msft.png":::


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [控制台概述](index.md) - 控制台 **的常规用途** ，用于显示和解决错误消息。
