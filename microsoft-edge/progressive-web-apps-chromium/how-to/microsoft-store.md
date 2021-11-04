---
description: 在PWA中发布，使你的Microsoft Store
title: 在应用程序中发布渐进式 Web Microsoft Store
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/09/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: 渐进 Web 应用、PWA、Edge、Windows、Microsoft Store
ms.openlocfilehash: 5ab67502780fde250bb400635ddc8665f4f0c2fd
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12156695"
---
# <a name="publish-your-progressive-web-app-to-the-microsoft-store"></a>将渐进式 Web 应用发布到Microsoft Store

将渐进式 Web (PWA) 发布到[Microsoft Store](/windows/uwp/publish/index)具有下列优点。

:::row:::
   :::column span="1":::
      **可发现性**
   :::column-end:::
   :::column span="2":::

      用户自然地在应用商店中查找应用。  当你发布到应用Microsoft Store，Windows数百万PWA发现你的Windows应用。  应用商店通过类别、已选择的集合等展示应用。  应用发现门户为应用的潜在用户提供轻松的浏览和购物体验。  你甚至可以 [使用屏幕截图、Hero](/windows/uwp/publish/app-screenshots-and-images) 图像和视频预告片增强应用商店一览。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      **Trustiness**
   :::column-end:::
   :::column span="2":::

      Windows客户知道他们可以信任他们的Microsoft Store购买和下载，因为他们遵守严格的 Microsoft[质量和安全标准](/legal/windows/agreements/store-policies)。
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      **易于安装**
   :::column-end:::
   :::column span="2":::
      the Microsoft Store provides a consistent and user-friendly install experience across [all Windows 10 or later apps](https://www.microsoft.com/store/apps/windows).
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      **应用分析**
   :::column-end:::
   :::column span="2":::
      合作伙伴[Windows](/windows/uwp/publish/index)仪表板提供了有关应用运行状况、使用情况等的详细分析[](/windows/uwp/publish/analytics)。
   :::column-end:::
:::row-end:::

若要将PWA发布到Microsoft Store，无需更改代码。  相反，你可以创建应用预订、打包你的PWA，然后提交到应用商店。  以下各节将介绍这些步骤。


<!-- ====================================================================== -->
## <a name="create-an-app-reservation"></a>创建应用预订

[Windows中心](https://partner.microsoft.com/dashboard/windows/overview)是你将应用提交到应用中心Microsoft Store。

若要创建应用预订：

1.  显示已注册计划：
    1.  使用 Microsoft Windows登录到合作伙伴中心，然后转到合作伙伴[中心仪表板](https://partner.microsoft.com/dashboard/home)。
    1.  导航到**Windows & Xbox。**
        *   如果**Windows & Xbox，** 则应用已注册。
        *   如果未**Windows & Xbox，** 请选择"添加**程序"。**

    :::image type="content" source="../media/windows-partner-center-add-program.msft.png" alt-text="在合作伙伴中心仪表板Windows计划。" lightbox="../media/windows-partner-center-add-program.msft.png":::

1.  若要注册开发人员计划：
    1.  导航到**Windows & Xbox。**
    1.  选择**开始使用**。
    1.  请按照提示操作。
1.  现在，你的帐户已注册应用开发人员计划。 若要创建应用预订：
    1.  导航到**Windows & Xbox。**
    1.  选择 **"**  >  **概述""新建应用"。**
    1.  在提示符中键入应用的名称。
    1.  选择 `Reserve product name`。


    :::image type="content" source="../media/windows-partner-center-create-app.msft.png" alt-text="在合作伙伴中心Windows应用预订。" lightbox="../media/windows-partner-center-create-app.msft.png":::

1.  若要显示发布者详细信息，以在程序包你的[PWA部分中，](#package-your-pwa-for-the-store)选择**产品**管理产品  >  **标识**。


    :::image type="content" source="../media/windows-partner-center-publisher-info.msft.png" alt-text="从合作伙伴中心复制Windows发布者信息。" lightbox="../media/windows-partner-center-publisher-info.msft.png":::

1.  复制并保存以下值。
    *   **程序包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**


<!-- ====================================================================== -->
## <a name="package-your-pwa-for-the-store"></a>打包PWA应用商店

现在你已拥有应用发布信息，请为Windows生成一个PWA。

若要生成应用包：

1.  转到["PWA生成器"。](https://www.pwabuilder.com)
1.  键入你的网站的 URL PWA然后单击"开始 **"。**
1.  报告完成后，请确保你的PWA已准备就绪。 如果你的PWA分数太低，你可以访问清单**选项**和服务工作者**选项**并查看需要工作的部分。
1.  当你的PWA准备好发布时，单击下一步，然后选择**** 发布页面的**Windows部分**中的**** 应用商店程序包按钮。
1.  粘贴以下值，这些值保存在"创建 [应用预订"部分](#create-an-app-reservation) ：
    *   **程序包 ID**
    *   **发布者 ID**
    *   **Publisher显示名称**

    :::image type="content" source="../media/pwabuilder-windows-package-options.png" alt-text="将发布者信息粘贴到 PWABuilder 中。" lightbox="../media/pwabuilder-windows-package-options.png":::

1.  选择"**生成"。**
1.  若要下载你的Windows程序包，**请选择下载。**

下载的内容 `.zip` 是包含文件和 `.msixbundle` 文件的 `.classic.appxbundle` 存档。  这两个应用包PWA各种应用包上的Windows运行。  有关详细信息，请参阅[什么是经典程序包？。](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)


### <a name="submit-your-app-package-to-the-store"></a>将应用包提交到应用商店

若要将应用提交到应用商店：

1.  转到[Windows中心](https://partner.microsoft.com/dashboard/windows/overview)
1.  选择你的应用。
1.  选择 **"开始提交"。**

    :::image type="content" source="../media/windows-partner-center-start-submission.msft.png" alt-text="在合作伙伴中心上开始Windows应用提交。" lightbox="../media/windows-partner-center-start-submission.msft.png":::

1.  当系统提示你时，提供有关你的应用的信息，例如定价和年龄分级。

1.  在**程序包提示**符上，选择 在打包你的程序包部分中生成的 和 `.msixbundle` `.classic.appxbundle` [PWA](#package-your-pwa-for-the-store)文件。

完成提交后，通常会在 24 至 48 小时内查看你的应用。  收到批准后，PWA中将Microsoft Store。


<!-- ====================================================================== -->
## <a name="measure-usage-of-your-store-installed-pwa"></a>测量应用商店安装的应用商店的使用情况PWA

初始PWA时，如果 PWA 从 Microsoft Store 安装，Microsoft Edge 将以下标头与 Web 应用的第一个导航请求一起 `Referer` 包含。

```
Referer: app-info://platform/microsoft-store
```

使用此功能测量与应用商店安装版本不同的PWA。  根据流量，你可以调整应用内容以改进用户体验。  客户端和服务器代码均可访问此功能。 若要在客户端访问此信息，可以在 `document.referrer` JavaScript 中查询。

此功能在 91 Microsoft Edge首次引入，DOM API 在 Microsoft Edge版本 93 中引入。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [测试和提交你的PWA包](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/next-steps.md)
*   [将新PWA发布到应用商店](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/publish-new-app.md)
*   [将现有应用商店应用更新到PWA](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/update-existing-app.md)
*   [应用商店中 PBA 的图像建议](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/image-recommendations.md)
*   [应用打包解释器](https://github.com/pwa-builder/pwabuilder-windows-chromium-docs/blob/master/classic-package.md)
