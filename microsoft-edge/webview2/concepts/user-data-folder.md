---
title: 管理用户数据文件夹
description: 如何在 WebView2 主机应用中管理用户数据文件夹。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 03/17/2022
ms.openlocfilehash: 5a30793f921abb785e39e4487b52b6cde4a4d7a7
ms.sourcegitcommit: fad2471fb5d304c36ad4b52c57c9fb791356d097
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2022
ms.locfileid: "12459642"
---
# <a name="manage-user-data-folders"></a>管理用户数据文件夹
<!-- # old title: Manage the user data folder -->

UDF (用户) 文件夹存储在用户计算机上，其中包含与主机应用和 WebView2 相关的数据。


**术语：**

| 术语 | 定义 |
|---|---|
| _用户数据文件夹_ | WebView2 创建用于存储浏览器数据（如 Cookie、权限和缓存资源）的文件夹。 |
| _UDF_ | 用户数据文件夹。 |
| _UDF 位置_ | 用户数据文件夹的目录路径。 |
| _默认 UDF 位置_ | 用户数据文件夹的默认目录路径。  如果不指定自定义 UDF 位置，WebView2 将创建 UDF 的目录路径。 |
| _自定义 UDF 位置_ | 用户数据文件夹的自定义位置。  WebView2 主机应用指定的 WebView2 将在何处创建用户数据文件夹的目录路径。 |

WebView2 在平台的默认位置或主机应用显式指定的自定义 UDF 位置创建 UDF。

默认情况下，WebView2 在特定平台的默认位置创建 UDF。  这适用于某些平台，但其他平台则不能。  如果你的应用有特定需求，你可以指定自定义 UDF 位置。  确保指定的自定义 UDF 位置对 WebView2 应用运行时具有相应的读/写权限。


<!-- ====================================================================== -->
## <a name="what-kind-of-data-is-stored-in-the-udf"></a>UDF 中存储的数据类型

WebView2 应用使用 UDF (用户数据) 存储浏览器数据，如 Cookie、权限和缓存的资源。

| 数据类型 | 说明 |
|---|---|
| `AllDomStorage` | DOM 存储数据，现在和未来。 此浏览数据类型包括 、`FileSystems``IndexedDb``WebSql`、 。 `CacheStorage` |
| `AllProfile` | 应擦除的配置文件数据，使其看起来像新配置文件。 这不会删除帐户范围内的数据，如密码，但会通过让用户退出来删除对帐户范围内数据的访问权限。 现在和未来的所有配置文件数据。 将来可能会向此数据类型中添加新的配置文件数据类型。 此浏览数据类型包括数据类型 `AllSite``GeneralAutofill``DownloadHistory``PasswordAutosave``DiskCache``BrowsingHistory`、 和 。`Settings` |
| `AllSite` | 现在和未来的所有网站数据。 此浏览数据类型包括数据类型 和 `AllDomStorage` `Cookies`。 将来可能会向此数据类型中添加新的网站数据类型。 |
| `BrowsingHistory` | 浏览历史记录数据。 |
| `CacheStorage` | CacheStorage DOM API 存储的数据。 |
| `Cookies` | HTTP Cookie 数据。 |
| `DiskCache` | 磁盘缓存。 |
| `DownloadHistory` | 下载历史记录数据。 |
| `FileSystems` | 文件系统数据。 |
| `GeneralAutofill` | 常规自动填充表单数据。 这将排除密码信息，并包括姓名、街道和电子邮件地址、电话号码和任意输入等信息。 包括付款数据。 |
| `IndexedDb` | IndexedDB DOM 功能存储的数据。 |
| `LocalStorage` | 由 localStorage DOM API 存储的数据。 |
| `PasswordAutosave` | 密码自动保存数据。 |
| `Settings` | 设置数据。 |
| `WebSql` | Web 数据库 DOM API SQL存储的数据。 |

