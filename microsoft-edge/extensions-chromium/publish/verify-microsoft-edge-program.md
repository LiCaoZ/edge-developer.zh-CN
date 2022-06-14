---
title: 验证与 Microsoft 合作伙伴中心帐户关联的公司帐户信息
description: 了解在公司注册合作伙伴中心Microsoft Edge计划以将扩展发布到Microsoft Edge加载项网站时如何验证帐户信息。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 06/09/2022
ms.openlocfilehash: a2a1958eb40c93d8ce79a28ea84873eea535d18c
ms.sourcegitcommit: 6e391333a3e37bb862ac6124ed154f779dbaf027
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2022
ms.locfileid: "12589478"
---
# <a name="verify-the-company-account-information-associated-with-your-microsoft-partner-center-account"></a>验证与 Microsoft 合作伙伴中心帐户关联的公司帐户信息

在合作伙伴中心注册Microsoft Edge计划以发布扩展名或更改个人资料中的法律详细信息时，Microsoft 会验证你提供的信息。 信息可以包括公司名称、公司地址和主要联系人详细信息。 在此过程中，Microsoft 可能会向主要联系人发送电子邮件以请求验证。

可以转到合作伙伴中心[的法律信息](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)，监视Microsoft Edge开发人员计划的验证状态。

帐户验证完成后，可以使用合作伙伴中心仪表板将扩展发布到Microsoft Edge加载项网站。

验证通常需要三到五个工作日。 如果已过五天以上，可以联系[Microsoft Edge扩展支持](/microsoft-edge/extensions-chromium/publish/contact-extensions-team/)部门寻求帮助。


<!-- ====================================================================== -->
## <a name="what-is-verified-and-what-is-required-for-a-company-account"></a>验证的内容以及公司帐户需要什么？

本部分介绍验证类型、验证内容以及满足验证要求的建议。

### <a name="verify-email-ownership"></a>验证电子邮件所有权

电子邮件所有权验证主要联系人 (主电子邮件) 地址是否有效。

* 主要联系人电子邮件地址必须是受监视并可发送/接收电子邮件的工作帐户。
* 避免使用与公司域无关的个人电子邮件地址，例如 abc@gmail.com。
* 避免使用未与电子邮件关联的租户用户凭据，此类asjsmith@testcompany microsoft.com。

#### <a name="suggestions"></a>建议

请务必将来自 Microsoft.com 的电子邮件标记为 **安全** 域，并检查垃圾邮件文件夹。

如果在一个工作日内未收到电子邮件所有权验证电子邮件，可以要求我们再次发送电子邮件。 转到合作伙伴中心帐户，转到 **“主页>帐户设置**。 在 **帐户设置上|“我的配置文件** ”页，选择 **“重新发送验证电子邮件**”。

### <a name="verify-employment"></a>验证就业情况

就业验证确认你的主要联系人是注册公司的员工，并且注册表中输入的域属于注册公司。

* 公司的公共网站与注册表单中输入的域相同。
* 联系人拥有公司拥有的电子邮件域上的活动电子邮件地址。

#### <a name="suggestions"></a>建议

对于验证证明，可以提交网站的屏幕截图，其中显示了组织的名称、地址、联系人信息和域。

如果就业验证被拒绝，或者注册电子邮件的域与雇主的公有域不同，则必须提供文档， ***确认电子邮件域属于雇主的所有权***，其形式为：

* 组织授权代表的分配信。
* 域所有权记录，如 [whois](https://www.whois.com/whois)。
* 域购买发票或注册表确认记录。

### <a name="verify-business"></a>验证业务

业务验证确认注册公司是合法的业务实体，并在声明的地址。

#### <a name="suggestions"></a>建议

提交以下文档之一进行业务验证：

* 组建文档，如合并文章、合伙企业契约。
* 特许经营或代理约会信。
* 政府颁发的信件、许可证、企业登记或税务登记证书。
* 租约或租赁文档。
* 来自金融机构或公用事业公司的信件或声明。
* 在政府注册表网站上记录。 必须显示站点/链接。
* 证券交易所申报或纳税申报记录。
* 外部公司数据库，如 Dun & Bradstreet (DUNS ID) 或州注册表。
* 收到公司所在国家、直辖市的收据。

确认 [法律业务配置文件](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) 中的公司名称和地址没有拼写错误或缩写。 它们必须与正式的公司业务注册记录完全匹配。 如果适用，请选择在外部公司数据库中找到的匹配项，例如 Dun & Bradstreet (DUNS ID) 或状态注册表。

Microsoft 使用此文档验证公司是否有权以该名称进行业务，以及它是否位于提供的地址。 如需进一步帮助，请转到个人资料页，通过交互式审查体验上传其他证据;请参阅下一部分， [检查验证状态](#checking-your-verification-status)。


<!-- ====================================================================== -->
## <a name="checking-your-verification-status"></a>检查验证状态

可以在帐户中的合作伙伴中心检查验证状态**[设置 |法律信息](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)**，可在其中看到：

1. 一个或多个选项卡，例如 **合作伙伴**、 **开发人员**或 **经销商**，具体取决于组织在其中注册的程序。
1. “ **开发人员”** 选项卡包含显示验证阶段和任何挂起阶段的 **“帐户详细信息** ”进度栏。
1. 验证状态： **挂起**、 **已授权/接受**或 **操作必需/已拒绝**，并带有状态图标。
1. 包含信息图标 **的“法律业务配置文件** 进度”栏，可以选择以获取详细信息。
1. “ **立即修复** ”按钮，用于开始解决验证问题。


<!-- ====================================================================== -->
## <a name="verification-status"></a>验证状态

检查验证状态时有三种可能的结果：

*   **已授权/接受**：你提交的信息已验证，你已收到接受程序的通知。 无需执行其他操作。

*   **挂起**：验证过程已启动，但尚未完成。 如果已完成电子邮件验证步骤，则无需执行其他操作。 可以在帐户设置 |监视验证状态法律信息。 验证通常需要三到五个工作日。

*   **操作必需/已拒绝**：无法验证你提交的信息。 原因以及如何上诉的说明显示在 **“帐户验证** ”窗格中。 请参阅下面 [的“对已拒绝的应用程序进行上诉](#appealing-a-rejected-application)”。


<!-- ====================================================================== -->
## <a name="appealing-a-rejected-application"></a>对被拒绝的应用程序提出上诉

对被拒绝的应用程序提出上诉：

1. 在**[帐户设置 |法律信息](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)**，立即选择 **“修复**”。
1. 在 **帐户验证**中，从 **“选择要上传的文档类型**”中，选择要上传以进行验证的文档类型。
1. 在 **“输入批注**”中，可以输入有关上诉的详细信息。
1. 选择**Upload**。

审查上诉所需的时间不同。 可以返回到**[帐户设置 |随时](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer)** 检查验证状态的法律信息。 审阅期间验证状态 **为“挂起** ”。

![帐户设置 |法律信息](media/account-settings-legal-info-microsoft-edge-partner-center.png)


> [!NOTE]
> 无法从企业帐户切换回单个帐户。 请参阅文档以做出明智的决策。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

若要查看验证状态，请转到 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择 **“帐户设置**”。  在等待验证过程完成时，继续生成、测试和准备提交。

*  [发布扩展](publish-extension.md)

*  [扩展概念和体系结构](../getting-started/index.md)

*  [将用户添加到Microsoft Edge程序](aad-account.md) - 将其他用户添加到Microsoft Edge计划和合作伙伴中心开发人员帐户。  若要启用添加用户，请将组织的Azure Active Directory帐户与合作伙伴中心上 MSA)  (Microsoft 帐户相关联。

