---
title: DevTools (Microsoft Edge 95) 中的新增功能
description: 现在，CSS 样式编辑器中的更改显示在 Visual Studio Code 内的 CSS 文件中。  所有控制台错误和警告现在都包含一个搜索 Web 图标。  改进了用于定义用户代理客户端提示的键盘访问。  改进了控制台中分组消息的筛选。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/20/2021
ms.openlocfilehash: 40e37908121853dc58b6eb5eeb4bc7a9b08d0fcb
ms.sourcegitcommit: 6f5fd86f5c5d9f200fb83defaec955dae438169d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2022
ms.locfileid: "12631189"
---
# <a name="whats-new-in-devtools-microsoft-edge-95"></a>DevTools (Microsoft Edge 95)中的新增功能

[!INCLUDE [Microsoft Edge team note for top of What's New](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="sync-live-changes-from-the-styles-tool-in-the-visual-studio-code-extension"></a>从 Visual Studio Code 扩展中的样式工具同步实时更改

<!-- Title: CSS Mirror Editing in Visual Studio Code -->
<!-- Subtitle: Changes in the CSS Styles editor now show up in your CSS files inside Visual Studio Code. -->

现在，[适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)具有名为 **CSS 镜像编辑**的试验功能。  使用此功能，可以使用**样式**工具来调整 CSS，并将所应用的更改自动添加到 Visual Studio Code 编辑器中的 CSS 源文件中。  可以切换打开和关闭此功能。

有关详细信息，请参阅[通过使用 CSS 镜像编辑从样式工具同步实时更改](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing)。

要提供反馈，请在 Visual Studio Code 的“**活动栏**”中，单击“**Microsoft Edge 工具**”，然后在“**CSS 镜像编辑**”部分中，单击“**在此处留下反馈**”链接。

![现在，CSS 样式编辑器中的更改显示在 Visual Studio Code 内的 CSS 文件中。](../../media/2021/10/css-mirror-editing-button.msft.png)


<!-- ====================================================================== -->
## <a name="all-error-and-warning-messages-in-the-console-now-have-a-search-web-icon"></a>控制台中的所有错误和警告消息现在都包含一个搜索 Web 图标

<!-- Title: All console errors and warnings now have a Search Web icon -->
<!-- Subtitle: You can now search for any of your console errors and warnings right from DevTools. -->

现在，**在 Web 上搜索此消息**图标可用于**控制台**中的所有错误和警告。  以前，此图标仅针对一些常见错误和警告出现。  现在，图标已添加到其他错误和警告上。  单击“**在 Web 上搜索此消息**”图标以使用相关错误或警告字符串搜索 Web。

有关详细信息，请参阅[在 Web 上搜索控制台错误](../09/devtools.md#search-for-console-errors-on-the-web)。
<!-- todo: cover in regular doc -->

![现在，所有控制台中的错误和警告消息现在都具有搜索 Web 图标。](../../media/2021/10/console-message-search-web-button.png)

另请参阅：
* [在 Web 中搜索控制台错误消息字符串](../../../console/index.md#search-the-web-for-a-console-error-message-string) （ _在控制台概述_中）。


<!-- ====================================================================== -->
## <a name="improved-keyboard-access-for-defining-user-agent-client-hints"></a>改进了用于定义用户代理客户端提示的键盘访问

<!-- Title: Improved keyboard access when navigating to User agent client hints in Settings -->
<!-- Subtitle: When adding a custom device to emulate in DevTools, you can now expand the User agent client hints section more easily. -->

从 [Microsoft Edge 版本 92](../05/devtools.md#user-agent-client-hints-for-devices-in-the-network-conditions-tab)开始，可以指定用户代理客户端提示。  可以在以下两个位置之一指定用户代理客户端提示：

*  [在网络条件工具中定义用户代理字符串时](../../../device-mode/override-user-agent.md)。
*  [在“设置”中添加自定义设备以进行模拟时](../../../device-mode/index.md#add-a-custom-mobile-device)。

在版本 95 之前的 Microsoft Edge 中，当从“**设置**”的“**设备**”部分中添加自定义设备进行模拟时，使用键盘选择“**用户代理提示**”按钮会导致激活不正确的 UI 项。  此操作选择了“**添加**”按钮，而不是展开供你填写的“**用户代理提示**”部分。  使用“**用户代理客户端提示**”部分中的空字段，可立即添加你要定义的设备。

在 Microsoft Edge 版本 95 中，此问题已得到修复。  现在，通过使用键盘选择“**用户代理客户端提示**”按钮将展开一个窗体，可在其中为自定义设备指定客户端提示。

要了解有关用户代理客户端提示的详细信息，请参阅[从网站检测 Microsoft Edge](../../../../web-platform/user-agent-guidance.md#user-agent-client-hints)。

![设置>设备>设置User-Agent客户端提示。](../../media/2021/10/keyboard-define-ua-client-hints.png)

要在 Chromium 开放源代码项目中查看此功能的历史记录，请参阅[问题 1243827：用户代理客户端提示窗体辅助功能](https://bugs.chromium.org/p/chromium/issues/detail?id=1243827)。


<!-- ====================================================================== -->
## <a name="console-filters-now-display-grouped-messages-if-the-filter-matches-the-group-title"></a>如果筛选器与组标题匹配，则控制台筛选器现在会显示分组消息

<!-- Title: Improved filtering for grouped messages in the Console -->
<!-- Subtitle: Filters in the Console is now more intuitive, displaying grouped messages only when the filter matches the group label. -->

可以使用 `console.group()` 标记一组消息，并为控制台消息提供一些组织。  在早期版本的 Microsoft Edge 中，尝试在控制台中筛选分组消息时会出现一些问题。  在筛选到组标签时，控制台不会显示组内的单个消息。  此外，即使标签与筛选器不匹配，筛选也不会隐藏组标签。

在 Microsoft Edge 版本 95 中，这些问题已得到修复。  现在，筛选到标签将显示组标签和组内的单个消息。  当筛选器与组标签不匹配时，将隐藏整个组。

当筛选器字符串与组标签匹配时，将显示该组及其成员：

![当筛选器字符串与组标签匹配时，将显示该组及其成员。](../../media/2021/10/filter-matches-group-label.png)

当筛选器字符串与组标签不匹配时，不会显示该组及其成员：

![当筛选器字符串与组标签不匹配时，不会显示该组及其成员。](../../media/2021/10/filter-matches-group-label-asdf.png)

另请参阅：
* _控制台对象 API 参考_中的[组](../../../../devtools-guide-chromium/console/api.md#group)。

要在 Chromium 开放源代码项目中查看此功能的历史记录，请参阅[问题 363796： ☂ 控制台筛选器不适当地隐藏分组内容，并且不隐藏组标题](https://bugs.chromium.org/p/chromium/issues/detail?id=363796)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下是 Microsoft Edge 版本 95 中可用的一些附加功能，这些功能已为开源 Chromium 项目提供。


<!-- ====================================================================== -->
## <a name="improved-the-display-of-properties"></a>改进了属性的显示

<!-- Chromium What's New entry: [Improved the display of properties](https://developer.chrome.com/blog/new-in-devtools-95/#properties) at _What's New in DevTools (Chrome 95)_. -->

DevTools 通过以下方式改进了属性的显示：
*  在**控制台**、**“源**”工具和 **“元素**”工具的“**属性**”选项卡中，始终先加粗和排序自己的属性。  （_自己的属性_是直接在对象上定义的属性。）
*  在“**属性**”窗格中平展属性显示。

例如，下面的代码片段创建具有两个自身属性的 [URL](https://developer.mozilla.org/docs/Web/API/URL) 对象`link`： `user` `access`然后更新继承属性的值： `search`

```javascript
const link = new URL('https://blogs.windows.com/msedgedev/');
link.user = { id: 1, name: 'Amelie Garner' };
link.access = 'admin';
link.search = `?access=${link.access}`;
```

在“**控制台**”中输入上述代码后，尝试记录 `link`。  现在，自己的属性是粗体的，并且在排序顺序中处于第一位。  通过这些更改，可以更轻松地发现自定义属性，尤其是对于 [Web API](https://developer.mozilla.org/docs/Web/API) (，例如 `URL` 具有许多继承属性的) ：

![自己的属性是粗体的，并且首先排序。](../../media/2021/10/improved-display-properties.png)

在 **“元素**”工具的“**属性**”窗格中，属性列表现在已平展，以便在调试 DOM 属性（尤其是 Web [组件](https://www.webcomponents.org/introduction)）时获得更好的体验：

![已平展的属性列表。](../../media/2021/10/flattened-list-of-properties.png)

另请参阅：
* [使用 Elements 工具检查、编辑和调试 HTML 和 CSS](../../../elements-tool/elements-tool.md)
<!-- todo: link to an Elements > Properties ui doc'n?  try FTS repo **Properties** - not really found -->

有关此功能的历史记录，请参阅 Chromium 问题 [1076820](https://crbug.com/1076820) 和 [1119900](https://crbug.com/1119900)。


<!-- ====================================================================== -->
## <a name="snippets-are-now-sorted-in-the-sources-panel"></a>现在，代码片段在“源”面板中排序

<!-- Chromium What's New entry: [Sort snippets in the Sources panel](https://developer.chrome.com/blog/new-in-devtools-95/#snippets) at _What's New in DevTools (Chrome 95)_. -->

以前，在 **“源**”工具的“代码**段**”选项卡中，代码段未排序。  代码片段现在按字母顺序排序：

![“源”面板中的已排序代码段。](../../media/2021/10/snippets-sorted-alphbetically.png)

另请参阅：
* [在任何网页上运行 JavaScript 的代码片段](../../../javascript/snippets.md)
* [Chrome 85 - DevTools 中的新增功能](https://youtu.be/NOal2gTzftI?t=176) - 视频。

有关此功能的历史记录，请参阅 Chromium 问题：[1243976](https://crbug.com/1243976)。


<!-- ====================================================================== -->
## <a name="improved-ui-for-devtools-command-menu"></a>改进了 DevTools 命令菜单的 UI

<!-- Chromium What's New entry: [Improved UI for DevTools command menu](https://developer.chrome.com/blog/new-in-devtools-95/#command-menu) at _What's New in DevTools (Chrome 95)_. -->

已增强**命令菜单**，以便更轻松地搜索文件。  在 Windows 和 Linux 或 `Command+P` macOS 中按下`P``Ctrl`+时，**命令菜单**现在以粗体显示文件名，以及指示文件类型的图标：

![命令菜单以粗体显示文件名，并显示指示文件类型的图标。](../../media/2021/10/command-menu-filenames-bold-icons.png)

另请参阅：
* [命令菜单](../../../command-menu/index.md)

有关此功能的历史记录，请参阅 Chromium 问题 [1201997](https://crbug.com/1201997)。 


<!-- ====================================================================== -->
> [!NOTE]
> 本页中“Chromium 项目公告”部分是基于 Google 根据[网站策略](https://developers.google.com/terms/site-policies)创建和共享的工作进行的修改，其使用应符合[知识共享署名 4.0 国际许可协议](https://creativecommons.org/licenses/by/4.0)中所述的条款。  Chromium 项目公告的原始页面为“[DevTools 中的最近更新 (Chrome 95)](https://developer.chrome.com/blog/new-in-devtools-95)”，作者为 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen)（Google 负责 Chrome DevTools 工作的开发人员大使）。

[![知识共享许可协议。](../../../../media/cc-logo/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
