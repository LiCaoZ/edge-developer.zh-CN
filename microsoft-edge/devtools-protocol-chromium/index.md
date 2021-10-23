---
description: 更新到 Microsoft Edge DevTools 协议
title: Microsoft EdgeDevTools 协议概述
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/06/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.openlocfilehash: 043ce449b8447b77c22b94389c5feea21a101bec
ms.sourcegitcommit: 97b32870897c702eed52d9fbbd13cfff2046ad87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2021
ms.locfileid: "12108561"
---
# <a name="microsoft-edge-devtools-protocol-overview"></a>Microsoft EdgeDevTools 协议概述

使用 DevTools 协议检测、检查、调试和配置文件浏览器，包括Microsoft Edge。  The Microsoft Edge DevTools Protocol matches the APIS of the Chrome DevTools Protocol.  有关参考文档，请导航到 [Chrome DevTools 协议查看器](https://chromedevtools.github.io/devtools-protocol/tot)。

> [!NOTE]
> 随着 Microsoft Edge 基础 Web 平台Chromium，Microsoft Edge (EdgeHTML) [DevTools 协议](/archive/microsoft-edge/legacy/developer/devtools-protocol/index)将不会接收任何进一步的更新。  The Microsoft Edge DevTools Protocol will match the API of the Chrome DevTools Protocol going.
>
> `ms` [) DevTool Microsoft Edge s](/archive/microsoft-edge/legacy/developer/devtools-protocol/index)协议不再支持在 Microsoft Edge (EdgeHTML) 中作为前缀的任何方法。


<!-- ====================================================================== -->
## <a name="using-the-devtools-protocol"></a>使用 DevTools 协议

若要将自定义工具客户端附加到开发人员工具服务器，Microsoft Edge：

1.  关闭所有 Microsoft Edge。

1.  使用Microsoft Edge调试端口启动客户端。

    ```shell
    msedge.exe --remote-debugging-port=9222
    ```

1.  （可选）可以使用一个不同的用户配置文件Microsoft Edge单独的应用程序实例。

    ```shell
    msedge.exe --user-data-dir=<some directory>
    ```

1.  接下来，使用 HTTP `list` 终结点获取可附加页面目标的列表。

    ```http
    http://localhost:9222/json/list
    ```

1.  最后，通过 DevTools Web 套接字服务器连接到所需目标的 并发出命令 `webSocketDebuggerUrl` /订阅事件消息。


<!-- ====================================================================== -->
## <a name="devtools-protocol-http-endpoints"></a>DevTools 协议 HTTP 终结点

Microsoft Edge DevTools 协议支持以下 HTTP 终结点。


<!-- ====================================================================== -->
## <a name="jsonversion"></a>/json/version

提供有关主机的浏览器及其支持的 DevTools 协议的哪个版本的信息。

**参数**

**无**

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

**无**

**Return 对象**

表示协议当前版本的可用 API 图面的 JSON 对象。


<!-- ====================================================================== -->
## <a name="jsonlist"></a>/json/list

提供用于调试的页面目标的候选列表。

**参数**

**无**

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

关闭目标进程。  例如，在Microsoft Edge中，关闭页面选项卡。

**参数**

目标 ID

**Return 对象**

```
String(“Target is closing”)
```


<!-- ====================================================================== -->
## <a name="remote-tools-for-microsoft-edge-beta"></a>Microsoft Edge 适用的远程工具 (Beta)

现在，你可以从 Microsoft Edge (安装[) Beta](https://www.microsoft.com/store/apps/9P6CMFV44ZLT) [Microsoft Store。](https://www.microsoft.com/store/apps/windows)  此应用使你能够远程调试Microsoft Edge计算机Windows 10或更高版本设备上运行的应用。

若要了解如何设置 Windows 设备，以及如何从开发计算机连接到该设备，请导航到开始使用远程调试[Windows设备](../devtools-guide-chromium/remote-debugging/windows.md)。

[Microsoft Edge (Beta) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)的远程工具使用与开发人员工具相同的 Microsoft Edge DevTools 协议与在要调试[](../devtools-guide-chromium/index.md)的 Windows 10 或更高版本设备上运行的 Microsoft Edge 通信。  此应用只是预pends and a process ID () `/msedge/` before each call to the `pid` protocol.  它支持以下 HTTP 终结点。

以下参考部分适用于远程工具 for Microsoft Edge。


<!-- ====================================================================== -->
## <a name="msedgejsonlist"></a>/msedge/json/list

提供所有进程 \ (包括 PBA 以及 Microsoft Edge\) 或更高版本设备上所有 Windows 10 实例的所有选项卡Windows 10进行 `msedge.exe` 调试。 [](../progressive-web-apps-chromium/index.md)

**参数**

**无**

**Return 对象**

```json
[{
   "description": "",
    "devtoolsFrontendUrl": "http://172.17.75.195:80/msedge/7264/devtools/inspector.html?ws=172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "faviconUrl": "https://docs.microsoft.com/favicon.ico",
    "id": "ED4FFDB4529723A0FAFCBDB9B45851BB",
    "title": "Get Started with Remote Debugging Windows Devices - Microsoft Edge Development | Microsoft Docs",
    "type": "page",
    "url": "https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/remote-debugging/windows",
    "webSocketDebuggerUrl": "ws://172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "browserProcessId": 7264
}, ...  ]
```


<!-- ====================================================================== -->
## <a name="msedge"></a>/msedge/

在功能上等同于 [/msedge/json/list](#msedgejsonlist)。


<!-- ====================================================================== -->
## <a name="msedgepidjsonlist"></a>/msedge/[pid]/json/list

提供与提供的调试匹配的 Microsoft Edge 实例的候选页面 `[pid]` 目标列表。

**参数**

**无**

**Return 对象**

```json
[{
    "description": "",
    "devtoolsFrontendUrl": "http://172.17.75.195:80/msedge/7264/devtools/inspector.html?ws=172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB",
    "faviconUrl": "https://docs.microsoft.com/favicon.ico",
    "id": "ED4FFDB4529723A0FAFCBDB9B45851BB",
    "title": "Get Started with Remote Debugging Windows Devices - Microsoft Edge Development | Microsoft Docs",
    "type": "page",
    "url": "https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/remote-debugging/windows",
    "webSocketDebuggerUrl": "ws://172.17.75.195:80/msedge/7264/devtools/page/ED4FFDB4529723A0FAFCBDB9B45851BB"
}, ...  ]
```


<!-- ====================================================================== -->
## <a name="msedgepidjsonversion"></a>/msedge/[pid]/json/version

提供有关与提供的Microsoft Edge版本匹配的应用程序实例及其支持的 `[pid]` DevTools 协议版本的信息。

**参数**

**无**

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

提供序列化为 JSON 的整个协议 API 图面，Microsoft Edge `[pid]` 提供的实例。

**参数**

**无**

**Return 对象**

JSON 对象，该对象表示与所提供的实例Microsoft Edge使用的协议版本的可用 API `[pid]` 图面。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [在 WebView2 中使用 Chrome DevTools 协议](../webview2/how-to/chromium-devtools-protocol.md)