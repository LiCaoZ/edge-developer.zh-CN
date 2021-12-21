---
title: 模拟验证器并调试 WebAuthn
description: 在 DevTools 中模拟验证器和调试 WebAuthn。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.date: 05/04/2021
ms.openlocfilehash: 263e57315fc17548277f36019caff346ace39d66
ms.sourcegitcommit: 6fa0ef440a4e4565a2055dc2742d5d1bf8744939
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2021
ms.locfileid: "12284208"
---
# <a name="emulate-authenticators-and-debug-webauthn"></a>模拟验证器并调试 WebAuthn

<!--todo: remove notice at bottom, or add notice here?-->

使用 Microsoft Edge DevTools 中的**WebAuthn**工具创建基于软件的虚拟验证器并与之交互，而不是使用物理验证器在网站或应用中调试 Web 身份验证。


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

Web 身份验证 API 规范是开始使用 [Web 身份验证的一个很好的位置](https://w3c.github.io/webauthn)。


<!-- ====================================================================== -->
## <a name="set-up-the-webauthn-tool"></a>设置 WebAuthn 工具

1.  导航到使用 WebAuthn 的网页，如以下演示网站。

    [webauthndemo.appspot.com](https://webauthndemo.appspot.com)

1.  登录到网站。
1.  [打开 DevTools](../open/index.md)。
1.  若要打开**WebAuthn**工具，请选择"自定义和控制**开发人员**工具" () "> `...` ****  >  **WebAuthn"图标**。

    :::image type="complex" source="../media/webauthn-webauthn-tab.msft.png" alt-text="WebAuthn 工具" lightbox="../media/webauthn-webauthn-tab.msft.png":::
       **WebAuthn** 工具
    :::image-end:::

1.  在 **WebAuthn 工具** 中，打开" **启用虚拟验证器环境"** 复选框。
1.  启用后，将显示名为 **"新建验证器"** 的新节。

    :::image type="complex" source="../media/webauthn-enable-virtual-auth.msft.png" alt-text="启用虚拟验证器环境" lightbox="../media/webauthn-enable-virtual-auth.msft.png":::
        **启用虚拟验证器环境**
    :::image-end:::

1.  在" **新建验证器"** 部分，配置以下选项。

    | 选项 | 值 | 详细信息 |
    |:--- |:--- |:--- |
    | `Protocol` | [ctap2](https://fidoalliance.org/specs/fido-v2.0-id-20180227/fido-client-to-authenticator-protocol-v2.0-id-20180227.html) 或 [u2f](https://fidoalliance.org/specs/fido-u2f-v1.2-ps-20170411/fido-u2f-overview-v1.2-ps-20170411.html) | 虚拟验证器用于编码和解码的协议 |
    | `Transport` |   `usb``nfc` `ble` 、、、 或 `internal` | 虚拟验证器模拟所选传输以便与客户端通信，以获取特定凭据的断言。  有关详细信息，请导航到Authenticator[枚举](https://w3c.github.io/webauthn#enum-transport) |
    |  `Supports resident keys` | 使用复选框 (或) 或关闭" | 如果 Web 应用依赖于常驻密钥， (也称为客户端可发现凭据) 。  有关详细信息，请导航到 [Resident Key Requirement 枚举](https://w3c.github.io/webauthn#enum-residentKeyRequirement)。 |
    | `Supports user verification` | 使用复选框 (或) 或关闭" | 如果 Web 应用依赖使用手势形式（如触摸和引脚代码、密码输入或生物识别识别）的本地授权，则打开。  有关详细信息，请导航到" [用户验证"](https://w3c.github.io/webauthn#user-verification) |

1.  选择“添加”按钮****。
1.  将显示新创建的验证器的新部分。

    :::image type="complex" source="../media/webauthn-authenticator.msft.png" alt-text="Authenticator" lightbox="../media/webauthn-authenticator.msft.png":::
       Authenticator
    :::image-end:::

The **Authenticator** section includes a **Credentials** table.  在将凭据注册到验证器之前，该表为空。

:::image type="complex" source="../media/webauthn-no-cred.msft.png" alt-text="无凭据" lightbox="../media/webauthn-no-cred.msft.png":::
   无凭据
:::image-end:::


<!-- ====================================================================== -->
## <a name="register-a-new-credential"></a>注册新凭据

若要注册新凭据，请完成以下步骤。  有关注册新凭据时[Web 身份验证 API](https://w3c.github.io/webauthn)正在执行哪些操作的信息，请导航到"[新建凭据"。](https://w3c.github.io/webauthn#sctn-createCredential)

1.  在演示网站上，选择"**注册新凭据"。**
1.  此时，新的凭据将添加到 WebAuthn 工具中的 **Credentials** 表中。

    :::image type="complex" source="../media/webauthn-view-cred.msft.png" alt-text="查看凭据" lightbox="../media/webauthn-view-cred.msft.png":::
       查看凭据
    :::image-end:::

在演示网站上，选择"验证 **"** 按钮。  确认"[凭据"表中的](https://w3c.github.io/webauthn/#sctn-sign-counter)凭据的 Sign **** Count 增加了 1，这表示[authenticatorGetAssertion](https://w3c.github.io/webauthn#authenticatorgetassertion)操作成功。


<!-- ====================================================================== -->
## <a name="export-and-remove-credentials"></a>导出和删除凭据

若要导出或删除凭据，请选择"导出 **"** 或" **删除"** 按钮。

:::image type="complex" source="../media/webauthn-export-remove.msft.png" alt-text="导出或删除凭据" lightbox="../media/webauthn-export-remove.msft.png":::
   导出或删除凭据
:::image-end:::


<!-- ====================================================================== -->
## <a name="rename-an-authenticator"></a>重命名验证器

若要重命名验证器，请完成以下步骤。

1.  在验证器名称旁边，选择"编辑 **"** 按钮。
1.  编辑名称，然后选择 **Enter** 以保存更改。

:::image type="complex" source="../media/webauthn-rename.msft.png" alt-text="重命名验证器" lightbox="../media/webauthn-rename.msft.png":::
   重命名验证器
:::image-end:::


<!-- ====================================================================== -->
## <a name="set-the-active-authenticator"></a>设置活动验证器

将自动激活新创建的验证器。  若要使用另一个虚拟验证器，请选择验证器旁边的 **"** 活动"单选按钮。

> [!NOTE]
> DevTools 在任意时间点仅支持一个活动的虚拟验证器。  如果删除活动验证器，则不会自动激活另一个验证器。

:::image type="complex" source="../media/webauthn-set-active.msft.png" alt-text="设置活动验证器" lightbox="../media/webauthn-set-active.msft.png":::
   设置活动验证器
:::image-end:::


<!-- ====================================================================== -->
## <a name="remove-a-virtual-authenticator"></a>删除虚拟验证器

若要删除虚拟验证器，请选择验证器旁边的"删除 **"** 按钮。

:::image type="complex" source="../media/webauthn-remove-authenticator.msft.png" alt-text="删除验证器" lightbox="../media/webauthn-remove-authenticator.msft.png":::
   删除验证器
:::image-end:::


<!--todo: remove this notice, or add notice at top?-->

<!-- ====================================================================== -->
> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的](https://developers.google.com/terms/site-policies)作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ](https://creativecommons.org/licenses/by/4.0)中描述的条款使用。
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/webauthn/index)，并由 [Jecelyn Yeen](https://developers.google.com/web/resources/contributors#jecelyn-yeen)  \（开发人员支持者，Chrome DevTools\）制作。

[![知识共享许可](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0) 本作品根据[知识共享署名 4.0 国际许可](https://creativecommons.org/licenses/by/4.0)获得许可。
