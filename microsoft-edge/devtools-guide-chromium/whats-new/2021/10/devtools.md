---
title: DevTools (Microsoft Edge 95) 中的新增功能
description: 现在，CSS 样式编辑器中的更改显示在 Visual Studio Code 内的 CSS 文件中。  所有控制台错误和警告现在都包含一个搜索 Web 图标。  改进了用于定义用户代理客户端提示的键盘访问。  改进了控制台中分组消息的筛选。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/20/2021
ms.openlocfilehash: 47d16d6dc516fd182256754987e64680f94d4d8c
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12430834"
---
# <a name="whats-new-in-devtools-microsoft-edge-95"></a>DevTools (Microsoft Edge 95)中的新增功能

此页顶部列出了来自 Microsoft Edge DevTools 团队的公告，底部介绍了 Chromium 项目中的所选功能。  要试用 Microsoft Edge DevTools 和适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展中的新增功能，请阅读这些公告。

若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。  如果你使用的是 Windows、Linux 或 macOS，请考虑将 Microsoft Edge Canary 预览频道之一用作默认开发浏览器。


<!-- ====================================================================== -->
## <a name="sync-live-changes-from-the-styles-tool-in-the-visual-studio-code-extension"></a>从 Visual Studio Code 扩展中的样式工具同步实时更改

<!-- Title: CSS Mirror Editing in Visual Studio Code -->
<!-- Subtitle: Changes in the CSS Styles editor now show up in your CSS files inside Visual Studio Code. -->

现在，[适用于 Visual Studio Code 的 Microsoft Edge DevTools 扩展](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)具有名为 **CSS 镜像编辑**的试验功能。  使用此功能，可以使用**样式**工具来调整 CSS，并将所应用的更改自动添加到 Visual Studio Code 编辑器中的 CSS 源文件中。  可以切换打开和关闭此功能。

有关详细信息，请参阅[通过使用 CSS 镜像编辑从样式工具同步实时更改](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing)。

要提供反馈，请在 Visual Studio Code 的“**活动栏**”中，单击“**Microsoft Edge 工具**”，然后在“**CSS 镜像编辑**”部分中，单击“**在此处留下反馈**”链接。

:::image type="content" source="../../media/2021/10/css-mirror-editing-button.msft.png" alt-text="现在，CSS 样式编辑器中的更改显示在 Visual Studio Code 内的 CSS 文件中。" lightbox="../../media/2021/10/css-mirror-editing-button.msft.png":::


<!-- ====================================================================== -->
## <a name="all-error-and-warning-messages-in-the-console-now-have-a-search-web-icon"></a>控制台中的所有错误和警告消息现在都包含一个搜索 Web 图标

<!-- Title: All console errors and warnings now have a Search Web icon -->
<!-- Subtitle: You can now search for any of your console errors and warnings right from DevTools. -->

现在，**在 Web 上搜索此消息**图标可用于**控制台**中的所有错误和警告。  以前，此图标仅针对一些常见错误和警告出现。  现在，图标已添加到其他错误和警告上。  单击“**在 Web 上搜索此消息**”图标以使用相关错误或警告字符串搜索 Web。

