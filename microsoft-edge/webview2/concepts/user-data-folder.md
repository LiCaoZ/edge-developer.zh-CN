---
title: 管理用户数据文件夹
description: 如何管理 WebView2 主机应用中的用户数据文件夹。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 061fe65b9c133c36639cb03fc1fdf4f552d42b43
ms.sourcegitcommit: dc0001e208a1511cbeca620a5790aad54b3bfbb3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2022
ms.locfileid: "12522453"
---
# <a name="manage-user-data-folders"></a>管理用户数据文件夹
<!-- # old title: Manage the user data folder -->

UDF)  (用户数据文件夹是存储在用户计算机上的文件夹，其中包含与主机应用和 WebView2 相关的数据。


**术语：**

| 术语 | 定义 |
|---|---|
| _用户数据文件夹_ | WebView2 创建的用于存储浏览器数据的文件夹，例如 Cookie、权限和缓存资源。 |
| _UDF_ | 用户数据文件夹。 |
| _UDF 位置_ | 用户数据文件夹的目录路径。 |
| _默认 UDF 位置_ | 用户数据文件夹的默认目录路径。  如果未指定自定义 UDF 位置，则 WebView2 将在其中创建 UDF 的目录路径。 |
| _自定义 UDF 位置_ | 用户数据文件夹的自定义位置。  WebView2 主机应用指定 WebView2 将创建用户数据文件夹的位置的目录路径。 |

WebView2 在平台的默认位置或主机应用显式指定的自定义 UDF 位置中创建 UDF。

默认情况下，WebView2 在特定平台的默认位置创建 UDF。  这适用于某些平台，但不适用于其他平台。  如果应用有特定需求，可以指定自定义 UDF 位置。  确保指定的自定义 UDF 位置对 WebView2 应用运行时具有适当的读/写权限。


<!-- ====================================================================== -->
## <a name="what-kind-of-data-is-stored-in-the-udf"></a>UDF 中存储的数据类型

WebView2 应用使用用户数据文件夹 (UDF) 来存储浏览器数据，例如 Cookie、权限和缓存的资源。

| 数据类型 | 描述 |
|---|---|
| `AllDomStorage` | DOM 存储数据，现在和将来。 这种浏览数据类型包括`FileSystems`， ， `IndexedDb``WebSql`， 。 `CacheStorage` |
| `AllProfile` | 应擦除的配置文件数据，使其看起来像新配置文件。 这不会删除帐户范围的数据（如密码），但会通过注销用户来删除对帐户范围数据的访问权限。 现在和将来的所有配置文件数据。 将来可能会将新的配置文件数据类型添加到此数据类型。 这种浏览数据类型包括数据类型`AllSite`、`DiskCache`、`DownloadHistory`、`GeneralAutofill`、`PasswordAutosave``BrowsingHistory`和 `Settings`。 |
| `AllSite` | 现在和将来的所有站点数据。 这种浏览数据类型包括数据类型 `AllDomStorage` 和 `Cookies`。 将来可能会将新的站点数据类型添加到此数据类型中。 |
| `BrowsingHistory` | 浏览历史记录数据。 |
| `CacheStorage` | CacheStorage DOM API 存储的数据。 |
| `Cookies` | HTTP Cookie 数据。 |
| `DiskCache` | 磁盘缓存。 |
| `DownloadHistory` | 下载历史记录数据。 |
| `FileSystems` | 文件系统数据。 |
| `GeneralAutofill` | 常规自动填充表单数据。 这不包括密码信息，包括姓名、街道和电子邮件地址、电话号码和任意输入等信息。 包括付款数据。 |
| `IndexedDb` | IndexedDB DOM 功能存储的数据。 |
| `LocalStorage` | localStorage DOM API 存储的数据。 |
| `PasswordAutosave` | 密码自动保存数据。 |
| `Settings` | 设置数据。 |
| `WebSql` | Web SQL数据库 DOM API 存储的数据。 |

上述类型的数据在 [CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds#fields)中列为枚举成员。


<!-- ====================================================================== -->
## <a name="how-and-when-the-udf-is-created"></a>如何以及何时创建 UDF

WebView2 控件为 WebView2 主机应用创建用户数据文件夹 (UDF) 。

UDF 是在平台的默认 UDF 位置中创建的，或者如果主机应用指定了自定义 UDF 位置，则会在自定义 UDF 位置中创建 UDF。

如果 UDF 不存在，则会在启动 WebView2 主机应用时创建 UDF。


<!-- ====================================================================== -->
## <a name="how-many-udfs-are-created"></a>创建了多少 UDF？

WebView2 控件的每个实例都与用户数据文件夹 (UDF) 相关联。

每个 WebView2 会话必须具有 UDF。  每个 WebView2 会话只有 1 个活动 UDF。

每个应用 WebView2 会话至少有一个 UDF。  主机应用可以通过指定自定义 UDF 位置来重叠它们。
或者，每台计算机可以有一个 UDF。  这取决于主机应用如何配置 UDF。

如果每个用户安装了应用，则 UDF 可以是每个用户。
如果主机应用是按用户安装的，则每个 UDF 对于用户是唯一的（如果未指定）。


<!-- ====================================================================== -->
## <a name="how-to-move-the-udf"></a>如何移动 UDF

若要将用户数据文件夹移 (UDF) ：

1. 关闭所有 WebView2 会话。

1. "开始"菜单新的 WebView2 主机应用会话，指定新的自定义 UDF 位置。


<!-- ====================================================================== -->
## <a name="the-default-udf-location"></a>默认 UDF 位置

默认用户数据文件夹 (UDF) 位置因平台而异。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置是应用可执行文件 () `.exe` 正在运行的目录。  默认 UDF 是应用 + `.WebView2`的可执行 (`exe`) 路径。  UDF 的文件名是应用 + `.WebView2`的可执行 (`exe`) 路径。

例如，如果运行`D:\WebView2App\WebView2.exe`，将创建一个 UDF 文件夹： `D:\WebView2App\WebView2.exe.WebView2\`  另一个示例是： `WebView2APISample.exe.WebView2\`.


**应使用默认或自定义 UDF 位置？**

在大多数情况下，应指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这可确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入该控件。  请参阅下面的“指定自定义 UDF 位置”部分。


**包装：**

Win32 MSIX 打包是独立的 `.exe`。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置是应用可执行文件 () `.exe` 正在运行的目录。  默认 UDF 是应用 + `.WebView2`的可执行 (`exe`) 路径。  UDF 的文件名是应用 + `.WebView2`的可执行 (`exe`) 路径。

例如，如果运行`D:\WebView2App\WebView2.exe`，将创建一个 UDF 文件夹： `D:\WebView2App\WebView2.exe.WebView2\`  另一个示例是： `WebView2APISample.exe.WebView2\`.


**应使用默认或自定义 UDF 位置？**

在大多数情况下，应指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这可确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入该控件。  请参阅下面的“指定自定义 UDF 位置”部分。



<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置是应用可执行文件 () `.exe` 在 (中运行的目录或) 的子目录。


**应使用默认或自定义 UDF 位置？**

在大多数情况下，应使用默认的 UDF 位置。  将创建 UDF 的默认位置将在运行时具有适当的权限;默认 UDF 位置是可写的位置。


**默认位置为何可写入：**

在运行时，ClickOnce会自动在 WebView2 具有写入权限的位置安装主机应用。  ClickOnce可以使用默认的 UDF 位置，并保证 WebView2 具有写入权限，以便能够在此处创建 UDF。

但是，主机应用可能无法使用该位置将数据写入其中。  如果主机应用无法写入默认 UDF 位置，请参阅下面的“指定自定义 UDF 位置”部分。


**清理：**

会话结束时，ClickOnce自动清理。  


**包装：**

ClickOnce是轻型暂时性应用的部署方法;它是混合模型。  可以保留ClickOnce应用，但这不是标准的典型做法。  


**ClickOnce应用包装的平台应用类型：**

ClickOnce应用通常包含 .NET 应用。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="winui-2-uwp"></a>WinUI 2 (UWP) ](#tab/uwp)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置是 `ApplicationData\LocalFolder` 包文件夹中的子文件夹。


**应使用默认或自定义 UDF 位置？**

在此平台上，使用默认 UDF 位置。


**默认位置为何可写入：**

WinUI 2 (UWP) 是打包平台;它在沙盒中运行，并打包在沙盒中运行，通常不是作为单独的文件，而是作为应用捆绑包运行。

WinUI 2 (UWP) 应用是每个用户的，并且在安装的位置下具有写入访问权限。

对于 UWP， `.exe` 该位置位于安装程序可以写入的受保护位置。

在运行时，仅在会话期间，WebView2 主机应用将有权访问本地文件夹，因此 WebView2 控件能够在此处创建 UDF 并写入到该文件夹。

WebView2 检查该运行时，并在该可写位置创建 UDF。


**包装：**

WinUI 2 (UWP) 应用在依赖项和部署 (DLL) 方面是自包含的，尽管它未打包到单个文件中。

WinUI 2 (UWP) 应用是每个用户的，并且在安装的位置下具有写入访问权限。


<!-- ====================================================================== -->
<!-- default UDF location -->

# [<a name="winui-3"></a>WinUI 3](#tab/winui3)

<!--
**What is the default UDF location?**
-->
在此平台上，默认 UDF 位置是 `ApplicationData\LocalFolder` 包文件夹中的子文件夹。


**应使用默认或自定义 UDF 位置？**

在此平台上，使用默认 UDF 位置。


**包装：**

WinUI 3 是一个“打包”平台;它在沙盒中运行，并打包在沙盒中运行，通常不是作为单独的文件，而是作为应用捆绑包运行。

---

<!-- end of "default location" tab-set -->


<!-- ====================================================================== -->
## <a name="specifying-a-custom-udf-location"></a>指定自定义 UDF 位置

如何指定自定义用户数据文件夹 (UDF) 位置因平台而异。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，应指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这可确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入该控件。

应指定存储所有其他应用数据的同一文件夹。


**如何指定自定义 UDF 位置：**

使用 [ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment) 和 `userDataFolder` 参数。  但请使用下面的代码，该代码来自 `WebView2Samples` 存储库。<!-- this api ref contains incorrect content but use the code listing below -->


**示例代码：**

```cpp
std::wstring m_userDataFolder;
m_userDataFolder = L"C:\\MyAppUserDataFolder"
auto options = Microsoft::WRL::Make<CoreWebView2ExperimentalEnvironmentOptions>();

HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
    NULL, m_userDataFolder.c_str(), options.Get(),
    Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
        this, &AppWindow::OnCreateEnvironmentCompleted)
        .Get());
