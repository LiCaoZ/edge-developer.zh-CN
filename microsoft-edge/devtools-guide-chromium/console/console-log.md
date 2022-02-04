---
title: 在控制台工具中记录消息
description: 如何在开发人员工具控制台中记录Microsoft Edge JavaScript。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
---
# <a name="log-messages-in-the-console-tool"></a>在控制台工具中记录消息

自浏览器开始**** `print` `log`提供开发人员工具以来，控制台一直很常用，因为在大多数编程课程，你学习输出某种类型或命令，以了解有关代码发生的情况的见解。

在 DevTools 之前，对于 JavaScript， `alert()` 你只能使用 或 `document.write()` 语句在浏览器中调试。  使用 **** DevTools`Console`，若要在控制台中记录信息，控制台中提供了对象的许多方法，如控制台**** 对象 [API 参考中所列](api.md)。


## <a name="console-messages-examples-log-info-error-and-warn"></a>控制台消息示例：日志、信息、错误和警告

对象 `Console` 具有多个级别的邮件日志记录方法：

* `console.log` - 将文本作为日志消息打印到控制台。
* `console.info` - 将文本作为信息性消息打印到控制台。
* `console.error` - 将文本作为错误消息打印到控制台。
* `console.warn` - 将文本作为警告打印到控制台。


### <a name="example-code"></a>示例代码

```javascript
// prints the text to the console as  a log message
console.log('This is a log message')

// prints the text to the console as an informational message
console.info('This is some information') 

// prints the text to the console as an error message
console.error('This is an error')

// prints the text to the console as a warning
console.warn('This is a warning') 
```


### <a name="demo-webpage-console-messages-examples-log-info-error-and-warn"></a>演示网页：控制台消息示例：日志、信息、错误和警告

若要尝试使用控制台中的日志记录函数：

<!-- demo 1 of 6 -->

