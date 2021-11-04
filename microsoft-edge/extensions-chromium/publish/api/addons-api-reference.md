---
description: 加载项 API 参考，适用于 REST 终结点，用于自动发布提交到加载项网站的加载项Microsoft Edge更新。
title: Microsoft Edge加载项 API 参考
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/19/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员， 加载项 api， 发布 api
ms.openlocfilehash: b0eddd3ae769942129f03abe510c2d5b25ca011d
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12157290"
---
# <a name="microsoft-edge-add-ons-api-reference-under-development"></a>Microsoft Edge正在开发 (加载项 API) 

> [!NOTE]
> 本文是一个请求注释。  Microsoft Edge加载项 API 尚无法进行测试，并且合作伙伴中心尚未提供"发布 API"页。  加载项MICROSOFT EDGE API 正在积极开发中，路线图根据市场变化和客户反馈不断发展。  此处列出的计划并不详尽，可能会发生变化。

这是加载项 API 的 REST Microsoft Edge引用。  此 API 可自动发布已提交到加载项网站的Microsoft Edge更新。

有关概述，请导航到["使用Microsoft Edge加载项 API"。](using-addons-api.md)


<!-- ====================================================================== -->
## <a name="get-the-list-of-products"></a>获取产品列表

获取属于该帐户的所有产品的列表。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `GET` | `/products` |

#### <a name="uri-parameters"></a>URI 参数

无。

#### <a name="request-headers"></a>请求标头

* 必需。  `Authorization: Bearer <auth token>`

#### <a name="request-body"></a>请求正文

无。

### <a name="response"></a>响应

该响应包括一个产品列表，其中包含每个产品的详细信息。  此响应的模板如下所示。

```json
[
    {
        "id": "<productID1>",
        "name": "<Name of Product 1>",
        "status": "In review",
        "lastUpdatedDate": "7/19/2021"
    },
    {
        "id": "<productID2>",
        "name": "<Name of Product 2>",
        "status": "In the store",
        "lastUpdatedDate": "5/21/2021"
    }
]
```

对于产品的第一个版本，状态字段具有以下值：
*  在草稿中
*  正在审阅
*  在应用商店中，或失败

