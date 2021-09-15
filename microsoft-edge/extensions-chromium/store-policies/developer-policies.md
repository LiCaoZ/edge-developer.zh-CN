---
description: Microsoft Edge 加载项商店开发人员策略
title: Microsoft Edge 加载项商店开发人员策略
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/17/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员
ms.openlocfilehash: f05ae204316797dc7a532d825f71572abcff89d7
ms.sourcegitcommit: 1c5bc4695c976805fb5acbdac3350414bf79582d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2021
ms.locfileid: "11976556"
---
# <a name="microsoft-edge-add-ons-store-developer-policies"></a>Microsoft Edge 加载项商店开发人员策略  

## <a name="introduction-and-objective-of-this-document"></a>本文档的简介和目标  

感谢你有兴趣开发适用于加载项Microsoft Edge扩展。  Microsoft Edge 加载项应用商店开发人员策略 \ (加载项应用商店开发人员策略\) 适用于你的扩展，包括通过合作伙伴中心提交扩展，以及通过 Microsoft Edge 加载项提供此类扩展。 [][MicrosoftPartnerCenter]  

加载项_Microsoft Edge也称为_加载项Microsoft Edge_加载项网站_。  加载项_Microsoft Edge开发人员_策略也称为加载项Microsoft Edge_开发人员_策略。


## <a name="principles"></a>原则  

下面是一些入门准则：  

*   你应该在扩展中提供独特且独特的价值，以用于Microsoft Edge。  提供从加载项应用商店 \Microsoft Edge 加载项\加载项 (Microsoft Edge下载扩展的极具吸引力) 。  
*   你不得误导我们的联合用户有关你的扩展功能、谁提供它等。  
*   不得试图欺骗用户、系统或生态系统。  我们的加载项Microsoft Edge任何类型的欺诈;是评分和审查操作、信用卡欺诈或其他欺诈活动。  
    
遵循加载项Microsoft Edge开发人员策略有助于你做出选择，以增强扩展的吸引力和受众。  

扩展对于亿万用户的体验至关重要。  我们期待体验你创建并感到兴奋，帮助你向全世界提供扩展。  

## <a name="1-product-policies"></a>1. 产品策略  

### <a name="11-distinct-function--value-accurate-representation"></a>1.1 Distinct Function & Value;准确的表示形式  

扩展和相关元数据必须准确且清楚地反映您描述的源、功能和功能。  

#### <a name="111-extensions-must-have-a-single-purpose"></a>1.1.1 扩展必须具有单一用途  

扩展必须具有具有窄功能的单一用途。  

#### <a name="112-describe-your-extension"></a>1.1.2 描述扩展  

扩展的所有方面都应准确地描述扩展的功能、功能和任何重要限制，包括必需或受支持的输入设备。  首次运行体验期间，扩展的价值主张必须清楚。  您的扩展不得使用类似于其他扩展的名称或图标，如果您无权进行该表示，则不得声明代表公司、政府机构或其他实体。  

#### <a name="113-functionality"></a>1.1.3 功能  

扩展必须完全正常工作。  

#### <a name="114-search-and-discovery"></a>1.1.4 搜索和发现  

搜索词不能超过七个唯一术语，且应该与扩展相关。  

#### <a name="115-provide-appropriate-details"></a>1.1.5 提供相应详细信息  

你必须提供有关扩展以及扩展一览 \ (metadata\) 功能的详细信息。  扩展必须提供有价值且高质量的用户体验。  你的扩展还必须在加载项Microsoft Edge活动状态。  

#### <a name="116-stability-and-performance"></a>1.1.6 稳定性和性能  

扩展不得对扩展的性能或稳定性Microsoft Edge。  

#### <a name="117-obfuscation"></a>1.1.7 模糊处理  

不允许使用模糊代码的扩展。  这包括扩展包中的代码，以及从 Web 获取的任何外部代码或资源。  如果代码不可审阅，系统可能会要求您重构代码的某些部分。  

#### <a name="118-altering-browser-settings"></a>1.1.8 更改浏览器设置  

未经适当的用户同意，您的扩展不得更改或看似改变浏览器功能或设置，包括但不限于：地址栏搜索提供程序和建议、起始页或主页、新选项卡页以及添加或删除收藏夹。  

