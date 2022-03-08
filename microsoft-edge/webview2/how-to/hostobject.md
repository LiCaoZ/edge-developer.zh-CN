---
title: 从 Web 端代码调用本机代码
description: 如何使用适用于 WebView2 应用的 AddHostObjectToScript API 将主机对象传递到 JavaScript。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 2/28/2022
ms.openlocfilehash: 1c8e7c71ec6f4773d3293b993f0eb333c7f16950
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12433507"
---
# <a name="call-native-side-code-from-web-side-code"></a>从 Web 端代码调用本机代码

WebView2 使应用程序能够将对象传递到 Web，从而缩小应用程序的 Web 和本机面之间的间隙。 此类对象在本机代码中定义，通常称为 *host 对象*。 它们可以使用 WebView2 `AddHostObjectToScript` API 计划到 JavaScript 中，如本文档中所述。

为什么使用 `AddHostObjectToScript`？

  * 开发 WebView2 应用时，你可能会遇到一个本机对象，该对象的方法或属性非常有用。 你可能想要从 Web 端代码触发这些本机对象方法，或者由于应用 Web 端上的用户交互而触发。 此外，您可能不希望在 Web 端代码中重新实现本机对象的方法。  API `AddHostObjectToScript` 支持通过 Web 端代码重新使用本机代码。 

  * 例如，可能有本机网络摄像机 API，这需要在 Web 端重新编写大量代码。 能够调用本机对象的方法比在应用的 Web 端重新编码对象的方法更快速、更高效。 在这种情况下，本机代码可以将对象传递到应用的 Web 端 JavaScript 代码，以便 JavaScript 代码可以重复使用本机 API 的方法。

可能受益于在脚本中使用主机对象的方案：

  * 存在键盘 API，并且你想要从 Web `keyboardObject.showKeyboard` 端调用 函数。

  * JavaScript 是沙盒，限制了其本机功能。 例如，如果需要访问本机上的文件，则必须使用本机文件系统。 如果你有通过 公开给 JavaScript `AddHostObjectToScript`的本机对象，可以使用它操作本机文件系统上的文件。

本文使用 [WebView2 Win32 示例应用](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample) 演示 的一些实际应用程序 `AddHostObjectToScript`。 若要详细了解如何将 Web 内容嵌入本机应用程序中，请参阅 [将 Web 内容嵌入本机应用程序](/microsoft-edge/webview2/how-to/communicate-btwn-web-native)。

**预览本文中的主要步骤：**

1. 安装Visual Studio、安装 git、克隆 [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples/tree/master/SampleApps/WebView2APISample)，然后打开解决方案。

1. 定义主机对象并实现 `IDispatch` ，以便 WebView2 可以将其项目/添加到 Web 端。

1. 用于 `AddHostObjectToScript` 将对象传递到 Web。

1. 从应用的 Web 端代码调用应用的本机对象的方法。


<!-- ====================================================================== -->
## <a name="step-1-install-visual-studio-install-git-clone-the-webview2samples-repo-and-open-the-solution"></a>步骤 1：Visual Studio、安装 git、克隆 WebView2Samples 存储库并打开解决方案

