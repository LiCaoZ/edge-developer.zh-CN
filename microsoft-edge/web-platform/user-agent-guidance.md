---
description: 本文介绍如何使用客户端Microsoft Edge和User-Agent字符串检测User-Agent数据。
title: 正在从网站检测 Microsoft Edge
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/22/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， 兼容性， Web 平台， 用户代理字符串， ua 字符串， ua 替代， 用户代理客户端提示， 用户代理客户端提示， ua 客户端提示， ua ch， 功能检测， 浏览器标识， 浏览器检测， 标头， https 标头， 检测 microsoft edge， 检测 Microsoft edge
ms.openlocfilehash: 7a56dafcc399baae453ff1de7822b5227b73cad7
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12155911"
---
# <a name="detecting-microsoft-edge-from-your-website"></a>正在从网站检测 Microsoft Edge

<!-- restricted lexicon to use:
User-Agent Client Hints
User-Agent string
user agent string - not used
-->

本文介绍Microsoft Edge检索用户代理信息的方法。

浏览器为网站提供用于检测浏览器信息（如品牌、版本号和主机操作系统）的机制。 旧版 [用户代理字符串](#user-agent-strings) 已过时，并且具有导致网站兼容性问题的历史记录。 新的 [用户代理客户端提示](#user-agent-client-hints) 是检索浏览器信息的改进机制。

你可能希望基于用户的浏览器为用户提供不同的体验。 例如，如果包含有关配置浏览器或Microsoft Edge浏览器以用于您的网站的步骤，您可能需要检测浏览器，然后显示相应的内容。

浏览器检测机制：

| 机制 | 服务器端 | 客户端 |
|:--- |:--- |:--- |
| **用户代理客户端提示 (** 推荐)  | `Sec-CH-UA` HTTPS 标头 | `navigator.userAgentData` JavaScript 方法 |
| **旧版用户代理 (** 代理)  | `User-Agent` HTTPS 标头 | `navigator.userAgent` JavaScript 方法 |


<!-- ====================================================================== -->
## <a name="feature-detection"></a>功能检测

Microsoft [建议尽可能检测](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) 浏览器是否支持功能，而不是检测浏览器。

如果必须检测浏览器，Microsoft 建议User-Agent客户端提示，如下所示。


<!-- ====================================================================== -->
## <a name="user-agent-client-hints"></a>User-Agent客户端提示

Microsoft Edge版本 90 User-Agent客户端提示。

User-Agent客户端提示是访问浏览器信息（如浏览器名称、版本号、平台等）的更简洁、更隐私的方式。 很快User-Agent浏览器将冻结和弃用该字符串。 例如，Chrome 平台状态网站描述功能 [： 减少用户代理字符串信息中的更改](https://www.chromestatus.com/feature/5704553745874944)。

当你User-Agent时，使用客户端提示：
- 确定新的浏览器活动是否来自预期用户。
- 如果用户是此网站的新用户，请自定义提示或说明。

请勿使用客户端User-Agent提示：
- 阻止 *不受支持的* 浏览器。
- 限制对网站上功能的访问。

有关详细信息，请导航到 W3C 组草稿Community[报告：User-Agent客户端提示"中的规范](https://wicg.github.io/ua-client-hints/)。

### <a name="user-agent-client-hints-https-header"></a>User-Agent客户端提示 HTTPS 标头

当Microsoft Edge向服务器发送 HTTPS 请求时，它会发送一组低向User-Agent客户端提示标头。 有关详细信息，请导航到低 [向异性提示表](https://wicg.github.io/client-hints-infrastructure/#low-entropy-table)。 如果服务器需要有关浏览器的更具体的信息，则其响应包括 `Accept-CH` 标头。 该响应标头的值是服务器从浏览器需要的所有客户端提示请求标头的逗号分隔列表，例如 `Accept-CH: Sec-CH-UA-Full-Version,Sec-CH-UA-Platform-Version` 。 下一Microsoft Edge HTTPS 请求将包含指定的客户端User-Agent标头。

默认情况下，Microsoft Edge发送以下格式的 、 和 `Sec-CH-UA` `Sec-CH-UA-Mobile` `Sec-CH-UA-Platform` 请求标头。

```https
Sec-CH-UA: "Chromium";v="92", "Microsoft Edge";v="92","Placeholder;Browser Brand";v="99"
Sec-CH-UA-Mobile: ?0
Sec-CH-UA-Platform: "Windows"
```

下表显示了具有示例值的所有可用提示请求标头。

| User-Agent请求标头 | 响应User-Agent的示例 |
|:--- |:--- |
| `Sec-CH-UA` | `"Chromium";v="91", "Microsoft Edge";v="91","GREASE";v="99"` |
| `Sec-CH-UA-Mobile` | `?0` |
| `Sec-CH-UA-Full-Version` | `91.0.866.0` |
| `Sec-CH-UA-Platform` | `Windows` |
| `Sec-CH-UA-Platform-Version` | `10.0` |
| `Sec-CH-UA-Arch` | `x86` |
| `Sec-CH-UA-Bitness` | `64` |
| `Sec-CH-UA-Model` | `Surface Pro` |

> [!NOTE]
> User-Agent客户端提示仅在使用 的安全连接上发送 `HTTPS` 。

### <a name="user-agent-client-hints-javascript-api"></a>User-Agent客户端提示 JavaScript API

可以在客户端User-Agent JavaScript 访问客户端提示。 调用默认 时 `navigator.userAgentData` ，它将返回以下响应。

```JSON
{ brands: [ {brand: "Chromium","version":"91"}, {brand: "Microsoft Edge","version":"91"}, {brand: "GREASE","version":"99"}, ]
mobile: false }
```

Microsoft Edge包括 `GREASE` 一个品牌值，该值会随着时间而改变。 它会阻止网站在尝试检测产品版本时匹配整个品牌Microsoft Edge。

若要请求更多详细信息（如 ）， `platform` 请使用以下代码。

以下代码段发送请求。

```javascript
navigator.userAgentData.getHighEntropyValues(
   ["architecture", "model", "platform", "platformVersion", "uaFullVersion"])
      .then(ua => { console.log(ua) });
```

接收以下响应。

```javascript
{architecture: "x86",
   model: "",
   platform: "Windows",
   platformVersion: "10.0",
   uaFullVersion: "92.0.866.0"}
```

有关详细信息，请导航到 [getHighEntropyValues () ](https://wicg.github.io/ua-client-hints#getHighEntropyValues)。

### <a name="platformversion-hint"></a>platformVersion 提示

标头中的操作系统版本令牌尚未更新，Windows 11 `User-Agent` 报告 `Windows NT 10.0` 。

若要区分 Windows 10 和 Windows 11，请请求 Microsoft Edge `platformVersion` 95 或更高版本中的客户端提示。 值介于 和 之间（包括 和 表示 Windows 10 版本，而 值或更高版本表示 `1.0.0` `12.0.0` `14.0.0` Windows 11。

### <a name="user-agent-client-hints-suggested-use"></a>User-Agent建议使用的客户端提示

将User-Agent客户端提示 [与功能检测](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) 相结合是提供兼容 Web 内容的一种有效方法。 Microsoft 建议使用此模式：
* 提高代码可维护性。
* 减少代码错误。
* 减少代码中断（由对字符串User-Agent更改。

如果你需要检查与 Chrome 类似浏览器，Microsoft 建议检测 ，这是为浏览器 `Chromium` Microsoft Edge。

使用此方法验证品牌，并针对所有受影响的基于Chromium `Chromium` 应用检测。

```javascript
function isChromium() {
    for (brand_version_pair of navigator.userAgentData.brands) {
        if (brand_version_pair.brand == "Chromium"){
            return true;
        }
    }
    return false;
}
```

使用上述方法可避免对特定索引的品牌进行硬编码检查。 品牌名称的显示顺序可能会随着时间的推移而更改。

如果您不使用功能[检测，](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection)请不要使用基于 Chromium 的已知浏览器的硬编码列表进行验证。 硬编码浏览器名称的示例包括 `Microsoft Edge` 和 `Google Chrome` 。  功能检测可能不可用，因为必须Chromium修复更高版本中的错误，并且受影响的浏览器难以检测。


<!-- ====================================================================== -->
## <a name="user-agent-strings"></a>User-Agent字符串

User-Agent字符串已过时，并且具有导致网站兼容性问题的长历史记录。

如果可能，Microsoft 建议尽可能Microsoft Edge基于字符串的浏览器User-Agent逻辑。 如果你有一个很好的理由来检测浏览器，Microsoft Edge建议将[用户代理](#user-agent-client-hints)客户端提示用作主要检测逻辑。 [用户代理客户端提示](#user-agent-client-hints) 还降低了浏览器检测代码的复杂性。

对于旧引用，以下格式用于User-Agent字符串。

在Windows上 `User-Agent` ，HTTP 请求标头采用以下格式。

```https
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36 Edg/90.0.818.46
```

在 Android 上 `User-Agent` ，HTTP 请求标头采用以下格式。

```https
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Mobile Safari/537.36 Edg/90.0.818.46
```

来自 方法的响应 `navigator.userAgent` 值采用以下格式。

```javascript
"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4501.0 Safari/537.36 Edg/91.0.866.0"
```

平台标识符根据操作系统发生变化，并且版本号会随着时间的推移而递增。 格式与用户代理Chromium，末尾添加新 `Edg` 令牌。 Microsoft 选择令牌以避免由字符串引起的兼容性问题，字符串以前用于基于 `Edg` `Edge` EdgeHTML Microsoft Edge旧版浏览器。 令牌 `Edg` 还与用于 iOS 和[](https://blogs.windows.com/msedgedev/2017/10/05/microsoft-edge-ios-android-developer)Android 的现有令牌一致。


<!-- ====================================================================== -->
## <a name="identifiers-for-microsoft-edge-on-various-platforms"></a>各种平台上Microsoft Edge标识符

在桌面操作系统上，Microsoft Edge字符串中的标记 `Edg` 通常User-Agent标识。  但是，某些设备Microsoft Edge使用不同的令牌，如下所示：


| 平台 | 标识符令牌 |
|:--- |:--- |
| 桌面 (Windows/Mac/Linux)  | `Edg` |
| iPhone/iPad | `EdgiOS` |
| Android (Mobile/tablet)  | `EdgA`|


<!-- ====================================================================== -->
## <a name="map-the-user-agent-string-to-an-expanded-browser-name"></a>将User-Agent字符串映射到扩展的浏览器名称


将User-Agent字符串令牌映射到要用于代码的可读浏览器名称。 这种做法在 Web 上很常见。 将新令牌映射到浏览器名称时，Microsoft 建议使用与旧版 Microsoft EdgeHTML 浏览器不同的名称，以避免意外应用不适用于基于 Chromium 的浏览器的旧解决方法。 `Edg`


<!-- ====================================================================== -->
## <a name="user-agent-overrides"></a>User-Agent替代

有时，网站无法识别Microsoft Edge代理。 因此，一组网站功能可能无法正常运行。 当 Microsoft 收到问题类型通知时，Microsoft 会 (网站所有者联系) 并通知你更新的用户代理。

可能需要更多时间来更新和测试网站的用户代理检测逻辑，以解决 Microsoft 报告的问题。 为了最大限度地提高用户的兼容性，Microsoft Edge Beta和稳定渠道使用用户代理替代列表。 更新网站时，请使用用户代理替代。 用户代理替代列表由 Microsoft 提供。

替代指定要发送Microsoft Edge用户代理值，而不是指定特定网站的默认用户代理。 若要显示当前应用的用户代理覆盖列表，请执行以下操作：
1. 打开 Microsoft Edge Beta 或 Stable 渠道。
1. 导航到 `edge://compat/useragent`。

Canary Microsoft Edge开发人员频道当前不会接收用户代理覆盖。 Canary Microsoft Edge开发人员频道提供的环境使用默认模式Microsoft Edge代理。 使用Microsoft Edge Canary 和 Dev 渠道重现由默认用户代理导致Microsoft Edge的问题。

若要在渠道或稳定渠道中Microsoft Edge Beta代理替代：

1. 打开命令提示符。  例如，在"**搜索Windows输入 cmd，** 然后选择命令**提示符**应用。

1. 复制以下代码段：

    ```shell
    --disable-domain-action-user-agent-override
    ```

1. 使用Microsoft Edge代码段运行应用程序，如下所示：

    ```shell
    {path/to/microsoft/edge.ext} --disable-domain-action-user-agent-override
    ```
