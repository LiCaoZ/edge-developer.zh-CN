---
description: 使用控制台 API 将消息写入控制台。
title: 控制台 API 参考
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/04/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: aa4b7803d7de9fc3567859c65b27ced3b10c2063
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12140324"
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
# <a name="console-api-reference"></a>控制台 API 参考

当你 **在** DevTools 中完成多个任务时，控制台工具非常有用。  API 可以包括在脚本中。 便利方法仅在控制台工具 **（** 如 和 方法） `debug()` `monitorEvents()` 中可用。  有关控制台入门的信息，请导航到**** 开始将消息记录[到控制台](console-log.md)。  有关控制台中便利方法详细信息 **，** 请导航到"[控制台实用程序 API 参考"。](utilities.md)

---


<!-- ====================================================================== -->
## <a name="assert"></a>assert

此方法在计算[结果为](#error)**时将**错误 `expression` 写入控制台 `false` 。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.assert(expression, object)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Error`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      const x = 5;
      const y = 3;
      const reason = 'x is expected to be less than y';
      console.assert(x < y, {x, y, reason});
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-assert-button.msft.png" alt-text="console.assert () 示例的结果" lightbox="../media/console-demo-assert-button.msft.png":::
         示例 `console.assert()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="clear"></a>clear

此方法 **清除控制台**。

如果 [打开](reference.md#filter-by-log-level) "保留日志"，则 [清除](#clear) 方法将关闭。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.clear()
```

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.clear();
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::

   :::column-end:::
:::row-end:::

### <a name="see-also"></a>另请参阅

*   [清除控制台](reference.md#clear-the-console)

---


<!-- ====================================================================== -->
## <a name="count"></a>count

此方法写入在同一行和同一行调用 [count](#count) 方法次数 `label` 。  使用 [countReset](#countreset) 方法可重置计数。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.count([label])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.count();
      console.count('coffee');
      console.count();
      console.count();
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-count-button.msft.png" alt-text="console.count () 示例的结果" lightbox="../media/console-demo-count-button.msft.png":::
         示例 `console.count()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="countreset"></a>countReset

此方法重置计数。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.countReset([label])
```

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.countReset();
      console.countReset('coffee');
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::

   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="debug"></a>调试

此方法与日志方法 [相同](#log) ，不同日志级别除外。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.debug(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Verbose`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.debug('debug');
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-debug-button.msft.png" alt-text="console.debug () 示例的结果" lightbox="../media/console-demo-debug-button.msft.png":::
         示例 `console.debug()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="dir"></a>dir

此方法打印指定对象的 JSON 表示形式。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.dir(object)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.dir(document.head);
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-dir-button.msft.png" alt-text="console.dir () 示例的结果" lightbox="../media/console-demo-dir-button.msft.png":::
         示例 `console.dir()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="dirxml"></a>dirxml

此方法打印 后代的 XML 表示形式 `node` 。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.dirxml(node)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.dirxml(document);
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-dirxml-button.msft.png" alt-text="console.dirxml () 示例的结果" lightbox="../media/console-demo-dirxml-button.msft.png":::
         示例 `console.dirxml()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="error"></a>错误

此方法将 打印 `object` 到 **控制台**，将格式设置为错误，并包括堆栈跟踪。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.error(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Error`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.error("I'm sorry, Dave.  I'm afraid I can't do that.");
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-error-button.msft.png" alt-text="console.error () 示例的结果" lightbox="../media/console-demo-error-button.msft.png":::
         示例 `console.error()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="group"></a>组

此方法直观地将邮件分组在一起，直到 [使用 groupEnd](#groupend) 方法。  使用 [groupCollapsed](#groupcollapsed) 方法可折叠最初记录到控制台的 **组**。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.group(label)
```

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      const label = 'Adolescent Irradiated Espionage Tortoises';
      console.group(label);
      console.info('Leo');
      console.info('Mike');
      console.info('Don');
      console.info('Raph');
      console.groupEnd(label);
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-group-button.msft.png" alt-text="console.group () 示例的结果" lightbox="../media/console-demo-group-button.msft.png":::
         示例 `console.group()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="groupcollapsed"></a>groupCollapsed

此方法与日志方法相同，[](#log)但组最初在记录到控制台**时折叠。**

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.groupCollapsed(label)
```

---


<!-- ====================================================================== -->
## <a name="groupend"></a>groupEnd

此方法停止对邮件进行视觉分组。  导航到 [group](#group) 方法。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.groupEnd(label)
```

---


<!-- ====================================================================== -->
## <a name="info"></a>信息

此方法与 log 方法[相同。](#log)

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.info(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.info('info');
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-info-button.msft.png" alt-text="示例 #console.info () 的结果" lightbox="../media/console-demo-info-button.msft.png":::
         示例 `console.info()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="log"></a>日志

此方法将一条消息打印到 **控制台**。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.log(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.log('log');
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-log-button.msft.png" alt-text="console.log () 示例的结果" lightbox="../media/console-demo-log-button.msft.png":::
         示例 `console.log()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="table"></a>table

此方法将对象数组记录为表。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.table(array)
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
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
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-table-button.msft.png" alt-text="console.table () 示例的结果" lightbox="../media/console-demo-table-button.msft.png":::
         示例 `console.table()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="time"></a>time

此方法启动一个新的计时器。  使用 [timeEnd](#timeend) 方法停止计时器，将已用时间打印到 **控制台**。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.time([label])
```

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.time();
      for (var i = 0; i < 100000; i++) {
          let square = i ** 2;
      }
      console.timeEnd();
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-time-button.msft.png" alt-text="console.time () 示例的结果" lightbox="../media/console-demo-time-button.msft.png":::
         示例 `console.time()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="timeend"></a>timeEnd

此方法将停止计时器。  有关详细信息，请导航到 [time](#time) 方法。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.timeEnd([label])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

---


<!-- ====================================================================== -->
## <a name="trace"></a>trace

此方法将堆栈跟踪打印到 **控制台**。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.trace()
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Info`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      const first = () => { second(); };
      const second = () => { third(); };
      const third = () => { fourth(); };
      const fourth = () => { console.trace(); };
      first();
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-trace-button.msft.png" alt-text="console.trace () 示例的结果" lightbox="../media/console-demo-trace-button.msft.png":::
         示例 `console.trace()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
## <a name="warn"></a>warn

此方法将警告输出到 **控制台**。

### <a name="javascript-syntax"></a>JavaScript 语法

```javascript
console.warn(object [, object, ...])
```

[日志级别](reference.md#persist-messages-across-page-loads)： `Warning`

### <a name="javascript-example"></a>JavaScript 示例

:::row:::
   :::column span="1":::
      输入
   :::column-end:::
   :::column span="3":::
      ```javascript
      console.warn('warn');
      ```
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      输出
   :::column-end:::
   :::column span="3":::
      :::image type="complex" source="../media/console-demo-warn-button.msft.png" alt-text="console.warn () 示例的结果" lightbox="../media/console-demo-warn-button.msft.png":::
         示例 `console.warn()` 结果 :::image-end:::
   :::column-end:::
:::row-end:::

---


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/console/api)，由技术编写 (、Chrome DevTools & Lighthouse) 创作。 [](https://developers.google.com/web/resources/contributors/kaycebasques)

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
