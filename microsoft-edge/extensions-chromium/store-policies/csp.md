---
title: '内容安全策略 (CSP) '
description: Microsoft Edge 扩展的内容安全策略。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
ms.openlocfilehash: 2ec10109da8fe120fd6a64e3ef12cc4c0de972dd
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12630653"
---
# <a name="content-security-policy-csp"></a>内容安全策略 (CSP) 

为了缓解大量潜在的跨站点脚本问题，Microsoft Edge 扩展系统已纳入 [内容安全策略 (CSP) ](https://w3c.github.io/webappsec-csp)的一般概念。  这会引入一些相当严格的策略，使扩展在默认情况下更加安全，并使你能够创建和强制实施规则来管理可由扩展和应用程序加载和运行的内容类型。

一般情况下，CSP 充当扩展加载或运行的资源的块/允许列表机制。  为扩展定义合理的策略可让你仔细考虑扩展所需的资源，并要求浏览器确保这些资源是扩展访问的唯一资源。  这些策略提供扩展请求的主机权限及以上安全性;它们是额外的保护层，而不是替代层。

在 Web 上，此类策略是通过 HTTP 标头或 `meta` 元素定义的。  在 Microsoft Edge 扩展系统中，两者都不是适当的机制。  而是使用扩展文件定义扩展策略， `manifest.json` 如下所示：

```javascript
{
    ...,
    "content_security_policy": "[POLICY STRING GOES HERE]"
    ...
}
```

> 有关 CSP 语法的完整详细信息，请参阅 W3C [内容安全策略规范](https://w3c.github.io/webappsec-csp)和 _HTML5Rocks_ [内容安全策略简介](https://www.html5rocks.com/en/tutorials/security/content-security-policy)。


<!-- ====================================================================== -->
## <a name="default-policy-restrictions"></a>默认策略限制

未定义 `manifest_version` 不具有默认内容安全策略的包。  使用 `manifest_version` 2 的包具有以下默认内容安全策略：

```javascript
script-src 'self'; object-src 'self'
```

该策略通过三种方式限制扩展和应用程序来增加安全性：

**已禁用 Eval 和相关函数**

如下所示的代码不起作用：

```javascript
alert(eval("foo.bar.baz"));
window.setTimeout("alert('hi')", 10);
window.setInterval("alert('hi')", 10);
new Function("return foo.bar.baz");
```

像这样评估 JavaScript 的字符串是常见的 XSS 攻击向量。  相反，应编写如下所示的代码：

```javascript
alert(foo && foo.bar && foo.bar.baz);
window.setTimeout(function() { alert('hi'); }, 10);
window.setInterval(function() { alert('hi'); }, 10);
function() { return foo && foo.bar && foo.bar.baz };
```

**内联 JavaScript 未运行**

内联 JavaScript 不会运行。  此限制禁止内联 `<script>` 块和内联事件处理程序，例如 `<button onclick="...">`。

第一个限制通过使你无法意外运行恶意第三方提供的脚本来消除大量跨站点脚本攻击。  但是，它确实要求你编写代码，并在内容和行为之间进行干净的分离。  一个示例可以更清楚地说明这一点。  可以尝试将浏览器操作弹出窗口写入为包含以下内容的单 `pop-up.html` 个弹出窗口：

```html
<!doctype html>
<html>
    <head>
        <title>My Awesome Pop-up!</title>
        <script>
            function awesome() {
                // do something awesome!
            }

            function totallyAwesome() {
                // do something TOTALLY awesome!
            }

            function clickHandler(element) {
                setTimeout("awesome(); totallyAwesome()", 1000);
            }

            function main() {
                // Initialization work goes here.
            }
        </script>
    </head>
    <body onload="main();">
        <button onclick="clickHandler(this)">
            Click for awesomeness!
        </button>
    </body>
</html>
```

但是，必须更改三个事项才能使此工作按预期方式进行：

*  定义 `clickHandler` 必须移到外部 JavaScript 文件中， (`popup.js` 可能是一个很好的目标) 。

*  内联事件处理程序定义必须按以下条件 `addEventListener` 重写并提取到 `popup.js`中。  如果当前使用类似 `<body onload="main();">`代码的代码启动程序，请考虑通过挂钩到 `DOMContentLoaded` 文档事件或 `load` 窗口事件来替换它，具体取决于你的要求。  使用前者，因为它通常触发速度更快。

*  `setTimeout`必须重写调用以避免将字符串`"awesome(); totallyAwesome()"`转换为 JavaScript 以运行。

这些更改可能如下所示：

```javascript
function awesome() {
    // Do something awesome!
}

function totallyAwesome() {
    // do something TOTALLY awesome!
}

function awesomeTask() {
    awesome();
    totallyAwesome();
}

function clickHandler(e) {
    setTimeout(awesomeTask, 1000);
}

function main() {
    // Initialization work goes here.
}

// Add event listeners once the DOM has fully loaded by listening for the
// `DOMContentLoaded` event on the document, and adding your listeners to
// specific elements when it triggers.
document.addEventListener('DOMContentLoaded', function () {
    document.querySelector('button').addEventListener('click', clickHandler);
    main();
});
```

```html
<!doctype html>
<html>
    <head>
        <title>My Awesome Pop-up!</title>
        <script src="popup.js"></script>
    </head>
    <body>
        <button>Click for awesomeness!</button>
    </body>
</html>
```

**仅加载本地脚本和对象资源**

脚本和对象资源只能从扩展包加载，而不能从整个 Web 加载。  这可确保扩展仅运行你特别批准的代码，防止活动网络攻击者恶意重定向对资源的请求。

请考虑在扩展包中包括特定版本的 jQuery，而不是编写依赖于 jQuery (或任何其他库) 从外部 CDN 加载的代码。  也就是说，而不是：

```html
<!doctype html>
<html>
    <head>
        <title>My Awesome Pop-up!</title>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
    </head>
    <body>
        <button>Click for awesomeness!</button>
    </body>
</html>
```

请改用以下方法。  下载文件，将其包含在包中，然后写入：

```html
<!doctype html>
<html>
    <head>
        <title>My Awesome Pop-up!</title>
        <script src="jquery.min.js"></script>
    </head>
    <body>
        <button>Click for awesomeness!</button>
    </body>
</html>
```


<!-- ====================================================================== -->
## <a name="relaxing-the-default-policy"></a>放宽默认策略

**内联脚本**

<!-- Up until Chrome 45, there was no mechanism for relaxing the restriction against running inline JavaScript.  In particular, setting a script policy that includes `'unsafe-inline'` has no effect.

As of Chrome 46, -->

可以通过在策略中指定源代码的 base64 编码哈希来允许内联脚本。  此哈希必须以 (sha256、sha384 或 sha512) 使用的哈希算法为前缀。  有关示例，请参阅 [W3C >元素的 \<script\> 哈希使用情况](https://www.w3.org/TR/CSP2#script-src-hash-usage)。

**远程脚本**

如果需要一些外部 JavaScript 或对象资源，可以通过允许列出应从中接受脚本的安全源来在有限程度上放宽策略。  验证加载了扩展权限提升的运行时资源是否正是你期望的资源，并且不会被活动网络攻击者取代。  由于中间 [人攻击](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) 在 HTTP 上既简单又不可检测，因此不接受这些来源。

目前，你可以允许列表来源具有以下方案： `blob`， ， `filesystem`， `https`和 `extension`.  源的主机部分必须显式指定为 `https` 和 `extension` 方案。  一般通配符（如 https： `https://*` ）是 `https://*.com` 不允许的;子域通配符（如 `https://*.example.com` 允许）。  [公共后缀列表](https://publicsuffix.org/list)中的域也被视为泛型顶级域。  若要从这些域加载资源，必须显式列出子域。  例如，无效，`https://*.cloudfront.net`但`https://XXXX.cloudfront.net``https://*.XXXX.cloudfront.net`可能有效`allowlisted`。

为方便开发，可以通过 `allowlisted`HTTP 从本地计算机上的服务器加载的资源。  可以在任一 `http://127.0.0.1` 或 `http://localhost`的任意端口上允许列表脚本和对象源。

> [!NOTE]
> 对通过 HTTP 加载的资源的限制仅适用于直接运行的资源。  例如，你仍可以自由地与任何喜欢的源建立 `XMLHTTPRequest` 连接;默认策略不会以任何方式限制 `connect-src` 或任何其他 CSP 指令。

允许通过 `example.com` HTTPS 加载脚本资源的宽松策略定义可能如下所示：

```javascript
"content_security_policy": "script-src 'self' https://example.com; object-src 'self'"
```

> [!NOTE]
> 同时 `script-src` 由 `object-src` 策略定义。  Microsoft Edge 不接受不将每个值限制为 (至少) “的策略`self`。

<!-- Making use of Google Analytics is the canonical example for this sort of policy definition.  It is common enough that an Analytics boilerplate of sorts is provided in the Event Tracking with Google Analytics sample Extension, and a brief tutorial that goes into more detail.  -->

**评估的 JavaScript**

策略与`eval()`相关函数（例如）一样`setTimeout(String)`，`setInterval(String)``new Function(String)`可以通过添加`unsafe-eval`到策略来放宽：

```javascript
"content_security_policy": "script-src 'self' 'unsafe-eval'; object-src 'self'"
```

但是，应避免放宽策略。  这些类型的函数是臭名昭著的 XSS 攻击向量。


<!-- ====================================================================== -->
## <a name="tightening-the-default-policy"></a>收紧默认策略

你可以在扩展允许的任何程度上收紧此策略，以提高安全性，而牺牲了方便。  若要指定扩展只能加载任何类型的资源 (映像，等等，) 关联的扩展包，例如，可能适合的 `default-src 'self'` 策略。

<!-- The Mappy sample Extension is a good example of an Extension that is been locked down above and beyond the defaults.  -->


<!-- ====================================================================== -->
## <a name="content-scripts"></a>内容脚本

正在讨论的策略适用于扩展的后台页和事件页。  内容脚本如何应用于扩展的内容脚本更为复杂。

内容脚本通常不受扩展的 CSP 约束。  由于内容脚本不是 HTML，因此主要影响是它们可以使用 `eval` ，即使扩展的 CSP 未指定 `unsafe-eval`，尽管不建议这样做。  此外，页面的 CSP 不适用于内容脚本。  更复杂的是 `<script>` 内容脚本创建并放入其正在运行的页面的 DOM 中的标记。  这些脚本被引用为未来 DOM 注入的脚本。

DOM 注入了在注入页面时立即运行的脚本，如预期的那样运行。  将包含以下代码的内容脚本想象成一个简单的示例：

```javascript
document.write("<script>alert(1);</script>");
 ```

此内容脚本会导致 `alert` 立即出现 `document.write()`。  请注意，无论页面指定的策略如何，此操作都将运行。  但是，在该 DOM 注入的脚本中，对于在注入时不会立即运行的任何脚本，行为变得更加复杂。

假设扩展在提供指定的关联 CSP `script-src 'self'`的页面上运行。  现在假设内容脚本运行以下代码：

```javascript
document.write("<button onclick='alert(1);'>click me</button>'");
```

如果用户单击该按钮， `onclick` 则脚本不会运行。  这是因为脚本没有立即运行，并且在事件发生之前 `click` 未解释的代码不被视为内容脚本的一部分，因此页面的 CSP (不属于扩展) 限制行为。  由于该 CSP 未指定 `unsafe-inline`，因此内联事件处理程序会被阻止。

在本例中实现所需行为的正确方法是从内容脚本中将处理程序添加 `onclick` 为函数，如下所示：

```javascript
document.write("<button id='mybutton'>click me</button>'");
var button = document.getElementById('mybutton');
button.onclick = function() {
      alert(1);
};
```

如果内容脚本运行以下命令，则会出现另一个类似问题：

```javascript
var script = document.createElement('script');
script.innerHTML = 'alert(1);'
document.getElementById('body').appendChild(script);
```

在这种情况下，脚本将运行，并显示警报。  但是，请考虑以下情况：

```javascript
var script = document.createElement('script');
script.innerHTML = 'eval("alert(1);")';
=document.getElementById('body').appendChild(script);
```

当初始脚本运行时，调用 `eval` 会被阻止。  也就是说，虽然允许初始脚本运行时，但脚本中的行为由页面的 CSP 进行控制。  因此，根据在扩展中编写 DOM 注入脚本的方式，对页面 CSP 的更改可能会影响扩展的行为。

由于内容脚本不受页面 CSP 的影响，因此这是将尽可能多的扩展行为放入内容脚本而不是 DOM 注入脚本的绝佳理由。


> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/extensions/contentSecurityPolicy)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
