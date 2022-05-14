---
title: Microsoft Edge 加载项商店开发人员策略
description: Microsoft Edge加载项存储开发人员策略。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 02/17/2021
ms.openlocfilehash: d80713bba5977567155b501dc74957ad72e03917
ms.sourcegitcommit: e33dc94c1a64cb6a7b5c40ca6886fefa6865c9d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2022
ms.locfileid: "12514852"
---
# <a name="microsoft-edge-add-ons-store-developer-policies"></a>Microsoft Edge 加载项商店开发人员策略


<!-- ====================================================================== -->
## <a name="introduction-and-objective-of-this-document"></a>本文档的简介和目标

感谢你对开发Microsoft Edge加载项存储的扩展感兴趣。  Microsoft Edge加载项存储开发人员策略 (加载项存储开发人员策略) 适用于扩展，包括通过[合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)提交扩展，以及通过Microsoft Edge加载项预配此类扩展。

_Microsoft Edge加载项存储_也称为_Microsoft Edge加载项网站_。  _Microsoft Edge加载项存储开发人员策略_也称为_Microsoft Edge加载项网站开发人员策略_。


<!-- ====================================================================== -->
## <a name="principles"></a>原则

下面是一些入门准则：

*   应在扩展中为Microsoft Edge提供唯一和独特的值。  提供从Microsoft Edge加载项存储 (Microsoft Edge加载项) 下载扩展的令人信服的理由。

*   您不得误导我们的联合用户，了解扩展的功能、提供扩展的人员等。

*   不得尝试欺骗用户、系统或生态系统。  我们的Microsoft Edge加载项中没有任何位置可用于任何类型的欺诈;无论是评级和审查操作、信用卡欺诈或其他欺诈活动。

遵守Microsoft Edge加载项存储开发人员策略应有助于你做出增强扩展吸引力和受众的选择。

你的扩展对亿万用户的体验至关重要。  我们期待着体验你创建的内容，并非常激动地帮助向世界提供你的扩展。


<!-- ====================================================================== -->
## <a name="1-product-policies"></a>1. 产品策略

### <a name="11-distinct-function--value-accurate-representation"></a>1.1 Distinct 函数&值;准确表示形式

扩展和关联的元数据必须准确而清晰地反映所描述的源、功能和功能。

#### <a name="111-extensions-must-have-a-single-purpose"></a>1.1.1 扩展必须具有单个用途

扩展必须具有具有窄功能的单个用途。

#### <a name="112-describe-your-extension"></a>1.1.2 描述扩展

扩展的所有方面都应准确地描述扩展的函数、功能和任何重要限制，包括所需的或受支持的输入设备。  在第一次运行体验期间，扩展的价值主张必须明确。  你的扩展不得使用与其他扩展类似的名称或图标，如果您无权进行该表示，则不得声称代表公司、政府机构或其他实体。

#### <a name="113-functionality"></a>1.1.3 功能

扩展必须功能齐全。

#### <a name="114-search-and-discovery"></a>1.1.4 搜索和发现

搜索词不得超过七个唯一术语，并且应与扩展相关。

#### <a name="115-provide-appropriate-details"></a>1.1.5 提供适当的详细信息

必须提供有关扩展的不同信息详细信息，以及列出扩展 (元数据) 中的功能。  扩展必须提供有价值且高质量的用户体验。  扩展还必须在Microsoft Edge加载项中具有活动状态。

#### <a name="116-stability-and-performance"></a>1.1.6 稳定性和性能

扩展不得对Microsoft Edge的性能或稳定性产生负面影响。

#### <a name="117-obfuscation"></a>1.1.7 模糊

不允许使用模糊代码的扩展。  这包括扩展包中的代码，以及从 Web 提取的任何外部代码或资源。  如果代码不可审阅，则可能会要求你重构部分代码。

#### <a name="118-altering-browser-settings"></a>1.1.8 更改浏览器设置

未经用户适当同意，扩展不得更改或显示为更改浏览器功能或设置，包括但不限于：地址栏搜索提供程序和建议、开始页或主页、新选项卡页以及添加或删除收藏夹。

对浏览器设置的任何更改都应在扩展说明中显式记录。

你的扩展只能修改关键设置，以将 Microsoft 网页或服务替换为第三方 (，例如需要使用第三方搜索引擎或将主页设置为第三方 Web 属性) （如果受雇于或以其他方式与此类第三方关联）。

### <a name="12-security"></a>1.2 安全性

你的扩展不得危及或损害用户安全性，也不得损害设备、系统或相关系统的安全性或功能。

