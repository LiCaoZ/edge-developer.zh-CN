---
title: Microsoft Edge 外接程序 API 参考 (在个人预览版中)
description: 加载项 API 参考，适用于 REST 终结点，用于自动发布提交到加载项网站的加载项Microsoft Edge更新。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/19/2021
ms.openlocfilehash: 9ec2739b87db49359b1a3e36de0f21d88629ac6c
ms.sourcegitcommit: 650850feb90fa62f0b1c02f47fb0727c780dfb03
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2022
ms.locfileid: "12436322"
---
# <a name="microsoft-edge-add-ons-api-reference-in-private-preview"></a>Microsoft Edge 外接程序 API 参考 (在个人预览版中)

> [!NOTE]
> 加载项Microsoft Edge API 目前处于个人预览阶段。  " **发布 API** "页仅对私人预览版的参与者在合作伙伴中心显示。  加载项MICROSOFT EDGE API 正在积极开发中，路线图根据市场变化和客户反馈不断发展。  此处列出的计划并不详尽，可能会发生变化。

这是加载项 API 的 REST Microsoft Edge引用。  此 API 可自动发布已提交到加载项网站的Microsoft Edge更新。

有关概述，请参阅[使用Microsoft Edge预览版中的 (加载项 API) ](using-addons-api.md)。

<!-- ====================================================================== -->
## <a name="upload-a-package-to-update-an-existing-submission"></a>Upload程序包以更新现有提交

上载程序包以更新加载项产品的现有草稿提交。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `POST` | `/products/{productID}/submissions/draft/package` |

#### <a name="uri-parameters"></a>URI 参数

| URI 参数 | 说明 |
|---|---|
| `productID` | 必需。  必须将程序包上载到的产品的产品 ID。 |

#### <a name="request-headers"></a>请求标头

*  必需。  `Authorization: Bearer <auth token>`

*  必需。  `Content-Type: application/zip`

#### <a name="request-body"></a>请求正文

* `<Zip package>`

### <a name="response"></a>响应

#### <a name="response-headers"></a>响应头

*  地点： `{operationID}`

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 202 | 请求已接受处理，但处理未完成。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |

### <a name="see-also"></a>另请参阅

*  简介 [：上载程序包以更新现有提交](using-addons-api.md#uploading-a-package-to-update-an-existing-submission)


<!-- ====================================================================== -->
## <a name="check-the-status-of-a-package-upload"></a>检查程序包上载的状态

获取程序包上载的状态。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `GET` | `/products/{productID}/submissions/draft/package/operations/{operationID}` |

#### <a name="uri-parameters"></a>URI 参数

| URI 参数 | 说明 |
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
    "createdTime": "Date Time",
    "lastUpdatedTime": "Date Time",
    "status": "InProgress",
    "message": null,
    "errorCode": null,
    "errors": null
}
```

#### <a name="response-when-the-operation-succeeds"></a>操作成功时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": "Date Time",
    "status": "Succeeded",
    "message": "Successfully updated package to {fileName}.zip",
    "errorCode": "",
    "errors": null
}
```

#### <a name="response-when-the-operation-fails-with-errors"></a>操作失败但出现错误时的响应

```json
 {
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": "Date Time",
    "status": "Failed",
    "message": "Error Message.",
    "errorCode": "Error Code",
    "errors": ["list of errors"]
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

### <a name="see-also"></a>另请参阅

*  简介 [：检查程序包上载的状态](using-addons-api.md#checking-the-status-of-a-package-upload)


<!-- ====================================================================== -->
## <a name="publish-the-product-draft-submission"></a>发布产品草稿提交

将产品的当前草稿发布到Microsoft Edge加载项。

### <a name="request"></a>请求

| 方法 | 请求 URI |
|---|---|
| `POST` | `/products/{productID}/submissions` |

#### <a name="uri-parameters"></a>URI 参数


| URI 参数 | 说明 |
|---|---|
| `productID` | 必需。  必须发布其草稿的产品的产品 ID。 |

#### <a name="request-headers"></a>请求标头

* 必需。  `Authorization: Bearer <auth token>`

#### <a name="request-body"></a>请求正文

`<Notes for certification>`，采用纯文本格式。

### <a name="response"></a>响应

#### <a name="response-headers"></a>响应头

* 地点： `{operationID}`

#### <a name="status-codes"></a>状态代码

此 API 具有以下预期状态代码。

| HTTP 状态代码 | 说明 |
|---|---|
| 202 | 请求已接受处理，但处理未完成。 |
| 4XX | 请参阅 [错误代码](#error-codes)。 |
| 5XX | 请参阅 [错误代码](#error-codes)。 |

### <a name="see-also"></a>另请参阅

*  简介 [：发布提交](using-addons-api.md#publishing-the-submission)


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

可以在 `GET` 以下方案中调用操作状态 API。  在所有有效的方案中，将 `200 OK` 返回 ，并返回不同的状态消息。

#### <a name="response-when-a-new-product-is-published"></a>新产品发布时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Can't create new extension.",
    "errorCode": "CreateNotAllowed",
    "errors": null
}
```

