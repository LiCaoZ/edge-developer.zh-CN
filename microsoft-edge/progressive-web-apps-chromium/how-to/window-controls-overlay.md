---
title: 在标题栏中显示内容
description: 了解如何使用窗口控件覆盖 API 为应用使用整个窗口区域。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/02/2021
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， 窗口控件覆盖， API
ms.openlocfilehash: 4c9d8819bdf232e5f2d46475318f743fa289f9e6
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12156198"
---
# <a name="display-content-in-the-title-bar"></a>在标题栏中显示内容

虽然移动版 PWA 可以定义他们希望如何使用应用清单文件的显示属性显示，但[](https://developer.mozilla.org/docs/Web/Manifest/display)桌面 PBA 无法使用它来创建沉浸式、本机式体验。

默认情况下，应用区域从保留的标题栏区域正下方开始。

:::image type="content" source="../media/my-tracks-titlebar.png" alt-text="The default Windows app title bar shown on the My Tracks demo PWA." lightbox="../media/my-tracks-titlebar.png":::

能够显示标题栏通常位于其中的内容可以帮助 PWA 感觉更加本机。

许多桌面应用程序Visual Studio Code、Microsoft Teams或Microsoft Edge已执行过此操作。

:::image type="content" source="../media/vscode-titlebar.png" alt-text="VS Code标题栏区域中显示内容。" lightbox="../media/vscode-titlebar.png":::

窗口控件覆盖 API 允许你在应用的整个图面区域上显示 Web 内容，将关键系统所需的窗口控件移动到覆盖层，并让你的内容保持清除此覆盖。


<!-- ====================================================================== -->
## <a name="enable-the-window-controls-overlay-api-in-microsoft-edge"></a>在窗口中启用窗口控件覆盖 API Microsoft Edge

窗口控件覆盖 API 是实验性的，需要先在Microsoft Edge启用。

若要启用 API：

1.  转到 `edge://flags` Microsoft Edge。
1.  选择 **"搜索标志** "并键入"窗口控件覆盖"。
1.  选择 **"默认**  >  **启用重启**  >  **"。**

    :::image type="content" source="../media/enable-window-controls-overlay-experiment.png" alt-text="启用窗口控件覆盖 API 实验。" lightbox="../media/enable-window-controls-overlay-experiment.png":::

窗口控件覆盖 API 也作为源试用功能提供。 你可以为应用的用户使用源试用版，以便从此功能中获益，而无需启用它。

有关源试用版详细信息，请转到Microsoft Edge[源试用版开发人员控制台。](https://developer.microsoft.com/microsoft-edge/origin-trials)


<!-- ====================================================================== -->
## <a name="enable-the-feature-in-your-app"></a>在应用中启用该功能

首先要使用 属性在应用清单文件中启用此功能，[](./web-app-manifests.md) `display_override` 如下面的代码示例所示。

```json
{
    "display_override": ["window-controls-overlay"]
}
```


<!-- ====================================================================== -->
## <a name="toggle-the-title-bar"></a>切换标题栏

启用后，应用的用户可以通过单击标题栏切换按钮来选择是否具有标题栏。

:::image type="content" source="../media/my-tracks-titlebar-toggle.png" alt-text="选择标题栏切换按钮。" lightbox="../media/my-tracks-titlebar-toggle.png":::

由于用户可以做出此选择，并且你的应用还可以在 Web 浏览器或移动设备上运行，因此代码无法对是否显示窗口控件覆盖做出任何假设。 因此，代码对标题栏几何图形更改做出反应非常重要。

若要了解更多信息，请参阅React[覆盖更改。](#react-to-overlay-changes)


<!-- ====================================================================== -->
## <a name="use-css-environment-variables-to-stay-clear-of-the-overlay"></a>使用 CSS 环境变量保持覆盖清晰

[`env()`](https://developer.mozilla.org/docs/Web/CSS/env)CSS 函数可用于访问用户代理定义的环境变量。

四个新的环境变量随窗口控件覆盖功能一起提供。

| 变量 | 说明 |
|:--- |:---
| `titlebar-area-x` | 覆盖层 `px` 与窗口左侧的距离（在 中） |
| `titlebar-area-y` | 覆盖层与窗口顶边的距离（在 `px` 中） |
| `titlebar-area-width` | 覆盖的宽度，以 `px` |
| `titlebar-area-height` | 覆盖的高度，以 `px` |

例如，可以使用这些变量来定位自己的标题栏并调整其大小。

```css
#title-bar {
    position: absolute;
    left: env(titlebar-area-x);
    top: env(titlebar-area-y);
    height: env(titlebar-area-height);
    width: env(titlebar-area-width);
}
```

知道覆盖的位置以及它的大小很重要，因为它可能并不总是位于同一侧 (例如，它位于 macOS 的左侧和 Windows) 的右侧，并且可能并不总是相同大小。


<!-- ====================================================================== -->
## <a name="make-regions-of-your-app-drag-handlers-for-the-window"></a>为窗口创建应用拖动处理程序的区域

隐藏标题栏时，只有系统关键窗口控件保持可见 (最大化、最小化、关闭以及应用信息按钮) ，这意味着用户移动应用的空间非常少。

您可以使用 CSS `-webkit-app-region` 属性为用户提供更多拖动应用程序的方法。 例如，如果你有自己的标题栏，你可以将其转换为窗口拖动处理程序。

```css
#title-bar {
    position: absolute;
    left: env(titlebar-area-x);
    top: env(titlebar-area-y);
    height: env(titlebar-area-height);
    width: env(titlebar-area-width);
    -webkit-app-region: drag;
}
```


<!-- ====================================================================== -->
## <a name="react-to-overlay-changes"></a>React覆盖更改

用户可以在应用运行时切换标题栏或更改窗口尺寸。 了解何时发生这些事件对于你的应用来说非常重要。 您可能需要重新排列标题栏中显示的某些内容，或页面上其他位置的布局部分。

可以使用 对象的 事件和 属性来侦听更改， `geometrychange` `visible` `navigator.windowControlsOverlay` 并知道标题栏是否可见。

> [!NOTE]
> 当用户 `geometrychange` 调整窗口大小时，会非常频繁地触发 。 为了避免过于频繁运行更改布局的代码并引起应用中的性能问题，建议使用 函数来限制事件 `debounce` 处理次数。
> 若要了解有关 有关详细信息 `debounce` ，请参阅限制 [和取消限制的区别](https://css-tricks.com/the-difference-between-throttling-and-debouncing/)。

```javascript
const debounce = (func, wait) => {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
};

if ('windowControlsOverlay' in navigator) {
    navigator.windowControlsOverlay.addEventListener('geometrychange', debounce(e => {
        // Detect if the Window Controls Overlay is visible.
        const isOverlayVisible = navigator.windowControlsOverlay.visible;
        // Get the size and position of the title bar area.
        const titleBarRect = e.boundingRect;

        console.log(`The overlay is ${isOverlayVisible ? 'visible' : 'hidden'}, the title bar width is ${titleBarRect.width}px`);
    }, 200));
}
```


<!-- ====================================================================== -->
## <a name="demo-pwa"></a>演示PWA

My Tracks 是一PWA窗口控件覆盖功能的应用演示应用。

* [在"管理"中](#enable-the-feature-in-your-app)Microsoft Edge。
* 转到 ["我的跟踪"](https://captainbrosset.github.io/mytracks/) 并安装应用。
* 从应用 **标题栏中选择** 隐藏标题栏按钮。

请注意，应用现在将内容一起显示到窗口框架的顶部，其中的标题栏曾位于该窗口框架的顶部。 地图的顶部区域也是一个拖动处理程序，可让用户移动窗口。

:::image type="content" source="../media/my-tracks-draggable-titlebar.png" alt-text="地图的顶部区域可用于移动窗口。" lightbox="../media/my-tracks-draggable-titlebar.png":::

此应用的源代码可以在"我的跟踪"库GitHub[访问](https://github.com/captainbrosset/mytracks)。

* [manifest.json](https://github.com/captainbrosset/mytracks/blob/main/mytracks/manifest.json)源文件声明应用使用窗口控件覆盖功能。
* 文件 [overlay.js](https://github.com/captainbrosset/mytracks/blob/main/src/overlay.js) 使用 `navigator.windowControlsOverlay` 对象。
* [style.css](https://github.com/captainbrosset/mytracks/blob/main/mytracks/style.css)源文件使用 `titlebar-area-height` CSS 环境变量。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [窗口控件覆盖视频教程](https://www.youtube.com/watch?v=NvClp35dFVI)
*   [自定义窗口控件覆盖PWA标题栏](https://web.dev/window-controls-overlay/)
