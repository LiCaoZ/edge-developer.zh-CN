---
title: 管理用户数据文件夹
description: 如何在 WebView2 应用程序中管理用户数据文件夹。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 05/06/2021
ms.openlocfilehash: 4879e5d0595e4e421a789661651d71d940aa45a0
ms.sourcegitcommit: ae41e2c0ca42fb7eac73824c828305c7b13b4203
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2022
ms.locfileid: "12345735"
---
# <a name="manage-the-user-data-folder"></a>管理用户数据文件夹

WebView2 应用程序与用户数据文件夹交互，以存储浏览器数据，如 Cookie、权限和缓存的资源。  WebView2 控件的每个实例都与一个用户数据文件夹关联。  每个用户数据文件夹对于用户都是唯一的。


<!-- ====================================================================== -->
## <a name="best-practices"></a>最佳做法

用户数据文件夹由 WebView2 自动创建。  WebView2 开发人员控制用户数据文件夹的生命周期。  如果应用程序重新使用来自应用程序会话的用户数据，请考虑保存用户数据文件夹，否则可以将其删除。  在决定如何管理用户数据文件夹时，请考虑以下方案：

*  如果同一用户反复使用您的应用程序，并且应用程序的 Web 内容依赖于用户的数据，请保存用户数据文件夹。

*  如果多个用户重复使用您的应用程序，请为每个新用户创建一个新的用户数据文件夹，并保存每个用户的用户数据文件夹。

*  如果应用程序没有重复用户，请为每个用户创建一个新的用户数据文件夹，并删除以前的用户数据文件夹。


<!-- ====================================================================== -->
## <a name="create-user-data-folders"></a>创建用户数据文件夹

`userDataFolder`若要指定用户数据文件夹的位置，在调用 [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment) (Win32) 或 [CoreWebView2Environment](/dotnet/api/microsoft.web.webview2.core.corewebview2environment) (.NET) 时包括 参数。  创建后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。

未指定 `userDataFolder` 时，WebView2 在默认位置创建用户数据文件夹，如下所示：

*  对于Windows应用商店应用，默认用户`ApplicationData\LocalFolder`文件夹是程序包文件夹中的子文件夹。

*  对于现有桌面应用，默认用户数据文件夹是应用程序 + (`exe`) 可执行文件 `.WebView2`。  我们建议你显式指定用户数据文件夹，并在同一文件夹中创建它，该文件夹中存储所有其他应用数据，而不是使用默认值。


<!-- ====================================================================== -->
## <a name="delete-user-data-folders"></a>删除用户数据文件夹

由于以下任一原因，您的应用程序可能需要删除用户数据文件夹：

*  卸载应用时。  如果要卸载已打包Windows应用商店应用，Windows自动删除用户数据文件夹。

*  清除所有浏览数据历史记录。

*  从数据损坏中恢复。

*  删除以前的会话数据。

关闭 WebView2 应用程序后，用户数据文件夹中的文件可能仍在使用中。  在这种情况下，请等待浏览器进程及所有子进程退出，然后再删除该文件夹。  可以使用 WebView2 的 属性检索浏览器进程 `BrowserProcessId` 的进程 ID。


<!-- ====================================================================== -->
## <a name="share-user-data-folders"></a>共享用户数据文件夹

WebView2 控件可以共享相同的用户数据文件夹，以执行以下操作：

*  通过运行在一个浏览器进程中优化系统资源。  请参阅 [WebView2 进程模型](../concepts/process-model.md)。

*  共享浏览器历史记录和缓存的资源。


共享用户数据文件夹时，请考虑以下事项：

*  当使用 [add_NewBrowserVersionAvailable](/microsoft-edge/webview2/reference/win32/icorewebview2environment#add_newbrowserversionavailable) (Win32) 或 [NewBrowserVersionAvailable](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.newbrowserversionavailable) (.NET) 事件重新创建 WebView2 控件以更新浏览器版本时，请确保浏览器进程退出并关闭共享相同用户数据文件夹的 WebView2 控件。  若要检索浏览器进程的进程 ID，请使用 `BrowserProcessId` WebView2 控件的 属性。

*  共享相同用户数据文件夹的 WebView2 控件必须对 [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment) (Win32) 或 [CoreWebView2Environment](/dotnet/api/microsoft.web.webview2.core.corewebview2environment) (.NET) 使用相同的选项。  如果没有，WebView2 的创建将失败 `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`。


### <a name="avoid-running-too-many-folders-at-once"></a>避免同时运行过多文件夹

若要隔离应用程序的不同部分，或者不需要在 WebView2 控件之间共享数据，可以使用不同的用户数据文件夹。  例如，应用程序可以包含两个 WebView2 控件，一个控件用于显示广告，另一个控件用于显示应用程序内容。  可以针对每个 WebView2 控件使用不同的用户数据文件夹。

每个 WebView2 浏览器进程会占用额外的内存和磁盘空间。  因此，请避免同时运行具有过多不同用户数据文件夹的 WebView2 控件。
