---
title: 功能和 EdgeOptions
description: EdgeDriver 支持的 WebDriver 功能和Microsoft Edge特定选项的参考。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: devtools
ms.date: 02/10/2021
ms.openlocfilehash: aa77c7c47ed957c877b71a74eb54bef1600aebc4
ms.sourcegitcommit: fad2471fb5d304c36ad4b52c57c9fb791356d097
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2022
ms.locfileid: "12459705"
---
# <a name="capabilities-and-edgeoptions"></a>功能和 EdgeOptions

功能是可用于自定义和配置会话的选项 `EdgeDriver` 。  若要了解如何启动新会话`EdgeDriver`，请参阅自动执行[Microsoft Edge](index.md#automate-microsoft-edge)。  本文介绍所有支持的功能Microsoft Edge并提供有关将`EdgeDriver`这些功能传递到会话的详细信息。

功能作为 JSON 映射传递到 WebDriver 会话。  WebDriver 测试框架提供 WebDriver 语言绑定。  WebDriver 语言绑定通常提供类型安全的便利方法，因此无需自己配置 JSON 映射。  不同的 WebDriver 语言绑定使用不同的机制来配置功能。  [Selenium](https://www.selenium.dev) 通过类配置 `EdgeOptions` 功能。

若要详细了解如何配置功能，请参阅文档了解首选 WebDriver 测试框架。  有关详细信息，请参阅 [选择 WebDriver 测试框架](index.md#choose-a-webdriver-testing-framework)。


<!-- ====================================================================== -->
## <a name="using-the-edgeoptions-class"></a>使用 EdgeOptions 类

创建 实例`EdgeOptions`，从而提供设置特定于Microsoft Edge的便利方法。  配置对象后 `EdgeOptions` ，请传递到 `EdgeOptions` 构造函数 `EdgeDriver` 中。

```csharp
var options = new EdgeOptions();
options.AddExtensions("/path/to/extension.crx");
var driver = new EdgeDriver(options);
```

若要使用没有关联的便利方法的功能，请使用 `AddAdditionalCapability` 方法。  您必须传递功能的完整名称和正确类型的值。  有关接受的功能和值类型的完整列表，请参阅 [EdgeOptions 对象](#edgeoptions-object)。

```csharp
options.AddAdditionalCapability("wdpAddress", "remotehost:50080");
```


<!-- ====================================================================== -->
## <a name="recognized-capabilities"></a>可识别的功能

有关接受的标准功能 `EdgeDriver` ，请参阅 [Selenium 文档](https://www.selenium.dev/documentation/en/driver_idiosyncrasies/shared_capabilities/) 和 [W3C WebDriver 标准](https://www.w3.org/TR/webdriver#capabilities)。  本文仅列出了特定于 Microsoft Edge。


<!-- ====================================================================== -->
## <a name="edgeoptions-object"></a>EdgeOptions 对象

大多数Microsoft Edge特定功能都通过 对象`EdgeOptions`公开。  在某些语言中，这些功能由 类 `EdgeOptions` 实现。  在其他语言中，这些功能存储在 中的字典 `ms:edgeOptions` 下 `DesiredCapabilities`。

| 功能 | 类型 | 详细信息 |
|:--- |:--- |:--- |
| `args` | 字符串列表 | 要传递给启动时要传递给 Microsoft Edge参数的列表。 具有关联值的参数应用 `=` 符号分隔 (例如，) `['start-maximized', 'user-data-dir=/tmp/temp_profile']` 。 如果你要启动 WebView2 应用，则这些参数将传递到你的应用，而不是基础Microsoft Edge进程。 若要在启动 WebView2 应用时将参数传递到浏览器进程，请改为使用 [webviewOptions.additionalBrowserArguments](#webviewoptions-object) 。 |
| `binary` | 字符串 | 在 macOS Microsoft Edge二进制文件 (路径，路径应为实际二进制文件，而不只是应用。  例如，) `/Applications/Microsoft Edge.app/Contents/MacOS/Microsoft Edge` 。 |
| `debuggerAddress` | 字符串 | 要连接到的调试器服务器的地址 `hostname/ip:port`，格式为 ，例如 `127.0.0.1:38947`。 |
| `detach` | 布尔型 | 默认值 = `false`。 如果`false`为 ，Microsoft Edge WebDriver 服务关闭时退出，即使 WebDriver 本地端尚未关闭会话。  如果`true`为 ，Microsoft Edge仅在 WebDriver 本地端关闭会话时退出。  如果 `true`为 ，并且 WebDriver `EdgeDriver` 本地端不关闭会话，则不清理网站实例使用的临时用户Microsoft Edge文件夹。 |
| `excludeSwitches` | 字符串列表 | 默认情况下，Microsoft Edge开关以排除该 EdgeDriver 的列表，该列表在启动 Microsoft Edge。  避免使用 `--` 开关前缀。 |
| `extensions` | 字符串列表 | 启动时要安装的扩展的列表。  列表中的每个项目应为 Base64 编码的打包扩展 () `.crx` 。 |
| `localState` | 字典 | 包含每个条目的字典，包含首选项的名称和值。  首选项将应用于用户数据文件夹中的本地状态文件。 |
| `minidumpPath` | 字符串 | 用于存储最小Microsoft Edge的目录。   (Linux.)  |
| `mobileEmulation` | 字典 | 值为 的字典， `deviceName`或和 `deviceMetrics` 的值 `userAgent`。 |
| `perfLoggingPrefs` | 字典 | 指定性能日志记录首选项的可选字典。  有关详细信息，请参阅 [perfLoggingPrefs 对象](#perfloggingprefs-object)。 |
| `prefs` | 字典 | 包含每个条目的字典，包含首选项的名称和值。  首选项仅适用于使用的用户配置文件。  例如，请参阅 Microsoft Edge `Preferences` 的用户数据文件夹中的文件。 |
| `wdpAddress` | 字符串 | 要连接到Windows门户服务器的地址，格式`hostname/ip:port`为 ，例如 `127.0.0.1:50080`。  有关详细信息，请参阅远程[调试 - Windows 10设备](../devtools-guide-chromium/remote-debugging/windows.md)。 |
| `wdpPassword` | 字符串 | 连接到 Device Portal 服务器时Windows可选密码。  如果服务器已启用身份验证，则必需。 |
| `wdpUsername` | 字符串 | 连接到 Device Portal 服务器时Windows的可选用户名。  如果服务器已启用身份验证，则必需。 |
| `webviewOptions` | 字典 | 可选字典，可用于在启动 WebView2 应用时配置 WebView2 环境。 有关详细信息，请参阅 [webviewOptions 对象](#webviewoptions-object)。 |
| `windowsApp` | 字符串 | 要启动的应用包Microsoft Edge模型 ID，例如 `Microsoft.MicrosoftEdge.Stable_8wekyb3d8bbwe!MSEDGE`。  使用 `windowsApp` Device `binary` Portal 连接到 Windows 10X 设备或仿真器Windows使用。 |
| `windowTypes` | 字符串列表 | 窗口句柄列表中显示的窗口类型列表。  若要访问 Android webview 元素，请包含 `webview` 到列表中。 |


<!-- ====================================================================== -->
## <a name="perfloggingprefs-object"></a>perfLoggingPrefs 对象

字典 `perfLoggingPrefs` 具有以下格式。 所有键都是可选的。

| 项 | 类型 | 默认值 | 详细信息 |
|:--- |:--- |:--- |:--- |
| `bufferUsageReportingInterval` | 正整数 | 1000 | DevTools 跟踪缓冲区使用事件之间请求的毫秒数。  例如，如果为 1000，则每秒一次，则 DevTools 报告跟踪缓冲区的已满。  如果报告指示缓冲区使用率为 100%，则发出警告。 |
| `enableNetwork` | 布尔型 | true | 收集 (或不从) 域收集事件。 |
| `enablePage` | 布尔型 | true | 收集 (或不从) 域收集事件。 |
| `traceCategories` | 字符串 |  (空)  | 一个逗号分隔Microsoft Edge跟踪类别的字符串，应收集跟踪事件。  未指定或空字符串禁用跟踪。 |


<!-- ====================================================================== -->
## <a name="webviewoptions-object"></a>webviewOptions 对象

该 `webviewOptions` 字典用于在启动 WebView2 应用时配置 WebView2 环境。 它具有以下格式。 所有键都是可选的。

| 项 | 类型 | 默认值 | 详细信息 |
|:--- |:--- |:--- |:--- |
| `browserExecutableFolder` | 字符串 |  (空)  | 包含要使用的固定版本的 WebView2 运行时的文件夹的路径。 有关将固定版本运行时分发与 WebView2 一同使用的信息，请参阅分发 [WebView2 应用和 WebView2 运行时](../webview2/concepts/distribution.md#the-fixed-version-runtime-distribution-mode)。 |
| `userDataFolder` | 字符串 |  (空)  | WebView2 将使用的用户数据文件夹的路径。 如果`userDataFolder`未指定，Microsoft Edge WebDriver 将创建一个临时用户数据文件夹。 有关使用 WebView2 管理用户数据文件夹的信息，请参阅 [管理用户数据文件夹](../webview2/concepts/user-data-folder.md)。 |
| `additionalBrowserArguments` | 字符串列表 |  | WebView2 将在启动时传递到浏览器进程的命令行参数列表。 具有关联值的参数应用 `=` 符号分隔 (例如，) `['start-maximized', 'log-level=0']` 。 |
| `releaseChannelPreference` | 字符串 |  | 首选的 WebView2 常青运行时分发使用。 可以是 或 `"stable"` `"canary"`。 |

<!-- ====================================================================== -->
## <a name="returned-capabilities"></a>返回的功能

以下列表包含创建新会话Microsoft Edge`EdgeDriver`返回的所有特定于会话的功能。

| 功能 | 类型 | 详细信息 |
|:--- |:--- |:--- |
| `msedge.msedgedriverVersion` | 字符串 | EdgeDriver 的版本。 |
| `msedge.userDataDir` | 字符串 | 用户数据文件夹的路径，该实例Microsoft Edge路径。 |