```

例如代码，请参阅 [WebView2Samples 存储库> WebView2APISample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample) 附近适合 `.cpp` Win32 或`.cs`文件。


<!-- neither specific to custom nor default -->
**在 UDF 中存储浏览器数据的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在子文件夹中 `userDataFolder`。


**为何应在此平台上使用自定义 UDF 位置：**

如果未指定自定义 UDF 位置，默认位置可能会导致运行时失败（如果使用安装程序技术），因为安装程序技术将应用和 UDF 置于文件系统的受保护区域，其中 WebView2 无法创建 UDF，因此 UDF 创建通常会失败。  WebView2 将引发错误，让主机应用知道无法在该位置创建 UDF。

如果主机应用从用户没有写入访问权限的位置运行，WebView2 将无法创建 UDF，并且会在 WebView2 启动期间收到运行时错误。



<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，应指定自定义 UDF 位置，而不是使用默认 UDF 位置。  这可确保 WebView2 控件具有写入访问权限，以便 WebView2 控件能够创建 UDF，然后写入该控件。


**如何指定自定义 UDF 位置：**

应指定存储所有其他应用数据的同一文件夹。

使用 [CoreWebView2Environment.CreateAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createasync)，传递 `userDataFolder` 参数。


**示例代码：**

```csharp
string UserDataFolder;
UserDataFolder = "C:\\MyAppUserDataFolder";
_task = CoreWebView2Environment.CreateAsync(BrowserExecutableFolder, 
                                            UserDataFolder, 
                                            new CoreWebView2EnvironmentOptions(null, Language, null));