对于后续提交，你将收到以下任一值：
*  正在审阅
*  在应用商店中，或失败

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 200 | 请求正常 |
| 4XX | 有关更多详细信息，请参阅 [错误代码](#error-codes)。 |
| 5XX | 有关更多详细信息，请参阅 [错误代码](#error-codes)。 |


<!-- ====================================================================== -->
## <a name="upload-a-package-to-update-an-existing-submission"></a>Upload程序包以更新现有提交

上载程序包以更新加载项产品的现有草稿提交。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `PUT` | `/products/{productID}/submissions/draft/package` |

#### <a name="uri-parameters"></a>URI 参数

| URI 参数 | 描述 |
|---|---|
| `productID` | 必需。  必须将程序包上载到的产品的产品 ID。 |

#### <a name="request-headers"></a>请求标头

*  必需。  `Authorization: Bearer <auth token>`

*  必需。  `Content-Type: application/zip`

#### <a name="request-body"></a>请求正文

* `<Zip package>`

### <a name="response"></a>响应

#### <a name="response-headers"></a>响应头

*  地点： `/products/{productID}/submissions/draft/package/operations/{operationID}`

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 202 | 请求已接受处理，但处理未完成。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |


<!-- ====================================================================== -->
## <a name="check-the-status-of-a-package-upload"></a>检查程序包上载的状态

获取程序包上载的状态。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `GET` | `/products/{productID}/submissions/draft/package/operations/{operationID}` |

#### <a name="uri-parameters"></a>URI 参数

| URI 参数 | 描述 |
|---|---|
| `operationID` | 必需。  上一步中提交的上传请求的操作 ID。  此信息在响应标头中提供。

#### <a name="request-headers"></a>请求标头

* 必需。  `Authorization: Bearer <auth token>`

#### <a name="request-body"></a>请求正文

无。

### <a name="response"></a>响应

对于不同的方案，有几个响应。

#### <a name="response-when-the-operation-is-still-in-progress"></a>操作正在进行时的响应

```json
{
    "id": "{operationID}",
    "status": "IN-PROGRESS",
    "message": "The package upload is in progress. Please check the status after some time."
}
```

#### <a name="response-when-the-operation-succeeds"></a>操作成功时的响应

```json
{
    "id": "{operationID}",
    "status": "SUCCESS",
    "message": "Package upload successfully completed. Please proceed with publishing."
}
```

#### <a name="response-when-the-operation-fails-with-errors"></a>操作失败但出现错误时的响应

```json
{
    "id": "{operationID}",
    "status": "FAILED",
    "message": "The package upload failed. Please fix the errors and make the request again.",
    "errors": [
       {
           "id": "MANIFEST_FILE_MISSING",
           "message": "Zip file must contain a manifest.json file."
       },
       {
           "id": "SIZE_LIMIT_EXCEEDED",
           "message": "Zip file size must not exceed 500MB."
       }
    ]
}
```

#### <a name="response-headers"></a>响应头

无。

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 200 | 请求正常。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |


<!-- ====================================================================== -->
## <a name="publish-the-product-draft-submission"></a>发布产品草稿提交

将产品的当前草稿发布到Microsoft Edge加载项。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `POST` | `/products/{productID}/submissions` |

#### <a name="uri-parameters"></a>URI 参数


| URI 参数 | 描述 |
|---|---|
| `productID` | 必需。  必须发布其草稿的产品的产品 ID。 |

#### <a name="request-headers"></a>请求标头

* 必需。  `Authorization: Bearer <auth token>`

#### <a name="request-body"></a>请求正文

`<Notes for certification>`，采用纯文本格式。

### <a name="response"></a>响应

#### <a name="response-headers"></a>响应头

* 地点： `/products/{productID}/submissions/operations/{operationID}`

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 202 | 请求已接受处理，但处理未完成。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |


<!-- ====================================================================== -->
## <a name="check-the-publishing-status"></a>检查发布状态

检查发布操作的状态。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `GET` | `/products/{productID}/submissions/operations/{operationID}` |

#### <a name="uri-parameters"></a>URI 参数

无。

#### <a name="request-headers"></a>请求标头

* 必需。  `Authorization: Bearer <auth token>`

#### <a name="request-body"></a>请求正文

无。

### <a name="response"></a>响应

可以在 `GET` 以下方案中调用操作状态 API。  在所有有效的方案中， `200 OK` 将返回 ，并返回不同的状态消息。

#### <a name="response-when-there-is-nothing-new-to-be-published"></a>没有要发布的新增功能时的响应

```json
{
    "id": "{operationID}",
    "status": "NOTHING-TO-PUBLISH",
    "message": "There is no draft available to publish. Please update the draft before publishing."
}
```

#### <a name="response-when-there-is-an-in-review-submission-for-the-same-product"></a>当同一产品有评价中提交时的响应

```json
{
    "id": "{operationID}",
    "status": "CONFLICT",
    "message": "There is another in-review submission for this product. Please wait for that submission to be completed before triggering a new publish."
}
```

#### <a name="response-when-the-publish-call-succeeds"></a>发布调用成功时的响应

```json
{
    "id": "{operationID}",
    "status": "IN-REVIEW",
    "message": "The draft has been successfully submitted and is in review. The review may take up to 7 business days."
}
```

#### <a name="response-when-the-publish-call-fails-with-an-irrecoverable-failure"></a>发布调用失败且无法恢复失败时的响应

```json
{
    "id": "{operationID}",
    "status": "FAILED",
    "message": "The operation failed due to an unknown error. Please re-trigger the publish call."
}
```

#### <a name="response-headers"></a>响应头

无。

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 200 | 请求正常。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |


<!-- ====================================================================== -->
## <a name="error-codes"></a>错误代码

下面列出了常见错误代码和可能的原因。  对于完整列表，导航到 [合作伙伴中心 REST 错误代码](/partner-center/develop/error-codes) 或 [HTTP 状态代码列表](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)。

### <a name="4xx-client-error"></a>4xx：客户端错误

| 邮件 | 描述 | 示例方案 |
|---|---|---|
| 400 错误的请求 | 服务器无法理解该请求。 | 正文中没有 (zip) 包。  或者 `Content-Type` ，标头缺失或其值不正确。 |
| 401 未经授权 | 请求页面需要授权。 | 身份验证令牌缺失、过期或无效。 |
| 404 未找到 | 服务器找不到请求的页面。 | 指定 `productID` `operationID` 或无效，或不属于正在提出请求的开发人员。 |
| 408 请求超时 | 请求所等待的时间比服务器准备等待的时间长。 | 上传程序包时存在超时。 |
| 429 请求过多 | 用户发送的请求过多。 | 发送的请求过多且受到限制。 |

### <a name="5xx-server-error"></a>5xx：服务器错误

| 邮件  | 描述  | 示例方案 |
|---|---|---|
| 500 内部服务器错误 | 请求未完成。 | 服务器遇到意外情况。 |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用Microsoft Edge加载项 API](using-addons-api.md)
