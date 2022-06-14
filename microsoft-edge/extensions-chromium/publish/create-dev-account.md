---
title: 注册为 Microsoft Edge 扩展开发人员
description: 了解如何注册合作伙伴中心开发人员帐户以将扩展发布到Microsoft Edge加载项网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/27/2021
ms.openlocfilehash: e0c3a7d19420b0923b22ae35a7ae3b9308b28e02
ms.sourcegitcommit: 6e391333a3e37bb862ac6124ed154f779dbaf027
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2022
ms.locfileid: "12589438"
---
# <a name="register-as-a-microsoft-edge-extension-developer"></a>注册为 Microsoft Edge 扩展开发人员

如果你是合作伙伴中心的新用户，本文将帮助你创建合作伙伴中心帐户，通过该帐户可以将Microsoft Edge扩展提交到[Microsoft Edge加载项网站](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)。

如果你有合作伙伴中心帐户，但帐户的主要所有者不是 MICROSOFT 帐户 (MSA) ，本文将帮助你创建和链接合适的帐户。  本文将帮助你创建一个 Microsoft 帐户 (MSA) （如果没有帐户），并将帮助你将 MICROSOFT 帐户 (MSA) 链接到合作伙伴中心帐户。

若要在Microsoft Edge计划中添加和管理用户以管理扩展，可以将合作伙伴中心帐户与组织的Azure Active Directory (Azure AD) 租户相关联。


<!-- ====================================================================== -->
## <a name="types-of-accounts-related-to-publishing-microsoft-edge-extensions"></a>与发布Microsoft Edge扩展相关的帐户类型

| 帐户类型 | 说明 |
|---|---|
| _Microsoft 帐户 (MSA)_ | Outlook.com、Live.com 或 Hotmail.com 帐户。 |
| _GitHub帐户_ | GitHub.com 的用户帐户。  可以使用个人GitHub帐户登录到合作伙伴中心-将为你创建一个 Microsoft 帐户 (MSA) 。 |
| _合作伙伴中心帐户_， _合作伙伴中心开发人员帐户_ | _合作伙伴中心帐户_是 partner.microsoft.com 上的帐户。  若要提交Microsoft Edge扩展，需要一个_合作伙伴中心开发人员帐户_，该帐户是一个合作伙伴中心帐户，其 Microsoft 帐户 (MSA) 作为主所有者。 |
| _Microsoft Edge计划帐户_ | 使多个用户能够在合作伙伴中心使用Microsoft Edge扩展。 |
| _Azure Active Directory_、_AD 帐户_、_Azure AD_ | Azure Active Directory帐户。 |
| _Azure Active Directory租户_、_AAD 租户_ | _租户_表示组织。  租户是组织或应用开发人员在与 Microsoft 建立关系时收到的 Azure AD 的专用实例。 |


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

