---
title: 验证与 Microsoft 合作伙伴中心帐户关联的公司帐户信息
description: 了解如何在合作伙伴中心注册 Microsoft Edge 计划以将扩展发布到 Microsoft Edge 加载项网站时验证帐户信息。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/02/2022
ms.openlocfilehash: 7b867e601e65e0c041f5d16dc35a14ac7b8f2487
ms.sourcegitcommit: 8f385c507ab0077f989cc72b8b1b71703822ea95
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/03/2022
ms.locfileid: "12852192"
---
# <a name="verify-the-company-account-information-associated-with-your-microsoft-partner-center-account"></a>验证与 Microsoft 合作伙伴中心帐户关联的公司帐户信息

在合作伙伴中心注册 Microsoft Edge 计划以在个人资料中发布扩展或更改法律详细信息时，Microsoft 会验证你提供的信息。 此信息可以包括你的公司名称、公司地址和主要联系人详细信息。 在验证过程中，Microsoft 可能会向主要联系人发送电子邮件，请求确认提供的信息。

可以转到合作伙伴中心的法律 [信息](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) 来监视 Microsoft Edge 开发人员计划的验证状态。

完成帐户验证后，可以使用合作伙伴中心仪表板将扩展发布到 Microsoft Edge 加载项网站。

验证通常需要 3 到 5 个工作日。 如果超过五天，可以联系 [Microsoft Edge 扩展支持部门](/microsoft-edge/extensions-chromium/publish/contact-extensions-team/) 寻求帮助。


<!-- ====================================================================== -->
## <a name="what-is-verified-and-what-is-required-for-a-company-account"></a>公司帐户需要验证哪些内容？

本部分介绍验证的类型、验证的内容以及满足验证要求的建议。

### <a name="verify-email-ownership"></a>验证Email所有权

Email所有权验证主要联系人 (主要电子邮件) 地址是否有效。

* 主要联系人电子邮件地址必须是受监视且可以发送和接收电子邮件的工作帐户。
* 请勿使用个人电子邮件地址。  必须使用与公司域关联的电子邮件地址，例如 \<alias\>@contoso.com。
* 请勿使用未与电子邮件关联的租户用户凭据，例如 \<alias\>microsoft.com 上的@contoso。

#### <a name="suggestions"></a>建议

请务必将来自 Microsoft.com 的电子邮件标记为 **安全** 域，并检查垃圾邮件文件夹。

如果在一个工作日内未收到电子邮件所有权验证电子邮件，可以要求我们再次发送电子邮件。 转到合作伙伴中心帐户，转到 **“主页”>“帐户设置**”。 在 **“帐户设置”|我的个人资料** 页，选择 **“重新发送验证电子邮件**”。

### <a name="verify-employment"></a>验证雇佣

就业验证确认主要联系人是注册公司的员工，并且注册表单中输入的域属于注册公司。 以下信息用于验证就业情况：

* 公司的公共网站具有注册表单中输入的相同域。
* 联系人在公司拥有的电子邮件域上具有活动电子邮件地址。

#### <a name="suggestions"></a>建议

对于验证证明，可以提交网站的屏幕截图，其中显示组织的名称、地址、联系信息和域。

如果就业验证被拒绝，或者注册电子邮件的域与雇主的公共域不同，则必须提供确认 ***电子邮件域属于雇主所有权***的文档，格式为：