对浏览器设置的任何更改都应在扩展说明中明确记录。  

您的扩展可能仅修改关键设置，以将 Microsoft 网页或服务替换为第三方 \ (例如，要求使用第三方搜索引擎，或将主页设置为第三方 Web 属性\) （如果你被此类第三方使用或以其他方式关联）。  

### <a name="12-security"></a>1.2 安全性  

你的扩展不得危及或损害用户安全，或设备、系统或相关系统的安全或功能。  

#### <a name="121-content-security-policies"></a>1.2.1 内容安全策略  

> [!NOTE]
> 如果对扩展进行除上述功能之外的任何更改，则对代码的任何更改都必须符合Microsoft Edge[安全策略][MicrosoftEdgeContentSecurityPolicyRemoteScript]。  例如，扩展不应下载远程脚本，随后以与描述的功能不一致的方式运行该脚本。  

#### <a name="122-unwanted-and-malicious-software"></a>1.2.2 不需要和恶意软件  

您的扩展不得包含或启用 Microsoft 针对不需要和恶意软件 [的条件所定义的恶意软件][MicrosoftIdentifiesMalwareUnwantedApplications]。  

#### <a name="123-dependency-on-other-software"></a>1.2.3 依赖其他软件  

扩展可能依赖于非集成软件 \ (如其他产品、模块或服务\) 以提供主要功能，但您必须在描述中披露依赖项  

#### <a name="124-extensions-update"></a>1.2.4 扩展更新  

除非 Microsoft 另行允许，否则扩展必须仅通过加载项Microsoft Edge更新。  

### <a name="13-product-is-testable"></a>1.3 产品可测试  

扩展必须可测试。  如果出于任何原因（包括但不限于以下项目）无法测试扩展，你的扩展可能无法满足此要求。  

#### <a name="131-user-credentials"></a>1.3.1 用户凭据  

如果您的扩展需要登录凭据，则使用 字段提供一个工作演示 `Notes for certification` 帐户。  

#### <a name="132-availability-of-services"></a>1.3.2 服务的可用性  

如果您的扩展需要访问服务器，则服务器必须能够正常运行，以验证其是否正常工作。  

### <a name="14-usability"></a>1.4 可用性  

你的扩展必须符合Microsoft Edge加载项应用商店的可用性标准，包括但不限于以下子部分中列出的标准。  

#### <a name="141-compatibility-across-platforms"></a>1.4.1 跨平台的兼容性  

你的扩展应该与Microsoft Edge下载它们的所有设备和平台上的扩展兼容。  如果在与扩展不兼容的设备上下载扩展，它应在启动时检测到该扩展，并向用户显示一条消息，详细说明设备必须满足的要求以便与扩展兼容。  

#### <a name="142-user-experience"></a>1.4.2 用户体验  

扩展必须迅速启动，并且必须保持响应用户输入。  扩展必须继续运行，并始终响应用户输入。  扩展必须正常关闭，且不能意外关闭。  处理异常后，扩展应处理异常并始终响应用户输入。  

### <a name="15-personal-information"></a>1.5 个人信息  

以下要求适用于访问个人信息的扩展。  个人信息包括标识或可用于标识人员或与此类信息或数据关联的所有信息或数据。  

#### <a name="151-collect-personal-information-only-when-necessary"></a>1.5.1 仅在必要时收集个人信息  

你的扩展可能会收集、访问、使用或传输个人信息 \ (包括 Web 浏览活动\) ;仅在需要且仅在显著披露的面向用户的功能中使用时。  

#### <a name="152-maintain-a-privacy-policy"></a>1.5.2 维护隐私策略  

无论扩展是访问、收集还是传输个人信息;你必须在法律要求时提供醒目的通知并遵守隐私策略。  隐私策略必须通知用户你的扩展访问、收集或传输的个人信息、该信息的使用、存储和保护方式，并指示其披露给的各方类型。  隐私策略必须说明用户对信息的使用和共享的控制、他们如何访问其信息，并且必须遵守适用的法律和法规。  向扩展添加新特性和功能时，隐私策略必须保持最新。  

如果向 Microsoft 提供隐私策略，即表示你同意允许 Microsoft 与扩展用户共享此类隐私策略。  

