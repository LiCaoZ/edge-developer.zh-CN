---
title: 自定义 WebView2 中的上下文菜单
description: 如何向 WebView2 应用添加右键 (菜单) 菜单。  添加和删除默认 WebView2 上下文菜单中的项。  通过使用从 WebView2 控件传递到应用的数据创建自己的上下文菜单 UI。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
ms.date: 03/10/2022
ms.openlocfilehash: 95eb7032924f37c53e560f5d9e9df56e76b3ab4d
ms.sourcegitcommit: 2631c3835d23d9adaa28c19198319588baf9d8c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2022
ms.locfileid: "12439775"
---
# <a name="customize-context-menus-in-webview2"></a>自定义 WebView2 中的上下文菜单

使用 **ContextMenuRequested** API 自定义 WebView2 (右键单击菜单) 菜单。

WebView2 控件提供默认上下文菜单。


**术语：**

| 术语 | 定义 |
|---|---|
| _菜单项_ | 一个宽泛的术语。  包括复选框、命令、单选按钮、分隔符和子菜单。 |
| _命令_ | 一个较窄的术语。  五种类型的菜单项之一。 |
| _上下文菜单_ | 默认上下文菜单 (单击菜单) WebView2 控件，或自定义上下文菜单 (右键单击菜单) 属于你的主机应用。 |


<!-- ====================================================================== -->
## <a name="adding-a-custom-context-menu"></a>添加自定义上下文菜单

主机应用可以使用从 WebView2 上下文菜单发送的信息绘制自己的上下文菜单，而不是使用默认上下文菜单。  你的应用处理事件 `ContextMenuRequested` 。  可以使用 Event 参数中提供的数据 `ContextMenuRequested` 来显示包含您所选择的条目的自定义上下文菜单。  在这种情况下，你处理事件并请求延迟。

当用户从自定义上下文菜单中选择命令时，你的应用需要通过使用 属性告诉 WebView2 控件用户选择了哪个 `SelectedCommandId` 命令。

您可以将默认菜单项和/或自定义菜单项添加到自定义上下文菜单中。


# [<a name="c"></a>C#](#tab/csharp)

若要显示包含所需菜单项的自定义上下文菜单，请使用 `CoreWebView2ContextMenuRequestedEventArgs` `CoreWebView2` [ContextMenuRequested 事件的 中提供的数据](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)。  对于这种情况，你指定 `Handled` 为 `true`，并请求延迟。 

在事件 `CoreWebView2.ContextMenuRequested` 上，添加具有 的事件侦听器 `CoreWebView2ContextMenuRequestedEventArgs`。

的 `MenuItems` 属性 `CoreWebView2ContextMenuRequestedEventArgs` 为右键单击的上下文提供 WebView2 的上下文菜单项的树。  若要在应用的上下文菜单中`IList<CoreWebView2ContextMenuItem>``CoreWebView2ContextMenuItem`包括 WebView2 上下文菜单项，请通过 ，添加每个菜单项的 。  测试每个 `.Kind` 菜单项的 ，如 `Command` 或 `Separator`。

* **[CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)**
   * [ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)

* **[CoreWebView2ContextMenuItem 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem)**
   * [Children 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.children)
   * [CommandId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.commandid)
   * [IsChecked 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.ischecked)
   * [IsEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.isenabled)
   * [Kind 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.kind)
   * [Label 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.label)
   * [ShortcutKeyDescription 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.shortcutkeydescription)

* **[CoreWebView2ContextMenuRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs)**
   * [ContextMenuTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.contextmenutarget)
   * [Handled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.handled)
   * [MenuItems 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.menuitems)
   * [SelectedCommandId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.selectedcommandid)
   * [GetDeferral 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.getdeferral)

* **[CoreWebView2ContextMenuItemKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitemkind)**
   * `CoreWebView2ContextMenuItemKind.Command`
   * `CoreWebView2ContextMenuItemKind.Separator`

* **[CoreWebView2ContextMenuTargetKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutargetkind)**

* **[CoreWebView2Deferral 类](/dotnet/api/microsoft.web.webview2.core.corewebview2deferral)**
   * [Complete 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2deferral.complete)

* **[CoreWebView2ContextMenuItemKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitemkind)**
   * `CheckBox`
   * `Radio`
   * `Separator`
   * `Submenu`


# [<a name="c"></a>C++](#tab/cpp)

若要显示包含所需菜单项的自定义上下文菜单，请使用 [ICoreWebView2ContextMenuRequestedEventArgs 中提供的数据](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs)。  对于这种情况，你指定 `Handled` 为 `true`，并请求延迟。 

在事件 `ContextMenuRequested` 上，添加具有 的事件侦听器 `ICoreWebView2ContextMenuRequestedEventArgs`。

