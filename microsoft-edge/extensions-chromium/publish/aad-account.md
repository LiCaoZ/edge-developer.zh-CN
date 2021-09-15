---
description: 将你的组织的用户添加到Microsoft Edge计划以帮助管理合作伙伴中心帐户。  允许其他团队成员使用Microsoft Edge中心帐户Microsoft Edge加载项网站发布加载项扩展。
title: 将用户添加到Microsoft Edge程序
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/27/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: 1909ff45b2286698c90007eb6e5bb0671b4d5c07
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976559"
---
# <a name="add-users-to-the-microsoft-edge-program"></a>将用户添加到Microsoft Edge程序

<!-- better? # Add users to your Partner Center account -->
<!-- todo globally: "Microsoft Edge program", or other term? -->

为了帮助管理Microsoft Edge，你可以向现有合作伙伴中心帐户添加更多用户。  若要Microsoft Edge扩展，合作伙伴中心帐户的主所有者必须是 MSA (Microsoft) 。

MSA (Microsoft) 是 Outlook.com、Live.com 或 Hotmail.com 帐户。  有关概述，请参阅[Types of accounts related to publishing Microsoft Edge extensions](create-dev-account.md#types-of-accounts-related-to-publishing-microsoft-edge-extensions)。


<!-- ====================================================================== -->
## <a name="making-sure-you-have-a-partner-center-account-with-a-microsoft-account-msa-as-the-primary-owner"></a>确保你拥有具有 Microsoft 帐户的合作伙伴中心帐户 (MSA) 作为主要所有者

若要创建可发布 Microsoft Edge 扩展的合作伙伴中心帐户，你必须拥有 Microsoft 帐户 (MSA) ，方法为直接创建一个，或者使用个人 GitHub 帐户凭据创建一个。  

在合作伙伴中心帐户能够发布 Microsoft Edge 扩展后，你可以将合作伙伴中心帐户链接到 Azure Active Directory (Azure AD) 租户。  链接的 Active Directory 租户使已添加的用户能够使用他们的工作帐户登录到合作伙伴中心开发人员帐户。

合作伙伴中心上的不同计划需要不同类型的帐户：

*  此Microsoft Edge计划 (开发人员Windows计划) 合作伙伴中心_开发人员_帐户。  合作伙伴中心开发人员帐户的主所有者是 MSA (Microsoft) 。

*  相比之下，Azure 市场需要合作伙伴中心 _商业帐户_ 。   (注册，用户必须使用工作帐户登录。) 

另请参阅合作伙伴中心文档中的以下文章：
*  [管理合作伙伴中心帐户](/partner-center/partner-center-account-setup)
*  [Microsoft 合作伙伴网络成员身份权益](/partner-center/mpn-overview)


<!-- ====================================================================== -->
## <a name="step-1-enroll-in-the-microsoft-edge-program-on-partner-center"></a>步骤 1：在合作伙伴中心注册Microsoft Edge计划

<!-- todo: consider moving entire Step 1 section into create-dev-account.md -->

首先，确定你是否拥有合作伙伴中心帐户。  如果你有合作伙伴中心帐户，请确定主要所有者是否是 Microsoft 帐户 (MSA) （加入 Microsoft Edge 计划需要该帐户）来管理 Microsoft Edge 扩展。  然后按照适用于你的合作伙伴中心帐户类型的部分中的步骤操作。

### <a name="if-you-dont-have-a-partner-center-account"></a>如果你没有合作伙伴中心帐户

1.  使用 Microsoft 帐户 (MSA) 注册到 Microsoft Edge 计划，按照注册为 Microsoft Edge 扩展开发人员一文[中的步骤操作][DeveloperRegistration]。<!-- = create-dev-account.md-->  如该文章所述，可以使用你的 GitHub 帐户在 MSA (Microsoft) 。

接下来，执行[步骤 2：将Azure Active Directory与下面的Microsoft Edge计划帐户](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account)关联。


### <a name="if-the-primary-owner-of-your-partner-center-account-isnt-a-microsoft-account-msa"></a>如果你的合作伙伴中心帐户的主要所有者不是 MSA 帐户 (Microsoft) 

对于要管理 Microsoft Edge 扩展的合作伙伴中心帐户，合作伙伴中心帐户的主所有者必须是 MSA (Microsoft) 。

若要确定合作伙伴中心帐户的主要所有者是否是 MSA 帐户 (Microsoft) ：

1. 使用 MSA (MSA) 与合作伙伴中心商业帐户对应的 Microsoft 帐户登录合作伙伴中心商业帐户。

1. 导航到 **"帐户设置**  >  [""合作伙伴][UserMGMT]中心的用户管理"。

1. 检查合作伙伴中心帐户的主要所有者是否是 MSA (Microsoft) 。  如果主要所有者不是 MSA (Microsoft 帐户) ，这意味着这是合作伙伴中心商业帐户，而不是合作伙伴中心_开发人员_帐户。 __

1. 按照注册为 Microsoft Edge 扩展开发人员中的步骤，使用 Microsoft 帐户 (MSA)  (而不是工作 Microsoft 帐户 (MSA) 或学校 Microsoft 帐户 (MSA) ) 注册 Microsoft Edge[计划][DeveloperRegistration]<!-- = create-dev-account.md-->.

接下来，执行[步骤 2：将Azure Active Directory与下面的Microsoft Edge计划帐户](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account)关联。


### <a name="if-the-primary-owner-of-your-partner-center-account-is-a-microsoft-account-msa"></a>如果你的合作伙伴中心帐户的主要所有者是 MSA 帐户 (Microsoft) 

1. 如果你已使用工作 Microsoft 帐户登录合作伙伴中心， (MSA) 注销。 合作伙伴Microsoft Edge中心上的注册计划不支持使用工作 Microsoft 帐户 (MSA) 或学校 Microsoft 帐户 (MSA) 。

1. 使用 MSA (Microsoft 帐户) 与合作伙伴中心开发人员帐户对应的帐户登录合作伙伴中心开发人员帐户。

1. 导航到 **"帐户设置**  >  [""合作伙伴][UserMGMT]中心的用户管理"。

1. 了解合作伙伴中心开发人员帐户的主要所有者。

1. 确认合作伙伴中心开发人员帐户的主要所有者是 MSA (Microsoft) 帐户。  这不能是 MSA (工作 Microsoft) 或学校 Microsoft 帐户 (MSA) 。

1. 按照注册为开发人员扩展开发人员中的步骤，使合作伙伴中心开发人员帐户的主要所有者注册 Microsoft Edge [Microsoft Edge 计划][DeveloperRegistration]<!-- = create-dev-account.md-->.

接下来，执行[步骤 2：将Azure Active Directory与下面的Microsoft Edge计划帐户](#step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account)关联。


<!-- ====================================================================== -->
## <a name="step-2-associate-azure-active-directory-with-your-microsoft-edge-program-account"></a>步骤 2：将Azure Active Directory与Microsoft Edge计划帐户关联

接下来，将你的 Azure Active Directory 租户 (Azure AD 租户) 你的 Microsoft Edge 计划帐户，以启用管理 Microsoft Edge 扩展。  可以使用 Azure Active Directory将用户添加到你的 Microsoft Edge 计划帐户，并管理该帐户中的这些用户。  您可以添加单个用户、用户组或Azure Active Directory应用程序。

若要能够将用户添加到 Microsoft Edge 计划帐户，并管理该帐户中的这些用户，必须先将 Microsoft Edge 计划帐户与组织的 Azure Active Directory 租户 (Azure AD 租户) 关联。  如果你的组织已使用 microsoft Office 365或其他业务服务，则你已经拥有 Azure AD 租户。  否则，你可以免费创建新的 Azure AD 租户。  若要创建 AD 租户，请参阅将你的合作伙伴中心帐户与合作伙伴中心帐户关联一Azure Active Directory Azure [AD][AssociateAzureADPCnew]以与合作伙伴中心_帐户关联_。

另请参阅[Azure Active Directory][AssociateAzureADPC]UWP 文档中的将你的Windows中心帐户关联。  在合作伙伴中心将 Azure AD 租户与 Microsoft Edge 计划帐户相关联的工作方式与将租户与 Windows 应用开发人员计划相关联的方式相同。

> [!IMPORTANT]
> 如果在将 Azure AD 租户与合作伙伴中心上的 Microsoft 帐户关联后添加了用户，请注意，当前不支持更改用户的角色或权限。  但是，您可以继续根据需要添加多少用户，并使用"用户管理"部分中的筛选器选项查找特定[][UserManagementPartnerCenter]角色的管理员。


<!-- ====================================================================== -->
## <a name="step-3-add-users-groups-and-azure-active-directory-applications-to-your-account"></a>步骤 3：将用户、组Azure Active Directory应用程序添加到帐户

设置关联后，可以在合作伙伴Azure Active Directory帐户设置"用户管理"**添加**  >  **用户**。  每个用户都完全可以访问程序中可用的扩展。  还可以添加用户组，或添加Azure Active Directory应用程序，以授予他们访问合作伙伴中心帐户的权限。

有关添加用户的信息，请参阅 UWP 文档中的添加用户、组Windows Azure [AD][AddAzure]应用程序。


<!-- ====================================================================== -->
## <a name="contact-us"></a>联系我们 

如果需要有关关联帐户或其他相关Azure Active Directory方面的帮助，请导航到"联系Microsoft Edge[扩展支持"。][ContactEdgeExtensions]


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [快速入门：设置](/azure/active-directory/develop/quickstart-create-new-tenant)租户 - Active Directory 文档中Azure Active Directory (Azure AD) 租户的常规信息。
<!-- contrasts "Work and school accounts, or personal Microsoft accounts" -->


<!-- ====================================================================== -->
<!-- links -->
[DeveloperRegistration]: ./create-dev-account.md "注册为Microsoft Edge开发人员|Microsoft Docs"
[ContactEdgeExtensions]: ./contact-extensions-team.md "请联系Microsoft Edge扩展支持|Microsoft Docs"

<!-- DMC/windows/uwp -->
[AssociateAADWithPartnerCenterAccount]: /windows/uwp/publish/associate-azure-ad-with-partner-center

[CreateNewAzureAD]: /windows/uwp/publish/associate-azure-ad-with-partner-center#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account

[AddAADUsersGroups]: /windows/uwp/publish/add-users-groups-and-azure-ad-applications

[AssociateAzureADPC]: /windows/uwp/publish/associate-azure-ad-with-partner-center "将Azure Active Directory与合作伙伴中心帐户|Microsoft Docs"

[AssociateAzureADPCnew]: /windows/uwp/publish/associate-azure-ad-with-partner-center#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account "创建与合作伙伴中心帐户关联的全新 Azure AD - 将Azure Active Directory与合作伙伴中心帐户关联|Microsoft Docs"

[AddAzure]: /windows/uwp/publish/add-users-groups-and-azure-ad-applications "将用户、组和 Azure AD 应用程序添加到|Microsoft Docs"

<!-- non-DMC -->
[MicrosoftAccount]: https://account.microsoft.com/account "Microsoft 帐户"

[UserManagementPartnerCenter]: https://partner.microsoft.com/dashboard/account/v3/usermanagement
[UserMGMT]: https://partner.microsoft.com/dashboard/account/v3/usermanagement "Microsoft 合作伙伴中心|帐户设置|用户管理"

[WindowsCommunityEverythingAboutMicrosoftAccounts]: https://community.windows.com/stories/everything-you-need-to-know-about-microsoft-accounts "你需要了解的 Microsoft 帐户信息|Windows Community"
