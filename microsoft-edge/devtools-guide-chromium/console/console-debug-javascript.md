---
title: 修复控制台中报告的 JavaScript 错误
description: 调试和解决控制台中报告的与 JavaScript 相关的错误。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 04/13/2021
ms.openlocfilehash: 42e3f9ff694039f3850ea26b416ebd2783641240
ms.sourcegitcommit: fd3b79a0570cfefc2a40107b223569210cb2c2d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2021
ms.locfileid: "12269107"
---
# <a name="fixing-javascript-errors-that-are-reported-in-the-console"></a>修复控制台中报告的 JavaScript 错误

本文介绍解决控制台中报告的 JavaScript 错误。  有关用于 **显示和解决** 错误消息的控制台的常规用途，请参阅 [控制台概述](index.md)。


<!-- ====================================================================== -->
## <a name="fix-javascript-errors"></a>修复 JavaScript 错误

使用控制台的第一 **个体验** 可能是脚本中的错误。  若要试用，请参阅控制台工具 [中报告的 JavaScript 错误](https://microsoftedge.github.io/DevToolsSamples/console/error.html)。

在浏览器中打开 DevTools。  右 **上方的"打开** 控制台查看错误"按钮将显示有关网页的错误。  选择按钮以将你带至 **控制台** ，并提供有关错误的详细信息：

:::image type="content" source="../media/console-debug-displays-error.msft.png" alt-text="DevTools 提供有关控制台中错误的详细信息。" lightbox="../media/console-debug-displays-error.msft.png":::

控制台中的许多错误消息**在****"Web"** 按钮上都有"搜索此消息"，显示为放大镜。  此功能是在版本 94 Microsoft Edge引入的。  有关详细信息，请参阅从控制台查找 [Web 上的错误消息](index.md#look-up-error-messages-on-the-web-from-the-console)。

此错误消息中的信息表明错误位于文件的第 16 `error.html` 行。  在 `error.html:16` 控制台 中选择错误消息右侧 **的链接**。  " **源** "工具将打开并突出显示代码行，并出现错误：

:::image type="content" source="../media/console-debug-displays-in-sources.msft.png" alt-text="&quot;源&quot;工具突出显示导致错误的代码行。" lightbox="../media/console-debug-displays-in-sources.msft.png":::

该脚本尝试获取文档中的第 `h2` 一个元素，并围绕该元素绘制红色边框。  但不存在 `h2` 元素，因此脚本失败。


<!-- ====================================================================== -->
## <a name="find-and-debug-network-issues"></a>查找和调试网络问题

控制台报告 **的其他错误** 是网络错误。  若要在操作中显示它，请参阅控制台 [中报告的网络错误](https://microsoftedge.github.io/DevToolsSamples/console/network-error.html)。

:::image type="content" source="../media/console-debug-network-error.msft.png" alt-text="控制台显示网络和 JavaScript 错误。" lightbox="../media/console-debug-network-error.msft.png":::

该表显示 `loading` ，但网页上没有任何更改，因为永远不会检索数据。  在 **控制台中**，发生了以下两个错误：

*   以 HTTP 方法开头，后 `GET` 跟 URI 的网络错误。
*   错误 `Uncaught (in promise) TypeError: data.forEach is not a function` 。

选择指向发生错误的网页和代码行的链接，以打开"源"工具。  在此示例中，选择 `network-error.html:40` 控制台中 **的链接**：

:::image type="content" source="../media/console-debug-network-error-code-line.msft.png" alt-text="选择指向发生错误的网页和代码行的链接，以打开&quot;源&quot;工具。" lightbox="../media/console-debug-network-error-code-line.msft.png":::

将 **打开"** 源"工具。  有问题的代码行突出显示，后跟一个 `error` () `x` 按钮。  若要显示 `Failed to load resource: the server responded with a status of 404 ()` 错误消息，请选择 () **** `x` 按钮。

:::image type="content" source="../media/console-debug-network-error-sources.msft.png" alt-text="若要在 JavaScript 中查找错误，请使用&quot;源&quot;工具。" lightbox="../media/console-debug-network-error-sources.msft.png":::

在示例中，错误会通知您找不到请求的 URL。  接下来，打开 **"网络"** 工具，如下所示：

1.  打开“**控制台**”。
1.  选择与错误关联的 URI。

在未加载资源后，控制台将显示错误的 HTTP 状态代码：

:::image type="content" source="../media/console-debug-network-error-url.msft.png" alt-text="在资源未加载后，控制台将显示错误的 HTTP 状态代码。" lightbox="../media/console-debug-network-error-url.msft.png":::

**网络工具**显示有关失败请求详细信息：

:::image type="content" source="../media/console-debug-network-error-network.msft.png" alt-text="&quot;网络&quot;工具显示有关失败请求详细信息。" lightbox="../media/console-debug-network-error-network.msft.png":::

检查"网络 **"工具中的** 标头可能会提供进一步见解：

:::image type="content" source="../media/console-debug-network-error-network-detail.msft.png" alt-text="检查&quot;网络&quot;工具中的标头可能会提供更多信息。" lightbox="../media/console-debug-network-error-network-detail.msft.png":::

问题是什么？  在请求的 `//` URI () 两个斜杠字符 `repos` 。  打开" **源"** 工具并检查第 26 行。  尾部斜杠 () URI 的末尾 `/` 出现。

" **源** "工具显示包含错误的代码行：

:::image type="content" source="../media/console-debug-network-error-code-error.msft.png" alt-text="&quot;源&quot;工具显示包含错误的代码行。" lightbox="../media/console-debug-network-error-code-error.msft.png":::

To see the resulting page when there are no errors in the **Console，** see [Fixed network error reported in Console](https://microsoftedge.github.io/DevToolsSamples/console/network-error-fixed.html).

没有任何错误的示例将加载来自GitHub并显示该信息：

:::image type="content" source="../media/console-debug-network-error-fixed.msft.png" alt-text="没有任何错误的示例将加载来自GitHub并显示该信息。" lightbox="../media/console-debug-network-error-fixed.msft.png":::

使用防御性编码技术以避免以前的用户体验。  请确保代码捕获错误，并显示控制台中的每个 **错误**。  请参阅 [控制台和 UI 中的网络错误报告](https://microsoftedge.github.io/DevToolsSamples/console/network-error-reported.html) 并查看以下项。

*   向用户提供 UI 以指示出现问题。
*   在 **控制台中**，从代码提供有关 **网络** 错误的有用信息。

捕获和报告错误的示例：

:::image type="content" source="../media/console-debug-network-error-report.msft.png" alt-text="捕获和报告错误的示例。" lightbox="../media/console-debug-network-error-report.msft.png":::

以下代码段使用 方法捕获和报告错误 `handleErrors` ，特别是 `throw Error` 行：

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

除了 `throw Error` 上一部分中的示例之外，您还可以在控制台中创建不同的错误和跟踪 **问题**。
若要在控制台中显示两个创建的 **错误消息**，请参阅 [在控制台中创建错误报告和断言](https://microsoftedge.github.io/DevToolsSamples/console/error-assert.html)。

从控制台创建的 **错误消息**：

:::image type="content" source="../media/console-debug-error-assert.msft.png" alt-text="从控制台创建的错误消息。" lightbox="../media/console-debug-error-assert.msft.png":::

在上一示例中使用了以下代码段。

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

您具有三个连续相互请求的函数：

*   `first()`
*   `second()`
*   `third()`

每个函数向另 `name` 一个函数发送一个参数。  在 函数中，检查参数是否存在，如果没有，则记录一 `third()` `name` 个未定义该名称的错误。  如果 `name` 已定义 ，则 `assert()` 使用 方法检查参数是否少于 `name` 8 个字母长。  使用下列 `first()` 参数请求函数三次。

*   没有在函数 `console.error()` 中触发方法 `third()` 的参数。
*   作为函数参数的术语不会导致错误，因为 `Console` `first()` `name` 参数存在且小于八个字母。
*   用作 `Microsoft Edge Canary` 函数参数的短语 `first()` 会导致方法报告错误， `console.assert()` 因为参数长于 8 个字母。

使用 `console.assert()` 方法创建条件错误报告。  以下两个示例具有相同的结果，但其中一个示例需要一个额外的 `if{}` 语句。

```javascript
let x = 20;
if (x < 40) { console.error(`${x} is too small`) };
console.assert(x >= 40, `${x} is too small`)
```

> [!IMPORTANT]
> 代码的第二行和第三行执行相同的测试。  由于断言需要记录负结果，因此在案例和 `x < 40` `if` `x >= 40` 断言中进行测试。

如果不确定哪个函数请求另一个函数，请使用 方法跟踪请求获取当前函数 `console.trace()` 的函数。  若要在控制台中显示 **跟踪，** 请参阅 [在控制台中创建跟踪](https://microsoftedge.github.io/DevToolsSamples/console/trace.html)。

```javascript
function here() {there()}
function there() {everywhere()}
function everywhere() {
    console.trace();
}
here();
there();
```

结果是一个要显示的名称为 、然后为 的跟踪，并且第二个示例中显示其 `here()` `there()` 名为 `everywhere()` `everywhere()` 。

从控制台创建的 **跟踪**：

:::image type="content" source="../media/console-debug-trace.msft.png" alt-text="从控制台创建的跟踪。" lightbox="../media/console-debug-trace.msft.png":::
