---
title: Microsoft Edge 隐私白皮书
description: Microsoft Edge 隐私白皮书。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.localizationpriority: high
no-loc:
- Cast
- Google Cast
ms.date: 12/10/2021
ms.openlocfilehash: b0832b8ada5b7c4d4a15b7df0528a6868708b9d4
ms.sourcegitcommit: 82de2fa19bf9c925ff5faafe8be6b24d21767e03
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2022
ms.locfileid: "12346482"
---
# <a name="microsoft-edge-privacy-whitepaper"></a>Microsoft Edge 隐私白皮书

我们的浏览器隐私承诺旨在向你提供应获得的保护、透明度、控制权和尊重。  为了履行承诺，让你在 Microsoft 产品中保持透明度，Microsoft Edge团队提供了此隐私白皮书。 它介绍了Microsoft Edge功能和服务的工作原理，以及每项功能和服务如何影响你的隐私。  Microsoft Edge团队的目标是使你全面了解数据的使用方式、如何控制不同的功能以及如何管理收集的数据。 阅读本文档后，你将获得为你做出正确隐私决策所需的信息。

本文档提供了导航到Microsoft Edge设置和其他页面的链接。  快捷方式 URL 以 `edge://`如 `edge://favorites`和 `edge://settings/privacy`开头。  若要转到页面，请直接在 Microsoft Edge 地址栏中输入粗体文本。  页面仅可在 Microsoft Edge 中查看。

本白皮书重点介绍桌面版的Microsoft Edge。 文档的某些部分可能包含并非面向所有用户的功能或体验。  本白皮书还讨论了当前产品中存在的功能和服务，但将来可能会发生更改。  Microsoft 实践数据收集最小化。 数据将保留最短时间。  保留时间因功能或服务而异，并且可能会随时间而变化。


<!-- ====================================================================== -->
## <a name="address-bar-and-suggestions"></a>地址栏和建议

通过地址栏，可输入网站 URL 并搜索 Web。  默认情况下，地址栏使用输入的字符提供搜索和网站建议。  建议来自收藏夹、浏览历史记录、以前的搜索和默认搜索提供程序。

:::image type="complex" source="./media/address-bar.png" alt-text="地址栏。" lightbox="./media/address-bar.png":::
   地址栏
:::image-end:::

为了加快浏览和搜索速度，键入地址栏中的字符将发送到默认搜索提供程序。 搜索提供程序返回建议的搜索查询。

地址栏将条目分类为 URL、搜索或未知。  此信息以及你选择的建议、所选位置和其他地址栏数据将发送到默认搜索提供程序。

如果搜索提供程序是必应，则会随数据一起发送浏览器特有的可重置标识符。 它可帮助必应了解搜索查询和查询会话。 其他自动建议服务标识符将发送到你的默认搜索引擎，以完成搜索建议。 将你的 IP 地址和 cookie 发送到你的默认搜索提供程序，以提高搜索结果的相关性。

选择地址栏时，会向默认搜索提供程序发送信号。 信号指示提供程序准备建议。  输入的字符和搜索查询不会发送给 Microsoft，除非你的搜索提供程序是必应。  若要启用将数据发送到默认搜索提供程序，请导航到 `edge://settings/privacy`。 在**Services**中，选择**地址栏**并打开**使用我键入的字符显示搜索和网站建议**设置。  如果禁用此设置，则输入的字符将不再发送到默认搜索提供程序。  搜索查询仍将发送到默认搜索提供程序，以提供搜索结果。

<!-- The Privacy settings have been updated from what is described here -->

如果Microsoft Edge检测到地址栏中可能包含敏感信息的键入，则不会发送键入的文本。 敏感信息包括身份验证凭据、本地文件名或通常加密的 URL 数据。

可以将Microsoft Edge配置为收集有关地址栏的诊断数据。 收集的数据包括为所有搜索提供程序提供的查询数。 导航到 `edge://settings/privacy`。 在 **"个性化 Web 体验** "中， **通过允许 Microsoft 使用此帐户中的浏览历史记录个性化广告、搜索、新闻和其他Microsoft 服务设置，** 开启"改善 Web 体验"。

键入的字符和访问的网站存储在每个配置文件上的本地设备上。  若要删除数据，请导航到 `edge://settings/clearBrowserData`。 在**Clear 浏览数据**窗口中，选中**浏览历史记录**复选框，然后选中 **"立即清除**按钮。

如果必应是默认搜索提供程序并且你已登录，则可以通过 [Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)删除搜索。  可以清除浏览历史记录，并删除在地址栏中显示为建议的网站。 导航到 `edge://history`，然后选择 **"清除浏览数据**"。  你可以从地址栏中删除 Microsoft 收集的数据，并在Windows 10及更高版本上搜索建议功能。 打开 **"开始** > **设置**" > **隐私** > **诊断和反馈**。 在 **"删除诊断数据**"中，选择 **"删除**"。  所有其他数据将在 36 个月后删除。

<!-- Deleting diagnostic data could use rewrite -->

如果你使用 Microsoft 工作或学校帐户登录到Microsoft Edge，并且 Microsoft 搜索可用，则可以使用特定于帐户的搜索函数。 Microsoft 可能会向你的查询发送匿名令牌，以提供特定于帐户的功能，例如特定于公司的结果。

