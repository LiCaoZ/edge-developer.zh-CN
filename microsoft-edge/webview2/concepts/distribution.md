---
title: 分发 WebView2 应用和 WebView2 运行时
description: 如何在发布使用 Microsoft Edge WebView2 的应用时分发 WebView2 运行时，方法为分发自动更新的 Evergreen Runtime，或分发 WebView2 运行时的固定版本。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 1/20/2022
ms.openlocfilehash: 0730b25914cad55e5eb81f6443ee6cfb35ee25dd
ms.sourcegitcommit: f3a81f0fe8edab8bef9c027efb7195c65445e109
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2022
ms.locfileid: "12311179"
---
# <a name="distribute-a-webview2-app-and-the-webview2-runtime"></a>分发 WebView2 应用和 WebView2 运行时

在发布使用 Microsoft Edge WebView2 的应用时，你需要通过分发自动更新的_Evergreen_ Runtime 或分发运行时的固定版本来分发 WebView2__ 运行时。

WebView2 应用依赖于客户端计算机上的 WebView2 运行时。  分发 WebView2 应用时，需要考虑如何将 WebView2 运行时分发到客户端计算机并更新它。


<!-- ====================================================================== -->
## <a name="the-webview2-runtime"></a>WebView2 运行时

WebView2 运行时是一个可再发行组件运行时，可用作 WebView2 __ (或) Web 平台的基础组件。  此概念类似于 Visual C++/.NET 应用的 .NET 运行时。  WebView2 运行时包含经过Microsoft Edge修改的二进制文件，这些二进制文件针对 WebView2 应用进行了微调和测试。  安装 WebView2 运行时后，它不会显示为用户可见的浏览器应用。  例如，用户没有浏览器桌面快捷方式或"开始"菜单中 **的条目** 。

有两种不同的方法将 WebView2 运行时分发和更新到客户端计算机：常青分发模式和固定版本分发模式。


<!-- ====================================================================== -->
## <a name="the-evergreen-runtime-distribution-mode"></a>Evergreen Runtime 分发模式

在 _Evergreen_ 分发模式下，WebView2 运行时不与你的应用打包，但最初使用联机引导程序或脱机安装程序安装到客户端上。  之后，WebView2 运行时将在客户端计算机上自动更新。  然后，你可以从最新的 WebView2 SDK 分发使用最新 WebView2 API 的 WebView2 应用更新。  建议大多数开发人员使用常青分发模式。

优点：
*  基础 Web 平台 (WebView2 运行时) 自动更新，无需你进行更多工作。
*  客户端系统上 WebView2 运行时所需的磁盘空间更少，因为 WebView2 运行时由客户端上的所有 WebView2 应用共享。
*  在符合条件的系统上，Microsoft Edge和 Evergreen WebView2 运行时的二进制文件在同一版本上时硬链接在一起。  此链接为磁盘占用、内存和性能带来了好处。

缺点：
*  WebView2 应用不能指定需要 WebView2 运行时的特定版本。


<!-- ====================================================================== -->
## <a name="the-fixed-version-runtime-distribution-mode"></a>固定版本运行时分发模式

在 _固定版本分发_ 模式下，下载特定版本的 WebView2 运行时，并随应用包中的 WebView2 应用一起打包它。  随应用打包的 WebView2 运行时仅由 WebView2 应用使用，客户端计算机上任何其他应用不会使用。

优点：
*  你可以更加控制 WebView2 运行时的版本控制。  你知道哪些 WebView2 API 可用于你的应用，因为你控制哪个版本的 WebView2 运行时可用于你的应用。  你的应用无需测试是否有最新的 API。

缺点：
*  你需要自己管理 WebView2 运行时。  WebView2 运行时不会在客户端上自动更新，因此若要使用最新的 WebView2 API，必须定期更新应用以及更新后的 WebView2 运行时。
*  如果安装了多个 WebView2 应用，则客户端上需要更多磁盘空间。
*  固定版本运行时无法通过使用安装程序进行安装。


