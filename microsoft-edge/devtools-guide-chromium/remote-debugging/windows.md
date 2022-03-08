---
title: 远程调试 Windows 设备
description: 开始远程调试Windows设备。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 04/23/2021
ms.openlocfilehash: 212054f9ce81dcc6d0cb007d5c18dd3cc707c3f2
ms.sourcegitcommit: e286d79fbd94666df7596bd2633fb60fe08e86fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2022
ms.locfileid: "12431821"
---
# <a name="remotely-debug-windows-devices"></a>远程调试 Windows 设备

远程调试设备或 macOS Windows 10或更高版本Windows实时内容。

本教程指导你完成以下任务：

*  将 Windows 设备设置为远程调试，然后从开发计算机连接到该设备。

*  检查和调试开发Windows设备中的实时内容。

*  将来自你的Windows内容的屏幕广播到开发计算机上 DevTools 实例上。


<!-- ====================================================================== -->
## <a name="step-1-set-up-the-host-debuggee-machine"></a>步骤 1：设置 (调试程序计算机) 

主机或调试程序计算机是Windows 10调试的设备或更高版本的设备。  这可能是你很难从物理上访问的远程设备，或者可能没有键盘和鼠标外设，导致难以与该设备上的 Microsoft Edge DevTools 交互。

若要在调试 (计算机) 主机：

