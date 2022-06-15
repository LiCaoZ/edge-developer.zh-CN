---
title: 功能和 EdgeOptions
description: EdgeDriver 支持的 WebDriver 功能和特定于Microsoft Edge的选项的参考。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 06/09/2022
ms.openlocfilehash: c4bd4c98431d6b5967d8007a2c9f07aba556171a
ms.sourcegitcommit: 327937a2c505038f4533f3dab38fa058df91c4e8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2022
ms.locfileid: "12595032"
---
# <a name="capabilities-and-edgeoptions"></a>功能和 EdgeOptions

功能是可用于自定义和配置会话的 `EdgeDriver` 选项。  若要了解如何启动新`EdgeDriver`会话，请参阅[自动Microsoft Edge](index.md#automate-microsoft-edge)。  本文介绍所有支持的Microsoft Edge功能，并提供有关将功能传递给`EdgeDriver`会话的详细信息。

功能将作为 JSON 映射传递到 WebDriver 会话，但不需要或建议以这种方式设置它们。   (（如 [Selenium](https://www.selenium.dev)) ）的 WebDriver 测试框架提供语言绑定，这些绑定通常具有方便的方法，因此无需自行配置 JSON 映射。  例如，Selenium 通过 `EdgeOptions` 类配置功能。


若要详细了解如何配置功能，请参阅首选 WebDriver 测试框架的文档。  有关详细信息，请参阅 [“选择 WebDriver 测试框架](index.md#choose-a-webdriver-testing-framework)”。


<!-- ====================================================================== -->
## <a name="using-the-edgeoptions-class"></a>使用 EdgeOptions 类

创建一个实例`EdgeOptions`，为设置特定于Microsoft Edge功能提供方便的方法。  配置 `EdgeOptions` 对象后，传 `EdgeOptions` 入 `EdgeDriver` 构造函数。

```csharp
var options = new EdgeOptions();
options.AddExtensions("/path/to/extension.crx");
var driver = new EdgeDriver(options);
```

若要使用没有关联的便利方法的功能，请使用该 `AddAdditionalEdgeOption` 方法。  必须传递功能的全名和类型正确的值。  有关接受的功能和值类型的完整列表， [请参阅 EdgeOptions 对象](#edgeoptions-object)。

```csharp
options.AddAdditionalEdgeOption("wdpAddress", "remotehost:50080");
```


<!-- ====================================================================== -->
## <a name="recognized-capabilities"></a>识别的功能

有关接受的标准功能 `EdgeDriver` ，请参阅 [Selenium 文档](https://www.selenium.dev/documentation/en/driver_idiosyncrasies/shared_capabilities/) 和 [W3C WebDriver 标准](https://www.w3.org/TR/webdriver#capabilities)。  本文仅列出特定于Microsoft Edge的功能。


<!-- ====================================================================== -->
## <a name="edgeoptions-object"></a>EdgeOptions 对象

大多数特定于Microsoft Edge功能都是通过对象公开的`EdgeOptions`。  在某些语言中，功能由 `EdgeOptions` 类实现。  在其他语言中，这些功能存储在字典下`ms:edgeOptions``DesiredCapabilities`。

| 功能 | 类型 | 详细信息 |
|:--- |:--- |:--- |
| `args` | 字符串列表 | 要在启动时传递给Microsoft Edge进程的命令行参数列表。 具有关联值的参数应由 `=` 符号 (分隔，例如， `['start-maximized', 'user-data-dir=/tmp/temp_profile']`) 。 如果要启动 WebView2 应用，则会将这些参数传递给应用，而不是基础Microsoft Edge浏览器进程。 若要在启动 WebView2 应用时将参数传递给浏览器进程，请改用 [webviewOptions.additionalBrowserArguments](#webviewoptions-object) 。 |
| `binary` | 字符串 | 要在macOS上使用 (的Microsoft Edge二进制文件的路径，路径应该是实际的二进制文件，而不仅仅是应用。  例如， `/Applications/Microsoft Edge.app/Contents/MacOS/Microsoft Edge`) 。 |
| `debuggerAddress` | 字符串 | 要连接到的调试器服务器的地址，其形式 `hostname/ip:port`例如 `127.0.0.1:38947`。 |
| `detach` | 布尔型 | 默认值 = `false`. 如果`false`在 WebDriver 服务关闭时Microsoft Edge退出，即使 WebDriver 本地端尚未关闭会话。  如果`true`Microsoft Edge仅在 WebDriver 本地端关闭会话时退出。  如果 `true`WebDriver 本地端未关闭会话，`EdgeDriver`则不会清理Microsoft Edge实例使用的临时用户数据文件夹。 |
| `excludeSwitches` | 字符串列表 | Microsoft Edge命令行开关的列表，以排除在开始Microsoft Edge时默认传递的 EdgeDriver。  `--`避免交换机的前缀。 |
| `extensions` | 字符串列表 | 要在启动时安装的扩展列表。  列表中的每个项应为 base-64 编码的打包扩展 () `.crx` 。 |
| `localState` | 字典 | 包含每个条目的字典，其中包含首选项的名称和值。  首选项应用于用户数据文件夹中的本地状态文件。 |
| `minidumpPath` | 字符串 | 用于存储Microsoft Edge小型转储的目录。   (仅在 Linux.) 上受支持 |
| `mobileEmulation` | 字典 | 一个字典，其中包含值，或值用于`deviceName``deviceMetrics`和 `userAgent`。 |
| `perfLoggingPrefs` | 字典 | 指定性能日志记录首选项的可选字典。  有关详细信息，请参阅 [perfLoggingPrefs 对象](#perfloggingprefs-object)。 |
| `prefs` | 字典 | 包含每个条目的字典，其中包含首选项的名称和值。  首选项仅应用于正在使用的用户配置文件。  有关示例，请参阅`Preferences`Microsoft Edge的用户数据文件夹中的文件。 |
| `wdpAddress` | 字符串 | 要连接到的Windows设备门户服务器的地址，`hostname/ip:port`例如`127.0.0.1:50080`。  有关详细信息，请参阅[远程调试 - Windows 10设备](../devtools-guide-chromium/remote-debugging/windows.md)。 |
| `wdpPassword` | 字符串 | 连接到Windows设备门户服务器时要使用的可选密码。  如果服务器已启用身份验证，则为必需。 |
| `wdpUsername` | 字符串 | 连接到Windows设备门户服务器时要使用的可选用户名。  如果服务器已启用身份验证，则为必需。 |
| `webviewOptions` | 字典 | 可选字典，可用于在启动 WebView2 应用时配置 WebView2 环境。 有关详细信息，请参阅 [webviewOptions 对象](#webviewoptions-object)。 |
| `windowsApp` | 字符串 | 例如`Microsoft.MicrosoftEdge.Stable_8wekyb3d8bbwe!MSEDGE`，要启动的Microsoft Edge应用包的应用程序用户模型 ID。  `binary`使用Windows设备门户连接到Windows 10X设备或模拟器时，请使用`windowsApp`它。 |
| `windowTypes` | 字符串列表 | 窗口句柄列表中显示的窗口类型的列表。  若要访问Android Webview 元素，请包括`webview`在列表中。 |


<!-- ====================================================================== -->
## <a name="perfloggingprefs-object"></a>perfLoggingPrefs 对象

字 `perfLoggingPrefs` 典具有以下格式。 所有密钥都是可选的。

| 项 | 类型 | 默认值 | 详细信息 |
|:--- |:--- |:--- |:--- |
| `bufferUsageReportingInterval` | 正整数 | 1000 | DevTools 跟踪缓冲区使用事件之间的请求毫秒数。  例如，如果为 1000，则每秒一次，DevTools 将报告跟踪缓冲区的完整程度。  如果报表指示缓冲区使用率为 100%，则会发出警告。 |
| `enableNetwork` | 布尔型 | true | 从网络域收集 (或不收集) 事件。 |
| `enablePage` | 布尔型 | true | 从 Page 域收集 (或不收集) 事件。 |
| `traceCategories` | 字符串 |  (空)  | 以逗号分隔的Microsoft Edge跟踪类别的字符串，应为其收集跟踪事件。  未指定或空字符串禁用跟踪。 |


<!-- ====================================================================== -->
## <a name="webviewoptions-object"></a>webviewOptions 对象

该 `webviewOptions` 字典用于在启动 WebView2 应用时配置 WebView2 环境。 它具有以下格式。 所有密钥都是可选的。

| 项 | 类型 | 默认值 | 详细信息 |
|:--- |:--- |:--- |:--- |
| `browserExecutableFolder` | 字符串 |  (空)  | 包含要使用的固定版本 WebView2 运行时的文件夹的路径。 有关将固定版本运行时分发与 WebView2 配合使用的详细信息，请参阅 [“分发 WebView2 应用”和“WebView2 运行时](../webview2/concepts/distribution.md#the-fixed-version-runtime-distribution-mode)”。 |
| `userDataFolder` | 字符串 |  (空)  | WebView2 将使用的用户数据文件夹的路径。 如果`userDataFolder`未指定，Microsoft Edge WebDriver 将创建一个临时用户数据文件夹。 有关使用 WebView2 管理用户数据文件夹的详细信息，请参 [阅“管理用户数据文件夹](../webview2/concepts/user-data-folder.md)”。 |
| `additionalBrowserArguments` | 字符串列表 |  | WebView2 将在启动时传递给浏览器进程的命令行参数列表。 具有关联值的参数应由 `=` 符号 (分隔，例如， `['start-maximized', 'log-level=0']`) 。 |
| `releaseChannelPreference` | 字符串 |  | 要使用的首选 WebView2 常青运行时分发。 可以是 `"stable"` 或 `"canary"`. |

<!-- ====================================================================== -->
## <a name="returned-capabilities"></a>返回的功能

以下列表包含创建新会话时返回的所有特定于Microsoft Edge的功能`EdgeDriver`。

| 功能 | 类型 | 详细信息 |
|:--- |:--- |:--- |
| `msedge.msedgedriverVersion` | 字符串 | EdgeDriver 的版本。 |
| `msedge.userDataDir` | 字符串 | Microsoft Edge实例使用的用户数据文件夹的路径。 |
