---
title: 正在从网站检测 Microsoft Edge
description: 如何使用客户端Microsoft Edge和User-Agent字符串检测User-Agent数据。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 12/09/2021
ms.openlocfilehash: c5aa13fc0eacedf389907ed0814b320fd381cf4a
ms.sourcegitcommit: accae5bfd503ec9b17fd69ddcf373bf6ba707928
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2022
ms.locfileid: "12463979"
---
# <a name="detecting-microsoft-edge-from-your-website"></a>正在从网站检测 Microsoft Edge

<!-- restricted lexicon to use:
User-Agent Client Hints
User-Agent string
user agent string - not used
-->

Microsoft Edge网站检索用户代理信息。  您可以使用用户代理信息为每个用户的浏览器正确呈现网页。  浏览器为网站提供用于检测浏览器信息（如品牌、版本号和主机操作系统）的机制。

*  **用户代理客户端提示** 是检索浏览器信息的改进机制。  请参阅 [下面的用户代理客户端](#user-agent-client-hints)提示。

*  **用户代理字符串是** 旧版的;它们已过时，并且具有导致网站兼容性问题的历史记录。  请参阅 [下面的用户代理](#user-agent-strings)字符串。

你可能希望基于用户的浏览器为用户提供不同的体验。  例如，如果包含有关如何配置浏览器或Microsoft Edge浏览器以用于您的网站的步骤，您可能需要检测浏览器，然后显示相应的内容。

浏览器检测机制：

| 机制 | 服务器端 | 客户端 |
|:--- |:--- |:--- |
| **用户代理客户端提示 (** 建议)  | `Sec-CH-UA` HTTPS 标头 | `navigator.userAgentData` JavaScript 方法 |
| **用户代理字符串 (** 旧版)  | `User-Agent` HTTPS 标头 | `navigator.userAgent` JavaScript 方法 |


<!-- ====================================================================== -->
## <a name="feature-detection"></a>功能检测

Microsoft [建议尽可能检测](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) 浏览器是否支持功能，而不是检测浏览器。

如果必须检测浏览器，Microsoft 建议User-Agent客户端提示，如下所示 [，并结合功能检测](#combine-user-agent-client-hints-with-feature-detection)。


<!-- ====================================================================== -->
## <a name="user-agent-client-hints"></a>User-Agent客户端提示

Microsoft Edge版本 90 User-Agent客户端提示。

User-Agent客户端提示是访问浏览器信息（如浏览器名称、版本号、平台等）的更简洁、更隐私的方式。 很快User-Agent浏览器将冻结和弃用该字符串。 例如，Chrome 平台状态网站描述功能 [：减少用户代理字符串信息中的更改](https://www.chromestatus.com/feature/5704553745874944)。

当你User-Agent时，使用客户端提示：
- 确定新的浏览器活动是否来自预期用户。
- 如果用户是此网站的新用户，请自定义提示或说明。

请勿使用客户端User-Agent提示：
- 阻止 *不受支持的* 浏览器。
- 限制对网站上功能的访问。

有关详细信息，请参阅 [W3C 组草稿Community：User-Agent客户端提示中的规范](https://wicg.github.io/ua-client-hints/)。

### <a name="user-agent-client-hints-https-header"></a>User-Agent客户端提示 HTTPS 标头

当Microsoft Edge向服务器发送 HTTPS 请求时，它会发送一组低User-Agent客户端提示标头。 有关详细信息，请参阅低 [向异性提示表](https://wicg.github.io/client-hints-infrastructure/#low-entropy-table)。 如果服务器需要有关浏览器的更具体的信息，则其响应包括标头 `Accept-CH` 。 该响应标头的值是服务器从浏览器需要的所有客户端提示请求标头的逗号分隔列表，例如 `Accept-CH: Sec-CH-UA-Full-Version,Sec-CH-UA-Platform-Version`。 下一Microsoft Edge HTTPS 请求将包含指定的客户端User-Agent标头。

默认情况下，Microsoft Edge`Sec-CH-UA`发送以下格式的 、 `Sec-CH-UA-Mobile``Sec-CH-UA-Platform` 和 请求标头。

```https
Sec-CH-UA: "Chromium";v="92", "Microsoft Edge";v="92", "Placeholder;Browser Brand";v="99"
Sec-CH-UA-Mobile: ?0
Sec-CH-UA-Platform: "Windows"
```

下表显示了具有示例值的所有可用提示请求标头。

| User-Agent请求标头 | 响应User-Agent的示例 |
|:--- |:--- |
| `Sec-CH-UA` | `"Chromium";v="91", "Microsoft Edge";v="91", "GREASE";v="99"` |
| `Sec-CH-UA-Mobile` | `?0` |
| `Sec-CH-UA-Full-Version` | `91.0.866.0` |
| `Sec-CH-UA-Platform` | `Windows` |
| `Sec-CH-UA-Platform-Version` | `10.0` |
| `Sec-CH-UA-Arch` | `x86` |
| `Sec-CH-UA-Bitness` | `64` |
| `Sec-CH-UA-Model` | `Surface Pro` |

> [!NOTE]
> User-Agent客户端提示仅在使用 的安全连接上发送 `HTTPS`。

### <a name="user-agent-client-hints-javascript-api"></a>User-Agent客户端提示 JavaScript API

可以在客户端User-Agent JavaScript 访问客户端提示。 调用默认 时 `navigator.userAgentData`，它将返回以下响应。

```JSON
{
  "brands": [
    {
      "brand": "Chromium",
      "version":"91"
    },
    {
      "brand": "Microsoft Edge",
      "version":"91"
    },
    {
      "brand": "GREASE",
      "version":"99"
    }
  ],
  "mobile": false 
}
```

Microsoft Edge品牌值`GREASE`会随着时间而改变。 它会阻止网站在尝试检测产品版本时匹配整个品牌Microsoft Edge。

若要发送请求获取更多详细信息（如 ） `platform`，请使用以下代码：

```javascript
navigator.userAgentData.getHighEntropyValues(
   ["architecture", "model", "platform", "platformVersion", "uaFullVersion"])
      .then(ua => { console.log(ua) });
```

该响应具有以下格式：

```javascript
{architecture: "x86",
   model: "",
   platform: "Windows",
   platformVersion: "10.0",
   uaFullVersion: "92.0.866.0"}
```

有关详细信息，请参阅 [getHighEntropyValues () ](https://wicg.github.io/ua-client-hints#getHighEntropyValues)。

### <a name="platformversion-hint"></a>platformVersion 提示

标头中的操作系统版本`User-Agent`令牌尚未针对更新，Windows 11报告 `Windows NT 10.0`。

若要区分Windows 10和Windows 11，请请求`platformVersion`客户端提示Microsoft Edge。 值之间以及包括`1.0.0``12.0.0`和表示Windows 10版本，`14.0.0`而值或更高版本表示版本Windows 11。


### <a name="combine-user-agent-client-hints-with-feature-detection"></a>将User-Agent客户端提示与功能检测相结合

将User-Agent客户端提示 [与功能检测](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) 相结合是提供兼容 Web 内容的一种有效方法。 Microsoft 建议使用此模式：
* 提高代码可维护性。
* 减少代码错误。
* 减少代码中断（由对字符串User-Agent更改。

如果需要检查与 Chrome 类似浏览器，Microsoft `Chromium`建议检测 ，这是为浏览器Microsoft Edge。

使用此方法验证品牌，`Chromium`并针对所有受影响的基于Chromium应用检测：

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

如果您不使用功能[检测，](https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection)请不要使用基于 Chromium 的已知浏览器硬编码列表进行验证。 硬编码浏览器名称的示例包括 和 `Microsoft Edge` `Google Chrome`。  功能检测可能不可用，因为必须Chromium修复更高版本中的错误，并且受影响的浏览器难以检测。


<!-- ====================================================================== -->
## <a name="user-agent-strings"></a>User-Agent字符串

User-Agent字符串已过时，并且具有导致网站兼容性问题的长历史记录。

如果可能，Microsoft 建议尽可能Microsoft Edge基于字符串的浏览器检测User-Agent逻辑。 如果你有一个很好的理由来检测浏览器，Microsoft Edge建议将[用户代理](#user-agent-client-hints)客户端提示用作主要检测逻辑。 [用户代理客户端提示](#user-agent-client-hints) 还降低了浏览器检测代码的复杂性。

对于旧引用，以下信息包含在User-Agent字符串中。

在Windows，`User-Agent`HTTP 请求标头包括：

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64)  
AppleWebKit/537.36 (KHTML, like Gecko)  
Chrome/90.0.4430.85  
Safari/537.36  
Edg/90.0.818.46
```

在 Android 上， `User-Agent` HTTP 请求标头包括：

```
Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N)  
AppleWebKit/537.36 (KHTML, like Gecko)  
Chrome/90.0.4430.85  
Mobile Safari/537.36  
EdgA/90.0.818.46
```

来自 方法的响应 `navigator.userAgent` 值采用以下格式：

```javascript
"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4501.0 Safari/537.36 Edg/91.0.866.0"
```

平台标识符根据操作系统发生变化，并且版本号会随着时间的推移而递增。 格式与用户代理Chromium`Edg`，末尾添加新令牌。 Microsoft 选择令牌`Edg`以避免`Edge`由字符串引起的兼容性问题，字符串以前用于基于 EdgeHTML Microsoft Edge旧版浏览器。 令牌 `Edg` 还 [与用于](https://blogs.windows.com/msedgedev/2017/10/05/microsoft-edge-ios-android-developer) iOS 和 Android 的现有令牌一致。

### <a name="microsoft-edge-version-increment-change"></a>Microsoft Edge版本增量更改

Microsoft Edge的主要版本号即将`Edg/99`从两位数字（如 ）递增到三位数字（如 ）。`Edg/100` 网站所有者应确保其User-Agent逻辑可靠且能够正常工作。


<!-- ====================================================================== -->
## <a name="identifiers-for-microsoft-edge-on-various-platforms"></a>各种平台上Microsoft Edge标识符

在桌面操作系统上，Microsoft Edge`Edg`字符串中的标记通常User-Agent标识。  但是，某些设备Microsoft Edge使用不同的令牌，如下所示：

| 平台 | 标识符令牌 |
|:--- |:--- |
| 桌面 (Windows/Mac/Linux)  | `Edg` |
| iPhone/iPad | `EdgiOS` |
| Android (Mobile/tablet)  | `EdgA`|

Microsoft Edge 旧版不再支持。 有关详细信息[，Microsoft Edge 旧版](#microsoft-edge-legacy)部分。

<!-- ====================================================================== -->
## <a name="map-the-user-agent-string-to-an-expanded-browser-name"></a>将User-Agent字符串映射到扩展的浏览器名称

将User-Agent字符串令牌映射到要用于代码的可读浏览器名称。 这种做法在 Web 上很常见。 `Edg`将新令牌映射到浏览器名称时，Microsoft 建议使用与旧版 Microsoft EdgeHTML 浏览器不同的名称，以避免意外应用不适用于基于 Chromium 的浏览器的旧解决方法。


<!-- ====================================================================== -->
## <a name="user-agent-overrides"></a>User-Agent替代

有时，网站无法识别Microsoft Edge代理。 因此，一组网站功能可能无法正常运行。 当 Microsoft 收到问题类型通知时，Microsoft 会 (网站所有者) 并通知你更新的用户代理。

可能需要更多时间来更新和测试网站的用户代理检测逻辑，以解决 Microsoft 报告的问题。 为了最大限度地提高用户的兼容性，Microsoft Edge Beta和稳定渠道使用用户代理替代列表。 更新网站时，请使用用户代理替代。 用户代理替代列表由 Microsoft 提供。

替代指定要发送Microsoft Edge用户代理值，而不是指定特定网站的默认用户代理。 若要显示当前应用的用户代理覆盖列表，请执行以下操作：

1. 打开 Microsoft Edge Beta 或 Stable 渠道。

1. 转到 `edge://compat/useragent`。

Canary Microsoft Edge开发人员频道当前不会接收用户代理覆盖。 Canary Microsoft Edge开发人员频道提供的环境使用默认模式Microsoft Edge代理。 使用 Microsoft Edge Canary 和 Dev 渠道重现由默认用户代理导致Microsoft Edge问题。

若要关闭渠道或稳定渠道中的Microsoft Edge Beta覆盖：

1. 打开命令提示符。  例如，在"**搜索Windows输入 cmd**，然后选择命令**提示符**应用。

1. 复制以下代码：

    ```shell
    --disable-domain-action-user-agent-override
    ```

1. 使用Microsoft Edge代码运行应用，如下所示：

    ```shell
    {path/to/microsoft/edge.ext} --disable-domain-action-user-agent-override
    ```


<!-- ====================================================================== -->
## <a name="microsoft-edge-legacy"></a>Microsoft Edge 旧版

旧版浏览器注意事项：

*  不再Microsoft Edge 旧版浏览器。 请参阅博客文章新[Microsoft Edge替换Microsoft Edge 旧版](https://techcommunity.microsoft.com/t5/microsoft-365-blog/new-microsoft-edge-to-replace-microsoft-edge-legacy-with-april-s/ba-p/2114224)。

*  Microsoft Edge 旧版仅在 Windows 10 上可用。

*  在本文User-Agent的所有浏览器机制中，唯一支持的特定于浏览器的机制是Microsoft Edge 旧版字符串User-Agent机制。

*  User-Agent的字符串Microsoft Edge 旧版令牌`Edge`。

    字符串字符串的Microsoft Edge 旧版 User-Agent示例： `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.102 Safari/537.36 Edge/18.19582`


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

[使用用户代理客户端提示检测 Windows 11](/microsoft-edge/web-platform/how-to-detect-win11)