```

例如代码，请参阅 [WebView2Samples 存储库> WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser) 附近的 .NET (WPF & WinForms) 适当的 .cpp 或 .cs 文件。


**为何需要在此平台上指定自定义 UDF：**

如果未指定自定义 UDF 位置，默认位置可能会导致运行时失败（如果使用安装程序技术）。  这是因为安装程序技术将应用和 UDF 置于文件系统的受保护区域，其中 WebView2 无法创建 UDF，因此 UDF 创建通常会失败。

WebView2 将引发错误，让主机应用知道无法在该位置创建 UDF。


<!-- neither focused on default nor custom -->
**在 UDF 中存储数据的位置：** 创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在子文件夹中 `userDataFolder`。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，在大多数情况下，应使用默认 UDF 位置。

如果指定自定义 UDF 位置，请确保用户数据文件夹位置对 WebView2 应用运行时具有适当的读/写权限。


**如何指定自定义 UDF 位置：**

使用 [CoreWebView2Environment.CreateAsync 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createasync)，传递 `userDataFolder` 参数。

应指定存储所有其他应用数据的同一文件夹。


**示例代码：**

```csharp
string UserDataFolder;
UserDataFolder = "C:\\MyAppUserDataFolder";
_task = CoreWebView2Environment.CreateAsync(BrowserExecutableFolder, 
                                            UserDataFolder, 
                                            new CoreWebView2EnvironmentOptions(null, Language, null));