#### <a name="121-content-security-policies"></a>1.2.1 内容安全策略

如果对扩展所做的任何更改超出了所述的功能，则对代码所做的任何更改都必须符合[Microsoft Edge内容安全策略](csp.md#relaxing-the-default-policy)。  例如，扩展不应下载远程脚本，随后以与所述功能不一致的方式运行该脚本。

#### <a name="122-unwanted-and-malicious-software"></a>1.2.2 不需要和恶意软件

你的扩展不得包含或启用由 Microsoft“ [不需要”和“恶意软件](/windows/security/threat-protection/intelligence/criteria)”条件定义的恶意软件。

#### <a name="123-dependency-on-other-software"></a>1.2.3 依赖于其他软件

扩展可能依赖于非集成软件 (（如其他产品、模块或服务) ）来提供主要功能，前提是你在说明中披露了依赖项。

#### <a name="124-extensions-update"></a>1.2.4 扩展更新

除非 Microsoft 另有允许，否则只能通过Microsoft Edge加载项更新扩展。

### <a name="13-product-is-testable"></a>1.3 产品是可测试的

扩展必须可测试。  如果无法出于任何原因（包括但不限于以下项）测试扩展，则扩展可能会失败此要求。

#### <a name="131-user-credentials"></a>1.3.1 用户凭据

如果扩展需要登录凭据，请使用该 `Notes for certification` 字段提供有效的演示帐户。

#### <a name="132-availability-of-services"></a>1.3.2 服务可用性

如果扩展需要对服务器的访问权限，则服务器必须正常运行，以验证其是否正常工作。

### <a name="14-usability"></a>1.4 可用性

扩展必须符合Microsoft Edge加载项存储标准才能使用，包括但不限于以下子节中列出的扩展。

#### <a name="141-compatibility-across-platforms"></a>跨平台的 1.4.1 兼容性

扩展应与可下载扩展的所有设备和平台上的Microsoft Edge兼容。  如果在不兼容的设备上下载了扩展，则它应在启动时检测到该扩展，并向用户显示一条消息，详细说明设备必须满足的要求才能与扩展兼容。

#### <a name="142-user-experience"></a>1.4.2 用户体验

扩展必须立即启动，并且必须保持对用户输入的响应。  扩展必须继续运行，并保持对用户输入的响应。  你的扩展必须正常关闭，而不是意外关闭。  在处理异常后，扩展应处理异常并保持对用户输入的响应。

### <a name="15-personal-information"></a>1.5 个人信息

以下要求适用于访问个人信息的扩展。  个人信息包括标识或可用于标识人员或与此类信息或数据关联的所有信息或数据。

#### <a name="151-collect-personal-information-only-when-necessary"></a>1.5.1 仅在必要时收集个人信息

扩展可以收集、访问、使用或传输个人信息 (包括 Web 浏览活动) ;仅当需要并且仅用于突出公开的面向用户的功能时。

#### <a name="152-maintain-a-privacy-policy"></a>1.5.2 维护隐私策略

无论扩展是访问、收集还是传输个人信息，如果法律要求，必须提供重要通知并遵守隐私政策。  隐私策略必须告知用户扩展访问、收集或传输的个人信息、如何使用、存储和保护该信息，并指示向其披露该信息的当事人类型。

隐私策略必须描述用户在信息的使用和共享方面拥有的控制措施、他们如何访问其信息，并且必须遵守适用的法律和法规。  向扩展添加新功能时，必须保持最新隐私策略。

如果向 Microsoft 提供隐私策略，则你同意允许 Microsoft 与扩展用户共享此类隐私策略。

#### <a name="153-sharing-data-with-third-parties"></a>1.5.3 与第三方共享数据

只有在获得这些用户的选择加入许可后，才能通过扩展或关联的元数据将扩展用户的个人信息发布到外部服务或第三方。  选择加入许可意味着用户在你为请求的活动提供扩展的用户界面中的快速权限后：

*   向用户介绍如何访问、使用或共享信息，并指示向其披露信息的各方类型。

*   在扩展用户界面中为用户提供一种机制，通过该机制，他们可以选择以后取消权限并选择退出。

#### <a name="154-sharing-information-of-non-users"></a>1.5.4 非用户共享信息

如果通过扩展或元数据将人员的个人信息发布到外部服务或第三方，但要共享其信息的人员不是你的扩展的用户：

1.  必须获得快速书面许可才能发布该个人信息。

1.  必须允许共享其信息的人员随时撤回该同意。

1.  隐私策略必须明确披露可以以这种方式收集个人信息。

1.  如果适用法律要求，必须根据要求删除任何个人的个人信息，包括以这种方式收集其信息的个人。

1.  如果扩展为用户提供对他人个人信息的访问权限，则此要求也适用。

#### <a name="155-transmit-information-securely"></a>1.5.5 安全传输信息

如果扩展收集、存储或传输个人信息;它必须使用新式加密方法安全地执行此操作。

#### <a name="156-highly-sensitive-information"></a>1.5.6 高度敏感信息

除非信息与扩展的功能相关，否则扩展不得收集、存储或传输高度敏感的个人信息，例如运行状况或财务数据。  在收集、存储或传输此类信息之前，你的扩展还必须获得用户的明确同意。

### <a name="16-permissions"></a>1.6 权限

扩展必须仅请求运行所需的权限。  必须提供扩展工作原理的说明。  扩展必须仅按所述执行。  扩展可能不会请求超出所需功能的功能的权限并按声明运行。

### <a name="17-localization"></a>1.7 本地化

应为扩展声称支持的所有语言本地化扩展。  扩展说明的文本应以声明的每种语言进行本地化。

如果扩展已本地化，导致某些功能在本地化版本中不可用，则必须在扩展说明中明确说明或显示本地化的限制。 扩展提供的体验在它支持的所有语言中必须相当相似。

### <a name="18-financial-transactions"></a>1.8 金融交易

如果产品包括产品内购买、订阅、虚拟货币、计费功能或捕获财务信息;以下部分中的要求适用。

#### <a name="181-paid-features"></a>1.8.1 付费功能

你的扩展可能会使用户能够使用通过第三方购买机制或 API 购买的数字内容或服务。

必须使用安全的第三方购买 API 来购买物理商品或服务。  必须使用安全的第三方购买 API 来支付与任何其他服务（包括真实世界赌博或慈善捐款）相关的付款。

*   如果你的扩展用于促进或收集慈善捐款或进行促销抽奖或竞赛，则必须按照适用的法律执行此操作。

*   您还必须明确声明，Microsoft 不是此次促销活动的集资者或主办方。

*   在扩展中销售的产品内产品不得转换为任何合法有效的货币 (如美元、欧元等) 或任何实物商品或服务。

以下要求适用于使用安全的第三方购买 API：

*   在交易时或从用户处收集任何付款或财务信息时;你的扩展必须标识商务事务提供商，对用户进行身份验证，并获取交易的用户确认。  商业事务提供商维护金融交易的安全平台。

*   你的扩展可能为用户提供保存此身份验证的功能，但用户必须能够要求对每个事务进行身份验证或关闭产品内事务。

*   如果扩展收集信用卡信息或使用第三方付款处理器收集信用卡信息，则付款处理必须符合当前 PCI 数据安全标准 (PCI DSS) 。

#### <a name="182-disclosing-paid-features"></a>1.8.2 披露付费功能

扩展和关联元数据必须提供有关产品内购买类型和价格范围的信息。  不得误导用户，并且必须清楚产品内促销和产品/服务的性质，包括任何试用体验的范围和条款。

如果扩展限制在试用期间或试用后访问用户创建的内容，则必须提前通知用户。  此外，你的扩展必须向用户表明他们正在你的扩展中启动购买选项。

### <a name="19-notifications"></a>1.9 通知

扩展必须遵守通知的系统设置。  这意味着任何向用户显示广告和通知都必须与用户首选项一致，无论这些通知是由 Microsoft 推送通知服务 (MPNS) 、Windows推送通知服务 (WNS) 还是任何其他服务提供。  如果用户在特定于产品或系统范围内禁用通知，则扩展必须保持正常运行。

如果产品使用 MPNS 或 WNS 来传输通知，则必须符合以下要求：

#### <a name="191-general-guidance"></a>1.9.1 一般指南

通过 WNS 或 MPNS 提供的通知被视为产品内容，并受所有加载项目录开发人员策略的约束。

#### <a name="192-ownership-of-notifications"></a>1.9.2 通知所有权

不得遮盖或尝试掩盖从扩展发起的任何通知的源。

#### <a name="193-no-confidential-or-sensitive-information"></a>1.9.3 无机密或敏感信息

不得在通知中包含任何用户可以合理考虑机密或敏感的信息。

#### <a name="194-purpose-of-notifications"></a>1.9.4 通知用途

从扩展发送的通知必须与该扩展或在 Microsoft Edge 加载项存储中发布的其他扩展相关，并且不得包含与扩展无关的任何类型的促销消息。

### <a name="110-advertising-conduct-and-content"></a>1.10 广告行为和内容

对于所有与广告相关联的活动，应符合以下要求：

#### <a name="1101-purpose"></a>1.10.1 用途

扩展的主要内容不能是广告，广告必须与扩展中的其他内容明显区分开来。

#### <a name="1102-policies-and-agreements"></a>1.10.2 策略和协议

你的扩展显示的任何广告内容都必须遵守 [Microsoft 创意接受策略](https://about.ads.microsoft.com/solutions/ad-products/display-advertising/creative-acceptance-policies)。

如果扩展显示广告，则显示的所有内容都必须符合 [应用开发人员协议](/legal/windows/agreements/app-developer-agreement) 和此策略的广告要求。

#### <a name="1103-quality-of-advertising"></a>1.10.3 广告质量

*   扩展的主要目的不得是让用户单击广告。

*   你的扩展不得执行任何干扰或降低其显示的任何广告的可见性、值或质量的任何操作。

#### <a name="1104-promotions"></a>1.10.4 促销

如果通过 [合作伙伴中心的](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)广告市场活动功能购买或创建促销广告活动来推广扩展，则提供给 Microsoft 的所有广告材料（包括任何关联的登陆页面）都必须符合 [Microsoft 创意规范策略](https://about.ads.microsoft.com/solutions/ad-products/display-advertising/creative-specs) 和 [Microsoft 创意接受策略](https://about.ads.microsoft.com/solutions/ad-products/display-advertising/creative-acceptance-policies)。

#### <a name="1105-notifying-users-of-opt-out-for-interest-based-advertising"></a>1.10.5 通知用户Interest-Based广告Opt-Out

隐私声明或使用条款必须让用户知道你计划向广告服务提供商发送个人信息，并且必须告知用户如何选择退出基于兴趣的广告。

#### <a name="1106-other-guidelines"></a>1.10.6 其他准则

如果你的扩展针对的是13岁以下的儿童，如 [《儿童在线隐私保护法》](https://www.ftc.gov/tips-advice/business-center/privacy-and-security/children%27s-privacy)中所定义;必须在 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd) 通知 Microsoft 此事实，并确保扩展中显示的所有广告内容都适用于 13 岁以下的儿童。


<!-- ====================================================================== -->
## <a name="2-content-policies"></a>2 个内容策略

以下策略适用于内容和元数据 (包括发布者名称、扩展名称、扩展图标、扩展说明、扩展屏幕截图、扩展预告片和预告片缩略图，以及用于在Microsoft Edge加载项中分发的任何其他扩展元数据) 。  _内容_ 是指扩展中包含的图像、声音、视频和文本、通过扩展公开的磁贴、通知、错误消息或广告，以及从服务器或扩展连接到的任何内容。

由于扩展和Microsoft Edge加载项在世界各地使用，因此这些要求在区域和文化规范的上下文中得到解释和应用。

### <a name="21-content-requirements-for-microsoft-edge-add-on-catalog-listing"></a>2.1 Microsoft Edge加载项目录列表的内容要求

在扩展过程中提交的元数据和其他内容可能不包含成熟的内容。  不符合加载项存储列表要求Microsoft Edge提交将被拒绝或立即删除。

### <a name="22-content-including-names-logos-original-and-third-party"></a>2.2 内容，包括名称、徽标、原始和第三方

扩展和关联元数据中的所有内容必须最初由你创建或从第三方权利持有者获得适当许可，并且必须仅在权利持有者允许或法律允许时使用。

### <a name="23-risk-of-harm"></a>2.3 危害风险

#### <a name="231-requirements"></a>2.3.1 要求

你的扩展不得包含任何有助于或美化以下现实世界活动的内容： () 极端或无端暴力; (b) 侵犯人权： (c) 制造非法武器：或 (d) 对人、动物或实际或个人财产使用武器。

#### <a name="232-responsibility"></a>2.3.2 责任

扩展不得： () 对最终用户或任何其他人或动物造成安全风险，也不得造成不适、伤害或任何其他伤害：或 (b) 对实际或个人财产造成损害或造成损害的风险。  你完全负责所有扩展安全测试、证书获取以及任何适当功能保障措施的实现。

不得禁用任何平台安全性或舒适功能，并且必须在扩展中包含所有适用的法律要求和行业标准警告、通知和免责声明。

### <a name="24-defamatory-libelous-slanderous-and-threatening"></a>2.4 诽谤、诽谤、诽谤和威胁

你的扩展不得包含任何诽谤、诽谤、诽谤或威胁的内容。

### <a name="25-offensive-content"></a>2.5 冒犯性内容

扩展和关联的元数据不得包含潜在的敏感或冒犯性内容。  由于当地法律或文化规范，内容在某些国家/地区可能被视为敏感或冒犯性内容。  此外，你的扩展和相关元数据不得包含基于种族、种族、民族、语言、性别、年龄、残疾、宗教、性取向、退伍军人身份或任何其他社会群体成员身份而主张歧视、仇恨或暴力的内容。

### <a name="26-alcohol-tobacco-and-drugs"></a>2.6 酒精、烟草和毒品

你的扩展不得包含任何有助于或美化过度或不负责任地使用酒精、烟草制品或药物的内容。

### <a name="27-adult-content"></a>2.7 成人内容

你的扩展不得包含或显示合理人会认为色情或色情内容的内容。

### <a name="28-prohibited-content-services-and-activity"></a>2.8 禁止的内容、服务和活动

扩展必须遵循以下条件。

*   你的扩展不得包含内容或提供有助于在线赌博的服务。  网上赌博包括但不限于在线赌场、体育博彩、彩票或提供现金或其他价值奖品的技能游戏。

*   扩展不得提供对网站内容的未经授权的访问，例如绕过付费墙或登录限制。

*   扩展不得提供、鼓励或启用未经授权的访问、下载或流式传输受版权保护的内容或媒体。

*   扩展不得挖掘加密货币。

### <a name="29-illegal-activity"></a>2.9 非法活动

你的扩展不得包含在现实世界中鼓励、促进或美化非法活动的内容或功能。

### <a name="210-excessive-profanity-and-inappropriate-content"></a>2.10 过多的猥亵和不当内容

*   扩展不得包含过多或无端的亵渎行为。

*   你的扩展不得包含或显示合理人认为淫秽的内容。

### <a name="211-countryregion-specific-requirements"></a>2.11 国家/地区特定要求

不允许在扩展目标的任何国家/地区中具有攻击性的内容。  由于当地法律或文化规范，一些内容可能会在某些国家/地区视为冒犯性内容。  在某些国家/地区可能被视为具有冒犯性的内容示例包括以下各项：

**中国**

*   禁止的性内容。
*   有争议的领土或区域引用。
*   根据适用的地方法律，提供或启用对非法内容或服务的访问。

### <a name="212-age-ratings"></a>2.12 年龄分级

#### <a name="2121-mature-content"></a>2.12.1 成熟内容

将扩展提交到 [合作伙伴中心](https://partner.microsoft.com/dashboard/microsoftedge/public/login?ref=dd)时，必须指示扩展是否显示应标记为“成熟”的内容。  确定扩展的分级时，请考虑应用中的所有内容，包括用户生成的内容和广告，以及扩展链接的内容。  如果指示扩展不包含任何“成熟”内容，则负责保持此分级的准确性。

无论给扩展的分级如何，它仍必须遵守Microsoft Edge加载项开发人员策略的所有内容要求。

#### <a name="2122-ratings-change"></a>2.12.2 分级更改

如果扩展提供内容 (（例如用户生成的、零售或其他基于 Web 的内容) ，这些内容可能适用于比分配的分级更高的年龄分级，则必须要求用户通过使用内容筛选器或使用预先存在的帐户登录来选择接收此类内容。

### <a name="213-videos"></a>2.13 视频

如果在列表中提交促销视频，则应遵循此策略中提到的所有内容准则。  如果选择提供 YouTube 链接，则必须确保针对要嵌入的特定视频关闭广告。  有关在 YouTube 上打开或关闭广告的详细信息，请参阅在[嵌入的视频上](https://support.google.com/youtube/answer/132596)[设置默认广告格式](https://support.google.com/youtube/answer/2531367?ref_topic=7072227)和广告。


<!-- ====================================================================== -->
## <a name="edge-add-ons-certification-complaint-and-appeal-process"></a>Edge 加载项认证投诉和上诉流程

所有扩展都应遵循上面列出的存储策略。 如果扩展在评审过程中失败，请查看应用商店策略以了解失败的原因。 使用合作伙伴中心提交扩展后，若要询问有关其评审或认证状态的问题，请转到 [“新建支持请求](https://support.microsoft.com/supportrequestform/e7a381be-9c9a-fafb-ed76-262bc93fd9e4) ”并完成表单。

### <a name="microsoft-edge-add-ons-appeal-statistics-for-fy2021"></a>Microsoft Edge加载项吸引 2021 财年统计信息

| 主要投诉类型 #1：强制上诉 | 主要投诉类型 #2：认证结果 | 其他投诉类型 | 投诉总数 | 已推翻的投诉 |
|:--- |:--- |
| 8 | 2 | 4 | 14 | 0 |