#### <a name="153-sharing-data-with-third-parties"></a>1.5.3 与第三方共享数据  

只有在获得外部服务或第三方用户的选择加入同意后，才能通过扩展或关联元数据将扩展用户的个人信息发布到外部服务或第三方。  选择加入同意意味着用户在您执行以下操作后，在请求的活动的扩展的用户界面中提供其明确权限：  

*   向用户描述如何访问、使用或共享信息，并指示其披露给的各方类型，以及  
*   在扩展用户界面中为用户提供一种机制，他们可以选择稍后撤销权限并选择退出。  
    
#### <a name="154-sharing-information-of-non-users"></a>1.5.4 非用户的共享信息  

如果您通过扩展名或元数据将某人的个人信息发布到外部服务或第三方，但共享其信息的用户不是您的扩展用户;  

1.  您必须获得明确书面同意才能发布该个人信息。  
1.  必须允许共享其信息的人随时撤销该同意。  
1.  隐私策略必须明确披露你可能会通过此方式收集个人信息。  
1.  如果适用法律要求，你必须根据请求删除任何个人的个人信息，包括你通过此方式收集其信息的个人。  
1.  如果您的扩展为用户提供了对其他人个人信息的访问权限，则此要求也适用。  
    
#### <a name="155-transmit-information-securely"></a>1.5.5 安全地传输信息  

如果扩展收集、存储或传输个人信息;必须使用新式加密方法安全地进行加密。  

#### <a name="156-highly-sensitive-information"></a>1.5.6 高度敏感信息  

您的扩展不得收集、存储或传输高度敏感的个人信息，例如健康或财务数据，除非该信息与扩展的功能相关。  在收集、存储或传输此类信息之前，你的扩展还必须获得用户明确同意。  

### <a name="16-permissions"></a>1.6 权限  

扩展必须仅请求正常运行所需的权限。  你必须提供扩展工作原理的说明。  扩展必须仅执行所述的操作。  扩展可能不会请求超出声明的执行和运行所需功能的功能的权限。  

### <a name="17-localization"></a>1.7 本地化  

应为扩展声明支持的所有语言本地化扩展。  扩展说明的文本应该以声明的每种语言进行本地化。  
如果扩展已本地化，因此某些功能在本地化版本中不可用，则必须在扩展说明中清楚地说明或显示本地化的限制。 Extension 提供的体验在它支持的所有语言中必须非常类似。  

### <a name="18-financial-transactions"></a>1.8 财务事务  

如果你的产品包括产品内购买、订阅、虚拟货币、计费功能或捕获财务信息;以下各节中的要求适用。  

#### <a name="181-paid-features"></a>1.8.1 付费功能  

你的扩展可能允许用户使用通过第三方购买机制或 API 购买的数字内容或服务。  

您必须使用安全的第三方购买 API 购买物理商品或服务。  你必须使用安全的第三方购买 API，以支付与任何其他服务（包括实际管理或自我贡献）相关付款。  

*   如果你的扩展用于促进或收集集体贡献，或进行促销比赛或比赛，则必须遵循适用法律。  
*   您还必须明确声明，Microsoft 不是此次促销活动的集资者或主办方。  
*   在扩展中销售的产品内产品/服务不得转换为任何合法有效的货币 \ (如美元、欧元等\) 或任何物理商品或服务。  
    
以下要求适用于使用安全的第三方购买 API：  

*   在交易时或收集用户的任何付款或财务信息时;您的扩展必须标识商业交易提供商、对用户进行身份验证，并获取交易的用户确认。  商业交易提供商维护一个安全的财务交换平台。  
*   您的扩展可能为用户提供保存此身份验证的能力，但用户必须能够要求每次事务进行身份验证或关闭产品内事务。  
*   如果您的扩展收集信用卡信息，或者使用收集信用卡信息的第三方付款处理器，则付款处理必须符合当前的 PCI 数据安全标准 \ (PCI DSS\) 。  
    
#### <a name="182-disclosing-paid-features"></a>1.8.2 泄漏付费功能  

