---
title: 在 Microsoft Edge 中自动更新扩展
description: 了解 Microsoft Edge 中扩展的自动更新。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/13/2021
ms.openlocfilehash: f92244f071446ca994b7fb009f7338c02bb76615
ms.sourcegitcommit: 108b9a0673be978d89bc99d923582f569a43f6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2022
ms.locfileid: "12635440"
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
# <a name="automatically-update-extensions-in-microsoft-edge"></a>在 Microsoft Edge 中自动更新扩展

> [!NOTE]
> 本文不适用于使用 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) 仪表板发布的扩展。  可以使用仪表板向用户和 Microsoft Edge 加载项网站发布更新的版本。  有关详细信息，请参阅 [更新 Microsoft Edge 扩展](../publish/update-extension.md)。

将扩展设置为在用户计算机上自动更新时，当设置为自动更新时，你的扩展将与 Microsoft Edge 共享以下优势：

*   合并 bug 和安全修补程序。
*   添加新功能或性能增强功能。
*   改进用户界面。

以前支持基于非存储的扩展。  此外，以前还同时更新了本机二进制文件和扩展。  现在，Microsoft Edge 加载项网站托管扩展，并且使用与 Microsoft Edge 相同的机制更新扩展。  你无法控制更新机制。  更新依赖于本机二进制文件的扩展时，请小心。


<!-- ====================================================================== -->
## <a name="overview"></a>概述

每隔几个小时，Microsoft Edge 将检查每个已安装的扩展或应用是否具有更新 URL。  若要为扩展指定更新 URL，请使用 `update_url` 清单中的字段。  清单 `update_url` 中的字段指向要完成更新检查的位置。  对于每个 `update_url`文件，它发送更新的清单 XML 文件的请求。  如果更新清单 XML 文件列出了比安装版本更新的版本，Microsoft Edge 将下载并安装较新的版本。  相同的过程适用于手动更新，其中必须使用与当前安装的版本相同的私钥对新 `.crx` 文件进行签名。

> [!NOTE]
> 为了维护用户隐私，Microsoft Edge 不会发送包含自动更新清单请求的任何 `Cookie` 标头，并且会忽略对这些请求的响应中的任何 `Set-Cookie` 标头。


<!-- ====================================================================== -->
## <a name="update-url"></a>更新 URL

如果托管自己的扩展或应用，则必须将字 `update_url` 段添加到 `manifest.json` 文件中。  查看以下代码片段，了解该代码片段的 `update_url`示例。

```json
{
  "name": "My extension",
  ...
  "update_url": "http://contoso.com/mytestextension/updates.xml",
  ...
}
```


<!-- ====================================================================== -->
## <a name="update-manifest"></a>更新清单

服务器返回的更新清单应为 XML 文档;例如：

```xml
<?xml version='1.0' encoding='UTF-8'?>
<gupdate xmlns='http://www.google.com/update2/response' protocol='2.0'>
  <app appid='aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'>
    <updatecheck codebase='http://contoso.com/mytestextension/mte_v2.crx' version='2.0' />
  </app>
</gupdate>
```

更新的清单 XML 文件定义以下属性：

| 属性 | 详细信息 |
|:--- |:--- |
| `appid` | 扩展 ID 基于公钥的哈希生成。  若要查找扩展的 ID，请打开 Microsoft Edge 并查看 `edge://extensions`。 |
| `codebase` | 文件的 `.crx` URL。 |
| `version` | Microsoft Edge 使用此属性值来确定是否应下载 `.crx` 指定 `codebase`的文件。  它应与文件文件`.crx`中的`manifest.json`值`version`匹配。 |

更新清单 XML 文件可以通过包含多个元素来包含有关多个 `<app>` 扩展的信息。


<!-- ====================================================================== -->
## <a name="testing"></a>测试

默认更新检查频率为几个小时。  若要强制更新，请立即查看 `edge://extensions` 并选择 **“更新扩展** ”按钮。


<!-- ====================================================================== -->
## <a name="advanced-usage-request-parameters"></a>高级用法：请求参数

基本机制很简单。  若要自动更新扩展，请执行以下操作：

1.  在 Web 服务器上上传静态 XML 文件，例如 Apache。
1.  在发布新版本的扩展时更新 XML 文件。

利用添加到更新清单请求中的某些参数指示扩展 `ID` 和 `version`扩展这一事实。  可以对所有扩展使用相同的 `update URL` 扩展，而不是静态 XML 文件。  若要对所有扩展使用相同的 `update URL` 操作，请指向运行测试参数的动态服务器端代码的 URL。

以下示例演示更新 URL 的请求参数的格式：

```url
?x={extension_data}
```

在此示例中， `{extension_data}` 是使用以下格式的 URL 编码字符串。

```url
id={id}&v={version}
```

例如，以下两个扩展都指向相同的更新 URL `http://contoso.com/extension_updates.php`。

*   扩展 1
    *   ID： `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`
    *   更新 URL： `http://contoso.com/extension_updates.php`
    *   版本： `1.1`
*   扩展 2
    *   ID： `bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb`
    *   更新 URL： `http://contoso.com/extension_updates.php`
    *   版本： `0.4`


下面是更新每个扩展的请求。

```https
http://contoso.com/extension_updates.php?x=id%3Daaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa%26v%3D1.1
```

```https
http://contoso.com/extension_updates.php?x=id%3Dbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb%26v%3D0.4
```

还可以列出每个唯一更新 URL 的单个请求中的多个扩展。  以下示例将以前的请求合并到单个请求中：

```https
http://contoso.com/extension_updates.php?x=id%3Daaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa%26v%3D1.1&x=id%3Dbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb%26v%3D0.4
```

如果发送单个请求且使用相同更新 URL 的已安装扩展数过长，更新检查会发出更多 `GET` 请求。  `GET`如果请求 URL 大约为 2000 个字符，则该 URL 太长。

> [!NOTE]
> 将来，可能会发出单`POST`个请求，而不是发出多个`GET`请求，其中正文中`POST`包含请求参数。


<!-- ====================================================================== -->
## <a name="advanced-usage-minimum-browser-version"></a>高级使用情况：最低浏览器版本

随着 Microsoft Edge 扩展系统的新 API 发布，你可能希望发布仅适用于较新版本的 Microsoft Edge 的扩展或应用的更新版本。  当 Microsoft Edge 自动更新时，大多数用户可能需要几天时间才能更新到该新版本。

若要确保特定更新仅适用于当前版本或比特定版本更新的 Microsoft Edge 版本，请在更新清单中添加 `prodversionmin` 该属性。  

例如，在以下代码中，`prodversionmin`属性值`3.0.193.0`指定仅当用户运行 Microsoft Edge `3.0.193.0` 或更高版本时，应用才会自动更新到版本`2.0`：

```xml
<?xml version='1.0' encoding='UTF-8'?>
<gupdate xmlns='http://www.google.com/update2/response' protocol='2.0'>
  <app appid='aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'>
    <updatecheck codebase='http://contoso.com/mytestextension/mte_v2.crx' version='2.0' prodversionmin='3.0.193.0' />
  </app>
</gupdate>
```


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/docs/apps/autoupdate)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
