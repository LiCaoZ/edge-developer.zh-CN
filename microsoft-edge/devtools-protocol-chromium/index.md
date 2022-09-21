---
title: Microsoft Edge 开发工具协议
description: 使用 DevTools 协议检测、检查、调试和配置文件浏览器（包括 Microsoft Edge）。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/06/2021
ms.openlocfilehash: b8b000f01cdfc7163cb06cb9b3d55404c8fa3923
ms.sourcegitcommit: 4d5a0892ecdfbb06749149bd516c92b190700a9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2022
ms.locfileid: "12757809"
---
# <a name="microsoft-edge-devtools-protocol"></a>Microsoft Edge 开发工具协议

使用 DevTools 协议检测、检查、调试和配置文件浏览器（包括 Microsoft Edge）。  Microsoft Edge DevTools 协议与 Chrome DevTools 协议的 API 匹配。  有关参考文档，请转到 [Chrome DevTools 协议查看器](https://chromedevtools.github.io/devtools-protocol/tot)。

> [!NOTE]
> 随着 Microsoft Edge 的基础 Web 平台转移到Chromium，[Microsoft Edge (EdgeHTML) DevTools 协议](/archive/microsoft-edge/legacy/developer/devtools-protocol/index)将不会收到任何进一步的更新。  今后，Microsoft Edge DevTools 协议将匹配 Chrome DevTools 协议的 API。
>
> [Microsoft Edge (EdgeHTML) DevTools 协议](/archive/microsoft-edge/legacy/developer/devtools-protocol/index)中前缀`ms`的任何方法在 Microsoft Edge DevTools 协议中不再受支持。


<!-- ====================================================================== -->
## <a name="using-the-devtools-protocol"></a>使用 DevTools 协议

若要将自定义工具客户端附加到 Microsoft Edge 中的 DevTools 服务器，请执行以下操作：

1.  关闭 Microsoft Edge 的所有实例。

1.  使用远程调试端口启动 Microsoft Edge。

    ```shell
    msedge.exe --remote-debugging-port=9222
    ```

1.  （可选）可以使用不同的用户配置文件启动单独的 Microsoft Edge 实例。

    ```shell
    msedge.exe --user-data-dir=<some directory>
    ```

1.  接下来，使用 HTTP `list` 终结点获取可附加页面目标的列表。

    ```http
    http://localhost:9222/json/list
    ```

1.  最后，通过 DevTools Web 套接字服务器连接到 `webSocketDebuggerUrl` 所需目标并发出命令/订阅事件消息。


<!-- ====================================================================== -->
## <a name="devtools-protocol-http-endpoints"></a>DevTools 协议 HTTP 终结点

Microsoft Edge DevTools 协议支持以下 HTTP 终结点。


<!-- ====================================================================== -->
## <a name="jsonversion"></a>/json/version

提供有关主机浏览器及其支持的 DevTools 协议版本的信息。

**参数**

无。

**Return 对象**

```json
{
   "Browser": "Edg/75.0.115.0",
   "Protocol-Version": "1.3",
   "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3739.0 Safari/537.36 Edg/75.0.115.0",
   "V8-Version": "7.5.98",
   "WebKit-Version": "537.36 (@68a98f73c7d0f766fb5a013ea7f8dbb41089bc1b)",
   "webSocketDebuggerUrl": "ws://localhost:9222/devtools/browser/a9d0e8cf-476a-4a89-bba9-0fc27ce691cd"
}
```


<!-- ====================================================================== -->
## <a name="jsonprotocol"></a>/json/protocol

提供序列化为 JSON 的整个协议 API 图面。

**参数**

无。

**Return 对象**

JSON 对象，表示当前版本的协议的可用 API 图面。


<!-- ====================================================================== -->
## <a name="jsonlist"></a>/json/list

提供用于调试的页面目标的候选列表。

**参数**

无。

**Return 对象**

```json
[{
   "description": "",
   "devtoolsFrontendUrl": "/devtools/inspector.html?ws=localhost:9222/devtools/page/AB07C11A262D1EC8634EB12E2DCA4989",
   "id": "AB07C11A262D1EC8634EB12E2DCA4989",
   "title": "localhost:9222/json/protocol",
   "type": "page",
   "url": "http://localhost:9222/json/list",
   "webSocketDebuggerUrl": "ws://localhost:9222/devtools/page/AB07C11A262D1EC8634EB12E2DCA4989"
}, ...  ]
```


<!-- ====================================================================== -->
## <a name="jsonclose"></a>/json/close

关闭目标进程。  例如，在 Microsoft Edge 中，关闭页面选项卡。

**参数**

目标 ID

**Return 对象**

```
String("Target is closing")
```


<!-- ====================================================================== -->
## <a name="remote-tools-for-microsoft-edge-beta"></a>Microsoft Edge 适用的远程工具 (Beta)

可以从 [Microsoft Store](https://www.microsoft.com/store/apps/windows) [安装适用于 Microsoft Edge 的远程工具 (Beta) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)。  使用此应用，可以从开发计算机远程调试在Windows 10或更高版本设备上运行的 Microsoft Edge。

若要了解如何设置 Windows 设备并从开发计算机连接到它，请 [参阅远程调试 Windows 设备入](../devtools-guide-chromium/remote-debugging/windows.md)门。

Microsoft [Edge 远程工具 (Beta) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)使用与 [DevTools](../devtools-guide-chromium/overview.md) 相同的 Microsoft Edge DevTools 协议与要调试的Windows 10或更高版本设备上运行的 Microsoft Edge 通信。  每次调用协议之前，此应用只是预支 `/msedge/` 和进程 ID (`pid`) 。  它支持以下 HTTP 终结点。

以下参考部分适用于适用于 Microsoft Edge 的远程工具。


<!-- ====================================================================== -->
## <a name="msedgejsonlist"></a>/msedge/json/list

提供所有进程的候选列表`msedge.exe` (包括 [PVA](../progressive-web-apps-chromium/index.md) 和所有 Microsoft Edge 实例中的所有选项卡) Windows 10或更高版本设备上用于调试。

**参数**

无。

**Return 对象**

```json
[{
   "description": "",
    "devtoolsFrontendUrl": "http://172.17.75.195:80/msedge/7264/devtools/inspector.html?ws=172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "faviconUrl": "https://learn.microsoft.com/favicon.ico",
    "id": "ED4FFDB4529723A0FAFCBDB9B45851BB",
    "title": "Get Started with Remote Debugging Windows Devices - Microsoft Edge Development | Microsoft Docs",
    "type": "page",
    "url": "https://learn.microsoft.com/microsoft-edge/devtools-guide-chromium/remote-debugging/windows",
    "webSocketDebuggerUrl": "ws://172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "browserProcessId": 7264
}, ...  ]
```


<!-- ====================================================================== -->
## <a name="msedge"></a>/msedge/

在功能上等效于 [/msedge/json/list](#msedgejsonlist)。


<!-- ====================================================================== -->
## <a name="msedgepidjsonlist"></a>/msedge/[pid]/json/list

为 Microsoft Edge 实例提供与提供的 `[pid]` 调试匹配的页面目标的候选列表。

**参数**

无。

**Return 对象**

```json
[{
    "description": "",
    "devtoolsFrontendUrl": "http://172.17.75.195:80/msedge/7264/devtools/inspector.html?ws=172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "faviconUrl": "https://learn.microsoft.com/favicon.ico",
    "id": "ED4FFDB4529723A0FAFCBDB9B45851BB",
    "title": "Get Started with Remote Debugging Windows Devices - Microsoft Edge Development | Microsoft Docs",
    "type": "page",
    "url": "https://learn.microsoft.com/microsoft-edge/devtools-guide-chromium/remote-debugging/windows",
    "webSocketDebuggerUrl": "ws://172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB"
}, ...  ]
```


<!-- ====================================================================== -->
## <a name="msedgepidjsonversion"></a>/msedge/[pid]/json/version

提供与提供的 `[pid]` Microsoft Edge 实例匹配的信息，以及它支持哪个版本的 DevTools 协议。

**参数**

无。

**Return 对象**

```json
{
    "Browser": "Edg/82.0.452.0",
    "Protocol-Version": "1.3",
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/82.0.4080.0 Safari/537.36 Edg/82.0.452.0",
    "V8-Version": "8.2.263",
    "WebKit-Version": "537.36 (@fe0232051787ca94ac8edfc0084c3488b7d9bdb2)",
    "webSocketDebuggerUrl": "172.17.75.195:80/msedge/7264/devtools/browser/7a67c8c4-138b-48e3-bfe0-cb7af34d559a"
}
```


<!-- ====================================================================== -->
## <a name="msedgepidjsonprotocol"></a>/msedge/[pid]/json/protocol/

为与提供的 `[pid]`Microsoft Edge 实例匹配的 Microsoft Edge 实例提供序列化为 JSON 的整个协议 API 图面。

**参数**

无。

**Return 对象**

JSON 对象，表示与所提供的 `[pid]` 协议匹配的 Microsoft Edge 实例所使用的协议版本的可用 API 图面。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [在 WebView2 应用中使用 Chrome DevTools 协议](../webview2/how-to/chromium-devtools-protocol.md)
