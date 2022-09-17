---
title: 从 Web 端代码调用本机代码
description: 如何使用适用于 WebView2 应用的 AddHostObjectToScript API 将主机对象传递到 JavaScript。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 04/27/2022
ms.openlocfilehash: d234122b154e488091137c53f7e7215110e7a9a4
ms.sourcegitcommit: ff01ae09a41be04a53ca8ee918bbf5fb999543c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2022
ms.locfileid: "12754586"
---
# <a name="call-native-side-code-from-web-side-code"></a>从 Web 端代码调用本机代码

WebView2 使应用程序能够通过启用要传递到 Web 的对象来弥合应用程序的 Web 和本机端之间的差距。 此类对象在本机代码中定义，通常称为 *主机对象*。 可以使用 WebView2 `AddHostObjectToScript` API 将它们投影到 JavaScript 中，如本文档中所述。

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addhostobjecttoscript)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#addhostobjecttoscript)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript)

---


#### <a name="why-use-addhostobjecttoscript"></a>为什么要使用 `AddHostObjectToScript`？

  * 开发 WebView2 应用时，可能会遇到一个本机对象，该对象的方法或属性非常有用。 你可能想要从 Web 端代码触发这些本机对象方法，或者是应用 Web 端的用户交互的结果。 此外，你可能不想在 Web 端代码中重新实现本机对象的方法。  API `AddHostObjectToScript` 允许通过 Web 端代码重新使用本机端代码。 

  * 例如，可能有一个本机网络摄像头 API，需要在 Web 端重新编写大量代码。 能够调用本机对象的方法比在应用的 Web 端重新编码对象的方法更快、更高效。 在这种情况下，本机代码可以将对象传递到应用的 Web 端 JavaScript 代码，以便 JavaScript 代码可以重复使用本机 API 的方法。

在脚本中使用主机对象可能受益的方案：

  * 有一个键盘 API，你想要从 Web 端调用该 `keyboardObject.showKeyboard` 函数。

  * JavaScript 是沙盒的，限制了其在本机端的功能。 例如，如果需要访问本机端的文件，则必须使用本机文件系统。 如果你有一个通过 `AddHostObjectToScript`JavaScript 公开的本机对象，则可以使用它来操作本机文件系统上的文件。

本文使用 [Win32 示例应用](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample) 演示一些实际的 `AddHostObjectToScript`应用程序。 有关如何将 Web 内容嵌入本机应用程序的详细信息，请参阅 [将 Web 内容嵌入本机应用程序](/microsoft-edge/webview2/how-to/communicate-btwn-web-native)。


#### <a name="preview-of-the-major-steps-in-this-article"></a>本文中主要步骤的预览

1. 安装 Visual Studio、安装 git、克隆 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples/tree/main/SampleApps/WebView2APISample)并打开解决方案。

1. 定义主机对象并实现 `IDispatch` ，以便 WebView2 可以投影/将其添加到 Web 端。

1. 用于 `AddHostObjectToScript` 将对象传递到 Web。

1. 从应用的 Web 端代码调用应用的本机对象的方法。


<!-- ====================================================================== -->
## <a name="step-1-install-visual-studio-install-git-clone-the-webview2samples-repo-and-open-the-solution"></a>步骤 1：安装 Visual Studio、安装 git、克隆 WebView2Samples 存储库并打开解决方案

