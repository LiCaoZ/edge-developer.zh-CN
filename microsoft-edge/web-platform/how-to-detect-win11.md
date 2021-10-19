---
description: 如何使用客户端Windows 10 Windows 11区分User-Agent和客户端提示
title: 使用Windows 11客户端User-Agent检测客户端提示
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/15/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， 兼容性， Web 平台， 用户代理字符串， ua 字符串， 用户代理客户端提示， 用户代理客户端提示， ua 客户端提示， ua ch， windows 11， win11， 检测 windows 11， windows 检测
ms.openlocfilehash: aea68e00c5376f49f8b82386b1e0c707f508ad47
ms.sourcegitcommit: 3dce4eececc6b998c604547174d56be5dd0bf45d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2021
ms.locfileid: "12100805"
---
# <a name="detecting-windows-11-using-user-agent-client-hints"></a>使用Windows 11客户端User-Agent检测客户端提示

<!--
Restrict the lexicon to these forms:
User-Agent string
user agent string
User-Agent Client Hints
user agent information
-->

网站可以使用从浏览器发送的用户代理信息检测品牌、版本、设备平台等。 网站有两种访问用户代理信息的方法：
*  User-Agent旧版 (字符串) 。
*  User-Agent客户端提示 (推荐) 。

有关这两种方法的详细信息，请参阅[检测Microsoft Edge中的内容](user-agent-guidance.md)。

从 Microsoft Edge 版本 94 和 Chrome 版本 95 开始，网站可以通过 User-Agent 客户端提示 (UA-CH) 区分 Windows 11 和 Windows 10 上的用户。 可以在以下 UA-CH 请求标头中找到此信息：

| 头字段 | 指示Windows 10 | 指示Windows 11 |
| --- | --- | --- |
| `Sec-CH-UA-Platform` | `Windows` | `Windows` |
| `Sec-CH-UA-Platform-Version` | 值介于 `1.0.0` 和 之间 `10.0.0` | `13.0.0` 及以上 |

User-Agent字符串不会进行更新以区分Windows 11和Windows 10。  我们不建议使用字符串User-Agent检索用户代理数据。  不支持客户端提示User-Agent将无法区分用户和Windows 11 Windows 10。


<!-- ====================================================================== -->
## <a name="browsers-that-support-user-agent-client-hints"></a>支持客户端提示User-Agent浏览器

下表显示哪些浏览器支持区分Windows 11和Windows 10。

| 浏览器 | 通过客户端提示User-Agent区别？ |
| --- | --- |
| Microsoft Edge 94 及以上 | 是 |
| Chrome 95 及以上 | 是 |
| Opera | 是 |
| Firefox | 否 |
| Internet Explorer 11 | 否 |


<!-- ====================================================================== -->
## <a name="sample-code-for-detecting-windows-11"></a>检测数据示例Windows 11

以下代码将检测Windows 11：

```javascript
navigator.userAgentData.getHighEntropyValues(["platformVersion"])
 .then(ua => {
   if (navigator.userAgentData.platform === "Windows") {
     const majorPlatformVersion = parseInt(ua.platformVersion.split('.')[0]);
     if (majorPlatformVersion >= 13) {
       console.log("Windows 11 or later");
      }
      else if (majorPlatformVersion > 0) {
        console.log("Windows 10");
      }
      else {
        console.log("Before Windows 10");
      }
   }
   else {
     console.log("Not running on Windows");
   }
 });

```


<!-- ====================================================================== -->
## <a name="detecting-specific-windows-versions"></a>检测特定Windows版本

若要检测特定版本的Windows，请使用客户端提示中的以下User-Agent `platformVersion` 值：

| 版本 | `platformVersion` |
| --- | --- | --- |
| Win7/8/8.1 | 0 |
| Win10 1507 | 1 |
| Win10 1511 | 2 |
| Win10 1607 | 3 |
| Win10 1703 | 4 |
| Win10 1709 | 5 |
| Win10 1803 | 6 |
| Win10 1809 | 7 |
| Win10 1903 | 8 |
| Win10 1909 | 8 |
| Win10 2004 | 10 |
| Win10 20H2 | 10 |
| Win10 21H1 | 10 |
| Win11 | 13+ |
