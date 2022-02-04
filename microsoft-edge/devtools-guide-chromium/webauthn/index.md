---
title: 模拟身份验证器并调试 WebAuthn
description: 在 DevTools 中模拟验证器和调试 WebAuthn。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 05/04/2021
---
# <a name="emulate-authenticators-and-debug-webauthn"></a>模拟身份验证器并调试 WebAuthn

<!--todo: remove notice at bottom, or add notice here?-->

使用 Microsoft Edge **DevTools 中的 WebAuthn** 工具创建基于软件的虚拟验证器并与之交互，而不是使用物理验证器在网站或应用中调试 Web 身份验证。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

Web 身份验证 API 规范是开始使用 [Web 身份验证的一个很好的位置](https://w3c.github.io/webauthn)。


<!-- ====================================================================== -->
## <a name="set-up-the-webauthn-tool"></a>设置 WebAuthn 工具

1. 转到使用 WebAuthn 的网页。  例如，在新的浏览器窗口或选项卡中打开以下演示 [webauthndemo.appspot.com](https://webauthndemo.appspot.com)。

1. 登录到网站。

1. [打开 DevTools](../open/index.md)。

1. 若要打开 **WebAuthn** 工具，请选择"自定义和控制 **DevTools** `...` 工具" () **">工具** > **""WebAuthn"**。

   :::image type="content" source="../media/webauthn-webauthn-tab.msft.png" alt-text="WebAuthn 工具。" lightbox="../media/webauthn-webauthn-tab.msft.png":::

1. 在 **WebAuthn 工具** 中，选中" **启用虚拟验证器环境"** 复选框。  将显示名为" **新建验证器"** 的新节：

   :::image type="content" source="../media/webauthn-enable-virtual-auth.msft.png" alt-text="启用虚拟验证器环境。" lightbox="../media/webauthn-enable-virtual-auth.msft.png":::

1. 在" **新建验证器** "部分，配置以下选项：

    | 选项 | Value | 详细信息 |
    |:--- |:--- |:--- |
    | `Protocol` | [ctap2](https://fidoalliance.org/specs/fido-v2.0-id-20180227/fido-client-to-authenticator-protocol-v2.0-id-20180227.html) 或 [u2f](https://fidoalliance.org/specs/fido-u2f-v1.2-ps-20170411/fido-u2f-overview-v1.2-ps-20170411.html) | 虚拟验证器用于编码和解码的协议 |
    | `Transport` |   `usb`、 `nfc`、 `ble`、 或 `internal` | 虚拟验证器模拟所选传输以便与客户端通信，以获取特定凭据的断言。  请参阅[Authenticator传输枚举](https://w3c.github.io/webauthn#enum-transport) |
    |  `Supports resident keys` | 使用复选框 (或) 或关闭复选框 | 如果 Web 应用依赖常驻密钥或 (客户端可发现凭据，请) 。  请参阅 [Resident Key Requirement 枚举](https://w3c.github.io/webauthn#enum-residentKeyRequirement)。 |
    | `Supports user verification` | 使用复选框 (或) 或关闭复选框 | 如果 Web 应用依赖使用手势形式（如触摸和引脚代码、密码输入或生物识别识别）的本地授权，则打开。  请参阅 [用户验证](https://w3c.github.io/webauthn#user-verification) |

1. 单击“添加”**** 按钮。

1. 将显示新创建的验证器的新部分：

   :::image type="content" source="../media/webauthn-authenticator.msft.png" alt-text="Authenticator。" lightbox="../media/webauthn-authenticator.msft.png":::

The **Authenticator** section includes a **Credentials** table.  在将凭据注册到验证器之前，该表为空：

:::image type="content" source="../media/webauthn-no-cred.msft.png" alt-text="无凭据。" lightbox="../media/webauthn-no-cred.msft.png":::


<!-- ====================================================================== -->
## <a name="register-a-new-credential"></a>注册新凭据

注册新凭据：

1. 在演示网站上，单击 **"注册新凭据"**。

1. 此时，新的凭据将添加到 WebAuthn 工具中的 **Credentials** 表中：

   :::image type="content" source="../media/webauthn-view-cred.msft.png" alt-text="查看凭据。" lightbox="../media/webauthn-view-cred.msft.png":::

在演示网站上，单击"验证 **"** 按钮。  确认"[凭据"表中的](https://w3c.github.io/webauthn/#sctn-sign-counter)凭据的 Sign Count 增加了 **** 1，这表示 [authenticatorGetAssertion](https://w3c.github.io/webauthn#authenticatorgetassertion) 操作成功。

有关注册新凭据时 [Web 身份验证 API](https://w3c.github.io/webauthn) 正在执行哪些操作的信息，请参阅 [创建新的凭据](https://w3c.github.io/webauthn#sctn-createCredential)。


<!-- ====================================================================== -->
## <a name="export-and-remove-credentials"></a>导出和删除凭据

若要导出或删除凭据，请单击"导出**或删除****"** 按钮。

:::image type="content" source="../media/webauthn-export-remove.msft.png" alt-text="导出或删除凭据。" lightbox="../media/webauthn-export-remove.msft.png":::


<!-- ====================================================================== -->
## <a name="rename-an-authenticator"></a>重命名验证器

重命名验证器：

1. 在验证器名称旁边，单击"编辑 **"** 按钮。

1. 编辑名称，然后按 **Enter** 保存更改。

:::image type="content" source="../media/webauthn-rename.msft.png" alt-text="重命名验证器。" lightbox="../media/webauthn-rename.msft.png":::


<!-- ====================================================================== -->
## <a name="set-the-active-authenticator"></a>设置活动验证器

将自动激活新创建的验证器。  若要使用另一个虚拟验证器，请单击验证器旁边的 **"** 活动"单选按钮。

DevTools 在任意时间点仅支持一个活动的虚拟验证器。  如果删除活动验证器，则不会自动激活另一个验证器。

:::image type="content" source="../media/webauthn-set-active.msft.png" alt-text="设置活动验证器。" lightbox="../media/webauthn-set-active.msft.png":::


<!-- ====================================================================== -->
## <a name="remove-a-virtual-authenticator"></a>删除虚拟验证器

若要删除虚拟验证器，请在验证器旁边单击"删除 **"** 按钮。

:::image type="content" source="../media/webauthn-remove-authenticator.msft.png" alt-text="删除验证器。" lightbox="../media/webauthn-remove-authenticator.msft.png":::


<!--todo: remove this notice, or add notice at top?-->

<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/webauthn/index)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可协议。](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
本作品根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)获得许可。
