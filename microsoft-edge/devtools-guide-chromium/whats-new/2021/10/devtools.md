---
description: CSS 样式编辑器中的更改现在显示在 CSS 编辑器内的 CSS Visual Studio Code。  所有控制台错误和警告现在都有一个搜索 Web 图标。  改进了用于定义客户端提示User-Agent键盘访问。  改进了对控制台中分组邮件的筛选。
title: 'DevTools (Microsoft Edge 95 中的新增) '
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/20/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: b2d26ab2a8b1ca5970d48e14c1e9c4b49bfab057
ms.sourcegitcommit: 148b9b2f609eb775ed7fd71d50ac98a829ca90df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2021
ms.locfileid: "12141864"
---
# <a name="whats-new-in-devtools-microsoft-edge-95"></a>DevTools (Microsoft Edge 95 中的新增) 

[!INCLUDE [note about What's New announcements from the Microsoft Edge DevTools team](../../includes/edge-whats-new-note.md)]


<!-- ====================================================================== -->
## <a name="sync-live-changes-from-the-styles-tool-in-the-visual-studio-code-extension"></a>同步来自"样式"扩展中的"样式"Visual Studio Code更改

<!-- Title: CSS Mirror Editing in Visual Studio Code -->
<!-- Subtitle: Changes in the CSS Styles editor now show up in your CSS files inside Visual Studio Code. -->

当前[Microsoft Edge开发人员工具扩展Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)一个称为 **"CSS 镜像编辑"的实验**。  使用此功能，您可以使用样式工具调整**** CSS，并且您应用的更改会自动添加到 css 源文件中的Visual Studio Code编辑器中。  你可以打开和关闭此功能。

有关详细信息，请参阅 [Syncing live changes from the Styles tool by using CSS Mirror Editing](../../../../visual-studio-code/microsoft-edge-devtools-extension.md#syncing-live-changes-from-the-styles-tool-by-using-css-mirror-editing)。

若要提供反馈，Visual Studio Code活动栏中，单击"Microsoft Edge******工具**"，然后在 **"CSS 镜像**编辑"部分，单击"**此处留下的反馈"** 链接。

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
*  [添加自定义设备以在 设置 中模拟](../../../device-mode/index.md#add-a-custom-mobile-device)时。

在 Microsoft Edge 95 之前的版本中，当从 设置 的"设备"**** 部分添加要模拟的自定义设备时，使用**** 键盘选择"用户代理客户端提示 **"** 按钮会导致激活不正确的 UI 项。  它选择了" **添加** "按钮，而不是展开"用户代理客户端提示"部分供你 **填写** 。  你开始定义的设备已立即添加，使用"用户代理客户端提示"部分 **中的空** 字段。

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

若要查看 Chromium 开放源代码项目中此功能的历史记录，请参阅问题[363796： ☂ 控制台](https://bugs.chromium.org/p/chromium/issues/detail?id=363796)筛选器以不当方式隐藏分组内容，并且不会隐藏组标题。


<!-- ====================================================================== -->
## <a name="download-the-microsoft-edge-preview-channels"></a>下载 Microsoft Edge 预览频道

如果你使用的是 Windows、Linux 或 macOS，请考虑使用[canary preview channel of Microsoft Edge](https://www.microsoftedgeinsider.com/download)作为默认开发浏览器。  预览频道让你可以访问开发人员工具Microsoft Edge功能。


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> Chromium 项目中通知的原始页面是[What's New in DevTools (Chrome 95) ，](https://developer.chrome.com/blog/new-in-devtools-95)由[Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelynyeen) (Developer（在 Google) 上处理 Chrome DevTools 的开发人员宣传）创作。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
