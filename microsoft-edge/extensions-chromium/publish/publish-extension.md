---
title: 发布 Microsoft Edge 扩展
description: 将 Microsoft Edge 扩展发布到 Microsoft Edge 加载项网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/25/2021
ms.openlocfilehash: 25ea0dd9b620bd42b7bf0f39f50d1ac6ad807b59
ms.sourcegitcommit: 108b9a0673be978d89bc99d923582f569a43f6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2022
ms.locfileid: "12635358"
---
# <a name="publish-a-microsoft-edge-extension"></a>发布 Microsoft Edge 扩展

开发并测试 Microsoft Edge 扩展后，即可分发扩展。 使用 Microsoft Edge 加载项网站分发扩展。  若要为 Microsoft Edge 用户发布现有Chromium扩展，请参阅[移植现有的Chromium扩展](../developer-guide/port-chrome-extension.md)。

将扩展发布到 [Microsoft Edge 加载项网站，](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home) 以增加其覆盖范围，并使其可供其他 Microsoft Edge 用户使用。  本文提供将扩展提交到 Microsoft Edge 加载项网站的过程。


<!-- ========================================================================== -->
## <a name="before-you-begin"></a>在开始之前

应准备好扩展的工作原型。  有关如何创建扩展的信息，请参阅 [扩展概念和体系结构](../getting-started/index.md)。

若要将扩展发布到 Microsoft Edge 加载项网站，请在 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)使用你的活动开发人员帐户。  如果没有开发人员帐户，请创建新的开发人员帐户。  若要打开新的开发人员帐户并注册到Microsoft Edge 外接程序计划，请参阅[开发人员注册](create-dev-account.md)。

创建一个代表扩展包的 zip 文件。  扩展包必须包含以下文件：

*  指定扩展名称、简短说明、权限和默认语言等详细信息的扩展清单。

*  扩展所需的图像和其他文件。

清单中的以下字段将自动包含在应用商店列表详细信息中。  这些字段在 **应用商店列表** 网页上是只读的。  本文稍后将介绍应用商店列表网页。  将包上传到合作伙伴中心之前，请确保字段值与商店详细信息网页上的首选显示匹配，如下所示。

在清单文件中，查看以下字段：

*  在 `Name` 存储详细信息网页上填充 **显示名称** 的字段。

*  该 `Description` 字段填充存储详细信息网页上的 **Short 说明** 。<!--todo: confirm "description" vs "short description" in manifest vs. store page-->
   
   填写字 `Description` 段，以显式提供将显示在扩展列表顶部的吸引人的说明。

   *  如果在扩展清单文件中包含一个 `short description` ，则该简短说明将显示在应用商店一览中。

   *  如果未在清单文件中包含清单 `short description` 文件，则会在应用商店列表中显示前几行 `Description` 。  我们建议提供一个 `short description`，以避免在应用商店列表网页上重复内容。


<!-- ========================================================================== -->
## <a name="submit-your-extension-to-the-microsoft-edge-add-ons-website"></a>将扩展提交到 Microsoft Edge 加载项网站

将扩展提交到合作伙伴中心：

1. 启动新提交。

1. 上传扩展包。

1. 提供可用性详细信息。

1. 选择扩展的属性。

1. 为扩展添加应用商店列表详细信息。

1. 完成提交。

本文的其余部分提供有关这些步骤的详细信息。


<!-- ========================================================================== -->
## <a name="step-1--start-a-new-submission"></a>步骤 1：启动新提交

转到[开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)，然后在 **“概述**”网页上选择 **“新建扩展**”。


<!-- ========================================================================== -->
## <a name="step-2--upload-the-extension-package"></a>步骤 2：上传扩展包

1. 转到 **包** 网页上传扩展包的 zip 文件。

   一次只能上传一个包。 如果包在 **包网页上** 传不成功，则会阻止提交。

1. 若要上传包，请将 zip 文件拖放到网页 **的“拖动包” (.zip“) ** ”部分。 或者，可以选择 **“浏览文件** ”以打开对话框以选择要上传的包。

   上传包后，将对其进行验证。 如果出现验证错误，请解决此问题，然后再次尝试上传包。

1. 验证成功后，查看扩展详细信息，然后选择 **“继续** ”继续。  


<!-- ========================================================================== -->
## <a name="step-3--provide-availability-details"></a>步骤 3：提供可用性详细信息

在 **可用性** 网页上，输入有关扩展可用性的以下信息。

### <a name="visibility"></a>可见性

选择以下可见性选项之一，以定义扩展是否可在 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)中发现。

*  `Public`  (默认) - 允许每个人通过搜索、在 Microsoft Edge 加载项网站中浏览或使用 Microsoft Edge 加载项网站中的扩展列表 URL 来发现你的扩展。  “扩展 **概述** ”网页上的合作伙伴中心仪表板上提供了列表 URL。