1. 安装和配置[Microsoft Edge](https://www.microsoft.com/edge)

1. 从客户端[安装 Microsoft Edge (Beta) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)远程[Microsoft Store](https://www.microsoft.com/store/apps/windows)

1. 激活 [开发人员模式](/windows/apps/get-started/enable-your-device-for-development) 并启用 [Device Portal](/windows/uwp/debug-test-perf/device-portal)

### <a name="install-and-configure-microsoft-edge"></a>安装和配置Microsoft Edge

1. 如果尚未在要调试Windows 10或更高版本的设备上，从此页面Microsoft Edge[安装。](https://www.microsoft.com/edge)

1. 如果在调试程序 () 计算机上使用预安装的 Microsoft Edge 版本，请验证您是否具有 Microsoft Edge (Chromium) ，而不是 Microsoft Edge (EdgeHTML) 。  检查的一种快速方法就是在 `edge://settings/help` 浏览器中加载并确认版本号是否为 75 或更高。

1. 转到"`edge://flags`Microsoft Edge"。 

1. 在 **"搜索标志**"中，键入"通过设备门户启用**Windows调试"**。 将标志设置为 **已启用**。 然后，单击 **"重启**"按钮以重新启动Microsoft Edge。

:::image type="content" source="../media/remote-debugging-windows-media-edge-flags-on-host.msft.png" alt-text="设置&quot;通过设备门户标志Windows远程调试&quot;。" lightbox="../media/remote-debugging-windows-media-edge-flags-on-host.msft.png":::

### <a name="install-the-remote-tools-for-microsoft-edge-beta"></a>安装适用于 Microsoft Edge (Beta) 

从客户端[安装 Microsoft Edge (Beta) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)远程[Microsoft Store](https://www.microsoft.com/store/apps/windows)。

> [!NOTE]
> **如果你** Microsoft Edge (使用 Windows 10 或更高版本 1809 或更早版本) [Beta ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT) 版远程工具的"获取"按钮可能处于禁用状态。  若要在调试 (中) 主机，它必须在 Windows 10版本 1903 或更高版本中运行。  更新调试 () 的主机，以获取适用于 [Microsoft Edge (Beta) 的远程) ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)。

:::image type="content" source="../media/remote-debugging-windows-media-remote-tools-in-store.msft.png" alt-text="Microsoft Edge (中的) Beta Microsoft Store。" lightbox="../media/remote-debugging-windows-media-remote-tools-in-store.msft.png":::

启动 [Beta Microsoft Edge (](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)远程) ，如果系统提示，接受应用中的权限对话框。  现在，你可以关闭 [Beta ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT) Microsoft Edge (远程工具) 无需为将来的远程调试会话打开它。

### <a name="activate-developer-mode-and-enable-device-portal"></a>激活开发人员模式并启用 Device Portal

如果你使用 WiFi 网络，请确保该网络标记为"域"或"**专用"**。****  可以通过打开应用验证状态，Windows 安全中心防火墙****&网络保护并检查你的网络**** 是否列为"域网络"或"**专用网络**"。****

如果网络列为**** > "公用"****，请转到 设置**Network &** **InternetWi-Fi** > ，单击网络，将"网络**配置文件**"按钮切换为 **"专用"**。

现在，打开**设置**应用。  在 **"查找设置"** 中，输入 `Developer settings` 并选择它。  打开开发人员**模式。**  现在，可以通过将"通过本地网络连接打开远程诊断"设置为"打开"来**打开** **Device** **Portal**。  然后可以选择 **打开身份验证，** 以便客户端 (调试) 设备必须提供正确的凭据才能连接到此设备。

> [!NOTE]
> 如果 **通过本地网络连接打开远程诊断。** 之前已打开，必须将其关闭并再次打开，Device **Portal** 可以使用 Microsoft Edge ([Beta ](https://www.microsoft.com/store/apps/9P6CMFV44ZLT)) 。  如果 **"适用于开发人员**"部分未设置，**Device Portal** 可能已经打开，因此请尝试重新启动 Windows 10 或更高版本的设备。****

:::image type="content" source="../media/remote-debugging-windows-media-host-settings.msft.png" alt-text="已设置开发人员模式和设备门户的开发人员应用。" lightbox="../media/remote-debugging-windows-media-host-settings.msft.png":::

注意以下位置下显示计算机 IP 地址和连接**使用：**。  下图中的 IP 地址为 ， `192.168.86.78` 连接端口为 `50080`：

:::image type="content" source="../media/remote-debugging-windows-media-host-settings-ip-address.msft.png" alt-text="请注意 ip 地址和连接端口在设置。" lightbox="../media/remote-debugging-windows-media-host-settings-ip-address.msft.png":::

你将在下面一节中 (调试) 设备上 [输入信息](#step-2-set-up-the-client-debugger-machine)。  在主机 (调试程序) 计算机上打开要从客户端 (调试器) 计算机调试的 Microsoft Edge 和[渐进式 Web 应用 (PWA ](../progressive-web-apps/index.md)) 中的选项卡。


<!-- ====================================================================== -->
## <a name="step-2-set-up-the-client-debugger-machine"></a>步骤 2：将客户端 (调试器计算机) 

客户端或调试程序计算机是你想要调试的设备。  此设备可能是你的日常开发计算机，也可能只是在家工作时的电脑或 MacBook。

1. 若要将客户端 (调试) 计算机，[Microsoft Edge从此页面](https://www.microsoft.com/edge)安装客户端。如果尚未安装。

1. 如果在调试程序 () 计算机上使用预安装的 Microsoft Edge 版本，请验证您是否具有 Microsoft Edge (Chromium) ，而不是 Microsoft Edge (EdgeHTML) 。  检查的一种快速方法就是在 `edge://settings/help` 浏览器中加载并确认版本号是否为 75 或更高。

1. 转到 Microsoft Edge `edge://inspect` 中的页面。  默认情况下，你应该位于" **设备"** 部分。

1. under **连接 to a remote Windows device**， enter the IP address and the connection port of the host (debuggee) machine following this pattern： http://`IP address`：`connection port`.

1. 单击**连接设备"**。

   :::image type="content" source="../media/remote-debugging-windows-media-edge-inspect.msft.png" alt-text="客户端 edge://inspect 页。" lightbox="../media/remote-debugging-windows-media-edge-inspect.msft.png":::

1. 如果为 (调试) 主机设置身份验证，系统将提示输入用户名和密码，以便客户端 (调试) 计算机成功连接。**** ****

### <a name="using-https-instead-of-http"></a>使用 https 而不是 http

如果要连接到调试程序 (而不是) 连接到 `https` 调试者计算机 `http`：

1. 转到客户端`http://IP address:50080/config/rootcertificate`Microsoft Edge调试器 (上的) 中。  这会自动下载名为 的安全证书 `rootcertificate.cer`。

1. 选择 `rootcertificate.cer`。  这将打开Windows[管理器工具](/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in#view-certificates-with-the-certificate-manager-tool)。

1. 单击 **"安装证书...**"，确保" **当前** 用户"已打开，然后单击"下一步 **"**。

1. 单击 **"将所有证书放在以下存储中"，** 然后单击" **浏览..."**。

1. 选择" **受信任的根证书颁发机构"** 存储，然后单击"确定 **"**。

1. 单击**下一步**，然后单击**完成**。

1. 如果系统提示，请确认要安装此证书到受信任的根 **证书颁发机构** 存储。

1. 现在，在使用页面从 (调试) `edge://inspect` (调试程序) 主机连接到调试程序计算机时，必须使用其他 `connection port` 值。  默认情况下，对于桌面Windows，Device Portal 使用 `50080` 作为 `connection port` 的 `http`。  对于 `https`，Device Portal 使用 ， `50043` 因此请遵循此 https://`IP address`：`50043` 在页面上 `edge://inspect` 。  [详细了解 Device Portal 使用的默认端口](/windows/uwp/debug-test-perf/device-portal#setup)。

> [!NOTE]
> `http` `50043``https` `50080`的默认端口为 ，默认端口为 ，但并不总是这样，因为桌面版 Device Portal 声明临时范围 (\>50，000) 中的端口，以防止与设备上现有端口声明发生冲突。  若要了解更多信息，请参阅桌面[版](/windows/uwp/debug-test-perf/device-portal-desktop#registry-based-configuration-for-device-portal) Device Portal 设置移植Windows部分。


<!-- ====================================================================== -->
## <a name="step-3-debug-content-on-the-host-from-the-client"></a>步骤 3：从客户端调试主机上的内容

如果客户端 (调试器) 计算机成功连接到主机 (debuggee) 计算机`edge://inspect`，则客户端上的页面现在会显示 Microsoft Edge 中的选项卡列表和主机上任何打开的 PWA。

:::image type="content" source="../media/remote-debugging-windows-media-edge-inspect-connected.msft.png" alt-text="客户端 edge://inspect 页在主机上显示 Microsoft Edge 和 PWA 中的选项卡。" lightbox="../media/remote-debugging-windows-media-edge-inspect-connected.msft.png":::

确定要调试的内容，然后单击"检查 **"**。  开发人员Microsoft Edge工具将在新选项卡中打开，并屏幕将内容从主机 (调试程序) 计算机屏蔽到客户端 (调试) 计算机。  现在，你可以对主机上运行Microsoft Edge使用客户端上的 DevTools 的完整功能。  在此处了解有关如何使用开发人员工具Microsoft Edge开发人员[工具。](../index.md)

:::image type="content" source="../media/remote-debugging-windows-media-devtools-client.msft.png" alt-text="The Microsoft Edge DevTools on the client debugging a tab in Microsoft Edge on the host." lightbox="../media/remote-debugging-windows-media-devtools-client.msft.png":::

### <a name="inspect-elements"></a>检查元素

例如，尝试检查元素。  转到客户端 **上的** DevTools 实例的"元素"工具，将鼠标悬停在某个元素上以在主机设备的视口中突出显示它。

还可以点击主机设备屏幕上的某个元素，以在"元素"工具 **中选择** 它。  在 **客户端上的** DevTools 实例上选择"选择元素"，然后点击主机设备屏幕上的元素。

> [!NOTE]
> **Select Element** is disabled after the first touch， so you need to turn it on again time you want to use this feature.

> [!IMPORTANT]
> "**元素"工具**中的"事件侦听器 **"窗格在**版本 1903 Windows 10为空。  这是一个已知问题，团队计划在版本 1903 的服务更新中修复Windows 10侦听器"窗格。****


<!-- ====================================================================== -->
## <a name="step-4-screencast-your-host-screen-to-your-client-device"></a>步骤 4：将主机屏幕屏蔽到客户端设备

默认情况下，客户端上的 DevTools 实例已打开屏幕视频，这允许你在客户端设备的 DevTools 实例中查看主机设备上的内容。  单击 **"切换屏幕视频** "以打开或关闭此功能。

:::image type="content" source="../media/remote-debugging-windows-media-toggle-screencast.msft.png" alt-text="客户端上的开发人员工具Microsoft Edge切换屏幕显示按钮。" lightbox="../media/remote-debugging-windows-media-toggle-screencast.msft.png":::

可以通过多种方式与屏幕广播交互：
*  单击将转换为点击，在设备上触发正确的触摸事件。
*  计算机上的击键会发送到设备。
*  若要模拟收缩手势，拖动时按住 `Shift`。
*  如果要滚动，请使用触控板或鼠标滚轮，或使用鼠标指针拖动。

屏幕广播上的一些注释：
*  截屏视频仅显示页面内容。  屏幕广播的透明部分表示设备接口，例如 Microsoft Edge 地址栏、Windows 10 或更高版本的任务栏以及 Windows 10 或更高版本的键盘。
*  截屏视频会对帧速率产生负面影响。  在测量滚动或动画时禁用截屏视频，以更准确地了解页面性能。
*  如果主机设备屏幕锁定，屏幕视频的内容将消失。  解锁主机设备屏幕以自动恢复屏幕视频。


<!-- ====================================================================== -->
## <a name="known-issues"></a>已知问题

"**元素"工具**中的"事件侦听器 **"窗格在**版本 1903 Windows 10为空。  该团队计划在服务更新中**** 修复事件侦听器窗格，以Windows 10版本 1903。

在**版本** 1903 上 **，**"应用程序"面板Windows 10为空。  该团队计划将服务更新中的 **"Cookie**"窗格修复为Windows 10版本 1903。

审核**工具**、**3D 视图**工具、设置 中的"模拟设备******"** 部分以及"元素"工具中的"辅助功能"树窗格**** 当前未按预期工作。****  该团队计划在未来更新中修复列出的Microsoft Edge。

当你远程调试时，文件资源管理器不会从源工具中的 DevTools 或**安全**面板中启动。****  该团队计划在未来更新中修复Microsoft Edge。
