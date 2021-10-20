---
description: 使用 Microsoft Edge 中的虚拟设备构建移动优先的网站。
title: 在 Microsoft Edge DevTools 中模拟移动设备
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/19/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools, 仿真, 设备, 模拟, 移动
ms.openlocfilehash: 9c0396537dfc7ba75bd979b1197b0f4c287e56a5
ms.sourcegitcommit: 54f9566aa935fb853215c9b6f995fa0c98f3261f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2021
ms.locfileid: "12103501"
---
<!-- Copyright Kayce Basques

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->
# <a name="emulate-mobile-devices-in-microsoft-edge-devtools"></a>在 Microsoft Edge DevTools 中模拟移动设备

使用“**设备仿真**”来大致了解你的页面在移动设备上的外观和响应方式。  Microsoft Edge DevTools 提供了一系列功能，可帮助你模拟移动设备。  该系列包括以下功能。

*   [模拟移动视区](#simulate-a-mobile-viewport)
*   [限制网络](#throttle-the-network-only)
*   [限制 CPU](#throttle-the-cpu-only)
*   [替代地理位置](#override-geolocation)
*   [设置方向](#set-orientation)
*   [设置用户代理字符串](#set-the-user-agent-string)
*   [设置用户代理客户端提示](#set-user-agent-client-hints)


<!-- ====================================================================== -->
## <a name="limitations"></a>限制

**设备模拟** 是移动设备上页面外观[一级近似][WikiApproximation]。  **设备仿真** 实际上不会在移动设备上运行你的代码。  相反，你可以模拟笔记本电脑或台式机的移动用户体验。

移动设备的某些方面从不在 DevTools 中模拟。  例如，移动 CPU 的体系结构与笔记本电脑或台式机 CPU 的体系结构不同。  如有疑问，最佳选择是在移动设备上实际运行页面。

使用 [远程调试][DevToolsRemoteDebugging] 与计算机中的页面代码交互，而你的页面实际上在移动设备上运行。  与代码交互时，可以查看、更改、调试、配置文件或全部四者。  你的计算机可以是笔记本或台式计算机。


<!-- ====================================================================== -->
## <a name="simulate-a-mobile-viewport"></a>模拟移动视区

选择"切换 **设备仿真 (**  切换设备工具栏) 或选择"自定义和控制 ![ ](../media/toggle-device-toolbar-dark-icon.msft.png) **DevTools** (`...`) > **设备模拟** "以打开使您能够模拟移动视口的 UI。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-highlighted.msft.png" alt-text="设备工具栏。" lightbox="../media/device-mode-toggle-device-toolbar-highlighted.msft.png":::

默认情况下，设备工具栏在响应式视区模式下打开。

### <a name="responsive-viewport-mode"></a>响应式视区模式

若要跨多个屏幕大小快速测试页面的外观，请拖动手柄以将视区调整为所需尺寸。  还可以在宽度和高度框中输入特定值。  在下图中，宽度设置为 `626`，高度设置为 `516`。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-handles-highlighted.msft.png" alt-text="在响应式视口模式下更改视口尺寸的句柄。" lightbox="../media/device-mode-toggle-device-toolbar-handles-highlighted.msft.png":::

#### <a name="show-media-queries"></a>显示媒体查询

如果已在页面上定义了媒体查询，请通过在视区上方显示媒体查询断点，跳至视区维度，使这些媒体查询生效。  选择 **"更多选项**  >  **""显示媒体查询"。**

:::image type="content" source="../media/device-mode-toggle-device-toolbar-more-options-show-media-queries.msft.png" alt-text="显示媒体查询。" lightbox="../media/device-mode-toggle-device-toolbar-more-options-show-media-queries.msft.png":::

选择一个断点以更改视口的宽度，以便触发媒体查询。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-click-breakpoint.msft.png" alt-text="选择一个断点以更改视口的宽度。" lightbox="../media/device-mode-toggle-device-toolbar-click-breakpoint.msft.png":::

#### <a name="set-the-device-type"></a>设置设备类型

使用“**设备类型**”列表模拟移动设备或桌面设备。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-device-type-list.msft.png" alt-text="设备类型列表。" lightbox="../media/device-mode-toggle-device-toolbar-device-type-list.msft.png":::

下表介绍了可用设备类型选项之间的差异。  “渲染方法”列是指 Microsoft Edge 是将页面渲染为移动视区还是桌面视区。  “光标图标”列是指当你将鼠标悬停在页面上时所显示的光标类型。  “触发事件”列是指你与页面交互时页面是触发 `touch` 还是 `click` 事件。

| 选项 | 渲染方法 | 光标图标 | 触发事件 |
|:--- |:--- |:--- |:--- |
| 移动设备 | 移动设备 | 圆形 | `touch` |
| 移动 (触摸)  | 移动设备 | 正常 | `click` |
| 桌面 | 桌面 | 正常 | `click` |
| 桌面 (触摸)  | 桌面 | 圆形 | `touch` |

> [!NOTE]
> 如果未显示**设备类型**列表，请选择"更多选项****  >  **""添加设备类型"。**

### <a name="mobile-device-viewport-mode"></a>移动设备视区模式

若要模拟特定移动设备的尺寸，请从“**设备**”列表中选择该设备。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-device-list.msft.png" alt-text="设备列表。" lightbox="../media/device-mode-toggle-device-toolbar-device-list.msft.png":::

#### <a name="rotate-the-viewport-to-landscape-orientation"></a>将视区旋转为横向

横向测试你的网页。

*   若要将视口旋转到横向，请选择旋转 ** (** ![ 旋转 ](../media/rotate-dark-icon.msft.png)) 。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-landscape.msft.png" alt-text="页面以横向显示。" lightbox="../media/device-mode-toggle-device-toolbar-landscape.msft.png":::

> [!NOTE]
> 如果“**设备**”工具栏较窄，将不显示“**旋转**”按钮。 若要访问 **旋转按钮** ，请增加设备工具栏 **的宽度**。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-highlighted.msft.png" alt-text="设备工具栏。" lightbox="../media/device-mode-toggle-device-toolbar-highlighted.msft.png":::

另请参阅 [设置方向](#set-orientation)。

#### <a name="show-device-frame"></a>显示设备框架

若要模拟特定移动设备的尺寸，请打开"更多选项"，然后选择"显示设备**** 框架"以显示视口周围的物理设备框架。 ****

:::image type="content" source="../media/device-mode-toggle-device-toolbar-option-show-device-frame.msft.png" alt-text="&quot;显示设备框架&quot;菜单项。" lightbox="../media/device-mode-toggle-device-toolbar-option-show-device-frame.msft.png":::

> [!NOTE]
> 如果未为特定设备显示设备帧，这意味着 DevTools 没有该设备的艺术。

设备框架 6 iPhone帧：

:::image type="content" source="../media/device-mode-toggle-device-toolbar-options-device-frame-iphone-6.msft.png" alt-text="设备框架 6 iPhone帧。" lightbox="../media/device-mode-toggle-device-toolbar-options-device-frame-iphone-6.msft.png":::

#### <a name="add-a-custom-mobile-device"></a>添加自定义移动设备

如果默认列表中未包含所需的移动设备选项，可以添加自定义设备。  添加自定义设备：

1.  Select the **Device** list > **Edit**.

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-device-list-edit.msft.png" alt-text="从&quot;设备&quot;列表中选择&quot;编辑&quot;。" lightbox="../media/device-mode-toggle-device-toolbar-device-list-edit.msft.png":::

1.  选择 **"添加自定义设备"。**

1.  在“**仿真设备**”上，输入自定义设备的设备名称、屏幕宽度和屏幕高度。  [设备像素比率][MDNWindowDevicePixelRatio]、[用户代理字符串][MDNUserAgent]和设备 [类型](#set-the-device-type) 字段是可选的。  设备类型字段默认为“**移动设备**”。

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-settings-emulated-devices-add.msft.png" alt-text="添加自定义设备。" lightbox="../media/device-mode-toggle-device-toolbar-settings-emulated-devices-add.msft.png":::

### <a name="show-rulers"></a>显示标尺

如果你需要测量屏幕尺寸，可以使用标尺测量屏幕大小（以像素为单位）。  选择 **"更多**  >  **选项"显示**标尺以显示视口上方和左侧的标尺。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-options-show-rulers.msft.png" alt-text="&quot;显示标尺&quot;菜单项。":::

标尺显示在视口的上方和左侧：

:::image type="content" source="../media/device-mode-toggle-device-toolbar-rulers.msft.png" alt-text="视口上方和左侧的标尺。":::

### <a name="zoom-the-viewport"></a>缩放视区

若要在多个缩放级别测试页面的外观，请使用“**缩放**”列表进行缩放。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-zoom.msft.png" alt-text="缩放列表。" lightbox="../media/device-mode-toggle-device-toolbar-zoom.msft.png":::


<!-- ====================================================================== -->
## <a name="throttle-the-network-and-cpu"></a>限制网络和 CPU

移动设备通常具有网络和 CPU 限制。  测试页面加载的速度，以及页面如何以不同的 Internet 和 CPU 速度响应。

1.  选择 **限制** 列表，将预设更改为 **中层移动** 或 **低端移动**。
    *   “**中层移动设备**”将模拟 `fast 3G` 并限制你的 CPU。  它是正常速度的 1/4。
    *   “**低端移动设备**”将模拟 `slow 3G` 并限制你的 CPU。  它是正常速度的 1/6。

所有限制都基于笔记本电脑或桌面设备的正常功能。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-throttle.msft.png" alt-text="设备工具栏中的限制列表。" lightbox="../media/device-mode-toggle-device-toolbar-throttle.msft.png":::

> [!NOTE]
> 如果 **“限制”列表**处于隐藏状态，则表示**设备工具栏**过窄。  若要访问 **“限制”列表**，请增加**设备工具栏**的宽度。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-highlighted.msft.png" alt-text="设备工具栏。" lightbox="../media/device-mode-toggle-device-toolbar-highlighted.msft.png":::

### <a name="throttle-the-cpu-only"></a>仅限制 CPU

仅限制 CPU 而不是网络：

1.  选择"**性能"** 面板，然后选择 **"捕获**设置 (![ 捕获 ](../media/capture-settings-icon.msft.png) 设置) 。
1.  选择**CPU**  >  **速度减慢 4 倍或****速度减慢 6 倍**。

:::image type="content" source="../media/device-mode-performance-cpu-throttle.msft.png" alt-text="&quot;性能&quot;面板中的 CPU 列表。" lightbox="../media/device-mode-performance-cpu-throttle.msft.png":::

### <a name="throttle-the-network-only"></a>仅限制网络

仅限制网络而不是 CPU：

1.  选择"**网络"** 工具，然后选择"**联机**  >  **快速 3G"** 或"**慢速 3G"。**

    :::image type="content" source="../media/device-mode-network-throttle.msft.png" alt-text="网络面板中的限制列表。" lightbox="../media/device-mode-network-throttle.msft.png":::

    或者 `Control` + `Shift` + `P` ， (Windows、Linux) 或 `Command` (macOS + `Shift` + `P`) **** `3G` ******** 打开"命令菜单"，键入 ，然后选择"启用快速 3G 限制"或"启用慢速 3G 限制"。

    :::image type="content" source="../media/device-mode-command-menu-throttle.msft.png" alt-text="从&quot;命令菜单&quot;中选择&quot;启用快速或缓慢的 3G 限制&quot;。" lightbox="../media/device-mode-command-menu-throttle.msft.png":::

您还可以从"性能"面板设置 **网络** 限制：

1.  选择 **"捕获设置 (** 捕获设置) 并选择"网络"列表，将预设更改为 ![ ](../media/capture-settings-icon.msft.png) **"快速 3G"** 或"**慢速 3G"。** ****

    :::image type="content" source="../media/device-mode-performance-network-throttle.msft.png" alt-text="从&quot;性能&quot;面板设置网络限制。" lightbox="../media/device-mode-performance-network-throttle.msft.png":::


<!-- ====================================================================== -->
## <a name="override-geolocation"></a>替代地理位置

 如果页面依赖移动设备中的地理位置信息正确呈现，则使用替代地理位置的 UI 提供不同的地理位置。

1.  选择 **"自定义和控制开发工具 () >** `...` **更多工具**  >  **传感器"。**

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-more-tools-sensors.msft.png" alt-text="用于地理位置的传感器。" lightbox="../media/device-mode-toggle-device-toolbar-more-tools-sensors.msft.png":::

    或者，通过选择"命令菜单" (Windows、Linux) `Control` + `Shift` + `P` 或 (`Command` + `Shift` + `P` macOS) 。  键入 `Sensors` ，然后选择显示 **传感器**。

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-command-menu-sensors.msft.png" alt-text="显示命令菜单中的地理位置传感器。" lightbox="../media/device-mode-toggle-device-toolbar-command-menu-sensors.msft.png":::

在 **"传感器"** 面板上，若要选择预设位置之一，请使用" **位置** "下拉菜单。  若要输入自定义位置，请选择 **"其他"** 并输入自定义位置的坐标。  若要测试页面在位置信息不可用时的行为方式，请选择"**位置不可用"。**

:::image type="content" source="../media/device-mode-toggle-device-toolbar-sensors-tokyo.msft.png" alt-text="已选择预设位置的“传感器”面板。" lightbox="../media/device-mode-toggle-device-toolbar-sensors-tokyo.msft.png":::


<!-- ====================================================================== -->
## <a name="set-orientation"></a>设置方向

如果页面依赖来自移动设备的方向信息来正确呈现，请打开方向 UI。

1.  选择 **"自定义和控制开发工具 () >** `...` **更多工具**  >  **传感器"。**

:::image type="content" source="../media/device-mode-toggle-device-toolbar-more-tools-sensors.msft.png" alt-text="&quot;更多工具&quot;菜单上的&quot;传感器&quot;命令。" lightbox="../media/device-mode-toggle-device-toolbar-more-tools-sensors.msft.png":::

1.  或者，通过选择"命令菜单" (Windows、Linux) `Control` + `Shift` + `P` 或 (`Command` + `Shift` + `P` macOS) 。  键入 `Sensors` ，然后选择"**显示传感器"。**

:::image type="content" source="../media/device-mode-toggle-device-toolbar-command-menu-sensors.msft.png" alt-text="显示方向传感器。" lightbox="../media/device-mode-toggle-device-toolbar-command-menu-sensors.msft.png":::
   针对方向**显示传感器**
:::image-end:::

在 **"传感器"** 面板上，可以从"方向"下拉菜单中选择预设**** 方向。  若要输入你自己的方向，请选择"**** 自定义方向"，然后输入你自己的 [alpha][MDNDeviceOrientaitonAlpha]、[beta][MDNDeviceOrientaitonBeta] 和 [gamma][MDNDeviceOrientaitonGamma] 值。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-sensors-tokyo-portrait-upside-down.msft.png" alt-text="&quot;传感器&quot;面板上的方向选项。" lightbox="../media/device-mode-toggle-device-toolbar-sensors-tokyo-portrait-upside-down.msft.png":::


<!-- ====================================================================== -->
## <a name="set-the-user-agent-string"></a>设置用户代理字符串

如果页面依赖移动设备中的用户代理字符串来正确呈现，请使用“**网络条件**”面板提供不同的用户代理字符串。

1.  选择 **"自定义和控制开发工具 () >** `...` **更多工具**  >  **网络条件"。**

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-more-tools-network-conditions.msft.png" alt-text="&quot;更多工具&quot;菜单中的网络条件条目。" lightbox="../media/device-mode-toggle-device-toolbar-more-tools-network-conditions.msft.png":::

1.  或者，通过选择"命令菜单" (Windows、Linux) `Control` + `Shift` + `P` 或 (`Command` + `Shift` + `P` macOS) 。键入 `Network conditions` ，然后选择"**显示网络条件"。**

    :::image type="content" source="../media/device-mode-toggle-device-toolbar-command-menu-network-conditions.msft.png" alt-text="显示网络条件。" lightbox="../media/device-mode-toggle-device-toolbar-command-menu-network-conditions.msft.png":::

在" **用户代理"旁边**，清除" **使用浏览器默认"** 复选框。  然后， **选择"自定义** "以从预定义的用户代理字符串列表中选择。  若要输入你自己的用户代理字符串，请在“**输入自定义用户代理**”中输入字符串。

:::image type="content" source="../media/device-mode-toggle-device-toolbar-network-conditions-macos.msft.png" alt-text="将用户代理字符串设置为Microsoft Edge macOS 上。" lightbox="../media/device-mode-toggle-device-toolbar-network-conditions-macos.msft.png":::


<!-- ====================================================================== -->
## <a name="set-user-agent-client-hints"></a>设置用户代理客户端提示

如果你的网站使用 [用户代理客户端提示](../../web-platform/user-agent-guidance.md)，请使用 **模拟设备** 面板添加设备和设置用户代理客户端提示。

1.  打开上下文**菜单 (** 右键单击") "，然后选择"检查 **"。**
1.  选择**设置**  >  **设备"。**
1.  在"模拟设备"面板中，选择 **"添加自定义设备**"，然后展开 **"用户代理客户端提示"。**

    :::image type="content" source="images/emulated-devices-user-agent-client-hints.msft.png" alt-text="设置用户代理客户端提示。" lightbox="images/emulated-devices-user-agent-client-hints.msft.png":::

1.  在"设备名称"文本框 **中键入** 唯一的名称，例如 `Test101` 。
1.  接受默认值或根据需要更改**Width、Height**和设备**像素**比率。 ****
1.  按如下所示设置用户代理客户端提示。
    *  **品牌**和**版本**，如*Edge*和*92。*  选择 **+ 添加品牌** 以添加多个品牌和版本对。
    *  **完整浏览器版本**，例如*92.0.1111.0。*
    *  **平台**和**版本**，如*Windows*和*10.0。*
    *  **体系结构** ，如 *x86*。
    *  **设备型号** ，例如 *，一些设备型号*。

    > [!NOTE]
    > 设置或更改任何用户代理客户端提示。 没有所需的值。

1. 选择**添加**。 新设备以选定状态显示在" **模拟设备** "列表顶部。

还可以在网络分析参考中设置用户 [代理客户端提示](../network/reference.md)。


<!-- ====================================================================== -->
<!-- links -->
[DevToolsRemoteDebugging]: ../remote-debugging/index.md "Android 设备远程调试入门 | Microsoft Docs"
<!--[DevToolsCommunity]: ../index.md#community "Join the DevTools community | Microsoft Docs"  -->
<!-- external links -->
[MDNWindowDevicePixelRatio]：" https://developer.mozilla.org/docs/Web/API/Window/devicePixelRatio Window.devicePixelRatio |MDN&quot; [MDNUserAgent]： https://developer.mozilla.org/docs/Glossary/User_agent &quot;User Agent |MDN&quot; [MDNDeviceOrientaitonAlpha]： https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/alpha &quot;DeviceOrientationEvent.alpha |MDN&quot; [MDNDeviceOrientaitonBeta]： https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/beta &quot;DeviceOrientationEvent.beta |MDN&quot; [MDNDeviceOrientaitonGamma]： https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/gamma &quot;DeviceOrientationEvent.gamma |MDN&quot; [WikiApproximation]： https://en.wikipedia.org/wiki/Order_of_approximation#First-order &quot;近似顺序 - 一级 - 维基百科"


<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/device-mode/index)，由技术编写 (Chrome DevTools \& Lighthouse) 创作。 [][KayceBasques]

[![知识共享许可][CCby4Image]][CCA4IL] 本作品根据[知识共享署名 4.0 国际许可][CCA4IL]获得许可。

[CCA4IL]: https://creativecommons.org/licenses/by/4.0
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies
[KayceBasques]: https://developers.google.com/web/resources/contributors#kayce-basques