* 来自组织的授权代表的分配信。
* 域所有权记录，例如 [whois](https://www.whois.com/whois)。
* 域购买发票或注册表确认记录。

### <a name="verify-business"></a>验证业务

业务验证确认注册公司是合法的业务实体，并且位于应用程序中的地址。

#### <a name="suggestions"></a>建议

提交以下文档之一进行业务验证：

* 成立文件，如公司章程或合伙企业契据。
* 特许经营权或代理任命书。
* 政府颁发的信函、许可证、企业登记或税务登记证。
* 租约或租赁文档。
* 金融机构或公用事业公司的信件或对账单。
* 在政府注册表网站上记录。 必须显示站点/链接。
* 证券交易所申报或税务申报记录。
* 外部公司数据库，例如 Dun & Bradstreet (DUNS ID) 或状态注册表。
* 公司所在国家/地区、直辖市的收据。

确认 [法律业务配置文件](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) 中的公司名称和地址没有拼写错误或缩写。 它们必须与正式的公司业务注册记录完全匹配。 如果适用，请选择在外部公司数据库中找到的匹配项，例如 Dun & Bradstreet (DUNS ID) 或状态注册表。

Microsoft 使用这些文档来验证公司是否有权使用该名称开展业务，以及公司是否位于提供的地址。 如需进一步帮助，请转到个人资料页面，通过交互式审查体验上传更多证据。 有关详细信息，请参阅 [检查验证状态](#checking-your-verification-status)。


<!-- ====================================================================== -->
## <a name="checking-your-verification-status"></a>检查验证状态

可以在合作伙伴中心的 **[“帐户设置”|中检查验证状态法律信息](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)**，可在其中查看：

1. 合作伙伴 **、****开发人员**或**经销商**等一个或多个选项卡，具体取决于组织注册的计划。
1. “ **开发人员** ”选项卡包括显示验证阶段和任何挂起阶段的 **帐户详细信息** 进度栏。
1. 验证状态：**“挂起”、“****已授权/已接受**”或 **“需要操作/已拒绝**”，并带有状态图标。 有关详细信息，请参阅 [验证状态](#verification-status)。
1. **“法律业务配置文件**”进度栏带有信息图标，你可以选择以获取详细信息。
1. “ **立即修复** ”按钮可开始解决验证问题。


<!-- ====================================================================== -->
## <a name="verification-status"></a>验证状态

检查验证状态时，有三种可能的结果：

*   **已授权/已接受**：已验证你提交的信息，并通知你已接受该计划。 无需执行其他操作。

*   **挂起**：验证过程已启动，但尚未完成。 如果已完成电子邮件验证步骤，则无需执行进一步操作。 验证通常需要 3 到 5 个工作日。 可以在 **“帐户设置”|监视验证状态法律信息**。

*   **所需操作/已拒绝**：无法验证您提交的信息。 原因和上诉说明显示在 **“帐户验证** ”窗格中。 请参阅下一节中的对 [被拒绝的申请提出上诉](#appealing-a-rejected-application) 。 


<!-- ====================================================================== -->
## <a name="appealing-a-rejected-application"></a>对被拒绝的申请提出上诉

使用以下步骤对被拒绝的申请提出上诉：

1. 帐户 **[设置|“法律信息”](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)**，选择“ **立即修复**”。
1. 在 **“帐户验证”** 中，从 **“选择要上传的文档类型**”中，选择要上传用于验证的文档类型。
1. 在 **“输入评论**”中，可以输入有关上诉的详细信息。
1. 选择“ **上传**”。

审查上诉所需的时间各不相同。 可以返回到 **[“帐户设置”|随时](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)** 检查验证状态的法律信息。 审核期间验证状态为 **“挂起** ”。

![帐户设置|法律信息](media/account-settings-legal-info-microsoft-edge-partner-center.png)


> [!NOTE]
> 无法从企业帐户切换回个人帐户。 请参阅文档以做出明智的决策。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

若要查看验证状态，请转到 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择 **“帐户设置**”。  在等待验证过程完成时，可以继续生成、测试和准备提交。 查看以下扩展文档：

*  [扩展概念和体系结构](../getting-started/index.md) - 概述扩展和基本发布信息。

*  [发布扩展](publish-extension.md) - 提供发布扩展的详细信息和步骤。

*  [将用户添加到 Microsoft Edge 计划](aad-account.md) - 介绍如何将更多用户添加到 Microsoft Edge 计划和合作伙伴中心开发人员帐户。  若要启用添加用户，请将组织的 Azure Active Directory 帐户与合作伙伴中心上的 Microsoft 帐户 (MSA) 相关联。

