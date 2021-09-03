---
description: 调试和解决控制台中报告的与 JavaScript 相关的错误。
title: 修复控制台中报告的 JavaScript 错误
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/13/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 351c93f86cad16f2bcc0cae56939fce1535850af
ms.sourcegitcommit: 22acb7a57d9d8e21e4348aa699c1a2c53618e93d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2021
ms.locfileid: "11936675"
---
# <a name="fixing-javascript-errors-that-are-reported-in-the-console"></a>修复控制台中报告的 JavaScript 错误

本文介绍解决控制台中报告的 JavaScript 错误。  有关用于**显示和解析**错误消息的控制台的常规用途，请导航到"[使用控制台"。](index.md)


## <a name="fix-javascript-errors"></a>修复 JavaScript 错误

使用控制台的第一 **个体验** 可能是脚本中的错误。  若要试用它，请导航到控制台工具 [中报告的 JavaScript 错误][GithubMicrosoftedgeDevtoolssamplesConsoleErrorHtml]。  

在浏览器中打开 DevTools。  右 **上方的"打开** 控制台查看错误"按钮将显示有关网页的错误。  选择按钮以将你导航到 **控制台** ，并提供有关错误的详细信息。

:::image type="complex" source="../media/console-debug-displays-error.msft.png" alt-text="DevTools 提供有关控制台中错误的详细信息" lightbox="../media/console-debug-displays-error.msft.png":::
   DevTools 提供有关控制台中错误 **的详细信息**  
:::image-end:::  

该信息表明错误位于文件的第 16 `error.html` 行。  选择 `error.html:16` 控制台 右侧 **的链接**。  " **源** "工具将打开并突出显示包含错误的代码行。  

:::image type="complex" source="../media/console-debug-displays-in-sources.msft.png" alt-text="源工具突出显示导致错误的代码行" lightbox="../media/console-debug-displays-in-sources.msft.png":::
   源 **工具** 突出显示导致错误的代码行  
:::image-end:::  

该脚本尝试获取文档中的第 `h2` 一个元素，并围绕该元素绘制红色边框。  但不存在 `h2` 元素，因此脚本失败。  


## <a name="find-and-debug-network-issues"></a>查找和调试网络问题  

控制台报告 **的其他错误** 是网络错误。  若要在操作中显示它，请导航到控制台 [中报告的网络错误][GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorHtml]。  

:::image type="complex" source="../media/console-debug-network-error.msft.png" alt-text="控制台显示网络和 JavaScript 错误" lightbox="../media/console-debug-network-error.msft.png":::
   **控制台** 显示网络和 JavaScript 错误  
:::image-end:::  

该表显示 `loading` ，但网页上没有任何变化，因为从不检索数据。  在控制台 **中**，发生了以下两个错误。  

*   以 HTTP 方法开头，后 `GET` 跟 URI 的网络错误。  
*   错误 `Uncaught (in promise) TypeError: data.forEach is not a function` 。  
    
选择 `network-error.html:40` 控制台 中 **的链接**。  将 **打开"** 源"工具。  有问题的代码行突出显示，后跟 `error` \(`x` \) 按钮。  若要显示 `Failed to load resource: the server responded with a status of 404 ()` 错误消息，请选择错误 \(**** `x` \) 按钮。  

:::row:::
   :::column span="":::
      :::image type="complex" source="../media/console-debug-network-error-code-line.msft.png" alt-text="选择指向发生错误的网页和代码行的链接，以打开"源"工具" lightbox="../media/console-debug-network-error-code-line.msft.png":::
         选择指向发生错误的网页和代码行的链接，以打开 **"源"** 工具 :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../media/console-debug-network-error-sources.msft.png" alt-text="若要在 JavaScript 中查找错误，请使用源工具" lightbox="../media/console-debug-network-error-sources.msft.png":::
         若要在 JavaScript 中查找错误，请使用 **"源"** 工具  
      :::image-end:::  
   :::column-end:::
:::row-end:::

在示例中，错误会通知您找不到请求的 URL。  接下来，打开 **"网络"** 工具，如下所示。

1.  打开“**控制台**”。  
1.  选择与错误关联的 URI。  
    
:::image type="complex" source="../media/console-debug-network-error-url.msft.png" alt-text="控制台在资源未加载后显示错误的 HTTP 状态代码" lightbox="../media/console-debug-network-error-url.msft.png":::
   **控制台** 在资源未加载后显示错误的 HTTP 状态代码  
:::image-end:::  

:::row:::
    :::column:::
        :::image type="complex" source="../media/console-debug-network-error-network.msft.png" alt-text="网络工具显示有关失败请求详细信息" lightbox="../media/console-debug-network-error-network.msft.png":::
           **"网络**"工具显示有关失败请求详细信息  
        :::image-end:::  
    :::column-end:::
    :::column:::
        :::image type="complex" source="../media/console-debug-network-error-network-detail.msft.png" alt-text="检查网络工具中的标头可能会提供更多信息" lightbox="../media/console-debug-network-error-network-detail.msft.png":::
           检查网络 **工具中的标头** 可能会提供更多信息 :::image-end:::  
    :::column-end:::
