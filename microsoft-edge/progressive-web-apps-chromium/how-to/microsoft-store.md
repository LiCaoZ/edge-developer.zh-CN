---
title: 将渐进式 Web 应用发布到Microsoft Store
description: 通过在Microsoft Store中发布，使渐进式 Web 应用 (PWA) 更易于发现。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 12/03/2021
ms.openlocfilehash: 721b1b0d371bf3f0b5638d6a70b6f8aec8d20b10
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522439"
---
# <a name="publish-a-progressive-web-app-to-the-microsoft-store"></a>将渐进式 Web 应用发布到Microsoft Store

将渐进式 Web 应用 (PWA) 发布到[Microsoft Store](/windows/uwp/publish/index)具有以下优势：

| 优势 | 描述 |
|---|---|
| **可发现性** | 用户自然会在应用商店中查找应用。  发布到Microsoft Store时，数百万Windows用户可以与其他Windows应用一起发现PWA。  Microsoft Store通过类别、精选集合等展示应用。  应用发现门户为应用的潜在用户提供了轻松的浏览和购物体验。  甚至可以使用屏幕截图、英雄图像和视频预告片[增强Microsoft Store](/windows/uwp/publish/app-screenshots-and-images)列表。 |
| **诚信** | Windows客户知道他们可以信任他们的Microsoft Store购买和下载，因为他们遵守严格的 Microsoft [质量和安全标准](/legal/windows/agreements/store-policies)。 |
| **轻松安装** | Microsoft Store为[所有Windows 10或更高](https://www.microsoft.com/store/apps/windows)版本的应用提供一致且用户友好的安装体验。 |
| **应用分析** | [Windows合作伙伴中心仪表板](/windows/uwp/publish/index)提供有关应用运行状况、使用情况等[的详细分析](/windows/uwp/publish/analytics)。 |

若要将PWA发布到Microsoft Store，无需更改代码。  而是创建应用预留、打包PWA，并将包提交到Microsoft Store。  以下部分介绍了这些步骤。


<!-- ====================================================================== -->
## <a name="create-an-app-reservation"></a>创建应用预留

[Windows合作伙伴中心](https://partner.microsoft.com/dashboard/windows/overview)是将应用提交到Microsoft Store的中心。

若要创建应用预留，请执行以下操作：

1.  若要显示已注册的程序，请执行以下操作：
    1.  使用 Microsoft 帐户登录到Windows合作伙伴中心，然后转到[合作伙伴中心仪表板](https://partner.microsoft.com/dashboard/home)。
    1.  导航到**Windows & Xbox**。
        *   如果显示**Windows & Xbox**，则应用已注册。
        *   如果未显示**Windows & Xbox**，请选择 **“添加程序**”。

    :::image type="content" source="../media/windows-partner-center-add-program.msft.png" alt-text="在Windows合作伙伴中心仪表板中添加程序。":::

1.  若要注册开发人员计划，请执行以下操作：
    1.  导航到**Windows & Xbox**。
    1.  选择**开始使用**。
    1.  请按照提示操作。
1.  现在，你的帐户已注册到应用开发人员计划中。 若要创建应用预留，请执行以下操作：
    1.  导航到**Windows & Xbox**。
    1.  选择 **“概述** > **创建新应用**”。
    1.  在提示中键入应用的名称。
    1.  选择 `Reserve product name`。

    :::image type="content" source="../media/windows-partner-center-create-app.msft.png" alt-text="在合作伙伴中心Windows创建应用预留。":::

1.  若要显示发布者详细信息，以便在[“打包PWA](#package-your-pwa-for-the-store)”部分中使用，请选择 **“产品管理** > **产品标识**”。

    :::image type="content" source="../media/windows-partner-center-publisher-info.msft.png" alt-text="从合作伙伴中心Windows复制发布者信息。" lightbox="../media/windows-partner-center-publisher-info.msft.png":::
    <!-- lightbox justified because large detailed image -->

1.  复制并保存以下值。
    *   **包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**


<!-- ====================================================================== -->
## <a name="package-your-pwa-for-the-store"></a>为Microsoft Store打包PWA

获取应用发布信息后，为PWA生成Windows应用包。

若要生成应用包，请执行以下操作：

1.  转到[PWA生成器](https://www.pwabuilder.com)。
1.  键入PWA的 URL，然后单击 **"开始"菜单**。
1.  报表完成后，请确保PWA已准备就绪。 如果PWA分数太低，可以访问**清单选项**和**服务辅助角色选项**，并查看需要工作的部分。
1.  当PWA准备发布时，单击 **“下一步**”，然后在发布页面**的Windows**部分中选择“**Microsoft Store包**”按钮。
1.  粘贴在 [“创建应用预留](#create-an-app-reservation) ”部分中保存的以下值：
    *   **包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**

    :::image type="content" source="../media/pwabuilder-windows-package-options.png" alt-text="将发布者信息粘贴到 PWABuilder 中。":::

1.  选择 **“生成**”。
1.  若要下载Windows应用包，请选择 **“下载**”。

下载是包含`.zip``.msixbundle`文件和文件的`.classic.appxbundle`存档。  这两个应用包允许PWA在各种Windows版本上运行。  有关详细信息，请参阅[什么是经典包？](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)<!-- changing master to main doesn't work 5/19/2022 -->


### <a name="submit-your-app-package-to-the-store"></a>将应用包提交到Microsoft Store

若要将应用提交到Microsoft Store：

1.  转到[Windows合作伙伴中心](https://partner.microsoft.com/dashboard/windows/overview)
1.  选择应用。
1.  **选择提交"开始"菜单**。

    :::image type="content" source="../media/windows-partner-center-start-submission.msft.png" alt-text="&quot;开始&quot;菜单合作伙伴中心Windows新应用提交。":::

1.  系统提示时，请提供有关应用的信息，例如定价和年龄分级。

1.  在 **“包**”提示符下，选择`.msixbundle`“[打包”部分](#package-your-pwa-for-the-store)中生成的文件和`.classic.appxbundle`PWA文件。

完成提交后，通常会在 24 到 48 小时内查看应用。  获得批准后，PWA可在Microsoft Store中使用。


<!-- ====================================================================== -->
## <a name="measure-usage-of-your-pwa-installed-from-the-microsoft-store"></a>测量从Microsoft Store安装的PWA的使用情况

最初启动PWA时，如果从Microsoft Store安装PWA，Microsoft Edge包含以下`Referer`标头，其中包含 Web 应用的第一个导航请求。

```
Referer: app-info://platform/microsoft-store
```

使用此功能可以测量从Microsoft Store安装的PWA的不同流量。  可以根据流量调整应用的内容，以改善用户体验。  客户端和服务器代码都可以访问此功能。 若要在客户端访问此信息，可以在 JavaScript 中进行查询 `document.referrer` 。

Microsoft Edge版本 91 中首次引入了此功能，DOM API 是在版本 93 Microsoft Edge引入的。


<!-- ====================================================================== -->
## <a name="redirect-to-locale-specific-domains-without-displaying-additional-ui"></a>重定向到特定于区域设置的域，而不显示其他 UI

默认情况下，从Microsoft Store安装的PWA在应用重定向到特定于区域设置的域时会显示其他 UI。  添加的 UI 显示 URL 和页面标题。  添加此 UI 是因为导航到特定于区域设置的域被视为“超出范围”。  但是，可以通过指定与PWA关联的特定于区域设置的源来阻止显示此 UI。

下图显示了当用户移出PWA范围时引入的 UI。 

:::image type="content" source="../media/locale-redirection-additional-ui.png" alt-text="当应用重定向到另一个域时，具有 URL 和页面标题的其他 UI。":::

### <a name="domain-redirection-with-browser-installed-pwas"></a>使用浏览器安装的 PVA 进行域重定向

Web 应用清单绑定到单个域。  但是，某些 PVA 为其客户在全球特定区域使用特定于区域设置的域。  在 Web 浏览器中访问PWA时，客户会从主体域 (无缝过渡，例如，contoso.com) 到特定于区域设置的域 (contoso.co.ke) ，因为重定向发生在该网站的初始加载过程中。

因此，从Microsoft Edge安装PWA的客户将从特定于区域设置的域安装PWA。  后续启动的PWA直接转到特定于区域设置的域，而不是先转到主体域。

### <a name="domain-redirection-with-pwas-installed-from-the-microsoft-store"></a>使用从Microsoft Store安装的 PVA 的域重定向

从Microsoft Store安装的 PVA 具有指向主体域的硬编码起始 URL。  启动PWA时，PWA最初会导航到主体域，然后客户可能会根据需要 () 重定向到其特定于区域设置的域。 如果发生重定向，则导航被视为“超出范围”。  因此，应用会在页面顶部显示 URL 和页面标题。

显示 URL 和页面标题是一项安全功能，可确保用户知道他们已离开PWA的上下文。  当用户在PWA上下文中从另一个网站加载页面时，这增加了 UI。  但是，当用户在同一网站的域之间移动时，添加的 UI 可能不合适。

### <a name="prevent-the-locale-specific-url-and-title-from-being-displayed"></a>防止显示特定于区域设置的 URL 和标题

若要防止在从Microsoft Store安装的PWA中显示其他 UI，可以使用 [URL 处理程序](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md)使PWA跨多个特定于区域设置的域。

若要防止显示 URL 和页面标题，请执行以下操作：

1. 在PWA的 Web 应用清单中，使用[该`url_handlers`成员](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md#manifest-changes)指定与该应用关联的源数组。
1. 在每个引用的源上，包括一个[`web-app-origin-association`将](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md#web-app-origin-association-file)PWA与该域相关联的文件。

当这些域列表就位时，当主体域重定向到特定于区域设置的域时，Microsoft Edge将不再显示其他 UI。

最终， `url_handlers` 该功能将被替换 [`scope_extensions`](https://github.com/WICG/manifest-incubations/blob/gh-pages/scope_extensions-explainer.md)，但该规格仍在开发中。  `scope_extensions` 将产生相同的结果 `url_handlers`。

此功能首次在 Microsoft Edge 版本 97 中引入。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [测试并提交PWA应用包](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/next-steps.md)
*   [将新PWA发布到Microsoft Store](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/publish-new-app.md)
*   [将现有Microsoft Store应用更新到PWA](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/update-existing-app.md)
*   [Microsoft Store中 PVA 的图像建议](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/image-recommendations.md)
*   [应用打包解释器](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)