*  `Hidden` - 从搜索结果中删除扩展或在 Microsoft Edge 加载项网站中浏览。  若要在 Microsoft Edge 加载项网站中分发隐藏的扩展，必须与客户共享扩展的列表 URL。

可以将扩展的可见性从 **“公共** ”更改为 **“隐藏**”。  在将扩展设置为公共时安装扩展的用户将保留对扩展的访问权限，并接收通过 Microsoft Edge 加载项网站提供的任何更新。

### <a name="markets"></a>市场

定义计划提供扩展的特定市场。  市场的默认设置是所有市场，其中包括以后添加的任何未来市场。

1. 若要选择特定市场，请选择 **“更改市场**”。

1. 切换单个市场以排除每个市场或选择 **“全部取消选择** ”，然后添加所选的各个市场。

   可以更改提供扩展的市场。 在用户市场中安装扩展时安装扩展的用户将保留对扩展的访问权限。 但是，用户无法访问将来提交到 Microsoft Edge 加载项网站的任何更新。

1. 单击 **“保存&继续** 执行” **属性** “部分。


<!-- ========================================================================== -->
## <a name="step-4-select-properties-for-your-extension"></a>步骤 4：选择扩展的属性

在 **“属性** ”网页上，输入以下信息以指定扩展的属性。  这些属性在 Microsoft Edge 加载项网站上显示给用户。

| 扩展属性名称 | 描述 |
|:--- |:--- |
| 所需的类别 ()  | 最能描述扩展的类别。  在正确的类别中列出扩展可帮助用户轻松找到你的扩展并了解有关它的详细信息。  |
| 隐私策略要求 (所需的)  | 指示扩展是否访问、收集或传输任何个人信息。  如果选择 **“是** ”且未提供 `Privacy policy URL`认证步骤，则扩展可能会失败。 |
| 隐私策略 URL | 一个有效的隐私策略 URL，用于传达扩展如何遵循隐私法律和法规。  你负责确保你的扩展遵循隐私法律和法规。  如果扩展正在访问、传输或收集任何个人信息，你还负责提供隐私策略 URL。  若要确定扩展是否需要隐私策略，请参阅 [Microsoft Edge 开发人员协议](/legal/windows/agreements/app-developer-agreement) 和 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。 |
| 网站 URL | 提供有关扩展的其他信息的网页。  必须 `Website URL` 指向你自己的网站上的网页，而不是 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)中扩展的 Web 列表。  帮助 `Website URL` 用户详细了解扩展、其功能和任何其他相关信息。 |
| 支持联系人详细信息 | 支持网页的 URL，或要联系支持团队的电子邮件地址。 |
| 成熟内容 | 用于指定扩展是否包含成熟内容的复选框。  扩展分级有助于确定扩展目标受众的适当年龄组。  若要帮助确定扩展内容是否成熟，请参阅 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。 |

选择 **“保存&继续** 转到 **”应用商店一览** “部分。

> [!Important]
> 注册期间提交的开发人员/组织名称、网站 URL 和支持联系人详细信息将显示给 Microsoft Edge 加载项网站上的用户。


<!-- ========================================================================== -->
## <a name="step-5-add-store-listing-details-for-your-extension"></a>步骤 5：为扩展添加应用商店列表详细信息

以下部分中提供的信息将显示给在 Microsoft Edge 加载项网站上查看列表的用户。  即使某些字段是可选的，也应提供尽可能多的信息。  若要在存储中列出扩展，需要以下详细信息。

