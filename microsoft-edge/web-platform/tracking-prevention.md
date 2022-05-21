---
title: Microsoft Edge 中的跟踪防护
description: Microsoft Edge跟踪预防功能。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 01/07/2021
ms.openlocfilehash: b1fb1ebeab54f210b5f3c6c0b329f408af0f621c
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522334"
---
# <a name="tracking-prevention-in-microsoft-edge"></a>Microsoft Edge 中的跟踪防护

Microsoft Edge中的跟踪防护功能通过限制跟踪器访问基于浏览器的存储和网络的能力来保护用户免受联机跟踪。

构建跟踪防护功能是为了维护Microsoft Edge[浏览器隐私承诺](https://microsoftedgewelcome.microsoft.com/privacy)，同时确保默认情况下不会影响网站兼容性或 Web 的经济可行性。


<!-- ====================================================================== -->
## <a name="levels-of-tracking-prevention"></a>跟踪防护级别

Microsoft Edge目前为用户提供三个级别的跟踪预防，这是通过导航到`edge://settings/privacy`选择。

![跟踪防护的三个设置。](media/tracking-prevention-settings.png)

1. **基本** - 最不受限制的跟踪防护级别，专为喜欢个性化广告且不介意在 Web 上跟踪的用户设计。  基本仅保护用户免受恶意跟踪器（如指纹和加密器）的侵害。

1. **平衡 (默认) ** - 默认跟踪防护级别，专为希望查看不太个性化广告的用户设计，同时在浏览 Web 时最大程度地降低兼容性问题的风险。  平衡的目的是阻止来自用户从不参与的网站的跟踪器。

1. **严格** - 最严格的跟踪防护级别，专为交易网站兼容性以实现最大隐私性的用户而设计。

Microsoft Edge中的跟踪防护功能由三个主要组件组成，这些组件协同工作，以确定网站中的特定资源是否应分类为跟踪器并阻止。  组件如下所示：

* **分类** - Microsoft Edge确定 URL 是否属于跟踪器的方式。

* **强制** - 为保护Microsoft Edge用户免受分类为跟踪器的 URL 而采取的操作。

* **缓解 -** 提供的机制可确保用户指定的收藏网站仍可正常工作，同时提供强大的默认保护。

此页上将详细了解和解释每个组件。


<!-- ====================================================================== -->
## <a name="classification"></a>分类

Microsoft Edge中跟踪防护功能的第一个组成部分是分类。  若要对联机跟踪器进行分类并将其分组为类别，Microsoft Edge使用[断开连接](https://disconnect.me)开放源代码[跟踪保护列表](https://github.com/disconnectme/disconnect-tracking-protection)。  这些列表是通过“信任保护列表”组件传递的，可在 `edge://components`其中查看。  下载后，列表存储在磁盘上，你可以使用它们来确定是否或如何分类特定 URL。

若要确定Microsoft Edge中的分类系统是否将 URL 视为跟踪器，请检查一系列主机名，从完全匹配开始，然后继续检查顶级域之外最多四个标签的部分匹配项。

> **示例**：
>
> URL： `https://a.subdomain.of.a.known.tracker.test/some/path`
>
> 已测试主机名：
>
> *   `a.subdomain.of.a.known.tracker.test`
> *   `of.a.known.tracker.test`
> *   `a.known.tracker.test`
> *   `known.tracker.test`
> *   `tracker.test`

如果这些主机名中的任何一个与[“断开连接](https://disconnect.me)”[列表](https://github.com/disconnectme/disconnect-tracking-protection)中的主机名匹配，Microsoft Edge继续评估强制措施，以防止跟踪用户。


<!-- ====================================================================== -->
## <a name="enforcement"></a>强制

为了防止在 Web 上跟踪操作，Microsoft Edge对分类跟踪器采取两项强制措施：

*  **限制存储访问** - 如果已知跟踪资源尝试访问任何 Web 存储（其中可能尝试保留有关用户的数据），Microsoft Edge阻止该访问。  这包括限制该跟踪器获取或设置 Cookie 的功能，以及访问存储 API（例如 `IndexedDB` 和 `localStorage`）。

*  **阻止资源加载** - 如果在网站上加载已知跟踪资源，Microsoft Edge可能会在请求到达网络之前阻止该加载，具体取决于负载的兼容性影响以及用户设置的跟踪防护设置。  阻止的负载可能包括跟踪脚本、像素、iframe 等。  这可以防止任何数据可能发送到跟踪域，甚至可以改善加载时间和页面性能作为副作用。

用户可以选择地址栏左侧的页面信息浮出图标，以找出在特定页面上阻止了哪些跟踪器：

![页面信息浮出控件中阻止的跟踪器。](media/page-info-flyout.png)

如何应用强制措施取决于用户选择的跟踪防护级别以及可能适用的缓解措施。


<!-- ====================================================================== -->
## <a name="mitigations"></a>缓解措施

为了确保尽可能保持 Web 兼容性，Microsoft Edge有三种缓解措施，有助于在特定情况下平衡执法。  这些是 [组织关系缓解](#org-relationship-mitigation)、 [Org Engagement 缓解](#org-engagement-mitigation)和 [CompatExceptions 列表](#the-compatexceptions-list)。

在深入探讨缓解措施之前，有必要简而言之，定义“组织”或“组织”的概念。  [断开连接](https://disconnect.me)还维护名为 [entities.json 的](https://github.com/disconnectme/disconnect-tracking-protection/blob/master/entities.json)列表<!-- changing master to main doesn't work 5/19/2022 --> 定义同一父组织/公司拥有的 URL 组。  Microsoft Edge中的跟踪预防功能在[组织关系缓解](#org-relationship-mitigation)和 [Org Engagement 缓解](#org-engagement-mitigation)措施中都使用此列表，以尽量减少跟踪预防影响跨组织请求导致的兼容性问题的发生。

### <a name="org-relationship-mitigation"></a>组织关系缓解

一些热门网站维护网站和内容分发网络 (CDN) 为这些网站提供静态资源和内容。  若要确保这些类型的方案不受跟踪防护的影响，Microsoft Edge在站点向同一父组织拥有的其他站点发出第三方请求时，Microsoft Edge将免除对同一父组织拥有的其他站点的跟踪防护， (在 [Disconnect entities.json 列表](https://github.com/disconnectme/disconnect-tracking-protection/blob/master/entities.json)) 中定义。  此示例最能说明这一点。

> **示例：**
>
> 名为 Org1 的组织拥有域 `org1.test` ，并且 `org1-cdn.test`在 [Disconnect entities.json 列表](https://github.com/disconnectme/disconnect-tracking-protection/blob/master/entities.json)中定义。  `org1-cdn.test` Imagine分类为跟踪程序，并且通常会应用跟踪预防强制措施。  如果用户访问`https://org1.test`并尝试从`https://org1-cdn.test`站点加载资源，Microsoft Edge不会对向其发出的请求执行`org1-cdn.test`任何强制措施，即使它不是第一方 URL。  但是，如果不是 Org1 组织一部分的另一个 URL 尝试加载同一资源，则请求将受到强制执行，因为它不是同一组织的一部分。
>
> 尽管这放宽了对属于同一组织的网站的跟踪预防强制措施，但这不太可能带来很高的隐私风险，因为此类组织能够确定你访问过 `https://org1.test` 的网站/资源以及 `https://org1-cdn.test` 使用内部后端数据。

### <a name="org-engagement-mitigation"></a>组织参与缓解

创建组织参与缓解措施的目的是通过确保用户充分参与的组织拥有的网站在 Web 上继续按预期工作，从而最大程度地降低通过跟踪防护引入的兼容性风险。  每当用户与给定网站建立当前由 4.1 或更高) 的网站参与分数定义的持续 (关系时，它就会利用 [网站参与](https://www.chromium.org/developers/design-documents/site-engagement) 来放宽强制执行。  示例再次说明了这一点：

> **示例：**
>
> 一个名为 Social Org 的组织拥有域和`social-videos.example`域`social.example`。
>
> 如果用户已与社交组织拥有的任何一个域建立了 4.1 或更高的网站参与分数，则被视为与 Social Org 有关系。
>
> 如果另一个网站 `https://content-embedder.example`包含第三方内容， (说来自社交组织拥有的任何域的嵌入式视频 `social-videos.example`) ，通常会受到跟踪预防执法的限制，只要社交组织拥有的域的用户网站参与分数保持在阈值以上，该网站就可以免于跟踪预防执法。
>
> 如果网站不属于组织，则用户必须直接使用它建立 4.1 或更高的网站参与分数，然后才能放宽通过跟踪防护施加的任何存储访问/资源负载块。

组织参与缓解目前仅在均衡模式下应用，因此Microsoft Edge为选择“严格”的用户提供尽可能高的保护。

### <a name="the-compatexceptions-list"></a>CompatExceptions 列表

根据 Microsoft 最近收到的用户反馈，Microsoft Edge维护一小部分网站列表 (其中大多数位于“断开连接内容”类别) 中，尽管存在上述两种缓解措施，但由于跟踪防护而中断。 此列表中的站点不受跟踪预防执法的约束。  可以在磁盘上找到下述 [位置](#determining-whetherhow-a-particular-url-is-classified) 的列表。  用户可以使用“ **阻止** ”选项 `edge://settings/content/cookies`替代其上的条目。

为了避免保持此列表向前移动，Microsoft 目前正在开源代码库中处理[存储访问 API](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/master/StorageAccessAPI/explainer.md)。  [存储访问 API](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/master/StorageAccessAPI/explainer.md) 为网站开发人员提供了一种直接向用户请求存储访问权限的方法，使用户能够更透明地了解其隐私设置如何影响其浏览体验，并使网站开发人员能够快速直观地取消阻止自己。

[实现存储访问 API](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/master/StorageAccessAPI/explainer.md) 后，Microsoft 将弃用 CompatExceptions 列表，并联系受影响的站点，让他们了解问题，并请求他们使用[存储访问 API](https://github.com/MicrosoftEdge/MSEdgeExplainers/blob/master/StorageAccessAPI/explainer.md)。


<!-- ====================================================================== -->
## <a name="current-tracking-prevention-behavior"></a>当前跟踪防护行为

下表显示了应用于Microsoft Edge中分类跟踪器的每个类别的强制操作和缓解措施。

*  顶部是 [断开连接跟踪保护列表类别](https://github.com/disconnectme/disconnect-tracking-protection/blob/master/services.json)定义的跟踪器类别。
*  左侧是Microsoft Edge (基本、均衡和严格) 的跟踪预防三个级别。
*  该字母 `S` 指示存储访问被阻止。
*  该字母 `B` 指示存储访问和资源加载 (，如网络请求) 被阻止。
*  连字符 (`-`) 指示不会对存储访问或资源加载应用任何块。

| | 广告 | 分析 | 内容 | 加密 | 指纹 | 社交 | Other | 同一组织缓解 | 组织参与缓解 |
| - | - | - | - | - | - | - | - | - | - | - |
| **基本** | - | - | - | B | B | - | - | 启用 | 不适用 |
| **平衡** | S | - | S | B | B | S | S | 已启用 | 已启用 |
| **“严格”** | B | B | S | B | B | B | B | 已启用 | 禁用 |

> [!NOTE]
> 组织参与缓解不适用于加密或指纹类别。

> [!TIP]
> 严格模式阻止比均衡更多的资源负载。  阻止更多的资源加载可能会导致“严格”模式似乎阻止的跟踪请求比均衡的要少，因为发出请求的跟踪器从未加载过。

> [!NOTE]
> [当前跟踪防护行为](#current-tracking-prevention-behavior)中的指纹列是指除了另一个列表之外，指纹列表中的跟踪器。  仅出现在指纹列表上的跟踪器被视为非恶意指纹识别器，不会被阻止。

### <a name="inprivate-behavior"></a>InPrivate 行为

在 Microsoft Edge 79 中，默认行为是在 InPrivate 中应用严格模式保护。  在 Microsoft Edge 80 中，此行为被一个开关所取代，该开关`edge://settings/privacy`允许用户在浏览 InPrivate 时决定是否应用严格模式保护或保留其常规设置。


<!-- ====================================================================== -->
## <a name="determining-whetherhow-a-particular-url-is-classified"></a>确定是否/如何分类特定 URL

若要确定特定 URL 是否分类为已知跟踪器，

1. 打开 DevTools 并打开 **控制台** 工具。

1. 刷新网页。

   你可能想要先清除 **Cookie 和其他站点数据** ，以重置网站参与度分数并确保完全干净。

1. 查找读取 `Tracking Prevention blocked access to storage for <URL>`的任何消息。  可以展开消息以查看被阻止的单个 URL。

1. 如果需要确定特定被阻止网站属于哪个类别，则最简单的方法是在 [Disconnect services.json 列表](https://github.com/disconnectme/disconnect-tracking-protection/blob/master/services.json)中搜索它。  条目按字母顺序排列，因此，滚动到网站条目的块顶部可查找特定网站的特定类别。

### <a name="access-tracking-prevention-lists-stored-on-disk"></a>存储在磁盘上的访问跟踪防护列表

如果需要访问存储在磁盘上的跟踪防护列表，可以在以下两个位置之一找到每个列表：

**基于组件的更新** - 从“信任保护列表”组件下载的列表

窗口： `%LOCALAPPDATA%\Microsoft\Edge <OptionalChannelName>\User Data\Trust Protection Lists`

macOS： `~/Library/Application Support/Microsoft Edge <OptionalChannelName>/Trust Protection Lists`

**安装目录** - 与Microsoft Edge安装程序捆绑的列表。  如果选择了不同的安装目录，则确切路径可能有所不同。

窗口： `%PROGRAMFILES(x86)%\Microsoft\ Edge <OptionalChannelName>\Application<Version>\Trust Protection Lists`

macOS： `/Applications/Microsoft Edge.app/Contents/Frameworks/Microsoft Edge Framework.framework/Libraries/Trust Protection Lists`


<!-- ====================================================================== -->
## <a name="frequently-asked-questions"></a>常见问题

以下部分包含有关Microsoft Edge中跟踪预防功能的常见问题的解答。

**是否有方法可以阻止或允许特定跟踪器进行调试？**

目前，Microsoft Edge只公开一个选项，禁止跟踪预防强制措施在指定的站点上运行。  此选项通过页面信息浮出控件或页面 `edge://settings/privacy/trackingPreventionExceptions` 访问。

也就是说，页面上的`edge://settings/content/cookies`**“阻止**和**允许**”选项可用于允许或拒绝特定域对存储（如 Cookie 和其他浏览器存储机制）的访问。  这对于调试因跟踪阻止访问特定站点的存储而导致的站点问题非常有用。