1. 下载并安装 [Microsoft Visual Studio](https://visualstudio.microsoft.com/) 2019 (版本 16.11.10) 或更高版本，以及 [Win32 应用中的 WebView2](/microsoft-edge/webview2/get-started/win32) 入门中所述的其他先决条件。

1. 克隆 [WebView2Samples](https://github.com/MicrosoftEdge/WebView2Samples) 存储库，其中包括特定于 Win32 的 WebView2 示例应用。  有关说明，在新建窗口或选项卡中，打开  [Win32 应用中的 WebView2 入门](/microsoft-edge/webview2/get-started/win32)。

1. 打开 Microsoft Visual Studio。

1. 在克隆存储库的本地副本中 `WebView2Samples` ，打开 `GettingStartedGuides > Win32_GettingStarted > WebView2GettingStarted.sln`。 保持示例应用解决方案为打开状态，以遵循本文的其余部分。


<!-- ====================================================================== -->
## <a name="step-2-define-the-host-object-and-implement-idispatch"></a>步骤 2：定义主机对象和实现 IDispatch

若要使用此 `AddHostObjectToScript` API，首先需要定义实现 的主机对象 `IDispatch`。 如果已经有一个实现 的主机 `IDispatch`对象，请跳到步骤 [3：调用 AddHostObjectToScript API](#step-3-call-the-addhostobjecttoscript-api)。 实现 `IDispatch` 对设置主机对象的格式至关重要，以便可以传递给 Web 端代码。

下面的示例从头创建一个主机对象。

**第 2A 部分：** 使用接口定义语言和 IDL (COM) 。 这一点在 文件中 `HostObjectSample.idl` 演示。 

**第 2B 部分：** 创建 C++ 对象。 这一点在 文件中 `HostObjectSampleImpl.cpp` 演示。

**重要提示：** IDL (`.idl`) 定义接口，C**++ `.cpp` (*) 文件实现*定义的接口，并且还实现 。`IDispatch`

### <a name="part-2a-create-the-com-interface"></a>第 2A 部分：创建 COM 接口

在 WebView2 示例代码中，该文件 `HostObjectSample.idl` 将创建一个 COM 对象。 此步骤介绍如何在 IDL 文件中创建自己的对象。

1. 在Visual Studio**资源管理器**"中，打开 **WebView2APISampleSource** >  **FilesHostObjectSample.idl****** > 。

    以下代码示例分为两个部分。 第一个接口 `IHostObjectSample`是从第 9 行开始，它继承该 `IUnknown` 接口。 `IHostObjectSample`使用此定义作为模板来定义对象的方法、属性、回调函数等。
    
    第二部分是组件 `HostObjectSample` 对象类 [coclass](/windows/win32/midl/coclass)，从第 35 行开始，其中包括 `IDispatch` 和  `IHostObjectSample` 接口。

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

1. 在行 38 中， `interface IDispatch`我们包括了 ，主机对象需要此代码才能使用 `AddHostObjectToScript`。

    **关于 IDispatch**：

    `IDispatch` 允许你动态调用方法和属性。 通常，调用对象需要静态调用，但可以使用 JavaScript 动态创建对象调用。 有关继承和方法的信息 `IDispatch` ，请参阅 [IDispatch interface (oaidl.h) ](/windows/win32/api/oaidl/nn-oaidl-idispatch)。 
    
    如 `IDispatch` 类型库 [和对象描述语言中所述实现](/previous-versions/windows/desktop/automat/type-libraries-and-the-object-description-language)。
    
    如果要添加到 JavaScript `IDispatch``IDispatch` 的对象还没有实现 ，则需要为要公开的对象编写类包装。

    可能有一些库可以自动执行这一操作。  若要了解有关为要公开 `IDispatch` 的对象编写类包装器所需的步骤，请参阅 [自动化](/previous-versions/windows/desktop/automat/automation-programming-reference)。
    
1. 在 IDL 中定义接口后，在 Visual Studio 中保存并编译示例项目，以在 TLB (创建) 缓冲区。 你需要从 C++ 源代码引用 TLB 文件，如以下部分所示。

### <a name="part-2b-create-the-c-object"></a>第 2B 部分：创建 C++ 对象

在 WebView2 示例代码中 `HostObjectSampleImpl.cpp` ，文件采用在 COM IDL 文件中创建框架并生成 C++ 对象。

实现在对象接口中定义的所有函数，如 IDL 文件所述。 请务必实现 所需的函数 `IDispatch`。  如果未定义这些函数，编译器将引发错误。

接下来，我们检查在 IDL 中定义的两个特定属性，以显示 IDL 与文件是如何相关的 `.cpp` 。

1. 在Visual Studio**资源管理器**"中，打开 **WebView2APISampleSource** >  **FilesHostObjectSampleImpl.cpp****** > 。

1. 比较 ... *中的*属性声明`HostObjectSample.idl`
 
    ```csharp
    [propget] HRESULT Property([out, retval] BSTR* stringResult);
    [propput] HRESULT Property([in] BSTR stringValue);
    ```
    ...到 *对象* 属性的实现，在 `HostObjectSampleImpl.cpp`中：

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

到目前为止，我们已经构建了接口并实现了我们的主机对象。 现在我们可以使用 API 将 `AddHostObjectToScript` 主机对象传递到应用的 Web 端 JavaScript 代码。

1. 在Visual Studio**资源管理器**"中，打开 **Web在 2APISampleSource** >  **文件** > **ScenarioHostObject.cpp**。

1. 转到第 28 行，其中 `ScenarioAddHostObject` 类开始。

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

    第 31 至 46 行显示特定于此示例应用的代码，我们在此显示 HTML。 你的应用可能对此代码具有不同的实现。  

1. 查看第 33 行，其中显示了如何实例化 IDL 文件中刚定义的 COM 对象。 这是我们稍后在调用 时将使用的对象 `AddHostObjectToScript`。 这将获取指向 中接口的指针 `HostObjectSampleImpl.cpp`。

1. 查看第 51 行，该行将新创建的 COM `IDispatch` 对象转换为类型，然后将该对象转换为 `VARIANT`。 `VARIANT` types 允许您使用数据结构（如整数和数组）以及更复杂的类型（如 `IDispatch`）。 

    有关受支持的数据类型的完整列表，请参阅 [VARIANT structure (oaidl.h) - Win32 apps |Microsoft Docs](/windows/win32/api/oaidl/ns-oaidl-variant)。但是，请注意，并非所有联合类型 `VARIANT` 都受 支持 `AddHostObjectToScript`。 请参阅 [WebView2 Win32 C++ ICoreWebView2 |有关更多详细信息，请参阅 Microsoft Docs](/microsoft-edge/webview2/reference/win32/icorewebview2#addhostobjecttoscript) 。
    
    现在我们具有 C++ 代码友好的对象的变体，我们的应用的本机代码已准备好将主机对象传递到应用的 Web 端代码。

1. 查看第 52 行，将远程对象变量类型设置为 `IDispatch`。 

1. 查看第 59 行`VARIANT` `VARIANT` `AddHostObjectToScript``sample``&remoteObjectAsVariant` ，其中我们将 传递到 ，将它命名，并启用远程对象作为 () 。

现在，WebView2 应用的本机代码已成功创建实现 的主机对象 `IDispatch`。 此本机代码还调用 WebView2 API `AddHostObjectToScript` ，并且通过 将对象传递给应用的 Web 端代码 `AddHostObjectToScript`。 继续执行下一步，查看通过将主机对象从应用的本机代码传递到应用的 Web 端代码启用的内容。


<!-- ====================================================================== -->
## <a name="step-4-use-addhostobjecttoscript-to-pass-a-method-to-the-web"></a>步骤 4：使用 AddHostObjectToScript 将方法传递到 Web

为了继续操作，我们使用 WebView2 示例应用。  

1. In Microsoft Visual Studio， select **FileSave All (Ctrl+Shift+S) ** to save the project.**** > 

1. 按 **F5** 生成并运行项目。

1. 打开 `ScenarioAddHostObject.html`。

1. 单击 **"ScenarioHost** >  **对象"**。

1. 通过单击"属性"、**"方法**"和"回调"**** 等按钮来浏览属性，以查看示例代码的行为方式。****

    现在，你已观察到从应用的 Web 端代码使用的主机对象的功能。 若要深入了解 JavaScript 中发生了什么，让我们看一下以下代码： 

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

    第 154 行引用 `chrome.webview.hostObjects.sync.sample.dateProperty`。 此代码行获取 `dateProperty` 本机 host 对象的 。

祝贺你！ 你已成功在应用的本机代码中创建主机对象，将主机对象传递到应用的 Web 端代码，然后从应用的 Web 端代码使用 host 对象。

现在，让我们了解主机对象生态系统中还有哪些其他 API。 有关主机对象详细信息，请参阅 [WebView2 Win32 C++ ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2?view=webview2-1.0.1054.31#addhostobjecttoscript&preserve-view=true)。