:::row-end:::  

问题是什么？  两个斜杠字符 `//` \(\) 出现在请求的 URI 中的单词 `repos` 后。  打开" **源"** 工具并检查第 26 行。  尾部斜杠字符 \(\) 出现在基本 `/` URI 的末尾。  

:::image type="complex" source="../media/console-debug-network-error-code-error.msft.png" alt-text="源工具显示包含错误的代码行" lightbox="../media/console-debug-network-error-code-error.msft.png":::
   " **源** "工具显示包含错误的代码行  
:::image-end:::  

To see the resulting page when there are no errors in the **Console**， navigate to [Fixed network error reported in Console][GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorFixedHtml].  

:::image type="complex" source="../media/console-debug-network-error-fixed.msft.png" alt-text="没有任何错误的示例将加载来自GitHub并显示该信息" lightbox="../media/console-debug-network-error-fixed.msft.png":::
   没有任何错误的示例将加载来自GitHub并显示该信息  
:::image-end:::  

使用防御性编码技术以避免以前的用户体验。  请确保代码捕获错误，并显示控制台中的每个 **错误**。  在控制台 [和 UI 中导航到][GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorReportedHtml] 网络错误报告并查看以下项目。

*   向用户提供 UI 以指示出现问题。  
*   在 **控制台中**，从代码提供有关 **网络** 错误的有用信息。
    
:::image type="complex" source="../media/console-debug-network-error-report.msft.png" alt-text="捕获和报告错误的示例" lightbox="../media/console-debug-network-error-report.msft.png":::
   捕获和报告错误的示例  
:::image-end:::  

以下代码段使用 方法捕获和报告错误 `handleErrors` ，特别是 行 `throw Error` 。  

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

## <a name="create-errors-and-traces-in-the-console"></a>在控制台创建错误和跟踪

除了 `throw Error` 上一部分中的示例之外，您还可以在控制台中创建不同的错误和跟踪 **问题**。  
若要在控制台中显示两个创建的 **错误消息**，请导航到在控制台中创建错误报告和 [断言][GithubMicrosoftedgeDevtoolssamplesConsoleErrorAssertHtml]。  

:::image type="complex" source="../media/console-debug-error-assert.msft.png" alt-text="从控制台创建的错误消息" lightbox="../media/console-debug-error-assert.msft.png":::
   从控制台创建的 **错误消息**  
:::image-end:::  

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

您具有三个连续相互请求的函数。  

*   `first()`  
*   `second()`  
*   `third()`  
    
每个参数 `name` 向另一个参数发送。  在 函数中，检查参数是否存在，如果没有，则记录一 `third()` `name` 个未定义该名称的错误。  如果 `name` 已定义 ，则 `assert()` 使用 方法检查参数是否少于 `name` 8 个字母长。  使用下列 `first()` 参数请求函数三次。  

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

如果不确定哪个函数请求另一个函数，请使用 方法跟踪请求获取当前函数 `console.trace()` 的函数。  若要在控制台中显示 **跟踪，** 请导航到在控制台 [中创建跟踪][GithubMicrosoftedgeDevtoolssamplesConsoleTraceHtml]。  

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

:::image type="complex" source="../media/console-debug-trace.msft.png" alt-text="从控制台创建的跟踪" lightbox="../media/console-debug-trace.msft.png":::
   从控制台创建的 **跟踪**  
:::image-end:::  


## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  
[GithubMicrosoftedgeDevtoolssamplesConsoleErrorHtml]: https://microsoftedge.github.io/DevToolsSamples/console/error.html "控制台工具控制台中报告的 JavaScript |GitHub"  
[GithubMicrosoftedgeDevtoolssamplesConsoleErrorAssertHtml]: https://microsoftedge.github.io/DevToolsSamples/console/error-assert.html "在控制台控制台中创建错误报告和|GitHub"  
[GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorHtml]: https://microsoftedge.github.io/DevToolsSamples/console/network-error.html "控制台控制台中报告的网络|GitHub"  
[GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorFixedHtml]: https://microsoftedge.github.io/DevToolsSamples/console/network-error-fixed.html "修复了控制台控制台中报告的网络|GitHub"  
[GithubMicrosoftedgeDevtoolssamplesConsoleNetworkErrorReportedHtml]: https://microsoftedge.github.io/DevToolsSamples/console/network-error-reported.html "控制台和 UI 服务中的网络错误|GitHub"  
[GithubMicrosoftedgeDevtoolssamplesConsoleTraceHtml]: https://microsoftedge.github.io/DevToolsSamples/console/trace.html "在控制台控制台中|GitHub"  
