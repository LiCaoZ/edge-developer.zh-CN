---
title: 将渐进式 Web 应用发布到Microsoft Store
description: 通过在你的应用程序中 (PWA) 渐进式 Web 应用，使其Microsoft Store。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
ms.date: 12/03/2021
ms.openlocfilehash: ee49dfd1ac8274db3492fd5060012b2075997ac8
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12320219"
---
# <a name="publish-a-progressive-web-app-to-the-microsoft-store"></a>将渐进式 Web 应用发布到Microsoft Store

将渐进式 Web (PWA) 发布到[Microsoft Store具有下列](/windows/uwp/publish/index)优点：

| 优势 | 描述 |
|---|---|
| **可发现性** | 用户自然地在应用商店中查找应用。  当你发布到应用Microsoft Store，Windows数百万PWA发现你的Windows应用。  应用商店通过类别、已选择的集合等展示应用。  应用发现门户为应用的潜在用户提供轻松的浏览和购物体验。  你甚至可以 [使用屏幕截图、Hero](/windows/uwp/publish/app-screenshots-and-images) 图像和视频预告片增强应用商店一览。 |
| **Trustiness** | Windows客户知道他们可以信任他们的Microsoft Store购买和下载，因为他们遵守严格的 Microsoft[质量和安全标准](/legal/windows/agreements/store-policies)。 |
| **易于安装** | the Microsoft Store provides a consistent and user-friendly install experience across [all Windows 10 or later apps](https://www.microsoft.com/store/apps/windows). |
| **应用分析** | 合作伙伴[Windows](/windows/uwp/publish/index)仪表板可提供有关应用运行状况、使用情况等的详细[](/windows/uwp/publish/analytics)分析。 |

若要将PWA发布到Microsoft Store，无需更改代码。  相反，你可以创建应用预订、打包PWA，然后提交到应用商店。  以下各节将介绍这些步骤。


<!-- ====================================================================== -->
## <a name="create-an-app-reservation"></a>创建应用预订

[Windows中心](https://partner.microsoft.com/dashboard/windows/overview)是你将应用提交到应用中心Microsoft Store。

若要创建应用预订：

1.  显示已注册计划：
    1.  使用 Microsoft Windows登录到合作伙伴中心，然后转到合作伙伴[中心仪表板](https://partner.microsoft.com/dashboard/home)。
    1.  导航到**Windows & Xbox。**
        *   如果**Windows & Xbox，** 则应用已注册。
        *   如果未**Windows & Xbox，** 请选择"添加**程序"。**

    :::image type="content" source="../media/windows-partner-center-add-program.msft.png" alt-text="在合作伙伴中心仪表板Windows计划。":::

1.  若要注册开发人员计划：
    1.  导航到**Windows & Xbox。**
    1.  选择**开始使用**。
    1.  请按照提示操作。
1.  现在，你的帐户已注册应用开发人员计划。 若要创建应用预订：
    1.  导航到**Windows & Xbox。**
    1.  选择 **"**  >  **概述""新建应用"。**
    1.  在提示符中键入应用的名称。
    1.  选择 `Reserve product name`。

    :::image type="content" source="../media/windows-partner-center-create-app.msft.png" alt-text="在合作伙伴中心创建Windows预订。":::

1.  若要显示发布者详细信息，以在打包你的[PWA部分中使用](#package-your-pwa-for-the-store)**，请选择产品**管理  >  **产品标识**。

    :::image type="content" source="../media/windows-partner-center-publisher-info.msft.png" alt-text="从合作伙伴中心复制Windows发布者信息。" lightbox="../media/windows-partner-center-publisher-info.msft.png":::
    <!-- lightbox justified because large detailed image -->

1.  复制并保存以下值。
    *   **程序包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**


<!-- ====================================================================== -->
## <a name="package-your-pwa-for-the-store"></a>打包PWA应用商店

现在你已拥有应用发布信息，请为Windows生成一个应用包PWA。

若要生成应用包：

1.  转到["PWA生成器"。](https://www.pwabuilder.com)
1.  键入您网站的 URL PWA然后单击"开始 **"。**
1.  报告完成后，请确保你的PWA已准备就绪。 如果你的PWA分数太低，你可以访问清单选项和服务工作者选项并查看**** 需要工作的章节****。
1.  准备好发布PWA后，单击"下一步 **"，** 然后选择**** 发布页面的"Windows"**** 部分中的"应用商店程序包"按钮。
1.  粘贴以下值，这些值保存在"创建 [应用预订"部分](#create-an-app-reservation) ：
    *   **程序包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**

    :::image type="content" source="../media/pwabuilder-windows-package-options.png" alt-text="将发布者信息粘贴到 PWABuilder 中。":::

1.  选择"**生成"。**
1.  若要下载应用Windows程序包，请选择"下载 **"。**

下载的内容 `.zip` 是包含文件和 `.msixbundle` 文件的 `.classic.appxbundle` 存档。  这两个应用包PWA各种应用包上的Windows运行。  有关详细信息，请参阅[什么是经典程序包？。](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)


### <a name="submit-your-app-package-to-the-store"></a>将应用包提交到应用商店

若要将应用提交到Microsoft Store：

1.  转到Windows[中心](https://partner.microsoft.com/dashboard/windows/overview)
1.  选择你的应用。
1.  选择 **"开始提交"。**

    :::image type="content" source="../media/windows-partner-center-start-submission.msft.png" alt-text="在合作伙伴中心上开始Windows应用提交。":::

1.  系统提示时，提供有关应用的信息，如定价和年龄分级。

1.  在**程序包提示**符上，选择 你在打包你的程序包 `.msixbundle` 部分PWA `.classic.appxbundle` 文件。 [](#package-your-pwa-for-the-store)

完成提交后，通常会在 24 至 48 小时内查看你的应用。  收到批准后，PWA中将Microsoft Store。


<!-- ====================================================================== -->
## <a name="measure-usage-of-your-pwa-installed-from-the-microsoft-store"></a>测量从PWA安装的 Microsoft Store

初始PWA时，如果 PWA 从 Microsoft Store 安装，Microsoft Edge将以下标头与 Web 应用的第一个导航 `Referer` 请求一起提供。

```
Referer: app-info://platform/microsoft-store
```

使用此功能可测量与PWA安装的应用程序不同的Microsoft Store。  根据流量，你可以调整应用内容以改进用户体验。  客户端和服务器代码均可访问此功能。 若要在客户端访问此信息，可以在 `document.referrer` JavaScript 中查询。

此功能在 91 Microsoft Edge首次引入，DOM API 在 Microsoft Edge版本 93 中引入。


<!-- ====================================================================== -->
## <a name="redirect-to-locale-specific-domains-without-displaying-additional-ui"></a>重定向到特定于区域设置的域，而不显示其他 UI

默认情况下，PWA安装的应用程序在Microsoft Store重定向到特定于区域设置域时显示其他 UI。  添加的 UI 显示 URL 和页面标题。  添加此 UI 是因为导航到特定于区域设置域的域被视为"超出范围"。  但是，可以通过指定与项目关联的特定于区域设置的来源来阻止显示PWA。

下图显示了当用户移动到外部的 UI 作用域时引入PWA。 

:::image type="content" source="../media/locale-redirection-additional-ui.png" alt-text="当应用重定向到另一个域时，具有 URL 和页面标题的其他 UI。":::

### <a name="domain-redirection-with-browser-installed-pwas"></a>使用浏览器安装的 PWA 进行域重定向

Web 应用清单绑定到单个域。  但是，某些 PWA 为在全球特定地区的客户使用区域设置特定的域。  在 Web 浏览器中访问 PWA 时，客户会从主体域 (（例如 contoso.com) ）无缝转换为特定于区域设置域 (例如 contoso.co.ke) ，因为重定向发生在该网站的初始加载过程中。

因此，从PWA安装Microsoft Edge将安装PWA特定区域设置域中的域。  后续启动的 PWA直接转到特定于区域设置的域，而不是先转到主体域。

### <a name="domain-redirection-with-pwas-installed-from-the-microsoft-store"></a>域重定向（从服务器安装 PWA Microsoft Store

从服务器安装的 PWA Microsoft Store一个指向主体域的硬编码起始 URL。  启动 PWA 时，PWA最初导航到主体域，然后客户可能会 (将) 重定向到其区域设置特定的域。 如果发生该重定向，则认为该导航"超出范围"。  因此，应用会在页面顶部显示 URL 和页面标题。

显示 URL 和页面标题是一项安全功能，可确保用户知道他们已离开网站PWA。  当用户从网站上下文的另一个网站加载页面时，此添加的 UI PWA。  但是，当用户在同一网站的所有域之间移动时，添加的 UI 可能不合适。

### <a name="prevent-the-locale-specific-url-and-title-from-being-displayed"></a>阻止显示区域设置特定的 URL 和标题

若要防止其他 UI 显示在从 Microsoft Store 安装的 PWA 中，可以使用[URL](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md)处理程序使 PWA 能够跨越多个区域设置特定的域。

若要阻止显示 URL 和页面标题，

1. 在PWA Web 应用清单中，使用 成员指定[与 `url_handlers` ](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md#manifest-changes)该应用关联的源数组。
1. 在每个引用的源上，包括一[ `web-app-origin-association` 个](https://github.com/WICG/pwa-url-handler/blob/main/explainer.md#web-app-origin-association-file)将PWA域的文件。

当这些域列表就位时，Microsoft Edge重定向到区域设置特定的域时，系统将不再显示其他 UI。

最终， `url_handlers` 该功能将替换为 [`scope_extensions`](https://github.com/WICG/manifest-incubations/blob/gh-pages/scope_extensions-explainer.md) ，但该规范仍在开发中。  `scope_extensions` 将生成与 相同的结果 `url_handlers` 。

此功能是在版本 97 Microsoft Edge首次引入的。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [测试和提交你的PWA包](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/next-steps.md)
*   [将新PWA发布到应用商店](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/publish-new-app.md)
*   [将现有应用商店应用更新到PWA](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/update-existing-app.md)
*   [应用商店中 PBA 的图像建议](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/image-recommendations.md)
*   [应用打包解释器](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)