扩展和相关元数据必须提供有关所提供的产品内购买类型和价格范围的信息。  不得误导用户，并且必须清楚产品内促销和产品/服务的性质，包括任何试用体验的范围和条款。  如果扩展限制在试用期间或之后访问用户创建的内容，则必须提前通知用户。  此外，你的扩展必须让用户清楚他们正在你的扩展中启动购买选项。  

### <a name="19-notifications"></a>1.9 通知  

你的扩展必须遵守通知的系统设置。  这意味着向用户显示的广告和通知必须与用户首选项一致，无论通知是由 Microsoft 推送通知服务 \ (MPNS\) 、Windows 推送通知服务 \ (WNS\) 还是由任何其他服务提供。  如果用户在特定于产品或系统范围内禁用通知，扩展必须保持功能。  

如果你的产品使用 MPNS 或 WNS 传输通知，它必须符合以下要求：  

#### <a name="191-general-guidance"></a>1.9.1 一般指南  

通过 WNS 或 MPNS 提供的通知被视为产品内容，并受所有加载项目录开发人员策略限制。  

#### <a name="192-ownership-of-notifications"></a>1.9.2 通知的所有权  

不得掩盖或试图伪装从扩展启动的任何通知的来源。  

#### <a name="193-no-confidential-or-sensitive-information"></a>1.9.3 无机密或敏感信息  

不得在通知中包括用户合理认为机密或敏感的任何信息。  

#### <a name="194-purpose-of-notifications"></a>1.9.4 通知的用途  

从你的扩展发送的通知必须与该扩展或你在 Microsoft Edge 加载项应用商店中发布的其他扩展相关，并且不得包含与你的扩展不相关的任何类型的促销邮件。  

### <a name="110-advertising-conduct-and-content"></a>1.10 广告行为准则和内容  

对于所有与广告相关联的活动，应符合以下要求：  

#### <a name="1101-purpose"></a>1.10.1 用途  

扩展的主要内容不得为广告，并且广告必须与扩展中其他内容明确区分。  

#### <a name="1102-policies-and-agreements"></a>1.10.2 策略和协议  

扩展显示的任何广告内容都必须遵守 [Microsoft 创意接受策略][MicrosoftAdvertisingCreativeAcceptancePolicies]。  
如果你的扩展显示广告，则显示的所有内容都必须符合应用开发人员协议和此 [策略的广告要求][MicrosoftAppDeveloperAgreement] 。  

#### <a name="1103-quality-of-advertising"></a>1.10.3 广告质量  

*   扩展的主要用途不得是让用户单击广告。  
*   你的扩展不得执行任何干扰或降低其显示的任何广告的可见性、价值或质量的任何工作。  

#### <a name="1104-promotions"></a>1.10.4 促销  

如果你购买或创建促销广告市场活动以通过合作伙伴中心中的广告市场活动功能推广你的扩展，你向[][MicrosoftPartnerCenter]Microsoft 提供的所有广告材料（包括任何关联的登陆页面）都必须符合[Microsoft 创意][MicrosoftAdvertisingCreativeSpecifications]规范策略和[Microsoft 创意接受][MicrosoftAdvertisingCreativeAcceptancePolicies]策略。  

#### <a name="1105-notifying-users-of-opt-out-for-interest-based-advertising"></a>1.10.5 通知用户Opt-OutInterest-Based广告  

你的隐私声明或使用条款必须让用户知道你计划向广告服务提供商发送个人信息，并且必须告诉用户他们如何选择退出基于兴趣的广告。  

#### <a name="1106-other-guidelines"></a>1.10.6 其他准则  

如果你的扩展面向 13 岁以下的儿童，如《儿童在线隐私保护法》[中的定义][FTCChildrensPrivacy];你必须在合作伙伴中心向 Microsoft[][MicrosoftPartnerCenter]通知这一情况，并确保扩展中显示的所有广告内容都适合 13 岁以下的儿童。  

## <a name="2-content-policies"></a>2 内容策略  

以下策略适用于内容和元数据 \ (包括发布者名称、扩展名称、扩展图标、扩展说明、扩展屏幕截图、扩展预告片和预告片缩略图，以及任何其他在 Microsoft Edge 加载项中提供用于分发的扩展元数据\) 。  内容是指扩展中包含的图像、声音、视频和文本、通过扩展公开的磁贴、通知、错误消息或广告，以及从服务器或扩展连接到的任何内容。  由于扩展Microsoft Edge加载项已全球使用，因此在地区和文化规范的上下文中解释和应用这些要求。  

