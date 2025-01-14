---
title: Microsoft Edge 扩展概述
description: 构建和发布 Microsoft Edge 扩展的概述。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/25/2021
ms.openlocfilehash: c919e9dfb0587725589373976df1780ca32f4bd0
ms.sourcegitcommit: 627ac3e3d4404d9701c81a81609dc49de7c28add
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2022
ms.locfileid: "12552498"
---
# <a name="overview-of-microsoft-edge-extensions"></a>Microsoft Edge 扩展概述

Microsoft Edge *扩展* 是开发人员用于添加或修改 Microsoft Edge 功能的小程序。  扩展可改善用户的浏览体验。  它通常提供对目标受众很重要的基函数。

如果你的想法或产品基于特定 Web 浏览器或特定网页功能的改进，则可以创建 Microsoft Edge 扩展。  *配套体验* 的示例包括广告拦截器和密码管理器。

扩展的结构类似于常规 Web 应用。  扩展应至少包含以下功能:

*   包含基本平台信息的应用程序清单 JSON 文件。
*   定义该函数的 JavaScript 文件。
*   定义用户界面的 HTML 和 CSS 文件。

若要直接使用部分浏览器 (如窗口或选项卡)，必须发送 API 请求并通常按名称引用浏览器。

![Microsoft Edge扩展。](./media/example-extension-screenshot.png)


<!-- ====================================================================== -->
## <a name="basic-guidance"></a>基本指南

为一些最受欢迎的浏览器包括 Safari、Firefox、Chrome、Opera、Cookie 和 Microsoft Edge 构建扩展。  浏览器组织托管的网站是开始扩展开发教程和文档研究很好的位置。  下表并非详尽或明确。 这只是研究的起点。

