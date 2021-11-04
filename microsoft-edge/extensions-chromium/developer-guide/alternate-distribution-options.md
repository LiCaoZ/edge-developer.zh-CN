---
description: 了解如何使用不使用已验证存储的备用方法分发扩展
title: 分发扩展的备用方法
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/17/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: 491c6a1e632061fe75477b6bd4f7ef9e0b823e61
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12155470"
---
# <a name="alternate-extension-distribution-methods"></a>备用扩展分发方法

通常，扩展通过加载项Microsoft Edge分发。 在某些情况下，开发人员可能需要使用备用方法分发扩展。 例如：

1.  扩展与其他软件相关联，并且应该与捆绑软件的其余部分一起安装。
1.  网络管理员希望在整个组织中分发扩展。

未从边缘加载项存储加载的扩展称为外部安装的扩展。 以下列表提供了分发外部安装的扩展的替代方法。

*   请使用Windows注册表 (Windows注册表) 。
*   在 macOS 和 Linux (使用首选项 JSON) 。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

请确保在加载项网站中Microsoft Edge扩展，或打包文件，并确保其成功 `.crx` 安装在您的计算机上。  如果使用 安装 `.crx` 文件， `update_URL` 请确保可以导航到位于该 URL 的扩展名。

此外，请确保您拥有以下信息。

1.  文件的文件 `.crx` 路径或扩展 `update_URL` 名的 。
1.  扩展的版本。  版本信息在清单文件中提供，或Microsoft Edge `edge://extensions` 打包扩展后在 中提供。
1.  扩展的 ID。  ID 信息在加载打包扩展Microsoft Edge `edge://extensions` 位于 以下版本。

> [!NOTE]
> 以下示例使用 `1.0` 作为 版本 和 `aaaaaaaaaabbbbbbbbbbcccccccccc` 作为 ID。


<!-- ====================================================================== -->
## <a name="use-the-windows-registry-windows-only"></a>仅Windows注册表 (Windows注册表) 

若要使用注册表Windows扩展，请执行以下步骤。

1.  在注册表中查找或创建以下注册表项：
    *   32 位 `HKEY_LOCAL_MACHINE\Software\Microsoft\Edge\Extensions` Windows：。
    *   64 位 `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Edge\Extensions` Windows：。
1.  使用与扩展 ID 相同的名称在****"扩展"下创建新密钥或文件夹。 例如，创建名称为 的键 `aaaaaaaaaabbbbbbbbbbcccccccccc` 。
1.  在 **Extensions** 键中， `update_url` 创建 属性，将值设置为 `https://edge.microsoft.com/extensionwebstorebase/v1/crx` 。  `update_url`属性指向 `.crx` 加载项网站中扩展Microsoft Edge文件。

    ```json
    {
        "update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx"
    }
    ```

    > [!NOTE]
    > 如果要从客户端安装扩展Chrome Web Store，将 的值 `update_url` 设置为 `https://clients2.google.com/service/update2/crx` 。

1.  导航到 ，验证扩展Microsoft Edge中列出的 `edge://extensions` 扩展。


<!-- ====================================================================== -->
## <a name="use-a-preferences-json-file-macos-and-linux"></a>在 macOS 和 Linux (使用首选项 JSON) 

若要使用首选项 JSON 文件分发扩展名，请执行以下步骤。

1.  使用 Linux 时，请确保扩展文件在将安装扩展 `.crx` 的计算机中可用。 将 `.crx` 扩展文件复制到本地目录，或使用从计算机访问的网络共享。
1.  创建一个 JSON 文件，其中文件的名称与扩展名的 ID 相对应。 例如，使用文件名 创建 JSON 文件 `aaaaaaaaaabbbbbbbbbbcccccccccc.json` 。
1.  根据操作系统，将 JSON 文件保存到以下文件夹之一。
    *   **macOS**
        *   特定于用户： `~USERNAME/Library/Application Support/Microsoft Edge/External Extensions/`
        *   所有用户： `/Library/Application Support/Microsoft/Edge/External Extensions/`

        若要防止未经授权的用户为所有用户安装扩展，请确保扩展文件是只读的。 此外，请确保满足以下条件：

        *   路径中的每个目录都归用户根所有。
        *   路径中的每个目录都分配给 `admin` 或 `wheel` 组。
        *   路径中的每个目录都不可写入世界。
        *   路径还必须没有符号链接。

    *   **Linux**
        *   特定于用户： `~/.config/microsoft-edge/External Extensions/`
        *   所有用户： `/usr/share/microsoft-edge/extensions/`
1.  根据您的方案，将相应的代码复制到 JSON 文件。
    *   仅适用于 Linux。 如果从文件安装，则使用 和 指定位置和 `external_crx` 版本 `external_version` 。

        ```json
        {
            "external_crx": "/home/share/extension.crx",
            "external_version": "1.0"
        }
        ```

    *   适用于 macOS 和 Linux。 如果从 安装 `update_URL` ，则使用 指定更新 `external_update_url` URL。

        仅在 Linux 上从本地文件安装时，将以下代码复制到 JSON `.crx` 文件。

        ```json
        {
            "external_update_url": "http://myhost.com/mytestextension/updates.xml"
        }
        ```

    *  从 macOS 和 Linux 上的 Microsoft Edge 加载项网站安装时，将以下代码复制到 JSON 文件。

        ```json
        {
            "external_update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx"
        }
        ```

1.  若要为特定区域设置安装扩展，使用 列出受支持的区域设置 `supported_locale` 。  还可以指定父区域设置，为使用该父语言的所有语言区域设置安装扩展。 例如，使用父区域设置时，扩展将安装所有英语区域设置，如 、 `en` `en-US` `en-GB` 等。  当用户在浏览器中更改其区域设置时，将卸载外部安装的扩展。  若要为任何区域设置安装扩展，请勿使用 `supported_locales` 。

    ```json
    {
        "external_update_url": "https://edge.microsoft.com/extensionwebstorebase/v1/crx",
        "supported_locales": [ "en", "fr", "de" ]
    }
    ```

1.  导航到 ，验证扩展Microsoft Edge安装于 `edge://extensions` 中。


<!-- ====================================================================== -->
## <a name="update-and-uninstall-externally-installed-extensions"></a>更新和卸载外部安装的扩展

Microsoft Edge浏览器每次启动时扫描注册表中的元数据条目，并更改外部安装的扩展。

若要将扩展更新到新版本，请更新清单文件中的版本，然后在注册表中更新版本。

你可能需要卸载外部安装的扩展，这些扩展是作为以前安装在计算机中的软件捆绑包的一部分安装的。  若要卸载扩展，请删除首选项 JSON 文件，或者从注册表中删除项。



> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。  原始页面位于 [此处](https://developer.chrome.com/apps/external_extensions)。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
