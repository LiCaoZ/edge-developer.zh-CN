---
title: '内容安全策略 (CSP) '
description: 适用于扩展Microsoft Edge安全策略。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
---

# <a name="content-security-policy-csp"></a>内容安全策略 (CSP) 

为了缓解大量的潜在跨网站脚本问题，Microsoft Edge 扩展系统已纳入内容安全策略和 [CSP (的](https://w3c.github.io/webappsec-csp)一般) 。  这引入了一些相当严格的策略，这些策略使扩展在默认情况下更加安全，并让你能够创建和实施规则，以管理扩展和应用程序可以加载和运行的内容类型。

通常，CSP 用作扩展加载或运行的资源的阻止/允许列表机制。  通过为扩展定义合理的策略，你可以仔细考虑扩展所需的资源，并要求浏览器确保这些是你的扩展有权访问的唯一资源。  这些策略提供高于扩展请求的主机权限的安全性;它们是一层额外的保护，而不是替代。

在 Web 上，此类策略通过 HTTP 标头或元素 `meta` 定义。  在 Microsoft Edge 扩展系统中，两者都不是适当的机制。  而是使用扩展的文件定义扩展 `manifest.json` 策略，如下所示：

```javascript
{
    ...,
    "content_security_policy": "[POLICY STRING GOES HERE]"
    ...
}
```

> 有关 CSP 语法的完整详细信息，请参阅 W3C [内容](https://w3c.github.io/webappsec-csp)安全策略规范和 _HTML5Rocks_ 的内容安全策略简介。[](https://www.html5rocks.com/en/tutorials/security/content-security-policy)


<!-- ====================================================================== -->
## <a name="default-policy-restrictions"></a>默认策略限制

不定义 的包 `manifest_version` 没有默认内容安全策略。  `manifest_version`使用 2 的程序包具有以下默认内容安全策略：

```javascript
script-src 'self'; object-src 'self'
```

该策略通过以下三种方式限制扩展和应用程序来增加安全性：

**Eval 和相关函数已禁用**

类似下面的代码不起作用：

```javascript
alert(eval("foo.bar.baz"));
window.setTimeout("alert('hi')", 10);
window.setInterval("alert('hi')", 10);
new Function("return foo.bar.baz");
```

像这样评估 JavaScript 字符串是一种常见的 XSS 攻击矢量。  相反，您应编写如下所示的代码：

```javascript
alert(foo && foo.bar && foo.bar.baz);
window.setTimeout(function() { alert('hi'); }, 10);
window.setInterval(function() { alert('hi'); }, 10);
function() { return foo && foo.bar && foo.bar.baz };
```

**内联 JavaScript 不运行**

内联 JavaScript 不运行。  此限制同时禁止内联 `<script>` 块和内联事件处理程序（如 `<button onclick="...">`）。

第一个限制通过使您无法意外运行恶意第三方提供的脚本来擦除大量跨站点脚本攻击。  但是，它确实需要你在内容和行为之间以干净分隔方式编写代码。  例如，可以更清楚地说明这一点。  您可以尝试将浏览器操作弹出窗口编写为包含 `pop-up.html` 以下内容的单一项：

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

但是，必须更改以下三项操作，才能让此操作按预期方式工作：

*  必须将 `clickHandler` 定义移动到外部 JavaScript 文件 `popup.js` (可能是一个很好的目标) 。

*  内联事件处理程序定义必须重写为 ，并 `addEventListener` 提取到 `popup.js`中。  如果当前正在使用`<body onload="main();">``DOMContentLoaded``load`类似 的代码启动程序，请考虑根据你的要求，通过挂钩到文档的事件或窗口的事件来替换它。  使用前者，因为它通常更快速地触发。

*  必须 `setTimeout` 重写调用以避免将字符串 `"awesome(); totallyAwesome()"` 转换为 JavaScript 以运行。

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

脚本和对象资源只能从扩展包加载，而不是从大型 Web 加载。  这将确保你的扩展仅运行你专门批准的代码，防止活动网络攻击者恶意重定向你的资源请求。

请考虑在扩展包中) jQuery 的特定版本，而不是编写依赖于 jQuery (从外部 CDN 加载的其他任何库的代码。  即，而不是：

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

请改为使用以下方法。  下载文件，将文件包括在程序包中，然后编写：

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
## <a name="relaxing-the-default-policy"></a>支持默认策略

**内联脚本**

<!-- Up until Chrome 45, there was no mechanism for relaxing the restriction against running inline JavaScript.  In particular, setting a script policy that includes `'unsafe-inline'` has no effect.

As of Chrome 46, -->

可以通过在策略中指定源代码的 base64 编码哈希来允许内联脚本。  此哈希必须以 sha256、sha384 或 sha512 (使用的哈希算法作为) 。  有关示例，请参阅 [W3C >元素的哈希 \<script\> 用法](https://www.w3.org/TR/CSP2#script-src-hash-usage)。

**远程脚本**

如果需要一些外部 JavaScript 或对象资源，可以通过允许从其中列出应接受脚本的安全源来限制策略。  验证使用扩展的提升权限加载的运行时资源是否正是您期望的资源，并且不会替换为活动网络攻击者。  由于 [中间人攻击](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) 在 HTTP 上是无关紧要且无法检测到的，因此不接受这些来源。

目前，你可以允许具有以下方案列表源：`blob``filesystem`、、和 `https``extension`。  必须为 和 方案显式指定源的主机`https``extension`部分。  不允许使用泛型通配符（如 https： `https://*` `https://*.com` 和 ）;允许使用诸如 这样的 `https://*.example.com` 子域通配符。  公共后缀 [列表中的域](https://publicsuffix.org/list) 也被视为常规顶级域。  若要从这些域加载资源，必须明确列出子域。  例如， `https://*.cloudfront.net` 是 无效，但 `https://XXXX.cloudfront.net` 和 `https://*.XXXX.cloudfront.net` 可以是 `allowlisted`。

为了便于开发，在本地计算机上通过 HTTP 加载的资源可以是 `allowlisted`。  可以在 或 的任何端口上允许列出脚本和对象 `http://127.0.0.1` 源 `http://localhost`。

> [!NOTE]
> 对通过 HTTP 加载的资源的限制仅适用于直接运行的资源。  例如，你`XMLHTTPRequest``connect-src`仍然可以自由地连接到任何喜欢的源;默认策略不会以任何方式限制或其他任何云解决方案提供商指令。

允许通过 HTTPS 加载脚本 `example.com` 资源的宽松策略定义可能如下所示：

```javascript
"content_security_policy": "script-src 'self' https://example.com; object-src 'self'"
```

> [!NOTE]
> `object-src`和 `script-src` 都由策略定义。  Microsoft Edge不接受不将其中每个值限制为至少为"" (一) 的策略`self`。

<!-- Making use of Google Analytics is the canonical example for this sort of policy definition.  It is common enough that an Analytics boilerplate of sorts is provided in the Event Tracking with Google Analytics sample Extension, and a brief tutorial that goes into more detail.  -->

**评估的 JavaScript**

针对 的策略 `eval()` 和相关功能（如 `setTimeout(String)`、 `setInterval(String)`和 `new Function(String)` ）可通过向策略添加来 `unsafe-eval` 轻松：

```javascript
"content_security_policy": "script-src 'self' 'unsafe-eval'; object-src 'self'"
```

但是，应避免使用策略。  这些类型的函数是 XSS 攻击途径。


<!-- ====================================================================== -->
## <a name="tightening-the-default-policy"></a>使用默认策略

你可以将此策略严格到扩展允许的任何程度，以提高安全性，但代价是方便。  若要指定你的扩展只能加载任何类型的资源 (图像，等等) 关联的扩展包，例如，策略 可能 `default-src 'self'` 合适。

<!-- The Mappy sample Extension is a good example of an Extension that is been locked down above and beyond the defaults.  -->


<!-- ====================================================================== -->
## <a name="content-scripts"></a>内容脚本

正在讨论的策略适用于扩展的背景页和事件页面。  内容脚本如何应用于扩展的内容脚本更加复杂。

内容脚本通常不受扩展 CSP 的管理。  由于内容脚本不是 HTML `eval` ，因此主要影响是，即使扩展 CSP `unsafe-eval`未指定 ，它们也可使用，尽管不建议这样做。  此外，页面的 CSP 不适用于内容脚本。  更复杂的是 `<script>` 内容脚本创建并放入其运行的页面的 DOM 中的标记。  这些脚本将作为 DOM 注入脚本进行引用。

注入到页面后立即运行的 DOM 注入脚本将如预期运行。  Imagine代码编写内容脚本作为简单示例：

```javascript
document.write("<script>alert(1);</script>");
 ```

此内容脚本会立即 `alert` 在 上引发 `document.write()`。  请注意，无论页面指定何种策略，这都将运行。  但是，该 DOM 注入脚本内的行为以及任何在注入时不立即运行的脚本的行为都变得更加复杂。

Imagine你的扩展正在提供指定 的关联 CSP 的页面上运行`script-src 'self'`。  现在假设内容脚本运行以下代码：

```javascript
document.write("<button onclick='alert(1);'>click me</button>'");
```

如果用户单击该按钮， `onclick` 脚本不会运行。  这是因为脚本未 `click` 立即运行，且在事件发生之前未解释的代码不会被视为内容脚本的一部分，因此页面 CSP (不是扩展) 限制行为。  由于该 CSP 未指定 ， `unsafe-inline`内联事件处理程序将被阻止。

在这种情况下，实现所需行为 `onclick` 的正确方法就是将处理程序添加为内容脚本中的函数，如下所示：

```javascript
document.write("<button id='mybutton'>click me</button>'");
var button = document.getElementById('mybutton');
button.onclick = function() {
      alert(1);
};
```

如果内容脚本运行以下内容，也会出现另一个类似问题：

```javascript
var script = document.createElement('script');
script.innerHTML = 'alert(1);'
document.getElementById('body').appendChild(script);
```

在这种情况下，脚本将运行，并出现警报。  但是，请考虑这种情况：

```javascript
var script = document.createElement('script');
script.innerHTML = 'eval("alert(1);")';
=document.getElementById('body').appendChild(script);
```

在初始脚本运行时，将阻止 `eval` 对 的调用。  也就是说，虽然允许初始脚本运行时，但脚本内的行为由页面的 CSP 进行控制。  因此，根据在扩展中编写 DOM 注入脚本的方法，对页面 CSP 的更改可能会影响扩展的行为。

由于内容脚本不受页面 CSP 的影响，因此，这是将尽可能多的扩展行为放入内容脚本（而不是 DOM 注入脚本）的一个很好的理由。


> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/extensions/contentSecurityPolicy)。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
