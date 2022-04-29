---
title: 从用户数据文件夹中清除浏览数据
description: 如何清除 WebView2 应用的用户数据文件夹中的浏览数据以释放空间。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: 1b7e20c6920fda8f92414061a2ad4b172ed32a66
ms.sourcegitcommit: b2062efd99182cb0b6c3115439fb45838841b276
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2022
ms.locfileid: "12496685"
---
# <a name="clear-browsing-data-from-the-user-data-folder"></a>从用户数据文件夹中清除浏览数据

若要清除 WebView2 应用的用户数据文件夹中的浏览数据并释放空间，请调用 Clear Browsing Data API 的方法。

使用 Clear Browsing Data API，可以以编程方式清除与 WebView2 用户配置文件关联的 [用户数据文件夹](user-data-folder.md) 中的数据。  例如，使用此 API 在用户注销时清除用户数据和历史记录。

您可以：
*  清除所有浏览数据。
*  清除所选类型的浏览数据。
*  清除指定时间范围内的选定类型的浏览数据。


<!-- ====================================================================== -->
## <a name="clear-all-browsing-data"></a>清除所有浏览数据

无论何时创建数据，此方法都会清除数据类型枚举中列出的所有类型的浏览数据。  它从调用该方法的用户配置文件的用户数据文件夹中清除数据。


<!-- ------------------------------ -->

# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync () 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync)


<!-- ------------------------------ -->

# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2Profile：：ClearBrowsingDataAll () 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataall)


---

<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="clear-selected-kinds-of-browsing-data"></a>清除所选类型的浏览数据

无论何时创建数据，此方法都会清除指定类型的浏览数据。  它从调用该方法的用户配置文件的用户数据文件夹中清除数据。


<!-- ------------------------------ -->

# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds))

[CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)


<!-- ------------------------------ -->

# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2Profile：：ClearBrowsingData (dataKinds) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdata)

[COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)

---

<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="clear-selected-kinds-of-browsing-data-in-a-time-range"></a>清除时间范围内选定类型的浏览数据

此方法清除在指定的开始时间和结束时间之间创建的指定类型的浏览数据。  它从调用该方法的用户配置文件的用户数据文件夹中清除数据。


<!-- ------------------------------ -->

# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds、startTime、endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))

[CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)


<!-- ------------------------------ -->

# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)

[COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)

---

<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="example-clearing-selected-kinds-of-browsing-data-in-a-time-range"></a>示例：清除时间范围内选定类型的浏览数据

本示例清除过去一小时内的自动填充数据和密码自动保存数据。

以下参数值将传递给 Clear Browsing Data API 方法：

*  所选类型的浏览器数据 = 自动填充数据和密码自动保存数据。

*  指定的时间范围 = 过去一小时 (3600 秒) 。


<!-- ------------------------------ -->

# [<a name="c"></a>C#](#tab/csharp)

```csharp
// Clears autofill data.
private void ClearAutofillData()
{
    CoreWebView2Profile profile;
    if (webView.CoreWebView2 != null)
    {
        profile = webView.CoreWebView2.Profile;
        // Get the current time, the time in which the browsing data will be cleared
        // until.
        System.DateTime endTime = DateTime.Now;
        System.DateTime startTime = DateTime.Now.AddHours(-1);
        // Offset the current time by one hour to clear the browsing data from the
        // last hour.
        CoreWebView2BrowsingDataKinds dataKinds = (CoreWebView2BrowsingDataKinds)
                                 (CoreWebView2BrowsingDataKinds.GeneralAutofill | 
                                  CoreWebView2BrowsingDataKinds.PasswordAutosave);
        await profile.ClearBrowsingDataAsync(dataKinds, startTime, endTime);
    }
}
```

**Api：**

* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds、startTime、endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))
* [CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)


<!-- ------------------------------ -->

# [<a name="c"></a>C++](#tab/cpp)

```cpp
// Clears the autofill data from the last hour.
void ClearAutofillData()
{
    wwil::com_ptr<ICoreWebView2> coreWebView2;
    CHECK_FAILURE(m_controller->get_CoreWebView2(&coreWebView2));

    auto webview7 = coreWebView2.try_query<ICoreWebView2_7>();
    if (webview7)
    {
        wil::com_ptr<ICoreWebView2Profile> profile;
        CHECK_FAILURE(webview7->get_Profile(&profile));
        double endTime = (double)std::time(nullptr);
        double startTime = endTime - 3600;
        // Get the current time and offset the current time by 3600 seconds to clear
        // the data from the start time (one hour ago), until the end time (present 
        // time).
        // This clears the data for the last hour.
        COREWEBVIEW2_BROWSING_DATA_KINDS dataKinds = 
            (COREWEBVIEW2_BROWSING_DATA_KINDS)
            (COREWEBVIEW2_BROWSING_DATA_KINDS_GENERAL_AUTOFILL |
            COREWEBVIEW2_BROWSING_DATA_KINDS_PASSWORD_AUTOSAVE);
        CHECK_FAILURE(profile->ClearBrowsingDataInTimeRange(
            dataKinds, startTime, endTime,
            Callback<ICoreWebView2ClearBrowsingDataCompletedHandler>(
                [this](HRESULT error)
                    -> HRESULT {
                    return S_OK;
                })
                .Get()));
    }
}
```

**Api：**

* [ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)
* [COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)
* [ICoreWebView2ClearBrowsingDataCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalclearbrowsingdatacompletedhandler)

---

<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="api-reference"></a>API 参考


<!-- ------------------------------ -->

# [<a name="c"></a>C#](#tab/csharp)

* [CoreWebView2.Profile 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.profile)
* [CoreWebView2Profile 类](/dotnet/api/microsoft.web.webview2.core.corewebview2profile)
* [CoreWebView2Profile.ClearBrowsingDataAsync () 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync)
* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds))
* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds、startTime、endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))
* [CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)


<!-- ------------------------------ -->

# [<a name="c"></a>C++](#tab/cpp)

* [ICoreWebView2Profile：：ClearBrowsingDataAll () 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataall)
* [ICoreWebView2Profile：：ClearBrowsingData (dataKinds) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdata)
* [ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)
* [COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)
* [ICoreWebView2ClearBrowsingDataCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalclearbrowsingdatacompletedhandler)

---

<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [管理用户数据文件夹](user-data-folder.md)
* [指定清除浏览数据 API](https://github.com/MicrosoftEdge/WebView2Feedback/blob/main/specs/ClearBrowsingData.md)
