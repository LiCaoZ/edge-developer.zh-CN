---
title: 从用户数据文件夹中清除浏览数据
description: 如何清除 WebView2 应用的用户数据文件夹中的浏览数据以释放空间。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 02/09/2022
ms.openlocfilehash: 9cfde870bef656fede7f5e16b457bc7440af3940
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433688"
---
# <a name="clear-browsing-data-from-the-user-data-folder"></a>从用户数据文件夹中清除浏览数据

若要清除 WebView2 应用的用户数据文件夹中的浏览数据并释放空间，请调用清除浏览数据 API 的方法。

"清除浏览数据"API 允许你以编程方式擦除与 WebView2 用户配置文件关联的用户数据文件夹中的数据。[](user-data-folder.md)  例如，使用此 API 在用户退出时清除用户数据和历史记录。

您可以：
*  清除所有浏览数据。
*  清除所选的浏览数据类型。
*  清除指定时间范围内选定的浏览数据类型。


<!-- ====================================================================== -->
## <a name="clear-all-browsing-data"></a>清除所有浏览数据

此方法清除在数据类型枚举中列出的所有类型的浏览数据，而不管数据是何时创建的。  它清除调用方法的用户配置文件的用户数据文件夹中的数据。


<!-- ------------------------------ -->
# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2ExperimentalProfile4：：ClearBrowsingDataAll () 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataall)


<!-- ------------------------------ -->
# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync () 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync)

---
<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="clear-selected-kinds-of-browsing-data"></a>清除所选浏览数据类型

此方法清除指定的浏览数据类型，无论数据创建时间如何。  它清除调用方法的用户配置文件的用户数据文件夹中的数据。


<!-- ------------------------------ -->
# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2Profile：：ClearBrowsingData (dataKinds) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdata)

[COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)


<!-- ------------------------------ -->
# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds))

[CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)

---
<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="clear-selected-kinds-of-browsing-data-in-a-time-range"></a>清除一个时间范围内选定的浏览数据类型

此方法清除在指定的开始时间和结束时间之间创建的指定类型的浏览数据。  它清除调用方法的用户配置文件的用户数据文件夹中的数据。


<!-- ------------------------------ -->
# [<a name="c"></a>C++](#tab/cpp)

[ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)

[COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)


<!-- ------------------------------ -->
# [<a name="c"></a>C#](#tab/csharp)

[CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds， startTime， endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))

[CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)

---
<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="example-clearing-selected-kinds-of-browsing-data-in-a-time-range"></a>示例：清除一个时间范围内选定的浏览数据类型

本示例清除上一小时内的自动填充数据和密码自动保存数据。

以下参数值将传递给"清除浏览数据 API"方法：

*  所选类型的浏览器数据 = 自动填充数据和密码自动保存数据。

*  指定的时间范围 = 过去一小时 (3600 秒) 。


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

**API：**

* [ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)
* [COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)
* [ICoreWebView2ClearBrowsingDataCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalclearbrowsingdatacompletedhandler)


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

**API：**

* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds， startTime， endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))
* [CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)

---
<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="api-reference"></a>API 参考


<!-- ------------------------------ -->
# [<a name="c"></a>C++](#tab/cpp)

* [ICoreWebView2Profile：：ClearBrowsingDataAll () 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataall)
* [ICoreWebView2Profile：：ClearBrowsingData (dataKinds) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdata)
* [ICoreWebView2Profile：：ClearBrowsingDataInTimeRange (dataKinds、startTime、endTime) 方法](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalprofile4#clearbrowsingdataintimerange)
* [COREWEBVIEW2_BROWSING_DATA_KINDS枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_browsing_data_kinds)
* [ICoreWebView2ClearBrowsingDataCompletedHandler 接口](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalclearbrowsingdatacompletedhandler)


<!-- ------------------------------ -->
# [<a name="c"></a>C#](#tab/csharp)

* [CoreWebView2.Profile 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2.profile)
* [CoreWebView2Profile 类](/dotnet/api/microsoft.web.webview2.core.corewebview2profile)
* [CoreWebView2Profile.ClearBrowsingDataAsync () 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync)
* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds))
* [CoreWebView2Profile.ClearBrowsingDataAsync (dataKinds， startTime， endTime) 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2profile.clearbrowsingdataasync#microsoft-web-webview2-core-corewebview2profile-clearbrowsingdataasync(microsoft-web-webview2-core-corewebview2browsingdatakinds-system-datetime-system-datetime))
* [CoreWebView2BrowsingDataKinds 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2browsingdatakinds)

---
<!-- end of tab-set -->


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [管理用户数据文件夹](user-data-folder.md)
* [清除浏览数据 API 规范](https://github.com/MicrosoftEdge/WebView2Feedback/blob/master/specs/ClearBrowsingData.md)
