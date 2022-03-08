---
title: 为 WebView2 设置开发环境
description: 设置用于 WebView2 开发的开发环境。  设置 git、Visual Studio和预览频道的 Microsoft Edge，并克隆 WebView2Samples 存储库。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/18/2022
ms.openlocfilehash: 7de3c600f567c150f2724fa410120ff8258d1e2d
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433469"
---
# <a name="set-up-your-dev-environment-for-webview2"></a>为 WebView2 设置开发环境

本文介绍了 WebView2 开发开发环境的常规用途设置。  一入门一些教程指向此处，了解初步设置步骤，然后添加特定于平台或特定于项目的设置步骤。


<!-- ====================================================================== -->
## <a name="install-visual-studio"></a>安装Visual Studio

1. 安装 [Visual Studio](https://visualstudio.microsoft.com) 2015 或更高版本，如 Visual Studio Professional 2022。

   WebView2 示例专为 Microsoft **Visual Studio**设计，**Visual Studio Code。**

   如果要在 2022 Visual Studio，可以立即接受默认值;可以单击"安装"，此时拒绝安装 Workloads。****  Visual Studio打开特定文件时`.sln`，系统稍后会提示你安装适合平台的工作负载。


<!-- ====================================================================== -->
## <a name="install-a-preview-channel-of-microsoft-edge"></a>安装预览频道Microsoft Edge

1. 在受支持的[Microsoft Edge](https://www.microsoftedgeinsider.com/download)操作系统 () 操作系统 (安装任何预览体验预览体验成员) 预览 (版本) ：
   *  Windows 7
   *  Windows 8.1
   *  Windows 10
   *  Windows 11

我们建议使用 Canary 通道。  最低要求版本为 82.0.488.0。


<!-- ====================================================================== -->
## <a name="install-the-webview2-runtime"></a>安装 WebView2 运行时

1. （可选）安装 [WebView2 运行时](https://developer.microsoft.com/microsoft-edge/webview2)。

如果不确定，请跳过此步骤;你可以改为使用上Microsoft Edge预览频道。

请参阅 [了解不同的 WebView2 SDK 版本](../concepts/versioning.md)。


<!-- The h3 section [Download or clone the WebView2Samples repo](../get-started/win32.md#download-or-clone-the-webview2samples-repo) in _Get started with WebView2 in Win32 apps_ links to here -->
<!-- ====================================================================== -->
## <a name="download-the-webview2samples-repo"></a>下载 WebView2Samples 存储库

您可以将存储库下载为文件 `.zip` ，或克隆存储库。

*  如果以文件 (下载 `.zip` 存储库) ，将获取存储库的快照副本。  然后，你可以下载该存储库的另一个更新副本。

*  如果你克隆存储库，可以使用 git 命令或各种开发人员应用的功能更新本地副本。


若要将存储库下载 (文件，) `.zip` ：

1. 打开新 [窗口或选项卡中的 WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库。

1. 单击存储库**右上角**的绿色"代码"GitHub，然后单击"下载 **ZIP"**。

   ![下载 WebView2Samples 存储库。](../media/download-the-webview2-samples-repo.png)

   The **Download** pop-up appears in Microsoft Edge：

   !["设置"工具栏中的"Microsoft Edge"图标。](../media/settings-and-more-edge-icon.png)

   In Microsoft Edge， if the **Download** pop-up isn't visible， click **设置 and more** (...) and then click **Downloads**.

1. 在 **"下载"** 弹出窗口中，将`WebView2Samples-master.zip`鼠标悬停在 右侧，然后单击"在文件夹中显示****" (文件夹) 图标。

   建议不要单击"打开文件"链接，因为这**** 会立即解压缩"下载"区域中的文件，这会使移动到所需位置的 (和) 速度变慢。

1. 将文件从 `WebView2Samples-master.zip` 下载目录复制或剪切到常规目录，例如 `Documents`。

1. 解压缩 。`WebView2Samples-master.zip` 文件，并记下解压缩文件的位置。

   ![下载的解压缩的 WebView2Samples 存储库。](../media/downloaded-samples-repo-unzipped.png)

1. 研究主目录的分类。

   `-master` 是下载的目录快照表示的存储库分支的名称。  可以切换到其他分支，然后GitHub，例如 ， `WebView2Samples-smoketest-1.0.1054.27-prerelease-testing.zip`。  在这种情况下，下载的文件 `.zip` 是存储库 `smoketest-1.0.1054.27-prerelease-testing` 分支的快照。  本文档假定您下载了 `master` 存储库的分支。

1. 建议：将根目录从 重命名为 `WebView2Samples-master` `WebView2Samples`，以匹配存储库名称和路径。


<!-- The h3 section [Download or clone the WebView2Samples repo](../get-started/win32.md#download-or-clone-the-webview2samples-repo) in _Get started with WebView2 in Win32 apps_ links to here -->
<!-- ====================================================================== -->
## <a name="clone-the-webview2samples-repo"></a>克隆 WebView2Samples 存储库

您可以将存储库下载为文件 `.zip` ，或克隆存储库。

*  如果以文件 (下载 `.zip` 存储库) ，将获取存储库的快照副本。  然后，你可以下载该存储库的另一个更新副本。

*  如果你克隆存储库，可以使用 git 命令或各种开发人员应用的功能更新本地副本。


若要克隆存储库 `WebView2Samples` ，必须先安装 git。  可以下载存储库（如上所述）或克隆它。

### <a name="install-git"></a>安装 git

1. 如果你想要克隆存储库 `WebView2Samples` (而不是将其) ，并且如果 git 尚未安装，请下载 [git](https://git-scm.com/downloads) 并安装它。


### <a name="obtain-the-url-for-cloning-the-webview2samples-repo"></a>获取用于克隆 WebView2Samples 存储库的 URL

1. 打开新 [窗口或选项卡中的 WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库。

1. 单击 GitHub 存储库右上角的绿色"代码"按钮，选择"克隆"，然后单击"复制****"图标 (或者，选择**** 文本框中的 HTTPS URL 字符串，然后) 。****

   ![克隆 WebView2Samples 存储库。](../media/clone-the-webview2-samples-repo.png)

1. 确定要用于本地克隆存储库的工具：
   *  Visual Studio
   *  GitHub 桌面
   *  Git Bash shell 或命令提示符

接下来，将GitHub存储库克隆到本地驱动器。  为此，请针对想要使用的工具执行下面的相应步骤。


### <a name="cloning-the-repo-by-using-visual-studio"></a>使用方法克隆存储库Visual Studio

如果你想要使用 Visual Studio将GitHub存储库克隆到本地驱动器：

1. 在Visual Studio中，选择 **"文件** > **""Clone 存储库"**。

1. 输入从应用程序存储库复制GitHub URL。

1. `git` `GitHub`在同一对话框内或文件资源管理器实用工具中，可以在可写位置创建通用根目录或文件夹，然后选择该目录，以便存储库作为新目录克隆到该目录。

   例如，可以在父文件夹中创建存储库： `C:\Users\myUserName\Documents\GitHub\`，以便克隆操作将创建新目录 `C:\Users\myUserName\Documents\GitHub\WebView2Samples`。

你已将存储库克隆到本地驱动器。  跳到下面的下一个主要部分。


### <a name="cloning-the-repo-by-using-github-desktop"></a>使用桌面复制存储库GitHub存储库

如果你想要使用 GitHub Desktop 将GitHub存储库克隆到本地驱动器：

1. 安装[GitHub桌面](https://desktop.github.com)。

1. 在GitHub桌面"中，选择 **"文件** > **""Clone 存储库"**。

1. 在Visual Studio或GitHub桌面"中，输入从桌面存储库GitHub URL。

1. `git` `GitHub`在同一对话框内或文件资源管理器实用工具中，可以在可写位置创建通用根目录或文件夹，然后选择该目录，以便存储库作为新目录克隆到该目录。

   例如，可以在父文件夹中创建存储库： `C:\Users\myUserName\Documents\GitHub\`，以便克隆操作将创建新目录 `C:\Users\myUserName\Documents\GitHub\WebView2Samples`。

你已将存储库克隆到本地驱动器。  跳到下面的下一个主要部分。


### <a name="cloning-the-repo-by-using-git-bash-shell-or-a-command-prompt"></a>使用 Git Bash shell 或命令提示符克隆存储库

如果要改为使用 Git Bash shell 或命令提示符克隆存储库：

1. 将存储库克隆到本地驱动器，输入从本地驱动器存储库复制的 URL GitHub字符串：

   ```Shell
   # example location where the repo directory will be added:
   cd c:/users/myusername/documents/github/
   git clone https://github.com/MicrosoftEdge/WebView2Samples.git
   ```

   ![使用 Git Bash 命令行管理程序在所需的本地目标 git 或存储库目录中GitHub git clone 命令。](../media/git-bash-git-clone-url-command.png)

   目录在指定的路径本地驱动器上创建，如下图所示：

   ![显示克隆的 WebView2Samples 存储库的目录的文件资源管理器。](../media/file-explorer-cloned-webview2-samples-repo.png)

   你已将存储库克隆到本地驱动器。


<!-- ====================================================================== -->
## <a name="open-a-webview2samples-sln-file-in-visual-studio"></a>打开 WebView2Samples .sln 文件Visual Studio

下载或克隆存储库后`WebView2Samples`，在文件包`.sln`中打开Visual Studio。

1. 在存储库目录结构的本地副本中，找到文件 `.sln` 。  请参阅 Sample _Code for WebView2_中所有 [.sln 和 README.md](../code-samples-links.md#local-paths-for-sln-and-readmemd-files) 文件的本地路径。  [WebView2Samples 存储库的](https://github.com/MicrosoftEdge/WebView2Samples#readme)顶级自述文件提供了类似的概述。

1. 打开文件`.sln`Visual Studio。  例如，打开 [WebView2Samples.sln 的本地副本](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln)。  此存储库的解决方案文件需要Visual Studio，Visual Studio Code。

1. 打开其中一 `.sln` 个文件。  例如，打开主 Win32 解决方案文件 [WebView2Samples/SampleApps/WebView2Samples.sln](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln) (`WebView2Samples-master/SampleApps/WebView2Samples.sln` 下载为 Microsoft Visual Studio 中的路径) 副本。  当您在解决方案资源管理器中打开该解决方案Visual Studio **，解决方案资源管理器**将包含以下项目：

   ![WebView2Samples 存储库的解决方案资源管理器，将 WebView2 示例作为项目显示。](media/machine-setup-solution-file-webview2samples.png)


一般情况下，初始开发人员环境设置，你可以 `.sln` 从存储库打开任何类型的 `WebView2Samples` 文件：

*  目录子 `.sln` 目录中特定于平台 `GettingStartedGuides` 的文件。  这些与入门匹配，并且都是演示几个 API 功能的示例。

*  目录中包含多个平台项目的 `SampleApps` Win32 `.sln` 文件。  这是一个全面的 API 演示。

*  目录子 `.sln` 目录中特定于平台 `SampleApps` 的文件。  这些是全面的 API 演示。


<!-- ====================================================================== -->
## <a name="install-visual-studio-workloads"></a>安装Visual Studio工作负载

如果Visual Studio，请安装新工作负载。  在 Microsoft Visual Studio `.sln` `WebView2Samples` 2019 或 2022 中从克隆或下载的存储库打开文件时，可能会看到"无法打开"对话框。

<!-- For example, the Win32 tutorial tells how to install a particular workload if prompted to, upon opening a particular sample.  For example, see [Install the "Desktop development with C++" workload](../get-started/win32.md#install-workloads) in _Get started with WebView2 in Win32 apps_. -->

1. 单击" **确定"** 按钮。  然后，你可能会看到工作负荷安装程序，例如：

   ![Visual Studio .NET 桌面开发工作负载的安装程序。](../media/visual-studio-installer-net-desktop-devmt-workload.png).

1. 选中复选框，然后单击"安装 **"** 按钮。

   适用于Visual Studio工作负载的运行安装程序：

   ![Visual Studio安装程序，安装 .NET 桌面开发工作负载。](../media/visual-studio-installer-for-platform-workload.png).

   迁移报告日志文件可能会打开，例如 ：`file:///C:/Users/username/Documents/WebView2Samples-master/WebView2Samples-master/SampleApps/UpgradeLog.htm`

   ![Visual Studio多平台综合 API 示例的 2022 工作负载安装程序迁移报告。](../media/migration-report-while-installing-workload.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_

   上面， `-master` 存储库的 `.zip` 下载文件存在目录后缀，如果你克隆了存储库，则不存在。

   Visual Studio"解决方案资源管理器"中`.sln`打开所选文件：

   ![Visual Studio多平台综合 API 示例时运行工作负载安装程序后运行 2022 年 2022 年。](../media/vs2022-after-net-workload-installer.png)


<!--
maintenance links; keep:
Main, central copy:
[Install the WebView2 SDK](../how-to/machine-setup.md#install-the-webview2-sdk) in _Set up your Dev environment for WebView2_
Secondary copies:
[Install the WebView2 SDK](../get-started/win32.md#step-6---install-the-webview2-sdk) in _Get started with WebView2 in Win32 apps_
[Install the WebView2 SDK](../get-started/winforms.md#step-3---install-the-webview2-sdk) in _Get started with WebView2 in WinForms apps_
[Install the WebView2 SDK](../get-started/wpf.md#step-3---install-the-webview2-sdk) in _Get started with WebView2 in WPF apps_
[Install the WebView2 SDK](../get-started/winui2.md#step-6---install-the-webview2-sdk) in _Get started with WebView2 in WinUI 2 (UWP) apps (public preview)_
[Install the WebView2 SDK](../get-started/winui.md#step-4---install-the-webview2-sdk) in _Get started with WebView2 in WinUI 3 (Windows App SDK) apps_
-->
<!-- ====================================================================== -->
## <a name="install-the-webview2-sdk"></a>安装 WebView2 SDK

WebView2 SDK 包括 WebView2 控件，该控件由 Microsoft Edge 支持，使你能够将 Web 技术 (HTML、CSS 和 JavaScript) 嵌入本机应用程序中。

每个文件的每个项目节点安装一次 WebView2 SDK `.sln` 。  WebView2 SDK 安装仅适用于安装它的项目。

无需从 NuGet `Microsoft.Web.WebView2` 下载 SDK nuget.org 包，而是通过 Visual Studio 中的 NuGet 面板安装 WebView2 SDK NuGet 程序包管理器 包。****  下载或克隆 WebView2Samples `.sln` 存储库后，在 Visual Studio 中打开该存储库的一个文件，然后右键单击解决方案中的项目节点。  使用 **NuGet 程序包管理器 面板**将 SDK 作为 `Microsoft.Web.WebView2` NuGet 程序包安装。

SDK `Microsoft.Web.WebView2` 在发布版本和预发行版中提供。  若要开始，建议使用发布版本。


安装 WebView2 SDK，如下所示：

1. 打开文件`.sln`Visual Studio。  例如，打开 [WebView2Samples.sln 的本地副本](https://github.com/MicrosoftEdge/WebView2Samples/blob/master/SampleApps/WebView2Samples.sln)。  此存储库的解决方案文件需要Visual Studio，Visual Studio Code。

1. 在****"解决方案资源管理器"中，右键单击解决方案的项目节点，例如"**WebView2GettingStarted**"项目节点 (而不是解决方案节点) 然后选择"管理 NuGet **包"**。

   下图显示了特定的 .sln 文件和项目;使用要安装 SDK 的任何项目：

   ![管理NuGet包。](../media/manage-nuget-packages.png)

   the **NuGet 程序包管理器** tab opens in Visual Studio.

1. 在"**NuGet**窗口中，单击"浏览 **"** 选项卡。

1. 在搜索栏右侧，清除"包含预发行**** (复选框，除非你知道需要 SDK) 。

1. 在左上角的搜索栏中，键入 **Microsoft.Web.WebView2**。

1. 在搜索栏下方，单击 **Microsoft.Web.WebView2** 卡。

1. 在右侧窗格中，单击"安装 ("**** 或 **"** 更新) 按钮。  NuGet WebView2 SDK 下载到计算机，供此项目使用。

   ![选择 microsoft.Web.WebView2 中的 NuGet 程序包管理器 包Visual Studio。](../media/nuget.png)

   _若要缩放，请右键> **新选项卡中的"打开图像"**。_

1. 关闭"**NuGet 程序包管理器**"选项卡。

WebView2 SDK 现已安装，因此开发环境现已设置为将 WebView2 功能添加到 WebView2 应用。

另请参阅 [NuGet.org > Microsoft.Web.WebView2 SDK](https://www.nuget.org/packages/Microsoft.Web.WebView2)。
