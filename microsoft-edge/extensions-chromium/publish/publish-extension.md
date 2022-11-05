---
title: 发布 Microsoft Edge 扩展
description: 将 Microsoft Edge 扩展发布到 Microsoft Edge 加载项网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/03/2022
ms.openlocfilehash: e40583cd486e09d7b1a59a4c6d0a3f438a60f7ae
ms.sourcegitcommit: dd668d16163d750f0dd23fd3379dfac9b2382b99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2022
ms.locfileid: "12854787"
---
# <a name="publish-a-microsoft-edge-extension"></a>发布 Microsoft Edge 扩展

开发和测试 Microsoft Edge 扩展后，即可分发扩展。 使用 Microsoft Edge 加载项网站分发扩展。  若要为 Microsoft Edge 用户发布现有的 Chromium 扩展，请参阅[移植现有 Chromium 扩展](../developer-guide/port-chrome-extension.md)。

将扩展发布到 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home) ，以增加其访问范围并使其可供其他 Microsoft Edge 用户使用。  本文提供将扩展提交到 Microsoft Edge 加载项网站的过程。


<!-- ========================================================================== -->
## <a name="before-you-begin"></a>在开始之前

应准备好扩展的工作原型。  有关如何创建扩展的信息，请参阅 [扩展概念和体系结构](../getting-started/index.md)。

若要将扩展发布到 Microsoft Edge 加载项网站，请使用 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)上的活动开发人员帐户。  如果没有开发人员帐户，请创建新的开发人员帐户。  若要打开新的开发人员帐户并注册到Microsoft Edge 外接程序计划，请参阅[开发人员注册](create-dev-account.md)。

为扩展包创建 zip 文件。  扩展包必须包含以下文件：

*  扩展清单，指定详细信息，例如扩展的名称、简短说明、权限和默认语言。

*  扩展所需的图像和其他文件。

清单中的以下字段会自动包含在你的商店一览详细信息中。  这些字段在 **Microsoft Store 一览** 网页上是只读的。  本文稍后将介绍应用商店一览网页。  在将程序包上传到合作伙伴中心之前，请确保字段值与你在商店详细信息网页上的首选显示相匹配，如下所示。

在清单文件中，查看以下字段：

*  字段 `Name` ，用于填充商店详细信息网页上的 **显示名称** 。

*  字段 `Description` ，用于填充商店详细信息网页上的 **简短说明** 。<!--todo: confirm "description" vs "short description" in manifest vs. store page-->
   
   填写 `Description` 字段，以显式提供一个吸引人的说明，该说明将显示在扩展列表顶部。

   *  如果在扩展清单文件中包含 ， `short description` 该简短说明将显示在你的商店一览中。

   *  如果未在清单文件中包含 `short description` ，则会在应用商店一览中显示 的前几行 `Description` 。  建议提供 ， `short description`以避免在商店一览网页上重复内容。


<!-- ========================================================================== -->
## <a name="submit-your-extension-to-the-microsoft-edge-add-ons-website"></a>将扩展提交到 Microsoft Edge 加载项网站

若要将扩展提交到合作伙伴中心，请执行以下操作：

1. 开始新的提交。

1. 上传扩展包。

1. 提供可用性详细信息。

1. 为扩展选择“属性”。

1. 为扩展添加 Microsoft Store 一览详细信息。

1. 完成提交。

本文的其余部分详细介绍了这些步骤。


<!-- ========================================================================== -->
## <a name="step-1--start-a-new-submission"></a>步骤 1：开始新提交

转到[开发人员仪表板](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)，然后在 **“概述**”网页上选择“**创建新扩展**”。


<!-- ========================================================================== -->
## <a name="step-2--upload-the-extension-package"></a>步骤 2：上传扩展包

1. 转到 **“包”** 网页以上传扩展包的 zip 文件。

   一次只能上传一个包。 如果在“ **包** ”网页上上传包不成功，则会阻止提交。

1. 若要上传包，请将 zip 文件拖放到网页的“ **将包拖到此处 (.zip) ** ”部分。 或者，可以选择“ **浏览文件** ”以打开对话框以选择要上传的包。

   上传包后，将对其进行验证。 如果存在验证错误，请解决此问题，然后再次尝试上传程序包。

1. 验证成功后，查看扩展详细信息，然后选择“ **继续** ”以继续。  


<!-- ========================================================================== -->
## <a name="step-3--provide-availability-details"></a>步骤 3：提供可用性详细信息

在 **“可用性** ”网页上，输入有关扩展可用性的以下信息。

#### <a name="visibility"></a>可见性

选择以下可见性选项之一，以定义扩展是否可在 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)中发现。

*  `Public`  (默认) - 允许每个人通过搜索、浏览 Microsoft Edge 加载项网站或使用 Microsoft Edge 加载项网站上的扩展列表 URL 来发现你的扩展。  合作伙伴中心仪表板上的扩展 **概述** 网页上提供了列表 URL。