上述数据类型在 [CoreWebView2BrowsingDataKinds 枚举中列为枚举成员](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds#fields)。


<!-- ====================================================================== -->
## <a name="how-and-when-the-udf-is-created"></a>UDF 的创建方式和时间

UDF (文件夹) WebView2 控件为 WebView2 主机应用创建。

UDF 是在平台的默认 UDF 位置创建的，或者如果你的主机应用指定了自定义 UDF 位置，则 UDF 是在自定义 UDF 位置中创建的。

如果 UDF 不存在，UDF 在启动 WebView2 主机应用时创建。


<!-- ====================================================================== -->
## <a name="how-many-udfs-are-created"></a>创建多少个 UDF？

WebView2 控件的每个实例都与 UDF (用户数据) 。

每个 WebView2 会话必须具有 UDF。  每个 WebView2 会话只有 1 个活动的 UDF。

每个应用 WebView2 会话至少存在一个 UDF。  通过指定自定义 UDF 位置，主机应用可以重叠它们。
或者，每台计算机可以有一个 UDF。  这取决于主机应用配置 UDF 的方式。

如果应用是按用户安装的，则 UDF 可以是每个用户。
如果按用户安装主机应用，则每个 UDF 对于用户是唯一的（如果未指定）。


<!-- ====================================================================== -->
## <a name="how-to-move-the-udf"></a>如何移动 UDF

若要将用户数据文件夹 (UDF) ：

1. 关闭所有 WebView2 会话。

1. 启动新的 WebView2 主机应用会话，指定新的自定义 UDF 位置。


<!-- ====================================================================== -->
## <a name="the-default-udf-location"></a>默认 UDF 位置

默认用户数据文件夹 (UDF) 因平台而异。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF `.exe` 位置是应用可执行文件 () 运行的目录。  默认 UDF 是可执行 () `exe` 应用 + `.WebView2`的路径。  UDF 的文件名是应用的可执行 (`exe`) + 的路径 `.WebView2`。

例如，如果运行 ， `D:\WebView2App\WebView2.exe`将创建 UDF 文件夹： `D:\WebView2App\WebView2.exe.WebView2\`。  另一个示例： `WebView2APISample.exe.WebView2\`。


**你应该使用默认或自定义 UDF 位置吗？**

在大多数情况下，你应该指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这将确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入它。  请参阅下面的"指定自定义 UDF 位置"部分。


**打包：**

Win32 MSIX 打包是一个独立的 `.exe`。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF `.exe` 位置是应用可执行文件 () 运行的目录。  默认 UDF 是可执行 () `exe` 应用 + `.WebView2`的路径。  UDF 的文件名是应用的可执行 (`exe`) + 的路径 `.WebView2`。

例如，如果运行 ， `D:\WebView2App\WebView2.exe`将创建 UDF 文件夹： `D:\WebView2App\WebView2.exe.WebView2\`。  另一个示例： `WebView2APISample.exe.WebView2\`。


**你应该使用默认或自定义 UDF 位置吗？**

在大多数情况下，你应该指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这将确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入它。  请参阅下面的"指定自定义 UDF 位置"部分。



<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF `.exe` 位置是应用程序可执行 () 在 (中运行的目录或它的子) 。


**你应该使用默认或自定义 UDF 位置吗？**

在大多数情况下，你应该使用默认 UDF 位置。  创建 UDF 的默认位置在运行时将具有相应的权限;默认 UDF 位置是可写位置。


**默认位置为什么可写：**

运行时，ClickOnce WebView2 具有写入权限的位置自动安装主机应用。  ClickOnce UDF 默认位置，并保证 WebView2 具有写入权限，可以在该位置创建 UDF。

但是，主机应用可能无法使用该位置将数据写入。  如果你的主机应用无法写入默认 UDF 位置，请参阅下面的"指定自定义 UDF 位置"部分。


**清理：**

在会话结束时，ClickOnce自动清理。  


**打包：**

ClickOnce是轻型瞬态应用的部署方法;它是混合模型。  可以保留一个ClickOnce应用，但这不是标准的典型做法。  


**应用包装的平台应用ClickOnce类型：**

一ClickOnce应用通常包含 .NET 应用。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="winui-2-uwp"></a>WinUI 2 (UWP) ](#tab/uwp)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置 `ApplicationData\LocalFolder` 是包文件夹中的子文件夹。


**你应该使用默认或自定义 UDF 位置吗？**

在此平台上，使用默认 UDF 位置。


**默认位置为什么可写：**

WinUI 2 (UWP) 打包平台;它在沙盒中运行，并打包为在沙盒中运行，通常不作为单独的文件，而是作为应用程序包运行。

WinUI 2 (UWP) 应用是每个用户的，并且具有安装位置下的写入访问权限。

对于 UWP， `.exe` 位于安装程序可写入的受保护位置。

运行时，仅在会话期间，会向 WebView2 主机应用提供对本地文件夹的访问权限，因此 WebView2 控件可以在该位置创建 UDF 并写入它。

WebView2 检查该运行时，并创建该可写位置的 UDF。


**打包：**

WinUI 2 (UWP) 应用是自包含的依赖项和部署 (DLL) ，尽管它未打包到单个文件中。

WinUI 2 (UWP) 应用是每个用户的，并且具有安装位置下的写入访问权限。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="winui-3"></a>WinUI 3](#tab/winui3)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置 `ApplicationData\LocalFolder` 是包文件夹中的子文件夹。


**你应该使用默认或自定义 UDF 位置吗？**

在此平台上，使用默认 UDF 位置。


**打包：**

WinUI 3 是一个"打包"平台;它在沙盒中运行，并打包为在沙盒中运行，通常不作为单独的文件，而是作为应用程序包运行。

---

<!-- end of "default location" tab-set -->


<!-- ====================================================================== -->
## <a name="specifying-a-custom-udf-location"></a>指定自定义 UDF 位置

如何在 UDF 中指定自定义用户数据 (位置) 因平台而异。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，你应该指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这将确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入它。

你应该指定存储所有其他应用数据的同一文件夹。


**如何指定自定义 UDF 位置：**

使用 [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment) 和 `userDataFolder` 参数。  但请使用下面的代码，该代码来自 `WebView2Samples` 存储库。<!-- this api ref contains incorrect content but use the code listing below -->


**示例代码：**

```cpp
std::wstring m_userDataFolder;
m_userDataFolder = L"C:\MyAppUserDataFolder"
auto options = Microsoft::WRL::Make<CoreWebView2ExperimentalEnvironmentOptions>();

HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
    NULL, m_userDataFolder.c_str(), options.Get(),
    Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
        this, &AppWindow::OnCreateEnvironmentCompleted)
        .Get());
