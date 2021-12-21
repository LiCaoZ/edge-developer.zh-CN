---
title: 在标题栏中显示内容
description: 了解如何使用窗口控件覆盖 API 为应用使用整个窗口区域。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， 窗口控件覆盖， API
ms.date: 09/02/2021
ms.openlocfilehash: 77a3e452b3edea6bb1fe452cfc60ee5e6c959d10
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12285244"
---
# <a name="display-content-in-the-title-bar"></a>在标题栏中显示内容

一PWA应用程序清单文件中显示属性，定义它在移动平台上的显示方式。 [](https://developer.mozilla.org/docs/Web/Manifest/display)  但是，若要创建类似本机的沉浸式体验， _桌面_ PBA 无法采用这种方法。

默认情况下，应用区域紧接在保留的标题栏区域下方开始：

:::image type="content" source="../media/my-tracks-titlebar.png" alt-text="The default Windows app title bar shown on the My Tracks demo app.":::

正常情况下显示标题栏的内容可以帮助 PWA 感觉更加本机。  许多桌面应用程序（如Visual Studio Code、Microsoft Teams和Microsoft Edge已执行如下操作：

:::image type="content" source="../media/vscode-titlebar.png" alt-text="Visual Studio Code标题栏区域中显示内容。":::

窗口控件覆盖 API 执行以下操作：
*  允许你在应用的整个图面区域显示 Web 内容。
*  将关键系统所需的窗口控件移动到覆盖层中。
*  使内容可以保持清除此覆盖层。


<!-- ====================================================================== -->
## <a name="enable-the-window-controls-overlay-api-in-microsoft-edge"></a>在窗口中启用窗口控件覆盖 API Microsoft Edge

窗口控件覆盖 API 是实验性的，必须在Microsoft Edge中启用，以使用它。

若要启用窗口控件覆盖 API：

1.  在Microsoft Edge中，转到 `edge://flags` 。
1.  选择 **"搜索标志** "，然后键入"窗口控件覆盖"。
1.  选择 **"默认**  >  **启用重启**  >  **"。**

    :::image type="content" source="../media/enable-window-controls-overlay-experiment.png" alt-text="启用窗口控件覆盖 API 实验。":::

窗口控件覆盖 API 也作为源试用功能提供。  若要使应用的用户从窗口控件覆盖中获益，而无需在 Microsoft Edge 中启用它，可以使用源试用版。

有关源试用版详细信息，请转到Microsoft Edge[源试用版开发人员控制台。](https://developer.microsoft.com/microsoft-edge/origin-trials)


<!-- ====================================================================== -->
## <a name="enable-the-window-controls-overlay-in-your-app"></a>在应用中启用窗口控件覆盖

首先要在应用的 Web 应用清单文件中启用窗口控件 [覆盖功能](./web-app-manifests.md)。  为此，在清单文件中，设置 `display_override` 属性：

```json
{
    "display_override": ["window-controls-overlay"]
}
```


<!-- ====================================================================== -->
## <a name="toggle-the-title-bar"></a>切换标题栏

启用"窗口控件覆盖"功能后，用户可以通过单击标题栏切换按钮来选择是否具有标题栏：

:::image type="content" source="../media/my-tracks-titlebar-toggle.png" alt-text="选择标题栏切换按钮。":::

代码无法假定显示窗口控件覆盖层，因为：
*  用户可以选择是否显示标题栏。
*  你的应用还可以在 Web 浏览器或移动设备上运行，也可以作为桌面应用运行。

因此，代码需要响应标题栏几何图形更改。  若要了解更多信息，请参阅React[覆盖更改。](#react-to-overlay-changes)


<!-- ====================================================================== -->
## <a name="use-css-environment-variables-to-stay-clear-of-the-overlay"></a>使用 CSS 环境变量保持覆盖清晰

[`env()`](https://developer.mozilla.org/docs/Web/CSS/env)CSS 函数可用于访问用户代理定义的环境变量。

窗口控件覆盖功能添加了四个环境变量：

| 变量 | 说明 |
|:--- |:---
| `titlebar-area-x` | 覆盖层 `px` 与窗口左侧的距离（在 中） |
| `titlebar-area-y` | 覆盖层与窗口顶边的距离（在 `px` 中） |
| `titlebar-area-width` | 覆盖的宽度，以 `px` |
| `titlebar-area-height` | 覆盖的高度，以 `px` |

可以使用这些环境变量来定位应用的标题栏并调整其大小：

```css
#title-bar {
    position: absolute;
    left: env(titlebar-area-x);
    top: env(titlebar-area-y);
    height: env(titlebar-area-height);
    width: env(titlebar-area-width);
}
```

了解覆盖的位置以及它的重要位置。  覆盖可能并不总是位于窗口的同一侧;在 macOS 上，覆盖位于左侧，但在Windows，覆盖位于右侧。  此外，覆盖可能并不总是相同大小。


<!-- ====================================================================== -->
## <a name="make-regions-of-your-app-drag-handlers-for-the-window"></a>为窗口创建应用拖动处理程序的区域

当标题栏隐藏时，只有系统关键窗口控件 (最大化、最小化、关闭以及应用信息图标****) 。 **** **** ****  这意味着用户很少能四处移动应用。

您可以使用 CSS `-webkit-app-region` 属性为用户提供更多拖动应用程序的方法。  例如，如果你的应用有自己的标题栏，你可以将其标题栏转换为窗口拖动处理程序：

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

用户可以在应用运行时切换标题栏或更改窗口尺寸。  了解何时发生这些事件对于你的应用来说非常重要。  你的应用可能需要重新排列标题栏中显示的内容，或重新排列页面上其他位置的布局。

若要侦听更改，请使用 `geometrychange` 事件。  若要检测标题栏是否可见，请使用 `visible` 对象上的 `navigator.windowControlsOverlay` 属性。

> [!NOTE]
> 当用户 `geometrychange` 调整窗口大小时，会非常频繁地触发 。  若要避免过于频繁运行更改布局的代码，并且导致应用中出现性能问题，请使用 函数来限制 `debounce` 处理事件的时间。  请参阅 [限制和取消跳到的区别](https://css-tricks.com/the-difference-between-throttling-and-debouncing/)。

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
        const titleBarRect = e.titlebarAreaRect;

        console.log(`The overlay is ${isOverlayVisible ? 'visible' : 'hidden'}, the title bar width is ${titleBarRect.width}px`);
    }, 200));
}
```


<!-- ====================================================================== -->
## <a name="demo-app"></a>演示应用

My Tracks 是PWA窗口控件覆盖功能的主要演示应用。

1. 在Microsoft Edge中，[启用窗口控件覆盖](#enable-the-window-controls-overlay-in-your-app)。

2. 转到 ["我的跟踪"](https://captainbrosset.github.io/mytracks/) 并安装应用。

3. 从应用 **标题栏中选择** 隐藏标题栏按钮。

   应用现在一向显示窗口框架顶部的内容，标题栏以前位于该窗口框架的顶部。  地图的顶部区域是一个拖动处理程序，以允许用户移动窗口。

   :::image type="content" source="../media/my-tracks-draggable-titlebar.png" alt-text="地图的顶部区域可用于移动窗口。":::

此应用程序的源代码位于"我的轨 ["](https://github.com/captainbrosset/mytracks) 存储库。

* [manifest.json](https://github.com/captainbrosset/mytracks/blob/main/mytracks/manifest.json)源文件声明应用使用窗口控件覆盖功能。

* 文件 [overlay.js](https://github.com/captainbrosset/mytracks/blob/main/src/overlay.js) 使用 `navigator.windowControlsOverlay` 对象。

* [style.css](https://github.com/captainbrosset/mytracks/blob/main/mytracks/style.css)源文件使用 `titlebar-area-height` CSS 环境变量。


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*   [窗口控件覆盖视频教程](https://www.youtube.com/watch?v=NvClp35dFVI)
*   [自定义窗口标题栏PWA窗口控件覆盖](https://web.dev/window-controls-overlay/)
*   [开箱而出](https://alistapart.com/article/breaking-out-of-the-box/)