*  `Hidden` - 从 Microsoft Edge 加载项网站上的搜索结果或浏览中删除扩展。  若要在 Microsoft Edge 加载项网站中分发隐藏的扩展，必须与客户共享该扩展的列表 URL。

可以将扩展的可见性从 **“公共”** 更改为 **“隐藏**”。  在可见性设置为 **“公开** ”时安装了扩展的用户将保留对扩展的访问权限，并接收你通过 Microsoft Edge 加载项网站提供的任何更新。

#### <a name="markets"></a>市场

定义计划在其中提供扩展的特定市场。  市场的默认设置是所有市场，包括以后添加的任何未来市场。

1. 若要选择特定市场，请选择“ **更改市场**”。

1. 切换单个市场以排除每个市场，或选择“ **取消选择全部”** ，然后添加所选的单个市场。

   可以更改提供扩展的市场。 在用户市场中提供扩展时安装扩展的用户将保留对扩展的访问权限。 但是，用户无权访问提交到 Microsoft Edge 加载项网站的任何将来更新。

1. 单击“ **保存&继续** ”以继续转到 **“属性”** 部分。


<!-- ========================================================================== -->
## <a name="step-4-select-properties-for-your-extension"></a>步骤 4：为扩展选择“属性”

在 **“属性”** 网页上，输入以下信息以指定扩展的属性。  这些属性在 Microsoft Edge 加载项网站上向用户显示。

| 扩展属性名称 | 描述 |
|:--- |:--- |
| 类别 (必需)  | 最能描述扩展的类别。  在正确的类别中列出扩展可帮助用户轻松找到你的扩展并详细了解它。  |
| 需要)  (隐私策略要求 | 指示扩展是否访问、收集或传输任何个人信息。  如果选择“ **是** ”，但未提供 `Privacy policy URL`，则扩展可能会使认证步骤失败。 |
| 隐私策略 URL | 有效的隐私策略 URL，用于传达扩展如何遵循隐私法律和法规。  你负责确保扩展遵循隐私法律和法规。  如果扩展访问、传输或收集任何个人信息，你还负责提供隐私策略 URL。  若要确定扩展是否需要隐私策略，请参阅 [Microsoft Edge 开发人员协议](/legal/windows/agreements/app-developer-agreement) 和 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。 |
| 网站 URL | 提供有关扩展的其他信息的网页。  必须 `Website URL` 指向你自己的网站上的网页，而不是 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)中扩展的 Web 列表。  可帮助 `Website URL` 用户了解有关扩展、其功能以及任何其他相关信息的详细信息。 |
| 支持联系人详细信息 | 支持网页的 URL，或用于联系支持团队的电子邮件地址。 |
| 成熟内容 | 用于指定扩展是否包含成熟内容的复选框。  扩展分级有助于确定扩展目标受众的相应年龄组。  若要帮助确定扩展是否包含成熟内容，请参阅 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。 |

选择 **“保存&继续** ”以继续转到 **“应用商店一览** ”部分。

> [!IMPORTANT]
> 你在注册期间提交的开发人员/组织名称、网站 URL 和支持联系人详细信息将显示在 Microsoft Edge 加载项网站上的用户。


<!-- ========================================================================== -->
## <a name="step-5-add-store-listing-details-for-your-extension"></a>步骤 5：为扩展添加应用商店一览详细信息

以下部分中提供的信息将显示给在 Microsoft Edge 加载项网站上查看你的一览的用户。  即使某些字段是可选的，也应提供尽可能多的信息。  若要在存储中列出扩展，需要以下详细信息。