1. 打开演示网页 [控制台消息示例：日志、信息、](https://microsoftedge.github.io/Demos/devtools-console/logging-examples.html) 错误和新窗口或选项卡中的警告。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 将打开， **主机在主** 工具栏中打开。

   演示页面已经将上述日志消息发送到 **控制台**：

   :::image type="content" source="../media/console-log-examples.msft.png" alt-text="控制台显示来自不同日志 API 的消息。" lightbox="../media/console-log-examples.msft.png":::

   和 `log()` `info()` 方法似乎执行相同的操作。  对`info()`不同的`log()`日志任务使用 和 ，因为这允许您筛选控制台消息[](console-filters.md)，以仅显示日志条目的子集。
  
   和 `error()` `warn()` 方法在消息旁边显示一个图标，以及检查消息堆栈 [跟踪](https://en.wikipedia.org/wiki/Stack_trace) 的方法。

1. 将任意示例复制并粘贴到 **控制台中**，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


<!-- ====================================================================== -->
## <a name="different-types-of-log-entries-and-variables"></a>不同类型的日志条目和变量

您可以将任何有效的 JavaScript 或 DOM 引用发送到控制台，而不是日志 **文本**。  **控制台会**适当地显示从控制台日志消息发送给它的各种类型的 JavaScript 值。  **控制台**显示结果的已筛选和格式化表示形式。


### <a name="example-code"></a>示例代码

```javascript
let x = 2;

// logs the value of x
console.log(x);

// logs the name x and value of x
console.log({x})   

// logs a DOM reference  
console.log(document.querySelector('body'));

// logs an Object
console.log({"type":"life", "meaning": 42});
let w3techs = ['HTML', 'CSS', 'SVG', 'MathML'];

// logs an Array
console.log(w3techs);
```


### <a name="demo-webpage-logging-different-variable-types"></a>演示网页：记录不同的变量类型

若要使用 `log` 函数显示不同的变量类型，

<!-- demo 2 of 6 -->

1. 打开演示网页 [控制台消息示例：记录](https://microsoftedge.github.io/Demos/devtools-console/logging-types.html) 新窗口或选项卡中的不同类型。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 将打开， **主机在主** 工具栏中打开。

   每种类型的结果以不同方式显示。

1. 单击三角形切换信息并更详细地分析每个结果。

   假设您收到许多仅显示值的日志消息，但不知道该值源自何处。  对于这种情况，我们在 变量`{}``x`周围添加了大括号，以便提供更好的分组。

   在控制台中记录不同类型的 **变量**：

   :::image type="content" source="../media/console-log-types.msft.png" alt-text="在控制台中记录不同类型的变量。" lightbox="../media/console-log-types.msft.png":::

   使用扩展的额外信息在 **控制台中** 记录不同类型的变量：

   :::image type="content" source="../media/console-log-types-expanded.msft.png" alt-text="使用扩展的额外信息在控制台中记录不同类型的变量。" lightbox="../media/console-log-types-expanded.msft.png":::

1. 将任意示例复制并粘贴到 **控制台中**，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


<!-- ====================================================================== -->
## <a name="format-and-convert-values-with-specifiers"></a>使用说明符设置值的格式和转换值

所有日志方法的一个特殊功能是，您可以在日志语句的消息中使用说明符。  说明符是日志消息的一部分，以百分比符号 () `%` 字符开始。  使用说明符，可以记录不同格式的某些值，甚至可以在两种格式之间转换。

*  `%s` 记录为"字符串"。
*  `%i` 或 `%d` 作为 Integers 记录。
*  `%f` 记录为浮点值。
*  `%o` 日志作为可展开的 DOM 元素。
*  `%O` 日志作为可展开的 JavaScript 对象。
*  `%c` 允许您使用 CSS 设置邮件样式。

### <a name="example-code"></a>示例代码

```javascript
// logs "10x console developer"
console.log('%ix %s developer', 10, 'console');

// logs PI => 3.141592653589793
console.log(Math.PI); 

// logs PI as an integer = 3
console.log('%i', Math.PI); 

// logs the document body as a DOM node
console.log('%o', document.body); 

// logs the body of the document as a JavaScript object with all properties
console.log('%O', document.body); 

// shows the message as red and big
console.log('%cImportant message follows','color:red;font-size:40px')
```


### <a name="demo-webpage-logging-with-specifiers"></a>演示网页：使用说明符记录

<!-- demo 3 -->

1. 打开演示页面 [控制台消息示例：使用说明符](https://microsoftedge.github.io/Demos/devtools-console/logging-with-specifiers.html) 记录新选项卡或窗口中的内容。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 将打开， **主机在主** 工具栏中打开。

   该网页已经使用输出 **填充了** 控制台。

   第一个示例演示了说明符的替换顺序是字符串后的参数顺序：

   ```javascript
   console.log('%ix %s developer', 10, 'console'); // logs "10x console developer"
   ```
   
1. 单击输出结果中的 `log` 展开器三角形，以展开并查看由网页中的上述语句输出的数据。

1. 如有必要，按 `F5` 以重新加载页面并重新填充 **控制台** 输出。

   说明符用于记录、格式化和转换值：

   :::image type="content" source="../media/console-log-specifiers.msft.png" alt-text="使用说明符记录并转换值。" lightbox="../media/console-log-specifiers.msft.png":::

1. 在 **控制台中**，单击三角形以展开日志结果，以查看 和 `%o` 说明 `%O` 符之间的差。

   网页正文显示为可展开的 DOM 节点，或显示为网页正文上所有 JavaScript 属性的完整列表：

   :::image type="content" source="../media/console-log-specifiers-expanded.msft.png" alt-text="Expand 结果显示 %O 和 %o 说明符之间的差值 - 正文显示为可展开的 DOM 节点或网页正文上所有 JavaScript 属性的完整列表。" lightbox="../media/console-log-specifiers-expanded.msft.png":::

1. 将上述示例代码列表复制并粘贴到 **控制台**中，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


<!-- ====================================================================== -->
## <a name="group-log-messages"></a>组日志消息

如果记录大量信息 `group` ，可以使用 和 `groupCollapsed` 方法在控制台中将日志消息显示为可展开和可折叠 **组**。  可以嵌套和命名组，使数据更易于理解。

### <a name="example-code"></a>示例代码

```javascript
// Example 1: Nested groups, with the inner group hidden (collapsed):
console.group("Passengers: Heart of Gold");
console.log('Zaphod');
console.log('Trillian');
console.log('Ford');
console.log('Arthur');
console.log('Marvin');
console.groupCollapsed("Hidden");
console.log('(Frankie & Benjy)');
console.groupEnd("Hidden");
console.groupEnd("Passengers: Heart of Gold");

// Example 2:
let technologies = {
  "Standards": ["HTML", "CSS", "SVG", "ECMAScript"],
  "Others": ["jQuery", "Markdown", "Textile", "Sass", "Pug"]
}
for (tech in technologies) {
  console.groupCollapsed(tech);
  technologies[tech].forEach(t => console.log(t));
  console.groupEnd(tech);
}
```


### <a name="demo-webpage-grouping-logs"></a>演示网页：分组日志

本示例中，可以选择生成组名称。

<!-- demo 4 -->

1. 打开演示页面 [控制台消息示例：将日志分组](https://microsoftedge.github.io/Demos/devtools-console/logging-with-groups.html) 到新选项卡或窗口中。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 将打开， **主机在主** 工具栏中打开。

   该网页已经使用输出 **填充了** 控制台。

   将大量值记录为组：

   :::image type="content" source="../media/console-log-groups.msft.png" alt-text="将大量值记录为组。" lightbox="../media/console-log-groups.msft.png":::

1. 在控制台输出中，展开并折叠每个部分：

   :::image type="content" source="../media/console-log-groups-expanded.msft.png" alt-text="可以展开和折叠每个组。" lightbox="../media/console-log-groups-expanded.msft.png":::

1. 将上述示例代码列表复制并粘贴到 **控制台**中，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


<!-- ====================================================================== -->
## <a name="display-complex-data-as-tables"></a>将复杂数据显示为表

该方法 `console.table()` 不将复杂数据记录为可折叠和可展开的对象，而是记录为可以使用不同标题进行排序的表。  排序表使用户更容易查看信息。


### <a name="example-code"></a>示例代码

```javascript
let technologies = {
  "Standards": ["HTML", "CSS", "SVG", "ECMAScript"],
  "Others": ["jQuery", "Markdown", "Textile", "Sass", "Pug"]
}
// log technologies as an object
console.log(technologies);
// show technologies as a table
console.table(technologies);

// get the dimensions of the document body
let bodyDimensions = document.body.getBoundingClientRect();
// show dimensions as an object
console.log(bodyDimensions);
// show dimensions as a table
console.table(bodyDimensions);
```

演示页面的代码列表的第二部分将进一步向下显示。


### <a name="demo-webpage-using-table-formatting"></a>演示网页：使用表格格式

将复杂数据显示为表：

<!-- demo 5 -->

1. 打开演示页面 [控制台消息示例：使用新](https://microsoftedge.github.io/Demos/devtools-console/logging-with-table.html) 窗口或选项卡中的表。

1. 按`Control`+`Shift`+`J`（Windows、Linux）或 `Command`+`Option`+`J` （macOS）。  DevTools 将打开， **主机在主** 工具栏中打开。

   该网页已经使用输出 **填充了** 控制台。

1. 在控制台 **中**，单击展开器三角形。

1. 单击展开器三角形。  使用 显示数据 `console.table` 可使数据更易于读取：

   :::image type="content" source="../media/console-log-table.msft.png" alt-text="使用 console.table 显示数据，以便更轻松地阅读。" lightbox="../media/console-log-table.msft.png":::

1. 将上述代码列表复制并粘贴到 **控制台中**，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


的输出 `console.table` 具有表格格式。  输出不仅具有表格式，不仅当输出显示在控制台中时，而且**** 当您将表复制并粘贴到 Microsoft Excel、Microsoft Word 或其他支持表格数据的产品中时，输出的结构保持不变。


#### <a name="specify-an-array-of-columns-for-each-property-for-readability"></a>为每个属性指定一个列数组，以用于可读性

如果数据具有命名参数 `console.table()` ，则该方法还允许您为每个属性指定一 `Array` 个列，以作为第二个参数显示。  以下示例演示如何指定一个可读的列数组：

##### <a name="example-code"></a>示例代码

此代码来自上述同一演示网页。

```javascript
// get all the h1, p and script elements
let contentElements = document.querySelectorAll(':is(h1,p,script)');
// show the elements as an unfiltered table
console.table(contentElements)
// show only relevant columns
console.table(contentElements,['nodeName', 'innerText', 'offsetHeight'])
```

此代码筛选方法显示 `console.table()` 的信息。

该代码提供要显示的属性数组，作为第二个参数：

:::image type="content" source="../media/console-log-table-filtered.msft.png" alt-text="筛选&quot;console.table&quot;显示的信息，并提供要显示的属性数组作为第二个参数。" lightbox="../media/console-log-table-filtered.msft.png":::

1. 将上述代码列表复制并粘贴到 **控制台中**，然后按 `Enter`。

   输出将显示在控制台 **中**您输入的代码下方。


### <a name="log-statements-vs-breakpoint-debugging-and-live-expressions"></a>日志语句与断点调试和 Live Expressions

你可能会尝试将这些方法 `log` 用作调试网页的主要方式，因为日志方法易于使用。  请考虑任何请求 `console.log()` 的结果。  已发布的产品不应使用用于 `log` 调试的任何声明，因为它可能会向用户显示内部信息。  控制台中创建的噪音 **非常** 强烈。

请尝试使用`log`断[点调试或实时表达式，而不是](../javascript/breakpoints.md)[语句](live-expressions.md)。  您可能会发现您的工作流更有效，并且您可以获得更好的结果。
