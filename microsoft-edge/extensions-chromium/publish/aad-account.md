---
description: 了解如何将组织的用户添加到"Microsoft Edge计划"
title: 在合作伙伴中心注册Microsoft Edge计划
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/30/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: f3ddbd5cfcc1fc2180648f6daa274283e5e98ec57254308230b9d251bb1aca48
ms.sourcegitcommit: 841e41de1a32501ece862399fa56170c022127c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2021
ms.locfileid: "11809942"
---
# <a name="add-and-manage-users-from-your-organization-on-to-the-microsoft-edge-program"></a>将组织的用户添加到组织计划并Microsoft Edge计划

若要在 Microsoft Edge 计划中添加和管理用户以管理扩展，你现在可以将合作伙伴中心帐户与组织的 Azure Active Directory。

## <a name="step-1-enroll-in-the-microsoft-edge-program-on-partner-center"></a>步骤 1：在合作伙伴中心注册Microsoft Edge计划

如果你没有帐户并且不是合作伙伴中心的新用户，请继续执行步骤 **1**。 如果你有合作伙伴中心开发人员帐户，请继续执行步骤 **2**。

1. 如果你是合作伙伴中心的新用户，没有帐户，或者如果你有合作伙伴中心 (请参阅) 下面的步骤**2.c，** 有关详细信息，请导航到 Microsoft 帐户 [ (MSA) ][WindowsCommunityEverythingAboutMicrosoftAccounts] (或使用现有) 注册 Microsoft Edge 计划。 按照注册为[开发人员扩展Microsoft Edge中的步骤操作][DeveloperRegistration]。 

1. 如果你在合作伙伴中心注册了开发人员帐户，请使用 MSA (相应的 Microsoft) 登录到你的开发人员帐户。 然后，注册Microsoft Edge计划。 合作伙伴Microsoft Edge计划不支持直接使用**工作**或学校帐户注册。 
    1. **如果你已使用工作帐户**登录合作伙伴中心，你需要以全局管理员或主要所有者登录。 如果您不是所有者，请导航到"用户[][UserMGMT]管理"以查找帐户的主要所有者。
    1. 验证主所有者是 MsA (Hotmail/Live/Outlook) 用户。 要求帐户所有者使用注册合作伙伴中心的 Microsoft Edge 计划中的步骤注册 Microsoft Edge[加载项计划][DeveloperRegistration]。
    1. 如果您的组织没有 MSA (Hotmail/Live/Outlook) 帐户作为主要所有者，您需要使用 MSA 帐户注册 Microsoft Edge 计划。 当你的组织在合作伙伴中心上拥有商业帐户时，将发生这种情况。 按照注册合作伙伴[中心的 Microsoft Edge 计划中的步骤操作][DeveloperRegistration]。

设置帐户后，继续下一部分，将你的 Azure AD 租户链接到此帐户进行扩展管理。

## <a name="step-2-associate-azure-active-directory-with-your-account"></a>步骤 2：Azure Active Directory帐户关联

可以使用Azure Active Directory帐户添加和管理Microsoft Edge用户。 你可以添加单个用户、用户组或 Azure AD 应用程序。 

### <a name="associate-azure-active-directory-with-your-account"></a>将Azure Active Directory与帐户关联

为了添加和管理帐户用户，必须先将帐户与组织的 Azure Active Directory。 如果你的组织已经使用 Office 365 或 Microsoft 的其他业务服务，则你已经具有 Azure AD。 否则，你可以免费创建新的 Azure AD 租户。 有关详细信息，请导航到[将Azure Active Directory与合作伙伴中心帐户关联|Microsoft Docs][AssociateAzureADPCnew]。

有关详细信息[，Azure Active Directory关联到合作伙伴中心][AssociateAzureADPC]帐户。 虽然此主题重点介绍Windows开发人员计划，但关联租户的方式与租户Microsoft Edge相同。

> [!IMPORTANT]
> 如果在将 Azure AD 帐户与合作伙伴中心上的 Microsoft 帐户关联后添加了用户，请注意，当前不支持更改用户的角色或权限。 但是，您可以继续根据需要添加多少用户，并使用"用户管理"部分中的筛选器选项查找特定角色[][UserManagementPartnerCenter]的管理员。

## <a name="step-3-add-users-groups-and-azure-ad-applications-to-your-account"></a>步骤 3：将用户、组和 Azure AD 应用程序添加到你的帐户

设置 Azure AD 关联后，可以在合作伙伴中心上的"帐户设置""用户管理****"  >  **中添加用户**。 每个用户都完全可以访问程序中可用的扩展。 还可以添加用户组和 Azure AD 应用程序，以授予他们访问合作伙伴中心帐户的权限。 有关添加用户的信息，请参阅添加 [用户、组和 Azure AD 应用程序][AddAzure]。

## <a name="contact-us"></a>联系我们 

如果您需要有关关联 Azure AD 帐户或其他相关查询的帮助，请导航到"联系[Microsoft Edge][ContactEdgeExtensions]扩展支持"并查找查询的相关支持联系人。


<!-- links -->

[AssociateAADWithPartnerCenterAccount]: https://docs.microsoft.com/windows/uwp/publish/associate-azure-ad-with-partner-center

[CreateNewAzureAD]: https://docs.microsoft.com/windows/uwp/publish/associate-azure-ad-with-partner-center#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account

[UserManagementPartnerCenter]: https://partner.microsoft.com/dashboard/account/v3/usermanagement

[AddAADUsersGroups]: https://docs.microsoft.com/windows/uwp/publish/add-users-groups-and-azure-ad-applications

[ContactEdgeExtensions]: ./contact-extensions-team.md "联系边缘扩展支持|Microsoft Docs"

[WindowsCommunityEverythingAboutMicrosoftAccounts]:  https://community.windows.com/stories/everything-you-need-to-know-about-microsoft-accounts "你需要了解的 Microsoft 帐户信息|Windows Community"

[MicrosoftAccount]:  https://account.microsoft.com/account "Microsoft 帐户"

[DeveloperRegistration]: ./create-dev-account.md "注册为Microsoft Edge开发人员|Microsoft Docs"

[AssociateAzureADPC]: /windows/uwp/publish/associate-azure-ad-with-partner-center "将Azure Active Directory与合作伙伴中心帐户|Microsoft Docs"

[AssociateAzureADPCnew]: /windows/uwp/publish/associate-azure-ad-with-partner-center#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account "将Azure Active Directory与合作伙伴中心帐户|Microsoft Docs"

[AddAzure]: /windows/uwp/publish/add-users-groups-and-azure-ad-applications "将用户、组和 Azure AD 应用程序添加到|Microsoft Docs"

[UserMGMT]: https://partner.microsoft.com/dashboard/account/v3/usermanagement "Microsoft 合作伙伴中心|帐户设置|用户管理"