```

有关示例代码，请参阅 WebView2Samples 存储库附近的适用于 Win32 `.cpp` `.cs` 的或文件> [WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample)。


<!-- neither specific to custom nor default -->
**浏览器数据存储在 UDF 中的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。


**为什么应该在此平台上使用自定义 UDF 位置：**

如果不指定自定义 UDF 位置，则默认位置可能会产生运行时故障（如果使用安装程序技术，因为安装程序技术将应用和 UDF 放在文件系统的受保护区域中，其中 WebView2 无法创建 UDF，因此 UDF 创建通常失败。  WebView2 将引发错误，让你的主机应用知道 UDF 无法创建于该位置。

如果主机应用从用户没有写入权限的位置运行，WebView2 将无法创建 UDF，并且你将在 WebView2 启动期间收到运行时错误。



<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，你应该指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这将确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入它。


**如何指定自定义 UDF 位置：**

你应该指定存储所有其他应用数据的同一文件夹。

使用 [CoreWebView2Environment.CreateAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createasync)传递参数 `userDataFolder` 。


**示例代码：**

```csharp
string UserDataFolder;
UserDataFolder = "C:\MyAppUserDataFolder";
_task = CoreWebView2Environment.CreateAsync(BrowserExecutableFolder, 
                                            UserDataFolder, 
                                            new CoreWebView2EnvironmentOptions(null, Language, null));
```

有关示例代码，请参阅 WebView2Samples 存储库附近的 .NET (WPF & WinForms) 、.cpp 或 .cs 文件，> [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser)。


**为什么需要在此平台上指定自定义 UDF：**

如果不指定自定义 UDF 位置，则默认位置可能会产生运行时故障（如果使用安装程序技术）。  这是因为安装程序技术将应用和 UDF 放在文件系统的受保护区域中，其中 WebView2 无法创建 UDF，因此 UDF 创建通常会失败。

WebView2 将引发错误，让你的主机应用知道 UDF 无法创建于该位置。


<!-- neither focused on default nor custom -->
**数据在 UDF 中的存储位置：** 创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，你应该使用默认 UDF 位置。

如果指定自定义 UDF 位置，请确保用户数据文件夹位置对 WebView2 应用运行时具有相应的读/写权限。


**如何指定自定义 UDF 位置：**

使用 [CoreWebView2Environment.CreateAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createasync)传递参数 `userDataFolder` 。

你应该指定存储所有其他应用数据的同一文件夹。


**示例代码：**

```csharp
string UserDataFolder;
UserDataFolder = "C:\MyAppUserDataFolder";
_task = CoreWebView2Environment.CreateAsync(BrowserExecutableFolder, 
                                            UserDataFolder, 
                                            new CoreWebView2EnvironmentOptions(null, Language, null));
