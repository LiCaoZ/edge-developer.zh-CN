---
title: 为 WebView2 设置开发环境
description: 为 WebView2 开发设置开发环境。  设置 git、Visual Studio 和 Microsoft Edge 的预览频道，并克隆 WebView2Samples 存储库。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 10/26/2022
ms.openlocfilehash: 9b5a539ade651329cf53a7eb333036536cd5061d
ms.sourcegitcommit: 31669c03063cb6de515ba9c6d57a9cd8658f445e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2022
ms.locfileid: "12841142"
---
# <a name="set-up-your-dev-environment-for-webview2"></a>为 WebView2 设置开发环境

本文介绍用于 WebView2 开发的开发环境的常规用途设置。  一些入门教程指向此处的初步设置步骤，然后添加特定于平台或特定于项目的设置步骤。


<!-- ====================================================================== -->
## <a name="install-visual-studio"></a>安装 Visual Studio

1. 安装 [Visual Studio](https://visualstudio.microsoft.com) 2015 或更高版本，例如 Visual Studio Professional 2019。  大多数 WebView2 示例都是使用 Visual Studio 2019 创建和测试的。  如果示例是使用 Visual Studio 2019 创建的，则应先在 Visual Studio 2019 中生成并运行该示例，然后再在 Visual Studio 2022 中使用示例。

   WebView2 示例专为 Microsoft **Visual Studio** 设计，而不是 Microsoft **Visual Studio Code**。

   如果要安装 Visual Studio，则可以立即接受默认值：此时可以单击“ **安装**”，然后拒绝安装工作负载。  稍后，当你打开特定 `.sln` 文件时，Visual Studio 将提示你安装适合平台的工作负载。


<!-- ====================================================================== -->
## <a name="install-a-preview-channel-of-microsoft-edge"></a>安装 Microsoft Edge 的预览频道

1. 在受支持的操作系统 [ (OS) 上安装任何 Microsoft Edge Insider (预览版) Channel](https://www.microsoftedgeinsider.com/download) (Beta、Dev 或 Canary) ：
   *  Windows 7
   *  Windows 8.1
   *  Windows 10
   *  Windows 11

建议使用 Canary 通道。  所需的最低版本为 82.0.488.0。

若要使用 WebView2 SDK 的预发行版，需要 Microsoft Edge 的预览频道。  通过预发布 SDK，可以针对最新的 API 测试应用，并试用最新的 API。


<!-- The h3 section [Clone or download the WebView2Samples repo](../get-started/win32.md#download-or-clone-the-webview2samples-repo) in _Get started with WebView2 in Win32 apps_ links to here -->
<!-- ====================================================================== -->
## <a name="download-the-webview2samples-repo"></a>下载 WebView2Samples 存储库

有两个包含 WebView2 示例的存储库：
*  [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)
*  [WebView2Browser 存储库](https://github.com/MicrosoftEdge/WebView2Browser)

可以将存储库下载为 `.zip` 文件，也可以克隆存储库。

*  如果将存储库 (下载为 `.zip` 文件) ，则会获得存储库的快照副本。  然后，可以稍后下载存储库的另一个更新副本。

*  如果克隆存储库，可以使用 git 命令或各种开发应用的功能更新本地副本。


若要将存储库 (下载为 `.zip` 文件) ：

1. 在新窗口或选项卡中打开 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) (或 [WebView2Browser 存储库](https://github.com/MicrosoftEdge/WebView2Browser)) 。

1. 单击 GitHub 存储库右上角的绿色“ **代码** ”按钮，然后单击“ **下载 ZIP**”。

   ![下载 WebView2Samples 存储库。](../media/download-the-webview2-samples-repo.png)

   Microsoft Edge 中将显示 **“下载”** 弹出窗口：

   ![Microsoft Edge 工具栏中的“设置和更多”图标。](../media/settings-and-more-edge-icon.png)

   在 Microsoft Edge 中，如果 **“下载** ”弹出窗口不可见，请单击“ **设置和更多** (...) 然后单击” **下载**”。

1. 在 **“下载”** 弹出窗口中，将鼠标悬停在 右侧 `WebView2Samples-main.zip` ，然后单击“ **在文件夹中显示** (文件夹) ”图标。

   建议不要单击“ **打开文件** ”链接，因为这会立即解压缩“下载”区域中的文件，这可能使移动到所需位置 (更困难，) 较慢。

1. 将 `WebView2Samples-main.zip` 文件从 Downloads 目录复制或剪切到常规目录，例如 `Documents`。

1. 解压缩文件并 `WebView2Samples-main.zip` 记下解压缩的文件的位置。

   ![下载的解压缩的 WebView2Samples 存储库。](../media/downloaded-samples-repo-unzipped.png)

1. 研究主目录的突破。

   `-main` 是此下载的目录快照所表示的存储库分支的名称。  可以在 GitHub 切换到其他分支，然后下载 ，例如 `WebView2Samples-smoketest-1.0.1054.27-prerelease-testing.zip`。  在这种情况下，下载 `.zip` 的文件是存储库分支 `smoketest-1.0.1054.27-prerelease-testing` 的快照。  本文档假定你已 `main` 下载存储库的 分支。

1. 建议：将根目录从 `WebView2Samples-main` 重命名为 `WebView2Samples`，以匹配存储库名称和路径。


<!-- The h3 section [Clone or download the WebView2Samples repo](../get-started/win32.md#download-or-clone-the-webview2samples-repo) in _Get started with WebView2 in Win32 apps_ links to here -->
<!-- ====================================================================== -->
## <a name="clone-the-webview2samples-repo"></a>克隆 WebView2Samples 存储库

可以将存储库下载为 `.zip` 文件，也可以克隆存储库。

*  如果将存储库 (下载为 `.zip` 文件) ，则会获得存储库的快照副本。  然后，可以稍后下载存储库的另一个更新副本。

*  如果克隆存储库，可以使用 git 命令或各种开发应用的功能更新本地副本。


若要克隆 `WebView2Samples` 存储库 (或 `WebView2Browser` 存储库) ，必须先安装 git。  可以如上所述下载存储库，也可以克隆它。

### <a name="install-git"></a>安装 git

1. 如果要克隆 `WebView2Samples` 存储库 (而不是) 下载存储库，如果尚未安装 git， [请下载](https://git-scm.com/downloads) 并安装它。


### <a name="obtain-the-url-for-cloning-the-webview2samples-repo"></a>获取用于克隆 WebView2Samples 存储库的 URL

1. 在新窗口或选项卡中打开 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples) 。

1. 单击 GitHub 存储库右上角的绿色 **“代码** ”按钮，选择“ **克隆**”，然后单击“ **复制** ”图标 (，或者选择文本框中的 HTTPS URL 字符串并将其复制到) 。

   ![克隆 WebView2Samples 存储库。](../media/clone-the-webview2-samples-repo.png)

1. 确定要使用哪个工具在本地克隆存储库：
   *  Visual Studio
   *  GitHub Desktop
   *  Git Bash shell 或命令提示符

接下来，将 GitHub 存储库克隆到本地驱动器。  为此，请针对要使用的工具执行下面的相应步骤。


### <a name="cloning-the-repo-by-using-visual-studio"></a>使用 Visual Studio 克隆存储库

如果要使用 Visual Studio 将 GitHub 存储库克隆到本地驱动器：

1. 在 Visual Studio 中，选择“ **文件** > **克隆存储库**”。

1. 输入从 GitHub 存储库复制的 URL。

1. 在同一对话框或文件资源管理器实用工具中，可以在可写位置创建常规用途根 `git` 目录或 `GitHub` 文件夹，然后选择该目录，以便将存储库作为新目录克隆到该位置。

   例如，可以在父文件夹中创建存储库： `C:\Users\myUserName\Documents\GitHub\`，以便克隆操作将创建新目录 `C:\Users\myUserName\Documents\GitHub\WebView2Samples`。

已将存储库克隆到本地驱动器。  跳到下面的下一个主要部分。


### <a name="cloning-the-repo-by-using-github-desktop"></a>使用 GitHub Desktop 克隆存储库

如果要使用 GitHub Desktop 将 GitHub 存储库克隆到本地驱动器：

1. 安装 [GitHub Desktop](https://desktop.github.com)。

1. 在 GitHub Desktop 中，选择“ **文件** > **克隆存储库**”。

1. 在 Visual Studio 或 GitHub Desktop 中，输入从 GitHub 存储库复制的 URL。

1. 在同一对话框或文件资源管理器实用工具中，可以在可写位置创建常规用途根 `git` 目录或 `GitHub` 文件夹，然后选择该目录，以便将存储库作为新目录克隆到该位置。

   例如，可以在父文件夹中创建存储库： `C:\Users\myUserName\Documents\GitHub\`，以便克隆操作将创建新目录 `C:\Users\myUserName\Documents\GitHub\WebView2Samples`。

已将存储库克隆到本地驱动器。  跳到下面的下一个主要部分。


### <a name="cloning-the-repo-by-using-git-bash-shell-or-a-command-prompt"></a>使用 Git Bash shell 或命令提示符克隆存储库

如果要改为使用 Git Bash shell 或命令提示符克隆存储库：

1. 将存储库克隆到本地驱动器，输入从 GitHub 存储库复制的 URL 字符串：

   ```Shell
   # example location where the repo directory will be added:
   cd c:/users/myusername/documents/github/
   git clone https://github.com/MicrosoftEdge/WebView2Samples.git
   ```

   ![使用 Git Bash shell 在所需的本地目标 git 或 GitHub 存储库目录中输入 git clone 命令。](../media/git-bash-git-clone-url-command.png)

   目录在本地驱动器上创建，位于指定的路径中，如下图所示：

   ![文件资源管理器显示克隆的 WebView2Samples 存储库的目录。](../media/file-explorer-cloned-webview2-samples-repo.png)

   已将存储库克隆到本地驱动器。


<!-- ====================================================================== -->
## <a name="open-a-webview2samples-sln-file-in-visual-studio"></a>在 Visual Studio 中打开 WebView2Samples .sln 文件

克隆或下载 `WebView2Samples` 存储库后，在 Visual Studio 中打开文件 `.sln` 。

1. 在存储库目录结构的本地副本中，找到文件 `.sln` 。  [WebView2Samples 存储库中的顶级自述文件](https://github.com/MicrosoftEdge/WebView2Samples#readme)提供了类似的概述。

1. `.sln`在 Visual Studio 中打开文件。  例如，打开 [WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/main/SampleApps/WebView2Samples.sln) 的本地副本。  此存储库的解决方案文件需要 Visual Studio，而不是Visual Studio Code。

1. 打开其中 `.sln` 一个文件。  例如，打开在 Microsoft Visual Studio 中作为路径`WebView2Samples-main/SampleApps/WebView2Samples.sln`) 下载的主 Win32 解决方案文件 [WebView2Samples/SampleApps/WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/main/SampleApps/WebView2Samples.sln) (本地副本。  在 Visual Studio 中打开该解决方案文件时，**解决方案资源管理器**包含以下项目：

   ![解决方案资源管理器 WebView2Samples 存储库，将 WebView2 示例显示为项目。](media/machine-setup-solution-file-webview2samples.png)


对于常规的初始开发环境设置，可以从存储库中打开任何类型的 `.sln` 文件 `WebView2Samples` ：

*  目录子目录中的特定于 `.sln` 平台的文件 `GettingStartedGuides` 。  这些教程与入门教程相匹配，并且是演示几个 API 功能的已完成示例。

*  目录中包含多个平台项目的 `SampleApps` Win32 `.sln` 文件。  这是一个全面的 API 演示。

*  目录子目录中的特定于 `.sln` 平台的文件 `SampleApps` 。  这些是全面的 API 演示。


<!-- ====================================================================== -->
## <a name="install-visual-studio-workloads"></a>安装 Visual Studio 工作负载

如果出现提示，请安装 Visual Studio 工作负载。  在 Microsoft Visual Studio 2019 或 2022 中从克隆或下载`WebView2Samples`的存储库打开`.sln`文件时，可能会看到“无法打开”对话框。

<!-- For example, the Win32 tutorial tells how to install a particular workload if prompted to, upon opening a particular sample.  For example, see [Install the "Desktop development with C++" workload](../get-started/win32.md#install-workloads) in _Get started with WebView2 in Win32 apps_. -->

1. 单击“ **确定”** 按钮。  然后，你可能会看到工作负载安装程序，例如：

   ![用于 .NET 桌面开发工作负荷的 Visual Studio 安装程序。](../media/visual-studio-installer-net-desktop-devmt-workload.png).

1. 选中该复选框，然后单击“ **安装** ”按钮。

   Visual Studio 安装程序针对平台的工作负荷运行：

   ![Visual Studio 安装程序，安装 .NET 桌面开发工作负荷。](../media/visual-studio-installer-for-platform-workload.png).

   可能会打开迁移报告日志文件页，例如 ：`file:///C:/Users/username/Documents/WebView2Samples-main/WebView2Samples-main/SampleApps/UpgradeLog.htm`

   ![多平台综合 API 示例的 Visual Studio 2022 工作负载安装程序迁移报告。](../media/migration-report-while-installing-workload.png)

   _若要缩放，请右键单击> **“在新选项卡中打开图像**”。_

   在上面， `-main` 下载的存储库文件存在 `.zip` 目录后缀，而不是克隆存储库时。

   Visual Studio 在 解决方案资源管理器 中打开所选`.sln`文件：

   ![在打开多平台综合 API 示例时运行工作负载安装程序后，Visual Studio 2022。](../media/vs2022-after-net-workload-installer.png)


<!--
maintenance links; keep:
Main, central copy:
[Install the WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) in _Set up your Dev environment for WebView2_
Secondary copies:
[Install the WebView2 SDK](../get-started/win32.md#step-6---install-the-webview2-sdk) in _Get started with WebView2 in Win32 apps_
[Install the WebView2 SDK](../get-started/winforms.md#step-3---install-the-webview2-sdk) in _Get started with WebView2 in WinForms apps_
[Install the WebView2 SDK](../get-started/wpf.md#step-3---install-the-webview2-sdk) in _Get started with WebView2 in WPF apps_
[Install the WebView2 SDK](../get-started/winui2.md#step-6---install-the-webview2-sdk) in _Get started with WebView2 in WinUI 2 (UWP) apps_
[Install the WebView2 SDK](../get-started/winui.md#step-4---install-the-webview2-sdk) in _Get started with WebView2 in WinUI 3 (Windows App SDK) apps_
-->
<!-- ====================================================================== -->
## <a name="install-the-webview2-sdk"></a>安装 WebView2 SDK

WebView2 SDK 包含由 Microsoft Edge 提供支持的 WebView2 控件，使你能够在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) 。

为每个文件的每个项目节点 `.sln` 安装一次 WebView2 SDK。  WebView2 SDK 安装仅适用于安装它的项目。

通过 Visual Studio 中的 `Microsoft.Web.WebView2` “NuGet 包管理器”面板安装 WebView2 SDK NuGet 包，而不是从 nuget.org 下载 **SDK NuGet 包** 。  克隆或下载 WebView2Samples 存储库后，在 Visual Studio 中打开存储库 `.sln` 之一，并右键单击解决方案中的项目节点。  使用 **“NuGet 包管理器** ”面板将 `Microsoft.Web.WebView2` SDK 安装为 NuGet 包。

SDK `Microsoft.Web.WebView2` 在发布和预发布版本中可用。  若要开始，建议使用发布版本。


安装 WebView2 SDK，如下所示：

1. `.sln`在 Visual Studio 中打开文件。  例如，打开 [WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/main/SampleApps/WebView2Samples.sln) 的本地副本。  此存储库的解决方案文件需要 Visual Studio，而不是Visual Studio Code。

1. 在 **解决方案资源管理器**中，右键单击解决方案的项目节点，例如 **WebView2GettingStarted** 项目节点 (而不是解决方案节点) 然后选择 **“管理 NuGet 包**”。

   下图显示了特定的 .sln 文件和项目：使用想要将 SDK 安装到的项目中：

   ![管理 NuGet 包。](../media/manage-nuget-packages.png)

   **“NuGet 包管理器**”选项卡在 Visual Studio 中打开。

1. 在 **“NuGet”** 窗口中，单击“ **浏览** ”选项卡。

1. 在搜索栏右侧，清除“ **包括预发行版** ”复选框 (，除非你知道需要预发行版本的 SDK) 。

1. 在左上角的搜索栏中，键入 **Microsoft.Web.WebView2**。

1. 在搜索栏下方，单击 **Microsoft.Web.WebView2** 卡片。

1. 在右侧窗格中，单击“ **安装** (”或“ **更新**) ”按钮。  NuGet 将 WebView2 SDK 下载到计算机，供此项目使用。

   ![在 Visual Studio 的 NuGet 包管理器中选择“Microsoft.Web.WebView2”包。](../media/nuget.png)

   _若要缩放，请右键单击> **“在新选项卡中打开图像**”。_

1. 关闭 **“NuGet 包管理器** ”选项卡。

现在已安装 WebView2 SDK，因此开发环境现在已设置为将 WebView2 功能添加到 WebView2 应用。

另请参阅 [microsoft.Web.WebView2 SDK NuGet.org >](https://www.nuget.org/packages/Microsoft.Web.WebView2)。