### <a name="21-content-requirements-for-microsoft-edge-addon-catalog-listing"></a>2.1 加载项目录Microsoft Edge的内容要求  

你提交的元数据和扩展附带的其他内容可能不包含成熟内容。  
不符合加载项应用商店Microsoft Edge一览要求的提交将被拒绝或立即删除。  

### <a name="22-content-including-names-logos-original-and-third-party"></a>2.2 内容，包括名称、徽标、原始和第三方  

扩展和相关元数据中的内容必须由你最初创建，或由第三方权利持有者适当授权，并且必须仅在权限持有者允许或法律允许的情况下使用。  

### <a name="23-risk-of-harm"></a>2.3 危害风险  

#### <a name="231-requirements"></a>2.3.1 要求  

您的扩展不得包含任何促进或宣传以下实际活动的内容：\ (\) 极端或无端暴力;\ (b\) 违反;\ (c\) 制造非法武器;或 \ (d\) 对个人、动物、真实或个人属性使用武器。  

#### <a name="232-responsibility"></a>2.3.2 责任  

你的扩展不得：\ (\) 对最终用户或者任何其他人员或动物造成危害、危害或任何其他危害;或 \ (b\) 对真实或个人属性带来风险或造成损坏。  你应单独负责所有扩展安全测试、证书获取以及任何相应功能安全措施的实施。  不得禁用任何平台安全或舒适功能，并且必须在扩展中包括所有适用的法律要求和行业标准警告、通知和免责声明。  

### <a name="24-defamatory-libelous-slanderous-and-threatening"></a>2.4 中拉拉、中利贝利、斯兰达和布尔  

您的扩展不得包含任何破坏性、中义性、中化或威胁的内容。  

### <a name="25-offensive-content"></a>2.5 冒犯性内容  

扩展和关联的元数据不得包含潜在敏感或冒犯性内容。  由于当地法律或文化规范，内容在某些国家/地区可能被视为敏感或冒犯性内容。  此外，你的扩展和相关元数据不得包含基于种族、族裔、国家/地区、语言、性别、年龄、残障、性取向、作为一名好人的状态或任何其他社会团体中的成员身份而宣传种族、种族或暴力的内容。  

### <a name="26-alcohol-tobacco-and-drugs"></a>2.6000000000000000000000000000000  

您的扩展不得包含任何促进或宣传滥用或滥用商品、非法产品或非法滥用的内容。  

### <a name="27-adult-content"></a>2.7 成人内容  

您的扩展不得包含或显示合理人员认为具有色情性或明显性的内容。  

### <a name="28-prohibited-content-services-and-activity"></a>2.8 禁止的内容、服务和活动  

扩展必须遵守以下条件。  

*   您的扩展不得包含内容或提供促进联机管理的服务。  在线购物包括但不限于在线购物者、体育俱乐部、手风牌或技能游戏，这些游戏提供现金或其他价值。  
*   您的扩展不得提供对网站内容的未经授权的访问，例如通过避开支付通道或登录限制。  
*   您的扩展不得提供、鼓励或启用对受版权保护的内容或媒体的未经授权的访问、下载或流式处理。  
*   您的扩展不得挖掘加密货币。  
    
### <a name="29-illegal-activity"></a>2.9 非法活动  

您的扩展不得包含鼓励、促进或宣传现实世界中的非法活动的内容或功能。  

### <a name="210-excessive-profanity-and-inappropriate-content"></a>2.10 过度亵亵和不当内容  

*   您的扩展不得包含过多或无理的亵亵。  
*   您的扩展不得包含或显示合理用户认为具有攻击性的内容。  
    
### <a name="211-countryregion-specific-requirements"></a>2.11 特定于国家/地区的要求  

不允许在扩展所针对的任何国家/地区中冒犯性内容。  由于当地法律或文化规范，一些内容可能会在某些国家/地区视为冒犯性内容。  在某些国家/地区可能被视为具有冒犯性的内容示例包括以下各项：  

**中国**  

*   违禁的色情内容  
*   有争议的领土或区域引用  
*   提供或允许对违反适用的当地法律的内容或服务的访问  
    