*   扩展包中每种语言**的说明**。 若要支持多种语言，可以使用国际化 API ([chrome.i18n](https://go.microsoft.com/fwlink/?linkid=2167478)) 。
*   **扩展包** 中每种语言的扩展存储徽标。

> [!NOTE]
> 对于扩展 zip 包中提到的至少一种语言，必须填写所需的最低应用商店一览详细信息。  若要在 Microsoft Edge 加载项网站上的商店一览中添加或删除语言，请使用 **Microsoft Edge 一览**网页上的 **“添加语言**”下拉列表。  此外，可以使用语言详细信息网页上的“ **重复功能** ”按钮将资产从一种语言复制到另一 **种语言** 。

| 语言详细信息属性名称 | 描述 |
|:--- |:--- |
| 显示名称 (必需)  | 在 `name` 扩展的清单文件中指定的扩展的 。  若要在提交后更改存储显示名称，可以更新清单文件中的名称，创建新的扩展包，然后重新加载它。  |
| 描述 (必需)  | 该 `description` 字段重点说明扩展的功能、用户应安装它的原因或用户需要了解的其他相关信息。  它应小于 10，000 个字符。  |
| 扩展存储徽标 (必需)  | 表示公司或 `extension logo` 纵横比为 1、建议大小为 300 x 300 像素的图像。  此外，可以使用“复制”按钮将资产从一种语言复制到所有其他语言。  上传语言徽标后，可在字段后面找到此按钮。  |
| 小型促销磁贴 (可选)  | 该 `Small promotional tile` 图像用于在存储区中的其他扩展旁边显示扩展。  图像的大小应为 440 x 280 像素。  此外，可以使用“复制”按钮将资产从一种语言复制到所有其他语言。  上传语言的促销磁贴后，将在字段后面找到该按钮。  |
| 大型促销磁贴 (可选)  | `Large promotion tiles` 用于 Microsoft Edge 加载项网站中更突出的功能扩展。  图像（如果已提交）对用户可见。  PNG 文件的大小必须为 1400 x 560 像素。  此外，可以使用“复制”按钮将资产从一种语言复制到所有其他语言。  上传语言的促销磁贴后，将在字段后面找到该按钮。  |
| 可选)  (屏幕截图 | 最多可以提交 10 `screenshots` 个，详细说明扩展的功能。  屏幕截图的大小必须为 640 x 480 像素或 1280 x 800 像素。  此外，可以使用“复制”按钮将资产从一种语言复制到所有其他语言。  上传至少一个用于语言的按钮后，会在字段后面找到。|
| YouTube 视频 URL (可选)  | 可以包含扩展的宣传性 YouTube 视频。  视频 `YouTube video URL` 显示在扩展的应用商店一览网页上。  |
| 所需的)  (简短说明 | 若要编辑 `short description`，必须更新扩展包的清单文件中的说明字段并重新加载它。  |
| 搜索词 (可选)  | `Search terms` 当用户在 Microsoft Edge 加载项网站中搜索时，这些字词或短语可帮助发现扩展。  搜索词不会向用户显示。  |

#### <a name="youtube-video-url-requirements"></a>YouTube 视频 URL 要求

确保视频满足以下要求。

*  验证 YouTube 视频的内容是否遵循 [Microsoft Edge 加载项网站开发人员策略](../store-policies/developer-policies.md)。

*  关闭视频上的广告。  有关详细信息，请参阅 [设置默认广告格式](https://support.google.com/youtube/answer/2531367?ref_topic=7072227) 和 [嵌入视频上的广告](https://support.google.com/youtube/answer/132596)。

*  为视频启用嵌入。  有关详细信息，请参阅 [嵌入视频&播放列表](https://support.google.com/youtube/answer/171780)。

若要提交视频的 YouTube 视频 URL，

1. 在 YouTube 上，找到要添加到商店一览网页的视频。

1. 在视频下，选择“ **共享** > **嵌入**”。

1. 复制显示的 HTML 代码。

1. 在应用商店一览详细信息网页上，将 HTML 代码粘贴到 `YouTube video URL` 字段中。


#### <a name="search-terms-requirements"></a>搜索词要求

搜索词必须满足以下要求：

*  输入搜索词最多可以使用 21 个单词。  无论是用作单个字词、短语还是这两者的组合，最多只能使用 21 个单词。

*  最多 7 个搜索词 (单个字词或短语) 。  每个搜索词的字符限制为 30 个字符。


<!-- ========================================================================== -->
## <a name="step-6-complete-your-submission"></a>步骤 6：完成提交

在 **“提交扩展”** 网页上，添加认证说明以帮助测试扩展。


#### <a name="notes-for-certification-optional"></a>认证 (可选) 的说明

提交扩展时，请使用 **认证说明** 网页向认证测试人员提供其他信息。  附加信息有助于确保正确测试扩展。  如果扩展未经过全面测试，则可能无法通过认证。

确保根据需要包括以下信息：

*   测试帐户的用户名和密码。

*   访问隐藏或锁定功能的步骤。

*   基于区域或其他用户设置的预期功能差异。

*   如果提交是现有扩展的更新，请包含有关对扩展所做的更改的信息。

*   测试人员必须了解的有关你的提交的任何其他信息。

提供信息后，选择“ **发布** ”，将扩展提交到 [Microsoft Edge 加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。  提交将继续执行认证步骤。  提交后，认证过程最多可能需要 7 个工作日。

提交通过认证后，将在 Microsoft Edge 加载项网站上发布扩展。  合作伙伴中心仪表板中扩展的状态将更改为 `In the Store`。


<!-- ========================================================================== -->
## <a name="support-for-issues"></a>对问题的支持

如果在提交或注册过程中遇到任何问题，请在 [扩展新支持请求](https://support.microsoft.com/supportrequestform/e7a381be-9c9a-fafb-ed76-262bc93fd9e4) 上提交支持票证，或发送电子邮件到 [ext_dev_support@microsoft.com](mailto:ext_dev_support@microsoft.com)。