在项目列表中进行浏览 `ICoreWebView2ContextMenuItem` ，并添加每个 `ICoreWebView2ContextMenuItem` 菜单项的 。  测试每个 `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND` 菜单项的 ，如 `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR` 或 `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND`。

* **[ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6)** (ICoreWebView2Experimental6) 
   * [add_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#add_contextmenurequested)
   * [remove_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#remove_contextmenurequested)

* **[ICoreWebView2ContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem)** () `ICoreWebView2ExperimentalContextMenuItem`
   * [get_Children](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_children)
   * [get_CommandId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_commandid)
   * [get_IsChecked](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_ischecked)
   * [get_IsEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_isenabled)
   * [get_Kind](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_kind)
   * [get_Label](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_label)
   * [get_ShortcutKeyDescription](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_shortcutkeydescription)

* **[ICoreWebView2ContextMenuItemCollection](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection)** () `ICoreWebView2ExperimentalContextMenuItemCollection`
   * [get_Count](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#get_count)
   * [GetValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#getvalueatindex)

* **[ICoreWebView2ContextMenuRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs)** () `ICoreWebView2ExperimentalContextMenuRequestedEventArgs`
   * [put_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#put_handled)
   * [put_SelectedCommandId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#put_selectedcommandid)
   * [get_MenuItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_menuitems)
   * [get_Location](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_location)
   * [GetDeferral](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#getdeferral)

* **[ICoreWebView2ContextMenuRequestedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventhandler)** () `ICoreWebView2ExperimentalContextMenuRequestedEventHandler`

* **[ICoreWebView2Deferral](/microsoft-edge/webview2/reference/win32/icorewebview2deferral)**

* [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_item_kind)
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU`
   
* [COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_target_kind)

---


<!-- ====================================================================== -->
## <a name="example-adding-a-custom-context-menu"></a>示例：添加自定义上下文菜单

以下示例以 Win32/WPF 上下文菜单格式呈现 WebView2 上下文菜单。


# [<a name="c"></a>C#](#tab/csharp)

```csharp
webView.CoreWebView2.ContextMenuRequested += delegate (object sender, 
                                    CoreWebView2ContextMenuRequestedEventArgs args)
{
    IList<CoreWebView2ContextMenuItem> menuList = args.MenuItems;
    CoreWebView2Deferral deferral = args.GetDeferral();
    args.Handled = true;
    ContextMenu cm = new ContextMenu();
    cm.Closed += (s, ex) => deferral.Complete();
    PopulateContextMenu(args, menuList, cm);
    cm.IsOpen = true;
};
void PopulateContextMenu(CoreWebView2ContextMenuRequestedEventArgs args, 
IList<CoreWebView2ContextMenuItem> menuList, ItemsControl cm)
{
    for (int i = 0; i < menuList.Count; i++)
    {
        CoreWebView2ContextMenuItem current = menuList[i];
        if (current.Kind == CoreWebView2ContextMenuItemKind.Separator)
        {
            Separator sep = new Separator();
            cm.Items.Add(sep);
            continue;
        }
        MenuItem newItem = new MenuItem();
        // The accessibility key is the key after the & in the label
        // Replace with '_' so it is underlined in the label
        newItem.Header = current.Label.Replace('&', '_');
        newItem.InputGestureText = current.ShortcutKeyDescription;
        newItem.IsEnabled = current.IsEnabled;
        if (current.Kind == CoreWebView2ContextMenuItemKind.Submenu)
        {
            PopulateContextMenu(args, current.Children, newItem);
        }
        else
        {
            if (current.Kind == CoreWebView2ContextMenuItemKind.CheckBox
            || current.Kind == CoreWebView2ContextMenuItemKind.Radio)
            {
                newItem.IsCheckable = true;
                newItem.IsChecked = current.IsChecked;
            }

            newItem.Click += (s, ex) =>
            {
                args.SelectedCommandId = current.CommandId;
            };
        }
        cm.Items.Add(newItem);
    }
}
```

# [<a name="c"></a>C++](#tab/cpp)

```cpp
m_webView2_4 = m_webView.try_query<ICoreWebView2_4>();
webview2_4->add_ContextMenuRequested(
    Callback<ICoreWebView2ContextMenuRequestedEventHandler>(
        [this](
            ICoreWebView2* sender,
            ICoreWebView2ContextMenuRequestedEventArgs* args)
        {
            auto showMenu = [this, args = 
            wil::com_ptr<ICoreWebView2ContextMenuRequestedEventArgs>(args)]
            {
                wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items;
                CHECK_FAILURE(args->get_MenuItems(&items));
                CHECK_FAILURE(args->put_Handled(true));
                HMENU hPopupMenu = CHECK_POINTER(CreatePopupMenu());
                AddMenuItems(hPopupMenu, items);
                HWND hWnd;
                m_controller->get_ParentWindow(&hWnd);
                POINT locationInControlCoordinates;
                POINT locationInScreenCoordinates;
                CHECK_FAILURE(args->get_Location(&locationInControlCoordinates));
                // get_Location returns coordinates in relation to upper left Bounds
                // of the WebView2.Controller. Will need to convert to Screen 
                // coordinates to display the popup menu in the correct location.
                ConvertToScreenCoordinates(locationInControlCoordinates, 
                                           locationInScreenCoordinates);
                UINT32 selectedCommandId = TrackPopupMenu(
                                       hPopupMenu, 
                                       TPM_TOPALIGN | TPM_LEFTALIGN | TPM_RETURNCMD,
                                       locationInScreenCoordinates.x, 
                                       locationInScreenCoordinates.y, 
                                       0, 
                                       hWnd, 
                                       NULL);
                if (selectedCommandId != 0) {
                    CHECK_FAILURE(args->put_SelectedCommandId(selectedCommandId));
                }
            };
            wil::com_ptr<ICoreWebView2Deferral> deferral;
            CHECK_FAILURE(args->GetDeferral(&deferral));
            m_sampleWindow->RunAsync([deferral, showMenu]() {
                showMenu();
                CHECK_FAILURE(deferral->Complete());
            });
            return S_OK;
        }).Get(),
    &m_contextMenuRequestedToken);

void ContextMenu::AddMenuItems(
    HMENU hPopupMenu, wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items)
    {
        wil::com_ptr<ICoreWebView2ContextMenuItem> current;
        UINT32 itemsCount;

        CHECK_FAILURE(items->get_Count(&itemsCount));
        for (UINT32 i = 0; i < itemsCount; i++)
        {
            CHECK_FAILURE(items->GetValueAtIndex(i, &current));
            COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND kind;
            CHECK_FAILURE(current->get_Kind(&kind));
            wil::unique_cotaskmem_string label;
            CHECK_FAILURE(current->get_Label(&label));
            std::wstring labelString = label.get();
            wil::unique_cotaskmem_string shortcut;
            CHECK_FAILURE(current->get_ShortcutKeyDescription(&shortcut));
            std::wstring shortcutString = shortcut.get();
            if (!shortcutString.empty())
            {
                labelString = labelString + L"\t" + shortcutString;
            }
            BOOL isEnabled;
            CHECK_FAILURE(current->get_IsEnabled(&isEnabled));
            BOOL isChecked;
            CHECK_FAILURE(current->get_IsChecked(&isChecked));
            INT32 commandId;
            CHECK_FAILURE(current->get_CommandId(&commandId));
            if (kind == COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR)
            {
                CHECK_BOOL(AppendMenu(hPopupMenu, MF_SEPARATOR, 0, nullptr));
            }
            else if (kind == COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU)
            {
                HMENU newMenu = CHECK_POINTER(CreateMenu());
                wil::com_ptr<ICoreWebView2ContextMenuItemCollection> submenuItems;
                CHECK_FAILURE(current->get_Children(&submenuItems));
                BOOL isEnabled;
                CHECK_FAILURE(current->get_IsEnabled(&isEnabled));
                if (isEnabled)
                {
                    AddMenuItems(newMenu, submenuItems);
                    CHECK_BOOL(AppendMenu(hPopupMenu,
                                          MF_POPUP, 
                                          (UINT_PTR)newMenu, 
                                          labelString.c_str()));
                }
                else
                {
                    CHECK_BOOL(AppendMenu(hPopupMenu, 
                                          MF_POPUP | MF_GRAYED, 
                                          (UINT_PTR)newMenu, 
                                          labelString.c_str()));
                }
            }
            else if (
                kind == COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_CHECK_BOX ||
                kind == COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_RADIO)
            {
                if (isEnabled)
                {
                    if (isChecked)
                    {
                        CHECK_BOOL(AppendMenu(hPopupMenu, 
                                              MF_CHECKED | MF_STRING, 
                                              commandId, 
                                              labelString.c_str()));
                    }
                    else
                    {
                        CHECK_BOOL(AppendMenu(hPopupMenu, 
                                              MF_BYPOSITION | MF_STRING,
                                              commandId, 
                                              labelString.c_str()));
                    }
                }
                else
                {
                    if (isChecked)
                    {
                        CHECK_BOOL(AppendMenu(hPopupMenu, 
                                              MF_CHECKED | MF_GRAYED | MF_STRING, 
                                              commandId, 
                                              labelString.c_str()));
                    }
                    else
                    {
                        CHECK_BOOL(AppendMenu(hPopupMenu, 
                                              MF_GRAYED | MF_STRING, 
                                              commandId, 
                                              labelString.c_str()));
                    }
                }
            }
            else if (kind == COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND)
            {
                if (isEnabled)
                {
                    CHECK_BOOL(AppendMenu(hPopupMenu,
                                          MF_BYPOSITION | MF_STRING, 
                                          commandId, 
                                          labelString.c_str()));
                }
                else
                {
                    CHECK_BOOL(AppendMenu(hPopupMenu, 
                                          MF_GRAYED | MF_STRING, 
                                          commandId, 
                                          labelString.c_str()));
                }
            }
        }
    }
```

---


<!-- ====================================================================== -->
## <a name="adding-menu-items-to-a-context-menu"></a>向上下文菜单添加菜单项

您可以：

*  将默认菜单项添加到自定义上下文菜单，如上面"添加自定义上下文菜单"中所示。

*  将自定义菜单项添加到默认上下文菜单，如"向默认上下文菜单添加自定义菜单项"中所示。


### <a name="adding-custom-menu-items-to-a-default-context-menu"></a>将自定义菜单项添加到默认上下文菜单

若要将自定义菜单项添加到默认上下文菜单，请使用以下 API 项。


# [<a name="c"></a>C#](#tab/csharp)

* **[CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)**
   * [ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)

* **[CoreWebView2ContextMenuItem 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem)**
   * [CustomItemSelected 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.customitemselected)

* **[CoreWebView2ContextMenuItemKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitemkind)**
   * `Command`

* **[CoreWebView2ContextMenuRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs)**
   * [ContextMenuTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.contextmenutarget)
   * `ContextMenuTarget.PageUri`

* **[CoreWebView2ContextMenuTarget 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutarget)**
   * [CoreWebView2ContextMenuTarget.PageUri 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutarget.pageuri)

* **[CoreWebView2Environment 类](/dotnet/api/microsoft.web.webview2.core.corewebview2environment)**
   * [CreateContextMenuItem 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcontextmenuitem)


# [<a name="c"></a>C++](#tab/cpp)

* **[ICoreWebView2Experimental6](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6)**
   * [add_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#add_contextmenurequested)

* **[ICoreWebView2ContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem)** () `ICoreWebView2ExperimentalContextMenuItem`
   * [add_CustomItemSelected](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#add_customitemselected)

* **[ICoreWebView2ContextMenuItemCollection](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection)** () `ICoreWebView2ExperimentalContextMenuItemCollection`

* **[ICoreWebView2ContextMenuRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs)** () `ICoreWebView2ExperimentalContextMenuRequestedEventArgs`
   * [get_MenuItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_menuitems)

* **[ICoreWebView2ContextMenuRequestedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventhandler)** () `ICoreWebView2ExperimentalContextMenuRequestedEventHandler`

* **[ICoreWebView2CustomItemSelectedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcustomitemselectedeventhandler)** (`ICoreWebView2ExperimentalCustomItemSelectedEventHandler`) 

* **[ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment)**
   * [CreateContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment6#createcontextmenuitem)

* [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_item_kind)
   * COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND

---

<!-- ====================================================================== -->
## <a name="example-adding-custom-menu-items-to-a-default-context-menu"></a>示例：将自定义菜单项添加到默认上下文菜单

以下示例向 WebView2 上下文菜单添加"显示页面 **Uri** "命令。


# [<a name="c"></a>C#](#tab/csharp)

```csharp
webView.CoreWebView2.ContextMenuRequested += delegate (object sender, 
                                    CoreWebView2ContextMenuRequestedEventArgs args)
{
    // add new item to end of collection
    CoreWebView2ContextMenuItem newItem = 
                        webView.CoreWebView2.Environment.CreateContextMenuItem(
        "Display Page Uri", null, CoreWebView2ContextMenuItemKind.Command);
        newItem.CustomItemSelected += delegate (object send, Object ex)
        {
            string pageUri = args.ContextMenuTarget.PageUri;
            System.Threading.SynchronizationContext.Current.Post((_) =>
            {
                MessageBox.Show(pageUri, "Page Uri", MessageBoxButton.OK);
            }, null);
        }
    menuList.Insert(menuList.Count, newItem);
};
``` 


# [<a name="c"></a>C++](#tab/cpp)

```cpp
m_webView2_4 = m_webView.try_query<ICoreWebView2_4>();
webview2_4->add_ContextMenuRequested(
    Callback<ICoreWebView2ContextMenuRequestedEventHandler>(
        [this](
            ICoreWebView2* sender,
            ICoreWebView2ContextMenuRequestedEventArgs* args)
        {
            wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items;
            CHECK_FAILURE(args->get_MenuItems(&items));
            UINT32 itemsCount;
            CHECK_FAILURE(items->get_Count(&itemsCount));
            // Adding a custom context menu item for the page that will display the page's URI.
            wil::com_ptr<ICoreWebView2Environment5> webviewEnvironment;
            CHECK_FAILURE(m_appWindow->GetWebViewEnvironment()->QueryInterface(
                IID_PPV_ARGS(&webviewEnvironment)));
            wil::com_ptr<ICoreWebView2ContextMenuItem> newMenuItem;
            CHECK_FAILURE(webviewEnvironment->CreateContextMenuItem(
                    L"Display page Uri", 
                    nullptr, 
                    COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND, &newMenuItem));
            newMenuItem->add_CustomItemSelected(
                        Callback<ICoreWebView2CustomItemSelectedEventHandler>(
                [this, info](
                    ICoreWebView2* sender,
                    IUnknown* args)
                    {
                        wil::unique_cotaskmem_string pageUri;
                        CHECK_FAILURE(info->get_PageUri(&pageUri));
                        std::wstring pageString = pageUri.get();
                        m_appWindow->RunAsync([this, pageString]()
                        {
                            MessageBox(
                                m_appWindow->GetMainWindow(), pageString.c_str(),
                                L"Display Page Uri", MB_OK);
                        });
                        return S_OK;
                    })
                    .Get(),
                nullptr);
            CHECK_FAILURE(items->InsertValueAtIndex(itemsCount, newMenuItem.get()));
            return S_OK;
        })
        .Get(),
    &m_contextMenuRequestedToken);
```

---


<!-- ====================================================================== -->
## <a name="removing-menu-items-from-a-default-context-menu"></a>从默认上下文菜单中删除菜单项

可以从默认上下文菜单中删除默认或自定义菜单项。


# [<a name="c"></a>C#](#tab/csharp)

* **[CoreWebView2ContextMenuItem 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem)**
   * [Name 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.name)

* [ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)

* **[CoreWebView2ContextMenuRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs)**
   * [ContextMenuTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.contextmenutarget)
   * [MenuItems 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.menuitems)

* **[CoreWebView2ContextMenuTargetKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutargetkind)**
   * `Image`


# [<a name="c"></a>C++](#tab/cpp)

* [COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_target_kind)
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE`

* **[ICoreWebView2_4](/microsoft-edge/webview2/reference/win32/icorewebview2_4)**

* **[ICoreWebView2ContextMenuRequestedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventhandler)** () `ICoreWebView2ExperimentalContextMenuRequestedEventHandler`

* **[ICoreWebView2ContextMenuRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs)** () `ICoreWebView2ExperimentalContextMenuRequestedEventArgs`
   * [get_MenuItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_menuitems)
   * [get_ContextMenuTarget](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_contextmenutarget)

* **[ICoreWebView2ContextMenuItemCollection](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection)** () `ICoreWebView2ExperimentalContextMenuItemCollection`
   * [get_Count](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#get_count)
   * [GetValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#getvalueatindex)
   * [RemoveValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#removevalueatindex)

* **[ICoreWebView2ContextMenuTarget](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenutarget)** () `ICoreWebView2ExperimentalContextMenuTarget`
   * [get_kind](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenutarget#get_kind)

* **[ICoreWebView2ContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem)** () `ICoreWebView2ExperimentalContextMenuItem`
   * [get_Name](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_name)

---

<!-- ====================================================================== -->
## <a name="example-removing-menu-items-from-a-default-context-menu"></a>示例：从默认上下文菜单中删除菜单项

以下示例从 WebView2 上下文 **菜单中删除"** 将图像另存为"命令。


# [<a name="c"></a>C#](#tab/csharp)

```csharp
webView.CoreWebView2.ContextMenuRequested += delegate (object sender, 
                                    CoreWebView2ContextMenuRequestedEventArgs args)
{
    IList<CoreWebView2ContextMenuItem> menuList = args.MenuItems;
    CoreWebView2ContextMenuTargetKind context = args.ContextMenuTarget.Kind;
    if (context == CoreWebView2ContextMenuTargetKind.Image)
    {
        for (int index = 0; index < menuList.Count; index++)
        {
            if (menuList[index].Name == "saveImageAs")
            {
                menuList.RemoveAt(index);
                break;
            }
        }
    }
};
``` 


# [<a name="c"></a>C++](#tab/cpp)

```cpp
m_webView2_4 = m_webView.try_query<ICoreWebView2_4>();
webview2_4->add_ContextMenuRequested(
    Callback<ICoreWebView2ContextMenuRequestedEventHandler>(
        [this](
            ICoreWebView2* sender,
            ICoreWebView2ContextMenuRequestedEventArgs* args)
        {
            wil::com_ptr<ICoreWebView2ContextMenuItemCollection> items;
            CHECK_FAILURE(args->get_MenuItems(&items));
            wil::com_ptr<ICoreWebView2ContextMenuTarget> target;
            CHECK_FAILURE(args->get_ContextMenuTarget(&target));
            COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND context_kind;
            CHECK_FAILURE(target->get_Kind(&context_kind));
            UINT32 itemsCount;
            CHECK_FAILURE(items->get_Count(&itemsCount));
            // Removing the 'Save image as' context menu item for image context selections.
            if (context_kind == COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE)
            {
                wil::com_ptr<ICoreWebView2ContextMenuItem> current;
                for(UINT32 i = 0; i < itemsCount; i++) 
                {
                    CHECK_FAILURE(items->GetValueAtIndex(i, &current));
                    wil::unique_cotaskmem_string name;
                    CHECK_FAILURE(current->get_Name(&name));
                    if (wcsmp(name.get(), L"saveImageAs") == 0)
                    {
                        CHECK_FAILURE(items->RemoveValueAtIndex(i));
                        break;
                    }
                }
            return S_OK;
        })
        .Get(),
    &m_contextMenuRequestedToken);
```

---

<!-- ====================================================================== -->
## <a name="detecting-when-the-user-requests-a-context-menu"></a>检测用户何时请求上下文菜单

本节介绍如何检测用户何时请求打开上下文菜单。  自定义或默认上下文菜单是相同的。

当用户请求打开上下文菜单 (例如右键单击) ，你的应用需要侦听 `ContextMenuRequested` 事件。

当你的应用检测到此事件时，你的应用应执行以下某种组合：
*  将自定义菜单项添加到默认上下文菜单中。
*  从默认上下文菜单中删除自定义菜单项。
*  打开自定义上下文菜单。

该事件 `ContextMenuRequested` 指示用户请求打开上下文菜单。

WebView2 控件引发此事件以指示用户请求在 WebView2 控件中打开上下文菜单，例如通过右键单击。

WebView2 控件仅在 `ContextMenuRequested` 当前网页允许显示上下文菜单时引发事件;即，如果 `AreDefaultContextMenusEnabled` 属性为 `true`。

[CoreWebView2ContextMenuRequestedEventArgs](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs) 包含以下信息： 

*  用于填充自定义上下文 `ContextMenuItem` 菜单的对象的有序列表。  已排序列表包括以下内容：
   *  菜单项的内部名称。
   *  在 UI 中向用户显示的菜单项的 UI 标签。
   *  菜单项类型。
   *  键盘快捷方式 Description（如果有）例如 `Alt+C`。
   *  自定义菜单项的其他任何属性。

*  请求上下文菜单的坐标，以便你的应用可以检测用户右键单击的 UI 项。  坐标相对于 WebView2 控件的左上角进行定义。

*  将包含所选上下文类型的选择对象<!--such as?--> 和相应的上下文菜单参数数据。<!--what sort of param data - which piece of info that's sent, tells which menu item, from the ordered list of menu items, the user selected?-->

当用户在上下文菜单上选择自定义菜单项时，WebView2 控件将触发事件 `CustomItemSelected` 。

当主机应用向 WebView2 指示用户选择了上下文菜单上的菜单项时，WebView2 将运行选定的命令。


# [<a name="c"></a>C#](#tab/csharp)

* **[CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)**
   * [ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)

* **[CoreWebView2Settings 类](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)**
   * [AreDefaultContextMenusEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.aredefaultcontextmenusenabled)


# [<a name="c"></a>C++](#tab/cpp)

* **[ICoreWebView2Experimental6](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6)**
   * [add_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#add_contextmenurequested)
   * [remove_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#remove_contextmenurequested)

* **[ICoreWebView2Settings](/microsoft-edge/webview2/reference/win32/icorewebview2settings)**
   * [get_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_aredefaultcontextmenusenabled)
   * [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_aredefaultcontextmenusenabled)

---


<!-- ====================================================================== -->
## <a name="detecting-when-the-user-selects-a-custom-menu-item"></a>检测用户何时选择自定义菜单项

主机应用可以处理用户选择的菜单项，或者你的应用可以将该菜单项返回到 WebView2 控件以处理用户选择的菜单项。

主机应用应侦听事件 `CustomItemSelected` ，该事件在用户选择默认或自定义上下文菜单上的自定义菜单项时引发。

WebView2 控件引发此事件以指示用户选择了你的应用添加到上下文菜单中的自定义菜单项。

如果用户选择自定义 `CustomMenuItemSelected` 菜单项，则事件在选择的上下文菜单项对象上引发，在这些情况下：

*  应用添加自定义菜单项，但将上下文菜单 UI 延迟到 WebView 平台。

*  应用添加自定义菜单项，显示自定义 UI `SelectedCommandId` ，并将属性设置为自定义菜单项的 ID。


<!-- ====================================================================== -->
## <a name="reporting-a-selected-command-menu-item-to-webview2"></a>向 WebView2 报告选定的命令菜单项

当用户选择 WebView2 上下文菜单命令 (自定义上下文菜单) 中的默认菜单项时，主机应用可以选择向 WebView2 报告该选择，以便 WebView2 将调用该命令。


# [<a name="c"></a>C#](#tab/csharp)

* **[CoreWebView2ContextMenuItemKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitemkind)**
   * `CheckBox`
   * `Command`
   * `Radio`
   * `Separator`
   * `Submenu`


# [<a name="c"></a>C++](#tab/cpp)

* [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_item_kind)
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_CHECK_BOX`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_RADIO`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU`

---

<!-- -------------------------------------------------- -->
### <a name="custom-menu-items"></a>自定义菜单项

如果主机应用将自定义菜单项报告 `CustomMenuItemSelected` 为选定菜单项，将为自定义菜单项触发该事件。


<!-- ====================================================================== -->
## <a name="disabling-context-menus"></a>禁用上下文菜单

属性 `AreDefaultContextMenusEnabled` 控制是否可以打开任何上下文菜单。  如果将 WebView2 `AreDefaultContextMenusEnabled` 设置为 `False`， `ContextMenuRequested` 则禁用上下文菜单，并且不会引发事件，例如当用户右键单击时。


# [<a name="c"></a>C#](#tab/csharp)

* **[CoreWebView2Settings 类](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)**
   * [AreDefaultContextMenusEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.aredefaultcontextmenusenabled)


# [<a name="c"></a>C++](#tab/cpp)

* **[ICoreWebView2Settings](/microsoft-edge/webview2/reference/win32/icorewebview2settings)**
   * [get_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_aredefaultcontextmenusenabled)
   * [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_aredefaultcontextmenusenabled)

---


<!-- ====================================================================== -->
## <a name="api-reference-overview"></a>API 参考概述


<!-- C# API Ref -->

# [<a name="c"></a>C#](#tab/csharp)

* **[WebView2 类](/dotnet/api/microsoft.web.webview2.wpf.webview2)**
   * [ContextMenu 属性](/dotnet/api/microsoft.web.webview2.wpf.webview2.contextmenu)

* **[CoreWebView2 类](/dotnet/api/microsoft.web.webview2.core.corewebview2)**
   * [ContextMenuRequested 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2.contextmenurequested)

* **[CoreWebView2ContextMenuItem 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem)**
   * [Children 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.children)
   * [CommandId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.commandid)
   * [Icon 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.icon)
   * [IsChecked 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.ischecked)
   * [IsEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.isenabled)
   * [Kind 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.kind)
   * [Label 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.label)
   * [Name 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.name)
   * [ShortcutKeyDescription 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.shortcutkeydescription)
   * [CustomItemSelected 事件](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitem.customitemselected)

* **[CoreWebView2ContextMenuItemKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenuitemkind)**
   * `CheckBox`
   * `Command`
   * `Radio`
   * `Separator`
   * `Submenu`

* **[CoreWebView2ContextMenuRequestedEventArgs 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs)**
   * [ContextMenuTarget 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.contextmenutarget)
   * [Handled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.handled)
   * [Location 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.location)
   * [MenuItems 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.menuitems)
   * [SelectedCommandId 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.selectedcommandid)
   * [GetDeferral 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenurequestedeventargs.getdeferral)

* **[CoreWebView2ContextMenuTarget 类](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutarget)**
   * [CoreWebView2ContextMenuTarget.PageUri 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutarget.pageuri)
   <!--13 properties-->

* **[CoreWebView2ContextMenuTargetKind 枚举](/dotnet/api/microsoft.web.webview2.core.corewebview2contextmenutargetkind)**
   * `Audio`
   * `Image`
   * `Page`
   * `SelectedText`
   * `Video`

* **[CoreWebView2Deferral 类](/dotnet/api/microsoft.web.webview2.core.corewebview2deferral)**
   * [Complete 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2deferral.complete)

* **[CoreWebView2Environment 类](/dotnet/api/microsoft.web.webview2.core.corewebview2environment)**
   * [CreateContextMenuItem 方法](/dotnet/api/microsoft.web.webview2.core.corewebview2environment.createcontextmenuitem)

* **[CoreWebView2Settings 类](/dotnet/api/microsoft.web.webview2.core.corewebview2settings)**
   * [AreDefaultContextMenusEnabled 属性](/dotnet/api/microsoft.web.webview2.core.corewebview2settings.aredefaultcontextmenusenabled)


<!-- ---------------------------------------------------------------------- -->
<!-- C++ API Ref -->

# [<a name="c"></a>C++](#tab/cpp)

* **[ICoreWebView2](/microsoft-edge/webview2/reference/win32/icorewebview2)**
* **[ICoreWebView2_4](/microsoft-edge/webview2/reference/win32/icorewebview2_4)**
* **[ICoreWebView2Experimental6](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6)**
   * [add_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#add_contextmenurequested)
   * [remove_ContextMenuRequested](/microsoft-edge/webview2/reference/win32/icorewebview2experimental6#remove_contextmenurequested)

* **[ICoreWebView2ContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem)** () `ICoreWebView2ExperimentalContextMenuItem`
   * [add_CustomItemSelected](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#add_customitemselected)
   * [get_Children](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_children)
   * [get_CommandId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_commandid)
   * [get_Icon](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_icon)
   * [get_IsChecked](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_ischecked)
   * [get_IsEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_isenabled)
   * [get_Kind](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_kind)
   * [get_Label](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_label)
   * [get_Name](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_name)
   * [get_ShortcutKeyDescription](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#get_shortcutkeydescription)
   * [put_IsChecked](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#put_ischecked)
   * [put_IsEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#put_isenabled)
   * [remove_CustomItemSelected](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitem#remove_customitemselected)
   
* **[ICoreWebView2ContextMenuItemCollection](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection)** () `ICoreWebView2ExperimentalContextMenuItemCollection`
   * [get_Count](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#get_count)
   * [GetValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#getvalueatindex)
   * [InsertValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#insertvalueatindex)
   * [RemoveValueAtIndex](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenuitemcollection#removevalueatindex)

* **[ICoreWebView2ContextMenuRequestedEventArgs](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs)** () `ICoreWebView2ExperimentalContextMenuRequestedEventArgs`
   * [get_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_handled)
   * [get_Location](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_location)
   * [get_MenuItems](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_menuitems)
   * [get_SelectedCommandId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_selectedcommandid)
   * [get_ContextMenuTarget](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#get_contextmenutarget)
   * [GetDeferral](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#getdeferral)
   * [put_Handled](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#put_handled)
   * [put_SelectedCommandId](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventargs#put_selectedcommandid)

* **[ICoreWebView2ContextMenuRequestedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventhandler)** () `ICoreWebView2ExperimentalContextMenuRequestedEventHandler`
   * [调用](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenurequestedeventhandler#invoke)

* **[ICoreWebView2ContextMenuTarget](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenutarget)** () `ICoreWebView2ExperimentalContextMenuTarget`
   * [get_kind](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcontextmenutarget#get_kind)

* **[ICoreWebView2CustomItemSelectedEventHandler](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcustomitemselectedeventhandler)** (`ICoreWebView2ExperimentalCustomItemSelectedEventHandler`) 

* **[ICoreWebView2Deferral](/microsoft-edge/webview2/reference/win32/icorewebview2deferral)**
   * [完成](/microsoft-edge/webview2/reference/win32/icorewebview2deferral#complete)

* **[ICoreWebView2Environment](/microsoft-edge/webview2/reference/win32/icorewebview2environment)**
   * [CreateContextMenuItem](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalenvironment6#createcontextmenuitem)

* **[ICoreWebView2Settings](/microsoft-edge/webview2/reference/win32/icorewebview2settings)**
   * [get_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#get_aredefaultcontextmenusenabled)
   * [put_AreDefaultContextMenusEnabled](/microsoft-edge/webview2/reference/win32/icorewebview2settings#put_aredefaultcontextmenusenabled)
   
* [COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_item_kind)
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_COMMAND`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_CHECK_BOX`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_RADIO`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SEPARATOR`
   * `COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND_SUBMENU`

* [COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND枚举](/microsoft-edge/webview2/reference/win32/icorewebview2experimentalcompositioncontroller4#corewebview2_context_menu_target_kind)
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_PAGE`
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_IMAGE`
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_SELECTED_TEXT`
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_AUDIO`
   * `COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND_VIDEO`

---


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

* [WebView2Samples 存储库](https://github.com/MicrosoftEdge/WebView2Samples)

<!-- spec: https://github.com/MicrosoftEdge/WebView2Feedback/blob/master/specs/ContextMenuRequested.md -->
