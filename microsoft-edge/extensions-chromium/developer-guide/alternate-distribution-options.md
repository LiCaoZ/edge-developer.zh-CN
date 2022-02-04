---
title: 分发扩展的替代方法
description: 如何使用不使用已验证存储的备用方法分发扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
---
# <a name="alternative-ways-to-distribute-extensions"></a>分发扩展的替代方法

通常，通过加载项网站Microsoft Edge分发扩展。 在某些情况下，开发人员可能需要使用备用方法分发扩展。 例如：

1. 扩展与其他软件相关联，并且应该与捆绑软件的其余部分一起安装。

1. 网络管理员希望在整个组织中分发扩展。

未从边缘加载项存储加载的扩展称为外部安装的扩展。 下面是分发外部安装的扩展的备用方法：

*  请使用Windows注册表 (Windows注册表) 。
*  在 macOS 和 Linux (使用首选项 JSON) 。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

请确保在加载项网站`.crx`中发布扩展Microsoft Edge或打包文件，并确保其成功安装在您的计算机上。  如果使用 安装文件 `.crx` ， `update_URL`请确保可以转到该 URL 的扩展名。

此外，请确保你拥有以下信息：

*  文件的文件路径 `.crx` 或扩展 `update_URL` 名的 。

*  扩展的版本。  版本信息在清单文件中提供，`edge://extensions`或Microsoft Edge打包扩展后在 中提供。

*  扩展的 ID。  ID 信息在加载打包扩展Microsoft Edge`edge://extensions`位于 以下版本。

以下示例使用 作为 `1.0` 版本 和 `aaaaaaaaaabbbbbbbbbbcccccccccc` 作为 ID。


<!-- ====================================================================== -->
## <a name="use-the-windows-registry-windows-only"></a>仅Windows注册表 (Windows注册表) 

若要使用注册表Windows扩展：

1. 在注册表中查找或创建以下注册表项：
   *  32 位Windows：`HKEY_LOCAL_MACHINE\Software\Microsoft\Edge\Extensions`。
   *  64 位Windows：`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Edge\Extensions`。

1. 使用与扩展 ID 相同的名称在 **"** 扩展"下创建新密钥或文件夹。 例如，创建名称为 的键 `aaaaaaaaaabbbbbbbbbbcccccccccc`。

1. 在 **Extensions** 键中，创建 `update_url` 属性，将值设置为 `https://edge.microsoft.com/extensionwebstorebase/v1/crx`。  属性`update_url`指向加载项`.crx`网站中扩展Microsoft Edge文件。

   ```json
   {
       "update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx"
   }
   ```

   > [!NOTE]
   > 如果要从客户端安装扩展Chrome Web Store，将 的值`update_url`设置为 `https://clients2.google.com/service/update2/crx`。

1. 通过进入 验证扩展Microsoft Edge中列出`edge://extensions`。


<!-- ====================================================================== -->
## <a name="use-a-preferences-json-file-macos-and-linux"></a>将首选项 JSON 文件 (macOS 和 Linux) 

若要使用首选项 JSON 文件分发扩展，请：

1. 使用 Linux 时，请确保扩展 `.crx` 文件在将安装扩展的计算机中可用。 `.crx`将扩展文件复制到本地目录，或使用从计算机访问的网络共享。

1. 创建一个 JSON 文件，其中文件的名称与扩展名的 ID 相对应。 例如，使用文件名 创建 JSON 文件 `aaaaaaaaaabbbbbbbbbbcccccccccc.json`。

1. 根据操作系统的不同，将 JSON 文件保存到以下文件夹之一：

    *  **macOS**
        *  特定于用户： `~USERNAME/Library/Application Support/Microsoft Edge/External Extensions/`
        *  对于所有用户： `/Library/Application Support/Microsoft/Edge/External Extensions/`

        若要防止未经授权的用户为所有用户安装扩展，请确保扩展文件是只读的。

        此外，请确保满足以下条件：

        *  路径中的每个目录都归用户根所有。
        *  路径中的每个目录都分配给 或 `admin` `wheel` 组。
        *  路径中的每个目录都不可写入世界。
        *  路径还必须没有符号链接。

    *  **Linux**
        *  特定于用户： `~/.config/microsoft-edge/External Extensions/`
        *  对于所有用户： `/usr/share/microsoft-edge/extensions/`

1. 根据您的方案，将以下相应代码复制到 JSON 文件中。

    *  仅适用于 Linux。  如果从文件安装，请指定 和 中的位置和 `external_crx` 版本 `external_version`：

        ```json
        {
            "external_crx": "/home/share/extension.crx",
            "external_version": "1.0"
        }
        ```

    *  适用于 macOS 和 Linux。  如果从 安装， `update_URL`请指定 中的更新 URL `external_update_url`。

       仅在 Linux 上从本地文件安装时， `.crx` 将以下代码复制到 JSON 文件中：

       ```json
       {
           "external_update_url": "http://myhost.com/mytestextension/updates.xml"
       }
       ```

    *  从 macOS 和 Linux 上的 Microsoft Edge 加载项网站安装时，将以下代码复制到 JSON 文件：

       ```json
       {
           "external_update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx"
       }
       ```

1. 若要为特定区域设置安装扩展，在 中列出受支持的区域设置 `supported_locales`。

   可以指定父区域设置，为使用该父区域设置的所有语言区域设置安装扩展。  例如，使用父区域设置时`en`，扩展将安装所有英语区域`en-US``en-GB`设置，如 、 等。  当用户在浏览器中更改其区域设置时，将卸载外部安装的扩展。  若要为任何区域 _设置安装_ 扩展，请勿使用 `supported_locales`。

    ```json
    {
        "external_update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx",
        "supported_locales": [ "en", "fr", "de" ]
    }
    ```

1. 通过进入 验证扩展Microsoft Edge安装。`edge://extensions`


<!-- ====================================================================== -->
## <a name="update-and-uninstall-externally-installed-extensions"></a>更新和卸载外部安装的扩展

Microsoft Edge浏览器每次启动时扫描注册表中的元数据条目，并更改外部安装的扩展。

若要将扩展更新到新版本，请更新清单文件中的版本，然后在注册表中更新版本。

你可能需要卸载外部安装的扩展，这些扩展是作为以前安装在计算机中的软件捆绑包的一部分安装的。  若要卸载扩展，请删除首选项 JSON 文件，或者从注册表中删除项。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。  原始页面位于 [此处](https://developer.chrome.com/apps/external_extensions)。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