*   扩展包中每种语言的**说明**。 若要支持多种语言，可以使用国际化 API ([chrome.i18n](https://go.microsoft.com/fwlink/?linkid=2167478)) 。
*   扩展包中每种语言的**扩展存储徽标**。

> [!NOTE]
> 必须为扩展 zip 包中提到的至少一种语言填写所需的最低商店列表详细信息。  若要在 Microsoft Edge 加载项网站上的应用商店列表中添加或删除语言，请在**应用商店**列表网页上使用 **“添加语言**”下拉列表。  此外，可以使用“**语言详细信息**”网页上的 **“重复功能**”按钮，将资产从一种语言复制到其他语言。

| 语言详细信息属性名称 | 描述 |
|:--- |:--- |
| 所需 (显示名称)  | 扩展 `name` 的清单文件中指定的扩展名。  若要在提交后更改应用商店显示名称，可以更新清单文件中的名称，创建新的扩展包，然后重新加载它。  |
| 所需)  (说明 | 该 `description` 字段重点介绍扩展的功能、用户安装扩展的原因或用户需要了解的其他相关信息。  应小于 10，000 个字符。  |
| 扩展应用商店徽标 (所需的)  | 表示公司或 `extension logo` 纵横比为 1 且建议大小为 300 x 300 像素的图像。  此外，可以使用“重复”按钮将资产从一种语言复制到所有其他语言。  上传语言徽标后，会在字段后找到此按钮。  |
| 小型促销磁贴 (可选)  | 该 `Small promotional tile` 映像用于在应用商店中与其他扩展一起显示扩展。  图像的大小应为 440 x 280 像素。  此外，可以使用“重复”按钮将资产从一种语言复制到所有其他语言。  上传语言的促销磁贴后，会在字段后找到该按钮。  |
|  (可选) 的屏幕截图 | 最多可以提交 10 个 `screenshots` 详细描述扩展功能的内容。  屏幕截图的大小必须是 640 x 480 像素或 1280 x 800 像素。  此外，可以使用“重复”按钮将资产从一种语言复制到所有其他语言。  至少上传一个语言后，会在字段后找到该按钮。|
| 大型促销磁贴 (可选)  | `Large promotion tiles` 在 Microsoft Edge 加载项网站中，在应用商店中更突出地使用扩展功能。  图像（如果已提交）对用户可见。  PNG 文件的大小必须是 1400 x 560 像素。  此外，可以使用“重复”按钮将资产从一种语言复制到所有其他语言。  上传语言的促销磁贴后，会在字段后找到该按钮。  |
| YouTube 视频 URL (可选)  | 可以包含扩展的促销 YouTube 视频。  该 `YouTube video URL` 视频显示在扩展的应用商店列表网页上。  |
| 所需的简短说明 ()  | 若要编辑， `short description`必须更新扩展包清单文件中的说明字段并重新上传。  |
| 搜索词 (可选)  | `Search terms` 当用户在 Microsoft Edge 加载项网站中搜索时，可帮助发现扩展的单个单词或短语。  搜索词不会显示给用户。  |

### <a name="youtube-video-url-requirements"></a>YouTube 视频 URL 要求

确保视频满足以下要求。

*  验证 YouTube 视频的内容是否遵循 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。

*  关闭视频上的广告。  有关详细信息，请参阅在[嵌入的视频上](https://support.google.com/youtube/answer/132596)[设置默认广告格式](https://support.google.com/youtube/answer/2531367?ref_topic=7072227)和广告。

*  为视频启用嵌入。  有关详细信息，请参阅 [嵌入视频&播放列表](https://support.google.com/youtube/answer/171780)。

若要提交视频的 YouTube 视频 URL，请执行以下操作：

1. 在 YouTube 上，找到要添加到应用商店列表网页的视频。

1. 在视频下，选择 **“共享** > **嵌入**”。

1. 复制显示的 HTML 代码。

1. 在应用商店列表详细信息网页上，将 HTML 代码粘贴到字段中 `YouTube video URL` 。


### <a name="search-terms-requirements"></a>搜索词要求

搜索词必须满足以下要求：

*  可以输入搜索词，最多使用 21 个单词。  无论是用作单个单词、短语还是两者的组合，最多只能使用 21 个单词。

*  最多七个搜索词 (单个单词或短语) 。  每个搜索词的字符限制为 30 个字符。


<!-- ========================================================================== -->
## <a name="step-6-complete-your-submission"></a>步骤 6：完成提交

在 **“提交扩展** ”网页上，添加认证说明以帮助测试扩展。


### <a name="notes-for-certification-optional"></a>认证说明 (可选) 

提交扩展时，请使用 **“认证说明** ”网页向认证测试人员提供其他信息。  其他信息有助于确保正确测试扩展。  如果扩展未经过完全测试，则可能会失败认证。

请确保根据需要包含以下信息：

*   测试帐户的用户名和密码。

*   访问隐藏或锁定功能的步骤。

*   基于区域或其他用户设置的功能预期差异。

*   如果你的提交是对现有扩展的更新，请包括有关对扩展所做的更改的信息。

*   测试人员必须了解的有关提交的其他任何信息。

提供信息后，选择 **“发布** ”以将扩展提交到 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。  你的提交将转到认证步骤。  提交后，认证过程最多可能需要 7 个工作日。

提交通过认证后，你的扩展将发布在 Microsoft Edge 加载项网站上。  合作伙伴中心仪表板中的扩展状态更改为 `In the Store`。


<!-- ========================================================================== -->
## <a name="support-for-issues"></a>对问题的支持

如果在提交或注册过程中遇到任何问题，请在 [扩展新支持请求](https://support.microsoft.com/supportrequestform/e7a381be-9c9a-fafb-ed76-262bc93fd9e4) 上提交支持票证，或向 [ext_dev_support@microsoft.com](mailto:ext_dev_support@microsoft.com) 发送电子邮件。
