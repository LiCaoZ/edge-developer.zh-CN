---
title: 分发扩展的替代方法
description: 如何使用不使用已验证存储的备用方法分发扩展。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: 9db8986381f976915349baebe3dcaac1b349e594
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631605"
---
# <a name="alternative-ways-to-distribute-extensions"></a>分发扩展的替代方法

通常，扩展是通过 Microsoft Edge 加载项网站分发的。 在某些情况下，开发人员可能需要使用备用方法分发扩展。 例如：

1. 该扩展与其他软件相关联，应与其他捆绑软件一起安装。

1. 网络管理员希望在整个组织中分发扩展。

未从 Edge 加载项存储加载的扩展称为外部安装的扩展。 以下是分配外部安装的扩展的备用方法：

*  仅使用 Windows 注册表 () 。
*  在 macOS 和 Linux)  (使用首选项 JSON 文件。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

请确保在 Microsoft Edge 加载项网站中发布扩展名，或打包 `.crx` 文件，并确保它在计算机上成功安装。  如果使用`update_URL`该 `.crx` URL 安装文件，请确保可以转到该 URL 处的扩展名。

此外，请确保具有以下信息：

*  文件的文件路径或`update_URL`扩展名的文件路径`.crx`。

*  扩展的版本。  版本信息在清单文件中或在加载打包扩展名后在 Microsoft Edge `edge://extensions` 中可用。

*  扩展的 ID。  加载打包的扩展后，Microsoft Edge `edge://extensions` 中提供了 ID 信息。

以下示例用作 `1.0` 版本和 `aaaaaaaaaabbbbbbbbbbcccccccccc` ID。


<!-- ====================================================================== -->
## <a name="use-the-windows-registry-windows-only"></a>仅使用 Windows 注册表 (Windows) 

若要使用 Windows 注册表分发扩展，请执行以下操作：

1. 在注册表中查找或创建以下密钥：
   *  32 位 Windows：  `HKEY_LOCAL_MACHINE\Software\Microsoft\Edge\Extensions`.
   *  64 位 Windows：  `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Edge\Extensions`.

1. 在 **扩展名下** 创建与扩展 ID 相同的新密钥或文件夹。 例如，使用名称 `aaaaaaaaaabbbbbbbbbbcccccccccc`创建密钥。

1. 在 **Extensions** 键中，创建属性 `update_url` 并将值设置为 `https://edge.microsoft.com/extensionwebstorebase/v1/crx`。  该 `update_url` 属性指向 `.crx` Microsoft Edge 加载项网站中的扩展文件。

   ```json
   {
       "update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx"
   }
   ```

   > [!NOTE]
   > 如果要从 Chrome Web Store 安装扩展，请将该扩展的 `update_url` 值设置为 `https://clients2.google.com/service/update2/crx`。

1. 转到 `edge://extensions`Microsoft Edge，验证你的扩展是否已列出。


<!-- ====================================================================== -->
## <a name="use-a-preferences-json-file-macos-and-linux"></a>使用首选项 JSON 文件 (macOS 和 Linux) 

若要使用首选项 JSON 文件分发扩展名：

1. 使用 Linux 时，请确保 `.crx` 扩展文件在安装扩展的计算机上可用。 将 `.crx` 扩展文件复制到本地目录，或使用可从计算机访问的网络共享。

1. 创建一个 JSON 文件，其中文件的名称对应于扩展名的 ID。 例如，使用文件名 `aaaaaaaaaabbbbbbbbbbcccccccccc.json`创建 JSON 文件。

1. 根据操作系统，将 JSON 文件保存到以下文件夹之一：

    *  **macOS**
        *  用户特定： `~USERNAME/Library/Application Support/Microsoft Edge/External Extensions/`
        *  对于所有用户： `/Library/Application Support/Microsoft/Edge/External Extensions/`

        若要防止未经授权的用户为所有用户安装扩展插件，请确保扩展文件是只读的。

        另请确保满足以下条件：

        *  路径中的每个目录都归用户根所有。
        *  路径中的每个目录都分配给 `admin` 该或 `wheel` 组。
        *  路径中的每个目录都无法写入世界。
        *  路径还必须没有符号链接。

    *  **Linux**
        *  用户特定： `~/.config/microsoft-edge/External Extensions/`
        *  对于所有用户： `/usr/share/microsoft-edge/extensions/`

1. 根据方案，将下面的相应代码复制到 JSON 文件中。

    *  仅适用于 Linux。  如果从文件安装，请指定其中的位置和版本 `external_crx` ，并 `external_version`：

        ```json
        {
            "external_crx": "/home/share/extension.crx",
            "external_version": "1.0"
        }
        ```

    *  适用于 macOS 和 Linux。  如果从其中 `update_URL`安装，请在 `external_update_url`其中指定更新 URL。

       仅从 Linux 上的本地 `.crx` 文件安装时，将以下代码复制到 JSON 文件中：

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

1. 若要安装特定区域设置的扩展，请在 `supported_locales`其中列出支持的区域设置。

   可以指定父区域设置，以便为使用该父级的所有语言区域设置安装扩展。  例如，使用父区域设置 `en`时，扩展将安装所有英语区域设置，例如 `en-US`， `en-GB`等等。  当用户在其浏览器中更改其区域设置时，将卸载外部安装的扩展。  若要为 _任何_ 区域设置安装扩展，请勿使用 `supported_locales`。

    ```json
    {
        "external_update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx",
        "supported_locales": [ "en", "fr", "de" ]
    }
    ```

1. 转到 `edge://extensions`Microsoft Edge，验证你的扩展是否已安装。


<!-- ====================================================================== -->
## <a name="update-and-uninstall-externally-installed-extensions"></a>更新和卸载外部安装的扩展

每次浏览器启动时，Microsoft Edge 都会扫描注册表中的元数据条目，并对其外部安装的扩展进行任何更改。

若要将扩展名更新为新版本，请更新清单文件中的版本，然后更新注册表中的版本。

可能需要卸载外部安装的扩展，这些扩展作为以前安装在计算机上的软件捆绑包的一部分安装。  若要卸载扩展，请删除首选项 JSON 文件或从注册表中删除密钥。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。  此 [处找到原始](https://developer.chrome.com/apps/external_extensions)页面。

[![知识共享许可协议。](../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
