---
title: 在扩展清单中声明 API 权限
description: 了解如何在清单中声明 API 的权限。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/17/2021
ms.openlocfilehash: 7f407d69fd03f9f478557d8d49ae0053bc376894
ms.sourcegitcommit: bbbf0c01af1bc21ab02da849e04408e1dafaeeaf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2022
ms.locfileid: "12699514"
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
# <a name="declare-api-permissions-in-extension-manifests"></a>在扩展清单中声明 API 权限

若要使用大部分 `chrome.*` API，扩展必须在清单的字段中 `permissions` 声明其意向。  扩展可以使用下表中的权限字符串声明权限，也可以使用模式来匹配类似的字符串。  权限有助于在扩展被恶意软件入侵时对其进行约束。  在安装扩展之前或在运行时根据需要向用户显示某些权限以供其同意;这些是权限警告。

如果 API 要求你在清单中声明权限，请参阅该 API 的文档以了解所需的权限。  例如，存储 API 页描述如何声明权 `storage` 限。

以下代码概述了如何在清单文件中声明权限：

```json
"permissions": [
  "tabs",
  "bookmarks",
  "http://www.blogger.com/",
  "http://*.google.com/",
  "unlimitedStorage"
]
```

下表列出了清单中要使用的当前可用权限字符串和说明。

