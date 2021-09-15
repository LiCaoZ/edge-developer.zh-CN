---
description: 构建和发布 Microsoft Edge (Chromium) 扩展的概述。
title: Microsoft Edge扩展概述
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/25/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: edge， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员， chromium 扩展
ms.openlocfilehash: 50582ee10c0467c5e9cdb301daccba8e38a6ca9c
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976560"
---
# <a name="overview-of-microsoft-edge-extensions"></a>Microsoft Edge扩展概述

Microsoft Edge_扩展_是一个小程序， (开发人员) 添加或修改 Microsoft Edge (Chromium) 。  扩展旨在改善用户的日常浏览体验。  它提供了对目标受众很重要的功能。  

如果你有基于Microsoft Edge浏览器或特定网页功能的改进的想法或产品，可以创建一个扩展。  配套 _体验的示例包括_ 广告阻止者和密码管理器。

扩展的结构类似于常规 Web 应用。  扩展应至少包含以下功能：

*   包含基本平台信息的应用程序清单 JSON 文件。
*   定义功能的 JavaScript 文件。
*   定义用户界面的 HTML 和 CSS 文件。

若要直接使用部分浏览器（如窗口或选项卡），必须发送 API 请求，并且必须经常按名称引用浏览器。

:::image type="complex" source="./media/example-extension-screenshot.png" alt-text="Microsoft Edge (Chromium) 扩展" lightbox="./media/example-extension-screenshot.png":::
  Microsoft Edge (Chromium) 扩展
:::image-end:::


<!-- ====================================================================== -->
## <a name="basic-guidance"></a>基本指南

为一些最受欢迎的浏览器包括 Safari、Firefox、Chrome、Opera、Cookie 和 Microsoft Edge 构建扩展。  浏览器组织托管的网站是开始扩展开发教程和文档研究很好的位置。  下表并不明确，只是一个起点。

| Web 浏览器 | 基于 Chromium？ | 扩展开发网页 |  
|:--- |:--- |:--- |  
| Safari | 否 | [developer.apple.com/documentation/safariservices/safari_app_extensions][AppleDeveloperSafariservicesAppExtensions] |  
| Firefox | 否 | [developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions][MDNWebextensions] |  
| 镶边 | 是 | [developer.chrome.com/extensions][ChromeDeveloperExtensions] |  
| Opera | 是 | [dev.opera.com/extensions][OperaDevExtensions] |  
| 勇敢 | 是 | 使用 [Chrome Web Store][GoogleChromeWebstoreCategoryExtensions] |  
| 新 Microsoft Edge | 是 | [developer.microsoft.com/microsoft-edge/extensions][MicrosoftDeveloperEdgeExtensions] |  