```

有关示例代码，请参阅 WebView2Samples 存储库附近的 .NET (WPF & WinForms) 、.cpp 或 .cs 文件，> [WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2WpfBrowser)。


<!-- neither specific to custom nor default -->
**浏览器数据存储在 UDF 中的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="winui-2-uwp"></a>WinUI 2 (UWP) ](#tab/uwp)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，使用默认 UDF 位置。


**浏览器数据存储在 UDF 中的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。


**示例代码：**

有关示例代码，请参阅 WinUI 2 (UWP) `.cs` 文件，网址为 [WebView2Samples 存储库> webview2_sample_uwp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/webview2_sample_uwp)。



<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="winui-3"></a>WinUI 3](#tab/winui3)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，使用默认 UDF 位置。


**示例代码：**

有关示例代码，请参阅 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2_WinUI3_Sample) 存储库上的 WinUI 3 `.cs` > WebView2_WinUI3_Sample。


**浏览器数据存储在 UDF 中的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在 的子文件夹内 `userDataFolder`。


---

<!-- end of "custom UDF location" tab-set -->


<!-- ====================================================================== -->
## <a name="retrieving-the-udf-location"></a>检索 UDF 位置

若要了解 UDF 用户数据 (设置为) ，请使用 `UserDataFolder` 属性。  此只读属性返回 WebView2 应用的 UDF 位置。

你可能想要读取 UDF 位置的原因：

*  如果你想要清除 UDF 文件夹中的浏览数据，例如会话结束时。

*  如果要删除 UDF。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

使用 Win32 [ICoreWebView2Environment7.get_UserDataFolder getter](/microsoft-edge/webview2/reference/win32/icorewebview2environment7#get_userdatafolder)。  该 API 参考页包含显示如何读取属性的示例 `UserDataFolder` 代码。


**示例代码：**

```cpp
auto environment7 = m_webViewEnvironment.try_query<ICoreWebView2Environment7>();
CHECK_FEATURE_RETURN(environment7);
wil::unique_cotaskmem_string userDataFolder;
environment7->get_UserDataFolder(&userDataFolder);
```

有关读取属性的示例 `UserDataFolder` ，请参阅 [WebView2Samples 存储库的 Win32 示例](https://github.com/MicrosoftEdge/WebView2Samples)。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

使用 .NET [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)。

<!-- dev: add example code to https://docs.microsoft.com/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder showing how to read the `UserDataFolder` property, copy that from the below code block: -->


**示例代码：**

<!-- ```csharp -->
<!-- // ADO work item "[wv2] Update .NET (WPF/WinForms) sample to add code to retrieve UDF location" - then copy lines to here
<!-- ``` -->

有关读取属性的示例 `UserDataFolder` ，请参阅 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) (中的 .NET) WPF/WinForms 示例。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

使用 .NET [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)。


**示例代码：**

<!-- ```csharp -->
<!-- // ADO work item "[wv2] Update ClickOnce sample to add code to retrieve UDF location" - then copy lines to here
<!-- ``` -->

有关读取属性的示例 `UserDataFolder` ，请参阅 [WebView2Samples 存储库> webview2_sample_uwp](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/webview2_sample_uwp)。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="winui-2-uwp"></a>WinUI 2 (UWP) ](#tab/uwp)

使用 WinRT [CoreWebView2Environment.UserDataFolder 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2environment#userdatafolder)。


**示例代码：**

```csharp
private void OnGetUDFClick(object sender, RoutedEventArgs e)
{
    // This property can be used after WebView2 creation to find the actual location of the User Data Folder
    UserDataFolder.Text = WebView2.CoreWebView2.Environment.UserDataFolder;
}
```

有关读取属性 `UserDataFolder` 的示例，请参阅 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/webview2_sample_uwp) (中的 WinUI 2) UWP > webview2_sample_uwp。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="winui-3"></a>WinUI 3](#tab/winui3)

使用 .NET [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)。


**示例代码：**

```csharp
private void OnGetUDFClick(object sender, RoutedEventArgs e)
{
    // This property can be used after WebView2 creation to find the actual location of the User Data Folder
    UserDataFolder.Text = WebView2.CoreWebView2.Environment.UserDataFolder;
}
```

有关示例代码，请参阅 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2_WinUI3_Sample) 存储库上的 WinUI 3 `.cs` > WebView2_WinUI3_Sample。


---

<!-- end of "retrieving location" tab-set -->


<!-- ====================================================================== -->
## <a name="clearing-space-in-the-udf"></a>清除 UDF 中的空间

请清除 UDF 中的浏览 (，) UDF 中的浏览数据，而不是删除 UDF 中的用户数据文件夹。  例如，当用户退出时清除用户数据和历史记录。

请参阅 [清除用户数据文件夹中的浏览数据](clear-browsing-data.md)。


<!-- ====================================================================== -->
## <a name="handling-error-messages"></a>处理错误消息

如果用户数据文件夹 (UDF) 没有"写入"权限，可能会返回以下错误消息字符串：
* `User data folder cannot be created because a file with the same name already exists.`
* `Unable to create user data folder, Access Denied.`

无论用户数据文件夹的位置是默认的 UDF 位置还是自定义 UDF 位置，上述内容都是如此。

如果内存不足，或者 Microsoft Edge运行时无法启动，或找不到 WebView2 运行时，可能会返回与以下内容类似的错误消息字符串：
*  `Microsoft Edge runtime unable to start`
*  `Failed to create WebView2 environment`

添加代码（如 `try/catch` 代码）以处理这些错误。  这些错误可能是无法恢复的致命错误，因此 `try/catch` 将阻止应用崩溃。  然后，你将能够检测故障并正常关闭应用。  某些错误无法恢复 `Access Denied` ，例如尝试使用没有写入权限的用户数据文件夹时。

错误消息字符串显示在对话框中。


<!-- ====================================================================== -->
## <a name="whether-to-persist-user-data-folders-in-various-scenarios"></a>是否在各种方案中保留用户数据文件夹

主机应用控制 UDF 应用中用户数据文件夹 (生命周期) 。  如果你的应用从应用会话中重新使用用户数据，请考虑 (，即，) UDF。

如果你的应用不重用应用会话中的用户数据，你可以删除 UDF。  但是，在会话运行时，最好调用清晰的浏览数据方法，而不是删除 __ UDF。


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-same-user-uses-your-app-repeatedly-and-the-web-content-of-the-app-relies-on-the-users-data"></a>如果同一用户重复使用你的应用，并且应用的 Web 内容依赖于用户数据，则保留用户数据文件夹

在此方案中，不要显式删除 UDF (用户) ;保留数据。


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-multiple-users-use-your-app-repeatedly"></a>如果多个用户重复使用你的应用，则保留用户数据文件夹

如果多个用户重复使用你的应用，你应该为每个新 (UDF) 一个新的用户数据文件夹，并保存每个用户的 UDF。

WebView2 控件为每个新用户创建一个新的 UDF。  WebView2 控件为每个会话创建一个 UDF。  如果有多个 WebView2 会话，WebView2 控件将创建多个 UDF。  通常，如果主机应用具有多个 WebView2 控件实例，则主机应用应该将 WebView2 的所有实例指向同一 UDF。

每个具有 WebView2 控件实例的主机应用都将有自己的 UDF。  主机应用可以将每个 UDF 指向同一位置。  

如果你的主机应用适用于多个用户，你可能需要为每个用户创建一个 UDF。  如果你的应用是按用户安装的，这就是它的工作原理。
<!-- in a more detailed article, cover this: how does your host app cause WebView2 to create one UDF per user vs. causing WebView2 to create one UDF per X or Y or Z instead? -->

如果你启动主机应用的两个副本，他们将使用相同的 UDF。  
<!-- cover this in advanced whitepaper article -->

*  对于 Win32 主机应用，UDF 不会自动删除。
*  对于 .NET (WPF & WinForms) 主机应用，UDF 不会自动删除。
*  对于ClickOnce应用，将自动删除 UDF。
*  对于 WinUI 2 (UWP) 应用，UDF 不会自动删除。
*  对于 WinUI 3 主机应用，UDF 不会自动删除。


<!-- ====================================================================== -->
## <a name="uninstalling-a-host-app"></a>卸载主机应用

卸载 WebView2 主机应用使用标准卸载过程;此过程并非 WebView2 所特有的。

在卸载期间，安装程序可能需要清理任何创建的 UDF。  在某些情况下，你可能想要保留 UDF。

如果创建主机应用，创建 MSIX 安装程序，安装主机应用，然后运行主机应用，它将创建 UDF。  但是，如果你卸载主机应用，将不会自动清理 UDF (因为卸载程序会保护和保留用户数据) ，因此卸载过程需要注意这一注意事项。

在ClickOnce中，它安装在单个位置，会话结束时，它会删除整个树，因此会自动删除 UDF。  这是因为 WebView2 的工作原理ClickOnce，而不是 WebView2 的工作原理。

<!-- details about these Windows considerations belong in a whitepaper article -->


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-your-app-doesnt-have-repeat-users"></a>如果应用没有重复用户，则保留用户数据文件夹

在此方案中，使用 UDF (一) 用户数据文件夹，并删除以前的 UDF。


<!-- ====================================================================== -->
## <a name="deleting-user-data-folders"></a>删除用户数据文件夹

主机应用或卸载程序可以删除 UDF (用户) 。  出于以下任一原因，您可能需要删除 UDF：

*  如果你想要卸载打包的应用商店Windows应用。  在这种情况下，Windows自动删除 UDF。

*  如果要清除所有浏览数据历史记录。  但是，首先 _查看清晰的浏览数据_ 方法，这是一种更简单、更灵活的方法。

*  如果要从数据损坏中恢复。

*  如果要删除以前的会话数据。

*  如果要更改 UDF 位置。  如果更改 UDF 位置，则以前的 UDF 不会自动清理。


### <a name="end-the-webview2-session-before-deleting-the-udf"></a>在删除 UDF 之前结束 WebView2 会话

若要在 UDF (用户数据) ，必须先结束 WebView2 会话。  如果 WebView2 会话当前处于活动状态，则不能删除 UDF。

<!-- write a separate article about writing a WebView2 uninstaller -->


### <a name="wait-for-browser-processes-to-exit-before-deleting-the-udf"></a>等待浏览器进程退出，然后再删除 UDF

如果 WebView2 主机应用关闭后文件仍在使用中，请等待浏览器进程退出，然后再从 UDF (用户) 。

关闭 WebView2 应用后，UDF 中的文件可能仍在使用中。  在这种情况下，请等待浏览器进程及所有子进程退出，然后再删除 UDF。  若要监视进程以等待其退出 `BrowserProcessId` ，请通过使用 WebView2 应用实例的 属性检索浏览器进程的进程 ID。


<!-- ====================================================================== -->
## <a name="sharing-user-data-folders"></a>共享用户数据文件夹

WebView2 控件实例可以在 UDF (共享) 用户数据文件夹，以执行以下操作：

*  通过运行在一个浏览器进程中优化系统资源。  请参阅 [WebView2 应用的进程模型](../concepts/process-model.md)。

*  共享浏览器历史记录和缓存的资源。


共享 UDF 时，请考虑以下事项：

*  当使用 [add_NewBrowserVersionAvailable](/microsoft-edge/webview2/reference/win32/icorewebview2environment#add_newbrowserversionavailable) (Win32) 事件处理程序或 [NewBrowserVersionAvailable](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.newbrowserversionavailable) (.NET) 事件重新创建 WebView2 控件以更新浏览器版本时，主机应用必须确保浏览器进程退出并关闭共享同一 UDF 的任何 WebView2 控件。  若要检索浏览器进程的进程 ID，请使用 `BrowserProcessId` WebView2 控件的 属性。


<!-- ====================================================================== -->
## <a name="avoid-running-too-many-folders-at-once"></a>避免同时运行过多文件夹

若要隔离应用的不同部分，或者不需要在 WebView2 控件之间共享数据，可以使用 UDF 或 UDF (不同的) 。  例如，应用可以包含两个 WebView2 控件，一个控件用于显示广告，另一个用于显示应用内容。  可以针对每个 WebView2 控件使用不同的 UDF。

每个 WebView2 浏览器进程会占用额外的内存和磁盘空间。  因此，请避免同时运行具有过多不同 UDF 的 WebView2 控件。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [从用户数据文件夹中清除浏览数据](clear-browsing-data.md)
* [在应用开发](/windows/apps/package-and-deploy/)Windows_中_打包和 (生成桌面应用Windows) 。
* [ClickOnce安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment) - Visual Studio文档。
* [了解ClickOnce文档中的 Microsoft Edge 和 DirectInvoke](/deployedge/edge-learn-more-co-di) Microsoft Edge Enterprise功能。

<!-- clickable: https://docs.microsoft.com/windows/apps/package-and-deploy/ -->