```

例如代码，请参阅 [WebView2Samples 存储库> WebView2WpfBrowser](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2WpfBrowser) 附近的 .NET (WPF & WinForms) 适当的 .cpp 或 .cs 文件。


<!-- neither specific to custom nor default -->
**在 UDF 中存储浏览器数据的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在子文件夹中 `userDataFolder`。


<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="winui-2-uwp"></a>WinUI 2 (UWP) ](#tab/uwp)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，使用默认 UDF 位置。


**在 UDF 中存储浏览器数据的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在子文件夹中 `userDataFolder`。


**示例代码：**

例如代码，请参阅 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/webview2_sample_uwp)> webview2_sample_uwp中的 WinUI 2 (`.cs` UWP) 文件。



<!-- ====================================================================== -->
<!-- custom UDF location -->

# [<a name="winui-3"></a>WinUI 3](#tab/winui3)

<!--
**Should you use default or custom UDF location?**
-->
在此平台上，使用默认 UDF 位置。


**示例代码：**

例如代码，请参阅 [WebView2Samples 存储库> WebView2_WinUI3_Sample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2_WinUI3_Sample)中的 WinUI 3 `.cs` 文件。


**在 UDF 中存储浏览器数据的位置：**

创建会话和 UDF 后，WebView2 控件中的浏览器数据存储在子文件夹中 `userDataFolder`。


---

<!-- end of "custom UDF location" tab-set -->


<!-- ====================================================================== -->
## <a name="retrieving-the-udf-location"></a>检索 UDF 位置

若要了解用户数据文件夹 (UDF) 位置的设置，请使用该 `UserDataFolder` 属性。  此只读属性返回 WebView2 应用的 UDF 位置。

你可能想要读取 UDF 位置的原因：

*  如果要清除 UDF 文件夹中的浏览数据，例如在会话结束时。

*  如果要删除 UDF。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="win32"></a>Win32](#tab/win32)

使用 Win32 [ICoreWebView2Environment7.get_UserDataFolder属性 getter](/microsoft-edge/webview2/reference/win32/icorewebview2environment7#get_userdatafolder)。  该 API 参考页包含演示如何读取属性的 `UserDataFolder` 示例代码。


**示例代码：**

```cpp
auto environment7 = m_webViewEnvironment.try_query<ICoreWebView2Environment7>();
CHECK_FEATURE_RETURN(environment7);
wil::unique_cotaskmem_string userDataFolder;
environment7->get_UserDataFolder(&userDataFolder);
```

有关读取属性的 `UserDataFolder` 示例，请参阅 [WebView2Samples 存储库中的 Win32 示](https://github.com/MicrosoftEdge/WebView2Samples)例。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="net-wpfwinforms"></a>.NET (WPF/WinForms) ](#tab/dotnet)

使用 .NET [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)。

<!-- dev: add example code to https://docs.microsoft.com/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder showing how to read the `UserDataFolder` property, copy that from the below code block: -->


**示例代码：**

<!-- ```csharp -->
<!-- // ADO work item "[wv2] Update .NET (WPF/WinForms) sample to add code to retrieve UDF location" - then copy lines to here
<!-- ``` -->

有关读取属性 `UserDataFolder` 的示例，请参阅 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)中的 .NET (WPF/WinForms) 示例。


<!-- ====================================================================== -->
<!-- retrieving UDF location -->

# [<a name="clickonce"></a>ClickOnce](#tab/clickonce)

使用 .NET [CoreWebView2Environment.UserDataFolder 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.userdatafolder)。


**示例代码：**

<!-- ```csharp -->
<!-- // ADO work item "[wv2] Update ClickOnce sample to add code to retrieve UDF location" - then copy lines to here
<!-- ``` -->

有关读取属性的 `UserDataFolder` 示例，请参阅 [WebView2Samples 存储库> webview2_sample_uwp](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/webview2_sample_uwp)。


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

有关读取属性 `UserDataFolder` 的示例，请参阅 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/webview2_sample_uwp)> webview2_sample_uwp中的 WinUI 2 (UWP) 示例。


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

例如代码，请参阅 [WebView2Samples 存储库> WebView2_WinUI3_Sample](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2_WinUI3_Sample)中的 WinUI 3 `.cs` 文件。


---

<!-- end of "retrieving location" tab-set -->


<!-- ====================================================================== -->
## <a name="clearing-space-in-the-udf"></a>清除 UDF 中的空间

从 UDF 中清除浏览数据，而不是 (UDF) 删除用户数据文件夹。  例如，在用户注销时清除用户数据和历史记录。

请参阅 [“清除浏览用户数据”文件夹中的数据](clear-browsing-data.md)。


<!-- ====================================================================== -->
## <a name="handling-error-messages"></a>处理错误消息

如果用户数据文件夹 (UDF) 没有写入权限，则可能会返回以下错误消息字符串：
* `User data folder cannot be created because a file with the same name already exists.`
* `Unable to create user data folder, Access Denied.`

无论用户数据文件夹的位置是默认 UDF 位置还是自定义 UDF 位置，上述内容均为 true。

如果内存不足，或者Microsoft Edge运行时无法启动，或者找不到 WebView2 运行时，可能会返回类似于以下内容的错误消息字符串：
*  `Microsoft Edge runtime unable to start`
*  `Failed to create WebView2 environment`

添加代码（如代码） `try/catch` 以处理这些错误。  这些错误往往是无法从中恢复的致命错误，因此 `try/catch` 会防止应用崩溃。  然后，你将能够检测到故障并正常关闭应用。  某些错误是无法恢复的，例如 `Access Denied` ，尝试使用没有写入权限的用户数据文件夹时。

错误消息字符串显示在对话框中。


<!-- ====================================================================== -->
## <a name="whether-to-persist-user-data-folders-in-various-scenarios"></a>是否在各种方案中保留用户数据文件夹

主机应用控制用户数据文件夹的生存期 (UDF) 。  如果应用重新使用应用会话中的用户数据，请考虑保存 (，而不是删除 UDF) 。

如果应用不重复使用应用会话中的用户数据，则可以删除 UDF。  但是，当会话正在运行时，最好调用 _清晰的浏览数据_ 方法，而不是删除 UDF。


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-same-user-uses-your-app-repeatedly-and-the-web-content-of-the-app-relies-on-the-users-data"></a>如果同一用户重复使用你的应用，并且应用的 Web 内容依赖于用户的数据，则保留用户数据文件夹

在此方案中，请勿显式删除用户数据文件夹 (UDF) ;保留数据。


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-multiple-users-use-your-app-repeatedly"></a>如果多个用户重复使用你的应用，则保留用户数据文件夹

如果多个用户重复使用应用，则应为每个新用户创建新的用户数据文件夹 (UDF) ，并保存每个用户的 UDF。

WebView2 控件为每个新用户创建一个新的 UDF。  WebView2 控件为每个会话创建一个 UDF。  如果有多个 WebView2 会话，WebView2 控件将创建多个 UDF。  通常，如果主机应用具有多个 WebView2 控件实例，则主机应用应将 WebView2 的所有实例指向同一 UDF。

每个具有 WebView2 控件实例的主机应用都将有自己的 UDF。  主机应用可以将每个 UDF 点指向同一位置。  

如果主机应用适用于多个用户，则可能应为每个用户创建一个 UDF。  如果你的应用是按用户安装的，则这就是它的工作原理。
<!-- in a more detailed article, cover this: how does your host app cause WebView2 to create one UDF per user vs. causing WebView2 to create one UDF per X or Y or Z instead? -->

如果启动两个主机应用副本，它们将使用相同的 UDF。  
<!-- cover this in advanced whitepaper article -->

*  对于 Win32 主机应用，不会自动删除 UDF。
*  对于 .NET (WPF & WinForms) 主机应用，不会自动删除 UDF。
*  对于ClickOnce主机应用，将自动删除 UDF。
*  对于 WinUI 2 (UWP) 主机应用，不会自动删除 UDF。
*  对于 WinUI 3 主机应用，不会自动删除 UDF。


<!-- ====================================================================== -->
## <a name="uninstalling-a-host-app"></a>卸载主机应用

卸载 WebView2 主机应用使用标准卸载过程;此过程对 WebView2 并不唯一。

卸载期间，安装程序可能需要清理任何创建的 UDF。  在某些情况下，你可能想要保留 UDF。

如果创建主机应用、创建 MSIX 安装程序、安装主机应用，然后运行主机应用，则会创建 UDF。  但是，如果卸载主机应用，则不会自动清理 UDF (，因为卸载程序会保护并保留用户数据) ，因此卸载过程需要注意这一注意事项。

在ClickOnce应用中，它将安装在单个位置，会话结束时，它会删除整个树，以便自动删除 UDF。  这是因为ClickOnce的工作原理，而不是因为 WebView2 的工作原理。

<!-- details about these Windows considerations belong in a whitepaper article -->


<!-- ====================================================================== -->
## <a name="persisting-user-data-folders-if-your-app-doesnt-have-repeat-users"></a>如果应用没有重复用户，请保留用户数据文件夹

在此方案中，为每个用户创建新的用户数据文件夹 (UDF) ，并删除以前的 UDF。


<!-- ====================================================================== -->
## <a name="deleting-user-data-folders"></a>删除用户数据文件夹

主机应用或卸载程序可以删除用户数据文件夹 (UDF) 。  出于以下任何原因，可能需要删除 UDF：

*  如果要卸载打包的Windows Microsoft Store应用。  在这种情况下，Windows自动删除 UDF。

*  如果要清理所有浏览数据历史记录。  但是，请首先将 _清晰的浏览数据_ 方法视为更简单、更灵活的方法。

*  如果要从数据损坏中恢复。

*  如果要删除以前的会话数据。

*  如果要更改 UDF 位置。  如果更改 UDF 位置，则不会自动清理以前的 UDF。


### <a name="end-the-webview2-session-before-deleting-the-udf"></a>在删除 UDF 之前结束 WebView2 会话

若要删除 UDF)  (用户数据文件夹，必须先结束 WebView2 会话。  如果 WebView2 会话当前处于活动状态，则无法删除 UDF。

<!-- write a separate article about writing a WebView2 uninstaller -->


### <a name="wait-for-browser-processes-to-exit-before-deleting-the-udf"></a>在删除 UDF 之前等待浏览器进程退出

如果在 WebView2 主机应用关闭后文件仍在使用中，请等待浏览器进程退出，然后再删除用户数据文件夹 (UDF) 。

关闭 WebView2 应用后，UDF 中的文件可能仍在使用中。  在这种情况下，请等待浏览器进程和所有子进程退出，然后再删除 UDF。  若要监视等待其退出的进程，请使用 `BrowserProcessId` WebView2 应用实例的属性检索浏览器进程的进程 ID。


<!-- ====================================================================== -->
## <a name="sharing-user-data-folders"></a>共享用户数据文件夹

WebView2 控件实例可以在 UDF)  (共享相同的用户数据文件夹，以执行以下操作：

*  通过在一个浏览器进程中运行来优化系统资源。  请参阅 [WebView2 应用的进程模型](../concepts/process-model.md)。

*  共享浏览器历史记录和缓存的资源。


共享 UDF 时，请考虑以下事项：

*  重新创建 WebView2 控件以使用 [add_NewBrowserVersionAvailable (](/microsoft-edge/webview2/reference/win32/icorewebview2environment#add_newbrowserversionavailable) Win32) 事件处理程序或 [NewBrowserVersionAvailable](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.newbrowserversionavailable) (.NET) 事件更新浏览器版本时，主机应用必须确保浏览器进程退出并关闭共享同一 UDF 的任何 WebView2 控件。  若要检索浏览器进程的进程 ID，请使用 `BrowserProcessId` WebView2 控件的属性。


<!-- ====================================================================== -->
## <a name="avoid-running-too-many-folders-at-once"></a>避免一次运行过多的文件夹

若要隔离应用的不同部分，或者当不需要在 WebView2 控件之间共享数据时，可以使用不同的用户数据文件夹 (UDF) 。  例如，应用可以包含两个 WebView2 控件，一个用于显示广告，另一个用于显示应用内容。  可以为每个 WebView2 控件使用不同的 UDF。

每个 WebView2 浏览器进程都会占用额外的内存和磁盘空间。  因此，请避免同时运行具有过多不同 UDF 的 WebView2 控件。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [从用户数据文件夹中清除浏览数据](clear-browsing-data.md)
* _在Windows应用开发_文档中[打包和部署](/windows/apps/package-and-deploy/) (生成适用于Windows) 的桌面应用。
* [ClickOnce安全和部署](/visualstudio/deployment/clickonce-security-and-deployment) - Visual Studio部署文档。
* [了解 Microsoft Edge 中的 ClickOnce 和 DirectInvoke 功能](/deployedge/edge-learn-more-co-di) - Microsoft Edge Enterprise文档。

<!-- clickable: https://docs.microsoft.com/windows/apps/package-and-deploy/ -->