> [!IMPORTANT]
> 许多网站的教程都使用与所开发浏览器不匹配的特定于浏览器的 API。  在大多数情况下，Chromium 扩展在不同 Chromium 浏览器中工作，且 API 按预期工作。  一些不太常见的 API 可能是特定于浏览器的。  有关教程的链接，请导航至“[另请参见](#see-also)”。  


<!-- ====================================================================== -->
## <a name="why-chromium"></a>为什么使用 Chromium？  

如果你的目标是在每个浏览器的扩展存储中发布扩展，则必须针对每个版本修改扩展，以在每个不同的浏览器环境中定位和运行扩展。  例如 [，Safari 扩展][AppleDeveloperSafariservicesAppExtensions] 可以使用 Web 和本机代码与对应的本机应用程序进行通信。  上表中的最后四个浏览器使用相同的代码包，并将维护并行版本的要求降到最低。  这些浏览器基于 [Chromium 开源项目][|::ref1::|Home]。  

创建 Chromium 扩展以编写最少的代码。  它还以扩展应用商店的最大数量以及最终以找到和获取扩展的最大用户数为目标。  

以下内容主要侧重于 Chromium 扩展。  


<!-- ====================================================================== -->
## <a name="browser-compatibility-and-extension-testing"></a>浏览器兼容性和扩展测试  

有时，Chromium 浏览器之间不存在 API 奇偶校验。  例如，标识和付款 API 存在差异。  若要确保您的扩展符合客户期望，请通过以下官方浏览器文档查看 API 状态：

*   [Chrome API][ChromeDeveloperExtensionsApiIndex]  
*   [Opera 支持的扩展 API][OperaDevExtensionsApis]  
*   [将 Chrome 扩展移植到 Microsoft Edge (Chromium)][ExtensionsChromiumDeveloperGuidePortChrome]  
    
您需要的 API 定义必须所做的更改以解决每个浏览器之间的差异。  你可能需要为每个应用商店创建略有不同的代码包，但略有不同。  

若要在将扩展提交到浏览器存储之前在不同环境中测试扩展，请开发扩展时将扩展旁加载到浏览器中。


<!-- ====================================================================== -->
## <a name="publish-your-extension-to-browser-stores"></a>将扩展发布到浏览器应用商店  

可以在以下浏览器商店中提交和查找浏览器扩展。  

*   [Firefox 浏览器加载项][MozillaAddonsFirefoxExtensions]  
*   [Chrome Web Store][GoogleChromeWebstoreCategoryExtensions]  
*   [Opera加载项][OperaAddonsExtensions]  
*   [Microsoft Edge 加载项][MicrosoftEdgeAddonsCategoryExtensions]  

某些商店允许你从其他浏览器下载列出的扩展。  但是，浏览器商店无法保证跨浏览器访问。  若要确保用户在不同的浏览器中找到扩展，应在每个浏览器扩展存储上维护一个列表。  

用户可能需要在不同的浏览器中安装扩展。 在此方案中，可以将现有 Chromium扩展从一个浏览器迁移到另一个浏览器。  

### <a name="migrate-an-existing-extension-to-microsoft-edge"></a>将现有扩展迁移到 Microsoft Edge  

如果你已针对另一个基于 Chromium 的浏览器开发扩展，你可以将其提交到Microsoft Edge加载项网站。 不需要重写扩展，并且必须验证它在 MicrosoftEdge 中是否工作。  将现有 Chromium 扩展迁移到其他 Chromium 浏览器时，请确保相同的 API 或替代项可用于目标浏览器。

有关将 Chrome 扩展移植到 Microsoft Edge 的更多信息，请导航到[将 Chrome 扩展移植到 Microsoft Edge (Chrome)][ExtensionsChromiumDeveloperGuidePortChrome]。 将扩展移植到目标浏览器后，下一步是发布它。  

### <a name="publish-to-the-microsoft-edge-add-ons-website"></a>发布到Microsoft Edge加载项网站

若要开始将扩展发布到 Microsoft Edge，必须使用 Microsoft 帐户[][MicrosoftDeveloperRegistration] (MSA) 电子邮件帐户注册开发人员帐户，以将扩展列表提交到应用商店。  MSA 帐户的 Microsoft (电子邮件地址 `@outlook.com`) 、或 `@live.com` "@hotmail.com"。  选择要注册的电子邮件地址时，请考虑是否必须与组织Microsoft Edge转移或共享该扩展的所有权。  注册完成后，你可以创建新的扩展提交到应用商店。

若要将扩展提交到应用商店，需要提供以下项：

*   包含代码文件的存档 \ (`.zip`\) 文件。  
*   所有必需的视觉资源，包括徽标和小型促销磁贴。  
*   可选促销媒体，如屏幕截图、促销贴片和视频 URL。  
*   描述扩展名的信息，如名称、简短描述和隐私策略链接。  

> [!NOTE]
> 不同的应用商店可能具有不同的提交要求。  上面的列表总结了发布 [Microsoft Edge][ExtensionsChromiumPublish] 扩展的要求。  

成功提交扩展后，扩展将经历审核过程，它将通过或不通过认证过程。  向所有者通知结果，并按需要提供下一步步骤。  如果向应用商店提交扩展更新，则会启动新的审阅过程。  


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅  

*   [移植 Google Chrome 扩展][ExtensionworkshopPorting]  
*   [构建 Safari 应用扩展][AppleDeveloperSafariservicesAppExtensionsBuilding]  
*   [第一个扩展 (Firefox)][MDNWebextensionsYourFirst]  
*   [入门教程 (Opera)][ChromeDeveloperExtensionsGetstarted]  
*   [入门 (Opera)][OperaDevExtensionsGettingStarted]  
*   [扩展概念和体系结构][ExtensionsChromiumGettingStartedIndex]  


<!-- ====================================================================== -->
<!-- links -->  
[ExtensionsChromiumDeveloperGuidePortChrome]: ./developer-guide/port-chrome-extension.md "将 Chrome 扩展移植到 Microsoft Edge (Chromium) |Microsoft Docs"  
[ExtensionsChromiumGettingStartedIndex]: ./getting-started/index.md "扩展概念和体系结构|Microsoft Docs"  
[ExtensionsChromiumPublish]: ./publish/publish-extension.md "发布Microsoft Edge扩展|Microsoft Docs"  

[MicrosoftDeveloperEdgeExtensions]: https://developer.microsoft.com/microsoft-edge/extensions "开发 Microsoft Edge |Microsoft 开发人员"  
[MicrosoftDeveloperRegistration]: https://developer.microsoft.com/registration "合作伙伴中心|Microsoft 开发人员"  

[MicrosoftEdgeAddonsCategoryExtensions]: https://microsoftedge.microsoft.com/addons/category/Edge-Extensions "Microsoft Edge |Microsoft Edge"  

[AppleDeveloperSafariservicesAppExtensions]: https://developer.apple.com/documentation/safariservices/safari_app_extensions "Safari 应用扩展|Apple 开发人员"  
[AppleDeveloperSafariservicesAppExtensionsBuilding]: https://developer.apple.com/documentation/safariservices/safari_app_extensions/building_a_safari_app_extension "生成 Safari 应用扩展|Apple 开发人员"  

[ChromeDeveloperExtensions]: https://developer.chrome.com/extensions "什么是扩展？|Chrome 开发人员"  
[ChromeDeveloperExtensionsApiIndex]: https://developer.chrome.com/extensions/api_index "Chrome API |Chrome 开发人员"  
[ChromeDeveloperExtensionsGetstarted]: https://developer.chrome.com/extensions/getstarted "入门教程|Chrome 开发人员"  

[ChromiumHome]: https://www.chromium.org/Home "Chromium"  

[ExtensionworkshopPorting]: https://extensionworkshop.com/documentation/develop/porting-a-google-chrome-extension "移植 Google Chrome 扩展|扩展研讨会"  

[GoogleChromeWebstoreCategoryExtensions]: https://chrome.google.com/webstore/category/extensions "扩展|Chrome Web Store"  

[MDNWebextensions]: https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions "浏览器扩展|MDN"  
[MDNWebextensionsYourFirst]: https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions/Your_first_WebExtension "你的第一个|MDN"  

[MozillaAddonsFirefoxExtensions]: https://addons.mozilla.org/firefox/extensions "扩展|Firefox 加载项"  

[OperaAddonsExtensions]: https://addons.opera.com/extensions "扩展|Opera Addons"  

[OperaDevExtensions]: https://dev.opera.com/extensions "扩展文档|Dev. Opera"  
[OperaDevExtensionsApis]: https://dev.opera.com/extensions/apis "操作方法支持扩展|Dev. Opera"  
[OperaDevExtensionsGettingStarted]: https://dev.opera.com/extensions/getting-started "入门 | Dev. Opera"  
