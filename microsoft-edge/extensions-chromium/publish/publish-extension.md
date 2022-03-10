---
title: 发布Microsoft Edge扩展
description: 将Microsoft Edge扩展发布到 Microsoft Edge 加载项网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/25/2021
ms.openlocfilehash: 8bee33d5f8bc482b03c5f9dbcbe6d0cc6d682990
ms.sourcegitcommit: fa1b0662af7c59a37f96260e5aba1922343d1ae7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2022
ms.locfileid: "12437475"
---
# <a name="publish-a-microsoft-edge-extension"></a>发布Microsoft Edge扩展

开发和测试你的 Microsoft Edge 扩展后，你已准备好分发你的扩展。 使用Microsoft Edge加载项网站分发扩展。  若要为用户Chromium现有 Microsoft Edge 扩展，请参阅移植[现有 Chromium 扩展](../developer-guide/port-chrome-extension.md)。

将扩展发布到 [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)网站，以增加其范围，使其可供其他用户Microsoft Edge使用。  本文提供将扩展提交到 Microsoft Edge 加载项网站的过程。


<!-- ========================================================================== -->
## <a name="before-you-begin"></a>在开始之前

你应该已准备好扩展的工作原型。  若要了解如何创建扩展，请参阅扩展 [概念和体系结构](../getting-started/index.md)。

若要将扩展发布到 Microsoft Edge 加载项网站，请使用合作伙伴中心上的活动开发人员[帐户](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)。  如果你没有开发人员帐户，请创建新的开发人员帐户。  若要打开新的开发人员帐户并注册到 Microsoft Edge 外接程序 计划，请参阅开发人员[注册](create-dev-account.md)。

创建表示扩展包的 zip 文件。  扩展包必须包含以下文件：

*  指定扩展名、简短说明、权限和默认语言等详细信息的扩展清单。

*  扩展名所需的图像和其他文件。

清单中的以下字段将自动包含在应用商店一览详细信息中。  这些字段在"应用商店一览 **"网页上是只读** 的。  本文稍后将介绍应用商店一览网页。  在将程序包上载到合作伙伴中心之前，请确保字段值与应用商店详细信息网页上的首选显示相匹配，如下所示。

在清单文件中，查看以下字段：

*  字段 `Name` ，用于填充应用商店 **详细信息** 网页上的"显示名称"。

*  字段 `Description` ，用于填充应用商店 **详细信息网页上** 的"简短说明"。<!--todo: confirm "description" vs "short description" in manifest vs. store page-->
   
   填写字段 `Description` ，明确提供将在扩展列表顶部显示的捕获说明。

   *  如果扩展清单 `short description` 文件包含 ，该简短说明将显示在应用商店一览中。

   *  如果清单文件中不包含 `short description` `Description` ，则应用商店一览中会显示 的前几行。  我们建议提供 ， `short description`以避免在应用商店一览网页上重复内容。


<!-- ========================================================================== -->
## <a name="submit-your-extension-to-the-microsoft-edge-add-ons-website"></a>将扩展提交Microsoft Edge加载项网站

若要将扩展提交到合作伙伴中心：

1. 开始新的提交。

1. Upload扩展包。

1. 提供可用性详细信息。

1. 选择扩展的属性。

1. 添加扩展的应用商店一览详细信息。

1. 完成提交。

本文的其余部分提供有关这些步骤的详细信息。


<!-- ========================================================================== -->
## <a name="step-1--start-a-new-submission"></a>步骤 1：启动新提交

转到开发人员 [仪表板，](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) 然后在"概述 **"网页上** 选择"创建新 **扩展** "。


<!-- ========================================================================== -->
## <a name="step-2--upload-the-extension-package"></a>步骤 2：Upload扩展包

1. 转到程序包 **网页** 以上传扩展包的 zip 文件。

   一次只能上载一个程序包。 如果程序包上传在程序包网页上未成功，你的 **提交将被** 阻止。

1. 若要上传程序包，请将 zip 文件拖放到网页的"将程序包拖动到 **此处 (.zip **) "部分。 也可以选择" **浏览文件** "打开对话框，选择要上载的程序包。

   上传程序包后，将进行验证。 如果存在验证错误，请解决该问题，然后再次尝试上传程序包。

1. 验证成功后，查看扩展详细信息，然后选择" **继续** "继续。  


<!-- ========================================================================== -->
## <a name="step-3--provide-availability-details"></a>步骤 3：提供可用性详细信息

在 **可用性** 网页上，输入有关扩展可用性的以下信息。

### <a name="visibility"></a>可见性

