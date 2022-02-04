---
title: 在扩展清单中声明 API 权限
description: 了解如何在清单中声明 API 的权限。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/17/2021
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

若要使用大部分 `chrome.*` API，扩展必须在 `permissions` 清单的字段中声明其意图。  扩展可以使用下表中的权限字符串声明权限，或使用模式来匹配类似的字符串。  如果扩展受到恶意软件的攻击，权限有助于限制扩展。  在安装扩展之前或运行时，会根据需要向用户显示一些权限，以征得他们的同意;这些是权限警告。

如果 API 要求你在清单中声明权限，请参阅该 API 的文档以了解所需的权限。  例如，存储 API 页面介绍了如何声明`storage`权限。

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

下表列出了清单中当前可用的权限字符串以及说明。

| 权限字符串 | 详细信息 |
|:--- |:--- |
| `activeTab` | 请求根据规范向扩展授予权限 `activeTab` 。 |
| `alarms` | 授予对 API 的扩展 `chrome.alarms` 访问权限。 |
| `background` | 使Microsoft Edge提前启动并延迟关闭，以便扩展的生命周期更长。  当任何安装的`background`扩展具有权限时，Microsoft Edge在用户登录到用户计算机时，以及用户启动 Microsoft Edge 之前，以不明显方式Microsoft Edge。  权限`background`还使Microsoft Edge继续运行，即使其最后一个窗口已关闭，直到用户显式退出Microsoft Edge。  此权限不会影响浏览器中关闭的扩展。  该 `background` 权限通常在背景页上使用。 |
| `bookmarks` | 授予对 API 的扩展 `chrome.bookmarks` 访问权限。 |
| `browsingData` | 授予对 API 的扩展 `chrome.browsingData` 访问权限。 |
| `certificateProvider` | 授予对 API 的扩展 `chrome.certificateProvider` 访问权限。 |
| `clipboardRead` | 如果扩展使用 ，则必需 `document.execCommand('paste')`。 |
| `clipboardWrite` | 指示扩展使用 或 `document.execCommand('copy')` `document.execCommand('cut')`。 |
| `contentSettings` | 授予对 API 的扩展 `chrome.contentSettings` 访问权限。 |
| `contextMenus` | 授予对 API 的扩展 `chrome.contextMenus` 访问权限。 |
| `cookies` | 授予对 API 的扩展 `chrome.cookies` 访问权限。 |
| `debugger` | 授予对 API 的扩展 `chrome.debugger` 访问权限。 |
| `declarativeContent` | 授予对 API 的扩展 `chrome.declarativeContent` 访问权限。 |
| `declarativeNetRequest` | 授予对 API 的扩展 `chrome.declarativeNetRequest` 访问权限。 |
| `declarativeNetRequestFeedback` | 授予对 API 内事件 `chrome.declarativeNetRequest` 和方法的扩展访问权限，这将返回有关匹配的声明性规则的信息。 |
| `declarativeWebRequest` | 授予对 API 的扩展 `chrome.declarativeWebRequest` 访问权限。 |
| `desktopCapture` | 授予对 API 的扩展 `chrome.desktopCapture` 访问权限。 |
| `documentScan` | 授予对 API 的扩展 `chrome.documentScan` 访问权限。 |
| `downloads` | 授予对 API 的扩展 `chrome.downloads` 访问权限。 |
| `enterprise.deviceAttributes` | 授予对 API 的扩展 `chrome.enterprise.deviceAttributes` 访问权限。 |
| `enterprise.hardwarePlatform` | 授予对 API 的扩展 `chrome.enterprise.hardwarePlatform` 访问权限。 |
| `enterprise.networkingAttributes` | 授予对 API 的扩展 `chrome.enterprise.networkingAttributes` 访问权限。 |
| `enterprise.platformKeys` | 授予对 API 的扩展 `chrome.enterprise.platformKeys` 访问权限。 |
| `experimental` | 如果扩展使用任意 API，则必需 `chrome.experimental.*` 。 |
| `fileBrowserHandler` | 授予对 API 的扩展 `chrome.fileBrowserHandler` 访问权限。 |
| `fileSystemProvider` | 授予对 API 的扩展 `chrome.fileSystemProvider` 访问权限。 |
| `fontSettings` | 授予对 API 的扩展 `chrome.fontSettings` 访问权限。 |
| `geolocation` | 允许扩展使用地理位置 API，而不提示用户授予权限。 |
| `history` | 授予对 API 的扩展 `chrome.history` 访问权限。 |
| `identity` | 授予对 API 的扩展 `chrome.identity` 访问权限。 |
| `idle` | 授予对 API 的扩展 `chrome.idle` 访问权限。 |
| `loginState` | 授予对 API 的扩展 `chrome.loginState` 访问权限。 |
| `management` | 授予对 API 的扩展 `chrome.management` 访问权限。 |
| `nativeMessaging` | 授予对本机消息传递 API 的扩展访问权限。 |
| `notifications` | 授予对 API 的扩展 `chrome.notifications` 访问权限。 |
| `pageCapture` | 授予对 API 的扩展 `chrome.pageCapture` 访问权限。 |
| `platformKeys` | 授予对 API 的扩展 `chrome.platformKeys` 访问权限。 |
| `power` | 授予对 API 的扩展 `chrome.power` 访问权限。 |
| `printerProvider` | 授予对 API 的扩展 `chrome.printerProvider` 访问权限。 |
| `printing` | 授予对 API 的扩展 `chrome.printing` 访问权限。 |
| `printingMetrics` | 授予对 API 的扩展 `chrome.printingMetrics` 访问权限。 |
| `privacy` | 授予对 API 的扩展 `chrome.privacy` 访问权限。 |
| `processes` | 授予对 API 的扩展 `chrome.processes` 访问权限。 |
| `proxy` | 授予对 API 的扩展 `chrome.proxy` 访问权限。 |
| `scripting` | 授予对 API 的扩展 `chrome.scripting` 访问权限。 |
| `search` | 授予对 API 的扩展 `chrome.search` 访问权限。 |
| `sessions` | 授予对 API 的扩展 `chrome.sessions` 访问权限。 |
| `signedInDevices` | 授予对 API 的扩展 `chrome.signedInDevices` 访问权限。 |
| `storage` | 授予对 API 的扩展 `chrome.storage` 访问权限。 |
| `system.cpu` | 授予对 API 的扩展 `chrome.system.cpu` 访问权限。 |
| `system.display` | 授予对 API 的扩展 `chrome.system.display` 访问权限。 |
| `system.memory` | 授予对 API 的扩展 `chrome.system.memory` 访问权限。 |
| `system.storage` | 授予对 API 的扩展 `chrome.system.storage` 访问权限。 |
| `tabCapture` | 授予对 API 的扩展 `chrome.tabCapture` 访问权限。 |
| `tabGroups` | 授予对 API 的扩展 `chrome.tabGroups` 访问权限。 |
| `tabs` | 向扩展授予对对象（ `Tab` 包括 和 ）可以使用的对象的特权字段 `chrome.tabs` 的访问权限 `chrome.windows`。  在许多情况下，扩展无需 `tabs` 声明权限，即使用这些 API。 |
| `topSites` | 授予对 API 的扩展 `chrome.topSites` 访问权限。 |
| `tts` | 授予对 API 的扩展 `chrome.tts` 访问权限。 |
| `ttsEngine` | 授予对 API 的扩展 `chrome.ttsEngine` 访问权限。 |
| `unlimitedStorage` | 提供用于存储客户端数据（如数据库和本地存储文件）的无限制配额。  如果没有此权限，扩展将限制为 5 MB 的本地存储。 |
| `vpnProvider` | 授予对 API 的扩展 `chrome.vpnProvider` 访问权限。 |
| `wallpaper` | 授予对 API 的扩展 `chrome.wallpaper` 访问权限。 |
| `webNavigation` | 授予对 API 的扩展 `chrome.webNavigation` 访问权限。 |
| `webRequest` | 授予对 API 的扩展 `chrome.webRequest` 访问权限。 |
| `webRequestBlocking` | 如果扩展使用 API 阻止 `chrome.webRequest` 请求，此为必需项。 |



> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developer.chrome.com/docs/extensions/mv3/declare_permissions/)。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