1. 下载并安装 [Microsoft Visual Studio](https://visualstudio.microsoft.com/) 2019 (版本 16.11.10) 或更高版本，以及 [Win32 应用中 WebView2 入门中](/microsoft-edge/webview2/get-started/win32)所述的其他先决条件。

1. 克隆 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库，其中包括特定于 Win32 的 WebView2 示例应用。  有关说明，请在新窗口或选项卡中打开  [Win32 应用中的 WebView2 入](/microsoft-edge/webview2/get-started/win32)门。

1. 打开 Microsoft Visual Studio。

1. 在克隆 `WebView2Samples` 存储库的本地副本中，打开 `GettingStartedGuides > Win32_GettingStarted > WebView2GettingStarted.sln`。 使示例应用解决方案保持打开状态，以配合本文的其余部分。


<!-- ====================================================================== -->
## <a name="step-2-define-the-host-object-and-implement-idispatch"></a>步骤 2：定义主机对象并实现 IDispatch

若要使用此 `AddHostObjectToScript` API，首先需要定义实现的 `IDispatch`主机对象。 如果已有实现的 `IDispatch`主机对象，请跳到 [步骤 3：调用 AddHostObjectToScript API](#step-3-call-the-addhostobjecttoscript-api)。 实现 `IDispatch` 对于设置主机对象的格式，以便将其传递到 Web 端代码至关重要。

以下示例从头开始创建主机对象。

**第 2A 部分：** 使用接口定义语言 (IDL) 创建 COM 接口。 此操作在文件中 `HostObjectSample.idl` 演示。 

**第 2B 部分：** 创建 C++ 对象。 此操作在文件中 `HostObjectSampleImpl.cpp` 演示。

**重要：** IDL (`.idl`) 文件 *定义* 接口，C++ () `.cpp` 文件 *实现定义的* 接口，并实现 `IDispatch`。

### <a name="part-2a-create-the-com-interface"></a>第 2A 部分：创建 COM 接口

在 WebView2 示例代码中，该文件 `HostObjectSample.idl` 创建一个 COM 对象。 此步骤介绍如何在 IDL 文件中创建自己的对象。

1. 在 Visual Studio **解决方案资源管理器**中，打开 **WebView2APISample** > **源文件** > **HostObjectSample.idl**。

    以下代码示例分为两个部分。 第一个接口是 `IHostObjectSample`从继承 `IUnknown` 接口的第 9 行开始。 使用此 `IHostObjectSample` 定义作为模板来定义对象的方法、属性、回调函数等。
    
    第二部分是 `HostObjectSample` 组件对象类 [coclass](/windows/win32/midl/coclass)，从第 35 行（包括 `IDispatch` ）和  `IHostObjectSample` 接口开始。

    ```csharp
     1    import "oaidl.idl";
     2    import "ocidl.idl";
     3
     4    [uuid(0a7a4655-5660-47d0-8a37-98ae21399e57), version(0.1)]
     5    library HostObjectSampleLibrary
     6    {
     7        //! [AddHostObjectInterface]
     8        [uuid(3a14c9c0-bc3e-453f-a314-4ce4a0ec81d8), object, local]
     9        interface IHostObjectSample : IUnknown
    10        {
    11            // Demonstrates a basic method call with some parameters and a return value.
    12            HRESULT MethodWithParametersAndReturnValue([in] BSTR stringParameter, [in] INT integerParameter, [out, retval] BSTR* stringResult);
    13    
    14           // Demonstrate getting and setting a property.
    15            [propget] HRESULT Property([out, retval] BSTR* stringResult);
    16            [propput] HRESULT Property([in] BSTR stringValue);
    17
    18            [propget] HRESULT IndexedProperty(INT index, [out, retval] BSTR * stringResult);
    19            [propput] HRESULT IndexedProperty(INT index, [in] BSTR stringValue);
    20
    21            // Demonstrate native calling back into JavaScript.
    22            HRESULT CallCallbackAsynchronously([in] IDispatch* callbackParameter);
    23
    24            // Demonstrates a property which uses Date types.    25            [propget] HRESULT DateProperty([out, retval] DATE * dateResult);
    26            [propput] HRESULT DateProperty([in] DATE dateValue);
    27
    28            // Creates a date object on the native side and sets the DateProperty to it.
    29            HRESULT CreateNativeDate();
    30
    31        };
    32        //! [AddHostObjectInterface]
    33
    34        [uuid(637abc45-11f7-4dde-84b4-317d62a638d3)]
    35        coclass HostObjectSample
    36        {
    37            [default] interface IHostObjectSample;
    38            interface IDispatch;
    39        };
    40    }
    ```

1. 第38行，我们包括 `interface IDispatch`，这是需要我们的主机对象使用 `AddHostObjectToScript`。

    **关于 IDispatch**：

    `IDispatch` 允许你动态调用方法和属性。 通常，调用对象需要静态调用，但可以使用 JavaScript 动态创建对象调用。 有关 `IDispatch` 继承和方法的详细信息，请 [参阅 IDispatch 接口 (oaidl.h) ](/windows/win32/api/oaidl/nn-oaidl-idispatch)。 
    
    如`IDispatch`[类型库和对象描述语言](/previous-versions/windows/desktop/automat/type-libraries-and-the-object-description-language)中所述实现。
    
    如果要添加到 JavaScript 的对象尚未实现 `IDispatch`，则需要为要公开的对象编写 `IDispatch` 类包装器。

    可能有库可以自动执行此操作。  若要详细了解为要公开的对象编写 `IDispatch` 类包装所需的步骤，请参阅 [自动化](/previous-versions/windows/desktop/automat/automation-programming-reference)。
    
1. 在 IDL 中定义接口后，在 Visual Studio 中保存并编译示例项目，以创建转换外观缓冲区 (TLB) 文件。 需要从以下部分中所示的 C++ 源代码引用 TLB 文件。

### <a name="part-2b-create-the-c-object"></a>第 2B 部分：创建 C++ 对象

在 WebView2 示例代码中， `HostObjectSampleImpl.cpp` 该文件采用 COM IDL 文件中创建的框架并生成 C++ 对象。

实现对象界面中定义的所有函数，如 IDL 文件中所述。 请务必实现所需的函数 `IDispatch`。  如果未定义这些函数，编译器将引发错误。

接下来，我们检查 IDL 中定义的两个特定属性，以显示 IDL 与文件的相关 `.cpp` 性。

1.  在 Visual Studio **解决方案资源管理器**中，打开 **WebView2APISample** > **源文件** > **HostObjectSampleImpl.cpp**。

1.  比较属性 *声明*，在 `HostObjectSample.idl` ...
 
    ```csharp
    [propget] HRESULT Property([out, retval] BSTR* stringResult);
    [propput] HRESULT Property([in] BSTR stringValue);
    ```
    ...若要 *实现* 对象的属性，请执行以下操作 `HostObjectSampleImpl.cpp`：

    ```cpp
    STDMETHODIMP HostObjectSample::get_Property(BSTR* stringResult)
    {
        *stringResult = SysAllocString(m_propertyValue.c_str());
        return S_OK;
    }
    
    STDMETHODIMP HostObjectSample::put_Property(BSTR stringValue)
    {
        m_propertyValue = stringValue;
        return S_OK;
    }
    ```


<!-- ====================================================================== -->
## <a name="step-3-call-the-addhostobjecttoscript-api"></a>步骤 3：调用 AddHostObjectToScript API

到目前为止，我们已经构建了接口并实现了主机对象。 现在，我们已准备好使用 `AddHostObjectToScript` API 将主机对象传递到应用的 Web 端 JavaScript 代码。

1. 在 Visual Studio **解决方案资源管理器**中，打开 **WebVie2APISample** > **源文件** > **ScenarioHostObject.cpp**。

1. 转到课程开始的第 `ScenarioAddHostObject` 28 行。

    ```cpp
    28    ScenarioAddHostObject::ScenarioAddHostObject(AppWindow* appWindow)
    29        : m_appWindow(appWindow), m_webView(appWindow->GetWebView())
    30    {
    31        std::wstring sampleUri = m_appWindow->GetLocalUri(L"ScenarioAddHostObject.html");
    32
    33        m_hostObject = Microsoft::WRL::Make<HostObjectSample>(
    34            [appWindow = m_appWindow](std::function<void(void)> callback)
    35        {
    36            appWindow->RunAsync(callback);
    37        });
    38
    39        CHECK_FAILURE(m_webView->add_NavigationStarting(
    40            Microsoft::WRL::Callback<ICoreWebView2NavigationStartingEventHandler>(
    41                [this, sampleUri](ICoreWebView2* sender, ICoreWebView2NavigationStartingEventArgs* args) -> HRESULT
    42        {
    43            wil::unique_cotaskmem_string navigationTargetUri;
    44            CHECK_FAILURE(args->get_Uri(&navigationTargetUri));
    45            std::wstring uriTarget(navigationTargetUri.get());
    46
    47            if (AreFileUrisEqual(sampleUri, uriTarget))
    48            {
    49                //! [AddHostObjectToScript]
    50                VARIANT remoteObjectAsVariant = {};
    51                m_hostObject.query_to<IDispatch>(&remoteObjectAsVariant.pdispVal);
    52                remoteObjectAsVariant.vt = VT_DISPATCH;
    53
    54                // We can call AddHostObjectToScript multiple times in a row without
    55                // calling RemoveHostObject first. This will replace the previous object
    56                // with the new object. In our case this is the same object and everything
    57                // is fine.
    58                CHECK_FAILURE(
    59                    m_webView->AddHostObjectToScript(L"sample", &remoteObjectAsVariant));
    60                remoteObjectAsVariant.pdispVal->Release();
    61                //! [AddHostObjectToScript]
    62            }
    ```

    第 31 行到第 46 行显示特定于此示例应用的代码，我们在其中显示 HTML。 你的应用可能具有此代码的不同实现。  

1. 查看第 33 行，显示如何实例化 IDL 文件中刚定义的 COM 对象。 这是我们稍后在调用 `AddHostObjectToScript`时使用的对象。 这会给我们一个指向接口的 `HostObjectSampleImpl.cpp`指针。

1. 查看第 51 行，该行将新创建的 COM 对象转换为类型 `IDispatch` ，然后将该对象转换为一个 `VARIANT`类型。 `VARIANT` 类型允许你使用数据结构，如整数和数组，以及更复杂的类型，如 `IDispatch`。 

    有关受支持数据类型的完整列表，请[参阅 VARIANT 结构 (oaidl.h) - Win32 应用|Microsoft Docs](/windows/win32/api/oaidl/ns-oaidl-variant)。但是，请注意，联盟中`VARIANT`并非所有类型都受`AddHostObjectToScript`支持。 请参阅 [WebView2 Win32 C++ ICoreWebView2 |Microsoft Docs](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript)了解更多详细信息。
    
    现在，我们的对象变体对 C++ 代码友好，应用的本机端代码已准备好将主机对象传递到应用的 Web 端代码。

1. 查看第 52 行，该行将远程对象变体类型设置为 `IDispatch`。 

1. 查看第 59 行，在其中传递 `VARIANT` 给 `AddHostObjectToScript`远程对象，将其 `sample`命名，并启用远程对象作为 `VARIANT` () `&remoteObjectAsVariant` 。

现在，WebView2 应用的本机端代码已成功创建实现的 `IDispatch`主机对象。 此本机代码还会调用 WebView2 API `AddHostObjectToScript` ，并通过将对象传递给应用的 Web 端代码 `AddHostObjectToScript`。 继续执行下一步，了解通过将主机对象从应用的本机端代码传递到应用的 Web 端代码来启用的内容。


<!-- ====================================================================== -->
## <a name="step-4-use-addhostobjecttoscript-to-pass-a-method-to-the-web"></a>步骤 4：使用 AddHostObjectToScript 将方法传递到 Web

若要继续操作，我们使用 WebView2 示例应用。  

1. 在 Microsoft Visual Studio 中，选择 **“文件** > **保存所有 (Ctrl+Shift+S) ** 以保存项目。

1. 按 **F5** 生成并运行项目。

1. 打开 `ScenarioAddHostObject.html`。

1. 单击 **方案** > **主机对象**。

1. 通过单击**属性、****方法**和**回调**等按钮来浏览属性，以查看示例代码的行为方式。

    至此，你已观察到从应用的 Web 端代码中使用的主机对象的功能。 若要深入了解 JavaScript 中发生的情况，我们来检查以下代码： 

    ```html
    150    // Date property 
    151    document.getElementById("setDateButton").addEventListener("click", () => { 
    152        chrome.webview.hostObjects.options.shouldSerializeDates = true; 
    153        chrome.webview.hostObjects.sync.sample.dateProperty = new Date(); 
    154        document.getElementById("dateOutput").textContent = "sample.dateProperty: " + chrome.webview.hostObjects.sync.sample.dateProperty; 
    155    }); 
    156    document.getElementById("createRemoteDateButton").addEventListener("click", () => { 
    157        chrome.webview.hostObjects.sync.sample.createNativeDate(); 
    158        document.getElementById("dateOutput").textContent = "sample.dateProperty: " + chrome.webview.hostObjects.sync.sample.dateProperty; 
    159    });
    ```

    第 154 行引用 `chrome.webview.hostObjects.sync.sample.dateProperty`。 此代码行获取本 `dateProperty` 机主机对象。

祝贺你！ 你已在应用的本机代码中成功创建了主机对象，将主机对象传递给应用的 Web 端代码，然后使用应用的 Web 端代码中的主机对象。

现在，让我们看看主机对象生态系统中还有哪些其他 API。 有关主机对象的详细信息，请参阅 [WebView2 Win32 C++ ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-1.0.1054.31#addhostobjecttoscript&preserve-view=true)。


<!-- ====================================================================== -->
## <a name="api-reference-overview"></a>API 参考概述

##### [<a name="netc"></a>.NET/C#](#tab/dotnetcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.addhostobjecttoscript)
* [CoreWebView2.RemoveHostObjectFromScript 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2.removehostobjectfromscript)
* [CoreWebView2Settings.AreHostObjectsAllowed 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.arehostobjectsallowed)

##### [<a name="winrtc"></a>WinRT/C#](#tab/winrtcsharp)

* [CoreWebView2.AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#addhostobjecttoscript)
* [CoreWebView2.RemoveHostObjectFromScript 方法](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2#removehostobjectfromscript)
* [CoreWebView2Settings.AreHostObjectsAllowed 属性](/microsoft-edge/webview2/reference/winrt/microsoft_web_webview2_core/corewebview2settings#arehostobjectsallowed)

##### [<a name="win32c"></a>Win32/C++](#tab/win32cpp)

* [ICoreWebView2：：AddHostObjectToScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript)
* [ICoreWebView2：：RemoveHostObjectFromScript 方法](/microsoft-edge/webview2/reference/win32/icorewebview2#removehostobjectfromscript)
* [ICoreWebView2Settings：：AreHostObjectsAllowed 属性 (获取](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_arehostobjectsallowed)， [放) ](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_arehostobjectsallowed)

---


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* _WebView2 功能和 API 概述中的 Web_[/本机互操作](../concepts/overview-features-apis.md#webnative-interop)。