有关详细信息，请参阅[在 Web 上搜索控制台错误](../09/devtools.md#search-for-console-errors-on-the-web)。

:::image type="content" source="../../media/2021/10/console-message-search-web-button.png" alt-text="现在，所有控制台中的错误和警告消息现在都具有搜索 Web 图标。" lightbox="../../media/2021/10/console-message-search-web-button.png":::


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

:::image type="content" source="../../media/2021/10/keyboard-define-ua-client-hints.png" alt-text="描述。" lightbox="../../media/2021/10/keyboard-define-ua-client-hints.png":::

要在 Chromium 开放源代码项目中查看此功能的历史记录，请参阅[问题 1243827：用户代理客户端提示窗体辅助功能](https://bugs.chromium.org/p/chromium/issues/detail?id=1243827)。


<!-- ====================================================================== -->
## <a name="console-filters-now-display-grouped-messages-if-the-filter-matches-the-group-title"></a>如果筛选器与组标题匹配，则控制台筛选器现在会显示分组消息

<!-- Title: Improved filtering for grouped messages in the Console -->
<!-- Subtitle: Filters in the Console is now more intuitive, displaying grouped messages only when the filter matches the group label. -->

可以使用 `console.group()` 标记一组消息，并为控制台消息提供一些组织。  在早期版本的 Microsoft Edge 中，尝试在控制台中筛选分组消息时会出现一些问题。  在筛选到组标签时，控制台不会显示组内的单个消息。  此外，即使标签与筛选器不匹配，筛选也不会隐藏组标签。

在 Microsoft Edge 版本 95 中，这些问题已得到修复。  现在，筛选到标签将显示组标签和组内的单个消息。  当筛选器与组标签不匹配时，将隐藏整个组。

要详细了解 DevTools 中控制台的 `group()` API，请参阅_控制台对象 API 参考_中的[组](../../../../devtools-guide-chromium/console/api.md#group)。

当筛选器字符串与组标签匹配时，将显示该组及其成员：

:::image type="content" source="../../media/2021/10/filter-matches-group-label.png" alt-text="当筛选器字符串与组标签匹配时，将显示该组及其成员。" lightbox="../../media/2021/10/filter-matches-group-label.png":::

当筛选器字符串与组标签不匹配时，不会显示该组及其成员：

:::image type="content" source="../../media/2021/10/filter-matches-group-label-asdf.png" alt-text="当筛选器字符串与组标签不匹配时，不会显示该组及其成员。" lightbox="../../media/2021/10/filter-matches-group-label-asdf.png":::

要在 Chromium 开放源代码项目中查看此功能的历史记录，请参阅[问题 363796： ☂ 控制台筛选器不适当地隐藏分组内容，并且不隐藏组标题](https://bugs.chromium.org/p/chromium/issues/detail?id=363796)。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下是 Microsoft Edge 版本 95 中可用的一些附加功能，这些功能已为开源 Chromium 项目提供。


<!-- ====================================================================== -->
## <a name="improved-the-display-of-properties"></a>改进了属性的显示

<!-- Chromium What's New entry: [Improved the display of properties](https://developer.chrome.com/blog/new-in-devtools-95/#properties) at _What's New in DevTools (Chrome 95)_. -->

DevTools 通过以下方式改进了属性的显示：
*  在“**控制台**”、“**源**”面板和“**属性**”窗格中，始终首先加粗自己的属性，并将这些属性排在前面。  （_自己的属性_是直接在对象上定义的属性。）
*  在“**属性**”窗格中平展属性显示。

例如，下面的代码片段创建了具有两个自己的属性的 [URL](https://developer.mozilla.org/docs/Web/API/URL) 对象 `link`：`user` 和 `access`，然后更新继承属性的值，`search`。

```javascript
const link = new URL('https://blogs.windows.com/msedgedev/');
link.user = { id: 1, name: 'Amelie Garner' };
link.access = 'admin';
link.search = `?access=${link.access}`;
```

在“**控制台**”中输入上述代码后，尝试记录 `link`。  现在，自己的属性是粗体的，并且在排序顺序中处于第一位。  通过这些更改，可以更轻松地发现自定义属性，尤其是对于具有许多继承属性的 [Web API](https://developer.mozilla.org/en-US/docs/Web/API)（例如 `URL`）。

:::image type="content" source="../../media/2021/10/improved-display-properties.png" alt-text="自己的属性是粗体的，并且首先排序。":::

在“**属性**”窗格中，属性列表现已平展显示，以便在调试 DOM 属性（尤其是 [Web 组件](https://www.webcomponents.org/introduction)的 DOM 属性）时获得更好的体验。

:::image type="content" source="../../media/2021/10/flattened-list-of-properties.png" alt-text="已平展的属性列表。":::

有关此功能的历史记录，请参阅 Chromium 问题 [1076820](https://crbug.com/1076820) 和 [1119900](https://crbug.com/1119900)。


<!-- ====================================================================== -->
## <a name="snippets-are-now-sorted-in-the-sources-panel"></a>现在，代码片段在“源”面板中排序

<!-- Chromium What's New entry: [Sort snippets in the Sources panel](https://developer.chrome.com/blog/new-in-devtools-95/#snippets) at _What's New in DevTools (Chrome 95)_. -->

现在，“**源**”面板中“**代码片段**”窗格中的代码片段按字母顺序排序。  以前，代码片段是不进行排序的。

:::image type="content" source="../../media/2021/10/snippets-sorted-alphbetically.png" alt-text="“源”面板中的已排序代码段。":::

有关代码片段的详细信息，请参阅[在任何网页上运行 JavaScript 的代码片段](../../../javascript/snippets.md)并观看视频 [Chrome 85 - DevTools 中的新增功能](https://youtu.be/NOal2gTzftI?t=176)。  有关此功能的历史记录，请参阅 Chromium 问题：[1243976](https://crbug.com/1243976)。


<!-- ====================================================================== -->
## <a name="improved-ui-for-devtools-command-menu"></a>改进了 DevTools 命令菜单的 UI

<!-- Chromium What's New entry: [Improved UI for DevTools command menu](https://developer.chrome.com/blog/new-in-devtools-95/#command-menu) at _What's New in DevTools (Chrome 95)_. -->

已增强[命令菜单](../../../command-menu/index.md)，以便更轻松地搜索文件。  现在，如果在 Windows 和 Linux 中按 `Ctrl`+`P`，或在 macOS 中按 `Command+P`，**命令菜单**将以粗体显示文件名，并显示指示文件类型的图标。

:::image type="content" source="../../media/2021/10/command-menu-filenames-bold-icons.png" alt-text="命令菜单以粗体显示文件名，并显示指示文件类型的图标。":::

有关此功能的历史记录，请参阅 Chromium 问题 [1201997](https://crbug.com/1201997)。 


<!-- ====================================================================== -->
> [!NOTE]
> 本页中“Chromium 项目公告”部分是基于 Google 根据[网站策略](https://developers.google.com/terms/site-policies)创建和共享的工作进行的修改，其使用应符合[知识共享署名 4.0 国际许可协议](https://creativecommons.org/licenses/by/4.0)中所述的条款。  Chromium 项目公告的原始页面为“[DevTools 中的最近更新 (Chrome 95)](https://developer.chrome.com/blog/new-in-devtools-95)”，作者为 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen)（Google 负责 Chrome DevTools 工作的开发人员大使）。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