所有数据均通过 HTTPS 安全传输。  如果[必应](https://bing.com)是默认搜索提供程序，则搜索和输入的字符最多保存 6 个月。

如果在地址框中搜索单个字词，Microsoft Edge可能会将单个单词发送到 DNS 服务器。 发送单个字词是检查它是否对应于网络上的主机。 如果是这样，Microsoft Edge可能会尝试连接到相应的主机。 此选项允许你导航到特定主机，而不是搜索。  例如，如果路由器使用主机名 `router`并且在地址栏中键入 `router`， 可以导航到 `https://router`，或搜索单词 `router`。  该功能不受“**使用我输入的字符显示搜索和网站建议**”设置控制，因为它不会将数据发送到默认搜索引擎。

可以控制是否将类型化字符发送到默认搜索提供程序。 导航到 `edge://settings/search`。 **使用我键入的字符设置切换"显示搜索和网站建议**"。

<!-- The Search settings seem different from what is described here -->

可以更改默认搜索引擎。 导航到 `edge://settings/search`。  选择“**地址栏中使用的搜索引擎**”下拉菜单。  如果在使用 **InPrivate** 或 **来宾** 模式时进行浏览，则会关闭自动建议。  **InPrivate**显示来自本地浏览的建议，例如浏览历史记录和过去的搜索。 不会将任何类型化字符发送到默认搜索引擎。  **来宾**模式不会显示任何建议，或将输入的字符发送到默认搜索引擎。

其他搜索提供程序收集的数据遵循公司的隐私策略。


<!-- ====================================================================== -->
## <a name="autofill"></a>自动填充

自动填充Microsoft Edge可保存表单条目数据。 表单条目数据包括密码、付款信息、地址和其他数据（如生日）。 访问网站并开始填写表单时，Microsoft Edge使用表单填充信息将保存的自动填充数据与窗体匹配。  Microsoft Edge提供以前在打开类似表单时保存的表单条目数据。  密码和信用卡信息仅在你对每个密码和卡的显式权限下保存。

默认情况下，将保存地址和其他表单项。  若要控制地址和其他窗体数据的保存和自动填充，请导航到。 `edge://settings/profiles` 选择**个人信息**并切换**保存和填充个人信息**设置。

<!-- The addresses settings have been moved to Profiles and updated from what is described here -->

可以阻止Microsoft Edge提示你保存密码。 导航到 `edge://settings/passwords`。 关闭**Offer 以保存密码**设置。  可以阻止Microsoft Edge对保存的密码使用自动填充并删除保存的密码。 导航到`edge://settings/passwords`，然后选择 **"已保存的密码"。**  若要删除所有自动填充数据，请导航到 `edge://settings/clearBrowserData`，选择“自动填充表单数据”****，选择所需的时间范围，然后选择“立即清除”****。

如果已登录并同步，则自动填充数据将同步到使用相同凭据登录的所有Microsoft Edge版本。  同步时，所有自动填充数据都存储在加密的 Microsoft 服务器上。  存储在 Microsoft 服务器上的自动填充数据仅用于同步目的。  可以关闭自动填充数据的同步。 导航到 `edge://settings/profiles/sync` 并关闭 **"基本信息** "切换。 如果同步已启用以进行自动填充，则在登录到Microsoft Edge时从设备中删除自动填充数据会从使用相同凭据登录的所有其他设备中删除数据。

访问网页并提交表单时，Microsoft Edge向 Microsoft 表单填充服务发送有关表单的信息。 此信息包括主机名和自动填充条目的哈希。 例如，文本框 1 需要电子邮件地址，文本框 2 需要密码，等等。  不会向服务发送用户输入的信息或用户标识符。  这些信息有助于Microsoft Edge正确标识不同网页的表单。  数据用于帮助将已保存的自动填充数据与表单匹配。

在 **来宾** 模式下，自动填充不可用，并且不会添加新的自动填充条目。  对于 **InPrivate** 模式，Microsoft Edge 提供自动填充条目，但不会添加新的自动填充条目。


<!-- ====================================================================== -->
## Cast

Cast 在 Microsoft Edge 中，可以使用 Google Cast将媒体显示到另一个屏幕。  若要访问 Cast，请打开**设置和更多 (...)** > **更多工具** > **Cast介质到设备**。  Cast 依赖于未随Microsoft Edge自动安装的媒体路由器扩展。  第一次使用 Cast 时，Microsoft Edge 会提示你允许安装媒体路由器扩展。

选择“**重启**”，从 Chrome Web Store 安装媒体路由器扩展。 启动时，Microsoft Edge定期向Chrome Web Store发送更新请求。 更新请求包括有关Microsoft Edge版本的基本数据。 定期更新请求使媒体路由器扩展保持最新。

Google 可能会收集一些与媒体路由器扩展相关联的数据。 若要卸载媒体路由器扩展，请导航到 `edge://flags#edge-on-demand-media-router`并更改设置。 卸载也会停止来自Chrome Web Store的更新。 扩展已隐藏，且不会显示在“安装的扩展”**** 列表中。 有关“安装的扩展”**** 列表，请导航到 `edge://extensions`。


<!-- ====================================================================== -->
## <a name="collections"></a>集锦

可以从 Web 收集网站、文本和图像，并在Microsoft Edge中使用"集合"组织内容。  所有集合数据均本地存储在设备上，并按 Microsoft Edge 配置文件进行组织。  如果已为集合启用同步，则集合、备注和注释可在所有已登录和同步版本的Microsoft Edge中使用。

每 24 小时，Microsoft Edge下载具有特殊实体提取模板的支持站点的列表。 这些模板特定于各个网站。 在集合中创建新项时，Microsoft Edge验证要从中收集的网站是否在受支持的网站列表中。 如果站点在列表中，Microsoft Edge对特定站点模板的实体提取服务执行 ping 操作。 没有用户标识符与服务请求相关联。 该模板尝试识别有关所收集项目的名称、价格、评级、主图像和其他数据。 如果要从中收集的网站不在受支持的列表站点上，Microsoft Edge不会下载模板。 模板允许在设备上本地创建集合项。 创建集合时，不会向服务发送有关集合项的数据。

可以删除存储在设备上的模板并清除缓存数据。 导航到 `edge://settings/privacy`。 在**Clear 浏览数据**旁边的**现在浏览数据**，选择**选择要清除的内容**按钮。 选择所需的时间范围和数据类型，然后选择 **"立即清除**按钮。  另一种删除缓存数据的方法是，导航到 `edge://settings/clearBrowserData`，选择所需的时间范围和数据类型，然后选择“立即清除”**** 按钮。

<!-- Above, should pick one way. Check UI for privacy updates -->


在 Microsoft 必应中搜索时，可以使用集合的标题查找相关的 Pinterest 主题页面。 导航到 `edge://settings/privacy`。 在 Collections 中打开**显示来自 Pinterest 的建议**设置。 Microsoft Edge 不会向 Pinterest 发送有关集锦的数据。 可以删除建议并停止搜索 Pinterest 主题页面。 导航到 `edge://settings/privacy` 并关闭 **“在收藏夹中显示来自 Pinterest 的建议”** 设置。
使用 **InPrivate** 或 **来宾** 模式时，集合不可用。


<!-- ====================================================================== -->
## <a name="crashes"></a>故障

如果启用了可选诊断数据（包括崩溃报告），则在意外崩溃或关闭Microsoft Edge时收集诊断数据。 诊断数据用于诊断和修复Microsoft Edge和其他 Microsoft 产品和服务的问题。

:::image type="complex" source="./media/crashes2.png" alt-text="故障。" lightbox="./media/crashes2.png":::
   故障
:::image-end:::

收集的诊断数据采用故障转储的形式，其中包含在崩溃或关闭Microsoft Edge时捕获的设备和软件状态。 故障转储包含有关在遇到可靠性问题时所发生的情况的信息。 诊断数据中可能包含在出现故障时正在访问的网站或 CPU 使用情况等信息。 如果故障报告已打开，则故障转储将本地存储在设备上，并使用加密链接发送到 Microsoft。

每个故障转储都包含设备特有的标识符和浏览器特有的可重置标识符。 它还包括额外的诊断数据，例如 URL、CPU 使用情况和网络使用情况，以帮助识别问题。 额外的诊断数据可帮助 Microsoft 确定遇到问题的设备数量和严重性。

故障转储将存储在安全的 Microsoft 服务器上长达 30 天，然后将其删除。  你可以请求删除Windows 10及更高版本设备上的诊断数据。 打开 **"开始** > **设置**" > **隐私** > **诊断和反馈**。 在 **"删除诊断数据**"中，选择 **"删除**"。 将存储聚合故障信息（例如发生故障的类型的计数）用于报告和产品改进。

可以清除本地存储在设备上的故障诊断数据。 导航到 `edge://crashes` 并选择" **全部清除** "按钮。

若要在Windows 10及更高版本上关闭故障诊断数据收集，请打开 **"开始** > **设置** > **""隐私**"，然后选择 **"诊断和反馈**"。  对于所有其他平台上的 Microsoft Edge 版本，请导航到 `edge://settings/privacy`，然后禁用“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品”**** 设置。 可以在企业级别管理诊断数据收集。 导航到[组织管理的组策略](/deployedge/microsoft-edge-enterprise-privacy-settings)。


<!-- ====================================================================== -->
## <a name="developer-tools"></a>开发人员工具

Microsoft Edge 开发人员工具有关网站调试和测试的帮助。 打开 **"设置"等 （...）** > **更多工具**，然后选择**开发人员工具。** 在开发人员工具中启用某些功能时，Microsoft Edge从 Microsoft 服务器请求模块并将其下载到设备。 请求通过安全的 HTTPS 连接发送，并包含表示Microsoft Edge版本的非唯一标识符。 需要远程下载的特定体验包括 3D 视图和"元素工具辅助功能"窗格。 Webhint 集成需要在打开开发人员工具时自动请求的远程模块。


<!-- ====================================================================== -->
## <a name="diagnostic-data"></a>诊断数据

Microsoft 使用诊断数据来改进产品和服务。 诊断数据还用于确保产品安全、最新并按预期运行。 Microsoft 认可并践行信息收集最小化。 我们力求仅收集所需的信息，并仅根据需要存储这些信息来改进产品和服务。

Microsoft Edge收集一组必需的诊断数据，以确保产品安全、更新和正常运行。 所需的诊断数据包括设备连接、配置信息、软件设置和清单。 Microsoft 使用此诊断数据来解决问题，并使 Microsoft 产品和服务可靠、安全且正常运行。 如需详细了解所管理设备的诊断数据，请导航到[在组织中配置 Windows 诊断数据](/windows/privacy/configure-windows-diagnostic-data-in-your-organization)和 [Microsoft Edge 诊断数据组策略](/deployedge/microsoft-edge-enterprise-privacy-settings)。

:::image type="complex" source="./media/diagnostic-data2.png" alt-text="诊断数据。" lightbox="./media/diagnostic-data2.png":::
   诊断数据
:::image-end:::

还可以选择共享可选诊断数据。 使用Microsoft Edge功能和服务或其他使用Microsoft Edge Web 平台的应用程序时，Microsoft Edge发送有关如何使用这些功能和所访问的网站的可选诊断数据。 在你同意后，此可选诊断数据将发送给 Microsoft，以便为每个人改进产品和服务。 此数据的收集或存储不会涉及你的 Microsoft 帐户。

可选诊断数据包括功能使用情况、性能数据、站点加载时间、内存使用情况和你访问的网站。 例如，如果选择网站作为收藏，则会发送可选诊断数据。 它包括已选择收藏按钮，并且已成功添加收藏夹，但未将哪个网站设置为收藏夹。

有关你在 Microsoft Edge 中访问的网站的信息可帮助我们了解网站的加载速度，并为所有用户提高搜索结果的相关性。 数据包括有关网站的信息，例如所访问的页面的 URL、网站指标、页面标题、访问页面的方式、有关页面内容的信息以及有关页面导航的其他相关信息。

诊断数据将使用 HTTPS 发送，并存储在 Microsoft 服务器上。 在 Windows 设备上，在发送诊断数据时将随同发送设备所特有的识符。 在其他设备上，诊断数据与浏览器特有的可重置标识符相关联。 该标识符是随机生成的，不包含你的个人信息。

Microsoft Edge 团队通过限制数据访问或删除个人身份信息来尊重诊断数据的敏感性。 若要在Windows 10及更高版本的设备上重置浏览器特有的标识符，请导航到 **"开始** > **设置** > **隐私** > **诊断和反馈**"，然后在"**删除诊断数据**"下选择"**删除**"，或将**诊断数据**下的设置从 **"完整**"更改为 **"基本**"或关闭 **"可选诊断数据**"。

在其他平台上，若要生成浏览器特有的新的可重置标识符 (ID) ，请导航到 `edge://settings/privacy` 并关闭**通过发送有关浏览器、访问的网站和崩溃报告使用方式的可选诊断数据来帮助改进 Microsoft 产品**设置。 对于由组织设置的组策略管理的设备，重置 (ID) 功能可能有所不同。

如果你使用的是 Windows 10 版本 1803（2018 年 4 月更新）或更高版本，若要在诊断数据查看器中查看与 Microsoft 共享的产品数据，请导航到“开始****” > “设置****” > “隐私****” > “诊断和反馈****”，然后在“查看诊断数据****”下选择“打开诊断数据查看器****”。

对于其他平台或 Windows 10 版本 1803 及更低版本，，请导航到 `edge://data-viewer` 查看诊断数据。 若要查看自上次打开查看器后定期发送到 Microsoft 的数据，请导航到 `edge://data-viewer`。 若要查看特定会话的哪些数据发送到 Microsoft，请刷新查看器。 用于填充 `edge://data-viewer` 的数据本地存储在设备上。 若要清除查看器中的数据，请关闭 `edge://data-viewer` 选项卡。

为了帮助我们改进 Microsoft 产品和服务，将聚合诊断数据，并删除个人标识符，并存储长达两年。 由于不会从 Microsoft 帐户中收集或保存诊断数据，因此可能无法从“[Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)”查看或删除诊断数据。 若要删除Windows 10及更高版本上的诊断数据，请导航到 **"开始** > **设置** > **隐私** > **诊断和反馈**"，**然后在"****删除诊断数据**"下选择"删除"。 仅 Windows 10 版本 1803 或更高版本支持删除诊断数据功能。 有关详细信息，请导航到 [Windows 10及更高版本中的诊断、反馈和隐私](https://support.microsoft.com/help/4468236)。

对于Windows 10及更高版本的Microsoft Edge，发送可选诊断数据由Windows 诊断数据设置确定。 该设置会反映在 `edge://settings/privacy` 中。 转到“开始****” > “设置****” > “隐私****” > “诊断和反馈****”，以更改 Windows 设置。 在所有其他平台上，若要控制诊断数据的集合，请导航到 `edge://settings/privacy`，然后启用或禁用“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品****”。 该设置用于与设备上安装 Microsoft Edge 相关联的所有配置文件。  此设置不会跨设备同步。 此设置适用于 **InPrivate** 浏览和来宾模式。 浏览 **InPrivate** 或来 **宾** 模式时，绝不会发送有关你访问的网站的信息。 如果设备使用组织设置的组策略进行管理，请参阅 `edge://settings/privacy`中所述。


<!-- ====================================================================== -->
## <a name="digital-rights-management-and-media-licenses"></a>数字版权管理和媒体许可证

当网站提供受数字版权管理 (DRM) 保护的媒体内容时，Microsoft Edge 使用安全播放管道确保内容不会不正确地查看或复制。 作为该功能的一部分，Microsoft Edge可能会在设备上存储与 DRM 相关的数据，包括唯一标识符和媒体许可证。 Microsoft Edge还可以将唯一标识符传输到内容提供程序指定的媒体授权服务器。 使用网站时，Microsoft Edge检索 DRM 信息，以确保你有权使用该内容。 数据可帮助验证对受保护内容的访问权限，并确保无缝媒体体验。

Microsoft Edge 支持使用适用于 HTML5 网站的加密媒体扩展 API (EME API) 的 DRM。  EME API 允许网站与名为“内容解密模块 (CDM)”的 DRM 提供商进行通信。 开发人员的 CDM 实施可能支持其他 DRM 系统（例如，Google 的 Widevine 或 Microsoft 的 PlayReady）。  内容提供商可以选择支持一个或多个潜在的 DRM 系统。 提供程序可以使用 EME API 的功能来确定要用于特定客户端的 DRM 系统。 有关 EME 隐私的详细信息，请导航到[加密媒体扩展隐私](https://w3.org/TR/encrypted-media#privacy)。

Microsoft Edge仅在Windows 10及更高版本上支持 PlayReady DRM。 PlayReady 是一种 DRM 实现，可提供 4K 视频和 Dolby Atmos 音频等媒体体验。  Microsoft Edge 使用 Windows 平台媒体基础 API 来支持 PlayReady。  若要验证对受保护内容的访问权限，Microsoft Edge使用Windows 10或 Windows 11 操作系统。 Windows 使用唯一标识符 (ID)，并将 ID 与 PlayReady 服务通信。  在设备上持久保存的 PlayReady 的所有 EME、CDM 和浏览器数据都将存储在 Microsoft Edge 中并保留。  有关 PlayReady 的详细信息，请导航到[简易端到端系统](/playready/overview/simple-end-to-end-system)。

Microsoft Edge 支持 Google DRM 的 Widevine，默认情况下，此选项处于启用状态。  Microsoft Edge 定期从 Google 服务器获取 Widevine 更新。  使用 Widevine 可能包括与 Google 的通信。  若要选择退出使用 Microsoft Edge 中的 Widevine，请导航到 `edge://flags/#edge-widevine-drm` 并禁用 Widevine DRM 设置。  Widevine 可创建唯一的设备标识符并将其传输到 Google。  有关 Widevine 和隐私的更多详细信息，请导航到 Google 隐私策略。

Microsoft Edge 支持 Adobe 的 Flash Access DRM，由某些网站使用，而不是由 HTML5 使用。 当站点请求 Adobe Flash 时，系统会提示你允许它。  当网站使用 Adobe 的 Flash Access DRM 时，Microsoft Edge 将为 Adobe 提供对唯一设备标识符的访问权限。  可以清除和重置标识符的任何本地存储实例。 导航到 `edge://settings/privacy`。 在 **"清除浏览数据"中**。 选择**选择要清除的内容**，选中**Cookies 和其他站点数据**的复选框，然后选择**Clear now**删除任何存储的标识符。 若要阻止使用 Adobe Flash DRM，请导航到 `edge://settings/content/flash`。

当你请求访问加密的 HTML5 媒体（如在线电影）时，Microsoft Edge创建一个许可证请求来解密媒体。 正在使用的 CDM 创建包含请求 ID 的许可证请求。 请求将发送到许可证服务器。  许可证请求的任何部分都不包含任何个人数据，并且许可证请求不存储在设备上。

返回媒体许可证时，将创建一个媒体标识符，该标识符是用户和网站所特有的。  ID 不在网站之间共享，并且因每个网站而异。  用于识别播放会话的会话 ID 将与媒体标识符一起发送，用于解密媒体。  媒体标识符本地存储在设备上，可随内容提供商一起存储。

若要控制 DRM 和内容保护，请导航到 `edge://settings/content/protectedContent`。 切换**允许网站播放受保护内容（推荐）** 并**允许受保护内容的标识符（可能需要重新启动计算机）** 设置。

*   **允许网站播放受保护的内容**设置控制基于 CDM 的 DRM 系统（如 PlayReady 和 Widevine）的播放，但不控制基于非 CDM 的系统（如 Flash Access DRM）的播放。  若要管理 Flash 网站权限，请导航到 `edge://settings/content/flash`。  关闭设置会导致媒体函数停止正常工作。
*   禁用“**允许对受保护的内容使用标识符**”设置将阻止为 Flash Access DRM 创建标识符，并阻止 Widevine 定期提取 Google 中的更新。  关闭设置可能会导致某些网站上的媒体函数停止正常工作。


<!-- ====================================================================== -->
## <a name="do-not-track"></a>禁止跟踪

可以在Microsoft Edge上启用**禁止跟踪**。 导航到 `edge://settings/privacy`。 打开 **"发送"禁止跟踪"请求** 设置。  如果启用**禁止跟踪**功能，Microsoft Edge使用传出的 `DNT:1 HTTP` HTTP、HTTPS 和 SPDY 浏览流量请求发送头。 此功能告知你访问的网站不要使用跟踪器。 但是，启用**发送“禁止跟踪”请求**设置并不能保证网站无法跟踪你。 某些网站可能会通过向你显示非以前浏览过的广告来接受请求。 Microsoft Edge不控制是否接受请求。 可帮助防止网站跟踪你。 导航到 `edge://settings/privacy`。 将**跟踪防护**设置更改为**Balanced** 或**Strict**。

使用 **来宾** 模式时，Microsoft Edge不会发送 **禁止跟踪** 请求。  使用 **InPrivate** 浏览时，Microsoft Edge仅 **在** 为正在使用的配置文件启用 **"发送""禁止跟踪"请求** 设置时发送禁止跟踪请求。


<!-- ====================================================================== -->
## <a name="downloads"></a>下载

借助 Microsoft Edge，可安全可靠地下载文件。  若要选择在设备上下载文件的位置，请导航到 `edge://settings/downloads`。  如果启用 SmartScreen，则文件的相关信息（如文件名和 URL）将发送到 SmartScreen 以检查文件的信誉。 信誉检查可帮助你避免意外下载会损害设备的已知恶意软件。  若要更改 SmartScreen 设置，请导航到 `edge://settings/privacy` 并切换 SmartScreen。 有关 SmartScreen 的详细信息，请导航到 [SmartScreen](#smartscreen) 部分。

若要查看先前下载的历史记录，请导航到 `edge://downloads`。  若要清除浏览数据并删除下载历史记录，请导航到 `edge://settings/clearBrowserData`。  从 Microsoft Edge 中删除下载历史记录不会删除设备中的文件。  从设备中删除下载的文件不会从下载历史记录中删除文件。  使用 **InPrivate** 浏览或 **来宾** 模式时，关闭 **InPrivate** 或来 **宾** 窗口时，会清除会话中的下载历史记录。 文件仍保存在设备上。


<!-- ====================================================================== -->
## <a name="extensions-and-microsoft-edge-add-ons"></a>扩展和 Microsoft Edge 加载项

可以在Microsoft Edge中安装扩展，以将函数添加到浏览器。 从 Microsoft Edge 加载项网站或其他扩展存储中安装扩展时，Microsoft 会收集扩展信息，帮助开发人员和 Microsoft 了解如何使用扩展。 Microsoft Edge 收集聚合数据，包括扩展的下载次数和有关其执行方式的信息（如故障数据）。 Microsoft 将与扩展的开发人员共享聚合数据。

来自用户的评论和意见在加载项网站上是公开的，并且也会与开发人员共享。 如果你已登录到 Microsoft Edge，则Microsoft Edge加载项网站中安装的扩展将与你的帐户相关联，以提供扩展建议。 该数据用于汇总以了解扩展的普及程度。

可以跨所有已登录同步版本的Microsoft Edge同步扩展和首选项。 导航到 `edge://settings/profiles/sync`，然后选择 **"登录以同步数据"** 按钮。

安装扩展是可选的。 若要随时卸载任何扩展，请导航到 `edge://extensions`。 安装扩展时，它指定需要访问哪些用户数据。 Microsoft Edge在安装扩展之前请求你的权限。 在安装扩展之前，请确保其安全可靠。 查看开发人员针对特定扩展的隐私策略。

扩展使用 Microsoft Edge 更新服务进行更新。  Microsoft Edge将已安装的扩展列表发送到更新服务以检查更新。  如果安装 Chrome Web Store 中的扩展，请求将定期发送到 Chrome Web Store，以检查扩展更新。 更新请求中包含扩展标识符、扩展版本和有关Microsoft Edge的信息。 可以停止对Chrome Web Store的请求。 导航到 `edge://extensions`。 关闭**从其他源**切换到卸载扩展。

可以从其他浏览器（如 Google Chrome）导入扩展。 如果Microsoft Edge加载项网站中提供了导入的扩展，Microsoft Edge从Microsoft Edge加载项网站自动安装该扩展。 如果之前已打开扩展，Microsoft Edge会自动为你打开它。

如果扩展在 Microsoft Edge 加载项网站上不可用，Microsoft Edge本地复制并安装 Google Chrome 中的扩展，而无需将其打开或连接到Chrome Web Store。  Microsoft Edge 需要你的许可才能启用该扩展，并允许启用其他存储中的扩展。  如果你已授予权限，则 Microsoft Edge 将允许安装其他存储中的扩展，并使用 Chrome Web Store 来更新你的扩展。  可以控制允许从其他商店进行扩展的选项。 导航到 `edge://extensions`。 切换**允许其他存储中的扩展**设置。


<!-- ====================================================================== -->
## <a name="family-safety"></a>家庭安全

Microsoft 提供了一些工具来帮助家庭保持联系，让孩子在运行微软桌面的 Windows、Xbox 和 Android 设备上更安全。

在家庭组中，使用 Microsoft Edge 时应为孩子启用家庭设置。  家庭组组织者必须为组中的用户启用设置。  为家庭组提供的三个主要功能是“Web 筛选”、“活动报告”和“安全搜索”。

Web 筛选可防止家庭组中的孩子转到家庭组织者阻止的成熟网站或网站。

活动报告记录有关儿童访问的网站的信息。 记录还包括搜索、屏幕时间、使用的设备以及尝试访问被阻止的站点。 家庭组组织者可能会在 [family.microsoft.com](https://account.microsoft.com/family)看到信息。 数据在传输过程中收集、加密、发送到 Microsoft 并存储在安全的 Microsoft 存储服务器上。 这些数据是通过孩子的 Microsoft 帐户收集的，因此可以妥善管理。 活动报告存储在 [family.microsoft.com](https://account.microsoft.com/family) 上长达 30 天，之后会将其删除。

“安全搜索”可向搜索引擎的头请求添加安全关键字。 必应读取安全关键字，并筛选返回给孩子的搜索结果。 由于关键字，其他搜索引擎可能会返回筛选结果。 将收集孩子搜索的所有数据，并供家庭组织者在活动报告或 [family.microsoft.com](https://account.microsoft.com/family) 中查看。 这些数据是通过孩子的 Microsoft 帐户收集的，因此可以妥善管理。

孩子的浏览数据存储在安全的 Microsoft 服务器上，可供家长在 30 天内查看，然后会立即删除。  可随时从“Microsoft 隐私仪表板”[](https://account.microsoft.com/privacy/)中删除数据。 若要清除在设备本地存储的浏览数据，请导航到 `edge://settings/clearBrowserData`。  选择**Time 范围**，根据需要选中复选框，然后选择 **"立即**。

收集孩子浏览数据并与家庭组组织者共享数据需要两项操作。 1.\） 必须使用Microsoft 帐户登录到Windows 10及更高版本。 2.\） 活动报告设置必须由家庭组织者打开。 无需登录子级即可Microsoft Edge收集浏览数据。 如果你的 Windows 版本上没有家庭安全功能，请更新到最新版本的 Windows。

如果已打开 Web 筛选或活动报告，则**来宾**模式和 **InPrivate** 浏览不可用。

家庭组组织者可能会停止从家庭安全门户中收集数据。  有关 Microsoft 家庭安全功能的详细信息，请导航到[什么是 Microsoft 家庭组？](https://support.microsoft.com/help/12413)


<!-- ====================================================================== -->
## <a name="geolocation"></a>地理位置

浏览 Web 时，网站可能会从 Microsoft Edge 请求设备的位置。 有关你的设备位置的数据（可能是精确数据，也可能是模糊数据）。 例如，请求一个精确的位置来提供特定位置的驾驶路线。 可能需要一个不精确的位置来提供与常规位置相关的搜索结果、新闻和天气。

Microsoft Edge支持[地理位置 API](https://w3.org/TR/geolocation-api)，允许网站在你许可的情况下访问你的精确位置。 在允许网站访问你的位置之前，Microsoft Edge 会始终征求你的许可。 若要管理特定于站点的权限或始终阻止站点访问精确位置，请转到 `edge://settings/content/location`。

Microsoft Edge 指示何时在地址栏右侧共享精确位置。 

:::image type="complex" source="./media/geolocation2.png" alt-text="位置。" lightbox="./media/geolocation2.png":::
   位置
:::image-end:::

如果允许与站点共享精确位置，Microsoft Edge 将本地网络信息发送到 Microsoft 定位服务。 此信息包括 IP 地址和邻近 Wi-Fi 接入点。 Microsoft 位置服务使用此信息估计地理位置坐标。 地理位置估计值与你同意共享精确位置的站点共享。

可以允许 Microsoft Edge 在Windows 10及 Windows 11 上为请求站点提供更精确的位置。 打开 **"设置** > **隐私** > **位置**"，然后打开"**允许访问此设备上的位置**"，**并允许应用访问你的位置**设置。

如果关闭 **“允许访问此设备上的位置”** 和 **“允许应用访问你的位置”** 设置，某些站点可以使用 IP 地址等信息来确定设备不精确的位置。 有关 Windows 位置设置的详细信息，请导航到 [Windows 位置服务和隐私](https://support.microsoft.com/help/4468240)。

Microsoft Edge 不存储地理位置坐标。 向 Microsoft 定位服务请求时，Microsoft Edge 每个请求生成一个新的随机 ID。

**InPrivate** 浏览使用启动 **InPrivate** 会话的配置文件的精确位置权限设置。 在向站点授予你的精确位置之前，**来宾**模式始终会要求你提供权限。


<!-- ====================================================================== -->
## <a name="image-enhancement"></a>图像增强
为了提供更好的浏览体验，Microsoft Edge 通过改进图像的颜色、照明、对比度和清晰度来提供图像增强功能。 启用图像增强功能后，Microsoft Edge 会对图像进行加密并将其传输到 Microsoft 服务器以执行图像增强。 对服务器的请求中不包含任何用户标识符。 图像缓存 30 天以提高性能。 

若要控制图像增强，请导航到 `edge://settings/privacy` 并打开或关闭 **Microsoft Edge 中的增强图像设置**。 


<!-- ====================================================================== -->
## <a name="import-browser-data"></a>导入浏览器数据

第一次启动浏览器时，Microsoft Edge 将提供交互式无缝体验。  可以将浏览器数据导入到其他浏览器Microsoft Edge。  在导入期间，可以保留现有数据，也可以将其删除并重新启动。  数据包括收藏夹、浏览历史记录、自动填充数据、扩展、设置以及其他浏览数据。

更新Microsoft Edge时，会自动导入旧版Microsoft Edge中的浏览数据。  确认后，Microsoft Edge从其他浏览器（如 Google Chrome、Mozilla Firefox 或 Internet Explorer）导入浏览器数据。 Microsoft Edge从操作系统定义的最常用浏览器导入数据。  在设备上本地完成数据导入，并存储在本地，并且不会发送到 Microsoft，除非你登录并同步浏览数据。

:::image type="complex" source="./media/migration.png" alt-text="导入。" lightbox="./media/migration.png":::
   Import
:::image-end:::

可以从其他浏览器（如 Google Chrome）导入扩展。 如果扩展在Microsoft Edge加载项网站上不可用，Microsoft Edge导入本地副本，并在开始之前请求权限。 某些扩展的权限可能已更改。 若要查看扩展权限，请导航到 `edge://extensions`。

若要随时导入其他浏览器中的数据，请导航到 `edge://settings/importData`。


<!-- ====================================================================== -->
## <a name="install-and-update"></a>安装和更新

可在 Windows 和 macOS 等平台上下载和安装 Microsoft Edge。  Microsoft Edge 使用更新服务使 Microsoft Edge 版本处于最新状态，并确保安全。

安装或更新Microsoft Edge时，设备信息将发送到 Microsoft。 设备信息包括发布频道、基本硬件信息、更新标识符、设备特有的标识符，以及浏览器特有的可重置标识符。 设备的 IP 地址将发送到更新程序服务，但最后一个十进制文件经过清理以添加隐私保护。 在每个浏览会话过程中，将创建一个随机生成的新令牌来安装 Microsoft Edge 的更新版本。 令牌不与任何个人信息相关联，仅用于安装和更新过程以及改进更新服务。

Microsoft Edge 就安装和更新进度对 Microsoft Edge 更新服务执行 ping 操作。  如果安装或更新失败，并且启用了故障报告，则会创建一个日志并发送到 Microsoft。  有关向 Microsoft 发送故障报告的详细信息，请导航到[故障](#crashes)部分。  Microsoft 收集有关 Microsoft Edge 的下载方式、成功安装以及任何卸载的信息，以便更好地理解如何成功下载 Microsoft Edge。

默认情况下，所有 Microsoft Edge 用户都会启用自动更新。  在所有平台上，Microsoft Edge 都会在启动时和运行时定期检查更新。  在 macOS 设备上，Microsoft AutoUpdate 还会定期检查 Microsoft 产品的更新。  组织可以使用更多控件和配置。  有关控件和配置的详细信息，请导航到 ["更新](/deployedge/microsoft-edge-update-policies#update)"。


<!-- ====================================================================== -->
## <a name="internet-explorer-mode"></a>Internet Explorer 模式

Microsoft Edge 通过 Internet Explorer (IE) 集成简化了体验。  Microsoft Edge 仅支持 IE 11，而 IE 模式仅在 Windows 上可用。  通过组策略，组织可以使用 IE 模式功能。  管理员选择在 Microsoft Edge 的 IE 模式下打开特定网站。

:::image type="complex" source="./media/ie-mode.png" alt-text="IE 模式。" lightbox="./media/ie-mode.png":::
   IE 模式
:::image-end:::

Microsoft Edge 通过策略从管理员定义的位置下载网站列表，并缓存确定必须以 IE 模式打开的网站的文件。  根据 Windows 或 IE 11 设置，Microsoft Edge收集有关使用 IE 模式的诊断数据。 收集的数据包括用户访问的站点、性能数据、可靠性数据和功能使用情况数据。  在Windows 10及更高版本上，将根据 Windows 诊断数据设置收集诊断数据。  Windows 8.1，如果用户已选择在 IE 中使用"向前翻转"或"建议的网站"功能，则会收集网站信息。  IE 模式可能不会遵循 Microsoft Edge 隐私设置中的相同数据收集设置。

如果管理员启用了企业站点发现，则会定期收集浏览历史记录数据，以帮助管理员查看用户访问的站点，并确保系统升级继续支持这些站点。  有关 IE11 中“企业网站发现”功能的详细信息，请导航到[使用企业网站发现收集数据](/internet-explorer/ie11-deploy-guide/collect-data-using-enterprise-site-discovery)。

Windows 设备上的非企业用户也可以访问 IE 模式。  若要启用 IE 模式，请导航到 `edge://settings/defaultBrowser`，然后选择“允许在 Internet Explorer 模式下重新加载网站”**** 设置。  若要打开 IE 模式下的选项卡，请打开“**设置和更多(...)**” > “**更多工具**”并选择“**在 Internet Explorer 模式下重新加载**”。  启用 IE 模式后，Microsoft Edge 会定期从 Microsoft 服务请求不受支持的网站的列表。  请求是通过 HTTPS 发送的，且不包含任何标识符。

Internet Explorer 浏览数据本地存储在 Microsoft Edge 和 Internet Explorer 中。  若要在 IE 模式下浏览时删除浏览数据，请导航到 `edge://settings/privacy`，并从“清除浏览数据”**** 和“清除 Internet Explorer 的浏览数据”**** 中清除数据。


<!-- ====================================================================== -->
## <a name="intrusive-ads"></a>侵入式广告

为了提供更好的浏览体验，Microsoft Edge 将阻止在显示侵入性或误导性广告的网站上加载广告。 启用“广告屏蔽”后，Microsoft Edge 将定期从 Microsoft 服务器下载显示有侵入性或误导性广告的最新网站列表，并存储在设备本地。  下载请求中不包含任何用户标识符。  如果访问列表上的网站，Microsoft Edge 会阻止该网站上的所有广告，并且你会看到 `Ads blocked` 消息。  为获得网站广告，请导航到 `edge://settings/content/ads` 并更改设置。 除了下载具有侵入式广告的网站列表之外，“广告屏蔽”功能不会向 Microsoft 发送其他信息，也不会在你浏览网站时向 Microsoft 请求其他信息。


<!-- ====================================================================== -->
## <a name="jump-list"></a>跳转列表

使用 Microsoft Edge 中的“跳转列表”，你可以通过将鼠标悬停在任务栏中的 Microsoft Edge 图标上并打开上下文菜单（右键单击）轻松找到最近关闭的网站。 为每个配置文件本地存储最后三个关闭的选项卡。  若要从 Windows 10 及更高版本的跳转列表中删除网站，请将鼠标悬停在每个站点上，然后打开上下文菜单（右键单击）。

可以在跳转列表中清除或更改最近关闭的选项卡的显示。 导航到， `edge://settings/privacy` 然后选择**选择每次关闭浏览器时要清除的内容**设置。 使用 **InPrivate** 窗口时，Microsoft Edge 不会将关闭的选项卡信息添加到“跳转列表”。  使用 **来宾** 模式时，跳转列表不可用。  有关清除浏览数据的详细信息，请导航到[查看和删除 Microsoft Edge 中的浏览器历史记录](https://support.microsoft.com/help/10607)。


<!-- ====================================================================== -->
## <a name="kids-mode"></a>儿童模式

儿童模式是专为 Microsoft Edge 中的儿童设计的便捷浏览模式。  有了儿童友好功能和安全护栏，“儿童模式”是儿童安全浏览网络的理想之地。  儿童模式包括自定义浏览器主题、儿童友好内容、基于允许列表进行浏览、必应安全搜索设置为严格以及退出密码要求等功能。  儿童模式不需要子帐户或个人资料，因此你无法登录儿童模式。

:::image type="complex" source="./media/kids-mode.png" alt-text="儿童模式。" lightbox="./media/kids-mode.png":::
   儿童模式
:::image-end:::

在儿童模式下浏览仅限于儿童友好网站的默认列表。  导航时，网站会与允许的网站的本地列表进行比较。  在儿童模式下访问的网站不能在 [family.microsoft.com](https://account.microsoft.com/family) 查看，因为在儿童模式下浏览不会与任何帐户相关联。  可以通过启动儿童模式的个人资料添加允许的网站例外。  如果用户已登录，则这些异常将同步到启动儿童模式的配置文件。

为了增强儿童模式体验，Microsoft Edge 向 Microsoft 必应和 Microsoft 新闻的标题请求添加了一个安全关键字。  安全关键字有助于筛选掉不适当的搜索结果和新闻。  儿童模式设置 Microsoft Edge 设置的首选项，例如将跟踪防护设置为严格以阻止网站上大多数跟踪器。  关闭时清除浏览数据也已被打开，这将在儿童模式关闭时清除 Cookie 和其他网站数据等内容。  若要在儿童模式下随时清除浏览数据，请完成以下操作。

1.  选择 **"设置**  >  **""隐私"。**
1.  选择 **"选择要清除哪些项目"。**

儿童模式不会收集用于新闻源或其他 Microsoft 服务个性化的数据。  你不得更改儿童模式的隐私设置。  其他设置（如 Windows Defender SmartScreen 和诊断数据）根据启动儿童模式的个人资料进行配置。  若要详细了解如何使用浏览器和 Windows Defender SmartScreen 的诊断数据，请导航到 [诊断数据](#diagnostic-data)和[SmartScreen](#smartscreen)。


<!-- ====================================================================== -->
## <a name="microsoft-edge-driver"></a>Microsoft Edge 驱动程序

Microsoft Edge 驱动程序允许开发人员使用 [WebDriver 协议](https://www.w3.org/TR/webdriver2/)驱动 Microsoft Edge 浏览器。  Microsoft Edge驱动程序是可执行文件 `msedgedriver.exe` 与Microsoft Edge进行分隔。 开发人员可以从客户端代码（例如测试脚本）调用驱动程序。  默认情况下，Microsoft Edge 驱动程序会向 Microsoft 发送诊断数据，如[新建会话 WebDriver 命令](https://www.w3.org/TR/webdriver2/#new-session)的状态。  若要关闭 Microsoft Edge 驱动程序的诊断数据收集，请将 `MSEDGEDRIVER_TELEMETRY_OPTOUT` 环境变量设置为 `1`。  有关 Microsoft Edge 驱动程序的详细信息，请导航到 [使用 WebDriver 自动执行 Microsoft Edge 自动化](/microsoft-edge/webdriver-chromium)。


<!-- ====================================================================== -->
## <a name="network-time"></a>网络时间

Microsoft Edge 使用 Microsoft 网络时间服务来跟踪来自外部源（如时间服务器）的时间。  通过随机间隔或当 Microsoft Edge 遇到过期的 SSL 证书时，Microsoft Edge 可能会向 Microsoft 发送请求，以获取来自受信任源的时间。  如果 Microsoft Edge 检测到系统时钟不准确，将会更频繁地发出请求。  如果用户更改了操作系统上的时间且该时间与正确时区相冲突，则会导致系统时钟不准确。  Microsoft 网络时间服务用于获取协调世界时 (UTC)。  请求中不包含 cookie 或用户标识符，并且不会记录任何数据。


<!-- ====================================================================== -->
## <a name="new-tab-page"></a>“新建选项卡”页面

Microsoft Edge提供了一个以用户为中心的新选项卡页面，其中的搜索框由[Bing](https://bing.com)提供支持。 Microsoft Edge还为你最常访问的网站提供快速链接磁贴，以及来自 Microsoft 新闻或 Office 365 的相关内容。 可以通过选择 **"自定义** "按钮来更改新选项卡页的外观。 为每个配置文件设置新的选项卡页首选项，并将其存储在本地设备上。 首选项不会跨设备同步。

为了加快 Microsoft Edge 新选项卡页的加载时间，可以在后台加载该页面。 如果允许 Cookie，加载的内容可能包含 Cookie。 可以关闭 Microsoft 新选项卡页面的后台加载。 导航到 `edge://settings/newTabPage` 并关闭 **"预加载新选项卡"页，以获得更快的体验** 设置。

:::image type="complex" source="./media/n-t-p1.png" alt-text="“新建选项卡”页面。" lightbox="./media/n-t-p1.png":::
   “新建选项卡”页面
:::image-end:::

### <a name="microsoft-news"></a>Microsoft 资讯

为了根据用户的交互和偏好定制内容，Microsoft Edge 中的“新建选项卡”页面会在设备上使用随机生成的标识符存储 cookie。  还会使用你的 IP 地址的精制版本，来根据你的通用区域定制内容。  若要清除设备上保留的 cookie，请导航到 `edge://settings/siteData`。

若要防止对广告进行个性化设置，请导航到 Microsoft[隐私仪表板](https://account.microsoft.com/privacy/)上的[广告设置](https://account.microsoft.com/privacy/ad-settings)。 在 **浏览器设置中关闭"查看个性化广告** "。  若要禁用快速链接磁贴，请打开“自定义按钮”**** > “自定义”****，禁用“显示快速链接”**** 设置。 Microsoft Edge 使用本地浏览历史记录对快速链接磁贴进行个性化设置，你可以删除或新建磁贴。 你可以删除或创建新磁贴。 根据配置文件，数据只是本地存储在设备上。

“新建选项卡”页面上的搜索框根据输入的搜索查询执行必应搜索。  若要自动提供搜索建议和结果，Microsoft Edge 可与必应共享输入的字符、搜索查询、IP 地址和搜索标识符。 搜索框可能配置了组策略来提供 Microsoft 搜索中的搜索结果，进而返回来自贵组织的信息，如文档和 Intranet 内容。 结果可能包括来自组织的信息，如文档和 Intranet 内容。 为了提供集成搜索体验，Microsoft Edge 将在设备上本地存储 cookie。

如果你已使用Microsoft 帐户登录到Microsoft Edge，则可以从 [Microsoft 隐私仪表板](https://account.microsoft.com/privacy/ad-settings)管理与新选项卡页关联的浏览活动。

Microsoft Edge 收集有关如何使用新选项卡页的诊断数据，如与搜索框的交互以及选择快速链接磁贴的情况。  若要支持有关如何使用新标签页的诊断数据的收集，请导航到 `edge://settings/privacy`，然后启用“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品”**** 设置。  浏览器将有关如何使用“Microsoft 资讯”页面的诊断数据发送到 Microsoft，以帮助了解用户与资讯内容的交互并改进 Microsoft 产品。  你可以通过选择新选项卡页上的 **"自定义"** 按钮来关闭 Microsoft 新闻内容。  资讯数据通过 HTTPS 发送到 Microsoft，并保存长达 13 个月，之后会被聚合并进行匿名处理。

通过“新建选项卡”页面，你还可以将自定义图像设置为背景。 图像本地存储在设备上，可通过删除图像或上传新图像进行删除。 不会向 Microsoft 发送有关图像的任何信息。

### <a name="office-365"></a>Office 365

如果你使用工作或学校帐户登录到 Microsoft Edge，则你的组织可能会在“新建选项卡”页面上启用 Office 365 作为页面内容的选项。 此功能目前仅适用于商业客户，并受到 [Microsoft 在线服务条款 (OST)](https://www.microsoft.com/licensing/product-licensing/products) 的制约。 有关 Office 365 隐私的详细信息，请导航到 [Microsoft 365 企业应用版的隐私控制概述](/deployoffice/privacy/overview-privacy-controls)。

**InPrivate** 浏览和 **来宾** 模式提供了替代的新选项卡页面体验。


<!-- ====================================================================== -->
## <a name="on-startup"></a>启动时

通过 Microsoft Edge，你可以从上次浏览会话中打开上次打开的选项卡，选择从上次离开的位置开始浏览。 它将打开上一浏览会话中最后打开的选项卡，包括会话 Cookie。 此功能在启动时仍然可用，以还原上一会话中的选项卡，并让你登录到已访问的网站。  你可以将 Microsoft 配置为 edge 显示上一浏览会话中打开的选项卡。 导航到 `edge://settings/onStartup` 并打开" **继续，其中你已离开"** 设置。 如果你选择“**从上次离开的位置继续**”设置并在每次关闭浏览器时清除浏览数据，则将删除你指定的数据，但该 URL 会保留到下一次会话。

你还可以设置 Microsoft Edge，以便在启动时打开特定页面。 你指定的页面本地存储在设备上，并特定于配置文件。  如果启用了设置同步，指定的页面将同步到你登录的所有 Microsoft Edge 版本。  若要启用同步设置，请导航到`edge://settings/profiles/sync`并打开 **"设置"。**

启动时不会还原 **InPrivate** 和**来宾**模式选项卡。


<!-- ====================================================================== -->
## <a name="password-monitor"></a>密码监视器

Microsoft Edge 致力于保证你在 Web 上的安全性。 为了帮助保护你个人信息的隐私和安全，如果你登录到了 Microsoft Edge，密码监视器会在第三方数据泄露你的凭据时提醒你。 如果启用了密码监视器，则已保存的凭据将在你的设备上进行本地哈希和加密，然后通过 HTTPS 发送到 Microsoft 服务器，并与已知泄露凭据的加密列表进行比较。

如果启用了密码监视器，则已保存的凭据将在你的设备上进行本地哈希和加密，然后通过 HTTPS 发送到 Microsoft 服务器，并与已知泄露凭据的加密列表进行比较。 将登录帐户标识符与哈希和加密凭据一起安全发送到密码监视器服务。

如果在已知的泄露凭据列表中发现凭据，Microsoft 将向你的 Microsoft Edge 版本发送加密响应，提醒在黑客入侵或泄露过程检测到你的凭据。 该消息警告你，你的凭据被检测为黑客攻击或泄露的一部分。 检查完成后，Microsoft 服务器上不会存储任何数据。

该功能仅适用于已登录到 Microsoft Edge 的用户。 Microsoft Edge 要求你提供启用密码监视器的权限。  若要启用\（或禁用\）“密码监视器”，请导航到 `edge://passwords`。


<!-- ====================================================================== -->
## <a name="payments"></a>付款

通过 Microsoft Edge，你可以将付款信息保存到你的浏览器配置文件，以及在你浏览时根据需要使用信息自动填充付款表单，从而帮助你提高工作效率。  遇到类似付款表单时，Microsoft Edge 将使用保存的信息填写表单。  信用卡和其他付款信息仅通过显式权限保存。

如果启用了付款自动填充功能，则 Microsoft Edge 会询问你是否要存储付款信息。  将在你的设备上本地加密此信息。  若要删除保存的付款信息，请导航到 `edge://settings/payments`。  删除保存的付款信息后，该信息不再显示为自动填充建议。  若要不保存任何付款信息，请导航到 `edge://settings/payments`，然后关闭该功能。

Microsoft Edge允许你将付款信息保存到浏览器配置文件。 Microsoft Edge根据需要自动填写付款表单。 遇到类似付款表单时，Microsoft Edge 将使用保存的信息填写表单。  信用卡和其他付款信息仅通过显式权限保存。

如果启用了付款自动填充功能，则 Microsoft Edge 会询问你是否要存储付款信息。 将在你的设备上本地加密此信息。 若要删除保存的付款信息，请导航到 `edge://settings/payments`。  删除保存的付款信息后，该信息不再显示为自动填充建议。

Microsoft Edge支持 PaymentRequest API。 API 允许你使用之前使用自动填充保存的付款信息支付购买费用。 PaymentRequest API 允许商家请求以下信息：信用卡号码、信用卡到期日、全名、帐单邮寄地址、电子邮件地址、电话号码和送货地址。 API 告知商家你已保存信用卡信息，但除非允许，否则不会与商家共享任何信息。 若要关闭“付款”功能，请导航到 `edge://settings/privacy`。

如果你以前将付款信息保存到你的 Microsoft 帐户，也可在浏览器中自动填充。 存储在 Microsoft 帐户中的付款信息将跨设备同步。 如果你以前在任何 Xbox 或 Microsoft Store 进行了购买，则可能已将付款信息保存到 Microsoft 帐户。  在付款自动填充过程中，来自 Microsoft 帐户的信用卡将使用掩码，并且仅在双因素身份验证后才完全显示。 掩码在检索付款信息时提供了额外的安全性。

该功能仅适用于具有非 Microsoft 子帐户的用户。  对于使用工作或学校帐户登录到 Microsoft Edge 的用户，此功能不可用。

如果你允许个性化，Microsoft Edge 团队会收集并使用你的 Microsoft Edge 浏览历史记录，以便对[必应](https://bing.com)、Microsoft 资讯和其他 Microsoft 服务的体验和广告进行个性化设置。  个性化设置提供了更为相关且有用的搜索结果、广告和资讯内容。  例如，如果 Microsoft Edge 团队根据你的浏览情况推断出你喜欢在某个商店购物，则你看到的广告可能是根据特定商店中的产品定制的。  类似地，如果经常查看旅行博客和阅读旅行文章，你的新闻源可能包含更多旅行相关的资讯内容。

该功能仅适用于具有非 Microsoft 子帐户的用户。 对于使用工作或学校帐户登录到 Microsoft Edge 的用户，此功能不可用。

仅当满足所有四个条件时，才会收集浏览历史记录并将其用于个性化设置。

* 你已登录到非子 Microsoft 帐户。
* 用户已授予收集和使用数据进行个性化设置的权限。
* 由组织管理的用户组策略（雇主、学校等）允许进行个性化设置。
* 你未在 **来宾** 或 **InPrivate** 模式下使用浏览器。

浏览历史记录和其他相关数据将通过 HTTPS 传输并附加到你的 Microsoft 帐户信息。  浏览历史记录存储在安全的 Microsoft 服务器上。  可通过“[Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)”查看和删除以前共享的浏览历史记录。  浏览历史记录存储在安全的 Microsoft 服务器上长达 45 天。  45 天后，数据将被删除，且不用于个性化设置。

可从“[Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)”上的“[广告设置](https://account.microsoft.com/privacy/ad-settings)”中修改兴趣或选择退出个性化广告。

> [!NOTE]
> 选择退出“[Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)”上的个性化广告，不会禁用对个性化搜索结果和新闻源内容的浏览历史记录的收集和使用。 您可以关闭个性化搜索结果和新闻的 Microsoft Edge浏览历史记录的收集和使用。 导航到 `edge://settings/privacy`。 在 **"个性化 Web 体验** "中， **允许 Microsoft 使用帐户中的浏览历史记录个性化广告、搜索、新闻和其他Microsoft 服务** 设置，从而关闭"改善 Web 体验"。 如果停止共享数据，Microsoft 将不再收集和使用你的浏览历史记录来个性化广告、搜索结果和资讯。 有关 Microsoft Edge 中的个性化设置的详细信息，请导航到[用于个性化广告和体验的 Microsoft Edge 浏览历史记录](https://support.microsoft.com/help/4532583)。


<!-- ====================================================================== -->
## <a name="print"></a>Print

借助 Microsoft Edge，可使用多种设备和应用程序来打印网页、PDF 文件或其他内容。 打印到打印机、应用程序或 PDF 时，Microsoft Edge 会将命令和文件信息发送到设备的操作系统。 不会将该信息发送给 Microsoft。 该信息不会发送给 Microsoft，且所有发送到设备操作系统的数据在完成或取消打印后将立即删除。 若要更改打印目标，请导航到 `edge://settings/printing`。

也可以使用 Microsoft Print to PDF 将网页和文件打印到 PDF，此操作不会将有关该文件的任何数据发送回 Microsoft。  对 PDF 文件所做的任何批注将本地保存到文件。


<!-- ====================================================================== -->
## <a name="profiles"></a>配置文件

Microsoft Edge 中的配置文件使你能够将浏览数据分隔到独立的配置文件中。  与一个配置文件关联的数据独立于与其他配置文件关联的数据。  例如，如果你在不同的配置文件中设置了个人收藏夹和历史记录，那么它们就不会与你的工作帐户同步。

但是，用户可以在 Microsoft Edge 中轻松切换现有配置文件，而无需密码。  如果用户有权访问同一设备，则可以在相同版本的 Microsoft Edge 上创建另一个配置文件，而无需获得当前配置文件所有者的许可。  从 Microsoft Edge 设置中删除配置文件，将永久删除设备上存储的特定配置文件的浏览数据，如浏览历史记录、收藏夹、表单填充数据和密码。  同步到你的帐户的数据可能仍存储在 Microsoft 云中，并且可能会从“[Microsoft 隐私仪表板](https://account.microsoft.com/privacy/)”中清除。

**来宾** 模式是新配置文件的临时实例。  它允许你在不修改已登录配置文件的情况下浏览其他用户的设备。 关闭所有**来宾**模式窗口后，从**来宾**模式（如收藏夹、浏览历史记录、密码和表单填充数据）浏览数据不会保留。  下载的文件存储在设备上，但下载的历史记录将被删除。

**来宾** 模式允许你在不自动登录其他站点的情况下浏览 Web。  Microsoft Edge不会向网站发送任何信息，以指示用户正在来 **宾** 模式下浏览。  使用 **来宾** 模式时，从启动来 **宾** 模式会话的Microsoft Edge配置文件中获取有关如何使用浏览器和网站的诊断数据的权限。  关闭所有 **来宾** 窗口后，将清除特定来 **宾** 模式会话的所有浏览数据。

**InPrivate** 浏览是一种私人浏览模式。 InPrivate 浏览是一种私有浏览模式，在该模式下，不会记住浏览历史记录、下载历史记录、cookie 和网站数据以及表单填充数据。 Microsoft Edge保存下载的文件和浏览 **InPrivate**时创建的任何新收藏夹。

默认情况下，在浏览 **InPrivate**时，Microsoft 不会收集有关你出于产品改进目的访问的网站的任何信息。 你的学校、工作场所或 Internet 服务提供商可能仍然能够看到你的浏览活动。

关闭所有 **InPrivate** 窗口后，将清除特定 **InPrivate** 会话的浏览数据。  使用 Windows 输入法编辑器 (IME) 键盘进行输入和墨迹书写时，可能会收集数据以改进语言识别和建议功能。  在 **InPrivate** 和正常浏览期间使用 Windows 输入法键盘时，可以停止 Microsoft 收集墨迹书写和键入数据。 打开 **"开始** > **设置** > **隐私**"，并关闭 **"墨迹书写"和"键入个性化设置**"。  有关**InPrivate**浏览的详细信息，请导航到[Microsoft Edge 中的"浏览 InPrivate"。](https://support.microsoft.com/help/4533513)


<!-- ====================================================================== -->
## <a name="read-aloud"></a>大声朗读

Microsoft Edge 提供大声朗读功能，它向用户朗读网页内容。  若要启动“大声朗读”，请将鼠标悬停在页面上的任意位置，并打开上下文菜单（右键单击）或打开“**设置和更多(...)**” 并选择“ **大声朗读**”。  大声朗读提供了多种语音，可用于阅读网页内容。  如果使用的语音安装在 Windows 设置的"**时间和语言**"部分[Windows 10及更高版本上](https://support.office.com/article/4c83a8d8-7486-42f7-8e46-2b0fdf753130)，并且想要清除以前使用的任何语音的本地缓存，请导航到`edge://settings/clearBrowserData`。

当你启动“大声朗读”时，Microsoft Edge 将使用 [Web 语音 API](https://wicg.github.io/speech-api)。 根据你选择的语音，将使用平台提供的客户端库（例如，特定于你的操作系统的客户端库）或由 Azure 认知服务提供支持的服务器端库，将页面内容从文本转换为语音。

如果使用客户端库将内容转换为语音，则不会向 Microsoft 服务器发送任何信息。 如果使用 Azure 认知服务（如任何语音名称中的“Online”一词所示）将内容转换为语音，则文本以及随机生成的令牌将发送到 Microsoft。  转换完成后，服务会将音频文件中的口述文本返回到你的设备。  所有数据在从设备传输到 Microsoft 时都会加密，反之亦然。  发送给 Microsoft 的文本和生成的音频文件将在转换发生后立即删除；任何时间段内均不会存储有关你的 Web 内容的其他数据。


<!-- ====================================================================== -->
## <a name="releasing-new-functionality"></a>发布新功能

为改进 Microsoft Edge，Microsoft Edge 团队一直在向用户学习。  在学习过程中，某些用户可能会在新功能公开发布之前体验这些新功能。

若要为随机选定的用户启用新功能，Microsoft Edge 会定期向 Microsoft Edge 配置服务发送有关你的操作系统、频道、版本、国家/地区和其他设备配置数据的所需信息。  将使用你的浏览器所特有的可重置标识符发送数据。  数据通过 HTTPS 传输到服务。  这些数据用于接收更新以启用新功能，使 Microsoft Edge 保持最新状态并正常运行，以及改进 Microsoft 产品和服务。

组织可以使用更多控件和配置。  有关组织的其他控制和配置的详细信息，请导航到 [Microsoft Edge 配置和试验](/deployedge/edge-configuration-and-experiments)。

作为用户，你无法关闭组织控制或配置的浏览器更新。 你可以控制是否将产品使用情况数据发送给 Microsoft。 导航到 `edge://settings/privacy` ，并更改 **可选诊断数据** 设置。

Microsoft 开发人员需要了解新函数对Microsoft Edge Microsoft 服务。 Microsoft Edge发送浏览器唯一的可重置标识符和一个函数标记，该标记对哪些新函数进行了编码Microsoft Edge和Microsoft 服务。 新功能有助于为每个用户构建最佳体验和最佳的浏览器。

函数标记不是安装函数的唯一Microsoft Edge。 标记在共享同一Microsoft Edge集的所有实例之间共享。  Microsoft Edge 将 HTTPS 中的信息发送给 Microsoft 服务。 浏览 **InPrivate** 或来 **宾** 模式时，浏览器不会发送信息。 可以阻止发送数据。 请导航到 `edge://settings/privacy`，然后关闭 **“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品”** 设置。 有关如何重置浏览器特有的标识符的详细信息，请导航到[有关如何使用浏览器的诊断数据](#diagnostic-data)部分。


<!-- ====================================================================== -->
## <a name="resolve-navigation-errors"></a>解决导航错误

如果 Microsoft Edge 检测到 SSL 连接超时、证书错误或可能由强制网络门户（例如，旅馆或机场的 Wi-Fi 网络）导致的其他网络问题，Microsoft Edge 将向 `http://edge.microsoft.com/captiveportal/generate_204` 发送请求并检查响应代码。 强制网络门户包括酒店或机场的 Wi-Fi 网络。 如果请求重定向到另一个 URL，Microsoft Edge 将在新选项卡中打开该 URL，假定该 URL 是一个登录页面。  对强制网络门户检测页的请求是无状态服务。 不会记录请求，也不会发送或保存 Cookie。  在 Windows 平台上，Microsoft Edge 使用 Windows 强制网络门户服务。 否则，将使用 Microsoft Edge 强制网络门户服务。 可以关闭该服务。 导航到 `edge://settings/privacy`，并关闭 **"使用 Web 服务帮助解决导航错误** "设置。


<!-- ====================================================================== -->
## <a name="search-results-data-for-product-improvement"></a>搜索结果数据以改进产品 
为了改进你在 Microsoft Edge、Microsoft 必应、Microsoft 新闻和其他 Microsoft 服务中的体验，当启用此功能的设置时，Microsoft Edge 将收集并使用你在 Microsoft Edge 中的网络搜索数据。 Microsoft 将使用你的搜索结果活动，使每个人的 Web 和搜索体验更好、更相关且更有用。 Microsoft 收集的数据来自你在 Web 上执行的搜索，包括 Microsoft 不拥有或不运营的网站。

* Microsoft Edge 将删除标识数据收集对象（人员或设备）的数据，以清理和取消识别数据。 

* Microsoft 不会使用我们收集的任何信息来进行个性化设置或向你提供广告。 

* Microsoft 收集的数据永远不会与你的帐户或设备相关联。 

* 此数据收集和设置在托管设备上不可用。 

Microsoft 收集数据的数据可能包括搜索查询、显示给你的搜索结果，以及你与这些搜索结果的交互，例如你单击的链接。 Microsoft 也会收集人口统计数据。 

若要管理用于改进产品的搜索结果活动的收集和使用，请执行以下操作: 

1. 打开 Microsoft Edge。

1. 选择 **“设置及更多”** > **“设置”**。 

1. 选择 **“隐私、搜索和服务”**。 

1. 在 **搜索和服务改进** 下，打开或关闭 **通过在 Web 上发送搜索结果来帮助改进 Microsoft 产品**。 

如果停止共享你的数据，Microsoft 可能会继续使用以前收集的搜索结果数据，但它仍将被取消标识，并且不会与你或你的设备相关联。


<!-- ====================================================================== -->
## <a name="secure-dns"></a>安全 DNS

导航到网站时，浏览器需要查找网络地址，如 `93.184.216.34`，以解析主机名，例如 `example.com`。 安全 DNS 通过与 DNS 服务提供程序的 HTTPS 连接使用服务执行此查找。 安全 DNS 可防止网络上的攻击者修改或窃听查找。

默认情况下，当前 DNS 服务提供商用于避免浏览中断。 并非所有服务提供商都提供安全 DNS。 为了避免浏览延迟，如果安全 DNS 连接失败，Microsoft Edge尝试使用当前未加密的 DNS 服务提供程序进行 DNS 查找。

Microsoft Edge 支持使用特定的安全 DNS 提供商。 如果选择安全 DNS 提供程序，则Microsoft Edge在安全查找失败时不会回退到常规 DNS 查找。 可以在 中控制安全 DNS 设置 `edge://setting/privacy`。

对于属于组织的托管计算机，默认 `off` 安全 DNS。 可以使用管理策略对其进行配置。 **InPrivate** 浏览使用从中启动 **InPrivate** 会话的配置文件的安全 DNS 设置。 来宾模式将始终使用当前的服务提供商。


<!-- ====================================================================== -->
## <a name="shopping"></a>购物

Microsoft Edge可以帮助您在在线购物时找到优惠券，折扣和更优惠的价格。 为帮助你在在线购物时查找赠券或最适合的价格，Microsoft Edge 从 Microsoft 购物服务将本地购物域列表下载到客户。

浏览网站或将项目保存到收藏时，Microsoft Edge 本地确定访问的网站是购物域还是产品详细信息网页。  如果网站标识为购物网页，Microsoft Edge将删除的个人数据的 URL 发送到 Microsoft 购物服务。

Microsoft 还会向该服务发送产品价格、产品图像、产品名称、评级和评论，以及 Microsoft Edge 和操作系统版本的信息。  数据通过 HTTPS 发送，并包含随机生成的标识符和 Cookie（如果允许 Cookie）。

Microsoft Edge 购物功能要求与必应共享 Cookie 信息。  例如，Cookie 可用于调试、欺诈检测和分析。  Microsoft 购物服务返回其他零售商提供的价格、历史价格趋势和该网站的任何可用赠券。

当你应用优惠券时，Cookie 将存储在你的设备上以正确分配优惠券提供商。  仅在成功在购物车应用赠券后，Microsoft 信任的赠券提供商才保存 Cookie。  在应用优惠券后，有关优惠券成功与否的信息将发送回 Microsoft 购物服务，以帮助我们了解哪些优惠券成功或失败。

发送到 Microsoft 购物服务的数据通过 HTTPS 发送，其中包含随机生成的标识符，该标识符会更改每个优惠券查找。 Microsoft Edge 与必应购物合作，提供与用户查询相关的优惠券。 在某些情况下，Microsoft 可能会获得使用优惠券的收入。 是否可以接收收入份额付款不会纳入向用户显示的优惠券排名。

:::image type="complex" source="./media/shopping.png" alt-text="购物和优惠券。" lightbox="./media/shopping.png":::
   购物和优惠券
:::image-end:::

如果你访问购物域，并且你是现有的必应奖励用户，Microsoft Edge 会随 Cookie 一起将域发送到 Microsoft 购物服务，以检索你的必应退款配置文件和该域的退款优惠。  如果选择激活现金返还，Microsoft Edge将把网址发送到Microsoft购物服务，以接收关联URL。  设备上可能会存储Cookies，以正确归属返利提供者。

默认情况下，将为所有用户启用购物服务。  若要更改 Microsoft Edge 中的购物设置，请完成以下操作。

1.  导航到 `edge://settings/privacy`。
1.  关闭" **在 Microsoft Edge 中购物节省时间和资金"** 设置。

**InPrivate** 浏览使用启动 **InPrivate** 会话的配置文件的购物设置。

InPrivate 浏览使用启动 InPrivate 会话的配置文件的购物设置。


<!-- ====================================================================== -->
## <a name="sign-in-and-identity"></a>登录和标识

登录到Microsoft Edge提供了许多功能，可提高浏览器的效率。 若要在首次启动Microsoft Edge时无缝登录，它会尝试从操作系统检测你的身份。 如果Microsoft Edge从操作系统检测到你的身份，但你不希望继续登录到Microsoft Edge，请导航到 `edge://settings/profiles` 并注销或删除配置文件。

如果向操作系统添加了新的标识，而你的 Microsoft Edge 配置文件当前尚无标识，则 Microsoft Edge 会将特定标识添加到你的配置文件。 如果你使用Microsoft 帐户或工作或学校帐户登录Microsoft Edge，并且你的 Windows 配置文件上没有标识，则该帐户将添加到 Windows 配置文件中，除非你选择在登录时不将其添加到 Windows。

登录到Microsoft Edge启用单一登录。 你将自动登录到某些网站 (如必应) 和其他标识支持的体验 (如同步)。如果要将自动登录限制为 Microsoft 站点 (如 [必应](https://bing.com))，则可以退出登录浏览器。

若要使用用户名和密码再次登录到特定网站或清除 cookie ，请导航到 `edge://settings/privacy`。 有关清除浏览数据的详细信息，请导航到[查看和删除 Microsoft Edge 中的浏览器历史记录](https://support.microsoft.com/help/10607)。

若要阻止任何标识与 Microsoft Edge 关联，请删除 Microsoft Edge 配置文件或注销 Microsoft Edge。 若要从设备中删除与 Microsoft Edge 配置文件关联的所有数据，必须删除 Microsoft Edge 配置文件。 删除所有数据不会删除以前同步的与该标识相关联的数据。

macOS 上 Microsoft Edge 中的标识在 Microsoft 应用间共享。 共享标识允许你登录到 Microsoft 应用，而无需单独输入凭据（如果你已登录到设备上的另一个 Microsoft 应用）。 在 macOS 上，不会根据你在另一个 Microsoft 应用中的身份验证状态自动登录到 Microsoft Edge。 尝试登录到 Microsoft Edge 时，可使用设备上来自其他 Microsoft 应用的凭据无缝登录到 Microsoft Edge。  同样，当你登录到帐户以Microsoft Edge时，如果尝试登录其他 Microsoft 应用，则可以使用Microsoft Edge凭据来帮助你在设备上登录到其他 Microsoft 应用，而无需再次输入凭据。

使用 **来宾** 模式或 **InPrivate**时，无法登录 Microsoft Edge。

<!-- ====================================================================== -->
## <a name="smartscreen"></a>SmartScreen

SmartScreen 旨在帮助你安全浏览 Web。  访问网站或下载文件时，SmartScreen 会检查 URL 或文件的信誉。  如果 SmartScreen 确定网站或文件有恶意，则会阻止你访问网站或下载文件。

:::image type="complex" source="./media/smart-screen.png" alt-text="SmartScreen。" lightbox="./media/smart-screen.png":::
   SmartScreen
:::image-end:::

浏览 Web 时，SmartScreen 将网站和下载分类为主要流量、危险或未知。  主要流量是被 SmartScreen 确定为可信的网站。  如果转到标记为危险的网站，SmartScreen 将立即阻止你访问此网站。  转到未知网站时，SmartScreen 会检查其信誉以确定是否应访问此网站。

SmartScreen 采用三种类型的信誉检查。

1. SmartScreen 会根据本地列表检查你访问的站点的 URL，以确定该站点是主要流量的一部分还是已知危险站点。 访问主要流量网站时，SmartScreen 不会向 SmartScreen 服务发送 URL。  如果 URL 位于危险网站的本地列表中，SmartScreen 就会阻止它，以防加载恶意 Web 内容的任何部分。  Microsoft Edge 定期将更新的主要流量和危险网站列表下载到设备。

2. SmartScreen 对 URL 执行同步信誉检查。  SmartScreen 检查未归类为顶级流量的所有 URL。  Microsoft Edge将 URL、有关站点的相关信息、设备特有的标识符以及常规位置信息传递给 SmartScreen 服务，以确定站点的安全性。  Microsoft Edge 提供的信息使服务能够识别新的危险网站，并随时了解最新安全威胁。  URL 检查的结果本地存储在设备上，并且会在浏览器会话结束时自动清除。  所有 SmartScreen 服务请求均可使用 HTTPS 加密进行。

3. SmartScreen 检查下载的文件，以帮助防止对设备造成损害。  下载完成后，SmartScreen 会同步执行二进制文件信誉检查。  Microsoft Edge向 SmartScreen 发送有关文件的信息，例如文件哈希、文件名、下载 URI 和设备特有的标识符，以执行信誉检查。  所有 SmartScreen 请求均可使用 HTTPS 加密进行。  SmartScreen 服务会将检查结果发送回来，以便文件完全下载或不下载。  这些结果将本地存储在设备上。

SmartScreen 服务存储有关信誉检查的数据，并生成已知恶意 URL 和文件的数据库。  此数据存储在安全的 Microsoft 服务器上，仅用于 Microsoft 安全服务。  数据不会用于以任何方式识别或瞄准你。  清除浏览缓存将清除所有本地存储的 SmartScreen URL 数据。  清除下载历史记录将删除本地存储的任何有关文件下载的 SmartScreen 数据。

默认情况下，Microsoft Edge 将启用 SmartScreen。  若要禁用 SmartScreen，请导航到 `edge://settings/privacy`，在“安全性”**** 下禁用“Microsoft Defender SmartScreen”**** 设置。  对于与设备上 Microsoft Edge 安装相关的所有配置文件，此设置相同。  此设置不会跨设备同步。  此设置适用于 InPrivate 浏览和来宾模式。  如果设备是通过组织设置的组策略进行管理的，则设置会反映在 Microsoft Edge 中。  若要查看设置，请导航到 `edge://settings/privacy`。  有关 SmartScreen 的详细信息，请导航到 [SmartScreen：常见问题解答](https://support.microsoft.com/help/17443)。

此外，SmartScreen 还可以检查下载文件的 URL，确定是否有任何内容可能归类为不需要的应用。  阻止可能不需要的应用有助于提供更高效、高性能和更愉悦的 Windows 体验。  默认情况下，该设置处于关闭状态，并且仅在Windows 10和更高版本的设备上可用。  若要启用该功能，请导航到 `edge://settings/privacy`，启用“阻止可能不需要的应用”**** 设置。  有关如何对可能不需要的应用进行分类的详细信息，请导航到[可能不需要的应用程序 (PUA)](/windows/security/threat-protection/intelligence/criteria#potentially-unwanted-application-pua)。  有关如何配置设置的详细信息，请导航到[检测并阻止可能不需要的应用程序](/windows/security/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)。


<!-- ====================================================================== -->
## <a name="speech-recognition"></a>语音识别

若要将语音转换为文本，Microsoft Edge 支持 [Web 语音 API](https://wicg.github.io/speech-api)。  如果网站所含 Web 功能需要将语音捕获和转换为文本并请求访问你的麦克风，则 Microsoft Edge 会将捕获的音频发送到 Microsoft 服务，将其转换为文本。  录制的音频通过与 Microsoft Azure 认知服务的安全 HTTPS 连接使用随机生成的令牌发送。  不会出于任何目的存储录制的音频内容。  文本将发送回你的设备，然后发送到网站。

若要关闭将语音转换为文本，可以拒绝任何提示许可的站点的麦克风访问。  若要关闭所有网站的麦克风权限，请导航到 `edge://settings/content/microphone`。


<!-- ====================================================================== -->
## <a name="spellcheck"></a>拼写检查

当你在浏览器中输入时，Microsoft Edge 将检查拼写。  拼写检查服务已在设备本地完成。 Microsoft Edge不会将有关键入的信息发送给 Microsoft 进行拼写检查。 可以关闭该功能。 导航到 `edge://settings/languages`。 在 **"检查拼写"中**，关闭每种所需语言的设置。

向 Microsoft Edge 添加新语言后，浏览器将使用 HTTPS 将新语言字典下载到设备。  该字典用于内置拼写检查服务。  从 Microsoft Edge 设置中删除语言将从设备中删除字典。  来宾模式不使用来自配置文件或任何添加的语言的自定义字典。  若要添加或删除本地字典中的单词，请导航到 `edge://settings/languages`，在“检查拼写”**** 下选择“添加或删除单词”****。


<!-- ====================================================================== -->
## <a name="suggest-similar-sites"></a>建议类似网站

为了帮助解决地址栏中导致网站错误的 URL 拼写错误，Microsoft Edge 可能会建议使用正确的 URL。  出现网站导航错误时，Microsoft Edge 会将 Web 地址的域发送到 Microsoft 服务，以建议更正的 URL。  Microsoft Edge 不包含域中的标识符或令牌。  如果服务找到建议，它将返回建议的 URL。  Microsoft 存储不正确的域和建议的域。 帮助改进服务。  为了帮助导航到正确的网站，默认情况下将启用该功能。  若要关闭该功能，请导航到 `edge://settings/privacy`，然后在“服务”**** 下禁用“建议在找不到网站时显示类似网站”**** 设置。


<!-- ====================================================================== -->
## <a name="sync"></a>同步

使用Microsoft 帐户登录Microsoft Edge可跨所有已登录版本的Microsoft Edge同步浏览数据。 可以同步浏览历史记录、收藏夹、设置、表单填充数据（包括地址等）、密码、扩展、打开选项卡和集合。 可以单独打开或关闭每个同步的数据类型。

收藏夹包括之前在早期版本的Microsoft Edge中预留的任何选项卡，这些选项卡与收藏夹的其余部分同步。 从 Microsoft Edge 的一个已登录版本中删除或修改收藏夹或其他数据，将同步到已启用同步的 Microsoft Edge 的所有其他已登录版本。  若要管理同步配置，请导航到 `edge://settings/profiles/sync`。  你的同步设置可能由组织进行管理。

:::image type="complex" source="./media/sync.png" alt-text="将同步设置设为开启的图像。" lightbox="./media/sync.png":::
   同步设置已开启
:::image-end:::

为了使同步正常工作，提供同步体验所需的所有设备连接和配置数据将发送到 Microsoft。 同步数据包括设备的名称、制作和型号。 若要删除同步数据，请导航到 [Microsoft 设备仪表板](https://account.microsoft.com/devices)。 若要管理同步收藏夹，请导航到 `edge://favorites`。 若要管理所有其他数据类型，请导航到 `edge://settings/profiles`。

使用Microsoft 帐户或工作或学校帐户登录Microsoft Edge时，Microsoft Edge将在 Microsoft 服务器中存储数据隐私设置的首选项。 Microsoft Edge将仅使用存储的设置，以便在开始在其他设备上使用Microsoft Edge或登录到Microsoft Edge时更轻松地迁移体验。

在浏览器和 Microsoft 服务器之间传输时，将通过 HTTPS 加密传输所有同步数据。  同步的数据同样以加密状态存储在 Microsoft 服务器中。  敏感数据类型（如地址和密码）将在同步前在设备上进一步加密。  如果使用工作或学校帐户，所有数据类型在同步之前都会使用 Microsoft 信息保护进一步加密。  将存储所有其他同步数据类型，直至你删除数据、删除帐户或者帐户处于非活动状态。  帐户 ID 附加到所有同步数据，因为需要使用 ID 才能跨多个设备执行同步。

InPrivate 和来宾模式浏览数据不会同步到你的 Microsoft 帐户。  但是，在 InPrivate 会话期间创建的收藏夹跨已登录版本的 Microsoft Edge 同步。


<!-- ====================================================================== -->
## <a name="tips-and-recommendations"></a>提示和建议

Microsoft Edge 希望为你提供相关的提示和建议，以便在使用浏览器的过程中获得最佳体验。  Microsoft Edge 使用可用的设备连接和配置数据来提供相关的提示和建议。  此数据将由你的操作系统、区域设置、浏览器设置以及其他设备连接和配置数据组成。  将使用你的浏览器所特有的可重置标识符，通过安全的 HTTPS 连接发送该数据。  对于设置Microsoft Edge时Windows 10和更高版本的设备，我们遵循 Windows 中定制的体验。  [深入了解 Windows 中的定制体验](https://support.microsoft.com/help/4468236/diagnostics-feedback-and-privacy-in-windows-10-microsoft-privacy)。

在 InPrivate 浏览或来宾模式下，不会发送此数据。


<!-- ====================================================================== -->
## <a name="tracking-prevention"></a>跟踪防护

Microsoft Edge 旨在检测和阻止已知跟踪器。  用户可以从三个跟踪防护级别中进行选择：“基本”、“平衡”和“严格”。  为了保护用户隐私，默认情况下选择“平衡”。  Microsoft Edge 使用已知跟踪器的开源列表，在页面上加载任意跟踪器之前对其进行检测。  列表更新时，会定期将列表下载到设备。  出于统计目的，被阻止的跟踪器数和这些跟踪器名称将本地存储在设备上。  若要清除数据，请导航到 `edge://settings/privacy/blockedTrackers`。  检测和阻止跟踪器在设备本地上进行。  若要禁用跟踪防护，请导航到 `edge://settings/privacy`。  有关跟踪防护的详细信息，请导航到[了解 Microsoft Edge 中的跟踪防护](https://support.microsoft.com/help/4533959)。

可使用以下组策略“[启用 Microsoft Edge 中的组件更新](/deployedge/microsoft-edge-policies#componentupdatesenabled)”禁用列表更新。

:::image type="complex" source="./media/tracking-prevention.png" alt-text="跟踪防护。" lightbox="./media/tracking-prevention.png":::
   跟踪防护
:::image-end:::


<!-- ====================================================================== -->
## <a name="translate"></a>翻译

在 Microsoft Edge 中，你可以浏览 Web 并将网页翻译为你选择的语言。 Microsoft Edge 使用 [Microsoft Translator](https://azure.microsoft.com/services/cognitive-services/speech-translation/) 来翻译网页。 此功能最初使用设备上的库来采样网页的某些可见部分，以检测原始语言。 如果检测到的语言不是你的首选语言之一，则 Microsoft Edge 会将该网页翻译为首选语言或所选择的其他语言。 然后，可以通过选择“**翻译**”来翻译页面。 可通过从\<a language\>复选框中选择 **"始终翻译页面**"，以该语言自动翻译所有页面。

Microsoft Edge 不会在未经你允许的情况下翻译网页。 如果确实决定翻译，Microsoft Edge 则通过安全的 HTTPS 连接将要翻译的网页文本，以及 *目标* 和 *源* 语言和服务令牌发送到 Microsoft Translator。 服务令牌不包含任何用户个人身份信息。 [Microsoft Translator](https://azure.microsoft.com/services/cognitive-services/speech-translation/) 随后处理文本，以删除任何标识符（如电子邮件或电话号码）并存储文本以改进服务。 [Microsoft 隐私声明 - Microsoft 隐私](https://privacy.microsoft.com/privacystatement) 下介绍了此通信的详细信息。

要停止 Microsoft Edge 提供翻译网页服务，请完成以下步骤。

1. 导航到  `edge://settings/languages`。
1. 关闭“ **询问是否翻译非你所用语言的网页**”  切换开关并关闭网页。


<!-- ====================================================================== -->
## <a name="travel"></a>旅行

当你执行与旅行相关的联机活动时，Microsoft Edge 可帮助你找到有关旅行的建议。  为了帮助你在联机规划旅行时查找建议，Microsoft Edge 从 Microsoft 旅行服务将旅行域列表下载到客户端。

在你访问网站时，Microsoft Edge 在本地确定你所在的网站是否为旅行域。  如果确认该网站是与旅行相关的网页，Microsoft Edge 则将域、航班日期、出发和到达位置和乘客计数以及有关 Microsoft Edge 和 Cookie（如果允许 Cookie）的信息发送到服务。  此数据不包括任何个人身份信息，并通过 HTTPS 发送。

Microsoft Edge 旅行功能需要与必应共享 Cookie 信息。  例如，可以将 Cookie 用于调试、欺诈检测和分析。  在浏览器中访问 Bing.com 并更新必应页面上的任何设置时，Bing.com 将在浏览器中创建 Cookie 并将信息存储在 Cookie 中。  此 Cookie 在 Bing.com 页面之间共享，并由 Microsoft Edge 将此 Cookie 发送到 Microsoft 旅行服务，以保持你的体验一致。

默认情况下，旅行服务处于启用状态。  如果要在 Microsoft Edge 中更改“旅行”设置，请执行以下操作：
1. 导航到 `edge://settings/privacy`。
2. 在页面底部的“**服务**”部分中，禁用设置“**在 Microsoft Edge 中显示旅行建议**”。


<!-- ====================================================================== -->
## <a name="web-apps-and-pinned-sites"></a>Web 应用和已固定网站

Microsoft Edge使你能够安装网站开发人员创建的 Web 应用，并固定你最喜欢的网站。

固定网站时，会将其添加到任务栏或快捷栏。  数据本地存储在设备上。  对于某些站点，有关网站是否已固定的信息与网站共享，因此站点不知道是否提示固定。  可通过任务栏或快捷栏管理已固定网站。  已固定网站在 Microsoft Edge 窗口中打开，并使用与特定版本的 Microsoft Edge 相同的网站权限和诊断数据设置。


<!-- ====================================================================== -->
## <a name="webview"></a>WebView

Microsoft Edge WebView 控件允许应用开发人员在 Windows 7、Windows 10 及更高版本的本机应用程序中托管 Web 内容。  托管 WebView2 实例的应用程序可能会向 Microsoft 发送诊断数据。 诊断数据可以包括你如何使用Microsoft Edge和你访问的站点。

若要启用诊断数据收集，请导航到 `edge://settings/privacy`。 打开 **可选诊断数据** 设置。 若要在 Windows 10 上禁用 Microsoft Edge 故障诊断数据收集，请打开“**开始**” > “**设置**” > “**隐私**”并选择“**诊断和反馈**”。 若要关闭所有其他平台的诊断数据收集，请导航到 `edge://settings/privacy`。 **通过发送有关如何使用浏览器、访问的网站和故障报告设置的可选诊断数据，关闭帮助改进 Microsoft 产品**。 托管 Microsoft Edge WebView 的应用程序可能会收集受开发人员数据收集管理和相关隐私策略约束的其他数据。


<!-- ====================================================================== -->
## <a name="windows-defender-application-guard"></a>Windows Defender 应用程序防护

Windows Defender 应用程序防护 (WDAG) 是一项适用于组织的功能。  打开Windows Defender 应用程序防护时，Microsoft Edge打开隔离容器内不受信任的站点。 使用容器有助于保护组织中的资源免受恶意站点或网络钓鱼攻击。 仅对组织管理的组策略启用此功能。 它仅适用于最新版本的 Windows 10 和更高版本。 WDAG 收集有关在独立容器中打开不受信任的网站的产品改进诊断数据（例如打开新应用程序防护窗口所需的时间）。

在你同意后，WDAG 还会收集有关如何使用浏览器的信息以及有关你访问的网站的信息。  若要在 Windows 10 上禁用 Microsoft Edge 故障诊断数据收集，请打开“**开始**” > “**设置**” > “**隐私**”并选择“**诊断和反馈**”。  若要禁止所有其他平台的诊断数据收集，请在正常浏览会话中导航到 `edge://settings/privacy`，然后禁用“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品”**** 设置。


<!-- ====================================================================== -->
## <a name="windows-information-protection"></a>Windows 信息保护

Windows 信息保护 (WIP) 有助于防止意外泄漏公司信息。 它仅适用于组织通过组织管理的组策略。 为标识为公司资产的站点启用 WIP。 通过地址栏中的“管理”图标标识属于企业资产的网站。 WIP 可防止从浏览器复制和粘贴，或将某些文件上传到组织外部的站点。

:::image type="complex" source="./media/w-i-p.png" alt-text="Windows 信息保护。" lightbox="./media/w-i-p.png":::
   Windows 信息保护
:::image-end:::

如果你的 Microsoft Edge 版本启用了 WIP，该浏览器将收集事件日志，并将其发送给你的组织。  如果 WIP 已打开，则无法选择退出数据收集。  WIP 只适用于 2016 年 8 月或更高版本的 Windows 10 版本。  有关由 WIP 捕获的事件日志的详细信息，请导航到[如何收集 Windows 信息保护 (WIP) 审核事件日志](/windows/security/information-protection/windows-information-protection/collect-wip-audit-event-logs)。


<!-- ====================================================================== -->
## <a name="thank-you"></a>谢谢！

Microsoft Edge 可通过 [Chromium](https://www.chromium.org) 开源项目和其他开源软件实现。  若要查看所有软件积分，请导航到 `edge://credits`。  [Google Chrome 隐私白皮书](https://www.google.com/chrome/privacy/whitepaper.html)被用作收集 Chromium 开源项目相关信息的来源。


<!-- ====================================================================== -->
## <a name="getting-in-touch-with-the-microsoft-edge-team"></a>与 Microsoft Edge 团队联系

Microsoft Edge 团队将始终倾听客户的意见，且非常重视客户的反馈。  若要在 Microsoft Edge 中提供反馈，请打开“**设置和更多**” > “**帮助和反馈**”并选择“**发送反馈**”。  对于渐进式 Web 应用 (PWA)，请打开“**设置和更多(...)**”并选择“**向 Microsoft 发送反馈**”。  提供有关反馈的详细信息，但所有其他信息都是可选的。

如果从Microsoft Edge配置文件检测到电子邮件，则会预先填充当前站点的 URL 和相关诊断数据。 诊断数据可以包含有关你打开的Microsoft Edge功能和浏览器使用的数据。 还可以选择包括屏幕截图、设备中的文件以及浏览器的录制。 如果提供可选内容，则可以包含个人数据。 数据仅用于诊断和产品改进目的。

用户反馈将通过 HTTPS 安全发送到 Microsoft，并存储在安全的 Microsoft 服务器上。  如果你包含电子邮件地址，并且在 Microsoft Edge 隐私设置中启用了“通过发送有关如何使用浏览器的可选诊断数据、访问的网站和故障报告来帮助改进 Microsoft 产品****”设置，则你设备上的浏览器安装所特有的标识符将与你的反馈相关联。  如果你已使用Microsoft 帐户登录到Microsoft Edge，则你的反馈将与你的帐户相关联。  所有诊断数据（包括诊断日志、记录和附件）最多保存 30 天。  剩下的反馈数据（包括可选的屏幕截图）最多保存 15 个月。  如果你提供了含反馈项的电子邮件，可提出 [请求](https://www.microsoft.com/concern/privacy) 以删除反馈。