| Web 浏览器 | 基于 Chromium？ | 扩展开发网页 |
|:--- |:--- |:--- |
| Safari | 否 | [Safari 应用扩展](https://developer.apple.com/documentation/safariservices/safari_app_extensions) |
| Firefox | 否 | [浏览器扩展](https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions) |
| Chrome | 是 | [API 参考](https://developer.chrome.com/extensions) |
| Opera | 是 | [扩展文档](https://dev.opera.com/extensions) |
| 勇敢 | 是 | 使用 [Chrome Web Store](https://chrome.google.com/webstore/category/extensions) |
| Microsoft Edge | 是 | [Microsoft Edge加载项开发人员](https://developer.microsoft.com/microsoft-edge/extensions) |

> [!IMPORTANT]
> 许多网站教程使用的浏览器特定的 API 可能与为其开发的浏览器不匹配。  在大多数情况下，Chromium 扩展在不同 Chromium 浏览器中工作，且 API 按预期工作。  某些不太常见的 API 可能特定于浏览器。  本教程的链接位于下面的 [“另请参阅](#see-also) ”部分中。


<!-- ====================================================================== -->
## <a name="why-chromium"></a>为什么使用 Chromium？

如果目标是在每个浏览器扩展应用商店中发布扩展，则扩展必须为每个版本对其进行修改，以便在不同浏览器环境中运行。  例如，[Safari 扩展](https://developer.apple.com/documentation/safariservices/safari_app_extensions) 可以同时使用 web 和本机代码与对应的本机应用通信。  上表中的最后四个浏览器使用相同的代码包，并最大限度地减少维护并行版本的需求。  这些浏览器基于 [Chromium 开源项目](https://www.chromium.org/Home)。

创建Chromium扩展的好处包括编写最少的代码行。  它还针对扩展存储的最大数量，并最终确定可以查找和获取扩展的最大用户数。

以下内容主要侧重于 Chromium 扩展。


<!-- ====================================================================== -->
## <a name="browser-compatibility-and-extension-testing"></a>浏览器兼容性和扩展测试

有时，Chromium 浏览器之间不存在 API 奇偶校验。  例如，标识和付款 API 存在差异。  为了确保扩展满足客户的期望，请通过以下官方浏览器文档查看 API 状态:

*   [Chrome API](https://developer.chrome.com/extensions/api_index)
*   [Opera 支持的扩展 API](https://dev.opera.com/extensions/apis)
*   [将 Chrome 扩展移植到 Microsoft Edge](developer-guide/port-chrome-extension.md)

所需 API 定义了为解决各浏览器之间差异而必须进行的更改。  你可能需要为每个应用商店创建略有差异的不同代码包。

若要在将扩展提交扩展到浏览器存储之前在不同环境中测试扩展，请在开发扩展时将其侧载到浏览器中。


<!-- ====================================================================== -->
## <a name="publish-your-extension-to-browser-stores"></a>将扩展发布到浏览器应用商店

可以在以下浏览器存储中提交和查找浏览器扩展。

*   [Firefox 浏览器加载项](https://addons.mozilla.org/firefox/extensions)
*   [Chrome Web Store](https://chrome.google.com/webstore/category/extensions)
*   [Opera加载项](https://addons.opera.com/extensions)
*   [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/category/Edge-Extensions)

某些商店允许你从其他浏览器下载列出的扩展。  但是，浏览器存储不保证跨浏览器访问。  为了确保你的用户可在不同的浏览器中找到扩展，应该在每个浏览器扩展商店上维护一个列表。

用户可能需要在不同的浏览器中安装扩展。 在这种情况下，可以将现有的 Chromium 扩展从一个浏览器迁移到另一个浏览器。

### <a name="migrate-an-existing-extension-to-microsoft-edge"></a>将现有扩展迁移到 Microsoft Edge

如果已经为另一个基于Chromium的浏览器开发了扩展，则可以将其提交到[Microsoft Edge加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。 无需重写扩展或验证它是否在Microsoft Edge中工作。  将现有的 Chromium 扩展迁移到其他 Chromium 浏览器时，请确保相同的 API 或替代方案可用于该目标浏览器。

有关将 Chrome 扩展移植到Microsoft Edge的详细信息，请参阅[端口 Chrome 扩展以Microsoft Edge](developer-guide/port-chrome-extension.md)。 将扩展移植到目标浏览器后，下一步是发布它。

### <a name="publish-to-the-microsoft-edge-add-ons-website"></a>发布到 Microsoft Edge 外接程序网站

若要开始将扩展发布到 Microsoft Edge，必须 [使用 Microsoft account (MSA) 电子邮件帐户注册开发人员帐户](https://developer.microsoft.com/registration)，才能将扩展列表提交到商店。  Microsoft 帐户 (MSA) 的电子邮件地址包括 `@outlook.com`、`@live.com` 或 `@hotmail.com`。  选择电子邮件地址进行注册时，请考虑是否必须将 Microsoft Edge 扩展的所有权转让或与组织中的其他人共享。  注册完成后，可以向应用商店创建新的扩展提交。

若要向应用商店提交扩展，你需要提供以下项目:

*   包含代码文件的存档 (`.zip`) 文件。
*   所有必需的视觉资源，包括徽标和小型促销磁贴。
*   可选促销媒体，如屏幕截图、促销贴片和视频 URL。
*   描述扩展名的信息，如名称、简短描述和隐私策略链接。

> [!NOTE]
> 不同的应用商店可能具有不同的提交要求。  上面的列表总结了发布 [Microsoft Edge](publish/publish-extension.md) 扩展的要求。

成功提交扩展后，扩展将经历审核过程，它将通过或不通过认证过程。  向所有者通知结果，并按需要提供下一步步骤。  如果将扩展更新提交到应用商店，它将开始新的审阅过程。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [扩展概念和体系结构](getting-started/index.md)
*  [在企业中管理 Microsoft Edge 扩展](/deployedge/microsoft-edge-manage-extensions)

外部链接:
*  [移植 Google Chrome 扩展](https://extensionworkshop.com/documentation/develop/porting-a-google-chrome-extension)
*  [构建 Safari 应用扩展](https://developer.apple.com/documentation/safariservices/safari_app_extensions/building_a_safari_app_extension)
*  [第一个扩展 (Firefox)](https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions/Your_first_WebExtension)
*  [入门教程 (Chrome)](https://developer.chrome.com/extensions/getstarted)
*  [入门 (Opera)](https://dev.opera.com/extensions/getting-started)

用于 Visual Studio Code 而不是用于 Microsoft Edge 的扩展:
*  [用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](../visual-studio-code/microsoft-edge-devtools-extension.md)
*  [适用于Visual Studio Code的 webhint 扩展](../visual-studio-code/webhint.md)