若要向Microsoft Edge加载项网站提交扩展，必须注册为具有Microsoft Edge程序的开发人员。  在[合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)注册Microsoft Edge计划。  若要注册Microsoft Edge程序，需要一个 Microsoft 帐户 (MSA) 。  如果没有 Microsoft 帐户 (MSA) ，请创建一个。  在 MSA)  (创建 Microsoft 帐户的一种方法是使用现有的GitHub帐户登录到合作伙伴中心。 按照对话框中显示的提示自动创建 MICROSOFT 帐户 (MSA) 。

> [!NOTE]
> 向Microsoft Edge计划提交扩展名不收取注册费。

如果没有合作伙伴中心帐户，或者有合作伙伴中心帐户，但其主所有者不是 MICROSOFT 帐户 (MSA) ，则必须执行以下操作：
*  使用现有的 Microsoft 帐户 (MSA) 注册Microsoft Edge程序。
*   (MSA) 创建新的 Microsoft 帐户。  MSA)  (Microsoft 帐户是一个Outlook.com、Live.com 或 Hotmail.com 帐户。

若要创建 Microsoft 帐户 (MSA) ：

1. 确定是否要使用现有的GitHub帐户 (MSA) 创建 Microsoft 帐户。  请参阅[使用GitHub帐户发布Microsoft Edge扩展](github.md)。

1. 如果未使用GitHub帐户 (MSA) 创建 Microsoft 帐户，请参阅 [account.microsoft.com](https://account.microsoft.com/account)。

1. 选择 **“创建 Microsoft 帐户**”。

1. 完成注册步骤。

如果有一个合作伙伴中心帐户，其中主所有者是 MICROSOFT 帐户 (MSA) ，请使用 MSA (该 Microsoft 帐户) 登录到合作伙伴中心帐户。  然后注册Microsoft Edge计划。

请注意，Microsoft Edge计划当前不支持向工作或学校帐户注册。  必须使用 MICROSOFT 帐户 (MSA) 进行注册，然后将 Azure AD 租户与该帐户链接，以便能够管理扩展。


<!-- ====================================================================== -->
## <a name="enroll-in-the-microsoft-edge-program-on-partner-center"></a>在合作伙伴中心注册Microsoft Edge计划

<!-- 1.  Navigate to the [webpage about Partner Center](https://partner.microsoft.com).  You might see a "Join the Microsoft Partner Network" page with a **Become a partner** button, or a "Welcome back" page with a **Visit Partner Center** button.  Select the **Become a partner** button or the **Visit Partner Center** button. -->

1.  导航到 [合作伙伴中心开发人员登录页](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)，然后选择 **“合作伙伴中心**”。

1.  如果有一个 Microsoft 帐户 (MSA) ，请使用它登录到合作伙伴中心。  MSA)  (Microsoft 帐户是一个Outlook.com、Live.com 或 Hotmail.com 帐户。  然后使用下表填写Microsoft Edge程序注册表。

1.  如果没有 microsoft 帐户 (MSA) ，请直接 (MSA) 创建新的 Microsoft 帐户，或者使用下一步使用GitHub帐户登录到合作伙伴中心。  合作伙伴中心帐户必须具有一个主要所有者，该主所有者是 MSA)  (Microsoft 帐户。  如果要使用现有的个人GitHub帐户登录到合作伙伴中心，请在新选项卡或窗口中[使用GitHub帐户打开“发布Microsoft Edge扩展”一](github.md)文，然后按照步骤操作。  GitHub帐户将链接到自动创建的 Microsoft 帐户 (MSA) ，该帐户的凭据可用于注册Microsoft Edge程序。

1.  登录后，将显示注册表单，以注册Microsoft Edge程序。  若要帮助填写注册表单，请参阅下一部分。

1.  在提交注册表单之前，请阅读并接受[Microsoft Edge开发人员协议](/legal/windows/agreements/app-developer-agreement)的条款和条件。

1.  若要完成注册，请选择 **“完成**”。


<!-- ====================================================================== -->
## <a name="filling-in-the-registration-form"></a>填写注册表单

按如下所示填写注册表单的字段。

### <a name="account-countryregion"></a>帐户国家/地区

此字段是你居住的地方，或者是你的企业所在的位置。

> [!IMPORTANT]
> 注册后，此字段的值为只读。

### <a name="account-type"></a>帐户类型

[合作伙伴中心的](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)Microsoft Edge计划提供个人帐户和公司帐户。  以下部分详细介绍了这些帐户。  这两种帐户类型都允许你将扩展发布到Microsoft Edge加载项网站。

> [!IMPORTANT]
> 注册后，无法更改此字段的值。

#### <a name="individual-account"></a>个人帐户

单个帐户适用于未与公司关联的开发人员。  帐户验证过程较短，涉及验证发布者显示名称是否可用。

#### <a name="company-account"></a>公司帐户

公司帐户与组织或企业相关联。  帐户验证过程更长，涉及确认你已获授权为公司创建帐户。  该过程的持续时间可能从几天到几周不等。  你的公司可能会收到来自 Microsoft 验证合作伙伴的电话。

对于公司帐户，注册到新的合作伙伴中心计划时，验证Microsoft Edge计划信息至关重要。 这是将扩展发布到Microsoft Edge加载项存储所必需的。 请参阅[“验证Microsoft Edge合作伙伴中心计划信息](verify-microsoft-edge-program.md)。

### <a name="publisher-display-name"></a>发布者显示名称

此字段包含Microsoft Edge加载项网站中显示的名称。  若要使用特定名称，该名称必须可用，并且必须具有使用该名称的权限。  公司帐户必须使用组织的注册业务名称。

此字段的最大长度为 50 (50) 个字符。

### <a name="contact-details"></a>联系人详情

此字段包含 Microsoft 用来联系你的任何有关任何帐户问题的联系信息。  注册完成后，将收到电子邮件确认。  对于公司帐户，必须使用与组织关联的已注册电子邮件地址。

### <a name="company-approver"></a>公司审批者

对于公司帐户，必须提供公司审批者的联系信息。  联系人信息包括姓名、电子邮件地址和电话号码。  作为验证过程的一部分，Microsoft 会联系指定的公司审批者，以确保你的扩展属于你的组织。


<!-- ====================================================================== -->
## <a name="next-steps"></a>后续步骤

若要显示验证状态，请转到 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) ，然后选择 **“帐户”设置**。  在等待验证过程完成时，继续生成、测试和准备提交。

*  [发布扩展](publish-extension.md)

*  [扩展概念和体系结构](../getting-started/index.md)

*  [将用户添加到Microsoft Edge程序](aad-account.md) - 将其他用户添加到Microsoft Edge计划和合作伙伴中心开发人员帐户。  若要启用添加用户，请将组织的Azure Active Directory帐户与合作伙伴中心上 MSA)  (Microsoft 帐户相关联。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [快速入门：在](/azure/active-directory/develop/quickstart-create-new-tenant) Active Directory 文档中设置租户 - 有关Azure Active Directory (Azure AD) 租户的常规信息。
