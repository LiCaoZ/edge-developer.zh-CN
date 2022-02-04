---
title: 控制台对象 API 参考
description: 使用控制台 API 将消息写入控制台。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="console-object-api-reference"></a>控制台对象 API 参考
<!-- orig:
# Console API reference
-->

`console`使用对象的方法从 JavaScript 将**消息写入控制台**。

还可以在控制台中输入 **这些方法**。  例如，在 **控制台中**，输入一个 `console` 接受变量的方法：

1. 在 **"源** "工具中的调试器中，在 JavaScript 代码中设置断点。

1. 在调试器中，逐步调试代码。

1. 如果位于有效上下文中， `console` 以便所需变量位于范围内，请在控制台工具中输入 **对象的一** 个方法。  结果将显示在控制台 **中**。

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="assert"></a>assert

当[计算结果](#error)**为 时，** 将错误写入`expression`控制台`false`。

```javascript
console.assert(expression, object)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Error`

### <a name="example"></a>示例

```javascript
const x = 5;
const y = 3;
const reason = 'x is expected to be less than y';
console.assert(x < y, {x, y, reason});
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-assert-button.msft.png" alt-text="console.assert () 示例的结果" lightbox="../media/console-demo-assert-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="clear"></a>clear

清除 **控制台**。

如果 [打开](reference.md#filter-by-log-level) "保留日志"，则 [清除](#clear) 方法将关闭。

```javascript
console.clear()
```

### <a name="see-also"></a>另请参阅

* [清除控制台](reference.md#clear-the-console)

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="count"></a>count

写入在同一行和同一行中调用 [count](#count) 方法次数 `label`。  使用 [countReset](#countreset) 方法可重置计数。

```javascript
console.count([label])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.count();
console.count('coffee');
console.count();
console.count();
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-count-button.msft.png" alt-text="console.count () 示例的结果" lightbox="../media/console-demo-count-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="countreset"></a>countReset

重置计数。

```javascript
console.countReset([label])
```

### <a name="example"></a>示例

```javascript
console.countReset();
console.countReset('coffee');
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="debug"></a>调试

与日志方法 [相同](#log) ，不同日志级别除外。

```javascript
console.debug(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Verbose`

### <a name="example"></a>示例

```javascript
console.debug('debug');
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-debug-button.msft.png" alt-text="console.debug () 示例的结果" lightbox="../media/console-demo-debug-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="dir"></a>dir

打印指定对象的 JSON 表示形式。

```javascript
console.dir(object)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.dir(document.head);
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-dir-button.msft.png" alt-text="console.dir () 示例的结果" lightbox="../media/console-demo-dir-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="dirxml"></a>dirxml

打印 后代的 XML 表示形式 `node`。

```javascript
console.dirxml(node)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.dirxml(document);
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-dirxml-button.msft.png" alt-text="console.dirxml () 示例的结果" lightbox="../media/console-demo-dirxml-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="error"></a>错误

将 打印 `object` 到 **控制台，** 将 它格式化为错误，并包括堆栈跟踪。

```javascript
console.error(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Error`

### <a name="example"></a>示例

```javascript
console.error("I'm sorry, Dave.  I'm afraid I can't do that.");
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-error-button.msft.png" alt-text="console.error () 示例的结果" lightbox="../media/console-demo-error-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="group"></a>组

直观地将邮件分组在一起，直到 [使用 groupEnd](#groupend) 方法。  使用 [groupCollapsed](#groupcollapsed) 方法可折叠最初记录到控制台的 **组**。

```javascript
console.group(label)
```

### <a name="example"></a>示例

```javascript
const label = 'Adolescent Irradiated Espionage Tortoises';
console.group(label);
console.info('Leo');
console.info('Mike');
console.info('Don');
console.info('Raph');
console.groupEnd(label);
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-group-button.msft.png" alt-text="console.group () 示例的结果" lightbox="../media/console-demo-group-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="groupcollapsed"></a>groupCollapsed

与 log 方法[相同](#log)，但组最初在记录到控制台时**折叠。**

```javascript
console.groupCollapsed(label)
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="groupend"></a>groupEnd

停止对邮件进行视觉分组。  请参阅 [group](#group) 方法。

```javascript
console.groupEnd(label)
```

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="info"></a>信息

与 [log 方法](#log) 相同。

```javascript
console.info(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.info('info');
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-info-button.msft.png" alt-text="console.info () 示例的结果" lightbox="../media/console-demo-info-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="log"></a>日志

将消息打印到 **控制台**。

```javascript
console.log(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.log('log');
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-log-button.msft.png" alt-text="console.log () 示例的结果" lightbox="../media/console-demo-log-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="table"></a>table

将对象数组记录为表。

```javascript
console.table(array)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
console.table([
      {
         first: 'René',
         last: 'Magritte',
      },
      {
         first: 'Chaim',
         last: 'Soutine',
         birthday: '18930113',
      },
      {
         first: 'Henri',
         last: 'Matisse',
      }
]);
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-table-button.msft.png" alt-text="console.table () 示例的结果" lightbox="../media/console-demo-table-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="time"></a>time

启动新计时器。  使用 [timeEnd](#timeend) 方法停止计时器，将已用时间打印到 **控制台**。

```javascript
console.time([label])
```

### <a name="example"></a>示例

```javascript
console.time();
for (var i = 0; i < 100000; i++) {
      let square = i ** 2;
}
console.timeEnd();
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-time-button.msft.png" alt-text="console.time () 示例的结果" lightbox="../media/console-demo-time-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="timeend"></a>timeEnd

停止计时器。  有关详细信息，请参阅 [time](#time) 方法。

```javascript
console.timeEnd([label])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="trace"></a>trace

将堆栈跟踪打印到 **控制台**。

```javascript
console.trace()
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="example"></a>示例

```javascript
const first = () => { second(); };
const second = () => { third(); };
const third = () => { fourth(); };
const fourth = () => { console.trace(); };
first();
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-trace-button.msft.png" alt-text="console.trace () 示例的结果" lightbox="../media/console-demo-trace-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="warn"></a>warn

将警告打印到 **控制台**。

```javascript
console.warn(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Warning`

### <a name="example"></a>示例

```javascript
console.warn('warn');
```

#### <a name="output"></a>输出

:::image type="content" source="../media/console-demo-warn-button.msft.png" alt-text="console.warn () 示例的结果" lightbox="../media/console-demo-warn-button.msft.png":::

<br/><br/>

---

<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

<!-- if an article's title is adequately descriptive, and the article is in the same TOC bucket as the present article, don't much need a link here: -->
* [MDN Web 文档> `console`](https://developer.mozilla.org/en-US/docs/Web/API/Console) 对象参考 - 具有方法的摘要概述，每个方法有一个页面，并包含其他语法详细信息。
* [在控制台工具中记录消息](console-log.md) - 交互式简介。
* [控制台工具实用程序函数和选择器](utilities.md) - **仅**控制台实用程序方法，如 和 `debug()` `monitorEvents()`。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/console/api)，由技术编写 (Chrome DevTools & Lighthouse) 创作。[](https://developers.google.com/web/resources/contributors/kaycebasques)

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
