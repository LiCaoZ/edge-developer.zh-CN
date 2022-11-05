---
title: 将用户添加到Microsoft Edge程序
description: 向 Microsoft Edge 计划添加和管理组织中的用户，以帮助管理合作伙伴中心帐户。  允许其他团队成员使用合作伙伴中心帐户将 Microsoft Edge 扩展发布到 Microsoft Edge 加载项网站。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 11/03/2022
ms.openlocfilehash: f1112945f07c7c3edb1273dcf5c2866cdd97b571
ms.sourcegitcommit: dd668d16163d750f0dd23fd3379dfac9b2382b99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2022
ms.locfileid: "12854806"
---
# <a name="add-users-to-the-microsoft-edge-program"></a>将用户添加到Microsoft Edge程序

<!-- better? # Add users to your Partner Center account -->
<!-- todo globally: "Microsoft Edge program", or other term? -->

若要帮助管理 Microsoft Edge 扩展，可以将更多用户添加到现有合作伙伴中心帐户。  若要管理 Microsoft Edge 扩展，合作伙伴中心帐户的主要所有者必须是 microsoft 帐户 (MSA) 。

MICROSOFT 帐户 (MSA) 是 Outlook.com、Live.com 或 Hotmail.com 帐户。  有关用于发布扩展的帐户类型的摘要，请参阅 [与发布 Microsoft Edge 扩展相关的帐户类型](create-dev-account.md#types-of-accounts-related-to-publishing-microsoft-edge-extensions)。


<!-- ====================================================================== -->
## <a name="making-sure-you-have-a-partner-center-account-with-a-microsoft-account-msa-as-the-primary-owner"></a>确保拥有 Microsoft 帐户的合作伙伴中心帐户， (MSA) 作为主要所有者

若要创建可以发布 Microsoft Edge 扩展的合作伙伴中心帐户，必须通过直接创建 MICROSOFT 帐户或使用个人 GitHub 帐户凭据， (MSA) 。

合作伙伴中心帐户能够发布 Microsoft Edge 扩展后，可以将合作伙伴中心帐户链接到 Azure Active Directory (Azure AD) 租户。  通过链接的 Active Directory 租户，添加的用户可以使用其工作帐户登录到合作伙伴中心开发人员帐户。

合作伙伴中心上的不同计划需要不同类型的帐户：

*  Microsoft Edge 计划 (（如 Windows 开发人员计划) ）需要合作伙伴中心 _开发人员_ 帐户。  合作伙伴中心开发人员帐户的主要所有者是 MICROSOFT 帐户， (MSA) 。

*  相比之下，Azure 市场需要合作伙伴中心 _商业_ 帐户。   (若要注册，用户必须使用其工作帐户登录。) 

另请参阅合作伙伴中心文档中的以下文章：
*  [管理合作伙伴中心帐户](/partner-center/partner-center-account-setup)
*  [Microsoft 合作伙伴网络成员资格权益](/partner-center/mpn-overview)


<!-- ====================================================================== -->
## <a name="step-1-enroll-in-the-microsoft-edge-program-on-partner-center"></a>步骤 1：在合作伙伴中心注册 Microsoft Edge 计划

<!-- todo: consider moving entire Step 1 section into create-dev-account.md -->

首先，确定你是否有合作伙伴中心帐户。  如果你有合作伙伴中心帐户，请确定主所有者是否是 Microsoft 帐户 (MSA) （加入 Microsoft Edge 计划需要）来管理 Microsoft Edge 扩展。  然后，按照适用于合作伙伴中心帐户类型的部分中的步骤进行操作。

#### <a name="if-you-dont-have-a-partner-center-account"></a>如果没有合作伙伴中心帐户

1.  按照注册为 Microsoft Edge 扩展开发人员一文中的步骤，使用 Microsoft 帐户 ([MSA) 注册到 Microsoft Edge](create-dev-account.md) 计划。 如本文所述，可以使用 GitHub 帐户 (MSA) 创建 Microsoft 帐户。

接下来，执行 [下面的步骤 2：将 Azure Active Directory 与 Microsoft Edge 计划帐户相关联](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account) 。


#### <a name="if-the-primary-owner-of-your-partner-center-account-isnt-a-microsoft-account-msa"></a>如果合作伙伴中心帐户的主要所有者不是 Microsoft 帐户 (MSA) 

若要使合作伙伴中心帐户管理 Microsoft Edge 扩展，合作伙伴中心帐户的主要所有者必须是 microsoft 帐户 (MSA) 。

若要确定合作伙伴中心帐户的主要所有者是否为 Microsoft 帐户， (MSA) ：

1. 使用与合作伙伴中心商业帐户对应的 Microsoft 帐户 (MSA) 登录到合作伙伴中心商业帐户。

1. 在合作伙伴中心导航到 **“帐户设置** > [”“用户管理](https://partner.microsoft.com/dashboard/account/v3/usermanagement) ”。

1. 检查合作伙伴中心帐户的主要所有者是否是 microsoft 帐户， (MSA) 。  如果主要所有者不是 Microsoft 帐户 (MSA) ，则表示这是合作伙伴中心 _商业_ 帐户，而不是合作伙伴中心 _开发人员_ 帐户。

1. 按照注册为 Microsoft Edge 扩展开发人员中的步骤，使用个人 Microsoft 帐户 (MSA)  (不是工作 Microsoft 帐户 (MSA) 或学校 Microsoft 帐户 (MSA) ) 注册 [Microsoft Edge](create-dev-account.md) 计划。

   接下来，转到下面的 [步骤 2：将 Azure Active Directory 与 Microsoft Edge 计划帐户相关联](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account) 。


#### <a name="if-the-primary-owner-of-your-partner-center-account-is-a-microsoft-account-msa"></a>如果合作伙伴中心帐户的主要所有者是 microsoft 帐户 (MSA) 

1. 如果已使用工作 Microsoft 帐户 (MSA) 登录到合作伙伴中心，请注销。合作伙伴中心上的 Microsoft Edge 计划不支持使用工作 Microsoft 帐户 (MSA) 或学校 Microsoft 帐户 (MSA) 进行注册。

1. 使用与合作伙伴中心开发人员帐户对应的 Microsoft 帐户 (MSA) 登录到合作伙伴中心开发人员帐户。

1. 转到合作伙伴中心的 **“帐户设置** > [”“用户管理](https://partner.microsoft.com/dashboard/account/v3/usermanagement) ”。

1. 了解谁是合作伙伴中心开发人员帐户的主要所有者。

1. 验证合作伙伴中心开发人员帐户的主要所有者是 MICROSOFT 帐户 (MSA) 用户。  主要所有者不得是 MSA)  (工作 Microsoft 帐户，也不能是 MSA)  (学校 Microsoft 帐户。

1. 按照注册为 Microsoft Edge 扩展开发人员中的步骤，让合作伙伴中心开发人员帐户的主要所有者 [注册 Microsoft Edge](create-dev-account.md) 计划。

   接下来，转到 [步骤 2：将 Azure Active Directory 与 Microsoft Edge 计划帐户相关联](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account)。


<!-- ====================================================================== -->
## <a name="step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account"></a>步骤 2：将 Azure Active Directory 与 Microsoft Edge 计划帐户相关联

若要启用管理 Microsoft Edge 扩展，请将 Azure Active Directory 租户 (Azure AD 租户) 链接到 Microsoft Edge 计划帐户。  可以使用 Azure Active Directory 将用户添加到 Microsoft Edge 计划帐户，并在该帐户中管理这些用户。  可以添加单个用户、用户组或 Azure Active Directory 应用程序。

若要能够将用户添加到 Microsoft Edge 计划帐户并管理该帐户中的用户，必须先将 Microsoft Edge 计划帐户与组织的 Azure Active Directory 租户 (Azure AD 租户) 相关联。  如果组织已使用 Microsoft 提供的Office 365或其他业务服务，则你已有 Azure AD 租户。  否则，可以免费创建新的 Azure AD 租户。

若要创建 AD 租户，请参阅将 Azure Active Directory [与合作伙伴中心帐户关联](/windows/uwp/publish/associate-azure-ad-with-partner-center#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account) 一文中的创建全新的 _Azure AD 以与合作伙伴中心帐户相关联_。

另请参阅 Windows UWP 文档中的 [将 Azure Active Directory 与合作伙伴中心帐户关联](/windows/uwp/publish/associate-azure-ad-with-partner-center)。  在合作伙伴中心将 Azure AD 租户与 Microsoft Edge 计划帐户关联的方式与将租户与 Windows 应用开发人员计划关联的方式相同。

> [!IMPORTANT]
> 如果在将 Azure AD 租户与合作伙伴中心上的 Microsoft 帐户关联后添加了用户，请注意，当前不支持更改用户角色或权限。  但是，可以根据需要继续添加任意数量的用户，并使用 [用户管理](https://partner.microsoft.com/dashboard/account/v3/usermanagement) 部分的筛选器选项来查找特定角色的管理员。


<!-- ====================================================================== -->
## <a name="step-3-add-users-groups-and-azure-active-directory-applications-to-your-account"></a>步骤 3：将用户、组和 Azure Active Directory 应用程序添加到帐户

设置 Azure Active Directory 关联后，可以在合作伙伴中心的 **“帐户设置** > **”“用户管理** ”中添加用户。  每个用户对程序中可用的扩展具有完全访问权限。  还可以添加用户组或添加 Azure Active Directory 应用程序，向他们授予对合作伙伴中心帐户的访问权限。

有关添加用户的详细信息，请参阅 Windows UWP 文档中的 [添加用户、组和 Azure AD 应用程序](/windows/uwp/publish/add-users-groups-and-azure-ad-applications) 。


<!-- ====================================================================== -->
## <a name="contact-us"></a>联系我们

如果需要有关关联 Azure Active Directory 帐户或其他相关查询的帮助或帮助， [请联系 Microsoft Edge 扩展支持人员](contact-extensions-team.md)。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [快速入门：设置租户](/azure/active-directory/develop/quickstart-create-new-tenant) - Active Directory 文档中有关 Azure Active Directory (Azure AD) 租户的一般信息。
<!-- contrasts "Work and school accounts, or personal Microsoft accounts" -->