### <a name="212-age-ratings"></a>2.12 年龄分级  

#### <a name="2121-mature-content"></a>2.12.1 成熟内容  

将扩展提交到 [合作伙伴中心][MicrosoftPartnerCenter]时，必须指示扩展是否显示应标记为"成熟"的内容。  在确定扩展的分级时，请考虑应用内的所有内容（包括用户生成的内容和广告）以及扩展链接的内容。  如果你指示你的扩展不包含任何"成熟"内容，则你负责保持此分级的准确性。  无论为扩展提供何种分级，它仍然必须遵循加载项开发人员策略Microsoft Edge所有内容要求  

#### <a name="2122-ratings-change"></a>2.12.2 评分更改  

如果扩展提供的内容 \ (如用户生成的内容、零售内容或其他基于 Web 的内容\) 可能适用于高于分配分级的年龄分级，则必须要求用户选择通过使用内容筛选器或通过使用预先存在的帐户登录来接收此类内容。  

### <a name="213-videos"></a>2.13 视频  

如果你在一览中提交促销视频，它应遵循此策略中提到的所有内容指南。  如果选择提供 YouTube 链接，必须确保为要嵌入的特定视频关闭广告。  若要详细了解如何打开或关闭 YouTube 上的广告，请导航[][GoogleYoutubeAnswer2531367Topic7072227]到"设置嵌入视频的默认广告格式[和广告"。][GoogleYoutubeAnswer132596]


## <a name="certification-appeal-process"></a>认证请求流程

所有扩展都应遵循上面列出的应用商店策略。 如果扩展在审查过程中失败，请查看应用商店策略以了解失败的原因。 使用合作伙伴中心提交扩展后，若要询问有关其评价或认证状态的问题，请导航 [到"新建][MicrosoftSupportSupportrequestformE7a381be9c9aFafbEd76262bc93fd9e4] 支持请求"并填写表单。

### <a name="microsoft-edge-add-ons-appeal-statistics-for-fy2021"></a>Microsoft Edge2021 年 9 月加载项吸引力统计信息

| 主要投诉类型#1：强制投诉 | 主要投诉类型#2：认证结果 | 其他投诉类型 | Total Complaints | 过度投诉 |
|:--- |:--- |
| 8 | 2 | 4 | 14 | 0 |


<!-- links -->  

[MicrosoftEdgeContentSecurityPolicyRemoteScript]: ./csp.md#relaxing-the-default-policy "支持默认策略 - 内容安全策略 \ (CSP\) |Microsoft Docs"  

[MicrosoftAppDeveloperAgreement]: /legal/windows/agreements/app-developer-agreement "应用开发人员协议|Microsoft Docs"  
[MicrosoftIdentifiesMalwareUnwantedApplications]: /windows/security/threat-protection/intelligence/criteria "Microsoft 如何识别恶意软件和可能不需要的应用程序|Microsoft Docs"  

[GoogleYoutubeAnswer2531367Topic7072227]: https://support.google.com/youtube/answer/2531367?ref_topic=7072227 "设置默认广告格式 - YouTube 帮助"  
[GoogleYoutubeAnswer132596]: https://support.google.com/youtube/answer/132596 "嵌入视频上的广告 - YouTube 帮助"  
[FTCChildrensPrivacy]: https://www.ftc.gov/tips-advice/business-center/privacy-and-security/children%27s-privacy "儿童隐私 - 联邦贸易委员会"  

[MicrosoftAdvertisingCreativeAcceptancePolicies]: https://about.ads.microsoft.com/solutions/ad-products/display-advertising/creative-acceptance-policies "创意接受策略 - Microsoft Advertising"  
[MicrosoftAdvertisingCreativeSpecifications]: https://about.ads.microsoft.com/solutions/ad-products/display-advertising/creative-specs "创意规范 - Microsoft Advertising"  

[MicrosoftPartnerCenter]: https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd "合作伙伴中心"  

[MicrosoftSupportSupportrequestformE7a381be9c9aFafbEd76262bc93fd9e4]: https://support.microsoft.com/supportrequestform/e7a381be-9c9a-fafb-ed76-262bc93fd9e4 "Extensions 新支持请求|Microsoft 支持"