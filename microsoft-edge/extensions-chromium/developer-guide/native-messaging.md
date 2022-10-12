---
title: 本机消息传递
description: 若要与安装在用户设备上的本机 Win32 应用通信，扩展使用消息传递 API。  本机应用主机使用标准输入和标准输出发送和接收扩展消息。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/31/2021
ms.openlocfilehash: 44647f961fd1a921c2e8b17cfa549b7210954ce1
ms.sourcegitcommit: abf18b3d2ac43ff56ce0ab567db698351def791a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2022
ms.locfileid: "12772572"
---
# <a name="native-messaging"></a>本机消息传递

若要与安装在用户设备上的本机 Win32 应用通信，扩展使用消息传递 API。  本机应用主机使用标准输入和标准输出发送和接收扩展消息。

使用本机消息传送的扩展安装在 Microsoft Edge 中，类似于任何其他扩展。  但是，本机应用不由 Microsoft Edge 安装或管理。

若要获取扩展和本机应用主机，有两种不同的分发模型：

*  将扩展和主机打包在一起。  当用户安装包时，将同时安装扩展和主机。

*  或者，使用 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)安装扩展，扩展会提示用户安装主机。

若要创建扩展以使用本机应用主机发送和接收消息，请执行以下步骤。


<!-- ====================================================================== -->
## <a name="step-1---add-permissions-to-the-extension-manifest"></a>步骤 1 - 向扩展清单添加权限

将权 `nativeMessaging` 限添加到扩展名的 **manifest.json** 文件。

下面是一个 **manifest.json** 文件示例：

```json
{
    "name": "Native Messaging Example",
    "version": "1.0",
    "manifest_version": 3,
    "description": "Send a message to a native app.",
    "app": {
        "launch": {
            "local_path": "main.html"
        }
    },
    "icons": {
        "128": "icon-128.png"
    },
    "permissions": ["nativeMessaging"]
}
```


<!-- ====================================================================== -->
## <a name="step-2---create-your-native-messaging-host-manifest-file"></a>步骤 2 - 创建本机消息传送主机清单文件

本机应用必须提供本机消息传送主机清单文件。  清单文件包含以下信息：

*  本机消息传送主机运行时的路径。

*  与扩展的通信方法。

*  与之通信的允许扩展的列表。

浏览器读取和验证本机消息传送主机清单。  浏览器不安装或管理本机消息传送主机清单文件。

本机消息传送主机清单文件的示例：

```json
{
    "name": "com.my_company.my_app",
    "description": "My App",
    "path": "C:\\Program Files\\My App\\chrome_native_messaging_host.exe",
    "type": "stdio",
    "allowed_origins": [
        "chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/"
    ]
}
```

主机清单文件必须是包含以下密钥的有效 JSON 文件：

| 密钥 | 详细信息 |
| --- | --- |
| `name` | 指定本机消息传送主机的名称。  客户端将字符串传递给 `runtime.connectNative` 或 `runtime.sendNativeMessage`传递 。<br/>  该值只能包含小写字母数字字符、下划线和点。<br/> 该值不得以点开头或结尾，并且一个点不得后跟另一个点。 |
| `description` | 介绍应用。 |
| `path` | 指定本机消息传送主机二进制文件的路径。<br/> 在 Windows 设备上，可以使用包含清单文件的目录的相对路径。<br/>  在 macOS 和 Linux 上，路径必须是绝对的。<br/>  主机进程从当前目录设置为包含主机二进制文件的目录开始。  例如， (Windows) ，如果参数设置为 `C:\App\nm_host.exe`二进制文件，则使用当前目录 () `C:\App\` 启动二进制文件。 |
| `type` | 指定用于与本机消息传送主机通信的接口的类型。  该值指示 Microsoft Edge 使用 `stdin` 和 `stdout` 与主机通信。  唯一可接受的值是 `stdio`。 |
| `allowed_origins` | 指定有权访问本机消息传送主机的扩展列表。  若要启用应用来标识扩展并与之通信，请在本机消息传送主机清单文件中设置以下值：<br/> `"allowed_origins": ["chrome-extension://{microsoft_catalog_extension_id}"]`|

旁加载扩展以使用主机测试本机消息传送。  在开发期间旁加载扩展并检索 `microsoft_catalog_extension_id`：

1. 转到 `edge://extensions`，然后打开 **“开发人员模式** 切换”按钮。

1. 选择 **“卸包加载**”，然后选择要旁加载的扩展包。

1. 单击“确定”****。

1. 转到页面 `edge://extensions` 并验证扩展是否已列出。