| 权限字符串 | 详细信息 |
|:--- |:--- |
| `activeTab` | 请求根据 `activeTab` 规范授予扩展权限。 |
| `alarms` | 提供对 API 的 `chrome.alarms` 扩展访问权限。 |
| `background` | 使 Microsoft Edge 提前启动并延迟关闭，以便扩展的使用寿命可能更长。  当任何已安装的扩展具有 `background` 权限时，当用户登录到用户的计算机后以及在用户启动 Microsoft Edge 之前，Microsoft Edge 将立即以无形方式运行。  该 `background` 权限还允许 Microsoft Edge 继续运行，即使在其最后一个窗口关闭之后，直到用户显式退出 Microsoft Edge。 权 `background` 限通常用于后台页面。 <br/>禁用的扩展被视为未安装。 应将“后台”权限与 [后台脚本配合使用](https://developer.chrome.com/docs/extensions/mv3/background_pages/)。|
| `bookmarks` | 提供对 API 的 `chrome.bookmarks` 扩展访问权限。 |
| `browsingData` | 提供对 API 的 `chrome.browsingData` 扩展访问权限。 |
| `certificateProvider` | 提供对 API 的 `chrome.certificateProvider` 扩展访问权限。 |
| `clipboardRead` | 如果扩展使用 `document.execCommand('paste')`，则为必需。 |
| `clipboardWrite` | 指示扩展使用 `document.execCommand('copy')` 或 `document.execCommand('cut')`。 |
| `contentSettings` | 提供对 API 的 `chrome.contentSettings` 扩展访问权限。 |
| `contextMenus` | 提供对 API 的 `chrome.contextMenus` 扩展访问权限。 |
| `cookies` | 提供对 API 的 `chrome.cookies` 扩展访问权限。 |
| `debugger` | 提供对 API 的 `chrome.debugger` 扩展访问权限。 |
| `declarativeContent` | 提供对 API 的 `chrome.declarativeContent` 扩展访问权限。 |
| `declarativeNetRequest` | 提供对 API 的 `chrome.declarativeNetRequest` 扩展访问权限。 |
| `declarativeNetRequestFeedback` | 授予对 API 中事件和方法的 `chrome.declarativeNetRequest` 扩展访问权限，后者返回与之匹配的声明性规则的信息。 |
| `declarativeWebRequest` | 提供对 API 的 `chrome.declarativeWebRequest` 扩展访问权限。 |
| `desktopCapture` | 提供对 API 的 `chrome.desktopCapture` 扩展访问权限。 |
| `documentScan` | 提供对 API 的 `chrome.documentScan` 扩展访问权限。 |
| `downloads` | 提供对 API 的 `chrome.downloads` 扩展访问权限。 |
| `enterprise.deviceAttributes` | 提供对 API 的 `chrome.enterprise.deviceAttributes` 扩展访问权限。 |
| `enterprise.hardwarePlatform` | 提供对 API 的 `chrome.enterprise.hardwarePlatform` 扩展访问权限。 |
| `enterprise.networkingAttributes` | 提供对 API 的 `chrome.enterprise.networkingAttributes` 扩展访问权限。 |
| `enterprise.platformKeys` | 提供对 API 的 `chrome.enterprise.platformKeys` 扩展访问权限。 |
| `experimental` | 如果扩展使用任何 `chrome.experimental.*` API，则为必需。 |
| `fileBrowserHandler` | 提供对 API 的 `chrome.fileBrowserHandler` 扩展访问权限。 |
| `fileSystemProvider` | 提供对 API 的 `chrome.fileSystemProvider` 扩展访问权限。 |
| `fontSettings` | 提供对 API 的 `chrome.fontSettings` 扩展访问权限。 |
| `geolocation` | 允许扩展在不提示用户获取权限的情况下使用地理位置 API。 |
| `history` | 提供对 API 的 `chrome.history` 扩展访问权限。 |
| `identity` | 提供对 API 的 `chrome.identity` 扩展访问权限。 |
| `idle` | 提供对 API 的 `chrome.idle` 扩展访问权限。 |
| `loginState` | 提供对 API 的 `chrome.loginState` 扩展访问权限。 |
| `management` | 提供对 API 的 `chrome.management` 扩展访问权限。 |
| `nativeMessaging` | 提供对本机消息传送 API 的扩展访问权限。 |
| `notifications` | 提供对 API 的 `chrome.notifications` 扩展访问权限。 |
| `pageCapture` | 提供对 API 的 `chrome.pageCapture` 扩展访问权限。 |
| `platformKeys` | 提供对 API 的 `chrome.platformKeys` 扩展访问权限。 |
| `power` | 提供对 API 的 `chrome.power` 扩展访问权限。 |
| `printerProvider` | 提供对 API 的 `chrome.printerProvider` 扩展访问权限。 |
| `printing` | 提供对 API 的 `chrome.printing` 扩展访问权限。 |
| `printingMetrics` | 提供对 API 的 `chrome.printingMetrics` 扩展访问权限。 |
| `privacy` | 提供对 API 的 `chrome.privacy` 扩展访问权限。 |
| `processes` | 提供对 API 的 `chrome.processes` 扩展访问权限。 |
| `proxy` | 提供对 API 的 `chrome.proxy` 扩展访问权限。 |
| `scripting` | 提供对 API 的 `chrome.scripting` 扩展访问权限。 |
| `search` | 提供对 API 的 `chrome.search` 扩展访问权限。 |
| `sessions` | 提供对 API 的 `chrome.sessions` 扩展访问权限。 |
| `signedInDevices` | 提供对 API 的 `chrome.signedInDevices` 扩展访问权限。 |
| `storage` | 提供对 API 的 `chrome.storage` 扩展访问权限。 |
| `system.cpu` | 提供对 API 的 `chrome.system.cpu` 扩展访问权限。 |
| `system.display` | 提供对 API 的 `chrome.system.display` 扩展访问权限。 |
| `system.memory` | 提供对 API 的 `chrome.system.memory` 扩展访问权限。 |
| `system.storage` | 提供对 API 的 `chrome.system.storage` 扩展访问权限。 |
| `tabCapture` | 提供对 API 的 `chrome.tabCapture` 扩展访问权限。 |
| `tabGroups` | 提供对 API 的 `chrome.tabGroups` 扩展访问权限。 |
| `tabs` | 允许扩展访问可由多个 API 使用的对象的 `Tab` 特权字段，包括 `chrome.tabs` 和 `chrome.windows`。  在许多情况下，扩展不需要声明 `tabs` 权限即可使用这些 API。 |
| `topSites` | 提供对 API 的 `chrome.topSites` 扩展访问权限。 |
| `tts` | 提供对 API 的 `chrome.tts` 扩展访问权限。 |
| `ttsEngine` | 提供对 API 的 `chrome.ttsEngine` 扩展访问权限。 |
| `unlimitedStorage` | 为存储客户端数据（例如数据库和本地存储文件）提供无限配额。  如果没有此权限，扩展限制为 5 MB 的本地存储。 <br/>此权限仅适用于 Web SQL 数据库和应用程序缓存 (请参阅[问题 58985：无限存储权限应应用于本地存储](https://bugs.chromium.org/p/chromium/issues/detail?id=58985)) 。 <br/>此权限当前不适用于通配符子域，例如 `http://*.contoso.com`。 |
| `vpnProvider` | 提供对 API 的 `chrome.vpnProvider` 扩展访问权限。 |
| `wallpaper` | 提供对 API 的 `chrome.wallpaper` 扩展访问权限。 |
| `webNavigation` | 提供对 API 的 `chrome.webNavigation` 扩展访问权限。 |
| `webRequest` | 提供对 API 的 `chrome.webRequest` 扩展访问权限。 |
| `webRequestBlocking` | 如果扩展使用 API 阻止请求， `chrome.webRequest` 则为必需。 |



> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/docs/extensions/mv3/declare_permissions/)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