#### <a name="response-when-there-is-nothing-new-to-be-published"></a>没有要发布的新增功能时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Can't publish extension since there are no updates, please try again after updating the package.",
    "errorCode": "NoModulesUpdated",
    "errors": null
}
```

#### <a name="response-when-there-is-an-in-review-submission-for-the-same-product"></a>当同一产品有评价中提交时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Can't publish extension as your extension submission is in progress. Please try again later.",
    "errorCode": "InProgressSubmission",
    "errors": null    
}
```

#### <a name="response-when-there-is-an-ongoing-unpublished-submission-for-the-same-product"></a>同一产品正在进行的未发布提交时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Can't publish extension as your extension is being unpublished. Please try after you've unpublished.",
    "errorCode": "UnpublishInProgress",
    "errors": null    
}
```

#### <a name="response-where-any-of-the-modules-are-invalid"></a>任何模块无效的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Can't publish extension as your extension has modules that are not valid. Fix the modules with errors and try to publish again.",
    "errorCode": "ModuleStateUnPublishable",
    "errors": [
        {
            "message": "Invalid module : <Modules>"
        }
    ]
}
```

#### <a name="response-when-there-are-validation-errors-in-submission"></a>提交中出现验证错误时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "Extension can't be published as there are submission validation failures. Fix these errors and try again later.",
    "errorCode": "SubmissionValidationError",
    "errors": ["{list of errors}"]
}
```

#### <a name="response-when-the-publish-call-succeeds"></a>发布调用成功时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": "Date Time",
    "status": "Succeeded",
    "message": "Successfully created submission with ID {submission.Id}",
    "errorCode": "",
    "errors": null
}
```

#### <a name="response-when-the-publish-call-fails-with-an-irrecoverable-failure"></a>发布调用失败且无法恢复失败时的响应

```json
{
    "id": "{operationID}",
    "createdTime": "Date Time",
    "lastUpdatedTime": " Date Time ",
    "status": "Failed",
    "message": "An error occurred while performing the operation",
    "errorCode": null,
    "errors": null
}
```

#### <a name="response-when-the-publish-call-fails-with-an-unexpected-failure"></a>发布调用失败但意外失败时的响应

```json
{
    "id": "{operationID}",
    "message": "An error occurred while processing the request. Please contact support Correlation ID: {operationID} Timestamp: {timeStamp}",
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

### <a name="see-also"></a>另请参阅

*  简介 [：检查发布状态](using-addons-api.md#checking-the-publishing-status)


<!-- ====================================================================== -->
## <a name="error-codes"></a>错误代码

下面列出了常见错误代码和可能的原因。  有关完整列表，请参阅 [合作伙伴中心 REST 错误代码](/partner-center/develop/error-codes) 或 [HTTP 状态代码列表](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)。

### <a name="4xx-client-error"></a>4xx：客户端错误

| 消息 | 描述 | 示例方案 |
|---|---|---|
| 400 错误的请求 | 服务器无法理解该请求。 | 正文中没有 (zip) 包。  或者， `Content-Type` 标头缺失或其值不正确。 |
| 401 未经授权 | 请求页面需要授权。 | 身份验证令牌缺失、过期或无效。 |
| 404 未找到 | 服务器找不到请求的页面。 | 指定的 `productID` 或 `operationID` 没有有效 GUID、无效或不属于正在提出请求的开发人员。 |
| 408 请求超时 | 请求所等待的时间比服务器准备等待的时间长。 | 上传程序包时存在超时。 |
| 429 请求过多 | 用户发送的请求过多。 | 发送的请求过多且受到限制。 |

### <a name="5xx-server-error"></a>5xx：服务器错误

| 消息  | 描述  | 示例方案 |
|---|---|---|
| 500 内部服务器错误 | 请求未完成。 | 服务器遇到意外情况。 |


<!-- ====================================================================== -->
## <a name="see-also"></a>另请参阅

*  [使用 Microsoft Edge 外接程序 API (在个人预览版中)](using-addons-api.md)
