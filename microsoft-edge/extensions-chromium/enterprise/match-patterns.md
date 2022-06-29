---
title: 匹配模式
description: 主机权限和内容脚本模式匹配的工作原理，以及示例。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/17/2021
ms.openlocfilehash: 4ae4df2490bb39b3f582b7a3b277a3ec8861ab31
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631581"
---
<!-- Copyright A. W. Fuchs

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="match-patterns"></a>匹配模式

主机权限和内容脚本匹配基于匹配模式定义的一组 URL。  匹配模式本质上是一个 URL，它以允许的方案开头`http`， (、`https``file`或`ftp`，并且可以包含“`*`”字符。  特殊模式 `<all_urls>` 与以允许的方案开头的任何 URL 匹配。  每个匹配模式有 3 个部分：

*   _方案_ - 例如，`http`或`file` `*`

> [!NOTE]
> 对 `file` URL 的访问不是自动的。  用户必须访问“扩展管理”页，并选择 `file` 访问请求它的每个扩展。

*   `_host_` - 例如，`www.google.com`或`*.google.com``*`;如果方案为文件，则没有主机部件。
*   `_path_` - 例如，`/*``/foo*`或 `/foo/bar`.  路径必须位于主机权限中，但始终被视为 `/*`。


<!-- ====================================================================== -->
## <a name="basic-syntax"></a>基本语法

基本语法：

```shell
<url-pattern> := <scheme>://<host><path>
<scheme> := '*' | 'http' | 'https' | 'file' | 'ftp'
<host> := '*' | '*.' <any char except '/' and '*'>+
<path> := '/' <any chars>
```

其含义 `*` 取决于它是在方案、主机还是路径部件中。  如果计划是`*`，那么它匹配或`http``https`，而不是`file`，或`ftp`。  如果主机只是 `*`，则它与任何主机匹配。 如果主机是 `*.hostname`，则它与指定的主机或任何子域匹配。  在路径部分中，每个字符匹配 `*` 0 个或更多个字符。  下表显示了一些有效的模式。


<!-- ====================================================================== -->
## <a name="examples-of-valid-patterns"></a>有效模式的示例

| 模式 | 它的作用 | 匹配 URL 的示例 |
|:--- |:--- |:--- |
| `http://*/*` | 匹配使用 http 方案的任何 URL | `http://www.google.com` `http://example.org/foo/bar.html` |
| `http://*/foo*` | 匹配任何主机上使用 http 方案的任何 URL，前提是路径以 `/foo` | `http://example.com/foo/bar.html` `http://www.google.com/foo` |
| `https://*.google.com/foo*bar` | 匹配使用 https 方案的任何 URL，该 URL 位于 `google.com` 主机 (上，例如 `www.google.com`， `docs.google.com`或 `google.com`) ，前提是路径以路径开头 `/foo` 并以结尾 `bar` | `https://www.google.com/foo/baz/bar` `https://docs.google.com/foobar` |
| `http://example.org/foo/bar.html` | 匹配指定的 URL | `http://example.org/foo/bar.html` |
|`file:///foo*` | 匹配路径以其开头的任何本地文件 `/foo` | `file:///foo/bar.html` `file:///foo` |
| `http://127.0.0.1/*` | 匹配使用 `http` 方案且位于主机上的任何 URL `127.0.0.1` | `http://127.0.0.1` `http://127.0.0.1/foo/bar.html` |
| `*://mail.google.com/*` | 匹配以或 `https://mail.google.com`. 开头`http://mail.google.com`的任何 URL。 | `http://mail.google.com/foo/baz/bar` `https://mail.google.com/foobar` |
| `<all_urls>` | 匹配使用允许方案的任何 URL。  (请参阅本部分的开头，了解允许的计划列表。)  | `http://example.org/foo/bar.html` `file:///bar/baz.html` |


<!-- ====================================================================== -->
## <a name="examples-of-invalid-patterns"></a>无效模式的示例

下面是模式匹配的 `_invalid_` 一些示例：

| 不良模式 | 为什么它是坏的 |
|:--- |:--- |
| `http://www.foo.com` | 否 `_path_` |
| `http://*foo/bar` | 主机中的“”`*`只能后跟“`.`”或“`/`” |
| `http://foo.*.bar/baz` | 如果“`*`”位于其中 `_host_`，则必须是第一个字符 |
| `http:/bar` | 缺少 `_scheme_` 分隔符 (“`/`应为”“`//`)  |
| `foo://*` | 无效 `_scheme_` |

某些方案在所有上下文中都不受支持。

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/extensions/match_patterns)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