选择以下可见性选项之一，定义你的扩展在加载项Microsoft Edge[中是否可发现](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。

*  `Public`  (默认) - 允许所有人通过搜索、浏览 Microsoft Edge 加载项网站或使用 Microsoft Edge 加载项网站中的扩展列表 URL 来发现扩展。  合作伙伴中心仪表板上的扩展概述网页中提供了**列表 URL。**

*  `Hidden` - 从搜索结果中或在加载项网站Microsoft Edge扩展。  若要在加载项网站中Microsoft Edge隐藏的扩展，必须与客户共享扩展列表 URL。

你可以将扩展的可见性从 **"公共"更改为****"隐藏"**。  当可见性设置为公共时安装扩展的用户将保留对扩展的访问权限，并接收你通过"加载项"Microsoft Edge提供的任何更新。

### <a name="markets"></a>市场

定义计划提供扩展的特定市场。  市场默认设置是所有市场，包括以后添加的任何未来市场。

1. 若要选择特定市场，请选择" **更改市场"**。

1. 切换个别市场以排除每个市场，或选择 **"取消全** 选"，然后添加你选择的个别市场。

   你可以更改提供扩展的市场。 在用户市场中提供扩展时安装扩展的用户将保留对扩展的访问权限。 但是，用户不能访问提交到加载项网站的任何Microsoft Edge更新。

1. 单击 **"&"** 继续"以继续"属性 **"** 部分。


<!-- ========================================================================== -->
## <a name="step-4-select-properties-for-your-extension"></a>步骤 4：选择扩展的属性

在 **"属性** "网页上，输入以下信息以指定扩展的属性。  这些属性在加载项网站上Microsoft Edge用户。

| 扩展属性名称 | 说明 |
|:--- |:--- |
| 需要 (类别)  | 最能描述扩展的类别。  在正确的类别中列出扩展可帮助用户轻松找到扩展并了解有关它的更多信息。  |
| 隐私策略要求 (要求)  | 指示您的扩展是否访问、收集或传输任何个人信息。  如果选择是，并且未提供 ，你的扩展可能无法**** 通过认证步骤`Privacy policy URL`。 |
| 隐私策略 URL | 用于传达扩展如何遵循隐私法律和法规的有效隐私策略 URL。  你负责确保你的扩展遵循隐私法律和法规。  如果你的扩展正在访问、传输或收集任何个人信息，你还负责提供隐私策略 URL。  若要确定扩展是否要求隐私策略，请参阅Microsoft Edge[开发人员](/legal/windows/agreements/app-developer-agreement)协议和Microsoft Edge[加载项网站开发人员策略](../store-policies/developer-policies.md)。 |
| 网站 URL | 提供有关扩展的其他信息的网页。  必须`Website URL`指向自己网站上的网页，而不是加载项网站中扩展Microsoft Edge [Web 列表](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。  帮助 `Website URL` 用户了解有关扩展、扩展功能以及任何其他相关信息的更多信息。 |
| 支持联系人详细信息 | 支持网页的 URL 或用于联系支持团队的电子邮件地址。 |
| 成熟内容 | 用于指定扩展是否包含成熟内容的复选框。  扩展分级可帮助确定扩展的目标受众的适当年龄组。  若要帮助确定扩展内容是否成熟，请参阅Microsoft Edge加载项[网站开发人员策略](../store-policies/developer-policies.md)。 |

选择 **"&** "继续"以继续浏览 **应用商店一览** 部分。

> [!Important]
> 你的开发人员/组织名称、网站 URL 和支持你在注册期间提交的联系人详细信息将显示在加载项Microsoft Edge用户。


<!-- ========================================================================== -->
## <a name="step-5-add-store-listing-details-for-your-extension"></a>步骤 5：为扩展添加应用商店一览详细信息

以下部分中提供的信息显示给在加载项网站上查看Microsoft Edge列表的用户。  尽管某些字段是可选的，但您应该提供尽可能多的信息。  若要在应用商店中列出扩展，需要以下详细信息。

*   **扩展** 包中每种语言的说明。 若要支持多种语言，可以使用 [chrome.i18n (的](https://go.microsoft.com/fwlink/?linkid=2167478) 国际化 API) 。
*   **扩展包中** 每种语言的扩展应用商店徽标。

> [!NOTE]
> 必须为扩展 zip 包中提到的至少一种语言填写所需的最低应用商店一览详细信息。  若要在加载项网站的应用商店一览中添加或删除Microsoft Edge，请使用"应用商店一览"网页上的"添加语言 **"** 下拉列表。****  此外，您可以使用"语言详细信息"网页上的"重复功能"按钮**** 将资产从一种语言复制到**另一**种语言。

| 语言详细信息属性名称 | 说明 |
|:--- |:--- |
| 显示名称 (必填)  | 在 `name` 扩展的清单文件中指定的扩展的 。  若要在提交显示名称应用商店，可以在清单文件中更新名称，创建新的扩展包，然后重新加载它。  |
| 说明 (必需)  | 该字段 `description` 重点介绍扩展执行哪些功能、为什么用户应安装它，或者用户需要知道的其他相关信息。  它应小于 10，000 个字符。  |
| 扩展存储徽标 (必需的)  | 表示你的公司或 `extension logo` 纵横比为 1、建议大小为 300 x 300 像素的图像。  此外，可以使用"复制"按钮将资源从一种语言复制到所有其他语言。  为语言上载徽标后，可以在字段后找到此按钮。  |
| 小促销磁贴 (可选)  | 该 `Small promotional tile` 图像用于将扩展与应用商店中其他扩展一起显示。  图像的大小应为 440 x 280 像素。  此外，可以使用"复制"按钮将资源从一种语言复制到所有其他语言。  在上传该语言的促销磁贴后，可以在字段后找到该按钮。  |
| 可选 (屏幕截图)  | 你最多可提交 10 `screenshots` 个描述扩展功能的详细信息。  屏幕截图的大小必须为 640 x 480 像素或 1280 x 800 像素。  此外，可以使用"复制"按钮将资源从一种语言复制到所有其他语言。  在上载至少一种语言后，可以在字段后找到该按钮。|
| 大型促销磁贴 (可选)  | `Large promotion tiles` 在应用商店中用来在加载项网站中更Microsoft Edge扩展。  图像（如果已提交）对用户可见。  PNG 文件的大小必须为 1400 x 560 像素。  此外，可以使用"复制"按钮将资源从一种语言复制到所有其他语言。  在上传该语言的促销磁贴后，可以在字段后找到该按钮。  |
| YouTube 视频 URL (可选)  | 你可以包含扩展的促销 YouTube 视频。  视频 `YouTube video URL` 显示在扩展的应用商店一览网页上。  |
| 简短说明 (必填)  | 若要编辑 `short description`，必须更新扩展包清单文件中的描述字段，然后重新上载它。  |
| 搜索词 (可选)  | `Search terms` 是一个字词或短语，当用户在加载项网站中搜索时Microsoft Edge扩展。  搜索词不会显示给用户。  |

### <a name="youtube-video-url-requirements"></a>YouTube 视频 URL 要求

确保您的视频满足以下要求。

*  验证 YouTube 视频的内容是否遵循Microsoft Edge[加载项网站开发人员策略](../store-policies/developer-policies.md)。

*  关闭视频上的广告。  有关详细信息，请参阅在 [嵌入式视频上](https://support.google.com/youtube/answer/2531367?ref_topic=7072227) 设置默认广告格式 [和广告](https://support.google.com/youtube/answer/132596)。

*  为视频启用嵌入。  有关详细信息，请参阅嵌入 [视频&播放列表](https://support.google.com/youtube/answer/171780)。

若要提交视频的 YouTube 视频 URL，

1. 在 YouTube 上，找到要添加到应用商店一览网页的视频。

1. 在视频下，选择 **"****ShareEmbed** > "。

1. 复制显示的 HTML 代码。

1. 在应用商店一览详细信息网页上，将 HTML 代码粘贴到 `YouTube video URL` 字段中。

### <a name="search-terms-requirements"></a>搜索词要求

搜索词必须满足以下要求：

*  输入搜索词最多可使用 21 个单词。  无论是用作单个单词、短语还是同时用作两者的组合，您最多只能使用 21 个单词。

*  最多七个搜索词：单个单词或短语。  每个搜索词的字符限制为 30 个字符。


<!-- ========================================================================== -->
## <a name="step-6-complete-your-submission"></a>步骤 6：完成提交

在 **"提交扩展"** 网页上，添加认证说明以帮助测试扩展。

### <a name="notes-for-certification-optional"></a>认证说明 (可选) 

提交扩展时，请使用认证 **网页** 的"说明"向认证测试人员提供其他信息。  其他信息有助于确保正确测试扩展。  如果你的扩展未经过完全测试，它可能无法通过认证。

必要时，请确保包含以下信息：

*   测试帐户的用户名和密码。

*   访问隐藏或锁定功能的步骤。

*   基于区域或其他用户设置的预期功能差异。

*   如果你的提交是对现有扩展的更新，请包含有关对扩展所做的更改的信息。

*   测试人员必须了解的有关你的提交的其他信息。

在提供该信息后，**选择"发布**"以将扩展Microsoft Edge[加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。  你的提交将继续执行认证步骤。  提交后，认证过程最多可能需要 7 个工作日。

提交通过认证后，你的扩展Microsoft Edge加载项网站中发布。  合作伙伴中心仪表板中扩展的状态将更改为 `In the Store`。

> [!NOTE]
> 如果你在提交或注册过程中遇到任何问题，请向扩展新支持请求提交支持票证[](https://support.microsoft.com/supportrequestform/e7a381be-9c9a-fafb-ed76-262bc93fd9e4)或向用户 [ext_dev_support@microsoft.com](mailto:ext_dev_support@microsoft.com)。