<!-- ====================================================================== -->
## <a name="understanding-the-options-at-the-runtime-download-page"></a>了解运行时下载页上的选项

[WebView2 页面的](https://developer.microsoft.com/microsoft-edge/webview2#download-section)"下载**WebView2**运行时Microsoft Edge提供了几种用于将 WebView2 运行时分发到客户端计算机的选项。  了解此页的选项提供了一个很好的介绍，可帮助确定要使用哪种方法。

:::image type="content" source="../media/runtime-distrib-options.png" alt-text="用于分发和更新 WebView2 运行时的选项。" lightbox="../media/runtime-distrib-options.png":::

* 页面 **的 Evergreen Bootstrapper** 部分为联机用户提供在客户端计算机上运行的一个小的 Evergreen Runtime 引导程序。  引导程序在客户端上下载并安装相应的 WebView2 Evergreen Runtime。  可以通过几种不同的方式使用引导程序：

  * 指向引导程序的链接，使用从"获取链接"按钮 **获取** 的链接。  你的应用使用此链接以编程方式将引导程序下载到客户端并调用引导程序。  此方法无需将引导程序打包到你的应用中。  此方法依赖于 Microsoft 的 内容分发网络 (CDN) ，以获取引导程序。

  * 使用"引导程序 (部分中的"下载"**** 按钮下载引导程序****) ，然后将引导程序与你的应用一起分发。  在此方法中，使用应用安装程序/更新程序或应用本身打包引导程序，并调用应用中包含的引导程序。  此方法可避免依赖 Microsoft CDN，以获取引导程序。

* 页面 **的"常青独立** 安装程序"部分提供大型的独立 Evergreen 安装程序，主要面向脱机用户。  在此方法中，使用应用安装程序/更新程序或应用本身打包独立安装程序，并调用 Evergreen Standalone 安装程序。  此方法可避免依赖 Microsoft CDN获取运行时。

* 页面 **的"** 固定版本"部分提供"固定版本"运行时，它是随应用一起分发的特定版本的 WebView2 运行时。

对于大多数应用，建议使用常青分发模式。


<!-- ====================================================================== -->
## <a name="details-about-the-webview2-runtime"></a>有关 WebView2 运行时的详细信息

分发 WebView2 应用时，请确保客户端计算机上存在 WebView2 运行时。  此要求适用于常青和固定版本分发模式。

如果你想要使用固定版本分发模式，可以跳过接下来的几个部分并导航到有关固定版本运行时分发 [模式的详细信息](#details-about-the-fixed-version-runtime-distribution-mode)。

### <a name="servicing-the-webview2-runtime-through-windows-server-update-services-wsus"></a>通过 WSUS Windows Server Update Services (WebView2 运行时) 

请参阅管理[WebView2](enterprise.md#windows-server-update-services-wsus) Windows Server Update Services (中) WSUS 应用程序部分。

### <a name="runtime-or-browser-support-during-development-or-production"></a>开发或生产期间运行时或浏览器支持

在开发和测试期间，WebView2 应用可以使用以下任一选项作为支持 Web 平台：

* WebView2 运行时。  运行时通常提供与浏览器稳定渠道相同的 Web 平台功能Microsoft Edge节奏。  在生产环境中使用 WebView2 运行时，或针对用户当前具有的 Web 平台进行开发和测试。

* 预览体验 (预览) Microsoft Edge浏览器频道。  这些Microsoft Edge预览频道包括 Beta、Dev 和 Canary。  使用这种方法测试你的应用是否具有向前兼容性，以便你了解是否即将发生需要更新你的应用的新的更改。  有关详细信息，请导航到 [切换到预览频道以测试即将推出的 API 和功能](../how-to/set-preview-channel.md)。

WebView2 应用的生产版本只能将 WebView2 运行时用作支持 Web 平台，Microsoft Edge。

#### <a name="microsoft-edge-stable-channel-isnt-supported-for-webview2"></a>Microsoft Edge WebView2 不支持 Stable 渠道

不允许 WebView2 应用将稳定渠道Microsoft Edge Web 平台。  此限制可防止 WebView2 应用的生产版本依赖浏览器。  WebView2 应用在生产期间无法依赖浏览器，原因如下：

* Microsoft Edge用户设备上均存在此限制。  企业和教育中的许多设备与 Windows 更新断开连接，或者不是由 Microsoft 直接管理。  此类设备可能尚未Microsoft Edge安装。  要求 WebView2 应用的生产版本使用 WebView2 运行时Microsoft Edge可以避免使Microsoft Edge WebView2 应用的先决条件。

* 浏览器和应用具有不同的用例。  如果 WebView2 应用要求在客户端Microsoft Edge，这可能会导致 WebView2 应用出现意外的负面影响。  例如，IT 管理员可以阻止从特定版本更新浏览器，以保持浏览器与内部网站兼容。  要求 WebView2 应用的生产版本使用 WebView2 运行时（而不是浏览器）可使 WebView2 应用保持常青，即使客户端管理员阻止了浏览器更新。

* 与浏览器相反，WebView2 运行时针对应用方案进行开发和测试，在某些情况下，WebView2 运行时可能包含浏览器中尚未提供的 Bug 修复。

Evergreen WebView2 运行时将作为操作系统的一Windows 11一部分。 各种 WebView2 应用在运行前在操作系统设备上安装了 Evergreen Runtime Windows 11。  但是，某些设备可能未预安装运行时，因此，最佳做法是检查运行时是否存在于客户端上。

在应用创建 WebView2 之前，应用应检查 WebView2 运行时是否 (通过检查注册表项或调用 API) 并安装运行时（如果缺少）。  应用可以在安装或更新应用时执行此检查 (推荐) 或应用运行时。  若要检查运行时是否存在，请导航到下面的部署 [Evergreen WebView2 运行时](#deploying-the-evergreen-webview2-runtime) 。


<!-- ====================================================================== -->
## <a name="details-about-the-evergreen-runtime-distribution-mode"></a>有关 Evergreen Runtime 分发模式的详细信息

常青分发模式可确保 WebView2 应用充分利用最新的 WebView2 功能和安全更新。  常青分发模式具有以下特征：

* WebView2 运行时将自动更新，无需你进行更多工作。
* 所有使用 Evergreen 分发模式的 WebView2 应用都使用 Evergreen WebView2 运行时的共享副本，从而节省磁盘空间。
* 在符合条件的系统上，Microsoft Edge和 Evergreen WebView2 运行时的二进制文件在同一版本上时硬链接在一起。  此链接为磁盘占用、内存和性能带来了好处。

使用 WebView2 运行时的 Evergreen 分发模式时，WebView2 应用假定客户端具有最新的运行时。  对于客户端上的所有应用，你的应用不能要求 WebView2 运行时的特定版本。  在发布新的 WebView2 SDK 包时，WebView2 运行时的兼容版本已分发给客户端。  因此，WebView2 应用可以使用最新版本的 WebView2 SDK 中的 API。

有关详细信息，请导航到了解[浏览器版本和 WebView2。](./versioning.md)

### <a name="deploying-the-evergreen-webview2-runtime"></a>部署 Evergreen WebView2 运行时

设备上的所有 Evergreen 应用只需安装一次 Evergreen WebView2 运行时。  下载 [WebView2 运行时中](https://developer.microsoft.com/microsoft-edge/webview2#download-section) 提供了一些工具，可帮助你部署 Evergreen Runtime。

* 对于联机客户端 _：WebView2 运行时引导_ 程序是一个 (大约 2 MB) 安装程序。  WebView2 运行时引导程序从与用户设备体系结构匹配的 Microsoft 服务器下载并安装 Evergreen Runtime。
  * 在 WebView2 应用的安装部分，链接到引导程序。  使用链接以编程方式下载引导程序;选择上面的 **下载页面上** 的"获取链接"按钮。
  * 或者，下载引导程序，然后使用 WebView2 应用打包它。

* 对于脱机客户端 _：WebView2 运行时独立_ 安装程序是在脱机环境中安装 Evergreen WebView2 运行时的完整安装程序。

### <a name="installing-the-runtime-as-per-machine-or-per-user"></a>将运行时安装为每台计算机或每用户

最新的引导程序和独立安装程序支持每_台计算机_和每用户安装__ WebView2 运行时。

<!-- keep the 3 instances or variants of this passage in sync: instance 1: -->
如果从提升的进程或命令提示符运行安装程序，则运行时将按计算机 _安装_。  如果不从提升的进程或命令提示符运行安装程序，运行时将按用户 _安装_。  但是 _，每_用户安装将自动替换为每台计算机安装（如果__ 每台计算机Microsoft Edge Updater__ 已就位）。  每_计算机_Microsoft Edge Updater 作为更新程序Microsoft Edge，但 Canary 预览频道除外Microsoft Edge。

使用以下联机部署工作流或脱机部署工作流，以确保在应用启动之前已安装运行时。  可以根据方案调整工作流。  示例代码在示例 [存储库中提供](https://github.com/MicrosoftEdge/WebView2Samples#webview2-deployment)。

#### <a name="online-only-deployment"></a>仅联机部署

如果您具有假定用户具有 Internet 访问权限的仅联机部署方案，请使用以下工作流。

1. 在应用设置期间，运行测试以确保已安装 WebView2 运行时。  若要验证是否安装了运行时，请使用以下任一方法：

    *  方法 1：检查以下两个注册表位置的 `pv (REG_SZ)` WebView2 运行时的注册表项。  注册表 `HKEY_LOCAL_MACHINE` 项用于每 _台计算机_ 安装。  `HKEY_CURRENT_USE`注册表项用于_每用户_安装。

       对于 WebView2 应用程序，必须至少存在并定义其中一个注册表项。  如果 regkey 不存在，或者只有其中一个注册表项存在，但其值为 或为空字符串，这意味着 `null` WebView2 运行时未安装在客户端上。  检查这些注册表项以检测是否已安装 WebView2 运行时，并获取 WebView2 运行时的版本。  在 `pv (REG_SZ)` 下列两个位置查找。

       要检查的两个注册表位置位于 64 位Windows：

       ```
       HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}

       HKEY_CURRENT_USER\Software\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       ```

       要检查的两个注册表位置位于 32 位Windows：

       ```
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}

       HKEY_CURRENT_USER\Software\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       ```

    * 方法 2：运行 [GetAvailableCoreWebView2BrowserVersionString](/microsoft-edge/webview2/reference/win32/webview2-idl#getavailablecorewebview2browserversionstring) 并评估 `versionInfo` 是否是 `nullptr` 。  `nullptr` 指示未安装 WebView2 运行时。  此 API 返回 WebView2 运行时或 Beta、Dev 或 Canary Microsoft Edge (的任何已安装预览频道的版本) 。

1. 如果未安装运行时，在应用设置过程中，使用下载页面上的"获取链接"按钮 (链接) 以**** 编程方式下载 WebView2 运行时引导程序。

1. 通过发出以下命令调用 WebView2 运行时引导程序。

    <!-- keep the 3 instances or variants of this passage in sync: instance 2: -->

    如果从提升的进程或命令提示符运行以下命令，它将触发每 _台计算机_ 安装。  如果不从提升的进程或命令提示符运行命令，将进行每用户安装。 __  但是 _，每_用户安装将自动替换为每台计算机安装（如果__ 每台计算机Microsoft Edge Updater__ 已就位）。  每_计算机 Microsoft Edge_ Updater 作为更新的一Microsoft Edge，但 Canary 预览频道除外Microsoft Edge。  有关详细信息，请参阅 [将运行时安装为每计算机或每用户](#installing-the-runtime-as-per-machine-or-per-user)。<!-- since this link is provided, the present paragraph could be shortened -->

    ```Shell
    MicrosoftEdgeWebview2Setup.exe /silent /install
    ```

上述工作流具有多个优点：

* 仅在需要时安装运行时。
* 无需使用 WebView2 应用打包运行时安装程序。
* WebView2 运行时引导程序自动检测设备在平台 (体系结构) 然后安装匹配的 WebView2 运行时。
* 运行时以静默方式安装。

或者，你可以将 WebView2 运行时的 Evergreen Bootstrapper 打包到你的应用，而不是通过获取链接以编程方式按需下载引导程序。

#### <a name="offline-deployment"></a>脱机部署

如果你有脱机部署方案（其中应用部署必须完全脱机工作），请使用以下工作流。

1. 从将 [WebView2](https://developer.microsoft.com/microsoft-edge/webview2#download-section) 运行时下载到开发计算机下载 Evergreen Standalone Installer。  Evergreen 独立安装程序在客户端上安装 WebView2 Evergreen Runtime。

1. 在应用安装程序或更新程序中包括 Evergreen Standalone Installer。

1. 在应用设置期间，使用下列任一方法测试是否已安装 WebView2 运行时：

    * 检查 `pv (REG_SZ)` 以下两个位置的 WebView2 运行时的注册表项。  `HKEY_LOCAL_MACHINE`regkey 指示每台计算机安装， `HKEY_CURRENT_USE` 而 regkey 指示每用户安装。 对于 WebView2 应用程序，这两者都足够。 如果 regkey 不存在，或者如果存在 且 为 或为空字符串，则意味着 `null` WebView2 运行时未安装在客户端上。  使用注册表项可检测是否已安装 WebView2 运行时，并获取 WebView2 运行时的版本。  在 `pv (REG_SZ)` 下列位置查找：

       在 64 位Windows：

       ```text
       HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       HKEY_CURRENT_USER\Software\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       ```

       在 32 位Windows：

       ```text
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       HKEY_CURRENT_USER\Software\Microsoft\EdgeUpdate\Clients\{F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}
       ```

   * 或者，调用 [GetAvailableCoreWebView2BrowserVersionString](/microsoft-edge/webview2/reference/win32/webview2-idl#getavailablecorewebview2browserversionstring) 并检查 `versionInfo` 是否是 `nullptr` 。  `versionInfo`如果 `nullptr` 为 ，则意味着 WebView2 运行时未安装在客户端上。 如果在 Beta、Microsoft Edge或 Canary (安装预览频道，API 将) 该预览频道的版本信息。

1. 如果未安装 WebView2 运行时，请运行 Evergreen Standalone Installer。  如果要运行无提示安装，可以运行以下命令。

    <!-- keep the 3 instances or variants of this passage in sync: instance 3 -->

    如果从提升的进程或命令提示符运行以下命令，它将触发每 _台计算机_ 安装。  如果不从提升的进程或命令提示符运行命令，将进行每用户安装。 __  但是 _，每_用户安装将自动替换为每台计算机安装（如果__ 每台计算机Microsoft Edge Updater__ 已就位）。  每_计算机 Microsoft Edge_ Updater 作为更新的一Microsoft Edge，但 Canary 预览频道除外Microsoft Edge。  有关详细信息，请参阅 [将运行时安装为每计算机或每用户](#installing-the-runtime-as-per-machine-or-per-user)。<!-- since this link is provided, the present paragraph could be shortened -->

    ```Shell
    MicrosoftEdgeWebView2RuntimeInstaller{X64/X86/ARM64}.exe /silent /install
    ```

### <a name="test-your-app-for-forward-compatibility"></a>测试应用是否向前兼容

Web 在不断演变。  在常青分发模式下，WebView2 运行时在客户端上自动保持最新，以提供最新功能和安全修补程序。  如果使用 Evergreen 分发，为了确保 WebView2 应用与 Web 保持兼容，应设置测试基础结构。

Microsoft Edge Beta、Dev 和 Canary (预览频道) 快速了解 WebView2 运行时接下来将发生的内容。  针对预览频道定期测试 WebView2 Microsoft Edge，并更新应用或报告[问题（如果](https://github.com/MicrosoftEdge/WebViewFeedback)出现问题）。  Canary 是推荐的预览频道，因为它以最快节奏提供，并且具有最新的 API。

若要帮助你确定哪个频道正确，请导航到"Microsoft Edge[概述"。](/deployedge/microsoft-edge-channels)  可以在[测试Microsoft Edge下载](https://www.microsoftedgeinsider.com/download)预览体验成员频道，并使用或环境变量指示测试 `regkey` 应用的通道首选项。

有关详细信息，请导航到 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions)。  您还可以使用 WebDriver 自动执行 WebView2 测试，如自动执行和使用驱动程序测试[WebView2 Microsoft Edge中所述](../how-to/webdriver.md)。

### <a name="feature-detect-when-using-recent-apis"></a>使用最新 API 时的功能检测

<!-- the main section about QueryInterface is in versioning.md, so limit this section to a couple paragraphs -->

如果使用常青模式，当 WebView2 应用使用来自最新 SDK 的新 WebView2 API 时，应该使用 或 等方法，以确保新 API 存在于客户端计算机上。 `QueryInterface` `try-catch`  此功能检测是最佳做法，因为在某些情况下 WebView2 运行时未更新。

即使使用常青分发模式，WebView2 运行时也可能未更新，原因如下：
*  IT 管理员可以关闭 WebView2 运行时的更新，因为管理员可以控制其设备的更新。
*  脱机的客户端不会收到更新的 WebView2 运行时。

WebView2 运行时Microsoft Edge策略是分开的。  即使 IT 管理员已禁用 Microsoft _Edge_的自动更新，WebView2 __ 运行时仍将自动更新，除非管理员关闭运行时更新。  如果管理员禁用更新Microsoft Edge (更新是一种) ，这不会影响客户端计算机上可用的 WebView2 API。

有关详细信息，请导航到功能[检测以测试安装的运行时是否支持最近添加的 API。](../concepts/versioning.md#feature-detecting-to-test-whether-the-installed-runtime-supports-recently-added-apis)


<!-- ====================================================================== -->
## <a name="details-about-the-fixed-version-runtime-distribution-mode"></a>有关固定版本运行时分发模式的详细信息

对于具有严格兼容性要求的限制环境，请考虑使用固定版本分发模式。  固定版本分发模式以前称为 _自带的_。

在固定版本分发模式下，你可以控制更新应用的 WebView2 运行时的时间。  下载 WebView2 运行时的特定版本，然后使用 WebView2 应用打包它。  客户端上的 WebView2 运行时不会自动更新。  相反，你可以定期更新打包并随更新的应用一起分发的 WebView2 运行时。  固定版本方法不使用 WebView2 运行时的注册表项。

固定版本二进制文件超过 250 MB，并且会使你的应用包增大该大小。

若要使用固定版本分发模式：

1. 从下载 WebView2 运行时（作为程序包）下载 [WebView2](https://developer.microsoft.com/microsoft-edge/webview2#download-section)运行时的固定版本。

   可在此网站上下载最新版和第二个最新主要版本的修补程序最晚版本。  保留所需的任何版本的存档副本。

1. 使用命令行命令或 WinRAR 等解压缩工具解压缩 WebView2 运行时 `expand {path to the package} -F:* {path to the destination folder}` 包。  避免通过文件资源管理器解压缩，因为该方法可能无法生成正确的文件夹结构。

1. 在应用包中包括所有解压缩的固定版本二进制文件，这些二进制文件将在应用安装期间部署到目标计算机上。

1. 指示创建 WebView2 环境时固定版本二进制文件的路径。

   *  对于 Win32 C/C++，可以使用 [CreateCoreWebView2EnvironmentWithOptions](/microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions) 函数创建环境。  使用 `browserExecutableFolder` 参数指示包含 的文件夹的路径 `msedgewebview2.exe` 。

   *  对于 .NET，必须在 WebView2 属性生效 `Source` 之前指定环境。  对于 .NET，可以使用以下任一方法来指定环境：

       *  设置 (`CreationProperties` [上的 WPF](/dotnet/api/microsoft.web.webview2.wpf.webview2.creationproperties) / [WinForms](/dotnet/api/microsoft.web.webview2.winforms.webview2)) 属性 `WebView2` 。  使用 `BrowserExecutableFolder` `CoreWebView2CreationProperties` [WPF](/dotnet/api/microsoft.web.webview2.wpf.corewebview2creationproperties) / [WinForms](/dotnet/api/microsoft.web.webview2.winforms) (中的 成员) 指示固定版本二进制文件的路径。

       *  或者，使用 `EnsureCoreWebView2Async` ([WPF](/dotnet/api/microsoft.web.webview2.wpf.webview2.ensurecorewebview2async) / [WinForms) ](/dotnet/api/microsoft.web.webview2.winforms.webview2.ensurecorewebview2async)指定环境。  使用 `browserExecutableFolder` [CoreWebView2Environment.CreateAsync](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createasync) 中的 参数指示固定版本二进制文件的路径。

1. 将固定版本二进制文件打包并随你的应用一起提供。  根据情况更新二进制文件。

### <a name="known-issues-for-fixed-version"></a>固定版本的已知问题

*  目前，固定版本无法从网络位置或 UNC 路径运行。

*  在客户端上安装 WebView2 运行时的固定版本会导致Microsoft PlayReady[停止工作](https://www.microsoft.com/playready)。  按如下所示修复 PlayReady 设置。

   1. 找到在用户设备上部署固定版本程序包的路径，例如以下位置：

       ```text
       D:\myapp\Microsoft.WebView2.FixedVersionRuntime.87.0.664.8.x64
       ```

   1. 在用户设备上运行以下命令：

       ```shell
       icacls {Fixed Version path} /grant *S-1-15-2-2:(OI)(CI)(RX)
       icacls {Fixed Version path} /grant *S-1-15-2-1:(OI)(CI)(RX)
       ```

   1. PlayReady 现在应在用户的设备上运行。  若要确认 PlayReady 安装正确，在"**** 固定版本"文件夹**** 的"安全性"选项卡中，确保为 和 `ALL APPLICATION PACKAGES` 授予 `ALL RESTRICTED APPLICATION PACKAGES` 权限，如下所示：

       :::image type="content" source="../media/play-ready-permission.png" alt-text="PlayReady 的权限。" lightbox="../media/play-ready-permission.png":::

<!-- ====================================================================== -->
## <a name="files-to-ship-with-the-app"></a>要随应用一起提供的文件

`WebView2Loader`代码需要随应用一起提供。  这可以通过静态链接到应用 [二](../how-to/static.md)进制文件，或者包含与应用体系结构相匹配的 实现 `WebView2Loader.lib` `WebView2Loader.dll` 。

`WebView2Loader.dll` 是本机和特定于体系结构的二进制文件，因此你需要包含希望应用运行的所有二进制文件。  例如，对于 x86，将包括 的 x86 版本，而对于 `WebView2Loader.dll` AnyCPU，将包括 的 x86、x64 和 arm64 版本 `WebView2Loader.dll` 。  对于托管应用，从相应的特定于体系结构的文件夹 `WebView2Loader.dll` 加载 的正确版本。

示例本机应用文件夹结构：

```
\<myApp>
    \WebView2Loader.dll
```

对于 .NET 托管应用，还需要包括核心 WebView2 功能 () 和 `Microsoft.Web.WebView2.Core.dll` WPF/WinForms 特定功能 (或 `Microsoft.Web.WebView2.Winforms.dll` `Microsoft.Web.WebView2.WPF.dll`) 的 WebView2 .NET 程序集。

示例本机应用文件夹结构：

```
\<myApp>
    \Microsoft.Web.WebView2.Core.dll
    \Microsoft.Web.WebView2.Winforms.dll
    \Microsoft.Web.WebView2.WPF.dll
    \runtimes
        \win-arm64\native\WebView2Loader.dll (arm64)
        \win-x64\native\WebView2Loader.dll (x64)
        \win-x86\native\WebView2Loader.dll (x86)
```
