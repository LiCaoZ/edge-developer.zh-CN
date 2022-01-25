---
title: 'DevTools (Microsoft Edge 95 中的) '
description: CSS 样式编辑器中的更改现在显示在 CSS 编辑器内的 CSS Visual Studio Code。  所有控制台错误和警告现在都有一个搜索 Web 图标。  改进了用于定义客户端提示User-Agent键盘访问。  改进了对控制台中分组邮件的筛选。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 10/20/2021
ms.openlocfilehash: 73dc6e9c7c5018be535dcf4e4a1e10ad76fc330d
ms.sourcegitcommit: e12d7e7d8b182b79cc8ce96b9889073aeaabac30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2022
ms.locfileid: "12320079"
---
# <a name="whats-new-in-devtools-microsoft-edge-95"></a>DevTools (Microsoft Edge 95 中的新增) 

此页面的顶部列出了来自开发人员工具Microsoft Edge通知，然后此页面底部介绍了来自 Chromium 项目的选定功能。  若要试用 Microsoft Edge Tools 和 Microsoft Edge DevTools 扩展中的新功能Visual Studio Code，请阅读这些通知。

若要随时了解有关开发人员工具的最新和最强大功能，请下载 [Microsoft Edge 预览频道](https://www.microsoftedgeinsider.com/download) 并 [在 Twitter 上关注 Microsoft Edge 开发人员工具团队](https://twitter.com/EdgeDevTools)。  无论你使用的是 Windows、Linux 还是 macOS，都应考虑使用 Microsoft Edge 预览频道之一作为默认开发浏览器。


<!-- ====================================================================== -->
## <a name="sync-live-changes-from-the-styles-tool-in-the-visual-studio-code-extension"></a>Sync live changes from the Styles tool in the Visual Studio Code extension

<!-- Title: CSS Mirror Editing in Visual Studio Code -->
<!-- Subtitle: Changes in the CSS Styles editor now show up in your CSS files inside Visual Studio Code. -->

当前[Microsoft Edge开发人员工具扩展Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)一个称为 **"CSS 镜像编辑"的实验**。  使用此功能，您可以使用样式工具调整**** CSS，并且您应用的更改会自动添加到 CSS Visual Studio Code文件中。  你可以打开和关闭此功能。

有关详细信息，请参阅 [Syncing live changes from the Styles tool by using CSS Mirror Editing](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing)。

若要提供反馈，Visual Studio Code活动栏中，单击"Microsoft Edge**工具**"，然后在 **"CSS 镜像**编辑"部分，单击"**此处留下的反馈"** 链接。 ****

:::image type="content" source="../../media/2021/10/css-mirror-editing-button.msft.png" alt-text="CSS 样式编辑器中的更改现在显示在 CSS 编辑器内的 CSS Visual Studio Code。" lightbox="../../media/2021/10/css-mirror-editing-button.msft.png":::


<!-- ====================================================================== -->
## <a name="all-error-and-warning-messages-in-the-console-now-have-a-search-web-icon"></a>控制台中所有错误和警告消息现在都有搜索 Web 图标

<!-- Title: All console errors and warnings now have a Search Web icon -->
<!-- Subtitle: You can now search for any of your console errors and warnings right from DevTools. -->

现在 **，"在 Web 上搜索** 此消息"图标可用于控制台中所有的错误和 **警告**。  以前，此图标只出现一些常见错误和警告。  现在，该图标已添加到剩余的错误和警告上。  单击 **Web 图标上的"搜索** 此消息"，以使用相关错误或警告字符串搜索 Web。

有关详细信息，请参阅搜索 [Web 上的控制台错误](../09/devtools.md#search-for-console-errors-on-the-web)。

:::image type="content" source="../../media/2021/10/console-message-search-web-button.png" alt-text="控制台中所有错误和警告消息现在都有一个搜索 Web 图标。" lightbox="../../media/2021/10/console-message-search-web-button.png":::


<!-- ====================================================================== -->
## <a name="improved-keyboard-access-for-defining-user-agent-client-hints"></a>改进了用于定义客户端提示User-Agent键盘访问

<!-- Title: Improved keyboard access when navigating to User agent client hints in Settings -->
<!-- Subtitle: When adding a custom device to emulate in DevTools, you can now expand the User agent client hints section more easily. -->

从[Microsoft Edge版本 92](../05/devtools.md#user-agent-client-hints-for-devices-in-the-network-conditions-tab)开始，你可以指定User-Agent提示。  可以在两User-Agent位置指定客户端提示：

*  [在网络条件工具 中定义用户代理字符串时](../../../device-mode/override-user-agent.md)。
*  [添加自定义设备以在 设置 中设置。](../../../device-mode/index.md#add-a-custom-mobile-device)

在 Microsoft Edge 95 之前的版本中，当从 设置 的"设备"部分**** 添加要模拟的自定义设备时，使用键盘**** 选择"用户代理客户端提示 **"** 按钮会导致激活不正确的 UI 项。  它选择了" **添加** "按钮，而不是展开"用户代理客户端提示"部分供你 **填写** 。  你开始定义的设备已立即添加，使用"用户代理客户端提示"部分 **中的空** 字段。

在 Microsoft Edge 95 版本中，此问题已修复。  现在 **，使用键盘** 选择"用户代理客户端提示"按钮将展开一个表单，您可以在其中为自定义设备指定客户端提示。

若要详细了解如何User-Agent提示，请参阅从Microsoft Edge[检测客户端提示](../../../../web-platform/user-agent-guidance.md#user-agent-client-hints)。

:::image type="content" source="../../media/2021/10/keyboard-define-ua-client-hints.png" alt-text="描述" lightbox="../../media/2021/10/keyboard-define-ua-client-hints.png":::

若要查看开放源代码项目中此功能的历史记录Chromium，请参阅 Issue [1243827： User agent client hints form accessibility](https://bugs.chromium.org/p/chromium/issues/detail?id=1243827)。


<!-- ====================================================================== -->
## <a name="console-filters-now-display-grouped-messages-if-the-filter-matches-the-group-title"></a>控制台筛选器现在显示分组消息（如果筛选器与组标题匹配）

<!-- Title: Improved filtering for grouped messages in the Console -->
<!-- Subtitle: Filters in the Console is now more intuitive, displaying grouped messages only when the filter matches the group label. -->

可以使用 标记 `console.group()` 一组邮件并为控制台邮件提供一些组织。  在早期版本的 Microsoft Edge，尝试在控制台中筛选分组邮件时有几个问题。  筛选到组标签时，控制台不会在组内显示单个邮件。  此外，筛选不会隐藏组标签，即使标签与筛选器不匹配。

在 Microsoft Edge 95 版本中，已修复这些问题。  筛选到标签现在将显示组标签和组内的单个邮件。  当筛选器与组标签不匹配时，将隐藏整个组。

若要了解有关 `group()` DevTools 中控制台 API 的更多信息，请导航到"控制台 API 参考[：组"。](../../../../devtools-guide-chromium/console/api.md#group)

当筛选器字符串与组标签匹配时，将显示该组及其成员：

:::image type="content" source="../../media/2021/10/filter-matches-group-label.png" alt-text="当筛选器字符串与组标签匹配时，将显示该组及其成员。" lightbox="../../media/2021/10/filter-matches-group-label.png":::

当筛选器字符串与组标签不匹配时，不显示组及其成员：

:::image type="content" source="../../media/2021/10/filter-matches-group-label-asdf.png" alt-text="当筛选器字符串与组标签不匹配时，不显示组及其成员。" lightbox="../../media/2021/10/filter-matches-group-label-asdf.png":::

若要查看 Chromium 开放源代码项目中此功能的历史记录，请参阅问题[363796： ☂ 控制台](https://bugs.chromium.org/p/chromium/issues/detail?id=363796)筛选器以不当方式隐藏分组的内容，并且不会隐藏组标题。


<!-- ====================================================================== -->
## <a name="announcements-from-the-chromium-project"></a>来自 Chromium 项目的公告

以下是版本 95 中可用的一些Microsoft Edge开放源代码管理项目Chromium功能。


<!-- ====================================================================== -->
## <a name="improved-the-display-of-properties"></a>改进了属性的显示

<!-- Chromium What's New entry: [Improved the display of properties](https://developer.chrome.com/blog/new-in-devtools-95/#properties) at _What's New In DevTools (Chrome 95)_. -->

DevTools 通过以下方式改进了属性的显示：
*  始终先在"控制台、源"面板和"属性****"窗格中**** 加粗和排序**自己的**属性。   (_一个属性_ 是直接在 object.) 
*  平展"属性"窗格中 **显示** 的属性。

例如，下面的代码段创建一个 [URL](https://developer.mozilla.org/docs/Web/API/URL) 对象，该对象具有两个自己的属性： 和 ，然后更新继承 `link` `user` `access` 属性的值 `search` 。

```javascript
const link = new URL('https://blogs.windows.com/msedgedev/');
link.user = { id: 1, name: 'Amelie Garner' };
link.access = 'admin';
link.search = `?access=${link.access}`;
```

在控制台中输入上述代码 **后，** 请尝试记录 `link` 。  自己的属性现在以粗体显示，并按排序顺序排序。  通过这些更改，可以更轻松地找到自定义属性，特别是对于 [Web](https://developer.mozilla.org/en-US/docs/Web/API) API， (具有许多继承) `URL` 的属性的网站。

:::image type="content" source="../../media/2021/10/improved-display-properties.png" alt-text="自己的属性以粗体显示，并首先排序。":::

在 **"属性** "窗格中，属性列表现已展开，以在调试 DOM 属性时获得更好的体验，特别是对于 [Web 组件](https://www.webcomponents.org/introduction)。

:::image type="content" source="../../media/2021/10/flattened-list-of-properties.png" alt-text="平展的属性列表。":::

有关此功能的历史记录，请参阅 Chromium[和](https://crbug.com/1076820)[1119900](https://crbug.com/1119900)1076820的问题。


<!-- ====================================================================== -->
## <a name="snippets-are-now-sorted-in-the-sources-panel"></a>现在，代码段在"源"面板中排序

<!-- Chromium What's New entry: [Sort snippets in the Sources panel](https://developer.chrome.com/blog/new-in-devtools-95/#snippets) at _What's New In DevTools (Chrome 95)_. -->

现在，按字母**顺序**对"源"**** 面板中"代码段"窗格中的代码段进行排序。  以前，代码段未排序。

:::image type="content" source="../../media/2021/10/snippets-sorted-alphbetically.png" alt-text="&quot;源&quot;面板中的已排序代码段。":::

有关代码段详细信息，请参阅在任何网页上运行 [JavaScript](../../../javascript/snippets.md) 的代码段并观看视频 [Chrome 85 - DevTools 中的新增功能](https://youtu.be/NOal2gTzftI?t=176)。  有关此功能的历史记录，请参阅Chromium问题[：1243976。](https://crbug.com/1243976)


<!-- ====================================================================== -->
## <a name="improved-ui-for-devtools-command-menu"></a>改进的用于 DevTools 命令菜单的 UI

<!-- Chromium What's New entry: [Improved UI for DevTools command menu](https://developer.chrome.com/blog/new-in-devtools-95/#command-menu) at _What's New In DevTools (Chrome 95)_. -->

" [命令](../../../command-menu/index.md) 菜单"已经过增强，更易于搜索文件。  当你在 Windows Linux 或 macOS 中按时，命令菜单现在以粗体显示文件名，以及一个指示文件类型的 `Ctrl` + `P` `Command+P` 图标。 ****

:::image type="content" source="../../media/2021/10/command-menu-filenames-bold-icons.png" alt-text="命令菜单，以粗体显示文件名，并包含指示文件类型的图标。":::

有关此功能的历史记录，请参阅Chromium问题[1201997。](https://crbug.com/1201997) 


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的"Chromium 项目通知"部分基于 Google 根据网站策略创建和共享的工作进行修改，根据[Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0)中所述的术语使用。 [](https://developers.google.com/terms/site-policies)  Chromium 项目中通知的原始页面是[What's New in DevTools (Chrome 95) ，](https://developer.chrome.com/blog/new-in-devtools-95)作者[Jecelyn Yeen，](https://developers.google.com/web/resources/contributors#jecelynyeen)一名开发人员支持者，他负责处理 Google 的 Chrome DevTools。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