1. 从 `microsoft_catalog_extension_id` 页面上的扩展列表) 复制 (ID 中的密钥。

准备好将扩展分发给用户后，请将扩展发布到 Microsoft Edge 加载项网站。  已发布的扩展的扩展 ID 可能与旁加载扩展时使用的 ID 不同。  如果 ID 已更改，请使用已发布的扩展名的 ID 更新 `allowed_origins` 主机清单文件。


<!-- ====================================================================== -->
## <a name="step-3---copy-the-native-messaging-host-manifest-file-to-your-system"></a>步骤 3 - 将本机消息传送主机清单文件复制到系统

最后一步是将本机消息传送主机清单文件复制到计算机，并确保正确配置清单文件。  若要确保清单文件放置在预期位置，请执行以下步骤。  位置因平台而异。

> [!NOTE]
> 确保对清单文件提供读取权限，并在主机运行时上运行权限。

### [<a name="windows"></a>Windows](#tab/windows/)

清单文件可能位于文件系统中的任意位置。  应用安装程序必须创建注册表项并将密钥的默认值设置为清单文件的完整路径。  以下位置是注册表项的示例：

```output
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Edge\NativeMessagingHosts\com.my_company.my_app

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Edge\NativeMessagingHosts\com.my_company.my_app
```

若要使用清单密钥将注册表项添加到目录，请执行以下任一操作：

*  在命令提示符下运行命令：

   ```shell
   REG ADD "HKCU\Software\Microsoft\Edge\NativeMessagingHosts\com.my_company.my_app" /ve /t REG_SZ /d "C:\path\to\nmh-manifest.json" /f
   ```

*  或者，创建一个 `.reg` 文件并运行它，如下所示：

    1. 将以下命令复制到 `.reg` 文件中：

        ```shell
        Windows Registry Editor Version 5.00
        [HKEY_CURRENT_USER\Software\Microsoft\Edge\NativeMessagingHosts\com.my_company.my_app]
        @="C:\\path\\to\\nmh-manifest.json"
        ```

    1. 运行文件 `.reg` 。  如果将创建 `.reg` 的文件作为批处理脚本的一部分运行，请确保使用管理员命令提示符运行它。

Microsoft Edge 查询 `HKEY_CURRENT_USER` 根密钥，后跟 `HKEY_LOCAL_MACHINE`。  在这两个密钥中，首先搜索 32 位注册表，然后搜索 64 位注册表以标识本机消息传送主机。  注册表项指定本机消息传送主机清单的位置。

如果 Microsoft Edge 的注册表项没有主机清单的位置，则Chromium和 Chrome 注册表位置将用作回退选项。

如果 Microsoft Edge 在以前列出的任何位置找到注册表项，则它不会查询以下代码片段中列出的位置。


注册表位置的搜索顺序为：

```output
HKEY_CURRENT_USER\SOFTWARE\WOW6432Node\Microsoft\Edge\NativeMessagingHosts\
HKEY_CURRENT_USER\SOFTWARE\WOW6432Node\Chromium\NativeMessagingHosts\
HKEY_CURRENT_USER\SOFTWARE\WOW6432Node\Google\Chrome\NativeMessagingHosts\
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Edge\NativeMessagingHosts\
HKEY_CURRENT_USER\SOFTWARE\Chromium\NativeMessagingHosts\
HKEY_CURRENT_USER\SOFTWARE\Google\Chrome\NativeMessagingHosts\

HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Edge\NativeMessagingHosts\
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Chromium\NativeMessagingHosts\
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Google\Chrome\NativeMessagingHosts\
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Edge\NativeMessagingHosts\
HKEY_LOCAL_MACHINE\SOFTWARE\Chromium\NativeMessagingHosts\
HKEY_LOCAL_MACHINE\SOFTWARE\Google\Chrome\NativeMessagingHosts\
```

> [!NOTE]
> 如果在 Microsoft Edge 加载项和 Chrome Webstore 上有扩展，则必须添加与主机清单文件中的 `allowed_origins` 两个存储对应的扩展 ID，因为只读取与找到的第一个注册表位置对应的主机清单。

### [<a name="macos"></a>macOS](#tab/macos/)

若要存储清单文件，请执行以下操作：

*  系统范围的本机消息传送主机（可供所有用户使用）存储在固定位置。  例如，清单文件必须存储在以下位置。

   ```bash
   /Library/Microsoft/Edge/NativeMessagingHosts/com.my_company.my_app.json
   ```

*  用户特定的本机消息传送主机（仅对当前用户可用）位于 `NativeMessagingHosts` 用户配置文件目录的子目录中。  例如，清单文件必须存储在以下位置。

   ```bash
   ~/Library/Application Support/Microsoft Edge {Channel_Name}/NativeMessagingHosts/com.my_company.my_app.json
   ```

   In `{Channel_Name}` `Microsoft Edge {Channel_Name}` 必须是以下值之一：

    * `Canary`
    * `Dev`
    * `Beta`

    使用稳定通道时， ` {Channel_Name}` 不是必需的。

### [<a name="linux"></a>Linux](#tab/linux/)

若要存储清单文件，请执行以下操作：

*  系统范围的本机消息传送主机（可供所有用户使用）存储在固定位置。  清单文件必须存储在以下位置：

   ```bash
   /etc/opt/edge/native-messaging-hosts
   ```

*  用户特定的本机消息传送主机（仅对当前用户可用）位于 `NativeMessagingHosts` 用户配置文件目录的子目录中。  清单文件必须存储在以下位置：

   ```bash
   ~/.config/microsoft-edge/NativeMessagingHosts
   ```

* * *


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 此 [处找到原始](https://developer.chrome.com/extensions/nativeMessaging)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
